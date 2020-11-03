---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/22/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-package?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Package
ms.openlocfilehash: 0b821f96606215d5d961329ebc69a1e5d3260763
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93198141"
---
# <span data-ttu-id="3bc44-103">Get-Package</span><span class="sxs-lookup"><span data-stu-id="3bc44-103">Get-Package</span></span>

## <span data-ttu-id="3bc44-104">摘要</span><span class="sxs-lookup"><span data-stu-id="3bc44-104">SYNOPSIS</span></span>
<span data-ttu-id="3bc44-105">返回使用 **PackageManagement** 安装的所有软件包的列表。</span><span class="sxs-lookup"><span data-stu-id="3bc44-105">Returns a list of all software packages that were installed with **PackageManagement** .</span></span>

## <span data-ttu-id="3bc44-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3bc44-106">SYNTAX</span></span>

### <span data-ttu-id="3bc44-107">NuGet</span><span class="sxs-lookup"><span data-stu-id="3bc44-107">NuGet</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="3bc44-108">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="3bc44-108">PowerShellGet</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Scope <String>] [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions]
 [<CommonParameters>]
```

## <span data-ttu-id="3bc44-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3bc44-109">DESCRIPTION</span></span>

<span data-ttu-id="3bc44-110">`Get-Package`Cmdlet 将返回本地计算机上使用 **PackageManagement** 安装的所有软件包的列表。</span><span class="sxs-lookup"><span data-stu-id="3bc44-110">The `Get-Package` cmdlet returns a list of all software packages on the local computer that were installed with **PackageManagement** .</span></span> <span data-ttu-id="3bc44-111">您可以 `Get-Package` 在远程计算机上运行它，方法是将它作为 `Invoke-Command` 或 `Enter-PSSession` 命令或脚本的一部分运行。</span><span class="sxs-lookup"><span data-stu-id="3bc44-111">You can run `Get-Package` on remote computers by running it as part of an `Invoke-Command` or `Enter-PSSession` command or script.</span></span>

## <span data-ttu-id="3bc44-112">示例</span><span class="sxs-lookup"><span data-stu-id="3bc44-112">EXAMPLES</span></span>

### <span data-ttu-id="3bc44-113">示例1：获取所有已安装的包</span><span class="sxs-lookup"><span data-stu-id="3bc44-113">Example 1: Get all installed packages</span></span>

<span data-ttu-id="3bc44-114">该 `Get-Package` cmdlet 将获取在本地计算机上安装的所有包。</span><span class="sxs-lookup"><span data-stu-id="3bc44-114">The `Get-Package` cmdlet gets all packages that are installed on the local computer.</span></span>

```powershell
Get-Package
```

```Output
Name           Version      Source                                     ProviderName
----           -------      ------                                     ------------
posh-git       0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
```

### <span data-ttu-id="3bc44-115">示例2：获取远程计算机上安装的包</span><span class="sxs-lookup"><span data-stu-id="3bc44-115">Example 2: Get packages that are installed on a remote computer</span></span>

<span data-ttu-id="3bc44-116">此命令获取由 **PackageManagement** 在远程计算机上安装的包的列表。</span><span class="sxs-lookup"><span data-stu-id="3bc44-116">This command gets a list of packages that were installed by **PackageManagement** on a remote computer.</span></span> <span data-ttu-id="3bc44-117">此命令会提示你提供指定用户的密码。</span><span class="sxs-lookup"><span data-stu-id="3bc44-117">This command prompts you to provide the specified user's password.</span></span>

```
PS> Invoke-Command -ComputerName Server01 -Credential CONTOSO\TestUser -ScriptBlock {Get-Package}
```

<span data-ttu-id="3bc44-118">`Invoke-Command` 使用 **ComputerName** 参数指定远程计算机 **Server01** 。</span><span class="sxs-lookup"><span data-stu-id="3bc44-118">`Invoke-Command` uses the **ComputerName** parameter to specify a remote computer, **Server01** .</span></span> <span data-ttu-id="3bc44-119">**Credential** 参数指定有权在计算机上运行命令的域和用户名。</span><span class="sxs-lookup"><span data-stu-id="3bc44-119">The **Credential** parameter specifies a domain and user name with permissions to run commands on the computer.</span></span> <span data-ttu-id="3bc44-120">**ScriptBlock** 参数 `Get-Package` 在远程计算机上运行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3bc44-120">The **ScriptBlock** parameter runs the `Get-Package` cmdlet on the remote computer.</span></span>

### <span data-ttu-id="3bc44-121">示例3：获取指定提供程序的包</span><span class="sxs-lookup"><span data-stu-id="3bc44-121">Example 3: Get packages for a specified provider</span></span>

<span data-ttu-id="3bc44-122">此命令从特定提供程序获取在本地计算机上安装的软件包。</span><span class="sxs-lookup"><span data-stu-id="3bc44-122">This command gets software packages installed on the local computer from a specific provider.</span></span>

```powershell
Get-Package -ProviderName PowerShellGet -AllVersions
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.2.2        https://www.powershellgallery.com/api/v2   PowerShellGet
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
posh-git              0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
PowerShellGet         2.0.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

