---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/21/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-csv?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Csv
ms.openlocfilehash: 483f3767af4df9e5e044ab3b46811f22b63a5723
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93197968"
---
# <span data-ttu-id="1d2b7-103">ConvertFrom-Csv</span><span class="sxs-lookup"><span data-stu-id="1d2b7-103">ConvertFrom-Csv</span></span>

## <span data-ttu-id="1d2b7-104">摘要</span><span class="sxs-lookup"><span data-stu-id="1d2b7-104">SYNOPSIS</span></span>
<span data-ttu-id="1d2b7-105">将采用逗号分隔值 (CSV) 格式的对象属性转换为原始对象的 CSV 版本。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-105">Converts object properties in comma-separated value (CSV) format into CSV versions of the original objects.</span></span>

## <span data-ttu-id="1d2b7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1d2b7-106">SYNTAX</span></span>

### <span data-ttu-id="1d2b7-107">Delimiter（默认值）</span><span class="sxs-lookup"><span data-stu-id="1d2b7-107">Delimiter (Default)</span></span>

```
ConvertFrom-Csv [-InputObject] <psobject[]> [[-Delimiter] <char>] [-Header <string[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="1d2b7-108">UseCulture</span><span class="sxs-lookup"><span data-stu-id="1d2b7-108">UseCulture</span></span>

```
ConvertFrom-Csv [-InputObject] <psobject[]> -UseCulture [-Header <string[]>] [<CommonParameters>]
```

## <span data-ttu-id="1d2b7-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1d2b7-109">DESCRIPTION</span></span>

<span data-ttu-id="1d2b7-110">`ConvertFrom-Csv`Cmdlet 可从 cmdlet 生成的 CSV 可变长度字符串创建对象 `ConvertTo-Csv` 。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-110">The `ConvertFrom-Csv` cmdlet creates objects from CSV variable-length strings that are generated by the `ConvertTo-Csv` cmdlet.</span></span>

<span data-ttu-id="1d2b7-111">您可以使用此 cmdlet 的参数来指定列标题行（它确定生成对象的属性名称），以指定项分隔符，或指示此 cmdlet 将当前区域性的列表分隔符用作分隔符。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-111">You can use the parameters of this cmdlet to specify the column header row, which determines the property names of the resulting objects, to specify the item delimiter, or to direct this cmdlet to use the list separator for the current culture as the delimiter.</span></span>

<span data-ttu-id="1d2b7-112">创建的对象 `ConvertFrom-Csv` 是原始对象的 CSV 版本。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-112">The objects that `ConvertFrom-Csv` creates are CSV versions of the original objects.</span></span> <span data-ttu-id="1d2b7-113">CSV 对象的属性值是原始对象的属性值的字符串版本。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-113">The property values of the CSV objects are string versions of the property values of the original objects.</span></span> <span data-ttu-id="1d2b7-114">对象的 CSV 版本不包含任何方法。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-114">The CSV versions of the objects do not have any methods.</span></span>

<span data-ttu-id="1d2b7-115">你还可以使用 `Export-Csv` 和 `Import-Csv` cmdlet 将对象转换为文件中的 CSV 字符串 (和后) 。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-115">You can also use the `Export-Csv` and `Import-Csv` cmdlets to convert objects to CSV strings in a file (and back).</span></span> <span data-ttu-id="1d2b7-116">这些 cmdlet 与 `ConvertTo-Csv` 和 `ConvertFrom-Csv` cmdlet 相同，不同之处在于它们会将 CSV 字符串保存在文件中。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-116">These cmdlets are the same as the `ConvertTo-Csv` and `ConvertFrom-Csv` cmdlets, except that they save the CSV strings in a file.</span></span>

## <span data-ttu-id="1d2b7-117">示例</span><span class="sxs-lookup"><span data-stu-id="1d2b7-117">EXAMPLES</span></span>

### <span data-ttu-id="1d2b7-118">示例1：将本地计算机上的进程转换为 CSV 格式</span><span class="sxs-lookup"><span data-stu-id="1d2b7-118">Example 1: Convert processes on the local computer to CSV format</span></span>

<span data-ttu-id="1d2b7-119">此示例显示了如何将本地计算机上的进程转换为 CSV 格式，然后将其还原为对象形式。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-119">This example shows how to convert the processes on the local computer into CSV format and then restore them to object form.</span></span>

```powershell
$P = Get-Process | ConvertTo-Csv
$P | ConvertFrom-Csv
```

<span data-ttu-id="1d2b7-120">`Get-Process`Cmdlet 将进程向下发送到 `ConvertTo-Csv` 。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-120">The `Get-Process` cmdlet sends the processes down the pipeline to `ConvertTo-Csv`.</span></span> <span data-ttu-id="1d2b7-121">`ConvertTo-Csv`Cmdlet 可将进程对象转换为一系列 CSV 字符串。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-121">The `ConvertTo-Csv` cmdlet converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="1d2b7-122">该 `ConvertFrom-Csv` cmdlet 将 csv 字符串转换为原始进程对象的 csv 版本。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-122">The `ConvertFrom-Csv` cmdlet converts the CSV strings into CSV versions of the original process objects.</span></span> <span data-ttu-id="1d2b7-123">CSV 字符串保存在 `$P` 变量中。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-123">The CSV strings are saved in the `$P` variable.</span></span>

### <span data-ttu-id="1d2b7-124">示例2：将数据对象转换为 CSV 格式，然后转换为 CSV 对象格式</span><span class="sxs-lookup"><span data-stu-id="1d2b7-124">Example 2: Convert a data object to CSV format and then to CSV object format</span></span>

<span data-ttu-id="1d2b7-125">此示例演示如何将数据对象转换为 CSV 格式，然后再转换为 CSV 对象格式。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-125">This example shows how to convert a data object to CSV format and then to CSV object format.</span></span>

```powershell
$Date = Get-Date | ConvertTo-Csv -Delimiter ';'
ConvertFrom-Csv -InputObject $Date -Delimiter ';'
```

<span data-ttu-id="1d2b7-126">第一个命令使用将 `Get-Date` 当前日期和时间向下发送到 `ConvertTo-Csv` 。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-126">The first command uses `Get-Date` to send the current date and time down the pipeline to `ConvertTo-Csv`.</span></span> <span data-ttu-id="1d2b7-127">`ConvertTo-Csv`Cmdlet 将日期对象转换为一系列 CSV 字符串。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-127">The `ConvertTo-Csv` cmdlet converts the date object to a series of CSV strings.</span></span>
<span data-ttu-id="1d2b7-128">**分隔符** 参数用于指定分号分隔符。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-128">The **Delimiter** parameter is used to specify a semicolon delimiter.</span></span> <span data-ttu-id="1d2b7-129">字符串保存在 `$Date` 变量中。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-129">The strings are saved in the `$Date` variable.</span></span>

### <span data-ttu-id="1d2b7-130">示例3：使用 header 参数更改属性的名称</span><span class="sxs-lookup"><span data-stu-id="1d2b7-130">Example 3: Use the header parameter to change the names of properties</span></span>

<span data-ttu-id="1d2b7-131">此示例演示如何使用的 **Header** 参数 `ConvertFrom-Csv` 来更改生成的导入对象中的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-131">This example shows how to use the **Header** parameter of `ConvertFrom-Csv` to change the names of properties in the resulting imported object.</span></span>

```powershell
$J = Start-Job -ScriptBlock { Get-Process } | ConvertTo-Csv  -NoTypeInformation
$Header = 'State', 'MoreData', 'StatusMessage', 'Location', 'Command', 'StateInfo', 'Finished', 'InstanceId', 'Id', 'Name', 'ChildJobs', 'BeginTime', 'EndTime', 'JobType', 'Output', 'Error', 'Progress', 'Verbose', 'Debug', 'Warning', 'Information'
# Delete the default header from $J
$J = $J[1..($J.count - 1)]
$J | ConvertFrom-Csv -Header $Header
```

```Output
State         : Running
MoreData      : True
StatusMessage :
Location      : localhost
Command       : Get-Process
StateInfo     : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : a259eb63-6824-4b97-a033-305108ae1c2e
Id            : 1
Name          : Job1
ChildJobs     : System.Collections.Generic.List`1[System.Management.Automation.Job]
BeginTime     : 12/20/2018 18:59:57
EndTime       :
JobType       : BackgroundJob
Output        : System.Management.Automation.PSDataCollection`1[System.Management.Automation.PSObject]
Error         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ErrorRecord]
Progress      : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ProgressRecord]
Verbose       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.VerboseRecord]
Debug         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.DebugRecord]
Warning       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.WarningRecord]
Information   : System.Management.Automation.PSDataCollection`1[System.Management.Automation.InformationRecord]
```

