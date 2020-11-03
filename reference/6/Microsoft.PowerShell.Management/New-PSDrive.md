---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-psdrive?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSDrive
ms.openlocfilehash: 04346a3bd324b2d7033405546f131d2d56c5a2bd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93197718"
---
# <span data-ttu-id="cddb3-103">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="cddb3-103">New-PSDrive</span></span>

## <span data-ttu-id="cddb3-104">摘要</span><span class="sxs-lookup"><span data-stu-id="cddb3-104">SYNOPSIS</span></span>
<span data-ttu-id="cddb3-105">创建临时映射网络驱动器和永久映射网络驱动器</span><span class="sxs-lookup"><span data-stu-id="cddb3-105">Creates temporary and persistent mapped network drives.</span></span>

## <span data-ttu-id="cddb3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cddb3-106">SYNTAX</span></span>

### <span data-ttu-id="cddb3-107">全部</span><span class="sxs-lookup"><span data-stu-id="cddb3-107">All</span></span>

```
New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Description <String>]
 [-Scope <String>] [-Persist] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="cddb3-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cddb3-108">DESCRIPTION</span></span>

<span data-ttu-id="cddb3-109">该 `New-PSDrive` cmdlet 将创建映射到数据存储区中的位置或与数据存储区中的某个位置（例如网络驱动器、本地计算机上的目录或注册表项）以及与远程计算机上的文件系统位置关联的持久 Windows 映射网络驱动器的临时驱动器。</span><span class="sxs-lookup"><span data-stu-id="cddb3-109">The `New-PSDrive` cmdlet creates temporary and persistent drives that are mapped to or associated with a location in a data store, such as a network drive, a directory on the local computer, or a registry key, and persistent Windows mapped network drives that are associated with a file system location on a remote computer.</span></span>

<span data-ttu-id="cddb3-110">临时驱动器仅存在于当前 PowerShell 会话中以及在当前会话中创建的会话中。</span><span class="sxs-lookup"><span data-stu-id="cddb3-110">Temporary drives exist only in the current PowerShell session and in sessions that you create in the current session.</span></span> <span data-ttu-id="cddb3-111">它们的名称可以在 PowerShell 中有效，并且可以映射到任何本地或远程资源。</span><span class="sxs-lookup"><span data-stu-id="cddb3-111">They can have any name that is valid in PowerShell and can be mapped to any local or remote resource.</span></span> <span data-ttu-id="cddb3-112">您可以使用临时 PowerShell 驱动器访问关联数据存储中的数据，就像使用任何映射的网络驱动器一样。</span><span class="sxs-lookup"><span data-stu-id="cddb3-112">You can use temporary PowerShell drives to access data in the associated data store, just as you would do with any mapped network drive.</span></span> <span data-ttu-id="cddb3-113">您可以使用或来将位置更改到驱动器中，通过使用来 `Set-Location` 访问驱动器的内容 `Get-Item` `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="cddb3-113">You can change locations into the drive, by using `Set-Location`, and access the contents of the drive by using `Get-Item` or `Get-ChildItem`.</span></span>

<span data-ttu-id="cddb3-114">由于临时驱动器仅适用于 PowerShell，因此不能通过使用文件资源管理器、Windows Management Instrumentation (WMI) 、组件对象模型 (COM) 、Microsoft .NET 框架或使用 **NET use** 等工具来访问临时驱动器。</span><span class="sxs-lookup"><span data-stu-id="cddb3-114">Because temporary drives are known only to PowerShell, you can't access them by using File Explorer, Windows Management Instrumentation (WMI), Component Object Model (COM), Microsoft .NET Framework, or with tools such as **net use** .</span></span>

<span data-ttu-id="cddb3-115">PowerShell 3.0 中添加了以下功能 `New-PSDrive` ：</span><span class="sxs-lookup"><span data-stu-id="cddb3-115">The following features were added to `New-PSDrive` in PowerShell 3.0:</span></span>

