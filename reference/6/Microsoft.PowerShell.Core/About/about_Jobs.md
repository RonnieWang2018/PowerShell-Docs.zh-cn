---
description: 提供有关 PowerShell 后台作业如何在后台运行命令或表达式，而不与当前会话交互的信息。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_jobs?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Jobs
ms.openlocfilehash: 6ddb54bac62e7bc11a045874700acb3982a0093b
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524444"
---
# <a name="about-jobs"></a><span data-ttu-id="910d6-104">关于作业</span><span class="sxs-lookup"><span data-stu-id="910d6-104">About Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="910d6-105">简短说明</span><span class="sxs-lookup"><span data-stu-id="910d6-105">Short description</span></span>
<span data-ttu-id="910d6-106">提供有关 PowerShell 后台作业如何在后台运行命令或表达式，而不与当前会话交互的信息。</span><span class="sxs-lookup"><span data-stu-id="910d6-106">Provides information about how PowerShell background jobs run a command or expression in the background without interacting with the current session.</span></span>

## <a name="long-description"></a><span data-ttu-id="910d6-107">长说明</span><span class="sxs-lookup"><span data-stu-id="910d6-107">Long description</span></span>

<span data-ttu-id="910d6-108">PowerShell 通过作业并发运行命令和脚本。</span><span class="sxs-lookup"><span data-stu-id="910d6-108">PowerShell concurrently runs commands and scripts through jobs.</span></span> <span data-ttu-id="910d6-109">PowerShell 提供三种作业类型来支持并发。</span><span class="sxs-lookup"><span data-stu-id="910d6-109">There are three jobs types provided by PowerShell to support concurrency.</span></span>

