---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: jianyunt, quoctruong
title: Ulepszenia zarządzania pakietami w programie WMF 5.1
ms.openlocfilehash: 30ef59ed9dc0d56636d85cc6e53523a9a73963a4
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794284"
---
# <a name="improvements-to-package-management-in-wmf-51"></a>Ulepszenia zarządzania pakietami w programie WMF 5.1

## <a name="improvements-in-packagemanagement"></a>Ulepszenia funkcji PackageManagement

Poprawki wprowadzone w program WMF 5.1 są następujące:

### <a name="version-alias"></a>Alias wersji

**Scenariusz**: Jeśli masz wersję 1.0 i 2.0 pakiet, P1, zainstalowanych w systemie, a chcesz odinstalować w wersji 1.0, należy uruchomić następujące polecenie `Uninstall-Package -Name P1 -Version 1.0` i oczekują w wersji 1.0 do odinstalowania po uruchomieniu polecenia cmdlet. Jednak wynik jest w tej wersji 2.0 zostaje odinstalowana.

Dzieje się tak dlatego `-Version` parametru jest aliasem `-MinimumVersion` parametru. Funkcja PackageManagement szuka kwalifikowaną pakietu co najmniej w wersji 1.0, funkcja zwraca najnowszej wersji. To zachowanie jest oczekiwane w warunkach normalnych, ponieważ uważa się, że najnowsza wersja jest zazwyczaj oczekiwany rezultat. Jednak nie ma zastosowania do `Uninstall-Package` przypadek.

**Rozwiązanie**: usunięte `-Version` aliasu w całości PackageManagement (zwane) OneGet) i modułu PowerShellGet.

### <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a>Wiele ustawień wyświetla monit dotyczący uruchamianie dostawcy NuGet

**Scenariusz**: Po uruchomieniu `Find-Module` lub `Install-Module` lub inne polecenia cmdlet funkcji PackageManagement na komputerze po raz pierwszy, funkcja PackageManagement próbuje bootstrap dostawcy NuGet. Dzieje się tak, ponieważ dostawca PowerShellGet również używa dostawcy NuGet można pobrać modułów programu PowerShell. Funkcja PackageManagement następnie monituje użytkownika o zgodę zainstalować dostawcę NuGet. Po użytkownik wybierze "yes" do uruchomienia, zostanie zainstalowana najnowsza wersja dostawcy NuGet.

Jednak w niektórych przypadkach, w przypadku starszej wersji dostawcy NuGet zainstalowany na tym komputerze starszej wersji pakietu NuGet czasami pobiera ładowane najpierw do sesji programu PowerShell (dotyczy to sytuacji wyścigu w funkcji PackageManagement). Moduł PowerShellGet wymaga jednak nowszą wersję dostawcy NuGet do pracy, dlatego moduł PowerShellGet prosi PackageManagement ponownie uruchomienie dostawcy NuGet. Powoduje to wiele monity dotyczące uruchamianie dostawcy NuGet.

**Rozwiązanie**: W WMF5.1 funkcja PackageManagement ładuje najnowszą wersję dostawcy NuGet, aby uniknąć wielu monity dotyczące uruchamianie dostawcy NuGet.

Użytkownik może również obejść ten problem, ręcznie usuwając starą wersję dostawcy NuGet (NuGet Anycpu.exe), jeśli istnieje z $env: ProgramFiles\PackageManagement\ProviderAssemblies $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies


### <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a>Obsługa funkcji PackageManagement na komputerach z systemem tylko dostęp do intranetu

**Scenariusz**: W scenariuszu enterprise osób pracuje w środowisku w przypadku, gdy jest nie dostępu do Internetu, ale intranetu tylko. Funkcja PackageManagement nie obsługują tego przypadku w programie WMF 5.0.

**Scenariusz**: W programie WMF 5.0, funkcja PackageManagement nie obsługują komputerów, które mają tylko Intranet (ale nie Internetu) dostępu.

**Rozwiązanie**: Programu WMF 5.1 należy wykonać następujące kroki, aby umożliwić komputerów w intranecie, użyj funkcji PackageManagement:

1. Pobieranie dostawcy NuGet za pomocą innego komputera, który ma połączenie z Internetem przy użyciu `Install-PackageProvider -Name NuGet`.

2. Znajdź dostawcę NuGet w obszarze `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` lub `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.

3. Skopiuj pliki binarne w folderze lub w sieci lokalizacji udziału, komputer w intranecie dostępu, a następnie zainstaluj dostawcę NuGet za pomocą `Install-PackageProvider -Name NuGet -Source <Path to folder>`.


### <a name="event-logging-improvements"></a>Ulepszenia rejestrowania zdarzenia

Podczas instalowania pakietów zmieniasz stan komputera. W program WMF 5.1 PackageManagement teraz rejestruje zdarzenia w dzienniku zdarzeń Windows `Install-Package`, `Uninstall-Package`, i `Save-Package` działań. Dziennik zdarzeń jest taka sama, jak w przypadku programu PowerShell, czyli `Microsoft-Windows-PowerShell, Operational`.

### <a name="support-for-basic-authentication"></a>Obsługa uwierzytelniania podstawowego

Program WMF 5.1 PackageManagement obsługuje wyszukiwanie i instalowanie pakietów z repozytorium, który wymaga uwierzytelniania podstawowego. Możesz podać swoje poświadczenia, aby `Find-Package` i `Install-Package` polecenia cmdlet. Przykład:

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```

### <a name="support-for-using-packagemanagement-behind-a-proxy"></a>Obsługa za pomocą modułu PackageManagement za serwerem proxy

W program WMF 5.1 PackageManagement przyjmuje teraz nowe parametry serwera proxy `-ProxyCredential` i `-Proxy`. Korzystając z tych parametrów, można określić adres URL serwera proxy i poświadczeń do polecenia cmdlet funkcji PackageManagement. Domyślnie są używane ustawienia serwera proxy systemu. Przykład:

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```