- <span data-ttu-id="cddb3-116">映射的网络驱动器。</span><span class="sxs-lookup"><span data-stu-id="cddb3-116">Mapped network drives.</span></span> <span data-ttu-id="cddb3-117">你可以使用的 **持久** 参数 `New-PSDrive` 来创建 Windows 映射网络驱动器。</span><span class="sxs-lookup"><span data-stu-id="cddb3-117">You can use the **Persist** parameter of `New-PSDrive` to create Windows mapped network drives.</span></span> <span data-ttu-id="cddb3-118">与临时 PowerShell 驱动器不同，Windows 映射网络驱动器不是会话特定的。</span><span class="sxs-lookup"><span data-stu-id="cddb3-118">Unlike temporary PowerShell drives, Windows mapped network drives aren't session-specific.</span></span> <span data-ttu-id="cddb3-119">它们保存在 Windows 中，可以通过使用标准的 Windows 工具（例如文件资源管理器和 **net use** ）进行管理。</span><span class="sxs-lookup"><span data-stu-id="cddb3-119">They're saved in Windows and they can be managed by using standard Windows tools, such as File Explorer and **net use** .</span></span> <span data-ttu-id="cddb3-120">映射网络驱动器必须以驱动器号命名，并且连接到某个远程文件系统位置。</span><span class="sxs-lookup"><span data-stu-id="cddb3-120">Mapped network drives must have a drive-letter name and be connected to a remote file system location.</span></span> <span data-ttu-id="cddb3-121">如果命令的作用域为本地，则不会有任何点，则 **持久性** 参数不会在运行该命令的范围之外保存 **new-psdrive** 的创建。</span><span class="sxs-lookup"><span data-stu-id="cddb3-121">When your command is scoped locally, no dot-sourcing, the **Persist** parameter doesn't persist the creation of a **PSDrive** beyond the scope in which the command is running.</span></span> <span data-ttu-id="cddb3-122">如果在 `New-PSDrive` 脚本中运行，并且希望驱动器无限期地保留，则必须将脚本保存到点。</span><span class="sxs-lookup"><span data-stu-id="cddb3-122">If you're running `New-PSDrive` inside a script, and you want the drive to persist indefinitely, you must dot-source the script.</span></span> <span data-ttu-id="cddb3-123">为了获得最佳结果，若要强制新驱动器无限期保留，请将 **Scope** 参数添加到命令中，并将其值设置为 **Global** 。</span><span class="sxs-lookup"><span data-stu-id="cddb3-123">For best results, to force a new drive to persist indefinitely, add the **Scope** parameter to your command, and set its value to **Global** .</span></span> <span data-ttu-id="cddb3-124">有关点到的详细信息，请参阅 [about_Scripts](../Microsoft.PowerShell.Core/About/about_Scripts.md#script-scope-and-dot-sourcing)。</span><span class="sxs-lookup"><span data-stu-id="cddb3-124">For more information about dot-sourcing, see [about_Scripts](../Microsoft.PowerShell.Core/About/about_Scripts.md#script-scope-and-dot-sourcing).</span></span>
- <span data-ttu-id="cddb3-125">外部驱动器。</span><span class="sxs-lookup"><span data-stu-id="cddb3-125">External drives.</span></span> <span data-ttu-id="cddb3-126">当外部驱动器连接到计算机时，PowerShell 会自动将 **new-psdrive** 添加到代表新驱动器的文件系统中。</span><span class="sxs-lookup"><span data-stu-id="cddb3-126">When an external drive is connected to the computer, PowerShell automatically adds a **PSDrive** to the file system that represents the new drive.</span></span> <span data-ttu-id="cddb3-127">无需重新启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="cddb3-127">You don't have to restart PowerShell.</span></span> <span data-ttu-id="cddb3-128">同样，当外部驱动器与计算机断开连接时，PowerShell 会自动删除表示已删除驱动器的 **new-psdrive** 。</span><span class="sxs-lookup"><span data-stu-id="cddb3-128">Similarly, when an external drive is disconnected from the computer, PowerShell automatically deletes the **PSDrive** that represents the removed drive.</span></span>
- <span data-ttu-id="cddb3-129">通用命名约定 (UNC) 路径的凭据。</span><span class="sxs-lookup"><span data-stu-id="cddb3-129">Credentials for Universal Naming Convention (UNC) paths.</span></span>

<span data-ttu-id="cddb3-130">当 **根** 参数的值为 UNC 路径（例如）时，将 `\\Server\Share` 使用 **credential** 参数的值中指定的凭据创建 **new-psdrive** 。</span><span class="sxs-lookup"><span data-stu-id="cddb3-130">When the value of the **Root** parameter is a UNC path, such as `\\Server\Share`, the credential specified in the value of the **Credential** parameter is used to create the **PSDrive** .</span></span> <span data-ttu-id="cddb3-131">否则，在创建新的文件系统驱动器时， **凭据** 不起作用。</span><span class="sxs-lookup"><span data-stu-id="cddb3-131">Otherwise, **Credential** isn't effective when you're creating new file system drives.</span></span>

<span data-ttu-id="cddb3-132">一些代码示例使用展开来减小行长度，提高可读性。</span><span class="sxs-lookup"><span data-stu-id="cddb3-132">Some code samples use splatting to reduce the line length and improve readability.</span></span> <span data-ttu-id="cddb3-133">有关详细信息，请参阅 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)。</span><span class="sxs-lookup"><span data-stu-id="cddb3-133">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

## <span data-ttu-id="cddb3-134">示例</span><span class="sxs-lookup"><span data-stu-id="cddb3-134">EXAMPLES</span></span>

### <span data-ttu-id="cddb3-135">示例1：创建映射到网络共享的临时驱动器</span><span class="sxs-lookup"><span data-stu-id="cddb3-135">Example 1: Create a temporary drive mapped to a network share</span></span>

