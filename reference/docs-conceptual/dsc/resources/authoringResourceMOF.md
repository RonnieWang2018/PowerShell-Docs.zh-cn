---
ms.date: 07/08/2020
keywords: dsc,powershell,配置,安装程序
title: 使用 MOF 编写自定义 DSC 资源
description: 本文将在 MOF 文件中定义 DSC 自定义资源的架构，并在 PowerShell 脚本文件中实现资源。
ms.openlocfilehash: e79a37699c468b2c55c307c96f1c193a2c1595b3
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667175"
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a><span data-ttu-id="cbebd-104">使用 MOF 编写自定义 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="cbebd-104">Writing a custom DSC resource with MOF</span></span>

> <span data-ttu-id="cbebd-105">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="cbebd-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="cbebd-106">在本文中，我们将在 MOF 文件中定义 Windows PowerShell Desired State Configuration (DSC) 自定义资源的架构，并在 Windows PowerShell 脚本文件中实现资源。</span><span class="sxs-lookup"><span data-stu-id="cbebd-106">In this article, we will define the schema for a Windows PowerShell Desired State Configuration (DSC) custom resource in a MOF file, and implement the resource in a Windows PowerShell script file.</span></span>
<span data-ttu-id="cbebd-107">此自定义资源被用于创建和维护网站。</span><span class="sxs-lookup"><span data-stu-id="cbebd-107">This custom resource is for creating and maintaining a web site.</span></span>

## <a name="creating-the-mof-schema"></a><span data-ttu-id="cbebd-108">创建 MOF 架构</span><span class="sxs-lookup"><span data-stu-id="cbebd-108">Creating the MOF schema</span></span>

<span data-ttu-id="cbebd-109">架构定义可通过 DSC 配置脚本进行配置的资源的资源的属性。</span><span class="sxs-lookup"><span data-stu-id="cbebd-109">The schema defines the properties of your resource that can be configured by a DSC configuration script.</span></span>

### <a name="folder-structure-for-a-mof-resource"></a><span data-ttu-id="cbebd-110">MOF 资源的文件夹结构</span><span class="sxs-lookup"><span data-stu-id="cbebd-110">Folder structure for a MOF resource</span></span>

<span data-ttu-id="cbebd-111">想要使用 MOF 架构实现 DSC 自定义资源，请创建下列文件夹结构。</span><span class="sxs-lookup"><span data-stu-id="cbebd-111">To implement a DSC custom resource with a MOF schema, create the following folder structure.</span></span> <span data-ttu-id="cbebd-112">MOF 架构在文件 `Demo_IISWebsite.schema.mof` 中进行定义，资源脚本在 `Demo_IISWebsite.psm1` 中进行定义。</span><span class="sxs-lookup"><span data-stu-id="cbebd-112">The MOF schema is defined in the file `Demo_IISWebsite.schema.mof`, and the resource script is defined in `Demo_IISWebsite.psm1`.</span></span> <span data-ttu-id="cbebd-113">或者你也可以创建一个模块清单 (psd1) 文件。</span><span class="sxs-lookup"><span data-stu-id="cbebd-113">Optionally, you can create a module manifest (psd1) file.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

> [!NOTE]
> <span data-ttu-id="cbebd-114">需要在顶级文件夹下创建一个名为 DSCResources 的文件夹，并且每个资源的文件夹都必须与资源名称一致。</span><span class="sxs-lookup"><span data-stu-id="cbebd-114">It is necessary to create a folder named DSCResources under the top-level folder, and that the folder for each resource must have the same name as the resource.</span></span>

### <a name="the-contents-of-the-mof-file"></a><span data-ttu-id="cbebd-115">MOF 文件的内容</span><span class="sxs-lookup"><span data-stu-id="cbebd-115">The contents of the MOF file</span></span>

