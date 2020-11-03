---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-hex?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Hex
ms.openlocfilehash: 587f063c425ceb7561bdd2f9f696c8b3d638a835
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "93199348"
---
# <span data-ttu-id="13ac4-103">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="13ac4-103">Format-Hex</span></span>

## <span data-ttu-id="13ac4-104">摘要</span><span class="sxs-lookup"><span data-stu-id="13ac4-104">SYNOPSIS</span></span>

<span data-ttu-id="13ac4-105">将文件或其他输入显示为十六进制。</span><span class="sxs-lookup"><span data-stu-id="13ac4-105">Displays a file or other input as hexadecimal.</span></span>

## <span data-ttu-id="13ac4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="13ac4-106">SYNTAX</span></span>

### <span data-ttu-id="13ac4-107">`Path`</span><span class="sxs-lookup"><span data-stu-id="13ac4-107">Path</span></span>

```
Format-Hex [-Path] <String[]> [-Count <Int64>] [-Offset <Int64>] [<CommonParameters>]
```

### <span data-ttu-id="13ac4-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="13ac4-108">LiteralPath</span></span>

```
Format-Hex -LiteralPath <String[]> [-Count <Int64>] [-Offset <Int64>] [<CommonParameters>]
```

### <span data-ttu-id="13ac4-109">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="13ac4-109">ByInputObject</span></span>

```
Format-Hex -InputObject <PSObject> [-Encoding <Encoding>] [-Count <Int64>] [-Offset <Int64>] [-Raw]
 [<CommonParameters>]
```

## <span data-ttu-id="13ac4-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="13ac4-110">DESCRIPTION</span></span>

<span data-ttu-id="13ac4-111">`Format-Hex`Cmdlet 将文件或其他输入显示为十六进制值。</span><span class="sxs-lookup"><span data-stu-id="13ac4-111">The `Format-Hex` cmdlet displays a file or other input as hexadecimal values.</span></span> <span data-ttu-id="13ac4-112">若要确定输出中的字符的偏移量，请将行最左侧的数字与该字符所在列顶部的数字相加。</span><span class="sxs-lookup"><span data-stu-id="13ac4-112">To determine the offset of a character from the output, add the number at the leftmost of the row to the number at the top of the column for that character.</span></span>

<span data-ttu-id="13ac4-113">此 `Format-Hex` cmdlet 可帮助你确定损坏文件的文件类型或可能不具有文件扩展名的文件。</span><span class="sxs-lookup"><span data-stu-id="13ac4-113">The `Format-Hex` cmdlet can help you determine the file type of a corrupted file or a file that might not have a filename extension.</span></span> <span data-ttu-id="13ac4-114">您可以运行此 cmdlet，然后读取十六进制输出以获取文件信息。</span><span class="sxs-lookup"><span data-stu-id="13ac4-114">You can run this cmdlet, and then read the hexadecimal output to get file information.</span></span>

<span data-ttu-id="13ac4-115">`Format-Hex`对文件使用时，该 cmdlet 将忽略换行符，并将保留了换行符的文件中的全部内容返回。</span><span class="sxs-lookup"><span data-stu-id="13ac4-115">When using `Format-Hex` on a file, the cmdlet ignores newline characters and returns the entire contents of a file in one string with the newline characters preserved.</span></span>

## <span data-ttu-id="13ac4-116">示例</span><span class="sxs-lookup"><span data-stu-id="13ac4-116">EXAMPLES</span></span>

### <span data-ttu-id="13ac4-117">示例 1：获取字符串的十六进制表示形式</span><span class="sxs-lookup"><span data-stu-id="13ac4-117">Example 1: Get the hexadecimal representation of a string</span></span>

<span data-ttu-id="13ac4-118">此命令返回字符串的十六进制值。</span><span class="sxs-lookup"><span data-stu-id="13ac4-118">This command returns the hexadecimal values of a string.</span></span>

```powershell
'Hello World' | Format-Hex
```

