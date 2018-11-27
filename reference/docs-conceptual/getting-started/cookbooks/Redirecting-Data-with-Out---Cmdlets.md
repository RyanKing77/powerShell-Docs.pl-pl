---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Przekierowywanie danych przy użyciu poleceń cmdlet Out
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: f08879f436ce751b176af020aba21e90f09aa61f
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52321013"
---
# <a name="redirecting-data-with-out--cmdlets"></a><span data-ttu-id="2c836-103">Przekierowywanie danych przy użyciu Out-\* poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="2c836-103">Redirecting Data with Out-\* Cmdlets</span></span>

<span data-ttu-id="2c836-104">Windows PowerShell udostępnia kilka poleceń cmdlet umożliwiające kontrolowanie danych wyjściowych bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="2c836-104">Windows PowerShell provides several cmdlets that let you control data output directly.</span></span> <span data-ttu-id="2c836-105">Te polecenia cmdlet mają dwie istotne cech.</span><span class="sxs-lookup"><span data-stu-id="2c836-105">These cmdlets share two important characteristics.</span></span>

<span data-ttu-id="2c836-106">Najpierw są zazwyczaj przekształcania danych do jakiegoś tekstu.</span><span class="sxs-lookup"><span data-stu-id="2c836-106">First, they generally transform data to some form of text.</span></span> <span data-ttu-id="2c836-107">Mogą to zrobić, ponieważ ich dane wyjściowe do składników systemu, które wymagają wprowadzania tekstu.</span><span class="sxs-lookup"><span data-stu-id="2c836-107">They do this because they output the data to system components that require text input.</span></span> <span data-ttu-id="2c836-108">Oznacza to, które są im potrzebne do reprezentowania obiektów jako tekst.</span><span class="sxs-lookup"><span data-stu-id="2c836-108">This means they need to represent the objects as text.</span></span> <span data-ttu-id="2c836-109">W związku z tym tekst jest w formacie zostanie wyświetlony w oknie konsoli środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2c836-109">Therefore, the text is formatted as you see it in the Windows PowerShell console window.</span></span>

<span data-ttu-id="2c836-110">Po drugie, te polecenia cmdlet użyć zlecenie programu Windows PowerShell **się** ponieważ one wysyłać informacje za pomocą programu Windows PowerShell do innej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="2c836-110">Second, these cmdlets use the Windows PowerShell verb **Out** because they send information out from Windows PowerShell to somewhere else.</span></span> <span data-ttu-id="2c836-111">**Wyjściowego hosta** polecenie cmdlet nie jest wyjątkiem: wyświetlanie okna host znajduje się poza programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2c836-111">The **Out-Host** cmdlet is no exception: the host window display is outside of Windows PowerShell.</span></span> <span data-ttu-id="2c836-112">Jest to ważne, ponieważ po wysłaniu danych z programu Windows PowerShell, faktycznie jest usuwany.</span><span class="sxs-lookup"><span data-stu-id="2c836-112">This is important because when data is sent out of Windows PowerShell, it is actually removed.</span></span> <span data-ttu-id="2c836-113">Widać to w przypadku próby utworzenia potoku danych strony do okna hosta, a następnie ponów próbę sformatować je jako lista, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="2c836-113">You can see this if you try to create a pipeline that pages data to the host window, and then attempt to format it as a list, as shown here:</span></span>

```powershell
Get-Process | Out-Host -Paging | Format-List
```

<span data-ttu-id="2c836-114">Można by oczekiwać polecenia, aby wyświetlić strony informacji o procesie w formacie listy.</span><span class="sxs-lookup"><span data-stu-id="2c836-114">You might expect the command to display pages of process information in list format.</span></span> <span data-ttu-id="2c836-115">Zamiast tego Wyświetla listy tabelarycznej domyślne:</span><span class="sxs-lookup"><span data-stu-id="2c836-115">Instead, it displays the default tabular list:</span></span>

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    101       5     1076       3316    32     0.05   2888 alg
...
    618      18    39348      51108   143   211.20    740 explorer
    257       8     9752      16828    79     3.02   2560 explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="2c836-116">**Wyjściowego hosta** polecenia cmdlet wysyła dane bezpośrednio do konsoli, więc **Format-Lista** polecenia nigdy nie otrzymuje żadnych czynności, aby sformatować.</span><span class="sxs-lookup"><span data-stu-id="2c836-116">The **Out-Host** cmdlet sends the data directly to the console, so the **Format-List** command never receives anything to format.</span></span>

