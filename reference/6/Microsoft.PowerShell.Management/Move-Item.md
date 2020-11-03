---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-item?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-Item
ms.openlocfilehash: 462b90535e33f1822d346dde2b2b1ecb9a790d84
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93197727"
---
# <span data-ttu-id="eb88e-103">Move-Item</span><span class="sxs-lookup"><span data-stu-id="eb88e-103">Move-Item</span></span>

## <span data-ttu-id="eb88e-104">摘要</span><span class="sxs-lookup"><span data-stu-id="eb88e-104">SYNOPSIS</span></span>
<span data-ttu-id="eb88e-105">将项从一个位置移动到另一个位置。</span><span class="sxs-lookup"><span data-stu-id="eb88e-105">Moves an item from one location to another.</span></span>

## <span data-ttu-id="eb88e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="eb88e-106">SYNTAX</span></span>

### <span data-ttu-id="eb88e-107">Path（默认值）</span><span class="sxs-lookup"><span data-stu-id="eb88e-107">Path (Default)</span></span>

```
Move-Item [-Path] <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="eb88e-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="eb88e-108">LiteralPath</span></span>

```
Move-Item -LiteralPath <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="eb88e-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="eb88e-109">DESCRIPTION</span></span>

<span data-ttu-id="eb88e-110">`Move-Item`Cmdlet 将项（包括其属性、内容和子项）从一个位置移动到另一个位置。</span><span class="sxs-lookup"><span data-stu-id="eb88e-110">The `Move-Item` cmdlet moves an item, including its properties, contents, and child items, from one location to another location.</span></span> <span data-ttu-id="eb88e-111">但这些位置必须由同一提供程序支持。</span><span class="sxs-lookup"><span data-stu-id="eb88e-111">The locations must be supported by the same provider.</span></span>
<span data-ttu-id="eb88e-112">例如，它可以将文件或子目录从一个目录移动到另一个目录，或将注册表子项从一个项移动到另一个项。</span><span class="sxs-lookup"><span data-stu-id="eb88e-112">For example, it can move a file or subdirectory from one directory to another or move a registry subkey from one key to another.</span></span>
<span data-ttu-id="eb88e-113">在你移动某个项时，该属性将被添加到新位置，并从其原来的位置删除。</span><span class="sxs-lookup"><span data-stu-id="eb88e-113">When you move an item, it is added to the new location and deleted from its original location.</span></span>

## <span data-ttu-id="eb88e-114">示例</span><span class="sxs-lookup"><span data-stu-id="eb88e-114">EXAMPLES</span></span>

### <span data-ttu-id="eb88e-115">示例1：将文件移到另一个目录并将其重命名</span><span class="sxs-lookup"><span data-stu-id="eb88e-115">Example 1: Move a file to another directory and rename it</span></span>

<span data-ttu-id="eb88e-116">此命令将 `Test.txt` 文件从驱动器移动 `C:` 到 `E:\Temp` 目录，并将其重命名 `test.txt` 为 `tst.txt` 。</span><span class="sxs-lookup"><span data-stu-id="eb88e-116">This command moves the `Test.txt` file from the `C:` drive to the `E:\Temp` directory and renames it from `test.txt` to `tst.txt`.</span></span>

```powershell
Move-Item -Path C:\test.txt -Destination E:\Temp\tst.txt
```

### <span data-ttu-id="eb88e-117">示例2：将目录及其内容移到另一个目录</span><span class="sxs-lookup"><span data-stu-id="eb88e-117">Example 2: Move a directory and its contents to another directory</span></span>

<span data-ttu-id="eb88e-118">此命令将 `C:\Temp` 目录及其内容移动到 `C:\Logs` 目录中。</span><span class="sxs-lookup"><span data-stu-id="eb88e-118">This command moves the `C:\Temp` directory and its contents to the `C:\Logs` directory.</span></span>
<span data-ttu-id="eb88e-119">"Temp" 目录及其所有子目录和文件都显示在 "日志" 目录中。</span><span class="sxs-lookup"><span data-stu-id="eb88e-119">The "Temp" directory, and all of its subdirectories and files, then appear in the "Logs" directory.</span></span>

```powershell
Move-Item -Path C:\Temp -Destination C:\Logs
```

### <span data-ttu-id="eb88e-120">示例3：将指定扩展的所有文件从当前目录移动到另一个目录</span><span class="sxs-lookup"><span data-stu-id="eb88e-120">Example 3: Move all files of a specified extension from the current directory to another directory</span></span>

