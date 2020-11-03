---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 2/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-alias?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Alias
ms.openlocfilehash: 2a84c08022689d53c3273f1b6f802cfeae67953d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93197386"
---
# <span data-ttu-id="2f630-103">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="2f630-103">Set-Alias</span></span>

## <span data-ttu-id="2f630-104">摘要</span><span class="sxs-lookup"><span data-stu-id="2f630-104">SYNOPSIS</span></span>
<span data-ttu-id="2f630-105">在当前 PowerShell 会话中为 cmdlet 或其他命令创建或更改别名。</span><span class="sxs-lookup"><span data-stu-id="2f630-105">Creates or changes an alias for a cmdlet or other command in the current PowerShell session.</span></span>

## <span data-ttu-id="2f630-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2f630-106">SYNTAX</span></span>

### <span data-ttu-id="2f630-107">Default（默认值）</span><span class="sxs-lookup"><span data-stu-id="2f630-107">Default (Default)</span></span>

```
Set-Alias [-Name] <string> [-Value] <string> [-Description <string>] [-Option <ScopedItemOptions>]
 [-PassThru] [-Scope <string>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2f630-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2f630-108">DESCRIPTION</span></span>

<span data-ttu-id="2f630-109">`Set-Alias`Cmdlet 可为 cmdlet 或命令创建或更改别名，例如函数、脚本、文件或其他可执行文件。</span><span class="sxs-lookup"><span data-stu-id="2f630-109">The `Set-Alias` cmdlet creates or changes an alias for a cmdlet or a command, such as a function, script, file, or other executable.</span></span> <span data-ttu-id="2f630-110">别名是引用 cmdlet 或命令的替代名称。</span><span class="sxs-lookup"><span data-stu-id="2f630-110">An alias is an alternate name that refers to a cmdlet or command.</span></span>
<span data-ttu-id="2f630-111">例如， `sal` 是 cmdlet 的别名 `Set-Alias` 。</span><span class="sxs-lookup"><span data-stu-id="2f630-111">For example, `sal` is the alias for the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="2f630-112">有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="2f630-112">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="2f630-113">一个 cmdlet 可以具有多个别名，但一个别名只能与一个 cmdlet 关联。</span><span class="sxs-lookup"><span data-stu-id="2f630-113">A cmdlet can have multiple aliases, but an alias can only be associated with one cmdlet.</span></span> <span data-ttu-id="2f630-114">你可以使用 `Set-Alias` 将现有别名重新分配给另一个 cmdlet，或更改别名的属性，如描述。</span><span class="sxs-lookup"><span data-stu-id="2f630-114">You can use `Set-Alias` to reassign an existing alias to another cmdlet, or change an alias's properties, such as the description.</span></span>

<span data-ttu-id="2f630-115">由创建或更改的别名 `Set-Alias` 不是永久性的，并且仅在当前 PowerShell 会话中可用。</span><span class="sxs-lookup"><span data-stu-id="2f630-115">An alias that is created or changed by `Set-Alias` is not permanent and is only available during the current PowerShell session.</span></span> <span data-ttu-id="2f630-116">关闭 PowerShell 会话后，会删除该别名。</span><span class="sxs-lookup"><span data-stu-id="2f630-116">When the PowerShell session is closed, the alias is removed.</span></span>

## <span data-ttu-id="2f630-117">示例</span><span class="sxs-lookup"><span data-stu-id="2f630-117">EXAMPLES</span></span>

### <span data-ttu-id="2f630-118">示例 1：创建 cmdlet 的别名</span><span class="sxs-lookup"><span data-stu-id="2f630-118">Example 1: Create an alias for a cmdlet</span></span>

<span data-ttu-id="2f630-119">此命令在当前 PowerShell 会话中为 cmdlet 创建别名。</span><span class="sxs-lookup"><span data-stu-id="2f630-119">This command creates an alias to a cmdlet in the current PowerShell session.</span></span>

```
PS> Set-Alias -Name list -Value Get-ChildItem

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem
```

<span data-ttu-id="2f630-120">`Set-Alias`Cmdlet 可在当前 PowerShell 会话中创建别名。</span><span class="sxs-lookup"><span data-stu-id="2f630-120">The `Set-Alias` cmdlet creates an alias in the current PowerShell session.</span></span> <span data-ttu-id="2f630-121">**Name** 参数指定别名的名称 `list` 。</span><span class="sxs-lookup"><span data-stu-id="2f630-121">The **Name** parameter specifies the alias's name, `list`.</span></span> <span data-ttu-id="2f630-122">**Value** 参数指定别名运行的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2f630-122">The **Value** parameter specifies the cmdlet that the alias runs.</span></span>

<span data-ttu-id="2f630-123">若要运行别名，请 `list` 在 PowerShell 命令行上键入。</span><span class="sxs-lookup"><span data-stu-id="2f630-123">To run the alias, type `list` on the PowerShell command line.</span></span>

### <span data-ttu-id="2f630-124">示例2：将现有别名重新分配给其他 cmdlet</span><span class="sxs-lookup"><span data-stu-id="2f630-124">Example 2: Reassign an existing alias to a different cmdlet</span></span>

<span data-ttu-id="2f630-125">此命令将重新分配现有别名以运行不同的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2f630-125">This command reassigns an existing alias to run a different cmdlet.</span></span>

```
PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem

