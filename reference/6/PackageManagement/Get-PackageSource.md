---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 03/29/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packagesource?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageSource
ms.openlocfilehash: 8910f7b72d29614a9e92786ace517f99ee07fe76
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93198139"
---
# <span data-ttu-id="fadca-103">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="fadca-103">Get-PackageSource</span></span>

## <span data-ttu-id="fadca-104">摘要</span><span class="sxs-lookup"><span data-stu-id="fadca-104">SYNOPSIS</span></span>
<span data-ttu-id="fadca-105">获取为包提供程序注册的包源的列表。</span><span class="sxs-lookup"><span data-stu-id="fadca-105">Gets a list of package sources that are registered for a package provider.</span></span>

## <span data-ttu-id="fadca-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fadca-106">SYNTAX</span></span>

### <span data-ttu-id="fadca-107">NuGet</span><span class="sxs-lookup"><span data-stu-id="fadca-107">NuGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="fadca-108">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="fadca-108">PowerShellGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="fadca-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="fadca-109">DESCRIPTION</span></span>

<span data-ttu-id="fadca-110">该 `Get-PackageSource` cmdlet 将获取在本地计算机上向 **PackageManagement** 注册的包源的列表。</span><span class="sxs-lookup"><span data-stu-id="fadca-110">The `Get-PackageSource` cmdlet gets a list of package sources that are registered with **PackageManagement** on the local computer.</span></span> <span data-ttu-id="fadca-111">如果指定包提供程序，则 `Get-PackageSource` 仅获取与指定的提供程序关联的那些源。</span><span class="sxs-lookup"><span data-stu-id="fadca-111">If you specify a package provider, `Get-PackageSource` gets only those sources that are associated with the specified provider.</span></span> <span data-ttu-id="fadca-112">否则，该命令将返回已注册到 **PackageManagement** 的所有包源。</span><span class="sxs-lookup"><span data-stu-id="fadca-112">Otherwise, the command returns all package sources that are registered with **PackageManagement** .</span></span>

## <span data-ttu-id="fadca-113">示例</span><span class="sxs-lookup"><span data-stu-id="fadca-113">EXAMPLES</span></span>

### <span data-ttu-id="fadca-114">示例1：获取所有包源</span><span class="sxs-lookup"><span data-stu-id="fadca-114">Example 1: Get all package sources</span></span>

<span data-ttu-id="fadca-115">该 `Get-PackageSource` cmdlet 将获取在本地计算机上注册到 **PackageManagement** 的所有包源。</span><span class="sxs-lookup"><span data-stu-id="fadca-115">The `Get-PackageSource` cmdlet gets all package sources that are registered with **PackageManagement** on the local computer.</span></span>

```powershell
Get-PackageSource
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
PSGallery            PowerShellGet    False      https://www.powershellgallery.com/api/v2
```

### <span data-ttu-id="fadca-116">示例2：获取特定提供程序的所有包源</span><span class="sxs-lookup"><span data-stu-id="fadca-116">Example 2: Get all package sources for a specific provider</span></span>

<span data-ttu-id="fadca-117">此命令将获取为特定提供程序注册的包源。</span><span class="sxs-lookup"><span data-stu-id="fadca-117">This command gets package sources that are registered for a specific provider.</span></span>

```powershell
Get-PackageSource -ProviderName NuGet
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="fadca-118">`Get-PackageSource` 使用 **ProviderName** 参数获取为 **NuGet** 提供程序注册的包源。</span><span class="sxs-lookup"><span data-stu-id="fadca-118">`Get-PackageSource` uses the **ProviderName** parameter to get package sources that are registered for the **NuGet** provider.</span></span>

### <span data-ttu-id="fadca-119">示例3：从包提供程序获取源</span><span class="sxs-lookup"><span data-stu-id="fadca-119">Example 3: Get sources from a package provider</span></span>

<span data-ttu-id="fadca-120">此命令使用包提供程序获取包源。</span><span class="sxs-lookup"><span data-stu-id="fadca-120">This command uses a package provider to get package sources.</span></span>

```powershell
Get-PackageProvider -Name NuGet | Get-PackageSource
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="fadca-121">`Get-PackageProvider` 使用 **Name** 参数指定提供程序名称（ **NuGet** ）。</span><span class="sxs-lookup"><span data-stu-id="fadca-121">`Get-PackageProvider` uses the **Name** parameter specify the provider name, **NuGet** .</span></span> <span data-ttu-id="fadca-122">将对象向下发送到 `Get-PackageSource` 。</span><span class="sxs-lookup"><span data-stu-id="fadca-122">The object is sent down the pipeline to `Get-PackageSource`.</span></span>

## <span data-ttu-id="fadca-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fadca-123">PARAMETERS</span></span>

