---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Zarządzanie procesami przy użyciu poleceń cmdlet procesu
ms.assetid: 5038f612-d149-4698-8bbb-999986959e31
ms.openlocfilehash: 741a3464bce6284c4933384398c4e9ddcca2572c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404717"
---
# <a name="managing-processes-with-process-cmdlets"></a>Zarządzanie procesami przy użyciu poleceń cmdlet procesu

Do zarządzania procesami lokalnych i zdalnych w programie Windows PowerShell, można użyć poleceń cmdlet procesu w programie Windows PowerShell.

## <a name="getting-processes-get-process"></a>Pobieranie procesów (Get-Process)

Aby uzyskać procesów uruchomionych na komputerze lokalnym, uruchom **Get-Process** bez parametrów.

Możesz uzyskać konkretne procesy, przez określenie ich nazwy procesu lub identyfikatorów procesów. Następujące polecenie pobiera procesu bezczynności:

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

Mimo że normalny polecenia cmdlet, aby nie zwracają danych w niektórych sytuacjach po określeniu proces, za pomocą jego ProcessId **Get-Process** generuje błąd, jeśli znajdzie nie są zgodne, ponieważ zwykle celem jest pobrać znanego, działającego procesu. Jeśli żaden proces o takim identyfikatorze jest prawdopodobne, że identyfikator jest nieprawidłowy lub odpowiedni proces został już zakończony:

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

Aby określić podzbiór procesów na podstawie nazwy procesu, można użyć parametru Name polecenia cmdlet Get-Process. Parametr Name może zająć wiele nazw na liście rozdzielanej przecinkami i obsługuje z użyciem symboli wieloznacznych, dzięki czemu można wpisać nazwę wzorców.

Na przykład następujące polecenie pobiera procesów, których nazwy zaczynają się od "np."

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

Ponieważ klasa .NET System.Diagnostics.Process jest podstawą dla procesów programu Windows PowerShell, jest zgodna z niektórych Konwencji używanych przez System.Diagnostics.Process. Czy nazwa procesu dla pliku wykonywalnego nigdy nie zawiera ".exe" jedną z tych konwencji jest na końcu nazwy pliku wykonywalnego.

**Get-Process** akceptuje także wiele wartości dla parametru Name.

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

Można użyć parametru ComputerName Get-Process, można pobrać procesów na komputerach zdalnych. Na przykład następujące polecenie pobiera procesów programu PowerShell na komputerze lokalnym (reprezentowany przez "localhost") i na dwóch komputerach zdalnych.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

Nazwy komputerów nie są widoczne w na tym ekranie, ale są one przechowywane we właściwości MachineName obiektów procesów, które zwraca Get-Process. Następujące polecenie używa polecenia cmdlet Format-Table, aby wyświetlić identyfikator procesu, ProcessName i MachineName (ComputerName) właściwości obiektów procesów.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

To bardziej złożone polecenie dodaje Właściwość MachineName do standardowego Get-Process.

