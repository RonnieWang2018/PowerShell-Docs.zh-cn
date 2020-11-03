---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-content?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Content
ms.openlocfilehash: e2b78a2062ac551b76c0a1b6b31d721bfefcf3bd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93198298"
---
# <span data-ttu-id="b5f35-103">Get-Content</span><span class="sxs-lookup"><span data-stu-id="b5f35-103">Get-Content</span></span>

## <span data-ttu-id="b5f35-104">摘要</span><span class="sxs-lookup"><span data-stu-id="b5f35-104">SYNOPSIS</span></span>
<span data-ttu-id="b5f35-105">获取位于指定位置的项的内容。</span><span class="sxs-lookup"><span data-stu-id="b5f35-105">Gets the content of the item at the specified location.</span></span>

## <span data-ttu-id="b5f35-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b5f35-106">SYNTAX</span></span>

### <span data-ttu-id="b5f35-107">Path（默认值）</span><span class="sxs-lookup"><span data-stu-id="b5f35-107">Path (Default)</span></span>

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] [-Path] <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-UseTransaction] [-Delimiter <String>] [-Wait] [-Raw]
 [-Encoding <FileSystemCmdletProviderEncoding>] [-Stream <String>] [<CommonParameters>]
```

### <span data-ttu-id="b5f35-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b5f35-108">LiteralPath</span></span>

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] -LiteralPath <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-UseTransaction] [-Delimiter <String>] [-Wait] [-Raw]
 [-Encoding <FileSystemCmdletProviderEncoding>] [-Stream <String>] [<CommonParameters>]
```

## <span data-ttu-id="b5f35-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b5f35-109">DESCRIPTION</span></span>

<span data-ttu-id="b5f35-110">该 `Get-Content` cmdlet 将获取由路径指定的位置处的项的内容，例如，文件中的文本或函数的内容。</span><span class="sxs-lookup"><span data-stu-id="b5f35-110">The `Get-Content` cmdlet gets the content of the item at the location specified by the path, such as the text in a file or the content of a function.</span></span> <span data-ttu-id="b5f35-111">对于文件，内容每次读取一行，并返回对象的集合，其中每个对象表示一行内容。</span><span class="sxs-lookup"><span data-stu-id="b5f35-111">For files, the content is read one line at a time and returns a collection of objects, each of which represents a line of content.</span></span>

<span data-ttu-id="b5f35-112">从 PowerShell 3.0 开始， `Get-Content` 还可以从项的开头或结尾获取指定数目的行。</span><span class="sxs-lookup"><span data-stu-id="b5f35-112">Beginning in PowerShell 3.0, `Get-Content` can also get a specified number of lines from the beginning or end of an item.</span></span>

## <span data-ttu-id="b5f35-113">示例</span><span class="sxs-lookup"><span data-stu-id="b5f35-113">EXAMPLES</span></span>

### <span data-ttu-id="b5f35-114">示例 1：获取文本文件的内容</span><span class="sxs-lookup"><span data-stu-id="b5f35-114">Example 1: Get the content of a text file</span></span>

<span data-ttu-id="b5f35-115">此示例获取当前目录中的文件的内容。</span><span class="sxs-lookup"><span data-stu-id="b5f35-115">This example gets the content of a file in the current directory.</span></span> <span data-ttu-id="b5f35-116">`LineNumbers.txt`文件包含100行，格式 **为第 X 行** ，在几个示例中使用。</span><span class="sxs-lookup"><span data-stu-id="b5f35-116">The `LineNumbers.txt` file contains 100 lines in the format, **This is Line X** and is used in several examples.</span></span>

```powershell
1..100 | ForEach-Object { Add-Content -Path .\LineNumbers.txt -Value "This is line $_." }
Get-Content -Path .\LineNumbers.txt
```

```Output
This is Line 1
This is Line 2
...
This is line 99.
This is line 100.
```

<span data-ttu-id="b5f35-117">数组值1-100 将由管道发送到 `ForEach-Object` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b5f35-117">The array values 1-100 are sent down the pipeline to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="b5f35-118">`ForEach-Object` 使用带有 cmdlet 的脚本块 `Add-Content` 来创建 `LineNumbers.txt` 文件。</span><span class="sxs-lookup"><span data-stu-id="b5f35-118">`ForEach-Object` uses a script block with the `Add-Content` cmdlet to create the `LineNumbers.txt` file.</span></span> <span data-ttu-id="b5f35-119">变量 `$_` 表示数组值，因为每个对象都沿管道向下发送。</span><span class="sxs-lookup"><span data-stu-id="b5f35-119">The variable `$_` represents the array values as each object is sent down the pipeline.</span></span> <span data-ttu-id="b5f35-120">`Get-Content`Cmdlet 使用 **Path** 参数指定 `LineNumbers.txt` 文件，并在 PowerShell 控制台中显示内容。</span><span class="sxs-lookup"><span data-stu-id="b5f35-120">The `Get-Content` cmdlet uses the **Path** parameter to specify the `LineNumbers.txt` file and displays the content in the PowerShell console.</span></span>

