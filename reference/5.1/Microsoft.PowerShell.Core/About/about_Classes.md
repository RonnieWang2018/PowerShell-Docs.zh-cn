---
description: 描述如何使用类创建自己的自定义类型。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_classes?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Classes
ms.openlocfilehash: 3b4222752492d13d07aba14b2b4f157edc319353
ms.sourcegitcommit: 16d62a98449e3ddaf8d7c65bc1848ede1fd8a3e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "93199422"
---
# <a name="about-classes"></a><span data-ttu-id="d481b-104">关于类</span><span class="sxs-lookup"><span data-stu-id="d481b-104">About Classes</span></span>

## <a name="short-description"></a><span data-ttu-id="d481b-105">简短说明</span><span class="sxs-lookup"><span data-stu-id="d481b-105">Short description</span></span>
<span data-ttu-id="d481b-106">描述如何使用类创建自己的自定义类型。</span><span class="sxs-lookup"><span data-stu-id="d481b-106">Describes how you can use classes to create your own custom types.</span></span>

## <a name="long-description"></a><span data-ttu-id="d481b-107">长说明</span><span class="sxs-lookup"><span data-stu-id="d481b-107">Long description</span></span>

<span data-ttu-id="d481b-108">PowerShell 5.0 添加了一种正式的语法来定义类和其他用户定义类型。</span><span class="sxs-lookup"><span data-stu-id="d481b-108">PowerShell 5.0 adds a formal syntax to define classes and other user-defined types.</span></span> <span data-ttu-id="d481b-109">通过添加类，开发人员和 IT 专业人员可以将 PowerShell 用于更广泛的用例。</span><span class="sxs-lookup"><span data-stu-id="d481b-109">The addition of classes enables developers and IT professionals to embrace PowerShell for a wider range of use cases.</span></span> <span data-ttu-id="d481b-110">它简化了 PowerShell 项目的开发并加快了管理面的覆盖范围。</span><span class="sxs-lookup"><span data-stu-id="d481b-110">It simplifies development of PowerShell artifacts and accelerates coverage of management surfaces.</span></span>

<span data-ttu-id="d481b-111">类声明是一个蓝图，用于在运行时创建对象的实例。</span><span class="sxs-lookup"><span data-stu-id="d481b-111">A class declaration is a blueprint used to create instances of objects at run time.</span></span> <span data-ttu-id="d481b-112">在定义类时，类名称是类型的名称。</span><span class="sxs-lookup"><span data-stu-id="d481b-112">When you define a class, the class name is the name of the type.</span></span> <span data-ttu-id="d481b-113">例如，如果声明名为 **device** 的类并将变量初始化 `$dev` 为 **设备** 的新实例， `$dev` 则为 **设备** 类型的对象或实例。</span><span class="sxs-lookup"><span data-stu-id="d481b-113">For example, if you declare a class named **Device** and initialize a variable `$dev` to a new instance of **Device** , `$dev` is an object or instance of type **Device** .</span></span> <span data-ttu-id="d481b-114">**设备** 的每个实例都可以在其属性中具有不同的值。</span><span class="sxs-lookup"><span data-stu-id="d481b-114">Each instance of **Device** can have different values in its properties.</span></span>

## <a name="supported-scenarios"></a><span data-ttu-id="d481b-115">支持的方案</span><span class="sxs-lookup"><span data-stu-id="d481b-115">Supported scenarios</span></span>

- <span data-ttu-id="d481b-116">使用熟悉的面向对象的编程语义（如类、属性、方法、继承等）在 PowerShell 中定义自定义类型。</span><span class="sxs-lookup"><span data-stu-id="d481b-116">Define custom types in PowerShell using familiar object-oriented programming semantics like classes, properties, methods, inheritance, etc.</span></span>
- <span data-ttu-id="d481b-117">使用 PowerShell 语言调试类型。</span><span class="sxs-lookup"><span data-stu-id="d481b-117">Debug types using the PowerShell language.</span></span>
- <span data-ttu-id="d481b-118">使用正式的机制生成并处理异常。</span><span class="sxs-lookup"><span data-stu-id="d481b-118">Generate and handle exceptions using formal mechanisms.</span></span>
- <span data-ttu-id="d481b-119">使用 PowerShell 语言定义 DSC 资源及其关联的类型。</span><span class="sxs-lookup"><span data-stu-id="d481b-119">Define DSC resources and their associated types by using the PowerShell language.</span></span>

## <a name="syntax"></a><span data-ttu-id="d481b-120">语法</span><span class="sxs-lookup"><span data-stu-id="d481b-120">Syntax</span></span>

<span data-ttu-id="d481b-121">使用以下语法声明类：</span><span class="sxs-lookup"><span data-stu-id="d481b-121">Classes are declared using the following syntax:</span></span>

```syntax
class <class-name> [: [<base-class>][,<interface-list]] {
    [[<attribute>] [hidden] [static] <property-definition> ...]
    [<class-name>([<constructor-argument-list>])
      {<constructor-statement-list>} ...]
    [[<attribute>] [hidden] [static] <method-definition> ...]
}
```

<span data-ttu-id="d481b-122">使用以下语法之一对类进行实例化：</span><span class="sxs-lookup"><span data-stu-id="d481b-122">Classes are instantiated using either of the following syntaxes:</span></span>

```syntax
[$<variable-name> =] New-Object -TypeName <class-name> [
  [-ArgumentList] <constructor-argument-list>]
```

```syntax
[$<variable-name> =] [<class-name>]::new([<constructor-argument-list>])
```

