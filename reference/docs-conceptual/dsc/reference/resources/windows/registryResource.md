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
# <a name="dsc-registry-resource"></a><span data-ttu-id="f24ca-103">DSC Registry 资源</span><span class="sxs-lookup"><span data-stu-id="f24ca-103">DSC Registry Resource</span></span>

> <span data-ttu-id="f24ca-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="f24ca-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="f24ca-105">Windows PowerShell Desired State Configuration (DSC) 中的 **Registry** 资源提供了在目标节点上管理注册表项和值的机制。</span><span class="sxs-lookup"><span data-stu-id="f24ca-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="f24ca-106">语法</span><span class="sxs-lookup"><span data-stu-id="f24ca-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="f24ca-107">属性</span><span class="sxs-lookup"><span data-stu-id="f24ca-107">Properties</span></span>

|<span data-ttu-id="f24ca-108">properties</span><span class="sxs-lookup"><span data-stu-id="f24ca-108">Property</span></span> |<span data-ttu-id="f24ca-109">说明</span><span class="sxs-lookup"><span data-stu-id="f24ca-109">Description</span></span> |
|---|---|
|<span data-ttu-id="f24ca-110">密钥</span><span class="sxs-lookup"><span data-stu-id="f24ca-110">Key</span></span> |<span data-ttu-id="f24ca-111">指示要确保其特定状态的注册表项的路径。</span><span class="sxs-lookup"><span data-stu-id="f24ca-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="f24ca-112">路径必须包含配置单元。</span><span class="sxs-lookup"><span data-stu-id="f24ca-112">This path must include the hive.</span></span> |
|<span data-ttu-id="f24ca-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="f24ca-113">ValueName</span></span> |<span data-ttu-id="f24ca-114">指示注册表值的名称。</span><span class="sxs-lookup"><span data-stu-id="f24ca-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="f24ca-115">若要添加或删除注册表项，请将此属性指定为空字符串，无需指定 **ValueType** 或 **ValueData** 。</span><span class="sxs-lookup"><span data-stu-id="f24ca-115">To add or remove a registry key, specify this property as an empty string without specifying **ValueType** or **ValueData** .</span></span> <span data-ttu-id="f24ca-116">若要修改或删除注册表项的默认值，请将此属性指定为空字符串，同时指定 **ValueType** 或 **ValueData** 。</span><span class="sxs-lookup"><span data-stu-id="f24ca-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying **ValueType** or **ValueData** .</span></span> |
|<span data-ttu-id="f24ca-117">Force</span><span class="sxs-lookup"><span data-stu-id="f24ca-117">Force</span></span> |<span data-ttu-id="f24ca-118">如果指定的注册表项存在， **Force** 将用新值覆盖它。</span><span class="sxs-lookup"><span data-stu-id="f24ca-118">If the specified registry key is present, **Force** overwrites it with the new value.</span></span> <span data-ttu-id="f24ca-119">如果要删除包含子项的注册表项，这必须是 `$true`。</span><span class="sxs-lookup"><span data-stu-id="f24ca-119">If deleting a registry key with subkeys, this needs to be `$true`.</span></span> |
|<span data-ttu-id="f24ca-120">Hex</span><span class="sxs-lookup"><span data-stu-id="f24ca-120">Hex</span></span> |<span data-ttu-id="f24ca-121">指示是否以十六进制格式表示数据。</span><span class="sxs-lookup"><span data-stu-id="f24ca-121">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="f24ca-122">如果指定此项，则以十六进制格式显示 DWORD/QWORD 值数据。</span><span class="sxs-lookup"><span data-stu-id="f24ca-122">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="f24ca-123">对其他类型无效。</span><span class="sxs-lookup"><span data-stu-id="f24ca-123">Not valid for other types.</span></span> <span data-ttu-id="f24ca-124">默认值是 `$false`。</span><span class="sxs-lookup"><span data-stu-id="f24ca-124">The default value is `$false`.</span></span> |
|<span data-ttu-id="f24ca-125">ValueData</span><span class="sxs-lookup"><span data-stu-id="f24ca-125">ValueData</span></span> |<span data-ttu-id="f24ca-126">注册表值的数据。</span><span class="sxs-lookup"><span data-stu-id="f24ca-126">The data for the registry value.</span></span> |
|<span data-ttu-id="f24ca-127">ValueType</span><span class="sxs-lookup"><span data-stu-id="f24ca-127">ValueType</span></span> |<span data-ttu-id="f24ca-128">指示值的类型。</span><span class="sxs-lookup"><span data-stu-id="f24ca-128">Indicates the type of the value.</span></span> <span data-ttu-id="f24ca-129">支持的类型包括： **String** (REG_SZ)、 **Binary** (REG-BINARY)、 **Dword** （32 位 REG_DWORD）、 **Qword** （64 位 REG_QWORD）、 **MultiString** (REG_MULTI_SZ)、 **ExpandString** (REG_EXPAND_SZ)。</span><span class="sxs-lookup"><span data-stu-id="f24ca-129">The supported types are: **String** (REG_SZ), **Binary** (REG-BINARY), **Dword** (32-bit REG_DWORD), **Qword** (64-bit REG_QWORD), **MultiString** (REG_MULTI_SZ), **ExpandString** (REG_EXPAND_SZ).</span></span> |

