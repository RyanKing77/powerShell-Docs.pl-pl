---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a96a4a58dafa01fb43f5bdffb52ef833816148e7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688476"
---
# <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="c142a-102">Nowe funkcje języka, w programie PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c142a-102">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="c142a-103">PowerShell 5.0 wprowadzono następujące nowe elementy języka w programie Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c142a-103">PowerShell 5.0 introduces the following new language elements in Windows PowerShell:</span></span>

## <a name="class-keyword"></a><span data-ttu-id="c142a-104">Class — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="c142a-104">Class keyword</span></span>

<span data-ttu-id="c142a-105">**Klasy** — słowo kluczowe definiuje nową klasę.</span><span class="sxs-lookup"><span data-stu-id="c142a-105">The **class** keyword defines a new class.</span></span> <span data-ttu-id="c142a-106">Jest to PRAWDA typ .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c142a-106">This is a true .NET Framework type.</span></span>
<span data-ttu-id="c142a-107">Elementy członkowskie klasy są publiczne, ale tylko publiczne w zakresie modułu.</span><span class="sxs-lookup"><span data-stu-id="c142a-107">Class members are public, but only public within the module scope.</span></span>
<span data-ttu-id="c142a-108">Nie można odwołać się do nazwy typu jako ciąg (na przykład `New-Object` nie działa), w tej wersji, ale nie można użyć literału typu (na przykład `[MyClass]`) poza plikiem skryptu/modułu, w którym klasa jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="c142a-108">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script/module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="c142a-109">Enum — słowo kluczowe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c142a-109">Enum keyword and enumerations</span></span>

<span data-ttu-id="c142a-110">Obsługa **wyliczenia** — słowo kluczowe zostały dodane, który używa nowego wiersza jako ogranicznika.</span><span class="sxs-lookup"><span data-stu-id="c142a-110">Support for the **enum** keyword has been added, which uses newline as the delimiter.</span></span>
<span data-ttu-id="c142a-111">Bieżące ograniczenia: nie można zdefiniować moduł wyliczający pod względem samego, ale można zainicjować wyliczenia pod względem innego typu wyliczeniowego, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c142a-111">Current limitations: you cannot define an enumerator in terms of itself, but you can initialize an enum in terms of another enum, as shown in the following example.</span></span>
<span data-ttu-id="c142a-112">Ponadto nie można aktualnie określone typu podstawowego; zawsze warto też [int].</span><span class="sxs-lookup"><span data-stu-id="c142a-112">Also, the base type cannot currently be specified; it is always [int].</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="c142a-113">Wartość modułu wyliczającego musi być stałą czasu analizy; nie możesz ustawić wyniku wywoływane polecenie.</span><span class="sxs-lookup"><span data-stu-id="c142a-113">An enumerator value must be a parse time constant; you cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="c142a-114">Typy wyliczeniowe obsługują operacje arytmetyczne, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c142a-114">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a><span data-ttu-id="c142a-115">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="c142a-115">Import-DscResource</span></span>

<span data-ttu-id="c142a-116">**Import-DscResource** jest teraz true — słowo kluczowe dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="c142a-116">**Import-DscResource** is now a true dynamic keyword.</span></span>
<span data-ttu-id="c142a-117">Program PowerShell analizuje modułu głównego określonego modułu, Wyszukiwanie klas, które zawierają **DscResource** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c142a-117">PowerShell parses the specified module’s root module, searching for classes that contain the **DscResource** attribute.</span></span>

## <a name="implementingassembly"></a><span data-ttu-id="c142a-118">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="c142a-118">ImplementingAssembly</span></span>

<span data-ttu-id="c142a-119">Nowe pole **ImplementingAssembly**, została dodana do ModuleInfo.</span><span class="sxs-lookup"><span data-stu-id="c142a-119">A new field, **ImplementingAssembly**, has been added to ModuleInfo.</span></span> <span data-ttu-id="c142a-120">Ustawiono się do zestawu dynamicznego utworzony dla modułu skryptu, jeśli skrypt definiuje klasy lub załadować zestawu dla moduły binarne.</span><span class="sxs-lookup"><span data-stu-id="c142a-120">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="c142a-121">Nie jest ustawiona podczas ModuleType = manifestu.</span><span class="sxs-lookup"><span data-stu-id="c142a-121">It is not set when ModuleType = Manifest.</span></span>

