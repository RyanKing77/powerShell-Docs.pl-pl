---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: Nowe scenariusze i funkcje w wersji 5.1 WMF
ms.openlocfilehash: 8edea99731df44349c8bcff113a8163ba5401ccd
ms.sourcegitcommit: a9aa5e8d0fab0cbb3e4e6cff0e3ca8c0339ab4e6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="new-scenarios-and-features-in-wmf-51"></a>Nowe scenariusze i funkcje w wersji 5.1 WMF

> Uwaga: Te informacje są wstępne i mogą ulec zmianie.

## <a name="powershell-editions"></a>Wersje programu PowerShell

Od wersji 5.1 program PowerShell jest dostępny w różnych wersjach, które charakteryzują się różnymi zestawami funkcji i zgodnością z różnymi platformami.

- **Wersja Desktop:** jest oparta na programie .NET Framework i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w pełnych wersjach systemu Windows, takich jak instalacja Podstawowe funkcje serwera i system Windows dla komputerów stacjonarnych.
- **Wersja Core:** jest oparta na module .NET Core i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w ograniczonych wersjach systemu Windows, takich jak system Nano Server i Windows IoT.

**Dowiedz się więcej o korzystaniu z wersji programu PowerShell**

- [Określić uruchomiona wersja programu PowerShell przy użyciu $PSVersionTable](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Filtrowanie wyników Get-Module przez CompatiblePSEditions za pomocą parametru PSEdition](/powershell/module/microsoft.powershell.core/get-module)
- [Uniemożliwić wykonywanie skryptu, chyba że Uruchom na zgodna wersja środowiska PowerShell](/powershell/gallery/psget/script/scriptwithpseditionsupport)
- [Deklarowanie zgodności modułu do określonej wersji programu PowerShell](/powershell/gallery/psget/module/modulewithpseditionsupport)

## <a name="catalog-cmdlets"></a>Polecenia cmdlet katalogu

Dodano dwa nowe polecenia cmdlet w [Microsoft.PowerShell.Security](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security) modułu; te Generowanie i zweryfikować pliki w katalogu systemu Windows.

### <a name="new-filecatalog"></a>New-FileCatalog
--------------------------------

Nowe FileCatalog tworzy plik katalogu systemu Windows dla zestawu plików i folderów.
Ten plik katalogu zawiera wartości skrótu dla wszystkich plików w określonych ścieżek.
Użytkownicy można rozpowszechniać zestaw folderów wraz z odpowiedniego pliku wykazu reprezentujący te foldery.
Informacje te są przydatne w celu zweryfikowania, czy zmiany zostały wprowadzone do folderów od czasu utworzenia katalogu.

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

Katalog w wersji 1 i 2 są obsługiwane.
W wersji 1 używa algorytmu wyznaczania wartości skrótu SHA1 do utworzenia skróty plików; w wersji 2 używa SHA256.
2. Wersja katalogu nie jest obsługiwana w *systemu Windows Server 2008 R2* lub *Windows 7*.
Należy użyć w katalogu w wersji 2 *systemu Windows 8*, *systemu Windows Server 2012*i nowszych systemów operacyjnych.

![](../images/NewFileCatalog.jpg)

Spowoduje to utworzenie pliku wykazu.

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

Aby sprawdzić integralność pliku katalogu (Pester.cat w powyżej przykładzie), podpisz go za pomocą [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) polecenia cmdlet.

### <a name="test-filecatalog"></a>Test-FileCatalog
--------------------------------

Test FileCatalog weryfikuje katalogu, reprezentujący zestaw folderów.

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

To polecenie cmdlet porównuje wszystkie wartości skrótów plików i ich ścieżek względnych znalezione w *katalogu* z tych na *dysku*.
W przypadku wykrycia niezgodność wartości skrótu pliku i ścieżki zwraca stan jako *ValidationFailed*.
Użytkownicy mogą pobierać te informacje przy użyciu *— szczegółowe* parametru.
Wyświetla również podpisywania stan katalogu w *podpisu* właściwości, który jest odpowiednikiem wywołania [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) polecenia cmdlet na plik wykazu.
Użytkownicy mogą też pominąć każdego pliku, podczas sprawdzania poprawności przy użyciu *- FilesToSkip* parametru.

## <a name="module-analysis-cache"></a>Moduł analizy w pamięci podręcznej

Począwszy od wersji 5.1 WMF, programu PowerShell zapewnia kontrolę nad pliku, który jest używany do pamięci podręcznej dane dotyczące modułu, na przykład poleceń, które eksportuje go.

Domyślnie ta pamięć podręczna jest przechowywane w pliku `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Pamięć podręczna jest zazwyczaj odczytu przy uruchamianiu podczas wyszukiwania dla polecenia i jest zapisywany jakimś wątku w tle w po zaimportowaniu modułu.

Aby zmienić domyślną lokalizację pamięci podręcznej, ustaw `$env:PSModuleAnalysisCachePath` zmiennej środowiskowej przed uruchomieniem programu PowerShell.
Zmiany tej zmiennej środowiskowej wpływają tylko procesów podrzędnych.
Wartość powinna nazw pełną ścieżkę (takie jak nazwa pliku), programu PowerShell z uprawnieniami do tworzenia i zapisać pliki.
Aby wyłączyć pamięć podręczną plików, ustaw tę wartość nieprawidłową lokalizację, na przykład:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

To ustawia ścieżkę do urządzenia z systemem nieprawidłowy.
Jeśli programu PowerShell nie można zapisać do ścieżki, zwracany jest błąd, ale mogą przeglądać raportowania za pomocą śledzenia błędów:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Podczas zapisywania w pamięci podręcznej, programu PowerShell będzie sprawdzać dla modułów, które już nie istnieje w celu uniknięcia niepotrzebnie pamięci podręcznej.
Czasami te testy nie są pożądane, w którym to przypadku należy je wyłączyć, ustawiając:

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Ustawienie tej zmiennej środowiskowej zacznie obowiązywać natychmiast w bieżącym procesie.

## <a name="specifying-module-version"></a>Określanie wersji modułu

W wersji 5.1 WMF `using module` działa tak samo jak inne konstrukcje związanych z modułu w programie PowerShell.
Wcześniej trzeba było ma sposobu na określenie wersji danego modułu; Jeśli istnieje wiele wersji, to spowodowało wystąpienie błędu.

W WMF 5.1:

- Można użyć [ModuleSpecification — Konstruktor (Hashtable)](https://msdn.microsoft.com/library/jj136290).
Ta tabela skrótów ma tego samego formatu co `Get-Module -FullyQualifiedName`.

**Przykład:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- W przypadku wielu wersji modułu PowerShell korzysta z **samej logiki rozpoznawania** jako `Import-Module` i nie zwraca błąd — jak `Import-Module` i `Import-DscResource`.

## <a name="improvements-to-pester"></a>Ulepszenia Pester

W wersji 5.1 WMF, wersja Pester jest dostarczany z programem PowerShell zaktualizowano z 3.3.5 3.4.0, z uwzględnieniem zatwierdzania https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, która umożliwia lepsze zachowanie dla Pester na serwerze Nano.

Możesz przejrzeć zmiany w wersji 3.3.5 i 3.4.0 przez sprawdzanie pliku ChangeLog.md na: https://github.com/pester/Pester/blob/master/CHANGELOG.md