```Output
   Label: String (System.String) <2944BEC3>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 48 65 6C 6C 6F 20 57 6F 72 6C 64                Hello World
```

<span data-ttu-id="13ac4-119">字符串 **Hello World** 会沿管道向下发送到 `Format-Hex` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="13ac4-119">The string **Hello World** is sent down the pipeline to the `Format-Hex` cmdlet.</span></span> <span data-ttu-id="13ac4-120">的十六进制输出 `Format-Hex` 显示字符串中每个字符的值。</span><span class="sxs-lookup"><span data-stu-id="13ac4-120">The hexadecimal output from `Format-Hex` shows the values of each character in the string.</span></span>

### <span data-ttu-id="13ac4-121">示例2：从十六进制输出中查找文件类型</span><span class="sxs-lookup"><span data-stu-id="13ac4-121">Example 2: Find a file type from hexadecimal output</span></span>

<span data-ttu-id="13ac4-122">此示例使用十六进制输出来确定文件类型。</span><span class="sxs-lookup"><span data-stu-id="13ac4-122">This example uses the hexadecimal output to determine the file type.</span></span> <span data-ttu-id="13ac4-123">Cmdlet 显示文件的完整路径和十六进制值。</span><span class="sxs-lookup"><span data-stu-id="13ac4-123">The cmdlet displays the file's full path and the hexadecimal values.</span></span>

<span data-ttu-id="13ac4-124">若要测试以下命令，请在本地计算机上创建现有 PDF 文件的副本，并将复制的文件重命名为 `File.t7f` 。</span><span class="sxs-lookup"><span data-stu-id="13ac4-124">To test the following command, make a copy of an existing PDF file on your local computer and rename the copied file to `File.t7f`.</span></span>

```powershell
Format-Hex -Path .\File.t7f -Count 48
```

```Output
   Label: C:\Test\File.t7f

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 25 50 44 46 2D 31 2E 35 0D 0A 25 B5 B5 B5 B5 0D %PDF-1.5..%????.
0000000000000010 0A 31 20 30 20 6F 62 6A 0D 0A 3C 3C 2F 54 79 70 .1 0 obj..<</Typ
0000000000000020 65 2F 43 61 74 61 6C 6F 67 2F 50 61 67 65 73 20 e/Catalog/Pages
```

<span data-ttu-id="13ac4-125">`Format-Hex`Cmdlet 使用 **Path** 参数来指定当前目录中的文件名 `File.t7f` 。</span><span class="sxs-lookup"><span data-stu-id="13ac4-125">The `Format-Hex` cmdlet uses the **Path** parameter to specify a filename in the current directory, `File.t7f`.</span></span> <span data-ttu-id="13ac4-126">文件扩展名 `.t7f` 不常见，但十六进制输出 `%PDF` 显示它是 PDF 文件。</span><span class="sxs-lookup"><span data-stu-id="13ac4-126">The file extension `.t7f` is uncommon, but the hexadecimal output `%PDF` shows that it is a PDF file.</span></span> <span data-ttu-id="13ac4-127">在此示例中， **Count** 参数用于将输出限制为文件的前48字节。</span><span class="sxs-lookup"><span data-stu-id="13ac4-127">In this example, the **Count** parameter is used to limit the output to the first 48 bytes of the file.</span></span>

### <span data-ttu-id="13ac4-128">示例3：设置不同数据类型的数组格式</span><span class="sxs-lookup"><span data-stu-id="13ac4-128">Example 3: Format an array of different data types</span></span>

<span data-ttu-id="13ac4-129">此示例使用不同数据类型的数组，以突出显示如何 `Format-Hex` 在管道中处理它们。</span><span class="sxs-lookup"><span data-stu-id="13ac4-129">This example uses an array of different data types to highlight how `Format-Hex` handles them in the Pipeline.</span></span>

