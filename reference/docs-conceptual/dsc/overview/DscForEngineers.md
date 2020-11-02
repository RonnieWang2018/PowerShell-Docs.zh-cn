---
ms.date: 10/13/2017
keywords: dsc,powershell,配置,安装程序
title: 适用于工程师的 Desired State Configuration 概述
description: 本文档旨在使开发人员和运营团队了解 PowerShell Desired State Configuration (DSC) 的优势。
ms.openlocfilehash: c98295d0e78f4dc89e5df429e3c1de9a0c024054
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646932"
---
# <a name="desired-state-configuration-overview-for-engineers"></a>适用于工程师的 Desired State Configuration 概述

本文档旨在使开发人员和运营团队了解 PowerShell Desired State Configuration (DSC) 的优势。 有关 DSC 提供的值的更高级别视图，请参阅[适用于决策者的 Desired State Configuration 概述](decisionMaker.md)

## <a name="benefits-of-desired-state-configuration"></a>Desired State Configuration 的优势

DSC 具有以下优势：

- 降低在 Windows 中编写脚本的复杂程度
- 提高迭代速度

“连续部署”的概念变得更加重要。 连续部署是指能够频繁部署，可能每天进行多次部署。 这些部署的目的不是为了提供修复，而是为了进行快速发布。 通过尽可能顺畅可靠地完成新功能从开发到操作的过程，可以缩短新的业务逻辑转换为价值的时间。

转向云计算意味着采用了利用“声明式”模板模型的部署解决方案，其中结束状态环境声明为文本，并发布到部署引擎中。 此部署技术允许使用针对失败威胁的恢复能力进行大规模的快速更改，这是因为，在任何时候都可以不断重复部署，以保证结束状态。 创建通过自动化支持此操作风格的工具和服务是对这些更改的响应。

DSC 是一个提供声明式和幂等式（可重复）部署、配置和符合项的平台。 通过 DSC 平台，你可以确保数据中心的组件采用了正确的配置，从而避免错误并防止代价高昂的部署失败。 通过将 DSC 配置视为应用程序代码的一部分，DSC 可实现连续部署。 DSC 配置应作为应用程序的一部分进行更新，从而确保部署应用程序所需知识始终保持最新且随时可以使用。

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a>“我已有 PowerShell，为什么还需要 Desired State Configuration？”

DSC 配置将意图或“我想要执行哪些操作”与执行或“我要如何操作”分离开来。 这意味着资源内包含执行逻辑。 当某个功能的 DSC 资源可用时，用户无需知道如何实现或部署该功能。 这样，用户就可以专注于部署的结构。

例如，PowerShell 脚本应如下所示：

```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```

虽然此脚本简单易懂。 但是，如果尝试将该脚本投入生产环境，将会遇到一些问题。 如果该脚本连续运行两次会发生什么情况？ 如果 Bob 以前对共享具有完全访问权限会发生什么情况？

为了弥补这些问题，“实际”版本的脚本将进一步类似于：

```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @PSBoundParameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($PSBoundParameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

此脚本更加复杂，包含大量逻辑和错误处理。 该脚本更为复杂，因为不再需要指出要执行哪些操作，而是说明如何执行  。

使用 DSC 可以指出要执行哪些操作，并且抽象出底层逻辑。

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present"
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"
          ReadAccess  = "Bob"
          FullAccess  = "Alice"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

此脚本格式清晰，简单易读。
逻辑路径和错误处理仍存在于[资源](../resources/resources.md)实现中，但对脚本作者不可见。

## <a name="separating-environment-from-structure"></a>将环境从结构中分离出来

DevOps 中的常见模式是多个环境用于部署。 例如，可能有用于快速生成原型新代码的“开发”环境。 “开发”环境中的代码进入“测试”环境，其他人员在其中验证新功能。 最后，代码将进入“生产”或实时站点生产环境。

DSC 配置可通过使用[配置数据](../configurations/configData.md)适应此开发-测试-生产流程。
这可进一步抽象出托管节点的配置结构之间的差异。 例如，可以定义需要 SQL server、IIS 服务器和中间层服务器的配置。 无论哪个节点接收到此配置的不同部分，这三个元素会始终存在。 对于开发环境，可以使用配置数据将所有三个元素指向同一计算机；对于测试环境，可以将这三个元素分离到三个不同的计算机；最后对于生产环境，又可以将其指向所有的生产服务器。 若要部署到各种环境中，可以针对想要面向的环境，使用正确的配置数据调用 `Start-DscConfiguration`。

## <a name="see-also"></a>另请参阅

[配置](../configurations/configurations.md)

[配置数据](../configurations/configData.md)

[资源](../resources/resources.md)
