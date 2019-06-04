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
# <a name="creating-custom-types-using-powershell-classes"></a>Tworzenie typów niestandardowych przy użyciu klas programu PowerShell

PowerShell 5.0 dodano możliwość definiowania klas i innych typów zdefiniowanych przez użytkownika za pomocą formalne składnia i semantyka, takich jak innych języków programowania obiektowego. Celem jest umożliwienie deweloperom i informatykom przyjęcie programu PowerShell dla szerszego zakresu zastosowań, upraszczają proces tworzenia artefaktów programu PowerShell (takich jak zasoby DSC) oraz skrócenia procesu pokrycia powierzchni zarządzania.

## <a name="supported-scenarios-in-this-release"></a>Scenariusze obsługiwane w tej wersji

- Zdefiniuj zasoby DSC i ich skojarzone typy przy użyciu języka programu PowerShell
- Definiowanie typów niestandardowych w programie PowerShell, za pomocą dobrze znanych zorientowane obiektowo narzędzi programistycznych, takich jak klasy, właściwości, metod itd.
- Obsługa dziedziczenia z klasy w podstawowej zasobów DSC programu PowerShell i klasy
- Debugowanie typów przy użyciu języka programu PowerShell
- Generowanie i obsługa wyjątków za pomocą mechanizmów formalne i na właściwym poziomie

## <a name="declare-base-class"></a>Deklarowanie klasy bazowej

Klasa programu PowerShell można zadeklarować jako typ podstawowy dla innej klasy programu PowerShell.

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

Można również użyć istniejących typów programu .NET Framework jako klay bazowe:

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

### <a name="call-base-class-constructor"></a>Wywoływanie konstruktora klasy bazowej

Aby wywołać konstruktora klasy bazowej z podklasy, należy użyć słowa kluczowego **podstawowy**:

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

Jeśli klasa bazowa ma Konstruktor domyślny (nie parametrów), można pominąć wywołanie jawny Konstruktor:

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-method"></a>Wywoływanie metody klasy bazowej

Można zastąpić istniejących metod w podklasach. Aby to zrobić, należy zadeklarować metody przy użyciu tej samej nazwie i sygnaturze:

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

Aby wywołać metody klasy bazowej z implementacji zastąpione, rzutowanie do klasy bazowej (`[baseClass]$this`) na wywołania:

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

Wszystkie metody programu PowerShell są wirtualne. Można ukryć .NET metod niewirtualnych w podklasę przy użyciu tej samej składni, tak jak w przypadku zastąpienia, przez zadeklarowanie metody o tej samej nazwie i sygnaturze.

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

### <a name="declare-implemented-interface"></a>Deklarowanie zaimplementowanego interfejsu

Możesz zadeklarować implementowane interfejsy po typy podstawowe lub od razu po dwukropek (:), jeśli bez określonego typu podstawowego. Oddziel nazwy wszystkich typów za pomocą przecinków. Jest on podobny do C# składni.

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

## <a name="new-language-features-in-powershell-50"></a>Nowe funkcje języka, w programie PowerShell 5.0

PowerShell 5.0 wprowadzono następujące nowe elementy języka w programie PowerShell:

### <a name="class-keyword"></a>Class — słowo kluczowe

`class` — Słowo kluczowe definiuje nową klasę. Jest to PRAWDA typ .NET Framework. Elementy członkowskie klasy są publiczne, ale tylko publiczne w zakresie modułu. Nie można odwołać się do nazwy typu jako ciąg (na przykład `New-Object` nie działa), w tej wersji, ale nie można użyć literału typu (na przykład `[MyClass]`) poza plikiem skryptu lub moduł, w którym klasa jest zdefiniowana.

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a>Enum — słowo kluczowe i wyliczenia

Obsługa `enum` — słowo kluczowe zostały dodane, który używa nowego wiersza jako ogranicznika. Obecnie nie można zdefiniować moduł wyliczający pod względem samego. Jednak należy zainicjować wyliczenia pod względem innego typu wyliczeniowego, jak pokazano w poniższym przykładzie. Ponadto nie można określić typu podstawowego; zawsze warto też `[int]`.

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Wartość modułu wyliczającego musi być stałą czasu analizy. Nie możesz ustawić wyniku wywoływane polecenie.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

Typy wyliczeniowe obsługują operacje arytmetyczne, jak pokazano w poniższym przykładzie.

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a>Import-DscResource

`Import-DscResource` jest teraz true — słowo kluczowe dynamicznych. Program PowerShell analizuje modułu głównego określonego modułu, Wyszukiwanie klas, które zawierają **DscResource** atrybutu.

### <a name="implementingassembly"></a>ImplementingAssembly

Nowe pole **ImplementingAssembly**, została dodana do **ModuleInfo**. Ustawiono się do zestawu dynamicznego utworzony dla modułu skryptu, jeśli skrypt definiuje klasy lub załadować zestawu dla moduły binarne. Nie jest ustawiona podczas **ModuleType** jest **manifestu**.

Rozważania na temat **ImplementingAssembly** pola odnalezieniu zasobów w module. Oznacza to, że można odnajdywać zasoby napisane w programie PowerShell lub innych języków zarządzanych.

