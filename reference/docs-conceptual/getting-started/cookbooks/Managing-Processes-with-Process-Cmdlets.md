---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Zarządzanie procesami przy użyciu poleceń cmdlet procesu
ms.assetid: 5038f612-d149-4698-8bbb-999986959e31
ms.openlocfilehash: d6d7daa810dce2d476566e4d30f03cc95bf730e6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="managing-processes-with-process-cmdlets"></a><span data-ttu-id="c75ef-103">Zarządzanie procesami przy użyciu poleceń cmdlet procesu</span><span class="sxs-lookup"><span data-stu-id="c75ef-103">Managing Processes with Process Cmdlets</span></span>

<span data-ttu-id="c75ef-104">Polecenia cmdlet procesów w programie Windows PowerShell umożliwiają zarządzanie procesów lokalnych i zdalnych w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c75ef-104">You can use the Process cmdlets in Windows PowerShell to manage local and remote processes in Windows PowerShell.</span></span>

## <a name="getting-processes-get-process"></a><span data-ttu-id="c75ef-105">Pobieranie procesów (Get-Process)</span><span class="sxs-lookup"><span data-stu-id="c75ef-105">Getting Processes (Get-Process)</span></span>

<span data-ttu-id="c75ef-106">Aby uzyskać procesów uruchomionych na komputerze lokalnym, uruchom **Get-Process** bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="c75ef-106">To get the processes running on the local computer, run a **Get-Process** with no parameters.</span></span>

<span data-ttu-id="c75ef-107">Procesy, które można uzyskać, określając ich nazwy procesu lub identyfikatorów procesów.</span><span class="sxs-lookup"><span data-stu-id="c75ef-107">You can get particular processes by specifying their process names or process IDs.</span></span> <span data-ttu-id="c75ef-108">Polecenie pobiera procesu bezczynności:</span><span class="sxs-lookup"><span data-stu-id="c75ef-108">The following command gets the Idle process:</span></span>

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

<span data-ttu-id="c75ef-109">Chociaż jest to zjawisko normalne w polecenia cmdlet, aby zwracać żadnych danych w niektórych sytuacjach po określeniu procesu przez jego identyfikator procesu, **Get-Process** generuje błąd w przypadku odnalezienia nie są zgodne, ponieważ zwykle celem jest pobrać znanego uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="c75ef-109">Although it is normal for cmdlets to return no data in some situations, when you specify a process by its ProcessId, **Get-Process** generates an error if it finds no matches, because the usual intent is to retrieve a known running process.</span></span> <span data-ttu-id="c75ef-110">Jeśli nie ma żadnych procesów o takim identyfikatorze, istnieje prawdopodobieństwo, że identyfikator jest nieprawidłowy lub proces został już zakończony:</span><span class="sxs-lookup"><span data-stu-id="c75ef-110">If there is no process with that Id, it is likely that the Id is incorrect or that the process of interest has already exited:</span></span>

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

<span data-ttu-id="c75ef-111">Parametr Name polecenia cmdlet Get-Process służy do określania podzestawu procesów na podstawie nazwy procesu.</span><span class="sxs-lookup"><span data-stu-id="c75ef-111">You can use the Name parameter of the Get-Process cmdlet to specify a subset of processes based on the process name.</span></span> <span data-ttu-id="c75ef-112">Parametr Name może zająć wiele nazw w postaci listy rozdzielanej przecinkami i obsługuje z użyciem symboli wieloznacznych, więc możesz wpisać wzorce nazw.</span><span class="sxs-lookup"><span data-stu-id="c75ef-112">The Name parameter can take multiple names in a comma-separated list and it supports the use of wildcards, so you can type name patterns.</span></span>

<span data-ttu-id="c75ef-113">Na przykład następujące polecenie pobiera procesu, których nazwy zaczynają się od "ex".</span><span class="sxs-lookup"><span data-stu-id="c75ef-113">For example, the following command gets process whose names begin with "ex."</span></span>

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