<span data-ttu-id="cddb3-136">此示例将创建一个映射到网络共享的临时 PowerShell 驱动器。</span><span class="sxs-lookup"><span data-stu-id="cddb3-136">This example creates a temporary PowerShell drive that's mapped to a network share.</span></span>

```powershell
New-PSDrive -Name "Public" -PSProvider "FileSystem" -Root "\\Server01\Public"
```

```Output
Name       Provider      Root
----       --------      ----
Public     FileSystem    \\Server01\Public
```

<span data-ttu-id="cddb3-137">`New-PSDrive` 使用 **Name** 参数指定名为的 powershell 驱动器 `Public` ，并使用 **PSProvider** 参数来指定 powershell `FileSystem` 提供程序。</span><span class="sxs-lookup"><span data-stu-id="cddb3-137">`New-PSDrive` uses the **Name** parameter to specify PowerShell drive named `Public` and the **PSProvider** parameter to specify the PowerShell `FileSystem` provider.</span></span> <span data-ttu-id="cddb3-138">**Root** 参数指定网络共享的 UNC 路径。</span><span class="sxs-lookup"><span data-stu-id="cddb3-138">The **Root** parameter specifies the network share's UNC path.</span></span>

<span data-ttu-id="cddb3-139">查看 PowerShell 会话的内容： `Get-ChildItem -Path Public:`</span><span class="sxs-lookup"><span data-stu-id="cddb3-139">To view the contents from a PowerShell session: `Get-ChildItem -Path Public:`</span></span>

### <span data-ttu-id="cddb3-140">示例2：创建映射到本地目录的临时驱动器</span><span class="sxs-lookup"><span data-stu-id="cddb3-140">Example 2: Create a temporary drive mapped to a local directory</span></span>

<span data-ttu-id="cddb3-141">此示例将创建一个临时 PowerShell 驱动器，用于访问本地计算机上的某个目录。</span><span class="sxs-lookup"><span data-stu-id="cddb3-141">This example creates a temporary PowerShell drive that provides access to a directory on the local computer.</span></span>

```powershell
$parameters = @{
    Name = "MyDocs"
    PSProvider = "FileSystem"
    Root = "C:\Users\User01\Documents"
    Description = "Maps to my My Documents folder."
}
New-PSDrive @parameters
```

```Output
Name        Provider      Root
----        --------      ----
MyDocs      FileSystem    C:\Users\User01\Documents
```

<span data-ttu-id="cddb3-142">展开创建参数键和值。</span><span class="sxs-lookup"><span data-stu-id="cddb3-142">Splatting creates the parameter keys and values.</span></span> <span data-ttu-id="cddb3-143">**Name** 参数指定驱动器名称， **MyDocs** 。</span><span class="sxs-lookup"><span data-stu-id="cddb3-143">The **Name** parameter specifies the drive name, **MyDocs** .</span></span> <span data-ttu-id="cddb3-144">**PSProvider** 参数指定 PowerShell `FileSystem` 提供程序。</span><span class="sxs-lookup"><span data-stu-id="cddb3-144">The **PSProvider** parameter specifies the PowerShell `FileSystem` provider.</span></span> <span data-ttu-id="cddb3-145">**Root** 指定本地计算机的目录。</span><span class="sxs-lookup"><span data-stu-id="cddb3-145">**Root** specifies the local computer's directory.</span></span> <span data-ttu-id="cddb3-146">**Description** 参数描述驱动器的用途。</span><span class="sxs-lookup"><span data-stu-id="cddb3-146">The **Description** parameter describes the drive's purpose.</span></span> <span data-ttu-id="cddb3-147">`New-PSDrive` 使用 splatted 参数创建 `MyDocs` 驱动器。</span><span class="sxs-lookup"><span data-stu-id="cddb3-147">`New-PSDrive` uses the splatted parameters to create the `MyDocs` drive.</span></span>

<span data-ttu-id="cddb3-148">查看 PowerShell 会话的内容： `Get-ChildItem -Path MyDocs:`</span><span class="sxs-lookup"><span data-stu-id="cddb3-148">To view the contents from a PowerShell session: `Get-ChildItem -Path MyDocs:`</span></span>

### <span data-ttu-id="cddb3-149">示例3：创建用于注册表项的临时驱动器</span><span class="sxs-lookup"><span data-stu-id="cddb3-149">Example 3: Create a temporary drive for a registry key</span></span>

<span data-ttu-id="cddb3-150">此示例创建一个提供对注册表项的访问的临时 PowerShell 驱动器。</span><span class="sxs-lookup"><span data-stu-id="cddb3-150">This example creates a temporary PowerShell drive that provides access to a registry key.</span></span> <span data-ttu-id="cddb3-151">它会创建一个名为 MyCompany 的驱动器，该驱动器映射到 `HKLM:\Software\MyCompany` 注册表项。</span><span class="sxs-lookup"><span data-stu-id="cddb3-151">It creates a drive named MyCompany that is mapped to the `HKLM:\Software\MyCompany` registry key.</span></span>

