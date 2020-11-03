---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-wide?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Wide
ms.openlocfilehash: f2dccb4d0fb2d39114e5b24af8085424938ea9c7
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "93199254"
---
# <span data-ttu-id="c816f-103">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="c816f-103">Format-Wide</span></span>

## <span data-ttu-id="c816f-104">摘要</span><span class="sxs-lookup"><span data-stu-id="c816f-104">SYNOPSIS</span></span>
<span data-ttu-id="c816f-105">将对象格式设置为宽表，此表仅显示每个对象的一个属性。</span><span class="sxs-lookup"><span data-stu-id="c816f-105">Formats objects as a wide table that displays only one property of each object.</span></span>

## <span data-ttu-id="c816f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c816f-106">SYNTAX</span></span>

```
Format-Wide [[-Property] <Object>] [-AutoSize] [-Column <int>] [-GroupBy <Object>] [-View <string>]
  [-ShowError] [-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>]
  [<CommonParameters>]
```

## <span data-ttu-id="c816f-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c816f-107">DESCRIPTION</span></span>

<span data-ttu-id="c816f-108">该 `Format-Wide` cmdlet 将对象格式设置为宽表，只显示每个对象的一个属性。</span><span class="sxs-lookup"><span data-stu-id="c816f-108">The `Format-Wide` cmdlet formats objects as a wide table that displays only one property of each object.</span></span> <span data-ttu-id="c816f-109">您可以使用 **property** 参数来确定显示哪个属性。</span><span class="sxs-lookup"><span data-stu-id="c816f-109">You can use the **Property** parameter to determine which property is displayed.</span></span>

## <span data-ttu-id="c816f-110">示例</span><span class="sxs-lookup"><span data-stu-id="c816f-110">EXAMPLES</span></span>

### <span data-ttu-id="c816f-111">示例1：格式化当前目录中文件的名称</span><span class="sxs-lookup"><span data-stu-id="c816f-111">Example 1: Format names of files in the current directory</span></span>

<span data-ttu-id="c816f-112">此命令将在屏幕上的三个列中显示当前目录中的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="c816f-112">This command displays the names of files in the current directory in three columns across the screen.</span></span>

```powershell
Get-ChildItem | Format-Wide -Column 3
```

<span data-ttu-id="c816f-113">Get-ChildItem cmdlet 将获取表示目录中的每个对象的对象。</span><span class="sxs-lookup"><span data-stu-id="c816f-113">The Get-ChildItem cmdlet gets objects representing each file in the directory.</span></span> <span data-ttu-id="c816f-114">管道运算符 (|) 将文件对象通过管道传递到 `Format-Wide` ，这会将它们格式化为输出。</span><span class="sxs-lookup"><span data-stu-id="c816f-114">The pipeline operator (|) passes the file objects through the pipeline to `Format-Wide`, which formats them for output.</span></span> <span data-ttu-id="c816f-115">**Column** 参数指定列数。</span><span class="sxs-lookup"><span data-stu-id="c816f-115">The **Column** parameter specifies the number of columns.</span></span>

### <span data-ttu-id="c816f-116">示例2：格式化注册表项的名称</span><span class="sxs-lookup"><span data-stu-id="c816f-116">Example 2: Format names of registry keys</span></span>

<span data-ttu-id="c816f-117">此命令显示 HKEY_CURRENT_USER\Software\Microsoft 项中的注册表项的名称。</span><span class="sxs-lookup"><span data-stu-id="c816f-117">This command displays the names of registry keys in the HKEY_CURRENT_USER\Software\Microsoft key.</span></span>

```powershell
Get-ChildItem HKCU:\software\microsoft | Format-Wide -Property pschildname -AutoSize
```

<span data-ttu-id="c816f-118">Get-ChildItem cmdlet 将获取表示这些注册表项的对象。</span><span class="sxs-lookup"><span data-stu-id="c816f-118">The Get-ChildItem cmdlet gets objects representing the keys.</span></span> <span data-ttu-id="c816f-119">路径指定为 HKCU：、PowerShell 注册表提供程序公开的驱动器之一，后跟密钥路径。</span><span class="sxs-lookup"><span data-stu-id="c816f-119">The path is specified as HKCU:, one of the drives exposed by the PowerShell Registry provider, followed by the key path.</span></span> <span data-ttu-id="c816f-120">管道运算符 (|) 通过管道将注册表项对象传递到 `Format-Wide` ，后者将它们格式化为输出。</span><span class="sxs-lookup"><span data-stu-id="c816f-120">The pipeline operator (|) passes the registry key objects through the pipeline to `Format-Wide`, which formats them for output.</span></span> <span data-ttu-id="c816f-121">**Property** 参数指定属性的名称，而 **AutoSize** 参数调整列以提高可读性。</span><span class="sxs-lookup"><span data-stu-id="c816f-121">The **Property** parameter specifies the name of the property, and the **AutoSize** parameter adjusts the columns for readability.</span></span>

