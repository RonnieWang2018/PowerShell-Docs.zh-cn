---
ms.date: 10/11/2019
keywords: dsc,powershell,配置,安装程序
title: 适用于决策者的 Desired State Configuration 概述
description: 本文档描述了使用 PowerShell Desired State Configuration (DSC) 的商业利益，而非技术指南。
ms.openlocfilehash: fc28c9290c993131fc7bf2046eb64b144d3da609
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654142"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a><span data-ttu-id="8a71d-104">适用于决策者的 Desired State Configuration 概述</span><span class="sxs-lookup"><span data-stu-id="8a71d-104">Desired State Configuration overview for decision makers</span></span>

<span data-ttu-id="8a71d-105">本文档描述了使用 PowerShell Desired State Configuration (DSC) 的商业利益，而非技术指南。</span><span class="sxs-lookup"><span data-stu-id="8a71d-105">This document describes the business benefits of using PowerShell Desired State Configuration (DSC), and isn't a technical guide.</span></span>

## <a name="what-is-dsc"></a><span data-ttu-id="8a71d-106">什么是 DSC？</span><span class="sxs-lookup"><span data-stu-id="8a71d-106">What Is DSC?</span></span>

<span data-ttu-id="8a71d-107">PowerShell DSC 是基于开放标准的内置于 Windows 中的配置管理平台。</span><span class="sxs-lookup"><span data-stu-id="8a71d-107">PowerShell DSC is a configuration management platform built into Windows that is based on open standards.</span></span> <span data-ttu-id="8a71d-108">DSC 足够灵活，能够在部署生命周期的各个阶段（开发、测试、预生产、生产）及扩展期间可靠而一致地运转。</span><span class="sxs-lookup"><span data-stu-id="8a71d-108">DSC is flexible enough to function reliably and consistently in each stage of the deployment lifecycle (development, test, pre-production, production), and during scale-out.</span></span>

<span data-ttu-id="8a71d-109">DSC 以[配置](../configurations/configurations.md)为中心。</span><span class="sxs-lookup"><span data-stu-id="8a71d-109">DSC centers around [configurations](../configurations/configurations.md).</span></span> <span data-ttu-id="8a71d-110">配置是 PowerShell 脚本，它描述了由具有特定特征的计算机或节点组成的环境。</span><span class="sxs-lookup"><span data-stu-id="8a71d-110">A configuration is PowerShell script that describes an environment made up of computers, or nodes, with specific characteristics.</span></span> <span data-ttu-id="8a71d-111">这些特性可简单可复杂，或如确保特定 Windows 功能已启用般简单，或如部署 SharePoint 般复杂。</span><span class="sxs-lookup"><span data-stu-id="8a71d-111">These characteristics can be as simple as ensuring a specific Windows feature is enabled or as complex as deploying SharePoint.</span></span>

<span data-ttu-id="8a71d-112">DSC 内置了监视和报告。</span><span class="sxs-lookup"><span data-stu-id="8a71d-112">DSC has monitoring and reporting built-in.</span></span> <span data-ttu-id="8a71d-113">如果系统不再相容，DSC 会引发警报，并采取措施更正系统。</span><span class="sxs-lookup"><span data-stu-id="8a71d-113">If a system is no longer compliant, DSC can raise an alert and act to correct the system.</span></span>

## <a name="benefits-of-using-dsc"></a><span data-ttu-id="8a71d-114">使用 DSC 的好处</span><span class="sxs-lookup"><span data-stu-id="8a71d-114">Benefits of using DSC</span></span>

<span data-ttu-id="8a71d-115">配置的设计简化了读取、存储和更新配置的方式。</span><span class="sxs-lookup"><span data-stu-id="8a71d-115">The configuration's design simplifies how they're read, stored, and updated.</span></span> <span data-ttu-id="8a71d-116">配置声明目标设备的状态，而非编写如何将设备置于该状态的说明。</span><span class="sxs-lookup"><span data-stu-id="8a71d-116">Configurations declare the state of target devices, rather than writing instructions for how to place devices in that state.</span></span> <span data-ttu-id="8a71d-117">这些因素降低了通过 DSC 学习、使用、实现和维护配置的成本。</span><span class="sxs-lookup"><span data-stu-id="8a71d-117">These factors reduce the costs to learn, adopt, implement, and maintain configuration through DSC.</span></span>

<span data-ttu-id="8a71d-118">创建配置意味着，单个位置中的复杂部署步骤将捕获为“单一资料来源”。 </span><span class="sxs-lookup"><span data-stu-id="8a71d-118">Creating configurations means that complex deployment steps are captured as a **single source of truth** in a single location.</span></span> <span data-ttu-id="8a71d-119">配置使得重复部署一组特定的计算机不易出错。</span><span class="sxs-lookup"><span data-stu-id="8a71d-119">Configurations make repeated deployments of a specific set of machines less error-prone.</span></span> <span data-ttu-id="8a71d-120">此外，还使部署更快并且更可靠，从而可以快速周转复杂部署。</span><span class="sxs-lookup"><span data-stu-id="8a71d-120">And, deployments are faster and more reliable, which enables a quick turnaround on complex deployments.</span></span>

