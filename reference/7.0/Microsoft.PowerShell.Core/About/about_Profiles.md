---
description: 介绍如何创建和使用 PowerShell 配置文件。
keywords: powershell,cmdlet
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Profiles
ms.openlocfilehash: 3fb6a67e160281f60f20c187bf37c6920a506705
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/13/2020
ms.locfileid: "93199595"
---
# <a name="about-profiles"></a><span data-ttu-id="a1dbb-104">关于配置文件</span><span class="sxs-lookup"><span data-stu-id="a1dbb-104">About Profiles</span></span>

## <a name="short-description"></a><span data-ttu-id="a1dbb-105">简短说明</span><span class="sxs-lookup"><span data-stu-id="a1dbb-105">Short Description</span></span>
<span data-ttu-id="a1dbb-106">介绍如何创建和使用 PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-106">Describes how to create and use a PowerShell profile.</span></span>

## <a name="long-description"></a><span data-ttu-id="a1dbb-107">详细说明</span><span class="sxs-lookup"><span data-stu-id="a1dbb-107">Long Description</span></span>

<span data-ttu-id="a1dbb-108">可以创建 PowerShell 配置文件以自定义环境，并向启动的每个 PowerShell 会话中添加特定于会话的元素。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-108">You can create a PowerShell profile to customize your environment and to add session-specific elements to every PowerShell session that you start.</span></span>

<span data-ttu-id="a1dbb-109">PowerShell 配置文件是在 PowerShell 启动时运行的脚本。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-109">A PowerShell profile is a script that runs when PowerShell starts.</span></span> <span data-ttu-id="a1dbb-110">你可以使用配置文件作为登录脚本来自定义环境。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-110">You can use the profile as a logon script to customize the environment.</span></span> <span data-ttu-id="a1dbb-111">可以添加命令、别名、函数、变量、管理单元、模块和 PowerShell 驱动器。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-111">You can add commands, aliases, functions, variables, snap-ins, modules, and PowerShell drives.</span></span> <span data-ttu-id="a1dbb-112">你还可以将其他特定于会话的元素添加到你的配置文件中，以便它们可在每个会话中使用，而无需导入或重新创建它们。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-112">You can also add other session-specific elements to your profile so they are available in every session without having to import or re-create them.</span></span>

<span data-ttu-id="a1dbb-113">PowerShell 支持多个用户和主机程序配置文件。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-113">PowerShell supports several profiles for users and host programs.</span></span> <span data-ttu-id="a1dbb-114">但是，它不会为你创建配置文件。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-114">However, it does not create the profiles for you.</span></span> <span data-ttu-id="a1dbb-115">本主题介绍了配置文件，并介绍了如何在计算机上创建和维护配置文件。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-115">This topic describes the profiles, and it describes how to create and maintain profiles on your computer.</span></span>

