---
ms.date: 08/27/2018
keywords: polecenia cmdlet programu PowerShell
title: Wykonywanie skryptów programu PowerShell
ms.openlocfilehash: 281f2e798b3d3fa1c150b079d633cb7e8490dcec
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685095"
---
# <a name="powershell"></a><span data-ttu-id="ea55d-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea55d-103">PowerShell</span></span>

<span data-ttu-id="ea55d-104">PowerShell jest powłoką wiersza polecenia opartego na zadaniach i język skryptowy, oparte na platformie .NET.</span><span class="sxs-lookup"><span data-stu-id="ea55d-104">PowerShell is a task-based command-line shell and scripting language built on .NET.</span></span>
<span data-ttu-id="ea55d-105">Program PowerShell ułatwia administratorom systemu i użytkownicy zaawansowani szybko Automatyzuj zarządzanych systemów operacyjnych (Linux, macOS i Windows) oraz procesy.</span><span class="sxs-lookup"><span data-stu-id="ea55d-105">PowerShell helps system administrators and power-users rapidly automate tasks that manage operating systems (Linux, macOS, and Windows) and processes.</span></span>

<span data-ttu-id="ea55d-106">Polecenia programu PowerShell umożliwiają zarządzanie komputerami z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="ea55d-106">PowerShell commands let you manage computers from the command line.</span></span> <span data-ttu-id="ea55d-107">Dostawcy programu PowerShell umożliwiają dostęp do magazynów danych, takich jak rejestr i magazyn certyfikatów, równie łatwo, jak dostęp do systemu plików.</span><span class="sxs-lookup"><span data-stu-id="ea55d-107">PowerShell providers let you access data stores, such as the registry and certificate store, as easily as you access the file system.</span></span> <span data-ttu-id="ea55d-108">Program PowerShell zawiera analizator składni wyrażeń i pełni rozwinięty język skryptowy.</span><span class="sxs-lookup"><span data-stu-id="ea55d-108">PowerShell includes a rich expression parser and a fully developed scripting language.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="ea55d-109">Program PowerShell jest typu open-source</span><span class="sxs-lookup"><span data-stu-id="ea55d-109">PowerShell is open-source</span></span>