<span data-ttu-id="c142a-122">Rozważania na temat **ImplementingAssembly** pola odnalezieniu zasobów w module.</span><span class="sxs-lookup"><span data-stu-id="c142a-122">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="c142a-123">Oznacza to, że można odnajdywać zasoby napisane w programie PowerShell lub innych języków zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="c142a-123">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="c142a-124">Pola z inicjatorami:</span><span class="sxs-lookup"><span data-stu-id="c142a-124">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="c142a-125">Statyczna jest obsługiwana; działa podobnie jak atrybut, tak jak ograniczenia typu, dzięki czemu mogą być podane w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="c142a-125">Static is supported; it works like an attribute, as do the type constraints, so it can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="c142a-126">Typem jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="c142a-126">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="c142a-127">Wszystkie elementy członkowskie są publiczne.</span><span class="sxs-lookup"><span data-stu-id="c142a-127">All members are public.</span></span>

## <a name="constructors-and-instantiation"></a><span data-ttu-id="c142a-128">Konstruktory i wystąpienia</span><span class="sxs-lookup"><span data-stu-id="c142a-128">Constructors and instantiation</span></span>

<span data-ttu-id="c142a-129">Klasy programu Windows PowerShell, mogą mieć konstruktorów; mają one taką samą nazwę jak ich klasy.</span><span class="sxs-lookup"><span data-stu-id="c142a-129">Windows PowerShell classes can have constructors; they have the same name as their class.</span></span> <span data-ttu-id="c142a-130">Mogą być przeciążone konstruktory.</span><span class="sxs-lookup"><span data-stu-id="c142a-130">Constructors can be overloaded.</span></span> <span data-ttu-id="c142a-131">Konstruktory statyczne są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c142a-131">Static constructors are supported.</span></span> <span data-ttu-id="c142a-132">Właściwości za pomocą wyrażenia inicjowania są inicjowane przed uruchomieniem jakiegokolwiek kodu w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="c142a-132">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="c142a-133">Właściwości statyczne są inicjowane przed treści statyczny Konstruktor i właściwości wystąpienia są inicjowane przed treść konstruktora niestatycznych.</span><span class="sxs-lookup"><span data-stu-id="c142a-133">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="c142a-134">Obecnie nie ma żadnych składnia wywoływania konstruktora od innego konstruktora (takich jak C\# składni ": this()").</span><span class="sxs-lookup"><span data-stu-id="c142a-134">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="c142a-135">Obejście polega na definiowanie typowe metody Init.</span><span class="sxs-lookup"><span data-stu-id="c142a-135">The workaround is to define a common Init method.</span></span>

<span data-ttu-id="c142a-136">Poniżej przedstawiono sposób tworzenia wystąpienia klasy w tej wersji.</span><span class="sxs-lookup"><span data-stu-id="c142a-136">The following are ways of instantiating classes in this release.</span></span>

<span data-ttu-id="c142a-137">Utworzenie wystąpienia przy użyciu domyślnego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="c142a-137">Instantiating by using the default constructor.</span></span> <span data-ttu-id="c142a-138">Należy pamiętać, że nowy obiekt nie jest obsługiwany w tej wersji.</span><span class="sxs-lookup"><span data-stu-id="c142a-138">Note that New-Object is not supported in this release.</span></span>

```powershell
$a = [MyClass]::new()
```

<span data-ttu-id="c142a-139">Wywołanie konstruktora z parametrem</span><span class="sxs-lookup"><span data-stu-id="c142a-139">Calling a constructor with a parameter</span></span>

```powershell
$b = [MyClass]::new(42)
```

<span data-ttu-id="c142a-140">Przekazywanie tablicę do konstruktora z wieloma parametrami</span><span class="sxs-lookup"><span data-stu-id="c142a-140">Passing an array to a constructor with multiple parameters</span></span>
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

