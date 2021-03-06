---
title: GroupBy (Format) 的 ExpressionBinding 的 ItemSelectionCondition 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a9b74f1882efc578f7d9ab27b8cd2f8a52833ab8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773430"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a>ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)

定义要使用此控件必须存在的条件。 对于可为控件项指定的选择条件数没有限制。 此元素在定义如何显示新的对象组时使用。

配置元素 (格式) ViewDefinitions 元素 (格式) 视图元素 (格式) GroupBy 元素，用于 CustomEntries 的元素，适用于 CustomControl for groupby (格式) 元素 for for groupby (format) CustomEntry 元素 for CustomControl for groupby (format) CustomItem 元素 for CustomEntry for groupby (format) 

## <a name="syntax"></a>语法

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了元素的属性、子元素和父元素 `ItemSelectionCondition` 。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[PropertyName Element for ItemSelectionCondition for GroupBy (Format)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|可选元素。<br /><br /> 指定触发条件的 .NET 属性。|
|[ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|可选元素。<br /><br /> 指定触发条件的脚本。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[ExpressionBinding Element for CustomItem for GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|定义控件显示的数据。|

## <a name="remarks"></a>备注

您可以为此条件指定一个属性名称或脚本，但不能同时指定两者。

## <a name="see-also"></a>另请参阅

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)

[ExpressionBinding Element for CustomItem for GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)
