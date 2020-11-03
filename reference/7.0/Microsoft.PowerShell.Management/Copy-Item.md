---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/copy-item?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Copy-Item
ms.openlocfilehash: 6ddcada506e5bc1ed70615ce32b1481b7d4e9d8b
ms.sourcegitcommit: 33ac34789e86ffb4e7e69453ae38fc0bd24933dd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "93199370"
---
# <span data-ttu-id="9ca65-103">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="9ca65-103">Copy-Item</span></span>

## <span data-ttu-id="9ca65-104">摘要</span><span class="sxs-lookup"><span data-stu-id="9ca65-104">SYNOPSIS</span></span>
<span data-ttu-id="9ca65-105">将项从一个位置复制到另一个位置。</span><span class="sxs-lookup"><span data-stu-id="9ca65-105">Copies an item from one location to another.</span></span>

## <span data-ttu-id="9ca65-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9ca65-106">SYNTAX</span></span>

### <span data-ttu-id="9ca65-107">Path（默认值）</span><span class="sxs-lookup"><span data-stu-id="9ca65-107">Path (Default)</span></span>

```
Copy-Item [-Path] <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

### <span data-ttu-id="9ca65-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9ca65-108">LiteralPath</span></span>

```
Copy-Item -LiteralPath <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

## <span data-ttu-id="9ca65-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9ca65-109">DESCRIPTION</span></span>

<span data-ttu-id="9ca65-110">`Copy-Item`Cmdlet 将项从一个位置复制到同一命名空间中的另一个位置。</span><span class="sxs-lookup"><span data-stu-id="9ca65-110">The `Copy-Item` cmdlet copies an item from one location to another location in the same namespace.</span></span>
<span data-ttu-id="9ca65-111">例如，它可以将文件复制到文件夹，但无法将文件复制到证书驱动器。</span><span class="sxs-lookup"><span data-stu-id="9ca65-111">For instance, it can copy a file to a folder, but it can't copy a file to a certificate drive.</span></span>

<span data-ttu-id="9ca65-112">此 cmdlet 不会剪切或删除要复制的项。</span><span class="sxs-lookup"><span data-stu-id="9ca65-112">This cmdlet doesn't cut or delete the items being copied.</span></span> <span data-ttu-id="9ca65-113">Cmdlet 可复制的特定项取决于公开该项的 PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="9ca65-113">The particular items that the cmdlet can copy depend on the PowerShell provider that exposes the item.</span></span> <span data-ttu-id="9ca65-114">例如，它可以复制文件系统驱动器中的文件和目录以及注册表驱动器中的注册表项和条目。</span><span class="sxs-lookup"><span data-stu-id="9ca65-114">For instance, it can copy files and directories in a file system drive and registry keys and entries in the registry drive.</span></span>

<span data-ttu-id="9ca65-115">此 cmdlet 可以复制和重命名同一命令中的项。</span><span class="sxs-lookup"><span data-stu-id="9ca65-115">This cmdlet can copy and rename items in the same command.</span></span> <span data-ttu-id="9ca65-116">若要重命名某个项，请在 **Destination** 参数的值中输入新名称。</span><span class="sxs-lookup"><span data-stu-id="9ca65-116">To rename an item, enter the new name in the value of the **Destination** parameter.</span></span> <span data-ttu-id="9ca65-117">若要重命名某个项而不复制该项，请使用 `Rename-Item` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9ca65-117">To rename an item and not copy it, use the `Rename-Item` cmdlet.</span></span>

## <span data-ttu-id="9ca65-118">示例</span><span class="sxs-lookup"><span data-stu-id="9ca65-118">EXAMPLES</span></span>

### <span data-ttu-id="9ca65-119">示例1：将文件复制到指定的目录</span><span class="sxs-lookup"><span data-stu-id="9ca65-119">Example 1: Copy a file to the specified directory</span></span>

