---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Informacje o wersji programu WMF 5.x
ms.openlocfilehash: 8bdc423234cf0b104b72b1bee1de35e50783d8a4
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856399"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a>Windows Management Framework (WMF) 5.x Release Notes

## <a name="wmf-50-changes"></a>WMF 5.0 Changes

- PowerShell 5.0 dodaje nową strukturę **informacji** strumienia
- Ulepszenia DSC łącznie cztery nowe zasoby DSC:
  - WindowsFeatureSet
  - WindowsOptionalFeatureSet
  - ServiceSet
  - ProcessSet
- Dodano Just Enough Administration umożliwiające administracji opartej na rolach za pomocą komunikacji zdalnej programu PowerShell
- PowerShell 5.0 rozszerza język klasy zdefiniowane przez użytkownika i wyliczenia
- Ulepszone debugowanie funkcji w środowisku PowerShell ISE i dodano zdalnego debugowania
- Z dodanych modułów modułu PowerShellGet oraz funkcji PackageManagement
- Rejestrowanie udoskonalone skrypt programu PowerShell i zapisy
- Dodano polecenia cmdlet składnię komunikatów kryptograficznych
- Program WMF 5.0 zawiera moduł NetworkSwitchManager for Windows
- Dodano moduł Microsoft.PowerShell.ODataUtils
- Dodano obsługę dla rejestrowania spisu oprogramowania (SIL)
- Nowy serwer lub zaktualizujesz poleceń cmdlet w odpowiedzi na problemów i żądań użytkowników

## <a name="wmf-51-changes"></a>Zmiany w programie WMF 5.1

Program WMF 5.1 obejmuje składniki programu PowerShell, usługi WMI, usługi WinRM i rejestrowania spisu oprogramowania (SIL), które zostały wydane z systemem Windows Server 2016. Program WMF 5.1 można zainstalować na Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 i 2012 R2 i udostępnia kilka następujących ulepszeń w porównaniu z tym program WMF 5.0:

- Nowe polecenia cmdlet
- Ulepszenia rozwiązania PowerShellGet obejmują wymuszanie podpisanych modułów i instalowanie modułów JEA
- Dodano obsługę funkcji PackageManagement na potrzeby kontenerów, instalacji CBS, instalacji opartej na plikach EXE i pakietów CAB
- Ulepszenia debugowania dla klas konfiguracji DSC i programu PowerShell
- Ulepszenia zabezpieczeń obejmują wymuszanie modułów podpisanych w wykazie pochodzących z serwera ściągania oraz w przypadku korzystania z poleceń cmdlet PowerShellGet
- Odpowiedzi na wiele problemów i żądań użytkowników

## <a name="powershell-editions"></a>Wersje programu PowerShell

Począwszy od wersji 5.1 PowerShell jest dostępny w różnych wersjach, które wyznaczają różnymi zestawami funkcji i zgodności platformy.

- **Wersja Desktop:** Oparta na programie .NET Framework i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w pełnych wersjach systemu Windows, takich jak instalacja Server Core i Windows Desktop.
- **Wersja Core:** Oparta na module .NET Core i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w ograniczonych wersjach systemu Windows, takich jak Nano Server i Windows IoT.

### <a name="learn-more-about-using-powershell-editions"></a>Dowiedz się więcej o korzystaniu z wersje programu PowerShell

- [Określić, działającej wersji programu PowerShell, korzystając z $PSVersionTable](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Filtrowanie wyników Get-Module przez CompatiblePSEditions przy użyciu parametru PSEdition](/powershell/module/microsoft.powershell.core/get-module)
- [Uniemożliwić wykonywanie skryptu, chyba że systemem zgodnej wersji programu PowerShell](/powershell/gallery/concepts/script-psedition-support)
- [Zadeklaruj zgodność modułu do określonej wersji programu PowerShell](/powershell/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a>Moduł analizy w pamięci podręcznej

Począwszy od programu WMF 5.1 program PowerShell zapewnia kontrolę nad pliku, który jest używany do pamięci podręcznej dane dotyczące modułu, na przykład polecenia, które eksportuje ona.

Domyślnie ta pamięć podręczna znajduje się w pliku `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`. Pamięć podręczna jest zwykle do odczytu przy uruchamianiu podczas wyszukiwania dla polecenia i jest zapisywany trochę czasu w wątku tła w po zaimportowaniu modułu.

Aby zmienić domyślną lokalizację pamięci podręcznej, należy ustawić `$env:PSModuleAnalysisCachePath` zmiennej środowiskowej przed uruchomieniem programu PowerShell. Zmiany w tej zmiennej środowiskowej mają wpływ tylko na procesy podrzędne. Pełna ścieżka (takie jak nazwa pliku), programu PowerShell z uprawnieniami do tworzenia i zapisywać pliki należy nadać nazwę wartości. Aby wyłączyć pamięć podręczną plików, należy ustawić tę wartość w nieprawidłowej lokalizacji, na przykład:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

To ustawia ścieżkę do nieprawidłowe urządzenie. Jeśli programu PowerShell nie można zapisać do ścieżki, zwracany jest błąd braku, ale możesz zobaczyć raportowania za pomocą śledzenia błędów:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Podczas pisania, limit pamięci podręcznej, programu PowerShell będzie sprawdzać modułów, które już nie istnieją, aby uniknąć niepotrzebnego dużej pamięci podręcznej. Czasami te testy nie są pożądane, w którym to przypadku należy je wyłączyć, ustawiając:

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

W program WMF 5.1 wersję usług Pester który jest dostarczany za pomocą programu PowerShell ma został zaktualizowany z 3.3.5 3.4.0.
Ta aktualizacja umożliwia lepsze zachowanie dla usług Pester na serwerze Nano Server.

Możesz przejrzeć zmiany w szkodnikami, sprawdzając [dziennika zmian](https://github.com/pester/Pester/blob/master/CHANGELOG.md) w repozytorium GitHub.
