---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Wprowadzenie do programu PowerShell Konfiguracja żądanego stanu
ms.openlocfilehash: a449382c979e680ea311c887c86cb675ba6162b7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="getting-started-with-powershell-desired-state-configuration"></a><span data-ttu-id="49e57-103">Wprowadzenie do programu PowerShell Konfiguracja żądanego stanu</span><span class="sxs-lookup"><span data-stu-id="49e57-103">Getting Started with PowerShell Desired State Configuration</span></span> #

<span data-ttu-id="49e57-104">W tym przewodniku opisano, jak rozpocząć tworzenie dokumentów konfiguracji żądanego stanu środowiska PowerShell i zastosować je do maszyny.</span><span class="sxs-lookup"><span data-stu-id="49e57-104">This guide describes how to begin creating PowerShell Desired State Configuration documents and apply them to machines.</span></span> <span data-ttu-id="49e57-105">Zakłada się znajomość podstawowych poleceń cmdlet programu PowerShell, moduły i funkcje.</span><span class="sxs-lookup"><span data-stu-id="49e57-105">It assumes basic familiarity with PowerShell cmdlets, modules, and functions.</span></span>


## <a name="create-a-configuration"></a><span data-ttu-id="49e57-106">Tworzenie konfiguracji</span><span class="sxs-lookup"><span data-stu-id="49e57-106">Create a Configuration</span></span> ##

