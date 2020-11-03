---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Send-MailMessage
ms.openlocfilehash: 6603e427a44d5b45d339b8cbf3f56a6b8d25e699
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2020
ms.locfileid: "93196912"
---
# <span data-ttu-id="aa19b-103">Send-MailMessage</span><span class="sxs-lookup"><span data-stu-id="aa19b-103">Send-MailMessage</span></span>

## <span data-ttu-id="aa19b-104">摘要</span><span class="sxs-lookup"><span data-stu-id="aa19b-104">SYNOPSIS</span></span>
<span data-ttu-id="aa19b-105">发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="aa19b-105">Sends an email message.</span></span>

## <span data-ttu-id="aa19b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="aa19b-106">SYNTAX</span></span>

### <span data-ttu-id="aa19b-107">全部</span><span class="sxs-lookup"><span data-stu-id="aa19b-107">All</span></span>

```
Send-MailMessage [-Attachments <String[]>] [-Bcc <String[]>] [[-Body] <String>] [-BodyAsHtml]
 [-Encoding <Encoding>] [-Cc <String[]>] [-DeliveryNotificationOption <DeliveryNotificationOptions>]
 -From <String> [[-SmtpServer] <String>] [-Priority <MailPriority>] [-ReplyTo <String[]>]
 [[-Subject] <String>] [-To] <String[]> [-Credential <PSCredential>] [-UseSsl] [-Port <Int32>]
 [<CommonParameters>]
```

## <span data-ttu-id="aa19b-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="aa19b-108">DESCRIPTION</span></span>

<span data-ttu-id="aa19b-109">`Send-MailMessage`Cmdlet 可从 PowerShell 内部发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="aa19b-109">The `Send-MailMessage` cmdlet sends an email message from within PowerShell.</span></span>

<span data-ttu-id="aa19b-110">必须 (SMTP) 服务器指定简单邮件传输协议，否则命令将 `Send-MailMessage` 失败。</span><span class="sxs-lookup"><span data-stu-id="aa19b-110">You must specify a Simple Mail Transfer Protocol (SMTP) server or the `Send-MailMessage` command fails.</span></span> <span data-ttu-id="aa19b-111">使用 **SmtpServer** 参数或将变量设置 `$PSEmailServer` 为有效的 SMTP 服务器。</span><span class="sxs-lookup"><span data-stu-id="aa19b-111">Use the **SmtpServer** parameter or set the `$PSEmailServer` variable to a valid SMTP server.</span></span>
<span data-ttu-id="aa19b-112">分配给的值 `$PSEmailServer` 是 PowerShell 的默认 SMTP 设置。</span><span class="sxs-lookup"><span data-stu-id="aa19b-112">The value assigned to `$PSEmailServer` is the default SMTP setting for PowerShell.</span></span> <span data-ttu-id="aa19b-113">有关详细信息，请参阅 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="aa19b-113">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