<span data-ttu-id="cbebd-116">下面是一个可用于自定义网站资源的示例 MOF 文件。</span><span class="sxs-lookup"><span data-stu-id="cbebd-116">Following is an example MOF file that can be used for a custom website resource.</span></span> <span data-ttu-id="cbebd-117">要执行此示例操作，请将此架构保存至文件，并调用文件 `Demo_IISWebsite.schema.mof`。</span><span class="sxs-lookup"><span data-stu-id="cbebd-117">To follow this example, save this schema to a file, and call the file `Demo_IISWebsite.schema.mof`.</span></span>

```
[ClassVersion("1.0.0"), FriendlyName("Website")]
class Demo_IISWebsite : OMI_BaseResource
{
  [Key] string Name;
  [Required] string PhysicalPath;
  [write,ValueMap{"Present", "Absent"},Values{"Present", "Absent"}] string Ensure;
  [write,ValueMap{"Started","Stopped"},Values{"Started", "Stopped"}] string State;
  [write] string Protocol[];
  [write] string BindingInfo[];
  [write] string ApplicationPool;
  [read] string ID;
};
```

<span data-ttu-id="cbebd-118">请注意下列有关之前代码的信息：</span><span class="sxs-lookup"><span data-stu-id="cbebd-118">Note the following about the previous code:</span></span>

- <span data-ttu-id="cbebd-119">`FriendlyName` 定义一个名称，你可以将其用来在 DSC 配置脚本中指代此自定义资源。</span><span class="sxs-lookup"><span data-stu-id="cbebd-119">`FriendlyName` defines the name you can use to refer to this custom resource in DSC configuration scripts.</span></span> <span data-ttu-id="cbebd-120">在此示例中，`Website` 相当于内置存档资源的友好名称 `Archive`。</span><span class="sxs-lookup"><span data-stu-id="cbebd-120">In this example, `Website` is equivalent to the friendly name `Archive` for the built-in Archive resource.</span></span>
- <span data-ttu-id="cbebd-121">为自定义资源定义的类必须派生自 `OMI_BaseResource`。</span><span class="sxs-lookup"><span data-stu-id="cbebd-121">The class you define for your custom resource must derive from `OMI_BaseResource`.</span></span>
- <span data-ttu-id="cbebd-122">属性上的类型限定符 `[Key]` 表示此属性将唯一地标识资源实例。</span><span class="sxs-lookup"><span data-stu-id="cbebd-122">The type qualifier, `[Key]`, on a property indicates that this property will uniquely identify the resource instance.</span></span> <span data-ttu-id="cbebd-123">至少需要一个 `[Key]` 属性。</span><span class="sxs-lookup"><span data-stu-id="cbebd-123">At least one `[Key]` property is required.</span></span>
- <span data-ttu-id="cbebd-124">`[Required]` 限定符表示属性是必需的（在使用此资源的任何配置脚本中都必须指定值）。</span><span class="sxs-lookup"><span data-stu-id="cbebd-124">The `[Required]` qualifier indicates that the property is required (a value must be specified in any configuration script that uses this resource).</span></span>
- <span data-ttu-id="cbebd-125">`[write]` 限定符表示在配置脚本中使用自定义资源时，此属性是可选的。</span><span class="sxs-lookup"><span data-stu-id="cbebd-125">The `[write]` qualifier indicates that this property is optional when using the custom resource in a configuration script.</span></span> <span data-ttu-id="cbebd-126">`[read]` 限定符表示不能通过配置来设置属性，属性只用于报告目的。</span><span class="sxs-lookup"><span data-stu-id="cbebd-126">The `[read]` qualifier indicates that a property cannot be set by a configuration, and is for reporting purposes only.</span></span>
- <span data-ttu-id="cbebd-127">`Values` 按照 `ValueMap` 中定义的值的列表限制分配给属性的值。</span><span class="sxs-lookup"><span data-stu-id="cbebd-127">`Values` restricts the values that can be assigned to the property to the list of values defined in `ValueMap`.</span></span> <span data-ttu-id="cbebd-128">有关详细信息，请参阅 [ValueMap 和值限定符](/windows/desktop/WmiSdk/value-map)。</span><span class="sxs-lookup"><span data-stu-id="cbebd-128">For more information, see [ValueMap and Value Qualifiers](/windows/desktop/WmiSdk/value-map).</span></span>
- <span data-ttu-id="cbebd-129">建议在资源中包含一个名为 `Ensure` 且包含值 `Present` 和 `Absent` 的属性，以便与内置 DSC 资源保持一致。</span><span class="sxs-lookup"><span data-stu-id="cbebd-129">Including a property called `Ensure` with values `Present` and `Absent` in your resource is recommended as a way to maintain a consistent style with built-in DSC resources.</span></span>
- <span data-ttu-id="cbebd-130">如下所示命名自定义资源的架构文件：`classname.schema.mof`，其中 `classname` 是遵循架构定义中 `class` 关键字的标识符。</span><span class="sxs-lookup"><span data-stu-id="cbebd-130">Name the schema file for your custom resource as follows: `classname.schema.mof`, where `classname` is the identifier that follows the `class` keyword in your schema definition.</span></span>

