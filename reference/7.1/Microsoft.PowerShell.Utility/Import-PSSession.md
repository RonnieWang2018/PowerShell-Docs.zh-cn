---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PSSession
ms.openlocfilehash: 05e2d4575be1617feb29c58acbfd9a2a68fbb607
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389175"
---
# <span data-ttu-id="04606-103">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="04606-103">Import-PSSession</span></span>

## <span data-ttu-id="04606-104">摘要</span><span class="sxs-lookup"><span data-stu-id="04606-104">SYNOPSIS</span></span>
<span data-ttu-id="04606-105">将另一个会话中的命令导入当前会话中。</span><span class="sxs-lookup"><span data-stu-id="04606-105">Imports commands from another session into the current session.</span></span>

## <span data-ttu-id="04606-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="04606-106">SYNTAX</span></span>

```
Import-PSSession [-Prefix <String>] [-DisableNameChecking] [[-CommandName] <String[]>] [-AllowClobber]
 [-ArgumentList <Object[]>] [-CommandType <CommandTypes>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-FormatTypeName] <String[]>]
 [-Certificate <X509Certificate2>] [-Session] <PSSession> [<CommonParameters>]
```

## <span data-ttu-id="04606-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="04606-107">DESCRIPTION</span></span>

<span data-ttu-id="04606-108">该 `Import-PSSession` cmdlet 从本地或远程计算机上的 PSSession 中导入命令，例如 cmdlet、函数和别名，并将其导入到当前会话中。</span><span class="sxs-lookup"><span data-stu-id="04606-108">The `Import-PSSession` cmdlet imports commands , such as cmdlets, functions, and aliases, from a PSSession on a local or remote computer into the current session.</span></span> <span data-ttu-id="04606-109">你可以导入 `Get-Command` cmdlet 可在 PSSession 中找到的任何命令。</span><span class="sxs-lookup"><span data-stu-id="04606-109">You can import any command that the `Get-Command` cmdlet can find in the PSSession.</span></span>

<span data-ttu-id="04606-110">使用 `Import-PSSession` 命令从自定义 shell （如 Microsoft Exchange Server shell）或包含 Windows PowerShell 模块和管理单元或其他不在当前会话中的元素的会话导入命令。</span><span class="sxs-lookup"><span data-stu-id="04606-110">Use an `Import-PSSession` command to import commands from a customized shell, such as a Microsoft Exchange Server shell, or from a session that includes Windows PowerShell modules and snap-ins or other elements that are not in the current session.</span></span>

<span data-ttu-id="04606-111">若要导入命令，请先使用 `New-PSSession` cmdlet 创建 PSSession。</span><span class="sxs-lookup"><span data-stu-id="04606-111">To import commands, first use the `New-PSSession` cmdlet to create a PSSession.</span></span> <span data-ttu-id="04606-112">然后，使用 `Import-PSSession` cmdlet 导入命令。</span><span class="sxs-lookup"><span data-stu-id="04606-112">Then, use the `Import-PSSession` cmdlet to import the commands.</span></span> <span data-ttu-id="04606-113">默认情况下， `Import-PSSession` 会导入除当前会话中的命令具有相同名称的命令之外的所有命令。</span><span class="sxs-lookup"><span data-stu-id="04606-113">By default, `Import-PSSession` imports all commands except for commands that have the same names as commands in the current session.</span></span> <span data-ttu-id="04606-114">若要导入所有命令，请使用 **AllowClobber** 参数。</span><span class="sxs-lookup"><span data-stu-id="04606-114">To import all the commands, use the **AllowClobber** parameter.</span></span>

<span data-ttu-id="04606-115">你可以使用导入的命令，如同你在会话中使用的任何命令一样。</span><span class="sxs-lookup"><span data-stu-id="04606-115">You can use imported commands just as you would use any command in the session.</span></span> <span data-ttu-id="04606-116">当使用导入的命令时，命令的导入部分将在导出该命令的会话中隐式运行。</span><span class="sxs-lookup"><span data-stu-id="04606-116">When you use an imported command, the imported part of the command runs implicitly in the session from which it was imported.</span></span> <span data-ttu-id="04606-117">但是，远程操作完全由 Windows PowerShell 处理。</span><span class="sxs-lookup"><span data-stu-id="04606-117">However, the remote operations are handled entirely by Windows PowerShell.</span></span> <span data-ttu-id="04606-118">你甚至不需要注意它们，只不过必须使与另一个会话 （PSSession) 的连接保持打开状态。</span><span class="sxs-lookup"><span data-stu-id="04606-118">You need not even be aware of them, except that you must keep the connection to the other session (PSSession) open.</span></span> <span data-ttu-id="04606-119">如果关闭该链接，则导入的命令将不再可用。</span><span class="sxs-lookup"><span data-stu-id="04606-119">If you close it, the imported commands are no longer available.</span></span>