<span data-ttu-id="13ac4-130">它将通过管道和单独处理每个对象。</span><span class="sxs-lookup"><span data-stu-id="13ac4-130">It will pass each object through the Pipeline and process individually.</span></span> <span data-ttu-id="13ac4-131">但是，如果它是数值数据，并且相邻对象也是数值数据，则会将其组合成单个输出块。</span><span class="sxs-lookup"><span data-stu-id="13ac4-131">However, if it's numeric data, and the adjacent object is also numeric, it will group them into a single output block.</span></span>

```powershell
'Hello world!', 1, 1138, 'foo', 'bar', 0xdeadbeef, 1gb, 0b1101011100 , $true, $false | Format-Hex
```

```Output
   Label: String (System.String) <24F1F0A3>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 48 65 6C 6C 6F 20 77 6F 72 6C 64 21             Hello world!

   Label: Int32 (System.Int32) <2EB933C5>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 01 00 00 00 72 04 00 00                         �   r�

   Label: String (System.String) <4078B66C>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 66 6F 6F                                        foo

   Label: String (System.String) <51E4A317>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 62 61 72                                        bar

   Label: Int32 (System.Int32) <5ADF167B>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 EF BE AD DE 00 00 00 40 5C 03 00 00             ï¾-Þ   @\�

   Label: Boolean (System.Boolean) <7D8C4C1D>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 01 00 00 00 00 00 00 00                         �
```

## <span data-ttu-id="13ac4-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="13ac4-132">PARAMETERS</span></span>

### <span data-ttu-id="13ac4-133">-Encoding</span><span class="sxs-lookup"><span data-stu-id="13ac4-133">-Encoding</span></span>

<span data-ttu-id="13ac4-134">指定输入字符串的编码。</span><span class="sxs-lookup"><span data-stu-id="13ac4-134">Specifies the encoding of the input strings.</span></span> <span data-ttu-id="13ac4-135">这仅适用于 `[string]` 输入。</span><span class="sxs-lookup"><span data-stu-id="13ac4-135">This only applies to `[string]` input.</span></span> <span data-ttu-id="13ac4-136">参数对数值类型不起作用。</span><span class="sxs-lookup"><span data-stu-id="13ac4-136">The parameter has no effect on numeric types.</span></span> <span data-ttu-id="13ac4-137">输出值始终为 `utf8NoBOM` 。</span><span class="sxs-lookup"><span data-stu-id="13ac4-137">The output value is always `utf8NoBOM`.</span></span>

<span data-ttu-id="13ac4-138">此参数可接受的值如下所示：</span><span class="sxs-lookup"><span data-stu-id="13ac4-138">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="13ac4-139">`ascii`：使用 ASCII (7 位) 字符集的编码。</span><span class="sxs-lookup"><span data-stu-id="13ac4-139">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="13ac4-140">`bigendianunicode`：使用大字节序字节顺序对 UTF-16 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="13ac4-140">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="13ac4-141">`bigendianutf32`：使用大字节序字节顺序编码为32格式。</span><span class="sxs-lookup"><span data-stu-id="13ac4-141">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="13ac4-142">`oem`：使用 MS-DOS 和控制台程序的默认编码。</span><span class="sxs-lookup"><span data-stu-id="13ac4-142">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="13ac4-143">`unicode`：使用小 endian 字节顺序对 UTF-16 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="13ac4-143">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="13ac4-144">`utf7`：以 UTF-7 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="13ac4-144">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="13ac4-145">`utf8`：以 UTF-8 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="13ac4-145">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="13ac4-146">`utf8BOM`：以 UTF-8 格式编码 (BOM) </span><span class="sxs-lookup"><span data-stu-id="13ac4-146">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="13ac4-147">`utf8NoBOM`：以 UTF-8 格式编码，而不包含字节顺序标记 (BOM) </span><span class="sxs-lookup"><span data-stu-id="13ac4-147">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="13ac4-148">`utf32`：以32格式编码。</span><span class="sxs-lookup"><span data-stu-id="13ac4-148">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="13ac4-149">从 PowerShell 6.2 开始， **Encoding** 参数还允许已注册代码页的数字 id (如 `-Encoding 1251` (如) 所注册代码页的) 或字符串名称 `-Encoding "windows-1251"` 。</span><span class="sxs-lookup"><span data-stu-id="13ac4-149">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="13ac4-150">有关详细信息，请参阅 .NET 文档中的[编码。](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)</span><span class="sxs-lookup"><span data-stu-id="13ac4-150">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="13ac4-151">不建议使用 **utf-7** \*。</span><span class="sxs-lookup"><span data-stu-id="13ac4-151">**UTF-7** \* is no longer recommended to use.</span></span> <span data-ttu-id="13ac4-152">在 PowerShell 7.1 中，如果 `utf7` 为 **编码** 参数指定，则会写入警告。</span><span class="sxs-lookup"><span data-stu-id="13ac4-152">In PowerShell 7.1, a warning is written if you specify `utf7` for the **Encoding** parameter.</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: ByInputObject
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13ac4-153">-InputObject</span><span class="sxs-lookup"><span data-stu-id="13ac4-153">-InputObject</span></span>

