---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Tworzenie typów niestandardowych przy użyciu klas programu PowerShell
ms.openlocfilehash: c2c50fb65ce4931fcf6ae529b4146df391c831c4
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470934"
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="b9ec7-103">Tworzenie typów niestandardowych przy użyciu klas programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9ec7-103">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="b9ec7-104">PowerShell 5.0 dodano możliwość definiowania klas i innych typów zdefiniowanych przez użytkownika za pomocą formalne składnia i semantyka, takich jak innych języków programowania obiektowego.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-104">PowerShell 5.0 added the ability to define classes and other user-defined types using formal syntax and semantics like other object-oriented programming languages.</span></span> <span data-ttu-id="b9ec7-105">Celem jest umożliwienie deweloperom i informatykom przyjęcie programu PowerShell dla szerszego zakresu zastosowań, upraszczają proces tworzenia artefaktów programu PowerShell (takich jak zasoby DSC) oraz skrócenia procesu pokrycia powierzchni zarządzania.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-105">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="b9ec7-106">Scenariusze obsługiwane w tej wersji</span><span class="sxs-lookup"><span data-stu-id="b9ec7-106">Supported scenarios in this release</span></span>

- <span data-ttu-id="b9ec7-107">Zdefiniuj zasoby DSC i ich skojarzone typy przy użyciu języka programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9ec7-107">Define DSC resources and their associated types by using the PowerShell language</span></span>
- <span data-ttu-id="b9ec7-108">Definiowanie typów niestandardowych w programie PowerShell, za pomocą dobrze znanych zorientowane obiektowo narzędzi programistycznych, takich jak klasy, właściwości, metod itd.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-108">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
- <span data-ttu-id="b9ec7-109">Obsługa dziedziczenia z klasy w podstawowej zasobów DSC programu PowerShell i klasy</span><span class="sxs-lookup"><span data-stu-id="b9ec7-109">Inheritance support with class in PowerShell and class base DSC resource</span></span>
- <span data-ttu-id="b9ec7-110">Debugowanie typów przy użyciu języka programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9ec7-110">Debug types by using the PowerShell language</span></span>
- <span data-ttu-id="b9ec7-111">Generowanie i obsługa wyjątków za pomocą mechanizmów formalne i na właściwym poziomie</span><span class="sxs-lookup"><span data-stu-id="b9ec7-111">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>

## <a name="declare-base-class"></a><span data-ttu-id="b9ec7-112">Deklarowanie klasy bazowej</span><span class="sxs-lookup"><span data-stu-id="b9ec7-112">Declare Base Class</span></span>

<span data-ttu-id="b9ec7-113">Klasa programu PowerShell można zadeklarować jako typ podstawowy dla innej klasy programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-113">You can declare a PowerShell class as a base type for another PowerShell class.</span></span>

```powershell
class bar
{
   [int]foo()
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

<span data-ttu-id="b9ec7-114">Można również użyć istniejących typów programu .NET Framework jako klay bazowe:</span><span class="sxs-lookup"><span data-stu-id="b9ec7-114">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

### <a name="call-base-class-constructor"></a><span data-ttu-id="b9ec7-115">Wywoływanie konstruktora klasy bazowej</span><span class="sxs-lookup"><span data-stu-id="b9ec7-115">Call Base Class Constructor</span></span>

<span data-ttu-id="b9ec7-116">Aby wywołać konstruktora klasy bazowej z podklasy, należy użyć słowa kluczowego **podstawowy**:</span><span class="sxs-lookup"><span data-stu-id="b9ec7-116">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

```powershell
class A
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

<span data-ttu-id="b9ec7-117">Jeśli klasa bazowa ma Konstruktor domyślny (nie parametrów), można pominąć wywołanie jawny Konstruktor:</span><span class="sxs-lookup"><span data-stu-id="b9ec7-117">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-method"></a><span data-ttu-id="b9ec7-118">Wywoływanie metody klasy bazowej</span><span class="sxs-lookup"><span data-stu-id="b9ec7-118">Call Base Class Method</span></span>

