---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 使用配置 ID 发布到拉取服务器 (v4/v5)
description: 本文介绍了如何上传资源以供下载，以及如何将客户端配置为自动下载资源。
ms.openlocfilehash: 20e12e3cac6b6e4a86563576f4a915429b18aadb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646836"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="cfb8b-104">使用配置 ID 发布到拉取服务器 (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="cfb8b-104">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="cfb8b-105">以下部分假定你已设置拉取服务器。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-105">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="cfb8b-106">如果尚未设置拉取服务器，可以遵循以下指南：</span><span class="sxs-lookup"><span data-stu-id="cfb8b-106">If you haven't set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="cfb8b-107">设置 DSC SMB 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="cfb8b-107">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="cfb8b-108">设置 DSC HTTP 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="cfb8b-108">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="cfb8b-109">每个目标节点都可以配置为下载配置、资源，甚至是报告其状态。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-109">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="cfb8b-110">本文介绍了如何上传资源以供下载，以及如何将客户端配置为自动下载资源。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-110">This article shows you how to upload resources so they're available to be downloaded, and configure clients to automatically download resources.</span></span> <span data-ttu-id="cfb8b-111">如果节点通过“拉取”或“推送”(v5) 收到分配的配置，便会从本地配置管理器 (LCM) 中指定的位置自动下载配置所需的任何资源。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-111">When the node receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the Local Configuration Manager (LCM).</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="cfb8b-112">编译配置</span><span class="sxs-lookup"><span data-stu-id="cfb8b-112">Compile configurations</span></span>

<span data-ttu-id="cfb8b-113">将[配置](../configurations/configurations.md)存储在拉取服务器上的第一步是，将配置编译为 `.mof` 文件。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-113">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into `.mof` files.</span></span> <span data-ttu-id="cfb8b-114">若要使配置通用并适用于多个客户端，请使用节点块中的 `localhost`。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-114">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="cfb8b-115">下面的示例显示使用 `localhost`（而不是特定客户端名称）的配置 Shell。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-115">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="cfb8b-116">编译通用配置后，应该就会有 `localhost.mof` 文件。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-116">Once you've compiled your generic configuration, you should have a `localhost.mof` file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="cfb8b-117">重命名 MOF 文件</span><span class="sxs-lookup"><span data-stu-id="cfb8b-117">Renaming the MOF file</span></span>

<span data-ttu-id="cfb8b-118">可以按 ConfigurationName 或 ConfigurationID 将配置 `.mof` 文件存储在拉取服务器上。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-118">You can store Configuration `.mof` files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="cfb8b-119">可以选择下面的部分来正确重命名已编译的 `.mof` 文件，具体视你计划如何设置拉取客户端。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-119">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled `.mof` files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="cfb8b-120">配置 ID (GUID)</span><span class="sxs-lookup"><span data-stu-id="cfb8b-120">Configuration IDs (GUID)</span></span>

<span data-ttu-id="cfb8b-121">需要将 `localhost.mof` 文件重命名为 `<GUID>.mof` 文件。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-121">You'll need to rename your `localhost.mof` file to `<GUID>.mof` file.</span></span> <span data-ttu-id="cfb8b-122">可以使用以下示例，或使用 [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet 创建随机 Guid。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-122">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="cfb8b-123">示例输出</span><span class="sxs-lookup"><span data-stu-id="cfb8b-123">Sample Output</span></span>

