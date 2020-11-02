---
ms.date: 07/16/2020
ms.topic: reference
title: DSC WindowsProcess 资源
description: DSC WindowsProcess 资源
ms.openlocfilehash: 3076e9cb857b78953c164253351b23e7da9b40c6
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143001"
---
# <a name="dsc-windowsprocess-resource"></a>DSC WindowsProcess 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x

Windows PowerShell Desired State Configuration (DSC) 中的 **WindowsProcess** 资源提供了用于在目标节点上配置进程的机制。

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>语法

```Syntax
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>属性

|properties |说明 |
|---|---|
|参数 |指示要原样传递到进程的参数字符串 如果需要传递多个参数，请将它们全部放在此字符串中。 |
|路径 |进程可执行文件的路径。 如果这是可执行文件的文件名（不是完全限定的路径），则 DSC 资源会搜索环境 `$env:Path` 变量以查找可执行文件。 如果此属性的值是完全限定的路径，则 DSC 不使用 `$env:Path` 变量查找文件，并且会在不存在路径时引发错误。 不允许使用相对路径。 |
|凭据 |指示启动进程的凭据。 |
|StandardErrorPath |指示写入标准错误的目录路径。 将覆盖任何现有文件。 |
|StandardInputPath |指示标准输入位置。 |
|StandardOutputPath |指示写入标准输出的位置。 将覆盖任何现有文件。 |
|WorkingDirectory |指示将用作进程当前工作目录的位置。 |

## <a name="common-properties"></a>公共属性

|properties |说明 |
|---|---|
|DependsOn |指示必须先运行其他资源的配置，再配置此资源。 例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |指示进程是否存在。 将此属性设置为 **Present** 可确保进程存在。 否则，将其设置为 **Absent** 。 默认值为 **Present** 。 |
|PsDscRunAsCredential |设置用于运行整个资源的身份的凭据。 |