### <span data-ttu-id="b5f35-121">示例2：限制 Get-Content 返回的行数</span><span class="sxs-lookup"><span data-stu-id="b5f35-121">Example 2: Limit the number of lines Get-Content returns</span></span>

<span data-ttu-id="b5f35-122">此命令获取文件的前五行。</span><span class="sxs-lookup"><span data-stu-id="b5f35-122">This command gets the first five lines of a file.</span></span> <span data-ttu-id="b5f35-123">**TotalCount** 参数用于获取前五行内容。</span><span class="sxs-lookup"><span data-stu-id="b5f35-123">The **TotalCount** parameter is used to gets the first five lines of content.</span></span> <span data-ttu-id="b5f35-124">此示例使用 `LineNumbers.txt` 在示例1中创建的文件。</span><span class="sxs-lookup"><span data-stu-id="b5f35-124">This example uses the `LineNumbers.txt` file that was created in Example 1.</span></span>

```powershell
Get-Content -Path .\LineNumbers.txt -TotalCount 5
```

```Output
This is Line 1
This is Line 2
This is Line 3
This is Line 4
This is Line 5
```

### <span data-ttu-id="b5f35-125">示例3：从文本文件获取特定内容行</span><span class="sxs-lookup"><span data-stu-id="b5f35-125">Example 3: Get a specific line of content from a text file</span></span>

<span data-ttu-id="b5f35-126">此命令从文件中获取特定数量的行，然后仅显示该内容的最后一行。</span><span class="sxs-lookup"><span data-stu-id="b5f35-126">This command gets a specific number of lines from a file and then displays only the last line of that content.</span></span> <span data-ttu-id="b5f35-127">**TotalCount** 参数获取前25行内容。</span><span class="sxs-lookup"><span data-stu-id="b5f35-127">The **TotalCount** parameter gets the first 25 lines of content.</span></span> <span data-ttu-id="b5f35-128">此示例使用 `LineNumbers.txt` 在示例1中创建的文件。</span><span class="sxs-lookup"><span data-stu-id="b5f35-128">This example uses the `LineNumbers.txt` file that was created in Example 1.</span></span>

```powershell
(Get-Content -Path .\LineNumbers.txt -TotalCount 25)[-1]
```

```Output
This is Line 25
```

<span data-ttu-id="b5f35-129">`Get-Content`命令括在括号中，以便在执行下一步之前命令完成。</span><span class="sxs-lookup"><span data-stu-id="b5f35-129">The `Get-Content` command is wrapped in parentheses so that the command completes before going to the next step.</span></span> <span data-ttu-id="b5f35-130">`Get-Content`返回行的数组，这允许您在括号后添加索引表示法来检索特定行号。</span><span class="sxs-lookup"><span data-stu-id="b5f35-130">`Get-Content`returns an array of lines, this allows you to add the index notation after the parenthesis to retrieve a specific line number.</span></span> <span data-ttu-id="b5f35-131">在这种情况下， `[-1]` 索引将指定返回的25个行的返回数组中的最后一个索引。</span><span class="sxs-lookup"><span data-stu-id="b5f35-131">In this case, the `[-1]` index specifies the last index in the returned array of 25 retrieved lines.</span></span>

### <span data-ttu-id="b5f35-132">示例4：获取文本文件的最后一行</span><span class="sxs-lookup"><span data-stu-id="b5f35-132">Example 4: Get the last line of a text file</span></span>

<span data-ttu-id="b5f35-133">此命令从文件中获取第一行和最后一行内容。</span><span class="sxs-lookup"><span data-stu-id="b5f35-133">This command gets the first line and last line of content from a file.</span></span> <span data-ttu-id="b5f35-134">此示例使用 `LineNumbers.txt` 在示例1中创建的文件。</span><span class="sxs-lookup"><span data-stu-id="b5f35-134">This example uses the `LineNumbers.txt` file that was created in Example 1.</span></span>

```powershell
Get-Item -Path .\LineNumbers.txt | Get-Content -Tail 1
```

```Output
This is Line 100
```

<span data-ttu-id="b5f35-135">此示例使用 `Get-Item` cmdlet 演示可以通过管道将文件传输到参数中 `Get-Content` 。</span><span class="sxs-lookup"><span data-stu-id="b5f35-135">This example uses the `Get-Item` cmdlet to demonstrate that you can pipe files into the `Get-Content` parameter.</span></span> <span data-ttu-id="b5f35-136">**Tail** 参数获取文件的最后一行。</span><span class="sxs-lookup"><span data-stu-id="b5f35-136">The **Tail** parameter gets the last line of the file.</span></span> <span data-ttu-id="b5f35-137">此方法比检索所有行和使用 `[-1]` 索引表示法更快。</span><span class="sxs-lookup"><span data-stu-id="b5f35-137">This method is faster than retrieving all of the lines and using the `[-1]` index notation.</span></span>

### <span data-ttu-id="b5f35-138">示例5：获取备用数据流的内容</span><span class="sxs-lookup"><span data-stu-id="b5f35-138">Example 5: Get the content of an alternate data stream</span></span>

