---
description: 注册表
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_registry_provider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Registry 提供程序
ms.openlocfilehash: e97fc607c456909dc0abdb50cb7dd5b5847998a0
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/13/2020
ms.locfileid: "93200329"
---
# <a name="registry-provider"></a><span data-ttu-id="ed276-104">注册表提供程序</span><span class="sxs-lookup"><span data-stu-id="ed276-104">Registry provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="ed276-105">提供程序名称</span><span class="sxs-lookup"><span data-stu-id="ed276-105">Provider name</span></span>

<span data-ttu-id="ed276-106">注册表</span><span class="sxs-lookup"><span data-stu-id="ed276-106">Registry</span></span>

## <a name="drives"></a><span data-ttu-id="ed276-107">驱动器</span><span class="sxs-lookup"><span data-stu-id="ed276-107">Drives</span></span>

<span data-ttu-id="ed276-108">`HKLM:`, `HKCU:`</span><span class="sxs-lookup"><span data-stu-id="ed276-108">`HKLM:`, `HKCU:`</span></span>

## <a name="capabilities"></a><span data-ttu-id="ed276-109">功能</span><span class="sxs-lookup"><span data-stu-id="ed276-109">Capabilities</span></span>

<span data-ttu-id="ed276-110">**ShouldProcess** 、 **UseTransactions**</span><span class="sxs-lookup"><span data-stu-id="ed276-110">**ShouldProcess** , **UseTransactions**</span></span>

## <a name="short-description"></a><span data-ttu-id="ed276-111">简短说明</span><span class="sxs-lookup"><span data-stu-id="ed276-111">Short description</span></span>

<span data-ttu-id="ed276-112">提供对 PowerShell 中的注册表项、条目和值的访问权限。</span><span class="sxs-lookup"><span data-stu-id="ed276-112">Provides access to the registry keys, entries, and values in PowerShell.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="ed276-113">详细说明</span><span class="sxs-lookup"><span data-stu-id="ed276-113">Detailed description</span></span>

<span data-ttu-id="ed276-114">PowerShell **注册表** 提供程序可让你获取、添加、更改、清除和删除 PowerShell 中的注册表项、条目和值。</span><span class="sxs-lookup"><span data-stu-id="ed276-114">The PowerShell **Registry** provider lets you get, add, change, clear, and delete registry keys, entries, and values in PowerShell.</span></span>

<span data-ttu-id="ed276-115">**注册表** 驱动器是包含计算机上的注册表项和子项的分层命名空间。</span><span class="sxs-lookup"><span data-stu-id="ed276-115">The **Registry** drives are a hierarchical namespace containing the registry keys and subkeys on your computer.</span></span> <span data-ttu-id="ed276-116">注册表条目和注册表值不是该层次结构的组成部分。</span><span class="sxs-lookup"><span data-stu-id="ed276-116">Registry entries and values are not components of that hierarchy.</span></span> <span data-ttu-id="ed276-117">而是每个注册表项的属性。</span><span class="sxs-lookup"><span data-stu-id="ed276-117">Instead, they are properties of each of the keys.</span></span>

<span data-ttu-id="ed276-118">**注册表** 提供程序支持以下 cmdlet，本文将对此进行介绍。</span><span class="sxs-lookup"><span data-stu-id="ed276-118">The **Registry** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="ed276-119">Get-Location</span><span class="sxs-lookup"><span data-stu-id="ed276-119">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="ed276-120">Set-Location</span><span class="sxs-lookup"><span data-stu-id="ed276-120">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="ed276-121">Get-Item</span><span class="sxs-lookup"><span data-stu-id="ed276-121">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="ed276-122">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="ed276-122">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="ed276-123">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="ed276-123">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="ed276-124">Move-Item</span><span class="sxs-lookup"><span data-stu-id="ed276-124">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="ed276-125">New-Item</span><span class="sxs-lookup"><span data-stu-id="ed276-125">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="ed276-126">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="ed276-126">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="ed276-127">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ed276-127">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="ed276-128">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ed276-128">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="ed276-129">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ed276-129">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="ed276-130">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ed276-130">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="ed276-131">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="ed276-131">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="ed276-132">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="ed276-132">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="ed276-133">此提供程序公开的类型</span><span class="sxs-lookup"><span data-stu-id="ed276-133">Types exposed by this provider</span></span>

