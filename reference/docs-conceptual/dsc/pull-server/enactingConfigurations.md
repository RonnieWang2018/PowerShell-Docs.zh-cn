---
ms.date: 10/16/2017
keywords: dsc,powershell,配置,安装程序
title: 执行配置
description: 有两种执行 PowerShell DSC 配置的方法 - 推送模式和拉取模式。
ms.openlocfilehash: 466eb43cd266ceb4ae81cc997a7b338e041f8a15
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661721"
---
# <a name="enacting-configurations"></a>执行配置

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

有两种执行 PowerShell Desired State Configuration (DSC) 配置的方法：推送模式和请求模式。

## <a name="push-mode"></a>推送模式

![推送模式概述](media/enactingConfigurations/pushModel.png "推送模式的工作原理")

推送模式指的是用户通过调用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet 主动将配置应用到目标节点。

创建并编译配置后，可通过调用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet，并将 cmdlet 的 -Path 参数设置为配置 MOF 所在的路径，从而在推送模式下执行该配置。 例如，如果配置 MOF 位于 `C:\DSC\Configurations\localhost.mof` 中，则使用以下命令将其应用于本地计算机：`Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> [!NOTE]
> 默认情况下，DSC 运行配置作为后台作业。 若要以交互方式运行此配置，请使用 Wait 参数调用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)。

## <a name="pull-mode"></a>请求模式

![请求模式概述](media/enactingConfigurations/pullModel.png "请求模式的工作原理")

在请求模式下，配置请求客户端以从远程请求服务中获取所需的状态配置。 同样，已将请求服务设置为托管 DSC 服务，并预配了请求服务器所需的配置和资源。 每个请求客户端都有计划的事件，在节点的配置上定期执行符合性检查。 首次触发事件时，请求客户端上的本地配置管理器 (LCM) 对请求服务发出请求，获取 LCM 中指定的配置。 如果请求服务上存在该配置，并通过了初始验证检查，则配置将下载到请求客户端，然后在其上由 LCM 进行执行。

LCM 会按其 **ConfigurationModeFrequencyMins** 属性指定的时间间隔来定期检查客户端是否符合配置要求。 LCM 会按其 RefreshModeFrequency  属性指定的时间间隔来定期检查请求服务上的更新配置。 若要了解如何配置 LCM，请参阅[配置本地配置管理器](../managing-nodes/metaConfig.md)。

用于托管请求服务的推荐解决方案是 DSC 云服务，[Azure 自动化](https://azure.microsoft.com/services/automation/)。 此托管解决方案提供图形管理、报告和集中式管理。

有关在 Windows Server 上设置请求服务的详细信息，请参阅[设置 DSC Web 请求服务器](pullServer.md)。 但是，请了解，此实现的功能有限，并且需要一些“自助式”集成。

以下主题说明了请求服务和客户端：

- [Azure Automation DSC 概述](/azure/automation/automation-dsc-overview)
- [设置 SMB 请求服务器](pullServerSMB.md)
- [配置请求客户端](pullClientConfigID.md)
