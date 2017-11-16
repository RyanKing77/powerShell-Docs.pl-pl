---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: 2c7e718bc518b332cb4303ef73b1bf5c924ca471
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a>Odnajdywanie modułu programu PowerShell, zainstalować i spisu z PowerShellGet
 
PowerShellGet znajduje się w tej wersji platformy WMF:
-   Znajdź moduł można filtrować według metadanych z parametrem - Tag
-   Znajdź moduł można filtrować według języka wyszukiwania specyficznego dla repozytorium z parametrem - filtru
-   Można znaleźć modułu filtr oparty na module zawartości — polecenie - DscResource i - zawiera parametry
-   Znajdź DscResource umożliwia odnajdywania poszczególnych zasobów DSC w repozytoria
-   Obsługa instalowania z i publikowania dla udziałów plików z NuGet

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

## <a name="new-features-in-powershellget"></a>Nowe funkcje w PowerShellGet
-   Obsługa wersji Side-by-side, w programie Windows PowerShell 5.0 lub nowszej
-   Obsługa instalacji modułu zależności
-   Trzy nowe polecenia cmdlet
    -   Get-InstalledModule
    -   Odinstaluj moduł
    -   Moduł zapisywania
    