<span data-ttu-id="ed276-134">注册表项表示为 [Microsoft. RegistryKey](/dotnet/api/microsoft.win32.registrykey) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="ed276-134">Registry keys are represented as instances of the [Microsoft.Win32.RegistryKey](/dotnet/api/microsoft.win32.registrykey) class.</span></span> <span data-ttu-id="ed276-135">注册表项表示为 [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="ed276-135">Registry entries are represented as instances of the [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) class.</span></span>

## <a name="navigating-the-registry-drives"></a><span data-ttu-id="ed276-136">导航注册表驱动器</span><span class="sxs-lookup"><span data-stu-id="ed276-136">Navigating the Registry drives</span></span>

<span data-ttu-id="ed276-137">**注册表** 提供程序将其数据存储公开为两个默认驱动器。</span><span class="sxs-lookup"><span data-stu-id="ed276-137">The **Registry** provider exposes its data store as two default drives.</span></span> <span data-ttu-id="ed276-138">注册表位置 HKEY_LOCAL_MACHINE 映射到 `HKLM:` 驱动器，HKEY_CURRENT_USER 映射到 `HKCU:` 驱动器。</span><span class="sxs-lookup"><span data-stu-id="ed276-138">The registry location HKEY_LOCAL_MACHINE is mapped to the `HKLM:` drive and HKEY_CURRENT_USER is mapped to the `HKCU:` drive.</span></span> <span data-ttu-id="ed276-139">若要使用注册表，可以使用以下命令将位置更改为 `HKLM:` 驱动器。</span><span class="sxs-lookup"><span data-stu-id="ed276-139">To work with the registry, you can change your location to the `HKLM:` drive using the following command.</span></span>

```powershell
Set-Location HKLM:
```

<span data-ttu-id="ed276-140">若要返回到文件系统驱动器，请键入驱动器名称。</span><span class="sxs-lookup"><span data-stu-id="ed276-140">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="ed276-141">例如，键入：</span><span class="sxs-lookup"><span data-stu-id="ed276-141">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="ed276-142">还可以从任何其他 PowerShell 驱动器使用 **注册表** 提供程序。</span><span class="sxs-lookup"><span data-stu-id="ed276-142">You can also work with the **Registry** provider from any other PowerShell drive.</span></span> <span data-ttu-id="ed276-143">若要从其他位置引用注册表项，请在路径中使用驱动器名称 (`HKLM:` ， `HKCU:`) 。</span><span class="sxs-lookup"><span data-stu-id="ed276-143">To reference a registry key from another location, use the drive name (`HKLM:`, `HKCU:`) in the path.</span></span> <span data-ttu-id="ed276-144">使用反斜杠 (\\) 或正斜杠 (/) 来指示 **注册表** 驱动器的级别。</span><span class="sxs-lookup"><span data-stu-id="ed276-144">Use a backslash (\\) or a forward slash (/) to indicate a level of the **Registry** drive.</span></span>

```powershell
PS C:\> cd HKLM:\Software
```

> [!NOTE]
> <span data-ttu-id="ed276-145">PowerShell 使用别名以允许你熟悉的方法来处理提供程序路径。</span><span class="sxs-lookup"><span data-stu-id="ed276-145">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="ed276-146">命令（如 `dir` 和） `ls` 现在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的别名， `cd` 是 [集位置](xref:Microsoft.PowerShell.Management.Set-Location)的别名， `pwd` 是 [获取位置](xref:Microsoft.PowerShell.Management.Get-Location)的别名。</span><span class="sxs-lookup"><span data-stu-id="ed276-146">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location), and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

<span data-ttu-id="ed276-147">最后一个示例显示了另一种可以用来导航 **注册表** 提供程序的路径语法。</span><span class="sxs-lookup"><span data-stu-id="ed276-147">This last example shows another path syntax you can use to navigate the **Registry** provider.</span></span> <span data-ttu-id="ed276-148">此语法使用提供程序名称，后跟两个冒号 `::` 。</span><span class="sxs-lookup"><span data-stu-id="ed276-148">This syntax uses the provider name, followed by two colons `::`.</span></span> <span data-ttu-id="ed276-149">此语法允许使用完整的 HIVE 名称，而不是映射的驱动器名称 `HKLM` 。</span><span class="sxs-lookup"><span data-stu-id="ed276-149">This syntax allows you to use the full HIVE name, instead of the mapped drive name `HKLM`.</span></span>

```powershell
cd "Registry::HKEY_LOCAL_MACHINE\Software"
```

## <a name="displaying-the-contents-of-registry-keys"></a><span data-ttu-id="ed276-150">显示注册表项的内容</span><span class="sxs-lookup"><span data-stu-id="ed276-150">Displaying the contents of registry keys</span></span>

<span data-ttu-id="ed276-151">注册表分为多个键、子项和项。</span><span class="sxs-lookup"><span data-stu-id="ed276-151">The registry is divided into keys, subkeys, and entries.</span></span> <span data-ttu-id="ed276-152">有关注册表结构的详细信息，请参阅 [注册表的结构](/windows/desktop/sysinfo/structure-of-the-registry)。</span><span class="sxs-lookup"><span data-stu-id="ed276-152">For more information about registry structure, see [Structure of the Registry](/windows/desktop/sysinfo/structure-of-the-registry).</span></span>

<span data-ttu-id="ed276-153">在 **注册表** 驱动器中，每个密钥都是一个容器。</span><span class="sxs-lookup"><span data-stu-id="ed276-153">In a **Registry** drive, each key is a container.</span></span> <span data-ttu-id="ed276-154">键可以包含任意数量的键。</span><span class="sxs-lookup"><span data-stu-id="ed276-154">A key can contain any number of keys.</span></span> <span data-ttu-id="ed276-155">具有父键的注册表项称为 "子项"。</span><span class="sxs-lookup"><span data-stu-id="ed276-155">A registry key that has a parent key is called a subkey.</span></span> <span data-ttu-id="ed276-156">你可以使用 `Get-ChildItem` 查看注册表项并 `Set-Location` 导航到密钥路径。</span><span class="sxs-lookup"><span data-stu-id="ed276-156">You can use `Get-ChildItem` to view registry keys and `Set-Location` to navigate to a key path.</span></span>