<span data-ttu-id="49e57-107">[**Konfiguracje** ](https://msdn.microsoft.com/powershell/dsc/configurations) dokumentów, które opisują środowiska.</span><span class="sxs-lookup"><span data-stu-id="49e57-107">[**Configurations**](https://msdn.microsoft.com/powershell/dsc/configurations) are documents that describe an environment.</span></span> <span data-ttu-id="49e57-108">Środowiskach składają się z "**węzłów**", które są często maszyn wirtualnych lub fizycznych.</span><span class="sxs-lookup"><span data-stu-id="49e57-108">Environments consist of "**nodes**", which are commonly virtual or physical machines.</span></span>

<span data-ttu-id="49e57-109">Konfiguracje mogą mieć różne formy.</span><span class="sxs-lookup"><span data-stu-id="49e57-109">Configurations can come in a variety of forms.</span></span> <span data-ttu-id="49e57-110">Najprostszym sposobem tworzenia nowej konfiguracji jest tworzenie pliku .ps1 (skrypt programu PowerShell).</span><span class="sxs-lookup"><span data-stu-id="49e57-110">The easiest way to create a new configuration is to create a .ps1 (PowerShell script) file.</span></span> <span data-ttu-id="49e57-111">Aby to zrobić, Otwórz Edytor wybór.</span><span class="sxs-lookup"><span data-stu-id="49e57-111">To do this, open your editor of choice.</span></span> <span data-ttu-id="49e57-112">PowerShell ISE jest dobrym rozwiązaniem, ponieważ rozumie DSC natywnie.</span><span class="sxs-lookup"><span data-stu-id="49e57-112">The PowerShell ISE is a good choice, since it understands DSC natively.</span></span> <span data-ttu-id="49e57-113">Zapisz poniższy jako PS1:</span><span class="sxs-lookup"><span data-stu-id="49e57-113">Save the following as a PS1:</span></span>

```powershell
configuration MyFirstConfiguration
{
    Import-DscResource -Name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }

    }

}
```
## <a name="parts-of-a-configuration"></a><span data-ttu-id="49e57-114">Elementy konfiguracji</span><span class="sxs-lookup"><span data-stu-id="49e57-114">Parts of a Configuration</span></span> ##
<span data-ttu-id="49e57-115">**Konfiguracja** jest słowem kluczowym, który został dodany do programu PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="49e57-115">**Configuration** is a keyword that has been added to PowerShell 4.0.</span></span> <span data-ttu-id="49e57-116">Oznacza on specjalny rodzaj funkcji programu PowerShell używanego przez konfiguracji żądanego stanu.</span><span class="sxs-lookup"><span data-stu-id="49e57-116">It signifies a special kind of PowerShell function used by Desired State Configuration.</span></span> <span data-ttu-id="49e57-117">W tym przykładzie funkcja nosi nazwę myFirstConfiguration.</span><span class="sxs-lookup"><span data-stu-id="49e57-117">In this example, the function is named myFirstConfiguration.</span></span>

<span data-ttu-id="49e57-118">Następnego wiersza jest instrukcję import, podobnie jak importowanie modułu.</span><span class="sxs-lookup"><span data-stu-id="49e57-118">The next line is an import statement, similar to importing a module.</span></span> <span data-ttu-id="49e57-119">Będzie można omówione później.</span><span class="sxs-lookup"><span data-stu-id="49e57-119">It will be discussed later on.</span></span>

<span data-ttu-id="49e57-120">"Węzeł" definiuje nazwę komputera, które będą działać tej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="49e57-120">"Node" defines the machine name this configuration will act on.</span></span> <span data-ttu-id="49e57-121">Chociaż ta konfiguracja jest edytowany lokalnie, konfiguracje mogą dotrzeć do zdalnego węzłów i skonfigurować je.</span><span class="sxs-lookup"><span data-stu-id="49e57-121">Although this configuration is edited locally, configurations can reach out to remote nodes and configure them.</span></span>

<span data-ttu-id="49e57-122">Węzły mogą być nazwy komputerów lub adresy IP.</span><span class="sxs-lookup"><span data-stu-id="49e57-122">Nodes can be machine names or IP addresses.</span></span> <span data-ttu-id="49e57-123">Może mieć wiele węzłów w dokumencie pojedynczą konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="49e57-123">You can have multiple nodes in a single configuration document.</span></span> <span data-ttu-id="49e57-124">Przy użyciu [dane konfiguracji](https://msdn.microsoft.com/powershell/dsc/configdata), może także zawierać taką samą konfigurację dotyczą wiele węzłów.</span><span class="sxs-lookup"><span data-stu-id="49e57-124">Using [configuration data](https://msdn.microsoft.com/powershell/dsc/configdata), you can also have the same configuration apply to multiple nodes.</span></span> <span data-ttu-id="49e57-125">W takim przypadku ten węzeł jest "localhost" — co oznacza komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="49e57-125">In this case, the node is "localhost" - which means the local computer.</span></span>

<span data-ttu-id="49e57-126">Następny element jest [ **zasobów**](https://msdn.microsoft.com/powershell/dsc/resources).</span><span class="sxs-lookup"><span data-stu-id="49e57-126">The next item is a [**resource**](https://msdn.microsoft.com/powershell/dsc/resources).</span></span> <span data-ttu-id="49e57-127">Zasoby są blokami konstrukcyjnymi konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="49e57-127">Resources are building blocks of configurations.</span></span> <span data-ttu-id="49e57-128">Każdy zasób jest moduł, który definiuje implementację logiki jeden aspekt maszyny.</span><span class="sxs-lookup"><span data-stu-id="49e57-128">Each resource is a module that defines the implementation logic of a single aspect of a machine.</span></span> <span data-ttu-id="49e57-129">Na tym komputerze można wyświetlić wszystkich zasobów, uruchamiając **Get-DscResource** w programie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49e57-129">You can view every resource on your machine by running **Get-DscResource** in PowerShell.</span></span> <span data-ttu-id="49e57-130">Zasoby musi znajdować się na komputerze lokalnym i zaimportować przed ich użyciem w elemencie configuration z **DscResource importu** czyli w drugim wierszu tej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="49e57-130">Resources must be present on the local machine and imported before they can be used in a configuration with **Import-DscResource** which is on the second line of this configuration.</span></span>

<span data-ttu-id="49e57-131">**Wprowadzania konfiguracji**</span><span class="sxs-lookup"><span data-stu-id="49e57-131">**Enacting a Configuration**</span></span>

<span data-ttu-id="49e57-132">Jeśli skrypt powyżej jest zapisany i uruchom, nie zostaną zwrócone żadne dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="49e57-132">If the script above is saved and run, no output will be produced.</span></span> <span data-ttu-id="49e57-133">Jest tak, ponieważ konfiguracja jest tylko funkcji, a skrypt powyżej zdefiniował funkcji, ale nie zostały jeszcze ją uruchomić.</span><span class="sxs-lookup"><span data-stu-id="49e57-133">This is because a configuration is just a function, and the script above has defined the function but not yet run it.</span></span> <span data-ttu-id="49e57-134">Po zdefiniowaniu funkcji muszą być wywoływane:</span><span class="sxs-lookup"><span data-stu-id="49e57-134">After the function is defined, it must be invoked:</span></span>
```powershell
myFirstConfiguration
```

<span data-ttu-id="49e57-135">Po wykonaniu konfiguracji funkcji sprawdzania poprawności konfiguracji jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="49e57-135">When executed, configuration functions validate the configuration is valid.</span></span> <span data-ttu-id="49e57-136">Nie powinien mieć go ma błędów składni, zasobów musi mieć wszystkie obowiązkowe parametry zdefiniowany i wszystkie zasoby, które należy zaimportować przed realizacją.</span><span class="sxs-lookup"><span data-stu-id="49e57-136">It should have no syntax errors, resources should have all mandatory parameters defined, and all resources should be imported before execution.</span></span>

<span data-ttu-id="49e57-137">Po wykonaniu konfiguracji tworzy folder o nazwie zawierających konfiguracji **. Plik MOF** dla każdego węzła w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="49e57-137">Once the configuration is executed, it creates a folder with the name of the configuration containing a **.MOF file** for every node in the configuration.</span></span> <span data-ttu-id="49e57-138">. Plik MOF jest format opartych na standardach zarządzania, który jest używany przez DSC środowiska PowerShell do komunikacji za pośrednictwem sieci.</span><span class="sxs-lookup"><span data-stu-id="49e57-138">The .MOF file is a standards-based management format which is used by PowerShell DSC to communicate over the network.</span></span>

<span data-ttu-id="49e57-139">Wprowadzenie konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="49e57-139">To enact the configuration:</span></span>
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration
```
<span data-ttu-id="49e57-140">Spowoduje to utworzenie zadania programu PowerShell, osiągnie, węzły w konfiguracji i konfiguruje je.</span><span class="sxs-lookup"><span data-stu-id="49e57-140">This creates a PowerShell job that reaches out to the nodes in the configuration and configures them.</span></span> <span data-ttu-id="49e57-141">Aby wyświetlić dane wyjściowe zadania, użyj — oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="49e57-141">To see the output of the job, use -Wait.</span></span>
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration -Wait
```