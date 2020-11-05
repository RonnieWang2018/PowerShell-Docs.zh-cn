---
ms.date: 06/12/2017
title: 脚本跟踪和日志记录
description: Windows PowerShell 5.x 添加了新的事件日志记录，允许你审核脚本块执行。
ms.openlocfilehash: d47fb6fdd1ee4b9372fab7b81e6dc94fb45b8880
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663121"
---
# <a name="script-tracing-and-logging"></a>脚本跟踪和日志记录

尽管 PowerShell 已经具有 LogPipelineExecutionDetails  组策略设置用以记录 cmdlet 的调用，但 PowerShell 的脚本语言仍有多个你可能想记录和审核的功能。 新的“详细脚本跟踪”功能提供系统上的 PowerShell 脚本活动的详细跟踪和分析。 在启用详细脚本跟踪后，PowerShell 会将所有脚本块记录到 Microsoft-Windows-PowerShell/Operational  的 ETW 事件日志中。 如果脚本块创建另一个脚本块（例如，调用 `Invoke-Expression`），则也会记录调用的脚本块。

可以通过“打开 PowerShell 脚本块日志记录”  组策略设置（位于“管理模板” **“Windows 组件”** “Windows PowerShell”中）来启用日志记录。 ->    ->  

这些事件是：

| Channel |                               可运行                               |
| ------- | ----------------------------------------------------------------------- |
| 级别   | “详细”                                                                 |
| 操作码  | 创建                                                                  |
| 任务    | CommandStart                                                            |
| 关键字 | Runspace                                                                |
| EventId | Engine_ScriptBlockCompiled (0x1008 = 4104)                              |
| 消息 | 创建脚本块文本 (%1/%2)： </br> %3 </br> ScriptBlock ID：%4 |

消息中嵌入的文本是编译的脚本块的范围。 该 ID 是脚本块生存期内保留的 GUID。

当启用 verbose 日志记录时，此功能将写入开始和结束标记：

| Channel |                                 可运行                                |
| ------- | -------------------------------------------------------------------------- |
| 级别   | “详细”                                                                    |
| 操作码  | 打开/关闭                                                               |
| 任务    | CommandStart/CommandStop                                                 |
| 关键字 | Runspace                                                                   |
| EventId | ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) / </br> ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106) |
| 消息 | 已开始/已完成对 ScriptBlock ID 的调用：%1 </br> Runspace ID：%2 |

该 ID 是表示脚本块的 GUID（可以与事件 ID 0x1008 相关联），且 Runspace ID 表示该脚本块在其中运行的运行空间。

调用消息中的百分号表示结构化的 ETW 属性。 虽然它们会被消息文本中的实际值替换，但访问它们更可靠的的方式是，使用 Get-WinEvent cmdlet 检索消息，然后使用消息的  “属性”数组。

下例描述了该功能如何帮助取消对脚本进行加密和模糊化的恶意尝试：

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)
}

$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
Invoke-Expression $decrypted
```

运行它将生成以下日志条目：

```Output
Compiling Scriptblock text (1 of 1):
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)
    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)

}
ScriptBlock ID: ad8ae740-1f33-42aa-8dfc-1314411877e3

Compiling Scriptblock text (1 of 1):
$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
ScriptBlock ID: ba11c155-d34c-4004-88e3-6502ecb50f52

Compiling Scriptblock text (1 of 1):
Invoke-Expression $decrypted
ScriptBlock ID: 856c01ca-85d7-4989-b47f-e6a09ee4eeb3

Compiling Scriptblock text (1 of 1):
Write-Host 'Pwnd'
ScriptBlock ID: 5e618414-4e77-48e3-8f65-9a863f54b4c8
```

如果脚本块的长度超出单个事件所能支持的长度，PowerShell 会将脚本分成多个部分。 下面是从其日志消息中重组脚本的示例代码：

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

正如所有日志系统都有一个有限的保留缓存区一样，攻击此基础结构的一种方式就是，用虚假事件充斥日志以隐藏早期的证据。 若要避免这种攻击，请确保具有某种形式的事件日志集合设置（即 Windows 事件转发）。 有关详细信息，请参阅[通过 Windows 事件日志监视发现攻击者](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)。
