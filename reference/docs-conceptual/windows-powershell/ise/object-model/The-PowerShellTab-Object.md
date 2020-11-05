---
ms.date: 06/05/2017
title: PowerShellTab 对象
description: PowerShellTab 对象代表 Windows PowerShell 运行时环境。
ms.openlocfilehash: ac89875e408a41a92d7e3d1a83a849466296c3c6
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663397"
---
# <a name="the-powershelltab-object"></a><span data-ttu-id="f4583-103">PowerShellTab 对象</span><span class="sxs-lookup"><span data-stu-id="f4583-103">The PowerShellTab Object</span></span>

<span data-ttu-id="f4583-104">**PowerShellTab** 对象代表 Windows PowerShell 运行时环境。</span><span class="sxs-lookup"><span data-stu-id="f4583-104">The **PowerShellTab** object represents a Windows PowerShell runtime environment.</span></span>

## <a name="methods"></a><span data-ttu-id="f4583-105">方法</span><span class="sxs-lookup"><span data-stu-id="f4583-105">Methods</span></span>

### <a name="invoke-script-"></a><span data-ttu-id="f4583-106">调用\(脚本\)</span><span class="sxs-lookup"><span data-stu-id="f4583-106">Invoke\( Script \)</span></span>

<span data-ttu-id="f4583-107">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="f4583-107">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f4583-108">在 PowerShell 选项卡中运行给定的脚本。</span><span class="sxs-lookup"><span data-stu-id="f4583-108">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="f4583-109">此方法仅适用于其他 PowerShell 选项卡，不适用于运行它的 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f4583-109">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="f4583-110">它不返回任何对象或值。</span><span class="sxs-lookup"><span data-stu-id="f4583-110">It does not return any object or value.</span></span> <span data-ttu-id="f4583-111">如果代码修改任何变量，则这些更改将仍保存在根据其调用该命令的选项卡上。</span><span class="sxs-lookup"><span data-stu-id="f4583-111">If the code modifies any variable, then those changes persist on the tab against which the command was invoked.</span></span>

<span data-ttu-id="f4583-112">**Script** - 要运行的脚本块的 System.Management.Automation.ScriptBlock 或字符串。</span><span class="sxs-lookup"><span data-stu-id="f4583-112">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a><span data-ttu-id="f4583-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span><span class="sxs-lookup"><span data-stu-id="f4583-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span></span>

<span data-ttu-id="f4583-114">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="f4583-114">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f4583-115">在 PowerShell 选项卡中运行给定的脚本。</span><span class="sxs-lookup"><span data-stu-id="f4583-115">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="f4583-116">此方法仅适用于其他 PowerShell 选项卡，不适用于运行它的 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f4583-116">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="f4583-117">运行脚本块，并且从该脚本返回的任何值将返回到从中调用该命令的运行环境。</span><span class="sxs-lookup"><span data-stu-id="f4583-117">The script block is run and any value that is returned from the script is returned to the run environment from which you invoked the command.</span></span> <span data-ttu-id="f4583-118">如果命令运行所花费的时间大于指定的 millesecondsTimeout  值，则该命令将失败并出现异常：“操作已超时。”</span><span class="sxs-lookup"><span data-stu-id="f4583-118">If the command takes longer to run than the **millesecondsTimeout** value specifies, then the command fails with an exception: "The operation has timed out."</span></span>

<span data-ttu-id="f4583-119">**Script** - 要运行的脚本块的 System.Management.Automation.ScriptBlock 或字符串。</span><span class="sxs-lookup"><span data-stu-id="f4583-119">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

<span data-ttu-id="f4583-120">**\[useNewScope\]** -  可选的布尔值，默认值为 `$true`，如果设置为 `$true`，则会新建作用域以在其中运行命令。</span><span class="sxs-lookup"><span data-stu-id="f4583-120">**\[useNewScope\]** -  Optional Boolean that defaults to `$true` If set to `$true`, then a new scope is created within which to run the command.</span></span> <span data-ttu-id="f4583-121">它不会修改该命令指定的 PowerShell 选项卡的运行时环境。</span><span class="sxs-lookup"><span data-stu-id="f4583-121">It does not modify the runtime environment of the PowerShell tab that is specified by the command.</span></span>