<span data-ttu-id="b9ec7-119">Można zastąpić istniejących metod w podklasach.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-119">You can override existing methods in subclasses.</span></span> <span data-ttu-id="b9ec7-120">Aby to zrobić, należy zadeklarować metody przy użyciu tej samej nazwie i sygnaturze:</span><span class="sxs-lookup"><span data-stu-id="b9ec7-120">To do this, declare methods by using the same name and signature:</span></span>

```powershell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

<span data-ttu-id="b9ec7-121">Aby wywołać metody klasy bazowej z implementacji zastąpione, rzutowanie do klasy bazowej (`[baseClass]$this`) na wywołania:</span><span class="sxs-lookup"><span data-stu-id="b9ec7-121">To call base class methods from overridden implementations, cast to the base class (`[baseClass]$this`) on invocation:</span></span>

```powershell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

<span data-ttu-id="b9ec7-122">Wszystkie metody programu PowerShell są wirtualne.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-122">All PowerShell methods are virtual.</span></span> <span data-ttu-id="b9ec7-123">Można ukryć .NET metod niewirtualnych w podklasę przy użyciu tej samej składni, tak jak w przypadku zastąpienia, przez zadeklarowanie metody o tej samej nazwie i sygnaturze.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-123">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override, by declaring methods with same name and signature.</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```

### <a name="declare-implemented-interface"></a><span data-ttu-id="b9ec7-124">Deklarowanie zaimplementowanego interfejsu</span><span class="sxs-lookup"><span data-stu-id="b9ec7-124">Declare Implemented Interface</span></span>

<span data-ttu-id="b9ec7-125">Możesz zadeklarować implementowane interfejsy po typy podstawowe lub od razu po dwukropek (:), jeśli bez określonego typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-125">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="b9ec7-126">Oddziel nazwy wszystkich typów za pomocą przecinków.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-126">Separate all type names by using commas.</span></span> <span data-ttu-id="b9ec7-127">Jest on podobny do C# składni.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-127">It's similar to C# syntax.</span></span>

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

## <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="b9ec7-128">Nowe funkcje języka, w programie PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b9ec7-128">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="b9ec7-129">PowerShell 5.0 wprowadzono następujące nowe elementy języka w programie PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b9ec7-129">PowerShell 5.0 introduces the following new language elements in PowerShell:</span></span>

### <a name="class-keyword"></a><span data-ttu-id="b9ec7-130">Class — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="b9ec7-130">Class keyword</span></span>

<span data-ttu-id="b9ec7-131">`class` — Słowo kluczowe definiuje nową klasę.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-131">The `class` keyword defines a new class.</span></span> <span data-ttu-id="b9ec7-132">Jest to PRAWDA typ .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-132">This is a true .NET Framework type.</span></span> <span data-ttu-id="b9ec7-133">Elementy członkowskie klasy są publiczne, ale tylko publiczne w zakresie modułu.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-133">Class members are public, but only public within the module scope.</span></span> <span data-ttu-id="b9ec7-134">Nie można odwołać się do nazwy typu jako ciąg (na przykład `New-Object` nie działa), w tej wersji, ale nie można użyć literału typu (na przykład `[MyClass]`) poza plikiem skryptu lub moduł, w którym klasa jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-134">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script or module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="b9ec7-135">Enum — słowo kluczowe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="b9ec7-135">Enum keyword and enumerations</span></span>

<span data-ttu-id="b9ec7-136">Obsługa `enum` — słowo kluczowe zostały dodane, który używa nowego wiersza jako ogranicznika.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-136">Support for the `enum` keyword has been added, which uses newline as the delimiter.</span></span> <span data-ttu-id="b9ec7-137">Obecnie nie można zdefiniować moduł wyliczający pod względem samego.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-137">Currently, you cannot define an enumerator in terms of itself.</span></span> <span data-ttu-id="b9ec7-138">Jednak należy zainicjować wyliczenia pod względem innego typu wyliczeniowego, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-138">However, you can initialize an enum in terms of another enum, as shown in the following example.</span></span> <span data-ttu-id="b9ec7-139">Ponadto nie można określić typu podstawowego; zawsze warto też `[int]`.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-139">Also, the base type cannot be specified; it is always `[int]`.</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="b9ec7-140">Wartość modułu wyliczającego musi być stałą czasu analizy.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-140">An enumerator value must be a parse time constant.</span></span> <span data-ttu-id="b9ec7-141">Nie możesz ustawić wyniku wywoływane polecenie.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-141">You cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="b9ec7-142">Typy wyliczeniowe obsługują operacje arytmetyczne, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-142">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a><span data-ttu-id="b9ec7-143">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="b9ec7-143">Import-DscResource</span></span>

<span data-ttu-id="b9ec7-144">`Import-DscResource` jest teraz true — słowo kluczowe dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-144">`Import-DscResource` is now a true dynamic keyword.</span></span> <span data-ttu-id="b9ec7-145">Program PowerShell analizuje modułu głównego określonego modułu, Wyszukiwanie klas, które zawierają **DscResource** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-145">PowerShell parses the specified module's root module, searching for classes that contain the **DscResource** attribute.</span></span>

### <a name="implementingassembly"></a><span data-ttu-id="b9ec7-146">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="b9ec7-146">ImplementingAssembly</span></span>

<span data-ttu-id="b9ec7-147">Nowe pole **ImplementingAssembly**, została dodana do **ModuleInfo**.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-147">A new field, **ImplementingAssembly**, has been added to **ModuleInfo**.</span></span> <span data-ttu-id="b9ec7-148">Ustawiono się do zestawu dynamicznego utworzony dla modułu skryptu, jeśli skrypt definiuje klasy lub załadować zestawu dla moduły binarne.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-148">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="b9ec7-149">Nie jest ustawiona podczas **ModuleType** jest **manifestu**.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-149">It is not set when **ModuleType** is **Manifest**.</span></span>

<span data-ttu-id="b9ec7-150">Rozważania na temat **ImplementingAssembly** pola odnalezieniu zasobów w module.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-150">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="b9ec7-151">Oznacza to, że można odnajdywać zasoby napisane w programie PowerShell lub innych języków zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-151">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="b9ec7-152">Pola z inicjatorami:</span><span class="sxs-lookup"><span data-stu-id="b9ec7-152">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="b9ec7-153">`Static` jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-153">`Static` is supported.</span></span> <span data-ttu-id="b9ec7-154">Działa podobnie jak atrybut, jak to ma ograniczenia typu.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-154">It works like an attribute, as do the type constraints.</span></span> <span data-ttu-id="b9ec7-155">Mogą być podane w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-155">It can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="b9ec7-156">Typem jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-156">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="b9ec7-157">Wszystkie elementy członkowskie są publiczne.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-157">All members are public.</span></span>

### <a name="constructors-and-instantiation"></a><span data-ttu-id="b9ec7-158">Konstruktory i wystąpienia</span><span class="sxs-lookup"><span data-stu-id="b9ec7-158">Constructors and instantiation</span></span>

<span data-ttu-id="b9ec7-159">Klas programu PowerShell mogą mieć konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-159">PowerShell classes can have constructors.</span></span> <span data-ttu-id="b9ec7-160">Mają one taką samą nazwę jak ich klasy.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-160">They have the same name as their class.</span></span> <span data-ttu-id="b9ec7-161">Mogą być przeciążone konstruktory.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-161">Constructors can be overloaded.</span></span> <span data-ttu-id="b9ec7-162">Konstruktory statyczne są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-162">Static constructors are supported.</span></span> <span data-ttu-id="b9ec7-163">Właściwości za pomocą wyrażenia inicjowania są inicjowane przed uruchomieniem jakiegokolwiek kodu w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-163">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="b9ec7-164">Właściwości statyczne są inicjowane przed treści statyczny Konstruktor i właściwości wystąpienia są inicjowane przed treść konstruktora niestatycznych.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-164">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="b9ec7-165">Obecnie nie ma żadnych składnia wywoływania konstruktora od innego konstruktora (takich jak C\# składni ": this()").</span><span class="sxs-lookup"><span data-stu-id="b9ec7-165">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="b9ec7-166">Obejście polega na zdefiniowaniu często `Init()` metody.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-166">The workaround is to define a common `Init()` method.</span></span>

#### <a name="creating-instances"></a><span data-ttu-id="b9ec7-167">Tworzenie instancji</span><span class="sxs-lookup"><span data-stu-id="b9ec7-167">Creating instances</span></span>

> [!NOTE]
> <span data-ttu-id="b9ec7-168">W programie PowerShell w wersji 5.0 `New-Object` nie działa z klas zdefiniowanych w programie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-168">In PowerShell 5.0, `New-Object` does not work with classes defined in PowerShell.</span></span> <span data-ttu-id="b9ec7-169">Ponadto nazwa typu jest tylko widoczne leksykalnie, co oznacza, że nie jest widoczne na zewnątrz modułu lub skryptu, który definiuje klasę.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-169">Also, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="b9ec7-170">Funkcje mogą zwracać wystąpienia klasy zdefiniowanej w programie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-170">Functions can return instances of a class defined in PowerShell.</span></span> <span data-ttu-id="b9ec7-171">Te wystąpienia działają poza modułu lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-171">Those instances work outside of the module or script.</span></span>

1. <span data-ttu-id="b9ec7-172">Utworzenie wystąpienia przy użyciu domyślnego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-172">Instantiating by using the default constructor.</span></span>

   ```powershell
   $a = [MyClass]::new()
   ```

1. <span data-ttu-id="b9ec7-173">Wywołanie konstruktora z parametrem</span><span class="sxs-lookup"><span data-stu-id="b9ec7-173">Calling a constructor with a parameter</span></span>

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. <span data-ttu-id="b9ec7-174">Przekazywanie tablicę do konstruktora z wieloma parametrami.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-174">Passing an array to a constructor with multiple parameters.</span></span>

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

<span data-ttu-id="b9ec7-175">Pseudolosowego statycznej metody `new()` działa z typami .NET, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-175">The pseudo-static method `new()` works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

#### <a name="discovering-constructors"></a><span data-ttu-id="b9ec7-176">Odnajdywanie konstruktorów</span><span class="sxs-lookup"><span data-stu-id="b9ec7-176">Discovering constructors</span></span>

<span data-ttu-id="b9ec7-177">Teraz możesz wyświetlać przeciążeń konstruktora z `Get-Member`, lub jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="b9ec7-177">You can now see constructor overloads with `Get-Member`, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

<span data-ttu-id="b9ec7-178">`Get-Member -Static` Wyświetla listę konstruktorów, aby można było wyświetlić przeciążenia, jak każda inna metoda.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-178">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="b9ec7-179">Wydajność tej składni jest również znacznie szybsze niż `New-Object`.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-179">The performance of this syntax is also considerably faster than `New-Object`.</span></span>

### <a name="methods"></a><span data-ttu-id="b9ec7-180">Metody</span><span class="sxs-lookup"><span data-stu-id="b9ec7-180">Methods</span></span>

<span data-ttu-id="b9ec7-181">Metoda klasy programu PowerShell jest implementowany jako **ScriptBlock** zawierający tylko blok końcowy.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-181">A PowerShell class method is implemented as a **ScriptBlock** that has only an end block.</span></span> <span data-ttu-id="b9ec7-182">Wszystkie metody są publiczne.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-182">All methods are public.</span></span> <span data-ttu-id="b9ec7-183">Poniżej pokazano przykład definiujący metodę o nazwie **DoSomething**.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-183">The following shows an example of defining a method named **DoSomething**.</span></span>

```powershell
class MyClass
{
    DoSomething($x)
    {
        $this._doSomething($x) # method syntax
    }
    private _doSomething($a) {}
}
```

<span data-ttu-id="b9ec7-184">Wywołanie metody:</span><span class="sxs-lookup"><span data-stu-id="b9ec7-184">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="b9ec7-185">Przeciążone metody są również obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-185">Overloaded methods are also supported.</span></span>

### <a name="properties"></a><span data-ttu-id="b9ec7-186">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b9ec7-186">Properties</span></span>

<span data-ttu-id="b9ec7-187">Wszystkie właściwości są publiczne.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-187">All properties are public.</span></span> <span data-ttu-id="b9ec7-188">Właściwości wymagają nowego wiersza lub średnikami.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-188">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="b9ec7-189">Jeśli jest określony żaden typ obiektu, z typem właściwości jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-189">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="b9ec7-190">Właściwości, które są używane atrybuty przekształcania sprawdzania poprawności lub argumentu (takich jak `[ValidateSet("aaa")]`) działają zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-190">Properties that use validation or argument transformation attributes (like `[ValidateSet("aaa")]`) work as expected.</span></span>

### <a name="hidden"></a><span data-ttu-id="b9ec7-191">Ukryte</span><span class="sxs-lookup"><span data-stu-id="b9ec7-191">Hidden</span></span>

<span data-ttu-id="b9ec7-192">Nowe słowo kluczowe `Hidden`, został dodany.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-192">A new keyword, `Hidden`, has been added.</span></span> <span data-ttu-id="b9ec7-193">`Hidden` można zastosować do właściwości i metod (w tym konstruktory).</span><span class="sxs-lookup"><span data-stu-id="b9ec7-193">`Hidden` can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="b9ec7-194">Ukryte elementy członkowskie są publiczne, ale nie są wyświetlane w danych wyjściowych `Get-Member` chyba że `-Force` zostanie dodany parametr.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-194">Hidden members are public, but do not appear in the output of `Get-Member` unless the `-Force` parameter is added.</span></span> <span data-ttu-id="b9ec7-195">Ukryte elementy członkowskie nie są uwzględniane podczas karcie ukończenie lub za pomocą funkcji Intellisense, chyba że zakończenia wystąpi w klasie Definiowanie ukrytej składowej.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-195">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="b9ec7-196">Nowy atrybut **System.Management.Automation.HiddenAttribute** został dodany tak że C\# kod może mieć tej samej semantyki w ramach programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-196">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C\# code can have the same semantics within PowerShell.</span></span>

### <a name="return-types"></a><span data-ttu-id="b9ec7-197">Typy zwracane</span><span class="sxs-lookup"><span data-stu-id="b9ec7-197">Return types</span></span>

<span data-ttu-id="b9ec7-198">Typ zwracany jest kontraktu.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-198">Return type is a contract.</span></span> <span data-ttu-id="b9ec7-199">Wartość zwracana jest konwertowana do oczekiwanego typu.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-199">The return value is converted to the expected type.</span></span> <span data-ttu-id="b9ec7-200">Jeśli żaden typ zwracany jest określony, zwracany typ jest **void**.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-200">If no return type is specified, the return type is **void**.</span></span> <span data-ttu-id="b9ec7-201">Nie ma żadnych przesyłania strumieniowego obiektów.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-201">There is no streaming of objects.</span></span> <span data-ttu-id="b9ec7-202">Nie można zapisać obiekty do potoku, celowo lub przypadkowo.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-202">Objects cannot be written to the pipeline either intentionally or by accident.</span></span>

### <a name="attributes"></a><span data-ttu-id="b9ec7-203">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b9ec7-203">Attributes</span></span>

<span data-ttu-id="b9ec7-204">Dwa nowe atrybuty, **DscResource** i **DscProperty** zostały dodane.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-204">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

### <a name="lexical-scoping-of-variables"></a><span data-ttu-id="b9ec7-205">Wyznaczanie zakresu leksykalne zmiennych</span><span class="sxs-lookup"><span data-stu-id="b9ec7-205">Lexical scoping of variables</span></span>

<span data-ttu-id="b9ec7-206">Poniżej przedstawiono przykładowy sposób leksykalne zakresu działa w tej wersji.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-206">The following shows an example of how lexical scoping works in this release.</span></span>

```powershell
$d = 42 # Script scope