<span data-ttu-id="13ac4-154">用于管道输入。</span><span class="sxs-lookup"><span data-stu-id="13ac4-154">Used for pipeline input.</span></span> <span data-ttu-id="13ac4-155">管道输入仅支持特定于管道的标量类型和 `[system.io.fileinfo]` 实例 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="13ac4-155">Pipeline input supports only certain scalar types and `[system.io.fileinfo]` instances for piping from `Get-ChildItem`.</span></span>

<span data-ttu-id="13ac4-156">支持的标量类型为：</span><span class="sxs-lookup"><span data-stu-id="13ac4-156">The supported scalar types are:</span></span>

- <span data-ttu-id="13ac4-157">`[string]`, `[char]`</span><span class="sxs-lookup"><span data-stu-id="13ac4-157">`[string]`, `[char]`</span></span>
- <span data-ttu-id="13ac4-158">`[byte]`, `[sbyte]`</span><span class="sxs-lookup"><span data-stu-id="13ac4-158">`[byte]`, `[sbyte]`</span></span>
- <span data-ttu-id="13ac4-159">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span><span class="sxs-lookup"><span data-stu-id="13ac4-159">`[int16]`, `[uint16]`, `[short]`, `[ushort]`</span></span>
- <span data-ttu-id="13ac4-160">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span><span class="sxs-lookup"><span data-stu-id="13ac4-160">`[int]`, `[uint]`, `[int32]`, `[uint32]`,</span></span>
- <span data-ttu-id="13ac4-161">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="13ac4-161">`[long]`, `[ulong]`, `[int64]`, `[uint64]`</span></span>
- <span data-ttu-id="13ac4-162">`[single]`, `[float]`, `[double]`</span><span class="sxs-lookup"><span data-stu-id="13ac4-162">`[single]`, `[float]`, `[double]`</span></span>
- `[boolean]`

<span data-ttu-id="13ac4-163">在 PowerShell 6.2 之前， `Format-Hex` 将通过将所有 like 对象组合在一起来处理多个输入类型的管道输入。</span><span class="sxs-lookup"><span data-stu-id="13ac4-163">Prior to PowerShell 6.2, `Format-Hex` would handle a Pipeline input with multiple input types by grouping all like objects together.</span></span> <span data-ttu-id="13ac4-164">现在，它在通过管道传递时处理每个单独的对象，并且不会将对象组合在一起，除非对象是相邻的。</span><span class="sxs-lookup"><span data-stu-id="13ac4-164">Now, it handles each individual object as it passes through the Pipeline and won't group objects together unless like objects are adjacent.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="13ac4-165">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="13ac4-165">-LiteralPath</span></span>

