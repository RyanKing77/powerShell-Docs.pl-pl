---
ms.date: 08/24/2018
keywords: polecenia cmdlet programu PowerShell
title: Poznawanie nazw programu PowerShell
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
ms.openlocfilehash: 6ed1f99513f00c174147876e1982c0d12869cacb
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405389"
---
# <a name="learning-powershell-names"></a>Poznawanie nazw programu PowerShell

Poznawanie nazw poleceń i parametrów wymaga inwestycji znaczną ilość czasu, z większości interfejsów z wierszem polecenia. Problem polega na tym, że istnieje kilka wzorców. Zapamiętywania jest jedynym sposobem, aby dowiedzieć się więcej poleceń i parametrów, które należy użyć w regularnych odstępach czasu.

Podczas pracy za pomocą nowego polecenia lub parametru nie zawsze używaj tego, co już znasz. Należy znaleźć i Dowiedz się, nową nazwę. Tradycyjnie interfejsów z wierszem polecenia start wprowadzaj w małej grupie, narzędzi i rozwój za pomocą dodatków przyrostowe. To proste zobaczyć, dlatego nie standardowej strukturze.
Może to być dla nazwy poleceń, ponieważ każde polecenie jest osobnego narzędzia. Program PowerShell ma lepszy sposób obsługi nazw poleceń.

## <a name="learning-command-names-in-traditional-shells"></a>Poznawanie nazw poleceń w tradycyjnej powłoki

Większość poleceń są kompilowane do elementów systemu operacyjnego lub aplikacji, takich jak usługi lub procesy zarządzania. Polecenia mają nazwy, jakie mogą być lub może nie być dopasowane do rodziny. Na przykład w przypadku systemów Windows, możesz użyć `net start` i `net stop` polecenia, aby uruchomić i zatrzymać usługę. **SC.exe** to kolejne narzędzie kontroli usługi dla Windows. Tej nazwy nie pasuje do wzorca nazewnictwa dla **net.exe** usługi poleceń. Do zarządzania procesami Windows ma **tasklist.exe** polecenia do listy procesów i **taskkill.exe** polecenie, aby zatrzymywać procesy.

Ponadto tych poleceń obowiązują specyfikacje nieregularne parametru. Nie można użyć `net start` polecenie, aby uruchomić usługę na komputerze zdalnym. **Sc.exe** polecenia można uruchomić usługę na komputerze zdalnym. Jednak aby określić komputer zdalny, możesz jej nazwę musi poprzedzać prefiks podwójny ukośnik odwrotny. Aby uruchomić usługę Bufor wydruku na komputerze zdalnym o nazwie DC01, możesz wpisać `sc.exe \\DC01 start spooler`.
Do listy podzadań uruchomionych w centrum danych DC01, użyj **/S** parametr i nazwę komputera bez ukośników odwrotnych. Na przykład `tasklist /S DC01`.

> [!NOTE]
> Przed programu PowerShell w wersji 6 `sc` alias został `Set-Content` polecenia cmdlet. Aby uruchomić **sc.exe** polecenia, musi zawierać rozszerzenie pliku.

Usługi i procesy są przykładami elementy zarządzane na komputerze, które mają dobrze zdefiniowanego cyklu. Może rozpocząć lub zatrzymać usług i procesów lub Uzyskaj listę wszystkich aktualnie uruchomionych usług lub procesów. Mimo że istnieją ważne różnice techniczne między nimi, akcje, które można wykonać na usług i procesów są koncepcyjnie takie same. Ponadto wyborów, których możemy wprowadzić dostosować akcję określania parametrów może być zachowuje się podobnie jak również.

Program PowerShell wykorzystuje te podobieństwa, aby zmniejszyć liczbę unikatowych nazw, trzeba znać do zrozumienia i użycia polecenia cmdlet.

## <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a>Polecenia cmdlet Użyj nazw czasownik rzeczownik, aby zmniejszyć zapamiętywania polecenia

Program PowerShell korzysta z systemu nazewnictwa "czasownik rzeczownik". Każda nazwa polecenia cmdlet składa się z standardowy czasownika podzielić przy użyciu określonych rzeczownik. Poleceń programu PowerShell nie zawsze są zleceń w języku angielskim, ale ich express konkretne akcje w programie PowerShell. Rzeczowniki są bardzo podobne rzeczowniki w dowolnym języku. Opisują one określonych typów obiektów, które są ważne w przypadku Administracja systemu. To proste zademonstrować, jak te nazwy legalną dwuczęściową zmniejszyć nakład pracy nauki, analizując kilka przykładów.

Program PowerShell zawiera zalecany zestaw zleceń standardowych. Rzeczowniki są mniej ograniczone, ale zawsze opisuje zlecenie działa na. Program PowerShell zawiera polecenia, takie jak `Get-Process`, `Stop-Process`, `Get-Service`, i `Stop-Service`.