> [!NOTE]
> <span data-ttu-id="d481b-123">使用语法时 `[<class-name>]::new()` ，类名称的两侧的方括号是必需的。</span><span class="sxs-lookup"><span data-stu-id="d481b-123">When using the `[<class-name>]::new()` syntax, brackets around the class name are mandatory.</span></span> <span data-ttu-id="d481b-124">括号指示 PowerShell 的类型定义。</span><span class="sxs-lookup"><span data-stu-id="d481b-124">The brackets signal a type definition for PowerShell.</span></span>

### <a name="example-syntax-and-usage"></a><span data-ttu-id="d481b-125">示例语法和用法</span><span class="sxs-lookup"><span data-stu-id="d481b-125">Example syntax and usage</span></span>

<span data-ttu-id="d481b-126">此示例显示创建可用类所需的最少语法。</span><span class="sxs-lookup"><span data-stu-id="d481b-126">This example shows the minimum syntax needed to create a usable class.</span></span>

```powershell
class Device {
    [string]$Brand
}

$dev = [Device]::new()
$dev.Brand = "Microsoft"
$dev
```

```Output
Brand
-----
Microsoft
```

## <a name="class-properties"></a><span data-ttu-id="d481b-127">类属性</span><span class="sxs-lookup"><span data-stu-id="d481b-127">Class properties</span></span>

<span data-ttu-id="d481b-128">属性是在类范围中声明的变量。</span><span class="sxs-lookup"><span data-stu-id="d481b-128">Properties are variables declared at class scope.</span></span> <span data-ttu-id="d481b-129">属性可以是任何内置类型，也可以是其他类的实例。</span><span class="sxs-lookup"><span data-stu-id="d481b-129">A property may be of any built-in type or an instance of another class.</span></span> <span data-ttu-id="d481b-130">类的属性数量没有限制。</span><span class="sxs-lookup"><span data-stu-id="d481b-130">Classes have no restriction in the number of properties they have.</span></span>

### <a name="example-class-with-simple-properties"></a><span data-ttu-id="d481b-131">带有简单属性的示例类</span><span class="sxs-lookup"><span data-stu-id="d481b-131">Example class with simple properties</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
}

$device = [Device]::new()
$device.Brand = "Microsoft"
$device.Model = "Surface Pro 4"
$device.VendorSku = "5072641000"

$device
```

```Output
Brand     Model         VendorSku
-----     -----         ---------
Microsoft Surface Pro 4 5072641000
```

### <a name="example-complex-types-in-class-properties"></a><span data-ttu-id="d481b-132">类属性中的复杂类型示例</span><span class="sxs-lookup"><span data-stu-id="d481b-132">Example complex types in class properties</span></span>

<span data-ttu-id="d481b-133">此示例使用 **Device** 类定义一个空 **机架** 类。</span><span class="sxs-lookup"><span data-stu-id="d481b-133">This example defines an empty **Rack** class using the **Device** class.</span></span> <span data-ttu-id="d481b-134">下面的示例演示如何将设备添加到机架，以及如何从预加载的机架开始。</span><span class="sxs-lookup"><span data-stu-id="d481b-134">The examples, following this one, show how to add devices to the rack and how to start with a pre-loaded rack.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
}

class Rack {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new(8)

}

$rack = [Rack]::new()

$rack
```

```Output

Brand     :
Model     :
VendorSku :
AssetId   :
Devices   : {$null, $null, $null, $null...}


```

## <a name="class-methods"></a><span data-ttu-id="d481b-135">类方法</span><span class="sxs-lookup"><span data-stu-id="d481b-135">Class methods</span></span>

<span data-ttu-id="d481b-136">方法定义类可以执行的操作。</span><span class="sxs-lookup"><span data-stu-id="d481b-136">Methods define the actions that a class can perform.</span></span> <span data-ttu-id="d481b-137">方法可能采用提供输入数据的参数。</span><span class="sxs-lookup"><span data-stu-id="d481b-137">Methods may take parameters that provide input data.</span></span> <span data-ttu-id="d481b-138">方法可以返回输出。</span><span class="sxs-lookup"><span data-stu-id="d481b-138">Methods can return output.</span></span> <span data-ttu-id="d481b-139">方法返回的数据可以是任何定义的数据类型。</span><span class="sxs-lookup"><span data-stu-id="d481b-139">Data returned by a method can be any defined data type.</span></span>

<span data-ttu-id="d481b-140">定义类的方法时，可以使用自动变量引用当前类对象 `$this` 。</span><span class="sxs-lookup"><span data-stu-id="d481b-140">When defining a method for a class, you reference the current class object by using the `$this` automatic variable.</span></span> <span data-ttu-id="d481b-141">这允许您访问在当前类中定义的属性和其他方法。</span><span class="sxs-lookup"><span data-stu-id="d481b-141">This allows you to access properties and other methods defined in the current class.</span></span>

### <a name="example-simple-class-with-properties-and-methods"></a><span data-ttu-id="d481b-142">具有属性和方法的示例简单类</span><span class="sxs-lookup"><span data-stu-id="d481b-142">Example simple class with properties and methods</span></span>

<span data-ttu-id="d481b-143">扩展 **机架** 类以在其中添加和删除设备。</span><span class="sxs-lookup"><span data-stu-id="d481b-143">Extending the **Rack** class to add and remove devices to or from it.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    [string]ToString(){
        return ("{0}|{1}|{2}" -f $this.Brand, $this.Model, $this.VendorSku)
    }
}

