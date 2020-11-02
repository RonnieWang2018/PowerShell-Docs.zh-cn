---
ms.date: 07/17/2020
ms.topic: reference
title: GetConfigurationResultOutput 方法
description: GetConfigurationResultOutput 方法
ms.openlocfilehash: 7c885109b3078189b7ac653733a5fb24db66312e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644710"
---
# <a name="getconfigurationresultoutput-method"></a>GetConfigurationResultOutput 方法

获取与特定作业相关的配置代理输出。

## <a name="syntax"></a>语法

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a>参数

jobId  \[in\]：要为其获取输出数据的作业的 ID。

resumeOutputBookmark  \[in\]：指定输出应接着上一书签。

output  \[out\]：指定作业的输出。

## <a name="return-value"></a>返回值

如果成功，则返回零；否则返回错误代码。

## <a name="remarks"></a>备注

这是一种静态方法。

## <a name="requirements"></a>要求

**MOF：** DscCore.mof

**命名空间** ：Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>另请参阅

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
