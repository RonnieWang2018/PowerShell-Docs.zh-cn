---
title: Cmdlet 代码中的属性 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853783"
---
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="2bc56-102">Cmdlet 代码中的属性</span><span class="sxs-lookup"><span data-stu-id="2bc56-102">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="2bc56-103">若要使用提供的 Windows PowerShell 的常见功能，类和 cmdlet 代码中定义的公共属性进行修饰的属性。</span><span class="sxs-lookup"><span data-stu-id="2bc56-103">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="2bc56-104">例如，以下类定义使用 Cmdlet 属性来标识在其中的 Microsoft.NET Framework 类**Get-proc** cmdlet 实现。</span><span class="sxs-lookup"><span data-stu-id="2bc56-104">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="2bc56-105">(此 cmdlet 用作示例，请参见本文档中，它类似于`Get-Process`提供的 Windows PowerShell cmdlet。)</span><span class="sxs-lookup"><span data-stu-id="2bc56-105">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="2bc56-106">这些属性被视为元数据，因为它们的实现是独立于实现的 cmdlet 代码。</span><span class="sxs-lookup"><span data-stu-id="2bc56-106">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="2bc56-107">Windows PowerShell 运行时在该 cmdlet，它将识别特性，然后为每个属性执行适当的操作。</span><span class="sxs-lookup"><span data-stu-id="2bc56-107">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="2bc56-108">虽然你可能想要实现自己的这些属性提供的功能版本，但好 cmdlet 设计使用这些常见的功能。</span><span class="sxs-lookup"><span data-stu-id="2bc56-108">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="2bc56-109">有关可以在 cmdlet 中声明的不同属性的详细信息，请参阅[属性类型](./attribute-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2bc56-109">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2bc56-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2bc56-110">See Also</span></span>

[<span data-ttu-id="2bc56-111">属性类型</span><span class="sxs-lookup"><span data-stu-id="2bc56-111">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="2bc56-112">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2bc56-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)