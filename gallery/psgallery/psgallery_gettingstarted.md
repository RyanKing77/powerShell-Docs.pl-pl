---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: psgallery_gettingstarted
ms.openlocfilehash: 599b148e141ba4205a7c774581e737a5d54bfae1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="get-started-with-the-powershell-gallery"></a>Rozpoczynanie pracy z galerii programu PowerShell

## <a name="what-is-the-powershell-gallery"></a>Co to jest galerii programu PowerShell?

Galerii programu PowerShell jest centralnym repozytorium zawartości programu PowerShell.
W ramach tego można znaleźć przydatne moduły programu PowerShell, zawierająca poleceń programu PowerShell i zasoby konfiguracji żądanego stanu (DSC). Można również znaleźć skryptów programu PowerShell, niektóre z nich może zawierać przepływów pracy programu PowerShell, a które przedstawiają zestaw zadań i podaj sekwencji zadań.
Niektóre z tych elementów są utworzone przez firmę Microsoft, a inne są tworzone przez społeczność programu PowerShell.

## <a name="requirements"></a>Wymagania

Pobieranie elementów z galerii programu PowerShell w systemie wymaga [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) modułu. Moduł PowerShellGet można znaleźć w jednym z następujących czynności. Nie trzeba zalogować się do pobierania elementów z galerii programu PowerShell.