<span data-ttu-id="9ca65-120">此示例将 `mar1604.log.txt` 文件复制到 `C:\Presentation` 目录。</span><span class="sxs-lookup"><span data-stu-id="9ca65-120">This example copies the `mar1604.log.txt` file to the `C:\Presentation` directory.</span></span> <span data-ttu-id="9ca65-121">不会删除原始文件。</span><span class="sxs-lookup"><span data-stu-id="9ca65-121">The original file isn't deleted.</span></span>

```powershell
Copy-Item "C:\Wabash\Logfiles\mar1604.log.txt" -Destination "C:\Presentation"
```

### <span data-ttu-id="9ca65-122">示例2：将目录内容复制到现有目录</span><span class="sxs-lookup"><span data-stu-id="9ca65-122">Example 2: Copy directory contents to an existing directory</span></span>

<span data-ttu-id="9ca65-123">此示例将目录的内容复制 `C:\Logfiles` 到现有目录中 `C:\Drawings` 。</span><span class="sxs-lookup"><span data-stu-id="9ca65-123">This example copies the contents of the `C:\Logfiles` directory into the existing `C:\Drawings` directory.</span></span> <span data-ttu-id="9ca65-124">`Logfiles`不复制此目录。</span><span class="sxs-lookup"><span data-stu-id="9ca65-124">The `Logfiles` directory isn't copied.</span></span>

<span data-ttu-id="9ca65-125">如果 `Logfiles` 目录在子目录中包含文件，则会将这些子目录原样复制到其文件树中。</span><span class="sxs-lookup"><span data-stu-id="9ca65-125">If the `Logfiles` directory contains files in subdirectories, those subdirectories are copied with their file trees intact.</span></span> <span data-ttu-id="9ca65-126">默认情况下， **Container** 参数设置为 **True** ，这将保留目录结构。</span><span class="sxs-lookup"><span data-stu-id="9ca65-126">By default, the **Container** parameter is set to **True** , which preserves the directory structure.</span></span>

```powershell
Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings" -Recurse
```

> [!NOTE]
> <span data-ttu-id="9ca65-127">如果需要 `Logfiles` 在副本中包含目录，请 `\*` 从 **路径** 中删除。</span><span class="sxs-lookup"><span data-stu-id="9ca65-127">If you need to include the `Logfiles` directory in the copy, remove the `\*` from the **Path** .</span></span>
> <span data-ttu-id="9ca65-128">例如：</span><span class="sxs-lookup"><span data-stu-id="9ca65-128">For example:</span></span>
>
> `Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings" -Recurse`

### <span data-ttu-id="9ca65-129">示例3：将目录和内容复制到新目录</span><span class="sxs-lookup"><span data-stu-id="9ca65-129">Example 3: Copy directory and contents to a new directory</span></span>

<span data-ttu-id="9ca65-130">此示例将复制 `C:\Logfiles` 源目录的内容并创建一个新的目标目录。</span><span class="sxs-lookup"><span data-stu-id="9ca65-130">This example copies the contents of the `C:\Logfiles` source directory and creates a new destination directory.</span></span> <span data-ttu-id="9ca65-131">在中创建新的目标目录 `\Logs` `C:\Drawings` 。</span><span class="sxs-lookup"><span data-stu-id="9ca65-131">The new destination directory, `\Logs` is created in `C:\Drawings`.</span></span>

<span data-ttu-id="9ca65-132">若要包括源目录的名称，请复制到现有目标目录，如 **示例 2** 所示。</span><span class="sxs-lookup"><span data-stu-id="9ca65-132">To include the source directory's name, copy to an existing destination directory as shown in **Example 2** .</span></span> <span data-ttu-id="9ca65-133">或者，将新的目标目录命名为与源目录相同。</span><span class="sxs-lookup"><span data-stu-id="9ca65-133">Or, name the new destination directory with the same as the source directory.</span></span>

```powershell
Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings\Logs" -Recurse
```