Na przykład dwa rzeczowniki i zleceń spójności nie uprościć, nauki tej bardzo. Rozszerz tej liście, aby zestaw standardowych 10 zleceń i rzeczowniki 10. Teraz wystarczy tylko 20 wyrazy, aby zrozumieć.
Jednak te słowa mogą być połączone do formularza 100 polecenia unikatowych nazw.

Jest łatwa do zrozumienia, czytając nazwy działania polecenia programu PowerShell. To polecenie, aby zamknąć komputer `Stop-Computer`. Polecenie, aby wyświetlić listę wszystkich komputerów w sieci jest `Get-Computer`. To polecenie, aby pobrać daty systemowej `Get-Date`.

Możesz wyświetlić listę wszystkich poleceń, które zawierają konkretnego zlecenia z **zlecenie** parametr `Get-Command`. Na przykład, aby wyświetlić wszystkie polecenia cmdlet, które używają zlecenie `Get`, wpisz:

```
PS> Get-Command -Verb Get

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Acl                         Get-Acl [[-Path] <String[]>]...
Cmdlet          Get-Alias                       Get-Alias [[-Name] <String[]...
Cmdlet          Get-AuthenticodeSignature       Get-AuthenticodeSignature [-...
Cmdlet          Get-ChildItem                   Get-ChildItem [[-Path] <Stri...
...
```

Użyj **rzeczownik** parametru, aby zobaczyć rodzinę poleceń, które mają wpływ na ten sam typ obiektu. Na przykład uruchom następujące polecenie, aby zobaczyć dostępne do zarządzania usługami polecenia:

```
PS> Get-Command -Noun Service

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Service                     Get-Service [[-Name] <String...
Cmdlet          New-Service                     New-Service [-Name] <String>...
Cmdlet          Restart-Service                 Restart-Service [-Name] <Str...
Cmdlet          Resume-Service                  Resume-Service [-Name] <Stri...
Cmdlet          Set-Service                     Set-Service [-Name] <String>...
Cmdlet          Start-Service                   Start-Service [-Name] <Strin...
Cmdlet          Stop-Service                    Stop-Service [-Name] <String...
Cmdlet          Suspend-Service                 Suspend-Service [-Name] <Str...
...
```

## <a name="cmdlets-use-standard-parameters"></a>Polecenia cmdlet używają standardowe parametry

Jak wspomniano wcześniej, polecenia używane w tradycyjnych interfejsów z wierszem polecenia nie zawsze mają nazwy parametrów spójne. Parametry są często pojedynczych znaków lub skrócone wyrazy, które są łatwe do typu, ale nie są zrozumiałe dla nowych użytkowników.

W przeciwieństwie do większości innych tradycyjnych interfejsów wiersza polecenia programu PowerShell bezpośrednio przetwarza parametrów i używa tego bezpośredni dostęp do parametrów oraz wskazówki dla deweloperów do standaryzacji nazwy parametrów. Niniejsze wskazówki zachęca, ale nie gwarantuje, że każdego polecenia cmdlet są zgodne ze standardem.

Program PowerShell standaryzuje również separator parametru. Zawsze mieć nazwy parametru "-" dołączony do nich za pomocą polecenia programu PowerShell. Rozważmy następujący przykład:

```powershell
Get-Command -Name Clear-Host
```

Nazwa parametru jest **nazwa**, ale ma `-Name` stosowania jako parametr w wierszu polecenia.

Poniżej przedstawiono ogólne charakterystyki nazwy parametrów standardowe i użycia.

### <a name="the-help-parameter-"></a>Parametr pomocy (?)

Po określeniu `-?` parametru każdego polecenia cmdlet programu PowerShell Wyświetla Pomoc dotyczącą polecenia cmdlet.
Polecenie cmdlet nie jest wykonywany.

### <a name="common-parameters"></a>Wspólne parametry

Program PowerShell ma kilka *wspólnych parametrów*. Te parametry są kontrolowane przez aparatu programu PowerShell. Wspólne parametry zawsze zachowują się tak samo. Wspólne parametry są **WhatIf**, **Potwierdź**, **pełne**, **debugowania**, **Ostrzegaj**, **ErrorAction**, **ErrorVariable**, **OutVariable**, i **OutBuffer**.

### <a name="recommended-parameter-names"></a>Nazwy parametrów zalecane

Polecenia cmdlet programu PowerShell core używać standardowych nazw podobne parametry. Korzystanie z tych nazw standard nie są wymuszane, ale istnieje jawne ze wskazówkami, aby zachęcić normalizacji.

Na przykład, jest zalecane nazwę parametru, która odnosi się do komputera **ComputerName**, a nie serwera, hosta, System, węzeł lub powszechną alternatywą. Inne nazwy ważnych parametrów zalecane **życie**, **wykluczyć**, **Include**, **PassThru**, **ścieżki**, i **CaseSensitive**.
