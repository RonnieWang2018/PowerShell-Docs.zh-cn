---
ms.date: 09/26/2017
title: 预发行模块版本
description: PowerShellGet 模块支持使用语义化版本控制将 1.0.0 以上的版本的模块标记为预发行版。
ms.openlocfilehash: f794722f0a89f98f8f445ecd45dad9d3d2d7f3cb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661524"
---
# <a name="prerelease-module-versions"></a><span data-ttu-id="1ef43-103">预发行模块版本</span><span class="sxs-lookup"><span data-stu-id="1ef43-103">Prerelease Module Versions</span></span>

<span data-ttu-id="1ef43-104">从版本 1.6.0 开始，PowerShellGet 和 PowerShell 库都支持将 1.0.0 以上的版本标记为预发行版。</span><span class="sxs-lookup"><span data-stu-id="1ef43-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="1ef43-105">在此功能之前，预发行包仅限于以 0 开头的版本。</span><span class="sxs-lookup"><span data-stu-id="1ef43-105">Prior to this feature, prerelease packages were limited to having a version beginning with 0.</span></span> <span data-ttu-id="1ef43-106">这些功能的目标是为 [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) 版本控制约定提供更好的支持，并且不会破坏 PowerShell 版本 3 及更高版本或 PowerShellGet 现有版本的向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="1ef43-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="1ef43-107">本主题重点介绍特定于模块的功能。</span><span class="sxs-lookup"><span data-stu-id="1ef43-107">This topic focuses on the module-specific features.</span></span> <span data-ttu-id="1ef43-108">脚本的等效功能在[预发行版脚本](script-prerelease-support.md)主题中介绍。</span><span class="sxs-lookup"><span data-stu-id="1ef43-108">The equivalent features for scripts are in the [Prerelease Versions of Scripts](script-prerelease-support.md) topic.</span></span> <span data-ttu-id="1ef43-109">使用这些功能，发布服务器可以将模块或脚本标识为版本 2.5.0-alpha，随后可发布用于取代预发行版本的生产就绪版本 2.5.0。</span><span class="sxs-lookup"><span data-stu-id="1ef43-109">Using these features, publishers can identify a module or script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="1ef43-110">在高级别中，预发行模块的功能包括：</span><span class="sxs-lookup"><span data-stu-id="1ef43-110">At a high level, the prerelease module features include:</span></span>

- <span data-ttu-id="1ef43-111">在模块清单的 PSData 部分添加预发行版字符串将模块标识为预发行版本。</span><span class="sxs-lookup"><span data-stu-id="1ef43-111">Adding a Prerelease string to the PSData section of the module manifest identifies the module as a prerelease version.</span></span> <span data-ttu-id="1ef43-112">当模块发布到 PowerShell 库后，会从清单中提取此数据，用于标识预发行包。</span><span class="sxs-lookup"><span data-stu-id="1ef43-112">When the module is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease packages.</span></span>
- <span data-ttu-id="1ef43-113">获取预发行包需要将 `-AllowPrerelease` 标记添加到 PowerShellGet 命令 `Find-Module`、`Install-Module`、`Update-Module` 和 `Save-Module`。</span><span class="sxs-lookup"><span data-stu-id="1ef43-113">Acquiring prerelease packages requires adding `-AllowPrerelease` flag to the PowerShellGet commands `Find-Module`, `Install-Module`, `Update-Module`, and `Save-Module`.</span></span> <span data-ttu-id="1ef43-114">如果未指定标记，则不会显示预发行包。</span><span class="sxs-lookup"><span data-stu-id="1ef43-114">If the flag is not specified, prerelease packages will not be shown.</span></span>
- <span data-ttu-id="1ef43-115">`Find-Module`、`Get-InstalledModule` 显示的模块版本及在 PowerShell 库中显示的模块版本将显示为附加了预发行版字符串的单个字符串，如 2.5.0-alpha。</span><span class="sxs-lookup"><span data-stu-id="1ef43-115">Module versions displayed by `Find-Module`, `Get-InstalledModule`, and in the PowerShell Gallery will be displayed as a single string with the Prerelease string appended, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="1ef43-116">以下介绍了这些功能的详细信息。</span><span class="sxs-lookup"><span data-stu-id="1ef43-116">Details for the features are included below.</span></span>