> [!NOTE]
> <span data-ttu-id="9ca65-134">如果 **路径** 包含 `\*` ，则会将目录的所有文件内容（包括子目录树）复制到新的目标目录。</span><span class="sxs-lookup"><span data-stu-id="9ca65-134">If the **Path** includes `\*`, all the directory's file contents, including the subdirectory trees, are copied to the new destination directory.</span></span> <span data-ttu-id="9ca65-135">例如：</span><span class="sxs-lookup"><span data-stu-id="9ca65-135">For example:</span></span>
>
> `Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings\Logs" -Recurse`

### <span data-ttu-id="9ca65-136">示例4：将文件复制到指定的目录并重命名文件</span><span class="sxs-lookup"><span data-stu-id="9ca65-136">Example 4: Copy a file to the specified directory and rename the file</span></span>

<span data-ttu-id="9ca65-137">此示例使用 `Copy-Item` cmdlet 将 `Get-Widget.ps1` 脚本从 `\\Server01\Share` 目录复制到 `\\Server12\ScriptArchive` 目录。</span><span class="sxs-lookup"><span data-stu-id="9ca65-137">This example uses the `Copy-Item` cmdlet to copy the `Get-Widget.ps1` script from the `\\Server01\Share` directory to the `\\Server12\ScriptArchive` directory.</span></span> <span data-ttu-id="9ca65-138">作为复制操作的一部分，该命令会将项名称从更改 `Get-Widget.ps1` 为 `Get-Widget.ps1.txt` ，以便可以将其附加到电子邮件中。</span><span class="sxs-lookup"><span data-stu-id="9ca65-138">As part of the copy operation, the command changes the item name from `Get-Widget.ps1` to `Get-Widget.ps1.txt`, so it can be attached to email messages.</span></span>

```powershell
Copy-Item "\\Server01\Share\Get-Widget.ps1" -Destination "\\Server12\ScriptArchive\Get-Widget.ps1.txt"
```

### <span data-ttu-id="9ca65-139">示例5：将文件复制到远程计算机</span><span class="sxs-lookup"><span data-stu-id="9ca65-139">Example 5: Copy a file to a remote computer</span></span>

<span data-ttu-id="9ca65-140">使用的凭据将会话创建到名为 **Server01** 的远程计算机 `Contoso\User01` ，并将结果存储在名为的变量中 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="9ca65-140">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="9ca65-141">该 `Copy-Item` cmdlet `test.log` `D:\Folder001` 使用存储在变量中的会话信息，将文件夹中的文件夹复制到 `C:\Folder001_Copy` 远程计算机上的文件夹 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="9ca65-141">The `Copy-Item` cmdlet copies `test.log` from the `D:\Folder001` folder to the `C:\Folder001_Copy` folder on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="9ca65-142">不会删除原始文件。</span><span class="sxs-lookup"><span data-stu-id="9ca65-142">The original file isn't deleted.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "D:\Folder001\test.log" -Destination "C:\Folder001_Copy\" -ToSession $Session
```

### <span data-ttu-id="9ca65-143">示例6：将文件夹复制到远程计算机</span><span class="sxs-lookup"><span data-stu-id="9ca65-143">Example 6: Copy a folder to a remote computer</span></span>

<span data-ttu-id="9ca65-144">使用的凭据将会话创建到名为 **Server01** 的远程计算机 `Contoso\User01` ，并将结果存储在名为的变量中 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="9ca65-144">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="9ca65-145">`Copy-Item`Cmdlet `D:\Folder002` `C:\Folder002_Copy` 使用存储在变量中的会话信息将文件夹复制到远程计算机上的目录中 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="9ca65-145">The `Copy-Item` cmdlet copies the `D:\Folder002` folder to the `C:\Folder002_Copy` directory on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="9ca65-146">不使用 **递归** 开关复制任何子文件夹或文件。</span><span class="sxs-lookup"><span data-stu-id="9ca65-146">Any subfolders or files are not copied without using the **Recurse** switch.</span></span>
<span data-ttu-id="9ca65-147">如果文件夹尚不存在，则该操作将创建该 `Folder002_Copy` 文件夹。</span><span class="sxs-lookup"><span data-stu-id="9ca65-147">The operation creates the `Folder002_Copy` folder if it doesn't already exist.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server02" -Credential "Contoso\User01"
Copy-Item "D:\Folder002\" -Destination "C:\Folder002_Copy\" -ToSession $Session
```

