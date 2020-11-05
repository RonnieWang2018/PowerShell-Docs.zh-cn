---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: PowerShell Desired State Configuration 部分配置
description: DSC 允许从多个源中以片段形式提交配置。 目标节点上的 LCM 将碎片整理到一起，然后将其作为单个配置进行应用。
ms.openlocfilehash: 3afe5d684cabec9c8ab528347610b6dd00c5d4e9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661603"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a><span data-ttu-id="72e2e-105">PowerShell Desired State Configuration 部分配置</span><span class="sxs-lookup"><span data-stu-id="72e2e-105">PowerShell Desired State Configuration partial configurations</span></span>

> <span data-ttu-id="72e2e-106">适用于：Windows PowerShell 5.0 及更高版本。</span><span class="sxs-lookup"><span data-stu-id="72e2e-106">Applies To: Windows PowerShell 5.0 and later.</span></span>

<span data-ttu-id="72e2e-107">在 PowerShell 5.0 中，Desired State Configuration (DSC) 允许从多个源中以片段形式提交配置。</span><span class="sxs-lookup"><span data-stu-id="72e2e-107">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span></span> <span data-ttu-id="72e2e-108">目标节点上的本地配置管理器 (LCM) 将碎片整理到一起，然后将其作为单个配置进行应用。</span><span class="sxs-lookup"><span data-stu-id="72e2e-108">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span></span> <span data-ttu-id="72e2e-109">此功能允许在团队或个人之间共享配置控制权。</span><span class="sxs-lookup"><span data-stu-id="72e2e-109">This capability allows sharing control of configuration between teams or individuals.</span></span> <span data-ttu-id="72e2e-110">例如，如果两个或更多开发人员团队协作提供一项服务，那么每个团队都可以创建配置来管理该服务中由其负责的部分。</span><span class="sxs-lookup"><span data-stu-id="72e2e-110">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span></span> <span data-ttu-id="72e2e-111">可以从不同请求服务器请求其中每个配置，并可以在各个开发阶段加入这些配置。</span><span class="sxs-lookup"><span data-stu-id="72e2e-111">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span></span> <span data-ttu-id="72e2e-112">部分配置还允许不同的个人或团队控制配置节点的不同方面，而无需协调单个配置文档的编辑。</span><span class="sxs-lookup"><span data-stu-id="72e2e-112">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span></span> <span data-ttu-id="72e2e-113">例如，可能由一个团队负责部署 VM 和操作系统，而由另一个团队负责在该 VM 上部署其它应用程序和服务。</span><span class="sxs-lookup"><span data-stu-id="72e2e-113">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span></span> <span data-ttu-id="72e2e-114">使用部分配置，每个团队都可以创建自己的配置，避免任何不必要的复杂配置。</span><span class="sxs-lookup"><span data-stu-id="72e2e-114">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span></span>

<span data-ttu-id="72e2e-115">可以在推送模式、请求模式或两种模式的组合下使用部分配置。</span><span class="sxs-lookup"><span data-stu-id="72e2e-115">You can use partial configurations in push mode, pull mode, or a combination of the two.</span></span>

## <a name="partial-configurations-in-push-mode"></a><span data-ttu-id="72e2e-116">推送模式下的部分配置</span><span class="sxs-lookup"><span data-stu-id="72e2e-116">Partial configurations in push mode</span></span>

<span data-ttu-id="72e2e-117">若要在推送模式下使用部分配置，你需要在目标节点上配置 LCM 以接收部分配置。</span><span class="sxs-lookup"><span data-stu-id="72e2e-117">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span></span> <span data-ttu-id="72e2e-118">必须使用 `Publish-DSCConfiguration` cmdlet 将每个部分配置推送到目标。</span><span class="sxs-lookup"><span data-stu-id="72e2e-118">Each partial configuration must be pushed to the target by using the `Publish-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="72e2e-119">然后，目标节点将部分配置组合成为单个配置。你可以通过调用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet 来应用配置。</span><span class="sxs-lookup"><span data-stu-id="72e2e-119">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a><span data-ttu-id="72e2e-120">针对推送模式部分配置来配置 LCM</span><span class="sxs-lookup"><span data-stu-id="72e2e-120">Configuring the LCM for push-mode partial configurations</span></span>

<span data-ttu-id="72e2e-121">若要针对推送模式下的部分配置来配置 LCM，你可以为每个部分配置创建带有一个 **PartialConfiguration** 块的 **DSCLocalConfigurationManager** 配置。</span><span class="sxs-lookup"><span data-stu-id="72e2e-121">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span></span> <span data-ttu-id="72e2e-122">有关配置 LCM 的详细信息，请参阅 [Windows 配置本地配置管理器](../managing-nodes/metaConfig.md)。</span><span class="sxs-lookup"><span data-stu-id="72e2e-122">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span> <span data-ttu-id="72e2e-123">下面的示例显示了需要两个部分配置的 LCM 配置：一个用于部署操作系统，另一个用于部署和配置 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="72e2e-123">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {

        PartialConfiguration ServiceAccountConfig
        {
            Description = 'Configuration to add the SharePoint service account to the Administrators group.'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}

PartialConfigDemo
```

