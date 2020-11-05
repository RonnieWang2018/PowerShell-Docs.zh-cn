---
ms.date: 07/08/2020
keywords: dsc,powershell,配置,安装程序
title: 编写单实例 DSC 资源（最佳做法）
description: 本文介绍了在配置中定义仅允许单个实例的 DSC 资源的最佳做法。
ms.openlocfilehash: 4744136b5a733c86b517b239b2c37ce57a4246f7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662641"
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a><span data-ttu-id="f551e-104">编写单实例 DSC 资源（最佳做法）</span><span class="sxs-lookup"><span data-stu-id="f551e-104">Writing a single-instance DSC resource (best practice)</span></span>

> [!NOTE]
> <span data-ttu-id="f551e-105">本文介绍了在配置中定义仅允许单个实例的 DSC 资源的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="f551e-105">This article describes a best practice for defining a DSC resource that allows only a single instance in a configuration.</span></span> <span data-ttu-id="f551e-106">目前还没有用于实现此操作的内置 DSC 功能。</span><span class="sxs-lookup"><span data-stu-id="f551e-106">Currently, there is no built-in DSC feature to do this.</span></span> <span data-ttu-id="f551e-107">将来可能会发生改变。</span><span class="sxs-lookup"><span data-stu-id="f551e-107">That might change in the future.</span></span>

<span data-ttu-id="f551e-108">在一些情况下，你不希望允许在配置中多次使用某一资源。</span><span class="sxs-lookup"><span data-stu-id="f551e-108">There are situations where you don't want to allow a resource to be used multiple times in a configuration.</span></span> <span data-ttu-id="f551e-109">例如，在 [xTimeZone](https://github.com/PowerShell/xTimeZone) 资源的早期实现中，配置可以多次调用资源，在每个资源块中将时区设置为不同的设置：</span><span class="sxs-lookup"><span data-stu-id="f551e-109">For example, in a previous implementation of the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource, a configuration could call the resource multiple times, setting the time zone to a different setting in each resource block:</span></span>

```powershell
Configuration SetTimeZone
{
    Param
    (
        [String[]]$NodeName = $env:COMPUTERNAME

    )

    Import-DSCResource -ModuleName xTimeZone


    Node $NodeName
    {
         xTimeZone TimeZoneExample
         {

            TimeZone = 'Eastern Standard Time'
         }

         xTimeZone TimeZoneExample2
         {

            TimeZone = 'Pacific Standard Time'

         }

    }
}
```

