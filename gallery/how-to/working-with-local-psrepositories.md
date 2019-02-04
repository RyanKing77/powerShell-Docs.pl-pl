---
ms.date: 11/06/2018
contributor: JKeithB
keywords: Galeria programu powershell, polecenie cmdlet, galerii programu PowerShell, psget
title: Praca z lokalnym PSRepositories
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688392"
---
# <a name="working-with-local-powershellget-repositories"></a>Praca z lokalne repozytoria modułu PowerShellGet

Repozytoriów Obsługa modułu PowerShellGet innych niż Galeria programu PowerShell.
Te polecenia cmdlet Włącz następujące scenariusze:

- Obsługuje zestaw zaufanych, wstępnie zatwierdzonych modułów programu PowerShell do użycia w danym środowisku
- Testowanie potoku ciągłej integracji/ciągłego wdrażania, który kompiluje modułów programu PowerShell lub skryptów
- Dostarczanie modułów i skryptów programu PowerShell do systemów, które nie mogą uzyskać dostęp do Internetu

W tym artykule opisano sposób konfigurowania lokalnego repozytorium programu PowerShell. Artykuł obejmuje również [OfflinePowerShellGetDeploy][] modułu, które są dostępne z galerii programu PowerShell. Ten moduł zawiera polecenia cmdlet, aby zainstalować najnowszą wersję modułu PowerShellGet w lokalnym repozytorium.

## <a name="local-repository-types"></a>Typy repozytorium lokalnego

Istnieją dwa sposoby tworzenia lokalnego PSRepository: NuGet serwer lub udział plików. Każdy typ ma zalety i wady:

NuGet Server

| Zalety| Wady |
| --- | --- |
| Ścisłe naśladowanie funkcji galerii PowerShellGallery | Wymaga aplikacji wielowarstwowej, operacje, planowania i pomoc techniczna |
| NuGet jest zintegrowany z programem Visual Studio i innych narzędzi | Model uwierzytelniania i konieczne zarządzanie kontami NuGet |
| NuGet obsługuje metadanych w `.Nupkg` pakietów | Publikowanie wymaga klucza interfejsu API zarządzania i konserwacji |
| Umożliwia wyszukiwanie pakietów administracyjnych, itp. | |

Udział plików

| Zalety| Wady |
| --- | --- |
| Łatwe konfigurowanie, tworzenie kopii zapasowej i konserwacji | Metadane używane przez moduł PowerShellGet jest niedostępna |
| Model zabezpieczeń proste — uprawnienia użytkownika do udziału | Brak interfejsu użytkownika po przekroczeniu podstawowy udział pliku |
| Bez ograniczeń, takich jak zastąpienie istniejących elementów | Ograniczonych zabezpieczeń i kto co aktualizacji nie rejestrowania |

Moduł PowerShellGet współpracuje z typu i obsługuje lokalizowanie wersje i zależności instalacji.
Jednak niektóre funkcje, które działają w przypadku galerii programu PowerShell nie są dostępne dla podstawowej serwerów NuGet ani udziałów plików.

- Wszystko, co jest pakietem - rozróżnienia skryptów, moduły, zasoby DSC lub możliwości roli.
- Serwery udziału plików nie może wyświetlić metadane pakietów, łącznie z tagami.

## <a name="creating-a-local-repository"></a>Tworzenia repozytorium lokalnego

Następujący artykuł zawiera kroki dotyczące konfigurowania serwera NuGet.

- [NuGet.Server][]

