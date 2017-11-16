---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Zarządzanie procesów przy użyciu poleceń cmdlet procesu"
ms.assetid: 5038f612-d149-4698-8bbb-999986959e31
ms.openlocfilehash: 3786fb77167746d6a477dffdd4ea13e863c99964
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2017
---
# <a name="managing-processes-with-process-cmdlets"></a>Zarządzanie procesów przy użyciu poleceń cmdlet procesu
Polecenia cmdlet procesów w programie Windows PowerShell umożliwiają zarządzanie procesów lokalnych i zdalnych w programie Windows PowerShell.

## <a name="getting-processes-get-process"></a>Pobieranie procesów (Get-Process)
Aby uzyskać procesów uruchomionych na komputerze lokalnym, uruchom **Get-Process** bez parametrów.

Procesy, które można uzyskać, określając ich nazwy procesu lub identyfikatorów procesów. Polecenie pobiera procesu bezczynności:

```
PS> Get-Process -id 0
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

Chociaż jest to zjawisko normalne w polecenia cmdlet, aby zwracać żadnych danych w niektórych sytuacjach po określeniu procesu przez jego identyfikator procesu, **Get-Process** generuje błąd w przypadku odnalezienia nie są zgodne, ponieważ zwykle celem jest pobrać znanego uruchomionego procesu. Jeśli nie ma żadnych procesów o takim identyfikatorze, istnieje prawdopodobieństwo, że identyfikator jest nieprawidłowy lub proces został już zakończony:

```
PS> Get-Process -Id 99
Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

Parametr Name polecenia cmdlet Get-Process służy do określania podzestawu procesów na podstawie nazwy procesu. Parametr Name może zająć wiele nazw w postaci listy rozdzielanej przecinkami i obsługuje z użyciem symboli wieloznacznych, więc możesz wpisać wzorce nazw.

Na przykład następujące polecenie pobiera procesu, których nazwy zaczynają się od "ex".

```
PS> Get-Process -Name ex*
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

Ponieważ klasa .NET System.Diagnostics.Process jest podstawą dla procesów programu Windows PowerShell, wynika z niektórych konwencje używane przez System.Diagnostics.Process. Czy nazwę pliku wykonywalnego procesu nigdy nie obejmuje ".exe" jednego z tych konwencji jest na końcu nazwy pliku wykonywalnego.

**Get-Process** również akceptuje wiele wartości dla parametru Name.

```
PS> Get-Process -Name exp*,power* 
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

Parametr ComputerName Get-Process umożliwia uzyskiwanie procesów na komputerach zdalnych. Na przykład następujące polecenie pobiera procesów programu PowerShell na komputerze lokalnym (reprezentowane przez "localhost") i na dwóch komputerach zdalnych.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

Nazwy komputerów nie są widoczne w tym wyświetlania, ale są zapisywane we właściwości MachineName obiektów procesów, które zwraca Get-Process. Polecenie używa polecenia cmdlet Format-Table do wyświetlenia Identyfikatora procesu, ProcessName i MachineName (ComputerName) właściwości obiektów procesu.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName
  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

To polecenie bardziej złożonych dodaje Właściwość MachineName do standardowego Get-Process. Backtick (\`)(ASCII 96) jest znak kontynuacji środowiska Windows PowerShell.

```
get-process powershell -computername localhost, Server01, Server02 | format-table -property Handles, `
                    @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}}, `
                    @{Label="PM(K)";Expression={[int]($_.PM/1024)}}, `
                    @{Label="WS(K)";Expression={[int]($_.WS/1024)}}, `
                    @{Label="VM(M)";Expression={[int]($_.VM/1MB)}}, `
                    @{Label="CPU(s)";Expression={if ($_.CPU -ne $()` 
                    {$_.CPU.ToString("N")}}}, `                                                                         
                    Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a>Zatrzymywanie procesów (Stop-Process)
Środowisko Windows PowerShell zapewnia elastyczność do wyświetlania procesów, ale jak zatrzymywanie procesu?

**Stop-Process** polecenia cmdlet przyjmuje nazwę lub identyfikator, aby określić, aby zatrzymać proces. Możliwość zatrzymania procesów zależy od uprawnień. Nie można zatrzymać niektórych procesów. Na przykład jeśli użytkownik spróbuje zatrzymać proces bezczynny, występuje błąd:

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

Możesz też wymusić monitowanie o **Potwierdź** parametru. Ten parametr jest szczególnie przydatne w przypadku symbolu wieloznacznego podczas określania nazwy procesu, ponieważ mogą przypadkowo zgodne niektórych procesów, których nie chcesz zatrzymać:

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

Manipulowanie złożonym procesem jest możliwe za pomocą filtrowania poleceń cmdlet Object. Ponieważ obiektu procesu ma właściwość odpowiada, która ma wartość true, jeśli nie odpowiada, można zatrzymać wszystkie aplikacje nieodpowiadający przy użyciu następującego polecenia:

```
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