<span data-ttu-id="1ef43-117">这些更改不会影响内置于 PowerShell 的模块版本支持，并与 PowerShell 3.0、4.0 和 5 兼容。</span><span class="sxs-lookup"><span data-stu-id="1ef43-117">These changes do not affect the module version support that is built into PowerShell, and are compatible with PowerShell 3.0, 4.0, and 5.</span></span>

## <a name="identifying-a-module-version-as-a-prerelease"></a><span data-ttu-id="1ef43-118">将模块版本标识为预发行版</span><span class="sxs-lookup"><span data-stu-id="1ef43-118">Identifying a module version as a prerelease</span></span>

<span data-ttu-id="1ef43-119">PowerShellGet 对预发行版本的支持要求在模块清单中使用两个字段：</span><span class="sxs-lookup"><span data-stu-id="1ef43-119">PowerShellGet support for prerelease versions requires the use of two fields within the Module Manifest:</span></span>

- <span data-ttu-id="1ef43-120">如果使用预发行版本，包含在模块清单中的 ModuleVersion 必须为 3 段式版本，且必须符合现有的 PowerShell 版本控制。</span><span class="sxs-lookup"><span data-stu-id="1ef43-120">The ModuleVersion included in the module manifest must be a 3-part version if a prerelease version is used, and must comply with existing PowerShell versioning.</span></span> <span data-ttu-id="1ef43-121">版本格式为 A.B.C，其中 A、B 和 C 均为整数。</span><span class="sxs-lookup"><span data-stu-id="1ef43-121">The version format would be A.B.C, where A, B, and C are all integers.</span></span>
- <span data-ttu-id="1ef43-122">预发行版字符串指定于模块清单、PrivateData 的 PSData 部分。</span><span class="sxs-lookup"><span data-stu-id="1ef43-122">The Prerelease string is specified in the module manifest, in the PSData section of PrivateData.</span></span>

<span data-ttu-id="1ef43-123">下面是对预发行版字符串的详细要求。</span><span class="sxs-lookup"><span data-stu-id="1ef43-123">Detailed requirements on the Prerelease string are below.</span></span>

<span data-ttu-id="1ef43-124">用于将模块定义为预发行版的模块清单的示例部分如下所示：</span><span class="sxs-lookup"><span data-stu-id="1ef43-124">An example section of a module manifest that defines a module as a prerelease would look like the following:</span></span>

```powershell
@{
    ModuleVersion = '2.5.0'
    #---
    PrivateData = @{
        PSData = @{
            Prerelease = 'alpha'
        }
    }
}
```

<span data-ttu-id="1ef43-125">对预发行版字符串的详细要求如下：</span><span class="sxs-lookup"><span data-stu-id="1ef43-125">The detailed requirements for Prerelease string are:</span></span>