> [!WARNING]
> <span data-ttu-id="aa19b-114">`Send-MailMessage`Cmdlet 已过时。</span><span class="sxs-lookup"><span data-stu-id="aa19b-114">The `Send-MailMessage` cmdlet is obsolete.</span></span> <span data-ttu-id="aa19b-115">此 cmdlet 不保证与 SMTP 服务器的安全连接。</span><span class="sxs-lookup"><span data-stu-id="aa19b-115">This cmdlet does not guarantee secure connections to SMTP servers.</span></span> <span data-ttu-id="aa19b-116">虽然 PowerShell 中没有即时替换，但建议你不要使用 `Send-MailMessage` 。</span><span class="sxs-lookup"><span data-stu-id="aa19b-116">While there is no immediate replacement available in PowerShell, we recommend you do not use `Send-MailMessage`.</span></span> <span data-ttu-id="aa19b-117">有关详细信息，请参阅 [平台兼容性说明 DE0005](https://aka.ms/SendMailMessage)。</span><span class="sxs-lookup"><span data-stu-id="aa19b-117">For more information, see [Platform Compatibility note DE0005](https://aka.ms/SendMailMessage).</span></span>

## <span data-ttu-id="aa19b-118">示例</span><span class="sxs-lookup"><span data-stu-id="aa19b-118">EXAMPLES</span></span>

### <span data-ttu-id="aa19b-119">示例1：向其他人发送电子邮件</span><span class="sxs-lookup"><span data-stu-id="aa19b-119">Example 1: Send an email from one person to another person</span></span>

<span data-ttu-id="aa19b-120">此示例将一封电子邮件发送给其他人。</span><span class="sxs-lookup"><span data-stu-id="aa19b-120">This example sends an email message from one person to another person.</span></span>

<span data-ttu-id="aa19b-121">需要使用 **From** 、 **To** 和 **Subject** 参数 `Send-MailMessage` 。</span><span class="sxs-lookup"><span data-stu-id="aa19b-121">The **From** , **To** , and **Subject** parameters are required by `Send-MailMessage`.</span></span> <span data-ttu-id="aa19b-122">此示例使用 `$PSEmailServer` SMTP 服务器的默认变量，因此不需要 **SmtpServer** 参数。</span><span class="sxs-lookup"><span data-stu-id="aa19b-122">This example uses the default `$PSEmailServer` variable for the SMTP server, so the **SmtpServer** parameter is not needed.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>' -Subject 'Test mail'
```

<span data-ttu-id="aa19b-123">`Send-MailMessage`Cmdlet 使用 **From** 参数来指定消息的发送方。</span><span class="sxs-lookup"><span data-stu-id="aa19b-123">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="aa19b-124">**To** 参数指定消息的接收方。</span><span class="sxs-lookup"><span data-stu-id="aa19b-124">The **To** parameter specifies the message's recipient.</span></span> <span data-ttu-id="aa19b-125">**Subject** 参数使用文本字符串 **测试邮件** 作为消息，因为不包括可选的 **Body** 参数。</span><span class="sxs-lookup"><span data-stu-id="aa19b-125">The **Subject** parameter uses the text string **Test mail** as the message because the optional **Body** parameter is not included.</span></span>

### <span data-ttu-id="aa19b-126">示例2：发送附件</span><span class="sxs-lookup"><span data-stu-id="aa19b-126">Example 2: Send an attachment</span></span>

<span data-ttu-id="aa19b-127">此示例发送一封电子邮件，其中包含附件。</span><span class="sxs-lookup"><span data-stu-id="aa19b-127">This example sends an email message with an attachment.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>', 'User03 <user03@fabrikam.com>' -Subject 'Sending the Attachment' -Body "Forgot to send the attachment. Sending now." -Attachments .\data.csv -Priority High -DeliveryNotificationOption OnSuccess, OnFailure -SmtpServer 'smtp.fabrikam.com'
```

<span data-ttu-id="aa19b-128">`Send-MailMessage`Cmdlet 使用 **From** 参数来指定消息的发送方。</span><span class="sxs-lookup"><span data-stu-id="aa19b-128">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="aa19b-129">**To** 参数指定邮件的收件人。</span><span class="sxs-lookup"><span data-stu-id="aa19b-129">The **To** parameter specifies the message's recipients.</span></span> <span data-ttu-id="aa19b-130">**Subject** 参数描述消息的内容。</span><span class="sxs-lookup"><span data-stu-id="aa19b-130">The **Subject** parameter describes the content of the message.</span></span> <span data-ttu-id="aa19b-131">**Body** 参数是消息的内容。</span><span class="sxs-lookup"><span data-stu-id="aa19b-131">The **Body** parameter is the content of the message.</span></span>

<span data-ttu-id="aa19b-132">**附件** 参数指定附加到电子邮件的当前目录中的文件。</span><span class="sxs-lookup"><span data-stu-id="aa19b-132">The **Attachments** parameter specifies the file in the current directory that is attached to the email message.</span></span> <span data-ttu-id="aa19b-133">**Priority** 参数将消息设置为 **高** 优先级。</span><span class="sxs-lookup"><span data-stu-id="aa19b-133">The **Priority** parameter sets the message to **High** priority.</span></span> <span data-ttu-id="aa19b-134">**-DeliveryNotificationOption** 参数指定了两个值： **OnSuccess** 和 **OnFailure** 。</span><span class="sxs-lookup"><span data-stu-id="aa19b-134">The **-DeliveryNotificationOption** parameter specifies two values, **OnSuccess** and **OnFailure** .</span></span> <span data-ttu-id="aa19b-135">发件人将收到电子邮件通知，以确认消息传递的成功或失败。</span><span class="sxs-lookup"><span data-stu-id="aa19b-135">The sender will receive email notifications to confirm the success or failure of the message delivery.</span></span>
<span data-ttu-id="aa19b-136">**SmtpServer** 参数将 SMTP 服务器设置为 **smtp.fabrikam.com** 。</span><span class="sxs-lookup"><span data-stu-id="aa19b-136">The **SmtpServer** parameter sets the SMTP server to **smtp.fabrikam.com** .</span></span>

### <span data-ttu-id="aa19b-137">示例3：向邮件列表发送电子邮件</span><span class="sxs-lookup"><span data-stu-id="aa19b-137">Example 3: Send email to a mailing list</span></span>

<span data-ttu-id="aa19b-138">此示例向邮件列表发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="aa19b-138">This example sends an email message to a mailing list.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'ITGroup <itdept@fabrikam.com>' -Cc 'User02 <user02@fabrikam.com>' -Bcc 'ITMgr <itmgr@fabrikam.com>' -Subject "Don't forget today's meeting!" -Credential domain01\admin01 -UseSsl
```

<span data-ttu-id="aa19b-139">`Send-MailMessage`Cmdlet 使用 **From** 参数来指定消息的发送方。</span><span class="sxs-lookup"><span data-stu-id="aa19b-139">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="aa19b-140">**To** 参数指定邮件的收件人。</span><span class="sxs-lookup"><span data-stu-id="aa19b-140">The **To** parameter specifies the message's recipients.</span></span> <span data-ttu-id="aa19b-141">**Cc** 参数将消息的副本发送到指定的收件人。</span><span class="sxs-lookup"><span data-stu-id="aa19b-141">The **Cc** parameter sends a copy of the message to the specified recipient.</span></span> <span data-ttu-id="aa19b-142">**Bcc** 参数发送邮件的直接副本。</span><span class="sxs-lookup"><span data-stu-id="aa19b-142">The **Bcc** parameter sends a blind copy of the message.</span></span> <span data-ttu-id="aa19b-143">直接副本是隐藏在其他收件人的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="aa19b-143">A blind copy is an email address that is hidden from the other recipients.</span></span> <span data-ttu-id="aa19b-144">**Subject** 参数是消息，因为不包括可选的 **Body** 参数。</span><span class="sxs-lookup"><span data-stu-id="aa19b-144">The **Subject** parameter is the message because the optional **Body** parameter is not included.</span></span>

<span data-ttu-id="aa19b-145">**Credential** 参数指定用于发送消息的域管理员凭据。</span><span class="sxs-lookup"><span data-stu-id="aa19b-145">The **Credential** parameter specifies a domain administrator's credentials are used to send the message.</span></span> <span data-ttu-id="aa19b-146">**UseSsl** 参数指定安全套接字层 (SSL) 创建安全连接。</span><span class="sxs-lookup"><span data-stu-id="aa19b-146">The **UseSsl** parameter specifies that Secure Socket Layer (SSL) creates a secure connection.</span></span>

## <span data-ttu-id="aa19b-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aa19b-147">PARAMETERS</span></span>

### <span data-ttu-id="aa19b-148">-Attachments</span><span class="sxs-lookup"><span data-stu-id="aa19b-148">-Attachments</span></span>

<span data-ttu-id="aa19b-149">指定要附加到电子邮件的文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="aa19b-149">Specifies the path and file names of files to be attached to the email message.</span></span> <span data-ttu-id="aa19b-150">可以使用此参数或通过管道将路径和文件名传递给 `Send-MailMessage` 。</span><span class="sxs-lookup"><span data-stu-id="aa19b-150">You can use this parameter or pipe the paths and file names to `Send-MailMessage`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PsPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="aa19b-151">-Bcc</span><span class="sxs-lookup"><span data-stu-id="aa19b-151">-Bcc</span></span>

<span data-ttu-id="aa19b-152">指定接收邮件副本但未列为邮件收件人的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="aa19b-152">Specifies the email addresses that receive a copy of the mail but are not listed as recipients of the message.</span></span> <span data-ttu-id="aa19b-153">输入名称 (可选) 和电子邮件地址，如 `Name <someone@fabrikam.com>` 。</span><span class="sxs-lookup"><span data-stu-id="aa19b-153">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aa19b-154">-Body</span><span class="sxs-lookup"><span data-stu-id="aa19b-154">-Body</span></span>

<span data-ttu-id="aa19b-155">指定电子邮件的内容。</span><span class="sxs-lookup"><span data-stu-id="aa19b-155">Specifies the content of the email message.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aa19b-156">-BodyAsHtml</span><span class="sxs-lookup"><span data-stu-id="aa19b-156">-BodyAsHtml</span></span>

<span data-ttu-id="aa19b-157">指定 **Body** 参数的值包含 HTML。</span><span class="sxs-lookup"><span data-stu-id="aa19b-157">Specifies that the value of the **Body** parameter contains HTML.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: BAH

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aa19b-158">-Cc</span><span class="sxs-lookup"><span data-stu-id="aa19b-158">-Cc</span></span>

<span data-ttu-id="aa19b-159">指定电子邮件的抄送 (CC) 发送到的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="aa19b-159">Specifies the email addresses to which a carbon copy (CC) of the email message is sent.</span></span> <span data-ttu-id="aa19b-160">输入名称 (可选) 和电子邮件地址，如 `Name <someone@fabrikam.com>` 。</span><span class="sxs-lookup"><span data-stu-id="aa19b-160">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aa19b-161">-Credential</span><span class="sxs-lookup"><span data-stu-id="aa19b-161">-Credential</span></span>

<span data-ttu-id="aa19b-162">指定有权执行此操作的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="aa19b-162">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="aa19b-163">默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="aa19b-163">The default is the current user.</span></span>

<span data-ttu-id="aa19b-164">键入用户名，如 **User01** 或 **Domain01\User01** 。</span><span class="sxs-lookup"><span data-stu-id="aa19b-164">Type a user name, such as **User01** or **Domain01\User01** .</span></span> <span data-ttu-id="aa19b-165">或者输入 **PSCredential** 对象，例如 cmdlet 中的一个 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="aa19b-165">Or, enter a **PSCredential** object, such as one from the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="aa19b-166">凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="aa19b-166">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="aa19b-167">有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="aa19b-167">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aa19b-168">-DeliveryNotificationOption</span><span class="sxs-lookup"><span data-stu-id="aa19b-168">-DeliveryNotificationOption</span></span>

<span data-ttu-id="aa19b-169">指定电子邮件的送达通知选项。</span><span class="sxs-lookup"><span data-stu-id="aa19b-169">Specifies the delivery notification options for the email message.</span></span> <span data-ttu-id="aa19b-170">你可以指定多个值。</span><span class="sxs-lookup"><span data-stu-id="aa19b-170">You can specify multiple values.</span></span>
<span data-ttu-id="aa19b-171">None 为默认值。</span><span class="sxs-lookup"><span data-stu-id="aa19b-171">None is the default value.</span></span> <span data-ttu-id="aa19b-172">此参数的别名为 **DNO** 。</span><span class="sxs-lookup"><span data-stu-id="aa19b-172">The alias for this parameter is **DNO** .</span></span>

<span data-ttu-id="aa19b-173">送达通知将发送到 **From** 参数中的地址。</span><span class="sxs-lookup"><span data-stu-id="aa19b-173">The delivery notifications are sent to the address in the **From** parameter.</span></span>

<span data-ttu-id="aa19b-174">此参数可接受的值如下所示：</span><span class="sxs-lookup"><span data-stu-id="aa19b-174">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="aa19b-175">`None`：无通知。</span><span class="sxs-lookup"><span data-stu-id="aa19b-175">`None`: No notification.</span></span>
- <span data-ttu-id="aa19b-176">`OnSuccess`：通知传送是否成功。</span><span class="sxs-lookup"><span data-stu-id="aa19b-176">`OnSuccess`: Notify if the delivery is successful.</span></span>
- <span data-ttu-id="aa19b-177">`OnFailure`：通知传送是否失败。</span><span class="sxs-lookup"><span data-stu-id="aa19b-177">`OnFailure`: Notify if the delivery is unsuccessful.</span></span>
- <span data-ttu-id="aa19b-178">`Delay`：通知传送是否已延迟。</span><span class="sxs-lookup"><span data-stu-id="aa19b-178">`Delay`: Notify if the delivery is delayed.</span></span>
- <span data-ttu-id="aa19b-179">`Never`：从不通知。</span><span class="sxs-lookup"><span data-stu-id="aa19b-179">`Never`: Never notify.</span></span>

```yaml
Type: System.Net.Mail.DeliveryNotificationOptions
Parameter Sets: (All)
Aliases: DNO
Accepted values: None, OnSuccess, OnFailure, Delay, Never

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aa19b-180">-Encoding</span><span class="sxs-lookup"><span data-stu-id="aa19b-180">-Encoding</span></span>

<span data-ttu-id="aa19b-181">指定目标文件的编码类型。</span><span class="sxs-lookup"><span data-stu-id="aa19b-181">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="aa19b-182">默认值是 `utf8NoBOM`。</span><span class="sxs-lookup"><span data-stu-id="aa19b-182">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="aa19b-183">此参数可接受的值如下所示：</span><span class="sxs-lookup"><span data-stu-id="aa19b-183">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="aa19b-184">`ascii`：使用 ASCII (7 位) 字符集的编码。</span><span class="sxs-lookup"><span data-stu-id="aa19b-184">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="aa19b-185">`bigendianunicode`：使用大字节序字节顺序对 UTF-16 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="aa19b-185">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="aa19b-186">`oem`：使用 MS-DOS 和控制台程序的默认编码。</span><span class="sxs-lookup"><span data-stu-id="aa19b-186">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="aa19b-187">`unicode`：使用小 endian 字节顺序对 UTF-16 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="aa19b-187">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="aa19b-188">`utf7`：以 UTF-7 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="aa19b-188">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="aa19b-189">`utf8`：以 UTF-8 格式进行编码。</span><span class="sxs-lookup"><span data-stu-id="aa19b-189">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="aa19b-190">`utf8BOM`：以 UTF-8 格式编码 (BOM) </span><span class="sxs-lookup"><span data-stu-id="aa19b-190">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="aa19b-191">`utf8NoBOM`：以 UTF-8 格式编码，而不包含字节顺序标记 (BOM) </span><span class="sxs-lookup"><span data-stu-id="aa19b-191">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="aa19b-192">`utf32`：以32格式编码。</span><span class="sxs-lookup"><span data-stu-id="aa19b-192">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="aa19b-193">从 PowerShell 6.2 开始， **Encoding** 参数还允许已注册代码页的数字 id (如 `-Encoding 1251` (如) 所注册代码页的) 或字符串名称 `-Encoding "windows-1251"` 。</span><span class="sxs-lookup"><span data-stu-id="aa19b-193">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="aa19b-194">有关详细信息，请参阅 .NET 文档中的[编码。](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)</span><span class="sxs-lookup"><span data-stu-id="aa19b-194">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases: BE
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aa19b-195">-From</span><span class="sxs-lookup"><span data-stu-id="aa19b-195">-From</span></span>

<span data-ttu-id="aa19b-196">**From** 参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="aa19b-196">The **From** parameter is required.</span></span> <span data-ttu-id="aa19b-197">此参数指定发件人的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="aa19b-197">This parameter specifies the sender's email address.</span></span> <span data-ttu-id="aa19b-198">输入名称 (可选) 和电子邮件地址，如 `Name <someone@fabrikam.com>` 。</span><span class="sxs-lookup"><span data-stu-id="aa19b-198">Enter a name (optional) and email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aa19b-199">-Port</span><span class="sxs-lookup"><span data-stu-id="aa19b-199">-Port</span></span>

<span data-ttu-id="aa19b-200">指定 SMTP 服务器上的备用端口。</span><span class="sxs-lookup"><span data-stu-id="aa19b-200">Specifies an alternate port on the SMTP server.</span></span> <span data-ttu-id="aa19b-201">默认值为 25，这是默认的 SMTP 端口。</span><span class="sxs-lookup"><span data-stu-id="aa19b-201">The default value is 25, which is the default SMTP port.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 25
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aa19b-202">-Priority</span><span class="sxs-lookup"><span data-stu-id="aa19b-202">-Priority</span></span>

<span data-ttu-id="aa19b-203">指定电子邮件的优先级。</span><span class="sxs-lookup"><span data-stu-id="aa19b-203">Specifies the priority of the email message.</span></span> <span data-ttu-id="aa19b-204">默认值为 Normal。</span><span class="sxs-lookup"><span data-stu-id="aa19b-204">Normal is the default.</span></span> <span data-ttu-id="aa19b-205">此参数可接受的值为 Normal、High 和 Low。</span><span class="sxs-lookup"><span data-stu-id="aa19b-205">The acceptable values for this parameter are Normal, High, and Low.</span></span>

```yaml
Type: System.Net.Mail.MailPriority
Parameter Sets: (All)
Aliases:
Accepted values: Normal, High, Low

Required: False
Position: Named
Default value: Normal
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aa19b-206">-ReplyTo</span><span class="sxs-lookup"><span data-stu-id="aa19b-206">-ReplyTo</span></span>

<span data-ttu-id="aa19b-207">指定其他电子邮件地址，而不是 "发件人" 地址) 使用来回复此邮件 (。</span><span class="sxs-lookup"><span data-stu-id="aa19b-207">Specifies additional email addresses (other than the From address) to use to reply to this message.</span></span>
<span data-ttu-id="aa19b-208">输入名称 (可选) 和电子邮件地址，如 `Name <someone@fabrikam.com>` 。</span><span class="sxs-lookup"><span data-stu-id="aa19b-208">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

<span data-ttu-id="aa19b-209">此参数是在 PowerShell 6.2 中引入的。</span><span class="sxs-lookup"><span data-stu-id="aa19b-209">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aa19b-210">-SmtpServer</span><span class="sxs-lookup"><span data-stu-id="aa19b-210">-SmtpServer</span></span>

<span data-ttu-id="aa19b-211">指定发送电子邮件的 SMTP 服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="aa19b-211">Specifies the name of the SMTP server that sends the email message.</span></span>

<span data-ttu-id="aa19b-212">默认值为 `$PSEmailServer` 首选项变量的值。</span><span class="sxs-lookup"><span data-stu-id="aa19b-212">The default value is the value of the `$PSEmailServer` preference variable.</span></span> <span data-ttu-id="aa19b-213">如果未设置首选项变量，并且未使用此参数，则该 `Send-MailMessage` 命令将失败。</span><span class="sxs-lookup"><span data-stu-id="aa19b-213">If the preference variable is not set and this parameter is not used, the `Send-MailMessage` command fails.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ComputerName

Required: False
Position: 3
Default value: $PSEmailServer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aa19b-214">-Subject</span><span class="sxs-lookup"><span data-stu-id="aa19b-214">-Subject</span></span>

<span data-ttu-id="aa19b-215">**Subject** 参数不是必需的。</span><span class="sxs-lookup"><span data-stu-id="aa19b-215">The **Subject** parameter isn't required.</span></span> <span data-ttu-id="aa19b-216">此参数指定电子邮件的主题。</span><span class="sxs-lookup"><span data-stu-id="aa19b-216">This parameter specifies the subject of the email message.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sub

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aa19b-217">-To</span><span class="sxs-lookup"><span data-stu-id="aa19b-217">-To</span></span>

<span data-ttu-id="aa19b-218">**To** 参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="aa19b-218">The **To** parameter is required.</span></span> <span data-ttu-id="aa19b-219">此参数指定收件人的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="aa19b-219">This parameter specifies the recipient's email address.</span></span> <span data-ttu-id="aa19b-220">如果有多个收件人，请用逗号分隔其地址 (`,`) 。</span><span class="sxs-lookup"><span data-stu-id="aa19b-220">If there are multiple recipients, separate their addresses with a comma (`,`).</span></span> <span data-ttu-id="aa19b-221">输入名称 (可选) 和电子邮件地址，如 `Name <someone@fabrikam.com>` 。</span><span class="sxs-lookup"><span data-stu-id="aa19b-221">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

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

### <span data-ttu-id="aa19b-222">-UseSsl</span><span class="sxs-lookup"><span data-stu-id="aa19b-222">-UseSsl</span></span>

<span data-ttu-id="aa19b-223">安全套接字层 (SSL) 协议用于建立到远程计算机的安全连接以发送邮件。</span><span class="sxs-lookup"><span data-stu-id="aa19b-223">The Secure Sockets Layer (SSL) protocol is used to establish a secure connection to the remote computer to send mail.</span></span> <span data-ttu-id="aa19b-224">默认情况下，不使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="aa19b-224">By default, SSL is not used.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aa19b-225">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aa19b-225">CommonParameters</span></span>

<span data-ttu-id="aa19b-226">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="aa19b-226">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aa19b-227">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="aa19b-227">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aa19b-228">输入</span><span class="sxs-lookup"><span data-stu-id="aa19b-228">INPUTS</span></span>

### <span data-ttu-id="aa19b-229">System.String</span><span class="sxs-lookup"><span data-stu-id="aa19b-229">System.String</span></span>

<span data-ttu-id="aa19b-230">你可以通过管道将附件的路径和文件名传递给 `Send-MailMessage` 。</span><span class="sxs-lookup"><span data-stu-id="aa19b-230">You can pipe the path and file names of attachments to `Send-MailMessage`.</span></span>

## <span data-ttu-id="aa19b-231">输出</span><span class="sxs-lookup"><span data-stu-id="aa19b-231">OUTPUTS</span></span>

### <span data-ttu-id="aa19b-232">无</span><span class="sxs-lookup"><span data-stu-id="aa19b-232">None</span></span>

<span data-ttu-id="aa19b-233">此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="aa19b-233">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="aa19b-234">注释</span><span class="sxs-lookup"><span data-stu-id="aa19b-234">NOTES</span></span>

## <span data-ttu-id="aa19b-235">相关链接</span><span class="sxs-lookup"><span data-stu-id="aa19b-235">RELATED LINKS</span></span>

[<span data-ttu-id="aa19b-236">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="aa19b-236">about_Preference_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[<span data-ttu-id="aa19b-237">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="aa19b-237">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)
