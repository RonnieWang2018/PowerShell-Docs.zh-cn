---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-expression?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Expression
ms.openlocfilehash: f0fca430b4a378b88498a96ab6c9dc0f4d4881a4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93197892"
---
# <span data-ttu-id="c6026-103">Invoke-Expression</span><span class="sxs-lookup"><span data-stu-id="c6026-103">Invoke-Expression</span></span>

## <span data-ttu-id="c6026-104">摘要</span><span class="sxs-lookup"><span data-stu-id="c6026-104">SYNOPSIS</span></span>
<span data-ttu-id="c6026-105">在本地计算机上运行命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="c6026-105">Runs commands or expressions on the local computer.</span></span>

## <span data-ttu-id="c6026-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c6026-106">SYNTAX</span></span>

```
Invoke-Expression [-Command] <String> [<CommonParameters>]
```

## <span data-ttu-id="c6026-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c6026-107">DESCRIPTION</span></span>

<span data-ttu-id="c6026-108">该 `Invoke-Expression` cmdlet 将指定的字符串作为命令进行计算，并返回表达式或命令的结果。</span><span class="sxs-lookup"><span data-stu-id="c6026-108">The `Invoke-Expression` cmdlet evaluates or runs a specified string as a command and returns the results of the expression or command.</span></span> <span data-ttu-id="c6026-109">如果没有，则在 `Invoke-Expression` 命令行提交的字符串将 (回显) 更改。</span><span class="sxs-lookup"><span data-stu-id="c6026-109">Without `Invoke-Expression`, a string submitted at the command line is returned (echoed) unchanged.</span></span>

<span data-ttu-id="c6026-110">表达式在当前作用域中计算和运行。</span><span class="sxs-lookup"><span data-stu-id="c6026-110">Expressions are evaluated and run in the current scope.</span></span> <span data-ttu-id="c6026-111">有关详细信息，请参阅 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="c6026-111">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

> [!CAUTION]
> <span data-ttu-id="c6026-112">在脚本中使用 cmdlet 时，请采取合理的防范措施 `Invoke-Expression` 。</span><span class="sxs-lookup"><span data-stu-id="c6026-112">Take reasonable precautions when using the `Invoke-Expression` cmdlet in scripts.</span></span> <span data-ttu-id="c6026-113">当使用 `Invoke-Expression` 运行用户输入的命令时，请验证在运行该命令之前，该命令是否可安全运行。</span><span class="sxs-lookup"><span data-stu-id="c6026-113">When using `Invoke-Expression` to run a command that the user enters, verify that the command is safe to run before running it.</span></span> <span data-ttu-id="c6026-114">通常，最好将脚本设计为包含预定义的输入选项，而不允许随意输入。</span><span class="sxs-lookup"><span data-stu-id="c6026-114">In general, it is best to design your script with predefined input options, rather than allowing freeform input.</span></span>

## <span data-ttu-id="c6026-115">示例</span><span class="sxs-lookup"><span data-stu-id="c6026-115">EXAMPLES</span></span>

### <span data-ttu-id="c6026-116">示例 1：计算表达式</span><span class="sxs-lookup"><span data-stu-id="c6026-116">Example 1: Evaluate an expression</span></span>

```powershell
$Command = "Get-Process"
$Command
```

```Output
Get-Process
```

```powershell
Invoke-Expression $Command
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
-------  ------    -----      ----- -----   ------     --   -----------
296       4       1572       1956    20       0.53     1348   AdtAgent
270       6       1328       800     34       0.06     2396   alg
67        2       620        484     20       0.22     716    ati2evxx
1060      15      12904      11840   74       11.48    892    CcmExec
1400      33      25280      37544   223      38.44    2564   communicator
...
```

<span data-ttu-id="c6026-117">此示例演示 `Invoke-Expression` 如何使用来计算表达式。</span><span class="sxs-lookup"><span data-stu-id="c6026-117">This example demonstrates the use of `Invoke-Expression` to evaluate an expression.</span></span> <span data-ttu-id="c6026-118">如果没有 `Invoke-Expression` ，则打印但不计算表达式。</span><span class="sxs-lookup"><span data-stu-id="c6026-118">Without `Invoke-Expression`, the expression is printed, but not evaluated.</span></span>