```
PS> Get-Process powershell -ComputerName localhost, Server01, Server02 |
    Format-Table -Property Handles,
        @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}},
        @{Label="PM(K)";Expression={[int]($_.PM/1024)}},
        @{Label="WS(K)";Expression={[int]($_.WS/1024)}},
        @{Label="VM(M)";Expression={[int]($_.VM/1MB)}},
        @{Label="CPU(s)";Expression={if ($_.CPU -ne $()){$_.CPU.ToString("N")}}},
        Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a>Zatrzymywanie procesów (Zatrzymaj proces)

Program Windows PowerShell zapewnia elastyczność, wyświetlanie listy procesów, ale co zrobić zatrzymywanie procesu?

**Stop-Process** polecenie cmdlet przyjmuje nazwę lub identyfikator, aby określić, aby zatrzymać proces. Możliwość zatrzymać procesy zależy od uprawnień. Nie można zatrzymać niektórych procesów. Na przykład jeśli zostanie podjęta próba zatrzymać proces bezczynny, wystąpi błąd:

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

Możesz też wymusić monituje o **Potwierdź** parametru. Ten parametr jest szczególnie przydatne, jeśli możesz użyć symbolu wieloznacznego podczas określania nazwy procesu, ponieważ może przypadkowo zgodna niektóre procesy, które nie chcesz zatrzymać:

```
PS> Stop-Process -Name t*,e* -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "explorer (408)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "taskmgr (4072)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
```

Manipulowanie złożonego procesu dotyczącego jest możliwe za pomocą niektórych obiektów filtrowanie poleceń cmdlet. Ponieważ obiekt proces ma właściwość odpowiada, która ma wartość true, jeśli nie odpowiada, możesz zatrzymać wszystkie aplikacje nieodpowiadający za pomocą następującego polecenia:

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

W innych sytuacjach, można użyć tej samej metody. Na przykład załóżmy, że aplikacja obszaru powiadomień dodatkowej automatycznie uruchamia po uruchomieniu w innej aplikacji. Może się okazać, że to nie działa prawidłowo w sesji usług terminalowych, ale nadal chcesz przechowywać w sesji, które Uruchom w konsoli komputera fizycznego. Sesje połączone na pulpicie komputera fizycznego zawsze mieć identyfikator sesji, 0, więc można zatrzymać wszystkie wystąpienia procesu, które znajdują się w innych sesjach przy użyciu **Where-Object** i procesu, **SessionId** :

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

Polecenie cmdlet Stop-Process ma parametr ComputerName. W związku z tym aby uruchomić polecenie zatrzymania procesu na komputerze zdalnym, należy użyć polecenia cmdlet Invoke-Command. Na przykład aby zatrzymać proces programu PowerShell na komputerze zdalnym Serwer01, wpisz:

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a>Zatrzymanie wszystkich innych sesji programu PowerShell Windows

Od czasu do czasu może być przydatne można było zatrzymać wszystkie uruchomione sesji programu Windows PowerShell inne niż bieżąca sesja. Jeśli sesja używa zbyt wiele zasobów lub jest niedostępny (to musi być uruchomiona zdalnie, lub w innej sesji pulpitu), nie można bezpośrednio ją zatrzymać. Jeśli zostanie podjęta próba zatrzymania wszystkich uruchomionych sesji, jednak bieżąca sesja może zostać zakończona zamiast tego.

Każda sesja programu Windows PowerShell zawiera zmienną środowiskową identyfikatora PID, który zawiera identyfikator procesu programu Windows PowerShell. Należy sprawdzić $PID względem identyfikator sesji, a zakończenie tylko sesji programu Windows PowerShell, które mają inny identyfikator. Poniższe polecenie potoku dzieje i zwraca listę wszystkich sesji zakończone (z powodu użycia **PassThru** parametr):

```
PS> Get-Process -Name powershell | Where-Object -FilterScript {$_.Id -ne $PID} | Stop-Process -PassThru

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    334       9    23348      29136   143     1.03    388 powershell
    304       9    23152      29040   143     1.03    632 powershell
    302       9    20916      26804   143     1.03   1116 powershell
    335       9    25656      31412   143     1.09   3452 powershell
    303       9    23156      29044   143     1.05   3608 powershell
    287       9    21044      26928   143     1.02   3672 powershell
```

## <a name="starting-debugging-and-waiting-for-processes"></a>Uruchamianie, debugowanie oraz oczekiwanie na procesy

Programu Windows PowerShell jest dostarczany za pomocą poleceń cmdlet, aby uruchomić (lub ponownego uruchomienia), również proces debugowania i poczekaj na ukończenie przed uruchomieniem polecenia procesu. Aby uzyskać informacje o tych poleceniach cmdlet Zobacz tematu pomocy polecenia cmdlet dla każdego polecenia cmdlet.

## <a name="see-also"></a>Zobacz też

- [Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)
- [Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)
- [Rozpocznij proces](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
- [Proces oczekiwania](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
- [Proces debugowania](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
- [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)
