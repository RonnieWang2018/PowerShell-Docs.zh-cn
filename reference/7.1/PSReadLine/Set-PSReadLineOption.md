---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 06/30/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlineoption?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineOption
ms.openlocfilehash: 4c1c6712966d78f9af4f0c1ff181bf1869c01eea
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2020
ms.locfileid: "93200673"
---
# <span data-ttu-id="9aba8-103">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="9aba8-103">Set-PSReadLineOption</span></span>

## <span data-ttu-id="9aba8-104">摘要</span><span class="sxs-lookup"><span data-stu-id="9aba8-104">Synopsis</span></span>
<span data-ttu-id="9aba8-105">自定义 **PSReadLine** 中命令行编辑的行为。</span><span class="sxs-lookup"><span data-stu-id="9aba8-105">Customizes the behavior of command line editing in **PSReadLine** .</span></span>

## <span data-ttu-id="9aba8-106">语法</span><span class="sxs-lookup"><span data-stu-id="9aba8-106">Syntax</span></span>

```
Set-PSReadLineOption [-EditMode <EditMode>] [-ContinuationPrompt <String>] [-HistoryNoDuplicates]
 [-AddToHistoryHandler <System.Func[System.String,System.Object]>]
 [-CommandValidationHandler <System.Action[System.Management.Automation.Language.CommandAst]>]
 [-HistorySearchCursorMovesToEnd] [-MaximumHistoryCount <Int32>] [-MaximumKillRingCount <Int32>]
 [-ShowToolTips] [-ExtraPromptLineCount <Int32>] [-DingTone <Int32>] [-DingDuration <Int32>]
 [-BellStyle <BellStyle>] [-CompletionQueryItems <Int32>] [-WordDelimiters <String>]
 [-HistorySearchCaseSensitive] [-HistorySaveStyle <HistorySaveStyle>] [-HistorySavePath <String>]
 [-AnsiEscapeTimeout <Int32>] [-PromptText <String[]>] [-ViModeIndicator <ViModeStyle>]
 [-ViModeChangeHandler <ScriptBlock>] [-Colors <Hashtable>] [-PredictionSource <PredictionSource>]
 [<CommonParameters>]
```

## <span data-ttu-id="9aba8-107">说明</span><span class="sxs-lookup"><span data-stu-id="9aba8-107">Description</span></span>

<span data-ttu-id="9aba8-108">`Set-PSReadLineOption`当你编辑该命令行时，该 cmdlet 将自定义 **PSReadLine** 模块的行为。</span><span class="sxs-lookup"><span data-stu-id="9aba8-108">The `Set-PSReadLineOption` cmdlet customizes the behavior of the **PSReadLine** module when you're editing the command line.</span></span> <span data-ttu-id="9aba8-109">若要查看 **PSReadLine** 设置，请使用 `Get-PSReadLineOption` 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-109">To view the **PSReadLine** settings, use `Get-PSReadLineOption`.</span></span>

## <span data-ttu-id="9aba8-110">示例</span><span class="sxs-lookup"><span data-stu-id="9aba8-110">Examples</span></span>

### <span data-ttu-id="9aba8-111">示例1：设置前景色和背景色</span><span class="sxs-lookup"><span data-stu-id="9aba8-111">Example 1: Set foreground and background colors</span></span>

<span data-ttu-id="9aba8-112">此示例将 **PSReadLine** 设置为显示灰色背景上带有绿色前景文本的 **注释** 标记。</span><span class="sxs-lookup"><span data-stu-id="9aba8-112">This example sets **PSReadLine** to display the **Comment** token with green foreground text on a gray background.</span></span> <span data-ttu-id="9aba8-113">在示例中使用的转义序列中， **32** 表示前景色， **47** 表示背景色。</span><span class="sxs-lookup"><span data-stu-id="9aba8-113">In the escape sequence used in the example, **32** represents the foreground color and **47** represents the background color.</span></span>

