---
description: 描述如何从 PowerShell 中的工作位置访问项。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_locations?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Locations
ms.openlocfilehash: 070b28dee62771fc7014a9a8aa6c1732c3f0b2cd
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2020
ms.locfileid: "93200598"
---
# <a name="about_locations"></a><span data-ttu-id="28d70-104">about_Locations</span><span class="sxs-lookup"><span data-stu-id="28d70-104">about_Locations</span></span>

## <a name="short-description"></a><span data-ttu-id="28d70-105">简短说明</span><span class="sxs-lookup"><span data-stu-id="28d70-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="28d70-106">描述如何从 PowerShell 中的工作位置访问项。</span><span class="sxs-lookup"><span data-stu-id="28d70-106">Describes how to access items from the working location in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="28d70-107">详细说明</span><span class="sxs-lookup"><span data-stu-id="28d70-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="28d70-108">当前工作位置是命令点的默认位置。</span><span class="sxs-lookup"><span data-stu-id="28d70-108">The current working location is the default location to which commands point.</span></span>
<span data-ttu-id="28d70-109">换句话说，如果不提供受命令影响的项或位置的显式路径，则这是 PowerShell 使用的位置。</span><span class="sxs-lookup"><span data-stu-id="28d70-109">In other words, this is the location that PowerShell uses if you do not supply an explicit path to the item or location that is affected by the command.</span></span> <span data-ttu-id="28d70-110">在大多数情况下，当前工作位置是通过 PowerShell FileSystem 提供程序访问的驱动器，在某些情况下是该驱动器上的目录。</span><span class="sxs-lookup"><span data-stu-id="28d70-110">In most cases, the current working location is a drive accessed through the PowerShell FileSystem provider and, in some cases, a directory on that drive.</span></span>
<span data-ttu-id="28d70-111">例如，你可以将当前工作位置设置为以下位置：</span><span class="sxs-lookup"><span data-stu-id="28d70-111">For example, you might set your current working location to the following location:</span></span>

```powershell
C:\Program Files\Windows PowerShell
```

<span data-ttu-id="28d70-112">因此，除非显式提供另一个路径，否则将从该位置处理所有命令。</span><span class="sxs-lookup"><span data-stu-id="28d70-112">As a result, all commands are processed from this location unless another path is explicitly provided.</span></span>

<span data-ttu-id="28d70-113">即使驱动器不是当前驱动器，PowerShell 也会保留每个驱动器的当前工作位置。</span><span class="sxs-lookup"><span data-stu-id="28d70-113">PowerShell maintains the current working location for each drive even when the drive is not the current drive.</span></span> <span data-ttu-id="28d70-114">这允许你通过只引用另一个位置的驱动器来访问当前工作位置的项。</span><span class="sxs-lookup"><span data-stu-id="28d70-114">This allows you to access items from the current working location by referring only to the drive of another location.</span></span>
<span data-ttu-id="28d70-115">例如，假设您的当前工作位置是 C： \\ Windows。</span><span class="sxs-lookup"><span data-stu-id="28d70-115">For example, suppose that your current working location is C:\\Windows.</span></span> <span data-ttu-id="28d70-116">现在，假设你使用以下命令将当前工作位置更改为 HKLM：驱动器：</span><span class="sxs-lookup"><span data-stu-id="28d70-116">Now, suppose you use the following command to change your current working location to the HKLM: drive:</span></span>

```powershell
Set-Location HKLM:
```

<span data-ttu-id="28d70-117">尽管当前位置现在是注册表驱动器，但仍可以 \\ 使用 c：驱动器仅访问 c： Windows 目录中的项，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="28d70-117">Although your current location is now the registry drive, you can still access items in the C:\\Windows directory simply by using the C: drive, as shown in the following example:</span></span>

```powershell
Get-ChildItem C:
```

<span data-ttu-id="28d70-118">PowerShell 会记住，当前该驱动器的工作位置是 Windows 目录，因此它将从该目录中检索项。</span><span class="sxs-lookup"><span data-stu-id="28d70-118">PowerShell remembers that your current working location for that drive is the Windows directory, so it retrieves items from that directory.</span></span> <span data-ttu-id="28d70-119">如果你运行以下命令，结果将相同：</span><span class="sxs-lookup"><span data-stu-id="28d70-119">The results would be the same if you ran the following command:</span></span>

```powershell
Get-ChildItem C:\Windows
```

<span data-ttu-id="28d70-120">在 PowerShell 中，可以使用 Get-Location 命令来确定当前工作位置，并且可以使用 Set-Location 命令设置当前工作位置。</span><span class="sxs-lookup"><span data-stu-id="28d70-120">In PowerShell, you can use the Get-Location command to determine the current working location, and you can use the Set-Location command to set the current working location.</span></span> <span data-ttu-id="28d70-121">例如，以下命令将当前工作位置设置为 C：驱动器的 Windows 目录：</span><span class="sxs-lookup"><span data-stu-id="28d70-121">For example, the following command sets the current working location to the Windows directory of the C: drive:</span></span>

```powershell
Set-Location c:\windows
```

