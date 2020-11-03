---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 07/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertfrom-securestring?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SecureString
ms.openlocfilehash: ed9ef1102c1e34670b3cb5664a227f86124812a0
ms.sourcegitcommit: b7ff031a12afd04910aeb98345ebee92f5845b0c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "93199180"
---
# <span data-ttu-id="f5bbe-103">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="f5bbe-103">ConvertFrom-SecureString</span></span>

## <span data-ttu-id="f5bbe-104">摘要</span><span class="sxs-lookup"><span data-stu-id="f5bbe-104">SYNOPSIS</span></span>
<span data-ttu-id="f5bbe-105">将安全字符串转换为加密的标准字符串。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-105">Converts a secure string to an encrypted standard string.</span></span>

## <span data-ttu-id="f5bbe-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f5bbe-106">SYNTAX</span></span>

### <span data-ttu-id="f5bbe-107">Secure（默认值）</span><span class="sxs-lookup"><span data-stu-id="f5bbe-107">Secure (Default)</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### <span data-ttu-id="f5bbe-108">AsPlainText</span><span class="sxs-lookup"><span data-stu-id="f5bbe-108">AsPlainText</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-AsPlainText] [<CommonParameters>]
```

### <span data-ttu-id="f5bbe-109">打开</span><span class="sxs-lookup"><span data-stu-id="f5bbe-109">Open</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-Key <Byte[]>] [<CommonParameters>]
```

## <span data-ttu-id="f5bbe-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f5bbe-110">DESCRIPTION</span></span>

<span data-ttu-id="f5bbe-111">**Convertfrom-csv** cmdlet 将 ( **SecureString** ) 的安全字符串转换为加密的标准 **字符串 (的** ) 。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-111">The **ConvertFrom-SecureString** cmdlet converts a secure string ( **System.Security.SecureString** ) into an encrypted standard string ( **System.String** ).</span></span> <span data-ttu-id="f5bbe-112">和安全字符串不同，加密的标准字符串可保存在文件中以供以后使用。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-112">Unlike a secure string, an encrypted standard string can be saved in a file for later use.</span></span> <span data-ttu-id="f5bbe-113">使用 cmdlet 可以将加密的标准字符串转换回其安全字符串格式 `ConvertTo-SecureString` 。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-113">The encrypted standard string can be converted back to its secure string format by using the `ConvertTo-SecureString` cmdlet.</span></span>

<span data-ttu-id="f5bbe-114">如果使用 **Key** 或 **SecureKey** 参数指定加密密钥，则使用高级加密标准 (AES) 加密算法。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-114">If an encryption key is specified by using the **Key** or **SecureKey** parameters, the Advanced Encryption Standard (AES) encryption algorithm is used.</span></span> <span data-ttu-id="f5bbe-115">指定的密钥必须具有 128、192 或 256 字节的长度，因为这些是 AES 加密算法支持的密钥长度。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-115">The specified key must have a length of 128, 192, or 256 bits because those are the key lengths supported by the AES encryption algorithm.</span></span> <span data-ttu-id="f5bbe-116">如果未指定密钥，则使用 Windows 数据保护 API (DPAPI) 加密标准字符串表示形式。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-116">If no key is specified, the Windows Data Protection API (DPAPI) is used to encrypt the standard string representation.</span></span>

