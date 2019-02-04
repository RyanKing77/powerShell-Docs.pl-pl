---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób Windowsfeatureset DSC
ms.openlocfilehash: 8b7c7e72dd58459bd19cb723e5790a82841515c0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684794"
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="97058-103">Zasób Windowsfeatureset DSC</span><span class="sxs-lookup"><span data-stu-id="97058-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="97058-104">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="97058-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="97058-105">**WindowsFeatureSet** zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm, aby upewnić się, że role i funkcje są dodawane lub usuwane w węźle docelowym.</span><span class="sxs-lookup"><span data-stu-id="97058-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>
<span data-ttu-id="97058-106">Ten zasób jest [złożonego zasobów](../../../resources/authoringResourceComposite.md) wywołująca [zasób WindowsFeature](windowsfeatureResource.md) dla każdej funkcji, określone w `Name` właściwości.</span><span class="sxs-lookup"><span data-stu-id="97058-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="97058-107">Korzystając z tego zasobu, gdy użytkownik chce skonfigurować pewną liczbę funkcji Windows na tym samym stanie.</span><span class="sxs-lookup"><span data-stu-id="97058-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="97058-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="97058-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="97058-109">Właściwości</span><span class="sxs-lookup"><span data-stu-id="97058-109">Properties</span></span>

|  <span data-ttu-id="97058-110">Właściwość</span><span class="sxs-lookup"><span data-stu-id="97058-110">Property</span></span>  |  <span data-ttu-id="97058-111">Opis</span><span class="sxs-lookup"><span data-stu-id="97058-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="97058-112">Nazwa</span><span class="sxs-lookup"><span data-stu-id="97058-112">Name</span></span>| <span data-ttu-id="97058-113">Nazwy ról lub funkcji, które chcesz, aby upewnić się, są dodawane lub usuwane.</span><span class="sxs-lookup"><span data-stu-id="97058-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="97058-114">To jest taka sama jak **nazwa** właściwość [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) polecenia cmdlet, a nie nazwę wyświetlaną ról lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="97058-114">This is the same as the **Name** property of the [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet, and not the display name of the roles or features.</span></span>|
| <span data-ttu-id="97058-115">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="97058-115">Credential</span></span>| <span data-ttu-id="97058-116">Poświadczenia używane do dodawania lub usuwania ról lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="97058-116">The credentials to use to add or remove the roles or features.</span></span>|
| <span data-ttu-id="97058-117">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="97058-117">Ensure</span></span>| <span data-ttu-id="97058-118">Wskazuje, czy dodać ról lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="97058-118">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="97058-119">Aby upewnić się, że ról lub funkcji dodano, ustaw tę właściwość na "Obecny", aby upewnić się, czy role i funkcje zostały usunięte, należy ustawić właściwość na "Brak".</span><span class="sxs-lookup"><span data-stu-id="97058-119">To ensure that the roles or features are added, set this property to "Present" To ensure that the roles or features are removed, set the property to "Absent".</span></span>|
| <span data-ttu-id="97058-120">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="97058-120">IncludeAllSubFeature</span></span>| <span data-ttu-id="97058-121">Ustaw tę właściwość na **$true** obejmujący wszystkie wymagane podfunkcje przy użyciu funkcji, należy określić przy użyciu **nazwa** właściwości.</span><span class="sxs-lookup"><span data-stu-id="97058-121">Set this property to **$true** to include all required subfeatures with of the features you specify with the **Name** property.</span></span>|
| <span data-ttu-id="97058-122">Ścieżka dziennika</span><span class="sxs-lookup"><span data-stu-id="97058-122">LogPath</span></span>| <span data-ttu-id="97058-123">Ścieżka do pliku dziennika, w której chcesz dostawcy zasobów do dziennika operacji.</span><span class="sxs-lookup"><span data-stu-id="97058-123">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="97058-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="97058-124">DependsOn</span></span>| <span data-ttu-id="97058-125">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="97058-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="97058-126">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="97058-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="97058-127">Źródło</span><span class="sxs-lookup"><span data-stu-id="97058-127">Source</span></span>| <span data-ttu-id="97058-128">Wskazuje lokalizację pliku źródłowego na potrzeby instalacji, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="97058-128">Indicates the location of the source file to use for installation, if necessary.</span></span>|

## <a name="example"></a><span data-ttu-id="97058-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="97058-129">Example</span></span>

<span data-ttu-id="97058-130">Następująca konfiguracja zapewnia, że **serwera sieci Web** (IIS) i **serwera SMTP** funkcji wraz z wszystkimi podfunkcjami każdego, są zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="97058-130">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

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
