---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 调试 DSC 资源
description: 本文介绍如何为 DSC 配置启用调试。
ms.openlocfilehash: 5dda217e8dc9cc4b8699c82153c1a588d405d99e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654123"
---
# <a name="debugging-dsc-resources"></a>调试 DSC 资源

> 适用于：Windows PowerShell 5.0

在 PowerShell 5.0 中，Desired State Configuration (DSC) 引入了一项新功能，允许你在应用配置时调试 DSC 资源。

## <a name="enabling-dsc-debugging"></a>启用 DSC 调试

必须通过调用 [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) cmdlet 启用调试后，才能调试资源。 此 cmdlet 采用强制参数， **BreakAll** 。

你可通过查看调用 [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) 的结果以验证是否已启用调试。

以下 PowerShell 输出显式了启用调试的结果：

```powershell
PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
NONE

PS C:\DebugTest> Enable-DscDebug -BreakAll

PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
ForceModuleImport
ResourceScriptBreakAll

PS C:\DebugTest>
```

## <a name="starting-a-configuration-with-debug-enabled"></a>启用调试时启动配置

若要调试 DSC 资源，首先需启动调用该资源的配置。 针对此示例，我们将查看调用 **WindowsFeature** 资源的简单配置以确保安装了“WindowsPowerShellWebAccess”功能：

```powershell
Configuration PSWebAccess
    {
    Import-DscResource -ModuleName 'PsDesiredStateConfiguration'
    Node localhost
        {
        WindowsFeature PSWA
            {
            Name = 'WindowsPowerShellWebAccess'
            Ensure = 'Present'
            }
        }
    }
PSWebAccess
```

编译配置后，通过调用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) 启用该配置。 当本地配置管理器 (LCM) 调用配置中的首个资源时，配置会停止运行。 如果你使用 `-Verbose` 和 `-Wait` 参数，输出会显示你需要输入才能启动调试的各行内容。

```powershell
Start-DscConfiguration .\PSWebAccess -Wait -Verbose
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfiguration
Manager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Set      ]
WARNING: [TEST-SRV]:                            [DSCEngine] Warning LCM is in Debug 'ResourceScriptBreakAll' mode.  Resource script processing will
be stopped to wait for PowerShell script debugger to attach.
VERBOSE: [TEST-SRV]:                            [DSCEngine] Importing the module C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateCo
nfiguration\DscResources\MSFT_RoleResource\MSFT_RoleResource.psm1 in force mode.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Resource ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]: LCM:  [ Start  Test     ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]:                            [[WindowsFeature]PSWA] Importing the module MSFT_RoleResource in force mode.
WARNING: [TEST-SRV]:                            [[WindowsFeature]PSWA] Resource is waiting for PowerShell script debugger to attach.
Use the following commands to begin debugging this resource script:
Enter-PSSession -ComputerName TEST-SRV -Credential <credentials>
Enter-PSHostProcess -Id 9000 -AppDomainName DscPsPluginWkr_AppDomain
Debug-Runspace -Id 9
```

此时，LCM 已调用该资源，并到达第一个断点。 输出中的最后三行表明了如何附加到进程并启动调试资源脚本。

## <a name="debugging-the-resource-script"></a>调试资源脚本

启动 PowerShell ISE 的新实例。 在控制台窗格中，输入 `Start-DscConfiguration` 输出中最后三行的内容作为命令，将 `<credentials>` 替换为有效的用户凭据。 你现在应看到类似于下面这样的提示：

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

资源脚本会在脚本窗格中打开，调试器会在 **Test-TargetResource** 函数（基于类的资源的 **Test()** 方法）的第一行上停止。 现在可以在 ISE 中使用调试命令来单步执行资源脚本、查看变量值、查看调用堆栈等等。 请记住，资源脚本（或类）中的每行都会设置为断点。

## <a name="disabling-dsc-debugging"></a>禁用 DSC 调试

在调用 [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) 后，对 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) 的所有调用都会导致配置中断调试器。 若要让配置正常运行，必须通过调用 [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) cmdlet 来禁用调试。

> [!NOTE]
> 重启不会更改 LCM 的调试状态。 如果调试已启用，那么启动配置仍会在重启后中断调试器。

## <a name="see-also"></a>另请参阅

- [使用 MOF 编写自定义 DSC 资源](../resources/authoringResourceMOF.md)
- [使用 PowerShell 类编写自定义 DSC 资源](../resources/authoringResourceClass.md)
