---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób WindowsFeature DSC
ms.openlocfilehash: ece77043d3a4131150b934a19ee8b92dd75c48f0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="a78f0-103">Zasób WindowsFeature DSC</span><span class="sxs-lookup"><span data-stu-id="a78f0-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="a78f0-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a78f0-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="a78f0-105">**WindowsFeature** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm, aby upewnić się, że role i funkcje zostały dodane lub usunięte w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="a78f0-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="a78f0-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a78f0-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="a78f0-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="a78f0-107">Properties</span></span>

|  <span data-ttu-id="a78f0-108">Właściwość</span><span class="sxs-lookup"><span data-stu-id="a78f0-108">Property</span></span>  |  <span data-ttu-id="a78f0-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a78f0-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="a78f0-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a78f0-110">Name</span></span>| <span data-ttu-id="a78f0-111">Wskazuje nazwę roli lub funkcji, które chcesz zapewnić zostanie dodany lub usunięty.</span><span class="sxs-lookup"><span data-stu-id="a78f0-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="a78f0-112">Jest taka sama jak __nazwa__ właściwość z [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) polecenia cmdlet, a nie nazwę wyświetlaną roli lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="a78f0-112">This is the same as the __Name__ property from the [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, and not the display name of the role or feature.</span></span>|
| <span data-ttu-id="a78f0-113">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="a78f0-113">Credential</span></span>| <span data-ttu-id="a78f0-114">Określa poświadczenia używane do dodawania lub usuwania roli lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="a78f0-114">Indicates the credentials to use to add or remove the role or feature.</span></span>|
| <span data-ttu-id="a78f0-115">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="a78f0-115">Ensure</span></span>| <span data-ttu-id="a78f0-116">Wskazuje, jeśli jest dodawany roli lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="a78f0-116">Indicates if the role or feature is added.</span></span> <span data-ttu-id="a78f0-117">Aby upewnić się, że roli lub funkcji jest dodany, ustaw tę właściwość na "Brak", aby upewnić się, że zostanie usunięty rolę lub funkcję, ustaw właściwość na "Brak".</span><span class="sxs-lookup"><span data-stu-id="a78f0-117">To ensure that the role or feature is added, set this property to "Present" To ensure that the role or feature is removed, set the property to "Absent".</span></span>|
| <span data-ttu-id="a78f0-118">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="a78f0-118">IncludeAllSubFeature</span></span>| <span data-ttu-id="a78f0-119">Ta właściwość jest ustawiana __$true__ do zapewnienia stan wszystkich wymaganych podfunkcje ze stanem funkcji z __nazwa__ właściwości.</span><span class="sxs-lookup"><span data-stu-id="a78f0-119">Set this property to __$true__ to ensure the state of all required subfeatures with the state of the feature you specify with the __Name__ property.</span></span>|
| <span data-ttu-id="a78f0-120">Ścieżka dziennika</span><span class="sxs-lookup"><span data-stu-id="a78f0-120">LogPath</span></span>| <span data-ttu-id="a78f0-121">Określa ścieżkę do pliku dziennika miejscu dostawcy zasobów do operacji logowania.</span><span class="sxs-lookup"><span data-stu-id="a78f0-121">Indicates the path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="a78f0-122">dependsOn</span><span class="sxs-lookup"><span data-stu-id="a78f0-122">DependsOn</span></span>| <span data-ttu-id="a78f0-123">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="a78f0-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a78f0-124">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a78f0-124">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="a78f0-125">Źródło</span><span class="sxs-lookup"><span data-stu-id="a78f0-125">Source</span></span>| <span data-ttu-id="a78f0-126">Określa lokalizację pliku źródłowego do użycia na potrzeby instalacji, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="a78f0-126">Indicates the location of the source file to use for installation, if necessary.</span></span>|

## <a name="example"></a><span data-ttu-id="a78f0-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="a78f0-127">Example</span></span>
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```