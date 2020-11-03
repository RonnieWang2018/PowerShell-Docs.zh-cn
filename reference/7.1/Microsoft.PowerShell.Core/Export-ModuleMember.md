---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/export-modulemember?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-ModuleMember
ms.openlocfilehash: 447cfe74c350286dcf396bde7ea8f442e39d637f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93198864"
---
# <span data-ttu-id="585dc-103">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="585dc-103">Export-ModuleMember</span></span>

## <span data-ttu-id="585dc-104">摘要</span><span class="sxs-lookup"><span data-stu-id="585dc-104">SYNOPSIS</span></span>
<span data-ttu-id="585dc-105">指定要导出的模块成员。</span><span class="sxs-lookup"><span data-stu-id="585dc-105">Specifies the module members that are exported.</span></span>

## <span data-ttu-id="585dc-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="585dc-106">SYNTAX</span></span>

```
Export-ModuleMember [[-Function] <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="585dc-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="585dc-107">DESCRIPTION</span></span>

<span data-ttu-id="585dc-108">**Export-ModuleMember** cmdlet 指定从脚本模块 (.psm1) 文件或从使用 New-Module cmdlet 创建的动态模块中导出的模块成员。</span><span class="sxs-lookup"><span data-stu-id="585dc-108">The **Export-ModuleMember** cmdlet specifies the module members that are exported from a script module (.psm1) file, or from a dynamic module created by using the New-Module cmdlet.</span></span>
<span data-ttu-id="585dc-109">模块成员包括 cmdlet、函数、变量和别名。</span><span class="sxs-lookup"><span data-stu-id="585dc-109">Module members include cmdlets, functions, variables, and aliases.</span></span>
<span data-ttu-id="585dc-110">此 cmdlet 只能用于脚本模块文件或动态模块。</span><span class="sxs-lookup"><span data-stu-id="585dc-110">This cmdlet can be used only in a script module file or a dynamic module.</span></span>

<span data-ttu-id="585dc-111">如果脚本模块不包含 **export-modulemember** 命令，则会导出脚本模块中的函数和别名，但不会导出变量。</span><span class="sxs-lookup"><span data-stu-id="585dc-111">If a script module does not include an **Export-ModuleMember** command, the functions and aliases in the script module are exported, but the variables are not.</span></span>
<span data-ttu-id="585dc-112">当脚本模块包含 **export-modulemember** 命令时，只会导出 **export-modulemember** 命令中指定的成员。</span><span class="sxs-lookup"><span data-stu-id="585dc-112">When a script module includes **Export-ModuleMember** commands, only the members specified in the **Export-ModuleMember** commands are exported.</span></span>
<span data-ttu-id="585dc-113">还可以使用 **export-modulemember** 来禁止或导出脚本模块从其他模块导入的成员。</span><span class="sxs-lookup"><span data-stu-id="585dc-113">You can also use **Export-ModuleMember** to suppress or export members that the script module imports from other modules.</span></span>

<span data-ttu-id="585dc-114">**Export-modulemember** 命令是可选的，但这是最佳做法。</span><span class="sxs-lookup"><span data-stu-id="585dc-114">An **Export-ModuleMember** command is optional, but it is a best practice.</span></span>
<span data-ttu-id="585dc-115">即使该命令确认了默认值，但它演示了模块作者的初衷。</span><span class="sxs-lookup"><span data-stu-id="585dc-115">Even if the command confirms the default values, it demonstrates the intention of the module author.</span></span>

## <span data-ttu-id="585dc-116">示例</span><span class="sxs-lookup"><span data-stu-id="585dc-116">EXAMPLES</span></span>

### <span data-ttu-id="585dc-117">示例1：导出脚本模块中的函数和别名</span><span class="sxs-lookup"><span data-stu-id="585dc-117">Example 1: Export functions and aliases in a script module</span></span>

```powershell
Export-ModuleMember -Function * -Alias *
```

<span data-ttu-id="585dc-118">此命令导出在脚本模块中定义的所有函数和别名。</span><span class="sxs-lookup"><span data-stu-id="585dc-118">This command exports all the functions and aliases defined in the script module.</span></span>

### <span data-ttu-id="585dc-119">示例 2：导出特定别名和函数</span><span class="sxs-lookup"><span data-stu-id="585dc-119">Example 2: Export specific aliases and functions</span></span>

```powershell
Export-ModuleMember -Function Get-Test, New-Test, Start-Test -Alias gtt, ntt, stt
```

<span data-ttu-id="585dc-120">此命令导出在脚本模块中定义的三个别名和三个函数。</span><span class="sxs-lookup"><span data-stu-id="585dc-120">This command exports three aliases and three functions defined in the script module.</span></span>

<span data-ttu-id="585dc-121">可以使用此命令格式指定模块成员的名称。</span><span class="sxs-lookup"><span data-stu-id="585dc-121">You can use this command format to specify the names of module members.</span></span>

### <span data-ttu-id="585dc-122">示例 3：不导出成员</span><span class="sxs-lookup"><span data-stu-id="585dc-122">Example 3: Export no members</span></span>

```powershell
Export-ModuleMember
```

<span data-ttu-id="585dc-123">此命令指定不导出在脚本模块中定义的成员。</span><span class="sxs-lookup"><span data-stu-id="585dc-123">This command specifies that no members defined in the script module are exported.</span></span>

<span data-ttu-id="585dc-124">此命令阻止导出模块成员，但不隐藏模块成员。</span><span class="sxs-lookup"><span data-stu-id="585dc-124">This command prevents the module members from being exported, but it does not hide the members.</span></span>
<span data-ttu-id="585dc-125">用户可以读取和复制模块成员，或使用调用运算符 (&) 来调用未导出的模块成员。</span><span class="sxs-lookup"><span data-stu-id="585dc-125">Users can read and copy module members or use the call operator (&) to invoke module members that are not exported.</span></span>

### <span data-ttu-id="585dc-126">示例 4：导出某一特定变量</span><span class="sxs-lookup"><span data-stu-id="585dc-126">Example 4: Export a specific variable</span></span>

```powershell
Export-ModuleMember -Variable increment
```

<span data-ttu-id="585dc-127">此命令只从脚本模块中导出 $increment 变量。</span><span class="sxs-lookup"><span data-stu-id="585dc-127">This command exports only the $increment variable from the script module.</span></span>
<span data-ttu-id="585dc-128">不导出其他成员。</span><span class="sxs-lookup"><span data-stu-id="585dc-128">No other members are exported.</span></span>

<span data-ttu-id="585dc-129">如果要导出某个变量，除了导出模块中的函数外， **export-modulemember** 命令必须包含所有函数的名称和该变量的名称。</span><span class="sxs-lookup"><span data-stu-id="585dc-129">If you want to export a variable, in addition to exporting the functions in a module, the **Export-ModuleMember** command must include the names of all of the functions and the name of the variable.</span></span>

### <span data-ttu-id="585dc-130">示例 5：多个导出命令</span><span class="sxs-lookup"><span data-stu-id="585dc-130">Example 5: Multiple export commands</span></span>

```powershell
# From TestModule.psm1
Function New-Test
{
    Write-Output 'I am New-Test function'
}
Export-ModuleMember -Function New-Test

