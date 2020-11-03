---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlinekeyhandler?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineKeyHandler
ms.openlocfilehash: 7794fc8814364d3ee62b0dece787aa0213dc4ff3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93198157"
---
# <span data-ttu-id="d76c8-103">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="d76c8-103">Set-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="d76c8-104">摘要</span><span class="sxs-lookup"><span data-stu-id="d76c8-104">SYNOPSIS</span></span>
<span data-ttu-id="d76c8-105">将键绑定到用户定义的或 PSReadLine 的密钥处理程序函数。</span><span class="sxs-lookup"><span data-stu-id="d76c8-105">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

## <span data-ttu-id="d76c8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d76c8-106">SYNTAX</span></span>

### <span data-ttu-id="d76c8-107">脚本块</span><span class="sxs-lookup"><span data-stu-id="d76c8-107">ScriptBlock</span></span>

```
Set-PSReadLineKeyHandler [-ScriptBlock] <ScriptBlock> [-BriefDescription <String>]
 [-Description <String>] [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

### <span data-ttu-id="d76c8-108">函数</span><span class="sxs-lookup"><span data-stu-id="d76c8-108">Function</span></span>

```
Set-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [-Function] <String>
 [<CommonParameters>]
```

## <span data-ttu-id="d76c8-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d76c8-109">DESCRIPTION</span></span>

<span data-ttu-id="d76c8-110">`Set-PSReadLineKeyHandler`当按下键或键序列时，该 cmdlet 将自定义结果。</span><span class="sxs-lookup"><span data-stu-id="d76c8-110">The `Set-PSReadLineKeyHandler` cmdlet customizes the result when a key or sequence of keys is pressed.</span></span> <span data-ttu-id="d76c8-111">使用用户定义的键绑定，可以在 PowerShell 脚本中执行几乎所有的操作。</span><span class="sxs-lookup"><span data-stu-id="d76c8-111">With user-defined key bindings, you can do almost anything that is possible from within a PowerShell script.</span></span>

## <span data-ttu-id="d76c8-112">示例</span><span class="sxs-lookup"><span data-stu-id="d76c8-112">EXAMPLES</span></span>

### <span data-ttu-id="d76c8-113">示例1：将箭头键绑定到函数</span><span class="sxs-lookup"><span data-stu-id="d76c8-113">Example 1: Bind the arrow key to a function</span></span>

<span data-ttu-id="d76c8-114">此命令将向上箭头键绑定到 **HistorySearchBackward** 函数。</span><span class="sxs-lookup"><span data-stu-id="d76c8-114">This command binds the up arrow key to the **HistorySearchBackward** function.</span></span> <span data-ttu-id="d76c8-115">此函数搜索命令行中以命令行的当前内容开头的命令行的命令历史记录。</span><span class="sxs-lookup"><span data-stu-id="d76c8-115">This function searches command history for command lines that start with the current contents of the command line.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord UpArrow -Function HistorySearchBackward
```

### <span data-ttu-id="d76c8-116">示例2：将密钥绑定到脚本块</span><span class="sxs-lookup"><span data-stu-id="d76c8-116">Example 2: Bind a key to a script block</span></span>

