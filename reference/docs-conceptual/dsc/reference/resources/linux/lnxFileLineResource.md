---
ms.date: 07/17/2020
ms.topic: reference
title: 适用于 Linux nxFileLine 资源的 DSC
description: 适用于 Linux nxFileLine 资源的 DSC
ms.openlocfilehash: b342021176e4d8584afec82173f31bf5191ad264
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644752"
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="14418-103">适用于 Linux nxFileLine 资源的 DSC</span><span class="sxs-lookup"><span data-stu-id="14418-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="14418-104">PowerShell Desired State Configuration (DSC) 中的 nxFileLine  资源提供了管理 Linux 节点上配置文件中的行的机制。</span><span class="sxs-lookup"><span data-stu-id="14418-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="14418-105">语法</span><span class="sxs-lookup"><span data-stu-id="14418-105">Syntax</span></span>

```Syntax
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="14418-106">属性</span><span class="sxs-lookup"><span data-stu-id="14418-106">Properties</span></span>

|<span data-ttu-id="14418-107">properties</span><span class="sxs-lookup"><span data-stu-id="14418-107">Property</span></span> |<span data-ttu-id="14418-108">说明</span><span class="sxs-lookup"><span data-stu-id="14418-108">Description</span></span> |
|---|---|
|<span data-ttu-id="14418-109">文件路径</span><span class="sxs-lookup"><span data-stu-id="14418-109">FilePath</span></span> |<span data-ttu-id="14418-110">要管理其在目标节点上的行的文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="14418-110">The full path to the file to manage lines in on the target node.</span></span> |
|<span data-ttu-id="14418-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="14418-111">ContainsLine</span></span> |<span data-ttu-id="14418-112">要确保存在于文件中的行。</span><span class="sxs-lookup"><span data-stu-id="14418-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="14418-113">如果此行不存在于文件中，则将其追加到该文件中。</span><span class="sxs-lookup"><span data-stu-id="14418-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="14418-114">ContainsLine  为必填项，但是如不需要，则可将其设置为空字符串 (`ContainsLine = ""`)。</span><span class="sxs-lookup"><span data-stu-id="14418-114">**ContainsLine** is mandatory, but can be set to an empty string (`ContainsLine = ""`) if it is not needed.</span></span> |
|<span data-ttu-id="14418-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="14418-115">DoesNotContainPattern</span></span> |<span data-ttu-id="14418-116">不应存在于此文件中的行的正则表达式模式。</span><span class="sxs-lookup"><span data-stu-id="14418-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="14418-117">将从文件中删除任何存在于此文件中并与正则表达式相匹配的行。</span><span class="sxs-lookup"><span data-stu-id="14418-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="14418-118">公共属性</span><span class="sxs-lookup"><span data-stu-id="14418-118">Common properties</span></span>

|<span data-ttu-id="14418-119">properties</span><span class="sxs-lookup"><span data-stu-id="14418-119">Property</span></span> |<span data-ttu-id="14418-120">说明</span><span class="sxs-lookup"><span data-stu-id="14418-120">Description</span></span> |
|---|---|
|<span data-ttu-id="14418-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="14418-121">DependsOn</span></span> |<span data-ttu-id="14418-122">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="14418-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="14418-123">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="14418-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="example"></a><span data-ttu-id="14418-124">示例</span><span class="sxs-lookup"><span data-stu-id="14418-124">Example</span></span>

<span data-ttu-id="14418-125">此示例演示如何使用 **nxFileLine** 资源来配置 `/etc/sudoers` 文件，从而确保将用户 monuser 配置为“not requiretty”。</span><span class="sxs-lookup"><span data-stu-id="14418-125">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = "/etc/sudoers"
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```
