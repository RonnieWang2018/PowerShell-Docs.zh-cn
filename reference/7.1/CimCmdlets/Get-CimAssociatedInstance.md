---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimassociatedinstance?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimAssociatedInstance
ms.openlocfilehash: c00507460cb80121c0fc8fc246d7fb3f7d7fe0f3
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "93199137"
---
# <span data-ttu-id="41749-103">Get-CimAssociatedInstance</span><span class="sxs-lookup"><span data-stu-id="41749-103">Get-CimAssociatedInstance</span></span>

## <span data-ttu-id="41749-104">摘要</span><span class="sxs-lookup"><span data-stu-id="41749-104">SYNOPSIS</span></span>
<span data-ttu-id="41749-105">检索通过关联连接到特定 CIM 实例的 CIM 实例。</span><span class="sxs-lookup"><span data-stu-id="41749-105">Retrieves the CIM instances that are connected to a specific CIM instance by an association.</span></span>

## <span data-ttu-id="41749-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="41749-106">SYNTAX</span></span>

### <span data-ttu-id="41749-107">ComputerSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="41749-107">ComputerSet (Default)</span></span>

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] [-ComputerName <String[]>] [-KeyOnly] [<CommonParameters>]
```

### <span data-ttu-id="41749-108">SessionSet</span><span class="sxs-lookup"><span data-stu-id="41749-108">SessionSet</span></span>

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] -CimSession <CimSession[]> [-KeyOnly] [<CommonParameters>]
```

## <span data-ttu-id="41749-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="41749-109">DESCRIPTION</span></span>

<span data-ttu-id="41749-110">`Get-CimAssociatedInstance`Cmdlet 通过关联检索连接到特定 cim 实例（称为源实例）的 cim 实例。</span><span class="sxs-lookup"><span data-stu-id="41749-110">The `Get-CimAssociatedInstance` cmdlet retrieves the CIM instances connected to a specific CIM instance, called the source instance, by an association.</span></span>

<span data-ttu-id="41749-111">在关联中，每个 CIM 实例都有一个已命名的角色，同一 CIM 实例可以参与不同角色的关联。</span><span class="sxs-lookup"><span data-stu-id="41749-111">In an association, each CIM instance has a named role and the same CIM instance can participate in an association in different roles.</span></span>

<span data-ttu-id="41749-112">如果未指定 InputObject 参数，该 cmdlet 将采用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="41749-112">If the InputObject parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="41749-113">如果 **ComputerName** 参数和 **CimSession** 参数均未指定，则此 cmdlet 将在本地 Windows Management Instrumentation (WMI) 使用组件对象模型 (COM) 会话。</span><span class="sxs-lookup"><span data-stu-id="41749-113">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="41749-114">如果指定 **computername** 参数或 **CimSession** 参数，则此 cmdlet 适用于 **ComputerName** 参数或 **CimSession** 参数指定的 CIM 服务器。</span><span class="sxs-lookup"><span data-stu-id="41749-114">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

## <span data-ttu-id="41749-115">示例</span><span class="sxs-lookup"><span data-stu-id="41749-115">EXAMPLES</span></span>

### <span data-ttu-id="41749-116">示例1：获取特定实例的所有关联实例</span><span class="sxs-lookup"><span data-stu-id="41749-116">Example 1: Get all the associated instances of a specific instance</span></span>

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1]
```

<span data-ttu-id="41749-117">这一组命令将检索名为 Win32_LogicalDisk 的类的实例，并使用 cmdlet 将该信息存储在名为的变量中 `$disk` `Get-CimInstance` 。</span><span class="sxs-lookup"><span data-stu-id="41749-117">This set of commands retrieves the instances of the class named Win32_LogicalDisk and stores the information in a variable named `$disk` using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="41749-118">然后，将变量中的第一个逻辑磁盘实例用作 cmdlet 的输入对象 `Get-CimAssociatedInstance` ，以获取指定的 cim 实例的所有关联 cim 实例。</span><span class="sxs-lookup"><span data-stu-id="41749-118">The first logical disk instance in the variable is then used as the input object for the `Get-CimAssociatedInstance` cmdlet to get all the associated CIM instances of the specified CIM instance.</span></span>

### <span data-ttu-id="41749-119">示例2：获取特定类型的所有关联实例</span><span class="sxs-lookup"><span data-stu-id="41749-119">Example 2: Get all the associated instances of a specific type</span></span>

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1] -ResultClass Win32_DiskPartition
```

