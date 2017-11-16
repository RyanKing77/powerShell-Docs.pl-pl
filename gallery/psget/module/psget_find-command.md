---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: "Find — polecenie"
ms.openlocfilehash: f867f12b1c6efad30a04581c6f36c5a77a2fb2ae
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="find-command"></a>Find — polecenie

Wyszukuje poleceń programu PowerShell w modułach.

## <a name="description"></a>Opis
Polecenia cmdlet polecenia Find znajduje poleceń programu PowerShell, takie jak polecenia cmdlet, aliasy, funkcje i przepływy pracy. Polecenie Znajdź wyszukuje modułów w zarejestrowany repozytoriów.
Dla każdego polecenia wyszukującą to polecenie cmdlet zwraca obiekt PSGetCommandInfo. Obiekt PSGetCommandInfo można przekazać do polecenia cmdlet Install-Module, zainstalować moduł, który zawiera polecenie.

- Polecenie Znajdź można filtrować z parametrami wersji: MinimumVersion, RequiredVersion, AllVersions.
  - Parametry te wzajemnie się wykluczają.
  - Te parametry wersji są dozwolone tylko w przypadku nazwę jednego modułu bez żadnych symboli wieloznacznych.
  - Jeśli parametr RequiredVersion nie zostanie określony, polecenie Znajdź zwraca najnowszej wersji modułu, która jest równa lub większa niż określona wersja minimalna lub najnowszej wersji modułu, jeśli wersja minimalna nie jest określona.
  - Jeśli określono parametr RequiredVersion, Znajdź polecenie zwraca tylko wersję modułu, która dokładnie odpowiada określonej wersji.
- Polecenie Znajdź można filtrować według metadanych z parametrem - Tag
- Polecenie Znajdź można filtrować według języka wyszukiwania specyficznego dla repozytorium z parametrem - filtru.
- Polecenie Znajdź można filtrować według modułów z wszystkich lub kilku zarejestrowanych repozytoriów.

## <a name="cmdlet-syntax"></a>Składnia polecenia cmdlet
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Dokumentacja poleceń cmdlet pomocy online

[Find — polecenie](http://go.microsoft.com/fwlink/?LinkId=733636)

## <a name="example-commands"></a>Przykładowe polecenia
```powershell

# Find a specific command
Find-Command -Name Get-ScriptAnalyzerRule

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Get-ScriptAnalyzerRule              1.5.0      PSScriptAnalyzer                    PSGallery

# Find multiple commands
Find-Command -Name Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

# Find all available commands from all registered repositories
Find-Command

# Find available commands from few registered repositories
Find-Command -Repository PSGallery,PrivatePSGallery

# Find all commands in a specified repository
Find-Command -Repository PSGallery

# Find a command defined in a specific module
Find-Command -Name Get-ScriptAnalyzerRule -Module PSScriptAnalyzer

# Find commands from all versions of a module
Find-Command -ModuleName PSReadline -AllVersions

# Find commands with module name and MinimumVersion.
Find-Command -ModuleName PSReadline -MinimumVersion 1.1

# Find commands with module name and exact version
Find-Command -ModuleName AzureRM -RequiredVersion 1.4.0

# Find commands defined modules with -Filter based search. -Filter searches in description and module names
Find-Command -Filter Cookbook
Find-Command -Filter RBAC

# Find all commands with tags Azure or DSC in module metadata
Find-Command -Tag Azure, DSC

```