W innych sytuacjach, można użyć tej samej metody. Na przykład załóżmy, że aplikacja obszaru powiadomień dodatkowej uruchamia się automatycznie po użytkownicy uruchamiają inną aplikację. Może okazać się, że to nie zadziała poprawnie w sesji usług terminalowych, ale nadal chcesz przechowywać w sesji, w konsoli fizycznego komputera z systemem. Sesje zawsze połączone na pulpicie komputera fizycznego ma identyfikator sesji 0, więc można zatrzymać wszystkich wystąpień procesu, które znajdują się w innych sesji przy użyciu **Where-Object** i ten proces, **SessionId** :

```
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

Polecenie cmdlet Stop-Process nie ma parametr ComputerName. W związku z tym aby uruchomić polecenie zatrzymania procesu na komputerze zdalnym, należy użyć polecenia cmdlet Invoke-Command. Na przykład aby zatrzymać proces programu PowerShell na komputerze zdalnym Serwer01, wpisz:

```
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a>Zatrzymanie wszystkich innych sesji programu PowerShell systemu Windows
Czasami może być warto mieć możliwość zatrzymania wszystkich uruchomionych sesji środowiska Windows PowerShell inne niż bieżącej sesji. Jeśli sesja używa zbyt wiele zasobów lub jest niedostępny (to musi być uruchomiona zdalnie lub w innej sesji pulpitu), nie można bezpośrednio Zatrzymaj ją. Próba zatrzymania wszystkich uruchomionych sesji jednak bieżąca sesja może zostać rozwiązana zamiast tego.

Każdej sesji programu Windows PowerShell zawiera zmienną środowiskową identyfikator PID procesu, który zawiera identyfikator procesu programu Windows PowerShell. Można sprawdzić $PID na podstawie identyfikatora sesji i zakończyć tylko sesji środowiska Windows PowerShell, które mają inny identyfikator. Polecenie potoku robi to i zwraca listę zakończone sesji (z powodu użycia **PassThru** parametru):

```
PS> Get-Process -Name powershell | Where-Object -FilterScript {$_.Id -ne $PID} | Stop-Process -
PassThru
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    334       9    23348      29136   143     1.03    388 powershell
    304       9    23152      29040   143     1.03    632 powershell
    302       9    20916      26804   143     1.03   1116 powershell
    335       9    25656      31412   143     1.09   3452 powershell
    303       9    23156      29044   143     1.05   3608 powershell
    287       9    21044      26928   143     1.02   3672 powershell
```

## <a name="starting-debugging-and-waiting-for-processes"></a>Uruchamianie, debugowanie i Trwa oczekiwanie na procesy
Programu Windows PowerShell jest dostarczany z poleceń cmdlet w celu uruchomienia (lub ponownego uruchomienia), również debugowania procesu i poczekaj na zakończenie przed uruchomieniem polecenia procesu. Aby uzyskać informacje o tych poleceniach cmdlet zobacz temat pomocy polecenia cmdlet poszczególnych poleceń cmdlet.

## <a name="see-also"></a>Zobacz też
- [Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)
- [Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)
- [Procesu uruchamiania](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
- [Proces oczekiwania](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
- [Proces debugowania](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
- [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)

