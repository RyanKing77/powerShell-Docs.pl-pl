---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Pakiety z zgodne wersje programu PowerShell lub systemu operacyjnego
ms.openlocfilehash: 8230866561d3021379a48cc2c83fb4104a4058c1
ms.sourcegitcommit: d396d0e4cfe3d279f399c17e7337380a31d373ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2018
ms.locfileid: "53747708"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a>Pakiety z zgodne wersje programu PowerShell lub systemów operacyjnych

Począwszy od wersji 5.1 program PowerShell jest dostępny w różnych wersjach, które charakteryzują się różnymi zestawami funkcji i możliwości platformy.

## <a name="searching-by-powershell-edition"></a>Wyszukiwanie według wersji programu PowerShell 
Dwie wersje programu Powershell są:
- **Wersja Desktop:** Oparta na programie .NET Framework i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w pełnych wersjach systemu Windows, takich jak instalacja Server Core i Windows Desktop.
- **Wersja Core:** Oparta na module .NET Core i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w ograniczonych wersjach systemu Windows, takich jak Nano Server i Windows IoT.

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a>Galeria programu PowerShell umożliwia filtrowanie pakietów zgodnych dla określonej wersji programu PowerShell

Jeżeli pakiet zawiera niezgodny elementami Psedition określony, są one wyświetlane jako część "Wersje programu PowerShell" na stronie wyświetlania pakietu, a także w wynikach pakietów.
Możesz również wyszukać zgodnych pakietów przy użyciu programu PowerShell.

![Strona wyświetlania elementu z elementami Psedition](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a>Wyszukaj pakiety w galerii interfejsu użytkownika, które działają w programie PowerShell Core

Za pomocą tagów: "PSEdition_Desktop" i tagów: "PSEdition_Core" do filtrów pakietów w galerii programu PowerShell.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Za pomocą tagów: "PSEdition_Core", aby wyszukać elementy zgodne z programu PowerShell Core Edition.

![Wyniki wyszukiwania dla elementów zgodnych z psedition tabeli podstawowej](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Za pomocą tagów: "PSEdition_Desktop", aby wyszukać elementy zgodne z programu PowerShell w wersji Desktop.

![Wyniki wyszukiwania dla elementów, spełniając Desktop PSEdition](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a>Wyszukaj pakiety, aby znaleźć zgodne wersje przy użyciu programu PowerShell
Można określić znaczniki, aby filtrować przy użyciu wersji programu PowerShell i systemu operacyjnego. Możesz użyć `Find-Package` polecenia cmdlet, określając `-Tag` parametru do określenia wersji (i systemu operacyjnego) przeznaczonych do pracy.
Jak to:

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a>Wyszukiwanie według systemu operacyjnego 

Ponieważ program PowerShell Core jest dostępna dla Windows, Linux i MacOS, pakietów w galerii, mogą być przeznaczone dla dowolnej kombinacji tych systemów operacyjnych. W galerii interfejsu użytkownika za pomocą następujących znaczników searchs wyszukiwać pakiety oznaczone przez system operacyjny:

- Tagi: "Windows"
- Tagi: "Linux"
- Tagi: "System MacOS" 

Można określić te znaczniki `Find-Module` (i inne polecenia cmdlet w PowerShellGet module), podobnie do następującego:

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a>Wyszukiwanie wiele możliwości

Można wyszukać pakiet, który ma wiele możliwości przy użyciu składni: 

Tagi: "Compatibility1" "Compatibility2" 

Na przykład jeśli szukasz pakietu przy użyciu programu PowerShell Core zgodności, który działa na maszynach Moje Windows i Linux, należy użyć tagów wyszukiwania:

Tagi: "PSEdition_Core" "Windows" "Linux" 

Aby przeprowadzić wyszukiwanie, przy użyciu programu PowerShell, można użyć `Find-Module` i inne polecenia cmdlet modułu PowerShellGet, podobnie do następującego:

```powewrshell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Szczegółowe informacje na temat tworzenia i znalezienie pakietów o niezgodne wersje programu PowerShell

- [Moduły z elementami PSEdition](../../concepts/module-psedition-support.md)
- [Skrypty z elementami PSEdition](../../concepts/script-psedition-support.md)
