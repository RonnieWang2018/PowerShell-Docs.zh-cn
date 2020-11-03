---
description: PowerShell 中的实验性功能支持提供了一种机制，可便于实验性功能与 PowerShell 或 PowerShell 模块中的现有稳定功能共存。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 关于实验性功能
ms.openlocfilehash: fb13d605607b3f6daaba30cef9e7ee339221191c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/13/2020
ms.locfileid: "93199943"
---
# <a name="experimental-features"></a><span data-ttu-id="fa363-104">实验性功能</span><span class="sxs-lookup"><span data-stu-id="fa363-104">Experimental Features</span></span>

<span data-ttu-id="fa363-105">PowerShell 中的实验性功能支持提供了一种机制，可便于实验性功能与 PowerShell 或 PowerShell 模块中的现有稳定功能共存。</span><span class="sxs-lookup"><span data-stu-id="fa363-105">The Experimental Features support in PowerShell provides a mechanism for experimental features to coexist with existing stable features in PowerShell or PowerShell modules.</span></span>

<span data-ttu-id="fa363-106">实验性功能是指设计尚未最终确定的功能。</span><span class="sxs-lookup"><span data-stu-id="fa363-106">An experimental feature is one where the design is not finalized.</span></span> <span data-ttu-id="fa363-107">此类功能可供用户进行测试和提供反馈。</span><span class="sxs-lookup"><span data-stu-id="fa363-107">The feature is available for users to test and provide feedback.</span></span> <span data-ttu-id="fa363-108">一旦实验性功能最终确定下来，设计变更就变成了中断性变更。</span><span class="sxs-lookup"><span data-stu-id="fa363-108">Once an experimental feature is finalized, the design changes become breaking changes.</span></span> <span data-ttu-id="fa363-109">实验性功能不适合在生产环境中使用，因为允许变更成为中断性变更。</span><span class="sxs-lookup"><span data-stu-id="fa363-109">Experimental features aren't intended to be used in production since the changes are allowed to be breaking.</span></span>

<span data-ttu-id="fa363-110">默认情况下，实验功能处于禁用状态，需要由系统的用户或管理员显式启用。</span><span class="sxs-lookup"><span data-stu-id="fa363-110">Experimental features are disabled by default and need to be explicitly enabled by the user or administrator of the system.</span></span>

<span data-ttu-id="fa363-111">启用的实验性功能列在 " `powershell.config.json` `$PSHOME` 适用于所有用户的文件" 或特定用户的用户特定的配置文件中。</span><span class="sxs-lookup"><span data-stu-id="fa363-111">Enabled experimental features are listed in the `powershell.config.json` file in `$PSHOME` for all users or the user-specific configuration file for a specific user.</span></span>

> [!NOTE]
> <span data-ttu-id="fa363-112">用户配置文件中启用的实验性功能优先于系统配置文件中列出的实验性功能。</span><span class="sxs-lookup"><span data-stu-id="fa363-112">Experimental features enabled in the user configuration file take precedence over experimental features listed in the system configuration file.</span></span>

## <a name="the-experimental-attribute"></a><span data-ttu-id="fa363-113">实验特性</span><span class="sxs-lookup"><span data-stu-id="fa363-113">The Experimental Attribute</span></span>

<span data-ttu-id="fa363-114">使用 `Experimental` 属性将一些代码声明为实验性。</span><span class="sxs-lookup"><span data-stu-id="fa363-114">Use the `Experimental` attribute to declare some code as experimental.</span></span>

<span data-ttu-id="fa363-115">使用以下语法声明一个 `Experimental` 属性，该属性提供实验功能的名称和启用实验功能时要执行的操作：</span><span class="sxs-lookup"><span data-stu-id="fa363-115">Use the following syntax to declare the `Experimental` attribute providing the name of the experimental feature and the action to take if the experimental feature is enabled:</span></span>

```csharp
[Experimental(NameOfExperimentalFeature, ExperimentAction)]
```

<span data-ttu-id="fa363-116">对于模块， `NameOfExperimentalFeature` 必须遵循的形式 `<modulename>.<experimentname>` 。</span><span class="sxs-lookup"><span data-stu-id="fa363-116">For modules, the `NameOfExperimentalFeature` must follow the form of `<modulename>.<experimentname>`.</span></span> <span data-ttu-id="fa363-117">`ExperimentAction`必须指定参数，并且唯一有效值为：</span><span class="sxs-lookup"><span data-stu-id="fa363-117">The `ExperimentAction` parameter must be specified and the only valid values are:</span></span>