<span data-ttu-id="41749-120">这一组命令将检索 **Win32_LogicalDisk** 类的所有实例，并将它们存储在一个名为的变量中 `$disk` 。</span><span class="sxs-lookup"><span data-stu-id="41749-120">This set of commands retrieves all the instances of the **Win32_LogicalDisk** class and stores them in a variable named `$disk`.</span></span> <span data-ttu-id="41749-121">然后，将变量中的第一个逻辑磁盘实例用作 cmdlet 的输入对象， `Get-CimAssociatedInstance` 以获取通过指定的 association 类 **Win32_DiskPartition** 关联的所有关联的实例。</span><span class="sxs-lookup"><span data-stu-id="41749-121">The first logical disk instance in the variable is then used as the input object for the `Get-CimAssociatedInstance` cmdlet to get all the associated instances that are associated through the specified association class **Win32_DiskPartition** .</span></span>

### <span data-ttu-id="41749-122">示例3：通过特定类的限定符获取所有关联的实例</span><span class="sxs-lookup"><span data-stu-id="41749-122">Example 3: Get all the associated instances through qualifier of a specific class</span></span>

```powershell
$s = Get-CimInstance -Query "Select * from Win32_Service where name like 'Winmgmt'"
Get-CimClass -ClassName *Service* -Qualifier "Association"
$c.CimClasName
```

```Output
Win32_LoadOrderGroupServiceDependencies
Win32_DependentService
Win32_SystemServices
Win32_LoadOrderGroupServiceMembers
Win32_ServiceSpecificationService
```

```powershell
Get-CimAssociatedInstance -InputObject $s -Association Win32_DependentService
```

<span data-ttu-id="41749-123">这一组命令将检索依赖于 WMI 服务的服务，并将它们存储在一个名为的变量中 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="41749-123">This set of commands retrieves the services that depend on WMI service and stores them in a variable named `$s`.</span></span> <span data-ttu-id="41749-124">使用 cmdlet 检索 **Win32_DependentService** 的关联类名称，方法是将 `Get-CimClass` **association** 指定为限定符，然后将 $s 传递到 `Get-CimAssociatedInstance` cmdlet，以获取已检索关联类的所有关联实例。</span><span class="sxs-lookup"><span data-stu-id="41749-124">The association class name for the **Win32_DependentService** is retrieved using the `Get-CimClass` cmdlet by specifying **Association** as the qualifier and is then passed with $s to the `Get-CimAssociatedInstance` cmdlet to get all the associated instances of the retrieved association class.</span></span>

## <span data-ttu-id="41749-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="41749-125">PARAMETERS</span></span>

### <span data-ttu-id="41749-126">-关联</span><span class="sxs-lookup"><span data-stu-id="41749-126">-Association</span></span>

<span data-ttu-id="41749-127">指定关联类的名称。</span><span class="sxs-lookup"><span data-stu-id="41749-127">Specifies the name of the association class.</span></span> <span data-ttu-id="41749-128">如果未指定此参数，则该 cmdlet 将返回任何类型的所有现有关联对象。</span><span class="sxs-lookup"><span data-stu-id="41749-128">If you do not specify this parameter, the cmdlet returns all existing association objects of any type.</span></span>

<span data-ttu-id="41749-129">例如，如果类 A 通过两个关联（AB1 和 AB2）与类 B 关联，则可以使用此参数来指定关联类型（AB1 或 AB2）。</span><span class="sxs-lookup"><span data-stu-id="41749-129">For example, if class A is associated with class B through two associations, AB1 and AB2, then this parameter can be used to specify the type of association, either AB1 or AB2.</span></span>

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

### <span data-ttu-id="41749-130">-CimSession</span><span class="sxs-lookup"><span data-stu-id="41749-130">-CimSession</span></span>

<span data-ttu-id="41749-131">使用指定的 CIM 会话运行该命令。</span><span class="sxs-lookup"><span data-stu-id="41749-131">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="41749-132">输入包含 CIM 会话的变量，或输入创建或获取 CIM 会话的命令（如 `New-CimSession` 或） `Get-CimSession` 。</span><span class="sxs-lookup"><span data-stu-id="41749-132">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as `New-CimSession` or `Get-CimSession`.</span></span> <span data-ttu-id="41749-133">有关详细信息，请参阅 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)。</span><span class="sxs-lookup"><span data-stu-id="41749-133">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

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

### <span data-ttu-id="41749-134">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="41749-134">-ComputerName</span></span>

