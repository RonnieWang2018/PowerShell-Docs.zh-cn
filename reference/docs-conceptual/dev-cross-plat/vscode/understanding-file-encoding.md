---
title: 了解 VS Code 和 PowerShell 中的文件编码
description: 在 VS Code 和 PowerShell 中配置文件编码
ms.date: 02/28/2019
ms.openlocfilehash: afad189ff20a4e73d25f15c48d6c4982b18f29a3
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142542"
---
# <a name="understanding-file-encoding-in-vs-code-and-powershell"></a><span data-ttu-id="137f1-103">了解 VS Code 和 PowerShell 中的文件编码</span><span class="sxs-lookup"><span data-stu-id="137f1-103">Understanding file encoding in VS Code and PowerShell</span></span>

<span data-ttu-id="137f1-104">使用 VS Code 创建和编辑 PowerShell 脚本时，务必使用正确的字符编码格式保存文件。</span><span class="sxs-lookup"><span data-stu-id="137f1-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="137f1-105">什么是文件编码以及它为什么很重要？</span><span class="sxs-lookup"><span data-stu-id="137f1-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="137f1-106">VS Code 管理人员向缓冲区中输入字符串与对文件系统读取/写入字节块之间的接口。</span><span class="sxs-lookup"><span data-stu-id="137f1-106">VS Code manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="137f1-107">当 VS Code 保存文件时，它会使用文本编码来确定每个字符变为哪些字节。</span><span class="sxs-lookup"><span data-stu-id="137f1-107">When VS Code saves a file, it uses a text encoding to decide what bytes each character becomes.</span></span> <span data-ttu-id="137f1-108">有关详细信息，请参阅 [about_Character_Encoding](/powershell/module/microsoft.powershell.core/about/about_character_encoding)。</span><span class="sxs-lookup"><span data-stu-id="137f1-108">For more information, see [about_Character_Encoding](/powershell/module/microsoft.powershell.core/about/about_character_encoding).</span></span>

<span data-ttu-id="137f1-109">同样，当 PowerShell 运行脚本时，必须将文件中的字节转换为字符以将文件重新构造为 PowerShell 程序。</span><span class="sxs-lookup"><span data-stu-id="137f1-109">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="137f1-110">由于 VS Code 写入文件，而 PowerShell 读取文件，因此它们需要使用相同的编码系统。</span><span class="sxs-lookup"><span data-stu-id="137f1-110">Since VS Code writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="137f1-111">分析 PowerShell 脚本的这一过程是：字节   -> 字符   -> 标记   -> 抽象语法树   -> 执行  。</span><span class="sxs-lookup"><span data-stu-id="137f1-111">This process of parsing a PowerShell script goes: _bytes_ -> _characters_ -> _tokens_ -> _abstract syntax tree_ -> _execution_.</span></span>

<span data-ttu-id="137f1-112">VS Code 和 PowerShell 都使用合理的默认编码配置进行安装。</span><span class="sxs-lookup"><span data-stu-id="137f1-112">Both VS Code and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="137f1-113">但是，PowerShell 使用的默认编码已随着 PowerShell Core (v6.x) 的发布而更改。</span><span class="sxs-lookup"><span data-stu-id="137f1-113">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="137f1-114">若要确保在 VS Code 中使用 PowerShell 或 PowerShell 扩展时不会出现问题，需要正确配置 VS Code 和 PowerShell 设置。</span><span class="sxs-lookup"><span data-stu-id="137f1-114">To ensure you have no problems using PowerShell or the PowerShell extension in VS Code, you need to configure your VS Code and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="137f1-115">编码问题的常见原因</span><span class="sxs-lookup"><span data-stu-id="137f1-115">Common causes of encoding issues</span></span>

