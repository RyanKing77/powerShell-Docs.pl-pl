---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Przekierowywanie danych przy użyciu poleceń cmdlet Out
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: 3ca7984e831a995e80cbd8a4d83ae9225c2a4f4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952124"
---
# <a name="redirecting-data-with-out--cmdlets"></a><span data-ttu-id="80f28-103">Przekierowywanie danych z Out-\* poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="80f28-103">Redirecting Data with Out-\* Cmdlets</span></span>

<span data-ttu-id="80f28-104">Środowisko Windows PowerShell udostępnia kilka polecenia cmdlet umożliwiające sterowanie danych wyjściowych bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="80f28-104">Windows PowerShell provides several cmdlets that let you control data output directly.</span></span> <span data-ttu-id="80f28-105">Te polecenia cmdlet udziału dwie najważniejsze czynniki.</span><span class="sxs-lookup"><span data-stu-id="80f28-105">These cmdlets share two important characteristics.</span></span>

<span data-ttu-id="80f28-106">Po pierwsze one zazwyczaj przekształcania danych do jakiegoś tekstu.</span><span class="sxs-lookup"><span data-stu-id="80f28-106">First, they generally transform data to some form of text.</span></span> <span data-ttu-id="80f28-107">Są to zrobić, ponieważ ich wyprowadzania danych składników systemu, które wymagają wprowadzania tekstu.</span><span class="sxs-lookup"><span data-stu-id="80f28-107">They do this because they output the data to system components that require text input.</span></span> <span data-ttu-id="80f28-108">Oznacza to, że potrzebuje do reprezentowania obiektów jako tekst.</span><span class="sxs-lookup"><span data-stu-id="80f28-108">This means they need to represent the objects as text.</span></span> <span data-ttu-id="80f28-109">W związku z tym tekst jest w formacie zostanie wyświetlony w oknie konsoli środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="80f28-109">Therefore, the text is formatted as you see it in the Windows PowerShell console window.</span></span>

<span data-ttu-id="80f28-110">Po drugie, te polecenia cmdlet użyj polecenia programu Windows PowerShell **limit** ponieważ one wysyłać informacje z programu Windows PowerShell do innych lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="80f28-110">Second, these cmdlets use the Windows PowerShell verb **Out** because they send information out from Windows PowerShell to somewhere else.</span></span> <span data-ttu-id="80f28-111">**Wyjściowego hosta** polecenie cmdlet nie jest wyjątkiem: wyświetlanie okna host znajduje się poza środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="80f28-111">The **Out-Host** cmdlet is no exception: the host window display is outside of Windows PowerShell.</span></span> <span data-ttu-id="80f28-112">Jest to ważne w przypadku, gdy dane są przesyłane z programu Windows PowerShell, faktycznie jest usunięty.</span><span class="sxs-lookup"><span data-stu-id="80f28-112">This is important because when data is sent out of Windows PowerShell, it is actually removed.</span></span> <span data-ttu-id="80f28-113">Użytkownik może wystąpić, jeśli próbuje utworzyć potok danych strony do okno hosta, a następnie spróbuj go sformatować jako listę, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="80f28-113">You can see this if you try to create a pipeline that pages data to the host window, and then attempt to format it as a list, as shown here:</span></span>

```powershell
Get-Process | Out-Host -Paging | Format-List
```

<span data-ttu-id="80f28-114">Może spodziewać się polecenie, aby wyświetlić strony informacji o procesie w formacie listy.</span><span class="sxs-lookup"><span data-stu-id="80f28-114">You might expect the command to display pages of process information in list format.</span></span> <span data-ttu-id="80f28-115">Zamiast tego umożliwia wyświetlenie listy tabelarycznej domyślne:</span><span class="sxs-lookup"><span data-stu-id="80f28-115">Instead, it displays the default tabular list:</span></span>

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

<span data-ttu-id="80f28-116">**Wyjściowego hosta** polecenia cmdlet wysyła dane bezpośrednio do konsoli programu tak **Format-Lista** polecenia nigdy nie otrzymuje żadnych czynności, aby sformatować.</span><span class="sxs-lookup"><span data-stu-id="80f28-116">The **Out-Host** cmdlet sends the data directly to the console, so the **Format-List** command never receives anything to format.</span></span>