<span data-ttu-id="c142a-141">W tej wersji New-Object nie działa z klas zdefiniowanych w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c142a-141">In this release, New-Object does not work with classes defined in Windows PowerShell.</span></span> <span data-ttu-id="c142a-142">Również w tej wersji, nazwa typu jest tylko widoczne leksykalnie, co oznacza, że nie jest widoczne na zewnątrz modułu lub skryptu, który definiuje klasę.</span><span class="sxs-lookup"><span data-stu-id="c142a-142">Also for this release, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="c142a-143">Funkcje mogą zwracać wystąpienia klasy zdefiniowanej w programie Windows PowerShell, a wystąpienia działają dobrze, poza modułu lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="c142a-143">Functions can return instances of a class defined in Windows PowerShell, and instances work well outside of the module or script.</span></span>

<span data-ttu-id="c142a-144">`Get-Member -Static` Wyświetla listę konstruktorów, aby można było wyświetlić przeciążenia, jak każda inna metoda.</span><span class="sxs-lookup"><span data-stu-id="c142a-144">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="c142a-145">Wydajność tej składni jest również znacznie szybsze niż New-Object.</span><span class="sxs-lookup"><span data-stu-id="c142a-145">The performance of this syntax is also considerably faster than New-Object.</span></span>

<span data-ttu-id="c142a-146">Pseudolosowego statyczną metodę o nazwie **nowe** działa z typami .NET, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c142a-146">The pseudo-static method named **new** works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

<span data-ttu-id="c142a-147">Teraz widać przeciążeń konstruktora, Get-Member lub zgodnie z informacjami w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c142a-147">You can now see constructor overloads with Get-Member, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a><span data-ttu-id="c142a-148">Metody</span><span class="sxs-lookup"><span data-stu-id="c142a-148">Methods</span></span>

<span data-ttu-id="c142a-149">Metoda klasy środowiska Windows PowerShell jest implementowany jako blok skryptu, który zawiera blok końcowy.</span><span class="sxs-lookup"><span data-stu-id="c142a-149">A Windows PowerShell class method is implemented as a ScriptBlock that has only an end block.</span></span> <span data-ttu-id="c142a-150">Wszystkie metody są publiczne.</span><span class="sxs-lookup"><span data-stu-id="c142a-150">All methods are public.</span></span> <span data-ttu-id="c142a-151">Poniżej pokazano przykład definiujący metodę o nazwie **DoSomething**.</span><span class="sxs-lookup"><span data-stu-id="c142a-151">The following shows an example of defining a method named **DoSomething**.</span></span>

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

<span data-ttu-id="c142a-152">Wywołanie metody:</span><span class="sxs-lookup"><span data-stu-id="c142a-152">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="c142a-153">Przeciążone metody — czyli tych, które są w samej nazwie jak istniejącą metodę, ale zróżnicowane według określonej wartości — także są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c142a-153">Overloaded methods--that is, those that are named the same as an existing method, but differentiated by their specified values--are also supported.</span></span>

## <a name="properties"></a><span data-ttu-id="c142a-154">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c142a-154">Properties</span></span>

<span data-ttu-id="c142a-155">Wszystkie właściwości są publiczne.</span><span class="sxs-lookup"><span data-stu-id="c142a-155">All properties are public.</span></span> <span data-ttu-id="c142a-156">Właściwości wymagają nowego wiersza lub średnikami.</span><span class="sxs-lookup"><span data-stu-id="c142a-156">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="c142a-157">Jeśli jest określony żaden typ obiektu, z typem właściwości jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="c142a-157">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="c142a-158">Właściwości, które za pomocą atrybutów sprawdzania poprawności lub argument przekształcania atrybuty (np. `[ValidateSet("aaa")]`) działają zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="c142a-158">Properties that use validation attributes or argument transformation attributes (e.g. `[ValidateSet("aaa")]`) work as expected.</span></span>

## <a name="hidden"></a><span data-ttu-id="c142a-159">Ukryte</span><span class="sxs-lookup"><span data-stu-id="c142a-159">Hidden</span></span>

