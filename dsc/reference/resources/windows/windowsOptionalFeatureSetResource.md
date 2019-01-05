---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób Windowsoptionalfeatureset DSC
ms.openlocfilehash: c27d026e01bbb443a82112e37f1d199fb3482e49
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048413"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="091f5-103">Zasób Windowsoptionalfeatureset DSC</span><span class="sxs-lookup"><span data-stu-id="091f5-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="091f5-104">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="091f5-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="091f5-105">**WindowsOptionalFeatureSet** zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm, aby upewnić się, że funkcje opcjonalne są włączone na węźle docelowym.</span><span class="sxs-lookup"><span data-stu-id="091f5-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>
<span data-ttu-id="091f5-106">Ten zasób jest [złożonego zasobów](../../../resources/authoringResourceComposite.md) wywołująca [zasób WindowsOptionalFeature](windowsOptionalFeatureResource.md) dla każdej funkcji, określone w `Name` właściwości.</span><span class="sxs-lookup"><span data-stu-id="091f5-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="091f5-107">Korzystając z tego zasobu, jeśli chcesz skonfigurować liczbę Windows opcjonalnych funkcji do takiego samego stanu.</span><span class="sxs-lookup"><span data-stu-id="091f5-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="091f5-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="091f5-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="091f5-109">Właściwości</span><span class="sxs-lookup"><span data-stu-id="091f5-109">Properties</span></span>

|  <span data-ttu-id="091f5-110">Właściwość</span><span class="sxs-lookup"><span data-stu-id="091f5-110">Property</span></span>  |  <span data-ttu-id="091f5-111">Opis</span><span class="sxs-lookup"><span data-stu-id="091f5-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="091f5-112">Nazwa</span><span class="sxs-lookup"><span data-stu-id="091f5-112">Name</span></span>| <span data-ttu-id="091f5-113">Wskazuje nazwę funkcji, które chcesz, aby upewnić się, są włączone lub wyłączone.</span><span class="sxs-lookup"><span data-stu-id="091f5-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span>|
| <span data-ttu-id="091f5-114">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="091f5-114">Ensure</span></span>| <span data-ttu-id="091f5-115">Określa, czy włączono wybór funkcji.</span><span class="sxs-lookup"><span data-stu-id="091f5-115">Specifies whether the features are enabled.</span></span> <span data-ttu-id="091f5-116">Aby upewnić się, że funkcje te są włączone, ustaw tę właściwość na "Włącz", aby upewnić się, że funkcje są wyłączone, ustaw właściwość na "Wyłącz".</span><span class="sxs-lookup"><span data-stu-id="091f5-116">To ensure that the features are enabled, set this property to "Enable" To ensure that the features are disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="091f5-117">Źródło</span><span class="sxs-lookup"><span data-stu-id="091f5-117">Source</span></span>| <span data-ttu-id="091f5-118">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="091f5-118">Not implemented.</span></span>|
| <span data-ttu-id="091f5-119">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="091f5-119">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="091f5-120">Określa, czy narzędzia DISM skontaktuje się z usługą Windows Update (WU) podczas szukania plików źródłowych w celu włączenia funkcji.</span><span class="sxs-lookup"><span data-stu-id="091f5-120">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="091f5-121">Jeśli $true, narzędzia DISM nie skontaktować się z usługi WU.</span><span class="sxs-lookup"><span data-stu-id="091f5-121">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="091f5-122">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="091f5-122">RemoveFilesOnDisable</span></span>| <span data-ttu-id="091f5-123">Ustaw **$true** Aby usunąć wszystkie pliki skojarzone z funkcjami, gdy są one wyłączone (to znaczy, gdy **upewnij się, że** jest ustawiona na "Nieobecny").</span><span class="sxs-lookup"><span data-stu-id="091f5-123">Set to **$true** to remove all files associated with the features when they are disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="091f5-124">PoziomRejestrowania</span><span class="sxs-lookup"><span data-stu-id="091f5-124">LogLevel</span></span>| <span data-ttu-id="091f5-125">Maksymalny poziom informacji wyjściowych wyświetlanych w dziennikach.</span><span class="sxs-lookup"><span data-stu-id="091f5-125">The maximum output level shown in the logs.</span></span> <span data-ttu-id="091f5-126">Dozwolone wartości to: "ErrorsOnly" (tylko błędy są rejestrowane), "ErrorsAndWarning" (błędy i ostrzeżenia są rejestrowane), a "ErrorsAndWarningAndInformation" (błędy, ostrzeżenia i informacje o debugowaniu są rejestrowane).</span><span class="sxs-lookup"><span data-stu-id="091f5-126">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="091f5-127">Ścieżka dziennika</span><span class="sxs-lookup"><span data-stu-id="091f5-127">LogPath</span></span>| <span data-ttu-id="091f5-128">Ścieżka do pliku dziennika, w której chcesz dostawcy zasobów do dziennika operacji.</span><span class="sxs-lookup"><span data-stu-id="091f5-128">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="091f5-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="091f5-129">DependsOn</span></span>| <span data-ttu-id="091f5-130">Określa, czy konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="091f5-130">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="091f5-131">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="091f5-131">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
