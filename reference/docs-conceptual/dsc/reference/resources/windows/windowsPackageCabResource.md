---
ms.date: 07/16/2020
ms.topic: reference
title: DSC WindowsPackageCab 资源
description: DSC WindowsPackageCab 资源
ms.openlocfilehash: 3ac10eb2a7da502b8cac23ab8bfee869a4e26fd3
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143018"
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="d7904-103">DSC WindowsPackageCab 资源</span><span class="sxs-lookup"><span data-stu-id="d7904-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="d7904-104">适用于：Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="d7904-104">Applies To: Windows PowerShell 5.1</span></span>

<span data-ttu-id="d7904-105">Windows PowerShell Desired State Configuration (DSC) 中的 WindowsPackageCab  资源提供了一种机制，用于在目标节点上安装或卸载 Windows Cabinet (.cab) 程序包。</span><span class="sxs-lookup"><span data-stu-id="d7904-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="d7904-106">目标节点必须已安装 DISM PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="d7904-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="d7904-107">有关信息，请参阅[在 Windows PowerShell 中使用 DISM](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14)。</span><span class="sxs-lookup"><span data-stu-id="d7904-107">For information, see [Use DISM in Windows PowerShell](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="d7904-108">语法</span><span class="sxs-lookup"><span data-stu-id="d7904-108">Syntax</span></span>

```Syntax
{
    Name = [string]
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    Ensure = [string] { Absent | Present }
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="d7904-109">属性</span><span class="sxs-lookup"><span data-stu-id="d7904-109">Properties</span></span>

|<span data-ttu-id="d7904-110">properties</span><span class="sxs-lookup"><span data-stu-id="d7904-110">Property</span></span> |<span data-ttu-id="d7904-111">说明</span><span class="sxs-lookup"><span data-stu-id="d7904-111">Description</span></span> |
|---|---|
|<span data-ttu-id="d7904-112">名称</span><span class="sxs-lookup"><span data-stu-id="d7904-112">Name</span></span> |<span data-ttu-id="d7904-113">指明要确保其处于特定状态的程序包的名称。</span><span class="sxs-lookup"><span data-stu-id="d7904-113">Indicates the name of the package for you want to ensure a specific state.</span></span> |
|<span data-ttu-id="d7904-114">SourcePath</span><span class="sxs-lookup"><span data-stu-id="d7904-114">SourcePath</span></span> |<span data-ttu-id="d7904-115">指示程序包所在的路径。</span><span class="sxs-lookup"><span data-stu-id="d7904-115">Indicates the path where the package resides.</span></span> |
|<span data-ttu-id="d7904-116">LogPath</span><span class="sxs-lookup"><span data-stu-id="d7904-116">LogPath</span></span> |<span data-ttu-id="d7904-117">指示你希望提供程序用于保存安装或卸载程序包的日志文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="d7904-117">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="d7904-118">公共属性</span><span class="sxs-lookup"><span data-stu-id="d7904-118">Common properties</span></span>

|<span data-ttu-id="d7904-119">properties</span><span class="sxs-lookup"><span data-stu-id="d7904-119">Property</span></span> |<span data-ttu-id="d7904-120">说明</span><span class="sxs-lookup"><span data-stu-id="d7904-120">Description</span></span> |
|---|---|
|<span data-ttu-id="d7904-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d7904-121">DependsOn</span></span> |<span data-ttu-id="d7904-122">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="d7904-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d7904-123">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="d7904-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="d7904-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="d7904-124">Ensure</span></span> |<span data-ttu-id="d7904-125">指示程序包是否已安装。</span><span class="sxs-lookup"><span data-stu-id="d7904-125">Indicates if the package is installed.</span></span> <span data-ttu-id="d7904-126">将此属性设置为 **Absent** 可确保未安装包（如果已安装，则卸载包）。</span><span class="sxs-lookup"><span data-stu-id="d7904-126">Set this property to **Absent** to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="d7904-127">将其设置为 **Present** 可确保已安装包。</span><span class="sxs-lookup"><span data-stu-id="d7904-127">Set it to **Present** to ensure the package is installed.</span></span> <span data-ttu-id="d7904-128">**Ensure** 是 **WindowsPackageCab** 资源上的必需属性。</span><span class="sxs-lookup"><span data-stu-id="d7904-128">**Ensure** is a required property on the **WindowsPackageCab** resource.</span></span> |
|<span data-ttu-id="d7904-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="d7904-129">PsDscRunAsCredential</span></span> |<span data-ttu-id="d7904-130">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="d7904-130">Sets the credential for running the entire resource as.</span></span> |

## <a name="example"></a><span data-ttu-id="d7904-131">示例</span><span class="sxs-lookup"><span data-stu-id="d7904-131">Example</span></span>

<span data-ttu-id="d7904-132">下面的示例配置需要使用输入参数，并确保安装了 `$Name` 参数指定的.cab 文件。</span><span class="sxs-lookup"><span data-stu-id="d7904-132">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```