<span data-ttu-id="2c836-117">Poprawny sposób struktury to polecenie jest umieszczenie **wyjściowego hosta** polecenia cmdlet na końcu potoku, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="2c836-117">The correct way to structure this command is to put the **Out-Host** cmdlet at the end of the pipeline as shown below.</span></span> <span data-ttu-id="2c836-118">Powoduje to przetwarzanie danych do sformatowania przed są stronicowane i wyświetlane na liście.</span><span class="sxs-lookup"><span data-stu-id="2c836-118">This causes the process data to be formatted in a list before being paged and displayed.</span></span>

```
PS> Get-Process | Format-List | Out-Host -Paging

Id      : 2888
Handles : 101
CPU     : 0.046875
Name    : alg
...

Id      : 740
Handles : 612
CPU     : 211.703125
Name    : explorer

Id      : 2560
Handles : 257
CPU     : 3.015625
Name    : explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="2c836-119">Dotyczy to wszystkich **się** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2c836-119">This applies to all of the **Out** cmdlets.</span></span> <span data-ttu-id="2c836-120">**Się** polecenia cmdlet powinny zawsze pojawiają się na końcu potoku.</span><span class="sxs-lookup"><span data-stu-id="2c836-120">An **Out** cmdlet should always appear at the end of the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="2c836-121">Wszystkie **się** poleceń cmdlet renderowania dane wyjściowe jako tekst, przy użyciu formatowania w praktyce, w oknie konsoli, w tym wierszu długość granicach.</span><span class="sxs-lookup"><span data-stu-id="2c836-121">All the **Out** cmdlets render output as text, using the formatting in effect for the console window, including line length limits.</span></span>

#### <a name="paging-console-output-out-host"></a><span data-ttu-id="2c836-122">Stronicowanie danych wyjściowych konsoli (wyjściowego hosta)</span><span class="sxs-lookup"><span data-stu-id="2c836-122">Paging Console Output (Out-Host)</span></span>

<span data-ttu-id="2c836-123">Domyślnie środowisko Windows PowerShell wysyła dane do okna hosta, które jest dokładnie wyjściowego hosta polecenia cmdlet robi.</span><span class="sxs-lookup"><span data-stu-id="2c836-123">By default, Windows PowerShell sends data to the host window, which is exactly what the Out-Host cmdlet does.</span></span> <span data-ttu-id="2c836-124">Podstawowym zastosowaniem hostowania wyjściowego polecenia cmdlet jest stronicowanie danych, tak jak Omówiliśmy to wcześniej.</span><span class="sxs-lookup"><span data-stu-id="2c836-124">The primary use for the Out-Host cmdlet is paging data as we discussed earlier.</span></span> <span data-ttu-id="2c836-125">Na przykład następujące zastosowania polecenia wyjściowego hostowanie strony danych wyjściowych polecenia cmdlet Get-Command:</span><span class="sxs-lookup"><span data-stu-id="2c836-125">For example, the following command uses Out-Host to page the output of the Get-Command cmdlet:</span></span>

```powershell
Get-Command | Out-Host -Paging
```

<span data-ttu-id="2c836-126">Można również użyć **więcej** funkcji do danych strony.</span><span class="sxs-lookup"><span data-stu-id="2c836-126">You can also use the **more** function to page data.</span></span> <span data-ttu-id="2c836-127">W programie Windows PowerShell **więcej** jest funkcją, która wywołuje **wyjściowego hosta — stronicowania**.</span><span class="sxs-lookup"><span data-stu-id="2c836-127">In Windows PowerShell, **more** is a function that calls **Out-Host -Paging**.</span></span> <span data-ttu-id="2c836-128">Następujące polecenie, który demonstruje sposób użycia **więcej** funkcję, aby dane wyjściowe polecenia Get strony:</span><span class="sxs-lookup"><span data-stu-id="2c836-128">The following command demonstrates using the **more** function to page the output of Get-Command:</span></span>

```powershell
Get-Command | more
```

<span data-ttu-id="2c836-129">Jeśli dołączysz jeden lub więcej nazw plików jako argumenty do funkcji więcej funkcja odczytuje określone pliki i stronie ich zawartość do hosta:</span><span class="sxs-lookup"><span data-stu-id="2c836-129">If you include one or more filenames as arguments to the more function, the function will read the specified files and page their contents to the host:</span></span>

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### <a name="discarding-output-out-null"></a><span data-ttu-id="2c836-130">Odrzucanie danych wyjściowych (wyjściowego o wartości Null)</span><span class="sxs-lookup"><span data-stu-id="2c836-130">Discarding Output (Out-Null)</span></span>

<span data-ttu-id="2c836-131">**Wyjściowego o wartości Null** polecenia cmdlet jest przeznaczona do natychmiast odrzucić wszystkie dane wejściowe odbierze.</span><span class="sxs-lookup"><span data-stu-id="2c836-131">The **Out-Null** cmdlet is designed to immediately discard any input it receives.</span></span> <span data-ttu-id="2c836-132">Jest to przydatne do odrzucania niepotrzebnych dane, które otrzymujesz jako efekt uboczny uruchomienia polecenia.</span><span class="sxs-lookup"><span data-stu-id="2c836-132">This is useful for discarding unnecessary data that you get as a side-effect of running a command.</span></span> <span data-ttu-id="2c836-133">Kiedy należy wpisać następujące polecenie, nie uzyskasz żadnych powrót z polecenia:</span><span class="sxs-lookup"><span data-stu-id="2c836-133">When type the following command, you do not get anything back from the command:</span></span>

```powershell
Get-Command | Out-Null
```

<span data-ttu-id="2c836-134">**Wyjściowego o wartości Null** polecenie cmdlet nie odrzuca dane wyjściowe błędu.</span><span class="sxs-lookup"><span data-stu-id="2c836-134">The **Out-Null** cmdlet does not discard error output.</span></span> <span data-ttu-id="2c836-135">Na przykład wprowadzając następujące polecenie, zostanie wyświetlony komunikat informujący o tym, że programu Windows PowerShell nie rozpoznaje "Jest-NotACommand":</span><span class="sxs-lookup"><span data-stu-id="2c836-135">For example, if you enter the following command, a message is displayed informing you that Windows PowerShell does not recognize 'Is-NotACommand':</span></span>

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### <a name="printing-data-out-printer"></a><span data-ttu-id="2c836-136">Drukowanie danych (Out-drukarka)</span><span class="sxs-lookup"><span data-stu-id="2c836-136">Printing Data (Out-Printer)</span></span>

<span data-ttu-id="2c836-137">Wydrukować dane, używając **Out-drukarki** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2c836-137">You can print data by using the **Out-Printer** cmdlet.</span></span> <span data-ttu-id="2c836-138">**Out-drukarki** polecenia cmdlet użyje drukarki domyślnej, jeśli nie podasz nazwę drukarki.</span><span class="sxs-lookup"><span data-stu-id="2c836-138">The **Out-Printer** cmdlet will use your default printer if you do not provide a printer name.</span></span> <span data-ttu-id="2c836-139">Można użyć żadnych drukarek, systemem Windows, podając jego nazwę wyświetlaną.</span><span class="sxs-lookup"><span data-stu-id="2c836-139">You can use any Windows-based printer by specifying its display name.</span></span> <span data-ttu-id="2c836-140">Nie ma potrzeby dla każdego rodzaju mapowania portu drukarki lub rzeczywistego fizyczne drukarki.</span><span class="sxs-lookup"><span data-stu-id="2c836-140">There is no need for any kind of printer port mapping or even a real physical printer.</span></span> <span data-ttu-id="2c836-141">Na przykład jeśli narzędzia obrazowania dokumentu Microsoft Office, zainstalowane, możesz wysłać dane do pliku obrazu, wpisując:</span><span class="sxs-lookup"><span data-stu-id="2c836-141">For example, if you have the Microsoft Office document imaging tools installed, you can send the data to an image file by typing:</span></span>

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

#### <a name="saving-data-out-file"></a><span data-ttu-id="2c836-142">Zapisywanie danych (pliku wyjściowego)</span><span class="sxs-lookup"><span data-stu-id="2c836-142">Saving Data (Out-File)</span></span>

<span data-ttu-id="2c836-143">Wysłać dane wyjściowe do pliku, a nie w oknie konsoli przy użyciu **out-file** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2c836-143">You can send output to a file instead of the console window by using the **Out-File** cmdlet.</span></span> <span data-ttu-id="2c836-144">Następujące polecenie w wierszu wysyła listę procesów do pliku **C:\\temp\\processlist.txt**:</span><span class="sxs-lookup"><span data-stu-id="2c836-144">The following command line sends a list of processes to the file **C:\\temp\\processlist.txt**:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

<span data-ttu-id="2c836-145">Wyniki użycia **out-file** polecenie cmdlet nie można oczekiwać, jeśli są używane do przekierowania danych wyjściowych tradycyjnych.</span><span class="sxs-lookup"><span data-stu-id="2c836-145">The results of using the **Out-File** cmdlet may not be what you expect if you are used to traditional output redirection.</span></span> <span data-ttu-id="2c836-146">Aby poznać jej zachowanie, należy pamiętać o kontekście, w którym **out-file** działania polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2c836-146">To understand its behavior, you must be aware of the context in which the **Out-File** cmdlet operates.</span></span>

<span data-ttu-id="2c836-147">Domyślnie **out-file** polecenie cmdlet tworzy plik w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="2c836-147">By default, the **Out-File** cmdlet creates a Unicode file.</span></span> <span data-ttu-id="2c836-148">Jest to najlepsze domyślne w perspektywie długoterminowej, ale oznacza to, że narzędzia, które oczekują plików ASCII nie będą działać poprawnie przy użyciu domyślnego formatu danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="2c836-148">This is the best default in the long run, but it means that tools that expect ASCII files will not work correctly with the default output format.</span></span> <span data-ttu-id="2c836-149">Można zmienić domyślnego formatu danych wyjściowych ASCII, za pomocą **kodowanie** parametru:</span><span class="sxs-lookup"><span data-stu-id="2c836-149">You can change the default output format to ASCII by using the **Encoding** parameter:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

<span data-ttu-id="2c836-150">**Out-file** formatów plików zawartości, aby wyglądał jak na dane wyjściowe z konsoli.</span><span class="sxs-lookup"><span data-stu-id="2c836-150">**Out-file** formats file contents to look like console output.</span></span> <span data-ttu-id="2c836-151">To powoduje, że dane wyjściowe do skrócenia dokładnie tak jak w oknie konsoli, w większości przypadków.</span><span class="sxs-lookup"><span data-stu-id="2c836-151">This causes the output to be truncated just as it is in a console window in most circumstances.</span></span> <span data-ttu-id="2c836-152">Jeśli na przykład uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="2c836-152">For example, if you run the following command:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

<span data-ttu-id="2c836-153">Dane wyjściowe będą wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="2c836-153">The output will look like this:</span></span>

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

<span data-ttu-id="2c836-154">Aby uzyskać dane wyjściowe nie wymusza zawinięte, aby dopasować szerokości ekranu, można użyć **szerokość** parametru, aby określić szerokość linii.</span><span class="sxs-lookup"><span data-stu-id="2c836-154">To get output that does not force line wraps to match the screen width, you can use the **Width** parameter to specify line width.</span></span> <span data-ttu-id="2c836-155">Ponieważ **szerokość** jest parametrem 32-bitowa liczba całkowita może mieć wartość maksymalna to 2147483647.</span><span class="sxs-lookup"><span data-stu-id="2c836-155">Because **Width** is a 32-bit integer parameter, the maximum value it can have is 2147483647.</span></span> <span data-ttu-id="2c836-156">Wpisz następujące polecenie, aby ustawić szerokość linii ta wartość maksymalna:</span><span class="sxs-lookup"><span data-stu-id="2c836-156">Type the following to set the line width to this maximum value:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

<span data-ttu-id="2c836-157">**Out-file** polecenia cmdlet jest najbardziej użyteczna, gdy użytkownik chce zapisać danych wyjściowych, ponieważ może być wyświetlany w konsoli.</span><span class="sxs-lookup"><span data-stu-id="2c836-157">The **Out-File** cmdlet is most useful when you want to save output as it would have displayed on the console.</span></span> <span data-ttu-id="2c836-158">Aby uzyskać bardziej precyzyjną kontrolę nad format danych wyjściowych należy bardziej zaawansowanych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="2c836-158">For finer control over output format, you need more advanced tools.</span></span> <span data-ttu-id="2c836-159">Przyjrzymy się w następnym rozdziale, wraz z informacjami o manipulowanie obiektem.</span><span class="sxs-lookup"><span data-stu-id="2c836-159">We will look at those in the next chapter, along with some details about object manipulation.</span></span>