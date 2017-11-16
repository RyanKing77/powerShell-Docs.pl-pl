---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Za pomocą polecenia zmiany formatu danych wyjściowych widoku"
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: 0163fcb21d586fc98902d9bdcfab6fe4eb97c225
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2017
---
# <a name="using-format-commands-to-change-output-view"></a>Za pomocą polecenia zmiany formatu danych wyjściowych widoku
Środowisko Windows PowerShell jest zestaw poleceń cmdlet, które umożliwiają kontrolowanie właściwości, które są wyświetlane dla konkretnego obiektów. Nazwy wszystkich poleceń cmdlet zaczynają się od zlecenie **Format**. Umożliwiają one wybierz jedną lub więcej właściwości do wyświetlenia.

**Format** polecenia cmdlet są **całej Format**, **Format-Lista**, **Format-Table**, i **Format-niestandardowe**. Zostaną przedstawione tylko **całej Format**, **Format-Lista**, i **Format-Table** polecenia cmdlet w tym podręczniku użytkownika.

Każde polecenie cmdlet format ma domyślne właściwości, które zostaną użyte, jeśli nie określisz określonych właściwości do wyświetlenia. Każde polecenie cmdlet używa również nazwę tego samego parametru **właściwości**, aby określić właściwości, które mają być wyświetlane. Ponieważ **całej Format** przedstawia tylko jedną właściwość jego **właściwości** Parametr przyjmuje tylko pojedynczą wartość, ale parametry właściwości **listy Format** i **Format-Table** przyjmuje listę nazw właściwości.

Jeśli używasz polecenia **Get-Process - powershell nazwę** z dwoma wystąpieniami programu Windows PowerShell działa, możesz uzyskać dane wyjściowe, która wygląda następująco:

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

W dalszej części tej sekcji, przeanalizujemy sposobu używania **Format** polecenia cmdlet, aby zmienić sposób wyświetlania danych wyjściowych tego polecenia.

### <a name="using-format-wide-for-single-item-output"></a>Przy użyciu formatu na poziomie dla danych wyjściowych jednego elementu
**Całej Format** polecenia cmdlet, domyślnie są wyświetlane tylko domyślnej właściwości obiektu. Informacje skojarzone z każdego obiektu są wyświetlane w jednej kolumnie:

```
PS> Get-Process -Name powershell | Format-Wide

powershell                              powershell
```

Można również określić właściwości innych niż domyślne:

```
PS> Get-Process -Name powershell | Format-Wide -Property Id

2760                                    3448
```

#### <a name="controlling-format-wide-display-with-column"></a>Kontrolowanie Format całej wyświetlana z kolumną
Z **całej Format** polecenia cmdlet, możesz wyświetlić tylko jedną właściwość naraz. Dzięki temu przydatne do wyświetlania listy proste, które zawierają tylko jeden element w jednym wierszu. Aby uzyskać listę proste, ustaw wartość **kolumny** parametru na wartość 1, wpisując:

```
Get-Command Format-Wide -Property Name -Column 1
```

### <a name="using-format-list-for-a-list-view"></a>Przy użyciu listy Format dla widoku listy
**Format-Lista** polecenie cmdlet wyświetla obiektu w postaci listy, z każdej właściwości z etykietą i wyświetlane w oddzielnym wierszu:

```
PS> Get-Process -Name powershell | Format-List

Id      : 2760
Handles : 1242
CPU     : 3.03125
Name    : powershell

Id      : 3448
Handles : 328
CPU     : 1.0625
Name    : powershell
```

Można określić dowolną liczbę właściwości:

```
PS> Get-Process -Name powershell | Format-List -Property ProcessName,FileVersion
,StartTime,Id

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:42:00
Id          : 2760

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:54:28
Id          : 3448
```

#### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a>Pobieranie szczegółowych informacji przy użyciu listy formatów z symbolami wieloznacznymi
**Format-Lista** polecenie cmdlet pozwala używać symboli wieloznacznych jako wartości jego **właściwości** parametru. Dzięki temu można wyświetlić szczegółowe informacje. Często obiekty zawierają więcej informacji niż to konieczne, dlatego środowiska Windows PowerShell nie są wyświetlane wszystkie wartości właściwości domyślnie. Aby wyświetlić wszystkie właściwości obiektu, należy użyć **listy Format — właściwość \&#42;** polecenia. Polecenie generuje ponad 60 wiersze danych wyjściowych dla pojedynczego procesu:

```
Get-Process -Name powershell | Format-List -Property *
```

Mimo że **Format-Lista** polecenie jest przydatne do wyświetlania szczegółów, jeśli chcesz przejrzeć dane wyjściowe, który zawiera wiele elementów prostsze widoku tabelarycznego jest często bardziej użyteczne.

