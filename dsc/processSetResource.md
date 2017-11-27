---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Zasób ProcessSet DSC"
ms.openlocfilehash: b713d1a9c34eab6966de4f342991ead32c19df5d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="bf5ae-103">Zasób WindowsProcess DSC</span><span class="sxs-lookup"><span data-stu-id="bf5ae-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="bf5ae-104">Dotyczy: Środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bf5ae-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="bf5ae-105">**ProcessSet** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm konfigurowania procesów w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="bf5ae-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span> <span data-ttu-id="bf5ae-106">Ten zasób jest [złożonego zasobów](authoringResourceComposite.md) , który odwołuje się [zasobów WindowsProcess](windowsProcessResource.md) dla każdej grupy określonej w `GroupName` parametru.</span><span class="sxs-lookup"><span data-stu-id="bf5ae-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsProcess resource](windowsProcessResource.md) for each group specified in the `GroupName` parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="bf5ae-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf5ae-107">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]   
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="bf5ae-108">Właściwości</span><span class="sxs-lookup"><span data-stu-id="bf5ae-108">Properties</span></span>
|  <span data-ttu-id="bf5ae-109">Właściwość</span><span class="sxs-lookup"><span data-stu-id="bf5ae-109">Property</span></span>  |  <span data-ttu-id="bf5ae-110">Opis</span><span class="sxs-lookup"><span data-stu-id="bf5ae-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="bf5ae-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="bf5ae-111">Arguments</span></span>| <span data-ttu-id="bf5ae-112">Ciąg, który zawiera argumenty do przekazania do procesu jako — jest.</span><span class="sxs-lookup"><span data-stu-id="bf5ae-112">A string that contains arguments to pass to the process as-is.</span></span> <span data-ttu-id="bf5ae-113">Aby przekazać argumenty kilka należy umieścić je w tym ciągu.</span><span class="sxs-lookup"><span data-stu-id="bf5ae-113">If you need to pass several arguments, put them all in this string.</span></span>| 
| <span data-ttu-id="bf5ae-114">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="bf5ae-114">Path</span></span>| <span data-ttu-id="bf5ae-115">Ścieżki do plików wykonywalnych procesu.</span><span class="sxs-lookup"><span data-stu-id="bf5ae-115">The paths to the process executables.</span></span> <span data-ttu-id="bf5ae-116">Jeśli są one nazwy plików wykonywalnych (nie w pełni kwalifikowanej ścieżki), zasobu DSC przeszuka środowiska **ścieżki** zmiennej (`$env:Path`) można znaleźć plików.</span><span class="sxs-lookup"><span data-stu-id="bf5ae-116">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the files.</span></span> <span data-ttu-id="bf5ae-117">Jeśli wartości tej właściwości są w pełni kwalifikowanymi ścieżkami, nie będzie używać DSC **ścieżki** zmiennej środowiskowej można znaleźć plików i zgłosi błąd, jeśli ścieżki nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="bf5ae-117">If the values of this property are fully qualified paths, DSC will not use the **Path** environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="bf5ae-118">Ścieżki względne nie są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="bf5ae-118">Relative paths are not allowed.</span></span>| 
| <span data-ttu-id="bf5ae-119">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="bf5ae-119">Credential</span></span>| <span data-ttu-id="bf5ae-120">Wskazuje poświadczeń dla uruchamiania procesu.</span><span class="sxs-lookup"><span data-stu-id="bf5ae-120">Indicates the credentials for starting the process.</span></span>| 
| <span data-ttu-id="bf5ae-121">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="bf5ae-121">Ensure</span></span>| <span data-ttu-id="bf5ae-122">Określa, czy istnieje procesów.</span><span class="sxs-lookup"><span data-stu-id="bf5ae-122">Specifies whether the processes exists.</span></span> <span data-ttu-id="bf5ae-123">Ustaw tę właściwość na "Brak", aby upewnić się, czy Proces istnieje.</span><span class="sxs-lookup"><span data-stu-id="bf5ae-123">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="bf5ae-124">W przeciwnym wypadku ustaw ją na "Brak".</span><span class="sxs-lookup"><span data-stu-id="bf5ae-124">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="bf5ae-125">Wartość domyślna to "Brak".</span><span class="sxs-lookup"><span data-stu-id="bf5ae-125">The default is "Present".</span></span>| 
| <span data-ttu-id="bf5ae-126">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="bf5ae-126">StandardErrorPath</span></span>| <span data-ttu-id="bf5ae-127">Ścieżka, do którego standardowy błąd zapisu procesów.</span><span class="sxs-lookup"><span data-stu-id="bf5ae-127">The path to which the processes write standard error.</span></span> <span data-ttu-id="bf5ae-128">Wszystkie istniejące pliki zostaną zastąpione.</span><span class="sxs-lookup"><span data-stu-id="bf5ae-128">Any existing file there will be overwritten.</span></span>| 
| <span data-ttu-id="bf5ae-129">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="bf5ae-129">StandardInputPath</span></span>| <span data-ttu-id="bf5ae-130">Strumień, z którego proces odbiera standardowe dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="bf5ae-130">The stream from which the process receives standard input.</span></span>| 
| <span data-ttu-id="bf5ae-131">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="bf5ae-131">StandardOutputPath</span></span>| <span data-ttu-id="bf5ae-132">Ścieżka pliku, do którego procesy zapisu wyjścia standardowego.</span><span class="sxs-lookup"><span data-stu-id="bf5ae-132">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="bf5ae-133">Wszystkie istniejące pliki zostaną zastąpione.</span><span class="sxs-lookup"><span data-stu-id="bf5ae-133">Any existing file there will be overwritten.</span></span>| 
| <span data-ttu-id="bf5ae-134">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="bf5ae-134">WorkingDirectory</span></span>| <span data-ttu-id="bf5ae-135">Lokalizacja używana jako bieżący katalog roboczy dla procesów.</span><span class="sxs-lookup"><span data-stu-id="bf5ae-135">The location used as the current working directory for the processes.</span></span>| 
| <span data-ttu-id="bf5ae-136">dependsOn</span><span class="sxs-lookup"><span data-stu-id="bf5ae-136">DependsOn</span></span> | <span data-ttu-id="bf5ae-137">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="bf5ae-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="bf5ae-138">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest **ResourceName** i jej typ jest **_ResourceType**, składnia za pomocą tej właściwości to "DependsOn ="[ResourceName ResourceType]"".</span><span class="sxs-lookup"><span data-stu-id="bf5ae-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **_ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`\` .</span></span>| 