<span data-ttu-id="04606-120">由于导入的命令的运行时间可能比本地命令长，因此会 `Import-PSSession` 将 **AsJob** 参数添加到每个导入的命令。</span><span class="sxs-lookup"><span data-stu-id="04606-120">Because imported commands might take longer to run than local commands, `Import-PSSession` adds an **AsJob** parameter to every imported command.</span></span> <span data-ttu-id="04606-121">此参数使你可以将该命令作为 Windows PowerShell 后台作业运行。</span><span class="sxs-lookup"><span data-stu-id="04606-121">This parameter allows you to run the command as a Windows PowerShell background job.</span></span> <span data-ttu-id="04606-122">有关详细信息，请参阅 [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="04606-122">For more information, see [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md).</span></span>

<span data-ttu-id="04606-123">使用时 `Import-PSSession` ，Windows PowerShell 会将导入的命令添加到仅存在于会话中的临时模块，并返回表示该模块的对象。</span><span class="sxs-lookup"><span data-stu-id="04606-123">When you use `Import-PSSession`, Windows PowerShell adds the imported commands to a temporary module that exists only in your session and returns an object that represents the module.</span></span> <span data-ttu-id="04606-124">若要创建可在将来的会话中使用的持久性模块，请使用 `Export-PSSession` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="04606-124">To create a persistent module that you can use in future sessions, use the `Export-PSSession` cmdlet.</span></span>

<span data-ttu-id="04606-125">`Import-PSSession`Cmdlet 使用 Windows PowerShell 的隐式远程处理功能。</span><span class="sxs-lookup"><span data-stu-id="04606-125">The `Import-PSSession` cmdlet uses the implicit remoting feature of Windows PowerShell.</span></span> <span data-ttu-id="04606-126">将命令导入到当前会话中时，它们将在原始会话或原始计算机上的类似会话中隐式运行。</span><span class="sxs-lookup"><span data-stu-id="04606-126">When you import commands into the current session, they run implicitly in the original session or in a similar session on the originating computer.</span></span>

<span data-ttu-id="04606-127">从 Windows PowerShell 3.0 开始，可以使用 cmdlet 将 `Import-Module` 远程会话中的模块导入到当前会话中。</span><span class="sxs-lookup"><span data-stu-id="04606-127">Beginning in Windows PowerShell 3.0, you can use the `Import-Module` cmdlet to import modules from a remote session into the current session.</span></span> <span data-ttu-id="04606-128">此功能使用隐式远程处理。</span><span class="sxs-lookup"><span data-stu-id="04606-128">This feature uses implicit remoting.</span></span> <span data-ttu-id="04606-129">它相当于使用 `Import-PSSession` 将所选模块从远程会话导入到当前会话中。</span><span class="sxs-lookup"><span data-stu-id="04606-129">It is equivalent to using `Import-PSSession` to import selected modules from a remote session into the current session.</span></span>

## <span data-ttu-id="04606-130">示例</span><span class="sxs-lookup"><span data-stu-id="04606-130">EXAMPLES</span></span>

### <span data-ttu-id="04606-131">示例1：从 PSSession 导入所有命令</span><span class="sxs-lookup"><span data-stu-id="04606-131">Example 1: Import all commands from a PSSession</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S
```

<span data-ttu-id="04606-132">此命令将所有命令从 Server01 计算机上的 PSSession 导入到当前会话中，与当前会话中的命令具有相同名称的命令除外。</span><span class="sxs-lookup"><span data-stu-id="04606-132">This command imports all commands from a PSSession on the Server01 computer into the current session, except for commands that have the same names as commands in the current session.</span></span>

<span data-ttu-id="04606-133">因为此命令不使用 **CommandName** 参数，所以它还会导入已导入命令所需的所有格式设置数据。</span><span class="sxs-lookup"><span data-stu-id="04606-133">Because this command does not use the **CommandName** parameter, it also imports all of the formatting data required for the imported commands.</span></span>

### <span data-ttu-id="04606-134">示例2：导入以特定字符串结尾的命令</span><span class="sxs-lookup"><span data-stu-id="04606-134">Example 2: Import commands that end with a specific string</span></span>

```
PS C:\> $S = New-PSSession https://ps.testlabs.com/powershell
PS C:\> Import-PSSession -Session $S -CommandName *-test -FormatTypeName *
PS C:\> New-Test -Name Test1
PS C:\> Get-Test test1 | Run-Test
```

<span data-ttu-id="04606-135">这些命令会将 PSSession 中名称以“-test”结尾的命令导入本地会话，然后显示如何使用导入的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="04606-135">These commands import the commands with names that end in "-test" from a PSSession into the local session, and then they show how to use an imported cmdlet.</span></span>

<span data-ttu-id="04606-136">第一个命令使用 `New-PSSession` cmdlet 创建 PSSession。</span><span class="sxs-lookup"><span data-stu-id="04606-136">The first command uses the `New-PSSession` cmdlet to create a PSSession.</span></span> <span data-ttu-id="04606-137">它将 PSSession 保存在 `$S` 变量中。</span><span class="sxs-lookup"><span data-stu-id="04606-137">It saves the PSSession in the `$S` variable.</span></span>

<span data-ttu-id="04606-138">第二个命令使用 `Import-PSSession` cmdlet 将命令从中的 PSSession 导入 `$S` 到当前会话中。</span><span class="sxs-lookup"><span data-stu-id="04606-138">The second command uses the `Import-PSSession` cmdlet to import commands from the PSSession in `$S` into the current session.</span></span> <span data-ttu-id="04606-139">它使用 **CommandName** 参数指定带有名词 Test 的命令，使用 **FormatTypeName** 参数来导入这些命令的格式设置数据。</span><span class="sxs-lookup"><span data-stu-id="04606-139">It uses the **CommandName** parameter to specify commands with the Test noun and the **FormatTypeName** parameter to import the formatting data for the Test commands.</span></span>

<span data-ttu-id="04606-140">第三个和第四个命令使用当前会话中导入的命令。</span><span class="sxs-lookup"><span data-stu-id="04606-140">The third and fourth commands use the imported commands in the current session.</span></span> <span data-ttu-id="04606-141">由于导入的命令实际添加到当前会话中，因此你将使用本地语法来运行它们。</span><span class="sxs-lookup"><span data-stu-id="04606-141">Because imported commands are actually added to the current session, you use the local syntax to run them.</span></span> <span data-ttu-id="04606-142">不需要使用 `Invoke-Command` cmdlet 来运行导入的命令。</span><span class="sxs-lookup"><span data-stu-id="04606-142">You do not need to use the `Invoke-Command` cmdlet to run an imported command.</span></span>

### <span data-ttu-id="04606-143">示例3：从 PSSession 导入 cmdlet</span><span class="sxs-lookup"><span data-stu-id="04606-143">Example 3: Import cmdlets from a PSSession</span></span>

```
PS C:\> $S1 = New-PSSession -ComputerName s1
PS C:\> $S2 = New-PSSession -ComputerName s2
PS C:\> Import-PSSession -Session s1 -Type cmdlet -Name New-Test, Get-Test -FormatTypeName *
PS C:\> Import-PSSession -Session s2 -Type Cmdlet -Name Set-Test -FormatTypeName *
PS C:\> New-Test Test1 | Set-Test -RunType Full
```

<span data-ttu-id="04606-144">此示例演示可以像使用本地 cmdlet 一样使用导入的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="04606-144">This example shows that you can use imported cmdlets just as you would use local cmdlets.</span></span>

<span data-ttu-id="04606-145">这些命令 `New-Test` `Get-Test` 从 Server01 计算机上的 pssession 中导入和 cmdlet，并 `Set-Test` 从 Server02 计算机上的 pssession 中导入 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="04606-145">These commands import the `New-Test` and `Get-Test` cmdlets from a PSSession on the Server01 computer and the `Set-Test` cmdlet from a PSSession on the Server02 computer.</span></span>

<span data-ttu-id="04606-146">尽管这些 cmdlet 从不同的 PSSession 中导入，但是可以通过管道将来自一个 cmdlet 的对象无误地传递到另一个 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="04606-146">Even though the cmdlets were imported from different PSSessions, you can pipe an object from one cmdlet to another without error.</span></span>

### <span data-ttu-id="04606-147">示例4：将导入的命令作为后台作业运行</span><span class="sxs-lookup"><span data-stu-id="04606-147">Example 4: Run an imported command as a background job</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S -CommandName *-test* -FormatTypeName *
PS C:\> $batch = New-Test -Name Batch -AsJob
PS C:\> Receive-Job $batch
```

<span data-ttu-id="04606-148">此示例演示了如何将导入的命令作为后台作业运行。</span><span class="sxs-lookup"><span data-stu-id="04606-148">This example shows how to run an imported command as a background job.</span></span>

<span data-ttu-id="04606-149">由于导入的命令的运行时间可能比本地命令长，因此会 `Import-PSSession` 将 **AsJob** 参数添加到每个导入的命令。</span><span class="sxs-lookup"><span data-stu-id="04606-149">Because imported commands might take longer to run than local commands, `Import-PSSession` adds an **AsJob** parameter to every imported command.</span></span> <span data-ttu-id="04606-150">**AsJob** 参数允许你将该命令作为后台作业运行。</span><span class="sxs-lookup"><span data-stu-id="04606-150">The **AsJob** parameter lets you run the command as a background job.</span></span>

<span data-ttu-id="04606-151">第一个命令在 Server01 计算机上创建 PSSession，并将 PSSession 对象保存在 `$S` 变量中。</span><span class="sxs-lookup"><span data-stu-id="04606-151">The first command creates a PSSession on the Server01 computer and saves the PSSession object in the `$S` variable.</span></span>

<span data-ttu-id="04606-152">第二个命令使用 `Import-PSSession` 将中的 PSSession 的测试 cmdlet 导入 `$S` 到当前会话中。</span><span class="sxs-lookup"><span data-stu-id="04606-152">The second command uses `Import-PSSession` to import the Test cmdlets from the PSSession in `$S` into the current session.</span></span>

<span data-ttu-id="04606-153">第三个命令使用导入的 cmdlet 的 **AsJob** 参数 `New-Test` 将 `New-Test` 命令作为后台作业运行。</span><span class="sxs-lookup"><span data-stu-id="04606-153">The third command uses the **AsJob** parameter of the imported `New-Test` cmdlet to run a `New-Test` command as a background job.</span></span> <span data-ttu-id="04606-154">命令保存 `New-Test` 在变量中返回的作业对象 `$batch` 。</span><span class="sxs-lookup"><span data-stu-id="04606-154">The command saves the job object that `New-Test` returns in the `$batch` variable.</span></span>

<span data-ttu-id="04606-155">第四个命令使用 `Receive-Job` cmdlet 来获取变量中的作业的结果 `$batch` 。</span><span class="sxs-lookup"><span data-stu-id="04606-155">The fourth command uses the `Receive-Job` cmdlet to get the results of the job in the `$batch` variable.</span></span>

### <span data-ttu-id="04606-156">示例5：从 Windows PowerShell 模块导入 cmdlet 和函数</span><span class="sxs-lookup"><span data-stu-id="04606-156">Example 5: Import cmdlets and functions from a Windows PowerShell module</span></span>

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Invoke-Command -Session $S {Import-Module TestManagement}
PS C:\> Import-PSSession -Session $S -Module TestManagement
```

<span data-ttu-id="04606-157">此示例演示如何将远程计算机上的 Windows PowerShell 模块中的 cmdlet 和函数导入当前会话。</span><span class="sxs-lookup"><span data-stu-id="04606-157">This example shows how to import the cmdlets and functions from a Windows PowerShell module on a remote computer into the current session.</span></span>

<span data-ttu-id="04606-158">第一个命令在 Server01 计算机上创建 PSSession，并将其保存在 `$S` 变量中。</span><span class="sxs-lookup"><span data-stu-id="04606-158">The first command creates a PSSession on the Server01 computer and saves it in the `$S` variable.</span></span>

<span data-ttu-id="04606-159">第二个命令使用 `Invoke-Command` cmdlet `Import-Module` 在中的 PSSession 中运行命令 `$S` 。</span><span class="sxs-lookup"><span data-stu-id="04606-159">The second command uses the `Invoke-Command` cmdlet to run an `Import-Module` command in the PSSession in `$S`.</span></span>

<span data-ttu-id="04606-160">通常，该模块将通过 `Import-Module` Windows PowerShell 配置文件中的命令添加到所有会话，但配置文件不会在 pssession 中运行。</span><span class="sxs-lookup"><span data-stu-id="04606-160">Typically, the module would be added to all sessions by an `Import-Module` command in a Windows PowerShell profile, but profiles are not run in PSSessions.</span></span>

<span data-ttu-id="04606-161">第三个命令使用 **module** 参数 `Import-PSSession` 将模块中的 cmdlet 和函数导入到当前会话中。</span><span class="sxs-lookup"><span data-stu-id="04606-161">The third command uses the **Module** parameter of `Import-PSSession` to import the cmdlets and functions in the module into the current session.</span></span>

### <span data-ttu-id="04606-162">示例6：在临时文件中创建模块</span><span class="sxs-lookup"><span data-stu-id="04606-162">Example 6: Create a module in a temporary file</span></span>

```
PS C:\> Import-PSSession $S -CommandName Get-Date, SearchHelp -FormatTypeName * -AllowClobber

Name              : tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf
Path              : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1
zunz.ttf\tmp_79468106-4e1d-4d90-af97-1154f9317239_
tcw1zunz.ttf.psm1
Description       : Implicit remoting for http://server01.corp.fabrikam.com/wsman
Guid              : 79468106-4e1d-4d90-af97-1154f9317239
Version           : 1.0
ModuleBase        : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1
zunz.ttf
ModuleType        : Script
PrivateData       : {ImplicitRemoting}
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Get-Date, Get-Date], [SearchHelp, SearchHelp]}
ExportedVariables : {}
NestedModules     : {}
```

<span data-ttu-id="04606-163">此示例演示如何 `Import-PSSession` 在磁盘上的临时文件中创建一个模块。</span><span class="sxs-lookup"><span data-stu-id="04606-163">This example shows that `Import-PSSession` creates a module in a temporary file on disk.</span></span> <span data-ttu-id="04606-164">它还显示所有命令在导入当前会话之前都已转换为函数。</span><span class="sxs-lookup"><span data-stu-id="04606-164">It also shows that all commands are converted into functions before they are imported into the current session.</span></span>

<span data-ttu-id="04606-165">该命令使用 `Import-PSSession` cmdlet 将 `Get-Date` Cmdlet 和 SearchHelp 函数导入到当前会话中。</span><span class="sxs-lookup"><span data-stu-id="04606-165">The command uses the `Import-PSSession` cmdlet to import a `Get-Date` cmdlet and a SearchHelp function into the current session.</span></span>

<span data-ttu-id="04606-166">`Import-PSSession`Cmdlet 将返回表示临时模块的 **PSModuleInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="04606-166">The `Import-PSSession` cmdlet returns a **PSModuleInfo** object that represents the temporary module.</span></span> <span data-ttu-id="04606-167">" **路径** " 属性的值显示 `Import-PSSession` 在临时位置创建脚本模块 ( hbase-runner.psm1) 文件。</span><span class="sxs-lookup"><span data-stu-id="04606-167">The value of the **Path** property shows that `Import-PSSession` created a script module (.psm1) file in a temporary location.</span></span> <span data-ttu-id="04606-168">**ExportedFunctions** 属性显示 `Get-Date` cmdlet 和 SearchHelp 函数均作为函数导入。</span><span class="sxs-lookup"><span data-stu-id="04606-168">The **ExportedFunctions** property shows that the `Get-Date` cmdlet and the SearchHelp function were both imported as functions.</span></span>

### <span data-ttu-id="04606-169">示例7：运行由导入的命令隐藏的命令</span><span class="sxs-lookup"><span data-stu-id="04606-169">Example 7: Run a command that is hidden by an imported command</span></span>

```
PS C:\> Import-PSSession $S -CommandName Get-Date -FormatTypeName * -AllowClobber

