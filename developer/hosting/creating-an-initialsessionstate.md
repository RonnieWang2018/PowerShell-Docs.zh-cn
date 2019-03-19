---
title: 创建 InitialSessionState |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ae707db-52e0-408c-87fa-b35c42eaaab1
caps.latest.revision: 5
ms.openlocfilehash: 3a7c47487b632d00643fce0aa082e0dc9a9bb626
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057988"
---
# <a name="creating-an-initialsessionstate"></a><span data-ttu-id="4a888-102">创建 InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="4a888-102">Creating an InitialSessionState</span></span>

<span data-ttu-id="4a888-103">Windows PowerShell 命令在运行空间中运行。</span><span class="sxs-lookup"><span data-stu-id="4a888-103">Windows PowerShell commands run in a runspace.</span></span> <span data-ttu-id="4a888-104">若要在应用程序中托管 Windows PowerShell，必须创建[System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace)对象。</span><span class="sxs-lookup"><span data-stu-id="4a888-104">To host Windows PowerShell in your application, you must create a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span> <span data-ttu-id="4a888-105">每个运行空间具有[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象与之关联。</span><span class="sxs-lookup"><span data-stu-id="4a888-105">Every runspace has an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object associated with it.</span></span> <span data-ttu-id="4a888-106">[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)指定的运行空间，如哪些命令、 变量和模块是可用于该运行空间的特征。</span><span class="sxs-lookup"><span data-stu-id="4a888-106">The [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) specifies characteristics of the runspace, such as which commands, variables, and modules are available for that runspace.</span></span>

## <a name="create-a-default-initialsessionstate"></a><span data-ttu-id="4a888-107">创建默认的 InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="4a888-107">Create a default InitialSessionState</span></span>

 <span data-ttu-id="4a888-108">[System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)并[System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2)可以使用方法若要创建[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象。</span><span class="sxs-lookup"><span data-stu-id="4a888-108">The [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)and [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methods can be used to create [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objects.</span></span> <span data-ttu-id="4a888-109">[System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)使用所有的内置命令加载，同时创建 InitialSessionState [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2)加载所需主机 Windows PowerShell （从 Microsoft.PowerShell.Core 模块命令命令。</span><span class="sxs-lookup"><span data-stu-id="4a888-109">[System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) creates an InitialSessionState with all of the built-in commands loaded, while [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) loads only the commands required to host Windows PowerShell (the commands from the Microsoft.PowerShell.Core module.</span></span>

 <span data-ttu-id="4a888-110">如果你想要进一步限制在主机应用程序中可用的命令需要创建受限运行空间。</span><span class="sxs-lookup"><span data-stu-id="4a888-110">If you want to further limit the commands available in your host application you need to create a constrained runspace.</span></span> <span data-ttu-id="4a888-111">有关信息，请参阅创建受限运行空间。</span><span class="sxs-lookup"><span data-stu-id="4a888-111">For information, see Creating a constrained runspace.</span></span>

 <span data-ttu-id="4a888-112">下面的代码演示如何创建 InitialSessionState、 将其分配给一个运行空间中，将命令添加到该运行空间中的管道和调用命令。</span><span class="sxs-lookup"><span data-stu-id="4a888-112">The following code shows how to create an InitialSessionState, assign it to a runspace, add commands to the pipeline in that runspace, and invoke the commands.</span></span> <span data-ttu-id="4a888-113">有关添加和调用命令的详细信息，请参阅添加和调用命令。</span><span class="sxs-lookup"><span data-stu-id="4a888-113">For more information about adding and invoking commands, see Adding and invoking commands.</span></span>

```csharp

namespace SampleHost
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;

  class HostP4b
  {
    static void Main(string[] args)
    {
      // Call the InitialSessionState.CreateDefault method to create
      // an empty InitialSessionState object, and then add the
      // elements that will be available when the runspace is opened.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      SessionStateVariableEntry var1 = new
          SessionStateVariableEntry("test1",
                                    "MyVar1",
                                    "Initial session state MyVar1 test");
      iss.Variables.Add(var1);

      SessionStateVariableEntry var2 = new
          SessionStateVariableEntry("test2",
                                    "MyVar2",
                                    "Initial session state MyVar2 test");
      iss.Variables.Add(var2);

      // Call the RunspaceFactory.CreateRunspace(InitialSessionState)
      // method to create the runspace where the pipeline is run.
      Runspace rs = RunspaceFactory.CreateRunspace(iss);
      rs.Open();

      // Call the PowerShell.Create() method to create the PowerShell
      // object,and then specify the runspace and commands to the pipeline.
      // and  create the command pipeline.
      PowerShell ps = PowerShell.Create();
      ps.Runspace = rs;
      ps.AddCommand("Get-Variable");
      ps.AddArgument("test*");

      Console.WriteLine("Variable             Value");
      Console.WriteLine("--------------------------");

      // Call the PowerShell.Invoke() method to run
      // the pipeline synchronously.
        foreach (PSObject result in ps.Invoke())
        {
          Console.WriteLine("{0,-20}{1}",
                  result.Members["Name"].Value,
                  result.Members["Value"].Value);
        } // End foreach.

        // Close the runspace to free resources.
        rs.Close();

    } // End Main.
  } // End SampleHost.
}
```

## <a name="see-also"></a><span data-ttu-id="4a888-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4a888-114">See Also</span></span>

 [<span data-ttu-id="4a888-115">创建受限运行空间</span><span class="sxs-lookup"><span data-stu-id="4a888-115">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)