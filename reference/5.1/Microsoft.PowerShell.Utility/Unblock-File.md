---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unblock-file?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unblock-File
ms.openlocfilehash: 57c8c6f2ceda124b3dc89c363c6cf942680781ca
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344501"
---
# <span data-ttu-id="5a3f5-103">Unblock-File</span><span class="sxs-lookup"><span data-stu-id="5a3f5-103">Unblock-File</span></span>

## <span data-ttu-id="5a3f5-104">摘要</span><span class="sxs-lookup"><span data-stu-id="5a3f5-104">SYNOPSIS</span></span>
<span data-ttu-id="5a3f5-105">取消阻止已从 Internet 下载的文件。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-105">Unblocks files that were downloaded from the Internet.</span></span>

## <span data-ttu-id="5a3f5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5a3f5-106">SYNTAX</span></span>

### <span data-ttu-id="5a3f5-107">ByPath（默认值）</span><span class="sxs-lookup"><span data-stu-id="5a3f5-107">ByPath (Default)</span></span>

```
Unblock-File [-Path] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5a3f5-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="5a3f5-108">ByLiteralPath</span></span>

```
Unblock-File -LiteralPath <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5a3f5-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5a3f5-109">DESCRIPTION</span></span>

<span data-ttu-id="5a3f5-110">`Unblock-File`Cmdlet 可让你打开从 Internet 下载的文件。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-110">The `Unblock-File` cmdlet lets you open files that were downloaded from the Internet.</span></span> <span data-ttu-id="5a3f5-111">它取消阻止从 Internet 下载的 PowerShell 脚本文件，以便你可以运行这些文件，即使 PowerShell 执行策略是 **RemoteSigned** 也是如此。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-111">It unblocks PowerShell script files that were downloaded from the Internet so you can run them, even when the PowerShell execution policy is **RemoteSigned**.</span></span> <span data-ttu-id="5a3f5-112">默认情况下，将阻止这些文件以保护计算机免受不受信任的文件的威胁。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-112">By default, these files are blocked to protect the computer from untrusted files.</span></span>

<span data-ttu-id="5a3f5-113">使用 cmdlet 之前 `Unblock-File` ，请查看该文件及其来源，并验证是否可以安全地打开。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-113">Before using the `Unblock-File` cmdlet, review the file and its source and verify that it is safe to open.</span></span>

<span data-ttu-id="5a3f5-114">在内部，该 `Unblock-File` cmdlet 将删除该区域。标识符备用数据流，该数据流的值为 "3"，表示它是从 Internet 下载的。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-114">Internally, the `Unblock-File` cmdlet removes the Zone.Identifier alternate data stream, which has a value of "3" to indicate that it was downloaded from the Internet.</span></span>

