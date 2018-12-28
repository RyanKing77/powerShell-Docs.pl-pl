---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Zmienianie widoku wyjściowego przy użyciu poleceń formatowania
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: 97d3a9e04abb61bb80a0b8c67d9fb9e885a0b91b
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405377"
---
# <a name="using-format-commands-to-change-output-view"></a>Zmienianie widoku wyjściowego przy użyciu poleceń formatowania

Programu Windows PowerShell zawiera zestaw poleceń cmdlet, które umożliwiają kontrolowanie, właściwości, które są wyświetlane dla konkretnego obiektów. Nazwy wszystkich poleceń cmdlet rozpoczynają się od zlecenie **Format**. Umożliwiają one można wybrać jedną lub więcej właściwości do wyświetlenia.

**Format** polecenia cmdlet są **całej Format**, **Format-Lista**, **Format-Table**, i **Format-niestandardowe**. Tylko opiszemy **całej Format**, **Format-Lista**, i **Format-Table** polecenia cmdlet w tym podręczniku użytkownika.

Każde polecenie cmdlet format ma domyślne właściwości, które będą używane, jeśli nie zostanie określone właściwości, aby wyświetlić. Każde polecenie cmdlet używa również taką samą nazwę parametru, **właściwości**, aby określić właściwości, które mają być wyświetlane. Ponieważ **całej Format** zawiera tylko jedną właściwość jego **właściwość** Parametr przyjmuje tylko jedną wartość, ale parametry właściwości **listy Format** i **Format-Table** przyjmuje listę nazw właściwości.

Jeśli używasz polecenia **Get-Process - powershell nazwę** z dwoma wystąpieniami uruchamianie środowiska Windows PowerShell, otrzymasz dane wyjściowe wyglądają następująco:

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

W pozostałej części tej sekcji, przeanalizujemy sposób używania **Format** poleceń cmdlet, aby zmienić sposób wyświetlania danych wyjściowych tego polecenia.

### <a name="using-format-wide-for-single-item-output"></a>Przy użyciu całej formatu dla jednego elementu danych wyjściowych

**Całej Format** polecenia cmdlet, domyślnie są wyświetlane tylko domyślne właściwości obiektu. Informacje związane z każdego obiektu, jest wyświetlany w jednej kolumnie:

```
PS> Get-Process -Name powershell | Format-Wide

powershell                              powershell
```

Można również określić właściwości inny niż domyślny:

```
PS> Get-Process -Name powershell | Format-Wide -Property Id

2760                                    3448
```

#### <a name="controlling-format-wide-display-with-column"></a>Kontrolowanie wyświetlanie całej Format za pomocą kolumny

Za pomocą **całej Format** polecenia cmdlet, możesz wyświetlić tylko jedną właściwość w danym momencie. Dzięki temu przydatne do wyświetlania listy prosty, które zawierają tylko jeden element w każdym wierszu. Aby uzyskać listę prosty, ustaw wartość **kolumny** parametru na wartość 1, wpisując:

```powershell
Get-Command Format-Wide -Property Name -Column 1
```

### <a name="using-format-list-for-a-list-view"></a>Za pomocą listy formatów dla widoku listy

**Format-Lista** polecenie cmdlet wyświetla obiektu w postaci listy, z każda właściwość etykietą i wyświetlane w osobnym wierszu:

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

#### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a>Pobieranie szczegółowe informacje przy użyciu listy Format z symbolami wieloznacznymi

**Format-Lista** polecenie cmdlet pozwala użyć symbolu wieloznacznego jako wartość jej **właściwość** parametru. Dzięki temu można wyświetlić szczegółowe informacje. Często obiekty zawierają więcej informacji niż jest Ci potrzebne, dlatego program Windows PowerShell nie uwzględnia wszystkie wartości właściwości domyślnie. Aby wyświetlić wszystkie właściwości obiektu, należy użyć **listy Format — właściwość \&#42;** polecenia. Następujące polecenie generuje ponad 60 wiersze danych wyjściowych dla pojedynczego procesu:

```powershell
Get-Process -Name powershell | Format-List -Property *
```

Mimo że **Format-Lista** polecenie jest przydatne do wyświetlania szczegółów, jeśli chcesz, aby przegląd danych wyjściowych, który zawiera wiele elementów, prostszy widok tabelaryczny jest często bardziej użyteczne.

### <a name="using-format-table-for-tabular-output"></a>Przy użyciu formatu tabeli dla tabelaryczne dane wyjściowe

