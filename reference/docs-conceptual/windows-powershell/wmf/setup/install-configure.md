---
ms.date: 06/10/2020
title: 安装和配置 WMF 5.1
description: 本文介绍如何安装 WMF 5.1 及其先决条件。
ms.openlocfilehash: 0e076bfab684b6c83d62d236eea3bbd7ab2ad411
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660834"
---
# <a name="install-and-configure-wmf-51"></a>安装和配置 WMF 5.1

> [!IMPORTANT]
> WMF 5.0 已被 WMF 5.1 取代。 使用 WMF 5.0 的用户必须升级到 WMF 5.1 才能接受支持。
> WMF 5.1 需要 .NET Framework 4.5.2 或更高版本。 安装将成功，但如果未安装 .NET 4.5.2 或更高版本，将无法使用主要功能。

## <a name="download-and-install-the-wmf-51-package"></a>下载和安装 WMF 5.1 包

下载适用于要在其中进行安装的操作系统和体系结构的 WMF 5.1 包：

| 操作系统       | 先决条件           | 包链接                          |
|------------------------|-------------------------|----------------------------------------|
| Windows Server 2012 R2 |                         | [Win8.1AndW2K12R2-KB3191564-x64.msu][] |
| Windows Server 2012    |                         | [W2K12-KB3191565-x64.msu][]            |
| Windows Server 2008 R2 | [.NET Framework 4.5.2][]| [Win7AndW2K8R2-KB3191566-x64.ZIP][]    |
| Windows 8.1            |                         | **x64：** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</br>**x86：** [Win8.1-KB3191564-x86.msu][] |
| Windows 7 SP1          | [.NET Framework 4.5.2][]| **x64：** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</br>**x86：** [Win7-KB3191566-x86.ZIP][] |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

- 安装 WMF 5.1 RTM 之前，必须先卸载 WMF 5.1 预览版。
- 可在 WMF 5.0 或 WMF 4.0 上直接安装 WMF 5.1。
- 在 Windows 7 和 Windows Server 2008 R2 上安装 WMF 5.1 前，无需安装 WMF 4.0。

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>安装适用于 Windows Server 2008 R2 和 Windows 7 的 WMF 5.1

> [!NOTE]
> 针对 Windows Server 2008 R2 和 Windows 7 的安装说明发生变化，不同于其他包的安装说明。 下文中介绍了针对 Windows Server 2012 R2、Windows Server 2012 和 Windows 8.1 的安装说明。

### <a name="wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a>Windows Server 2008 R2 SP1 和 Windows 7 SP1 的 WMF 5.1 系统必备

若要在 Windows Server 2008 R2 SP1 或 Windows 7 SP1 上安装 WMF 5.1，必须先安装以下各项：

- 必须安装最新 Service Pack。
- **不得** 安装 WMF 3.0。 安装 WMF 5.1 来替代 WMF 3.0 会导致 PSModulePath (`$env:PSModulePath`) 丢失，进而可能会导致其他应用无法正常运行。 安装 WMF 5.1 前，要么必须先卸载 WMF 3.0，要么必须先保存 PSModulePath，然后在 WMF 5.1 安装完成后进行手动还原。
- WMF 5.1 中至少需要[.NET Framework 4.5.2](https://www.microsoft.com/download/details.aspx?id=42642)。 可按照下载位置的说明安装 Microsoft .NET Framework 4.5.2。

### <a name="installing-wmf-51-on-windows-server-2008-r2-and-windows-7"></a>在 Windows Server 2008 R2 和 Windows 7 上安装 WMF 5.1

1. 转到在其中下载了 ZIP 文件的文件夹。

1. 右键单击 ZIP 文件，然后选择“全部提取...”。ZIP 文件包含两个文件：MSU 和 `Install-WMF5.1.ps1` 脚本文件。 解压缩 ZIP 文件后，便可以将内容复制到运行 Windows 7 或 Windows Server 2008 R2 的任何一台计算机上。

1. 提取 ZIP 文件内容后，以管理员身份打开 PowerShell，然后导航到包含 ZIP 文件内容的文件夹。

1. 在此文件夹中运行 `Install-WMF5.1.ps1` 脚本，然后按说明操作。 此脚本会在本地计算机上检查系统必备，如果系统必备已满足，则会安装 WMF 5.1。 下文中列出了系统必备。

   `Install-WMF5.1.ps1` 采用以下参数，以简化在 Windows Server 2008 R2 和 Windows 7 上自动执行安装：

   - **AcceptEula** ：如果包含此参数，将会自动接受但不显示 EULA。
   - **AllowRestart** ：只有在指定 AcceptEula 后，才能使用此参数。 如果包含此参数，并且在安装 WMF 5.1 后需要重启，将在安装完成后不发出提示就立即重启计算机。

## <a name="winrm-dependency"></a>WinRM 依赖关系

Windows PowerShell Desired State Configuration (DSC) 依赖 WinRM。 在 Windows Server 2008 R2 和 Windows 7 上默认不启用 WinRM。 若要启用 WinRM，在 Windows PowerShell 提升的会话中运行 `Set-WSManQuickConfig`。

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>安装适用于 Windows Server 2012 R2、Windows Server 2012 和 Windows 8.1 的 WMF 5.1

### <a name="install-from-windows-file-explorer"></a>从 Windows 文件资源管理器安装

1. 导航到在其中下载了 MSU 文件的文件夹。
1. 双击 MSU 以运行它。

### <a name="installing-from-the-command-prompt"></a>通过命令提示符进行安装

1. 下载适用于计算机体系结构的正确程序包后，使用提升的用户权限（以管理员身份运行）打开“命令提示符”窗口。 在 Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1 的服务器核心安装选项上，命令提示符默认使用提升的用户权限打开。
1. 将目录更改为向其中下载或复制 WMF 5.1 安装包的文件夹。
1. 运行下列命令之一：
   - 在运行 Windows Server 2012 R2 或 Windows 8.1 x64 的计算机上，运行 `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet /norestart`。
   - 在运行 Windows Server 2012 的计算机上，运行 `W2K12-KB3191565-x64.msu /quiet /norestart`。
   - 在运行 Windows 8.1 x86 的计算机上，运行 `Win8.1-KB3191564-x86.msu /quiet /norestart`。

   > [!NOTE]
   > 安装 WMF 5.1 需要重新启动。 单独使用 `/quiet` 选项将重新启动系统而不发出警告。 使用 `/norestart` 选项可避免重新启动。 但是，要重新启动才会安装 WMF 5.1。
