---
title: View (Format) 的控件的 ExpressionBinding 的 CustomControlName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 871c6afd89db9360ea5012191b08863a9441f899
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786010"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a>CustomControlName Element for ExpressionBinding for Controls for View (Format)

指定公共控件或视图控件的名称。 定义可由视图使用的控件时，将使用此元素。

配置元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控件元素 (格式) 用于控件的控件 (控件元素) 用于控件的控件 (CustomControl 的 CustomEntries 元素用于视图 (格式的控件的 CustomEntries) CustomEntry 元素的格式) CustomItem 元素 For CustomEntry 的控件 For view) 格式的控件 (ExpressionBinding 元素) CustomItem 元素 For CustomControlName 的控件 (ExpressionBindine)  (

## <a name="syntax"></a>语法

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了元素的属性、子元素和父元素 `CustomControlName` 。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|定义控件显示的数据。|

## <a name="text-value"></a>文本值

指定控件的名称。

## <a name="remarks"></a>备注

您可以创建可供格式设置文件的所有视图使用的公共控件，还可以创建可供特定视图使用的视图控件。 以下元素指定这些控件的名称：

- [Name Element for Control for Controls for Configuration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name Element for Control for Controls for View (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>另请参阅

[Name Element for Control for Controls for Configuration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Name Element for Control for Controls for View (Format)](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