<span data-ttu-id="eb88e-121">此命令会将当前目录中的所有 () 的文本文件移动 `*.txt` (由点 (`.`) # A5 表示为 `C:\Logs` 目录。</span><span class="sxs-lookup"><span data-stu-id="eb88e-121">This command moves all of the text files (`*.txt`) in the current directory (represented by a dot (`.`)) to the `C:\Logs` directory.</span></span>

```powershell
Move-Item -Path .\*.txt -Destination C:\Logs
```

### <span data-ttu-id="eb88e-122">示例4：以递归方式将指定扩展名的所有文件从当前目录移动到另一个目录</span><span class="sxs-lookup"><span data-stu-id="eb88e-122">Example 4: Recursively move all files of a specified extension from the current directory to another directory</span></span>

<span data-ttu-id="eb88e-123">此命令将所有文本文件从当前目录和所有子目录递归地移动到 "C:\TextFiles" 目录。</span><span class="sxs-lookup"><span data-stu-id="eb88e-123">This command moves all of the text files from the current directory and all subdirectories, recursively, to the "C:\TextFiles" directory.</span></span>

```powershell
Get-ChildItem -Path ".\*.txt" -Recurse | Move-Item -Destination "C:\TextFiles"
```

<span data-ttu-id="eb88e-124">该命令使用 `Get-ChildItem` cmdlet 来获取当前目录中的所有子项目， (由 \[ \]) 及其子目录（其 *文件扩展名为 ".txt"）表示。它使用 recursive **Recurse** 参数将检索设置为 recursive，并使用 Include 参数将检索限制为 "* .txt" 文件。</span><span class="sxs-lookup"><span data-stu-id="eb88e-124">The command uses the `Get-ChildItem` cmdlet to get all of the child items in the current directory (represented by the dot \[.\]) and its subdirectories that have a " *.txt" file name extension. It uses the **Recurse** parameter to make the retrieval recursive and the Include parameter to limit the retrieval to "* .txt" files.</span></span>

<span data-ttu-id="eb88e-125">管道运算符 (`|`) 将此命令的结果发送到 `Move-Item` ，后者将文本文件移动到 "TextFiles" 目录。</span><span class="sxs-lookup"><span data-stu-id="eb88e-125">The pipeline operator (`|`) sends the results of this command to `Move-Item`, which moves the text files to the "TextFiles" directory.</span></span>

<span data-ttu-id="eb88e-126">如果要移动到 "C:\Textfiles" 的文件具有相同的名称，将 `Move-Item` 显示错误并继续，但它只会将一个具有每个名称的文件移动到 "C:\Textfiles"。</span><span class="sxs-lookup"><span data-stu-id="eb88e-126">If files that are to be moved to "C:\Textfiles" have the same name, `Move-Item` displays an error and continues, but it moves only one file with each name to "C:\Textfiles".</span></span>
<span data-ttu-id="eb88e-127">其他文件仍保留在其原始目录下。</span><span class="sxs-lookup"><span data-stu-id="eb88e-127">The other files remain in their original directories.</span></span>

<span data-ttu-id="eb88e-128">如果 "Textfiles" 目录 (或目标路径) 的任何其他元素不存在，则该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="eb88e-128">If the "Textfiles" directory (or any other element of the destination path) does not exist, the command fails.</span></span>
<span data-ttu-id="eb88e-129">不会为你创建缺少的目录，即使使用 **Force** 参数也是如此。</span><span class="sxs-lookup"><span data-stu-id="eb88e-129">The missing directory is not created for you, even if you use the **Force** parameter.</span></span>
<span data-ttu-id="eb88e-130">`Move-Item` 将第一项移到名为 "Textfiles" 的文件中，然后显示一个错误，指出该文件已存在。</span><span class="sxs-lookup"><span data-stu-id="eb88e-130">`Move-Item` moves the first item to a file called "Textfiles" and then displays an error explaining that the file already exists.</span></span>

<span data-ttu-id="eb88e-131">而且，默认情况下 `Get-ChildItem` 不会移动隐藏的文件。</span><span class="sxs-lookup"><span data-stu-id="eb88e-131">Also, by default, `Get-ChildItem` does not move hidden files.</span></span>
<span data-ttu-id="eb88e-132">若要移动隐藏的文件，请使用 **Force** 参数 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="eb88e-132">To move hidden files, use the **Force** parameter with `Get-ChildItem`.</span></span>

> [!NOTE]
> <span data-ttu-id="eb88e-133">在 Windows PowerShell 2.0 中，使用 cmdlet 的 **递归** 参数时 `Get-ChildItem` ， **Path** 参数的值必须是一个容器。</span><span class="sxs-lookup"><span data-stu-id="eb88e-133">In Windows PowerShell 2.0, when using the **Recurse** parameter of the `Get-ChildItem` cmdlet, the value of the **Path** parameter must be a container.</span></span>
> <span data-ttu-id="eb88e-134">使用 **Include** 参数指定 .txt 文件扩展名筛选器 (`Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles`)。</span><span class="sxs-lookup"><span data-stu-id="eb88e-134">Use the **Include** parameter to specify the .txt file name extension filter (`Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles`).</span></span>

### <span data-ttu-id="eb88e-135">示例5：将注册表项和值移动到另一个键</span><span class="sxs-lookup"><span data-stu-id="eb88e-135">Example 5: Move registry keys and values to another key</span></span>

<span data-ttu-id="eb88e-136">此命令将中 "MyCompany" 注册表项中的注册表项和值移动 `HKLM\Software` 到 "MyNewCompany" 键。</span><span class="sxs-lookup"><span data-stu-id="eb88e-136">This command moves the registry keys and values within the "MyCompany" registry key in `HKLM\Software` to the "MyNewCompany" key.</span></span>
<span data-ttu-id="eb88e-137">通配符 (`*`) 指示应移动 "MyCompany" 键的内容，而不是键本身。</span><span class="sxs-lookup"><span data-stu-id="eb88e-137">The wildcard character (`*`) indicates that the contents of the "MyCompany" key should be moved, not the key itself.</span></span>
<span data-ttu-id="eb88e-138">在此命令中，省略了可选的 **Path** 和 **Destination** 参数名。</span><span class="sxs-lookup"><span data-stu-id="eb88e-138">In this command, the optional **Path** and **Destination** parameter names are omitted.</span></span>

```powershell
Move-Item "HKLM:\software\mycompany\*" "HKLM:\software\mynewcompany"
```

### <span data-ttu-id="eb88e-139">示例6：将目录及其内容移动到指定目录的子目录</span><span class="sxs-lookup"><span data-stu-id="eb88e-139">Example 6: Move a directory and its contents to a subdirectory of the specified directory</span></span>

<span data-ttu-id="eb88e-140">此命令会将 "日志 \[ 九月 \` 06 \] " 目录 (，并将其内容) 到 "日志 \[ 2006 \] " 目录中。</span><span class="sxs-lookup"><span data-stu-id="eb88e-140">This command moves the "Logs\[Sept\`06\]" directory (and its contents) into the "Logs\[2006\]" directory.</span></span>

```powershell
Move-Item -LiteralPath 'Logs[Sept`06]' -Destination 'Logs[2006]'
```

<span data-ttu-id="eb88e-141">使用 **LiteralPath** 参数而不是 **Path** ，因为原始目录名称包含左方括号和右方括号字符 ( " \[ " 和 " \] " ) 。</span><span class="sxs-lookup"><span data-stu-id="eb88e-141">The **LiteralPath** parameter is used instead of **Path** , because the original directory name includes left bracket and right bracket characters ("\[" and "\]").</span></span>
<span data-ttu-id="eb88e-142">也可将路径括在单引号 (' ') 中，以便不会曲解倒引号 (\`)。</span><span class="sxs-lookup"><span data-stu-id="eb88e-142">The path is also enclosed in single quotation marks (' '), so that the backtick symbol (\`) is not misinterpreted.</span></span>

<span data-ttu-id="eb88e-143">**Destination** 参数不需要文本路径，因为目标变量也必须括在单引号中，因为它包含可能被误解的方括号。</span><span class="sxs-lookup"><span data-stu-id="eb88e-143">The **Destination** parameter does not require a literal path, because the Destination variable also must be enclosed in single quotation marks, because it includes brackets that can be misinterpreted.</span></span>

## <span data-ttu-id="eb88e-144">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="eb88e-144">PARAMETERS</span></span>

### <span data-ttu-id="eb88e-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="eb88e-145">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="eb88e-146">随 PowerShell 一起安装的任何提供程序都不支持此参数。</span><span class="sxs-lookup"><span data-stu-id="eb88e-146">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="eb88e-147">若要在运行此 cmdlet 时模拟其他用户或提升凭据，请使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="eb88e-147">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="eb88e-148">-Destination</span><span class="sxs-lookup"><span data-stu-id="eb88e-148">-Destination</span></span>

<span data-ttu-id="eb88e-149">指定指向要移动其中的项的位置的路径。</span><span class="sxs-lookup"><span data-stu-id="eb88e-149">Specifies the path to the location where the items are being moved.</span></span>
<span data-ttu-id="eb88e-150">默认为当前目录。</span><span class="sxs-lookup"><span data-stu-id="eb88e-150">The default is the current directory.</span></span>
<span data-ttu-id="eb88e-151">允许使用通配符，但结果必须指定单个位置。</span><span class="sxs-lookup"><span data-stu-id="eb88e-151">Wildcards are permitted, but the result must specify a single location.</span></span>

<span data-ttu-id="eb88e-152">若要重命名要移动的项，请在 **Destination** 参数的值中指定新名称。</span><span class="sxs-lookup"><span data-stu-id="eb88e-152">To rename the item being moved, specify a new name in the value of the **Destination** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="eb88e-153">-Exclude</span><span class="sxs-lookup"><span data-stu-id="eb88e-153">-Exclude</span></span>

<span data-ttu-id="eb88e-154">指定为字符串数组，此 cmdlet 在操作中排除的项。</span><span class="sxs-lookup"><span data-stu-id="eb88e-154">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="eb88e-155">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="eb88e-155">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="eb88e-156">请输入路径元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="eb88e-156">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="eb88e-157">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="eb88e-157">Wildcard characters are permitted.</span></span> <span data-ttu-id="eb88e-158">仅 **Exclude** 当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Exclude 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="eb88e-158">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="eb88e-159">-Filter</span><span class="sxs-lookup"><span data-stu-id="eb88e-159">-Filter</span></span>

<span data-ttu-id="eb88e-160">指定用于限定 **路径** 参数的筛选器。</span><span class="sxs-lookup"><span data-stu-id="eb88e-160">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="eb88e-161">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供程序是唯一一种支持使用筛选器的已安装 PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="eb88e-161">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="eb88e-162">可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **文件系统** 筛选语言的语法。</span><span class="sxs-lookup"><span data-stu-id="eb88e-162">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="eb88e-163">筛选器比其他参数更有效，因为提供程序在 cmdlet 获取对象时应用筛选器，而不是在检索对象后再对其进行筛选。</span><span class="sxs-lookup"><span data-stu-id="eb88e-163">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="eb88e-164">-Force</span><span class="sxs-lookup"><span data-stu-id="eb88e-164">-Force</span></span>

<span data-ttu-id="eb88e-165">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="eb88e-165">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="eb88e-166">不同提供程序有不同的实现。</span><span class="sxs-lookup"><span data-stu-id="eb88e-166">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="eb88e-167">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="eb88e-167">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="eb88e-168">-Include</span><span class="sxs-lookup"><span data-stu-id="eb88e-168">-Include</span></span>

<span data-ttu-id="eb88e-169">指定此 cmdlet 将在操作中包含的一个项或多个项（作为一个字符串数组）。</span><span class="sxs-lookup"><span data-stu-id="eb88e-169">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="eb88e-170">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="eb88e-170">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="eb88e-171">请输入路径元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="eb88e-171">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="eb88e-172">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="eb88e-172">Wildcard characters are permitted.</span></span> <span data-ttu-id="eb88e-173">仅 **Include** 当命令包括项的内容时（例如 `C:\Windows\*` ，其中的通配符指定目录的内容），Include 参数才有效 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="eb88e-173">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="eb88e-174">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="eb88e-174">-LiteralPath</span></span>

<span data-ttu-id="eb88e-175">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="eb88e-175">Specifies a path to one or more locations.</span></span> <span data-ttu-id="eb88e-176">**LiteralPath** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="eb88e-176">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="eb88e-177">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="eb88e-177">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="eb88e-178">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="eb88e-178">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="eb88e-179">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="eb88e-179">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="eb88e-180">有关详细信息，请参阅 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="eb88e-180">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="eb88e-181">-PassThru</span><span class="sxs-lookup"><span data-stu-id="eb88e-181">-PassThru</span></span>

<span data-ttu-id="eb88e-182">返回一个代表你所处理的项目的对象。</span><span class="sxs-lookup"><span data-stu-id="eb88e-182">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="eb88e-183">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="eb88e-183">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="eb88e-184">-Path</span><span class="sxs-lookup"><span data-stu-id="eb88e-184">-Path</span></span>

<span data-ttu-id="eb88e-185">指定指向项的当前位置的路径。</span><span class="sxs-lookup"><span data-stu-id="eb88e-185">Specifies the path to the current location of the items.</span></span>
<span data-ttu-id="eb88e-186">默认为当前目录。</span><span class="sxs-lookup"><span data-stu-id="eb88e-186">The default is the current directory.</span></span>
<span data-ttu-id="eb88e-187">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="eb88e-187">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="eb88e-188">-Confirm</span><span class="sxs-lookup"><span data-stu-id="eb88e-188">-Confirm</span></span>

<span data-ttu-id="eb88e-189">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="eb88e-189">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="eb88e-190">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="eb88e-190">-WhatIf</span></span>

<span data-ttu-id="eb88e-191">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="eb88e-191">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="eb88e-192">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="eb88e-192">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="eb88e-193">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="eb88e-193">CommonParameters</span></span>

<span data-ttu-id="eb88e-194">此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="eb88e-194">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="eb88e-195">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="eb88e-195">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="eb88e-196">输入</span><span class="sxs-lookup"><span data-stu-id="eb88e-196">INPUTS</span></span>

### <span data-ttu-id="eb88e-197">System.String</span><span class="sxs-lookup"><span data-stu-id="eb88e-197">System.String</span></span>

<span data-ttu-id="eb88e-198">可以通过管道将包含路径的字符串传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="eb88e-198">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="eb88e-199">输出</span><span class="sxs-lookup"><span data-stu-id="eb88e-199">OUTPUTS</span></span>

### <span data-ttu-id="eb88e-200">无或表示已移动项的对象</span><span class="sxs-lookup"><span data-stu-id="eb88e-200">None or an object representing the moved item</span></span>

<span data-ttu-id="eb88e-201">当使用 *PassThru* 参数时，此 cmdlet 将生成一个表示已移动项的对象。</span><span class="sxs-lookup"><span data-stu-id="eb88e-201">When you use the *PassThru* parameter, this cmdlet generates an object representing the moved item.</span></span>
<span data-ttu-id="eb88e-202">否则，此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="eb88e-202">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="eb88e-203">注释</span><span class="sxs-lookup"><span data-stu-id="eb88e-203">NOTES</span></span>

- <span data-ttu-id="eb88e-204">此 cmdlet 将在同一提供程序支持的驱动器之间移动文件，但它只在同一驱动器内移动目录。</span><span class="sxs-lookup"><span data-stu-id="eb88e-204">This cmdlet will move files between drives that are supported by the same provider, but it will move directories only within the same drive.</span></span>
- <span data-ttu-id="eb88e-205">因为 `Move-Item` 命令移动项的属性、内容和子项，所以默认情况下，所有移动都是递归的。</span><span class="sxs-lookup"><span data-stu-id="eb88e-205">Because a `Move-Item` command moves the properties, contents, and child items of an item, all moves are recursive by default.</span></span>
- <span data-ttu-id="eb88e-206">此 cmdlet 用于处理由任何提供程序公开的数据。</span><span class="sxs-lookup"><span data-stu-id="eb88e-206">This cmdlet is designed to work with the data exposed by any provider.</span></span>
  <span data-ttu-id="eb88e-207">若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="eb88e-207">To list the providers available in your session, type `Get-PSProvider`.</span></span>
  <span data-ttu-id="eb88e-208">有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="eb88e-208">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="eb88e-209">相关链接</span><span class="sxs-lookup"><span data-stu-id="eb88e-209">RELATED LINKS</span></span>

[<span data-ttu-id="eb88e-210">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="eb88e-210">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="eb88e-211">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="eb88e-211">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="eb88e-212">Get-Item</span><span class="sxs-lookup"><span data-stu-id="eb88e-212">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="eb88e-213">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="eb88e-213">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="eb88e-214">New-Item</span><span class="sxs-lookup"><span data-stu-id="eb88e-214">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="eb88e-215">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="eb88e-215">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="eb88e-216">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="eb88e-216">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="eb88e-217">Set-Item</span><span class="sxs-lookup"><span data-stu-id="eb88e-217">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="eb88e-218">about_Providers</span><span class="sxs-lookup"><span data-stu-id="eb88e-218">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