function bar
{
    $d = 0 # Function scope
    [MyClass]::DoSomething()
}

class MyClass
{
    static [object] DoSomething()
    {
        return $d # error, not found dynamically
        return $script:d # no error
        $d = $script:d
        return $d # no error, found lexically
    }
}

$v = bar
$v -eq $d # true
```

## <a name="end-to-end-example"></a><span data-ttu-id="b9ec7-207">Przykład end-to-End</span><span class="sxs-lookup"><span data-stu-id="b9ec7-207">End-to-End Example</span></span>

<span data-ttu-id="b9ec7-208">Poniższy przykład tworzy niektórych klas niestandardowych do zaimplementowania HTML dynamiczne stylu arkusza język (DSL).</span><span class="sxs-lookup"><span data-stu-id="b9ec7-208">The following example creates some custom classes to implement an HTML dynamic style sheet language (DSL).</span></span> <span data-ttu-id="b9ec7-209">Następnie w przykładzie dodano funkcji pomocnika, aby utworzyć typy określonego elementu jako część klasy elementów, takich jak style nagłówków i tabel, ponieważ nie można używać typów poza zakresem modułu.</span><span class="sxs-lookup"><span data-stu-id="b9ec7-209">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

```powershell
# Classes that define the structure of the document
#
class Html
{
    [string] $docType
    [HtmlHead] $Head
    [Element[]] $Body

