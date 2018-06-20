---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób WindowsProcess DSC
ms.openlocfilehash: 72668136a3a51c17c52f762c6f94bec3ed4597b0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187031"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="aacf6-103">Zasób WindowsProcess DSC</span><span class="sxs-lookup"><span data-stu-id="aacf6-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="aacf6-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="aacf6-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="aacf6-105">**WindowsProcess** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm konfigurowania procesów w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="aacf6-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="aacf6-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="aacf6-106">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="aacf6-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="aacf6-107">Properties</span></span>
|  <span data-ttu-id="aacf6-108">Właściwość</span><span class="sxs-lookup"><span data-stu-id="aacf6-108">Property</span></span>  |  <span data-ttu-id="aacf6-109">Opis</span><span class="sxs-lookup"><span data-stu-id="aacf6-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="aacf6-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="aacf6-110">Arguments</span></span>| <span data-ttu-id="aacf6-111">Wskazuje ciąg argumenty do przekazania do procesu jako — jest.</span><span class="sxs-lookup"><span data-stu-id="aacf6-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="aacf6-112">Aby przekazać argumenty kilka należy umieścić je w tym ciągu.</span><span class="sxs-lookup"><span data-stu-id="aacf6-112">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="aacf6-113">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="aacf6-113">Path</span></span>| <span data-ttu-id="aacf6-114">Ścieżka do pliku wykonywalnego procesu.</span><span class="sxs-lookup"><span data-stu-id="aacf6-114">The path to the process executable.</span></span> <span data-ttu-id="aacf6-115">Jeśli nazwa pliku wykonywalnego (nie pełni kwalifikowana ścieżka), zasobu DSC przeszuka środowiska **ścieżki** zmiennej (`$env:Path`) można znaleźć pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="aacf6-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the executable file.</span></span> <span data-ttu-id="aacf6-116">Jeśli wartość tej właściwości jest w pełni kwalifikowana, nie będzie używać DSC **ścieżki** zmiennej środowiskowej, aby znaleźć plik i zgłosi błąd, jeśli ścieżka nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="aacf6-116">If the value of this property is a fully qualified path, DSC will not use the **Path** environment variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="aacf6-117">Ścieżki względne nie są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="aacf6-117">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="aacf6-118">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="aacf6-118">Credential</span></span>| <span data-ttu-id="aacf6-119">Wskazuje poświadczeń dla uruchamiania procesu.</span><span class="sxs-lookup"><span data-stu-id="aacf6-119">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="aacf6-120">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="aacf6-120">Ensure</span></span>| <span data-ttu-id="aacf6-121">Wskazuje, czy Proces istnieje.</span><span class="sxs-lookup"><span data-stu-id="aacf6-121">Indicates if the process exists.</span></span> <span data-ttu-id="aacf6-122">Ustaw tę właściwość na "Brak", aby upewnić się, czy Proces istnieje.</span><span class="sxs-lookup"><span data-stu-id="aacf6-122">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="aacf6-123">W przeciwnym wypadku ustaw ją na "Brak".</span><span class="sxs-lookup"><span data-stu-id="aacf6-123">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="aacf6-124">Wartość domyślna to "Brak".</span><span class="sxs-lookup"><span data-stu-id="aacf6-124">The default is "Present".</span></span>|
| <span data-ttu-id="aacf6-125">dependsOn</span><span class="sxs-lookup"><span data-stu-id="aacf6-125">DependsOn</span></span> | <span data-ttu-id="aacf6-126">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="aacf6-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="aacf6-127">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości to "DependsOn ="[ResourceName ResourceType]"".</span><span class="sxs-lookup"><span data-stu-id="aacf6-127">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\` .</span></span>|
| <span data-ttu-id="aacf6-128">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="aacf6-128">StandardErrorPath</span></span>| <span data-ttu-id="aacf6-129">Określa ścieżkę katalogu do zapisania standardowy błąd.</span><span class="sxs-lookup"><span data-stu-id="aacf6-129">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="aacf6-130">Wszystkie istniejące pliki zostaną zastąpione.</span><span class="sxs-lookup"><span data-stu-id="aacf6-130">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="aacf6-131">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="aacf6-131">StandardInputPath</span></span>| <span data-ttu-id="aacf6-132">Określa lokalizację standardowe wejściowego.</span><span class="sxs-lookup"><span data-stu-id="aacf6-132">Indicates the standard input location.</span></span>|
| <span data-ttu-id="aacf6-133">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="aacf6-133">StandardOutputPath</span></span>| <span data-ttu-id="aacf6-134">Wskazuje lokalizację do zapisania wyjścia standardowego.</span><span class="sxs-lookup"><span data-stu-id="aacf6-134">Indicates the location to write the standard output.</span></span> <span data-ttu-id="aacf6-135">Wszystkie istniejące pliki zostaną zastąpione.</span><span class="sxs-lookup"><span data-stu-id="aacf6-135">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="aacf6-136">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="aacf6-136">WorkingDirectory</span></span>| <span data-ttu-id="aacf6-137">Określa lokalizację, która będzie służyć jako bieżący katalog roboczy dla procesu.</span><span class="sxs-lookup"><span data-stu-id="aacf6-137">Indicates the location that will be used as the current working directory for the process.</span></span>|