<span data-ttu-id="72e2e-124">每个部分配置的 **RefreshMode** 都设置为“Push”。</span><span class="sxs-lookup"><span data-stu-id="72e2e-124">The **RefreshMode** for each partial configuration is set to "Push".</span></span> <span data-ttu-id="72e2e-125">**PartialConfiguration** 块的名称（在本例中即“ServiceAccountConfig”和“SharePointConfig”）必须与推送到目标节点的配置名称完全匹配。</span><span class="sxs-lookup"><span data-stu-id="72e2e-125">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span></span>

> [!Note]
> <span data-ttu-id="72e2e-126">每个 PartialConfiguration 块的名称都必须与配置脚本中指定的配置实际名称匹配，而不是与 MOF 文件的名称（这应是目标节点的名称或 `localhost`）匹配。</span><span class="sxs-lookup"><span data-stu-id="72e2e-126">The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span></span>

### <a name="publishing-and-starting-push-mode-partial-configurations"></a><span data-ttu-id="72e2e-127">发布和启动推送模式部分配置</span><span class="sxs-lookup"><span data-stu-id="72e2e-127">Publishing and starting push-mode partial configurations</span></span>

<span data-ttu-id="72e2e-128">然后，可以对每个配置调用 [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)，将包含配置文档的文件夹作为 **Path** 参数进行传递。</span><span class="sxs-lookup"><span data-stu-id="72e2e-128">You then call [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span></span> <span data-ttu-id="72e2e-129">`Publish-DSCConfiguration`将配置 MOF 文件放置到目标节点。</span><span class="sxs-lookup"><span data-stu-id="72e2e-129">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span></span> <span data-ttu-id="72e2e-130">发布两个配置后，即可在目标节点上调用 `Start-DSCConfiguration –UseExisting`。</span><span class="sxs-lookup"><span data-stu-id="72e2e-130">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span></span>

<span data-ttu-id="72e2e-131">例如，如果你在创作节点上编译了以下配置 MOF 文档：</span><span class="sxs-lookup"><span data-stu-id="72e2e-131">For example, if you have compiled the following configuration MOF documents on the authoring node:</span></span>

```powershell
Get-ChildItem -Recurse
```

```output
    Directory: C:\PartialConfigTest

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        8/11/2016   1:55 PM                ServiceAccountConfig
d-----       11/17/2016   4:14 PM                SharePointConfig

    Directory: C:\PartialConfigTest\ServiceAccountConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/11/2016   2:02 PM           2034 TestVM.mof

    Directory: C:\PartialConfigTest\SharePointConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

<span data-ttu-id="72e2e-132">你会发布和运行如下所示的配置：</span><span class="sxs-lookup"><span data-stu-id="72e2e-132">You would publish and run the configurations as follows:</span></span>

```powershell
Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
Start-DscConfiguration -UseExisting -ComputerName 'TestVM'
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

> [!Note]
> <span data-ttu-id="72e2e-133">运行 [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet 的用户必须在目标节点上拥有管理员权限。</span><span class="sxs-lookup"><span data-stu-id="72e2e-133">The user running the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet must have administrator privileges on the target node.</span></span>

## <a name="partial-configurations-in-pull-mode"></a><span data-ttu-id="72e2e-134">请求模式下的部分配置</span><span class="sxs-lookup"><span data-stu-id="72e2e-134">Partial configurations in pull mode</span></span>

<span data-ttu-id="72e2e-135">可以从一个或多个请求服务器请求部分配置（有关请求服务器的详细信息，请参阅 [Windows PowerShell Desired State Configuration 请求服务器](pullServer.md)）。</span><span class="sxs-lookup"><span data-stu-id="72e2e-135">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="72e2e-136">若要执行此操作，必须在要请求部分配置的目标节点上配置 LCM，并在请求服务器上正确命名和定位配置文档。</span><span class="sxs-lookup"><span data-stu-id="72e2e-136">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span></span>

### <a name="configuring-the-lcm-for-pull-node-configurations"></a><span data-ttu-id="72e2e-137">针对请求节点配置来配置 LCM</span><span class="sxs-lookup"><span data-stu-id="72e2e-137">Configuring the LCM for pull node configurations</span></span>

<span data-ttu-id="72e2e-138">若要配置 LCM 以从请求服务器请求部分配置，你需要在 **ConfigurationRepositoryWeb** （适用于 HTTP 请求服务器）或者 **ConfigurationRepositoryShare** （适用于 SMB 请求服务器）块上定义请求服务器。</span><span class="sxs-lookup"><span data-stu-id="72e2e-138">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span></span> <span data-ttu-id="72e2e-139">然后创建 **PartialConfiguration** 块，这些块通过使用 **ConfigurationSource** 属性引用请求服务器。</span><span class="sxs-lookup"><span data-stu-id="72e2e-139">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span></span> <span data-ttu-id="72e2e-140">你还需创建 **设置** 块来指定 LCM 使用请求模式，并指定请求服务器和目标节点用于识别配置的 **ConfigurationNames** 或者 **ConfigurationID** 。</span><span class="sxs-lookup"><span data-stu-id="72e2e-140">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span></span> <span data-ttu-id="72e2e-141">下面的元配置定义了名为 CONTOSO-PullSrv 的 HTTP 请求服务器，以及使用该请求服务器的两个部分配置。</span><span class="sxs-lookup"><span data-stu-id="72e2e-141">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span></span>

<span data-ttu-id="72e2e-142">有关使用 **ConfigurationNames** 配置 LCM 的详细信息，请参阅 [使用配置名称设置请求客户端](pullClientConfigNames.md)。</span><span class="sxs-lookup"><span data-stu-id="72e2e-142">For more information about configuring the LCM using **ConfigurationNames** , see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span></span> <span data-ttu-id="72e2e-143">有关使用 **ConfigurationID** 配置 LCM 的详细信息，请参阅 [使用配置 ID 设置请求客户端](pullClientConfigID.md)。</span><span class="sxs-lookup"><span data-stu-id="72e2e-143">For information about configuring the LCM using **ConfigurationID** , see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a><span data-ttu-id="72e2e-144">使用配置名称针对配置模式配置来配置 LCM</span><span class="sxs-lookup"><span data-stu-id="72e2e-144">Configuring the LCM for pull mode configurations using configuration names</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               ="ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
        }
}
```

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a><span data-ttu-id="72e2e-145">使用配置 ID 针对配置模式配置来配置 LCM</span><span class="sxs-lookup"><span data-stu-id="72e2e-145">Configuring the LCM for pull mode configurations using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemoConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode                     = 'Pull'
            ConfigurationID                 = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins            = 30
            RebootNodeIfNeeded              = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description                     = 'Configuration for the Base OS'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode                     = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description                     = 'Configuration for the Sharepoint Server'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Pull'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="72e2e-146">你可以从多个请求服务器请求部分配置：定义每个请求服务器，然后在每个 **PartialConfiguration** 块中引用相应请求服务器即可。</span><span class="sxs-lookup"><span data-stu-id="72e2e-146">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span></span>

<span data-ttu-id="72e2e-147">创建元配置后，必须运行该元配置以创建配置文档（MOF 文件），然后调用 [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) 以配置 LCM。</span><span class="sxs-lookup"><span data-stu-id="72e2e-147">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) to configure the LCM.</span></span>

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a><span data-ttu-id="72e2e-148">在请求服务器 (ConfigurationNames) 上命名和放置配置文档</span><span class="sxs-lookup"><span data-stu-id="72e2e-148">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span></span>

<span data-ttu-id="72e2e-149">必须将部分配置文档置于请求服务器的 `web.config` 文件中指定为 **ConfigurationPath** 的文件夹中（通常为 `C:\Program
Files\WindowsPowerShell\DscService\Configuration`）。</span><span class="sxs-lookup"><span data-stu-id="72e2e-149">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a><span data-ttu-id="72e2e-150">在 PowerShell 5.1 中的拉取服务器上命名配置文档</span><span class="sxs-lookup"><span data-stu-id="72e2e-150">Naming configuration documents on the pull server in PowerShell 5.1</span></span>

<span data-ttu-id="72e2e-151">如果只要从单个拉取服务器中拉取一个部分配置，可以对配置文档进行任意命名。</span><span class="sxs-lookup"><span data-stu-id="72e2e-151">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span></span> <span data-ttu-id="72e2e-152">如果要从拉取服务器中拉取多个部分配置，可以将配置文档命名为 `<ConfigurationName>.mof`（其中 ConfigurationName 是部分配置的名称）或 `<ConfigurationName>.<NodeName>.mof`（其中 ConfigurationName 是部分配置的名称，NodeName 是目标节点的名称）。</span><span class="sxs-lookup"><span data-stu-id="72e2e-152">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where *ConfigurationName* is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where *ConfigurationName* is the name of the partial configuration, and *NodeName* is the name of the target node.</span></span> <span data-ttu-id="72e2e-153">这样一来，便可以从 Azure Automation DSC 拉取服务器中拉取配置。</span><span class="sxs-lookup"><span data-stu-id="72e2e-153">This allows you to pull configurations from Azure Automation DSC pull server.</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a><span data-ttu-id="72e2e-154">在 PowerShell 5.0 中的拉取服务器上命名配置文档</span><span class="sxs-lookup"><span data-stu-id="72e2e-154">Naming configuration documents on the pull server in PowerShell 5.0</span></span>

<span data-ttu-id="72e2e-155">配置文档必须按如下所示命名：`ConfigurationName.mof`，其中 *ConfigurationName* 是部分配置的名称。</span><span class="sxs-lookup"><span data-stu-id="72e2e-155">The configuration documents must be named as follows: `ConfigurationName.mof`, where *ConfigurationName* is the name of the partial configuration.</span></span> <span data-ttu-id="72e2e-156">在本例中，配置文档应按如下所示命名：</span><span class="sxs-lookup"><span data-stu-id="72e2e-156">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a><span data-ttu-id="72e2e-157">在请求服务器 (ConfigurationID) 上命名和放置配置文档</span><span class="sxs-lookup"><span data-stu-id="72e2e-157">Naming and placing the configuration documents on the pull server (ConfigurationID)</span></span>

<span data-ttu-id="72e2e-158">必须将部分配置文档置于请求服务器的 `web.config` 文件中指定为 **ConfigurationPath** 的文件夹中（通常为 `C:\Program Files\WindowsPowerShell\DscService\Configuration`）。</span><span class="sxs-lookup"><span data-stu-id="72e2e-158">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> <span data-ttu-id="72e2e-159">配置文档必须按如下所示命名：`<ConfigurationName>.<ConfigurationID>.mof`，其中 ConfigurationName 是部分配置的名称，ConfigurationID 是目标节点上 LCM 中定义的配置 ID。</span><span class="sxs-lookup"><span data-stu-id="72e2e-159">The configuration documents must be named as follows: `<ConfigurationName>.<ConfigurationID>.mof`, where _ConfigurationName_ is the name of the partial configuration and _ConfigurationID_ is the configuration ID defined in the LCM on the target node.</span></span> <span data-ttu-id="72e2e-160">在本例中，配置文档应按如下所示命名：</span><span class="sxs-lookup"><span data-stu-id="72e2e-160">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a><span data-ttu-id="72e2e-161">从请求服务器上运行部分配置</span><span class="sxs-lookup"><span data-stu-id="72e2e-161">Running partial configurations from a pull server</span></span>

<span data-ttu-id="72e2e-162">在目标节点上配置 LCM，并在请求服务器上正确创建和命名配置文档后，目标节点将请求并合并部分配置，然后按照由 LCM 的 **RefreshFrequencyMins** 属性指定的固定时间间隔应用生成的配置。</span><span class="sxs-lookup"><span data-stu-id="72e2e-162">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="72e2e-163">如果想要强制进行刷新，则可以调用 [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) cmdlet 以请求配置，然后调用 `Start-DSCConfiguration –UseExisting` 以应用这些配置。</span><span class="sxs-lookup"><span data-stu-id="72e2e-163">If you want to force a refresh, you can call the [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span></span>

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a><span data-ttu-id="72e2e-164">推送与请求混合模式下的部分配置</span><span class="sxs-lookup"><span data-stu-id="72e2e-164">Partial configurations in mixed push and pull modes</span></span>

<span data-ttu-id="72e2e-165">你还可以混用推送和请求模式以进行部分配置。</span><span class="sxs-lookup"><span data-stu-id="72e2e-165">You can also mix push and pull modes for partial configurations.</span></span> <span data-ttu-id="72e2e-166">也就是说，你可以同时拥有一个从请求服务器请求的部分配置和另一个推送的部分配置。</span><span class="sxs-lookup"><span data-stu-id="72e2e-166">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span></span> <span data-ttu-id="72e2e-167">根据上文各部分所述，指定每个部分配置的刷新模式。</span><span class="sxs-lookup"><span data-stu-id="72e2e-167">Specify the refresh mode for each partial configuration as described in the previous sections.</span></span> <span data-ttu-id="72e2e-168">例如，还是以下面的元配置为例，其中 `ServiceAccountConfig` 部分配置处于拉取模式，`SharePointConfig` 部分配置处于推送模式。</span><span class="sxs-lookup"><span data-stu-id="72e2e-168">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span></span>

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a><span data-ttu-id="72e2e-169">使用 ConfigurationNames 的推送与请求混合模式</span><span class="sxs-lookup"><span data-stu-id="72e2e-169">Mixed push and pull modes using ConfigurationNames</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               = "ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            RefreshMode                     = 'Pull'
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Push'
        }

}
```