```powershell
New-PSDrive -Name "MyCompany" -PSProvider "Registry" -Root "HKLM:\Software\MyCompany"
```

```Output
Name           Provider      Root
----           --------      ----
MyCompany      Registry      HKLM:\Software\MyCompany
```

<span data-ttu-id="cddb3-152">`New-PSDrive` 使用 **Name** 参数指定名为的 powershell 驱动器 `MyCompany` ，并使用 **PSProvider** 参数来指定 powershell `Registry` 提供程序。</span><span class="sxs-lookup"><span data-stu-id="cddb3-152">`New-PSDrive` uses the **Name** parameter to specify PowerShell drive named `MyCompany` and the **PSProvider** parameter to specify the PowerShell `Registry` provider.</span></span> <span data-ttu-id="cddb3-153">**Root** 参数指定注册表位置。</span><span class="sxs-lookup"><span data-stu-id="cddb3-153">The **Root** parameter specifies the registry location.</span></span>

<span data-ttu-id="cddb3-154">查看 PowerShell 会话的内容： `Get-ChildItem -Path MyCompany:`</span><span class="sxs-lookup"><span data-stu-id="cddb3-154">To view the contents from a PowerShell session: `Get-ChildItem -Path MyCompany:`</span></span>

### <span data-ttu-id="cddb3-155">示例4：使用凭据创建永久映射网络驱动器</span><span class="sxs-lookup"><span data-stu-id="cddb3-155">Example 4: Create a persistent mapped network drive using credentials</span></span>

<span data-ttu-id="cddb3-156">此示例将使用域服务帐户凭据进行身份验证的网络驱动器进行映射。</span><span class="sxs-lookup"><span data-stu-id="cddb3-156">This example maps a network drive that's authenticated with a domain service account's credentials.</span></span>
<span data-ttu-id="cddb3-157">有关存储凭据的 **PSCredential** 对象以及如何将密码存储为 **SecureString** 的详细信息，请参阅 **Credential** 参数的描述。</span><span class="sxs-lookup"><span data-stu-id="cddb3-157">For more information about the **PSCredential** object that stores credentials and how passwords are stored as a **SecureString** , see the **Credential** parameter's description.</span></span>

```powershell
$cred = Get-Credential -Credential Contoso\ServiceAccount
New-PSDrive -Name "S" -Root "\\Server01\Scripts" -Persist -PSProvider "FileSystem" -Credential $cred
Net Use
```

```Output
Status       Local     Remote                    Network
---------------------------------------------------------
OK           S:        \\Server01\Scripts        Microsoft Windows Network
```

> [!NOTE]
> <span data-ttu-id="cddb3-158">请记住，如果在脚本中使用上述代码片段，请将 **作用域** 参数值设置为 "Global"，以确保驱动器在当前作用域外保持不变。</span><span class="sxs-lookup"><span data-stu-id="cddb3-158">Remember, if you use the above snippet in a script, set the **Scope** parameter value to "Global" to ensure the drive persists outside the current scope.</span></span>

<span data-ttu-id="cddb3-159">`$cred`变量存储包含服务帐户凭据的 **PSCredential** 对象。</span><span class="sxs-lookup"><span data-stu-id="cddb3-159">The `$cred` variable stores a **PSCredential** object that contains the service account's credentials.</span></span> <span data-ttu-id="cddb3-160">`Get-Credential` 提示输入存储在 **SecureString** 中的密码。</span><span class="sxs-lookup"><span data-stu-id="cddb3-160">`Get-Credential` prompts you to enter the password that's stored in a **SecureString** .</span></span>

<span data-ttu-id="cddb3-161">`New-PSDrive` 使用几个参数创建映射网络驱动器。</span><span class="sxs-lookup"><span data-stu-id="cddb3-161">`New-PSDrive` creates the mapped network drive by using several parameters.</span></span> <span data-ttu-id="cddb3-162">**名称** 指定 `S` Windows 接受的驱动器号。</span><span class="sxs-lookup"><span data-stu-id="cddb3-162">**Name** specifies the `S` drive letter that Windows accepts.</span></span> <span data-ttu-id="cddb3-163">和 **Root** 定义 `\\Server01\Scripts` 为远程计算机上的位置。</span><span class="sxs-lookup"><span data-stu-id="cddb3-163">and **Root** defines `\\Server01\Scripts` as the location on a remote computer.</span></span> <span data-ttu-id="cddb3-164">**持久性** 将创建保存在本地计算机上的 Windows 映射网络驱动器。</span><span class="sxs-lookup"><span data-stu-id="cddb3-164">**Persist** creates a Windows mapped network drive that's saved on the local computer.</span></span> <span data-ttu-id="cddb3-165">**PSProvider** 指定 `FileSystem` 提供程序。</span><span class="sxs-lookup"><span data-stu-id="cddb3-165">**PSProvider** specifies the `FileSystem` provider.</span></span> <span data-ttu-id="cddb3-166">**Credential** 使用该 `$cred` 变量获取用于身份验证的服务帐户凭据。</span><span class="sxs-lookup"><span data-stu-id="cddb3-166">**Credential** uses the `$cred` variable to get the service account credentials for authentication.</span></span>

