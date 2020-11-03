---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-psdrive?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSDrive
ms.openlocfilehash: 4b9b466be3d52877056b948e4cc373991784416a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93198065"
---
# <span data-ttu-id="63c60-103">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="63c60-103">Remove-PSDrive</span></span>

## <span data-ttu-id="63c60-104">摘要</span><span class="sxs-lookup"><span data-stu-id="63c60-104">SYNOPSIS</span></span>
<span data-ttu-id="63c60-105">删除临时 PowerShell 驱动器并断开映射的网络驱动器的连接。</span><span class="sxs-lookup"><span data-stu-id="63c60-105">Deletes temporary PowerShell drives and disconnects mapped network drives.</span></span>

## <span data-ttu-id="63c60-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="63c60-106">SYNTAX</span></span>

### <span data-ttu-id="63c60-107">Name（默认值）</span><span class="sxs-lookup"><span data-stu-id="63c60-107">Name (Default)</span></span>

```
Remove-PSDrive [-Name] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="63c60-108">LiteralName</span><span class="sxs-lookup"><span data-stu-id="63c60-108">LiteralName</span></span>

```
Remove-PSDrive [-LiteralName] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="63c60-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="63c60-109">DESCRIPTION</span></span>

<span data-ttu-id="63c60-110">`Remove-PSDrive`Cmdlet 删除使用 cmdlet 创建的临时 PowerShell 驱动器 `New-PSDrive` 。</span><span class="sxs-lookup"><span data-stu-id="63c60-110">The `Remove-PSDrive` cmdlet deletes temporary PowerShell drives that were created by using the `New-PSDrive` cmdlet.</span></span>

<span data-ttu-id="63c60-111">从 Windows PowerShell 3.0 开始， `Remove-PSDrive` 还会断开映射的网络驱动器（包括但不限于）使用的参数创建的驱动器 `Persist` `New-PSDrive` 。</span><span class="sxs-lookup"><span data-stu-id="63c60-111">Beginning in Windows PowerShell 3.0, `Remove-PSDrive` also disconnects mapped network drives, including, but not limited to, drives created by using the `Persist` parameter of `New-PSDrive`.</span></span>

<span data-ttu-id="63c60-112">`Remove-PSDrive` 无法删除 Windows 物理或逻辑驱动器。</span><span class="sxs-lookup"><span data-stu-id="63c60-112">`Remove-PSDrive` cannot delete Windows physical or logical drives.</span></span>

<span data-ttu-id="63c60-113">从 Windows PowerShell 3.0 开始，当外部驱动器连接到计算机时，PowerShell 会自动将 New-psdrive 添加到代表新驱动器的文件系统中。</span><span class="sxs-lookup"><span data-stu-id="63c60-113">Beginning in Windows PowerShell 3.0, when an external drive is connected to the computer, PowerShell automatically adds a PSDrive to the file system that represents the new drive.</span></span>
<span data-ttu-id="63c60-114">不需要重新启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="63c60-114">You do not need to restart PowerShell.</span></span>
<span data-ttu-id="63c60-115">同样，当外部驱动器与计算机断开连接时，PowerShell 会自动删除表示已删除驱动器的 New-psdrive。</span><span class="sxs-lookup"><span data-stu-id="63c60-115">Similarly, when an external drive is disconnected from the computer, PowerShell automatically deletes the PSDrive that represents the removed drive.</span></span>

## <span data-ttu-id="63c60-116">示例</span><span class="sxs-lookup"><span data-stu-id="63c60-116">EXAMPLES</span></span>

### <span data-ttu-id="63c60-117">示例 1：删除文件系统驱动器</span><span class="sxs-lookup"><span data-stu-id="63c60-117">Example 1: Remove a file system drive</span></span>

<span data-ttu-id="63c60-118">此命令删除一个名为“smp”的临时文件系统驱动器。</span><span class="sxs-lookup"><span data-stu-id="63c60-118">This command removes a temporary file system drive named "smp".</span></span>

```powershell
Remove-PSDrive -Name smp
```

### <span data-ttu-id="63c60-119">示例 2：删除映射的网络驱动器</span><span class="sxs-lookup"><span data-stu-id="63c60-119">Example 2: Remove mapped network drives</span></span>

<span data-ttu-id="63c60-120">此命令使用 `Remove-PSDrive` 断开 X：和 S：映射网络驱动器的连接。</span><span class="sxs-lookup"><span data-stu-id="63c60-120">This command uses `Remove-PSDrive` to disconnect the X: and S: mapped network drives.</span></span>

```powershell
Get-PSDrive X, S | Remove-PSDrive
```

## <span data-ttu-id="63c60-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="63c60-121">PARAMETERS</span></span>

### <span data-ttu-id="63c60-122">-Force</span><span class="sxs-lookup"><span data-stu-id="63c60-122">-Force</span></span>

<span data-ttu-id="63c60-123">删除当前 PowerShell 驱动器。</span><span class="sxs-lookup"><span data-stu-id="63c60-123">Removes the current PowerShell drive.</span></span>

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

### <span data-ttu-id="63c60-124">-LiteralName</span><span class="sxs-lookup"><span data-stu-id="63c60-124">-LiteralName</span></span>

<span data-ttu-id="63c60-125">指定驱动器的名称。</span><span class="sxs-lookup"><span data-stu-id="63c60-125">Specifies the name of the drive.</span></span>

<span data-ttu-id="63c60-126">**LiteralName** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="63c60-126">The value of **LiteralName** is used exactly as typed.</span></span>
<span data-ttu-id="63c60-127">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="63c60-127">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="63c60-128">如果名称包括转义符，请将其括在单引号 (') 中。</span><span class="sxs-lookup"><span data-stu-id="63c60-128">If the name includes escape characters, enclose it in single quotation marks (').</span></span>
<span data-ttu-id="63c60-129">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="63c60-129">Single quotation marks instruct PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="63c60-130">-Name</span><span class="sxs-lookup"><span data-stu-id="63c60-130">-Name</span></span>

