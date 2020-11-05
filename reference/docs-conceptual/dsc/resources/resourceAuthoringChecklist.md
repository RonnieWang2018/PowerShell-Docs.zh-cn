---
ms.date: 07/08/2020
keywords: dsc,powershell,配置,安装程序
title: 资源创作清单
description: 本文包含在创作新 DSC 资源时应使用的最佳实践的清单。
ms.openlocfilehash: 5b618511f730c80104620c84e693c13ae4f536ac
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656344"
---
# <a name="resource-authoring-checklist"></a>资源创作清单

此清单是创作新 DSC 资源时的最佳做法的列表。

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a>资源模块包含用于所有资源的 .psd1 文件和 schema.mof

检查资源是否具有正确的结构以及是否包含所有所需文件。 每个资源模块都应包含 .psd1 文件且每个非复合资源都应具有 schema.mof 文件。
未包含架构的资源不会被 `Get-DscResource` 列出且用户在针对 ISE 中的这些模块写入代码时不能使用 IntelliSense。 xRemoteFile 资源是 [xPSDesiredStateConfiguration 资源模块](https://github.com/PowerShell/xPSDesiredStateConfiguration)的一部分，其目录结构如下所示：

```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## <a name="resource-and-schema-are-correct"></a>资源和架构正确

验证资源架构 (`*.schema.mof`) 文件。 你可以使用 [DSC 资源设计器](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0)来帮助开发和测试架构。 请确保：

- 属性类型正确（例如，不将字符串用于接受数值的属性，应改为使用 UInt32 或其他数值类型）
- 按以下格式正确指定属性特性：([key], [required], [write], [read])
- 架构中至少有一个参数被标记为 [key]
- [read] 属性不与下列任意一个属性共同存在：[required]、[key]、[write]
- 如果指定了除 [read] 之外的多个限定符，则 [key] 优先级最高
- 如果指定了 [write] 和 [required]，则 [required] 优先级更高
- 在适当的位置指定了 ValueMap。示例：

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- 指定了友好名称且符合 DSC 命名约定

  示例： `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`

- 每个字段的说明均有意义。 PowerShell GitHub 存储库中有典型示例，如 [xRemoteFile 的 .schema.mof](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/DSCResources/DSC_xRemoteFile/DSC_xRemoteFile.schema.mof)

此外，应使用 [DSC 资源设计器](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0)中的 `Test-xDscResource` 和 `Test-xDscSchema` cmdlet 来自动验证资源和架构：

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

例如：

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a>资源已加载，未出现错误

检查是否可以成功地加载资源模块。 你可以手动完成检查，方法是运行 `Import-Module <resource_module> -force` 并确认未发生错误，或者可以编写自动化测试用例来进行检查。 如果选用后者，则可以在测试用例中遵循此结构：

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw "Module was not imported correctly. Errors returned: $error"
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a>在正向用例中资源是幂等的

DSC 资源的基本特征之一是幂等性。 这意味着多次应用包含该资源的 DSC 配置将始终获得相同的结果。 例如，如果创建包含以下文件资源的配置：

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

在第一次应用它之后，test.txt 文件应出现在 `C:\test` 文件夹。 但是，后续运行相同配置时不会更改计算机的状态（例如，不会创建 `test.txt` 文件的任何副本）。 要确保资源是幂等的，可以在直接测试资源时重复调用 `Set-TargetResource`，或在进行端到端测试时多次调用 `Start-DscConfiguration`。 每次运行后结果都应是相同的。

## <a name="test-user-modification-scenario"></a>测试用户修改场景

通过更改计算机的状态，然后重新运行 DSC，可以验证 `Set-TargetResource` 和 `Test-TargetResource` 是否正常工作。 以下是你要采取的步骤：

1. 从未在所需状态的资源开始。
1. 使用资源运行配置
1. 验证 `Test-DscConfiguration` 是否返回 True
1. 修改已配置项使其不在期望状态
1. 验证 `Test-DscConfiguration` 是否返回 false

下文介绍使用 Registry 资源的更为具体的示例：

1. 从未在所需状态的注册表项开始
1. 运行 `Start-DscConfiguration` 及其配置，以将它放入所需状态并验证其是否通过。
1. 运行 `Test-DscConfiguration` 并验证它是否返回 true
1. 修改项的值，使它不在所需状态
1. 运行 `Test-DscConfiguration` 并验证它是否返回 false
1. 已使用 `Get-DscConfiguration` 对 `Get-TargetResource` 功能进行了验证

`Get-TargetResource` 应返回资源的当前状态的详细信息。 确保对其进行测试，方法是：在应用该配置之后调用 `Get-DscConfiguration`，并验证输出是否正确反映了计算机的当前状态。 请务必对它进行单独测试，因为在调用 `Start-DscConfiguration` 时此区域的任何问题都不会出现。

## <a name="call-getsettest-targetresource-functions-directly"></a>直接调用函数 **Get/Set/Test-TargetResource**

请确保对在资源中实现的 `Get/Set/Test-TargetResource` 函数进行测试，可通过直接调用它们并按预期方式进行验证完成此操作。

## <a name="verify-end-to-end-using-start-dscconfiguration"></a>使用 Start-DscConfiguration 进行端到端验证

虽然通过直接调用 `Get/Set/Test-TargetResource` 函数对它们进行测试至关重要，但不是所有问题都能以这种方法发现。 你应将测试的关注重心放在使用 `Start-DscConfiguration` 上或请求服务器上。 事实上，这就是用户使用资源的方式，所以不要低估此类测试的重要性。 可能的问题类型：

- 由于 DSC 代理以服务方式运行，因此凭据/会话的行为可能不同。 请务必端到端地测试此处的任何功能。
- 由 `Start-DscConfiguration` 输出的错误可能与在直接调用 `Set-TargetResource` 函数时显示的错误不同。

## <a name="test-compatibility-on-all-dsc-supported-platforms"></a>在所有 DSC 支持的平台上测试兼容性

资源应适用于所有支持 DSC 的平台（Windows Server 2008 R2 或更高版本）。 在操作系统上安装最新的 WMF (Windows Management Framework) 以获取最新版本的 DSC。 如果资源按设计无法在部分平台上运作，则将返回特定的错误消息。 此外，确保资源检查你调用的 cmdlet 是否存在于特定的计算机上。 Windows Server 2012 添加了大量新 cmdlet，即使安装了 WMF，它们在 Windows Server 2008R2 上也不可用。

## <a name="verify-on-windows-client-if-applicable"></a>在 Windows 客户端上验证（如果适用）

一个非常常见的测试间隙在于，仅在 Windows 的服务器版本上验证资源。 许多资源也被设计用于客户端 SKU，因此如果你也属于这种情况，请不要忘记在这些平台上测试它。

## <a name="get-dscresource-lists-the-resource"></a>Get-DSCResource 用于列出资源

部署模块后，调用 `Get-DscResource` 将列出资源等作为结果。 如果无法在列表中找到你的资源，请确保该资源的 schema.mof 文件存在。

## <a name="resource-module-contains-examples"></a>资源模块包含示例

创建高质量示例可以帮助其他人了解如何使用它。 这一点至关重要，因为许多用户会将示例代码视为文档。

- 首先，你应确定要在模块中包含的示例（至少你应涵盖资源的最重要用例）：
- 如果模块包含几个需要一起用于端到端方案的资源，则最好将基本的端到端示例作为第一个示例。
- 最初的示例应非常简单 -- 如何在小的可管理区块中开始使用你的资源（例如，创建新 VHD）
- 随后的示例应该建立在这些示例之上（例如，从 VHD 中创建 VM、删除 VM、修改 VM），且应介绍高级功能（例如，创建具有动态内存的 VM）
- 示例配置应该参数化（所有的值都应作为参数传递到配置且不能包含硬编码值）：

```powershell
configuration Sample_xRemoteFile_DownloadFile
{
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
}
```

- 包括（注释掉）关于如何在示例脚本的末尾使用实际值调用配置的示例，就是一个很好的做法。 例如，在上面的配置中，指定 UserAgent 的最佳做法如下所示，但这种最佳做法并非显而易见：

  `UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer`：这样，注释可以阐明配置的执行目的：

```powershell
<#
Sample use (parameter values need to be changed according to your scenario):

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
-userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
#>
```

- 对于每个示例，编写简短说明，解释它能做什么以及参数的意义。
- 确保示例涵盖资源的大部分重要方案，如果没有任何遗漏，验证它们是否都能执行以及是否能让计算机达到所需状态。

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a>错误消息要易于理解，以便帮助用户解决问题

好的错误消息应具有以下特性：

- 存在性：错误消息最大的问题在于它们经常不存在，因此应确保它们的确存在。
- 易于理解：人工可读，没有晦涩的错误代码
- 精确性：描述问题的具体内容
- 建设性：建议如何修复问题
- 礼貌用语：不要责怪用户或让他们感到不舒服

确保验证端到端方案中的错误（使用 `Start-DscConfiguration`），因为它们可能与直接运行资源函数时返回的错误不同。

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a>日志消息要易于理解且信息量大（包括 –verbose、–debug 和 ETW 日志）

确保由资源输出的日志易于理解且向用户提供有价值的信息。
资源应输出所有可能对用户有用的信息，但并不总是日志越多越好。 你应该避免冗余和输出不提供更多价值的数据 - 不要让人为了找到他们要找的内容而浏览成百上千条日志。 当然，针对此问题没有任何日志也是不可接受的解决方案。

测试时还应分析 verbose 和 debug 日志（通过合理使用 `–Verbose` 和 `–Debug` 开关运行 `Start-DscConfiguration`）以及 ETW 日志。 若要查看 DSC ETW 日志，请转到事件查看器并打开以下文件夹：Applications and Services- Microsoft - Windows - Desired State Configuration。 默认情况下设置有“操作”通道，但要确保在运行配置之前启用了“分析”通道和“调试”通道。 若要启用“分析”/“调试”通道，可以执行下面的脚本：

```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug"
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}
Invoke-Expression $commandToExecute
```

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a>资源实现不包含硬编码路径

确保资源实现中没有硬编码路径，特别是如果它们表示语言时 (en-us)，或者当存在可以使用的系统变量时。 如果资源需要访问特定路径，请使用环境变量而非硬编码路径，因为后者在其他计算机上可能有所不同。

示例：

不是：

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

你可以编写：

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a>资源实现不包含用户信息

请确保代码中没有电子邮件名称、帐户信息或人员姓名。

## <a name="resource-was-tested-with-validinvalid-credentials"></a>已使用有效/无效凭据验证了资源

如果资源将凭据作为参数：

- 当本地系统（或远程资源计算机帐户）无访问权限时验证资源是否正常运行。
- 使用为 Get、Set 和 Test 指定的凭据验证资源是否正常运行。
- 如果资源访问共享，请测试你需要支持的所有变体，例如：
  - 标准 Windows 共享。
  - DFS 共享。
  - SAMBA 共享（如果希望支持 Linux。）

## <a name="resource-does-not-require-interactive-input"></a>资源不需要交互式输入

应自动执行 `Get/Set/Test-TargetResource` 函数，且不能在任何执行阶段等待用户输入（例如，不能在这些函数中使用 `Get-Credential`）。 如果需要提供用户的输入，应在编译阶段期间将它作为参数传递到配置。

## <a name="resource-functionality-was-thoroughly-tested"></a>已全面测试资源功能

此清单包含要测试的重要项和/或经常丢失的项。 提供了一系列测试，主要是特定于你要测试的资源和此处未提及的测试。 不要忘记负面测试用例。

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a>最佳做法：资源模块包含具有 ResourceDesignerTests.ps1 脚本的 Tests 文件夹

对于给定模块中的所有资源，最好使用 `Test-xDscResource` 和 `Test-xDscSchema` 在资源模块中创建“Tests”文件夹，创建 `ResourceDesignerTests.ps1` 文件并添加测试。 通过这种方法你可以快速验证给定模块的所有资源的架构，并在发布前执行完整性检查。 对于 xRemoteFile，`ResourceTests.ps1` 可能和以下情况一样简单：

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-supports--whatif"></a>最佳做法：资源支持 - WhatIf

如果资源正在执行“危险”操作，最佳做法是实现 `-WhatIf` 功能。 完成后，请确保 `-WhatIf` 输出正确地描述了在无 `-WhatIf` 开关情况下执行命令时可能发生的操作。 此外，验证当 `–WhatIf` 开关存在时操作是否不会执行（未对节点的状态进行更改）。 例如，假设我们正在测试 File 资源。 下面是创建 `test.txt` 文件及其“test”内容的简单配置：

```powershell
configuration config
{
    node localhost
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config
```

如果我们使用 `-WhatIf` 开关进行编译，然后执行配置，则输出将报告运行该配置时具体会发生什么。 但是配置本身并没有被执行（没有创建 `test.txt` 文件）。

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```Output
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

此列表并不详尽，但它涵盖了在设计、开发和测试 DSC 资源时会遇到的许多重要问题。
