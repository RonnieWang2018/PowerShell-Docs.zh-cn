---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-PSSession
ms.openlocfilehash: 67501a78ba577f63c97e595f4bacd28160fea416
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93197938"
---
# <span data-ttu-id="9c3c3-103">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="9c3c3-103">Export-PSSession</span></span>

## <span data-ttu-id="9c3c3-104">摘要</span><span class="sxs-lookup"><span data-stu-id="9c3c3-104">SYNOPSIS</span></span>

<span data-ttu-id="9c3c3-105">导出另一个会话中的命令，并将其保存在 PowerShell 模块中。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-105">Exports commands from another session and saves them in a PowerShell module.</span></span>

## <span data-ttu-id="9c3c3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9c3c3-106">SYNTAX</span></span>

```
Export-PSSession [-Session] <PSSession> [-OutputModule] <string> [[-CommandName] <string[]>]
 [[-FormatTypeName] <string[]>] [-Force] [-Encoding <string>] [-AllowClobber]
 [-ArgumentList <Object[]>] [-CommandType <CommandTypes>] [-Module <string[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-Certificate <X509Certificate2>]
 [<CommonParameters>]
```

## <span data-ttu-id="9c3c3-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9c3c3-107">DESCRIPTION</span></span>

<span data-ttu-id="9c3c3-108">此 `Export-PSSession` cmdlet 从本地或远程计算机上 (PSSession) 的其他 PowerShell 会话中获取 cmdlet、函数、别名和其他命令类型，并将它们保存在 PowerShell 模块中。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-108">The `Export-PSSession` cmdlet gets cmdlets, functions, aliases, and other command types from another PowerShell session (PSSession) on a local or remote computer and saves them in a PowerShell module.</span></span> <span data-ttu-id="9c3c3-109">若要将该模块中的命令添加到当前会话中，请使用 `Import-Module` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-109">To add the commands from the module to the current session, use the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="9c3c3-110">与 `Import-PSSession` （不同于）将命令从另一个 PSSession 导入到当前会话中， `Export-PSSession` 将命令保存在模块中。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-110">Unlike `Import-PSSession`, which imports commands from another PSSession into the current session, `Export-PSSession` saves the commands in a module.</span></span> <span data-ttu-id="9c3c3-111">这些命令不会被导入到当前会话中。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-111">The commands are not imported into the current session.</span></span>

<span data-ttu-id="9c3c3-112">若要导出命令，请使用 `New-PSSession` cmdlet 创建具有要导出的命令的 PSSession。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-112">To export commands, use the `New-PSSession` cmdlet to create a PSSession that has the commands that you want to export.</span></span> <span data-ttu-id="9c3c3-113">然后使用 `Export-PSSession` cmdlet 导出命令。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-113">Then use the `Export-PSSession` cmdlet to export the commands.</span></span>

<span data-ttu-id="9c3c3-114">若要防止命令名称冲突，则的默认值 `Export-PSSession` 是导出所有命令，当前会话中存在的命令除外。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-114">To prevent command name conflicts, the default for `Export-PSSession` is to export all commands, except for commands that exist in the current session.</span></span> <span data-ttu-id="9c3c3-115">可以使用 **CommandName** 参数来指定要导出的命令。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-115">You can use the **CommandName** parameter to specify the commands to export.</span></span>

<span data-ttu-id="9c3c3-116">`Export-PSSession`Cmdlet 使用 PowerShell 的隐式远程处理功能。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-116">The `Export-PSSession` cmdlet uses the implicit remoting feature of PowerShell.</span></span> <span data-ttu-id="9c3c3-117">将命令导入到当前会话中时，它们将在原始会话或原始计算机上的类似会话中隐式运行。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-117">When you import commands into the current session, they run implicitly in the original session or in a similar session on the originating computer.</span></span>

## <span data-ttu-id="9c3c3-118">示例</span><span class="sxs-lookup"><span data-stu-id="9c3c3-118">EXAMPLES</span></span>

### <span data-ttu-id="9c3c3-119">示例1：从 PSSession 导出命令</span><span class="sxs-lookup"><span data-stu-id="9c3c3-119">Example 1: Export commands from a PSSession</span></span>

<span data-ttu-id="9c3c3-120">此示例将从本地计算机创建新的 PSSession 到 Server01 计算机。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-120">This example creates a new PSSession from the local computer to the Server01 computer.</span></span> <span data-ttu-id="9c3c3-121">除当前会话中存在的命令外，所有命令都导出到本地计算机上名为 Server01 的模块中。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-121">All of the commands, except those that exist in the current session, are exported to the module named Server01 on the local computer.</span></span> <span data-ttu-id="9c3c3-122">导出包括这些命令的格式设置数据。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-122">The export includes the formatting data for the commands.</span></span>

```powershell
$S = New-PSSession -ComputerName Server01
Export-PSSession -Session $S -OutputModule Server01
```