<span data-ttu-id="63c60-131">指定要删除的驱动器的名称。</span><span class="sxs-lookup"><span data-stu-id="63c60-131">Specifies the names of the drives to remove.</span></span>
<span data-ttu-id="63c60-132">请不要在驱动器名称后面键入冒号 (:)。</span><span class="sxs-lookup"><span data-stu-id="63c60-132">Do not type a colon (:) after the drive name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="63c60-133">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="63c60-133">-PSProvider</span></span>

<span data-ttu-id="63c60-134">指定 **PSProvider** 对象的数组。</span><span class="sxs-lookup"><span data-stu-id="63c60-134">Specifies an array of **PSProvider** objects.</span></span>
<span data-ttu-id="63c60-135">此 cmdlet 将删除与指定的 PowerShell 提供程序关联的所有驱动器并断开连接。</span><span class="sxs-lookup"><span data-stu-id="63c60-135">This cmdlet removes and disconnects all of the drives associated with the specified PowerShell provider.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="63c60-136">-Scope</span><span class="sxs-lookup"><span data-stu-id="63c60-136">-Scope</span></span>

<span data-ttu-id="63c60-137">指定驱动器的作用域。</span><span class="sxs-lookup"><span data-stu-id="63c60-137">Specifies a scope for the drive.</span></span>
<span data-ttu-id="63c60-138">此参数的可接受值为： Global、Local、Script 或相对于当前作用域的数字。</span><span class="sxs-lookup"><span data-stu-id="63c60-138">The acceptable values for this parameter are: Global, Local, and Script, or a number relative to the current scope.</span></span> <span data-ttu-id="63c60-139">范围号0到范围数。</span><span class="sxs-lookup"><span data-stu-id="63c60-139">Scopes number 0 through the number of scopes.</span></span> <span data-ttu-id="63c60-140">当前作用域编号为0，其父级为1。</span><span class="sxs-lookup"><span data-stu-id="63c60-140">The current scope number is 0 and its parent is 1.</span></span>
<span data-ttu-id="63c60-141">有关详细信息，请参阅 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="63c60-141">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="63c60-142">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="63c60-142">-UseTransaction</span></span>

<span data-ttu-id="63c60-143">在活动事务中使用该命令。</span><span class="sxs-lookup"><span data-stu-id="63c60-143">Includes the command in the active transaction.</span></span>
<span data-ttu-id="63c60-144">仅当正在执行事务时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="63c60-144">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="63c60-145">有关详细信息，请参阅 about_Transactions。</span><span class="sxs-lookup"><span data-stu-id="63c60-145">For more information, see about_Transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="63c60-146">-Confirm</span><span class="sxs-lookup"><span data-stu-id="63c60-146">-Confirm</span></span>

<span data-ttu-id="63c60-147">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="63c60-147">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="63c60-148">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="63c60-148">-WhatIf</span></span>

<span data-ttu-id="63c60-149">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="63c60-149">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="63c60-150">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="63c60-150">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="63c60-151">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="63c60-151">CommonParameters</span></span>

<span data-ttu-id="63c60-152">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="63c60-152">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="63c60-153">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="63c60-153">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="63c60-154">输入</span><span class="sxs-lookup"><span data-stu-id="63c60-154">INPUTS</span></span>

### <span data-ttu-id="63c60-155">System.Management.Automation.PSDriveInfo</span><span class="sxs-lookup"><span data-stu-id="63c60-155">System.Management.Automation.PSDriveInfo</span></span>

<span data-ttu-id="63c60-156">可以通过管道将驱动器对象（例如 `Get-PSDrive` cmdlet）传递给 `Remove-PSDrive` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="63c60-156">You can pipe a drive object, such as one from the `Get-PSDrive` cmdlet, to the `Remove-PSDrive` cmdlet.</span></span>

## <span data-ttu-id="63c60-157">输出</span><span class="sxs-lookup"><span data-stu-id="63c60-157">OUTPUTS</span></span>

### <span data-ttu-id="63c60-158">无</span><span class="sxs-lookup"><span data-stu-id="63c60-158">None</span></span>

<span data-ttu-id="63c60-159">此 cmdlet 不返回任何输出。</span><span class="sxs-lookup"><span data-stu-id="63c60-159">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="63c60-160">注释</span><span class="sxs-lookup"><span data-stu-id="63c60-160">NOTES</span></span>

- <span data-ttu-id="63c60-161">`Remove-PSDrive`Cmdlet 设计用于处理由任何 PowerShell 提供程序公开的数据。</span><span class="sxs-lookup"><span data-stu-id="63c60-161">The `Remove-PSDrive` cmdlet is designed to work with the data exposed by any PowerShell provider.</span></span> <span data-ttu-id="63c60-162">若要列出会话中的提供程序，请使用 `Get-PSProvider` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="63c60-162">To list the providers in your session, use the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="63c60-163">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="63c60-163">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="63c60-164">相关链接</span><span class="sxs-lookup"><span data-stu-id="63c60-164">RELATED LINKS</span></span>

[<span data-ttu-id="63c60-165">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="63c60-165">Get-PSDrive</span></span>](Get-PSDrive.md)

[<span data-ttu-id="63c60-166">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="63c60-166">New-PSDrive</span></span>](New-PSDrive.md)

[<span data-ttu-id="63c60-167">about_Providers</span><span class="sxs-lookup"><span data-stu-id="63c60-167">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)