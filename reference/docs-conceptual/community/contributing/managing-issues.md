---
title: 如何管理问题
description: 本文介绍 PowerShell-Docs 团队如何管理问题。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 56f0ea5b4c5c700db8fdd0b16e3ce1c4040a43dc
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354586"
---
# <a name="how-we-manage-issues"></a><span data-ttu-id="8e066-103">如何管理问题</span><span class="sxs-lookup"><span data-stu-id="8e066-103">How we manage issues</span></span>

<span data-ttu-id="8e066-104">本文记录了如何管理 PowerShell-Docs 存储库中的问题。</span><span class="sxs-lookup"><span data-stu-id="8e066-104">This article documents how we manage issues in the PowerShell-Docs repo.</span></span> <span data-ttu-id="8e066-105">本文旨在为 PowerShell-Docs 团队成员提供帮助。</span><span class="sxs-lookup"><span data-stu-id="8e066-105">This article is designed to be a job aid for members of the PowerShell-Docs team.</span></span> <span data-ttu-id="8e066-106">在此处发布本文，以便为公共参与者提供流程透明性。</span><span class="sxs-lookup"><span data-stu-id="8e066-106">It is published here to provide process transparency for our public contributors.</span></span>

## <a name="sources-of-issues"></a><span data-ttu-id="8e066-107">问题源</span><span class="sxs-lookup"><span data-stu-id="8e066-107">Sources of issues</span></span>

- <span data-ttu-id="8e066-108">社区参与者</span><span class="sxs-lookup"><span data-stu-id="8e066-108">Community contributors</span></span>
- <span data-ttu-id="8e066-109">内部参与者</span><span class="sxs-lookup"><span data-stu-id="8e066-109">Internal contributors</span></span>
- <span data-ttu-id="8e066-110">来自社交媒体渠道的注释转录</span><span class="sxs-lookup"><span data-stu-id="8e066-110">Transcriptions of comments from social media channels</span></span>
- <span data-ttu-id="8e066-111">通过 Docs 反馈窗体提供的反馈</span><span class="sxs-lookup"><span data-stu-id="8e066-111">Feedback via the Docs feedback form</span></span>

## <a name="response-time-targets"></a><span data-ttu-id="8e066-112">响应时间目标</span><span class="sxs-lookup"><span data-stu-id="8e066-112">Response time targets</span></span>

- <span data-ttu-id="8e066-113">已会审 - 5 个工作日</span><span class="sxs-lookup"><span data-stu-id="8e066-113">Triaged - 5 business days</span></span>
- <span data-ttu-id="8e066-114">修复或更改 - 无具体目标 - 仅尽最大努力</span><span class="sxs-lookup"><span data-stu-id="8e066-114">Fix or change - no specific target - best effort only</span></span>

### <a name="labeling--milestones"></a><span data-ttu-id="8e066-115">标记和里程碑</span><span class="sxs-lookup"><span data-stu-id="8e066-115">Labeling & Milestones</span></span>

#### <a name="label-types"></a><span data-ttu-id="8e066-116">标签类型</span><span class="sxs-lookup"><span data-stu-id="8e066-116">Label Types</span></span>

