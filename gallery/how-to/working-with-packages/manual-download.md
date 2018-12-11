---
ms.date: 09/11/2018
contributor: JKeithB
keywords: 库, powershell, psgallery
title: 手动包下载
ms.openlocfilehash: 57baa14089b803f58c42ccb54553ecace841e34b
ms.sourcegitcommit: e24525046dd37166b9d83eeecdc534726316f429
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2018
ms.locfileid: "52742816"
---
# <a name="manual-package-download"></a><span data-ttu-id="f0d50-103">手动包下载</span><span class="sxs-lookup"><span data-stu-id="f0d50-103">Manual Package Download</span></span>

<span data-ttu-id="f0d50-104">Powershell 库支持直接下载网站中的包而无需使用 PowerShellGet cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f0d50-104">The Powershell Gallery supports downloading a package from the website directly, without using the PowerShellGet cmdlets.</span></span> <span data-ttu-id="f0d50-105">您可以为 NuGet 包 (.nupkg) 文件，然后将复制到内部存储库下载任何包。</span><span class="sxs-lookup"><span data-stu-id="f0d50-105">You can download any package as a NuGet package (.nupkg) file, which you can then copy to an internal repository.</span></span>

> [!NOTE]
> <span data-ttu-id="f0d50-106">手动包下载并非旨在替代 Install-Module cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f0d50-106">Manual package download is **not** intended as a replacement for the Install-Module cmdlet.</span></span>
> <span data-ttu-id="f0d50-107">下载包不会安装模块或脚本。</span><span class="sxs-lookup"><span data-stu-id="f0d50-107">Downloading the package does not install the module or script.</span></span> <span data-ttu-id="f0d50-108">下载的 NuGet 包中不包含依赖项。</span><span class="sxs-lookup"><span data-stu-id="f0d50-108">Dependencies are not included in the NuGet package downloaded.</span></span> <span data-ttu-id="f0d50-109">以下说明仅供参考。</span><span class="sxs-lookup"><span data-stu-id="f0d50-109">The following instructions are provided for reference purposes only.</span></span>

## <a name="using-manual-download-to-acquire-a-package"></a><span data-ttu-id="f0d50-110">使用手动下载以获取包</span><span class="sxs-lookup"><span data-stu-id="f0d50-110">Using manual download to acquire a package</span></span>

<span data-ttu-id="f0d50-111">每个页面都有一个手动下载链接，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f0d50-111">Each page has a link for Manual Download, as shown here:</span></span>

![手动下载](../../Images/packagedisplaypagewithpseditions.png)

<span data-ttu-id="f0d50-113">若要手动下载，请单击“下载原始 nupkg 文件”。</span><span class="sxs-lookup"><span data-stu-id="f0d50-113">To download manually, click on **Download the raw nupkg file**.</span></span> <span data-ttu-id="f0d50-114">将包的副本复制到名称为 `<name>.<version>.nupkg` 的浏览器的下载文件夹中。</span><span class="sxs-lookup"><span data-stu-id="f0d50-114">A copy of the package copied to the download folder for your browser with the name `<name>.<version>.nupkg`.</span></span>

<span data-ttu-id="f0d50-115">NuGet 包是一个 ZIP 存档，其中的额外文件包含有关包内容的信息。</span><span class="sxs-lookup"><span data-stu-id="f0d50-115">A NuGet package is a ZIP archive with extra files containing information about the contents of the package.</span></span> <span data-ttu-id="f0d50-116">某些浏览器（如 Internet Explorer）会自动将 `.nupkg` 文件扩展名替换为 `.zip`。</span><span class="sxs-lookup"><span data-stu-id="f0d50-116">Some browsers, like Internet Explorer, automatically replace the `.nupkg` file extension with `.zip`.</span></span> <span data-ttu-id="f0d50-117">要展开包，请根据需要将 `.nupkg` 文件重命名为 `.zip`，然后将内容提取到本地文件夹。</span><span class="sxs-lookup"><span data-stu-id="f0d50-117">To expand the package, rename the `.nupkg` file to `.zip`, if needed, then extract the contents to a local folder.</span></span>

<span data-ttu-id="f0d50-118">NuGet 包文件包含以下特定于 NuGet 的元素，这些元素不是原始打包代码的一部分：</span><span class="sxs-lookup"><span data-stu-id="f0d50-118">A NuGet package file includes the following NuGet-specific elements that aren't part of the original packaged code:</span></span>