### <span data-ttu-id="c816f-122">示例3：疑难解答格式错误</span><span class="sxs-lookup"><span data-stu-id="c816f-122">Example 3: Troubleshooting format errors</span></span>

<span data-ttu-id="c816f-123">下面的示例显示了使用表达式添加 **DisplayError** 或 **ShowError** 参数的结果。</span><span class="sxs-lookup"><span data-stu-id="c816f-123">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
PS /> Get-Date | Format-Wide { $_ / $null } -DisplayError


#ERR

PS /> Get-Date | Format-Wide { $_ / $null } -ShowError


Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:18:01 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## <span data-ttu-id="c816f-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c816f-124">PARAMETERS</span></span>

### <span data-ttu-id="c816f-125">-AutoSize</span><span class="sxs-lookup"><span data-stu-id="c816f-125">-AutoSize</span></span>

<span data-ttu-id="c816f-126">基于数据的宽度来调整列的大小和数量。</span><span class="sxs-lookup"><span data-stu-id="c816f-126">Adjusts the column size and number of columns based on the width of the data.</span></span> <span data-ttu-id="c816f-127">默认情况下，列大小和数量由视图确定。</span><span class="sxs-lookup"><span data-stu-id="c816f-127">By default, the column size and number are determined by the view.</span></span> <span data-ttu-id="c816f-128">不能在同一命令中使用 **AutoSize** 和 **Column** 参数。</span><span class="sxs-lookup"><span data-stu-id="c816f-128">You cannot use the **AutoSize** and **Column** parameters in the same command.</span></span>

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

### <span data-ttu-id="c816f-129">-Column</span><span class="sxs-lookup"><span data-stu-id="c816f-129">-Column</span></span>

<span data-ttu-id="c816f-130">指定显示中的列数。</span><span class="sxs-lookup"><span data-stu-id="c816f-130">Specifies the number of columns in the display.</span></span> <span data-ttu-id="c816f-131">不能在同一命令中使用 **AutoSize** 和 **Column** 参数。</span><span class="sxs-lookup"><span data-stu-id="c816f-131">You cannot use the **AutoSize** and **Column** parameters in the same command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c816f-132">-DisplayError</span><span class="sxs-lookup"><span data-stu-id="c816f-132">-DisplayError</span></span>

<span data-ttu-id="c816f-133">在命令行中显示错误。</span><span class="sxs-lookup"><span data-stu-id="c816f-133">Displays errors at the command line.</span></span> <span data-ttu-id="c816f-134">此参数很少使用，但当你在命令中设置表达式的格式 `Format-Wide` ，并且表达式似乎无法正常工作时，可将其用作调试帮助。</span><span class="sxs-lookup"><span data-stu-id="c816f-134">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Wide` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="c816f-135">-Expand</span><span class="sxs-lookup"><span data-stu-id="c816f-135">-Expand</span></span>

<span data-ttu-id="c816f-136">设置集合对象以及集合中的对象的格式。</span><span class="sxs-lookup"><span data-stu-id="c816f-136">Formats the collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="c816f-137">此参数旨在用于设置支持 ICollection (System.Collections) 接口的对象的格式。</span><span class="sxs-lookup"><span data-stu-id="c816f-137">This parameter is designed to format objects that support the ICollection (System.Collections) interface.</span></span> <span data-ttu-id="c816f-138">默认值为 **EnumOnly** 。</span><span class="sxs-lookup"><span data-stu-id="c816f-138">The default value is **EnumOnly** .</span></span>

<span data-ttu-id="c816f-139">有效值是：</span><span class="sxs-lookup"><span data-stu-id="c816f-139">Valid values are:</span></span>

- <span data-ttu-id="c816f-140">EnumOnly：显示集合中的对象的属性。</span><span class="sxs-lookup"><span data-stu-id="c816f-140">EnumOnly: Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="c816f-141">CoreOnly：显示集合对象的属性。</span><span class="sxs-lookup"><span data-stu-id="c816f-141">CoreOnly: Displays the properties of the collection object.</span></span>
- <span data-ttu-id="c816f-142">Both：显示集合对象的属性以及集合中的对象的属性。</span><span class="sxs-lookup"><span data-stu-id="c816f-142">Both: Displays the properties of the collection object and the properties of objects in the collection.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: EnumOnly
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c816f-143">-Force</span><span class="sxs-lookup"><span data-stu-id="c816f-143">-Force</span></span>

<span data-ttu-id="c816f-144">指示此 cmdlet 将覆盖阻止命令成功的限制，因此更改不会危及安全性。</span><span class="sxs-lookup"><span data-stu-id="c816f-144">Indicates that this cmdlet overrides restrictions that prevent the command from succeeding, just so the changes do not compromise security.</span></span> <span data-ttu-id="c816f-145">例如， **Force** 将覆盖只读属性或创建目录来完成文件路径，但它不会尝试更改文件权限。</span><span class="sxs-lookup"><span data-stu-id="c816f-145">For example, **Force** will override the read-only attribute or create directories to complete a file path, but it will not attempt to change file permissions.</span></span>

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

### <span data-ttu-id="c816f-146">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="c816f-146">-GroupBy</span></span>

<span data-ttu-id="c816f-147">基于共享属性或值设置组中输出的格式。</span><span class="sxs-lookup"><span data-stu-id="c816f-147">Formats the output in groups based on a shared property or value.</span></span> <span data-ttu-id="c816f-148">请输入表达式或输出的属性。</span><span class="sxs-lookup"><span data-stu-id="c816f-148">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="c816f-149">**GroupBy** 参数的值可以是新的计算属性。</span><span class="sxs-lookup"><span data-stu-id="c816f-149">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="c816f-150">计算属性可以是脚本块，也可以是哈希表。</span><span class="sxs-lookup"><span data-stu-id="c816f-150">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="c816f-151">有效的键-值对为：</span><span class="sxs-lookup"><span data-stu-id="c816f-151">Valid key-value pairs are:</span></span>

- <span data-ttu-id="c816f-152">名称 (或标签) - `<string>`</span><span class="sxs-lookup"><span data-stu-id="c816f-152">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="c816f-153">Expression `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="c816f-153">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="c816f-154">说明符 `<string>`</span><span class="sxs-lookup"><span data-stu-id="c816f-154">FormatString - `<string>`</span></span>

