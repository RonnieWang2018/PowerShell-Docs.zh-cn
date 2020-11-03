---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-pssessionconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSSessionConfiguration
ms.openlocfilehash: f44da41a08746ddb5b4396dbd263a671edb470bf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93197449"
---
# <span data-ttu-id="1dde9-103">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1dde9-103">Enable-PSSessionConfiguration</span></span>

## <span data-ttu-id="1dde9-104">摘要</span><span class="sxs-lookup"><span data-stu-id="1dde9-104">SYNOPSIS</span></span>
<span data-ttu-id="1dde9-105">启用本地计算机上的会话配置。</span><span class="sxs-lookup"><span data-stu-id="1dde9-105">Enables the session configurations on the local computer.</span></span>

## <span data-ttu-id="1dde9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1dde9-106">SYNTAX</span></span>

```
Enable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-SecurityDescriptorSddl <String>]
 [-SkipNetworkProfileCheck] [-NoServiceRestart] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1dde9-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1dde9-107">DESCRIPTION</span></span>

<span data-ttu-id="1dde9-108">`Enable-PSSessionConfiguration`Cmdlet 可启用已禁用的已注册会话配置，例如通过使用 `Disable-PSSessionConfiguration` 或 `Disable-PSRemoting` Cmdlet 或的 **AccessMode** 参数 `Register-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="1dde9-108">The `Enable-PSSessionConfiguration` cmdlet enables registered session configurations that have been disabled, such as by using the `Disable-PSSessionConfiguration` or `Disable-PSRemoting` cmdlets, or the **AccessMode** parameter of `Register-PSSessionConfiguration`.</span></span> <span data-ttu-id="1dde9-109">这是一个高级 cmdlet，旨在供系统管理员为其用户管理自定义会话配置时使用。</span><span class="sxs-lookup"><span data-stu-id="1dde9-109">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="1dde9-110">如果没有参数，则将 `Enable-PSSessionConfiguration` 启用 " **Microsoft PowerShell** 配置"，这是用于会话的默认配置。</span><span class="sxs-lookup"><span data-stu-id="1dde9-110">Without parameters, `Enable-PSSessionConfiguration` enables the **Microsoft.PowerShell** configuration, which is the default configuration that is used for sessions.</span></span>

<span data-ttu-id="1dde9-111">`Enable-PSSessionConfiguration` 从受影响的会话配置的安全描述符中删除 **Deny_All** 设置，启用接受任何 IP 地址上的请求的侦听器，并重新启动 WinRM 服务。</span><span class="sxs-lookup"><span data-stu-id="1dde9-111">`Enable-PSSessionConfiguration` removes the **Deny_All** setting from the security descriptor of the affected session configurations, turns on the listener that accepts requests on any IP address, and restarts the WinRM service.</span></span> <span data-ttu-id="1dde9-112">从 PowerShell 3.0 开始， `Enable-PSSessionConfiguration` 还将会话配置的 **Enabled** 属性的值 (`WSMan:\<computer>\PlugIn\<SessionConfigurationName>\Enabled`) 设置为 True。</span><span class="sxs-lookup"><span data-stu-id="1dde9-112">Beginning in PowerShell 3.0, `Enable-PSSessionConfiguration` also sets the value of the **Enabled** property of the session configuration (`WSMan:\<computer>\PlugIn\<SessionConfigurationName>\Enabled`) to True.</span></span> <span data-ttu-id="1dde9-113">但是，不 `Enable-PSSessionConfiguration` 会删除或更改 **Network_Deny_All** (`AccessMode=Local`) 安全描述符设置，只允许本地计算机的用户使用该会话配置。</span><span class="sxs-lookup"><span data-stu-id="1dde9-113">However, `Enable-PSSessionConfiguration` does not remove or change the **Network_Deny_All** (`AccessMode=Local`) security descriptor setting that allows only users of the local computer to use to the session configuration.</span></span>

## <span data-ttu-id="1dde9-114">示例</span><span class="sxs-lookup"><span data-stu-id="1dde9-114">EXAMPLES</span></span>

### <span data-ttu-id="1dde9-115">示例1：重新启用默认会话</span><span class="sxs-lookup"><span data-stu-id="1dde9-115">Example 1: Re-enable the default session</span></span>

<span data-ttu-id="1dde9-116">此示例将在计算机上重新启用 **Microsoft PowerShell** 默认会话配置。</span><span class="sxs-lookup"><span data-stu-id="1dde9-116">This example re-enables the **Microsoft.PowerShell** default session configuration on the computer.</span></span>

```powershell
Enable-PSSessionConfiguration
```

### <span data-ttu-id="1dde9-117">示例2：重新启用指定的会话</span><span class="sxs-lookup"><span data-stu-id="1dde9-117">Example 2: Re-enable specified sessions</span></span>

<span data-ttu-id="1dde9-118">此示例将重新启用计算机上的 **MaintenanceShell** 和 **AdminShell** 会话配置。</span><span class="sxs-lookup"><span data-stu-id="1dde9-118">This example re-enables the **MaintenanceShell** and **AdminShell** session configurations on the computer.</span></span>

