---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób WindowsFeature DSC
ms.openlocfilehash: 7a57f4b2797ab3bb202aea8b2543d1e3f14074e9
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048469"
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="364a6-103">Zasób WindowsFeature DSC</span><span class="sxs-lookup"><span data-stu-id="364a6-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="364a6-104">Dotyczy: Program Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="364a6-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="364a6-105">**WindowsFeature** zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm, aby upewnić się, że role i funkcje są dodawane lub usuwane w węźle docelowym.</span><span class="sxs-lookup"><span data-stu-id="364a6-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="364a6-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="364a6-106">Syntax</span></span>

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="364a6-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="364a6-107">Properties</span></span>

|  <span data-ttu-id="364a6-108">Właściwość</span><span class="sxs-lookup"><span data-stu-id="364a6-108">Property</span></span>  |  <span data-ttu-id="364a6-109">Opis</span><span class="sxs-lookup"><span data-stu-id="364a6-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="364a6-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="364a6-110">Name</span></span>| <span data-ttu-id="364a6-111">Wskazuje nazwę rolę lub funkcję, która chce mieć pewność, jest dodane lub usunięte.</span><span class="sxs-lookup"><span data-stu-id="364a6-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="364a6-112">To jest taka sama jak __nazwa__ właściwości z [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) polecenia cmdlet, a nie nazwę wyświetlaną roli lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="364a6-112">This is the same as the __Name__ property from the [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, and not the display name of the role or feature.</span></span>|
| <span data-ttu-id="364a6-113">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="364a6-113">Credential</span></span>| <span data-ttu-id="364a6-114">Określa poświadczenia do użycia w celu dodania lub usunięcia roli lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="364a6-114">Indicates the credentials to use to add or remove the role or feature.</span></span>|
| <span data-ttu-id="364a6-115">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="364a6-115">Ensure</span></span>| <span data-ttu-id="364a6-116">Wskazuje, jeśli jest dodawany roli lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="364a6-116">Indicates if the role or feature is added.</span></span> <span data-ttu-id="364a6-117">Aby upewnij się, że rola lub funkcja dodano, ustaw tę właściwość na "Obecny", aby upewnić się, że została usunięta rolę lub funkcję, należy ustawić właściwość na "Brak".</span><span class="sxs-lookup"><span data-stu-id="364a6-117">To ensure that the role or feature is added, set this property to "Present" To ensure that the role or feature is removed, set the property to "Absent".</span></span>|
| <span data-ttu-id="364a6-118">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="364a6-118">IncludeAllSubFeature</span></span>| <span data-ttu-id="364a6-119">Ustaw tę właściwość na __$true__ do zapewnienia stan podfunkcje wszystkie wymagane ze stanem tej funkcji należy określić przy użyciu __nazwa__ właściwości.</span><span class="sxs-lookup"><span data-stu-id="364a6-119">Set this property to __$true__ to ensure the state of all required subfeatures with the state of the feature you specify with the __Name__ property.</span></span>|
| <span data-ttu-id="364a6-120">Ścieżka dziennika</span><span class="sxs-lookup"><span data-stu-id="364a6-120">LogPath</span></span>| <span data-ttu-id="364a6-121">Określa ścieżkę do pliku dziennika, w której chcesz dostawcy zasobów do dziennika operacji.</span><span class="sxs-lookup"><span data-stu-id="364a6-121">Indicates the path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="364a6-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="364a6-122">DependsOn</span></span>| <span data-ttu-id="364a6-123">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="364a6-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="364a6-124">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="364a6-124">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="364a6-125">Źródło</span><span class="sxs-lookup"><span data-stu-id="364a6-125">Source</span></span>| <span data-ttu-id="364a6-126">Wskazuje lokalizację pliku źródłowego na potrzeby instalacji, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="364a6-126">Indicates the location of the source file to use for installation, if necessary.</span></span>|

## <a name="example"></a><span data-ttu-id="364a6-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="364a6-127">Example</span></span>
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```