### <span data-ttu-id="9ca65-148">示例7：以递归方式将文件夹的全部内容复制到远程计算机</span><span class="sxs-lookup"><span data-stu-id="9ca65-148">Example 7: Recursively copy the entire contents of a folder to a remote computer</span></span>

<span data-ttu-id="9ca65-149">使用的凭据将会话创建到名为 **Server01** 的远程计算机 `Contoso\User01` ，并将结果存储在名为的变量中 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="9ca65-149">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="9ca65-150">`Copy-Item`Cmdlet `D:\Folder003` `C:\Folder003_Copy` 使用存储在变量中的会话信息，将文件夹中的全部内容复制到远程计算机上的目录中 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="9ca65-150">The `Copy-Item` cmdlet copies the entire contents from the `D:\Folder003` folder to the `C:\Folder003_Copy` directory on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="9ca65-151">子文件夹将会原样复制到其文件树中。</span><span class="sxs-lookup"><span data-stu-id="9ca65-151">The subfolders are copied with their file trees intact.</span></span> <span data-ttu-id="9ca65-152">如果文件夹尚不存在，则该操作将创建该 `Folder003_Copy` 文件夹。</span><span class="sxs-lookup"><span data-stu-id="9ca65-152">The operation creates the `Folder003_Copy` folder if it doesn't already exist.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder003\" -Destination "C:\Folder003_Copy\" -ToSession $Session -Recurse
```

### <span data-ttu-id="9ca65-153">示例8：将文件复制到远程计算机，然后重命名该文件</span><span class="sxs-lookup"><span data-stu-id="9ca65-153">Example 8: Copy a file to a remote computer and then rename the file</span></span>

<span data-ttu-id="9ca65-154">使用的凭据将会话创建到名为 **Server01** 的远程计算机 `Contoso\User01` ，并将结果存储在名为的变量中 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="9ca65-154">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="9ca65-155">该 `Copy-Item` cmdlet `scriptingexample.ps1` `D:\Folder004` 使用存储在变量中的会话信息，将文件夹中的文件夹复制到 `C:\Folder004_Copy` 远程计算机上的文件夹 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="9ca65-155">The `Copy-Item` cmdlet copies `scriptingexample.ps1` from the `D:\Folder004` folder to the `C:\Folder004_Copy` folder on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="9ca65-156">作为复制操作的一部分，该命令会将项名称从更改 `scriptingexample.ps1` 为 `scriptingexample_copy.ps1` ，以便可以将其附加到电子邮件中。</span><span class="sxs-lookup"><span data-stu-id="9ca65-156">As part of the copy operation, the command changes the item name from `scriptingexample.ps1` to `scriptingexample_copy.ps1`, so it can be attached to email messages.</span></span> <span data-ttu-id="9ca65-157">不会删除原始文件。</span><span class="sxs-lookup"><span data-stu-id="9ca65-157">The original file isn't deleted.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder004\scriptingexample.ps1" -Destination "C:\Folder004_Copy\scriptingexample_copy.ps1" -ToSession $Session
```

### <span data-ttu-id="9ca65-158">示例9：将远程文件复制到本地计算机</span><span class="sxs-lookup"><span data-stu-id="9ca65-158">Example 9: Copy a remote file to the local computer</span></span>

<span data-ttu-id="9ca65-159">使用的凭据将会话创建到名为 **Server01** 的远程计算机 `Contoso\User01` ，并将结果存储在名为的变量中 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="9ca65-159">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="9ca65-160">该 `Copy-Item` cmdlet `test.log` `C:\MyRemoteData\` `D:\MyLocalData` 使用存储在变量中的会话信息从远程文件夹复制到本地文件夹 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="9ca65-160">The `Copy-Item` cmdlet copies `test.log` from the remote `C:\MyRemoteData\` to the local `D:\MyLocalData` folder using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="9ca65-161">不会删除原始文件。</span><span class="sxs-lookup"><span data-stu-id="9ca65-161">The original file isn't deleted.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\test.log" -Destination "D:\MyLocalData\" -FromSession $Session
```