- <span data-ttu-id="1ef43-126">ModuleVersion 为 Major.Minor.Build 的 3 段时，可能只指定预发行版字符串。</span><span class="sxs-lookup"><span data-stu-id="1ef43-126">Prerelease string may only be specified when the ModuleVersion is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="1ef43-127">这符合 SemVer v1.0.0 的要求。</span><span class="sxs-lookup"><span data-stu-id="1ef43-127">This aligns with SemVer v1.0.0.</span></span>
- <span data-ttu-id="1ef43-128">连字符是内部版本号和预发行版字符串之间的分隔符。</span><span class="sxs-lookup"><span data-stu-id="1ef43-128">A hyphen is the delimiter between the Build number and the Prerelease string.</span></span> <span data-ttu-id="1ef43-129">连字符只能作为第一个字符包含在预发行版字符串中。</span><span class="sxs-lookup"><span data-stu-id="1ef43-129">A hyphen may be included in the Prerelease string as the first character, only.</span></span>
- <span data-ttu-id="1ef43-130">预发行版字符串可以只包含 ASCII 字母数字 [0-9A-Za-z-]。</span><span class="sxs-lookup"><span data-stu-id="1ef43-130">The Prerelease string may contain only ASCII alphanumerics [0-9A-Za-z-].</span></span> <span data-ttu-id="1ef43-131">预发行版字符串最好以 alpha 字符开头，这样在扫描包列表时，可以更轻松地辨认这是预发行版本。</span><span class="sxs-lookup"><span data-stu-id="1ef43-131">It is a best practice to begin the Prerelease string with an alpha character, as it will be easier to identify that this is a prerelease version when scanning a list of packages.</span></span>
- <span data-ttu-id="1ef43-132">此时仅支持 SemVer v1.0.0 预发行字符串。</span><span class="sxs-lookup"><span data-stu-id="1ef43-132">Only SemVer v1.0.0 prerelease strings are supported at this time.</span></span> <span data-ttu-id="1ef43-133">预发行版字符串不得包含句点或 + [.+]，而在 SemVer 2.0 中允许包含  。</span><span class="sxs-lookup"><span data-stu-id="1ef43-133">Prerelease string **must not** contain either period or + [.+], which are allowed in SemVer 2.0.</span></span>
- <span data-ttu-id="1ef43-134">支持的预发行版字符串的示例包括：-alpha、-alpha1、-BETA、-update20171020</span><span class="sxs-lookup"><span data-stu-id="1ef43-134">Examples of supported Prerelease string are: -alpha, -alpha1, -BETA, -update20171020</span></span>

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a><span data-ttu-id="1ef43-135">预发行版本控制对排序顺序和安装文件夹的影响</span><span class="sxs-lookup"><span data-stu-id="1ef43-135">Prerelease versioning impact on sort order and installation folders</span></span>

<span data-ttu-id="1ef43-136">使用预发行版本时，排序顺序会发生更改，这在发布到 PowerShell 库时，以及使用 PowerShellGet 命令安装模块时非常重要。</span><span class="sxs-lookup"><span data-stu-id="1ef43-136">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing modules using PowerShellGet commands.</span></span> <span data-ttu-id="1ef43-137">如果预发行版字符串是针对两个模块指定的，则排序顺序基于连字符后面的字符串部分。</span><span class="sxs-lookup"><span data-stu-id="1ef43-137">If the Prerelease string is specified for two modules, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="1ef43-138">因此，2.5.0-alpha 版低于 2.5.0-beta 版，而 2.5.0-beta 版低于 2.5.0-gamma 版。</span><span class="sxs-lookup"><span data-stu-id="1ef43-138">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="1ef43-139">如果两个模块具有相同的 ModuleVersion，并且只有一个模块具有预发行版字符串，则不具有预发行版字符串的模块会假定为生产就绪版本，在排序时的版本要比具有预发行版字符串的预发行版本高。</span><span class="sxs-lookup"><span data-stu-id="1ef43-139">If two modules have the same ModuleVersion, and only one has a Prerelease string, the module without the Prerelease string is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version (which includes the Prerelease string).</span></span> <span data-ttu-id="1ef43-140">例如，在比较 2.5.0 和 2.5.0-beta 版本时，2.5.0 版本会视为两者中更高的版本。</span><span class="sxs-lookup"><span data-stu-id="1ef43-140">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="1ef43-141">在发布到 PowerShell 库时，默认情况下，发布的模块版本必须高于 PowerShell 库中以前发布的任何版本。</span><span class="sxs-lookup"><span data-stu-id="1ef43-141">When publishing to the PowerShell Gallery, by default the version of the module being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span>

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a><span data-ttu-id="1ef43-142">使用 PowerShellGet 命令查找和获取预发行包</span><span class="sxs-lookup"><span data-stu-id="1ef43-142">Finding and acquiring prerelease packages using PowerShellGet commands</span></span>