- <span data-ttu-id="fa363-118">`Show` 表示在启用功能的情况下显示此试验性功能</span><span class="sxs-lookup"><span data-stu-id="fa363-118">`Show` means to show this experimental feature if the feature is enabled</span></span>
- <span data-ttu-id="fa363-119">`Hide` 如果启用了该功能，则表示隐藏此试验性功能</span><span class="sxs-lookup"><span data-stu-id="fa363-119">`Hide` means to hide this experimental feature if the feature is enabled</span></span>

### <a name="declaring-experimental-features-in-modules-written-in-c"></a><span data-ttu-id="fa363-120">在用 C 语言编写的模块中声明实验性功能\#</span><span class="sxs-lookup"><span data-stu-id="fa363-120">Declaring Experimental Features in Modules Written in C\#</span></span>

<span data-ttu-id="fa363-121">要使用实验功能标志的模块作者可以通过使用属性将 cmdlet 声明为试验性 `Experimental` 。</span><span class="sxs-lookup"><span data-stu-id="fa363-121">Module authors who want to use the Experimental Feature flags can declare a cmdlet as experimental by using the `Experimental` attribute.</span></span>

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }
```

### <a name="declaring-experimental-features-in-modules-written-in-powershell"></a><span data-ttu-id="fa363-122">在用 PowerShell 编写的模块中声明实验性功能</span><span class="sxs-lookup"><span data-stu-id="fa363-122">Declaring Experimental Features in Modules written in PowerShell</span></span>

<span data-ttu-id="fa363-123">使用 PowerShell 编写的模块还可以使用 `Experimental` 属性声明实验性 cmdlet：</span><span class="sxs-lookup"><span data-stu-id="fa363-123">Module written in PowerShell can also use the `Experimental` attribute to declare experimental cmdlets:</span></span>

```powershell
function Enable-SSHRemoting {
    [Experimental("MyRemoting.PSSSHRemoting", "Show")]
    [CmdletBinding()]
    param()
    ...
}
```

### <a name="mutually-exclusive-experimental-features"></a><span data-ttu-id="fa363-124">相互排斥的实验性功能</span><span class="sxs-lookup"><span data-stu-id="fa363-124">Mutually Exclusive Experimental Features</span></span>

<span data-ttu-id="fa363-125">在某些情况下，实验功能不能与现有功能或其他实验功能并存。</span><span class="sxs-lookup"><span data-stu-id="fa363-125">There are cases where an experimental feature cannot co-exist side-by-side with an existing feature or another experimental feature.</span></span>

<span data-ttu-id="fa363-126">例如，可以有一个可替代现有 cmdlet 的试验性 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fa363-126">For example, you can have an experimental cmdlet that overrides an existing cmdlet.</span></span> <span data-ttu-id="fa363-127">这两个版本不能并行共存。</span><span class="sxs-lookup"><span data-stu-id="fa363-127">The two versions can't coexist side by side.</span></span> <span data-ttu-id="fa363-128">`ExperimentAction.Hide`设置允许一次只启用这两个 cmdlet 之一。</span><span class="sxs-lookup"><span data-stu-id="fa363-128">The `ExperimentAction.Hide` setting allows only one of the two cmdlets to be enabled at one time.</span></span>

<span data-ttu-id="fa363-129">在此示例中，我们将创建一个新的实验性 `Invoke-WebRequest` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fa363-129">In this example, we create a new experimental `Invoke-WebRequest` cmdlet.</span></span>
<span data-ttu-id="fa363-130">`InvokeWebRequestCommand` 包含非试验性实现。</span><span class="sxs-lookup"><span data-stu-id="fa363-130">`InvokeWebRequestCommand` contains the non-experimental implementation.</span></span>
<span data-ttu-id="fa363-131">`InvokeWebRequestCommandV2` 包含 cmdlet 的实验版本。</span><span class="sxs-lookup"><span data-stu-id="fa363-131">`InvokeWebRequestCommandV2` contains the experimental version of the cmdlet.</span></span>

<span data-ttu-id="fa363-132">使用 `ExperimentAction.Hide` 将只允许一次启用这两项功能之一：</span><span class="sxs-lookup"><span data-stu-id="fa363-132">The use of `ExperimentAction.Hide` will allow only one of the two features to be enabled at one time:</span></span>

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }

[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Hide)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommand : WebCmdletBase { ... }
```

