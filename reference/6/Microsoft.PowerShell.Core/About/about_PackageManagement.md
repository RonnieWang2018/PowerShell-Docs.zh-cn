---
description: PackageManagement 是软件程序包管理器的聚合器。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_packagemanagement?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PackageManagement
ms.openlocfilehash: 8fd5d8e059d09556f0e7efa6b68ab4a7c018d3c0
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/13/2020
ms.locfileid: "93199787"
---
# <a name="about-packagemanagement"></a><span data-ttu-id="2129c-104">关于 PackageManagement</span><span class="sxs-lookup"><span data-stu-id="2129c-104">About PackageManagement</span></span>

## <a name="short-description"></a><span data-ttu-id="2129c-105">简短说明</span><span class="sxs-lookup"><span data-stu-id="2129c-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="2129c-106">PackageManagement 是软件程序包管理器的聚合器。</span><span class="sxs-lookup"><span data-stu-id="2129c-106">PackageManagement is an aggregator for software package managers.</span></span>

## <a name="long-description"></a><span data-ttu-id="2129c-107">详细说明</span><span class="sxs-lookup"><span data-stu-id="2129c-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="2129c-108">PackageManagement 功能是在 Windows PowerShell 5.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="2129c-108">PackageManagement functionality was introduced in Windows PowerShell 5.0.</span></span>

<span data-ttu-id="2129c-109">PackageManagement 是软件包管理系统的统一接口;可以运行 PackageManagement cmdlet 来执行软件发现、安装和清单 (SDII) 任务。</span><span class="sxs-lookup"><span data-stu-id="2129c-109">PackageManagement is a unified interface for software package management systems; you can run PackageManagement cmdlets to perform software discovery, installation, and inventory (SDII) tasks.</span></span> <span data-ttu-id="2129c-110">无论采用哪种基础安装技术，都可以在 PackageManagement 模块中运行公共 cmdlet，搜索、安装或卸载包;添加、删除和查询包存储库;并在计算机上运行查询以确定安装了哪些软件包。</span><span class="sxs-lookup"><span data-stu-id="2129c-110">Regardless of the underlying installation technology, you can run the common cmdlets in the PackageManagement module to search for, install, or uninstall packages; add, remove, and query package repositories; and run queries on a computer to determine which software packages are installed.</span></span>

<span data-ttu-id="2129c-111">PackageManagement 支持支持其他软件包管理系统的灵活插件模型。</span><span class="sxs-lookup"><span data-stu-id="2129c-111">PackageManagement supports a flexible plug-in model that enables support for other software package management systems.</span></span>

<span data-ttu-id="2129c-112">PackageManagement 模块随 Windows PowerShell 5.0 和更高版本的 PowerShell 一起提供，可用于三个级别的包管理结构：包提供程序、包源和包本身。</span><span class="sxs-lookup"><span data-stu-id="2129c-112">The PackageManagement module is included with Windows PowerShell 5.0 and later releases of PowerShell, and works on three levels of package management structure: package providers, package sources, and the packages themselves.</span></span> <span data-ttu-id="2129c-113">让我们定义一些术语：</span><span class="sxs-lookup"><span data-stu-id="2129c-113">Let us define some terms:</span></span>

- <span data-ttu-id="2129c-114">程序包管理器：软件程序包管理系统。</span><span class="sxs-lookup"><span data-stu-id="2129c-114">Package manager: Software package management system.</span></span> <span data-ttu-id="2129c-115">采用 PackageManagement 术语，这是一个程序包提供程序。</span><span class="sxs-lookup"><span data-stu-id="2129c-115">In PackageManagement terms, this is a package provider.</span></span>
- <span data-ttu-id="2129c-116">包提供程序：适用于包管理器的 PackageManagement 术语。</span><span class="sxs-lookup"><span data-stu-id="2129c-116">Package provider: PackageManagement term for a package manager.</span></span> <span data-ttu-id="2129c-117">示例可以包括 Windows Installer、Chocolatey 等。</span><span class="sxs-lookup"><span data-stu-id="2129c-117">Examples can include Windows Installer, Chocolatey, and others.</span></span>
- <span data-ttu-id="2129c-118">包源：配置包提供程序以用作存储库的 URL、本地文件夹或网络共享文件夹。</span><span class="sxs-lookup"><span data-stu-id="2129c-118">Package source: A URL, local folder, or network shared folder that you configure package providers to use as a repository.</span></span>
- <span data-ttu-id="2129c-119">包：包提供程序管理并存储在特定包源中的一段软件。</span><span class="sxs-lookup"><span data-stu-id="2129c-119">Package: A piece of software that a package provider manages, and that is stored in a specific package source.</span></span>

