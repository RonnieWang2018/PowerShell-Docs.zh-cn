---
description: 描述联接运算符 ( 联接) 如何将多个字符串合并为一个字符串。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_join?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Join
ms.openlocfilehash: d89b9066ef34e814c0e546246c7b50cfc73bcb38
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/13/2020
ms.locfileid: "93199993"
---
# <a name="about-join"></a><span data-ttu-id="f2566-104">关于联接</span><span class="sxs-lookup"><span data-stu-id="f2566-104">About join</span></span>

## <a name="short-description"></a><span data-ttu-id="f2566-105">简短说明</span><span class="sxs-lookup"><span data-stu-id="f2566-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="f2566-106">描述联接运算符 ( 联接) 如何将多个字符串合并为一个字符串。</span><span class="sxs-lookup"><span data-stu-id="f2566-106">Describes how the join operator (-join) combines multiple strings into a single string.</span></span>

## <a name="long-description"></a><span data-ttu-id="f2566-107">详细说明</span><span class="sxs-lookup"><span data-stu-id="f2566-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="f2566-108">联接运算符将一组字符串连接成一个字符串。</span><span class="sxs-lookup"><span data-stu-id="f2566-108">The join operator concatenates a set of strings into a single string.</span></span> <span data-ttu-id="f2566-109">字符串将按照它们在命令中出现的顺序追加到结果字符串。</span><span class="sxs-lookup"><span data-stu-id="f2566-109">The strings are appended to the resulting string in the order that they appear in the command.</span></span>

### <a name="syntax"></a><span data-ttu-id="f2566-110">语法</span><span class="sxs-lookup"><span data-stu-id="f2566-110">Syntax</span></span>

<span data-ttu-id="f2566-111">下图显示了联接运算符的语法。</span><span class="sxs-lookup"><span data-stu-id="f2566-111">The following diagram shows the syntax for the join operator.</span></span>

```powershell
-Join <String[]>
<String[]> -Join <Delimiter>
```

#### <a name="parameters"></a><span data-ttu-id="f2566-112">parameters</span><span class="sxs-lookup"><span data-stu-id="f2566-112">Parameters</span></span>

<span data-ttu-id="f2566-113">String []-指定要联接的一个或多个字符串。</span><span class="sxs-lookup"><span data-stu-id="f2566-113">String[] - Specifies one or more strings to be joined.</span></span>

<span data-ttu-id="f2566-114">分隔符-指定在串联的字符串之间放置的一个或多个字符。</span><span class="sxs-lookup"><span data-stu-id="f2566-114">Delimiter - Specifies one or more characters placed between the concatenated strings.</span></span> <span data-ttu-id="f2566-115">默认值为 "" )  ( 分隔符。</span><span class="sxs-lookup"><span data-stu-id="f2566-115">The default is no delimiter ("").</span></span>

<span data-ttu-id="f2566-116">备注</span><span class="sxs-lookup"><span data-stu-id="f2566-116">Remarks</span></span>

<span data-ttu-id="f2566-117">一元联接运算符 ( 联接 <string [] >) 的优先级高于逗号。</span><span class="sxs-lookup"><span data-stu-id="f2566-117">The unary join operator (-join <string[]>) has higher precedence than a comma.</span></span> <span data-ttu-id="f2566-118">因此，如果您将逗号分隔的字符串列表提交给一元联接运算符，则在第一个逗号) 之前仅 (第一个字符串提交到联接运算符。</span><span class="sxs-lookup"><span data-stu-id="f2566-118">As a result, if you submit a comma-separated list of strings to the unary join operator, only the first string (before the first comma) is submitted to the join operator.</span></span>

<span data-ttu-id="f2566-119">若要使用一元联接运算符，请将字符串括在括号中，或将字符串存储在变量中，然后提交要联接的变量。</span><span class="sxs-lookup"><span data-stu-id="f2566-119">To use the unary join operator, enclose the strings in parentheses, or store the strings in a variable, and then submit the variable to join.</span></span>

<span data-ttu-id="f2566-120">例如：</span><span class="sxs-lookup"><span data-stu-id="f2566-120">For example:</span></span>

```powershell
-join "a", "b", "c"
a
b
c

-join ("a", "b", "c")
abc

$z = "a", "b", "c"
-join $z
abc
```

### <a name="examples"></a><span data-ttu-id="f2566-121">示例</span><span class="sxs-lookup"><span data-stu-id="f2566-121">Examples</span></span>

<span data-ttu-id="f2566-122">下面的语句联接了三个字符串：</span><span class="sxs-lookup"><span data-stu-id="f2566-122">The following statement joins three strings:</span></span>

```powershell
-join ("Windows", "PowerShell", "2.0")
WindowsPowerShell2.0
```

<span data-ttu-id="f2566-123">下面的语句联接由空格分隔的三个字符串：</span><span class="sxs-lookup"><span data-stu-id="f2566-123">The following statement joins three strings delimited by a space:</span></span>

```powershell
"Windows", "PowerShell", "2.0" -join " "
Windows PowerShell 2.0
```

<span data-ttu-id="f2566-124">以下语句使用多字符分隔符来联接三个字符串：</span><span class="sxs-lookup"><span data-stu-id="f2566-124">The following statements use a multiple-character delimiter to join three strings:</span></span>

```powershell
$a = "WIND", "S P", "ERSHELL"
$a -join "OW"
WINDOWS POWERSHELL
```

<span data-ttu-id="f2566-125">下面的语句将下一个字符串中的行联接到一个字符串中。</span><span class="sxs-lookup"><span data-stu-id="f2566-125">The following statement joins the lines in a here-string into a single string.</span></span> <span data-ttu-id="f2566-126">由于此字符串是一个字符串，因此必须先拆分此字符串中的行，然后才能联接它们。</span><span class="sxs-lookup"><span data-stu-id="f2566-126">Because a here-string is one string, the lines in the here-string must be split before they can be joined.</span></span> <span data-ttu-id="f2566-127">您可以使用此方法重新加入已保存在以下字符串中的 XML 文件中的字符串：</span><span class="sxs-lookup"><span data-stu-id="f2566-127">You can use this method to rejoin the strings in an XML file that has been saved in a here-string:</span></span>

```powershell
$a = @'
a
b
c
'@

(-split $a) -join " "
a b c
```

## <a name="see-also"></a><span data-ttu-id="f2566-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f2566-128">SEE ALSO</span></span>

[<span data-ttu-id="f2566-129">about_Operators</span><span class="sxs-lookup"><span data-stu-id="f2566-129">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="f2566-130">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="f2566-130">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="f2566-131">about_Split</span><span class="sxs-lookup"><span data-stu-id="f2566-131">about_Split</span></span>](about_Split.md)
