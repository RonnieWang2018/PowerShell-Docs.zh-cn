---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSession
ms.openlocfilehash: aa6965b3a21c145ecccb284d43c6d0913bb31027
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2020
ms.locfileid: "93196900"
---
# <span data-ttu-id="4d87a-103">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="4d87a-103">Remove-PSSession</span></span>

## <span data-ttu-id="4d87a-104">摘要</span><span class="sxs-lookup"><span data-stu-id="4d87a-104">SYNOPSIS</span></span>
<span data-ttu-id="4d87a-105"> (Pssession) 关闭一个或多个 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="4d87a-105">Closes one or more PowerShell sessions (PSSessions).</span></span>

## <span data-ttu-id="4d87a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4d87a-106">SYNTAX</span></span>

### <span data-ttu-id="4d87a-107">ID（默认值）</span><span class="sxs-lookup"><span data-stu-id="4d87a-107">Id (Default)</span></span>

```
Remove-PSSession [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4d87a-108">会话</span><span class="sxs-lookup"><span data-stu-id="4d87a-108">Session</span></span>

```
Remove-PSSession [-Session] <PSSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4d87a-109">ContainerId</span><span class="sxs-lookup"><span data-stu-id="4d87a-109">ContainerId</span></span>

```
Remove-PSSession -ContainerId <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4d87a-110">VMId</span><span class="sxs-lookup"><span data-stu-id="4d87a-110">VMId</span></span>

```
Remove-PSSession -VMId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4d87a-111">VMName</span><span class="sxs-lookup"><span data-stu-id="4d87a-111">VMName</span></span>

```
Remove-PSSession -VMName <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4d87a-112">InstanceId</span><span class="sxs-lookup"><span data-stu-id="4d87a-112">InstanceId</span></span>

```
Remove-PSSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4d87a-113">名称</span><span class="sxs-lookup"><span data-stu-id="4d87a-113">Name</span></span>

```
Remove-PSSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4d87a-114">计算机名</span><span class="sxs-lookup"><span data-stu-id="4d87a-114">ComputerName</span></span>

```
Remove-PSSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4d87a-115">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4d87a-115">DESCRIPTION</span></span>

<span data-ttu-id="4d87a-116">Pssession **cmdlet 将** 关闭当前会话中 (**PSSessions**) 的 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="4d87a-116">The **Remove-PSSession** cmdlet closes PowerShell sessions (**PSSessions**) in the current session.</span></span>
<span data-ttu-id="4d87a-117">它将停止在 **PSSession** 中运行的任何命令、结束 **PSSession**，并释放 **PSSession** 使用的资源。</span><span class="sxs-lookup"><span data-stu-id="4d87a-117">It stops any commands that are running in the **PSSessions**, ends the **PSSession**, and releases the resources that the **PSSession** was using.</span></span>
<span data-ttu-id="4d87a-118">如果 **PSSession** 连接到远程计算机，则此 cmdlet 还会关闭本地计算机和远程计算机之间的连接。</span><span class="sxs-lookup"><span data-stu-id="4d87a-118">If the **PSSession** is connected to a remote computer, this cmdlet also closes the connection between the local and remote computers.</span></span>

<span data-ttu-id="4d87a-119">若要删除 **PSSession**，请输入会话的 Name、ComputerName、ID 或 InstanceID。</span><span class="sxs-lookup"><span data-stu-id="4d87a-119">To remove a **PSSession**, enter the *Name*, *ComputerName*, *ID*, or *InstanceID* of the session.</span></span>

<span data-ttu-id="4d87a-120">如果你已将 PSSession 保存在变量中，则会话对象将保留在该变量中，但 PSSession 的状态为 Closed。</span><span class="sxs-lookup"><span data-stu-id="4d87a-120">If you have saved the *PSSession* in a variable, the session object remains in the variable, but the state of the *PSSession* is Closed.</span></span>

## <span data-ttu-id="4d87a-121">示例</span><span class="sxs-lookup"><span data-stu-id="4d87a-121">EXAMPLES</span></span>