### <a name="writing-the-resource-script"></a><span data-ttu-id="cbebd-131">编写资源脚本</span><span class="sxs-lookup"><span data-stu-id="cbebd-131">Writing the resource script</span></span>

<span data-ttu-id="cbebd-132">资源脚本实现资源的逻辑。</span><span class="sxs-lookup"><span data-stu-id="cbebd-132">The resource script implements the logic of the resource.</span></span> <span data-ttu-id="cbebd-133">在此模块中必须包含三个分别名为 `Get-TargetResource`、`Set-TargetResource` 和 `Test-TargetResource` 的函数。</span><span class="sxs-lookup"><span data-stu-id="cbebd-133">In this module, you must include three functions called `Get-TargetResource`, `Set-TargetResource`, and `Test-TargetResource`.</span></span> <span data-ttu-id="cbebd-134">三个函数采用的参数集都必须与你为资源创建的 MOF 架构中定义的属性集一致。</span><span class="sxs-lookup"><span data-stu-id="cbebd-134">All three functions must take a parameter set that is identical to the set of properties defined in the MOF schema that you created for your resource.</span></span> <span data-ttu-id="cbebd-135">在本文档中，这组属性被称为“资源属性”。</span><span class="sxs-lookup"><span data-stu-id="cbebd-135">In this document, this set of properties is referred to as the "resource properties."</span></span> <span data-ttu-id="cbebd-136">将这三个函数保存在名为 `<ResourceName>.psm1` 的文件中。</span><span class="sxs-lookup"><span data-stu-id="cbebd-136">Store these three functions in a file called `<ResourceName>.psm1`.</span></span> <span data-ttu-id="cbebd-137">在下面的示例中，函数存储在名为 `Demo_IISWebsite.psm1` 的文件中。</span><span class="sxs-lookup"><span data-stu-id="cbebd-137">In the following example, the functions are stored in a file called `Demo_IISWebsite.psm1`.</span></span>

> [!NOTE]
> <span data-ttu-id="cbebd-138">在资源上多次运行相同的配置脚本时，你应该不会收到错误报告，并且资源的状态应该与运行一次脚本的状态相同。</span><span class="sxs-lookup"><span data-stu-id="cbebd-138">When you run the same configuration script on your resource more than once, you should receive no errors and the resource should remain in the same state as running the script once.</span></span> <span data-ttu-id="cbebd-139">要达到此目的，请确保 `Get-TargetResource` 和 `Test-TargetResource` 函数没有改变资源，并且确保在具有相同参数值的序列中多次调用 `Set-TargetResource` 函数始终等效于调用其一次。</span><span class="sxs-lookup"><span data-stu-id="cbebd-139">To accomplish this, ensure that your `Get-TargetResource` and `Test-TargetResource` functions leave the resource unchanged, and that invoking the `Set-TargetResource` function more than once in a sequence with the same parameter values is always equivalent to invoking it once.</span></span>

