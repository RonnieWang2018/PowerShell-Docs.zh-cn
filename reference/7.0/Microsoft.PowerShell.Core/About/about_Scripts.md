---
description: 介绍如何在 PowerShell 中运行和编写脚本。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scripts
ms.openlocfilehash: f439e6600df49652d25dbd7337fa3db7cff501bb
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/13/2020
ms.locfileid: "93199580"
---
# <a name="about-scripts"></a><span data-ttu-id="f2fed-104">关于脚本</span><span class="sxs-lookup"><span data-stu-id="f2fed-104">About Scripts</span></span>

## <a name="short-description"></a><span data-ttu-id="f2fed-105">简短说明</span><span class="sxs-lookup"><span data-stu-id="f2fed-105">Short description</span></span>
<span data-ttu-id="f2fed-106">介绍如何在 PowerShell 中运行和编写脚本。</span><span class="sxs-lookup"><span data-stu-id="f2fed-106">Describes how to run and write scripts in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="f2fed-107">长说明</span><span class="sxs-lookup"><span data-stu-id="f2fed-107">Long description</span></span>

<span data-ttu-id="f2fed-108">脚本是一种纯文本文件，其中包含一个或多个 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="f2fed-108">A script is a plain text file that contains one or more PowerShell commands.</span></span>
<span data-ttu-id="f2fed-109">PowerShell 脚本具有 `.ps1` 文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="f2fed-109">PowerShell scripts have a `.ps1` file extension.</span></span>

<span data-ttu-id="f2fed-110">运行脚本非常类似于运行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f2fed-110">Running a script is a lot like running a cmdlet.</span></span> <span data-ttu-id="f2fed-111">键入脚本的路径和文件名，并使用参数提交数据并设置选项。</span><span class="sxs-lookup"><span data-stu-id="f2fed-111">You type the path and file name of the script and use parameters to submit data and set options.</span></span> <span data-ttu-id="f2fed-112">您可以在您的计算机上或在其他计算机上的远程会话中运行脚本。</span><span class="sxs-lookup"><span data-stu-id="f2fed-112">You can run scripts on your computer or in a remote session on a different computer.</span></span>

<span data-ttu-id="f2fed-113">编写脚本时，将保存一个命令以供以后使用，并使与他人共享。</span><span class="sxs-lookup"><span data-stu-id="f2fed-113">Writing a script saves a command for later use and makes it easy to share with others.</span></span> <span data-ttu-id="f2fed-114">最重要的是，它只需键入脚本路径和文件名即可运行命令。</span><span class="sxs-lookup"><span data-stu-id="f2fed-114">Most importantly, it lets you run the commands simply by typing the script path and the filename.</span></span> <span data-ttu-id="f2fed-115">脚本可以像文件中的单个命令一样简单，也可以是复杂的程序。</span><span class="sxs-lookup"><span data-stu-id="f2fed-115">Scripts can be as simple as a single command in a file or as extensive as a complex program.</span></span>

<span data-ttu-id="f2fed-116">脚本具有其他功能，如 `#Requires` 特殊注释、参数的使用、对数据部分的支持和用于安全设置的数字签名。</span><span class="sxs-lookup"><span data-stu-id="f2fed-116">Scripts have additional features, such as the `#Requires` special comment, the use of parameters, support for data sections, and digital signing for security.</span></span>
<span data-ttu-id="f2fed-117">你还可以为脚本和脚本中的任何函数编写帮助主题。</span><span class="sxs-lookup"><span data-stu-id="f2fed-117">You can also write Help topics for scripts and for any functions in the script.</span></span>

## <a name="how-to-run-a-script"></a><span data-ttu-id="f2fed-118">如何运行脚本</span><span class="sxs-lookup"><span data-stu-id="f2fed-118">How to run a script</span></span>

<span data-ttu-id="f2fed-119">你需要更改默认 PowerShell 执行策略，然后才能在 Windows 上运行脚本。</span><span class="sxs-lookup"><span data-stu-id="f2fed-119">Before you can run a script on Windows, you need to change the default PowerShell execution policy.</span></span> <span data-ttu-id="f2fed-120">执行策略不适用于在非 Windows 平台上运行的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="f2fed-120">Execution policy does not apply to PowerShell running on non-Windows platforms.</span></span>

