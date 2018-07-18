---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Wykonywanie skryptów programu PowerShell
ms.openlocfilehash: c6ba3abc2544834e2cbec16a524f79399a1d2599
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094055"
---
# <a name="powershell"></a><span data-ttu-id="4c967-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="4c967-103">PowerShell</span></span>

<span data-ttu-id="4c967-104">Oparta na programie .NET Framework, programu PowerShell jest, powłoka wiersza polecenia opartego na zadaniach oraz językiem skryptowym; jest on zaprojektowany specjalnie dla administratorów systemów i użytkownicy zaawansowani szybko zautomatyzować administracji wielu systemów operacyjnych (Linux, macOS, Unix i Windows) i procesów związanych z aplikacjami, które są uruchamiane w tych systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="4c967-104">Built on the .NET Framework, PowerShell is a task-based command-line shell and scripting language; it is designed specifically for system administrators and power-users, to rapidly automate the administration of multiple operating systems (Linux, macOS, Unix, and Windows) and the processes related to the applications that run on those operating systems.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="4c967-105">Program PowerShell jest "open source"</span><span class="sxs-lookup"><span data-stu-id="4c967-105">PowerShell is open source</span></span>

<span data-ttu-id="4c967-106">Kod źródłowy podstawowej programu PowerShell są dostępne w usłudze GitHub i otwarty, aby kod wniesiony przez społeczność.</span><span class="sxs-lookup"><span data-stu-id="4c967-106">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="4c967-107">Zobacz [źródła programu PowerShell w usłudze GitHub](https://github.com/powershell/powershell).</span><span class="sxs-lookup"><span data-stu-id="4c967-107">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="4c967-108">Można uruchomić przy użyciu usługi bits na [pobieranie programu PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span><span class="sxs-lookup"><span data-stu-id="4c967-108">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="4c967-109">Lub, z krótkiego przewodnika po [wprowadzenie](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)</span><span class="sxs-lookup"><span data-stu-id="4c967-109">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="4c967-110">Cele projektu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="4c967-110">PowerShell design goals</span></span>
<span data-ttu-id="4c967-111">Program PowerShell jest przeznaczony do dbać o środowisko wiersza polecenia i skryptów, eliminując problemy długotrwałych i dodając nowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="4c967-111">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="4c967-112">Odnajdowanie</span><span class="sxs-lookup"><span data-stu-id="4c967-112">Discoverability</span></span>
<span data-ttu-id="4c967-113">PowerShell ułatwia odnajdywanie jego funkcji.</span><span class="sxs-lookup"><span data-stu-id="4c967-113">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="4c967-114">Na przykład aby uzyskać listę poleceń cmdlet, które umożliwia wyświetlanie i zmienianie usług Windows, wpisz:</span><span class="sxs-lookup"><span data-stu-id="4c967-114">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="4c967-115">Po odkryciu, które polecenie cmdlet w ramach zadania, możesz dowiedzieć się więcej informacji na temat polecenia cmdlet przy użyciu `Get-Help` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4c967-115">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span>
<span data-ttu-id="4c967-116">Na przykład, aby wyświetlić Pomoc na temat `Get-Service` polecenia cmdlet, wpisz:</span><span class="sxs-lookup"><span data-stu-id="4c967-116">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```
<span data-ttu-id="4c967-117">Większość poleceń cmdlet emitować obiekty, które mogą być zmieniane i następnie renderowany na tekst do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="4c967-117">Most cmdlets emit objects which can be manipulated and then rendered into text for display.</span></span>
<span data-ttu-id="4c967-118">Aby w pełni zrozumieć dane wyjściowe tego polecenia cmdlet, należy przekazać dane wyjściowe do `Get-Member` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4c967-118">To fully understand the output of that cmdlet, pipe its output to the `Get-Member` cmdlet.</span></span>
<span data-ttu-id="4c967-119">Na przykład następujące polecenie wyświetla informacje o członkach dane wyjściowe obiektu przez `Get-Service` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4c967-119">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="4c967-120">Consistency</span><span class="sxs-lookup"><span data-stu-id="4c967-120">Consistency</span></span>
<span data-ttu-id="4c967-121">Systemy zarządzania mogą być złożone pozwala i narzędzia, które mają spójny interfejs ułatwiają kontrolowanie zamaskować złożoność.</span><span class="sxs-lookup"><span data-stu-id="4c967-121">Managing systems can be a complex endeavor and tools that have a consistent interface help to control the inherent complexity.</span></span>
<span data-ttu-id="4c967-122">Niestety narzędzia wiersza polecenia ani za pomocą skryptów obiektów COM nie być znane w celu zachowania ich spójności.</span><span class="sxs-lookup"><span data-stu-id="4c967-122">Unfortunately, neither command-line tools nor scriptable COM objects have been known for their consistency.</span></span>

<span data-ttu-id="4c967-123">Spójność programu PowerShell jest jednym z jego głównej zasoby.</span><span class="sxs-lookup"><span data-stu-id="4c967-123">The consistency of PowerShell is one of its primary assets.</span></span>
<span data-ttu-id="4c967-124">Na przykład, jeśli dowiesz się, jak używać `Sort-Object` polecenia cmdlet, można użyć tę wiedzę, aby posortować dane wyjściowe każdego polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4c967-124">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span>
<span data-ttu-id="4c967-125">Nie masz się różne procedury sortowania każdego polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4c967-125">You do not have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="4c967-126">Ponadto deweloperzy polecenie cmdlet nie trzeba projektować funkcje sortowania dla ich poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4c967-126">In addition, cmdlet developers do not have to design sorting features for their cmdlets.</span></span>
<span data-ttu-id="4c967-127">Program PowerShell nadaje im strukturę, która udostępnia podstawowe funkcje i wymusza, aby był spójny o wiele aspektów interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4c967-127">PowerShell gives them a framework that provides the basic features and forces them to be consistent about many aspects of the interface.</span></span>
<span data-ttu-id="4c967-128">Struktura eliminuje niektórych opcji, które zazwyczaj są pozostawiane do deweloperów, ale w zamian ułatwia rozwój niezawodne i łatwe w użyciu poleceń cmdlet znacznie prostsza.</span><span class="sxs-lookup"><span data-stu-id="4c967-128">The framework eliminates some of the choices that are typically left to the developer, but, in return, it makes the development of robust and easy-to-use cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="4c967-129">Środowiska interaktywnego i skryptów</span><span class="sxs-lookup"><span data-stu-id="4c967-129">Interactive and Scripting Environments</span></span>
<span data-ttu-id="4c967-130">PowerShell jest połączonym środowiskiem interakcyjne i skryptów, zapewnia dostęp do obiektów COM i narzędzi wiersza polecenia, a także umożliwia korzystanie z możliwości platformy .NET Framework klasy biblioteki (FCL).</span><span class="sxs-lookup"><span data-stu-id="4c967-130">PowerShell is a combined interactive and scripting environment that gives you access to command-line tools and COM objects, and also enables you to use the power of the .NET Framework Class Library (FCL).</span></span>

<span data-ttu-id="4c967-131">To środowisko zwiększa na Windows wiersza polecenia, który zapewnia środowisko interaktywne z wielu narzędzi wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="4c967-131">This environment improves upon the Windows Command Prompt, which provides an interactive environment with multiple command-line tools.</span></span>
<span data-ttu-id="4c967-132">Zapewnia on także ulepszenia skryptów Windows Script Host (WSH), które pozwalają na korzystanie z wielu narzędzi wiersza polecenia i obiektów automatyzacji COM, ale nie zapewnia interaktywne środowisko.</span><span class="sxs-lookup"><span data-stu-id="4c967-132">It also improves upon Windows Script Host (WSH) scripts, which let you use multiple command-line tools and COM automation objects, but do not provide an interactive environment.</span></span>

<span data-ttu-id="4c967-133">Łącząc dostęp do wszystkich tych funkcji, programu PowerShell rozszerza możliwości użytkownik interakcyjny i autor skryptu i sprawia, że administracja systemu jest łatwiejsze w zarządzaniu.</span><span class="sxs-lookup"><span data-stu-id="4c967-133">By combining access to all of these features, PowerShell extends the ability of the interactive user and the script writer, and makes system administration more manageable.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="4c967-134">Orientacja obiektu</span><span class="sxs-lookup"><span data-stu-id="4c967-134">Object Orientation</span></span>
<span data-ttu-id="4c967-135">Mimo że możesz korzystać przy użyciu programu PowerShell, wpisując tekst polecenia programu PowerShell jest oparty na obiektów, nie tekstu.</span><span class="sxs-lookup"><span data-stu-id="4c967-135">Although you interact with PowerShell by typing commands in text, PowerShell is based on objects, not text.</span></span>
<span data-ttu-id="4c967-136">Dane wyjściowe polecenia jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="4c967-136">The output of a command is an object.</span></span>
<span data-ttu-id="4c967-137">Obiekt danych wyjściowych do innego polecenia można wysłać jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="4c967-137">You can send the output object to another command as its input.</span></span>
<span data-ttu-id="4c967-138">W rezultacie PowerShell udostępnia znajomy interfejs do osób technicznego z systemem innymi powłok, podczas wprowadzania nowych i zaawansowanych paradygmat wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="4c967-138">As a result, PowerShell provides a familiar interface to people experienced with other shells, while introducing a new and powerful command-line paradigm.</span></span>
<span data-ttu-id="4c967-139">Rozszerza pojęcie przesyłania danych między poleceniami, umożliwiając wysyłać obiekty zamiast tekstu.</span><span class="sxs-lookup"><span data-stu-id="4c967-139">It extends the concept of sending data between commands by enabling you to send objects, rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="4c967-140">Łatwe przejście do skryptów</span><span class="sxs-lookup"><span data-stu-id="4c967-140">Easy Transition to Scripting</span></span>
<span data-ttu-id="4c967-141">Umożliwia PowerShell ułatwiają przejścia do wpisywania poleceń interaktywnie do tworzenia i uruchamiania skryptów.</span><span class="sxs-lookup"><span data-stu-id="4c967-141">PowerShell makes it easy to transition from typing commands interactively to creating and running scripts.</span></span>
<span data-ttu-id="4c967-142">Polecenia można wpisać w wierszu polecenia programu PowerShell, aby odnaleźć poleceń, które wykonują zadania.</span><span class="sxs-lookup"><span data-stu-id="4c967-142">You can type commands at the PowerShell command prompt to discover the commands that perform a task.</span></span>
<span data-ttu-id="4c967-143">Następnie można zapisać tych poleceń w transkrypcji lub historię przed skopiowaniem ich do pliku do użycia jako skrypt.</span><span class="sxs-lookup"><span data-stu-id="4c967-143">Then, you can save those commands in a transcript or a history before copying them to a file for use as a script.</span></span>