|<span data-ttu-id="8e066-117">前缀</span><span class="sxs-lookup"><span data-stu-id="8e066-117">Prefix</span></span>  | <span data-ttu-id="8e066-118">说明</span><span class="sxs-lookup"><span data-stu-id="8e066-118">Description</span></span>                                                         |
|------- | --------------------------------------------------------------------|
|<span data-ttu-id="8e066-119">区域</span><span class="sxs-lookup"><span data-stu-id="8e066-119">Area</span></span>    | <span data-ttu-id="8e066-120">用于指示问题正在讨论哪个部分的 PowerShell 或文档。</span><span class="sxs-lookup"><span data-stu-id="8e066-120">Used to indicate what part of PowerShell or the docs that the issue is discussing.</span></span><br><span data-ttu-id="8e066-121">有助于功能所有者查找其功能的问题。</span><span class="sxs-lookup"><span data-stu-id="8e066-121">Useful for feature owners to find issues for their feature.</span></span>|
|<span data-ttu-id="8e066-122">Pri</span><span class="sxs-lookup"><span data-stu-id="8e066-122">Pri</span></span>     | <span data-ttu-id="8e066-123">用于指示问题的优先级。</span><span class="sxs-lookup"><span data-stu-id="8e066-123">Used to indicate the priority of the issue.</span></span> <span data-ttu-id="8e066-124">值范围是 0-4。</span><span class="sxs-lookup"><span data-stu-id="8e066-124">Value range 0-4.</span></span>        |
|<span data-ttu-id="8e066-125">问题</span><span class="sxs-lookup"><span data-stu-id="8e066-125">Issue</span></span>   | <span data-ttu-id="8e066-126">用于对问题的反馈类型进行分类</span><span class="sxs-lookup"><span data-stu-id="8e066-126">Used to classify the type of feedback for issue</span></span>                     |
|<span data-ttu-id="8e066-127">审阅</span><span class="sxs-lookup"><span data-stu-id="8e066-127">Review</span></span>  | <span data-ttu-id="8e066-128">用于需要团队进一步评审的问题</span><span class="sxs-lookup"><span data-stu-id="8e066-128">Used for issue that require further review by the team</span></span>              |
|<span data-ttu-id="8e066-129">状态</span><span class="sxs-lookup"><span data-stu-id="8e066-129">Status</span></span>  | <span data-ttu-id="8e066-130">用于指示工作项的状态</span><span class="sxs-lookup"><span data-stu-id="8e066-130">Used to indicate the status of the work item</span></span>                        |
|<span data-ttu-id="8e066-131">等待</span><span class="sxs-lookup"><span data-stu-id="8e066-131">Waiting</span></span> | <span data-ttu-id="8e066-132">用于指示我们正在等待</span><span class="sxs-lookup"><span data-stu-id="8e066-132">Used to indicate that we are waiting on something</span></span>                   |

#### <a name="milestones"></a><span data-ttu-id="8e066-133">里程碑</span><span class="sxs-lookup"><span data-stu-id="8e066-133">Milestones</span></span>

<span data-ttu-id="8e066-134">应使用相应的里程碑标记的问题和 PR。</span><span class="sxs-lookup"><span data-stu-id="8e066-134">Issues and PRs should be tagged with the appropriate milestone.</span></span> <span data-ttu-id="8e066-135">如果问题并未针对特定版本，则不使用里程碑。</span><span class="sxs-lookup"><span data-stu-id="8e066-135">If the issue is not targeted for a specific version then no milestone is used.</span></span> <span data-ttu-id="8e066-136">应将尚未合并到 PowerShell 代码库中的更改的 Docs PR 的问题分配给“未来”里程碑。</span><span class="sxs-lookup"><span data-stu-id="8e066-136">Issues for Docs PRs for changes that have yet to be merged into the PowerShell code base should be assigned to the **Future** milestone.</span></span> <span data-ttu-id="8e066-137">合并代码更改后，将里程碑更改为相应的版本。</span><span class="sxs-lookup"><span data-stu-id="8e066-137">After the code change has been merged, change the milestone to the appropriate version.</span></span>

