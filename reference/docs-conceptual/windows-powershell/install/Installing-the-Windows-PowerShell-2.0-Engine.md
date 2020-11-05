---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 安装 Windows PowerShell 2.0 引擎
description: Windows PowerShell 2.0 引擎是 Windows 的一项可选功能。 本文介绍了如何安装该功能和必要的要求。
ms.openlocfilehash: c82725c34f5c5864eba0c88eb33ecac9e43f86d3
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663962"
---
# <a name="installing-the-windows-powershell-20-engine"></a>安装 Windows PowerShell 2.0 引擎

本主题介绍了如何安装 Windows PowerShell 2.0 引擎。

Windows PowerShell 3.0 旨在能够与 Windows PowerShell 2.0 向后兼容。 为 Windows PowerShell 2.0 编写的 Cmdlet、提供程序、管理单元、模块以及脚本无需更改，即可在 Windows PowerShell 3.0 和 Windows PowerShell 4.0 中运行。 但是，由于 Microsoft.NET framework 4 中的运行时激活策略的更改，为 Windows PowerShell 2.0 编写并使用公共语言运行时 (CLR) 2.0 编译的 Windows PowerShell 主机程序在使用 CLR 4.0 编译的 Windows PowerShell 的更高版本中未进行修改时，将无法运行。

为了保持与受这些更改影响的命令和主机程序的向后兼容性，Windows PowerShell 2.0、Windows PowerShell 3.0 和 Windows PowerShell 4.0 引擎被设计为并排运行。 此外，Windows PowerShell 2.0 引擎也包含在 Windows Server 2012 R2、Windows 8.1、Windows 8、Windows Server 2012 和 Windows Management Framework 3.0 中。 Windows PowerShell 2.0 引擎仅在当前脚本或主机程序无法运行时使用，因为它与 Windows PowerShell 3.0、Windows PowerShell 4.0 或 Microsoft .NET Framework 4 不兼容。 这种情况很少见。

Windows PowerShell 2.0 引擎是 Windows Server 2012 R2、Windows 8.1、Windows&reg; 8 和 Windows Server&reg; 2012 的一项可选功能。 在早期版本的 Windows 中，在安装 Windows Management Framework 3.0 时，Windows PowerShell 3.0 安装将完全替代 Windows PowerShell 安装目录中的 Windows PowerShell 2.0 安装。 然而，Windows PowerShell 2.0 引擎将保留。

有关启动 Windows PowerShell 2.0 引擎的信息，请参阅[启动 Windows PowerShell 2.0 引擎](../Starting-the-Windows-PowerShell-2.0-Engine.md)。

## <a name="on-windows-81-and-windows-8"></a>在 Windows 8.1 和 Windows 8 上

在 Windows 8.1 和 Windows 8 上，默认情况下启用 Windows PowerShell 2.0 引擎功能。
但是，若要使用它，则需要打开它所要求的 Microsoft.NET Framework 3.5 的选项。 本节还介绍了如何打开和关闭 Windows PowerShell 2.0. 引擎功能。

#### <a name="to-turn-on-net-framework-35"></a>打开 .NET Framework 3.5

1. 在“开始”屏幕上，键入“Windows 功能”。
2. 在“应用”工具栏上，单击“设置”，然后单击“打开或关闭 Windows 功能”。
3. 在“Windows 功能”框中，单击“.NET Framework 3.5（包括.NET 2.0 和 3.0）”以将其选中。

   当你选择“.NET Framework 3.5（包括.NET 2.0 和 3.0）”后，将填充该框，以指示仅选中功能的一部分。 但是，这对于 Windows PowerShell 2.0 引擎已经足够。

#### <a name="to-turn-the-windows-powershell-20-engine-on-and-off"></a>打开或关闭 Windows PowerShell 2.0 引擎

1. 在“开始”屏幕上，键入“Windows 功能”。

2. 在“应用”工具栏上，单击“设置”，然后单击“打开或关闭 Windows 功能”。

3. 在“Windows 功能”框中，展开“Windows PowerShell 2.0”节点，然后单击“Windows PowerShell 2.0 引擎”框来选择或清除它。

## <a name="on-windows-server-2012-r2-and-windows-server-2012"></a>在 Windows Server 2012 R2 和 Windows Server 2012 上

使用以下过程来添加 Windows PowerShell 2.0 引擎和 Microsoft .NET Framework 3.5 功能。 Windows PowerShell 2.0 引擎至少需要 Microsoft .NET Framework 2.0.50727。 Microsoft .NET Framework 3.5 满足此要求。

#### <a name="to-add-the-net-framework-35-feature"></a>添加 .NET Framework 3.5 功能

1. 在“服务器管理器”中，从“管理”菜单上，选择“添加角色和功能”。

    或者在“服务器管理器”中，单击“所有服务器”，右键单击某个服务器名称，然后选择“添加角色和功能”。

2. 在“ **安装类型** ”页上，选择“ **基于角色或基于功能的安装** ”。

3. 在“功能”页上，展开“.NET 3.5 Framework 功能”节点，然后选择“.NET Framework 3.5（包括 .NET 2.0 和 3.0）”。

   Windows PowerShell 2.0 引擎不需要该节点下的其他选项。

#### <a name="to-add-the-windows-powershell-20-engine-feature"></a>添加 Windows PowerShell 2.0 引擎功能

- 在“服务器管理器”中，从“管理”菜单上，选择“添加角色和功能”。

  或者“ **服务器管理器** ”，单击“ **所有服务器** ”，右键单击服务器名称，然后选择“ **添加角色和功能** ”。

- 在“ **安装类型** ”页上，选择“ **基于角色或基于功能的安装** ”。

- 在 **功能** 页上，展开 **Windows PowerShell (已安装)** 节点，然后选择 **Windows PowerShell 2.0 引擎** 。

有关启动 Windows PowerShell 2.0 引擎的信息，请参阅[启动 Windows PowerShell 2.0 引擎](../Starting-the-Windows-PowerShell-2.0-Engine.md)。

## <a name="on-earlier-systems"></a>在较早的系统上

在 Windows 7、Windows Server 2008 R2 和 Windows Server 2012 上安装 Windows PowerShell 4.0 的 [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881) 程序包中包括 Windows PowerShell 2.0 引擎。 Windows PowerShell 2.0 引擎已启用并可供使用（若需要），而无需其他安装、设置或配置。

在 Windows 7、Windows Server 2008 R2 和 Windows Server 2008 上安装 Windows PowerShell 3.0 的 Windows Management Framework 3.0 程序包中包括 Windows PowerShell 2.0 引擎。 Windows PowerShell 2.0 引擎已启用并可供使用（若需要），而无需其他安装、设置或配置。

## <a name="see-also"></a>另请参阅

- [Windows PowerShell 系统要求](Windows-PowerShell-System-Requirements.md)
- [安装 Windows PowerShell](Installing-Windows-PowerShell.md)
- [启动 Windows PowerShell](/previous-versions/ms714415(v=vs.85))
- [启动 Windows PowerShell 2.0 引擎](../Starting-the-Windows-PowerShell-2.0-Engine.md)