- <span data-ttu-id="f0d50-119">名为 `_rels` 的文件夹 - 包含列出依赖项的 `.rels` 文件</span><span class="sxs-lookup"><span data-stu-id="f0d50-119">A folder named `_rels` - contains a `.rels` file that lists the dependencies</span></span>
- <span data-ttu-id="f0d50-120">名为 `package` 的文件夹 - 包含特定于 NuGet 的数据</span><span class="sxs-lookup"><span data-stu-id="f0d50-120">A folder named `package` - contains the NuGet-specific data</span></span>
- <span data-ttu-id="f0d50-121">名为 `[Content_Types].xml` 的文件 - 描述 PowerShellGet 等扩展如何与 NuGet 一起使用</span><span class="sxs-lookup"><span data-stu-id="f0d50-121">A file named `[Content_Types].xml` - describes how extensions like PowerShellGet work with NuGet</span></span>
- <span data-ttu-id="f0d50-122">名为 `<name>.nuspec` 的文件 - 包含大量元数据</span><span class="sxs-lookup"><span data-stu-id="f0d50-122">A file named `<name>.nuspec` - contains the bulk of the metadata</span></span>

## <a name="installing-powershell-modules-from-a-nuget-package"></a><span data-ttu-id="f0d50-123">从 NuGet 包安装 PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="f0d50-123">Installing PowerShell Modules from a NuGet package</span></span>

> [!NOTE]
> <span data-ttu-id="f0d50-124">这些说明并未给出与运行 `Install-Module` 相同的结果。</span><span class="sxs-lookup"><span data-stu-id="f0d50-124">These instructions **DO NOT** give the same result as running `Install-Module`.</span></span> <span data-ttu-id="f0d50-125">这些说明满足最低要求。</span><span class="sxs-lookup"><span data-stu-id="f0d50-125">These instructions fulfill the minimum requirements.</span></span> <span data-ttu-id="f0d50-126">它们并非 `Install-Module` 的替代品。</span><span class="sxs-lookup"><span data-stu-id="f0d50-126">They are not intended to be a replacement for `Install-Module`.</span></span> <span data-ttu-id="f0d50-127">`Install-Module` 执行的某些步骤不包括在内。</span><span class="sxs-lookup"><span data-stu-id="f0d50-127">Some steps performed by `Install-Module` are not included.</span></span>

<span data-ttu-id="f0d50-128">最简单的方法是从文件夹中删除特定于 NuGet 的元素。</span><span class="sxs-lookup"><span data-stu-id="f0d50-128">The easiest approach is to remove the NuGet-specific elements from the folder.</span></span> <span data-ttu-id="f0d50-129">此方法将保留由包创建者创建的 PowerShell 代码。</span><span class="sxs-lookup"><span data-stu-id="f0d50-129">This leaves the PowerShell code created by the package author.</span></span> <span data-ttu-id="f0d50-130">步骤如下：</span><span class="sxs-lookup"><span data-stu-id="f0d50-130">The steps are:</span></span>