<span data-ttu-id="cddb3-167">可以在本地计算机上的 PowerShell 会话、文件资源管理器和 **网络使用** 等工具中查看映射的驱动器。</span><span class="sxs-lookup"><span data-stu-id="cddb3-167">The mapped drive can be viewed on the local computer in PowerShell sessions, File Explorer, and with tools such as **net use** .</span></span> <span data-ttu-id="cddb3-168">查看 PowerShell 会话的内容： `Get-ChildItem -Path S:`</span><span class="sxs-lookup"><span data-stu-id="cddb3-168">To view the contents from a PowerShell session: `Get-ChildItem -Path S:`</span></span>

### <span data-ttu-id="cddb3-169">示例5：创建持久和临时驱动器</span><span class="sxs-lookup"><span data-stu-id="cddb3-169">Example 5: Create persistent and temporary drives</span></span>

<span data-ttu-id="cddb3-170">此示例显示了永久映射网络驱动器与映射到同一网络共享的临时 PowerShell 驱动器之间的差异。</span><span class="sxs-lookup"><span data-stu-id="cddb3-170">This example shows the difference between a persistent mapped network drive and a temporary PowerShell drive that is mapped to the same network share.</span></span>

<span data-ttu-id="cddb3-171">如果关闭 PowerShell 会话并打开一个新的会话，则该临时 `PSDrive:` 磁盘不可用，但永久 `X:` 驱动器可用。</span><span class="sxs-lookup"><span data-stu-id="cddb3-171">If you close the PowerShell session and then open a new session, the temporary `PSDrive:` isn't available, but the persistent `X:` drive is available.</span></span> <span data-ttu-id="cddb3-172">确定使用哪种方法来映射网络驱动器时，请考虑使用驱动器的方式。</span><span class="sxs-lookup"><span data-stu-id="cddb3-172">When deciding which method to use to map network drives, consider how you'll use the drive.</span></span> <span data-ttu-id="cddb3-173">例如，它是否必须是永久性的，以及驱动器是否对其他 Windows 功能可见。</span><span class="sxs-lookup"><span data-stu-id="cddb3-173">For example, whether it has to be persistent, and whether the drive has to be visible to other Windows features.</span></span>

```powershell
# Create a temporary PowerShell drive called PSDrive:
# that's mapped to the \\Server01\Public network share.
New-PSDrive -Name "PSDrive" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Use the Persist parameter of New-PSDrive to create the X: mapped network drive,
# which is also mapped to the \\Server01\Public network share.
New-PSDrive -Persist -Name "X" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Now, you can use the Get-PSDrive drive cmdlet to examine the two drives.
# The drives appear to be the same, although the network share name appears only
# in the root of the PSDrive: drive.
Get-PSDrive -Name "PSDrive", "X"
```

```Output
Name       Provider      Root
----       --------      ----

PsDrive    FileSystem    \\Server01\public
X          FileSystem    X:\
```

```powershell
# Get-Member cmdlet shows that the drives have the same object type,
# System.Management.Automation.PSDriveInfo.
Get-PSDrive "PSDrive", "x" | Get-Member
```

```Output
TypeName: System.Management.Automation.PSDriveInfo

Name                MemberType   Definition
----                ----------   ----------
CompareTo           Method       System.Int32 CompareTo(PSDriveInfo drive),
Equals              Method       System.Boolean Equals(Object obj),
GetHashCode         Method       System.Int32 GetHashCode()
...
```

```powershell
# Net Use and Get-CimInstance for the Win32_LogicalDisk class,
# and Win32_NetworkConnection class find only the persistent X: drive.
# PowerShell temporary drives are known only to PowerShell.
Net Use
Get-CimInstance Win32_LogicalDisk | Format-Table -Property DeviceID
Get-CimInstance Win32_NetworkConnection
```

```Output
Status       Local     Remote                    Network
--------------------------------------------------------
OK           X:        \\contoso-pc\data         Microsoft Windows Network

deviceid
--------
C:
D:
X:

LocalName    RemoteName              ConnectionState          Status
---------    ----------              ---------------          ------
X:           \\products\public       Disconnected             Unavailable
```

## <span data-ttu-id="cddb3-174">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cddb3-174">PARAMETERS</span></span>