PS> Set-Alias -Name list -Value Get-Location

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-Location
```

<span data-ttu-id="2f630-126">`Get-Alias`Cmdlet 使用 **Name** 参数显示 `list` 别名。</span><span class="sxs-lookup"><span data-stu-id="2f630-126">The `Get-Alias` cmdlet uses the **Name** parameter to display the `list` alias.</span></span> <span data-ttu-id="2f630-127">`list`别名与 `Get-ChildItem` cmdlet 关联。</span><span class="sxs-lookup"><span data-stu-id="2f630-127">The `list` alias is associated with the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="2f630-128">`list`运行别名时，会显示当前目录中的项。</span><span class="sxs-lookup"><span data-stu-id="2f630-128">When the `list` alias is run, the items in the current directory are displayed.</span></span>

<span data-ttu-id="2f630-129">`Set-Alias`Cmdlet 使用 **Name** 参数来指定 `list` 别名。</span><span class="sxs-lookup"><span data-stu-id="2f630-129">The `Set-Alias` cmdlet uses the **Name** parameter to specify the `list` alias.</span></span> <span data-ttu-id="2f630-130">**Value** 参数将别名与 `Get-Location` cmdlet 关联。</span><span class="sxs-lookup"><span data-stu-id="2f630-130">The **Value** parameter associates the alias to the `Get-Location` cmdlet.</span></span>

<span data-ttu-id="2f630-131">`Get-Alias`Cmdlet 使用 **Name** 参数显示 `list` 别名。</span><span class="sxs-lookup"><span data-stu-id="2f630-131">The `Get-Alias` cmdlet uses the **Name** parameter to display the `list` alias.</span></span> <span data-ttu-id="2f630-132">`list`别名与 `Get-Location` cmdlet 关联。</span><span class="sxs-lookup"><span data-stu-id="2f630-132">The `list` alias is associated with the `Get-Location` cmdlet.</span></span> <span data-ttu-id="2f630-133">`list`运行别名时，会显示当前目录的位置。</span><span class="sxs-lookup"><span data-stu-id="2f630-133">When the `list` alias is run, the current directory's location is displayed.</span></span>

### <span data-ttu-id="2f630-134">示例3：创建和更改只读别名</span><span class="sxs-lookup"><span data-stu-id="2f630-134">Example 3: Create and change a read-only alias</span></span>

<span data-ttu-id="2f630-135">此命令创建只读别名。</span><span class="sxs-lookup"><span data-stu-id="2f630-135">This command creates a read-only alias.</span></span> <span data-ttu-id="2f630-136">只读选项可防止对别名所做的意外更改。</span><span class="sxs-lookup"><span data-stu-id="2f630-136">The read-only option prevents unintended changes to an alias.</span></span> <span data-ttu-id="2f630-137">若要更改或删除只读别名，请使用 **Force** 参数。</span><span class="sxs-lookup"><span data-stu-id="2f630-137">To change or delete a read-only alias, use the **Force** parameter.</span></span>

```
PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         :
Name                : loc
CommandType         : Alias

PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -Description 'Displays the current directory' -Force -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         : Displays the current directory
Name                : loc
CommandType         : Alias
```

<span data-ttu-id="2f630-138">`Set-Alias`Cmdlet 可在当前 PowerShell 会话中创建别名。</span><span class="sxs-lookup"><span data-stu-id="2f630-138">The `Set-Alias` cmdlet creates an alias in the current PowerShell session.</span></span> <span data-ttu-id="2f630-139">**Name** 参数指定别名的名称 `loc` 。</span><span class="sxs-lookup"><span data-stu-id="2f630-139">The **Name** parameter specifies the alias's name, `loc`.</span></span> <span data-ttu-id="2f630-140">**Value** 参数指定 `Get-Location` 别名运行的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2f630-140">The **Value** parameter specifies the `Get-Location` cmdlet that the alias runs.</span></span> <span data-ttu-id="2f630-141">**选项** 参数指定 **ReadOnly** 值。</span><span class="sxs-lookup"><span data-stu-id="2f630-141">The **Option** parameter specifies the **ReadOnly** value.</span></span> <span data-ttu-id="2f630-142">**PassThru** 参数表示 alias 对象，并将对象向下发送到 `Format-List` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2f630-142">The **PassThru** parameter represents the alias object and sends the object down the pipeline to the `Format-List` cmdlet.</span></span> <span data-ttu-id="2f630-143">`Format-List` 使用带有星号 (的 **属性** 参数 `*`) 以便显示所有属性。</span><span class="sxs-lookup"><span data-stu-id="2f630-143">`Format-List` uses the **Property** parameter with an asterisk (`*`) so that all of the properties are displayed.</span></span> <span data-ttu-id="2f630-144">示例输出显示了这些属性的部分列表。</span><span class="sxs-lookup"><span data-stu-id="2f630-144">The example output shows a partial list of those properties.</span></span>

<span data-ttu-id="2f630-145">`loc`通过添加两个参数来更改该别名。</span><span class="sxs-lookup"><span data-stu-id="2f630-145">The `loc` alias is changed with the addition of two parameters.</span></span> <span data-ttu-id="2f630-146">**说明** 添加文本以说明别名的用途。</span><span class="sxs-lookup"><span data-stu-id="2f630-146">**Description** adds text to explain the alias's purpose.</span></span> <span data-ttu-id="2f630-147">因为别名是只读的，所以需要 **Force** 参数 `loc` 。</span><span class="sxs-lookup"><span data-stu-id="2f630-147">The **Force** parameter is needed because the `loc` alias is read-only.</span></span> <span data-ttu-id="2f630-148">如果未使用 **Force** 参数，则更改将失败。</span><span class="sxs-lookup"><span data-stu-id="2f630-148">If the **Force** parameter is not used, the change fails.</span></span>

### <span data-ttu-id="2f630-149">示例4：创建可执行文件的别名</span><span class="sxs-lookup"><span data-stu-id="2f630-149">Example 4: Create an alias to an executable file</span></span>

<span data-ttu-id="2f630-150">此示例为本地计算机上的可执行文件创建别名。</span><span class="sxs-lookup"><span data-stu-id="2f630-150">This example creates an alias to an executable file on the local computer.</span></span>

```
PS> Set-Alias -Name np -Value C:\Windows\notepad.exe

PS> Get-Alias -Name np

