---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galeria, PowerShell, psgallery
title: Ręczne pobieranie pakietów
ms.openlocfilehash: c0a96e866dfd27f9b2170ea540ec6dd0c67701fd
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215460"
---
# <a name="manual-package-download"></a>Ręczne pobieranie pakietów

Galeria programu PowerShell obsługuje pobieranie pakietu z witryny sieci Web bezpośrednio, bez korzystania z poleceń cmdlet PowerShellGet. Możesz pobrać dowolny pakiet jako plik pakietu NuGet (`.nupkg`), który można następnie skopiować do wewnętrznego repozytorium.

> [!NOTE]
> Ręczne pobieranie pakietu **nie** jest przeznaczone jako zamiennik dla tego `Install-Module` polecenia cmdlet.
> Pobranie pakietu nie powoduje instalacji modułu lub skryptu. Zależności nie są uwzględniane w pobranym pakiecie NuGet. Poniższe instrukcje są dostępne wyłącznie w celach informacyjnych.

## <a name="using-manual-download-to-acquire-a-package"></a>Pobieranie pakietu przy użyciu funkcji ręcznego pobierania

Każda Strona zawiera link do pobierania ręcznego, jak pokazano poniżej:

![Pobieranie ręczne](../../Images/packagedisplaypagewithpseditions.png)

Aby pobrać ręcznie, kliknij pozycję **Pobierz Nieprzetworzony plik NUPKG**. Kopia pakietu jest kopiowana do folderu pobierania dla przeglądarki o nazwie `<name>.<version>.nupkg`.

Pakiet NuGet to archiwum ZIP z dodatkowymi plikami zawierającymi informacje o zawartości pakietu. Niektóre przeglądarki, takie jak Internet Explorer, automatycznie zamieniają `.nupkg` rozszerzenie pliku na. `.zip` Aby rozwinąć pakiet, w razie potrzeby `.nupkg` Zmień nazwę `.zip`pliku na, a następnie wyodrębnij zawartość do folderu lokalnego.

Plik pakietu NuGet zawiera następujące **elementy specyficzne dla programu NuGet** , które nie są częścią oryginalnego spakowanego kodu:

- Folder o nazwie `_rels` - `.rels` zawiera plik, w którym znajdują się zależności
- Folder o nazwie `package` -zawiera dane specyficzne dla narzędzia NuGet
- Plik o nazwie `[Content_Types].xml` -opisuje, jak rozszerzenia, takie jak PowerShellGet, współpracują z pakietem NuGet
- Plik o nazwie `<name>.nuspec` -zawiera zbiorcze metadane

## <a name="installing-powershell-modules-from-a-nuget-package"></a>Instalowanie modułów programu PowerShell z pakietu NuGet

> [!NOTE]
> Te instrukcje **nie** dają tego samego wyniku jako uruchomiony `Install-Module`. Te instrukcje spełniają minimalne wymagania. Nie są one przeznaczone do zamiany na `Install-Module`.
> Niektóre kroki wykonywane przez `Install-Module` nie są uwzględniane.

Najprostszym rozwiązaniem jest usunięcie elementów specyficznych dla programu NuGet z folderu. Usunięcie elementów pozostawia kod programu PowerShell utworzony przez autora pakietu.
Aby uzyskać listę elementów specyficznych dla narzędzia NuGet, zobacz [Pobieranie pakietu przy użyciu funkcji ręcznego pobierania](#using-manual-download-to-acquire-a-package).

Dostępne są następujące czynności:

1. Wyodrębnij zawartość pakietu NuGet do folderu lokalnego.
2. Usuń elementy specyficzne dla narzędzia NuGet z folderu.
3. Zmień nazwę folderu. Domyślna nazwa folderu jest zwykle `<name>.<version>`. Wersja może obejmować `-prerelease` , czy moduł jest oznaczony jako wersja wstępna. Zmień nazwę folderu na tylko nazwę modułu. Na przykład `azurerm.storage.5.0.4-preview` zostanie `azurerm.storage`.
4. Skopiuj folder do jednego z folderów w `$env:PSModulePath value`. `$env:PSModulePath`to rozdzielany średnikami zestaw ścieżek, w których program PowerShell powinien szukać modułów.

> [!IMPORTANT]
> Pobieranie ręczne nie obejmuje żadnych zależności wymaganych przez moduł. Jeśli pakiet ma zależności, muszą one być zainstalowane w systemie, aby ten moduł działał poprawnie. W Galeria programu PowerShell są wyświetlane wszystkie zależności wymagane przez pakiet.

## <a name="installing-powershell-scripts-from-a-nuget-package"></a>Instalowanie skryptów programu PowerShell z pakietu NuGet

> [!NOTE]
> Te instrukcje **nie** dają tego samego wyniku jako uruchomiony `Install-Script`. Te instrukcje spełniają minimalne wymagania. Nie są one przeznaczone do zamiany na `Install-Script`.

Najprostszym podejściem jest wyodrębnienie pakietu NuGet, a następnie użycie skryptu bezpośrednio.

Dostępne są następujące czynności:

1. Wyodrębnij zawartość pakietu NuGet.
2. `.PS1` Plik w folderze może być używany bezpośrednio z tej lokalizacji.
3. Elementy specyficzne dla programu NuGet można usunąć w folderze.

Aby uzyskać listę elementów specyficznych dla narzędzia NuGet, zobacz [Pobieranie pakietu przy użyciu funkcji ręcznego pobierania](#using-manual-download-to-acquire-a-package).

> [!IMPORTANT]
> Pobieranie ręczne nie obejmuje żadnych zależności wymaganych przez moduł. Jeśli pakiet ma zależności, muszą one być zainstalowane w systemie, aby ten moduł działał poprawnie. W Galeria programu PowerShell są wyświetlane wszystkie zależności wymagane przez pakiet.
