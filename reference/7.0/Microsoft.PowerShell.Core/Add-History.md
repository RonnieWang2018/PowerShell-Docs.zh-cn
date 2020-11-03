---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/add-history?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-History
ms.openlocfilehash: 1c0a4c958ae60ab6bde170a71f6bc69e09079074
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2020
ms.locfileid: "93197135"
---
# <span data-ttu-id="ff658-103">Add-History</span><span class="sxs-lookup"><span data-stu-id="ff658-103">Add-History</span></span>

## <span data-ttu-id="ff658-104">摘要</span><span class="sxs-lookup"><span data-stu-id="ff658-104">SYNOPSIS</span></span>
<span data-ttu-id="ff658-105">向会话历史记录附加条目。</span><span class="sxs-lookup"><span data-stu-id="ff658-105">Appends entries to the session history.</span></span>

## <span data-ttu-id="ff658-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ff658-106">SYNTAX</span></span>

```
Add-History [[-InputObject] <PSObject[]>] [-Passthru] [<CommonParameters>]
```

## <span data-ttu-id="ff658-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ff658-107">DESCRIPTION</span></span>

<span data-ttu-id="ff658-108">`Add-History`Cmdlet 将条目添加到会话历史记录的末尾，即在当前会话期间输入的命令的列表。</span><span class="sxs-lookup"><span data-stu-id="ff658-108">The `Add-History` cmdlet adds entries to the end of the session history, that is, the list of commands entered during the current session.</span></span>

<span data-ttu-id="ff658-109">会话历史记录是在会话期间输入的命令的列表。</span><span class="sxs-lookup"><span data-stu-id="ff658-109">The session history is a list of the commands entered during the session.</span></span> <span data-ttu-id="ff658-110">会话历史记录表示命令的执行顺序、状态以及开始和结束时间。</span><span class="sxs-lookup"><span data-stu-id="ff658-110">The session history represents the order of execution, the status, and the start and end times of the command.</span></span> <span data-ttu-id="ff658-111">当你输入每个命令时，PowerShell 会将其添加到历史记录，以便你可以重复使用它。</span><span class="sxs-lookup"><span data-stu-id="ff658-111">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="ff658-112">有关会话历史记录的详细信息，请参阅 [about_History](About/about_History.md)。</span><span class="sxs-lookup"><span data-stu-id="ff658-112">For more information about the session history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="ff658-113">会话历史记录与 **PSReadLine** 模块维护的历史记录分开管理。</span><span class="sxs-lookup"><span data-stu-id="ff658-113">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="ff658-114">在加载 **PSReadLine** 的会话中提供两个历史记录。</span><span class="sxs-lookup"><span data-stu-id="ff658-114">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="ff658-115">此 cmdlet 仅适用于会话历史记录。</span><span class="sxs-lookup"><span data-stu-id="ff658-115">This cmdlet only works with the session history.</span></span> <span data-ttu-id="ff658-116">有关详细信息，请参阅 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)。</span><span class="sxs-lookup"><span data-stu-id="ff658-116">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

<span data-ttu-id="ff658-117">你可以使用 `Get-History` cmdlet 来获取命令并将其传递到 `Add-History` ，也可以将命令导出到 CSV 或 XML 文件，然后导入命令，然后将导入的文件传递给 `Add-History` 。</span><span class="sxs-lookup"><span data-stu-id="ff658-117">You can use the `Get-History` cmdlet to get the commands and pass them to `Add-History`, or you can export the commands to a CSV or XML file, then import the commands, and pass the imported file to `Add-History`.</span></span> <span data-ttu-id="ff658-118">可以使用此 cmdlet 向历史记录添加特定命令，或创建单个历史记录文件以保存来自多个会话的命令。</span><span class="sxs-lookup"><span data-stu-id="ff658-118">You can use this cmdlet to add specific commands to the history or to create a single history file that includes commands from more than one session.</span></span>

## <span data-ttu-id="ff658-119">示例</span><span class="sxs-lookup"><span data-stu-id="ff658-119">EXAMPLES</span></span>

### <span data-ttu-id="ff658-120">示例1：向其他会话的历史记录添加命令</span><span class="sxs-lookup"><span data-stu-id="ff658-120">Example 1: Add commands to the history of a different session</span></span>

