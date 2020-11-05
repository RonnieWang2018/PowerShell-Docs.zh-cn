---
ms.date: 07/08/2020
keywords: dsc,powershell,配置,安装程序
title: 使用 PowerShell 类编写自定义 DSC 资源
description: 本文演示了如何创建简单的资源来管理指定路径中的文件。
ms.openlocfilehash: 72a828795c29e10ff66f164b8871b0fea7a1e0a8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667311"
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a>使用 PowerShell 类编写自定义 DSC 资源

> 适用于：Windows PowerShell 5.0

了解了在 Windows PowerShell 5.0 中使用 PowerShell 类的简介后，现在你可以通过创建一个类来定义 DSC 资源。 类可以同时定义资源的架构和实现，因此无需创建单独的 MOF 文件。 因为无需 **DSCResources** 文件夹，基于类的资源的文件夹结构也得以简化。

在基于类的 DSC 资源中，架构被定义为类的属性，可通过特性对其进行修改来指定属性类型。 资源通过 `Get()` 、`Set()` 和 `Test()` 的方法得到实现（相当于脚本资源中的 `Get-TargetResource`、`Set-TargetResource` 和 `Test-TargetResource` 函数）。

在本文中，我们将创建一个名为 FileResource 的简单资源来管理指定路径中的文件。

有关 DSC 资源的详细信息，请参阅[构建自定义 Windows PowerShell Desired State Configuration 资源](authoringResource.md)。

> [!Note]
> 基于类的资源中不支持泛型集合。

## <a name="folder-structure-for-a-class-resource"></a>类资源的文件夹结构

想要使用 PowerShell 类实现 DSC 自定义资源，请创建下列文件夹结构。
在 `MyDscResource.psm1` 中定义类，并且在 `MyDscResource.psd1` 中定义模块清单。

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        MyDscResource.psm1
        MyDscResource.psd1
```

## <a name="create-the-class"></a>创建类

使用类关键字创建 PowerShell 类。 使用 `DscResource()` 特性来指定类是 DSC 资源。 类的名称就是 DSC 资源的名称。

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a>声明属性

DSC 资源架构被定义为类的属性。 我们声明下列三个属性。

```powershell
[DscProperty(Key)]
[string]$Path

[DscProperty(Mandatory)]
[Ensure] $Ensure

[DscProperty(Mandatory)]
[string] $SourcePath

