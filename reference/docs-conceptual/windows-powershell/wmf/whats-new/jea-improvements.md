---
ms.date: 06/12/2017
title: 对 Just Enough Administration (JEA) 的改进
description: JEA 是 WMF 5.0 中的新功能，可通过 PowerShell 远程处理实现基于角色的管理。 通过允许非管理员以管理员身份运行特定的命令、脚本和可执行文件，它扩展了现有受约束的终结点基础结构。
ms.openlocfilehash: f255d0ecbd4bbd9a5ade4b6e19f066cc007481fb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654019"
---
# <a name="improvements-to-just-enough-administration-jea"></a>对 Just Enough Administration (JEA) 的改进

Just Enough Administration 是 WMF 5.0 中的新功能，可通过 PowerShell 远程处理实现基于角色的管理。 通过允许非管理员以管理员身份运行特定的命令、脚本和可执行文件，它扩展了现有受约束的终结点基础结构。 这使你可以减少环境中的完全权限管理员数量并提高安全性。

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a>指向/来自 JEA 终结点的受约束的文件副本

现可将文件远程复制到 JEA 终结点或远程复制其中的文件，并确信连接用户不能复制你系统上的任意文件。 这可通过配置 PSSC 文件为连接用户安装用户驱动器来实现。 用户驱动器是新的 PSDrive，是每个连接用户特有的并跨会话保持。 当 `Copy-Item` 用于将文件复制到 JEA 会话或从中复制时，其被限制为仅允许访问用户驱动器。 将文件复制到任何其他 PSDrive 的尝试会失败。

若要在 JEA 会话配置文件中设置用户驱动器，请使用以下新字段：

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

将在 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\` 处创建支持用户驱动器的文件夹。 对于连接到终结点的每位用户，将创建一个具有 `$env:USERDOMAIN_$env:USERNAME` 名称的文件夹。

若要利用用户驱动器，并将文件复制到配置为公开用户驱动器的 JEA 终结点或从中复制文件，请使用 `Copy-Item` 上的 `-ToSession` 和 `-FromSession` 参数。

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine.
# You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

随后可编写自定义函数以处理用户驱动器中存储的数据，并将其提供“角色功能”文件中的用户。

## <a name="support-for-group-managed-service-accounts"></a>支持组托管服务帐户

在某些情况下，用户需在 JEA 会话中执行的任务可能需要访问本地计算机以外的资源 。 当 JEA 会话配置为使用虚拟帐户时，任何接触此类资源的尝试都将来自本地计算机的 ID，而非虚拟帐户或已连接用户。 TP5 现已开始支持在[组托管服务帐户](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\))上下文中运行 JEA，从而大大简化了使用域标识来访问网络资源的过程。

若要将 JEA 会话配置为在 gMSA 帐户下运行，请在 PSSC 文件中使用以下新密钥：

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> 组托管服务帐户不会隔离虚拟帐户或限制其范围。
> 每个连接用户都将共享同一 gMSA 标识，这一标识可能拥有整个企业范围内的权限。 选择使用 gMSA 时请格外小心；若可能，请始终优先使用限于本地计算机的虚拟帐户。

## <a name="conditional-access-policies"></a>条件访问策略

JEA 可很好地限制用户在连接到系统进行管理时可执行的操作；但如果你还想限制用户可使用 JEA 的 *时间* ，该如何操作？ 我们已向会话配置文件 (.pssc) 添加了配置选项，使你能够指定用户为建立 JEA 会话而必须归属的安全组。 如果你的环境中有实时 (JIT) 系统且希望你的用户在访问高权限 JEA 终结点前提升其权限，那么这将特别有用。

通过 PSSC 文件中的新 *RequiredGroups* 字段，你可指定用于确定用户是否可连接到 JEA 的逻辑。 它包括指定使用“And”和“Or”密钥来构造规则的哈希表（可选择嵌套）。 以下是如何使用此字段的一些示例：

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a>已修复：Windows Server 2008 R2 现支持虚拟帐户

在 WMF 5.1 中，现可在 Windows Server 2008 R2 上使用虚拟帐户，从而跨 Windows Server 2008 R2 - 2016 实现一致的配置和功能。 在 Windows 7 上使用 JEA 时，虚拟帐户仍不受支持。
