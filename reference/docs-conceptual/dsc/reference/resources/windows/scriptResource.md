---
ms.date: 07/16/2020
ms.topic: reference
title: DSC Script 资源
description: DSC Script 资源
ms.openlocfilehash: f404bf3137caa9f57ad56034895cb15c8944ec07
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142967"
---
# <a name="dsc-script-resource"></a>DSC Script 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x

Windows PowerShell Desired State Configuration (DSC) 中的 `Script` 资源提供了在目标节点上运行 Windows PowerShell 脚本的机制。 `Script` 资源使用 `GetScript`
`SetScript` 和 `TestScript` 属性，这些属性包含定义以执行相应的 DSC 状态操作的脚本块。

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>语法

```Syntax
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> 将 `GetScript`、`TestScript` 和 `SetScript` 块存储为字符串。

## <a name="properties"></a>属性

|  properties  |                                          说明                                          |
| ---------- | --------------------------------------------------------------------------------------------- |
| GetScript  | 一个返回节点当前状态的脚本块。                                    |
| SetScript  | DSC 在节点未处于所需状态时用于强制执行符合性的脚本块。 |
| TestScript | 一个用于确定节点是否处于所需状态的脚本块。                           |
| 凭据 | 指示要用于运行此脚本的凭据（如果需要凭据）。        |

## <a name="common-properties"></a>公共属性

|       properties       |                                            说明                                            |
| -------------------- | ------------------------------------------------------------------------------------------------- |
| DependsOn            | 指示必须先运行其他资源的配置，再配置此资源。 |
| PsDscRunAsCredential | 设置用于运行整个资源的身份的凭据。                                           |

> [!NOTE]
> 在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。 有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。

### <a name="additional-information"></a>其他信息

#### <a name="getscript"></a>GetScript

DSC 不使用 `GetScript`，[Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet 执行 `GetScript` 以检索节点的当前状态。 `GetScript` 不需要返回值，如果指定返回值，则它必须是包含值为字符串的 Result 键的哈希表。

#### <a name="testscript"></a>TestScript

DSC 执行 `TestScript` 以确定是否应运行 `SetScript`。 如果 `TestScript` 返回 `$false`，则 DSC 执行 `SetScript` 以使节点恢复到所需的状态。 它必须返回一个布尔值。 `$true` 的结果表示节点是符合的，不应执行 `SetScript`。

[Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet 执行 `TestScript` 以检索节点是否符合 `Script` 资源。 但是，在这种情况下，无论 `TestScript` 块返回什么，`SetScript` 都不会运行。

> [!NOTE]
> `TestScript` 的所有输出都是其返回值的一部分。 PowerShell 将未压缩的输出视为非零，这意味着无论节点的状态如何，`TestScript` 都将返回 `$true`。 这会导致不可预测的结果和误报，并导致在故障排除时出现问题。

#### <a name="setscript"></a>SetScript

`SetScript` 修改节点以强制执行所需的状态。 如果 `TestScript` 脚本块返回 `$false`，则其由 DSC 调用。 `SetScript` 应该没有返回值。

## <a name="examples"></a>示例

### <a name="example-1-write-sample-text-using-a-script-resource"></a>示例 1：使用脚本资源编写示例文本

此示例测试每个节点上是否存在 `C:\TempFolder\TestFile.txt`。 如果它不存在，则使用 `SetScript` 创建它。 `GetScript` 返回文件的内容，并且不使用其返回值。

```powershell
Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a>示例 2：使用脚本资源比较版本信息

此示例从创作计算机上的文本文件中检索符合的版本信息，并将其存储在 `$version` 变量中。 在生成节点的 MOF 文件时，DSC 将每个脚本块中的 `$using:version` 变量替换为 `$version` 变量的值。
在执行期间，符合的版本存储在每个节点上的文本文件中，并在后续执行时进行比较和更新。

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state.Result -eq $using:version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state.Result,$using:version)
                    return $true
                }
                Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
                return $false
            }
            SetScript = {
                $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            }
        }
    }
}
```

### <a name="example-3-utilizing-parameters-in-a-script-resource"></a>示例 3：使用脚本资源中的参数

此示例通过使用 `using` 范围，从脚本资源中访问参数。
请注意，ConfigurationData 可通过类似的方式进行访问。 如示例 2 所示，版本应存储在目标节点上的本地文件中。 但本地文件路径和版本都是可配置的，这会将代码与配置数据分开。

```powershell
Configuration ScriptTest
{
    param
    (
        [Version]
        $Version,

        [string]
        $FilePath
    )

    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content -Path $using:FilePath
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state['Result'] -eq $using:Version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                    return $true
                }

                Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
                return $false
            }
            SetScript = {
                Set-Content -Path $using:FilePath -Value $using:Version
            }
        }
    }
}
```

生成的 MOF 文件包含通过 `using` 范围访问的变量及其值。
它们被注入每个使用变量的脚本块中。 为简洁起见，删除了测试和设置脚本：

```Output
instance of MSFT_ScriptResource as $MSFT_ScriptResource1ref
{
 GetScript = "$FilePath ='C:\\Config.ini'\n\n $currentVersion = Get-Content -Path $FilePath\n return @{ 'Result' = \"$currentVersion\" }\n";
 TestScript = ...;
 SetScript = ...;
};
```

### <a name="known-limitations"></a>已知限制

- 使用拉取或推送服务器模型时，在脚本资源中传递的凭据并不总是可靠。 在此情况下，建议使用完整资源，而不是使用脚本资源。
