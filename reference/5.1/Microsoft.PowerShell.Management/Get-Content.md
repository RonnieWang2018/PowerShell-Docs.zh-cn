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
# Get-Content

## 摘要
获取位于指定位置的项的内容。

## SYNTAX

### Path（默认值）

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] [-Path] <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-UseTransaction] [-Delimiter <String>] [-Wait] [-Raw]
 [-Encoding <FileSystemCmdletProviderEncoding>] [-Stream <String>] [<CommonParameters>]
```

### LiteralPath

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] -LiteralPath <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-UseTransaction] [-Delimiter <String>] [-Wait] [-Raw]
 [-Encoding <FileSystemCmdletProviderEncoding>] [-Stream <String>] [<CommonParameters>]
```

## DESCRIPTION

该 `Get-Content` cmdlet 将获取由路径指定的位置处的项的内容，例如，文件中的文本或函数的内容。 对于文件，内容每次读取一行，并返回对象的集合，其中每个对象表示一行内容。

从 PowerShell 3.0 开始， `Get-Content` 还可以从项的开头或结尾获取指定数目的行。

## 示例

### 示例 1：获取文本文件的内容

此示例获取当前目录中的文件的内容。 `LineNumbers.txt`文件包含100行，格式 **为第 X 行** ，在几个示例中使用。

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

数组值1-100 将由管道发送到 `ForEach-Object` cmdlet。 `ForEach-Object` 使用带有 cmdlet 的脚本块 `Add-Content` 来创建 `LineNumbers.txt` 文件。 变量 `$_` 表示数组值，因为每个对象都沿管道向下发送。 `Get-Content`Cmdlet 使用 **Path** 参数指定 `LineNumbers.txt` 文件，并在 PowerShell 控制台中显示内容。

### 示例2：限制 Get-Content 返回的行数

此命令获取文件的前五行。 **TotalCount** 参数用于获取前五行内容。 此示例使用 `LineNumbers.txt` 在示例1中创建的文件。

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

### 示例3：从文本文件获取特定内容行

此命令从文件中获取特定数量的行，然后仅显示该内容的最后一行。 **TotalCount** 参数获取前25行内容。 此示例使用 `LineNumbers.txt` 在示例1中创建的文件。

```powershell
(Get-Content -Path .\LineNumbers.txt -TotalCount 25)[-1]
```

```Output
This is Line 25
```

`Get-Content`命令括在括号中，以便在执行下一步之前命令完成。 `Get-Content`返回行的数组，这允许您在括号后添加索引表示法来检索特定行号。 在这种情况下， `[-1]` 索引将指定返回的25个行的返回数组中的最后一个索引。

### 示例4：获取文本文件的最后一行

此命令从文件中获取第一行和最后一行内容。 此示例使用 `LineNumbers.txt` 在示例1中创建的文件。

```powershell
Get-Item -Path .\LineNumbers.txt | Get-Content -Tail 1
```

```Output
This is Line 100
```

此示例使用 `Get-Item` cmdlet 演示可以通过管道将文件传输到参数中 `Get-Content` 。 **Tail** 参数获取文件的最后一行。 此方法比检索所有行和使用 `[-1]` 索引表示法更快。

### 示例5：获取备用数据流的内容

此示例介绍如何使用 **Stream** 参数获取 Windows NTFS 卷上存储的文件的备用数据流的内容。 在此示例中， `Set-Content` cmdlet 用于在名为的文件中创建示例内容 `Stream.txt` 。

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

