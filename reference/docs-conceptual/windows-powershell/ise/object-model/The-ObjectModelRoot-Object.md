---
ms.date: 08/25/2017
title: ObjectModelRoot 对象
description: PowerShell ISE 中的主体根对象（$psISE 对象）是 Microsoft.PowerShell.Host.ISE.ObjectModelRoot 类的实例。 本主题介绍 ObjectModelRoot 对象的属性。
ms.openlocfilehash: c8ae703c2663256ca037090fd3b1eb239cfc431a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660950"
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="0a803-104">ObjectModelRoot 对象</span><span class="sxs-lookup"><span data-stu-id="0a803-104">The ObjectModelRoot Object</span></span>

<span data-ttu-id="0a803-105">Windows PowerShell&reg; 集成脚本环境 (ISE) 中的主体根对象（`$psISE` 对象）是 Microsoft.PowerShell.Host.ISE.ObjectModelRoot 类的实例。</span><span class="sxs-lookup"><span data-stu-id="0a803-105">The `$psISE` object, which is the principal root object in Windows PowerShell&reg; Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span> <span data-ttu-id="0a803-106">本主题介绍 **ObjectModelRoot** 对象的属性。</span><span class="sxs-lookup"><span data-stu-id="0a803-106">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="0a803-107">属性</span><span class="sxs-lookup"><span data-stu-id="0a803-107">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="0a803-108">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="0a803-108">CurrentFile</span></span>

> <span data-ttu-id="0a803-109">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="0a803-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="0a803-110">只读属性，可获取与该主机对象相关联的当前具有焦点的文件。</span><span class="sxs-lookup"><span data-stu-id="0a803-110">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="0a803-111">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="0a803-111">CurrentPowerShellTab</span></span>

> <span data-ttu-id="0a803-112">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="0a803-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="0a803-113">只读属性，可获取具有焦点的 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="0a803-113">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="0a803-114">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="0a803-114">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="0a803-115">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="0a803-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="0a803-116">只读属性，可获取位于编辑器底部水平工具窗格中、当前可见的 Windows PowerShell ISE 加载项工具。</span><span class="sxs-lookup"><span data-stu-id="0a803-116">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="0a803-117">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="0a803-117">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="0a803-118">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="0a803-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="0a803-119">只读属性，可获取位于编辑器右侧竖直工具窗格中、当前可见的 Windows PowerShell ISE 加载项工具。</span><span class="sxs-lookup"><span data-stu-id="0a803-119">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="0a803-120">选项</span><span class="sxs-lookup"><span data-stu-id="0a803-120">Options</span></span>

> <span data-ttu-id="0a803-121">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="0a803-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="0a803-122">只读属性，可获取可以更改 Windows PowerShell ISE 中设置的各种选项。</span><span class="sxs-lookup"><span data-stu-id="0a803-122">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="0a803-123">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="0a803-123">PowerShellTabs</span></span>

> <span data-ttu-id="0a803-124">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="0a803-124">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="0a803-125">只读属性，可获取 Windows PowerShell ISE 中打开的 PowerShell 选项卡的集合。</span><span class="sxs-lookup"><span data-stu-id="0a803-125">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="0a803-126">默认情况下，此对象包含一个 PowerShell 选项卡。但是，可以将更多 PowerShell 选项卡添加到此对象中，方法是通过使用脚本或者使用 Windows PowerShell ISE 中的菜单。</span><span class="sxs-lookup"><span data-stu-id="0a803-126">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a803-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0a803-127">See Also</span></span>

- [<span data-ttu-id="0a803-128">Windows PowerShell ISE 脚本对象模型的用途</span><span class="sxs-lookup"><span data-stu-id="0a803-128">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="0a803-129">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="0a803-129">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
