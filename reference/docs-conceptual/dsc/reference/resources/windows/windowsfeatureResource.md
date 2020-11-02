---
ms.date: 07/16/2020
ms.topic: reference
title: DSC WindowsFeature 资源。
description: DSC WindowsFeature 资源。
ms.openlocfilehash: 0089e1d2a045e9398aa53a3cedc3f64285c7cd58
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142984"
---
# <a name="dsc-windowsfeature-resource"></a>DSC WindowsFeature 资源。

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x

Windows PowerShell Desired State Configuration (DSC) 中的 **WindowsFeature** 资源提供了在目标节点上添加或删除角色和功能的机制。

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>语法

```Syntax
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>属性

|properties |说明 |
|---|---|
|名称 |指示想确保添加或删除的角色或功能的名称。 此参数与来自 [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet 的 **Name** 属性一样，并非该角色或功能的显示名称。 |
|凭据 |指示要用于添加或删除角色或功能的凭据。 |
|IncludeAllSubFeature |将此属性设置为 `$true` 以确保所有必需的子功能的状态为通过 **Name** 属性指定的功能的状态。 |
|LogPath |指示你希望资源提供程序在其中记录操作的日志文件的路径。 |

## <a name="common-properties"></a>公共属性

|properties |说明 |
|---|---|
|DependsOn |指示必须先运行其他资源的配置，再配置此资源。 例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |指示是否已添加角色或功能。 若要确保添加角色或功能，请将此属性设置为 **Present** 。 若要确保删除角色或功能，请将此属性设置为 **Absent** 。 默认值为 **Present** 。 |
|PsDscRunAsCredential |设置用于运行整个资源的身份的凭据。 |

> [!NOTE]
> 在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。 有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。

## <a name="example"></a>示例

```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```
