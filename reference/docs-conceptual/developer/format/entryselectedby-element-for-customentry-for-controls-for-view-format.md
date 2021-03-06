---
title: View (Format) 的控件的 CustomEntry 的 EntrySelectedBy 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5c82e02d23b1694d05f7a32578ccc5d33686f13f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774246"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a>EntrySelectedBy Element for CustomEntry for Controls for View (Format)

定义使用此控件定义的 .NET 类型或要使用此定义时必须存在的条件。 定义可由视图使用的控件时，将使用此元素。

配置元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控件元素 (格式) 用于控件的控件 (控件元素) CustomControl 元素，用于控件的视图 (格式) CustomEntries 元素 (CustomEntry 的控件) CustomEntries 的控件，用于查看 (格式的控件) EntrySelectedBy 元素

## <a name="syntax"></a>语法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了元素的属性、子元素和父元素 `EntrySelectedBy` 。 必须为定义至少指定一个类型、选择集或选择条件。 您可以使用的子元素数没有最大限制。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[SelectionCondition Element for EntrySelectedBy for Controls for View (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|可选元素。<br /><br /> 定义要使用此定义必须存在的条件。|
|[SelectionSetName Element for EntrySelectedBy for Controls for View (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|可选元素。<br /><br /> 指定一组使用此控件定义的 .NET 类型。|
|[TypeName Element for EntrySelectedBy for Controls for View (Format)](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|可选元素。<br /><br /> 指定使用控件的此定义的 .NET 类型。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[CustomEntry Element for CustomEntries for Controls for View (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|提供控件的定义。|

## <a name="remarks"></a>备注

选择条件用于定义要使用的定义必须存在的条件，例如当对象具有特定属性或特定属性值或脚本计算结果为时 `true` 。 有关选择条件的详细信息，请参阅[定义使用视图条目或项的条件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另请参阅

[CustomEntry Element for CustomEntries for Controls for View (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
