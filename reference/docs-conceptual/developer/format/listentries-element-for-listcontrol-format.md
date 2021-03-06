---
title: ListControl (Format) 的 ListEntries 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0fe07e739c2d2fec153599ec6c0c0b3ecc14df18
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785704"
---
# <a name="listentries-element-for-listcontrol-format"></a>ListEntries Element for ListControl (Format)

提供列表视图的定义。 列表视图必须指定一个或多个定义。

配置元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 元素 (格式) ListEntries 元素 (格式) 

## <a name="syntax"></a>语法

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了元素的属性、子元素和父元素 `ListEntries` 。 必须至少指定一个子元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[ListEntry 元素 (格式) ](./listentry-element-for-listcontrol-format.md)|提供列表视图的定义。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[ListControl Element (Format)](./listcontrol-element-format.md)|定义视图的列表格式。|

## <a name="remarks"></a>备注

有关列表视图的详细信息，请参阅[列表视图](./creating-a-list-view.md)。

## <a name="example"></a>示例

此示例显示了为[system.serviceprocess. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象定义列表视图的 XML 元素。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>另请参阅

[ListControl Element (Format)](./listcontrol-element-format.md)

[ListEntry 元素 (格式) ](./listentry-element-for-listcontrol-format.md)

[列表视图](./creating-a-list-view.md)

[编写 Windows PowerShell 格式设置和类型文件](./writing-a-powershell-formatting-file.md)