```powershell
Set-PSReadLineOption -Colors @{ "Comment"="`e[32;47m" }
```

<span data-ttu-id="9aba8-114">您可以选择仅设置前景文本颜色。</span><span class="sxs-lookup"><span data-stu-id="9aba8-114">You can choose to set only a foreground text color.</span></span> <span data-ttu-id="9aba8-115">例如， **注释** 标记的浅绿色前景文本颜色： ``"Comment"="`e[92m"`` 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-115">For example, a bright green foreground text color for the **Comment** token: ``"Comment"="`e[92m"``.</span></span>

### <span data-ttu-id="9aba8-116">示例2：设置铃声样式</span><span class="sxs-lookup"><span data-stu-id="9aba8-116">Example 2: Set bell style</span></span>

<span data-ttu-id="9aba8-117">在此示例中， **PSReadLine** 将响应需要用户注意的错误或情况。</span><span class="sxs-lookup"><span data-stu-id="9aba8-117">In this example, **PSReadLine** will respond to errors or conditions that require user attention.</span></span>
<span data-ttu-id="9aba8-118">**BellStyle** 设置为在 1221 Hz 为60毫秒发出嘟嘟声。</span><span class="sxs-lookup"><span data-stu-id="9aba8-118">The **BellStyle** is set to emit an audible beep at 1221 Hz for 60 ms.</span></span>

```powershell
Set-PSReadLineOption -BellStyle Audible -DingTone 1221 -DingDuration 60
```

> [!NOTE]
> <span data-ttu-id="9aba8-119">此功能可能不适用于平台上的所有主机。</span><span class="sxs-lookup"><span data-stu-id="9aba8-119">This feature may not work in all hosts on platforms.</span></span>

### <span data-ttu-id="9aba8-120">示例3：设置多个选项</span><span class="sxs-lookup"><span data-stu-id="9aba8-120">Example 3: Set multiple options</span></span>

<span data-ttu-id="9aba8-121">`Set-PSReadLineOption` 可以设置具有哈希表的多个选项。</span><span class="sxs-lookup"><span data-stu-id="9aba8-121">`Set-PSReadLineOption` can set multiple options with a hash table.</span></span>

```powershell
$PSReadLineOptions = @{
    EditMode = "Emacs"
    HistoryNoDuplicates = $true
    HistorySearchCursorMovesToEnd = $true
    Colors = @{
        "Command" = "#8181f7"
    }
}
Set-PSReadLineOption @PSReadLineOptions
```

<span data-ttu-id="9aba8-122">`$PSReadLineOptions`哈希表设置键和值。</span><span class="sxs-lookup"><span data-stu-id="9aba8-122">The `$PSReadLineOptions` hash table sets the keys and values.</span></span> <span data-ttu-id="9aba8-123">`Set-PSReadLineOption` 使用的键和值 `@PSReadLineOptions` 来更新 **PSReadLine** 选项。</span><span class="sxs-lookup"><span data-stu-id="9aba8-123">`Set-PSReadLineOption` uses the keys and values with `@PSReadLineOptions` to update the **PSReadLine** options.</span></span>

<span data-ttu-id="9aba8-124">可以 `$PSReadLineOptions` 在 PowerShell 命令行上查看输入哈希表名称的键和值。</span><span class="sxs-lookup"><span data-stu-id="9aba8-124">You can view the keys and values entering the hash table name, `$PSReadLineOptions` on the PowerShell command line.</span></span>

### <span data-ttu-id="9aba8-125">示例4：设置多个颜色选项</span><span class="sxs-lookup"><span data-stu-id="9aba8-125">Example 4: Set multiple color options</span></span>

<span data-ttu-id="9aba8-126">此示例演示如何在单个命令中设置多个颜色值。</span><span class="sxs-lookup"><span data-stu-id="9aba8-126">This example shows how to set more than one color value in a single command.</span></span>

```powershell
Set-PSReadLineOption -Colors @{
  Command            = 'Magenta'
  Number             = 'DarkGray'
  Member             = 'DarkGray'
  Operator           = 'DarkGray'
  Type               = 'DarkGray'
  Variable           = 'DarkGreen'
  Parameter          = 'DarkGreen'
  ContinuationPrompt = 'DarkGray'
  Default            = 'DarkGray'
}
```

### <span data-ttu-id="9aba8-127">示例5：设置多个类型的颜色值</span><span class="sxs-lookup"><span data-stu-id="9aba8-127">Example 5: Set color values for multiple types</span></span>

<span data-ttu-id="9aba8-128">此示例显示了三种不同的方法，说明如何设置 **PSReadLine** 中显示的标记的颜色。</span><span class="sxs-lookup"><span data-stu-id="9aba8-128">This example shows three different methods for how to set the color of tokens displayed in **PSReadLine** .</span></span>

```powershell
Set-PSReadLineOption -Colors @{
 # Use a ConsoleColor enum
 "Error" = [ConsoleColor]::DarkRed

 # 24 bit color escape sequence
 "String" = "$([char]0x1b)[38;5;100m"

 # RGB value
 "Command" = "#8181f7"
}
```

### <span data-ttu-id="9aba8-129">示例6：使用 ViModeChangeHandler 显示 Vi 模式更改</span><span class="sxs-lookup"><span data-stu-id="9aba8-129">Example 6: Use ViModeChangeHandler to display Vi mode changes</span></span>

<span data-ttu-id="9aba8-130">此示例将发出一个游标更改 VT 转义，以响应 **Vi** 模式更改。</span><span class="sxs-lookup"><span data-stu-id="9aba8-130">This example emits a cursor change VT escape in response to a **Vi** mode change.</span></span>

```powershell
function OnViModeChange {
    if ($args[0] -eq 'Command') {
        # Set the cursor to a blinking block.
        Write-Host -NoNewLine "`e[1 q"
    } else {
        # Set the cursor to a blinking line.
        Write-Host -NoNewLine "`e[5 q"
    }
}
Set-PSReadLineOption -ViModeIndicator Script -ViModeChangeHandler $Function:OnViModeChange
```

<span data-ttu-id="9aba8-131">**OnViModeChange** 函数设置用于 **Vi** 模式的游标选项： insert 和 command。</span><span class="sxs-lookup"><span data-stu-id="9aba8-131">The **OnViModeChange** function sets the cursor options for the **Vi** modes: insert and command.</span></span>
<span data-ttu-id="9aba8-132">**ViModeChangeHandler** 使用 `Function:` 提供程序将 **OnViModeChange** 引用为脚本块对象。</span><span class="sxs-lookup"><span data-stu-id="9aba8-132">**ViModeChangeHandler** uses the `Function:` provider to reference **OnViModeChange** as a script block object.</span></span>

<span data-ttu-id="9aba8-133">有关详细信息，请参阅 [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)。</span><span class="sxs-lookup"><span data-stu-id="9aba8-133">For more information, see [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).</span></span>

## <span data-ttu-id="9aba8-134">parameters</span><span class="sxs-lookup"><span data-stu-id="9aba8-134">Parameters</span></span>

### <span data-ttu-id="9aba8-135">-AddToHistoryHandler</span><span class="sxs-lookup"><span data-stu-id="9aba8-135">-AddToHistoryHandler</span></span>

<span data-ttu-id="9aba8-136">指定控制哪些命令将添加到 **PSReadLine** 历史记录的 **ScriptBlock** 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-136">Specifies a **ScriptBlock** that controls which commands get added to **PSReadLine** history.</span></span>

<span data-ttu-id="9aba8-137">**ScriptBlock** 接收命令行作为输入。</span><span class="sxs-lookup"><span data-stu-id="9aba8-137">The **ScriptBlock** receives the command line as input.</span></span> <span data-ttu-id="9aba8-138">如果 **ScriptBlock** 返回 `$True` ，则会将命令行添加到历史记录中。</span><span class="sxs-lookup"><span data-stu-id="9aba8-138">If the **ScriptBlock** returns `$True`, the command line is added to the history.</span></span>

```yaml
Type: System.Func`2[System.String,System.Object]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-139">-AnsiEscapeTimeout</span><span class="sxs-lookup"><span data-stu-id="9aba8-139">-AnsiEscapeTimeout</span></span>

<span data-ttu-id="9aba8-140">此选项在重定向输入时（例如，在或下运行时）特定于 Windows `tmux` `screen` 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-140">This option is specific to Windows when input is redirected, for example, when running under `tmux` or `screen`.</span></span>

<span data-ttu-id="9aba8-141">使用 Windows 上的重定向输入时，会以转义符开头的字符序列发送多个密钥。</span><span class="sxs-lookup"><span data-stu-id="9aba8-141">With redirected input on Windows, many keys are sent as a sequence of characters starting with the escape character.</span></span> <span data-ttu-id="9aba8-142">不可能区分后跟多个字符和有效转义序列的单个转义字符。</span><span class="sxs-lookup"><span data-stu-id="9aba8-142">It's impossible to distinguish between a single escape character followed by more characters and a valid escape sequence.</span></span>

<span data-ttu-id="9aba8-143">假设终端发送字符的速度比用户类型要快。</span><span class="sxs-lookup"><span data-stu-id="9aba8-143">The assumption is that the terminal can send the characters faster than a user types.</span></span> <span data-ttu-id="9aba8-144">**PSReadLine** 在结束之前将等待此超时，直到它收到了一个完整的转义序列。</span><span class="sxs-lookup"><span data-stu-id="9aba8-144">**PSReadLine** waits for this timeout before concluding that it has received a complete escape sequence.</span></span>

<span data-ttu-id="9aba8-145">如果在键入时看到随机或意外的字符，则可以调整此超时值。</span><span class="sxs-lookup"><span data-stu-id="9aba8-145">If you see random or unexpected characters when you type, you can adjust this timeout.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-146">-BellStyle</span><span class="sxs-lookup"><span data-stu-id="9aba8-146">-BellStyle</span></span>

<span data-ttu-id="9aba8-147">指定 **PSReadLine** 如何响应各种错误和不明确的情况。</span><span class="sxs-lookup"><span data-stu-id="9aba8-147">Specifies how **PSReadLine** responds to various error and ambiguous conditions.</span></span>

<span data-ttu-id="9aba8-148">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="9aba8-148">The valid values are as follows:</span></span>

- <span data-ttu-id="9aba8-149">**声响** ：短时间提示音。</span><span class="sxs-lookup"><span data-stu-id="9aba8-149">**Audible** : A short beep.</span></span>
- <span data-ttu-id="9aba8-150">**视觉对象** ：文本短暂闪烁。</span><span class="sxs-lookup"><span data-stu-id="9aba8-150">**Visual** : Text flashes briefly.</span></span>
- <span data-ttu-id="9aba8-151">**无** ：无反馈。</span><span class="sxs-lookup"><span data-stu-id="9aba8-151">**None** : No feedback.</span></span>

```yaml
Type: Microsoft.PowerShell.BellStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Audible
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-152">-颜色</span><span class="sxs-lookup"><span data-stu-id="9aba8-152">-Colors</span></span>

<span data-ttu-id="9aba8-153">**Colors** 参数指定 **PSReadLine** 使用的各种颜色。</span><span class="sxs-lookup"><span data-stu-id="9aba8-153">The **Colors** parameter specifies various colors used by **PSReadLine** .</span></span>

<span data-ttu-id="9aba8-154">参数是一个哈希表，其中的键指定哪个元素和值指定了颜色。</span><span class="sxs-lookup"><span data-stu-id="9aba8-154">The argument is a hash table where the keys specify which element and the values specify the color.</span></span>
<span data-ttu-id="9aba8-155">有关详细信息，请参阅 [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables)。</span><span class="sxs-lookup"><span data-stu-id="9aba8-155">For more information, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="9aba8-156">颜色既可以是 **ConsoleColor** 中的值，也可以是 `[ConsoleColor]::Red` 有效的 ANSI 转义序列。</span><span class="sxs-lookup"><span data-stu-id="9aba8-156">Colors can be either a value from **ConsoleColor** , for example `[ConsoleColor]::Red`, or a valid ANSI escape sequence.</span></span> <span data-ttu-id="9aba8-157">有效的转义序列取决于你的终端。</span><span class="sxs-lookup"><span data-stu-id="9aba8-157">Valid escape sequences depend on your terminal.</span></span> <span data-ttu-id="9aba8-158">在 PowerShell 5.0 中，红色文本的示例转义序列是 `$([char]0x1b)[91m` 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-158">In PowerShell 5.0, an example escape sequence for red text is `$([char]0x1b)[91m`.</span></span> <span data-ttu-id="9aba8-159">在 PowerShell 6 及更高版本中，同一转义序列是 `` `e[91m`` 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-159">In PowerShell 6 and above, the same escape sequence is `` `e[91m``.</span></span> <span data-ttu-id="9aba8-160">可以指定其他转义序列，包括以下类型：</span><span class="sxs-lookup"><span data-stu-id="9aba8-160">You can specify other escape sequences including the following types:</span></span>

- <span data-ttu-id="9aba8-161">256颜色</span><span class="sxs-lookup"><span data-stu-id="9aba8-161">256 color</span></span>
- <span data-ttu-id="9aba8-162">24位颜色</span><span class="sxs-lookup"><span data-stu-id="9aba8-162">24-bit color</span></span>
- <span data-ttu-id="9aba8-163">前景、背景或两者</span><span class="sxs-lookup"><span data-stu-id="9aba8-163">Foreground, background, or both</span></span>
- <span data-ttu-id="9aba8-164">反色、粗体</span><span class="sxs-lookup"><span data-stu-id="9aba8-164">Inverse, bold</span></span>

<span data-ttu-id="9aba8-165">有关 ANSI 颜色代码的详细信息，请参阅维基百科中的 [ansi 转义码](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-165">For more information about ANSI color codes, see [ANSI escape code](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) in Wikipedia.</span></span>

<span data-ttu-id="9aba8-166">有效的密钥包括：</span><span class="sxs-lookup"><span data-stu-id="9aba8-166">The valid keys include:</span></span>

- <span data-ttu-id="9aba8-167">**ContinuationPrompt** ：继续提示的颜色。</span><span class="sxs-lookup"><span data-stu-id="9aba8-167">**ContinuationPrompt** : The color of the continuation prompt.</span></span>
- <span data-ttu-id="9aba8-168">**强调** ：强调颜色。</span><span class="sxs-lookup"><span data-stu-id="9aba8-168">**Emphasis** : The emphasis color.</span></span> <span data-ttu-id="9aba8-169">例如，在搜索历史记录时匹配文本。</span><span class="sxs-lookup"><span data-stu-id="9aba8-169">For example, the matching text when searching history.</span></span>
- <span data-ttu-id="9aba8-170">**错误** ：错误颜色。</span><span class="sxs-lookup"><span data-stu-id="9aba8-170">**Error** : The error color.</span></span> <span data-ttu-id="9aba8-171">例如，在提示符下。</span><span class="sxs-lookup"><span data-stu-id="9aba8-171">For example, in the prompt.</span></span>
- <span data-ttu-id="9aba8-172">**选择** ：突出显示菜单选择或选定文本的颜色。</span><span class="sxs-lookup"><span data-stu-id="9aba8-172">**Selection** : The color to highlight the menu selection or selected text.</span></span>
- <span data-ttu-id="9aba8-173">**默认** 值：默认标记颜色。</span><span class="sxs-lookup"><span data-stu-id="9aba8-173">**Default** : The default token color.</span></span>
- <span data-ttu-id="9aba8-174">**Comment** ：注释标记颜色。</span><span class="sxs-lookup"><span data-stu-id="9aba8-174">**Comment** : The comment token color.</span></span>
- <span data-ttu-id="9aba8-175">**关键字** ：关键字标记颜色。</span><span class="sxs-lookup"><span data-stu-id="9aba8-175">**Keyword** : The keyword token color.</span></span>
- <span data-ttu-id="9aba8-176">**String** ：字符串标记颜色。</span><span class="sxs-lookup"><span data-stu-id="9aba8-176">**String** : The string token color.</span></span>
- <span data-ttu-id="9aba8-177">**运算符** ：运算符标记颜色。</span><span class="sxs-lookup"><span data-stu-id="9aba8-177">**Operator** : The operator token color.</span></span>
- <span data-ttu-id="9aba8-178">**变量** ：变量标记颜色。</span><span class="sxs-lookup"><span data-stu-id="9aba8-178">**Variable** : The variable token color.</span></span>
- <span data-ttu-id="9aba8-179">**命令** ：命令标记颜色。</span><span class="sxs-lookup"><span data-stu-id="9aba8-179">**Command** : The command token color.</span></span>
- <span data-ttu-id="9aba8-180">**参数** ：参数标记颜色。</span><span class="sxs-lookup"><span data-stu-id="9aba8-180">**Parameter** : The parameter token color.</span></span>
- <span data-ttu-id="9aba8-181">**类型** ：类型标记颜色。</span><span class="sxs-lookup"><span data-stu-id="9aba8-181">**Type** : The type token color.</span></span>
- <span data-ttu-id="9aba8-182">**Number** ：数字标记颜色。</span><span class="sxs-lookup"><span data-stu-id="9aba8-182">**Number** : The number token color.</span></span>
- <span data-ttu-id="9aba8-183">**Member** ：成员名称令牌颜色。</span><span class="sxs-lookup"><span data-stu-id="9aba8-183">**Member** : The member name token color.</span></span>
- <span data-ttu-id="9aba8-184">**InlinePrediction** ：预测建议的内嵌视图的颜色。</span><span class="sxs-lookup"><span data-stu-id="9aba8-184">**InlinePrediction** : The color for the inline view of the predictive suggestion.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-185">-CommandValidationHandler</span><span class="sxs-lookup"><span data-stu-id="9aba8-185">-CommandValidationHandler</span></span>

<span data-ttu-id="9aba8-186">指定从 **ValidateAndAcceptLine** 调用的 **ScriptBlock** 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-186">Specifies a **ScriptBlock** that is called from **ValidateAndAcceptLine** .</span></span> <span data-ttu-id="9aba8-187">如果引发异常，验证将失败并报告错误。</span><span class="sxs-lookup"><span data-stu-id="9aba8-187">If an exception is thrown, validation fails and the error is reported.</span></span>

<span data-ttu-id="9aba8-188">在引发异常之前，验证处理程序可以将光标置于错误的点，以便更轻松地进行修复。</span><span class="sxs-lookup"><span data-stu-id="9aba8-188">Before throwing an exception, the validation handler can place the cursor at the point of the error to make it easier to fix.</span></span> <span data-ttu-id="9aba8-189">验证处理程序还可以更改命令行，如更正常见的录入错误。</span><span class="sxs-lookup"><span data-stu-id="9aba8-189">A validation handler can also change the command line, such as to correct common typographical errors.</span></span>

<span data-ttu-id="9aba8-190">**ValidateAndAcceptLine** 用于避免使用无法使用的命令使历史记录混乱。</span><span class="sxs-lookup"><span data-stu-id="9aba8-190">**ValidateAndAcceptLine** is used to avoid cluttering your history with commands that can't work.</span></span>

```yaml
Type: System.Action`1[System.Management.Automation.Language.CommandAst]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-191">-CompletionQueryItems</span><span class="sxs-lookup"><span data-stu-id="9aba8-191">-CompletionQueryItems</span></span>

<span data-ttu-id="9aba8-192">指定在不提示的情况下显示的最大完成项数。</span><span class="sxs-lookup"><span data-stu-id="9aba8-192">Specifies the maximum number of completion items that are shown without prompting.</span></span>

<span data-ttu-id="9aba8-193">如果要显示的项的数目大于此值， **PSReadLine** 将在显示完成项之前提示 **"是/否** "。</span><span class="sxs-lookup"><span data-stu-id="9aba8-193">If the number of items to show is greater than this value, **PSReadLine** prompts **yes/no** before displaying the completion items.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-194">-ContinuationPrompt</span><span class="sxs-lookup"><span data-stu-id="9aba8-194">-ContinuationPrompt</span></span>

<span data-ttu-id="9aba8-195">指定输入多行输入时在后续行开头显示的字符串。</span><span class="sxs-lookup"><span data-stu-id="9aba8-195">Specifies the string displayed at the beginning of the subsequent lines when multi-line input is entered.</span></span> <span data-ttu-id="9aba8-196">默认值为 double 大于符号 (`>>`) 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-196">The default is double greater-than signs (`>>`).</span></span> <span data-ttu-id="9aba8-197">空字符串有效。</span><span class="sxs-lookup"><span data-stu-id="9aba8-197">An empty string is valid.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >>
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-198">-DingDuration</span><span class="sxs-lookup"><span data-stu-id="9aba8-198">-DingDuration</span></span>

<span data-ttu-id="9aba8-199">指定当 **BellStyle** 设置为 "可 **听见** " 时提示音的持续时间。</span><span class="sxs-lookup"><span data-stu-id="9aba8-199">Specifies the duration of the beep when **BellStyle** is set to **Audible** .</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 50ms
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-200">-DingTone</span><span class="sxs-lookup"><span data-stu-id="9aba8-200">-DingTone</span></span>

<span data-ttu-id="9aba8-201">指定 **BellStyle** 设置为 "可 **听见** " 时提示音 (Hz) 的色调。</span><span class="sxs-lookup"><span data-stu-id="9aba8-201">Specifies the tone in Hertz (Hz) of the beep when **BellStyle** is set to **Audible** .</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1221
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-202">-EditMode</span><span class="sxs-lookup"><span data-stu-id="9aba8-202">-EditMode</span></span>

<span data-ttu-id="9aba8-203">指定命令行编辑模式。</span><span class="sxs-lookup"><span data-stu-id="9aba8-203">Specifies the command line editing mode.</span></span> <span data-ttu-id="9aba8-204">使用此参数将重置任何由设置的键绑定 `Set-PSReadLineKeyHandler` 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-204">Using this parameter resets any key bindings set by `Set-PSReadLineKeyHandler`.</span></span>

<span data-ttu-id="9aba8-205">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="9aba8-205">The valid values are as follows:</span></span>

- <span data-ttu-id="9aba8-206">**Windows** ：键绑定模拟 PowerShell、Cmd 和 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="9aba8-206">**Windows** : Key bindings emulate PowerShell, cmd, and Visual Studio.</span></span>
- <span data-ttu-id="9aba8-207">**Emacs** ：键绑定模拟 Bash 或 Emacs。</span><span class="sxs-lookup"><span data-stu-id="9aba8-207">**Emacs** : Key bindings emulate Bash or Emacs.</span></span>
- <span data-ttu-id="9aba8-208">**Vi** ：键绑定模拟 Vi。</span><span class="sxs-lookup"><span data-stu-id="9aba8-208">**Vi** : Key bindings emulate Vi.</span></span>

<span data-ttu-id="9aba8-209">使用 `Get-PSReadLineKeyHandler` 可查看当前配置的 **EditMode** 的键绑定。</span><span class="sxs-lookup"><span data-stu-id="9aba8-209">Use `Get-PSReadLineKeyHandler` to see the key bindings for the currently configured **EditMode** .</span></span>

```yaml
Type: Microsoft.PowerShell.EditMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-210">-ExtraPromptLineCount</span><span class="sxs-lookup"><span data-stu-id="9aba8-210">-ExtraPromptLineCount</span></span>

<span data-ttu-id="9aba8-211">指定额外行的数目。</span><span class="sxs-lookup"><span data-stu-id="9aba8-211">Specifies the number of extra lines.</span></span>

<span data-ttu-id="9aba8-212">如果提示跨多行，请为此参数指定一个值。</span><span class="sxs-lookup"><span data-stu-id="9aba8-212">If your prompt spans more than one line, specify a value for this parameter.</span></span> <span data-ttu-id="9aba8-213">如果希望在显示某些输出后 **PSReadLine** 显示提示时提供额外的行，请使用此选项。</span><span class="sxs-lookup"><span data-stu-id="9aba8-213">Use this option when you want extra lines to be available when **PSReadLine** displays the prompt after showing some output.</span></span> <span data-ttu-id="9aba8-214">例如， **PSReadLine** 返回完成列表。</span><span class="sxs-lookup"><span data-stu-id="9aba8-214">For example, **PSReadLine** returns a list of completions.</span></span>

<span data-ttu-id="9aba8-215">在以前版本的 **PSReadLine** 中需要此选项，但在使用函数时，此选项很有用 `InvokePrompt` 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-215">This option is needed less than in previous versions of **PSReadLine** , but is useful when the `InvokePrompt` function is used.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-216">-HistoryNoDuplicates</span><span class="sxs-lookup"><span data-stu-id="9aba8-216">-HistoryNoDuplicates</span></span>

<span data-ttu-id="9aba8-217">此选项控制回调行为。</span><span class="sxs-lookup"><span data-stu-id="9aba8-217">This option controls the recall behavior.</span></span> <span data-ttu-id="9aba8-218">重复的命令仍将添加到历史记录文件中。</span><span class="sxs-lookup"><span data-stu-id="9aba8-218">Duplicate commands are still added to the history file.</span></span>
<span data-ttu-id="9aba8-219">如果设置了此选项，则在调用命令时仅显示最新的调用。</span><span class="sxs-lookup"><span data-stu-id="9aba8-219">When this option is set, only the most recent invocation appears when recalling commands.</span></span> <span data-ttu-id="9aba8-220">重复执行的命令将添加到历史记录，以便在撤回期间保留排序。</span><span class="sxs-lookup"><span data-stu-id="9aba8-220">Repeated commands are added to history to preserve ordering during recall.</span></span> <span data-ttu-id="9aba8-221">但是，在调用或搜索历史记录时，通常不需要多次看到此命令。</span><span class="sxs-lookup"><span data-stu-id="9aba8-221">However, you typically don't want to see the command multiple times when recalling or searching the history.</span></span>

<span data-ttu-id="9aba8-222">默认情况下，global **PSConsoleReadLineOptions** 对象的 **HistoryNoDuplicates** 属性设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-222">By default, the **HistoryNoDuplicates** property of the global **PSConsoleReadLineOptions** object is set to `True`.</span></span> <span data-ttu-id="9aba8-223">使用此 **SwitchParameter** 会将属性值设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-223">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="9aba8-224">若要更改属性值，必须按如下所示指定 **SwitchParameter** 的值： `-HistoryNoDuplicates:$False` 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-224">To change the property value, you must specify the value of the **SwitchParameter** as follows: `-HistoryNoDuplicates:$False`.</span></span>

<span data-ttu-id="9aba8-225">使用以下命令，可以直接设置属性值：</span><span class="sxs-lookup"><span data-stu-id="9aba8-225">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).HistoryNoDuplicates = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-226">-HistorySavePath</span><span class="sxs-lookup"><span data-stu-id="9aba8-226">-HistorySavePath</span></span>

