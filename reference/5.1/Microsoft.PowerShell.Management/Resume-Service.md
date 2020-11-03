---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resume-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Service
ms.openlocfilehash: c90c9fcaca3a003d46b41a7ff8b9901079c9f134
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93198046"
---
# <span data-ttu-id="baadc-103">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="baadc-103">Resume-Service</span></span>

## <span data-ttu-id="baadc-104">摘要</span><span class="sxs-lookup"><span data-stu-id="baadc-104">SYNOPSIS</span></span>
<span data-ttu-id="baadc-105">恢复一项或多项挂起（暂停的）服务。</span><span class="sxs-lookup"><span data-stu-id="baadc-105">Resumes one or more suspended (paused) services.</span></span>

## <span data-ttu-id="baadc-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="baadc-106">SYNTAX</span></span>

### <span data-ttu-id="baadc-107">InputObject（默认值）</span><span class="sxs-lookup"><span data-stu-id="baadc-107">InputObject (Default)</span></span>

```
Resume-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="baadc-108">默认</span><span class="sxs-lookup"><span data-stu-id="baadc-108">Default</span></span>

```
Resume-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="baadc-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="baadc-109">DisplayName</span></span>

```
Resume-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="baadc-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="baadc-110">DESCRIPTION</span></span>

<span data-ttu-id="baadc-111">对于每个指定的服务， **Resume Service** cmdlet 都向 Windows 服务控制器发送一条恢复消息。</span><span class="sxs-lookup"><span data-stu-id="baadc-111">The **Resume-Service** cmdlet sends a resume message to the Windows Service Controller for each of the specified services.</span></span>
<span data-ttu-id="baadc-112">如果服务已挂起，则会恢复。</span><span class="sxs-lookup"><span data-stu-id="baadc-112">If a service is suspended, it resumes.</span></span>
<span data-ttu-id="baadc-113">如果当前正在运行，则忽略该消息。</span><span class="sxs-lookup"><span data-stu-id="baadc-113">If it is currently running, the message is ignored.</span></span>
<span data-ttu-id="baadc-114">你可以通过服务名称或显示名称来指定服务，也可以使用 *InputObject* 参数传递表示要恢复的服务的服务对象。</span><span class="sxs-lookup"><span data-stu-id="baadc-114">You can specify the services by their service names or display names, or you can use the *InputObject* parameter to pass a service object that represents the services that you want to resume.</span></span>

## <span data-ttu-id="baadc-115">示例</span><span class="sxs-lookup"><span data-stu-id="baadc-115">EXAMPLES</span></span>

### <span data-ttu-id="baadc-116">示例1：在本地计算机上恢复服务</span><span class="sxs-lookup"><span data-stu-id="baadc-116">Example 1: Resume a service on the local computer</span></span>

```
PS C:\> Resume-Service "sens"
```

<span data-ttu-id="baadc-117">此命令在本地计算机上恢复系统事件通知服务。</span><span class="sxs-lookup"><span data-stu-id="baadc-117">This command resumes the System Event Notification service  on the local computer.</span></span>
<span data-ttu-id="baadc-118">服务名称在命令中由 sens 表示。</span><span class="sxs-lookup"><span data-stu-id="baadc-118">The service name is represented in the command by sens.</span></span>
<span data-ttu-id="baadc-119">该命令使用 *name* 参数来指定服务的服务名称，但该命令省略了参数名称，因为参数名称是可选的。</span><span class="sxs-lookup"><span data-stu-id="baadc-119">The command uses the *Name* parameter to specify the service name of the service, but the command omits the parameter name because the parameter name is optional.</span></span>

### <span data-ttu-id="baadc-120">示例2：恢复所有挂起的服务</span><span class="sxs-lookup"><span data-stu-id="baadc-120">Example 2: Resume all suspended services</span></span>

```
PS C:\> Get-Service | Where-Object {$_.Status -eq "Paused"} | Resume-Service
```

<span data-ttu-id="baadc-121">此命令恢复计算机上所有挂起的服务。</span><span class="sxs-lookup"><span data-stu-id="baadc-121">This command resumes all of the suspended  services on the computer.</span></span>
<span data-ttu-id="baadc-122">Get-Service cmdlet 命令获取计算机上的所有服务。</span><span class="sxs-lookup"><span data-stu-id="baadc-122">The Get-Service cmdlet command gets all of the services on the computer.</span></span>
<span data-ttu-id="baadc-123">管道运算符 (|) 将结果传递给 Where-Object cmdlet，该 cmdlet 选择 **状态** 属性为 "已暂停" 的服务。</span><span class="sxs-lookup"><span data-stu-id="baadc-123">The pipeline operator (|) passes the results to the Where-Object cmdlet, which selects the services that have a **Status** property of Paused.</span></span>
<span data-ttu-id="baadc-124">下一个管道运算符将结果发送到 **Resume 服务** ，后者将恢复暂停的服务。</span><span class="sxs-lookup"><span data-stu-id="baadc-124">The next pipeline operator sends the results to **Resume-Service** , which resumes the paused services.</span></span>

<span data-ttu-id="baadc-125">在实际操作中，你将使用 *WhatIf* 参数来确定该命令的影响，然后再运行该命令。</span><span class="sxs-lookup"><span data-stu-id="baadc-125">In practice, you would use the *WhatIf* parameter to determine the effect of the command before you run it.</span></span>

## <span data-ttu-id="baadc-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="baadc-126">PARAMETERS</span></span>

### <span data-ttu-id="baadc-127">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="baadc-127">-DisplayName</span></span>

<span data-ttu-id="baadc-128">指定要恢复的服务的显示名称。</span><span class="sxs-lookup"><span data-stu-id="baadc-128">Specifies the display names of the services to be resumed.</span></span>
<span data-ttu-id="baadc-129">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="baadc-129">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="baadc-130">-Exclude</span><span class="sxs-lookup"><span data-stu-id="baadc-130">-Exclude</span></span>

<span data-ttu-id="baadc-131">指定此 cmdlet 省略的服务。</span><span class="sxs-lookup"><span data-stu-id="baadc-131">Specifies services that this cmdlet omits.</span></span>
<span data-ttu-id="baadc-132">此参数值使 *Name* 参数有效。</span><span class="sxs-lookup"><span data-stu-id="baadc-132">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="baadc-133">输入名称元素或模式，例如 "s \*"。</span><span class="sxs-lookup"><span data-stu-id="baadc-133">Enter a name element or pattern, such as s\*.</span></span>
<span data-ttu-id="baadc-134">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="baadc-134">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="baadc-135">-Include</span><span class="sxs-lookup"><span data-stu-id="baadc-135">-Include</span></span>

<span data-ttu-id="baadc-136">指定要恢复的服务。</span><span class="sxs-lookup"><span data-stu-id="baadc-136">Specifies services to resume.</span></span>
<span data-ttu-id="baadc-137">此参数的值限定 *Name* 参数。</span><span class="sxs-lookup"><span data-stu-id="baadc-137">The value of this parameter qualifies *Name* parameter.</span></span>
<span data-ttu-id="baadc-138">输入名称元素或模式，例如 "s \*"。</span><span class="sxs-lookup"><span data-stu-id="baadc-138">Enter a name element or pattern, such as s\*.</span></span>
<span data-ttu-id="baadc-139">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="baadc-139">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="baadc-140">-InputObject</span><span class="sxs-lookup"><span data-stu-id="baadc-140">-InputObject</span></span>

<span data-ttu-id="baadc-141">指定表示要恢复的服务的 **ServiceController** 对象。</span><span class="sxs-lookup"><span data-stu-id="baadc-141">Specifies **ServiceController** objects that represent the services to resumed.</span></span>
<span data-ttu-id="baadc-142">输入一个包含对象的变量，或键入可获取对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="baadc-142">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="baadc-143">-Name</span><span class="sxs-lookup"><span data-stu-id="baadc-143">-Name</span></span>

<span data-ttu-id="baadc-144">指定要恢复的服务的服务名称。</span><span class="sxs-lookup"><span data-stu-id="baadc-144">Specifies the service names of the services to be resumed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="baadc-145">-PassThru</span><span class="sxs-lookup"><span data-stu-id="baadc-145">-PassThru</span></span>

<span data-ttu-id="baadc-146">返回一个表示服务的对象。</span><span class="sxs-lookup"><span data-stu-id="baadc-146">Returns an object that represents the service.</span></span>
<span data-ttu-id="baadc-147">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="baadc-147">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="baadc-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="baadc-148">-Confirm</span></span>

<span data-ttu-id="baadc-149">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="baadc-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="baadc-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="baadc-150">-WhatIf</span></span>

<span data-ttu-id="baadc-151">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="baadc-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="baadc-152">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="baadc-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="baadc-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="baadc-153">CommonParameters</span></span>

<span data-ttu-id="baadc-154">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="baadc-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="baadc-155">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="baadc-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="baadc-156">输入</span><span class="sxs-lookup"><span data-stu-id="baadc-156">INPUTS</span></span>

### <span data-ttu-id="baadc-157">System.ServiceProcess.ServiceController、System.String</span><span class="sxs-lookup"><span data-stu-id="baadc-157">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="baadc-158">可以通过管道将服务对象或包含服务名称的字符串传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="baadc-158">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="baadc-159">输出</span><span class="sxs-lookup"><span data-stu-id="baadc-159">OUTPUTS</span></span>

### <span data-ttu-id="baadc-160">无、System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="baadc-160">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="baadc-161">如果指定 *PassThru* 参数，则此 cmdlet 将生成表示已恢复服务的 **ServiceController** 对象。</span><span class="sxs-lookup"><span data-stu-id="baadc-161">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the resumed service, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="baadc-162">否则，此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="baadc-162">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="baadc-163">注释</span><span class="sxs-lookup"><span data-stu-id="baadc-163">NOTES</span></span>

* <span data-ttu-id="baadc-164">已暂停的服务的状态为 "已暂停"。</span><span class="sxs-lookup"><span data-stu-id="baadc-164">The status of services that have been suspended is Paused.</span></span> <span data-ttu-id="baadc-165">当服务恢复后，其状态为 "正在运行"。</span><span class="sxs-lookup"><span data-stu-id="baadc-165">When services are resumed, their status is Running.</span></span>
* <span data-ttu-id="baadc-166">**Resume-** 仅当当前用户有权执行此操作时，服务才能控制服务。</span><span class="sxs-lookup"><span data-stu-id="baadc-166">**Resume-Service** can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="baadc-167">如果某个命令不能正常工作，则可能你不具有所需的权限。</span><span class="sxs-lookup"><span data-stu-id="baadc-167">If a command does not work correctly, you might not have the required permissions.</span></span>
* <span data-ttu-id="baadc-168">若要查找服务名称并显示系统中的服务名称，请键入 `Get-Service`。</span><span class="sxs-lookup"><span data-stu-id="baadc-168">To find the service names and display names of the services on your system, type `Get-Service`.</span></span> <span data-ttu-id="baadc-169">服务名称显示在 " **名称** " 列中，显示名称显示在 **DisplayName** 列中。</span><span class="sxs-lookup"><span data-stu-id="baadc-169">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="baadc-170">相关链接</span><span class="sxs-lookup"><span data-stu-id="baadc-170">RELATED LINKS</span></span>

[<span data-ttu-id="baadc-171">Get-Service</span><span class="sxs-lookup"><span data-stu-id="baadc-171">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="baadc-172">New-Service</span><span class="sxs-lookup"><span data-stu-id="baadc-172">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="baadc-173">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="baadc-173">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="baadc-174">Set-Service</span><span class="sxs-lookup"><span data-stu-id="baadc-174">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="baadc-175">Start-Service</span><span class="sxs-lookup"><span data-stu-id="baadc-175">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="baadc-176">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="baadc-176">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="baadc-177">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="baadc-177">Suspend-Service</span></span>](Suspend-Service.md)
