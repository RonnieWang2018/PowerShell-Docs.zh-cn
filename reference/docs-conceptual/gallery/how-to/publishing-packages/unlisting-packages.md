---
ms.date: 06/12/2017
title: 取消列出包
description: PowerShell 库不支持用户永久删除其包。 这让其他人能够依赖你的包而无需担心将来可能产生的中断。
ms.openlocfilehash: 738167011f64b5174df3504c8e1d06146f4c7db5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662418"
---
# <a name="unlisting-packages"></a><span data-ttu-id="cfbfe-104">取消列出包</span><span class="sxs-lookup"><span data-stu-id="cfbfe-104">Unlisting Packages</span></span>

<span data-ttu-id="cfbfe-105">为什么未显示从 PowerShell 库删除包的选项？</span><span class="sxs-lookup"><span data-stu-id="cfbfe-105">**Why is removing a package from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="cfbfe-106">PowerShell 库不支持用户永久删除其包。</span><span class="sxs-lookup"><span data-stu-id="cfbfe-106">The PowerShell Gallery does not support users permanently deleting their packages.</span></span> <span data-ttu-id="cfbfe-107">这让其他人能够依赖你的包而无需担心将来可能产生的中断。</span><span class="sxs-lookup"><span data-stu-id="cfbfe-107">This enables others to take dependencies on your packages without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="cfbfe-108">例如，如果 Pester 模块依赖 Azure 模块，而 Azure 模块从库中删除，那么用户将不能使用 Pester 模块。</span><span class="sxs-lookup"><span data-stu-id="cfbfe-108">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then users can no longer use the Pester module.</span></span>

<span data-ttu-id="cfbfe-109">可以取消列出包，但不能删除包。</span><span class="sxs-lookup"><span data-stu-id="cfbfe-109">Instead of removing a package you can unlist it.</span></span>

<span data-ttu-id="cfbfe-110">在 PowerShell 库中取消列出包的作用是什么？</span><span class="sxs-lookup"><span data-stu-id="cfbfe-110">**What does unlisting a package on PowerShell Gallery do?**</span></span>

<span data-ttu-id="cfbfe-111">在 PowerShell 库中取消列出包（例如模块或脚本）会将其从“包”选项卡中移除。此外，使用搜索栏将无法发现取消列出的包。</span><span class="sxs-lookup"><span data-stu-id="cfbfe-111">Unlisting a package such as a module or script in the PowerShell Gallery removes it from the Packages tab. In addition, unlisted packages will not be discoverable using the search bar.</span></span> <span data-ttu-id="cfbfe-112">下载取消列出的包的唯一方法是指定包的确切名称和版本。</span><span class="sxs-lookup"><span data-stu-id="cfbfe-112">The only way to download an unlisted package is to specify the exact name and version of the package.</span></span> <span data-ttu-id="cfbfe-113">因此，取消列出的包将不会中断依赖它的其他模块或脚本。</span><span class="sxs-lookup"><span data-stu-id="cfbfe-113">Because of this, the unlisting of a package will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="cfbfe-114">若要取消列出包，可访问包详细信息页，选择“删除模块”。</span><span class="sxs-lookup"><span data-stu-id="cfbfe-114">To unlist your package, visit the package details page and select 'Delete Module'.</span></span> <span data-ttu-id="cfbfe-115">取消选中“列出”复选框，并选择“保存”。</span><span class="sxs-lookup"><span data-stu-id="cfbfe-115">Uncheck the 'Listed' checkbox, and select 'Save'.</span></span>

<span data-ttu-id="cfbfe-116">**如何移除包？**</span><span class="sxs-lookup"><span data-stu-id="cfbfe-116">**How can I remove a package?**</span></span>

<span data-ttu-id="cfbfe-117">如果遇到有必要删除包的情况，请与 PowerShell 库管理员联系。</span><span class="sxs-lookup"><span data-stu-id="cfbfe-117">If you experience a scenario where package deletion is necessary, contact the PowerShell Gallery Administrators.</span></span> <span data-ttu-id="cfbfe-118">正当的删除情况包括：</span><span class="sxs-lookup"><span data-stu-id="cfbfe-118">Valid deletion scenarios are:</span></span>

- <span data-ttu-id="cfbfe-119">侵犯版权问题。</span><span class="sxs-lookup"><span data-stu-id="cfbfe-119">Issues of copyright infringement.</span></span>
- <span data-ttu-id="cfbfe-120">包包含可能有害的内容。</span><span class="sxs-lookup"><span data-stu-id="cfbfe-120">Package contains potentially harmful content.</span></span>
- <span data-ttu-id="cfbfe-121">包包含敏感数据。</span><span class="sxs-lookup"><span data-stu-id="cfbfe-121">Package contains sensitive data.</span></span>

<span data-ttu-id="cfbfe-122">若要向 PowerShell 库管理员提交删除包请求，请访问包的详细信息页并选择“联系支持人员”。</span><span class="sxs-lookup"><span data-stu-id="cfbfe-122">To submit a Delete Package Request to the PowerShell Gallery Administrators, visit your package's detail page and select Contact Support.</span></span>