<span data-ttu-id="28d70-122">设置当前工作位置之后，你仍可以通过在命令中包含驱动器名称 (后跟冒号) 来访问其他驱动器中的项，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="28d70-122">After you set the current working location, you can still access items from other drives simply by including the drive name (followed by a colon) in the command, as shown in the following example:</span></span>

```powershell
Get-ChildItem HKLM:\software
```

<span data-ttu-id="28d70-123">示例命令将检索注册表中 HKEY 本地计算机 hive 的软件容器中的项列表。</span><span class="sxs-lookup"><span data-stu-id="28d70-123">The example command retrieves a list of items in the Software container of the HKEY Local Machine hive in the registry.</span></span>

<span data-ttu-id="28d70-124">PowerShell 还允许使用特殊字符表示当前工作位置及其父位置。</span><span class="sxs-lookup"><span data-stu-id="28d70-124">PowerShell also allows you to use special characters to represent the current working location and its parent location.</span></span> <span data-ttu-id="28d70-125">若要表示当前工作位置，请使用单个句点。</span><span class="sxs-lookup"><span data-stu-id="28d70-125">To represent the current working location, use a single period.</span></span> <span data-ttu-id="28d70-126">若要表示当前工作位置的父级，请使用两个句点。</span><span class="sxs-lookup"><span data-stu-id="28d70-126">To represent the parent of the current working location, use two periods.</span></span> <span data-ttu-id="28d70-127">例如，下面指定了当前工作位置中的系统子目录：</span><span class="sxs-lookup"><span data-stu-id="28d70-127">For example, the following specifies the System subdirectory in the current working location:</span></span>

```powershell
Get-ChildItem .\system
```

<span data-ttu-id="28d70-128">如果当前工作位置为 C： \\ windows，则此命令将返回 c： windows 系统中所有项的 \\ 列表 \\ 。</span><span class="sxs-lookup"><span data-stu-id="28d70-128">If the current working location is C:\\Windows, this command returns a list of all the items in C:\\Windows\\System.</span></span> <span data-ttu-id="28d70-129">但是，如果使用两个句点，则使用当前工作目录的父目录，如下面的示例中所示：</span><span class="sxs-lookup"><span data-stu-id="28d70-129">However, if you use two periods, the parent directory of the current working directory is used, as shown in the following example:</span></span>

```powershell
Get-ChildItem ..\"program files"
```

<span data-ttu-id="28d70-130">在这种情况下，PowerShell 将两个句点视为 C：驱动器，因此该命令检索 C： Program Files 目录中的所有项 \\ 。</span><span class="sxs-lookup"><span data-stu-id="28d70-130">In this case, PowerShell treats the two periods as the C: drive, so the command retrieves all the items in the C:\\Program Files directory.</span></span>

<span data-ttu-id="28d70-131">以斜杠开头的路径标识来自当前驱动器的根目录的路径。</span><span class="sxs-lookup"><span data-stu-id="28d70-131">A path beginning with a slash identifies a path from the root of the current drive.</span></span> <span data-ttu-id="28d70-132">例如，如果当前工作位置是 C： \\ Program Files \\ PowerShell，则驱动器的根目录为 c。因此，以下命令列出了 C： Windows 目录中的所有项 \\ ：</span><span class="sxs-lookup"><span data-stu-id="28d70-132">For example, if your current working location is C:\\Program Files\\PowerShell, the root of your drive is C. Therefore, the following command lists all items in the C:\\Windows directory:</span></span>

```powershell
Get-ChildItem \windows
```

<span data-ttu-id="28d70-133">如果在提供容器或项的名称时未指定以驱动器名称、斜杠或句点开头的路径，则假定容器或项位于当前工作位置。</span><span class="sxs-lookup"><span data-stu-id="28d70-133">If you do not specify a path beginning with a drive name, slash, or period when supplying the name of a container or item, the container or item is assumed to be located in the current working location.</span></span> <span data-ttu-id="28d70-134">例如，如果您的当前工作位置是 C： \\ windows，则以下命令将返回 c： \\ windows 系统目录中的所有项 \\ ：</span><span class="sxs-lookup"><span data-stu-id="28d70-134">For example, if your current working location is C:\\Windows, the following command returns all the items in the C:\\Windows\\System directory:</span></span>

```powershell
Get-ChildItem system
```

<span data-ttu-id="28d70-135">如果指定文件名而不是目录名称，则 PowerShell 将返回有关该文件的详细信息， (假设该文件位于当前工作位置) 。</span><span class="sxs-lookup"><span data-stu-id="28d70-135">If you specify a file name rather than a directory name, PowerShell returns details about that file (assuming that file is located in the current working location).</span></span>

## <a name="see-also"></a><span data-ttu-id="28d70-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="28d70-136">SEE ALSO</span></span>

[<span data-ttu-id="28d70-137">Set-Location</span><span class="sxs-lookup"><span data-stu-id="28d70-137">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)

[<span data-ttu-id="28d70-138">about_Providers</span><span class="sxs-lookup"><span data-stu-id="28d70-138">about_Providers</span></span>](about_Providers.md)

[<span data-ttu-id="28d70-139">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="28d70-139">about_Path_Syntax</span></span>](about_Path_Syntax.md)