CommandType     Name
-----------     ----
Alias           np -> notepad.exe
```

<span data-ttu-id="2f630-151">`Set-Alias`Cmdlet 可在当前 PowerShell 会话中创建别名。</span><span class="sxs-lookup"><span data-stu-id="2f630-151">The `Set-Alias` cmdlet creates an alias in the current PowerShell session.</span></span> <span data-ttu-id="2f630-152">**Name** 参数指定别名的名称 `np` 。</span><span class="sxs-lookup"><span data-stu-id="2f630-152">The **Name** parameter specifies the alias's name, `np`.</span></span> <span data-ttu-id="2f630-153">**Value** 参数指定路径和应用程序名称 **C:\Windows\notepad.exe** 。</span><span class="sxs-lookup"><span data-stu-id="2f630-153">The **Value** parameter specifies the path and application name **C:\Windows\notepad.exe** .</span></span> <span data-ttu-id="2f630-154">`Get-Alias`Cmdlet 使用 **Name** 参数显示该 `np` 别名与 **notepad.exe** 相关联。</span><span class="sxs-lookup"><span data-stu-id="2f630-154">The `Get-Alias` cmdlet uses the **Name** parameter to show that the `np` alias is associated with **notepad.exe** .</span></span>

<span data-ttu-id="2f630-155">若要运行别名，请 `np` 在 PowerShell 命令行上键入以打开 **notepad.exe** 。</span><span class="sxs-lookup"><span data-stu-id="2f630-155">To run the alias, type `np` on the PowerShell command line to open **notepad.exe** .</span></span>

### <span data-ttu-id="2f630-156">示例5：为带有参数的命令创建别名</span><span class="sxs-lookup"><span data-stu-id="2f630-156">Example 5: Create an alias for a command with parameters</span></span>

<span data-ttu-id="2f630-157">此示例演示如何为带有参数的命令分配别名。</span><span class="sxs-lookup"><span data-stu-id="2f630-157">This example shows how to assign an alias to a command with parameters.</span></span>

<span data-ttu-id="2f630-158">你可以为 cmdlet 创建别名，例如 `Set-Location` 。</span><span class="sxs-lookup"><span data-stu-id="2f630-158">You can create an alias for a cmdlet, such as `Set-Location`.</span></span> <span data-ttu-id="2f630-159">不能为带有参数和值的命令创建别名，例如 `Set-Location -Path C:\Windows\System32` 。</span><span class="sxs-lookup"><span data-stu-id="2f630-159">You cannot create an alias for a command with parameters and values, such as `Set-Location -Path C:\Windows\System32`.</span></span> <span data-ttu-id="2f630-160">若要为某个命令创建别名，请创建一个包括该命令的函数，然后为此函数创建别名。</span><span class="sxs-lookup"><span data-stu-id="2f630-160">To create an alias for a command, create a function that includes the command, and then create an alias to the function.</span></span> <span data-ttu-id="2f630-161">有关详细信息，请参阅 [about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md)。</span><span class="sxs-lookup"><span data-stu-id="2f630-161">For more information, see [about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md).</span></span>

```
PS> Function CD32 {Set-Location -Path C:\Windows\System32}

