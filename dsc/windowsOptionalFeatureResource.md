---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób WindowsOptionalFeature DSC
ms.openlocfilehash: 1866bc9cd2194a62de23eaabee8a9c5049a84946
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219406"
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="aa2be-103">Zasób WindowsOptionalFeature DSC</span><span class="sxs-lookup"><span data-stu-id="aa2be-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="aa2be-104">Dotyczy: Środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="aa2be-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="aa2be-105">**WindowsOptionalFeature** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm, aby upewnić się, że funkcje opcjonalne są włączone w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="aa2be-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="aa2be-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="aa2be-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="aa2be-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="aa2be-107">Properties</span></span>

|  <span data-ttu-id="aa2be-108">Właściwość</span><span class="sxs-lookup"><span data-stu-id="aa2be-108">Property</span></span>  |  <span data-ttu-id="aa2be-109">Opis</span><span class="sxs-lookup"><span data-stu-id="aa2be-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="aa2be-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="aa2be-110">Name</span></span>| <span data-ttu-id="aa2be-111">Wskazuje nazwę funkcji, który chcesz zapewnić jest włączone lub wyłączone.</span><span class="sxs-lookup"><span data-stu-id="aa2be-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span>|
| <span data-ttu-id="aa2be-112">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="aa2be-112">Ensure</span></span>| <span data-ttu-id="aa2be-113">Określa, czy ta funkcja jest włączona.</span><span class="sxs-lookup"><span data-stu-id="aa2be-113">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="aa2be-114">Aby upewnić się, że funkcja jest włączona, ustaw tę właściwość, aby "Włącz", aby upewnić się, że funkcja jest wyłączona, ustaw dla właściwości "Wyłącz".</span><span class="sxs-lookup"><span data-stu-id="aa2be-114">To ensure that the feature is enabled, set this property to "Enable" To ensure that the feature is disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="aa2be-115">Źródło</span><span class="sxs-lookup"><span data-stu-id="aa2be-115">Source</span></span>| <span data-ttu-id="aa2be-116">Nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="aa2be-116">Not implemented.</span></span>|
| <span data-ttu-id="aa2be-117">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="aa2be-117">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="aa2be-118">Określa, czy narzędzia DISM kontaktuje Windows Update (WU) podczas wyszukiwania plików źródłowych włączyć funkcję.</span><span class="sxs-lookup"><span data-stu-id="aa2be-118">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="aa2be-119">Jeśli $true, narzędzia DISM skontaktować się z usługi WU.</span><span class="sxs-lookup"><span data-stu-id="aa2be-119">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="aa2be-120">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="aa2be-120">RemoveFilesOnDisable</span></span>| <span data-ttu-id="aa2be-121">Ustaw **$true** Aby usunąć wszystkie pliki skojarzone z funkcją wyłączonego (oznacza to, gdy **upewnij się, że** jest ustawiona na "Brak").</span><span class="sxs-lookup"><span data-stu-id="aa2be-121">Set to **$true** to remove all files associated with the feature when it is disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="aa2be-122">PoziomRejestrowania</span><span class="sxs-lookup"><span data-stu-id="aa2be-122">LogLevel</span></span>| <span data-ttu-id="aa2be-123">Maksymalny poziom informacji wyjściowych wyświetlanych w dziennikach.</span><span class="sxs-lookup"><span data-stu-id="aa2be-123">The maximum output level shown in the logs.</span></span> <span data-ttu-id="aa2be-124">Dopuszczalne wartości to: "ErrorsOnly" (tylko błędy są rejestrowane), "ErrorsAndWarning" (błędy i ostrzeżenia są rejestrowane), a "ErrorsAndWarningAndInformation" (błędy, ostrzeżenia i informacje o debugowaniu są rejestrowane).</span><span class="sxs-lookup"><span data-stu-id="aa2be-124">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="aa2be-125">Ścieżka dziennika</span><span class="sxs-lookup"><span data-stu-id="aa2be-125">LogPath</span></span>| <span data-ttu-id="aa2be-126">Ścieżka do pliku dziennika miejscu dostawcy zasobów do operacji logowania.</span><span class="sxs-lookup"><span data-stu-id="aa2be-126">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="aa2be-127">dependsOn</span><span class="sxs-lookup"><span data-stu-id="aa2be-127">DependsOn</span></span>| <span data-ttu-id="aa2be-128">Określa, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="aa2be-128">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="aa2be-129">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="aa2be-129">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|