### <span data-ttu-id="9ca65-162">示例10：将远程文件夹的全部内容复制到本地计算机</span><span class="sxs-lookup"><span data-stu-id="9ca65-162">Example 10: Copy the entire contents of a remote folder to the local computer</span></span>

<span data-ttu-id="9ca65-163">使用的凭据将会话创建到名为 **Server01** 的远程计算机 `Contoso\User01` ，并将结果存储在名为的变量中 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="9ca65-163">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="9ca65-164">`Copy-Item`Cmdlet `C:\MyRemoteData\scripts` `D:\MyLocalData` 使用变量中存储的会话信息将远程文件夹中的全部内容复制到本地文件夹 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="9ca65-164">The `Copy-Item` cmdlet copies the entire contents from the remote `C:\MyRemoteData\scripts` folder to the local `D:\MyLocalData` folder using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="9ca65-165">如果 "脚本" 文件夹的子文件夹中包含文件，则会将这些子文件夹原样复制到其文件树中。</span><span class="sxs-lookup"><span data-stu-id="9ca65-165">If the scripts folder contains files in subfolders, those subfolders are copied with their file trees intact.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\" -FromSession $Session
```

### <span data-ttu-id="9ca65-166">示例11：以递归方式将远程文件夹的全部内容复制到本地计算机</span><span class="sxs-lookup"><span data-stu-id="9ca65-166">Example 11: Recursively copy the entire contents of a remote folder to the local computer</span></span>

<span data-ttu-id="9ca65-167">使用的凭据将会话创建到名为 **Server01** 的远程计算机 `Contoso\User01` ，并将结果存储在名为的变量中 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="9ca65-167">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="9ca65-168">`Copy-Item`Cmdlet `C:\MyRemoteData\scripts` `D:\MyLocalData\scripts` 使用变量中存储的会话信息将远程文件夹中的全部内容复制到本地文件夹 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="9ca65-168">The `Copy-Item` cmdlet copies the entire contents from the remote `C:\MyRemoteData\scripts` folder to the local `D:\MyLocalData\scripts` folder using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="9ca65-169">由于使用了 **递归** 参数，因此，如果脚本文件夹尚不存在，则该操作将创建它们。</span><span class="sxs-lookup"><span data-stu-id="9ca65-169">Because the **Recurse** parameter is used, the operation creates the scripts folder if it doesn't already exist.</span></span> <span data-ttu-id="9ca65-170">如果 "脚本" 文件夹的子文件夹中包含文件，则会将这些子文件夹原样复制到其文件树中。</span><span class="sxs-lookup"><span data-stu-id="9ca65-170">If the scripts folder contains files in subfolders, those subfolders are copied with their file trees intact.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\scripts" -FromSession $Session -Recurse
```

### <span data-ttu-id="9ca65-171">示例12：以递归方式将文件从文件夹树复制到当前文件夹中</span><span class="sxs-lookup"><span data-stu-id="9ca65-171">Example 12: Recursively copy files from a folder tree into the current folder</span></span>

<span data-ttu-id="9ca65-172">此示例演示如何将文件从多级文件夹结构复制到单个平面文件夹中。</span><span class="sxs-lookup"><span data-stu-id="9ca65-172">This example shows how to copy files from a multilevel folder structure into a single flat folder.</span></span>
<span data-ttu-id="9ca65-173">前三个命令显示现有文件夹结构和两个文件的内容，两个文件都是名称 `file3.txt` 。</span><span class="sxs-lookup"><span data-stu-id="9ca65-173">The first three commands show the existing folder structure and the contents of two files, both names `file3.txt`.</span></span>