Postępuj zgodnie z instrukcjami aż do momentu dodania pakietów. Kroki [publikowania pakietu](#publishing-to-a-local-repository) zostały omówione w dalszej części tego artykułu.

W przypadku repozytorium opartych na udziałach plików upewnij się, czy użytkownicy mają uprawnienia dostępu do udziału plików.

## <a name="registering-a-local-repository"></a>Rejestrowanie repozytorium lokalnego

Przed użyciem repozytorium, musi być zarejestrowana, za pomocą `Register-PSRepository` polecenia.
W poniższych przykładach **InstallationPolicy** ustawiono *zaufanego*, przy założeniu, że masz zaufanie własnego repozytorium.

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

Zwróć uwagę na różnicę między jak obsługiwać dwa polecenia **ScriptSourceLocation**. W przypadku repozytoriów z opartych na udziałach plików **SourceLocation** i **ScriptSourceLocation** muszą być zgodne. Repozytorium opartego na sieci web, muszą być różne, dlatego w tym przykładzie końcowe "/" zostanie dodany do **SourceLocation**.

Jeśli chcesz, aby nowo utworzony PSRepository jako repozytorium domyślne, należy wyrejestrować wszystkie inne PSRepositories. Przykład:

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> Nazwa repozytorium "Galerii programu PowerShell" jest zarezerwowana do użytku w galerii programu PowerShell. Można wyrejestrować galerii programu PowerShell, ale nie można ponownie użyć nazwy galerii programu PowerShell, która znajduje się w przypadku dowolnego innego repozytorium.

Jeśli trzeba przywrócić galerii programu PowerShell, uruchom następujące polecenie:

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a>Publikowanie lokalnego repozytorium

Po zarejestrowaniu PSRepository lokalnym, możesz opublikować swoje lokalne PSRepository. Istnieją dwa główne scenariusze publikowania: publikowanie własny moduł i publikowania modułu z galerii programu PowerShell.

### <a name="publishing-a-module-you-authored"></a>Publikowanie modułu Twojego autorstwa

Użyj `Publish-Module` i `Publish-Script` do publikowania modułu swoje lokalne PSRepository taki sam sposób jak w przypadku galerii programu PowerShell.

- Określ lokalizację, w kodzie
- Podaj klucz interfejsu API
- Określ nazwę repozytorium. Na przykład `-PSRepository LocalPSRepo`

> [!NOTE]
> Należy utworzyć konto w serwer NuGet, a następnie zaloguj się wygenerować i zapisać klucz interfejsu API.
> Dla udziału plików należy użyć wartości NuGetApiKey dowolny ciąg nie jest pusty.

Przykłady:

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Aby zapewnić bezpieczeństwo, klucze interfejsu API nie może być zakodowane w skryptach. Należy używać systemu bezpieczne zarządzanie kluczami.

### <a name="publishing-a-module-from-the-psgallery"></a>Publikowanie modułu z galerii programu PowerShell

Aby opublikować modułu z galerii programu PowerShell do swojej lokalnej PSRepository, można użyć polecenia cmdlet "Zapisz pakiet".

- Określ nazwę pakietu
- Określ "NuGet" jako dostawcy
- Określ lokalizację galerii programu PowerShell jako (źródła https://www.powershellgallery.com/api/v2)
- Określ ścieżkę do repozytorium lokalnego

Przykład:

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

Jeśli Twoje lokalne PSRepository jest oparte na sieci web, wymaga dodatkowego kroku, który używa nuget.exe do publikowania.

Zajrzyj do dokumentacji przy użyciu [nuget.exe][].

## <a name="installing-powershellget-on-a-disconnected-system"></a>Instalowanie modułu PowerShellGet w systemie bez połączenia

Wdrażanie modułu PowerShellGet jest trudne w środowiskach, które wymagają systemów, które mogą być rozłączone z Internetu. Moduł PowerShellGet ma ładowania początkowego procesu, który instaluje najnowszą wersję z pierwszym, który jest używany. Moduł OfflinePowerShellGetDeploy w galerii programu PowerShell udostępnia polecenia cmdlet, który obsługuje ten proces ładowania.

Uruchomienie wdrożenie w trybie offline, należy:

- Pobierz i zainstaluj system OfflinePowerShellGetDeploy usługi połączonej z Internetem i z odrębnych systemów
- Pobieranie modułu PowerShellGet oraz jego zależności w systemie podłączonej do Internetu przy użyciu `Save-PowerShellGetForOffline` polecenia cmdlet
- Skopiuj modułu PowerShellGet oraz jego zależności z systemu podłączonej do Internetu do odłączonego systemu
- Użyj `Install-PowerShellGetOffline` systemie odłączonego umieszcza modułu PowerShellGet oraz jego zależności w odpowiednich folderów

Następujące polecenia, użyj `Save-PowerShellGetForOffline` do wszystkich składników należy umieścić w folderze `f:\OfflinePowerShellGet`

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

W tym momencie należy udostępnić zawartość `F:\OfflinePowerShellGet` dostępne dla odłączonych systemów. Uruchom `Install-PowerShellGetOffline` polecenia cmdlet do zainstalowania modułu PowerShellGet w systemie bez połączenia.

> [!NOTE]
> Należy pamiętać, że nie zostanie uruchomiony moduł PowerShellGet w sesji programu PowerShell, przed uruchomieniem tych poleceń. Po załadowaniu modułu PowerShellGet w sesji nie można zaktualizować składniki. W przypadku uruchomienia modułu PowerShellGet przez pomyłkę, zamknij i ponownie uruchom program PowerShell.

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

Po uruchomieniu tych poleceń, jesteś gotowy do opublikowania PowerShellGet do lokalnego repozytorium.

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Aby zapewnić bezpieczeństwo, klucze interfejsu API nie może być zakodowane w skryptach. Należy używać systemu bezpieczne zarządzanie kluczami.

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
