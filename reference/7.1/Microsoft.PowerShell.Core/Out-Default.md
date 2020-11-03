---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-default?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Default
ms.openlocfilehash: c1293b93079fed439c42d6ba41747cbe6a0c33fe
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93198789"
---
# <span data-ttu-id="3ade8-103">Out-Default</span><span class="sxs-lookup"><span data-stu-id="3ade8-103">Out-Default</span></span>

## <span data-ttu-id="3ade8-104">摘要</span><span class="sxs-lookup"><span data-stu-id="3ade8-104">SYNOPSIS</span></span>
<span data-ttu-id="3ade8-105">将输出发送到默认的格式化程序和默认的输出 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3ade8-105">Sends the output to the default formatter and to the default output cmdlet.</span></span>

## <span data-ttu-id="3ade8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3ade8-106">SYNTAX</span></span>

```
Out-Default [-Transcript] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="3ade8-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3ade8-107">DESCRIPTION</span></span>

<span data-ttu-id="3ade8-108">PowerShell 会自动添加 `Out-Default` 到每个管道的末尾。</span><span class="sxs-lookup"><span data-stu-id="3ade8-108">PowerShell automatically adds `Out-Default` to the end of every pipeline.</span></span> <span data-ttu-id="3ade8-109">`Out-Default` 确定如何格式化和输出对象流。</span><span class="sxs-lookup"><span data-stu-id="3ade8-109">`Out-Default` decides how to format and output the object stream.</span></span> <span data-ttu-id="3ade8-110">如果对象流是字符串流，则 `Out-Default` 直接将这些对象传递给 `Out-Host` 调用主机提供的相应 api 的管道。</span><span class="sxs-lookup"><span data-stu-id="3ade8-110">If the object stream is a stream of strings, `Out-Default` pipes these directly to `Out-Host` which calls the appropriate APIs provided by the host.</span></span> <span data-ttu-id="3ade8-111">如果对象流不包含字符串，将 `Out-Default` 检查对象以确定要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="3ade8-111">If the object stream does not contain strings, `Out-Default` inspects the object to determine what to do.</span></span>
<span data-ttu-id="3ade8-112">首先，它将查看对象类型并确定是否有此对象类型的已注册 _视图_ 。</span><span class="sxs-lookup"><span data-stu-id="3ade8-112">First it looks at the object type and determines whether there is a registered _view_ for this object type.</span></span>

<span data-ttu-id="3ade8-113">PowerShell 定义 (cmdlet) 的 XML 架构和机制， `Update-FormatData` 任何人都可以在其中注册对象类型的视图。</span><span class="sxs-lookup"><span data-stu-id="3ade8-113">PowerShell defines XML schema and a mechanism (the `Update-FormatData` cmdlet) where anyone can register views for an object type.</span></span> <span data-ttu-id="3ade8-114">您可以为任何对象类型指定 " **宽** "、" **列表** "、" **表** " 或 " **自定义** " 视图。</span><span class="sxs-lookup"><span data-stu-id="3ade8-114">You can specify **wide** , **list** , **table** , or **custom** views for any object type.</span></span> <span data-ttu-id="3ade8-115">视图指定要显示的属性以及显示方式。</span><span class="sxs-lookup"><span data-stu-id="3ade8-115">The views specify which properties to display and how they should be displayed.</span></span> <span data-ttu-id="3ade8-116">如果已注册视图，它将定义要使用的格式化程序。</span><span class="sxs-lookup"><span data-stu-id="3ade8-116">If a view is registered, it defines which formatter to use.</span></span> <span data-ttu-id="3ade8-117">因此，如果已注册的视图是 **表** 视图，则将 `Out-Default` 对象流式传输到 `Format-Table | Out-Host` 。</span><span class="sxs-lookup"><span data-stu-id="3ade8-117">So if the registered view is a **table** view, `Out-Default` streams the objects to `Format-Table | Out-Host`.</span></span> <span data-ttu-id="3ade8-118">`Format-Table` 将对象转换为 (由视图) 定义中的数据驱动的格式设置记录流，并 `Out-Host` 将格式设置记录转换为主机接口上的调用。</span><span class="sxs-lookup"><span data-stu-id="3ade8-118">`Format-Table` transforms the objects into a stream of Formatting records (driven by the data in the view definition) and `Out-Host` transforms the formatting records into calls on the Host interface.</span></span>

## <span data-ttu-id="3ade8-119">示例</span><span class="sxs-lookup"><span data-stu-id="3ade8-119">EXAMPLES</span></span>

### <span data-ttu-id="3ade8-120">示例 1</span><span class="sxs-lookup"><span data-stu-id="3ade8-120">Example 1</span></span>

<span data-ttu-id="3ade8-121">尽管此 cmdlet 不应由最终用户直接运行，但也可以是。</span><span class="sxs-lookup"><span data-stu-id="3ade8-121">While this cmdlet is not intended to be run directly by the end user, it can be.</span></span>

```powershell
Get-Process | Select-Object -First 5 | Out-Default
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     12     2.56       5.20       0.00    7376   0 aesm_service
     48    34.32      18.10      26.64    9320  13 AlertusDesktopAlert
     24    13.97      12.74       0.77   12656  13 ApplicationFrameHost
      8     1.79       4.41       0.00    8180   0 AppVShNotify
      9     1.99       5.07       0.19   19320  13 AppVShNotify