<span data-ttu-id="41749-135">指定要在其上运行 CIM 操作的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="41749-135">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="41749-136">可以指定完全限定的域名 (FQDN) 或 NetBIOS 名称。</span><span class="sxs-lookup"><span data-stu-id="41749-136">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

<span data-ttu-id="41749-137">如果指定此参数，则该 cmdlet 将使用 WsMan 协议创建到指定计算机的临时会话。</span><span class="sxs-lookup"><span data-stu-id="41749-137">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="41749-138">如果未指定此参数，则该 cmdlet 将使用组件对象模型 (COM) 在本地计算机上执行操作。</span><span class="sxs-lookup"><span data-stu-id="41749-138">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="41749-139">如果在同一台计算机上执行多个操作，则使用 CIM 会话进行连接可以提高性能。</span><span class="sxs-lookup"><span data-stu-id="41749-139">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41749-140">-InputObject</span><span class="sxs-lookup"><span data-stu-id="41749-140">-InputObject</span></span>

<span data-ttu-id="41749-141">指定此 cmdlet 的输入。</span><span class="sxs-lookup"><span data-stu-id="41749-141">Specifies the input to this cmdlet.</span></span> <span data-ttu-id="41749-142">可以使用此参数，也可以通过管道传送此 cmdlet 的输入。</span><span class="sxs-lookup"><span data-stu-id="41749-142">You can use this parameter, or you can pipe the input to this cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: (All)
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="41749-143">-KeyOnly</span><span class="sxs-lookup"><span data-stu-id="41749-143">-KeyOnly</span></span>

<span data-ttu-id="41749-144">返回仅填充了键属性的对象。</span><span class="sxs-lookup"><span data-stu-id="41749-144">Returns objects with only key properties populated.</span></span> <span data-ttu-id="41749-145">这将减少通过网络传输的数据量。</span><span class="sxs-lookup"><span data-stu-id="41749-145">This reduces the amount of data that is transferred over the network.</span></span>

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

### <span data-ttu-id="41749-146">-Namespace</span><span class="sxs-lookup"><span data-stu-id="41749-146">-Namespace</span></span>

<span data-ttu-id="41749-147">指定 CIM 操作的命名空间。</span><span class="sxs-lookup"><span data-stu-id="41749-147">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="41749-148">默认命名空间为 root/cimv2。</span><span class="sxs-lookup"><span data-stu-id="41749-148">The default namespace is root/cimv2.</span></span>

> [!NOTE]
> <span data-ttu-id="41749-149">您可以使用 tab 自动补全来浏览命名空间列表，因为 PowerShell 从本地 WMI 服务器获取命名空间列表以提供命名空间列表。</span><span class="sxs-lookup"><span data-stu-id="41749-149">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

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

### <span data-ttu-id="41749-150">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="41749-150">-OperationTimeoutSec</span></span>

<span data-ttu-id="41749-151">指定 cmdlet 等待计算机响应的时间量。</span><span class="sxs-lookup"><span data-stu-id="41749-151">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="41749-152">默认情况下，此参数的值为0，表示该 cmdlet 使用服务器的默认超时值。</span><span class="sxs-lookup"><span data-stu-id="41749-152">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="41749-153">如果 **OperationTimeoutSec** 参数设置为小于3分钟的稳定连接重试超时值，则不能恢复最后超过 **OperationTimeoutSec** 参数值的网络故障，因为在客户端重新连接之前，服务器上的操作将超时。</span><span class="sxs-lookup"><span data-stu-id="41749-153">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="41749-154">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="41749-154">-ResourceUri</span></span>

