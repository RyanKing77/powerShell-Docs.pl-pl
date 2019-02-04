---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a0b1573611c5d4232082c19ca19b4cca79d0699e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685256"
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a>Odnajdywanie modułu programu PowerShell, instalowanie i tworzenie spisu przy użyciu funkcji PowerShellGet

Moduł PowerShellGet znajduje się w tej wersji programu WMF:
-   Znajdź moduł może filtrować metadane modułu z parametrem - Tag
-   Znajdź moduł może filtrować języka specyficznego dla repozytorium wyszukiwania za pomocą parametru - Filter
-   Można znaleźć modułu filtru opartego na module zawartości za pomocą polecenia-, - DscResource i - zawierają parametry
-   Znajdź-DscResource umożliwia wykrywanie poszczególne zasoby DSC w repozytoriach
-   Obsługa instalowania z i publikowania udziałami plików za pomocą NuGet

## <a name="example-commands"></a>Przykładowe polecenia
```powershell
\# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

\# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

\#Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

\# Find all modules with Dsc resources
Find-Module -Includes DscResource

\# Find all modules with cmdlets
Find-Module -Includes Cmdlet

\# Find all modules with functions
Find-Module -Includes Function

\# Find all DSC resources
Find-DscResource

\# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking

\# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

\# Find modules using -Filter parameter
\# Specified filter value is searched in Name and Description properties
Find-Module -Filter Cookbook -Repository PSGallery
Find-Module -Filter RBAC -Repository PSGallery
```

## <a name="new-features-in-powershellget"></a>Nowe funkcje w moduł PowerShellGet
-   Obsługa wersji Side-by-side, w programie Windows PowerShell 5.0 lub nowszy
-   Obsługa instalacji zależności modułów
-   Trzy nowe polecenia cmdlet
    -   Get-InstalledModule
    -   Odinstalowanie modułu
    -   Save-Module
