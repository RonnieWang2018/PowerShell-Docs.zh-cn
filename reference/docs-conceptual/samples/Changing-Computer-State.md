---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 更改计算机状态
description: 本示例演示如何使用 PowerShell 中的外部命令管理计算机的配置。
ms.openlocfilehash: 341f29f24d7e4bd341ccc0954b16d4b75880678b
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500668"
---
# <a name="changing-computer-state"></a>更改计算机状态

若要在 PowerShell 中重置计算机，请使用标准命令行工具、WMI 或 CIM 类。
尽管你使用 PowerShell 仅仅是为了运行该工具，但了解如何在 PowerShell 中更改计算机的电源状态将阐明有关在 PowerShell 中使用外部工具的一些重要详细信息。

## <a name="locking-a-computer"></a>锁定计算机

使用标准可用工具直接锁定计算机的唯一方法是调用 **user32.dll** 中的 **LockWorkstation()** 函数：

```powershell
rundll32.exe user32.dll,LockWorkStation
```

此命令将立即锁定工作站。 它使用 rundll32.exe，后者运行 Windows DLL（并保存其库以便重复使用）以运行 `user32.dll`（Windows 管理函数的库）。

如果在启用了“快速用户切换”时锁定工作站（例如在 Windows XP 中），则计算机将显示用户登录屏幕，而不会启动当前用户的屏幕保护程序。

若要关闭终端服务器上的特定会话，请使用 **tsshutdn.exe** 命令行工具。

## <a name="logging-off-the-current-session"></a>注销当前会话

可以使用多种不同的方法来注销本地系统上的会话。 最简单的方法是使用远程桌面/终端服务命令行工具 logoff.exe（若要了解有关详细信息，请在 PowerShell 提示符处键入 `logoff /?`）。 若要注销当前活动会话，请键入 `logoff` 而不带参数。

你还可以使用具 **shutdown.exe** 工具及其 logoff 选项：

```powershell
shutdown.exe -l
```

另一种方法是使用 WMI。 Win32_OperatingSystem 类具有 Shutdown 方法。
调用具有 0 标志的方法将启动注销：

有关 Shutdown 方法的详细信息，请参阅 [Win32_OperatingSystem 类的 Shutdown 方法](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)

```powershell
Get-CimInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a>关闭或重启计算机

关闭和重启计算机通常是相同类型的任务。 关闭计算机的工具通常也可以重启计算机，反之亦然。 从 PowerShell 重启计算机有两个直接的选项。 使用 tsshutdn.exe 或 shutdown.exe 及其相应参数。 你可以从 `tsshutdn.exe /?` 或 `shutdown.exe /?` 获取详细的使用信息。

也可以直接从 PowerShell 执行关闭和重启操作。

要关闭计算机，请使用 Stop-Computer 命令

```powershell
Stop-Computer
```

要重启操作系统，请使用 Restart-Computer 命令

```powershell
Restart-Computer
```

要强制立即重新启动计算机，请使用 -Force 参数。

```powershell
Restart-Computer -Force
```
