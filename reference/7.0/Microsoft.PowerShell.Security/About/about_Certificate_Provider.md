---
description: 证书
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/about/about_certificate_provider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Certificate 提供程序
ms.openlocfilehash: d1280d34429600e8c06e96a36921df3d04f9eda6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/13/2020
ms.locfileid: "93200340"
---
# <a name="certificate-provider"></a><span data-ttu-id="df064-104">Certificate 提供程序</span><span class="sxs-lookup"><span data-stu-id="df064-104">Certificate Provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="df064-105">提供程序名称</span><span class="sxs-lookup"><span data-stu-id="df064-105">Provider name</span></span>

<span data-ttu-id="df064-106">证书</span><span class="sxs-lookup"><span data-stu-id="df064-106">Certificate</span></span>

## <a name="drives"></a><span data-ttu-id="df064-107">驱动器</span><span class="sxs-lookup"><span data-stu-id="df064-107">Drives</span></span>

`Cert:`

## <a name="capabilities"></a><span data-ttu-id="df064-108">功能</span><span class="sxs-lookup"><span data-stu-id="df064-108">Capabilities</span></span>

<span data-ttu-id="df064-109">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="df064-109">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="df064-110">简短说明</span><span class="sxs-lookup"><span data-stu-id="df064-110">Short description</span></span>

<span data-ttu-id="df064-111">在 PowerShell 中提供对 x.509 证书存储和证书的访问。</span><span class="sxs-lookup"><span data-stu-id="df064-111">Provides access to X.509 certificate stores and certificates in PowerShell.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="df064-112">详细说明</span><span class="sxs-lookup"><span data-stu-id="df064-112">Detailed description</span></span>

<span data-ttu-id="df064-113">PowerShell **证书** 提供程序允许你获取、添加、更改、清除和删除 PowerShell 中的证书和证书存储。</span><span class="sxs-lookup"><span data-stu-id="df064-113">The PowerShell **Certificate** provider lets you get, add, change, clear, and delete certificates and certificate stores in PowerShell.</span></span>

<span data-ttu-id="df064-114">**证书** 驱动器是包含计算机上的证书存储和证书的分层命名空间。</span><span class="sxs-lookup"><span data-stu-id="df064-114">The **Certificate** drive is a hierarchical namespace containing the certificate stores and certificates on your computer.</span></span>