```powershell
Enable-PSSessionConfiguration -Name MaintenanceShell, AdminShell
```

### <span data-ttu-id="1dde9-119">示例3：重新启用所有会话</span><span class="sxs-lookup"><span data-stu-id="1dde9-119">Example 3: Re-enable the all sessions</span></span>

<span data-ttu-id="1dde9-120">此示例将重新启用计算机上的所有会话配置。</span><span class="sxs-lookup"><span data-stu-id="1dde9-120">This example re-enables all session configurations on the computer.</span></span> <span data-ttu-id="1dde9-121">这些命令是等效的。</span><span class="sxs-lookup"><span data-stu-id="1dde9-121">These commands are equivalent.</span></span>
<span data-ttu-id="1dde9-122">因此，您可以使用这两种方法。</span><span class="sxs-lookup"><span data-stu-id="1dde9-122">Therefore, you can use either.</span></span>

```powershell
Enable-PSSessionConfiguration -Name *
Get-PSSessionConfiguration | Enable-PSSessionConfiguration
```

<span data-ttu-id="1dde9-123">`Enable-PSSessionConfiguration` 如果启用已启用的会话配置，则不会生成错误。</span><span class="sxs-lookup"><span data-stu-id="1dde9-123">`Enable-PSSessionConfiguration` does not generate an error if you enable a session configuration that is already enabled.</span></span>

### <span data-ttu-id="1dde9-124">示例4：重新启用会话并指定新的安全描述符</span><span class="sxs-lookup"><span data-stu-id="1dde9-124">Example 4: Re-enable a session and specify a new security descriptor</span></span>

<span data-ttu-id="1dde9-125">此示例将重新启用 **MaintenanceShell** 会话配置，并为该配置指定新的安全描述符。</span><span class="sxs-lookup"><span data-stu-id="1dde9-125">This example re-enables the **MaintenanceShell** session configuration and specifies a new security descriptor for the configuration.</span></span>

```powershell
$sddl = "O:NSG:BAD:P(A;;GXGWGR;;;BA)(A;;GAGR;;;S-1-5-21-123456789-188441444-3100496)S:P"
Enable-PSSessionConfiguration -Name MaintenanceShell -SecurityDescriptorSDDL $sddl
```

## <span data-ttu-id="1dde9-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1dde9-126">PARAMETERS</span></span>

### <span data-ttu-id="1dde9-127">-Force</span><span class="sxs-lookup"><span data-stu-id="1dde9-127">-Force</span></span>

<span data-ttu-id="1dde9-128">指示 cmdlet 不提示进行确认，并且将在无提示的情况下重启 WinRM 服务。</span><span class="sxs-lookup"><span data-stu-id="1dde9-128">Indicates that the cmdlet does not prompt you for confirmation, and restarts the WinRM service without prompting.</span></span> <span data-ttu-id="1dde9-129">重新启动服务可使配置更改生效。</span><span class="sxs-lookup"><span data-stu-id="1dde9-129">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="1dde9-130">若要阻止重新启动并取消重新启动提示，请使用 **NoServiceRestart** 参数。</span><span class="sxs-lookup"><span data-stu-id="1dde9-130">To prevent a restart and suppress the restart prompt, use the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="1dde9-131">-Name</span><span class="sxs-lookup"><span data-stu-id="1dde9-131">-Name</span></span>

<span data-ttu-id="1dde9-132">指定要启用的会话配置的名称。</span><span class="sxs-lookup"><span data-stu-id="1dde9-132">Specifies the names of session configurations to enable.</span></span> <span data-ttu-id="1dde9-133">输入一个或多个配置名称。</span><span class="sxs-lookup"><span data-stu-id="1dde9-133">Enter one or more configuration names.</span></span>
<span data-ttu-id="1dde9-134">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="1dde9-134">Wildcard characters are permitted.</span></span>

