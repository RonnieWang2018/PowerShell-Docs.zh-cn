---
description: 描述可与任何 cmdlet 一起使用的参数。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_CommonParameters
ms.openlocfilehash: 441154d60440024ebea9d5047430f6e9209d8f04
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/13/2020
ms.locfileid: "93200327"
---
# <a name="about-commonparameters"></a><span data-ttu-id="f43dc-104">关于 CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f43dc-104">About CommonParameters</span></span>

## <a name="short-description"></a><span data-ttu-id="f43dc-105">简短说明</span><span class="sxs-lookup"><span data-stu-id="f43dc-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="f43dc-106">描述可与任何 cmdlet 一起使用的参数。</span><span class="sxs-lookup"><span data-stu-id="f43dc-106">Describes the parameters that can be used with any cmdlet.</span></span>

## <a name="long-description"></a><span data-ttu-id="f43dc-107">详细说明</span><span class="sxs-lookup"><span data-stu-id="f43dc-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="f43dc-108">常见参数是一组 cmdlet 参数，可用于任何 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f43dc-108">The common parameters are a set of cmdlet parameters that you can use with any cmdlet.</span></span> <span data-ttu-id="f43dc-109">它们是由 PowerShell 实现的，而不是由 cmdlet 开发人员实现的，并且可自动用于任何 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f43dc-109">They're implemented by PowerShell, not by the cmdlet developer, and they're automatically available to any cmdlet.</span></span>

<span data-ttu-id="f43dc-110">可以将通用参数与任何 cmdlet 一起使用，但它们可能对所有 cmdlet 不起作用。</span><span class="sxs-lookup"><span data-stu-id="f43dc-110">You can use the common parameters with any cmdlet, but they might not have an effect on all cmdlets.</span></span> <span data-ttu-id="f43dc-111">例如，如果某个 cmdlet 没有生成任何详细输出，则使用 **verbose** common 参数不起作用。</span><span class="sxs-lookup"><span data-stu-id="f43dc-111">For example, if a cmdlet doesn't generate any verbose output, using the **Verbose** common parameter has no effect.</span></span>

<span data-ttu-id="f43dc-112">通用参数还可用于使用 **CmdletBinding** 特性或 **Parameter** 特性的高级函数。</span><span class="sxs-lookup"><span data-stu-id="f43dc-112">The common parameters are also available on advanced functions that use the **CmdletBinding** attribute or the **Parameter** attribute.</span></span>

<span data-ttu-id="f43dc-113">几个通用参数会替代使用 PowerShell 首选项变量设置的系统默认值或首选项。</span><span class="sxs-lookup"><span data-stu-id="f43dc-113">Several common parameters override system defaults or preferences that you set by using the PowerShell preference variables.</span></span> <span data-ttu-id="f43dc-114">与首选项变量不同，common 参数仅影响使用这些参数的命令。</span><span class="sxs-lookup"><span data-stu-id="f43dc-114">Unlike the preference variables, the common parameters affect only the commands in which they're used.</span></span>