<span data-ttu-id="9aba8-227">指定保存历史记录的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="9aba8-227">Specifies the path to the file where history is saved.</span></span> <span data-ttu-id="9aba8-228">运行 Windows 或非 Windows 平台的计算机将文件存储在不同的位置。</span><span class="sxs-lookup"><span data-stu-id="9aba8-228">Computers running Windows or non-Windows platforms store the file in different locations.</span></span> <span data-ttu-id="9aba8-229">例如，filename 存储在一个变量中 `$($host.Name)_history.txt` `ConsoleHost_history.txt` 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-229">The filename is stored in a variable `$($host.Name)_history.txt`, for example `ConsoleHost_history.txt`.</span></span>

<span data-ttu-id="9aba8-230">如果不使用此参数，则默认路径如下所示：</span><span class="sxs-lookup"><span data-stu-id="9aba8-230">If you don't use this parameter, the default path is as follows:</span></span>

<span data-ttu-id="9aba8-231">**Windows**</span><span class="sxs-lookup"><span data-stu-id="9aba8-231">**Windows**</span></span>

`$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine\$($host.Name)_history.txt`

<span data-ttu-id="9aba8-232">**非 Windows**</span><span class="sxs-lookup"><span data-stu-id="9aba8-232">**non-Windows**</span></span>

