---
ms.date: 08/15/2019
keywords: dsc,powershell,配置,安装程序
title: 适用于 Windows 的 Desired State Configuration (DSC) 入门
description: 本主题介绍了如何开始使用适用于 Windows 的 PowerShell Desired State Configuration (DSC)。
ms.openlocfilehash: 2b9ddba2023a3933e3ad70d7bfee798ff07f0484
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662817"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a>适用于 Windows 的 Desired State Configuration (DSC) 入门

本主题介绍了如何开始使用适用于 Windows 的 PowerShell Desired State Configuration (DSC)。 有关 DSC 的常规信息，请参阅 [Windows PowerShell Desired State Configuration 入门](../overview/overview.md)。

## <a name="supported-windows-operation-system-versions"></a>支持的 Windows 操作系统版本

支持以下版本：

- Windows Server 2019
- Windows Server 2016
- Windows Server 2012R2
- Windows Server 2012
- Windows Server 2008 R2 SP1
- Windows 10
- Windows 8.1
- Windows 7

由于 [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) 独立产品 SKU 不包含 Desired State Configuraion 实现，因此无法由 PowerShell DSC 或 Azure Automation State Configuration 管理。

## <a name="installing-dsc"></a>安装 DSC

PowerShell Desired State Configuration 包含在 Windows 中，并通过 Windows Management Framework 进行更新。 最新版本为 [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616)。

> [!NOTE]
> 无需启用 Windows Server 功能“DSC 服务”，即可使用 DSC 管理计算机。
> 只有在生成 Windows 拉取服务器实例时，才需要此功能。

## <a name="using-dsc-for-windows"></a>使用适用于 Windows 的 DSC

下面几个部分介绍了如何在 Windows 计算机上创建和运行 DSC 配置。

### <a name="creating-a-configuration-mof-document"></a>创建配置 MOF 文档

Windows PowerShell `Configuration` 关键字用于创建配置。
下面逐步介绍了如何使用 Windows PowerShell 创建配置文档。

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a>定义配置并生成配置文档：

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```

#### <a name="install-a-module-containing-dsc-resources"></a>安装包含 DSC 资源的模块

Windows PowerShell Desired State Configuration 有包含 DSC 资源的内置模块。
也可以使用 PowerShellGet cmdlet 从 PowerShell 库等外部源加载模块。

```PowerShell
Install-Module 'PSDscResources' -Verbose
```

#### <a name="apply-the-configuration-to-the-machine"></a>将配置应用于计算机

> [!NOTE]
> 即使在运行 `localhost` 配置的情况下，也需要将 Windows 配置为接收 PowerShell 远程命令，以允许 DSC 运行。 在提升的 PowerShell 终端中运行 `Set-WsManQuickConfig -Force`，即可轻松地正确配置环境。

可以使用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet，将配置文档（MOF 文件）应用于计算机。

```powershell
Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose
```

#### <a name="get-the-current-state-of-the-configuration"></a>获取配置的当前状态

[Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet 可查询计算机的当前状态，并返回配置的当前值。

```powershell
Get-DscConfiguration
```

[Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) cmdlet 可返回应用于计算机的当前元配置。

```powershell
Get-DscLocalConfigurationManager
```

#### <a name="remove-the-current-configuration-from-a-machine"></a>从计算机中删除当前配置

[Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)

```powershell
Remove-DscConfigurationDocument -Stage Current -Verbose
```

#### <a name="configure-settings-in-local-configuration-manager"></a>在本地配置管理器中配置设置

使用 [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet 将元配置 MOF 文件应用于计算机。 需要元配置 MOF 的路径。

```powershell
Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose
```

## <a name="windows-powershell-desired-state-configuration-log-files"></a>Windows PowerShell Desired State Configuration 日志文件

DSC 日志写入 Windows 事件日志，路径为 `Microsoft-Windows-Dsc/Operational`。
可以按照 [DSC 事件日志位置](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs)中的步骤操作，启用其他日志用于调试目的。
