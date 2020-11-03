---
description: 说明如何使用 `pwsh` 命令行界面。 显示命令行参数并描述语法。
keywords: powershell,cmdlet
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pwsh
ms.openlocfilehash: 549c99fa618e2e53aed8945d95e92f97117aa6c9
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2020
ms.locfileid: "93200594"
---
# <a name="about-pwsh"></a><span data-ttu-id="012e7-105">关于 pwsh</span><span class="sxs-lookup"><span data-stu-id="012e7-105">About pwsh</span></span>

## <a name="short-description"></a><span data-ttu-id="012e7-106">简短说明</span><span class="sxs-lookup"><span data-stu-id="012e7-106">Short Description</span></span>
<span data-ttu-id="012e7-107">说明如何使用 `pwsh` 命令行界面。</span><span class="sxs-lookup"><span data-stu-id="012e7-107">Explains how to use the `pwsh` command-line interface.</span></span> <span data-ttu-id="012e7-108">显示命令行参数并描述语法。</span><span class="sxs-lookup"><span data-stu-id="012e7-108">Displays the command-line parameters and describes the syntax.</span></span>

## <a name="long-description"></a><span data-ttu-id="012e7-109">详细说明</span><span class="sxs-lookup"><span data-stu-id="012e7-109">Long Description</span></span>

## <a name="syntax"></a><span data-ttu-id="012e7-110">语法</span><span class="sxs-lookup"><span data-stu-id="012e7-110">Syntax</span></span>

```
pwsh[.exe]
   [[-File] <filePath> [args]]
   [-Command { - | <script-block> [-args <arg-array>]
                 | <string> [<CommandParameters>] } ]
   [-ConfigurationName <string>]
   [-CustomPipeName <string>]
   [-EncodedCommand <Base64EncodedCommand>]
   [-ExecutionPolicy <ExecutionPolicy>]
   [-InputFormat {Text | XML}]
   [-Interactive]
   [-NoExit]
   [-NoLogo]
   [-NonInteractive]
   [-NoProfile]
   [-OutputFormat {Text | XML}]
   [-SettingsFile <SettingsFilePath>]
   [-Version]
   [-WindowStyle <style>]
   [-WorkingDirectory <directoryPath>]

pwsh[.exe] -h | -Help | -? | /?
```

## <a name="parameters"></a><span data-ttu-id="012e7-111">parameters</span><span class="sxs-lookup"><span data-stu-id="012e7-111">Parameters</span></span>

<span data-ttu-id="012e7-112">所有参数都不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="012e7-112">All parameters are case-insensitive.</span></span>

### <a name="-file---f"></a><span data-ttu-id="012e7-113">-File |-f</span><span class="sxs-lookup"><span data-stu-id="012e7-113">-File | -f</span></span>

<span data-ttu-id="012e7-114">如果的值 `File` 为 `-` ，则从标准输入读取命令文本。</span><span class="sxs-lookup"><span data-stu-id="012e7-114">If the value of `File` is `-`, the command text is read from standard input.</span></span>
<span data-ttu-id="012e7-115">运行时 `pwsh -File -` 不使用重定向标准输入会启动常规会话。</span><span class="sxs-lookup"><span data-stu-id="012e7-115">Running `pwsh -File -` without redirected standard input starts a regular session.</span></span> <span data-ttu-id="012e7-116">这与根本不指定 `File` 参数相同。</span><span class="sxs-lookup"><span data-stu-id="012e7-116">This is the same as not specifying the `File` parameter at all.</span></span>