`$env:XDG_DATA_HOME/powershell/PSReadLine\$($host.Name)_history.txt`

`$env:HOME/.local/share/powershell/PSReadLine\$($host.Name)_history.txt`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: A file named $($host.Name)_history.txt in $env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine on Windows and $env:XDG_DATA_HOME/powershell/PSReadLine or $env:HOME/.local/share/powershell/PSReadLine on non-Windows platforms
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-233">-HistorySaveStyle</span><span class="sxs-lookup"><span data-stu-id="9aba8-233">-HistorySaveStyle</span></span>

<span data-ttu-id="9aba8-234">指定 **PSReadLine** 如何保存历史记录。</span><span class="sxs-lookup"><span data-stu-id="9aba8-234">Specifies how **PSReadLine** saves history.</span></span>

<span data-ttu-id="9aba8-235">以下是有效值：</span><span class="sxs-lookup"><span data-stu-id="9aba8-235">Valid values are as follows:</span></span>

- <span data-ttu-id="9aba8-236">**SaveIncrementally** ：在每个命令执行后保存历史记录，并跨多个 PowerShell 实例共享。</span><span class="sxs-lookup"><span data-stu-id="9aba8-236">**SaveIncrementally** : Save history after each command is executed and share across multiple instances of PowerShell.</span></span>
- <span data-ttu-id="9aba8-237">**SaveAtExit** ： PowerShell 退出时追加历史记录文件。</span><span class="sxs-lookup"><span data-stu-id="9aba8-237">**SaveAtExit** : Append history file when PowerShell exits.</span></span>
- <span data-ttu-id="9aba8-238">**SaveNothing** ：不要使用历史记录文件。</span><span class="sxs-lookup"><span data-stu-id="9aba8-238">**SaveNothing** : Don't use a history file.</span></span>