<span data-ttu-id="41749-155">指定资源类或实例 (URI) 的资源统一资源标识符。</span><span class="sxs-lookup"><span data-stu-id="41749-155">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="41749-156">URI 用于标识计算机上特定类型的资源，例如磁盘或进程。</span><span class="sxs-lookup"><span data-stu-id="41749-156">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="41749-157">URI 由前缀和指向资源的路径组成。</span><span class="sxs-lookup"><span data-stu-id="41749-157">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="41749-158">例如：</span><span class="sxs-lookup"><span data-stu-id="41749-158">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="41749-159">默认情况下，如果不指定此参数，则将使用 DMTF 标准资源 URI， `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 并向其追加类名称。</span><span class="sxs-lookup"><span data-stu-id="41749-159">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="41749-160">**ResourceURI** 只能与使用 wsman 协议创建的 cim 会话一起使用，也可以在指定 **ComputerName** 参数时使用，后者使用 wsman 创建 cim 会话。</span><span class="sxs-lookup"><span data-stu-id="41749-160">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="41749-161">如果在不指定 **ComputerName** 参数的情况下指定此参数，或指定使用 DCOM 协议创建的 CIM 会话，则会出现错误，因为 DCOM 协议不支持 **ResourceURI** 参数。</span><span class="sxs-lookup"><span data-stu-id="41749-161">If you specify this parameter without specifying the **ComputerName** parameter, or if you specify a CIM session created using DCOM protocol, you get an error, because the DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="41749-162">如果同时指定了 **ResourceUri** 参数和 **筛选器** 参数，则忽略 **筛选器** 参数。</span><span class="sxs-lookup"><span data-stu-id="41749-162">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41749-163">-ResultClassName</span><span class="sxs-lookup"><span data-stu-id="41749-163">-ResultClassName</span></span>

<span data-ttu-id="41749-164">指定关联实例的类名称。</span><span class="sxs-lookup"><span data-stu-id="41749-164">Specifies the class name of the associated instances.</span></span> <span data-ttu-id="41749-165">CIM 实例可以与一个或多个 CIM 实例相关联。</span><span class="sxs-lookup"><span data-stu-id="41749-165">A CIM instance can be associated with one or more CIM instances.</span></span> <span data-ttu-id="41749-166">如果未指定结果类名称，则返回所有关联的 CIM 实例。</span><span class="sxs-lookup"><span data-stu-id="41749-166">All associated CIM instances are returned if you do not specify the result class name.</span></span>

<span data-ttu-id="41749-167">默认情况下，此参数的值为 null，并返回所有关联的 CIM 实例。</span><span class="sxs-lookup"><span data-stu-id="41749-167">By default, the value of this parameter is null, and all associated CIM instances are returned.</span></span>

<span data-ttu-id="41749-168">可以筛选关联结果以匹配特定类名。</span><span class="sxs-lookup"><span data-stu-id="41749-168">You can filter the association results to match a specific class name.</span></span> <span data-ttu-id="41749-169">筛选将在服务器上进行。</span><span class="sxs-lookup"><span data-stu-id="41749-169">Filtering happens on the server.</span></span> <span data-ttu-id="41749-170">如果未指定此参数，则将 `Get-CIMAssociatedInstance` 返回所有现有关联。</span><span class="sxs-lookup"><span data-stu-id="41749-170">If this parameter is not specified, `Get-CIMAssociatedInstance` returns all existing associations.</span></span> <span data-ttu-id="41749-171">例如，如果类 A 与类 B、C 和 D 相关联，则可以使用此参数将输出限制为 (B、C 或 D) 的特定类型。</span><span class="sxs-lookup"><span data-stu-id="41749-171">For example, if class A is associated with classes B, C and D, then this parameter can be used to restrict the output to a specific type (B, C or D).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41749-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="41749-172">CommonParameters</span></span>

<span data-ttu-id="41749-173">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="41749-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="41749-174">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="41749-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="41749-175">输入</span><span class="sxs-lookup"><span data-stu-id="41749-175">INPUTS</span></span>

### <span data-ttu-id="41749-176">无</span><span class="sxs-lookup"><span data-stu-id="41749-176">None</span></span>

<span data-ttu-id="41749-177">此 cmdlet 不接受输入对象。</span><span class="sxs-lookup"><span data-stu-id="41749-177">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="41749-178">输出</span><span class="sxs-lookup"><span data-stu-id="41749-178">OUTPUTS</span></span>

### <span data-ttu-id="41749-179">System.Object</span><span class="sxs-lookup"><span data-stu-id="41749-179">System.Object</span></span>

<span data-ttu-id="41749-180">此 cmdlet 将返回一个对象。</span><span class="sxs-lookup"><span data-stu-id="41749-180">This cmdlet returns an object.</span></span>

## <span data-ttu-id="41749-181">注释</span><span class="sxs-lookup"><span data-stu-id="41749-181">NOTES</span></span>

## <span data-ttu-id="41749-182">相关链接</span><span class="sxs-lookup"><span data-stu-id="41749-182">RELATED LINKS</span></span>

[<span data-ttu-id="41749-183">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="41749-183">Get-CimClass</span></span>](get-cimclass.md)

[<span data-ttu-id="41749-184">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="41749-184">Get-CimInstance</span></span>](get-ciminstance.md)