<span data-ttu-id="80f28-117">Prawidłowy sposób struktury tego polecenia jest umieszczenie **wyjściowego hosta** polecenia cmdlet na końcu potoku, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="80f28-117">The correct way to structure this command is to put the **Out-Host** cmdlet at the end of the pipeline as shown below.</span></span> <span data-ttu-id="80f28-118">Powoduje to przetwarzania danych w liście przed stronicowana i wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="80f28-118">This causes the process data to be formatted in a list before being paged and displayed.</span></span>

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

<span data-ttu-id="80f28-119">Dotyczy to wszystkich **limit** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80f28-119">This applies to all of the **Out** cmdlets.</span></span> <span data-ttu-id="80f28-120">**Limit** polecenia cmdlet powinny zawsze występować na końcu potoku.</span><span class="sxs-lookup"><span data-stu-id="80f28-120">An **Out** cmdlet should always appear at the end of the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="80f28-121">Wszystkie **limit** poleceń cmdlet renderować dane wyjściowe jako tekst, przy użyciu formatowania obowiązująca, w oknie konsoli, łącznie z limitów długość wiersza.</span><span class="sxs-lookup"><span data-stu-id="80f28-121">All the **Out** cmdlets render output as text, using the formatting in effect for the console window, including line length limits.</span></span>

#### <a name="paging-console-output-out-host"></a><span data-ttu-id="80f28-122">Stronicowanie danych wyjściowych konsoli (wyjściowego hosta)</span><span class="sxs-lookup"><span data-stu-id="80f28-122">Paging Console Output (Out-Host)</span></span>

<span data-ttu-id="80f28-123">Domyślnie, programu Windows PowerShell wysyła dane do okna hosta, który jest dokładnie wyjściowego hosta polecenie cmdlet ma.</span><span class="sxs-lookup"><span data-stu-id="80f28-123">By default, Windows PowerShell sends data to the host window, which is exactly what the Out-Host cmdlet does.</span></span> <span data-ttu-id="80f28-124">Podstawowym zastosowaniem wyjściowego hosta polecenia cmdlet jest stronicowania danych, jak wspomniano wcześniej.</span><span class="sxs-lookup"><span data-stu-id="80f28-124">The primary use for the Out-Host cmdlet is paging data as we discussed earlier.</span></span> <span data-ttu-id="80f28-125">Na przykład następujące zastosowania polecenia wyjściowego hosta dane wyjściowe polecenia cmdlet Get-Command strony:</span><span class="sxs-lookup"><span data-stu-id="80f28-125">For example, the following command uses Out-Host to page the output of the Get-Command cmdlet:</span></span>

```powershell
Get-Command | Out-Host -Paging
```

<span data-ttu-id="80f28-126">Można również użyć **więcej** funkcji do danych strony.</span><span class="sxs-lookup"><span data-stu-id="80f28-126">You can also use the **more** function to page data.</span></span> <span data-ttu-id="80f28-127">W programie Windows PowerShell **więcej** jest funkcją, która wywołuje **wyjściowego Host-stronicowania**.</span><span class="sxs-lookup"><span data-stu-id="80f28-127">In Windows PowerShell, **more** is a function that calls **Out-Host -Paging**.</span></span> <span data-ttu-id="80f28-128">Polecenie pokazuje przy użyciu **więcej** funkcji, aby dane wyjściowe polecenia Get strony:</span><span class="sxs-lookup"><span data-stu-id="80f28-128">The following command demonstrates using the **more** function to page the output of Get-Command:</span></span>

```powershell
Get-Command | more
```

<span data-ttu-id="80f28-129">Jeśli jako argumenty funkcji więcej uwzględniony jednego lub więcej nazw plików, funkcja odczytu określonych plików i strony ich zawartość do hosta:</span><span class="sxs-lookup"><span data-stu-id="80f28-129">If you include one or more filenames as arguments to the more function, the function will read the specified files and page their contents to the host:</span></span>

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### <a name="discarding-output-out-null"></a><span data-ttu-id="80f28-130">Odrzucanie danych wyjściowych (wyjściowego o wartości Null)</span><span class="sxs-lookup"><span data-stu-id="80f28-130">Discarding Output (Out-Null)</span></span>