```

## <span data-ttu-id="3ade8-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3ade8-122">PARAMETERS</span></span>

### <span data-ttu-id="3ade8-123">-InputObject</span><span class="sxs-lookup"><span data-stu-id="3ade8-123">-InputObject</span></span>

<span data-ttu-id="3ade8-124">接受 cmdlet 的输入。</span><span class="sxs-lookup"><span data-stu-id="3ade8-124">Accepts input to the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3ade8-125">-脚本</span><span class="sxs-lookup"><span data-stu-id="3ade8-125">-Transcript</span></span>

<span data-ttu-id="3ade8-126">确定是否应将输出发送到 PowerShell 的脚本服务。</span><span class="sxs-lookup"><span data-stu-id="3ade8-126">Determines whether the output should be sent to PowerShell's transcription services.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ade8-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3ade8-127">CommonParameters</span></span>

<span data-ttu-id="3ade8-128">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3ade8-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3ade8-129">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="3ade8-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3ade8-130">输入</span><span class="sxs-lookup"><span data-stu-id="3ade8-130">INPUTS</span></span>

## <span data-ttu-id="3ade8-131">输出</span><span class="sxs-lookup"><span data-stu-id="3ade8-131">OUTPUTS</span></span>

## <span data-ttu-id="3ade8-132">注释</span><span class="sxs-lookup"><span data-stu-id="3ade8-132">NOTES</span></span>

## <span data-ttu-id="3ade8-133">相关链接</span><span class="sxs-lookup"><span data-stu-id="3ade8-133">RELATED LINKS</span></span>

[<span data-ttu-id="3ade8-134">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="3ade8-134">Format-Custom</span></span>](../Microsoft.PowerShell.Utility/Format-Custom.md)

[<span data-ttu-id="3ade8-135">Format-List</span><span class="sxs-lookup"><span data-stu-id="3ade8-135">Format-List</span></span>](../Microsoft.PowerShell.Utility/Format-List.md)

[<span data-ttu-id="3ade8-136">Format-Table</span><span class="sxs-lookup"><span data-stu-id="3ade8-136">Format-Table</span></span>](../Microsoft.PowerShell.Utility/Format-Table.md)

[<span data-ttu-id="3ade8-137">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="3ade8-137">Format-Wide</span></span>](../Microsoft.PowerShell.Utility/Format-Wide.md)

[<span data-ttu-id="3ade8-138">about_Format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="3ade8-138">about_Format.ps1xml</span></span>](About/about_Format.ps1xml.md)

[<span data-ttu-id="3ade8-139">PowerShell 格式设置和输出的实际工作原理</span><span class="sxs-lookup"><span data-stu-id="3ade8-139">How PowerShell Formatting and Outputting REALLY works</span></span>](https://devblogs.microsoft.com/powershell/how-powershell-formatting-and-outputting-really-works/)