### <a name="mixed-push-and-pull-modes-using-configurationid"></a><span data-ttu-id="72e2e-170">使用 ConfigurationID 的推送与请求混合模式</span><span class="sxs-lookup"><span data-stu-id="72e2e-170">Mixed push and pull modes using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode             = 'Pull'
            ConfigurationID         = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins    = 30
            RebootNodeIfNeeded      = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL               = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description             = 'Configuration for the Base OS'
            ConfigurationSource     = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode             = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description             = 'Configuration for the Sharepoint Server'
            DependsOn               = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode             = 'Push'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="72e2e-171">请注意，Settings 块中指定的 **RefreshMode** 为“Pull”，而 `SharePointConfig` 部分配置的 **RefreshMode** 为“Push”。</span><span class="sxs-lookup"><span data-stu-id="72e2e-171">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span></span>

<span data-ttu-id="72e2e-172">可按照上文所述的相应刷新模式命名和放置配置 MOF 文件。</span><span class="sxs-lookup"><span data-stu-id="72e2e-172">Name and locate the configuration MOF files as described above for their respective refresh modes.</span></span>
<span data-ttu-id="72e2e-173">可调用 `Publish-DSCConfiguration` 来发布 `SharePointConfig` 部分配置，并等待从请求服务器请求 `ServiceAccountConfig` 配置或通过调用 [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) 强制进行刷新。</span><span class="sxs-lookup"><span data-stu-id="72e2e-173">Call `Publish-DSCConfiguration` to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span></span>