### <span data-ttu-id="cddb3-175">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cddb3-175">-Confirm</span></span>

<span data-ttu-id="cddb3-176">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="cddb3-176">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cddb3-177">-Credential</span><span class="sxs-lookup"><span data-stu-id="cddb3-177">-Credential</span></span>

<span data-ttu-id="cddb3-178">指定有权执行此操作的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="cddb3-178">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="cddb3-179">默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="cddb3-179">The default is the current user.</span></span>

<span data-ttu-id="cddb3-180">由于 PowerShell 3.0，当 **Root** 参数的值为 UNC 路径时，你可以使用凭据来创建文件系统驱动器。</span><span class="sxs-lookup"><span data-stu-id="cddb3-180">Since PowerShell 3.0, when the value of the **Root** parameter is a UNC path, you can use credentials to create file system drives.</span></span>

<span data-ttu-id="cddb3-181">键入用户名（如 **User01** 或 **Domain01\User01** ），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="cddb3-181">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="cddb3-182">如果键入用户名，系统会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="cddb3-182">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="cddb3-183">凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="cddb3-183">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="cddb3-184">有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="cddb3-184">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cddb3-185">-Description</span><span class="sxs-lookup"><span data-stu-id="cddb3-185">-Description</span></span>

<span data-ttu-id="cddb3-186">指定驱动器的简短文本说明。</span><span class="sxs-lookup"><span data-stu-id="cddb3-186">Specifies a brief text description of the drive.</span></span> <span data-ttu-id="cddb3-187">键入任意字符串。</span><span class="sxs-lookup"><span data-stu-id="cddb3-187">Type any string.</span></span>

<span data-ttu-id="cddb3-188">若要查看所有会话驱动器的说明，请参阅 `Get-PSDrive | Format-Table Name, Description` 。</span><span class="sxs-lookup"><span data-stu-id="cddb3-188">To see the descriptions of all the session's drives, `Get-PSDrive | Format-Table Name, Description`.</span></span>

<span data-ttu-id="cddb3-189">若要查看特定驱动器的说明，请键入 `(Get-PSDrive <DriveName>).Description` 。</span><span class="sxs-lookup"><span data-stu-id="cddb3-189">To see the description of a particular drive, type `(Get-PSDrive <DriveName>).Description`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cddb3-190">-Name</span><span class="sxs-lookup"><span data-stu-id="cddb3-190">-Name</span></span>

<span data-ttu-id="cddb3-191">指定新驱动器的名称。</span><span class="sxs-lookup"><span data-stu-id="cddb3-191">Specifies a name for the new drive.</span></span> <span data-ttu-id="cddb3-192">对于永久映射网络驱动器，请使用驱动器号。</span><span class="sxs-lookup"><span data-stu-id="cddb3-192">For persistent mapped network drives, use a drive letter.</span></span> <span data-ttu-id="cddb3-193">对于临时 PowerShell 驱动器，你并不限于驱动器号，请使用任何有效的字符串。</span><span class="sxs-lookup"><span data-stu-id="cddb3-193">For temporary PowerShell drives, you aren't limited to drive letters, use any valid string.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cddb3-194">-持久性</span><span class="sxs-lookup"><span data-stu-id="cddb3-194">-Persist</span></span>

<span data-ttu-id="cddb3-195">指示此 cmdlet 创建 Windows 映射网络驱动器。</span><span class="sxs-lookup"><span data-stu-id="cddb3-195">Indicates that this cmdlet creates a Windows mapped network drive.</span></span> <span data-ttu-id="cddb3-196">**持久性** 参数仅在 Windows 上可用。</span><span class="sxs-lookup"><span data-stu-id="cddb3-196">The **Persist** parameter is only available on Windows.</span></span>

<span data-ttu-id="cddb3-197">映射网络驱动器保存于本地计算机的 Windows 中。</span><span class="sxs-lookup"><span data-stu-id="cddb3-197">Mapped network drives are saved in Windows on the local computer.</span></span> <span data-ttu-id="cddb3-198">它们是持久性的，而不是特定于会话的，可以在文件资源管理器和其他工具中进行查看和管理。</span><span class="sxs-lookup"><span data-stu-id="cddb3-198">They're persistent, not session-specific, and can be viewed and managed in File Explorer and other tools.</span></span>