<span data-ttu-id="9c3c3-123">`New-PSSession`命令在 Server01 计算机上创建 PSSession。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-123">The `New-PSSession` command creates a PSSession on the Server01 computer.</span></span> <span data-ttu-id="9c3c3-124">PSSession 存储在 `$S` 变量中。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-124">The PSSession is stored in the `$S` variable.</span></span> <span data-ttu-id="9c3c3-125">此 `Export-PSSession` 命令会将 `$S` 变量的命令和格式数据导出到 Server01 模块中。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-125">The `Export-PSSession` command exports the `$S` variable's commands and formatting data into the Server01 module.</span></span>

### <span data-ttu-id="9c3c3-126">示例2：导出 Get 和 Set 命令</span><span class="sxs-lookup"><span data-stu-id="9c3c3-126">Example 2: Export the Get and Set commands</span></span>

<span data-ttu-id="9c3c3-127">此示例从服务器导出所有 `Get` 和 `Set` 命令。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-127">This example exports all of the `Get` and `Set` commands from a server.</span></span>

```powershell
$S = New-PSSession -ConnectionUri https://exchange.microsoft.com/mailbox -Credential exchangeadmin01@hotmail.com -Authentication Negotiate
Export-PSSession -Session $S -Module exch* -CommandName Get-*, Set-* -FormatTypeName * -OutputModule $PSHOME\Modules\Exchange -Encoding ASCII
```

<span data-ttu-id="9c3c3-128">这些命令将 `Get` 和 `Set` 命令从远程计算机上的 Microsoft exchange Server 管理单元导出到本地计算机上的目录中的 exchange 模块 `$PSHOME\Modules` 。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-128">These commands export the `Get` and `Set` commands from a Microsoft Exchange Server snap-in on a remote computer to an Exchange module in the `$PSHOME\Modules` directory on the local computer.</span></span>
<span data-ttu-id="9c3c3-129">将模块放在 `$PSHOME\Modules` 目录中后，计算机的所有用户都可以访问它。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-129">Placing the module in the `$PSHOME\Modules` directory makes it accessible to all users of the computer.</span></span>

### <span data-ttu-id="9c3c3-130">示例3：从远程计算机导出命令</span><span class="sxs-lookup"><span data-stu-id="9c3c3-130">Example 3: Export commands from a remote computer</span></span>

<span data-ttu-id="9c3c3-131">此示例从远程计算机上的 PSSession 导出 cmdlet，并将它们保存在本地计算机上的模块中。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-131">This example exports cmdlets from a PSSession on a remote computer and saves them in a module on the local computer.</span></span> <span data-ttu-id="9c3c3-132">将模块中的 cmdlet 添加到当前会话，以便可以使用它们。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-132">The cmdlets from the module are added to the current session so that they can be used.</span></span>

```powershell
$S = New-PSSession -ComputerName Server01 -Credential Server01\User01
Export-PSSession -Session $S -OutputModule TestCmdlets -Type Cmdlet -CommandName *test* -FormatTypeName *
Remove-PSSession $S
Import-Module TestCmdlets
Get-Help Test*
Test-Files
```

<span data-ttu-id="9c3c3-133">此 `New-PSSession` 命令在 Server01 计算机上创建 PSSession，并将其保存在 `$S` 变量中。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-133">The `New-PSSession` command creates a PSSession on the Server01 computer and saves it in the `$S` variable.</span></span> <span data-ttu-id="9c3c3-134">`Export-PSSession`命令将名称以 Test 开头的 cmdlet 从中的 PSSession 导出 `$S` 到本地计算机上的 TestCmdlets 模块。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-134">The `Export-PSSession` command exports the cmdlets whose names begin with Test from the PSSession in `$S` to the TestCmdlets module on the local computer.</span></span>

<span data-ttu-id="9c3c3-135">`Remove-PSSession`Cmdlet `$S` 从当前会话中删除 PSSession。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-135">The `Remove-PSSession` cmdlet deletes the PSSession in `$S` from the current session.</span></span> <span data-ttu-id="9c3c3-136">此命令显示 PSSession 不需要处于活动状态即可使用从会话中导入的命令。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-136">This command shows that the PSSession need not be active to use the commands that were imported from the session.</span></span> <span data-ttu-id="9c3c3-137">`Import-Module`Cmdlet 将 TestCmdlets 模块中的 cmdlet 添加到当前会话。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-137">The `Import-Module` cmdlet adds the cmdlets in the TestCmdlets module to the current session.</span></span> <span data-ttu-id="9c3c3-138">可随时在任何会话中运行该命令。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-138">The command can be run in any session at any time.</span></span>

<span data-ttu-id="9c3c3-139">`Get-Help`Cmdlet 将获取名称以 "Test" 开头的 cmdlet 的帮助。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-139">The `Get-Help` cmdlet gets help for cmdlets whose names begin with Test.</span></span> <span data-ttu-id="9c3c3-140">将模块中的命令添加到当前会话后，可以使用 `Get-Help` 和 `Get-Command` cmdlet 来了解导入的命令。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-140">After the commands in a module are added to the current session, you can use the `Get-Help` and `Get-Command` cmdlets to learn about the imported commands.</span></span> <span data-ttu-id="9c3c3-141">`Test-Files`Cmdlet 从 Server01 计算机导出并添加到会话中。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-141">The `Test-Files` cmdlet was exported from the Server01 computer and added to the session.</span></span> <span data-ttu-id="9c3c3-142">该 `Test-Files` cmdlet 在从中导入该命令的计算机上的远程会话中运行。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-142">The `Test-Files` cmdlet runs in a remote session on the computer from which the command was imported.</span></span> <span data-ttu-id="9c3c3-143">PowerShell 将从 TestCmdlets 模块中存储的信息创建一个会话。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-143">PowerShell creates a session from information that is stored in the TestCmdlets module.</span></span>