<span data-ttu-id="fa363-133">`MyWebCmdlets.PSWebCmdletV2`启用实验功能后，将 `InvokeWebRequestCommand` 隐藏现有实现，并提供的 `InvokeWebRequestCommandV2` 实现 `Invoke-WebRequest` 。</span><span class="sxs-lookup"><span data-stu-id="fa363-133">When the `MyWebCmdlets.PSWebCmdletV2` experimental feature is enabled, the existing `InvokeWebRequestCommand` implementation is hidden and the `InvokeWebRequestCommandV2` provides the implementation of `Invoke-WebRequest`.</span></span>

<span data-ttu-id="fa363-134">这样，用户就可以试用新的 cmdlet 并提供反馈，并在需要时恢复到非实验版本。</span><span class="sxs-lookup"><span data-stu-id="fa363-134">This allows users to try out the new cmdlet and provide feedback then revert to the non-experimental version when needed.</span></span>

### <a name="experimental-parameters-in-cmdlets"></a><span data-ttu-id="fa363-135">Cmdlet 中的实验参数</span><span class="sxs-lookup"><span data-stu-id="fa363-135">Experimental Parameters in Cmdlets</span></span>

<span data-ttu-id="fa363-136">`Experimental`特性还可以应用于单个参数。</span><span class="sxs-lookup"><span data-stu-id="fa363-136">The `Experimental` attribute can also be applied to individual parameters.</span></span> <span data-ttu-id="fa363-137">这允许您为现有 cmdlet （而不是全新的 cmdlet）创建实验参数集。</span><span class="sxs-lookup"><span data-stu-id="fa363-137">This allows you to create an experimental set of parameters for an existing cmdlet rather than an entirely new cmdlet.</span></span>

<span data-ttu-id="fa363-138">下面是 c # 中的一个示例：</span><span class="sxs-lookup"><span data-stu-id="fa363-138">Here is an example in C#:</span></span>

```csharp
[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Show)]
[Parameter(ParameterSet = "NewCompilation")]
public CompilationParameters CompileParameters { ... }

[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Hide)]
[Parameter()]
public CodeDom CodeDom { ... }
```

<span data-ttu-id="fa363-139">下面是 PowerShell 脚本中的其他示例：</span><span class="sxs-lookup"><span data-stu-id="fa363-139">Here is a different example in PowerShell script:</span></span>

```powershell
param(
    [Experimental("MyModule.PSNewFeature", "Show")]
    [string] $NewName,

    [Experimental("MyModule.PSNewFeature", "Hide")]
    [string] $OldName
)
```

## <a name="checking-if-an-experimental-feature-is-enabled"></a><span data-ttu-id="fa363-140">检查试验性功能是否已启用</span><span class="sxs-lookup"><span data-stu-id="fa363-140">Checking if an Experimental Feature is Enabled</span></span>

<span data-ttu-id="fa363-141">在代码中，需要检查是否已启用实验功能，然后再采取适当的措施。</span><span class="sxs-lookup"><span data-stu-id="fa363-141">In your code, you will need to check if your experimental feature is enabled before taking appropriate action.</span></span> <span data-ttu-id="fa363-142">您可以使用类的静态方法来确定是否启用了实验功能 `IsEnabled()` `System.Management.Automation.ExperimentalFeature` 。</span><span class="sxs-lookup"><span data-stu-id="fa363-142">You can determine if an experimental feature is enabled using the static `IsEnabled()` method on the `System.Management.Automation.ExperimentalFeature` class.</span></span>

<span data-ttu-id="fa363-143">下面是 c # 中的一个示例：</span><span class="sxs-lookup"><span data-stu-id="fa363-143">Here is an example in C#:</span></span>

```csharp
if (ExperimentalFeature.IsEnabled("MyModule.MyExperimentalFeature"))
{
   // code specific to the experimental feature
}
```

<span data-ttu-id="fa363-144">下面是 PowerShell 脚本中的一个示例：</span><span class="sxs-lookup"><span data-stu-id="fa363-144">Here is an example in PowerShell script:</span></span>

```powershell
if ([ExperimentalFeature]::IsEnabled("MyModule.MyExperimentalFeature"))
{
  # code specific to the experimental feature
}
```

## <a name="see-also"></a><span data-ttu-id="fa363-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa363-145">See also</span></span>

[<span data-ttu-id="fa363-146">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="fa363-146">Enable-ExperimentalFeature</span></span>](xref:Microsoft.PowerShell.Core.Enable-ExperimentalFeature)

[<span data-ttu-id="fa363-147">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="fa363-147">Disable-ExperimentalFeature</span></span>](xref:Microsoft.PowerShell.Core.Disable-ExperimentalFeature)

[<span data-ttu-id="fa363-148">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="fa363-148">Get-ExperimentalFeature</span></span>](xref:Microsoft.PowerShell.Core.Get-ExperimentalFeature)

