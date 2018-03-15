---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: "Znajdź DscResource"
ms.openlocfilehash: 6c5713f122d48e9c9d5e0aa45dc14047afc56102
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="find-dscresource"></a>Znajdź DscResource

Umożliwia znalezienie zasobów DSC w modułach.

## <a name="description"></a>Opis

Polecenia cmdlet Find DscResource znajduje [konfiguracji żądanego stanu (DSC)](https://msdn.microsoft.com/PowerShell/dsc/overview) zasoby zawarte w modułach, spełniających określone kryteria z zarejestrowanych repozytoriów.
Dla każdego modułu znajdzie tego polecenia cmdlet Znajdź DscResource zwraca obiekt PSGetDscResourceInfo za pomocą którego można przekazać do instalacji — modułu, aby zainstalować moduły zawierający zasoby, które to polecenie cmdlet zwraca.

DSC jest nowa platforma zarządzania w programie Windows PowerShell, która umożliwia wdrażanie i zarządzanie dane konfiguracyjne usługi oprogramowania i zarządzanie środowisko, w którym są uruchomione następujące usługi.

Żądana Konfiguracja stanu (DSC) zasoby dostarczają bloków konstrukcyjnych dla konfiguracji DSC. Zasób udostępnia właściwości, które mogą być skonfigurowane (schemat) i zawiera funkcje skryptu programu PowerShell, które wywołuje lokalnego Menedżera konfiguracji (LCM) umożliwia "tak".

Zasób może modelu coś jako ogólnego jako plik lub jako określone w ustawieniach serwera IIS. Grupy takich jak zasoby połączone w Module DSC organizuje wszystkie wymagane pliki w strukturze przenośnego i zawierający metadane, aby określić, jak zasoby są przeznaczone do użycia.

- Znajdź DscResource można filtrować z parametrami wersji: MinimumVersion, RequiredVersion, AllVersions.
  - Parametry te wzajemnie się wykluczają.
  - Te parametry wersji są dozwolone tylko w przypadku nazwę jednego modułu bez żadnych symboli wieloznacznych.
  - Jeśli nie określono parametru RequiredVersion, Znajdź DscResource zwraca najnowszej wersji modułu, która jest równa lub większa niż określona wersja minimalna lub najnowszej wersji modułu, jeśli wersja minimalna nie jest określona.
  - Jeśli określono parametr RequiredVersion, Znajdź DscResource zwraca tylko wersję modułu, która dokładnie odpowiada określonej wersji.
- Znajdź DscResource można filtrować według metadanych z parametrem - Tag
- Znajdź DscResource można filtrować według języka wyszukiwania specyficznego dla repozytorium z parametrem - filtru.
- Znajdź DscResource można filtrować według modułów z wszystkich lub kilku zarejestrowanych repozytoriów.

## <a name="cmdlet-syntax"></a>Składnia polecenia cmdlet
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Dokumentacja poleceń cmdlet pomocy online

[Find-DscResource](http://go.microsoft.com/fwlink/?LinkId=517196)

## <a name="example-commands"></a>Przykładowe polecenia
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

