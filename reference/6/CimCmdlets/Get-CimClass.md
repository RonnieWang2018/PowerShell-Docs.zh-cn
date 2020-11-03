---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimclass?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimClass
ms.openlocfilehash: 551ac39084ff7bf1729618d09cfa521cb6858242
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93198462"
---
# <span data-ttu-id="35b23-103">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="35b23-103">Get-CimClass</span></span>

## <span data-ttu-id="35b23-104">摘要</span><span class="sxs-lookup"><span data-stu-id="35b23-104">SYNOPSIS</span></span>
<span data-ttu-id="35b23-105">获取特定命名空间中的 CIM 类的列表。</span><span class="sxs-lookup"><span data-stu-id="35b23-105">Gets a list of CIM classes in a specific namespace.</span></span>

## <span data-ttu-id="35b23-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="35b23-106">SYNTAX</span></span>

### <span data-ttu-id="35b23-107">ComputerSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="35b23-107">ComputerSet (Default)</span></span>

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 [-ComputerName <String[]>] [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

### <span data-ttu-id="35b23-108">SessionSet</span><span class="sxs-lookup"><span data-stu-id="35b23-108">SessionSet</span></span>

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 -CimSession <CimSession[]> [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

## <span data-ttu-id="35b23-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="35b23-109">DESCRIPTION</span></span>

<span data-ttu-id="35b23-110">`Get-CimClass`Cmdlet 将检索特定命名空间中的 CIM 类的列表。</span><span class="sxs-lookup"><span data-stu-id="35b23-110">The `Get-CimClass` cmdlet retrieves a list of CIM classes in a specific namespace.</span></span> <span data-ttu-id="35b23-111">如果未提供类名，则该 cmdlet 将返回命名空间中的所有类。</span><span class="sxs-lookup"><span data-stu-id="35b23-111">If there is no class name supplied, then the cmdlet returns all the classes in the namespace.</span></span> <span data-ttu-id="35b23-112">与 CIM 实例不同，CIM 类不包含从中检索它们的 CIM 会话或计算机名称。</span><span class="sxs-lookup"><span data-stu-id="35b23-112">Unlike a CIM instance, CIM classes do not contain the CIM session or computer name from which they are retrieved.</span></span>

## <span data-ttu-id="35b23-113">示例</span><span class="sxs-lookup"><span data-stu-id="35b23-113">EXAMPLES</span></span>

### <span data-ttu-id="35b23-114">示例1：获取所有类定义</span><span class="sxs-lookup"><span data-stu-id="35b23-114">Example 1: Get all the class definitions</span></span>

<span data-ttu-id="35b23-115">此示例获取命名空间 **root/cimv2** 下的所有类定义。</span><span class="sxs-lookup"><span data-stu-id="35b23-115">This example gets all the class definitions under the namespace **root/cimv2** .</span></span>

```powershell
Get-CimClass
```

### <span data-ttu-id="35b23-116">示例2：获取具有特定名称的类</span><span class="sxs-lookup"><span data-stu-id="35b23-116">Example 2: Get the classes with a specific name</span></span>

<span data-ttu-id="35b23-117">此示例获取名称中包含单词 **disk** 的类。</span><span class="sxs-lookup"><span data-stu-id="35b23-117">This example gets the classes that contain the word **disk** in their names.</span></span>

```powershell
Get-CimClass -ClassName *disk*
```

### <span data-ttu-id="35b23-118">示例3：获取具有特定方法名称的类</span><span class="sxs-lookup"><span data-stu-id="35b23-118">Example 3: Get the classes with a specific method name</span></span>

<span data-ttu-id="35b23-119">此示例获取以名称 **Win32** 开头并且具有以 **Term** 开头的方法名称的类。</span><span class="sxs-lookup"><span data-stu-id="35b23-119">This example gets the classes that start with the name **Win32** and have a method name that starts with **Term** .</span></span>

```powershell
Get-CimClass -ClassName Win32* -MethodName Term*
```

### <span data-ttu-id="35b23-120">示例4：获取具有特定属性名称的类</span><span class="sxs-lookup"><span data-stu-id="35b23-120">Example 4: Get the classes with a specific property name</span></span>

<span data-ttu-id="35b23-121">此示例获取以名称 **Win32** 开头并具有名为 **Handle** 的属性的类。</span><span class="sxs-lookup"><span data-stu-id="35b23-121">This example gets the classes that start with the name **Win32** and have a property named **Handle** .</span></span>

```powershell
Get-CimClass -ClassName Win32* -PropertyName Handle
```

### <span data-ttu-id="35b23-122">示例5：获取具有特定限定符名称的类</span><span class="sxs-lookup"><span data-stu-id="35b23-122">Example 5: Get the classes with a specific qualifier name</span></span>

<span data-ttu-id="35b23-123">此示例获取以名称 **Win32** 开头的类，在其名称中包含单词 **Disk** ，并具有指定的限定符 **关联** 。</span><span class="sxs-lookup"><span data-stu-id="35b23-123">This example gets the classes that start with the name **Win32** , contain the word **Disk** in their names and have the specified qualifier **Association** .</span></span>

```powershell
Get-CimClass -ClassName Win32*Disk* -QualifierName Association
```

### <span data-ttu-id="35b23-124">示例6：获取特定命名空间中的类定义</span><span class="sxs-lookup"><span data-stu-id="35b23-124">Example 6: Get the class definitions from a specific namespace</span></span>

<span data-ttu-id="35b23-125">此示例从指定的命名空间 **root/standardCimv2** 获取名称中包含单词 **Net** 的类定义。</span><span class="sxs-lookup"><span data-stu-id="35b23-125">This example gets the class definitions that contain the word **Net** in their names from the specified namespace **root/standardCimv2** .</span></span>

```powershell
Get-CimClass -Namespace root/standardCimv2 -ClassName *Net*
```

### <span data-ttu-id="35b23-126">示例7：从远程服务器获取类定义</span><span class="sxs-lookup"><span data-stu-id="35b23-126">Example 7: Get the class definitions from a remote server</span></span>

<span data-ttu-id="35b23-127">此示例从指定远程服务器 **Server01** 和 **Server02** 中获取名称中包含单词 **disk** 的类定义。</span><span class="sxs-lookup"><span data-stu-id="35b23-127">This example gets the class definitions that contain the word **disk** in their names from the specified remote servers **Server01** and **Server02** .</span></span>

```powershell
Get-CimClass -ClassName *disk* -ComputerName Server01, Server02
```

### <span data-ttu-id="35b23-128">示例8：使用 CIM 会话获取类</span><span class="sxs-lookup"><span data-stu-id="35b23-128">Example 8: Get the classes by using a CIM session</span></span>

```powershell
$s = New-CimSession -ComputerName Server01, Server02
Get-CimClass -ClassName *disk* -CimSession $s
```

<span data-ttu-id="35b23-129">此组命令创建一个与多台计算机的会话，并使用 cmdlet 将其存储在变量中 `$s` `New-CimSession` ，然后使用 cmdlet 获取类 `Get-CimClass` 。</span><span class="sxs-lookup"><span data-stu-id="35b23-129">This set of commands creates a session with multiple computers and stores it into a variable `$s` using the `New-CimSession` cmdlet, and then gets the classes using the `Get-CimClass` cmdlet.</span></span>

## <span data-ttu-id="35b23-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="35b23-130">PARAMETERS</span></span>

### <span data-ttu-id="35b23-131">-CimSession</span><span class="sxs-lookup"><span data-stu-id="35b23-131">-CimSession</span></span>

<span data-ttu-id="35b23-132">在远程会话中或在远程计算机上运行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="35b23-132">Runs the cmdlet in a remote session or on a remote computer.</span></span> <span data-ttu-id="35b23-133">输入计算机名或会话对象，例如 `New-CimSession` 或 cmdlet 的输出 `Get-CimSession` 。</span><span class="sxs-lookup"><span data-stu-id="35b23-133">Enter a computer name or a session object, such as the output of a `New-CimSession` or `Get-CimSession` cmdlet.</span></span> <span data-ttu-id="35b23-134">默认为本地计算机上的当前会话。</span><span class="sxs-lookup"><span data-stu-id="35b23-134">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: SessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="35b23-135">-ClassName</span><span class="sxs-lookup"><span data-stu-id="35b23-135">-ClassName</span></span>

<span data-ttu-id="35b23-136">指定要对其执行操作的 CIM 类的名称。</span><span class="sxs-lookup"><span data-stu-id="35b23-136">Specifies the name of the CIM class for which to perform the operation.</span></span> <span data-ttu-id="35b23-137">您可以使用 tab 自动补全来浏览类列表，因为 PowerShell 从本地 WMI 服务器获取类的列表以提供类名的列表。</span><span class="sxs-lookup"><span data-stu-id="35b23-137">You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="35b23-138">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="35b23-138">-ComputerName</span></span>

<span data-ttu-id="35b23-139">指定要在其上运行 CIM 操作的计算机。</span><span class="sxs-lookup"><span data-stu-id="35b23-139">Specifies the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="35b23-140">可以指定完全限定的域名 (FQDN) NetBIOS 名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="35b23-140">You can specify a fully qualified domain name (FQDN) a NetBIOS name, or an IP address.</span></span>

<span data-ttu-id="35b23-141">如果指定此参数，则该 cmdlet 将使用 WsMan 协议创建到指定计算机的临时会话。</span><span class="sxs-lookup"><span data-stu-id="35b23-141">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="35b23-142">如果未指定此参数，则该 cmdlet 将使用组件对象模型 (COM) 在本地计算机上执行操作。</span><span class="sxs-lookup"><span data-stu-id="35b23-142">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="35b23-143">如果在同一台计算机上执行多个操作，则使用 CIM 会话可提供更好的性能。</span><span class="sxs-lookup"><span data-stu-id="35b23-143">If multiple operations are being performed on the same computer, using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="35b23-144">-方法名称</span><span class="sxs-lookup"><span data-stu-id="35b23-144">-MethodName</span></span>

<span data-ttu-id="35b23-145">查找具有与此名称匹配的方法的类。</span><span class="sxs-lookup"><span data-stu-id="35b23-145">Finds the classes that have a method matching this name.</span></span> <span data-ttu-id="35b23-146">可以将通配符用于此参数。</span><span class="sxs-lookup"><span data-stu-id="35b23-146">You can use wildcard characters with this parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="35b23-147">-Namespace</span><span class="sxs-lookup"><span data-stu-id="35b23-147">-Namespace</span></span>

<span data-ttu-id="35b23-148">指定 CIM 操作的命名空间。</span><span class="sxs-lookup"><span data-stu-id="35b23-148">Specifies the namespace for CIM operation.</span></span> <span data-ttu-id="35b23-149">默认命名空间为 **root/cimv2** 。</span><span class="sxs-lookup"><span data-stu-id="35b23-149">The default namespace is **root/cimv2** .</span></span> <span data-ttu-id="35b23-150">您可以使用 tab 自动补全来浏览命名空间列表，因为 PowerShell 从本地 WMI 服务器获取命名空间列表以提供命名空间列表。</span><span class="sxs-lookup"><span data-stu-id="35b23-150">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="35b23-151">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="35b23-151">-OperationTimeoutSec</span></span>

<span data-ttu-id="35b23-152">指定 cmdlet 等待计算机响应的时间量。</span><span class="sxs-lookup"><span data-stu-id="35b23-152">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="35b23-153">默认情况下，此参数的值为0，表示该 cmdlet 使用服务器的默认超时值。</span><span class="sxs-lookup"><span data-stu-id="35b23-153">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="35b23-154">如果 **OperationTimeoutSec** 参数设置为小于3分钟的稳定连接重试超时值，则不能恢复最后超过 **OperationTimeoutSec** 参数值的网络故障，因为在客户端重新连接之前，服务器上的操作将超时。</span><span class="sxs-lookup"><span data-stu-id="35b23-154">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="35b23-155">-PropertyName</span><span class="sxs-lookup"><span data-stu-id="35b23-155">-PropertyName</span></span>

<span data-ttu-id="35b23-156">查找具有与此名称匹配的属性的类。</span><span class="sxs-lookup"><span data-stu-id="35b23-156">Finds the classes which have a property matching this name.</span></span> <span data-ttu-id="35b23-157">可以将通配符用于此参数。</span><span class="sxs-lookup"><span data-stu-id="35b23-157">You can use wildcard characters with this parameter.</span></span>

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

### <span data-ttu-id="35b23-158">-QualifierName</span><span class="sxs-lookup"><span data-stu-id="35b23-158">-QualifierName</span></span>

<span data-ttu-id="35b23-159">按类级别限定符名称筛选类。</span><span class="sxs-lookup"><span data-stu-id="35b23-159">Filters the classes by class level qualifier name.</span></span> <span data-ttu-id="35b23-160">可以将通配符用于此参数。</span><span class="sxs-lookup"><span data-stu-id="35b23-160">You can use wildcard characters with this parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="35b23-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="35b23-161">CommonParameters</span></span>

<span data-ttu-id="35b23-162">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="35b23-162">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="35b23-163">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="35b23-163">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="35b23-164">输入</span><span class="sxs-lookup"><span data-stu-id="35b23-164">INPUTS</span></span>

### <span data-ttu-id="35b23-165">无</span><span class="sxs-lookup"><span data-stu-id="35b23-165">None</span></span>

<span data-ttu-id="35b23-166">此 cmdlet 不接受输入对象。</span><span class="sxs-lookup"><span data-stu-id="35b23-166">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="35b23-167">输出</span><span class="sxs-lookup"><span data-stu-id="35b23-167">OUTPUTS</span></span>

### <span data-ttu-id="35b23-168">CimClass。</span><span class="sxs-lookup"><span data-stu-id="35b23-168">Microsoft.Management.Infrastructure.CimClass</span></span>

<span data-ttu-id="35b23-169">此 cmdlet 将返回一个 CIM 类对象。</span><span class="sxs-lookup"><span data-stu-id="35b23-169">This cmdlet returns a CIM class object.</span></span>

## <span data-ttu-id="35b23-170">注释</span><span class="sxs-lookup"><span data-stu-id="35b23-170">NOTES</span></span>

## <span data-ttu-id="35b23-171">相关链接</span><span class="sxs-lookup"><span data-stu-id="35b23-171">RELATED LINKS</span></span>

[<span data-ttu-id="35b23-172">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="35b23-172">New-CimSession</span></span>](New-CimSession.md)