<span data-ttu-id="cbebd-140">在 `Get-TargetResource` 函数的实现中，使用作为参数而提供的键资源属性值来检查指定资源实例的状态。</span><span class="sxs-lookup"><span data-stu-id="cbebd-140">In the `Get-TargetResource` function implementation, use the key resource property values that are provided as parameters to check the status of the specified resource instance.</span></span> <span data-ttu-id="cbebd-141">此函数必须返回列举了所有作为键的资源属性的哈希表，并返回这些属性的实际值作为对应值。</span><span class="sxs-lookup"><span data-stu-id="cbebd-141">This function must return a hash table that lists all the resource properties as keys and the actual values of these properties as the corresponding values.</span></span> <span data-ttu-id="cbebd-142">以下代码是一个示例。</span><span class="sxs-lookup"><span data-stu-id="cbebd-142">The following code provides an example.</span></span>

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance
# specified in the parameters for the target machine
function Get-TargetResource
{
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

        $getTargetResourceResult = $null;

        <#
          Insert logic that uses the mandatory parameter values to get the website and
          assign it to a variable called $Website
          Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise
        #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
            Name = $Website.Name
            Ensure = $ensureResult
            PhysicalPath = $Website.physicalPath
            State = $Website.state
            ID = $Website.id
            ApplicationPool = $Website.applicationPool
            Protocol = $Website.bindings.Collection.protocol
            Binding = $Website.bindings.Collection.bindingInformation
        }

        $getTargetResourceResult
}
```

<span data-ttu-id="cbebd-143">根据配置脚本中为资源属性指定的值，`Set-TargetResource` 必须执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="cbebd-143">Depending on the values that are specified for the resource properties in the configuration script, the `Set-TargetResource` must do one of the following:</span></span>

- <span data-ttu-id="cbebd-144">创建一个新网站</span><span class="sxs-lookup"><span data-stu-id="cbebd-144">Create a new website</span></span>
- <span data-ttu-id="cbebd-145">更新现有网站</span><span class="sxs-lookup"><span data-stu-id="cbebd-145">Update an existing website</span></span>
- <span data-ttu-id="cbebd-146">删除现有网站</span><span class="sxs-lookup"><span data-stu-id="cbebd-146">Delete an existing website</span></span>

<span data-ttu-id="cbebd-147">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="cbebd-147">The following example illustrates this.</span></span>

```powershell
# The Set-TargetResource function is used to create, delete or configure a website on the target machine.
function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

    <#
        If Ensure is set to "Present" and the website specified in the mandatory input parameters
          does not exist, then create it using the specified parameter values
        Else, if Ensure is set to "Present" and the website does exist, then update its properties
          to match the values provided in the non-mandatory parameter values
        Else, if Ensure is set to "Absent" and the website does not exist, then do nothing
        Else, if Ensure is set to "Absent" and the website does exist, then delete the website
    #>
}
```

<span data-ttu-id="cbebd-148">最后，`Test-TargetResource` 函数必须采用与 `Get-TargetResource` 和 `Set-TargetResource` 相同的参数集。</span><span class="sxs-lookup"><span data-stu-id="cbebd-148">Finally, the `Test-TargetResource` function must take the same parameter set as `Get-TargetResource` and `Set-TargetResource`.</span></span> <span data-ttu-id="cbebd-149">在 `Test-TargetResource` 的实现中，检查在键参数中指定的资源实例的状态。</span><span class="sxs-lookup"><span data-stu-id="cbebd-149">In your implementation of `Test-TargetResource`, check the status of the resource instance that is specified in the key parameters.</span></span> <span data-ttu-id="cbebd-150">如果资源实例的实际状态与在参数集中指定的值不匹配，则返回 `$false`。</span><span class="sxs-lookup"><span data-stu-id="cbebd-150">If the actual status of the resource instance does not match the values specified in the parameter set, return `$false`.</span></span> <span data-ttu-id="cbebd-151">否则，返回 `$true`。</span><span class="sxs-lookup"><span data-stu-id="cbebd-151">Otherwise, return `$true`.</span></span>

<span data-ttu-id="cbebd-152">下面的代码实现 `Test-TargetResource` 函数。</span><span class="sxs-lookup"><span data-stu-id="cbebd-152">The following code implements the `Test-TargetResource` function.</span></span>

```powershell
function Test-TargetResource
{
    [CmdletBinding()]
    [OutputType([System.Boolean])]
    param
    (
        [ValidateSet("Present","Absent")]
        [System.String]
        $Ensure,

        [parameter(Mandatory = $true)]
        [System.String]
        $Name,

        [parameter(Mandatory = $true)]
        [System.String]
        $PhysicalPath,

        [ValidateSet("Started","Stopped")]
        [System.String]
        $State,

        [System.String[]]
        $Protocol,

        [System.String[]]
        $BindingData,

        [System.String]
        $ApplicationPool
    )

    # Get the current state
    $currentState = Get-TargetResource -Ensure $Ensure -Name $Name -PhysicalPath $PhysicalPath -State $State -ApplicationPool $ApplicationPool -BindingInfo $BindingInfo -Protocol $Protocol

    # Write-Verbose "Use this cmdlet to deliver information about command processing."

    # Write-Debug "Use this cmdlet to write debug information while troubleshooting."

    # Include logic to
    $result = [System.Boolean]
    # Add logic to test whether the website is present and its status matches the supplied
    # parameter values. If it does, return true. If it does not, return false.
    $result
}
```

> [!NOTE]
> <span data-ttu-id="cbebd-153">为方便调试，请在上述三个函数的实现中使用 `Write-Verbose` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cbebd-153">For easier debugging, use the `Write-Verbose` cmdlet in your implementation of the previous three functions.</span></span> <span data-ttu-id="cbebd-154">此 cmdlet 将文本写入详细消息流。</span><span class="sxs-lookup"><span data-stu-id="cbebd-154">This cmdlet writes text to the verbose message stream.</span></span> <span data-ttu-id="cbebd-155">默认情况下，不显示详细消息流，但你可以通过更改 **$VerbosePreference** 变量的值或通过在 DSC cmdlets = new 中使用 **Verbose** 参数来显示该流。</span><span class="sxs-lookup"><span data-stu-id="cbebd-155">By default, the verbose message stream is not displayed, but you can display it by changing the value of the **$VerbosePreference** variable or by using the **Verbose** parameter in the DSC cmdlets = new.</span></span>

### <a name="creating-the-module-manifest"></a><span data-ttu-id="cbebd-156">创建模块清单</span><span class="sxs-lookup"><span data-stu-id="cbebd-156">Creating the module manifest</span></span>

<span data-ttu-id="cbebd-157">最后，使用 `New-ModuleManifest` cmdlet 为自定义资源模块定义一个 `<ResourceName>.psd1` 文件。</span><span class="sxs-lookup"><span data-stu-id="cbebd-157">Finally, use the `New-ModuleManifest` cmdlet to define a `<ResourceName>.psd1` file for your custom resource module.</span></span> <span data-ttu-id="cbebd-158">调用此 cmdlet 时，引用上一节中所介绍的脚本模块 (.psm1) 文件。</span><span class="sxs-lookup"><span data-stu-id="cbebd-158">When you invoke this cmdlet, reference the script module (.psm1) file described in the previous section.</span></span> <span data-ttu-id="cbebd-159">将 `Get-TargetResource`、`Set-TargetResource` 和 `Test-TargetResource` 包括在要导出的函数列表中。</span><span class="sxs-lookup"><span data-stu-id="cbebd-159">Include `Get-TargetResource`, `Set-TargetResource`, and `Test-TargetResource` in the list of functions to export.</span></span> <span data-ttu-id="cbebd-160">以下是一个示例清单文件。</span><span class="sxs-lookup"><span data-stu-id="cbebd-160">Following is an example manifest file.</span></span>

```powershell
# Module manifest for module 'Demo.IIS.Website'
#
# Generated on: 1/10/2013
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '6AB5ED33-E923-41d8-A3A4-5ADDA2B301DE'

