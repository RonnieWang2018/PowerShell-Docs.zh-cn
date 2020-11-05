---
ms.date: 06/12/2017
title: 部署到 Azure 自动化
description: 本文介绍了如何使用 PowerShell 库将包部署到 Azure 自动化。
ms.openlocfilehash: e9de079ee6cc950c8a268423b9eabd515959b718
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662367"
---
# <a name="deploy-to-azure-automation"></a>部署到 Azure 自动化

包详细信息页上的“部署到 Azure 自动化”按钮会将包从 PowerShell 库部署到 Azure 自动化。

![“部署到 Azure 自动化”按钮](media/deploy-to-azure-automation/DeployToAzureAutomationButton.png)

单击后，将重定向到 Azure 管理门户，可使用 Azure 帐户凭据进行登录。 如果该包包含依赖关系，则所有依赖关系也将部署到 Azure 自动化。

> [!WARNING]
> 如果自动化帐户中已存在相同的包和版本，将其从 PowerShell 库再次部署会覆盖自动化帐户中的包。

如果部署模块，则该模块会出现在 Azure 自动化的“模块”部分中。 如果部署脚本，则该脚本会出现在 Azure 自动化的“Runbook”部分中。

通过将 AzureAutomationNotSupported 标记添加到包元数据可禁用“部署到 Azure 自动化”按钮。

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>在部署到 Azure 自动化时需要接受许可证

如果正在部署到 Azure 自动化的模块需要接受许可证，则门户 UI 将会显示内容为“此模块需要接受许可证。 单击“确定”接受许可证条款。”的声明

![部署到 Azure 自动化需要接受许可证](media/deploy-to-azure-automation/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>更多详细信息

- [在 PowerShellGet 中需要接受许可证](../../concepts/module-license-acceptance.md)
- [在 Power 库中需要接受许可证](packages-that-require-license-acceptance.md)
- [Azure 自动化网站](https://azure.microsoft.com/services/automation/)
