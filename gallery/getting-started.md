---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: Rozpoczynanie pracy z galerii programu PowerShell
ms.openlocfilehash: 83974698152e75efac66ea725a9c220486676d6f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="get-started-with-the-powershell-gallery"></a>Rozpoczynanie pracy z galerii programu PowerShell

Pobieranie elementów z galerii programu PowerShell w systemie wymaga [PowerShellGet](/powershell/module/powershellget) modułu. Moduł PowerShellGet można znaleźć w jednym z następujących czynności. Nie trzeba zalogować się do pobierania elementów z galerii programu PowerShell.

## <a name="discovering-items-from-the-powershell-gallery"></a>Wykrywanie elementów z galerii programu PowerShell

Elementy można znaleźć w galerii programu PowerShell, za pomocą **wyszukiwania** formantu w tej witrynie sieci Web lub przechodząc na stronach moduły i skryptów. Możesz również znaleźć elementów z galerii programu PowerShell, uruchamiając [Znajdź moduł][] i [skryptu Znajdź][] poleceń cmdlet, w zależności od typu elementu z `-Repository PSGallery`.

Filtrowanie wyników z galerii może odbywać się przy użyciu następujących parametrów:

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

Jeśli interesuje Cię tylko wykrywania określonych zasobów DSC w galerii, możesz uruchomić [DscResource Znajdź] polecenia cmdlet. Znajdź DscResource zwraca dane na zasoby DSC zawarte w galerii.
Ponieważ DSC zasoby są zawsze dostarczane jako część modułu, nadal należy uruchomić [instalacji modułu][] do zainstalowania tych zasobów usługi Konfiguracja DSC.

## <a name="learning-about-items-in-the-powershell-gallery"></a>Informacje o elementów w galerii programu PowerShell

Po wyłaniają element, który chcesz, możesz uzyskać więcej informacji. Można to zrobić, sprawdzając określonej strony tego elementu w galerii. Na tej stronie można wyświetlić wszystkie metadane przekazany do elementu. Te metadane dla elementu jest zapewniana przez autora elementu i nie jest weryfikowany przez firmę Microsoft. Właściciel elementu silnie jest powiązany z galerii konto używane do publikowania elementu i jest bardziej wiarygodny niż pole autora.

Jeśli uważasz, że element nie jest opublikowana w dobrej wierze, kliknij przycisk **zgłaszania nadużyć** na stronie tego elementu.

Jeśli korzystasz z [Znajdź moduł][] lub [skryptu Znajdź][], można wyświetlić te dane w zwrócony obiekt PSGetModuleInfo. Na przykład uruchomiona `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` zwraca dane dla modułu PSReadLine w galerii.

## <a name="downloading-items-from-the-powershell-gallery"></a>Pobieranie elementów z galerii programu PowerShell

Firma Microsoft zachęca następujący proces pobierania elementów z galerii programu PowerShell:

### <a name="inspect"></a>Sprawdź

Aby pobrać elementu galerii do inspekcji, uruchom [moduł zapisywania][] lub [Zapisz skrypt][] polecenia cmdlet, w zależności od typu elementu. Dzięki temu można zapisać elementu lokalnie bez instalowania go i sprawdzić zawartość elementu. Pamiętaj, aby ręcznie usunąć element zapisany.

Niektóre z tych elementów są utworzone przez firmę Microsoft, a inne są tworzone przez społeczność programu PowerShell.
Firma Microsoft zaleca przejrzenie zawartość i kod elementów na tej galerii przed instalacją.

Jeśli uważasz, że element nie jest opublikowana w dobrej wierze, kliknij przycisk **zgłaszania nadużyć** na stronie tego elementu.

### <a name="install"></a>Instalowanie w klastrze zarządzania systemu

Aby zainstalować element galerii do użycia, uruchom [instalacji modułu][] lub [skrypt instalacji][] polecenia cmdlet, w zależności od typu elementu.

[instalacji modułu][] instaluje moduł `$env:ProgramFiles\WindowsPowerShell\Modules` domyślnie.
Wymaga to konto administratora. Jeśli dodasz `-Scope CurrentUser` parametru moduł jest zainstalowany na `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .

[skrypt instalacji][] instaluje skrypt `$env:ProgramFiles\WindowsPowerShell\Scripts` domyślnie.
Wymaga to konto administratora. Jeśli dodasz `-Scope CurrentUser` parametru skryptu jest instalowana na `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .

Domyślnie [instalacji modułu][] i [skrypt instalacji][] instaluje najnowszą wersję elementu.
Aby zainstalować starszą wersję elementu, Dodaj `-RequiredVersion` parametru.

### <a name="deploy"></a>Wdróż program

Aby wdrożyć element z galerii programu PowerShell do automatyzacji Azure, kliknij przycisk **Wdróż automatyzacji Azure** na stronie szczegółów. Nastąpi przekierowanie do portalu zarządzania Azure, której użytkownik loguje się przy użyciu poświadczeń konta platformy Azure. Należy pamiętać, że wdrażanie elementy z zależnościami wdroży wszystkie zależności w automatyzacji Azure. Przycisk "Wdrażanie na automatyzacji Azure" można wyłączyć, dodając **AzureAutomationNotSupported** tag do metadanych elementu.

Aby dowiedzieć się więcej na temat usługi Automatyzacja Azure, zobacz [usługi Automatyzacja Azure](/azure/automation) dokumentacji.

## <a name="updating-items-from-the-powershell-gallery"></a>Aktualizowanie elementów z galerii programu PowerShell

Aby zaktualizować elementów z galerii programu PowerShell, uruchom [] [aktualizacji modułu] albo polecenia cmdlet [] [skrypt aktualizacji]. Uruchomienie bez żadnych dodatkowych parametrów [] [aktualizacji modułu] dokona próby uaktualnienia zainstalowany, uruchamiając każdy moduł [instalacji modułu][]. Aby selektywnie zaktualizować modułów, Dodaj `-Name` parametru.

Podobnie, uruchomienie bez żadnych dodatkowych parametrów [] [skrypt aktualizacji] próbuje również zaktualizować każdego skryptu zainstalowany, uruchamiając [skrypt instalacji][]. Aby selektywnie zaktualizować skryptów, Dodaj `-Name` parametru.

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>Elementy listy, które zainstalowano z galerii programu PowerShell

Aby dowiedzieć się, które moduły mają zainstalowane z galerii programu PowerShell, uruchom [Get-InstalledModule][] polecenia cmdlet. To polecenie wyświetla listę wszystkich modułów w systemie, które zostały zainstalowane bezpośrednio z galerii programu PowerShell.

Podobnie, aby dowiedzieć się, które skrypty zainstalowano z galerii programu PowerShell, uruchom [Get-InstalledScript][] polecenia cmdlet. To polecenie wyświetla wszystkie skrypty w systemie zainstalowanych bezpośrednio z galerii programu PowerShell.

[DscResource Znajdź]: /powershell/module/powershellget/Find-DscResource
[Znajdź moduł]: /powershell/module/powershellget/Find-Module
[skryptu Znajdź]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[instalacji modułu]: /powershell/module/powershellget/Install-Module
[skrypt instalacji]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[moduł zapisywania]: /powershell/module/powershellget/Save-Module
[Zapisz skrypt]: /powershell/module/powershellget/Save-Script