# Author of this module
Author = 'Contoso'

# Company or vendor of this module
CompanyName = 'Contoso'

# Copyright statement for this module
Copyright = 'Contoso. All rights reserved.'

# Description of the functionality provided by this module
Description = 'This Module is used to support the creation and configuration of IIS Websites through Get, Set and Test API on the DSC managed nodes.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '4.0'

# Minimum version of the common language runtime (CLR) required by this module
CLRVersion = '4.0'

# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @("WebAdministration")

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @("Demo_IISWebsite.psm1")

# Functions to export from this module
FunctionsToExport = @("Get-TargetResource", "Set-TargetResource", "Test-TargetResource")

# Cmdlets to export from this module
#CmdletsToExport = '*'

# HelpInfo URI of this module
# HelpInfoURI = ''
}
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="cbebd-161">支持 PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="cbebd-161">Supporting PsDscRunAsCredential</span></span>

> [!Note]
> <span data-ttu-id="cbebd-162">PsDscRunAsCredential 在 PowerShell 5.0 及更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="cbebd-162">**PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="cbebd-163">可以在 [DSC 配置](../configurations/configurations.md)资源块中使用 PsDscRunAsCredential 属性，以指定应使用指定的一组凭据运行资源。</span><span class="sxs-lookup"><span data-stu-id="cbebd-163">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span> <span data-ttu-id="cbebd-164">有关详细信息，请参阅[使用用户凭据运行 DSC](../configurations/runAsUser.md)。</span><span class="sxs-lookup"><span data-stu-id="cbebd-164">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="cbebd-165">若要从自定义资源访问用户上下文，可以使用自动变量 `$PsDscContext`。</span><span class="sxs-lookup"><span data-stu-id="cbebd-165">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="cbebd-166">例如，下面的代码会将用于运行资源的用户上下文写入详细输出流：</span><span class="sxs-lookup"><span data-stu-id="cbebd-166">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="rebooting-the-node"></a><span data-ttu-id="cbebd-167">重新启动节点</span><span class="sxs-lookup"><span data-stu-id="cbebd-167">Rebooting the Node</span></span>