<span data-ttu-id="ff658-121">此示例将在一个 PowerShell 会话中键入的命令添加到不同 PowerShell 会话的历史记录中。</span><span class="sxs-lookup"><span data-stu-id="ff658-121">This example add the commands typed in one PowerShell session to the history of a different PowerShell session.</span></span>

```powershell
Get-History | Export-Csv c:\testing\history.csv -IncludeTypeInformation
Import-Csv c:\testing\history.csv | Add-History
```

<span data-ttu-id="ff658-122">第一个命令获取表示历史记录中的命令的对象，并将其导出到 `History.csv` 文件。</span><span class="sxs-lookup"><span data-stu-id="ff658-122">The first command gets objects representing the commands in the history and exports them to the `History.csv` file.</span></span>

<span data-ttu-id="ff658-123">第二个命令是在另一个会话的命令行中键入的。</span><span class="sxs-lookup"><span data-stu-id="ff658-123">The second command is typed at the command line of a different session.</span></span> <span data-ttu-id="ff658-124">它使用 `Import-Csv` cmdlet 导入文件中的对象 `History.csv` 。</span><span class="sxs-lookup"><span data-stu-id="ff658-124">It uses the `Import-Csv` cmdlet to import the objects in the `History.csv` file.</span></span> <span data-ttu-id="ff658-125">管道运算符 (`|`) 将对象传递给 `Add-History` cmdlet，后者将表示文件中的命令的对象添加 `History.csv` 到当前会话历史记录。</span><span class="sxs-lookup"><span data-stu-id="ff658-125">The pipeline operator (`|`) passes the objects to the `Add-History` cmdlet, which adds the objects representing the commands in the `History.csv` file to the current session history.</span></span>

### <span data-ttu-id="ff658-126">示例2：导入和运行命令</span><span class="sxs-lookup"><span data-stu-id="ff658-126">Example 2: Import and run commands</span></span>

<span data-ttu-id="ff658-127">此示例从文件导入命令 `History.xml` ，将这些命令添加到当前会话历史记录，然后在合并的历史记录中运行命令。</span><span class="sxs-lookup"><span data-stu-id="ff658-127">This example imports commands from the `History.xml` file, adds them to the current session history, and then runs the commands in the combined history.</span></span>

```powershell
Import-Clixml c:\temp\history.xml | Add-History -PassThru | ForEach-Object -Process {Invoke-History}
```

<span data-ttu-id="ff658-128">第一个命令使用 `Import-Clixml` cmdlet 导入已导出到文件中的命令历史记录 `History.xml` 。</span><span class="sxs-lookup"><span data-stu-id="ff658-128">The first command uses the `Import-Clixml` cmdlet to import a command history that was exported to the `History.xml` file.</span></span> <span data-ttu-id="ff658-129">管道运算符将命令传递给 `Add-History` cmdlet，这会将命令添加到当前会话历史记录。</span><span class="sxs-lookup"><span data-stu-id="ff658-129">The pipeline operator passes the commands to the `Add-History` cmdlet, which adds the commands to the current session history.</span></span> <span data-ttu-id="ff658-130">**PassThru** 参数将表示所添加命令的对象沿管道向下传递。</span><span class="sxs-lookup"><span data-stu-id="ff658-130">The **PassThru** parameter passes the objects representing the added commands down the pipeline.</span></span>

<span data-ttu-id="ff658-131">然后，该命令使用 `ForEach-Object` cmdlet 将命令应用于 `Invoke-History` 合并的历史记录中的每个命令。</span><span class="sxs-lookup"><span data-stu-id="ff658-131">The command then uses the `ForEach-Object` cmdlet to apply the `Invoke-History` command to each of the commands in the combined history.</span></span> <span data-ttu-id="ff658-132">该 `Invoke-History` 命令的格式为脚本块，括在大括号中 (`{}`) ，这是 Cmdlet 的 **Process** 参数所要求的 `ForEach-Object` 。</span><span class="sxs-lookup"><span data-stu-id="ff658-132">The `Invoke-History` command is formatted as a script block, enclosed in braces (`{}`), as required by the **Process** parameter of the `ForEach-Object` cmdlet.</span></span>

### <span data-ttu-id="ff658-133">示例3：在历史记录中将命令添加到历史记录的末尾</span><span class="sxs-lookup"><span data-stu-id="ff658-133">Example 3: Add commands in the history to the end of the history</span></span>

