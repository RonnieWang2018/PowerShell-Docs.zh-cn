---
description: PowerShell 记录来自引擎、提供程序和 cmdlet 的内部操作。
keywords: powershell
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_non-windows?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging_Non-Windows
ms.openlocfilehash: 402c59f839de4a2b16e2abde29e1e9cfa6be6fa7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/13/2020
ms.locfileid: "93199808"
---
# <a name="about-logging-non-windows"></a><span data-ttu-id="795fc-104">关于记录非 Windows</span><span class="sxs-lookup"><span data-stu-id="795fc-104">About Logging Non-Windows</span></span>

## <a name="short-description"></a><span data-ttu-id="795fc-105">简短说明</span><span class="sxs-lookup"><span data-stu-id="795fc-105">Short description</span></span>

<span data-ttu-id="795fc-106">PowerShell 记录来自引擎、提供程序和 cmdlet 的内部操作。</span><span class="sxs-lookup"><span data-stu-id="795fc-106">PowerShell logs internal operations from the engine, providers, and cmdlets.</span></span>

## <a name="long-description"></a><span data-ttu-id="795fc-107">长说明</span><span class="sxs-lookup"><span data-stu-id="795fc-107">Long description</span></span>

<span data-ttu-id="795fc-108">Powershell 日志详细信息。</span><span class="sxs-lookup"><span data-stu-id="795fc-108">PowerShell logs details of PowerShell operations.</span></span> <span data-ttu-id="795fc-109">例如，PowerShell 将记录启动和停止引擎以及启动和停止提供程序等操作。</span><span class="sxs-lookup"><span data-stu-id="795fc-109">For example, PowerShell will log operations such as starting and stopping the engine and starting and stopping providers.</span></span> <span data-ttu-id="795fc-110">它还将记录有关 PowerShell 命令的详细信息。</span><span class="sxs-lookup"><span data-stu-id="795fc-110">It will also log details about PowerShell commands.</span></span>

<span data-ttu-id="795fc-111">PowerShell 日志的位置取决于目标平台。</span><span class="sxs-lookup"><span data-stu-id="795fc-111">The location of PowerShell logs is dependent on the target platform.</span></span> <span data-ttu-id="795fc-112">在 **Linux** 上，可以使用将 PowerShell 日志到 **syslog** 和 **rsyslog** 。</span><span class="sxs-lookup"><span data-stu-id="795fc-112">On **Linux** , PowerShell logs to **syslog** and **rsyslog.conf** can be used.</span></span> <span data-ttu-id="795fc-113">有关详细信息，请参阅 Linux 计算机的本地 `man` 页面。</span><span class="sxs-lookup"><span data-stu-id="795fc-113">For more information, refer to the Linux computer's local `man` pages.</span></span> <span data-ttu-id="795fc-114">在 **macOS** 上，使用 **os_log** 日志记录系统。</span><span class="sxs-lookup"><span data-stu-id="795fc-114">On **macOS** , the **os_log** logging system is used.</span></span> <span data-ttu-id="795fc-115">有关详细信息，请参阅 [os_log 开发人员文档](https://developer.apple.com/documentation/os/os_log)。</span><span class="sxs-lookup"><span data-stu-id="795fc-115">For more information, see [os_log developer documentation](https://developer.apple.com/documentation/os/os_log).</span></span>

## <a name="viewing-powershell-log-output-on-linux"></a><span data-ttu-id="795fc-116">在 Linux 上查看 PowerShell 日志输出</span><span class="sxs-lookup"><span data-stu-id="795fc-116">Viewing PowerShell log output on Linux</span></span>

<span data-ttu-id="795fc-117">可以使用 Linux 上 **syslog** 中的日志以及通常用于查看 **syslog** 内容的任何工具。</span><span class="sxs-lookup"><span data-stu-id="795fc-117">PowerShell logs to **syslog** on Linux and any of the tools commonly used to view **syslog** contents may be used.</span></span>

<span data-ttu-id="795fc-118">日志条目的格式使用以下模板：</span><span class="sxs-lookup"><span data-stu-id="795fc-118">The format of the log entries uses the following template:</span></span>

