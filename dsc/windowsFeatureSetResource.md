---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób WindowsFeatureSet DSC
ms.openlocfilehash: a6fecba0397b88ce39f6f1a1be6cc366c8a983a6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="1b3a1-103">Zasób WindowsFeatureSet DSC</span><span class="sxs-lookup"><span data-stu-id="1b3a1-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="1b3a1-104">Dotyczy: Środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1b3a1-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="1b3a1-105">**WindowsFeatureSet** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm, aby upewnić się, że role i funkcje zostały dodane lub usunięte w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="1b3a1-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>
<span data-ttu-id="1b3a1-106">Ten zasób jest [złożonego zasobów](authoringResourceComposite.md) , który odwołuje się [zasobów WindowsFeature](windowsfeatureResource.md) dla każdej funkcji określone w `Name` właściwości.</span><span class="sxs-lookup"><span data-stu-id="1b3a1-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="1b3a1-107">Jeśli chcesz skonfigurować wiele funkcji systemu Windows na tym samym stanie, należy użyć tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="1b3a1-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="1b3a1-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b3a1-108">Syntax</span></span>

```
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [bool] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="1b3a1-109">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1b3a1-109">Properties</span></span>

|  <span data-ttu-id="1b3a1-110">Właściwość</span><span class="sxs-lookup"><span data-stu-id="1b3a1-110">Property</span></span>  |  <span data-ttu-id="1b3a1-111">Opis</span><span class="sxs-lookup"><span data-stu-id="1b3a1-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="1b3a1-112">Nazwa</span><span class="sxs-lookup"><span data-stu-id="1b3a1-112">Name</span></span>| <span data-ttu-id="1b3a1-113">Nazwy ról lub funkcji, które chcesz zapewnić zostały dodane lub usunięte.</span><span class="sxs-lookup"><span data-stu-id="1b3a1-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="1b3a1-114">To jest taka sama jak **nazwa** właściwość [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) polecenia cmdlet, a nie nazwę wyświetlaną ról lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="1b3a1-114">This is the same as the **Name** property of the [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet, and not the display name of the roles or features.</span></span>|
| <span data-ttu-id="1b3a1-115">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="1b3a1-115">Credential</span></span>| <span data-ttu-id="1b3a1-116">Poświadczenia używane do dodawania lub usuwania ról lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="1b3a1-116">The credentials to use to add or remove the roles or features.</span></span>|
| <span data-ttu-id="1b3a1-117">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="1b3a1-117">Ensure</span></span>| <span data-ttu-id="1b3a1-118">Wskazuje, czy role i funkcje zostaną dodane.</span><span class="sxs-lookup"><span data-stu-id="1b3a1-118">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="1b3a1-119">Aby upewnić się, że role i funkcje są dodane, ustaw tę właściwość na "Brak", aby upewnić się, że role i funkcje zostały usunięte, ustaw właściwość na "Brak".</span><span class="sxs-lookup"><span data-stu-id="1b3a1-119">To ensure that the roles or features are added, set this property to "Present" To ensure that the roles or features are removed, set the property to "Absent".</span></span>|
| <span data-ttu-id="1b3a1-120">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="1b3a1-120">IncludeAllSubFeature</span></span>| <span data-ttu-id="1b3a1-121">Ta właściwość jest ustawiana **$true** uwzględnienie wszystkich wymaganych podfunkcje z funkcji z **nazwa** właściwości.</span><span class="sxs-lookup"><span data-stu-id="1b3a1-121">Set this property to **$true** to include all required subfeatures with of the features you specify with the **Name** property.</span></span>|
| <span data-ttu-id="1b3a1-122">Ścieżka dziennika</span><span class="sxs-lookup"><span data-stu-id="1b3a1-122">LogPath</span></span>| <span data-ttu-id="1b3a1-123">Ścieżka do pliku dziennika miejscu dostawcy zasobów do operacji logowania.</span><span class="sxs-lookup"><span data-stu-id="1b3a1-123">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="1b3a1-124">dependsOn</span><span class="sxs-lookup"><span data-stu-id="1b3a1-124">DependsOn</span></span>| <span data-ttu-id="1b3a1-125">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="1b3a1-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1b3a1-126">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="1b3a1-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="1b3a1-127">Źródło</span><span class="sxs-lookup"><span data-stu-id="1b3a1-127">Source</span></span>| <span data-ttu-id="1b3a1-128">Określa lokalizację pliku źródłowego do użycia na potrzeby instalacji, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="1b3a1-128">Indicates the location of the source file to use for installation, if necessary.</span></span>|

## <a name="example"></a><span data-ttu-id="1b3a1-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b3a1-129">Example</span></span>

<span data-ttu-id="1b3a1-130">Następująca konfiguracja zapewnia, że **serwera sieci Web** (IIS) i **serwera SMTP** funkcji wraz z wszystkimi podfunkcjami, są zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="1b3a1-130">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        }
    }
}
```