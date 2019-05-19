---
ms.date: 08/23/2018
keywords: polecenia cmdlet programu PowerShell
title: Opis potoki PowerShell
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: 10e09fbe8de83eba2473f8f042657f7c80473fbd
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854342"
---
# <a name="understanding-pipelines"></a><span data-ttu-id="696c3-103">Opis potoków</span><span class="sxs-lookup"><span data-stu-id="696c3-103">Understanding pipelines</span></span>

<span data-ttu-id="696c3-104">Potoki zachowywać się jak szereg podłączonych segmentów potoku.</span><span class="sxs-lookup"><span data-stu-id="696c3-104">Pipelines act like a series of connected segments of pipe.</span></span> <span data-ttu-id="696c3-105">Przenoszenie do potoku elementów przechodzi przez każdy z segmentów.</span><span class="sxs-lookup"><span data-stu-id="696c3-105">Items moving along the pipeline pass through each segment.</span></span> <span data-ttu-id="696c3-106">Aby utworzyć potok w programie PowerShell, łączenie poleceń, wraz z operatora potoku "|".</span><span class="sxs-lookup"><span data-stu-id="696c3-106">To create a pipeline in PowerShell, you connect commands together with the pipe operator "|".</span></span> <span data-ttu-id="696c3-107">Dane wyjściowe każdego polecenia jest używany jako dane wejściowe dla następnego polecenia.</span><span class="sxs-lookup"><span data-stu-id="696c3-107">The output of each command is used as input to the next command.</span></span>

<span data-ttu-id="696c3-108">Oznaczenie użyte w potokach przypomina notację używaną w innych powłoki.</span><span class="sxs-lookup"><span data-stu-id="696c3-108">The notation used for pipelines is similar to the notation used in other shells.</span></span> <span data-ttu-id="696c3-109">Na pierwszy rzut oka może nie być jasne, jak potoków różnią się w programie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="696c3-109">At first glance, it may not be apparent how pipelines are different in PowerShell.</span></span> <span data-ttu-id="696c3-110">Mimo, że tekst jest widoczne na ekranie, programu PowerShell przekazuje obiektów, nie tekstu między poleceniami.</span><span class="sxs-lookup"><span data-stu-id="696c3-110">Although you see text on the screen, PowerShell pipes objects, not text, between commands.</span></span>

## <a name="the-powershell-pipeline"></a><span data-ttu-id="696c3-111">Potoku programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="696c3-111">The PowerShell pipeline</span></span>

<span data-ttu-id="696c3-112">Potoki są prawdopodobnie najbardziej wartościowych pojęcia używane w interfejsów z wierszem polecenia.</span><span class="sxs-lookup"><span data-stu-id="696c3-112">Pipelines are arguably the most valuable concept used in command-line interfaces.</span></span> <span data-ttu-id="696c3-113">W przypadku poprawnie potoki zmniejszyć nakład pracy przy użyciu poleceń złożone i ułatwić Zobacz przepływ pracy dla poleceń.</span><span class="sxs-lookup"><span data-stu-id="696c3-113">When used properly, pipelines reduce the effort of using complex commands and make it easier to see the flow of work for the commands.</span></span> <span data-ttu-id="696c3-114">Każde polecenie w potoku (nazywany elementem potoku) przekazuje dane wyjściowe do następnego polecenia w potoku, element przez element.</span><span class="sxs-lookup"><span data-stu-id="696c3-114">Each command in a pipeline (called a pipeline element) passes its output to the next command in the pipeline, item-by-item.</span></span> <span data-ttu-id="696c3-115">Polecenia nie ma potrzeby obsługi więcej niż jeden element w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="696c3-115">Commands don't have to handle more than one item at a time.</span></span> <span data-ttu-id="696c3-116">Wynik jest użycie niższych zasobów oraz możliwość rozpocząć od razu uzyskiwanie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="696c3-116">The result is reduced resource consumption and the ability to begin getting the output immediately.</span></span>

<span data-ttu-id="696c3-117">Na przykład, jeśli używasz `Out-Host` po prostu wymusić wyświetlania strony Strona danych wyjściowych z innego polecenia, wyszukuje dane wyjściowe, takie jak zwykły tekst wyświetlany na ekranie, podzielone na strony:</span><span class="sxs-lookup"><span data-stu-id="696c3-117">For example, if you use the `Out-Host` cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

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

