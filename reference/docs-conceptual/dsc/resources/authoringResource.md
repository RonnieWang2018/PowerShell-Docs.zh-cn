---
ms.date: 07/08/2020
keywords: dsc,powershell,配置,安装程序
title: 构建自定义 Windows PowerShell Desired State Configuration 资源
description: 本文概述了开发资源和具有特定信息与示例的文章的链接。
ms.openlocfilehash: ff9a0c8ae10583155217fbeccc62e6e1c94f9a11
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656405"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="a0820-104">构建自定义 Windows PowerShell Desired State Configuration 资源</span><span class="sxs-lookup"><span data-stu-id="a0820-104">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="a0820-105">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a0820-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="a0820-106">Windows PowerShell Desired State Configuration (DSC) 具有可用于配置环境的内置资源。</span><span class="sxs-lookup"><span data-stu-id="a0820-106">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="a0820-107">本文概述了开发资源和具有特定信息与示例的文章的链接。</span><span class="sxs-lookup"><span data-stu-id="a0820-107">This article provides an overview of developing resources and links to articles with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="a0820-108">DSC 资源组件</span><span class="sxs-lookup"><span data-stu-id="a0820-108">DSC resource components</span></span>

<span data-ttu-id="a0820-109">DSC 资源是一个 Windows PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="a0820-109">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="a0820-110">该模块既包含资源的架构（可配置属性的定义）又包含资源的实现（执行配置指定的实际工作的代码）。</span><span class="sxs-lookup"><span data-stu-id="a0820-110">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="a0820-111">可在 MOF 文件中定义 DSC 资源架构，由脚本模块执行实现。</span><span class="sxs-lookup"><span data-stu-id="a0820-111">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="a0820-112">从版本 5 开始支持 PowerShell 类，因此架构和实现都可以在类中定义。</span><span class="sxs-lookup"><span data-stu-id="a0820-112">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="a0820-113">以下文章对如何创建 DSC 资源进行了更详细的介绍。</span><span class="sxs-lookup"><span data-stu-id="a0820-113">The following articles describe in more detail how to create DSC resources.</span></span>

- [<span data-ttu-id="a0820-114">使用 MOF 编写自定义 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="a0820-114">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
- [<span data-ttu-id="a0820-115">在 C# 中实现 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="a0820-115">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
- [<span data-ttu-id="a0820-116">使用 PowerShell 类编写自定义 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="a0820-116">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
- [<span data-ttu-id="a0820-117">复合资源：将 DSC 配置用作资源</span><span class="sxs-lookup"><span data-stu-id="a0820-117">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
- [<span data-ttu-id="a0820-118">使用资源设计器工具</span><span class="sxs-lookup"><span data-stu-id="a0820-118">Using the Resource Designer tool</span></span>](authoringResourceMofDesigner.md)