<span data-ttu-id="f2fed-121">默认执行策略 `Restricted` 会阻止所有脚本运行，包括在本地计算机上编写的脚本。</span><span class="sxs-lookup"><span data-stu-id="f2fed-121">The default execution policy, `Restricted`, prevents all scripts from running, including scripts that you write on the local computer.</span></span> <span data-ttu-id="f2fed-122">有关详细信息，请参阅 [about_Execution_Policies](about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="f2fed-122">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

<span data-ttu-id="f2fed-123">执行策略保存在注册表中，因此只需在每台计算机上更改一次。</span><span class="sxs-lookup"><span data-stu-id="f2fed-123">The execution policy is saved in the registry, so you need to change it only once on each computer.</span></span>

<span data-ttu-id="f2fed-124">若要更改执行策略，请使用以下过程。</span><span class="sxs-lookup"><span data-stu-id="f2fed-124">To change the execution policy, use the following procedure.</span></span>

<span data-ttu-id="f2fed-125">在命令提示符处，键入：</span><span class="sxs-lookup"><span data-stu-id="f2fed-125">At the command prompt, type:</span></span>

```powershell
Set-ExecutionPolicy AllSigned
```

<span data-ttu-id="f2fed-126">或</span><span class="sxs-lookup"><span data-stu-id="f2fed-126">or</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

<span data-ttu-id="f2fed-127">更改立即生效。</span><span class="sxs-lookup"><span data-stu-id="f2fed-127">The change is effective immediately.</span></span>

<span data-ttu-id="f2fed-128">若要运行脚本，请键入该脚本文件的完整名称和完整路径。</span><span class="sxs-lookup"><span data-stu-id="f2fed-128">To run a script, type the full name and the full path to the script file.</span></span>

<span data-ttu-id="f2fed-129">例如，若要在 C：\Scripts 目录中运行 Get-ServiceLog.ps1 脚本，请键入：</span><span class="sxs-lookup"><span data-stu-id="f2fed-129">For example, to run the Get-ServiceLog.ps1 script in the C:\Scripts directory, type:</span></span>

```powershell
C:\Scripts\Get-ServiceLog.ps1
```

<span data-ttu-id="f2fed-130">若要在当前目录中运行脚本，请键入当前目录的路径，或使用点表示当前目录，然后使用路径反斜杠 (`.\`) 。</span><span class="sxs-lookup"><span data-stu-id="f2fed-130">To run a script in the current directory, type the path to the current directory, or use a dot to represent the current directory, followed by a path backslash (`.\`).</span></span>

<span data-ttu-id="f2fed-131">例如，若要在本地目录中运行 ServicesLog.ps1 脚本，请键入：</span><span class="sxs-lookup"><span data-stu-id="f2fed-131">For example, to run the ServicesLog.ps1 script in the local directory, type:</span></span>

```powershell
.\Get-ServiceLog.ps1
```

<span data-ttu-id="f2fed-132">如果脚本中包含参数，请在脚本文件名后面键入参数和参数值。</span><span class="sxs-lookup"><span data-stu-id="f2fed-132">If the script has parameters, type the parameters and parameter values after the script filename.</span></span>

<span data-ttu-id="f2fed-133">例如，以下命令使用 Get-ServiceLog 脚本的 ServiceName 参数来请求 WinRM 服务活动的日志。</span><span class="sxs-lookup"><span data-stu-id="f2fed-133">For example, the following command uses the ServiceName parameter of the Get-ServiceLog script to request a log of WinRM service activity.</span></span>

```powershell
.\Get-ServiceLog.ps1 -ServiceName WinRM
```

<span data-ttu-id="f2fed-134">作为一项安全功能，当你在文件资源管理器中双击脚本图标时，或在不使用完整路径的情况下键入脚本名称（即使脚本位于当前目录中时），PowerShell 不会运行脚本。</span><span class="sxs-lookup"><span data-stu-id="f2fed-134">As a security feature, PowerShell does not run scripts when you double-click the script icon in File Explorer or when you type the script name without a full path, even when the script is in the current directory.</span></span> <span data-ttu-id="f2fed-135">有关在 PowerShell 中运行命令和脚本的详细信息，请参阅 [about_Command_Precedence](about_Command_Precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="f2fed-135">For more information about running commands and scripts in PowerShell, see [about_Command_Precedence](about_Command_Precedence.md).</span></span>

### <a name="run-with-powershell"></a><span data-ttu-id="f2fed-136">使用 PowerShell 运行</span><span class="sxs-lookup"><span data-stu-id="f2fed-136">Run with PowerShell</span></span>

<span data-ttu-id="f2fed-137">从 PowerShell 3.0 开始，你可以从文件资源管理器运行脚本。</span><span class="sxs-lookup"><span data-stu-id="f2fed-137">Beginning in PowerShell 3.0, you can run scripts from File Explorer.</span></span>

<span data-ttu-id="f2fed-138">若要使用 "使用 PowerShell 运行" 功能：</span><span class="sxs-lookup"><span data-stu-id="f2fed-138">To use the "Run with PowerShell" feature:</span></span>

<span data-ttu-id="f2fed-139">运行文件资源管理器，右键单击脚本文件名，然后选择 "用 PowerShell 运行"。</span><span class="sxs-lookup"><span data-stu-id="f2fed-139">Run File Explorer, right-click the script filename and then select "Run with PowerShell".</span></span>

<span data-ttu-id="f2fed-140">"使用 PowerShell 运行" 功能旨在运行没有必需参数的脚本，不会将输出返回到命令提示符。</span><span class="sxs-lookup"><span data-stu-id="f2fed-140">The "Run with PowerShell" feature is designed to run scripts that do not have required parameters and do not return output to the command prompt.</span></span>

<span data-ttu-id="f2fed-141">有关详细信息，请参阅 [about_Run_With_PowerShell](about_Run_With_PowerShell.md)。</span><span class="sxs-lookup"><span data-stu-id="f2fed-141">For more information, see [about_Run_With_PowerShell](about_Run_With_PowerShell.md).</span></span>

### <a name="running-scripts-on-other-computers"></a><span data-ttu-id="f2fed-142">在其他计算机上运行脚本</span><span class="sxs-lookup"><span data-stu-id="f2fed-142">Running scripts on other computers</span></span>

<span data-ttu-id="f2fed-143">若要在一台或多台远程计算机上运行脚本，请使用该 cmdlet 的 **FilePath** 参数 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="f2fed-143">To run a script on one or more remote computers, use the **FilePath** parameter of the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="f2fed-144">输入脚本的路径和文件名作为 **FilePath** 参数的值。</span><span class="sxs-lookup"><span data-stu-id="f2fed-144">Enter the path and filename of the script as the value of the **FilePath** parameter.</span></span> <span data-ttu-id="f2fed-145">脚本必须位于本地计算机上或者本地计算机能够访问的目录中。</span><span class="sxs-lookup"><span data-stu-id="f2fed-145">The script must reside on the local computer or in a directory that the local computer can access.</span></span>

<span data-ttu-id="f2fed-146">以下命令 `Get-ServiceLog.ps1` 在名为 Server01 和 Server02 的远程计算机上运行该脚本。</span><span class="sxs-lookup"><span data-stu-id="f2fed-146">The following command runs the `Get-ServiceLog.ps1` script on the remote computers named Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01,Server02 -FilePath `
  C:\Scripts\Get-ServiceLog.ps1
```

## <a name="get-help-for-scripts"></a><span data-ttu-id="f2fed-147">获取脚本的帮助</span><span class="sxs-lookup"><span data-stu-id="f2fed-147">Get help for scripts</span></span>

<span data-ttu-id="f2fed-148">Get-Help cmdlet 获取脚本的帮助主题，以及 cmdlet 和其他类型的命令的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="f2fed-148">The Get-Help cmdlet gets the help topics for scripts as well as for cmdlets and other types of commands.</span></span> <span data-ttu-id="f2fed-149">若要获取脚本的帮助主题，请键入， `Get-Help` 然后键入脚本的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="f2fed-149">To get the help topic for a script, type `Get-Help` followed by the path and filename of the script.</span></span> <span data-ttu-id="f2fed-150">如果脚本路径在 `Path` 环境变量中，则可以省略该路径。</span><span class="sxs-lookup"><span data-stu-id="f2fed-150">If the script path is in your `Path` environment variable, you can omit the path.</span></span>

<span data-ttu-id="f2fed-151">例如，若要获取 ServicesLog.ps1 脚本的帮助，请键入：</span><span class="sxs-lookup"><span data-stu-id="f2fed-151">For example, to get help for the ServicesLog.ps1 script, type:</span></span>

```powershell
get-help C:\admin\scripts\ServicesLog.ps1
```

## <a name="how-to-write-a-script"></a><span data-ttu-id="f2fed-152">如何编写脚本</span><span class="sxs-lookup"><span data-stu-id="f2fed-152">How to write a script</span></span>

<span data-ttu-id="f2fed-153">脚本可以包含任何有效的 PowerShell 命令，其中包括单个命令、使用管道、函数和控制结构的命令（如 If 语句和 For 循环）。</span><span class="sxs-lookup"><span data-stu-id="f2fed-153">A script can contain any valid PowerShell commands, including single commands, commands that use the pipeline, functions, and control structures such as If statements and For loops.</span></span>

<span data-ttu-id="f2fed-154">若要编写脚本，请在文本编辑器中打开一个新文件，键入命令，然后将其保存到文件扩展名为的有效文件名的文件中 `.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="f2fed-154">To write a script, open a new file in a text editor, type the commands, and save them in a file with a valid filename with the `.ps1` file extension.</span></span>

<span data-ttu-id="f2fed-155">下面的示例是一个简单的脚本，用于获取当前系统上运行的服务并将其保存到日志文件中。</span><span class="sxs-lookup"><span data-stu-id="f2fed-155">The following example is a simple script that gets the services that are running on the current system and saves them to a log file.</span></span> <span data-ttu-id="f2fed-156">将从当前日期创建日志文件名。</span><span class="sxs-lookup"><span data-stu-id="f2fed-156">The log filename is created from the current date.</span></span>

```powershell
$date = (get-date).dayofyear
get-service | out-file "$date.log"
```

<span data-ttu-id="f2fed-157">若要创建此脚本，请打开文本编辑器或脚本编辑器，键入这些命令，然后将其保存到名为的文件中 `ServiceLog.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="f2fed-157">To create this script, open a text editor or a script editor, type these commands, and then save them in a file named `ServiceLog.ps1`.</span></span>

### <a name="parameters-in-scripts"></a><span data-ttu-id="f2fed-158">脚本中的参数</span><span class="sxs-lookup"><span data-stu-id="f2fed-158">Parameters in scripts</span></span>

<span data-ttu-id="f2fed-159">若要在脚本中定义参数，请使用 Param 语句。</span><span class="sxs-lookup"><span data-stu-id="f2fed-159">To define parameters in a script, use a Param statement.</span></span> <span data-ttu-id="f2fed-160">`Param`语句必须是脚本中的第一个语句，注释和任何 `#Require` 语句除外。</span><span class="sxs-lookup"><span data-stu-id="f2fed-160">The `Param` statement must be the first statement in a script, except for comments and any `#Require` statements.</span></span>

<span data-ttu-id="f2fed-161">脚本参数的工作方式类似于函数参数。</span><span class="sxs-lookup"><span data-stu-id="f2fed-161">Script parameters work like function parameters.</span></span> <span data-ttu-id="f2fed-162">参数值可用于脚本中的所有命令。</span><span class="sxs-lookup"><span data-stu-id="f2fed-162">The parameter values are available to all of the commands in the script.</span></span> <span data-ttu-id="f2fed-163">函数参数的所有功能（包括 Parameter 属性及其命名参数）在脚本中也是有效的。</span><span class="sxs-lookup"><span data-stu-id="f2fed-163">All of the features of function parameters, including the Parameter attribute and its named arguments, are also valid in scripts.</span></span>

<span data-ttu-id="f2fed-164">运行脚本时，脚本用户在脚本名称后键入参数。</span><span class="sxs-lookup"><span data-stu-id="f2fed-164">When running the script, script users type the parameters after the script name.</span></span>

<span data-ttu-id="f2fed-165">下面的示例演示一个 `Test-Remote.ps1` 包含 **ComputerName** 参数的脚本。</span><span class="sxs-lookup"><span data-stu-id="f2fed-165">The following example shows a `Test-Remote.ps1` script that has a **ComputerName** parameter.</span></span> <span data-ttu-id="f2fed-166">这两个脚本函数都可以访问 **ComputerName** 参数值。</span><span class="sxs-lookup"><span data-stu-id="f2fed-166">Both of the script functions can access the **ComputerName** parameter value.</span></span>

```powershell
param ($ComputerName = $(throw "ComputerName parameter is required."))

function CanPing {
   $error.clear()
   $tmp = test-connection $computername -erroraction SilentlyContinue

   if (!$?)
       {write-host "Ping failed: $ComputerName."; return $false}
   else
       {write-host "Ping succeeded: $ComputerName"; return $true}
}

function CanRemote {
    $s = new-pssession $computername -erroraction SilentlyContinue

    if ($s -is [System.Management.Automation.Runspaces.PSSession])
        {write-host "Remote test succeeded: $ComputerName."}
    else
        {write-host "Remote test failed: $ComputerName."}
}

if (CanPing $computername) {CanRemote $computername}
```

<span data-ttu-id="f2fed-167">若要运行此脚本，请在脚本名称后键入参数名称。</span><span class="sxs-lookup"><span data-stu-id="f2fed-167">To run this script, type the parameter name after the script name.</span></span> <span data-ttu-id="f2fed-168">例如：</span><span class="sxs-lookup"><span data-stu-id="f2fed-168">For example:</span></span>

```powershell
C:\PS> .\test-remote.ps1 -computername Server01

Ping succeeded: Server01
Remote test failed: Server01
```

<span data-ttu-id="f2fed-169">有关 Param 语句和函数参数的详细信息，请参阅 [about_Functions](about_Functions.md) 和 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="f2fed-169">For more information about the Param statement and the function parameters, see [about_Functions](about_Functions.md) and [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

### <a name="writing-help-for-scripts"></a><span data-ttu-id="f2fed-170">编写脚本的帮助</span><span class="sxs-lookup"><span data-stu-id="f2fed-170">Writing help for scripts</span></span>

<span data-ttu-id="f2fed-171">您可以使用以下两种方法之一来编写脚本的帮助主题：</span><span class="sxs-lookup"><span data-stu-id="f2fed-171">You can write a help topic for a script by using either of the two following methods:</span></span>

- <span data-ttu-id="f2fed-172">脚本 Comment-Based 帮助</span><span class="sxs-lookup"><span data-stu-id="f2fed-172">Comment-Based Help for Scripts</span></span>

  <span data-ttu-id="f2fed-173">在注释中使用特殊关键字创建帮助主题。</span><span class="sxs-lookup"><span data-stu-id="f2fed-173">Create a Help topic by using special keywords in the comments.</span></span> <span data-ttu-id="f2fed-174">若要为脚本创建基于注释的帮助，必须在脚本文件的开头或结尾处放置注释。</span><span class="sxs-lookup"><span data-stu-id="f2fed-174">To create comment-based Help for a script, the comments must be placed at the beginning or end of the script file.</span></span> <span data-ttu-id="f2fed-175">有关基于注释的帮助的详细信息，请参阅 [about_Comment_Based_Help](about_Comment_Based_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="f2fed-175">For more information about comment-based Help, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span>

- <span data-ttu-id="f2fed-176">脚本 XML-Based 帮助</span><span class="sxs-lookup"><span data-stu-id="f2fed-176">XML-Based Help  for Scripts</span></span>

  <span data-ttu-id="f2fed-177">创建基于 XML 的帮助主题，如通常为 cmdlet 创建的类型。</span><span class="sxs-lookup"><span data-stu-id="f2fed-177">Create an XML-based Help topic, such as the type that is typically created for cmdlets.</span></span> <span data-ttu-id="f2fed-178">如果要将帮助主题转换为多种语言，则必须提供基于 XML 的帮助。</span><span class="sxs-lookup"><span data-stu-id="f2fed-178">XML-based Help is required if you are translating Help topics into multiple languages.</span></span>

<span data-ttu-id="f2fed-179">若要将脚本与基于 XML 的帮助主题相关联，请使用。.Externalhelp Help comment 关键字。</span><span class="sxs-lookup"><span data-stu-id="f2fed-179">To associate the script with the XML-based Help topic, use the .ExternalHelp Help comment keyword.</span></span> <span data-ttu-id="f2fed-180">有关 .Externalhelp 关键字的详细信息，请参阅 [about_Comment_Based_Help](about_Comment_Based_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="f2fed-180">For more information about the ExternalHelp keyword, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span> <span data-ttu-id="f2fed-181">有关基于 XML 的帮助的详细信息，请参阅 [如何编写 Cmdlet 帮助](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)。</span><span class="sxs-lookup"><span data-stu-id="f2fed-181">For more information about XML-based help, see [How to Write Cmdlet Help](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

### <a name="returning-an-exit-value"></a><span data-ttu-id="f2fed-182">返回退出值</span><span class="sxs-lookup"><span data-stu-id="f2fed-182">Returning an exit value</span></span>

<span data-ttu-id="f2fed-183">默认情况下，脚本结束时，脚本不返回退出状态。</span><span class="sxs-lookup"><span data-stu-id="f2fed-183">By default, scripts do not return an exit status when the script ends.</span></span> <span data-ttu-id="f2fed-184">必须使用 `exit` 语句从脚本返回退出代码。</span><span class="sxs-lookup"><span data-stu-id="f2fed-184">You must use the `exit` statement to return an exit code from a script.</span></span> <span data-ttu-id="f2fed-185">默认情况下，该 `exit` 语句将返回 `0` 。</span><span class="sxs-lookup"><span data-stu-id="f2fed-185">By default, the `exit` statement returns `0`.</span></span> <span data-ttu-id="f2fed-186">您可以提供一个数值来返回不同的退出状态。</span><span class="sxs-lookup"><span data-stu-id="f2fed-186">You can provide a numeric value to return a different exit status.</span></span> <span data-ttu-id="f2fed-187">非零退出代码通常会发出错误信号。</span><span class="sxs-lookup"><span data-stu-id="f2fed-187">A nonzero exit code typically signals a failure.</span></span>

<span data-ttu-id="f2fed-188">在 Windows 上，允许使用介于和之间的任何数字 `[int]::MinValue` `[int]::MaxValue` 。</span><span class="sxs-lookup"><span data-stu-id="f2fed-188">On Windows, any number between `[int]::MinValue` and `[int]::MaxValue` is allowed.</span></span>

<span data-ttu-id="f2fed-189">在 Unix 上，只 `[byte]::MinValue` 允许 (0) 和 `[byte]::MaxValue` (255) 之间的正数。</span><span class="sxs-lookup"><span data-stu-id="f2fed-189">On Unix, only positive numbers between `[byte]::MinValue` (0) and `[byte]::MaxValue` (255) are allowed.</span></span> <span data-ttu-id="f2fed-190">范围内的负数将 `-1` `-255` 通过添加来自动转换为正数</span><span class="sxs-lookup"><span data-stu-id="f2fed-190">A negative number in the range of `-1` through `-255` is automatically translated into a positive number by adding</span></span>
256. <span data-ttu-id="f2fed-191">例如， `-2` 将转换为 `254` 。</span><span class="sxs-lookup"><span data-stu-id="f2fed-191">For example, `-2` is transformed to `254`.</span></span>

<span data-ttu-id="f2fed-192">在 PowerShell 中， `exit` 语句设置变量的值 `$LASTEXITCODE` 。</span><span class="sxs-lookup"><span data-stu-id="f2fed-192">In PowerShell, the `exit` statement sets the value of the `$LASTEXITCODE` variable.</span></span> <span data-ttu-id="f2fed-193">在 Windows 命令行界面 ( # A0) 中，exit 语句设置环境变量的值 `%ERRORLEVEL%` 。</span><span class="sxs-lookup"><span data-stu-id="f2fed-193">In the Windows Command Shell (cmd.exe), the exit statement sets the value of the `%ERRORLEVEL%` environment variable.</span></span>

<span data-ttu-id="f2fed-194">任何非数字或超出平台特定范围的参数均转换为的值 `0` 。</span><span class="sxs-lookup"><span data-stu-id="f2fed-194">Any argument that is non-numeric or outside the platform-specific range is translated to the value of `0`.</span></span>

## <a name="script-scope-and-dot-sourcing"></a><span data-ttu-id="f2fed-195">脚本范围和网点源</span><span class="sxs-lookup"><span data-stu-id="f2fed-195">Script scope and dot sourcing</span></span>

<span data-ttu-id="f2fed-196">每个脚本都在其自己的作用域中运行。</span><span class="sxs-lookup"><span data-stu-id="f2fed-196">Each script runs in its own scope.</span></span> <span data-ttu-id="f2fed-197">脚本中创建的函数、变量、别名和驱动器仅存在于脚本作用域中。</span><span class="sxs-lookup"><span data-stu-id="f2fed-197">The functions, variables, aliases, and drives that are created in the script exist only in the script scope.</span></span> <span data-ttu-id="f2fed-198">你无法在运行脚本的范围内访问这些项或其值。</span><span class="sxs-lookup"><span data-stu-id="f2fed-198">You cannot access these items or their values in the scope in which the script runs.</span></span>

<span data-ttu-id="f2fed-199">若要在不同的作用域中运行脚本，可以指定一个范围（如 Global 或 Local），也可以在脚本中使用点值。</span><span class="sxs-lookup"><span data-stu-id="f2fed-199">To run a script in a different scope, you can specify a scope, such as Global or Local, or you can dot source the script.</span></span>

<span data-ttu-id="f2fed-200">使用 "中点采购" 功能，您可以在当前范围内而不是在脚本范围内运行脚本。</span><span class="sxs-lookup"><span data-stu-id="f2fed-200">The dot sourcing feature lets you run a script in the current scope instead of in the script scope.</span></span> <span data-ttu-id="f2fed-201">当你运行带点的脚本时，脚本中的命令将按你在命令提示符下键入的那样运行。</span><span class="sxs-lookup"><span data-stu-id="f2fed-201">When you run a script that is dot sourced, the commands in the script run as though you had typed them at the command prompt.</span></span> <span data-ttu-id="f2fed-202">脚本创建的函数、变量、别名和驱动器在工作范围内创建。</span><span class="sxs-lookup"><span data-stu-id="f2fed-202">The functions, variables, aliases, and drives that the script creates are created in the scope in which you are working.</span></span> <span data-ttu-id="f2fed-203">脚本运行后，可以使用创建的项目并在会话中访问其值。</span><span class="sxs-lookup"><span data-stu-id="f2fed-203">After the script runs, you can use the created items and access their values in your session.</span></span>

<span data-ttu-id="f2fed-204">若要将脚本保存到点源，请在脚本路径之前键入一个点 ( ) 和一个空格。</span><span class="sxs-lookup"><span data-stu-id="f2fed-204">To dot source a script, type a dot (.) and a space before the script path.</span></span>

<span data-ttu-id="f2fed-205">例如：</span><span class="sxs-lookup"><span data-stu-id="f2fed-205">For example:</span></span>

```powershell
. C:\scripts\UtilityFunctions.ps1
```

<span data-ttu-id="f2fed-206">或</span><span class="sxs-lookup"><span data-stu-id="f2fed-206">or</span></span>

```powershell
. .\UtilityFunctions.ps1
```

<span data-ttu-id="f2fed-207">`UtilityFunctions.ps1`脚本运行后，脚本创建的函数和变量将添加到当前作用域中。</span><span class="sxs-lookup"><span data-stu-id="f2fed-207">After the `UtilityFunctions.ps1` script runs, the functions and variables that the script creates are added to the current scope.</span></span>

<span data-ttu-id="f2fed-208">例如，该 `UtilityFunctions.ps1` 脚本会创建 `New-Profile` 函数和 `$ProfileName` 变量。</span><span class="sxs-lookup"><span data-stu-id="f2fed-208">For example, the `UtilityFunctions.ps1` script creates the `New-Profile` function and the `$ProfileName` variable.</span></span>

```powershell
#In UtilityFunctions.ps1

function New-Profile
{
  Write-Host "Running New-Profile function"
  $profileName = split-path $profile -leaf

  if (test-path $profile)
    {write-error "Profile $profileName already exists on this computer."}
  else
    {new-item -type file -path $profile -force }
}
```

<span data-ttu-id="f2fed-209">如果在脚本的 `UtilityFunctions.ps1` 脚本作用域中运行该脚本，则 `New-Profile` `$ProfileName` 只有当脚本正在运行时，函数和变量才存在。</span><span class="sxs-lookup"><span data-stu-id="f2fed-209">If you run the `UtilityFunctions.ps1` script in its own script scope, the `New-Profile` function and the `$ProfileName` variable exist only while the script is running.</span></span> <span data-ttu-id="f2fed-210">脚本退出后，将删除函数和变量，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="f2fed-210">When the script exits, the function and variable are removed, as shown in the following example.</span></span>

```powershell
C:\PS> .\UtilityFunctions.ps1

C:\PS> New-Profile
The term 'new-profile' is not recognized as a cmdlet, function, operable
program, or script file. Verify the term and try again.
At line:1 char:12
+ new-profile <<<<
   + CategoryInfo          : ObjectNotFound: (new-profile:String) [],
   + FullyQualifiedErrorId : CommandNotFoundException

C:\PS> $profileName
C:\PS>
```

<span data-ttu-id="f2fed-211">当你用点来编写脚本并运行它时，脚本将在你的作用域内的会话中创建 `New-Profile` 函数和 `$ProfileName` 变量。</span><span class="sxs-lookup"><span data-stu-id="f2fed-211">When you dot source the script and run it, the script creates the `New-Profile` function and the `$ProfileName` variable in your session in your scope.</span></span> <span data-ttu-id="f2fed-212">脚本运行后，你可以 `New-Profile` 在会话中使用函数，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="f2fed-212">After the script runs, you can use the `New-Profile` function in your session, as shown in the following example.</span></span>

```powershell
C:\PS> . .\UtilityFunctions.ps1

C:\PS> New-Profile

    Directory: C:\Users\juneb\Documents\WindowsPowerShell

    Mode    LastWriteTime     Length Name
    ----    -------------     ------ ----
    -a---   1/14/2009 3:08 PM      0 Microsoft.PowerShellISE_profile.ps1

C:\PS> $profileName
Microsoft.PowerShellISE_profile.ps1
```

<span data-ttu-id="f2fed-213">有关作用域的详细信息，请参阅 about_Scopes。</span><span class="sxs-lookup"><span data-stu-id="f2fed-213">For more information about scope, see about_Scopes.</span></span>

## <a name="scripts-in-modules"></a><span data-ttu-id="f2fed-214">模块中的脚本</span><span class="sxs-lookup"><span data-stu-id="f2fed-214">Scripts in modules</span></span>

<span data-ttu-id="f2fed-215">模块是可作为一个单元分发的一组相关 PowerShell 资源。</span><span class="sxs-lookup"><span data-stu-id="f2fed-215">A module is a set of related PowerShell resources that can be distributed as a unit.</span></span> <span data-ttu-id="f2fed-216">您可以使用模块来组织您的脚本、函数和其他资源。</span><span class="sxs-lookup"><span data-stu-id="f2fed-216">You can use modules to organize your scripts, functions, and other resources.</span></span> <span data-ttu-id="f2fed-217">你还可以使用模块将代码分发给其他人，并从受信任的源获取代码。</span><span class="sxs-lookup"><span data-stu-id="f2fed-217">You can also use modules to distribute your code to others, and to get code from trusted sources.</span></span>

<span data-ttu-id="f2fed-218">您可以将脚本包含在您的模块中，也可以创建脚本模块，该模块是完全或主要包含脚本和支持资源的模块。</span><span class="sxs-lookup"><span data-stu-id="f2fed-218">You can include scripts in your modules, or you can create a script module, which is a module that consists entirely or primarily of a script and supporting resources.</span></span> <span data-ttu-id="f2fed-219">脚本模块只是文件扩展名为 hbase-runner.psm1 的脚本。</span><span class="sxs-lookup"><span data-stu-id="f2fed-219">A script module is just a script with a .psm1 file extension.</span></span>

<span data-ttu-id="f2fed-220">有关模块的详细信息，请参阅 [about_Modules](about_Modules.md)。</span><span class="sxs-lookup"><span data-stu-id="f2fed-220">For more information about modules, see [about_Modules](about_Modules.md).</span></span>

## <a name="other-script-features"></a><span data-ttu-id="f2fed-221">其他脚本功能</span><span class="sxs-lookup"><span data-stu-id="f2fed-221">Other script features</span></span>

<span data-ttu-id="f2fed-222">PowerShell 提供了许多可在脚本中使用的有用功能。</span><span class="sxs-lookup"><span data-stu-id="f2fed-222">PowerShell has many useful features that you can use in scripts.</span></span>

- <span data-ttu-id="f2fed-223">`#Requires` -可以使用 `#Requires` 语句阻止脚本在没有指定模块或管理单元和指定版本的 PowerShell 的情况下运行。</span><span class="sxs-lookup"><span data-stu-id="f2fed-223">`#Requires` - You can use a `#Requires` statement to prevent a script from running without specified modules or snap-ins and a specified version of PowerShell.</span></span> <span data-ttu-id="f2fed-224">有关详细信息，请参阅 about_Requires。</span><span class="sxs-lookup"><span data-stu-id="f2fed-224">For more information, see about_Requires.</span></span>

- <span data-ttu-id="f2fed-225">`$PSCommandPath` -包含正在运行的脚本的完整路径和名称。</span><span class="sxs-lookup"><span data-stu-id="f2fed-225">`$PSCommandPath` - Contains the full path and name of the script that is being run.</span></span> <span data-ttu-id="f2fed-226">此参数在所有脚本中都有效。</span><span class="sxs-lookup"><span data-stu-id="f2fed-226">This parameter is valid in all scripts.</span></span> <span data-ttu-id="f2fed-227">此自动变量在 PowerShell 3.0 中引入。</span><span class="sxs-lookup"><span data-stu-id="f2fed-227">This automatic variable is introduced in PowerShell 3.0.</span></span>

- <span data-ttu-id="f2fed-228">`$PSScriptRoot` -包含正在从中运行脚本的目录。</span><span class="sxs-lookup"><span data-stu-id="f2fed-228">`$PSScriptRoot` - Contains the directory from which a script is being run.</span></span> <span data-ttu-id="f2fed-229">在 PowerShell 2.0 中，此变量仅在) 的脚本模块中有效 (`.psm1` 。</span><span class="sxs-lookup"><span data-stu-id="f2fed-229">In PowerShell 2.0, this variable is valid only in script modules (`.psm1`).</span></span>
  <span data-ttu-id="f2fed-230">从 PowerShell 3.0 开始，它在所有脚本中都有效。</span><span class="sxs-lookup"><span data-stu-id="f2fed-230">Beginning in PowerShell 3.0, it is valid in all scripts.</span></span>

- <span data-ttu-id="f2fed-231">`$MyInvocation` - `$MyInvocation` 自动变量包含当前脚本的相关信息，包括有关如何启动或 "调用" 的信息。</span><span class="sxs-lookup"><span data-stu-id="f2fed-231">`$MyInvocation` - The `$MyInvocation` automatic variable contains information about the current script, including information about how it was started or "invoked."</span></span> <span data-ttu-id="f2fed-232">您可以使用此变量及其属性来获取有关正在运行的脚本的信息。</span><span class="sxs-lookup"><span data-stu-id="f2fed-232">You can use this variable and its properties to get information about the script while it is running.</span></span> <span data-ttu-id="f2fed-233">例如， `$MyInvocation` 。MyCommand 变量包含脚本的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="f2fed-233">For example, the `$MyInvocation`.MyCommand.Path variable contains the path and filename of the script.</span></span> <span data-ttu-id="f2fed-234">`$MyInvocation`.行包含启动脚本的命令，包括所有参数和值。</span><span class="sxs-lookup"><span data-stu-id="f2fed-234">`$MyInvocation`.Line contains the command that started the script, including all parameters and values.</span></span>

  <span data-ttu-id="f2fed-235">从 PowerShell 3.0 开始， `$MyInvocation` 具有两个新属性，这些属性提供有关调用或调用当前脚本的脚本的信息。</span><span class="sxs-lookup"><span data-stu-id="f2fed-235">Beginning in PowerShell 3.0, `$MyInvocation` has two new properties that provide information about the script that called or invoked the current script.</span></span> <span data-ttu-id="f2fed-236">仅当调用程序或调用方为脚本时，才填充这些属性的值。</span><span class="sxs-lookup"><span data-stu-id="f2fed-236">The values of these properties are populated only when the invoker or caller is a script.</span></span>

  - <span data-ttu-id="f2fed-237">**PSCommandPath** 包含调用或调用当前脚本的脚本的完整路径和名称。</span><span class="sxs-lookup"><span data-stu-id="f2fed-237">**PSCommandPath** contains the full path and name of the script that called or invoked the current script.</span></span>

  - <span data-ttu-id="f2fed-238">**PSScriptRoot** 包含调用或调用当前脚本的脚本的目录。</span><span class="sxs-lookup"><span data-stu-id="f2fed-238">**PSScriptRoot** contains the directory of the script that called or invoked the current script.</span></span>

  <span data-ttu-id="f2fed-239">与 `$PSCommandPath` `$PSScriptRoot` 包含当前脚本相关信息的和自动变量不同，该变量的 **PSCommandPath** 和 **PSScriptRoot** 属性 `$MyInvocation` 包含有关调用当前脚本的脚本的信息。</span><span class="sxs-lookup"><span data-stu-id="f2fed-239">Unlike the `$PSCommandPath` and `$PSScriptRoot` automatic variables, which contain information about the current script, the **PSCommandPath** and **PSScriptRoot** properties of the `$MyInvocation` variable contain information about the script that called the current script.</span></span>

- <span data-ttu-id="f2fed-240">数据部分-可以使用 `Data` 关键字在脚本中将数据与逻辑分离。</span><span class="sxs-lookup"><span data-stu-id="f2fed-240">Data sections - You can use the `Data` keyword to separate data from logic in scripts.</span></span> <span data-ttu-id="f2fed-241">数据节还可以更轻松地进行本地化。</span><span class="sxs-lookup"><span data-stu-id="f2fed-241">Data sections can also make localization easier.</span></span> <span data-ttu-id="f2fed-242">有关详细信息，请参阅 [about_Data_Sections](about_Data_Sections.md) 和 [about_Script_Internationalization](about_Script_Internationalization.md)。</span><span class="sxs-lookup"><span data-stu-id="f2fed-242">For more information, see [about_Data_Sections](about_Data_Sections.md) and [about_Script_Internationalization](about_Script_Internationalization.md).</span></span>

- <span data-ttu-id="f2fed-243">脚本签名-可以向脚本添加数字签名。</span><span class="sxs-lookup"><span data-stu-id="f2fed-243">Script Signing - You can add a digital signature to a script.</span></span> <span data-ttu-id="f2fed-244">根据执行策略，可以使用数字签名来限制可能包含不安全命令的脚本的运行。</span><span class="sxs-lookup"><span data-stu-id="f2fed-244">Depending on the execution policy, you can use digital signatures to restrict the running of scripts that could include unsafe commands.</span></span> <span data-ttu-id="f2fed-245">有关详细信息，请参阅 [about_Execution_Policies](about_Execution_Policies.md) 和 [about_Signing](about_Signing.md)。</span><span class="sxs-lookup"><span data-stu-id="f2fed-245">For more information, see [about_Execution_Policies](about_Execution_Policies.md) and [about_Signing](about_Signing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f2fed-246">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f2fed-246">See also</span></span>

[<span data-ttu-id="f2fed-247">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="f2fed-247">about_Command_Precedence</span></span>](about_Command_Precedence.md)

[<span data-ttu-id="f2fed-248">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="f2fed-248">about_Comment_Based_Help</span></span>](about_Comment_Based_Help.md)

[<span data-ttu-id="f2fed-249">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="f2fed-249">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="f2fed-250">about_Functions</span><span class="sxs-lookup"><span data-stu-id="f2fed-250">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="f2fed-251">about_Modules</span><span class="sxs-lookup"><span data-stu-id="f2fed-251">about_Modules</span></span>](about_Modules.md)

[<span data-ttu-id="f2fed-252">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="f2fed-252">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="f2fed-253">about_Requires</span><span class="sxs-lookup"><span data-stu-id="f2fed-253">about_Requires</span></span>](about_Requires.md)

[<span data-ttu-id="f2fed-254">about_Run_With_PowerShell</span><span class="sxs-lookup"><span data-stu-id="f2fed-254">about_Run_With_PowerShell</span></span>](about_Run_With_PowerShell.md)

[<span data-ttu-id="f2fed-255">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="f2fed-255">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="f2fed-256">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="f2fed-256">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="f2fed-257">about_Signing</span><span class="sxs-lookup"><span data-stu-id="f2fed-257">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="f2fed-258">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="f2fed-258">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
