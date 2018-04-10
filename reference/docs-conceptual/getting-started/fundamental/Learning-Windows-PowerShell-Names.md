---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Poznawanie nazw programu Windows PowerShell
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
ms.openlocfilehash: 381aa619a41ccacb2ff3a4cdbc2b75b7f04282d1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="learning-windows-powershell-names"></a>Poznawanie nazw programu Windows PowerShell
Learning nazwy poleceń i parametrów polecenia jest inwestycji długiego czasu, większość interfejsów wiersza polecenia. Problem polega na tym, czy bardzo mało wzorców, więc jedynym sposobem, aby dowiedzieć się, jest tylko każdego polecenia i każdego parametru, który musi być na bieżąco.

Podczas pracy z nowego polecenia lub parametr, zwykle można co znasz już; należy znaleźć i Dowiedz się nową nazwę. Jeśli przyjrzymy się jak Zwiększ interfejsy z niewielki zestaw narzędzi z dodatkami przyrostowe do funkcji, jest łatwo sprawdzić, dlaczego struktury jest niestandardowy. Z nazw poleceń w szczególności, to może dźwiękowej logicznej ponieważ każde polecenie jest narzędziem do oddzielnych, ale lepiej obsługiwać nazw poleceń.

Większość używanych poleceń są przeznaczone do zarządzania elementami systemu operacyjnego lub aplikacji, takich jak usług lub procesów. Polecenia mają różne nazwy, które mogą lub mogą nie pasować do rodziny. Na przykład w systemach Windows, można użyć **net start** i **net stop** polecenia, aby uruchomić i zatrzymać usługi. Istnieje inne narzędzie kontroli usługi bardziej ogólną dla systemu Windows o innej nazwie, **sc**, który nie pasuje do wzorca nazewnictwa dla **net** obsługi poleceń. Zarządzanie procesem, system Windows ma **tasklist** polecenia do listy procesów i **taskkill** polecenia kill procesów.

Polecenia, które przyjmują parametry mają specyfikacje nieprawidłowych parametrów. Nie można użyć **net start** polecenie, aby uruchomić usługę na komputerze zdalnym. **Sc** polecenia powoduje uruchomienie usługi na komputerze zdalnym, ale aby określić komputer zdalny, możesz jej nazwę musi poprzedzać prefiks podwójny ukośnik odwrotny. Na przykład, aby uruchomić usługę buforu wydruku na komputerze zdalnym o nazwie DC01, należy wpisać **sc \\ \\DC01 start buforu**. Do listy zadań uruchomionych na DC01, należy użyć **/S** parametr (dla "systemu") i podaj nazwę DC01 bez ukośników odwrotnych w następujący sposób: **tasklist /S DC01**.

Chociaż są ważne techniczne różnice między usługą i procesem, są oba przykłady elementów można zarządzać na komputerze, które mają dobrze zdefiniowanego cyklu życia. Możesz rozpocząć lub zatrzymać usługi lub procesu lub uzyskać listę wszystkich aktualnie uruchomione usług lub procesów. Innymi słowy mimo że usługę i procesem są różne, akcje, które na usługi lub procesu są często koncepcyjnie takie same. Ponadto opcje, które firma Microsoft może wprowadzać można dostosować, określając parametry akcji mogą być podobny również.

Środowisko Windows PowerShell wykorzystuje te podobieństwa, aby zmniejszyć liczbę unikatowych nazw musisz wiedzieć, aby zrozumieć i użyć polecenia cmdlet.

### <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a>Użyj polecenia cmdlet czasownik rzeczownik nazw zmniejszenie Memorization polecenia
Program Windows PowerShell korzysta "czasownik rzeczownik" systemem nazw, gdy każda nazwa polecenia cmdlet składa się z standardowe zlecenie dzielone z określonych rzeczownik. Poleceń programu Windows PowerShell nie zawsze są zleceń w języku angielskim, ale one express określone czynności w programie Windows PowerShell. Rzeczowniki są bardzo podobne rzeczowniki w dowolnym języku, opisano w nich określonych typów obiektów, które są ważne w witrynie Administracja systemu. To proste zademonstrować, jak te nazwy dwuczęściową ograniczyć learning analizując kilka przykładów zleceń i rzeczowniki.

Rzeczowniki są mniej ograniczone, ale należy zawsze opisano polecenie działa na. Środowisko Windows PowerShell jest polecenia **Get-Process**, **Stop-Process**, **Get-Service**, i **Stop-Service**.

W przypadku dwóch rzeczowniki i dwóch zleceń spójności nie uprościć, learning fragment odpowiadający. Jednak jeśli przyjrzymy się standardowy zestaw 10 zleceń i 10 rzeczowniki, można wybrać tylko 20 słów, aby zrozumieć, ale te słowa może służyć do tworzenia 100 polecenia unikatowych nazw.