<span data-ttu-id="ff658-134">此示例将历史记录中前五个命令添加到历史记录列表的末尾。</span><span class="sxs-lookup"><span data-stu-id="ff658-134">This example adds the first five commands in the history to the end of the history list.</span></span>

```powershell
Get-History -Id 5 -Count 5 | Add-History
```

<span data-ttu-id="ff658-135">该 `Get-History` cmdlet 将获取以命令5结尾的五个命令。</span><span class="sxs-lookup"><span data-stu-id="ff658-135">The `Get-History` cmdlet gets the five commands ending in command 5.</span></span> <span data-ttu-id="ff658-136">管道运算符将其传递给 `Add-History` cmdlet，后者将它们追加到当前历史记录中。</span><span class="sxs-lookup"><span data-stu-id="ff658-136">The pipeline operator passes them to the `Add-History` cmdlet, which appends them to the current history.</span></span> <span data-ttu-id="ff658-137">此 `Add-History` 命令不包括任何参数，但 PowerShell 将通过管道传递的对象与的 **InputObject** 参数相关联 `Add-History` 。</span><span class="sxs-lookup"><span data-stu-id="ff658-137">The `Add-History` command does not include any parameters, but PowerShell associates the objects passed through the pipeline with the **InputObject** parameter of `Add-History`.</span></span>

### <span data-ttu-id="ff658-138">示例4：将 .csv 文件中的命令添加到当前历史记录</span><span class="sxs-lookup"><span data-stu-id="ff658-138">Example 4: Add commands in a .csv file to the current history</span></span>

<span data-ttu-id="ff658-139">此示例将文件中的命令添加 `History.csv` 到当前会话历史记录。</span><span class="sxs-lookup"><span data-stu-id="ff658-139">This example add the commands in the `History.csv` file to the current session history.</span></span>

```powershell
$a = Import-Csv c:\testing\history.csv
Add-History -InputObject $a -PassThru
```

<span data-ttu-id="ff658-140">`Import-Csv`Cmdlet 将导入文件中的命令 `History.csv` ，并将其内容存储在变量中 `$a` 。</span><span class="sxs-lookup"><span data-stu-id="ff658-140">The `Import-Csv` cmdlet imports the commands in the `History.csv` file and store its contents in the variable `$a`.</span></span>

<span data-ttu-id="ff658-141">第二个命令使用 `Add-History` cmdlet 将中的命令添加 `History.csv` 到当前会话历史记录。</span><span class="sxs-lookup"><span data-stu-id="ff658-141">The second command uses the `Add-History` cmdlet to add the commands from `History.csv` to the current session history.</span></span> <span data-ttu-id="ff658-142">它使用 **InputObject** 参数来指定 `$a` 变量，使用 **PassThru** 参数来生成要在命令行中显示的对象。</span><span class="sxs-lookup"><span data-stu-id="ff658-142">It uses the **InputObject** parameter to specify the `$a` variable and the **PassThru** parameter to generate an object to display at the command line.</span></span> <span data-ttu-id="ff658-143">如果没有 **PassThru** 参数，该 `Add-History` cmdlet 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="ff658-143">Without the **PassThru** parameter, the `Add-History` cmdlet does not generate any output.</span></span>

### <span data-ttu-id="ff658-144">示例5：将 .xml 文件中的命令添加到当前历史记录</span><span class="sxs-lookup"><span data-stu-id="ff658-144">Example 5: Add commands in an .xml file to the current history</span></span>

<span data-ttu-id="ff658-145">此示例将文件中的命令添加 `history.xml` 到当前会话历史记录。</span><span class="sxs-lookup"><span data-stu-id="ff658-145">This example adds the commands in the `history.xml` file to the current session history.</span></span>

```powershell
Add-History -InputObject (Import-Clixml c:\temp\history.xml)
```

<span data-ttu-id="ff658-146">**InputObject** 参数将括号中命令的结果传递给 `Add-History` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ff658-146">The **InputObject** parameter passes the results of the command in parentheses to the `Add-History` cmdlet.</span></span> <span data-ttu-id="ff658-147">首先执行括号中的命令，将文件导入 `history.xml` PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ff658-147">The command in parentheses, which is executed first, imports the `history.xml` file into PowerShell.</span></span> <span data-ttu-id="ff658-148">然后，该 `Add-History` cmdlet 会将该文件中的命令添加到会话历史记录。</span><span class="sxs-lookup"><span data-stu-id="ff658-148">The `Add-History` cmdlet then adds the commands in the file to the session history.</span></span>