```yaml
Type: Microsoft.PowerShell.HistorySaveStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SaveIncrementally
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-239">-HistorySearchCaseSensitive</span><span class="sxs-lookup"><span data-stu-id="9aba8-239">-HistorySearchCaseSensitive</span></span>

<span data-ttu-id="9aba8-240">指定在函数（如 **ReverseSearchHistory** 或 **HistorySearchBackward** ）中，历史记录搜索区分大小写。</span><span class="sxs-lookup"><span data-stu-id="9aba8-240">Specifies that history searching is case-sensitive in functions like **ReverseSearchHistory** or **HistorySearchBackward** .</span></span>

<span data-ttu-id="9aba8-241">默认情况下，global **PSConsoleReadLineOptions** 对象的 **HistorySearchCaseSensitive** 属性设置为 `False` 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-241">By default, the **HistorySearchCaseSensitive** property of the global **PSConsoleReadLineOptions** object is set to `False`.</span></span> <span data-ttu-id="9aba8-242">使用此 **SwitchParameter** 会将属性值设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-242">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="9aba8-243">若要更改属性值，必须按如下所示指定 **SwitchParameter** 的值： `-HistorySearchCaseSensitive:$False` 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-243">To change the property value back, you must specify the value of the **SwitchParameter** as follows: `-HistorySearchCaseSensitive:$False`.</span></span>

<span data-ttu-id="9aba8-244">使用以下命令，可以直接设置属性值：</span><span class="sxs-lookup"><span data-stu-id="9aba8-244">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).HistorySearchCaseSensitive = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-245">-HistorySearchCursorMovesToEnd</span><span class="sxs-lookup"><span data-stu-id="9aba8-245">-HistorySearchCursorMovesToEnd</span></span>

<span data-ttu-id="9aba8-246">指示光标移动到通过使用搜索从历史记录加载的命令的末尾。</span><span class="sxs-lookup"><span data-stu-id="9aba8-246">Indicates that the cursor moves to the end of commands that you load from history by using a search.</span></span>
<span data-ttu-id="9aba8-247">如果将此参数设置为 `$False` ，则光标将保持按向上或向下箭头时的位置。</span><span class="sxs-lookup"><span data-stu-id="9aba8-247">When this parameter is set to `$False`, the cursor remains at the position it was when you pressed the up or down arrows.</span></span>

<span data-ttu-id="9aba8-248">默认情况下，global **PSConsoleReadLineOptions** 对象的 **HistorySearchCursorMovesToEnd** 属性设置为 `False` 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-248">By default, the **HistorySearchCursorMovesToEnd** property of the global **PSConsoleReadLineOptions** object is set to `False`.</span></span> <span data-ttu-id="9aba8-249">使用此 **SwitchParameter** 将属性值设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-249">Using this **SwitchParameter** set the property value to `True`.</span></span> <span data-ttu-id="9aba8-250">若要更改属性值，必须按如下所示指定 **SwitchParameter** 的值： `-HistorySearchCursorMovesToEnd:$False` 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-250">To change the property value back, you must specify the value of the **SwitchParameter** as follows: `-HistorySearchCursorMovesToEnd:$False`.</span></span>

<span data-ttu-id="9aba8-251">使用以下命令，可以直接设置属性值：</span><span class="sxs-lookup"><span data-stu-id="9aba8-251">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).HistorySearchCursorMovesToEnd = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-252">-MaximumHistoryCount</span><span class="sxs-lookup"><span data-stu-id="9aba8-252">-MaximumHistoryCount</span></span>

<span data-ttu-id="9aba8-253">指定要在 **PSReadLine** 历史记录中保存的最大命令数。</span><span class="sxs-lookup"><span data-stu-id="9aba8-253">Specifies the maximum number of commands to save in **PSReadLine** history.</span></span>

<span data-ttu-id="9aba8-254">**PSReadLine** 历史记录独立于 PowerShell 历史记录。</span><span class="sxs-lookup"><span data-stu-id="9aba8-254">**PSReadLine** history is separate from PowerShell history.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-255">-MaximumKillRingCount</span><span class="sxs-lookup"><span data-stu-id="9aba8-255">-MaximumKillRingCount</span></span>

<span data-ttu-id="9aba8-256">指定存储在终止环中的最大项数。</span><span class="sxs-lookup"><span data-stu-id="9aba8-256">Specifies the maximum number of items stored in the kill ring.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-257">-PredictionSource</span><span class="sxs-lookup"><span data-stu-id="9aba8-257">-PredictionSource</span></span>

<span data-ttu-id="9aba8-258">指定 PSReadLine 的源以获取预测建议。</span><span class="sxs-lookup"><span data-stu-id="9aba8-258">Specifies the source for PSReadLine to get predictive suggestions.</span></span>

<span data-ttu-id="9aba8-259">有效值是：</span><span class="sxs-lookup"><span data-stu-id="9aba8-259">Valid values are:</span></span>

- <span data-ttu-id="9aba8-260">**无** ：禁用预测建议功能</span><span class="sxs-lookup"><span data-stu-id="9aba8-260">**None** : disable the predictive suggestion feature</span></span>
- <span data-ttu-id="9aba8-261">**历史记录** ：仅获取历史记录中的预测建议</span><span class="sxs-lookup"><span data-stu-id="9aba8-261">**History** : get predictive suggestions from history only</span></span>

```yaml
Type: PredictionSource
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-262">-PromptText</span><span class="sxs-lookup"><span data-stu-id="9aba8-262">-PromptText</span></span>

