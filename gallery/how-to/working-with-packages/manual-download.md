---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galeria programu powershell, galerii programu PowerShell
title: Ręczne pobieranie pakietów
ms.openlocfilehash: 57baa14089b803f58c42ccb54553ecace841e34b
ms.sourcegitcommit: e24525046dd37166b9d83eeecdc534726316f429
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2018
ms.locfileid: "52742826"
---
# <a name="manual-package-download"></a>Ręczne pobieranie pakietów

Galeria programu Powershell obsługuje pobieranie pakietu z witryny sieci Web bezpośrednio, bez korzystania z polecenia cmdlet PowerShellGet. Możesz pobrać dowolny pakiet jako plik (.nupkg) pakietu NuGet, który można następnie skopiować do wewnętrznego repozytorium.

> [!NOTE]
> Pobieranie pakietu ręczne jest **nie** przeznaczony jako zamiennika dla polecenia cmdlet Install-Module.
> Pobieranie pakietu nie można zainstalować moduł lub skryptu. Zależności nie są uwzględnione w pobrany pakiet NuGet. Poniższe instrukcje znajdują się tylko do celów informacyjnych.

## <a name="using-manual-download-to-acquire-a-package"></a>Uzyskiwanie pakietu za pomocą ręcznego pobierania

Każda strona ma link do ręcznego pobierania, jak pokazano poniżej:

![Pobieranie ręczne](../../Images/packagedisplaypagewithpseditions.png)

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
4. Skopiuj folder na jednym z folderów w `$env:PSModulePath value`. `$env:PSModulePath` to zbiór rozdzielaną średnikami ścieżki, w których programu PowerShell należy szukać modułów.

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
