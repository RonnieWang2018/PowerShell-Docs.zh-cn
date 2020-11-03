---
description: 描述可用于根据条件测试运行语句的语言命令。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 3/4/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_for?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_For
ms.openlocfilehash: 07037b73a5507bb0ef420ad39271be8832f7500b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/13/2020
ms.locfileid: "93199660"
---
# <a name="about-for"></a><span data-ttu-id="9a2a4-104">关于</span><span class="sxs-lookup"><span data-stu-id="9a2a4-104">About For</span></span>

## <a name="short-description"></a><span data-ttu-id="9a2a4-105">简短说明</span><span class="sxs-lookup"><span data-stu-id="9a2a4-105">Short description</span></span>
<span data-ttu-id="9a2a4-106">描述可用于根据条件测试运行语句的语言命令。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-106">Describes a language command you can use to run statements based on a conditional test.</span></span>

## <a name="long-description"></a><span data-ttu-id="9a2a4-107">长说明</span><span class="sxs-lookup"><span data-stu-id="9a2a4-107">Long description</span></span>

<span data-ttu-id="9a2a4-108">`For`语句 (也称为 `For` 循环) 是一种语言构造，可用于创建在指定条件的计算结果为时在命令块中运行命令的循环 `$true` 。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-108">The `For` statement (also known as a `For` loop) is a language construct you can use to create a loop that runs commands in a command block while a specified condition evaluates to `$true`.</span></span>

<span data-ttu-id="9a2a4-109">循环的典型用途 `For` 是循环访问值的数组，并对这些值的子集进行运算。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-109">A typical use of the `For` loop is to iterate an array of values and to operate on a subset of these values.</span></span> <span data-ttu-id="9a2a4-110">在大多数情况下，如果要对数组中的所有值进行迭代，请考虑使用 `Foreach` 语句。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-110">In most cases, if you want to iterate all the values in an array, consider using a `Foreach` statement.</span></span>

### <a name="syntax"></a><span data-ttu-id="9a2a4-111">语法</span><span class="sxs-lookup"><span data-stu-id="9a2a4-111">Syntax</span></span>

<span data-ttu-id="9a2a4-112">下面显示了 `For` 语句语法。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-112">The following shows the `For` statement syntax.</span></span>

```
for (<Init>; <Condition>; <Repeat>)
{
    <Statement list>
}
```

<span data-ttu-id="9a2a4-113">**Init** 占位符表示在循环开始之前运行的一个或多个命令。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-113">The **Init** placeholder represents one or more commands that are run before the loop begins.</span></span> <span data-ttu-id="9a2a4-114">通常使用语句的 **Init** 部分来创建和初始化具有起始值的变量。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-114">You typically use the **Init** portion of the statement to create and initialize a variable with a starting value.</span></span>

<span data-ttu-id="9a2a4-115">然后，此变量将成为该语句的下一部分中要测试的条件的基础 `For` 。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-115">This variable will then be the basis for the condition to be tested in the next portion of the `For` statement.</span></span>

<span data-ttu-id="9a2a4-116">**条件** 占位符表示 `For` 语句中解析为 `$true` 或 `$false` **布尔** 值的部分。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-116">The **Condition** placeholder represents the portion of the `For` statement that resolves to a `$true` or `$false` **Boolean** value.</span></span> <span data-ttu-id="9a2a4-117">PowerShell 将在每次循环运行时评估条件 `For` 。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-117">PowerShell evaluates the condition each time the `For` loop runs.</span></span> <span data-ttu-id="9a2a4-118">如果语句为 `$true` ，则命令块中的命令将运行，并再次计算语句。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-118">If the statement is `$true`, the commands in the command block run, and the statement is evaluated again.</span></span> <span data-ttu-id="9a2a4-119">如果条件仍为 `$true` ， **语句列表** 中的命令将再次运行。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-119">If the condition is still `$true`, the commands in the **Statement list** run again.</span></span> <span data-ttu-id="9a2a4-120">循环将重复，直到该条件变为 `$false` 。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-120">The loop is repeated until the condition becomes `$false`.</span></span>

<span data-ttu-id="9a2a4-121">**重复** 占位符表示一个或多个以逗号分隔的命令，这些命令在每次循环重复时执行。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-121">The **Repeat** placeholder represents one or more commands, separated by commas, that are executed each time the loop repeats.</span></span> <span data-ttu-id="9a2a4-122">通常，这用于修改在语句的 **条件** 部分内测试的变量。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-122">Typically, this is used to modify a variable that is tested inside the **Condition** part of the statement.</span></span>

