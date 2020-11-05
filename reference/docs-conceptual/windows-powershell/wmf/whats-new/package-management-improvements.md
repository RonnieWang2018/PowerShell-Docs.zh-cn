---
ms.date: 06/12/2017
title: WMF 5.1 中对包管理的改进
description: Windows PowerShell 5.1 包括更新的包管理 cmdlet。
ms.openlocfilehash: 572ebd1f0aa3cf09579e13c3ea52ae3e979e421f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663186"
---
# <a name="improvements-to-package-management-in-wmf-51"></a>WMF 5.1 中对包管理的改进

以下是 WMF 5.1 中所做的修复：

## <a name="version-alias"></a>版本别名

**情形** ：如果在系统上安装了包 P1 的版本 1.0 和 2.0，并且要卸载版本 1.0，则会运行 `Uninstall-Package -Name P1 -Version 1.0`，并且预计在运行该 cmdlet 之后将卸载版本 1.0。 但是结果是卸载了版本 2.0。

出现此问题是因为 `-Version` 参数是 `-MinimumVersion` 参数的别名。 当 PackageManagement 查找具有最低版本 1.0 的合格包时，它会返回最新版本。 在正常情况下需要此行为，因为查找最新版本通常是所需结果。 但是，它不应该应用于 `Uninstall-Package` 情况。

**解决方案** ：在 PackageManagement（也称为 OneGet）和 PowerShellGet 中完全删除了 `-Version` 别名。

## <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a>多个用于启动 NuGet 提供程序的提示

**情形** ：在计算机上首次运行 `Find-Module`、`Install-Module` 或其他 PackageManagement cmdlet 时，PackageManagement 会尝试启动 NuGet 提供程序。 它这样做是因为 PowerShellGet 提供程序还使用 NuGet 提供程序来下载 PowerShell 模块。
PackageManagement 随后会提示用户输入安装 NuGet 提供程序的权限。 用户选择“yes”进行启动之后，会安装最新版本的 NuGet 提供程序。

但是在某些情况下，当在计算机上安装了旧版本的 NuGet 提供程序时，较旧版本的 NuGet 有时会先加载到 PowerShell 会话中（这是 PackageManagement 中的争用条件）。 但是 PowerShellGet 需要更新版本的 NuGet 提供程序才可正常运行，因此 PowerShellGet 会要求 PackageManagement 再次启动 NuGet 提供程序。
这会导致出现多个用于启动 NuGet 提供程序的提示。

**解决方案** ：在 WMF 5.1 中，PackageManagement 加载最新版本的 NuGet 提供程序，以避免出现多个要求启动 NuGet 提供程序的提示。

还可以通过手动删除旧版本的 NuGet 提供程序（NuGet-Anycpu.exe，如果在 $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies 中存在）来解决此问题

## <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a>在仅具有 intranet 访问的计算机上支持 PackageManagement

**情形** ：对于企业情形，人们在没有 Internet 访问，而是只有 Intranet 的环境中工作。 在 WMF 5.0 中，PackageManagement 不支持这种情况。

**情形** ：在 WMF 5.0 中，PackageManagement 不支持仅具有 Intranet（但没有 Internet）访问的计算机。

**解决方案** ：在 WMF 5.1 中，可以按照以下步骤允许 Intranet 计算机使用 PackageManagement：

1. 使用 `Install-PackageProvider -Name NuGet`，通过具有 Internet 连接的其他计算机下载 NuGet 提供程序。

2. 在 `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` 或 `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget` 下找到 NuGet 提供程序。

3. 将二进制文件复制到 Intranet 计算机可以访问的文件夹或网络共享位置，然后使用 `Install-PackageProvider -Name NuGet -Source <Path to folder>` 安装 NuGet 提供程序。

## <a name="event-logging-improvements"></a>事件日志记录改进

安装包时，你会更改计算机的状态。 在 WMF 5.1 中，PackageManagement 现在针对 `Install-Package`、`Uninstall-Package` 和 `Save-Package` 活动将事件记录到 Windows 事件日志中。 对于 PowerShell，事件日志是相同的，即 `Microsoft-Windows-PowerShell, Operational`。

## <a name="support-for-basic-authentication"></a>对基本身份验证的支持

在 WMF 5.1 中，PackageManagement 支持从需要基本身份验证的存储库查找和安装包。 可以向 `Find-Package` 和 `Install-Package` cmdlet 提供凭据。 例如：

```powershell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```

## <a name="support-for-using-packagemanagement-behind-a-proxy"></a>支持在代理后面使用 PackageManagement

在 WMF 5.1 中，PackageManagement 现在采用新的代理参数 `-ProxyCredential` 和 `-Proxy`。 使用这些参数可以向 PackageManagement cmdlets 指定代理 URL 和凭据。 默认情况下，会使用系统代理设置。 例如：

```powershell
Find-Package -Source https://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```