class Rack {
    [int]$Slots = 8
    [string]$Brand
    [string]$Model
    [string]$VendorSku
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    [void] AddDevice([Device]$dev, [int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $dev
    }

    [void]RemoveDevice([int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $null
    }

    [int[]] GetAvailableSlots(){
        [int]$i = 0
        return @($this.Devices.foreach{ if($_ -eq $null){$i}; $i++})
    }
}

$rack = [Rack]::new()

$surface = [Device]::new()
$surface.Brand = "Microsoft"
$surface.Model = "Surface Pro 4"
$surface.VendorSku = "5072641000"

$rack.AddDevice($surface, 2)

$rack
$rack.GetAvailableSlots()
```

```Output

Slots     : 8
Brand     :
Model     :
VendorSku :
AssetId   :
Devices   : {$null, $null, Microsoft|Surface Pro 4|5072641000, $null...}

0
1
3
4
5
6
7

```

## <a name="output-in-class-methods"></a><span data-ttu-id="d481b-144">类方法中的输出</span><span class="sxs-lookup"><span data-stu-id="d481b-144">Output in class methods</span></span>

<span data-ttu-id="d481b-145">方法应具有定义的返回类型。</span><span class="sxs-lookup"><span data-stu-id="d481b-145">Methods should have a return type defined.</span></span> <span data-ttu-id="d481b-146">如果方法不返回 output，则输出类型应为 `[void]` 。</span><span class="sxs-lookup"><span data-stu-id="d481b-146">If a method doesn't return output, then the output type should be `[void]`.</span></span>

<span data-ttu-id="d481b-147">在类方法中，除了语句中提到的对象之外，不会向管道发送任何对象 `return` 。</span><span class="sxs-lookup"><span data-stu-id="d481b-147">In class methods, no objects get sent to the pipeline except those mentioned in the `return` statement.</span></span> <span data-ttu-id="d481b-148">不会从代码中意外输出到管道。</span><span class="sxs-lookup"><span data-stu-id="d481b-148">There's no accidental output to the pipeline from the code.</span></span>

> [!NOTE]
> <span data-ttu-id="d481b-149">这在本质上与 PowerShell 函数处理输出的方式不同，其中一切都进入管道。</span><span class="sxs-lookup"><span data-stu-id="d481b-149">This is fundamentally different from how PowerShell functions handle output, where everything goes to the pipeline.</span></span>

<span data-ttu-id="d481b-150">从类方法内部写入错误流的非终止错误不会通过。</span><span class="sxs-lookup"><span data-stu-id="d481b-150">Non-terminating errors written to the error stream from inside a class method are not passed through.</span></span> <span data-ttu-id="d481b-151">必须使用 `throw` 来呈现终止错误。</span><span class="sxs-lookup"><span data-stu-id="d481b-151">You must use `throw` to surface a terminating error.</span></span>
<span data-ttu-id="d481b-152">使用 `Write-*` cmdlet，您仍然可以从类方法中写入 PowerShell 的输出流。</span><span class="sxs-lookup"><span data-stu-id="d481b-152">Using the `Write-*` cmdlets, you can still write to PowerShell's output streams from within a class method.</span></span> <span data-ttu-id="d481b-153">但是，应避免使用此方法，以便方法仅使用语句发出对象 `return` 。</span><span class="sxs-lookup"><span data-stu-id="d481b-153">However, this should be avoided so that the method emits objects using only the `return` statement.</span></span>

### <a name="method-output"></a><span data-ttu-id="d481b-154">方法输出</span><span class="sxs-lookup"><span data-stu-id="d481b-154">Method output</span></span>

<span data-ttu-id="d481b-155">此示例演示除了语句外，不会从类方法中意外输出到管道 `return` 。</span><span class="sxs-lookup"><span data-stu-id="d481b-155">This example demonstrates no accidental output to the pipeline from class methods, except on the `return` statement.</span></span>

```powershell
class FunWithIntegers
{
    [int[]]$Integers = 0..10

    [int[]]GetOddIntegers(){
        return $this.Integers.Where({ ($_ % 2) })
    }

    [void] GetEvenIntegers(){
        # this following line doesn't go to the pipeline
        $this.Integers.Where({ ($_ % 2) -eq 0})
    }

    [string]SayHello(){
        # this following line doesn't go to the pipeline
        "Good Morning"

        # this line goes to the pipeline
        return "Hello World"
    }
}

$ints = [FunWithIntegers]::new()
$ints.GetOddIntegers()
$ints.GetEvenIntegers()
$ints.SayHello()
```

```Output
1
3
5
7
9
Hello World

```

## <a name="constructor"></a><span data-ttu-id="d481b-156">构造函数</span><span class="sxs-lookup"><span data-stu-id="d481b-156">Constructor</span></span>

<span data-ttu-id="d481b-157">构造函数使你能够在创建类的实例时设置默认值和验证对象逻辑。</span><span class="sxs-lookup"><span data-stu-id="d481b-157">Constructors enable you to set default values and validate object logic at the moment of creating the instance of the class.</span></span> <span data-ttu-id="d481b-158">构造函数具有与类相同的名称。</span><span class="sxs-lookup"><span data-stu-id="d481b-158">Constructors have the same name as the class.</span></span> <span data-ttu-id="d481b-159">构造函数可能具有参数，用于初始化新对象的数据成员。</span><span class="sxs-lookup"><span data-stu-id="d481b-159">Constructors might have arguments, to initialize the data members of the new object.</span></span>

<span data-ttu-id="d481b-160">类可以定义零个或多个构造函数。</span><span class="sxs-lookup"><span data-stu-id="d481b-160">The class can have zero or more constructors defined.</span></span> <span data-ttu-id="d481b-161">如果未定义任何构造函数，则将为该类提供默认的无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="d481b-161">If no constructor is defined, the class is given a default parameterless constructor.</span></span> <span data-ttu-id="d481b-162">此构造函数将所有成员初始化为其默认值。</span><span class="sxs-lookup"><span data-stu-id="d481b-162">This constructor initializes all members to their default values.</span></span> <span data-ttu-id="d481b-163">为对象类型和字符串提供了 null 值。</span><span class="sxs-lookup"><span data-stu-id="d481b-163">Object types and strings are given null values.</span></span> <span data-ttu-id="d481b-164">定义构造函数时，不会创建默认的无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="d481b-164">When you define constructor, no default parameterless constructor is created.</span></span> <span data-ttu-id="d481b-165">如果需要，请创建一个无参数的构造函数。</span><span class="sxs-lookup"><span data-stu-id="d481b-165">Create a parameterless constructor if one is needed.</span></span>

### <a name="constructor-basic-syntax"></a><span data-ttu-id="d481b-166">构造函数基本语法</span><span class="sxs-lookup"><span data-stu-id="d481b-166">Constructor basic syntax</span></span>

<span data-ttu-id="d481b-167">在此示例中，设备类是使用属性和构造函数定义的。</span><span class="sxs-lookup"><span data-stu-id="d481b-167">In this example, the Device class is defined with properties and a constructor.</span></span>
<span data-ttu-id="d481b-168">若要使用此类，用户需要为构造函数中列出的参数提供值。</span><span class="sxs-lookup"><span data-stu-id="d481b-168">To use this class, the user is required to provide values for the parameters listed in the constructor.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    Device(
        [string]$b,
        [string]$m,
        [string]$vsk
    ){
        $this.Brand = $b
        $this.Model = $m
        $this.VendorSku = $vsk
    }
}

[Device]$surface = [Device]::new("Microsoft", "Surface Pro 4", "5072641000")

$surface
```

```Output
Brand     Model         VendorSku
-----     -----         ---------
Microsoft Surface Pro 4 5072641000
```

### <a name="example-with-multiple-constructors"></a><span data-ttu-id="d481b-169">具有多个构造函数的示例</span><span class="sxs-lookup"><span data-stu-id="d481b-169">Example with multiple constructors</span></span>

<span data-ttu-id="d481b-170">在此示例中，使用属性、默认构造函数和构造函数来定义 **设备** 类以初始化实例。</span><span class="sxs-lookup"><span data-stu-id="d481b-170">In this example, the **Device** class is defined with properties, a default constructor, and a constructor to initialize the instance.</span></span>

<span data-ttu-id="d481b-171">默认构造函数将该 **品牌** 设置为 **Undefined** ，并将 **模型** 和 **供应商-sku** 保留为 null 值。</span><span class="sxs-lookup"><span data-stu-id="d481b-171">The default constructor sets the **brand** to **Undefined** , and leaves **model** and **vendor-sku** with null values.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    Device(){
        $this.Brand = 'Undefined'
    }

    Device(
        [string]$b,
        [string]$m,
        [string]$vsk
    ){
        $this.Brand = $b
        $this.Model = $m
        $this.VendorSku = $vsk
    }
}

[Device]$somedevice = [Device]::new()
[Device]$surface = [Device]::new("Microsoft", "Surface Pro 4", "5072641000")

$somedevice
$surface
```

```Output
Brand       Model           VendorSku
-----       -----           ---------
Undefined
Microsoft   Surface Pro 4   5072641000
```

## <a name="hidden-attribute"></a><span data-ttu-id="d481b-172">隐藏属性</span><span class="sxs-lookup"><span data-stu-id="d481b-172">Hidden attribute</span></span>

<span data-ttu-id="d481b-173">`hidden`属性隐藏属性或方法。</span><span class="sxs-lookup"><span data-stu-id="d481b-173">The `hidden` attribute hides a property or method.</span></span> <span data-ttu-id="d481b-174">用户仍可访问该属性或方法，并且在该对象可用的所有范围内均可用。</span><span class="sxs-lookup"><span data-stu-id="d481b-174">The property or method is still accessible to the user and is available in all scopes in which the object is available.</span></span> <span data-ttu-id="d481b-175">隐藏的成员在 cmdlet 中是隐藏的 `Get-Member` ，不能在类定义之外使用 tab 自动补全或 IntelliSense 来显示。</span><span class="sxs-lookup"><span data-stu-id="d481b-175">Hidden members are hidden from the `Get-Member` cmdlet and can't be displayed using tab completion or IntelliSense outside the class definition.</span></span>

<span data-ttu-id="d481b-176">有关详细信息，请参阅 [About_hidden](About_hidden.md)。</span><span class="sxs-lookup"><span data-stu-id="d481b-176">For more information, see [About_hidden](About_hidden.md).</span></span>

### <a name="example-using-hidden-attributes"></a><span data-ttu-id="d481b-177">使用隐藏特性的示例</span><span class="sxs-lookup"><span data-stu-id="d481b-177">Example using hidden attributes</span></span>

<span data-ttu-id="d481b-178">创建 **机架** 对象时，设备的槽数是固定值，不应在任何时间更改。</span><span class="sxs-lookup"><span data-stu-id="d481b-178">When a **Rack** object is created, the number of slots for devices is a fixed value that shouldn't be changed at any time.</span></span> <span data-ttu-id="d481b-179">此值在创建时是已知的。</span><span class="sxs-lookup"><span data-stu-id="d481b-179">This value is known at creation time.</span></span>

<span data-ttu-id="d481b-180">使用 hidden 属性允许开发人员保持隐藏的槽数，并防止意外更改机架的大小。</span><span class="sxs-lookup"><span data-stu-id="d481b-180">Using the hidden attribute allows the developer to keep the number of slots hidden and prevents unintentional changes the size of the rack.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
}

class Rack {
    [int] hidden $Slots = 8
    [string]$Brand
    [string]$Model
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack ([string]$b, [string]$m, [int]$capacity){
        ## argument validation here

        $this.Brand = $b
        $this.Model = $m
        $this.Slots = $capacity

        ## reset rack size to new capacity
        $this.Devices = [Device[]]::new($this.Slots)
    }
}

[Rack]$r1 = [Rack]::new("Microsoft", "Surface Pro 4", 16)

$r1
$r1.Devices.Length
$r1.Slots
```

```Output
Brand     Model         Devices
-----     -----         -------
Microsoft Surface Pro 4 {$null, $null, $null, $null...}
16
16
```

<span data-ttu-id="d481b-181">"公告 **槽** " 属性未显示在 `$r1` 输出中。</span><span class="sxs-lookup"><span data-stu-id="d481b-181">Notice **Slots** property isn't shown in `$r1` output.</span></span> <span data-ttu-id="d481b-182">但是，该大小已由构造函数更改。</span><span class="sxs-lookup"><span data-stu-id="d481b-182">However, the size was changed by the constructor.</span></span>

## <a name="static-attribute"></a><span data-ttu-id="d481b-183">静态属性</span><span class="sxs-lookup"><span data-stu-id="d481b-183">Static attribute</span></span>

<span data-ttu-id="d481b-184">`static`特性定义类中存在的属性或方法，无需任何实例。</span><span class="sxs-lookup"><span data-stu-id="d481b-184">The `static` attribute defines a property or a method that exists in the class and needs no instance.</span></span>

<span data-ttu-id="d481b-185">静态属性始终可用，与类实例化无关。</span><span class="sxs-lookup"><span data-stu-id="d481b-185">A static property is always available, independent of class instantiation.</span></span> <span data-ttu-id="d481b-186">静态属性跨类的所有实例共享。</span><span class="sxs-lookup"><span data-stu-id="d481b-186">A static property is shared across all instances of the class.</span></span> <span data-ttu-id="d481b-187">静态方法始终可用。</span><span class="sxs-lookup"><span data-stu-id="d481b-187">A static method is available always.</span></span> <span data-ttu-id="d481b-188">整个会话范围内的所有静态属性。</span><span class="sxs-lookup"><span data-stu-id="d481b-188">All static properties live for the entire session span.</span></span>

### <a name="example-using-static-attributes-and-methods"></a><span data-ttu-id="d481b-189">使用静态属性和方法的示例</span><span class="sxs-lookup"><span data-stu-id="d481b-189">Example using static attributes and methods</span></span>

<span data-ttu-id="d481b-190">假设你的数据中心中存在此处实例化的机架。</span><span class="sxs-lookup"><span data-stu-id="d481b-190">Assume the racks instantiated here exist in your data center.</span></span> <span data-ttu-id="d481b-191">因此，您希望在代码中跟踪机架。</span><span class="sxs-lookup"><span data-stu-id="d481b-191">So, you would like to keep track of the racks in your code.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
}

