---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: efe0e6c9287b3595988aa3ffc520ce46699cafda
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93197447"
---
# <span data-ttu-id="e1b6b-103">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="e1b6b-103">Exit-PSSession</span></span>

## <span data-ttu-id="e1b6b-104">摘要</span><span class="sxs-lookup"><span data-stu-id="e1b6b-104">SYNOPSIS</span></span>
<span data-ttu-id="e1b6b-105">结束与远程计算机的交互式会话。</span><span class="sxs-lookup"><span data-stu-id="e1b6b-105">Ends an interactive session with a remote computer.</span></span>

## <span data-ttu-id="e1b6b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e1b6b-106">SYNTAX</span></span>

```
Exit-PSSession [<CommonParameters>]
```

## <span data-ttu-id="e1b6b-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e1b6b-107">DESCRIPTION</span></span>
<span data-ttu-id="e1b6b-108">**Exit-PSSession** cmdlet 结束使用 Enter-PSSession cmdlet 启动的交互式会话。</span><span class="sxs-lookup"><span data-stu-id="e1b6b-108">The **Exit-PSSession** cmdlet ends interactive sessions that you started by using the Enter-PSSession cmdlet.</span></span>

<span data-ttu-id="e1b6b-109">你还可以使用 **Exit** 关键字来结束交互式会话。</span><span class="sxs-lookup"><span data-stu-id="e1b6b-109">You can also use the **Exit** keyword to end an interactive session.</span></span>
<span data-ttu-id="e1b6b-110">其效果与使用 **Exit-PSSession** 相同。</span><span class="sxs-lookup"><span data-stu-id="e1b6b-110">The effect is the same as using **Exit-PSSession** .</span></span>

## <span data-ttu-id="e1b6b-111">示例</span><span class="sxs-lookup"><span data-stu-id="e1b6b-111">EXAMPLES</span></span>

### <span data-ttu-id="e1b6b-112">示例1：启动和停止交互式会话</span><span class="sxs-lookup"><span data-stu-id="e1b6b-112">Example 1: Start and stop an interactive session</span></span>

```
PS C:\> Enter-PSSession -computername Server01
Server01\PS> Exit-PSSession
PS C:\>
```

<span data-ttu-id="e1b6b-113">这些命令启动与 Server01 远程计算机的交互式会话，然后停止该会话。</span><span class="sxs-lookup"><span data-stu-id="e1b6b-113">These commands start and then stop an interactive session with the Server01 remote computer.</span></span>

### <span data-ttu-id="e1b6b-114">示例2：使用 PSSession 对象启动和停止交互式会话</span><span class="sxs-lookup"><span data-stu-id="e1b6b-114">Example 2: Start and stop an interactive session by using a PSSession object</span></span>