### <span data-ttu-id="fadca-124">-Read-configfile</span><span class="sxs-lookup"><span data-stu-id="fadca-124">-ConfigFile</span></span>

<span data-ttu-id="fadca-125">指定配置文件。</span><span class="sxs-lookup"><span data-stu-id="fadca-125">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="fadca-126">-Force</span><span class="sxs-lookup"><span data-stu-id="fadca-126">-Force</span></span>

<span data-ttu-id="fadca-127">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="fadca-127">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="fadca-128">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="fadca-128">-ForceBootstrap</span></span>

<span data-ttu-id="fadca-129">指示此 cmdlet 强制 **PackageManagement** 自动安装包提供程序。</span><span class="sxs-lookup"><span data-stu-id="fadca-129">Indicates that this cmdlet forces **PackageManagement** to automatically install a package provider.</span></span>

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

### <span data-ttu-id="fadca-130">-Location</span><span class="sxs-lookup"><span data-stu-id="fadca-130">-Location</span></span>

<span data-ttu-id="fadca-131">指定包管理源或存储库的位置。</span><span class="sxs-lookup"><span data-stu-id="fadca-131">Specifies the location of a package management source or repository.</span></span>

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

### <span data-ttu-id="fadca-132">-Name</span><span class="sxs-lookup"><span data-stu-id="fadca-132">-Name</span></span>

<span data-ttu-id="fadca-133">指定包管理源的名称。</span><span class="sxs-lookup"><span data-stu-id="fadca-133">Specifies the name of a package management source.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fadca-134">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="fadca-134">-PackageManagementProvider</span></span>

<span data-ttu-id="fadca-135">指定包管理提供程序。</span><span class="sxs-lookup"><span data-stu-id="fadca-135">Specifies a package management provider.</span></span>

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

### <span data-ttu-id="fadca-136">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="fadca-136">-ProviderName</span></span>

<span data-ttu-id="fadca-137">指定一个或多个包提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="fadca-137">Specifies one or more package provider names.</span></span> <span data-ttu-id="fadca-138">用逗号分隔多个包提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="fadca-138">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="fadca-139">使用 `Get-PackageProvider` 获取可用包提供程序的列表。</span><span class="sxs-lookup"><span data-stu-id="fadca-139">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

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

### <span data-ttu-id="fadca-140">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="fadca-140">-PublishLocation</span></span>

<span data-ttu-id="fadca-141">指定包源的发布位置。</span><span class="sxs-lookup"><span data-stu-id="fadca-141">Specifies the publish location for the package source.</span></span>

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

### <span data-ttu-id="fadca-142">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="fadca-142">-ScriptPublishLocation</span></span>

<span data-ttu-id="fadca-143">指定脚本发布位置。</span><span class="sxs-lookup"><span data-stu-id="fadca-143">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="fadca-144">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="fadca-144">-ScriptSourceLocation</span></span>

<span data-ttu-id="fadca-145">指定脚本源位置。</span><span class="sxs-lookup"><span data-stu-id="fadca-145">Specifies the script source location.</span></span>

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

### <span data-ttu-id="fadca-146">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="fadca-146">-SkipValidate</span></span>

<span data-ttu-id="fadca-147">跳过验证包源凭据的开关。</span><span class="sxs-lookup"><span data-stu-id="fadca-147">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="fadca-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fadca-148">CommonParameters</span></span>

<span data-ttu-id="fadca-149">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="fadca-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fadca-150">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="fadca-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fadca-151">输入</span><span class="sxs-lookup"><span data-stu-id="fadca-151">INPUTS</span></span>

## <span data-ttu-id="fadca-152">输出</span><span class="sxs-lookup"><span data-stu-id="fadca-152">OUTPUTS</span></span>

### <span data-ttu-id="fadca-153">Register-packagesource []</span><span class="sxs-lookup"><span data-stu-id="fadca-153">PackageSource[]</span></span>

<span data-ttu-id="fadca-154">指定一个或多个包源。</span><span class="sxs-lookup"><span data-stu-id="fadca-154">Specifies one or more package sources.</span></span>

## <span data-ttu-id="fadca-155">注释</span><span class="sxs-lookup"><span data-stu-id="fadca-155">NOTES</span></span>

## <span data-ttu-id="fadca-156">相关链接</span><span class="sxs-lookup"><span data-stu-id="fadca-156">RELATED LINKS</span></span>

[<span data-ttu-id="fadca-157">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="fadca-157">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="fadca-158">Find-Package</span><span class="sxs-lookup"><span data-stu-id="fadca-158">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="fadca-159">Get-Package</span><span class="sxs-lookup"><span data-stu-id="fadca-159">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="fadca-160">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="fadca-160">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="fadca-161">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="fadca-161">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="fadca-162">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="fadca-162">Set-PackageSource</span></span>](Set-PackageSource.md)

[<span data-ttu-id="fadca-163">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="fadca-163">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)