<span data-ttu-id="9aba8-263">出现分析错误时， **PSReadLine** 会将 "提示" 部分更改为 "红色"。</span><span class="sxs-lookup"><span data-stu-id="9aba8-263">When there's a parse error, **PSReadLine** changes a part of the prompt red.</span></span> <span data-ttu-id="9aba8-264">**PSReadLine** 分析 prompt 函数，以确定如何仅更改提示部分的颜色。</span><span class="sxs-lookup"><span data-stu-id="9aba8-264">**PSReadLine** analyzes your prompt function to determine how to change only the color of part of your prompt.</span></span> <span data-ttu-id="9aba8-265">此分析的可靠性不是100%。</span><span class="sxs-lookup"><span data-stu-id="9aba8-265">This analysis isn't 100% reliable.</span></span>

<span data-ttu-id="9aba8-266">如果 **PSReadLine** 以意外的方式更改提示，请使用此选项。</span><span class="sxs-lookup"><span data-stu-id="9aba8-266">Use this option if **PSReadLine** is changing your prompt in unexpected ways.</span></span> <span data-ttu-id="9aba8-267">包括任何尾随空格。</span><span class="sxs-lookup"><span data-stu-id="9aba8-267">Include any trailing whitespace.</span></span>

<span data-ttu-id="9aba8-268">例如，如果您的 prompt 函数如下例所示：</span><span class="sxs-lookup"><span data-stu-id="9aba8-268">For example, if your prompt function looked like the following example:</span></span>

