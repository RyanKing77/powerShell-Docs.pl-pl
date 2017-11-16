---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: "Znajdź RoleCapability"
ms.openlocfilehash: 77c5b492d9681fa05315401fba410c508af1d13b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="find-rolecapability"></a>Znajdź RoleCapability

Znajduje rolę funkcji w modułach.

## <a name="description"></a>Opis
Polecenia cmdlet Find RoleCapability znajduje możliwości roli programu PowerShell w modułach. Znajdź RoleCapability wyszukuje modułów w zarejestrowany repozytoriów. Dla każdej funkcji roli wyszukującą to polecenie cmdlet zwraca obiekt PSGetRoleCapabilityInfo. Obiekt PSGetRoleCapabilityInfo można przekazać do polecenia cmdlet Install-Module zainstalować moduł, który zawiera możliwości roli.
Możliwości roli programu PowerShell definiują, które polecenia, aplikacji i tak dalej są dostępne dla użytkownika w punkcie końcowym tylko tyle administracyjnej (JEA). Możliwości roli są definiowane przez pliki z rozszerzeniem .psrc.

- Znajdź RoleCapability można filtrować z parametrami wersji: MinimumVersion, RequiredVersion, AllVersions.
  - Parametry te wzajemnie się wykluczają.
  - Te parametry wersji są dozwolone tylko w przypadku nazwę jednego modułu bez żadnych symboli wieloznacznych.
  - Jeśli nie określono parametru RequiredVersion, Znajdź RoleCapability zwraca najnowszej wersji modułu, która jest równa lub większa niż określona wersja minimalna lub najnowszej wersji modułu, jeśli wersja minimalna nie jest określona.
  - Jeśli określono parametr RequiredVersion, Znajdź RoleCapability zwraca tylko wersję modułu, która dokładnie odpowiada określonej wersji.
- Znajdź RoleCapability można filtrować według metadanych z parametrem - Tag
- Znajdź RoleCapability można filtrować według języka wyszukiwania specyficznego dla repozytorium z parametrem - filtru.
- Znajdź RoleCapability można filtrować według modułów z wszystkich lub kilku zarejestrowanych repozytoriów.

## <a name="cmdlet-syntax"></a>Składnia polecenia cmdlet
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Dokumentacja poleceń cmdlet pomocy online

[Znajdź RoleCapability](http://go.microsoft.com/fwlink/?LinkId=718029)

## <a name="example-commands"></a>Przykładowe polecenia
```powershell

# Find a specific role capability
Find-RoleCapability -Name Maintenance

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Maintenance                         1.5.0      RoleCapModule                       PrivatePSGallery

# Find multiple role capabilities
Find-RoleCapability -Name MyJeaRole, Maintenance

# Find all available role capabilities from all registered repositories
Find-RoleCapability

# Find available role capabilities from few registered repositories
Find-RoleCapability -Repository PSGallery,PrivatePSGallery

# Find all role capabilities in a specified repository
Find-RoleCapability -Repository PSGallery

# Find a role capability defined in a specific module
Find-RoleCapability -Name Maintenance -ModuleName RoleCapModule

# Find role capabilities from all versions of a module
Find-RoleCapability -ModuleName RoleCapModule -AllVersions

# Find role capabilities with module name and MinimumVersion.
Find-RoleCapability -ModuleName RoleCapModule -MinimumVersion 1.1

# Find role capabilities with module name and exact version
Find-RoleCapability -ModuleName RoleCapModule -RequiredVersion 1.4.0

# Find role capabilities defined modules with -Filter based search. -Filter searches in description and module names
Find-RoleCapability -Filter Cookbook
Find-RoleCapability -Filter RBAC

# Find all role capabilities with tags Azure or DSC in module metadata
Find-RoleCapability -Tag Azure, DSC

```

