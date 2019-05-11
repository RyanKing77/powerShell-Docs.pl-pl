---
title: Jak napisać Manifest modułu programu PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: 93a8c11099a9883127bca87422e1acaebfd2c093
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670294"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>Jak napisać manifest modułu programu PowerShell

Po napisaniu modułu programu Windows PowerShell, możesz opcjonalnie dodać manifestu modułu. Manifest modułu jest plik skryptu programu PowerShell, których można użyć w celu dodania informacji o module. Na przykład możesz opisują autora, określ pliki modułów (np. moduły zagnieżdżonych) uruchamianie skryptów, aby dostosować środowisko użytkownika obciążenia typu i pliki formatowania, zdefiniuj wymagania systemowe i ograniczyć elementów członkowskich, które eksportuje modułu.

## <a name="creating-a-module-manifest"></a>Tworzenie manifestu modułu

A *manifestu modułu* jest plikiem danych programu Windows PowerShell (psd1), w tym artykule opisano zawartość modułu, który określa sposób przetwarzania modułu. Sam plik manifestu to plik tekstowy, który zawiera tabelę mieszania kluczy i wartości. Możesz połączyć plik manifestu modułu nazewnictwa taka sama jak moduł, i umieszczając go w folderze głównym katalogu modułu.

Proste modułów, które zawierają tylko jednego psm1 lub zestawie binarnym manifestu modułu jest opcjonalne. Jednak zalecane jest, że używasz manifestu modułu, jeśli to możliwe, są one przydatne, aby ułatwić organizowanie kodu i utrzymać informacji o wersji. Ponadto manifestu modułu jest wymagany do wyeksportowania zestawu, który jest zainstalowany w globalnej pamięci podręcznej. Manifest modułu jest również wymagane dla modułów, które obsługują funkcję aktualizowalnej pomocy. Oznacza to, że aktualizowalnej pomocy używa **HelpInfoUri** klucza w manifeście modułu, można znaleźć pliku pomocy informacje (HelpInfo XML), zawierający lokalizację plików zaktualizowano Pomoc dla modułu. Aby uzyskać więcej informacji na temat aktualizowalnej pomocy zobacz [Obsługa aktualizowalnej pomocy](./supporting-updatable-help.md).

### <a name="to-create-and-use-a-module-manifest"></a>Tworzenie i używanie manifestu modułu

