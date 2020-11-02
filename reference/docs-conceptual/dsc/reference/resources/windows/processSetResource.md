---
ms.date: 07/16/2020
ms.topic: reference
title: DSC ProcessSet 资源
description: DSC ProcessSet 资源
ms.openlocfilehash: 3e09c8c7b4ca7d8e95b36f9d4c20c2a85abad9dd
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142559"
---
# <a name="dsc-processset-resource"></a><span data-ttu-id="fa4eb-103">DSC ProcessSet 资源</span><span class="sxs-lookup"><span data-stu-id="fa4eb-103">DSC ProcessSet Resource</span></span>

> <span data-ttu-id="fa4eb-104">适用于：Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="fa4eb-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="fa4eb-105">Windows PowerShell Desired State Configuration (DSC) 中的 **ProcessSet** 资源提供了用于在目标节点上配置进程的机制。</span><span class="sxs-lookup"><span data-stu-id="fa4eb-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="fa4eb-106">语法</span><span class="sxs-lookup"><span data-stu-id="fa4eb-106">Syntax</span></span>

```Syntax
ProcessSet [string] #ResourceName
{
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="fa4eb-107">属性</span><span class="sxs-lookup"><span data-stu-id="fa4eb-107">Properties</span></span>

|<span data-ttu-id="fa4eb-108">properties</span><span class="sxs-lookup"><span data-stu-id="fa4eb-108">Property</span></span> |<span data-ttu-id="fa4eb-109">说明</span><span class="sxs-lookup"><span data-stu-id="fa4eb-109">Description</span></span> |
|---|---|
|<span data-ttu-id="fa4eb-110">路径</span><span class="sxs-lookup"><span data-stu-id="fa4eb-110">Path</span></span> |<span data-ttu-id="fa4eb-111">进程可执行文件的路径。</span><span class="sxs-lookup"><span data-stu-id="fa4eb-111">The path to the process executable.</span></span> <span data-ttu-id="fa4eb-112">如果这些是可执行文件的名称（不是完全限定的路径），则 DSC 资源会搜索环境 `$env:Path` 变量以查找文件。</span><span class="sxs-lookup"><span data-stu-id="fa4eb-112">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment `$env:Path` variable to find the files.</span></span> <span data-ttu-id="fa4eb-113">如果此属性的值是完全限定的路径，则 DSC 不使用 `$env:Path` 环境变量查找文件，并且会在不存在任何路径时引发错误。</span><span class="sxs-lookup"><span data-stu-id="fa4eb-113">If the values of this property are fully qualified paths, DSC will not use the `$env:Path` environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="fa4eb-114">不允许使用相对路径。</span><span class="sxs-lookup"><span data-stu-id="fa4eb-114">Relative paths are not allowed.</span></span> |
|<span data-ttu-id="fa4eb-115">凭据</span><span class="sxs-lookup"><span data-stu-id="fa4eb-115">Credential</span></span> |<span data-ttu-id="fa4eb-116">指示启动进程的凭据。</span><span class="sxs-lookup"><span data-stu-id="fa4eb-116">Indicates the credentials for starting the process.</span></span> |
|<span data-ttu-id="fa4eb-117">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="fa4eb-117">StandardErrorPath</span></span> |<span data-ttu-id="fa4eb-118">进程写入标准错误的路径。</span><span class="sxs-lookup"><span data-stu-id="fa4eb-118">The path to which the processes write standard error.</span></span> <span data-ttu-id="fa4eb-119">将覆盖任何现有文件。</span><span class="sxs-lookup"><span data-stu-id="fa4eb-119">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="fa4eb-120">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="fa4eb-120">StandardInputPath</span></span> |<span data-ttu-id="fa4eb-121">进程从中接收标准输入的流。</span><span class="sxs-lookup"><span data-stu-id="fa4eb-121">The stream from which the process receives standard input.</span></span> |
|<span data-ttu-id="fa4eb-122">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="fa4eb-122">StandardOutputPath</span></span> |<span data-ttu-id="fa4eb-123">进程写入标准输出的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="fa4eb-123">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="fa4eb-124">将覆盖任何现有文件。</span><span class="sxs-lookup"><span data-stu-id="fa4eb-124">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="fa4eb-125">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="fa4eb-125">WorkingDirectory</span></span> |<span data-ttu-id="fa4eb-126">用作进程当前工作目录的位置。</span><span class="sxs-lookup"><span data-stu-id="fa4eb-126">The location used as the current working directory for the processes.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="fa4eb-127">公共属性</span><span class="sxs-lookup"><span data-stu-id="fa4eb-127">Common properties</span></span>

|<span data-ttu-id="fa4eb-128">properties</span><span class="sxs-lookup"><span data-stu-id="fa4eb-128">Property</span></span> |<span data-ttu-id="fa4eb-129">说明</span><span class="sxs-lookup"><span data-stu-id="fa4eb-129">Description</span></span> |
|---|---|
|<span data-ttu-id="fa4eb-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="fa4eb-130">DependsOn</span></span> |<span data-ttu-id="fa4eb-131">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="fa4eb-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="fa4eb-132">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="fa4eb-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="fa4eb-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="fa4eb-133">Ensure</span></span> |<span data-ttu-id="fa4eb-134">指定进程是否存在。</span><span class="sxs-lookup"><span data-stu-id="fa4eb-134">Specifies whether the processes exists.</span></span> <span data-ttu-id="fa4eb-135">将此属性设置为 **Present** 可确保进程存在。</span><span class="sxs-lookup"><span data-stu-id="fa4eb-135">Set this property to **Present** to ensure that the process exists.</span></span> <span data-ttu-id="fa4eb-136">否则，将其设置为 **Absent** 。</span><span class="sxs-lookup"><span data-stu-id="fa4eb-136">Otherwise, set it to **Absent** .</span></span> <span data-ttu-id="fa4eb-137">默认值为 **Present** 。</span><span class="sxs-lookup"><span data-stu-id="fa4eb-137">The default value is **Present** .</span></span> |
|<span data-ttu-id="fa4eb-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="fa4eb-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="fa4eb-139">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="fa4eb-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="fa4eb-140">在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="fa4eb-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="fa4eb-141">有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="fa4eb-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>