<span data-ttu-id="13ac4-166">指定文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="13ac4-166">Specifies the complete path to a file.</span></span> <span data-ttu-id="13ac4-167">**LiteralPath** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="13ac4-167">The value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="13ac4-168">此参数不接受通配符。</span><span class="sxs-lookup"><span data-stu-id="13ac4-168">This parameter does not accept wildcard characters.</span></span> <span data-ttu-id="13ac4-169">若要指定文件的多个路径，请使用逗号分隔这些路径。</span><span class="sxs-lookup"><span data-stu-id="13ac4-169">To specify multiple paths to files, separate the paths with a comma.</span></span> <span data-ttu-id="13ac4-170">如果 **LiteralPath** 参数包含转义符，请将路径用单引号引起来。</span><span class="sxs-lookup"><span data-stu-id="13ac4-170">If the **LiteralPath** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="13ac4-171">PowerShell 不会将单个带引号的字符串中的任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="13ac4-171">PowerShell does not interpret any characters in a single quoted string as escape sequences.</span></span> <span data-ttu-id="13ac4-172">有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="13ac4-172">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13ac4-173">-Path</span><span class="sxs-lookup"><span data-stu-id="13ac4-173">-Path</span></span>

<span data-ttu-id="13ac4-174">指定文件的路径。</span><span class="sxs-lookup"><span data-stu-id="13ac4-174">Specifies the path to files.</span></span> <span data-ttu-id="13ac4-175">使用点)  (`.` 指定当前位置。</span><span class="sxs-lookup"><span data-stu-id="13ac4-175">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="13ac4-176">通配符 (`*`) 是可接受的，并且可用于指定位置中的所有项。</span><span class="sxs-lookup"><span data-stu-id="13ac4-176">The wildcard character (`*`) is accepted and can be used to specify all the items in a location.</span></span> <span data-ttu-id="13ac4-177">如果 **path** 参数包含转义符，请将路径用单引号引起来。</span><span class="sxs-lookup"><span data-stu-id="13ac4-177">If the **Path** parameter includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="13ac4-178">若要指定文件的多个路径，请使用逗号分隔这些路径。</span><span class="sxs-lookup"><span data-stu-id="13ac4-178">To specify multiple paths to files, separate the paths with a comma.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="13ac4-179">-Raw</span><span class="sxs-lookup"><span data-stu-id="13ac4-179">-Raw</span></span>

<span data-ttu-id="13ac4-180">此参数不再执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="13ac4-180">This parameter no longer does anything.</span></span> <span data-ttu-id="13ac4-181">它保留用于脚本兼容性。</span><span class="sxs-lookup"><span data-stu-id="13ac4-181">It is retained for script compatibility.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13ac4-182">-Offset</span><span class="sxs-lookup"><span data-stu-id="13ac4-182">-Offset</span></span>

<span data-ttu-id="13ac4-183">这表示要从十六进制输出中跳过的字节数。</span><span class="sxs-lookup"><span data-stu-id="13ac4-183">This represents the number of bytes to skip from being part of the hex output.</span></span>

<span data-ttu-id="13ac4-184">此参数是在 PowerShell 6.2 中引入的。</span><span class="sxs-lookup"><span data-stu-id="13ac4-184">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13ac4-185">-Count</span><span class="sxs-lookup"><span data-stu-id="13ac4-185">-Count</span></span>

<span data-ttu-id="13ac4-186">这表示要包含在十六进制输出中的字节数。</span><span class="sxs-lookup"><span data-stu-id="13ac4-186">This represents the number of bytes to include in the hex output.</span></span>

<span data-ttu-id="13ac4-187">此参数是在 PowerShell 6.2 中引入的。</span><span class="sxs-lookup"><span data-stu-id="13ac4-187">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Int64.MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13ac4-188">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="13ac4-188">CommonParameters</span></span>

<span data-ttu-id="13ac4-189">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="13ac4-189">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="13ac4-190">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="13ac4-190">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="13ac4-191">输入</span><span class="sxs-lookup"><span data-stu-id="13ac4-191">INPUTS</span></span>

### <span data-ttu-id="13ac4-192">System.String</span><span class="sxs-lookup"><span data-stu-id="13ac4-192">System.String</span></span>

<span data-ttu-id="13ac4-193">可以通过管道将字符串传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="13ac4-193">You can pipe a string to this cmdlet.</span></span>

## <span data-ttu-id="13ac4-194">输出</span><span class="sxs-lookup"><span data-stu-id="13ac4-194">OUTPUTS</span></span>

### <span data-ttu-id="13ac4-195">Microsoft.PowerShell.Commands.ByteCollection</span><span class="sxs-lookup"><span data-stu-id="13ac4-195">Microsoft.PowerShell.Commands.ByteCollection</span></span>

<span data-ttu-id="13ac4-196">此 cmdlet 返回 **ByteCollection** 。</span><span class="sxs-lookup"><span data-stu-id="13ac4-196">This cmdlet returns a **ByteCollection** .</span></span> <span data-ttu-id="13ac4-197">此对象表示字节的集合。</span><span class="sxs-lookup"><span data-stu-id="13ac4-197">This object represents a collection of bytes.</span></span> <span data-ttu-id="13ac4-198">它包含一些方法，这些方法可将字节的集合转换为格式类似于返回的每个输出行的字符串 `Format-Hex` 。</span><span class="sxs-lookup"><span data-stu-id="13ac4-198">It includes methods that convert the collection of bytes to a string formatted like each line of output returned by `Format-Hex`.</span></span> <span data-ttu-id="13ac4-199">输出还规定处理的字节类型。</span><span class="sxs-lookup"><span data-stu-id="13ac4-199">The output also states they type of bytes being processed.</span></span> <span data-ttu-id="13ac4-200">如果指定 **Path** 或 **LiteralPath** 参数，则对象将包含包含每个字节的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="13ac4-200">If you specify the **Path** or **LiteralPath** parameter, the object contains the path of the file that contains each byte.</span></span> <span data-ttu-id="13ac4-201">如果传递字符串、布尔值、整数等，则会相应地对其进行标记。</span><span class="sxs-lookup"><span data-stu-id="13ac4-201">If you pass a string, boolean, integer, etc, it will be labeled appropriately.</span></span>

## <span data-ttu-id="13ac4-202">注释</span><span class="sxs-lookup"><span data-stu-id="13ac4-202">NOTES</span></span>

<span data-ttu-id="13ac4-203">输出的最右侧列尝试将字节呈现为 ASCII 字符：</span><span class="sxs-lookup"><span data-stu-id="13ac4-203">The right-most column of output tries to render the bytes as ASCII characters:</span></span>

<span data-ttu-id="13ac4-204">通常，每个字节都被解释为 Unicode 码位，这意味着：</span><span class="sxs-lookup"><span data-stu-id="13ac4-204">Generally, each byte is interpreted as a Unicode code point, which means that:</span></span>

- <span data-ttu-id="13ac4-205">可打印的 ASCII 字符始终正确呈现</span><span class="sxs-lookup"><span data-stu-id="13ac4-205">Printable ASCII characters are always rendered correctly</span></span>
- <span data-ttu-id="13ac4-206">多字节 UTF-8 字符永远无法正确呈现</span><span class="sxs-lookup"><span data-stu-id="13ac4-206">Multi-byte UTF-8 characters never render correctly</span></span>
- <span data-ttu-id="13ac4-207">只有在高序位字节发生的情况下，UTF-16 字符才会正确呈现 `NUL` 。</span><span class="sxs-lookup"><span data-stu-id="13ac4-207">UTF-16 characters render correctly only if their high-order byte happens be `NUL`.</span></span>

## <span data-ttu-id="13ac4-208">相关链接</span><span class="sxs-lookup"><span data-stu-id="13ac4-208">RELATED LINKS</span></span>

[<span data-ttu-id="13ac4-209">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="13ac4-209">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="13ac4-210">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="13ac4-210">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="13ac4-211">Format-List</span><span class="sxs-lookup"><span data-stu-id="13ac4-211">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="13ac4-212">Format-Table</span><span class="sxs-lookup"><span data-stu-id="13ac4-212">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="13ac4-213">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="13ac4-213">Format-Wide</span></span>](Format-Wide.md)

