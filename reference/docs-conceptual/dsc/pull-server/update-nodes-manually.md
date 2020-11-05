---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 从拉取服务器更新节点
description: 本文介绍了如何从拉取服务器更新 DSC 托管节点
ms.openlocfilehash: 7256a0e1fdfaa8e56150c4f7299640bc95b82cee
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656761"
---
# <a name="update-nodes-from-a-pull-server"></a><span data-ttu-id="47f94-104">从拉取服务器更新节点</span><span class="sxs-lookup"><span data-stu-id="47f94-104">Update Nodes from a Pull Server</span></span>

<span data-ttu-id="47f94-105">以下部分假定你已设置拉取服务器。</span><span class="sxs-lookup"><span data-stu-id="47f94-105">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="47f94-106">如果尚未设置拉取服务器，则可以使用以下指南：</span><span class="sxs-lookup"><span data-stu-id="47f94-106">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="47f94-107">设置 DSC SMB 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="47f94-107">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="47f94-108">设置 DSC HTTP 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="47f94-108">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="47f94-109">每个目标节点都可以配置为下载配置、资源，甚至是报告其状态。</span><span class="sxs-lookup"><span data-stu-id="47f94-109">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="47f94-110">本文将演示如何上传资源以便下载，以及如何将客户端配置为自动下载资源。</span><span class="sxs-lookup"><span data-stu-id="47f94-110">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="47f94-111">当节点通过“拉取”  或“推送”  (v5) 接收已分配的配置时，将从 LCM 中指定的位置自动下载配置所需的任何资源。</span><span class="sxs-lookup"><span data-stu-id="47f94-111">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="using-the-update-dscconfiguration-cmdlet"></a><span data-ttu-id="47f94-112">使用 Update-DSCConfiguration cmdlet</span><span class="sxs-lookup"><span data-stu-id="47f94-112">Using the Update-DSCConfiguration cmdlet</span></span>

<span data-ttu-id="47f94-113">从 PowerShell 5.0 开始，[Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet 强制节点从 LCM 中配置的拉服务器更新其配置。</span><span class="sxs-lookup"><span data-stu-id="47f94-113">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span></span>

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a><span data-ttu-id="47f94-114">使用 Invoke-CIMMethod</span><span class="sxs-lookup"><span data-stu-id="47f94-114">Using Invoke-CIMMethod</span></span>

<span data-ttu-id="47f94-115">在 PowerShell 4.0 中，仍可以手动强制拉取客户端以使用 [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod) 更新其配置。</span><span class="sxs-lookup"><span data-stu-id="47f94-115">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span></span> <span data-ttu-id="47f94-116">以下示例使用指定的凭据创建 CIM 会话、调用相应的 CIM 方法以及删除该会话。</span><span class="sxs-lookup"><span data-stu-id="47f94-116">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span></span>

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a><span data-ttu-id="47f94-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="47f94-117">See Also</span></span>

[<span data-ttu-id="47f94-118">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="47f94-118">PerformRequiredConfigurationChecks</span></span>](../reference/mof-classes/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)
