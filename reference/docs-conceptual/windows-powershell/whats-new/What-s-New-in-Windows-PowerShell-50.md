---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell 5.0 中的新增功能
description: 这些发行说明介绍了 Windows PowerShell 5.x 中的新增功能和更改。
ms.openlocfilehash: 82d3e10fa417085911242241dcfc54e931df8eb4
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663367"
---
# <a name="whats-new-in-windows-powershell-50"></a>Windows PowerShell 5.0 中的新增功能

Windows PowerShell 5.0 新增了大量功能，不仅扩展并提升了自身的用途和可用性，还方便用户能够更轻松、全面地控制和管理基于 Windows 的环境。

Windows PowerShell 5.0 可向后兼容。 为 Windows PowerShell 4.0、Windows PowerShell 3.0 和 Windows PowerShell 2.0 设计的 cmdlet、提供程序、模块、管理单元、脚本、函数和配置文件通常适用于 Windows PowerShell 5.0，无需更改。

## <a name="installing-windows-powershell"></a>安装 Windows PowerShell

Windows PowerShell 5.0 默认安装在 Windows Server 2016 Technical Preview 和 Windows 上
10.

若要在 Windows Server 2012 R2、Windows 8.1 企业版或 Windows 8.1 专业版上安装 Windows PowerShell 5.0，请下载并安装 [Windows Management Framework 5.0](https://aka.ms/wmf5download)。 请务必先阅读下载详细信息并确保满足所有系统要求，然后再安装 Windows Management Framework 5.0。

## <a name="in-this-topic"></a>本主题内容

- [KB 3000850 中的 Windows PowerShell 4.0 DSC 更新](#windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850)
- [Windows PowerShell 5.0 中的新增功能](#new-features-in-windows-powershell-50)
- [Windows PowerShell 4.0 中的新增功能](#new-features-in-windows-powershell-40)
- [Windows PowerShell 3.0 中的新增功能](#new-features-in-windows-powershell-30)

## <a name="windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850"></a>2014 年 11 月更新汇总中的 Windows PowerShell 4.0 更新 (KB 3000850)

针对 Windows PowerShell 4.0 中 Windows PowerShell Desired State Configuration (DSC) 的许多更新和改进均在 [2014 年 11 月 Windows RT 8.1、Windows 8.1 和 Windows Server 2012 R2 更新汇总](https://support.microsoft.com/kb/3000850/) (KB 3000850) 中提供。 你可以通过在 Windows PowerShell 中运行 `Get-Hotfix -Id KB3000850` 以确定你的系统上是否已安装 KB 3000850。

- 对 [PSDesiredStateConfiguration](/powershell/module/PSDesiredStateConfiguration) 模块中现有 cmdlet 的更新。
  - [Get-DscResource](/powershell/module/PSDesiredStateConfiguration) 更加快速（特别是在 ISE 中）。
  - [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration) 有一个新的 -UseExisting 参数，使用该参数可重新应用上一次应用的配置。
  - 已修复 [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration) -Force。
  - [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration) 显示有关引擎状态的更多有用信息。
  - [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration) 现在可返回计算机名称以及 True 或 False。
  - [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration) 现在支持 UNC 路径。

- [PSDesiredStateConfiguration](/powershell/module/PSDesiredStateConfiguration) 模块中新的 cmdlet。
  - [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)：按需执行请求服务器检查。
  - [Stop-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)：停止已运行的配置。
  - [Remove-DscConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)：使你能够在各个阶段中（挂起、之前或当前）删除配置文档。

- 语言增强功能
  - DependsOn 现在支持复合资源。
  - DependsOn 现在支持资源实例名称中带有数字。
  - 计算结果为空的节点表达式不再引发错误。
  - 已修复当节点表达式计算结果为空时发生的错误。
  - 配置调用的配置现在可在 Windows PowerShell 控制台中使用。

- 请求模式增强功能
  - 请求模式现在支持所有的 ZIP 文件。
  - **AllowModuleOverwrite** 现在可正常工作。

- 复原能力改进
  - 新的 **DebugMode** 使你能够重新加载资源模块。
  - 如果出现配置失败，pending.mof 文件则不会被删除。
  - 当元配置设置损坏时，本地配置管理器 (LCM) 更具有复原能力。

- 诊断改进
  - 当 LCM 将计时器设置为与你已指定的设置不同时，会显示一条警告。
  - 错误日志文件现在包括 Windows PowerShell 资源的调用堆栈。

- 灵活性改进
  - LocalConfigurationManager 资源拥有一个新属性， **ActionAfterReboot** 。
    - ContinueConfiguration（默认值）：在目标节点重启后自动恢复配置。
    - StopConfiguration：不会在节点重启后自动恢复配置。
  - 现在一致性运行可以比 PULL 操作发生的更频繁，或者反之亦然。
  - 版本控制支持：DSC 现在可以识别在较新的客户端上生成的文档（包括使用 [WMF 5.0](https://aka.ms/wmf5download) 生成的文档）。

- 错误防护改进
  - 现在在应用配置前，会强制执行模块版本。
  - 现在已为 Get-TargetResource、Set-TargetResource 或 Test-TargetResource 调用正确地设置了 **DebugPreference** 。

- 凭据处理改进
  - 现在如果同时指定 **Certificate** 和 **PSDscAllowPlainTextPassword** ，则可使用证书。
  - 凭据是解密的、甚至对 Get-TargetResource 来说也是如此。
  - 元配置凭据为加密的和解密的。
  - 当 PSCredential 在嵌入对象中时，它们是解密的。

- 内置资源改进
  - Package 资源
    - 不再安装错误的包（无论从本地或 Web 资源中安装）。
    - 现在支持 HTTPS。
  - 现在在 [Package 资源](/powershell/scripting/dsc/reference/resources/windows/packageresource)中支持 HTTPS。
  - [Archive 资源](/powershell/scripting/dsc/reference/resources/windows/archiveresource)现在支持凭据。

## <a name="new-features-in-windows-powershell-50"></a>Windows PowerShell 5.0 中的新增功能

- [Windows PowerShell 中的新增功能](#new-features-in-windows-powershell)
- [Windows PowerShell Desired State Configuration 中的新增功能](#new-features-in-windows-powershell-desired-state-configuration)
- [Windows PowerShell ISE 中的新增功能](#new-features-in-windows-powershell-ise)
- [Windows PowerShell Web 服务中的新增功能](#new-features-in-windows-powershell-web-services-management-odata-iis-extension)
- [Windows PowerShell 5.0 中值得注意的 Bug 修复](#notable-bug-fixes-in-windows-powershell-50)

### <a name="new-features-in-windows-powershell"></a>Windows PowerShell 中的新增功能

- 从 Windows PowerShell 5.0 开始，你可以通过使用类，通过使用正式语法和类似于其他面向对象的编程语言的语义进行开发。 **Class** 、 **Enum** 和其他关键字已添加到 Windows PowerShell 语言中以支持新增功能。
  有关使用类的详细信息，请参阅 about_Classes。

- Windows PowerShell 5.0 引入了一个新的结构化信息流，可用于在脚本和其调用方（或主机环境）之间传输结构化数据。 现在可使用 Write-Host 将输出发出到信息流。 信息流也适用于 PowerShell.Streams、作业、计划作业和工作流。 以下功能支持信息流。
  - 一个新的 Write-Information cmdlet，使你能够指定 Windows PowerShell 如何处理命令的信息流数据。 Write-Host 是 Write-Information 的包装器。 Write-Information 也是受支持的工作流活动。
  - 两个新的通用参数 InformationVariable 和 InformationAction，使你能够确定如何显示来自命令的信息流。 InformationAction 有效的值是 SilentlyContinue、Stop、Continue、Inquire、Ignore 或 Suspend，默认值是 SilentlyContinue。 InformationVariable 将字符串指定为你希望将来自命令的 Write-Host 数据保存到其中的变量的名称。
  - 一个新的首选项变量 InformationPreference，它指定在 Windows PowerShell 会话中信息流数据的默认首选项。 默认值是 SilentlyContinue。
  - 已添加两个新的工作流通用参数 PSInformation 和 InformationAction。
  - 当你使用 Format-Table 命令时，表列现评估通过流传递的前 300ms 的数据来自动进行格式设置。

- 与 [Microsoft Research](https://research.microsoft.com/) 协作添加了一个新的 cmdlet，即 ConvertFrom-String。 ConvertFrom-String 使你能够从文本字符串的内容中提取和分析结构化对象。 有关详细信息，请参阅 ConvertFrom-String。
- 新的 Convert-String cmdlet 基于你在 -Example 参数中提供的示例自动设置文本的格式。
- 新的模块 Microsoft.PowerShell.Archive 包括了使你能够将文件和文件夹压缩到存档文件（也被称为 ZIP）、从现有 ZIP 文件中提取文件以及使用其中压缩的较新版本文件更新 ZIP 文件的 cmdlet。
- 新的模块 PackageManagement 使你能够在 Internet 上发现并安装软件包。
  PackageManagement（以前被称为 OneGet）模块是一个管理器或现有包管理器（也被称为包提供程序）的多路复用器，使用单个 Windows PowerShell 界面统一管理 Windows 包。
- 新的模块 PowerShellGet 使你能够在 [PowerShell 库](https://www.powershellgallery.com/)上，或者在可以通过运行 Register-PSRepository cmdlet 来进行设置的内部模块存储库上查找、安装、发布和更新模块和 DSC 资源。
- 已添加了一个新的语言关键字 **Hidden** ，用于指定默认情况下成员（属性或方法）不显示在 Get-Member 结果中（除非添加了 -Force 参数）。
  已标记为隐藏的属性或方法也不会出现在 IntelliSense 结果中，除非你位于成员应为可见的上下文中；例如，当在类方法中时自动变量 $This 应显示隐藏成员。
- 已增强了 New-Item、Remove-Item、Get-ChildItem 的功能，用于支持创建和管理[符号链接](https://en.wikipedia.org/wiki/Symbolic_link)。 New-Item 的 **ItemType** 参数接受一个新的值 **SymbolicLink** 。 现在可通过运行 New-Item cmdlet 在单行中创建符号链接。
- Get-ChildItem 也有一个新的 -Depth 参数，可将该参数与 -Recurse 参数一起使用，以限制递归。 例如，Get-ChildItem -Recurse -Depth 2 从当前文件夹、当前文件夹中的所有子文件夹，以及子文件夹中的所有文件夹返回结果。
- 现在，使用 Copy-Item，可以将文件或文件夹从一个 Windows PowerShell 会话复制到另一个会话中；也就是说，可以将文件复制到已连接到远程计算机（包括正在运行 Nano Server 的计算机，因此没有其他接口）的会话中。 若要复制文件，请将 PSSession ID 指定为新的 -FromSession 和 -ToSession 参数的值，并添加 -Path 和 -Destination 以分别指定源路径和目标位置。 例如，Copy-Item -Path c:\\myFile.txt -ToSession $s -Destination d:\\destinationFolder。
- 除了控制台主机 ( **powershell.exe** ) 外，Windows PowerShell 转录已经得到改进以应用到所有主机应用程序（例如 Windows PowerShell ISE）。 脚本选项（包括启用 system-wide 脚本）可以通过启用“打开 PowerShell 脚本”  组策略设置（位于 Administrative Templates/Windows Components/Windows PowerShell）来进行配置。
- 新的“详细脚本跟踪”功能让你能够启用系统上使用的 Windows PowerShell 脚本的详细跟踪和分析。 在启用详细脚本跟踪后，Windows PowerShell 会将所有的脚本块记录到 **Microsoft-Windows-PowerShell/Operational** 的 Windows 事件跟踪 (ETW) 事件日志中。
- 从 Windows PowerShell 5.0 开始，新的加密消息语法 cmdlet 通过使用加密保护消息的 IETF 标准格式对内容的加密和解密提供支持，如 [RFC5652](https://tools.ietf.org/html/rfc5652) 中所述。 已将 Get-CmsMessage、Protect-CmsMessage 和 Unprotect-CmsMessage cmdlet 添加到 [Microsoft.PowerShell.Security](/powershell/module/Microsoft.PowerShell.Security) 模块中。
- [Microsoft.PowerShell.Utility](/powershell/module/Microsoft.PowerShell.Utility) 中新的 cmdlet 包括 Get-Runspace、Debug-Runspace、Get-RunspaceDebug、Enable-RunspaceDebug 和 Disable-RunspaceDebug，使你能够在运行空间上设置调试选型，以及在运行空间上开始和停止调试。 针对调试任意运行空间（即不是 Windows PowerShell 控制台或 Windows PowerShell ISE 会话默认的运行空间），Windows PowerShell 使你能够在脚本中设置断点，并添加了断点以停止脚本运行，直到你可以附加调试器来调试运行空间脚本。 已将对任意运行空间的嵌套调试支持添加到了运行空间的 Windows PowerShell 脚本调试器中。
- 已将一个新的 Format-Hex cmdlet 添加到了 [Microsoft.PowerShell.Utility](/powershell/module/Microsoft.PowerShell.Utility) 模块中。
  Format-Hex 使你可以以十六进制格式查看文本或二进制数据。
- 已将 Get-Clipboard 和 Set-Clipboard cmdlet 添加到了 [Microsoft.PowerShell.Utility](/powershell/module/Microsoft.PowerShell.Utility) 模块中；它们易于将内容传输到 Windows PowerShell 会话以及从其中传输内容。 剪贴板 cmdlet 支持图像、音频文件、文件列表和文本。
- 新的 Clear-RecycleBin cmdlet 已添加到 [Microsoft.PowerShell.Management](/powershell/module/Microsoft.PowerShell.Management) 模块中；此 cmdlet 清空固定驱动器（包括外部驱动器）的回收站。 默认情况下，你会收到确认 Clear-RecycleBin 命令的提示，因为该 cmdlet 的 ConfirmImpact 属性设置为 ConfirmImpact.High。
- 新的 New-TemporaryFile cmdlet 使你能够创建临时文件作为脚本的一部分。 默认情况下，新的临时文件创建在 ```C:\Users\<user name>\AppData\Local\Temp``` 中。
- Out-File、Add-Content 和 Set-Content cmdlet 现在有一个新的 -NoNewline 参数，使用该参数将在输出后省略新的行。
- New-Guid cmdlet 利用 .NET Framework Guid 类以生成 GUID，这在当你正在编写脚本或 DSC 资源时很有用。
- 由于文件版本信息可能会产生误导（尤其是在修补文件后），因此新的 FileVersionRaw 和 ProductVersionRaw 脚本属性可用于 FileInfo 对象。 例如，可以运行下面的命令来显示 powershell.exe 的这些属性值，其中 $pid 包含正在运行的 Windows PowerShell 会话的进程 ID：`Get-Process -Id $pid -FileVersionInfo | Format-List *version* -Force`
- 新的 Enter-PSHostProcess 和 Exit-PSHostProcess cmdlet 使你能够在独立于正在 Windows PowerShell 控制台中运行的当前进程的进程中调试 Windows PowerShell 脚本。 运行 Enter-PSHostProcess 以输入或附上一个特定的进程 ID，然后运行 Get-Runspace 以返回进程内活动的运行空间。 当你完成进程内的脚本调试后，运行 Exit-PSHostProcess 从进程中分离出来。
- 已将一个新的 Wait-Debugger cmdlet 添加到了 [Microsoft.PowerShell.Utility](/powershell/module/Microsoft.PowerShell.Utility) 模块中。 在脚本中运行下一个语句时，可运行 Wait-Debugger 以停止调试器中的脚本。
- Windows PowerShell 工作流调试器现在支持命令或 Tab 自动补全，并且你可以调试嵌套的工作流函数。 现在，可以按 **Ctrl+Break** 进入正在运行的脚本、本地和远程会话以及工作流脚本中的调试器。
- 已将 Debug-Job cmdlet 添加到 [Microsoft.PowerShell.Core](/powershell/module/Microsoft.PowerShell.Core) 模块中，用于调试 Windows PowerShell 工作流、后台以及在远程会话中运行的作业的运行作业脚本。
- 已为 Windows PowerShell 作业添加一个新状态 AtBreakpoint。 AtBreakpoint 状态在作业正在运行包含设置断点的脚本以及脚本命中断点时应用。 当作业在调试断点处停止时，必须运行 Debug-Job cmdlet 来调试该作业。
- Windows PowerShell 5.0 实现了在 $PSModulePath 中的相同文件夹内对单个 Windows PowerShell 模块的多个版本的支持。 已将 RequiredVersion 属性添加到了 ModuleSpecification 类中，用于帮助获取模块的所需版本；此属性与 ModuleVersion 属性相互排斥。 RequiredVersion 现在作为 Get-Module、Import-Module 和 Remove-Module cmdlet 的 FullyQualifiedName 参数的值的一部分受到支持。
- 你现在可以通过运行 Test-ModuleManifest cmdlet 执行模块版本验证。
- 现在 Get-Command cmdlet 的结果显示版本列；一个新的版本属性已添加到 CommandInfo 类中。 Get-Command 从相同模块的多个版本中显示命令。 Version 属性也是 CmdletInfo 的派生类的一部分：CmdletInfo 和 ApplicationInfo。
- Get-Command 拥由一个新的参数 -ShowCommandInfo，它将 ShowCommand 信息作为 PSObjects 返回。 当通过使用 Windows PowerShell 远程在 Windows PowerShell ISE 中运行 Show-Command 时，这是非常有用的功能。 -ShowCommandInfo 参数替换了 Microsoft.PowerShell.Utility 模块中现有的 Get-SerializedCommand 函数，但 Get-SerializedCommand 脚本仍可用于支持下层脚本。
- 新的 Get-ItemPropertyValue cmdlet 使你能够获取属性的值，而无需使用点表示法。 例如，在 Windows PowerShell 的较旧版本中，可以运行以下命令来获取 PowerShellEngine 注册表项的 Application Base 属性的值：(Get-ItemProperty -Path HKLM:\\SOFTWARE\\Microsoft\\PowerShell\\3\\PowerShellEngine -Name ApplicationBase).ApplicationBase  。 从 PowerShell 5.0 开始，可运行 **Get-ItemPropertyValue -Path HKLM:\\SOFTWARE\\Microsoft\\PowerShell\\3\\PowerShellEngine -Name ApplicationBase** 。
- Windows PowerShell 控制台现在使用语法着色，就像 Windows PowerShell ISE 中一样。
- 新的 NetworkSwitch 模块包括的 cmdlet 使你能够将交换机、虚拟 LAN (VLAN) 和基本第 2 层网络交换机端口配置应用到 Windows Server 2012 R2 徽章认证的网络交换机中。
- 已将 FullyQualifiedName 参数添加到 Import-Module 和 Remove-Module cmdlet 中，用于支持存储单个模块的多个版本。
- Save-Help、Update-Help、Import-PSSession、Export-PSSession 和 Get-Command 拥有一个新的参数，ModuleSpecification 类型的 FullyQualifiedModule。 添加此参数以按模块的完全限定名称来指定它。
- **$PSVersionTable.PSVersion** 的值已更新为 5.0。
- WMF 5.0 (PowerShell 5.0) 包括 Pester  模块。 Pester 是 PowerShell 的单元测试框架。 它提供了几个易于使用的关键字，可用于为脚本创建测试。

### <a name="new-features-in-windows-powershell-desired-state-configuration"></a>Windows PowerShell Desired State Configuration 中的新增功能

- Windows PowerShell 语言增强功能使你能够通过使用类来定义 Windows PowerShell Desired State Configuration (DSC) 资源。 Import-DscResource 现在是一个真正的动态关键字；Windows PowerShell 分析指定模块的根模块，搜索包含 DscResource 特性的类。 现在可使用类来定义 DSC 资源，其中既不需要模块文件夹中的 MOF 文件，也不需要模块文件夹中的 DSCResource 子文件夹。 Windows PowerShell 模块文件可以包含多个 DSC 资源类。
- 新的 ThrottleLimit 参数已添加到 PSDesiredStateConfiguration 模块中的以下 cmdlet。 添加 ThrottleLimit 参数以指定你希望命令同时在上面进行工作的目标计算机或设备的数量。
  - Get-DscConfiguration
  - Get-DscConfigurationStatus
  - Get-DscLocalConfigurationManager
  - Restore-DscConfiguration
  - Test-DscConfiguration
  - Compare-DscConfiguration
  - Publish-DscConfiguration
  - Set-DscLocalConfigurationManager
  - Start-DscConfiguration
  - Update-DscConfiguration
- 通过集中式的 DSC 错误报告，丰富的错误信息不仅可以记录在事件日志中，同样也可以发送到一个中心位置以供日后分析使用。 可以使用此中心位置来存储在其环境中针对任何服务器而发生的 DSC 配置错误。 在元配置中定义报表服务器后，所有的错误会发送到报表服务器，然后存储在数据库中。 无论是否已配置目标节点以从请求服务器中请求配置，你都可以设置此功能。
- 针对 Windows PowerShell ISE 的改进使创作 DSC 资源变得轻松。 现在可以执行以下操作。
  - 通过在块内的空行上输入 **Ctrl+Space** ，列出 **配置** 或 **节点** 块内的所有 DSC 资源。
  - **枚举** 类型的资源属性的自动完成。
  - DSC 资源的 **DependsOn** 属性的自动完成基于配置中的其他资源实例。
  - 改进的资源属性值的 Tab 自动补全。
- 用户现在可以通过将 **PSDscRunAsCredential** 特性添加到节点块来运行一组指定凭据下的某个资源。 例如，PSDscRunAsCredential = Get-Credential Contoso\\DscUser。 此功能可用于创建配置来运行 Windows Installer 和可执行的安装程序、访问基于用户的注册表配置单元或执行当前用户上下文以外的其他任务。
- 已为 **Configuration** 关键字添加 32 位（基于 x86）的支持。
- Windows PowerShell 现在包括对 DSC 配置的自定义帮助的支持，该帮助是由通过将 \[CmdletBinding()] 添加到生成的配置函数来定义的。
- 新的 **DscLocalConfigurationManager** 特性将配置块设指定为元配置，用于配置 DSC 本地配置管理器。 此特性将配置限制为仅包含配置 DSC 本地配置管理器的项。 在处理期间，此配置生成 \*.meta.mof 文件，然后通过运行 Set-DscLocalConfigurationManager cmdlet 将其发送到相应的目标节点。
- Windows PowerShell 5.0 中现允许部分配置。 可以将配置文档以片段的形式传递到节点。 对于要接收配置文档的多个片段的节点，必须将其本地配置管理器首先设置为指定预期片段
- 跨计算机同步是 Windows PowerShell 5.0 中 DSC 中的新增功能。 通过使用内置 WaitFor\* 资源（ **WaitForAll** 、 **WaitForAny** 和 **WaitForSome** ），你现可在配置运行期间指定跨计算机的依赖关系，而无需外部业务流程。 以下资源通过 WS-Man 协议使用 CIM 连接进行节点到节点同步。
  配置可以等待另一台计算机特定的资源状态更改。
- Just Enough Administration (JEA) 是一个新的委派安全性功能，它利用 DSC 和 Windows PowerShell 受限运行空间以帮助保护企业免于数据丢失或员工（有意或无意）造成的泄露。 若要详细了解 JEA（包括从哪里可下载 xJEA DSC 资源），请参阅 [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview)。
- 以下新的 cmdlet 已添加到 PSDesiredStateConfiguration 模块中。
  - 新的 Get-DscConfigurationStatus cmdlet 从目标节点中获取有关配置状态的高级信息。 你可以获取最近的状态或所有配置。
  - 新的 Compare-DscConfiguration cmdlet 将指定的配置与一个或多个目标节点的实际状态进行比较。
  - 新的 Publish-DscConfiguration cmdlet 将配置 MOF 文件复制到目标节点，但不应用该配置。 将在下次一致性通过时或运行 Update-DscConfiguration cmdlet 时应用此配置。
  - 新的 Test-DscConfiguration cmdlet 使你能够验证生成的配置是否与所需的配置相匹配，如果该配置与所需配置相匹配，则返回 True，或如果实际配置与所需配置不匹配，则返回 False。
  - 新的 Update-DscConfiguration cmdlet 强制处理配置。 如果本地配置管理器处于请求模式下，该 cmdlet 将先从请求服务器中获取配置，然后再应用它。

### <a name="new-features-in-windows-powershell-ise"></a>Windows PowerShell ISE 中的新增功能

- 现在可以通过运行 Enter-PSSession 在存储你希望编辑的文件的计算机上启动远程会话，然后运行 PSEdit \<path and file name on the remote computer\> 以在 Windows PowerShell ISE 的本地副本中编辑远程 Windows PowerShell 脚本和文件。 此功能实现轻松编辑存储在 Windows Server 的服务器核心安装选项（Windows PowerShell ISE 无法在其中运行）上的 Windows PowerShell 文件。
- Windows PowerShell ISE 中现在支持 Start-Transcript cmdlet。
- 现在可以在 Windows PowerShell ISE 中调试远程脚本。
- 新的菜单命令 **Break All** (Ctrl+B) 会强行进入本地和远程运行的脚本的调试器中。

### <a name="new-features-in-windows-powershell-web-services-management-odata-iis-extension"></a>Windows PowerShell Web 服务（Management OData IIS 扩展）中的新增功能

- 从 Windows PowerShell 5.0 开始，你可以通过运行 Export-ODataEndpointProxy cmdlet（位于新的 [Microsoft.PowerShell.OdataUtils](/powershell/module/microsoft.powershell.odatautils) 模块中），基于由给定 OData 终结点暴露的功能来生成一组 Windows PowerShell cmdlet。

### <a name="notable-bug-fixes-in-windows-powershell-50"></a>Windows PowerShell 5.0 中值得注意的 Bug 修复

- Windows PowerShell 5.0 包含新的 COM 实现，在你使用 COM 对象时它可以提供显著的性能改进。 有关效果的视频演示，请参阅 [Com_Perf_Improvements](https://1drv.ms/1qu3UPZ)。
- 对 Windows PowerShell 会话中的第一个 Tab 自动补全进行了显著的性能改进，由此将 Tab 自动补全时间缩短了近 500ms。

## <a name="new-features-in-windows-powershell-40"></a>Windows PowerShell 4.0 中的新增功能

Windows PowerShell 4.0 可向后兼容。 为 Windows PowerShell 3.0 和 Windows PowerShell 2.0 设计的 Cmdlet、提供程序、模块、管理单元、脚本、函数和配置文件通常适用于 Windows PowerShell 4.0，无需更改。

Windows PowerShell 4.0 默认安装在 Windows 8.1 和 Windows Server 2012 R2 上。 若要在 Windows 7 SP1 或 Windows Server 2008 R2 上安装 Windows PowerShell 4.0，请下载并安装 [Windows Management Framework 4.0](https://www.microsoft.com/download/details.aspx?id=40855)。 请务必先阅读下载详细信息并确保满足所有系统要求，然后再安装 Windows Management Framework 4.0。

- [Windows PowerShell 中的新增功能](#new-features-in-windows-powershell-1)
- [Windows PowerShell 集成脚本环境 (ISE) 中的新增功能](#new-features-in-windows-powershell-integrated-scripting-environment-ise)
- [Windows PowerShell 工作流中的新增功能](#new-features-in-windows-powershell-workflow)
- [Windows PowerShell Web 服务中的新增功能](#new-features-in-windows-powershell-web-services)
- [Windows PowerShell Web 访问中的新增功能](#new-features-in-windows-powershell-web-access)
- [Windows PowerShell 4.0 中值得注意的 Bug 修复](#notable-bug-fixes-in-windows-powershell-40)

Windows PowerShell 4.0 包括以下新增功能。

### <a name="new-features-in-windows-powershell"></a><a name="new-features-in-windows-powershell-1" />Windows PowerShell 中的新增功能

- **Windows PowerShell Desired State Configuration** (DSC) 是 Windows PowerShell 4.0 中的新管理系统，可为软件服务和运行这些服务的环境部署和管理配置数据。 有关 DSC 的详细信息，请参阅 [Windows PowerShell Desired State Configuration 入门](/powershell/scripting/dsc/getting-started/wingettingstarted)。
- **Save-Help** 使你能够为安装在远程计算机上的模块保存帮助。 可以使用 Save-Help 从连接了 Internet 的客户端（不必在其上安装需要帮助的所有模块）下载模块“帮助”，然后将已保存的“帮助”复制到远程共享文件夹或无法访问 Internet 的远程计算机。
- Windows PowerShell 调试器已经过增强，从而允许对 Windows PowerShell 工作流以及在远程计算机上运行的脚本进行调试。 现在，Windows PowerShell 工作流都可以从 Windows PowerShell 命令行或 Windows PowerShell ISE 在脚本级别进行调试。 现在，可通过远程会话来调试 Windows PowerShell 脚本，包括脚本工作流。 远程调试会话是通过先断开连接再重新连接的 Windows PowerShell 远程会话保留的。
- **Register-ScheduledJob** 和 **Set-ScheduledJob** 的 **RunNow** 参数无需使用 **Trigger** 参数为作业设置即时启动日期和时间。
- **Invoke-RestMethod** 和 **Invoke-WebRequest** 现在使你能够使用 Headers 参数来设置所有标头。 虽然此参数一直存在，但它也是会导致异常或错误的 Web cmdlet 的几个参数之一。
- **Get-Module** 具有一个新参数 **FullyQualifiedName** ，其类型为 **ModuleSpecification\[]** 。 Get-Module 的参数 **FullyQualifiedName** 现在使你能够通过使用模块的名称、版本和 GUID（可选）来指定该模块。
- Windows Server 2012 R2 上的默认执行策略设置为 **RemoteSigned** 。 在 Windows 8.1 上，默认设置保持不变。
- 从 Windows PowerShell 4.0 开始，支持通过使用动态方法名称来调用方法。
  你可以使用变量来存储方法名称，然后通过调用该变量动态调用该方法。
- 超过由 **PSElapsedTimeoutSec** 工作流通用参数指定的超时期限时，不再删除异步工作流作业。
- 已向 **New-JobTrigger** 和 **Set-JobTrigger** cmdlet 添加新参数： **RepeatIndefinitely** 。 可在不指定 **RepetitionDuration** 参数的 **TimeSpan.MaxValue** 值的情况下无限期重复运行计划作业。
- 已向 **Enable-JobTrigger** 和 **Disable-JobTrigger** cmdlet 添加新参数： **Passthru** 。 Passthru 参数显示通过你的命令创建或修改的所有对象。
- **Add-Computer** 和 **Remove-Computer** cmdlet 中用于指定工作组的参数名称现在是一致的。 这两个 cmdlet 现在都使用 **WorkgroupName** 参数。
- 已添加新的通用参数： **PipelineVariable** 。 PipelineVariable 使你能够将某个通过管道传送的命令的结果（或该命令的一部分）另存为可通过管道的其余部分传递的一个变量。
- 现在支持使用方法语法筛选集合。 这意味着，现在可以通过使用简化的语法（类似于 Where() 或 Where-Object 的语法）采用方法调用的格式来筛选对象集合。 以下是一个示例：(Get-Process).where({$_.Name -match 'powershell'})
- **Get-Process** cmdlet 具有一个新的开关参数： **IncludeUserName** 。
- 已添加新 cmdlet **Get-FileHash** ，该 cmdlet 可返回采用几种格式之一的指定文件的文件哈希。
- 在 Windows PowerShell 4.0 中，如果某个模块在其清单中使用了 **DefaultCommandPrefix** 键，或者如果用户导入了一个带有 **Prefix** 参数的模块，则该模块的 **ExportedCommands** 属性将显示该模块中带有前缀的命令。 当你使用模块限定语法 ModuleName\\CommandName 来运行这些命令时，命令名称必须包含前缀。
- **$PSVersionTable.PSVersion** 的值已更新为 4.0。
- **Where()** 运算符行为已更改。 不再支持接受采用 `"Property -CompareOperator Value"` 格式的字符串表达式的 `Collection.Where('property -match name')`。
  但是， **Where()** 运算符可接受采用脚本块格式的字符串表达式；仍支持此行为。

### <a name="new-features-in-windows-powershell-integrated-scripting-environment-ise"></a>Windows PowerShell 集成脚本环境 (ISE) 中的新增功能

- Windows PowerShell ISE 同时支持 Windows PowerShell 工作流调试和远程脚本调试。
- 已为 Windows PowerShell Desired State Configuration 提供程序和配置添加 IntelliSense 支持。

### <a name="new-features-in-windows-powershell-workflow"></a>Windows PowerShell 工作流中的新增功能

- 已添加对迭代管道上下文中新的 **PipelineVariable** 通用参数的支持，其中迭代管道是指诸如这些由 System Center Orchestrator 所使用的管道；即相对于通过使用流式处理交错运行，只需从左到右运行命令的管道。
- 参数绑定已得到显著增强，从而在 Tab 自动补全情况以外的其他情况下使用，例如用于当前运行空间中不存在的命令。
- 已向 Windows PowerShell 工作流添加对自定义容器活动的支持。 如果某个活动参数 Activity\[] 属于类型 Activity（或为泛型活动集合），并且用户已提供一个脚本块作为实际参数，则 Windows PowerShell 工作流会将该脚本块转换为 XAML，正如处理普通的 Windows PowerShell 脚本到工作流编译一样   。
- 在发生崩溃之后，Windows PowerShell 工作流会自动重新连接到托管的节点。
- 你现在可以通过使用 **ThrottleLimit** 属性来限制 **Foreach -Parallel** 活动语句。
- **ErrorAction** 通用参数具有一个专用于工作流的新的有效值： **Suspend** 。
- 现在，如果不存在任何活动会话、进行中的作业和挂起的作业，则工作流终结点会自动关闭。 当满足自动关闭条件时，此功能可保存充当工作流服务器的计算机上的资源。

### <a name="new-features-in-windows-powershell-web-services"></a>Windows PowerShell Web 服务中的新增功能

- 当 Windows PowerShell Web 服务（PSWS，也称为“管理 OData IIS 扩展”）中发生错误时，则在 cmdlet 运行的同时，会向调用方返回更详细的错误消息。 此外，错误代码遵守 [Windows Azure REST API 错误代码指南](/rest/api/storageservices/Common-REST-API-Error-Codes)。
- 现在，终结点可以定义 API 版本，也可以强制使用特定的 API 版本。 每当客户端和服务器之间发生版本不匹配时，都会向客户端和服务器显示错误。
- 通过为调度架构中任何缺少的字段自动生成值，简化了该架构的管理操作。 即使调度架构不存在，生成也会发生，它是一个很有帮助的起点。
- 通过效仿 Windows PowerShell 中的 **PSTypeConverter** 的行为，PSWS 中的类型处理得到了改进，可支持使用除默认构造函数以外的其他构造函数的类型。 这使你能够通过 PSWS 使用复杂类型。
- PSWS 现在允许在运行查询的同时扩展关联的实例。 对于较大的二进制内容（如图像、音频或视频），传输成本相当高，最好在未编码的情况下传输二进制数据。 PSWS 将命名的资源流用于传输，无需编码。
  命名的资源流是 **Edm.Stream** 类型的实体的属性。 每个命名的资源流都具有针对 GET 或 UPDATE 操作的单独 URI。
- OData 操作现在提供一种用于对资源调用非 CRUD（Create、Read、Update 和 Delete）方法的机制。 你可以通过将 HTTP POST 请求发送到为操作定义的 URI 来调用该操作。 操作参数是在 POST 请求的正文中定义的。
- 为了与 Windows Azure 指南保持一致，所有的 URL 都应简化。 包含在 **Key As Segment** 中的更改允许以分段形式表示单独的键。 请注意，使用多个键值的引用仍旧要求值以逗号分隔并用括号括起来。
- 在此版本的 PSWS 之前，执行 Create、Update 或 Delete 操作的唯一方式是对顶级资源调用 Post、Put 或 Delete。 此版本的 PSWS 中新增了 Contained Resource 操作，它使用户能够获得相同的结果却不必如此直接地访问相同的资源，如同在这些资源已包含在内的情况下进行访问。

### <a name="new-features-in-windows-powershell-web-access"></a>Windows PowerShell Web 访问中的新增功能

- 在基于 Web 的 Windows PowerShell Web 访问控制台中，你可以断开现有会话的连接，然后重新连接到这些会话。 基于 Web 的控制台中的“ **保存** ”按钮使你可以在不删除会话的情况下断开与它的连接，然后在下次重新连接到该会话。
- 默认参数可以显示在登录页上。 若要显示默认参数，请在名为 **web.config** 的文件中为显示在登录页的“ **可选的连接设置** ”区域中的所有设置配置值。可以使用 **web.config** 文件来配置所有可选的连接设置（一组辅助或备用凭据除外）。
- 在 Windows Server 2012 R2 中，可以远程管理 Windows PowerShell Web 访问的授权规则。 **Add-PswaAuthorizationRule** 和 **Test-PswaAuthorizationRule** cmdlet 现在包含一个 Credential 参数，该参数使管理员能够从远程计算机或在 Windows PowerShell Web 访问会话中管理授权规则。
- 现在，你可以通过将新的浏览器选项卡用于每个会话，在单个浏览器会话中实现多个 Windows PowerShell Web 访问会话。 你不再需要打开新的浏览器会话，即可连接到基于 Web 的 Windows PowerShell 控制台中的新会话。

### <a name="notable-bug-fixes-in-windows-powershell-40"></a>Windows PowerShell 4.0 中值得注意的 Bug 修复

- **Get-Counter** 现在可以返回法语版 Windows 中包含一个撇号字符的计数器。
- 你现在可以查看反序列化对象上的 **GetType** 方法。
- **#Requires** 语句现在允许用户获得管理员访问权限（如果需要）。
- **Import-Csv** cmdlet 现在忽略空白行。
- 已修复运行 **Invoke-WebRequest** 命令时 Windows PowerShell ISE 占用太多内存的问题。
- **Get-Module** 现在可在 **Version** 列中显示模块版本。
- 不出所料，现在 Remove-Item -Recurse 会删除子文件夹中的项。
- 已向 **Get-Process** 输出对象添加 **UserName** 属性。
- **Invoke-RestMethod** cmdlet 现在可返回所有可用结果。
- **Add-Member** 现在将对哈希表生效，即使尚未访问这些哈希表。
- **Select-Object -Expand** 在属性值为 null 或空时不再失败或生成异常。
- **Get-Process** 现在可与用于从对象中获取 **ComputerName** 属性的其他命令一起在管道中使用。
- **ConvertTo-Json** 和 **ConvertFrom-Json** 现在可以接受用双引号引起来的术语，并且其错误消息现在可以进行本地化。
- **Get-Job** 现在返回所任何已完成的计划作业，甚至是新会话中的计划作业。
- 已修复在 Windows PowerShell 4.0 中使用 **FileSystem** 提供程序装载和卸载 VHD 的问题。 现在，当新的驱动器装载在相同的会话中时，Windows PowerShell 能够检测到这些驱动器。
- 不再需要显式地加载 **ScheduledJob** 或 **Workflow** 模块即可使用其作业类型。
- 已对以下过程进行了性能改进：导入用于定义嵌套工作流的工作流；此过程现在速度更快。

## <a name="new-features-in-windows-powershell-30"></a>Windows PowerShell 3.0 中的新增功能

Windows PowerShell 3.0 包括以下新增功能。

- [Windows PowerShell 工作流](#windows-powershell-workflow)
- [Windows PowerShell Web 访问](#windows-powershell-web-access)
- [新的 Windows PowerShell ISE 功能](#new-windows-powershell-ise-features)
- [对 Microsoft .NET Framework 4.0 的支持](#support-for-microsoft-net-framework-4)
- [对 Windows 预安装环境的支持](#support-for-windows-preinstallation-environment)
- [断开连接的会话](#disconnected-sessions)
- [稳定的会话连接](#robust-session-connectivity)
- [可更新的帮助系统](#updatable-help-system)
- [增强的联机帮助](#enhanced-online-help)
- [CIM 集成](#cim-integration)
- [会话配置文件](#session-configuration-files)
- [计划作业和任务计划程序集成](#scheduled-jobs-and-task-scheduler-integration)
- [Windows PowerShell 语言增强功能](#windows-powershell-language-enhancements)
- [新的核心 Cmdlet](#new-core-cmdlets)
- [对现有核心 Cmdlet 和提供程序的改进](#improvements-to-existing-core-cmdlets-and-providers)
- [远程模块导入和发现](#remote-module-import-and-discovery)
- [增强的 Tab 自动补全](#enhanced-tab-completion)
- [模块自动加载](#module-auto-loading)
- [模块体验改进](#module-experience-improvements)
- [简化的命令发现](#simplified-command-discovery)
- [改进的日志记录、诊断和组策略支持](#improved-logging-diagnostics-and-group-policy-support)
- [格式设置和输出改进](#formatting-and-output-improvements)
- [增强的控制台主机体验](#enhanced-console-host-experience)
- [新的 Cmdlet 和宿主 API](#new-cmdlet-and-hosting-apis)
- [性能改进](#performance-improvements)
- [运行身份和共享主机支持](#runas-and-shared-host-support)
- [特殊字符处理改进](#special-character-handling-improvements)

### <a name="windows-powershell-workflow"></a>Windows PowerShell 工作流程

Windows PowerShell 工作流将 Windows Workflow Foundation 的强大功能引入到 Windows PowerShell 中。
你可以采用 XAML 或 Windows PowerShell 语言编写工作流，然后像运行 cmdlet 一样运行它们。 `Get-Command` cmdlet 获取工作流命令，而 `Get-Help` cmdlet 则获取工作流帮助。

工作流是多计算机管理活动序列，其特点是长期运行、可重复、频繁、可并行化、可中断、可挂起并且可重启。 工作流可以从有意或意外中断（例如网络中断、Windows 重新启动或电源故障）中恢复。

工作流也是便携式的；它们可作为 XAML 文件导出或从 XAML 文件中导入。 你可以编写自定义会话配置，这些配置允许工作流或工作流中的活动由获委派的或下级用户操作。

以下是 Windows PowerShell 工作流的优势

- 自动运行有序的、长期运行的任务。
- **远程监控长期运行的任务** 。 活动的状态和进度随时可见。
- **多计算机管理。** 同时在数百个托管节点上将任务作为工作流运行。
  Windows PowerShell 工作流包含了一个内置的常用管理参数（例如 **PSComputerName** ）库，实现了多计算机管理方案。
- **复杂进程的单个任务执行。** 你可将实施整个端到端方案的相关脚本集成到单个工作流中。
- **暂留。** ：工作流保存在由其作者定义的特定点上（或在这些点上对工作流执行检查点），以便你可以从最后暂留的任务（或检查点）恢复该工作流，而不是从开头重启该工作流。
- **稳定性。** 自动的故障恢复。 工作流支持计划和非计划的重新启动。 你可以挂起工作流执行，然后从最后一个暂留点恢复该工作流。
  工作流作者可以指定当在一个或多个托管节点上出现故障时，要重新运行的特定活动。
- **断开连接、重新连接以及在已断开连接的会话中运行的能力。** 用户可以连接和断开工作流服务器，但工作流依旧继续运行。 你可以注销客户端计算机或重新启动客户端计算机，并通过其他计算机监视工作流执行，而不中断工作流。
- **计划。** 可以像计划任何 Windows PowerShell cmdlet 或脚本那样计划工作流任务。
- **工作流和连接限制。** 可以限制工作流执行和到节点的连接，从而实现可扩展性且高可用性的方案。

### <a name="windows-powershell-web-access"></a>Windows PowerShell Web 访问

Windows PowerShell Web 访问是一项 Windows Server 2012 功能，它允许用户在基于 Web 的控制台中运行 Windows PowerShell 命令和脚本。 使用基于 Web 的控制台的设备不需要安装 Windows PowerShell、远程管理软件或浏览器插件。 只需要正确配置的 Windows PowerShell Web 访问网关以及支持 JavaScript 和接受 Cookie 的客户端设备浏览器。

有关详细信息，请参阅[部署 Windows PowerShell Web 访问](/previous-versions/powershell/scripting/components/web-access/install-and-use-windows-powershell-web-access)。

### <a name="new-windows-powershell-ise-features"></a>新的 Windows PowerShell ISE 功能

对于 Windows PowerShell 3.0 来说，Windows PowerShell 集成脚本环境 (ISE) 具有许多新增功能，包括 IntelliSense、显示命令窗口、统一的控制台窗格、代码段、大括号匹配、展开/折叠部分、自动保存、最近使用的项列表、批量复制、块复制，以及对编写 Windows PowerShell 脚本工作流的完全支持。 有关详细信息，请参阅 [about_Windows_PowerShell_ISE](/powershell/module/microsoft.powershell.core/about/about_windows_powershell_ise)。

### <a name="support-for-microsoft-net-framework-4"></a>对 Microsoft .NET Framework 4 的支持

Windows PowerShell 是针对公共语言运行时 4.0 而构建的。 Cmdlet、脚本和工作流作者可以在 Windows PowerShell 中使用新的 Microsoft .NET Framework 4 类，其功能包括应用程序兼容性和部署、Managed Extensibility Framework、并行计算、网络、Windows Communication Foundation 和 Windows Workflow Foundation。

### <a name="support-for-windows-preinstallation-environment"></a>对 Windows 预安装环境的支持

Windows PowerShell 3.0 是 Windows 8 的 Windows 预安装环境 (Windows PE) 4.0 中的可选组件。 Windows PE 是用于启动没有操作系统的计算机并使其为 Windows 安装做好准备的最小操作系统。 Windows PE 可用于对硬盘驱动器进行分区和格式设置、将磁盘映像复制到计算机，以及从网络共享启动 Windows 安装程序。
可以在 Windows PE 上使用 Windows PowerShell 3.0 来管理部署、诊断和恢复方案。

### <a name="disconnected-sessions"></a>断开连接的会话

从 Windows PowerShell 3.0 开始，你使用 New-PSSession cmdlet 创建的用户托管的永久会话（“Pssession”）将保存在远程计算机上。 它们将不再依赖于创建它们的会话。

你现在可以在不中断在会话中运行的命令的情况下断开与该会话的连接。 你可以关闭该会话并关闭计算机。 稍后，你可以从相同或不同计算机上的另一个会话重新连接到该会话。

`Get-PSSession` cmdlet 的 ComputerName  参数现在获取用户所有连接到计算机的会话，即使会话是在其他计算机上的不同会话中启动的，也不例外。 你可以连接到这些会话、获取命令结果、启动新的命令，然后断开与该会话的连接。

新增了 cmdlet（包括 `Disconnect-PSSession`、`Connect-PSSession` 和 `Receive-PSSession`），以支持“已断开连接的会话”功能；同时还向管理 PSSession 的 cmdlet 添加了新参数，如 `Invoke-Command` cmdlet 的 InDisconnectedSession  参数。

仅当连接的源端（“客户端”）和终端（“服务器”）上的计算机都运行的是 Windows PowerShell 3.0 时，才支持“断开连接的会话”功能。

### <a name="robust-session-connectivity"></a>稳定的会话连接

Windows PowerShell 3.0 可检测到客户端和服务器之间的意外连接损失，然后自动尝试重新建立连接并恢复执行。 如果无法在分配的时间内重新建立客户端到服务器的连接，则会通知用户并且断开与会话的连接。 在尝试重新连接期间，Windows PowerShell 将向用户持续提供反馈。

如果已断开连接的会话是通过使用 InvokeCommand 启动的，则 Windows PowerShell 将为已断开连接的会话创建作业，以更加轻松地重新连接并恢复执行。

这些功能提供了更加可靠且更易恢复的远程体验，并允许用户执行需要稳定会话的长期运行的任务，例如工作流。

### <a name="updatable-help-system"></a>可更新的帮助系统

现在，你可以为模块中的 cmdlet 下载更新的帮助文件。 `Update-Help` cmdlet 发现最新的帮助文件，从 Internet 下载这些文件，解压缩并验证它们，然后将它们安装在模块的特定语言正确目录中。

若要使用更新的帮助文件，只需键入 `Get-Help`。 你无需重启 Windows 或 Windows PowerShell。 若要为 $pshome 目录中的模块更新帮助，请使用“以管理员身份运行”选项启动 Windows PowerShell。

为了支持没有连接到 Internet 的用户和防火墙后的用户，新 `Save-Help` cmdlet 将帮助文件下载到文件系统目录（如文件共享）中。 然后，用户可以使用 `Update-Help` cmdlet 从文件共享中获取更新后的帮助文件。

使用 `Update-Help` cmdlet，可以更新所有受支持 UI 区域性中全部或特定模块的帮助文件。 甚至可以将 `Update-Help` 命令置于 Windows PowerShell 配置文件中。
默认情况下，Windows PowerShell 每天下载模块帮助文件的次数不超过一次。

Windows 8 和 Windows Server 2012 模块不包含帮助文件。 若要下载最新的帮助文件，请键入 `Update-Help`。 有关详细信息，请键入 `Get-Help`（不带参数）或请参阅 [about_Updatable_Help](/powershell/module/microsoft.powershell.core/about/about_Updatable_Help)。

如果计算机上未安装 cmdlet 的帮助文件，`Get-Help` cmdlet 现在会显示自动生成的帮助。 自动生成的帮助中包含命令语法，以及关于如何使用 `Update-Help` cmdlet 下载帮助文件的说明。

任何模块作者都可为其模块提供“可更新的帮助”。 你可以将帮助文件包含在模块中并使用“可更新的帮助”来更新它们，或忽略帮助文件并使用“可更新的帮助”来安装它们。 若要详细了解如何支持“可更新的帮助”，请参阅[支持“可更新的帮助”](/powershell/scripting/developer/module/supporting-updatable-help)。

### <a name="enhanced-online-help"></a>增强的联机帮助

Windows PowerShell 联机帮助是面向所有用户的宝贵资源，但对于没有或无法安装更新的帮助文件的用户尤为重要。

若要获取任何 Windows PowerShell cmdlet 的联机帮助，请键入：

```
Get-Help <cmdlet-name> -Online
```

Windows PowerShell 在默认 Internet 浏览器中打开帮助主题的联机版本。

Windows PowerShell 3.0 中的 **Get-Help -Online** 功能现在更加强大了，因为即使未在计算机上安装 cmdlet 的帮助文件，它也起作用。 **Get-Help -Online** 功能从 cmdlet 和高级函数的 HelpUri 属性中获取联机帮助主题的 URI。

```
PS C:\>(Get-Command Get-ScheduledJob).HelpUri
https://go.microsoft.com/fwlink/?LinkID=223923
```

从 Windows PowerShell 3.0 开始，C# cmdlet 的作者可以通过在 cmdlet 类上创建 **HelpUri** 特性来填充 **HelpUri** 属性。 高级函数的作者可以在 **CmdletBinding** 特性上定义 **HelpUri** 属性。 **HelpUri** 属性的值必须以“http”或“https”开头。

你也可以将 **HelpUri** 值包含在基于 XML 的 cmdlet 帮助文件的第一个相关链接中，或包含在函数中基于注释的帮助的 .Link 指令中。

有关支持联机帮助的详细信息，请参阅 Microsoft Docs 中的[支持联机帮助](/powershell/scripting/developer/module/supporting-online-help)。

### <a name="cim-integration"></a>CIM 集成

Windows PowerShell 3.0 中包括对通用信息模型 (CIM) 的支持，CIM 为系统、网络、应用程序和服务提供了管理信息的通用定义，从而允许它们在异类系统之间交换管理信息。 Windows PowerShell 3.0 中对 CIM 的支持，包括基于新的或现有的 CIM 类编写 Windows PowerShell cmdlet 的能力、基于 cmdlet 定义 XML 文件编写命令的能力、对 CIM .NET Framework 的支持。 API、CIM 管理 cmdlet 和 WMI 2.0 提供程序。

### <a name="session-configuration-files"></a>会话配置文件

从 Windows PowerShell 3.0 开始，你可以通过使用文件来设计自定义会话配置。
新的会话配置文件使你能够确定使用会话配置的会话环境，包括向会话中加载哪些模块、脚本和格式文件、用户可以使用哪些 cmdlet 和语言元素、可以运行哪些模块和脚本以及可以看到哪些变量。

你可以设计用户只能在其中运行来自一个特定模块的 cmdlet 的会话，或用户在其中具有完整的语言、对所有模块的访问权限，以及对可执行高级任务的脚本的访问权限的会话。

在以前版本的 Windows PowerShell 中，仅为那些可以编写 C# 程序或复杂启动脚本的用户提供此级别的控制。 现在，计算机上“管理员”组中的任何成员都可以通过使用配置文件来自定义会话配置。

若要创建会话配置文件，请使用 `New-PSSessionConfigurationFile` cmdlet。 若要将会话配置文件应用于会话配置，请使用 `Register-PSSessionConfiguration` 或 Set-PSSessionConfiguration cmdlet。

有关详细信息，请参阅 [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files) 和 `New-PSSessionConfigurationFile`。

### <a name="scheduled-jobs-and-task-scheduler-integration"></a>计划作业和任务计划程序集成

现在可以计划 Windows PowerShell 后台作业，并在 Windows PowerShell 和任务计划程序中对其进行管理。

Windows PowerShell 计划作业是 Windows PowerShell 后台作业和“任务计划程序”任务的有用结合。

与 Windows PowerShell 后台作业一样，计划作业以异步方式在后台运行。
可以使用作业 cmdlet（如 `Start-Job` 和 `Get-Job`），管理已完成的计划作业实例。

与“任务计划程序”任务一样，你可以按一次性或重复计划运行计划作业，或者根据操作或事件运行它们。 你可以在“任务计划程序”中查看和管理计划作业、按需启用和禁用它们、将其作为模板运行或使用，并设置启动作业的条件。

此外，计划作业还附带用于管理它们的一组自定义 cmdlet。 这些 cmdlet 使你能够创建、编辑、管理、禁用和重新启用计划作业，创建计划作业触发器并设置计划作业选项。

有关计划作业的详细信息，请参阅 [about_Scheduled_Jobs](/powershell/module/psscheduledjob/about/about_scheduled_jobs)。

### <a name="windows-powershell-language-enhancements"></a>Windows PowerShell 语言增强功能

Windows PowerShell 3.0 包括许多功能，旨在使其语言更简单、更易于使用并避免常见错误。 改进包括属性枚举、标量对象上的计数和长度属性、新的重定向运算符、$Using 作用域修饰符、PSItem 自动变量、灵活的脚本格式设置、变量特性、简化的特性参数、数字命令名称、停止分析运算符、改进的数组展开、新的位运算符、有序词典、PSCustomObject 强制转换和改进的基于注释的帮助。

### <a name="new-core-cmdlets"></a>新的核心 Cmdlet

已向 Windows PowerShell 核心安装添加新的 cmdlet，包括用于管理计划作业、已断开连接的会话、CIM 集成和“可更新的帮助系统”的 cmdlet。

- CimCmdlet
  - Get-CimAssociatedInstance
  - Get-CimClass
  - Get-CimInstance
  - Get-CimSession
  - Invoke-CimMethod
  - New-CimInstance
  - New-CimSession
  - New-CimSessionOption
  - Register-CimIndicationEvent
  - Remove-CimInstance
  - Remove-CimSession
  - Set-CimInstance
- Microsoft.PowerShell.Core
  - Connect-PSSession
  - Disconnect-PSSession
  - New-PSSessionConfigurationFile
  - New-PSTransportOption
  - Receive-PSSession
  - Resume-Job
  - Save-Help
  - Suspend-Job
  - Test-PSSessionConfigurationFile
  - Update-Help
- Microsoft.PowerShell.Diagnostics
  - New-WinEvent
- Microsoft.PowerShell.Management
  - Get-ControlPanelItem
  - Rename-Computer
  - Show-ControlPanelItem
- Microsoft.PowerShell.Utility
  - ConvertFrom-Json
  - ConvertTo-Json
  - Get-TypeData
  - Invoke-RestMethod
  - Invoke-WebRequest
  - Remove-TypeData
  - Show-Command
  - Unblock-File
- PSScheduledJob
  - Add-JobTrigger
  - Disable-JobTrigger
  - Disable-ScheduledJob
  - Enable-JobTrigger
  - Enable-ScheduledJob
  - Get-JobTrigger
  - Get-ScheduledJob
  - Get-ScheduledJobOption
  - New-JobTrigger
  - New-ScheduledJobOption
  - Register-ScheduledJob
  - Set-JobTrigger
  - Set-ScheduledJob
  - Set-ScheduledJobOption
  - Unregister-ScheduledJob
- PSWorkflow
  - New-PSWorkflowExecutionOption
  - New-PSWorkflowSession
- PSWorkflowUtility
  - Invoke-AsWorkflow
- ISE
  - Get-IseSnippet
  - Import-IseSnippet
  - New-IseSnippet

### <a name="improvements-to-existing-core-cmdlets-and-providers"></a>对现有核心 Cmdlet 和提供程序的改进

Windows PowerShell 3.0 中包括已有 cmdlet（包括简化的语法）的新增功能以及以下 cmdlet 的新参数：Computer cmdlet、CSV cmdlet、Get-ChildItem、Get-Command、Get-Content、Get-History、Measure-Object、Security cmdlet、Select-Object、Select-String、Split-Path、Start-Process、Tee-Object、Test-Connection、Add-Member 和 WMI cmdlet。

Windows PowerShell 提供程序也已得到明显改进，包括 Certificate 提供程序对管理用于 Web 托管的安全套接字层 (SSL) 证书的支持，对凭据、永久性网络驱动器以及文件系统驱动器中的备用数据流的支持。

### <a name="remote-module-import-and-discovery"></a>远程模块导入和发现

Windows PowerShell 3.0 扩展了远程计算机上的模块发现、导入和隐式远程功能。 Module cmdlet 可通过使用 Windows PowerShell 远程处理获取远程计算机上的模块，并将其导入到远程或本地计算机中。 通过将在远程计算机上隐式运行的命令导入到本地计算机中，新的 CIM 会话支持使你能够使用 CIM 和 WMI 来管理非 Windows 计算机。

有关详细信息，请参阅 `Get-Module` 和 `Import-Module` cmdlet 的帮助主题。

### <a name="enhanced-tab-completion"></a>增强的 Tab 自动补全

Windows PowerShell 控制台中的 Tab 自动补全现在可以自动补全 cmdlet 的名称、参数、参数值、枚举、.NET Frameworks 类型、COM 对象、隐藏的目录等等。
Tab 自动补全功能是基于新的分析程序和抽象语法树彻底重写的，旨在支持更多方案，包括内存中的分析树和中间部分 Tab 自动补全。

### <a name="module-auto-loading"></a>模块自动加载

`Get-Command` cmdlet 现在从计算机上安装的所有模块中获取全部 cmdlet 和函数，即使模块未导入到当前会话中，也不例外。

当你获得所需的 cmdlet 时，可以在不导入任何模块的情况下立即使用它。
现在，当你使用模块中的任何 cmdlet 时，Windows PowerShell 模块都会自动导入。 不再需要搜索模块并将其导入即可使用其 cmdlet。

自动导入模块是通过在命令中使用 cmdlet 触发的，即对没有通配符的 cmdlet 运行 `Get-Command` 或 `Get-Help`。

可以通过使用 **$PSModuleAutoLoadingPreference** 首选项变量来启用、禁用和配置模块的自动导入。

有关详细信息，请参阅 [about_Modules](/powershell/module/microsoft.powershell.core/about/about_modules)、[about_Preference_Variables](/powershell/module/microsoft.powershell.core/about/about_Preference_Variables)，以及 `Get-Command` 和 `Import-Module` cmdlet 的帮助主题。

### <a name="module-experience-improvements"></a>模块体验改进

Windows PowerShell 3.0 将高级功能支持引入了模块，包括以下新增功能。

1. 各个模块的模块日志记录 (LogPipelineExecutionDetails) 和新的“打开模块日志记录”组策略设置
2. 扩展了可公开模块清单中的值的模块对象
3. 新增了模块（包括嵌套模块）的 **ExportedCommands** 属性，该属性合并了所有类型的命令
4. 改进了可用（未导入）模块的发现，包括允许 **Path** 和 **ListAvailable** 参数位于同一命令中
5. 在模块清单中新增了 **DefaultCommandPrefix** 项，可在不更改模块代码的情况下避免名称冲突。
6. 改进了模块要求，包括附带版本和 GUID 的完全限定的所需模块和所需模块的自动导入
7. 更安静、更流畅地操作 `New-ModuleManifest` cmdlet。
8. 为 #Requires 新增了 **Module** 参数
9. 改进了包含 MinimumVersion  和 RequiredVersion  参数的 `Import-Module` cmdlet。

### <a name="simplified-command-discovery"></a>简化的命令发现

你不再需要导入所有模块即可发现可用于会话的命令。 在 Windows PowerShell 3.0 中，`Get-Command` cmdlet 从所有已安装的模块中获取全部命令。 而且，如果你使用了某个命令，则导出该命令的模块会自动导入到你的会话中。

新 `Show-Command` cmdlet 是专门为新手设计的。 你可以在窗口中搜索命令。 你可以查看所有命令或按模块筛选、通过单击按钮导入模块、使用文本框和下拉列表来构造一个有效命令，然后复制或运行该命令，而无需离开窗口。

### <a name="improved-logging-diagnostics-and-group-policy-support"></a>改进的日志记录、诊断和组策略支持

借助对 Windows 事件跟踪 (ETW) 日志、模块中可编辑的 **LogPipelineExecutionDetails** 属性和“打开模块日志记录”组策略设置的支持，Windows PowerShell 3.0 改进了对命令和模块的日志记录和跟踪支持。 你现在可以通过显示日志属性从日志详细信息中获取参数值。

### <a name="formatting-and-output-improvements"></a>格式设置和输出改进

新的格式设置和输出改进提高了所有 Windows PowerShell 用户的效率。 这些改进包括所有流的输出重定向、增强的 Update-Type cmdlet（可动态地添加类型而无需使用 Format.ps1xml 文件）、在输出中自动换行、自定义对象的默认格式设置属性、 **PSCustomObject** 类型、WMI 对象和异类对象的改进的格式设置，以及对发现方法重载的支持。

### <a name="enhanced-console-host-experience"></a>增强的控制台主机体验

在 Windows PowerShell 3.0 中，Windows PowerShell 控制台主机程序具有一些新增功能，其中默认包括单线程单元。 通过“文件资源管理器”中的新“使用 PowerShell 运行”选项，你只需通过右键单击即可在不受限制的会话中运行脚本。 新的控制台主机启动逻辑可更快地启动 Windows PowerShell，而且你可以使用新的字体个性化旧的控制台窗口体验。

### <a name="new-cmdlet-and-hosting-apis"></a>新的 Cmdlet 和宿主 API

新的 Cmdlet API 和宿主 API 包括公用高级语法树 (AST) API、管道分页 API、嵌套管道、运行空间池 Tab 自动补全、Windows RT、cmdlet 特性 Obsolete 以及 FunctionInfo 对象的 Verb 和 Noun 属性。

### <a name="performance-improvements"></a>性能改进

Windows PowerShell 中的显著性能改进来自于新的语言分析程序（它是在 .NET Framework 4 中的动态语言运行时 (DLR) 基础之上构建而成），以及运行时脚本编译、引擎可靠性提升和 `Get-ChildItem` 算法更改（提升了自身性能，尤其是在搜索网络共享时）。

### <a name="runas-and-shared-host-support"></a>运行身份和共享主机支持

Windows PowerShell 3.0 包括对运行身份和共享主机功能的支持。

*运行身份* 功能专用于 Windows PowerShell 工作流，使会话配置用户可以创建使用共享用户帐户的权限运行的会话。 这使权限较低的用户能够使用管理员权限来运行特定命令和脚本，而无需将太多较为低级的用户添加到“管理员”组。

**SharedHost** 功能允许多台计算机上的多个用户同时连接到工作流会话并监视工作流进度。 用户可以在一台计算机上启动工作流，然后连接到另一台计算机上的工作流会话，而无需断开会话与原始计算机的连接。 用户必须具有相同的权限，并且必须使用相同的会话配置。 有关详细信息，请参阅 Windows PowerShell 工作流入门中的“运行 Windows PowerShell 工作流”。

### <a name="special-character-handling-improvements"></a>特殊字符处理改进

为了提高 Windows PowerShell 3.0 解释和正确处理特殊字符的能力，用于处理路径中特殊字符的 LiteralPath  参数几乎对包含 Path  参数的所有 cmdlet 都有效，包括新增的 `Update-Help` 和 `Save-Help` cmdlet。 分析程序中还包括了特殊逻辑，用于改进对文件名和路径中的反撇号字符 (\`) 和方括号的处理。

## <a name="see-also"></a>另请参阅

- [about_Windows_PowerShell_5.0](/previous-versions/powershell/module/microsoft.powershell.core/about/about_windows_powershell_5.0)
- [Windows PowerShell](/powershell/)