PS C:\> Get-Command Get-Date -All

CommandType   Name       Definition
-----------   ----       ----------
Function      Get-Date   ...
Cmdlet        Get-Date   Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>]

PS C:\> Get-Date
09074

PS C:\> (Get-Command -Type Cmdlet -Name Get-Date).PSSnapin.Name
Microsoft.PowerShell.Utility

PS C:\> Microsoft.PowerShell.Utility\Get-Date
Sunday, March 15, 2009 2:08:26 PM
```

<span data-ttu-id="04606-170">此示例演示如何运行导入的命令隐藏的命令。</span><span class="sxs-lookup"><span data-stu-id="04606-170">This example shows how to run a command that is hidden by an imported command.</span></span>

<span data-ttu-id="04606-171">第一个命令 `Get-Date` 从变量的 PSSession 中导入一个 cmdlet `$S` 。</span><span class="sxs-lookup"><span data-stu-id="04606-171">The first command imports a `Get-Date` cmdlet from the PSSession in the `$S` variable.</span></span> <span data-ttu-id="04606-172">由于当前会话包含 `Get-Date` cmdlet，因此命令中需要 **AllowClobber** 参数。</span><span class="sxs-lookup"><span data-stu-id="04606-172">Because the current session includes a `Get-Date` cmdlet, the **AllowClobber** parameter is required in the command.</span></span>

<span data-ttu-id="04606-173">第二个命令使用 cmdlet 的 **all** 参数 `Get-Command` 获取 `Get-Date` 当前会话中的所有命令。</span><span class="sxs-lookup"><span data-stu-id="04606-173">The second command uses the **All** parameter of the `Get-Command` cmdlet to get all `Get-Date` commands in the current session.</span></span> <span data-ttu-id="04606-174">此输出显示会话包括原始 `Get-Date` cmdlet 和 `Get-Date` 函数。</span><span class="sxs-lookup"><span data-stu-id="04606-174">The output shows that the session includes the original `Get-Date` cmdlet and a `Get-Date` function.</span></span> <span data-ttu-id="04606-175">`Get-Date`函数在 `Get-Date` 中的 PSSession 中运行导入的 cmdlet `$S` 。</span><span class="sxs-lookup"><span data-stu-id="04606-175">The `Get-Date` function runs the imported `Get-Date` cmdlet in the PSSession in `$S`.</span></span>

<span data-ttu-id="04606-176">第三个命令运行 `Get-Date` 命令。</span><span class="sxs-lookup"><span data-stu-id="04606-176">The third command runs a `Get-Date` command.</span></span> <span data-ttu-id="04606-177">由于函数优先于 cmdlet，因此 Windows PowerShell 会运行导入的 `Get-Date` 函数，该函数将返回儒略历日期。</span><span class="sxs-lookup"><span data-stu-id="04606-177">Because functions take precedence over cmdlets, Windows PowerShell runs the imported `Get-Date` function, which returns a Julian date.</span></span>

<span data-ttu-id="04606-178">第四个和第五个命令显示如何使用限定的名称来运行由导入的命令隐藏的命令。</span><span class="sxs-lookup"><span data-stu-id="04606-178">The fourth and fifth commands show how to use a qualified name to run a command that is hidden by an imported command.</span></span>

<span data-ttu-id="04606-179">第四个命令获取将原始 `Get-Date` cmdlet 添加到当前会话的 Windows PowerShell 管理单元的名称。</span><span class="sxs-lookup"><span data-stu-id="04606-179">The fourth command gets the name of the Windows PowerShell snap-in that added the original `Get-Date` cmdlet to the current session.</span></span>

<span data-ttu-id="04606-180">第五个命令使用 cmdlet 的管理限定名称 `Get-Date` 运行 `Get-Date` 命令。</span><span class="sxs-lookup"><span data-stu-id="04606-180">The fifth command uses the snap-in-qualified name of the `Get-Date` cmdlet to run a `Get-Date` command.</span></span>

<span data-ttu-id="04606-181">有关命令优先级和隐藏的命令的详细信息，请参阅 [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="04606-181">For more information about command precedence and hidden commands, see [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="04606-182">示例8：导入名称中包含特定字符串的命令</span><span class="sxs-lookup"><span data-stu-id="04606-182">Example 8: Import commands that have a specific string in their names</span></span>

```
PS C:\> Import-PSSession -Session $S -CommandName **Item** -AllowClobber
```

<span data-ttu-id="04606-183">此命令导入其名称包含中的 PSSession 项的命令 `$S` 。</span><span class="sxs-lookup"><span data-stu-id="04606-183">This command imports commands whose names include Item from the PSSession in `$S`.</span></span> <span data-ttu-id="04606-184">由于该命令包含 **CommandName** 参数而不是 **FormatTypeData** 参数，因此只会导入该命令。</span><span class="sxs-lookup"><span data-stu-id="04606-184">Because the command includes the **CommandName** parameter but not the **FormatTypeData** parameter, only the command is imported.</span></span>

<span data-ttu-id="04606-185">当你使用在 `Import-PSSession` 远程计算机上运行命令并且当前会话中的命令具有格式数据时，请使用此命令。</span><span class="sxs-lookup"><span data-stu-id="04606-185">Use this command when you are using `Import-PSSession` to run a command on a remote computer and you already have the formatting data for the command in the current session.</span></span>

### <span data-ttu-id="04606-186">示例9：使用 Module 参数来发现已导入到会话中的命令</span><span class="sxs-lookup"><span data-stu-id="04606-186">Example 9: Use the Module parameter to discover which commands were imported into the session</span></span>

```
PS C:\> $M = Import-PSSession -Session $S -CommandName *bits* -FormatTypeName *bits*
PS C:\> Get-Command -Module $M
CommandType     Name
-----------     ----
Function        Add-BitsFile
Function        Complete-BitsTransfer
Function        Get-BitsTransfer
Function        Remove-BitsTransfer
Function        Resume-BitsTransfer
Function        Set-BitsTransfer
Function        Start-BitsTransfer
Function        Suspend-BitsTransfer
```

<span data-ttu-id="04606-187">此命令演示如何使用 **Module** 参数 `Get-Command` 来找出命令已导入到会话中的命令 `Import-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="04606-187">This command shows how to use the **Module** parameter of `Get-Command` to find out which commands were imported into the session by an `Import-PSSession` command.</span></span>