<span data-ttu-id="137f1-116">当 VS Code 或脚本文件的编码与 PowerShell 的期望编码不匹配时，会出现编码问题。</span><span class="sxs-lookup"><span data-stu-id="137f1-116">Encoding problems occur when the encoding of VS Code or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="137f1-117">PowerShell 无法自动确定文件编码。</span><span class="sxs-lookup"><span data-stu-id="137f1-117">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="137f1-118">如果使用的字符不在 [7 位 ASCII 字符集](https://ascii.cl/)中，则更可能出现编码问题。</span><span class="sxs-lookup"><span data-stu-id="137f1-118">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="137f1-119">例如：</span><span class="sxs-lookup"><span data-stu-id="137f1-119">For example:</span></span>

<!-- markdownlint-disable MD038 -->
- <span data-ttu-id="137f1-120">扩展的非字母字符，如长破折号 (`—`)、不间断空格 (` `) 或左双引号 (`"`)</span><span class="sxs-lookup"><span data-stu-id="137f1-120">Extended non-letter characters like em-dash (`—`), non-breaking space (` `) or left double quotation mark (`"`)</span></span>
- <span data-ttu-id="137f1-121">重音拉丁字符（`É`、`ü`）</span><span class="sxs-lookup"><span data-stu-id="137f1-121">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="137f1-122">非拉丁字符，如西里尔文（`Д`、`Ц`）</span><span class="sxs-lookup"><span data-stu-id="137f1-122">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="137f1-123">CJK 字符（`本`、`화`、`が`）</span><span class="sxs-lookup"><span data-stu-id="137f1-123">CJK characters (`本`, `화`, `が`)</span></span>

<span data-ttu-id="137f1-124">编码问题的常见原因有：</span><span class="sxs-lookup"><span data-stu-id="137f1-124">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="137f1-125">VS Code 和 PowerShell 的编码尚未更改，仍使用默认设置。</span><span class="sxs-lookup"><span data-stu-id="137f1-125">The encodings of VS Code and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="137f1-126">对于 PowerShell 5.1 及更低版本，默认编码与 VS Code 的编码不同。</span><span class="sxs-lookup"><span data-stu-id="137f1-126">For PowerShell 5.1 and below, the default encoding is different from VS Code's.</span></span>
- <span data-ttu-id="137f1-127">另一个编辑器已打开，并采用新编码覆盖了文件。</span><span class="sxs-lookup"><span data-stu-id="137f1-127">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="137f1-128">ISE 通常会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="137f1-128">This often happens with the ISE.</span></span>
- <span data-ttu-id="137f1-129">文件采用与 VS Code 或 PowerShell 应使用的编码不同的编码签入了源代码管理。</span><span class="sxs-lookup"><span data-stu-id="137f1-129">The file is checked into source control in an encoding that is different from what VS Code or PowerShell expects.</span></span> <span data-ttu-id="137f1-130">当协作者使用具有不同编码配置的编辑器时，可能会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="137f1-130">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="137f1-131">如何判断出现了编码问题</span><span class="sxs-lookup"><span data-stu-id="137f1-131">How to tell when you have encoding issues</span></span>

<span data-ttu-id="137f1-132">编码错误通常表现为脚本中的分析错误。</span><span class="sxs-lookup"><span data-stu-id="137f1-132">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="137f1-133">如果在脚本中发现奇怪的字符序列，则这可能是问题所在。</span><span class="sxs-lookup"><span data-stu-id="137f1-133">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="137f1-134">在以下示例中，短划线 (`–`) 显示为字符 `â&euro;"`：</span><span class="sxs-lookup"><span data-stu-id="137f1-134">In the example below, an en-dash (`–`) appears as the characters `â&euro;"`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â&euro;"From $from â&euro;"To $recipient1 â&euro;"Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="137f1-135">发生此问题的原因是 VS Code 将采用 UTF-8 的字符 `–` 编码为字节 `0xE2 0x80 0x93`。</span><span class="sxs-lookup"><span data-stu-id="137f1-135">This problem occurs because VS Code encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span> <span data-ttu-id="137f1-136">当这些字节解码为 Windows-1252 时，它们会被解释为字符 `â&euro;"`。</span><span class="sxs-lookup"><span data-stu-id="137f1-136">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â&euro;"`.</span></span>

<span data-ttu-id="137f1-137">可能会看到的一些奇怪字符序列包括：</span><span class="sxs-lookup"><span data-stu-id="137f1-137">Some strange character sequences that you might see include:</span></span>

<!-- markdownlint-disable MD038 -->
- <span data-ttu-id="137f1-138">`â&euro;"`（而不是 `–`）</span><span class="sxs-lookup"><span data-stu-id="137f1-138">`â&euro;"` instead of `–`</span></span>
- <span data-ttu-id="137f1-139">`â&euro;"`（而不是 `—`）</span><span class="sxs-lookup"><span data-stu-id="137f1-139">`â&euro;"` instead of `—`</span></span>
- <span data-ttu-id="137f1-140">`Ã„2`（而不是 `Ä`）</span><span class="sxs-lookup"><span data-stu-id="137f1-140">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="137f1-141">`Â`（而不是 ` `（不间断空格））</span><span class="sxs-lookup"><span data-stu-id="137f1-141">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="137f1-142">`Ã&copy;`（而不是 `é`）</span><span class="sxs-lookup"><span data-stu-id="137f1-142">`Ã&copy;` instead of `é`</span></span>
<!-- markdownlint-enable MD038 -->

<span data-ttu-id="137f1-143">此便捷[参考](https://www.i18nqa.com/debug/utf8-debug.html)列出了指示 UTF-8/Windows-1252 编码问题的常见模式。</span><span class="sxs-lookup"><span data-stu-id="137f1-143">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vs-code-interacts-with-encodings"></a><span data-ttu-id="137f1-144">VS Code 中的 PowerShell 扩展与编码的交互方式</span><span class="sxs-lookup"><span data-stu-id="137f1-144">How the PowerShell extension in VS Code interacts with encodings</span></span>

<span data-ttu-id="137f1-145">PowerShell 扩展通过多种方式与脚本进行交互：</span><span class="sxs-lookup"><span data-stu-id="137f1-145">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="137f1-146">在 VS Code 中编辑脚本时，内容由 VS Code 发送到扩展。</span><span class="sxs-lookup"><span data-stu-id="137f1-146">When scripts are edited in VS Code, the contents are sent by VS Code to the extension.</span></span> <span data-ttu-id="137f1-147">[语言服务器协议][]要求此内容采用 UTF-8 进行传输。</span><span class="sxs-lookup"><span data-stu-id="137f1-147">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="137f1-148">因此，扩展不可能获取错误的编码。</span><span class="sxs-lookup"><span data-stu-id="137f1-148">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
1. <span data-ttu-id="137f1-149">当脚本直接在集成控制台中执行时，它们直接由 PowerShell 从文件读取。</span><span class="sxs-lookup"><span data-stu-id="137f1-149">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="137f1-150">如果 PowerShell 的编码与 VS Code 的编码不同，则可能会出错。</span><span class="sxs-lookup"><span data-stu-id="137f1-150">If PowerShell's encoding differs from VS Code's, something can go wrong here.</span></span>
1. <span data-ttu-id="137f1-151">当在 VS Code 中打开的一个脚本引用未在 VS Code 中打开的另一个脚本时，扩展会回退到从文件系统加载该脚本的内容。</span><span class="sxs-lookup"><span data-stu-id="137f1-151">When a script that is open in VS Code references another script that is not open in VS Code, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="137f1-152">PowerShell 扩展默认为 UTF-8 编码，但使用[字节顺序标记][]（或 BOM）检测来选择正确编码。</span><span class="sxs-lookup"><span data-stu-id="137f1-152">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="137f1-153">当采用无 BOM 式格式的编码（如没有 BOM 的 [UTF-8][] 和 [Windows-1252][]）时，会出现问题。</span><span class="sxs-lookup"><span data-stu-id="137f1-153">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span> <span data-ttu-id="137f1-154">PowerShell 扩展默认为 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="137f1-154">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="137f1-155">扩展无法更改 VS Code 的编码设置。</span><span class="sxs-lookup"><span data-stu-id="137f1-155">The extension cannot change VS Code's encoding settings.</span></span> <span data-ttu-id="137f1-156">有关详细信息，请参阅[问题 #824](https://github.com/Microsoft/VSCode/issues/824)。</span><span class="sxs-lookup"><span data-stu-id="137f1-156">For more information, see [issue #824](https://github.com/Microsoft/VSCode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="137f1-157">选择正确编码</span><span class="sxs-lookup"><span data-stu-id="137f1-157">Choosing the right encoding</span></span>

<span data-ttu-id="137f1-158">不同的系统和应用程序可以使用不同的编码：</span><span class="sxs-lookup"><span data-stu-id="137f1-158">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="137f1-159">在 .NET Standard 中、Web 上以及 Linux 领域中，UTF-8 现在是主流编码。</span><span class="sxs-lookup"><span data-stu-id="137f1-159">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="137f1-160">许多 .NET Framework 应用程序使用 [UTF-16][]。</span><span class="sxs-lookup"><span data-stu-id="137f1-160">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="137f1-161">由于历史原因，这有时称为“Unicode”，该术语现在是指包括 UTF-8 和 UTF-16 在内的广泛[标准](https://en.wikipedia.org/wiki/Unicode)。</span><span class="sxs-lookup"><span data-stu-id="137f1-161">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="137f1-162">在 Windows 中上，早于 Unicode 出现的许多本机应用程序在默认情况下继续使用 Windows-1252。</span><span class="sxs-lookup"><span data-stu-id="137f1-162">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="137f1-163">Unicode 编码也具有字节顺序标记 (BOM) 的概念。</span><span class="sxs-lookup"><span data-stu-id="137f1-163">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="137f1-164">BOM 在文本开头出现，用于向解码器告知文本所使用的编码。</span><span class="sxs-lookup"><span data-stu-id="137f1-164">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="137f1-165">对于多字节编码，BOM 还指示编码的[字节顺序](https://en.wikipedia.org/wiki/Endianness)。</span><span class="sxs-lookup"><span data-stu-id="137f1-165">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="137f1-166">BOM 设计为很少出现在非 Unicode 文本中的字节，从而当 BOM 存在时可以合理地猜测文本是 Unicode。</span><span class="sxs-lookup"><span data-stu-id="137f1-166">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="137f1-167">BOM 是可选的，其采用在 Linux 领域中并不普遍，因为到处都在使用可靠的 UTF-8 约定。</span><span class="sxs-lookup"><span data-stu-id="137f1-167">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="137f1-168">大多数 Linux 应用程序假设文本输入采用 UTF-8 进行编码。</span><span class="sxs-lookup"><span data-stu-id="137f1-168">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="137f1-169">虽然许多 Linux 应用程序可识别并正确处理 BOM，不过有一些应用程序无法这样做，从而导致使用这些应用程序操作的文本中出现异常。</span><span class="sxs-lookup"><span data-stu-id="137f1-169">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="137f1-170">**因此** ：</span><span class="sxs-lookup"><span data-stu-id="137f1-170">**Therefore** :</span></span>

- <span data-ttu-id="137f1-171">如果主要使用 Windows 应用程序和 Windows PowerShell，则应优先使用诸如具有 BOM 的 UTF-8 或 UTF-16 这类编码。</span><span class="sxs-lookup"><span data-stu-id="137f1-171">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="137f1-172">如果跨平台工作，则应优先使用具有 BOM 的 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="137f1-172">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="137f1-173">如果主要在与 Linux 关联的环境中工作，则应优先使用不具有 BOM 的 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="137f1-173">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="137f1-174">Windows-1252 和拉丁语-1 本质上是旧编码，应尽可能避免使用。</span><span class="sxs-lookup"><span data-stu-id="137f1-174">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="137f1-175">但是，某些较旧的 Windows 应用程序可能依赖于它们。</span><span class="sxs-lookup"><span data-stu-id="137f1-175">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="137f1-176">另外值得注意的是，脚本签名[依赖于编码](https://github.com/PowerShell/PowerShell/issues/3466)，这意味着签名脚本中的编码更改需要重新签名。</span><span class="sxs-lookup"><span data-stu-id="137f1-176">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vs-code"></a><span data-ttu-id="137f1-177">配置 VS Code</span><span class="sxs-lookup"><span data-stu-id="137f1-177">Configuring VS Code</span></span>

<span data-ttu-id="137f1-178">VS Code 的默认编码是不具有 BOM 的 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="137f1-178">VS Code's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="137f1-179">若要设置 [VS Code 的编码][]，请转到 VS Code 设置 (<kbd>Ctrl</kbd>+<kbd>,</kbd>) 并设置 `"files.encoding"` 设置：</span><span class="sxs-lookup"><span data-stu-id="137f1-179">To set [VS Code's encoding][], go to the VS Code settings (<kbd>Ctrl</kbd>+<kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="137f1-180">一些可能值有：</span><span class="sxs-lookup"><span data-stu-id="137f1-180">Some possible values are:</span></span>

- <span data-ttu-id="137f1-181">`utf8`：不具有 BOM 的 [UTF-8]</span><span class="sxs-lookup"><span data-stu-id="137f1-181">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="137f1-182">`utf8bom`：具有 BOM 的 [UTF-8]</span><span class="sxs-lookup"><span data-stu-id="137f1-182">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="137f1-183">`utf16le`：Little endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="137f1-183">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="137f1-184">`utf16be`：Big endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="137f1-184">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="137f1-185">`windows1252`：[Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="137f1-185">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="137f1-186">应在 GUI 视图中看到适用于此内容的下拉列表，或是在 JSON 视图中看到其完成。</span><span class="sxs-lookup"><span data-stu-id="137f1-186">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="137f1-187">还可以添加以下内容以尽可能自动检测编码：</span><span class="sxs-lookup"><span data-stu-id="137f1-187">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="137f1-188">如果不希望这些设置影响所有文件类型，则 VS Code 还允许按语言进行配置。</span><span class="sxs-lookup"><span data-stu-id="137f1-188">If you don't want these settings to affect all files types, VS Code also allows per-language configurations.</span></span> <span data-ttu-id="137f1-189">创建在 `[<language-name>]` 字段中放置设置，可以配置特定于语言的设置。</span><span class="sxs-lookup"><span data-stu-id="137f1-189">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="137f1-190">例如：</span><span class="sxs-lookup"><span data-stu-id="137f1-190">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="137f1-191">你可能还要考虑为 Visual Studio Code 安装 [Gremlins 跟踪器][]。</span><span class="sxs-lookup"><span data-stu-id="137f1-191">You may also want to consider installing the [Gremlins tracker][] for Visual Studio Code.</span></span> <span data-ttu-id="137f1-192">此扩展显示某些很容易损坏的 Unicode 字符，因为它们不可见或看起来像其他普通字符。</span><span class="sxs-lookup"><span data-stu-id="137f1-192">This extension reveals certain Unicode characters that easily corrupted because they are invisible or look like other normal characters.</span></span>

## <a name="configuring-powershell"></a><span data-ttu-id="137f1-193">配置 PowerShell</span><span class="sxs-lookup"><span data-stu-id="137f1-193">Configuring PowerShell</span></span>

<span data-ttu-id="137f1-194">PowerShell 的默认编码因版本而异：</span><span class="sxs-lookup"><span data-stu-id="137f1-194">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="137f1-195">在 PowerShell 6+ 中，默认编码在所有平台上都是不具有 BOM 的 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="137f1-195">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="137f1-196">在 Windows PowerShell 中，默认编码通常是 Windows-1252，这是[latin-1][] 的扩展，也称为 ISO 8859-1。</span><span class="sxs-lookup"><span data-stu-id="137f1-196">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="137f1-197">在 PowerShell 5+ 中，可以使用以下方法查找默认编码：</span><span class="sxs-lookup"><span data-stu-id="137f1-197">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="137f1-198">以下[脚本](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e)用于确定 PowerShell 会话对不具有 BOM 的脚本推断出何种编码。</span><span class="sxs-lookup"><span data-stu-id="137f1-198">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

```powershell
$badBytes = [byte[]]@(0xC3, 0x80)
$utf8Str = [System.Text.Encoding]::UTF8.GetString($badBytes)
$bytes = [System.Text.Encoding]::ASCII.GetBytes('Write-Output "') + [byte[]]@(0xC3, 0x80) + [byte[]]@(0x22)
$path = Join-Path ([System.IO.Path]::GetTempPath()) 'encodingtest.ps1'

try
{
    [System.IO.File]::WriteAllBytes($path, $bytes)

    switch (& $path)
    {
        $utf8Str
        {
            return 'UTF-8'
            break
        }

        default
        {
            return 'Windows-1252'
            break
        }
    }
}
finally
{
    Remove-Item $path
}
```

<span data-ttu-id="137f1-199">可以更普遍地使用配置文件设置将 PowerShell 配置为使用给定编码。</span><span class="sxs-lookup"><span data-stu-id="137f1-199">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span>
<span data-ttu-id="137f1-200">请参阅以下文章：</span><span class="sxs-lookup"><span data-stu-id="137f1-200">See the following articles:</span></span>

- <span data-ttu-id="137f1-201">[@mklement0][有关 StackOverflow 上的 PowerShell 编码的解答](https://stackoverflow.com/a/40098904)。</span><span class="sxs-lookup"><span data-stu-id="137f1-201">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="137f1-202">[@rkeithhill][有关在 PowerShell 中处理无 BOM 式 UTF-8 输入的博客文章](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/)。</span><span class="sxs-lookup"><span data-stu-id="137f1-202">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="137f1-203">无法强制 PowerShell 使用特定输入编码。</span><span class="sxs-lookup"><span data-stu-id="137f1-203">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="137f1-204">如果未提供 BOM，则在 Windows（区域设置为 en-US）上运行的 PowerShell 5.1 及更低版本默认使用 Windows-1252 编码。</span><span class="sxs-lookup"><span data-stu-id="137f1-204">PowerShell 5.1 and below, running on Windows with the locale set to en-US, defaults to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="137f1-205">其他区域设置可能使用不同的编码。</span><span class="sxs-lookup"><span data-stu-id="137f1-205">Other locale settings may use a different encoding.</span></span> <span data-ttu-id="137f1-206">为了确保互操作性，最好使用具有 BOM 的 Unicode 格式保存脚本。</span><span class="sxs-lookup"><span data-stu-id="137f1-206">To ensure interoperability, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="137f1-207">涉及 PowerShell 脚本的任何其他工具都可能会受到编码选择的影响，或是将脚本重新编码为另一种编码。</span><span class="sxs-lookup"><span data-stu-id="137f1-207">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="137f1-208">现有脚本</span><span class="sxs-lookup"><span data-stu-id="137f1-208">Existing scripts</span></span>

<span data-ttu-id="137f1-209">文件系统上已有的脚本可能需要重新编码为新的所选编码。</span><span class="sxs-lookup"><span data-stu-id="137f1-209">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="137f1-210">在 VS Code 底部栏中，会看到 UTF-8 标签。</span><span class="sxs-lookup"><span data-stu-id="137f1-210">In the bottom bar of VS Code, you'll see the label UTF-8.</span></span> <span data-ttu-id="137f1-211">单击它可打开操作栏并选择“保存时使用编码”  。</span><span class="sxs-lookup"><span data-stu-id="137f1-211">Click it to open the action bar and select **Save with encoding**.</span></span> <span data-ttu-id="137f1-212">现在可以为该文件选取新编码。</span><span class="sxs-lookup"><span data-stu-id="137f1-212">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="137f1-213">有关完整说明，请参阅 [VS Code 的编码][]。</span><span class="sxs-lookup"><span data-stu-id="137f1-213">See [VS Code's encoding][] for full instructions.</span></span>

<span data-ttu-id="137f1-214">如果需要重新编码多个文件，则可以使用以下脚本：</span><span class="sxs-lookup"><span data-stu-id="137f1-214">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="137f1-215">PowerShell 集成脚本环境 (ISE)</span><span class="sxs-lookup"><span data-stu-id="137f1-215">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="137f1-216">如果还使用 PowerShell ISE 编辑脚本，则需要在其中同步编码设置。</span><span class="sxs-lookup"><span data-stu-id="137f1-216">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="137f1-217">ISE 应遵循 BOM，但也可以使用反射来[设置编码](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/)。</span><span class="sxs-lookup"><span data-stu-id="137f1-217">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="137f1-218">请注意，这不会在启动之间保持。</span><span class="sxs-lookup"><span data-stu-id="137f1-218">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="137f1-219">源代码管理软件</span><span class="sxs-lookup"><span data-stu-id="137f1-219">Source control software</span></span>

<span data-ttu-id="137f1-220">一些源代码管理工具（如 git）会忽略编码；git 只跟踪字节。</span><span class="sxs-lookup"><span data-stu-id="137f1-220">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span> <span data-ttu-id="137f1-221">其他工具（如 Azure DevOps 或 Mercurial）可能不会忽略编码。</span><span class="sxs-lookup"><span data-stu-id="137f1-221">Others, like Azure DevOps or Mercurial, may not.</span></span> <span data-ttu-id="137f1-222">甚至一些基于 git 的工具也依赖于文本解码。</span><span class="sxs-lookup"><span data-stu-id="137f1-222">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="137f1-223">在这种情况下，请确保：</span><span class="sxs-lookup"><span data-stu-id="137f1-223">When this is the case, make sure you:</span></span>

- <span data-ttu-id="137f1-224">在源代码管理中配置文本编码以匹配 VS Code 配置。</span><span class="sxs-lookup"><span data-stu-id="137f1-224">Configure the text encoding in your source control to match your VS Code configuration.</span></span>
- <span data-ttu-id="137f1-225">确保所有文件都采用相关编码签入到源代码管理中。</span><span class="sxs-lookup"><span data-stu-id="137f1-225">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="137f1-226">应注意通过源代码管理收到的编码更改。</span><span class="sxs-lookup"><span data-stu-id="137f1-226">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="137f1-227">这种情况的一个重要迹象是有差异指示更改，但似乎没有任何内容发生更改（因为字节更改，但字符未更改）。</span><span class="sxs-lookup"><span data-stu-id="137f1-227">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="137f1-228">协作者环境</span><span class="sxs-lookup"><span data-stu-id="137f1-228">Collaborators' environments</span></span>

<span data-ttu-id="137f1-229">在配置源代码管理的基础上，确保你所共享的任何文件上的协作者没有通过重新编码 PowerShell 文件来替代你的编码的设置。</span><span class="sxs-lookup"><span data-stu-id="137f1-229">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="137f1-230">其他程序</span><span class="sxs-lookup"><span data-stu-id="137f1-230">Other programs</span></span>

<span data-ttu-id="137f1-231">读取或写入 PowerShell 脚本的其他任何程序都可能会对它重新编码。</span><span class="sxs-lookup"><span data-stu-id="137f1-231">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="137f1-232">一些示例如下：</span><span class="sxs-lookup"><span data-stu-id="137f1-232">Some examples are:</span></span>

- <span data-ttu-id="137f1-233">使用剪贴板复制和粘贴脚本。</span><span class="sxs-lookup"><span data-stu-id="137f1-233">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="137f1-234">这是以下这类情形中十分常见：</span><span class="sxs-lookup"><span data-stu-id="137f1-234">This is common in scenarios like:</span></span>
  - <span data-ttu-id="137f1-235">将脚本复制到 VM 中</span><span class="sxs-lookup"><span data-stu-id="137f1-235">Copying a script into a VM</span></span>
  - <span data-ttu-id="137f1-236">从电子邮件或网页中复制脚本</span><span class="sxs-lookup"><span data-stu-id="137f1-236">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="137f1-237">将脚本复制到 Microsoft Word 或 PowerPoint 文档中，或从这类文档中复制脚本</span><span class="sxs-lookup"><span data-stu-id="137f1-237">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="137f1-238">其他文本编辑器，如：</span><span class="sxs-lookup"><span data-stu-id="137f1-238">Other text editors, such as:</span></span>
  - <span data-ttu-id="137f1-239">记事本</span><span class="sxs-lookup"><span data-stu-id="137f1-239">Notepad</span></span>
  - <span data-ttu-id="137f1-240">vim</span><span class="sxs-lookup"><span data-stu-id="137f1-240">vim</span></span>
  - <span data-ttu-id="137f1-241">任何其他 PowerShell 脚本编辑器</span><span class="sxs-lookup"><span data-stu-id="137f1-241">Any other PowerShell script editor</span></span>
- <span data-ttu-id="137f1-242">文本编辑实用工具，如：</span><span class="sxs-lookup"><span data-stu-id="137f1-242">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="137f1-243">PowerShell 重定向运算符，如 `>` 和 `>>`</span><span class="sxs-lookup"><span data-stu-id="137f1-243">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="137f1-244">文件传输程序，如：</span><span class="sxs-lookup"><span data-stu-id="137f1-244">File transfer programs, like:</span></span>
  - <span data-ttu-id="137f1-245">Web 浏览器（下载脚本时）</span><span class="sxs-lookup"><span data-stu-id="137f1-245">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="137f1-246">文件共享</span><span class="sxs-lookup"><span data-stu-id="137f1-246">A file share</span></span>

<span data-ttu-id="137f1-247">其中一些工具以字节（而不是文本）进行处理，而其他工具提供编码配置。</span><span class="sxs-lookup"><span data-stu-id="137f1-247">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="137f1-248">在需要配置编码的情况下，需要使它与编辑器编码相同，以防止出现问题。</span><span class="sxs-lookup"><span data-stu-id="137f1-248">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="137f1-249">有关 PowerShell 中的编码的其他资源</span><span class="sxs-lookup"><span data-stu-id="137f1-249">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="137f1-250">有其他几篇有关在 PowerShell 中编码和配置编码的很好的文章值得一读：</span><span class="sxs-lookup"><span data-stu-id="137f1-250">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- [<span data-ttu-id="137f1-251">about_Character_Encoding</span><span class="sxs-lookup"><span data-stu-id="137f1-251">about_Character_Encoding</span></span>](/powershell/module/microsoft.powershell.core/about/about_character_encoding)
- <span data-ttu-id="137f1-252">[@mklement0] 的 [StackOverflow 上的 PowerShell 编码摘要](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span><span class="sxs-lookup"><span data-stu-id="137f1-252">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="137f1-253">以前在 VS Code-PowerShell 上创建的针对编码问题的问题：</span><span class="sxs-lookup"><span data-stu-id="137f1-253">Previous issues opened on VS Code-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="137f1-254">#1308</span><span class="sxs-lookup"><span data-stu-id="137f1-254">#1308</span></span>](https://github.com/PowerShell/VSCode-powershell/issues/1308)
  - [<span data-ttu-id="137f1-255">#1628</span><span class="sxs-lookup"><span data-stu-id="137f1-255">#1628</span></span>](https://github.com/PowerShell/VSCode-powershell/issues/1628)
  - [<span data-ttu-id="137f1-256">#1680</span><span class="sxs-lookup"><span data-stu-id="137f1-256">#1680</span></span>](https://github.com/PowerShell/VSCode-powershell/issues/1680)
  - [<span data-ttu-id="137f1-257">#1744</span><span class="sxs-lookup"><span data-stu-id="137f1-257">#1744</span></span>](https://github.com/PowerShell/VSCode-powershell/issues/1744)
  - [<span data-ttu-id="137f1-258">#1751</span><span class="sxs-lookup"><span data-stu-id="137f1-258">#1751</span></span>](https://github.com/PowerShell/VSCode-powershell/issues/1751)
- [<span data-ttu-id="137f1-259">经典的“Joel 说软件”  探讨 Unicode</span><span class="sxs-lookup"><span data-stu-id="137f1-259">The classic _Joel on Software_ write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="137f1-260">.NET Standard 中的编码</span><span class="sxs-lookup"><span data-stu-id="137f1-260">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)

[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[字节顺序标记]: https://wikipedia.org/wiki/Byte_order_mark
[byte-order mark]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[语言服务器协议]: https://microsoft.github.io/language-server-protocol/
[Language Server Protocol]: https://microsoft.github.io/language-server-protocol/
[VS Code 的编码]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[VS Code's encoding]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[Gremlins 跟踪器]: https://marketplace.visualstudio.com/items?itemName=nhoizey.gremlins
[Gremlins tracker]: https://marketplace.visualstudio.com/items?itemName=nhoizey.gremlins