class Rack {
    hidden [int] $Slots = 8
    static [Rack[]]$InstalledRacks = @()
    [string]$Brand
    [string]$Model
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack ([string]$b, [string]$m, [string]$id, [int]$capacity){
        ## argument validation here

        $this.Brand = $b
        $this.Model = $m
        $this.AssetId = $id
        $this.Slots = $capacity

        ## reset rack size to new capacity
        $this.Devices = [Device[]]::new($this.Slots)

        ## add rack to installed racks
        [Rack]::InstalledRacks += $this
    }

    static [void]PowerOffRacks(){
        foreach ($rack in [Rack]::InstalledRacks) {
            Write-Warning ("Turning off rack: " + ($rack.AssetId))
        }
    }
}
```

### <a name="testing-static-property-and-method-exist"></a><span data-ttu-id="d481b-192">测试静态属性和方法存在</span><span class="sxs-lookup"><span data-stu-id="d481b-192">Testing static property and method exist</span></span>

```
PS> [Rack]::InstalledRacks.Length
0

PS> [Rack]::PowerOffRacks()

PS> (1..10) | ForEach-Object {
>>   [Rack]::new("Adatum Corporation", "Standard-16",
>>     $_.ToString("Std0000"), 16)
>> } > $null

PS> [Rack]::InstalledRacks.Length
10