-   [Windows 10](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)
-   [Oprogramowanie Windows Management Framework 5.0](http://go.microsoft.com/fwlink/?LinkId=398175)
-   [Instalator MSI (dla środowiska PowerShell 3 i 4)](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

Wymaga również PowerShellGet [dostawcy NuGet](http://go.microsoft.com/fwlink/?LinkId=722208) do pracy z galerii programu PowerShell. Pojawi się monit do zainstalowania dostawcy NuGet automatycznie po pierwszym użyciu PowerShellGet, jeśli dostawca NuGet nie znajduje się w jednej z następujących lokalizacji:

- `$env:ProgramFiles\PackageManagement\ProviderAssemblies`
- `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies`

Można również uruchomić `Install-PackageProvider -Name NuGet -Force` można zautomatyzować, pobieranie i instalowanie dostawcy NuGet.


Jeśli masz wersji starszej niż 2.8.5.201 NuGet, należy wywołać następujących poleceń cmdlet programu PowerShell do zainstalowania i przełącznika do najnowszej wersji programu NuGet.

1.  `Install-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
2.  `Import-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
3.  Usuń starszą wersję programu NuGet z powyższej lokalizacji zainstalowane.

Aby uzyskać więcej informacji, zobacz <http://oneget.org/> .


Uwaga: Z powodu zmian w formatach pakowania, zaleca się aktualizacji do najnowszej wersji PowerShellGet i PackageManagement zainstalować elementy, które zostały niedawno zaktualizowane. PowerShellGet znajduje się w systemie Windows 10, możesz dowiedzieć się więcej o [tutaj](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409).
PowerShellGet wchodzi w skład programu Windows Management Framework (WMF) 5.0, który można pobrać [tutaj](http://go.microsoft.com/fwlink/?LinkId=398175).

## <a name="discovering-items-from-the-powershell-gallery"></a>Wykrywanie elementów z galerii programu PowerShell

Elementy można znaleźć w galerii programu PowerShell, za pomocą **wyszukiwania** formantu w tej witrynie sieci Web lub przechodząc na stronach moduły i skryptów. Możesz również znaleźć elementów z galerii programu PowerShell, uruchamiając [Znajdź moduł](https://go.microsoft.com/fwlink/?LinkId=821658) i [Znajdź skryptu](https://go.microsoft.com/fwlink/?LinkId=822322) poleceń cmdlet, w zależności od typu elementu z `-Repository PSGallery`.

Filtrowanie wyników z galerii można to zrobić przy użyciu następujących parametrów [Znajdź moduł](https://go.microsoft.com/fwlink/?LinkId=821658) i [Znajdź skryptu](https://go.microsoft.com/fwlink/?LinkId=822322)

- Nazwa
- AllVersions
- MinimumVersion
- RequiredVersion
- Tag
- Zawiera
- DscResource
- RoleCapability
- Polecenie
- Filtr

Jeśli interesuje Cię tylko wykrywania określonych zasobów DSC w galerii, możesz uruchomić [DscResource Znajdź](https://go.microsoft.com/fwlink/?LinkId=517196) polecenia cmdlet.
[Znajdź DscResource](https://go.microsoft.com/fwlink/?LinkId=517196) zwraca dane na zasoby DSC zawarte w galerii. Ponieważ DSC zasoby są zawsze dostarczane jako część modułu, nadal należy uruchomić [instalacji modułu](https://go.microsoft.com/fwlink/?LinkId=821663) do zainstalowania tych zasobów usługi Konfiguracja DSC.

## <a name="learning-about-items-in-the-powershell-gallery"></a>Informacje o elementów w galerii programu PowerShell

Po wyłaniają element, który chcesz, możesz uzyskać więcej informacji. Można to zrobić, sprawdzając określonej strony tego elementu w galerii. Na tej stronie można wyświetlić wszystkie metadane przekazany do elementu. Te metadane dla elementu jest zapewniana przez autora elementu i nie jest weryfikowany przez firmę Microsoft. Właściciel elementu silnie jest powiązany z galerii konto używane do publikowania elementu i jest bardziej wiarygodny niż pole autora.

Jeśli uważasz, że element nie jest opublikowana w dobrej wierze, kliknij przycisk **zgłaszania nadużyć** na stronie tego elementu.

Jeśli korzystasz z [Znajdź moduł](https://go.microsoft.com/fwlink/?LinkId=821658) lub [skryptu Znajdź](https://go.microsoft.com/fwlink/?LinkId=822322), można wyświetlić te dane w zwrócony obiekt PSGetModuleInfo.
Na przykład uruchomiona `Find-Module -Name PSReadLine -Repository PSGallery | Get-Member` zwraca dane dla modułu PSReadLine w galerii.

## <a name="downloading-items-from-the-powershell-gallery"></a>Pobieranie elementów z galerii programu PowerShell

Firma Microsoft zachęca następujący proces pobierania elementów z galerii programu PowerShell:

### <a name="inspect"></a>Sprawdź

Aby pobrać elementu galerii do inspekcji, uruchom [moduł zapisywania](https://go.microsoft.com/fwlink/?LinkId=821669) lub [Zapisz skrypt](https://go.microsoft.com/fwlink/?LinkId=822334) polecenia cmdlet, w zależności od typu elementu. Dzięki temu można zapisać elementu lokalnie bez instalowania go i sprawdzić zawartość elementu. Pamiętaj, aby ręcznie usunąć element zapisany.

Niektóre z tych elementów są utworzone przez firmę Microsoft, a inne są tworzone przez społeczność programu PowerShell. Firma Microsoft zaleca przejrzenie zawartość i kod elementów na tej galerii przed instalacją.

Jeśli uważasz, że element nie jest opublikowana w dobrej wierze, kliknij przycisk **zgłaszania nadużyć** na stronie tego elementu.

### <a name="install"></a>Instalowanie w klastrze zarządzania systemu

Aby zainstalować element galerii do użycia, uruchom [instalacji modułu](https://go.microsoft.com/fwlink/?LinkId=821663) lub [skrypt instalacji](https://go.microsoft.com/fwlink/?LinkId=822327) polecenia cmdlet, w zależności od typu elementu.

[Zainstaluj moduł](https://go.microsoft.com/fwlink/?LinkId=821663) instaluje moduł `$env:ProgramFiles\WindowsPowerShell\Modules` domyślnie. Wymaga to konto administratora. Jeśli dodasz `-Scope
CurrentUser` parametru moduł jest zainstalowany na `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .

[Skrypt instalacji](https://go.microsoft.com/fwlink/?LinkId=822327) instaluje skrypt `$env:ProgramFiles\WindowsPowerShell\Scripts` domyślnie. Wymaga to konto administratora. Jeśli dodasz `-Scope
CurrentUser` parametru skryptu jest instalowana na `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .

Domyślnie [instalacji modułu](https://go.microsoft.com/fwlink/?LinkId=821663) i [skrypt instalacji](https://go.microsoft.com/fwlink/?LinkId=822327) instaluje najnowszą wersję elementu. Aby zainstalować starszą wersję elementu, Dodaj `-RequiredVersion` parametru.

### <a name="deploy"></a>Wdróż program

Aby wdrożyć element z galerii programu PowerShell do automatyzacji Azure, kliknij przycisk **Wdróż automatyzacji Azure** na stronie szczegółów. Nastąpi przekierowanie do portalu zarządzania Azure, której użytkownik loguje się przy użyciu poświadczeń konta platformy Azure. Należy pamiętać, że wdrażanie elementy z zależnościami wdroży wszystkie zależności w automatyzacji Azure. Przycisk "Wdrażanie na automatyzacji Azure" można wyłączyć, dodając **AzureAutomationNotSupported** tag do metadanych elementu.

Aby dowiedzieć się więcej na temat usługi Automatyzacja Azure, zobacz [witryny sieci Web usługi Automatyzacja Azure](http://azure.microsoft.com/services/automation/).

## <a name="updating-items-from-the-powershell-gallery"></a>Aktualizowanie elementów z galerii programu PowerShell

Aby zaktualizować elementów z galerii programu PowerShell, uruchom [aktualizacji modułu](https://go.microsoft.com/fwlink/?LinkID=398576) lub [skryptu aktualizacji](http://go.microsoft.com/fwlink/?LinkId=619787) polecenia cmdlet. Podczas uruchamiania bez żadnych dodatkowych parametrów, [aktualizacji modułu](https://go.microsoft.com/fwlink/?LinkID=398576) próbuje zaktualizować zainstalowany, uruchamiając każdy moduł [instalacji modułu](https://go.microsoft.com/fwlink/?LinkId=821663).
Aby selektywnie zaktualizować modułów, Dodaj `-Name` parametru.

Podobnie, kiedy są uruchamiane bez żadnych dodatkowych parametrów [skryptu aktualizacji](http://go.microsoft.com/fwlink/?LinkId=619787) próbuje również zaktualizować każdy zainstalowany, uruchamiając skrypt [skrypt instalacji](https://go.microsoft.com/fwlink/?LinkId=822327).
Aby selektywnie zaktualizować skryptów, Dodaj `-Name` parametru.

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>Elementy listy, które zainstalowano z galerii programu PowerShell

Aby dowiedzieć się, które moduły mają zainstalowane z galerii programu PowerShell, uruchom [Get-InstalledModule](https://go.microsoft.com/fwlink/?LinkId=526863) polecenia cmdlet. To polecenie wyświetla listę wszystkich modułów w systemie, które zostały zainstalowane bezpośrednio z galerii programu PowerShell.

Podobnie, aby dowiedzieć się, które skrypty zainstalowano z galerii programu PowerShell, uruchom [Get-InstalledScript](https://go.microsoft.com/fwlink/?LinkId=619790) polecenia cmdlet. To polecenie wyświetla wszystkie skrypty w systemie zainstalowanych bezpośrednio z galerii programu PowerShell.