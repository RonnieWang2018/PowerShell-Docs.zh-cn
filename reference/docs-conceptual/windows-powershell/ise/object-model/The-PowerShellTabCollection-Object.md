---
ms.date: 06/05/2017
title: PowerShellTabCollection 对象
description: PowerShellTab 集合对象是 PowerShellTab 对象的集合。 每个 PowerShellTab 对象充当一个单独的运行时环境。
ms.openlocfilehash: 60f8001f096b50bd8433a5685f1f70a350f07f61
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658271"
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="34ee9-104">PowerShellTabCollection 对象</span><span class="sxs-lookup"><span data-stu-id="34ee9-104">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="34ee9-105">**PowerShellTab** 集合对象是 **PowerShellTab** 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="34ee9-105">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="34ee9-106">每个 **PowerShellTab** 对象充当一个单独的运行时环境。</span><span class="sxs-lookup"><span data-stu-id="34ee9-106">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="34ee9-107">它是 Microsoft.PowerShell.Host.ISE.PowerShellTabs 类的实例。</span><span class="sxs-lookup"><span data-stu-id="34ee9-107">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="34ee9-108">`$psISE.PowerShellTabs` 对象就是一个示例。</span><span class="sxs-lookup"><span data-stu-id="34ee9-108">An example is the `$psISE.PowerShellTabs` object.</span></span>

## <a name="methods"></a><span data-ttu-id="34ee9-109">方法</span><span class="sxs-lookup"><span data-stu-id="34ee9-109">Methods</span></span>

### <a name="add"></a><span data-ttu-id="34ee9-110">添加\(\)</span><span class="sxs-lookup"><span data-stu-id="34ee9-110">Add\(\)</span></span>

<span data-ttu-id="34ee9-111">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="34ee9-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="34ee9-112">向集合中添加一个新的 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="34ee9-112">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="34ee9-113">它将返回新添加的选项卡。</span><span class="sxs-lookup"><span data-stu-id="34ee9-113">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="34ee9-114">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="34ee9-114">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="34ee9-115">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="34ee9-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="34ee9-116">删除由 **psTab** 参数指定的选项卡。</span><span class="sxs-lookup"><span data-stu-id="34ee9-116">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="34ee9-117">**psTab** 要删除的 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="34ee9-117">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="34ee9-118">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="34ee9-118">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="34ee9-119">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="34ee9-119">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="34ee9-120">选择由 **psTab** 参数指定的 PowerShell 选项卡，以使它当前是处于活动状态的 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="34ee9-120">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="34ee9-121">**psTab** 要选择的 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="34ee9-121">**psTab** The PowerShell tab to select.</span></span>

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a><span data-ttu-id="34ee9-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="34ee9-122">See Also</span></span>

- [<span data-ttu-id="34ee9-123">PowerShellTab 对象</span><span class="sxs-lookup"><span data-stu-id="34ee9-123">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="34ee9-124">Windows PowerShell ISE 脚本对象模型的用途</span><span class="sxs-lookup"><span data-stu-id="34ee9-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="34ee9-125">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="34ee9-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
