---
ms.date: 07/17/2020
ms.topic: reference
title: 适用于 Linux 的 DSC nxSshAuthorizedKeys 资源
description: 适用于 Linux 的 DSC nxSshAuthorizedKeys 资源
ms.openlocfilehash: 881e94aa583a745cdac7f01b6e445352ef4ca937
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662768"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a>适用于 Linux 的 DSC nxSshAuthorizedKeys 资源

PowerShell Desired State Configuration (DSC) 中的 **nxAuthorizedKeys** 资源提供了为指定用户管理授权 ssh 密钥的机制。

## <a name="syntax"></a>语法

```Syntax
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>属性

|properties |说明 |
|---|---|
|KeyComment |密钥的唯一注释。 它用于对密钥进行唯一标识。 |
|用户名 |要管理其 ssh 授权密钥的用户名。 如果未定义，则默认用户为 **root** 。 |
|密钥 |密钥的内容。 如果将 **Ensure** 设置为 **Present** ，则此项为必需项。|

## <a name="common-properties"></a>公共属性

|properties |说明 |
|---|---|
|DependsOn |指示必须先运行其他资源的配置，再配置此资源。 例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |指定密钥是否已定义。 将此属性设置为 **Absent** 可确保用户的授权密钥文件中不存在密钥。 将此属性设置为 **Present** 可确保用户的授权密钥文件中已定义密钥。 |

## <a name="example"></a>示例

下面的示例为用户“monuser”定义了公共 ssh 授权密钥。

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxSshAuthorizedKeys myKey
    {
        KeyComment = "myKey"
        Ensure = "Present"
        Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
        UserName = "monuser"
    }
}
```
