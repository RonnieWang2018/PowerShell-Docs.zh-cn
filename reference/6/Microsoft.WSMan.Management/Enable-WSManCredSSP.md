---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 08/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/enable-wsmancredssp?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManCredSSP
ms.openlocfilehash: 48429114a8e174351f4323acb501f89261e4a40a
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "93199078"
---
# <span data-ttu-id="e87cd-103">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="e87cd-103">Enable-WSManCredSSP</span></span>

## <span data-ttu-id="e87cd-104">摘要</span><span class="sxs-lookup"><span data-stu-id="e87cd-104">SYNOPSIS</span></span>
<span data-ttu-id="e87cd-105">在计算机上启用凭据安全支持提供程序 (CredSSP) 身份验证。</span><span class="sxs-lookup"><span data-stu-id="e87cd-105">Enables Credential Security Support Provider (CredSSP) authentication on a computer.</span></span>

## <span data-ttu-id="e87cd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e87cd-106">SYNTAX</span></span>

### <span data-ttu-id="e87cd-107">全部</span><span class="sxs-lookup"><span data-stu-id="e87cd-107">All</span></span>

```
Enable-WSManCredSSP [[-DelegateComputer] <String[]>] [-Force] [-Role] <String> [<CommonParameters>]
```

## <span data-ttu-id="e87cd-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e87cd-108">DESCRIPTION</span></span>

<span data-ttu-id="e87cd-109">`Enable-WSManCredSSP`Cmdlet 可在客户端或服务器计算机上启用 CredSSP 身份验证。</span><span class="sxs-lookup"><span data-stu-id="e87cd-109">The `Enable-WSManCredSSP` cmdlet enables CredSSP authentication on a client or on a server computer.</span></span>
<span data-ttu-id="e87cd-110">当使用 CredSSP 身份验证时，用户凭据将传递给要进行身份验证的远程计算机。</span><span class="sxs-lookup"><span data-stu-id="e87cd-110">When CredSSP authentication is used, the user credentials are passed to a remote computer to be authenticated.</span></span> <span data-ttu-id="e87cd-111">此类型的身份验证旨在用于从一个远程会话创建另一个远程会话的命令。</span><span class="sxs-lookup"><span data-stu-id="e87cd-111">This type of authentication is designed for commands that create a remote session from another remote session.</span></span> <span data-ttu-id="e87cd-112">例如，若要在远程计算机上运行后台作业，可以使用此类型的身份验证。</span><span class="sxs-lookup"><span data-stu-id="e87cd-112">For example, if you want to run a background job on a remote computer, use this kind of authentication.</span></span>

<span data-ttu-id="e87cd-113">`Enable-WSManCredSSP` 可以在 **客户端** 或 **服务器** 上启用 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="e87cd-113">`Enable-WSManCredSSP` can enable CredSSP on a **Client** or a **Server** .</span></span> <span data-ttu-id="e87cd-114">若要在客户端上启用 CredSSP，请在 **Role** 参数中指定 **client** 。</span><span class="sxs-lookup"><span data-stu-id="e87cd-114">To enable CredSSP on a client, specify **Client** in the **Role** parameter.</span></span> <span data-ttu-id="e87cd-115">客户端在实现服务器身份验证时将显式凭据委派给服务器。</span><span class="sxs-lookup"><span data-stu-id="e87cd-115">Clients delegate explicit credentials to a server when server authentication is achieved.</span></span> <span data-ttu-id="e87cd-116">若要在服务器上启用 CredSSP，请在 **Role** 参数中指定 **server** 。</span><span class="sxs-lookup"><span data-stu-id="e87cd-116">To enable CredSSP on a server, specify **Server** in the **Role** parameter.</span></span> <span data-ttu-id="e87cd-117">服务器充当客户端的代理。</span><span class="sxs-lookup"><span data-stu-id="e87cd-117">A server acts as a delegate for clients.</span></span> <span data-ttu-id="e87cd-118">有关更多详细信息，请参阅参数部分中的 **Role** 。</span><span class="sxs-lookup"><span data-stu-id="e87cd-118">For more details, see **Role** in the Parameters section.</span></span>

> [!CAUTION]
> <span data-ttu-id="e87cd-119">CredSSP 身份验证将用户凭据从本地计算机委派给远程计算机。</span><span class="sxs-lookup"><span data-stu-id="e87cd-119">CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span> <span data-ttu-id="e87cd-120">此做法增加了远程操作的安全风险。</span><span class="sxs-lookup"><span data-stu-id="e87cd-120">This practice increases the security risk of the remote operation.</span></span> <span data-ttu-id="e87cd-121">如果远程计算机的安全受到威胁，则在向该计算机传递凭据时，可使用这些凭据来控制网络会话。</span><span class="sxs-lookup"><span data-stu-id="e87cd-121">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="e87cd-122">示例</span><span class="sxs-lookup"><span data-stu-id="e87cd-122">EXAMPLES</span></span>