<span data-ttu-id="a1dbb-116">它说明了如何使用 PowerShell 控制台的 **NoProfile** 参数 ( # A0) 在不使用任何配置文件的情况下启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-116">It explains how to use the **NoProfile** parameter of the PowerShell console (PowerShell.exe) to start PowerShell without any profiles.</span></span> <span data-ttu-id="a1dbb-117">而且，它还说明了 PowerShell 执行策略对配置文件的影响。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-117">And, it explains the effect of the PowerShell execution policy on profiles.</span></span>

## <a name="the-profile-files"></a><span data-ttu-id="a1dbb-118">配置文件</span><span class="sxs-lookup"><span data-stu-id="a1dbb-118">The Profile Files</span></span>

<span data-ttu-id="a1dbb-119">PowerShell 支持多个配置文件。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-119">PowerShell supports several profile files.</span></span> <span data-ttu-id="a1dbb-120">此外，PowerShell 主机程序还可以支持其自己的特定于主机的配置文件。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-120">Also, PowerShell host programs can support their own host-specific profiles.</span></span>

<span data-ttu-id="a1dbb-121">例如，PowerShell 控制台支持以下基本配置文件。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-121">For example, the PowerShell console supports the following basic profile files.</span></span> <span data-ttu-id="a1dbb-122">配置文件按优先级顺序列出。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-122">The profiles are listed in precedence order.</span></span> <span data-ttu-id="a1dbb-123">第一个配置文件的优先级最高。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-123">The first profile has the highest precedence.</span></span>

|<span data-ttu-id="a1dbb-124">说明</span><span class="sxs-lookup"><span data-stu-id="a1dbb-124">Description</span></span>               | <span data-ttu-id="a1dbb-125">路径</span><span class="sxs-lookup"><span data-stu-id="a1dbb-125">Path</span></span>                                          |
|--------------------------|-----------------------------------------------|
|<span data-ttu-id="a1dbb-126">所有用户，所有主机</span><span class="sxs-lookup"><span data-stu-id="a1dbb-126">All Users, All Hosts</span></span>      |<span data-ttu-id="a1dbb-127">$PSHOME \\Profile.ps1</span><span class="sxs-lookup"><span data-stu-id="a1dbb-127">$PSHOME\\Profile.ps1</span></span>                           |
|<span data-ttu-id="a1dbb-128">所有用户，当前主机</span><span class="sxs-lookup"><span data-stu-id="a1dbb-128">All Users, Current Host</span></span>   |<span data-ttu-id="a1dbb-129">$PSHOME \\Microsoft.PowerShell_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="a1dbb-129">$PSHOME\\Microsoft.PowerShell_profile.ps1</span></span>      |
|<span data-ttu-id="a1dbb-130">当前用户，所有主机</span><span class="sxs-lookup"><span data-stu-id="a1dbb-130">Current User, All Hosts</span></span>   |<span data-ttu-id="a1dbb-131">$Home \\ [My] 文档 \\ PowerShell \\Profile.ps1</span><span class="sxs-lookup"><span data-stu-id="a1dbb-131">$Home\\[My ]Documents\\PowerShell\\Profile.ps1</span></span> |
|<span data-ttu-id="a1dbb-132">当前用户、当前主机</span><span class="sxs-lookup"><span data-stu-id="a1dbb-132">Current user, Current Host</span></span>|<span data-ttu-id="a1dbb-133">$Home \\ [My] 文档 \\ PowerShell</span><span class="sxs-lookup"><span data-stu-id="a1dbb-133">$Home\\[My ]Documents\\PowerShell</span></span>\\<br><span data-ttu-id="a1dbb-134">Microsoft.PowerShell_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="a1dbb-134">Microsoft.PowerShell_profile.ps1</span></span> |

<span data-ttu-id="a1dbb-135">配置文件路径包含以下变量：</span><span class="sxs-lookup"><span data-stu-id="a1dbb-135">The profile paths include the following variables:</span></span>

- <span data-ttu-id="a1dbb-136">`$PSHOME`变量，存储 PowerShell 的安装目录</span><span class="sxs-lookup"><span data-stu-id="a1dbb-136">The `$PSHOME` variable, which stores the installation directory for PowerShell</span></span>
- <span data-ttu-id="a1dbb-137">`$Home`变量，用于存储当前用户的主目录</span><span class="sxs-lookup"><span data-stu-id="a1dbb-137">The `$Home` variable, which stores the current user's home directory</span></span>

<span data-ttu-id="a1dbb-138">此外，托管 PowerShell 的其他程序可以支持其自己的配置文件。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-138">In addition, other programs that host PowerShell can support their own profiles.</span></span> <span data-ttu-id="a1dbb-139">例如，Visual Studio Code 支持以下特定于主机的配置文件。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-139">For example, Visual Studio Code supports the following host-specific profiles.</span></span>

|<span data-ttu-id="a1dbb-140">说明</span><span class="sxs-lookup"><span data-stu-id="a1dbb-140">Description</span></span>               | <span data-ttu-id="a1dbb-141">路径</span><span class="sxs-lookup"><span data-stu-id="a1dbb-141">Path</span></span>                                     |
|--------------------------|------------------------------------------|
|<span data-ttu-id="a1dbb-142">所有用户，当前主机</span><span class="sxs-lookup"><span data-stu-id="a1dbb-142">All users, Current Host</span></span>   |<span data-ttu-id="a1dbb-143">$PSHOME \\Microsoft.VSCode_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="a1dbb-143">$PSHOME\\Microsoft.VSCode_profile.ps1</span></span>|
|<span data-ttu-id="a1dbb-144">当前用户、当前主机</span><span class="sxs-lookup"><span data-stu-id="a1dbb-144">Current user, Current Host</span></span>|<span data-ttu-id="a1dbb-145">$Home \\ [My] 文档 \\ PowerShell</span><span class="sxs-lookup"><span data-stu-id="a1dbb-145">$Home\\[My ]Documents\\PowerShell</span></span>\\<br><span data-ttu-id="a1dbb-146">Microsoft.VSCode_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="a1dbb-146">Microsoft.VSCode_profile.ps1</span></span>|

<span data-ttu-id="a1dbb-147">在 PowerShell 帮助中，"CurrentUser，Current Host" 配置文件是最常称为 "你的 PowerShell 配置文件" 的配置文件。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-147">In PowerShell Help, the "CurrentUser, Current Host" profile is the profile most often referred to as "your PowerShell profile".</span></span>

## <a name="the-profile-variable"></a><span data-ttu-id="a1dbb-148">$PROFILE 变量</span><span class="sxs-lookup"><span data-stu-id="a1dbb-148">The $PROFILE variable</span></span>

<span data-ttu-id="a1dbb-149">`$PROFILE`自动变量存储当前会话中可用的 PowerShell 配置文件的路径。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-149">The `$PROFILE` automatic variable stores the paths to the PowerShell profiles that are available in the current session.</span></span>

<span data-ttu-id="a1dbb-150">若要查看配置文件路径，请显示变量的值 `$PROFILE` 。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-150">To view a profile path, display the value of the `$PROFILE` variable.</span></span> <span data-ttu-id="a1dbb-151">你还可以使用 `$PROFILE` 命令中的变量来表示路径。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-151">You can also use the `$PROFILE` variable in a command to represent a path.</span></span>

<span data-ttu-id="a1dbb-152">`$PROFILE`变量存储 "当前用户，当前主机" 配置文件的路径。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-152">The `$PROFILE` variable stores the path to the "Current User, Current Host" profile.</span></span> <span data-ttu-id="a1dbb-153">其他配置文件保存在变量的 "注意" 属性中 `$PROFILE` 。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-153">The other profiles are saved in note properties of the `$PROFILE` variable.</span></span>

<span data-ttu-id="a1dbb-154">例如，在 `$PROFILE` Windows PowerShell 控制台中，变量具有以下值。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-154">For example, the `$PROFILE` variable has the following values in the Windows PowerShell console.</span></span>

|<span data-ttu-id="a1dbb-155">说明</span><span class="sxs-lookup"><span data-stu-id="a1dbb-155">Description</span></span>                |<span data-ttu-id="a1dbb-156">名称</span><span class="sxs-lookup"><span data-stu-id="a1dbb-156">Name</span></span>                              |
|---------------------------|----------------------------------|
|<span data-ttu-id="a1dbb-157">当前用户、当前主机</span><span class="sxs-lookup"><span data-stu-id="a1dbb-157">Current User, Current Host</span></span> |`$PROFILE`                        |
|<span data-ttu-id="a1dbb-158">当前用户、当前主机</span><span class="sxs-lookup"><span data-stu-id="a1dbb-158">Current User, Current Host</span></span> |`$PROFILE.CurrentUserCurrentHost` |
|<span data-ttu-id="a1dbb-159">当前用户，所有主机</span><span class="sxs-lookup"><span data-stu-id="a1dbb-159">Current User, All Hosts</span></span>    |`$PROFILE.CurrentUserAllHosts`    |
|<span data-ttu-id="a1dbb-160">所有用户，当前主机</span><span class="sxs-lookup"><span data-stu-id="a1dbb-160">All Users, Current Host</span></span>    |`$PROFILE.AllUsersCurrentHost`    |
|<span data-ttu-id="a1dbb-161">所有用户，所有主机</span><span class="sxs-lookup"><span data-stu-id="a1dbb-161">All Users, All Hosts</span></span>       |`$PROFILE.AllUsersAllHosts`       |

<span data-ttu-id="a1dbb-162">由于变量的值会 `$PROFILE` 随每个用户和每个主机应用程序更改，因此请确保在使用的每个 PowerShell 主机应用程序中显示配置文件变量的值。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-162">Because the values of the `$PROFILE` variable change for each user and in each host application, ensure that you display the values of the profile variables in each PowerShell host application that you use.</span></span>

<span data-ttu-id="a1dbb-163">若要查看变量的当前值 `$PROFILE` ，请键入：</span><span class="sxs-lookup"><span data-stu-id="a1dbb-163">To see the current values of the `$PROFILE` variable, type:</span></span>

```powershell
$PROFILE | Get-Member -Type NoteProperty
```

<span data-ttu-id="a1dbb-164">可以 `$PROFILE` 在许多命令中使用该变量。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-164">You can use the `$PROFILE` variable in many commands.</span></span> <span data-ttu-id="a1dbb-165">例如，以下命令将在记事本中打开 "当前用户、当前主机" 配置文件：</span><span class="sxs-lookup"><span data-stu-id="a1dbb-165">For example, the following command opens the "Current User, Current Host" profile in Notepad:</span></span>

```powershell
notepad $PROFILE
```

<span data-ttu-id="a1dbb-166">以下命令确定是否已在本地计算机上创建 "所有用户，所有主机" 配置文件：</span><span class="sxs-lookup"><span data-stu-id="a1dbb-166">The following command determines whether an "All Users, All Hosts" profile has been created on the local computer:</span></span>

```powershell
Test-Path -Path $PROFILE.AllUsersAllHosts
```

## <a name="how-to-create-a-profile"></a><span data-ttu-id="a1dbb-167">如何创建配置文件</span><span class="sxs-lookup"><span data-stu-id="a1dbb-167">How to create a profile</span></span>

<span data-ttu-id="a1dbb-168">若要创建 PowerShell 配置文件，请使用以下命令格式：</span><span class="sxs-lookup"><span data-stu-id="a1dbb-168">To create a PowerShell profile, use the following command format:</span></span>

```powershell
if (!(Test-Path -Path <profile-name>)) {
  New-Item -ItemType File -Path <profile-name> -Force
}
```

<span data-ttu-id="a1dbb-169">例如，若要在当前 PowerShell 主机应用程序中创建当前用户的配置文件，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="a1dbb-169">For example, to create a profile for the current user in the current PowerShell host application, use the following command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE)) {
  New-Item -ItemType File -Path $PROFILE -Force
}
```

<span data-ttu-id="a1dbb-170">在此命令中， `If` 语句阻止你覆盖现有的配置文件。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-170">In this command, the `If` statement prevents you from overwriting an existing profile.</span></span> <span data-ttu-id="a1dbb-171">将占位符的值替换 \<profile-path\> 为要创建的配置文件的路径。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-171">Replace the value of the \<profile-path\> placeholder with the path to the profile file that you want to create.</span></span>

> [!NOTE]
> <span data-ttu-id="a1dbb-172">若要在 Windows Vista 和更高版本的 Windows 中创建 "所有用户" 配置文件，请以 "以 **管理员身份运行** " 选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-172">To create "All Users" profiles in Windows Vista and later versions of Windows, start PowerShell with the **Run as administrator** option.</span></span>

## <a name="how-to-edit-a-profile"></a><span data-ttu-id="a1dbb-173">如何编辑配置文件</span><span class="sxs-lookup"><span data-stu-id="a1dbb-173">How to edit a profile</span></span>

<span data-ttu-id="a1dbb-174">可以在文本编辑器（例如记事本）中打开任何 PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-174">You can open any PowerShell profile in a text editor, such as Notepad.</span></span>

<span data-ttu-id="a1dbb-175">若要在 "记事本" 中打开当前 PowerShell 主机应用程序中当前用户的配置文件，请键入：</span><span class="sxs-lookup"><span data-stu-id="a1dbb-175">To open the profile of the current user in the current PowerShell host application in Notepad, type:</span></span>

```powershell
notepad $PROFILE
```

<span data-ttu-id="a1dbb-176">若要打开其他配置文件，请指定配置文件名称。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-176">To open other profiles, specify the profile name.</span></span> <span data-ttu-id="a1dbb-177">例如，若要打开所有主机应用程序的所有用户的配置文件，请键入：</span><span class="sxs-lookup"><span data-stu-id="a1dbb-177">For example, to open the profile for all the users of all the host applications, type:</span></span>

```powershell
notepad $PROFILE.AllUsersAllHosts
```

<span data-ttu-id="a1dbb-178">若要应用更改，请保存配置文件，然后重新启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-178">To apply the changes, save the profile file, and then restart PowerShell.</span></span>

## <a name="how-to-choose-a-profile"></a><span data-ttu-id="a1dbb-179">如何选择配置文件</span><span class="sxs-lookup"><span data-stu-id="a1dbb-179">How to choose a profile</span></span>

<span data-ttu-id="a1dbb-180">如果使用多个主机应用程序，请将在所有主机应用程序中使用的项放入 `$PROFILE.CurrentUserAllHosts` 配置文件中。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-180">If you use multiple host applications, put the items that you use in all the host applications into your `$PROFILE.CurrentUserAllHosts` profile.</span></span> <span data-ttu-id="a1dbb-181">将特定于宿主应用程序的项（如用于设置宿主应用程序的背景色的命令）放置在特定于该宿主应用程序的配置文件中。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-181">Put items that are specific to a host application, such as a command that sets the background color for a host application, in a profile that is specific to that host application.</span></span>

<span data-ttu-id="a1dbb-182">如果你是为多个用户自定义 PowerShell 的管理员，请遵循以下准则：</span><span class="sxs-lookup"><span data-stu-id="a1dbb-182">If you are an administrator who is customizing PowerShell for many users, follow these guidelines:</span></span>

- <span data-ttu-id="a1dbb-183">将常见项存储在 `$PROFILE.AllUsersAllHosts` 配置文件中</span><span class="sxs-lookup"><span data-stu-id="a1dbb-183">Store the common items in the `$PROFILE.AllUsersAllHosts` profile</span></span>
- <span data-ttu-id="a1dbb-184">在 `$PROFILE.AllUsersCurrentHost` 特定于宿主应用程序的配置文件中存储特定于宿主应用程序的项</span><span class="sxs-lookup"><span data-stu-id="a1dbb-184">Store items that are specific to a host application in `$PROFILE.AllUsersCurrentHost` profiles that are specific to the host application</span></span>
- <span data-ttu-id="a1dbb-185">为特定用户存储特定于用户的配置文件的项</span><span class="sxs-lookup"><span data-stu-id="a1dbb-185">Store items for particular users in the user-specific profiles</span></span>

<span data-ttu-id="a1dbb-186">务必查看主机应用程序文档，了解 PowerShell 配置文件的任何特殊实现。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-186">Be sure to check the host application documentation for any special implementation of PowerShell profiles.</span></span>

## <a name="how-to-use-a-profile"></a><span data-ttu-id="a1dbb-187">如何使用配置文件</span><span class="sxs-lookup"><span data-stu-id="a1dbb-187">How to use a profile</span></span>

<span data-ttu-id="a1dbb-188">在 PowerShell 中创建的许多项和运行的大多数命令只会影响当前会话。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-188">Many of the items that you create in PowerShell and most commands that you run affect only the current session.</span></span> <span data-ttu-id="a1dbb-189">结束会话时，将删除这些项。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-189">When you end the session, the items are deleted.</span></span>

<span data-ttu-id="a1dbb-190">特定于会话的命令和项包括变量、首选项变量、别名、函数、命令 (除了 [set-executionpolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)) 之外，还包括添加到会话中的 PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-190">The session-specific commands and items include variables, preference variables, aliases, functions, commands (except for [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)), and PowerShell modules that you add to the session.</span></span>

<span data-ttu-id="a1dbb-191">若要保存这些项目并使其在将来的所有会话中可用，请将它们添加到 PowerShell 配置文件中。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-191">To save these items and make them available in all future sessions, add them to a PowerShell profile.</span></span>

<span data-ttu-id="a1dbb-192">配置文件的另一个常见用途是保存常用的函数、别名和变量。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-192">Another common use for profiles is to save frequently-used functions, aliases, and variables.</span></span> <span data-ttu-id="a1dbb-193">在配置文件中保存项时，可以在任何适用的会话中使用它们，而无需重新创建它们。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-193">When you save the items in a profile, you can use them in any applicable session without recreating them.</span></span>

## <a name="how-to-start-a-profile"></a><span data-ttu-id="a1dbb-194">如何启动配置文件</span><span class="sxs-lookup"><span data-stu-id="a1dbb-194">How to start a profile</span></span>

<span data-ttu-id="a1dbb-195">打开配置文件时，它是空白的。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-195">When you open the profile file, it is blank.</span></span> <span data-ttu-id="a1dbb-196">不过，你可以使用经常使用的变量、别名和命令来填充它。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-196">However, you can fill it with the variables, aliases, and commands that you use frequently.</span></span>

<span data-ttu-id="a1dbb-197">下面是几个入门建议。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-197">Here are a few suggestions to get you started.</span></span>

### <a name="add-commands-that-make-it-easy-to-open-your-profile"></a><span data-ttu-id="a1dbb-198">添加使你可以轻松地打开配置文件的命令</span><span class="sxs-lookup"><span data-stu-id="a1dbb-198">Add commands that make it easy to open your profile</span></span>

<span data-ttu-id="a1dbb-199">如果你使用的配置文件不是 "当前用户"、"当前主机" 配置文件，则此方法特别有用。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-199">This is especially useful if you use a profile other than the "Current User, Current Host" profile.</span></span> <span data-ttu-id="a1dbb-200">例如，添加以下命令：</span><span class="sxs-lookup"><span data-stu-id="a1dbb-200">For example, add the following command:</span></span>

```powershell
function Pro {notepad $PROFILE.CurrentUserAllHosts}
```

### <a name="add-a-function-that-lists-the-aliases-for-any-cmdlet"></a><span data-ttu-id="a1dbb-201">添加一个函数，该函数列出任何 cmdlet 的别名</span><span class="sxs-lookup"><span data-stu-id="a1dbb-201">Add a function that lists the aliases for any cmdlet</span></span>

```powershell
function Get-CmdletAlias ($cmdletname) {
  Get-Alias |
    Where-Object -FilterScript {$_.Definition -like "$cmdletname"} |
      Format-Table -Property Definition, Name -AutoSize
}
```

### <a name="customize-your-console"></a><span data-ttu-id="a1dbb-202">自定义控制台</span><span class="sxs-lookup"><span data-stu-id="a1dbb-202">Customize your console</span></span>

```powershell
function Color-Console {
  $Host.ui.rawui.backgroundcolor = "white"
  $Host.ui.rawui.foregroundcolor = "black"
  $hosttime = (Get-ChildItem -Path $PSHOME\PowerShell.exe).CreationTime
  $hostversion="$($Host.Version.Major)`.$($Host.Version.Minor)"
  $Host.UI.RawUI.WindowTitle = "PowerShell $hostversion ($hosttime)"
  Clear-Host
}
Color-Console
```

### <a name="add-a-customized-powershell-prompt"></a><span data-ttu-id="a1dbb-203">添加自定义 PowerShell 提示符</span><span class="sxs-lookup"><span data-stu-id="a1dbb-203">Add a customized PowerShell prompt</span></span>

```powershell
function Prompt
{
$env:COMPUTERNAME + "\" + (Get-Location) + "> "
}
```

<span data-ttu-id="a1dbb-204">有关 PowerShell 提示符的详细信息，请参阅 [about_Prompts](about_Prompts.md)。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-204">For more information about the PowerShell prompt, see [about_Prompts](about_Prompts.md).</span></span>

## <a name="the-noprofile-parameter"></a><span data-ttu-id="a1dbb-205">NoProfile 参数</span><span class="sxs-lookup"><span data-stu-id="a1dbb-205">The NoProfile parameter</span></span>

<span data-ttu-id="a1dbb-206">若要在不使用配置文件的情况下启动 PowerShell，请使用 **PowerShell.exe** 的 **NoProfile** 参数，该程序启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-206">To start PowerShell without profiles, use the **NoProfile** parameter of **PowerShell.exe** , the program that starts PowerShell.</span></span>

<span data-ttu-id="a1dbb-207">若要开始，请打开可启动 PowerShell 的程序，例如 Cmd.exe 或 PowerShell 本身。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-207">To begin, open a program that can start PowerShell, such as Cmd.exe or PowerShell itself.</span></span> <span data-ttu-id="a1dbb-208">你还可以使用 Windows 中的 "运行" 对话框。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-208">You can also use the Run dialog box in Windows.</span></span>

<span data-ttu-id="a1dbb-209">类型：</span><span class="sxs-lookup"><span data-stu-id="a1dbb-209">Type:</span></span>

```
PowerShell -NoProfile
```

<span data-ttu-id="a1dbb-210">有关 PowerShell.exe 的参数的完整列表，请键入：</span><span class="sxs-lookup"><span data-stu-id="a1dbb-210">For a complete list of the parameters of PowerShell.exe, type:</span></span>

```
PowerShell -?
```

## <a name="profiles-and-execution-policy"></a><span data-ttu-id="a1dbb-211">配置文件和执行策略</span><span class="sxs-lookup"><span data-stu-id="a1dbb-211">Profiles and Execution Policy</span></span>

<span data-ttu-id="a1dbb-212">PowerShell 执行策略确定是否可以运行脚本并加载配置文件（包括配置文件）。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-212">The PowerShell execution policy determines, in part, whether you can run scripts and load configuration files, including the profiles.</span></span> <span data-ttu-id="a1dbb-213">默认情况下， **限制** 执行策略为。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-213">The **Restricted** execution policy is the default.</span></span> <span data-ttu-id="a1dbb-214">它将阻止所有脚本运行，包括配置文件。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-214">It prevents all scripts from running, including the profiles.</span></span> <span data-ttu-id="a1dbb-215">如果你使用 "受限" 策略，则不会运行配置文件，并且不会应用其内容。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-215">If you use the "Restricted" policy, the profile does not run, and its contents are not applied.</span></span>

<span data-ttu-id="a1dbb-216">`Set-ExecutionPolicy`命令设置并更改您的执行策略。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-216">A `Set-ExecutionPolicy` command sets and changes your execution policy.</span></span> <span data-ttu-id="a1dbb-217">这是适用于所有 PowerShell 会话的几个命令之一，因为该值保存在注册表中。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-217">It is one of the few commands that applies in all PowerShell sessions because the value is saved in the registry.</span></span> <span data-ttu-id="a1dbb-218">不需要在打开控制台时进行设置，也不必 `Set-ExecutionPolicy` 在配置文件中存储命令。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-218">You do not have to set it when you open the console, and you do not have to store a `Set-ExecutionPolicy` command in your profile.</span></span>

## <a name="profiles-and-remote-sessions"></a><span data-ttu-id="a1dbb-219">配置文件和远程会话</span><span class="sxs-lookup"><span data-stu-id="a1dbb-219">Profiles and remote sessions</span></span>

<span data-ttu-id="a1dbb-220">PowerShell 配置文件不会自动在远程会话中运行，因此配置文件添加的命令不会出现在远程会话中。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-220">PowerShell profiles are not run automatically in remote sessions, so the commands that the profiles add are not present in the remote session.</span></span> <span data-ttu-id="a1dbb-221">此外，在 `$PROFILE` 远程会话中不填充自动变量。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-221">In addition, the `$PROFILE` automatic variable is not populated in remote sessions.</span></span>

<span data-ttu-id="a1dbb-222">若要在会话中运行配置文件，请使用 [命令调用](xref:Microsoft.PowerShell.Core.Invoke-Command) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-222">To run a profile in a session, use the [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command) cmdlet.</span></span>

<span data-ttu-id="a1dbb-223">例如，以下命令在的会话中从本地计算机运行 "当前用户，当前主机" 配置文件 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-223">For example, the following command runs the "Current user, Current Host" profile from the local computer in the session in `$s`.</span></span>

```powershell
Invoke-Command -Session $s -FilePath $PROFILE
```

<span data-ttu-id="a1dbb-224">以下命令在的会话中从远程计算机运行 "当前用户，当前主机" 配置文件 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-224">The following command runs the "Current user, Current Host" profile from the remote computer in the session in `$s`.</span></span> <span data-ttu-id="a1dbb-225">由于 `$PROFILE` 未填充变量，因此该命令使用配置文件的显式路径。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-225">Because the `$PROFILE` variable is not populated, the command uses the explicit path to the profile.</span></span> <span data-ttu-id="a1dbb-226">我们使用点采购运算符，使配置文件在远程计算机上的当前作用域中运行，而不是在其自身的作用域中执行。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-226">We use dot sourcing operator so that the profile executes in the current scope on the remote computer and not in its own scope.</span></span>

```powershell
Invoke-Command -Session $s -ScriptBlock {
  . "$HOME\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

<span data-ttu-id="a1dbb-227">运行此命令后，配置文件添加到会话中的命令在中可用 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="a1dbb-227">After running this command, the commands that the profile adds to the session are available in `$s`.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1dbb-228">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a1dbb-228">See Also</span></span>

[<span data-ttu-id="a1dbb-229">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="a1dbb-229">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="a1dbb-230">about_Functions</span><span class="sxs-lookup"><span data-stu-id="a1dbb-230">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="a1dbb-231">about_Prompts</span><span class="sxs-lookup"><span data-stu-id="a1dbb-231">about_Prompts</span></span>](about_Prompts.md)

[<span data-ttu-id="a1dbb-232">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="a1dbb-232">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="a1dbb-233">about_Signing</span><span class="sxs-lookup"><span data-stu-id="a1dbb-233">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="a1dbb-234">about_Remote</span><span class="sxs-lookup"><span data-stu-id="a1dbb-234">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="a1dbb-235">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="a1dbb-235">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="a1dbb-236">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="a1dbb-236">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)