<span data-ttu-id="1d2b7-132">`Start-Job`Cmdlet 可启动运行的后台作业 `Get-Process` 。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-132">The `Start-Job` cmdlet starts a background job that runs `Get-Process`.</span></span> <span data-ttu-id="1d2b7-133">作业对象将向下发送到管道 `ConvertTo-Csv` 并转换为 CSV 字符串。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-133">A job object is sent down the pipeline to `ConvertTo-Csv` and converted to a CSV string.</span></span> <span data-ttu-id="1d2b7-134">**NoTypeInformation** 参数从 CSV 输出中删除类型信息标头，在 PowerShell Core 中是可选的。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-134">The **NoTypeInformation** parameter removes the type information header from CSV output and is optional in PowerShell Core.</span></span> <span data-ttu-id="1d2b7-135">`$Header`变量包含一个自定义标头，用于替换以下默认值： **HasMoreData** 、 **JobStateInfo** 、 **PSBeginTime** 、 **PSEndTime** 和 **PSJobTypeName** 。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-135">The `$Header` variable contains a custom header that replaces the following default values: **HasMoreData** , **JobStateInfo** , **PSBeginTime** , **PSEndTime** , and **PSJobTypeName** .</span></span> <span data-ttu-id="1d2b7-136">该 `$J` 变量包含 CSV 字符串，用于删除默认标头。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-136">The `$J` variable contains the CSV string and is used to remove the default header.</span></span> <span data-ttu-id="1d2b7-137">该 `ConvertFrom-Csv` cmdlet 将 CSV 字符串转换为 **PSCustomObject** ，并使用 **Header** 参数来应用 `$Header` 变量。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-137">The `ConvertFrom-Csv` cmdlet converts the CSV string into a **PSCustomObject** and uses the **Header** parameter to apply the `$Header` variable.</span></span>

