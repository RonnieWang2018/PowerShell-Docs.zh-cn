---
title: GetProc01 (C#) Sample Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65094bb7-1972-44b3-b8b0-5f639860b58c
caps.latest.revision: 5
ms.openlocfilehash: 32c8214935a8c9f455426b76966d8c7fb33353d4
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57430071"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="666db-102">GetProc01 (C#) 示例代码</span><span class="sxs-lookup"><span data-stu-id="666db-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="666db-103">下面的代码演示 GetProc01 示例 cmdlet 的实现。</span><span class="sxs-lookup"><span data-stu-id="666db-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="666db-104">请注意，该 cmdlet 简化了离开进程检索到的实际工作[System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses)方法。</span><span class="sxs-lookup"><span data-stu-id="666db-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="666db-105">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件此 Get-proc cmdlet 的源文件 (getproc01.cs)。</span><span class="sxs-lookup"><span data-stu-id="666db-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="666db-106">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="666db-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="666db-107">已下载的源文件中有 **\<PowerShell 示例 >** 目录。</span><span class="sxs-lookup"><span data-stu-id="666db-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="666db-108">代码示例</span><span class="sxs-lookup"><span data-stu-id="666db-108">Code Sample</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L11-L126 "GetProcessSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="666db-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="666db-109">See Also</span></span>

[<span data-ttu-id="666db-110">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="666db-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="666db-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="666db-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)