### <span data-ttu-id="9c3c3-144">示例4：在当前会话中导出和寄存器命令</span><span class="sxs-lookup"><span data-stu-id="9c3c3-144">Example 4: Export and clobber commands in the current session</span></span>

<span data-ttu-id="9c3c3-145">此示例将存储在变量中的命令导出到当前会话中。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-145">This example exports commands that are stored in a variable into the current session.</span></span>

```powershell
Export-PSSession -Session $S -AllowClobber -OutputModule AllCommands
```

<span data-ttu-id="9c3c3-146">此 `Export-PSSession` 命令会将变量中 PSSession 的所有命令和格式数据导出 `$S` 到当前会话中。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-146">This `Export-PSSession` command exports all commands and all formatting data from the PSSession in the `$S` variable into the current session.</span></span> <span data-ttu-id="9c3c3-147">**AllowClobber** 参数包含的命令与当前会话中的命令具有相同的名称。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-147">The **AllowClobber** parameter includes commands with the same names as commands in the current session.</span></span>

### <span data-ttu-id="9c3c3-148">示例5：从关闭的 PSSession 导出命令</span><span class="sxs-lookup"><span data-stu-id="9c3c3-148">Example 5: Export commands from a closed PSSession</span></span>

<span data-ttu-id="9c3c3-149">此示例演示如何在关闭创建导出的命令的 PSSession 后，通过特殊选项运行导出的命令。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-149">This example shows how to run the exported commands with special options when the PSSession that created the exported commands is closed.</span></span>

<span data-ttu-id="9c3c3-150">如果在导入模块时原始远程会话已关闭，则该模块将使用连接到原始计算机的任何打开的远程会话。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-150">If the original remote session is closed when a module is imported, the module will use any open remote session that connects to the originating computer.</span></span> <span data-ttu-id="9c3c3-151">如果源计算机没有当前会话，则该模块将重新建立会话。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-151">If there is no current session to the originating computer, the module will reestablish a session.</span></span>

<span data-ttu-id="9c3c3-152">若要在远程会话中使用特殊选项运行导出的命令，您必须在导入模块之前，使用这些选项创建远程会话。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-152">To run exported commands with special options in a remote session, you must create a remote session with those options before you import the module.</span></span> <span data-ttu-id="9c3c3-153">将 `New-PSSession` cmdlet 与 **SessionOption** 参数一起使用</span><span class="sxs-lookup"><span data-stu-id="9c3c3-153">Use the `New-PSSession` cmdlet with the **SessionOption** parameter</span></span>

```powershell
$Options = New-PSSessionOption -NoMachineProfile
$S = New-PSSession -ComputerName Server01 -SessionOption $Options
Export-PSSession -Session $S -OutputModule Server01
Remove-PSSession $S
New-PSSession -ComputerName Server01 -SessionOption $Options
Import-Module Server01
```

<span data-ttu-id="9c3c3-154">`New-PSSessionOption`Cmdlet 将创建一个 **PSSessionOption** 对象，并将该对象保存在 `$Options` 变量中。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-154">The `New-PSSessionOption` cmdlet creates a **PSSessionOption** object, and it saves the object in the `$Options` variable.</span></span> <span data-ttu-id="9c3c3-155">`New-PSSession`命令在 Server01 计算机上创建 PSSession。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-155">The `New-PSSession` command creates a PSSession on the Server01 computer.</span></span>
<span data-ttu-id="9c3c3-156">**SessionOption** 参数使用存储在中的对象 `$Options` 。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-156">The **SessionOption** parameter uses the object stored in `$Options`.</span></span> <span data-ttu-id="9c3c3-157">会话存储在 `$S` 变量中。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-157">The session is stored in the `$S` variable.</span></span>

<span data-ttu-id="9c3c3-158">`Export-PSSession`Cmdlet 可将中的 PSSession 的命令导出 `$S` 到 Server01 模块中。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-158">The `Export-PSSession` cmdlet exports commands from the PSSession in `$S` to the Server01 module.</span></span>
<span data-ttu-id="9c3c3-159">`Remove-PSSession`Cmdlet 将删除该变量中的 PSSession `$S` 。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-159">The `Remove-PSSession` cmdlet deletes the PSSession in the `$S` variable.</span></span>

<span data-ttu-id="9c3c3-160">`New-PSSession`Cmdlet 将创建一个连接到 Server01 计算机的新 PSSession。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-160">The `New-PSSession` cmdlet creates a new PSSession that connects to the Server01 computer.</span></span> <span data-ttu-id="9c3c3-161">**SessionOption** 参数使用存储在中的对象 `$Options` 。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-161">The **SessionOption** parameter uses the object stored in `$Options`.</span></span> <span data-ttu-id="9c3c3-162">`Import-Module`Cmdlet 从 Server01 模块导入命令。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-162">The `Import-Module` cmdlet imports the commands from the Server01 module.</span></span> <span data-ttu-id="9c3c3-163">模块中的命令在 Server01 计算机上的 PSSession 中运行。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-163">The commands in the module are run in the PSSession on the Server01 computer.</span></span>

