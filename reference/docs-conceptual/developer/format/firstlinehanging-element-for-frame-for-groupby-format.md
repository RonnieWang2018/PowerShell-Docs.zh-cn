---
title: GroupBy (Format) 的帧的 FirstLineHanging 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3def56e918810d9e201d7a9ae73776d90646d8b3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773600"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a>FirstLineHanging Element for Frame for GroupBy (Format)

指定将第一行数据向左移动的字符数。 此元素在定义如何显示新的对象组时使用。

配置元素 (格式) ViewDefinitions 元素 (格式) 视图元素 (格式) GroupBy 元素，用于 CustomEntries 的元素，适用于 CustomControl for groupby (格式) 元素 for for groupby (format) CustomEntry 元素 for CustomControl for groupby (format) CustomItem 元素 for CustomEntry for groupby (格式) 

## <a name="syntax"></a>语法

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了元素的属性、子元素和父元素 `FirstLineHanging` 。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[Frame Element for CustomItem for GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)|定义数据的显示方式，例如，将数据向左或向右移动。|

## <a name="text-value"></a>文本值

指定要将数据的第一行移动到的字符数。

## <a name="remarks"></a>备注

如果指定此元素，则不能指定[FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md)元素。

## <a name="see-also"></a>另请参阅

[FirstLineIndent Element for Frame for GroupBy (Format)](./firstlineindent-element-for-frame-for-groupby-format.md)

[Frame Element for CustomItem for GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