<span data-ttu-id="f4583-122">**\[millisecondsTimeout\]** - 可选整数，默认值为 **500** 。</span><span class="sxs-lookup"><span data-stu-id="f4583-122">**\[millisecondsTimeout\]** -  Optional integer that defaults to **500**.</span></span>
<span data-ttu-id="f4583-123">如果在指定时间内未完成命令，则该命令将生成 **TimeoutException** 并显示消息“操作已超时。”</span><span class="sxs-lookup"><span data-stu-id="f4583-123">If the command does not finish within the specified time, then the command generates a **TimeoutException** with the message "The operation has timed out."</span></span>

```powershell
# Create a new PowerShell tab and then switch back to the first
$psISE.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0])

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1', $false)
# You can switch to the other tab and type '$x' to see that the value is saved there.

# This example sets a value in the other tab (in a different scope)
# and returns it through the pipeline to this tab to store in $a
$a = $psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z')
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
Measure-Command {$psISE.PowerShellTabs[1].InvokeSynchronous('sleep 10', $false, 5000)}
```

## <a name="properties"></a><span data-ttu-id="f4583-124">属性</span><span class="sxs-lookup"><span data-stu-id="f4583-124">Properties</span></span>

### <a name="addonsmenu"></a><span data-ttu-id="f4583-125">AddOnsMenu</span><span class="sxs-lookup"><span data-stu-id="f4583-125">AddOnsMenu</span></span>

<span data-ttu-id="f4583-126">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="f4583-126">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f4583-127">只读属性，可获取 PowerShell 选项卡的“加载项”菜单。</span><span class="sxs-lookup"><span data-stu-id="f4583-127">The read-only property that gets the Add-ons menu for the PowerShell tab.</span></span>