<span data-ttu-id="b5f35-139">此示例介绍如何使用 **Stream** 参数获取 Windows NTFS 卷上存储的文件的备用数据流的内容。</span><span class="sxs-lookup"><span data-stu-id="b5f35-139">This example describes how to use the **Stream** parameter to get the content of an alternate data stream for files stored on a Windows NTFS volume.</span></span> <span data-ttu-id="b5f35-140">在此示例中， `Set-Content` cmdlet 用于在名为的文件中创建示例内容 `Stream.txt` 。</span><span class="sxs-lookup"><span data-stu-id="b5f35-140">In this example, the `Set-Content` cmdlet is used to create sample content in a file named `Stream.txt`.</span></span>

```powershell
Set-Content -Path .\Stream.txt -Value 'This is the content of the Stream.txt file'
# Specify a wildcard to the Stream parameter to display all streams of the recently created file.
Get-Item -Path .\Stream.txt -Stream *
```

```Output
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : :$DATA
Length        : 44
```

```powershell
# Retrieve the content of the primary, or $DATA stream.
Get-Content -Path .\Stream.txt -Stream $DATA
```

```Output
This is the content of the Stream.txt file
```

```powershell
# Use the Stream parameter of Add-Content to create a new Stream containing sample content.
Add-Content -Path .\Stream.txt -Stream NewStream -Value 'Added a stream named NewStream to Stream.txt'
# Use Get-Item to verify the stream was created.
Get-Item -Path .\Stream.txt -Stream *
```

```Output
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : :$DATA
Length        : 44

PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt:NewStream
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt:NewStream
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : NewStream
Length        : 46
```

```powershell
# Retrieve the content of your newly created Stream.
Get-Content -Path .\Stream.txt -Stream NewStream
```

```Output
Added a stream named NewStream to Stream.txt
```

