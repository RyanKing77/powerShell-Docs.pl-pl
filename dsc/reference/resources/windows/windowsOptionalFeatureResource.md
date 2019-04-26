---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób WindowsOptionalFeature DSC
ms.openlocfilehash: 390caefd2ad190afc651b22ed1beb5cf1d604527
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076762"
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="3c189-103">Zasób WindowsOptionalFeature DSC</span><span class="sxs-lookup"><span data-stu-id="3c189-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="3c189-104">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3c189-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="3c189-105">**WindowsOptionalFeature** zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm, aby upewnić się, że funkcje opcjonalne są włączone na węźle docelowym.</span><span class="sxs-lookup"><span data-stu-id="3c189-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="3c189-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c189-106">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="3c189-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="3c189-107">Properties</span></span>

|  <span data-ttu-id="3c189-108">Właściwość</span><span class="sxs-lookup"><span data-stu-id="3c189-108">Property</span></span>  |  <span data-ttu-id="3c189-109">Opis</span><span class="sxs-lookup"><span data-stu-id="3c189-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="3c189-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="3c189-110">Name</span></span>| <span data-ttu-id="3c189-111">Wskazuje nazwę funkcji, którą chcesz, aby upewnić się, jest włączone lub wyłączone.</span><span class="sxs-lookup"><span data-stu-id="3c189-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span>|
| <span data-ttu-id="3c189-112">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="3c189-112">Ensure</span></span>| <span data-ttu-id="3c189-113">Określa, czy ta funkcja jest włączona.</span><span class="sxs-lookup"><span data-stu-id="3c189-113">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="3c189-114">Aby upewnić się, że ta funkcja jest włączona, ustaw tę właściwość na "Włącz", aby upewnić się, że funkcja jest wyłączona, ustaw właściwość na "Wyłącz".</span><span class="sxs-lookup"><span data-stu-id="3c189-114">To ensure that the feature is enabled, set this property to "Enable" To ensure that the feature is disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="3c189-115">Źródło</span><span class="sxs-lookup"><span data-stu-id="3c189-115">Source</span></span>| <span data-ttu-id="3c189-116">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="3c189-116">Not implemented.</span></span>|
| <span data-ttu-id="3c189-117">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="3c189-117">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="3c189-118">Określa, czy narzędzia DISM skontaktuje się z usługą Windows Update (WU) podczas szukania plików źródłowych włączyć funkcję.</span><span class="sxs-lookup"><span data-stu-id="3c189-118">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="3c189-119">Jeśli $true, narzędzia DISM nie skontaktować się z usługi WU.</span><span class="sxs-lookup"><span data-stu-id="3c189-119">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="3c189-120">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="3c189-120">RemoveFilesOnDisable</span></span>| <span data-ttu-id="3c189-121">Ustaw **$true** Aby usunąć wszystkie pliki skojarzone z funkcją, gdy jest on wyłączony (to znaczy, gdy **upewnij się, że** jest ustawiona na "Brak").</span><span class="sxs-lookup"><span data-stu-id="3c189-121">Set to **$true** to remove all files associated with the feature when it is disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="3c189-122">PoziomRejestrowania</span><span class="sxs-lookup"><span data-stu-id="3c189-122">LogLevel</span></span>| <span data-ttu-id="3c189-123">Maksymalny poziom informacji wyjściowych wyświetlanych w dziennikach.</span><span class="sxs-lookup"><span data-stu-id="3c189-123">The maximum output level shown in the logs.</span></span> <span data-ttu-id="3c189-124">Dozwolone wartości to: "ErrorsOnly" (tylko błędy są rejestrowane), "ErrorsAndWarning" (błędy i ostrzeżenia są rejestrowane), a "ErrorsAndWarningAndInformation" (błędy, ostrzeżenia i informacje o debugowaniu są rejestrowane).</span><span class="sxs-lookup"><span data-stu-id="3c189-124">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="3c189-125">Ścieżka dziennika</span><span class="sxs-lookup"><span data-stu-id="3c189-125">LogPath</span></span>| <span data-ttu-id="3c189-126">Ścieżka do pliku dziennika, w której chcesz dostawcy zasobów do dziennika operacji.</span><span class="sxs-lookup"><span data-stu-id="3c189-126">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="3c189-127">dependsOn</span><span class="sxs-lookup"><span data-stu-id="3c189-127">DependsOn</span></span>| <span data-ttu-id="3c189-128">Określa, czy konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="3c189-128">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="3c189-129">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="3c189-129">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|