|    <span data-ttu-id="8e066-138">里程碑</span><span class="sxs-lookup"><span data-stu-id="8e066-138">Milestone</span></span>     |                    <span data-ttu-id="8e066-139">说明</span><span class="sxs-lookup"><span data-stu-id="8e066-139">Description</span></span>                     |
| ---------------- | -------------------------------------------------- |
| <span data-ttu-id="8e066-140">6.x</span><span class="sxs-lookup"><span data-stu-id="8e066-140">6.x</span></span>              | <span data-ttu-id="8e066-141">与 PowerShell 6.0 到 6.2.x 相关的工作项</span><span class="sxs-lookup"><span data-stu-id="8e066-141">Work items related to PowerShell 6.0 through 6.2.x</span></span> |
| <span data-ttu-id="8e066-142">7.0.0</span><span class="sxs-lookup"><span data-stu-id="8e066-142">7.0.0</span></span>            | <span data-ttu-id="8e066-143">与 PowerShell 7.0 相关的工作项</span><span class="sxs-lookup"><span data-stu-id="8e066-143">Work items related to PowerShell 7.0</span></span>               |
| <span data-ttu-id="8e066-144">7.1.0</span><span class="sxs-lookup"><span data-stu-id="8e066-144">7.1.0</span></span>            | <span data-ttu-id="8e066-145">与 PowerShell 7.1 相关的工作项</span><span class="sxs-lookup"><span data-stu-id="8e066-145">Work items related to PowerShell 7.1</span></span>               |
| <span data-ttu-id="8e066-146">未来</span><span class="sxs-lookup"><span data-stu-id="8e066-146">Future</span></span>           | <span data-ttu-id="8e066-147">工作项 PowerShell 的未来版本</span><span class="sxs-lookup"><span data-stu-id="8e066-147">Work items a future version of PowerShell</span></span>          |
| <span data-ttu-id="8e066-148">PSReadline-vNext</span><span class="sxs-lookup"><span data-stu-id="8e066-148">PSReadline-vNext</span></span> | <span data-ttu-id="8e066-149">工作项 PSReadline 的未来版本</span><span class="sxs-lookup"><span data-stu-id="8e066-149">Work items a future version of PSReadline</span></span>          |

## <a name="triage-process"></a><span data-ttu-id="8e066-150">会审过程</span><span class="sxs-lookup"><span data-stu-id="8e066-150">Triage process</span></span>

<span data-ttu-id="8e066-151">PowerShell Docs 团队每周都要开会讨论自上次会议以来新增的任何问题。</span><span class="sxs-lookup"><span data-stu-id="8e066-151">The PowerShell docs team meets once per week to discuss any issues added since last meeting.</span></span> <span data-ttu-id="8e066-152">如果分配了标签或分配了所有者，则会将问题视为已会审。</span><span class="sxs-lookup"><span data-stu-id="8e066-152">An issue is considered to have been triaged when labels have been assigned or an owner has been assigned.</span></span> <span data-ttu-id="8e066-153">建议 PowerShell Docs 团队成员每天审查问题，并在遇到新问题时进行会审。</span><span class="sxs-lookup"><span data-stu-id="8e066-153">PowerShell docs team members are encouraged to review the issues daily and triage new issues as they arrive.</span></span> <span data-ttu-id="8e066-154">然后，可以根据需要开展每周会审会议来更详细地讨论新问题。</span><span class="sxs-lookup"><span data-stu-id="8e066-154">The weekly triage meeting can then be used to discuss the new issues in more detail, as needed.</span></span>

### <a name="misplaced-product-feedback"></a><span data-ttu-id="8e066-155">错放的产品反馈</span><span class="sxs-lookup"><span data-stu-id="8e066-155">Misplaced product feedback</span></span>