<span data-ttu-id="f551e-110">这是由 DSC 资源键的作用方式导致的。</span><span class="sxs-lookup"><span data-stu-id="f551e-110">This is because of the way DSC resource keys work.</span></span> <span data-ttu-id="f551e-111">一个资源必须具有至少一个键属性。</span><span class="sxs-lookup"><span data-stu-id="f551e-111">A resource must have at least one key property.</span></span> <span data-ttu-id="f551e-112">如果资源实例的所有键属性的值组合是唯一的，那么该实例也被视为是唯一的。</span><span class="sxs-lookup"><span data-stu-id="f551e-112">A resource instance is considered unique if the combination of the values of all of its key properties is unique.</span></span> <span data-ttu-id="f551e-113">在其早期实现中， [xTimeZone](https://github.com/PowerShell/xTimeZone) 资源仅有一个属性（即 **TimeZone** ），该属性必须是一个键。</span><span class="sxs-lookup"><span data-stu-id="f551e-113">In its previous implementation, the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource had only one property-- **TimeZone** , which was required to be a key.</span></span> <span data-ttu-id="f551e-114">因此，如上所示的配置可以编译和运行，而不会发出警告。</span><span class="sxs-lookup"><span data-stu-id="f551e-114">Because of this, a configuration such as the one above would compile and run without warning.</span></span> <span data-ttu-id="f551e-115">每个 **xTimeZone** 资源块都被视为是唯一的。</span><span class="sxs-lookup"><span data-stu-id="f551e-115">Each of the **xTimeZone** resource blocks is considered unique.</span></span> <span data-ttu-id="f551e-116">这将导致配置重复应用于该节点，反复循环时区。</span><span class="sxs-lookup"><span data-stu-id="f551e-116">This would cause the configuration to be repeatedly applied to the node, cycling the timezone back and forth.</span></span>

<span data-ttu-id="f551e-117">为确保配置只能为目标节点设置一次时区，已更新资源以添加另一属性，即 **IsSingleInstance** ，该属性已成为键属性。</span><span class="sxs-lookup"><span data-stu-id="f551e-117">To ensure that a configuration could set the time zone for a target node only once, the resource was updated to add a second property, **IsSingleInstance** , that became the key property.</span></span> <span data-ttu-id="f551e-118">已使用 **ValueMap** 将 **IsSingleInstance** 限制为单个值，即“Yes”。</span><span class="sxs-lookup"><span data-stu-id="f551e-118">The **IsSingleInstance** was limited to a single value, "Yes" by using a **ValueMap**.</span></span> <span data-ttu-id="f551e-119">该资源的旧 MOF 架构为：</span><span class="sxs-lookup"><span data-stu-id="f551e-119">The old MOF schema for the resource was:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="f551e-120">该资源更新后的 MOF 架构为：</span><span class="sxs-lookup"><span data-stu-id="f551e-120">The updated MOF schema for the resource is:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="f551e-121">资源脚本也已更新为使用新参数。</span><span class="sxs-lookup"><span data-stu-id="f551e-121">The resource script was also updated to use the new parameter.</span></span> <span data-ttu-id="f551e-122">下面介绍了资源脚本发生的变化：</span><span class="sxs-lookup"><span data-stu-id="f551e-122">Here how the resource script was changed:</span></span>

```powershell
function Get-TargetResource
{
    [CmdletBinding()]
    [OutputType([Hashtable])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Get the current TimeZone
    $CurrentTimeZone = Get-TimeZone

    $returnValue = @{
        TimeZone = $CurrentTimeZone
        IsSingleInstance = 'Yes'
    }

    #Output the target resource
    $returnValue
}

function Set-TargetResource
{
    [CmdletBinding()]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output the result of Get-TargetResource function.
    $CurrentTimeZone = Get-TimeZone

    Write-Verbose -Message "Replace the System Time Zone to $TimeZone"

    try
    {
        if($CurrentTimeZone -ne $TimeZone)
        {
            Write-Verbose -Verbose "Setting the TimeZone"
            Set-TimeZone -TimeZone $TimeZone
        }
        else
        {
            Write-Verbose -Verbose "TimeZone already set to $TimeZone"
        }
    }
    catch
    {
        $ErrorMsg = $_.Exception.Message
        Write-Verbose -Verbose $ErrorMsg
    }
}


function Test-TargetResource
{
    [CmdletBinding()]
    [OutputType([Boolean])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output from Get-TargetResource
    $CurrentTimeZone = Get-TimeZone

    if($TimeZone -eq $CurrentTimeZone)
    {
        return $true
    }
    else
    {
        return $false
    }
}

Function Get-TimeZone {
    [CmdletBinding()]
    param()

    & tzutil.exe /g
}

Function Set-TimeZone {
    [CmdletBinding()]
    param(
        [Parameter(Mandatory=$true)]
        [System.String]
        $TimeZone
    )

    try
    {
        & tzutil.exe /s $TimeZone
    }
    catch
    {
        $ErrorMsg = $_.Exception.Message
        Write-Verbose $ErrorMsg
    }
}

Export-ModuleMember -Function *-TargetResource
```

<span data-ttu-id="f551e-123">请注意， **TimeZone** 属性不再是一个键。</span><span class="sxs-lookup"><span data-stu-id="f551e-123">Notice that the **TimeZone** property is no longer a key.</span></span> <span data-ttu-id="f551e-124">现在，如果配置（通过使用两个具有不同 **TimeZone** 值的 **xTimeZone** 块）尝试设置时区两次，尝试编译配置将会导致错误生成：</span><span class="sxs-lookup"><span data-stu-id="f551e-124">Now, if a configuration attempts to set the time zone twice (by using two different **xTimeZone** blocks with different **TimeZone** values), attempting to compile the configuration will cause an error:</span></span>

```Output
Test-ConflictingResources : A conflict was detected between resources '[xTimeZone]TimeZoneExample (::15::10::xTimeZone)' and
'[xTimeZone]TimeZoneExample2 (::22::10::xTimeZone)' in node 'CONTOSO-CLIENT'. Resources have identical key properties but there are differences in the
following non-key properties: 'TimeZone'. Values 'Eastern Standard Time' don't match values 'Pacific Standard Time'. Please update these property
values so that they are identical in both cases.
At line:271 char:9
+         Test-ConflictingResources $keywordName $canonicalizedValue $k ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : ConflictingDuplicateResource,Test-ConflictingResources
Errors occurred while processing configuration 'SetTimeZone'.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3705 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (SetTimeZone:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```