<span data-ttu-id="04606-188">第一个命令使用 `Import-PSSession` cmdlet 导入其名称包含变量中 PSSession 的 "bits" 的命令 `$S` 。</span><span class="sxs-lookup"><span data-stu-id="04606-188">The first command uses the `Import-PSSession` cmdlet to import commands whose names include "bits" from the PSSession in the `$S` variable.</span></span> <span data-ttu-id="04606-189">该 `Import-PSSession` 命令将返回一个临时模块，并且该命令会将模块保存在 `$m` 变量中。</span><span class="sxs-lookup"><span data-stu-id="04606-189">The `Import-PSSession` command returns a temporary module, and the command saves the module in the `$m` variable.</span></span>

<span data-ttu-id="04606-190">第二个命令使用 `Get-Command` cmdlet 来获取由变量中的模块导出的命令 `$M` 。</span><span class="sxs-lookup"><span data-stu-id="04606-190">The second command uses the `Get-Command` cmdlet to get the commands that are exported by the module in the `$M` variable.</span></span>

<span data-ttu-id="04606-191">**Module** 参数采用字符串值，这是为模块名称而设计的。</span><span class="sxs-lookup"><span data-stu-id="04606-191">The **Module** parameter takes a string value, which is designed for the module name.</span></span> <span data-ttu-id="04606-192">但是，当你提交模块对象时，Windows PowerShell 将对该模块对象使用 **ToString** 方法，然后返回模块名称。</span><span class="sxs-lookup"><span data-stu-id="04606-192">However, when you submit a module object, Windows PowerShell uses the **ToString** method on the module object, which returns the module name.</span></span>