PS> [Rack]::InstalledRacks[3]
Brand              Model       AssetId Devices
-----              -----       ------- -------
Adatum Corporation Standard-16 Std0004 {$null, $null, $null, $null...}

PS> [Rack]::PowerOffRacks()
WARNING: Turning off rack: Std0001
WARNING: Turning off rack: Std0002
WARNING: Turning off rack: Std0003
WARNING: Turning off rack: Std0004
WARNING: Turning off rack: Std0005
WARNING: Turning off rack: Std0006
WARNING: Turning off rack: Std0007
WARNING: Turning off rack: Std0008
WARNING: Turning off rack: Std0009
WARNING: Turning off rack: Std0010
```

<span data-ttu-id="d481b-193">请注意，每次运行此示例时，机架数都会增加。</span><span class="sxs-lookup"><span data-stu-id="d481b-193">Notice that the number of racks increases each time you run this example.</span></span>

## <a name="property-validation-attributes"></a><span data-ttu-id="d481b-194">属性验证特性</span><span class="sxs-lookup"><span data-stu-id="d481b-194">Property validation attributes</span></span>

<span data-ttu-id="d481b-195">通过验证特性，可以测试为属性指定的值是否满足定义的要求。</span><span class="sxs-lookup"><span data-stu-id="d481b-195">Validation attributes allow you to test that values given to properties meet defined requirements.</span></span> <span data-ttu-id="d481b-196">在分配值时触发验证。</span><span class="sxs-lookup"><span data-stu-id="d481b-196">Validation is triggered the moment that the value is assigned.</span></span> <span data-ttu-id="d481b-197">请参阅 [about_functions_advanced_parameters](about_functions_advanced_parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="d481b-197">See [about_functions_advanced_parameters](about_functions_advanced_parameters.md).</span></span>

### <a name="example-using-validation-attributes"></a><span data-ttu-id="d481b-198">使用验证特性的示例</span><span class="sxs-lookup"><span data-stu-id="d481b-198">Example using validation attributes</span></span>

```powershell
class Device {
    [ValidateNotNullOrEmpty()][string]$Brand
    [ValidateNotNullOrEmpty()][string]$Model
}