<span data-ttu-id="b5f35-141">**Stream** 参数是 [FileSystem 提供程序](../microsoft.powershell.core/about/about_filesystem_provider.md#stream-systemstring)的动态参数。</span><span class="sxs-lookup"><span data-stu-id="b5f35-141">The **Stream** parameter is a dynamic parameter of the [FileSystem provider](../microsoft.powershell.core/about/about_filesystem_provider.md#stream-systemstring).</span></span>
<span data-ttu-id="b5f35-142">默认情况下 `Get-Content` ，仅从主副本或流检索数据 `$DATA` 。</span><span class="sxs-lookup"><span data-stu-id="b5f35-142">By default `Get-Content` only retrieves data from the primary, or `$DATA` stream.</span></span> <span data-ttu-id="b5f35-143">**流** 可用于存储隐藏数据，如属性、安全设置或其他数据。</span><span class="sxs-lookup"><span data-stu-id="b5f35-143">**Streams** can be used to store hidden data such as attributes, security settings, or other data.</span></span>

### <span data-ttu-id="b5f35-144">示例6：获取原始内容</span><span class="sxs-lookup"><span data-stu-id="b5f35-144">Example 6: Get raw content</span></span>

<span data-ttu-id="b5f35-145">此示例中的命令以一个字符串而不是字符串数组的形式获取文件内容。</span><span class="sxs-lookup"><span data-stu-id="b5f35-145">The commands in this example get the contents of a file as one string, instead of an array of strings.</span></span> <span data-ttu-id="b5f35-146">默认情况下，如果没有 **原始** 动态参数，则内容将以换行符分隔的字符串数组的形式返回。</span><span class="sxs-lookup"><span data-stu-id="b5f35-146">By default, without the **Raw** dynamic parameter, content is returned as an array of newline-delimited strings.</span></span> <span data-ttu-id="b5f35-147">此示例使用 `LineNumbers.txt` 在示例中创建的文件</span><span class="sxs-lookup"><span data-stu-id="b5f35-147">This example uses the `LineNumbers.txt` file that was created in Example</span></span>
1.

```powershell
$raw = Get-Content -Path .\LineNumbers.txt -Raw
$lines = Get-Content -Path .\LineNumbers.txt
Write-Host "Raw contains $($raw.Count) lines."
Write-Host "Lines contains $($lines.Count) lines."
```

```Output
Raw contains 1 lines.
Lines contains 100 lines.
```

### <span data-ttu-id="b5f35-148">示例7：使用筛选器与 Get-Content</span><span class="sxs-lookup"><span data-stu-id="b5f35-148">Example 7: Use Filters with Get-Content</span></span>

<span data-ttu-id="b5f35-149">可以为 cmdlet 指定筛选器 `Get-Content` 。</span><span class="sxs-lookup"><span data-stu-id="b5f35-149">You can specify a filter to the `Get-Content` cmdlet.</span></span> <span data-ttu-id="b5f35-150">使用筛选器限定 **路径** 参数时，需要包含一个尾随星号 (`*`) ，以指示路径的内容。</span><span class="sxs-lookup"><span data-stu-id="b5f35-150">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="b5f35-151">以下命令将获取 `*.log` 目录中所有文件的内容 `C:\Temp` 。</span><span class="sxs-lookup"><span data-stu-id="b5f35-151">The following command gets the content of all `*.log` files in the `C:\Temp` directory.</span></span>

```powershell
Get-Content -Path C:\Temp\* -Filter *.log
```

### <span data-ttu-id="b5f35-152">示例8：将文件内容作为字节数组获取</span><span class="sxs-lookup"><span data-stu-id="b5f35-152">Example 8: Get file contents as a byte array</span></span>

<span data-ttu-id="b5f35-153">此示例演示如何将文件的内容作为 `[byte[]]` 单个对象获取。</span><span class="sxs-lookup"><span data-stu-id="b5f35-153">This example demonstrates how to get the contents of a file as a `[byte[]]` as a single object.</span></span>

```powershell
$byteArray = Get-Content -Path C:\temp\test.txt -Encoding Byte -Raw
Get-Member -InputObject $bytearray
```

```Output
   TypeName: System.Byte[]

Name           MemberType            Definition
----           ----------            ----------
Count          AliasProperty         Count = Length
Add            Method                int IList.Add(System.Object value)
```

<span data-ttu-id="b5f35-154">第一个命令使用 **Encoding** 参数从文件中获取字节流。</span><span class="sxs-lookup"><span data-stu-id="b5f35-154">The first command uses the **Encoding** parameter to get the stream of bytes from the file.</span></span>
<span data-ttu-id="b5f35-155">**Raw** 参数可确保以形式返回字节 `[System.Byte[]]` 。</span><span class="sxs-lookup"><span data-stu-id="b5f35-155">The **Raw** parameter ensures that the bytes are returned as a `[System.Byte[]]`.</span></span> <span data-ttu-id="b5f35-156">如果缺少 **原始** 参数，则返回值为字节流，由 PowerShell 解释为 `[System.Object[]]` 。</span><span class="sxs-lookup"><span data-stu-id="b5f35-156">If the **Raw** parameter was absent, the return value is a stream of bytes, which is interpreted by PowerShell as `[System.Object[]]`.</span></span>

## <span data-ttu-id="b5f35-157">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b5f35-157">PARAMETERS</span></span>

### <span data-ttu-id="b5f35-158">-Path</span><span class="sxs-lookup"><span data-stu-id="b5f35-158">-Path</span></span>

<span data-ttu-id="b5f35-159">指定获取内容的项的路径 `Get-Content` 。</span><span class="sxs-lookup"><span data-stu-id="b5f35-159">Specifies the path to an item where `Get-Content` gets the content.</span></span> <span data-ttu-id="b5f35-160">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="b5f35-160">Wildcard characters are permitted.</span></span> <span data-ttu-id="b5f35-161">此路径必须是指向该项的路径，而不是容器的路径。</span><span class="sxs-lookup"><span data-stu-id="b5f35-161">The paths must be paths to items, not to containers.</span></span> <span data-ttu-id="b5f35-162">例如，必须指定一个或多个文件的路径，而不是目录的路径。</span><span class="sxs-lookup"><span data-stu-id="b5f35-162">For example, you must specify a path to one or more files, not a path to a directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="b5f35-163">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b5f35-163">-LiteralPath</span></span>

<span data-ttu-id="b5f35-164">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="b5f35-164">Specifies a path to one or more locations.</span></span> <span data-ttu-id="b5f35-165">**LiteralPath** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="b5f35-165">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="b5f35-166">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="b5f35-166">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="b5f35-167">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="b5f35-167">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="b5f35-168">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="b5f35-168">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="b5f35-169">有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="b5f35-169">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b5f35-170">-ReadCount</span><span class="sxs-lookup"><span data-stu-id="b5f35-170">-ReadCount</span></span>

<span data-ttu-id="b5f35-171">指定每次通过管道发送的内容行数。</span><span class="sxs-lookup"><span data-stu-id="b5f35-171">Specifies how many lines of content are sent through the pipeline at a time.</span></span> <span data-ttu-id="b5f35-172">默认值为 1。</span><span class="sxs-lookup"><span data-stu-id="b5f35-172">The default value is 1.</span></span>
<span data-ttu-id="b5f35-173">值 0（零）将一次发送所有内容。</span><span class="sxs-lookup"><span data-stu-id="b5f35-173">A value of 0 (zero) sends all of the content at one time.</span></span>

<span data-ttu-id="b5f35-174">此参数不会更改显示的内容，但会影响显示内容所用的时间。</span><span class="sxs-lookup"><span data-stu-id="b5f35-174">This parameter does not change the content displayed, but it does affect the time it takes to display the content.</span></span> <span data-ttu-id="b5f35-175">随着 **ReadCount** 的值增加，返回第一行所用的时间将会增加，但该操作的总计时间将会减少。</span><span class="sxs-lookup"><span data-stu-id="b5f35-175">As the value of **ReadCount** increases, the time it takes to return the first line increases, but the total time for the operation decreases.</span></span> <span data-ttu-id="b5f35-176">这可能会在大型项目中明显不同。</span><span class="sxs-lookup"><span data-stu-id="b5f35-176">This can make a perceptible difference in large items.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b5f35-177">-TotalCount</span><span class="sxs-lookup"><span data-stu-id="b5f35-177">-TotalCount</span></span>

<span data-ttu-id="b5f35-178">从文件或其他项的开始处指定行数。</span><span class="sxs-lookup"><span data-stu-id="b5f35-178">Specifies the number of lines from the beginning of a file or other item.</span></span> <span data-ttu-id="b5f35-179">默认值为 -1（所有行）。</span><span class="sxs-lookup"><span data-stu-id="b5f35-179">The default is -1 (all lines).</span></span>

<span data-ttu-id="b5f35-180">您可以使用 **TotalCount** 参数名称或其别名 **First** 或 **Head** 。</span><span class="sxs-lookup"><span data-stu-id="b5f35-180">You can use the **TotalCount** parameter name or its aliases, **First** or **Head** .</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases: First, Head

Required: False
Position: Named
Default value: -1
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b5f35-181">-Tail</span><span class="sxs-lookup"><span data-stu-id="b5f35-181">-Tail</span></span>

<span data-ttu-id="b5f35-182">从文件或其他项的结尾处指定行数。</span><span class="sxs-lookup"><span data-stu-id="b5f35-182">Specifies the number of lines from the end of a file or other item.</span></span> <span data-ttu-id="b5f35-183">您可以使用 **Tail** 参数名或其别名 **Last** 。</span><span class="sxs-lookup"><span data-stu-id="b5f35-183">You can use the **Tail** parameter name or its alias, **Last** .</span></span> <span data-ttu-id="b5f35-184">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="b5f35-184">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: Last

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b5f35-185">-Filter</span><span class="sxs-lookup"><span data-stu-id="b5f35-185">-Filter</span></span>

<span data-ttu-id="b5f35-186">指定用于限定 **路径** 参数的筛选器。</span><span class="sxs-lookup"><span data-stu-id="b5f35-186">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="b5f35-187">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供程序是唯一一种支持使用筛选器的已安装 PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="b5f35-187">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="b5f35-188">可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **文件系统** 筛选语言的语法。</span><span class="sxs-lookup"><span data-stu-id="b5f35-188">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="b5f35-189">筛选器比其他参数更有效，因为提供程序在 cmdlet 获取对象时应用筛选器，而不是在检索对象后再对其进行筛选。</span><span class="sxs-lookup"><span data-stu-id="b5f35-189">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="b5f35-190">-Include</span><span class="sxs-lookup"><span data-stu-id="b5f35-190">-Include</span></span>

<span data-ttu-id="b5f35-191">指定此 cmdlet 将在操作中包含的一个项或多个项（作为一个字符串数组）。</span><span class="sxs-lookup"><span data-stu-id="b5f35-191">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="b5f35-192">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="b5f35-192">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="b5f35-193">请输入路径元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="b5f35-193">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="b5f35-194">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="b5f35-194">Wildcard characters are permitted.</span></span> <span data-ttu-id="b5f35-195">仅 **Include** 当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Include 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="b5f35-195">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="b5f35-196">-Exclude</span><span class="sxs-lookup"><span data-stu-id="b5f35-196">-Exclude</span></span>

<span data-ttu-id="b5f35-197">指定为字符串数组，此 cmdlet 在操作中排除的项。</span><span class="sxs-lookup"><span data-stu-id="b5f35-197">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span>
<span data-ttu-id="b5f35-198">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="b5f35-198">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="b5f35-199">请输入路径元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="b5f35-199">Enter a path element or pattern, such as `*.txt`.</span></span>
<span data-ttu-id="b5f35-200">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="b5f35-200">Wildcard characters are permitted.</span></span>

<span data-ttu-id="b5f35-201">仅 **Exclude** 当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Exclude 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="b5f35-201">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="b5f35-202">-Force</span><span class="sxs-lookup"><span data-stu-id="b5f35-202">-Force</span></span>

<span data-ttu-id="b5f35-203">**强制** 将覆盖只读属性或创建目录来完成文件路径。</span><span class="sxs-lookup"><span data-stu-id="b5f35-203">**Force** will override a read-only attribute or create directories to complete a file path.</span></span> <span data-ttu-id="b5f35-204">**Force** 参数不会尝试更改文件权限或覆盖安全限制。</span><span class="sxs-lookup"><span data-stu-id="b5f35-204">The **Force** parameter does not attempt to change file permissions or override security restrictions.</span></span>

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

### <span data-ttu-id="b5f35-205">-Credential</span><span class="sxs-lookup"><span data-stu-id="b5f35-205">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="b5f35-206">随 PowerShell 一起安装的任何提供程序都不支持此参数。</span><span class="sxs-lookup"><span data-stu-id="b5f35-206">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="b5f35-207">若要在运行此 cmdlet 时模拟其他用户或提升凭据，请使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="b5f35-207">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b5f35-208">-Delimiter</span><span class="sxs-lookup"><span data-stu-id="b5f35-208">-Delimiter</span></span>

<span data-ttu-id="b5f35-209">指定在 `Get-Content` 读取文件时将其划分为对象的分隔符。</span><span class="sxs-lookup"><span data-stu-id="b5f35-209">Specifies the delimiter that `Get-Content` uses to divide the file into objects while it reads.</span></span> <span data-ttu-id="b5f35-210">默认值为 `\n` 行尾字符。</span><span class="sxs-lookup"><span data-stu-id="b5f35-210">The default is `\n`, the end-of-line character.</span></span> <span data-ttu-id="b5f35-211">读取文本文件时， `Get-Content` 将返回 string 对象的集合，其中每个对象都以行尾字符结尾。</span><span class="sxs-lookup"><span data-stu-id="b5f35-211">When reading a text file, `Get-Content` returns a collection of string objects, each of which ends with an end-of-line character.</span></span> <span data-ttu-id="b5f35-212">当你输入文件中不存在的分隔符时，会 `Get-Content` 将整个文件作为单个 get-content 对象返回。</span><span class="sxs-lookup"><span data-stu-id="b5f35-212">When you enter a delimiter that does not exist in the file, `Get-Content` returns the entire file as a single, undelimited object.</span></span>

<span data-ttu-id="b5f35-213">您可以使用此参数将一个大文件拆分为较小的文件，方法是指定一个文件分隔符作为分隔符。</span><span class="sxs-lookup"><span data-stu-id="b5f35-213">You can use this parameter to split a large file into smaller files by specifying a file separator, as the delimiter.</span></span> <span data-ttu-id="b5f35-214">分隔符将被保留（不会被丢弃），并且成为每个文件部分中的最后一项。</span><span class="sxs-lookup"><span data-stu-id="b5f35-214">The delimiter is preserved (not discarded) and becomes the last item in each file section.</span></span>

<span data-ttu-id="b5f35-215">**分隔符** 是 **FileSystem** 提供程序添加到 cmdlet 的动态参数 `Get-Content` 。</span><span class="sxs-lookup"><span data-stu-id="b5f35-215">**Delimiter** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet.</span></span> <span data-ttu-id="b5f35-216">此参数仅在文件系统驱动器中有效。</span><span class="sxs-lookup"><span data-stu-id="b5f35-216">This parameter works only in file system drives.</span></span>

> [!NOTE]
> <span data-ttu-id="b5f35-217">目前， **分隔符** 参数的值为空字符串时，不 `Get-Content` 返回任何内容。</span><span class="sxs-lookup"><span data-stu-id="b5f35-217">Currently, when the value of the **Delimiter** parameter is an empty string, `Get-Content` does not return anything.</span></span> <span data-ttu-id="b5f35-218">这是一个已知问题。</span><span class="sxs-lookup"><span data-stu-id="b5f35-218">This is a known issue.</span></span> <span data-ttu-id="b5f35-219">强制 `Get-Content` 将整个文件作为单个 get-content 字符串返回。</span><span class="sxs-lookup"><span data-stu-id="b5f35-219">To force `Get-Content` to return the entire file as a single, undelimited string.</span></span> <span data-ttu-id="b5f35-220">输入文件中不存在的值。</span><span class="sxs-lookup"><span data-stu-id="b5f35-220">Enter a value that does not exist in the file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: End-of-line character
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5f35-221">-Wait</span><span class="sxs-lookup"><span data-stu-id="b5f35-221">-Wait</span></span>

<span data-ttu-id="b5f35-222">在输出所有现有行后，使文件保持打开状态。</span><span class="sxs-lookup"><span data-stu-id="b5f35-222">Keeps the file open after all existing lines have been output.</span></span> <span data-ttu-id="b5f35-223">等待时， `Get-Content` 每秒检查一次文件，并输出新行（如果存在）。</span><span class="sxs-lookup"><span data-stu-id="b5f35-223">While waiting, `Get-Content` checks the file once each second and outputs new lines if present.</span></span> <span data-ttu-id="b5f35-224">可以按 **CTRL + C** 中断 **等待** 。</span><span class="sxs-lookup"><span data-stu-id="b5f35-224">You can interrupt **Wait** by pressing **CTRL+C** .</span></span> <span data-ttu-id="b5f35-225">如果文件被删除，则等待也会结束，在这种情况下，会报告非终止错误。</span><span class="sxs-lookup"><span data-stu-id="b5f35-225">Waiting also ends if the file gets deleted, in which case a non-terminating error is reported.</span></span>

<span data-ttu-id="b5f35-226">**Wait** 是 FileSystem 提供程序添加到 cmdlet 的动态参数 `Get-Content` 。</span><span class="sxs-lookup"><span data-stu-id="b5f35-226">**Wait** is a dynamic parameter that the FileSystem provider adds to the `Get-Content` cmdlet.</span></span> <span data-ttu-id="b5f35-227">此参数仅在文件系统驱动器中有效。</span><span class="sxs-lookup"><span data-stu-id="b5f35-227">This parameter works only in file system drives.</span></span> <span data-ttu-id="b5f35-228">**Wait** 无法与 **Raw** 组合。</span><span class="sxs-lookup"><span data-stu-id="b5f35-228">**Wait** cannot be combined with **Raw** .</span></span>

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

### <span data-ttu-id="b5f35-229">-Raw</span><span class="sxs-lookup"><span data-stu-id="b5f35-229">-Raw</span></span>

<span data-ttu-id="b5f35-230">忽略换行字符，并返回一个字符串中文件的全部内容，并保留换行符。</span><span class="sxs-lookup"><span data-stu-id="b5f35-230">Ignores newline characters and returns the entire contents of a file in one string with the newlines preserved.</span></span> <span data-ttu-id="b5f35-231">默认情况下，文件中的换行符用作分隔符，以将输入拆分为字符串数组。</span><span class="sxs-lookup"><span data-stu-id="b5f35-231">By default, newline characters in a file are used as delimiters to separate the input into an array of strings.</span></span> <span data-ttu-id="b5f35-232">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="b5f35-232">This parameter was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="b5f35-233">**Raw** 是 **FileSystem** 提供程序添加到 cmdlet 的动态参数， `Get-Content` 此参数仅在文件系统驱动器中有效。</span><span class="sxs-lookup"><span data-stu-id="b5f35-233">**Raw** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet This parameter works only in file system drives.</span></span>

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

### <span data-ttu-id="b5f35-234">-Encoding</span><span class="sxs-lookup"><span data-stu-id="b5f35-234">-Encoding</span></span>

<span data-ttu-id="b5f35-235">指定目标文件的编码类型。</span><span class="sxs-lookup"><span data-stu-id="b5f35-235">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="b5f35-236">默认值是 `Default`。</span><span class="sxs-lookup"><span data-stu-id="b5f35-236">The default value is `Default`.</span></span>

<span data-ttu-id="b5f35-237">此参数可接受的值如下所示：</span><span class="sxs-lookup"><span data-stu-id="b5f35-237">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="b5f35-238">`Ascii` 使用 ASCII (7 位) 字符集。</span><span class="sxs-lookup"><span data-stu-id="b5f35-238">`Ascii` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="b5f35-239">`BigEndianUnicode` 使用带有大 endian 字节顺序的 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="b5f35-239">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="b5f35-240">`BigEndianUTF32` 使用带有大字节序字节顺序的 32 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="b5f35-240">`BigEndianUTF32` Uses UTF-32 with the big-endian byte order.</span></span>
- <span data-ttu-id="b5f35-241">`Byte` 将一组字符编码为一个字节序列。</span><span class="sxs-lookup"><span data-stu-id="b5f35-241">`Byte` Encodes a set of characters into a sequence of bytes.</span></span>
- <span data-ttu-id="b5f35-242">`Default` 使用与系统的活动代码页相对应的编码 (通常为 ANSI) 。</span><span class="sxs-lookup"><span data-stu-id="b5f35-242">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="b5f35-243">`Oem` 使用与系统的当前 OEM 代码页相对应的编码。</span><span class="sxs-lookup"><span data-stu-id="b5f35-243">`Oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="b5f35-244">`String` 与 `Unicode` 相同。</span><span class="sxs-lookup"><span data-stu-id="b5f35-244">`String` Same as `Unicode`.</span></span>
- <span data-ttu-id="b5f35-245">`Unicode` 使用带有小 endian 字节顺序的 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="b5f35-245">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="b5f35-246">`Unknown` 与 `Unicode` 相同。</span><span class="sxs-lookup"><span data-stu-id="b5f35-246">`Unknown` Same as `Unicode`.</span></span>
- <span data-ttu-id="b5f35-247">`UTF7` 使用 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="b5f35-247">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="b5f35-248">`UTF8` 使用 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="b5f35-248">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="b5f35-249">`UTF32` 使用带有小 endian 字节顺序的 32 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="b5f35-249">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

<span data-ttu-id="b5f35-250">Encoding 是 **FileSystem** 提供程序添加到 cmdlet 的动态参数 `Get-Content` 。</span><span class="sxs-lookup"><span data-stu-id="b5f35-250">Encoding is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet.</span></span>
<span data-ttu-id="b5f35-251">此参数仅在文件系统驱动器中有效。</span><span class="sxs-lookup"><span data-stu-id="b5f35-251">This parameter works only in file system drives.</span></span>

<span data-ttu-id="b5f35-252">从二进制文件中读取和写入二进制文件时，请使用 **Encoding** 动态参数的 **Byte** 值和 **ReadCount** 参数的值0。</span><span class="sxs-lookup"><span data-stu-id="b5f35-252">When reading from and writing to binary files, use a value of **Byte** for the **Encoding** dynamic parameter and a value of 0 for the **ReadCount** parameter.</span></span> <span data-ttu-id="b5f35-253">如果 **ReadCount** 值为0，则在单个读取操作中读取整个文件，并将其转换为单个对象 (PSObject) 。</span><span class="sxs-lookup"><span data-stu-id="b5f35-253">A **ReadCount** value of 0 reads the entire file in a single read operation and converts it into a single object (PSObject).</span></span> <span data-ttu-id="b5f35-254">默认的 **ReadCount** 值1在每个读取操作中读取一个字节，并将每个字节转换为单独的对象，这会在你使用 `Set-Content` cmdlet 将字节写入文件时导致错误。</span><span class="sxs-lookup"><span data-stu-id="b5f35-254">The default **ReadCount** value, 1, reads one byte in each read operation and converts each byte into a separate object, which causes errors when you use the `Set-Content` cmdlet to write the bytes to a file.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, Byte, Default, OEM, String, Unicode, Unknown, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5f35-255">-Stream</span><span class="sxs-lookup"><span data-stu-id="b5f35-255">-Stream</span></span>

<span data-ttu-id="b5f35-256">从文件中获取指定的备用 NTFS 文件流的内容。</span><span class="sxs-lookup"><span data-stu-id="b5f35-256">Gets the contents of the specified alternate NTFS file stream from the file.</span></span> <span data-ttu-id="b5f35-257">输入流名称。</span><span class="sxs-lookup"><span data-stu-id="b5f35-257">Enter the stream name.</span></span>
<span data-ttu-id="b5f35-258">不支持通配符。</span><span class="sxs-lookup"><span data-stu-id="b5f35-258">Wildcards are not supported.</span></span>

<span data-ttu-id="b5f35-259">**Stream** 是 **FileSystem** 提供程序添加到 cmdlet 的动态参数 `Get-Content` 。</span><span class="sxs-lookup"><span data-stu-id="b5f35-259">**Stream** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet.</span></span>
<span data-ttu-id="b5f35-260">此参数仅适用于 Windows 系统上的文件系统驱动器。</span><span class="sxs-lookup"><span data-stu-id="b5f35-260">This parameter works only in file system drives on Windows systems.</span></span> <span data-ttu-id="b5f35-261">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="b5f35-261">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="b5f35-262">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="b5f35-262">-UseTransaction</span></span>

<span data-ttu-id="b5f35-263">在活动事务中使用该命令。</span><span class="sxs-lookup"><span data-stu-id="b5f35-263">Includes the command in the active transaction.</span></span> <span data-ttu-id="b5f35-264">仅当正在执行事务时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="b5f35-264">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="b5f35-265">有关详细信息，请参阅 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)。</span><span class="sxs-lookup"><span data-stu-id="b5f35-265">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

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

### <span data-ttu-id="b5f35-266">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b5f35-266">CommonParameters</span></span>

<span data-ttu-id="b5f35-267">此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="b5f35-267">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="b5f35-268">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b5f35-268">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b5f35-269">输入</span><span class="sxs-lookup"><span data-stu-id="b5f35-269">INPUTS</span></span>

### <span data-ttu-id="b5f35-270">System.Int64、System.String[]、System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="b5f35-270">System.Int64, System.String[], System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="b5f35-271">你可以通过管道将读取计数、总计数、路径或凭据传递给 `Get-Content` 。</span><span class="sxs-lookup"><span data-stu-id="b5f35-271">You can pipe the read count, total count, paths, or credentials to `Get-Content`.</span></span>

## <span data-ttu-id="b5f35-272">输出</span><span class="sxs-lookup"><span data-stu-id="b5f35-272">OUTPUTS</span></span>

### <span data-ttu-id="b5f35-273">System.Byte、System.String</span><span class="sxs-lookup"><span data-stu-id="b5f35-273">System.Byte, System.String</span></span>

<span data-ttu-id="b5f35-274">`Get-Content` 返回字符串或字节。</span><span class="sxs-lookup"><span data-stu-id="b5f35-274">`Get-Content` returns strings or bytes.</span></span> <span data-ttu-id="b5f35-275">输出类型取决于指定为输入的内容类型。</span><span class="sxs-lookup"><span data-stu-id="b5f35-275">The output type depends upon the type of content that you specify as input.</span></span>

## <span data-ttu-id="b5f35-276">注释</span><span class="sxs-lookup"><span data-stu-id="b5f35-276">NOTES</span></span>

<span data-ttu-id="b5f35-277">`Get-Content`Cmdlet 设计用于处理由任何提供程序公开的数据。</span><span class="sxs-lookup"><span data-stu-id="b5f35-277">The `Get-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="b5f35-278">若要获取会话中的提供程序，请使用 `Get-PSProvider` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b5f35-278">To get the providers in your session, use the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="b5f35-279">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="b5f35-279">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="b5f35-280">相关链接</span><span class="sxs-lookup"><span data-stu-id="b5f35-280">RELATED LINKS</span></span>

[<span data-ttu-id="b5f35-281">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="b5f35-281">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="b5f35-282">about_Providers</span><span class="sxs-lookup"><span data-stu-id="b5f35-282">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="b5f35-283">Add-Content</span><span class="sxs-lookup"><span data-stu-id="b5f35-283">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="b5f35-284">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="b5f35-284">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="b5f35-285">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="b5f35-285">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="b5f35-286">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="b5f35-286">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="b5f35-287">Set-Content</span><span class="sxs-lookup"><span data-stu-id="b5f35-287">Set-Content</span></span>](Set-Content.md)