    [string] Render()
    {
        $text = "<html>`n<head>`n"
        $text += $this.Head
        $text += "`n</head>`n<body>`n"
        $text += $this.Body -join "`n" # Render all of the body elements
        $text += "</body>`n</html>"
        return $text
    }
    [string] ToString() { return $this.Render() }
}

class HtmlHead
{
    $Title
    $Base
    $Link
    $Style
    $Meta
    $Script
    [string] Render() { return "<title>$($this.Title)</title>" }
    [string] ToString() { return $this.Render() }
}

class Element
{
    [string] $Tag
    [string] $Text
    [hashtable] $Attributes
    [string] Render() {
        $attributesText= ""
        if ($this.Attributes)
        {
            foreach ($attr in $this.Attributes.Keys)
            {
                #BUGBUG - need to validate keys against attribute
                $attributesText += " $attr=`"$($this.Attributes[$attr])\`""
            }
        }
        return "<$($this.tag)${attributesText}>$($this.text)</$($this.tag)>`n"
    }
[string] ToString() { return $this.Render() }
}

#
# Helper functions for creating specific element types on top of the classes.
# These are required because types aren't visible outside of the module.
#

function H1 { [Element] @{ Tag = "H1" ; Text = $args.foreach{$_} -join " " }}
function H2 { [Element] @{ Tag = "H2" ; Text = $args.foreach{$_} -join " " }}
function H3 { [Element] @{ Tag = "H3" ; Text = $args.foreach{$_} -join " " }}
function P { [Element] @{ Tag = "P" ; Text = $args.foreach{$_} -join " " }}
function B { [Element] @{ Tag = "B" ; Text = $args.foreach{$_} -join " " }}
function I { [Element] @{ Tag = "I" ; Text = $args.foreach{$_} -join " " }}
function HREF
{
    param (
        $Name,
        $Link
    )
    return [Element] @{
        Tag = "A"
        Attributes = @{ HREF = $link }
        Text = $name
    }
}
function Table
{
    param (
    [Parameter(Mandatory)]
    [object[]]
        $Data,
    [Parameter()]
    [string[]]
        $Properties = "*",
    [Parameter()]
    [hashtable]
        $Attributes = @{ border=2; cellpadding=2; cellspacing=2 }
    )
$bodyText = ""
# Add the header tags
$bodyText += $Properties.foreach{TH $_}
# Add the rows
$bodyText += foreach ($row in $Data)
    {
        TR (-join $Properties.Foreach{ TD ($row.$_) } )
    }

    $table = [Element] @{
        Tag = "Table"
        Attributes = $Attributes
        Text = $bodyText
    }
$table
}
function TH { ([Element] @{ Tag = "TH" ; Text = $args.foreach{$_} -join " " }) }
function TR { ([Element] @{ Tag = "TR" ; Text = $args.foreach{$_} -join " " }) }
function TD { ([Element] @{ Tag = "TD" ; Text = $args.foreach{$_} -join " " }) }
function Style

{
    return [Element] @{
        Tag = "style"
        Text = "$args"
    }
}

# Takes a hash table, casts it to and HTML document
# and then returns the resulting type.
#
function Html ([HTML] $doc) { return $doc }
```