## <span data-ttu-id="ff658-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ff658-149">PARAMETERS</span></span>

### <span data-ttu-id="ff658-150">-InputObject</span><span class="sxs-lookup"><span data-stu-id="ff658-150">-InputObject</span></span>

<span data-ttu-id="ff658-151">指定一个条目数组，以将其作为 **HistoryInfo** 对象添加到会话历史记录。</span><span class="sxs-lookup"><span data-stu-id="ff658-151">Specifies an array of entries to add to the history as **HistoryInfo** object to the session history.</span></span>
<span data-ttu-id="ff658-152">你可以使用此参数将 **HistoryInfo** 对象（例如，、或 cmdlet 返回的对象）提交 `Get-History` `Import-Clixml` `Import-Csv` 到 `Add-History` 。</span><span class="sxs-lookup"><span data-stu-id="ff658-152">You can use this parameter to submit a **HistoryInfo** object, such as the ones that are returned by the `Get-History`, `Import-Clixml`, or `Import-Csv` cmdlets, to `Add-History`.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ff658-153">-Passthru</span><span class="sxs-lookup"><span data-stu-id="ff658-153">-Passthru</span></span>

<span data-ttu-id="ff658-154">指示此 cmdlet 为每个历史记录条目返回一个 **HistoryInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="ff658-154">Indicates that this cmdlet returns a **HistoryInfo** object for each history entry.</span></span> <span data-ttu-id="ff658-155">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="ff658-155">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff658-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ff658-156">CommonParameters</span></span>

<span data-ttu-id="ff658-157">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="ff658-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ff658-158">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="ff658-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ff658-159">输入</span><span class="sxs-lookup"><span data-stu-id="ff658-159">INPUTS</span></span>

### <span data-ttu-id="ff658-160">Microsoft.PowerShell.Commands.HistoryInfo</span><span class="sxs-lookup"><span data-stu-id="ff658-160">Microsoft.PowerShell.Commands.HistoryInfo</span></span>

<span data-ttu-id="ff658-161">可以通过管道将 **HistoryInfo** 对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ff658-161">You can pipe a **HistoryInfo** object to this cmdlet.</span></span>

## <span data-ttu-id="ff658-162">输出</span><span class="sxs-lookup"><span data-stu-id="ff658-162">OUTPUTS</span></span>

### <span data-ttu-id="ff658-163">无或 Microsoft.PowerShell.Commands.HistoryInfo</span><span class="sxs-lookup"><span data-stu-id="ff658-163">None or Microsoft.PowerShell.Commands.HistoryInfo</span></span>

<span data-ttu-id="ff658-164">如果指定 **PassThru** 参数，则此 cmdlet 将返回 **HistoryInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="ff658-164">This cmdlet returns a **HistoryInfo** object if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="ff658-165">否则，此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="ff658-165">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ff658-166">注释</span><span class="sxs-lookup"><span data-stu-id="ff658-166">NOTES</span></span>

<span data-ttu-id="ff658-167">会话历史记录是在会话期间与 ID 一起输入的命令的列表。</span><span class="sxs-lookup"><span data-stu-id="ff658-167">The session history is a list of the commands entered during the session together with the ID.</span></span> <span data-ttu-id="ff658-168">会话历史记录表示命令的执行顺序、状态以及开始和结束时间。</span><span class="sxs-lookup"><span data-stu-id="ff658-168">The session history represents the order of execution, the status, and the start and end times of the command.</span></span> <span data-ttu-id="ff658-169">当你输入每个命令时，PowerShell 会将其添加到历史记录，以便你可以重复使用它。</span><span class="sxs-lookup"><span data-stu-id="ff658-169">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="ff658-170">有关会话历史记录的详细信息，请参阅 [about_History](About/about_History.md)。</span><span class="sxs-lookup"><span data-stu-id="ff658-170">For more information about the session history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="ff658-171">若要指定要添加到历史记录中的命令，请使用 **InputObject** 参数。</span><span class="sxs-lookup"><span data-stu-id="ff658-171">To specify the commands to add to the history, use the **InputObject** parameter.</span></span> <span data-ttu-id="ff658-172">`Add-History`命令只接受 **HistoryInfo** 对象，例如由 cmdlet 为每个命令返回的对象 `Get-History` 。</span><span class="sxs-lookup"><span data-stu-id="ff658-172">The `Add-History` command accepts only **HistoryInfo** objects, such as those returned for each command by the `Get-History` cmdlet.</span></span> <span data-ttu-id="ff658-173">不能向其传递路径和文件名，也不能传递命令列表。</span><span class="sxs-lookup"><span data-stu-id="ff658-173">You cannot pass it a path and file name or a list of commands.</span></span>