## <span data-ttu-id="9c3c3-164">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9c3c3-164">PARAMETERS</span></span>

### <span data-ttu-id="9c3c3-165">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="9c3c3-165">-AllowClobber</span></span>

<span data-ttu-id="9c3c3-166">导出指定命令，即使它们与当前会话中的命令同名。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-166">Exports the specified commands, even if they have the same names as commands in the current session.</span></span>

<span data-ttu-id="9c3c3-167">如果导出与当前会话中的命令同名的命令，则导出的命令会隐藏或替换原始命令。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-167">If you export a command with the same name as a command in the current session, the exported command hides or replaces the original commands.</span></span> <span data-ttu-id="9c3c3-168">有关详细信息，请参阅 [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-168">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span></span>

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

### <span data-ttu-id="9c3c3-169">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="9c3c3-169">-ArgumentList</span></span>

<span data-ttu-id="9c3c3-170">将使用指定的参数（参数值）所得到的命令的变体导出。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-170">Exports the variant of the command that results from using the specified arguments (parameter values).</span></span>

<span data-ttu-id="9c3c3-171">例如，若要导出证书中的命令的变体 `Get-Item` (Cert： ) 驱动器 `$S` ，请键入 `Export-PSSession -Session $S -Command Get-Item -ArgumentList cert:` 。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-171">For example, to export the variant of the `Get-Item` command in the certificate (Cert:) drive in the PSSession in `$S`, type `Export-PSSession -Session $S -Command Get-Item -ArgumentList cert:`.</span></span>

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

### <span data-ttu-id="9c3c3-172">-Certificate</span><span class="sxs-lookup"><span data-stu-id="9c3c3-172">-Certificate</span></span>

