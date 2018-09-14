---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Rozpoczynanie pracy z galerii programu PowerShell
ms.openlocfilehash: 39998df1a2bf9363dd008dc96a802157c8d691d7
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523060"
---
# <a name="get-started-with-the-powershell-gallery"></a>Rozpoczynanie pracy z galerii programu PowerShell

Prawidłowego sposobu instalowanie elementów z galerii programu PowerShell jest użycie polecenia cmdlet w [PowerShellGet](/powershell/module/powershellget) modułu. Nie musisz zalogować się do pobierania elementów z galerii programu PowerShell.

> [!NOTE]
> Istnieje możliwość pobrania pakietu z galerii programu PowerShell bezpośrednio, ale nie jest to zalecane podejście. Aby uzyskać więcej informacji, zobacz [Pobieranie pakietu ręczne](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/how-to/working-with-items/manual-download.md).  


## <a name="discovering-items-from-the-powershell-gallery"></a>Odnajdywanie elementów z galerii programu PowerShell

Elementy w galerii programu PowerShell można znaleźć przy użyciu **wyszukiwania** kontroli w tej witrynie internetowej lub przeglądania stron modułów i skryptów. Możesz również znaleźć elementów z galerii programu PowerShell, uruchamiając [Find-Module][] i [Find-Script][] poleceń cmdlet, w zależności od typu elementu z `-Repository PSGallery`.

Filtrowanie wyników za pomocą galerii może odbywać się przy użyciu następujących parametrów:

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

Jeśli interesuje Cię tylko odnajdywanie określone zasoby DSC w galerii, możesz uruchomić [Find-DscResource] polecenia cmdlet. Znajdź-DscResource zwraca dane dla zasobów DSC znajdujących się w galerii.
Ponieważ zasoby DSC zawsze są dostarczane jako część modułu, nadal musisz uruchomić [Install-Module][] do zainstalowania tych zasobów DSC.

## <a name="learning-about-items-in-the-powershell-gallery"></a>Zapoznawanie się elementy w galerii programu PowerShell

Po zidentyfikowaniu element, który chcesz wziąć można dowiedzieć się więcej na ten temat. Można to zrobić, sprawdzając określonej strony tego elementu w galerii. Na tej stronie można będzie wyświetlić wszystkie metadane zostały przesłane z elementu. Te metadane dla elementu są dostarczane przez autora elementu, a nie został zweryfikowany przez firmę Microsoft. Właścicielem przedmiotu zdecydowanie jest powiązany z galerii konto używane do publikowania elementu i jest bardziej wiarygodne niż pola Autor.

Jeśli uważasz, że element nie został opublikowany w dobrej wierze, kliknij przycisk **Zgłoś nadużycie** na stronie tego elementu.

Jeśli korzystasz z [Find-Module][] lub [Find-Script][], dane te można wyświetlić w zwracany obiekt PSGetModuleInfo. Na przykład uruchomiony `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`
Zwraca dane na temat modułu PSReadLine w galerii.

## <a name="downloading-items-from-the-powershell-gallery"></a>Pobieranie elementów z galerii programu PowerShell

Firma Microsoft zachęca następującego procesu podczas pobierania elementów z galerii programu PowerShell:

### <a name="inspect"></a>Sprawdzanie

Aby pobrać element z galerii w celu przeprowadzenia inspekcji, uruchom [Save-Module][] lub [Save-Script][] polecenia cmdlet, w zależności od typu elementu. Dzięki temu można zapisać elementu lokalnie bez instalowania i sprawdź zawartość elementu. Pamiętaj, aby ręcznie usunąć zapisanego elementu.

Niektóre z tych elementów są tworzone przez firmę Microsoft, a inne są tworzone przez społeczność użytkowników programu PowerShell.
Firma Microsoft zaleca przejrzenie treści i kodu elementy w tej galerii, przed instalacją.

Jeśli uważasz, że element nie został opublikowany w dobrej wierze, kliknij przycisk **Zgłoś nadużycie** na stronie tego elementu.

### <a name="install"></a>Instalowanie w klastrze zarządzania systemu

Aby zainstalować elementu galerii do użycia, uruchom [Install-Module][] lub [Install-Script][] polecenia cmdlet, w zależności od typu elementu.

[Install-Module][] instaluje moduł do `$env:ProgramFiles\WindowsPowerShell\Modules` domyślnie.
Wymaga to konto administratora. Jeśli dodasz `-Scope CurrentUser` parametru moduł jest zainstalowany na `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .

[Install-Script][] instaluje skrypt, aby `$env:ProgramFiles\WindowsPowerShell\Scripts` domyślnie.
Wymaga to konto administratora. Jeśli dodasz `-Scope CurrentUser` parametru skryptu jest instalowana na `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .

Domyślnie [Install-Module][] i [Install-Script][] instaluje najnowszą wersję elementu.
Aby zainstalować starszą wersję elementu, należy dodać `-RequiredVersion` parametru.

### <a name="deploy"></a>Wdróż program

Aby wdrożyć element z galerii programu PowerShell w usłudze Azure Automation, kliknij **wdrażanie w usłudze Azure Automation** na stronie szczegółów elementu. Nastąpi przekierowanie do portalu zarządzania systemu Azure, w którym możesz logować się przy użyciu poświadczeń konta platformy Azure. Należy pamiętać, że wdrażanie elementy z zależnościami wdroży wszystkie zależności do usługi Azure Automation. Można wyłączyć przez dodanie przycisku "Wdroż do usługi Azure Automation" **AzureAutomationNotSupported** tagu metadanych elementu.

Aby dowiedzieć się więcej o usłudze Azure Automation, zobacz [usługi Azure Automation](/azure/automation) dokumentacji.

## <a name="updating-items-from-the-powershell-gallery"></a>Aktualizowanie elementów z galerii programu PowerShell

Aby zaktualizować elementów zainstalowany z galerii programu PowerShell, uruchom [Update-Module] [] lub polecenia cmdlet [] [skrypt aktualizacji]. Po uruchomieniu bez żadnych dodatkowych parametrów [] [Update-Module] próby uaktualnienia każdy moduł zainstalowane, uruchamiając [Install-Module][]. Aby selektywnie aktualizowanie modułów, należy dodać `-Name` parametru.

Podobnie, gdy są uruchomione bez żadnych dodatkowych parametrów, [] [skrypt aktualizacji] również próby uaktualnienia każdego skryptu zainstalowane, uruchamiając [Install-Script][]. Aby selektywnie zaktualizować skrypty, Dodaj `-Name` parametru.

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>Elementy listy, które zostały zainstalowane z galerii programu PowerShell

Aby dowiedzieć się, które moduły mają zainstalowany z galerii programu PowerShell, uruchom [Get-InstalledModule][] polecenia cmdlet. To polecenie wyświetla wszystkie moduły, które znajdują się w systemie i zainstalowanych bezpośrednio z galerii programu PowerShell.

Podobnie, aby dowiedzieć się, skrypty, które mają zainstalowany z galerii programu PowerShell, uruchom [Get-InstalledScript][] polecenia cmdlet. To polecenie wyświetla wszystkie skrypty, które znajdują się w systemie i zainstalowanych bezpośrednio z galerii programu PowerShell.

[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script