### <span data-ttu-id="4d87a-122">示例 1：使用 ID 删除会话</span><span class="sxs-lookup"><span data-stu-id="4d87a-122">Example 1: Remove sessions by using IDs</span></span>

```powershell
Remove-PSSession -Id 1, 2
```

<span data-ttu-id="4d87a-123">此命令将删除具有 ID 1 和 2 的 **PSSession**。</span><span class="sxs-lookup"><span data-stu-id="4d87a-123">This command removes the **PSSessions** that have IDs 1 and 2.</span></span>

### <span data-ttu-id="4d87a-124">示例 2：删除当前会话中的所有会话</span><span class="sxs-lookup"><span data-stu-id="4d87a-124">Example 2: Remove all the sessions in the current session</span></span>

```powershell
Get-PSSession | Remove-PSSession
Remove-PSSession -Session (Get-PSSession)
$s = Get-PSSession
Remove-PSSession -Session $s
```

<span data-ttu-id="4d87a-125">这些命令将删除当前会话中的所有 **PSSession**。</span><span class="sxs-lookup"><span data-stu-id="4d87a-125">These commands remove all of the **PSSessions** in the current session.</span></span>
<span data-ttu-id="4d87a-126">虽然这三个命令格式看起来不同，但它们具有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="4d87a-126">Although the three command formats look different, they have the same effect.</span></span>

### <span data-ttu-id="4d87a-127">示例 3：使用名称关闭会话</span><span class="sxs-lookup"><span data-stu-id="4d87a-127">Example 3: Close sessions by using names</span></span>

```powershell
$r = Get-PSSession -ComputerName Serv*
$r | Remove-PSSession
```

<span data-ttu-id="4d87a-128">这些命令将关闭连接到名称以 Serv 开头的计算机的 **PSSession**。</span><span class="sxs-lookup"><span data-stu-id="4d87a-128">These commands close the **PSSessions** that are connected to computers that have names that begin with Serv.</span></span>

### <span data-ttu-id="4d87a-129">示例 4：关闭连接到某个端口的会话</span><span class="sxs-lookup"><span data-stu-id="4d87a-129">Example 4: Close sessions connected to a port</span></span>

```powershell
Get-PSSession | where {$_.port -eq 90} | Remove-PSSession
```

<span data-ttu-id="4d87a-130">此命令将关闭连接到端口 90 的 **PSSession**。</span><span class="sxs-lookup"><span data-stu-id="4d87a-130">This command closes the **PSSessions** that are connected to port 90.</span></span>
<span data-ttu-id="4d87a-131">你可以使用此命令格式，通过 ComputerName、Name、InstanceID 和 ID 以外的属性标识 **PSSession**。</span><span class="sxs-lookup"><span data-stu-id="4d87a-131">You can use this command format to identify **PSSessions** by properties other than *ComputerName*, *Name*, *InstanceID*, and *ID*.</span></span>

### <span data-ttu-id="4d87a-132">示例 5：基于实例 ID 关闭会话</span><span class="sxs-lookup"><span data-stu-id="4d87a-132">Example 5: Close a session based on instance ID</span></span>

```powershell
Get-PSSession | Format-Table ComputerName, InstanceID  -AutoSize
```

```Output
ComputerName InstanceId
------------ ----------------
Server01     875d231b-2788-4f36-9f67-2e50d63bb82a
localhost    c065ffa0-02c4-406e-84a3-dacb0d677868
Server02     4699cdbc-61d5-4e0d-b916-84f82ebede1f
Server03     4e5a3245-4c63-43e4-88d0-a7798bfc2414
TX-TEST-01   fc4e9dfa-f246-452d-9fa3-1adbdd64ae85 PS C:\> Remove-PSSession -InstanceID fc4e9dfa-f246-452d-9fa3-1adbdd64ae85
```

