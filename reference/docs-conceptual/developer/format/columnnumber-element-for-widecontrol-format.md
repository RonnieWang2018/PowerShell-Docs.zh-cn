---
title: WideControl (Format) 的 ColumnNumber 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5f151bb0e629efcebe6295cdcae6cebcbbb1b39b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783851"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>ColumnNumber Element for WideControl (Format)

指定宽视图中显示的列数。

配置元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 元素 (格式) ColumnNumber 元素 (格式) 

## <a name="syntax"></a>语法

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了元素的属性、子元素和父元素 `ColumnNumber` 。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideControl Element (Format)](./widecontrol-element-format.md)|定义视图的宽 (单个值) 列表格式。|

## <a name="text-value"></a>文本值

指定一个正整数值。

## <a name="remarks"></a>备注

定义宽视图时，可以添加 `AutoSize` 元素或 `ColumnNumber` 元素，但不能同时添加这两个元素。

有关宽视图组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。

有关宽视图的示例，请参阅[宽视图 (基本) ](./wide-view-basic.md)。

## <a name="see-also"></a>另请参阅

[WideControl 的 Autosize 元素 (格式) ](./autosize-element-for-widecontrol-format.md)

[创建宽视图](./creating-a-wide-view.md)

[宽视图 (Basic)](./wide-view-basic.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
