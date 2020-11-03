---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSSession
ms.openlocfilehash: 3b087eb53fa575b2af7b18ec17823f9197e719d6
ms.sourcegitcommit: 9dddf1d2e91ebcd347fcfb7bf6ef670d49a12ab7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "93199165"
---
# <span data-ttu-id="bde3d-103">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="bde3d-103">Enter-PSSession</span></span>

## <span data-ttu-id="bde3d-104">摘要</span><span class="sxs-lookup"><span data-stu-id="bde3d-104">SYNOPSIS</span></span>
<span data-ttu-id="bde3d-105">启动与远程计算机的交互式会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-105">Starts an interactive session with a remote computer.</span></span>

## <span data-ttu-id="bde3d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bde3d-106">SYNTAX</span></span>

### <span data-ttu-id="bde3d-107">ComputerName（默认值）</span><span class="sxs-lookup"><span data-stu-id="bde3d-107">ComputerName (Default)</span></span>

```
Enter-PSSession [-ComputerName] <String> [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL] [-ApplicationName <String>]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="bde3d-108">SSHHost</span><span class="sxs-lookup"><span data-stu-id="bde3d-108">SSHHost</span></span>

```
Enter-PSSession [-HostName] <String> [-Port <Int32>] [-UserName <String>] [-KeyFilePath <String>]
 [-SSHTransport] [<CommonParameters>]