<span data-ttu-id="4d87a-133">这些命令显示了如何基于其实例 ID（或 **RemoteRunspaceID**）关闭 **PSSession**。</span><span class="sxs-lookup"><span data-stu-id="4d87a-133">These commands show how to close a **PSSession** based on its instance ID, or **RemoteRunspaceID**.</span></span>

<span data-ttu-id="4d87a-134">第一个命令使用 **Get-PSSession** cmdlet 来获取当前会话中的 **PSSession**。</span><span class="sxs-lookup"><span data-stu-id="4d87a-134">The first command uses the **Get-PSSession** cmdlet to get the **PSSessions** in the current session.</span></span>
<span data-ttu-id="4d87a-135">它使用管道运算符 (|) 将 **PSSession** 发送到 Format-Table cmdlet，后者将在表格中设置其 **ComputerName** 和 **InstanceID** 属性的格式。</span><span class="sxs-lookup"><span data-stu-id="4d87a-135">It uses a pipeline operator (|) to send the **PSSessions** to the Format-Table cmdlet, which formats their **ComputerName** and **InstanceID** properties in a table.</span></span>
<span data-ttu-id="4d87a-136">*AutoSize* 参数将压缩列以供显示。</span><span class="sxs-lookup"><span data-stu-id="4d87a-136">The *AutoSize* parameter compresses the columns for display.</span></span>

<span data-ttu-id="4d87a-137">从生成的显示内容中，可以标识要关闭的 **PSSession**，并将该 **PSSession** 的 InstanceID 复制和粘贴到第二个命令中。</span><span class="sxs-lookup"><span data-stu-id="4d87a-137">From the resulting display, you can identify the **PSSession** to be closed, and copy and paste the *InstanceID* of that **PSSession** into the second command.</span></span>

<span data-ttu-id="4d87a-138">第二个命令使用 **Remove-PSSession** cmdlet 删除具有指定实例 ID 的 PSSession。</span><span class="sxs-lookup"><span data-stu-id="4d87a-138">The second command uses the **Remove-PSSession** cmdlet to remove the *PSSession* with the specified instance ID.</span></span>

### <span data-ttu-id="4d87a-139">示例 6：创建删除当前会话中的所有会话的函数</span><span class="sxs-lookup"><span data-stu-id="4d87a-139">Example 6: Create a function that deletes all sessions in the current session</span></span>

```powershell
Function EndPSS { Get-PSSession | Remove-PSSession }
```

<span data-ttu-id="4d87a-140">此函数将删除当前会话中的所有 **PSSession**。</span><span class="sxs-lookup"><span data-stu-id="4d87a-140">This function deletes all of the **PSSessions** in the current session.</span></span>
<span data-ttu-id="4d87a-141">将此函数添加到 PowerShell 配置文件后，若要删除所有会话，请键入 `EndPSS` 。</span><span class="sxs-lookup"><span data-stu-id="4d87a-141">After you add this function to your PowerShell profile, to delete all sessions, type `EndPSS`.</span></span>

## <span data-ttu-id="4d87a-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4d87a-142">PARAMETERS</span></span>

### <span data-ttu-id="4d87a-143">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="4d87a-143">-ComputerName</span></span>

<span data-ttu-id="4d87a-144">指定计算机的名称数组。</span><span class="sxs-lookup"><span data-stu-id="4d87a-144">Specifies an array of names of computers.</span></span>
<span data-ttu-id="4d87a-145">此 cmdlet 关闭连接到指定计算机的 **PSSession**。</span><span class="sxs-lookup"><span data-stu-id="4d87a-145">This cmdlet closes the **PSSessions** that are connected to the specified computers.</span></span>
<span data-ttu-id="4d87a-146">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="4d87a-146">Wildcard characters are permitted.</span></span>

<span data-ttu-id="4d87a-147">键入一台或多台远程计算机的 NetBIOS 名称、IP 地址或完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="4d87a-147">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span>
<span data-ttu-id="4d87a-148">若要指定本地计算机，请键入该计算机名称、localhost 或句点 (.)。</span><span class="sxs-lookup"><span data-stu-id="4d87a-148">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="4d87a-149">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="4d87a-149">-ContainerId</span></span>