<span data-ttu-id="012e7-117">如果不存在任何参数，但命令行中存在值，则这是默认参数。</span><span class="sxs-lookup"><span data-stu-id="012e7-117">This is the default parameter if no parameters are present but values are present in the command line.</span></span> <span data-ttu-id="012e7-118">指定的脚本在本地作用域中运行 ( "点端" ) ，以便脚本创建的函数和变量在当前会话中可用。</span><span class="sxs-lookup"><span data-stu-id="012e7-118">The specified script runs in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="012e7-119">输入脚本文件路径和任何参数。</span><span class="sxs-lookup"><span data-stu-id="012e7-119">Enter the script file path and any parameters.</span></span> <span data-ttu-id="012e7-120">File 必须是命令中的最后一个参数，因为在文件参数名称后键入的所有字符都会被解释为后跟脚本参数的脚本文件路径。</span><span class="sxs-lookup"><span data-stu-id="012e7-120">File must be the last parameter in the command, because all characters typed after the File parameter name are interpreted as the script file path followed by the script parameters.</span></span>

<span data-ttu-id="012e7-121">通常，将包括或忽略脚本的开关参数。</span><span class="sxs-lookup"><span data-stu-id="012e7-121">Typically, the switch parameters of a script are either included or omitted.</span></span>
<span data-ttu-id="012e7-122">例如，以下命令使用 Get-Script.ps1 脚本文件的 All 参数： `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="012e7-122">For example, the following command uses the All parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

<span data-ttu-id="012e7-123">在极少数情况下，可能需要为开关参数提供一个 **布尔** 值。</span><span class="sxs-lookup"><span data-stu-id="012e7-123">In rare cases, you might need to provide a **Boolean** value for a switch parameter.</span></span> <span data-ttu-id="012e7-124">若要在 **File** 参数的值中为开关参数提供 **布尔** 值，请使用后面紧跟冒号和布尔值的参数，如下所示： `-File .\Get-Script.ps1 -All:$False` 。</span><span class="sxs-lookup"><span data-stu-id="012e7-124">To provide a **Boolean** value for a switch parameter in the value of the **File** parameter, Use the parameter normally followed immediately by a colon and the boolean value, such as the following: `-File .\Get-Script.ps1 -All:$False`.</span></span>

<span data-ttu-id="012e7-125">传递给脚本的参数作为文字字符串（在当前 shell 的解释后）传递。</span><span class="sxs-lookup"><span data-stu-id="012e7-125">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="012e7-126">例如，如果你在中， `cmd.exe` 并且想要传递环境变量值，则应使用 `cmd.exe` 语法： `pwsh -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="012e7-126">For example, if you are in `cmd.exe` and want to pass an environment variable value, you would use the `cmd.exe` syntax: `pwsh -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="012e7-127">相反，在脚本中运行将 `pwsh -File .\test.ps1 -TestParam $env:windir` `cmd.exe` 导致接收文本字符串， `$env:windir` 因为它对当前 shell 没有特殊意义 `cmd.exe` 。</span><span class="sxs-lookup"><span data-stu-id="012e7-127">In contrast, running `pwsh -File .\test.ps1 -TestParam $env:windir` in `cmd.exe` results in the script receiving the literal string `$env:windir` because it has no special meaning to the current `cmd.exe` shell.</span></span> <span data-ttu-id="012e7-128">`$env:windir`_可以_ 在 **命令** 参数中使用环境变量引用的样式，因为它被解释为 PowerShell 代码。</span><span class="sxs-lookup"><span data-stu-id="012e7-128">The `$env:windir` style of environment variable reference _can_ be used inside a **Command** parameter, since there it is interpreted as PowerShell code.</span></span>

<span data-ttu-id="012e7-129">同样，如果您想要从 _批处理脚本_ 执行相同的命令，则可以使用 `%~dp0` 而不是 `.\` 或 `$PSScriptRoot` 来表示当前执行目录： `pwsh -File %~dp0test.ps1 -TestParam %windir%` 。</span><span class="sxs-lookup"><span data-stu-id="012e7-129">Similarly, if you want to execute the same command from a _Batch script_ , you would use `%~dp0` instead of `.\` or `$PSScriptRoot` to represent the current execution directory: `pwsh -File %~dp0test.ps1 -TestParam %windir%`.</span></span> <span data-ttu-id="012e7-130">如果你使用 `.\test.ps1` ，则 PowerShell 将引发错误，因为它无法找到文本路径 `.\test.ps1`</span><span class="sxs-lookup"><span data-stu-id="012e7-130">If you instead used `.\test.ps1`, PowerShell would throw an error because it cannot find the literal path `.\test.ps1`</span></span>

<span data-ttu-id="012e7-131">当脚本文件以命令结束时 `exit` ，进程退出代码将设置为与命令一起使用的数值参数 `exit` 。</span><span class="sxs-lookup"><span data-stu-id="012e7-131">When the script file terminates with an `exit` command, the process exit code is set to the numeric argument used with the `exit` command.</span></span> <span data-ttu-id="012e7-132">如果正常终止，则始终会出现退出代码 `0` 。</span><span class="sxs-lookup"><span data-stu-id="012e7-132">With normal termination, the exit code is always `0`.</span></span>

<span data-ttu-id="012e7-133">类似于 `-Command` ，当发生脚本终止错误时，退出代码将设置为 `1` 。</span><span class="sxs-lookup"><span data-stu-id="012e7-133">Similar to `-Command`, when a script-terminating error occurs, the exit code is set to `1`.</span></span> <span data-ttu-id="012e7-134">不过，与不同的 `-Command` 是，在通过<kbd>Ctrl</kbd>C 中断执行时， - <kbd>C</kbd>退出代码为 `0` 。</span><span class="sxs-lookup"><span data-stu-id="012e7-134">However, unlike with `-Command`, when the execution is interrupted with <kbd>Ctrl</kbd>-<kbd>C</kbd> the exit code is `0`.</span></span>

### <a name="-command---c"></a><span data-ttu-id="012e7-135">-Command |-c</span><span class="sxs-lookup"><span data-stu-id="012e7-135">-Command | -c</span></span>

<span data-ttu-id="012e7-136">执行指定的命令 (和任何) 参数，如同在 PowerShell 命令提示符下键入一样，然后退出，除非 `NoExit` 指定了参数。</span><span class="sxs-lookup"><span data-stu-id="012e7-136">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the `NoExit` parameter is specified.</span></span>

<span data-ttu-id="012e7-137">**Command** 的值可以是 `-` 、脚本块或字符串。</span><span class="sxs-lookup"><span data-stu-id="012e7-137">The value of **Command** can be `-`, a script block, or a string.</span></span> <span data-ttu-id="012e7-138">如果 **command** 的值为，则将 `-` 从标准输入读取命令文本。</span><span class="sxs-lookup"><span data-stu-id="012e7-138">If the value of **Command** is `-`, the command text is read from standard input.</span></span>

<span data-ttu-id="012e7-139">仅当 **命令** 参数可以将传递给 **Command** 的值识别为 **ScriptBlock** 类型时，才接受脚本块执行。</span><span class="sxs-lookup"><span data-stu-id="012e7-139">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to **Command** as a **ScriptBlock** type.</span></span> <span data-ttu-id="012e7-140">_仅_ 当 `pwsh` 从另一个 PowerShell 主机运行时，才可能出现这种情况。</span><span class="sxs-lookup"><span data-stu-id="012e7-140">This is _only_ possible when running `pwsh` from another PowerShell host.</span></span> <span data-ttu-id="012e7-141">**ScriptBlock** 类型可能包含在从表达式返回的现有变量中，或由 PowerShell 主机分析为括在大括号中的文本脚本块 (`{}`) ，然后再传递到 `pwsh` 。</span><span class="sxs-lookup"><span data-stu-id="012e7-141">The **ScriptBlock** type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces (`{}`), before being passed to `pwsh`.</span></span>

```powershell
pwsh -Command {Get-WinEvent -LogName security}
```

<span data-ttu-id="012e7-142">在中 `cmd.exe` ，没有脚本块 (或 **ScriptBlock** 类型) ，因此传递给 **Command** 的值 _始终_ 为字符串。</span><span class="sxs-lookup"><span data-stu-id="012e7-142">In `cmd.exe`, there is no such thing as a script block (or **ScriptBlock** type), so the value passed to **Command** will _always_ be a string.</span></span> <span data-ttu-id="012e7-143">可以在字符串中编写一个脚本块，但它不会被执行，该脚本块的行为与你在典型 PowerShell 提示符中键入它的行为完全相同，即将脚本块内容输出出来返还给你。</span><span class="sxs-lookup"><span data-stu-id="012e7-143">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="012e7-144">传递给 **命令** 的字符串仍作为 PowerShell 代码执行，因此，在从运行时，在第一位置通常不需要脚本块大括号 `cmd.exe` 。</span><span class="sxs-lookup"><span data-stu-id="012e7-144">A string passed to **Command** is still executed as PowerShell code, so the script block curly braces are often not required in the first place when running from `cmd.exe`.</span></span> <span data-ttu-id="012e7-145">要执行在字符串中定义的内联脚本块，可以使用[调用操作符](about_operators.md#special-operators) `&`：</span><span class="sxs-lookup"><span data-stu-id="012e7-145">To execute an inline script block defined inside a string, the [call operator](about_operators.md#special-operators) `&` can be used:</span></span>

```
pwsh -Command "& {Get-WinEvent -LogName security}"
```

<span data-ttu-id="012e7-146">如果 **command** 的值为字符串，则 **command** 必须是 pwsh 的最后一个参数，因为其后面的所有参数都将解释为要执行的命令的一部分。</span><span class="sxs-lookup"><span data-stu-id="012e7-146">If the value of **Command** is a string, **Command** must be the last parameter for pwsh, because all arguments following it are interpreted as part of the command to execute.</span></span>

<span data-ttu-id="012e7-147">从现有 PowerShell 会话内调用时，结果将作为反序列化 XML 对象（而非活动对象）返回到父外壳程序。</span><span class="sxs-lookup"><span data-stu-id="012e7-147">When called from within an existing PowerShell session, the results are returned to the parent shell as deserialized XML objects, not live objects.</span></span> <span data-ttu-id="012e7-148">对于其他 shell，结果将作为字符串返回。</span><span class="sxs-lookup"><span data-stu-id="012e7-148">For other shells, the results are returned as strings.</span></span>

<span data-ttu-id="012e7-149">如果 **command** 的值为，则将 `-` 从标准输入读取命令文本。</span><span class="sxs-lookup"><span data-stu-id="012e7-149">If the value of **Command** is `-`, the command text is read from standard input.</span></span> <span data-ttu-id="012e7-150">使用带有标准输入的 **命令** 参数时，必须重定向标准输入。</span><span class="sxs-lookup"><span data-stu-id="012e7-150">You must redirect standard input when using the **Command** parameter with standard input.</span></span> <span data-ttu-id="012e7-151">例如：</span><span class="sxs-lookup"><span data-stu-id="012e7-151">For example:</span></span>

```powershell
@'
"in"