```

### <span data-ttu-id="bde3d-109">会话</span><span class="sxs-lookup"><span data-stu-id="bde3d-109">Session</span></span>

```
Enter-PSSession [[-Session] <PSSession>] [<CommonParameters>]
```

### <span data-ttu-id="bde3d-110">Uri</span><span class="sxs-lookup"><span data-stu-id="bde3d-110">Uri</span></span>

```
Enter-PSSession [[-ConnectionUri] <Uri>] [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="bde3d-111">InstanceId</span><span class="sxs-lookup"><span data-stu-id="bde3d-111">InstanceId</span></span>

```
Enter-PSSession [-InstanceId <Guid>] [<CommonParameters>]
```

### <span data-ttu-id="bde3d-112">ID</span><span class="sxs-lookup"><span data-stu-id="bde3d-112">Id</span></span>

```
Enter-PSSession [[-Id] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="bde3d-113">名称</span><span class="sxs-lookup"><span data-stu-id="bde3d-113">Name</span></span>

```
Enter-PSSession [-Name <String>] [<CommonParameters>]
```

### <span data-ttu-id="bde3d-114">VMId</span><span class="sxs-lookup"><span data-stu-id="bde3d-114">VMId</span></span>

```
Enter-PSSession [-VMId] <Guid> [-Credential] <PSCredential> [-ConfigurationName <String>] [<CommonParameters>]
```

### <span data-ttu-id="bde3d-115">VMName</span><span class="sxs-lookup"><span data-stu-id="bde3d-115">VMName</span></span>

```
Enter-PSSession [-VMName] <String> [-Credential] <PSCredential> [-ConfigurationName <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="bde3d-116">ContainerId</span><span class="sxs-lookup"><span data-stu-id="bde3d-116">ContainerId</span></span>

```
Enter-PSSession [-ContainerId] <String> [-ConfigurationName <String>] [-RunAsAdministrator]
 [<CommonParameters>]
```

## <span data-ttu-id="bde3d-117">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="bde3d-117">DESCRIPTION</span></span>

<span data-ttu-id="bde3d-118">`Enter-PSSession`Cmdlet 可启动与单台远程计算机的交互式会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-118">The `Enter-PSSession` cmdlet starts an interactive session with a single remote computer.</span></span>
<span data-ttu-id="bde3d-119">在会话期间，你键入的命令将在远程计算机上运行，就像你直接在远程计算机上键入一样。</span><span class="sxs-lookup"><span data-stu-id="bde3d-119">During the session, the commands that you type run on the remote computer, just as if you were typing directly on the remote computer.</span></span> <span data-ttu-id="bde3d-120">一次只可以进行一个交互式会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-120">You can have only one interactive session at a time.</span></span>

<span data-ttu-id="bde3d-121">通常，你可以使用 **ComputerName** 参数来指定远程计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="bde3d-121">Typically, you use the **ComputerName** parameter to specify the name of the remote computer.</span></span>
<span data-ttu-id="bde3d-122">但是，你还可以使用通过 `New-PSSession` cmdlet 为交互式会话创建的会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-122">However, you can also use a session that you create by using the `New-PSSession` cmdlet for the interactive session.</span></span> <span data-ttu-id="bde3d-123">但是，不能使用 `Disconnect-PSSession` 、 `Connect-PSSession` 或 cmdlet 与 `Receive-PSSession` 交互式会话断开连接或重新连接到该会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-123">However, you cannot use the `Disconnect-PSSession`, `Connect-PSSession`, or `Receive-PSSession` cmdlets to disconnect from or re-connect to an interactive session.</span></span>

<span data-ttu-id="bde3d-124">从 PowerShell 6.0 开始，可以使用安全外壳 (SSH) 建立与远程计算机的连接，如果本地计算机上有 SSH 并且远程计算机配置了 PowerShell SSH 终结点。</span><span class="sxs-lookup"><span data-stu-id="bde3d-124">Starting with PowerShell 6.0 you can use Secure Shell (SSH) to establish a connection to a remote computer, if SSH is available on the local computer and the remote computer is configured with a PowerShell SSH endpoint.</span></span> <span data-ttu-id="bde3d-125">基于 SSH 的 PowerShell 远程会话的优点在于，它可以跨多个平台 (Windows、Linux、macOS) 。</span><span class="sxs-lookup"><span data-stu-id="bde3d-125">The benefit an SSH based PowerShell remote session is that it works across multiple platforms (Windows, Linux, macOS).</span></span> <span data-ttu-id="bde3d-126">对于基于 SSH 的远程处理，请使用 **HostName** 参数集指定远程计算机和相关连接信息。</span><span class="sxs-lookup"><span data-stu-id="bde3d-126">For SSH based remoting you use the **HostName** parameter set to specify the remote computer and relevant connection information.</span></span> <span data-ttu-id="bde3d-127">有关如何设置 PowerShell SSH 远程处理的详细信息，请参阅 [通过 SSH 进行 Powershell 远程处理](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)。</span><span class="sxs-lookup"><span data-stu-id="bde3d-127">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

<span data-ttu-id="bde3d-128">若要结束交互式会话并断开与远程计算机的连接，请使用 `Exit-PSSession` cmdlet 或类型 `exit` 。</span><span class="sxs-lookup"><span data-stu-id="bde3d-128">To end the interactive session and disconnect from the remote computer, use the `Exit-PSSession` cmdlet, or type `exit`.</span></span>

## <span data-ttu-id="bde3d-129">示例</span><span class="sxs-lookup"><span data-stu-id="bde3d-129">EXAMPLES</span></span>

### <span data-ttu-id="bde3d-130">示例1：启动交互式会话</span><span class="sxs-lookup"><span data-stu-id="bde3d-130">Example 1: Start an interactive session</span></span>

```
PS> Enter-PSSession
[localhost]: PS>
```

<span data-ttu-id="bde3d-131">此命令将在本地计算机上启动交互式会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-131">This command starts an interactive session on the local computer.</span></span> <span data-ttu-id="bde3d-132">命令提示符将发生更改，以指示你现在正在不同的会话中运行命令。</span><span class="sxs-lookup"><span data-stu-id="bde3d-132">The command prompt changes to indicate that you are now running commands in a different session.</span></span>

<span data-ttu-id="bde3d-133">你输入的命令将在该新会话中运行，而结果将以文本形式返回到默认会话中。</span><span class="sxs-lookup"><span data-stu-id="bde3d-133">The commands that you enter run in the new session, and the results are returned to the default session as text.</span></span>

### <span data-ttu-id="bde3d-134">示例2：使用交互式会话</span><span class="sxs-lookup"><span data-stu-id="bde3d-134">Example 2: Work with an interactive session</span></span>

<span data-ttu-id="bde3d-135">第一个命令使用 `Enter-PSSession` cmdlet 来启动与 Server01 （远程计算机）的交互式会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-135">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with Server01, a remote computer.</span></span> <span data-ttu-id="bde3d-136">会话启动时，命令提示符将更改为包含该计算机名称。</span><span class="sxs-lookup"><span data-stu-id="bde3d-136">When the session starts, the command prompt changes to include the computer name.</span></span>

<span data-ttu-id="bde3d-137">第二个命令获取 PowerShell 进程，并将输出重定向到 Process.txt 文件。</span><span class="sxs-lookup"><span data-stu-id="bde3d-137">The second command gets the PowerShell process and redirects the output to the Process.txt file.</span></span> <span data-ttu-id="bde3d-138">该命令将提交到远程计算机，并且该文件将保存在远程计算机上。</span><span class="sxs-lookup"><span data-stu-id="bde3d-138">The command is submitted to the remote computer, and the file is saved on the remote computer.</span></span>

<span data-ttu-id="bde3d-139">第三个命令使用 **Exit** 关键字来结束交互式会话并关闭连接。</span><span class="sxs-lookup"><span data-stu-id="bde3d-139">The third command uses the **Exit** keyword to end the interactive session and close the connection.</span></span>
<span data-ttu-id="bde3d-140">第四个命令确认 Process.txt 文件是否位于远程计算机上。</span><span class="sxs-lookup"><span data-stu-id="bde3d-140">The fourth command confirms that the Process.txt file is on the remote computer.</span></span> <span data-ttu-id="bde3d-141">`Get-ChildItem`本地计算机上的 ( "dir" ) 命令找不到该文件。</span><span class="sxs-lookup"><span data-stu-id="bde3d-141">A `Get-ChildItem` ("dir") command on the local computer cannot find the file.</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
[Server01]: PS>
[Server01]: PS C:\> Get-Process PowerShell > C:\ps-test\Process.txt
[Server01]: PS C:\> exit
PS C:\>
PS C:\> dir C:\ps-test\process.txt
Get-ChildItem : Cannot find path 'C:\ps-test\process.txt' because it does not exist.
At line:1 char:4
+ dir <<<<  c:\ps-test\process.txt
```

<span data-ttu-id="bde3d-142">此命令显示了如何在与远程计算机的交互式会话中进行工作。</span><span class="sxs-lookup"><span data-stu-id="bde3d-142">This command shows how to work in an interactive session with a remote computer.</span></span>

### <span data-ttu-id="bde3d-143">示例3：使用 Session 参数</span><span class="sxs-lookup"><span data-stu-id="bde3d-143">Example 3: Use the Session parameter</span></span>

```powershell
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
[Server01]: PS>
```

<span data-ttu-id="bde3d-144">这些命令使用的 **Session** 参数 `Enter-PSSession` 在 ( **PSSession** ) 的现有 PowerShell 会话中运行交互式会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-144">These commands use the **Session** parameter of `Enter-PSSession` to run the interactive session in an existing PowerShell session ( **PSSession** ).</span></span>

### <span data-ttu-id="bde3d-145">示例4：启动交互式会话并指定端口和凭据参数</span><span class="sxs-lookup"><span data-stu-id="bde3d-145">Example 4: Start an interactive session and specify the Port and Credential parameters</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01 -Port 90 -Credential Domain01\User01
[Server01]: PS>
```

<span data-ttu-id="bde3d-146">此命令启动与 Server01 计算机的交互式会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-146">This command starts an interactive session with the Server01 computer.</span></span> <span data-ttu-id="bde3d-147">它使用 **port** 参数指定端口，并使用 **Credential** 参数指定有权连接到远程计算机的用户的帐户。</span><span class="sxs-lookup"><span data-stu-id="bde3d-147">It uses the **Port** parameter to specify the port and the **Credential** parameter to specify the account of a user who has permission to connect to the remote computer.</span></span>

### <span data-ttu-id="bde3d-148">示例5：停止交互式会话</span><span class="sxs-lookup"><span data-stu-id="bde3d-148">Example 5: Stop an interactive session</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01
[Server01]: PS> Exit-PSSession
PS>
```

<span data-ttu-id="bde3d-149">此示例显示了如何启动和停止交互式会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-149">This example shows how to start and stop an interactive session.</span></span> <span data-ttu-id="bde3d-150">第一个命令使用 `Enter-PSSession` cmdlet 来启动与 Server01 计算机的交互式会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-150">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with the Server01 computer.</span></span>

<span data-ttu-id="bde3d-151">第二个命令使用 `Exit-PSSession` cmdlet 结束会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-151">The second command uses the `Exit-PSSession` cmdlet to end the session.</span></span> <span data-ttu-id="bde3d-152">你还可以使用 **Exit** 关键字来结束交互式会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-152">You can also use the **Exit** keyword to end the interactive session.</span></span> <span data-ttu-id="bde3d-153">`Exit-PSSession` 和 **退出** 具有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="bde3d-153">`Exit-PSSession` and **Exit** have the same effect.</span></span>

### <span data-ttu-id="bde3d-154">示例6：使用 SSH 启动交互式会话</span><span class="sxs-lookup"><span data-stu-id="bde3d-154">Example 6: Start an interactive session using SSH</span></span>

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer01
```

<span data-ttu-id="bde3d-155">此示例演示如何使用安全外壳 (SSH) 启动交互式会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-155">This example shows how to start an interactive session using Secure Shell (SSH).</span></span> <span data-ttu-id="bde3d-156">如果在远程计算机上配置了 SSH 以提示输入密码，则会出现密码提示。</span><span class="sxs-lookup"><span data-stu-id="bde3d-156">If SSH is configured on the remote computer to prompt for passwords then you will get a password prompt.</span></span>
<span data-ttu-id="bde3d-157">否则，你将需要使用基于 SSH 密钥的用户身份验证。</span><span class="sxs-lookup"><span data-stu-id="bde3d-157">Otherwise you will have to use SSH key based user authentication.</span></span>

### <span data-ttu-id="bde3d-158">示例7：使用 SSH 启动交互式会话并指定端口和用户身份验证密钥</span><span class="sxs-lookup"><span data-stu-id="bde3d-158">Example 7: Start an interactive session using SSH and specify the Port and user authentication key</span></span>

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer02:22 -KeyFilePath c:\<path>\userAKey_rsa
```

<span data-ttu-id="bde3d-159">此示例演示如何使用 SSH 启动交互式会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-159">This example shows how to start an interactive session using SSH.</span></span> <span data-ttu-id="bde3d-160">它使用 **port** 参数指定要使用的端口，并使用 **KeyFilePath** 参数来指定用于对远程计算机上的用户进行身份验证的 RSA 密钥。</span><span class="sxs-lookup"><span data-stu-id="bde3d-160">It uses the **Port** parameter to specify the port to use and the **KeyFilePath** parameter to specify an RSA key used to authenticate the user on the remote computer.</span></span>

## <span data-ttu-id="bde3d-161">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bde3d-161">PARAMETERS</span></span>

### <span data-ttu-id="bde3d-162">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="bde3d-162">-AllowRedirection</span></span>

<span data-ttu-id="bde3d-163">允许将此连接重定向到备用统一资源标识符 (URI)。</span><span class="sxs-lookup"><span data-stu-id="bde3d-163">Allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="bde3d-164">默认情况下，不允许重定向。</span><span class="sxs-lookup"><span data-stu-id="bde3d-164">By default, redirection is not allowed.</span></span>

<span data-ttu-id="bde3d-165">使用 **ConnectionURI** 参数时，远程目标将返回一个指令，以重定向到不同的 URI。</span><span class="sxs-lookup"><span data-stu-id="bde3d-165">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="bde3d-166">默认情况下，PowerShell 不会重定向连接，但你可以使用此参数允许它重定向连接。</span><span class="sxs-lookup"><span data-stu-id="bde3d-166">By default, PowerShell does not redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="bde3d-167">你也可以通过更改 **MaximumConnectionRedirectionCount** 会话选项值，限制重定向连接的次数。</span><span class="sxs-lookup"><span data-stu-id="bde3d-167">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="bde3d-168">使用 cmdlet 的 **MaximumRedirection** 参数 `New-PSSessionOption` 或设置首选项变量的 **MaximumConnectionRedirectionCount** 属性 `$PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="bde3d-168">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="bde3d-169">默认值为 5。</span><span class="sxs-lookup"><span data-stu-id="bde3d-169">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-170">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="bde3d-170">-ApplicationName</span></span>

<span data-ttu-id="bde3d-171">指定连接 URI 的应用程序名称段。</span><span class="sxs-lookup"><span data-stu-id="bde3d-171">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="bde3d-172">当命令中未使用 **ConnectionURI** 参数时，请使用此参数指定应用程序名称。</span><span class="sxs-lookup"><span data-stu-id="bde3d-172">Use this parameter to specify the application name when you are not using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="bde3d-173">默认值为 `$PSSessionApplicationName` 本地计算机上首选项变量的值。</span><span class="sxs-lookup"><span data-stu-id="bde3d-173">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="bde3d-174">如果未定义此首选项变量，则默认值为 WSMAN。</span><span class="sxs-lookup"><span data-stu-id="bde3d-174">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="bde3d-175">该值适用于大多数使用情况。</span><span class="sxs-lookup"><span data-stu-id="bde3d-175">This value is appropriate for most uses.</span></span> <span data-ttu-id="bde3d-176">有关详细信息，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="bde3d-176">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="bde3d-177">**WinRM** 服务使用应用程序名称来选择用于处理连接请求的侦听器。</span><span class="sxs-lookup"><span data-stu-id="bde3d-177">The **WinRM** service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="bde3d-178">此参数的值应与远程计算机上的侦听器的 **URLPrefix** 属性值匹配。</span><span class="sxs-lookup"><span data-stu-id="bde3d-178">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-179">-Authentication</span><span class="sxs-lookup"><span data-stu-id="bde3d-179">-Authentication</span></span>

<span data-ttu-id="bde3d-180">指定用于对用户的凭据进行身份验证的机制。</span><span class="sxs-lookup"><span data-stu-id="bde3d-180">Specifies the mechanism that is used to authenticate the user's credentials.</span></span> <span data-ttu-id="bde3d-181">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="bde3d-181">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="bde3d-182">默认</span><span class="sxs-lookup"><span data-stu-id="bde3d-182">Default</span></span>
- <span data-ttu-id="bde3d-183">基本</span><span class="sxs-lookup"><span data-stu-id="bde3d-183">Basic</span></span>
- <span data-ttu-id="bde3d-184">Credssp</span><span class="sxs-lookup"><span data-stu-id="bde3d-184">Credssp</span></span>
- <span data-ttu-id="bde3d-185">摘要</span><span class="sxs-lookup"><span data-stu-id="bde3d-185">Digest</span></span>
- <span data-ttu-id="bde3d-186">Kerberos</span><span class="sxs-lookup"><span data-stu-id="bde3d-186">Kerberos</span></span>
- <span data-ttu-id="bde3d-187">Negotiate</span><span class="sxs-lookup"><span data-stu-id="bde3d-187">Negotiate</span></span>
- <span data-ttu-id="bde3d-188">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="bde3d-188">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="bde3d-189">默认值为 Default。</span><span class="sxs-lookup"><span data-stu-id="bde3d-189">The default value is Default.</span></span>

<span data-ttu-id="bde3d-190">CredSSP 身份验证仅在 Windows Vista、Windows Server 2008 和更高版本的 Windows 操作系统中可用。</span><span class="sxs-lookup"><span data-stu-id="bde3d-190">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="bde3d-191">有关此参数的值的详细信息，请参阅 [System.management.automation.runspaces.authenticationmechanism 枚举](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="bde3d-191">For more information about the values of this parameter, see [AuthenticationMechanism Enum](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

<span data-ttu-id="bde3d-192">警告：凭据安全支持提供程序 (CredSSP) 身份验证，其中用户的凭据将传递给要进行身份验证的远程计算机，其适用于需要在多个资源（例如访问远程网络共享）上进行身份验证的命令。</span><span class="sxs-lookup"><span data-stu-id="bde3d-192">Caution: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="bde3d-193">此机制增加了远程操作的安全风险。</span><span class="sxs-lookup"><span data-stu-id="bde3d-193">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="bde3d-194">如果远程计算机的安全受到威胁，则传递给该计算机的凭据可用于控制网络会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-194">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, Uri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-195">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="bde3d-195">-CertificateThumbprint</span></span>

<span data-ttu-id="bde3d-196">指定有权执行此操作的用户帐户的数字公钥证书 (X509)。</span><span class="sxs-lookup"><span data-stu-id="bde3d-196">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="bde3d-197">输入证书的证书指纹。</span><span class="sxs-lookup"><span data-stu-id="bde3d-197">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="bde3d-198">在基于客户端证书的身份验证中使用证书。</span><span class="sxs-lookup"><span data-stu-id="bde3d-198">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="bde3d-199">证书只能映射到本地用户帐户，而不适用于域帐户。</span><span class="sxs-lookup"><span data-stu-id="bde3d-199">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="bde3d-200">若要获取证书，请使用 `Get-Item` `Get-ChildItem` PowerShell Cert：驱动器中的或命令。</span><span class="sxs-lookup"><span data-stu-id="bde3d-200">To get a certificate, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-201">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="bde3d-201">-ComputerName</span></span>

<span data-ttu-id="bde3d-202">指定计算机名称。</span><span class="sxs-lookup"><span data-stu-id="bde3d-202">Specifies a computer name.</span></span> <span data-ttu-id="bde3d-203">此 cmdlet 将启动与指定远程计算机的交互式会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-203">This cmdlet starts an interactive session with the specified remote computer.</span></span> <span data-ttu-id="bde3d-204">仅输入一个计算机名称。</span><span class="sxs-lookup"><span data-stu-id="bde3d-204">Enter only one computer name.</span></span> <span data-ttu-id="bde3d-205">默认为本地计算机。</span><span class="sxs-lookup"><span data-stu-id="bde3d-205">The default is the local computer.</span></span>

<span data-ttu-id="bde3d-206">键入计算机的 NetBIOS 名称、IP 地址或完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="bde3d-206">Type the NetBIOS name, the IP address, or the fully qualified domain name of the computer.</span></span> <span data-ttu-id="bde3d-207">还可以通过管道将计算机名称传递给 `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="bde3d-207">You can also pipe a computer name to `Enter-PSSession`.</span></span>

<span data-ttu-id="bde3d-208">若要在 **ComputerName** 参数的值中使用 IP 地址，该命令必须包括 **Credential** 参数。</span><span class="sxs-lookup"><span data-stu-id="bde3d-208">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="bde3d-209">此外，必须为计算机配置 HTTPS 传输，或者必须在本地计算机上的 WinRM TrustedHosts 列表中包含远程计算机的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="bde3d-209">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="bde3d-210">有关将计算机名称添加到 TrustedHosts 列表的说明，请参阅 [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md)中的 "如何将计算机添加到受信任的主机列表中"。</span><span class="sxs-lookup"><span data-stu-id="bde3d-210">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md).</span></span>

<span data-ttu-id="bde3d-211">注意：在 Windows Vista 和更高版本的 Windows 操作系统中，若要在 **ComputerName** 参数的值中包含本地计算机，你必须以 "以管理员身份运行" 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="bde3d-211">Note: In Windows Vista and later versions of the Windows operating system, to include the local computer in the value of the **ComputerName** parameter, you must start PowerShell with the Run as administrator option.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-212">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="bde3d-212">-ConfigurationName</span></span>

<span data-ttu-id="bde3d-213">指定用于交互式会话的会话配置。</span><span class="sxs-lookup"><span data-stu-id="bde3d-213">Specifies the session configuration that is used for the interactive session.</span></span>

<span data-ttu-id="bde3d-214">输入会话配置的配置名称或完全限定的资源 URI。</span><span class="sxs-lookup"><span data-stu-id="bde3d-214">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="bde3d-215">如果只指定配置名称，则会预置以下架构 URI： `http://schemas.microsoft.com/powershell` 。</span><span class="sxs-lookup"><span data-stu-id="bde3d-215">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span>

<span data-ttu-id="bde3d-216">与 SSH 一起使用时，指定要在目标上使用的子系统，如 sshd_config 中所定义。</span><span class="sxs-lookup"><span data-stu-id="bde3d-216">When used with SSH, this specifies the subsystem to use on the target as defined in sshd_config.</span></span> <span data-ttu-id="bde3d-217">SSH 的默认值为 `powershell` 子系统。</span><span class="sxs-lookup"><span data-stu-id="bde3d-217">The default value for SSH is the `powershell` subsystem.</span></span>

<span data-ttu-id="bde3d-218">会话的会话配置位于远程计算机上。</span><span class="sxs-lookup"><span data-stu-id="bde3d-218">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="bde3d-219">如果远程计算机上不存在指定的会话配置，则该命令会失败。</span><span class="sxs-lookup"><span data-stu-id="bde3d-219">If the specified session configuration does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="bde3d-220">默认值为 `$PSSessionConfigurationName` 本地计算机上首选项变量的值。</span><span class="sxs-lookup"><span data-stu-id="bde3d-220">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="bde3d-221">如果未设置此首选项变量，则默认值为 Microsoft.PowerShell。</span><span class="sxs-lookup"><span data-stu-id="bde3d-221">If this preference variable is not set, the default is Microsoft.PowerShell.</span></span> <span data-ttu-id="bde3d-222">有关详细信息，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="bde3d-222">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri, VMId, VMName, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-223">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="bde3d-223">-ConnectionUri</span></span>

<span data-ttu-id="bde3d-224">指定一个 URI，该 URI 定义会话的连接终结点。</span><span class="sxs-lookup"><span data-stu-id="bde3d-224">Specifies a URI that defines the connection endpoint for the session.</span></span> <span data-ttu-id="bde3d-225">URI 必须完全限定。</span><span class="sxs-lookup"><span data-stu-id="bde3d-225">The URI must be fully qualified.</span></span> <span data-ttu-id="bde3d-226">此字符串的格式如下：</span><span class="sxs-lookup"><span data-stu-id="bde3d-226">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="bde3d-227">默认值如下：</span><span class="sxs-lookup"><span data-stu-id="bde3d-227">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="bde3d-228">如果未指定 **ConnectionURI** ，则可以使用 **UseSSL** 、 **ComputerName** 、 **Port** 和 **ApplicationName** 参数来指定 **ConnectionURI** 值。</span><span class="sxs-lookup"><span data-stu-id="bde3d-228">If you do not specify a **ConnectionURI** , you can use the **UseSSL** , **ComputerName** , **Port** , and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span>

<span data-ttu-id="bde3d-229">URI 的 Transport 段的有效值为 HTTP 和 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="bde3d-229">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="bde3d-230">如果使用传输段指定连接 URI，但未指定端口，则通过使用标准端口80（对于 HTTP 为）创建会话，对 HTTPS 使用443。</span><span class="sxs-lookup"><span data-stu-id="bde3d-230">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created by using standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="bde3d-231">若要使用 PowerShell 远程处理的默认端口，请为 HTTP 指定端口5985，为 HTTPS 指定5986。</span><span class="sxs-lookup"><span data-stu-id="bde3d-231">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="bde3d-232">如果目标计算机将连接重定向到不同的 URI，则 PowerShell 会阻止重定向，除非你在命令中使用 **AllowRedirection** 参数。</span><span class="sxs-lookup"><span data-stu-id="bde3d-232">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri
Parameter Sets: Uri
Aliases: URI, CU

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-233">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="bde3d-233">-ContainerId</span></span>

<span data-ttu-id="bde3d-234">指定容器的 ID。</span><span class="sxs-lookup"><span data-stu-id="bde3d-234">Specifies the ID of a container.</span></span>

```yaml
Type: System.String
Parameter Sets: ContainerId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-235">-Credential</span><span class="sxs-lookup"><span data-stu-id="bde3d-235">-Credential</span></span>

<span data-ttu-id="bde3d-236">指定有权执行此操作的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="bde3d-236">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="bde3d-237">默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="bde3d-237">The default is the current user.</span></span>

<span data-ttu-id="bde3d-238">键入用户名（如 **User01** 或 **Domain01\User01** ），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="bde3d-238">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="bde3d-239">如果键入用户名，系统会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="bde3d-239">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="bde3d-240">凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="bde3d-240">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="bde3d-241">有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="bde3d-241">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, Uri, VMId, VMName
Aliases:

Required: True (VMId, VMName), False (ComputerName, Uri)
Position: 1
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-242">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="bde3d-242">-EnableNetworkAccess</span></span>

<span data-ttu-id="bde3d-243">指示此 cmdlet 将交互式安全令牌添加到环回会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-243">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="bde3d-244">通过交互式令牌，你可以在环回会话中运行用于获取其他计算机中的数据的命令。</span><span class="sxs-lookup"><span data-stu-id="bde3d-244">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="bde3d-245">例如，你可以在该会话中运行用于将 XML 文件从远程计算机复制到本地计算机的命令。</span><span class="sxs-lookup"><span data-stu-id="bde3d-245">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="bde3d-246">环回会话是在同一计算机上开始并终止的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="bde3d-246">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="bde3d-247">若要创建环回会话，请省略 **ComputerName** 参数，或将其值设置为。</span><span class="sxs-lookup"><span data-stu-id="bde3d-247">To create a loopback session, omit the **ComputerName** parameter or set its value to .</span></span> <span data-ttu-id="bde3d-248"> (点) 、localhost 或本地计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="bde3d-248">(dot), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="bde3d-249">默认情况下，使用网络令牌创建环回会话，该令牌可能不提供足够的权限对远程计算机进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="bde3d-249">By default, loopback sessions are created by using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="bde3d-250">**EnableNetworkAccess** 参数仅在环回会话中有效。</span><span class="sxs-lookup"><span data-stu-id="bde3d-250">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="bde3d-251">如果在远程计算机上创建会话时使用 **EnableNetworkAccess** ，则该命令将成功，但会忽略此参数。</span><span class="sxs-lookup"><span data-stu-id="bde3d-251">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="bde3d-252">通过用于将会话凭据委派给其他计算机的 **CredSSP** 参数的 **Authentication** 值，你还可以在环回会话中进行远程访问。</span><span class="sxs-lookup"><span data-stu-id="bde3d-252">You can also allow remote access in a loopback session by using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="bde3d-253">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="bde3d-253">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-254">-HostName</span><span class="sxs-lookup"><span data-stu-id="bde3d-254">-HostName</span></span>

<span data-ttu-id="bde3d-255">指定安全外壳 (基于 SSH) 连接的计算机名称。</span><span class="sxs-lookup"><span data-stu-id="bde3d-255">Specifies a computer name for a Secure Shell (SSH) based connection.</span></span> <span data-ttu-id="bde3d-256">这与 **ComputerName** 参数类似，不同之处在于使用 SSH 而不是 Windows WinRM 建立与远程计算机的连接。</span><span class="sxs-lookup"><span data-stu-id="bde3d-256">This is similar to the **ComputerName** parameter except that the connection to the remote computer is made using SSH rather than Windows WinRM.</span></span> <span data-ttu-id="bde3d-257">此参数支持使用格式将用户名和/或端口指定为主机名称参数值的一部分 `user@hostname:port` 。</span><span class="sxs-lookup"><span data-stu-id="bde3d-257">This parameter supports specifying the user name and/or port as part of the host name parameter value using the form `user@hostname:port`.</span></span> <span data-ttu-id="bde3d-258">指定为主机名一部分的用户名和/或端口优先于 `-UserName` 和 `-Port` 参数（如果已指定）。</span><span class="sxs-lookup"><span data-stu-id="bde3d-258">The user name and/or port specified as part of the host name takes precedence over the `-UserName` and `-Port` parameters, if specified.</span></span> <span data-ttu-id="bde3d-259">这允许将多个计算机名称传递给此参数，其中某些计算机具有特定的用户名和/或端口，而另一些计算机使用和参数中的用户名和/或端口 `-UserName` `-Port` 。</span><span class="sxs-lookup"><span data-stu-id="bde3d-259">This allows passing multiple computer names to this parameter where some have specific user names and/or ports, while others use the user name and/or port from the `-UserName` and `-Port` parameters.</span></span>

<span data-ttu-id="bde3d-260">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="bde3d-260">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-261">-Id</span><span class="sxs-lookup"><span data-stu-id="bde3d-261">-Id</span></span>

<span data-ttu-id="bde3d-262">指定现有会话的 ID。</span><span class="sxs-lookup"><span data-stu-id="bde3d-262">Specifies the ID of an existing session.</span></span> <span data-ttu-id="bde3d-263">`Enter-PSSession` 为交互式会话使用指定的会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-263">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="bde3d-264">若要查找会话的 ID，请使用 `Get-PSSession` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bde3d-264">To find the ID of a session, use the `Get-PSSession` cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-265">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="bde3d-265">-InstanceId</span></span>

<span data-ttu-id="bde3d-266">指定现有会话的实例 ID。</span><span class="sxs-lookup"><span data-stu-id="bde3d-266">Specifies the instance ID of an existing session.</span></span> <span data-ttu-id="bde3d-267">`Enter-PSSession` 为交互式会话使用指定的会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-267">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="bde3d-268">实例 ID 是一个 GUID。</span><span class="sxs-lookup"><span data-stu-id="bde3d-268">The instance ID is a GUID.</span></span> <span data-ttu-id="bde3d-269">若要查找会话的实例 ID，请使用 `Get-PSSession` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bde3d-269">To find the instance ID of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="bde3d-270">你还可以使用 **Session** 、 **Name** 或 **ID** 参数来指定现有会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-270">You can also use the **Session** , **Name** , or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="bde3d-271">或者，可以使用 **ComputerName** 参数来启动临时会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-271">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

```yaml
Type: System.Guid
Parameter Sets: InstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-272">-KeyFilePath</span><span class="sxs-lookup"><span data-stu-id="bde3d-272">-KeyFilePath</span></span>

<span data-ttu-id="bde3d-273">指定安全外壳 (SSH) 用于对远程计算机上的用户进行身份验证的密钥文件路径。</span><span class="sxs-lookup"><span data-stu-id="bde3d-273">Specifies a key file path used by Secure Shell (SSH) to authenticate a user on a remote computer.</span></span>

<span data-ttu-id="bde3d-274">SSH 允许通过私有/公共密钥执行用户身份验证，作为基本密码身份验证的替代方法。</span><span class="sxs-lookup"><span data-stu-id="bde3d-274">SSH allows user authentication to be performed via private/public keys as an alternative to basic password authentication.</span></span> <span data-ttu-id="bde3d-275">如果将远程计算机配置为进行密钥身份验证，则可以使用此参数来提供用于标识用户的密钥。</span><span class="sxs-lookup"><span data-stu-id="bde3d-275">If the remote computer is configured for key authentication then this parameter can be used to provide the key that identifies the user.</span></span>

<span data-ttu-id="bde3d-276">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="bde3d-276">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-277">-Name</span><span class="sxs-lookup"><span data-stu-id="bde3d-277">-Name</span></span>

<span data-ttu-id="bde3d-278">指定现有会话的友好名称。</span><span class="sxs-lookup"><span data-stu-id="bde3d-278">Specifies the friendly name of an existing session.</span></span> <span data-ttu-id="bde3d-279">`Enter-PSSession` 为交互式会话使用指定的会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-279">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="bde3d-280">如果你指定的名称与多个会话相匹配，则该命令会失败。</span><span class="sxs-lookup"><span data-stu-id="bde3d-280">If the name that you specify matches more than one session, the command fails.</span></span> <span data-ttu-id="bde3d-281">你还可以使用 **Session** 、 **InstanceID** 或 **ID** 参数来指定现有会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-281">You can also use the **Session** , **InstanceID** , or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="bde3d-282">或者，可以使用 **ComputerName** 参数来启动临时会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-282">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

<span data-ttu-id="bde3d-283">若要为会话建立友好名称，请使用该 cmdlet 的 **name** 参数 `New-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="bde3d-283">To establish a friendly name for a session, use the **Name** parameter of the `New-PSSession` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-284">-Port</span><span class="sxs-lookup"><span data-stu-id="bde3d-284">-Port</span></span>

<span data-ttu-id="bde3d-285">指定远程计算机上用于此命令的网络端口。</span><span class="sxs-lookup"><span data-stu-id="bde3d-285">Specifies the network port on the remote computer that is used for this command.</span></span>

<span data-ttu-id="bde3d-286">在 PowerShell 6.0 中，此参数在支持安全外壳 (SSH) 连接的 **HostName** 参数集中包含。</span><span class="sxs-lookup"><span data-stu-id="bde3d-286">In PowerShell 6.0 this parameter was inlcuded in the **HostName** parameter set which supports Secure Shell (SSH) connections.</span></span>

<span data-ttu-id="bde3d-287">**WinRM (ComputerName 参数集)**</span><span class="sxs-lookup"><span data-stu-id="bde3d-287">**WinRM (ComputerName parameter set)**</span></span>

<span data-ttu-id="bde3d-288">若要连接到一台远程计算机，则必须在该连接所用的端口上侦听远程计算机。</span><span class="sxs-lookup"><span data-stu-id="bde3d-288">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="bde3d-289">默认端口为 5985（HTTP 的 WinRM 端口）和 5986（HTTPS 的 WinRM 端口）。</span><span class="sxs-lookup"><span data-stu-id="bde3d-289">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="bde3d-290">使用备用端口之前，你必须在远程计算机上配置 WinRM 侦听器，才能在该端口上进行侦听。</span><span class="sxs-lookup"><span data-stu-id="bde3d-290">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="bde3d-291">使用以下命令配置侦听器：</span><span class="sxs-lookup"><span data-stu-id="bde3d-291">Use the following commands to configure the listener:</span></span>

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="bde3d-292">除非必要，否则不要使用 **Port** 参数。</span><span class="sxs-lookup"><span data-stu-id="bde3d-292">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="bde3d-293">命令中的端口设置适用于运行该命令的所有计算机或会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-293">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="bde3d-294">备用端口设置可能会阻止在所有计算机上运行该命令。</span><span class="sxs-lookup"><span data-stu-id="bde3d-294">An alternate port setting might prevent the command from running on all computers.</span></span>

<span data-ttu-id="bde3d-295">**SSH (主机名参数集)**</span><span class="sxs-lookup"><span data-stu-id="bde3d-295">**SSH (HostName parameter set)**</span></span>

<span data-ttu-id="bde3d-296">若要连接到远程计算机，远程计算机必须配置有 SSH 服务 (SSHD) ，并且必须侦听连接使用的端口。</span><span class="sxs-lookup"><span data-stu-id="bde3d-296">To connect to a remote computer, the remote computer must be configured with the SSH service (SSHD) and must be listening on the port that the connection uses.</span></span> <span data-ttu-id="bde3d-297">SSH 的默认端口是22。</span><span class="sxs-lookup"><span data-stu-id="bde3d-297">The default port for SSH is 22.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-298">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="bde3d-298">-RunAsAdministrator</span></span>

<span data-ttu-id="bde3d-299">指示 **PSSession** 以管理员身份运行。</span><span class="sxs-lookup"><span data-stu-id="bde3d-299">Indicates that the **PSSession** runs as administrator.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-300">-Session</span><span class="sxs-lookup"><span data-stu-id="bde3d-300">-Session</span></span>

<span data-ttu-id="bde3d-301">指定要用于交互式会话 ( **PSSession** ) 的 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-301">Specifies a PowerShell session ( **PSSession** ) to use for the interactive session.</span></span> <span data-ttu-id="bde3d-302">此参数获取一个会话对象。</span><span class="sxs-lookup"><span data-stu-id="bde3d-302">This parameter takes a session object.</span></span> <span data-ttu-id="bde3d-303">你还可以使用 **Name** 、 **InstanceID** 或 **ID** 参数来指定 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="bde3d-303">You can also use the **Name** , **InstanceID** , or **ID** parameters to specify a **PSSession** .</span></span>

<span data-ttu-id="bde3d-304">输入包含 session 对象的变量或可创建或获取会话对象的命令，例如 `New-PSSession` 或 `Get-PSSession` 命令。</span><span class="sxs-lookup"><span data-stu-id="bde3d-304">Enter a variable that contains a session object or a command that creates or gets a session object, such as a `New-PSSession` or `Get-PSSession` command.</span></span> <span data-ttu-id="bde3d-305">还可以通过管道将会话对象传递给 `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="bde3d-305">You can also pipe a session object to `Enter-PSSession`.</span></span> <span data-ttu-id="bde3d-306">使用此参数只能提交一个 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="bde3d-306">You can submit only one **PSSession** by using this parameter.</span></span> <span data-ttu-id="bde3d-307">如果输入包含多个 **PSSession** 的变量，则该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="bde3d-307">If you enter a variable that contains more than one **PSSession** , the command fails.</span></span>

<span data-ttu-id="bde3d-308">当你使用 `Exit-PSSession` 或 **EXIT** 关键字时，交互式会话将结束，但你创建的 **PSSession** 仍处于打开状态并可供使用。</span><span class="sxs-lookup"><span data-stu-id="bde3d-308">When you use `Exit-PSSession` or the **EXIT** keyword, the interactive session ends, but the **PSSession** that you created remains open and available for use.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-309">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="bde3d-309">-SessionOption</span></span>

<span data-ttu-id="bde3d-310">为该会话设置高级选项。</span><span class="sxs-lookup"><span data-stu-id="bde3d-310">Sets advanced options for the session.</span></span> <span data-ttu-id="bde3d-311">输入 **SessionOption** 对象（例如使用 cmdlet 创建的对象） `New-PSSessionOption` ，或输入一个哈希表，其中的键是会话选项名称，而值是会话选项的值。</span><span class="sxs-lookup"><span data-stu-id="bde3d-311">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="bde3d-312">选项的默认值取决于 `$PSSessionOption` 首选项变量的值（如果已设置）。</span><span class="sxs-lookup"><span data-stu-id="bde3d-312">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="bde3d-313">否则，通过在会话配置中设置的选项创建默认值。</span><span class="sxs-lookup"><span data-stu-id="bde3d-313">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="bde3d-314">会话选项值优先于在 `$PSSessionOption` 首选项变量和会话配置中设置的会话的默认值。</span><span class="sxs-lookup"><span data-stu-id="bde3d-314">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="bde3d-315">但是，它们不优先于在会话配置中设置的最大值、配额或限制。</span><span class="sxs-lookup"><span data-stu-id="bde3d-315">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="bde3d-316">有关会话选项（包括默认值）的说明，请参阅 `New-PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="bde3d-316">For a description of the session options, including the default values, see `New-PSSessionOption`.</span></span>
<span data-ttu-id="bde3d-317">有关 `$PSSessionOption` 首选项变量的信息，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="bde3d-317">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="bde3d-318">有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="bde3d-318">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-319">-SSHTransport</span><span class="sxs-lookup"><span data-stu-id="bde3d-319">-SSHTransport</span></span>

<span data-ttu-id="bde3d-320">指示使用安全外壳 (SSH) 建立远程连接。</span><span class="sxs-lookup"><span data-stu-id="bde3d-320">Indicates that the remote connection is established using Secure Shell (SSH).</span></span>

<span data-ttu-id="bde3d-321">默认情况下，PowerShell 使用 Windows WinRM 连接到远程计算机。</span><span class="sxs-lookup"><span data-stu-id="bde3d-321">By default PowerShell uses Windows WinRM to connect to a remote computer.</span></span> <span data-ttu-id="bde3d-322">此开关强制 PowerShell 使用 HostName 参数集建立基于 SSH 的远程连接。</span><span class="sxs-lookup"><span data-stu-id="bde3d-322">This switch forces PowerShell to use the HostName parameter set for establishing an SSH based remote connection.</span></span>

<span data-ttu-id="bde3d-323">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="bde3d-323">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-324">-子系统</span><span class="sxs-lookup"><span data-stu-id="bde3d-324">-Subsystem</span></span>

<span data-ttu-id="bde3d-325">指定用于新的 **PSSession** 的 SSH 子系统。</span><span class="sxs-lookup"><span data-stu-id="bde3d-325">Specifies the SSH subsystem used for the new **PSSession** .</span></span>

<span data-ttu-id="bde3d-326">此项指定要在目标上使用的子系统（如 sshd_config 中所定义）。</span><span class="sxs-lookup"><span data-stu-id="bde3d-326">This specifies the subsystem to use on the target as defined in sshd_config.</span></span> <span data-ttu-id="bde3d-327">子系统使用预定义参数启动特定版本的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="bde3d-327">The subsystem starts a specific version of PowerShell with predefined parameters.</span></span> <span data-ttu-id="bde3d-328">如果远程计算机上不存在指定的子系统，则该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="bde3d-328">If the specified subsystem does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="bde3d-329">如果未使用此参数，则默认值为 "powershell" 子系统。</span><span class="sxs-lookup"><span data-stu-id="bde3d-329">If this parameter is not used, the default is the 'powershell' subsystem.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: powershell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-330">-UserName</span><span class="sxs-lookup"><span data-stu-id="bde3d-330">-UserName</span></span>

<span data-ttu-id="bde3d-331">指定用于在远程计算机上创建会话的帐户的用户名。</span><span class="sxs-lookup"><span data-stu-id="bde3d-331">Specifies the user name for the account used to create a session on the remote computer.</span></span> <span data-ttu-id="bde3d-332">用户身份验证方法取决于如何在远程计算机上配置 (SSH) 安全外壳。</span><span class="sxs-lookup"><span data-stu-id="bde3d-332">User authentication method will depend on how Secure Shell (SSH) is configured on the remote computer.</span></span>

<span data-ttu-id="bde3d-333">如果 SSH 配置了基本密码身份验证，则系统将提示你输入用户密码。</span><span class="sxs-lookup"><span data-stu-id="bde3d-333">If SSH is configured for basic password authentication then you will be prompted for the user password.</span></span>

<span data-ttu-id="bde3d-334">如果 SSH 配置为基于密钥的用户身份验证，则可以通过 **KeyFilePath** 参数提供密钥文件路径，并且不会出现密码提示。</span><span class="sxs-lookup"><span data-stu-id="bde3d-334">If SSH is configured for key based user authentication then a key file path can be provided via the **KeyFilePath** parameter and no password prompt will occur.</span></span> <span data-ttu-id="bde3d-335">请注意，如果客户端用户密钥文件位于 SSH 已知位置，则基于密钥的身份验证不需要 **KeyFilePath** 参数，并且将根据用户名自动进行用户身份验证。</span><span class="sxs-lookup"><span data-stu-id="bde3d-335">Note that if the client user key file is located in an SSH known location then the **KeyFilePath** parameter is not needed for key based authentication, and user authentication will occur automatically based on the user name.</span></span> <span data-ttu-id="bde3d-336">有关详细信息，请参阅 SSH 文档关于基于密钥的用户身份验证。</span><span class="sxs-lookup"><span data-stu-id="bde3d-336">See SSH documentation about key based user authentication for more information.</span></span>

<span data-ttu-id="bde3d-337">这不是必需的参数。</span><span class="sxs-lookup"><span data-stu-id="bde3d-337">This is not a required parameter.</span></span> <span data-ttu-id="bde3d-338">如果未指定 **用户名** 参数，则将使用当前登录的用户名作为连接。</span><span class="sxs-lookup"><span data-stu-id="bde3d-338">If no **UserName** parameter is specified then the current log on user name is used for the connection.</span></span>

<span data-ttu-id="bde3d-339">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="bde3d-339">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-340">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="bde3d-340">-UseSSL</span></span>

<span data-ttu-id="bde3d-341">指示此 cmdlet 使用安全套接字层 (SSL) 协议来建立与远程计算机的连接。</span><span class="sxs-lookup"><span data-stu-id="bde3d-341">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="bde3d-342">默认情况下，不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="bde3d-342">By default, SSL is not used.</span></span>

<span data-ttu-id="bde3d-343">WS-Management 加密通过网络传输的所有 PowerShell 内容。</span><span class="sxs-lookup"><span data-stu-id="bde3d-343">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="bde3d-344">**UseSSL** 参数是一种额外的保护措施，它通过 HTTPS 连接而不是 HTTP 连接来发送数据。</span><span class="sxs-lookup"><span data-stu-id="bde3d-344">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="bde3d-345">如果使用此参数，但 SSL 在用于此命令的端口上不可用，则该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="bde3d-345">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-346">-VMId</span><span class="sxs-lookup"><span data-stu-id="bde3d-346">-VMId</span></span>

<span data-ttu-id="bde3d-347">指定虚拟机的 ID。</span><span class="sxs-lookup"><span data-stu-id="bde3d-347">Specifies the ID of a virtual machine.</span></span>

```yaml
Type: System.Guid
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-348">-VMName</span><span class="sxs-lookup"><span data-stu-id="bde3d-348">-VMName</span></span>

<span data-ttu-id="bde3d-349">指定虚拟机的名称。</span><span class="sxs-lookup"><span data-stu-id="bde3d-349">Specifies the name of a virtual machine.</span></span>

```yaml
Type: System.String
Parameter Sets: VMName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bde3d-350">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bde3d-350">CommonParameters</span></span>

<span data-ttu-id="bde3d-351">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="bde3d-351">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bde3d-352">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="bde3d-352">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bde3d-353">输入</span><span class="sxs-lookup"><span data-stu-id="bde3d-353">INPUTS</span></span>

### <span data-ttu-id="bde3d-354">System.string、System.web. PSSession。</span><span class="sxs-lookup"><span data-stu-id="bde3d-354">System.String, System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="bde3d-355">你可以通过管道将计算机名称、字符串或会话对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bde3d-355">You can pipe a computer name, as a string, or a session object to this cmdlet.</span></span>

## <span data-ttu-id="bde3d-356">输出</span><span class="sxs-lookup"><span data-stu-id="bde3d-356">OUTPUTS</span></span>

### <span data-ttu-id="bde3d-357">无</span><span class="sxs-lookup"><span data-stu-id="bde3d-357">None</span></span>

<span data-ttu-id="bde3d-358">该 cmdlet 不返回任何输出。</span><span class="sxs-lookup"><span data-stu-id="bde3d-358">The cmdlet does not return any output.</span></span>

## <span data-ttu-id="bde3d-359">注释</span><span class="sxs-lookup"><span data-stu-id="bde3d-359">NOTES</span></span>

<span data-ttu-id="bde3d-360">若要连接到远程计算机，你必须是该远程计算机上 Administrators 组的成员。</span><span class="sxs-lookup"><span data-stu-id="bde3d-360">To connect to a remote computer, you must be a member of the Administrators group on the remote computer.</span></span> <span data-ttu-id="bde3d-361">若要在本地计算机上启动交互式会话，你必须使用 "以 **管理员身份运行** " 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="bde3d-361">To start an interactive session on the local computer, you must start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="bde3d-362">使用时 `Enter-PSSession` ，远程计算机上的用户配置文件用于交互会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-362">When you use `Enter-PSSession`, your user profile on the remote computer is used for the interactive session.</span></span> <span data-ttu-id="bde3d-363">远程用户配置文件中的命令（包括用于添加 PowerShell 模块和更改命令提示符的命令）将在显示远程提示之前运行。</span><span class="sxs-lookup"><span data-stu-id="bde3d-363">The commands in the remote user profile, including commands to add PowerShell modules and to change the command prompt, run before the remote prompt is displayed.</span></span>

<span data-ttu-id="bde3d-364">`Enter-PSSession` 为交互式会话使用本地计算机上的 UI 区域性设置。</span><span class="sxs-lookup"><span data-stu-id="bde3d-364">`Enter-PSSession` uses the UI culture setting on the local computer for the interactive session.</span></span> <span data-ttu-id="bde3d-365">若要查找本地 UI 区域性，请使用 `$UICulture` 自动变量。</span><span class="sxs-lookup"><span data-stu-id="bde3d-365">To find the local UI culture, use the `$UICulture` automatic variable.</span></span>

<span data-ttu-id="bde3d-366">`Enter-PSSession` 需要 `Get-Command` 、 `Out-Default` 和 `Exit-PSSession` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bde3d-366">`Enter-PSSession` requires the `Get-Command`, `Out-Default`, and `Exit-PSSession` cmdlets.</span></span> <span data-ttu-id="bde3d-367">如果远程计算机上的会话配置中未包含这些 cmdlet，则命令将 `Enter-PSSession` 失败。</span><span class="sxs-lookup"><span data-stu-id="bde3d-367">If these cmdlets are not included in the session configuration on the remote computer, the `Enter-PSSession` commands fails.</span></span>

<span data-ttu-id="bde3d-368">不同 `Invoke-Command` 于，它在将命令发送到远程计算机之前对其进行分析和解释， `Enter-PSSession` 将命令直接发送到远程计算机，而不会进行解释。</span><span class="sxs-lookup"><span data-stu-id="bde3d-368">Unlike `Invoke-Command`, which parses and interprets the commands before it sends them to the remote computer, `Enter-PSSession` sends the commands directly to the remote computer without interpretation.</span></span>

<span data-ttu-id="bde3d-369">如果要输入的会话正忙于处理命令，则 PowerShell 对命令的响应可能会有延迟 `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="bde3d-369">If the session you want to enter is busy processing a command, there might be a delay before PowerShell responds to the `Enter-PSSession` command.</span></span> <span data-ttu-id="bde3d-370">会话可用后，就会立即连接。</span><span class="sxs-lookup"><span data-stu-id="bde3d-370">You are connected as soon as the session is available.</span></span> <span data-ttu-id="bde3d-371">若要取消 `Enter-PSSession` 命令，请按<kbd>CTRL</kbd> + <kbd>C</kbd>。</span><span class="sxs-lookup"><span data-stu-id="bde3d-371">To cancel the `Enter-PSSession` command, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

<span data-ttu-id="bde3d-372">**主机名** 参数集包括从 PowerShell 6.0 开始。</span><span class="sxs-lookup"><span data-stu-id="bde3d-372">The **HostName** parameter set was included starting with PowerShell 6.0.</span></span> <span data-ttu-id="bde3d-373">添加它是为了提供基于 (SSH) 安全外壳的 PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="bde3d-373">It was added to provide PowerShell remoting based on Secure Shell (SSH).</span></span> <span data-ttu-id="bde3d-374">SSH 和 PowerShell 在多个平台上都受支持 (Windows、Linux、macOS) ，PowerShell 远程处理将在安装和配置 PowerShell 和 SSH 的这些平台上运行。</span><span class="sxs-lookup"><span data-stu-id="bde3d-374">Both SSH and PowerShell are supported on multiple platforms (Windows, Linux, macOS) and PowerShell remoting will work over these platforms where PowerShell and SSH are installed and configured.</span></span> <span data-ttu-id="bde3d-375">这不同于以前仅限 Windows 的基于 WinRM 的远程处理，并且很多 WinRM 特定功能和限制不适用。</span><span class="sxs-lookup"><span data-stu-id="bde3d-375">This is separate from the previous Windows only remoting that is based on WinRM and much of the WinRM specific features and limitations do not apply.</span></span> <span data-ttu-id="bde3d-376">例如，目前不支持基于 WinRM 的配额、会话选项、自定义终结点配置和断开/重新连接功能。</span><span class="sxs-lookup"><span data-stu-id="bde3d-376">For example, WinRM based quotas, session options, custom endpoint configuration, and disconnect/reconnect features are currently not supported.</span></span> <span data-ttu-id="bde3d-377">有关如何设置 PowerShell SSH 远程处理的详细信息，请参阅 [通过 SSH 进行 Powershell 远程处理](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)。</span><span class="sxs-lookup"><span data-stu-id="bde3d-377">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

<span data-ttu-id="bde3d-378">在 PowerShell 7.1 之前，通过 SSH 进行远程处理不支持第二个跃点的远程会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-378">Prior to PowerShell 7.1, remoting over SSH did not support second-hop remote sessions.</span></span> <span data-ttu-id="bde3d-379">此功能仅限于使用 WinRM 的会话。</span><span class="sxs-lookup"><span data-stu-id="bde3d-379">This capability was limited to sessions using WinRM.</span></span> <span data-ttu-id="bde3d-380">PowerShell 7.1 允许 `Enter-PSSession` 和 `Enter-PSHostProcess` 在任何交互式远程会话中工作。</span><span class="sxs-lookup"><span data-stu-id="bde3d-380">PowerShell 7.1 allows `Enter-PSSession` and `Enter-PSHostProcess` to work from within any interactive remote session.</span></span>

## <span data-ttu-id="bde3d-381">相关链接</span><span class="sxs-lookup"><span data-stu-id="bde3d-381">RELATED LINKS</span></span>

[<span data-ttu-id="bde3d-382">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="bde3d-382">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="bde3d-383">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="bde3d-383">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="bde3d-384">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="bde3d-384">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="bde3d-385">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="bde3d-385">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="bde3d-386">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="bde3d-386">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="bde3d-387">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="bde3d-387">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="bde3d-388">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="bde3d-388">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="bde3d-389">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="bde3d-389">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="bde3d-390">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="bde3d-390">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="bde3d-391">about_Remote</span><span class="sxs-lookup"><span data-stu-id="bde3d-391">about_Remote</span></span>](About/about_Remote.md)
