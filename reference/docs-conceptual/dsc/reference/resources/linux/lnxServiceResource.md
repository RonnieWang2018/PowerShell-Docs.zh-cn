---
ms.date: 07/17/2020
ms.topic: reference
title: 适用于 Linux 的 DSC nxService 资源
description: 适用于 Linux 的 DSC nxService 资源
ms.openlocfilehash: 4eefe491c491c9245732def1cc85260f368ef9e1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648781"
---
# <a name="dsc-for-linux-nxservice-resource"></a>适用于 Linux 的 DSC nxService 资源

PowerShell Desired State Configuration (DSC) 中的 **nxService** 资源提供了在 Linux 节点上管理服务的机制。

## <a name="syntax"></a>语法

```Syntax
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>属性

|properties |说明 |
|---|---|
|名称 |要配置的服务/守护程序的名称。 |
|控制器 |配置服务时使用的服务控制器类型。 |
|已启用 |指示服务是否开机启动。 |
|状态 |指示服务是否正在运行。 将此属性设置为 **Stopped** 可确保服务不在运行。 将其设置为 **Running** 可确保服务正在运行。 |

## <a name="common-properties"></a>公共属性

|properties |说明 |
|---|---|
|DependsOn |指示必须先运行其他资源的配置，再配置此资源。 例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。 |

## <a name="additional-information"></a>其他信息

**nxService** 资源不会为不存在的服务创建服务定义或脚本。 你可使用 PowerShell Desired State Configuration **nxFile** 资源管理服务定义文件或脚本是否存在或管理其内容。

## <a name="example"></a>示例

下面的示例展示了已向 SystemD  服务控制器注册的“httpd”服务（适用于 Apache HTTP 服务器）的配置。

```powershell
Import-DSCResource -Module nx

Node $node
{
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```