<span data-ttu-id="9c3c3-173">指定客户端证书，该证书用于对创建的模块中 ( \* .Format.ps1xml) 或脚本模块文件 ( hbase-runner.psm1) 进行签名 `Export-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-173">Specifies the client certificate that is used to sign the format files (\*.Format.ps1xml) or script module files (.psm1) in the module that `Export-PSSession` creates.</span></span> <span data-ttu-id="9c3c3-174">输入一个包含证书的变量，或可获取该证书的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-174">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="9c3c3-175">若要查找证书，请使用 `Get-PfxCertificate` cmdlet，或使用 `Get-ChildItem` 证书 (Cert： ) 驱动器中的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-175">To find a certificate, use the `Get-PfxCertificate` cmdlet or use the `Get-ChildItem` cmdlet in the Certificate (Cert:) drive.</span></span> <span data-ttu-id="9c3c3-176">如果证书无效或不具有足够的权限，则该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-176">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="9c3c3-177">-CommandName</span><span class="sxs-lookup"><span data-stu-id="9c3c3-177">-CommandName</span></span>

<span data-ttu-id="9c3c3-178">仅将具有指定名称或名称模式的命令导出。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-178">Exports only the commands with the specified names or name patterns.</span></span> <span data-ttu-id="9c3c3-179">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-179">Wildcards are permitted.</span></span> <span data-ttu-id="9c3c3-180">使用 **CommandName** 或其 **别名。**</span><span class="sxs-lookup"><span data-stu-id="9c3c3-180">Use **CommandName** or its alias, **Name** .</span></span>

<span data-ttu-id="9c3c3-181">默认情况下， `Export-PSSession` 从 PSSession 导出所有命令，但与当前会话中的命令同名的命令除外。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-181">By default, `Export-PSSession` exports all commands from the PSSession except for commands that have the same names as commands in the current session.</span></span> <span data-ttu-id="9c3c3-182">这可以防止当前会话中的命令隐藏或替换命令。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-182">This prevents commands from being hidden or replaced by commands in the current session.</span></span> <span data-ttu-id="9c3c3-183">若要导出所有命令（甚至是那些隐藏或替换其他命令的命令），请使用 **AllowClobber** 参数。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-183">To export all commands, even those that hide or replace other commands, use the **AllowClobber** parameter.</span></span>

<span data-ttu-id="9c3c3-184">如果使用 **CommandName** 参数，则将不导出命令的格式设置文件，除非使用 **FormatTypeName** 参数。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-184">If you use the **CommandName** parameter, the formatting files for the commands are not exported unless you use the **FormatTypeName** parameter.</span></span> <span data-ttu-id="9c3c3-185">同样，如果使用 **FormatTypeName** 参数，则不会导出任何命令，除非使用 **CommandName** 参数。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-185">Similarly, if you use the **FormatTypeName** parameter, no commands are exported unless you use the **CommandName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 2
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="9c3c3-186">-CommandType</span><span class="sxs-lookup"><span data-stu-id="9c3c3-186">-CommandType</span></span>

<span data-ttu-id="9c3c3-187">仅导出指定类型的命令对象。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-187">Exports only the specified types of command objects.</span></span> <span data-ttu-id="9c3c3-188">使用 **CommandType** 或其别名 **Type** 。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-188">Use **CommandType** or its alias, **Type** .</span></span>

<span data-ttu-id="9c3c3-189">此参数可接受的值如下所示：</span><span class="sxs-lookup"><span data-stu-id="9c3c3-189">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="9c3c3-190">A.</span><span class="sxs-lookup"><span data-stu-id="9c3c3-190">Alias.</span></span> <span data-ttu-id="9c3c3-191">当前会话中的所有 PowerShell 别名。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-191">All PowerShell aliases in the current session.</span></span>
- <span data-ttu-id="9c3c3-192">全部。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-192">All.</span></span> <span data-ttu-id="9c3c3-193">所有命令类型。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-193">All command types.</span></span> <span data-ttu-id="9c3c3-194">它等效于 `Get-Command -Name *` 。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-194">It is the equivalent of `Get-Command -Name *`.</span></span>
- <span data-ttu-id="9c3c3-195">应用程序。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-195">Application.</span></span> <span data-ttu-id="9c3c3-196">Path 环境变量中列出的路径中的 PowerShell 文件以外的所有文件 (`$env:path`) ，包括 .txt、.exe 和 .dll 文件。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-196">All files other than PowerShell files in paths listed in the Path environment variable (`$env:path`), including .txt, .exe, and .dll files.</span></span>
- <span data-ttu-id="9c3c3-197">Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9c3c3-197">Cmdlet.</span></span> <span data-ttu-id="9c3c3-198">当前会话中的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-198">The cmdlets in the current session.</span></span> <span data-ttu-id="9c3c3-199">Cmdlet 为默认值。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-199">Cmdlet is the default.</span></span>
- <span data-ttu-id="9c3c3-200">配置。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-200">Configuration.</span></span> <span data-ttu-id="9c3c3-201">PowerShell 配置。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-201">A PowerShell configuration.</span></span> <span data-ttu-id="9c3c3-202">有关详细信息，请参阅 [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-202">For more information, see [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md).</span></span>
- <span data-ttu-id="9c3c3-203">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="9c3c3-203">ExternalScript.</span></span> <span data-ttu-id="9c3c3-204">Path 环境变量中列出的路径中的所有 ps1 文件 (`$env:path`) 。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-204">All .ps1 files in the paths listed in the Path environment variable (`$env:path`).</span></span>
- <span data-ttu-id="9c3c3-205">Filter 和 Function。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-205">Filter and Function.</span></span> <span data-ttu-id="9c3c3-206">所有 PowerShell 函数。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-206">All PowerShell functions.</span></span>
- <span data-ttu-id="9c3c3-207">脚本。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-207">Script.</span></span> <span data-ttu-id="9c3c3-208">当前会话中的脚本块。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-208">Script blocks in the current session.</span></span>
- <span data-ttu-id="9c3c3-209">Workflow.</span><span class="sxs-lookup"><span data-stu-id="9c3c3-209">Workflow.</span></span> <span data-ttu-id="9c3c3-210">PowerShell 工作流。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-210">A PowerShell workflow.</span></span> <span data-ttu-id="9c3c3-211">有关详细信息，请参阅 [about_Workflows](../PSWorkflow/About/about_Workflows.md)。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-211">For more information, see [about_Workflows](../PSWorkflow/About/about_Workflows.md).</span></span>

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: Alias, All, Application, Cmdlet, Configuration, ExternalScript, Filter, Function, Script, Workflow

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9c3c3-212">-Encoding</span><span class="sxs-lookup"><span data-stu-id="9c3c3-212">-Encoding</span></span>

<span data-ttu-id="9c3c3-213">指定目标文件的编码类型。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-213">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="9c3c3-214">默认值是 `UTF8`。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-214">The default value is `UTF8`.</span></span>

<span data-ttu-id="9c3c3-215">此参数可接受的值如下所示：</span><span class="sxs-lookup"><span data-stu-id="9c3c3-215">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="9c3c3-216">`ASCII` 使用 ASCII (7 位) 字符集。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-216">`ASCII` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="9c3c3-217">`BigEndianUnicode` 使用带有大 endian 字节顺序的 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-217">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="9c3c3-218">`Default` 使用与系统的活动代码页相对应的编码。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-218">`Default` Uses the encoding that corresponds to the system's active code page.</span></span>
- <span data-ttu-id="9c3c3-219">`OEM` 使用与系统的当前 OEM 代码页相对应的编码。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-219">`OEM` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="9c3c3-220">`Unicode` 使用带有小 endian 字节顺序的 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-220">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="9c3c3-221">`UTF7` 使用 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-221">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="9c3c3-222">`UTF8` 使用 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-222">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="9c3c3-223">`UTF32` 使用带有小 endian 字节顺序的 32 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-223">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: UTF8
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9c3c3-224">-Force</span><span class="sxs-lookup"><span data-stu-id="9c3c3-224">-Force</span></span>

<span data-ttu-id="9c3c3-225">即使该文件具有只读属性，也会覆盖一个或多个现有输出文件。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-225">Overwrites one or more existing output files, even if the file has the read-only attribute.</span></span>

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

### <span data-ttu-id="9c3c3-226">-FormatTypeName</span><span class="sxs-lookup"><span data-stu-id="9c3c3-226">-FormatTypeName</span></span>

<span data-ttu-id="9c3c3-227">仅导出指定 Microsoft .NET Framework 类型的格式指令。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-227">Exports formatting instructions only for the specified Microsoft .NET Framework types.</span></span> <span data-ttu-id="9c3c3-228">输入类型名称。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-228">Enter the type names.</span></span> <span data-ttu-id="9c3c3-229">默认情况下， `Export-PSSession` 将导出所有不在 **system.web** 命名空间中的 .NET Framework 类型的格式说明。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-229">By default, `Export-PSSession` exports formatting instructions for all .NET Framework types that are not in the **System.Management.Automation** namespace.</span></span>

<span data-ttu-id="9c3c3-230">此参数的值必须是要 `Get-FormatData` 从其导入命令的会话中的命令返回的类型的名称。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-230">The value of this parameter must be the name of a type that is returned by a `Get-FormatData` command in the session from which the commands are being imported.</span></span> <span data-ttu-id="9c3c3-231">若要获取远程会话中的所有格式设置数据，请键入 `*` 。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-231">To get all of the formatting data in the remote session, type `*`.</span></span>

<span data-ttu-id="9c3c3-232">如果使用 **FormatTypeName** 参数，则不会导出任何命令，除非使用 **CommandName** 参数。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-232">If you use the **FormatTypeName** parameter, no commands are exported unless you use the **CommandName** parameter.</span></span>

<span data-ttu-id="9c3c3-233">如果使用 **CommandName** 参数，则将不导出命令的格式设置文件，除非使用 **FormatTypeName** 参数。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-233">If you use the **CommandName** parameter, the formatting files for the commands are not exported unless you use the **FormatTypeName** parameter.</span></span>

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

### <span data-ttu-id="9c3c3-234">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="9c3c3-234">-FullyQualifiedModule</span></span>

<span data-ttu-id="9c3c3-235">指定名称以 **ModuleSpecification** 对象的形式指定的模块。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-235">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span>
<span data-ttu-id="9c3c3-236">请参阅 ModuleSpecification 构造函数的 "备注" 部分 [ (哈希表) ](https://msdn.microsoft.com/library/jj136290)。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-236">See the Remarks section of [ModuleSpecification Constructor (Hashtable)](https://msdn.microsoft.com/library/jj136290).</span></span>

<span data-ttu-id="9c3c3-237">例如， **FullyQualifiedModule** 参数接受以下任何一种格式指定的模块名称：</span><span class="sxs-lookup"><span data-stu-id="9c3c3-237">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in either of these formats:</span></span>

`@{ModuleName = "modulename"; ModuleVersion = "version_number"}`

`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="9c3c3-238">**ModuleName** 和 **ModuleVersion** 是必需的，但 **Guid** 是可选的。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-238">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span> <span data-ttu-id="9c3c3-239">不能在与 **Module** 参数相同的命令中指定 **FullyQualifiedModule** 参数;这两个参数是互斥的。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-239">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter; the two parameters are mutually exclusive.</span></span>

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

