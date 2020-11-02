---
ms.date: 06/12/2017
title: WMF 5.0 中的已知问题
description: WMF 5.0 中的已知问题
ms.openlocfilehash: 3f8dcf0f7aab27ff9d3c3a17377959988844a430
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663379"
---
# <a name="known-issues-in-wmf-50"></a><span data-ttu-id="081fb-103">WMF 5.0 中的已知问题</span><span class="sxs-lookup"><span data-stu-id="081fb-103">Known Issues in WMF 5.0</span></span>

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="081fb-104">PowerShell 快捷方式在第一次使用时中断</span><span class="sxs-lookup"><span data-stu-id="081fb-104">PowerShell Shortcuts are broken when used for the first time</span></span>

<span data-ttu-id="081fb-105">**解决方法：** 执行下列其中一项操作：</span><span class="sxs-lookup"><span data-stu-id="081fb-105">**Resolution:** Perform one of the following actions:</span></span>

1. <span data-ttu-id="081fb-106">右键单击 PowerShell 快捷方式。</span><span class="sxs-lookup"><span data-stu-id="081fb-106">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="081fb-107">选择“Windows PowerShell”以在非提升模式下启动。</span><span class="sxs-lookup"><span data-stu-id="081fb-107">Select "Windows PowerShell" to launch in a non-elevated mode.</span></span>
2. <span data-ttu-id="081fb-108">右键单击 PowerShell 快捷方式。</span><span class="sxs-lookup"><span data-stu-id="081fb-108">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="081fb-109">右键单击“Windows PowerShell”并选择“以管理员身份运行”，以在提升模式下启动。</span><span class="sxs-lookup"><span data-stu-id="081fb-109">Right click on "Windows PowerShell" and select "Run As Administrator" to launch in an elevated mode.</span></span>

<span data-ttu-id="081fb-110">执行以上任一操作后，即可使用 PowerShell 快捷方式。</span><span class="sxs-lookup"><span data-stu-id="081fb-110">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="081fb-111">这些操作仅需要执行一次。</span><span class="sxs-lookup"><span data-stu-id="081fb-111">These actions need to be performed only once.</span></span>

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="081fb-112">在运行 Windows 7 操作系统的计算机上，PowerShell 模块和 DSC 资源报告有关 ExecutionPolicy 的错误</span><span class="sxs-lookup"><span data-stu-id="081fb-112">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>

<span data-ttu-id="081fb-113">在运行 Windows 7 操作系统的计算机上，使用 PowerShell 模块和 DSC 资源可能导致报告有关 ExecutionPolicy 的错误。</span><span class="sxs-lookup"><span data-stu-id="081fb-113">On Windows 7, using PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="081fb-114">**解决方法：** 通过在提升的 PowerShell 会话中运行以下命令（以管理员身份运行），将 ExecutionPolicy 设置为 RemoteSigned  ：</span><span class="sxs-lookup"><span data-stu-id="081fb-114">**Resolution:** Set the ExecutionPolicy to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="081fb-115">连接到旧的远程 Exchange 终结点引发故障</span><span class="sxs-lookup"><span data-stu-id="081fb-115">Connecting to an old remote Exchange endpoint causes a crash</span></span>

<span data-ttu-id="081fb-116">旧的 Exchange 终结点重定向到新的终结点。</span><span class="sxs-lookup"><span data-stu-id="081fb-116">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="081fb-117">引发故障的重定向逻辑中存在 Bug。</span><span class="sxs-lookup"><span data-stu-id="081fb-117">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="081fb-118">**解决方法：** 直接连接到新终结点。</span><span class="sxs-lookup"><span data-stu-id="081fb-118">**Resolution:** Connect directly to the new endpoint.</span></span>

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="081fb-119">在 Windows Server 2012 R2 上安装 WMF 5.0 后，错误地停止软件清单日志记录功能</span><span class="sxs-lookup"><span data-stu-id="081fb-119">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>

<span data-ttu-id="081fb-120">当在已运行 SIL 的 Windows Server 2012 R2 上安装 WMF 5.0 时，安装完成后错误地停止软件清单日志记录功能。</span><span class="sxs-lookup"><span data-stu-id="081fb-120">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="081fb-121">**解决方法：** 在 WMF 安装后立即运行 `Start-SilLogging` cmdlet，因为安装过程将错误地停止软件清单日志记录功能。</span><span class="sxs-lookup"><span data-stu-id="081fb-121">**Resolution:** Run the `Start-SilLogging` cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="081fb-122">如果将 -LiteralPath 和 -Recurse 一起使用，`Get-ChildItem` 将失效</span><span class="sxs-lookup"><span data-stu-id="081fb-122">`Get-ChildItem` does not work if -LiteralPath and -Recurse are used together</span></span>

<span data-ttu-id="081fb-123">如果目录名称包含无效的通配符，则将 -LiteralPath 和 -Recurse 一起使用时，`Get-ChildItem` 不会产生预期结果。</span><span class="sxs-lookup"><span data-stu-id="081fb-123">If a directory name contains an invalid wildcard character, then `Get-ChildItem` will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="081fb-124">**解决方法：** 尽管不理想，但当前的解决方法是在脚本中实现递归，而不是依赖 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="081fb-124">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>

## <a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="081fb-125">Sysprep 在安装 WMF 5.0 后无法正常工作</span><span class="sxs-lookup"><span data-stu-id="081fb-125">Sysprep fails after WMF 5.0 installation</span></span>

