---
ms.date: 09/26/2017
title: 预发行模块版本
description: PowerShellGet 模块支持使用语义化版本控制将 1.0.0 以上的版本的模块标记为预发行版。
ms.openlocfilehash: f794722f0a89f98f8f445ecd45dad9d3d2d7f3cb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661524"
---
# <a name="prerelease-module-versions"></a>预发行模块版本

从版本 1.6.0 开始，PowerShellGet 和 PowerShell 库都支持将 1.0.0 以上的版本标记为预发行版。 在此功能之前，预发行包仅限于以 0 开头的版本。 这些功能的目标是为 [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) 版本控制约定提供更好的支持，并且不会破坏 PowerShell 版本 3 及更高版本或 PowerShellGet 现有版本的向后兼容性。 本主题重点介绍特定于模块的功能。 脚本的等效功能在[预发行版脚本](script-prerelease-support.md)主题中介绍。 使用这些功能，发布服务器可以将模块或脚本标识为版本 2.5.0-alpha，随后可发布用于取代预发行版本的生产就绪版本 2.5.0。

在高级别中，预发行模块的功能包括：

- 在模块清单的 PSData 部分添加预发行版字符串将模块标识为预发行版本。 当模块发布到 PowerShell 库后，会从清单中提取此数据，用于标识预发行包。
- 获取预发行包需要将 `-AllowPrerelease` 标记添加到 PowerShellGet 命令 `Find-Module`、`Install-Module`、`Update-Module` 和 `Save-Module`。 如果未指定标记，则不会显示预发行包。
- `Find-Module`、`Get-InstalledModule` 显示的模块版本及在 PowerShell 库中显示的模块版本将显示为附加了预发行版字符串的单个字符串，如 2.5.0-alpha。

以下介绍了这些功能的详细信息。

这些更改不会影响内置于 PowerShell 的模块版本支持，并与 PowerShell 3.0、4.0 和 5 兼容。

## <a name="identifying-a-module-version-as-a-prerelease"></a>将模块版本标识为预发行版

PowerShellGet 对预发行版本的支持要求在模块清单中使用两个字段：

- 如果使用预发行版本，包含在模块清单中的 ModuleVersion 必须为 3 段式版本，且必须符合现有的 PowerShell 版本控制。 版本格式为 A.B.C，其中 A、B 和 C 均为整数。
- 预发行版字符串指定于模块清单、PrivateData 的 PSData 部分。

下面是对预发行版字符串的详细要求。

用于将模块定义为预发行版的模块清单的示例部分如下所示：

```powershell
@{
    ModuleVersion = '2.5.0'
    #---
    PrivateData = @{
        PSData = @{
            Prerelease = 'alpha'
        }
    }
}
```

对预发行版字符串的详细要求如下：

- ModuleVersion 为 Major.Minor.Build 的 3 段时，可能只指定预发行版字符串。 这符合 SemVer v1.0.0 的要求。
- 连字符是内部版本号和预发行版字符串之间的分隔符。 连字符只能作为第一个字符包含在预发行版字符串中。
- 预发行版字符串可以只包含 ASCII 字母数字 [0-9A-Za-z-]。 预发行版字符串最好以 alpha 字符开头，这样在扫描包列表时，可以更轻松地辨认这是预发行版本。
- 此时仅支持 SemVer v1.0.0 预发行字符串。 预发行版字符串不得包含句点或 + [.+]，而在 SemVer 2.0 中允许包含  。
- 支持的预发行版字符串的示例包括：-alpha、-alpha1、-BETA、-update20171020

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a>预发行版本控制对排序顺序和安装文件夹的影响

使用预发行版本时，排序顺序会发生更改，这在发布到 PowerShell 库时，以及使用 PowerShellGet 命令安装模块时非常重要。 如果预发行版字符串是针对两个模块指定的，则排序顺序基于连字符后面的字符串部分。 因此，2.5.0-alpha 版低于 2.5.0-beta 版，而 2.5.0-beta 版低于 2.5.0-gamma 版。 如果两个模块具有相同的 ModuleVersion，并且只有一个模块具有预发行版字符串，则不具有预发行版字符串的模块会假定为生产就绪版本，在排序时的版本要比具有预发行版字符串的预发行版本高。 例如，在比较 2.5.0 和 2.5.0-beta 版本时，2.5.0 版本会视为两者中更高的版本。

在发布到 PowerShell 库时，默认情况下，发布的模块版本必须高于 PowerShell 库中以前发布的任何版本。

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a>使用 PowerShellGet 命令查找和获取预发行包

使用 PowerShellGet Find-Module、Install-Module、Update-Module 和 Save-Module 命令处理预发行包需要添加 -AllowPrerelease 标记。 如果已指定 -AllowPrerelease，则会包括预发行包（如存在）。 如果未指定 -AllowPrerelease 标记，则不会显示预发行包。

PowerShellGet 模块命令中这种情况的唯一例外是 Get-InstalledModule，以及某些情况下的 Uninstall-Module。

- Get-InstalledModule 始终在模块的版本字符串中自动显示预发行信息。
- Uninstall-Module 在未指定任何版本时默认卸载最新版本的模块  。 该行为尚未更改。 但是，如果预发行版本是使用 -RequiredVersion 指定的，则需要 -AllowPrerelease。

## <a name="examples"></a>示例

假定 PowerShell 库具有 TestPackage 模块版本 1.8.0 和 1.9.0-alpha。 如果未指定 `-AllowPrerelease`，则仅返回版本 1.8.0。

```powershell
find-module TestPackage
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.8.0          TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

```powershell
find-module TestPackage -AllowPrerelease
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.9.0-alpha    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

若要安装预发行版，请始终指定 -AllowPrerelease。 指定预发行版字符串是不够的。

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha
```

```output
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage
```

前一个命令失败，因为未指定 -AllowPrerelease。 添加 `-AllowPrerelease` 将会成功。

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

如果模块仅仅是因为指定的预发行版而有所区别，则不支持并行安装该模块的各版本。 使用 PowerShellGet 安装模块时，通过使用 ModuleVersion 创建文件夹名称，并行安装同一模块的不同版本。 不含预发行版字符串的 ModuleVersion 可用作文件夹名称。 用户安装 MyModule 的 2.5.0-alpha 版本时，会安装到 `MyModule\2.5.0` 文件夹。 如果用户之后安装 2.5.0-beta，则 2.5.0-beta 版本会覆盖  `MyModule\2.5.0` 文件夹的内容。 此方法的一个优点是安装生产就绪版本后无需卸载预发行版本。 以下示例展示了期望的效果：

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-alpha     TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name            Repository  Description
-------        ----            ----------  -----------
1.9.0-beta     TestPackage     PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

```

如果未通过 -RequiredVersion，Uninstall-Module 会删除最新版本的模块。
如果已指定 -RequiredVersion，并且是预发行版，则必须将 -AllowPrerelease 添加到命令中。

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
2.0.0-alpha1    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta

Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-Module

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
2.0.0-alpha1    TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...
```

## <a name="more-details"></a>更多详细信息

- [预发行脚本版本](script-prerelease-support.md)
- [Find-Module](/powershell/module/powershellget/find-module)
- [Install-Module](/powershell/module/powershellget/install-module)
- [Save-Module](/powershell/module/powershellget/save-module)
- [Update-Module](/powershell/module/powershellget/Update-Module)
- [Get-InstalledModule](/powershell/module/powershellget/get-installedmodule)
- [UnInstall-Module](/powershell/module/powershellget/uninstall-module)