<span data-ttu-id="df064-115">此 **证书** 提供程序支持以下 cmdlet，本文将对此进行介绍。</span><span class="sxs-lookup"><span data-stu-id="df064-115">The **Certificate** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="df064-116">Get-Location</span><span class="sxs-lookup"><span data-stu-id="df064-116">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="df064-117">Set-Location</span><span class="sxs-lookup"><span data-stu-id="df064-117">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="df064-118">Get-Item</span><span class="sxs-lookup"><span data-stu-id="df064-118">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="df064-119">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="df064-119">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="df064-120">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="df064-120">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="df064-121">Move-Item</span><span class="sxs-lookup"><span data-stu-id="df064-121">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="df064-122">New-Item</span><span class="sxs-lookup"><span data-stu-id="df064-122">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="df064-123">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="df064-123">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="df064-124">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="df064-124">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="df064-125">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="df064-125">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="df064-126">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="df064-126">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="df064-127">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="df064-127">Get-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [<span data-ttu-id="df064-128">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="df064-128">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="df064-129">此提供程序公开的类型</span><span class="sxs-lookup"><span data-stu-id="df064-129">Types exposed by this provider</span></span>

<span data-ttu-id="df064-130">证书驱动器公开以下类型。</span><span class="sxs-lookup"><span data-stu-id="df064-130">The Certificate drive exposes the following types.</span></span>

- <span data-ttu-id="df064-131">将位置存储 (Microsoft.powershell.commands.x509storelocation) ，这是为当前用户和所有用户分组证书的高级容器。</span><span class="sxs-lookup"><span data-stu-id="df064-131">Store locations (Microsoft.PowerShell.Commands.X509StoreLocation), which are high-level containers that group the certificates for the current user and for all users.</span></span> <span data-ttu-id="df064-132">每个系统都具有 CurrentUser 和 LocalMachine（所有用户）存储位置。</span><span class="sxs-lookup"><span data-stu-id="df064-132">Each system has a CurrentUser and LocalMachine (all users) store location.</span></span>

- <span data-ttu-id="df064-133">证书存储 (System.security.cryptography.x509certificates.x509certificate2. X509Store) ，这是保存和管理证书的物理存储。</span><span class="sxs-lookup"><span data-stu-id="df064-133">Certificates stores (System.Security.Cryptography.X509Certificates.X509Store), which are physical stores in which certificates are saved and managed.</span></span>

- <span data-ttu-id="df064-134">X.509 **system.security.cryptography.x509certificates.x509certificate2. X509Certificate2** 证书，每个证书都代表计算机上的一个 x.509 证书。</span><span class="sxs-lookup"><span data-stu-id="df064-134">X.509 **System.Security.Cryptography.X509Certificates.X509Certificate2** certificates, each of which represent an X.509 certificate on the computer.</span></span>
  <span data-ttu-id="df064-135">证书由其指纹标识。</span><span class="sxs-lookup"><span data-stu-id="df064-135">Certificates are identified by their thumbprints.</span></span>

## <a name="navigating-the-certificate-drive"></a><span data-ttu-id="df064-136">导航证书驱动器</span><span class="sxs-lookup"><span data-stu-id="df064-136">Navigating the Certificate drive</span></span>

<span data-ttu-id="df064-137">**证书** 提供程序在 PowerShell 中将证书命名空间作为 `Cert:` 驱动器公开。</span><span class="sxs-lookup"><span data-stu-id="df064-137">The **Certificate** provider exposes the certificate namespace as the `Cert:` drive in PowerShell.</span></span> <span data-ttu-id="df064-138">此命令使用 `Set-Location` 命令将当前位置更改为 LocalMachine 存储位置中的根证书存储。</span><span class="sxs-lookup"><span data-stu-id="df064-138">This command uses the `Set-Location` command to change the current location to the Root certificate store in the LocalMachine store location.</span></span> <span data-ttu-id="df064-139">使用反斜杠 (\\) 或正斜杠 (/) 来指示驱动器的级别 `Cert:` 。</span><span class="sxs-lookup"><span data-stu-id="df064-139">Use a backslash (\\) or a forward slash (/) to indicate a level of the `Cert:` drive.</span></span>

```powershell
Set-Location Cert:
```

<span data-ttu-id="df064-140">你还可以使用任何其他 PowerShell 驱动器中的证书提供程序。</span><span class="sxs-lookup"><span data-stu-id="df064-140">You can also work with the certificate provider from any other PowerShell drive.</span></span> <span data-ttu-id="df064-141">若要从其他位置引用别名，请 `Cert:` 在路径中使用驱动器名称。</span><span class="sxs-lookup"><span data-stu-id="df064-141">To reference an alias from another location, use the `Cert:` drive name in the path.</span></span>

```powershell
PS Cert:\> Set-Location -Path LocalMachine\Root
```

<span data-ttu-id="df064-142">若要返回到文件系统驱动器，请键入驱动器名称。</span><span class="sxs-lookup"><span data-stu-id="df064-142">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="df064-143">例如，键入：</span><span class="sxs-lookup"><span data-stu-id="df064-143">For example, type:</span></span>

```powershell
Set-Location C:
```

> [!NOTE]
> <span data-ttu-id="df064-144">PowerShell 使用别名以允许你熟悉的方法来处理提供程序路径。</span><span class="sxs-lookup"><span data-stu-id="df064-144">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="df064-145">命令（如 `dir` 和） `ls` 现在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的别名， `cd` 是 [设置位置](xref:Microsoft.PowerShell.Management.Set-Location)的别名。</span><span class="sxs-lookup"><span data-stu-id="df064-145">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span>
> <span data-ttu-id="df064-146">和 `pwd` 是 [获取位置](xref:Microsoft.PowerShell.Management.Get-Location)的别名。</span><span class="sxs-lookup"><span data-stu-id="df064-146">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="displaying-the-contents-of-the-cert-drive"></a><span data-ttu-id="df064-147">显示 Cert：驱动器的内容</span><span class="sxs-lookup"><span data-stu-id="df064-147">Displaying the Contents of the Cert: drive</span></span>

<span data-ttu-id="df064-148">此命令使用 `Get-ChildItem` cmdlet 来显示 CurrentUser 证书存储位置中的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="df064-148">This command uses the `Get-ChildItem` cmdlet to display the certificate stores in the CurrentUser certificate store location.</span></span>

<span data-ttu-id="df064-149">如果不在 `Cert:` 驱动器中，请使用绝对路径。</span><span class="sxs-lookup"><span data-stu-id="df064-149">If you are not in the `Cert:` drive, use an absolute path.</span></span>

```powershell
PS Cert:\CurrentUser\> Get-ChildItem
```

### <a name="displaying-certificate-properties-within-the-cert-drive"></a><span data-ttu-id="df064-150">在 Cert：驱动器中显示证书属性</span><span class="sxs-lookup"><span data-stu-id="df064-150">Displaying certificate properties within the Cert: drive</span></span>

<span data-ttu-id="df064-151">此示例使用获取证书 `Get-Item` ，并将其存储在变量中。</span><span class="sxs-lookup"><span data-stu-id="df064-151">This example gets a certificate with `Get-Item` and stores it in a variable.</span></span>
<span data-ttu-id="df064-152">该示例显示了使用 ( **DnsNameList** ， **EnhancedKeyUsageList** ， **SendAsTrustedIssuer** ) 的新证书脚本属性 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="df064-152">The example shows the new certificate script properties ( **DnsNameList** , **EnhancedKeyUsageList** , **SendAsTrustedIssuer** ) using `Select-Object`.</span></span>

```powershell
$c = Get-Item cert:\LocalMachine\My\52A149D0393CE8A8D4AF0B172ED667A9E3A1F44E
$c | Format-List DnsNameList, EnhancedKeyUsageList, SendAsTrustedIssuer
```

```output
DnsNameList          : {SERVER01.contoso.com}
EnhancedKeyUsageList : {WiFi-Machine (1.3.6.1.4.1.311.42.2.6),
                       Client Authentication (1.3.6.1.5.5.7.3.2)}
SendAsTrustedIssuer  : False
```

### <a name="find-all-codesigning-certificates"></a><span data-ttu-id="df064-153">查找所有代码签名证书</span><span class="sxs-lookup"><span data-stu-id="df064-153">Find all CodeSigning certificates</span></span>

<span data-ttu-id="df064-154">此命令使用 cmdlet 的 **CodeSigningCert** 和 **递归** 参数 `Get-ChildItem` 获取具有代码签名颁发机构的计算机上的所有证书。</span><span class="sxs-lookup"><span data-stu-id="df064-154">This command uses the **CodeSigningCert** and **Recurse** parameters of the `Get-ChildItem` cmdlet to get all of the certificates on the computer that have code-signing authority.</span></span>

```powershell
Get-ChildItem -Path cert: -CodeSigningCert -Recurse
```

### <a name="find-expired-certificates"></a><span data-ttu-id="df064-155">查找过期的证书</span><span class="sxs-lookup"><span data-stu-id="df064-155">Find expired certificates</span></span>

<span data-ttu-id="df064-156">此命令使用 cmdlet 的 **ExpiringInDays** 参数 `Get-ChildItem` 来获取将在接下来的30天内到期的证书。</span><span class="sxs-lookup"><span data-stu-id="df064-156">This command uses the **ExpiringInDays** parameter of the `Get-ChildItem` cmdlet to get certificates that will expire within the next 30 days.</span></span>

```powershell
Get-ChildItem -Path cert:\LocalMachine\WebHosting -ExpiringInDays 30
```

### <a name="find-server-ssl-certificates"></a><span data-ttu-id="df064-157">查找服务器 SSL 证书</span><span class="sxs-lookup"><span data-stu-id="df064-157">Find Server SSL Certificates</span></span>

<span data-ttu-id="df064-158">此命令使用 cmdlet 的 **SSLServerAuthentication** 参数 `Get-ChildItem` 来获取 My 和 WebHosting 存储中的所有服务器 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="df064-158">This command uses the **SSLServerAuthentication** parameter of the `Get-ChildItem` cmdlet to get all Server SSL Certificates in the My and WebHosting stores.</span></span>

```powershell
Get-ChildItem -Path cert:\LocalMachine\My, cert:\LocalMachine\WebHosting `
  -SSLServerAuthentication
```

### <a name="find-expired-certificates-on-remote-computers"></a><span data-ttu-id="df064-159">在远程计算机上查找过期的证书</span><span class="sxs-lookup"><span data-stu-id="df064-159">Find expired certificates on remote computers</span></span>

<span data-ttu-id="df064-160">此命令使用 `Invoke-Command` cmdlet `Get-ChildItem` 在 Srv01 和 Srv02 计算机上运行命令。</span><span class="sxs-lookup"><span data-stu-id="df064-160">This command uses the `Invoke-Command` cmdlet to run a `Get-ChildItem` command on the Srv01 and Srv02 computers.</span></span> <span data-ttu-id="df064-161">如果 **ExpiringInDays** 参数中的值为零 (0) ，则将获取 Srv01 和 Srv02 计算机上已过期的证书。</span><span class="sxs-lookup"><span data-stu-id="df064-161">A value of zero (0) in the **ExpiringInDays** parameter gets certificates on the Srv01 and Srv02 computers that have expired.</span></span>

```powershell
Invoke-Command -ComputerName Srv01, Srv02 {Get-ChildItem -Path cert:\* `
  -Recurse -ExpiringInDays 0}
```

### <a name="combining-filters-to-find-a-specific-set-of-certificates"></a><span data-ttu-id="df064-162">合并筛选器以查找特定的一组证书</span><span class="sxs-lookup"><span data-stu-id="df064-162">Combining filters to find a specific set of certificates</span></span>

<span data-ttu-id="df064-163">此命令获取 LocalMachine 存储位置中具有以下属性的所有证书：</span><span class="sxs-lookup"><span data-stu-id="df064-163">This command gets all certificates in the LocalMachine store location that have the following attributes:</span></span>

- <span data-ttu-id="df064-164">其 DNS 名称中的 "fabrikam"</span><span class="sxs-lookup"><span data-stu-id="df064-164">"fabrikam" in their DNS name</span></span>
- <span data-ttu-id="df064-165">EKU 中的 "客户端身份验证"</span><span class="sxs-lookup"><span data-stu-id="df064-165">"Client Authentication" in their EKU</span></span>
- <span data-ttu-id="df064-166">`$true` **SendAsTrustedIssuer** 属性的值</span><span class="sxs-lookup"><span data-stu-id="df064-166">a value of `$true` for the **SendAsTrustedIssuer** property</span></span>
- <span data-ttu-id="df064-167">不会在接下来的30天内过期。</span><span class="sxs-lookup"><span data-stu-id="df064-167">do not expire within the next 30 days.</span></span>

<span data-ttu-id="df064-168">**NotAfter** 属性存储证书的过期日期。</span><span class="sxs-lookup"><span data-stu-id="df064-168">The **NotAfter** property stores the certificate expiration date.</span></span>

```powershell
[DateTime] $ValidThrough = (Get-Date) + (New-TimeSpan -Days 30)
Get-ChildItem -Path cert:\* -Recurse -DNSName "*fabrikam*" `
  -EKU "*Client Authentication*" | Where-Object {
                                     $_.SendAsTrustedIssuer -and `
                                     $_.NotAfter -gt $ValidThrough
                                   }
```

## <a name="opening-the-certificates-mmc-snap-in"></a><span data-ttu-id="df064-169">打开证书 MMC 管理单元</span><span class="sxs-lookup"><span data-stu-id="df064-169">Opening the Certificates MMC Snap-in</span></span>

<span data-ttu-id="df064-170">该 `Invoke-Item` cmdlet 将使用默认应用程序打开指定的路径。</span><span class="sxs-lookup"><span data-stu-id="df064-170">The `Invoke-Item` cmdlet will use the default application to open a path you specify.</span></span> <span data-ttu-id="df064-171">对于证书，默认的应用程序是 "证书" MMC 管理单元。</span><span class="sxs-lookup"><span data-stu-id="df064-171">For certificates, the default application is the Certificates MMC snap-in.</span></span>

<span data-ttu-id="df064-172">此命令将打开证书 MMC 管理单元以管理指定的证书。</span><span class="sxs-lookup"><span data-stu-id="df064-172">This command opens the Certificates MMC snap-in to manage the specified certificate.</span></span>

```powershell
Invoke-Item cert:\CurrentUser\my\6B8223358119BB08840DEE50FD8AF9EA776CE66B
```

## <a name="copying-certificates"></a><span data-ttu-id="df064-173">复制证书</span><span class="sxs-lookup"><span data-stu-id="df064-173">Copying Certificates</span></span>

<span data-ttu-id="df064-174">**证书** 提供程序不支持复制证书。</span><span class="sxs-lookup"><span data-stu-id="df064-174">Copying certificates is not supported by the **Certificate** provider.</span></span> <span data-ttu-id="df064-175">尝试复制证书时，会看到此错误。</span><span class="sxs-lookup"><span data-stu-id="df064-175">When you attempt to copy a certificate, you see this error.</span></span>

```
$path = "Cert:\LocalMachine\Root\E2C0F6662D3C569705B4B31FE2CBF3434094B254"
PS Cert:\LocalMachine\> Copy-Item -Path $path -Destination .\CA\
Copy-Item : Provider operation stopped because the provider does not support
this operation.
At line:1 char:1
+ Copy-Item -Path $path -Destination .\CA\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotImplemented: (:) [Copy-Item],
                              PSNotSupportedException
    + FullyQualifiedErrorId : NotSupported,
                              Microsoft.PowerShell.Commands.CopyItemCommand
```

## <a name="moving-certificates"></a><span data-ttu-id="df064-176">移动证书</span><span class="sxs-lookup"><span data-stu-id="df064-176">Moving Certificates</span></span>

### <a name="move-all-ssl-server-authentication-certs-to-the-webhosting-store"></a><span data-ttu-id="df064-177">将所有 SSL 服务器身份验证证书移到 WebHosting 存储</span><span class="sxs-lookup"><span data-stu-id="df064-177">Move all SSL Server authentication certs to the WebHosting store</span></span>

<span data-ttu-id="df064-178">此命令使用 `Move-Item` cmdlet 将证书从 My 存储移到 WebHosting 存储。</span><span class="sxs-lookup"><span data-stu-id="df064-178">This command uses the `Move-Item` cmdlet to move a certificate from the My store to the WebHosting store.</span></span>

<span data-ttu-id="df064-179">`Move-Item` 不会移动证书存储，也不会将证书移到不同的存储位置，例如将证书从 LocalMachine 移动到 CurrentUser。</span><span class="sxs-lookup"><span data-stu-id="df064-179">`Move-Item` will not move certificate stores and it will not move certificates to a different store location, such as moving a certificate from LocalMachine to CurrentUser.</span></span> <span data-ttu-id="df064-180">`Move-Item`Cmdlet 将移动证书，但不会移动私钥。</span><span class="sxs-lookup"><span data-stu-id="df064-180">The `Move-Item` cmdlet moves certificates, but it does not move private keys.</span></span>

<span data-ttu-id="df064-181">此命令使用 cmdlet 的 **SSLServerAuthentication** 参数 `Get-ChildItem` 来获取 "我的证书" 存储中的 SSL 服务器身份验证证书。</span><span class="sxs-lookup"><span data-stu-id="df064-181">This command uses the **SSLServerAuthentication** parameter of the `Get-ChildItem` cmdlet to get SSL server authentication certificates in the MY certificate store.</span></span>

<span data-ttu-id="df064-182">返回的证书将通过管道传递给 `Move-Item` cmdlet，这会将证书移到 WebHosting 存储区。</span><span class="sxs-lookup"><span data-stu-id="df064-182">The returned certificates are piped to the `Move-Item` cmdlet, which moves the certificates to the WebHosting store.</span></span>

```powershell
Get-ChildItem cert:\LocalMachine\My -SSLServerAuthentication | Move-Item `
  -Destination cert:\LocalMachine\WebHosting
```

## <a name="deleting-certificates-and-private-keys"></a><span data-ttu-id="df064-183">删除证书和私钥</span><span class="sxs-lookup"><span data-stu-id="df064-183">Deleting Certificates and Private Keys</span></span>

<span data-ttu-id="df064-184">该 `Remove-Item` cmdlet 将删除指定的证书。</span><span class="sxs-lookup"><span data-stu-id="df064-184">The `Remove-Item` cmdlet will remove certificates that you specify.</span></span> <span data-ttu-id="df064-185">`-DeleteKey`动态参数删除私钥。</span><span class="sxs-lookup"><span data-stu-id="df064-185">The `-DeleteKey` dynamic parameter deletes the private key.</span></span>

### <a name="delete-a-certificate-from-the-ca-store"></a><span data-ttu-id="df064-186">从 CA 存储区中删除证书</span><span class="sxs-lookup"><span data-stu-id="df064-186">Delete a Certificate from the CA store</span></span>

<span data-ttu-id="df064-187">此命令从 CA 证书存储中删除证书，但会使相关联的私钥保持不变。</span><span class="sxs-lookup"><span data-stu-id="df064-187">This command deletes a certificate from the CA certificate store, but leaves the associated private key intact.</span></span>

<span data-ttu-id="df064-188">在 `Cert:` 驱动器中， `Remove-Item` cmdlet 仅支持 **DeleteKey** 、 **Path** 、 **WhatIf** 和 **Confirm** 参数。</span><span class="sxs-lookup"><span data-stu-id="df064-188">In the `Cert:` drive, the `Remove-Item` cmdlet supports only the **DeleteKey** , **Path** , **WhatIf** , and **Confirm** parameters.</span></span> <span data-ttu-id="df064-189">忽略所有其他参数。</span><span class="sxs-lookup"><span data-stu-id="df064-189">All other parameters are ignored.</span></span>

```powershell
Remove-Item cert:\LocalMachine\CA\5DDC44652E62BF9AA1116DC41DE44AB47C87BDD0
```

### <a name="delete-a-certificate-using-a-wildcards-in-the-dns-name"></a><span data-ttu-id="df064-190">使用 DNS 名称中的通配符删除证书</span><span class="sxs-lookup"><span data-stu-id="df064-190">Delete a Certificate using a wildcards in the DNS name</span></span>

<span data-ttu-id="df064-191">此命令删除具有包含“Fabrikam”的 DNS 名称的所有证书。</span><span class="sxs-lookup"><span data-stu-id="df064-191">This command deletes all certificates that have a DNS name that contains "Fabrikam".</span></span> <span data-ttu-id="df064-192">它使用 cmdlet 的 **DNSName** 参数 `Get-ChildItem` 来获取证书，并使用 cmdlet 将 `Remove-Item` 其删除。</span><span class="sxs-lookup"><span data-stu-id="df064-192">It uses the **DNSName** parameter of the `Get-ChildItem` cmdlet to get the certificates and the `Remove-Item` cmdlet to delete them.</span></span>

```powershell
Get-ChildItem -Path cert:\LocalMachine -DnsName *Fabrikam* | Remove-Item
```

### <a name="delete-private-keys-from-a-remote-computer"></a><span data-ttu-id="df064-193">从远程计算机中删除私钥</span><span class="sxs-lookup"><span data-stu-id="df064-193">Delete private keys from a remote computer</span></span>

<span data-ttu-id="df064-194">这一系列命令将启用委派，然后在远程计算机上删除该证书和相关联的私钥。</span><span class="sxs-lookup"><span data-stu-id="df064-194">This series of commands enables delegation and then deletes the certificate and associated private key on a remote computer.</span></span> <span data-ttu-id="df064-195">若要删除远程计算机上的私钥，你必须使用委派的凭据。</span><span class="sxs-lookup"><span data-stu-id="df064-195">To delete a private key on a remote computer, you must use delegated credentials.</span></span>

<span data-ttu-id="df064-196">使用 `Enable-WSManCredSSP` cmdlet 在 S1 远程计算机上的客户端上启用凭据安全服务提供程序 (CredSSP) 身份验证。</span><span class="sxs-lookup"><span data-stu-id="df064-196">Use the `Enable-WSManCredSSP` cmdlet to enable Credential Security Service Provider (CredSSP) authentication on a client on the S1 remote computer.</span></span>
<span data-ttu-id="df064-197">CredSSP 允许使用委派的身份验证。</span><span class="sxs-lookup"><span data-stu-id="df064-197">CredSSP permits delegated authentication.</span></span>

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer S1
```

<span data-ttu-id="df064-198">使用 `Connect-WSMan` cmdlet 将 S1 计算机连接到本地计算机上的 WinRM 服务。</span><span class="sxs-lookup"><span data-stu-id="df064-198">Use the `Connect-WSMan` cmdlet to connect the S1 computer to the WinRM service on the local computer.</span></span> <span data-ttu-id="df064-199">此命令完成后，S1 计算机将显示在 `WSMan:` PowerShell 中的本地驱动器中。</span><span class="sxs-lookup"><span data-stu-id="df064-199">When this command completes, the S1 computer appears in the local `WSMan:` drive in PowerShell.</span></span>

```powershell
Connect-WSMan -ComputerName S1 -Credential Domain01\Admin01
```

<span data-ttu-id="df064-200">现在，你可以使用 WSMan：驱动器中的 Set-Item cmdlet 启用 WinRM 服务的 CredSSP 属性。</span><span class="sxs-lookup"><span data-stu-id="df064-200">Now, you can use the Set-Item cmdlet in the WSMan: drive to enable the CredSSP attribute for the WinRM service.</span></span>

```powershell
Set-Item -Path WSMan:\S1\Service\Auth\CredSSP -Value $true
```

<span data-ttu-id="df064-201">使用 cmdlet 在 s1 计算机上启动远程会话 `New-PSSession` ，并指定 CredSSP 身份验证。</span><span class="sxs-lookup"><span data-stu-id="df064-201">Start a remote session on the s1 computer using the `New-PSSession` cmdlet, and specify CredSSP authentication.</span></span> <span data-ttu-id="df064-202">将会话保存在 `$s` 变量中。</span><span class="sxs-lookup"><span data-stu-id="df064-202">Saves the session in the `$s` variable.</span></span>

```powershell
$s  = New-PSSession S1 -Authentication CredSSP -Credential Domain01\Admin01
```

<span data-ttu-id="df064-203">最后，使用 `Invoke-Command` cmdlet 在 `Remove-Item` 变量中的会话中运行命令 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="df064-203">Finally, use the `Invoke-Command` cmdlet to run a `Remove-Item` command in the session in the `$s` variable.</span></span> <span data-ttu-id="df064-204">该 `Remove-Item` 命令使用 **DeleteKey** 参数删除私钥以及指定的证书。</span><span class="sxs-lookup"><span data-stu-id="df064-204">The `Remove-Item` command uses the **DeleteKey** parameter to remove the private key along with the specified certificate.</span></span>

```powershell
Invoke-Command -Session $s { Remove-Item `
  -Path cert:\LocalMachine\My\D2D38EBA60CAA1C12055A2E1C83B15AD450110C2 `
  -DeleteKey
  }
```

### <a name="delete-expired-certificates"></a><span data-ttu-id="df064-205">删除过期的证书</span><span class="sxs-lookup"><span data-stu-id="df064-205">Delete expired Certificates</span></span>

<span data-ttu-id="df064-206">此命令使用值为0的 cmdlet 的 **ExpiringInDays** 参数 `Get-ChildItem` 来获取 WebHosting 存储区中已过期的证书。</span><span class="sxs-lookup"><span data-stu-id="df064-206">This command uses the **ExpiringInDays** parameter of the `Get-ChildItem` cmdlet with a value of 0 to get certificates in the WebHosting store that have expired.</span></span>

<span data-ttu-id="df064-207">包含所返回证书的变量将通过管道传递给 `Remove-Item` cmdlet，后者将删除它们。</span><span class="sxs-lookup"><span data-stu-id="df064-207">The variable containing the returned certificates is piped to the `Remove-Item` cmdlet, which deletes them.</span></span> <span data-ttu-id="df064-208">该命令使用 **DeleteKey** 参数来删除私钥以及证书。</span><span class="sxs-lookup"><span data-stu-id="df064-208">The command uses the **DeleteKey** parameter to delete the private key along with the certificate.</span></span>

```powershell
$expired = Get-ChildItem cert:\LocalMachine\WebHosting -ExpiringInDays 0
$expired | Remove-Item -DeleteKey
```

## <a name="creating-certificates"></a><span data-ttu-id="df064-209">创建证书</span><span class="sxs-lookup"><span data-stu-id="df064-209">Creating Certificates</span></span>

<span data-ttu-id="df064-210">`New-Item`Cmdlet 不会在 **证书** 提供程序中创建新证书。</span><span class="sxs-lookup"><span data-stu-id="df064-210">The `New-Item` cmdlet does not create new certificates in the **Certificate** provider.</span></span> <span data-ttu-id="df064-211">使用 [new-selfsignedcertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet 创建用于测试的证书。</span><span class="sxs-lookup"><span data-stu-id="df064-211">Use the [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet to create a certificate for testing purposes.</span></span>

## <a name="creating-certificate-stores"></a><span data-ttu-id="df064-212">创建证书存储</span><span class="sxs-lookup"><span data-stu-id="df064-212">Creating Certificate Stores</span></span>

<span data-ttu-id="df064-213">在 Cert：驱动器中， `New-Item` cmdlet 会在 LocalMachine 存储位置中创建证书存储。</span><span class="sxs-lookup"><span data-stu-id="df064-213">In the Cert: drive, the `New-Item` cmdlet creates certificate stores in the LocalMachine store location.</span></span> <span data-ttu-id="df064-214">它支持 **Name** 、 **Path** 、 **WhatIf** 和 **Confirm** 参数。</span><span class="sxs-lookup"><span data-stu-id="df064-214">It supports the **Name** , **Path** , **WhatIf** , and **Confirm** parameters.</span></span> <span data-ttu-id="df064-215">忽略所有其他参数。</span><span class="sxs-lookup"><span data-stu-id="df064-215">All other parameters are ignored.</span></span> <span data-ttu-id="df064-216">该命令将返回表示新证书存储的 **system.security.cryptography.x509certificates.x509certificate2. X509Store。**</span><span class="sxs-lookup"><span data-stu-id="df064-216">The command returns a **System.Security.Cryptography.X509Certificates.X509Store** that represents the new certificate store.</span></span>

<span data-ttu-id="df064-217">此命令在 LocalMachine 存储位置中创建名为“CustomStore”的新证书存储。</span><span class="sxs-lookup"><span data-stu-id="df064-217">This command creates a new certificate store named "CustomStore" in the LocalMachine store location.</span></span>

```powershell
New-Item -Path cert:\LocalMachine\CustomStore
```

### <a name="create-a-new-certificate-store-on-a-remote-computer"></a><span data-ttu-id="df064-218">在远程计算机上创建新的证书存储</span><span class="sxs-lookup"><span data-stu-id="df064-218">Create a new certificate store on a remote computer</span></span>

<span data-ttu-id="df064-219">此命令在 Server01 计算机上的 LocalMachine 存储位置中创建名为“HostingStore”的新证书存储。</span><span class="sxs-lookup"><span data-stu-id="df064-219">This command creates a new certificate store named "HostingStore" in the LocalMachine store location on the Server01 computer.</span></span>

<span data-ttu-id="df064-220">该命令使用 `Invoke-Command` cmdlet `New-Item` 在 Server01 计算机上运行命令。</span><span class="sxs-lookup"><span data-stu-id="df064-220">The command uses the `Invoke-Command` cmdlet to run a `New-Item` command on the Server01 computer.</span></span> <span data-ttu-id="df064-221">该命令将返回表示新证书存储的 **system.security.cryptography.x509certificates.x509certificate2. X509Store。**</span><span class="sxs-lookup"><span data-stu-id="df064-221">The command returns a **System.Security.Cryptography.X509Certificates.X509Store** that represents the new certificate store.</span></span>

```powershell
Invoke-Command { New-Item -Path cert:\LocalMachine\CustomStore } `
  -ComputerName Server01
```

## <a name="creating-client-certificates-for-ws-man"></a><span data-ttu-id="df064-222">为 WS-Man 创建客户端证书</span><span class="sxs-lookup"><span data-stu-id="df064-222">Creating Client Certificates for WS-Man</span></span>

<span data-ttu-id="df064-223">此命令创建 **ws-management** 客户端可以使用的 **ClientCertificate** 项。</span><span class="sxs-lookup"><span data-stu-id="df064-223">This command creates **ClientCertificate** entry that can be used by the **WS-Management** client.</span></span> <span data-ttu-id="df064-224">新的 **ClientCertificate** 将在 **ClientCertificate** 目录下显示为 "ClientCertificate_1234567890"。</span><span class="sxs-lookup"><span data-stu-id="df064-224">The new **ClientCertificate** will show up under the **ClientCertificate** directory as "ClientCertificate_1234567890".</span></span> <span data-ttu-id="df064-225">所有参数都是必需的。</span><span class="sxs-lookup"><span data-stu-id="df064-225">All of the parameters are mandatory.</span></span> <span data-ttu-id="df064-226">**颁发者** 必须是颁发者证书的指纹。</span><span class="sxs-lookup"><span data-stu-id="df064-226">The **Issuer** needs to be thumbprint of the issuers certificate.</span></span>

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* -Credential $cred
```

## <a name="deleting-certificate-stores"></a><span data-ttu-id="df064-227">删除证书存储</span><span class="sxs-lookup"><span data-stu-id="df064-227">Deleting Certificate Stores</span></span>

### <a name="delete-a-certificate-store-from-a-remote-computer"></a><span data-ttu-id="df064-228">从远程计算机中删除证书存储</span><span class="sxs-lookup"><span data-stu-id="df064-228">Delete a certificate store from a remote computer</span></span>

<span data-ttu-id="df064-229">此命令使用 `Invoke-Command` cmdlet `Remove-Item` 在 S1 和 S2 计算机上运行命令。</span><span class="sxs-lookup"><span data-stu-id="df064-229">This command uses the `Invoke-Command` cmdlet to run a `Remove-Item` command on the S1 and S2 computers.</span></span> <span data-ttu-id="df064-230">此 `Remove-Item` 命令包含 **递归** 参数，该参数在删除存储之前删除存储中的证书。</span><span class="sxs-lookup"><span data-stu-id="df064-230">The `Remove-Item` command includes the **Recurse** parameter, which deletes the certificates in the store before it deletes the store.</span></span>

```powershell
Invoke-Command { Remove-Item -Path cert:\LocalMachine\TestStore -Recurse } `
  -ComputerName S1, S2
```

## <a name="dynamic-parameters"></a><span data-ttu-id="df064-231">动态参数</span><span class="sxs-lookup"><span data-stu-id="df064-231">Dynamic parameters</span></span>

<span data-ttu-id="df064-232">动态参数是 PowerShell 提供程序添加的 cmdlet 参数，只有在启用了提供程序的驱动器中使用 cmdlet 时，这些参数才可用。</span><span class="sxs-lookup"><span data-stu-id="df064-232">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span> <span data-ttu-id="df064-233">这些参数在证书提供程序的所有子目录中都有效，但仅对证书有效。</span><span class="sxs-lookup"><span data-stu-id="df064-233">These parameters are valid in all subdirectories of the Certificate provider, but are effective only on certificates.</span></span>

> [!NOTE]
> <span data-ttu-id="df064-234">对属性执行筛选的参数 `EnhancedKeyUsageList` 还会返回具有空 `EnhancedKeyUsageList` 属性值的项。</span><span class="sxs-lookup"><span data-stu-id="df064-234">Parameters that perform filtering against the `EnhancedKeyUsageList` property also return items with an empty `EnhancedKeyUsageList` property value.</span></span>
> <span data-ttu-id="df064-235">具有空 **EnhancedKeyUsageList** 的证书可用于所有目的。</span><span class="sxs-lookup"><span data-stu-id="df064-235">Certificates that have an empty **EnhancedKeyUsageList** can be used for all purposes.</span></span>

<span data-ttu-id="df064-236">PowerShell 6.0 中删除了以下证书提供程序参数。</span><span class="sxs-lookup"><span data-stu-id="df064-236">The following Certificate provider parameters were removed in PowerShell 6.0.</span></span>

- <span data-ttu-id="df064-237">DNSName</span><span class="sxs-lookup"><span data-stu-id="df064-237">DNSName</span></span>
- <span data-ttu-id="df064-238">DocumentEncryptionCert</span><span class="sxs-lookup"><span data-stu-id="df064-238">DocumentEncryptionCert</span></span>
- <span data-ttu-id="df064-239">EKU</span><span class="sxs-lookup"><span data-stu-id="df064-239">EKU</span></span>
- <span data-ttu-id="df064-240">ExpiringInDays</span><span class="sxs-lookup"><span data-stu-id="df064-240">ExpiringInDays</span></span>
- <span data-ttu-id="df064-241">SSLServerAuthentication</span><span class="sxs-lookup"><span data-stu-id="df064-241">SSLServerAuthentication</span></span>

### <a name="codesigningcert-systemmanagementautomationswitchparameter"></a><span data-ttu-id="df064-242">CodeSigningCert <SwitchParameter></span><span class="sxs-lookup"><span data-stu-id="df064-242">CodeSigningCert <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="df064-243">支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="df064-243">Cmdlets supported</span></span>

- [<span data-ttu-id="df064-244">Get-Item</span><span class="sxs-lookup"><span data-stu-id="df064-244">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)

- [<span data-ttu-id="df064-245">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="df064-245">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="df064-246">此参数获取在其 **EnhancedKeyUsageList** 属性值中具有 "代码签名" 的证书。</span><span class="sxs-lookup"><span data-stu-id="df064-246">This parameter gets certificates that have "Code Signing" in their **EnhancedKeyUsageList** property value.</span></span>

### <a name="deletekey-systemmanagementautomationswitchparameter"></a><span data-ttu-id="df064-247">DeleteKey <SwitchParameter></span><span class="sxs-lookup"><span data-stu-id="df064-247">DeleteKey <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="df064-248">支持的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="df064-248">Cmdlets supported</span></span>

- [<span data-ttu-id="df064-249">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="df064-249">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)

<span data-ttu-id="df064-250">此参数删除证书时，删除相关联的私钥。</span><span class="sxs-lookup"><span data-stu-id="df064-250">This parameter deletes the associated private key when it deletes the certificate.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="df064-251">若要删除与远程计算机上的存储区中的用户证书关联的私钥 `Cert:\CurrentUser` ，必须使用委派的凭据。</span><span class="sxs-lookup"><span data-stu-id="df064-251">To delete a private key that is associated with a user certificate in the `Cert:\CurrentUser` store on a remote computer, you must use delegated credentials.</span></span> <span data-ttu-id="df064-252">`Invoke-Command`Cmdlet 使用 **CredSSP** 参数支持凭据委托。</span><span class="sxs-lookup"><span data-stu-id="df064-252">The `Invoke-Command` cmdlet supports credential delegation using the **CredSSP** parameter.</span></span> <span data-ttu-id="df064-253">使用 `Remove-Item` with 和 credential 委托之前，应考虑任何安全风险 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="df064-253">You should consider any security risks before using `Remove-Item` with `Invoke-Command` and credential delegation.</span></span>

<span data-ttu-id="df064-254">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="df064-254">This parameter was introduced in Windows PowerShell 3.0.</span></span>

### <a name="itemtype-string"></a><span data-ttu-id="df064-255">ItemType \<String\></span><span class="sxs-lookup"><span data-stu-id="df064-255">ItemType \<String\></span></span>

<span data-ttu-id="df064-256">此参数允许你指定由创建的项的类型 `New-Item` 。</span><span class="sxs-lookup"><span data-stu-id="df064-256">This parameter allows you to specify the type of item created by `New-Item`.</span></span>

<span data-ttu-id="df064-257">在 `Certificate` 驱动器中，允许使用以下值：</span><span class="sxs-lookup"><span data-stu-id="df064-257">In a `Certificate` drive, the following values are allowed:</span></span>

- <span data-ttu-id="df064-258">Certificate 提供程序</span><span class="sxs-lookup"><span data-stu-id="df064-258">Certificate Provider</span></span>
- <span data-ttu-id="df064-259">证书</span><span class="sxs-lookup"><span data-stu-id="df064-259">Certificate</span></span>
- <span data-ttu-id="df064-260">应用商店</span><span class="sxs-lookup"><span data-stu-id="df064-260">Store</span></span>
- <span data-ttu-id="df064-261">StoreLocation</span><span class="sxs-lookup"><span data-stu-id="df064-261">StoreLocation</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="df064-262">支持的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="df064-262">Cmdlets Supported</span></span>

- [<span data-ttu-id="df064-263">New-Item</span><span class="sxs-lookup"><span data-stu-id="df064-263">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="script-properties"></a><span data-ttu-id="df064-264">脚本属性</span><span class="sxs-lookup"><span data-stu-id="df064-264">Script properties</span></span>

<span data-ttu-id="df064-265">已将新的脚本属性添加到表示证书的 **x509Certificate2** 对象，以便轻松搜索和管理证书。</span><span class="sxs-lookup"><span data-stu-id="df064-265">New script properties have been added to the **x509Certificate2** object that represents the certificates to make it easy to search and manage the certificates.</span></span>

- <span data-ttu-id="df064-266">`DnsNameList`：若要填充 `DnsNameList` 属性，证书提供程序将从 SubjectAlternativeName (SAN) 扩展中的 DNSName 条目复制内容。</span><span class="sxs-lookup"><span data-stu-id="df064-266">`DnsNameList`: To populate the `DnsNameList` property, the Certificate provider copies the content from the DNSName entry in the SubjectAlternativeName (SAN) extension.</span></span> <span data-ttu-id="df064-267">如果 SAN 扩展为空，则使用证书的 Subject 字段中的内容填充该属性。</span><span class="sxs-lookup"><span data-stu-id="df064-267">If the SAN extension is empty, the property is populated with content from the Subject field of the certificate.</span></span>

- <span data-ttu-id="df064-268">`EnhancedKeyUsageList`：若要填充 `EnhancedKeyUsageList` 属性，证书提供程序将复制证书中 EnhancedKeyUsage (EKU) 字段的 OID 属性，并为其创建一个友好名称。</span><span class="sxs-lookup"><span data-stu-id="df064-268">`EnhancedKeyUsageList`: To populate the `EnhancedKeyUsageList` property, the Certificate provider copies the OID properties of the EnhancedKeyUsage (EKU) field in the certificate and creates a friendly name for it.</span></span>

- <span data-ttu-id="df064-269">`SendAsTrustedIssuer`：若要填充 `SendAsTrustedIssuer` 属性，证书提供程序将 `SendAsTrustedIssuer` 从证书复制属性。</span><span class="sxs-lookup"><span data-stu-id="df064-269">`SendAsTrustedIssuer`: To populate the `SendAsTrustedIssuer` property, the Certificate provider copies the `SendAsTrustedIssuer` property from the certificate.</span></span>  <span data-ttu-id="df064-270">有关详细信息，请参阅 [管理客户端身份验证的受信任颁发](/windows-server/security/tls/what-s-new-in-tls-ssl-schannel-ssp-overview#BKMK_TrustedIssuers)者。</span><span class="sxs-lookup"><span data-stu-id="df064-270">For more information see [Management of trusted issuers for client authentication](/windows-server/security/tls/what-s-new-in-tls-ssl-schannel-ssp-overview#BKMK_TrustedIssuers).</span></span>

<span data-ttu-id="df064-271">这些新功能允许你根据证书的 DNS 名称和到期日期搜索证书，并通过证书的增强型密钥使用 (EKU) 属性的值将客户端和服务器身份验证证书区分开来。</span><span class="sxs-lookup"><span data-stu-id="df064-271">These new features let you search for certificates based on their DNS names and expiration dates, and distinguish client and server authentication certificates by the value of their Enhanced Key Usage (EKU) properties.</span></span>

## <a name="using-the-pipeline"></a><span data-ttu-id="df064-272">使用管道</span><span class="sxs-lookup"><span data-stu-id="df064-272">Using the pipeline</span></span>

<span data-ttu-id="df064-273">提供程序 cmdlet 接受管道输入。</span><span class="sxs-lookup"><span data-stu-id="df064-273">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="df064-274">可以通过将提供程序数据从一个 cmdlet 发送到另一个提供程序 cmdlet 来使用管道来简化任务。</span><span class="sxs-lookup"><span data-stu-id="df064-274">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="df064-275">若要详细了解如何将管道与提供程序 cmdlet 配合使用，请参阅本文中提供的 cmdlet 参考。</span><span class="sxs-lookup"><span data-stu-id="df064-275">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="df064-276">获取帮助</span><span class="sxs-lookup"><span data-stu-id="df064-276">Getting help</span></span>

<span data-ttu-id="df064-277">从 Windows PowerShell 3.0 开始，你可以获取有关提供程序 cmdlet 的自定义帮助主题，它们介绍了这些 cmdlet 在文件系统驱动器中的行为方式。</span><span class="sxs-lookup"><span data-stu-id="df064-277">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="df064-278">若要获取针对文件系统驱动器进行自定义的帮助主题，请在文件系统驱动器中运行 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 命令，或使用的 `-Path` 参数 `Get-Help` 来指定文件系统驱动器。</span><span class="sxs-lookup"><span data-stu-id="df064-278">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of `Get-Help` to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path cert:
```

## <a name="see-also"></a><span data-ttu-id="df064-279">另请参阅</span><span class="sxs-lookup"><span data-stu-id="df064-279">See also</span></span>

[<span data-ttu-id="df064-280">about_Providers</span><span class="sxs-lookup"><span data-stu-id="df064-280">about_Providers</span></span>](../../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="df064-281">about_Signing</span><span class="sxs-lookup"><span data-stu-id="df064-281">about_Signing</span></span>](../../Microsoft.PowerShell.Core/About/about_Signing.md)

[<span data-ttu-id="df064-282">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="df064-282">Get-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)

[<span data-ttu-id="df064-283">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="df064-283">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

[<span data-ttu-id="df064-284">Get-PfxCertificate</span><span class="sxs-lookup"><span data-stu-id="df064-284">Get-PfxCertificate</span></span>](xref:Microsoft.PowerShell.Security.Get-PfxCertificate)
