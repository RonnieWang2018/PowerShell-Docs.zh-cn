---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 将凭据与 DSC 资源结合使用
description: DSC 允许你向配置提供凭据，以便可以在特定用户帐户（而不是本地系统帐户）的上下文中应用配置设置。
ms.openlocfilehash: e4ca39e099afacd7cb06c4d9ef889f94deb73cee
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645087"
---
# <a name="use-credentials-with-dsc-resources"></a><span data-ttu-id="40f47-104">将凭据与 DSC 资源结合使用</span><span class="sxs-lookup"><span data-stu-id="40f47-104">Use Credentials with DSC Resources</span></span>

> <span data-ttu-id="40f47-105">适用于：Windows PowerShell 5.0 和 Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="40f47-105">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="40f47-106">可以通过在配置中使用 **PsDscRunAsCredential** 属性，在指定的一组凭据之下运行 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="40f47-106">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span> <span data-ttu-id="40f47-107">默认情况下，DSC 以系统帐户身份运行每个资源。</span><span class="sxs-lookup"><span data-stu-id="40f47-107">By default, DSC runs each resource as the system account.</span></span> <span data-ttu-id="40f47-108">有时需要以用户身份运行，例如在特定用户上下文中安装 MSI 程序包、设置用户的注册表项、访问用户的特定本地目录或访问网络共享。</span><span class="sxs-lookup"><span data-stu-id="40f47-108">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span> <span data-ttu-id="40f47-109">对于您指定到 **PSDSCRunAsCredential** 的任何帐户，目标计算机都需要 **SeInteractiveLogonRight** 。</span><span class="sxs-lookup"><span data-stu-id="40f47-109">The **SeInteractiveLogonRight** is required, by the target machine, for any account you specify to **PSDSCRunAsCredential**.</span></span> <span data-ttu-id="40f47-110">有关详细信息，请参阅[帐户权限常量](/windows/desktop/secauthz/account-rights-constants)。</span><span class="sxs-lookup"><span data-stu-id="40f47-110">For more information, see [Account Rights Constants](/windows/desktop/secauthz/account-rights-constants).</span></span>

<span data-ttu-id="40f47-111">每个 DSC 资源都具有 **PsDscRunAsCredential** 属性，它可以设置为任何用户凭据（ [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象）。</span><span class="sxs-lookup"><span data-stu-id="40f47-111">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](/dotnet/api/system.management.automation.pscredential) object).</span></span> <span data-ttu-id="40f47-112">凭据可以硬编码为配置中属性的值，你也可以将值设置为 [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential)，这会在编译配置时提示用户输入凭据（有关编译配置的信息，请参阅[配置](configurations.md)）。</span><span class="sxs-lookup"><span data-stu-id="40f47-112">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="40f47-113">在 PowerShell 5.0 中，不支持在调用复合资源的配置中使用 PsDscRunAsCredential 属性。</span><span class="sxs-lookup"><span data-stu-id="40f47-113">In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span> <span data-ttu-id="40f47-114">在 PowerShell 5.1 中，支持在调用复合资源的配置中使用 **PsDscRunAsCredential** 属性。</span><span class="sxs-lookup"><span data-stu-id="40f47-114">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span> <span data-ttu-id="40f47-115">PsDscRunAsCredential 属性在 PowerShell 4.0 中不可用。</span><span class="sxs-lookup"><span data-stu-id="40f47-115">The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="40f47-116">在下面的示例中，`Get-Credential` 用于提示用户输入凭据。</span><span class="sxs-lookup"><span data-stu-id="40f47-116">In the following example, `Get-Credential` is used to prompt the user for credentials.</span></span> <span data-ttu-id="40f47-117">**Registry** 资源用于更改可指定 Windows 命令提示符窗口背景色的注册表项。</span><span class="sxs-lookup"><span data-stu-id="40f47-117">The **Registry** resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

```powershell
Configuration ChangeCmdBackGroundColor
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        Registry CmdPath
        {
            Key                  = 'HKEY_CURRENT_USER\SOFTWARE\Microsoft\Command Processor'
            ValueName            = 'DefaultColor'
            ValueData            = '1F'
            ValueType            = 'DWORD'
            Ensure               = 'Present'
            Force                = $true
            Hex                  = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost';
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

ChangeCmdBackGroundColor -ConfigurationData $configData
```

> [!NOTE]
> <span data-ttu-id="40f47-118">此示例假定你在 `C:\publicKeys\targetNode.cer` 上具有有效证书，并且该证书的指纹是显示的值。</span><span class="sxs-lookup"><span data-stu-id="40f47-118">This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span> <span data-ttu-id="40f47-119">有关在 DSC 配置 MOF 文件中加密凭据的信息，请参阅[保护 MOF 文件](../pull-server/secureMOF.md)。</span><span class="sxs-lookup"><span data-stu-id="40f47-119">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>