<span data-ttu-id="1ef43-143">使用 PowerShellGet Find-Module、Install-Module、Update-Module 和 Save-Module 命令处理预发行包需要添加 -AllowPrerelease 标记。</span><span class="sxs-lookup"><span data-stu-id="1ef43-143">Dealing with prerelease packages using PowerShellGet Find-Module, Install-Module, Update-Module, and Save-Module commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="1ef43-144">如果已指定 -AllowPrerelease，则会包括预发行包（如存在）。</span><span class="sxs-lookup"><span data-stu-id="1ef43-144">If -AllowPrerelease is specified, prerelease packages will be included if they are present.</span></span> <span data-ttu-id="1ef43-145">如果未指定 -AllowPrerelease 标记，则不会显示预发行包。</span><span class="sxs-lookup"><span data-stu-id="1ef43-145">If -AllowPrerelease flag is not specified, prerelease packages will not be shown.</span></span>

<span data-ttu-id="1ef43-146">PowerShellGet 模块命令中这种情况的唯一例外是 Get-InstalledModule，以及某些情况下的 Uninstall-Module。</span><span class="sxs-lookup"><span data-stu-id="1ef43-146">The only exceptions to this in the PowerShellGet module commands are Get-InstalledModule, and some cases with Uninstall-Module.</span></span>

- <span data-ttu-id="1ef43-147">Get-InstalledModule 始终在模块的版本字符串中自动显示预发行信息。</span><span class="sxs-lookup"><span data-stu-id="1ef43-147">Get-InstalledModule always will automatically show the prerelease information in the version string for modules.</span></span>
- <span data-ttu-id="1ef43-148">Uninstall-Module 在未指定任何版本时默认卸载最新版本的模块  。</span><span class="sxs-lookup"><span data-stu-id="1ef43-148">Uninstall-Module will by default uninstall the most recent version of a module, if __no version__ is specified.</span></span> <span data-ttu-id="1ef43-149">该行为尚未更改。</span><span class="sxs-lookup"><span data-stu-id="1ef43-149">That behavior has not changed.</span></span> <span data-ttu-id="1ef43-150">但是，如果预发行版本是使用 -RequiredVersion 指定的，则需要 -AllowPrerelease。</span><span class="sxs-lookup"><span data-stu-id="1ef43-150">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="1ef43-151">示例</span><span class="sxs-lookup"><span data-stu-id="1ef43-151">Examples</span></span>

<span data-ttu-id="1ef43-152">假定 PowerShell 库具有 TestPackage 模块版本 1.8.0 和 1.9.0-alpha。</span><span class="sxs-lookup"><span data-stu-id="1ef43-152">Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.</span></span> <span data-ttu-id="1ef43-153">如果未指定 `-AllowPrerelease`，则仅返回版本 1.8.0。</span><span class="sxs-lookup"><span data-stu-id="1ef43-153">If `-AllowPrerelease` is not specified, only version 1.8.0 will be returned.</span></span>

