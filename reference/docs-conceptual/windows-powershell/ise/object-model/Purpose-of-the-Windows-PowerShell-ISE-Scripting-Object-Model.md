---
ms.date: 12/31/2019
title: Windows PowerShell ISE 脚本对象模型的用途
description: Windows PowerShell ISE 脚本对象模型的用途
ms.openlocfilehash: 60bb15184eb5e7ff819f7c968dda7477d2b627d4
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667141"
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a>Windows PowerShell ISE 脚本对象模型的用途

对象与 Windows PowerShell 集成脚本环境 (ISE) 的窗体和函数相关。 对象模型参考提供有关这些对象公开的成员属性和方法的详细信息。 提供了示例来演示如何使用脚本直接访问这些方法和属性。 脚本对象模型使得可以轻松完成下列任务。

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a>自定义 Windows PowerShell ISE 的外观

对象模型可用于修改应用程序设置和选项。 例如，可以如下所示修改它们：

- 更改错误、警告、详细输出和调试输出的颜色。
- 获取或设置“命令”窗格、“输出”窗格以及“脚本”窗格的背景色。
- 设置“输出”窗格的前景色。
- 设置 Windows PowerShell ISE 的字体名称和字体大小。
- 配置警告。 此设置包含在多个 PowerShell 选项卡中打开一个文件或者在保存文件之前运行该文件中的脚本时将发出的警告。
- 在“脚本”窗格和“输出”窗格并排显示的视图与“脚本”窗格位于“输出”窗格之上的视图之间进行切换。
- 将“命令”窗格停靠在“输出”窗格的底部或之上。

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a>增强 Windows PowerShell ISE 的功能

对象模型可用于增强 Windows PowerShell ISE 的功能。 例如，你能够：

- 添加和修改 Windows PowerShell ISE 本身的实例。 例如，若要更改菜单，可以添加新菜单项并将新菜单项映射到脚本。
- 创建执行可以通过使用 Windows PowerShell ISE 中的菜单命令和按钮执行的一些任务的脚本。 例如，你可以添加、删除或选择一个 PowerShell 选项卡。
- 可以通过使用菜单命令和按钮执行的补充任务。 例如，你可以重命名 PowerShell 选项卡。
- 操作“命令”窗格、“输出”窗格以及“脚本”窗格与文件相关联的文本缓冲区。 例如，你能够：
  - 获取或设置所有文本。
  - 获取或设置文本选择。
  - 运行脚本或运行脚本的选定部分。
  - 将某行滚动到视图中。
  - 在脱字号位置插入文本。
  - 选择文本块。
  - 获取最后一个行号。
- 执行文件操作。 例如，你能够：
  - 打开文件、保存文件或使用其他名称保存文件。
  - 确定文件自上次保存后是否已更改。
  - 获取文件名。
  - 选择一个文件。

## <a name="automating-tasks"></a>自动执行任务

脚本对象模型可用于创建频繁执行的操作的键盘快捷方式。

## <a name="see-also"></a>另请参阅

- [ISE 对象模型层次结构](The-ISE-Object-Model-Hierarchy.md)
