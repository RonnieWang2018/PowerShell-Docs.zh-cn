---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-random?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Random
ms.openlocfilehash: 3c1f8d136cf98a703a1eb31d73e226df5d8ef56b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93198592"
---
# Get-Random

## 摘要
获取一个随机数，或从集合中随机选择对象。

## SYNTAX

### RandomNumberParameterSet（默认值）

```
Get-Random [-SetSeed <Int32>] [[-Maximum] <Object>] [-Minimum <Object>] [<CommonParameters>]
```

### RandomListItemParameterSet

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Count <Int32>] [<CommonParameters>]
```

## DESCRIPTION

`Get-Random`Cmdlet 将获取随机选择的数字。 如果将对象的集合提交到 `Get-Random` ，则它将从集合中获取一个或多个随机选择的对象。

如果不使用参数或输入，则 `Get-Random` 命令将返回 0 (零) 和 () 之间随机选择的 **Int32.MaxValue** 32 位无符号 `0x7FFFFFFF` 整数 `2,147,483,647` 。

您可以使用的参数 `Get-Random` 指定种子数、最小值和最大值，以及从已提交的集合中返回的对象数。

## 示例

### 示例1：获取随机整数

此命令将获取一个介于 0 (零) 之间的随机 **整数。**

```powershell
Get-Random
```

```Output
3951433
```

### 示例2：获取0到99之间的随机整数

```powershell
Get-Random -Maximum 100
```

```Output
47
```

### 示例3：获取-100 和99之间的随机整数

```powershell
Get-Random -Minimum -100 -Maximum 100
```

```Output
56
```

### 示例4：获取随机浮点数

此命令将获取一个大于或等于 10.7 且小于 20.92 的随机浮点数。

```powershell
Get-Random -Minimum 10.7 -Maximum 20.93
```

```Output
18.08467273887
```

### 示例5：从数组获取随机整数

此命令将从指定的数组中获取一个随机选择的数字。

```powershell
1, 2, 3, 5, 8, 13 | Get-Random
```

```Output
8
```

### 示例6：从数组获取几个随机整数

此命令以随机顺序从数组中获取三个随机选择的数字。

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count 3
```

```Output
3
1
13
```

### 示例7：随机化整个集合

此命令将按随机顺序返回整个集合。

**Count** 参数的值是 **整数的一个静态属性** 。

若要按随机顺序返回整个集合，请输入任一大于或等于该集合中的对象数的数字。

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count ([int]::MaxValue)
```

```Output
2
3
5
1
8
13
```

### 示例8：获取随机非数值

此命令将从非数值集合中返回一个随机值。

```powershell
"red", "yellow", "blue" | Get-Random
```

```Output
yellow
```

### 示例9：使用 SetSeed 参数

此示例显示了使用 **SetSeed** 参数的效果。

因为 **SetSeed** 会产生非随机行为，所以它通常仅用于重现结果，例如调试或分析脚本时。

```powershell
# Commands with the default seed are pseudorandom
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100
Get-Random -Maximum 100
Get-Random -Maximum 100
```

```Output
74
56
84
46
```

```powershell
# Commands with the same seed are not random
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100 -SetSeed 23
```

```Output
74
74
74
```

```powershell
# SetSeed results in a repeatable series
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100
Get-Random -Maximum 100
Get-Random -Maximum 100
```

```Output
74
56
84
46
```

### 示例10：获取随机文件

这些命令将从本地计算机驱动器获取随机选择的50文件示例 `C:` 。

```powershell
$Files = Get-ChildItem -Path C:\* -Recurse
$Sample = $Files | Get-Random -Count 50
```

### 示例11：滚动公平骰子

此示例将一个公平片1200次，并对结果进行计数。 第一个命令 `For-EachObject` `Get-Random` 从数字 (1-6) 中的数字中重复对的调用。 结果按其值进行分组 `Group-Object` ，并将设置为带有的表格式 `Select-Object` 。

```powershell
1..1200 | ForEach-Object {
    1..6 | Get-Random
} | Group-Object | Select-Object Name,Count
```

```Output
Name Count
---- -----
1      206
2      199
3      196
4      226
5      185
6      188
```

## PARAMETERS

### -Count

指定要返回的随机对象或数字的数目。 默认值为 1。

当与一起使用时 `InputObject` ，如果 **Count** 的值超过集合中的对象数， `Get-Random` 则将按随机顺序返回所有对象。

```yaml
Type: System.Int32
Parameter Sets: RandomListItemParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定对象的集合。 `Get-Random` 以随机顺序从集合中随机选择的对象到 **Count** 指定的数字。 输入对象、一个包含这些对象的变量，或可获取这些对象的命令或表达式。 还可以通过管道将对象集合传递给 `Get-Random` 。

