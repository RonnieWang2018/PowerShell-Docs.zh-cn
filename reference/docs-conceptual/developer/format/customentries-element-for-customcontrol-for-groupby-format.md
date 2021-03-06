---
title: GroupBy (Format) 的 CustomControl 的 CustomEntries 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2221d1bb94159697ff10466e4606d6d54e117e30
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785942"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a>CustomEntries Element for CustomControl for GroupBy (Format)

提供控件的定义。 此元素在定义如何显示新的对象组时使用。

配置元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomEntries 元素 for 元素 for CustomControl for GroupBy (格式) CustomControl 元素 (

## <a name="syntax"></a>语法

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了元素的属性、子元素和父元素 `CustomEntries` 。 对于可指定的子元素数没有最大限制。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[CustomEntry Element for CustomControl for GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)|必需的元素。<br /><br /> 提供控件的定义。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[CustomControl Element for GroupBy (Format)](./customcontrol-element-for-groupby-format.md)|定义显示新组的自定义控件。|

## <a name="remarks"></a>备注

在大多数情况下，控件只有一个定义，该定义是在单个元素中指定的 `CustomEntry` 。 但是，如果要使用相同的控件来显示不同的组，则可以提供多个定义。 在这些情况下，可以 `CustomEntry` 为组定义元素。

## <a name="see-also"></a>另请参阅

[CustomEntry Element for CustomEntries for Controls for View (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[CustomControl Element for GroupBy (Format)](./customcontrol-element-for-groupby-format.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