1. <span data-ttu-id="f0d50-131">将 NuGet 包的内容提取到本地文件夹。</span><span class="sxs-lookup"><span data-stu-id="f0d50-131">Extract the contents of the NuGet package to a local folder.</span></span>
2. <span data-ttu-id="f0d50-132">从文件夹中删除特定于 NuGet 的元素。</span><span class="sxs-lookup"><span data-stu-id="f0d50-132">Delete the NuGet-specific elements from the folder.</span></span>
3. <span data-ttu-id="f0d50-133">重命名文件夹。</span><span class="sxs-lookup"><span data-stu-id="f0d50-133">Rename the folder.</span></span> <span data-ttu-id="f0d50-134">默认文件夹名称通常是 `<name>.<version>`。</span><span class="sxs-lookup"><span data-stu-id="f0d50-134">The default folder name is usually `<name>.<version>`.</span></span> <span data-ttu-id="f0d50-135">若将模块标记为预发布版本，则版本可包含“预发行版”。</span><span class="sxs-lookup"><span data-stu-id="f0d50-135">The version can include "-prerelease" if the module is tagged as a prerelease version.</span></span> <span data-ttu-id="f0d50-136">将文件夹重命名为模块名称。</span><span class="sxs-lookup"><span data-stu-id="f0d50-136">Rename the folder to just the module name.</span></span> <span data-ttu-id="f0d50-137">例如，将“azurerm.storage.5.0.4-预览版”重命名为“azurerm.storage”。</span><span class="sxs-lookup"><span data-stu-id="f0d50-137">For example, "azurerm.storage.5.0.4-preview" becomes "azurerm.storage".</span></span>
4. <span data-ttu-id="f0d50-138">将文件夹复制到一个文件夹中`$env:PSModulePath value`。</span><span class="sxs-lookup"><span data-stu-id="f0d50-138">Copy the folder to one of the folders in the `$env:PSModulePath value`.</span></span> <span data-ttu-id="f0d50-139">`$env:PSModulePath` 是以分号分隔一系列 PowerShell 的模块应查找的路径。</span><span class="sxs-lookup"><span data-stu-id="f0d50-139">`$env:PSModulePath` is a semicolon delimited set of paths in which PowerShell should look for modules.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f0d50-140">手动下载不包括模块所需的任何依赖项。</span><span class="sxs-lookup"><span data-stu-id="f0d50-140">The manual download does not include any dependencies required by the module.</span></span> <span data-ttu-id="f0d50-141">若包具有依赖项，则必须在系统上安装它们才能使此模块正常工作。</span><span class="sxs-lookup"><span data-stu-id="f0d50-141">If the package has dependencies, they must be installed on the system for this module to work correctly.</span></span> <span data-ttu-id="f0d50-142">PowerShell 库显示包所需的所有依赖项。</span><span class="sxs-lookup"><span data-stu-id="f0d50-142">The PowerShell Gallery shows all dependencies required by the package.</span></span>

## <a name="installing-powershell-scripts-from-a-nuget-package"></a><span data-ttu-id="f0d50-143">在 NuGet 包安装 PowerShell 脚本</span><span class="sxs-lookup"><span data-stu-id="f0d50-143">Installing PowerShell Scripts from a NuGet package</span></span>

> [!NOTE]
> <span data-ttu-id="f0d50-144">这些说明并未给出与运行 `Install-Script` 相同的结果。</span><span class="sxs-lookup"><span data-stu-id="f0d50-144">These instructions **DO NOT** give the same result as running `Install-Script`.</span></span> <span data-ttu-id="f0d50-145">这些说明满足最低要求。</span><span class="sxs-lookup"><span data-stu-id="f0d50-145">These instructions fulfill the minimum requirements.</span></span> <span data-ttu-id="f0d50-146">它们并非 `Install-Script` 的替代品。</span><span class="sxs-lookup"><span data-stu-id="f0d50-146">They are not intended to be a replacement for `Install-Script`.</span></span>

<span data-ttu-id="f0d50-147">最简单的方法是提取 NuGet 包，然后直接使用脚本。</span><span class="sxs-lookup"><span data-stu-id="f0d50-147">The easiest approach is to extract the NuGet package, then use the script directly.</span></span> <span data-ttu-id="f0d50-148">步骤如下：</span><span class="sxs-lookup"><span data-stu-id="f0d50-148">The steps are:</span></span>

1. <span data-ttu-id="f0d50-149">提取 NuGet 包的内容。</span><span class="sxs-lookup"><span data-stu-id="f0d50-149">Extract the contents of the NuGet package.</span></span>
2. <span data-ttu-id="f0d50-150">文件夹中的 `.PS1` 文件可直接从此位置使用。</span><span class="sxs-lookup"><span data-stu-id="f0d50-150">The `.PS1` file in the folder can be used directly from this location.</span></span>
3. <span data-ttu-id="f0d50-151">可删除文件夹中特定于 NuGet 的元素。</span><span class="sxs-lookup"><span data-stu-id="f0d50-151">You may delete the NuGet-specific elements in the folder.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f0d50-152">手动下载不包括模块所需的任何依赖项。</span><span class="sxs-lookup"><span data-stu-id="f0d50-152">The manual download does not include any dependencies required by the module.</span></span> <span data-ttu-id="f0d50-153">若包具有依赖项，则必须在系统上安装它们才能使此模块正常工作。</span><span class="sxs-lookup"><span data-stu-id="f0d50-153">If the package has dependencies, they must be installed on the system for this module to work correctly.</span></span> <span data-ttu-id="f0d50-154">PowerShell 库显示包所需的所有依赖项。</span><span class="sxs-lookup"><span data-stu-id="f0d50-154">The PowerShell Gallery shows all dependencies required by the package.</span></span>