```yaml
Type: System.Object[]
Parameter Sets: RandomListItemParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Maximum

指定随机数的最大值。 `Get-Random` 返回小于 (不等于) 的最大值。 输入一个整数和一个双精度浮点数，或一个可以转换为整数或双精度的对象，如数值字符串 ( "100" ) 。

**Maximum** 值必须大于（不等于） **Minimum** 值。 如果 **最大** 值或 **最小** 值为浮点数，则 `Get-Random` 返回随机选择的浮点数。

在64位计算机上，如果 **最小** 值为32位整数，则 **最大** 值的默认 **值为 int32.maxvalue。**

如果 " **最小** 值" 为 double (浮点数) ，则 **最大** 值的默认值为 2 **。** 否则，默认 **值为 int32.maxvalue。**

```yaml
Type: System.Object
Parameter Sets: RandomNumberParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Minimum

指定随机数的最小值。 输入一个整数和一个双精度浮点数，或一个可以转换为整数或双精度的对象，如数值字符串 ( "100" ) 。 默认值为 0（零）。

**Minimum** 值必须小于（不等于） **Maximum** 值。 如果 **最大** 值或 **最小** 值为浮点数，则 `Get-Random` 返回随机选择的浮点数。

```yaml
Type: System.Object
Parameter Sets: RandomNumberParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SetSeed

为随机数生成程序指定种子值。 此种子值用于当前命令和当前会话中的所有后续 `Get-Random` 命令，直到再次使用 **SetSeed** 或关闭会话。 不能将种子重置为其默认值。

**SetSeed** 参数不是必需的。 默认情况下， `Get-Random` 使用 [RandomNumberGenerator ( # B1 ](/dotnet/api/system.security.cryptography.randomnumbergenerator) 方法来生成种子值。 因为 **SetSeed** 会导致非随机行为，所以通常仅在尝试重现行为时（例如在调试或分析包含命令的脚本时）使用 `Get-Random` 。

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Object

可以通过管道发送一个或多个对象。 `Get-Random` 从管道对象中随机选择值。

## 输出

### System.Int32, System.Int64, System.Double

`Get-Random` 返回一个整数或浮点数，或从已提交的集合中随机选择的对象。

## 注释

`Get-Random` 在会话启动时，根据系统时间时钟设置每个会话的默认种子。

`Get-Random` 并不总是返回与输入值相同的数据类型。 下表显示了每个数值输入类型的输出类型。

| 输入类型 | 输出类型 |
| :--------: | :---------: |
|   SByte    |   Double    |
|    Byte    |   Double    |
|   Int16    |   Double    |
|   UInt16   |   Double    |
|   Int32    |    Int32    |
|   UInt32   |   Double    |
|   Int64    |    Int64    |
|   UInt64   |   Double    |
|   Double   |   Double    |
|   Single   |   Double    |

从 Windows PowerShell 3.0 开始， `Get-Random` 支持64位整数。 在 Windows PowerShell 2.0 中，所有值都强制转换为 **system.object** 。

## 相关链接