1. Aby utworzyć manifest modułu, masz kilka opcji:

   1. Bezpośrednio utworzyć tablicy skrótów z minimalne wymagane informacje, a następnie zapisz go w pliku psd1, który ma taką samą nazwę jak modułu. Gdy to zrobisz, możesz otworzyć plik i ręcznie dodać odpowiednie wartości.

      `'@{ModuleVersion="1.0"}' > myModuleName.psd1`

   2. Lub zadzwoń [New ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) polecenia cmdlet z co najmniej jeden z wartościami domyślnymi przekazanych jako parametry. (Należy pamiętać, że tylko nazwa pliku jest wymagana do generowania manifestu, jednak.) Spowoduje to utworzenie manifestu modułu przy użyciu wszystkich manifestu wartości podanej jasno określone i z użyciem usług rest, zawierającego wartość odpowiednią wartość domyślną.

      `New-ModuleManifest myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   3. Na koniec możesz można również utworzyć plik psd1 pusty skopiuj szablon w dolnej części tego tematu do pliku i podaj odpowiednie wartości. Tylko rzeczywistego zapotrzebowania w tym przypadku byłoby upewnij się, że plik został samej nazwie jak moduł.

2. Dodaj w wszelkie dodatkowe elementy do manifestu, który chcesz mieć w pliku.

   Ogólnie rzecz biorąc będzie prawdopodobnie to w edytorze tekstów, niezależnie od preferowanego, takiego jak Notatnik. Jednak technicznie jest to plik skryptu, który zawiera kod, dzięki czemu możesz poddać go edycji w rzeczywistych skryptów lub tworzenia środowiska, takich jak program PowerShell ISE. Ponownie należy pamiętać, że wszystkie elementy pliku manifestu są opcjonalne, z wyjątkiem numer ModuleVersion.

   Opisy kluczy i wartości, które mogą mieć w manifeście modułu można znaleźć **elementy manifestu modułu** poniżej. Aby uzyskać dodatkowe informacje, zobacz opisy parametrów w [New ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) polecenia cmdlet.

3. Opcjonalnie można dodać dodatkowy kod do Twojego manifestu modułu dla scenariuszy, które nie zostaną objęte przez elementy manifestu bazowy moduł.

   Ze względów bezpieczeństwa środowiska PowerShell będzie działał tylko mały podzbiór dostępne operacje w pliku manifestu modułu. Ogólnie rzecz biorąc, można użyć **Jeśli** instrukcji, operatory arytmetyczne i porównania i podstawowe typy danych programu PowerShell.

4. Po utworzeniu manifeście modułu, można go przetestować (w celu potwierdzenia, że wszystkie ścieżki, które opisano w manifestu są prawidłowymi) z wywołaniem [ModuleManifest testu](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest).

   `Test-ModuleManifest myModuleName.psd1`

5. Pamiętaj, że Twoje manifestu modułu znajdują się w najwyższym poziomie katalogu, który zawiera modułu.

   Podczas kopiowania modułu do systemu i zaimportować go, programu PowerShell użyje manifestu modułu do zaimportowania modułu.

6. Opcjonalnie można przetestować bezpośrednio manifeście modułu z wywołaniem [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) , funkcja dot-sourcing manifestu, sam.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>Elementy manifestu modułu

W poniższej tabeli opisano elementy, które mogą mieć w manifeście modułu

|Element|Wartość domyślna|Opis|
|-------------|-------------|-----------------|
|Polach RootModule<br /><br /> Typ: ciąg|' '|Moduł lub dane binarne modułu plik skryptu skojarzone z tym manifeście. Poprzednie wersje programu PowerShell, nazywane tego elementu ModuleToProcess.<br /><br /> Możliwych typów dla modułu głównego może być pusta (który ułatwi to **manifestu** modułu), nazwa modułu skryptu (psm1, co sprawia, że to **skryptu** moduł), lub nazwą binarne modułu (.exe lub .dll, co sprawia, że to **binarne** modułu). Umieszczenie nazwy modułu manifestu (psd1) lub pliku skryptu (ps1), w tym elemencie spowoduje, że błąd wystąpić.|
|ModuleVersion<br /><br /> Typ: ciąg|1.0|Numer wersji tego modułu. Ciąg musi być możliwe do przekonwertowania na [System.Version]. Oznacza to "#. #. #. #. #". `Import-Module` zostanie załadowany pierwszy moduł znajdzie na **$psModulePath** jest zgodna z nazwą i jest przynajmniej tak duży ModuleVersion `-MinimumVersion` parametru. Aby zaimportować określoną wersję, użyj`-RequiredVersion` parametru, zamiast tego.<br /><br /> Przykład: `ModuleVersion = '1.0'`|
|IDENTYFIKATOR GUID<br /><br /> Typ: ciąg|Identyfikator GUID wygenerowany automatycznie|Identyfikator używany do jednoznacznego identyfikowania tego modułu. Należy pamiętać, że obecnie nie można zaimportować modułu przez identyfikator GUID.<br /><br /> Przykład: `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|Autor<br /><br /> Typ: ciąg|Brak|Autor tego modułu.<br /><br /> Przykład: `Author = 'AuthorNameHere'`|
|CompanyName<br /><br /> Typ: ciąg|Nieznany|Firmy lub dostawcy tego modułu.<br /><br /> Przykład: `CompanyName = 'Fabrikam'`|
|Prawa autorskie<br /><br /> Typ: ciąg|(c) [currentYear] [Autor]. Wszelkie prawa zastrzeżone.|Informacje o prawach autorskich dla tego modułu.<br /><br /> Przykład: `Copyright = '2016 AuthorName. All rights reserved.'`|
|Opis<br /><br /> Typ: ciąg|' '|Opis funkcji oferowanych przez ten moduł.<br /><br /> Przykład: `Description = 'This is a description of a module.'`|
|PowerShellVersion<br /><br /> Typ: ciąg|' '|Minimalna wersja aparatu programu Windows PowerShell, wymagane przez ten moduł. Bieżący prawidłowymi wartościami są 1.0, 2.0, 3.0, 4.0 i 5.0.<br /><br /> Przykład: `PowerShellVersion = '5.0'`|
|PowerShellHostName<br /><br /> Typ: ciąg|' '|Określa nazwę hosta programu Windows PowerShell, który jest wymagany przez moduł. Ta nazwa jest zapewniana przez środowisko Windows PowerShell. Aby znaleźć nazwę programu hostów w programie, wpisz: `$host.name` .<br /><br /> Przykład: `PowerShellHostName = 'Windows PowerShell ISE Host'`|
|PowerShellHostVersion<br /><br /> Typ: ciąg|' '|Minimalna wersja wymagana przez ten moduł hosta programu Windows PowerShell.<br /><br /> Przykład: `PowerShellHostVersion = '2.0'`|
|DotNetFrameworkVersion<br /><br /> Typ: ciąg|' '|Minimalna wersja programu Microsoft .NET Framework wymaganego przez ten moduł.<br /><br /> Przykład: `DotNetFrameworkVersion = '3.5'`|
|CLRVersion<br /><br /> Typ: ciąg|' '|Minimalna wersja środowisko uruchomieniowe języka wspólnego (CLR) wymagane przez ten moduł.<br /><br /> Przykład: `CLRVersion = '3.5'`|
|ProcessorArchitecture<br /><br /> Typ: ciąg|' '|Architektura procesora (Brak, X86, Amd64) wymagane przez ten moduł. Prawidłowe wartości to x86 AMD64 IA64 i None (nieznany lub nieokreślony).<br /><br /> Przykład: `ProcessorArchitecture = 'x86'`|
|RequiredModules<br /><br /> Typ: [string []]|@()|Moduły, które muszą być importowane w środowisku globalnym, przed zaimportowaniem tego modułu. Zostaną załadowane moduły, chyba, że już zostały załadowane na liście. (Na przykład niektóre moduły mogą już być ładowane przez innego modułu.). Istnieje również możliwość określenia określonej wersji, aby załadować przy użyciu `RequiredVersion` zamiast `ModuleVersion`. Korzystając z `ModuleVersion` będzie on ładować się najnowsza wersja dostępna z co najmniej wersja określona.<br /><br /> Przykład: `RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /><br /> Przykład: `RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|RequiredAssemblies<br /><br /> Typ: [string []]|@()|Zestawy, które muszą zostać załadowane przed zaimportowaniem tego modułu.<br /><br /> Należy pamiętać, że w przeciwieństwie do RequiredModules, programu PowerShell zostanie załadowany RequiredAssemblies, jeśli nie są już załadowane.|
|ScriptsToProcess<br /><br /> Typ: [string []]|@()|Pliki skryptów (ps1), które są uruchamiane w ramach stanu sesji obiektu wywołującego, po zaimportowaniu modułu. Może to być globalne sesji stanu lub, w przypadku modułów zagnieżdżonych, stan sesji innego modułu. Te skrypty można użyć, aby przygotować środowisko, tak samo, jak można użyć skryptu logowania.<br /><br /> Te skrypty są uruchamiane przed żadnych modułów wymienione w manifeście są ładowane.|
|TypesToProcess<br /><br /> Typ: [obiekt []]|@()|Typ plików (.ps1xml), należy załadować podczas importowania tego modułu.|
|FormatsToProcess<br /><br /> Typ: [obiekt []]|@()|Format plików (.ps1xml), należy załadować podczas importowania tego modułu.|
|NestedModules<br /><br /> Typ: [obiekt []]|@()|Moduły do zaimportowania jako moduły zagnieżdżonych modułu określone w polach RootModule/ModuleToProcess.<br /><br /> Dodawanie nazwy modułu do tego elementu jest podobne do wywoływania `Import-Module` z kodem skryptu lub zestawu. Główną różnicą jest ona łatwiej zobaczyć, jakie są ładowane w tym miejscu w pliku manifestu. Ponadto jeśli moduł ładuje się w tym miejscu, będą nie jeszcze załadowane rzeczywiste modułu.<br /><br /> Oprócz innych modułów należy również załadować pliki skryptu (ps1), w tym miejscu. Te pliki będą wykonywane w kontekście modułu głównego. (To jest równoważne z dot sourcing skryptu w module głównym).|
|FunctionsToExport<br /><br /> Typ: Ciąg|'*'|Określa funkcje, które moduł eksportuje (symbole wieloznaczne są dozwolone znaki) do obiektu wywołującego stanu sesji. Domyślnie wszystkie funkcje są eksportowane. Ten klucz służy do ograniczania funkcje, które są eksportowane przez moduł.<br /><br /> Stan sesji wywołującego może być globalne sesji stanu lub, w przypadku modułów zagnieżdżonych, stan sesji innego modułu. Podczas łańcuch modułów zagnieżdżonych, wszystkie funkcje, które są eksportowane przez moduł zagnieżdżonych zostaną wyeksportowane do globalnego stanu sesji, chyba, że moduł w łańcuchu ogranicza funkcję przy użyciu klucza FunctionsToExport.<br /><br /> Jeśli manifest Eksportuje również aliasy funkcji, ten klucz, można usunąć funkcji, którego aliasy są wymienione w kluczu AliasesToExport, ale ten klucz nie może dodać aliasy funkcji do listy.|
|CmdletsToExport<br /><br /> Typ: Ciąg|'*'|Określa polecenia cmdlet, które moduł eksportuje (symbole wieloznaczne są dozwolone znaki). Domyślnie wszystkie polecenia cmdlet są eksportowane. Ten klucz służy do ograniczania poleceń cmdlet, które są eksportowane przez moduł.<br /><br /> Stan sesji wywołującego może być globalne sesji stanu lub, w przypadku modułów zagnieżdżonych, stan sesji innego modułu. Gdy są łańcuch modułów zagnieżdżonych, wszystkie polecenia cmdlet, które są eksportowane przez moduł zagnieżdżonych zostanie ostatecznie wyeksportowany do globalnego stanu sesji chyba, że moduł w łańcuchu ogranicza możliwość użycia polecenia cmdlet przy użyciu klucza CmdletsToExport.<br /><br /> Jeśli manifest Eksportuje również aliasy dla poleceń cmdlet, ten klucz, można usunąć poleceń cmdlet, którego aliasy są wymienione w kluczu AliasesToExport, ale ten klucz nie może dodać aliasy polecenia cmdlet do listy.|
|VariablesToExport<br /><br /> Typ: Ciąg|'*'|Określa zmienne, które moduł eksportuje (symbole wieloznaczne są dozwolone znaki) do obiektu wywołującego stanu sesji. Domyślnie wszystkie zmienne są eksportowane. Ten klucz służy do ograniczania zmiennych, które są eksportowane przez moduł.<br /><br /> Stan sesji wywołującego może być globalne sesji stanu lub, w przypadku modułów zagnieżdżonych, stan sesji innego modułu. Gdy są łańcucha zagnieżdżonych modułów, wszystkie zmienne, które są eksportowane przez moduł zagnieżdżonych zostaną wyeksportowane do globalnego stanu sesji, chyba że moduł w łańcuchu ogranicza zmiennej za pomocą klucza VariablesToExport.<br /><br /> Jeśli manifest Eksportuje również aliasy zmiennych, ten klucz, można usunąć zmienne, którego aliasy są wymienione w kluczu AliasesToExport, ale ten klucz nie można dodać zmiennej aliasów do listy.|
|AliasesToExport<br /><br /> Typ: Ciąg|'*'|Określa aliasy, które moduł eksportuje (symbole wieloznaczne są dozwolone znaki) do obiektu wywołującego stanu sesji. Domyślnie wszystkie aliasy są eksportowane. Ten klucz służy do ograniczania aliasy, które są eksportowane przez moduł.<br /><br /> Stan sesji wywołującego może być globalne sesji stanu lub, w przypadku modułów zagnieżdżonych, stan sesji innego modułu. Gdy są łańcuch modułów zagnieżdżonych, wszystkie aliasy, które są eksportowane przez moduł zagnieżdżonych zostanie ostatecznie wyeksportowany do globalnego stanu sesji chyba, że moduł w łańcuchu ogranicza alias przy użyciu klucza AliasesToExport.|
|ModuleList<br /><br /> Typ: [string []]|@()|Określa wszystkie moduły, które są dostarczane za pomocą tego modułu. Te moduły można wprowadzić według nazwy (ciąg rozdzielony przecinkami) lub jako tabela skrótów przy użyciu kluczy ModuleName i identyfikator GUID. W tabeli mieszania może być również opcjonalny klucz ModuleVersion. Klucz ModuleList jest zaprojektowane do działania jako magazyn modułu. Te moduły nie zostały przetworzone automatycznie.|
|FileList<br /><br /> Typ: [string []]|@()|Lista wszystkich plików w pakiecie z tego modułu. Jako za pomocą ModuleList, FileList ma pomóc jako lista spisu, a w przeciwnym razie nie została przetworzona.|
|PrivateData<br /><br /> Typ: [object]|' '|Określa dane prywatne, które należy przekazać do modułu głównego określony przez klucz polach RootModule/ModuleToProcess.|
|HelpInfoURI<br /><br /> Typ: ciąg|' '|Identyfikator URI HelpInfo tego modułu.|
|DefaultCommandPrefix<br /><br /> Typ: ciąg|' '|Domyślny prefiks dla poleceń wyeksportować z tego modułu. Przesłonić domyślny prefiks przy użyciu `Import-Module` — prefiks.|

## <a name="sample-module-manifest"></a>Przykładowe manifestu modułu

Następujące przykładowe manifeście modułu zawiera klucze i wartości domyślne w manifeście modułu. W tym przykładzie został utworzony przy użyciu `New-ModuleManifest` polecenia cmdlet w środowisku Windows PowerShell 3.0. Podczas tworzenia wielu modułów, umożliwia to polecenie cmdlet tworzenia manifestu szablonu, który może być modyfikowany dla różnych modułów.

```powershell
#
# Module manifest for module 'myManifest'
#
# Generated by: User01
#
# Generated on: 1/24/2012
#

@{

# Script module or binary module file associated with this manifest
#RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = 'd0a9150d-b6a4-4b17-a325-e3a24fed0aa9'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2012 User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the Windows PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of the .NET Framework required by this module
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module
FunctionsToExport = '*'

# Cmdlets to export from this module
CmdletsToExport = '*'

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module
AliasesToExport = '*'

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess
# PrivateData = ''

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}

```

## <a name="see-also"></a>Zobacz też

[Pisanie modułu programu Windows PowerShell](./writing-a-windows-powershell-module.md)