<span data-ttu-id="04606-193">`Get-Command`命令等效于 `Get-Command $M.Name` "。</span><span class="sxs-lookup"><span data-stu-id="04606-193">The `Get-Command` command is the equivalent of `Get-Command $M.Name`".</span></span>

## <span data-ttu-id="04606-194">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="04606-194">PARAMETERS</span></span>

### <span data-ttu-id="04606-195">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="04606-195">-AllowClobber</span></span>

<span data-ttu-id="04606-196">指示此 cmdlet 将导入指定的命令，即使它们与当前会话中的命令具有相同的名称。</span><span class="sxs-lookup"><span data-stu-id="04606-196">Indicates that this cmdlet imports the specified commands, even if they have the same names as commands in the current session.</span></span>

<span data-ttu-id="04606-197">如果导入与当前会话中的命令同名的命令，则导入的命令会隐藏或替换原始命令。</span><span class="sxs-lookup"><span data-stu-id="04606-197">If you import a command with the same name as a command in the current session, the imported command hides or replaces the original commands.</span></span> <span data-ttu-id="04606-198">有关详细信息，请参阅 [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="04606-198">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span></span>

<span data-ttu-id="04606-199">默认情况下，不 `Import-PSSession` 会导入与当前会话中的命令同名的命令。</span><span class="sxs-lookup"><span data-stu-id="04606-199">By default, `Import-PSSession` does not import commands that have the same name as commands in the current session.</span></span>

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

### <span data-ttu-id="04606-200">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="04606-200">-ArgumentList</span></span>

<span data-ttu-id="04606-201">指定通过使用指定参数 (参数值) 导致的命令数组。</span><span class="sxs-lookup"><span data-stu-id="04606-201">Specifies an array of commands that results from using the specified arguments (parameter values).</span></span>

<span data-ttu-id="04606-202">例如，若要导入证书中的命令的变体 `Get-Item` (Cert： ) 驱动器 `$S` ，请键入 `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:` 。</span><span class="sxs-lookup"><span data-stu-id="04606-202">For instance, to import the variant of the `Get-Item` command in the certificate (Cert:) drive in the PSSession in `$S`, type `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:`.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04606-203">-Certificate</span><span class="sxs-lookup"><span data-stu-id="04606-203">-Certificate</span></span>

<span data-ttu-id="04606-204">指定客户端证书，该证书用于对创建的临时模块中 ( \* .Format.ps1xml) 或脚本模块文件)  ( 的格式文件进行签名 `Import-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="04606-204">Specifies the client certificate that is used to sign the format files (\*.Format.ps1xml) or script module files (.psm1) in the temporary module that `Import-PSSession` creates.</span></span>

<span data-ttu-id="04606-205">输入一个包含证书的变量，或可获取该证书的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="04606-205">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="04606-206">若要查找证书，请使用 `Get-PfxCertificate` cmdlet，或使用 `Get-ChildItem` 证书 (Cert： ) 驱动器中的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="04606-206">To find a certificate, use the `Get-PfxCertificate` cmdlet or use the `Get-ChildItem` cmdlet in the Certificate (Cert:) drive.</span></span> <span data-ttu-id="04606-207">如果证书无效或不具有足够的权限，则该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="04606-207">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04606-208">-CommandName</span><span class="sxs-lookup"><span data-stu-id="04606-208">-CommandName</span></span>

<span data-ttu-id="04606-209">指定带有指定名称或名称模式的命令。</span><span class="sxs-lookup"><span data-stu-id="04606-209">Specifies commands with the specified names or name patterns.</span></span> <span data-ttu-id="04606-210">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="04606-210">Wildcards are permitted.</span></span> <span data-ttu-id="04606-211">使用 **CommandName** 或其 **别名。**</span><span class="sxs-lookup"><span data-stu-id="04606-211">Use **CommandName** or its alias, **Name**.</span></span>

<span data-ttu-id="04606-212">默认情况下， `Import-PSSession` 从会话导入所有命令，但与当前会话中的命令同名的命令除外。</span><span class="sxs-lookup"><span data-stu-id="04606-212">By default, `Import-PSSession` imports all commands from the session, except for commands that have the same names as commands in the current session.</span></span> <span data-ttu-id="04606-213">这样可以防止导入的命令隐藏或替换会话中的命令。</span><span class="sxs-lookup"><span data-stu-id="04606-213">This prevents imported commands from hiding or replacing commands in the session.</span></span> <span data-ttu-id="04606-214">若要导入所有命令，甚至那些隐藏或替换其他命令的命令，请使用 **AllowClobber** 参数。</span><span class="sxs-lookup"><span data-stu-id="04606-214">To import all commands, even those that hide or replace other commands, use the **AllowClobber** parameter.</span></span>

<span data-ttu-id="04606-215">如果使用 **CommandName** 参数，则不导入这些命令的格式设置文件，除非使用 **FormatTypeName** 参数。</span><span class="sxs-lookup"><span data-stu-id="04606-215">If you use the **CommandName** parameter, the formatting files for the commands are not imported unless you use the **FormatTypeName** parameter.</span></span> <span data-ttu-id="04606-216">同样，如果使用 **FormatTypeName** 参数，则不导入任何命令，除非使用 **CommandName** 参数。</span><span class="sxs-lookup"><span data-stu-id="04606-216">Similarly, if you use the **FormatTypeName** parameter, no commands are imported unless you use the **CommandName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04606-217">-CommandType</span><span class="sxs-lookup"><span data-stu-id="04606-217">-CommandType</span></span>

<span data-ttu-id="04606-218">指定命令对象的类型。</span><span class="sxs-lookup"><span data-stu-id="04606-218">Specifies the type of command objects.</span></span> <span data-ttu-id="04606-219">默认值为 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="04606-219">The default value is Cmdlet.</span></span> <span data-ttu-id="04606-220">使用 **CommandType** 或其别名 **Type** 。</span><span class="sxs-lookup"><span data-stu-id="04606-220">Use **CommandType** or its alias, **Type**.</span></span> <span data-ttu-id="04606-221">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="04606-221">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="04606-222">A.</span><span class="sxs-lookup"><span data-stu-id="04606-222">Alias.</span></span> <span data-ttu-id="04606-223">远程会话中的 Windows PowerShell 别名。</span><span class="sxs-lookup"><span data-stu-id="04606-223">The Windows PowerShell aliases in the remote session.</span></span>
- <span data-ttu-id="04606-224">全部。</span><span class="sxs-lookup"><span data-stu-id="04606-224">All.</span></span> <span data-ttu-id="04606-225">远程会话中的 cmdlet 和函数。</span><span class="sxs-lookup"><span data-stu-id="04606-225">The cmdlets and functions in the remote session.</span></span>
- <span data-ttu-id="04606-226">应用程序。</span><span class="sxs-lookup"><span data-stu-id="04606-226">Application.</span></span> <span data-ttu-id="04606-227">Path 环境变量中列出的路径中 Windows-PowerShell 文件以外的所有文件 `$env:path` （包括 .txt、.exe 和 .dll 文件）将在远程会话中 () 。</span><span class="sxs-lookup"><span data-stu-id="04606-227">All the files other than Windows-PowerShell files in the paths that are listed in the Path environment variable (`$env:path`) in the remote session, including .txt, .exe, and .dll files.</span></span>
- <span data-ttu-id="04606-228">Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="04606-228">Cmdlet.</span></span> <span data-ttu-id="04606-229">远程会话中的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="04606-229">The cmdlets in the remote session.</span></span> <span data-ttu-id="04606-230">默认值为“Cmdlet”。</span><span class="sxs-lookup"><span data-stu-id="04606-230">"Cmdlet" is the default.</span></span>
- <span data-ttu-id="04606-231">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="04606-231">ExternalScript.</span></span> <span data-ttu-id="04606-232">Path 环境变量中列出的路径中的 ps1 文件 (`$env:path` 远程会话) 。</span><span class="sxs-lookup"><span data-stu-id="04606-232">The .ps1 files in the paths listed in the Path environment variable (`$env:path`) in the remote session.</span></span>
- <span data-ttu-id="04606-233">Filter 和 Function。</span><span class="sxs-lookup"><span data-stu-id="04606-233">Filter and Function.</span></span> <span data-ttu-id="04606-234">远程会话中的 Windows PowerShell 函数。</span><span class="sxs-lookup"><span data-stu-id="04606-234">The Windows PowerShell functions in the remote session.</span></span>
- <span data-ttu-id="04606-235">脚本。</span><span class="sxs-lookup"><span data-stu-id="04606-235">Script.</span></span> <span data-ttu-id="04606-236">远程会话中的脚本块。</span><span class="sxs-lookup"><span data-stu-id="04606-236">The script blocks in the remote session.</span></span>

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: Alias, Function, Filter, Cmdlet, ExternalScript, Application, Script, Workflow, Configuration, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04606-237">-DisableNameChecking</span><span class="sxs-lookup"><span data-stu-id="04606-237">-DisableNameChecking</span></span>

<span data-ttu-id="04606-238">指示当你导入的 cmdlet 或函数名称包括未经批准的动词或禁止的字符时，此 cmdlet 将禁止显示警告你的消息。</span><span class="sxs-lookup"><span data-stu-id="04606-238">Indicates that this cmdlet suppresses the message that warns you when you import a cmdlet or function whose name includes an unapproved verb or a prohibited character.</span></span>

<span data-ttu-id="04606-239">默认情况下，当导入的模块导出名称中包含未经批准的谓词的 cmdlet 或函数时，Windows PowerShell 将显示以下警告消息：</span><span class="sxs-lookup"><span data-stu-id="04606-239">By default, when a module that you import exports cmdlets or functions that have unapproved verbs in their names, the Windows PowerShell displays the following warning message:</span></span>

<span data-ttu-id="04606-240">"警告：某些导入的命令名称包括未经批准的动词，这可能会使它们的发现性更小。</span><span class="sxs-lookup"><span data-stu-id="04606-240">"WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span> <span data-ttu-id="04606-241">`Get-Verb`若要查看已批准的动词的列表，请使用 Verbose 参数获取更多详细信息或类型。</span><span class="sxs-lookup"><span data-stu-id="04606-241">Use the Verbose parameter for more detail or type `Get-Verb` to see the list of approved verbs."</span></span>

<span data-ttu-id="04606-242">此消息只是一个警告。</span><span class="sxs-lookup"><span data-stu-id="04606-242">This message is only a warning.</span></span> <span data-ttu-id="04606-243">仍将导入完整的模块，其中包括非一致性的命令。</span><span class="sxs-lookup"><span data-stu-id="04606-243">The complete module is still imported, including the non-conforming commands.</span></span> <span data-ttu-id="04606-244">尽管会向模块用户显示消息，但是模块作者应修复命名问题。</span><span class="sxs-lookup"><span data-stu-id="04606-244">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

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

### <span data-ttu-id="04606-245">-FormatTypeName</span><span class="sxs-lookup"><span data-stu-id="04606-245">-FormatTypeName</span></span>

<span data-ttu-id="04606-246">指定指定 Microsoft .NET 框架类型的格式设置说明。</span><span class="sxs-lookup"><span data-stu-id="04606-246">Specifies formatting instructions for the specified Microsoft .NET Framework types.</span></span>
<span data-ttu-id="04606-247">输入类型名称。</span><span class="sxs-lookup"><span data-stu-id="04606-247">Enter the type names.</span></span>
<span data-ttu-id="04606-248">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="04606-248">Wildcards are permitted.</span></span>

<span data-ttu-id="04606-249">此参数的值必须是要 `Get-FormatData` 从其导入命令的会话中的命令返回的类型的名称。</span><span class="sxs-lookup"><span data-stu-id="04606-249">The value of this parameter must be the name of a type that is returned by a `Get-FormatData` command in the session from which the commands are being imported.</span></span> <span data-ttu-id="04606-250">若要获取远程会话中的所有格式设置数据，请键入 `*` 。</span><span class="sxs-lookup"><span data-stu-id="04606-250">To get all of the formatting data in the remote session, type `*`.</span></span>

<span data-ttu-id="04606-251">如果此命令不包括 **CommandName** 或 **FormatTypeName** 参数，则将 `Import-PSSession` 导入 `Get-FormatData` 远程会话中命令返回的所有 .NET Framework 类型的格式说明。</span><span class="sxs-lookup"><span data-stu-id="04606-251">If the command does not include either the **CommandName** or **FormatTypeName** parameter, `Import-PSSession` imports formatting instructions for all .NET Framework types returned by a `Get-FormatData` command in the remote session.</span></span>

<span data-ttu-id="04606-252">如果使用 **FormatTypeName** 参数，则不导入任何命令，除非使用 **CommandName** 参数。</span><span class="sxs-lookup"><span data-stu-id="04606-252">If you use the **FormatTypeName** parameter, no commands are imported unless you use the **CommandName** parameter.</span></span>

<span data-ttu-id="04606-253">同样，如果使用 **CommandName** 参数，则不导入这些命令的格式设置文件，除非使用 **FormatTypeName** 参数。</span><span class="sxs-lookup"><span data-stu-id="04606-253">Similarly, if you use the **CommandName** parameter, the formatting files for the commands are not imported unless you use the **FormatTypeName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04606-254">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="04606-254">-FullyQualifiedModule</span></span>

<span data-ttu-id="04606-255">指定名称以 **ModuleSpecification** 对象的形式指定的模块 (在 PowerShell SDK 中的 [ModuleSpecification 构造函数 (哈希表)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_) 的 "备注" 部分中介绍。</span><span class="sxs-lookup"><span data-stu-id="04606-255">Specifies modules with names that are specified in the form of **ModuleSpecification** objects (described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_) in the PowerShell SDK.</span></span> <span data-ttu-id="04606-256">例如， **FullyQualifiedModule** 参数接受以下格式指定的模块名称：</span><span class="sxs-lookup"><span data-stu-id="04606-256">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in the format:</span></span>

- <span data-ttu-id="04606-257">`@{ModuleName = "modulename"; ModuleVersion = "version_number"}` 或</span><span class="sxs-lookup"><span data-stu-id="04606-257">`@{ModuleName = "modulename"; ModuleVersion = "version_number"}` or</span></span>
- <span data-ttu-id="04606-258">`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`.</span><span class="sxs-lookup"><span data-stu-id="04606-258">`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`.</span></span>

<span data-ttu-id="04606-259">**ModuleName** 和 **ModuleVersion** 是必需的，但 **Guid** 是可选的。</span><span class="sxs-lookup"><span data-stu-id="04606-259">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="04606-260">不能在与 **Module** 参数相同的命令中指定 **FullyQualifiedModule** 参数。</span><span class="sxs-lookup"><span data-stu-id="04606-260">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="04606-261">这两个参数是互斥的。</span><span class="sxs-lookup"><span data-stu-id="04606-261">The two parameters are mutually exclusive.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04606-262">-Module</span><span class="sxs-lookup"><span data-stu-id="04606-262">-Module</span></span>

<span data-ttu-id="04606-263">指定 Windows PowerShell 管理单元和模块中的命令的数组。</span><span class="sxs-lookup"><span data-stu-id="04606-263">Specifies and array of commands in the Windows PowerShell snap-ins and modules.</span></span> <span data-ttu-id="04606-264">输入管理单元和模块的名称。</span><span class="sxs-lookup"><span data-stu-id="04606-264">Enter the snap-in and module names.</span></span> <span data-ttu-id="04606-265">不允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="04606-265">Wildcards are not permitted.</span></span>

<span data-ttu-id="04606-266">`Import-PSSession` 无法从管理单元导入提供程序。</span><span class="sxs-lookup"><span data-stu-id="04606-266">`Import-PSSession` cannot import providers from a snap-in.</span></span>

<span data-ttu-id="04606-267">有关详细信息，请参阅 [about_PSSnapins](/powershell/module/Microsoft.PowerShell.Core/About/about_PSSnapins)和 [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)。</span><span class="sxs-lookup"><span data-stu-id="04606-267">For more information, see [about_PSSnapins](/powershell/module/Microsoft.PowerShell.Core/About/about_PSSnapins) and [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04606-268">-Prefix</span><span class="sxs-lookup"><span data-stu-id="04606-268">-Prefix</span></span>

<span data-ttu-id="04606-269">为导入的命令的名称中的名词指定前缀。</span><span class="sxs-lookup"><span data-stu-id="04606-269">Specifies a prefix to the nouns in the names of imported commands.</span></span>

<span data-ttu-id="04606-270">使用此参数可避免会话中的不同命令具有相同名称时可能出现的名称冲突。</span><span class="sxs-lookup"><span data-stu-id="04606-270">Use this parameter to avoid name conflicts that might occur when different commands in the session have the same name.</span></span>

<span data-ttu-id="04606-271">例如，如果你指定前缀 "远程"，然后导入 `Get-Date` cmdlet，则该 cmdlet 将在会话中称为 `Get-RemoteDate` ，而不会与原始 `Get-Date` cmdlet 混淆。</span><span class="sxs-lookup"><span data-stu-id="04606-271">For instance, if you specify the prefix Remote and then import a `Get-Date` cmdlet, the cmdlet is known in the session as `Get-RemoteDate`, and it is not confused with the original `Get-Date` cmdlet.</span></span>

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

### <span data-ttu-id="04606-272">-Session</span><span class="sxs-lookup"><span data-stu-id="04606-272">-Session</span></span>

<span data-ttu-id="04606-273">指定从中导入 cmdlet 的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="04606-273">Specifies the **PSSession** from which the cmdlets are imported.</span></span> <span data-ttu-id="04606-274">输入包含会话对象的变量或获取会话对象的命令，例如 `New-PSSession` 或 `Get-PSSession` 命令。</span><span class="sxs-lookup"><span data-stu-id="04606-274">Enter a variable that contains a session object or a command that gets a session object, such as a `New-PSSession` or `Get-PSSession` command.</span></span> <span data-ttu-id="04606-275">仅可以指定一个会话。</span><span class="sxs-lookup"><span data-stu-id="04606-275">You can specify only one session.</span></span> <span data-ttu-id="04606-276">此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="04606-276">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="04606-277">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="04606-277">CommonParameters</span></span>

<span data-ttu-id="04606-278">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="04606-278">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="04606-279">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="04606-279">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="04606-280">输入</span><span class="sxs-lookup"><span data-stu-id="04606-280">INPUTS</span></span>

### <span data-ttu-id="04606-281">无</span><span class="sxs-lookup"><span data-stu-id="04606-281">None</span></span>

<span data-ttu-id="04606-282">不能通过管道将对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="04606-282">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="04606-283">输出</span><span class="sxs-lookup"><span data-stu-id="04606-283">OUTPUTS</span></span>

### <span data-ttu-id="04606-284">System.Management.Automation.PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="04606-284">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="04606-285">`Import-PSSession` 返回 `New-Module` 与 cmdlet 返回的相同模块对象 `Get-Module` 。</span><span class="sxs-lookup"><span data-stu-id="04606-285">`Import-PSSession` returns the same module object that `New-Module` and `Get-Module` cmdlets return.</span></span>
<span data-ttu-id="04606-286">但是，导入的模块是临时的并且仅在当前会话中存在。</span><span class="sxs-lookup"><span data-stu-id="04606-286">However, the imported module is temporary and exists only in the current session.</span></span> <span data-ttu-id="04606-287">若要在磁盘上创建永久模块，请使用 `Export-PSSession` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="04606-287">To create a permanent module on disk, use the `Export-PSSession` cmdlet.</span></span>

## <span data-ttu-id="04606-288">注释</span><span class="sxs-lookup"><span data-stu-id="04606-288">NOTES</span></span>

- <span data-ttu-id="04606-289">`Import-PSSession` 依赖于 PowerShell 远程处理基础结构。</span><span class="sxs-lookup"><span data-stu-id="04606-289">`Import-PSSession` relies on the  PowerShell remoting infrastructure.</span></span> <span data-ttu-id="04606-290">若要使用此 cmdlet，必须为 WS-Management 远程处理配置计算机。</span><span class="sxs-lookup"><span data-stu-id="04606-290">To use this cmdlet, the computer must be configured for WS-Management remoting.</span></span> <span data-ttu-id="04606-291">有关详细信息，请参阅 [about_Remote](../Microsoft.PowerShell.Core/about/about_Remote.md) 和 [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="04606-291">For more information, see [about_Remote](../Microsoft.PowerShell.Core/about/about_Remote.md) and [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md).</span></span>
- <span data-ttu-id="04606-292">`Import-PSSession` 不导入变量或 PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="04606-292">`Import-PSSession` does not import variables or  PowerShell providers.</span></span>
- <span data-ttu-id="04606-293">当你导入与当前会话中的命令具有相同名称的命令时，导入的命令可以隐藏会话中的别名、函数和 cmdlet，并且可以替换会话中的函数和变量。</span><span class="sxs-lookup"><span data-stu-id="04606-293">When you import commands that have the same names as commands in the current session, the imported commands can hide aliases, functions, and cmdlets in the session and they can replace functions and variables in the session.</span></span> <span data-ttu-id="04606-294">若要防止名称冲突，请使用 **Prefix** 参数。</span><span class="sxs-lookup"><span data-stu-id="04606-294">To prevent name conflicts, use the **Prefix** parameter.</span></span> <span data-ttu-id="04606-295">有关详细信息，请参阅 [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="04606-295">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span></span>
- <span data-ttu-id="04606-296">`Import-PSSession` 在导入所有命令之前将其转换为函数。</span><span class="sxs-lookup"><span data-stu-id="04606-296">`Import-PSSession` converts all commands into functions before it imports them.</span></span> <span data-ttu-id="04606-297">这样，导入的命令的行为与保留其原始命令类型时的行为稍有不同。</span><span class="sxs-lookup"><span data-stu-id="04606-297">As a result, imported commands behave a bit differently than they would if they retained their original command type.</span></span> <span data-ttu-id="04606-298">例如，如果从 PSSession 中导入一个 cmdlet，然后从模块或管理单元中导入具有相同名称的 cmdlet，则从 PSSession 中导入的 cmdlet 默认始终运行，因为函数优先于 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="04606-298">For example, if you import a cmdlet from a PSSession and then import a cmdlet with the same name from a module or snap-in, the cmdlet that is imported from the PSSession always runs by default because functions take precedence over cmdlets.</span></span> <span data-ttu-id="04606-299">相反，如果将别名导入到具有相同名称的别名的会话，则始终使用原来的别名，因为别名优先于函数。</span><span class="sxs-lookup"><span data-stu-id="04606-299">Conversely, if you import an alias into a session that has an alias with the same name, the original alias is always used, because aliases take precedence over functions.</span></span> <span data-ttu-id="04606-300">有关详细信息，请参阅 [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="04606-300">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md).</span></span>
- <span data-ttu-id="04606-301">`Import-PSSession` 使用 `Write-Progress` cmdlet 显示该命令的进度。</span><span class="sxs-lookup"><span data-stu-id="04606-301">`Import-PSSession` uses the `Write-Progress` cmdlet to display the progress of the command.</span></span> <span data-ttu-id="04606-302">该命令正在运行时，你可能会看到进度条。</span><span class="sxs-lookup"><span data-stu-id="04606-302">You might see the progress bar while the command is running.</span></span>
- <span data-ttu-id="04606-303">若要查找要导入的命令，请 `Import-PSSession` 使用 `Invoke-Command` Cmdlet `Get-Command` 在 PSSession 中运行命令。</span><span class="sxs-lookup"><span data-stu-id="04606-303">To find the commands to import, `Import-PSSession` uses the `Invoke-Command` cmdlet to run a `Get-Command` command in the PSSession.</span></span> <span data-ttu-id="04606-304">若要获取命令的格式设置数据，请使用 `Get-FormatData` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="04606-304">To get formatting data for the commands, it uses the `Get-FormatData` cmdlet.</span></span> <span data-ttu-id="04606-305">运行命令时，可能会看到来自这些 cmdlet 的错误消息 `Import-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="04606-305">You might see error messages from these cmdlets when you run an `Import-PSSession` command.</span></span> <span data-ttu-id="04606-306">此外， `Import-PSSession` 不能从不包括 `Get-Command` 、 `Get-FormatData` 、 `Select-Object` 和 cmdlet 的 PSSession 中导入命令 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="04606-306">Also, `Import-PSSession` cannot import commands from a PSSession that does not include the `Get-Command`, `Get-FormatData`, `Select-Object`, and `Get-Help` cmdlets.</span></span>
- <span data-ttu-id="04606-307">导入的命令与其他远程命令具有相同的限制，包括无法通过用户界面（如“记事本”）启动程序。</span><span class="sxs-lookup"><span data-stu-id="04606-307">Imported commands have the same limitations as other remote commands, including the inability to start a program with a user interface, such as Notepad.</span></span>
- <span data-ttu-id="04606-308">因为 Windows PowerShell 配置文件不在 Pssession 中运行，所以配置文件添加到会话中的命令不能用于 `Import-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="04606-308">Because Windows PowerShell profiles are not run in PSSessions, the commands that a profile adds to a session are not available to `Import-PSSession`.</span></span> <span data-ttu-id="04606-309">若要从配置文件导入命令，请在 `Invoke-Command` 导入命令之前，使用命令手动运行该配置文件。</span><span class="sxs-lookup"><span data-stu-id="04606-309">To import commands from a profile, use an `Invoke-Command` command to run the profile in the PSSession manually before importing commands.</span></span>
- <span data-ttu-id="04606-310">创建的临时模块 `Import-PSSession` 可能包含格式设置文件，即使该命令不导入格式数据也是如此。</span><span class="sxs-lookup"><span data-stu-id="04606-310">The temporary module that `Import-PSSession` creates might include a formatting file, even if the command does not import formatting data.</span></span> <span data-ttu-id="04606-311">如果该命令不导入格式数据，则创建的任何格式设置文件都不包含格式数据。</span><span class="sxs-lookup"><span data-stu-id="04606-311">If the command does not import formatting data, any formatting files that are created will not contain formatting data.</span></span>
- <span data-ttu-id="04606-312">若要使用 `Import-PSSession` ，当前会话中的执行策略不能受到限制或 AllSigned，因为创建的临时模块 `Import-PSSession` 包含这些策略所禁止的未签名的脚本文件。</span><span class="sxs-lookup"><span data-stu-id="04606-312">To use `Import-PSSession`, the execution policy in the current session cannot be Restricted or AllSigned, because the temporary module that `Import-PSSession` creates contains unsigned script files that are prohibited by these policies.</span></span> <span data-ttu-id="04606-313">若要在 `Import-PSSession` 不更改本地计算机的执行策略的情况下使用，请使用的 **作用域** 参数 `Set-ExecutionPolicy` 为单个进程设置限制性较低的执行策略。</span><span class="sxs-lookup"><span data-stu-id="04606-313">To use `Import-PSSession` without changing the execution policy for the local computer, use the **Scope** parameter of `Set-ExecutionPolicy` to set a less restrictive execution policy for a single process.</span></span>
- <span data-ttu-id="04606-314">在 Windows PowerShell 2.0 中，从另一个会话中导入的命令的帮助主题不包括通过使用 **Prefix** 参数分配的前缀。</span><span class="sxs-lookup"><span data-stu-id="04606-314">In Windows PowerShell 2.0, help topics for commands that are imported from another session do not include the prefix that you assign by using the **Prefix** parameter.</span></span> <span data-ttu-id="04606-315">若要获得 Windows PowerShell 2.0 中导入命令的帮助，请使用原始（无前缀）的命令名称。</span><span class="sxs-lookup"><span data-stu-id="04606-315">To get help for an imported command in Windows PowerShell 2.0, use the original (non-prefixed) command name.</span></span>

## <span data-ttu-id="04606-316">相关链接</span><span class="sxs-lookup"><span data-stu-id="04606-316">RELATED LINKS</span></span>

[<span data-ttu-id="04606-317">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="04606-317">Export-PSSession</span></span>](Export-PSSession.md)