<span data-ttu-id="696c3-118">Stronicowanie także ogranicza wykorzystanie Procesora, ponieważ przetwarzanie przesyła do `Out-Host` polecenia cmdlet, gdy ma ona całą stronę gotowej do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="696c3-118">Paging also reduces CPU utilization because processing transfers to the `Out-Host` cmdlet when it has a complete page ready to display.</span></span> <span data-ttu-id="696c3-119">Polecenia cmdlet, które należy poprzedzić go w potoku zatrzymać wykonywanie aż do następnej strony w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="696c3-119">The cmdlets that precede it in the pipeline pause execution until the next page of output is available.</span></span>

<span data-ttu-id="696c3-120">Aby zobaczyć, jak przesyłanie potokowe ma wpływ na użycie procesora CPU i pamięci w Menedżerze zadań Windows porównując następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="696c3-120">You can see how piping impacts CPU and memory usage in the Windows Task Manager by comparing the following commands:</span></span>

- `Get-ChildItem C:\Windows -Recurse`
- `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`

> [!NOTE]
> <span data-ttu-id="696c3-121">**Stronicowania** parametr nie jest obsługiwany przez wszystkie hosty programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="696c3-121">The **Paging** parameter is not supported by all PowerShell hosts.</span></span> <span data-ttu-id="696c3-122">Na przykład podczas próby użycia **stronicowania** parametru w środowisku PowerShell ISE, zostanie wyświetlony następujący błąd:</span><span class="sxs-lookup"><span data-stu-id="696c3-122">For example, when you try to use the **Paging** parameter in the PowerShell ISE, you see the following error:</span></span>
>
> ```Output
> out-lineoutput : The method or operation is not implemented.
> At line:1 char:1
> + Get-ChildItem C:\Windows -Recurse | Out-Host -Paging
> + ~~~~~~~~~~~~~~~~~~~~~~~~~~~
>     + CategoryInfo          : NotSpecified: (:) [out-lineoutput], NotImplementedException
>     + FullyQualifiedErrorId : System.NotImplementedException,Microsoft.PowerShell.Commands.OutLineOutputCommand
> ```

## <a name="objects-in-the-pipeline"></a><span data-ttu-id="696c3-123">Obiekty w potoku</span><span class="sxs-lookup"><span data-stu-id="696c3-123">Objects in the pipeline</span></span>

<span data-ttu-id="696c3-124">Po uruchomieniu polecenia cmdlet programu PowerShell, zostaną wyświetlone dane wyjściowe tekstu, ponieważ jest on wymagany do reprezentowania obiektów jako tekst w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="696c3-124">When you run a cmdlet in PowerShell, you see text output because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="696c3-125">Tekst wyjściowy może nie wyświetlać wszystkich właściwości obiektu są dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="696c3-125">The text output may not display all of the properties of the object being output.</span></span>

<span data-ttu-id="696c3-126">Na przykład, rozważmy `Get-Location` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="696c3-126">For example, consider the `Get-Location` cmdlet.</span></span> <span data-ttu-id="696c3-127">Jeśli uruchamiasz `Get-Location` Twojej bieżącej lokalizacji jest głównym na dysku C, zobacz następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="696c3-127">If you run `Get-Location` while your current location is the root of the C drive, you see the following output:</span></span>

```
PS> Get-Location

Path
----
C:\
```

<span data-ttu-id="696c3-128">Tekst wyjściowy znajduje się podsumowanie informacji, nie pełną reprezentację obiektu zwróconego przez `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="696c3-128">The text output is a summary of information, not a complete representation of the object returned by `Get-Location`.</span></span> <span data-ttu-id="696c3-129">W pozycji w danych wyjściowych jest dodawany przez proces, która formatuje dane do wyświetlenia na ekranie.</span><span class="sxs-lookup"><span data-stu-id="696c3-129">The heading in the output is added by the process that formats the data for onscreen display.</span></span>

<span data-ttu-id="696c3-130">Gdy przekazać dane wyjściowe do `Get-Member` polecenia cmdlet, możesz uzyskać informacje na temat obiektu zwróconego przez `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="696c3-130">When you pipe the output to the `Get-Member` cmdlet you get information about the object returned by `Get-Location`.</span></span>

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

<span data-ttu-id="696c3-131">`Get-Location` Zwraca **PATHINFO zawiera** obiekt, który zawiera bieżącą ścieżkę i inne informacje.</span><span class="sxs-lookup"><span data-stu-id="696c3-131">`Get-Location` returns a **PathInfo** object that contains the current path and other information.</span></span>