### <a name="using-format-table-for-tabular-output"></a>Przy użyciu formatu tabeli dla tabelaryczne dane wyjściowe
Jeśli używasz **Format-Table** określone polecenie cmdlet z żadnych nazw właściwości do formatowania danych wyjściowych **Get-Process** polecenia Pobierz dokładnie takie same dane wyjściowe, jak bez formatowania. Dzieje się tak że procesy są zwykle wyświetlane w formacie tabelarycznym są większość obiektów programu Windows PowerShell.

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

#### <a name="improving-format-table-output-autosize"></a>Poprawa tabeli Format danych wyjściowych (AutoSize)
Mimo że widoku tabelarycznego jest przydatne w przypadku wyświetlania wielu porównywalne informacji, może być trudne interpretować Jeśli ekran jest zbyt ograniczone danych. Na przykład próba ścieżka procesu, identyfikator, nazwę wyświetlaną i firmy, możesz uzyskać skróconą dane wyjściowe ścieżka procesu i kolumn firmy:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

Jeśli określisz **AutoSize** parametru podczas uruchamiania **Format-Table** poleceń programu Windows PowerShell obliczy szerokości kolumn na podstawie rzeczywistych danych mają być wyświetlane. Dzięki temu **ścieżki** skróconą pozostaje kolumnę do odczytu, ale kolumna firmy:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

**Format-Table** polecenia cmdlet nadal może obciąć danych, ale będzie tylko dokonywać na końcu ekranu. Właściwości, innym niż ostatnio wyświetlane, są podane tyle rozmiar potrzebują ich najdłuższym elementu danych do poprawnego wyświetlania. Widać, że nazwa firmy jest widoczny, ale ścieżka zostanie obcięta, jeśli wymiany lokalizacje **ścieżki** i **firmy** w **właściwości** listy wartości:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

**Format-Table** poleceniu założono, że nearer właściwości znajduje się na początku listy właściwości jest ważniejsze. Dlatego próbuje wyświetlić właściwości najbliższej początku całkowicie. Jeśli **Format-Table** polecenia nie można wyświetlić wszystkie właściwości, będzie usunąć niektóre kolumny z ekranu i ostrzeżenie. To zachowanie można wyświetlić, musisz wprowadzić **nazwa** ostatnich właściwości na liście:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

W powyższych danych wyjściowych w kolumnie identyfikator został obcięty w celu dopasowania do listy, a nagłówki kolumn są ułożone w. Automatyczna zmiana rozmiaru kolumn zawsze nie chcesz.

#### <a name="wrapping-format-table-output-in-columns-wrap"></a>Zawijanie tabeli Format danych wyjściowych w kolumnach (zawijania)
Możesz wymusić, długotrwałą **Format-Table** danych do zakodowania w jego kolumnie jest wyświetlana przy użyciu **zawijanie** parametru. Przy użyciu **zawijanie** samego parametru niekoniecznie nie ma oczekiwanego, ponieważ wykorzystuje ustawienia domyślne, jeśli nie określono również **AutoSize**:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

Zaletą używania **zawijanie** parametr samodzielnie jest, że spowolnienia przetwarzania bardzo. Jeśli na liście plików cykliczne systemu dużego katalogu, może zająć bardzo dużo czasu i używać dużej ilości pamięci, przed wyświetleniem pierwsze elementów danych wyjściowych, jeśli używasz **AutoSize**.

Jeśli nie masz obawy obciążenia systemu, następnie **AutoSize** dobrze działa z **zawijanie** parametru. Początkowych kolumn zawsze są przydzielony tyle szerokość potrzebują do wyświetlania elementów w jednym wierszu, tak jak w przypadku określenia **AutoSize** bez **zawijanie** parametru. Jedyna różnica polega na tym, że w razie potrzeby zostaną opakowane ostatniej kolumny:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

Niektóre kolumny mogą nie być wyświetlane określenia najszerszego kolumn, dlatego jest najbezpieczniejszy określić najmniejszy elementy danych w pierwszej kolejności. W poniższym przykładzie, możemy Określ elementu bardzo szeroki ścieżki najpierw, a nawet z zawijaniem, będziemy nadal utratę ostatecznego **nazwa** kolumny:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

#### <a name="organizing-table-output--groupby"></a>Organizowanie w tabeli danych wyjściowych (-GroupBy)
Inny parametr przydatne do kontroli tabelaryczne dane wyjściowe jest **GroupBy**. W szczególności już tabelarycznych listy może być trudne do porównania. **GroupBy** parametru grupuje dane wyjściowe na podstawie wartości właściwości. Na przykład możemy grupy procesów przez firmę do kontroli łatwiejsze, pomijając wartość firmy z listy właściwości:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```