<span data-ttu-id="3bc44-123">`Get-Package` 使用 **ProviderName** 参数指定特定提供程序 **PowerShellGet** 。</span><span class="sxs-lookup"><span data-stu-id="3bc44-123">`Get-Package` uses the **ProviderName** parameter to specify a specific provider, **PowerShellGet** .</span></span>
<span data-ttu-id="3bc44-124">" **所有版本** " 参数显示安装的每个版本。</span><span class="sxs-lookup"><span data-stu-id="3bc44-124">The **All-Versions** parameter displays each version that is installed.</span></span>

### <span data-ttu-id="3bc44-125">示例4：获取特定包的确切版本</span><span class="sxs-lookup"><span data-stu-id="3bc44-125">Example 4: Get an exact version of a specific package</span></span>

<span data-ttu-id="3bc44-126">此命令将获取已安装包的特定版本。</span><span class="sxs-lookup"><span data-stu-id="3bc44-126">This command gets a specific version of an installed package.</span></span> <span data-ttu-id="3bc44-127">可以安装多个版本的包。</span><span class="sxs-lookup"><span data-stu-id="3bc44-127">More than one version of a package can be installed.</span></span>

```powershell
Get-Package -Name PackageManagement -ProviderName PowerShellGet -RequiredVersion 1.3.1
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

<span data-ttu-id="3bc44-128">`Get-Package` 使用 **Name** 参数指定包名称 **PackageManagement** 。</span><span class="sxs-lookup"><span data-stu-id="3bc44-128">`Get-Package` uses **Name** parameter to specify the package name, **PackageManagement** .</span></span> <span data-ttu-id="3bc44-129">**ProviderName** 参数指定提供程序 **PowerShellGet** 。</span><span class="sxs-lookup"><span data-stu-id="3bc44-129">The **ProviderName** parameter specifies the provider, **PowerShellGet** .</span></span> <span data-ttu-id="3bc44-130">**必需的版本** 参数指定已安装的版本。</span><span class="sxs-lookup"><span data-stu-id="3bc44-130">The **Required-Version** parameter specifies an installed version.</span></span>

### <span data-ttu-id="3bc44-131">示例5：卸载包</span><span class="sxs-lookup"><span data-stu-id="3bc44-131">Example 5: Uninstall a package</span></span>

<span data-ttu-id="3bc44-132">此示例将获取包信息，然后卸载包。</span><span class="sxs-lookup"><span data-stu-id="3bc44-132">This example gets package information and then uninstalls the package.</span></span>

```powershell
Get-Package -Name posh-git -RequiredVersion 0.7.3 | Uninstall-Package
```

<span data-ttu-id="3bc44-133">`Get-Package` 使用 **Name** 参数指定包名称 **posh** 。</span><span class="sxs-lookup"><span data-stu-id="3bc44-133">`Get-Package` uses the **Name** parameter to specify the package name, **posh-git** .</span></span> <span data-ttu-id="3bc44-134">**RequiredVersion** 参数是包的特定版本。</span><span class="sxs-lookup"><span data-stu-id="3bc44-134">The **RequiredVersion** parameter is a specific version of the package.</span></span> <span data-ttu-id="3bc44-135">对象通过管道向下发送到 `Uninstall-Package` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3bc44-135">The object is sent down the pipeline to the `Uninstall-Package` cmdlet.</span></span> <span data-ttu-id="3bc44-136">`Uninstall-Package` 删除包。</span><span class="sxs-lookup"><span data-stu-id="3bc44-136">`Uninstall-Package` removes the package.</span></span>

## <span data-ttu-id="3bc44-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3bc44-137">PARAMETERS</span></span>

### <span data-ttu-id="3bc44-138">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="3bc44-138">-AllowClobber</span></span>

<span data-ttu-id="3bc44-139">替代与现有命令冲突有关的警告消息。</span><span class="sxs-lookup"><span data-stu-id="3bc44-139">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="3bc44-140">覆盖与模块安装的命令同名的现有命令。</span><span class="sxs-lookup"><span data-stu-id="3bc44-140">Overwrites existing commands that have the same name as commands being installed by a module.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3bc44-141">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="3bc44-141">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="3bc44-142">在结果中包括标记为预发行版本的包。</span><span class="sxs-lookup"><span data-stu-id="3bc44-142">Includes packages marked as a prerelease in the results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3bc44-143">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="3bc44-143">-AllVersions</span></span>

<span data-ttu-id="3bc44-144">指示 `Get-Package` 返回包的所有可用版本。</span><span class="sxs-lookup"><span data-stu-id="3bc44-144">Indicates that `Get-Package` returns all available versions of the package.</span></span> <span data-ttu-id="3bc44-145">默认情况下， `Get-Package` 仅返回最新的可用版本。</span><span class="sxs-lookup"><span data-stu-id="3bc44-145">By default, `Get-Package` only returns the newest available version.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3bc44-146">-Destination</span><span class="sxs-lookup"><span data-stu-id="3bc44-146">-Destination</span></span>

<span data-ttu-id="3bc44-147">指定包含提取的包文件的目录的路径。</span><span class="sxs-lookup"><span data-stu-id="3bc44-147">Specifies the path to a directory that contains extracted package files.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3bc44-148">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="3bc44-148">-ExcludeVersion</span></span>

<span data-ttu-id="3bc44-149">切换到排除文件夹路径中的版本号。</span><span class="sxs-lookup"><span data-stu-id="3bc44-149">Switch to exclude the version number in the folder path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3bc44-150">-Force</span><span class="sxs-lookup"><span data-stu-id="3bc44-150">-Force</span></span>

<span data-ttu-id="3bc44-151">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="3bc44-151">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3bc44-152">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="3bc44-152">-ForceBootstrap</span></span>

<span data-ttu-id="3bc44-153">指示 `Get-Package` 强制 **PackageManagement** 自动安装包提供程序。</span><span class="sxs-lookup"><span data-stu-id="3bc44-153">Indicates that `Get-Package` forces **PackageManagement** to automatically install the package provider.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3bc44-154">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="3bc44-154">-InstallUpdate</span></span>

<span data-ttu-id="3bc44-155">指示此 cmdlet 安装更新。</span><span class="sxs-lookup"><span data-stu-id="3bc44-155">Indicates that this cmdlet installs updates.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3bc44-156">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="3bc44-156">-MaximumVersion</span></span>

<span data-ttu-id="3bc44-157">指定要查找的最大包版本。</span><span class="sxs-lookup"><span data-stu-id="3bc44-157">Specifies the maximum package version that you want to find.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3bc44-158">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="3bc44-158">-MinimumVersion</span></span>

<span data-ttu-id="3bc44-159">指定要查找的最小包版本。</span><span class="sxs-lookup"><span data-stu-id="3bc44-159">Specifies the minimum package version that you want to find.</span></span> <span data-ttu-id="3bc44-160">如果有更高版本，则返回该版本。</span><span class="sxs-lookup"><span data-stu-id="3bc44-160">If a higher version is available, that version is returned.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3bc44-161">-Name</span><span class="sxs-lookup"><span data-stu-id="3bc44-161">-Name</span></span>

<span data-ttu-id="3bc44-162">指定一个或多个包名称或包名称，其中包含通配符。</span><span class="sxs-lookup"><span data-stu-id="3bc44-162">Specifies one or more package names, or package names with wildcard characters.</span></span> <span data-ttu-id="3bc44-163">用逗号分隔多个包名称。</span><span class="sxs-lookup"><span data-stu-id="3bc44-163">Separate multiple package names with commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="3bc44-164">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="3bc44-164">-NoPathUpdate</span></span>

<span data-ttu-id="3bc44-165">**NoPathUpdate** 仅适用于 `Install-Script` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3bc44-165">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="3bc44-166">**NoPathUpdate** 是由提供程序添加的动态参数，不受支持 `Get-Package` 。</span><span class="sxs-lookup"><span data-stu-id="3bc44-166">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Get-Package`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3bc44-167">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="3bc44-167">-PackageManagementProvider</span></span>