<span data-ttu-id="081fb-126">该问题有两种解决方法，具体取决于正在运行的 Windows Server 版本。</span><span class="sxs-lookup"><span data-stu-id="081fb-126">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="081fb-127">**解决方法：**</span><span class="sxs-lookup"><span data-stu-id="081fb-127">**Resolution:**</span></span>

- <span data-ttu-id="081fb-128">对于运行 **Windows Server 2008 R2** 的系统</span><span class="sxs-lookup"><span data-stu-id="081fb-128">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="081fb-129">以管理员身份打开 PowerShell</span><span class="sxs-lookup"><span data-stu-id="081fb-129">Open PowerShell as an administrator</span></span>
  2. <span data-ttu-id="081fb-130">运行以下命令</span><span class="sxs-lookup"><span data-stu-id="081fb-130">Run the following command</span></span>

     ```powershell
     Set-SilLogging -TargetUri https://BlankTarget -CertificateThumbprint 0123456789
     ```

  3. <span data-ttu-id="081fb-131">按预期运行命令并忽略错误。</span><span class="sxs-lookup"><span data-stu-id="081fb-131">Run the command and ignore the error, as they are expected.</span></span>

     ```powershell
     Publish-SilData
     ```

  4. <span data-ttu-id="081fb-132">删除 \Windows\System32\Logfiles\SIL\ 目录中的文件</span><span class="sxs-lookup"><span data-stu-id="081fb-132">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. <span data-ttu-id="081fb-133">安装所有可用的重要 Windows 更新，并正常开始 Sysyprep 操作。</span><span class="sxs-lookup"><span data-stu-id="081fb-133">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>

- <span data-ttu-id="081fb-134">对于运行 **Windows Server 2012** 的系统</span><span class="sxs-lookup"><span data-stu-id="081fb-134">For systems running **Windows Server 2012**</span></span>
  1. <span data-ttu-id="081fb-135">在要执行 Sysprep 的服务器上安装 WMF 5.0 后，以管理员身份登录。</span><span class="sxs-lookup"><span data-stu-id="081fb-135">After installing WMF 5.0 on the server to be Sysprep'd, login as administrator.</span></span>
  2. <span data-ttu-id="081fb-136">将 Generize.xml 从目录 `\Windows\System32\Sysprep\ActionFiles\` 复制到 Windows 目录（比如 `C:\`）之外的位置。</span><span class="sxs-lookup"><span data-stu-id="081fb-136">Copy Generize.xml from directory `\Windows\System32\Sysprep\ActionFiles\` to a location outside of the Windows directory, `C:\` for example.</span></span>
  3. <span data-ttu-id="081fb-137">使用记事本打开 Generalize.xml 副本。</span><span class="sxs-lookup"><span data-stu-id="081fb-137">Open your Generalize.xml copy with notepad.</span></span>
  4. <span data-ttu-id="081fb-138">查找并删除以下文本，需要删除每个文本的一个实例（它们将位于接近文档结尾的地方）。</span><span class="sxs-lookup"><span data-stu-id="081fb-138">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. <span data-ttu-id="081fb-139">保存编辑过的 Generalize.xml 副本并关闭该文件。</span><span class="sxs-lookup"><span data-stu-id="081fb-139">Save the edited copy of Generalize.xml and close the file.</span></span>
  6. <span data-ttu-id="081fb-140">以管理员身份打开命令提示符</span><span class="sxs-lookup"><span data-stu-id="081fb-140">Open a command prompt as administrator</span></span>
  7. <span data-ttu-id="081fb-141">运行以下命令，以获得 system32 文件夹中的 Generalize.xml 文件的所有权：</span><span class="sxs-lookup"><span data-stu-id="081fb-141">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. <span data-ttu-id="081fb-142">运行以下命令以设置文件的适当权限：</span><span class="sxs-lookup"><span data-stu-id="081fb-142">Run the following command to set appropriate permission on the file:</span></span>

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - <span data-ttu-id="081fb-143">提示进行确认时回答“是”。</span><span class="sxs-lookup"><span data-stu-id="081fb-143">Answer Yes at the prompt for confirmation.</span></span>
     - <span data-ttu-id="081fb-144">请注意，`<AdministratorUserName>` 应替换为计算机管理员的用户名。</span><span class="sxs-lookup"><span data-stu-id="081fb-144">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="081fb-145">例如，“Administrator”。</span><span class="sxs-lookup"><span data-stu-id="081fb-145">For example, "Administrator".</span></span>

  9. <span data-ttu-id="081fb-146">使用以下命令将编辑并保存好的文件复制到 Sysprep 目录：</span><span class="sxs-lookup"><span data-stu-id="081fb-146">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - <span data-ttu-id="081fb-147">回答“是”进行覆盖（注意，如果没有任何覆盖提示，请再次检查输入的路径）。</span><span class="sxs-lookup"><span data-stu-id="081fb-147">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
     - <span data-ttu-id="081fb-148">假定你编辑的 Generalize.xml 副本已复制到 C:\。</span><span class="sxs-lookup"><span data-stu-id="081fb-148">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10. <span data-ttu-id="081fb-149">Generalize.xml 中现已更新解决方法。</span><span class="sxs-lookup"><span data-stu-id="081fb-149">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="081fb-150">请在启用通用选项的情况下运行 Sysprep。</span><span class="sxs-lookup"><span data-stu-id="081fb-150">Please run Sysprep with the generalize option enabled.</span></span>