```
TIMESTAMP MACHINENAME powershell[PID]: (COMMITID:TID:CID)
  [EVENTID:TASK.OPCODE.LEVEL] MESSAGE
```

|<span data-ttu-id="795fc-119">字段</span><span class="sxs-lookup"><span data-stu-id="795fc-119">Field</span></span>        |<span data-ttu-id="795fc-120">说明</span><span class="sxs-lookup"><span data-stu-id="795fc-120">Description</span></span>                                             |
|-------------|--------------------------------------------------------|
|`TIMESTAMP`  |<span data-ttu-id="795fc-121">生成日志条目的日期/时间。</span><span class="sxs-lookup"><span data-stu-id="795fc-121">A date/time when the log entry was produced.</span></span>            |
|`MACHINENAME`|<span data-ttu-id="795fc-122">生成日志的系统的名称。</span><span class="sxs-lookup"><span data-stu-id="795fc-122">The name of the system where the log was produced.</span></span>      |
|`PID`        |<span data-ttu-id="795fc-123">写入日志项的进程的进程 ID。</span><span class="sxs-lookup"><span data-stu-id="795fc-123">The process ID of the process that wrote the log entry.</span></span> |
|`COMMITID`   |<span data-ttu-id="795fc-124">`git commit`用于生成生成的 ID 或标记。</span><span class="sxs-lookup"><span data-stu-id="795fc-124">The `git commit` ID or tag used to produce the build.</span></span>   |
|`TID`        |<span data-ttu-id="795fc-125">写入日志项的线程的线程 ID。</span><span class="sxs-lookup"><span data-stu-id="795fc-125">The thread ID of the thread that wrote the log entry.</span></span>   |
|`CID`        |<span data-ttu-id="795fc-126">日志条目的十六进制通道标识符。</span><span class="sxs-lookup"><span data-stu-id="795fc-126">The hex channel identifier of the log entry.</span></span>            |
|             |<span data-ttu-id="795fc-127">10 = 操作，11 = 分析</span><span class="sxs-lookup"><span data-stu-id="795fc-127">10 = Operational, 11 = Analytic</span></span>                         |
|`EVENTID`    |<span data-ttu-id="795fc-128">日志条目的事件标识符。</span><span class="sxs-lookup"><span data-stu-id="795fc-128">The event identifier of the log entry.</span></span>                  |
|`TASK`       |<span data-ttu-id="795fc-129">事件项的任务标识符</span><span class="sxs-lookup"><span data-stu-id="795fc-129">The task identifier for the event entry</span></span>                 |
|`OPCODE`     |<span data-ttu-id="795fc-130">事件项的操作码</span><span class="sxs-lookup"><span data-stu-id="795fc-130">The opcode for the event entry</span></span>                          |
|`LEVEL`      |<span data-ttu-id="795fc-131">事件项的日志级别</span><span class="sxs-lookup"><span data-stu-id="795fc-131">The log level for the event entry</span></span>                       |
|`MESSAGE`    |<span data-ttu-id="795fc-132">与事件项关联的消息</span><span class="sxs-lookup"><span data-stu-id="795fc-132">The message associated with the event entry</span></span>             |

> [!NOTE]
> <span data-ttu-id="795fc-133">`EVENTID`、 `TASK` 、 `OPCODE` 和与 `LEVEL` 日志记录到 Windows 事件日志时使用的值相同。</span><span class="sxs-lookup"><span data-stu-id="795fc-133">`EVENTID`, `TASK`, `OPCODE`, and `LEVEL` are the same values as used when logging to the Windows event log.</span></span>

### <a name="filtering-powershell-log-entries-using-rsyslog"></a><span data-ttu-id="795fc-134">使用 rsyslog 筛选 PowerShell 日志条目</span><span class="sxs-lookup"><span data-stu-id="795fc-134">Filtering PowerShell log entries using rsyslog</span></span>

<span data-ttu-id="795fc-135">通常情况下，会将 PowerShell 日志条目写入 `location/file` **syslog** 的默认值。</span><span class="sxs-lookup"><span data-stu-id="795fc-135">Normally, PowerShell log entries are written to the default `location/file` for **syslog** .</span></span> <span data-ttu-id="795fc-136">但是，可以将条目重定向到自定义文件。</span><span class="sxs-lookup"><span data-stu-id="795fc-136">However, it's possible to redirect the entries to a custom file.</span></span>

