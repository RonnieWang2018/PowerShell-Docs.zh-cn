---
title: Runspace01 示例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1ac286512f3cb3b97a6b3179c9dd45f1fefe1ecf
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772189"
---
# <a name="runspace01-sample"></a>Runspace01 示例

此示例演示如何使用[system.exception 类以](/dotnet/api/system.management.automation.powershell)同步方式运行[Get Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet。 [获取进程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)cmdlet 将为在本地计算机上运行的每个进程返回[system.object](/dotnet/api/System.Diagnostics.Process) 。 然后，将从返回的对象中提取[Processname *](/dotnet/api/System.Diagnostics.Process.ProcessName)和[Handlecount *](/dotnet/api/System.Diagnostics.Process.Handlecount)属性的值，并将其显示在控制台窗口中。

## <a name="requirements"></a>要求

 此示例需要 Windows PowerShell 2.0。

## <a name="demonstrates"></a>演示

- 创建要运行命令的[system.web](/dotnet/api/system.management.automation.powershell)对象。

- 将命令添加到[system.web](/dotnet/api/system.management.automation.powershell)对象的管道。

- 同步运行命令。

- 使用 system.exception 对象从命令返回[的对象中](/dotnet/api/System.Management.Automation.PSObject)提取属性。

## <a name="example"></a>示例

 此示例在 Windows PowerShell 提供的默认运行空间中以同步方式运行[Get Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet。

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace01
  {
    /// <summary>
    /// This sample uses the PowerShell class to execute
    /// the get-process cmdlet synchronously. The name and
    /// handlecount are then extracted from the PSObjects
    /// returned and displayed.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object to run a command.
    /// 2. Adding a command to the pipeline of the PowerShell object.
    /// 3. Running the command synchronously.
    /// 4. Using PSObject objects to extract properties from the objects
    ///    returned by the command.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create().AddCommand("get-process"))
      {
        Console.WriteLine("Process              HandleCount");
        Console.WriteLine("--------------------------------");

        // Invoke the command synchronously and display the
        // ProcessName and HandleCount properties of the
        // objects that are returned.
        foreach (PSObject result in powershell.Invoke())
        {
          Console.WriteLine(
                      "{0,-20} {1}",
                      result.Members["ProcessName"].Value,
                      result.Members["HandleCount"].Value);
        }
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>另请参阅
