---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 85e9206ffef76fb4bd7714d847888e6e5bbcc4ec
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="new-language-features-in-powershell-50"></a>Nowe funkcje językowe w programie PowerShell 5.0

PowerShell 5.0 wprowadzono następujące nowe elementy języka w programie Windows PowerShell:

## <a name="class-keyword"></a>Class — słowo kluczowe

**Klasy** — słowo kluczowe definiuje nową klasę. Jest to PRAWDA typu .NET Framework.
Elementy członkowskie klasy są publiczne, ale tylko publicznej w zakresie modułu.
Nie można znaleźć nazwy typu jako ciąg (na przykład `New-Object` nie działa), a w tej wersji, nie można użyć literału typu (na przykład `[MyClass]`) poza plikiem skryptu/modułu, w którym klasa jest zdefiniowana.

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a>Enum — słowo kluczowe i wyliczenia

Obsługa **wyliczenia** dodano — słowo kluczowe, który używa jako ogranicznik nowego wiersza.
Bieżące ograniczenia: nie można zdefiniować moduł wyliczający pod względem samego, ale można zainicjować wyliczenie pod względem innego wyliczenia, jak pokazano w poniższym przykładzie.
Ponadto nie można obecnie określić typu podstawowego; zawsze [int].

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Moduł wyliczający wartość musi być stałą czasu analizy; Nie można go ustawić wynik polecenia wywoływane.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

Typy wyliczeniowe obsługuje operacje arytmetyczne, jak pokazano w poniższym przykładzie.

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a>Import-DscResource

**Import-DscResource** jest teraz true — słowo kluczowe dynamicznych.
PowerShell analizuje określony moduł główny moduł, wyszukiwanie dla klas, które zawierają **DscResource** atrybutu.

## <a name="implementingassembly"></a>ImplementingAssembly

Nowe pole **ImplementingAssembly**, został dodany do ModuleInfo. Zestaw dynamiczny utworzony dla modułu skryptu, jeśli skrypt definiuje klasy lub załadować zestawu dla moduły binarne jest ustawiona. Nie jest ustawiona podczas ModuleType = manifestu.

Odbicie na **ImplementingAssembly** pola umożliwia odnalezienie zasobów w module. Oznacza to, że można odnajdywać zasoby napisane w programie PowerShell lub inne języki zarządzane.

Pola z inicjatorami:

```powershell
[int] $i = 5
```

Statyczna jest obsługiwany; działa jak atrybutu, tak jak ograniczenia typu, dlatego można ją określić w dowolnej kolejności.

```powershell
static [int] $count = 0
```

Typem jest opcjonalna.

```powershell
$s = "hello"
```

Wszystkie elementy członkowskie są publiczne.

## <a name="constructors-and-instantiation"></a>Konstruktory i tworzenie wystąpień

Klasy środowiska Windows PowerShell można mieć konstruktorów; mają one taką samą nazwę jak ich klasy. Konstruktory mogą być przeciążone. Konstruktory statyczne są obsługiwane. Właściwości, za pomocą wyrażeń inicjowania są inicjowane przed uruchomieniem kodu w konstruktorze. Właściwości statyczne są inicjowane przed treści Konstruktor statyczny, a właściwości obiektu są zainicjowane przed treść konstruktora niestatycznego. Obecnie, nie istnieje żadna składnia wywoływania konstruktora od innego konstruktora (takich jak C\# składni ": this()"). Obejście polega na zdefiniować typowe metody Init.

Poniżej przedstawiono sposób tworzenia wystąpienia klasy w tej wersji.

Tworzenie wystąpień przy użyciu domyślnego konstruktora. Należy pamiętać, że nowy obiekt nie jest obsługiwana w tej wersji.

```powershell
$a = [MyClass]::new()
```

Wywołanie konstruktora z parametrem

```powershell
$b = [MyClass]::new(42)
```

Przekazanie tablicy do konstruktora o wiele parametrów
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

W tej wersji New-Object nie działa z klas zdefiniowanych w programie Windows PowerShell. Również w tej wersji, nazwa typu jest tylko widoczne lexically, co oznacza, że nie jest widoczne na zewnątrz modułu lub skrypt, który definiuje klasę. Funkcje może zwrócić wystąpienia klasy zdefiniowanej w programie Windows PowerShell i wystąpień działa dobrze poza modułu lub skryptu.

`Get-Member -Static` Wyświetla listę konstruktorów, dzięki czemu można zobaczyć przeciążenia, takich jak każdą inną metodę. Wydajność tej składni jest również znacznie krócej niż New-Object.

Artykule statyczną metodę o nazwie **nowe** współpracuje z typów .NET, jak pokazano w poniższym przykładzie.

```powershell
[hashtable]::new()
```

Możesz teraz przeglądać przeciążeń konstruktora z elementem członkowskim Get lub przedstawione w tym przykładzie:

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a>Metody

Metoda klasy środowiska Windows PowerShell jest implementowany jako blok skryptu, który ma blok końcowy. Wszystkie metody są publiczne. Poniżej przedstawiono przykład Definiowanie metodę o nazwie **DoSomething**.

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

Przeciążone metody — czyli tych, które są o nazwie takiej jak istniejącą metodę, ale zróżnicowane według określonej wartości — także są obsługiwane.

## <a name="properties"></a>Właściwości

Wszystkie właściwości są publiczne. Właściwości wymagają znaków nowego wiersza ani średnika. Jeśli jest określony żaden typ obiektu, typ właściwości jest obiektem.

Właściwości używających atrybuty weryfikacji lub przekształcania argumentu (np. `[ValidateSet("aaa")]`) działają zgodnie z oczekiwaniami.

## <a name="hidden"></a>Ukryte

New — słowo kluczowe, **Hidden**, został dodany. **Ukryte** może odnosić się do właściwości i metod (łącznie z konstruktorów).

Ukrytych elementów członkowskich są publiczne, ale nie są wyświetlane w danych wyjściowych elementu członkowskiego Get, chyba że Force zostanie dodany parametr.

Ukryte elementy członkowskie nie są uwzględniane podczas karcie Kończenie lub za pomocą funkcji Intellisense, o ile zakończenie występuje w klasie definiowania ukryte elementu członkowskiego.

Nowy atrybut **System.Management.Automation.HiddenAttribute** dodano, dzięki czemu kod w języku C# może mieć tej samej semantyki w programie Windows PowerShell.

## <a name="return-types"></a>Zwracane typy

Zwracany typ jest kontrakt; Wartość zwracana jest konwertowana na typ oczekiwany. Jeśli żaden typ zwracany jest określony, typ zwracany jest typ void. Nie istnieje żadne przesyłania strumieniowego obiektów; Nie można zapisać obiektów do potoku, celowo lub przypadkowo.

## <a name="attributes"></a>Atrybuty

Dwa nowe atrybuty, **DscResource** i **DscProperty** zostały dodane.

## <a name="lexical-scoping-of-variables"></a>Określanie zakresu leksykalne zmiennych

Poniżej przedstawiono przykład sposobu leksykalne zakresu działania w tej wersji.

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

Poniższy przykład tworzy kilka nowych, niestandardowych klasy do zaimplementowania języka arkusza dynamiczne stylu HTML (DSL).
Następnie w przykładzie dodano funkcje pomocnicze do tworzenia typów konkretny element w ramach klasy elementów, takich jak style nagłówków i tabele, ponieważ nie można używać typów poza zakresem modułu.

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
        TR (-join $Properties.Foreach{ TD ($row.$\_) } )
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