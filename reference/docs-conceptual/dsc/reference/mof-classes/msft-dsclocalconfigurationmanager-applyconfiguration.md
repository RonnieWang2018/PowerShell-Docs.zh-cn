---
ms.date: 07/14/2020
ms.topic: reference
title: ApplyConfiguration 方法
description: ApplyConfiguration 方法
ms.openlocfilehash: aa99221b33d39c3ecc70156a11eaee10b540e2dc
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664279"
---
# <a name="applyconfiguration-method"></a>ApplyConfiguration 方法

使用配置代理应用处于挂起状态的配置。

如果没有挂起的配置，此方法将重新应用当前配置。

## <a name="syntax"></a>语法

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>参数

### <a name="force"></a>force

如果为 **true** ，将会重新应用当前配置，即使存在挂起的配置。

## <a name="return-value"></a>返回值

如果成功，则返回零；否则返回错误代码。

## <a name="remarks"></a>注解

这是一种静态方法。

## <a name="requirements"></a>要求

**MOF：** DscCore.mof

**命名空间** ：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另请参阅

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
