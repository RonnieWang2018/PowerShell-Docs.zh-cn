---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/set-logproperties?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LogProperties
ms.openlocfilehash: e5d66d628f2240c86c8b94b846b0397d517adf43
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93197354"
---
# <span data-ttu-id="1ff95-102">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="1ff95-102">Set-LogProperties</span></span>

## <span data-ttu-id="1ff95-103">摘要</span><span class="sxs-lookup"><span data-stu-id="1ff95-103">SYNOPSIS</span></span>
<span data-ttu-id="1ff95-104">更改 Windows 事件日志的属性。</span><span class="sxs-lookup"><span data-stu-id="1ff95-104">Changes the properties of a Windows event log.</span></span>

## <span data-ttu-id="1ff95-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1ff95-105">SYNTAX</span></span>

```
Set-LogProperties [-LogDetails] <LogDetails> [-Force] [<CommonParameters>]
```

## <span data-ttu-id="1ff95-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1ff95-106">DESCRIPTION</span></span>

<span data-ttu-id="1ff95-107">此 cmdlet 更改 Windows 事件日志的配置设置。</span><span class="sxs-lookup"><span data-stu-id="1ff95-107">This cmdlet changes the configuration settings of a Windows event log.</span></span> <span data-ttu-id="1ff95-108">此 cmdlet 由 `Enable-PSTrace` 和 `Disable-PSTrace` cmdlet 使用。</span><span class="sxs-lookup"><span data-stu-id="1ff95-108">This cmdlet is used by the `Enable-PSTrace` and `Disable-PSTrace` cmdlets.</span></span>

<span data-ttu-id="1ff95-109">必须从提升的 PowerShell 会话中运行此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1ff95-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="1ff95-110">示例</span><span class="sxs-lookup"><span data-stu-id="1ff95-110">EXAMPLES</span></span>

### <span data-ttu-id="1ff95-111">示例1：更改 Windows PowerShell 事件日志的保留设置</span><span class="sxs-lookup"><span data-stu-id="1ff95-111">Example 1: Change the retention setting of the Windows PowerShell event log</span></span>

```powershell
$logDetails = Get-LogProperties 'Windows PowerShell'
$logDetails.Retention = $True
Set-LogProperties -LogDetails $logDetails
Get-LogProperties 'Windows PowerShell'
```

```Output
Name       : Windows PowerShell
Enabled    : True
Type       : Admin
Retention  : True
AutoBackup : False
MaxLogSize : 15728640
```

## <span data-ttu-id="1ff95-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1ff95-112">PARAMETERS</span></span>

### <span data-ttu-id="1ff95-113">-Force</span><span class="sxs-lookup"><span data-stu-id="1ff95-113">-Force</span></span>

<span data-ttu-id="1ff95-114">用于在不提示的情况下强制更改。</span><span class="sxs-lookup"><span data-stu-id="1ff95-114">Used to force the change without prompting.</span></span>

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

### <span data-ttu-id="1ff95-115">-LogDetails</span><span class="sxs-lookup"><span data-stu-id="1ff95-115">-LogDetails</span></span>

<span data-ttu-id="1ff95-116">要分配给事件日志的已更新配置设置。</span><span class="sxs-lookup"><span data-stu-id="1ff95-116">The updated configuration settings to be assigned to the event log.</span></span>

```yaml
Type: Microsoft.PowerShell.Diagnostics.LogDetails
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1ff95-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1ff95-117">CommonParameters</span></span>

<span data-ttu-id="1ff95-118">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="1ff95-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1ff95-119">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="1ff95-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1ff95-120">输入</span><span class="sxs-lookup"><span data-stu-id="1ff95-120">INPUTS</span></span>

### <span data-ttu-id="1ff95-121">LogDetails。</span><span class="sxs-lookup"><span data-stu-id="1ff95-121">Microsoft.PowerShell.Diagnostics.LogDetails</span></span>

<span data-ttu-id="1ff95-122">必须将完全配置的 **LogDetails** 对象传递给 `Set-LogProperties` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1ff95-122">You must pass a fully configured **LogDetails** object to the `Set-LogProperties` cmdlet.</span></span>
<span data-ttu-id="1ff95-123">因此，若要更改一个设置，您应该使用 `Get-LogProperties` 来检索当前配置。</span><span class="sxs-lookup"><span data-stu-id="1ff95-123">Therefore, to change one setting, you should use `Get-LogProperties` to retrieve the current configuration.</span></span>

## <span data-ttu-id="1ff95-124">输出</span><span class="sxs-lookup"><span data-stu-id="1ff95-124">OUTPUTS</span></span>

### <span data-ttu-id="1ff95-125">无</span><span class="sxs-lookup"><span data-stu-id="1ff95-125">None</span></span>

## <span data-ttu-id="1ff95-126">注释</span><span class="sxs-lookup"><span data-stu-id="1ff95-126">NOTES</span></span>

<span data-ttu-id="1ff95-127">必须从提升的 PowerShell 会话中运行此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1ff95-127">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="1ff95-128">相关链接</span><span class="sxs-lookup"><span data-stu-id="1ff95-128">RELATED LINKS</span></span>

[<span data-ttu-id="1ff95-129">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="1ff95-129">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="1ff95-130">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="1ff95-130">Enable-PSTrace</span></span>](Enable-PSTrace.md)

[<span data-ttu-id="1ff95-131">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="1ff95-131">Disable-PSTrace</span></span>](Disable-PSTrace.md)

