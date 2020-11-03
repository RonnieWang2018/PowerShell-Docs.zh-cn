---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psdrive?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSDrive
ms.openlocfilehash: d404f0fdc82e3730f1f6a04d7f39d5988a3de7d6
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2020
ms.locfileid: "93196979"
---
# <span data-ttu-id="4215c-103">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="4215c-103">Get-PSDrive</span></span>

## <span data-ttu-id="4215c-104">摘要</span><span class="sxs-lookup"><span data-stu-id="4215c-104">SYNOPSIS</span></span>
<span data-ttu-id="4215c-105">获取当前会话中的驱动器。</span><span class="sxs-lookup"><span data-stu-id="4215c-105">Gets drives in the current session.</span></span>

## <span data-ttu-id="4215c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4215c-106">SYNTAX</span></span>

### <span data-ttu-id="4215c-107">Name（默认值）</span><span class="sxs-lookup"><span data-stu-id="4215c-107">Name (Default)</span></span>

```
Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="4215c-108">LiteralName</span><span class="sxs-lookup"><span data-stu-id="4215c-108">LiteralName</span></span>

```
Get-PSDrive [-LiteralName] <String[]> [-Scope <String>] [-PSProvider <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="4215c-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4215c-109">DESCRIPTION</span></span>

<span data-ttu-id="4215c-110">`Get-PSDrive`Cmdlet 将获取当前会话中的驱动器。</span><span class="sxs-lookup"><span data-stu-id="4215c-110">The `Get-PSDrive` cmdlet gets the drives in the current session.</span></span> <span data-ttu-id="4215c-111">可以获取会话中的特定驱动器或所有驱动器。</span><span class="sxs-lookup"><span data-stu-id="4215c-111">You can get a particular drive or all drives in the session.</span></span>

<span data-ttu-id="4215c-112">此 cmdlet 将获取以下类型的驱动器：</span><span class="sxs-lookup"><span data-stu-id="4215c-112">This cmdlet gets the following types of drives:</span></span>

- <span data-ttu-id="4215c-113">计算机上的 Windows 逻辑驱动器，包括映射到网络共享的驱动器。</span><span class="sxs-lookup"><span data-stu-id="4215c-113">Windows logical drives on the computer, including drives mapped to network shares.</span></span>
- <span data-ttu-id="4215c-114">PowerShell 提供程序公开的驱动器 (如证书：、Function：和 Alias：驱动器) 以及由 Windows PowerShell Registry 提供程序公开的 HKLM：和 HKCU：驱动器。</span><span class="sxs-lookup"><span data-stu-id="4215c-114">Drives exposed by PowerShell providers (such as the Certificate:, Function:, and Alias: drives) and the HKLM: and HKCU: drives that are exposed by the Windows PowerShell Registry provider.</span></span>
- <span data-ttu-id="4215c-115">通过使用 cmdlet 创建的会话指定的临时驱动器和永久的映射网络驱动器。</span><span class="sxs-lookup"><span data-stu-id="4215c-115">Session-specified temporary drives and persistent mapped network drives that you create by using the New-PSDrive cmdlet.</span></span>

<span data-ttu-id="4215c-116">从 Windows PowerShell 3.0 开始，cmdlet 的 **持久** 参数 `New-PSDrive` 可以创建在本地计算机上保存并可用于其他会话的映射网络驱动器。</span><span class="sxs-lookup"><span data-stu-id="4215c-116">Beginning in Windows PowerShell 3.0, the **Persist** parameter of the `New-PSDrive` cmdlet can create mapped network drives that are saved on the local computer and are available in other sessions.</span></span> <span data-ttu-id="4215c-117">有关详细信息，请参阅 New-PSDrive。</span><span class="sxs-lookup"><span data-stu-id="4215c-117">For more information, see New-PSDrive.</span></span>

<span data-ttu-id="4215c-118">此外，从 Windows PowerShell 3.0 开始，当外部驱动器连接到计算机时，Windows PowerShell 自动将 PSDrive 添加到代表新驱动器的文件系统中。</span><span class="sxs-lookup"><span data-stu-id="4215c-118">Also, beginning in Windows PowerShell 3.0, when an external drive is connected to the computer, Windows PowerShell automatically adds a PSDrive to the file system that represents the new drive.</span></span>
<span data-ttu-id="4215c-119">你无需重启 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="4215c-119">You do not need to restart Windows PowerShell.</span></span> <span data-ttu-id="4215c-120">简单来说，当从计算机断开连接外部驱动器时，Windows PowerShell 会自动删除代表删除的驱动器的 PSDrive。</span><span class="sxs-lookup"><span data-stu-id="4215c-120">Similarly, when an external drive is disconnected from the computer, Windows PowerShell automatically deletes the PSDrive that represents the removed drive.</span></span>

## <span data-ttu-id="4215c-121">示例</span><span class="sxs-lookup"><span data-stu-id="4215c-121">EXAMPLES</span></span>

### <span data-ttu-id="4215c-122">示例1：获取当前会话中的驱动器</span><span class="sxs-lookup"><span data-stu-id="4215c-122">Example 1: Get drives in the current session</span></span>

```
PS C:\> Get-PSDrive

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
Alias                                  Alias
C                 202.06      23718.91 FileSystem    C:\
Cert                                   Certificate   \
D                1211.06     123642.32 FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
```

<span data-ttu-id="4215c-123">此命令获取当前会话中的驱动器。</span><span class="sxs-lookup"><span data-stu-id="4215c-123">This command gets the drives in the current session.</span></span>

<span data-ttu-id="4215c-124">输出显示硬盘驱动器 (C： ) 、CD-ROM 驱动器 (D： ) ，以及由 Windows PowerShell 提供程序公开的驱动器 (Alias：、Cert：、Env：、Function：、HKCU：、HKLM：和 Variable： ) 。</span><span class="sxs-lookup"><span data-stu-id="4215c-124">The output shows the hard drive (C:), CD-ROM drive (D:), and the drives exposed by the Windows PowerShell providers (Alias:, Cert:, Env:, Function:, HKCU:, HKLM:, and Variable:).</span></span>

### <span data-ttu-id="4215c-125">示例2：获取计算机上的驱动器</span><span class="sxs-lookup"><span data-stu-id="4215c-125">Example 2: Get a drive on the computer</span></span>

```
PS C:\foo> Get-PSDrive D

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
D                1211.06     123642.32 FileSystem    D:\
```

<span data-ttu-id="4215c-126">此命令获取计算机上的 D: 驱动器。</span><span class="sxs-lookup"><span data-stu-id="4215c-126">This command gets the D: drive on the computer.</span></span> <span data-ttu-id="4215c-127">请注意，该命令中的驱动器号后面不带冒号。</span><span class="sxs-lookup"><span data-stu-id="4215c-127">Note that the drive letter in the command is not followed by a colon.</span></span>

### <span data-ttu-id="4215c-128">示例3：获取 Windows PowerShell 文件系统提供程序支持的所有驱动器</span><span class="sxs-lookup"><span data-stu-id="4215c-128">Example 3: Get all the drives that are supported by the Windows PowerShell file system provider</span></span>

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
```

<span data-ttu-id="4215c-129">此命令获取 Windows PowerShell FileSystem 提供程序支持的所有驱动器。</span><span class="sxs-lookup"><span data-stu-id="4215c-129">This command gets all of the drives that are supported by the Windows PowerShell FileSystem provider.</span></span> <span data-ttu-id="4215c-130">这包括固定驱动器、逻辑分区、映射网络驱动器和使用 New-PSDrive cmdlet 创建的临时驱动器。</span><span class="sxs-lookup"><span data-stu-id="4215c-130">This includes fixed drives, logical partitions, mapped network drives, and temporary drives that you create by using the New-PSDrive cmdlet.</span></span>

### <span data-ttu-id="4215c-131">示例4：检查驱动器是否正在用作 Windows PowerShell 驱动器名称</span><span class="sxs-lookup"><span data-stu-id="4215c-131">Example 4: Check to see if a drive is in use as a Windows PowerShell drive name</span></span>

```powershell
if (Get-PSDrive X -ErrorAction SilentlyContinue) {
    Write-Host 'The X: drive is already in use.'
} else {
    New-PSDrive -Name X -PSProvider Registry -Root HKLM:\SOFTWARE
}
```

<span data-ttu-id="4215c-132">此命令检查 X 驱动器是否已作为 Windows PowerShell 驱动器名称使用。</span><span class="sxs-lookup"><span data-stu-id="4215c-132">This command checks to see whether the X drive is already in use as a Windows PowerShell drive name.</span></span>
<span data-ttu-id="4215c-133">如果不是，则该命令使用 `New-PSDrive` cmdlet 创建一个映射到 HKLM： \ SOFTWARE 注册表项的临时驱动器。</span><span class="sxs-lookup"><span data-stu-id="4215c-133">If it is not, the command uses the `New-PSDrive` cmdlet to create a temporary drive that is mapped to the HKLM:\SOFTWARE registry key.</span></span>

### <span data-ttu-id="4215c-134">示例5：比较文件的类型系统驱动器</span><span class="sxs-lookup"><span data-stu-id="4215c-134">Example 5: Compare the types of files system drives</span></span>

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
X                                      Registry      HKLM:\Network

PS C:\> net use
New connections will be remembered.
Status       Local     Remote                    Network
-------------------------------------------------------------------------------
OK           G:        \\Server01\Public         Microsoft Windows Network

PS C:\> [System.IO.DriveInfo]::GetDrives() | Format-Table
Name DriveType DriveFormat IsReady AvailableFreeSpace TotalFreeSpace TotalSize     RootDirectory VolumeLabel
---- --------- ----------- ------- ------------------ -------------- ---------     ------------- -----------
A:\    Network               False                                                 A:\
C:\      Fixed NTFS          True  771920580608       771920580608   988877418496  C:\           Windows
D:\      Fixed NTFS          True  689684144128       689684144128   1990045179904 D:\           Big Drive
E:\      CDRom               False                                                 E:\
G:\    Network NTFS          True      69120000           69120000       104853504 G:\           GratefulDead

PS N:\> Get-CimInstance -Class Win32_LogicalDisk

DeviceID DriveType ProviderName   VolumeName         Size          FreeSpace
-------- --------- ------------   ----------         ----          ---------
A:       4
C:       3                        Windows            988877418496  771926069248
D:       3                        Big!              1990045179904  689684144128
E:       5
G:       4         \\Music\GratefulDead              988877418496  771926069248


PS C:\> Get-CimInstance -Class Win32_NetworkConnection
LocalName RemoteName            ConnectionState Status
--------- ----------            --------------- ------
G:        \\Music\GratefulDead  Connected       OK
```

<span data-ttu-id="4215c-135">此示例将显示的文件系统驱动器的类型 `Get-PSDrive` 与使用其他方法显示的文件系统驱动器进行比较。</span><span class="sxs-lookup"><span data-stu-id="4215c-135">This example compares the types of file system drives that are displayed by `Get-PSDrive` to those displayed by using other methods.</span></span> <span data-ttu-id="4215c-136">此示例演示了在 Windows PowerShell 中显示驱动器的不同方式，并显示了使用 New-PSDrive cmdlet 创建的特定于会话的驱动器只能在 Windows PowerShell 中访问。</span><span class="sxs-lookup"><span data-stu-id="4215c-136">This example demonstrates different ways to display drives in Windows PowerShell, and it shows that session-specific drives created by using the New-PSDrive cmdlet are accessible only in Windows PowerShell.</span></span>

<span data-ttu-id="4215c-137">第一个命令使用 `Get-PSDrive` 来获取会话中的所有文件系统驱动器。</span><span class="sxs-lookup"><span data-stu-id="4215c-137">The first command uses `Get-PSDrive` to get all of the file system drives in the session.</span></span> <span data-ttu-id="4215c-138">这包括固定驱动器 (C：和 D： ) 、映射的网络驱动器 (G：通过使用的 **保持** 参数创建的 G： ) `New-PSDrive` ，以及使用 `New-PSDrive` 不带 **持久性** 参数创建的 PowerShell 驱动器 (T： ) 。</span><span class="sxs-lookup"><span data-stu-id="4215c-138">This includes the fixed drives (C: and D:), a mapped network drive (G:) that was created by using the **Persist** parameter of `New-PSDrive`, and a PowerShell drive (T:) that was created by using `New-PSDrive` without the **Persist** parameter.</span></span>

<span data-ttu-id="4215c-139">**Net use** 命令显示 Windows 映射网络驱动器，在这种情况下，它只显示 G 驱动器。</span><span class="sxs-lookup"><span data-stu-id="4215c-139">The **net use** command displays Windows mapped network drives, in this case it displays only the G drive.</span></span> <span data-ttu-id="4215c-140">它不显示创建的 X：驱动器 `New-PSDrive` 。</span><span class="sxs-lookup"><span data-stu-id="4215c-140">It does not display the X: drive that was created by `New-PSDrive`.</span></span> <span data-ttu-id="4215c-141">它显示 G：驱动器还映射到 \\ \\ 音乐 \\ GratefulDead。</span><span class="sxs-lookup"><span data-stu-id="4215c-141">It shows that the G: drive is also mapped to \\\\Music\\GratefulDead.</span></span>

<span data-ttu-id="4215c-142">第三条命令使用 Microsoft .NET Framework **System.IO.DriveInfo** 类的 **GetDrives** 方法。</span><span class="sxs-lookup"><span data-stu-id="4215c-142">The third command uses the **GetDrives** method of the Microsoft .NET Framework **System.IO.DriveInfo** class.</span></span> <span data-ttu-id="4215c-143">此命令获取 Windows 文件系统驱动器，包括驱动器 G：，但不会获取创建的驱动器 `New-PSDrive` 。</span><span class="sxs-lookup"><span data-stu-id="4215c-143">This command gets the Windows file system drives, including drive G:, but it does not get the drives created by `New-PSDrive`.</span></span>

<span data-ttu-id="4215c-144">第四条命令使用 `Get-CimInstance` cmdlet 来获取 **Win32_LogicalDisk** 类的实例。</span><span class="sxs-lookup"><span data-stu-id="4215c-144">The fourth command uses the `Get-CimInstance` cmdlet to get the instances of the **Win32_LogicalDisk** class.</span></span> <span data-ttu-id="4215c-145">它将返回 A：、C：、D：、E：和 G：驱动器，但不返回创建的驱动器 `New-PSDrive` 。</span><span class="sxs-lookup"><span data-stu-id="4215c-145">It returns the A:, C:, D:, E:, and G: drives, but not the drives created by `New-PSDrive`.</span></span>

<span data-ttu-id="4215c-146">最后一条命令使用 `Get-CimInstance` cmdlet 来显示 **Win32_NetworkConnection** 类的实例。</span><span class="sxs-lookup"><span data-stu-id="4215c-146">The last command uses the `Get-CimInstance` cmdlet to display the instances of the **Win32_NetworkConnection** class.</span></span> <span data-ttu-id="4215c-147">与 **net use** 类似，它仅返回由创建的永久性 G：驱动器 `New-PSDrive` 。</span><span class="sxs-lookup"><span data-stu-id="4215c-147">Like **net use** , it returns only the persistent G: drive created by `New-PSDrive`.</span></span>

## <span data-ttu-id="4215c-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4215c-148">PARAMETERS</span></span>

### <span data-ttu-id="4215c-149">-LiteralName</span><span class="sxs-lookup"><span data-stu-id="4215c-149">-LiteralName</span></span>

<span data-ttu-id="4215c-150">指定驱动器的名称。</span><span class="sxs-lookup"><span data-stu-id="4215c-150">Specifies the name of the drive.</span></span>

<span data-ttu-id="4215c-151">**LiteralName** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="4215c-151">The value of **LiteralName** is used exactly as it is typed.</span></span> <span data-ttu-id="4215c-152">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="4215c-152">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="4215c-153">如果名称包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="4215c-153">If the name includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="4215c-154">单引号会告知 Windows PowerShell 不要将所有字符都解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="4215c-154">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4215c-155">-Name</span><span class="sxs-lookup"><span data-stu-id="4215c-155">-Name</span></span>

<span data-ttu-id="4215c-156">以字符串数组的形式指定此 cmdlet 在操作中获取的驱动器的名称或名称。</span><span class="sxs-lookup"><span data-stu-id="4215c-156">Specifies, as a string array, the name or name of drives that this cmdlet gets in the operation.</span></span>
<span data-ttu-id="4215c-157">键入驱动器名称或驱动器号，不带冒号 (:)。</span><span class="sxs-lookup"><span data-stu-id="4215c-157">Type the drive name or letter without a colon (:).</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4215c-158">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="4215c-158">-PSProvider</span></span>

<span data-ttu-id="4215c-159">指定为 Windows PowerShell 提供程序形式的字符串数组。</span><span class="sxs-lookup"><span data-stu-id="4215c-159">Specifies, as a string array, the Windows PowerShell provider.</span></span> <span data-ttu-id="4215c-160">此 cmdlet 仅获取此提供程序支持的驱动器。</span><span class="sxs-lookup"><span data-stu-id="4215c-160">This cmdlet gets only the drives supported by this provider.</span></span> <span data-ttu-id="4215c-161">键入提供程序的名称，如 FileSystem、Registry 或 Certificate。</span><span class="sxs-lookup"><span data-stu-id="4215c-161">Type the name of a provider, such as FileSystem, Registry, or Certificate.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4215c-162">-Scope</span><span class="sxs-lookup"><span data-stu-id="4215c-162">-Scope</span></span>

<span data-ttu-id="4215c-163">指定此 cmdlet 获取驱动器的范围。</span><span class="sxs-lookup"><span data-stu-id="4215c-163">Specifies the scope in which this cmdlet gets the drives.</span></span>

<span data-ttu-id="4215c-164">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="4215c-164">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4215c-165">全球</span><span class="sxs-lookup"><span data-stu-id="4215c-165">Global</span></span>
- <span data-ttu-id="4215c-166">Local</span><span class="sxs-lookup"><span data-stu-id="4215c-166">Local</span></span>
- <span data-ttu-id="4215c-167">脚本</span><span class="sxs-lookup"><span data-stu-id="4215c-167">Script</span></span>
- <span data-ttu-id="4215c-168">一个相对于当前作用域的数字 (0 到作用域数，其中0是当前作用域，1是其父) 。</span><span class="sxs-lookup"><span data-stu-id="4215c-168">a number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span> <span data-ttu-id="4215c-169">默认值为“Local”。</span><span class="sxs-lookup"><span data-stu-id="4215c-169">"Local" is the default.</span></span>

<span data-ttu-id="4215c-170">有关详细信息，请参阅 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="4215c-170">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

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

### <span data-ttu-id="4215c-171">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4215c-171">CommonParameters</span></span>

<span data-ttu-id="4215c-172">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4215c-172">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4215c-173">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4215c-173">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4215c-174">输入</span><span class="sxs-lookup"><span data-stu-id="4215c-174">INPUTS</span></span>

### <span data-ttu-id="4215c-175">无</span><span class="sxs-lookup"><span data-stu-id="4215c-175">None</span></span>

<span data-ttu-id="4215c-176">不能通过管道将对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4215c-176">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="4215c-177">输出</span><span class="sxs-lookup"><span data-stu-id="4215c-177">OUTPUTS</span></span>

### <span data-ttu-id="4215c-178">System.Management.Automation.PSDriveInfo</span><span class="sxs-lookup"><span data-stu-id="4215c-178">System.Management.Automation.PSDriveInfo</span></span>

<span data-ttu-id="4215c-179">此 cmdlet 将返回表示会话中的驱动器的对象。</span><span class="sxs-lookup"><span data-stu-id="4215c-179">This cmdlet returns objects that represent the drives in the session.</span></span>

## <span data-ttu-id="4215c-180">注释</span><span class="sxs-lookup"><span data-stu-id="4215c-180">NOTES</span></span>

* <span data-ttu-id="4215c-181">此 cmdlet 用于处理由任何提供程序公开的数据。</span><span class="sxs-lookup"><span data-stu-id="4215c-181">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="4215c-182">若要列出会话中的可用提供程序，请使用 `Get-PSProvider` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4215c-182">To list the providers available in your session, use the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="4215c-183">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="4215c-183">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
* <span data-ttu-id="4215c-184">使用 New-PSDrive cmdlet 的 **Persist** 参数创建的映射网络驱动器是特定于用户帐户的。</span><span class="sxs-lookup"><span data-stu-id="4215c-184">Mapped network drives that are created by using the **Persist** parameter of the New-PSDrive cmdlet are specific to a user account.</span></span> <span data-ttu-id="4215c-185">在以 "以管理员身份运行" 选项启动的会话中创建的映射网络驱动器，或具有其他用户的凭据的会话在没有显式凭据或当前用户凭据启动的会话中不可见。</span><span class="sxs-lookup"><span data-stu-id="4215c-185">Mapped network drives that you create in sessions that are started with the Run as administrator option or with the credentials of another user are not visible in sessions that are started without explicit credentials or with the credentials of the current user.</span></span>

## <span data-ttu-id="4215c-186">相关链接</span><span class="sxs-lookup"><span data-stu-id="4215c-186">RELATED LINKS</span></span>

[<span data-ttu-id="4215c-187">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="4215c-187">New-PSDrive</span></span>](New-PSDrive.md)

[<span data-ttu-id="4215c-188">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="4215c-188">Remove-PSDrive</span></span>](Remove-PSDrive.md)

[<span data-ttu-id="4215c-189">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="4215c-189">Get-PSProvider</span></span>](Get-PSProvider.md)