1. <span data-ttu-id="795fc-137">为 PowerShell 日志配置创建会议，并为) 提供小于 50 (的数字 `50-default.conf` ，如 `40-powershell.conf` 。</span><span class="sxs-lookup"><span data-stu-id="795fc-137">Create a conf for PowerShell log configuration and provide a number that's less than 50 (for `50-default.conf`), such as `40-powershell.conf`.</span></span> <span data-ttu-id="795fc-138">文件应位于下 `/etc/rsyslog.d` 。</span><span class="sxs-lookup"><span data-stu-id="795fc-138">The file should be placed under `/etc/rsyslog.d`.</span></span>

1. <span data-ttu-id="795fc-139">将以下条目添加到文件：</span><span class="sxs-lookup"><span data-stu-id="795fc-139">Add the following entry to the file:</span></span>

   ```
   :syslogtag, contains, "powershell[" /var/log/powershell.log
   & stop
   ```

1. <span data-ttu-id="795fc-140">请确保 `/etc/rsyslog.conf` 包含新的文件。</span><span class="sxs-lookup"><span data-stu-id="795fc-140">Make sure `/etc/rsyslog.conf` includes the new file.</span></span> <span data-ttu-id="795fc-141">通常，它将具有如下所示的一般包含语句：</span><span class="sxs-lookup"><span data-stu-id="795fc-141">Often, it will have a generic include statement that looks like following configuration:</span></span>

   `$IncludeConfig /etc/rsyslog.d/*.conf`

   <span data-ttu-id="795fc-142">如果不是，则需要手动添加 include 语句。</span><span class="sxs-lookup"><span data-stu-id="795fc-142">If it doesn't, you'll need to add an include statement manually.</span></span>

1. <span data-ttu-id="795fc-143">请确保正确设置属性和权限。</span><span class="sxs-lookup"><span data-stu-id="795fc-143">Make sure attributes and permissions are set appropriately.</span></span>

   ```
   -rw-r--r-- 1 root root   67 Nov 28 12:51 40-powershell.conf
   ```

1. <span data-ttu-id="795fc-144">将所有权设置为 **root** 。</span><span class="sxs-lookup"><span data-stu-id="795fc-144">Set ownership to **root** .</span></span>

   ```
   chown root:root /etc/rsyslog.d/40-powershell.conf
   ```

1. <span data-ttu-id="795fc-145">设置访问权限： **root** 具有读/写权限， **用户** 已读取。</span><span class="sxs-lookup"><span data-stu-id="795fc-145">Set access permissions: **root** has read/write, **users** have read.</span></span>

   ```
   chmod 644 /etc/rsyslog.d/40-powershell.conf
   ```

## <a name="viewing-powershell-log-output-on-macos"></a><span data-ttu-id="795fc-146">查看 macOS 上的 PowerShell 日志输出</span><span class="sxs-lookup"><span data-stu-id="795fc-146">Viewing PowerShell log output on macOS</span></span>

<span data-ttu-id="795fc-147">在 macOS 上查看 PowerShell 日志输出的最简单方法是使用 **控制台** 应用程序。</span><span class="sxs-lookup"><span data-stu-id="795fc-147">The easiest method for viewing PowerShell log output on macOS is using the **Console** application.</span></span>

1. <span data-ttu-id="795fc-148">搜索 **控制台** 应用程序并启动它。</span><span class="sxs-lookup"><span data-stu-id="795fc-148">Search for the **Console** application and launch it.</span></span>
1. <span data-ttu-id="795fc-149">在 " **设备** " 下选择计算机名称。</span><span class="sxs-lookup"><span data-stu-id="795fc-149">Select the Machine name under **Devices** .</span></span>
1. <span data-ttu-id="795fc-150">在 **搜索** 字段中， `pwsh` 为 PowerShell 主二进制文件输入。</span><span class="sxs-lookup"><span data-stu-id="795fc-150">In the **Search** field, enter `pwsh` for the PowerShell main binary.</span></span>
1. <span data-ttu-id="795fc-151">将搜索筛选器从更改 `Any` 为 `Process` 。</span><span class="sxs-lookup"><span data-stu-id="795fc-151">Change the search filter from `Any` to `Process`.</span></span>
1. <span data-ttu-id="795fc-152">执行操作。</span><span class="sxs-lookup"><span data-stu-id="795fc-152">Perform the operations.</span></span>
1. <span data-ttu-id="795fc-153">还可以选择保存搜索以便将来使用。</span><span class="sxs-lookup"><span data-stu-id="795fc-153">Optionally, save the search for future use.</span></span>

<span data-ttu-id="795fc-154">若要在 **控制台** 中筛选 PowerShell 的特定进程实例，该变量 `$pid` 包含进程 ID。</span><span class="sxs-lookup"><span data-stu-id="795fc-154">To filter on a specific process instance of PowerShell in the **Console** , the variable `$pid` contains the process ID.</span></span>

1. <span data-ttu-id="795fc-155">在 **搜索** 字段中输入 **PID** (进程 ID) 。</span><span class="sxs-lookup"><span data-stu-id="795fc-155">Enter the **pid** (Process ID) in the **Search** field.</span></span>
1. <span data-ttu-id="795fc-156">将搜索筛选器更改为 `PID` 。</span><span class="sxs-lookup"><span data-stu-id="795fc-156">Change the search filter to `PID`.</span></span>
1. <span data-ttu-id="795fc-157">执行操作。</span><span class="sxs-lookup"><span data-stu-id="795fc-157">Perform the operations.</span></span>

### <a name="viewing-powershell-log-output-from-a-command-line"></a><span data-ttu-id="795fc-158">从命令行查看 PowerShell 日志输出</span><span class="sxs-lookup"><span data-stu-id="795fc-158">Viewing PowerShell log output from a command line</span></span>

<span data-ttu-id="795fc-159">`log`命令可用于从命令行查看 PowerShell 日志条目。</span><span class="sxs-lookup"><span data-stu-id="795fc-159">The `log` command can be used to view PowerShell log entries from the command line.</span></span>

```
sudo log stream --predicate 'process == "pwsh"' --info
```

### <a name="persisting-powershell-log-output"></a><span data-ttu-id="795fc-160">保留 PowerShell 日志输出</span><span class="sxs-lookup"><span data-stu-id="795fc-160">Persisting PowerShell log output</span></span>

<span data-ttu-id="795fc-161">默认情况下，PowerShell 使用 macOS 上默认的仅内存日志记录。</span><span class="sxs-lookup"><span data-stu-id="795fc-161">By default, PowerShell uses the default memory-only logging on macOS.</span></span> <span data-ttu-id="795fc-162">此行为可以更改为使用命令启用持久性 `log config` 。</span><span class="sxs-lookup"><span data-stu-id="795fc-162">This behavior can be changed to enable persistence using the `log config` command.</span></span>

<span data-ttu-id="795fc-163">以下脚本启用信息级别的日志记录和持久性：</span><span class="sxs-lookup"><span data-stu-id="795fc-163">The following script enables info level logging and persistence:</span></span>

```
log config --subsystem com.microsoft.powershell --mode=persist:info,level:info
```

<span data-ttu-id="795fc-164">以下命令将 PowerShell 日志记录还原为默认状态：</span><span class="sxs-lookup"><span data-stu-id="795fc-164">The following command reverts PowerShell logging to the default state:</span></span>

```
log config --subsystem com.microsoft.powershell --mode=persist:default,level:default
```

<span data-ttu-id="795fc-165">启用持久性后， `log show` 可以使用命令来导出日志项。</span><span class="sxs-lookup"><span data-stu-id="795fc-165">After persistence is enabled, the `log show` command can be used to export log items.</span></span> <span data-ttu-id="795fc-166">此命令提供用于导出最后 N 项、自给定时间之后的项或给定时间跨度内的项的选项。</span><span class="sxs-lookup"><span data-stu-id="795fc-166">The command provides options for exporting the last N items, items since a given time, or items within a given time span.</span></span>

<span data-ttu-id="795fc-167">例如，以下命令导出后的项 `9am on April 5 of 2018` ：</span><span class="sxs-lookup"><span data-stu-id="795fc-167">For example, the following command exports items since `9am on April 5 of 2018`:</span></span>

```
log show --info --start "2018-04-05 09:00:00" --predicate "process = 'pwsh'"
```

<span data-ttu-id="795fc-168">可以 `log` 通过运行来获取有关 `log show --help` 更多详细信息的帮助。</span><span class="sxs-lookup"><span data-stu-id="795fc-168">You can get help for `log` by running `log show --help` for additional details.</span></span>

> [!TIP]
> <span data-ttu-id="795fc-169">在 PowerShell 提示符或脚本中执行任何日志命令时，请使用双引号将整个谓词字符串和内的单引号括起来。</span><span class="sxs-lookup"><span data-stu-id="795fc-169">When executing any of the log commands from a PowerShell prompt or script, use double quotes around the entire predicate string and single quotes within.</span></span> <span data-ttu-id="795fc-170">这样就无需在谓词字符串中转义双引号字符。</span><span class="sxs-lookup"><span data-stu-id="795fc-170">This avoids the need to escape double quote characters within the predicate string.</span></span>

<span data-ttu-id="795fc-171">你可能还需要考虑将事件日志保存到更安全的位置，例如中央事件日志收集器或 [SIEM][] 聚合器。</span><span class="sxs-lookup"><span data-stu-id="795fc-171">You may also want to consider saving the event logs to a more secure location such as a central event log collector, or [SIEM][] aggregator.</span></span> <span data-ttu-id="795fc-172">可以在 Azure 中设置 SIEM。</span><span class="sxs-lookup"><span data-stu-id="795fc-172">You can set up SIEM in Azure.</span></span> <span data-ttu-id="795fc-173">有关详细信息，请参阅 [通用 SIEM 集成](/cloud-app-security/siem)。</span><span class="sxs-lookup"><span data-stu-id="795fc-173">For more information, see [Generic SIEM integration](/cloud-app-security/siem).</span></span>

## <a name="configuring-logging-on-a-non-windows-system"></a><span data-ttu-id="795fc-174">在非 Windows 系统上配置日志记录</span><span class="sxs-lookup"><span data-stu-id="795fc-174">Configuring logging on a non-Windows system</span></span>

<span data-ttu-id="795fc-175">在 Windows 上，通过创建 ETW 跟踪侦听器或使用事件查看器启用分析日志记录来配置日志记录。</span><span class="sxs-lookup"><span data-stu-id="795fc-175">On Windows, logging is configured by creating ETW trace listeners or by using the Event Viewer to enable Analytic logging.</span></span> <span data-ttu-id="795fc-176">在 Linux 和 macOS 上，使用文件配置日志记录 `powershell.config.json` 。</span><span class="sxs-lookup"><span data-stu-id="795fc-176">On Linux and macOS, logging is configured using the file `powershell.config.json`.</span></span> <span data-ttu-id="795fc-177">本部分的其余部分将讨论如何在非 Windows 系统上配置 PowerShell 日志记录。</span><span class="sxs-lookup"><span data-stu-id="795fc-177">The rest of this section will discuss configuring PowerShell logging on a non-Windows system.</span></span>

<span data-ttu-id="795fc-178">默认情况下，PowerShell 启用到操作通道的信息日志记录。</span><span class="sxs-lookup"><span data-stu-id="795fc-178">By default, PowerShell enables informational logging to the operational channel.</span></span> <span data-ttu-id="795fc-179">这意味着 PowerShell 生成的任何日志输出都标记为操作，并且将记录一个大于信息性的日志 (跟踪) 级别。</span><span class="sxs-lookup"><span data-stu-id="795fc-179">What this means is any log output produced by PowerShell that is marked as operational and has a log (trace) level greater than informational will be logged.</span></span> <span data-ttu-id="795fc-180">有时，诊断可能需要额外的日志输出，例如详细日志输出或启用分析日志输出。</span><span class="sxs-lookup"><span data-stu-id="795fc-180">Occasionally, diagnoses may require additional log output, such as verbose log output or enabling analytic log output.</span></span>

<span data-ttu-id="795fc-181">文件 `powershell.config.json` 是驻留在 PowerShell 目录中的 **JSON** 格式的文件 `$PSHOME` 。</span><span class="sxs-lookup"><span data-stu-id="795fc-181">The file `powershell.config.json` is a **JSON** formatted file residing in the PowerShell `$PSHOME` directory.</span></span> <span data-ttu-id="795fc-182">每个 PowerShell 安装都使用其自己的此文件的副本。</span><span class="sxs-lookup"><span data-stu-id="795fc-182">Each installation of PowerShell uses its own copy of this file.</span></span> <span data-ttu-id="795fc-183">对于正常操作，此文件保持不变。</span><span class="sxs-lookup"><span data-stu-id="795fc-183">For normal operation, this file is left unchanged.</span></span> <span data-ttu-id="795fc-184">尽管它可能很有用，但要更改文件中的某些设置，以便进行诊断或区分同一系统上的多个 PowerShell 版本，甚至区分同一版本的多个副本 (参阅 `LogIdentity` 下表中的) 。</span><span class="sxs-lookup"><span data-stu-id="795fc-184">Although it can be useful, to change some of the settings in the file, for diagnosis or for distinguishing between multiple PowerShell versions on the same system or even multiple copies of the same version (See `LogIdentity` in the table below).</span></span>

<span data-ttu-id="795fc-185">下面的代码是一个示例配置：</span><span class="sxs-lookup"><span data-stu-id="795fc-185">The following code is an example configuration:</span></span>

```json
{
  "Microsoft.PowerShell:ExecutionPolicy": "RemoteSigned",
  "PowerShellPolicies": {
    "ScriptExecution": {
      "ExecutionPolicy": "RemoteSigned",
      "EnableScripts": true
    },
    "ScriptBlockLogging": {
      "EnableScriptBlockInvocationLogging": true,
      "EnableScriptBlockLogging": true
    },
    "ModuleLogging": {
      "EnableModuleLogging": false,
      "ModuleNames": [
        "PSReadline",
        "PowerShellGet"
      ]
    },
    "ProtectedEventLogging": {
      "EnableProtectedEventLogging": false,
      "EncryptionCertificate": [
        "Joe"
      ]
    },
    "Transcription": {
      "EnableTranscripting": true,
      "EnableInvocationHeader": true,
      "OutputDirectory": "F:\\tmp\\new"
    },
    "UpdatableHelp": {
      "DefaultSourcePath": "f:\\temp"
    },
    "ConsoleSessionConfiguration": {
      "EnableConsoleSessionConfiguration": false,
      "ConsoleSessionConfigurationName": "name"
    }
  },
  "LogLevel": "verbose"
}
```

<span data-ttu-id="795fc-186">下表列出了用于配置 PowerShell 日志记录的属性。</span><span class="sxs-lookup"><span data-stu-id="795fc-186">The properties for configuring PowerShell logging are listed in the following table.</span></span> <span data-ttu-id="795fc-187">用星号标记的值（如 `Operational*` ）在文件中未提供任何值时指示默认值。</span><span class="sxs-lookup"><span data-stu-id="795fc-187">Values marked with an asterisk, such as `Operational*`, indicate the default value when no value is provided in the file.</span></span>

|<span data-ttu-id="795fc-188">属性</span><span class="sxs-lookup"><span data-stu-id="795fc-188">Property</span></span>   |<span data-ttu-id="795fc-189">值</span><span class="sxs-lookup"><span data-stu-id="795fc-189">Values</span></span>        |<span data-ttu-id="795fc-190">说明</span><span class="sxs-lookup"><span data-stu-id="795fc-190">Description</span></span>                                  |
|-----------|--------------|---------------------------------------------|
|`LogIdentity`|<span data-ttu-id="795fc-191"> (字符串名称) </span><span class="sxs-lookup"><span data-stu-id="795fc-191">(string name)</span></span> |<span data-ttu-id="795fc-192">要在日志记录时使用的名称。</span><span class="sxs-lookup"><span data-stu-id="795fc-192">The name to use when logging.</span></span> <span data-ttu-id="795fc-193">默认情况下，</span><span class="sxs-lookup"><span data-stu-id="795fc-193">By default,</span></span>  |
|           |<span data-ttu-id="795fc-194">powershell</span><span class="sxs-lookup"><span data-stu-id="795fc-194">powershell\*</span></span>   |<span data-ttu-id="795fc-195">powershell 是标识。</span><span class="sxs-lookup"><span data-stu-id="795fc-195">powershell is the identity.</span></span> <span data-ttu-id="795fc-196">此值可以是</span><span class="sxs-lookup"><span data-stu-id="795fc-196">This value can be</span></span>|
|           |              |<span data-ttu-id="795fc-197">用于说明两个</span><span class="sxs-lookup"><span data-stu-id="795fc-197">used to tell the difference between two</span></span>      |
|           |              |<span data-ttu-id="795fc-198">PowerShell 安装的实例，例如</span><span class="sxs-lookup"><span data-stu-id="795fc-198">instances of a PowerShell installation, such</span></span> |
|           |              |<span data-ttu-id="795fc-199">作为发布和 beta 版本。</span><span class="sxs-lookup"><span data-stu-id="795fc-199">as a release and beta version.</span></span> <span data-ttu-id="795fc-200">此值为</span><span class="sxs-lookup"><span data-stu-id="795fc-200">This value is</span></span> |
|           |              |<span data-ttu-id="795fc-201">还用于将日志输出重定向到</span><span class="sxs-lookup"><span data-stu-id="795fc-201">also used to redirect log output to a</span></span>        |
|           |              |<span data-ttu-id="795fc-202">Linux 上的单独文件。</span><span class="sxs-lookup"><span data-stu-id="795fc-202">separate file on Linux.</span></span> <span data-ttu-id="795fc-203">请参阅</span><span class="sxs-lookup"><span data-stu-id="795fc-203">See the discussion of</span></span>|
|           |              |<span data-ttu-id="795fc-204">**rsyslog** 。</span><span class="sxs-lookup"><span data-stu-id="795fc-204">**rsyslog** above.</span></span>                           |
|`LogChannels`|<span data-ttu-id="795fc-205">营业</span><span class="sxs-lookup"><span data-stu-id="795fc-205">Operational\*</span></span>  |<span data-ttu-id="795fc-206">要启用的通道。</span><span class="sxs-lookup"><span data-stu-id="795fc-206">The channels to enable.</span></span> <span data-ttu-id="795fc-207">分隔值</span><span class="sxs-lookup"><span data-stu-id="795fc-207">Separate the values</span></span>|
|           |<span data-ttu-id="795fc-208">分析</span><span class="sxs-lookup"><span data-stu-id="795fc-208">Analytic</span></span>      |<span data-ttu-id="795fc-209">指定多个时使用逗号。</span><span class="sxs-lookup"><span data-stu-id="795fc-209">with a comma when specifying more than one.</span></span>  |
|`LogLevel`   |<span data-ttu-id="795fc-210">始终</span><span class="sxs-lookup"><span data-stu-id="795fc-210">Always</span></span>        |<span data-ttu-id="795fc-211">指定单个值。</span><span class="sxs-lookup"><span data-stu-id="795fc-211">Specify a single value.</span></span> <span data-ttu-id="795fc-212">该值启用</span><span class="sxs-lookup"><span data-stu-id="795fc-212">The value enables</span></span>  |
|           |<span data-ttu-id="795fc-213">严重</span><span class="sxs-lookup"><span data-stu-id="795fc-213">Critical</span></span>      |<span data-ttu-id="795fc-214">本身以及它上面的所有值</span><span class="sxs-lookup"><span data-stu-id="795fc-214">itself and all values above it in the</span></span>        |
|           |<span data-ttu-id="795fc-215">错误</span><span class="sxs-lookup"><span data-stu-id="795fc-215">Error</span></span>         |<span data-ttu-id="795fc-216">向左列出。</span><span class="sxs-lookup"><span data-stu-id="795fc-216">list to the left.</span></span>                            |
|           |<span data-ttu-id="795fc-217">警告</span><span class="sxs-lookup"><span data-stu-id="795fc-217">Warning</span></span>       |                                             |
|           |<span data-ttu-id="795fc-218">条</span><span class="sxs-lookup"><span data-stu-id="795fc-218">Informational\*</span></span>|                                             |
|           |<span data-ttu-id="795fc-219">“详细”</span><span class="sxs-lookup"><span data-stu-id="795fc-219">Verbose</span></span>       |                                             |
|           |<span data-ttu-id="795fc-220">调试</span><span class="sxs-lookup"><span data-stu-id="795fc-220">Debug</span></span>         |                                             |
|`LogKeywords`|<span data-ttu-id="795fc-221">Runspace</span><span class="sxs-lookup"><span data-stu-id="795fc-221">Runspace</span></span>      |<span data-ttu-id="795fc-222">关键字提供限制日志记录的功能</span><span class="sxs-lookup"><span data-stu-id="795fc-222">Keywords provide the ability to limit logging</span></span>|
|           |<span data-ttu-id="795fc-223">管道</span><span class="sxs-lookup"><span data-stu-id="795fc-223">Pipeline</span></span>      |<span data-ttu-id="795fc-224">PowerShell 中的特定组件。</span><span class="sxs-lookup"><span data-stu-id="795fc-224">to specific components within PowerShell.</span></span> <span data-ttu-id="795fc-225">通过</span><span class="sxs-lookup"><span data-stu-id="795fc-225">By</span></span> |
|           |<span data-ttu-id="795fc-226">协议</span><span class="sxs-lookup"><span data-stu-id="795fc-226">Protocol</span></span>      |<span data-ttu-id="795fc-227">默认情况下，将启用并更改所有关键字</span><span class="sxs-lookup"><span data-stu-id="795fc-227">default, all keywords are enabled and change</span></span> |
|           |<span data-ttu-id="795fc-228">Transport</span><span class="sxs-lookup"><span data-stu-id="795fc-228">Transport</span></span>     |<span data-ttu-id="795fc-229">此值仅适用于</span><span class="sxs-lookup"><span data-stu-id="795fc-229">this value is only useful for very</span></span>           |
|           |<span data-ttu-id="795fc-230">主机</span><span class="sxs-lookup"><span data-stu-id="795fc-230">Host</span></span>          |<span data-ttu-id="795fc-231">专用故障排除。</span><span class="sxs-lookup"><span data-stu-id="795fc-231">specialized troubleshooting.</span></span>                |
|           |<span data-ttu-id="795fc-232">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="795fc-232">Cmdlets</span></span>       |                                             |
|           |<span data-ttu-id="795fc-233">序列化程序</span><span class="sxs-lookup"><span data-stu-id="795fc-233">Serializer</span></span>    |                                             |
|           |<span data-ttu-id="795fc-234">会话</span><span class="sxs-lookup"><span data-stu-id="795fc-234">Session</span></span>       |                                             |
|           |<span data-ttu-id="795fc-235">ManagedPlugin</span><span class="sxs-lookup"><span data-stu-id="795fc-235">ManagedPlugin</span></span> |                                             |

## <a name="see-also"></a><span data-ttu-id="795fc-236">另请参阅</span><span class="sxs-lookup"><span data-stu-id="795fc-236">See also</span></span>

<span data-ttu-id="795fc-237">有关 Linux **syslog** 和 **rsyslog** 信息，请参阅 linux 计算机的本地 `man` 页面。</span><span class="sxs-lookup"><span data-stu-id="795fc-237">For Linux **syslog** and **rsyslog.conf** information, refer to the Linux computer's local `man` pages.</span></span>

<span data-ttu-id="795fc-238">有关 macOS **os_log** 信息，请参阅 [os_log 开发人员文档](https://developer.apple.com/documentation/os/os_log)。</span><span class="sxs-lookup"><span data-stu-id="795fc-238">For macOS **os_log** information, see [os_log developer documentation](https://developer.apple.com/documentation/os/os_log).</span></span>

[<span data-ttu-id="795fc-239">about_Logging_Windows</span><span class="sxs-lookup"><span data-stu-id="795fc-239">about_Logging_Windows</span></span>](about_Logging_Windows.md)

[<span data-ttu-id="795fc-240">通用 SIEM 集成</span><span class="sxs-lookup"><span data-stu-id="795fc-240">Generic SIEM integration</span></span>](/cloud-app-security/siem)

<!-- link references -->
<span data-ttu-id="795fc-241">SIEM</span><span class="sxs-lookup"><span data-stu-id="795fc-241">[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management</span></span>