```powershell
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

### <a name="caninvoke"></a><span data-ttu-id="f4583-128">CanInvoke</span><span class="sxs-lookup"><span data-stu-id="f4583-128">CanInvoke</span></span>

<span data-ttu-id="f4583-129">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="f4583-129">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f4583-130">只读布尔属性，如果可以使用 [Invoke( Script )](#invoke-script-) 方法调用脚本，则返回 `$true` 值。</span><span class="sxs-lookup"><span data-stu-id="f4583-130">The read-only Boolean property that returns a `$true` value if a script can be invoked with the [Invoke( Script )](#invoke-script-) method.</span></span>

```powershell
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab.
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psISE.PowerShellTabs[1]
$secondTab.CanInvoke
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke
```

### <a name="consolepane"></a><span data-ttu-id="f4583-131">ConsolePane</span><span class="sxs-lookup"><span data-stu-id="f4583-131">ConsolePane</span></span>

<span data-ttu-id="f4583-132">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="f4583-132">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> <span data-ttu-id="f4583-133">在 Windows PowerShell ISE 2.0 中，这命名为 **CommandPane** 。</span><span class="sxs-lookup"><span data-stu-id="f4583-133">In Windows PowerShell ISE 2.0 this was named **CommandPane**.</span></span>

<span data-ttu-id="f4583-134">获取“控制台”窗格 [editor](The-ISEEditor-Object.md) 对象的只读属性。</span><span class="sxs-lookup"><span data-stu-id="f4583-134">The read-only property that gets the Console pane [editor](The-ISEEditor-Object.md) object.</span></span>

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a><span data-ttu-id="f4583-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="f4583-135">DisplayName</span></span>

<span data-ttu-id="f4583-136">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="f4583-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f4583-137">读写属性，可获取或设置 PowerShell 选项卡上显示的文本。默认情况下，选项卡命名为“PowerShell #”，其中 # 表示数字。</span><span class="sxs-lookup"><span data-stu-id="f4583-137">The read-write property that gets or sets the text that is displayed on the PowerShell tab. By default, tabs are named "PowerShell #", where the # represents a number.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a><span data-ttu-id="f4583-138">ExpandedScript</span><span class="sxs-lookup"><span data-stu-id="f4583-138">ExpandedScript</span></span>

<span data-ttu-id="f4583-139">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="f4583-139">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f4583-140">读写布尔属性，可确定“脚本”窗格是展开还是隐藏的。</span><span class="sxs-lookup"><span data-stu-id="f4583-140">The read-write Boolean property that determines whether the Script pane is expanded or hidden.</span></span>

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a><span data-ttu-id="f4583-141">文件</span><span class="sxs-lookup"><span data-stu-id="f4583-141">Files</span></span>

<span data-ttu-id="f4583-142">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="f4583-142">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f4583-143">只读属性，可获取 PowerShell 选项卡中打开的[脚本文件集合](The-ISEFileCollection-Object.md)。</span><span class="sxs-lookup"><span data-stu-id="f4583-143">The read-only property that gets the [collection of script files](The-ISEFileCollection-Object.md) that are open in the PowerShell tab.</span></span>

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a><span data-ttu-id="f4583-144">输出</span><span class="sxs-lookup"><span data-stu-id="f4583-144">Output</span></span>

<span data-ttu-id="f4583-145">此功能存在于 Windows PowerShell ISE 2.0 中，但已在更高版本的 ISE 中删除或重命名。</span><span class="sxs-lookup"><span data-stu-id="f4583-145">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="f4583-146">在更高版本的 Windows PowerShell ISE 中，你可以将 **ConsolePane** 对象用于相同的目的。</span><span class="sxs-lookup"><span data-stu-id="f4583-146">In later versions of Windows PowerShell ISE, you can use the **ConsolePane** object for the same purposes.</span></span>

<span data-ttu-id="f4583-147">只读属性，可获取当前[编辑器](The-ISEEditor-Object.md)的“输出”窗格。</span><span class="sxs-lookup"><span data-stu-id="f4583-147">The read-only property that gets the Output pane of the current [editor](The-ISEEditor-Object.md).</span></span>

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a><span data-ttu-id="f4583-148">Prompt</span><span class="sxs-lookup"><span data-stu-id="f4583-148">Prompt</span></span>

<span data-ttu-id="f4583-149">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="f4583-149">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f4583-150">只读属性，可获取当前提示文本。</span><span class="sxs-lookup"><span data-stu-id="f4583-150">The read-only property that gets the current prompt text.</span></span> <span data-ttu-id="f4583-151">注意：Prompt 函数可以被用户&trade;的配置文件覆盖。</span><span class="sxs-lookup"><span data-stu-id="f4583-151">Note: the **Prompt** function can be overridden by the user'&trade;s profile.</span></span> <span data-ttu-id="f4583-152">如果结果不止一个简单的字符串，则此属性不会返回任何内容。</span><span class="sxs-lookup"><span data-stu-id="f4583-152">If the result is other than a simple string, then this property returns nothing.</span></span>

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a><span data-ttu-id="f4583-153">ShowCommands</span><span class="sxs-lookup"><span data-stu-id="f4583-153">ShowCommands</span></span>

<span data-ttu-id="f4583-154">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="f4583-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f4583-155">读写属性，指示当前是否显示“命令”窗格。</span><span class="sxs-lookup"><span data-stu-id="f4583-155">The read-write property that indicates if the Commands pane is currently displayed.</span></span>

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a><span data-ttu-id="f4583-156">StatusText</span><span class="sxs-lookup"><span data-stu-id="f4583-156">StatusText</span></span>

<span data-ttu-id="f4583-157">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="f4583-157">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f4583-158">只读属性，可获取 **PowerShellTab** 状态文本。</span><span class="sxs-lookup"><span data-stu-id="f4583-158">The read-only property that gets the **PowerShellTab** status text.</span></span>

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a><span data-ttu-id="f4583-159">HorizontalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="f4583-159">HorizontalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="f4583-160">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="f4583-160">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f4583-161">只读属性，指示水平“加载项”工具窗格当前是否打开。</span><span class="sxs-lookup"><span data-stu-id="f4583-161">The read-only property that indicates whether the horizontal Add-Ons tool pane is currently open.</span></span>

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a><span data-ttu-id="f4583-162">VerticalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="f4583-162">VerticalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="f4583-163">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="f4583-163">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f4583-164">只读属性，指示竖直“加载项”工具窗格当前是否打开。</span><span class="sxs-lookup"><span data-stu-id="f4583-164">The read-only property that indicates whether the vertical Add-Ons tool pane is currently open.</span></span>

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a><span data-ttu-id="f4583-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f4583-165">See Also</span></span>

- [<span data-ttu-id="f4583-166">PowerShellTabCollection 对象</span><span class="sxs-lookup"><span data-stu-id="f4583-166">The PowerShellTabCollection Object</span></span>](The-PowerShellTabCollection-Object.md)
- [<span data-ttu-id="f4583-167">Windows PowerShell ISE 脚本对象模型的用途</span><span class="sxs-lookup"><span data-stu-id="f4583-167">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="f4583-168">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="f4583-168">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