<span data-ttu-id="ff658-174">可以使用 **InputObject** 参数将 **HistoryInfo** 对象的文件传递给 `Add-History` 。</span><span class="sxs-lookup"><span data-stu-id="ff658-174">You can use the **InputObject** parameter to pass a file of **HistoryInfo** objects to `Add-History`.</span></span> <span data-ttu-id="ff658-175">为此，请 `Get-History` 使用或 cmdlet 将命令的结果导出到文件， `Export-Csv` `Export-Clixml` 然后使用或 cmdlet 导入文件 `Import-Csv` `Import-Clixml` 。</span><span class="sxs-lookup"><span data-stu-id="ff658-175">To do so, export the results of a `Get-History` command to a file by using the `Export-Csv` or `Export-Clixml` cmdlet and then import the file by using the `Import-Csv` or `Import-Clixml` cmdlets.</span></span> <span data-ttu-id="ff658-176">然后，可以 **HistoryInfo** `Add-History` 通过管道或变量将导入的 HistoryInfo 对象的文件传递给。</span><span class="sxs-lookup"><span data-stu-id="ff658-176">You can then pass the file of imported **HistoryInfo** objects to `Add-History` through a pipeline or in a variable.</span></span> <span data-ttu-id="ff658-177">有关详细信息，请参阅示例。</span><span class="sxs-lookup"><span data-stu-id="ff658-177">For more information, see the examples.</span></span>

<span data-ttu-id="ff658-178">传递给 cmdlet 的 **HistoryInfo** 对象的文件 `Add-History` 必须包含类型信息、列标题和 **HistoryInfo** 对象的所有属性。</span><span class="sxs-lookup"><span data-stu-id="ff658-178">The file of **HistoryInfo** objects that you pass to the `Add-History` cmdlet must include the type information, column headings, and all of the properties of the **HistoryInfo** objects.</span></span> <span data-ttu-id="ff658-179">如果打算将对象传递回 `Add-History` ，请不要使用 cmdlet 的 **NoTypeInformation** 参数，也不要 `Export-Csv` 删除文件中的类型信息、列标题或任何字段。</span><span class="sxs-lookup"><span data-stu-id="ff658-179">If you intend to pass the objects back to `Add-History`, do not use the **NoTypeInformation** parameter of the `Export-Csv` cmdlet and do not delete the type information, column headings, or any fields in the file.</span></span>

<span data-ttu-id="ff658-180">若要修改会话历史记录，请将会话导出到 CSV 或 XML 文件，修改文件，导入文件，然后使用 `Add-History` 将其追加到当前会话历史记录。</span><span class="sxs-lookup"><span data-stu-id="ff658-180">To modify the session history, export the session to a CSV or XML file, modify the file, import the file, and use `Add-History` to append it to the current session history.</span></span>

## <span data-ttu-id="ff658-181">相关链接</span><span class="sxs-lookup"><span data-stu-id="ff658-181">RELATED LINKS</span></span>

[<span data-ttu-id="ff658-182">Clear-History</span><span class="sxs-lookup"><span data-stu-id="ff658-182">Clear-History</span></span>](Clear-History.md)

[<span data-ttu-id="ff658-183">Get-History</span><span class="sxs-lookup"><span data-stu-id="ff658-183">Get-History</span></span>](Get-History.md)

[<span data-ttu-id="ff658-184">Invoke-History</span><span class="sxs-lookup"><span data-stu-id="ff658-184">Invoke-History</span></span>](Invoke-History.md)

[<span data-ttu-id="ff658-185">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="ff658-185">about_PSReadLine</span></span>](../PSReadLine/About/about_PSReadLine.md)

[<span data-ttu-id="ff658-186">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="ff658-186">Get-PSReadLineOption</span></span>](/powershell/module/psreadline/get-psreadlineoption)

[<span data-ttu-id="ff658-187">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="ff658-187">Set-PSReadLineOption</span></span>](/powershell/module/psreadline/set-psreadlineoption)
