---
ms.date: 06/05/2017
title: PowerShellTabCollection 对象
description: PowerShellTab 集合对象是 PowerShellTab 对象的集合。 每个 PowerShellTab 对象充当一个单独的运行时环境。
ms.openlocfilehash: 60f8001f096b50bd8433a5685f1f70a350f07f61
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658271"
---
# <a name="the-powershelltabcollection-object"></a>PowerShellTabCollection 对象

**PowerShellTab** 集合对象是 **PowerShellTab** 对象的集合。 每个 **PowerShellTab** 对象充当一个单独的运行时环境。 它是 Microsoft.PowerShell.Host.ISE.PowerShellTabs 类的实例。 `$psISE.PowerShellTabs` 对象就是一个示例。

## <a name="methods"></a>方法

### <a name="add"></a>添加\(\)

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

向集合中添加一个新的 PowerShell 选项卡。 它将返回新添加的选项卡。

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

删除由 **psTab** 参数指定的选项卡。

**psTab** 要删除的 PowerShell 选项卡。

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

选择由 **psTab** 参数指定的 PowerShell 选项卡，以使它当前是处于活动状态的 PowerShell 选项卡。

**psTab** 要选择的 PowerShell 选项卡。

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a>另请参阅

- [PowerShellTab 对象](The-PowerShellTab-Object.md)
- [Windows PowerShell ISE 脚本对象模型的用途](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 对象模型层次结构](The-ISE-Object-Model-Hierarchy.md)