- <span data-ttu-id="910d6-110">`RemoteJob` -命令和脚本在远程会话上运行。</span><span class="sxs-lookup"><span data-stu-id="910d6-110">`RemoteJob` - Commands and scripts run on a remote session.</span></span> <span data-ttu-id="910d6-111">有关信息，请参阅 [about_Remote_Jobs](about_Remote_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="910d6-111">For information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
- <span data-ttu-id="910d6-112">`BackgroundJob` -命令和脚本在本地计算机上的单独进程中运行。</span><span class="sxs-lookup"><span data-stu-id="910d6-112">`BackgroundJob` - Commands and scripts run in a separate process on the local machine.</span></span>
- <span data-ttu-id="910d6-113">`PSTaskJob` 或 `ThreadJob` -命令和脚本在本地计算机上的同一进程内的单独线程中运行。</span><span class="sxs-lookup"><span data-stu-id="910d6-113">`PSTaskJob` or `ThreadJob` - Commands and scripts run in a separate thread within the same process on the local machine.</span></span> <span data-ttu-id="910d6-114">有关详细信息，请参阅 [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs)。</span><span class="sxs-lookup"><span data-stu-id="910d6-114">For more information, see [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs).</span></span>

<span data-ttu-id="910d6-115">在单独的计算机上或在单独的进程中远程运行脚本可提供强大的隔离。</span><span class="sxs-lookup"><span data-stu-id="910d6-115">Running scripts remotely, on a separate machine or in a separate process, provides great isolation.</span></span> <span data-ttu-id="910d6-116">远程作业中发生的任何错误都不会影响其他正在运行的作业或启动作业的父会话。</span><span class="sxs-lookup"><span data-stu-id="910d6-116">Any errors that occur in the remote job do not affect other running jobs or the parent session that started the job.</span></span> <span data-ttu-id="910d6-117">但是，远程处理层增加了开销，包括对象序列化。</span><span class="sxs-lookup"><span data-stu-id="910d6-117">However, the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="910d6-118">所有对象都将进行序列化和反序列化，因为在父会话与远程 (作业) 会话之间传递它们。</span><span class="sxs-lookup"><span data-stu-id="910d6-118">All objects are serialized and deserialized as they are passed between the parent session and the remote (job) session.</span></span> <span data-ttu-id="910d6-119">大型复杂数据对象的序列化会消耗大量的计算和内存资源，并跨网络传输大量数据。</span><span class="sxs-lookup"><span data-stu-id="910d6-119">Serialization of large complex data objects can consume large amounts of compute and memory resources and transfer large amounts of data across the network.</span></span>

<span data-ttu-id="910d6-120">基于线程的作业不像远程和后台作业那样可靠，因为它们在不同线程上的同一进程中运行。</span><span class="sxs-lookup"><span data-stu-id="910d6-120">Thread-based jobs are not as robust as remote and background jobs, because they run in the same process on different threads.</span></span> <span data-ttu-id="910d6-121">如果一个作业发生了导致进程崩溃的严重错误，则会终止该进程中的所有其他作业。</span><span class="sxs-lookup"><span data-stu-id="910d6-121">If one job has a critical error that crashes the process, then all other jobs in the process are terminated.</span></span>

<span data-ttu-id="910d6-122">但是，基于线程的作业需要更少的开销。</span><span class="sxs-lookup"><span data-stu-id="910d6-122">However, thread-based jobs require less overhead.</span></span> <span data-ttu-id="910d6-123">它们不使用远程层或序列化。</span><span class="sxs-lookup"><span data-stu-id="910d6-123">They don't use the remoting layer or serialization.</span></span> <span data-ttu-id="910d6-124">结果对象作为对当前会话中活动对象的引用返回。</span><span class="sxs-lookup"><span data-stu-id="910d6-124">The result objects are returned as references to live objects in the current session.</span></span> <span data-ttu-id="910d6-125">如果没有此开销，基于线程的作业运行速度更快，使用的资源比其他作业类型少。</span><span class="sxs-lookup"><span data-stu-id="910d6-125">Without this overhead, thread-based jobs run faster and use fewer resources than the other job types.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="910d6-126">创建作业的父会话还会监视作业状态和收集管道数据。</span><span class="sxs-lookup"><span data-stu-id="910d6-126">The parent session that created the job also monitors the job status and collects pipeline data.</span></span> <span data-ttu-id="910d6-127">作业到达完成状态后，父进程终止了作业子进程。</span><span class="sxs-lookup"><span data-stu-id="910d6-127">The job child process is terminated by the parent process once the job reaches a finished state.</span></span> <span data-ttu-id="910d6-128">如果终止了父会话，则所有正在运行的子作业都将与其子进程一起终止。</span><span class="sxs-lookup"><span data-stu-id="910d6-128">If the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span>

<span data-ttu-id="910d6-129">有两种方法可解决此限制：</span><span class="sxs-lookup"><span data-stu-id="910d6-129">There are two ways work around this limitation:</span></span>

1. <span data-ttu-id="910d6-130">用于 `Invoke-Command` 创建在断开连接的会话中运行的作业。</span><span class="sxs-lookup"><span data-stu-id="910d6-130">Use `Invoke-Command` to create jobs that run in disconnected sessions.</span></span> <span data-ttu-id="910d6-131">有关详细信息，请参阅 [about_Remote_Jobs](about_Remote_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="910d6-131">For more information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
1. <span data-ttu-id="910d6-132">使用 `Start-Process` 创建新进程，而不是作业。</span><span class="sxs-lookup"><span data-stu-id="910d6-132">Use `Start-Process` to create a new process rather than a job.</span></span> <span data-ttu-id="910d6-133">有关详细信息，请参阅 [开始处理](xref:Microsoft.PowerShell.Management.Start-Process)。</span><span class="sxs-lookup"><span data-stu-id="910d6-133">For more information, see [Start-Process](xref:Microsoft.PowerShell.Management.Start-Process).</span></span>

## <a name="the-job-cmdlets"></a><span data-ttu-id="910d6-134">作业 cmdlet</span><span class="sxs-lookup"><span data-stu-id="910d6-134">The job cmdlets</span></span>

|<span data-ttu-id="910d6-135">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="910d6-135">Cmdlet</span></span>          |<span data-ttu-id="910d6-136">说明</span><span class="sxs-lookup"><span data-stu-id="910d6-136">Description</span></span>                                            |
|----------------|-------------------------------------------------------|
|`Start-Job`     |<span data-ttu-id="910d6-137">在本地计算机上启动后台作业。</span><span class="sxs-lookup"><span data-stu-id="910d6-137">Starts a background job on a local computer.</span></span>           |
|`Get-Job`       |<span data-ttu-id="910d6-138">获取在中启动的后台作业</span><span class="sxs-lookup"><span data-stu-id="910d6-138">Gets the background jobs that were started in the</span></span>      |
|                |<span data-ttu-id="910d6-139">当前会话。</span><span class="sxs-lookup"><span data-stu-id="910d6-139">current session.</span></span>                                       |
|`Receive-Job`   |<span data-ttu-id="910d6-140">获取后台作业的结果。</span><span class="sxs-lookup"><span data-stu-id="910d6-140">Gets the results of background jobs.</span></span>                   |
|`Stop-Job`      |<span data-ttu-id="910d6-141">停止后台作业。</span><span class="sxs-lookup"><span data-stu-id="910d6-141">Stops a background job.</span></span>                                |
|`Wait-Job`      |<span data-ttu-id="910d6-142">禁止显示命令提示符，直到其中一个或所有作业都为</span><span class="sxs-lookup"><span data-stu-id="910d6-142">Suppresses the command prompt until one or all jobs are</span></span>|
|                |<span data-ttu-id="910d6-143">完成.</span><span class="sxs-lookup"><span data-stu-id="910d6-143">complete.</span></span>                                              |
|`Remove-Job`    |<span data-ttu-id="910d6-144">删除后台作业。</span><span class="sxs-lookup"><span data-stu-id="910d6-144">Deletes a background job.</span></span>                              |
|`Invoke-Command`|<span data-ttu-id="910d6-145">**AsJob** 参数在上创建后台作业</span><span class="sxs-lookup"><span data-stu-id="910d6-145">The **AsJob** parameter creates a background job on a</span></span>  |
|                |<span data-ttu-id="910d6-146">远程计算机。</span><span class="sxs-lookup"><span data-stu-id="910d6-146">remote computer.</span></span> <span data-ttu-id="910d6-147">你可以使用 `Invoke-Command` 运行</span><span class="sxs-lookup"><span data-stu-id="910d6-147">You can use `Invoke-Command` to run</span></span>   |
|                |<span data-ttu-id="910d6-148">任何远程作业命令，包括 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="910d6-148">any job command remotely, including `Start-Job`.</span></span>       |

## <a name="how-to-start-a-job-on-the-local-computer"></a><span data-ttu-id="910d6-149">如何在本地计算机上启动作业</span><span class="sxs-lookup"><span data-stu-id="910d6-149">How to start a job on the local computer</span></span>

<span data-ttu-id="910d6-150">若要在本地计算机上启动后台作业，请使用 `Start-Job` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="910d6-150">To start a background job on the local computer, use the `Start-Job` cmdlet.</span></span>

<span data-ttu-id="910d6-151">若要编写 `Start-Job` 命令，请将作业运行的命令括在大括号中， (`{}`) 。</span><span class="sxs-lookup"><span data-stu-id="910d6-151">To write a `Start-Job` command, enclose the command that the job runs in curly braces (`{}`).</span></span> <span data-ttu-id="910d6-152">使用 **ScriptBlock** 参数来指定命令。</span><span class="sxs-lookup"><span data-stu-id="910d6-152">Use the **ScriptBlock** parameter to specify the command.</span></span>

<span data-ttu-id="910d6-153">下面的命令启动在 `Get-Process` 本地计算机上运行命令的后台作业。</span><span class="sxs-lookup"><span data-stu-id="910d6-153">The following command starts a background job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="910d6-154">启动后台作业时，命令提示符会立即返回，即使作业需要很长时间才能完成。</span><span class="sxs-lookup"><span data-stu-id="910d6-154">When you start a background job, the command prompt returns immediately, even if the job takes an extended time to complete.</span></span> <span data-ttu-id="910d6-155">当该作业运行时，你可以继续在此会话中工作而不会发生中断。</span><span class="sxs-lookup"><span data-stu-id="910d6-155">You can continue to work in the session without interruption while the job runs.</span></span>

<span data-ttu-id="910d6-156">`Start-Job`命令返回一个表示作业的对象。</span><span class="sxs-lookup"><span data-stu-id="910d6-156">The `Start-Job` command returns an object that represents the job.</span></span> <span data-ttu-id="910d6-157">作业对象包含有关该作业的有用信息，但是不包含作业结果。</span><span class="sxs-lookup"><span data-stu-id="910d6-157">The job object contains useful information about the job, but it does not contain the job results.</span></span>

<span data-ttu-id="910d6-158">可以将作业对象保存在变量中，然后将其与其他 **作业** cmdlet 一起使用来管理后台作业。</span><span class="sxs-lookup"><span data-stu-id="910d6-158">You can save the job object in a variable and then use it with the other **Job** cmdlets to manage the background job.</span></span> <span data-ttu-id="910d6-159">下面的命令启动作业对象并将生成的作业对象保存在 `$job` 变量中。</span><span class="sxs-lookup"><span data-stu-id="910d6-159">The following command starts a job object and saves the resulting job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="910d6-160">从 PowerShell 6.0 开始，可以使用 `&` 管道末尾 () 后台运算符来启动后台作业。</span><span class="sxs-lookup"><span data-stu-id="910d6-160">Beginning in PowerShell 6.0, you can use the background operator (`&`) at the end of a pipeline to start a background job.</span></span> <span data-ttu-id="910d6-161">有关详细信息，请参阅 [背景运算符](about_Operators.md#background-operator-)。</span><span class="sxs-lookup"><span data-stu-id="910d6-161">For more information, see [background operator](about_Operators.md#background-operator-).</span></span>

<span data-ttu-id="910d6-162">使用 background 运算符在功能上等效于 `Start-Job` 在上一示例中使用 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="910d6-162">Using the background operator is functionally equivalent to using the `Start-Job` cmdlet in the previous example.</span></span>

```powershell
$job = Get-Process &
```

## <a name="getting-job-objects"></a><span data-ttu-id="910d6-163">正在获取作业对象</span><span class="sxs-lookup"><span data-stu-id="910d6-163">Getting job objects</span></span>

<span data-ttu-id="910d6-164">`Get-Job`Cmdlet 返回对象，这些对象表示在当前会话中启动的后台作业。</span><span class="sxs-lookup"><span data-stu-id="910d6-164">The `Get-Job` cmdlet returns objects that represent the background jobs that were started in the current session.</span></span> <span data-ttu-id="910d6-165">如果没有参数，则 `Get-Job` 返回在当前会话中启动的所有作业。</span><span class="sxs-lookup"><span data-stu-id="910d6-165">Without parameters, `Get-Job` returns all of the jobs that were started in the current session.</span></span>

```powershell
Get-Job
```

<span data-ttu-id="910d6-166">作业对象包含作业的状态，该状态指示作业是否已完成。</span><span class="sxs-lookup"><span data-stu-id="910d6-166">The job object contains the state of the job, which indicates whether the job has finished.</span></span> <span data-ttu-id="910d6-167">已完成的作业的状态为 " **完成** " 或 " **失败** "。</span><span class="sxs-lookup"><span data-stu-id="910d6-167">A finished job has a state of **Complete** or **Failed**.</span></span> <span data-ttu-id="910d6-168">作业也可能被 **阻止** 或 **正在运行** 。</span><span class="sxs-lookup"><span data-stu-id="910d6-168">A job might also be **Blocked** or **Running**.</span></span>

```Output
Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

<span data-ttu-id="910d6-169">可以将作业对象保存在变量中，并在后面的命令中使用它来表示作业。</span><span class="sxs-lookup"><span data-stu-id="910d6-169">You can save the job object in a variable and use it to represent the job in a later command.</span></span> <span data-ttu-id="910d6-170">以下命令获取 ID 为1的作业，并将其保存在 `$job` 变量中。</span><span class="sxs-lookup"><span data-stu-id="910d6-170">The following command gets the job with ID 1 and saves it in the `$job` variable.</span></span>

```powershell
$job = Get-Job -Id 1
```

## <a name="getting-the-results-of-a-job"></a><span data-ttu-id="910d6-171">获取作业的结果</span><span class="sxs-lookup"><span data-stu-id="910d6-171">Getting the results of a job</span></span>

<span data-ttu-id="910d6-172">运行后台作业时，结果不会立即显示。</span><span class="sxs-lookup"><span data-stu-id="910d6-172">When you run a background job, the results do not appear immediately.</span></span> <span data-ttu-id="910d6-173">若要获取后台作业的结果，请使用 `Receive-Job` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="910d6-173">To get the results of a background job, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="910d6-174">下面的示例 `Receive-Job` 使用变量中的作业对象获取作业的结果 `$job` 。</span><span class="sxs-lookup"><span data-stu-id="910d6-174">The following example, the `Receive-Job` cmdlet gets the results of the job using job object in the `$job` variable.</span></span>

```powershell
Receive-Job -Job $job
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
    103       4    11328       9692    56           1176 audiodg
    804      14    12228      14108   100   101.74  1740 CcmExec
    668       7     2672       6168   104    32.26   488 csrss
...
```

<span data-ttu-id="910d6-175">可以将作业的结果保存在变量中。</span><span class="sxs-lookup"><span data-stu-id="910d6-175">You can save the results of a job in a variable.</span></span> <span data-ttu-id="910d6-176">以下命令将变量中的作业结果保存 `$job` 到 `$results` 变量中。</span><span class="sxs-lookup"><span data-stu-id="910d6-176">The following command saves the results of the job in the `$job` variable to the `$results` variable.</span></span>

```powershell
$results = Receive-Job -Job $job
```

### <a name="getting-and-keeping-partial-job-results"></a><span data-ttu-id="910d6-177">获取并保留部分作业结果</span><span class="sxs-lookup"><span data-stu-id="910d6-177">Getting and keeping partial job results</span></span>

<span data-ttu-id="910d6-178">`Receive-Job`Cmdlet 将获取后台作业的结果。</span><span class="sxs-lookup"><span data-stu-id="910d6-178">The `Receive-Job` cmdlet gets the results of a background job.</span></span> <span data-ttu-id="910d6-179">如果作业已完成，则 `Receive-Job` 获取所有作业结果。</span><span class="sxs-lookup"><span data-stu-id="910d6-179">If the job is complete, `Receive-Job` gets all job results.</span></span> <span data-ttu-id="910d6-180">如果作业仍在运行，将 `Receive-Job` 获取迄今为止生成的结果。</span><span class="sxs-lookup"><span data-stu-id="910d6-180">If the job is still running, `Receive-Job` gets the results that have been generated thus far.</span></span> <span data-ttu-id="910d6-181">可以再次运行 `Receive-Job` 命令来获取剩余结果。</span><span class="sxs-lookup"><span data-stu-id="910d6-181">You can run `Receive-Job` commands again to get the remaining results.</span></span>

<span data-ttu-id="910d6-182">默认情况下， `Receive-Job` 会从缓存中删除存储作业结果的结果。</span><span class="sxs-lookup"><span data-stu-id="910d6-182">By default, `Receive-Job` deletes the results from the cache where job results are stored.</span></span> <span data-ttu-id="910d6-183">再次运行时 `Receive-Job` ，只会获得首次运行后收到的新结果。</span><span class="sxs-lookup"><span data-stu-id="910d6-183">When you run `Receive-Job` again, you get only the new results that arrived after the first run.</span></span>

<span data-ttu-id="910d6-184">以下命令显示在 `Receive-Job` 作业完成之前运行的命令的结果。</span><span class="sxs-lookup"><span data-stu-id="910d6-184">The following commands show the results of `Receive-Job` commands run before the job is complete.</span></span>

```powershell
C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    68       3     2632        664    29     0.36   1388 ccmsetup
   749      22    21468      19940   203   122.13   3644 communicator
   905       7     2980       2628    34   197.97    424 csrss
  1121      25    28408      32940   174   430.14   3048 explorer
```

<span data-ttu-id="910d6-185">使用 **Keep** 参数防止 `Receive-Job` 删除返回的作业结果。</span><span class="sxs-lookup"><span data-stu-id="910d6-185">Use the **Keep** parameter to prevent `Receive-Job` from deleting the job results that are returned.</span></span> <span data-ttu-id="910d6-186">以下命令显示对尚未完成的作业使用 **Keep** 参数的效果。</span><span class="sxs-lookup"><span data-stu-id="910d6-186">The following commands show the effect of using the **Keep** parameter on a job that is not yet complete.</span></span>

```powershell
C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec
     68       3     2632        664    29     0.36   1388 ccmsetup
    749      22    21468      19940   203   122.13   3644 communicator
    905       7     2980       2628    34   197.97    424 csrss
   1121      25    28408      32940   174   430.14   3048 explorer
```

### <a name="waiting-for-the-results"></a><span data-ttu-id="910d6-187">正在等待结果</span><span class="sxs-lookup"><span data-stu-id="910d6-187">Waiting for the results</span></span>

<span data-ttu-id="910d6-188">如果运行需要很长时间才能完成的命令，则可以使用作业对象的属性来确定作业的完成时间。</span><span class="sxs-lookup"><span data-stu-id="910d6-188">If you run a command that takes a long time to complete, you can use the properties of the job object to determine when the job is complete.</span></span> <span data-ttu-id="910d6-189">以下命令使用 `Get-Job` 对象获取当前会话中的所有后台作业。</span><span class="sxs-lookup"><span data-stu-id="910d6-189">The following command uses the `Get-Job` object to get all of the background jobs in the current session.</span></span>

```powershell
Get-Job
```

<span data-ttu-id="910d6-190">结果将显示在表中。</span><span class="sxs-lookup"><span data-stu-id="910d6-190">The results appear in a table.</span></span> <span data-ttu-id="910d6-191">作业的状态显示在 " **状态** " 列中。</span><span class="sxs-lookup"><span data-stu-id="910d6-191">The status of the job appears in the **State** column.</span></span>

```Output
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

<span data-ttu-id="910d6-192">在这种情况下，" **状态** " 属性显示 "作业 2" 仍在运行。</span><span class="sxs-lookup"><span data-stu-id="910d6-192">In this case, the **State** property reveals that Job 2 is still running.</span></span> <span data-ttu-id="910d6-193">如果你 `Receive-Job` 现在使用 cmdlet 来获取作业结果，结果将不完整。</span><span class="sxs-lookup"><span data-stu-id="910d6-193">If you were to use the `Receive-Job` cmdlet to get the job results now, the results would be incomplete.</span></span> <span data-ttu-id="910d6-194">可以重复使用此 `Receive-Job` cmdlet 来获取所有结果。</span><span class="sxs-lookup"><span data-stu-id="910d6-194">You can use the `Receive-Job` cmdlet repeatedly to get all of the results.</span></span> <span data-ttu-id="910d6-195">使用 **State** 属性来确定作业的完成时间。</span><span class="sxs-lookup"><span data-stu-id="910d6-195">Use the **State** property to determine when the job is complete.</span></span>

<span data-ttu-id="910d6-196">你还可以使用该 cmdlet 的 **Wait** 参数 `Receive-Job` 。</span><span class="sxs-lookup"><span data-stu-id="910d6-196">You can also use the **Wait** parameter of the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="910d6-197">如果使用此参数，则在作业完成并且所有结果都可用之前，cmdlet 不会返回命令提示符。</span><span class="sxs-lookup"><span data-stu-id="910d6-197">When use use this parameter, the cmdlet does not return the command prompt until the job is completed and all results are available.</span></span>

<span data-ttu-id="910d6-198">你还可以使用 `Wait-Job` cmdlet 等待作业的任何或所有结果。</span><span class="sxs-lookup"><span data-stu-id="910d6-198">You can also use the `Wait-Job` cmdlet to wait for any or all of the results of the job.</span></span> <span data-ttu-id="910d6-199">`Wait-Job` 允许你等待一个或多个特定作业或所有作业。</span><span class="sxs-lookup"><span data-stu-id="910d6-199">`Wait-Job` lets you wait for one or more specific job or for all jobs.</span></span>
<span data-ttu-id="910d6-200">以下命令使用 `Wait-Job` cmdlet 等待 **ID** 为的作业</span><span class="sxs-lookup"><span data-stu-id="910d6-200">The following command uses the `Wait-Job` cmdlet to wait for a job with **ID**</span></span>
10.

```powershell
Wait-Job -ID 10
```

<span data-ttu-id="910d6-201">因此，在作业完成之前，会禁止 PowerShell 提示。</span><span class="sxs-lookup"><span data-stu-id="910d6-201">As a result, the PowerShell prompt is suppressed until the job is completed.</span></span>

<span data-ttu-id="910d6-202">还可以等待预先确定的时间段。</span><span class="sxs-lookup"><span data-stu-id="910d6-202">You can also wait for a predetermined period of time.</span></span> <span data-ttu-id="910d6-203">此命令使用 **Timeout** 参数将等待时间限制为120秒。</span><span class="sxs-lookup"><span data-stu-id="910d6-203">This command uses the **Timeout** parameter to limit the wait to 120 seconds.</span></span> <span data-ttu-id="910d6-204">当时间到期时，命令提示符会返回，但作业将继续在后台运行。</span><span class="sxs-lookup"><span data-stu-id="910d6-204">When the time expires, the command prompt returns, but the job continues to run in the background.</span></span>

```powershell
Wait-Job -ID 10 -Timeout 120
```

## <a name="stopping-a-job"></a><span data-ttu-id="910d6-205">停止作业</span><span class="sxs-lookup"><span data-stu-id="910d6-205">Stopping a job</span></span>

<span data-ttu-id="910d6-206">若要停止后台作业，请使用 `Stop-Job` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="910d6-206">To stop a background job, use the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="910d6-207">下面的命令启动一个作业以获取系统事件日志中的每个条目。</span><span class="sxs-lookup"><span data-stu-id="910d6-207">The following command starts a job to get every entry in the System event log.</span></span> <span data-ttu-id="910d6-208">它将作业对象保存在 `$job` 变量中。</span><span class="sxs-lookup"><span data-stu-id="910d6-208">It saves the job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-EventLog -Log System}
```

<span data-ttu-id="910d6-209">以下命令停止作业。</span><span class="sxs-lookup"><span data-stu-id="910d6-209">The following command stops the job.</span></span> <span data-ttu-id="910d6-210">它使用管道运算符 (`|`) 将变量中的作业发送 `$job` 到 `Stop-Job` 。</span><span class="sxs-lookup"><span data-stu-id="910d6-210">It uses a pipeline operator (`|`) to send the job in the `$job` variable to `Stop-Job`.</span></span>

```powershell
$job | Stop-Job
```

## <a name="deleting-a-job"></a><span data-ttu-id="910d6-211">删除作业</span><span class="sxs-lookup"><span data-stu-id="910d6-211">Deleting a job</span></span>

<span data-ttu-id="910d6-212">若要删除后台作业，请使用 `Remove-Job` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="910d6-212">To delete a background job, use the `Remove-Job` cmdlet.</span></span> <span data-ttu-id="910d6-213">以下命令删除变量中的作业 `$job` 。</span><span class="sxs-lookup"><span data-stu-id="910d6-213">The following command deletes the job in the `$job` variable.</span></span>

```powershell
Remove-Job -Job $job
```

## <a name="investigating-a-failed-job"></a><span data-ttu-id="910d6-214">调查失败的作业</span><span class="sxs-lookup"><span data-stu-id="910d6-214">Investigating a failed job</span></span>

<span data-ttu-id="910d6-215">作业可能会因多种原因而失败。</span><span class="sxs-lookup"><span data-stu-id="910d6-215">Jobs can fail for many reasons.</span></span> <span data-ttu-id="910d6-216">作业对象包含 **Reason** 属性，其中包含有关失败原因的信息。</span><span class="sxs-lookup"><span data-stu-id="910d6-216">the job object contains a **Reason** property that contains information about the cause of the failure.</span></span>

<span data-ttu-id="910d6-217">下面的示例启动一个作业，该作业没有所需的凭据。</span><span class="sxs-lookup"><span data-stu-id="910d6-217">The following example starts a job without the required credentials.</span></span>

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}
Get-Job $job

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

<span data-ttu-id="910d6-218">检查 **原因** 属性以找到导致作业失败的错误。</span><span class="sxs-lookup"><span data-stu-id="910d6-218">Inspect the **Reason** property to find the error that caused the job to fail.</span></span>

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

<span data-ttu-id="910d6-219">在这种情况下，作业失败，因为远程计算机需要显式凭据才能运行该命令。</span><span class="sxs-lookup"><span data-stu-id="910d6-219">In this case, the job failed because the remote computer required explicit credentials to run the command.</span></span> <span data-ttu-id="910d6-220">**Reason** 属性包含以下消息：</span><span class="sxs-lookup"><span data-stu-id="910d6-220">The **Reason** property contains the following message:</span></span>

> <span data-ttu-id="910d6-221">连接到远程服务器失败，出现以下错误消息： "访问被拒绝"。</span><span class="sxs-lookup"><span data-stu-id="910d6-221">Connecting to remote server failed with the following error message: "Access is denied".</span></span>

## <a name="see-also"></a><span data-ttu-id="910d6-222">另请参阅</span><span class="sxs-lookup"><span data-stu-id="910d6-222">See also</span></span>

- [<span data-ttu-id="910d6-223">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="910d6-223">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="910d6-224">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="910d6-224">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="910d6-225">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="910d6-225">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="910d6-226">about_Remote</span><span class="sxs-lookup"><span data-stu-id="910d6-226">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="910d6-227">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="910d6-227">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="910d6-228">Start-Job</span><span class="sxs-lookup"><span data-stu-id="910d6-228">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="910d6-229">Get-Job</span><span class="sxs-lookup"><span data-stu-id="910d6-229">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="910d6-230">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="910d6-230">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="910d6-231">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="910d6-231">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="910d6-232">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="910d6-232">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="910d6-233">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="910d6-233">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="910d6-234">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="910d6-234">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