<span data-ttu-id="cddb3-199">在本地对命令进行作用域时，如果没有点到 **，则不会在运行** 命令的范围之外保存 **new-psdrive** 的创建。</span><span class="sxs-lookup"><span data-stu-id="cddb3-199">When you scope the command locally, without dot-sourcing, the **Persist** parameter doesn't persist the creation of a **PSDrive** beyond the scope in which you run the command.</span></span> <span data-ttu-id="cddb3-200">如果在 `New-PSDrive` 脚本中运行，并且希望新驱动器无限期地保留，则必须将脚本置于点端。</span><span class="sxs-lookup"><span data-stu-id="cddb3-200">If you run `New-PSDrive` inside a script, and you want the new drive to persist indefinitely, you must dot-source the script.</span></span> <span data-ttu-id="cddb3-201">为了获得最佳结果，若要强制新驱动器保留，请将 **Global** 指定为 **Scope** 参数的值，并在命令中包含 " **永久保存** "。</span><span class="sxs-lookup"><span data-stu-id="cddb3-201">For best results, to force a new drive to persist, specify **Global** as the value of the **Scope** parameter and include **Persist** in your command.</span></span>

<span data-ttu-id="cddb3-202">驱动器名称必须是字母，如 `D` 或 `E` 。</span><span class="sxs-lookup"><span data-stu-id="cddb3-202">The name of the drive must be a letter, such as `D` or `E`.</span></span> <span data-ttu-id="cddb3-203">**Root** 参数的值必须是另一台计算机的 UNC 路径。</span><span class="sxs-lookup"><span data-stu-id="cddb3-203">The value of **Root** parameter must be a UNC path of a different computer.</span></span> <span data-ttu-id="cddb3-204">**PSProvider** 参数的值必须是 `FileSystem` 。</span><span class="sxs-lookup"><span data-stu-id="cddb3-204">The **PSProvider** parameter's value must be `FileSystem`.</span></span>

<span data-ttu-id="cddb3-205">若要断开 Windows 映射网络驱动器，请使用 `Remove-PSDrive` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cddb3-205">To disconnect a Windows mapped network drive, use the `Remove-PSDrive` cmdlet.</span></span> <span data-ttu-id="cddb3-206">在断开 Windows 映射网络驱动器时，将从计算机中永久删除该映射，而不仅是从当前会话中删除。</span><span class="sxs-lookup"><span data-stu-id="cddb3-206">When you disconnect a Windows mapped network drive, the mapping is permanently deleted from the computer, not just deleted from the current session.</span></span>

<span data-ttu-id="cddb3-207">映射网络驱动器特定于用户帐户。</span><span class="sxs-lookup"><span data-stu-id="cddb3-207">Mapped network drives are specific to a user account.</span></span> <span data-ttu-id="cddb3-208">使用其他用户的凭据启动的会话中不显示使用其他用户的凭据在提升的会话或会话中创建的映射驱动器。</span><span class="sxs-lookup"><span data-stu-id="cddb3-208">Mapped drives created in elevated sessions or sessions using the credential of another user aren't visible in sessions started using different credentials.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cddb3-209">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="cddb3-209">-PSProvider</span></span>

<span data-ttu-id="cddb3-210">指定支持此类型的驱动器的 PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="cddb3-210">Specifies the PowerShell provider that supports drives of this kind.</span></span>

<span data-ttu-id="cddb3-211">例如，如果驱动器与网络共享或文件系统目录相关联，则 PowerShell 提供程序为 `FileSystem` 。</span><span class="sxs-lookup"><span data-stu-id="cddb3-211">For example, if the drive is associated with a network share or file system directory, the PowerShell provider is `FileSystem`.</span></span> <span data-ttu-id="cddb3-212">如果驱动器与注册表项关联，则提供程序为 `Registry` 。</span><span class="sxs-lookup"><span data-stu-id="cddb3-212">If the drive is associated with a registry key, the provider is `Registry`.</span></span>

<span data-ttu-id="cddb3-213">临时 PowerShell 驱动器可以与任何 PowerShell 提供程序相关联。</span><span class="sxs-lookup"><span data-stu-id="cddb3-213">Temporary PowerShell drives can be associated with any PowerShell provider.</span></span> <span data-ttu-id="cddb3-214">映射的网络驱动器只能与 `FileSystem` 提供程序相关联。</span><span class="sxs-lookup"><span data-stu-id="cddb3-214">Mapped network drives can be associated only with the `FileSystem` provider.</span></span>

<span data-ttu-id="cddb3-215">若要查看 PowerShell 会话中提供程序的列表，请使用 `Get-PSProvider` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cddb3-215">To see a list of the providers in your PowerShell session, use the `Get-PSProvider` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cddb3-216">-根</span><span class="sxs-lookup"><span data-stu-id="cddb3-216">-Root</span></span>

<span data-ttu-id="cddb3-217">指定 PowerShell 驱动器映射到的数据存储位置。</span><span class="sxs-lookup"><span data-stu-id="cddb3-217">Specifies the data store location to which a PowerShell drive is mapped.</span></span>

<span data-ttu-id="cddb3-218">例如，指定一个网络共享，例如 `\\Server01\Public` 本地目录（如 `C:\Program Files` ）或注册表项（如） `HKLM:\Software\Microsoft` 。</span><span class="sxs-lookup"><span data-stu-id="cddb3-218">For example, specify a network share, such as `\\Server01\Public`, a local directory, such as `C:\Program Files`, or a registry key, such as `HKLM:\Software\Microsoft`.</span></span>