<span data-ttu-id="1dde9-135">还可以通过管道将包含配置名称或会话配置对象的字符串传递给 `Enable-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="1dde9-135">You can also pipe a string that contains a configuration name or a session configuration object to `Enable-PSSessionConfiguration`.</span></span>

<span data-ttu-id="1dde9-136">如果省略此参数，则 `Enable-PSSessionConfiguration` 启用 **Microsoft PowerShell** 会话配置。</span><span class="sxs-lookup"><span data-stu-id="1dde9-136">If you omit this parameter, `Enable-PSSessionConfiguration` enables the **Microsoft.PowerShell** session configuration.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="1dde9-137">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="1dde9-137">-NoServiceRestart</span></span>

<span data-ttu-id="1dde9-138">指示该 cmdlet 不会重新启动该服务。</span><span class="sxs-lookup"><span data-stu-id="1dde9-138">Indicates that the cmdlet does not restart the service.</span></span>

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

### <span data-ttu-id="1dde9-139">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="1dde9-139">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="1dde9-140">指定一个安全描述符，此 cmdlet 用来替换会话配置上的安全描述符。</span><span class="sxs-lookup"><span data-stu-id="1dde9-140">Specifies a security descriptor with which this cmdlet replaces the security descriptor on the session configuration.</span></span>

<span data-ttu-id="1dde9-141">如果省略此参数，则 `Enable-PSSessionConfiguration` 仅从安全描述符中删除 "拒绝所有" 项。</span><span class="sxs-lookup"><span data-stu-id="1dde9-141">If you omit this parameter, `Enable-PSSessionConfiguration` only deletes the deny all item from the security descriptor.</span></span>

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

### <span data-ttu-id="1dde9-142">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="1dde9-142">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="1dde9-143">指示当计算机位于公用网络上时，此 cmdlet 将启用会话配置。</span><span class="sxs-lookup"><span data-stu-id="1dde9-143">Indicates that this cmdlet enables the session configuration when the computer is on a public network.</span></span> <span data-ttu-id="1dde9-144">此参数只允许为公用网络启用防火墙规则，该规则只允许远程访问同一本地子网中的计算机。</span><span class="sxs-lookup"><span data-stu-id="1dde9-144">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span> <span data-ttu-id="1dde9-145">默认情况下， `Enable-PSSessionConfiguration` 在公用网络上失败。</span><span class="sxs-lookup"><span data-stu-id="1dde9-145">By default, `Enable-PSSessionConfiguration` fails on a public network.</span></span>

<span data-ttu-id="1dde9-146">此参数适用于 Windows 操作系统的客户端版本。</span><span class="sxs-lookup"><span data-stu-id="1dde9-146">This parameter is designed for client versions of the Windows operating system.</span></span> <span data-ttu-id="1dde9-147">Windows 操作系统的服务器版本具有适用于公用网络的本地子网防火墙规则。</span><span class="sxs-lookup"><span data-stu-id="1dde9-147">Server versions of the Windows operating system have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="1dde9-148">但是，如果在 Windows 操作系统的服务器版本上禁用了本地子网防火墙规则，则此参数将重新启用它。</span><span class="sxs-lookup"><span data-stu-id="1dde9-148">However, if the local subnet firewall rule is disabled on a server version of the Windows operating system, this parameter re-enables it.</span></span>

<span data-ttu-id="1dde9-149">若要删除本地子网限制并从公用网络上的所有位置启用远程访问，请 `Set-NetFirewallRule` 在 NetSecurity 模块中使用 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1dde9-149">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the NetSecurity module.</span></span> <span data-ttu-id="1dde9-150">有关详细信息，请参阅 `Enable-PSRemoting`。</span><span class="sxs-lookup"><span data-stu-id="1dde9-150">For more information, see `Enable-PSRemoting`.</span></span>

<span data-ttu-id="1dde9-151">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="1dde9-151">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="1dde9-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1dde9-152">-Confirm</span></span>

<span data-ttu-id="1dde9-153">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="1dde9-153">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1dde9-154">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1dde9-154">-WhatIf</span></span>

<span data-ttu-id="1dde9-155">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="1dde9-155">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="1dde9-156">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="1dde9-156">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1dde9-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1dde9-157">CommonParameters</span></span>

<span data-ttu-id="1dde9-158">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="1dde9-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1dde9-159">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="1dde9-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1dde9-160">输入</span><span class="sxs-lookup"><span data-stu-id="1dde9-160">INPUTS</span></span>

### <span data-ttu-id="1dde9-161">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration、System.String</span><span class="sxs-lookup"><span data-stu-id="1dde9-161">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration, System.String</span></span>

<span data-ttu-id="1dde9-162">可以通过管道将会话配置对象或包含会话配置名称的字符串传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1dde9-162">You can pipe a session configuration object or a string that contains the name of a session configuration to this cmdlet.</span></span>

## <span data-ttu-id="1dde9-163">输出</span><span class="sxs-lookup"><span data-stu-id="1dde9-163">OUTPUTS</span></span>

### <span data-ttu-id="1dde9-164">无</span><span class="sxs-lookup"><span data-stu-id="1dde9-164">None</span></span>

<span data-ttu-id="1dde9-165">此 cmdlet 不返回任何对象。</span><span class="sxs-lookup"><span data-stu-id="1dde9-165">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="1dde9-166">注释</span><span class="sxs-lookup"><span data-stu-id="1dde9-166">NOTES</span></span>

<span data-ttu-id="1dde9-167">若要使用此 cmdlet，必须使用 "以 **管理员身份运行** " 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="1dde9-167">To use this cmdlet, you must start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="1dde9-168">相关链接</span><span class="sxs-lookup"><span data-stu-id="1dde9-168">RELATED LINKS</span></span>

[<span data-ttu-id="1dde9-169">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1dde9-169">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="1dde9-170">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1dde9-170">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="1dde9-171">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="1dde9-171">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="1dde9-172">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="1dde9-172">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="1dde9-173">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1dde9-173">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="1dde9-174">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1dde9-174">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="1dde9-175">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="1dde9-175">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="1dde9-176">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1dde9-176">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="1dde9-177">WSMan 提供程序</span><span class="sxs-lookup"><span data-stu-id="1dde9-177">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="1dde9-178">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="1dde9-178">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="1dde9-179">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="1dde9-179">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
