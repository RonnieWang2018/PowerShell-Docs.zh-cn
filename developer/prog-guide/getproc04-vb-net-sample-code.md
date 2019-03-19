---
title: GetProc04 (VB.NET) Sample Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d22f47b-3679-4587-a559-94454415d2dd
caps.latest.revision: 5
ms.openlocfilehash: 0d0d1a3f82bc2cee025139d69fee02eb601fa563
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055455"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="55b21-102">GetProc04 (VB.NET) 示例代码</span><span class="sxs-lookup"><span data-stu-id="55b21-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="55b21-103">下面的代码演示如何实现`Get-Process`cmdlet，它报告非终止错误。</span><span class="sxs-lookup"><span data-stu-id="55b21-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="55b21-104">此实现会调用[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)报告非终止错误的方法。</span><span class="sxs-lookup"><span data-stu-id="55b21-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="55b21-105">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件此 Get-proc cmdlet 的源文件 (getprov04.cs)。</span><span class="sxs-lookup"><span data-stu-id="55b21-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="55b21-106">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="55b21-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="55b21-107">已下载的源文件中有 **\<PowerShell 示例 >** 目录。</span><span class="sxs-lookup"><span data-stu-id="55b21-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="55b21-108">代码示例</span><span class="sxs-lookup"><span data-stu-id="55b21-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="55b21-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="55b21-109">See Also</span></span>

[<span data-ttu-id="55b21-110">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="55b21-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="55b21-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="55b21-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)