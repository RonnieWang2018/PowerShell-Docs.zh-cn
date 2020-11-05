---
ms.date: 12/12/2018
keywords: dsc,powershell,资源,库,安装程序
title: 安装其他 DSC 资源
description: 本文列出了包含在 PSDesiredStateConfiguration 模块中的 DSC 资源。 还介绍了如何查找和安装 PowerShell 库中的资源。
ms.openlocfilehash: e75561ed539e06716c9a103f905b9d1e4f3e71d3
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645125"
---
# <a name="install-additional-dsc-resources"></a><span data-ttu-id="ce5d0-105">安装其他 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="ce5d0-105">Install Additional DSC Resources</span></span>

<span data-ttu-id="ce5d0-106">PowerShell 包括 Desired State Configuration (DSC) 的多个现成资源。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-106">PowerShell includes several Out-of-the-box resources for Desired State Configuration (DSC).</span></span> <span data-ttu-id="ce5d0-107">PSDesiredStateConfiguration 模块包含特定 PowerShell 实例上可用的所有 OOB DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-107">The **PSDesiredStateConfiguration** module contains all of the OOB DSC resources available on your specific instance of PowerShell.</span></span>

<span data-ttu-id="ce5d0-108">这是包含在 PowerShell 4.0 中的 OOB 资源的列表以及资源功能的说明。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-108">This is a list of the OOB resources included in PowerShell 4.0 and a description of the resource's capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="ce5d0-109">此列表不完整，因为每个 PowerShell 版本都会增加 OOB 资源的数量。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-109">This is an incomplete list, as the number of OOB resources has grown with each version of PowerShell.</span></span>

|      <span data-ttu-id="ce5d0-110">资源</span><span class="sxs-lookup"><span data-stu-id="ce5d0-110">Resource</span></span>      |                                                                                       <span data-ttu-id="ce5d0-111">说明</span><span class="sxs-lookup"><span data-stu-id="ce5d0-111">Description</span></span>                                                                                        |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="ce5d0-112">**File**</span><span class="sxs-lookup"><span data-stu-id="ce5d0-112">**File**</span></span>           | <span data-ttu-id="ce5d0-113">控制文件和目录的状态。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-113">Controls the state of files and directories.</span></span> <span data-ttu-id="ce5d0-114">将文件从“源”复制到“目标”，然后在通过比较日期、校验和以及哈希确认“源”发生更改时更新这些文件。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-114">Copies files from a **Source** to a **Destination** and updates them when the **Source** changes by comparing dates, checksums, and hashes.</span></span> |
| <span data-ttu-id="ce5d0-115">**存档**</span><span class="sxs-lookup"><span data-stu-id="ce5d0-115">**Archive**</span></span>        | <span data-ttu-id="ce5d0-116">在指定位置解压缩存档。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-116">Unpacks archives and a specified location.</span></span> <span data-ttu-id="ce5d0-117">使用指定校验和验证存档。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-117">Validates the archives with a specified **Checksum**.</span></span>                                                                                         |
| <span data-ttu-id="ce5d0-118">**环境**</span><span class="sxs-lookup"><span data-stu-id="ce5d0-118">**Environment**</span></span>    | <span data-ttu-id="ce5d0-119">管理环境变量。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-119">Manages environment variables.</span></span>                                                                                                                                                           |
| <span data-ttu-id="ce5d0-120">**组**</span><span class="sxs-lookup"><span data-stu-id="ce5d0-120">**Group**</span></span>          | <span data-ttu-id="ce5d0-121">管理本地组并控制组成员身份。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-121">Manages local groups and controls group membership.</span></span>                                                                                                                                      |
| <span data-ttu-id="ce5d0-122">**日志**</span><span class="sxs-lookup"><span data-stu-id="ce5d0-122">**Log**</span></span>            | <span data-ttu-id="ce5d0-123">将消息写入 `Microsoft-Windows-Desired State Configuration/Analytic` 事件日志。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-123">Writes messages to the `Microsoft-Windows-Desired State Configuration/Analytic` event log.</span></span>                                                                                               |
| <span data-ttu-id="ce5d0-124">**包**</span><span class="sxs-lookup"><span data-stu-id="ce5d0-124">**Package**</span></span>        | <span data-ttu-id="ce5d0-125">使用 Arguments、LogPath、ReturnCode 和其他设置安装或卸载包。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-125">Installs or uninstalls packages using **Arguments** , **LogPath** , **ReturnCode** , other settings.</span></span>                                                                                        |
| <span data-ttu-id="ce5d0-126">**注册表**</span><span class="sxs-lookup"><span data-stu-id="ce5d0-126">**Registry**</span></span>       | <span data-ttu-id="ce5d0-127">管理注册表项和值。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-127">Manages registry keys and values.</span></span>                                                                                                                                                        |
| <span data-ttu-id="ce5d0-128">**脚本**</span><span class="sxs-lookup"><span data-stu-id="ce5d0-128">**Script**</span></span>         | <span data-ttu-id="ce5d0-129">可用于设计自己的 [get-test-set](../resources/get-test-set.md) 脚本块。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-129">Allows you to design your own [get-test-set](../resources/get-test-set.md) script blocks.</span></span>                                                                                                |
| <span data-ttu-id="ce5d0-130">**服务**</span><span class="sxs-lookup"><span data-stu-id="ce5d0-130">**Service**</span></span>        | <span data-ttu-id="ce5d0-131">配置 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-131">Configures Windows services.</span></span>                                                                                                                                                             |
| <span data-ttu-id="ce5d0-132">**User**</span><span class="sxs-lookup"><span data-stu-id="ce5d0-132">**User**</span></span>           | <span data-ttu-id="ce5d0-133">管理本地用户和属性。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-133">Manages local users and attributes.</span></span>                                                                                                                                                      |
| <span data-ttu-id="ce5d0-134">**WindowsFeature**</span><span class="sxs-lookup"><span data-stu-id="ce5d0-134">**WindowsFeature**</span></span> | <span data-ttu-id="ce5d0-135">管理角色和功能。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-135">Manages roles and features.</span></span>                                                                                                                                                              |
| <span data-ttu-id="ce5d0-136">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="ce5d0-136">**WindowsProcess**</span></span> | <span data-ttu-id="ce5d0-137">配置 Windows 进程。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-137">Configures Windows processes.</span></span>                                                                                                                                                            |