[Device]$dev = [Device]::new()

Write-Output "Testing dev"
$dev

$dev.Brand = ""
```

```Output
Testing dev

Brand Model
----- -----

Exception setting "Brand": "The argument is null or empty. Provide an
argument that is not null or empty, and then try the command again."
At C:\tmp\Untitled-5.ps1:11 char:1
+ $dev.Brand = ""
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [], SetValueInvocationException
    + FullyQualifiedErrorId : ExceptionWhenSetting
```

## <a name="inheritance-in-powershell-classes"></a><span data-ttu-id="d481b-199">PowerShell 类中的继承</span><span class="sxs-lookup"><span data-stu-id="d481b-199">Inheritance in PowerShell classes</span></span>

<span data-ttu-id="d481b-200">可以通过创建从现有类派生的新类来扩展类。</span><span class="sxs-lookup"><span data-stu-id="d481b-200">You can extend a class by creating a new class that derives from an existing class.</span></span> <span data-ttu-id="d481b-201">派生类继承基类的属性。</span><span class="sxs-lookup"><span data-stu-id="d481b-201">The derived class inherits the properties of the base class.</span></span> <span data-ttu-id="d481b-202">您可以根据需要添加或重写方法和属性。</span><span class="sxs-lookup"><span data-stu-id="d481b-202">You can add or override methods and properties as required.</span></span>

<span data-ttu-id="d481b-203">PowerShell 不支持多重继承。</span><span class="sxs-lookup"><span data-stu-id="d481b-203">PowerShell does not support multiple inheritance.</span></span> <span data-ttu-id="d481b-204">类不能从多个类继承。</span><span class="sxs-lookup"><span data-stu-id="d481b-204">Classes cannot inherit from more than one class.</span></span> <span data-ttu-id="d481b-205">不过，您可以使用接口来实现此目的。</span><span class="sxs-lookup"><span data-stu-id="d481b-205">However, you can use interfaces for that purpose.</span></span>

<span data-ttu-id="d481b-206">继承实现由 `:` 运算符定义; 这意味着扩展此类或实现这些接口。</span><span class="sxs-lookup"><span data-stu-id="d481b-206">Inheritance implementation is defined by the `:` operator; which means to extend this class or implements these interfaces.</span></span> <span data-ttu-id="d481b-207">派生类应始终在类声明中的最左侧。</span><span class="sxs-lookup"><span data-stu-id="d481b-207">The derived class should always be leftmost in the class declaration.</span></span>

### <a name="example-using-simple-inheritance-syntax"></a><span data-ttu-id="d481b-208">使用简单继承语法的示例</span><span class="sxs-lookup"><span data-stu-id="d481b-208">Example using simple inheritance syntax</span></span>

<span data-ttu-id="d481b-209">此示例显示了简单的 PowerShell 类继承语法。</span><span class="sxs-lookup"><span data-stu-id="d481b-209">This example shows the simple PowerShell class inheritance syntax.</span></span>

```powershell
Class Derived : Base {...}
```

<span data-ttu-id="d481b-210">此示例演示了具有基类的接口声明的继承。</span><span class="sxs-lookup"><span data-stu-id="d481b-210">This example shows inheritance with an interface declaration coming after the base class.</span></span>

```powershell
Class Derived : Base, Interface {...}
```

### <a name="example-of-simple-inheritance-in-powershell-classes"></a><span data-ttu-id="d481b-211">PowerShell 类中的简单继承示例</span><span class="sxs-lookup"><span data-stu-id="d481b-211">Example of simple inheritance in PowerShell classes</span></span>

<span data-ttu-id="d481b-212">在此示例中，在前面的示例中使用的 **机架** 和 **设备** 类更好地定义为：避免属性重复，更好地对齐通用属性，并重复使用常见业务逻辑。</span><span class="sxs-lookup"><span data-stu-id="d481b-212">In this example the **Rack** and **Device** classes used in the previous examples are better defined to: avoid property repetitions, better align common properties, and reuse common business logic.</span></span>

<span data-ttu-id="d481b-213">数据中心内的大多数对象都是公司资产，因此，开始将其作为资产进行跟踪是有意义的。</span><span class="sxs-lookup"><span data-stu-id="d481b-213">Most objects in the data center are company assets, which makes sense to start tracking them as assets.</span></span> <span data-ttu-id="d481b-214">设备类型由 `DeviceType` 枚举定义，有关枚举的详细信息，请参阅 [about_Enum](about_Enum.md) 。</span><span class="sxs-lookup"><span data-stu-id="d481b-214">Device types are defined by the `DeviceType` enumeration, see [about_Enum](about_Enum.md) for details on enumerations.</span></span>

<span data-ttu-id="d481b-215">在我们的示例中，我们仅定义 `Rack` 和 `ComputeServer` ; 这两个扩展都是 `Device` 类的。</span><span class="sxs-lookup"><span data-stu-id="d481b-215">In our example, we're only defining `Rack` and `ComputeServer`; both extensions to the `Device` class.</span></span>

```powershell
enum DeviceType {
    Undefined = 0
    Compute = 1
    Storage = 2
    Networking = 4
    Communications = 8
    Power = 16
    Rack = 32
}

