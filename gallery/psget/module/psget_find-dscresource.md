---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: "Znajdź DscResource"
ms.openlocfilehash: 37ba7925d6f73c453126f25e0818b3f8839d3b3b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="find-dscresource"></a><span data-ttu-id="ccd26-103">Znajdź DscResource</span><span class="sxs-lookup"><span data-stu-id="ccd26-103">Find-DscResource</span></span>

<span data-ttu-id="ccd26-104">Umożliwia znalezienie zasobów DSC w modułach.</span><span class="sxs-lookup"><span data-stu-id="ccd26-104">Finds DSC Resources in modules.</span></span>

## <a name="description"></a><span data-ttu-id="ccd26-105">Opis</span><span class="sxs-lookup"><span data-stu-id="ccd26-105">Description</span></span>

<span data-ttu-id="ccd26-106">Polecenia cmdlet Find DscResource znajduje [konfiguracji żądanego stanu (DSC)](https://msdn.microsoft.com/en-us/PowerShell/dsc/overview) zasoby zawarte w modułach, spełniających określone kryteria z zarejestrowanych repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="ccd26-106">The Find-DscResource cmdlet finds [Desired State Configuration (DSC)](https://msdn.microsoft.com/en-us/PowerShell/dsc/overview) resources contained in modules that match the specified criteria from registered repositories.</span></span>
<span data-ttu-id="ccd26-107">Dla każdego modułu znajdzie tego polecenia cmdlet Znajdź DscResource zwraca obiekt PSGetDscResourceInfo za pomocą którego można przekazać do instalacji — modułu, aby zainstalować moduły zawierający zasoby, które to polecenie cmdlet zwraca.</span><span class="sxs-lookup"><span data-stu-id="ccd26-107">For each module that this cmdlet finds, Find-DscResource returns a PSGetDscResourceInfo object that you can pipe to Install-Module to install the modules containing the resources that this cmdlet returns.</span></span>

<span data-ttu-id="ccd26-108">DSC jest nowa platforma zarządzania w programie Windows PowerShell, która umożliwia wdrażanie i zarządzanie dane konfiguracyjne usługi oprogramowania i zarządzanie środowisko, w którym są uruchomione następujące usługi.</span><span class="sxs-lookup"><span data-stu-id="ccd26-108">DSC is a new management platform in Windows PowerShell that enables deploying and managing configuration data for software services and managing the environment in which these services run.</span></span>

<span data-ttu-id="ccd26-109">Żądana Konfiguracja stanu (DSC) zasoby dostarczają bloków konstrukcyjnych dla konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="ccd26-109">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="ccd26-110">Zasób udostępnia właściwości, które mogą być skonfigurowane (schemat) i zawiera funkcje skryptu programu PowerShell, które wywołuje lokalnego Menedżera konfiguracji (LCM) umożliwia "tak".</span><span class="sxs-lookup"><span data-stu-id="ccd26-110">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="ccd26-111">Zasób może modelu coś jako ogólnego jako plik lub jako określone w ustawieniach serwera IIS.</span><span class="sxs-lookup"><span data-stu-id="ccd26-111">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span> <span data-ttu-id="ccd26-112">Grupy takich jak zasoby połączone w Module DSC organizuje wszystkie wymagane pliki w strukturze przenośnego i zawierający metadane, aby określić, jak zasoby są przeznaczone do użycia.</span><span class="sxs-lookup"><span data-stu-id="ccd26-112">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

- <span data-ttu-id="ccd26-113">Znajdź DscResource można filtrować z parametrami wersji: MinimumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="ccd26-113">Find-DscResource can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="ccd26-114">Parametry te wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="ccd26-114">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="ccd26-115">Te parametry wersji są dozwolone tylko w przypadku nazwę jednego modułu bez żadnych symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="ccd26-115">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="ccd26-116">Jeśli nie określono parametru RequiredVersion, Znajdź DscResource zwraca najnowszej wersji modułu, która jest równa lub większa niż określona wersja minimalna lub najnowszej wersji modułu, jeśli wersja minimalna nie jest określona.</span><span class="sxs-lookup"><span data-stu-id="ccd26-116">If the RequiredVersion parameter is not specified, Find-DscResource returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="ccd26-117">Jeśli określono parametr RequiredVersion, Znajdź DscResource zwraca tylko wersję modułu, która dokładnie odpowiada określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="ccd26-117">If the RequiredVersion parameter is specified, Find-DscResource only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="ccd26-118">Znajdź DscResource można filtrować według metadanych z parametrem - Tag</span><span class="sxs-lookup"><span data-stu-id="ccd26-118">Find-DscResource can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="ccd26-119">Znajdź DscResource można filtrować według języka wyszukiwania specyficznego dla repozytorium z parametrem - filtru.</span><span class="sxs-lookup"><span data-stu-id="ccd26-119">Find-DscResource can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="ccd26-120">Znajdź DscResource można filtrować według modułów z wszystkich lub kilku zarejestrowanych repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="ccd26-120">Find-DscResource can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="ccd26-121">Składnia polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="ccd26-121">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="ccd26-122">Dokumentacja poleceń cmdlet pomocy online</span><span class="sxs-lookup"><span data-stu-id="ccd26-122">Cmdlet online help reference</span></span>

[<span data-ttu-id="ccd26-123">Znajdź DscResource</span><span class="sxs-lookup"><span data-stu-id="ccd26-123">Find-DscResource</span></span>](http://go.microsoft.com/fwlink/?LinkId=517196)

## <a name="example-commands"></a><span data-ttu-id="ccd26-124">Przykładowe polecenia</span><span class="sxs-lookup"><span data-stu-id="ccd26-124">Example commands</span></span>
```powershell

# Find a specific DSC Resource
Find-DscResource -Name xIisFeatureDelegation

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
xIisFeatureDelegation               1.10.0.0   xWebAdministration                  PSGallery

# Find all available DSC Resources from all registered repositories
Find-DscResource

# Find a DSC resource by name
Find-DscResource -Name xWebsite

# Find multiple DSC Resources
Find-DscResource -Name xIisHandler, xFirewall

# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking
Find-DscResource -ModuleName xWebAdministration

# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

# Find available DSC Resources from few registered repositories
Find-DscResource -Repository PSGallery,PrivatePSGallery

# Find all DSC Resources in a specified repository
Find-DscResource -Repository PSGallery

# Find DSC Resources from all versions of a module
Find-DscResource -ModuleName xNetworking -AllVersions

# Find DSC Resources with module name and MinimumVersion.
Find-DscResource -ModuleName xNetworking -MinimumVersion 1.1

# Find DSC Resources with module name and exact version
Find-DscResource -ModuleName xNetworking -RequiredVersion 2.1.1

# Find DSC Resources defined modules with -Filter based search. -Filter searches in description and module names
Find-DscResource -Filter Domain

# Find all DSC Resources with tags Azure or DSC in module metadata
Find-DscResource -Tag Azure, DSC

```