<span data-ttu-id="f43dc-115">有关详细信息，请参阅 [about_Preference_Variables](./about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="f43dc-115">For more information, see [about_Preference_Variables](./about_Preference_Variables.md).</span></span>

<span data-ttu-id="f43dc-116">以下列表显示了通用参数。</span><span class="sxs-lookup"><span data-stu-id="f43dc-116">The following list displays the common parameters.</span></span> <span data-ttu-id="f43dc-117">它们的别名列在括号中。</span><span class="sxs-lookup"><span data-stu-id="f43dc-117">Their aliases are listed in parentheses.</span></span>

- <span data-ttu-id="f43dc-118">**Debug** (db)</span><span class="sxs-lookup"><span data-stu-id="f43dc-118">**Debug** (db)</span></span>
- <span data-ttu-id="f43dc-119">**ErrorAction** (ea) </span><span class="sxs-lookup"><span data-stu-id="f43dc-119">**ErrorAction** (ea)</span></span>
- <span data-ttu-id="f43dc-120">**ErrorVariable** (ev) </span><span class="sxs-lookup"><span data-stu-id="f43dc-120">**ErrorVariable** (ev)</span></span>
- <span data-ttu-id="f43dc-121">**InformationAction** (infa) </span><span class="sxs-lookup"><span data-stu-id="f43dc-121">**InformationAction** (infa)</span></span>
- <span data-ttu-id="f43dc-122">**InformationVariable** (iv) </span><span class="sxs-lookup"><span data-stu-id="f43dc-122">**InformationVariable** (iv)</span></span>
- <span data-ttu-id="f43dc-123">**OutVariable** (ov-es) </span><span class="sxs-lookup"><span data-stu-id="f43dc-123">**OutVariable** (ov)</span></span>
- <span data-ttu-id="f43dc-124">**OutBuffer** (ob) </span><span class="sxs-lookup"><span data-stu-id="f43dc-124">**OutBuffer** (ob)</span></span>
- <span data-ttu-id="f43dc-125">**PipelineVariable** (pv) </span><span class="sxs-lookup"><span data-stu-id="f43dc-125">**PipelineVariable** (pv)</span></span>
- <span data-ttu-id="f43dc-126">) **详细** (vb</span><span class="sxs-lookup"><span data-stu-id="f43dc-126">**Verbose** (vb)</span></span>
- <span data-ttu-id="f43dc-127">**WarningAction** (wa) </span><span class="sxs-lookup"><span data-stu-id="f43dc-127">**WarningAction** (wa)</span></span>
- <span data-ttu-id="f43dc-128">**WarningVariable** (wv) </span><span class="sxs-lookup"><span data-stu-id="f43dc-128">**WarningVariable** (wv)</span></span>

<span data-ttu-id="f43dc-129">**操作** 参数为 **ActionPreference** 类型值。</span><span class="sxs-lookup"><span data-stu-id="f43dc-129">The **Action** parameters are **ActionPreference** type values.</span></span>
<span data-ttu-id="f43dc-130">**ActionPreference** 是具有以下值的枚举：</span><span class="sxs-lookup"><span data-stu-id="f43dc-130">**ActionPreference** is an enumeration with the following values:</span></span>

| <span data-ttu-id="f43dc-131">名称</span><span class="sxs-lookup"><span data-stu-id="f43dc-131">Name</span></span>             | <span data-ttu-id="f43dc-132">Value</span><span class="sxs-lookup"><span data-stu-id="f43dc-132">Value</span></span> |
|------------------|-------|
| <span data-ttu-id="f43dc-133">挂起</span><span class="sxs-lookup"><span data-stu-id="f43dc-133">Suspend</span></span>          | <span data-ttu-id="f43dc-134">5</span><span class="sxs-lookup"><span data-stu-id="f43dc-134">5</span></span>     |
| <span data-ttu-id="f43dc-135">忽略</span><span class="sxs-lookup"><span data-stu-id="f43dc-135">Ignore</span></span>           | <span data-ttu-id="f43dc-136">4</span><span class="sxs-lookup"><span data-stu-id="f43dc-136">4</span></span>     |
| <span data-ttu-id="f43dc-137">查询</span><span class="sxs-lookup"><span data-stu-id="f43dc-137">Inquire</span></span>          | <span data-ttu-id="f43dc-138">3</span><span class="sxs-lookup"><span data-stu-id="f43dc-138">3</span></span>     |
| <span data-ttu-id="f43dc-139">继续</span><span class="sxs-lookup"><span data-stu-id="f43dc-139">Continue</span></span>         | <span data-ttu-id="f43dc-140">2</span><span class="sxs-lookup"><span data-stu-id="f43dc-140">2</span></span>     |
| <span data-ttu-id="f43dc-141">停止</span><span class="sxs-lookup"><span data-stu-id="f43dc-141">Stop</span></span>             | <span data-ttu-id="f43dc-142">1</span><span class="sxs-lookup"><span data-stu-id="f43dc-142">1</span></span>     |
| <span data-ttu-id="f43dc-143">SilentlyContinue</span><span class="sxs-lookup"><span data-stu-id="f43dc-143">SilentlyContinue</span></span> | <span data-ttu-id="f43dc-144">0</span><span class="sxs-lookup"><span data-stu-id="f43dc-144">0</span></span>     |

<span data-ttu-id="f43dc-145">可以将该名称或值与参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="f43dc-145">You may use the name or the value with the parameter.</span></span>

<span data-ttu-id="f43dc-146">除通用参数外，许多 cmdlet 还提供风险缓解参数。</span><span class="sxs-lookup"><span data-stu-id="f43dc-146">In addition to the common parameters, many cmdlets offer risk mitigation parameters.</span></span> <span data-ttu-id="f43dc-147">涉及系统风险或用户数据的 cmdlet 通常提供这些参数。</span><span class="sxs-lookup"><span data-stu-id="f43dc-147">Cmdlets that involve risk to the system or to user data usually offer these parameters.</span></span>

<span data-ttu-id="f43dc-148">风险缓解参数包括：</span><span class="sxs-lookup"><span data-stu-id="f43dc-148">The risk mitigation parameters are:</span></span>

- <span data-ttu-id="f43dc-149">**WhatIf** (wi) </span><span class="sxs-lookup"><span data-stu-id="f43dc-149">**WhatIf** (wi)</span></span>
- <span data-ttu-id="f43dc-150">**确认** (cf) </span><span class="sxs-lookup"><span data-stu-id="f43dc-150">**Confirm** (cf)</span></span>

### <a name="common-parameter-descriptions"></a><span data-ttu-id="f43dc-151">常见参数说明</span><span class="sxs-lookup"><span data-stu-id="f43dc-151">COMMON PARAMETER DESCRIPTIONS</span></span>

#### <a name="debug"></a><span data-ttu-id="f43dc-152">调试</span><span class="sxs-lookup"><span data-stu-id="f43dc-152">Debug</span></span>

<span data-ttu-id="f43dc-153">显示有关命令所执行操作的程序员级别的详细信息。</span><span class="sxs-lookup"><span data-stu-id="f43dc-153">Displays programmer-level detail about the operation done by the command.</span></span> <span data-ttu-id="f43dc-154">仅当命令生成调试消息时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="f43dc-154">This parameter works only when the command generates a debugging message.</span></span> <span data-ttu-id="f43dc-155">例如，当命令包含 cmdlet 时，此参数有效 `Write-Debug` 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-155">For example, this parameter works when a command contains the `Write-Debug` cmdlet.</span></span>

```yaml
Type: SwitchParameter
Aliases: db

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="f43dc-156">默认情况下，调试消息不会显示，因为变量的值 `$DebugPreference` 为 **SilentlyContinue** 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-156">By default, debugging messages aren't displayed because the value of the `$DebugPreference` variable is **SilentlyContinue** .</span></span>

<span data-ttu-id="f43dc-157">在交互模式下， **Debug** 参数会重写 `$DebugPreference` 当前命令的变量值，并将的值设置 `$DebugPreference` 为 **Inquire** 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-157">In interactive mode, the **Debug** parameter overrides the value of the `$DebugPreference` variable for the current command, setting the value of `$DebugPreference` to **Inquire** .</span></span>

<span data-ttu-id="f43dc-158">在非交互模式下， **Debug** 参数会重写 `$DebugPreference` 当前命令的变量值，并将的值设置 `$DebugPreference` 为 **Continue** 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-158">In non-interactive mode, the **Debug** parameter overrides the value of the `$DebugPreference` variable for the current command, setting the value of `$DebugPreference` to **Continue** .</span></span>

<span data-ttu-id="f43dc-159">`-Debug:$true` 与的效果相同 `-Debug` 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-159">`-Debug:$true` has the same effect as `-Debug`.</span></span> <span data-ttu-id="f43dc-160">用于 `-Debug:$false` 禁止在 `$DebugPreference` 不 **SilentlyContinue** （这是默认值）时显示调试消息。</span><span class="sxs-lookup"><span data-stu-id="f43dc-160">Use `-Debug:$false` to suppress the display of debugging messages when `$DebugPreference` isn't **SilentlyContinue** , which is the default.</span></span>

#### <a name="erroraction"></a><span data-ttu-id="f43dc-161">ErrorAction</span><span class="sxs-lookup"><span data-stu-id="f43dc-161">ErrorAction</span></span>

<span data-ttu-id="f43dc-162">确定 cmdlet 如何响应命令中的非终止错误。</span><span class="sxs-lookup"><span data-stu-id="f43dc-162">Determines how the cmdlet responds to a non-terminating error from the command.</span></span>
<span data-ttu-id="f43dc-163">此参数仅在命令生成非终止错误（如 cmdlet 中的错误）时才起作用 `Write-Error` 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-163">This parameter works only when the command generates a non-terminating error, such as those from the `Write-Error` cmdlet.</span></span>

```yaml
Type: ActionPreference
Aliases: ea
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="f43dc-164">**ErrorAction** 参数将重写 `$ErrorActionPreference` 当前命令的变量值。</span><span class="sxs-lookup"><span data-stu-id="f43dc-164">The **ErrorAction** parameter overrides the value of the `$ErrorActionPreference` variable for the current command.</span></span> <span data-ttu-id="f43dc-165">由于变量的默认值 `$ErrorActionPreference` 为 **Continue** ，将显示错误消息并继续执行，除非使用 **ErrorAction** 参数。</span><span class="sxs-lookup"><span data-stu-id="f43dc-165">Because the default value of the `$ErrorActionPreference` variable is **Continue** , error messages are displayed and execution continues unless you use the **ErrorAction** parameter.</span></span>

<span data-ttu-id="f43dc-166">**ErrorAction** 参数不会影响终止错误 (如缺少数据、无效的参数或权限不足) 阻止命令成功完成。</span><span class="sxs-lookup"><span data-stu-id="f43dc-166">The **ErrorAction** parameter has no effect on terminating errors (such as missing data, parameters that aren't valid, or insufficient permissions) that prevent a command from completing successfully.</span></span>

<span data-ttu-id="f43dc-167">`-ErrorAction:Continue` 显示错误消息并继续执行命令。</span><span class="sxs-lookup"><span data-stu-id="f43dc-167">`-ErrorAction:Continue` display the error message and continues executing the command.</span></span> <span data-ttu-id="f43dc-168">`Continue` 为默认值。</span><span class="sxs-lookup"><span data-stu-id="f43dc-168">`Continue` is the default.</span></span>

<span data-ttu-id="f43dc-169">`-ErrorAction:Ignore` 禁止显示错误消息并继续执行命令。</span><span class="sxs-lookup"><span data-stu-id="f43dc-169">`-ErrorAction:Ignore` suppresses the error message and continues executing the command.</span></span> <span data-ttu-id="f43dc-170">与 **SilentlyContinue** 不同， **Ignore** 不会将错误消息添加到 `$Error` 自动变量。</span><span class="sxs-lookup"><span data-stu-id="f43dc-170">Unlike **SilentlyContinue** , **Ignore** doesn't add the error message to the `$Error` automatic variable.</span></span> <span data-ttu-id="f43dc-171">在 PowerShell 3.0 中引入了 **Ignore** 值。</span><span class="sxs-lookup"><span data-stu-id="f43dc-171">The **Ignore** value is introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="f43dc-172">`-ErrorAction:Inquire` 显示错误消息并提示您进行确认，然后再继续执行。</span><span class="sxs-lookup"><span data-stu-id="f43dc-172">`-ErrorAction:Inquire` displays the error message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="f43dc-173">此值很少使用。</span><span class="sxs-lookup"><span data-stu-id="f43dc-173">This value is rarely used.</span></span>

<span data-ttu-id="f43dc-174">`-ErrorAction:SilentlyContinue` 禁止显示错误消息并继续执行命令。</span><span class="sxs-lookup"><span data-stu-id="f43dc-174">`-ErrorAction:SilentlyContinue` suppresses the error message and continues executing the command.</span></span>

<span data-ttu-id="f43dc-175">`-ErrorAction:Stop` 显示错误消息并停止执行命令。</span><span class="sxs-lookup"><span data-stu-id="f43dc-175">`-ErrorAction:Stop` displays the error message and stops executing the command.</span></span>

<span data-ttu-id="f43dc-176">`-ErrorAction:Suspend` 仅适用于 PowerShell 6 和更高版本中不支持的工作流。</span><span class="sxs-lookup"><span data-stu-id="f43dc-176">`-ErrorAction:Suspend` is only available for workflows which aren't supported in PowerShell 6 and beyond.</span></span>

> [!NOTE]
> <span data-ttu-id="f43dc-177">当 **ErrorAction** 在 `$ErrorAction` 命令中使用参数来运行脚本或函数时，ErrorAction 参数将重写，但不会替换首选项变量的值。</span><span class="sxs-lookup"><span data-stu-id="f43dc-177">The **ErrorAction** parameter overrides, but does not replace the value of the `$ErrorAction` preference variable when the parameter is used in a command to run a script or function.</span></span>

#### <a name="errorvariable"></a><span data-ttu-id="f43dc-178">ErrorVariable</span><span class="sxs-lookup"><span data-stu-id="f43dc-178">ErrorVariable</span></span>

<span data-ttu-id="f43dc-179">**ErrorVariable** 在指定变量和自动变量中存储有关命令的错误消息 `$Error` 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-179">**ErrorVariable** stores error messages about the command in the specified variable and in the `$Error` automatic variable.</span></span> <span data-ttu-id="f43dc-180">有关详细信息，请参阅 [about_Automatic_Variables](about_Automatic_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="f43dc-180">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md)</span></span>

```yaml
Type: String
Aliases: ev

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="f43dc-181">默认情况下，新的错误消息将覆盖变量中已存储的错误消息。</span><span class="sxs-lookup"><span data-stu-id="f43dc-181">By default, new error messages overwrite error messages that are already stored in the variable.</span></span> <span data-ttu-id="f43dc-182">若要将错误消息追加到变量内容，请在变量名之前键入一个加号 (`+`) 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-182">To append the error message to the variable content, type a plus sign (`+`) before the variable name.</span></span>

<span data-ttu-id="f43dc-183">例如，下面的命令创建 `$a` 变量，然后在其中存储任何错误：</span><span class="sxs-lookup"><span data-stu-id="f43dc-183">For example, the following command creates the `$a` variable and then stores any errors in it:</span></span>

```powershell
Get-Process -Id 6 -ErrorVariable a
```

<span data-ttu-id="f43dc-184">下面的命令将所有错误消息添加到 `$a` 变量：</span><span class="sxs-lookup"><span data-stu-id="f43dc-184">The following command adds any error messages to the `$a` variable:</span></span>

```powershell
Get-Process -Id 2 -ErrorVariable +a
```

<span data-ttu-id="f43dc-185">以下命令显示的内容 `$a` ：</span><span class="sxs-lookup"><span data-stu-id="f43dc-185">The following command displays the contents of `$a`:</span></span>

```powershell
$a
```

<span data-ttu-id="f43dc-186">可以使用此参数来创建一个变量，该变量只包含来自特定命令的错误消息，不会影响 `$Error` 自动变量的行为。</span><span class="sxs-lookup"><span data-stu-id="f43dc-186">You can use this parameter to create a variable that contains only error messages from specific commands and does not affect the behavior of the `$Error` automatic variable.</span></span> <span data-ttu-id="f43dc-187">`$Error`自动变量包含会话中所有命令的错误消息。</span><span class="sxs-lookup"><span data-stu-id="f43dc-187">The `$Error` automatic variable contains error messages from all the commands in the session.</span></span> <span data-ttu-id="f43dc-188">您可以使用数组表示法（如 `$a[0]` 或） `$error[1,2]` 来引用变量中存储的特定错误。</span><span class="sxs-lookup"><span data-stu-id="f43dc-188">You can use array notation, such as `$a[0]` or `$error[1,2]` to refer to specific errors stored in the variables.</span></span>

> [!NOTE]
> <span data-ttu-id="f43dc-189">自定义错误变量包含命令生成的所有错误，包括调用嵌套函数或脚本的错误。</span><span class="sxs-lookup"><span data-stu-id="f43dc-189">The custom error variable contains all errors generated by the command, including errors from calls to nested functions or scripts.</span></span>

#### <a name="informationaction"></a><span data-ttu-id="f43dc-190">InformationAction</span><span class="sxs-lookup"><span data-stu-id="f43dc-190">InformationAction</span></span>

<span data-ttu-id="f43dc-191">在 PowerShell 5.0 中引入。</span><span class="sxs-lookup"><span data-stu-id="f43dc-191">Introduced in PowerShell 5.0.</span></span> <span data-ttu-id="f43dc-192">在使用该参数的命令或脚本内， **InformationAction** common 参数将覆盖 `$InformationPreference` 首选项变量的值，默认情况下，该参数设置为 **SilentlyContinue** 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-192">Within the command or script in which it's used, the **InformationAction** common parameter overrides the value of the `$InformationPreference` preference variable, which by default is set to **SilentlyContinue** .</span></span> <span data-ttu-id="f43dc-193">`Write-Information`在带有 **InformationAction** 的脚本中使用时， `Write-Information` 会根据 **InformationAction** 参数的值来显示值。</span><span class="sxs-lookup"><span data-stu-id="f43dc-193">When you use `Write-Information` in a script with **InformationAction** , `Write-Information` values are shown depending on the value of the **InformationAction** parameter.</span></span> <span data-ttu-id="f43dc-194">有关的详细信息 `$InformationPreference` ，请参阅 [about_Preference_Variables](./about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="f43dc-194">For more information about `$InformationPreference`, see [about_Preference_Variables](./about_Preference_Variables.md).</span></span>

```yaml
Type: ActionPreference
Aliases: ia
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="f43dc-195">`-InformationAction:Stop` 在命令出现时停止命令或脚本 `Write-Information` 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-195">`-InformationAction:Stop` stops a command or script at an occurrence of the `Write-Information` command.</span></span>

<span data-ttu-id="f43dc-196">`-InformationAction:Ignore` 禁止显示信息性消息，并继续运行命令。</span><span class="sxs-lookup"><span data-stu-id="f43dc-196">`-InformationAction:Ignore` suppresses the informational message and continues running the command.</span></span> <span data-ttu-id="f43dc-197">与 **SilentlyContinue** 不同， **忽略** 完全忘记密码的信息性消息;它不会将信息性消息添加到信息流。</span><span class="sxs-lookup"><span data-stu-id="f43dc-197">Unlike **SilentlyContinue** , **Ignore** completely forgets the informational message; it doesn't add the informational message to the information stream.</span></span>

<span data-ttu-id="f43dc-198">`-InformationAction:Inquire` 显示你在命令中指定的信息性消息 `Write-Information` ，然后询问你是否要继续。</span><span class="sxs-lookup"><span data-stu-id="f43dc-198">`-InformationAction:Inquire` displays the informational message that you specify in a `Write-Information` command, then asks whether you want to continue.</span></span>

<span data-ttu-id="f43dc-199">`-InformationAction:Continue` 显示信息性消息，并继续运行。</span><span class="sxs-lookup"><span data-stu-id="f43dc-199">`-InformationAction:Continue` displays the informational message, and continues running.</span></span>

<span data-ttu-id="f43dc-200">`-InformationAction:Suspend` 在 PowerShell Core 中不受支持，因为它仅适用于工作流。</span><span class="sxs-lookup"><span data-stu-id="f43dc-200">`-InformationAction:Suspend` isn't supported on PowerShell Core as it is only available for workflows.</span></span>

<span data-ttu-id="f43dc-201">`-InformationAction:SilentlyContinue` 不会影响信息性消息 (默认) 显示，脚本会继续而不会中断。</span><span class="sxs-lookup"><span data-stu-id="f43dc-201">`-InformationAction:SilentlyContinue` no effect as the informational message aren't (Default) displayed, and the script continues without interruption.</span></span>

> [!NOTE]
> <span data-ttu-id="f43dc-202">当 **InformationAction** 在 `$InformationAction` 命令中使用参数来运行脚本或函数时，InformationAction 参数将重写，但不会替换首选项变量的值。</span><span class="sxs-lookup"><span data-stu-id="f43dc-202">The **InformationAction** parameter overrides, but does not replace the value of the `$InformationAction` preference variable when the parameter is used in a command to run a script or function.</span></span>

#### <a name="informationvariable"></a><span data-ttu-id="f43dc-203">InformationVariable</span><span class="sxs-lookup"><span data-stu-id="f43dc-203">InformationVariable</span></span>

<span data-ttu-id="f43dc-204">在 PowerShell 5.0 中引入。</span><span class="sxs-lookup"><span data-stu-id="f43dc-204">Introduced in PowerShell 5.0.</span></span> <span data-ttu-id="f43dc-205">在使用它的命令或脚本中， **InformationVariable** 通用参数将通过添加命令指定的字符串存储在变量中 `Write-Information` 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-205">Within the command or script in which it's used, the **InformationVariable** common parameter stores in a variable a string that you specify by adding the `Write-Information` command.</span></span> <span data-ttu-id="f43dc-206">`Write-Information` 根据 **InformationAction** 通用参数的值显示值;如果未添加 **InformationAction** 通用参数，将根据 `Write-Information` 首选项变量的值来显示字符串 `$InformationPreference` 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-206">`Write-Information` values are shown depending on the value of the **InformationAction** common parameter; if you don't add the **InformationAction** common parameter, `Write-Information` strings are shown depending on the value of the `$InformationPreference` preference variable.</span></span> <span data-ttu-id="f43dc-207">有关的详细信息 `$InformationPreference` ，请参阅 [about_Preference_Variables](./about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="f43dc-207">For more information about `$InformationPreference`, see [about_Preference_Variables](./about_Preference_Variables.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f43dc-208">信息变量包含命令生成的所有信息消息，包括调用嵌套函数或脚本的信息消息。</span><span class="sxs-lookup"><span data-stu-id="f43dc-208">The information variable contains all information messages generated by the command, including information messages from calls to nested functions or scripts.</span></span>

```yaml
Type: String
Aliases: iv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

#### <a name="outbuffer"></a><span data-ttu-id="f43dc-209">OutBuffer</span><span class="sxs-lookup"><span data-stu-id="f43dc-209">OutBuffer</span></span>

<span data-ttu-id="f43dc-210">确定在通过管道发送任何对象之前要在缓冲区中累积的对象数。</span><span class="sxs-lookup"><span data-stu-id="f43dc-210">Determines the number of objects to accumulate in a buffer before any objects are sent through the pipeline.</span></span> <span data-ttu-id="f43dc-211">如果省略此参数，则会在生成对象时将其发送。</span><span class="sxs-lookup"><span data-stu-id="f43dc-211">If you omit this parameter, objects are sent as they're generated.</span></span>

```yaml
Type: Int32
Aliases: ob

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="f43dc-212">此资源管理参数专用于高级用户。</span><span class="sxs-lookup"><span data-stu-id="f43dc-212">This resource management parameter is designed for advanced users.</span></span> <span data-ttu-id="f43dc-213">当你使用此参数时，PowerShell 将数据批量发送到下一个 cmdlet `OutBuffer + 1` 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-213">When you use this parameter, PowerShell sends data to the next cmdlet in batches of `OutBuffer + 1`.</span></span>

<span data-ttu-id="f43dc-214">下面的示例将在 `ForEach-Object` 使用 cmdlet 的进程块之间显示替换 `Write-Host` 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-214">The following example alternates displays between to `ForEach-Object` process blocks that use the `Write-Host` cmdlet.</span></span> <span data-ttu-id="f43dc-215">显示以2个或的批次备用 `OutBuffer + 1` 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-215">The display alternates in batches of 2 or `OutBuffer + 1`.</span></span>

```powershell
1..4 | ForEach-Object {
        Write-Host "$($_): First"; $_
      } -OutBuffer 1 | ForEach-Object {
                        Write-Host "$($_): Second" }
```

```Output
1: First
2: First
1: Second
2: Second
3: First
4: First
3: Second
4: Second
```

#### <a name="outvariable"></a><span data-ttu-id="f43dc-216">OutVariable</span><span class="sxs-lookup"><span data-stu-id="f43dc-216">OutVariable</span></span>

<span data-ttu-id="f43dc-217">除了通过管道发送输出之外，还将命令中的输出对象存储在指定的变量中。</span><span class="sxs-lookup"><span data-stu-id="f43dc-217">Stores output objects from the command in the specified variable in addition to sending the output along the pipeline.</span></span>

```yaml
Type: String
Aliases: ov

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="f43dc-218">若要将输出添加到变量，而不是替换可能已存储在该处的任何输出，请在变量名之前键入一个加号 (`+`) 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-218">To add the output to the variable, instead of replacing any output that might already be stored there, type a plus sign (`+`) before the variable name.</span></span>

<span data-ttu-id="f43dc-219">例如，下面的命令创建 `$out` 变量，并在其中存储进程对象：</span><span class="sxs-lookup"><span data-stu-id="f43dc-219">For example, the following command creates the `$out` variable and stores the process object in it:</span></span>

```powershell
Get-Process PowerShell -OutVariable out
```

<span data-ttu-id="f43dc-220">以下命令将进程对象添加到 `$out` 变量：</span><span class="sxs-lookup"><span data-stu-id="f43dc-220">The following command adds the process object to the `$out` variable:</span></span>

```powershell
Get-Process iexplore -OutVariable +out
```

<span data-ttu-id="f43dc-221">以下命令显示变量的内容 `$out` ：</span><span class="sxs-lookup"><span data-stu-id="f43dc-221">The following command displays the contents of the `$out` variable:</span></span>

```powershell
$out
```

> [!NOTE]
> <span data-ttu-id="f43dc-222">**OutVariable** 参数创建的变量是 `[System.Collections.ArrayList]` 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-222">The variable created by the **OutVariable** parameter is a `[System.Collections.ArrayList]`.</span></span>

#### <a name="pipelinevariable"></a><span data-ttu-id="f43dc-223">PipelineVariable</span><span class="sxs-lookup"><span data-stu-id="f43dc-223">PipelineVariable</span></span>

<span data-ttu-id="f43dc-224">当任何命名命令流过管道时， **PipelineVariable** 将当前管道元素的值存储为变量。</span><span class="sxs-lookup"><span data-stu-id="f43dc-224">**PipelineVariable** stores the value of the current pipeline element as a variable, for any named command as it flows through the pipeline.</span></span>

```yaml
Type: String
Aliases: pv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="f43dc-225">有效值为字符串，与任何变量名相同。</span><span class="sxs-lookup"><span data-stu-id="f43dc-225">Valid values are strings, the same as for any variable names.</span></span>

<span data-ttu-id="f43dc-226">下面是 **PipelineVariable** 工作原理的示例。</span><span class="sxs-lookup"><span data-stu-id="f43dc-226">The following is an example of how **PipelineVariable** works.</span></span> <span data-ttu-id="f43dc-227">在此示例中，将 **PipelineVariable** 参数添加到 `Foreach-Object` 命令中，以将命令的结果存储在变量中。</span><span class="sxs-lookup"><span data-stu-id="f43dc-227">In this example, the **PipelineVariable** parameter is added to a `Foreach-Object` command to store the results of the command in variables.</span></span> <span data-ttu-id="f43dc-228">从1到10的数字范围进入第一个 `Foreach-Object` 命令，其结果存储在名为 **Left** 的变量中。</span><span class="sxs-lookup"><span data-stu-id="f43dc-228">A range of numbers, 1 to 10, are piped into the first `Foreach-Object` command, the results of which are stored in a variable named **Left** .</span></span>

<span data-ttu-id="f43dc-229">第一个命令的结果 `Foreach-Object` 将通过管道传递到第二个 `Foreach-Object` 命令中，该命令将筛选第一个命令返回的对象 `Foreach-Object` 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-229">The results of the first `Foreach-Object` command are piped into a second `Foreach-Object` command, which filters the objects returned by the first `Foreach-Object` command.</span></span> <span data-ttu-id="f43dc-230">第二个命令的结果存储在一个名为 **Right** 的变量中。</span><span class="sxs-lookup"><span data-stu-id="f43dc-230">The results of the second command are stored in a variable named **Right** .</span></span>

<span data-ttu-id="f43dc-231">在第三 `Foreach-Object` 个命令中，通过 `Foreach-Object` 使用乘法运算符来处理前两个管道命令的结果（由 **左侧** 和 **右侧** 的变量表示）。</span><span class="sxs-lookup"><span data-stu-id="f43dc-231">In the third `Foreach-Object` command, the results of the first two `Foreach-Object` piped commands, represented by the variables **Left** and **Right** , are processed by using a multiplication operator.</span></span> <span data-ttu-id="f43dc-232">命令指示存储在 **左** 变量和 **右** 变量中的对象相乘，并指定结果应显示为 "左范围成员 \* 右侧范围成员 = product"。</span><span class="sxs-lookup"><span data-stu-id="f43dc-232">The command instructs objects stored in the **Left** and **Right** variables to be multiplied, and specifies that the results should be displayed as "Left range member \* Right range member = product".</span></span>

```powershell
1..10 | Foreach-Object -PipelineVariable Left -Process { $_ } |
  Foreach-Object -PV Right -Process { 1..10 } |
  Foreach-Object -Process { "$Left * $Right = " + ($Left*$Right) }
```

```output
1 * 1 = 1
1 * 2 = 2
1 * 3 = 3
1 * 4 = 4
1 * 5 = 5
...
```

#### <a name="verbose"></a><span data-ttu-id="f43dc-233">“详细”</span><span class="sxs-lookup"><span data-stu-id="f43dc-233">Verbose</span></span>

<span data-ttu-id="f43dc-234">显示有关命令所执行操作的详细信息。</span><span class="sxs-lookup"><span data-stu-id="f43dc-234">Displays detailed information about the operation done by the command.</span></span> <span data-ttu-id="f43dc-235">此信息类似于跟踪或事务日志中的信息。</span><span class="sxs-lookup"><span data-stu-id="f43dc-235">This information resembles the information in a trace or in a transaction log.</span></span> <span data-ttu-id="f43dc-236">仅当命令生成详细消息时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="f43dc-236">This parameter works only when the command generates a verbose message.</span></span> <span data-ttu-id="f43dc-237">例如，当命令包含 cmdlet 时，此参数有效 `Write-Verbose` 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-237">For example, this parameter works when a command contains the `Write-Verbose` cmdlet.</span></span>

```yaml
Type: SwitchParameter
Aliases: vb

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="f43dc-238">**Verbose** 参数重写 `$VerbosePreference` 当前命令的变量值。</span><span class="sxs-lookup"><span data-stu-id="f43dc-238">The **Verbose** parameter overrides the value of the `$VerbosePreference` variable for the current command.</span></span> <span data-ttu-id="f43dc-239">由于变量的默认值 `$VerbosePreference` 为 **SilentlyContinue** ，因此默认情况下不显示详细消息。</span><span class="sxs-lookup"><span data-stu-id="f43dc-239">Because the default value of the `$VerbosePreference` variable is **SilentlyContinue** , verbose messages aren't displayed by default.</span></span>

<span data-ttu-id="f43dc-240">`-Verbose:$true` 具有与相同的效果 `-Verbose`</span><span class="sxs-lookup"><span data-stu-id="f43dc-240">`-Verbose:$true` has the same effect as `-Verbose`</span></span>

<span data-ttu-id="f43dc-241">`-Verbose:$false` 禁止显示详细消息。</span><span class="sxs-lookup"><span data-stu-id="f43dc-241">`-Verbose:$false` suppresses the display of verbose messages.</span></span> <span data-ttu-id="f43dc-242">如果的值 `$VerbosePreference` 不是 **SilentlyContinue** (默认) ，请使用此参数。</span><span class="sxs-lookup"><span data-stu-id="f43dc-242">Use this parameter when the value of `$VerbosePreference` isn't **SilentlyContinue** (the default).</span></span>

#### <a name="warningaction"></a><span data-ttu-id="f43dc-243">WarningAction</span><span class="sxs-lookup"><span data-stu-id="f43dc-243">WarningAction</span></span>

<span data-ttu-id="f43dc-244">确定 cmdlet 如何响应命令中的警告。</span><span class="sxs-lookup"><span data-stu-id="f43dc-244">Determines how the cmdlet responds to a warning from the command.</span></span> <span data-ttu-id="f43dc-245">**Continue** 为默认值。</span><span class="sxs-lookup"><span data-stu-id="f43dc-245">**Continue** is the default value.</span></span> <span data-ttu-id="f43dc-246">仅当命令生成警告消息时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="f43dc-246">This parameter works only when the command generates a warning message.</span></span> <span data-ttu-id="f43dc-247">例如，当命令包含 cmdlet 时，此参数有效 `Write-Warning` 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-247">For example, this parameter works when a command contains the `Write-Warning` cmdlet.</span></span>

```yaml
Type: ActionPreference
Aliases: wa
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="f43dc-248">**WarningAction** 参数将重写 `$WarningPreference` 当前命令的变量值。</span><span class="sxs-lookup"><span data-stu-id="f43dc-248">The **WarningAction** parameter overrides the value of the `$WarningPreference` variable for the current command.</span></span> <span data-ttu-id="f43dc-249">由于变量的默认值 `$WarningPreference` 为 **Continue** ，将显示警告，并且执行将继续，除非使用 **WarningAction** 参数。</span><span class="sxs-lookup"><span data-stu-id="f43dc-249">Because the default value of the `$WarningPreference` variable is **Continue** , warnings are displayed and execution continues unless you use the **WarningAction** parameter.</span></span>

<span data-ttu-id="f43dc-250">`-WarningAction:Continue` 显示警告消息并继续执行命令。</span><span class="sxs-lookup"><span data-stu-id="f43dc-250">`-WarningAction:Continue` displays the warning messages and continues executing the command.</span></span> <span data-ttu-id="f43dc-251">`Continue` 为默认值。</span><span class="sxs-lookup"><span data-stu-id="f43dc-251">`Continue` is the default.</span></span>

<span data-ttu-id="f43dc-252">`-WarningAction:Inquire` 显示警告消息并提示您进行确认，然后再继续执行。</span><span class="sxs-lookup"><span data-stu-id="f43dc-252">`-WarningAction:Inquire` displays the warning message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="f43dc-253">此值很少使用。</span><span class="sxs-lookup"><span data-stu-id="f43dc-253">This value is rarely used.</span></span>

<span data-ttu-id="f43dc-254">`-WarningAction:SilentlyContinue` 禁止显示警告消息并继续执行命令。</span><span class="sxs-lookup"><span data-stu-id="f43dc-254">`-WarningAction:SilentlyContinue` suppresses the warning message and continues executing the command.</span></span>

<span data-ttu-id="f43dc-255">`-WarningAction:Stop` 显示警告消息，并停止执行命令。</span><span class="sxs-lookup"><span data-stu-id="f43dc-255">`-WarningAction:Stop` displays the warning message and stops executing the command.</span></span>

> [!NOTE]
> <span data-ttu-id="f43dc-256">当 **WarningAction** 在 `$WarningAction` 命令中使用参数来运行脚本或函数时，WarningAction 参数将重写，但不会替换首选项变量的值。</span><span class="sxs-lookup"><span data-stu-id="f43dc-256">The **WarningAction** parameter overrides, but does not replace the value of the `$WarningAction` preference variable when the parameter is used in a command to run a script or function.</span></span>

#### <a name="warningvariable"></a><span data-ttu-id="f43dc-257">WarningVariable</span><span class="sxs-lookup"><span data-stu-id="f43dc-257">WarningVariable</span></span>

<span data-ttu-id="f43dc-258">存储有关指定变量中的命令的警告。</span><span class="sxs-lookup"><span data-stu-id="f43dc-258">Stores warnings about the command in the specified variable.</span></span>

```yaml
Type: String
Aliases: wv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="f43dc-259">即使未向用户显示警告，所有生成的警告也将保存在变量中。</span><span class="sxs-lookup"><span data-stu-id="f43dc-259">All generated warnings are saved in the variable even if the warnings aren't displayed to the user.</span></span>

<span data-ttu-id="f43dc-260">若要将警告追加到变量内容，而不是替换可能已存储在该处的任何警告，请在变量名之前键入一个加号 (`+`) 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-260">To append the warnings to the variable content, instead of replacing any warnings that might already be stored there, type a plus sign (`+`) before the variable name.</span></span>

<span data-ttu-id="f43dc-261">例如，下面的命令创建 `$a` 变量，然后在其中存储任何警告：</span><span class="sxs-lookup"><span data-stu-id="f43dc-261">For example, the following command creates the `$a` variable and then stores any warnings in it:</span></span>

```powershell
Get-Process -Id 6 -WarningVariable a
```

<span data-ttu-id="f43dc-262">以下命令将任何警告添加到 `$a` 变量：</span><span class="sxs-lookup"><span data-stu-id="f43dc-262">The following command adds any warnings to the `$a` variable:</span></span>

```powershell
Get-Process -Id 2 -WarningVariable +a
```

<span data-ttu-id="f43dc-263">以下命令显示的内容 `$a` ：</span><span class="sxs-lookup"><span data-stu-id="f43dc-263">The following command displays the contents of `$a`:</span></span>

```powershell
$a
```

<span data-ttu-id="f43dc-264">你可以使用此参数来创建一个仅包含特定命令中的警告的变量。</span><span class="sxs-lookup"><span data-stu-id="f43dc-264">You can use this parameter to create a variable that contains only warnings from specific commands.</span></span> <span data-ttu-id="f43dc-265">可以使用数组表示法（如 `$a[0]` 或） `$warning[1,2]` 来引用变量中存储的特定警告。</span><span class="sxs-lookup"><span data-stu-id="f43dc-265">You can use array notation, such as `$a[0]` or `$warning[1,2]` to refer to specific warnings stored in the variable.</span></span>

> [!NOTE]
> <span data-ttu-id="f43dc-266">警告变量包含命令生成的所有警告，包括调用嵌套函数或脚本的警告。</span><span class="sxs-lookup"><span data-stu-id="f43dc-266">The warning variable contains all warnings generated by the command, including warnings from calls to nested functions or scripts.</span></span>
### <a name="risk-management-parameter-descriptions"></a><span data-ttu-id="f43dc-267">风险管理参数说明</span><span class="sxs-lookup"><span data-stu-id="f43dc-267">Risk Management Parameter Descriptions</span></span>

#### <a name="whatif"></a><span data-ttu-id="f43dc-268">WhatIf</span><span class="sxs-lookup"><span data-stu-id="f43dc-268">WhatIf</span></span>

<span data-ttu-id="f43dc-269">显示一条消息，该消息描述命令的效果，而不是执行命令。</span><span class="sxs-lookup"><span data-stu-id="f43dc-269">Displays a message that describes the effect of the command, instead of executing the command.</span></span>

```yaml
Type: SwitchParameter
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="f43dc-270">**WhatIf** 参数会重写 `$WhatIfPreference` 当前命令的变量值。</span><span class="sxs-lookup"><span data-stu-id="f43dc-270">The **WhatIf** parameter overrides the value of the `$WhatIfPreference` variable for the current command.</span></span> <span data-ttu-id="f43dc-271">由于变量的默认值 `$WhatIfPreference` 为 0 (禁用了) ，因此在没有 **whatif** 参数的情况下，无法完成 **whatif** 行为。</span><span class="sxs-lookup"><span data-stu-id="f43dc-271">Because the default value of the `$WhatIfPreference` variable is 0 (disabled), **WhatIf** behavior isn't done without the **WhatIf** parameter.</span></span> <span data-ttu-id="f43dc-272">有关详细信息，请参阅 [about_Preference_Variables](about_Preference_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="f43dc-272">For more information, see [about_Preference_Variables](about_Preference_Variables.md)</span></span>

<span data-ttu-id="f43dc-273">`-WhatIf:$true` 与的效果相同 `-WhatIf` 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-273">`-WhatIf:$true` has the same effect as `-WhatIf`.</span></span>

<span data-ttu-id="f43dc-274">`-WhatIf:$false` 取消当变量的值为1时产生的自动 WhatIf 行为 `$WhatIfPreference` 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-274">`-WhatIf:$false` suppresses the automatic WhatIf behavior that results when the value of the `$WhatIfPreference` variable is 1.</span></span>

<span data-ttu-id="f43dc-275">例如，以下命令使用 `-WhatIf` 命令中的参数 `Remove-Item` ：</span><span class="sxs-lookup"><span data-stu-id="f43dc-275">For example, the following command uses the `-WhatIf` parameter in a `Remove-Item` command:</span></span>

```powershell
Remove-Item Date.csv -WhatIf
```

<span data-ttu-id="f43dc-276">PowerShell 不会删除项目，而是列出要执行的操作和受影响的项目。</span><span class="sxs-lookup"><span data-stu-id="f43dc-276">Instead of removing the item, PowerShell lists the operations it would do and the items that would be affected.</span></span> <span data-ttu-id="f43dc-277">该命令生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="f43dc-277">This command produces the following output:</span></span>

```output
What if: Performing operation "Remove File" on
Target "C:\ps-test\date.csv".
```

#### <a name="confirm"></a><span data-ttu-id="f43dc-278">确认</span><span class="sxs-lookup"><span data-stu-id="f43dc-278">Confirm</span></span>

<span data-ttu-id="f43dc-279">在执行命令前提示您进行确认。</span><span class="sxs-lookup"><span data-stu-id="f43dc-279">Prompts you for confirmation before executing the command.</span></span>

```yaml
Type: SwitchParameter
Aliases: cf

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="f43dc-280">**Confirm** 参数重写 `$ConfirmPreference` 当前命令的变量值。</span><span class="sxs-lookup"><span data-stu-id="f43dc-280">The **Confirm** parameter overrides the value of the `$ConfirmPreference` variable for the current command.</span></span> <span data-ttu-id="f43dc-281">默认值为 true。</span><span class="sxs-lookup"><span data-stu-id="f43dc-281">The default value is true.</span></span> <span data-ttu-id="f43dc-282">有关详细信息，请参阅 [about_Preference_Variables](about_Preference_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="f43dc-282">For more information, see [about_Preference_Variables](about_Preference_Variables.md)</span></span>

<span data-ttu-id="f43dc-283">`-Confirm:$true` 与的效果相同 `-Confirm` 。</span><span class="sxs-lookup"><span data-stu-id="f43dc-283">`-Confirm:$true` has the same effect as `-Confirm`.</span></span>

<span data-ttu-id="f43dc-284">`-Confirm:$false` 取消自动确认，当的值 `$ConfirmPreference` 小于或等于该 cmdlet 的估计风险时，就会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="f43dc-284">`-Confirm:$false` suppresses automatic confirmation, which occurs when the value of `$ConfirmPreference` is less than or equal to the estimated risk of the cmdlet.</span></span>

<span data-ttu-id="f43dc-285">例如，以下命令将 **Confirm** 参数用于 `Remove-Item` 命令。</span><span class="sxs-lookup"><span data-stu-id="f43dc-285">For example, the following command uses the **Confirm** parameter with a `Remove-Item` command.</span></span> <span data-ttu-id="f43dc-286">在删除项之前，PowerShell 会列出它将执行的操作和受影响的项，并请求批准。</span><span class="sxs-lookup"><span data-stu-id="f43dc-286">Before removing the item, PowerShell lists the operations it would do and the items that would be affected, and asks for approval.</span></span>

```
PS C:\ps-test> Remove-Item tmp*.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target " C:\ps-test\tmp1.txt
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend
[?] Help (default is "Y"):
```

<span data-ttu-id="f43dc-287">确认响应选项如下所示：</span><span class="sxs-lookup"><span data-stu-id="f43dc-287">The Confirm response options are as follows:</span></span>

|<span data-ttu-id="f43dc-288">响应</span><span class="sxs-lookup"><span data-stu-id="f43dc-288">Response</span></span>       |<span data-ttu-id="f43dc-289">结果</span><span class="sxs-lookup"><span data-stu-id="f43dc-289">Result</span></span>                                                     |
|---------------|-----------------------------------------------------------|
|<span data-ttu-id="f43dc-290">是 (Y) </span><span class="sxs-lookup"><span data-stu-id="f43dc-290">Yes (Y)</span></span>        |<span data-ttu-id="f43dc-291">执行操作。</span><span class="sxs-lookup"><span data-stu-id="f43dc-291">Perform the action.</span></span>                                        |
|<span data-ttu-id="f43dc-292">全部 (都是) </span><span class="sxs-lookup"><span data-stu-id="f43dc-292">Yes to All (A)</span></span> |<span data-ttu-id="f43dc-293">执行所有操作并取消后续确认查询</span><span class="sxs-lookup"><span data-stu-id="f43dc-293">Perform all actions and suppress subsequent Confirm queries</span></span>|
|               |<span data-ttu-id="f43dc-294">此命令。</span><span class="sxs-lookup"><span data-stu-id="f43dc-294">for this command.</span></span>                                          |
|<span data-ttu-id="f43dc-295">不 (N) ：</span><span class="sxs-lookup"><span data-stu-id="f43dc-295">No (N):</span></span>        |<span data-ttu-id="f43dc-296">不要执行该操作。</span><span class="sxs-lookup"><span data-stu-id="f43dc-296">Do not perform the action.</span></span>                                 |
|<span data-ttu-id="f43dc-297">所有 (L) ：</span><span class="sxs-lookup"><span data-stu-id="f43dc-297">No to All (L):</span></span> |<span data-ttu-id="f43dc-298">不要执行任何操作并取消后续确认</span><span class="sxs-lookup"><span data-stu-id="f43dc-298">Do not perform any actions and suppress subsequent Confirm</span></span> |
|               |<span data-ttu-id="f43dc-299">此命令的查询。</span><span class="sxs-lookup"><span data-stu-id="f43dc-299">queries for this command.</span></span>                                  |
|<span data-ttu-id="f43dc-300">挂起)  (：</span><span class="sxs-lookup"><span data-stu-id="f43dc-300">Suspend (S):</span></span>   |<span data-ttu-id="f43dc-301">暂停命令并创建临时会话。</span><span class="sxs-lookup"><span data-stu-id="f43dc-301">Pause the command and create a temporary session.</span></span>          |
|<span data-ttu-id="f43dc-302">帮助 (？ ) </span><span class="sxs-lookup"><span data-stu-id="f43dc-302">Help (?)</span></span>       |<span data-ttu-id="f43dc-303">显示这些选项的帮助。</span><span class="sxs-lookup"><span data-stu-id="f43dc-303">Display help for these options.</span></span>                            |

<span data-ttu-id="f43dc-304">" **挂起** " 选项将命令置于保持状态，并创建一个临时嵌套会话，在该会话中，您可以选择 " **确认** " 选项。</span><span class="sxs-lookup"><span data-stu-id="f43dc-304">The **Suspend** option places the command on hold and creates a temporary nested session in which you can work until you're ready to choose a **Confirm** option.</span></span> <span data-ttu-id="f43dc-305">嵌套会话的命令提示符包含两个额外的插入符号 ( # A2) ，以指示它是原始父命令的子操作。</span><span class="sxs-lookup"><span data-stu-id="f43dc-305">The command prompt for the nested session has two extra carets (>>) to indicate that it's a child operation of the original parent command.</span></span> <span data-ttu-id="f43dc-306">可以在嵌套会话中运行命令和脚本。</span><span class="sxs-lookup"><span data-stu-id="f43dc-306">You can run commands and scripts in the nested session.</span></span> <span data-ttu-id="f43dc-307">若要结束嵌套会话并返回到原始命令的确认选项，请键入 "exit"。</span><span class="sxs-lookup"><span data-stu-id="f43dc-307">To end the nested session and return to the Confirm options for the original command, type "exit".</span></span>

<span data-ttu-id="f43dc-308">在下面的示例中， **暂停** 选项 (S) 用于在用户检查命令参数帮助时暂时停止命令。</span><span class="sxs-lookup"><span data-stu-id="f43dc-308">In the following example, the **Suspend** option (S) is used to halt a command temporarily while the user checks the help for a command parameter.</span></span> <span data-ttu-id="f43dc-309">获取所需的信息后，用户键入 "exit" 结束嵌套提示，然后选择 "是" (y) 响应确认查询。</span><span class="sxs-lookup"><span data-stu-id="f43dc-309">After obtaining the needed information, the user types "exit" to end the nested prompt and then selects the Yes (y) response to the Confirm query.</span></span>

```
PS C:\ps-test> New-Item -ItemType File -Name Test.txt -Confirm

Confirm
Are you sure you want to perform this action?

Performing operation "Create File" on Target "Destination:
C:\ps-test\test.txt".
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default
is "Y"): s

PS C:\ps-test> Get-Help New-Item -Parameter ItemType

-ItemType <string>
Specifies the provider-specified type of the new item.

Required?                    false
Position?                    named
Default value
Accept pipeline input?       true (ByPropertyName)
Accept wildcard characters?  false

PS C:\ps-test> exit

Confirm
Are you sure you want to perform this action?
Performing operation "Create File" on Target "Destination: C:\ps-test\test
.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (defau
lt is "Y"): y

Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---         8/27/2010   2:41 PM          0 test.txt
```

## <a name="keywords"></a><span data-ttu-id="f43dc-310">字</span><span class="sxs-lookup"><span data-stu-id="f43dc-310">KEYWORDS</span></span>

<span data-ttu-id="f43dc-311">about_Common_Parameters</span><span class="sxs-lookup"><span data-stu-id="f43dc-311">about_Common_Parameters</span></span>

## <a name="see-also"></a><span data-ttu-id="f43dc-312">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f43dc-312">SEE ALSO</span></span>

[<span data-ttu-id="f43dc-313">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="f43dc-313">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="f43dc-314">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="f43dc-314">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)

[<span data-ttu-id="f43dc-315">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="f43dc-315">Write-Warning</span></span>](xref:Microsoft.PowerShell.Utility.Write-Warning)

[<span data-ttu-id="f43dc-316">写入错误</span><span class="sxs-lookup"><span data-stu-id="f43dc-316">Write-Error</span></span>](xref:Microsoft.PowerShell.Utility.Write-Error)

[<span data-ttu-id="f43dc-317">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="f43dc-317">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)
