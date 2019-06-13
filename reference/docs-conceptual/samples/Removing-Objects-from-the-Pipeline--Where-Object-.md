---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Usuwanie obiektów z potoku gdzie obiektu
ms.openlocfilehash: c47efd38e2ff40ce3b7bf50b161cc38de922c5da
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030883"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a>Usuwanie obiektów z potoku (Where-Object)

W programie Windows PowerShell możesz często Generowanie i przekazują więcej obiektów do potoku niż potrzebujesz. Można określić właściwości określonego obiektów przeznaczonych do wyświetlenia przy użyciu **Format** poleceń cmdlet, ale nie jest pomocne w rozwiązaniu problemu usunięcia całe obiekty z widoku. Można filtrować obiektów przed zakończeniem potoku, dzięki czemu można przeprowadzać na tylko podzbiór obiektów początkowo wygenerował.

Program Windows PowerShell zawiera `Where-Object` polecenia cmdlet, które umożliwia testowanie każdy obiekt w potoku i tylko przekazać go do potoku Jeśli dana jednostka spełnia warunek określonego testu. Obiekty, które nie są przekazywane do testu są usuwane z potoku. Możesz podać warunek testu jako wartość `Where-Object` **FilterScript** parametru.

## <a name="performing-simple-tests-with-where-object"></a>Wykonując proste testy za pomocą Where-Object

Wartość **FilterScript** jest *blok skryptu* — jedno lub kilka poleceń programu Windows PowerShell, ujęte w nawiasy klamrowe {} — która daje w wyniku wartość true lub false. Te bloki skryptu może być bardzo proste, ale są one tworzone wymaga, wiedząc o innym pojęcia programu Windows PowerShell, operatory porównania. Operator porównania porównuje elementów, które pojawiają się na każdej stronie. Operatory porównania zaczynają się od "-" znaków i są następuje nazwa. Operatory porównania podstawowe działa na prawie każdy rodzaj obiektu. Więcej informacji o zaawansowanych operatory porównania może działać wyłącznie względem tekstu lub tablic.

> [!NOTE]
> Domyślnie podczas pracy z tekstem operatory porównania programu Windows PowerShell jest rozróżniana wielkość liter.

Ze względu na analizowanie zagadnienia, symbole, takie jak <>, i = nie są używane jako operatory porównania. Zamiast tego operatory porównania składają się z liter. Operatory porównania podstawowe są wymienione w poniższej tabeli.

|Operator porównania|Znaczenie|Przykład (zwraca wartość true)|
|-----------------------|-----------|--------------------------|
|-eq|jest równa|1 - eq 1|
|-ne|Nie równa się|1 - ne 2|
|-lt|Jest mniejsza niż|1 - lt 2|
|-le|jest mniejsze niż lub równe|1 - le 2|
|-gt|jest większa niż|2 - > 1|
|-ge|jest większe lub równe|2 -ge 1|
|— np.|Przypomina (symbol wieloznaczny porównanie tekstu)|"file.doc" — takich jak "f\*.korzystać?"|
|-notlike|Nie jest podobne (symbol wieloznaczny porównanie tekstu)|"file.doc"-notlike "p\*doc"|
|-zawiera|zawiera|1,2,3 - zawiera 1|
|-notcontains|Nie zawiera|1,2,3 - notcontains 4|

WHERE-Object Bloki skryptu za pomocą specjalnych zmiennej `$_` do odwoływania się do bieżącego obiektu w potoku. Oto przykład sposobu działania. Jeśli masz listę liczb i tylko mają być zwracane te, które są mniej niż 3, można użyć Where-Object do filtrowania liczby, wpisując:

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a>Filtrowanie oparte na właściwości obiektu

Ponieważ `$_` odwołuje się do bieżącego obiektu potoku, firma Microsoft będą mogli jej właściwości na potrzeby testów.

Na przykład można przyjrzymy się Klasa Win32_SystemDriver w usłudze WMI. Mogą istnieć setki sterowników systemu w określonym systemie, ale może być tylko zainteresowana określony zestaw sterowników systemu, takie jak te, które są aktualnie uruchomione. Jeśli używasz Get-Member, aby wyświetlić elementy członkowskie Win32_SystemDriver (**Get-WmiObject — Klasa Win32_SystemDriver | Właściwość Get-Member - MemberType**) widać to za pomocą odpowiednich właściwości stanu i że ma wartość "Uruchomiona", gdy sterownik jest uruchomiony. Możesz filtrować sterowniki systemowe, wybierając tylko uruchomione, wpisując:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

Daje to nadal długą listę. Można filtrować tylko wybranym sterowniki uruchamiana automatycznie, testując również wartość StartMode:

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

To daje nam mnóstwo informacji, które firma Microsoft nie są już potrzebne, ponieważ wiemy, że sterowniki są uruchomione. W rzeczywistości tylko informacje, które prawdopodobnie należy w tym momencie są nazwę i nazwę wyświetlaną. Poniższe polecenie uwzględnia tylko te dwie właściwości, co znacznie przyspiesza dane wyjściowe:

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

Istnieją dwa elementy Where-Object w poleceniu powyżej, ale mogą być wyrażone w pojedynczym elemencie Where-Object przy użyciu i operatora logicznego w następujący sposób:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual') } | Format-Table -Property Name,DisplayName
```

Standardowe operatory logiczne są wymienione w poniższej tabeli.

|Operator logiczny|Znaczenie|Przykład (zwraca wartość true)|
|--------------------|-----------|--------------------------|
|- i|Logiczne i; wartość true, jeśli obie strony mają wartość true|(1 - eq 1) — a (2 - eq 2).|
|— lub|Logiczne lub; wartość true, jeśli strona ma wartość true|(1 - eq 1) - lub (1 - eq 2).|
|-nie|Logiczne not; Odwraca wartość PRAWDA i FAŁSZ|-nie (1 - eq 2)|
|\!|Logiczne not; Odwraca wartość PRAWDA i FAŁSZ|\!(1 - eq 2)|
