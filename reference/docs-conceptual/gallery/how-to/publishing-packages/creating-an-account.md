---
ms.date: 09/11/2018
title: 创建 PowerShell 库帐户
description: 本文介绍了 PowerShell 库的用户帐户要求
ms.openlocfilehash: 24c7531e61128415a284d1b438b43f3af0d1053a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662604"
---
# <a name="creating-a-powershell-gallery-account"></a>创建 PowerShell 库帐户

在将任何内容发布到 PowerShell 库之前，必须先创建 PowerShell 库帐户。
必须将 PowerShell 库帐户链接到启用电子邮件的登录帐户。 此帐户可为 Azure Active Directory 帐户或 Microsoft ID，例如 outlook.com 或 hotmail.com 的电子邮件帐户。

要创建 PowerShell 库帐户，请转到 [https://PowerShellGallery.com](https://PowerShellGallery.com)，然后单击“登录”，如下图所示  。

![注册新帐户](media/creating-an-account/CreateAccount-Register.png)

若要使用 Azure Active Directory 帐户，请选择“工作或学校帐户”，并使用帐户登录  。 若要使用 Microsoft ID，请选择“个人帐户”并登录  。

接下来系统便会提示创建 PowerShell 库帐户的用户名。 查看使用条款和隐私策略，输入用户名，然后单击“注册”  。

> [!NOTE]
> 帐户名称一旦创建便无法再进行更改。 有关详细信息，请参阅[管理包所有者](managing-package-owners.md)。

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>适用于 PowerShell 库帐户的推荐做法

请务必确保可主动监视对 PowerShell 库帐户使用的电子邮件帐户。 与 PowerShell 库包所有者之间的所有通信均通过此电子邮件地址进行。 若 PowerShell 库运营团队无法联系包所有者，我们可能需要删除包。

出于此目的，发布到 PowerShell 库的组织通常会创建唯一外部帐户。 我们建议使用电子邮件转发功能将通知转发到组织内的地址。

当多个所有者与包关联时，会向所有所有者发送所有 PowerShell 库通知。 有关详细信息，请参阅[管理包所有者](managing-package-owners.md)。
