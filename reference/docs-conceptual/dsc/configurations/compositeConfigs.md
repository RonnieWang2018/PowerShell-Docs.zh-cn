---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 嵌套配置
description: DSC 允许你通过在其他配置中嵌套配置来创建复合配置。
ms.openlocfilehash: d7a81cb9673126e92e9185aacf19c5c7c17da8ca
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667413"
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="6ce3a-104">嵌套 DSC 配置</span><span class="sxs-lookup"><span data-stu-id="6ce3a-104">Nesting DSC configurations</span></span>

<span data-ttu-id="6ce3a-105">嵌套配置（也称为复合配置）是在其他配置中进行调用的配置，就像它是资源一样。</span><span class="sxs-lookup"><span data-stu-id="6ce3a-105">A nested configuration (also called composite configuration) is a configuration that's called within another configuration as if it were a resource.</span></span> <span data-ttu-id="6ce3a-106">两个配置必须在同一文件中定义。</span><span class="sxs-lookup"><span data-stu-id="6ce3a-106">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="6ce3a-107">让我们看一个简单的示例：</span><span class="sxs-lookup"><span data-stu-id="6ce3a-107">Let's look at a simple example:</span></span>

```powershell
Configuration FileConfig
{
    param (
        [Parameter(Mandatory = $true)]
        [String] $CopyFrom,

        [Parameter(Mandatory = $true)]
        [String] $CopyTo
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    File FileTest
    {
        SourcePath = $CopyFrom
        DestinationPath = $CopyTo
        Ensure = 'Present'
    }
}

Configuration NestedFileConfig
{
    Node localhost
    {
        FileConfig NestedConfig
        {
            CopyFrom = 'C:\Test\TestFile.txt'
            CopyTo = 'C:\Test2'
        }
    }
}
```

<span data-ttu-id="6ce3a-108">在这个示例中，`FileConfig` 采用两个强制参数 CopyFrom 和 CopyTo，它们在 `File` 资源块中用作 SourcePath 和 DestinationPath 属性的值。</span><span class="sxs-lookup"><span data-stu-id="6ce3a-108">In this example, `FileConfig` takes two mandatory parameters, **CopyFrom** and **CopyTo** , which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span> <span data-ttu-id="6ce3a-109">`NestedConfig` 配置调用 `FileConfig`，就像它是资源一样。</span><span class="sxs-lookup"><span data-stu-id="6ce3a-109">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span> <span data-ttu-id="6ce3a-110">`NestedConfig` 资源块中的属性（ **CopyFrom** 和 **CopyTo** ）是 `FileConfig` 配置的参数。</span><span class="sxs-lookup"><span data-stu-id="6ce3a-110">The properties in the `NestedConfig` resource block ( **CopyFrom** and **CopyTo** ) are the parameters of the `FileConfig` configuration.</span></span>

<span data-ttu-id="6ce3a-111">DSC 当前不支持嵌套配置中的嵌套配置。</span><span class="sxs-lookup"><span data-stu-id="6ce3a-111">DSC doesn't currently support nesting configurations within nested configurations.</span></span> <span data-ttu-id="6ce3a-112">只能将配置嵌套一层。</span><span class="sxs-lookup"><span data-stu-id="6ce3a-112">You can only nest a configuration one layer deep.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ce3a-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6ce3a-113">See Also</span></span>

- [<span data-ttu-id="6ce3a-114">复合资源--将 DSC 配置用作资源</span><span class="sxs-lookup"><span data-stu-id="6ce3a-114">Composite resources--Using a DSC configuration as a resource</span></span>](../resources/authoringResourceComposite.md)