<span data-ttu-id="ea55d-110">Kod źródłowy podstawowej programu PowerShell są dostępne w usłudze GitHub i otwarty, aby kod wniesiony przez społeczność.</span><span class="sxs-lookup"><span data-stu-id="ea55d-110">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="ea55d-111">Zobacz [źródła programu PowerShell w usłudze GitHub](https://github.com/powershell/powershell).</span><span class="sxs-lookup"><span data-stu-id="ea55d-111">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="ea55d-112">Można uruchomić przy użyciu usługi bits na [pobieranie programu PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span><span class="sxs-lookup"><span data-stu-id="ea55d-112">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="ea55d-113">Lub, z krótkiego przewodnika po [wprowadzenie](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span><span class="sxs-lookup"><span data-stu-id="ea55d-113">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="ea55d-114">Cele projektu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea55d-114">PowerShell design goals</span></span>

<span data-ttu-id="ea55d-115">Program PowerShell jest przeznaczony do dbać o środowisko wiersza polecenia i skryptów, eliminując problemy długotrwałych i dodając nowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="ea55d-115">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="ea55d-116">Odnajdowanie</span><span class="sxs-lookup"><span data-stu-id="ea55d-116">Discoverability</span></span>

<span data-ttu-id="ea55d-117">PowerShell ułatwia odnajdywanie jego funkcji.</span><span class="sxs-lookup"><span data-stu-id="ea55d-117">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="ea55d-118">Na przykład aby uzyskać listę poleceń cmdlet, które umożliwia wyświetlanie i zmienianie usług Windows, wpisz:</span><span class="sxs-lookup"><span data-stu-id="ea55d-118">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="ea55d-119">Po odkryciu, które polecenie cmdlet w ramach zadania, możesz dowiedzieć się więcej informacji na temat polecenia cmdlet przy użyciu `Get-Help` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea55d-119">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span> <span data-ttu-id="ea55d-120">Na przykład, aby wyświetlić Pomoc na temat `Get-Service` polecenia cmdlet, wpisz:</span><span class="sxs-lookup"><span data-stu-id="ea55d-120">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```

<span data-ttu-id="ea55d-121">Większość poleceń cmdlet zwracany obiektów, które mogą być zmieniane i następnie renderowany jako tekst do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="ea55d-121">Most cmdlets return objects that can be manipulated and then rendered as text for display.</span></span> <span data-ttu-id="ea55d-122">Aby w pełni zrozumieć dane wyjściowe polecenia cmdlet, należy przekazać dane wyjściowe do `Get-Member` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea55d-122">To fully understand the output of a cmdlet, pipe the output to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="ea55d-123">Na przykład następujące polecenie wyświetla informacje o członkach dane wyjściowe obiektu przez `Get-Service` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea55d-123">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="ea55d-124">Consistency</span><span class="sxs-lookup"><span data-stu-id="ea55d-124">Consistency</span></span>

<span data-ttu-id="ea55d-125">Zarządzanie systemami może być złożonym zadaniem.</span><span class="sxs-lookup"><span data-stu-id="ea55d-125">Managing systems can be a complex task.</span></span> <span data-ttu-id="ea55d-126">Narzędzia, które mają spójny interfejs ułatwiają kontrolowanie zamaskować złożoność.</span><span class="sxs-lookup"><span data-stu-id="ea55d-126">Tools that have a consistent interface help to control the inherent complexity.</span></span> <span data-ttu-id="ea55d-127">Niestety nie są znane w celu zachowania ich spójności obiektów skryptowych Component Object Model (COM) i narzędzi wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="ea55d-127">Unfortunately, command-line tools and scriptable Component Object Model (COM) objects aren't known for their consistency.</span></span>

<span data-ttu-id="ea55d-128">Spójność programu PowerShell jest jednym z jego głównej zasoby.</span><span class="sxs-lookup"><span data-stu-id="ea55d-128">The consistency of PowerShell is one of its primary assets.</span></span> <span data-ttu-id="ea55d-129">Na przykład, jeśli dowiesz się, jak używać `Sort-Object` polecenia cmdlet, można użyć tę wiedzę, aby posortować dane wyjściowe każdego polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea55d-129">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span> <span data-ttu-id="ea55d-130">Nie masz dowiedzieć się różne procedury sortowania każdego polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea55d-130">You don't have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="ea55d-131">Ponadto deweloperzy polecenie cmdlet nie trzeba projektować funkcje sortowania dla ich poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea55d-131">Additionally, cmdlet developers don't have to design sorting features for their cmdlets.</span></span> <span data-ttu-id="ea55d-132">Program PowerShell udostępnia framework z podstawowych funkcji, która wymusza spójność.</span><span class="sxs-lookup"><span data-stu-id="ea55d-132">PowerShell provides a framework with the basic features that forces consistency.</span></span> <span data-ttu-id="ea55d-133">Struktura eliminuje niektórych opcji, które są pozostawiane do deweloperów.</span><span class="sxs-lookup"><span data-stu-id="ea55d-133">The framework eliminates some choices that are left to the developer.</span></span> <span data-ttu-id="ea55d-134">Ale w zamian ułatwia rozwój poleceń cmdlet znacznie prostsza.</span><span class="sxs-lookup"><span data-stu-id="ea55d-134">But, in return, it makes the development of cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="ea55d-135">Środowiska interaktywnego i skryptów</span><span class="sxs-lookup"><span data-stu-id="ea55d-135">Interactive and scripting environments</span></span>

<span data-ttu-id="ea55d-136">Wiersz polecenia Windows zapewnia interaktywnej powłoki, dostęp do narzędzia wiersza polecenia i skrypty podstawowe.</span><span class="sxs-lookup"><span data-stu-id="ea55d-136">The Windows Command Prompt provides an interactive shell with access to command-line tools and basic scripting.</span></span> <span data-ttu-id="ea55d-137">Windows Script Host (WSH) zawiera narzędzia wiersza polecenia za pomocą skryptów i obiektów automatyzacji COM, ale nie zapewnia interaktywnej powłoki.</span><span class="sxs-lookup"><span data-stu-id="ea55d-137">Windows Script Host (WSH) has scriptable command-line tools and COM automation objects, but doesn't provide an interactive shell.</span></span>

<span data-ttu-id="ea55d-138">PowerShell łączy interaktywnej powłoki i skryptów środowiska.</span><span class="sxs-lookup"><span data-stu-id="ea55d-138">PowerShell combines an interactive shell and a scripting environment.</span></span> <span data-ttu-id="ea55d-139">PowerShell można uzyskać dostęp do narzędzia wiersza polecenia, obiekty COM i bibliotek klasy .NET.</span><span class="sxs-lookup"><span data-stu-id="ea55d-139">PowerShell can access command-line tools, COM objects, and .NET class libraries.</span></span> <span data-ttu-id="ea55d-140">Ta kombinacja funkcji rozszerza możliwości użytkownik interakcyjny, autor skryptu i administratorem systemu.</span><span class="sxs-lookup"><span data-stu-id="ea55d-140">This combination of features extends the capabilities of the interactive user, the script writer, and the system administrator.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="ea55d-141">Orientacja obiektu</span><span class="sxs-lookup"><span data-stu-id="ea55d-141">Object orientation</span></span>

<span data-ttu-id="ea55d-142">W obiekcie tekstowym nie jest oparte na programie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea55d-142">PowerShell is based on object not text.</span></span> <span data-ttu-id="ea55d-143">Dane wyjściowe polecenia jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="ea55d-143">The output of a command is an object.</span></span> <span data-ttu-id="ea55d-144">Obiekt danych wyjściowych, za pośrednictwem potoku, możesz wysłać do innego polecenia jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="ea55d-144">You can send the output object, through the pipeline, to another command as its input.</span></span>

<span data-ttu-id="ea55d-145">Ten potok zawiera znany interfejs dla osób doświadczenie w pracy z innymi powłoki.</span><span class="sxs-lookup"><span data-stu-id="ea55d-145">This pipeline provides a familiar interface for people experienced with other shells.</span></span> <span data-ttu-id="ea55d-146">Program PowerShell rozszerza tę koncepcję przez wysyłanie obiektów zamiast tekstu.</span><span class="sxs-lookup"><span data-stu-id="ea55d-146">PowerShell extends this concept by sending objects rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="ea55d-147">Łatwe przejście do skryptów</span><span class="sxs-lookup"><span data-stu-id="ea55d-147">Easy transition to scripting</span></span>

<span data-ttu-id="ea55d-148">Umożliwia odnajdowanie polecenia programu PowerShell ułatwiają przejścia do wpisywania poleceń interaktywnie do tworzenia i uruchamiania skryptów.</span><span class="sxs-lookup"><span data-stu-id="ea55d-148">PowerShell's command discoverability makes it easy to transition from typing commands interactively to creating and running scripts.</span></span> <span data-ttu-id="ea55d-149">Zapisy programu PowerShell i historię ułatwiają skopiowanie polecenia do pliku do użycia jako skrypt.</span><span class="sxs-lookup"><span data-stu-id="ea55d-149">PowerShell transcripts and history make it easy to copy commands to a file for use as a script.</span></span>
