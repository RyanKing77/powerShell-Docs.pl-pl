---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób WindowsOptionalFeatureSet DSC
ms.openlocfilehash: 7c5eb553b396776f54a36bec8971f71ec61f9354
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187661"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="e69dd-103">Zasób WindowsOptionalFeatureSet DSC</span><span class="sxs-lookup"><span data-stu-id="e69dd-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="e69dd-104">Dotyczy: Środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e69dd-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="e69dd-105">**WindowsOptionalFeatureSet** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm, aby upewnić się, że funkcje opcjonalne są włączone w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="e69dd-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>
<span data-ttu-id="e69dd-106">Ten zasób jest [złożonego zasobów](authoringResourceComposite.md) , który odwołuje się [zasobów WindowsOptionalFeature](windowsOptionalFeatureResource.md) dla każdej funkcji określone w `Name` właściwości.</span><span class="sxs-lookup"><span data-stu-id="e69dd-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="e69dd-107">Jeśli chcesz skonfigurować liczbę opcjonalne funkcje systemu Windows na tym samym stanie, należy użyć tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="e69dd-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="e69dd-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="e69dd-108">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="e69dd-109">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e69dd-109">Properties</span></span>

|  <span data-ttu-id="e69dd-110">Właściwość</span><span class="sxs-lookup"><span data-stu-id="e69dd-110">Property</span></span>  |  <span data-ttu-id="e69dd-111">Opis</span><span class="sxs-lookup"><span data-stu-id="e69dd-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="e69dd-112">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e69dd-112">Name</span></span>| <span data-ttu-id="e69dd-113">Wskazuje nazwę funkcji, które chcesz zapewnić są włączone lub wyłączone.</span><span class="sxs-lookup"><span data-stu-id="e69dd-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span>|
| <span data-ttu-id="e69dd-114">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="e69dd-114">Ensure</span></span>| <span data-ttu-id="e69dd-115">Określa, czy są włączone funkcje.</span><span class="sxs-lookup"><span data-stu-id="e69dd-115">Specifies whether the features are enabled.</span></span> <span data-ttu-id="e69dd-116">Aby upewnić się, że funkcje są włączone, ustaw tę właściwość, aby "Włącz", aby upewnić się, że te funkcje są wyłączone, ustaw dla właściwości "Wyłącz".</span><span class="sxs-lookup"><span data-stu-id="e69dd-116">To ensure that the features are enabled, set this property to "Enable" To ensure that the features are disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="e69dd-117">Źródło</span><span class="sxs-lookup"><span data-stu-id="e69dd-117">Source</span></span>| <span data-ttu-id="e69dd-118">Nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="e69dd-118">Not implemented.</span></span>|
| <span data-ttu-id="e69dd-119">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="e69dd-119">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="e69dd-120">Określa, czy narzędzia DISM kontaktuje Windows Update (WU) podczas wyszukiwania plików źródłowych do włączania funkcji.</span><span class="sxs-lookup"><span data-stu-id="e69dd-120">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="e69dd-121">Jeśli $true, narzędzia DISM skontaktować się z usługi WU.</span><span class="sxs-lookup"><span data-stu-id="e69dd-121">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="e69dd-122">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="e69dd-122">RemoveFilesOnDisable</span></span>| <span data-ttu-id="e69dd-123">Ustaw **$true** Aby usunąć wszystkie pliki skojarzone z funkcjami, gdy są one wyłączone (oznacza to, gdy **upewnij się, że** jest ustawiona na "Brak").</span><span class="sxs-lookup"><span data-stu-id="e69dd-123">Set to **$true** to remove all files associated with the features when they are disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="e69dd-124">PoziomRejestrowania</span><span class="sxs-lookup"><span data-stu-id="e69dd-124">LogLevel</span></span>| <span data-ttu-id="e69dd-125">Maksymalny poziom informacji wyjściowych wyświetlanych w dziennikach.</span><span class="sxs-lookup"><span data-stu-id="e69dd-125">The maximum output level shown in the logs.</span></span> <span data-ttu-id="e69dd-126">Dopuszczalne wartości to: "ErrorsOnly" (tylko błędy są rejestrowane), "ErrorsAndWarning" (błędy i ostrzeżenia są rejestrowane), a "ErrorsAndWarningAndInformation" (błędy, ostrzeżenia i informacje o debugowaniu są rejestrowane).</span><span class="sxs-lookup"><span data-stu-id="e69dd-126">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="e69dd-127">Ścieżka dziennika</span><span class="sxs-lookup"><span data-stu-id="e69dd-127">LogPath</span></span>| <span data-ttu-id="e69dd-128">Ścieżka do pliku dziennika miejscu dostawcy zasobów do operacji logowania.</span><span class="sxs-lookup"><span data-stu-id="e69dd-128">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="e69dd-129">dependsOn</span><span class="sxs-lookup"><span data-stu-id="e69dd-129">DependsOn</span></span>| <span data-ttu-id="e69dd-130">Określa, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="e69dd-130">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e69dd-131">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="e69dd-131">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|