[DscProperty(NotConfigurable)]
[Nullable[datetime]] $CreationTime
```

请注意，属性通过特性进行修改。 特性的含义如下：

- **DscProperty(Key)** ：属性是必需的。 属性为键。 所有被标记为键的属性的值必须接合以唯一地标识配置内的资源实例。
- **DscProperty(Mandatory)** ：属性是必需的。
- **DscProperty(NotConfigurable)** ：属性为只读属性。 使用此特性标记的属性不能通过配置进行设置，但出现时使用 `Get()` 方法进行填充。
- **DscProperty()** ：属性可配置，但不是必需的。

`$Path` 和 `$SourcePath` 属性均为字符串。 `$CreationTime` 是一个 [DateTime](/dotnet/api/system.datetime) 属性。 `$Ensure` 属性是枚举类，定义如下。

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a>实现该方法

`Get()` 、`Set()` 和 `Test()` 方法类似于脚本资源中的 `Get-TargetResource`、`Set-TargetResource` 和 `Test-TargetResource` 函数。

此代码还包括 `CopyFile()` 函数，这是一个可将文件从 `$SourcePath` 复制到 `$Path` 的 helper 函数。

```powershell
    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)

        if ($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ErrorAction Ignore

        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = New-Object -TypeName System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
```

### <a name="the-complete-file"></a>完整文件

完整类文件如下。

```powershell
enum Ensure
{
    Absent
    Present
}

<#
   This resource manages the file in a specific path.
   [DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource
{
    <#
       This property is the fully qualified path to the file that is
       expected to be present or absent.

       The [DscProperty(Key)] attribute indicates the property is a
       key and its value uniquely identifies a resource instance.
       Defining this attribute also means the property is required
       and DSC will ensure a value is set before calling the resource.

       A DSC resource must define at least one key property.
    #>
    [DscProperty(Key)]
    [string]$Path

    <#
        This property indicates if the settings should be present or absent
        on the system. For present, the resource ensures the file pointed
        to by $Path exists. For absent, it ensures the file point to by
        $Path does not exist.

        The [DscProperty(Mandatory)] attribute indicates the property is
        required and DSC will guarantee it is set.

        If Mandatory is not specified or if it is defined as
        Mandatory=$false, the value is not guaranteed to be set when DSC
        calls the resource.  This is appropriate for optional properties.
    #>
    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    <#
       This property defines the fully qualified path to a file that will
       be placed on the system if $Ensure = Present and $Path does not
        exist.

       NOTE: This property is required because [DscProperty(Mandatory)] is
        set.
    #>
    [DscProperty(Mandatory)]
    [string] $SourcePath

    <#
       This property reports the file's create timestamp.

       [DscProperty(NotConfigurable)] attribute indicates the property is
       not configurable in DSC configuration.  Properties marked this way
       are populated by the Get() method to report additional details
       about the resource when it is present.

    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = new-object System.IO.FileInfo($this.Path)
        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                 to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
} # This module defines a class for a DSC "FileResource" provider.
```

## <a name="create-a-manifest"></a>创建清单

若要让基于类的资源对 DSC 引擎可用，你必须在清单文件中添加 `DscResourcesToExport` 声明，以指示模块导出资源。 我们的清单如下所示：

```powershell
@{

# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

DscResourcesToExport = 'FileResource'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'Microsoft Corporation'

# Company or vendor of this module
CompanyName = 'Microsoft Corporation'

# Copyright statement for this module
Copyright = '(c) 2014 Microsoft. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''
}
```

## <a name="test-the-resource"></a>测试资源

如前面所述，将类和清单文件保存到文件夹结构中之后，就可以创建一个使用新资源的配置。 有关如何运行 DSC 配置的信息，请参阅[执行配置](../pull-server/enactingConfigurations.md)。 下面的配置将检查 `c:\test\test.txt` 的文件是否存在，如果不存在，则会从 `c:\test.txt` 进行复制（运行配置前应先创建 `c:\test.txt`）。

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    }
}
Test
Start-DscConfiguration -Wait -Force Test
```

## <a name="supporting-psdscrunascredential"></a>支持 PsDscRunAsCredential

> [注意] PsDscRunAsCredential 在 PowerShell 5.0 及更高版本中受支持。

可以在 [DSC 配置](../configurations/configurations.md)资源块中使用 PsDscRunAsCredential 属性，以指定应使用指定的一组凭据运行资源。 有关详细信息，请参阅[使用用户凭据运行 DSC](../configurations/runAsUser.md)。

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a>需要或禁止对资源使用 PsDscRunAsCredential

`DscResource()` 属性使用可选参数 RunAsCredential。 此参数可取以下三个值之一：

- `Optional` PsDscRunAsCredential：对于调用此资源的配置，此为可选值。 这是默认值。
- `Mandatory` PsDscRunAsCredential：必须用它来调用此资源的所有配置。
- `NotSupported`：调用此资源的配置无法使用 PsDscRunAsCredential。
- `Default` 与 `Optional` 相同。

例如，使用以下属性指定自定义资源不支持使用 PsDscRunAsCredential：

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="declaring-multiple-class-resources-in-a-module"></a>声明模块中的多个类资源

模块可以定义多个基于类的 DSC 资源。 可以按以下方式创建文件夹结构：

1. 定义 `<ModuleName>.psm1` 文件中的第一个资源以及 DSCResources 文件夹下的后续资源。

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- SecondResource.psm1
   ```

1. 定义“DSCResources”文件夹下的所有资源。

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- FirstResource.psm1
              SecondResource.psm1
   ```

> [!NOTE]
> 在上面的示例中，将“DSCResources”下的任何 PSM1 文件添加到 PSD1 文件中的“NestedModules”键。

### <a name="access-the-user-context"></a>访问用户上下文

若要从自定义资源访问用户上下文，可以使用自动变量 `$global:PsDscContext`。

例如，下面的代码会将用于运行资源的用户上下文写入详细输出流：

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>另请参阅

[构建自定义 Windows PowerShell Desired State Configuration 资源](authoringResource.md)