<span data-ttu-id="c6026-119">第一个命令将 `Get-Process` () 字符串的值分配给 `$Command` 变量。</span><span class="sxs-lookup"><span data-stu-id="c6026-119">The first command assigns a value of `Get-Process` (a string) to the `$Command` variable.</span></span>

<span data-ttu-id="c6026-120">第二个命令显示在命令行键入变量名称的效果。</span><span class="sxs-lookup"><span data-stu-id="c6026-120">The second command shows the effect of typing the variable name at the command line.</span></span> <span data-ttu-id="c6026-121">PowerShell 回显该字符串。</span><span class="sxs-lookup"><span data-stu-id="c6026-121">PowerShell echoes the string.</span></span>

<span data-ttu-id="c6026-122">第三个命令使用 `Invoke-Expression` 来计算字符串。</span><span class="sxs-lookup"><span data-stu-id="c6026-122">The third command uses `Invoke-Expression` to evaluate the string.</span></span>

### <span data-ttu-id="c6026-123">示例 2：在本地计算机上运行脚本</span><span class="sxs-lookup"><span data-stu-id="c6026-123">Example 2: Run a script on the local computer</span></span>

```powershell
Invoke-Expression -Command "C:\ps-test\testscript.ps1"
"C:\ps-test\testscript.ps1" | Invoke-Expression
```

<span data-ttu-id="c6026-124">这些命令用于 `Invoke-Expression` 在本地计算机上运行脚本 TestScript.ps1。</span><span class="sxs-lookup"><span data-stu-id="c6026-124">These commands use `Invoke-Expression` to run a script, TestScript.ps1, on the local computer.</span></span> <span data-ttu-id="c6026-125">这两个命令是等效的。</span><span class="sxs-lookup"><span data-stu-id="c6026-125">The two commands are equivalent.</span></span> <span data-ttu-id="c6026-126">第一个命令使用 **command** 参数来指定要运行的命令。</span><span class="sxs-lookup"><span data-stu-id="c6026-126">The first uses the **Command** parameter to specify the command to run.</span></span>
<span data-ttu-id="c6026-127">第二个使用管道运算符 (`|`) 将命令字符串发送到 `Invoke-Expression` 。</span><span class="sxs-lookup"><span data-stu-id="c6026-127">The second uses a pipeline operator (`|`) to send the command string to `Invoke-Expression`.</span></span>

### <span data-ttu-id="c6026-128">示例 3：运行变量中的命令</span><span class="sxs-lookup"><span data-stu-id="c6026-128">Example 3: Run a command in a variable</span></span>

```powershell
$Command = 'Get-Process | where {$_.cpu -gt 1000}'
Invoke-Expression $Command
```

<span data-ttu-id="c6026-129">此示例运行保存在变量中的命令字符串 `$Command` 。</span><span class="sxs-lookup"><span data-stu-id="c6026-129">This example runs a command string that is saved in the `$Command` variable.</span></span>

<span data-ttu-id="c6026-130">命令字符串括在单引号中，因为它包含一个 `$_` 表示当前对象的变量。</span><span class="sxs-lookup"><span data-stu-id="c6026-130">The command string is enclosed in single quotation marks because it includes a variable, `$_`, which represents the current object.</span></span> <span data-ttu-id="c6026-131">如果它用双引号引起来，则在将 `$_` 变量保存到变量之前，该变量将替换为其值 `$Command` 。</span><span class="sxs-lookup"><span data-stu-id="c6026-131">If it were enclosed in double quotation marks, the `$_` variable would be replaced by its value before it was saved in the `$Command` variable.</span></span>

### <span data-ttu-id="c6026-132">示例 4：获取并运行 cmdlet 帮助示例</span><span class="sxs-lookup"><span data-stu-id="c6026-132">Example 4: Get and run a cmdlet Help example</span></span>

```powershell
$Cmdlet_name = "Get-EventLog"
$Example_number = 1
$Example_code = (Get-Help $Cmdlet_name).examples.example[($Example_number-1)].code
Invoke-Expression $Example_code
```

<span data-ttu-id="c6026-133">此命令检索并运行 cmdlet 帮助主题中的第一个示例 `Get-EventLog` 。</span><span class="sxs-lookup"><span data-stu-id="c6026-133">This command retrieves and runs the first example in the `Get-EventLog` cmdlet Help topic.</span></span>