`function prompt { Write-Host -NoNewLine -ForegroundColor Yellow "$pwd"; return "# " }`

<span data-ttu-id="9aba8-269">然后设置：</span><span class="sxs-lookup"><span data-stu-id="9aba8-269">Then set:</span></span>

`Set-PSReadLineOption -PromptText "# "`

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-270">-ShowToolTips</span><span class="sxs-lookup"><span data-stu-id="9aba8-270">-ShowToolTips</span></span>

<span data-ttu-id="9aba8-271">显示可能的完成时，工具提示将显示在完成列表中。</span><span class="sxs-lookup"><span data-stu-id="9aba8-271">When displaying possible completions, tooltips are shown in the list of completions.</span></span>

<span data-ttu-id="9aba8-272">默认情况下会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="9aba8-272">This option is enabled by default.</span></span> <span data-ttu-id="9aba8-273">默认情况下，在早期版本的 **PSReadLine** 中未启用此选项。</span><span class="sxs-lookup"><span data-stu-id="9aba8-273">This option wasn't enabled by default in prior versions of **PSReadLine** .</span></span> <span data-ttu-id="9aba8-274">若要禁用，请将此选项设置为 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-274">To disable, set this option to `$False`.</span></span>

<span data-ttu-id="9aba8-275">默认情况下，global **PSConsoleReadLineOptions** 对象的 **ShowToolTips** 属性设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-275">By default, the **ShowToolTips** property of the global **PSConsoleReadLineOptions** object is set to `True`.</span></span> <span data-ttu-id="9aba8-276">使用此 **SwitchParameter** 会将属性值设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-276">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="9aba8-277">若要更改属性值，必须按如下所示指定 **SwitchParameter** 的值： `-ShowToolTips:$False` 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-277">To change the property value, you must specify the value of the **SwitchParameter** as follows: `-ShowToolTips:$False`.</span></span>