<span data-ttu-id="c816f-155">有关详细信息，请参阅 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="c816f-155">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c816f-156">-InputObject</span><span class="sxs-lookup"><span data-stu-id="c816f-156">-InputObject</span></span>

<span data-ttu-id="c816f-157">指定要设置格式的对象。</span><span class="sxs-lookup"><span data-stu-id="c816f-157">Specifies the objects to format.</span></span> <span data-ttu-id="c816f-158">输入一个包含对象的变量，或键入可获取对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="c816f-158">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c816f-159">-Property</span><span class="sxs-lookup"><span data-stu-id="c816f-159">-Property</span></span>

<span data-ttu-id="c816f-160">指定要在屏幕上显示的对象属性及其显示顺序。</span><span class="sxs-lookup"><span data-stu-id="c816f-160">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="c816f-161">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="c816f-161">Wildcards are permitted.</span></span>

<span data-ttu-id="c816f-162">如果省略此参数，则屏幕上显示的属性取决于要显示的对象。</span><span class="sxs-lookup"><span data-stu-id="c816f-162">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="c816f-163">参数名称 "Property" 是可选的。</span><span class="sxs-lookup"><span data-stu-id="c816f-163">The parameter name "Property" is optional.</span></span> <span data-ttu-id="c816f-164">不能在同一命令中使用 **Property** 和 **View** 参数。</span><span class="sxs-lookup"><span data-stu-id="c816f-164">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="c816f-165">**Property** 参数的值可以是新的计算属性。</span><span class="sxs-lookup"><span data-stu-id="c816f-165">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="c816f-166">计算属性可以是脚本块，也可以是哈希表。</span><span class="sxs-lookup"><span data-stu-id="c816f-166">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="c816f-167">有效的键-值对为：</span><span class="sxs-lookup"><span data-stu-id="c816f-167">Valid key-value pairs are:</span></span>

- <span data-ttu-id="c816f-168">Expression `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="c816f-168">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="c816f-169">说明符 `<string>`</span><span class="sxs-lookup"><span data-stu-id="c816f-169">FormatString - `<string>`</span></span>

<span data-ttu-id="c816f-170">有关详细信息，请参阅 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="c816f-170">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c816f-171">-ShowError</span><span class="sxs-lookup"><span data-stu-id="c816f-171">-ShowError</span></span>

<span data-ttu-id="c816f-172">通过管道发送错误。</span><span class="sxs-lookup"><span data-stu-id="c816f-172">Sends errors through the pipeline.</span></span> <span data-ttu-id="c816f-173">此参数很少使用，但当你在命令中设置表达式的格式 `Format-Wide` ，并且表达式似乎无法正常工作时，可将其用作调试帮助。</span><span class="sxs-lookup"><span data-stu-id="c816f-173">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Wide` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="c816f-174">-View</span><span class="sxs-lookup"><span data-stu-id="c816f-174">-View</span></span>

