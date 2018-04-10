---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Usuwanie obiektów z potoku gdzie obiektów
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
ms.openlocfilehash: 2d89defdb1b234a9d0021fc06e1f05a95bb1bce9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="removing-objects-from-the-pipeline-where-object"></a>Usuwanie obiektów z potoku (Where-Object)

W programie Windows PowerShell można często generować i przekazują więcej obiektów dla potoku nie ma. Możesz określić właściwości określonym obiektów do wyświetlenia za pomocą **Format** poleceń cmdlet, ale nie pomaga problemu usunięcie całych obiektów z ekranu. Można filtrować obiektów przed zakończeniem potoku, więc dostępne akcje na podzbiorze wstępnie wygenerowane obiekty.

Program Windows PowerShell zawiera **Where-Object** polecenia cmdlet, które umożliwia testowanie każdego obiektu w potoku i tylko przekazywanie ich do potoku spełniający określonego warunku. Obiekty, które nie przejdą testów są usuwane z potoku. Podaj warunku w postaci wartości **Where ObjectFilterScript** parametru.

### <a name="performing-simple-tests-with-where-object"></a>Wykonywanie prostych testów z Where-Object

Wartość **FilterScript** jest *bloku skryptu* — jeden lub więcej poleceń programu Windows PowerShell otoczona nawiasów klamrowych {} - który daje w wyniku wartość true lub false. Te bloki skryptu może być bardzo proste, ale są one tworzone wymaga wiedzy pojęcie innego środowiska Windows PowerShell i operatory porównania. Operator porównania porównuje elementy, które są wyświetlane na każdej stronie. Operatory porównania rozpoczynać się od "-" znak i zostaną wykonane przez nazwę. Operatory porównania podstawowe działają w niemal każdego rodzaju obiektu. Bardziej zaawansowane operatory porównania może działać tylko na tekst lub tablic.

> [!NOTE]
> Domyślnie podczas pracy z tekstem programu Windows PowerShell operatory porównania jest rozróżniana wielkość liter.

Z powodu analizy zagadnienia, symbole, takie jak <>, i = nie są używane jako operatory porównania. Zamiast tego operatory porównania składają się z liter. Operatory porównania podstawowe są wymienione w poniższej tabeli.

|Operator porównania|Znaczenie|Przykład (zwraca wartość true)|
|-----------------------|-----------|--------------------------|
|-eq|jest równa|1 - eq 1|
|-ne|Nie równa się|1 - ne 2|
|lt —|Jest mniejsza niż|1 - lt 2|
|-le|Jest mniejsze niż lub równe|le 1 - 2|
|-gt|Jest większa niż|2 - gt-1|
|-ge|Jest większe lub równe|2 -ge 1|
|-like|Przypomina (symbol wieloznaczny porównanie tekstu)|"file.doc" — takie jak "f\*.korzystać?"|
|-notlike|Nie jest jak (symbol wieloznaczny porównanie tekstu)|"file.doc"-notlike "p\*doc"|
|-zawiera|zawiera|1,2,3 - zawiera 1|
|-notcontains|Nie zawiera|1,2,3 - notcontains 4|

WHERE-Object blokach skryptu za pomocą specjalnych zmiennej '$_' do odwoływania się do bieżącego obiektu w potoku. Poniżej przedstawiono przykładowy sposób jej działania. Jeśli masz listę liczb i chcesz tylko te, które są mniej niż 3 zwracać, umożliwia Where-Object filtrować liczb, wpisując:

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

### <a name="filtering-based-on-object-properties"></a>Filtrowanie oparte na właściwości obiektu

Ponieważ $_ odwołuje się do bieżącego obiektu potoku, firma Microsoft dostęp do jej właściwości na potrzeby testów.

Na przykład można przyjrzymy się Klasa Win32_SystemDriver w usłudze WMI. Może to być setki sterowników systemu w określonym systemie, ale może być zainteresowany określony zestaw sterowników systemu, takich jak te, które są aktualnie uruchomione. Jeśli element członkowski Get służy do wyświetlania elementów członkowskich Win32_SystemDriver (**Get-WmiObject — Klasa Win32_SystemDriver | Właściwość Get-Member - MemberType**) pojawi się stan jest odpowiednie właściwości i że ma wartość "Działa" po uruchomieniu sterownika. Można filtrować sterowniki systemu wybranie tylko uruchomione te, wpisując:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

Daje to nadal długą listę. Można filtrować można wybrać tylko sterowniki uruchamiana automatycznie, sprawdzając wartość StartMode również:

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Auto"}

DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
```

Daje wiele informacji, które firma Microsoft nie jest już potrzebny, ponieważ wiemy, że sterowniki są uruchomione. W rzeczywistości tylko informacje, które prawdopodobnie potrzebujemy w tym momencie są nazwa i nazwę wyświetlaną. Polecenie zawiera tylko te dwie właściwości, co znacznie prostsze danych wyjściowych:

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Manual"} | Format-Table -Property Name,DisplayName

Name                                    DisplayName
----                                    -----------
AsyncMac                                RAS Asynchronous Media Driver
Fdc                                     Floppy Disk Controller Driver
Flpydisk                                Floppy Disk Driver
Gpc                                     Generic Packet Classifier
IpNat                                   IP Network Address Translator
mouhid                                  Mouse HID Driver
MRxDAV                                  WebDav Client Redirector
mssmbios                                Microsoft System Management BIOS Driver
```

Istnieją dwa elementy Where-Object w poleceniu powyżej, ale może zostać wyrażona w jednym elemencie Where-Object przy użyciu i operatora logicznego następująco:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual') } | Format-Table -Property Name,DisplayName
```

Standardowe operatory logiczne są wymienione w poniższej tabeli.

|Operator logiczny|Znaczenie|Przykład (zwraca wartość true)|
|--------------------|-----------|--------------------------|
|- i|Logiczne i; wartość true, jeśli obie strony mają wartość true|(1 - eq 1) - i (2 - eq 2).|
|- lub|Logiczna lub; wartość true, jeśli jedna strona ma wartość true|(1 - eq 1) - lub (1 - eq 2).|
|-nie|Negacja; Odwraca wartość true i false|-nie (1 - eq 2)|
|\!|Negacja; Odwraca wartość true i false|\!(1 - eq 2)|