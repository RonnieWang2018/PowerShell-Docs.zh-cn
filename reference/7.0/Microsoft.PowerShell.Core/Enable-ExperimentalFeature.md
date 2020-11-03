---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-experimentalfeature?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ExperimentalFeature
ms.openlocfilehash: 79884c73bc6e010eb218f1b722d26e0aaa05ef53
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2020
ms.locfileid: "93197176"
---
# <span data-ttu-id="4cad9-102">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="4cad9-102">Enable-ExperimentalFeature</span></span>

## <span data-ttu-id="4cad9-103">摘要</span><span class="sxs-lookup"><span data-stu-id="4cad9-103">SYNOPSIS</span></span>
<span data-ttu-id="4cad9-104">启动新的 PowerShell 实例时启用实验性功能。</span><span class="sxs-lookup"><span data-stu-id="4cad9-104">Enable an experimental feature on startup of new instance of PowerShell.</span></span>

## <span data-ttu-id="4cad9-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4cad9-105">SYNTAX</span></span>

```
Enable-ExperimentalFeature [-Name] <String[]> [-Scope <ConfigScope>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4cad9-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4cad9-106">DESCRIPTION</span></span>

<span data-ttu-id="4cad9-107">`Enable-ExperimentalFeature`Cmdlet 可通过将命名实验功能添加到 `powershell.config.json` 在 PowerShell 启动时读取的设置文件来启用实验性功能。</span><span class="sxs-lookup"><span data-stu-id="4cad9-107">The `Enable-ExperimentalFeature` cmdlet enables experimental features by adding the named experimental features to the `powershell.config.json` settings file read on PowerShell startup.</span></span>

<span data-ttu-id="4cad9-108">此 cmdlet 是在 PowerShell 6.2 中引入的。</span><span class="sxs-lookup"><span data-stu-id="4cad9-108">This cmdlet was introduced in PowerShell 6.2.</span></span>

> [!NOTE]
> <span data-ttu-id="4cad9-109">对实验性功能状态所做的任何更改仅会在重新启动 PowerShell 时生效</span><span class="sxs-lookup"><span data-stu-id="4cad9-109">Any changes to experimental feature state only takes effect on restart of PowerShell</span></span>

## <span data-ttu-id="4cad9-110">示例</span><span class="sxs-lookup"><span data-stu-id="4cad9-110">EXAMPLES</span></span>

### <span data-ttu-id="4cad9-111">示例1：启用实验性功能</span><span class="sxs-lookup"><span data-stu-id="4cad9-111">Example 1: Enable an experimental feature</span></span>

<span data-ttu-id="4cad9-112">在此示例中，如果之前禁用了此试验功能，则将 `powershell.config.json` 更新文件，以便用户在 PowerShell 重新启动后启用该功能。</span><span class="sxs-lookup"><span data-stu-id="4cad9-112">In this example, if this experimental feature was previously disabled, then the `powershell.config.json` file is updated for the user to enable that feature once PowerShell is restarted.</span></span>
<span data-ttu-id="4cad9-113">如果成功，则不会输出到管道，并且只显示一条警告消息。</span><span class="sxs-lookup"><span data-stu-id="4cad9-113">Upon success nothing is output to the pipeline and only a warning message is displayed.</span></span>

```powershell
Enable-ExperimentalFeature PSImplicitRemotingBatching
```

```Output
WARNING: Enabling and disabling experimental features do not take effect until next start of PowerShell.
```

## <span data-ttu-id="4cad9-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4cad9-114">PARAMETERS</span></span>

### <span data-ttu-id="4cad9-115">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4cad9-115">-Confirm</span></span>

<span data-ttu-id="4cad9-116">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="4cad9-116">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4cad9-117">-Name</span><span class="sxs-lookup"><span data-stu-id="4cad9-117">-Name</span></span>

<span data-ttu-id="4cad9-118">要启用的实验功能的名称。</span><span class="sxs-lookup"><span data-stu-id="4cad9-118">The name or names of the experimental features to enable.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4cad9-119">-Scope</span><span class="sxs-lookup"><span data-stu-id="4cad9-119">-Scope</span></span>

<span data-ttu-id="4cad9-120">确定 `powershell.config.json` 要更新哪个用户是否影响所有用户或仅影响当前用户。</span><span class="sxs-lookup"><span data-stu-id="4cad9-120">Determines which `powershell.config.json` to update whether it affects all users or just the current user.</span></span>

```yaml
Type: System.Management.Automation.Configuration.ConfigScope
Parameter Sets: (All)
Aliases:
Accepted values: AllUsers, CurrentUser

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4cad9-121">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4cad9-121">-WhatIf</span></span>

<span data-ttu-id="4cad9-122">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="4cad9-122">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="4cad9-123">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="4cad9-123">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4cad9-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4cad9-124">CommonParameters</span></span>

<span data-ttu-id="4cad9-125">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4cad9-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4cad9-126">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4cad9-126">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4cad9-127">输入</span><span class="sxs-lookup"><span data-stu-id="4cad9-127">INPUTS</span></span>

### <span data-ttu-id="4cad9-128">ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="4cad9-128">ExperimentalFeature</span></span>

<span data-ttu-id="4cad9-129">要启用的 ExperimentalFeature 从 cmdlet 的管道实例 `Get-ExperimentalFeature` 。</span><span class="sxs-lookup"><span data-stu-id="4cad9-129">Pipe instances of ExperimentalFeature from `Get-ExperimentalFeature` cmdlet to enable.</span></span>

## <span data-ttu-id="4cad9-130">输出</span><span class="sxs-lookup"><span data-stu-id="4cad9-130">OUTPUTS</span></span>

### <span data-ttu-id="4cad9-131">无</span><span class="sxs-lookup"><span data-stu-id="4cad9-131">None</span></span>

<span data-ttu-id="4cad9-132">此 cmdlet 不返回任何输出。</span><span class="sxs-lookup"><span data-stu-id="4cad9-132">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="4cad9-133">注释</span><span class="sxs-lookup"><span data-stu-id="4cad9-133">NOTES</span></span>

<span data-ttu-id="4cad9-134">对实验功能的状态的更改仅在重新启动 PowerShell 时才会生效。</span><span class="sxs-lookup"><span data-stu-id="4cad9-134">Changes to state of an experimental feature only take effect on restart of PowerShell.</span></span>

## <span data-ttu-id="4cad9-135">相关链接</span><span class="sxs-lookup"><span data-stu-id="4cad9-135">RELATED LINKS</span></span>

[<span data-ttu-id="4cad9-136">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="4cad9-136">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="4cad9-137">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="4cad9-137">Get-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)
