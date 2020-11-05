---
ms.date: 08/11/2020
keywords: dsc,powershell,配置,安装程序
title: 直接调用 DSC 资源方法
description: Invoke-DscResource cmdlet 可用于调用 DSC 资源的函数或方法。 这可为想要使用 DSC 资源的第三方所用，也可以作为开发资源时非常有用的工具。
ms.openlocfilehash: 5ccf0f589b60cef4ec197d1e0a583af9ed60d5e7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651003"
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="53a72-105">直接调用 DSC 资源方法</span><span class="sxs-lookup"><span data-stu-id="53a72-105">Calling DSC resource methods directly</span></span>

> <span data-ttu-id="53a72-106">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="53a72-106">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="53a72-107">可以使用 [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet 直接调用 DSC 资源的函数或方法（基于 MOF 资源的 `Get-TargetResource`、`Set-TargetResource` 和 `Test-TargetResource` 函数，或基于类的资源的 Get、Set 和 Test 方法）  。</span><span class="sxs-lookup"><span data-stu-id="53a72-107">You can use the [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet to directly call the functions or methods of a DSC resource (The `Get-TargetResource`, `Set-TargetResource`, and `Test-TargetResource` functions of a MOF-based resource, or the **Get** , **Set** , and **Test** methods of a class-based resource).</span></span> <span data-ttu-id="53a72-108">这可为想要使用 DSC 资源的第三方所用，也可以作为开发资源时非常有用的工具。</span><span class="sxs-lookup"><span data-stu-id="53a72-108">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span>

> [!NOTE]
> <span data-ttu-id="53a72-109">在 PowerShell 7.0+ 中，`Invoke-DscResource` 不再支持调用 WMI DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="53a72-109">In PowerShell 7.0+, `Invoke-DscResource` no longer supports invoking WMI DSC resources.</span></span> <span data-ttu-id="53a72-110">这包括 PSDesiredStateConfiguration 中的文件和日志资源  。</span><span class="sxs-lookup"><span data-stu-id="53a72-110">This includes the **File** and **Log** resources in **PSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="53a72-111">此 cmdlet 通常与元配置属性 `refreshMode = 'Disabled'` 组合使用，但无论 **refreshMode** 设置为何值，都可以使用它。</span><span class="sxs-lookup"><span data-stu-id="53a72-111">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="53a72-112">在调用 `Invoke-DscResource` cmdlet 时，可以通过使用 Method 参数来指定要调用的方法和函数。</span><span class="sxs-lookup"><span data-stu-id="53a72-112">When calling the `Invoke-DscResource` cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="53a72-113">你可以将哈希表作为 **Property** 参数的值进行传递，从而指定资源的属性。</span><span class="sxs-lookup"><span data-stu-id="53a72-113">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="53a72-114">直接调用资源方法的示例如下：</span><span class="sxs-lookup"><span data-stu-id="53a72-114">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="53a72-115">确保文件存在</span><span class="sxs-lookup"><span data-stu-id="53a72-115">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
              DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
              Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="53a72-116">测试文件存在</span><span class="sxs-lookup"><span data-stu-id="53a72-116">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="53a72-117">获取文件内容</span><span class="sxs-lookup"><span data-stu-id="53a72-117">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

> [!NOTE]
> <span data-ttu-id="53a72-118">不支持直接调用复合资源方法。</span><span class="sxs-lookup"><span data-stu-id="53a72-118">Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="53a72-119">请改为调用构成复合资源的基础资源的方法。</span><span class="sxs-lookup"><span data-stu-id="53a72-119">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="53a72-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="53a72-120">See Also</span></span>

- [<span data-ttu-id="53a72-121">使用 MOF 编写自定义 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="53a72-121">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="53a72-122">使用 PowerShell 类编写自定义 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="53a72-122">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
- [<span data-ttu-id="53a72-123">调试 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="53a72-123">Debugging DSC resources</span></span>](../troubleshooting/debugResource.md)
