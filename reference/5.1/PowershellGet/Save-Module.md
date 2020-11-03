---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/save-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Module
ms.openlocfilehash: 1b5bba73a55f92b515113c8b895dcb8af3c52eb6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93198236"
---
# <span data-ttu-id="9bc36-103">Save-Module</span><span class="sxs-lookup"><span data-stu-id="9bc36-103">Save-Module</span></span>

## <span data-ttu-id="9bc36-104">摘要</span><span class="sxs-lookup"><span data-stu-id="9bc36-104">SYNOPSIS</span></span>
<span data-ttu-id="9bc36-105">将模块及其依赖项保存在本地计算机上，但不会安装该模块。</span><span class="sxs-lookup"><span data-stu-id="9bc36-105">Saves a module and its dependencies on the local computer but doesn't install the module.</span></span>

## <span data-ttu-id="9bc36-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9bc36-106">SYNTAX</span></span>

### <span data-ttu-id="9bc36-107">NameAndPathParameterSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="9bc36-107">NameAndPathParameterSet (Default)</span></span>

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense]  [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9bc36-108">NameAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="9bc36-108">NameAndLiteralPathParameterSet</span></span>

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense]  [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9bc36-109">InputObjectAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="9bc36-109">InputObjectAndLiteralPathParameterSet</span></span>

```
Save-Module [-InputObject] <PSObject[]> -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9bc36-110">InputObjectAndPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="9bc36-110">InputObjectAndPathParameterSet</span></span>

```
Save-Module [-InputObject] <PSObject[]> [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9bc36-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9bc36-111">DESCRIPTION</span></span>

<span data-ttu-id="9bc36-112">`Save-Module`Cmdlet 从已注册的存储库下载模块和任何依赖项。</span><span class="sxs-lookup"><span data-stu-id="9bc36-112">The `Save-Module` cmdlet downloads a module and any dependencies from a registered repository.</span></span>
<span data-ttu-id="9bc36-113">`Save-Module` 下载并保存模块的最新版本。</span><span class="sxs-lookup"><span data-stu-id="9bc36-113">`Save-Module` downloads and saves the most current version of a module.</span></span> <span data-ttu-id="9bc36-114">文件将保存到本地计算机上的指定路径。</span><span class="sxs-lookup"><span data-stu-id="9bc36-114">The files are saved to a specified path on the local computer.</span></span> <span data-ttu-id="9bc36-115">未安装该模块，但可以由管理员检查内容。</span><span class="sxs-lookup"><span data-stu-id="9bc36-115">The module isn't installed, but the contents are available for inspection by an administrator.</span></span> <span data-ttu-id="9bc36-116">然后，可以将保存的模块复制到 `$env:PSModulePath` 脱机计算机的相应位置。</span><span class="sxs-lookup"><span data-stu-id="9bc36-116">The saved module can then be copied into the appropriate `$env:PSModulePath` location of the offline machine.</span></span>

<span data-ttu-id="9bc36-117">`Get-PSRepository` 显示本地计算机的已注册存储库。</span><span class="sxs-lookup"><span data-stu-id="9bc36-117">`Get-PSRepository` displays the local computer's registered repositories.</span></span> <span data-ttu-id="9bc36-118">你可以使用 `Find-Module` cmdlet 来搜索已注册的存储库。</span><span class="sxs-lookup"><span data-stu-id="9bc36-118">You can use the `Find-Module` cmdlet to search registered repositories.</span></span>

## <span data-ttu-id="9bc36-119">示例</span><span class="sxs-lookup"><span data-stu-id="9bc36-119">EXAMPLES</span></span>

### <span data-ttu-id="9bc36-120">示例1：保存模块</span><span class="sxs-lookup"><span data-stu-id="9bc36-120">Example 1: Save a module</span></span>

<span data-ttu-id="9bc36-121">在此示例中，模块及其依赖项保存到本地计算机。</span><span class="sxs-lookup"><span data-stu-id="9bc36-121">In this example, a module and its dependencies are saved to the local computer.</span></span>

```powershell
Save-Module -Name PowerShellGet -Path C:\Test\Modules -Repository PSGallery
Get-ChildItem -Path C:\Test\Modules
```

```Output
    Directory: C:\Test\Modules

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     13:31                PackageManagement
d-----         7/1/2019     13:31                PowerShellGet
```

<span data-ttu-id="9bc36-122">`Save-Module` 使用 **Name** 参数指定模块 **PowerShellGet** 。</span><span class="sxs-lookup"><span data-stu-id="9bc36-122">`Save-Module` uses the **Name** parameter to specify the module, **PowerShellGet** .</span></span> <span data-ttu-id="9bc36-123">**Path** 参数指定下载的模块的存储位置。</span><span class="sxs-lookup"><span data-stu-id="9bc36-123">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="9bc36-124">**存储库** 参数指定已注册的存储库 **PSGallery** 。</span><span class="sxs-lookup"><span data-stu-id="9bc36-124">The **Repository** parameter specifies a registered repository, **PSGallery** .</span></span> <span data-ttu-id="9bc36-125">下载完成后，将 `Get-ChildItem` 显示存储文件的 **路径** 的内容。</span><span class="sxs-lookup"><span data-stu-id="9bc36-125">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

### <span data-ttu-id="9bc36-126">示例2：保存模块的特定版本</span><span class="sxs-lookup"><span data-stu-id="9bc36-126">Example 2: Save a specific version of a module</span></span>

<span data-ttu-id="9bc36-127">此示例演示如何使用参数（如 **MaximumVersion** ）或 **RequiredVersion** 来指定模块版本。</span><span class="sxs-lookup"><span data-stu-id="9bc36-127">This example shows how to use a parameter such as **MaximumVersion** , or **RequiredVersion** to specify a module version.</span></span>

```powershell
Save-Module -Name PowerShellGet -Path C:\Test\Modules -Repository PSGallery -MaximumVersion 2.1.0
Get-ChildItem -Path C:\Test\Modules\PowerShellGet\
```

```Output
    Directory: C:\Test\Modules\PowerShellGet

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     13:40                2.1.0
```

<span data-ttu-id="9bc36-128">`Save-Module` 使用 **Name** 参数指定模块 **PowerShellGet** 。</span><span class="sxs-lookup"><span data-stu-id="9bc36-128">`Save-Module` uses the **Name** parameter to specify the module, **PowerShellGet** .</span></span> <span data-ttu-id="9bc36-129">**Path** 参数指定下载的模块的存储位置。</span><span class="sxs-lookup"><span data-stu-id="9bc36-129">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="9bc36-130">**存储库** 参数指定已注册的存储库 **PSGallery** 。</span><span class="sxs-lookup"><span data-stu-id="9bc36-130">The **Repository** parameter specifies a registered repository, **PSGallery** .</span></span> <span data-ttu-id="9bc36-131">**MaximumVersion** 指定下载并保存版本 **2.1.0** 。</span><span class="sxs-lookup"><span data-stu-id="9bc36-131">**MaximumVersion** specifies that version **2.1.0** is downloaded and saved.</span></span> <span data-ttu-id="9bc36-132">下载完成后，将 `Get-ChildItem` 显示存储文件的 **路径** 的内容。</span><span class="sxs-lookup"><span data-stu-id="9bc36-132">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

### <span data-ttu-id="9bc36-133">示例3：查找并保存模块的特定版本</span><span class="sxs-lookup"><span data-stu-id="9bc36-133">Example 3: Find and save a specific version of a module</span></span>

<span data-ttu-id="9bc36-134">在此示例中，在存储库中找到所需的模块版本，并将其保存到本地计算机。</span><span class="sxs-lookup"><span data-stu-id="9bc36-134">In this example, a required module version is found in the repository and saved to the local computer.</span></span>

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery -RequiredVersion 1.6.5 |
  Save-Module -Path C:\Test\Modules
Get-ChildItem -Path C:\Test\Modules\PowerShellGet
```

```Output
    Directory: C:\Test\Modules\PowerShellGet

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     14:04                1.6.5
```

<span data-ttu-id="9bc36-135">`Find-Module` 使用 **Name** 参数指定模块 **PowerShellGet** 。</span><span class="sxs-lookup"><span data-stu-id="9bc36-135">`Find-Module` uses the **Name** parameter to specify the module, **PowerShellGet** .</span></span> <span data-ttu-id="9bc36-136">**存储库** 参数指定已注册的存储库 **PSGallery** 。</span><span class="sxs-lookup"><span data-stu-id="9bc36-136">The **Repository** parameter specifies a registered repository, **PSGallery** .</span></span> <span data-ttu-id="9bc36-137">**RequiredVersion** 指定版本 **1.6.5** 。</span><span class="sxs-lookup"><span data-stu-id="9bc36-137">**RequiredVersion** specifies version **1.6.5** .</span></span>

<span data-ttu-id="9bc36-138">将对象向下发送到 `Save-Module` 。</span><span class="sxs-lookup"><span data-stu-id="9bc36-138">The object is sent down the pipeline to `Save-Module`.</span></span> <span data-ttu-id="9bc36-139">**Path** 参数指定下载的模块的存储位置。</span><span class="sxs-lookup"><span data-stu-id="9bc36-139">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="9bc36-140">下载完成后，将 `Get-ChildItem` 显示存储文件的 **路径** 的内容。</span><span class="sxs-lookup"><span data-stu-id="9bc36-140">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

## <span data-ttu-id="9bc36-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9bc36-141">PARAMETERS</span></span>

### <span data-ttu-id="9bc36-142">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="9bc36-142">-AcceptLicense</span></span>

<span data-ttu-id="9bc36-143">如果包需要许可协议，则自动接受该协议。</span><span class="sxs-lookup"><span data-stu-id="9bc36-143">Automatically accept the license agreement if the package requires it.</span></span>

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

### <span data-ttu-id="9bc36-144">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="9bc36-144">-AllowPrerelease</span></span>

<span data-ttu-id="9bc36-145">允许您保存标记为预发行的模块。</span><span class="sxs-lookup"><span data-stu-id="9bc36-145">Allows you to save a module marked as a prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9bc36-146">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9bc36-146">-Confirm</span></span>

<span data-ttu-id="9bc36-147">提示你在运行之前进行确认 `Save-Module` 。</span><span class="sxs-lookup"><span data-stu-id="9bc36-147">Prompts you for confirmation before running the `Save-Module`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9bc36-148">-Credential</span><span class="sxs-lookup"><span data-stu-id="9bc36-148">-Credential</span></span>

<span data-ttu-id="9bc36-149">指定有权保存模块的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="9bc36-149">Specifies a user account that has rights to save a module.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9bc36-150">-Force</span><span class="sxs-lookup"><span data-stu-id="9bc36-150">-Force</span></span>

<span data-ttu-id="9bc36-151">强制 `Save-Module` 运行而不请求用户确认。</span><span class="sxs-lookup"><span data-stu-id="9bc36-151">Forces `Save-Module` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="9bc36-152">-InputObject</span><span class="sxs-lookup"><span data-stu-id="9bc36-152">-InputObject</span></span>

<span data-ttu-id="9bc36-153">接受 **PSRepositoryItemInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="9bc36-153">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="9bc36-154">例如，输出 `Find-Module` 到变量，并将该变量用作 **InputObject** 参数。</span><span class="sxs-lookup"><span data-stu-id="9bc36-154">For example, output `Find-Module` to a variable and use that variable as the **InputObject** argument.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObjectAndLiteralPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9bc36-155">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9bc36-155">-LiteralPath</span></span>

<span data-ttu-id="9bc36-156">指定一个或多个位置的路径。</span><span class="sxs-lookup"><span data-stu-id="9bc36-156">Specifies a path to one or more locations.</span></span> <span data-ttu-id="9bc36-157">**LiteralPath** 参数的值完全按输入方式使用。</span><span class="sxs-lookup"><span data-stu-id="9bc36-157">The value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="9bc36-158">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="9bc36-158">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="9bc36-159">如果路径包含转义符，请将其括在单引号内。</span><span class="sxs-lookup"><span data-stu-id="9bc36-159">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="9bc36-160">PowerShell 不会将括在单引号中的任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="9bc36-160">PowerShell does not interpret any characters enclosed in single quotation marks as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndLiteralPathParameterSet, InputObjectAndLiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9bc36-161">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="9bc36-161">-MaximumVersion</span></span>

<span data-ttu-id="9bc36-162">指定要保存的模块的最大或最新版本。</span><span class="sxs-lookup"><span data-stu-id="9bc36-162">Specifies the maximum, or newest, version of the module to save.</span></span> <span data-ttu-id="9bc36-163">不能在同一命令中使用 **MaximumVersion** 和 **RequiredVersion** 参数。</span><span class="sxs-lookup"><span data-stu-id="9bc36-163">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9bc36-164">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="9bc36-164">-MinimumVersion</span></span>

<span data-ttu-id="9bc36-165">指定要保存的单个模块的最低版本。</span><span class="sxs-lookup"><span data-stu-id="9bc36-165">Specifies the minimum version of a single module to save.</span></span> <span data-ttu-id="9bc36-166">如果尝试安装多个模块，则无法添加此参数。</span><span class="sxs-lookup"><span data-stu-id="9bc36-166">You cannot add this parameter if you are attempting to install multiple modules.</span></span> <span data-ttu-id="9bc36-167">不能在同一命令中使用 **MinimumVersion** 和 **RequiredVersion** 参数。</span><span class="sxs-lookup"><span data-stu-id="9bc36-167">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9bc36-168">-Name</span><span class="sxs-lookup"><span data-stu-id="9bc36-168">-Name</span></span>

<span data-ttu-id="9bc36-169">指定要保存的模块的名称数组。</span><span class="sxs-lookup"><span data-stu-id="9bc36-169">Specifies an array of names of modules to save.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9bc36-170">-Path</span><span class="sxs-lookup"><span data-stu-id="9bc36-170">-Path</span></span>

<span data-ttu-id="9bc36-171">指定本地计算机上存储已保存模块的位置。</span><span class="sxs-lookup"><span data-stu-id="9bc36-171">Specifies the location on the local computer to store a saved module.</span></span> <span data-ttu-id="9bc36-172">接受通配符。</span><span class="sxs-lookup"><span data-stu-id="9bc36-172">Accepts wildcard characters.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="9bc36-173">-Proxy</span><span class="sxs-lookup"><span data-stu-id="9bc36-173">-Proxy</span></span>

<span data-ttu-id="9bc36-174">为请求指定代理服务器，而不是直接连接到 internet 资源。</span><span class="sxs-lookup"><span data-stu-id="9bc36-174">Specifies a proxy server for the request, rather than connecting directly to the internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9bc36-175">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="9bc36-175">-ProxyCredential</span></span>

<span data-ttu-id="9bc36-176">指定有权使用由 **Proxy** 参数指定的代理服务器的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="9bc36-176">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9bc36-177">-Repository</span><span class="sxs-lookup"><span data-stu-id="9bc36-177">-Repository</span></span>

<span data-ttu-id="9bc36-178">指定已通过运行注册的存储库的友好名称 `Register-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="9bc36-178">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="9bc36-179">用于 `Get-PSRepository` 显示已注册的存储库。</span><span class="sxs-lookup"><span data-stu-id="9bc36-179">Use `Get-PSRepository` to display registered repositories.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9bc36-180">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="9bc36-180">-RequiredVersion</span></span>

<span data-ttu-id="9bc36-181">指定要保存的模块的确切版本号。</span><span class="sxs-lookup"><span data-stu-id="9bc36-181">Specifies the exact version number of the module to save.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9bc36-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9bc36-182">-WhatIf</span></span>

<span data-ttu-id="9bc36-183">显示运行时将发生的情况 `Save-Module` 。</span><span class="sxs-lookup"><span data-stu-id="9bc36-183">Shows what would happen if the `Save-Module` runs.</span></span> <span data-ttu-id="9bc36-184">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="9bc36-184">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9bc36-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9bc36-185">CommonParameters</span></span>

<span data-ttu-id="9bc36-186">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9bc36-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9bc36-187">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="9bc36-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9bc36-188">输入</span><span class="sxs-lookup"><span data-stu-id="9bc36-188">INPUTS</span></span>

## <span data-ttu-id="9bc36-189">输出</span><span class="sxs-lookup"><span data-stu-id="9bc36-189">OUTPUTS</span></span>

## <span data-ttu-id="9bc36-190">注释</span><span class="sxs-lookup"><span data-stu-id="9bc36-190">NOTES</span></span>

## <span data-ttu-id="9bc36-191">相关链接</span><span class="sxs-lookup"><span data-stu-id="9bc36-191">RELATED LINKS</span></span>