<span data-ttu-id="4d87a-150">指定容器的 Id 的数组。</span><span class="sxs-lookup"><span data-stu-id="4d87a-150">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="4d87a-151">此 cmdlet 将删除每个指定容器的会话。</span><span class="sxs-lookup"><span data-stu-id="4d87a-151">This cmdlet removes sessions for each of the specified containers.</span></span> <span data-ttu-id="4d87a-152">使用 `docker ps` 命令获取容器 id 列表。</span><span class="sxs-lookup"><span data-stu-id="4d87a-152">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="4d87a-153">有关详细信息，请参阅 [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) 命令的帮助。</span><span class="sxs-lookup"><span data-stu-id="4d87a-153">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4d87a-154">-Id</span><span class="sxs-lookup"><span data-stu-id="4d87a-154">-Id</span></span>

<span data-ttu-id="4d87a-155">指定会话的 ID 数组。</span><span class="sxs-lookup"><span data-stu-id="4d87a-155">Specifies an array of IDs of sessions.</span></span>
<span data-ttu-id="4d87a-156">此 cmdlet 关闭具有指定 ID 的 PSSession。</span><span class="sxs-lookup"><span data-stu-id="4d87a-156">This cmdlet closes the *PSSessions* with the specified IDs.</span></span>
<span data-ttu-id="4d87a-157">键入一个或多个 ID（以逗号分隔），或使用范围运算符 (..) 来指定 ID 的范围。</span><span class="sxs-lookup"><span data-stu-id="4d87a-157">Type one or more IDs, separated by commas, or use the range operator (..) to specify a range of IDs.</span></span>

<span data-ttu-id="4d87a-158">ID 是一个整数，用于在当前会话中唯一标识 **PSSession**。</span><span class="sxs-lookup"><span data-stu-id="4d87a-158">An ID is an integer that uniquely identifies the **PSSession** in the current session.</span></span>
<span data-ttu-id="4d87a-159">它比 InstanceId 更容易记住和键入，但它仅在当前会话中是唯一的。</span><span class="sxs-lookup"><span data-stu-id="4d87a-159">It is easier to remember and type than the *InstanceId*, but it is unique only in the current session.</span></span>
<span data-ttu-id="4d87a-160">若要查找 **PSSession** 的 ID，请运行不带参数的 Get-PSSession。</span><span class="sxs-lookup"><span data-stu-id="4d87a-160">To find the ID of a **PSSession**, run the Get-PSSession cmdlet without parameters.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4d87a-161">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="4d87a-161">-InstanceId</span></span>

<span data-ttu-id="4d87a-162">指定实例 ID 的数组。</span><span class="sxs-lookup"><span data-stu-id="4d87a-162">Specifies an array of instance IDs.</span></span>
<span data-ttu-id="4d87a-163">此 cmdlet 关闭具有指定实例 ID 的 **PSSession**。</span><span class="sxs-lookup"><span data-stu-id="4d87a-163">This cmdlet closes the **PSSessions** that have the specified instance IDs.</span></span>

<span data-ttu-id="4d87a-164">实例 ID 是一个 GUID，用于在当前会话中唯一标识 **PSSession**。</span><span class="sxs-lookup"><span data-stu-id="4d87a-164">The instance ID is a GUID that uniquely identifies a **PSSession** in the current session.</span></span>
<span data-ttu-id="4d87a-165">即使在一台计算机上运行了多个会话，实例 ID 也是唯一的。</span><span class="sxs-lookup"><span data-stu-id="4d87a-165">The instance ID is unique, even when you have multiple sessions running on a single computer.</span></span>

