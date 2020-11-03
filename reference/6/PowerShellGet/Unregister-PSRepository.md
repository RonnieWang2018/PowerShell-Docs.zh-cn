---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/unregister-psrepository?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSRepository
ms.openlocfilehash: 50a8230385606dcf42c47787dea8feb30cd23f89
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93198559"
---
# Unregister-PSRepository

## 摘要
取消注册存储库。

## SYNTAX

```
Unregister-PSRepository [-Name] <String[]> [<CommonParameters>]
```

## DESCRIPTION

`Unregister-PSRepository`Cmdlet 将为当前用户注销存储库。

## 示例

### 示例1：取消注册存储库

此示例将注销名为 myNuGetSource 的存储库。

```powershell
Unregister-PSRepository -Name "myNuGetSource"
```

### 示例2：取消注册所有存储库

此示例使用 `Get-PSRepository` 来获取所有已注册的存储库，并使用管道运算符将其传递给 `Unregister-PSRepository` 以将其注销。

```powershell
Get-PSRepository | Unregister-PSRepository
```

## PARAMETERS

### -Name

指定要删除的存储库的名称数组。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String[]

## 输出

### System.Object

## 注释

## 相关链接

[Get-PSRepository](Get-PSRepository.md)

[Register-PSRepository](Register-PSRepository.md)

[Set-PSRepository](Set-PSRepository.md)