function Validate-Test
{
    Write-Output 'I am Validate-Test function'
}
function Start-Test
{
    Write-Output 'I am Start-Test function'
}
Set-Alias stt Start-Test
Export-ModuleMember -Function Start-Test -Alias stt
```

<span data-ttu-id="585dc-131">这些命令显示了如何在脚本模块 (. hbase-runner.psm1) 文件中解释多个 **export-modulemember** 命令。</span><span class="sxs-lookup"><span data-stu-id="585dc-131">These commands show how multiple **Export-ModuleMember** commands are interpreted in a script module (.psm1) file.</span></span>

<span data-ttu-id="585dc-132">这些命令创建了三个函数和一个别名，然后导出其中两个函数和该别名。</span><span class="sxs-lookup"><span data-stu-id="585dc-132">These commands create three functions and one alias, and then they export two of the functions and the alias.</span></span>

<span data-ttu-id="585dc-133">如果没有 **export-modulemember** 命令，则将导出所有三个函数和别名。</span><span class="sxs-lookup"><span data-stu-id="585dc-133">Without the **Export-ModuleMember** commands, all three of the functions and the alias would be exported.</span></span>
<span data-ttu-id="585dc-134">对于 **export-modulemember** 命令，只会导出新的 **测试** 和 **启动测试** 函数以及 STT 别名。</span><span class="sxs-lookup"><span data-stu-id="585dc-134">With the **Export-ModuleMember** commands, only the **New-Test** and **Start-Test** functions and the STT alias are exported.</span></span>

### <span data-ttu-id="585dc-135">示例 6：导出动态模块中的成员</span><span class="sxs-lookup"><span data-stu-id="585dc-135">Example 6: Export members in a dynamic module</span></span>

```powershell
New-Module -Script {function SayHello {"Hello!"}; Set-Alias Hi SayHello; Export-ModuleMember -Alias Hi -Function SayHello}
```

<span data-ttu-id="585dc-136">此命令显示了如何在使用 **新模块** cmdlet 创建的动态模块中使用 Export-ModuleMember。</span><span class="sxs-lookup"><span data-stu-id="585dc-136">This command shows how to use Export-ModuleMember in a dynamic module that is created by using the **New-Module** cmdlet.</span></span>

<span data-ttu-id="585dc-137">在此示例中，使用 **export-modulemember** 导出动态模块中的 "Hi" 和 " **SayHello** " 函数。</span><span class="sxs-lookup"><span data-stu-id="585dc-137">In this example, **Export-ModuleMember** is used to export both the Hi alias and the **SayHello** function in the dynamic module.</span></span>

### <span data-ttu-id="585dc-138">示例 7：声明和导出单个命令中的函数</span><span class="sxs-lookup"><span data-stu-id="585dc-138">Example 7: Declare and export a function in a single command</span></span>

```powershell
# From TestModule.psm1
function Export
{
  param (
    [Parameter(Mandatory=$true)]
    [ValidateSet("function","variable")]
    $Type,
    [Parameter(Mandatory=$true)]
    $Name,
    [Parameter(Mandatory=$true)]
    $Value
    )

    if ($Type -eq "function")
    {
        Set-item "function:script:$Name" $Value
        Export-ModuleMember $Name
    }
    else
    {
    Set-Variable -scope Script $Name $Value
    Export-ModuleMember -variable $Name
    }
}