<span data-ttu-id="9a2a4-123">**语句列表** 占位符表示在每次输入或重复循环时运行的一个或多个命令集。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-123">The **Statement list** placeholder represents a set of one or more commands that are run each time the loop is entered or repeated.</span></span> <span data-ttu-id="9a2a4-124">**语句列表** 的内容括在大括号中。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-124">The contents of the **Statement list** are surrounded by braces.</span></span>

### <a name="support-for-multiple-operations"></a><span data-ttu-id="9a2a4-125">支持多个操作</span><span class="sxs-lookup"><span data-stu-id="9a2a4-125">Support for multiple operations</span></span>

<span data-ttu-id="9a2a4-126">**Init** 语句中的多个赋值操作支持以下语法：</span><span class="sxs-lookup"><span data-stu-id="9a2a4-126">The following syntaxes are supported for multiple assignment operations in the **Init** statement:</span></span>

```powershell
# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}
```

<span data-ttu-id="9a2a4-127">**重复** 语句中的多个赋值操作支持以下语法：</span><span class="sxs-lookup"><span data-stu-id="9a2a4-127">The following syntaxes are supported for multiple assignment operations in the **Repeat** statement:</span></span>

```powershell
# Comma separated assignment expressions.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; ($i++), ($j++))
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $($i++;$j++))
{
    "`$i:$i"
    "`$j:$j"
}
```

> [!NOTE]
> <span data-ttu-id="9a2a4-128">除 pre 或 post 以外的其他操作可能不适用于所有语法。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-128">Operations other than pre or post increment may not work with all syntaxes.</span></span>

<span data-ttu-id="9a2a4-129">对于多个 **条件** 使用逻辑运算符，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-129">For multiple **Conditions** use logical operators as demonstrated by the following example.</span></span>

```powershell
for (($i = 0), ($j = 0); $i -lt 10 -and $j -lt 10; $i++,$j++)
{
    "`$i:$i"
    "`$j:$j"
}
```

<span data-ttu-id="9a2a4-130">有关详细信息，请参阅 [about_Logical_Operators](about_Logical_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-130">For more information, see [about_Logical_Operators](about_Logical_Operators.md).</span></span>

### <a name="examples"></a><span data-ttu-id="9a2a4-131">示例</span><span class="sxs-lookup"><span data-stu-id="9a2a4-131">Examples</span></span>

<span data-ttu-id="9a2a4-132">至少，语句要求在语句的 `For` 语句列表部分中，语句的 **Init** 、 **Condition** 和 **Repeat** 部分以及括在语句的 **语句列表** 部分中的命令使用括号。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-132">At a minimum, a `For` statement requires the parenthesis surrounding the **Init** , **Condition** , and **Repeat** part of the statement and a command surrounded by braces in the **Statement list** part of the statement.</span></span>

<span data-ttu-id="9a2a4-133">请注意，即将出现的示例有意显示语句外部的代码 `For` 。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-133">Note that the upcoming examples intentionally show code outside the `For` statement.</span></span> <span data-ttu-id="9a2a4-134">在后面的示例中，代码集成到 `For` 语句中。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-134">In later examples, code is integrated into the `For` statement.</span></span>

<span data-ttu-id="9a2a4-135">例如，下面的 `For` 语句持续显示变量的值， `$i` 直到你通过按 CTRL + C 手动跳出命令。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-135">For example, the following `For` statement continually displays the value of the `$i` variable until you manually break out of the command by pressing CTRL+C.</span></span>

```powershell
$i = 1
for (;;)
{
    Write-Host $i
}
```

<span data-ttu-id="9a2a4-136">您可以向语句列表中添加其他命令 `$i` ，以便每次运行该循环时，的值递增1，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-136">You can add additional commands to the statement list so that the value of `$i` is incremented by 1 each time the loop is run, as the following example shows.</span></span>

```powershell
for (;;)
{
    $i++; Write-Host $i
}
```

<span data-ttu-id="9a2a4-137">在您通过按 CTRL + C 跳出命令之前，此语句将持续显示变量的值， `$i` 因为每次运行该循环时，它将递增1。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-137">Until you break out of the command by pressing CTRL+C, this statement will continually display the value of the `$i` variable as it is incremented by 1 each time the loop is run.</span></span>

<span data-ttu-id="9a2a4-138">`For`您可以改为使用语句的 **重复** 部分，而不是在语句的语句列表部分中更改变量的值， `For` 如下所示。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-138">Rather than change the value of the variable in the statement list part of the `For` statement, you can use the **Repeat** portion of the `For` statement instead, as follows.</span></span>

```powershell
$i=1
for (;;$i++)
{
    Write-Host $i
}
```

<span data-ttu-id="9a2a4-139">此语句仍会无限重复，直到你通过按 CTRL + C 退出命令。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-139">This statement will still repeat indefinitely until you break out of the command by pressing CTRL+C.</span></span>

<span data-ttu-id="9a2a4-140">您可以 `For` 使用 *条件* 终止循环。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-140">You can terminate the `For` loop using a *condition* .</span></span> <span data-ttu-id="9a2a4-141">您可以使用语句的 **条件** 部分来放置条件 `For` 。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-141">You can place a condition using the **Condition** portion of the `For` statement.</span></span> <span data-ttu-id="9a2a4-142">`For`当条件的计算结果为时，循环将终止 `$false` 。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-142">The `For` loop terminates when the condition evaluates to `$false`.</span></span>

<span data-ttu-id="9a2a4-143">在下面的示例中， `For` 当的值 `$i` 小于或等于10时，将运行循环。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-143">In the following example, the `For` loop runs while the value of `$i` is less than or equal to 10.</span></span>

```powershell
$i=1
for(;$i -le 10;$i++)
{
    Write-Host $i
}
```

<span data-ttu-id="9a2a4-144">`For`您可以 `For` 使用语句的 **Init** 部分在循环内执行此任务，而不是在语句外部创建和初始化变量 `For` 。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-144">Instead of creating and initializing the variable outside the `For` statement, you can perform this task inside the `For` loop by using the **Init** portion of the `For` statement.</span></span>

```powershell
for($i=1; $i -le 10; $i++){Write-Host $i}
```

<span data-ttu-id="9a2a4-145">您可以使用回车符而不是分号来分隔语句的 **Init** 、 **Condition** 和 **Repeat** 部分 `For` 。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-145">You can use carriage returns instead of semicolons to delimit the **Init** , **Condition** , and **Repeat** portions of the `For` statement.</span></span> <span data-ttu-id="9a2a4-146">下面的示例演示一个 `For` 使用此替代语法的。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-146">The following example shows a `For` that uses this alternative syntax.</span></span>

```powershell
for ($i = 0
  $i -lt 10
  $i++){
  $i
}
```

<span data-ttu-id="9a2a4-147">该语句的这种替代形式 `For` 适用于 powershell 脚本文件和 powershell 命令提示符。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-147">This alternative form of the `For` statement works in PowerShell script files and at the PowerShell command prompt.</span></span> <span data-ttu-id="9a2a4-148">但是，在 `For` 命令提示符下输入交互命令时，使用带有分号的语句语法会更容易。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-148">However, it is easier to use the `For` statement syntax with semicolons when you enter interactive commands at the command prompt.</span></span>

<span data-ttu-id="9a2a4-149">`For`循环比循环更灵活， `Foreach` 因为它允许您通过使用模式来递增数组或集合中的值。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-149">The `For` loop is more flexible than the `Foreach` loop because it allows you to increment values in an array or collection by using patterns.</span></span> <span data-ttu-id="9a2a4-150">在下面的示例中，在 `$i` 语句的 **重复** 部分，变量递增 2 `For` 。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-150">In the following example, the `$i` variable is incremented by 2 in the **Repeat** portion of the `For` statement.</span></span>

```powershell
for ($i = 0; $i -le 20; $i += 2)
{
    Write-Host $i
}
```

<span data-ttu-id="9a2a4-151">`For`还可以在一行上写入循环，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="9a2a4-151">The `For` loop can also be written on one line as in the following example.</span></span>

```powershell
for ($i = 0; $i -lt 10; $i++) { Write-Host $i }
```

## <a name="see-also"></a><span data-ttu-id="9a2a4-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9a2a4-152">SEE ALSO</span></span>

[<span data-ttu-id="9a2a4-153">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="9a2a4-153">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="9a2a4-154">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="9a2a4-154">about_Foreach</span></span>](about_Foreach.md)