<span data-ttu-id="ed276-157">注册表值是注册表项的属性。</span><span class="sxs-lookup"><span data-stu-id="ed276-157">Registry values are attributes of a registry key.</span></span> <span data-ttu-id="ed276-158">在 **注册表** 驱动器中，它们被称为 " **项目属性** "。</span><span class="sxs-lookup"><span data-stu-id="ed276-158">In the **Registry** drive, they are called **Item Properties** .</span></span> <span data-ttu-id="ed276-159">注册表项可以同时具有子键和项属性。</span><span class="sxs-lookup"><span data-stu-id="ed276-159">A registry key can have both children keys and item properties.</span></span>

<span data-ttu-id="ed276-160">在此示例中，显示了和之间的差异 `Get-Item` `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="ed276-160">In this example, the difference between `Get-Item` and `Get-ChildItem` is shown.</span></span> <span data-ttu-id="ed276-161">当你 `Get-Item` 在 "后台处理程序" 注册表项上使用时，你可以查看其属性。</span><span class="sxs-lookup"><span data-stu-id="ed276-161">When you use `Get-Item` on the "Spooler" registry key, you can view its properties.</span></span>

```
PS C:\ > Get-Item -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services


Name        Property
----        --------
Spooler     DependOnService    : {RPCSS, http}
            Description        : @%systemroot%\system32\spoolsv.exe,-2
            DisplayName        : @%systemroot%\system32\spoolsv.exe,-1
            ErrorControl       : 1
            FailureActions     : {16, 14, 0, 0...}
            Group              : SpoolerGroup
            ImagePath          : C:\WINDOWS\System32\spoolsv.exe
            ObjectName         : LocalSystem
            RequiredPrivileges : {SeTcbPrivilege, SeImpersonatePrivilege, ...
            ServiceSidType     : 1
            Start              : 2
            Type               : 27
```

<span data-ttu-id="ed276-162">每个注册表项也可以具有子项。</span><span class="sxs-lookup"><span data-stu-id="ed276-162">Each registry key can also have subkeys.</span></span> <span data-ttu-id="ed276-163">使用 `Get-Item` 注册表项时，不显示子项。</span><span class="sxs-lookup"><span data-stu-id="ed276-163">When you use `Get-Item` on a registry key, the subkeys are not displayed.</span></span> <span data-ttu-id="ed276-164">该 `Get-ChildItem` cmdlet 将显示 "后台处理程序" 键的子项，其中包括每个子项的属性。</span><span class="sxs-lookup"><span data-stu-id="ed276-164">The `Get-ChildItem` cmdlet will show you children items of the "Spooler" key, including each subkey's properties.</span></span> <span data-ttu-id="ed276-165">使用时，不会显示父键属性 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="ed276-165">The parent keys properties are not shown when using `Get-ChildItem`.</span></span>

```
PS C:\> Get-ChildItem -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Spooler


Name             Property
----             --------
Performance      Close           : PerfClose
                 Collect         : PerfCollect
                 Collect Timeout : 2000
                 Library         : C:\Windows\System32\winspool.drv
                 Object List     : 1450
                 Open            : PerfOpen
                 Open Timeout    : 4000
Security         Security : {1, 0, 20, 128...}
```

<span data-ttu-id="ed276-166">此 `Get-Item` cmdlet 还可用于当前位置。</span><span class="sxs-lookup"><span data-stu-id="ed276-166">The `Get-Item` cmdlet can also be used on the current location.</span></span> <span data-ttu-id="ed276-167">下面的示例导航到 "后台处理程序" 注册表项并获取项属性。</span><span class="sxs-lookup"><span data-stu-id="ed276-167">The following example navigates to the "Spooler" registry key and gets the item properties.</span></span>
<span data-ttu-id="ed276-168">点 `.` 用于指示当前位置。</span><span class="sxs-lookup"><span data-stu-id="ed276-168">The dot `.` is used to indicate the current location.</span></span>

```
PS C:\> cd HKLM:\System\CurrentControlSet\Services\Spooler
PS HKLM:\SYSTEM\CurrentControlSet\Services\Spooler> Get-Item .

    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services

Name             Property
----             --------
Spooler          DependOnService    : {RPCSS, http}
                 Description        : @%systemroot%\system32\spoolsv.exe,-2
...
```

<span data-ttu-id="ed276-169">有关本部分中所述 cmdlet 的详细信息，请参阅以下文章。</span><span class="sxs-lookup"><span data-stu-id="ed276-169">For more information on the cmdlets covered in this section, see the following articles.</span></span>

<span data-ttu-id="ed276-170">-[获取项](xref:Microsoft.PowerShell.Management.Get-Item) 
-[Get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="ed276-170">-[Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
-[Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)</span></span>

## <a name="viewing-registry-key-values"></a><span data-ttu-id="ed276-171">查看注册表项值</span><span class="sxs-lookup"><span data-stu-id="ed276-171">Viewing registry key values</span></span>

<span data-ttu-id="ed276-172">注册表项值存储为每个注册表项的属性。</span><span class="sxs-lookup"><span data-stu-id="ed276-172">Registry key values are stored as properties of each registry key.</span></span> <span data-ttu-id="ed276-173">`Get-ItemProperty`Cmdlet 将使用指定的名称查看注册表项属性。</span><span class="sxs-lookup"><span data-stu-id="ed276-173">The `Get-ItemProperty` cmdlet views registry key properties using the name you specify.</span></span> <span data-ttu-id="ed276-174">结果为 **PSCustomObject** ，其中包含指定的属性。</span><span class="sxs-lookup"><span data-stu-id="ed276-174">The result is a **PSCustomObject** containing the properties you specify.</span></span>

<span data-ttu-id="ed276-175">下面的示例使用 `Get-ItemProperty` cmdlet 查看所有属性。</span><span class="sxs-lookup"><span data-stu-id="ed276-175">The Following example uses the `Get-ItemProperty` cmdlet to view all properties.</span></span> <span data-ttu-id="ed276-176">如果将生成的对象存储在变量中，则可以访问所需的属性值。</span><span class="sxs-lookup"><span data-stu-id="ed276-176">Storing the resulting object in a variable allows you to access the desired property value.</span></span>

```powershell
$p = Get-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler
$p.DependOnService
```

```output
RPCSS
http
```

<span data-ttu-id="ed276-177">指定参数的值 `-Name` 会选择指定的属性，并返回 **PSCustomObject** 。</span><span class="sxs-lookup"><span data-stu-id="ed276-177">Specifying a value for the `-Name` parameter selects the properties you specify and returns the **PSCustomObject** .</span></span>  <span data-ttu-id="ed276-178">下面的示例演示使用参数时的输出差异 `-Name` 。</span><span class="sxs-lookup"><span data-stu-id="ed276-178">The following example shows the difference in output when you use the `-Name` parameter.</span></span>

```
PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem

BUILD                      : 17134.1
Installation Directory     : C:\WINDOWS\system32\WBEM
MOF Self-Install Directory : C:\WINDOWS\system32\WBEM\MOF
PSPath                     : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath               : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName                : Wbem
PSDrive                    : HKLM
PSProvider                 : Microsoft.PowerShell.Core\Registry

PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD

BUILD        : 17134.1
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName  : Wbem
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
```

<span data-ttu-id="ed276-179">从 PowerShell 5.0 开始， `Get-ItemPropertyValue` cmdlet 仅返回指定属性的值。</span><span class="sxs-lookup"><span data-stu-id="ed276-179">Beginning in PowerShell 5.0, the `Get-ItemPropertyValue` cmdlet returns only the value of the property you specify.</span></span>

```powershell
Get-ItemPropertyValue -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD
```

```output
17134.1
```

<span data-ttu-id="ed276-180">有关本部分中使用的 cmdlet 的详细信息，请参阅以下文章。</span><span class="sxs-lookup"><span data-stu-id="ed276-180">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="ed276-181">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ed276-181">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="ed276-182">Get-ItemPropertyValue</span><span class="sxs-lookup"><span data-stu-id="ed276-182">Get-ItemPropertyValue</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)

## <a name="changing-registry-key-values"></a><span data-ttu-id="ed276-183">更改注册表项值</span><span class="sxs-lookup"><span data-stu-id="ed276-183">Changing registry key values</span></span>

<span data-ttu-id="ed276-184">`Set-ItemProperty`Cmdlet 将设置注册表项的属性。</span><span class="sxs-lookup"><span data-stu-id="ed276-184">The `Set-ItemProperty` cmdlet will set attributes for registry keys.</span></span> <span data-ttu-id="ed276-185">下面的示例使用将 `Set-ItemProperty` 后台处理程序服务启动类型更改为 "手动"。</span><span class="sxs-lookup"><span data-stu-id="ed276-185">The following example uses `Set-ItemProperty` to change the spooler service start type to manual.</span></span> <span data-ttu-id="ed276-186">该示例使用 cmdlet 将 **StartType** 更改回 *自动* `Set-Service` 。</span><span class="sxs-lookup"><span data-stu-id="ed276-186">The example changes the **StartType** back to *Automatic* using the `Set-Service` cmdlet.</span></span>

```
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler Automatic

PS C:\> $path = "HKLM:\SYSTEM\CurrentControlSet\Services\Spooler\"
PS C:\> Set-ItemProperty -Path $path -Name Start -Value 3
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler    Manual

PS C:\> Set-Service -Name Spooler -StartupType Automatic
```

<span data-ttu-id="ed276-187">每个注册表项都有一个 *默认* 值。</span><span class="sxs-lookup"><span data-stu-id="ed276-187">Each registry key has a *default* value.</span></span> <span data-ttu-id="ed276-188">您可以使用或更改注册表项的 *默认* 值 `Set-Item` `Set-ItemProperty` 。</span><span class="sxs-lookup"><span data-stu-id="ed276-188">You can change the *default* value for a registry key with either `Set-Item` or `Set-ItemProperty`.</span></span>

```powershell
Set-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name "(default)" -Value "one"
Set-Item -Path HKLM:\SOFTWARE\Contoso -Value "two"
```

<span data-ttu-id="ed276-189">有关本部分中使用的 cmdlet 的详细信息，请参阅以下文章。</span><span class="sxs-lookup"><span data-stu-id="ed276-189">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="ed276-190">Set-Item</span><span class="sxs-lookup"><span data-stu-id="ed276-190">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)
- [<span data-ttu-id="ed276-191">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ed276-191">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="creating-registry-keys-and-values"></a><span data-ttu-id="ed276-192">创建注册表项和值</span><span class="sxs-lookup"><span data-stu-id="ed276-192">Creating registry keys and values</span></span>

<span data-ttu-id="ed276-193">该 `New-Item` cmdlet 将创建具有你提供的名称的注册表项。</span><span class="sxs-lookup"><span data-stu-id="ed276-193">The `New-Item` cmdlet will create registry keys with a name that you provide.</span></span>
<span data-ttu-id="ed276-194">你还可以使用 `mkdir` 函数 `New-Item` 在内部调用 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ed276-194">You can also use the `mkdir` function, which calls the `New-Item` cmdlet internally.</span></span>

```
PS HKLM:\SOFTWARE\> mkdir ContosoCompany

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
ContosoCompany
```

<span data-ttu-id="ed276-195">可以使用 `New-ItemProperty` cmdlet 在指定的注册表项中创建值。</span><span class="sxs-lookup"><span data-stu-id="ed276-195">You can use the `New-ItemProperty` cmdlet to create values in a registry key that you specify.</span></span> <span data-ttu-id="ed276-196">下面的示例在 ContosoCompany 注册表项上创建新的 DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="ed276-196">The following example creates a new DWORD value on the ContosoCompany registry key.</span></span>

```powershell
$path = "HKLM:\SOFTWARE\ContosoCompany"
New-ItemProperty -Path  -Name Test -Type DWORD -Value 1
```

> [!NOTE]
> <span data-ttu-id="ed276-197">有关其他允许的类型值，请查看本文中的动态参数部分。</span><span class="sxs-lookup"><span data-stu-id="ed276-197">Review the dynamic parameters section in this article for other allowed type values.</span></span>

<span data-ttu-id="ed276-198">有关详细的 cmdlet 用法，请参阅 [set-itemproperty](xref:Microsoft.PowerShell.Management.New-ItemProperty)。</span><span class="sxs-lookup"><span data-stu-id="ed276-198">For detailed cmdlet usage, see [New-ItemProperty](xref:Microsoft.PowerShell.Management.New-ItemProperty).</span></span>

## <a name="copying-registry-keys-and-values"></a><span data-ttu-id="ed276-199">复制注册表项和值</span><span class="sxs-lookup"><span data-stu-id="ed276-199">Copying registry keys and values</span></span>

<span data-ttu-id="ed276-200">在 **注册表** 提供程序中，使用 `Copy-Item` cmdlet 复制注册表项和值。</span><span class="sxs-lookup"><span data-stu-id="ed276-200">In the **Registry** provider, use the `Copy-Item` cmdlet copies registry keys and values.</span></span> <span data-ttu-id="ed276-201">使用 `Copy-ItemProperty` cmdlet 仅复制注册表值。</span><span class="sxs-lookup"><span data-stu-id="ed276-201">Use the `Copy-ItemProperty` cmdlet to copy registry values only.</span></span>
<span data-ttu-id="ed276-202">以下命令将 "Contoso" 注册表项及其属性复制到指定位置 "HKLM： \ Software\Fabrikam"。</span><span class="sxs-lookup"><span data-stu-id="ed276-202">The following command copies the "Contoso" registry key, and its properties to the specified location "HKLM:\Software\Fabrikam".</span></span>

<span data-ttu-id="ed276-203">`Copy-Item` 如果目标项不存在，则创建它。</span><span class="sxs-lookup"><span data-stu-id="ed276-203">`Copy-Item` creates the destination key if it does not exist.</span></span> <span data-ttu-id="ed276-204">如果目标项存在，则会将源键的 `Copy-Item` 副本创建为子项， (目标键的子项) 。</span><span class="sxs-lookup"><span data-stu-id="ed276-204">If the destination key exists, `Copy-Item` creates a duplicate of the source key as a child item (subkey) of the destination key.</span></span>

```powershell
Copy-Item -Path  HKLM:\Software\Contoso -Destination HKLM:\Software\Fabrikam
```

<span data-ttu-id="ed276-205">以下命令使用 cmdlet 将 " `Copy-ItemProperty` Server" 值从 "Contoso" 密钥复制到 "Fabrikam" 密钥。</span><span class="sxs-lookup"><span data-stu-id="ed276-205">The following command uses the `Copy-ItemProperty` cmdlet to copy the "Server" value from the "Contoso" key to the "Fabrikam" key.</span></span>

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Copy-ItemProperty -Path $source -Destination $dest -Name Server
```

<span data-ttu-id="ed276-206">有关本部分中使用的 cmdlet 的详细信息，请参阅以下文章。</span><span class="sxs-lookup"><span data-stu-id="ed276-206">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="ed276-207">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="ed276-207">Copy-Item</span></span>](xref:Microsoft.PowerShell.Management.Copy-Item)
- [<span data-ttu-id="ed276-208">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ed276-208">Copy-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

## <a name="moving-registry-keys-and-values"></a><span data-ttu-id="ed276-209">移动注册表项和值</span><span class="sxs-lookup"><span data-stu-id="ed276-209">Moving registry keys and values</span></span>

<span data-ttu-id="ed276-210">`Move-Item`和 `Move-ItemProperty` cmdlet 的行为类似于其 "复制" 对应项。</span><span class="sxs-lookup"><span data-stu-id="ed276-210">The `Move-Item` and `Move-ItemProperty` cmdlets behave like their "Copy" counterparts.</span></span> <span data-ttu-id="ed276-211">如果目标存在，则 `Move-Item` 将源键移动到目标项的下方。</span><span class="sxs-lookup"><span data-stu-id="ed276-211">If the destination exists, `Move-Item` moves the source key underneath the destination key.</span></span> <span data-ttu-id="ed276-212">如果目标项不存在，则会将源键移动到目标路径。</span><span class="sxs-lookup"><span data-stu-id="ed276-212">If the destination key does not exist, the source key is moved to the destination path.</span></span>

<span data-ttu-id="ed276-213">以下命令将 "Contoso" 键移动到路径 "HKLM： \ SOFTWARE\Fabrikam"。</span><span class="sxs-lookup"><span data-stu-id="ed276-213">The following command moves the "Contoso" key to the path "HKLM:\SOFTWARE\Fabrikam".</span></span>

```powershell
Move-Item -Path HKLM:\SOFTWARE\Contoso -Destination HKLM:\SOFTWARE\Fabrikam
```

<span data-ttu-id="ed276-214">此命令将所有属性从 "HKLM： \ SOFTWARE\ContosoCompany" 移动到 "HKLM： \ SOFTWARE\Fabrikam"。</span><span class="sxs-lookup"><span data-stu-id="ed276-214">This command moves all of the properties from "HKLM:\SOFTWARE\ContosoCompany" to "HKLM:\SOFTWARE\Fabrikam".</span></span>

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Move-ItemProperty -Path $source -Destination $dest -Name *
```

<span data-ttu-id="ed276-215">有关本部分中使用的 cmdlet 的详细信息，请参阅以下文章。</span><span class="sxs-lookup"><span data-stu-id="ed276-215">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="ed276-216">Move-Item</span><span class="sxs-lookup"><span data-stu-id="ed276-216">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="ed276-217">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ed276-217">Move-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Move-ItemProperty)

## <a name="renaming-registry-keys-and-values"></a><span data-ttu-id="ed276-218">重命名注册表项和值</span><span class="sxs-lookup"><span data-stu-id="ed276-218">Renaming registry keys and values</span></span>

<span data-ttu-id="ed276-219">你可以像对文件和文件夹一样重命名注册表项和值。</span><span class="sxs-lookup"><span data-stu-id="ed276-219">You can rename registry keys and values just like you would files and folders.</span></span>
<span data-ttu-id="ed276-220">`Rename-Item` 重命名注册表项，同时 `Rename-ItemProperty` 重命名注册表值。</span><span class="sxs-lookup"><span data-stu-id="ed276-220">`Rename-Item` renames registry keys, while `Rename-ItemProperty` renames registry values.</span></span>

```powershell
$path = "HKLM:\SOFTWARE\Contoso"
Rename-ItemProperty -Path $path -Name ContosoTest -NewName FabrikamTest
Rename-Item -Path $path -NewName Fabrikam
```

## <a name="changing-security-descriptors"></a><span data-ttu-id="ed276-221">更改安全描述符</span><span class="sxs-lookup"><span data-stu-id="ed276-221">Changing security descriptors</span></span>

<span data-ttu-id="ed276-222">你可以使用和 cmdlet 限制对注册表项的访问 `Get-Acl` `Set-Acl` 。</span><span class="sxs-lookup"><span data-stu-id="ed276-222">You can restrict access to registry keys using the `Get-Acl` and `Set-Acl` cmdlets.</span></span> <span data-ttu-id="ed276-223">下面的示例将具有 "完全控制" 的新用户添加到 "HKLM： \ SOFTWARE\Contoso" 注册表项。</span><span class="sxs-lookup"><span data-stu-id="ed276-223">The following example adds a new user with full control to the "HKLM:\SOFTWARE\Contoso" registry key.</span></span>

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Contoso
$rule = New-Object System.Security.AccessControl.RegistryAccessRule `
("CONTOSO\jsmith", "FullControl", "Allow")
$acl.SetAccessRule($rule)
$acl | Set-Acl -Path HKLM:\SOFTWARE\Contoso
```

<span data-ttu-id="ed276-224">有关更多示例和 cmdlet 用法详细信息，请参阅以下文章。</span><span class="sxs-lookup"><span data-stu-id="ed276-224">For more examples and cmdlet usage details see the following articles.</span></span>

- [<span data-ttu-id="ed276-225">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="ed276-225">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="ed276-226">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="ed276-226">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="removing-and-clearing-registry-keys-and-values"></a><span data-ttu-id="ed276-227">删除和清除注册表项和值</span><span class="sxs-lookup"><span data-stu-id="ed276-227">Removing and clearing registry keys and values</span></span>

<span data-ttu-id="ed276-228">您可以通过使用 **Remove item** 删除包含的项，但如果项包含任何其他内容，系统将提示您确认删除。</span><span class="sxs-lookup"><span data-stu-id="ed276-228">You can remove contained items by using **Remove-Item** , but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="ed276-229">以下示例尝试删除密钥 "HKLM： \ SOFTWARE\Contoso"。</span><span class="sxs-lookup"><span data-stu-id="ed276-229">The following example attempts to delete a key "HKLM:\SOFTWARE\Contoso".</span></span>

```
PS C:\> dir HKLM:\SOFTWARE\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Contoso

Name                           Property
----                           --------
ChildKey

PS C:\> Remove-Item -Path HKLM:\SOFTWARE\Contoso

Confirm
The item at HKLM:\SOFTWARE\Contoso has children and the -Recurse
parameter was not specified. If you continue, all children will be removed
with the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="ed276-230">若要在不提示的情况下删除包含的项，请指定 `-Recurse` 参数。</span><span class="sxs-lookup"><span data-stu-id="ed276-230">To delete contained items without prompting, specify the `-Recurse` parameter.</span></span>

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso -Recurse
```

<span data-ttu-id="ed276-231">如果要删除 "HKLM： \ SOFTWARE\Contoso" 内的所有项，而不是 "HKLM： \ SOFTWARE\Contoso" 本身，请使用后面跟有通配符的尾随反斜杠 `\` 。</span><span class="sxs-lookup"><span data-stu-id="ed276-231">If you wanted to remove all items within "HKLM:\SOFTWARE\Contoso" but not "HKLM:\SOFTWARE\Contoso" itself, use a trailing backslash `\` followed by a wildcard.</span></span>

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso\* -Recurse
```

<span data-ttu-id="ed276-232">此命令从 "HKLM： \ SOFTWARE\Contoso" 注册表项中删除 "ContosoTest" 注册表值。</span><span class="sxs-lookup"><span data-stu-id="ed276-232">This command deletes the "ContosoTest" registry value from the "HKLM:\SOFTWARE\Contoso" registry key.</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name ContosoTest
```

<span data-ttu-id="ed276-233">`Clear-Item` 清除所有注册表项的注册表值。</span><span class="sxs-lookup"><span data-stu-id="ed276-233">`Clear-Item` clears all registry values for a key.</span></span> <span data-ttu-id="ed276-234">下面的示例将清除 "HKLM： \ SOFTWARE\Contoso" 注册表项中的所有值。</span><span class="sxs-lookup"><span data-stu-id="ed276-234">The following example clears all values from the "HKLM:\SOFTWARE\Contoso" registry key.</span></span> <span data-ttu-id="ed276-235">若要仅清除特定属性，请使用 `Clear-ItemProperty` 。</span><span class="sxs-lookup"><span data-stu-id="ed276-235">To clear only a specific property, use `Clear-ItemProperty`.</span></span>

```
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name           Property
----           --------
Contoso        Server     : {a, b, c}
               HereString : {This is text which contains
               newlines. It also contains "quoted" strings}
               (default)  : 1

PS HKLM:\SOFTWARE\> Clear-Item .\Contoso\
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
Contoso
```

<span data-ttu-id="ed276-236">有关更多示例和 cmdlet 用法详细信息，请参阅以下文章。</span><span class="sxs-lookup"><span data-stu-id="ed276-236">For more examples and cmdlet usage details see the following articles.</span></span>

- [<span data-ttu-id="ed276-237">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="ed276-237">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="ed276-238">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ed276-238">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="ed276-239">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="ed276-239">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="ed276-240">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ed276-240">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)

## <a name="dynamic-parameters"></a><span data-ttu-id="ed276-241">动态参数</span><span class="sxs-lookup"><span data-stu-id="ed276-241">Dynamic parameters</span></span>

<span data-ttu-id="ed276-242">动态参数是 PowerShell 提供程序添加的 cmdlet 参数，只有在启用了提供程序的驱动器中使用 cmdlet 时，这些参数才可用。</span><span class="sxs-lookup"><span data-stu-id="ed276-242">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="type-microsoftwin32registryvaluekind"></a><span data-ttu-id="ed276-243">键入 <RegistryValueKind></span><span class="sxs-lookup"><span data-stu-id="ed276-243">Type <Microsoft.Win32.RegistryValueKind></span></span>

<span data-ttu-id="ed276-244">建立或更改注册表值的数据类型。</span><span class="sxs-lookup"><span data-stu-id="ed276-244">Establishes or changes the data type of a registry value.</span></span> <span data-ttu-id="ed276-245">默认值为 `String` (REG_SZ) 。</span><span class="sxs-lookup"><span data-stu-id="ed276-245">The default is `String` (REG_SZ).</span></span>

<span data-ttu-id="ed276-246">此参数可用于 [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ed276-246">This parameter works as designed on the [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty) cmdlet.</span></span> <span data-ttu-id="ed276-247">此外，还可以在注册表驱动器中用于 [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item) cmdlet，但它不起作用。</span><span class="sxs-lookup"><span data-stu-id="ed276-247">It is also available on the [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item) cmdlet in the registry drives, but it has no effect.</span></span>

|<span data-ttu-id="ed276-248">Value</span><span class="sxs-lookup"><span data-stu-id="ed276-248">Value</span></span> | <span data-ttu-id="ed276-249">说明</span><span class="sxs-lookup"><span data-stu-id="ed276-249">Description</span></span> |
| ---- | ----------- |
| `String` | <span data-ttu-id="ed276-250">指定以 null 结尾的字符串。</span><span class="sxs-lookup"><span data-stu-id="ed276-250">Specifies a null-terminated string.</span></span> <span data-ttu-id="ed276-251">等效于 REG_SZ。</span><span class="sxs-lookup"><span data-stu-id="ed276-251">Equivalent to REG_SZ.</span></span> |
| `ExpandString` | <span data-ttu-id="ed276-252">指定以 null 结尾的字符串，该字符串包含未展开的</span><span class="sxs-lookup"><span data-stu-id="ed276-252">Specifies a null-terminated string that contains unexpanded</span></span> |
|                | <span data-ttu-id="ed276-253">引用扩展时扩展的环境变量</span><span class="sxs-lookup"><span data-stu-id="ed276-253">references to environment variables that are expanded when</span></span> |
|                | <span data-ttu-id="ed276-254">检索值。</span><span class="sxs-lookup"><span data-stu-id="ed276-254">the value is retrieved.</span></span> <span data-ttu-id="ed276-255">等效于 REG_EXPAND_SZ。</span><span class="sxs-lookup"><span data-stu-id="ed276-255">Equivalent to REG_EXPAND_SZ.</span></span> |
| `Binary` | <span data-ttu-id="ed276-256">指定采用任意格式的二进制数据。</span><span class="sxs-lookup"><span data-stu-id="ed276-256">Specifies binary data in any form.</span></span> <span data-ttu-id="ed276-257">等效于 REG_BINARY。</span><span class="sxs-lookup"><span data-stu-id="ed276-257">Equivalent to REG_BINARY.</span></span> |
| `DWord` | <span data-ttu-id="ed276-258">指定一个 32 位的二进制数字。</span><span class="sxs-lookup"><span data-stu-id="ed276-258">Specifies a 32-bit binary number.</span></span> <span data-ttu-id="ed276-259">等效于 REG_DWORD。</span><span class="sxs-lookup"><span data-stu-id="ed276-259">Equivalent to REG_DWORD.</span></span> |
| `MultiString` | <span data-ttu-id="ed276-260">指定以 null 结尾的字符串的数组，由终止</span><span class="sxs-lookup"><span data-stu-id="ed276-260">Specifies an array of null-terminated strings terminated by</span></span> |
|               | <span data-ttu-id="ed276-261">两个 null 字符。</span><span class="sxs-lookup"><span data-stu-id="ed276-261">two null characters.</span></span> <span data-ttu-id="ed276-262">等效于 REG_MULTI_SZ。</span><span class="sxs-lookup"><span data-stu-id="ed276-262">Equivalent to REG_MULTI_SZ.</span></span> |
| `QWord` | <span data-ttu-id="ed276-263">指定一个 64 位的二进制数字。</span><span class="sxs-lookup"><span data-stu-id="ed276-263">Specifies a 64-bit binary number.</span></span> <span data-ttu-id="ed276-264">等效于 REG_QWORD。</span><span class="sxs-lookup"><span data-stu-id="ed276-264">Equivalent to REG_QWORD.</span></span> |
| `Unknown` | <span data-ttu-id="ed276-265">指示不受支持的注册表数据类型，例如</span><span class="sxs-lookup"><span data-stu-id="ed276-265">Indicates an unsupported registry data type, such as</span></span> |
|           | <span data-ttu-id="ed276-266">REG_RESOURCE_LIST。</span><span class="sxs-lookup"><span data-stu-id="ed276-266">REG_RESOURCE_LIST.</span></span> |

#### <a name="cmdlets-supported"></a><span data-ttu-id="ed276-267">支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="ed276-267">Cmdlets supported</span></span>

- [<span data-ttu-id="ed276-268">Set-Item</span><span class="sxs-lookup"><span data-stu-id="ed276-268">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)
- [<span data-ttu-id="ed276-269">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ed276-269">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="using-the-pipeline"></a><span data-ttu-id="ed276-270">使用管道</span><span class="sxs-lookup"><span data-stu-id="ed276-270">Using the pipeline</span></span>

<span data-ttu-id="ed276-271">提供程序 cmdlet 接受管道输入。</span><span class="sxs-lookup"><span data-stu-id="ed276-271">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="ed276-272">可以通过将提供程序数据从一个 cmdlet 发送到另一个提供程序 cmdlet 来使用管道来简化任务。</span><span class="sxs-lookup"><span data-stu-id="ed276-272">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span> <span data-ttu-id="ed276-273">若要详细了解如何将管道与提供程序 cmdlet 配合使用，请参阅本文中提供的 cmdlet 参考。</span><span class="sxs-lookup"><span data-stu-id="ed276-273">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="ed276-274">获取帮助</span><span class="sxs-lookup"><span data-stu-id="ed276-274">Getting help</span></span>

<span data-ttu-id="ed276-275">从 Windows PowerShell 3.0 开始，你可以获取有关提供程序 cmdlet 的自定义帮助主题，它们介绍了这些 cmdlet 在文件系统驱动器中的行为方式。</span><span class="sxs-lookup"><span data-stu-id="ed276-275">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="ed276-276">若要获取针对文件系统驱动器进行自定义的帮助主题，请 `Get-Help` 在文件系统驱动器中运行命令，或使用 **Path** 参数指定文件系统驱动器。</span><span class="sxs-lookup"><span data-stu-id="ed276-276">To get the help topics that are customized for the file system drive, run a `Get-Help` command in a file system drive or use the **Path** parameter to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path HKLM:
```

## <a name="see-also"></a><span data-ttu-id="ed276-277">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ed276-277">See also</span></span>

 [<span data-ttu-id="ed276-278">about_Providers</span><span class="sxs-lookup"><span data-stu-id="ed276-278">about_Providers</span></span>](../About/about_Providers.md)

