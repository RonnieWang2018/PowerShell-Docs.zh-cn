---
ms.date: 07/17/2020
ms.topic: reference
title: GetConfiguration 方法
description: GetConfiguration 方法
ms.openlocfilehash: a49f810bd227142c8c3ae4de45f69450400e4e8c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650871"
---
# <a name="getconfiguration-method"></a>GetConfiguration 方法

将配置文档发送到托管节点，并使用配置代理的 **Get** 方法以应用配置。

## <a name="syntax"></a>语法

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a>参数

configurationData  \[in\]：指定要发送的配置数据。

configurations  \[out\]：返回响应时，包含配置的嵌入实例。

## <a name="return-value"></a>返回值

如果成功，则返回零；否则返回错误代码。

## <a name="remarks"></a>备注

这是一种静态方法。

## <a name="requirements"></a>要求

**MOF：** DscCore.mof

**命名空间** ：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另请参阅

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