<span data-ttu-id="8a71d-121">可通过 [PowerShell 库](https://powershellgallery.com)共享配置。</span><span class="sxs-lookup"><span data-stu-id="8a71d-121">Configurations are shareable via the [PowerShell Gallery](https://powershellgallery.com).</span></span> <span data-ttu-id="8a71d-122">你需完成的工作可能已存在常见方案和最佳做法。</span><span class="sxs-lookup"><span data-stu-id="8a71d-122">It's possible that common scenarios and best practices might already exist for the work you need to do.</span></span>

## <a name="dsc-and-devops"></a><span data-ttu-id="8a71d-123">DSC 和 DevOps</span><span class="sxs-lookup"><span data-stu-id="8a71d-123">DSC and DevOps</span></span>

<span data-ttu-id="8a71d-124">DSC 以 [DevOps](/archive/blogs/ashleymcglone/devops-for-n00bs-ie-windows-people-like-me) 为设计理念。</span><span class="sxs-lookup"><span data-stu-id="8a71d-124">DSC was designed with [DevOps](/archive/blogs/ashleymcglone/devops-for-n00bs-ie-windows-people-like-me) in mind.</span></span> <span data-ttu-id="8a71d-125">人员、流程和工具的组合，方便实现快速部署和迭代，旨在向内外部最终用户传递价值。</span><span class="sxs-lookup"><span data-stu-id="8a71d-125">A combination of people, processes, and tools that allow for rapid deployment and iteration focused on delivering value to end users whether internal or external.</span></span> <span data-ttu-id="8a71d-126">定义环境的单个配置意味着开发人员可以将其要求编码到配置，并将该配置签入源代码管理。</span><span class="sxs-lookup"><span data-stu-id="8a71d-126">A single configuration that defines an environment means that developers can encode their requirements into a configuration and check that configuration into source control.</span></span> <span data-ttu-id="8a71d-127">然后操作团队无需完成易出错的手动流程即可部署代码。</span><span class="sxs-lookup"><span data-stu-id="8a71d-127">Operations teams can then deploy code without going through error-prone manual processes.</span></span>

<span data-ttu-id="8a71d-128">配置[由数据驱动](../configurations/configData.md)。</span><span class="sxs-lookup"><span data-stu-id="8a71d-128">Configurations are [data-driven](../configurations/configData.md).</span></span> <span data-ttu-id="8a71d-129">定义的数据便于操作人员识别和更改环境，而无需开发人员介入。</span><span class="sxs-lookup"><span data-stu-id="8a71d-129">The defined data makes it easier for operations to identify and change environments without developer intervention.</span></span>

## <a name="dsc-on-premises-and-off-premises"></a><span data-ttu-id="8a71d-130">DSC 本地和非本地</span><span class="sxs-lookup"><span data-stu-id="8a71d-130">DSC on-premises and off-premises</span></span>

<span data-ttu-id="8a71d-131">DSC 可管理本地和非本地部署。</span><span class="sxs-lookup"><span data-stu-id="8a71d-131">DSC can manage on-premises and off-premises deployments.</span></span> <span data-ttu-id="8a71d-132">对于本地解决方案，DSC 拥有[请求服务器](../pull-server/pullServer.md)，可用于集中式管理计算机并报告其状态。</span><span class="sxs-lookup"><span data-stu-id="8a71d-132">For on-premises solutions, DSC has a [Pull Server](../pull-server/pullServer.md) that's used to centralize management of machines and report on their status.</span></span> <span data-ttu-id="8a71d-133">对于非本地云解决方案，Windows 适用的地方即可使用 DSC。</span><span class="sxs-lookup"><span data-stu-id="8a71d-133">For off-premises cloud solutions, DSC is usable any place Windows is usable.</span></span>
<span data-ttu-id="8a71d-134">Azure 有基于 DSC 的特定产品/服务，例如将 DSC 报告集中化的 [Azure 自动化](/azure/automation)。</span><span class="sxs-lookup"><span data-stu-id="8a71d-134">There are specific offerings from Azure built on DSC, such as [Azure Automation](/azure/automation), that centralizes DSC reporting.</span></span>

## <a name="dsc-and-compatibility"></a><span data-ttu-id="8a71d-135">DSC 和兼容性</span><span class="sxs-lookup"><span data-stu-id="8a71d-135">DSC and compatibility</span></span>

<span data-ttu-id="8a71d-136">尽管 DSC 在 Windows Server 2012 R2 中引入，但下层操作系统可通过 Windows Management Framework (WMF) 使用它。</span><span class="sxs-lookup"><span data-stu-id="8a71d-136">DSC was introduced in Windows Server 2012 R2, but it's available for down-level operating systems via the Windows Management Framework (WMF).</span></span> <span data-ttu-id="8a71d-137">有关 WMF 的详细信息，请参阅 [Windows Management Framework](/powershell/scripting/wmf/overview)。</span><span class="sxs-lookup"><span data-stu-id="8a71d-137">For more information about WMF, see [Windows Management Framework](/powershell/scripting/wmf/overview).</span></span>

<span data-ttu-id="8a71d-138">DSC 可以用于管理 Linux。</span><span class="sxs-lookup"><span data-stu-id="8a71d-138">DSC can be used to manage Linux.</span></span> <span data-ttu-id="8a71d-139">有关详细信息，请参阅[适用于 Linux 的 DSC 入门](../getting-started/lnxGettingStarted.md)。</span><span class="sxs-lookup"><span data-stu-id="8a71d-139">For more information, see [Getting Started with DSC for Linux](../getting-started/lnxGettingStarted.md).</span></span>