```
PS C:\> $s = New-PSSession -ComputerName Server01
PS C:\> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS C:\> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

<span data-ttu-id="e1b6b-115">这些命令启动和停止与使用 Windows PowerShell 会话 ( **PSSession** ) 的 Server01 计算机的交互式会话。</span><span class="sxs-lookup"><span data-stu-id="e1b6b-115">These commands start and stop an interactive session with the Server01 computer that uses a Windows PowerShell session ( **PSSession** ).</span></span>

<span data-ttu-id="e1b6b-116">由于交互式会话是通过使用 Windows PowerShell 会话启动的，因此，当交互式会话结束时， **PSSession** 仍然可用。</span><span class="sxs-lookup"><span data-stu-id="e1b6b-116">Because the interactive session was started by using a Windows PowerShell session, the **PSSession** is still available when the interactive session ends.</span></span>
<span data-ttu-id="e1b6b-117">如果使用 *ComputerName* 参数，则 **输入-PSSession** 会创建一个临时会话，当交互式会话结束时，该会话将关闭。</span><span class="sxs-lookup"><span data-stu-id="e1b6b-117">If you use the *ComputerName* parameter, **Enter-PSSession** creates a temporary session that it closes when the interactive session ends.</span></span>

<span data-ttu-id="e1b6b-118">第一个命令使用 New-PSSession cmdlet 在 Server01 计算机上创建 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="e1b6b-118">The first command uses the New-PSSession cmdlet to create a **PSSession** on the Server01 computer.</span></span>
<span data-ttu-id="e1b6b-119">该命令将 **PSSession** 保存在 $s 的变量中。</span><span class="sxs-lookup"><span data-stu-id="e1b6b-119">The command saves the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="e1b6b-120">第二个命令使用 **Enter-PSSession** 在 $s 中使用 **PSSession** 启动交互式会话。</span><span class="sxs-lookup"><span data-stu-id="e1b6b-120">The second command uses **Enter-PSSession** to start an interactive session using the **PSSession** in $s.</span></span>

<span data-ttu-id="e1b6b-121">第三个命令使用 **Exit-PSSession** 来停止交互会话。</span><span class="sxs-lookup"><span data-stu-id="e1b6b-121">The third command uses **Exit-PSSession** to stop the interactive session.</span></span>

<span data-ttu-id="e1b6b-122">最后一个命令显示 $s 变量中的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="e1b6b-122">The final command displays the **PSSession** in the $s variable.</span></span>
<span data-ttu-id="e1b6b-123">**State** 属性显示 **PSSession** 仍处于打开状态并可供使用。</span><span class="sxs-lookup"><span data-stu-id="e1b6b-123">The **State** property shows the **PSSession** is still open and available for use.</span></span>

### <span data-ttu-id="e1b6b-124">示例3：使用 Exit 关键字停止会话</span><span class="sxs-lookup"><span data-stu-id="e1b6b-124">Example 3: Use the Exit keyword to stop a session</span></span>

```
PS C:\> Enter-PSSession -computername Server01
Server01\PS> exit
PS C:\>
```

<span data-ttu-id="e1b6b-125">此示例使用 **Exit** 关键字来停止使用 **Enter-PSSession** 启动的交互式会话。</span><span class="sxs-lookup"><span data-stu-id="e1b6b-125">This example uses the **Exit** keyword to stop an interactive session started by using **Enter-PSSession** .</span></span>
<span data-ttu-id="e1b6b-126">**Exit** 关键字与使用 **exit-PSSession** 具有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="e1b6b-126">The **Exit** keyword has the same effect as using **Exit-PSSession** .</span></span>

## <span data-ttu-id="e1b6b-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e1b6b-127">PARAMETERS</span></span>

### <span data-ttu-id="e1b6b-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e1b6b-128">CommonParameters</span></span>
<span data-ttu-id="e1b6b-129">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="e1b6b-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e1b6b-130">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="e1b6b-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e1b6b-131">输入</span><span class="sxs-lookup"><span data-stu-id="e1b6b-131">INPUTS</span></span>

### <span data-ttu-id="e1b6b-132">无</span><span class="sxs-lookup"><span data-stu-id="e1b6b-132">None</span></span>
<span data-ttu-id="e1b6b-133">不能通过管道将对象传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e1b6b-133">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="e1b6b-134">输出</span><span class="sxs-lookup"><span data-stu-id="e1b6b-134">OUTPUTS</span></span>

### <span data-ttu-id="e1b6b-135">无</span><span class="sxs-lookup"><span data-stu-id="e1b6b-135">None</span></span>
<span data-ttu-id="e1b6b-136">此 cmdlet 不返回任何输出。</span><span class="sxs-lookup"><span data-stu-id="e1b6b-136">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="e1b6b-137">注释</span><span class="sxs-lookup"><span data-stu-id="e1b6b-137">NOTES</span></span>

* <span data-ttu-id="e1b6b-138">此 cmdlet 仅提取通用参数。</span><span class="sxs-lookup"><span data-stu-id="e1b6b-138">This cmdlet takes only the common parameters.</span></span>


## <span data-ttu-id="e1b6b-139">相关链接</span><span class="sxs-lookup"><span data-stu-id="e1b6b-139">RELATED LINKS</span></span>

[<span data-ttu-id="e1b6b-140">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="e1b6b-140">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="e1b6b-141">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="e1b6b-141">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="e1b6b-142">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="e1b6b-142">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="e1b6b-143">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="e1b6b-143">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="e1b6b-144">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="e1b6b-144">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="e1b6b-145">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="e1b6b-145">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="e1b6b-146">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="e1b6b-146">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="e1b6b-147">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="e1b6b-147">Remove-PSSession</span></span>](Remove-PSSession.md)
