---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-acl?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Acl
ms.openlocfilehash: 0f5757d7e9fb2615149fd08473685491bfccada7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93198652"
---
# <span data-ttu-id="1aaec-103">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="1aaec-103">Set-Acl</span></span>

## <span data-ttu-id="1aaec-104">摘要</span><span class="sxs-lookup"><span data-stu-id="1aaec-104">SYNOPSIS</span></span>
<span data-ttu-id="1aaec-105">更改指定项（如文件或注册表项）的安全描述符。</span><span class="sxs-lookup"><span data-stu-id="1aaec-105">Changes the security descriptor of a specified item, such as a file or a registry key.</span></span>

## <span data-ttu-id="1aaec-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1aaec-106">SYNTAX</span></span>

### <span data-ttu-id="1aaec-107">ByPath（默认值）</span><span class="sxs-lookup"><span data-stu-id="1aaec-107">ByPath (Default)</span></span>

```
Set-Acl [-Path] <String[]> [-AclObject] <Object> [-ClearCentralAccessPolicy] [-Passthru] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1aaec-108">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="1aaec-108">ByInputObject</span></span>

```
Set-Acl [-InputObject] <PSObject> [-AclObject] <Object> [-Passthru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1aaec-109">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="1aaec-109">ByLiteralPath</span></span>

```
Set-Acl -LiteralPath <String[]> [-AclObject] <Object> [-ClearCentralAccessPolicy] [-Passthru]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1aaec-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1aaec-110">DESCRIPTION</span></span>

<span data-ttu-id="1aaec-111">`Set-Acl`Cmdlet 更改指定项（如文件或注册表项）的安全描述符，以与你提供的安全描述符中的值相匹配。</span><span class="sxs-lookup"><span data-stu-id="1aaec-111">The `Set-Acl` cmdlet changes the security descriptor of a specified item, such as a file or a registry key, to match the values in a security descriptor that you supply.</span></span>

<span data-ttu-id="1aaec-112">若要使用 `Set-Acl` ，请使用 **Path** 或 **InputObject** 参数来识别要更改其安全描述符的项。</span><span class="sxs-lookup"><span data-stu-id="1aaec-112">To use `Set-Acl`, use the **Path** or **InputObject** parameter to identify the item whose security descriptor you want to change.</span></span> <span data-ttu-id="1aaec-113">然后，使用 **AclObject** 或 **SecurityDescriptor** 参数来提供具有要应用的值的安全描述符。</span><span class="sxs-lookup"><span data-stu-id="1aaec-113">Then, use the **AclObject** or **SecurityDescriptor** parameters to supply a security descriptor that has the values you want to apply.</span></span> <span data-ttu-id="1aaec-114">`Set-Acl` 应用提供的安全描述符。</span><span class="sxs-lookup"><span data-stu-id="1aaec-114">`Set-Acl` applies the security descriptor that is supplied.</span></span> <span data-ttu-id="1aaec-115">它将 **AclObject** 参数的值用作模型，并更改项的安全描述符中的值，以与 **AclObject** 参数中的值相匹配。</span><span class="sxs-lookup"><span data-stu-id="1aaec-115">It uses the value of the **AclObject** parameter as a model and changes the values in the item's security descriptor to match the values in the **AclObject** parameter.</span></span>

## <span data-ttu-id="1aaec-116">示例</span><span class="sxs-lookup"><span data-stu-id="1aaec-116">EXAMPLES</span></span>

### <span data-ttu-id="1aaec-117">示例1：将安全描述符从一个文件复制到另一个文件</span><span class="sxs-lookup"><span data-stu-id="1aaec-117">Example 1: Copy a security descriptor from one file to another</span></span>

```powershell
$DogACL = Get-Acl -Path "C:\Dog.txt"
Set-Acl -Path "C:\Cat.txt" -AclObject $DogACL
```

<span data-ttu-id="1aaec-118">这些命令将值从 Dog.txt 文件的安全描述符复制到 Cat.txt 文件的安全描述符。</span><span class="sxs-lookup"><span data-stu-id="1aaec-118">These commands copy the values from the security descriptor of the Dog.txt file to the security descriptor of the Cat.txt file.</span></span> <span data-ttu-id="1aaec-119">完成这些命令后，Dog.txt 文件和 Cat.txt 文件的安全描述符将完全相同。</span><span class="sxs-lookup"><span data-stu-id="1aaec-119">When the commands complete, the security descriptors of the Dog.txt and Cat.txt files are identical.</span></span>

<span data-ttu-id="1aaec-120">第一个命令使用 `Get-Acl` cmdlet 来获取 Dog.txt 文件的安全描述符。</span><span class="sxs-lookup"><span data-stu-id="1aaec-120">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span>
<span data-ttu-id="1aaec-121">赋值运算符 (`=`) 将安全描述符存储在 $DogACL 变量的值中。</span><span class="sxs-lookup"><span data-stu-id="1aaec-121">The assignment operator (`=`) stores the security descriptor in the value of the $DogACL variable.</span></span>

<span data-ttu-id="1aaec-122">第二个命令使用将 `Set-Acl` Cat.txt 的 ACL 中的值更改为中的值 `$DogACL` 。</span><span class="sxs-lookup"><span data-stu-id="1aaec-122">The second command uses `Set-Acl` to change the values in the ACL of Cat.txt to the values in `$DogACL`.</span></span>

<span data-ttu-id="1aaec-123">**Path** 参数的值是 Cat.txt 文件的路径。</span><span class="sxs-lookup"><span data-stu-id="1aaec-123">The value of the **Path** parameter is the path to the Cat.txt file.</span></span> <span data-ttu-id="1aaec-124">**AclObject** 参数的值是模型 acl，在此示例中，是在变量中保存的 Dog.txt 的 acl `$DogACL` 。</span><span class="sxs-lookup"><span data-stu-id="1aaec-124">The value of the **AclObject** parameter is the model ACL, in this case, the ACL of Dog.txt as saved in the `$DogACL` variable.</span></span>

### <span data-ttu-id="1aaec-125">示例2：使用管道运算符传递描述符</span><span class="sxs-lookup"><span data-stu-id="1aaec-125">Example 2: Use the pipeline operator to pass a descriptor</span></span>

```powershell
Get-Acl -Path "C:\Dog.txt" | Set-Acl -Path "C:\Cat.txt"
```

<span data-ttu-id="1aaec-126">此命令与上一示例中的命令几乎相同，不同之处在于它使用管道运算符 (`|`) 将安全描述符从 `Get-Acl` 命令发送到 `Set-Acl` 命令。</span><span class="sxs-lookup"><span data-stu-id="1aaec-126">This command is almost the same as the command in the previous example, except that it uses a pipeline operator (`|`) to send the security descriptor from a `Get-Acl` command to a `Set-Acl` command.</span></span>

<span data-ttu-id="1aaec-127">第一个命令使用 `Get-Acl` cmdlet 来获取 Dog.txt 文件的安全描述符。</span><span class="sxs-lookup"><span data-stu-id="1aaec-127">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span> <span data-ttu-id="1aaec-128">管道运算符 (`|`) 将表示 Dog.txt 安全描述符的对象传递给 `Set-Acl` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1aaec-128">The pipeline operator (`|`) passes an object that represents the Dog.txt security descriptor to the `Set-Acl` cmdlet.</span></span>

<span data-ttu-id="1aaec-129">第二个命令使用将 `Set-Acl` Dog.txt 的安全描述符应用到 Cat.txt。</span><span class="sxs-lookup"><span data-stu-id="1aaec-129">The second command uses `Set-Acl` to apply the security descriptor of Dog.txt to Cat.txt.</span></span>
<span data-ttu-id="1aaec-130">完成该命令后，Dog.txt 和 Cat.txt 文件的 ACL 将完全相同。</span><span class="sxs-lookup"><span data-stu-id="1aaec-130">When the command completes, the ACLs of the Dog.txt and Cat.txt files are identical.</span></span>

### <span data-ttu-id="1aaec-131">示例3：将安全描述符应用于多个文件</span><span class="sxs-lookup"><span data-stu-id="1aaec-131">Example 3: Apply a security descriptor to multiple files</span></span>

```powershell
$NewAcl = Get-Acl File0.txt
Get-ChildItem -Path "C:\temp" -Recurse -Include "*.txt" -Force | Set-Acl -AclObject $NewAcl
```

<span data-ttu-id="1aaec-132">这些命令将 File0.txt 文件中的安全描述符应用于 `C:\Temp` 目录及其所有子目录中的所有文本文件。</span><span class="sxs-lookup"><span data-stu-id="1aaec-132">These commands apply the security descriptors in the File0.txt file to all text files in the `C:\Temp` directory and all of its subdirectories.</span></span>

<span data-ttu-id="1aaec-133">第一个命令将获取当前目录中 File0.txt 文件的安全描述符，并使用赋值运算符 () 将 `=` 其存储在 `$NewACL` 变量中。</span><span class="sxs-lookup"><span data-stu-id="1aaec-133">The first command gets the security descriptor of the File0.txt file in the current directory and uses the assignment operator (`=`) to store it in the `$NewACL` variable.</span></span>

<span data-ttu-id="1aaec-134">管道中的第一个命令使用 Get-ChildItem cmdlet 获取目录中的所有文本文件 `C:\Temp` 。</span><span class="sxs-lookup"><span data-stu-id="1aaec-134">The first command in the pipeline uses the Get-ChildItem cmdlet to get all of the text files in the `C:\Temp` directory.</span></span> <span data-ttu-id="1aaec-135">**递归** 参数将该命令扩展到的所有子目录 `C:\temp` 。</span><span class="sxs-lookup"><span data-stu-id="1aaec-135">The **Recurse** parameter extends the command to all subdirectories of `C:\temp`.</span></span> <span data-ttu-id="1aaec-136">**Include** 参数将检索到的文件限制为文件扩展名为的文件 `.txt` 。</span><span class="sxs-lookup"><span data-stu-id="1aaec-136">The **Include** parameter limits the files retrieved to those with the `.txt` file name extension.</span></span> <span data-ttu-id="1aaec-137">**Force** 参数将获取本来会被排除的隐藏文件。</span><span class="sxs-lookup"><span data-stu-id="1aaec-137">The **Force** parameter gets hidden files, which would otherwise be excluded.</span></span> <span data-ttu-id="1aaec-138"> (不能使用 `c:\temp\*.txt` ，因为 **递归** 参数适用于目录而非文件。 ) </span><span class="sxs-lookup"><span data-stu-id="1aaec-138">(You cannot use `c:\temp\*.txt`, because the **Recurse** parameter works on directories, not on files.)</span></span>

<span data-ttu-id="1aaec-139">管道运算符 (`|`) 将表示检索到的文件的对象发送到 `Set-Acl` cmdlet，这会将 **AclObject** 参数中的安全描述符应用到管道中的所有文件。</span><span class="sxs-lookup"><span data-stu-id="1aaec-139">The pipeline operator (`|`) sends the objects representing the retrieved files to the `Set-Acl` cmdlet, which applies the security descriptor in the **AclObject** parameter to all of the files in the pipeline.</span></span>

<span data-ttu-id="1aaec-140">在实践中，最好将 **WhatIf** 参数与 `Set-Acl` 可能影响多个项的所有命令一起使用。</span><span class="sxs-lookup"><span data-stu-id="1aaec-140">In practice, it is best to use the **WhatIf** parameter with all `Set-Acl` commands that can affect more than one item.</span></span> <span data-ttu-id="1aaec-141">在这种情况下，管道中的第二个命令将为 `Set-Acl -AclObject $NewAcl -WhatIf` 。</span><span class="sxs-lookup"><span data-stu-id="1aaec-141">In this case, the second command in the pipeline would be `Set-Acl -AclObject $NewAcl -WhatIf`.</span></span> <span data-ttu-id="1aaec-142">此命令将列出会受该命令影响的文件。</span><span class="sxs-lookup"><span data-stu-id="1aaec-142">This command lists the files that would be affected by the command.</span></span> <span data-ttu-id="1aaec-143">查看结果后，可以在不带 **WhatIf** 参数的情况下再次运行该命令。</span><span class="sxs-lookup"><span data-stu-id="1aaec-143">After reviewing the result, you can run the command again without the **WhatIf** parameter.</span></span>

### <span data-ttu-id="1aaec-144">示例4：禁用继承并保留继承的访问规则</span><span class="sxs-lookup"><span data-stu-id="1aaec-144">Example 4: Disable inheritance and preserve inherited access rules</span></span>

```powershell
$NewAcl = Get-Acl -Path "C:\Pets\Dog.txt"
$isProtected = $true
$preserveInheritance = $true
$NewAcl.SetAccessRuleProtection($isProtected, $preserveInheritance)
Set-Acl -Path "C:\Pets\Dog.txt" -AclObject $NewAcl
```

<span data-ttu-id="1aaec-145">这些命令将禁止从父文件夹进行访问继承，同时仍然保留现有的继承访问规则。</span><span class="sxs-lookup"><span data-stu-id="1aaec-145">These commands is will disable access inheritance from parent folders, while still preserving the existing inherited access rules.</span></span>

<span data-ttu-id="1aaec-146">第一个命令使用 `Get-Acl` cmdlet 来获取 Dog.txt 文件的安全描述符。</span><span class="sxs-lookup"><span data-stu-id="1aaec-146">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span>

<span data-ttu-id="1aaec-147">接下来，创建变量以将继承的访问规则转换为显式访问规则。</span><span class="sxs-lookup"><span data-stu-id="1aaec-147">Next, variables are created to convert the inherited access rules to explicit access rules.</span></span> <span data-ttu-id="1aaec-148">若要通过继承保护与此关联的访问规则，请将 `$isProtected` 变量设置为 `$true` 。若要允许继承，请将设置 `$isProtected` 为 `$false` 。</span><span class="sxs-lookup"><span data-stu-id="1aaec-148">To protect the access rules associated with this from inheritance, set the `$isProtected` variable to `$true`.to allow inheritance, set `$isProtected` to `$false`.</span></span> <span data-ttu-id="1aaec-149">有关详细信息，请参阅 [设置访问规则保护](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection)。</span><span class="sxs-lookup"><span data-stu-id="1aaec-149">For more information, see [set access rule protection](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection).</span></span>
<span data-ttu-id="1aaec-150">`$preserveInheritance`设置为 `$true` 以保留继承的访问规则的变量; 如果为 false，则删除继承的访问规则。</span><span class="sxs-lookup"><span data-stu-id="1aaec-150">The `$preserveInheritance` variable set to `$true` to preserve inherited access rules; false to remove inherited access rules.</span></span> <span data-ttu-id="1aaec-151">然后，使用 **SetAccessRuleProtection ( # B1** 方法更新访问规则保护。</span><span class="sxs-lookup"><span data-stu-id="1aaec-151">Then the access rule protection is updated using the **SetAccessRuleProtection()** method.</span></span>

<span data-ttu-id="1aaec-152">最后一个命令使用将 `Set-Acl` 的安全描述符应用到 Dog.txt。</span><span class="sxs-lookup"><span data-stu-id="1aaec-152">The last command uses `Set-Acl` to apply the security descriptor of to Dog.txt.</span></span> <span data-ttu-id="1aaec-153">命令完成后，从 "宠物" 文件夹继承的 Dog.txt 的 Acl 将直接应用到 Dog.txt，而添加到宠物的新访问策略不会更改对 Dog.txt 的访问权限。</span><span class="sxs-lookup"><span data-stu-id="1aaec-153">When the command completes, the ACLs of the Dog.txt that were inherited from the Pets folder will be applied directly to Dog.txt, and new access policies added to Pets will not change the access to Dog.txt.</span></span>

### <span data-ttu-id="1aaec-154">示例5：授予管理员对文件的完全控制权限</span><span class="sxs-lookup"><span data-stu-id="1aaec-154">Example 5: Grant Administrators Full Control of the file</span></span>

```powershell
$NewAcl = Get-Acl -Path "C:\Pets\Dog.txt"
# Set properties
$identity = "BUILTIN\Administrators"
$fileSystemRights = "FullControl"
$type = "Allow"
# Create new rule
$fileSystemAccessRuleArgumentList = $identity, $fileSystemRights, $type
$fileSystemAccessRule = New-Object -TypeName System.Security.AccessControl.FileSystemAccessRule -ArgumentList $fileSystemAccessRuleArgumentList
# Apply new rule
$NewAcl.SetAccessRule($fileSystemAccessRule)
Set-Acl -Path "C:\Pets\Dog.txt" -AclObject $NewAcl
```

<span data-ttu-id="1aaec-155">此命令将授予 **BUILTIN\Administrators** 组对 Dog.txt 文件的完全控制权限。</span><span class="sxs-lookup"><span data-stu-id="1aaec-155">This command will grant the **BUILTIN\Administrators** group Full control of the Dog.txt file.</span></span>

<span data-ttu-id="1aaec-156">第一个命令使用 `Get-Acl` cmdlet 来获取 Dog.txt 文件的安全描述符。</span><span class="sxs-lookup"><span data-stu-id="1aaec-156">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span>

<span data-ttu-id="1aaec-157">创建后一种变量，为 **BUILTIN\Administrators** 组授予对 Dog.txt 文件的完全控制权。</span><span class="sxs-lookup"><span data-stu-id="1aaec-157">Next variables are created to grant the **BUILTIN\Administrators** group full control of the Dog.txt file.</span></span> <span data-ttu-id="1aaec-158">`$identity`设置为[用户帐户](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor)名称的变量。</span><span class="sxs-lookup"><span data-stu-id="1aaec-158">The `$identity` variable set to the name of a [user account](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor).</span></span>
<span data-ttu-id="1aaec-159">`$fileSystemRights`将变量设置为 FullControl，可以是指定与访问规则关联的操作的类型的[FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights)值之一。</span><span class="sxs-lookup"><span data-stu-id="1aaec-159">The `$fileSystemRights` variable set to FullControl, and can be any one of the [FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights) values that specifies the type of operation associated with the access rule.</span></span> <span data-ttu-id="1aaec-160">`$type`设置为 "允许" 的变量指定是允许还是拒绝该操作。</span><span class="sxs-lookup"><span data-stu-id="1aaec-160">The `$type` variable set to "Allow" to specifies whether to allow or deny the operation.</span></span> <span data-ttu-id="1aaec-161">`$fileSystemAccessRuleArgumentList`变量是在生成新的 **FileSystemAccessRule** 对象时传递的参数列表。</span><span class="sxs-lookup"><span data-stu-id="1aaec-161">The `$fileSystemAccessRuleArgumentList` variable is an argument list is to be passed when making the new **FileSystemAccessRule** object.</span></span> <span data-ttu-id="1aaec-162">然后，创建一个新的 **FileSystemAccessRule** 对象，并将 **FileSystemAccessRule** 对象传递到 **SetAccessRule ( # B1** 方法，添加新的访问规则。</span><span class="sxs-lookup"><span data-stu-id="1aaec-162">Then a new **FileSystemAccessRule** object is created, and the **FileSystemAccessRule** object is passed to the **SetAccessRule()** method, adds the new access rule.</span></span>

<span data-ttu-id="1aaec-163">最后一个命令使用将 `Set-Acl` 的安全描述符应用到 Dog.txt。</span><span class="sxs-lookup"><span data-stu-id="1aaec-163">The last command uses `Set-Acl` to apply the security descriptor of to Dog.txt.</span></span>
<span data-ttu-id="1aaec-164">命令完成后， **BUILTIN\Administrators** 组将对 Dog.txt 具有完全控制。</span><span class="sxs-lookup"><span data-stu-id="1aaec-164">When the command completes, the **BUILTIN\Administrators** group will have full control of the Dog.txt.</span></span>

## <span data-ttu-id="1aaec-165">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1aaec-165">PARAMETERS</span></span>

### <span data-ttu-id="1aaec-166">-AclObject</span><span class="sxs-lookup"><span data-stu-id="1aaec-166">-AclObject</span></span>

<span data-ttu-id="1aaec-167">指定具有所需属性值的 ACL。</span><span class="sxs-lookup"><span data-stu-id="1aaec-167">Specifies an ACL with the desired property values.</span></span> <span data-ttu-id="1aaec-168">`Set-Acl` 更改 **Path** 或 **InputObject** 参数指定的项的 ACL，使其与指定安全对象中的值相匹配。</span><span class="sxs-lookup"><span data-stu-id="1aaec-168">`Set-Acl` changes the ACL of item specified by the **Path** or **InputObject** parameter to match the values in the specified security object.</span></span>

<span data-ttu-id="1aaec-169">可以将命令的输出保存 `Get-Acl` 在变量中，然后使用 **AclObject** 参数传递变量，或者键入 `Get-Acl` 命令。</span><span class="sxs-lookup"><span data-stu-id="1aaec-169">You can save the output of a `Get-Acl` command in a variable and then use the **AclObject** parameter to pass the variable, or type a `Get-Acl` command.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1aaec-170">-ClearCentralAccessPolicy</span><span class="sxs-lookup"><span data-stu-id="1aaec-170">-ClearCentralAccessPolicy</span></span>

<span data-ttu-id="1aaec-171">从指定项中删除中心访问策略。</span><span class="sxs-lookup"><span data-stu-id="1aaec-171">Removes the central access policy from the specified item.</span></span>

<span data-ttu-id="1aaec-172">从 Windows Server 2012 开始，管理员可以使用 Active Directory 和组策略为用户和组设置中心访问策略。</span><span class="sxs-lookup"><span data-stu-id="1aaec-172">Beginning in Windows Server 2012, administrators can use Active Directory and Group Policy to set central access policies for users and groups.</span></span> <span data-ttu-id="1aaec-173">有关详细信息，请参阅 [动态访问控制：方案概述](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview)。</span><span class="sxs-lookup"><span data-stu-id="1aaec-173">For more information, see [Dynamic Access Control: Scenario Overview](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview).</span></span>

<span data-ttu-id="1aaec-174">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="1aaec-174">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ByPath, ByLiteralPath
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1aaec-175">-Exclude</span><span class="sxs-lookup"><span data-stu-id="1aaec-175">-Exclude</span></span>

<span data-ttu-id="1aaec-176">忽略指定项。</span><span class="sxs-lookup"><span data-stu-id="1aaec-176">Omits the specified items.</span></span> <span data-ttu-id="1aaec-177">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="1aaec-177">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="1aaec-178">请输入路径元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="1aaec-178">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="1aaec-179">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="1aaec-179">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="1aaec-180">-Filter</span><span class="sxs-lookup"><span data-stu-id="1aaec-180">-Filter</span></span>

<span data-ttu-id="1aaec-181">以提供程序的格式或语言指定筛选器。</span><span class="sxs-lookup"><span data-stu-id="1aaec-181">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="1aaec-182">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="1aaec-182">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="1aaec-183">筛选器的语法（包括通配符的使用）取决于提供程序。</span><span class="sxs-lookup"><span data-stu-id="1aaec-183">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="1aaec-184">筛选器比其他参数更有效，因为提供程序是在检索对象时应用筛选器，而不是在检索对象后再对其进行筛选。</span><span class="sxs-lookup"><span data-stu-id="1aaec-184">Filters are more efficient than other parameters, because the provider applies them when retrieving the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="1aaec-185">-Include</span><span class="sxs-lookup"><span data-stu-id="1aaec-185">-Include</span></span>

<span data-ttu-id="1aaec-186">只更改指定项。</span><span class="sxs-lookup"><span data-stu-id="1aaec-186">Changes only the specified items.</span></span> <span data-ttu-id="1aaec-187">此参数值使 **Path** 参数有效。</span><span class="sxs-lookup"><span data-stu-id="1aaec-187">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="1aaec-188">请输入路径元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="1aaec-188">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="1aaec-189">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="1aaec-189">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="1aaec-190">-InputObject</span><span class="sxs-lookup"><span data-stu-id="1aaec-190">-InputObject</span></span>

<span data-ttu-id="1aaec-191">更改指定对象的安全描述符。</span><span class="sxs-lookup"><span data-stu-id="1aaec-191">Changes the security descriptor of the specified object.</span></span> <span data-ttu-id="1aaec-192">请输入包含对象的变量或可获取该对象的命令。</span><span class="sxs-lookup"><span data-stu-id="1aaec-192">Enter a variable that contains the object or a command that gets the object.</span></span>

<span data-ttu-id="1aaec-193">不能通过管道将对象更改为 `Set-Acl` 。</span><span class="sxs-lookup"><span data-stu-id="1aaec-193">You cannot pipe the object to be changed to `Set-Acl`.</span></span> <span data-ttu-id="1aaec-194">而应该在命令中显式使用 **InputObject** 参数。</span><span class="sxs-lookup"><span data-stu-id="1aaec-194">Instead, use the **InputObject** parameter explicitly in the command.</span></span>

<span data-ttu-id="1aaec-195">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="1aaec-195">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1aaec-196">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1aaec-196">-LiteralPath</span></span>

<span data-ttu-id="1aaec-197">更改指定项的安全描述符。</span><span class="sxs-lookup"><span data-stu-id="1aaec-197">Changes the security descriptor of the specified item.</span></span> <span data-ttu-id="1aaec-198">与 **Path** 不同， **LiteralPath** 参数的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="1aaec-198">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="1aaec-199">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="1aaec-199">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="1aaec-200">如果路径包含转义符，请将其括在单引号中 (`'`) 。</span><span class="sxs-lookup"><span data-stu-id="1aaec-200">If the path includes escape characters, enclose it in single quotation marks (`'`).</span></span>
<span data-ttu-id="1aaec-201">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="1aaec-201">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="1aaec-202">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="1aaec-202">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1aaec-203">-Passthru</span><span class="sxs-lookup"><span data-stu-id="1aaec-203">-Passthru</span></span>

<span data-ttu-id="1aaec-204">返回表示已更改的安全描述符的对象。</span><span class="sxs-lookup"><span data-stu-id="1aaec-204">Returns an object that represents the security descriptor that was changed.</span></span> <span data-ttu-id="1aaec-205">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="1aaec-205">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1aaec-206">-Path</span><span class="sxs-lookup"><span data-stu-id="1aaec-206">-Path</span></span>

<span data-ttu-id="1aaec-207">更改指定项的安全描述符。</span><span class="sxs-lookup"><span data-stu-id="1aaec-207">Changes the security descriptor of the specified item.</span></span> <span data-ttu-id="1aaec-208">输入项的路径，如文件或注册表项的路径。</span><span class="sxs-lookup"><span data-stu-id="1aaec-208">Enter the path to an item, such as a path to a file or registry key.</span></span> <span data-ttu-id="1aaec-209">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="1aaec-209">Wildcards are permitted.</span></span>

<span data-ttu-id="1aaec-210">如果将安全对象传递到 `Set-Acl` (通过使用 **AclObject** 或 **SecurityDescriptor** 参数，或者通过将安全对象从 Get-Acl 传递到 `Set-Acl`) ，并且省略了 **path** 参数 (名称和值) ，则 `Set-Acl` 使用安全对象中包含的路径。</span><span class="sxs-lookup"><span data-stu-id="1aaec-210">If you pass a security object to `Set-Acl` (either by using the **AclObject** or **SecurityDescriptor** parameters or by passing a security object from Get-Acl to `Set-Acl`), and you omit the **Path** parameter (name and value), `Set-Acl` uses the path that is included in the security object.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="1aaec-211">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1aaec-211">-Confirm</span></span>

<span data-ttu-id="1aaec-212">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="1aaec-212">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1aaec-213">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1aaec-213">-WhatIf</span></span>

<span data-ttu-id="1aaec-214">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="1aaec-214">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="1aaec-215">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="1aaec-215">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1aaec-216">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1aaec-216">CommonParameters</span></span>

<span data-ttu-id="1aaec-217">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="1aaec-217">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1aaec-218">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="1aaec-218">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1aaec-219">输入</span><span class="sxs-lookup"><span data-stu-id="1aaec-219">INPUTS</span></span>

### <span data-ttu-id="1aaec-220">System.Security.AccessControl.ObjectSecurity、System.Security.AccessControl.CommonSecurityDescriptor</span><span class="sxs-lookup"><span data-stu-id="1aaec-220">System.Security.AccessControl.ObjectSecurity, System.Security.AccessControl.CommonSecurityDescriptor</span></span>

<span data-ttu-id="1aaec-221">你可以通过管道将 ACL 对象或安全描述符发送到 `Set-Acl` 。</span><span class="sxs-lookup"><span data-stu-id="1aaec-221">You can pipe an ACL object or a security descriptor to `Set-Acl`.</span></span>

## <span data-ttu-id="1aaec-222">输出</span><span class="sxs-lookup"><span data-stu-id="1aaec-222">OUTPUTS</span></span>

### <span data-ttu-id="1aaec-223">System.Security.AccessControl.FileSecurity</span><span class="sxs-lookup"><span data-stu-id="1aaec-223">System.Security.AccessControl.FileSecurity</span></span>

<span data-ttu-id="1aaec-224">默认情况下，不 `Set-Acl` 会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="1aaec-224">By default, `Set-Acl` does not generate any output.</span></span>
<span data-ttu-id="1aaec-225">但是，如果使用 **Passthru** 参数，则它会生成一个安全对象。</span><span class="sxs-lookup"><span data-stu-id="1aaec-225">However, if you use the **Passthru** parameter, it generates a security object.</span></span>
<span data-ttu-id="1aaec-226">安全对象的类型取决于项的类型。</span><span class="sxs-lookup"><span data-stu-id="1aaec-226">The type of the security object depends on the type of the item.</span></span>

## <span data-ttu-id="1aaec-227">注释</span><span class="sxs-lookup"><span data-stu-id="1aaec-227">NOTES</span></span>

 <span data-ttu-id="1aaec-228">`Set-Acl`PowerShell 文件系统和注册表提供程序支持 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1aaec-228">The `Set-Acl` cmdlet is supported by the PowerShell file system and registry providers.</span></span> <span data-ttu-id="1aaec-229">因此，可以使用它来更改文件、目录和注册表项的安全描述符。</span><span class="sxs-lookup"><span data-stu-id="1aaec-229">As such, you can use it to change the security descriptors of files, directories, and registry keys.</span></span>

## <span data-ttu-id="1aaec-230">相关链接</span><span class="sxs-lookup"><span data-stu-id="1aaec-230">RELATED LINKS</span></span>

[<span data-ttu-id="1aaec-231">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="1aaec-231">Get-Acl</span></span>](Get-Acl.md)

[<span data-ttu-id="1aaec-232">FileSystemAccessRule</span><span class="sxs-lookup"><span data-stu-id="1aaec-232">FileSystemAccessRule</span></span>](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor)

[<span data-ttu-id="1aaec-233">ObjectSecurity. SetAccessRuleProtection</span><span class="sxs-lookup"><span data-stu-id="1aaec-233">ObjectSecurity.SetAccessRuleProtection</span></span>](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection)

[<span data-ttu-id="1aaec-234">FileSystemRights</span><span class="sxs-lookup"><span data-stu-id="1aaec-234">FileSystemRights</span></span>](/dotnet/api/system.security.accesscontrol.filesystemrights)