### <span data-ttu-id="1d2b7-138">示例4：转换服务对象的 CSV 字符串</span><span class="sxs-lookup"><span data-stu-id="1d2b7-138">Example 4: Convert CSV strings of service objects</span></span>

<span data-ttu-id="1d2b7-139">此示例演示如何将 `ConvertFrom-Csv` cmdlet 与 **UseCulture** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-139">This example shows how to use the `ConvertFrom-Csv` cmdlet with the **UseCulture** parameter.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
$Services = (Get-Service | ConvertTo-Csv)
ConvertFrom-Csv -InputObject $Services -UseCulture
```

<span data-ttu-id="1d2b7-140">`Get-Culture`Cmdlet 使用嵌套属性 **TextInfo** 和 **ListSeparator** 获取当前区域性的默认列表分隔符。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-140">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** to get the current culture's default list separator.</span></span> <span data-ttu-id="1d2b7-141">`Get-Service`Cmdlet 将服务对象向下发送到 `ConvertTo-Csv` 。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-141">The `Get-Service` cmdlet sends service objects down the pipeline to `ConvertTo-Csv`.</span></span> <span data-ttu-id="1d2b7-142">将 `ConvertTo-Csv` 服务对象转换为一系列 CSV 字符串。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-142">The `ConvertTo-Csv` converts the service objects to a series of CSV strings.</span></span> <span data-ttu-id="1d2b7-143">CSV 字符串存储在 `$Services` 变量中。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-143">The CSV strings are stored in the `$Services` variable.</span></span> <span data-ttu-id="1d2b7-144">`ConvertFrom-Csv`Cmdlet 使用 **InputObject** 参数，并从变量转换 CSV 字符串 `$Services` 。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-144">The `ConvertFrom-Csv` cmdlet uses the **InputObject** parameter and converts the CSV strings from the `$Services` variable.</span></span> <span data-ttu-id="1d2b7-145">**UseCulture** 参数使用当前区域性的默认列表分隔符。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-145">The **UseCulture** parameter uses the current culture's default list separator.</span></span>

<span data-ttu-id="1d2b7-146">使用 **UseCulture** 参数时，请确保当前区域性的默认列表分隔符与 CSV 字符串中使用的分隔符相匹配。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-146">When the **UseCulture** parameter is used, be sure that the current culture's default list separator matches the delimiter used in the CSV strings.</span></span> <span data-ttu-id="1d2b7-147">否则， `ConvertFrom-Csv` 无法从 CSV 字符串生成对象。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-147">Otherwise, `ConvertFrom-Csv` cannot generate objects from the CSV strings.</span></span>

## <span data-ttu-id="1d2b7-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1d2b7-148">PARAMETERS</span></span>

### <span data-ttu-id="1d2b7-149">-Delimiter</span><span class="sxs-lookup"><span data-stu-id="1d2b7-149">-Delimiter</span></span>

<span data-ttu-id="1d2b7-150">指定用于分隔 CSV 字符串中的属性值的分隔符。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-150">Specifies the delimiter that separates the property values in the CSV strings.</span></span>
<span data-ttu-id="1d2b7-151">默认值为逗号 (,)。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-151">The default is a comma (,).</span></span>

<span data-ttu-id="1d2b7-152">输入一个字符，例如冒号 (:)。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-152">Enter a character, such as a colon (:).</span></span>
<span data-ttu-id="1d2b7-153">若要指定分号 (; ) 将其括在单引号内。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-153">To specify a semicolon (;) enclose it in single quotation marks.</span></span>

<span data-ttu-id="1d2b7-154">如果在文件中指定了实际字符串分隔符以外的其他字符，则 `ConvertFrom-Csv` 无法从 CSV 字符串创建对象，并将返回 csv 字符串。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-154">If you specify a character other than the actual string delimiter in the file, `ConvertFrom-Csv` cannot create the objects from the CSV strings and will return the CSV strings.</span></span>

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d2b7-155">-Header</span><span class="sxs-lookup"><span data-stu-id="1d2b7-155">-Header</span></span>

<span data-ttu-id="1d2b7-156">为导入的字符串指定替换列标题行。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-156">Specifies an alternate column header row for the imported string.</span></span> <span data-ttu-id="1d2b7-157">列标题确定由创建的对象的属性名称 `ConvertFrom-Csv` 。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-157">The column header determines the property names of the objects created by `ConvertFrom-Csv`.</span></span>

<span data-ttu-id="1d2b7-158">以逗号分隔的列表形式输入列标头。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-158">Enter column headers as a comma-separated list.</span></span> <span data-ttu-id="1d2b7-159">不要将标头字符串括在引号内。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-159">Do not enclose the header string in quotation marks.</span></span> <span data-ttu-id="1d2b7-160">用单引号将每个列标题括起来。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-160">Enclose each column header in single quotation marks.</span></span>

<span data-ttu-id="1d2b7-161">如果输入的列标题少于数据列，则会丢弃剩余的数据列。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-161">If you enter fewer column headers than there are data columns, the remaining data columns are discarded.</span></span> <span data-ttu-id="1d2b7-162">如果输入的列标题多于数据列，则将创建包含空数据列的其他列标题。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-162">If you enter more column headers than there are data columns, the additional column headers are created with empty data columns.</span></span>

<span data-ttu-id="1d2b7-163">使用 **Header** 参数时，请省略 CSV 字符串中的列标题字符串。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-163">When using the **Header** parameter, omit the column header string from the CSV strings.</span></span> <span data-ttu-id="1d2b7-164">否则，此 cmdlet 将从标题行中的项创建额外的对象。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-164">Otherwise, this cmdlet creates an extra object from the items in the header row.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d2b7-165">-InputObject</span><span class="sxs-lookup"><span data-stu-id="1d2b7-165">-InputObject</span></span>

<span data-ttu-id="1d2b7-166">指定要转换为对象的 CSV 字符串。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-166">Specifies the CSV strings to be converted to objects.</span></span> <span data-ttu-id="1d2b7-167">输入一个包含 CSV 字符串的变量，或键入可获取 CSV 字符串的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-167">Enter a variable that contains the CSV strings or type a command or expression that gets the CSV strings.</span></span> <span data-ttu-id="1d2b7-168">还可以通过管道将 CSV 字符串传递给 `ConvertFrom-Csv` 。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-168">You can also pipe the CSV strings to `ConvertFrom-Csv`.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1d2b7-169">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="1d2b7-169">-UseCulture</span></span>

<span data-ttu-id="1d2b7-170">将当前区域性的列表分隔符用作项分隔符。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-170">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="1d2b7-171">若要查找区域性的列表分隔符，请使用以下命令： `(Get-Culture).TextInfo.ListSeparator` 。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-171">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d2b7-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1d2b7-172">CommonParameters</span></span>

<span data-ttu-id="1d2b7-173">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1d2b7-174">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1d2b7-175">输入</span><span class="sxs-lookup"><span data-stu-id="1d2b7-175">INPUTS</span></span>

### <span data-ttu-id="1d2b7-176">System.String</span><span class="sxs-lookup"><span data-stu-id="1d2b7-176">System.String</span></span>

<span data-ttu-id="1d2b7-177">可以通过管道将 CSV 字符串传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-177">You can pipe CSV strings to this cmdlet.</span></span>

## <span data-ttu-id="1d2b7-178">输出</span><span class="sxs-lookup"><span data-stu-id="1d2b7-178">OUTPUTS</span></span>

### <span data-ttu-id="1d2b7-179">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="1d2b7-179">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="1d2b7-180">此 cmdlet 将返回 CSV 字符串中的属性所描述的对象。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-180">This cmdlet returns the objects described by the properties in the CSV strings.</span></span>

## <span data-ttu-id="1d2b7-181">注释</span><span class="sxs-lookup"><span data-stu-id="1d2b7-181">NOTES</span></span>

<span data-ttu-id="1d2b7-182">由于导入的对象是对象类型的 CSV 版本，因此它们不会被格式化对象类型的非 CSV 版本的 PowerShell 类型格式条目识别和格式化。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-182">Because the imported objects are CSV versions of the object type, they are not recognized and formatted by the PowerShell type formatting entries that format the non-CSV versions of the object type.</span></span>

<span data-ttu-id="1d2b7-183">在 CSV 格式中，通过以逗号分隔的对象属性值列表来表示每个对象。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-183">In CSV format, each object is represented by a comma-separated list of the property values of the object.</span></span> <span data-ttu-id="1d2b7-184">属性值使用对象) 的 **ToString ( # B2** 方法转换为字符串 (，因此它们由属性值的名称表示。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-184">The property values are converted to strings (by using the **ToString()** method of the object), so they are represented by the name of the property value.</span></span> <span data-ttu-id="1d2b7-185">此 cmdlet 不会导出对象的方法。</span><span class="sxs-lookup"><span data-stu-id="1d2b7-185">This cmdlet does not export the methods of the object.</span></span>

## <span data-ttu-id="1d2b7-186">相关链接</span><span class="sxs-lookup"><span data-stu-id="1d2b7-186">RELATED LINKS</span></span>

[<span data-ttu-id="1d2b7-187">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="1d2b7-187">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="1d2b7-188">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="1d2b7-188">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="1d2b7-189">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="1d2b7-189">Import-Csv</span></span>](Import-Csv.md)