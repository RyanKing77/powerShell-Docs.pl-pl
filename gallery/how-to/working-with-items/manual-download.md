---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galeria programu powershell, galerii programu PowerShell
title: Pobieranie pakietu ręczne
ms.openlocfilehash: 7d228ccea9b840e4850d03a7a2e3e1c71e11d95e
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523353"
---
# <a name="manual-package-download"></a>Pobieranie pakietu ręczne

Galeria programu Powershell obsługuje pobieranie pakietu z witryny sieci Web bezpośrednio, bez korzystania z polecenia cmdlet PowerShellGet. Pakiet będzie pobierana jako plik (.nupkg) pakietu NuGet, który następnie można łatwo skopiować do wewnętrznego repozytorium.

> [!NOTE]
> Pobieranie pakietu ręczne jest **nie** przeznaczony jako zamiennika dla polecenia cmdlet Install-Module.
> Pobieranie pakietu nie można zainstalować moduł lub skryptu. Zależności nie są uwzględnione w pobrany pakiet NuGet. Poniższe instrukcje znajdują się tylko do celów informacyjnych.

## <a name="using-manual-download-to-acquire-a-package"></a>Uzyskiwanie pakietu za pomocą ręcznego pobierania

Każda strona ma link do ręcznego pobierania, jak pokazano poniżej:

![Pobieranie ręczne](../../Images/Manual_Item_Download.PNG)

Aby pobrać ręcznie, kliknij **Pobierz plik raw nupkg**. Kopię pakietu skopiowane do folderu pobierania w przeglądarce o nazwie `<name>.<version>.nupkg`.

Pakiet NuGet jest archiwum ZIP z dodatkowe pliki zawierające informacje o zawartości pakietu. Niektóre przeglądarki, takich jak Internet Explorer automatycznie zastąpić `.nupkg` rozszerzenia za pomocą pliku `.zip`. Aby rozpakować pakiet, Zmień nazwę `.nupkg` plik `.zip`, jeśli to konieczne, a następnie Wyodrębnij zawartość do folderu lokalnego.

Plik pakietu NuGet zawiera następujące elementy specyficzne dla NuGet, które nie są częścią oryginalnego kodu spakowanych:

- Folder o nazwie `_rels` — zawiera `.rels` pliku, który znajduje się wykaz zależności
- Folder o nazwie `package` -zawiera dane specyficzne dla NuGet
- Plik o nazwie `[Content_Types].xml` — w tym artykule opisano, jak działają rozszerzeń, takich jak moduł PowerShellGet z NuGet
- Plik o nazwie `<name>.nuspec` — zawiera zbiorczego metadanych

## <a name="installing-powershell-modules-from-a-nuget-package"></a>Instalowanie modułów programu PowerShell z pakietu NuGet

> [!NOTE]
> Te instrukcje **nie** dają taki sam efekt, jak działa `Install-Module`. Instrukcje te spełniają minimalne wymagania. Nie są przeznaczone do używania zamiast `Install-Module`. Niektóre kroki wykonywane przez `Install-Module` nie są uwzględniane.

Jest to najłatwiejsza metoda można usunąć elementów specyficznych dla NuGet z folderu. Spowoduje to pozostawienie kod programu PowerShell utworzone przez autora pakietu. Dostępne są następujące czynności:

1. Wyodrębnij zawartość pakietu NuGet do folderu lokalnego.
2. Usuń elementy specyficzne dla NuGet z folderu.
3. Zmień nazwę folderu. Domyślna nazwa folderu jest zazwyczaj `<name>.<version>`. Wersja może zawierać "-wstępnej" Jeśli moduł jest oznaczony jako wersji wstępnej. Zmień nazwę folderu tylko do nazwy modułu. Na przykład "azurerm.storage.5.0.4-preview" staje się "azurerm.storage".
4. Skopiuj folder PSModulePath usługi.

> [!IMPORTANT]
> Ręcznego pobierania nie ma żadnych zależności wymagane przez moduł. Jeżeli pakiet zawiera zależności, muszą one zainstalowane w systemie dla tego modułu do prawidłowego działania. Galeria programu PowerShell pokazuje wszystkie zależności wymagane przez pakiet.

## <a name="installing-powershell-scripts-from-a-nuget-package"></a>Instalowanie skryptów programu PowerShell z pakietu NuGet

> [!NOTE]
> Te instrukcje **nie** dają taki sam efekt, jak działa `Install-Script`. Instrukcje te spełniają minimalne wymagania. Nie są przeznaczone do używania zamiast `Install-Script`.

To najłatwiejsza metoda jest bezpośrednio do wyodrębniania pakietu NuGet, a następnie użyj skryptu. Dostępne są następujące czynności:

1. Wyodrębnij zawartość pakietu NuGet.
2. `.PS1` Bezpośrednio z tej lokalizacji można użyć pliku w folderze.
3. Możesz usunąć elementy specyficzne dla NuGet, w tym folderze.

> [!IMPORTANT]
> Ręcznego pobierania nie ma żadnych zależności wymagane przez moduł. Jeżeli pakiet zawiera zależności, muszą one zainstalowane w systemie dla tego modułu do prawidłowego działania. Galeria programu PowerShell pokazuje wszystkie zależności wymagane przez pakiet.