<span data-ttu-id="ce5d0-138">OOB 资源可为常见操作提供良好起点。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-138">The OOB resources allow a good starting point for common operations.</span></span> <span data-ttu-id="ce5d0-139">如果 OOB 资源不能满足你的需求，则可以写入自己的[自定义资源](../resources/authoringResource.md)。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-139">If the OOB resources do not meet your needs, you can write your own [Custom Resource](../resources/authoringResource.md).</span></span> <span data-ttu-id="ce5d0-140">在写入自定义资源以解决问题之前，应在已通过 Microsoft 和 PowerShell 社区创建的大量 DSC 资源中查找。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-140">Before you write a custom resource to solve your problem, you should look through the vast number of DSC resources that have already been created by both Microsoft and the PowerShell community.</span></span>

<span data-ttu-id="ce5d0-141">可以在 [PowerShell 库](https://www.powershellgallery.com/)和 [GitHub](https://github.com/) 中查找 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-141">You can find DSC resources in both the [PowerShell Gallery](https://www.powershellgallery.com/) and [GitHub](https://github.com/).</span></span> <span data-ttu-id="ce5d0-142">还可以直接从 PowerShell 控制台使用 [PowerShellGet](/powershell/module/powershellget/) 安装 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-142">You can also install DSC resources directly from the PowerShell console using [PowerShellGet](/powershell/module/powershellget/).</span></span>

## <a name="installing-powershellget"></a><span data-ttu-id="ce5d0-143">安装 PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="ce5d0-143">Installing PowerShellGet</span></span>

<span data-ttu-id="ce5d0-144">若要确定是否已获得 PowerShell，或者若要获取安装它的帮助，请参阅以下指南：[安装 PowerShellGet](/powershell/scripting/gallery/installing-psget)。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-144">To determine if you already have **PowerShell** get, or to get help installing it, see the following guide: [Installing PowerShellGet](/powershell/scripting/gallery/installing-psget).</span></span>

## <a name="finding-dsc-resources-using-powershellget"></a><span data-ttu-id="ce5d0-145">使用 PowerShellGet 查找 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="ce5d0-145">Finding DSC resources using PowerShellGet</span></span>

<span data-ttu-id="ce5d0-146">在系统上安装 PowerShellGet 后，可以找到并安装 [PowerShell 库](https://www.powershellgallery.com/)中托管的 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-146">Once **PowerShellGet** is installed on your system, you can find and install DSC resources hosted in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

<span data-ttu-id="ce5d0-147">首先，使用 [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet 查找 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-147">First, use the [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet to find DSC resources.</span></span> <span data-ttu-id="ce5d0-148">首次运行 `Find-DSCResource` 时，你会看到安装“NuGet 提供程序”的提示。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-148">When you run `Find-DSCResource` for the first time, you see the following prompt to install the "NuGet provider".</span></span>

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based
repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies'
or 'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install
the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201
-Force'. Do you want PowerShellGet to install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

<span data-ttu-id="ce5d0-149">按“y”后，将安装“NuGet”提供程序，随后会看到可从 PowerShell 库安装的 DSC 资源的列表。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-149">After pressing 'y', the "NuGet" provider is installed, you see a list of DSC resources that you can install from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="ce5d0-150">由于列表非常大，因此不会显示。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-150">List is not shown because it is very large.</span></span>

<span data-ttu-id="ce5d0-151">还可以使用通配符指定 `-Name` 参数或指定不带通配符的 `-Filter` 参数来缩小搜索范围。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-151">You can also specify the `-Name` parameter using wildcards, or `-Filter` parameter without wildcards to narrow down your search.</span></span> <span data-ttu-id="ce5d0-152">此示例尝试使用通配符查找“TimeZone”DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-152">This example attempts to find a "TimeZone" DSC resource using the wildcards.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ce5d0-153">当前在 `Find-DSCResource` cmdlet 中有一个 bug，会阻止在 `-Name` 和 `-Filter` 参数中使用通配符。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-153">Currently there is a bug in the `Find-DSCResource` cmdlet that prevents using wildcards in both the `-Name` and `-Filter` parameters.</span></span> <span data-ttu-id="ce5d0-154">下面的第二个示例显示了使用 `Where-Object` 的解决方法。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-154">The second example below shows a workaround using `Where-Object`.</span></span>

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

<span data-ttu-id="ce5d0-155">还可以使用 `Where-Object` 通过更精细的筛选来查找 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-155">You can also use `Where-Object` to find DSC resources with more granular filtering.</span></span> <span data-ttu-id="ce5d0-156">此方法的速度慢于使用内置筛选参数的速度。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-156">This approach will be slower than using built in filtering parameters.</span></span>

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

<span data-ttu-id="ce5d0-157">有关筛选的详细信息，请参阅 [Where-Object](/powershell/module/microsoft.powershell.core/where-object)。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-157">For more information on filtering, see [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span>

## <a name="installing-dsc-resources-using-powershellget"></a><span data-ttu-id="ce5d0-158">使用 PowerShellGet 安装 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="ce5d0-158">Installing DSC Resources using PowerShellGet</span></span>

<span data-ttu-id="ce5d0-159">若要安装 DSC 资源，请使用 [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet，指定搜索结果中“模块”名称下显示的模块名称。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-159">To install a DSC resource, use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, specifying the name of the module shown under **Module** name in your search results.</span></span>

<span data-ttu-id="ce5d0-160">“TimeZone”资源存在于“ComputerManagementDSC”模块中，因此这是此示例安装的模块。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-160">The "TimeZone" resource exists in the "ComputerManagementDSC" module, so that is the module this example installs.</span></span>

> [!NOTE]
> <span data-ttu-id="ce5d0-161">如果未信任 PowerShell 库，则会看到下面要求确认的警告，并指示如何避免安装时的后续提示。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-161">If you have not trusted the PowerShell gallery, you see the warning below asking for confirmation, and instructing you how to avoid subsequent prompts on installs.</span></span>

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change
its InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to
install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="ce5d0-162">按“y”以继续安装模块。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-162">Press 'y' to continue installing the module.</span></span> <span data-ttu-id="ce5d0-163">安装后，可以验证新资源是否是使用 [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) 安装的。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-163">After install, you can verify that your new resource is installed using [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span></span>

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

<span data-ttu-id="ce5d0-164">还可以通过指定 `-ModuleName` 参数来查看新安装的模块中的其他资源。</span><span class="sxs-lookup"><span data-stu-id="ce5d0-164">You can also view other resources in your newly installed module, by specifying the `-ModuleName` parameter.</span></span>

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a><span data-ttu-id="ce5d0-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ce5d0-165">See also</span></span>

- [<span data-ttu-id="ce5d0-166">什么是资源？</span><span class="sxs-lookup"><span data-stu-id="ce5d0-166">What are Resources?</span></span>](../resources/resources.md)
