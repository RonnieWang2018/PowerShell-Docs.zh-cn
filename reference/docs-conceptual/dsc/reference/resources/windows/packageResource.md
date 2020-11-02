---
ms.date: 07/16/2020
ms.topic: reference
title: DSC Package 资源
description: DSC Package 资源
ms.openlocfilehash: 4bcc6dc68a37ebe434e30339452cd7269f984ae9
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142865"
---
# <a name="dsc-package-resource"></a><span data-ttu-id="d8003-103">DSC Package 资源</span><span class="sxs-lookup"><span data-stu-id="d8003-103">DSC Package Resource</span></span>

> <span data-ttu-id="d8003-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="d8003-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="d8003-105">Windows PowerShell Desired State Configuration (DSC) 中的 **Package** 资源提供了在目标节点上安装或卸载程序包（如 Windows Installer 和 setup.exe 程序包）的机制。</span><span class="sxs-lookup"><span data-stu-id="d8003-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="d8003-106">语法</span><span class="sxs-lookup"><span data-stu-id="d8003-106">Syntax</span></span>

```Syntax
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ ReturnCode = [UInt32[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="d8003-107">属性</span><span class="sxs-lookup"><span data-stu-id="d8003-107">Properties</span></span>

|<span data-ttu-id="d8003-108">properties</span><span class="sxs-lookup"><span data-stu-id="d8003-108">Property</span></span> |<span data-ttu-id="d8003-109">说明</span><span class="sxs-lookup"><span data-stu-id="d8003-109">Description</span></span> |
|---|---|
|<span data-ttu-id="d8003-110">名称</span><span class="sxs-lookup"><span data-stu-id="d8003-110">Name</span></span> |<span data-ttu-id="d8003-111">指示要确保其特定状态的程序包的名称。</span><span class="sxs-lookup"><span data-stu-id="d8003-111">Indicates the name of the package for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="d8003-112">路径</span><span class="sxs-lookup"><span data-stu-id="d8003-112">Path</span></span> |<span data-ttu-id="d8003-113">指示程序包所在的路径。</span><span class="sxs-lookup"><span data-stu-id="d8003-113">Indicates the path where the package resides.</span></span> |
|<span data-ttu-id="d8003-114">ProductId</span><span class="sxs-lookup"><span data-stu-id="d8003-114">ProductId</span></span> |<span data-ttu-id="d8003-115">指示唯一标识程序包的产品 ID。</span><span class="sxs-lookup"><span data-stu-id="d8003-115">Indicates the product ID that uniquely identifies the package.</span></span> |
|<span data-ttu-id="d8003-116">参数</span><span class="sxs-lookup"><span data-stu-id="d8003-116">Arguments</span></span> |<span data-ttu-id="d8003-117">列出按照原样传输到程序包的参数字符串。</span><span class="sxs-lookup"><span data-stu-id="d8003-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span> |
|<span data-ttu-id="d8003-118">凭据</span><span class="sxs-lookup"><span data-stu-id="d8003-118">Credential</span></span> |<span data-ttu-id="d8003-119">提供远程源上程序包的访问权限。</span><span class="sxs-lookup"><span data-stu-id="d8003-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="d8003-120">此属性不用于安装程序包。</span><span class="sxs-lookup"><span data-stu-id="d8003-120">This property is not used to install the package.</span></span> <span data-ttu-id="d8003-121">程序包始终安装在本地系统上。</span><span class="sxs-lookup"><span data-stu-id="d8003-121">The package is always installed on the local system.</span></span> |
|<span data-ttu-id="d8003-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="d8003-122">LogPath</span></span> |<span data-ttu-id="d8003-123">指示你希望提供程序用于保存安装或卸载程序包的日志文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="d8003-123">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span> |
|<span data-ttu-id="d8003-124">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="d8003-124">ReturnCode</span></span> |<span data-ttu-id="d8003-125">指示预期的返回代码。</span><span class="sxs-lookup"><span data-stu-id="d8003-125">Indicates the expected return code.</span></span> <span data-ttu-id="d8003-126">如果实际返回代码与此处提供的预期值不匹配，则配置将返回错误。</span><span class="sxs-lookup"><span data-stu-id="d8003-126">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="d8003-127">公共属性</span><span class="sxs-lookup"><span data-stu-id="d8003-127">Common properties</span></span>

|<span data-ttu-id="d8003-128">properties</span><span class="sxs-lookup"><span data-stu-id="d8003-128">Property</span></span> |<span data-ttu-id="d8003-129">说明</span><span class="sxs-lookup"><span data-stu-id="d8003-129">Description</span></span> |
|---|---|
|<span data-ttu-id="d8003-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d8003-130">DependsOn</span></span> |<span data-ttu-id="d8003-131">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="d8003-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d8003-132">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="d8003-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="d8003-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="d8003-133">Ensure</span></span> |<span data-ttu-id="d8003-134">指示程序包是否已安装。</span><span class="sxs-lookup"><span data-stu-id="d8003-134">Indicates if the package is installed.</span></span> <span data-ttu-id="d8003-135">将此属性设置为 **Absent** 可确保未安装包（如果已安装，则卸载包）。</span><span class="sxs-lookup"><span data-stu-id="d8003-135">Set this property to **Absent** to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="d8003-136">将其设置为 **Present** 可确保已安装包。</span><span class="sxs-lookup"><span data-stu-id="d8003-136">Set it to **Present** to ensure the package is installed.</span></span> <span data-ttu-id="d8003-137">默认值为 **Present** 。</span><span class="sxs-lookup"><span data-stu-id="d8003-137">The default value is **Present** .</span></span> |
|<span data-ttu-id="d8003-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="d8003-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="d8003-139">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="d8003-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="d8003-140">在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="d8003-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="d8003-141">有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="d8003-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="d8003-142">示例</span><span class="sxs-lookup"><span data-stu-id="d8003-142">Example</span></span>

<span data-ttu-id="d8003-143">此示例将运行位于指定路径且具有指定产品 ID 的 .msi 安装程序。</span><span class="sxs-lookup"><span data-stu-id="d8003-143">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```