```powershell
PS C:\temp\test> (Get-ChildItem C:\temp\tree -Recurse).FullName
C:\temp\tree\subfolder
C:\temp\tree\file1.txt
C:\temp\tree\file2.txt
C:\temp\tree\file3.txt
C:\temp\tree\subfolder\file3.txt
C:\temp\tree\subfolder\file4.txt
C:\temp\tree\subfolder\file5.txt

PS C:\temp\test> Get-Content C:\temp\tree\file3.txt
This is file3.txt in the root folder

PS C:\temp\test> Get-Content C:\temp\tree\subfolder\file3.txt
This is file3.txt in the subfolder

PS C:\temp\test> Copy-Item -Path C:\temp\tree -Filter *.txt -Recurse -Container:$false
PS C:\temp\test> (Get-ChildItem . -Recurse).FullName
C:\temp\test\subfolder
C:\temp\test\file1.txt
C:\temp\test\file2.txt
C:\temp\test\file3.txt
C:\temp\test\file4.txt
C:\temp\test\file5.txt

PS C:\temp\test> Get-Content .\file3.txt
This is file3.txt in the subfolder
```

<span data-ttu-id="9ca65-174">`Copy-Item`Cmdlet 将 **容器** 参数设置为 `$false` 。</span><span class="sxs-lookup"><span data-stu-id="9ca65-174">The `Copy-Item` cmdlet has the **Container** parameter set to `$false`.</span></span> <span data-ttu-id="9ca65-175">这会导致复制源文件夹的内容，但不会保留文件夹结构。</span><span class="sxs-lookup"><span data-stu-id="9ca65-175">This causes the contents of the source folder to be copied but does not preserve the folder structure.</span></span> <span data-ttu-id="9ca65-176">请注意，具有相同名称的文件在目标文件夹中被覆盖。</span><span class="sxs-lookup"><span data-stu-id="9ca65-176">Notice that files with the same name are overwritten in the destination folder.</span></span>

## <span data-ttu-id="9ca65-177">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9ca65-177">PARAMETERS</span></span>

### <span data-ttu-id="9ca65-178">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9ca65-178">-Confirm</span></span>

<span data-ttu-id="9ca65-179">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="9ca65-179">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9ca65-180">-Container</span><span class="sxs-lookup"><span data-stu-id="9ca65-180">-Container</span></span>

<span data-ttu-id="9ca65-181">指示此 cmdlet 在复制操作期间保留容器对象。</span><span class="sxs-lookup"><span data-stu-id="9ca65-181">Indicates that this cmdlet preserves container objects during the copy operation.</span></span> <span data-ttu-id="9ca65-182">默认情况下， **Container** 参数设置为 **True** 。</span><span class="sxs-lookup"><span data-stu-id="9ca65-182">By default, the **Container** parameter is set to **True** .</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ca65-183">-Credential</span><span class="sxs-lookup"><span data-stu-id="9ca65-183">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="9ca65-184">随 PowerShell 一起安装的任何提供程序都不支持此参数。</span><span class="sxs-lookup"><span data-stu-id="9ca65-184">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="9ca65-185">若要在运行此 cmdlet 时模拟其他用户或提升凭据，请使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="9ca65-185">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="9ca65-186">-Destination</span><span class="sxs-lookup"><span data-stu-id="9ca65-186">-Destination</span></span>

<span data-ttu-id="9ca65-187">指定新位置的路径。</span><span class="sxs-lookup"><span data-stu-id="9ca65-187">Specifies the path to the new location.</span></span> <span data-ttu-id="9ca65-188">默认为当前目录。</span><span class="sxs-lookup"><span data-stu-id="9ca65-188">The default is the current directory.</span></span>

<span data-ttu-id="9ca65-189">若要重命名要复制的项，请在 **Destination** 参数的值中指定新名称。</span><span class="sxs-lookup"><span data-stu-id="9ca65-189">To rename the item being copied, specify a new name in the value of the **Destination** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9ca65-190">-Exclude</span><span class="sxs-lookup"><span data-stu-id="9ca65-190">-Exclude</span></span>