<span data-ttu-id="3bc44-168">指定包管理提供程序的名称。</span><span class="sxs-lookup"><span data-stu-id="3bc44-168">Specifies the name of a package management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3bc44-169">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="3bc44-169">-ProviderName</span></span>

<span data-ttu-id="3bc44-170">指定一个或多个包提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="3bc44-170">Specifies one or more package provider names.</span></span> <span data-ttu-id="3bc44-171">用逗号分隔多个包提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="3bc44-171">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="3bc44-172">使用 `Get-PackageProvider` 获取可用包提供程序的列表。</span><span class="sxs-lookup"><span data-stu-id="3bc44-172">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3bc44-173">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="3bc44-173">-RequiredVersion</span></span>

<span data-ttu-id="3bc44-174">指定要查找的包的确切版本。</span><span class="sxs-lookup"><span data-stu-id="3bc44-174">Specifies the exact version of the package to find.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3bc44-175">-Scope</span><span class="sxs-lookup"><span data-stu-id="3bc44-175">-Scope</span></span>

<span data-ttu-id="3bc44-176">指定包的搜索范围。</span><span class="sxs-lookup"><span data-stu-id="3bc44-176">Specifies the search scope for the package.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3bc44-177">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="3bc44-177">-SkipDependencies</span></span>