<span data-ttu-id="80f28-131">**Wyjściowego o wartości Null** polecenia cmdlet jest przeznaczona do natychmiast odrzucić wszystkie dane wejściowe odbiera.</span><span class="sxs-lookup"><span data-stu-id="80f28-131">The **Out-Null** cmdlet is designed to immediately discard any input it receives.</span></span> <span data-ttu-id="80f28-132">Jest to przydatne dla odrzucanie zbędne dane, który można pobrać jako efekt uboczny uruchomienia polecenia.</span><span class="sxs-lookup"><span data-stu-id="80f28-132">This is useful for discarding unnecessary data that you get as a side-effect of running a command.</span></span> <span data-ttu-id="80f28-133">Gdy wpisz następujące polecenie, nie powrócisz niczego polecenia:</span><span class="sxs-lookup"><span data-stu-id="80f28-133">When type the following command, you do not get anything back from the command:</span></span>

```powreshell
Get-Command | Out-Null
```

<span data-ttu-id="80f28-134">**Wyjściowego o wartości Null** polecenia cmdlet nie odrzucenia danych wyjściowych błędu.</span><span class="sxs-lookup"><span data-stu-id="80f28-134">The **Out-Null** cmdlet does not discard error output.</span></span> <span data-ttu-id="80f28-135">Na przykład po wprowadzeniu poniższego polecenia, zostanie wyświetlony komunikat informujący o tym, że programu Windows PowerShell nie rozpoznaje "Jest-NotACommand":</span><span class="sxs-lookup"><span data-stu-id="80f28-135">For example, if you enter the following command, a message is displayed informing you that Windows PowerShell does not recognize 'Is-NotACommand':</span></span>

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### <a name="printing-data-out-printer"></a><span data-ttu-id="80f28-136">Drukowanie danych (Out-drukarki)</span><span class="sxs-lookup"><span data-stu-id="80f28-136">Printing Data (Out-Printer)</span></span>

<span data-ttu-id="80f28-137">Dane można drukować przy użyciu **Out-drukarki** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80f28-137">You can print data by using the **Out-Printer** cmdlet.</span></span> <span data-ttu-id="80f28-138">**Out-drukarki** polecenia cmdlet będzie używać drukarki domyślnej, jeśli nie podasz nazwę drukarki.</span><span class="sxs-lookup"><span data-stu-id="80f28-138">The **Out-Printer** cmdlet will use your default printer if you do not provide a printer name.</span></span> <span data-ttu-id="80f28-139">Wszystkie drukarki z systemem Windows można użyć, określając jej nazwę wyświetlaną.</span><span class="sxs-lookup"><span data-stu-id="80f28-139">You can use any Windows-based printer by specifying its display name.</span></span> <span data-ttu-id="80f28-140">Nie istnieje potrzeba dla dowolnego rodzaju mapowania portu drukarki lub rzeczywistego fizycznej drukarki.</span><span class="sxs-lookup"><span data-stu-id="80f28-140">There is no need for any kind of printer port mapping or even a real physical printer.</span></span> <span data-ttu-id="80f28-141">Na przykład jeśli masz narzędzia obrazu dokumentu Microsoft Office, zainstalowane, należy wysłać dane do pliku obrazu, wpisując:</span><span class="sxs-lookup"><span data-stu-id="80f28-141">For example, if you have the Microsoft Office document imaging tools installed, you can send the data to an image file by typing:</span></span>

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

#### <a name="saving-data-out-file"></a><span data-ttu-id="80f28-142">Zapisywanie danych (pliku wyjściowego)</span><span class="sxs-lookup"><span data-stu-id="80f28-142">Saving Data (Out-File)</span></span>

<span data-ttu-id="80f28-143">Możesz wysłać dane wyjściowe do pliku zamiast okna konsoli za pomocą **out-file** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80f28-143">You can send output to a file instead of the console window by using the **Out-File** cmdlet.</span></span> <span data-ttu-id="80f28-144">Następujące polecenie w wierszu wysyła listę procesów do pliku **C:\\temp\\processlist.txt**:</span><span class="sxs-lookup"><span data-stu-id="80f28-144">The following command line sends a list of processes to the file **C:\\temp\\processlist.txt**:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

