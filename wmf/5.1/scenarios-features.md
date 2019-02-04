---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Nowych scenariuszy i funkcji w programie WMF 5.1
ms.openlocfilehash: b00069aad7422f86d1462a62a6c4bc8a91e46705
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686999"
---
# <a name="new-scenarios-and-features-in-wmf-51"></a>Nowych scenariuszy i funkcji w programie WMF 5.1

> Uwaga: Niniejsze informacje mają charakter wstępny i mogą ulec zmianom.

## <a name="powershell-editions"></a>Wersje programu PowerShell

Od wersji 5.1 program PowerShell jest dostępny w różnych wersjach, które charakteryzują się różnymi zestawami funkcji i zgodnością z różnymi platformami.

- **Wersja Desktop:** Oparta na programie .NET Framework i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w pełnych wersjach systemu Windows, takich jak instalacja Server Core i Windows Desktop.
- **Wersja Core:** Oparta na module .NET Core i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w ograniczonych wersjach systemu Windows, takich jak Nano Server i Windows IoT.

**Dowiedz się więcej o korzystaniu z wersje programu PowerShell**

- [Określić, działającej wersji programu PowerShell, korzystając z $PSVersionTable](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Filtrowanie wyników Get-Module przez CompatiblePSEditions przy użyciu parametru PSEdition](/powershell/module/microsoft.powershell.core/get-module)
- [Uniemożliwić wykonywanie skryptu, chyba że systemem zgodnej wersji programu PowerShell](/powershell/gallery/concepts/script-psedition-support)
- [Zadeklaruj zgodność modułu do określonej wersji programu PowerShell](/powershell/gallery/concepts/module-psedition-support)

## <a name="catalog-cmdlets"></a>Polecenia cmdlet wykazu

Dodano dwa nowe polecenia cmdlet w [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security) moduł; to Generowanie i zweryfikować pliki w katalogu Windows.

### <a name="new-filecatalog"></a>New-FileCatalog
--------------------------------

Nowe FileCatalog tworzy plik katalogu Windows dla zestawu plików i folderów.
Ten plik w katalogu zawiera skróty dla wszystkich plików w określonych ścieżek.
Użytkownicy mogą dystrybuować zestawu folderów oraz odpowiedni plik wykazu reprezentujący te foldery.
Te informacje są przydatne sprawdzić, czy zmiany zostały dokonane w folderach od czasu utworzenia katalogu.

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

Wykaz w wersji 1 i 2 są obsługiwane.
Wersja 1 używa algorytmu wyznaczania wartości skrótu SHA1 w celu utworzenia skróty plików; w wersji 2 używa SHA256.
Wykaz w wersji 2 nie jest obsługiwana w *systemu Windows Server 2008 R2* lub *Windows 7*.
Wykaz w wersji 2 powinien być używany w *systemu Windows 8*, *systemu Windows Server 2012*i nowszych systemów operacyjnych.

![](../images/NewFileCatalog.jpg)

Spowoduje to utworzenie pliku wykazu.

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

Aby sprawdzić integralność pliku wykazu (Pester.cat w powyżej przykładzie), zaloguj się za pomocą [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) polecenia cmdlet.

### <a name="test-filecatalog"></a>Test-FileCatalog
--------------------------------

Test FileCatalog weryfikuje wykazu, reprezentujący zestaw folderów.

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

To polecenie cmdlet porównuje wszystkie skróty plików i ich ścieżek względnych znalezionej we *katalogu* z tymi na *dysku*.
Jeśli wykryje niezgodność skróty plików i ścieżek zwraca stan jako *ValidationFailed*.
Użytkownicy mogą pobrać te informacje przy użyciu *— szczegółowe* parametru.
Wyświetla również podpisywania stan katalogu w *podpisu* właściwość, która jest równoważne z wywoływaniem [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) polecenie cmdlet na plik wykazu.
Użytkownicy mogą również pomijać każdego pliku podczas weryfikacji za pomocą *- FilesToSkip* parametru.

## <a name="module-analysis-cache"></a>Moduł analizy w pamięci podręcznej

Począwszy od programu WMF 5.1 program PowerShell zapewnia kontrolę nad pliku, który jest używany do pamięci podręcznej dane dotyczące modułu, na przykład polecenia, które eksportuje ona.

Domyślnie ta pamięć podręczna znajduje się w pliku `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Pamięć podręczna jest zwykle do odczytu przy uruchamianiu podczas wyszukiwania dla polecenia i jest zapisywany trochę czasu w wątku tła w po zaimportowaniu modułu.

Aby zmienić domyślną lokalizację pamięci podręcznej, należy ustawić `$env:PSModuleAnalysisCachePath` zmiennej środowiskowej przed uruchomieniem programu PowerShell.
Zmiany w tej zmiennej środowiskowej mają wpływ tylko na procesy podrzędne.
Pełna ścieżka (takie jak nazwa pliku), programu PowerShell z uprawnieniami do tworzenia i zapisywać pliki należy nadać nazwę wartości.
Aby wyłączyć pamięć podręczną plików, należy ustawić tę wartość w nieprawidłowej lokalizacji, na przykład:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

To ustawia ścieżkę do nieprawidłowe urządzenie.
Jeśli programu PowerShell nie można zapisać do ścieżki, zwracany jest błąd braku, ale możesz zobaczyć raportowania za pomocą śledzenia błędów:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Podczas pisania, limit pamięci podręcznej, programu PowerShell będzie sprawdzać modułów, które już nie istnieją, aby uniknąć niepotrzebnego dużej pamięci podręcznej.
Czasami te testy nie są pożądane, w którym to przypadku należy je wyłączyć, ustawiając:

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Ustawienie tej zmiennej środowiskowej zacznie obowiązywać natychmiast w bieżącym procesie.

## <a name="specifying-module-version"></a>Określanie wersji modułu

W program WMF 5.1 `using module` działa tak samo jak inne konstrukcje związane z modułu w programie PowerShell.
Miała wcześniej, można określić wersji określonego modułu; Jeśli istnieje wiele wersji, to zakończyło się błędem.

W programie WMF 5.1:

- Możesz użyć [ModuleSpecification konstruktora (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).
Ta tabela skrótów ma tego samego formatu co `Get-Module -FullyQualifiedName`.

**Przykład:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- W przypadku wielu wersji modułu programu PowerShell używa **tę samą logikę rozpoznawania** jako `Import-Module` i nie zwraca błąd--takie samo zachowanie jako `Import-Module` i `Import-DscResource`.

## <a name="improvements-to-pester"></a>Ulepszenia Pester

W program WMF 5.1 wersję usług Pester który jest dostarczany za pomocą programu PowerShell została zaktualizowana z 3.3.5 3.4.0 dodając zatwierdzenia https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, która umożliwia lepsze zachowanie dla usług Pester na serwerze Nano Server.

Możesz przejrzeć zmiany wprowadzone w wersjach 3.3.5 do 3.4.0, sprawdzając plik ChangeLog.md w lokalizacji: https://github.com/pester/Pester/blob/master/CHANGELOG.md
