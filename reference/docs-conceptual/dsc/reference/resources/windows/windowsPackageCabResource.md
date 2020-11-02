---
ms.date: 07/16/2020
ms.topic: reference
title: DSC WindowsPackageCab 资源
description: DSC WindowsPackageCab 资源
ms.openlocfilehash: 3ac10eb2a7da502b8cac23ab8bfee869a4e26fd3
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143018"
---
# <a name="dsc-windowspackagecab-resource"></a>DSC WindowsPackageCab 资源

> 适用于：Windows PowerShell 5.1

Windows PowerShell Desired State Configuration (DSC) 中的 WindowsPackageCab  资源提供了一种机制，用于在目标节点上安装或卸载 Windows Cabinet (.cab) 程序包。

目标节点必须已安装 DISM PowerShell 模块。 有关信息，请参阅[在 Windows PowerShell 中使用 DISM](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14)。

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>语法

```Syntax
{
    Name = [string]
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    Ensure = [string] { Absent | Present }
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>属性

|properties |说明 |
|---|---|
|名称 |指明要确保其处于特定状态的程序包的名称。 |
|SourcePath |指示程序包所在的路径。 |
|LogPath |指示你希望提供程序用于保存安装或卸载程序包的日志文件的完整路径。 |

## <a name="common-properties"></a>公共属性

|properties |说明 |
|---|---|
|DependsOn |指示必须先运行其他资源的配置，再配置此资源。 例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |指示程序包是否已安装。 将此属性设置为 **Absent** 可确保未安装包（如果已安装，则卸载包）。 将其设置为 **Present** 可确保已安装包。 **Ensure** 是 **WindowsPackageCab** 资源上的必需属性。 |
|PsDscRunAsCredential |设置用于运行整个资源的身份的凭据。 |

## <a name="example"></a>示例

下面的示例配置需要使用输入参数，并确保安装了 `$Name` 参数指定的.cab 文件。

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```