<span data-ttu-id="80f28-145">Wyniki za pomocą **out-file** polecenie cmdlet nie może być oczekiwać jeśli są używane do przekierowania tradycyjnych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="80f28-145">The results of using the **Out-File** cmdlet may not be what you expect if you are used to traditional output redirection.</span></span> <span data-ttu-id="80f28-146">Aby poznać jego zachowanie, musi być znane kontekst, w którym **out-file** działania polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80f28-146">To understand its behavior, you must be aware of the context in which the **Out-File** cmdlet operates.</span></span>

<span data-ttu-id="80f28-147">Domyślnie **out-file** polecenie cmdlet tworzy plik Unicode.</span><span class="sxs-lookup"><span data-stu-id="80f28-147">By default, the **Out-File** cmdlet creates a Unicode file.</span></span> <span data-ttu-id="80f28-148">W dłuższej perspektywie jest to najlepsze domyślny, ale oznacza to, że narzędzia, które oczekują plików ASCII nie będą działać poprawnie z domyślny format danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="80f28-148">This is the best default in the long run, but it means that tools that expect ASCII files will not work correctly with the default output format.</span></span> <span data-ttu-id="80f28-149">Można zmienić domyślny format danych wyjściowych ASCII przy użyciu **kodowanie** parametru:</span><span class="sxs-lookup"><span data-stu-id="80f28-149">You can change the default output format to ASCII by using the **Encoding** parameter:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

<span data-ttu-id="80f28-150">**Out-file** formatów plików zawartości, aby wyglądały jak dane wyjściowe konsoli.</span><span class="sxs-lookup"><span data-stu-id="80f28-150">**Out-file** formats file contents to look like console output.</span></span> <span data-ttu-id="80f28-151">Powoduje to, że dane wyjściowe do skrócenia dokładnie tak jak w oknie konsoli w większości przypadków.</span><span class="sxs-lookup"><span data-stu-id="80f28-151">This causes the output to be truncated just as it is in a console window in most circumstances.</span></span> <span data-ttu-id="80f28-152">Jeśli na przykład uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="80f28-152">For example, if you run the following command:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

<span data-ttu-id="80f28-153">Dane wyjściowe będą wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="80f28-153">The output will look like this:</span></span>

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

<span data-ttu-id="80f28-154">Aby uzyskać dane wyjściowe nie wymusza zawija wiersza, aby dopasować szerokości ekranu, można użyć **szerokość** parametr, aby określić szerokość linii.</span><span class="sxs-lookup"><span data-stu-id="80f28-154">To get output that does not force line wraps to match the screen width, you can use the **Width** parameter to specify line width.</span></span> <span data-ttu-id="80f28-155">Ponieważ **szerokość** parametr 32-bitowa liczba całkowita, wartość maksymalna, może mieć to 2147483647.</span><span class="sxs-lookup"><span data-stu-id="80f28-155">Because **Width** is a 32-bit integer parameter, the maximum value it can have is 2147483647.</span></span> <span data-ttu-id="80f28-156">Wpisz następujące polecenie, aby ustawić szerokość linii ta wartość maksymalna:</span><span class="sxs-lookup"><span data-stu-id="80f28-156">Type the following to set the line width to this maximum value:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

<span data-ttu-id="80f28-157">**Out-file** polecenia cmdlet jest najbardziej przydatne, gdy chcesz zapisać dane wyjściowe, jak będzie wyświetlana na konsoli.</span><span class="sxs-lookup"><span data-stu-id="80f28-157">The **Out-File** cmdlet is most useful when you want to save output as it would have displayed on the console.</span></span> <span data-ttu-id="80f28-158">Aby uzyskać bardziej precyzyjną kontrolę nad format danych wyjściowych musisz mieć bardziej zaawansowane narzędzia.</span><span class="sxs-lookup"><span data-stu-id="80f28-158">For finer control over output format, you need more advanced tools.</span></span> <span data-ttu-id="80f28-159">Przedstawiono w następnego rozdziału oraz niektóre szczegóły na temat manipulowanie obiektem.</span><span class="sxs-lookup"><span data-stu-id="80f28-159">We will look at those in the next chapter, along with some details about object manipulation.</span></span>