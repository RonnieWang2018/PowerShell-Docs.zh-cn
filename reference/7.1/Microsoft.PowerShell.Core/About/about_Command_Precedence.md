---
description: 描述 PowerShell 如何确定要运行哪个命令。
keywords: powershell,cmdlet
ms.date: 02/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_precedence?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Precedence
ms.openlocfilehash: 0fc514f8e7e7894ae9da281867fd3d2fe61b89b6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/13/2020
ms.locfileid: "93200462"
---
# <a name="about-command-precedence"></a><span data-ttu-id="cb6d0-104">关于命令优先级</span><span class="sxs-lookup"><span data-stu-id="cb6d0-104">About Command Precedence</span></span>

## <a name="short-description"></a><span data-ttu-id="cb6d0-105">简短说明</span><span class="sxs-lookup"><span data-stu-id="cb6d0-105">Short description</span></span>
<span data-ttu-id="cb6d0-106">描述 PowerShell 如何确定要运行哪个命令。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-106">Describes how PowerShell determines which command to run.</span></span>

## <a name="long-description"></a><span data-ttu-id="cb6d0-107">长说明</span><span class="sxs-lookup"><span data-stu-id="cb6d0-107">Long description</span></span>

<span data-ttu-id="cb6d0-108">命令优先级说明了当会话包含多个具有相同名称的命令时，PowerShell 如何确定要运行哪个命令。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-108">Command precedence describes how PowerShell determines which command to run when a session contains more than one command with the same name.</span></span> <span data-ttu-id="cb6d0-109">可以隐藏或替换会话中的命令，这些命令具有相同的名称。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-109">Commands within a session can be hidden or replaced by commands with the same name.</span></span> <span data-ttu-id="cb6d0-110">本文介绍如何运行隐藏的命令以及如何避免命令名称冲突。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-110">This article shows you how to run hidden commands and how to avoid command-name conflicts.</span></span>

## <a name="command-precedence"></a><span data-ttu-id="cb6d0-111">命令优先级</span><span class="sxs-lookup"><span data-stu-id="cb6d0-111">Command precedence</span></span>

<span data-ttu-id="cb6d0-112">当 PowerShell 会话包含多个具有相同名称的命令时，PowerShell 会使用以下规则确定要运行的命令。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-112">When a PowerShell session includes more than one command that has the same name, PowerShell determines which command to run by using the following rules.</span></span>

<span data-ttu-id="cb6d0-113">如果指定一个命令的路径，则 PowerShell 会在路径指定的位置运行该命令。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-113">If you specify the path to a command, PowerShell runs the command at the location specified by the path.</span></span>

<span data-ttu-id="cb6d0-114">例如，以下命令在 "C： TechDocs" 目录中运行 FindDocs.ps1 脚本 \\ ：</span><span class="sxs-lookup"><span data-stu-id="cb6d0-114">For example, the following command runs the FindDocs.ps1 script in the "C:\\TechDocs" directory:</span></span>

```
C:\TechDocs\FindDocs.ps1
```