### <span data-ttu-id="e87cd-123">示例 1：委派客户端凭据</span><span class="sxs-lookup"><span data-stu-id="e87cd-123">Example 1: Delegate client credentials</span></span>

<span data-ttu-id="e87cd-124">此示例允许使用完全限定的域名将客户端凭据委派给计算机。</span><span class="sxs-lookup"><span data-stu-id="e87cd-124">This example allows the client credentials to be delegated to a computer by using the fully qualified domain name.</span></span>

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "Server02.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### <span data-ttu-id="e87cd-125">示例 2：将客户端凭据委派给域中的所有计算机</span><span class="sxs-lookup"><span data-stu-id="e87cd-125">Example 2: Delegate client credentials to all computers in a domain</span></span>

<span data-ttu-id="e87cd-126">此示例允许将客户端凭据委派给 **fabrikam.com** 域中的所有计算机。</span><span class="sxs-lookup"><span data-stu-id="e87cd-126">This example allows the client credentials to be delegated to all the computers in the **fabrikam.com** domain.</span></span> <span data-ttu-id="e87cd-127">星号 (`*`) 通配符指定所有计算机。</span><span class="sxs-lookup"><span data-stu-id="e87cd-127">The asterisk (`*`) wildcard specifies all computers.</span></span>

> [!NOTE]
> <span data-ttu-id="e87cd-128">使用带有 **DelegateComputer** 参数的通配符可在超过所需的计算机上启用 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="e87cd-128">Using wildcards with the **DelegateComputer** parameter can enable CredSSP on more computers than necessary.</span></span>

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "*.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### <span data-ttu-id="e87cd-129">示例 3：将客户端凭据委派给多台计算机</span><span class="sxs-lookup"><span data-stu-id="e87cd-129">Example 3: Delegate client credentials to multiple computers</span></span>

<span data-ttu-id="e87cd-130">此示例允许将客户端凭据委派给多台计算机。</span><span class="sxs-lookup"><span data-stu-id="e87cd-130">This example allows the client credentials to be delegated to multiple computers.</span></span>