<span data-ttu-id="cbebd-168">如果在 `Set-TargetResource` 函数中执行的操作需要重新启动，则可以使用全局标志告知 LCM 重新启动节点。</span><span class="sxs-lookup"><span data-stu-id="cbebd-168">If the actions taken in your `Set-TargetResource` function require a reboot, you can use a global flag to tell the LCM to reboot the Node.</span></span> <span data-ttu-id="cbebd-169">此重新启动会在 `Set-TargetResource` 函数完成之后直接进行。</span><span class="sxs-lookup"><span data-stu-id="cbebd-169">This reboot occurs directly after the `Set-TargetResource` function completes.</span></span>

<span data-ttu-id="cbebd-170">在 `Set-TargetResource` 函数中，添加以下代码行。</span><span class="sxs-lookup"><span data-stu-id="cbebd-170">Inside your `Set-TargetResource` function, add the following line of code.</span></span>

```powershell
# Include this line if the resource requires a system reboot.
$global:DSCMachineStatus = 1
```

<span data-ttu-id="cbebd-171">若要使 LCM 可重新启动节点，RebootNodeIfNeeded 标志需要设置为 `$true`。</span><span class="sxs-lookup"><span data-stu-id="cbebd-171">In order for the LCM to reboot the Node, the **RebootNodeIfNeeded** flag needs to be set to `$true`.</span></span>
<span data-ttu-id="cbebd-172">ActionAfterReboot 设置也应设置为 ContinueConfiguration（这是默认值）。</span><span class="sxs-lookup"><span data-stu-id="cbebd-172">The **ActionAfterReboot** setting should also be set to **ContinueConfiguration** , which is the default.</span></span> <span data-ttu-id="cbebd-173">有关配置 LCM 的详细信息，请参阅[配置本地配置管理器](../managing-nodes/metaConfig.md)或[配置本地配置管理器 (v4)](../managing-nodes/metaConfig4.md)。</span><span class="sxs-lookup"><span data-stu-id="cbebd-173">For more information on configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configuring the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>