- <span data-ttu-id="8e066-156">输入客户注释，指明它是产品反馈，并提供指向相应反馈渠道的链接。</span><span class="sxs-lookup"><span data-stu-id="8e066-156">Enter a comment for the customer indicating it is product feedback and provide a link to the appropriate feedback channel.</span></span>
- <span data-ttu-id="8e066-157">可选：将问题复制到相应的产品反馈位置，将链接添加到复制的项，并关闭问题。</span><span class="sxs-lookup"><span data-stu-id="8e066-157">Optional: Copy the issue to the appropriate product feedback location, add a link to the copied item, and close the issue.</span></span> <span data-ttu-id="8e066-158">请勿将问题复制到 UserVoice。</span><span class="sxs-lookup"><span data-stu-id="8e066-158">DO NOT copy issues to UserVoice.</span></span>

  | <span data-ttu-id="8e066-159">DocSet</span><span class="sxs-lookup"><span data-stu-id="8e066-159">DocSet</span></span>    | <span data-ttu-id="8e066-160">产品反馈 URL</span><span class="sxs-lookup"><span data-stu-id="8e066-160">Product Feedback URL</span></span>                                           |
  | --------- | -------------------------------------------------------------- |
  | <span data-ttu-id="8e066-161">开发人员</span><span class="sxs-lookup"><span data-stu-id="8e066-161">developer</span></span> | `https://github.com/PowerShell/PowerShell/issues/new/choose`   |
  | <span data-ttu-id="8e066-162">dsc</span><span class="sxs-lookup"><span data-stu-id="8e066-162">dsc</span></span>       | `https://windowsserver.uservoice.com/forums/301869-powershell` |
  | <span data-ttu-id="8e066-163">库</span><span class="sxs-lookup"><span data-stu-id="8e066-163">gallery</span></span>   | `https://github.com/powershell/powershellgallery/issues/new`   |
  | <span data-ttu-id="8e066-164">jea</span><span class="sxs-lookup"><span data-stu-id="8e066-164">jea</span></span>       | `https://github.com/powershell/jea/issues/new`                 |
  | <span data-ttu-id="8e066-165">reference</span><span class="sxs-lookup"><span data-stu-id="8e066-165">reference</span></span> | `https://github.com/PowerShell/PowerShell/issues/new/choose`   |
  | <span data-ttu-id="8e066-166">wmf</span><span class="sxs-lookup"><span data-stu-id="8e066-166">wmf</span></span>       | `https://windowsserver.uservoice.com/forums/301869-powershell` |

### <a name="support-requests"></a><span data-ttu-id="8e066-167">支持请求</span><span class="sxs-lookup"><span data-stu-id="8e066-167">Support requests</span></span>

- <span data-ttu-id="8e066-168">如果支持问题很简单，请礼貌答复并关闭问题。</span><span class="sxs-lookup"><span data-stu-id="8e066-168">If the support question is simple, answer it politely and close the issue.</span></span>
- <span data-ttu-id="8e066-169">如果问题较为复杂，或者提交者回复了更多问题，请将这些问题重定向到论坛和支持渠道。</span><span class="sxs-lookup"><span data-stu-id="8e066-169">If the question is more complicated, or the submitter replies with more questions, redirect them to forums and support channels.</span></span> <span data-ttu-id="8e066-170">用于重定向到论坛的建议文本：</span><span class="sxs-lookup"><span data-stu-id="8e066-170">Suggested text for redirecting to forums:</span></span>

  ```Markdown
  > This is not the right forum for these kinds of questions. Try posting your question in a
  > community support forum. For a list of community forums see:
  > https://docs.microsoft.com/powershell/scripting/community/community-support
  ```

### <a name="code-of-conduct-violations"></a><span data-ttu-id="8e066-171">行为准则冲突</span><span class="sxs-lookup"><span data-stu-id="8e066-171">Code of conduct violations</span></span>

- <span data-ttu-id="8e066-172">编辑问题以删除任何冒犯性内容（如有必要）。</span><span class="sxs-lookup"><span data-stu-id="8e066-172">Edit the issue to remove any offensive content, if necessary.</span></span>
- <span data-ttu-id="8e066-173">输入一条注释，指示此问题是垃圾邮件，关闭问题，然后将其锁定以防止进一步注释。</span><span class="sxs-lookup"><span data-stu-id="8e066-173">Enter a comment indicating the issue is spam, close the issue, and then lock it to prevent further comments.</span></span>
- <span data-ttu-id="8e066-174">每次出现该问题时应在每周会审中进行讨论，以确定是否需要执行进一步操作（向 GitHub 或 Microsoft 法律报告）。</span><span class="sxs-lookup"><span data-stu-id="8e066-174">Each occurrence of this should be discussed in the weekly triage to determine the need for further action (report to GitHub or Microsoft Legal).</span></span>