<span data-ttu-id="4d87a-166">实例 ID 存储在表示 **PSSession** 的对象的 **InstanceID** 属性中。</span><span class="sxs-lookup"><span data-stu-id="4d87a-166">The instance ID is stored in the **InstanceID** property of the object that represents a **PSSession**.</span></span>
<span data-ttu-id="4d87a-167">若要查找当前会话中的 **PSSession** 的 **InstanceID**，请键入 `Get-PSSession | Format-Table Name, ComputerName, InstanceId`。</span><span class="sxs-lookup"><span data-stu-id="4d87a-167">To find the **InstanceID** of the **PSSessions** in the current session, type `Get-PSSession | Format-Table Name, ComputerName, InstanceId`.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4d87a-168">-Name</span><span class="sxs-lookup"><span data-stu-id="4d87a-168">-Name</span></span>

<span data-ttu-id="4d87a-169">指定会话的友好名称数组。</span><span class="sxs-lookup"><span data-stu-id="4d87a-169">Specifies an array of friendly names of sessions.</span></span>
<span data-ttu-id="4d87a-170">此 cmdlet 关闭具有指定友好名称的 **PSSession**。</span><span class="sxs-lookup"><span data-stu-id="4d87a-170">This cmdlet closes the **PSSessions** that have the specified friendly names.</span></span>
<span data-ttu-id="4d87a-171">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="4d87a-171">Wildcard characters are permitted.</span></span>

<span data-ttu-id="4d87a-172">由于 **PSSession** 的友好名称可能不唯一，因此在使用 Name 参数时，还应考虑在 **Remove-PSSession** 命令中使用 WhatIf 或 Confirm 参数。</span><span class="sxs-lookup"><span data-stu-id="4d87a-172">Because the friendly name of a **PSSession** might not be unique, when you use the *Name* parameter, consider also using the *WhatIf* or *Confirm* parameter in the **Remove-PSSession** command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="4d87a-173">-Session</span><span class="sxs-lookup"><span data-stu-id="4d87a-173">-Session</span></span>

<span data-ttu-id="4d87a-174">指定要关闭的 **PSSession** 的会话对象。</span><span class="sxs-lookup"><span data-stu-id="4d87a-174">Specifies the session objects of the **PSSessions** to close.</span></span>
<span data-ttu-id="4d87a-175">输入包含 **PSSession** 的变量或用于创建或获取 **PSSession** 的命令，例如 New-PSSession 或 **Get-PSSession** 命令。</span><span class="sxs-lookup"><span data-stu-id="4d87a-175">Enter a variable that contains the **PSSessions** or a command that creates or gets the **PSSessions**, such as a New-PSSession or **Get-PSSession** command.</span></span>
<span data-ttu-id="4d87a-176">你还可以通过管道将一个或多个会话对象传递给 **Remove-PSSession**。</span><span class="sxs-lookup"><span data-stu-id="4d87a-176">You can also pipe one or more session objects to **Remove-PSSession**.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4d87a-177">-VMId</span><span class="sxs-lookup"><span data-stu-id="4d87a-177">-VMId</span></span>

<span data-ttu-id="4d87a-178">指定虚拟机的 ID 的数组。</span><span class="sxs-lookup"><span data-stu-id="4d87a-178">Specifies an array of ID of virtual machines.</span></span>
<span data-ttu-id="4d87a-179">此 cmdlet 与每个指定的虚拟机启动交互会话。</span><span class="sxs-lookup"><span data-stu-id="4d87a-179">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span>
<span data-ttu-id="4d87a-180">若要查看可供你使用的虚拟机，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="4d87a-180">To see the virtual machines that are available to you, use the following command:</span></span>

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4d87a-181">-VMName</span><span class="sxs-lookup"><span data-stu-id="4d87a-181">-VMName</span></span>

<span data-ttu-id="4d87a-182">指定一个虚拟机的名称数组。</span><span class="sxs-lookup"><span data-stu-id="4d87a-182">Specifies an array of names of virtual machines.</span></span>
<span data-ttu-id="4d87a-183">此 cmdlet 与每个指定的虚拟机启动交互会话。</span><span class="sxs-lookup"><span data-stu-id="4d87a-183">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span>
<span data-ttu-id="4d87a-184">若要查看可供你使用的虚拟机，请使用 **Get-VM** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4d87a-184">To see the virtual machines that are available to you, use the **Get-VM** cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4d87a-185">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4d87a-185">-Confirm</span></span>

