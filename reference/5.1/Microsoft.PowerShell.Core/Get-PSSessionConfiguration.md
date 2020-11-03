---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessionconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionConfiguration
ms.openlocfilehash: 61eecfe344116389f4e278fa623f74f452f7622b
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "93198979"
---
# <span data-ttu-id="3c8be-103">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="3c8be-103">Get-PSSessionConfiguration</span></span>

## <span data-ttu-id="3c8be-104">摘要</span><span class="sxs-lookup"><span data-stu-id="3c8be-104">SYNOPSIS</span></span>
<span data-ttu-id="3c8be-105">获取计算机上已注册的会话配置。</span><span class="sxs-lookup"><span data-stu-id="3c8be-105">Gets the registered session configurations on the computer.</span></span>

## <span data-ttu-id="3c8be-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3c8be-106">SYNTAX</span></span>

```
Get-PSSessionConfiguration [[-Name] <String[]>] [-Force] [<CommonParameters>]
```

## <span data-ttu-id="3c8be-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3c8be-107">DESCRIPTION</span></span>

<span data-ttu-id="3c8be-108">该 `Get-PSSessionConfiguration` cmdlet 将获取已在本地计算机上注册的会话配置。</span><span class="sxs-lookup"><span data-stu-id="3c8be-108">The `Get-PSSessionConfiguration` cmdlet gets the session configurations that have been registered on the local computer.</span></span> <span data-ttu-id="3c8be-109">这是一个高级 cmdlet，旨在供系统管理员为其用户管理自定义会话配置时使用。</span><span class="sxs-lookup"><span data-stu-id="3c8be-109">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="3c8be-110">从 PowerShell 3.0 开始，你可以使用会话配置 (. .pssc) 文件来定义会话配置的属性。</span><span class="sxs-lookup"><span data-stu-id="3c8be-110">Beginning in PowerShell 3.0, you can define the properties of a session configuration by using a session configuration (.pssc) file.</span></span> <span data-ttu-id="3c8be-111">此功能允许你创建自定义和受限制的会话，而无需编写计算机程序。</span><span class="sxs-lookup"><span data-stu-id="3c8be-111">This feature lets you create customized and restricted sessions without writing a computer program.</span></span> <span data-ttu-id="3c8be-112">有关会话配置文件的详细信息，请参阅 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)。</span><span class="sxs-lookup"><span data-stu-id="3c8be-112">For more information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="3c8be-113">此外，从 PowerShell 3.0 开始，已将新的备注属性添加到了返回的会话配置对象中 `Get-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="3c8be-113">Also, beginning in PowerShell 3.0, new note properties have been added to the session configuration object that `Get-PSSessionConfiguration` returns.</span></span> <span data-ttu-id="3c8be-114">这些属性使用户和会话配置作者可以更轻松地检查和比较会话配置。</span><span class="sxs-lookup"><span data-stu-id="3c8be-114">These properties make it easier for users and session configuration authors to examine and compare session configurations.</span></span>

<span data-ttu-id="3c8be-115">若要创建和注册会话配置，请使用 `Register-PSSessionConfiguration` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3c8be-115">To create and register a session configuration, use the `Register-PSSessionConfiguration` cmdlet.</span></span>
<span data-ttu-id="3c8be-116">有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="3c8be-116">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

## <span data-ttu-id="3c8be-117">示例</span><span class="sxs-lookup"><span data-stu-id="3c8be-117">EXAMPLES</span></span>

### <span data-ttu-id="3c8be-118">示例 1-获取本地计算机上的会话配置</span><span class="sxs-lookup"><span data-stu-id="3c8be-118">Example 1 - Get session configurations on the local computer</span></span>

```powershell
Get-PSSessionConfiguration
```

### <span data-ttu-id="3c8be-119">示例 2-获取两个默认会话配置</span><span class="sxs-lookup"><span data-stu-id="3c8be-119">Example 2 - Get the two default session configurations</span></span>

<span data-ttu-id="3c8be-120">命令使用的 **Name** 参数 `Get-PSSessionConfiguration` 仅获取名称以 "Microsoft" 开头的会话配置。</span><span class="sxs-lookup"><span data-stu-id="3c8be-120">The command uses the **Name** parameter of `Get-PSSessionConfiguration` to get only the session configurations with names that begin with "Microsoft".</span></span>

```powershell
Get-PSSessionConfiguration -Name Microsoft*
```

```Output
Name                      PSVersion  StartupScript        Permission
----                      ---------  -------------        ----------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll...
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll...
```

### <span data-ttu-id="3c8be-121">示例 3-获取会话配置的属性和值</span><span class="sxs-lookup"><span data-stu-id="3c8be-121">Example 3 - Get the properties and values of a session configuration</span></span>

<span data-ttu-id="3c8be-122">本示例显示了使用会话配置文件创建的会话配置的属性和属性值。</span><span class="sxs-lookup"><span data-stu-id="3c8be-122">This example shows the properties and property values of a session configuration that was created by using a session configuration file.</span></span>

```powershell
Get-PSSessionConfiguration -Name Full  | Format-List -Property *
```

```Output
Copyright                     : (c) 2011 User01. All rights reserved.
AliasDefinitions              : {System.Collections.Hashtable}
SessionType                   : Default
CompanyName                   : Unknown
GUID                          : 1e9cb265-dae0-4bd3-89a9-8338a47698a1
Author                        : User01
ExecutionPolicy               : Restricted
SchemaVersion                 : 1.0.0.0
LanguageMode                  : FullLanguage
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/Full
MaxConcurrentCommandsPerShell : 1500
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 10
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
configfilepath                : C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 300
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
SDKVersion                    : 1
Name                          : Full
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 25
Enabled                       : True
MaxShellsPerUser              : 30
Permission                    :
```

<span data-ttu-id="3c8be-123">该示例使用 `Get-PSSessionConfiguration` cmdlet 来获取完整的会话配置。</span><span class="sxs-lookup"><span data-stu-id="3c8be-123">The example uses the `Get-PSSessionConfiguration` cmdlet to get the full session configuration.</span></span> <span data-ttu-id="3c8be-124">管道运算符将完整会话配置发送到 `Format-List` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3c8be-124">A pipeline operator sends the Full session configuration to the `Format-List` cmdlet.</span></span> <span data-ttu-id="3c8be-125">如果 **Property** 参数的值为 `*` (all) ，则 `Format-List` 指示在列表中显示该对象的所有属性和值。</span><span class="sxs-lookup"><span data-stu-id="3c8be-125">The **Property** parameter with a value of `*` (all) directs `Format-List` to display all the properties and values of the object in a list.</span></span>

<span data-ttu-id="3c8be-126">输出包含有用的信息，包括会话配置的作者、会话类型、语言模式和通过此会话配置创建的会话的执行策略、会话配额和会话配置文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="3c8be-126">The output includes useful information, including the author of the session configuration, the session type, language mode, and execution policy of sessions that are created with this session configuration, session quotas, and the full path to the session configuration file.</span></span>

<span data-ttu-id="3c8be-127">会话配置的此视图适用于包括会话配置文件的会话。</span><span class="sxs-lookup"><span data-stu-id="3c8be-127">This view of a session configuration is used for sessions that include a session configuration file.</span></span>
<span data-ttu-id="3c8be-128">有关会话配置文件的详细信息，请参阅 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)。</span><span class="sxs-lookup"><span data-stu-id="3c8be-128">For more information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

### <span data-ttu-id="3c8be-129">示例 4-查看会话配置的另一种方法</span><span class="sxs-lookup"><span data-stu-id="3c8be-129">Example 4 - Another way to look at the session configurations</span></span>

<span data-ttu-id="3c8be-130">此示例使用 `Get-ChildItem` `dir` WSMan： provider 驱动器中的 cmdlet (别名) 来查看插件节点的内容。</span><span class="sxs-lookup"><span data-stu-id="3c8be-130">This example uses the `Get-ChildItem` cmdlet (alias `dir`) in the WSMan: provider drive to look at the content of the Plugin node.</span></span> <span data-ttu-id="3c8be-131">这是在计算机上查看会话配置的另一种方式。</span><span class="sxs-lookup"><span data-stu-id="3c8be-131">This is another way to look at the session configurations on the computer.</span></span>

```powershell
dir wsman:\localhost\plugin
```

```Output
Type            Keys                                Name
----            ----                                ----
Container       {Name=Event Forwarding Plugin}      Event Forwarding Plugin
Container       {Name=Full}                         Full
Container       {Name=microsoft.powershell}         microsoft.powershell
Container       {Name=microsoft.powershell.workf... microsoft.powershell.workflow
Container       {Name=microsoft.powershell32}       microsoft.powershell32
Container       {Name=microsoft.ServerManager}      microsoft.ServerManager
Container       {Name=WMI Provider}                 WMI Provider
```

<span data-ttu-id="3c8be-132">" **插件** " 节点包含 **ContainerElement** 对象 (WSManConfigContainerElement) ，这些对象表示已注册的 POWERSHELL 会话配置以及 ws-management 的其他插件。</span><span class="sxs-lookup"><span data-stu-id="3c8be-132">The **PlugIn** node contains **ContainerElement** objects (Microsoft.WSMan.Management.WSManConfigContainerElement) that represent the registered PowerShell session configurations, along with other plug-ins for WS-Management.</span></span>

### <span data-ttu-id="3c8be-133">示例 6-查看远程计算机上的会话配置</span><span class="sxs-lookup"><span data-stu-id="3c8be-133">Example 6 - View session configurations on a remote computer</span></span>

<span data-ttu-id="3c8be-134">本示例显示了如何使用 WSMan 提供程序在远程计算机上查看会话配置。</span><span class="sxs-lookup"><span data-stu-id="3c8be-134">This example shows how to use the WSMan provider to view the session configurations on a remote computer.</span></span> <span data-ttu-id="3c8be-135">此方法并不提供任何信息作为 `Get-PSSessionConfiguration` 命令，但用户无需成为 Administrators 组的成员即可运行此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3c8be-135">This method does not provide as much information as a `Get-PSSessionConfiguration` command, but the user does not need to be a member of the Administrators group to run this cmdlet.</span></span>

```powershell
Connect-WSMan -ComputerName Server01
dir WSMan:\Server01\Plugin
```

```Output
   WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type            Keys                                Name
----            ----                                ----
Container       {Name=Empty}                        Empty
Container       {Name=Event Forwarding Plugin}      Event Forwarding Plugin
Container       {Name=Full}                         Full
Container       {Name=microsoft.powershell}         microsoft.powershell
Container       {Name=microsoft.powershell.workf... microsoft.powershell.workflow
Container       {Name=microsoft.powershell32}       microsoft.powershell32
Container       {Name=microsoft.ServerManager}      microsoft.ServerManager
Container       {Name=NoLanguage}                   NoLanguage
Container       {Name=RestrictedLang}               RestrictedLang
Container       {Name=RRS}                          RRS
Container       {Name=SEL Plugin}                   SEL Plugin
Container       {Name=WithProfile}                  WithProfile
Container       {Name=WMI Provider}                 WMI Provider
```

<span data-ttu-id="3c8be-136">`Connect-WSMan`Cmdlet 连接到 Server01 远程计算机上的 WinRM 服务。</span><span class="sxs-lookup"><span data-stu-id="3c8be-136">The `Connect-WSMan` cmdlet connects to the WinRM service on the Server01 remote computer.</span></span> <span data-ttu-id="3c8be-137">`Get-ChildItem`WSMan：驱动器的 cmdlet (别名 `dir`) 获取 **Server01\Plugin** 路径中的项。</span><span class="sxs-lookup"><span data-stu-id="3c8be-137">The `Get-ChildItem` cmdlet (alias `dir`) of the WSMan: drive gets the items in the **Server01\Plugin** path.</span></span> <span data-ttu-id="3c8be-138">该输出将显示 Server01 计算机上 Plugin 目录中的项。</span><span class="sxs-lookup"><span data-stu-id="3c8be-138">The output shows the items in the Plugin directory on the Server01 computer.</span></span> <span data-ttu-id="3c8be-139">这些项包括会话配置（WSMan 插件的一种类型）以及计算机上的其他插件类型。</span><span class="sxs-lookup"><span data-stu-id="3c8be-139">The items include the session configurations, which are a type of WSMan plug-in, along with other types of plug-ins on the computer.</span></span>

### <span data-ttu-id="3c8be-140">示例 7-从远程计算机获取详细的会话配置</span><span class="sxs-lookup"><span data-stu-id="3c8be-140">Example 7 - Get detailed session configurations from a remote computer</span></span>

<span data-ttu-id="3c8be-141">此示例演示如何 `Get-PSSessionConfiguration` 在远程计算机上运行命令。</span><span class="sxs-lookup"><span data-stu-id="3c8be-141">This example shows how to run a `Get-PSSessionConfiguration` command on a remote computer.</span></span> <span data-ttu-id="3c8be-142">该命令要求在本地计算机上的客户端设置和远程计算机的服务设置中启用 CredSSP 委派。</span><span class="sxs-lookup"><span data-stu-id="3c8be-142">The command requires that CredSSP delegation be enabled in the client settings on the local computer and in the service settings on the remote computer.</span></span>

<span data-ttu-id="3c8be-143">若要运行此示例中的命令，您必须是本地计算机和远程计算机上的 Administrators 组的成员，并且您必须使用 "以 **管理员身份运行** " 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3c8be-143">To run the commands in this example, you must be a member of the Administrators group on the local and remote computers and you must start PowerShell with the **Run as administrator** option.</span></span>

```powershell
Enable-WSManCredSSP -Delegate Server02
Connect-WSMan Server02
Set-Item WSMan:\Server02*\Service\Auth\CredSSP -Value $true
Invoke-Command -ScriptBlock {Get-PSSessionConfiguration} -ComputerName Server02 -Authentication CredSSP -Credential Domain01\Admin01
```

```Output
Name                      PSVersion  StartupScript        Permission                          PSComputerName
----                      ---------  -------------        ----------                          --------------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
MyX86Shell                5.1        c:\test\x86Shell.ps1 BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
```

<span data-ttu-id="3c8be-144">`Enable-WSManCredSSP`Cmdlet 可在本地计算机上的 Server01 上启用 **CredSSP** 委托。</span><span class="sxs-lookup"><span data-stu-id="3c8be-144">The `Enable-WSManCredSSP` cmdlet enables **CredSSP** delegation on Server01, the local computer.</span></span> <span data-ttu-id="3c8be-145">`Connect-WSMan`Cmdlet 连接到 Server02 计算机。</span><span class="sxs-lookup"><span data-stu-id="3c8be-145">The `Connect-WSMan` cmdlet connects to Server02 computer.</span></span> <span data-ttu-id="3c8be-146">此操作会将 Server02 的节点添加到本地计算机上的 WSMan：驱动器中，以便查看和更改 Server02 计算机上的 WS-Management 设置。</span><span class="sxs-lookup"><span data-stu-id="3c8be-146">This action adds a node for Server02 to the WSMan: drive on the local computer, allowing you to view and change the WS-Management settings on the Server02 computer.</span></span> <span data-ttu-id="3c8be-147">`Set-Item`Cmdlet 将 Server02 计算机的 Service 节点中的 **CredSSP** 项的值更改为 **True** 。</span><span class="sxs-lookup"><span data-stu-id="3c8be-147">The `Set-Item` cmdlet changes the value of the **CredSSP** item in the Service node of the Server02 computer to **True** .</span></span> <span data-ttu-id="3c8be-148">这会在远程计算机上配置服务设置。</span><span class="sxs-lookup"><span data-stu-id="3c8be-148">This configures the service settings on the remote computer.</span></span> <span data-ttu-id="3c8be-149">`Invoke-Command`Cmdlet `Get-PSSessionConfiguration` 在 Server02 计算机上运行命令。</span><span class="sxs-lookup"><span data-stu-id="3c8be-149">The `Invoke-Command` cmdlet runs the`Get-PSSessionConfiguration` command on the Server02 computer.</span></span> <span data-ttu-id="3c8be-150">该命令使用 **Credential** 参数，并使用值为 **CredSSP** 的 **Authentication** 参数。</span><span class="sxs-lookup"><span data-stu-id="3c8be-150">The command uses the **Credential** parameter, and it uses the **Authentication** parameter with a value of **CredSSP** .</span></span> <span data-ttu-id="3c8be-151">该输出显示 Server02 远程计算机上的会话配置。</span><span class="sxs-lookup"><span data-stu-id="3c8be-151">The output shows the session configurations on the Server02 remote computer.</span></span>

### <span data-ttu-id="3c8be-152">示例 8-获取会话配置的资源 URI</span><span class="sxs-lookup"><span data-stu-id="3c8be-152">Example 8 - Get the resource URI of a session configuration</span></span>

<span data-ttu-id="3c8be-153">此示例适用于设置 `$PSSessionConfigurationName` 首选项变量的值，后者采用资源 URI。</span><span class="sxs-lookup"><span data-stu-id="3c8be-153">This example is useful for setting the value of the `$PSSessionConfigurationName` preference variable, which takes a resource URI.</span></span>

```
(Get-PSSessionConfiguration -Name CustomShell).resourceURI
```

```Output
http://schemas.microsoft.com/powershell/microsoft.CustomShell
```

<span data-ttu-id="3c8be-154">`$PSSessionConfigurationName`变量指定在创建会话时使用的默认配置。</span><span class="sxs-lookup"><span data-stu-id="3c8be-154">The `$PSSessionConfigurationName` variable specifies the default configuration that is used when you create a session.</span></span> <span data-ttu-id="3c8be-155">此变量是在本地计算机上设置的，但是它可指定远程计算机上的配置。</span><span class="sxs-lookup"><span data-stu-id="3c8be-155">This variable is set on the local computer, but it specifies a configuration on the remote computer.</span></span> <span data-ttu-id="3c8be-156">有关变量的详细信息 `$PSSessionConfiguration` ，请参阅 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="3c8be-156">For more information about the `$PSSessionConfiguration` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="3c8be-157">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3c8be-157">PARAMETERS</span></span>

### <span data-ttu-id="3c8be-158">-Force</span><span class="sxs-lookup"><span data-stu-id="3c8be-158">-Force</span></span>

<span data-ttu-id="3c8be-159">如果该服务尚未运行，请取消显示提示以重新启动 WinRM 服务。</span><span class="sxs-lookup"><span data-stu-id="3c8be-159">Suppresses the prompt to restart the WinRM service, if the service is not already running.</span></span>

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

### <span data-ttu-id="3c8be-160">-Name</span><span class="sxs-lookup"><span data-stu-id="3c8be-160">-Name</span></span>

<span data-ttu-id="3c8be-161">仅获取具有指定名称或名称模式的会话配置。</span><span class="sxs-lookup"><span data-stu-id="3c8be-161">Gets only the session configurations with the specified name or name pattern.</span></span> <span data-ttu-id="3c8be-162">输入一个或多个会话配置名称。</span><span class="sxs-lookup"><span data-stu-id="3c8be-162">Enter one or more session configuration names.</span></span> <span data-ttu-id="3c8be-163">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="3c8be-163">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: All session configurations on the local computer
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="3c8be-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3c8be-164">CommonParameters</span></span>

<span data-ttu-id="3c8be-165">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3c8be-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3c8be-166">有关详细信息，请参阅 [about_CommonParameters](./About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="3c8be-166">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="3c8be-167">输入</span><span class="sxs-lookup"><span data-stu-id="3c8be-167">INPUTS</span></span>

### <span data-ttu-id="3c8be-168">无</span><span class="sxs-lookup"><span data-stu-id="3c8be-168">None</span></span>

<span data-ttu-id="3c8be-169">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3c8be-169">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="3c8be-170">输出</span><span class="sxs-lookup"><span data-stu-id="3c8be-170">OUTPUTS</span></span>

### <span data-ttu-id="3c8be-171">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="3c8be-171">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration</span></span>

## <span data-ttu-id="3c8be-172">注释</span><span class="sxs-lookup"><span data-stu-id="3c8be-172">NOTES</span></span>

- <span data-ttu-id="3c8be-173">若要运行此 cmdlet，请通过 "以 **管理员身份运行** " 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3c8be-173">To run this cmdlet, start PowerShell with the **Run as administrator** option.</span></span>

- <span data-ttu-id="3c8be-174">若要查看计算机上的会话配置，你必须是计算机上 Administrators 组的成员。</span><span class="sxs-lookup"><span data-stu-id="3c8be-174">To view the session configurations on the computer, you must be a member of the Administrators group on the computer.</span></span>

- <span data-ttu-id="3c8be-175">若要 `Get-PSSessionConfiguration` 在远程计算机上运行命令，则必须在本地计算机上的客户端设置中启用凭据安全服务提供程序 (CredSSP) 身份验证 (通过在 `Enable-WSManCredSSP` 远程计算机上使用 cmdlet) 和服务设置。</span><span class="sxs-lookup"><span data-stu-id="3c8be-175">To run a `Get-PSSessionConfiguration` command on a remote computer, Credential Security Service Provider (CredSSP) authentication must be enabled in the client settings on the local computer (by using the `Enable-WSManCredSSP` cmdlet) and in the service settings on the remote computer.</span></span> <span data-ttu-id="3c8be-176">此外，在建立远程会话时，必须使用 **Authentication** 参数的 **CredSSP** 值。</span><span class="sxs-lookup"><span data-stu-id="3c8be-176">Also, you must use the **CredSSP** value of the **Authentication** parameter when establishing the remote session.</span></span> <span data-ttu-id="3c8be-177">否则，访问将被拒绝。</span><span class="sxs-lookup"><span data-stu-id="3c8be-177">Otherwise, access is denied.</span></span>

- <span data-ttu-id="3c8be-178">`Get-PSSessionConfiguration`仅当对象具有值时，才会在该对象上显示该对象的注解属性。</span><span class="sxs-lookup"><span data-stu-id="3c8be-178">The note properties of the object that `Get-PSSessionConfiguration` returns appear on the object only when they have a value.</span></span> <span data-ttu-id="3c8be-179">只有使用会话配置文件创建的会话配置具有所有已定义的属性。</span><span class="sxs-lookup"><span data-stu-id="3c8be-179">Only session configurations that were created by using a session configuration file have all the defined properties.</span></span>

- <span data-ttu-id="3c8be-180">会话配置对象的属性会根据为会话配置设置的选项以及这些选项的值而有所不同。</span><span class="sxs-lookup"><span data-stu-id="3c8be-180">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="3c8be-181">此外，使用会话配置文件的会话配置还具有其他属性。</span><span class="sxs-lookup"><span data-stu-id="3c8be-181">Also, session configurations that use a session configuration file have additional properties.</span></span>

- <span data-ttu-id="3c8be-182">你可以使用 WSMan: 驱动器中的命令来更改会话配置的属性。</span><span class="sxs-lookup"><span data-stu-id="3c8be-182">You can use commands in the WSMan: drive to change the properties of session configurations.</span></span>
  <span data-ttu-id="3c8be-183">但是，不能使用 PowerShell 2.0 中的 WSMan：驱动器来更改 PowerShell 3.0 中引入的会话配置属性，如 **OutputBufferingMode** 。</span><span class="sxs-lookup"><span data-stu-id="3c8be-183">However, you cannot use the WSMan: drive in PowerShell 2.0 to change session configuration properties that are introduced in PowerShell 3.0, such as **OutputBufferingMode** .</span></span> <span data-ttu-id="3c8be-184">PowerShell 2.0 命令不会生成错误，但它们是无效的。</span><span class="sxs-lookup"><span data-stu-id="3c8be-184">PowerShell 2.0 commands do not generate an error, but they are ineffective.</span></span> <span data-ttu-id="3c8be-185">若要更改 PowerShell 3.0 中引入的属性，请使用 PowerShell 3.0 中的 WSMan：驱动器。</span><span class="sxs-lookup"><span data-stu-id="3c8be-185">To change properties introduced in PowerShell 3.0, use the WSMan: drive in PowerShell 3.0.</span></span>

## <span data-ttu-id="3c8be-186">相关链接</span><span class="sxs-lookup"><span data-stu-id="3c8be-186">RELATED LINKS</span></span>

[<span data-ttu-id="3c8be-187">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="3c8be-187">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="3c8be-188">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="3c8be-188">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="3c8be-189">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="3c8be-189">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="3c8be-190">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="3c8be-190">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="3c8be-191">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="3c8be-191">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="3c8be-192">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="3c8be-192">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="3c8be-193">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="3c8be-193">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="3c8be-194">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="3c8be-194">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="3c8be-195">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="3c8be-195">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="3c8be-196">WSMan 提供程序</span><span class="sxs-lookup"><span data-stu-id="3c8be-196">WSMan Provider</span></span>](../microsoft.wsman.management/about/about_WSMan_Provider.md)

[<span data-ttu-id="3c8be-197">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="3c8be-197">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="3c8be-198">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="3c8be-198">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
