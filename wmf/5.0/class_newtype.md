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
# <a name="new-language-features-in-powershell-50"></a>Nowe funkcje języka, w programie PowerShell 5.0

PowerShell 5.0 wprowadzono następujące nowe elementy języka w programie Windows PowerShell:

## <a name="class-keyword"></a>Class — słowo kluczowe

**Klasy** — słowo kluczowe definiuje nową klasę. Jest to PRAWDA typ .NET Framework.
Elementy członkowskie klasy są publiczne, ale tylko publiczne w zakresie modułu.
Nie można odwołać się do nazwy typu jako ciąg (na przykład `New-Object` nie działa), w tej wersji, ale nie można użyć literału typu (na przykład `[MyClass]`) poza plikiem skryptu/modułu, w którym klasa jest zdefiniowana.

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a>Enum — słowo kluczowe i wyliczenia

Obsługa **wyliczenia** — słowo kluczowe zostały dodane, który używa nowego wiersza jako ogranicznika.
Bieżące ograniczenia: nie można zdefiniować moduł wyliczający pod względem samego, ale można zainicjować wyliczenia pod względem innego typu wyliczeniowego, jak pokazano w poniższym przykładzie.
Ponadto nie można aktualnie określone typu podstawowego; zawsze warto też [int].

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Wartość modułu wyliczającego musi być stałą czasu analizy; nie możesz ustawić wyniku wywoływane polecenie.

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

## <a name="import-dscresource"></a>Import-DscResource

**Import-DscResource** jest teraz true — słowo kluczowe dynamicznych.
Program PowerShell analizuje modułu głównego określonego modułu, Wyszukiwanie klas, które zawierają **DscResource** atrybutu.

## <a name="implementingassembly"></a>ImplementingAssembly

Nowe pole **ImplementingAssembly**, została dodana do ModuleInfo. Ustawiono się do zestawu dynamicznego utworzony dla modułu skryptu, jeśli skrypt definiuje klasy lub załadować zestawu dla moduły binarne. Nie jest ustawiona podczas ModuleType = manifestu.

Rozważania na temat **ImplementingAssembly** pola odnalezieniu zasobów w module. Oznacza to, że można odnajdywać zasoby napisane w programie PowerShell lub innych języków zarządzanych.

Pola z inicjatorami:

```powershell
[int] $i = 5
```

Statyczna jest obsługiwana; działa podobnie jak atrybut, tak jak ograniczenia typu, dzięki czemu mogą być podane w dowolnej kolejności.

```powershell
static [int] $count = 0
```

Typem jest opcjonalna.

```powershell
$s = "hello"
```

Wszystkie elementy członkowskie są publiczne.

## <a name="constructors-and-instantiation"></a>Konstruktory i wystąpienia

Klasy programu Windows PowerShell, mogą mieć konstruktorów; mają one taką samą nazwę jak ich klasy. Mogą być przeciążone konstruktory. Konstruktory statyczne są obsługiwane. Właściwości za pomocą wyrażenia inicjowania są inicjowane przed uruchomieniem jakiegokolwiek kodu w konstruktorze. Właściwości statyczne są inicjowane przed treści statyczny Konstruktor i właściwości wystąpienia są inicjowane przed treść konstruktora niestatycznych. Obecnie nie ma żadnych składnia wywoływania konstruktora od innego konstruktora (takich jak C\# składni ": this()"). Obejście polega na definiowanie typowe metody Init.

Poniżej przedstawiono sposób tworzenia wystąpienia klasy w tej wersji.

Utworzenie wystąpienia przy użyciu domyślnego konstruktora. Należy pamiętać, że nowy obiekt nie jest obsługiwany w tej wersji.

```powershell
$a = [MyClass]::new()
```

Wywołanie konstruktora z parametrem

```powershell
$b = [MyClass]::new(42)
```

Przekazywanie tablicę do konstruktora z wieloma parametrami
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

W tej wersji New-Object nie działa z klas zdefiniowanych w programie Windows PowerShell. Również w tej wersji, nazwa typu jest tylko widoczne leksykalnie, co oznacza, że nie jest widoczne na zewnątrz modułu lub skryptu, który definiuje klasę. Funkcje mogą zwracać wystąpienia klasy zdefiniowanej w programie Windows PowerShell, a wystąpienia działają dobrze, poza modułu lub skryptu.

`Get-Member -Static` Wyświetla listę konstruktorów, aby można było wyświetlić przeciążenia, jak każda inna metoda. Wydajność tej składni jest również znacznie szybsze niż New-Object.

Pseudolosowego statyczną metodę o nazwie **nowe** działa z typami .NET, jak pokazano w poniższym przykładzie.

```powershell
[hashtable]::new()
```

Teraz widać przeciążeń konstruktora, Get-Member lub zgodnie z informacjami w tym przykładzie:

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a>Metody

Metoda klasy środowiska Windows PowerShell jest implementowany jako blok skryptu, który zawiera blok końcowy. Wszystkie metody są publiczne. Poniżej pokazano przykład definiujący metodę o nazwie **DoSomething**.

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

Przeciążone metody — czyli tych, które są w samej nazwie jak istniejącą metodę, ale zróżnicowane według określonej wartości — także są obsługiwane.

## <a name="properties"></a>Właściwości

Wszystkie właściwości są publiczne. Właściwości wymagają nowego wiersza lub średnikami. Jeśli jest określony żaden typ obiektu, z typem właściwości jest obiektem.

Właściwości, które za pomocą atrybutów sprawdzania poprawności lub argument przekształcania atrybuty (np. `[ValidateSet("aaa")]`) działają zgodnie z oczekiwaniami.

## <a name="hidden"></a>Ukryte

Nowe słowo kluczowe **ukryty**, został dodany. **Ukryte** mogą być stosowane do właściwości i metody (w tym konstruktory).

Ukryte elementy członkowskie są publiczne, ale nie są wyświetlane w danych wyjściowych Get-Member chyba że Force, zostanie dodany parametr.

Ukryte elementy członkowskie nie są uwzględniane podczas karcie ukończenie lub za pomocą funkcji Intellisense, chyba że zakończenia wystąpi w klasie Definiowanie ukrytej składowej.

Nowy atrybut **System.Management.Automation.HiddenAttribute** dodano, dzięki czemu kod C# może mieć tej samej semantyki w ramach programu Windows PowerShell.

## <a name="return-types"></a>Typy zwracane

Typ zwracany jest Umowa; Wartość zwracana jest konwertowana do oczekiwanego typu. Jeśli żaden typ zwracany jest określony, zwracany typ jest typ void. Istnieje nie przesyłania strumieniowego obiektów; Nie można zapisać obiekty do potoku, celowo lub przypadkowo.

## <a name="attributes"></a>Atrybuty

Dwa nowe atrybuty, **DscResource** i **DscProperty** zostały dodane.

## <a name="lexical-scoping-of-variables"></a>Wyznaczanie zakresu leksykalne zmiennych

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

Poniższy przykład tworzy kilka nowych, niestandardowych klas do zaimplementowania HTML dynamiczne stylu arkusza język (DSL).
Następnie w przykładzie dodano funkcji pomocnika, aby utworzyć typy określonego elementu jako część klasy elementów, takich jak style nagłówków i tabel, ponieważ nie można używać typów poza zakresem modułu.

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