<span data-ttu-id="4d87a-186">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="4d87a-186">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4d87a-187">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4d87a-187">-WhatIf</span></span>

<span data-ttu-id="4d87a-188">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="4d87a-188">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="4d87a-189">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="4d87a-189">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4d87a-190">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4d87a-190">CommonParameters</span></span>

<span data-ttu-id="4d87a-191">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4d87a-191">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4d87a-192">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4d87a-192">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4d87a-193">输入</span><span class="sxs-lookup"><span data-stu-id="4d87a-193">INPUTS</span></span>

### <span data-ttu-id="4d87a-194">System.Management.Automation.Runspaces.PSSession</span><span class="sxs-lookup"><span data-stu-id="4d87a-194">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="4d87a-195">可以将会话对象通过管道传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4d87a-195">You can pipe a session object to this cmdlet.</span></span>

## <span data-ttu-id="4d87a-196">输出</span><span class="sxs-lookup"><span data-stu-id="4d87a-196">OUTPUTS</span></span>

### <span data-ttu-id="4d87a-197">无</span><span class="sxs-lookup"><span data-stu-id="4d87a-197">None</span></span>

<span data-ttu-id="4d87a-198">此 cmdlet 不返回任何对象。</span><span class="sxs-lookup"><span data-stu-id="4d87a-198">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="4d87a-199">注释</span><span class="sxs-lookup"><span data-stu-id="4d87a-199">NOTES</span></span>

* <span data-ttu-id="4d87a-200">Id 参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="4d87a-200">The *Id* parameter is mandatory.</span></span> <span data-ttu-id="4d87a-201">若要删除当前会话中的所有 **PSSession**，请键入 `Get-PSSession | Remove-PSSession`。</span><span class="sxs-lookup"><span data-stu-id="4d87a-201">To delete all the **PSSessions** in the current session, type `Get-PSSession | Remove-PSSession`.</span></span>
* <span data-ttu-id="4d87a-202">**PSSession** 使用与远程计算机的持续性连接。</span><span class="sxs-lookup"><span data-stu-id="4d87a-202">A **PSSession** uses a persistent connection to a remote computer.</span></span> <span data-ttu-id="4d87a-203">创建 **PSSession** 以运行共享数据的一系列命令。</span><span class="sxs-lookup"><span data-stu-id="4d87a-203">Create a **PSSession** to run a series of commands that share data.</span></span> <span data-ttu-id="4d87a-204">要了解详情，请键入 `Get-Help about_PSSessions`。</span><span class="sxs-lookup"><span data-stu-id="4d87a-204">For more information, type `Get-Help about_PSSessions`.</span></span>
* <span data-ttu-id="4d87a-205">**PSSession** 特定于当前会话。</span><span class="sxs-lookup"><span data-stu-id="4d87a-205">**PSSessions** are specific to the current session.</span></span> <span data-ttu-id="4d87a-206">结束某个会话时，将强制关闭你在该会话中创建的 **PSSession**。</span><span class="sxs-lookup"><span data-stu-id="4d87a-206">When you end a session, the **PSSessions** that you created in that session are forcibly closed.</span></span>

## <span data-ttu-id="4d87a-207">相关链接</span><span class="sxs-lookup"><span data-stu-id="4d87a-207">RELATED LINKS</span></span>

[<span data-ttu-id="4d87a-208">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="4d87a-208">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="4d87a-209">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="4d87a-209">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="4d87a-210">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="4d87a-210">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="4d87a-211">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="4d87a-211">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="4d87a-212">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="4d87a-212">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="4d87a-213">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="4d87a-213">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="4d87a-214">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="4d87a-214">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="4d87a-215">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="4d87a-215">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="4d87a-216">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="4d87a-216">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="4d87a-217">about_Remote</span><span class="sxs-lookup"><span data-stu-id="4d87a-217">about_Remote</span></span>](About/about_Remote.md)