<span data-ttu-id="c75ef-114">Ponieważ klasa .NET System.Diagnostics.Process jest podstawą dla procesów programu Windows PowerShell, wynika z niektórych konwencje używane przez System.Diagnostics.Process.</span><span class="sxs-lookup"><span data-stu-id="c75ef-114">Because the .NET System.Diagnostics.Process class is the foundation for Windows PowerShell processes, it follows some of the conventions used by System.Diagnostics.Process.</span></span> <span data-ttu-id="c75ef-115">Czy nazwę pliku wykonywalnego procesu nigdy nie obejmuje ".exe" jednego z tych konwencji jest na końcu nazwy pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="c75ef-115">One of those conventions is that the process name for an executable never includes the ".exe" at the end of the executable name.</span></span>

<span data-ttu-id="c75ef-116">**Get-Process** również akceptuje wiele wartości dla parametru Name.</span><span class="sxs-lookup"><span data-stu-id="c75ef-116">**Get-Process** also accepts multiple values for the Name parameter.</span></span>

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="c75ef-117">Parametr ComputerName Get-Process umożliwia uzyskiwanie procesów na komputerach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="c75ef-117">You can use the ComputerName parameter of Get-Process to get processes on remote computers.</span></span> <span data-ttu-id="c75ef-118">Na przykład następujące polecenie pobiera procesów programu PowerShell na komputerze lokalnym (reprezentowane przez "localhost") i na dwóch komputerach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="c75ef-118">For example, the following command gets the PowerShell processes on the local computer (represented by "localhost") and on two remote computers.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="c75ef-119">Nazwy komputerów nie są widoczne w tym wyświetlania, ale są zapisywane we właściwości MachineName obiektów procesów, które zwraca Get-Process.</span><span class="sxs-lookup"><span data-stu-id="c75ef-119">The computer names are not evident in this display, but they are stored in the MachineName property of the process objects that Get-Process returns.</span></span> <span data-ttu-id="c75ef-120">Polecenie używa polecenia cmdlet Format-Table do wyświetlenia Identyfikatora procesu, ProcessName i MachineName (ComputerName) właściwości obiektów procesu.</span><span class="sxs-lookup"><span data-stu-id="c75ef-120">The following command uses the Format-Table cmdlet to display the process ID, ProcessName and MachineName (ComputerName) properties of the process objects.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

<span data-ttu-id="c75ef-121">To polecenie bardziej złożonych dodaje Właściwość MachineName do standardowego Get-Process.</span><span class="sxs-lookup"><span data-stu-id="c75ef-121">This more complex command adds the MachineName property to the standard Get-Process display.</span></span>

