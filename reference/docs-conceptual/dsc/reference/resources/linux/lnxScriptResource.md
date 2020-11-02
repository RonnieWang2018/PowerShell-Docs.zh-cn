---
ms.date: 07/17/2020
ms.topic: reference
title: 适用于 Linux 的 DSC nxScript 资源
description: 适用于 Linux 的 DSC nxScript 资源
ms.openlocfilehash: c92d7ac76323d39167512734ef743c299857c9a6
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648800"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="2035f-103">适用于 Linux 的 DSC nxScript 资源</span><span class="sxs-lookup"><span data-stu-id="2035f-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="2035f-104">PowerShell Desired State Configuration (DSC) 中的 **nxScript** 资源提供了在 Linux 节点上运行 Linux 脚本的机制。</span><span class="sxs-lookup"><span data-stu-id="2035f-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="2035f-105">语法</span><span class="sxs-lookup"><span data-stu-id="2035f-105">Syntax</span></span>

```Syntax
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="2035f-106">属性</span><span class="sxs-lookup"><span data-stu-id="2035f-106">Properties</span></span>

|<span data-ttu-id="2035f-107">properties</span><span class="sxs-lookup"><span data-stu-id="2035f-107">Property</span></span> |<span data-ttu-id="2035f-108">说明</span><span class="sxs-lookup"><span data-stu-id="2035f-108">Description</span></span> |
|---|---|
|<span data-ttu-id="2035f-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="2035f-109">GetScript</span></span> |<span data-ttu-id="2035f-110">提供用于返回计算机当前状态的脚本。</span><span class="sxs-lookup"><span data-stu-id="2035f-110">Provides a script to return current status of the machine.</span></span> <span data-ttu-id="2035f-111">调用 [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) 脚本时，将运行此脚本。</span><span class="sxs-lookup"><span data-stu-id="2035f-111">This script runs when you invoke the [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="2035f-112">该脚本必须以 shebang 开头，如 `#!/bin/bash`。</span><span class="sxs-lookup"><span data-stu-id="2035f-112">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="2035f-113">SetScript</span><span class="sxs-lookup"><span data-stu-id="2035f-113">SetScript</span></span> |<span data-ttu-id="2035f-114">提供将计算机置于正确状态的脚本。</span><span class="sxs-lookup"><span data-stu-id="2035f-114">Provides a script that puts the machine in the correct state.</span></span> <span data-ttu-id="2035f-115">调用 [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) 脚本时，将首先运行 TestScript  。</span><span class="sxs-lookup"><span data-stu-id="2035f-115">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, the **TestScript** runs first.</span></span> <span data-ttu-id="2035f-116">如果 **TestScript** 块返回非 0 退出代码，则将运行 **SetScript** 块。</span><span class="sxs-lookup"><span data-stu-id="2035f-116">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="2035f-117">如果 **TestScript** 返回退出代码 0，则将不运行 **SetScript** 。</span><span class="sxs-lookup"><span data-stu-id="2035f-117">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="2035f-118">该脚本必须以 shebang 开头，如 `#!/bin/bash`。</span><span class="sxs-lookup"><span data-stu-id="2035f-118">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="2035f-119">TestScript</span><span class="sxs-lookup"><span data-stu-id="2035f-119">TestScript</span></span> |<span data-ttu-id="2035f-120">提供一个脚本，用于评估节点当前是否处于正确状态。</span><span class="sxs-lookup"><span data-stu-id="2035f-120">Provides a script that evaluates whether the node is currently in the correct state.</span></span> <span data-ttu-id="2035f-121">调用 [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) 脚本时，将首先运行此脚本。</span><span class="sxs-lookup"><span data-stu-id="2035f-121">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, this script runs.</span></span> <span data-ttu-id="2035f-122">如果它返回非 0 退出代码，则将运行 **SetScript** 。</span><span class="sxs-lookup"><span data-stu-id="2035f-122">If it returns an exit code other than 0, the **SetScript** will run.</span></span> <span data-ttu-id="2035f-123">如果它返回退出代码 0，则将不运行 **SetScript** 。</span><span class="sxs-lookup"><span data-stu-id="2035f-123">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="2035f-124">调用 [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) 脚本时，也会运行 TestScript。</span><span class="sxs-lookup"><span data-stu-id="2035f-124">The **TestScript** also runs when you invoke the [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="2035f-125">但是，在这种情况下，无论从 **TestScript** 返回何种退出代码，都不会运行 **SetScript** 。</span><span class="sxs-lookup"><span data-stu-id="2035f-125">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript** .</span></span> <span data-ttu-id="2035f-126">如果实际配置与当前所需状态配置相匹配，则 TestScript  必须包含内容且必须返回退出代码 0；如两者不匹配，则返回非 0 退出代码。</span><span class="sxs-lookup"><span data-stu-id="2035f-126">The **TestScript** must contain content and must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="2035f-127">当前所需状态配置是在使用 DSC 的节点上执行的最后一个配置。</span><span class="sxs-lookup"><span data-stu-id="2035f-127">The current desired state configuration is the last configuration enacted on the node that is using DSC.</span></span> <span data-ttu-id="2035f-128">该脚本必须以 shebang 开头，如 `#!/bin/bash`。</span><span class="sxs-lookup"><span data-stu-id="2035f-128">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="2035f-129">用户</span><span class="sxs-lookup"><span data-stu-id="2035f-129">User</span></span> |<span data-ttu-id="2035f-130">将该脚本作为此用户运行。</span><span class="sxs-lookup"><span data-stu-id="2035f-130">The user to run the script as.</span></span> |
|<span data-ttu-id="2035f-131">组</span><span class="sxs-lookup"><span data-stu-id="2035f-131">Group</span></span> |<span data-ttu-id="2035f-132">将该脚本作为此组运行。</span><span class="sxs-lookup"><span data-stu-id="2035f-132">The group to run the script as.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="2035f-133">公共属性</span><span class="sxs-lookup"><span data-stu-id="2035f-133">Common properties</span></span>

|<span data-ttu-id="2035f-134">properties</span><span class="sxs-lookup"><span data-stu-id="2035f-134">Property</span></span> |<span data-ttu-id="2035f-135">说明</span><span class="sxs-lookup"><span data-stu-id="2035f-135">Description</span></span> |
|---|---|
|<span data-ttu-id="2035f-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="2035f-136">DependsOn</span></span> |<span data-ttu-id="2035f-137">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="2035f-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2035f-138">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="2035f-138">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="example"></a><span data-ttu-id="2035f-139">示例</span><span class="sxs-lookup"><span data-stu-id="2035f-139">Example</span></span>

<span data-ttu-id="2035f-140">以下示例演示了如何使用 **nxScript** 资源进行其他配置管理。</span><span class="sxs-lookup"><span data-stu-id="2035f-140">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxScript KeepDirEmpty {

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
    }
}
```
