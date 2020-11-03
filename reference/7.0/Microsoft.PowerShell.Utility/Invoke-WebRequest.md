---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WebRequest
ms.openlocfilehash: b81074e14461b0bf481232553b614e06c23b90b6
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "93199285"
---
# <span data-ttu-id="55fc1-103">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="55fc1-103">Invoke-WebRequest</span></span>

## <span data-ttu-id="55fc1-104">摘要</span><span class="sxs-lookup"><span data-stu-id="55fc1-104">SYNOPSIS</span></span>
<span data-ttu-id="55fc1-105">从 internet 上的网页中获取内容。</span><span class="sxs-lookup"><span data-stu-id="55fc1-105">Gets content from a web page on the internet.</span></span>

## <span data-ttu-id="55fc1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="55fc1-106">SYNTAX</span></span>

### <span data-ttu-id="55fc1-107">StandardMethod (默认值) </span><span class="sxs-lookup"><span data-stu-id="55fc1-107">StandardMethod (Default)</span></span>

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
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="55fc1-108">StandardMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="55fc1-108">StandardMethodNoProxy</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Method <WebRequestMethod>] -NoProxy
 [-Body <Object>] [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>]
 [-InFile <String>] [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck]
 [-PreserveAuthorizationOnRedirect] [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="55fc1-109">CustomMethod</span><span class="sxs-lookup"><span data-stu-id="55fc1-109">CustomMethod</span></span>

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
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="55fc1-110">CustomMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="55fc1-110">CustomMethodNoProxy</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -CustomMethod <String> -NoProxy
 [-Body <Object>] [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>]
 [-InFile <String>] [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck]
 [-PreserveAuthorizationOnRedirect] [-SkipHeaderValidation] [<CommonParameters>]
```

## <span data-ttu-id="55fc1-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="55fc1-111">DESCRIPTION</span></span>

<span data-ttu-id="55fc1-112">`Invoke-WebRequest`Cmdlet 将 HTTP 和 HTTPS 请求发送到网页或 web 服务。</span><span class="sxs-lookup"><span data-stu-id="55fc1-112">The `Invoke-WebRequest` cmdlet sends HTTP and HTTPS requests to a web page or web service.</span></span> <span data-ttu-id="55fc1-113">它分析响应并返回链接、图像和其他重要 HTML 元素的集合。</span><span class="sxs-lookup"><span data-stu-id="55fc1-113">It parses the response and returns collections of links, images, and other significant HTML elements.</span></span>

<span data-ttu-id="55fc1-114">此 cmdlet 是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="55fc1-114">This cmdlet was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="55fc1-115">从 PowerShell 7.0 开始， `Invoke-WebRequest` 支持由环境变量定义的代理配置。</span><span class="sxs-lookup"><span data-stu-id="55fc1-115">Beginning in PowerShell 7.0, `Invoke-WebRequest` supports proxy configuration defined by environment variables.</span></span> <span data-ttu-id="55fc1-116">请参阅本文的 " [备注](#notes) " 部分。</span><span class="sxs-lookup"><span data-stu-id="55fc1-116">See the [Notes](#notes) section of this article.</span></span>

## <span data-ttu-id="55fc1-117">示例</span><span class="sxs-lookup"><span data-stu-id="55fc1-117">EXAMPLES</span></span>

### <span data-ttu-id="55fc1-118">示例1：发送 web 请求</span><span class="sxs-lookup"><span data-stu-id="55fc1-118">Example 1: Send a web request</span></span>

<span data-ttu-id="55fc1-119">此示例使用 `Invoke-WebRequest` cmdlet 向 Bing.com 站点发送 web 请求。</span><span class="sxs-lookup"><span data-stu-id="55fc1-119">This example uses the `Invoke-WebRequest` cmdlet to send a web request to the Bing.com site.</span></span>

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

<span data-ttu-id="55fc1-120">第一个命令发出请求，并将响应保存在 `$Response` 变量中。</span><span class="sxs-lookup"><span data-stu-id="55fc1-120">The first command issues the request and saves the response in the `$Response` variable.</span></span>

<span data-ttu-id="55fc1-121">第二个命令获取 **Name** 属性所喜欢的任何 **InputField** `"* Value"` 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-121">The second command gets any **InputField** where the **Name** property is like `"* Value"`.</span></span> <span data-ttu-id="55fc1-122">筛选后的结果将通过管道传递到 `Select-Object` ，以选择 **名称** 和 **值** 属性。</span><span class="sxs-lookup"><span data-stu-id="55fc1-122">The filtered results are piped to `Select-Object` to select the **Name** and **Value** properties.</span></span>

### <span data-ttu-id="55fc1-123">示例2：使用有状态 web 服务</span><span class="sxs-lookup"><span data-stu-id="55fc1-123">Example 2: Use a stateful web service</span></span>

<span data-ttu-id="55fc1-124">此示例演示如何将 `Invoke-WebRequest` cmdlet 与有状态 web 服务一起使用。</span><span class="sxs-lookup"><span data-stu-id="55fc1-124">This example shows how to use the `Invoke-WebRequest` cmdlet with a stateful web service.</span></span>

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

<span data-ttu-id="55fc1-125">发送登录请求的第一次调用 `Invoke-WebRequest` 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-125">The first call to `Invoke-WebRequest` sends a sign-in request.</span></span> <span data-ttu-id="55fc1-126">命令为 **-SessionVariable** 参数的值指定值 "Session"，并将结果保存在 `$LoginResponse` 变量中。</span><span class="sxs-lookup"><span data-stu-id="55fc1-126">The command specifies a value of "Session" for the value of the **-SessionVariable** parameter, and saves the result in the `$LoginResponse` variable.</span></span> <span data-ttu-id="55fc1-127">当该命令完成时， `$LoginResponse` 变量将包含 `BasicHtmlWebResponseObject` ，并且该 `$Session` 变量包含一个 `WebRequestSession` 对象。</span><span class="sxs-lookup"><span data-stu-id="55fc1-127">When the command completes, the `$LoginResponse` variable contains an `BasicHtmlWebResponseObject` and the `$Session` variable contains a `WebRequestSession` object.</span></span> <span data-ttu-id="55fc1-128">这会将用户记录到站点中。</span><span class="sxs-lookup"><span data-stu-id="55fc1-128">This logs the user into the site.</span></span>

<span data-ttu-id="55fc1-129">对的调用 `$Session` 本身显示 `WebRequestSession` 变量中的对象。</span><span class="sxs-lookup"><span data-stu-id="55fc1-129">The call to `$Session` by itself shows the `WebRequestSession` object in the variable.</span></span>

<span data-ttu-id="55fc1-130">第二次调用会 `Invoke-WebRequest` 提取用户的配置文件，要求用户登录到站点。</span><span class="sxs-lookup"><span data-stu-id="55fc1-130">The second call to `Invoke-WebRequest` fetches the user's profile which requires that the user be logged into the site.</span></span> <span data-ttu-id="55fc1-131">变量中存储的会话数据 `$Session` 用于向在登录时创建的站点提供会话 cookie。</span><span class="sxs-lookup"><span data-stu-id="55fc1-131">The session data stored in the `$Session` variable is used to provide session cookies to the site created during the login.</span></span> <span data-ttu-id="55fc1-132">结果保存在 `$ProfileResponse` 变量中。</span><span class="sxs-lookup"><span data-stu-id="55fc1-132">The result is saved in the `$ProfileResponse` variable.</span></span>

<span data-ttu-id="55fc1-133">对的调用 `$ProfileResponse` 本身显示 `BasicHtmlWebResponseObject` 变量中的。</span><span class="sxs-lookup"><span data-stu-id="55fc1-133">The call to `$ProfileResponse` by itself shows the `BasicHtmlWebResponseObject` in the variable.</span></span>

### <span data-ttu-id="55fc1-134">示例3：获取网页中的链接</span><span class="sxs-lookup"><span data-stu-id="55fc1-134">Example 3: Get links from a web page</span></span>

<span data-ttu-id="55fc1-135">此示例将获取网页中的链接。</span><span class="sxs-lookup"><span data-stu-id="55fc1-135">This example gets the links in a web page.</span></span> <span data-ttu-id="55fc1-136">它使用 `Invoke-WebRequest` cmdlet 来获取网页内容。</span><span class="sxs-lookup"><span data-stu-id="55fc1-136">It uses the `Invoke-WebRequest` cmdlet to get the web page content.</span></span> <span data-ttu-id="55fc1-137">然后，它使用 **Links** 返回的的 Links `BasicHtmlWebResponseObject` 属性 `Invoke-WebRequest` 和每个链接的 **Href** 属性。</span><span class="sxs-lookup"><span data-stu-id="55fc1-137">Then it uses the **Links** property of the `BasicHtmlWebResponseObject` that `Invoke-WebRequest` returns, and the **Href** property of each link.</span></span>

```powershell
(Invoke-WebRequest -Uri "https://aka.ms/pscore6-docs").Links.Href
```

### <span data-ttu-id="55fc1-138">示例4：使用请求页中定义的编码将响应内容写入文件。</span><span class="sxs-lookup"><span data-stu-id="55fc1-138">Example 4: Writes the response content to a file using the encoding defined in the requested page.</span></span>

<span data-ttu-id="55fc1-139">此示例使用 `Invoke-WebRequest` cmdlet 检索 PowerShell 文档页的网页内容。</span><span class="sxs-lookup"><span data-stu-id="55fc1-139">This example uses the `Invoke-WebRequest` cmdlet to retrieve the web page content of a PowerShell documentation page.</span></span>

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

<span data-ttu-id="55fc1-140">第一个命令检索页面，并将响应对象保存在 `$Response` 变量中。</span><span class="sxs-lookup"><span data-stu-id="55fc1-140">The first command retrieves the page and saves the response object in the `$Response` variable.</span></span>

<span data-ttu-id="55fc1-141">第二个命令创建用于将 `StreamWriter` 响应内容写入文件的。</span><span class="sxs-lookup"><span data-stu-id="55fc1-141">The second command creates a `StreamWriter` to use to write the response content to a file.</span></span> <span data-ttu-id="55fc1-142">响应对象的 " **编码** " 属性用于设置文件的编码。</span><span class="sxs-lookup"><span data-stu-id="55fc1-142">The **Encoding** property of the response object is used to set the encoding for the file.</span></span>

<span data-ttu-id="55fc1-143">最后几个命令将 **Content** 属性写入文件，然后释放 `StreamWriter` 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-143">The final few commands write the **Content** property to the file then disposes the `StreamWriter`.</span></span>

<span data-ttu-id="55fc1-144">请注意，如果 web 请求未返回文本内容，则 **编码** 属性为 null。</span><span class="sxs-lookup"><span data-stu-id="55fc1-144">Note that the **Encoding** property is null if the web request doesn't return text content.</span></span>

### <span data-ttu-id="55fc1-145">示例5：提交多部分/窗体数据文件</span><span class="sxs-lookup"><span data-stu-id="55fc1-145">Example 5: Submit a multipart/form-data file</span></span>

<span data-ttu-id="55fc1-146">此示例使用 `Invoke-WebRequest` cmdlet 将文件上传为 `multipart/form-data` 提交。</span><span class="sxs-lookup"><span data-stu-id="55fc1-146">This example uses the `Invoke-WebRequest` cmdlet upload a file as a `multipart/form-data` submission.</span></span> <span data-ttu-id="55fc1-147">文件 `c:\document.txt` 将作为的窗体字段进行提交 `document` `Content-Type` `text/plain` 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-147">The file `c:\document.txt` is submitted as the form field `document` with the `Content-Type` of `text/plain`.</span></span>

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

### <span data-ttu-id="55fc1-148">示例6：简化的多部分/表单数据提交</span><span class="sxs-lookup"><span data-stu-id="55fc1-148">Example 6: Simplified Multipart/Form-Data Submission</span></span>

<span data-ttu-id="55fc1-149">某些 Api 需要 `multipart/form-data` 提交来上传文件和混合内容。</span><span class="sxs-lookup"><span data-stu-id="55fc1-149">Some APIs require `multipart/form-data` submissions to upload files and mixed content.</span></span> <span data-ttu-id="55fc1-150">此示例演示如何更新用户配置文件。</span><span class="sxs-lookup"><span data-stu-id="55fc1-150">This example demonstrates updating a user profile.</span></span>

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

<span data-ttu-id="55fc1-151">配置文件窗体需要以下字段： `firstName` 、 `lastName` 、、、 `email` `avatar` `birthday` 和 `hobbies` 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-151">The profile form requires these fields: `firstName`, `lastName`, `email`, `avatar`, `birthday`, and `hobbies`.</span></span> <span data-ttu-id="55fc1-152">该 API 需要在字段中提供用户配置文件 pic 的映像 `avatar` 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-152">The API is expecting an image for the user profile pic to be supplied in the `avatar` field.</span></span> <span data-ttu-id="55fc1-153">该 API 还接受 `hobbies` 同一窗体中提交的多个条目。</span><span class="sxs-lookup"><span data-stu-id="55fc1-153">The API also accepts multiple `hobbies` entries to be submitted in the same form.</span></span>

<span data-ttu-id="55fc1-154">创建 `$Form` 哈希表时，键名称将用作窗体字段名称。</span><span class="sxs-lookup"><span data-stu-id="55fc1-154">When creating the `$Form` HashTable, the key names are used as form field names.</span></span> <span data-ttu-id="55fc1-155">默认情况下，哈希表的值将转换为字符串。</span><span class="sxs-lookup"><span data-stu-id="55fc1-155">By default, the values of the HashTable are converted to strings.</span></span> <span data-ttu-id="55fc1-156">如果存在 **FileInfo** 值，则提交文件内容。</span><span class="sxs-lookup"><span data-stu-id="55fc1-156">If a **System.IO.FileInfo** value is present, the file contents are submitted.</span></span> <span data-ttu-id="55fc1-157">如果存在数组或列表这样的集合，则将多次提交窗体字段。</span><span class="sxs-lookup"><span data-stu-id="55fc1-157">If a collection such as arrays or lists are present, the form field is submitted multiple times.</span></span>

<span data-ttu-id="55fc1-158">通过 `Get-Item` 对键使用 `avatar` ，将 `FileInfo` 对象设置为值。</span><span class="sxs-lookup"><span data-stu-id="55fc1-158">By using `Get-Item` on the `avatar` key, the `FileInfo` object is set as the value.</span></span> <span data-ttu-id="55fc1-159">结果就是提交的图像数据 `jdoe.png` 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-159">The result is that the image data for `jdoe.png` is submitted.</span></span>

<span data-ttu-id="55fc1-160">通过向键提供一个列表 `hobbies` ， `hobbies` 每个列表项的提交一次中都有该字段。</span><span class="sxs-lookup"><span data-stu-id="55fc1-160">By supplying a list to the `hobbies` key, the `hobbies` field is present in the submissions once for each list item.</span></span>

### <span data-ttu-id="55fc1-161">示例7：从 Invoke-WebRequest 中捕获非成功消息</span><span class="sxs-lookup"><span data-stu-id="55fc1-161">Example 7: Catch non success messages from Invoke-WebRequest</span></span>

<span data-ttu-id="55fc1-162">如果 `Invoke-WebRequest` 遇到非成功 HTTP 消息 (404、500等 ) ，它将不返回任何输出，并引发终止错误。</span><span class="sxs-lookup"><span data-stu-id="55fc1-162">When `Invoke-WebRequest` encounters a non-success HTTP message (404, 500, etc.), it returns no output and throws a terminating error.</span></span> <span data-ttu-id="55fc1-163">若要捕获错误并查看 **StatusCode** ，可以在块中包含执行 `try/catch` 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-163">To catch the error and view the **StatusCode** you can enclose execution in a `try/catch` block.</span></span>

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

<span data-ttu-id="55fc1-164">命令调用的 `Invoke-WebRequest` **ErrorAction** 为 **Stop** ，这会强制 `Invoke-WebRequest` 对任何失败的请求引发终止错误。</span><span class="sxs-lookup"><span data-stu-id="55fc1-164">The command calls `Invoke-WebRequest` with an **ErrorAction** of **Stop** , which forces `Invoke-WebRequest` to throw a terminating error on any failed requests.</span></span> <span data-ttu-id="55fc1-165">终止错误由 `catch` 从 **异常** 对象检索 **StatusCode** 的块捕获。</span><span class="sxs-lookup"><span data-stu-id="55fc1-165">The terminating error is caught by the `catch` block which retrieves the **StatusCode** from the **Exception** object.</span></span>

## <span data-ttu-id="55fc1-166">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="55fc1-166">PARAMETERS</span></span>

### <span data-ttu-id="55fc1-167">-AllowUnencryptedAuthentication</span><span class="sxs-lookup"><span data-stu-id="55fc1-167">-AllowUnencryptedAuthentication</span></span>

<span data-ttu-id="55fc1-168">允许通过未加密的连接发送凭据和密码。</span><span class="sxs-lookup"><span data-stu-id="55fc1-168">Allows sending of credentials and secrets over unencrypted connections.</span></span> <span data-ttu-id="55fc1-169">默认情况下，如果提供 **凭据** 或任何具有不以开头的 **Uri** 的 **身份验证** 选项，将 `https://` 会导致错误，请求会中止，以防止无意中以纯文本方式在未加密的连接上传递机密。</span><span class="sxs-lookup"><span data-stu-id="55fc1-169">By default, supplying **Credential** or any **Authentication** option with a **Uri** that does not begin with `https://` results in an error and the request is aborted to prevent unintentionally communicating secrets in plain text over unencrypted connections.</span></span> <span data-ttu-id="55fc1-170">若要重写此行为，需自行承担相应的风险，请提供 **AllowUnencryptedAuthentication** 参数。</span><span class="sxs-lookup"><span data-stu-id="55fc1-170">To override this behavior at your own risk, supply the **AllowUnencryptedAuthentication** parameter.</span></span>

> [!WARNING]
> <span data-ttu-id="55fc1-171">使用此参数并不安全，不建议使用。</span><span class="sxs-lookup"><span data-stu-id="55fc1-171">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="55fc1-172">提供它只是为了与无法提供加密连接的旧系统兼容。</span><span class="sxs-lookup"><span data-stu-id="55fc1-172">It is provided only for compatibility with legacy systems that cannot provide encrypted connections.</span></span> <span data-ttu-id="55fc1-173">使用自己的风险。</span><span class="sxs-lookup"><span data-stu-id="55fc1-173">Use at your own risk.</span></span>

<span data-ttu-id="55fc1-174">此功能已添加到 PowerShell 6.0.0。</span><span class="sxs-lookup"><span data-stu-id="55fc1-174">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="55fc1-175">-Authentication</span><span class="sxs-lookup"><span data-stu-id="55fc1-175">-Authentication</span></span>

<span data-ttu-id="55fc1-176">指定要用于请求的显式身份验证类型。</span><span class="sxs-lookup"><span data-stu-id="55fc1-176">Specifies the explicit authentication type to use for the request.</span></span> <span data-ttu-id="55fc1-177">默认值为“无”。</span><span class="sxs-lookup"><span data-stu-id="55fc1-177">The default is **None** .</span></span>
<span data-ttu-id="55fc1-178">**身份验证** 不能与 **UseDefaultCredentials** 一起使用。</span><span class="sxs-lookup"><span data-stu-id="55fc1-178">**Authentication** cannot be used with **UseDefaultCredentials** .</span></span>

<span data-ttu-id="55fc1-179">可用的身份验证选项：</span><span class="sxs-lookup"><span data-stu-id="55fc1-179">Available Authentication Options:</span></span>

- <span data-ttu-id="55fc1-180">**无** ：这是未提供 **身份验证** 时的默认选项;不使用显式身份验证。</span><span class="sxs-lookup"><span data-stu-id="55fc1-180">**None** : This is the default option when **Authentication** isn't supplied; no explicit authentication is used.</span></span>
- <span data-ttu-id="55fc1-181">**基本** ：需要 **凭据** 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-181">**Basic** : Requires **Credential** .</span></span> <span data-ttu-id="55fc1-182">凭据以的格式在 RFC 7617 基本身份验证标头中发送 `base64(user:password)` 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-182">The credentials are sent in an RFC 7617 Basic Authentication header in the format of `base64(user:password)`.</span></span>
- <span data-ttu-id="55fc1-183">**持有** 者：需要 **标记** 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-183">**Bearer** : Requires **Token** .</span></span> <span data-ttu-id="55fc1-184">`Authorization: Bearer`使用提供的令牌发送 RFC 6750 标头。</span><span class="sxs-lookup"><span data-stu-id="55fc1-184">Sends an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="55fc1-185">这是 **OAuth** 的别名</span><span class="sxs-lookup"><span data-stu-id="55fc1-185">This is an alias for **OAuth**</span></span>
- <span data-ttu-id="55fc1-186">**OAuth** ：需要 **标记** 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-186">**OAuth** : Requires **Token** .</span></span> <span data-ttu-id="55fc1-187">`Authorization: Bearer`使用提供的令牌发送 RFC 6750 标头。</span><span class="sxs-lookup"><span data-stu-id="55fc1-187">Sends an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="55fc1-188">这是 **持有** 者的别名</span><span class="sxs-lookup"><span data-stu-id="55fc1-188">This is an alias for **Bearer**</span></span>

<span data-ttu-id="55fc1-189">提供 **身份验证** `Authorization` 将覆盖提供给 **标头** 或包含在 **WebSession** 中的任何标头。</span><span class="sxs-lookup"><span data-stu-id="55fc1-189">Supplying **Authentication** overrides any `Authorization` headers supplied to **Headers** or included in **WebSession** .</span></span>

<span data-ttu-id="55fc1-190">此功能已添加到 PowerShell 6.0.0。</span><span class="sxs-lookup"><span data-stu-id="55fc1-190">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="55fc1-191">-Body</span><span class="sxs-lookup"><span data-stu-id="55fc1-191">-Body</span></span>

<span data-ttu-id="55fc1-192">指定请求的正文。</span><span class="sxs-lookup"><span data-stu-id="55fc1-192">Specifies the body of the request.</span></span> <span data-ttu-id="55fc1-193">正文是请求的内容，位于标头之后。</span><span class="sxs-lookup"><span data-stu-id="55fc1-193">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="55fc1-194">还可以通过管道将正文值传递给 `Invoke-WebRequest` 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-194">You can also pipe a body value to `Invoke-WebRequest`.</span></span>

<span data-ttu-id="55fc1-195">可以将 **Body** 参数用于指定查询参数的列表，或用于指定响应的内容。</span><span class="sxs-lookup"><span data-stu-id="55fc1-195">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="55fc1-196">如果输入是 GET 请求且正文是 `IDictionary` (通常是) 哈希表，则会将正文作为查询参数添加到 URI 中。</span><span class="sxs-lookup"><span data-stu-id="55fc1-196">When the input is a GET request and the body is an `IDictionary` (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="55fc1-197">对于其他请求类型 (如 POST) ，主体将设置为标准格式的请求正文的值 `name=value` 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-197">For other request types (such as POST), the body is set as the value of the request body in the standard `name=value` format.</span></span>

<span data-ttu-id="55fc1-198">**Body** 参数还可以接受一个 `System.Net.Http.MultipartFormDataContent` 对象。</span><span class="sxs-lookup"><span data-stu-id="55fc1-198">The **Body** parameter may also accept a `System.Net.Http.MultipartFormDataContent` object.</span></span> <span data-ttu-id="55fc1-199">这便于 `multipart/form-data` 请求。</span><span class="sxs-lookup"><span data-stu-id="55fc1-199">This facilitates `multipart/form-data` requests.</span></span> <span data-ttu-id="55fc1-200">为 **正文** 提供 **MultipartFormDataContent** 对象时，提供给 **ContentType** 、 **标头** 或 **WebSession** 参数的任何相关标题的任何内容都将被 **MultipartFormDataContent** 对象的内容标头重写。</span><span class="sxs-lookup"><span data-stu-id="55fc1-200">When a **MultipartFormDataContent** object is supplied for **Body** , any Content related headers supplied to the **ContentType** , **Headers** , or **WebSession** parameters is overridden by the Content headers of the **MultipartFormDataContent** object.</span></span> <span data-ttu-id="55fc1-201">此功能已添加到 PowerShell 6.0.0。</span><span class="sxs-lookup"><span data-stu-id="55fc1-201">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="55fc1-202">-Certificate</span><span class="sxs-lookup"><span data-stu-id="55fc1-202">-Certificate</span></span>

<span data-ttu-id="55fc1-203">指定用于安全的 web 请求的客户端证书。</span><span class="sxs-lookup"><span data-stu-id="55fc1-203">Specifies the client certificate that's used for a secure web request.</span></span> <span data-ttu-id="55fc1-204">输入一个包含证书的变量，或可获取该证书的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="55fc1-204">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="55fc1-205">若要查找证书，请使用 `Get-PfxCertificate` 或使用 `Get-ChildItem` 证书 () 驱动器中的 cmdlet `Cert:` 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-205">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate (`Cert:`) drive.</span></span> <span data-ttu-id="55fc1-206">如果证书无效或没有足够的权限，则该命令将失败。</span><span class="sxs-lookup"><span data-stu-id="55fc1-206">If the certificate isn't valid or doesn't have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="55fc1-207">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="55fc1-207">-CertificateThumbprint</span></span>

<span data-ttu-id="55fc1-208">指定有权发送请求的用户帐户的数字公钥证书 (X509)。</span><span class="sxs-lookup"><span data-stu-id="55fc1-208">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="55fc1-209">输入证书的证书指纹。</span><span class="sxs-lookup"><span data-stu-id="55fc1-209">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="55fc1-210">在基于客户端证书的身份验证中使用证书。</span><span class="sxs-lookup"><span data-stu-id="55fc1-210">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="55fc1-211">它们只能映射到本地用户帐户;它们不适用于域帐户。</span><span class="sxs-lookup"><span data-stu-id="55fc1-211">They can be mapped only to local user accounts; they don't work with domain accounts.</span></span>

<span data-ttu-id="55fc1-212">若要获取证书指纹，请使用 `Get-Item` `Get-ChildItem` PowerShell 驱动器中的或命令 `Cert:` 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-212">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

> [!NOTE]
> <span data-ttu-id="55fc1-213">目前只有 Windows 操作系统平台支持此功能。</span><span class="sxs-lookup"><span data-stu-id="55fc1-213">This feature is currently only supported on Windows OS platforms.</span></span>

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

### <span data-ttu-id="55fc1-214">-ContentType</span><span class="sxs-lookup"><span data-stu-id="55fc1-214">-ContentType</span></span>

<span data-ttu-id="55fc1-215">指定 Web 请求的内容类型。</span><span class="sxs-lookup"><span data-stu-id="55fc1-215">Specifies the content type of the web request.</span></span>

<span data-ttu-id="55fc1-216">如果省略此参数且请求方法为 POST，则 `Invoke-WebRequest` 将内容类型设置为 `application/x-www-form-urlencoded` 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-216">If this parameter is omitted and the request method is POST, `Invoke-WebRequest` sets the content type to `application/x-www-form-urlencoded`.</span></span> <span data-ttu-id="55fc1-217">否则，不会在调用中指定内容类型。</span><span class="sxs-lookup"><span data-stu-id="55fc1-217">Otherwise, the content type isn't specified in the call.</span></span>

<span data-ttu-id="55fc1-218">为 **正文** 提供 **MultipartFormDataContent** 对象时，会重写 **ContentType** 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-218">**ContentType** is overridden when a **MultipartFormDataContent** object is supplied for **Body** .</span></span>

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

### <span data-ttu-id="55fc1-219">-Credential</span><span class="sxs-lookup"><span data-stu-id="55fc1-219">-Credential</span></span>

<span data-ttu-id="55fc1-220">指定有权发送请求的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="55fc1-220">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="55fc1-221">默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="55fc1-221">The default is the current user.</span></span>

<span data-ttu-id="55fc1-222">键入用户名（如 **User01** 或 **Domain01\User01** ），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-222">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="55fc1-223">**凭据** 可以单独使用，也可以与某些 **身份验证** 参数选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="55fc1-223">**Credential** can be used alone or in conjunction with certain **Authentication** parameter options.</span></span> <span data-ttu-id="55fc1-224">当远程服务器发送身份验证质询请求时，它仅向远程服务器提供凭据。</span><span class="sxs-lookup"><span data-stu-id="55fc1-224">When used alone, it only supplies credentials to the remote server if the remote server sends an authentication challenge request.</span></span> <span data-ttu-id="55fc1-225">与 **身份验证** 选项一起使用时，会显式发送凭据。</span><span class="sxs-lookup"><span data-stu-id="55fc1-225">When used with **Authentication** options, the credentials are explicitly sent.</span></span>

<span data-ttu-id="55fc1-226">凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="55fc1-226">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="55fc1-227">有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="55fc1-227">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="55fc1-228">-CustomMethod</span><span class="sxs-lookup"><span data-stu-id="55fc1-228">-CustomMethod</span></span>

<span data-ttu-id="55fc1-229">指定用于 web 请求的自定义方法。</span><span class="sxs-lookup"><span data-stu-id="55fc1-229">Specifies a custom method used for the web request.</span></span> <span data-ttu-id="55fc1-230">如果终结点所需的请求方法不可用于 **方法** ，则可以使用此方法。</span><span class="sxs-lookup"><span data-stu-id="55fc1-230">This can be used if the Request Method required by the endpoint isn't an available option on the **Method** .</span></span> <span data-ttu-id="55fc1-231">**方法** 和 **CustomMethod** 不能一起使用。</span><span class="sxs-lookup"><span data-stu-id="55fc1-231">**Method** and **CustomMethod** can't be used together.</span></span>

<span data-ttu-id="55fc1-232">此示例 `TEST` 向 API 发出 HTTP 请求：</span><span class="sxs-lookup"><span data-stu-id="55fc1-232">This example makes a `TEST` HTTP request to the API:</span></span>

`Invoke-WebRequest -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

<span data-ttu-id="55fc1-233">此功能已添加到 PowerShell 6.0.0。</span><span class="sxs-lookup"><span data-stu-id="55fc1-233">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="55fc1-234">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="55fc1-234">-DisableKeepAlive</span></span>

<span data-ttu-id="55fc1-235">指示该 cmdlet 将 HTTP 头中的 **KeepAlive** 值设置为 **False** 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-235">Indicates that the cmdlet sets the **KeepAlive** value in the HTTP header to **False** .</span></span> <span data-ttu-id="55fc1-236">默认情况下， **KeepAlive** 为 **True** 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-236">By default, **KeepAlive** is **True** .</span></span> <span data-ttu-id="55fc1-237">**KeepAlive** 建立到服务器的持续性连接，以促进后续请求。</span><span class="sxs-lookup"><span data-stu-id="55fc1-237">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="55fc1-238">-窗体</span><span class="sxs-lookup"><span data-stu-id="55fc1-238">-Form</span></span>

<span data-ttu-id="55fc1-239">将字典转换为 `multipart/form-data` 提交。</span><span class="sxs-lookup"><span data-stu-id="55fc1-239">Converts a dictionary to a `multipart/form-data` submission.</span></span> <span data-ttu-id="55fc1-240">**窗体** 不能与 **正文** 一起使用。</span><span class="sxs-lookup"><span data-stu-id="55fc1-240">**Form** may not be used with **Body** .</span></span>
<span data-ttu-id="55fc1-241">如果使用 **ContentType** ，则会将其忽略。</span><span class="sxs-lookup"><span data-stu-id="55fc1-241">If **ContentType** is used, it's ignored.</span></span>

<span data-ttu-id="55fc1-242">字典的键用作窗体字段名称。</span><span class="sxs-lookup"><span data-stu-id="55fc1-242">The keys of the dictionary are used as the form field names.</span></span> <span data-ttu-id="55fc1-243">默认情况下，窗体值将转换为字符串值。</span><span class="sxs-lookup"><span data-stu-id="55fc1-243">By default, form values are converted to string values.</span></span>

<span data-ttu-id="55fc1-244">如果值是 **FileInfo** 对象，则会提交二进制文件内容。</span><span class="sxs-lookup"><span data-stu-id="55fc1-244">If the value is a **System.IO.FileInfo** object, then the binary file contents are submitted.</span></span> <span data-ttu-id="55fc1-245">文件的名称将作为 **filename** 属性提交。</span><span class="sxs-lookup"><span data-stu-id="55fc1-245">The name of the file is submitted as the **filename** property.</span></span> <span data-ttu-id="55fc1-246">MIME 类型设置为 `application/octet-stream` 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-246">The MIME type is set as `application/octet-stream`.</span></span> <span data-ttu-id="55fc1-247">`Get-Item` 可用于简化 **FileInfo** 对象的提供。</span><span class="sxs-lookup"><span data-stu-id="55fc1-247">`Get-Item` can be used to simplify supplying the **System.IO.FileInfo** object.</span></span>

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

<span data-ttu-id="55fc1-248">如果值是集合类型（如数组或列表），则将多次提交 for 字段。</span><span class="sxs-lookup"><span data-stu-id="55fc1-248">If the value is a collection type, such Arrays or Lists, the for field are submitted multiple times.</span></span>
<span data-ttu-id="55fc1-249">默认情况下，列表的值被视为字符串。</span><span class="sxs-lookup"><span data-stu-id="55fc1-249">The values of the list are treated as strings by default.</span></span> <span data-ttu-id="55fc1-250">如果值是 **FileInfo** 对象，则会提交二进制文件内容。</span><span class="sxs-lookup"><span data-stu-id="55fc1-250">If the value is a **System.IO.FileInfo** object, then the binary file contents are submitted.</span></span> <span data-ttu-id="55fc1-251">嵌套集合不受支持。</span><span class="sxs-lookup"><span data-stu-id="55fc1-251">Nested collections aren't supported.</span></span>

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

<span data-ttu-id="55fc1-252">在上面的示例中， `tags` 字段在窗体中提供三次，一次用于 `Vacation` 、 `Italy` 和 `2017` 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-252">In the above example the `tags` field are supplied three times in the form, once for each of `Vacation`, `Italy`, and `2017`.</span></span> <span data-ttu-id="55fc1-253">`pictures`对于文件夹中的每个文件，该字段也会提交一次 `2017-Italy` 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-253">The `pictures` field is also submitted once for each file in the `2017-Italy` folder.</span></span> <span data-ttu-id="55fc1-254">将该文件夹中的文件的二进制内容提交为值。</span><span class="sxs-lookup"><span data-stu-id="55fc1-254">The binary contents of the files in that folder are submitted as the values.</span></span>

<span data-ttu-id="55fc1-255">此功能已添加到 PowerShell 6.1.0。</span><span class="sxs-lookup"><span data-stu-id="55fc1-255">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="55fc1-256">-标头</span><span class="sxs-lookup"><span data-stu-id="55fc1-256">-Headers</span></span>

<span data-ttu-id="55fc1-257">指定 Web 请求的标头。</span><span class="sxs-lookup"><span data-stu-id="55fc1-257">Specifies the headers of the web request.</span></span> <span data-ttu-id="55fc1-258">输入哈希表或字典。</span><span class="sxs-lookup"><span data-stu-id="55fc1-258">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="55fc1-259">若要设置 UserAgent 标头，请使用 **UserAgent** 参数。</span><span class="sxs-lookup"><span data-stu-id="55fc1-259">To set UserAgent headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="55fc1-260">不能使用此参数指定 **用户代理** 或 cookie 标头。</span><span class="sxs-lookup"><span data-stu-id="55fc1-260">You can't use this parameter to specify **User-Agent** or cookie headers.</span></span>

<span data-ttu-id="55fc1-261">为 `Content-Type` **正文** 提供 **MultipartFormDataContent** 对象时，会重写与内容相关的标头（例如）。</span><span class="sxs-lookup"><span data-stu-id="55fc1-261">Content related headers, such as `Content-Type` is overridden when a **MultipartFormDataContent** object is supplied for **Body** .</span></span>

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

### <span data-ttu-id="55fc1-262">-InFile</span><span class="sxs-lookup"><span data-stu-id="55fc1-262">-InFile</span></span>

<span data-ttu-id="55fc1-263">从文件中获取 Web 请求的内容。</span><span class="sxs-lookup"><span data-stu-id="55fc1-263">Gets the content of the web request from a file.</span></span> <span data-ttu-id="55fc1-264">请输入路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="55fc1-264">Enter a path and file name.</span></span> <span data-ttu-id="55fc1-265">如果省略路径，则默认路径为当前位置。</span><span class="sxs-lookup"><span data-stu-id="55fc1-265">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="55fc1-266">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="55fc1-266">-MaximumRedirection</span></span>

<span data-ttu-id="55fc1-267">指定在连接失败之前，PowerShell 将连接重定向到备用统一资源标识符 (URI) 的次数。</span><span class="sxs-lookup"><span data-stu-id="55fc1-267">Specifies how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="55fc1-268">默认值为 5。</span><span class="sxs-lookup"><span data-stu-id="55fc1-268">The default value is 5.</span></span> <span data-ttu-id="55fc1-269">值为 0（零）将阻止所有重定向。</span><span class="sxs-lookup"><span data-stu-id="55fc1-269">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="55fc1-270">-MaximumRetryCount</span><span class="sxs-lookup"><span data-stu-id="55fc1-270">-MaximumRetryCount</span></span>

<span data-ttu-id="55fc1-271">指定在收到400与599（含）或304之间的失败代码时，PowerShell 重试连接的次数。</span><span class="sxs-lookup"><span data-stu-id="55fc1-271">Specifies how many times PowerShell retries a connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="55fc1-272">另请参阅 **RetryIntervalSec** 参数以指定重试次数。</span><span class="sxs-lookup"><span data-stu-id="55fc1-272">Also see **RetryIntervalSec** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="55fc1-273">-方法</span><span class="sxs-lookup"><span data-stu-id="55fc1-273">-Method</span></span>

<span data-ttu-id="55fc1-274">指定用于 Web 请求的方法。</span><span class="sxs-lookup"><span data-stu-id="55fc1-274">Specifies the method used for the web request.</span></span> <span data-ttu-id="55fc1-275">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="55fc1-275">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="55fc1-276">默认</span><span class="sxs-lookup"><span data-stu-id="55fc1-276">Default</span></span>
- <span data-ttu-id="55fc1-277">删除</span><span class="sxs-lookup"><span data-stu-id="55fc1-277">Delete</span></span>
- <span data-ttu-id="55fc1-278">获取</span><span class="sxs-lookup"><span data-stu-id="55fc1-278">Get</span></span>
- <span data-ttu-id="55fc1-279">Head</span><span class="sxs-lookup"><span data-stu-id="55fc1-279">Head</span></span>
- <span data-ttu-id="55fc1-280">合并</span><span class="sxs-lookup"><span data-stu-id="55fc1-280">Merge</span></span>
- <span data-ttu-id="55fc1-281">选项</span><span class="sxs-lookup"><span data-stu-id="55fc1-281">Options</span></span>
- <span data-ttu-id="55fc1-282">修补程序</span><span class="sxs-lookup"><span data-stu-id="55fc1-282">Patch</span></span>
- <span data-ttu-id="55fc1-283">邮递</span><span class="sxs-lookup"><span data-stu-id="55fc1-283">Post</span></span>
- <span data-ttu-id="55fc1-284">Put</span><span class="sxs-lookup"><span data-stu-id="55fc1-284">Put</span></span>
- <span data-ttu-id="55fc1-285">跟踪</span><span class="sxs-lookup"><span data-stu-id="55fc1-285">Trace</span></span>

<span data-ttu-id="55fc1-286">**CustomMethod** 参数可用于上面未列出的请求方法。</span><span class="sxs-lookup"><span data-stu-id="55fc1-286">The **CustomMethod** parameter can be used for Request Methods not listed above.</span></span>

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

### <span data-ttu-id="55fc1-287">-NoProxy</span><span class="sxs-lookup"><span data-stu-id="55fc1-287">-NoProxy</span></span>

<span data-ttu-id="55fc1-288">指示 cmdlet 不应使用代理来访问目标。</span><span class="sxs-lookup"><span data-stu-id="55fc1-288">Indicates that the cmdlet shouldn't use a proxy to reach the destination.</span></span> <span data-ttu-id="55fc1-289">如果需要绕过环境中配置的代理，请使用此开关。</span><span class="sxs-lookup"><span data-stu-id="55fc1-289">When you need to bypass the proxy configured in the environment, use this switch.</span></span> <span data-ttu-id="55fc1-290">此功能已添加到 PowerShell 6.0.0。</span><span class="sxs-lookup"><span data-stu-id="55fc1-290">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="55fc1-291">-OutFile</span><span class="sxs-lookup"><span data-stu-id="55fc1-291">-OutFile</span></span>

<span data-ttu-id="55fc1-292">指定此 cmdlet 为其保存响应正文的输出文件。</span><span class="sxs-lookup"><span data-stu-id="55fc1-292">Specifies the output file for which this cmdlet saves the response body.</span></span> <span data-ttu-id="55fc1-293">请输入路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="55fc1-293">Enter a path and file name.</span></span>
<span data-ttu-id="55fc1-294">如果省略路径，则默认路径为当前位置。</span><span class="sxs-lookup"><span data-stu-id="55fc1-294">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="55fc1-295">默认情况下，将 `Invoke-WebRequest` 结果返回到管道。</span><span class="sxs-lookup"><span data-stu-id="55fc1-295">By default, `Invoke-WebRequest` returns the results to the pipeline.</span></span> <span data-ttu-id="55fc1-296">若要将这些结果发送到文件和管道，请使用 **Passthru** 参数。</span><span class="sxs-lookup"><span data-stu-id="55fc1-296">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="55fc1-297">-PassThru</span><span class="sxs-lookup"><span data-stu-id="55fc1-297">-PassThru</span></span>

<span data-ttu-id="55fc1-298">指示除了将结果写入文件外，该 cmdlet 还会返回结果。</span><span class="sxs-lookup"><span data-stu-id="55fc1-298">Indicates that the cmdlet returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="55fc1-299">仅当命令中还使用了 **OutFile** 参数时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="55fc1-299">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="55fc1-300">-PreserveAuthorizationOnRedirect</span><span class="sxs-lookup"><span data-stu-id="55fc1-300">-PreserveAuthorizationOnRedirect</span></span>

<span data-ttu-id="55fc1-301">指示 cmdlet 应在重定向中保留 `Authorization` 标头（如果存在）。</span><span class="sxs-lookup"><span data-stu-id="55fc1-301">Indicates the cmdlet should preserve the `Authorization` header, when present, across redirections.</span></span>

<span data-ttu-id="55fc1-302">默认情况下，该 cmdlet 会 `Authorization` 在重定向前去除标头。</span><span class="sxs-lookup"><span data-stu-id="55fc1-302">By default, the cmdlet strips the `Authorization` header before redirecting.</span></span> <span data-ttu-id="55fc1-303">如果指定此参数，则会在需要将标头发送到重定向位置的情况下禁用此逻辑。</span><span class="sxs-lookup"><span data-stu-id="55fc1-303">Specifying this parameter disables this logic for cases where the header needs to be sent to the redirection location.</span></span>

<span data-ttu-id="55fc1-304">此功能已添加到 PowerShell 6.0.0。</span><span class="sxs-lookup"><span data-stu-id="55fc1-304">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="55fc1-305">-Proxy</span><span class="sxs-lookup"><span data-stu-id="55fc1-305">-Proxy</span></span>

<span data-ttu-id="55fc1-306">为请求指定代理服务器，而不是直接连接到 internet 资源。</span><span class="sxs-lookup"><span data-stu-id="55fc1-306">Specifies a proxy server for the request, rather than connecting directly to the internet resource.</span></span>
<span data-ttu-id="55fc1-307">输入网络代理服务器的 URI。</span><span class="sxs-lookup"><span data-stu-id="55fc1-307">Enter the URI of a network proxy server.</span></span>

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

### <span data-ttu-id="55fc1-308">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="55fc1-308">-ProxyCredential</span></span>

<span data-ttu-id="55fc1-309">指定有权使用由 **Proxy** 参数指定的代理服务器的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="55fc1-309">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="55fc1-310">默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="55fc1-310">The default is the current user.</span></span>

<span data-ttu-id="55fc1-311">键入用户名（如 **User01** 或 **Domain01\User01** ）， **User@Domain.Com** 或输入一个 `PSCredential` 对象，例如由 cmdlet 生成的对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-311">Type a user name, such as **User01** or **Domain01\User01** , **User@Domain.Com** , or enter a `PSCredential` object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="55fc1-312">仅当命令中还使用了 **代理** 参数时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="55fc1-312">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="55fc1-313">不能在同一命令中使用 **ProxyCredential** 和 **ProxyUseDefaultCredentials** 参数。</span><span class="sxs-lookup"><span data-stu-id="55fc1-313">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="55fc1-314">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="55fc1-314">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="55fc1-315">指示该 cmdlet 使用当前用户的凭据来访问 **代理** 参数指定的代理服务器。</span><span class="sxs-lookup"><span data-stu-id="55fc1-315">Indicates that the cmdlet uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="55fc1-316">仅当命令中还使用了 **代理** 参数时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="55fc1-316">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="55fc1-317">不能在同一命令中使用 **ProxyCredential** 和 **ProxyUseDefaultCredentials** 参数。</span><span class="sxs-lookup"><span data-stu-id="55fc1-317">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="55fc1-318">-Resume</span><span class="sxs-lookup"><span data-stu-id="55fc1-318">-Resume</span></span>

<span data-ttu-id="55fc1-319">尽力尝试恢复下载部分文件。</span><span class="sxs-lookup"><span data-stu-id="55fc1-319">Performs a best effort attempt to resume downloading a partial file.</span></span> <span data-ttu-id="55fc1-320">**Resume** 需要 **OutFile** 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-320">**Resume** requires **OutFile** .</span></span>

<span data-ttu-id="55fc1-321">**Resume** 仅对本地文件和远程文件的大小进行操作，并且不执行本地文件和远程文件相同的其他验证。</span><span class="sxs-lookup"><span data-stu-id="55fc1-321">**Resume** only operates on the size of the local file and remote file and performs no other validation that the local file and the remote file are the same.</span></span>

<span data-ttu-id="55fc1-322">如果本地文件的大小小于远程文件大小，则该 cmdlet 将尝试继续下载文件，并将剩余字节追加到文件末尾。</span><span class="sxs-lookup"><span data-stu-id="55fc1-322">If the local file size is smaller than the remote file size, then the cmdlet attempts to resume downloading the file and append the remaining bytes to the end of the file.</span></span>

<span data-ttu-id="55fc1-323">如果本地文件大小与远程文件大小相同，则不会执行任何操作，并且 cmdlet 会假设下载已完成。</span><span class="sxs-lookup"><span data-stu-id="55fc1-323">If the local file size is the same as the remote file size, then no action is taken and the cmdlet assumes the download already complete.</span></span>

<span data-ttu-id="55fc1-324">如果本地文件大小大于远程文件大小，则会覆盖本地文件，并重新下载整个远程文件。</span><span class="sxs-lookup"><span data-stu-id="55fc1-324">If the local file size is larger than the remote file size, then the local file is overwritten and the entire remote file is re-downloaded.</span></span> <span data-ttu-id="55fc1-325">此行为与在不 **恢复** 的情况下使用 **OutFile** 相同。</span><span class="sxs-lookup"><span data-stu-id="55fc1-325">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="55fc1-326">如果远程服务器不支持下载恢复，则会覆盖本地文件，并重新下载整个远程文件。</span><span class="sxs-lookup"><span data-stu-id="55fc1-326">If the remote server does not support download resuming, then the local file is overwritten and the entire remote file is re-downloaded.</span></span> <span data-ttu-id="55fc1-327">此行为与在不 **恢复** 的情况下使用 **OutFile** 相同。</span><span class="sxs-lookup"><span data-stu-id="55fc1-327">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="55fc1-328">如果本地文件不存在，则将创建本地文件并下载整个远程文件。</span><span class="sxs-lookup"><span data-stu-id="55fc1-328">If the local file does not exist, then the local file is created and the entire remote file is downloaded.</span></span> <span data-ttu-id="55fc1-329">此行为与在不 **恢复** 的情况下使用 **OutFile** 相同。</span><span class="sxs-lookup"><span data-stu-id="55fc1-329">This behavior is the same as using **OutFile** without **Resume** .</span></span>

<span data-ttu-id="55fc1-330">此功能已添加到 PowerShell 6.1.0。</span><span class="sxs-lookup"><span data-stu-id="55fc1-330">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="55fc1-331">-RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="55fc1-331">-RetryIntervalSec</span></span>

<span data-ttu-id="55fc1-332">指定在收到400与599（含）或304之间的失败代码时，连接的重试间隔。</span><span class="sxs-lookup"><span data-stu-id="55fc1-332">Specifies the interval between retries for the connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="55fc1-333">另请参阅 **MaximumRetryCount** 参数以指定重试次数。</span><span class="sxs-lookup"><span data-stu-id="55fc1-333">Also see **MaximumRetryCount** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="55fc1-334">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="55fc1-334">-SessionVariable</span></span>

<span data-ttu-id="55fc1-335">指定此 cmdlet 为其创建 web 请求会话的变量，并将其保存在值中。</span><span class="sxs-lookup"><span data-stu-id="55fc1-335">Specifies a variable for which this cmdlet creates a web request session and saves it in the value.</span></span>
<span data-ttu-id="55fc1-336">输入一个不带美元符号 () 符号的变量名称 `$` 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-336">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="55fc1-337">指定会话变量时，将 `Invoke-WebRequest` 创建一个 web 请求会话对象，并将其分配给 PowerShell 会话中具有指定名称的变量。</span><span class="sxs-lookup"><span data-stu-id="55fc1-337">When you specify a session variable, `Invoke-WebRequest` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="55fc1-338">命令完成后可以立即在会话中使用该变量。</span><span class="sxs-lookup"><span data-stu-id="55fc1-338">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="55fc1-339">与远程会话不同，Web 请求会话不是持续性连接。</span><span class="sxs-lookup"><span data-stu-id="55fc1-339">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="55fc1-340">它是一个包含有关连接和请求的信息的对象，包括 cookie、凭据、最大重定向值和用户代理字符串。</span><span class="sxs-lookup"><span data-stu-id="55fc1-340">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="55fc1-341">可用于共享 Web 请求之间的状态和数据。</span><span class="sxs-lookup"><span data-stu-id="55fc1-341">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="55fc1-342">若要在后续的 Web 请求中使用 Web 请求会话，请在 **WebSession** 参数的值中指定会话变量。</span><span class="sxs-lookup"><span data-stu-id="55fc1-342">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="55fc1-343">PowerShell 在建立新连接时使用 web 请求会话对象中的数据。</span><span class="sxs-lookup"><span data-stu-id="55fc1-343">PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="55fc1-344">若要在 Web 请求会话中重写某个值，请使用 cmdlet 参数，如 **UserAgent** 或 **Credential** 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-344">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="55fc1-345">参数值优先于 Web 请求会话中的值。</span><span class="sxs-lookup"><span data-stu-id="55fc1-345">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="55fc1-346">不能在同一命令中使用 **SessionVariable** 和 **WebSession** 参数。</span><span class="sxs-lookup"><span data-stu-id="55fc1-346">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="55fc1-347">-SkipCertificateCheck</span><span class="sxs-lookup"><span data-stu-id="55fc1-347">-SkipCertificateCheck</span></span>

<span data-ttu-id="55fc1-348">跳过证书验证检查。</span><span class="sxs-lookup"><span data-stu-id="55fc1-348">Skips certificate validation checks.</span></span> <span data-ttu-id="55fc1-349">这包括所有验证，如过期、吊销、受信任的根证书颁发机构等。</span><span class="sxs-lookup"><span data-stu-id="55fc1-349">This includes all validations such as expiration, revocation, trusted root authority, etc.</span></span>

> [!WARNING]
> <span data-ttu-id="55fc1-350">使用此参数并不安全，不建议使用。</span><span class="sxs-lookup"><span data-stu-id="55fc1-350">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="55fc1-351">此开关仅用于用于测试目的的已知主机使用自签名证书。</span><span class="sxs-lookup"><span data-stu-id="55fc1-351">This switch is only intended to be used against known hosts using a self-signed certificate for testing purposes.</span></span> <span data-ttu-id="55fc1-352">使用自己的风险。</span><span class="sxs-lookup"><span data-stu-id="55fc1-352">Use at your own risk.</span></span>

<span data-ttu-id="55fc1-353">此功能已添加到 PowerShell 6.0.0。</span><span class="sxs-lookup"><span data-stu-id="55fc1-353">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="55fc1-354">-SkipHeaderValidation</span><span class="sxs-lookup"><span data-stu-id="55fc1-354">-SkipHeaderValidation</span></span>

<span data-ttu-id="55fc1-355">指示 cmdlet 应将标头添加到无验证的请求。</span><span class="sxs-lookup"><span data-stu-id="55fc1-355">Indicates the cmdlet should add headers to the request without validation.</span></span>

<span data-ttu-id="55fc1-356">此开关适用于需要不符合标准的标头值的站点。</span><span class="sxs-lookup"><span data-stu-id="55fc1-356">This switch should be used for sites that require header values that do not conform to standards.</span></span>
<span data-ttu-id="55fc1-357">如果指定此开关，则将禁用验证以允许取消选中值。</span><span class="sxs-lookup"><span data-stu-id="55fc1-357">Specifying this switch disables validation to allow the value to be passed unchecked.</span></span> <span data-ttu-id="55fc1-358">指定时，将添加所有标头，而不进行验证。</span><span class="sxs-lookup"><span data-stu-id="55fc1-358">When specified, all headers are added without validation.</span></span>

<span data-ttu-id="55fc1-359">此开关将对传递给 **ContentType** 、 **标头** 和 **UserAgent** 参数的值禁用验证。</span><span class="sxs-lookup"><span data-stu-id="55fc1-359">This switch disables validation for values passed to the **ContentType** , **Headers** and **UserAgent** parameters.</span></span>

<span data-ttu-id="55fc1-360">此功能已添加到 PowerShell 6.0.0。</span><span class="sxs-lookup"><span data-stu-id="55fc1-360">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="55fc1-361">-SkipHttpErrorCheck</span><span class="sxs-lookup"><span data-stu-id="55fc1-361">-SkipHttpErrorCheck</span></span>

<span data-ttu-id="55fc1-362">此参数会导致 cmdlet 忽略 HTTP 错误状态并继续处理响应。</span><span class="sxs-lookup"><span data-stu-id="55fc1-362">This parameter causes the cmdlet to ignore HTTP error statuses and continue to process responses.</span></span>
<span data-ttu-id="55fc1-363">错误响应将写入管道，就像它们成功一样。</span><span class="sxs-lookup"><span data-stu-id="55fc1-363">The error responses are written to the pipeline just as if they were successful.</span></span>

<span data-ttu-id="55fc1-364">此参数是在 PowerShell 7 中引入的。</span><span class="sxs-lookup"><span data-stu-id="55fc1-364">This parameter was introduced in PowerShell 7.</span></span>

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

### <span data-ttu-id="55fc1-365">-SslProtocol</span><span class="sxs-lookup"><span data-stu-id="55fc1-365">-SslProtocol</span></span>

<span data-ttu-id="55fc1-366">设置允许用于 web 请求的 SSL/TLS 协议。</span><span class="sxs-lookup"><span data-stu-id="55fc1-366">Sets the SSL/TLS protocols that are permissible for the web request.</span></span> <span data-ttu-id="55fc1-367">默认情况下，允许系统支持的 SSL/TLS 协议。</span><span class="sxs-lookup"><span data-stu-id="55fc1-367">By default all, SSL/TLS protocols supported by the system are allowed.</span></span> <span data-ttu-id="55fc1-368">**SslProtocol** 允许出于符合性目的限制特定协议。</span><span class="sxs-lookup"><span data-stu-id="55fc1-368">**SslProtocol** allows for limiting to specific protocols for compliance purposes.</span></span>

<span data-ttu-id="55fc1-369">**SslProtocol** 使用 **WebSslProtocol** 标志枚举。</span><span class="sxs-lookup"><span data-stu-id="55fc1-369">**SslProtocol** uses the **WebSslProtocol** Flag Enum.</span></span> <span data-ttu-id="55fc1-370">可以使用标志表示法来提供多个协议，或将多个 **WebSslProtocol** 选项与 **bor** 结合使用，但不支持在所有平台上提供多个协议。</span><span class="sxs-lookup"><span data-stu-id="55fc1-370">It is possible to supply more than one protocol using flag notation or combining multiple **WebSslProtocol** options with **bor** , however supplying multiple protocols is not supported on all platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="55fc1-371">在非 Windows 平台上，可能无法将其 `'Tls, Tls12'` 作为选项提供。</span><span class="sxs-lookup"><span data-stu-id="55fc1-371">On non-Windows platforms it may not be possible to supply `'Tls, Tls12'` as an option.</span></span>

<span data-ttu-id="55fc1-372">此功能已添加到 PowerShell 6.0.0。</span><span class="sxs-lookup"><span data-stu-id="55fc1-372">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="55fc1-373">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="55fc1-373">-TimeoutSec</span></span>

<span data-ttu-id="55fc1-374">指定在超时之前请求可以挂起多长时间。输入一个值（以秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="55fc1-374">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="55fc1-375">默认值 0 指定无限超时。</span><span class="sxs-lookup"><span data-stu-id="55fc1-375">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="55fc1-376">域名系统 (DNS) 查询可能需要长达15秒钟的时间来返回或超时。如果你的请求包含需要解析的主机名，并将 **TimeoutSec** 设置为大于零的值，但不超过15秒，则在引发 WebException 之前可能需要15秒或更长时间，并且你的请求会超时。</span><span class="sxs-lookup"><span data-stu-id="55fc1-376">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set **TimeoutSec** to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a WebException is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="55fc1-377">-Token</span><span class="sxs-lookup"><span data-stu-id="55fc1-377">-Token</span></span>

<span data-ttu-id="55fc1-378">要包含在请求中的 OAuth 或持有者令牌。</span><span class="sxs-lookup"><span data-stu-id="55fc1-378">The OAuth or Bearer token to include in the request.</span></span> <span data-ttu-id="55fc1-379">某些 **身份验证** 选项需要 **标记** 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-379">**Token** is required by certain **Authentication** options.</span></span> <span data-ttu-id="55fc1-380">不能单独使用。</span><span class="sxs-lookup"><span data-stu-id="55fc1-380">It cannot be used independently.</span></span>

<span data-ttu-id="55fc1-381">**令牌** 采用 `SecureString` 包含标记的。</span><span class="sxs-lookup"><span data-stu-id="55fc1-381">**Token** takes a `SecureString` containing the token.</span></span> <span data-ttu-id="55fc1-382">若要手动提供令牌，请使用以下内容：</span><span class="sxs-lookup"><span data-stu-id="55fc1-382">To supply the token manually use the following:</span></span>

`Invoke-WebRequest -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

<span data-ttu-id="55fc1-383">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="55fc1-383">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="55fc1-384">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="55fc1-384">-TransferEncoding</span></span>

<span data-ttu-id="55fc1-385">指定传输编码 HTTP 响应头的值。</span><span class="sxs-lookup"><span data-stu-id="55fc1-385">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="55fc1-386">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="55fc1-386">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="55fc1-387">块</span><span class="sxs-lookup"><span data-stu-id="55fc1-387">Chunked</span></span>
- <span data-ttu-id="55fc1-388">压缩</span><span class="sxs-lookup"><span data-stu-id="55fc1-388">Compress</span></span>
- <span data-ttu-id="55fc1-389">Deflate</span><span class="sxs-lookup"><span data-stu-id="55fc1-389">Deflate</span></span>
- <span data-ttu-id="55fc1-390">GZip</span><span class="sxs-lookup"><span data-stu-id="55fc1-390">GZip</span></span>
- <span data-ttu-id="55fc1-391">标识</span><span class="sxs-lookup"><span data-stu-id="55fc1-391">Identity</span></span>

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

### <span data-ttu-id="55fc1-392">-Uri</span><span class="sxs-lookup"><span data-stu-id="55fc1-392">-Uri</span></span>

<span data-ttu-id="55fc1-393">指定将 web 请求发送到的 internet 资源 (URI) 的统一资源标识符。</span><span class="sxs-lookup"><span data-stu-id="55fc1-393">Specifies the Uniform Resource Identifier (URI) of the internet resource to which the web request is sent.</span></span> <span data-ttu-id="55fc1-394">输入 URI。</span><span class="sxs-lookup"><span data-stu-id="55fc1-394">Enter a URI.</span></span> <span data-ttu-id="55fc1-395">此参数仅支持 HTTP 或 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="55fc1-395">This parameter supports HTTP or HTTPS only.</span></span>

<span data-ttu-id="55fc1-396">此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="55fc1-396">This parameter is required.</span></span> <span data-ttu-id="55fc1-397">参数名称 **Uri** 是可选的。</span><span class="sxs-lookup"><span data-stu-id="55fc1-397">The parameter name **Uri** is optional.</span></span>

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

### <span data-ttu-id="55fc1-398">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="55fc1-398">-UseBasicParsing</span></span>

<span data-ttu-id="55fc1-399">此参数已弃用。</span><span class="sxs-lookup"><span data-stu-id="55fc1-399">This parameter has been deprecated.</span></span> <span data-ttu-id="55fc1-400">从 PowerShell 6.0.0 开始，所有 Web 请求仅使用基本分析。</span><span class="sxs-lookup"><span data-stu-id="55fc1-400">Beginning with PowerShell 6.0.0, all Web requests use basic parsing only.</span></span> <span data-ttu-id="55fc1-401">提供此参数只是为了实现向后兼容性，并且对此参数的任何使用都不会影响 cmdlet 的操作。</span><span class="sxs-lookup"><span data-stu-id="55fc1-401">This parameter is included for backwards compatibility only and any use of it has no effect on the operation of the cmdlet.</span></span>

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

### <span data-ttu-id="55fc1-402">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="55fc1-402">-UseDefaultCredentials</span></span>

<span data-ttu-id="55fc1-403">指示该 cmdlet 使用当前用户的凭据来发送 web 请求。</span><span class="sxs-lookup"><span data-stu-id="55fc1-403">Indicates that the cmdlet uses the credentials of the current user to send the web request.</span></span> <span data-ttu-id="55fc1-404">这不能用于 **身份验证** 或 **凭据** ，并且可能在所有平台上都不受支持。</span><span class="sxs-lookup"><span data-stu-id="55fc1-404">This can't be used with **Authentication** or **Credential** and may not be supported on all platforms.</span></span>

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

### <span data-ttu-id="55fc1-405">-UserAgent</span><span class="sxs-lookup"><span data-stu-id="55fc1-405">-UserAgent</span></span>

<span data-ttu-id="55fc1-406">指定 Web 请求的用户代理字符串。</span><span class="sxs-lookup"><span data-stu-id="55fc1-406">Specifies a user agent string for the web request.</span></span>

<span data-ttu-id="55fc1-407">默认的用户代理类似于 `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` 每个操作系统和平台稍有不同。</span><span class="sxs-lookup"><span data-stu-id="55fc1-407">The default user agent is similar to `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="55fc1-408">若要使用大多数 internet 浏览器使用的标准用户代理字符串测试网站，请使用 [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) 类的属性，例如 Chrome、FireFox、Microsoft-windows-ie-internetexplorer、Opera 和 Safari。</span><span class="sxs-lookup"><span data-stu-id="55fc1-408">To test a website with the standard user agent string that is used by most internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) class, such as Chrome, FireFox, InternetExplorer, Opera, and Safari.</span></span>

<span data-ttu-id="55fc1-409">例如，以下命令使用 Internet Explorer 的用户代理字符串：</span><span class="sxs-lookup"><span data-stu-id="55fc1-409">For example, the following command uses the user agent string for Internet Explorer:</span></span>

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

### <span data-ttu-id="55fc1-410">-WebSession</span><span class="sxs-lookup"><span data-stu-id="55fc1-410">-WebSession</span></span>

<span data-ttu-id="55fc1-411">指定一个 Web 请求会话。</span><span class="sxs-lookup"><span data-stu-id="55fc1-411">Specifies a web request session.</span></span> <span data-ttu-id="55fc1-412">输入变量名称，包括美元符号 (`$`) 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-412">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="55fc1-413">若要在 Web 请求会话中重写某个值，请使用 cmdlet 参数，如 **UserAgent** 或 **Credential** 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-413">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential** .</span></span> <span data-ttu-id="55fc1-414">参数值优先于 Web 请求会话中的值。</span><span class="sxs-lookup"><span data-stu-id="55fc1-414">Parameter values take precedence over values in the web request session.</span></span> <span data-ttu-id="55fc1-415">为 `Content-Type` **正文** 提供 **MultipartFormDataContent** 对象时，也会重写与内容相关的标头（例如）。</span><span class="sxs-lookup"><span data-stu-id="55fc1-415">Content related headers, such as `Content-Type`, are also be overridden when a **MultipartFormDataContent** object is supplied for **Body** .</span></span>

<span data-ttu-id="55fc1-416">与远程会话不同，web 请求会话不是持续性连接。</span><span class="sxs-lookup"><span data-stu-id="55fc1-416">Unlike a remote session, the web request session isn't a persistent connection.</span></span> <span data-ttu-id="55fc1-417">它是一个包含有关连接和请求的信息的对象，包括 cookie、凭据、最大重定向值和用户代理字符串。</span><span class="sxs-lookup"><span data-stu-id="55fc1-417">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="55fc1-418">可用于共享 Web 请求之间的状态和数据。</span><span class="sxs-lookup"><span data-stu-id="55fc1-418">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="55fc1-419">若要创建 web 请求会话，请在命令的 **SessionVariable** 参数的值中输入一个不带美元符号的变量名称 `Invoke-WebRequest` 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-419">To create a web request session, enter a variable name, without a dollar sign, in the value of the **SessionVariable** parameter of an `Invoke-WebRequest` command.</span></span> <span data-ttu-id="55fc1-420">`Invoke-WebRequest` 创建会话并将其保存在变量中。</span><span class="sxs-lookup"><span data-stu-id="55fc1-420">`Invoke-WebRequest` creates the session and saves it in the variable.</span></span> <span data-ttu-id="55fc1-421">在后续命令中，将该变量用作 **WebSession** 参数的值。</span><span class="sxs-lookup"><span data-stu-id="55fc1-421">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="55fc1-422">不能在同一命令中使用 **SessionVariable** 和 **WebSession** 参数。</span><span class="sxs-lookup"><span data-stu-id="55fc1-422">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="55fc1-423">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="55fc1-423">CommonParameters</span></span>

<span data-ttu-id="55fc1-424">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="55fc1-424">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="55fc1-425">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="55fc1-425">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="55fc1-426">输入</span><span class="sxs-lookup"><span data-stu-id="55fc1-426">INPUTS</span></span>

### <span data-ttu-id="55fc1-427">System.Object</span><span class="sxs-lookup"><span data-stu-id="55fc1-427">System.Object</span></span>

<span data-ttu-id="55fc1-428">你可以通过管道将 web 请求的正文传递给 `Invoke-WebRequest` 。</span><span class="sxs-lookup"><span data-stu-id="55fc1-428">You can pipe the body of a web request to `Invoke-WebRequest`.</span></span>

## <span data-ttu-id="55fc1-429">输出</span><span class="sxs-lookup"><span data-stu-id="55fc1-429">OUTPUTS</span></span>

### <span data-ttu-id="55fc1-430">BasicHtmlWebResponseObject。</span><span class="sxs-lookup"><span data-stu-id="55fc1-430">Microsoft.PowerShell.Commands.BasicHtmlWebResponseObject</span></span>

## <span data-ttu-id="55fc1-431">注释</span><span class="sxs-lookup"><span data-stu-id="55fc1-431">NOTES</span></span>

<span data-ttu-id="55fc1-432">从 PowerShell 6.0.0 开始 `Invoke-WebRequest` 仅支持基本分析。</span><span class="sxs-lookup"><span data-stu-id="55fc1-432">Beginning with PowerShell 6.0.0 `Invoke-WebRequest` supports basic parsing only.</span></span>

<span data-ttu-id="55fc1-433">有关详细信息，请参阅 [BasicHtmlWebResponseObject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject)。</span><span class="sxs-lookup"><span data-stu-id="55fc1-433">For more information, see [BasicHtmlWebResponseObject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject).</span></span>

<span data-ttu-id="55fc1-434">由于 .NET Core 3.1 中发生了更改，因此 PowerShell 7.0 和更高版本使用 [DefaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) 属性来确定代理配置。</span><span class="sxs-lookup"><span data-stu-id="55fc1-434">Because of changes in .NET Core 3.1, PowerShell 7.0 and higher use the [HttpClient.DefaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) Property to determine the proxy configuration.</span></span>

<span data-ttu-id="55fc1-435">此属性的值由您的平台确定：</span><span class="sxs-lookup"><span data-stu-id="55fc1-435">The value of this property is determined by your platform:</span></span>

- <span data-ttu-id="55fc1-436">**对于 Windows** ：从环境变量读取代理配置。</span><span class="sxs-lookup"><span data-stu-id="55fc1-436">**For Windows** : Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="55fc1-437">如果未定义这些变量，则将从用户的代理设置派生属性。</span><span class="sxs-lookup"><span data-stu-id="55fc1-437">If those variables are not defined the property is derived from the user's proxy settings.</span></span>
- <span data-ttu-id="55fc1-438">**对于 macOS** ：从环境变量读取代理配置。</span><span class="sxs-lookup"><span data-stu-id="55fc1-438">**For macOS** : Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="55fc1-439">如果未定义这些变量，则属性派生自系统的代理设置。</span><span class="sxs-lookup"><span data-stu-id="55fc1-439">If those variables are not defined the property is derived from the system's proxy settings.</span></span>
- <span data-ttu-id="55fc1-440">**对于 Linux** ：从环境变量读取代理配置。</span><span class="sxs-lookup"><span data-stu-id="55fc1-440">**For Linux** : Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="55fc1-441">如果未定义这些变量，则属性初始化将绕过所有地址的非配置实例。</span><span class="sxs-lookup"><span data-stu-id="55fc1-441">If those variables are not defined the property initializes a non-configured instance that bypasses all addresses.</span></span>

<span data-ttu-id="55fc1-442">用于 `DefaultProxy` 在 Windows 和基于 Unix 的平台上进行初始化的环境变量包括：</span><span class="sxs-lookup"><span data-stu-id="55fc1-442">The environment variables used for `DefaultProxy` initialization on Windows and Unix-based platforms are:</span></span>

- <span data-ttu-id="55fc1-443">` HTTP_PROXY`：用于 HTTP 请求的代理服务器的主机名或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="55fc1-443">` HTTP_PROXY`: the hostname or IP address of the proxy server used on HTTP requests.</span></span>
- <span data-ttu-id="55fc1-444">`HTTPS_PROXY`：用于 HTTPS 请求的代理服务器的主机名或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="55fc1-444">`HTTPS_PROXY`: the hostname or IP address of the proxy server used on HTTPS requests.</span></span>
- <span data-ttu-id="55fc1-445">`ALL_PROXY`：在 HTTP 和 HTTPS 请求上使用的代理服务器的主机名或 IP 地址（ `HTTP_PROXY` 如果 `HTTPS_PROXY` 未定义）或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="55fc1-445">`ALL_PROXY`: the hostname or IP address of the proxy server used on HTTP and HTTPS requests in case `HTTP_PROXY` or `HTTPS_PROXY` are not defined.</span></span>
- <span data-ttu-id="55fc1-446">`NO_PROXY`：应从代理中排除的主机名的逗号分隔列表。</span><span class="sxs-lookup"><span data-stu-id="55fc1-446">`NO_PROXY`: a comma-separated list of hostnames that should be excluded from proxying.</span></span>

## <span data-ttu-id="55fc1-447">相关链接</span><span class="sxs-lookup"><span data-stu-id="55fc1-447">RELATED LINKS</span></span>

[<span data-ttu-id="55fc1-448">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="55fc1-448">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="55fc1-449">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="55fc1-449">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="55fc1-450">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="55fc1-450">ConvertTo-Json</span></span>](ConvertTo-Json.md)
