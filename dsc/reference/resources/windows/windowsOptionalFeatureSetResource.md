---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: DSC WindowsOptionalFeatureSet Resource
ms.openlocfilehash: c27d026e01bbb443a82112e37f1d199fb3482e49
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076977"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="ce6af-103">DSC WindowsOptionalFeatureSet Resource</span><span class="sxs-lookup"><span data-stu-id="ce6af-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="ce6af-104">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ce6af-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="ce6af-105">**WindowsOptionalFeatureSet** zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm, aby upewnić się, że funkcje opcjonalne są włączone na węźle docelowym.</span><span class="sxs-lookup"><span data-stu-id="ce6af-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>
<span data-ttu-id="ce6af-106">Ten zasób jest [złożonego zasobów](../../../resources/authoringResourceComposite.md) wywołująca [zasób WindowsOptionalFeature](windowsOptionalFeatureResource.md) dla każdej funkcji, określone w `Name` właściwości.</span><span class="sxs-lookup"><span data-stu-id="ce6af-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="ce6af-107">Korzystając z tego zasobu, jeśli chcesz skonfigurować liczbę Windows opcjonalnych funkcji do takiego samego stanu.</span><span class="sxs-lookup"><span data-stu-id="ce6af-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="ce6af-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce6af-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="ce6af-109">Właściwości</span><span class="sxs-lookup"><span data-stu-id="ce6af-109">Properties</span></span>

|  <span data-ttu-id="ce6af-110">Właściwość</span><span class="sxs-lookup"><span data-stu-id="ce6af-110">Property</span></span>  |  <span data-ttu-id="ce6af-111">Opis</span><span class="sxs-lookup"><span data-stu-id="ce6af-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="ce6af-112">Nazwa</span><span class="sxs-lookup"><span data-stu-id="ce6af-112">Name</span></span>| <span data-ttu-id="ce6af-113">Wskazuje nazwę funkcji, które chcesz, aby upewnić się, są włączone lub wyłączone.</span><span class="sxs-lookup"><span data-stu-id="ce6af-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span>|
| <span data-ttu-id="ce6af-114">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="ce6af-114">Ensure</span></span>| <span data-ttu-id="ce6af-115">Określa, czy włączono wybór funkcji.</span><span class="sxs-lookup"><span data-stu-id="ce6af-115">Specifies whether the features are enabled.</span></span> <span data-ttu-id="ce6af-116">Aby upewnić się, że funkcje te są włączone, ustaw tę właściwość na "Włącz", aby upewnić się, że funkcje są wyłączone, ustaw właściwość na "Wyłącz".</span><span class="sxs-lookup"><span data-stu-id="ce6af-116">To ensure that the features are enabled, set this property to "Enable" To ensure that the features are disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="ce6af-117">Źródło</span><span class="sxs-lookup"><span data-stu-id="ce6af-117">Source</span></span>| <span data-ttu-id="ce6af-118">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="ce6af-118">Not implemented.</span></span>|
| <span data-ttu-id="ce6af-119">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="ce6af-119">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="ce6af-120">Określa, czy narzędzia DISM skontaktuje się z usługą Windows Update (WU) podczas szukania plików źródłowych w celu włączenia funkcji.</span><span class="sxs-lookup"><span data-stu-id="ce6af-120">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="ce6af-121">Jeśli $true, narzędzia DISM nie skontaktować się z usługi WU.</span><span class="sxs-lookup"><span data-stu-id="ce6af-121">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="ce6af-122">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="ce6af-122">RemoveFilesOnDisable</span></span>| <span data-ttu-id="ce6af-123">Ustaw **$true** Aby usunąć wszystkie pliki skojarzone z funkcjami, gdy są one wyłączone (to znaczy, gdy **upewnij się, że** jest ustawiona na "Nieobecny").</span><span class="sxs-lookup"><span data-stu-id="ce6af-123">Set to **$true** to remove all files associated with the features when they are disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="ce6af-124">PoziomRejestrowania</span><span class="sxs-lookup"><span data-stu-id="ce6af-124">LogLevel</span></span>| <span data-ttu-id="ce6af-125">Maksymalny poziom informacji wyjściowych wyświetlanych w dziennikach.</span><span class="sxs-lookup"><span data-stu-id="ce6af-125">The maximum output level shown in the logs.</span></span> <span data-ttu-id="ce6af-126">Dozwolone wartości to: "ErrorsOnly" (tylko błędy są rejestrowane), "ErrorsAndWarning" (błędy i ostrzeżenia są rejestrowane), a "ErrorsAndWarningAndInformation" (błędy, ostrzeżenia i informacje o debugowaniu są rejestrowane).</span><span class="sxs-lookup"><span data-stu-id="ce6af-126">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="ce6af-127">Ścieżka dziennika</span><span class="sxs-lookup"><span data-stu-id="ce6af-127">LogPath</span></span>| <span data-ttu-id="ce6af-128">Ścieżka do pliku dziennika, w której chcesz dostawcy zasobów do dziennika operacji.</span><span class="sxs-lookup"><span data-stu-id="ce6af-128">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="ce6af-129">dependsOn</span><span class="sxs-lookup"><span data-stu-id="ce6af-129">DependsOn</span></span>| <span data-ttu-id="ce6af-130">Określa, czy konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="ce6af-130">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ce6af-131">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="ce6af-131">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