PS> Set-Alias -Name Go -Value CD32
```

<span data-ttu-id="2f630-162">创建名为的函数 `CD32` 。</span><span class="sxs-lookup"><span data-stu-id="2f630-162">A function named `CD32` is created.</span></span> <span data-ttu-id="2f630-163">函数将 `Set-Location` cmdlet 与 **Path** 参数一起使用以指定目录 **C:\Windows\System32** 。</span><span class="sxs-lookup"><span data-stu-id="2f630-163">The function uses the `Set-Location` cmdlet with the **Path** parameter to specify the directory, **C:\Windows\System32** .</span></span>

<span data-ttu-id="2f630-164">`Set-Alias`Cmdlet 可在当前 PowerShell 会话中创建函数的别名。</span><span class="sxs-lookup"><span data-stu-id="2f630-164">The `Set-Alias` cmdlet creates an alias to the function in the current PowerShell session.</span></span> <span data-ttu-id="2f630-165">**Name** 参数指定别名的名称 `Go` 。</span><span class="sxs-lookup"><span data-stu-id="2f630-165">The **Name** parameter specifies the alias's name, `Go`.</span></span> <span data-ttu-id="2f630-166">**Value** 参数指定函数的名称， `CD32` 。</span><span class="sxs-lookup"><span data-stu-id="2f630-166">The **Value** parameter specifies the function's name, `CD32`.</span></span>

<span data-ttu-id="2f630-167">若要运行别名，请 `Go` 在 PowerShell 命令行上键入。</span><span class="sxs-lookup"><span data-stu-id="2f630-167">To run the alias, type `Go` on the PowerShell command line.</span></span> <span data-ttu-id="2f630-168">`CD32`函数会运行并更改目录 **C:\Windows\System32** 。</span><span class="sxs-lookup"><span data-stu-id="2f630-168">The `CD32` function runs and changes to the directory **C:\Windows\System32** .</span></span>

## <span data-ttu-id="2f630-169">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2f630-169">PARAMETERS</span></span>

### <span data-ttu-id="2f630-170">-Description</span><span class="sxs-lookup"><span data-stu-id="2f630-170">-Description</span></span>

<span data-ttu-id="2f630-171">指定对别名的描述。</span><span class="sxs-lookup"><span data-stu-id="2f630-171">Specifies a description of the alias.</span></span> <span data-ttu-id="2f630-172">你可以键入任意字符串。</span><span class="sxs-lookup"><span data-stu-id="2f630-172">You can type any string.</span></span> <span data-ttu-id="2f630-173">如果描述包含空格，则将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="2f630-173">If the description includes spaces, enclose it single quotation marks.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f630-174">-Force</span><span class="sxs-lookup"><span data-stu-id="2f630-174">-Force</span></span>

<span data-ttu-id="2f630-175">使用 **Force** 参数可更改或删除将 **选项** 参数设置为 **ReadOnly** 的别名。</span><span class="sxs-lookup"><span data-stu-id="2f630-175">Use the **Force** parameter to change or delete an alias that has the **Option** parameter set to **ReadOnly** .</span></span>

<span data-ttu-id="2f630-176">**Force** 参数无法更改或删除 **选项** 参数设置为 **常量** 的别名。</span><span class="sxs-lookup"><span data-stu-id="2f630-176">The **Force** parameter cannot change or delete an alias with the **Option** parameter set to **Constant** .</span></span>

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

### <span data-ttu-id="2f630-177">-Name</span><span class="sxs-lookup"><span data-stu-id="2f630-177">-Name</span></span>

<span data-ttu-id="2f630-178">指定新别名的名称。</span><span class="sxs-lookup"><span data-stu-id="2f630-178">Specifies the name of a new alias.</span></span> <span data-ttu-id="2f630-179">别名可以包含字母数字字符和连字符。</span><span class="sxs-lookup"><span data-stu-id="2f630-179">An alias name can contain alphanumeric characters and hyphens.</span></span> <span data-ttu-id="2f630-180">别名不能为数字，如123。</span><span class="sxs-lookup"><span data-stu-id="2f630-180">Alias names cannot be numeric, such as 123.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2f630-181">-Option</span><span class="sxs-lookup"><span data-stu-id="2f630-181">-Option</span></span>

<span data-ttu-id="2f630-182">设置别名的 **选项** 属性值。</span><span class="sxs-lookup"><span data-stu-id="2f630-182">Sets the **Option** property value of the alias.</span></span> <span data-ttu-id="2f630-183">值（如 **ReadOnly** 和 **常量** ）可防止意外更改的别名。</span><span class="sxs-lookup"><span data-stu-id="2f630-183">Values such as **ReadOnly** and **Constant** protect an alias from unintended changes.</span></span> <span data-ttu-id="2f630-184">若要查看会话中所有别名的 **选项** 属性，请键入 `Get-Alias | Format-Table -Property Name, Options -Autosize` 。</span><span class="sxs-lookup"><span data-stu-id="2f630-184">To see the **Option** property of all aliases in the session, type `Get-Alias | Format-Table -Property Name, Options -Autosize`.</span></span>

<span data-ttu-id="2f630-185">此参数可接受的值如下所示：</span><span class="sxs-lookup"><span data-stu-id="2f630-185">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="2f630-186">**AllScope** 将别名复制到任何创建的新作用域。</span><span class="sxs-lookup"><span data-stu-id="2f630-186">**AllScope** The alias is copied to any new scopes that are created.</span></span>
- <span data-ttu-id="2f630-187">**常量** 不能更改或删除。</span><span class="sxs-lookup"><span data-stu-id="2f630-187">**Constant** Cannot be changed or deleted.</span></span>
- <span data-ttu-id="2f630-188">**无** 不设置任何选项，是默认值。</span><span class="sxs-lookup"><span data-stu-id="2f630-188">**None** Sets no options and is the default.</span></span>
- <span data-ttu-id="2f630-189">**私有** 别名仅在当前作用域中可用。</span><span class="sxs-lookup"><span data-stu-id="2f630-189">**Private** The alias is available only in the current scope.</span></span>
- <span data-ttu-id="2f630-190">**ReadOnly** 除非使用 **Force** 参数，否则无法对其进行更改或删除。</span><span class="sxs-lookup"><span data-stu-id="2f630-190">**ReadOnly** Cannot be changed or deleted unless the **Force** parameter is used.</span></span>
- <span data-ttu-id="2f630-191">**Unspecified**</span><span class="sxs-lookup"><span data-stu-id="2f630-191">**Unspecified**</span></span>

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: AllScope, Constant, None, Private, ReadOnly, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f630-192">-PassThru</span><span class="sxs-lookup"><span data-stu-id="2f630-192">-PassThru</span></span>

<span data-ttu-id="2f630-193">返回一个表示别名的对象。</span><span class="sxs-lookup"><span data-stu-id="2f630-193">Returns an object that represents the alias.</span></span> <span data-ttu-id="2f630-194">使用格式 cmdlet （例如） `Format-List` 来显示对象。</span><span class="sxs-lookup"><span data-stu-id="2f630-194">Use a format cmdlet such as `Format-List` to display the object.</span></span> <span data-ttu-id="2f630-195">默认情况下，不 `Set-Alias` 会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="2f630-195">By default, `Set-Alias` does not generate any output.</span></span>

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

### <span data-ttu-id="2f630-196">-Scope</span><span class="sxs-lookup"><span data-stu-id="2f630-196">-Scope</span></span>

<span data-ttu-id="2f630-197">指定此别名的有效作用域。</span><span class="sxs-lookup"><span data-stu-id="2f630-197">Specifies the scope in which this alias is valid.</span></span> <span data-ttu-id="2f630-198">默认值为 " **本地** "。</span><span class="sxs-lookup"><span data-stu-id="2f630-198">The default value is **Local** .</span></span> <span data-ttu-id="2f630-199">有关详细信息，请参阅 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="2f630-199">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

<span data-ttu-id="2f630-200">可接受的值如下所示：</span><span class="sxs-lookup"><span data-stu-id="2f630-200">The acceptable values are as follows:</span></span>

- <span data-ttu-id="2f630-201">全球</span><span class="sxs-lookup"><span data-stu-id="2f630-201">Global</span></span>
- <span data-ttu-id="2f630-202">Local</span><span class="sxs-lookup"><span data-stu-id="2f630-202">Local</span></span>
- <span data-ttu-id="2f630-203">Private</span><span class="sxs-lookup"><span data-stu-id="2f630-203">Private</span></span>
- <span data-ttu-id="2f630-204">编号范围</span><span class="sxs-lookup"><span data-stu-id="2f630-204">Numbered scopes</span></span>
- <span data-ttu-id="2f630-205">脚本</span><span class="sxs-lookup"><span data-stu-id="2f630-205">Script</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Global, Local, Private, Numbered scopes, Script

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f630-206">-Value</span><span class="sxs-lookup"><span data-stu-id="2f630-206">-Value</span></span>

<span data-ttu-id="2f630-207">指定别名运行的 cmdlet 或命令的名称。</span><span class="sxs-lookup"><span data-stu-id="2f630-207">Specifies the name of the cmdlet or command that the alias runs.</span></span> <span data-ttu-id="2f630-208">**值** 参数是别名的 **定义** 属性。</span><span class="sxs-lookup"><span data-stu-id="2f630-208">The **Value** parameter is the alias's **Definition** property.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2f630-209">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2f630-209">-Confirm</span></span>

<span data-ttu-id="2f630-210">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="2f630-210">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f630-211">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2f630-211">-WhatIf</span></span>

<span data-ttu-id="2f630-212">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="2f630-212">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="2f630-213">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="2f630-213">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f630-214">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2f630-214">CommonParameters</span></span>

<span data-ttu-id="2f630-215">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2f630-215">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2f630-216">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2f630-216">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2f630-217">输入</span><span class="sxs-lookup"><span data-stu-id="2f630-217">INPUTS</span></span>

### <span data-ttu-id="2f630-218">无</span><span class="sxs-lookup"><span data-stu-id="2f630-218">None</span></span>

<span data-ttu-id="2f630-219">`Set-Alias` 不接受来自管道的输入。</span><span class="sxs-lookup"><span data-stu-id="2f630-219">`Set-Alias` does not accept input from the pipeline.</span></span>

## <span data-ttu-id="2f630-220">输出</span><span class="sxs-lookup"><span data-stu-id="2f630-220">OUTPUTS</span></span>

### <span data-ttu-id="2f630-221">无或 System.Management.Automation.AliasInfo</span><span class="sxs-lookup"><span data-stu-id="2f630-221">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="2f630-222">当使用 **PassThru** 参数时，将 `Set-Alias` 生成一个表示别名的 **system.management.automation.aliasinfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="2f630-222">When you use the **PassThru** parameter, `Set-Alias` generates a **System.Management.Automation.AliasInfo** object representing the alias.</span></span> <span data-ttu-id="2f630-223">否则，不 `Set-Alias` 会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="2f630-223">Otherwise, `Set-Alias` does not generate any output.</span></span>

## <span data-ttu-id="2f630-224">注释</span><span class="sxs-lookup"><span data-stu-id="2f630-224">NOTES</span></span>

<span data-ttu-id="2f630-225">PowerShell 包括每个 PowerShell 会话中提供的内置别名。</span><span class="sxs-lookup"><span data-stu-id="2f630-225">PowerShell includes built-in aliases that are available in each PowerShell session.</span></span> <span data-ttu-id="2f630-226">`Get-Alias`Cmdlet 显示 PowerShell 会话中可用的别名。</span><span class="sxs-lookup"><span data-stu-id="2f630-226">The `Get-Alias` cmdlet displays the aliases available in a PowerShell session.</span></span>

<span data-ttu-id="2f630-227">若要创建别名，请使用 cmdlet `Set-Alias` 或 `New-Alias` 。</span><span class="sxs-lookup"><span data-stu-id="2f630-227">To create an alias, use the cmdlets `Set-Alias` or `New-Alias`.</span></span> <span data-ttu-id="2f630-228">在 PowerShell 6 中，若要删除别名，请使用 `Remove-Alias` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2f630-228">In PowerShell 6, to delete an alias, use the `Remove-Alias` cmdlet.</span></span> <span data-ttu-id="2f630-229">`Remove-Item` 接受以实现向后兼容性，如用于在以前版本的 PowerShell 中创建的脚本。</span><span class="sxs-lookup"><span data-stu-id="2f630-229">`Remove-Item` is accepted for backwards compatibility such as for scripts created with prior versions of PowerShell.</span></span> <span data-ttu-id="2f630-230">使用命令（如） `Remove-Item -Path Alias:aliasname` 。</span><span class="sxs-lookup"><span data-stu-id="2f630-230">Use a command such as `Remove-Item -Path Alias:aliasname`.</span></span>

<span data-ttu-id="2f630-231">若要创建在每个 PowerShell 会话中都可用的别名，请将其添加到 PowerShell 配置文件中。</span><span class="sxs-lookup"><span data-stu-id="2f630-231">To create an alias that is available in each PowerShell session, add it to your PowerShell profile.</span></span>
<span data-ttu-id="2f630-232">有关详细信息，请参阅 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="2f630-232">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="2f630-233">可以通过执行 "导出" 和 "导入"，在另一个 PowerShell 会话中保存和重复使用别名。</span><span class="sxs-lookup"><span data-stu-id="2f630-233">An alias can be saved and reused in another PowerShell session by doing an export and import.</span></span> <span data-ttu-id="2f630-234">若要将别名保存到文件，请使用 `Export-Alias` 。</span><span class="sxs-lookup"><span data-stu-id="2f630-234">To save an alias to a file, use `Export-Alias`.</span></span> <span data-ttu-id="2f630-235">若要将保存的别名添加到新的 PowerShell 会话，请使用 `Import-Alias` 。</span><span class="sxs-lookup"><span data-stu-id="2f630-235">To add a saved alias to a new PowerShell session, use `Import-Alias`.</span></span>

## <span data-ttu-id="2f630-236">相关链接</span><span class="sxs-lookup"><span data-stu-id="2f630-236">RELATED LINKS</span></span>

[<span data-ttu-id="2f630-237">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="2f630-237">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="2f630-238">about_Functions</span><span class="sxs-lookup"><span data-stu-id="2f630-238">about_Functions</span></span>](../Microsoft.PowerShell.Core/about/about_Functions.md)

[<span data-ttu-id="2f630-239">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="2f630-239">about_Profiles</span></span>](../Microsoft.PowerShell.Core/About/about_Profiles.md)

[<span data-ttu-id="2f630-240">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="2f630-240">about_Scopes</span></span>](../Microsoft.PowerShell.Core/About/about_Scopes.md)

[<span data-ttu-id="2f630-241">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="2f630-241">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="2f630-242">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="2f630-242">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="2f630-243">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="2f630-243">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="2f630-244">New-Alias</span><span class="sxs-lookup"><span data-stu-id="2f630-244">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="2f630-245">Remove-Alias</span><span class="sxs-lookup"><span data-stu-id="2f630-245">Remove-Alias</span></span>](Remove-Alias.md)

[<span data-ttu-id="2f630-246">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="2f630-246">Remove-Item</span></span>](../Microsoft.PowerShell.Management/Remove-Item.md)