<span data-ttu-id="3bc44-178">指定跳过查找任何包依赖关系的开关。</span><span class="sxs-lookup"><span data-stu-id="3bc44-178">Switch that specifies to skip finding any package dependencies.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3bc44-179">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="3bc44-179">-SkipPublisherCheck</span></span>

<span data-ttu-id="3bc44-180">允许你获取比你安装的版本更新的包版本。</span><span class="sxs-lookup"><span data-stu-id="3bc44-180">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="3bc44-181">例如，由受信任的发布者进行数字签名，但未对新版本进行数字签名的已安装包。</span><span class="sxs-lookup"><span data-stu-id="3bc44-181">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3bc44-182">-Type</span><span class="sxs-lookup"><span data-stu-id="3bc44-182">-Type</span></span>

<span data-ttu-id="3bc44-183">指定是使用模块、脚本还是搜索包。</span><span class="sxs-lookup"><span data-stu-id="3bc44-183">Specifies whether to search for packages with a module, a script, or either.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3bc44-184">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3bc44-184">CommonParameters</span></span>

<span data-ttu-id="3bc44-185">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3bc44-185">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3bc44-186">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="3bc44-186">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3bc44-187">输入</span><span class="sxs-lookup"><span data-stu-id="3bc44-187">INPUTS</span></span>

## <span data-ttu-id="3bc44-188">输出</span><span class="sxs-lookup"><span data-stu-id="3bc44-188">OUTPUTS</span></span>

### <span data-ttu-id="3bc44-189">SoftwareIdentity[]</span><span class="sxs-lookup"><span data-stu-id="3bc44-189">SoftwareIdentity[]</span></span>

## <span data-ttu-id="3bc44-190">注释</span><span class="sxs-lookup"><span data-stu-id="3bc44-190">NOTES</span></span>

<span data-ttu-id="3bc44-191">在命令中包含包提供程序可以使动态参数可用于 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3bc44-191">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="3bc44-192">动态参数特定于包提供程序。</span><span class="sxs-lookup"><span data-stu-id="3bc44-192">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="3bc44-193">`Get-Help`Cmdlet 列出 cmdlet 的参数集，并包括提供程序的参数集。</span><span class="sxs-lookup"><span data-stu-id="3bc44-193">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="3bc44-194">例如， `Get-Package` 具有 **PowerShellGet** 参数集，其中包括 `-NoPathUpdate` 、 `AllowClobber` 和 `SkipPublisherCheck` 。</span><span class="sxs-lookup"><span data-stu-id="3bc44-194">For example, `Get-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

## <span data-ttu-id="3bc44-195">相关链接</span><span class="sxs-lookup"><span data-stu-id="3bc44-195">RELATED LINKS</span></span>

[<span data-ttu-id="3bc44-196">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="3bc44-196">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="3bc44-197">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="3bc44-197">Enter-PSSession</span></span>](../Microsoft.PowerShell.Core/Enter-PSSession.md)

[<span data-ttu-id="3bc44-198">Find-Package</span><span class="sxs-lookup"><span data-stu-id="3bc44-198">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="3bc44-199">Get-Help</span><span class="sxs-lookup"><span data-stu-id="3bc44-199">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="3bc44-200">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="3bc44-200">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="3bc44-201">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="3bc44-201">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="3bc44-202">Install-Package</span><span class="sxs-lookup"><span data-stu-id="3bc44-202">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="3bc44-203">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="3bc44-203">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="3bc44-204">Save-Package</span><span class="sxs-lookup"><span data-stu-id="3bc44-204">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="3bc44-205">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="3bc44-205">Uninstall-Package</span></span>](Uninstall-Package.md)