---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-service?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Service
ms.openlocfilehash: 8c10e9e97c3371e8de46ed76e4c8a1195bc21513
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93198191"
---
# <span data-ttu-id="1f8ad-103">Get-Service</span><span class="sxs-lookup"><span data-stu-id="1f8ad-103">Get-Service</span></span>

## <span data-ttu-id="1f8ad-104">摘要</span><span class="sxs-lookup"><span data-stu-id="1f8ad-104">SYNOPSIS</span></span>
<span data-ttu-id="1f8ad-105">获取计算机上的服务。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-105">Gets the services on the computer.</span></span>

## <span data-ttu-id="1f8ad-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1f8ad-106">SYNTAX</span></span>

### <span data-ttu-id="1f8ad-107">Default（默认值）</span><span class="sxs-lookup"><span data-stu-id="1f8ad-107">Default (Default)</span></span>

```
Get-Service [[-Name] <String[]>] [-DependentServices] [-RequiredServices] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="1f8ad-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="1f8ad-108">DisplayName</span></span>

```
Get-Service [-DependentServices] [-RequiredServices] -DisplayName <String[]> [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="1f8ad-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="1f8ad-109">InputObject</span></span>

```
Get-Service [-DependentServices] [-RequiredServices] [-Include <String[]>] [-Exclude <String[]>]
 [-InputObject <ServiceController[]>] [<CommonParameters>]
```

## <span data-ttu-id="1f8ad-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1f8ad-110">DESCRIPTION</span></span>

<span data-ttu-id="1f8ad-111">该 `Get-Service` cmdlet 将获取表示计算机上的服务（包括正在运行和已停止的服务）的对象。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-111">The `Get-Service` cmdlet gets objects that represent the services on a computer, including running and stopped services.</span></span> <span data-ttu-id="1f8ad-112">默认情况下，在不带参数的情况下 `Get-Service` 运行时，将返回所有本地计算机的服务。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-112">By default, when `Get-Service` is run without parameters, all the local computer's services are returned.</span></span>

<span data-ttu-id="1f8ad-113">可以通过指定服务的服务名称或显示名称来指示此 cmdlet 仅获取特定服务，也可以通过管道将服务对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-113">You can direct this cmdlet to get only particular services by specifying the service name or the display name of the services, or you can pipe service objects to this cmdlet.</span></span>

## <span data-ttu-id="1f8ad-114">示例</span><span class="sxs-lookup"><span data-stu-id="1f8ad-114">EXAMPLES</span></span>

### <span data-ttu-id="1f8ad-115">示例1：获取计算机上的所有服务</span><span class="sxs-lookup"><span data-stu-id="1f8ad-115">Example 1: Get all services on the computer</span></span>

<span data-ttu-id="1f8ad-116">此示例将获取计算机上的所有服务。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-116">This example gets all of the services on the computer.</span></span> <span data-ttu-id="1f8ad-117">它的行为如同你键入 `Get-Service *` 的一样。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-117">It behaves as though you typed `Get-Service *`.</span></span> <span data-ttu-id="1f8ad-118">默认显示将显示每个服务的状态、服务名称和显示名称。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-118">The default display shows the status, service name, and display name of each service.</span></span>

```powershell
Get-Service
```

### <span data-ttu-id="1f8ad-119">示例2：获取以搜索字符串开头的服务</span><span class="sxs-lookup"><span data-stu-id="1f8ad-119">Example 2: Get services that begin with a search string</span></span>

<span data-ttu-id="1f8ad-120">此示例检索服务名称以 WMI (Windows Management Instrumentation) 开头的服务。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-120">This example retrieves services with service names that begin with WMI (Windows Management Instrumentation).</span></span>

```powershell
Get-Service "wmi*"
```

### <span data-ttu-id="1f8ad-121">示例3：显示包含搜索字符串的服务</span><span class="sxs-lookup"><span data-stu-id="1f8ad-121">Example 3: Display services that include a search string</span></span>

<span data-ttu-id="1f8ad-122">此示例显示显示名称包括 "网络" 的服务。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-122">This example displays services with a display name that includes the word network.</span></span> <span data-ttu-id="1f8ad-123">搜索显示名称会找到与网络相关的服务，即使服务名称不包括 Net （如 xmlprov），网络预配服务也是如此。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-123">Searching the display name finds network-related services even when the service name doesn't include Net, such as xmlprov, the Network Provisioning Service.</span></span>

```powershell
Get-Service -Displayname "*network*"
```

### <span data-ttu-id="1f8ad-124">示例4：获取以搜索字符串开头的服务和排除项</span><span class="sxs-lookup"><span data-stu-id="1f8ad-124">Example 4: Get services that begin with a search string and an exclusion</span></span>

<span data-ttu-id="1f8ad-125">此示例仅获取服务名称以 " **win** " 开头的服务（WinRM 服务除外）。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-125">This example only gets the services with service names that begin with **win** , except for the WinRM service.</span></span>

```powershell
Get-Service -Name "win*" -Exclude "WinRM"
```

### <span data-ttu-id="1f8ad-126">示例5：显示当前处于活动状态的服务</span><span class="sxs-lookup"><span data-stu-id="1f8ad-126">Example 5: Display services that are currently active</span></span>

<span data-ttu-id="1f8ad-127">此示例仅显示状态为 "正在运行" 的服务。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-127">This example displays only the services with a status of Running.</span></span>

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

<span data-ttu-id="1f8ad-128">`Get-Service` 获取计算机上的所有服务，并沿管道向下发送对象。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-128">`Get-Service` gets all the services on the computer and sends the objects down the pipeline.</span></span> <span data-ttu-id="1f8ad-129">`Where-Object`Cmdlet 仅选择 **状态** 属性等于 "正在运行" 的服务。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-129">The `Where-Object` cmdlet, selects only the services with a **Status** property that equals Running.</span></span>

<span data-ttu-id="1f8ad-130">Status 是服务对象的唯一属性。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-130">Status is only one property of service objects.</span></span> <span data-ttu-id="1f8ad-131">若要查看所有属性，请键入 `Get-Service | Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-131">To see all of the properties, type `Get-Service | Get-Member`.</span></span>

### <span data-ttu-id="1f8ad-132">示例6：列出计算机上具有依赖服务的服务</span><span class="sxs-lookup"><span data-stu-id="1f8ad-132">Example 6: List the services on the computer that have dependent services</span></span>

<span data-ttu-id="1f8ad-133">此示例获取具有依赖服务的服务。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-133">This example gets services that have dependent services.</span></span>

```powershell
Get-Service |
  Where-Object {$_.DependentServices} |
    Format-List -Property Name, DependentServices, @{
      Label="NoOfDependentServices"; Expression={$_.dependentservices.count}
    }
```

```Output
Name                  : AudioEndpointBuilder
DependentServices     : {AudioSrv}
NoOfDependentServices : 1

Name                  : Dhcp
DependentServices     : {WinHttpAutoProxySvc}
NoOfDependentServices : 1
...
```

<span data-ttu-id="1f8ad-134">该 `Get-Service` cmdlet 将获取计算机上的所有服务，并沿管道向下发送对象。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-134">The `Get-Service` cmdlet gets all the services on the computer and sends the objects down the pipeline.</span></span> <span data-ttu-id="1f8ad-135">`Where-Object`Cmdlet 将选择其 **DependentServices** 属性不为 null 的服务。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-135">The `Where-Object` cmdlet selects the services whose **DependentServices** property isn't null.</span></span>

<span data-ttu-id="1f8ad-136">结果将通过管道向下发送到 `Format-List` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-136">The results are sent down the pipeline to the `Format-List` cmdlet.</span></span> <span data-ttu-id="1f8ad-137">**Property** 参数显示服务的名称、依赖服务的名称以及显示每个服务的依赖服务数目的计算属性。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-137">The **Property** parameter displays the name of the service, the name of the dependent services, and a calculated property that displays the number of dependent services for each service.</span></span>

### <span data-ttu-id="1f8ad-138">示例7：按属性值对服务排序</span><span class="sxs-lookup"><span data-stu-id="1f8ad-138">Example 7: Sort services by property value</span></span>

<span data-ttu-id="1f8ad-139">此示例显示，当你按 **状态** 属性的值以升序对服务进行排序时，已停止的服务将显示在运行服务之前。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-139">This example shows that when you sort services in ascending order by the value of their **Status** property, stopped services appear before running services.</span></span> <span data-ttu-id="1f8ad-140">原因在于， **Status** 的值是一个枚举，其中，已停止的值为1，并且运行的值为4。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-140">The reason is because the value of **Status** is an enumeration, in which Stopped has a value of 1, and Running has a value of 4.</span></span> <span data-ttu-id="1f8ad-141">有关详细信息，请参阅 [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-141">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

<span data-ttu-id="1f8ad-142">若要首先列出正在运行的服务，请使用 cmdlet 的 **降序** 参数 `Sort-Object` 。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-142">To list running services first, use the **Descending** parameter of the `Sort-Object` cmdlet.</span></span>

```powershell
Get-Service "s*" | Sort-Object status
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  stisvc             Windows Image Acquisition (WIA)
Stopped  SwPrv              MS Software Shadow Copy Provider
Stopped  SysmonLog          Performance Logs and Alerts
Running  Spooler            Print Spooler
Running  srservice          System Restore Service
Running  SSDPSRV            SSDP Discovery Service
Running  ShellHWDetection   Shell Hardware Detection
Running  Schedule           Task Scheduler
Running  SCardSvr           Smart Card
Running  SamSs              Security Accounts Manager
Running  SharedAccess       Windows Firewall/Internet Connectio...
Running  SENS               System Event Notification
Running  seclogon           Secondary Logon
```

### <span data-ttu-id="1f8ad-143">示例8：获取服务的依赖服务</span><span class="sxs-lookup"><span data-stu-id="1f8ad-143">Example 8: Get the dependent services of a service</span></span>

<span data-ttu-id="1f8ad-144">此示例获取 WinRM 服务所需的服务。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-144">This example gets the services that the WinRM service requires.</span></span> <span data-ttu-id="1f8ad-145">返回该服务的 **ServicesDependedOn** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-145">The value of the service's **ServicesDependedOn** property is returned.</span></span>

```powershell
Get-Service "WinRM" -RequiredServices
```

### <span data-ttu-id="1f8ad-146">示例9：通过管道运算符获取服务</span><span class="sxs-lookup"><span data-stu-id="1f8ad-146">Example 9: Get a service through the pipeline operator</span></span>

<span data-ttu-id="1f8ad-147">此示例将获取本地计算机上的 WinRM 服务。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-147">This example gets the WinRM service on the local computer.</span></span> <span data-ttu-id="1f8ad-148">用引号引起来的服务名称字符串向下发送到 `Get-Service` 。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-148">The service name string, enclosed in quotation marks, is sent down the pipeline to `Get-Service`.</span></span>

```powershell
"WinRM" | Get-Service
```

## <span data-ttu-id="1f8ad-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1f8ad-149">PARAMETERS</span></span>

### <span data-ttu-id="1f8ad-150">-DependentServices</span><span class="sxs-lookup"><span data-stu-id="1f8ad-150">-DependentServices</span></span>

<span data-ttu-id="1f8ad-151">指示此 cmdlet 仅获取依赖于指定服务的服务。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-151">Indicates that this cmdlet gets only the services that depend upon the specified service.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: DS

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1f8ad-152">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="1f8ad-152">-DisplayName</span></span>

<span data-ttu-id="1f8ad-153">指定作为字符串数组，要检索的服务的显示名称。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-153">Specifies, as a string array, the display names of services to be retrieved.</span></span> <span data-ttu-id="1f8ad-154">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-154">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DisplayName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="1f8ad-155">-Exclude</span><span class="sxs-lookup"><span data-stu-id="1f8ad-155">-Exclude</span></span>

<span data-ttu-id="1f8ad-156">指定为字符串数组、此 cmdlet 从操作中排除的一个或一组服务。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-156">Specifies, as a string array, a service or services that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="1f8ad-157">此参数值使 **Name** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-157">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="1f8ad-158">输入名称元素或模式，例如 `s*` 。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-158">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="1f8ad-159">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-159">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="1f8ad-160">-Include</span><span class="sxs-lookup"><span data-stu-id="1f8ad-160">-Include</span></span>

<span data-ttu-id="1f8ad-161">指定为字符串数组、此 cmdlet 包含在操作中的一个或一项服务。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-161">Specifies, as a string array, a service or services that this cmdlet includes in the operation.</span></span> <span data-ttu-id="1f8ad-162">此参数值使 **Name** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-162">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="1f8ad-163">输入名称元素或模式，例如 `s*` 。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-163">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="1f8ad-164">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-164">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="1f8ad-165">-InputObject</span><span class="sxs-lookup"><span data-stu-id="1f8ad-165">-InputObject</span></span>

<span data-ttu-id="1f8ad-166">指定表示要检索的服务的 **ServiceController** 对象。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-166">Specifies **ServiceController** objects representing the services to be retrieved.</span></span> <span data-ttu-id="1f8ad-167">输入一个包含对象的变量，或键入可获取对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-167">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="1f8ad-168">可以通过管道将服务对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-168">You can pipe a service object to this cmdlet.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1f8ad-169">-Name</span><span class="sxs-lookup"><span data-stu-id="1f8ad-169">-Name</span></span>

<span data-ttu-id="1f8ad-170">指定要检索的服务的名称。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-170">Specifies the service names of services to be retrieved.</span></span> <span data-ttu-id="1f8ad-171">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-171">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="1f8ad-172">-RequiredServices</span><span class="sxs-lookup"><span data-stu-id="1f8ad-172">-RequiredServices</span></span>

<span data-ttu-id="1f8ad-173">指示此 cmdlet 仅获取此服务所需的服务。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-173">Indicates that this cmdlet gets only the services that this service requires.</span></span> <span data-ttu-id="1f8ad-174">此参数获取服务的 **ServicesDependedOn** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-174">This parameter gets the value of the **ServicesDependedOn** property of the service.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SDO, ServicesDependedOn

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="1f8ad-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1f8ad-175">CommonParameters</span></span>

<span data-ttu-id="1f8ad-176">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1f8ad-177">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1f8ad-178">输入</span><span class="sxs-lookup"><span data-stu-id="1f8ad-178">INPUTS</span></span>

### <span data-ttu-id="1f8ad-179">System.ServiceProcess.ServiceController、System.String</span><span class="sxs-lookup"><span data-stu-id="1f8ad-179">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="1f8ad-180">可以通过管道将服务对象或服务名称传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-180">You can pipe a service object or a service name to this cmdlet.</span></span>

## <span data-ttu-id="1f8ad-181">输出</span><span class="sxs-lookup"><span data-stu-id="1f8ad-181">OUTPUTS</span></span>

### <span data-ttu-id="1f8ad-182">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="1f8ad-182">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="1f8ad-183">此 cmdlet 将返回表示计算机上的服务的对象。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-183">This cmdlet returns objects that represent the services on the computer.</span></span>

## <span data-ttu-id="1f8ad-184">注释</span><span class="sxs-lookup"><span data-stu-id="1f8ad-184">NOTES</span></span>

<span data-ttu-id="1f8ad-185">从 PowerShell 6.0 开始，将以下属性添加到 **ServiceController** 对象： **UserName** 、 **Description** 、 **DelayedAutoStart** 、 **BinaryPathName** 和 **StartupType** 。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-185">Beginning in PowerShell 6.0, the following properties are added to the **ServiceController** objects: **UserName** , **Description** , **DelayedAutoStart** , **BinaryPathName** , and **StartupType** .</span></span>

<span data-ttu-id="1f8ad-186">还可以 `Get-Service` 通过其内置别名来引用 `gsv` 。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-186">You can also refer to `Get-Service` by its built-in alias, `gsv`.</span></span> <span data-ttu-id="1f8ad-187">有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-187">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="1f8ad-188">此 cmdlet 只能在当前用户有权查看服务时显示服务。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-188">This cmdlet can display services only when the current user has permission to see them.</span></span> <span data-ttu-id="1f8ad-189">如果此 cmdlet 未显示服务，则你可能没有查看它们的权限。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-189">If this cmdlet does not display services, you might not have permission to see them.</span></span>

<span data-ttu-id="1f8ad-190">若要在系统中查找每个服务的服务名称和显示名称，请键入 `Get-Service` 。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-190">To find the service name and display name of each service on your system, type `Get-Service`.</span></span> <span data-ttu-id="1f8ad-191">服务名称显示在 "名称" 列中，显示名称显示在 **DisplayName** 列中。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-191">The service names appear in the Name column, and the display names appear in the **DisplayName** column.</span></span>

<span data-ttu-id="1f8ad-192">如果按 **状态** 属性的值按升序排序，停止的服务将显示在运行服务之前。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-192">When you sort in ascending order by the **Status** property's value, Stopped services appear before Running services.</span></span> <span data-ttu-id="1f8ad-193">服务的 **status** 属性是一个枚举值，状态名称表示整数值。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-193">The service's **Status** property is an enumerated value and the status names represent integer values.</span></span> <span data-ttu-id="1f8ad-194">排序顺序取决于整数值，而不是名称。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-194">The sort order is based on the integer value, not the name.</span></span> <span data-ttu-id="1f8ad-195">已停止出现，因为运行，因为停止的值为1，并且运行的值为4。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-195">Stopped appears before because Running because Stopped has a value of 1, and Running has a value of 4.</span></span> <span data-ttu-id="1f8ad-196">有关详细信息，请参阅 [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)。</span><span class="sxs-lookup"><span data-stu-id="1f8ad-196">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

## <span data-ttu-id="1f8ad-197">相关链接</span><span class="sxs-lookup"><span data-stu-id="1f8ad-197">RELATED LINKS</span></span>

[<span data-ttu-id="1f8ad-198">New-Service</span><span class="sxs-lookup"><span data-stu-id="1f8ad-198">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="1f8ad-199">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="1f8ad-199">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="1f8ad-200">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="1f8ad-200">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="1f8ad-201">Set-Service</span><span class="sxs-lookup"><span data-stu-id="1f8ad-201">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="1f8ad-202">Start-Service</span><span class="sxs-lookup"><span data-stu-id="1f8ad-202">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="1f8ad-203">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="1f8ad-203">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="1f8ad-204">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="1f8ad-204">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="1f8ad-205">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="1f8ad-205">Remove-Service</span></span>](Remove-Service.md)