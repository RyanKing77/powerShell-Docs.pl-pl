---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób Windowsprocess DSC
ms.openlocfilehash: cee93ab283ded407d6e032161125aa6d6ac98827
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076773"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="de3cd-103">Zasób Windowsprocess DSC</span><span class="sxs-lookup"><span data-stu-id="de3cd-103">DSC WindowsProcess Resource</span></span>

<span data-ttu-id="de3cd-104">_Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="de3cd-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="de3cd-105">**WindowsProcess** zasobów w Windows PowerShell Desired State Configuration (DSC) udostępnia mechanizm do konfigurowania procesów na węzeł docelowy.</span><span class="sxs-lookup"><span data-stu-id="de3cd-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="de3cd-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="de3cd-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="de3cd-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="de3cd-107">Properties</span></span>

| <span data-ttu-id="de3cd-108">Właściwość</span><span class="sxs-lookup"><span data-stu-id="de3cd-108">Property</span></span> | <span data-ttu-id="de3cd-109">Opis</span><span class="sxs-lookup"><span data-stu-id="de3cd-109">Description</span></span> |
| --- | --- |
| <span data-ttu-id="de3cd-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="de3cd-110">Arguments</span></span>| <span data-ttu-id="de3cd-111">Wskazuje ciąg argumenty do przekazania do procesu jako-to.</span><span class="sxs-lookup"><span data-stu-id="de3cd-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="de3cd-112">Jeśli musisz przekazać argumenty kilka umieściliśmy je w tym ciągu.</span><span class="sxs-lookup"><span data-stu-id="de3cd-112">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="de3cd-113">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="de3cd-113">Path</span></span>| <span data-ttu-id="de3cd-114">Ścieżka do pliku wykonywalnego procesu.</span><span class="sxs-lookup"><span data-stu-id="de3cd-114">The path to the process executable.</span></span> <span data-ttu-id="de3cd-115">Jeśli nazwa pliku wykonywalnego (nie w pełni kwalifikowana ścieżka), zasobu DSC wyszuka środowiska **ścieżki** zmiennej (`$env:Path`) można znaleźć pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="de3cd-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the executable file.</span></span> <span data-ttu-id="de3cd-116">Jeśli wartość tej właściwości jest w pełni kwalifikowaną ścieżkę, DSC nie będzie używać **ścieżki** zmiennej środowiskowej, aby znaleźć plik i zgłosi błąd, jeśli ścieżka nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="de3cd-116">If the value of this property is a fully qualified path, DSC will not use the **Path** environment variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="de3cd-117">Ścieżki względne są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="de3cd-117">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="de3cd-118">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="de3cd-118">Credential</span></span>| <span data-ttu-id="de3cd-119">Określa poświadczenia do uruchamiania procesu.</span><span class="sxs-lookup"><span data-stu-id="de3cd-119">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="de3cd-120">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="de3cd-120">Ensure</span></span>| <span data-ttu-id="de3cd-121">Wskazuje, czy Proces istnieje.</span><span class="sxs-lookup"><span data-stu-id="de3cd-121">Indicates if the process exists.</span></span> <span data-ttu-id="de3cd-122">Ustaw tę właściwość "Present", aby upewnić się, że istnieje proces.</span><span class="sxs-lookup"><span data-stu-id="de3cd-122">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="de3cd-123">W przeciwnym wypadku ustaw ją na "Brak".</span><span class="sxs-lookup"><span data-stu-id="de3cd-123">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="de3cd-124">Wartość domyślna to "Istnieje".</span><span class="sxs-lookup"><span data-stu-id="de3cd-124">The default is "Present".</span></span>|
| <span data-ttu-id="de3cd-125">dependsOn</span><span class="sxs-lookup"><span data-stu-id="de3cd-125">DependsOn</span></span> | <span data-ttu-id="de3cd-126">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="de3cd-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="de3cd-127">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest **ResourceName** a jej typ jest **ResourceType**, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="de3cd-127">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"` .</span></span>|
| <span data-ttu-id="de3cd-128">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="de3cd-128">StandardErrorPath</span></span>| <span data-ttu-id="de3cd-129">Określa ścieżkę katalogu do zapisu błędu standardowego.</span><span class="sxs-lookup"><span data-stu-id="de3cd-129">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="de3cd-130">Wszystkie istniejące pliki zostaną zastąpione.</span><span class="sxs-lookup"><span data-stu-id="de3cd-130">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="de3cd-131">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="de3cd-131">StandardInputPath</span></span>| <span data-ttu-id="de3cd-132">Wskazuje standardowy lokalizację danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="de3cd-132">Indicates the standard input location.</span></span>|
| <span data-ttu-id="de3cd-133">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="de3cd-133">StandardOutputPath</span></span>| <span data-ttu-id="de3cd-134">Wskazuje lokalizację do zapisania wyjścia standardowego.</span><span class="sxs-lookup"><span data-stu-id="de3cd-134">Indicates the location to write the standard output.</span></span> <span data-ttu-id="de3cd-135">Wszystkie istniejące pliki zostaną zastąpione.</span><span class="sxs-lookup"><span data-stu-id="de3cd-135">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="de3cd-136">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="de3cd-136">WorkingDirectory</span></span>| <span data-ttu-id="de3cd-137">Wskazuje lokalizację, która będzie służyć jako bieżący katalog roboczy dla procesu.</span><span class="sxs-lookup"><span data-stu-id="de3cd-137">Indicates the location that will be used as the current working directory for the process.</span></span>|