<span data-ttu-id="9ca65-191">指定为字符串数组，此 cmdlet 在操作中排除的项。</span><span class="sxs-lookup"><span data-stu-id="9ca65-191">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="9ca65-192">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="9ca65-192">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="9ca65-193">请输入路径元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="9ca65-193">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="9ca65-194">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="9ca65-194">Wildcard characters are permitted.</span></span> <span data-ttu-id="9ca65-195">仅 **Exclude** 当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Exclude 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="9ca65-195">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="9ca65-196">-Filter</span><span class="sxs-lookup"><span data-stu-id="9ca65-196">-Filter</span></span>

<span data-ttu-id="9ca65-197">指定用于限定 **路径** 参数的筛选器。</span><span class="sxs-lookup"><span data-stu-id="9ca65-197">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="9ca65-198">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供程序是唯一一种支持使用筛选器的已安装 PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="9ca65-198">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="9ca65-199">可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **文件系统** 筛选语言的语法。</span><span class="sxs-lookup"><span data-stu-id="9ca65-199">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="9ca65-200">筛选器比其他参数更有效，因为提供程序在 cmdlet 获取对象时应用筛选器，而不是在检索对象后再对其进行筛选。</span><span class="sxs-lookup"><span data-stu-id="9ca65-200">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="9ca65-201">-Force</span><span class="sxs-lookup"><span data-stu-id="9ca65-201">-Force</span></span>

<span data-ttu-id="9ca65-202">指示此 cmdlet 将复制不能更改的项，如复制只读文件或别名。</span><span class="sxs-lookup"><span data-stu-id="9ca65-202">Indicates that this cmdlet copies items that can't otherwise be changed, such as copying over a read-only file or alias.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ca65-203">-FromSession</span><span class="sxs-lookup"><span data-stu-id="9ca65-203">-FromSession</span></span>

<span data-ttu-id="9ca65-204">指定要从中复制远程文件的 **PSSession** 对象。</span><span class="sxs-lookup"><span data-stu-id="9ca65-204">Specifies the **PSSession** object from which a remote file is being copied.</span></span> <span data-ttu-id="9ca65-205">使用此参数时， **路径** 和 **LiteralPath** 参数将引用远程计算机上的本地路径。</span><span class="sxs-lookup"><span data-stu-id="9ca65-205">When you use this parameter, the **Path** and **LiteralPath** parameters refer to the local path on the remote machine.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ca65-206">-Include</span><span class="sxs-lookup"><span data-stu-id="9ca65-206">-Include</span></span>

<span data-ttu-id="9ca65-207">指定此 cmdlet 将在操作中包含的一个项或多个项（作为一个字符串数组）。</span><span class="sxs-lookup"><span data-stu-id="9ca65-207">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="9ca65-208">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="9ca65-208">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="9ca65-209">请输入路径元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="9ca65-209">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="9ca65-210">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="9ca65-210">Wildcard characters are permitted.</span></span> <span data-ttu-id="9ca65-211">仅 **Include** 当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Include 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="9ca65-211">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="9ca65-212">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9ca65-212">-LiteralPath</span></span>

<span data-ttu-id="9ca65-213">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="9ca65-213">Specifies a path to one or more locations.</span></span> <span data-ttu-id="9ca65-214">**LiteralPath** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="9ca65-214">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="9ca65-215">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="9ca65-215">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="9ca65-216">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="9ca65-216">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="9ca65-217">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="9ca65-217">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="9ca65-218">有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="9ca65-218">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9ca65-219">-PassThru</span><span class="sxs-lookup"><span data-stu-id="9ca65-219">-PassThru</span></span>

<span data-ttu-id="9ca65-220">返回一个对象，该对象表示正在处理的项。</span><span class="sxs-lookup"><span data-stu-id="9ca65-220">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="9ca65-221">默认情况下，此 cmdlet 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="9ca65-221">By default, this cmdlet doesn't generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ca65-222">-Path</span><span class="sxs-lookup"><span data-stu-id="9ca65-222">-Path</span></span>