<span data-ttu-id="2129c-120">PackageManagement 模块包含以下 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2129c-120">The PackageManagement module includes the following cmdlets.</span></span> <span data-ttu-id="2129c-121">有关详细信息，请参阅 [PackageManagement](/powershell/module/packagemanagement) 帮助。</span><span class="sxs-lookup"><span data-stu-id="2129c-121">For more information, see the [PackageManagement](/powershell/module/packagemanagement) help.</span></span>

- <span data-ttu-id="2129c-122">`Get-PackageProvider`：返回连接到 PackageManagement 的包提供程序的列表。</span><span class="sxs-lookup"><span data-stu-id="2129c-122">`Get-PackageProvider`: Returns a list of package providers that are  connected to PackageManagement.</span></span>
- <span data-ttu-id="2129c-123">`Get-PackageSource`：获取为包提供程序注册的包源的列表。</span><span class="sxs-lookup"><span data-stu-id="2129c-123">`Get-PackageSource`: Gets a list of package sources that are registered for a package provider.</span></span>
- <span data-ttu-id="2129c-124">`Register-PackageSource`：为指定的包提供程序添加包源。</span><span class="sxs-lookup"><span data-stu-id="2129c-124">`Register-PackageSource`: Adds a package source for a specified package provider.</span></span>
- <span data-ttu-id="2129c-125">`Set-PackageSource`：设置现有包源的属性。</span><span class="sxs-lookup"><span data-stu-id="2129c-125">`Set-PackageSource`: Sets properties on an existing package source.</span></span>
- <span data-ttu-id="2129c-126">`Unregister-PackageSource`：删除已注册的包源。</span><span class="sxs-lookup"><span data-stu-id="2129c-126">`Unregister-PackageSource`: Removes a registered package source.</span></span>
- <span data-ttu-id="2129c-127">`Get-Package`：返回已安装软件包的列表。</span><span class="sxs-lookup"><span data-stu-id="2129c-127">`Get-Package`: Returns a list of installed software packages.</span></span>
- <span data-ttu-id="2129c-128">`Find-Package`：在可用包源中查找软件包。</span><span class="sxs-lookup"><span data-stu-id="2129c-128">`Find-Package`: Finds software packages in available package sources.</span></span>
- <span data-ttu-id="2129c-129">`Install-Package`：安装一个或多个软件包。</span><span class="sxs-lookup"><span data-stu-id="2129c-129">`Install-Package`: Installs one or more software packages.</span></span>
- <span data-ttu-id="2129c-130">`Save-Package`：将包保存到本地计算机，但不安装它们。</span><span class="sxs-lookup"><span data-stu-id="2129c-130">`Save-Package`: Saves packages to the local computer without installing them.</span></span>
- <span data-ttu-id="2129c-131">`Uninstall-Package`：卸载一个或多个软件包。</span><span class="sxs-lookup"><span data-stu-id="2129c-131">`Uninstall-Package`: Uninstalls one or more software packages.</span></span>

### <a name="package-provider-bootstrapping-and-dynamic-cmdlet-parameters"></a><span data-ttu-id="2129c-132">包提供程序引导和动态 Cmdlet 参数</span><span class="sxs-lookup"><span data-stu-id="2129c-132">Package Provider Bootstrapping and Dynamic Cmdlet Parameters</span></span>

<span data-ttu-id="2129c-133">默认情况下，PackageManagement 附带核心启动提供程序。</span><span class="sxs-lookup"><span data-stu-id="2129c-133">By default, PackageManagement ships with a core bootstrap provider.</span></span> <span data-ttu-id="2129c-134">你可以通过引导提供程序来安装其他包提供程序，因为你需要它们;也就是说，从 web 服务响应自动安装提供程序的提示。</span><span class="sxs-lookup"><span data-stu-id="2129c-134">You can install additional package providers as you need them by bootstrapping the providers; that is, responding to a prompt to install the provider automatically, from a web service.</span></span> <span data-ttu-id="2129c-135">你可以使用任何 PackageManagement cmdlet 指定包提供程序;如果指定的提供程序不可用，则 PackageManagement 会提示你启动 (或自动安装) 提供程序。</span><span class="sxs-lookup"><span data-stu-id="2129c-135">You can specify a package provider with any PackageManagement cmdlet; if the specified provider is not available, PackageManagement prompts you to bootstrap (or automatically install) the provider.</span></span> <span data-ttu-id="2129c-136">在以下示例中，如果尚未安装 Chocolatey 提供程序，则 PackageManagement 引导会安装该提供程序。</span><span class="sxs-lookup"><span data-stu-id="2129c-136">In the following examples, if the Chocolatey provider is not already installed, PackageManagement bootstrapping installs the provider.</span></span>