<span data-ttu-id="5a3f5-115">有关 PowerShell 执行策略的详细信息，请参阅 [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-115">For more information about PowerShell execution policies, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

<span data-ttu-id="5a3f5-116">此 cmdlet 是在 Windows PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-116">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="5a3f5-117">示例</span><span class="sxs-lookup"><span data-stu-id="5a3f5-117">EXAMPLES</span></span>

### <span data-ttu-id="5a3f5-118">示例 1：取消阻止一个文件</span><span class="sxs-lookup"><span data-stu-id="5a3f5-118">Example 1: Unblock a file</span></span>

<span data-ttu-id="5a3f5-119">此命令将取消阻止 PowerShellTips.chm 文件。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-119">This command unblocks the PowerShellTips.chm file.</span></span>

```
PS C:\> Unblock-File -Path C:\Users\User01\Documents\Downloads\PowerShellTips.chm
```

### <span data-ttu-id="5a3f5-120">示例 2：取消阻止多个文件</span><span class="sxs-lookup"><span data-stu-id="5a3f5-120">Example 2: Unblock multiple files</span></span>

<span data-ttu-id="5a3f5-121">此命令取消阻止 `C:\Downloads` 目录中其名称包含 "PowerShell" 的所有文件。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-121">This command unblocks all of the files in the `C:\Downloads` directory whose names include "PowerShell".</span></span> <span data-ttu-id="5a3f5-122">在你已验证所有文件都安全之前，不要运行类似此命令的命令。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-122">Do not run a command like this one until you have verified that all files are safe.</span></span>

```
PS C:\> dir C:\Downloads\*PowerShell* | Unblock-File
```

### <span data-ttu-id="5a3f5-123">示例 3：查找和取消阻止脚本</span><span class="sxs-lookup"><span data-stu-id="5a3f5-123">Example 3: Find and unblock scripts</span></span>

<span data-ttu-id="5a3f5-124">此命令显示了如何查找和取消阻止 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-124">This command shows how to find and unblock PowerShell scripts.</span></span>

<span data-ttu-id="5a3f5-125">第一个命令使用 *get* Cmdlet 的 **Stream** 参数获取带有区域的文件。标识符流。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-125">The first command uses the **Stream** parameter of the *Get-Item* cmdlet get files with the Zone.Identifier stream.</span></span>

<span data-ttu-id="5a3f5-126">第二个命令显示在 PowerShell 会话中运行已阻止的脚本时所发生的情况，其中执行策略为 **RemoteSigned** 。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-126">The second command shows what happens when you run a blocked script in a PowerShell session in which the execution policy is **RemoteSigned**.</span></span> <span data-ttu-id="5a3f5-127">RemoteSigned 策略阻止你运行从 Internet 下载的脚本，除非它们已进行数字签名。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-127">The RemoteSigned policy prevents you from running scripts that are downloaded from the Internet unless they are digitally signed.</span></span>

<span data-ttu-id="5a3f5-128">第三个命令使用 `Unblock-File` cmdlet 取消阻止脚本，以便它可以在会话中运行。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-128">The third command uses the `Unblock-File` cmdlet to unblock the script so it can run in the session.</span></span>

```
PS C:\> Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue
   FileName: C:\ps-test\Start-ActivityTracker.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

PS C:\> C:\ps-test\Start-ActivityTracker.ps1
c:\ps-test\Start-ActivityTracker.ps1 : File c:\ps-test\Start-ActivityTracker.ps1 cannot
be loaded. The file c:\ps-test\Start-ActivityTracker.ps1 is not digitally signed. The script
will not execute on the system. For more information, see about_Execution_Policies.

At line:1 char:1
+ c:\ps-test\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess

PS C:\> Get-Item C:\ps-test\Start-ActivityTracker.ps1 | Unblock-File
```

## <span data-ttu-id="5a3f5-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5a3f5-129">PARAMETERS</span></span>

### <span data-ttu-id="5a3f5-130">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="5a3f5-130">-LiteralPath</span></span>

<span data-ttu-id="5a3f5-131">指定要取消阻止的文件。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-131">Specifies the files to unblock.</span></span> <span data-ttu-id="5a3f5-132">与 **Path** 不同， **LiteralPath** 参数的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-132">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="5a3f5-133">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-133">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="5a3f5-134">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-134">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="5a3f5-135">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-135">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5a3f5-136">-Path</span><span class="sxs-lookup"><span data-stu-id="5a3f5-136">-Path</span></span>

<span data-ttu-id="5a3f5-137">指定要取消阻止的文件。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-137">Specifies the files to unblock.</span></span> <span data-ttu-id="5a3f5-138">支持使用通配符。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-138">Wildcard characters are supported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="5a3f5-139">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5a3f5-139">-Confirm</span></span>

<span data-ttu-id="5a3f5-140">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-140">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5a3f5-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5a3f5-141">-WhatIf</span></span>

<span data-ttu-id="5a3f5-142">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-142">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="5a3f5-143">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-143">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5a3f5-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5a3f5-144">CommonParameters</span></span>

<span data-ttu-id="5a3f5-145">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5a3f5-146">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5a3f5-147">输入</span><span class="sxs-lookup"><span data-stu-id="5a3f5-147">INPUTS</span></span>

### <span data-ttu-id="5a3f5-148">System.String</span><span class="sxs-lookup"><span data-stu-id="5a3f5-148">System.String</span></span>

<span data-ttu-id="5a3f5-149">可以通过管道将文件路径传递给 `Unblock-File` 。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-149">You can pipe a file path to `Unblock-File`.</span></span>

## <span data-ttu-id="5a3f5-150">输出</span><span class="sxs-lookup"><span data-stu-id="5a3f5-150">OUTPUTS</span></span>

### <span data-ttu-id="5a3f5-151">None</span><span class="sxs-lookup"><span data-stu-id="5a3f5-151">None</span></span>

<span data-ttu-id="5a3f5-152">此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-152">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5a3f5-153">注释</span><span class="sxs-lookup"><span data-stu-id="5a3f5-153">NOTES</span></span>

- <span data-ttu-id="5a3f5-154">此 `Unblock-File` cmdlet 仅适用于文件系统驱动器。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-154">The `Unblock-File` cmdlet works only in file system drives.</span></span>
- <span data-ttu-id="5a3f5-155">`Unblock-File`执行与文件资源管理器的 " **属性** " 对话框中的 " **解除阻止** " 按钮相同的操作。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-155">`Unblock-File` performs the same operation as the **Unblock** button on the **Properties** dialog box in File Explorer.</span></span>
- <span data-ttu-id="5a3f5-156">如果在 `Unblock-File` 未被阻止的文件上使用 cmdlet，则该命令对未阻止的文件无效，并且该 cmdlet 不会生成错误。</span><span class="sxs-lookup"><span data-stu-id="5a3f5-156">If you use the `Unblock-File` cmdlet on a file that is not blocked, the command has no effect on the unblocked file and the cmdlet does not generate errors.</span></span>

## <span data-ttu-id="5a3f5-157">相关链接</span><span class="sxs-lookup"><span data-stu-id="5a3f5-157">RELATED LINKS</span></span>

[<span data-ttu-id="5a3f5-158">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="5a3f5-158">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="5a3f5-159">Get-Item</span><span class="sxs-lookup"><span data-stu-id="5a3f5-159">Get-Item</span></span>](../Microsoft.PowerShell.Management/Get-Item.md)

[<span data-ttu-id="5a3f5-160">Out-File</span><span class="sxs-lookup"><span data-stu-id="5a3f5-160">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="5a3f5-161">FileSystem 提供程序</span><span class="sxs-lookup"><span data-stu-id="5a3f5-161">FileSystem Provider</span></span>](../Microsoft.PowerShell.Core/about/about_FileSystem_Provider.md)