<span data-ttu-id="cddb3-219">临时 PowerShell 驱动器可以与任何受支持的提供程序驱动器上的本地或远程位置关联。</span><span class="sxs-lookup"><span data-stu-id="cddb3-219">Temporary PowerShell drives can be associated with a local or remote location on any supported provider drive.</span></span> <span data-ttu-id="cddb3-220">映射网络驱动器只能与远程计算机上的文件系统位置关联。</span><span class="sxs-lookup"><span data-stu-id="cddb3-220">Mapped network drives can be associated only with a file system location on a remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cddb3-221">-Scope</span><span class="sxs-lookup"><span data-stu-id="cddb3-221">-Scope</span></span>

<span data-ttu-id="cddb3-222">指定驱动器的作用域。</span><span class="sxs-lookup"><span data-stu-id="cddb3-222">Specifies a scope for the drive.</span></span> <span data-ttu-id="cddb3-223">此参数的可接受值为： **Global** 、 **Local** 、 **Script** 或相对于当前作用域的数字。</span><span class="sxs-lookup"><span data-stu-id="cddb3-223">The acceptable values for this parameter are: **Global** , **Local** , and **Script** , or a number relative to the current scope.</span></span> <span data-ttu-id="cddb3-224">范围号0到范围数。</span><span class="sxs-lookup"><span data-stu-id="cddb3-224">Scopes number 0 through the number of scopes.</span></span> <span data-ttu-id="cddb3-225">当前作用域编号为0，其父级为1。</span><span class="sxs-lookup"><span data-stu-id="cddb3-225">The current scope number is 0 and its parent is 1.</span></span> <span data-ttu-id="cddb3-226">有关详细信息，请参阅 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="cddb3-226">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cddb3-227">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cddb3-227">-WhatIf</span></span>

<span data-ttu-id="cddb3-228">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="cddb3-228">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="cddb3-229">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="cddb3-229">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cddb3-230">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cddb3-230">CommonParameters</span></span>

<span data-ttu-id="cddb3-231">此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="cddb3-231">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="cddb3-232">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="cddb3-232">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cddb3-233">输入</span><span class="sxs-lookup"><span data-stu-id="cddb3-233">INPUTS</span></span>

### <span data-ttu-id="cddb3-234">无</span><span class="sxs-lookup"><span data-stu-id="cddb3-234">None</span></span>

<span data-ttu-id="cddb3-235">不能通过管道将输入用于此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cddb3-235">You can't pipeline input to this cmdlet.</span></span>

## <span data-ttu-id="cddb3-236">输出</span><span class="sxs-lookup"><span data-stu-id="cddb3-236">OUTPUTS</span></span>

### <span data-ttu-id="cddb3-237">System.Management.Automation.PSDriveInfo</span><span class="sxs-lookup"><span data-stu-id="cddb3-237">System.Management.Automation.PSDriveInfo</span></span>

## <span data-ttu-id="cddb3-238">注释</span><span class="sxs-lookup"><span data-stu-id="cddb3-238">NOTES</span></span>

<span data-ttu-id="cddb3-239">`New-PSDrive` 设计用于处理由任何提供程序公开的数据。</span><span class="sxs-lookup"><span data-stu-id="cddb3-239">`New-PSDrive` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="cddb3-240">若要列出会话中可用的提供程序，请使用 `Get-PSProvider` 。</span><span class="sxs-lookup"><span data-stu-id="cddb3-240">To list the providers available in your session, use `Get-PSProvider`.</span></span> <span data-ttu-id="cddb3-241">有关提供程序的详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="cddb3-241">For more information about providers, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="cddb3-242">映射网络驱动器特定于用户帐户。</span><span class="sxs-lookup"><span data-stu-id="cddb3-242">Mapped network drives are specific to a user account.</span></span> <span data-ttu-id="cddb3-243">使用其他用户的凭据启动的会话中不显示使用其他用户的凭据在提升的会话或会话中创建的映射驱动器。</span><span class="sxs-lookup"><span data-stu-id="cddb3-243">Mapped drives created in elevated sessions or sessions using the credential of another user aren't visible in sessions started using different credentials.</span></span>

## <span data-ttu-id="cddb3-244">相关链接</span><span class="sxs-lookup"><span data-stu-id="cddb3-244">RELATED LINKS</span></span>

[<span data-ttu-id="cddb3-245">about_Providers</span><span class="sxs-lookup"><span data-stu-id="cddb3-245">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="cddb3-246">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="cddb3-246">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="cddb3-247">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="cddb3-247">Get-PSDrive</span></span>](Get-PSDrive.md)

[<span data-ttu-id="cddb3-248">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="cddb3-248">Remove-PSDrive</span></span>](Remove-PSDrive.md)