<span data-ttu-id="cb6d0-115">作为一项安全功能，PowerShell 不会运行本机) 命令（包括 PowerShell 脚本） (可执行文件，除非该命令位于 Path 环境变量中列出的路径中，否则， `$env:path` 除非指定了脚本文件的路径。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-115">As a security feature, PowerShell does not run executable (native) commands, including PowerShell scripts, unless the command is located in a path that is listed in the Path environment variable `$env:path` or unless you specify the path to the script file.</span></span>

<span data-ttu-id="cb6d0-116">若要运行位于当前目录中的脚本，请指定完整路径，或键入一个 `.\` 表示当前目录的点。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-116">To run a script that is in the current directory, specify the full path, or type a dot `.\` to represent the current directory.</span></span>

<span data-ttu-id="cb6d0-117">例如，若要在当前目录中运行 FindDocs.ps1 文件，请键入：</span><span class="sxs-lookup"><span data-stu-id="cb6d0-117">For example, to run the FindDocs.ps1 file in the current directory, type:</span></span>

```
.\FindDocs.ps1
```

### <a name="using-wildcards-in-execution"></a><span data-ttu-id="cb6d0-118">在执行中使用通配符</span><span class="sxs-lookup"><span data-stu-id="cb6d0-118">Using wildcards in execution</span></span>

<span data-ttu-id="cb6d0-119">可以在命令执行中使用通配符。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-119">You may use wildcards in command execution.</span></span> <span data-ttu-id="cb6d0-120">使用通配符 *也称为组合。*</span><span class="sxs-lookup"><span data-stu-id="cb6d0-120">Using wildcard characters is also known as *globbing* .</span></span>

<span data-ttu-id="cb6d0-121">PowerShell 在文本匹配之前执行具有通配符匹配项的文件。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-121">PowerShell executes a file that has a wildcard match, before a literal match.</span></span>

<span data-ttu-id="cb6d0-122">例如，请考虑具有以下文件的目录：</span><span class="sxs-lookup"><span data-stu-id="cb6d0-122">For example, consider a directory with the following files:</span></span>

```
Get-ChildItem C:\temp\test


    Directory: C:\temp\test


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        5/20/2019   2:29 PM             28 a.ps1
-a----        5/20/2019   2:29 PM             28 [a1].ps1
```

<span data-ttu-id="cb6d0-123">这两个脚本文件具有相同的内容： `$MyInvocation.MyCommand.Path` 。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-123">Both script files have the same content: `$MyInvocation.MyCommand.Path`.</span></span>
<span data-ttu-id="cb6d0-124">此命令显示所调用的脚本的名称。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-124">This command displays the name of the script that is invoked.</span></span>

<span data-ttu-id="cb6d0-125">当你运行时 `[a1].ps1` ，将执行该文件， `a.ps1` 即使该文件 `[a1].ps1` 是文字匹配。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-125">When you run `[a1].ps1`, the file `a.ps1` is executed even though the file `[a1].ps1` is a literal match.</span></span>

```powershell
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\a.ps1
```

<span data-ttu-id="cb6d0-126">现在，让我们删除该 `a.ps1` 文件并再次尝试运行它。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-126">Now let's delete the `a.ps1` file and attempt to run it again.</span></span>

```powershell
Remove-Item C:\temp\test\a.ps1
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\[a1].ps1
```

<span data-ttu-id="cb6d0-127">你可以从运行此时间的输出中看到， `[a1].ps1` 因为文本匹配是该通配符模式的唯一文件匹配。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-127">You can see from the output that `[a1].ps1` runs this time because the literal match is the only file match for that wildcard pattern.</span></span>

<span data-ttu-id="cb6d0-128">有关 PowerShell 如何使用通配符的详细信息，请参阅 [about_Wildcards](about_Wildcards.md)。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-128">For more information about how PowerShell uses wildcards, see [about_Wildcards](about_Wildcards.md).</span></span>

> [!NOTE]
> <span data-ttu-id="cb6d0-129">若要将搜索范围限制为相对路径，必须在脚本名称前面加上 `.\` 路径。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-129">To limit the search to a relative path, you must prefix the script name with the `.\` path.</span></span> <span data-ttu-id="cb6d0-130">这会将命令搜索限制为相对路径中的文件。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-130">This limits the search for commands to files in that relative path.</span></span> <span data-ttu-id="cb6d0-131">如果没有此前缀，其他 PowerShell 语法可能会发生冲突，并且很少保证会找到该文件。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-131">Without this prefix, other PowerShell syntax may conflict and there are few guarantees that the file will be found.</span></span>

<span data-ttu-id="cb6d0-132">如果未指定路径，则在为当前会话中加载的所有项运行命令时，PowerShell 将使用以下优先顺序：</span><span class="sxs-lookup"><span data-stu-id="cb6d0-132">If you do not specify a path, PowerShell uses the following precedence order when it runs commands for all items loaded in the current session:</span></span>

  1. <span data-ttu-id="cb6d0-133">Alias</span><span class="sxs-lookup"><span data-stu-id="cb6d0-133">Alias</span></span>
  2. <span data-ttu-id="cb6d0-134">函数</span><span class="sxs-lookup"><span data-stu-id="cb6d0-134">Function</span></span>
  3. <span data-ttu-id="cb6d0-135">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cb6d0-135">Cmdlet</span></span>
  4. <span data-ttu-id="cb6d0-136">外部可执行文件 (程序和非 PowerShell 脚本) </span><span class="sxs-lookup"><span data-stu-id="cb6d0-136">External executable files (programs and non-PowerShell scripts)</span></span>

<span data-ttu-id="cb6d0-137">因此，如果键入 "help"，PowerShell 将首先查找名为的别名，然后查找名为的 `help` 函数 `Help` ，最后查找名为的 cmdlet `Help` 。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-137">Therefore, if you type "help", PowerShell first looks for an alias named `help`, then a function named `Help`, and finally a cmdlet named `Help`.</span></span> <span data-ttu-id="cb6d0-138">它会运行它找到的第一 `help` 项。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-138">It runs the first `help` item that it finds.</span></span>

<span data-ttu-id="cb6d0-139">例如，如果你的会话包含一个 cmdlet 和一个函数，并且在 `Get-Map` 你键入时， `Get-Map` PowerShell 将运行该函数。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-139">For example, if your session contains a cmdlet and a function, both named `Get-Map`, when you type `Get-Map`, PowerShell runs the function.</span></span>

> [!NOTE]
> <span data-ttu-id="cb6d0-140">这仅适用于已加载的命令。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-140">This only applies to loaded commands.</span></span> <span data-ttu-id="cb6d0-141">如果有一个 `build` 可执行文件和一个 `build` 名称为的函数的别名， `Invoke-Build` 而该模块未加载到当前会话中，则 PowerShell 将改为运行该 `build` 可执行文件。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-141">If there is a `build` executable and an Alias `build` for a function with the name of `Invoke-Build` inside a module that is not loaded into the current session, PowerShell runs the `build` executable instead.</span></span> <span data-ttu-id="cb6d0-142">如果在这种情况下找到外部可执行文件，则它不会自动加载模块。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-142">It does not auto-load modules if it finds the external executable in this case.</span></span> <span data-ttu-id="cb6d0-143">仅当找不到外部可执行文件时，才会调用具有给定名称的别名、函数或 cmdlet，从而触发其模块的自动加载。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-143">It is only when no external executable is found that an alias, function, or cmdlet with the given name is invoked, thereby triggering auto-loading of its module.</span></span>

<span data-ttu-id="cb6d0-144">如果会话包含具有相同名称的相同类型的项，则 PowerShell 将运行较新的项。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-144">When the session contains items of the same type that have the same name, PowerShell runs the newer item.</span></span>

<span data-ttu-id="cb6d0-145">例如，如果从模块导入另一个 `Get-Date` cmdlet，则在键入时 `Get-Date` ，PowerShell 将在本机上运行导入的版本。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-145">For example, if you import another `Get-Date` cmdlet from a module, when you type `Get-Date`, PowerShell runs the imported version over the native one.</span></span>

## <a name="hidden-and-replaced-items"></a><span data-ttu-id="cb6d0-146">隐藏和替换项</span><span class="sxs-lookup"><span data-stu-id="cb6d0-146">Hidden and replaced items</span></span>

<span data-ttu-id="cb6d0-147">由于这些规则，项可以被具有相同名称的项替换或隐藏。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-147">As a result of these rules, items can be replaced or hidden by items with the same name.</span></span>

<span data-ttu-id="cb6d0-148">如果仍可以访问原始项，例如通过使用模块或管理单元名称来限定项名称，则项为 "隐藏" 或 "隐藏"。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-148">Items are "hidden" or "shadowed" if you can still access the original item, such as by qualifying the item name with a module or snap-in name.</span></span>

<span data-ttu-id="cb6d0-149">例如，如果导入的函数与会话中的 cmdlet 具有相同的名称，则该 cmdlet 将隐藏 (但不替换) ，因为它是从管理单元或模块导入的。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-149">For example, if you import a function that has the same name as a cmdlet in the session, the cmdlet is hidden (but not replaced) because it was imported from a snap-in or module.</span></span>

<span data-ttu-id="cb6d0-150">如果您无法再访问原始项，则会 "替换" 或 "覆盖" 项。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-150">Items are "replaced" or "overwritten" if you can no longer access the original item.</span></span>

<span data-ttu-id="cb6d0-151">例如，如果导入的变量与会话中的变量同名，则原始变量将被替换，并且不再可访问。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-151">For example, if you import a variable that has the same name as a variable in the session, the original variable is replaced and is no longer accessible.</span></span>
<span data-ttu-id="cb6d0-152">不能使用模块名称限定变量。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-152">You cannot qualify a variable with a module name.</span></span>

<span data-ttu-id="cb6d0-153">此外，如果在命令行中键入函数，然后导入具有相同名称的函数，则原始函数会被替换并且不再可访问。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-153">Also, if you type a function at the command line and then import a function with the same name, the original function is replaced and is no longer accessible.</span></span>

### <a name="finding-hidden-commands"></a><span data-ttu-id="cb6d0-154">查找隐藏的命令</span><span class="sxs-lookup"><span data-stu-id="cb6d0-154">Finding hidden commands</span></span>

<span data-ttu-id="cb6d0-155">[Get-Command](xref:Microsoft.PowerShell.Core.Get-Command) Cmdlet 的 **all** 参数将获取具有指定名称的所有命令，即使它们已隐藏或已被替换。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-155">The **All** parameter of the [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command) cmdlet gets all commands with the specified name, even if they are hidden or replaced.</span></span> <span data-ttu-id="cb6d0-156">从 PowerShell 3.0 开始，默认情况下， `Get-Command` 仅获取键入命令名称时运行的命令。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-156">Beginning in PowerShell 3.0, by default, `Get-Command` gets only the commands that run when you type the command name.</span></span>

<span data-ttu-id="cb6d0-157">在下面的示例中，该会话包括一个 `Get-Date` 函数和一个 [获取日期](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-157">In the following examples, the session includes a `Get-Date` function and a [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet.</span></span>

<span data-ttu-id="cb6d0-158">以下命令将获取 `Get-Date` 键入时运行的命令 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-158">The following command gets the `Get-Date` command that runs when you type `Get-Date`.</span></span>

```powershell
Get-Command Get-Date
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
```

<span data-ttu-id="cb6d0-159">以下命令使用 **all** 参数获取所有 `Get-Date` 命令。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-159">The following command uses the **All** parameter to get all `Get-Date` commands.</span></span>

```powershell
Get-Command Get-Date -All
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
Cmdlet          Get-Date                  Microsoft.PowerShell.Utility
```

### <a name="running-hidden-commands"></a><span data-ttu-id="cb6d0-160">运行隐藏的命令</span><span class="sxs-lookup"><span data-stu-id="cb6d0-160">Running hidden commands</span></span>

<span data-ttu-id="cb6d0-161">可以通过指定项属性来运行特定命令，将命令与其他可能具有相同名称的命令区分开来。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-161">You can run particular commands by specifying item properties that distinguish the command from other commands that might have the same name.</span></span> <span data-ttu-id="cb6d0-162">您可以使用此方法来运行任何命令，但它对于运行隐藏命令特别有用。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-162">You can use this method to run any command, but it is especially useful for running hidden commands.</span></span>

#### <a name="qualified-names"></a><span data-ttu-id="cb6d0-163">限定名称</span><span class="sxs-lookup"><span data-stu-id="cb6d0-163">Qualified names</span></span>

<span data-ttu-id="cb6d0-164">使用 cmdlet 的模块限定名称，可运行由具有相同名称的项隐藏的命令。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-164">Using the module-qualified name of a cmdlet allows you to run commands hidden by an item with the same name.</span></span> <span data-ttu-id="cb6d0-165">例如，你可以 `Get-Date` 通过使用其模块名称 " **Microsoft PowerShell** " 来对其进行限定来运行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-165">For example, you can run the `Get-Date` cmdlet by qualifying it with its module name **Microsoft.PowerShell.Utility** .</span></span>

<span data-ttu-id="cb6d0-166">编写要分发的脚本时，请使用此首选方法。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-166">Use this preferred method when writing scripts that you intend to distribute.</span></span> <span data-ttu-id="cb6d0-167">您无法预测运行脚本的会话中可能出现哪些命令。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-167">You cannot predict which commands might be present in the session in which the script runs.</span></span>

```powershell
New-Alias -Name "Get-Date" -Value "Get-ChildItem"
Microsoft.PowerShell.Utility\Get-Date
```

```output
Tuesday, September 4, 2018 8:17:25 AM
```

<span data-ttu-id="cb6d0-168">若要运行 `New-Map` 模块添加的命令 `MapFunctions` ，请使用其模块限定名称：</span><span class="sxs-lookup"><span data-stu-id="cb6d0-168">To run a `New-Map` command that was added by the `MapFunctions` module, use its module-qualified name:</span></span>

```powershell
MapFunctions\New-Map
```

<span data-ttu-id="cb6d0-169">若要查找从其导入命令的模块，请使用命令的 **ModuleName** 属性。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-169">To find the module from which a command was imported, use the **ModuleName** property of commands.</span></span>

```
(Get-Command <command-name>).ModuleName
```

<span data-ttu-id="cb6d0-170">例如，若要查找 cmdlet 的源 `Get-Date` ，请键入：</span><span class="sxs-lookup"><span data-stu-id="cb6d0-170">For example, to find the source of the `Get-Date` cmdlet, type:</span></span>

```powershell
(Get-Command Get-Date).ModuleName
```

```output
Microsoft.PowerShell.Utility
```

> [!NOTE]
> <span data-ttu-id="cb6d0-171">不能限定变量或别名。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-171">You cannot qualify variables or aliases.</span></span>

#### <a name="call-operator"></a><span data-ttu-id="cb6d0-172">Call 运算符</span><span class="sxs-lookup"><span data-stu-id="cb6d0-172">Call operator</span></span>

<span data-ttu-id="cb6d0-173">你还可以使用 `Call` 运算符 `&` 来运行隐藏的命令，方法是将其与 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem) (别名为 "Dir" ) `Get-Command` 或 [get-help](xref:Microsoft.PowerShell.Core.Get-Module)。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-173">You can also use the `Call` operator `&` to run hidden commands by combining it with a call to [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) (the alias is "dir"), `Get-Command` or [Get-Module](xref:Microsoft.PowerShell.Core.Get-Module).</span></span>

<span data-ttu-id="cb6d0-174">调用运算符在子范围内执行字符串和脚本块。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-174">The call operator executes strings and script blocks in a child scope.</span></span> <span data-ttu-id="cb6d0-175">有关详细信息，请参阅 [about_Operators](about_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-175">For more information, see [about_Operators](about_Operators.md).</span></span>

<span data-ttu-id="cb6d0-176">例如，如果你有一个名为的函数， `Map` 该函数被名为的别名隐藏 `Map` ，请使用以下命令运行该函数。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-176">For example, if you have a function named `Map` that is hidden by an alias named `Map`, use the following command to run the function.</span></span>

```powershell
&(Get-Command -Name Map -CommandType Function)
```

<span data-ttu-id="cb6d0-177">或</span><span class="sxs-lookup"><span data-stu-id="cb6d0-177">or</span></span>

```powershell
&(dir Function:\map)
```

<span data-ttu-id="cb6d0-178">你还可以将隐藏命令保存在变量中，以使其更易于运行。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-178">You can also save your hidden command in a variable to make it easier to run.</span></span>

<span data-ttu-id="cb6d0-179">例如，下面的命令将函数保存 `Map` 在变量中 `$myMap` ，然后使用 `Call` 运算符来运行该函数。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-179">For example, the following command saves the `Map` function in the `$myMap` variable and then uses the `Call` operator to run it.</span></span>

```powershell
$myMap = (Get-Command -Name map -CommandType function)
&($myMap)
```

### <a name="replaced-items"></a><span data-ttu-id="cb6d0-180">替换项</span><span class="sxs-lookup"><span data-stu-id="cb6d0-180">Replaced items</span></span>

<span data-ttu-id="cb6d0-181">"替换" 项是你不能再访问的项。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-181">A "replaced" item is one that you can no longer access.</span></span> <span data-ttu-id="cb6d0-182">可以通过从模块或管理单元中导入具有相同名称的项来替换项。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-182">You can replace items by importing items of the same name from a module or snap-in.</span></span>

<span data-ttu-id="cb6d0-183">例如，如果在 `Get-Map` 会话中键入函数，并导入名为的函数 `Get-Map` ，则该函数将替换原始函数。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-183">For example, if you type a `Get-Map` function in your session, and you import a function called `Get-Map`, it replaces the original function.</span></span> <span data-ttu-id="cb6d0-184">你无法在当前会话中检索它。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-184">You cannot retrieve it in the current session.</span></span>

<span data-ttu-id="cb6d0-185">变量和别名不能隐藏，因为不能使用调用运算符或限定名来运行它们。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-185">Variables and aliases cannot be hidden because you cannot use a call operator or a qualified name to run them.</span></span> <span data-ttu-id="cb6d0-186">从模块或管理单元中导入变量和别名时，它们会将会话中的变量替换为同一名称。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-186">When you import variables and aliases from a module or snap-in, they replace variables in the session with the same name.</span></span>

### <a name="avoiding-name-conflicts"></a><span data-ttu-id="cb6d0-187">避免名称冲突</span><span class="sxs-lookup"><span data-stu-id="cb6d0-187">Avoiding name conflicts</span></span>

<span data-ttu-id="cb6d0-188">管理命令名称冲突的最佳方式是阻止这些冲突。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-188">The best way to manage command name conflicts is to prevent them.</span></span> <span data-ttu-id="cb6d0-189">为命令命名时，使用唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-189">When you name your commands, use a unique name.</span></span> <span data-ttu-id="cb6d0-190">例如，将首字母缩写或公司名称缩写添加到命令中的名词。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-190">For example, add your initials or company name acronym to the nouns in your commands.</span></span>

<span data-ttu-id="cb6d0-191">此外，当你将命令从 PowerShell 模块或其他会话导入到会话时，请使用 `Prefix` [import-module](xref:Microsoft.PowerShell.Core.Import-Module) 的参数或</span><span class="sxs-lookup"><span data-stu-id="cb6d0-191">Also, when you import commands into your session from a PowerShell module or from another session, use the `Prefix` parameter of the [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module) or</span></span>

<span data-ttu-id="cb6d0-192">[Import-module](xref:Microsoft.PowerShell.Utility.Import-PSSession) cmdlet 将前缀添加到命令名称中的名词。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-192">[Import-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession) cmdlet to add a prefix to the nouns in the names of commands.</span></span>

<span data-ttu-id="cb6d0-193">例如，以下命令可避免与 `Get-Date` `Set-Date` 导入模块时 PowerShell 附带的和 cmdlet 发生冲突 `DateFunctions` 。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-193">For example, the following command avoids any conflict with the `Get-Date` and `Set-Date` cmdlets that come with PowerShell when you import the `DateFunctions` module.</span></span>

```powershell
Import-Module -Name DateFunctions -Prefix ZZ
```

<span data-ttu-id="cb6d0-194">有关详细信息，请参阅 `Import-Module` 和 `Import-PSSession` 下面的。</span><span class="sxs-lookup"><span data-stu-id="cb6d0-194">For more information, see `Import-Module` and `Import-PSSession` below.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb6d0-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cb6d0-195">See also</span></span>

- [<span data-ttu-id="cb6d0-196">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="cb6d0-196">about_Path_Syntax</span></span>](about_Path_Syntax.md)
- [<span data-ttu-id="cb6d0-197">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="cb6d0-197">about_Aliases</span></span>](about_Aliases.md)
- [<span data-ttu-id="cb6d0-198">about_Functions</span><span class="sxs-lookup"><span data-stu-id="cb6d0-198">about_Functions</span></span>](about_Functions.md)
- [<span data-ttu-id="cb6d0-199">Alias-Provider</span><span class="sxs-lookup"><span data-stu-id="cb6d0-199">Alias-Provider</span></span>](../../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)
- [<span data-ttu-id="cb6d0-200">Function-Provider</span><span class="sxs-lookup"><span data-stu-id="cb6d0-200">Function-Provider</span></span>](../../Microsoft.PowerShell.Core/About/about_Function_Provider.md)
- [<span data-ttu-id="cb6d0-201">Get-Command</span><span class="sxs-lookup"><span data-stu-id="cb6d0-201">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)
- [<span data-ttu-id="cb6d0-202">Import-Module</span><span class="sxs-lookup"><span data-stu-id="cb6d0-202">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)
- [<span data-ttu-id="cb6d0-203">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="cb6d0-203">Import-PSSession</span></span>](xref:Microsoft.PowerShell.Utility.Import-PSSession)