```Output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="cfb8b-124">然后，可以使用任何可接受的方法重命名 `.mof` 文件。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-124">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="cfb8b-125">以下示例使用 [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-125">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="cfb8b-126">有关在环境中使用 Guid 的详细信息，请参阅[规划 Guid](secureServer.md#guids)。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-126">For more information about using **Guids** in your environment, see [Plan for Guids](secureServer.md#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="cfb8b-127">配置名称</span><span class="sxs-lookup"><span data-stu-id="cfb8b-127">Configuration names</span></span>

<span data-ttu-id="cfb8b-128">需要将 `localhost.mof` 文件重命名为 `<Configuration Name>.mof` 文件。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-128">You'll need to rename your `localhost.mof` file to `<Configuration Name>.mof` file.</span></span> <span data-ttu-id="cfb8b-129">在以下示例中，将使用上一节中的配置名称。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-129">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="cfb8b-130">然后，可以使用任何可接受的方法重命名 `.mof` 文件。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-130">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="cfb8b-131">以下示例使用 [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-131">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="cfb8b-132">创建校验和</span><span class="sxs-lookup"><span data-stu-id="cfb8b-132">Create the checkSum</span></span>

<span data-ttu-id="cfb8b-133">拉取服务器上存储的每个 `.mof` 文件或 SMB 共享都需要有关联的 `.checksum` 文件。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-133">Each `.mof` file stored on a Pull Server, or SMB share needs to have an associated `.checksum` file.</span></span>
<span data-ttu-id="cfb8b-134">借助此文件，客户端可以了解关联的 `.mof` 文件何时发生了更改，以及应何时重新下载它。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-134">This file lets clients know when the associated `.mof` file has changed and should be downloaded again.</span></span>

<span data-ttu-id="cfb8b-135">可以使用 [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet 创建校验和。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-135">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="cfb8b-136">也可以使用 `-Path` 参数对文件的目录运行 `New-DSCCheckSum`。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-136">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span>
<span data-ttu-id="cfb8b-137">如果校验和已存在，则可以强制使用 `-Force` 参数重新创建校验和。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-137">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="cfb8b-138">下面的示例指定了包含上一部分中的 `.mof` 文件的目录，并使用 `-Force` 参数。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-138">The following example specified a directory containing the `.mof` file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="cfb8b-139">你将不会看到任何输出，但现在应看到 `<GUID or Configuration Name>.mof.checksum` 文件。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-139">No output will be shown, but you should now see a `<GUID or Configuration Name>.mof.checksum` file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="cfb8b-140">MOF 文件和校验和的存储位置</span><span class="sxs-lookup"><span data-stu-id="cfb8b-140">Where to store MOF files and checkSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="cfb8b-141">在 DSC HTTP 拉取服务器上</span><span class="sxs-lookup"><span data-stu-id="cfb8b-141">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="cfb8b-142">当按照[设置 DSC HTTP 拉取服务器](pullServer.md)中所述设置 HTTP 拉取服务器时，指定 ModulePath  和 ConfigurationPath  键的目录。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-142">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="cfb8b-143">ModulePath 键指明了应在哪里存储模块的打包 `.zip` 文件。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-143">The **ModulePath** key indicates where a module's packaged `.zip` files should be stored.</span></span> <span data-ttu-id="cfb8b-144">ConfigurationPath 键指明了应在哪里存储任何 `.mof` 文件和 `.checksum` 文件。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-144">The **ConfigurationPath** indicates where any `.mof` files and `.checksum` files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="cfb8b-145">在 SMB 共享上</span><span class="sxs-lookup"><span data-stu-id="cfb8b-145">On an SMB share</span></span>

<span data-ttu-id="cfb8b-146">将拉取客户端设置为使用 SMB 共享时，指定 ConfigurationRepositoryShare。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-146">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span>
<span data-ttu-id="cfb8b-147">所有 `.mof` 文件和 `.checksum` 文件应存储在 ConfigurationRepositoryShare 块的 SourcePath 目录中。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-147">All `.mof` files and `.checksum` files should be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="cfb8b-148">后续步骤</span><span class="sxs-lookup"><span data-stu-id="cfb8b-148">Next steps</span></span>

<span data-ttu-id="cfb8b-149">接下来，需要将拉取客户端配置为拉取指定配置。</span><span class="sxs-lookup"><span data-stu-id="cfb8b-149">Next, you'll want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="cfb8b-150">有关详细信息，请参阅以下指南之一：</span><span class="sxs-lookup"><span data-stu-id="cfb8b-150">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="cfb8b-151">使用配置 ID 设置拉取客户端 (v4)</span><span class="sxs-lookup"><span data-stu-id="cfb8b-151">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="cfb8b-152">使用配置 ID 设置拉取客户端 (v5)</span><span class="sxs-lookup"><span data-stu-id="cfb8b-152">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="cfb8b-153">使用配置名称设置拉取客户端 (v5)</span><span class="sxs-lookup"><span data-stu-id="cfb8b-153">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="cfb8b-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cfb8b-154">See also</span></span>

- [<span data-ttu-id="cfb8b-155">设置 DSC SMB 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="cfb8b-155">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="cfb8b-156">设置 DSC HTTP 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="cfb8b-156">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="cfb8b-157">打包资源并将其上传到拉取服务器</span><span class="sxs-lookup"><span data-stu-id="cfb8b-157">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
