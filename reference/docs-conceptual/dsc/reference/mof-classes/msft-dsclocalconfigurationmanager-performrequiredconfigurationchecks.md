---
ms.date: 07/17/2020
ms.topic: reference
title: PerformRequiredConfigurationChecks 方法
description: PerformRequiredConfigurationChecks 方法
ms.openlocfilehash: c5e847cda6376f4266cc771dc947032a279e25f4
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650833"
---
# <a name="performrequiredconfigurationchecks-method"></a>PerformRequiredConfigurationChecks 方法

使用任务计划程序启动一致性检查。

## <a name="syntax"></a>语法

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a>参数

Flags  \[in\]：指定要运行的一致性检查类型的位掩码。 以下值有效，并可以通过 **OR** 位运算组合：

|值 |说明 |
|:--- |:---|
|**1** | 常规的一致性检查。 |
|**2** | 重启后一致性检查的延续。 此值不应与其他值组合。 |
|**4** | 应从节点的元配置中指定的请求服务器请求配置。 此值应始终与 **1** 组合，以获得为 **5** 的值。 |
|**8** | 将状态发送到报表服务器。 |

## <a name="return-value"></a>返回值

如果成功，则返回零；否则返回错误代码。

## <a name="remarks"></a>备注

这是一种静态方法。

## <a name="requirements"></a>要求

**MOF：** DscCore.mof

**命名空间** ：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另请参阅

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