## <a name="example-serviceaccountconfig-partial-configuration"></a><span data-ttu-id="72e2e-174">ServiceAccountConfig 部分配置示例</span><span class="sxs-lookup"><span data-stu-id="72e2e-174">Example ServiceAccountConfig Partial Configuration</span></span>

```powershell
Configuration ServiceAccountConfig
{
    Param (
        [Parameter(Mandatory,
                   HelpMessage="Domain credentials required to add domain\sharepoint_svc to the local Administrators group.")]
        [ValidateNotNullOrEmpty()]
        [pscredential]$Credential
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Group LocalAdmins
        {
            GroupName           = 'Administrators'
            MembersToInclude    = 'domain\sharepoint_svc',
                                  'admins@example.domain'
            Ensure              = 'Present'
            Credential          = $Credential
        }

        WindowsFeature Telnet
        {
            Name                = 'Telnet-Server'
            Ensure              = 'Absent'
        }
    }
}
ServiceAccountConfig
```

## <a name="example-sharepointconfig-partial-configuration"></a><span data-ttu-id="72e2e-175">SharePointConfig 部分配置示例</span><span class="sxs-lookup"><span data-stu-id="72e2e-175">Example SharePointConfig Partial Configuration</span></span>

```powershell
Configuration SharePointConfig
{
    Param (
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [pscredential]$ProductKey
    )

    Import-DscResource -ModuleName xSharePoint

    Node localhost
    {
        xSPInstall SharePointDefault
        {
            Ensure      = 'Present'
            BinaryDir   = '\\FileServer\Installers\Sharepoint\'
            ProductKey  = $ProductKey
        }
    }
}
SharePointConfig
```

## <a name="see-also"></a><span data-ttu-id="72e2e-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="72e2e-176">See Also</span></span>

[<span data-ttu-id="72e2e-177">Windows PowerShell Desired State Configuration 请求服务器</span><span class="sxs-lookup"><span data-stu-id="72e2e-177">Windows PowerShell Desired State Configuration Pull Servers</span></span>](pullServer.md)

[<span data-ttu-id="72e2e-178">Windows 配置本地配置管理器</span><span class="sxs-lookup"><span data-stu-id="72e2e-178">Windows Configuring the Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
