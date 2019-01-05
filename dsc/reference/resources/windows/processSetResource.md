---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób Processset DSC
ms.openlocfilehash: 91a2d5b562864addcb8e11062916d291448bbf57
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048374"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="2dbfa-103">Zasób Windowsprocess DSC</span><span class="sxs-lookup"><span data-stu-id="2dbfa-103">DSC WindowsProcess Resource</span></span>

<span data-ttu-id="2dbfa-104">_Dotyczy: Program Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="2dbfa-104">_Applies To: Windows PowerShell 5.0_</span></span>

<span data-ttu-id="2dbfa-105">**ProcessSet** zasobów w Windows PowerShell Desired State Configuration (DSC) udostępnia mechanizm do konfigurowania procesów na węzeł docelowy.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span> <span data-ttu-id="2dbfa-106">Ten zasób jest [złożonego zasobów](../../../resources/authoringResourceComposite.md) wywołująca [zasób windowsprocess](windowsProcessResource.md) dla każdej grupy określony w `GroupName` parametru.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsProcess resource](windowsProcessResource.md) for each group specified in the `GroupName` parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="2dbfa-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="2dbfa-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="2dbfa-108">Właściwości</span><span class="sxs-lookup"><span data-stu-id="2dbfa-108">Properties</span></span>

| <span data-ttu-id="2dbfa-109">Właściwość</span><span class="sxs-lookup"><span data-stu-id="2dbfa-109">Property</span></span> | <span data-ttu-id="2dbfa-110">Opis</span><span class="sxs-lookup"><span data-stu-id="2dbfa-110">Description</span></span> |
| --- | --- |
| <span data-ttu-id="2dbfa-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2dbfa-111">Arguments</span></span>| <span data-ttu-id="2dbfa-112">Ciąg, który zawiera argumenty do przekazania do procesu jako-to.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-112">A string that contains arguments to pass to the process as-is.</span></span> <span data-ttu-id="2dbfa-113">Jeśli musisz przekazać argumenty kilka umieściliśmy je w tym ciągu.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-113">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="2dbfa-114">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="2dbfa-114">Path</span></span>| <span data-ttu-id="2dbfa-115">Ścieżki do plików wykonywalnych procesu.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-115">The paths to the process executables.</span></span> <span data-ttu-id="2dbfa-116">Jeśli są one nazwy plików wykonywalnych (nie w pełni kwalifikowanej ścieżki), umożliwia wyszukiwanie zasobów DSC środowiska **ścieżki** zmiennej (`$env:Path`) aby znaleźć pliki.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-116">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the files.</span></span> <span data-ttu-id="2dbfa-117">Jeśli wartości tej właściwości to w pełni kwalifikowanej ścieżki, DSC nie będzie używać **ścieżki** zmiennej środowiskowej, aby znaleźć pliki i zgłosi błąd, jeśli ścieżki nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-117">If the values of this property are fully qualified paths, DSC will not use the **Path** environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="2dbfa-118">Ścieżki względne są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-118">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="2dbfa-119">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="2dbfa-119">Credential</span></span>| <span data-ttu-id="2dbfa-120">Określa poświadczenia do uruchamiania procesu.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-120">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="2dbfa-121">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="2dbfa-121">Ensure</span></span>| <span data-ttu-id="2dbfa-122">Określa, czy istnieje procesów.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-122">Specifies whether the processes exists.</span></span> <span data-ttu-id="2dbfa-123">Ustaw tę właściwość "Present", aby upewnić się, że istnieje proces.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-123">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="2dbfa-124">W przeciwnym wypadku ustaw ją na "Brak".</span><span class="sxs-lookup"><span data-stu-id="2dbfa-124">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="2dbfa-125">Wartość domyślna to "Istnieje".</span><span class="sxs-lookup"><span data-stu-id="2dbfa-125">The default is "Present".</span></span>|
| <span data-ttu-id="2dbfa-126">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="2dbfa-126">StandardErrorPath</span></span>| <span data-ttu-id="2dbfa-127">Ścieżka, do którego procesy standardowy błąd zapisu.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-127">The path to which the processes write standard error.</span></span> <span data-ttu-id="2dbfa-128">Wszystkie istniejące pliki zostaną zastąpione.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-128">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="2dbfa-129">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="2dbfa-129">StandardInputPath</span></span>| <span data-ttu-id="2dbfa-130">Strumień, z którego proces odbiera standardowe dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-130">The stream from which the process receives standard input.</span></span>|
| <span data-ttu-id="2dbfa-131">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="2dbfa-131">StandardOutputPath</span></span>| <span data-ttu-id="2dbfa-132">Ścieżka pliku, w której procesy zapisuje standardowe dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-132">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="2dbfa-133">Wszystkie istniejące pliki zostaną zastąpione.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-133">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="2dbfa-134">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="2dbfa-134">WorkingDirectory</span></span>| <span data-ttu-id="2dbfa-135">Lokalizacja używana jako bieżący katalog roboczy dla procesów.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-135">The location used as the current working directory for the processes.</span></span>|
| <span data-ttu-id="2dbfa-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="2dbfa-136">DependsOn</span></span> | <span data-ttu-id="2dbfa-137">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2dbfa-138">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest **ResourceName** a jej typ jest **_ResourceType**, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="2dbfa-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **_ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"` .</span></span>|