## <a name="common-properties"></a><span data-ttu-id="f24ca-130">公共属性</span><span class="sxs-lookup"><span data-stu-id="f24ca-130">Common properties</span></span>

|<span data-ttu-id="f24ca-131">properties</span><span class="sxs-lookup"><span data-stu-id="f24ca-131">Property</span></span> |<span data-ttu-id="f24ca-132">说明</span><span class="sxs-lookup"><span data-stu-id="f24ca-132">Description</span></span> |
|---|---|
|<span data-ttu-id="f24ca-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f24ca-133">DependsOn</span></span> |<span data-ttu-id="f24ca-134">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="f24ca-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f24ca-135">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="f24ca-135">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="f24ca-136">Ensure</span><span class="sxs-lookup"><span data-stu-id="f24ca-136">Ensure</span></span> |<span data-ttu-id="f24ca-137">指示项和值是否存在。</span><span class="sxs-lookup"><span data-stu-id="f24ca-137">Indicates if the key and value exist.</span></span> <span data-ttu-id="f24ca-138">若要确保其存在，请将此属性设置为 **Present** 。</span><span class="sxs-lookup"><span data-stu-id="f24ca-138">To ensure that they do, set this property to **Present** .</span></span> <span data-ttu-id="f24ca-139">若要确保其不存在，请将此属性设置为 **Absent** 。</span><span class="sxs-lookup"><span data-stu-id="f24ca-139">To ensure that they do not exist, set the property to **Absent** .</span></span> <span data-ttu-id="f24ca-140">默认值为 **Present** 。</span><span class="sxs-lookup"><span data-stu-id="f24ca-140">The default value is **Present** .</span></span> |
|<span data-ttu-id="f24ca-141">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="f24ca-141">PsDscRunAsCredential</span></span> |<span data-ttu-id="f24ca-142">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="f24ca-142">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="f24ca-143">在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="f24ca-143">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="f24ca-144">有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="f24ca-144">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="examples"></a><span data-ttu-id="f24ca-145">示例</span><span class="sxs-lookup"><span data-stu-id="f24ca-145">Examples</span></span>

### <a name="example-1-ensure-specified-value-and-data-under-specified-registry-key"></a><span data-ttu-id="f24ca-146">示例 1：确保指定注册表项下具有指定值和数据</span><span class="sxs-lookup"><span data-stu-id="f24ca-146">Example 1: Ensure specified Value and Data under specified registry key</span></span>

<span data-ttu-id="f24ca-147">此示例确保 `HKEY\_LOCAL\_MACHINE` 配置单元中存在注册表值“TestValue”（位于“ExampleKey1”键下），并具有数据“TestData”。</span><span class="sxs-lookup"><span data-stu-id="f24ca-147">This example ensures that the registry value "TestValue" under a key named "ExampleKey1" is present in the `HKEY\_LOCAL\_MACHINE` hive and has the data "TestData".</span></span>

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

### <a name="example-2-ensure-specified-registry-key-exists"></a><span data-ttu-id="f24ca-148">示例 2：确保指定的注册表项存在</span><span class="sxs-lookup"><span data-stu-id="f24ca-148">Example 2: Ensure specified registry key exists</span></span>

<span data-ttu-id="f24ca-149">此示例确保 HKEY\_LOCAL\_MACHINE 配置单元中存在名为“ExampleKey2”的键。</span><span class="sxs-lookup"><span data-stu-id="f24ca-149">This example ensures that a key named "ExampleKey2" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>

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
> <span data-ttu-id="f24ca-150">必须使用用户凭据运行配置，而不是以系统身份运行，才能在 `HKEY_CURRENT_USER` 配置单元中更改注册表设置。</span><span class="sxs-lookup"><span data-stu-id="f24ca-150">Changing a registry setting in the `HKEY_CURRENT_USER` hive requires that the configuration runs with user credentials, rather than as the system.</span></span> <span data-ttu-id="f24ca-151">可以使用 **PsDscRunAsCredential** 属性来指定配置的用户凭据。</span><span class="sxs-lookup"><span data-stu-id="f24ca-151">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="f24ca-152">有关示例，请参阅[使用用户凭据运行 DSC](../../../configurations/runAsUser.md)。</span><span class="sxs-lookup"><span data-stu-id="f24ca-152">For an example, see [Running DSC with user credentials](../../../configurations/runAsUser.md).</span></span>