<span data-ttu-id="c6026-134">若要运行其他 cmdlet 的示例，请将该变量的值更改 `$Cmdlet_name` 为该 cmdlet 的名称。</span><span class="sxs-lookup"><span data-stu-id="c6026-134">To run an example of a different cmdlet, change the value of the `$Cmdlet_name` variable to the name of the cmdlet.</span></span> <span data-ttu-id="c6026-135">将 `$Example_number` 变量更改为要运行的示例编号。</span><span class="sxs-lookup"><span data-stu-id="c6026-135">And, change the `$Example_number` variable to the example number you want to run.</span></span> <span data-ttu-id="c6026-136">如果示例数字无效，则该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="c6026-136">The command fails if the example number is not valid.</span></span>

## <span data-ttu-id="c6026-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c6026-137">PARAMETERS</span></span>

### <span data-ttu-id="c6026-138">-Command</span><span class="sxs-lookup"><span data-stu-id="c6026-138">-Command</span></span>

<span data-ttu-id="c6026-139">指定要运行的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="c6026-139">Specifies the command or expression to run.</span></span> <span data-ttu-id="c6026-140">键入该命令或表达式，或输入包含该命或表达式的变量。</span><span class="sxs-lookup"><span data-stu-id="c6026-140">Type the command or expression or enter a variable that contains the command or expression.</span></span> <span data-ttu-id="c6026-141">**Command** 参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="c6026-141">The **Command** parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c6026-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c6026-142">CommonParameters</span></span>

<span data-ttu-id="c6026-143">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c6026-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c6026-144">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="c6026-144">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="c6026-145">输入</span><span class="sxs-lookup"><span data-stu-id="c6026-145">INPUTS</span></span>

### <span data-ttu-id="c6026-146">System.String 或 PSObject</span><span class="sxs-lookup"><span data-stu-id="c6026-146">System.String or PSObject</span></span>

<span data-ttu-id="c6026-147">可以通过管道将表示命令的对象传递给 `Invoke-Expression` 。</span><span class="sxs-lookup"><span data-stu-id="c6026-147">You can pipe an object that represents the command to `Invoke-Expression`.</span></span>
<span data-ttu-id="c6026-148">使用 `$Input` 自动变量来表示命令中的输入对象。</span><span class="sxs-lookup"><span data-stu-id="c6026-148">Use the `$Input` automatic variable to represent the input objects in the command.</span></span>

## <span data-ttu-id="c6026-149">输出</span><span class="sxs-lookup"><span data-stu-id="c6026-149">OUTPUTS</span></span>

### <span data-ttu-id="c6026-150">PSObject</span><span class="sxs-lookup"><span data-stu-id="c6026-150">PSObject</span></span>

<span data-ttu-id="c6026-151">返回由调用的命令生成的输出， () 的 **命令** 参数的值。</span><span class="sxs-lookup"><span data-stu-id="c6026-151">Returns the output that is generated by the invoked command (the value of the **Command** parameter).</span></span>

## <span data-ttu-id="c6026-152">注释</span><span class="sxs-lookup"><span data-stu-id="c6026-152">NOTES</span></span>

<span data-ttu-id="c6026-153">在大多数情况下，使用 PowerShell 调用运算符调用表达式并获得相同的结果。</span><span class="sxs-lookup"><span data-stu-id="c6026-153">In most cases, you invoke expressions using PowerShell's call operator and achieve the same results.</span></span>
<span data-ttu-id="c6026-154">调用运算符是一种更安全的方法。</span><span class="sxs-lookup"><span data-stu-id="c6026-154">The call operator is a safer method.</span></span> <span data-ttu-id="c6026-155">有关详细信息，请参阅 [about_Operators](../microsoft.powershell.core/about/about_operators.md#call-operator-)。</span><span class="sxs-lookup"><span data-stu-id="c6026-155">For more information, see [about_Operators](../microsoft.powershell.core/about/about_operators.md#call-operator-).</span></span>

## <span data-ttu-id="c6026-156">相关链接</span><span class="sxs-lookup"><span data-stu-id="c6026-156">RELATED LINKS</span></span>

[<span data-ttu-id="c6026-157">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="c6026-157">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="c6026-158">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="c6026-158">about_Scopes</span></span>](../Microsoft.PowerShell.Core/About/about_Scopes.md)
