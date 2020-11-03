---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-authenticodesignature?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-AuthenticodeSignature
ms.openlocfilehash: 4ec4261326e43b2f811d201bf45e6854b4f478ea
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "93197982"
---
# <span data-ttu-id="977af-103">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="977af-103">Set-AuthenticodeSignature</span></span>

## <span data-ttu-id="977af-104">摘要</span><span class="sxs-lookup"><span data-stu-id="977af-104">SYNOPSIS</span></span>
<span data-ttu-id="977af-105">将 [Authenticode](/windows-hardware/drivers/install/authenticode) 签名添加到 PowerShell 脚本或其他文件中。</span><span class="sxs-lookup"><span data-stu-id="977af-105">Adds an [Authenticode](/windows-hardware/drivers/install/authenticode) signature to a PowerShell script or other file.</span></span>

## <span data-ttu-id="977af-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="977af-106">SYNTAX</span></span>

### <span data-ttu-id="977af-107">ByPath（默认值）</span><span class="sxs-lookup"><span data-stu-id="977af-107">ByPath (Default)</span></span>

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] [-FilePath] <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="977af-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="977af-108">ByLiteralPath</span></span>

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -LiteralPath <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="977af-109">ByContent</span><span class="sxs-lookup"><span data-stu-id="977af-109">ByContent</span></span>

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -SourcePathOrExtension <String[]>
 -Content <Byte[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="977af-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="977af-110">DESCRIPTION</span></span>

<span data-ttu-id="977af-111">`Set-AuthenticodeSignature`Cmdlet 将验证码签名添加到支持主题界面包 (SIP) 的任何文件。</span><span class="sxs-lookup"><span data-stu-id="977af-111">The `Set-AuthenticodeSignature` cmdlet adds an Authenticode signature to any file that supports Subject Interface Package (SIP).</span></span>

<span data-ttu-id="977af-112">在 PowerShell 脚本文件中，该签名采用文本块的形式，它指示在脚本中执行的说明的结束。</span><span class="sxs-lookup"><span data-stu-id="977af-112">In a PowerShell script file, the signature takes the form of a block of text that indicates the end of the instructions that are executed in the script.</span></span> <span data-ttu-id="977af-113">如果在此 cmdlet 运行时文件中有签名，则该签名被删除。</span><span class="sxs-lookup"><span data-stu-id="977af-113">If there is a signature in the file when this cmdlet runs, that signature is removed.</span></span>

## <span data-ttu-id="977af-114">示例</span><span class="sxs-lookup"><span data-stu-id="977af-114">EXAMPLES</span></span>

### <span data-ttu-id="977af-115">示例 1-使用本地证书存储中的证书对脚本进行签名</span><span class="sxs-lookup"><span data-stu-id="977af-115">Example 1 - Sign a script using a certificate from the local certificate store</span></span>

<span data-ttu-id="977af-116">这些命令从 PowerShell 证书提供程序检索代码签名证书，并使用它对 PowerShell 脚本进行签名。</span><span class="sxs-lookup"><span data-stu-id="977af-116">These commands retrieve a code-signing certificate from the PowerShell certificate provider and use it to sign a PowerShell script.</span></span>

```powershell
$cert=Get-ChildItem -Path Cert:\CurrentUser\My -CodeSigningCert
Set-AuthenticodeSignature -FilePath PsTestInternet2.ps1 -Certificate $cert
```

<span data-ttu-id="977af-117">第一个命令使用 `Get-ChildItem` cmdlet 和 PowerShell 证书提供程序来获取 `Cert:\CurrentUser\My` 证书存储区中的证书。</span><span class="sxs-lookup"><span data-stu-id="977af-117">The first command uses the `Get-ChildItem` cmdlet and the PowerShell certificate provider to get the certificates in the `Cert:\CurrentUser\My` subdirectory of the certificate store.</span></span> <span data-ttu-id="977af-118">`Cert:`驱动器是由证书提供程序公开的驱动器。</span><span class="sxs-lookup"><span data-stu-id="977af-118">The `Cert:` drive is the drive exposed by the certificate provider.</span></span> <span data-ttu-id="977af-119">仅证书提供程序支持的 **CodeSigningCert** 参数将检索到的证书限制为具有代码签名颁发机构的证书。</span><span class="sxs-lookup"><span data-stu-id="977af-119">The **CodeSigningCert** parameter, which is supported only by the certificate provider, limits the certificates retrieved to those with code-signing authority.</span></span> <span data-ttu-id="977af-120">该命令将结果存储在 `$cert` 变量中。</span><span class="sxs-lookup"><span data-stu-id="977af-120">The command stores the result in the `$cert` variable.</span></span>

<span data-ttu-id="977af-121">第二个命令使用 `Set-AuthenticodeSignature` cmdlet 对脚本进行签名 `PSTestInternet2.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="977af-121">The second command uses the `Set-AuthenticodeSignature` cmdlet to sign the `PSTestInternet2.ps1` script.</span></span> <span data-ttu-id="977af-122">它使用 **FilePath** 参数来指定脚本的名称，并使用 **certificate** 参数来指定在变量中存储证书 `$cert` 。</span><span class="sxs-lookup"><span data-stu-id="977af-122">It uses the **FilePath** parameter to specify the name of the script and the **Certificate** parameter to specify that the certificate is stored in the `$cert` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="977af-123">使用 **CodeSigningCert** 参数 `Get-ChildItem` 只返回具有代码签名颁发机构并包含私钥的证书。</span><span class="sxs-lookup"><span data-stu-id="977af-123">Using the **CodeSigningCert** parameter with `Get-ChildItem` only returns certificates that have code-signing authority and contain a private key.</span></span> <span data-ttu-id="977af-124">如果没有私钥，则不能使用证书进行签名。</span><span class="sxs-lookup"><span data-stu-id="977af-124">If there is no private key, the certificates cannot be used for signing.</span></span>

### <span data-ttu-id="977af-125">示例 2-使用 PFX 文件中的证书对脚本进行签名</span><span class="sxs-lookup"><span data-stu-id="977af-125">Example 2 - Sign a script using a certificate from a PFX file</span></span>

<span data-ttu-id="977af-126">这些命令使用 `Get-PfxCertificate` cmdlet 加载代码签名证书。</span><span class="sxs-lookup"><span data-stu-id="977af-126">These commands use the `Get-PfxCertificate` cmdlet to load a code signing certificate.</span></span> <span data-ttu-id="977af-127">然后，使用它对 PowerShell 脚本进行签名。</span><span class="sxs-lookup"><span data-stu-id="977af-127">Then, use it to sign a PowerShell script.</span></span>

```powershell
$cert = Get-PfxCertificate -FilePath C:\Test\Mysign.pfx
Set-AuthenticodeSignature -FilePath ServerProps.ps1 -Certificate $cert
```

<span data-ttu-id="977af-128">第一个命令使用 `Get-PfxCertificate` cmdlet 将 C:\Test\MySign.pfx 证书加载到 `$cert` 变量中。</span><span class="sxs-lookup"><span data-stu-id="977af-128">The first command uses the `Get-PfxCertificate` cmdlet to load the C:\Test\MySign.pfx certificate into the `$cert` variable.</span></span>

<span data-ttu-id="977af-129">第二个命令使用 `Set-AuthenticodeSignature` 对脚本进行签名。</span><span class="sxs-lookup"><span data-stu-id="977af-129">The second command uses `Set-AuthenticodeSignature` to sign the script.</span></span> <span data-ttu-id="977af-130">的 **FilePath** 参数 `Set-AuthenticodeSignature` 指定要签名的脚本文件的路径， **Cert** 参数将 `$cert` 包含证书的变量传递到 `Set-AuthenticodeSignature` 。</span><span class="sxs-lookup"><span data-stu-id="977af-130">The **FilePath** parameter of `Set-AuthenticodeSignature` specifies the path to the script file being signed and the **Cert** parameter passes the `$cert` variable containing the certificate to `Set-AuthenticodeSignature`.</span></span>

<span data-ttu-id="977af-131">如果证书文件受密码保护，则 PowerShell 会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="977af-131">If the certificate file is password protected, PowerShell prompts you for the password.</span></span>

### <span data-ttu-id="977af-132">示例 3-添加包含根证书颁发机构的签名</span><span class="sxs-lookup"><span data-stu-id="977af-132">Example 3 - Add a signature that includes the root authority</span></span>

<span data-ttu-id="977af-133">此命令添加数字签名，它包括信任链中的根证书颁发机构，并由第三方时间戳服务器对其进行签名。</span><span class="sxs-lookup"><span data-stu-id="977af-133">This command adds a digital signature that includes the root authority in the trust chain, and it is signed by a third-party timestamp server.</span></span>

```powershell
Set-AuthenticodeSignature -FilePath c:\scripts\Remodel.ps1 -Certificate $cert -IncludeChain All -TimestampServer "http://timestamp.fabrikam.com/scripts/timstamper.dll"
```

<span data-ttu-id="977af-134">该命令使用 **FilePath** 参数来指定要签名的脚本，并使用 **Certificate** 参数来指定在变量中保存的证书 `$cert` 。</span><span class="sxs-lookup"><span data-stu-id="977af-134">The command uses the **FilePath** parameter to specify the script being signed and the **Certificate** parameter to specify the certificate that is saved in the `$cert` variable.</span></span> <span data-ttu-id="977af-135">它使用 **IncludeChain** 参数来包括信任链中的所有签名，包括根证书颁发机构。</span><span class="sxs-lookup"><span data-stu-id="977af-135">It uses the **IncludeChain** parameter to include all of the signatures in the trust chain, including the root authority.</span></span> <span data-ttu-id="977af-136">它还使用 **TimeStampServer** 参数将时间戳添加到签名。</span><span class="sxs-lookup"><span data-stu-id="977af-136">It also uses the **TimeStampServer** parameter to add a timestamp to the signature.</span></span>
<span data-ttu-id="977af-137">这会阻止脚本在证书过期时失败。</span><span class="sxs-lookup"><span data-stu-id="977af-137">This prevents the script from failing when the certificate expires.</span></span>

## <span data-ttu-id="977af-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="977af-138">PARAMETERS</span></span>

### <span data-ttu-id="977af-139">-Certificate</span><span class="sxs-lookup"><span data-stu-id="977af-139">-Certificate</span></span>

<span data-ttu-id="977af-140">指定将用来对脚本或文件进行签名的证书。</span><span class="sxs-lookup"><span data-stu-id="977af-140">Specifies the certificate that will be used to sign the script or file.</span></span> <span data-ttu-id="977af-141">输入存储对象的变量，该对象表示证书或获取证书的表达式。</span><span class="sxs-lookup"><span data-stu-id="977af-141">Enter a variable that stores an object representing the certificate or an expression that gets the certificate.</span></span>

<span data-ttu-id="977af-142">若要查找证书，请使用 `Get-PfxCertificate` 或使用 `Get-ChildItem` 证书驱动器中的 cmdlet `Cert:` 。</span><span class="sxs-lookup"><span data-stu-id="977af-142">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate `Cert:` drive.</span></span> <span data-ttu-id="977af-143">如果证书无效或没有 `code-signing` 权限，则该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="977af-143">If the certificate is not valid or does not have `code-signing` authority, the command fails.</span></span>

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="977af-144">-FilePath</span><span class="sxs-lookup"><span data-stu-id="977af-144">-FilePath</span></span>

<span data-ttu-id="977af-145">指定正进行签名的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="977af-145">Specifies the path to a file that is being signed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="977af-146">-Force</span><span class="sxs-lookup"><span data-stu-id="977af-146">-Force</span></span>

<span data-ttu-id="977af-147">允许该 cmdlet 将签名追加到只读文件。</span><span class="sxs-lookup"><span data-stu-id="977af-147">Allows the cmdlet to append a signature to a read-only file.</span></span> <span data-ttu-id="977af-148">即使使用 **Force** 参数，该 cmdlet 也无法覆盖安全限制。</span><span class="sxs-lookup"><span data-stu-id="977af-148">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="977af-149">-HashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="977af-149">-HashAlgorithm</span></span>

<span data-ttu-id="977af-150">指定 Windows 用来计算文件的数字签名的哈希算法。</span><span class="sxs-lookup"><span data-stu-id="977af-150">Specifies the hashing algorithm that Windows uses to compute the digital signature for the file.</span></span>

<span data-ttu-id="977af-151">对于 PowerShell 3.0，默认值为 SHA256，它是 Windows 默认哈希算法。</span><span class="sxs-lookup"><span data-stu-id="977af-151">For PowerShell 3.0, the default is SHA256, which is the Windows default hashing algorithm.</span></span> <span data-ttu-id="977af-152">对于 PowerShell 2.0，默认值为 SHA1。</span><span class="sxs-lookup"><span data-stu-id="977af-152">For PowerShell 2.0, the default is SHA1.</span></span> <span data-ttu-id="977af-153">使用不同的哈希算法进行签名的文件可能无法在其他系统上识别。</span><span class="sxs-lookup"><span data-stu-id="977af-153">Files that are signed with a different hashing algorithm might not be recognized on other systems.</span></span> <span data-ttu-id="977af-154">支持哪些算法取决于操作系统的版本。</span><span class="sxs-lookup"><span data-stu-id="977af-154">Which algorithms are supported depends on the version of the operating system.</span></span>

<span data-ttu-id="977af-155">有关可能值的列表，请参阅 [HashAlgorithmName 结构](/dotnet/api/system.security.cryptography.hashalgorithmname?view=netframework-4.7.2#properties)。</span><span class="sxs-lookup"><span data-stu-id="977af-155">For a list of possible values, see [HashAlgorithmName Struct](/dotnet/api/system.security.cryptography.hashalgorithmname?view=netframework-4.7.2#properties).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SHA256
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="977af-156">-IncludeChain</span><span class="sxs-lookup"><span data-stu-id="977af-156">-IncludeChain</span></span>

<span data-ttu-id="977af-157">确定证书信任链中的哪些证书包含在数字签名中。</span><span class="sxs-lookup"><span data-stu-id="977af-157">Determines which certificates in the certificate trust chain are included in the digital signature.</span></span>
<span data-ttu-id="977af-158">默认值为 **NotRoot** 。</span><span class="sxs-lookup"><span data-stu-id="977af-158">**NotRoot** is the default.</span></span>

<span data-ttu-id="977af-159">有效值是：</span><span class="sxs-lookup"><span data-stu-id="977af-159">Valid values are:</span></span>

- <span data-ttu-id="977af-160">签名者：仅包括签名者的证书。</span><span class="sxs-lookup"><span data-stu-id="977af-160">Signer: Includes only the signer's certificate.</span></span>
- <span data-ttu-id="977af-161">NotRoot：包括证书链中的所有证书，根颁发机构除外。</span><span class="sxs-lookup"><span data-stu-id="977af-161">NotRoot: Includes all of the certificates in the certificate chain, except for the root authority.</span></span>
- <span data-ttu-id="977af-162">所有：包括证书链中的所有证书。</span><span class="sxs-lookup"><span data-stu-id="977af-162">All: Includes all the certificates in the certificate chain.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: NotRoot
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="977af-163">-TimestampServer</span><span class="sxs-lookup"><span data-stu-id="977af-163">-TimestampServer</span></span>

<span data-ttu-id="977af-164">使用指定的时间戳服务器将时间戳添加到签名。</span><span class="sxs-lookup"><span data-stu-id="977af-164">Uses the specified time stamp server to add a time stamp to the signature.</span></span> <span data-ttu-id="977af-165">以字符串的形式键入时间戳服务器的 URL。</span><span class="sxs-lookup"><span data-stu-id="977af-165">Type the URL of the time stamp server as a string.</span></span>

<span data-ttu-id="977af-166">时间戳表示将证书添加到文件的确切时间。</span><span class="sxs-lookup"><span data-stu-id="977af-166">The time stamp represents the exact time that the certificate was added to the file.</span></span> <span data-ttu-id="977af-167">如果证书过期，时间戳可阻止脚本失败，因为用户和程序可以验证在签名时证书有效。</span><span class="sxs-lookup"><span data-stu-id="977af-167">A time stamp prevents the script from failing if the certificate expires because users and programs can verify that the certificate was valid at the time of signing.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="977af-168">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="977af-168">-LiteralPath</span></span>

<span data-ttu-id="977af-169">指定正进行签名的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="977af-169">Specifies the path to a file that is being signed.</span></span> <span data-ttu-id="977af-170">与 **FilePath** 不同， **LiteralPath** 参数的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="977af-170">Unlike **FilePath** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="977af-171">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="977af-171">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="977af-172">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="977af-172">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="977af-173">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="977af-173">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="977af-174">-SourcePathOrExtension</span><span class="sxs-lookup"><span data-stu-id="977af-174">-SourcePathOrExtension</span></span>

<span data-ttu-id="977af-175">要添加数字签名的内容的文件或文件类型的路径。</span><span class="sxs-lookup"><span data-stu-id="977af-175">Path to the file or file type of the content for which the digital signature is added.</span></span> <span data-ttu-id="977af-176">此参数用于将文件内容作为字节数组传递的 **内容** 。</span><span class="sxs-lookup"><span data-stu-id="977af-176">This parameter is used with **Content** where file content is passed as a byte array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="977af-177">-Content</span><span class="sxs-lookup"><span data-stu-id="977af-177">-Content</span></span>

<span data-ttu-id="977af-178">文件内容作为为其添加数字签名的字节数组。</span><span class="sxs-lookup"><span data-stu-id="977af-178">Contents of a file as a byte array for which the digital signature is added.</span></span> <span data-ttu-id="977af-179">此参数必须与 **SourcePathOrExtension** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="977af-179">This parameter must be used with **SourcePathOrExtension** parameter.</span></span> <span data-ttu-id="977af-180">文件的内容必须采用 Unicode 格式 (UTF-16LE) 格式。</span><span class="sxs-lookup"><span data-stu-id="977af-180">The contents of the file must be in Unicode (UTF-16LE) format.</span></span>

```yaml
Type: System.Byte[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="977af-181">-Confirm</span><span class="sxs-lookup"><span data-stu-id="977af-181">-Confirm</span></span>

<span data-ttu-id="977af-182">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="977af-182">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="977af-183">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="977af-183">-WhatIf</span></span>

<span data-ttu-id="977af-184">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="977af-184">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="977af-185">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="977af-185">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="977af-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="977af-186">CommonParameters</span></span>

<span data-ttu-id="977af-187">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="977af-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="977af-188">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="977af-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="977af-189">输入</span><span class="sxs-lookup"><span data-stu-id="977af-189">INPUTS</span></span>

### <span data-ttu-id="977af-190">System.String</span><span class="sxs-lookup"><span data-stu-id="977af-190">System.String</span></span>

<span data-ttu-id="977af-191">可以通过管道将包含文件路径的字符串传递给 `Set-AuthenticodeSignature` 。</span><span class="sxs-lookup"><span data-stu-id="977af-191">You can pipe a string that contains the file path to `Set-AuthenticodeSignature`.</span></span>

## <span data-ttu-id="977af-192">输出</span><span class="sxs-lookup"><span data-stu-id="977af-192">OUTPUTS</span></span>

### <span data-ttu-id="977af-193">System.Management.Automation.Signature</span><span class="sxs-lookup"><span data-stu-id="977af-193">System.Management.Automation.Signature</span></span>

## <span data-ttu-id="977af-194">注释</span><span class="sxs-lookup"><span data-stu-id="977af-194">NOTES</span></span>

## <span data-ttu-id="977af-195">相关链接</span><span class="sxs-lookup"><span data-stu-id="977af-195">RELATED LINKS</span></span>

[<span data-ttu-id="977af-196">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="977af-196">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="977af-197">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="977af-197">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="977af-198">Get-PfxCertificate</span><span class="sxs-lookup"><span data-stu-id="977af-198">Get-PfxCertificate</span></span>](Get-PfxCertificate.md)

[<span data-ttu-id="977af-199">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="977af-199">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)

[<span data-ttu-id="977af-200">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="977af-200">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="977af-201">about_Signing</span><span class="sxs-lookup"><span data-stu-id="977af-201">about_Signing</span></span>](../Microsoft.PowerShell.Core/About/about_Signing.md)