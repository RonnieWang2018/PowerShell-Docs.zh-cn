---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WebRequest
ms.openlocfilehash: 09270fd74fd256858faacaae399e05b40985ddb5
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "93199288"
---
# <span data-ttu-id="2c025-103">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="2c025-103">Invoke-WebRequest</span></span>

## <span data-ttu-id="2c025-104">摘要</span><span class="sxs-lookup"><span data-stu-id="2c025-104">SYNOPSIS</span></span>
<span data-ttu-id="2c025-105">从 internet 上的网页中获取内容。</span><span class="sxs-lookup"><span data-stu-id="2c025-105">Gets content from a web page on the internet.</span></span>

## <span data-ttu-id="2c025-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2c025-106">SYNTAX</span></span>

### <span data-ttu-id="2c025-107">StandardMethod (默认值) </span><span class="sxs-lookup"><span data-stu-id="2c025-107">StandardMethod (Default)</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Method <WebRequestMethod>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="2c025-108">StandardMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="2c025-108">StandardMethodNoProxy</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Method <WebRequestMethod>] -NoProxy
 [-Body <Object>] [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>]
 [-InFile <String>] [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="2c025-109">CustomMethod</span><span class="sxs-lookup"><span data-stu-id="2c025-109">CustomMethod</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -CustomMethod <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="2c025-110">CustomMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="2c025-110">CustomMethodNoProxy</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -CustomMethod <String> -NoProxy
 [-Body <Object>] [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>]
 [-InFile <String>] [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

## <span data-ttu-id="2c025-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2c025-111">DESCRIPTION</span></span>

<span data-ttu-id="2c025-112">`Invoke-WebRequest`Cmdlet 将 HTTP 和 HTTPS 请求发送到网页或 web 服务。</span><span class="sxs-lookup"><span data-stu-id="2c025-112">The `Invoke-WebRequest` cmdlet sends HTTP and HTTPS requests to a web page or web service.</span></span> <span data-ttu-id="2c025-113">它分析响应并返回链接、图像和其他重要 HTML 元素的集合。</span><span class="sxs-lookup"><span data-stu-id="2c025-113">It parses the response and returns collections of links, images, and other significant HTML elements.</span></span>

<span data-ttu-id="2c025-114">此 cmdlet 是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="2c025-114">This cmdlet was introduced in PowerShell 3.0.</span></span>

## <span data-ttu-id="2c025-115">示例</span><span class="sxs-lookup"><span data-stu-id="2c025-115">EXAMPLES</span></span>

### <span data-ttu-id="2c025-116">示例1：发送 web 请求</span><span class="sxs-lookup"><span data-stu-id="2c025-116">Example 1: Send a web request</span></span>

<span data-ttu-id="2c025-117">此示例使用 `Invoke-WebRequest` cmdlet 向 Bing.com 站点发送 web 请求。</span><span class="sxs-lookup"><span data-stu-id="2c025-117">This example uses the `Invoke-WebRequest` cmdlet to send a web request to the Bing.com site.</span></span>

```powershell
$Response = Invoke-WebRequest -URI https://www.bing.com/search?q=how+many+feet+in+a+mile
$Response.InputFields | Where-Object {
    $_.name -like "* Value*"
} | Select-Object Name, Value
```

```Output
name       value
----       -----
From Value 1
To Value   5280
```

<span data-ttu-id="2c025-118">第一个命令发出请求，并将响应保存在 `$Response` 变量中。</span><span class="sxs-lookup"><span data-stu-id="2c025-118">The first command issues the request and saves the response in the `$Response` variable.</span></span>

<span data-ttu-id="2c025-119">第二个命令获取 **Name** 属性所喜欢的任何 **InputField** `"* Value"` 。</span><span class="sxs-lookup"><span data-stu-id="2c025-119">The second command gets any **InputField** where the **Name** property is like `"* Value"`.</span></span> <span data-ttu-id="2c025-120">筛选后的结果将通过管道传递到 `Select-Object` ，以选择 **名称** 和 **值** 属性。</span><span class="sxs-lookup"><span data-stu-id="2c025-120">The filtered results are piped to `Select-Object` to select the **Name** and **Value** properties.</span></span>

### <span data-ttu-id="2c025-121">示例2：使用有状态 web 服务</span><span class="sxs-lookup"><span data-stu-id="2c025-121">Example 2: Use a stateful web service</span></span>

<span data-ttu-id="2c025-122">此示例演示如何将 `Invoke-WebRequest` cmdlet 与有状态 web 服务一起使用。</span><span class="sxs-lookup"><span data-stu-id="2c025-122">This example shows how to use the `Invoke-WebRequest` cmdlet with a stateful web service.</span></span>

```powershell
$Body = @{
    User = 'jdoe'
    password = 'P@S$w0rd!'
}
$LoginResponse = Invoke-WebRequest 'https://www.contoso.com/login/' -SessionVariable 'Session' -Body $Body -Method 'POST'

$Session

$ProfileResponse = Invoke-WebRequest 'https://www.contoso.com/profile/' -WebSession $Session

$ProfileResponse
```

<span data-ttu-id="2c025-123">发送登录请求的第一次调用 `Invoke-WebRequest` 。</span><span class="sxs-lookup"><span data-stu-id="2c025-123">The first call to `Invoke-WebRequest` sends a sign-in request.</span></span> <span data-ttu-id="2c025-124">命令为 **-SessionVariable** 参数的值指定值 "Session"，并将结果保存在 `$LoginResponse` 变量中。</span><span class="sxs-lookup"><span data-stu-id="2c025-124">The command specifies a value of "Session" for the value of the **-SessionVariable** parameter, and saves the result in the `$LoginResponse` variable.</span></span> <span data-ttu-id="2c025-125">当该命令完成时， `$LoginResponse` 变量将包含 `BasicHtmlWebResponseObject` ，并且该 `$Session` 变量包含一个 `WebRequestSession` 对象。</span><span class="sxs-lookup"><span data-stu-id="2c025-125">When the command completes, the `$LoginResponse` variable contains an `BasicHtmlWebResponseObject` and the `$Session` variable contains a `WebRequestSession` object.</span></span> <span data-ttu-id="2c025-126">这会将用户记录到站点中。</span><span class="sxs-lookup"><span data-stu-id="2c025-126">This logs the user into the site.</span></span>

<span data-ttu-id="2c025-127">对的调用 `$Session` 本身显示 `WebRequestSession` 变量中的对象。</span><span class="sxs-lookup"><span data-stu-id="2c025-127">The call to `$Session` by itself shows the `WebRequestSession` object in the variable.</span></span>

<span data-ttu-id="2c025-128">第二次调用会 `Invoke-WebRequest` 提取用户的配置文件，要求用户登录到站点。</span><span class="sxs-lookup"><span data-stu-id="2c025-128">The second call to `Invoke-WebRequest` fetches the user's profile which requires that the user be logged into the site.</span></span> <span data-ttu-id="2c025-129">变量中存储的会话数据 `$Session` 用于向在登录时创建的站点提供会话 cookie。</span><span class="sxs-lookup"><span data-stu-id="2c025-129">The session data stored in the `$Session` variable is used to provide session cookies to the site created during the login.</span></span> <span data-ttu-id="2c025-130">结果保存在 `$ProfileResponse` 变量中。</span><span class="sxs-lookup"><span data-stu-id="2c025-130">The result is saved in the `$ProfileResponse` variable.</span></span>

<span data-ttu-id="2c025-131">对的调用 `$ProfileResponse` 本身显示 `BasicHtmlWebResponseObject` 变量中的。</span><span class="sxs-lookup"><span data-stu-id="2c025-131">The call to `$ProfileResponse` by itself shows the `BasicHtmlWebResponseObject` in the variable.</span></span>

### <span data-ttu-id="2c025-132">示例3：获取网页中的链接</span><span class="sxs-lookup"><span data-stu-id="2c025-132">Example 3: Get links from a web page</span></span>

<span data-ttu-id="2c025-133">此示例将获取网页中的链接。</span><span class="sxs-lookup"><span data-stu-id="2c025-133">This example gets the links in a web page.</span></span> <span data-ttu-id="2c025-134">它使用 `Invoke-WebRequest` cmdlet 来获取网页内容。</span><span class="sxs-lookup"><span data-stu-id="2c025-134">It uses the `Invoke-WebRequest` cmdlet to get the web page content.</span></span> <span data-ttu-id="2c025-135">然后，它使用 **Links** 返回的的 Links `BasicHtmlWebResponseObject` 属性 `Invoke-WebRequest` 和每个链接的 **Href** 属性。</span><span class="sxs-lookup"><span data-stu-id="2c025-135">Then it uses the **Links** property of the `BasicHtmlWebResponseObject` that `Invoke-WebRequest` returns, and the **Href** property of each link.</span></span>

```powershell
(Invoke-WebRequest -Uri "https://aka.ms/pscore6-docs").Links.Href
```

### <span data-ttu-id="2c025-136">示例4：使用请求页中定义的编码将响应内容写入文件。</span><span class="sxs-lookup"><span data-stu-id="2c025-136">Example 4: Writes the response content to a file using the encoding defined in the requested page.</span></span>

<span data-ttu-id="2c025-137">此示例使用 `Invoke-WebRequest` cmdlet 检索 PowerShell 文档页的网页内容。</span><span class="sxs-lookup"><span data-stu-id="2c025-137">This example uses the `Invoke-WebRequest` cmdlet to retrieve the web page content of a PowerShell documentation page.</span></span>

```powershell
$Response = Invoke-WebRequest -Uri "https://aka.ms/pscore6-docs"
$Stream = [System.IO.StreamWriter]::new('.\docspage.html', $false, $Response.Encoding)
try {
    $Stream.Write($Response.Content)
}
finally {
    $Stream.Dispose()
}
```

<span data-ttu-id="2c025-138">第一个命令检索页面，并将响应对象保存在 `$Response` 变量中。</span><span class="sxs-lookup"><span data-stu-id="2c025-138">The first command retrieves the page and saves the response object in the `$Response` variable.</span></span>

<span data-ttu-id="2c025-139">第二个命令创建用于将 `StreamWriter` 响应内容写入文件的。</span><span class="sxs-lookup"><span data-stu-id="2c025-139">The second command creates a `StreamWriter` to use to write the response content to a file.</span></span> <span data-ttu-id="2c025-140">响应对象的 " **编码** " 属性用于设置文件的编码。</span><span class="sxs-lookup"><span data-stu-id="2c025-140">The **Encoding** property of the response object is used to set the encoding for the file.</span></span>

<span data-ttu-id="2c025-141">最后几个命令将 **Content** 属性写入文件，然后释放 `StreamWriter` 。</span><span class="sxs-lookup"><span data-stu-id="2c025-141">The final few commands write the **Content** property to the file then disposes the `StreamWriter`.</span></span>

<span data-ttu-id="2c025-142">请注意，如果 web 请求未返回文本内容，则 **编码** 属性为 null。</span><span class="sxs-lookup"><span data-stu-id="2c025-142">Note that the **Encoding** property is null if the web request doesn't return text content.</span></span>

### <span data-ttu-id="2c025-143">示例5：提交多部分/窗体数据文件</span><span class="sxs-lookup"><span data-stu-id="2c025-143">Example 5: Submit a multipart/form-data file</span></span>

<span data-ttu-id="2c025-144">此示例使用 `Invoke-WebRequest` cmdlet 将文件上传为 `multipart/form-data` 提交。</span><span class="sxs-lookup"><span data-stu-id="2c025-144">This example uses the `Invoke-WebRequest` cmdlet upload a file as a `multipart/form-data` submission.</span></span> <span data-ttu-id="2c025-145">文件 `c:\document.txt` 将作为的窗体字段进行提交 `document` `Content-Type` `text/plain` 。</span><span class="sxs-lookup"><span data-stu-id="2c025-145">The file `c:\document.txt` is submitted as the form field `document` with the `Content-Type` of `text/plain`.</span></span>

```powershell
$FilePath = 'c:\document.txt'
$FieldName = 'document'
$ContentType = 'text/plain'

$FileStream = [System.IO.FileStream]::new($filePath, [System.IO.FileMode]::Open)
$FileHeader = [System.Net.Http.Headers.ContentDispositionHeaderValue]::new('form-data')
$FileHeader.Name = $FieldName
$FileHeader.FileName = Split-Path -leaf $FilePath
$FileContent = [System.Net.Http.StreamContent]::new($FileStream)
$FileContent.Headers.ContentDisposition = $FileHeader
$FileContent.Headers.ContentType = [System.Net.Http.Headers.MediaTypeHeaderValue]::Parse($ContentType)

$MultipartContent = [System.Net.Http.MultipartFormDataContent]::new()
$MultipartContent.Add($FileContent)

$Response = Invoke-WebRequest -Body $MultipartContent -Method 'POST' -Uri 'https://api.contoso.com/upload'
```

### <span data-ttu-id="2c025-146">示例6：简化的多部分/表单数据提交</span><span class="sxs-lookup"><span data-stu-id="2c025-146">Example 6: Simplified Multipart/Form-Data Submission</span></span>

<span data-ttu-id="2c025-147">某些 Api 需要 `multipart/form-data` 提交来上传文件和混合内容。</span><span class="sxs-lookup"><span data-stu-id="2c025-147">Some APIs require `multipart/form-data` submissions to upload files and mixed content.</span></span> <span data-ttu-id="2c025-148">此示例演示如何更新用户配置文件。</span><span class="sxs-lookup"><span data-stu-id="2c025-148">This example demonstrates updating a user profile.</span></span>

```powershell
$Uri = 'https://api.contoso.com/v2/profile'
$Form = @{
    firstName  = 'John'
    lastName   = 'Doe'
    email      = 'john.doe@contoso.com'
    avatar     = Get-Item -Path 'c:\Pictures\jdoe.png'
    birthday   = '1980-10-15'
    hobbies    = 'Hiking','Fishing','Jogging'
}
$Result = Invoke-WebRequest -Uri $Uri -Method Post -Form $Form
```

<span data-ttu-id="2c025-149">配置文件窗体需要以下字段： `firstName` 、 `lastName` 、、、 `email` `avatar` `birthday` 和 `hobbies` 。</span><span class="sxs-lookup"><span data-stu-id="2c025-149">The profile form requires these fields: `firstName`, `lastName`, `email`, `avatar`, `birthday`, and `hobbies`.</span></span> <span data-ttu-id="2c025-150">该 API 需要在字段中提供用户配置文件 pic 的映像 `avatar` 。</span><span class="sxs-lookup"><span data-stu-id="2c025-150">The API is expecting an image for the user profile pic to be supplied in the `avatar` field.</span></span> <span data-ttu-id="2c025-151">该 API 还接受 `hobbies` 同一窗体中提交的多个条目。</span><span class="sxs-lookup"><span data-stu-id="2c025-151">The API also accepts multiple `hobbies` entries to be submitted in the same form.</span></span>

<span data-ttu-id="2c025-152">创建 `$Form` 哈希表时，键名称将用作窗体字段名称。</span><span class="sxs-lookup"><span data-stu-id="2c025-152">When creating the `$Form` HashTable, the key names are used as form field names.</span></span> <span data-ttu-id="2c025-153">默认情况下，哈希表的值将转换为字符串。</span><span class="sxs-lookup"><span data-stu-id="2c025-153">By default, the values of the HashTable are converted to strings.</span></span> <span data-ttu-id="2c025-154">如果存在 **FileInfo** 值，则提交文件内容。</span><span class="sxs-lookup"><span data-stu-id="2c025-154">If a **System.IO.FileInfo** value is present, the file contents are submitted.</span></span> <span data-ttu-id="2c025-155">如果存在数组或列表这样的集合，则将多次提交窗体字段。</span><span class="sxs-lookup"><span data-stu-id="2c025-155">If a collection such as arrays or lists are present, the form field is submitted multiple times.</span></span>

<span data-ttu-id="2c025-156">通过 `Get-Item` 对键使用 `avatar` ，将 `FileInfo` 对象设置为值。</span><span class="sxs-lookup"><span data-stu-id="2c025-156">By using `Get-Item` on the `avatar` key, the `FileInfo` object is set as the value.</span></span> <span data-ttu-id="2c025-157">结果就是提交的图像数据 `jdoe.png` 。</span><span class="sxs-lookup"><span data-stu-id="2c025-157">The result is that the image data for `jdoe.png` is submitted.</span></span>

<span data-ttu-id="2c025-158">通过向键提供一个列表 `hobbies` ， `hobbies` 每个列表项的提交一次中都有该字段。</span><span class="sxs-lookup"><span data-stu-id="2c025-158">By supplying a list to the `hobbies` key, the `hobbies` field is present in the submissions once for each list item.</span></span>

### <span data-ttu-id="2c025-159">示例7：从 Invoke-WebRequest 中捕获非成功消息</span><span class="sxs-lookup"><span data-stu-id="2c025-159">Example 7: Catch non success messages from Invoke-WebRequest</span></span>

<span data-ttu-id="2c025-160">如果 `Invoke-WebRequest` 遇到非成功 HTTP 消息 (404、500等 ) ，它将不返回任何输出，并引发终止错误。</span><span class="sxs-lookup"><span data-stu-id="2c025-160">When `Invoke-WebRequest` encounters a non-success HTTP message (404, 500, etc.), it returns no output and throws a terminating error.</span></span> <span data-ttu-id="2c025-161">若要捕获错误并查看 **StatusCode** ，可以在块中包含执行 `try/catch` 。</span><span class="sxs-lookup"><span data-stu-id="2c025-161">To catch the error and view the **StatusCode** you can enclose execution in a `try/catch` block.</span></span>

```powershell
try
{
    $Response = Invoke-WebRequest -Uri "www.microsoft.com/unkownhost" -ErrorAction Stop
    # This will only execute if the Invoke-WebRequest is successful.
    $StatusCode = $Response.StatusCode
}
catch
{
    $StatusCode = $_.Exception.Response.StatusCode.value__
}
$StatusCode
```

```Output
404
```

<span data-ttu-id="2c025-162">命令调用的 `Invoke-WebRequest` **ErrorAction** 为 **Stop** ，这会强制 `Invoke-WebRequest` 对任何失败的请求引发终止错误。</span><span class="sxs-lookup"><span data-stu-id="2c025-162">The command calls `Invoke-WebRequest` with an **ErrorAction** of **Stop** , which forces `Invoke-WebRequest` to throw a terminating error on any failed requests.</span></span> <span data-ttu-id="2c025-163">终止错误由 `catch` 从 **异常** 对象检索 **StatusCode** 的块捕获。</span><span class="sxs-lookup"><span data-stu-id="2c025-163">The terminating error is caught by the `catch` block which retrieves the **StatusCode** from the **Exception** object.</span></span>

## <span data-ttu-id="2c025-164">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2c025-164">PARAMETERS</span></span>

### <span data-ttu-id="2c025-165">-AllowUnencryptedAuthentication</span><span class="sxs-lookup"><span data-stu-id="2c025-165">-AllowUnencryptedAuthentication</span></span>

<span data-ttu-id="2c025-166">允许通过未加密的连接发送凭据和密码。</span><span class="sxs-lookup"><span data-stu-id="2c025-166">Allows sending of credentials and secrets over unencrypted connections.</span></span> <span data-ttu-id="2c025-167">默认情况下，如果提供 **凭据** 或任何具有不以开头的 **Uri** 的 **身份验证** 选项，将 `https://` 会导致错误，请求会中止，以防止无意中以纯文本方式在未加密的连接上传递机密。</span><span class="sxs-lookup"><span data-stu-id="2c025-167">By default, supplying **Credential** or any **Authentication** option with a **Uri** that does not begin with `https://` results in an error and the request is aborted to prevent unintentionally communicating secrets in plain text over unencrypted connections.</span></span> <span data-ttu-id="2c025-168">若要重写此行为，需自行承担相应的风险，请提供 **AllowUnencryptedAuthentication** 参数。</span><span class="sxs-lookup"><span data-stu-id="2c025-168">To override this behavior at your own risk, supply the **AllowUnencryptedAuthentication** parameter.</span></span>

> [!WARNING]
> <span data-ttu-id="2c025-169">使用此参数并不安全，不建议使用。</span><span class="sxs-lookup"><span data-stu-id="2c025-169">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="2c025-170">提供它只是为了与无法提供加密连接的旧系统兼容。</span><span class="sxs-lookup"><span data-stu-id="2c025-170">It is provided only for compatibility with legacy systems that cannot provide encrypted connections.</span></span> <span data-ttu-id="2c025-171">使用自己的风险。</span><span class="sxs-lookup"><span data-stu-id="2c025-171">Use at your own risk.</span></span>

<span data-ttu-id="2c025-172">此功能已添加到 PowerShell 6.0.0。</span><span class="sxs-lookup"><span data-stu-id="2c025-172">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="2c025-173">-Authentication</span><span class="sxs-lookup"><span data-stu-id="2c025-173">-Authentication</span></span>

<span data-ttu-id="2c025-174">指定要用于请求的显式身份验证类型。</span><span class="sxs-lookup"><span data-stu-id="2c025-174">Specifies the explicit authentication type to use for the request.</span></span> <span data-ttu-id="2c025-175">默认值为“无”。</span><span class="sxs-lookup"><span data-stu-id="2c025-175">The default is **None** .</span></span>
<span data-ttu-id="2c025-176">**身份验证** 不能与 **UseDefaultCredentials** 一起使用。</span><span class="sxs-lookup"><span data-stu-id="2c025-176">**Authentication** cannot be used with **UseDefaultCredentials** .</span></span>

<span data-ttu-id="2c025-177">可用的身份验证选项：</span><span class="sxs-lookup"><span data-stu-id="2c025-177">Available Authentication Options:</span></span>

- <span data-ttu-id="2c025-178">**无** ：这是未提供 **身份验证** 时的默认选项;不使用显式身份验证。</span><span class="sxs-lookup"><span data-stu-id="2c025-178">**None** : This is the default option when **Authentication** isn't supplied; no explicit authentication is used.</span></span>
- <span data-ttu-id="2c025-179">**基本** ：需要 **凭据** 。</span><span class="sxs-lookup"><span data-stu-id="2c025-179">**Basic** : Requires **Credential** .</span></span> <span data-ttu-id="2c025-180">凭据以的格式在 RFC 7617 基本身份验证标头中发送 `base64(user:password)` 。</span><span class="sxs-lookup"><span data-stu-id="2c025-180">The credentials are sent in an RFC 7617 Basic Authentication header in the format of `base64(user:password)`.</span></span>
- <span data-ttu-id="2c025-181">**持有** 者：需要 **标记** 。</span><span class="sxs-lookup"><span data-stu-id="2c025-181">**Bearer** : Requires **Token** .</span></span> <span data-ttu-id="2c025-182">`Authorization: Bearer`使用提供的令牌发送 RFC 6750 标头。</span><span class="sxs-lookup"><span data-stu-id="2c025-182">Sends an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="2c025-183">这是 **OAuth** 的别名</span><span class="sxs-lookup"><span data-stu-id="2c025-183">This is an alias for **OAuth**</span></span>
- <span data-ttu-id="2c025-184">**OAuth** ：需要 **标记** 。</span><span class="sxs-lookup"><span data-stu-id="2c025-184">**OAuth** : Requires **Token** .</span></span> <span data-ttu-id="2c025-185">`Authorization: Bearer`使用提供的令牌发送 RFC 6750 标头。</span><span class="sxs-lookup"><span data-stu-id="2c025-185">Sends an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="2c025-186">这是 **持有** 者的别名</span><span class="sxs-lookup"><span data-stu-id="2c025-186">This is an alias for **Bearer**</span></span>

<span data-ttu-id="2c025-187">提供 **身份验证** `Authorization` 将覆盖提供给 **标头** 或包含在 **WebSession** 中的任何标头。</span><span class="sxs-lookup"><span data-stu-id="2c025-187">Supplying **Authentication** overrides any `Authorization` headers supplied to **Headers** or included in **WebSession** .</span></span>

<span data-ttu-id="2c025-188">此功能已添加到 PowerShell 6.0.0。</span><span class="sxs-lookup"><span data-stu-id="2c025-188">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WebAuthenticationType
Parameter Sets: (All)
Aliases:
Accepted values: None, Basic, Bearer, OAuth

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c025-189">-Body</span><span class="sxs-lookup"><span data-stu-id="2c025-189">-Body</span></span>

<span data-ttu-id="2c025-190">指定请求的正文。</span><span class="sxs-lookup"><span data-stu-id="2c025-190">Specifies the body of the request.</span></span> <span data-ttu-id="2c025-191">正文是请求的内容，位于标头之后。</span><span class="sxs-lookup"><span data-stu-id="2c025-191">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="2c025-192">还可以通过管道将正文值传递给 `Invoke-WebRequest` 。</span><span class="sxs-lookup"><span data-stu-id="2c025-192">You can also pipe a body value to `Invoke-WebRequest`.</span></span>

<span data-ttu-id="2c025-193">可以将 **Body** 参数用于指定查询参数的列表，或用于指定响应的内容。</span><span class="sxs-lookup"><span data-stu-id="2c025-193">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="2c025-194">如果输入是 GET 请求且正文是 `IDictionary` (通常是) 哈希表，则会将正文作为查询参数添加到 URI 中。</span><span class="sxs-lookup"><span data-stu-id="2c025-194">When the input is a GET request and the body is an `IDictionary` (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="2c025-195">对于其他请求类型 (如 POST) ，主体将设置为标准格式的请求正文的值 `name=value` 。</span><span class="sxs-lookup"><span data-stu-id="2c025-195">For other request types (such as POST), the body is set as the value of the request body in the standard `name=value` format.</span></span>

<span data-ttu-id="2c025-196">**Body** 参数还可以接受一个 `System.Net.Http.MultipartFormDataContent` 对象。</span><span class="sxs-lookup"><span data-stu-id="2c025-196">The **Body** parameter may also accept a `System.Net.Http.MultipartFormDataContent` object.</span></span> <span data-ttu-id="2c025-197">这便于 `multipart/form-data` 请求。</span><span class="sxs-lookup"><span data-stu-id="2c025-197">This facilitates `multipart/form-data` requests.</span></span> <span data-ttu-id="2c025-198">为 **正文** 提供 **MultipartFormDataContent** 对象时，提供给 **ContentType** 、 **标头** 或 **WebSession** 参数的任何相关标题的任何内容都将被 **MultipartFormDataContent** 对象的内容标头重写。</span><span class="sxs-lookup"><span data-stu-id="2c025-198">When a **MultipartFormDataContent** object is supplied for **Body** , any Content related headers supplied to the **ContentType** , **Headers** , or **WebSession** parameters is overridden by the Content headers of the **MultipartFormDataContent** object.</span></span> <span data-ttu-id="2c025-199">此功能已添加到 PowerShell 6.0.0。</span><span class="sxs-lookup"><span data-stu-id="2c025-199">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2c025-200">-Certificate</span><span class="sxs-lookup"><span data-stu-id="2c025-200">-Certificate</span></span>

<span data-ttu-id="2c025-201">指定用于安全的 web 请求的客户端证书。</span><span class="sxs-lookup"><span data-stu-id="2c025-201">Specifies the client certificate that's used for a secure web request.</span></span> <span data-ttu-id="2c025-202">输入一个包含证书的变量，或可获取该证书的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="2c025-202">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="2c025-203">若要查找证书，请使用 `Get-PfxCertificate` 或使用 `Get-ChildItem` 证书 () 驱动器中的 cmdlet `Cert:` 。</span><span class="sxs-lookup"><span data-stu-id="2c025-203">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate (`Cert:`) drive.</span></span> <span data-ttu-id="2c025-204">如果证书无效或没有足够的权限，则该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="2c025-204">If the certificate isn't valid or doesn't have sufficient authority, the command fails.</span></span>

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c025-205">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="2c025-205">-CertificateThumbprint</span></span>

<span data-ttu-id="2c025-206">指定有权发送请求的用户帐户的数字公钥证书 (X509)。</span><span class="sxs-lookup"><span data-stu-id="2c025-206">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="2c025-207">输入证书的证书指纹。</span><span class="sxs-lookup"><span data-stu-id="2c025-207">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="2c025-208">在基于客户端证书的身份验证中使用证书。</span><span class="sxs-lookup"><span data-stu-id="2c025-208">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="2c025-209">它们只能映射到本地用户帐户;它们不适用于域帐户。</span><span class="sxs-lookup"><span data-stu-id="2c025-209">They can be mapped only to local user accounts; they don't work with domain accounts.</span></span>

<span data-ttu-id="2c025-210">若要获取证书指纹，请使用 `Get-Item` `Get-ChildItem` PowerShell 驱动器中的或命令 `Cert:` 。</span><span class="sxs-lookup"><span data-stu-id="2c025-210">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

> [!NOTE]
> <span data-ttu-id="2c025-211">目前只有 Windows 操作系统平台支持此功能。</span><span class="sxs-lookup"><span data-stu-id="2c025-211">This feature is currently only supported on Windows OS platforms.</span></span>

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

### <span data-ttu-id="2c025-212">-ContentType</span><span class="sxs-lookup"><span data-stu-id="2c025-212">-ContentType</span></span>

<span data-ttu-id="2c025-213">指定 Web 请求的内容类型。</span><span class="sxs-lookup"><span data-stu-id="2c025-213">Specifies the content type of the web request.</span></span>

<span data-ttu-id="2c025-214">如果省略此参数且请求方法为 POST，则 `Invoke-WebRequest` 将内容类型设置为 `application/x-www-form-urlencoded` 。</span><span class="sxs-lookup"><span data-stu-id="2c025-214">If this parameter is omitted and the request method is POST, `Invoke-WebRequest` sets the content type to `application/x-www-form-urlencoded`.</span></span> <span data-ttu-id="2c025-215">否则，不会在调用中指定内容类型。</span><span class="sxs-lookup"><span data-stu-id="2c025-215">Otherwise, the content type isn't specified in the call.</span></span>

<span data-ttu-id="2c025-216">为 **正文** 提供 **MultipartFormDataContent** 对象时，会重写 **ContentType** 。</span><span class="sxs-lookup"><span data-stu-id="2c025-216">**ContentType** is overridden when a **MultipartFormDataContent** object is supplied for **Body** .</span></span>

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

### <span data-ttu-id="2c025-217">-Credential</span><span class="sxs-lookup"><span data-stu-id="2c025-217">-Credential</span></span>

<span data-ttu-id="2c025-218">指定有权发送请求的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="2c025-218">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="2c025-219">默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="2c025-219">The default is the current user.</span></span>

<span data-ttu-id="2c025-220">键入用户名（如 **User01** 或 **Domain01\User01** ），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="2c025-220">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="2c025-221">**凭据** 可以单独使用，也可以与某些 **身份验证** 参数选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="2c025-221">**Credential** can be used alone or in conjunction with certain **Authentication** parameter options.</span></span> <span data-ttu-id="2c025-222">当远程服务器发送身份验证质询请求时，它仅向远程服务器提供凭据。</span><span class="sxs-lookup"><span data-stu-id="2c025-222">When used alone, it only supplies credentials to the remote server if the remote server sends an authentication challenge request.</span></span> <span data-ttu-id="2c025-223">与 **身份验证** 选项一起使用时，会显式发送凭据。</span><span class="sxs-lookup"><span data-stu-id="2c025-223">When used with **Authentication** options, the credentials are explicitly sent.</span></span>

<span data-ttu-id="2c025-224">凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="2c025-224">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="2c025-225">有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="2c025-225">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c025-226">-CustomMethod</span><span class="sxs-lookup"><span data-stu-id="2c025-226">-CustomMethod</span></span>

<span data-ttu-id="2c025-227">指定用于 web 请求的自定义方法。</span><span class="sxs-lookup"><span data-stu-id="2c025-227">Specifies a custom method used for the web request.</span></span> <span data-ttu-id="2c025-228">如果终结点所需的请求方法不可用于 **方法** ，则可以使用此方法。</span><span class="sxs-lookup"><span data-stu-id="2c025-228">This can be used if the Request Method required by the endpoint isn't an available option on the **Method** .</span></span> <span data-ttu-id="2c025-229">**方法** 和 **CustomMethod** 不能一起使用。</span><span class="sxs-lookup"><span data-stu-id="2c025-229">**Method** and **CustomMethod** can't be used together.</span></span>

<span data-ttu-id="2c025-230">此示例 `TEST` 向 API 发出 HTTP 请求：</span><span class="sxs-lookup"><span data-stu-id="2c025-230">This example makes a `TEST` HTTP request to the API:</span></span>

`Invoke-WebRequest -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

<span data-ttu-id="2c025-231">此功能已添加到 PowerShell 6.0.0。</span><span class="sxs-lookup"><span data-stu-id="2c025-231">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: System.String
Parameter Sets: CustomMethodNoProxy, CustomMethod
Aliases: CM

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c025-232">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="2c025-232">-DisableKeepAlive</span></span>

<span data-ttu-id="2c025-233">指示该 cmdlet 将 HTTP 头中的 **KeepAlive** 值设置为 **False** 。</span><span class="sxs-lookup"><span data-stu-id="2c025-233">Indicates that the cmdlet sets the **KeepAlive** value in the HTTP header to **False** .</span></span> <span data-ttu-id="2c025-234">默认情况下， **KeepAlive** 为 **True** 。</span><span class="sxs-lookup"><span data-stu-id="2c025-234">By default, **KeepAlive** is **True** .</span></span> <span data-ttu-id="2c025-235">**KeepAlive** 建立到服务器的持续性连接，以促进后续请求。</span><span class="sxs-lookup"><span data-stu-id="2c025-235">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="2c025-236">-窗体</span><span class="sxs-lookup"><span data-stu-id="2c025-236">-Form</span></span>

<span data-ttu-id="2c025-237">将字典转换为 `multipart/form-data` 提交。</span><span class="sxs-lookup"><span data-stu-id="2c025-237">Converts a dictionary to a `multipart/form-data` submission.</span></span> <span data-ttu-id="2c025-238">**窗体** 不能与 **正文** 一起使用。</span><span class="sxs-lookup"><span data-stu-id="2c025-238">**Form** may not be used with **Body** .</span></span>
<span data-ttu-id="2c025-239">如果使用 **ContentType** ，则会将其忽略。</span><span class="sxs-lookup"><span data-stu-id="2c025-239">If **ContentType** is used, it's ignored.</span></span>

<span data-ttu-id="2c025-240">字典的键用作窗体字段名称。</span><span class="sxs-lookup"><span data-stu-id="2c025-240">The keys of the dictionary are used as the form field names.</span></span> <span data-ttu-id="2c025-241">默认情况下，窗体值将转换为字符串值。</span><span class="sxs-lookup"><span data-stu-id="2c025-241">By default, form values are converted to string values.</span></span>

<span data-ttu-id="2c025-242">如果值是 **FileInfo** 对象，则会提交二进制文件内容。</span><span class="sxs-lookup"><span data-stu-id="2c025-242">If the value is a **System.IO.FileInfo** object, then the binary file contents are submitted.</span></span> <span data-ttu-id="2c025-243">文件的名称将作为 **filename** 属性提交。</span><span class="sxs-lookup"><span data-stu-id="2c025-243">The name of the file is submitted as the **filename** property.</span></span> <span data-ttu-id="2c025-244">MIME 类型设置为 `application/octet-stream` 。</span><span class="sxs-lookup"><span data-stu-id="2c025-244">The MIME type is set as `application/octet-stream`.</span></span> <span data-ttu-id="2c025-245">`Get-Item` 可用于简化 **FileInfo** 对象的提供。</span><span class="sxs-lookup"><span data-stu-id="2c025-245">`Get-Item` can be used to simplify supplying the **System.IO.FileInfo** object.</span></span>

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

<span data-ttu-id="2c025-246">如果值是集合类型（如数组或列表），则将多次提交 for 字段。</span><span class="sxs-lookup"><span data-stu-id="2c025-246">If the value is a collection type, such Arrays or Lists, the for field are submitted multiple times.</span></span>
<span data-ttu-id="2c025-247">默认情况下，列表的值被视为字符串。</span><span class="sxs-lookup"><span data-stu-id="2c025-247">The values of the list are treated as strings by default.</span></span> <span data-ttu-id="2c025-248">如果值是 **FileInfo** 对象，则会提交二进制文件内容。</span><span class="sxs-lookup"><span data-stu-id="2c025-248">If the value is a **System.IO.FileInfo** object, then the binary file contents are submitted.</span></span> <span data-ttu-id="2c025-249">嵌套集合不受支持。</span><span class="sxs-lookup"><span data-stu-id="2c025-249">Nested collections aren't supported.</span></span>

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

<span data-ttu-id="2c025-250">在上面的示例中， `tags` 字段在窗体中提供三次，一次用于 `Vacation` 、 `Italy` 和 `2017` 。</span><span class="sxs-lookup"><span data-stu-id="2c025-250">In the above example the `tags` field are supplied three times in the form, once for each of `Vacation`, `Italy`, and `2017`.</span></span> <span data-ttu-id="2c025-251">`pictures`对于文件夹中的每个文件，该字段也会提交一次 `2017-Italy` 。</span><span class="sxs-lookup"><span data-stu-id="2c025-251">The `pictures` field is also submitted once for each file in the `2017-Italy` folder.</span></span> <span data-ttu-id="2c025-252">将该文件夹中的文件的二进制内容提交为值。</span><span class="sxs-lookup"><span data-stu-id="2c025-252">The binary contents of the files in that folder are submitted as the values.</span></span>

<span data-ttu-id="2c025-253">此功能已添加到 PowerShell 6.1.0。</span><span class="sxs-lookup"><span data-stu-id="2c025-253">This feature was added in PowerShell 6.1.0.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c025-254">-标头</span><span class="sxs-lookup"><span data-stu-id="2c025-254">-Headers</span></span>

<span data-ttu-id="2c025-255">指定 Web 请求的标头。</span><span class="sxs-lookup"><span data-stu-id="2c025-255">Specifies the headers of the web request.</span></span> <span data-ttu-id="2c025-256">输入哈希表或字典。</span><span class="sxs-lookup"><span data-stu-id="2c025-256">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="2c025-257">若要设置 UserAgent 标头，请使用 **UserAgent** 参数。</span><span class="sxs-lookup"><span data-stu-id="2c025-257">To set UserAgent headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="2c025-258">不能使用此参数指定 **用户代理** 或 cookie 标头。</span><span class="sxs-lookup"><span data-stu-id="2c025-258">You can't use this parameter to specify **User-Agent** or cookie headers.</span></span>

<span data-ttu-id="2c025-259">为 `Content-Type` **正文** 提供 **MultipartFormDataContent** 对象时，会重写与内容相关的标头（例如）。</span><span class="sxs-lookup"><span data-stu-id="2c025-259">Content related headers, such as `Content-Type` is overridden when a **MultipartFormDataContent** object is supplied for **Body** .</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c025-260">-InFile</span><span class="sxs-lookup"><span data-stu-id="2c025-260">-InFile</span></span>

<span data-ttu-id="2c025-261">从文件中获取 Web 请求的内容。</span><span class="sxs-lookup"><span data-stu-id="2c025-261">Gets the content of the web request from a file.</span></span> <span data-ttu-id="2c025-262">请输入路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="2c025-262">Enter a path and file name.</span></span> <span data-ttu-id="2c025-263">如果省略路径，则默认路径为当前位置。</span><span class="sxs-lookup"><span data-stu-id="2c025-263">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="2c025-264">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="2c025-264">-MaximumRedirection</span></span>

<span data-ttu-id="2c025-265">指定在连接失败之前，PowerShell 将连接重定向到备用统一资源标识符 (URI) 的次数。</span><span class="sxs-lookup"><span data-stu-id="2c025-265">Specifies how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="2c025-266">默认值为 5。</span><span class="sxs-lookup"><span data-stu-id="2c025-266">The default value is 5.</span></span> <span data-ttu-id="2c025-267">值为 0（零）将阻止所有重定向。</span><span class="sxs-lookup"><span data-stu-id="2c025-267">A value of 0 (zero) prevents all redirection.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c025-268">-MaximumRetryCount</span><span class="sxs-lookup"><span data-stu-id="2c025-268">-MaximumRetryCount</span></span>

<span data-ttu-id="2c025-269">指定在收到400与599（含）或304之间的失败代码时，PowerShell 重试连接的次数。</span><span class="sxs-lookup"><span data-stu-id="2c025-269">Specifies how many times PowerShell retries a connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="2c025-270">另请参阅 **RetryIntervalSec** 参数以指定重试次数。</span><span class="sxs-lookup"><span data-stu-id="2c025-270">Also see **RetryIntervalSec** parameter for specifying number of retries.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c025-271">-方法</span><span class="sxs-lookup"><span data-stu-id="2c025-271">-Method</span></span>

<span data-ttu-id="2c025-272">指定用于 Web 请求的方法。</span><span class="sxs-lookup"><span data-stu-id="2c025-272">Specifies the method used for the web request.</span></span> <span data-ttu-id="2c025-273">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="2c025-273">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="2c025-274">默认</span><span class="sxs-lookup"><span data-stu-id="2c025-274">Default</span></span>
- <span data-ttu-id="2c025-275">删除</span><span class="sxs-lookup"><span data-stu-id="2c025-275">Delete</span></span>
- <span data-ttu-id="2c025-276">获取</span><span class="sxs-lookup"><span data-stu-id="2c025-276">Get</span></span>
- <span data-ttu-id="2c025-277">Head</span><span class="sxs-lookup"><span data-stu-id="2c025-277">Head</span></span>
- <span data-ttu-id="2c025-278">合并</span><span class="sxs-lookup"><span data-stu-id="2c025-278">Merge</span></span>
- <span data-ttu-id="2c025-279">选项</span><span class="sxs-lookup"><span data-stu-id="2c025-279">Options</span></span>
- <span data-ttu-id="2c025-280">修补程序</span><span class="sxs-lookup"><span data-stu-id="2c025-280">Patch</span></span>
- <span data-ttu-id="2c025-281">邮递</span><span class="sxs-lookup"><span data-stu-id="2c025-281">Post</span></span>
- <span data-ttu-id="2c025-282">Put</span><span class="sxs-lookup"><span data-stu-id="2c025-282">Put</span></span>
- <span data-ttu-id="2c025-283">跟踪</span><span class="sxs-lookup"><span data-stu-id="2c025-283">Trace</span></span>

<span data-ttu-id="2c025-284">**CustomMethod** 参数可用于上面未列出的请求方法。</span><span class="sxs-lookup"><span data-stu-id="2c025-284">The **CustomMethod** parameter can be used for Request Methods not listed above.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WebRequestMethod
Parameter Sets: StandardMethod, StandardMethodNoProxy
Aliases:
Accepted values: Default, Get, Head, Post, Put, Delete, Trace, Options, Merge, Patch

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c025-285">-NoProxy</span><span class="sxs-lookup"><span data-stu-id="2c025-285">-NoProxy</span></span>

<span data-ttu-id="2c025-286">指示 cmdlet 不应使用代理来访问目标。</span><span class="sxs-lookup"><span data-stu-id="2c025-286">Indicates that the cmdlet shouldn't use a proxy to reach the destination.</span></span> <span data-ttu-id="2c025-287">如果需要绕过环境中配置的代理，请使用此开关。</span><span class="sxs-lookup"><span data-stu-id="2c025-287">When you need to bypass the proxy configured in the environment, use this switch.</span></span> <span data-ttu-id="2c025-288">此功能已添加到 PowerShell 6.0.0。</span><span class="sxs-lookup"><span data-stu-id="2c025-288">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StandardMethodNoProxy, CustomMethodNoProxy
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c025-289">-OutFile</span><span class="sxs-lookup"><span data-stu-id="2c025-289">-OutFile</span></span>

<span data-ttu-id="2c025-290">指定此 cmdlet 为其保存响应正文的输出文件。</span><span class="sxs-lookup"><span data-stu-id="2c025-290">Specifies the output file for which this cmdlet saves the response body.</span></span> <span data-ttu-id="2c025-291">请输入路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="2c025-291">Enter a path and file name.</span></span>
<span data-ttu-id="2c025-292">如果省略路径，则默认路径为当前位置。</span><span class="sxs-lookup"><span data-stu-id="2c025-292">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="2c025-293">默认情况下，将 `Invoke-WebRequest` 结果返回到管道。</span><span class="sxs-lookup"><span data-stu-id="2c025-293">By default, `Invoke-WebRequest` returns the results to the pipeline.</span></span> <span data-ttu-id="2c025-294">若要将这些结果发送到文件和管道，请使用 **Passthru** 参数。</span><span class="sxs-lookup"><span data-stu-id="2c025-294">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="2c025-295">-PassThru</span><span class="sxs-lookup"><span data-stu-id="2c025-295">-PassThru</span></span>

<span data-ttu-id="2c025-296">指示除了将结果写入文件外，该 cmdlet 还会返回结果。</span><span class="sxs-lookup"><span data-stu-id="2c025-296">Indicates that the cmdlet returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="2c025-297">仅当命令中还使用了 **OutFile** 参数时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="2c025-297">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="2c025-298">-PreserveAuthorizationOnRedirect</span><span class="sxs-lookup"><span data-stu-id="2c025-298">-PreserveAuthorizationOnRedirect</span></span>

<span data-ttu-id="2c025-299">指示 cmdlet 应在重定向中保留 `Authorization` 标头（如果存在）。</span><span class="sxs-lookup"><span data-stu-id="2c025-299">Indicates the cmdlet should preserve the `Authorization` header, when present, across redirections.</span></span>

<span data-ttu-id="2c025-300">默认情况下，该 cmdlet 会 `Authorization` 在重定向前去除标头。</span><span class="sxs-lookup"><span data-stu-id="2c025-300">By default, the cmdlet strips the `Authorization` header before redirecting.</span></span> <span data-ttu-id="2c025-301">如果指定此参数，则会在需要将标头发送到重定向位置的情况下禁用此逻辑。</span><span class="sxs-lookup"><span data-stu-id="2c025-301">Specifying this parameter disables this logic for cases where the header needs to be sent to the redirection location.</span></span>

<span data-ttu-id="2c025-302">此功能已添加到 PowerShell 6.0.0。</span><span class="sxs-lookup"><span data-stu-id="2c025-302">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="2c025-303">-Proxy</span><span class="sxs-lookup"><span data-stu-id="2c025-303">-Proxy</span></span>

<span data-ttu-id="2c025-304">为请求指定代理服务器，而不是直接连接到 internet 资源。</span><span class="sxs-lookup"><span data-stu-id="2c025-304">Specifies a proxy server for the request, rather than connecting directly to the internet resource.</span></span>
<span data-ttu-id="2c025-305">输入网络代理服务器的 URI。</span><span class="sxs-lookup"><span data-stu-id="2c025-305">Enter the URI of a network proxy server.</span></span>

```yaml
Type: System.Uri
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c025-306">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="2c025-306">-ProxyCredential</span></span>

<span data-ttu-id="2c025-307">指定有权使用由 **Proxy** 参数指定的代理服务器的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="2c025-307">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="2c025-308">默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="2c025-308">The default is the current user.</span></span>

<span data-ttu-id="2c025-309">键入用户名（如 **User01** 或 **Domain01\User01** ）， **User@Domain.Com** 或输入一个 `PSCredential` 对象，例如由 cmdlet 生成的对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="2c025-309">Type a user name, such as **User01** or **Domain01\User01** , **User@Domain.Com** , or enter a `PSCredential` object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="2c025-310">仅当命令中还使用了 **代理** 参数时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="2c025-310">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="2c025-311">不能在同一命令中使用 **ProxyCredential** 和 **ProxyUseDefaultCredentials** 参数。</span><span class="sxs-lookup"><span data-stu-id="2c025-311">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c025-312">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="2c025-312">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="2c025-313">指示该 cmdlet 使用当前用户的凭据来访问 **代理** 参数指定的代理服务器。</span><span class="sxs-lookup"><span data-stu-id="2c025-313">Indicates that the cmdlet uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="2c025-314">仅当命令中还使用了 **代理** 参数时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="2c025-314">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="2c025-315">不能在同一命令中使用 **ProxyCredential** 和 **ProxyUseDefaultCredentials** 参数。</span><span class="sxs-lookup"><span data-stu-id="2c025-315">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c025-316">-Resume</span><span class="sxs-lookup"><span data-stu-id="2c025-316">-Resume</span></span>

<span data-ttu-id="2c025-317">尽力尝试恢复下载部分文件。</span><span class="sxs-lookup"><span data-stu-id="2c025-317">Performs a best effort attempt to resume downloading a partial file.</span></span> <span data-ttu-id="2c025-318">**Resume** 需要 **OutFile** 。</span><span class="sxs-lookup"><span data-stu-id="2c025-318">**Resume** requires **OutFile** .</span></span>

<span data-ttu-id="2c025-319">**Resume** 仅对本地文件和远程文件的大小进行操作，并且不执行本地文件和远程文件相同的其他验证。</span><span class="sxs-lookup"><span data-stu-id="2c025-319">**Resume** only operates on the size of the local file and remote file and performs no other validation that the local file and the remote file are the same.</span></span>

<span data-ttu-id="2c025-320">如果本地文件的大小小于远程文件大小，则该 cmdlet 将尝试继续下载文件，并将剩余字节追加到文件末尾。</span><span class="sxs-lookup"><span data-stu-id="2c025-320">If the local file size is smaller than the remote file size, then the cmdlet attempts to resume downloading the file and append the remaining bytes to the end of the file.</span></span>

<span data-ttu-id="2c025-321">如果本地文件大小与远程文件大小相同，则不会执行任何操作，并且 cmdlet 会假设下载已完成。</span><span class="sxs-lookup"><span data-stu-id="2c025-321">If the local file size is the same as the remote file size, then no action is taken and the cmdlet assumes the download already complete.</span></span>

<span data-ttu-id="2c025-322">如果本地文件大小大于远程文件大小，则会覆盖本地文件，并重新下载整个远程文件。</span><span class="sxs-lookup"><span data-stu-id="2c025-322">If the local file size is larger than the remote file size, then the local file is overwritten and the entire remote file is re-downloaded.</span></span> <span data-ttu-id="2c025-323">此行为与在不 **恢复** 的情况下使用 **OutFile** 相同。</span><span class="sxs-lookup"><span data-stu-id="2c025-323">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="2c025-324">如果远程服务器不支持下载恢复，则会覆盖本地文件，并重新下载整个远程文件。</span><span class="sxs-lookup"><span data-stu-id="2c025-324">If the remote server does not support download resuming, then the local file is overwritten and the entire remote file is re-downloaded.</span></span> <span data-ttu-id="2c025-325">此行为与在不 **恢复** 的情况下使用 **OutFile** 相同。</span><span class="sxs-lookup"><span data-stu-id="2c025-325">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="2c025-326">如果本地文件不存在，则将创建本地文件并下载整个远程文件。</span><span class="sxs-lookup"><span data-stu-id="2c025-326">If the local file does not exist, then the local file is created and the entire remote file is downloaded.</span></span> <span data-ttu-id="2c025-327">此行为与在不 **恢复** 的情况下使用 **OutFile** 相同。</span><span class="sxs-lookup"><span data-stu-id="2c025-327">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="2c025-328">此功能已添加到 PowerShell 6.1.0。</span><span class="sxs-lookup"><span data-stu-id="2c025-328">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="2c025-329">-RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="2c025-329">-RetryIntervalSec</span></span>

<span data-ttu-id="2c025-330">指定在收到400与599（含）或304之间的失败代码时，连接的重试间隔。</span><span class="sxs-lookup"><span data-stu-id="2c025-330">Specifies the interval between retries for the connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="2c025-331">另请参阅 **MaximumRetryCount** 参数以指定重试次数。</span><span class="sxs-lookup"><span data-stu-id="2c025-331">Also see **MaximumRetryCount** parameter for specifying number of retries.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c025-332">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="2c025-332">-SessionVariable</span></span>

<span data-ttu-id="2c025-333">指定此 cmdlet 为其创建 web 请求会话的变量，并将其保存在值中。</span><span class="sxs-lookup"><span data-stu-id="2c025-333">Specifies a variable for which this cmdlet creates a web request session and saves it in the value.</span></span>
<span data-ttu-id="2c025-334">输入一个不带美元符号 () 符号的变量名称 `$` 。</span><span class="sxs-lookup"><span data-stu-id="2c025-334">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="2c025-335">指定会话变量时，将 `Invoke-WebRequest` 创建一个 web 请求会话对象，并将其分配给 PowerShell 会话中具有指定名称的变量。</span><span class="sxs-lookup"><span data-stu-id="2c025-335">When you specify a session variable, `Invoke-WebRequest` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="2c025-336">命令完成后可以立即在会话中使用该变量。</span><span class="sxs-lookup"><span data-stu-id="2c025-336">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="2c025-337">与远程会话不同，Web 请求会话不是持续性连接。</span><span class="sxs-lookup"><span data-stu-id="2c025-337">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="2c025-338">它是一个包含有关连接和请求的信息的对象，包括 cookie、凭据、最大重定向值和用户代理字符串。</span><span class="sxs-lookup"><span data-stu-id="2c025-338">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="2c025-339">可用于共享 Web 请求之间的状态和数据。</span><span class="sxs-lookup"><span data-stu-id="2c025-339">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="2c025-340">若要在后续的 Web 请求中使用 Web 请求会话，请在 **WebSession** 参数的值中指定会话变量。</span><span class="sxs-lookup"><span data-stu-id="2c025-340">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="2c025-341">PowerShell 在建立新连接时使用 web 请求会话对象中的数据。</span><span class="sxs-lookup"><span data-stu-id="2c025-341">PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="2c025-342">若要在 Web 请求会话中重写某个值，请使用 cmdlet 参数，如 **UserAgent** 或 **Credential** 。</span><span class="sxs-lookup"><span data-stu-id="2c025-342">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="2c025-343">参数值优先于 Web 请求会话中的值。</span><span class="sxs-lookup"><span data-stu-id="2c025-343">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="2c025-344">不能在同一命令中使用 **SessionVariable** 和 **WebSession** 参数。</span><span class="sxs-lookup"><span data-stu-id="2c025-344">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: SV

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c025-345">-SkipCertificateCheck</span><span class="sxs-lookup"><span data-stu-id="2c025-345">-SkipCertificateCheck</span></span>

<span data-ttu-id="2c025-346">跳过证书验证检查。</span><span class="sxs-lookup"><span data-stu-id="2c025-346">Skips certificate validation checks.</span></span> <span data-ttu-id="2c025-347">这包括所有验证，如过期、吊销、受信任的根证书颁发机构等。</span><span class="sxs-lookup"><span data-stu-id="2c025-347">This includes all validations such as expiration, revocation, trusted root authority, etc.</span></span>

> [!WARNING]
> <span data-ttu-id="2c025-348">使用此参数并不安全，不建议使用。</span><span class="sxs-lookup"><span data-stu-id="2c025-348">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="2c025-349">此开关仅用于用于测试目的的已知主机使用自签名证书。</span><span class="sxs-lookup"><span data-stu-id="2c025-349">This switch is only intended to be used against known hosts using a self-signed certificate for testing purposes.</span></span> <span data-ttu-id="2c025-350">使用自己的风险。</span><span class="sxs-lookup"><span data-stu-id="2c025-350">Use at your own risk.</span></span>

<span data-ttu-id="2c025-351">此功能已添加到 PowerShell 6.0.0。</span><span class="sxs-lookup"><span data-stu-id="2c025-351">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="2c025-352">-SkipHeaderValidation</span><span class="sxs-lookup"><span data-stu-id="2c025-352">-SkipHeaderValidation</span></span>

<span data-ttu-id="2c025-353">指示 cmdlet 应将标头添加到无验证的请求。</span><span class="sxs-lookup"><span data-stu-id="2c025-353">Indicates the cmdlet should add headers to the request without validation.</span></span>

<span data-ttu-id="2c025-354">此开关适用于需要不符合标准的标头值的站点。</span><span class="sxs-lookup"><span data-stu-id="2c025-354">This switch should be used for sites that require header values that do not conform to standards.</span></span>
<span data-ttu-id="2c025-355">如果指定此开关，则将禁用验证以允许取消选中值。</span><span class="sxs-lookup"><span data-stu-id="2c025-355">Specifying this switch disables validation to allow the value to be passed unchecked.</span></span> <span data-ttu-id="2c025-356">指定时，将添加所有标头，而不进行验证。</span><span class="sxs-lookup"><span data-stu-id="2c025-356">When specified, all headers are added without validation.</span></span>

<span data-ttu-id="2c025-357">此开关将对传递给 **ContentType** 、 **标头** 和 **UserAgent** 参数的值禁用验证。</span><span class="sxs-lookup"><span data-stu-id="2c025-357">This switch disables validation for values passed to the **ContentType** , **Headers** and **UserAgent** parameters.</span></span>

<span data-ttu-id="2c025-358">此功能已添加到 PowerShell 6.0.0。</span><span class="sxs-lookup"><span data-stu-id="2c025-358">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="2c025-359">-SslProtocol</span><span class="sxs-lookup"><span data-stu-id="2c025-359">-SslProtocol</span></span>

<span data-ttu-id="2c025-360">设置允许用于 web 请求的 SSL/TLS 协议。</span><span class="sxs-lookup"><span data-stu-id="2c025-360">Sets the SSL/TLS protocols that are permissible for the web request.</span></span> <span data-ttu-id="2c025-361">默认情况下，允许系统支持的 SSL/TLS 协议。</span><span class="sxs-lookup"><span data-stu-id="2c025-361">By default all, SSL/TLS protocols supported by the system are allowed.</span></span> <span data-ttu-id="2c025-362">**SslProtocol** 允许出于符合性目的限制特定协议。</span><span class="sxs-lookup"><span data-stu-id="2c025-362">**SslProtocol** allows for limiting to specific protocols for compliance purposes.</span></span>

<span data-ttu-id="2c025-363">**SslProtocol** 使用 **WebSslProtocol** 标志枚举。</span><span class="sxs-lookup"><span data-stu-id="2c025-363">**SslProtocol** uses the **WebSslProtocol** Flag Enum.</span></span> <span data-ttu-id="2c025-364">可以使用标志表示法来提供多个协议，或将多个 **WebSslProtocol** 选项与 **bor** 结合使用，但不支持在所有平台上提供多个协议。</span><span class="sxs-lookup"><span data-stu-id="2c025-364">It is possible to supply more than one protocol using flag notation or combining multiple **WebSslProtocol** options with **bor** , however supplying multiple protocols is not supported on all platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="2c025-365">在非 Windows 平台上，可能无法将其 `'Tls, Tls12'` 作为选项提供。</span><span class="sxs-lookup"><span data-stu-id="2c025-365">On non-Windows platforms it may not be possible to supply `'Tls, Tls12'` as an option.</span></span>

<span data-ttu-id="2c025-366">此功能已添加到 PowerShell 6.0.0。</span><span class="sxs-lookup"><span data-stu-id="2c025-366">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WebSslProtocol
Parameter Sets: (All)
Aliases:
Accepted values: Default, Tls, Tls11, Tls12

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c025-367">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="2c025-367">-TimeoutSec</span></span>

<span data-ttu-id="2c025-368">指定在超时之前请求可以挂起多长时间。输入一个值（以秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="2c025-368">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="2c025-369">默认值 0 指定无限超时。</span><span class="sxs-lookup"><span data-stu-id="2c025-369">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="2c025-370">域名系统 (DNS) 查询可能需要长达15秒钟的时间来返回或超时。如果你的请求包含需要解析的主机名，并将 **TimeoutSec** 设置为大于零的值，但不超过15秒，则在引发 WebException 之前可能需要15秒或更长时间，并且你的请求会超时。</span><span class="sxs-lookup"><span data-stu-id="2c025-370">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set **TimeoutSec** to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a WebException is thrown, and your request times out.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c025-371">-Token</span><span class="sxs-lookup"><span data-stu-id="2c025-371">-Token</span></span>

<span data-ttu-id="2c025-372">要包含在请求中的 OAuth 或持有者令牌。</span><span class="sxs-lookup"><span data-stu-id="2c025-372">The OAuth or Bearer token to include in the request.</span></span> <span data-ttu-id="2c025-373">某些 **身份验证** 选项需要 **标记** 。</span><span class="sxs-lookup"><span data-stu-id="2c025-373">**Token** is required by certain **Authentication** options.</span></span> <span data-ttu-id="2c025-374">不能单独使用。</span><span class="sxs-lookup"><span data-stu-id="2c025-374">It cannot be used independently.</span></span>

<span data-ttu-id="2c025-375">**令牌** 采用 `SecureString` 包含标记的。</span><span class="sxs-lookup"><span data-stu-id="2c025-375">**Token** takes a `SecureString` containing the token.</span></span> <span data-ttu-id="2c025-376">若要手动提供令牌，请使用以下内容：</span><span class="sxs-lookup"><span data-stu-id="2c025-376">To supply the token manually use the following:</span></span>

`Invoke-WebRequest -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

<span data-ttu-id="2c025-377">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="2c025-377">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c025-378">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="2c025-378">-TransferEncoding</span></span>

<span data-ttu-id="2c025-379">指定传输编码 HTTP 响应头的值。</span><span class="sxs-lookup"><span data-stu-id="2c025-379">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="2c025-380">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="2c025-380">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="2c025-381">块</span><span class="sxs-lookup"><span data-stu-id="2c025-381">Chunked</span></span>
- <span data-ttu-id="2c025-382">压缩</span><span class="sxs-lookup"><span data-stu-id="2c025-382">Compress</span></span>
- <span data-ttu-id="2c025-383">Deflate</span><span class="sxs-lookup"><span data-stu-id="2c025-383">Deflate</span></span>
- <span data-ttu-id="2c025-384">GZip</span><span class="sxs-lookup"><span data-stu-id="2c025-384">GZip</span></span>
- <span data-ttu-id="2c025-385">标识</span><span class="sxs-lookup"><span data-stu-id="2c025-385">Identity</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: chunked, compress, deflate, gzip, identity

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c025-386">-Uri</span><span class="sxs-lookup"><span data-stu-id="2c025-386">-Uri</span></span>

<span data-ttu-id="2c025-387">指定将 web 请求发送到的 internet 资源 (URI) 的统一资源标识符。</span><span class="sxs-lookup"><span data-stu-id="2c025-387">Specifies the Uniform Resource Identifier (URI) of the internet resource to which the web request is sent.</span></span> <span data-ttu-id="2c025-388">输入 URI。</span><span class="sxs-lookup"><span data-stu-id="2c025-388">Enter a URI.</span></span> <span data-ttu-id="2c025-389">此参数仅支持 HTTP 或 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="2c025-389">This parameter supports HTTP or HTTPS only.</span></span>

<span data-ttu-id="2c025-390">此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="2c025-390">This parameter is required.</span></span> <span data-ttu-id="2c025-391">参数名称 **Uri** 是可选的。</span><span class="sxs-lookup"><span data-stu-id="2c025-391">The parameter name **Uri** is optional.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c025-392">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="2c025-392">-UseBasicParsing</span></span>

<span data-ttu-id="2c025-393">此参数已弃用。</span><span class="sxs-lookup"><span data-stu-id="2c025-393">This parameter has been deprecated.</span></span> <span data-ttu-id="2c025-394">从 PowerShell 6.0.0 开始，所有 Web 请求仅使用基本分析。</span><span class="sxs-lookup"><span data-stu-id="2c025-394">Beginning with PowerShell 6.0.0, all Web requests use basic parsing only.</span></span> <span data-ttu-id="2c025-395">提供此参数只是为了实现向后兼容性，并且对此参数的任何使用都不会影响 cmdlet 的操作。</span><span class="sxs-lookup"><span data-stu-id="2c025-395">This parameter is included for backwards compatibility only and any use of it has no effect on the operation of the cmdlet.</span></span>

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

### <span data-ttu-id="2c025-396">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="2c025-396">-UseDefaultCredentials</span></span>

<span data-ttu-id="2c025-397">指示该 cmdlet 使用当前用户的凭据来发送 web 请求。</span><span class="sxs-lookup"><span data-stu-id="2c025-397">Indicates that the cmdlet uses the credentials of the current user to send the web request.</span></span> <span data-ttu-id="2c025-398">这不能用于 **身份验证** 或 **凭据** ，并且可能在所有平台上都不受支持。</span><span class="sxs-lookup"><span data-stu-id="2c025-398">This can't be used with **Authentication** or **Credential** and may not be supported on all platforms.</span></span>

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

### <span data-ttu-id="2c025-399">-UserAgent</span><span class="sxs-lookup"><span data-stu-id="2c025-399">-UserAgent</span></span>

<span data-ttu-id="2c025-400">指定 Web 请求的用户代理字符串。</span><span class="sxs-lookup"><span data-stu-id="2c025-400">Specifies a user agent string for the web request.</span></span>

<span data-ttu-id="2c025-401">默认的用户代理类似于 `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` 每个操作系统和平台稍有不同。</span><span class="sxs-lookup"><span data-stu-id="2c025-401">The default user agent is similar to `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="2c025-402">若要使用大多数 internet 浏览器使用的标准用户代理字符串测试网站，请使用 [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) 类的属性，例如 Chrome、FireFox、Microsoft-windows-ie-internetexplorer、Opera 和 Safari。</span><span class="sxs-lookup"><span data-stu-id="2c025-402">To test a website with the standard user agent string that is used by most internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) class, such as Chrome, FireFox, InternetExplorer, Opera, and Safari.</span></span>

<span data-ttu-id="2c025-403">例如，以下命令使用 Internet Explorer 的用户代理字符串：</span><span class="sxs-lookup"><span data-stu-id="2c025-403">For example, the following command uses the user agent string for Internet Explorer:</span></span>

```powershell
Invoke-WebRequest -Uri https://website.com/ -UserAgent ([Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer)
```

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

### <span data-ttu-id="2c025-404">-WebSession</span><span class="sxs-lookup"><span data-stu-id="2c025-404">-WebSession</span></span>

<span data-ttu-id="2c025-405">指定一个 Web 请求会话。</span><span class="sxs-lookup"><span data-stu-id="2c025-405">Specifies a web request session.</span></span> <span data-ttu-id="2c025-406">输入变量名称，包括美元符号 (`$`) 。</span><span class="sxs-lookup"><span data-stu-id="2c025-406">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="2c025-407">若要在 Web 请求会话中重写某个值，请使用 cmdlet 参数，如 **UserAgent** 或 **Credential** 。</span><span class="sxs-lookup"><span data-stu-id="2c025-407">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="2c025-408">参数值优先于 Web 请求会话中的值。</span><span class="sxs-lookup"><span data-stu-id="2c025-408">Parameter values take precedence over values in the web request session.</span></span> <span data-ttu-id="2c025-409">为 `Content-Type` **正文** 提供 **MultipartFormDataContent** 对象时，也会重写与内容相关的标头（例如）。</span><span class="sxs-lookup"><span data-stu-id="2c025-409">Content related headers, such as `Content-Type`, are also be overridden when a **MultipartFormDataContent** object is supplied for **Body** .</span></span>

<span data-ttu-id="2c025-410">与远程会话不同，web 请求会话不是持续性连接。</span><span class="sxs-lookup"><span data-stu-id="2c025-410">Unlike a remote session, the web request session isn't a persistent connection.</span></span> <span data-ttu-id="2c025-411">它是一个包含有关连接和请求的信息的对象，包括 cookie、凭据、最大重定向值和用户代理字符串。</span><span class="sxs-lookup"><span data-stu-id="2c025-411">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="2c025-412">可用于共享 Web 请求之间的状态和数据。</span><span class="sxs-lookup"><span data-stu-id="2c025-412">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="2c025-413">若要创建 web 请求会话，请在命令的 **SessionVariable** 参数的值中输入一个不带美元符号的变量名称 `Invoke-WebRequest` 。</span><span class="sxs-lookup"><span data-stu-id="2c025-413">To create a web request session, enter a variable name, without a dollar sign, in the value of the **SessionVariable** parameter of an `Invoke-WebRequest` command.</span></span> <span data-ttu-id="2c025-414">`Invoke-WebRequest` 创建会话并将其保存在变量中。</span><span class="sxs-lookup"><span data-stu-id="2c025-414">`Invoke-WebRequest` creates the session and saves it in the variable.</span></span> <span data-ttu-id="2c025-415">在后续命令中，将该变量用作 **WebSession** 参数的值。</span><span class="sxs-lookup"><span data-stu-id="2c025-415">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="2c025-416">不能在同一命令中使用 **SessionVariable** 和 **WebSession** 参数。</span><span class="sxs-lookup"><span data-stu-id="2c025-416">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WebRequestSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c025-417">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2c025-417">CommonParameters</span></span>

<span data-ttu-id="2c025-418">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2c025-418">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2c025-419">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2c025-419">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2c025-420">输入</span><span class="sxs-lookup"><span data-stu-id="2c025-420">INPUTS</span></span>

### <span data-ttu-id="2c025-421">System.Object</span><span class="sxs-lookup"><span data-stu-id="2c025-421">System.Object</span></span>

<span data-ttu-id="2c025-422">你可以通过管道将 web 请求的正文传递给 `Invoke-WebRequest` 。</span><span class="sxs-lookup"><span data-stu-id="2c025-422">You can pipe the body of a web request to `Invoke-WebRequest`.</span></span>

## <span data-ttu-id="2c025-423">输出</span><span class="sxs-lookup"><span data-stu-id="2c025-423">OUTPUTS</span></span>

### <span data-ttu-id="2c025-424">BasicHtmlWebResponseObject。</span><span class="sxs-lookup"><span data-stu-id="2c025-424">Microsoft.PowerShell.Commands.BasicHtmlWebResponseObject</span></span>

## <span data-ttu-id="2c025-425">注释</span><span class="sxs-lookup"><span data-stu-id="2c025-425">NOTES</span></span>

<span data-ttu-id="2c025-426">从 PowerShell 6.0.0 开始 `Invoke-WebRequest` 仅支持基本分析。</span><span class="sxs-lookup"><span data-stu-id="2c025-426">Beginning with PowerShell 6.0.0 `Invoke-WebRequest` supports basic parsing only.</span></span>

<span data-ttu-id="2c025-427">有关 **BasicHtmlWebResponseObject** 对象类型的详细信息，请参阅 [BasicHtmlWebResponseObject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject)。</span><span class="sxs-lookup"><span data-stu-id="2c025-427">For more information about the **Microsoft.PowerShell.Commands.BasicHtmlWebResponseObject** object type, see [BasicHtmlWebResponseObject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject).</span></span>

<span data-ttu-id="2c025-428">有关 .NET 如何向 PowerShell 提供代理服务的详细信息，请参阅 [通过代理访问 Internet](/dotnet/framework/network-programming/accessing-the-internet-through-a-proxy)。</span><span class="sxs-lookup"><span data-stu-id="2c025-428">For more information about how .NET provides proxy services to PowerShell, see [Accessing the Internet Through a Proxy](/dotnet/framework/network-programming/accessing-the-internet-through-a-proxy).</span></span>

## <span data-ttu-id="2c025-429">相关链接</span><span class="sxs-lookup"><span data-stu-id="2c025-429">RELATED LINKS</span></span>

[<span data-ttu-id="2c025-430">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="2c025-430">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="2c025-431">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="2c025-431">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="2c025-432">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="2c025-432">ConvertTo-Json</span></span>](ConvertTo-Json.md)
