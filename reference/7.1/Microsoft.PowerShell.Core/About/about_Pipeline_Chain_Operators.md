---
description: 介绍如何 `&&` 在 PowerShell 中将管道与 and `||` 运算符链接。
ms.date: 09/30/2019
schema: 2.0.0
Locale: en-US
keywords: powershell,cmdlet
title: about_Pipeline_Chain_Operators
ms.openlocfilehash: 38895ff9acda9ead031c9be58904ac132364a584
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/13/2020
ms.locfileid: "93199937"
---
# <a name="about-pipeline-chain-operators"></a><span data-ttu-id="8162b-104">关于管道链运算符</span><span class="sxs-lookup"><span data-stu-id="8162b-104">About Pipeline Chain Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="8162b-105">简短说明</span><span class="sxs-lookup"><span data-stu-id="8162b-105">Short description</span></span>

<span data-ttu-id="8162b-106">介绍如何 `&&` 在 PowerShell 中将管道与 and `||` 运算符链接。</span><span class="sxs-lookup"><span data-stu-id="8162b-106">Describes chaining pipelines with the `&&` and `||` operators in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="8162b-107">长说明</span><span class="sxs-lookup"><span data-stu-id="8162b-107">Long description</span></span>

<span data-ttu-id="8162b-108">从 PowerShell 7 开始，PowerShell 实现 `&&` 和 `||` 运算符以有条件地链接管道。</span><span class="sxs-lookup"><span data-stu-id="8162b-108">Beginning in PowerShell 7, PowerShell implements the `&&` and `||` operators to conditionally chain pipelines.</span></span> <span data-ttu-id="8162b-109">这些运算符在 PowerShell 中已知为 *管道链运算符* ，并且类似于 POSIX shell 中的 [和-或列表](https://pubs.opengroup.org/onlinepubs/009695399/utilities/xcu_chap02.html#tag_02_09_03) （如 bash、zsh 和 Sh）以及 Windows 命令行界面中的 [条件处理符号](/previous-versions/windows/it-pro/windows-xp/bb490954(v=technet.10)#using-multiple-commands-and-conditional-processing-symbols) ( # A0) 。</span><span class="sxs-lookup"><span data-stu-id="8162b-109">These operators are known in PowerShell as *pipeline chain operators* , and are similar to [AND-OR lists](https://pubs.opengroup.org/onlinepubs/009695399/utilities/xcu_chap02.html#tag_02_09_03) in POSIX shells like bash, zsh and sh, as well as [conditional processing symbols](/previous-versions/windows/it-pro/windows-xp/bb490954(v=technet.10)#using-multiple-commands-and-conditional-processing-symbols) in the Windows Command Shell (cmd.exe).</span></span>

<span data-ttu-id="8162b-110">如果左侧管道成功，则 `&&` 运算符将执行右侧管道。</span><span class="sxs-lookup"><span data-stu-id="8162b-110">The `&&` operator executes the right-hand pipeline, if the left-hand pipeline succeeded.</span></span> <span data-ttu-id="8162b-111">相反，如果左侧管道失败，则 `||` 运算符将执行右侧管道。</span><span class="sxs-lookup"><span data-stu-id="8162b-111">Conversely, the `||` operator executes the right-hand pipeline if the left-hand pipeline failed.</span></span>

<span data-ttu-id="8162b-112">这些运算符使用 `$?` 和 `$LASTEXITCODE` 变量来确定管道是否失败。</span><span class="sxs-lookup"><span data-stu-id="8162b-112">These operators use the `$?` and `$LASTEXITCODE` variables to determine if a pipeline failed.</span></span> <span data-ttu-id="8162b-113">这允许你将其与本机命令一起使用，而不只是与 cmdlet 或函数一起使用。</span><span class="sxs-lookup"><span data-stu-id="8162b-113">This allows you to use them with native commands and not just with cmdlets or functions.</span></span> <span data-ttu-id="8162b-114">例如：</span><span class="sxs-lookup"><span data-stu-id="8162b-114">For example:</span></span>

```powershell
# Create an SSH key pair - if successful copy the public key to clipboard
ssh-keygen -t rsa -b 2048 && Get-Content -Raw ~\.ssh\id_rsa.pub | clip
```

### <a name="examples"></a><span data-ttu-id="8162b-115">示例</span><span class="sxs-lookup"><span data-stu-id="8162b-115">Examples</span></span>

#### <a name="two-successful-commands"></a><span data-ttu-id="8162b-116">两个成功的命令</span><span class="sxs-lookup"><span data-stu-id="8162b-116">Two successful commands</span></span>

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

#### <a name="first-command-fails-causing-second-not-to-be-executed"></a><span data-ttu-id="8162b-117">第一条命令失败，导致第二个命令失败</span><span class="sxs-lookup"><span data-stu-id="8162b-117">First command fails, causing second not to be executed</span></span>

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

#### <a name="first-command-succeeds-so-the-second-command-is-not-executed"></a><span data-ttu-id="8162b-118">第一个命令成功，因此不执行第二个命令</span><span class="sxs-lookup"><span data-stu-id="8162b-118">First command succeeds, so the second command is not executed</span></span>

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

#### <a name="first-command-fails-so-the-second-command-is-executed"></a><span data-ttu-id="8162b-119">第一条命令失败，因此将执行第二个命令</span><span class="sxs-lookup"><span data-stu-id="8162b-119">First command fails, so the second command is executed</span></span>

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error: Bad
Second
```

<span data-ttu-id="8162b-120">管道成功由变量的值定义 `$?` ，在基于其执行状态执行管道之后，PowerShell 会自动设置该变量的值。</span><span class="sxs-lookup"><span data-stu-id="8162b-120">Pipeline success is defined by the value of the `$?` variable, which PowerShell automatically sets after executing a pipeline based on its execution status.</span></span>
<span data-ttu-id="8162b-121">这意味着管道链运算符具有以下等效性：</span><span class="sxs-lookup"><span data-stu-id="8162b-121">This means that pipeline chain operators have the following equivalence:</span></span>

```powershell
Test-Command '1' && Test-Command '2'
```

<span data-ttu-id="8162b-122">的工作方式与</span><span class="sxs-lookup"><span data-stu-id="8162b-122">works the same as</span></span>

```powershell
Test-Command '1'; if ($?) { Test-Command '2' }
```

<span data-ttu-id="8162b-123">and</span><span class="sxs-lookup"><span data-stu-id="8162b-123">and</span></span>

```powershell
Test-Command '1' || Test-Command '2'
```

<span data-ttu-id="8162b-124">的工作方式与</span><span class="sxs-lookup"><span data-stu-id="8162b-124">works the same as</span></span>

```powershell
Test-Command '1'; if (-not $?) { Test-Command '2' }
```

### <a name="assignment-from-pipeline-chains"></a><span data-ttu-id="8162b-125">从管道链分配</span><span class="sxs-lookup"><span data-stu-id="8162b-125">Assignment from pipeline chains</span></span>

<span data-ttu-id="8162b-126">从管道链分配变量会使该链中的所有管道串联：</span><span class="sxs-lookup"><span data-stu-id="8162b-126">Assigning a variable from a pipeline chain takes the concatenation of all the pipelines in the chain:</span></span>

```powershell
$result = Write-Output '1' && Write-Output '2'
$result
```

```Output
1
2
```

<span data-ttu-id="8162b-127">如果在分配管道链期间出现脚本终止错误，则分配不会成功：</span><span class="sxs-lookup"><span data-stu-id="8162b-127">If a script-terminating error occurs during assignment from a pipeline chain, the assignment does not succeed:</span></span>

```powershell
try
{
    $result = Write-Output 'Value' && $(throw 'Bad')
}
catch
{
    # Do nothing, just squash the error
}

"Result: $result"
```

```Output
Result:
```

### <a name="operator-syntax-and-precedence"></a><span data-ttu-id="8162b-128">运算符语法和优先级</span><span class="sxs-lookup"><span data-stu-id="8162b-128">Operator syntax and precedence</span></span>

<span data-ttu-id="8162b-129">与其他运算符不同， `&&` 并对 `||` 管道进行操作，而不是在或等表达式上操作 `+` `-and` 。</span><span class="sxs-lookup"><span data-stu-id="8162b-129">Unlike other operators, `&&` and `||` operate on pipelines, rather than on expressions like `+` or `-and`, for example.</span></span>

<span data-ttu-id="8162b-130">`&&` 和的 `||` 优先级低于管道 (`|`) 或重定向 (`>`) ，但优先级高于作业运算符 () `&` 、赋值 (`=`) 或分号 (`;`) 。</span><span class="sxs-lookup"><span data-stu-id="8162b-130">`&&` and `||` have a lower precedence than piping (`|`) or redirection (`>`), but a higher precedence than job operators (`&`), assignment (`=`) or semicolons (`;`).</span></span> <span data-ttu-id="8162b-131">这意味着，可以单独重定向管道链内的管道，并且可以将整个管道链 backgrounded、赋值给变量或分隔为语句。</span><span class="sxs-lookup"><span data-stu-id="8162b-131">This means that pipelines within a pipeline chain can be individually redirected, and that entire pipeline chains can be backgrounded, assigned to variables, or separated as statements.</span></span>

<span data-ttu-id="8162b-132">若要在管道链中使用低优先级语法，请考虑使用括号 `(...)` 。</span><span class="sxs-lookup"><span data-stu-id="8162b-132">To use lower precedence syntax within a pipeline chain, consider the use of parentheses `(...)`.</span></span>
<span data-ttu-id="8162b-133">同样，若要在管道链中嵌入语句， `$(...)` 可以使用子表达式。</span><span class="sxs-lookup"><span data-stu-id="8162b-133">Similarly, to embed a statement within a pipeline chain, a subexpression `$(...)` can be used.</span></span>
<span data-ttu-id="8162b-134">这可用于结合控制流的本机命令：</span><span class="sxs-lookup"><span data-stu-id="8162b-134">This can be useful for combining native commands with control flow:</span></span>

```powershell
foreach ($file in 'file1','file2','file3')
{
    # When find succeeds, the loop breaks
    find $file && Write-Output "Found $file" && $(break)
}
```

```Output
find: file1: No such file or directory
file2
Found file2
```

<span data-ttu-id="8162b-135">从 PowerShell 7 起，这些语法的行为已更改，以便 `$?` 在命令在括号或子表达式内成功或失败时设置为预期。</span><span class="sxs-lookup"><span data-stu-id="8162b-135">As of PowerShell 7, the behaviour of these syntaxes has been changed so that `$?` is set as expected when a command succeeds or fails within parentheses or a subexpression.</span></span>

<span data-ttu-id="8162b-136">与 PowerShell 中的大多数其他运算符一样， `&&` 和 `||` 都是 *左结合* 运算符，这意味着它们从左侧进行分组。</span><span class="sxs-lookup"><span data-stu-id="8162b-136">Like most other operators in PowerShell, `&&` and `||` are also *left-associative* , meaning they group from the left.</span></span> <span data-ttu-id="8162b-137">例如：</span><span class="sxs-lookup"><span data-stu-id="8162b-137">For example:</span></span>

```powershell
Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist" && Get-Content -Raw ./file.txt
```

<span data-ttu-id="8162b-138">将按以下方式分组：</span><span class="sxs-lookup"><span data-stu-id="8162b-138">will group as:</span></span>

```
[Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist"] && Get-Content -Raw ./file.txt
```

<span data-ttu-id="8162b-139">等效于：</span><span class="sxs-lookup"><span data-stu-id="8162b-139">being equivalent to:</span></span>

```powershell
Get-ChildItem -Path ./file.txt

if (-not $?) { Write-Error "file.txt does not exist" }

if ($?) { Get-Content -Raw ./file.txt }
```

### <a name="error-interaction"></a><span data-ttu-id="8162b-140">错误交互</span><span class="sxs-lookup"><span data-stu-id="8162b-140">Error interaction</span></span>

<span data-ttu-id="8162b-141">管道链运算符不会吸收错误。</span><span class="sxs-lookup"><span data-stu-id="8162b-141">Pipeline chain operators do not absorb errors.</span></span> <span data-ttu-id="8162b-142">当管道链中的语句引发脚本终止错误时，管道链将终止。</span><span class="sxs-lookup"><span data-stu-id="8162b-142">When a statement in a pipeline chain throws a script-terminating error, the pipeline chain is terminated.</span></span>

<span data-ttu-id="8162b-143">例如：</span><span class="sxs-lookup"><span data-stu-id="8162b-143">For example:</span></span>

```powershell
$(throw 'Bad') || Write-Output '2'
```

```Output
Exception: Bad
```

<span data-ttu-id="8162b-144">即使捕获到错误，管道链仍会终止：</span><span class="sxs-lookup"><span data-stu-id="8162b-144">Even when the error is caught, the pipeline chain is still terminated:</span></span>

```powershell
try
{
    $(throw 'Bad') || Write-Output '2'
}
catch
{
    Write-Output "Caught: $_"
}
Write-Output 'Done'
```

```Output
Caught: Bad
Done
```

<span data-ttu-id="8162b-145">如果错误是非终止的，或者只是终止了管道，则管道链将继续，并遵从的值 `$?` ：</span><span class="sxs-lookup"><span data-stu-id="8162b-145">If an error is non-terminating, or only terminates a pipeline, the pipeline chain continues, respecting the value of `$?`:</span></span>

```powershell
function Test-NonTerminatingError
{
    [CmdletBinding()]
    param()

    $exception = [System.Exception]::new('BAD')
    $errorId = 'BAD'
    $errorCategory = 'NotSpecified'

    $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

    $PSCmdlet.WriteError($errorRecord)
}

Test-NonTerminatingError || Write-Output 'Second'
```

```Output
Test-NonTerminatingError: BAD
Second
```

### <a name="chaining-pipelines-rather-than-commands"></a><span data-ttu-id="8162b-146">链接管道，而不是命令</span><span class="sxs-lookup"><span data-stu-id="8162b-146">Chaining pipelines rather than commands</span></span>

<span data-ttu-id="8162b-147">管道链运算符（按其名称）可用于链接管道，而不只是命令。</span><span class="sxs-lookup"><span data-stu-id="8162b-147">Pipeline chain operators, by their name, can be used to chain pipelines, rather than just commands.</span></span> <span data-ttu-id="8162b-148">这与其他 shell 的行为匹配，但可能会导致难以 *成功* 确定：</span><span class="sxs-lookup"><span data-stu-id="8162b-148">This matches the behavior of other shells, but can make *success* harder to determine:</span></span>

```powershell
function Test-NotTwo
{
    [CmdletBinding()]
    param(
      [Parameter(ValueFromPipeline)]
      $Input
    )

    process
    {
        if ($Input -ne 2)
        {
            return $Input
        }

        $exception = [System.Exception]::new('Input is 2')
        $errorId = 'InputTwo'
        $errorCategory = 'InvalidData'

        $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

        $PSCmdlet.WriteError($errorRecord)
    }
}

1,2,3 | Test-NotTwo && Write-Output 'All done!'
```

```Output
1
Test-NotTwo : Input is 2
3
```

<span data-ttu-id="8162b-149">请注意， `Write-Output 'All done!'` 不会执行，因为在 `Test-NotTwo` 生成非终止错误后被视为已失败。</span><span class="sxs-lookup"><span data-stu-id="8162b-149">Note that `Write-Output 'All done!'` is not executed, since `Test-NotTwo` is deemed to have failed after generating the non-terminating error.</span></span>

## <a name="see-also"></a><span data-ttu-id="8162b-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8162b-150">See also</span></span>

- [<span data-ttu-id="8162b-151">about_Operators</span><span class="sxs-lookup"><span data-stu-id="8162b-151">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="8162b-152">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="8162b-152">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)
- [<span data-ttu-id="8162b-153">about_pipelines</span><span class="sxs-lookup"><span data-stu-id="8162b-153">about_pipelines</span></span>](about_pipelines.md)