### <span data-ttu-id="9c3c3-240">-Module</span><span class="sxs-lookup"><span data-stu-id="9c3c3-240">-Module</span></span>

<span data-ttu-id="9c3c3-241">仅导出指定 PowerShell 管理单元和模块中的命令。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-241">Exports only the commands in the specified PowerShell snap-ins and modules.</span></span> <span data-ttu-id="9c3c3-242">输入管理单元和模块的名称。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-242">Enter the snap-in and module names.</span></span> <span data-ttu-id="9c3c3-243">不允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-243">Wildcards are not permitted.</span></span>

<span data-ttu-id="9c3c3-244">有关详细信息，请参阅 `Import-Module` 和 [about_PSSnapins](../Microsoft.PowerShell.Core/About/about_PSSnapins.md)。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-244">For more information, see `Import-Module` and [about_PSSnapins](../Microsoft.PowerShell.Core/About/about_PSSnapins.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9c3c3-245">-OutputModule</span><span class="sxs-lookup"><span data-stu-id="9c3c3-245">-OutputModule</span></span>

<span data-ttu-id="9c3c3-246">指定由创建的模块的可选路径和名称 `Export-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-246">Specifies an optional path and name for the module created by `Export-PSSession`.</span></span> <span data-ttu-id="9c3c3-247">默认路径为 `$home\Documents\WindowsPowerShell\Modules`。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-247">The default path is `$home\Documents\WindowsPowerShell\Modules`.</span></span> <span data-ttu-id="9c3c3-248">此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-248">This parameter is required.</span></span>

<span data-ttu-id="9c3c3-249">如果已存在模块子目录或创建的任何文件 `Export-PSSession` ，则该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-249">If the module subdirectory or any of the files that `Export-PSSession` creates already exist, the command fails.</span></span> <span data-ttu-id="9c3c3-250">若要覆盖现有文件，请使用 **Force** 参数。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-250">To overwrite existing files, use the **Force** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, ModuleName

Required: True
Position: 1
Default value: $home\Documents\WindowsPowerShell\Modules
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9c3c3-251">-Session</span><span class="sxs-lookup"><span data-stu-id="9c3c3-251">-Session</span></span>

<span data-ttu-id="9c3c3-252">指定要从中导出命令的 PSSession。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-252">Specifies the PSSession from which the commands are exported.</span></span> <span data-ttu-id="9c3c3-253">输入包含会话对象的变量或获取会话对象的命令（如 `Get-PSSession` 命令）。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-253">Enter a variable that contains a session object or a command that gets a session object, such as a `Get-PSSession` command.</span></span> <span data-ttu-id="9c3c3-254">此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-254">This parameter is required.</span></span>

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

### <span data-ttu-id="9c3c3-255">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9c3c3-255">CommonParameters</span></span>

<span data-ttu-id="9c3c3-256">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-256">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9c3c3-257">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-257">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9c3c3-258">输入</span><span class="sxs-lookup"><span data-stu-id="9c3c3-258">INPUTS</span></span>

### <span data-ttu-id="9c3c3-259">无</span><span class="sxs-lookup"><span data-stu-id="9c3c3-259">None</span></span>

<span data-ttu-id="9c3c3-260">不能通过管道将对象传递给 `Export-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-260">You cannot pipe objects to `Export-PSSession`.</span></span>