<span data-ttu-id="c142a-160">Nowe słowo kluczowe **ukryty**, został dodany.</span><span class="sxs-lookup"><span data-stu-id="c142a-160">A new keyword, **Hidden**, has been added.</span></span> <span data-ttu-id="c142a-161">**Ukryte** mogą być stosowane do właściwości i metody (w tym konstruktory).</span><span class="sxs-lookup"><span data-stu-id="c142a-161">**Hidden** can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="c142a-162">Ukryte elementy członkowskie są publiczne, ale nie są wyświetlane w danych wyjściowych Get-Member chyba że Force, zostanie dodany parametr.</span><span class="sxs-lookup"><span data-stu-id="c142a-162">Hidden members are public, but do not appear in the output of Get-Member unless the -Force parameter is added.</span></span>

<span data-ttu-id="c142a-163">Ukryte elementy członkowskie nie są uwzględniane podczas karcie ukończenie lub za pomocą funkcji Intellisense, chyba że zakończenia wystąpi w klasie Definiowanie ukrytej składowej.</span><span class="sxs-lookup"><span data-stu-id="c142a-163">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="c142a-164">Nowy atrybut **System.Management.Automation.HiddenAttribute** dodano, dzięki czemu kod C# może mieć tej samej semantyki w ramach programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c142a-164">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C# code can have the same semantics within Windows PowerShell.</span></span>

## <a name="return-types"></a><span data-ttu-id="c142a-165">Typy zwracane</span><span class="sxs-lookup"><span data-stu-id="c142a-165">Return types</span></span>

<span data-ttu-id="c142a-166">Typ zwracany jest Umowa; Wartość zwracana jest konwertowana do oczekiwanego typu.</span><span class="sxs-lookup"><span data-stu-id="c142a-166">Return type is a contract; the return value is converted to the expected type.</span></span> <span data-ttu-id="c142a-167">Jeśli żaden typ zwracany jest określony, zwracany typ jest typ void.</span><span class="sxs-lookup"><span data-stu-id="c142a-167">If no return type is specified, the return type is void.</span></span> <span data-ttu-id="c142a-168">Istnieje nie przesyłania strumieniowego obiektów; Nie można zapisać obiekty do potoku, celowo lub przypadkowo.</span><span class="sxs-lookup"><span data-stu-id="c142a-168">There is no streaming of objects; objects cannot be written to the pipeline either intentionally or by accident.</span></span>

## <a name="attributes"></a><span data-ttu-id="c142a-169">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c142a-169">Attributes</span></span>

<span data-ttu-id="c142a-170">Dwa nowe atrybuty, **DscResource** i **DscProperty** zostały dodane.</span><span class="sxs-lookup"><span data-stu-id="c142a-170">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

## <a name="lexical-scoping-of-variables"></a><span data-ttu-id="c142a-171">Wyznaczanie zakresu leksykalne zmiennych</span><span class="sxs-lookup"><span data-stu-id="c142a-171">Lexical scoping of variables</span></span>

<span data-ttu-id="c142a-172">Poniżej przedstawiono przykładowy sposób leksykalne zakresu działa w tej wersji.</span><span class="sxs-lookup"><span data-stu-id="c142a-172">The following shows an example of how lexical scoping works in this release.</span></span>

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

## <a name="end-to-end-example"></a><span data-ttu-id="c142a-173">Przykład end-to-End</span><span class="sxs-lookup"><span data-stu-id="c142a-173">End-to-End Example</span></span>

<span data-ttu-id="c142a-174">Poniższy przykład tworzy kilka nowych, niestandardowych klas do zaimplementowania HTML dynamiczne stylu arkusza język (DSL).</span><span class="sxs-lookup"><span data-stu-id="c142a-174">The following example creates several new, custom classes to implement an HTML dynamic style sheet language (DSL).</span></span>
<span data-ttu-id="c142a-175">Następnie w przykładzie dodano funkcji pomocnika, aby utworzyć typy określonego elementu jako część klasy elementów, takich jak style nagłówków i tabel, ponieważ nie można używać typów poza zakresem modułu.</span><span class="sxs-lookup"><span data-stu-id="c142a-175">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

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
# These are required because types aren’t visible outside of the module.
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
