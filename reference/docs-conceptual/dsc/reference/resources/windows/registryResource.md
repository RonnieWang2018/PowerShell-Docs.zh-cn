---
ms.date: 07/16/2020
ms.topic: reference
title: DSC Registry 资源
description: DSC Registry 资源
ms.openlocfilehash: 075f64abffb429b83958d859b0328b4eeec4cee6
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142491"
---
# <a name="dsc-registry-resource"></a>DSC Registry 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x

Windows PowerShell Desired State Configuration (DSC) 中的 **Registry** 资源提供了在目标节点上管理注册表项和值的机制。

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>语法

```Syntax
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Present | Absent }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>属性

|properties |说明 |
|---|---|
|密钥 |指示要确保其特定状态的注册表项的路径。 路径必须包含配置单元。 |
|ValueName |指示注册表值的名称。 若要添加或删除注册表项，请将此属性指定为空字符串，无需指定 **ValueType** 或 **ValueData** 。 若要修改或删除注册表项的默认值，请将此属性指定为空字符串，同时指定 **ValueType** 或 **ValueData** 。 |
|Force |如果指定的注册表项存在， **Force** 将用新值覆盖它。 如果要删除包含子项的注册表项，这必须是 `$true`。 |
|Hex |指示是否以十六进制格式表示数据。 如果指定此项，则以十六进制格式显示 DWORD/QWORD 值数据。 对其他类型无效。 默认值是 `$false`。 |
|ValueData |注册表值的数据。 |
|ValueType |指示值的类型。 支持的类型包括： **String** (REG_SZ)、 **Binary** (REG-BINARY)、 **Dword** （32 位 REG_DWORD）、 **Qword** （64 位 REG_QWORD）、 **MultiString** (REG_MULTI_SZ)、 **ExpandString** (REG_EXPAND_SZ)。 |

## <a name="common-properties"></a>公共属性

|properties |说明 |
|---|---|
|DependsOn |指示必须先运行其他资源的配置，再配置此资源。 例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |指示项和值是否存在。 若要确保其存在，请将此属性设置为 **Present** 。 若要确保其不存在，请将此属性设置为 **Absent** 。 默认值为 **Present** 。 |
|PsDscRunAsCredential |设置用于运行整个资源的身份的凭据。 |

> [!NOTE]
> 在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。 有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。

## <a name="examples"></a>示例

### <a name="example-1-ensure-specified-value-and-data-under-specified-registry-key"></a>示例 1：确保指定注册表项下具有指定值和数据

此示例确保 `HKEY\_LOCAL\_MACHINE` 配置单元中存在注册表值“TestValue”（位于“ExampleKey1”键下），并具有数据“TestData”。

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey1"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

### <a name="example-2-ensure-specified-registry-key-exists"></a>示例 2：确保指定的注册表项存在

此示例确保 HKEY\_LOCAL\_MACHINE 配置单元中存在名为“ExampleKey2”的键。

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey2"
        ValueName   = ""
    }
}
```

> [!NOTE]
> 必须使用用户凭据运行配置，而不是以系统身份运行，才能在 `HKEY_CURRENT_USER` 配置单元中更改注册表设置。 可以使用 **PsDscRunAsCredential** 属性来指定配置的用户凭据。 有关示例，请参阅[使用用户凭据运行 DSC](../../../configurations/runAsUser.md)。
