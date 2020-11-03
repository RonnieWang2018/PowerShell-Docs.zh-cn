---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Module
ms.openlocfilehash: a1052c357f19fd8f06eb39a14f8e8eded0c881a9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93197627"
---
# <span data-ttu-id="5bd51-103">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="5bd51-103">Remove-Module</span></span>

## <span data-ttu-id="5bd51-104">摘要</span><span class="sxs-lookup"><span data-stu-id="5bd51-104">SYNOPSIS</span></span>
<span data-ttu-id="5bd51-105">删除当前会话中的模块。</span><span class="sxs-lookup"><span data-stu-id="5bd51-105">Removes modules from the current session.</span></span>

## <span data-ttu-id="5bd51-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5bd51-106">SYNTAX</span></span>

### <span data-ttu-id="5bd51-107">name</span><span class="sxs-lookup"><span data-stu-id="5bd51-107">name</span></span>

```
Remove-Module [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5bd51-108">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="5bd51-108">FullyQualifiedName</span></span>

```
Remove-Module [-FullyQualifiedName] <ModuleSpecification[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5bd51-109">ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="5bd51-109">ModuleInfo</span></span>

```
Remove-Module [-ModuleInfo] <PSModuleInfo[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5bd51-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5bd51-110">DESCRIPTION</span></span>

<span data-ttu-id="5bd51-111">**Remove-Module** cmdlet 将从当前会话中删除模块的成员，如 cmdlet 和函数。</span><span class="sxs-lookup"><span data-stu-id="5bd51-111">The **Remove-Module** cmdlet removes the members of a module, such as cmdlets and functions, from the current session.</span></span>

<span data-ttu-id="5bd51-112">如果模块包含某个程序集 (.dll)，则将删除由该程序集实现的所有成员，但不会卸载该程序集。</span><span class="sxs-lookup"><span data-stu-id="5bd51-112">If the module includes an assembly (.dll), all members that are implemented by the assembly are removed, but the assembly is not unloaded.</span></span>

<span data-ttu-id="5bd51-113">此 cmdlet 不会将该模块从计算机中卸载或删除。</span><span class="sxs-lookup"><span data-stu-id="5bd51-113">This cmdlet does not uninstall the module or delete it from the computer.</span></span>
<span data-ttu-id="5bd51-114">它仅影响当前 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="5bd51-114">It affects only the current PowerShell session.</span></span>

## <span data-ttu-id="5bd51-115">示例</span><span class="sxs-lookup"><span data-stu-id="5bd51-115">EXAMPLES</span></span>

### <span data-ttu-id="5bd51-116">示例 1：删除模块</span><span class="sxs-lookup"><span data-stu-id="5bd51-116">Example 1: Remove a module</span></span>

```powershell
Remove-Module -Name "BitsTransfer"
```

<span data-ttu-id="5bd51-117">此命令将从当前会话中删除 BitsTransfer 模块。</span><span class="sxs-lookup"><span data-stu-id="5bd51-117">This command removes the BitsTransfer module from the current session.</span></span>

### <span data-ttu-id="5bd51-118">示例 2：删除所有模块</span><span class="sxs-lookup"><span data-stu-id="5bd51-118">Example 2: Remove all modules</span></span>

```powershell
Get-Module | Remove-Module
```

<span data-ttu-id="5bd51-119">此命令将从当前会话中删除所有模块。</span><span class="sxs-lookup"><span data-stu-id="5bd51-119">This command removes all modules from the current session.</span></span>

### <span data-ttu-id="5bd51-120">示例 3：通过使用管道删除模块</span><span class="sxs-lookup"><span data-stu-id="5bd51-120">Example 3: Remove modules by using the pipeline</span></span>

```powershell
"FileTransfer", "PSDiagnostics" | Remove-Module -Verbose
```

```Output
VERBOSE: Performing operation "Remove-Module" on Target "filetransfer (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\filetransfer\filetransfer.psd1')".
VERBOSE: Performing operation "Remove-Module" on Target "Microsoft.BackgroundIntelligentTransfer.Management (Path: 'C:\Windows\assembly\GAC_MSIL\Microsoft.BackgroundIntelligentTransfer.Management\1.0.0.0__31bf3856ad364e35\Microsoft.BackgroundIntelligentTransfe
r.Management.dll')".
VERBOSE: Performing operation "Remove-Module" on Target "psdiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\psdiagnostics.psd1')".
VERBOSE: Removing imported function 'Start-Trace'.
VERBOSE: Removing imported function 'Stop-Trace'.
VERBOSE: Removing imported function 'Enable-WSManTrace'.
VERBOSE: Removing imported function 'Disable-WSManTrace'.
VERBOSE: Removing imported function 'Enable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Disable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Set-LogProperties'.
VERBOSE: Removing imported function 'Get-LogProperties'.
VERBOSE: Removing imported function 'Enable-PSTrace'.
VERBOSE: Removing imported function 'Disable-PSTrace'.
VERBOSE: Performing operation "Remove-Module" on Target "PSDiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\PSDiagnostics.psm1')".
```

<span data-ttu-id="5bd51-121">此命令将从当前会话中删除 BitsTransfer 和 PSDiagnostics 模块。</span><span class="sxs-lookup"><span data-stu-id="5bd51-121">This command removes the BitsTransfer and PSDiagnostics modules from the current session.</span></span>

<span data-ttu-id="5bd51-122">该命令使用管道运算符 (|) 将模块名称发送到 **Remove-Module** 。</span><span class="sxs-lookup"><span data-stu-id="5bd51-122">The command uses a pipeline operator (|) to send the module names to **Remove-Module** .</span></span>
<span data-ttu-id="5bd51-123">它使用 *Verbose* 通用参数来获取有关要删除的成员的详细信息。</span><span class="sxs-lookup"><span data-stu-id="5bd51-123">It uses the *Verbose* common parameter to get detailed information about the members that are removed.</span></span>

<span data-ttu-id="5bd51-124">Verbose  消息显示所删除的项。</span><span class="sxs-lookup"><span data-stu-id="5bd51-124">The *Verbose* messages show the items that are removed.</span></span>
<span data-ttu-id="5bd51-125">这些消息会有所不同，因为 BitsTransfer 模块包含一个实现其 cmdlet 的程序集，以及一个拥有自己的程序集的嵌套模块。</span><span class="sxs-lookup"><span data-stu-id="5bd51-125">The messages differ because the BitsTransfer module includes an assembly that implements its cmdlets and a nested module with its own assembly.</span></span>
<span data-ttu-id="5bd51-126">PSDiagnostics 模块包含用于导出函数的模块脚本文件 (.psm1)。</span><span class="sxs-lookup"><span data-stu-id="5bd51-126">The PSDiagnostics module includes a module script file (.psm1) that exports functions.</span></span>

### <span data-ttu-id="5bd51-127">示例 4：通过使用 ModuleInfo 删除模块</span><span class="sxs-lookup"><span data-stu-id="5bd51-127">Example 4: Remove a module by using ModuleInfo</span></span>

```powershell
$a = Get-Module BitsTransfer
Remove-Module -ModuleInfo $a
```

<span data-ttu-id="5bd51-128">此命令使用 ModuleInfo  参数删除 BitsTransfer 模块。</span><span class="sxs-lookup"><span data-stu-id="5bd51-128">This command uses the *ModuleInfo* parameter to remove the BitsTransfer module.</span></span>

## <span data-ttu-id="5bd51-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5bd51-129">PARAMETERS</span></span>

### <span data-ttu-id="5bd51-130">-Force</span><span class="sxs-lookup"><span data-stu-id="5bd51-130">-Force</span></span>

<span data-ttu-id="5bd51-131">指示此 cmdlet 将删除只读模块。</span><span class="sxs-lookup"><span data-stu-id="5bd51-131">Indicates that this cmdlet removes read-only modules.</span></span>
<span data-ttu-id="5bd51-132">默认情况下， **Remove-Module** 只删除读写模块。</span><span class="sxs-lookup"><span data-stu-id="5bd51-132">By default, **Remove-Module** removes only read-write modules.</span></span>

<span data-ttu-id="5bd51-133">**ReadOnly** 和 **ReadWrite** 值存储在模块的 **AccessMode** 属性中。</span><span class="sxs-lookup"><span data-stu-id="5bd51-133">The **ReadOnly** and **ReadWrite** values are stored in **AccessMode** property of a module.</span></span>

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

### <span data-ttu-id="5bd51-134">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="5bd51-134">-FullyQualifiedName</span></span>

<span data-ttu-id="5bd51-135">指定要删除的模块的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="5bd51-135">Specifies the fully qualified names of modules to remove.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5bd51-136">-ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="5bd51-136">-ModuleInfo</span></span>

<span data-ttu-id="5bd51-137">指定要删除的模块对象。</span><span class="sxs-lookup"><span data-stu-id="5bd51-137">Specifies the module objects to remove.</span></span>
<span data-ttu-id="5bd51-138">输入包含模块对象 ( **PSModuleInfo** ) 的变量，或输入可获取模块对象的命令，如 Get-Module 命令。</span><span class="sxs-lookup"><span data-stu-id="5bd51-138">Enter a variable that contains a module object ( **PSModuleInfo** ) or a command that gets a module object, such as a Get-Module command.</span></span>
<span data-ttu-id="5bd51-139">你还可以通过管道将模块对象传递给 **Remove-Module** 。</span><span class="sxs-lookup"><span data-stu-id="5bd51-139">You can also pipe module objects to **Remove-Module** .</span></span>

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: ModuleInfo
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5bd51-140">-Name</span><span class="sxs-lookup"><span data-stu-id="5bd51-140">-Name</span></span>

<span data-ttu-id="5bd51-141">指定要删除的模块的名称。</span><span class="sxs-lookup"><span data-stu-id="5bd51-141">Specifies the names of modules to remove.</span></span>
<span data-ttu-id="5bd51-142">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="5bd51-142">Wildcard characters are permitted.</span></span>
<span data-ttu-id="5bd51-143">还可以通过管道将名称字符串传递给 **Remove-Module** 。</span><span class="sxs-lookup"><span data-stu-id="5bd51-143">You can also pipe name strings to **Remove-Module** .</span></span>

```yaml
Type: System.String[]
Parameter Sets: name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="5bd51-144">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5bd51-144">-Confirm</span></span>

<span data-ttu-id="5bd51-145">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="5bd51-145">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5bd51-146">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5bd51-146">-WhatIf</span></span>

<span data-ttu-id="5bd51-147">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="5bd51-147">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5bd51-148">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="5bd51-148">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5bd51-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5bd51-149">CommonParameters</span></span>

<span data-ttu-id="5bd51-150">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="5bd51-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5bd51-151">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="5bd51-151">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5bd51-152">输入</span><span class="sxs-lookup"><span data-stu-id="5bd51-152">INPUTS</span></span>

### <span data-ttu-id="5bd51-153">System.String, System.Management.Automation.PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="5bd51-153">System.String, System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="5bd51-154">可以通过管道将模块名称和模块对象传递给 **Remove-Module** 。</span><span class="sxs-lookup"><span data-stu-id="5bd51-154">You can pipe module names and module objects to **Remove-Module** .</span></span>

## <span data-ttu-id="5bd51-155">输出</span><span class="sxs-lookup"><span data-stu-id="5bd51-155">OUTPUTS</span></span>

### <span data-ttu-id="5bd51-156">无</span><span class="sxs-lookup"><span data-stu-id="5bd51-156">None</span></span>

<span data-ttu-id="5bd51-157">此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="5bd51-157">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5bd51-158">注释</span><span class="sxs-lookup"><span data-stu-id="5bd51-158">NOTES</span></span>

## <span data-ttu-id="5bd51-159">相关链接</span><span class="sxs-lookup"><span data-stu-id="5bd51-159">RELATED LINKS</span></span>

[<span data-ttu-id="5bd51-160">Get-Module</span><span class="sxs-lookup"><span data-stu-id="5bd51-160">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="5bd51-161">Import-Module</span><span class="sxs-lookup"><span data-stu-id="5bd51-161">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="5bd51-162">about_Modules</span><span class="sxs-lookup"><span data-stu-id="5bd51-162">about_Modules</span></span>](About/about_Modules.md)
