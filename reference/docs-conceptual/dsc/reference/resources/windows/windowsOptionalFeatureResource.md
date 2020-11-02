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
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="b5200-103">DSC WindowsOptionalFeature 资源</span><span class="sxs-lookup"><span data-stu-id="b5200-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="b5200-104">适用于：Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="b5200-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="b5200-105">Windows PowerShell Desired State Configuration (DSC) 中的 **WindowsOptionalFeature** 资源提供了确保在目标节点上启用可选功能的机制。</span><span class="sxs-lookup"><span data-stu-id="b5200-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

> [!NOTE]
> <span data-ttu-id="b5200-106">WindowsOptionalFeature 仅适用于 Windows 10 等 Windows 客户端计算机。</span><span class="sxs-lookup"><span data-stu-id="b5200-106">**WindowsOptionalFeature** only works on Windows client machines like Windows 10.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="b5200-107">语法</span><span class="sxs-lookup"><span data-stu-id="b5200-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="b5200-108">属性</span><span class="sxs-lookup"><span data-stu-id="b5200-108">Properties</span></span>

|<span data-ttu-id="b5200-109">属性</span><span class="sxs-lookup"><span data-stu-id="b5200-109">Property</span></span> |<span data-ttu-id="b5200-110">说明</span><span class="sxs-lookup"><span data-stu-id="b5200-110">Description</span></span> |
|---|---|
|<span data-ttu-id="b5200-111">名称</span><span class="sxs-lookup"><span data-stu-id="b5200-111">Name</span></span> |<span data-ttu-id="b5200-112">指示要确保启用或禁用的功能的名称。</span><span class="sxs-lookup"><span data-stu-id="b5200-112">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span> |
|<span data-ttu-id="b5200-113">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="b5200-113">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="b5200-114">指定 DISM 在搜索源文件以启用功能时是否联系 Windows 更新 (WU)。</span><span class="sxs-lookup"><span data-stu-id="b5200-114">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="b5200-115">如果为 `$true`，则 DISM 不联系 WU。</span><span class="sxs-lookup"><span data-stu-id="b5200-115">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="b5200-116">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="b5200-116">RemoveFilesOnDisable</span></span> |<span data-ttu-id="b5200-117">当 **Ensure** 设置为 **Absent** 时，设置为 `$true` 以删除与功能关联的所有文件。</span><span class="sxs-lookup"><span data-stu-id="b5200-117">Set to `$true` to remove all files associated with the feature when **Ensure** is set to **Absent** .</span></span> |
|<span data-ttu-id="b5200-118">LogLevel</span><span class="sxs-lookup"><span data-stu-id="b5200-118">LogLevel</span></span> |<span data-ttu-id="b5200-119">日志中显示的最大输出级别。</span><span class="sxs-lookup"><span data-stu-id="b5200-119">The maximum output level shown in the logs.</span></span> <span data-ttu-id="b5200-120">接受的值包括： **ErrorsOnly** 、 **ErrorsAndWarning** 和 **ErrorsAndWarningAndInformation** 。</span><span class="sxs-lookup"><span data-stu-id="b5200-120">The accepted values are: **ErrorsOnly** , **ErrorsAndWarning** , and **ErrorsAndWarningAndInformation** .</span></span> |
|<span data-ttu-id="b5200-121">LogPath</span><span class="sxs-lookup"><span data-stu-id="b5200-121">LogPath</span></span> |<span data-ttu-id="b5200-122">希望资源提供程序在其中记录操作的日志文件的路径。</span><span class="sxs-lookup"><span data-stu-id="b5200-122">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="b5200-123">公共属性</span><span class="sxs-lookup"><span data-stu-id="b5200-123">Common properties</span></span>

|<span data-ttu-id="b5200-124">properties</span><span class="sxs-lookup"><span data-stu-id="b5200-124">Property</span></span> |<span data-ttu-id="b5200-125">说明</span><span class="sxs-lookup"><span data-stu-id="b5200-125">Description</span></span> |
|---|---|
|<span data-ttu-id="b5200-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b5200-126">DependsOn</span></span> |<span data-ttu-id="b5200-127">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="b5200-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b5200-128">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="b5200-128">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="b5200-129">Ensure</span><span class="sxs-lookup"><span data-stu-id="b5200-129">Ensure</span></span> |<span data-ttu-id="b5200-130">指定是否已启用该功能。</span><span class="sxs-lookup"><span data-stu-id="b5200-130">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="b5200-131">若要确保启用功能，请将此属性设置为 _Enable_ 。</span><span class="sxs-lookup"><span data-stu-id="b5200-131">To ensure that the feature is enabled, set this property to _Enable_ .</span></span> <span data-ttu-id="b5200-132">若要确保禁用功能，请将此属性设置为 _Disable_ 。</span><span class="sxs-lookup"><span data-stu-id="b5200-132">To ensure that the feature is disabled, set the property to _Disable_ .</span></span> <span data-ttu-id="b5200-133">默认值为 _Enable_ 。</span><span class="sxs-lookup"><span data-stu-id="b5200-133">The default value is _Enable_ .</span></span> |
|<span data-ttu-id="b5200-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="b5200-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="b5200-135">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="b5200-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="b5200-136">在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="b5200-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="b5200-137">有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="b5200-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>