"hi" |
  % { "$_ there" }

"out"
'@ | powershell -NoProfile -Command -
```

<span data-ttu-id="012e7-152">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="012e7-152">This example produces the following output:</span></span>

```Output
in
hi there
out
```

<span data-ttu-id="012e7-153">进程退出代码由脚本块内最后 (执行) 命令的状态确定。</span><span class="sxs-lookup"><span data-stu-id="012e7-153">The process exit code is determined by status of the last (executed) command within the script block.</span></span> <span data-ttu-id="012e7-154">退出代码为 `0` 时为 `$?` `$true` 或 `1` 何时为时 `$?` `$false` 。</span><span class="sxs-lookup"><span data-stu-id="012e7-154">The exit code is `0` when `$?` is `$true` or `1` when `$?` is `$false`.</span></span> <span data-ttu-id="012e7-155">如果最后一个命令是外部程序或 PowerShell 脚本，它显式设置除或之外的退出代码 `0` `1` ，则会将该退出代码转换为以 `1` 处理退出代码。</span><span class="sxs-lookup"><span data-stu-id="012e7-155">If the last command is an external program or a PowerShell script that explicitly sets an exit code other than `0` or `1`, that exit code is converted to `1` for process exit code.</span></span> <span data-ttu-id="012e7-156">若要保留特定退出代码，请将添加 `exit $LASTEXITCODE` 到命令字符串或脚本块。</span><span class="sxs-lookup"><span data-stu-id="012e7-156">To preserve the specific exit code, add `exit $LASTEXITCODE` to your command string or script block.</span></span>

<span data-ttu-id="012e7-157">同样，当脚本终止 (运行空间终止) 错误（如或）时，将返回值1， `throw` `-ErrorAction Stop` 或在使用<kbd>Ctrl</kbd> - <kbd>C</kbd>中断执行时进行。</span><span class="sxs-lookup"><span data-stu-id="012e7-157">Similarly, the value 1 is returned when a script-terminating (runspace-terminating) error, such as a `throw` or `-ErrorAction Stop`, occurs or when execution is interrupted with <kbd>Ctrl</kbd>-<kbd>C</kbd>.</span></span>

### <a name="-configurationname---config"></a><span data-ttu-id="012e7-158">-ConfigurationName |-config</span><span class="sxs-lookup"><span data-stu-id="012e7-158">-ConfigurationName | -config</span></span>

<span data-ttu-id="012e7-159">指定运行 PowerShell 的配置终结点。</span><span class="sxs-lookup"><span data-stu-id="012e7-159">Specifies a configuration endpoint in which PowerShell is run.</span></span> <span data-ttu-id="012e7-160">这可以是在本地计算机上注册的任何终结点，包括默认 PowerShell 远程处理终结点或具有特定用户角色功能的自定义终结点。</span><span class="sxs-lookup"><span data-stu-id="012e7-160">This can be any endpoint registered on the local machine including the default PowerShell remoting endpoints or a custom endpoint having specific user role capabilities.</span></span>

<span data-ttu-id="012e7-161">示例： `pwsh -ConfigurationName AdminRoles`</span><span class="sxs-lookup"><span data-stu-id="012e7-161">Example: `pwsh -ConfigurationName AdminRoles`</span></span>

### <a name="-custompipename"></a><span data-ttu-id="012e7-162">-CustomPipeName</span><span class="sxs-lookup"><span data-stu-id="012e7-162">-CustomPipeName</span></span>

<span data-ttu-id="012e7-163">指定用于调试的额外 IPC 服务器 (命名管道) 使用的名称，以及其他跨进程通信。</span><span class="sxs-lookup"><span data-stu-id="012e7-163">Specifies the name to use for an additional IPC server (named pipe) used for debugging and other cross-process communication.</span></span> <span data-ttu-id="012e7-164">这提供了一种可预测的连接到其他 PowerShell 实例的机制。</span><span class="sxs-lookup"><span data-stu-id="012e7-164">This offers a predictable mechanism for connecting to other PowerShell instances.</span></span> <span data-ttu-id="012e7-165">通常与上的 **CustomPipeName** 参数一起使用 `Enter-PSHostProcess` 。</span><span class="sxs-lookup"><span data-stu-id="012e7-165">Typically used with the **CustomPipeName** parameter on `Enter-PSHostProcess`.</span></span>

<span data-ttu-id="012e7-166">此参数是在 PowerShell 6.2 中引入的。</span><span class="sxs-lookup"><span data-stu-id="012e7-166">This parameter was introduced in PowerShell 6.2.</span></span>

<span data-ttu-id="012e7-167">例如：</span><span class="sxs-lookup"><span data-stu-id="012e7-167">For example:</span></span>

```powershell
# PowerShell instance 1
pwsh -CustomPipeName mydebugpipe
# PowerShell instance 2
Enter-PSHostProcess -CustomPipeName mydebugpipe
```

### <a name="-encodedcommand---e---ec"></a><span data-ttu-id="012e7-168">-EncodedCommand |-e |-ec</span><span class="sxs-lookup"><span data-stu-id="012e7-168">-EncodedCommand | -e | -ec</span></span>

<span data-ttu-id="012e7-169">接受命令的 Base64 编码字符串版本。</span><span class="sxs-lookup"><span data-stu-id="012e7-169">Accepts a Base64-encoded string version of a command.</span></span> <span data-ttu-id="012e7-170">使用此参数将命令提交到需要复杂的嵌套引号的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="012e7-170">Use this parameter to submit commands to PowerShell that require complex, nested quoting.</span></span> <span data-ttu-id="012e7-171">Base64 表示形式必须是 UTF-16 编码的字符串。</span><span class="sxs-lookup"><span data-stu-id="012e7-171">The Base64 representation must be a UTF-16 encoded string.</span></span>

<span data-ttu-id="012e7-172">例如：</span><span class="sxs-lookup"><span data-stu-id="012e7-172">For example:</span></span>

```powershell
$command = 'dir "c:\program files" '
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
pwsh -encodedcommand $encodedCommand
```

### <a name="-executionpolicy---ex---ep"></a><span data-ttu-id="012e7-173">-Set-executionpolicy |-ex |-ep</span><span class="sxs-lookup"><span data-stu-id="012e7-173">-ExecutionPolicy | -ex | -ep</span></span>

<span data-ttu-id="012e7-174">为当前会话设置默认执行策略，并将其保存在 `$env:PSExecutionPolicyPreference` 环境变量中。</span><span class="sxs-lookup"><span data-stu-id="012e7-174">Sets the default execution policy for the current session and saves it in the `$env:PSExecutionPolicyPreference` environment variable.</span></span> <span data-ttu-id="012e7-175">此参数不会更改永久配置的执行策略。</span><span class="sxs-lookup"><span data-stu-id="012e7-175">This parameter does not change the persistently configured execution policies.</span></span>

<span data-ttu-id="012e7-176">此参数仅适用于 Windows 计算机。</span><span class="sxs-lookup"><span data-stu-id="012e7-176">This parameter only applies to Windows computers.</span></span> <span data-ttu-id="012e7-177">`$env:PSExecutionPolicyPreference`环境变量在非 Windows 平台上不存在。</span><span class="sxs-lookup"><span data-stu-id="012e7-177">The `$env:PSExecutionPolicyPreference` environment variable does not exist on non-Windows platforms.</span></span>

### <a name="-inputformat---in---if"></a><span data-ttu-id="012e7-178">-InputFormat |-in |-如果</span><span class="sxs-lookup"><span data-stu-id="012e7-178">-InputFormat | -in | -if</span></span>

<span data-ttu-id="012e7-179">描述发送到 PowerShell 的数据格式。</span><span class="sxs-lookup"><span data-stu-id="012e7-179">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="012e7-180">有效值为“Text”（文本字符串）或“XML”（序列化 CLIXML 格式）。</span><span class="sxs-lookup"><span data-stu-id="012e7-180">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-interactive---i"></a><span data-ttu-id="012e7-181">-Interactive |-i</span><span class="sxs-lookup"><span data-stu-id="012e7-181">-Interactive | -i</span></span>

<span data-ttu-id="012e7-182">向用户显示交互式提示。</span><span class="sxs-lookup"><span data-stu-id="012e7-182">Present an interactive prompt to the user.</span></span> <span data-ttu-id="012e7-183">非交互式参数的反向。</span><span class="sxs-lookup"><span data-stu-id="012e7-183">Inverse for NonInteractive parameter.</span></span>

### <a name="-noexit---noe"></a><span data-ttu-id="012e7-184">-NoExit |-noe</span><span class="sxs-lookup"><span data-stu-id="012e7-184">-NoExit | -noe</span></span>

<span data-ttu-id="012e7-185">运行启动命令后不退出。</span><span class="sxs-lookup"><span data-stu-id="012e7-185">Does not exit after running startup commands.</span></span>

<span data-ttu-id="012e7-186">示例： `pwsh -NoExit -Command Get-Date`</span><span class="sxs-lookup"><span data-stu-id="012e7-186">Example: `pwsh -NoExit -Command Get-Date`</span></span>

### <a name="-nologo---nol"></a><span data-ttu-id="012e7-187">-NoLogo |-nol</span><span class="sxs-lookup"><span data-stu-id="012e7-187">-NoLogo | -nol</span></span>

<span data-ttu-id="012e7-188">交互式会话启动时隐藏版权横幅。</span><span class="sxs-lookup"><span data-stu-id="012e7-188">Hides the copyright banner at startup of interactive sessions.</span></span>

### <a name="-noninteractive---noni"></a><span data-ttu-id="012e7-189">-非交互式 |-noni</span><span class="sxs-lookup"><span data-stu-id="012e7-189">-NonInteractive | -noni</span></span>

<span data-ttu-id="012e7-190">不向用户显示交互式提示。</span><span class="sxs-lookup"><span data-stu-id="012e7-190">Does not present an interactive prompt to the user.</span></span> <span data-ttu-id="012e7-191">尝试使用交互式功能（如 `Read-Host` 或确认提示）会导致语句终止错误。</span><span class="sxs-lookup"><span data-stu-id="012e7-191">Any attempts to use interactive features, like `Read-Host` or confirmation prompts, result in statement-terminating errors.</span></span>

### <a name="-noprofile---nop"></a><span data-ttu-id="012e7-192">-NoProfile |-nop</span><span class="sxs-lookup"><span data-stu-id="012e7-192">-NoProfile | -nop</span></span>

<span data-ttu-id="012e7-193">不加载 PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="012e7-193">Does not load the PowerShell profiles.</span></span>

### <a name="-outputformat---o---of"></a><span data-ttu-id="012e7-194">-OutputFormat |-o |-of</span><span class="sxs-lookup"><span data-stu-id="012e7-194">-OutputFormat | -o | -of</span></span>

<span data-ttu-id="012e7-195">确定 PowerShell 输出内容的格式。</span><span class="sxs-lookup"><span data-stu-id="012e7-195">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="012e7-196">有效值为“Text”（文本字符串）或“XML”（序列化 CLIXML 格式）。</span><span class="sxs-lookup"><span data-stu-id="012e7-196">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

<span data-ttu-id="012e7-197">示例： `pwsh -o XML -c Get-Date`</span><span class="sxs-lookup"><span data-stu-id="012e7-197">Example: `pwsh -o XML -c Get-Date`</span></span>

<span data-ttu-id="012e7-198">在 PowerShell 会话限调用时，会将反序列化的对象作为输出而不是纯字符串获取。</span><span class="sxs-lookup"><span data-stu-id="012e7-198">When called withing a PowerShell session, you get deserialized objects as output rather plain strings.</span></span> <span data-ttu-id="012e7-199">从其他 shell 调用时，输出是格式为 EXPORT-CLIXML 文本的字符串数据。</span><span class="sxs-lookup"><span data-stu-id="012e7-199">When called from other shells, the output is string data formatted as CLIXML text.</span></span>

### <a name="-settingsfile---settings"></a><span data-ttu-id="012e7-200">-SettingsFile |-设置</span><span class="sxs-lookup"><span data-stu-id="012e7-200">-SettingsFile | -settings</span></span>

<span data-ttu-id="012e7-201">替代会话的系统范围 `powershell.config.json` 设置文件。</span><span class="sxs-lookup"><span data-stu-id="012e7-201">Overrides the system-wide `powershell.config.json` settings file for the session.</span></span> <span data-ttu-id="012e7-202">默认情况下，系统范围内的设置将从 `powershell.config.json` 目录中的中读取 `$PSHOME` 。</span><span class="sxs-lookup"><span data-stu-id="012e7-202">By default, system-wide settings are read from the `powershell.config.json` in the `$PSHOME` directory.</span></span>

<span data-ttu-id="012e7-203">请注意，参数指定的终结点不使用这些设置 `-ConfigurationName` 。</span><span class="sxs-lookup"><span data-stu-id="012e7-203">Note that these settings are not used by the endpoint specified by the `-ConfigurationName` argument.</span></span>

<span data-ttu-id="012e7-204">示例： `pwsh -SettingsFile c:\myproject\powershell.config.json`</span><span class="sxs-lookup"><span data-stu-id="012e7-204">Example: `pwsh -SettingsFile c:\myproject\powershell.config.json`</span></span>

### <a name="-sshservermode---sshs"></a><span data-ttu-id="012e7-205">-SSHServerMode |-sshs</span><span class="sxs-lookup"><span data-stu-id="012e7-205">-SSHServerMode | -sshs</span></span>

<span data-ttu-id="012e7-206">用于在 sshd_config 中将 PowerShell 作为 SSH 子系统运行。</span><span class="sxs-lookup"><span data-stu-id="012e7-206">Used in sshd_config for running PowerShell as an SSH subsystem.</span></span> <span data-ttu-id="012e7-207">对于任何其他用途，不建议使用或支持。</span><span class="sxs-lookup"><span data-stu-id="012e7-207">It is not intended or supported for any other use.</span></span>

### <a name="-version---v"></a><span data-ttu-id="012e7-208">-版本 |-v</span><span class="sxs-lookup"><span data-stu-id="012e7-208">-Version | -v</span></span>

<span data-ttu-id="012e7-209">显示 PowerShell 的版本。</span><span class="sxs-lookup"><span data-stu-id="012e7-209">Displays the version of PowerShell.</span></span> <span data-ttu-id="012e7-210">其他参数将被忽略。</span><span class="sxs-lookup"><span data-stu-id="012e7-210">Additional parameters are ignored.</span></span>

### <a name="-windowstyle---w"></a><span data-ttu-id="012e7-211">-WindowStyle |-w</span><span class="sxs-lookup"><span data-stu-id="012e7-211">-WindowStyle | -w</span></span>

<span data-ttu-id="012e7-212">为会话设置窗口样式。</span><span class="sxs-lookup"><span data-stu-id="012e7-212">Sets the window style for the session.</span></span> <span data-ttu-id="012e7-213">有效值包括 Normal、Minimized、Maximized 和 Hidden。</span><span class="sxs-lookup"><span data-stu-id="012e7-213">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-workingdirectory---wd"></a><span data-ttu-id="012e7-214">-WorkingDirectory |-wd</span><span class="sxs-lookup"><span data-stu-id="012e7-214">-WorkingDirectory | -wd</span></span>

<span data-ttu-id="012e7-215">设置在启动时执行的初始工作目录。</span><span class="sxs-lookup"><span data-stu-id="012e7-215">Sets the initial working directory by executing at startup.</span></span> <span data-ttu-id="012e7-216">支持任何有效的 PowerShell 文件路径。</span><span class="sxs-lookup"><span data-stu-id="012e7-216">Any valid PowerShell file path is supported.</span></span>

<span data-ttu-id="012e7-217">若要在主目录中启动 PowerShell，请使用： `pwsh -WorkingDirectory ~`</span><span class="sxs-lookup"><span data-stu-id="012e7-217">To start PowerShell in your home directory, use: `pwsh -WorkingDirectory ~`</span></span>

### <a name="-help---"></a><span data-ttu-id="012e7-218">-Help、-?、/?</span><span class="sxs-lookup"><span data-stu-id="012e7-218">-Help, -?, /?</span></span>

<span data-ttu-id="012e7-219">显示的帮助 `pwsh` 。</span><span class="sxs-lookup"><span data-stu-id="012e7-219">Displays help for `pwsh`.</span></span> <span data-ttu-id="012e7-220">如果要在 PowerShell 中键入 pwsh 命令，请在命令参数前面添加连字符 (`-`) ，而不是 () 的正斜杠 `/` 。</span><span class="sxs-lookup"><span data-stu-id="012e7-220">If you are typing a pwsh command in PowerShell, prepend the command parameters with a hyphen (`-`), not a forward slash (`/`).</span></span>
