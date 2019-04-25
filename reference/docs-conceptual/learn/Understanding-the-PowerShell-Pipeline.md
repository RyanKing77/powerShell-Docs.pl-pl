---
ms.date: 08/23/2018
keywords: polecenia cmdlet programu PowerShell
title: Opis potoki PowerShell
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: 05ab98b7261f4d41ade1788a924193eccda6318c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086446"
---
# <a name="understanding-pipelines"></a>Opis potoków

Potoki zachowywać się jak szereg podłączonych segmentów potoku. Przenoszenie do potoku elementów przechodzi przez każdy z segmentów. Aby utworzyć potok w programie PowerShell, łączenie poleceń, wraz z operatora potoku "|". Dane wyjściowe każdego polecenia jest używany jako dane wejściowe dla następnego polecenia.

Oznaczenie użyte w potokach przypomina notację używaną w innych powłoki. Na pierwszy rzut oka może nie być jasne, jak potoków różnią się w programie PowerShell. Mimo, że tekst jest widoczne na ekranie, programu PowerShell przekazuje obiektów, nie tekstu między poleceniami.

## <a name="the-powershell-pipeline"></a>Potoku programu PowerShell

Potoki są prawdopodobnie najbardziej wartościowych pojęcia używane w interfejsów z wierszem polecenia. W przypadku poprawnie potoki zmniejszyć nakład pracy przy użyciu poleceń złożone i ułatwić Zobacz przepływ pracy dla poleceń. Każde polecenie w potoku (nazywany elementem potoku) przekazuje dane wyjściowe do następnego polecenia w potoku, element przez element. Polecenia nie ma potrzeby obsługi więcej niż jeden element w danym momencie. Wynik jest użycie niższych zasobów oraz możliwość rozpocząć od razu uzyskiwanie danych wyjściowych.

Na przykład, jeśli używasz `Out-Host` po prostu wymusić wyświetlania strony Strona danych wyjściowych z innego polecenia, wyszukuje dane wyjściowe, takie jak zwykły tekst wyświetlany na ekranie, podzielone na strony:

```powershell
Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging
```

```Output
    Directory: C:\WINDOWS\system32

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        4/12/2018   2:15 AM                0409
d-----        5/13/2018  11:31 PM                1033
d-----        4/11/2018   4:38 PM                AdvancedInstallers
d-----        5/13/2018  11:13 PM                af-ZA
d-----        5/13/2018  11:13 PM                am-et
d-----        4/11/2018   4:38 PM                AppLocker
d-----        5/13/2018  11:31 PM                appmgmt
d-----        7/11/2018   2:05 AM                appraiser
d---s-        4/12/2018   2:20 AM                AppV
d-----        5/13/2018  11:10 PM                ar-SA
d-----        5/13/2018  11:13 PM                as-IN
d-----        8/14/2018   9:03 PM                az-Latn-AZ
d-----        5/13/2018  11:13 PM                be-BY
d-----        5/13/2018  11:10 PM                BestPractices
d-----        5/13/2018  11:10 PM                bg-BG
d-----        5/13/2018  11:13 PM                bn-BD
d-----        5/13/2018  11:13 PM                bn-IN
d-----        8/14/2018   9:03 PM                Boot
d-----        8/14/2018   9:03 PM                bs-Latn-BA
d-----        4/11/2018   4:38 PM                Bthprops
d-----        4/12/2018   2:19 AM                ca-ES
d-----        8/14/2018   9:03 PM                ca-ES-valencia
d-----        5/13/2018  10:46 PM                CatRoot
d-----        8/23/2018   5:07 PM                catroot2
<SPACE> next page; <CR> next line; Q quit
...
```

Stronicowanie także ogranicza wykorzystanie Procesora, ponieważ przetwarzanie przesyła do `Out-Host` polecenia cmdlet, gdy ma ona całą stronę gotowej do wyświetlenia. Polecenia cmdlet, które należy poprzedzić go w potoku zatrzymać wykonywanie aż do następnej strony w danych wyjściowych.

Możesz zobaczyć różnicę Menedżera zadań Windows do monitorowania procesora CPU i użycie pamięci przez program PowerShell. Uruchom następujące polecenie: `Get-ChildItem C:\Windows -Recurse`. Porównaj użycie Procesora i pamięci do tego polecenia: `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`.

> [!NOTE]
> **Stronicowania** parametr nie jest obsługiwany przez wszystkie hosty programu PowerShell. Na przykład podczas próby użycia **stronicowania** parametru w środowisku PowerShell ISE, zostanie wyświetlony następujący błąd:
>
> ```Output
> out-lineoutput : The method or operation is not implemented.
> At line:1 char:1
> + Get-ChildItem C:\Windows -Recurse | Out-Host -Paging
> + ~~~~~~~~~~~~~~~~~~~~~~~~~~~
>     + CategoryInfo          : NotSpecified: (:) [out-lineoutput], NotImplementedException
>     + FullyQualifiedErrorId : System.NotImplementedException,Microsoft.PowerShell.Commands.OutLineOutputCommand
> ```

## <a name="objects-in-the-pipeline"></a>Obiekty w potoku

Po uruchomieniu polecenia cmdlet programu PowerShell, zostaną wyświetlone dane wyjściowe tekstu, ponieważ jest on wymagany do reprezentowania obiektów jako tekst w oknie konsoli. Tekst wyjściowy może nie wyświetlać wszystkich właściwości obiektu są dane wyjściowe.

Na przykład, rozważmy `Get-Location` polecenia cmdlet. Jeśli uruchamiasz `Get-Location` Twojej bieżącej lokalizacji jest głównym na dysku C, zobacz następujące dane wyjściowe:

```
PS> Get-Location

Path
----
C:\
```

Tekst wyjściowy znajduje się podsumowanie informacji, nie pełną reprezentację obiektu zwróconego przez `Get-Location`. W pozycji w danych wyjściowych jest dodawany przez proces, która formatuje dane do wyświetlenia na ekranie.

Gdy przekazać dane wyjściowe do `Get-Member` polecenia cmdlet, możesz uzyskać informacje na temat obiektu zwróconego przez `Get-Location`.

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

`Get-Location` Zwraca **PATHINFO zawiera** obiekt, który zawiera bieżącą ścieżkę i inne informacje.