<span data-ttu-id="9ca65-223">指定为要复制的项的路径（作为字符串数组）。</span><span class="sxs-lookup"><span data-stu-id="9ca65-223">Specifies, as a string array, the path to the items to copy.</span></span> <span data-ttu-id="9ca65-224">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="9ca65-224">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="9ca65-225">-Recurse</span><span class="sxs-lookup"><span data-stu-id="9ca65-225">-Recurse</span></span>

<span data-ttu-id="9ca65-226">指示此 cmdlet 执行递归复制。</span><span class="sxs-lookup"><span data-stu-id="9ca65-226">Indicates that this cmdlet does a recursive copy.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ca65-227">-ToSession</span><span class="sxs-lookup"><span data-stu-id="9ca65-227">-ToSession</span></span>

<span data-ttu-id="9ca65-228">指定远程文件要复制到的 **PSSession** 对象。</span><span class="sxs-lookup"><span data-stu-id="9ca65-228">Specifies the **PSSession** object to which a remote file is being copied.</span></span> <span data-ttu-id="9ca65-229">如果使用此参数，则 **目标** 参数会引用远程计算机上的本地路径。</span><span class="sxs-lookup"><span data-stu-id="9ca65-229">When you use this parameter, the **Destination** parameter refers to the local path on the remote machine.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ca65-230">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9ca65-230">-WhatIf</span></span>

<span data-ttu-id="9ca65-231">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="9ca65-231">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="9ca65-232">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="9ca65-232">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="9ca65-233">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9ca65-233">CommonParameters</span></span>

<span data-ttu-id="9ca65-234">此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="9ca65-234">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="9ca65-235">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="9ca65-235">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9ca65-236">输入</span><span class="sxs-lookup"><span data-stu-id="9ca65-236">INPUTS</span></span>

### <span data-ttu-id="9ca65-237">System.String</span><span class="sxs-lookup"><span data-stu-id="9ca65-237">System.String</span></span>

<span data-ttu-id="9ca65-238">可以通过管道将包含路径的字符串传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9ca65-238">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="9ca65-239">输出</span><span class="sxs-lookup"><span data-stu-id="9ca65-239">OUTPUTS</span></span>

### <span data-ttu-id="9ca65-240">无或表示复制的项的对象</span><span class="sxs-lookup"><span data-stu-id="9ca65-240">None or an object representing the copied item</span></span>

<span data-ttu-id="9ca65-241">当使用 **PassThru** 参数时，此 cmdlet 将返回一个对象，该对象表示复制的项。</span><span class="sxs-lookup"><span data-stu-id="9ca65-241">When you use the **PassThru** parameter, this cmdlet returns an object that represents the copied item.</span></span> <span data-ttu-id="9ca65-242">否则，此 cmdlet 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="9ca65-242">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="9ca65-243">注释</span><span class="sxs-lookup"><span data-stu-id="9ca65-243">NOTES</span></span>

<span data-ttu-id="9ca65-244">此 cmdlet 用于处理由任何提供程序公开的数据。</span><span class="sxs-lookup"><span data-stu-id="9ca65-244">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="9ca65-245">若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="9ca65-245">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="9ca65-246">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="9ca65-246">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="9ca65-247">相关链接</span><span class="sxs-lookup"><span data-stu-id="9ca65-247">RELATED LINKS</span></span>

[<span data-ttu-id="9ca65-248">about_Providers</span><span class="sxs-lookup"><span data-stu-id="9ca65-248">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="9ca65-249">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="9ca65-249">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="9ca65-250">Get-Item</span><span class="sxs-lookup"><span data-stu-id="9ca65-250">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="9ca65-251">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="9ca65-251">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="9ca65-252">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="9ca65-252">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="9ca65-253">Move-Item</span><span class="sxs-lookup"><span data-stu-id="9ca65-253">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="9ca65-254">New-Item</span><span class="sxs-lookup"><span data-stu-id="9ca65-254">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="9ca65-255">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="9ca65-255">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="9ca65-256">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="9ca65-256">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="9ca65-257">Set-Item</span><span class="sxs-lookup"><span data-stu-id="9ca65-257">Set-Item</span></span>](Set-Item.md)
