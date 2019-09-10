---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Informacje o wersji programu WMF 5.x
ms.openlocfilehash: 8924240a4bbedcd34bc68b7cacdd23189a3716d6
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848142"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a>Informacje o wersji systemu Windows Management Framework (WMF) 5. x

## <a name="wmf-50-changes"></a>Zmiany w programie WMF 5,0

- Program PowerShell 5,0 dodaje nowy strumień **informacji o** strukturze
- Ulepszenia konfiguracji DSC, w tym cztery nowe zasoby DSC:
  - Zasób windowsfeatureset
  - Zasób windowsoptionalfeatureset
  - Zasób serviceset
  - Zasób processset
- Dodano tylko wystarczającą administrację, aby umożliwić administrację opartą na rolach za pośrednictwem komunikacji zdalnej programu PowerShell
- Program PowerShell 5,0 rozszerza język, tak aby obejmował klasy i wyliczenia zdefiniowane przez użytkownika
- Udoskonalone funkcje debugowania w programie PowerShell ISE i dodane debugowanie zdalne
- Dodano moduły PowerShellGet i PackageManagement
- Ulepszone rejestrowanie i transkrypcje skryptu programu PowerShell
- Dodawanie poleceń cmdlet składni wiadomości kryptograficznych
- Program WMF 5,0 zawiera moduł NetworkSwitchManager dla systemu Windows
- Dodano moduł Microsoft. PowerShell. ODataUtils
- Dodano obsługę rejestrowania spisu oprogramowania (SIL)
- Nowe lub zaktualizowane polecenia cmdlet w odpowiedzi na żądania i problemy użytkowników

## <a name="wmf-51-changes"></a>Zmiany w programie WMF 5,1

Program WMF 5,1 zawiera składniki programu PowerShell, usługi WMI, usługi WinRM i spisu oprogramowania SIL, które zostały wydane z systemem Windows Server 2016. Program WMF 5,1 można zainstalować w systemie Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 i 2012 R2 i oferuje kilka ulepszeń w porównaniu z modelem 5,0 WMF, w tym:

- Nowe polecenia cmdlet
- Ulepszenia rozwiązania PowerShellGet obejmują wymuszanie podpisanych modułów i instalowanie modułów JEA
- Dodano obsługę funkcji PackageManagement na potrzeby kontenerów, instalacji CBS, instalacji opartej na plikach EXE i pakietów CAB
- Ulepszenia debugowania dla klas konfiguracji DSC i programu PowerShell
- Ulepszenia zabezpieczeń obejmują wymuszanie modułów podpisanych w wykazie pochodzących z serwera ściągania oraz w przypadku korzystania z poleceń cmdlet PowerShellGet
- Odpowiedzi na wiele problemów i żądań użytkowników

> [!IMPORTANT]
> Przed zainstalowaniem programu WMF 5,1 w systemie Windows Server 2008 lub Windows 7 upewnij się, że nie zainstalowano plików WMF 3,0. Aby uzyskać więcej informacji, zobacz [wymagania wstępne dotyczące WMF 5,1 dla systemu Windows Server 2008 R2 z dodatkiem SP1 i Windows 7 z dodatkiem SP1](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1).

## <a name="powershell-editions"></a>Wersje programu PowerShell

Począwszy od wersji 5,1, program PowerShell jest dostępny w różnych wersjach, które oznaczają różne zestawy funkcji i zgodność platformy.

- **Wersja klasyczna:** Oparta na .NET Framework i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w pełnych wersjach systemu Windows, takich jak Server Core i Windows Desktop.
- **Wersja podstawowa:** Oparta na oprogramowaniu .NET Core i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w zmniejszonych wersjach systemu Windows, takich jak nano Server i Windows IoT.

### <a name="learn-more-about-using-powershell-editions"></a>Dowiedz się więcej o korzystaniu z wersji programu PowerShell

- [Określanie uruchomionej wersji programu PowerShell przy użyciu $PSVersionTable](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Filtrowanie wyników Get-module według CompatiblePSEditions przy użyciu parametru PSEdition](/powershell/module/microsoft.powershell.core/get-module)
- [Zapobiegaj wykonywaniu skryptów, chyba że jest uruchomiona w zgodnej wersji programu PowerShell](/powershell/gallery/concepts/script-psedition-support)
- [Deklarowanie zgodności modułu z określonymi wersjami programu PowerShell](/powershell/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a>Pamięć podręczna analizy modułów

Począwszy od programu WMF 5,1, program PowerShell zapewnia kontrolę nad plikiem używanym do buforowania danych dotyczących modułu, takich jak eksportowane polecenia.

Domyślnie ta pamięć podręczna jest przechowywana w pliku `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`. Pamięć podręczna jest zwykle odczytywana podczas uruchamiania podczas wyszukiwania polecenia i jest zapisywana w wątku w tle, gdy moduł zostanie zaimportowany.

Aby zmienić domyślną lokalizację pamięci podręcznej, należy ustawić `$env:PSModuleAnalysisCachePath` zmienną środowiskową przed uruchomieniem programu PowerShell. Zmiany w tej zmiennej środowiskowej będą miały wpływ tylko na procesy podrzędne. Wartość powinna mieć nazwę pełną ścieżkę (łącznie z nazwą pliku), która ma uprawnienia do tworzenia i zapisywania plików przez program PowerShell. Aby wyłączyć pamięć podręczną plików, ustaw tę wartość na nieprawidłową lokalizację, na przykład:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Spowoduje to ustawienie ścieżki do nieprawidłowego urządzenia. Jeśli program PowerShell nie może zapisać do ścieżki, żaden błąd nie jest zwracany, ale raportowanie błędów można zobaczyć przy użyciu śledzenia:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Podczas zapisywania pamięci podręcznej program PowerShell sprawdzi istnienie modułów, które już nie istnieją, aby uniknąć niepotrzebnej dużej pamięci podręcznej. Czasami te testy nie są pożądane, w takim przypadku można je wyłączyć przez ustawienie:

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Ustawienie tej zmiennej środowiskowej zacznie obowiązywać natychmiast w bieżącym procesie.

## <a name="specifying-module-version"></a>Określanie wersji modułu

W programie WMF 5,1 `using module` działa tak samo jak w przypadku innych konstrukcji związanych z modułami w programie PowerShell.
Wcześniej nie było możliwości określenia konkretnej wersji modułu; Jeśli istnieją różne wersje, spowoduje to błąd.

W programie WMF 5,1:

- Można użyć [konstruktora ModuleSpecification (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).

  Ta tabela skrótów ma ten sam format co `Get-Module -FullyQualifiedName`.

  **Przykład:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- Jeśli istnieje wiele wersji modułu, program PowerShell używa tej **samej logiki rozpoznawania** jak `Import-Module` i nie zwróci błędu--takie samo zachowanie jak `Import-Module` i `Import-DscResource`.

## <a name="improvements-to-pester"></a>Ulepszenia dla szkodnika

W programie WMF 5,1 wersja szkodnika, która jest dostarczana z programem PowerShell, została zaktualizowana z 3.3.5 na 3.4.0.
Ta aktualizacja umożliwia lepsze zachowanie szkodnika na serwerze nano Server.

Zmiany w szkodnikach można przejrzeć, sprawdzając [Dziennik zmian](https://github.com/pester/Pester/blob/master/CHANGELOG.md) w repozytorium GitHub.
