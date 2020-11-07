---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-pssessionconfiguration?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSSessionConfiguration
ms.openlocfilehash: 028e28e071bf6e19f2d0aef72b4eec45da6c45b7
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345878"
---
# <span data-ttu-id="93bb4-103">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="93bb4-103">Register-PSSessionConfiguration</span></span>

## <span data-ttu-id="93bb4-104">摘要</span><span class="sxs-lookup"><span data-stu-id="93bb4-104">SYNOPSIS</span></span>
<span data-ttu-id="93bb4-105">创建并注册新的会话配置。</span><span class="sxs-lookup"><span data-stu-id="93bb4-105">Creates and registers a new session configuration.</span></span>

## <span data-ttu-id="93bb4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="93bb4-106">SYNTAX</span></span>

### <span data-ttu-id="93bb4-107">NameParameterSet（默认值）</span><span class="sxs-lookup"><span data-stu-id="93bb4-107">NameParameterSet (Default)</span></span>

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String> [-ApplicationBase <String>]
 [-RunAsCredential <PSCredential>] [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="93bb4-108">AssemblyNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="93bb4-108">AssemblyNameParameterSet</span></span>

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String> [-AssemblyName] <String>
 [-ApplicationBase <String>] [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>]
 [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="93bb4-109">SessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="93bb4-109">SessionConfigurationFile</span></span>

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String>
 [-RunAsCredential <PSCredential>] [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="93bb4-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="93bb4-110">DESCRIPTION</span></span>

<span data-ttu-id="93bb4-111">`Register-PSSessionConfiguration`Cmdlet 在本地计算机上创建并注册新的会话配置。</span><span class="sxs-lookup"><span data-stu-id="93bb4-111">The `Register-PSSessionConfiguration` cmdlet creates and registers a new session configuration on the local computer.</span></span> <span data-ttu-id="93bb4-112">这是一个高级 cmdlet，可用于为远程用户创建自定义会话。</span><span class="sxs-lookup"><span data-stu-id="93bb4-112">This is an advanced cmdlet that you can use to create custom sessions for remote users.</span></span>

<span data-ttu-id="93bb4-113">每个 PowerShell 会话 ( **PSSession** ) 使用会话配置（也称为终结点）。</span><span class="sxs-lookup"><span data-stu-id="93bb4-113">Every PowerShell session ( **PSSession** ) uses a session configuration, also known as an endpoint.</span></span>
<span data-ttu-id="93bb4-114">当用户创建连接到计算机的会话时，他们可以选择一个会话配置，或使用在启用 PowerShell 远程处理时注册的默认会话配置。</span><span class="sxs-lookup"><span data-stu-id="93bb4-114">When users create a session that connects to the computer, they can select a session configuration or use the default session configuration that is registered when you enable PowerShell remoting.</span></span>
<span data-ttu-id="93bb4-115">用户还可以设置 $PSSessionConfigurationName 首选项变量，它指定在当前会话中创建的远程会话的默认配置。</span><span class="sxs-lookup"><span data-stu-id="93bb4-115">Users can also set the $PSSessionConfigurationName preference variable, which specifies a default configuration for remote sessions created in the current session.</span></span>

<span data-ttu-id="93bb4-116">会话配置可定义远程会话的环境。</span><span class="sxs-lookup"><span data-stu-id="93bb4-116">The session configuration defines the environment for the remote session.</span></span> <span data-ttu-id="93bb4-117">此配置可以确定会话中可使用哪些命令和语言元素，它可以包含用于保护计算机的设置，如用于限制单个对象或命令中会话可以远程接收的数据量的设置。</span><span class="sxs-lookup"><span data-stu-id="93bb4-117">The configuration can determine which commands and language elements are available in the session, and it can include settings that protect the computer, such as those that limit the amount of data that the session can receive remotely in a single object or command.</span></span> <span data-ttu-id="93bb4-118">会话配置的安全描述符将确定哪些用户有权使用会话配置。</span><span class="sxs-lookup"><span data-stu-id="93bb4-118">The security descriptor of the session configuration determines which users have permission to use the session configuration.</span></span>

<span data-ttu-id="93bb4-119">通过使用可实现新的配置类的程序集以及在会话中运行的脚本，可以定义配置的元素。</span><span class="sxs-lookup"><span data-stu-id="93bb4-119">You can define the elements of configuration by using an assembly that implements a new configuration class and by using a script that runs in the session.</span></span> <span data-ttu-id="93bb4-120">从 PowerShell 3.0 开始，还可以使用会话配置文件来定义会话配置。</span><span class="sxs-lookup"><span data-stu-id="93bb4-120">Beginning in PowerShell 3.0, you can also use a session configuration file to define the session configuration.</span></span>

<span data-ttu-id="93bb4-121">有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="93bb4-121">For information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>
<span data-ttu-id="93bb4-122">有关会话配置文件的信息，请参阅 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)。</span><span class="sxs-lookup"><span data-stu-id="93bb4-122">For information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

## <span data-ttu-id="93bb4-123">示例</span><span class="sxs-lookup"><span data-stu-id="93bb4-123">EXAMPLES</span></span>

### <span data-ttu-id="93bb4-124">示例1：注册 NewShell 会话配置</span><span class="sxs-lookup"><span data-stu-id="93bb4-124">Example 1: Register a NewShell session configuration</span></span>

<span data-ttu-id="93bb4-125">在此示例中，我们将注册 **NewShell** 会话配置。</span><span class="sxs-lookup"><span data-stu-id="93bb4-125">In this example, we register the **NewShell** session configuration.</span></span> <span data-ttu-id="93bb4-126">**AssemblyName** 和 **ApplicationBase** 参数指定 **MyShell.dll** 文件的位置，该位置指定会话配置中的 cmdlet 和提供程序。</span><span class="sxs-lookup"><span data-stu-id="93bb4-126">The **AssemblyName** and **ApplicationBase** parameters specify the location of the **MyShell.dll** file, which specifies the cmdlets and providers in the session configuration.</span></span> <span data-ttu-id="93bb4-127">**ConfigurationTypeName** 参数指定要从程序集使用的配置类。</span><span class="sxs-lookup"><span data-stu-id="93bb4-127">The **ConfigurationTypeName** parameter specifies the configuration class to use from the assembly.</span></span>

```powershell
$sessionConfiguration = @{
    Name='NewShell'
    ApplicationBase='c:\MyShells\'
    AssemblyName='MyShell.dll'
    ConfigurationTypeName='MyClass'
}
Register-PSSessionConfiguration @sessionConfiguration
```

<span data-ttu-id="93bb4-128">若要使用此配置，请键入 `New-PSSession -ConfigurationName newshell` 。</span><span class="sxs-lookup"><span data-stu-id="93bb4-128">To use this configuration, type `New-PSSession -ConfigurationName newshell`.</span></span>

### <span data-ttu-id="93bb4-129">示例2：注册 MaintenanceShell 会话配置</span><span class="sxs-lookup"><span data-stu-id="93bb4-129">Example 2: Register a MaintenanceShell session configuration</span></span>

<span data-ttu-id="93bb4-130">此示例在本地计算机上注册 **MaintenanceShell** 会话配置。</span><span class="sxs-lookup"><span data-stu-id="93bb4-130">This example registers the **MaintenanceShell** session configuration on the local computer.</span></span> <span data-ttu-id="93bb4-131">**StartupScript** 参数指定 `Maintenance.ps1` 脚本。</span><span class="sxs-lookup"><span data-stu-id="93bb4-131">The **StartupScript** parameter specifies the `Maintenance.ps1` script.</span></span>

```powershell
Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
```

<span data-ttu-id="93bb4-132">当用户使用 `New-PSSession` 命令并选择 **MaintenanceShell** 配置时，该脚本将 `Maintenance.ps1` 在新的会话中运行。</span><span class="sxs-lookup"><span data-stu-id="93bb4-132">When a user uses a `New-PSSession` command and selects the **MaintenanceShell** configuration, the `Maintenance.ps1` script runs in the new session.</span></span> <span data-ttu-id="93bb4-133">该脚本可以配置会话。</span><span class="sxs-lookup"><span data-stu-id="93bb4-133">The script can configure the session.</span></span> <span data-ttu-id="93bb4-134">这包括导入模块和设置会话的执行策略。</span><span class="sxs-lookup"><span data-stu-id="93bb4-134">This includes importing modules and setting the execution policy for the session.</span></span> <span data-ttu-id="93bb4-135">如果脚本生成任何错误，包括非终止错误，则该 `New-PSSession` 命令将失败。</span><span class="sxs-lookup"><span data-stu-id="93bb4-135">If the script generates any errors, including non-terminating errors, the `New-PSSession` command fails.</span></span>

### <span data-ttu-id="93bb4-136">示例3：注册会话配置</span><span class="sxs-lookup"><span data-stu-id="93bb4-136">Example 3: Register a session configuration</span></span>

<span data-ttu-id="93bb4-137">此示例将注册 **AdminShell** 会话配置。</span><span class="sxs-lookup"><span data-stu-id="93bb4-137">This example registers the **AdminShell** session configuration.</span></span>

<span data-ttu-id="93bb4-138">`$sessionParams`变量是包含所有参数值的哈希表。</span><span class="sxs-lookup"><span data-stu-id="93bb4-138">The `$sessionParams` variable is a hashtable containing all the parameter values.</span></span> <span data-ttu-id="93bb4-139">使用 PowerShell 展开将此哈希表传递给 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="93bb4-139">This hashtable is passed to the cmdlet using PowerShell splatting.</span></span> <span data-ttu-id="93bb4-140">该 `Register-PSSessionConfiguration` 命令使用 **SecurityDescritorSDDL** 参数在变量的值中指定 SDDL `$sddl` ，并使用 **MaximumReceivedObjectSizeMB** 参数来增加对象大小限制。</span><span class="sxs-lookup"><span data-stu-id="93bb4-140">The `Register-PSSessionConfiguration` command uses the **SecurityDescritorSDDL** parameter to specify the SDDL in the value of the `$sddl` variable and the **MaximumReceivedObjectSizeMB** parameter to increase the object size limit.</span></span> <span data-ttu-id="93bb4-141">它还使用 **StartupScript** 参数来指定用于配置会话的脚本。</span><span class="sxs-lookup"><span data-stu-id="93bb4-141">It also uses the **StartupScript** parameter to specify a script that configures the session.</span></span>

```powershell
$sddl = "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;FA;SA;GWGX;;WD)"
$sessionParams = @{
    Name="AdminShell"
    SecurityDescriptorSDDL=$sddl
    MaximumReceivedObjectSizeMB=20
    StartupScript="C:\scripts\AdminShell.ps1"
}
Register-PSSessionConfiguration @sessionParams
```

### <span data-ttu-id="93bb4-142">示例4：返回配置容器元素</span><span class="sxs-lookup"><span data-stu-id="93bb4-142">Example 4: Return a configuration container element</span></span>

<span data-ttu-id="93bb4-143">此示例演示如何注册 **MaintenanceShell** 配置。</span><span class="sxs-lookup"><span data-stu-id="93bb4-143">This example shows how to register the **MaintenanceShell** configuration.</span></span>
<span data-ttu-id="93bb4-144">`Register-PSSessionConfiguration` 返回存储在变量中的 **WSManConfigContainerElement** 对象 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="93bb4-144">`Register-PSSessionConfiguration` returns a **WSManConfigContainerElement** object stored in the `$s` variable.</span></span> <span data-ttu-id="93bb4-145">`Format-List` 显示返回对象的所有属性。</span><span class="sxs-lookup"><span data-stu-id="93bb4-145">`Format-List` displays all the properties of the returned object.</span></span> <span data-ttu-id="93bb4-146">**PSPath** 属性显示该对象存储在 WSMan: 驱动器的目录中。</span><span class="sxs-lookup"><span data-stu-id="93bb4-146">The **PSPath** property shows that the object is stored in a directory of the WSMan: drive.</span></span> <span data-ttu-id="93bb4-147">`Get-ChildItem` (别名 `dir`) 显示路径中的项 `WSMan:\LocalHost\PlugIn` 。</span><span class="sxs-lookup"><span data-stu-id="93bb4-147">`Get-ChildItem` (alias `dir`) displays the items in the `WSMan:\LocalHost\PlugIn` path.</span></span> <span data-ttu-id="93bb4-148">其中包括新的 **MaintenanceShell** 配置和 PowerShell 附带的两个默认配置。</span><span class="sxs-lookup"><span data-stu-id="93bb4-148">These include the new **MaintenanceShell** configuration and the two default configurations that come with PowerShell.</span></span>

```powershell
$s = Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
$s | Format-List -Property *
dir WSMan:\LocalHost\Plugin
```

```Output
PSPath            : Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell
PSParentPath      : Microsoft.WSMan.Management\WSMan::localhost\Plugin
PSChildName       : MaintenanceShell
PSDrive           : WSMan
PSProvider        : Microsoft.WSMan.Management\WSMan
PSIsContainer     : True
Keys              : {Name=MaintenanceShell}
Name              : MaintenanceShell
TypeNameOfElement : Container

Name                      Type                 Keys
----                      ----                 ----
MaintenanceShell          Container            {Name=MaintenanceShell}
microsoft.powershell      Container            {Name=microsoft.powershell}
microsoft.powershell32    Container            {Name=microsoft.powershell32}
```

### <span data-ttu-id="93bb4-149">示例5：使用启动脚本注册会话配置</span><span class="sxs-lookup"><span data-stu-id="93bb4-149">Example 5: Register a session configuration with a startup script</span></span>

<span data-ttu-id="93bb4-150">在此示例中，我们将创建并注册 **WithProfile** 会话配置。</span><span class="sxs-lookup"><span data-stu-id="93bb4-150">In this example we create and register the **WithProfile** session configuration.</span></span> <span data-ttu-id="93bb4-151">**StartupScript** 参数指示 PowerShell 为任何使用会话配置的会话运行指定的脚本。</span><span class="sxs-lookup"><span data-stu-id="93bb4-151">The **StartupScript** parameter directs PowerShell to run the specified script for any session that uses the session configuration.</span></span>

```powershell
Register-PSSessionConfiguration -Name WithProfile -StartupScript Add-Profile.ps1
```

<span data-ttu-id="93bb4-152">该脚本包含单个命令，该命令使用点 (.) 来获得来源，以在会话的当前作用域中运行用户的 **CurrentUserAllHosts** 配置文件。</span><span class="sxs-lookup"><span data-stu-id="93bb4-152">The script contains a single command that uses dot sourcing to run the user's **CurrentUserAllHosts** profile in the current scope of the session.</span></span>

<span data-ttu-id="93bb4-153">有关配置文件的详细信息，请参阅 [about_Profiles](./About/about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="93bb4-153">For more information about profiles, see [about_Profiles](./About/about_Profiles.md).</span></span> <span data-ttu-id="93bb4-154">有关使用点 (.) 来获得来源的详细信息，请参阅 [about_Scopes](./About/about_Scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="93bb4-154">For more information about dot sourcing, see [about_Scopes](./About/about_Scopes.md).</span></span>

## <span data-ttu-id="93bb4-155">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="93bb4-155">PARAMETERS</span></span>

### <span data-ttu-id="93bb4-156">-AccessMode</span><span class="sxs-lookup"><span data-stu-id="93bb4-156">-AccessMode</span></span>

<span data-ttu-id="93bb4-157">启用和禁用会话配置，并确定它是否可以用于计算机上的远程或本地会话。</span><span class="sxs-lookup"><span data-stu-id="93bb4-157">Enables and disables the session configuration and determines whether it can be used for remote or local sessions on the computer.</span></span> <span data-ttu-id="93bb4-158">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="93bb4-158">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="93bb4-159">已禁用。</span><span class="sxs-lookup"><span data-stu-id="93bb4-159">Disabled.</span></span> <span data-ttu-id="93bb4-160">禁用会话配置。</span><span class="sxs-lookup"><span data-stu-id="93bb4-160">Disables the session configuration.</span></span> <span data-ttu-id="93bb4-161">它不能用于对计算机的远程或本地访问。</span><span class="sxs-lookup"><span data-stu-id="93bb4-161">It cannot be used for remote or local access to the computer.</span></span>
- <span data-ttu-id="93bb4-162">Local。</span><span class="sxs-lookup"><span data-stu-id="93bb4-162">Local.</span></span> <span data-ttu-id="93bb4-163">允许本地计算机的用户使用会话配置在同一台计算机上创建本地环回会话，但拒绝远程用户的访问。</span><span class="sxs-lookup"><span data-stu-id="93bb4-163">Allows users of the local computer to use the session configuration to create a local loopback session on the same computer, but denies access to remote users.</span></span>
- <span data-ttu-id="93bb4-164">远程.</span><span class="sxs-lookup"><span data-stu-id="93bb4-164">Remote.</span></span> <span data-ttu-id="93bb4-165">允许本地和远程用户使用会话配置创建会话并在此计算机上运行命令。</span><span class="sxs-lookup"><span data-stu-id="93bb4-165">Allows local and remote users to use the session configuration to create sessions and run commands on this computer.</span></span>

<span data-ttu-id="93bb4-166">默认值为 "远程"。</span><span class="sxs-lookup"><span data-stu-id="93bb4-166">The default value is Remote.</span></span>

<span data-ttu-id="93bb4-167">其他 cmdlet 稍后可以重写此参数的值。</span><span class="sxs-lookup"><span data-stu-id="93bb4-167">Other cmdlets can override the value of this parameter later.</span></span> <span data-ttu-id="93bb4-168">例如， `Enable-PSRemoting` cmdlet 允许远程访问所有会话配置， `Enable-PSSessionConfiguration` cmdlet 启用会话配置，并且该 `Disable-PSRemoting` cmdlet 阻止对所有会话配置的远程访问。</span><span class="sxs-lookup"><span data-stu-id="93bb4-168">For example, the `Enable-PSRemoting` cmdlet allows for remote access to all session configurations, the `Enable-PSSessionConfiguration` cmdlet enables session configurations, and the `Disable-PSRemoting` cmdlet prevents remote access to all session configurations.</span></span>

<span data-ttu-id="93bb4-169">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="93bb4-169">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSessionConfigurationAccessMode
Parameter Sets: (All)
Aliases:
Accepted values: Disabled, Local, Remote

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93bb4-170">-ApplicationBase</span><span class="sxs-lookup"><span data-stu-id="93bb4-170">-ApplicationBase</span></span>

<span data-ttu-id="93bb4-171">指定 \* 在 **AssemblyName** 参数的值中指定的程序集文件 () 的路径。</span><span class="sxs-lookup"><span data-stu-id="93bb4-171">Specifies the path of the assembly file (\*.dll) that is specified in the value of the **AssemblyName** parameter.</span></span> <span data-ttu-id="93bb4-172">如果 **AssemblyName** 参数的值不包括路径，则使用此参数。</span><span class="sxs-lookup"><span data-stu-id="93bb4-172">Use this parameter when the value of the **AssemblyName** parameter does not include a path.</span></span> <span data-ttu-id="93bb4-173">默认为当前目录。</span><span class="sxs-lookup"><span data-stu-id="93bb4-173">The default is the current directory.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93bb4-174">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="93bb4-174">-AssemblyName</span></span>

<span data-ttu-id="93bb4-175">指定 \* 在其中定义配置类型 () 程序集文件的名称。</span><span class="sxs-lookup"><span data-stu-id="93bb4-175">Specifies the name of an assembly file (\*.dll) in which the configuration type is defined.</span></span> <span data-ttu-id="93bb4-176">可以在此参数或 **ApplicationBase** 参数的值中指定 .dll 的路径。</span><span class="sxs-lookup"><span data-stu-id="93bb4-176">You can specify the path of the .dll in this parameter or in the value of the **ApplicationBase** parameter.</span></span>

<span data-ttu-id="93bb4-177">当指定 **ConfigurationTypeName** 参数时，此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="93bb4-177">This parameter is required when you specify the **ConfigurationTypeName** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93bb4-178">-ConfigurationTypeName</span><span class="sxs-lookup"><span data-stu-id="93bb4-178">-ConfigurationTypeName</span></span>

<span data-ttu-id="93bb4-179">指定用于此配置的 Microsoft .NET Framework 类型的完全限定的名称。</span><span class="sxs-lookup"><span data-stu-id="93bb4-179">Specifies the fully qualified name of the Microsoft .NET Framework type that is used for this configuration.</span></span> <span data-ttu-id="93bb4-180">指定的类型必须实现 **System.Management.Automation.Remoting.PSSessionConfiguration** 类。</span><span class="sxs-lookup"><span data-stu-id="93bb4-180">The type that you specify must implement the **System.Management.Automation.Remoting.PSSessionConfiguration** class.</span></span>

<span data-ttu-id="93bb4-181">若要指定 \* 实现配置类型 () 的程序集文件，请指定 **AssemblyName** 和 **ApplicationBase** 参数。</span><span class="sxs-lookup"><span data-stu-id="93bb4-181">To specify the assembly file (\*.dll) that implements the configuration type, specify the **AssemblyName** and **ApplicationBase** parameters.</span></span>

<span data-ttu-id="93bb4-182">通过创建类型，可以控制会话配置的更多方面，如公开或隐藏 cmdlet 的某些参数，或设置用户无法重写的数据大小和对象大小限制。</span><span class="sxs-lookup"><span data-stu-id="93bb4-182">Creating a type lets you control more aspects of the session configuration, such as exposing or hiding certain parameters of cmdlets, or setting data size and object size limits that users cannot override.</span></span>

<span data-ttu-id="93bb4-183">如果省略此参数，则 **DefaultRemotePowerShellConfiguration** 类将用于会话配置。</span><span class="sxs-lookup"><span data-stu-id="93bb4-183">If you omit this parameter, the **DefaultRemotePowerShellConfiguration** class is used for the session configuration.</span></span>

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93bb4-184">-Force</span><span class="sxs-lookup"><span data-stu-id="93bb4-184">-Force</span></span>

<span data-ttu-id="93bb4-185">禁止显示所有用户提示，并在不提示的情况下重新启动 **WinRM** 服务。</span><span class="sxs-lookup"><span data-stu-id="93bb4-185">Suppresses all user prompts and restarts the **WinRM** service without prompting.</span></span> <span data-ttu-id="93bb4-186">重新启动服务可使配置更改生效。</span><span class="sxs-lookup"><span data-stu-id="93bb4-186">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="93bb4-187">若要防止重新启动并取消重新启动提示，请指定 **NoServiceRestart** 参数。</span><span class="sxs-lookup"><span data-stu-id="93bb4-187">To prevent a restart and suppress the restart prompt, specify the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="93bb4-188">-MaximumReceivedDataSizePerCommandMB</span><span class="sxs-lookup"><span data-stu-id="93bb4-188">-MaximumReceivedDataSizePerCommandMB</span></span>

<span data-ttu-id="93bb4-189">指定在任何单个远程命令中可以发送到此计算机的数据量限制。</span><span class="sxs-lookup"><span data-stu-id="93bb4-189">Specifies a limit for the amount of data that can be sent to this computer in any single remote command.</span></span> <span data-ttu-id="93bb4-190">输入数据大小（以兆字节 (MB) 为单位）。</span><span class="sxs-lookup"><span data-stu-id="93bb4-190">Enter the data size in megabytes (MB).</span></span> <span data-ttu-id="93bb4-191">默认值为 50 MB。</span><span class="sxs-lookup"><span data-stu-id="93bb4-191">The default is 50 MB.</span></span>

<span data-ttu-id="93bb4-192">如果在 **ConfigurationTypeName** 参数中指定的配置类型中定义数据大小限制，则将使用配置类型中的限制并忽略此参数的值。</span><span class="sxs-lookup"><span data-stu-id="93bb4-192">If a data size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used and the value of this parameter is ignored.</span></span>

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93bb4-193">-MaximumReceivedObjectSizeMB</span><span class="sxs-lookup"><span data-stu-id="93bb4-193">-MaximumReceivedObjectSizeMB</span></span>

<span data-ttu-id="93bb4-194">指定在任何单个对象中可以发送到此计算机的数据量的限制。</span><span class="sxs-lookup"><span data-stu-id="93bb4-194">Specifies a limit for the amount of data that can be sent to this computer in any single object.</span></span>
<span data-ttu-id="93bb4-195">输入数据大小（以 mb 为单位）。</span><span class="sxs-lookup"><span data-stu-id="93bb4-195">Enter the data size in megabytes.</span></span> <span data-ttu-id="93bb4-196">默认值为 10 MB。</span><span class="sxs-lookup"><span data-stu-id="93bb4-196">The default is 10 MB.</span></span>

<span data-ttu-id="93bb4-197">如果在 **ConfigurationTypeName** 参数中指定的配置类型中定义对象大小限制，则将使用配置类型中的限制并忽略此参数的值。</span><span class="sxs-lookup"><span data-stu-id="93bb4-197">If an object size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used and the value of this parameter is ignored.</span></span>

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93bb4-198">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="93bb4-198">-ModulesToImport</span></span>

<span data-ttu-id="93bb4-199">指定自动导入到使用会话配置的会话中的模块。</span><span class="sxs-lookup"><span data-stu-id="93bb4-199">Specifies the modules that are automatically imported into sessions that use the session configuration.</span></span>

<span data-ttu-id="93bb4-200">默认情况下，仅将 **Microsoft** 导入到会话中。</span><span class="sxs-lookup"><span data-stu-id="93bb4-200">By default, only **Microsoft.PowerShell.Core** is imported into sessions.</span></span> <span data-ttu-id="93bb4-201">除非排除 cmdlet，否则可以使用 `Import-Module` 将模块添加到会话中。</span><span class="sxs-lookup"><span data-stu-id="93bb4-201">Unless the cmdlets are excluded, you can use `Import-Module` to add modules to the session.</span></span>

<span data-ttu-id="93bb4-202">在此参数值中指定的模块将导入到由 **SessionType** 参数指定的模块中，以及会话配置文件中的 **ModulesToImport** 键中列出的模块 (`New-PSSessionConfigurationFile`) 。</span><span class="sxs-lookup"><span data-stu-id="93bb4-202">The modules specified in this parameter value are imported in additions to modules that are specified by the **SessionType** parameter and those listed in the **ModulesToImport** key in the session configuration file (`New-PSSessionConfigurationFile`).</span></span> <span data-ttu-id="93bb4-203">但是，会话配置文件中的设置可以隐藏模块所导出的命令或阻止用户使用它们。</span><span class="sxs-lookup"><span data-stu-id="93bb4-203">However, settings in the session configuration file can hide the commands exported by modules or prevent users from using them.</span></span>

<span data-ttu-id="93bb4-204">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="93bb4-204">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93bb4-205">-Name</span><span class="sxs-lookup"><span data-stu-id="93bb4-205">-Name</span></span>

<span data-ttu-id="93bb4-206">指定会话配置的名称。</span><span class="sxs-lookup"><span data-stu-id="93bb4-206">Specifies a name for the session configuration.</span></span> <span data-ttu-id="93bb4-207">此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="93bb4-207">This parameter is required.</span></span>

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

### <span data-ttu-id="93bb4-208">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="93bb4-208">-NoServiceRestart</span></span>

<span data-ttu-id="93bb4-209">不会重新启动 **WinRM** 服务，而会禁止提示重新启动该服务。</span><span class="sxs-lookup"><span data-stu-id="93bb4-209">Does not restart the **WinRM** service, and suppresses the prompt to restart the service.</span></span>

<span data-ttu-id="93bb4-210">默认情况下，当你运行 `Register-PSSessionConfiguration` 命令时，系统将提示你重新启动 **WinRM** 服务以使新的会话配置生效。</span><span class="sxs-lookup"><span data-stu-id="93bb4-210">By default, when you run a `Register-PSSessionConfiguration` command, you are prompted to restart the **WinRM** service to make the new session configuration effective.</span></span> <span data-ttu-id="93bb4-211">在重新启动 **WinRM** 服务之前，新的会话配置不会生效。</span><span class="sxs-lookup"><span data-stu-id="93bb4-211">Until the **WinRM** service is restarted, the new session configuration is not effective.</span></span>

<span data-ttu-id="93bb4-212">若要在无提示的情况下重启 **WinRM** 服务，请指定 Force 参数。</span><span class="sxs-lookup"><span data-stu-id="93bb4-212">To restart the **WinRM** service without prompting, specify the **Force** parameter.</span></span> <span data-ttu-id="93bb4-213">若要手动重新启动 **WinRM** 服务，请使用 `Restart-Service` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="93bb4-213">To restart the **WinRM** service manually, use the `Restart-Service` cmdlet.</span></span>

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

### <span data-ttu-id="93bb4-214">-Path</span><span class="sxs-lookup"><span data-stu-id="93bb4-214">-Path</span></span>

<span data-ttu-id="93bb4-215">指定会话配置文件的路径和文件名 ( .pssc) ，如创建的文件 `New-PSSessionConfigurationFile` 。</span><span class="sxs-lookup"><span data-stu-id="93bb4-215">Specifies the path and filename of a session configuration file (.pssc), such as one created by `New-PSSessionConfigurationFile`.</span></span> <span data-ttu-id="93bb4-216">如果省略路径，则默认路径为当前目录。</span><span class="sxs-lookup"><span data-stu-id="93bb4-216">If you omit the path, the default is the current directory.</span></span>

<span data-ttu-id="93bb4-217">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="93bb4-217">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SessionConfigurationFile
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93bb4-218">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="93bb4-218">-ProcessorArchitecture</span></span>

<span data-ttu-id="93bb4-219">确定在使用此会话配置的会话中是否启动了 PowerShell 进程的32位或64位版本。</span><span class="sxs-lookup"><span data-stu-id="93bb4-219">Determines whether a 32-bit or 64-bit version of the PowerShell process is started in sessions that use this session configuration.</span></span> <span data-ttu-id="93bb4-220">此参数可接受的值包括： x86 (32 位) 和 AMD64 () 64。</span><span class="sxs-lookup"><span data-stu-id="93bb4-220">The acceptable values for this parameter are: x86 (32-bit) and AMD64 (64-bit).</span></span> <span data-ttu-id="93bb4-221">默认值由托管该会话配置的计算机的处理器体系结构确定。</span><span class="sxs-lookup"><span data-stu-id="93bb4-221">The default value is determined by the processor architecture of the computer that hosts the session configuration.</span></span>

<span data-ttu-id="93bb4-222">可使用此参数在 64 位计算机上创建 32 位会话。</span><span class="sxs-lookup"><span data-stu-id="93bb4-222">You can use this parameter to create a 32-bit session on a 64-bit computer.</span></span> <span data-ttu-id="93bb4-223">尝试在 32 位计算机上创建 64 位进程将失败。</span><span class="sxs-lookup"><span data-stu-id="93bb4-223">Attempts to create a 64-bit process on a 32-bit computer fail.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PA
Accepted values: x86, amd64

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93bb4-224">-PSVersion</span><span class="sxs-lookup"><span data-stu-id="93bb4-224">-PSVersion</span></span>

<span data-ttu-id="93bb4-225">指定使用此会话配置的会话中的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="93bb4-225">Specifies the version of PowerShell in sessions that use this session configuration.</span></span>

<span data-ttu-id="93bb4-226">此参数的值优先于会话配置文件中 **PowerShellVersion** 键的值。</span><span class="sxs-lookup"><span data-stu-id="93bb4-226">The value of this parameter takes precedence over the value of the **PowerShellVersion** key in the session configuration file.</span></span>

<span data-ttu-id="93bb4-227">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="93bb4-227">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Version
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases: PowerShellVersion

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93bb4-228">-RunAsCredential</span><span class="sxs-lookup"><span data-stu-id="93bb4-228">-RunAsCredential</span></span>

<span data-ttu-id="93bb4-229">指定会话中的命令的凭据。</span><span class="sxs-lookup"><span data-stu-id="93bb4-229">Specifies credentials for commands in the session.</span></span> <span data-ttu-id="93bb4-230">默认情况下，在当前用户授权下运行命令。</span><span class="sxs-lookup"><span data-stu-id="93bb4-230">By default, commands run with the permissions of the current user.</span></span>

<span data-ttu-id="93bb4-231">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="93bb4-231">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93bb4-232">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="93bb4-232">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="93bb4-233">指定用于配置的安全描述符定义语言 (SDDL) 字符串。</span><span class="sxs-lookup"><span data-stu-id="93bb4-233">Specifies a Security Descriptor Definition Language (SDDL) string for the configuration.</span></span>

<span data-ttu-id="93bb4-234">此字符串确定使用新的会话配置所需的权限。</span><span class="sxs-lookup"><span data-stu-id="93bb4-234">This string determines the permissions that are required to use the new session configuration.</span></span> <span data-ttu-id="93bb4-235">若要在会话中使用会话配置，用户必须至少对配置执行 (调用) 权限。</span><span class="sxs-lookup"><span data-stu-id="93bb4-235">To use a session configuration in a session, users must have at least Execute (Invoke) permission for the configuration.</span></span>

<span data-ttu-id="93bb4-236">如果安全描述符较复杂，请考虑使用 **ShowSecurityDescriptorUI** 参数，而不是此参数。</span><span class="sxs-lookup"><span data-stu-id="93bb4-236">If the security descriptor is complex, consider using the **ShowSecurityDescriptorUI** parameter instead of this parameter.</span></span> <span data-ttu-id="93bb4-237">不能在同一命令中同时使用这两个参数。</span><span class="sxs-lookup"><span data-stu-id="93bb4-237">You cannot use both parameters in the same command.</span></span>

<span data-ttu-id="93bb4-238">如果省略此参数，则会将 **WinRM** 服务的根 SDDL 用于此配置。</span><span class="sxs-lookup"><span data-stu-id="93bb4-238">If you omit this parameter, the root SDDL for the **WinRM** service is used for this configuration.</span></span>
<span data-ttu-id="93bb4-239">若要查看或更改根 SDDL，请使用 WSMan 提供程序。</span><span class="sxs-lookup"><span data-stu-id="93bb4-239">To view or change the root SDDL, use the WSMan provider.</span></span> <span data-ttu-id="93bb4-240">例如，`Get-Item wsman:\localhost\service\rootSDDL`。</span><span class="sxs-lookup"><span data-stu-id="93bb4-240">For example `Get-Item wsman:\localhost\service\rootSDDL`.</span></span> <span data-ttu-id="93bb4-241">有关 WSMan 提供程序的详细信息，请键入 `Get-Help wsman` 。</span><span class="sxs-lookup"><span data-stu-id="93bb4-241">For more information about the WSMan provider, type `Get-Help wsman`.</span></span>

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

### <span data-ttu-id="93bb4-242">-SessionTypeOption</span><span class="sxs-lookup"><span data-stu-id="93bb4-242">-SessionTypeOption</span></span>

<span data-ttu-id="93bb4-243">指定会话配置的特定于类型的选项。</span><span class="sxs-lookup"><span data-stu-id="93bb4-243">Specifies type-specific options for the session configuration.</span></span> <span data-ttu-id="93bb4-244">输入会话类型选项对象，如 cmdlet 返回的 **new-psworkflowexecutionoption** 对象 `New-PSWorkflowExecutionOption` 。</span><span class="sxs-lookup"><span data-stu-id="93bb4-244">Enter a session type options object, such as the **PSWorkflowExecutionOption** object that the `New-PSWorkflowExecutionOption` cmdlet returns.</span></span>

<span data-ttu-id="93bb4-245">使用会话配置的会话选项由会话选项和会话配置选项的值确定。</span><span class="sxs-lookup"><span data-stu-id="93bb4-245">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="93bb4-246">除非指定，否则在会话中设置的选项（如使用 `New-PSSessionOption` cmdlet）优先于在会话配置中设置的选项。</span><span class="sxs-lookup"><span data-stu-id="93bb4-246">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="93bb4-247">但是，会话选项的值不能超过在会话配置中设置的最大值。</span><span class="sxs-lookup"><span data-stu-id="93bb4-247">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="93bb4-248">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="93bb4-248">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSSessionTypeOption
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93bb4-249">-ShowSecurityDescriptorUI</span><span class="sxs-lookup"><span data-stu-id="93bb4-249">-ShowSecurityDescriptorUI</span></span>

<span data-ttu-id="93bb4-250">指示此 cmdlet 显示可帮助你创建会话配置的 SDDL 的属性表。</span><span class="sxs-lookup"><span data-stu-id="93bb4-250">Indicates that this cmdlet displays a property sheet that helps you create the SDDL for the session configuration.</span></span> <span data-ttu-id="93bb4-251">输入该命令后，将显示属性表 `Register-PSSessionConfiguration` ，然后重新启动 **WinRM** 服务。</span><span class="sxs-lookup"><span data-stu-id="93bb4-251">The property sheet appears after you enter the `Register-PSSessionConfiguration` command and then restart the **WinRM** service.</span></span>

<span data-ttu-id="93bb4-252">在设置配置的权限时，请记住，用户必须至少执行 (调用) 权限才能在会话中使用会话配置。</span><span class="sxs-lookup"><span data-stu-id="93bb4-252">When setting the permissions for the configuration, remember that users must have at least Execute (Invoke) permission to use the session configuration in a session.</span></span>

<span data-ttu-id="93bb4-253">不能在同一命令中使用 **SecurityDescriptorSDDL** 参数和此参数。</span><span class="sxs-lookup"><span data-stu-id="93bb4-253">You cannot use the **SecurityDescriptorSDDL** parameter and this parameter in the same command.</span></span>

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

### <span data-ttu-id="93bb4-254">-StartupScript</span><span class="sxs-lookup"><span data-stu-id="93bb4-254">-StartupScript</span></span>

<span data-ttu-id="93bb4-255">指定 PowerShell 脚本的完全限定路径。</span><span class="sxs-lookup"><span data-stu-id="93bb4-255">Specifies the fully qualified path of a PowerShell script.</span></span> <span data-ttu-id="93bb4-256">指定的脚本在使用会话配置的新会话中运行。</span><span class="sxs-lookup"><span data-stu-id="93bb4-256">The specified script runs in the new session that uses the session configuration.</span></span>

<span data-ttu-id="93bb4-257">你可以使用脚本来额外配置会话。</span><span class="sxs-lookup"><span data-stu-id="93bb4-257">You can use the script to additionally configure the session.</span></span> <span data-ttu-id="93bb4-258">如果脚本生成错误，甚至是一个非终止错误，则不会创建会话，并且该 `New-PSSession` 命令将失败。</span><span class="sxs-lookup"><span data-stu-id="93bb4-258">If the script generates an error, even a non-terminating error, the session is not created and the `New-PSSession` command fails.</span></span>

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

### <span data-ttu-id="93bb4-259">-ThreadOptions</span><span class="sxs-lookup"><span data-stu-id="93bb4-259">-ThreadOptions</span></span>

<span data-ttu-id="93bb4-260">指定在会话中运行命令时如何创建和使用线程。</span><span class="sxs-lookup"><span data-stu-id="93bb4-260">Specifies how threads are created and used when a command runs in the session.</span></span> <span data-ttu-id="93bb4-261">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="93bb4-261">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="93bb4-262">默认</span><span class="sxs-lookup"><span data-stu-id="93bb4-262">Default</span></span>
- <span data-ttu-id="93bb4-263">ReuseThread</span><span class="sxs-lookup"><span data-stu-id="93bb4-263">ReuseThread</span></span>
- <span data-ttu-id="93bb4-264">UseCurrentThread</span><span class="sxs-lookup"><span data-stu-id="93bb4-264">UseCurrentThread</span></span>
- <span data-ttu-id="93bb4-265">UseNewThread</span><span class="sxs-lookup"><span data-stu-id="93bb4-265">UseNewThread</span></span>

<span data-ttu-id="93bb4-266">默认值为 **UseCurrentThread** 。</span><span class="sxs-lookup"><span data-stu-id="93bb4-266">The default value is **UseCurrentThread**.</span></span>

<span data-ttu-id="93bb4-267">有关详细信息，请参阅 [PSThreadOptions 枚举](/dotnet/api/system.management.automation.runspaces.psthreadoptions?view=powershellsdk-1.1.0)。</span><span class="sxs-lookup"><span data-stu-id="93bb4-267">For more information, see [PSThreadOptions Enumeration](/dotnet/api/system.management.automation.runspaces.psthreadoptions?view=powershellsdk-1.1.0).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSThreadOptions
Parameter Sets: (All)
Aliases:
Accepted values: Default, UseNewThread, ReuseThread, UseCurrentThread

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93bb4-268">-TransportOption</span><span class="sxs-lookup"><span data-stu-id="93bb4-268">-TransportOption</span></span>

<span data-ttu-id="93bb4-269">指定传输选项。</span><span class="sxs-lookup"><span data-stu-id="93bb4-269">Specifies the transport option.</span></span>

<span data-ttu-id="93bb4-270">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="93bb4-270">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSTransportOption
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93bb4-271">-UseSharedProcess</span><span class="sxs-lookup"><span data-stu-id="93bb4-271">-UseSharedProcess</span></span>

<span data-ttu-id="93bb4-272">仅使用一个进程来托管由同一用户启动的所有会话，并使用相同的会话配置。</span><span class="sxs-lookup"><span data-stu-id="93bb4-272">Use only one process to host all sessions that are started by the same user and use the same session configuration.</span></span> <span data-ttu-id="93bb4-273">默认情况下，每个会话都托管在其自身进程中。</span><span class="sxs-lookup"><span data-stu-id="93bb4-273">By default, each session is hosted in its own process.</span></span>

<span data-ttu-id="93bb4-274">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="93bb4-274">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="93bb4-275">-Confirm</span><span class="sxs-lookup"><span data-stu-id="93bb4-275">-Confirm</span></span>

<span data-ttu-id="93bb4-276">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="93bb4-276">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="93bb4-277">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="93bb4-277">-WhatIf</span></span>

<span data-ttu-id="93bb4-278">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="93bb4-278">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="93bb4-279">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="93bb4-279">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="93bb4-280">-ThreadApartmentState</span><span class="sxs-lookup"><span data-stu-id="93bb4-280">-ThreadApartmentState</span></span>

<span data-ttu-id="93bb4-281">指定要使用的线程模块的单元状态。</span><span class="sxs-lookup"><span data-stu-id="93bb4-281">Specifies the apartment state of the threading module to be used.</span></span> <span data-ttu-id="93bb4-282">可接受的值为：</span><span class="sxs-lookup"><span data-stu-id="93bb4-282">Acceptable values are:</span></span>

- <span data-ttu-id="93bb4-283">未知</span><span class="sxs-lookup"><span data-stu-id="93bb4-283">Unknown</span></span>
- <span data-ttu-id="93bb4-284">MTA</span><span class="sxs-lookup"><span data-stu-id="93bb4-284">MTA</span></span>
- <span data-ttu-id="93bb4-285">STA</span><span class="sxs-lookup"><span data-stu-id="93bb4-285">STA</span></span>

```yaml
Type: System.Threading.ApartmentState
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93bb4-286">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="93bb4-286">CommonParameters</span></span>

<span data-ttu-id="93bb4-287">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="93bb4-287">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="93bb4-288">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="93bb4-288">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="93bb4-289">输入</span><span class="sxs-lookup"><span data-stu-id="93bb4-289">INPUTS</span></span>

### <span data-ttu-id="93bb4-290">None</span><span class="sxs-lookup"><span data-stu-id="93bb4-290">None</span></span>

<span data-ttu-id="93bb4-291">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="93bb4-291">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="93bb4-292">输出</span><span class="sxs-lookup"><span data-stu-id="93bb4-292">OUTPUTS</span></span>

### <span data-ttu-id="93bb4-293">WSManConfigContainerElement。</span><span class="sxs-lookup"><span data-stu-id="93bb4-293">Microsoft.WSMan.Management.WSManConfigContainerElement</span></span>

## <span data-ttu-id="93bb4-294">注释</span><span class="sxs-lookup"><span data-stu-id="93bb4-294">NOTES</span></span>

<span data-ttu-id="93bb4-295">此 cmdlet 仅在 Windows 平台上可用。</span><span class="sxs-lookup"><span data-stu-id="93bb4-295">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="93bb4-296">若要运行此 cmdlet，必须使用 "以 **管理员身份运行** " 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="93bb4-296">To run this cmdlet you must start PowerShell by using the **Run as administrator** option.</span></span>

<span data-ttu-id="93bb4-297">此 cmdlet 将生成表示 Web Services for Management (WS-MANAGEMENT) 插件配置的 XML，并将该 XML 发送到 WS-MANAGEMENT，后者将在本地计算机上注册该插件 (`New-Item wsman:\localhost\plugin`) 。</span><span class="sxs-lookup"><span data-stu-id="93bb4-297">This cmdlet generates XML that represents a Web Services for Management (WS-Management) plug-in configuration and sends the XML to WS-Management, which registers the plug-in on the local computer (`New-Item wsman:\localhost\plugin`).</span></span>

<span data-ttu-id="93bb4-298">会话配置对象的属性会根据为会话配置设置的选项以及这些选项的值而有所不同。</span><span class="sxs-lookup"><span data-stu-id="93bb4-298">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="93bb4-299">此外，使用会话配置文件的会话配置还具有其他属性。</span><span class="sxs-lookup"><span data-stu-id="93bb4-299">Also, session configurations that use a session configuration file have additional properties.</span></span>

## <span data-ttu-id="93bb4-300">相关链接</span><span class="sxs-lookup"><span data-stu-id="93bb4-300">RELATED LINKS</span></span>

[<span data-ttu-id="93bb4-301">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="93bb4-301">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="93bb4-302">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="93bb4-302">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="93bb4-303">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="93bb4-303">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="93bb4-304">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="93bb4-304">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="93bb4-305">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="93bb4-305">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="93bb4-306">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="93bb4-306">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="93bb4-307">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="93bb4-307">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="93bb4-308">WSMan 提供程序</span><span class="sxs-lookup"><span data-stu-id="93bb4-308">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="93bb4-309">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="93bb4-309">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="93bb4-310">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="93bb4-310">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