## <span data-ttu-id="9c3c3-261">输出</span><span class="sxs-lookup"><span data-stu-id="9c3c3-261">OUTPUTS</span></span>

### <span data-ttu-id="9c3c3-262">System.IO.FileInfo</span><span class="sxs-lookup"><span data-stu-id="9c3c3-262">System.IO.FileInfo</span></span>

<span data-ttu-id="9c3c3-263">`Export-PSSession` 返回包含它所创建的模块的文件列表。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-263">`Export-PSSession` returns a list of files that comprise the module that it created.</span></span>

## <span data-ttu-id="9c3c3-264">注释</span><span class="sxs-lookup"><span data-stu-id="9c3c3-264">NOTES</span></span>

<span data-ttu-id="9c3c3-265">`Export-PSSession` 依赖于 PowerShell 远程处理基础结构。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-265">`Export-PSSession` relies on the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="9c3c3-266">若要使用此 cmdlet，必须对计算机进行相应配置以进行远程处理。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-266">To use this cmdlet, the computer must be configured for remoting.</span></span> <span data-ttu-id="9c3c3-267">有关详细信息，请参阅 [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-267">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="9c3c3-268">不能使用 `Export-PSSession` 导出 PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-268">You cannot use `Export-PSSession` to export a PowerShell provider.</span></span>

<span data-ttu-id="9c3c3-269">导出的命令在从中导出这些命令的 PSSession 中隐式运行。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-269">Exported commands run implicitly in the PSSession from which they were exported.</span></span> <span data-ttu-id="9c3c3-270">远程运行命令的详细信息完全由 PowerShell 处理。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-270">The details of running the commands remotely are handled entirely by PowerShell.</span></span> <span data-ttu-id="9c3c3-271">可以像运行本地命令那样运行导出的命令。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-271">You can run the exported commands just as you would run local commands.</span></span>

<span data-ttu-id="9c3c3-272">`Export-ModuleMember` 捕获并保存有关它所导出的模块中的 PSSession 的信息。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-272">`Export-ModuleMember` captures and saves information about the PSSession in the module that it exports.</span></span> <span data-ttu-id="9c3c3-273">如果在导入模块时从中导出命令的 PSSession 已关闭，并且同一台计算机上没有活动的 Pssession，则该模块中的命令将尝试重新创建 PSSession。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-273">If the PSSession from which the commands were exported is closed when you import the module, and there are no active PSSessions to the same computer, the commands in the module attempt to recreate the PSSession.</span></span> <span data-ttu-id="9c3c3-274">如果重新创建 PSSession 的尝试失败，则导出的命令将不会运行。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-274">If attempts to recreate the PSSession fail, the exported commands will not run.</span></span>

<span data-ttu-id="9c3c3-275">`Export-ModuleMember`在模块中捕获和保存的会话信息不包括会话选项，如您在首选项变量中指定的， `$PSSessionOption` 或者使用 **SessionOption** `New-PSSession` 、 `Enter-PSSession` 或 cmdlet 的 SessionOption 参数 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-275">The session information that `Export-ModuleMember` captures and saves in the module does not include session options, such as those that you specify in the `$PSSessionOption` preference variable or by using the **SessionOption** parameter of the `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` cmdlets.</span></span> <span data-ttu-id="9c3c3-276">如果在导入模块时原始 PSSession 已关闭，则该模块将使用同一台计算机上的另一个 PSSession（如果存在）。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-276">If the original PSSession is closed when you import the module, the module will use another PSSession to the same computer, if one is available.</span></span> <span data-ttu-id="9c3c3-277">若要启用导入的命令以在正确配置的会话中运行，请在导入模块之前使用所需选项来创建 PSSession。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-277">To enable the imported commands to run in a correctly configured session, create a PSSession with the options that you want before you import the module.</span></span>

<span data-ttu-id="9c3c3-278">若要查找要导出的命令，请 `Export-PSSession` 使用 `Invoke-Command` Cmdlet `Get-Command` 在 PSSession 中运行命令。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-278">To find the commands to export, `Export-PSSession` uses the `Invoke-Command` cmdlet to run a `Get-Command` command in the PSSession.</span></span> <span data-ttu-id="9c3c3-279">若要获取和保存命令的格式设置数据，请使用 `Get-FormatData` 和 `Export-FormatData` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-279">To get and save formatting data for the commands, it uses the `Get-FormatData` and `Export-FormatData` cmdlets.</span></span> <span data-ttu-id="9c3c3-280">`Invoke-Command` `Get-Command` `Get-FormatData` `Export-FormatData` 运行命令时，可能会看到来自、、和的错误消息 `Export-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-280">You might see error messages from `Invoke-Command`, `Get-Command`, `Get-FormatData`, and `Export-FormatData` when you run an `Export-PSSession` command.</span></span> <span data-ttu-id="9c3c3-281">此外， `Export-PSSession` 不能从不包括 `Get-Command` 、 `Get-FormatData` 、 `Select-Object` 和 cmdlet 的会话中导出命令 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-281">Also, `Export-PSSession` cannot export commands from a session that does not include the `Get-Command`, `Get-FormatData`, `Select-Object`, and `Get-Help` cmdlets.</span></span>

<span data-ttu-id="9c3c3-282">`Export-PSSession` 使用 `Write-Progress` cmdlet 显示该命令的进度。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-282">`Export-PSSession` uses the `Write-Progress` cmdlet to display the progress of the command.</span></span> <span data-ttu-id="9c3c3-283">该命令正在运行时，你可能会看到进度条。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-283">You might see the progress bar while the command is running.</span></span>

<span data-ttu-id="9c3c3-284">导出的命令与其他远程命令具有相同的限制（包括无法启动具有用户界面的程序，如记事本）。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-284">Exported commands have the same limitations as other remote commands, including the inability to start a program with a user interface, such as Notepad.</span></span>

<span data-ttu-id="9c3c3-285">因为 PowerShell 配置文件不在 Pssession 中运行，所以配置文件添加到会话中的命令不能用于 `Export-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-285">Because PowerShell profiles are not run in PSSessions, the commands that a profile adds to a session are not available to `Export-PSSession`.</span></span> <span data-ttu-id="9c3c3-286">若要从配置文件中导出命令，请在 `Invoke-Command` 导出命令之前使用命令手动运行该配置文件。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-286">To export commands from a profile, use an `Invoke-Command` command to run the profile in the PSSession manually before exporting commands.</span></span>

<span data-ttu-id="9c3c3-287">创建的模块 `Export-PSSession` 可能包含格式设置文件，即使该命令不导入格式数据也是如此。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-287">The module that `Export-PSSession` creates might include a formatting file, even if the command does not import formatting data.</span></span> <span data-ttu-id="9c3c3-288">如果该命令不导入格式数据，则创建的任何格式设置文件都不包含格式数据。</span><span class="sxs-lookup"><span data-stu-id="9c3c3-288">If the command does not import formatting data, any formatting files that are created will not contain formatting data.</span></span>

## <span data-ttu-id="9c3c3-289">相关链接</span><span class="sxs-lookup"><span data-stu-id="9c3c3-289">RELATED LINKS</span></span>

[<span data-ttu-id="9c3c3-290">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="9c3c3-290">about_Command_Precedence</span></span>](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)

[<span data-ttu-id="9c3c3-291">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="9c3c3-291">about_PSSessions</span></span>](../Microsoft.PowerShell.Core/About/about_PSSessions.md)

[<span data-ttu-id="9c3c3-292">about_PSSnapins</span><span class="sxs-lookup"><span data-stu-id="9c3c3-292">about_PSSnapins</span></span>](../Microsoft.PowerShell.Core/About/about_PSSnapins.md)

[<span data-ttu-id="9c3c3-293">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="9c3c3-293">about_Remote_Requirements</span></span>](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)

[<span data-ttu-id="9c3c3-294">Import-Module</span><span class="sxs-lookup"><span data-stu-id="9c3c3-294">Import-Module</span></span>](../Microsoft.PowerShell.Core/Import-Module.md)

[<span data-ttu-id="9c3c3-295">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="9c3c3-295">Import-PSSession</span></span>](Import-PSSession.md)

[<span data-ttu-id="9c3c3-296">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="9c3c3-296">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="9c3c3-297">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="9c3c3-297">New-PSSession</span></span>](../Microsoft.PowerShell.Core/New-PSSession.md)

[<span data-ttu-id="9c3c3-298">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="9c3c3-298">New-PSSessionOption</span></span>](../Microsoft.PowerShell.Core/New-PSSessionOption.md)

[<span data-ttu-id="9c3c3-299">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="9c3c3-299">Remove-PSSession</span></span>](../Microsoft.PowerShell.Core/Remove-PSSession.md)