<span data-ttu-id="c816f-175">指定替代表格式或视图的名称。</span><span class="sxs-lookup"><span data-stu-id="c816f-175">Specifies the name of an alternate table format or view.</span></span> <span data-ttu-id="c816f-176">不能在同一命令中使用 **Property** 和 **View** 参数。</span><span class="sxs-lookup"><span data-stu-id="c816f-176">You cannot use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="c816f-177">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c816f-177">CommonParameters</span></span>

<span data-ttu-id="c816f-178">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c816f-178">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c816f-179">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c816f-179">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c816f-180">输入</span><span class="sxs-lookup"><span data-stu-id="c816f-180">INPUTS</span></span>

### <span data-ttu-id="c816f-181">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="c816f-181">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="c816f-182">可以通过管道将任何对象传递给 `Format-Wide` 。</span><span class="sxs-lookup"><span data-stu-id="c816f-182">You can pipe any object to `Format-Wide`.</span></span>

## <span data-ttu-id="c816f-183">输出</span><span class="sxs-lookup"><span data-stu-id="c816f-183">OUTPUTS</span></span>

### <span data-ttu-id="c816f-184">Microsoft.PowerShell.Commands.Internal.Format</span><span class="sxs-lookup"><span data-stu-id="c816f-184">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="c816f-185">`Format-Wide` 返回表示表的格式对象。</span><span class="sxs-lookup"><span data-stu-id="c816f-185">`Format-Wide` returns format objects that represent the table.</span></span>

## <span data-ttu-id="c816f-186">注释</span><span class="sxs-lookup"><span data-stu-id="c816f-186">NOTES</span></span>

<span data-ttu-id="c816f-187">还可以 `Format-Wide` 通过其内置别名来引用 `fw` 。</span><span class="sxs-lookup"><span data-stu-id="c816f-187">You can also refer to `Format-Wide` by its built-in alias, `fw`.</span></span> <span data-ttu-id="c816f-188">有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="c816f-188">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="c816f-189">**GroupBy** 参数假定对象已排序。</span><span class="sxs-lookup"><span data-stu-id="c816f-189">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="c816f-190">使用 `Sort-Object` `Format-Custom` 来对对象进行分组之前，请使用。</span><span class="sxs-lookup"><span data-stu-id="c816f-190">Use `Sort-Object` before using `Format-Custom` to group the objects.</span></span>

<span data-ttu-id="c816f-191">使用 **View** 参数可以指定表的替代格式。</span><span class="sxs-lookup"><span data-stu-id="c816f-191">The **View** parameter lets you specify an alternate format for the table.</span></span> <span data-ttu-id="c816f-192">你可以使用 PowerShell 目录的文件中定义的视图 `*.format.PS1XML` ，也可以在新的 types.ps1xml 文件中创建自己的视图，并使用 `Update-FormatData` cmdlet 将它们包含在 powershell 中。</span><span class="sxs-lookup"><span data-stu-id="c816f-192">You can use the views defined in the `*.format.PS1XML` files in the PowerShell directory or you can create your own views in new PS1XML files and use the `Update-FormatData` cmdlet to include them in PowerShell.</span></span>

<span data-ttu-id="c816f-193">**View** 参数的替代视图必须使用表格式;否则，该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="c816f-193">The alternate view for the **View** parameter must use table format; if it does not, the command fails.</span></span> <span data-ttu-id="c816f-194">如果替代视图是一个列表，请使用 `Format-List` 。</span><span class="sxs-lookup"><span data-stu-id="c816f-194">If the alternate view is a list, use `Format-List`.</span></span> <span data-ttu-id="c816f-195">如果替代视图既不是列表也不是表格，请使用 Format-Custom。</span><span class="sxs-lookup"><span data-stu-id="c816f-195">If the alternate view is neither a list nor a table, use Format-Custom.</span></span>

## <span data-ttu-id="c816f-196">相关链接</span><span class="sxs-lookup"><span data-stu-id="c816f-196">RELATED LINKS</span></span>

[<span data-ttu-id="c816f-197">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="c816f-197">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="c816f-198">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="c816f-198">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="c816f-199">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="c816f-199">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="c816f-200">Format-List</span><span class="sxs-lookup"><span data-stu-id="c816f-200">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="c816f-201">Format-Table</span><span class="sxs-lookup"><span data-stu-id="c816f-201">Format-Table</span></span>](Format-Table.md)