<span data-ttu-id="9aba8-278">使用以下命令，可以直接设置属性值：</span><span class="sxs-lookup"><span data-stu-id="9aba8-278">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).ShowToolTips = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-279">-ViModeChangeHandler</span><span class="sxs-lookup"><span data-stu-id="9aba8-279">-ViModeChangeHandler</span></span>

<span data-ttu-id="9aba8-280">当 **ViModeIndicator** 设置为时 `Script` ，每次模式更改时将调用提供的脚本块。</span><span class="sxs-lookup"><span data-stu-id="9aba8-280">When the **ViModeIndicator** is set to `Script`, the script block provided will be invoked every time the mode changes.</span></span> <span data-ttu-id="9aba8-281">脚本块提供了一个类型为的参数 `ViMode` 。</span><span class="sxs-lookup"><span data-stu-id="9aba8-281">The script block is provided one argument of type `ViMode`.</span></span>

<span data-ttu-id="9aba8-282">此参数是在 PowerShell 7 中引入的。</span><span class="sxs-lookup"><span data-stu-id="9aba8-282">This parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-283">-ViModeIndicator</span><span class="sxs-lookup"><span data-stu-id="9aba8-283">-ViModeIndicator</span></span>

<span data-ttu-id="9aba8-284">此选项设置当前 **Vi** 模式的视觉指示。</span><span class="sxs-lookup"><span data-stu-id="9aba8-284">This option sets the visual indication for the current **Vi** mode.</span></span> <span data-ttu-id="9aba8-285">插入模式或命令模式。</span><span class="sxs-lookup"><span data-stu-id="9aba8-285">Either insert mode or command mode.</span></span>

<span data-ttu-id="9aba8-286">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="9aba8-286">The valid values are as follows:</span></span>

- <span data-ttu-id="9aba8-287">**无** ：无指示。</span><span class="sxs-lookup"><span data-stu-id="9aba8-287">**None** : There's no indication.</span></span>
- <span data-ttu-id="9aba8-288">**Prompt** ：提示更改颜色。</span><span class="sxs-lookup"><span data-stu-id="9aba8-288">**Prompt** : The prompt changes color.</span></span>
- <span data-ttu-id="9aba8-289">**Cursor** ：光标改变大小。</span><span class="sxs-lookup"><span data-stu-id="9aba8-289">**Cursor** : The cursor changes size.</span></span>
- <span data-ttu-id="9aba8-290">**脚本** ：打印用户指定的文本。</span><span class="sxs-lookup"><span data-stu-id="9aba8-290">**Script** : User-specified text is printed.</span></span>

```yaml
Type: Microsoft.PowerShell.ViModeStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-291">-WordDelimiters</span><span class="sxs-lookup"><span data-stu-id="9aba8-291">-WordDelimiters</span></span>

<span data-ttu-id="9aba8-292">指定分隔函数（如 **ForwardWord** 或 **KillWord** ）的字词的字符。</span><span class="sxs-lookup"><span data-stu-id="9aba8-292">Specifies the characters that delimit words for functions like **ForwardWord** or **KillWord** .</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: ;:,.[]{}()/\|^&*-=+'"–—―
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9aba8-293">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9aba8-293">CommonParameters</span></span>

<span data-ttu-id="9aba8-294">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9aba8-294">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9aba8-295">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="9aba8-295">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9aba8-296">输入</span><span class="sxs-lookup"><span data-stu-id="9aba8-296">Inputs</span></span>

### <span data-ttu-id="9aba8-297">无</span><span class="sxs-lookup"><span data-stu-id="9aba8-297">None</span></span>

<span data-ttu-id="9aba8-298">不能通过管道将对象传递给 `Set-PSReadLineOption.`</span><span class="sxs-lookup"><span data-stu-id="9aba8-298">You cannot pipe objects to `Set-PSReadLineOption.`</span></span>

## <span data-ttu-id="9aba8-299">Outputs</span><span class="sxs-lookup"><span data-stu-id="9aba8-299">Outputs</span></span>

### <span data-ttu-id="9aba8-300">无</span><span class="sxs-lookup"><span data-stu-id="9aba8-300">None</span></span>

<span data-ttu-id="9aba8-301">此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="9aba8-301">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="9aba8-302">注释</span><span class="sxs-lookup"><span data-stu-id="9aba8-302">Notes</span></span>

## <span data-ttu-id="9aba8-303">相关链接</span><span class="sxs-lookup"><span data-stu-id="9aba8-303">Related links</span></span>

[<span data-ttu-id="9aba8-304">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="9aba8-304">about_PSReadLine</span></span>](./About/about_PSReadLine.md)

[<span data-ttu-id="9aba8-305">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="9aba8-305">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="9aba8-306">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="9aba8-306">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="9aba8-307">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="9aba8-307">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="9aba8-308">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="9aba8-308">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