```powershell
find-module TestPackage
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.8.0          TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

```powershell
find-module TestPackage -AllowPrerelease
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.9.0-alpha    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="1ef43-154">若要安装预发行版，请始终指定 -AllowPrerelease。</span><span class="sxs-lookup"><span data-stu-id="1ef43-154">To install a prerelease, always specify -AllowPrerelease.</span></span> <span data-ttu-id="1ef43-155">指定预发行版字符串是不够的。</span><span class="sxs-lookup"><span data-stu-id="1ef43-155">Specifying a prerelease version string is not sufficient.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha
```

```output
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage
```

<span data-ttu-id="1ef43-156">前一个命令失败，因为未指定 -AllowPrerelease。</span><span class="sxs-lookup"><span data-stu-id="1ef43-156">The previous command failed because -AllowPrerelease was not specified.</span></span> <span data-ttu-id="1ef43-157">添加 `-AllowPrerelease` 将会成功。</span><span class="sxs-lookup"><span data-stu-id="1ef43-157">Adding `-AllowPrerelease` will result in success.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="1ef43-158">如果模块仅仅是因为指定的预发行版而有所区别，则不支持并行安装该模块的各版本。</span><span class="sxs-lookup"><span data-stu-id="1ef43-158">Side-by-side installation of versions of a module that differ only due to the prerelease specified is not supported.</span></span> <span data-ttu-id="1ef43-159">使用 PowerShellGet 安装模块时，通过使用 ModuleVersion 创建文件夹名称，并行安装同一模块的不同版本。</span><span class="sxs-lookup"><span data-stu-id="1ef43-159">When installing a module using PowerShellGet, different versions of the same module are installed side-by-side by creating a folder name using the ModuleVersion.</span></span> <span data-ttu-id="1ef43-160">不含预发行版字符串的 ModuleVersion 可用作文件夹名称。</span><span class="sxs-lookup"><span data-stu-id="1ef43-160">The ModuleVersion, without the prerelease string, is used for the folder name.</span></span> <span data-ttu-id="1ef43-161">用户安装 MyModule 的 2.5.0-alpha 版本时，会安装到 `MyModule\2.5.0` 文件夹。</span><span class="sxs-lookup"><span data-stu-id="1ef43-161">If a user installs MyModule version 2.5.0-alpha, it will be installed to the `MyModule\2.5.0` folder.</span></span> <span data-ttu-id="1ef43-162">如果用户之后安装 2.5.0-beta，则 2.5.0-beta 版本会覆盖  `MyModule\2.5.0` 文件夹的内容。</span><span class="sxs-lookup"><span data-stu-id="1ef43-162">If the user then installs 2.5.0-beta, the 2.5.0-beta version will **overwrite** the contents of the folder `MyModule\2.5.0`.</span></span> <span data-ttu-id="1ef43-163">此方法的一个优点是安装生产就绪版本后无需卸载预发行版本。</span><span class="sxs-lookup"><span data-stu-id="1ef43-163">One advantage to this approach is that there is no need to un-install the prerelease version after installing the production-ready version.</span></span> <span data-ttu-id="1ef43-164">以下示例展示了期望的效果：</span><span class="sxs-lookup"><span data-stu-id="1ef43-164">The example below shows what to expect:</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-alpha     TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name            Repository  Description
-------        ----            ----------  -----------
1.9.0-beta     TestPackage     PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

```

<span data-ttu-id="1ef43-165">如果未通过 -RequiredVersion，Uninstall-Module 会删除最新版本的模块。</span><span class="sxs-lookup"><span data-stu-id="1ef43-165">Uninstall-Module will remove the latest version of a module when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="1ef43-166">如果已指定 -RequiredVersion，并且是预发行版，则必须将 -AllowPrerelease 添加到命令中。</span><span class="sxs-lookup"><span data-stu-id="1ef43-166">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
2.0.0-alpha1    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta

Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-Module

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
2.0.0-alpha1    TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...
```

## <a name="more-details"></a><span data-ttu-id="1ef43-167">更多详细信息</span><span class="sxs-lookup"><span data-stu-id="1ef43-167">More details</span></span>

- [<span data-ttu-id="1ef43-168">预发行脚本版本</span><span class="sxs-lookup"><span data-stu-id="1ef43-168">Prerelease Script Versions</span></span>](script-prerelease-support.md)
- [<span data-ttu-id="1ef43-169">Find-Module</span><span class="sxs-lookup"><span data-stu-id="1ef43-169">Find-Module</span></span>](/powershell/module/powershellget/find-module)
- [<span data-ttu-id="1ef43-170">Install-Module</span><span class="sxs-lookup"><span data-stu-id="1ef43-170">Install-Module</span></span>](/powershell/module/powershellget/install-module)
- [<span data-ttu-id="1ef43-171">Save-Module</span><span class="sxs-lookup"><span data-stu-id="1ef43-171">Save-Module</span></span>](/powershell/module/powershellget/save-module)
- [<span data-ttu-id="1ef43-172">Update-Module</span><span class="sxs-lookup"><span data-stu-id="1ef43-172">Update-Module</span></span>](/powershell/module/powershellget/Update-Module)
- [<span data-ttu-id="1ef43-173">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="1ef43-173">Get-InstalledModule</span></span>](/powershell/module/powershellget/get-installedmodule)
- [<span data-ttu-id="1ef43-174">UnInstall-Module</span><span class="sxs-lookup"><span data-stu-id="1ef43-174">UnInstall-Module</span></span>](/powershell/module/powershellget/uninstall-module)