class Asset {
    [string]$Brand
    [string]$Model
}

class Device : Asset {
    hidden [DeviceType]$devtype = [DeviceType]::Undefined
    [string]$Status

    [DeviceType] GetDeviceType(){
        return $this.devtype
    }
}

class ComputeServer : Device {
    hidden [DeviceType]$devtype = [DeviceType]::Compute
    [string]$ProcessorIdentifier
    [string]$Hostname
}

class Rack : Device {
    hidden [DeviceType]$devtype = [DeviceType]::Rack
    hidden [int]$Slots = 8

    [string]$Datacenter
    [string]$Location
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack (){
        ## Just create the default rack with 8 slots
    }

    Rack ([int]$s){
        ## Add argument validation logic here
        $this.Devices = [Device[]]::new($s)
    }

    [void] AddDevice([Device]$dev, [int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $dev
    }

    [void] RemoveDevice([int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $null
    }
}

$FirstRack = [Rack]::new(16)
$FirstRack.Status = "Operational"
$FirstRack.Datacenter = "PNW"
$FirstRack.Location = "F03R02.J10"

(0..15).ForEach({
    $ComputeServer = [ComputeServer]::new()
    $ComputeServer.Brand = "Fabrikam, Inc."       ## Inherited from Asset
    $ComputeServer.Model = "Fbk5040"              ## Inherited from Asset
    $ComputeServer.Status = "Installed"           ## Inherited from Device
    $ComputeServer.ProcessorIdentifier = "x64"    ## ComputeServer
    $ComputeServer.Hostname = ("r1s" + $_.ToString("000")) ## ComputeServer
    $FirstRack.AddDevice($ComputeServer, $_)
  })

$FirstRack
$FirstRack.Devices
```

```Output
Datacenter : PNW
Location   : F03R02.J10
Devices    : {r1s000, r1s001, r1s002, r1s003...}
Status     : Operational
Brand      :
Model      :

ProcessorIdentifier : x64
Hostname            : r1s000
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040

ProcessorIdentifier : x64
Hostname            : r1s001
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040

<... content truncated here for brevity ...>

ProcessorIdentifier : x64
Hostname            : r1s015
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040
```

### <a name="calling-base-class-constructors"></a><span data-ttu-id="d481b-216">调用基类构造函数</span><span class="sxs-lookup"><span data-stu-id="d481b-216">Calling base class constructors</span></span>

<span data-ttu-id="d481b-217">若要从子类调用基类构造函数，请添加 `base` 关键字。</span><span class="sxs-lookup"><span data-stu-id="d481b-217">To invoke a base class constructor from a subclass, add the `base` keyword.</span></span>

```powershell
class Person {
    [int]$Age

    Person([int]$a)
    {
        $this.Age = $a
    }
}

class Child : Person
{
    [string]$School

    Child([int]$a, [string]$s ) : base($a) {
        $this.School = $s
    }
}

[Child]$littleone = [Child]::new(10, "Silver Fir Elementary School")

$littleone.Age
```

```Output

10
```

### <a name="invoke-base-class-methods"></a><span data-ttu-id="d481b-218">调用基类方法</span><span class="sxs-lookup"><span data-stu-id="d481b-218">Invoke base class methods</span></span>

<span data-ttu-id="d481b-219">若要重写子类中的现有方法，请使用相同的名称和签名声明方法。</span><span class="sxs-lookup"><span data-stu-id="d481b-219">To override existing methods in subclasses, declare methods using the same name and signature.</span></span>

```powershell
class BaseClass
{
    [int]days() {return 1}
}
class ChildClass1 : BaseClass
{
    [int]days () {return 2}
}

[ChildClass1]::new().days()
```

```Output

2
```

<span data-ttu-id="d481b-220">若要从重写实现中调用基类方法，请在调用时强制转换为基类 ( [baseclass] $this) 。</span><span class="sxs-lookup"><span data-stu-id="d481b-220">To call base class methods from overridden implementations, cast to the base class ([baseclass]$this) on invocation.</span></span>

```powershell
class BaseClass
{
    [int]days() {return 1}
}
class ChildClass1 : BaseClass
{
    [int]days () {return 2}
    [int]basedays() {return ([BaseClass]$this).days()}
}

[ChildClass1]::new().days()
[ChildClass1]::new().basedays()
```

```Output

2
1
```

### <a name="inheriting-from-interfaces"></a><span data-ttu-id="d481b-221">从接口继承</span><span class="sxs-lookup"><span data-stu-id="d481b-221">Inheriting from interfaces</span></span>

<span data-ttu-id="d481b-222">PowerShell 类可以使用用于扩展基类的相同继承语法来实现接口。</span><span class="sxs-lookup"><span data-stu-id="d481b-222">PowerShell classes can implement an interface using the same inheritance syntax used to extend base classes.</span></span> <span data-ttu-id="d481b-223">由于接口允许多个继承，因此，实现接口的 PowerShell 类可以从多个类型继承，方法是在冒号后 `:` 使用逗号 () 分隔类型名称 () `,` 。</span><span class="sxs-lookup"><span data-stu-id="d481b-223">Because interfaces allow multiple inheritance, a PowerShell class implementing an interface may inherit from multiple types, by separating the type names after the colon (`:`) with commas (`,`).</span></span> <span data-ttu-id="d481b-224">实现接口的 PowerShell 类必须实现该接口的所有成员。</span><span class="sxs-lookup"><span data-stu-id="d481b-224">A PowerShell class that implements an interface must implement all the members of that interface.</span></span> <span data-ttu-id="d481b-225">省略实现接口成员将导致脚本中出现分析时错误。</span><span class="sxs-lookup"><span data-stu-id="d481b-225">Omitting the implemention interface members causes a parse-time error in the script.</span></span>

> [!NOTE]
> <span data-ttu-id="d481b-226">PowerShell 当前不支持在 PowerShell 脚本中声明新接口。</span><span class="sxs-lookup"><span data-stu-id="d481b-226">PowerShell does not currently support declaring new interfaces in PowerShell script.</span></span>

```powershell
class MyComparable : System.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, System.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

## <a name="importing-classes-from-a-powershell-module"></a><span data-ttu-id="d481b-227">从 PowerShell 模块导入类</span><span class="sxs-lookup"><span data-stu-id="d481b-227">Importing classes from a PowerShell module</span></span>

<span data-ttu-id="d481b-228">`Import-Module``#requires`语句仅导入模块定义的模块函数、别名和变量。</span><span class="sxs-lookup"><span data-stu-id="d481b-228">`Import-Module` and the `#requires` statement only import the module functions, aliases, and variables, as defined by the module.</span></span> <span data-ttu-id="d481b-229">不导入类。</span><span class="sxs-lookup"><span data-stu-id="d481b-229">Classes are not imported.</span></span> <span data-ttu-id="d481b-230">`using module`语句将导入模块中定义的类。</span><span class="sxs-lookup"><span data-stu-id="d481b-230">The `using module` statement imports the classes defined in the module.</span></span> <span data-ttu-id="d481b-231">如果该模块未在当前会话中加载，则该 `using` 语句将失败。</span><span class="sxs-lookup"><span data-stu-id="d481b-231">If the module isn't loaded in the current session, the `using` statement fails.</span></span> <span data-ttu-id="d481b-232">有关语句的详细信息 `using` ，请参阅 [about_Using](about_Using.md)。</span><span class="sxs-lookup"><span data-stu-id="d481b-232">For more information about the `using` statement, see [about_Using](about_Using.md).</span></span>

## <a name="the-psreference-type-is-not-supported-with-class-members"></a><span data-ttu-id="d481b-233">类成员不支持 PSReference 类型</span><span class="sxs-lookup"><span data-stu-id="d481b-233">The PSReference type is not supported with class members</span></span>

<span data-ttu-id="d481b-234">对 `[ref]` 类成员使用类型强制转换将失败。</span><span class="sxs-lookup"><span data-stu-id="d481b-234">Using the `[ref]` type-cast with a class member silently fails.</span></span> <span data-ttu-id="d481b-235">使用参数的 Api `[ref]` 不能与类成员一起使用。</span><span class="sxs-lookup"><span data-stu-id="d481b-235">APIs that use `[ref]` parameters cannot be used with class members.</span></span> <span data-ttu-id="d481b-236">**PSReference** 旨在支持 COM 对象。</span><span class="sxs-lookup"><span data-stu-id="d481b-236">The **PSReference** was designed to support COM objects.</span></span> <span data-ttu-id="d481b-237">COM 对象的情况下，需要通过引用传递中的值。</span><span class="sxs-lookup"><span data-stu-id="d481b-237">COM objects have cases where you need to pass a value in by reference.</span></span>

<span data-ttu-id="d481b-238">有关类型的详细信息 `[ref]` ，请参阅 [PSReference 类](/dotnet/api/system.management.automation.psreference)。</span><span class="sxs-lookup"><span data-stu-id="d481b-238">For more information about the `[ref]` type, see [PSReference Class](/dotnet/api/system.management.automation.psreference).</span></span>

## <a name="see-also"></a><span data-ttu-id="d481b-239">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d481b-239">See also</span></span>

- [<span data-ttu-id="d481b-240">About_hidden</span><span class="sxs-lookup"><span data-stu-id="d481b-240">About_hidden</span></span>](About_hidden.md)
- [<span data-ttu-id="d481b-241">about_Enum</span><span class="sxs-lookup"><span data-stu-id="d481b-241">about_Enum</span></span>](about_Enum.md)
- [<span data-ttu-id="d481b-242">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="d481b-242">about_Language_Keywords</span></span>](about_language_keywords.md)
- [<span data-ttu-id="d481b-243">about_Methods</span><span class="sxs-lookup"><span data-stu-id="d481b-243">about_Methods</span></span>](about_methods.md)
- [<span data-ttu-id="d481b-244">about_Using</span><span class="sxs-lookup"><span data-stu-id="d481b-244">about_Using</span></span>](about_using.md)
