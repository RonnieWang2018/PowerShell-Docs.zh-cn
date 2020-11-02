---
ms.date: 06/12/2017
title: 信息流
description: PowerShell 5.0 添加了新的结构化信息  流以在脚本及其主机之间传输结构化数据。
ms.openlocfilehash: 818c99ce281f5ada596ff92cd7bafb8b7cacf709
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646706"
---
# <a name="information-stream"></a>信息流

PowerShell 5.0 添加了新的结构化信息  流以在脚本及其主机之间传输结构化数据。 已将 `Write-Host` 更新为将其输出发出到信息  流，你现在可以在信息流中捕获或抑制它。 新的 `Write-Information` cmdlet 与 InformationVariable  和 InformationAction  通用参数一起使用可以增加灵活性并启用更多功能。

以下函数使用充分利用新信息  流的 cmdlet。

```powershell
function OutputGusher {
  [CmdletBinding()]
  param()
  Write-Host -ForegroundColor Green 'Preparing to give you output!'
  Write-Host '============================='
  Write-Host 'I ' -ForegroundColor White -NoNewline
  Write-Host '<3 ' -ForegroundColor Red -NoNewline
  Write-Host 'Output' -ForegroundColor White
  Write-Host '============================='

  $p = Get-Process -id $pid
  $p

  Write-Information $p -Tag Process
  Write-Information 'Some spammy logging information' -Tag LogLow
  Write-Information 'Some important logging information' -Tag LogHigh

  Write-Host
  Write-Host -ForegroundColor Green 'SCRIPT COMPLETE!!'
}
```

以下示例显示运行此函数的结果。

```powershell
$r = OutputGusher
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================

SCRIPT COMPLETE!!
```

`$r` 变量已捕获脚本变量 `$p` 中的进程信息。

```powershell
$r.Id
4008
```

与 `Write-Host` cmdlet 不同，使用  **的 InformationVariable**`Write-Information` 参数可以捕获变量中的输出。 使用标记  可以为发送到信息  流的消息创建单独通道。

```powershell
$r = OutputGusher -InformationVariable iv
$ivOutput = $iv | Group-Object -AsHash { $_.Tags[0] } -AsString
$ivOutput
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================
SCRIPT COMPLETE!!

Name                 Value
----                 -----
LogLow               {Some spammy logging information}
LogHigh              {Some important logging information}
Process              {System.Diagnostics.Process (powershell)}
PSHOST               {Preparing to give you output!, =============================, I , <3 ...}
```

使用标记将消息发送到信息  流时，该消息不会显示在主机应用程序中，但可以使用标记名称进行检索。 例如：

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```
