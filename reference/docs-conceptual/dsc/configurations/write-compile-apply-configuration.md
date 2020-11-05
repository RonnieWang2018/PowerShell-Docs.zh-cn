---
ms.date: 06/22/2020
keywords: dsc,powershell,配置,服务,设置
title: 编写、编译和应用配置
description: 本练习演示创建和应用 DSC 配置的完整过程。 在以下示例中，你将学习如何编写和应用一个非常简单的配置
ms.openlocfilehash: f173fe0dc6cd73e2b49bb8c44a9ee1a53eab475f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645037"
---
# <a name="write-compile-and-apply-a-configuration"></a>编写、编译和应用配置

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

本练习演示创建和应用 Desired State Configuration (DSC) 配置的完整过程。 在以下示例中，你将学习如何编写和应用一个非常简单的配置。 该配置会确保本地计算机上存在“HelloWorld.txt”文件。
如果删除该文件，则 DSC 会在下次更新时重新创建它。

有关什么是 DSC 及其工作原理的概述，请参阅[面向开发人员的 Desired State Configuration 概述](../overview/overview.md)。

## <a name="requirements"></a>要求

要运行此示例，需要运行 PowerShell 4.0 或更高版本的计算机。

## <a name="write-the-configuration"></a>写入配置

DSC [配置](configurations.md)是一个特殊的 PowerShell 功能，可定义用于配置一个或多个目标计算机（节点）的方式。

在 PowerShell ISE 或其他 PowerShell 编辑器中，键入以下内容：

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when
    # this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a
        # source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

> [!IMPORTANT]
> 在更为复杂的场景中，如果需要导入多个模块以便在同一配置中使用多个 DSC 资源，请务必使用 `Import-DscResource` 让每个模块单独占一行。 这样一来，在源代码管理中更易于维护，这也是在 Azure 状态配置中使用 DSC 时所必需的操作。
>
> ```powershell
>  Configuration HelloWorld {
>
>   # Import the module that contains the File resource.
>   Import-DscResource -ModuleName PsDesiredStateConfiguration
>   Import-DscResource -ModuleName xWebAdministration
>
> ```

将文件保存为“HelloWorld.ps1”。

定义配置类似于定义函数。 **节点** 块指定要配置的目标节点，在本示例中为 `localhost`。

配置会调用一个[资源](../resources/resources.md)（`File` 资源）。 资源负责确保目标节点处于由配置定义的状态。

## <a name="compile-the-configuration"></a>编译配置

对于要应用于节点的 DSC 配置，必须首先将其编译为 MOF 文件。 与函数类似，运行配置会为 `Node` 块定义的每个节点编译一个 `.mof` 文件。 若要运行配置，需要使用点将 `HelloWorld.ps1` 脚本的来源获取到当前作用域内。 有关详细信息，请参阅 [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts#script-scope-and-dot-sourcing)。

<!-- markdownlint-disable MD038 -->
通过在 `. `（点、空格）后键入用于存储 `HelloWorld.ps1` 脚本的路径，来使用点获取其来源。 随后可以通过调用配置（类似于函数）来运行它。 还可以调用脚本底部的配置函数，以便无需使用点获取来源。
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

此操作生成以下输出：

```Output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a>应用配置

现在你已编译好 MOF，可以通过调用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet 将配置应用于目标节点（在本例中为本地计算机）。

`Start-DscConfiguration` cmdlet 通知作为 DSC 引擎的[本地配置管理器 (LCM)](../managing-nodes/metaConfig.md) 应用配置。 LCM 的工作是调用 DSC 资源以应用配置。

使用下面的代码执行 `Start-DSCConfiguration` cmdlet。 向 Path 参数指定用于存储 `localhost.mof` 的目录路径。 `Start-DSCConfiguration` cmdlet 在指定的目录中查找任何 `<computername>.mof` 文件。 `Start-DSCConfiguration` cmdlet 尝试将找到的每个 `.mof` 文件应用于通过文件名指定的 `computername`（“localhost”、“server01”、“dc-02”等）。

> [!NOTE]
> 如果未指定 `-Wait` 参数，则 `Start-DSCConfiguration` 会创建后台作业来执行操作。 通过指定 `-Verbose` 参数可以观察操作的详细输出。 `-Wait` 和 `-Verbose` 是可选参数。

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>测试配置

`Start-DSCConfiguration` cmdlet 完成后，指定的位置就会出现 `HelloWorld.txt` 文件。 可以使用 [Get-content](/powershell/module/microsoft.powershell.management/get-content) cmdlet 验证内容。

还可以使用 [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) 测试当前状态。

如果节点当前符合所应用的配置，则输出应为 `True`。

```powershell
Test-DSCConfiguration
```

```Output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```Output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a>重新应用配置

若要再次应用配置，可以删除配置所创建的文本文件。 将 `Start-DSCConfiguration` cmdlet 与 `-UseExisting` 参数一起使用。 `-UseExisting` 参数指示 `Start-DSCConfiguration` 重新应用“current.mof”文件，它表示最近成功应用的配置。

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>后续步骤

- 在 [DSC 配置](configurations.md)中了解有关 DSC 配置的详细信息。
- 查看哪些 DSC 资源可用，以及如何在 [DSC 资源](../resources/resources.md)中创建自定义 DSC 资源。
- 在 [PowerShell 库](https://www.powershellgallery.com/)中查找 DSC 配置和资源。
