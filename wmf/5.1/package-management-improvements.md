---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
contributor: jianyunt, quoctruong
title: "Ulepszenia zarządzania pakietami w WMF 5.1"
ms.openlocfilehash: b55a1742530b7cd48d60d79b7d4866ebee80a3b6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="improvements-to-package-management-in-wmf-51"></a>Ulepszenia zarządzania pakietami w WMF 5.1#

## <a name="improvements-in-packagemanagement"></a>Ulepszenia w PackageManagement ##
Poprawki w wersji 5.1 WMF są następujące: 

### <a name="version-alias"></a>Alias wersji

**Scenariusz**: Jeśli masz wersji 1.0 lub 2.0 pakietu P1, zainstalowanych w systemie i chcesz odinstalować w wersji 1.0, należy uruchomić `Uninstall-Package -Name P1 -Version 1.0` i w wersji 1.0 ma zostać odinstalowany po uruchomieniu polecenia cmdlet. Jednak odinstalować pobiera wynik jest tym w wersji 2.0.  
    
Dzieje się tak dlatego `-Version` parametru jest aliasem `-MinimumVersion` parametru. Gdy PackageManagement szuka pakietu kwalifikowaną o minimalnej wersji 1.0, zwraca najnowszej wersji. To zachowanie jest oczekiwane w warunkach normalnych, ponieważ wyszukiwanie najnowszej wersji zwykle jest pożądany wynik. Jednak nie ma zastosowania do `Uninstall-Package` case.
    
**Rozwiązanie**: usunięte `-Version` aliasu w całości PackageManagement () OneGet) i PowerShellGet. 

### <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a>Wiele monity do inicjalizacji dostawcy NuGet

**Scenariusz**: po uruchomieniu `Find-Module` lub `Install-Module` lub innych poleceń cmdlet PackageManagement na komputerze po raz pierwszy, PackageManagement próbuje bootstrap dostawcy NuGet. Dzieje się tak, ponieważ dostawca PowerShellGet również używa dostawcy NuGet do pobrania moduły programu PowerShell. PackageManagement następnie monituje użytkownika o zgodę do zainstalowania dostawcy programu NuGet. Po wybraniu przez użytkownika opcji "tak" dla inicjowanie, zostanie zainstalowana najnowsza wersja dostawcy NuGet. 
    
Jednak w niektórych przypadkach, gdy masz starsza wersja programu NuGet dostawca jest zainstalowany na komputerze, starszą wersję programu NuGet czasami pobiera wcześniej załadowany do sesji programu PowerShell (która jest sytuacja wyścigu w PackageManagement). Jednak PowerShellGet wymaga nowszej wersji dostawcy NuGet do pracy, dlatego PowerShellGet zapyta PackageManagement, aby ponownie zainicjować dostawcy NuGet. Powoduje to wiele monity do inicjalizacji dostawcy NuGet.

**Rozwiązanie**: W WMF5.1, PackageManagement ładuje najnowszą wersję dostawcy NuGet, aby wiele monity do inicjalizacji dostawcy NuGet.

Użytkownik może również obejść ten problem przez ręczne usunięcie starą wersję dostawcy NuGet (NuGet Anycpu.exe), jeśli istnieje z $env: ProgramFiles\PackageManagement\ProviderAssemblies $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies


### <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a>Obsługa PackageManagement na komputerach z tylko dostęp do intranetu

**Scenariusz**: W scenariuszu enterprise osób pracuje w środowisku w przypadku, gdy jest nie dostępu do Internetu, ale Intranet tylko. PackageManagement nie obsługuje tego przypadku w programie WMF 5.0.

**Scenariusz**: WMF 5.0, PackageManagement nie obsługuje komputerów, które mają tylko Intranet (ale nie Internet) dostępu.

**Rozwiązanie**: WMF 5.1 można wykonać następujące kroki, aby umożliwić komputerom intranecie Użyj PackageManagement:

1. Pobierz dostawcę NuGet za pomocą innego komputera z Internetem przy użyciu `Install-PackageProvider -Name NuGet`.

2. Znajdź dostawcę NuGet pod `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` lub `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.

3. Skopiuj pliki binarne do folderu lub udziału lokalizacji sieciowej komputera w intranecie dostępu, a następnie zainstaluj dostawcę NuGet z `Install-PackageProvider -Name NuGet -Source <Path to folder>`.


### <a name="event-logging-improvements"></a>Ulepszenia zdarzenia rejestrowania

Podczas instalowania pakietów to zmianę stanu komputera. W wersji 5.1 WMF, PackageManagement po teraz rejestruje zdarzenia w dzienniku zdarzeń systemu Windows `Install-Package`, `Uninstall-Package`, i `Save-Package` działań. Dziennik zdarzeń są takie same jak programu PowerShell, czyli `Microsoft-Windows-PowerShell, Operational`.

### <a name="support-for-basic-authentication"></a>Obsługę uwierzytelniania podstawowego

W wersji 5.1 WMF PackageManagement obsługuje znajdowanie i instalowanie pakietów z repozytorium, który wymaga uwierzytelniania podstawowego. Możesz podać swoje poświadczenia, aby `Find-Package` i `Install-Package` polecenia cmdlet. Przykład:

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
### <a name="support-for-using-packagemanagement-behind-a-proxy"></a>Obsługa użycia PackageManagement za serwerem proxy

W wersji 5.1 WMF, PackageManagement ma teraz nowe parametry serwera proxy `-ProxyCredential` i `-Proxy`. Przy użyciu tych parametrów, można określić adres URL serwera proxy i poświadczenia do poleceń cmdlet PackageManagement. Domyślnie są używane ustawienia serwera proxy systemu. Przykład:

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```