```powershell
Find-Package -Provider Chocolatey <PackageName>
```

<span data-ttu-id="2129c-137">如果尚未安装 Chocolatey 提供程序，则在运行上述命令时，系统将提示你安装它。</span><span class="sxs-lookup"><span data-stu-id="2129c-137">If the Chocolatey provider is not already installed, when you run the preceding command, you are prompted to install it.</span></span>

```powershell
Install-Package <Chocolatey package Name> -ForceBootstrap
```

<span data-ttu-id="2129c-138">如果尚未安装 Chocolatey 提供程序，则在运行上述命令时，将安装该提供程序;但由于 ForceBootstrap 参数已添加到命令中，系统不会提示你进行安装。提供程序和包都是自动安装的。</span><span class="sxs-lookup"><span data-stu-id="2129c-138">If the Chocolatey provider is not already installed, when you run the preceding command, the provider is installed; but because the ForceBootstrap parameter has been added to the command, you are not prompted to install it; both the provider and the package are installed automatically.</span></span>

<span data-ttu-id="2129c-139">当你尝试安装包时，如果你尚未安装支持的提供程序，并且未将 ForceBootstrap 参数添加到命令中，则 PackageManagement 会提示你安装该提供程序。</span><span class="sxs-lookup"><span data-stu-id="2129c-139">When you try to install a package, if you do not already have the supporting provider installed, and you do not add the ForceBootstrap parameter to your command, PackageManagement prompts you to install the provider.</span></span>

<span data-ttu-id="2129c-140">在 PackageManagement 命令中指定包提供程序可使动态参数可用于特定于该程序包提供程序。</span><span class="sxs-lookup"><span data-stu-id="2129c-140">Specifying a package provider in your PackageManagement command can make dynamic parameters available that are specific to that package provider.</span></span> <span data-ttu-id="2129c-141">针对特定的 PackageManagement cmdlet 运行 Get-Help 时，将返回参数集的列表，并将可用包提供程序的动态参数分组到不同的参数集。</span><span class="sxs-lookup"><span data-stu-id="2129c-141">When you run Get-Help for a specific PackageManagement cmdlet, a list of parameter sets are returned, grouping dynamic parameters for available package providers in separate parameter sets.</span></span>

<span data-ttu-id="2129c-142">有关 PackageManagement 项目的详细信息</span><span class="sxs-lookup"><span data-stu-id="2129c-142">More Information About the PackageManagement Project</span></span>

<span data-ttu-id="2129c-143">有关 PackageManagement open 开发项目的详细信息（包括如何创建 PackageManagement 包提供程序），请参阅 GitHub 上的 PackageManagement 项目 https://oneget.org 。</span><span class="sxs-lookup"><span data-stu-id="2129c-143">For more information about the PackageManagement open development project, including how to create a PackageManagement package provider, see the PackageManagement project on GitHub at https://oneget.org.</span></span>

## <a name="see-also"></a><span data-ttu-id="2129c-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2129c-144">SEE ALSO</span></span>

[<span data-ttu-id="2129c-145">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="2129c-145">Get-PackageProvider</span></span>](xref:PackageManagement.Get-PackageProvider)

[<span data-ttu-id="2129c-146">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="2129c-146">Get-PackageSource</span></span>](xref:PackageManagement.Get-PackageSource)

[<span data-ttu-id="2129c-147">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="2129c-147">Register-PackageSource</span></span>](xref:PackageManagement.Register-PackageSource)

[<span data-ttu-id="2129c-148">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="2129c-148">Set-PackageSource</span></span>](xref:PackageManagement.Set-PackageSource)

[<span data-ttu-id="2129c-149">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="2129c-149">Unregister-PackageSource</span></span>](xref:PackageManagement.Unregister-PackageSource)

[<span data-ttu-id="2129c-150">Get-Package</span><span class="sxs-lookup"><span data-stu-id="2129c-150">Get-Package</span></span>](xref:PackageManagement.Get-Package)

[<span data-ttu-id="2129c-151">Find-Package</span><span class="sxs-lookup"><span data-stu-id="2129c-151">Find-Package</span></span>](xref:PackageManagement.Find-Package)

[<span data-ttu-id="2129c-152">Install-Package</span><span class="sxs-lookup"><span data-stu-id="2129c-152">Install-Package</span></span>](xref:PackageManagement.Install-Package)

[<span data-ttu-id="2129c-153">Save-Package</span><span class="sxs-lookup"><span data-stu-id="2129c-153">Save-Package</span></span>](xref:PackageManagement.Save-Package)

[<span data-ttu-id="2129c-154">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="2129c-154">Uninstall-Package</span></span>](xref:PackageManagement.Uninstall-Package)