**Stream** 参数是 [FileSystem 提供程序](../microsoft.powershell.core/about/about_filesystem_provider.md#stream-systemstring)的动态参数。
默认情况下 `Get-Content` ，仅从主副本或流检索数据 `$DATA` 。 **流** 可用于存储隐藏数据，如属性、安全设置或其他数据。

### 示例6：获取原始内容

此示例中的命令以一个字符串而不是字符串数组的形式获取文件内容。 默认情况下，如果没有 **原始** 动态参数，则内容将以换行符分隔的字符串数组的形式返回。 此示例使用 `LineNumbers.txt` 在示例中创建的文件
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

### 示例7：使用筛选器与 Get-Content

可以为 cmdlet 指定筛选器 `Get-Content` 。 使用筛选器限定 **路径** 参数时，需要包含一个尾随星号 (`*`) ，以指示路径的内容。

以下命令将获取 `*.log` 目录中所有文件的内容 `C:\Temp` 。

```powershell
Get-Content -Path C:\Temp\* -Filter *.log
```

### 示例8：将文件内容作为字节数组获取

此示例演示如何将文件的内容作为 `[byte[]]` 单个对象获取。

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

第一个命令使用 **Encoding** 参数从文件中获取字节流。
**Raw** 参数可确保以形式返回字节 `[System.Byte[]]` 。 如果缺少 **原始** 参数，则返回值为字节流，由 PowerShell 解释为 `[System.Object[]]` 。

## PARAMETERS

### -Path

指定获取内容的项的路径 `Get-Content` 。 允许使用通配符。 此路径必须是指向该项的路径，而不是容器的路径。 例如，必须指定一个或多个文件的路径，而不是目录的路径。

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

### -LiteralPath

指定一个或多个位置的路径。 **LiteralPath** 的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。

有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。

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

### -ReadCount

指定每次通过管道发送的内容行数。 默认值为 1。
值 0（零）将一次发送所有内容。

此参数不会更改显示的内容，但会影响显示内容所用的时间。 随着 **ReadCount** 的值增加，返回第一行所用的时间将会增加，但该操作的总计时间将会减少。 这可能会在大型项目中明显不同。

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

### -TotalCount

从文件或其他项的开始处指定行数。 默认值为 -1（所有行）。

您可以使用 **TotalCount** 参数名称或其别名 **First** 或 **Head** 。

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

### -Tail

从文件或其他项的结尾处指定行数。 您可以使用 **Tail** 参数名或其别名 **Last** 。 此参数是在 PowerShell 3.0 中引入的。

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

### -Filter

指定用于限定 **路径** 参数的筛选器。 [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供程序是唯一一种支持使用筛选器的已安装 PowerShell 提供程序。 可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **文件系统** 筛选语言的语法。
筛选器比其他参数更有效，因为提供程序在 cmdlet 获取对象时应用筛选器，而不是在检索对象后再对其进行筛选。

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

### -Include

指定此 cmdlet 将在操作中包含的一个项或多个项（作为一个字符串数组）。 此参数值使 **Path** 参数有效。 请输入路径元素或模式，例如 `"*.txt"`。 允许使用通配符。 仅 **Include** 当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Include 参数才有效 `C:\Windows` 。

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

### -Exclude

指定为字符串数组，此 cmdlet 在操作中排除的项。
此参数值使 **Path** 参数有效。

请输入路径元素或模式，例如 `*.txt`。
允许使用通配符。

仅 **Exclude** 当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Exclude 参数才有效 `C:\Windows` 。

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

### -Force

**强制** 将覆盖只读属性或创建目录来完成文件路径。 **Force** 参数不会尝试更改文件权限或覆盖安全限制。

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

### -Credential

> [!NOTE]
> 随 PowerShell 一起安装的任何提供程序都不支持此参数。
> 若要在运行此 cmdlet 时模拟其他用户或提升凭据，请使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。

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

### -Delimiter

指定在 `Get-Content` 读取文件时将其划分为对象的分隔符。 默认值为 `\n` 行尾字符。 读取文本文件时， `Get-Content` 将返回 string 对象的集合，其中每个对象都以行尾字符结尾。 当你输入文件中不存在的分隔符时，会 `Get-Content` 将整个文件作为单个 get-content 对象返回。

您可以使用此参数将一个大文件拆分为较小的文件，方法是指定一个文件分隔符作为分隔符。 分隔符将被保留（不会被丢弃），并且成为每个文件部分中的最后一项。

**分隔符** 是 **FileSystem** 提供程序添加到 cmdlet 的动态参数 `Get-Content` 。 此参数仅在文件系统驱动器中有效。

> [!NOTE]
> 目前， **分隔符** 参数的值为空字符串时，不 `Get-Content` 返回任何内容。 这是一个已知问题。 强制 `Get-Content` 将整个文件作为单个 get-content 字符串返回。 输入文件中不存在的值。

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

### -Wait

在输出所有现有行后，使文件保持打开状态。 等待时， `Get-Content` 每秒检查一次文件，并输出新行（如果存在）。 可以按 **CTRL + C** 中断 **等待** 。 如果文件被删除，则等待也会结束，在这种情况下，会报告非终止错误。

**Wait** 是 FileSystem 提供程序添加到 cmdlet 的动态参数 `Get-Content` 。 此参数仅在文件系统驱动器中有效。 **Wait** 无法与 **Raw** 组合。

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

### -Raw

忽略换行字符，并返回一个字符串中文件的全部内容，并保留换行符。 默认情况下，文件中的换行符用作分隔符，以将输入拆分为字符串数组。 此参数是在 PowerShell 3.0 中引入的。

**Raw** 是 **FileSystem** 提供程序添加到 cmdlet 的动态参数， `Get-Content` 此参数仅在文件系统驱动器中有效。

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

### -Encoding

指定目标文件的编码类型。 默认值是 `Default`。

此参数可接受的值如下所示：

- `Ascii` 使用 ASCII (7 位) 字符集。
- `BigEndianUnicode` 使用带有大 endian 字节顺序的 UTF-16。
- `BigEndianUTF32` 使用带有大字节序字节顺序的 32 UTF-8。
- `Byte` 将一组字符编码为一个字节序列。
- `Default` 使用与系统的活动代码页相对应的编码 (通常为 ANSI) 。
- `Oem` 使用与系统的当前 OEM 代码页相对应的编码。
- `String` 与 `Unicode` 相同。
- `Unicode` 使用带有小 endian 字节顺序的 UTF-16。
- `Unknown` 与 `Unicode` 相同。
- `UTF7` 使用 UTF-8。
- `UTF8` 使用 UTF-8。
- `UTF32` 使用带有小 endian 字节顺序的 32 UTF-8。

Encoding 是 **FileSystem** 提供程序添加到 cmdlet 的动态参数 `Get-Content` 。
此参数仅在文件系统驱动器中有效。

从二进制文件中读取和写入二进制文件时，请使用 **Encoding** 动态参数的 **Byte** 值和 **ReadCount** 参数的值0。 如果 **ReadCount** 值为0，则在单个读取操作中读取整个文件，并将其转换为单个对象 (PSObject) 。 默认的 **ReadCount** 值1在每个读取操作中读取一个字节，并将每个字节转换为单独的对象，这会在你使用 `Set-Content` cmdlet 将字节写入文件时导致错误。

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

### -Stream

从文件中获取指定的备用 NTFS 文件流的内容。 输入流名称。
不支持通配符。

**Stream** 是 **FileSystem** 提供程序添加到 cmdlet 的动态参数 `Get-Content` 。
此参数仅适用于 Windows 系统上的文件系统驱动器。 已在 Windows PowerShell 3.0 中引入了此参数。

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

### -UseTransaction

在活动事务中使用该命令。 仅当正在执行事务时，此参数才有效。 有关详细信息，请参阅 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)。

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

### CommonParameters

此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Int64、System.String[]、System.Management.Automation.PSCredential

你可以通过管道将读取计数、总计数、路径或凭据传递给 `Get-Content` 。

## 输出

### System.Byte、System.String

`Get-Content` 返回字符串或字节。 输出类型取决于指定为输入的内容类型。

## 注释

`Get-Content`Cmdlet 设计用于处理由任何提供程序公开的数据。 若要获取会话中的提供程序，请使用 `Get-PSProvider` cmdlet。 有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相关链接

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Add-Content](Add-Content.md)

[Clear-Content](Clear-Content.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Get-PSProvider](Get-PSProvider.md)

[Set-Content](Set-Content.md)