Pola z inicjatorami:

```powershell
[int] $i = 5
```

`Static` jest obsługiwany. Działa podobnie jak atrybut, jak to ma ograniczenia typu. Mogą być podane w dowolnej kolejności.

```powershell
static [int] $count = 0
```

Typem jest opcjonalna.

```powershell
$s = "hello"
```

Wszystkie elementy członkowskie są publiczne.

### <a name="constructors-and-instantiation"></a>Konstruktory i wystąpienia

Klas programu PowerShell mogą mieć konstruktorów. Mają one taką samą nazwę jak ich klasy. Mogą być przeciążone konstruktory. Konstruktory statyczne są obsługiwane. Właściwości za pomocą wyrażenia inicjowania są inicjowane przed uruchomieniem jakiegokolwiek kodu w konstruktorze. Właściwości statyczne są inicjowane przed treści statyczny Konstruktor i właściwości wystąpienia są inicjowane przed treść konstruktora niestatycznych. Obecnie nie ma żadnych składnia wywoływania konstruktora od innego konstruktora (takich jak C\# składni ": this()"). Obejście polega na zdefiniowaniu często `Init()` metody.

#### <a name="creating-instances"></a>Tworzenie instancji

> [!NOTE]
> W programie PowerShell w wersji 5.0 `New-Object` nie działa z klas zdefiniowanych w programie PowerShell. Ponadto nazwa typu jest tylko widoczne leksykalnie, co oznacza, że nie jest widoczne na zewnątrz modułu lub skryptu, który definiuje klasę. Funkcje mogą zwracać wystąpienia klasy zdefiniowanej w programie PowerShell. Te wystąpienia działają poza modułu lub skryptu.

1. Utworzenie wystąpienia przy użyciu domyślnego konstruktora.

   ```powershell
   $a = [MyClass]::new()
   ```

1. Wywołanie konstruktora z parametrem

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. Przekazywanie tablicę do konstruktora z wieloma parametrami.

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

Pseudolosowego statycznej metody `new()` działa z typami .NET, jak pokazano w poniższym przykładzie.

```powershell
[hashtable]::new()
```

#### <a name="discovering-constructors"></a>Odnajdywanie konstruktorów

Teraz możesz wyświetlać przeciążeń konstruktora z `Get-Member`, lub jak pokazano w poniższym przykładzie:

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

`Get-Member -Static` Wyświetla listę konstruktorów, aby można było wyświetlić przeciążenia, jak każda inna metoda. Wydajność tej składni jest również znacznie szybsze niż `New-Object`.

### <a name="methods"></a>Metody

Metoda klasy programu PowerShell jest implementowany jako **ScriptBlock** zawierający tylko blok końcowy. Wszystkie metody są publiczne. Poniżej pokazano przykład definiujący metodę o nazwie **DoSomething**.

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

Wywołanie metody:

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

Przeciążone metody są również obsługiwane.

### <a name="properties"></a>Właściwości

Wszystkie właściwości są publiczne. Właściwości wymagają nowego wiersza lub średnikami. Jeśli jest określony żaden typ obiektu, z typem właściwości jest obiektem.

Właściwości, które są używane atrybuty przekształcania sprawdzania poprawności lub argumentu (takich jak `[ValidateSet("aaa")]`) działają zgodnie z oczekiwaniami.

### <a name="hidden"></a>Ukryte

Nowe słowo kluczowe `Hidden`, został dodany. `Hidden` można zastosować do właściwości i metod (w tym konstruktory).

Ukryte elementy członkowskie są publiczne, ale nie są wyświetlane w danych wyjściowych `Get-Member` chyba że `-Force` zostanie dodany parametr. Ukryte elementy członkowskie nie są uwzględniane podczas karcie ukończenie lub za pomocą funkcji Intellisense, chyba że zakończenia wystąpi w klasie Definiowanie ukrytej składowej.

Nowy atrybut **System.Management.Automation.HiddenAttribute** został dodany tak że C\# kod może mieć tej samej semantyki w ramach programu PowerShell.

### <a name="return-types"></a>Typy zwracane

Typ zwracany jest kontraktu. Wartość zwracana jest konwertowana do oczekiwanego typu. Jeśli żaden typ zwracany jest określony, zwracany typ jest **void**. Nie ma żadnych przesyłania strumieniowego obiektów. Nie można zapisać obiekty do potoku, celowo lub przypadkowo.

### <a name="attributes"></a>Atrybuty

Dwa nowe atrybuty, **DscResource** i **DscProperty** zostały dodane.

### <a name="lexical-scoping-of-variables"></a>Wyznaczanie zakresu leksykalne zmiennych

Poniżej przedstawiono przykładowy sposób leksykalne zakresu działa w tej wersji.

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

## <a name="end-to-end-example"></a>Przykład end-to-End

Poniższy przykład tworzy niektórych klas niestandardowych do zaimplementowania HTML dynamiczne stylu arkusza język (DSL). Następnie w przykładzie dodano funkcji pomocnika, aby utworzyć typy określonego elementu jako część klasy elementów, takich jak style nagłówków i tabel, ponieważ nie można używać typów poza zakresem modułu.

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
