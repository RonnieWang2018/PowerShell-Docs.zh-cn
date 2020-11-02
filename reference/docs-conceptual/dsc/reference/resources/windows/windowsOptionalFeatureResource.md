---
ms.date: 08/28/2020
ms.topic: reference
title: DSC WindowsOptionalFeature 资源
description: DSC WindowsOptionalFeature 资源
ms.openlocfilehash: 1c7e888ea49b0d1710cc22c975cb618999238f67
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143052"
---
# <a name="dsc-windowsoptionalfeature-resource"></a>DSC WindowsOptionalFeature 资源

> 适用于：Windows PowerShell 5.x

Windows PowerShell Desired State Configuration (DSC) 中的 **WindowsOptionalFeature** 资源提供了确保在目标节点上启用可选功能的机制。

> [!NOTE]
> WindowsOptionalFeature 仅适用于 Windows 10 等 Windows 客户端计算机。

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>语法

```Syntax
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>属性

|属性 |说明 |
|---|---|
|名称 |指示要确保启用或禁用的功能的名称。 |
|NoWindowsUpdateCheck |指定 DISM 在搜索源文件以启用功能时是否联系 Windows 更新 (WU)。 如果为 `$true`，则 DISM 不联系 WU。 |
|RemoveFilesOnDisable |当 **Ensure** 设置为 **Absent** 时，设置为 `$true` 以删除与功能关联的所有文件。 |
|LogLevel |日志中显示的最大输出级别。 接受的值包括： **ErrorsOnly** 、 **ErrorsAndWarning** 和 **ErrorsAndWarningAndInformation** 。 |
|LogPath |希望资源提供程序在其中记录操作的日志文件的路径。 |

## <a name="common-properties"></a>公共属性

|properties |说明 |
|---|---|
|DependsOn |指示必须先运行其他资源的配置，再配置此资源。 例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |指定是否已启用该功能。 若要确保启用功能，请将此属性设置为 _Enable_ 。 若要确保禁用功能，请将此属性设置为 _Disable_ 。 默认值为 _Enable_ 。 |
|PsDscRunAsCredential |设置用于运行整个资源的身份的凭据。 |

> [!NOTE]
> 在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。 有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。