<span data-ttu-id="d76c8-117">此示例演示如何使用单个键来运行命令。</span><span class="sxs-lookup"><span data-stu-id="d76c8-117">This example shows how a single key can be used to run a command.</span></span> <span data-ttu-id="d76c8-118">命令将键绑定 `Ctrl+B` 到一个清除行的脚本块，插入 "build" 一词，然后接受该行。</span><span class="sxs-lookup"><span data-stu-id="d76c8-118">The command binds the key `Ctrl+B` to a script block that clears the line, inserts the word "build", and then accepts the line.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord Ctrl+B -ScriptBlock {
    [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
    [Microsoft.PowerShell.PSConsoleReadLine]::Insert('build')
    [Microsoft.PowerShell.PSConsoleReadLine]::AcceptLine()
}
```

## <span data-ttu-id="d76c8-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d76c8-119">PARAMETERS</span></span>

### <span data-ttu-id="d76c8-120">-BriefDescription</span><span class="sxs-lookup"><span data-stu-id="d76c8-120">-BriefDescription</span></span>

<span data-ttu-id="d76c8-121">键绑定的简短说明。</span><span class="sxs-lookup"><span data-stu-id="d76c8-121">A brief description of the key binding.</span></span> <span data-ttu-id="d76c8-122">此说明由 `Get-PSReadLineKeyHandler` cmdlet 显示。</span><span class="sxs-lookup"><span data-stu-id="d76c8-122">This description is displayed by the `Get-PSReadLineKeyHandler` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d76c8-123">-弦</span><span class="sxs-lookup"><span data-stu-id="d76c8-123">-Chord</span></span>

<span data-ttu-id="d76c8-124">要绑定到函数或脚本块的键或键序列。</span><span class="sxs-lookup"><span data-stu-id="d76c8-124">The key or sequence of keys to be bound to a function or script block.</span></span> <span data-ttu-id="d76c8-125">使用单个字符串指定单个绑定。</span><span class="sxs-lookup"><span data-stu-id="d76c8-125">Use a single string to specify a single binding.</span></span> <span data-ttu-id="d76c8-126">如果绑定是键序列，请用逗号分隔键，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="d76c8-126">If the binding is a sequence of keys, separate the keys by a comma, as in the following example:</span></span>

`Ctrl+X,Ctrl+L`

<span data-ttu-id="d76c8-127">此参数接受字符串数组。</span><span class="sxs-lookup"><span data-stu-id="d76c8-127">This parameter accepts an array of strings.</span></span> <span data-ttu-id="d76c8-128">每个字符串都是一个单独的绑定，而不是单个绑定的键序列。</span><span class="sxs-lookup"><span data-stu-id="d76c8-128">Each string is a separate binding, not a sequence of keys for a single binding.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d76c8-129">-Description</span><span class="sxs-lookup"><span data-stu-id="d76c8-129">-Description</span></span>

<span data-ttu-id="d76c8-130">指定在 cmdlet 的输出中可见的键绑定的更详细说明 `Get-PSReadLineKeyHandler` 。</span><span class="sxs-lookup"><span data-stu-id="d76c8-130">Specifies a more detailed description of the key binding that is visible in the output of the `Get-PSReadLineKeyHandler` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases: LongDescription

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d76c8-131">-Function</span><span class="sxs-lookup"><span data-stu-id="d76c8-131">-Function</span></span>

<span data-ttu-id="d76c8-132">指定 PSReadLine 提供的现有密钥处理程序的名称。</span><span class="sxs-lookup"><span data-stu-id="d76c8-132">Specifies the name of an existing key handler provided by PSReadLine.</span></span> <span data-ttu-id="d76c8-133">此参数使你可以重新绑定现有的键绑定，或绑定当前未绑定的处理程序。</span><span class="sxs-lookup"><span data-stu-id="d76c8-133">This parameter lets you rebind existing key bindings, or bind a handler that is currently unbound.</span></span>

```yaml
Type: System.String
Parameter Sets: Function
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d76c8-134">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="d76c8-134">-ScriptBlock</span></span>

<span data-ttu-id="d76c8-135">指定输入弦时要运行的脚本块值。</span><span class="sxs-lookup"><span data-stu-id="d76c8-135">Specifies a script block value to run when the chord is entered.</span></span> <span data-ttu-id="d76c8-136">PSReadLine 将一个或两个参数传递给此脚本块。</span><span class="sxs-lookup"><span data-stu-id="d76c8-136">PSReadLine passes one or two parameters to this script block.</span></span> <span data-ttu-id="d76c8-137">第一个参数是 **ConsoleKeyInfo** 对象，表示按下的键。</span><span class="sxs-lookup"><span data-stu-id="d76c8-137">The first parameter is a **ConsoleKeyInfo** object representing the key pressed.</span></span> <span data-ttu-id="d76c8-138">第二个参数可以是任意对象，具体取决于上下文。</span><span class="sxs-lookup"><span data-stu-id="d76c8-138">The second argument can be any object depending on the context.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d76c8-139">-ViMode</span><span class="sxs-lookup"><span data-stu-id="d76c8-139">-ViMode</span></span>

<span data-ttu-id="d76c8-140">指定绑定应用于哪种 vi 模式。</span><span class="sxs-lookup"><span data-stu-id="d76c8-140">Specify which vi mode the binding applies to.</span></span>

<span data-ttu-id="d76c8-141">有效值是：</span><span class="sxs-lookup"><span data-stu-id="d76c8-141">Valid values are:</span></span>

- <span data-ttu-id="d76c8-142">插入</span><span class="sxs-lookup"><span data-stu-id="d76c8-142">Insert</span></span>
- <span data-ttu-id="d76c8-143">命令</span><span class="sxs-lookup"><span data-stu-id="d76c8-143">Command</span></span>

```yaml
Type: Microsoft.PowerShell.ViMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d76c8-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d76c8-144">CommonParameters</span></span>

<span data-ttu-id="d76c8-145">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d76c8-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d76c8-146">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d76c8-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d76c8-147">输入</span><span class="sxs-lookup"><span data-stu-id="d76c8-147">INPUTS</span></span>

### <span data-ttu-id="d76c8-148">无</span><span class="sxs-lookup"><span data-stu-id="d76c8-148">None</span></span>

<span data-ttu-id="d76c8-149">不能通过管道将对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d76c8-149">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="d76c8-150">输出</span><span class="sxs-lookup"><span data-stu-id="d76c8-150">OUTPUTS</span></span>

### <span data-ttu-id="d76c8-151">无</span><span class="sxs-lookup"><span data-stu-id="d76c8-151">None</span></span>

<span data-ttu-id="d76c8-152">此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="d76c8-152">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="d76c8-153">注释</span><span class="sxs-lookup"><span data-stu-id="d76c8-153">NOTES</span></span>

## <span data-ttu-id="d76c8-154">相关链接</span><span class="sxs-lookup"><span data-stu-id="d76c8-154">RELATED LINKS</span></span>

[<span data-ttu-id="d76c8-155">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="d76c8-155">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="d76c8-156">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="d76c8-156">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="d76c8-157">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="d76c8-157">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="d76c8-158">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="d76c8-158">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)