Jeśli używasz **Format-Table** określić polecenia cmdlet z nie nazw właściwości, aby sformatować dane wyjściowe **Get-Process** polecenia otrzymasz dokładnie takie same dane wyjściowe, tak jak bez przeprowadzania formatowanie. Przyczyną jest to procesy są zwykle wyświetlane w formacie tabelarycznym, ponieważ większość obiektów programu Windows PowerShell.

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

#### <a name="improving-format-table-output-autosize"></a>Poprawa formatowanie tabeli danych wyjściowych (AutoSize)

Mimo że tabelaryczny widok jest przydatny do wyświetlania wielu informacji porównywalne, może być trudne do interpretacji, gdy ekran jest zbyt wąska, aby uzyskać dane. Na przykład jeśli zostanie podjęta próba ścieżka procesu, identyfikator, nazwę wyświetlaną i firmy, otrzymasz obcięte dane wyjściowe ścieżka procesu i kolumny firmy:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

Jeśli określisz **AutoSize** parametru po uruchomieniu **Format-Table** polecenia programu Windows PowerShell będzie obliczać szerokości kolumn w oparciu o rzeczywiste dane są przesyłane do wyświetlenia. To sprawia, że **ścieżki** kolumny do odczytu, ale kolumna firmy pozostaje obcięte:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

**Format-Table** polecenia cmdlet nadal może obciąć dane, ale będzie tylko dokonywać na końcu ekranu. Właściwości, innym niż ostatnio wyświetlany, otrzymują tyle rozmiaru zgodnie z zapotrzebowaniem dla ich najdłuższy elementu danych poprawnie wyświetlić. Widać, że widoczna jest nazwa firmy, ale ścieżka jest przycinany, jeśli wymiany lokalizacje **ścieżki** i **firmy** w **właściwość** listy wartości:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

**Format-Table** poleceniu założono, że nearer właściwość jest na początku listy właściwości, jest niezwykle ważne. Więc próbuje wyświetlić jej właściwości w najbliższym początku całkowicie. Jeśli **Format-Table** polecenia nie można wyświetlić wszystkie właściwości, usunąć niektóre kolumny z ekranu i odpowiedniego ostrzeżenia. Widać to zachowanie w przypadku wprowadzenia **nazwa** ostatnie właściwości na liście:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

W powyższych danych wyjściowych kolumnie identyfikator został obcięty w celu dopasowania do listy i nagłówki kolumn są ułożone w. Automatyczna zmiana rozmiaru kolumn nie zawsze są co chcesz.

#### <a name="wrapping-format-table-output-in-columns-wrap"></a>Zawijanie dane wyjściowe w formacie tabeli w kolumnach (Wrap)

Można wymusić długich **Format-Table** dane, aby opakować w jego kolumnie jest wyświetlana za pomocą **opakować** parametru. Za pomocą **opakować** parametru samodzielnie niekoniecznie nie będzie z oczekiwaniami, ponieważ używa ustawień domyślnych, jeśli nie określono również **AutoSize**:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

Zaletą korzystania z **opakować** parametru przez siebie to, że spowolnienia przetwarzanie bardzo. Przeprowadzenie listę cyklicznego pliku systemu dużego katalogu może zająć bardzo dużo czasu i używa dużej ilości pamięci, przed wyświetleniem pierwsze elementy danych wyjściowych, jeśli używasz **AutoSize**.

Jeśli nie jesteś zajmującym się ochroną obciążenia systemu, następnie **AutoSize** działa dobrze z **opakować** parametru. Kolumny początkowe są zawsze przydzielony tyle szerokość zgodnie z zapotrzebowaniem do wyświetlania elementów w jednym wierszu, tak jak w przypadku określenia **AutoSize** bez **opakować** parametru. Jedyna różnica polega na tym, że w razie potrzeby zostanie zawinięta ostatniej kolumny:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

Niektóre kolumny mogą nie być wyświetlane w przypadku określenia najszerszego kolumn najpierw więc najbezpieczniejszy najpierw określić najmniejszy elementy danych. W poniższym przykładzie określamy elementu path bardzo szeroki, najpierw, a nawet w przypadku opakowywania, firma Microsoft nadal utracić końcowe **nazwa** kolumny:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

#### <a name="organizing-table-output--groupby"></a>Organizowanie danych wyjściowych tabeli (-GroupBy)

Inny parametr przydatne dla formantu tabelaryczne dane wyjściowe jest **GroupBy**. W szczególności już ofert tabelarycznego może być trudne do porównania. **GroupBy** parametru grupy danych wyjściowych na podstawie wartości właściwości. Na przykład mamy grupy procesów przez firmę do kontroli łatwiejsze, pomijając wartość firmy na liście właściwości:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```