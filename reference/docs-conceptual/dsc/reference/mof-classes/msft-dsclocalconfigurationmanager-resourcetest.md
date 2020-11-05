---
ms.date: 07/17/2020
ms.topic: reference
title: ResourceTest 方法
description: ResourceTest 方法
ms.openlocfilehash: cbac53ea96a59ec92fa840f75cd264a3125b965a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650677"
---
# <a name="resourcetest-method"></a>ResourceTest 方法

直接调用 DSC 资源的 **Test** 方法。

## <a name="syntax"></a>语法

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a>参数

ResourceType  \[in\]：要调用的资源的名称。

ModuleName  \[in\]：包含要调用资源的模块名称。

resourceProperty* \[in\] 在哈希表中分别将资源属性名及其值指定为键和值。 使用 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet 可以发现资源属性及其类型。

*InDesiredState** \[out\] 返回响应时，如果目标节点处于所需状态，便会将此属性设置为 true。

## <a name="return-value"></a>返回值

如果成功，则返回零；否则返回错误代码。

## <a name="remarks"></a>备注

这是一种静态方法。

## <a name="requirements"></a>要求

**MOF：** DscCore.mof

**命名空间** ：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另请参阅

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