```
PS> Get-Process powershell -ComputerName localhost, Server01, Server02 |
    Format-Table -Property Handles,
        @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}},
        @{Label="PM(K)";Expression={[int]($_.PM/1024)}},
        @{Label="WS(K)";Expression={[int]($_.WS/1024)}},
        @{Label="VM(M)";Expression={[int]($_.VM/1MB)}},
        @{Label="CPU(s)";Expression={if ($_.CPU -ne $() {$_.CPU.ToString("N")}}},
        Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a><span data-ttu-id="c75ef-122">Zatrzymywanie procesów (Stop-Process)</span><span class="sxs-lookup"><span data-stu-id="c75ef-122">Stopping Processes (Stop-Process)</span></span>

<span data-ttu-id="c75ef-123">Środowisko Windows PowerShell zapewnia elastyczność do wyświetlania procesów, ale jak zatrzymywanie procesu?</span><span class="sxs-lookup"><span data-stu-id="c75ef-123">Windows PowerShell gives you flexibility for listing processes, but what about stopping a process?</span></span>

<span data-ttu-id="c75ef-124">**Stop-Process** polecenia cmdlet przyjmuje nazwę lub identyfikator, aby określić, aby zatrzymać proces.</span><span class="sxs-lookup"><span data-stu-id="c75ef-124">The **Stop-Process** cmdlet takes a Name or Id to specify a process you want to stop.</span></span> <span data-ttu-id="c75ef-125">Możliwość zatrzymania procesów zależy od uprawnień.</span><span class="sxs-lookup"><span data-stu-id="c75ef-125">Your ability to stop processes depends on your permissions.</span></span> <span data-ttu-id="c75ef-126">Nie można zatrzymać niektórych procesów.</span><span class="sxs-lookup"><span data-stu-id="c75ef-126">Some processes cannot be stopped.</span></span> <span data-ttu-id="c75ef-127">Na przykład jeśli użytkownik spróbuje zatrzymać proces bezczynny, występuje błąd:</span><span class="sxs-lookup"><span data-stu-id="c75ef-127">For example, if you try to stop the idle process, you get an error:</span></span>

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

<span data-ttu-id="c75ef-128">Możesz też wymusić monitowanie o **Potwierdź** parametru.</span><span class="sxs-lookup"><span data-stu-id="c75ef-128">You can also force prompting with the **Confirm** parameter.</span></span> <span data-ttu-id="c75ef-129">Ten parametr jest szczególnie przydatne w przypadku symbolu wieloznacznego podczas określania nazwy procesu, ponieważ mogą przypadkowo zgodne niektórych procesów, których nie chcesz zatrzymać:</span><span class="sxs-lookup"><span data-stu-id="c75ef-129">This parameter is particularly useful if you use a wildcard when specifying the process name, because you may accidentally match some processes you do not want to stop:</span></span>

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

<span data-ttu-id="c75ef-130">Manipulowanie złożonym procesem jest możliwe za pomocą filtrowania poleceń cmdlet Object.</span><span class="sxs-lookup"><span data-stu-id="c75ef-130">Complex process manipulation is possible by using some of the object filtering cmdlets.</span></span> <span data-ttu-id="c75ef-131">Ponieważ obiektu procesu ma właściwość odpowiada, która ma wartość true, jeśli nie odpowiada, można zatrzymać wszystkie aplikacje nieodpowiadający przy użyciu następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="c75ef-131">Because a Process object has a Responding property that is true when it is no longer responding, you can stop all nonresponsive applications with the following command:</span></span>

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

<span data-ttu-id="c75ef-132">W innych sytuacjach, można użyć tej samej metody.</span><span class="sxs-lookup"><span data-stu-id="c75ef-132">You can use the same approach in other situations.</span></span> <span data-ttu-id="c75ef-133">Na przykład załóżmy, że aplikacja obszaru powiadomień dodatkowej uruchamia się automatycznie po użytkownicy uruchamiają inną aplikację.</span><span class="sxs-lookup"><span data-stu-id="c75ef-133">For example, suppose a secondary notification area application automatically runs when users start another application.</span></span> <span data-ttu-id="c75ef-134">Może okazać się, że to nie zadziała poprawnie w sesji usług terminalowych, ale nadal chcesz przechowywać w sesji, w konsoli fizycznego komputera z systemem.</span><span class="sxs-lookup"><span data-stu-id="c75ef-134">You may find that this does not work correctly in Terminal Services sessions, but you still want to keep it in sessions that run on the physical computer console.</span></span> <span data-ttu-id="c75ef-135">Sesje zawsze połączone na pulpicie komputera fizycznego ma identyfikator sesji 0, więc można zatrzymać wszystkich wystąpień procesu, które znajdują się w innych sesji przy użyciu **Where-Object** i ten proces, **SessionId** :</span><span class="sxs-lookup"><span data-stu-id="c75ef-135">Sessions connected to the physical computer desktop always have a session ID of 0, so you can stop all instances of the process that are in other sessions by using **Where-Object** and the process, **SessionId**:</span></span>

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

<span data-ttu-id="c75ef-136">Polecenie cmdlet Stop-Process nie ma parametr ComputerName.</span><span class="sxs-lookup"><span data-stu-id="c75ef-136">The Stop-Process cmdlet does not have a ComputerName parameter.</span></span> <span data-ttu-id="c75ef-137">W związku z tym aby uruchomić polecenie zatrzymania procesu na komputerze zdalnym, należy użyć polecenia cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="c75ef-137">Therefore, to run a stop process command on a remote computer, you need to use the Invoke-Command cmdlet.</span></span> <span data-ttu-id="c75ef-138">Na przykład aby zatrzymać proces programu PowerShell na komputerze zdalnym Serwer01, wpisz:</span><span class="sxs-lookup"><span data-stu-id="c75ef-138">For example, to stop the PowerShell process on the Server01 remote computer, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a><span data-ttu-id="c75ef-139">Zatrzymanie wszystkich innych sesji programu PowerShell systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c75ef-139">Stopping All Other Windows PowerShell Sessions</span></span>

<span data-ttu-id="c75ef-140">Czasami może być warto mieć możliwość zatrzymania wszystkich uruchomionych sesji środowiska Windows PowerShell inne niż bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="c75ef-140">It may occasionally be useful to be able to stop all running Windows PowerShell sessions other than the current session.</span></span> <span data-ttu-id="c75ef-141">Jeśli sesja używa zbyt wiele zasobów lub jest niedostępny (to musi być uruchomiona zdalnie lub w innej sesji pulpitu), nie można bezpośrednio Zatrzymaj ją.</span><span class="sxs-lookup"><span data-stu-id="c75ef-141">If a session is using too many resources or is inaccessible (it may be running remotely or in another desktop session), you may not be able to directly stop it.</span></span> <span data-ttu-id="c75ef-142">Próba zatrzymania wszystkich uruchomionych sesji jednak bieżąca sesja może zostać rozwiązana zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="c75ef-142">If you try to stop all running sessions, however, the current session may be terminated instead.</span></span>

<span data-ttu-id="c75ef-143">Każdej sesji programu Windows PowerShell zawiera zmienną środowiskową identyfikator PID procesu, który zawiera identyfikator procesu programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c75ef-143">Each Windows PowerShell session has an environment variable PID that contains the Id of the Windows PowerShell process.</span></span> <span data-ttu-id="c75ef-144">Można sprawdzić $PID na podstawie identyfikatora sesji i zakończyć tylko sesji środowiska Windows PowerShell, które mają inny identyfikator. Polecenie potoku robi to i zwraca listę zakończone sesji (z powodu użycia **PassThru** parametru):</span><span class="sxs-lookup"><span data-stu-id="c75ef-144">You can check the $PID against the Id of each session and terminate only Windows PowerShell sessions that have a different Id. The following pipeline command does this and returns the list of terminated sessions (because of the use of the **PassThru** parameter):</span></span>

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

## <a name="starting-debugging-and-waiting-for-processes"></a><span data-ttu-id="c75ef-145">Uruchamianie, debugowanie i Trwa oczekiwanie na procesy</span><span class="sxs-lookup"><span data-stu-id="c75ef-145">Starting, Debugging, and Waiting for Processes</span></span>

<span data-ttu-id="c75ef-146">Programu Windows PowerShell jest dostarczany z poleceń cmdlet w celu uruchomienia (lub ponownego uruchomienia), również debugowania procesu i poczekaj na zakończenie przed uruchomieniem polecenia procesu.</span><span class="sxs-lookup"><span data-stu-id="c75ef-146">Windows PowerShell also comes with cmdlets to start (or restart), debug a process, and wait for a process to complete before running a command.</span></span> <span data-ttu-id="c75ef-147">Aby uzyskać informacje o tych poleceniach cmdlet zobacz temat pomocy polecenia cmdlet poszczególnych poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c75ef-147">For information about these cmdlets, see the cmdlet help topic for each cmdlet.</span></span>

## <a name="see-also"></a><span data-ttu-id="c75ef-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c75ef-148">See Also</span></span>

- <span data-ttu-id="c75ef-149">[Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)</span><span class="sxs-lookup"><span data-stu-id="c75ef-149">[Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)</span></span>
- <span data-ttu-id="c75ef-150">[Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)</span><span class="sxs-lookup"><span data-stu-id="c75ef-150">[Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)</span></span>
- [<span data-ttu-id="c75ef-151">Procesu uruchamiania</span><span class="sxs-lookup"><span data-stu-id="c75ef-151">Start-Process</span></span>](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
- [<span data-ttu-id="c75ef-152">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="c75ef-152">Wait-Process</span></span>](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
- [<span data-ttu-id="c75ef-153">Proces debugowania</span><span class="sxs-lookup"><span data-stu-id="c75ef-153">Debug-Process</span></span>](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
- [<span data-ttu-id="c75ef-154">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="c75ef-154">Invoke-Command</span></span>](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)