Export function New-Test {Write-Output 'I am New-Test function'}
function helper {Write-Output 'I am helper function'}

Export variable Interval 0
$Interval = 2
```

<span data-ttu-id="585dc-139">此示例包含一个名为 **Export** 的函数，该函数声明函数或创建一个变量，然后 `Export-ModuleMember` 为该函数或变量编写命令。</span><span class="sxs-lookup"><span data-stu-id="585dc-139">This example includes a function named **Export** that declares a function or creates a variable, and then writes an `Export-ModuleMember` command for the function or variable.</span></span>
<span data-ttu-id="585dc-140">这样可以通过单个命令声明和导出函数或变量。</span><span class="sxs-lookup"><span data-stu-id="585dc-140">This lets you declare and export a function or variable in a single command.</span></span>

<span data-ttu-id="585dc-141">若要使用 **Export** 函数，请将其包含在脚本模块中。</span><span class="sxs-lookup"><span data-stu-id="585dc-141">To use the **Export** function, include it in your script module.</span></span>
<span data-ttu-id="585dc-142">若要导出某个函数，请在 **Function** 关键字之前键入 `Export`。</span><span class="sxs-lookup"><span data-stu-id="585dc-142">To export a function, type `Export` before the **Function** keyword.</span></span>

<span data-ttu-id="585dc-143">若要导出某个变量，请使用以下格式声明该变量并为其设置值：</span><span class="sxs-lookup"><span data-stu-id="585dc-143">To export a variable, use the following format to declare the variable and set its value:</span></span>

`Export variable <variable-name> <value>`

<span data-ttu-id="585dc-144">该示例中的命令显示了正确的格式。</span><span class="sxs-lookup"><span data-stu-id="585dc-144">The commands in the example show the correct format.</span></span>
<span data-ttu-id="585dc-145">在此示例中，仅导出 **新的测试** 函数和 $Interval 变量。</span><span class="sxs-lookup"><span data-stu-id="585dc-145">In this example, only the **New-Test** function and the $Interval variable are exported.</span></span>

## <span data-ttu-id="585dc-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="585dc-146">PARAMETERS</span></span>

### <span data-ttu-id="585dc-147">-Alias</span><span class="sxs-lookup"><span data-stu-id="585dc-147">-Alias</span></span>

<span data-ttu-id="585dc-148">指定要从脚本模块文件中导出的别名。</span><span class="sxs-lookup"><span data-stu-id="585dc-148">Specifies the aliases that are exported from the script module file.</span></span>
<span data-ttu-id="585dc-149">输入别名。</span><span class="sxs-lookup"><span data-stu-id="585dc-149">Enter the alias names.</span></span>
<span data-ttu-id="585dc-150">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="585dc-150">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="585dc-151">-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="585dc-151">-Cmdlet</span></span>

<span data-ttu-id="585dc-152">指定要从脚本模块文件中导出的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="585dc-152">Specifies the cmdlets that are exported from the script module file.</span></span>
<span data-ttu-id="585dc-153">输入 cmdlet 名称。</span><span class="sxs-lookup"><span data-stu-id="585dc-153">Enter the cmdlet names.</span></span>
<span data-ttu-id="585dc-154">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="585dc-154">Wildcard characters are permitted.</span></span>

<span data-ttu-id="585dc-155">不能在脚本模块文件中创建 cmdlet，但可将二进制模块中的 cmdlet 导入到脚本模块中，然后重新从该脚本模块中导出这些 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="585dc-155">You cannot create cmdlets in a script module file, but you can import cmdlets from a binary module into a script module and re-export them from the script module.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="585dc-156">-Function</span><span class="sxs-lookup"><span data-stu-id="585dc-156">-Function</span></span>

<span data-ttu-id="585dc-157">指定要从脚本模块文件中导出的函数。</span><span class="sxs-lookup"><span data-stu-id="585dc-157">Specifies the functions that are exported from the script module file.</span></span>
<span data-ttu-id="585dc-158">输入函数名称。</span><span class="sxs-lookup"><span data-stu-id="585dc-158">Enter the function names.</span></span>
<span data-ttu-id="585dc-159">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="585dc-159">Wildcard characters are permitted.</span></span>
<span data-ttu-id="585dc-160">还可以通过管道将函数名称字符串传递给 **export-modulemember** 。</span><span class="sxs-lookup"><span data-stu-id="585dc-160">You can also pipe function name strings to **Export-ModuleMember** .</span></span>

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

### <span data-ttu-id="585dc-161">-Variable</span><span class="sxs-lookup"><span data-stu-id="585dc-161">-Variable</span></span>

<span data-ttu-id="585dc-162">指定要从脚本模块文件中导出的变量。</span><span class="sxs-lookup"><span data-stu-id="585dc-162">Specifies the variables that are exported from the script module file.</span></span>
<span data-ttu-id="585dc-163">输入变量名称（不带美元符号）。</span><span class="sxs-lookup"><span data-stu-id="585dc-163">Enter the variable names, without a dollar sign.</span></span>
<span data-ttu-id="585dc-164">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="585dc-164">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="585dc-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="585dc-165">CommonParameters</span></span>

<span data-ttu-id="585dc-166">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="585dc-166">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="585dc-167">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="585dc-167">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="585dc-168">输入</span><span class="sxs-lookup"><span data-stu-id="585dc-168">INPUTS</span></span>

### <span data-ttu-id="585dc-169">System.String</span><span class="sxs-lookup"><span data-stu-id="585dc-169">System.String</span></span>

<span data-ttu-id="585dc-170">可以通过管道将函数名称字符串传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="585dc-170">You can pipe function name strings to this cmdlet.</span></span>

## <span data-ttu-id="585dc-171">输出</span><span class="sxs-lookup"><span data-stu-id="585dc-171">OUTPUTS</span></span>

### <span data-ttu-id="585dc-172">无</span><span class="sxs-lookup"><span data-stu-id="585dc-172">None</span></span>

<span data-ttu-id="585dc-173">此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="585dc-173">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="585dc-174">注释</span><span class="sxs-lookup"><span data-stu-id="585dc-174">NOTES</span></span>

* <span data-ttu-id="585dc-175">若要从导出的成员列表中排除某一成员，请添加一个 **export-modulemember** 命令，该命令列出所有其他成员，但省略你要排除的成员。</span><span class="sxs-lookup"><span data-stu-id="585dc-175">To exclude a member from the list of exported members, add an **Export-ModuleMember** command that lists all other members but omits the member that you want to exclude.</span></span>

## <span data-ttu-id="585dc-176">相关链接</span><span class="sxs-lookup"><span data-stu-id="585dc-176">RELATED LINKS</span></span>

[<span data-ttu-id="585dc-177">Get-Module</span><span class="sxs-lookup"><span data-stu-id="585dc-177">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="585dc-178">Import-Module</span><span class="sxs-lookup"><span data-stu-id="585dc-178">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="585dc-179">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="585dc-179">Remove-Module</span></span>](Remove-Module.md)