Często może rozpoznać, odczytując nazwy działania polecenia i zwykle okaże się, jaką nazwę ma być używane jako nowe polecenie. Na przykład polecenie zamknięcia komputera może być **Stop-Computer**. Polecenie, które wyświetla listę wszystkich komputerów w sieci może być **Get-Computer**. To polecenie pobiera datę systemową **Get-Date**.

Możesz wyświetlić listę wszystkich poleceń, które zawierają konkretnego zlecenia z **— zlecenie** parametr **Get-Command** (omówimy **Get-Command** szczegółowo w następnej sekcji). Na przykład, aby wyświetlić wszystkie polecenia cmdlet, które używają zlecenie **uzyskać**, wpisz:

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

**-Rzeczownik** parametr jest bardziej przydatne, ponieważ umożliwia Zobacz rodziny poleceń, które mają wpływ na ten sam typ obiektu. Na przykład jeśli chcesz zobaczyć, które polecenia są dostępne do zarządzania usługami, wpisz następujące polecenie:

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

Polecenie nie jest zawsze polecenia cmdlet, po prostu, ponieważ ma ona schemat nazewnictwa czasownik rzeczownik. Przykładem natywnego polecenia programu Windows PowerShell, który nie jest poleceniem cmdlet, ale nazwa czasownik rzeczownik, to polecenie czyszczenia okna konsoli, wyczyść hosta. Polecenie Wyczyść hosta jest rzeczywiście funkcji wewnętrznej, jak widać, jeśli Get-Command Uruchom na niej:

```
PS> Get-Command -Name Clear-Host

CommandType     Name                            Definition
-----------     ----                            ----------
Function        Clear-Host                      $spaceType = [System.Managem...
```

### <a name="cmdlets-use-standard-parameters"></a>Użyj polecenia cmdlet standardowe parametry
Jak wspomniano wcześniej, polecenia używane w tradycyjnych interfejsów wiersza polecenia nie ma zazwyczaj nazwy parametrów zgodne. Czasami parametry bez nazwy w ogóle. Gdy tak robią, są często jednym znaku lub skrócone słowa, które można wpisać szybko, ale nie są zrozumiałe dla nowych użytkowników.

W przeciwieństwie do większości innych tradycyjnych interfejsów wiersza polecenia programu Windows PowerShell bezpośrednio przetwarza parametry i używa tego bezpośredni dostęp do parametrów oraz wskazówki dla deweloperów normalizacji nazwy parametrów. Mimo że nie gwarantuje to, że każdy polecenia cmdlet będzie zawsze ze standardami, jego zachęca.

> [!NOTE]
> Zawsze mają nazwy parametru "-" dołączany na początku ich użycia, aby umożliwić programowi Windows PowerShell jednoznacznie zidentyfikować je jako parametry. W **Get-Command - Name Clear-Host** przykładzie nazwa parametru jest **nazwa**, ale jest wprowadzana jako -**nazwa**.

Poniżej przedstawiono ogólne właściwości nazwy parametrów standardowe i ich użycia.

#### <a name="the-help-parameter-"></a>Parametr pomocy (?)
Po określeniu **-?** parametr do każdego polecenia cmdlet, polecenie cmdlet nie została wykonana. Zamiast tego środowiska Windows PowerShell Wyświetla Pomoc dotyczącą polecenia cmdlet.

#### <a name="common-parameters"></a>Wspólne parametry
Środowisko Windows PowerShell zawiera kilka parametrów, znany jako *wspólne parametry*. Ponieważ te parametry są kontrolowane przez aparat środowiska Windows PowerShell w każdym przypadku, gdy są implementowane za pomocą polecenia cmdlet, będzie zawsze zachowują się tak samo. Wspólne parametry są **WhatIf**, **Potwierdź**, **pełne**, **debugowania**, **Ostrzegaj**, **ErrorAction**, **ErrorVariable**, **OutVariable**, i **OutBuffer**.

#### <a name="suggested-parameters"></a>Sugerowane parametrów
Podstawowych poleceń cmdlet programu Windows PowerShell Użyj standardowych nazw dla podobnych parametrów. Mimo że użycia nazwy parametrów nie jest wymuszana, nie istnieje jawne wskazówki dotyczące użycia wspieranie normalizacji.

Na przykład wskazówki zaleca parametr nazewnictwa, która odnosi się do komputera o nazwie, co **ComputerName**, a nie serwera hosta, System, węzła albo innych popularnych wyrazów alternatywnych. Wśród ważne parametru sugerowane nazwy są **życie**, **wykluczyć**, **Include**, **PassThru**, **ścieżka**, i **CaseSensitive**.