```powershell
$servers = "server02.fabrikam.com", "server03.fabrikam.com", "server04.fabrikam.com"
Enable-WSManCredSSP -Role "Client" -DelegateComputer $servers
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

<span data-ttu-id="e87cd-131">`$servers`变量包含服务器名称的列表。</span><span class="sxs-lookup"><span data-stu-id="e87cd-131">The `$servers` variable contains a list of server names.</span></span> <span data-ttu-id="e87cd-132">`Enable-WSManCredSSP` 使用 **Role** 参数指定 **客户端** 角色。</span><span class="sxs-lookup"><span data-stu-id="e87cd-132">`Enable-WSManCredSSP` uses the **Role** parameter to specify the **Client** role.</span></span> <span data-ttu-id="e87cd-133">**DelegateComputer** 从变量获取计算机名称 `$servers` 。</span><span class="sxs-lookup"><span data-stu-id="e87cd-133">The **DelegateComputer** gets the computer names from the `$servers` variable.</span></span>

### <span data-ttu-id="e87cd-134">示例 4：允许计算机充当代理</span><span class="sxs-lookup"><span data-stu-id="e87cd-134">Example 4: Allow a computer to act as a delegate</span></span>

<span data-ttu-id="e87cd-135">此示例允许计算机充当另一台计算机的委托。</span><span class="sxs-lookup"><span data-stu-id="e87cd-135">This example allows a computer to act as a delegate for another.</span></span> <span data-ttu-id="e87cd-136">`Enable-WSManCredSSP`前面的示例中所示的 cmdlet 仅在客户端上启用 CredSSP 身份验证，并指定可代表其执行操作的远程计算机。</span><span class="sxs-lookup"><span data-stu-id="e87cd-136">The `Enable-WSManCredSSP` cmdlet, shown in the earlier examples, only enables CredSSP authentication on the client, and specifies the remote computers that can act on its behalf.</span></span> <span data-ttu-id="e87cd-137">为了使远程计算机充当客户端的代理，WSMan 的 **Service** 节点中的 CredSSP 项必须设置为 true。</span><span class="sxs-lookup"><span data-stu-id="e87cd-137">In order for the remote computer to act as a delegate for the client, the CredSSP item in the **Service** node of WSMan must be set to true.</span></span> <span data-ttu-id="e87cd-138">此示例将 WSMan 的 **Service** 节点中的 CredSSP 项设置为 true。</span><span class="sxs-lookup"><span data-stu-id="e87cd-138">This example sets the CredSSP item in the **Service** node of WSMan to true.</span></span>

```powershell
Enable-WSManCredSSP -Role "Server"
```

### <span data-ttu-id="e87cd-139">示例 5：允许计算机通过使用 Set-Item 充当代理</span><span class="sxs-lookup"><span data-stu-id="e87cd-139">Example 5: Allow a computer to act as a delegate by using Set-Item</span></span>

<span data-ttu-id="e87cd-140">此示例允许一台计算机充当另一台计算机的代理。</span><span class="sxs-lookup"><span data-stu-id="e87cd-140">This example allows a computer to act as a delegate for another computer.</span></span> <span data-ttu-id="e87cd-141">`Enable-WSManCredSSP`前面的示例中所示的命令仅在客户端计算机上启用 CredSSP 身份验证，并指定可代表客户端计算机执行的远程计算机。</span><span class="sxs-lookup"><span data-stu-id="e87cd-141">The `Enable-WSManCredSSP` commands, shown in the earlier examples, enable CredSSP authentication only on the client computer, and they specify the remote computers that can act on behalf of the client computer.</span></span> <span data-ttu-id="e87cd-142">若要使远程计算机充当客户端计算机的代理，WSMan 提供程序的 Service 目录中的 CredSSP 项必须设置为 true。</span><span class="sxs-lookup"><span data-stu-id="e87cd-142">For the remote computer to act as a delegate for the client computer, the CredSSP item in the Service directory of the WSMan provider must be set to true.</span></span>

```powershell
Connect-WSMan -ComputerName "server02"
Set-Item -Path "WSMan:\server02\service\auth\credSSP" -Value $True
```

<span data-ttu-id="e87cd-143">`Connect-WSMan` 创建与远程计算机的连接 server02。</span><span class="sxs-lookup"><span data-stu-id="e87cd-143">`Connect-WSMan` creates a connection to the remote computer, server02.</span></span> <span data-ttu-id="e87cd-144">`Set-Item` 使用 **Path** 参数指定 **WSMan** 提供程序的位置。</span><span class="sxs-lookup"><span data-stu-id="e87cd-144">`Set-Item` uses the **Path** parameter to specify the **WSMan** provider's location.</span></span> <span data-ttu-id="e87cd-145">**Value** 参数将 **服务** 设置设置为 true。</span><span class="sxs-lookup"><span data-stu-id="e87cd-145">The **Value** parameter sets the **Service** setting to true.</span></span>

## <span data-ttu-id="e87cd-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e87cd-146">PARAMETERS</span></span>

### <span data-ttu-id="e87cd-147">-DelegateComputer</span><span class="sxs-lookup"><span data-stu-id="e87cd-147">-DelegateComputer</span></span>

<span data-ttu-id="e87cd-148">指定要向其委派客户端凭据的服务器。</span><span class="sxs-lookup"><span data-stu-id="e87cd-148">Specifies servers to which client credentials are delegated.</span></span> <span data-ttu-id="e87cd-149">最佳做法是使用完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="e87cd-149">The best practice is to use fully qualified domain names.</span></span>

<span data-ttu-id="e87cd-150">允许使用通配符，但可以在需要的计算机上启用 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="e87cd-150">Wildcards are accepted, but can enable CredSSP on more computers than necessary.</span></span>

<span data-ttu-id="e87cd-151">如果 **Role** 参数为 **Client** ，则必须指定此参数。</span><span class="sxs-lookup"><span data-stu-id="e87cd-151">If the **Role** parameter is **Client** , you must specify this parameter.</span></span> <span data-ttu-id="e87cd-152">如果 **Role** 是 **Server** ，请不要指定此参数。</span><span class="sxs-lookup"><span data-stu-id="e87cd-152">If **Role** is **Server** , don't specify this parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="e87cd-153">-Force</span><span class="sxs-lookup"><span data-stu-id="e87cd-153">-Force</span></span>

<span data-ttu-id="e87cd-154">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="e87cd-154">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="e87cd-155">-Role</span><span class="sxs-lookup"><span data-stu-id="e87cd-155">-Role</span></span>

<span data-ttu-id="e87cd-156">指定将 CredSSP 启用为客户端还是服务器。</span><span class="sxs-lookup"><span data-stu-id="e87cd-156">Specifies whether to enable CredSSP as a client or as a server.</span></span> <span data-ttu-id="e87cd-157">此参数的可接受值为： **Client** 和 **Server** 。</span><span class="sxs-lookup"><span data-stu-id="e87cd-157">The acceptable values for this parameter are: **Client** and **Server** .</span></span>

<span data-ttu-id="e87cd-158">如果指定 " **客户端** "，则会执行以下操作。</span><span class="sxs-lookup"><span data-stu-id="e87cd-158">If you specify **Client** , the following actions are performed.</span></span> <span data-ttu-id="e87cd-159">这些设置允许客户端在实现服务器身份验证时将显式凭据委派给服务器。</span><span class="sxs-lookup"><span data-stu-id="e87cd-159">These settings allow the client to delegate explicit credentials to a server when server authentication is achieved.</span></span>

- <span data-ttu-id="e87cd-160">启用客户端上的 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="e87cd-160">Enables CredSSP on the client.</span></span>
- <span data-ttu-id="e87cd-161">将 WS-Management 设置设置 `\<localhost|computername\>\Client\Auth\CredSSP` 为 true。</span><span class="sxs-lookup"><span data-stu-id="e87cd-161">Sets the WS-Management setting `\<localhost|computername\>\Client\Auth\CredSSP` to true.</span></span>
- <span data-ttu-id="e87cd-162">将 Windows CredSSP 策略 **AllowFreshCredentials** 设置为客户端上的 **WSMan/Delegate** 。</span><span class="sxs-lookup"><span data-stu-id="e87cd-162">Sets the Windows CredSSP policy **AllowFreshCredentials** to **WSMan/Delegate** on the client.</span></span>

<span data-ttu-id="e87cd-163">如果指定 **服务器** ，则执行以下操作。</span><span class="sxs-lookup"><span data-stu-id="e87cd-163">If you specify **Server** , the following actions are performed.</span></span> <span data-ttu-id="e87cd-164">此策略设置允许服务器充当客户端的代理。</span><span class="sxs-lookup"><span data-stu-id="e87cd-164">This policy setting allows the server to act as a delegate for clients.</span></span>

- <span data-ttu-id="e87cd-165">启用服务器上的 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="e87cd-165">Enables CredSSP on the server.</span></span>
- <span data-ttu-id="e87cd-166">将 WS-Management 设置设置 `\<localhost|computername\>\Service\Auth\CredSSP` 为 true。</span><span class="sxs-lookup"><span data-stu-id="e87cd-166">Sets the WS-Management setting `\<localhost|computername\>\Service\Auth\CredSSP` to true.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Client, Server

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e87cd-167">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e87cd-167">CommonParameters</span></span>

<span data-ttu-id="e87cd-168">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="e87cd-168">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e87cd-169">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="e87cd-169">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e87cd-170">输入</span><span class="sxs-lookup"><span data-stu-id="e87cd-170">INPUTS</span></span>

### <span data-ttu-id="e87cd-171">无</span><span class="sxs-lookup"><span data-stu-id="e87cd-171">None</span></span>

<span data-ttu-id="e87cd-172">此 cmdlet 不接受任何输入。</span><span class="sxs-lookup"><span data-stu-id="e87cd-172">This cmdlet doesn't accept any input.</span></span>

## <span data-ttu-id="e87cd-173">输出</span><span class="sxs-lookup"><span data-stu-id="e87cd-173">OUTPUTS</span></span>

### <span data-ttu-id="e87cd-174">System.Xml.XmlElement</span><span class="sxs-lookup"><span data-stu-id="e87cd-174">System.Xml.XmlElement</span></span>

<span data-ttu-id="e87cd-175">如果成功启用 CredSSP 身份验证，此 cmdlet 将生成一个 **XMLElement** 对象。</span><span class="sxs-lookup"><span data-stu-id="e87cd-175">If CredSSP authentication is successfully enabled, this cmdlet generates an **XMLElement** object.</span></span>

## <span data-ttu-id="e87cd-176">注释</span><span class="sxs-lookup"><span data-stu-id="e87cd-176">NOTES</span></span>

<span data-ttu-id="e87cd-177">若要禁用 CredSSP 身份验证，请使用 `Disable-WSManCredSSP` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e87cd-177">To disable CredSSP authentication, use the `Disable-WSManCredSSP` cmdlet.</span></span>

## <span data-ttu-id="e87cd-178">相关链接</span><span class="sxs-lookup"><span data-stu-id="e87cd-178">RELATED LINKS</span></span>

[<span data-ttu-id="e87cd-179">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="e87cd-179">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="e87cd-180">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="e87cd-180">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="e87cd-181">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="e87cd-181">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="e87cd-182">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="e87cd-182">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="e87cd-183">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="e87cd-183">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="e87cd-184">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="e87cd-184">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="e87cd-185">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="e87cd-185">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="e87cd-186">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="e87cd-186">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="e87cd-187">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="e87cd-187">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="e87cd-188">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="e87cd-188">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="e87cd-189">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="e87cd-189">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="e87cd-190">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="e87cd-190">Test-WSMan</span></span>](Test-WSMan.md)