> [!NOTE]
> <span data-ttu-id="f5bbe-117">请注意，在非 Windows 系统上，每个 [DotNet](/dotnet/api/system.security.securestring?view=netcore-2.1#remarks)不会加密 SecureString 的内容。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-117">Note that per [DotNet](/dotnet/api/system.security.securestring?view=netcore-2.1#remarks), the contents of a SecureString are not encrypted on non-Windows systems.</span></span>

## <span data-ttu-id="f5bbe-118">示例</span><span class="sxs-lookup"><span data-stu-id="f5bbe-118">EXAMPLES</span></span>

### <span data-ttu-id="f5bbe-119">示例1：创建安全字符串</span><span class="sxs-lookup"><span data-stu-id="f5bbe-119">Example 1: Create a secure string</span></span>

```powershell
$SecureString = Read-Host -AsSecureString
```

<span data-ttu-id="f5bbe-120">此命令从你在命令提示符处键入的字符创建安全字符串。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-120">This command creates a secure string from characters that you type at the command prompt.</span></span> <span data-ttu-id="f5bbe-121">输入命令后，键入要存储为安全字符串的字符串。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-121">After entering the command, type the string you want to store as a secure string.</span></span> <span data-ttu-id="f5bbe-122">将显示一个星号 (`*`) ，用于表示你键入的每个字符。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-122">An asterisk (`*`) is displayed to represent each character that you type.</span></span>

### <span data-ttu-id="f5bbe-123">示例2：将安全字符串转换为加密的标准字符串</span><span class="sxs-lookup"><span data-stu-id="f5bbe-123">Example 2: Convert a secure string to an encrypted standard string</span></span>

```powershell
$StandardString = ConvertFrom-SecureString $SecureString
```

<span data-ttu-id="f5bbe-124">此命令将变量中的安全字符串转换 `$SecureString` 为加密的标准字符串。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-124">This command converts the secure string in the `$SecureString` variable to an encrypted standard string.</span></span> <span data-ttu-id="f5bbe-125">生成的加密标准字符串存储在变量中 `$StandardString` 。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-125">The resulting encrypted standard string is stored in the `$StandardString` variable.</span></span>

### <span data-ttu-id="f5bbe-126">示例3：使用192位密钥将安全字符串转换为加密的标准字符串</span><span class="sxs-lookup"><span data-stu-id="f5bbe-126">Example 3: Convert a secure string to an encrypted standard string with a 192-bit key</span></span>

```powershell
$Key = (3,4,2,3,56,34,254,222,1,1,2,23,42,54,33,233,1,34,2,7,6,5,35,43)
$StandardString = ConvertFrom-SecureString $SecureString -Key $Key
```

<span data-ttu-id="f5bbe-127">这些命令使用高级加密标准 (AES) 算法将变量中存储的安全字符串转换 `$SecureString` 为具有192位密钥的加密的标准字符串。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-127">These commands use the Advanced Encryption Standard (AES) algorithm to convert the secure string stored in the `$SecureString` variable to an encrypted standard string with a 192-bit key.</span></span> <span data-ttu-id="f5bbe-128">生成的加密标准字符串存储在变量中 `$StandardString` 。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-128">The resulting encrypted standard string is stored in the `$StandardString` variable.</span></span>

<span data-ttu-id="f5bbe-129">第一个命令将密钥存储在 `$Key` 变量中。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-129">The first command stores a key in the `$Key` variable.</span></span> <span data-ttu-id="f5bbe-130">该密钥是24个十进制数字的数组，其中每个数字都必须小于256，才能容纳在一个无符号字节内。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-130">The key is an array of 24 decimal numerals, each of which must be less than 256 to fit within a single unsigned byte.</span></span>

<span data-ttu-id="f5bbe-131">由于每个十进制数字代表单个字节 (8 位) ，因此， (8 x 24) ，该密钥的总大小为192位。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-131">Because each decimal numeral represents a single byte (8 bits), the key has 24 digits for a total of 192 bits (8 x 24).</span></span> <span data-ttu-id="f5bbe-132">这是用于 AES 算法的有效的密钥长度值。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-132">This is a valid key length for the AES algorithm.</span></span>

<span data-ttu-id="f5bbe-133">第二个命令使用变量中的密钥 `$Key` 将安全字符串转换为加密的标准字符串。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-133">The second command uses the key in the `$Key` variable to convert the secure string to an encrypted standard string.</span></span>

### <span data-ttu-id="f5bbe-134">示例4：将安全字符串直接转换为纯文本字符串</span><span class="sxs-lookup"><span data-stu-id="f5bbe-134">Example 4: Convert a secure string directly to a plaintext string</span></span>

```powershell
$secureString = ConvertTo-SecureString -String 'Example' -AsPlainText
$secureString # 'System.Security.SecureString'
ConvertFrom-SecureString -SecureString $secureString -AsPlainText # 'Example'
```

## <span data-ttu-id="f5bbe-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f5bbe-135">PARAMETERS</span></span>

### <span data-ttu-id="f5bbe-136">-AsPlainText</span><span class="sxs-lookup"><span data-stu-id="f5bbe-136">-AsPlainText</span></span>

<span data-ttu-id="f5bbe-137">设置后， `ConvertFrom-SecureString` 会将安全字符串转换为加密的纯文本字符串作为输出。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-137">When set, `ConvertFrom-SecureString` will convert secure strings to the decrypted plaintext string as output.</span></span>

<span data-ttu-id="f5bbe-138">此参数已添加到 PowerShell 7.0。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-138">This paramater was added in PowerShell 7.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsPlainText
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f5bbe-139">-Key</span><span class="sxs-lookup"><span data-stu-id="f5bbe-139">-Key</span></span>

<span data-ttu-id="f5bbe-140">将加密密钥指定为字节数组。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-140">Specifies the encryption key as a byte array.</span></span>

```yaml
Type: System.Byte[]
Parameter Sets: Open
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f5bbe-141">-SecureKey</span><span class="sxs-lookup"><span data-stu-id="f5bbe-141">-SecureKey</span></span>

<span data-ttu-id="f5bbe-142">将加密密钥指定为安全字符串。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-142">Specifies the encryption key as a secure string.</span></span> <span data-ttu-id="f5bbe-143">在将安全字符串值用作密钥之前，需将其转换为字节数组。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-143">The secure string value is converted to a byte array before being used as the key.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: Secure
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f5bbe-144">-SecureString</span><span class="sxs-lookup"><span data-stu-id="f5bbe-144">-SecureString</span></span>

<span data-ttu-id="f5bbe-145">指定安全字符串转换为加密的标准字符串。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-145">Specifies the secure string to convert to an encrypted standard string.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f5bbe-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f5bbe-146">CommonParameters</span></span>

<span data-ttu-id="f5bbe-147">此 cmdlet 支持通用参数： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、、、、、、、 `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-147">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`,`-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span>
<span data-ttu-id="f5bbe-148">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f5bbe-149">输入</span><span class="sxs-lookup"><span data-stu-id="f5bbe-149">INPUTS</span></span>

### <span data-ttu-id="f5bbe-150">System.Security.SecureString</span><span class="sxs-lookup"><span data-stu-id="f5bbe-150">System.Security.SecureString</span></span>

<span data-ttu-id="f5bbe-151">可以通过管道将 **SecureString** 对象传递给 Convertfrom-csv-SecureString。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-151">You can pipe a **SecureString** object to ConvertFrom-SecureString.</span></span>

## <span data-ttu-id="f5bbe-152">输出</span><span class="sxs-lookup"><span data-stu-id="f5bbe-152">OUTPUTS</span></span>

### <span data-ttu-id="f5bbe-153">System.String</span><span class="sxs-lookup"><span data-stu-id="f5bbe-153">System.String</span></span>

<span data-ttu-id="f5bbe-154">ConvertFrom-SecureString 返回标准字符串对象。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-154">ConvertFrom-SecureString returns a standard string object.</span></span>

## <span data-ttu-id="f5bbe-155">注释</span><span class="sxs-lookup"><span data-stu-id="f5bbe-155">NOTES</span></span>

- <span data-ttu-id="f5bbe-156">若要从在命令提示符处键入的字符创建安全字符串，请使用 cmdlet 的 **AsSecureString** 参数 `Read-Host` 。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-156">To create a secure string from characters that are typed at the command prompt, use the **AsSecureString** parameter of the `Read-Host` cmdlet.</span></span>
- <span data-ttu-id="f5bbe-157">使用 **key** 或 **SecureKey** 参数指定密钥时，密钥长度必须正确。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-157">When you use the **Key** or **SecureKey** parameters to specify a key, the key length must be correct.</span></span> <span data-ttu-id="f5bbe-158">例如，128位的密钥可以指定为16个十进制数字的字节数组。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-158">For example, a key of 128 bits can be specified as a byte array of 16 decimal numerals.</span></span>
  <span data-ttu-id="f5bbe-159">同样，192位和256位的密钥分别对应于24和32十进制数字的字节数组。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-159">Similarly, 192-bit and 256-bit keys correspond to byte arrays of 24 and 32 decimal numerals, respectively.</span></span>
- <span data-ttu-id="f5bbe-160">一些字符（如图释）对应于包含它们的字符串中的几个码位。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-160">Some characters, such as emoticons, correspond to several code points in the string that contains them.</span></span> <span data-ttu-id="f5bbe-161">避免使用这些字符，因为在密码中使用时，它们可能会导致问题和误解。</span><span class="sxs-lookup"><span data-stu-id="f5bbe-161">Avoid using these characters because they may cause problems and misunderstandings when used in a password.</span></span>

## <span data-ttu-id="f5bbe-162">相关链接</span><span class="sxs-lookup"><span data-stu-id="f5bbe-162">RELATED LINKS</span></span>

[<span data-ttu-id="f5bbe-163">ConvertTo-SecureString</span><span class="sxs-lookup"><span data-stu-id="f5bbe-163">ConvertTo-SecureString</span></span>](ConvertTo-SecureString.md)

[<span data-ttu-id="f5bbe-164">Read-Host</span><span class="sxs-lookup"><span data-stu-id="f5bbe-164">Read-Host</span></span>](../Microsoft.PowerShell.Utility/Read-Host.md)
