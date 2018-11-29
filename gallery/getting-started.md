---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Rozpoczynanie pracy z galerii programu PowerShell
ms.openlocfilehash: c8beba3009e462ce52cdecd34fc0313d9234f289
ms.sourcegitcommit: 1082b13115c5c5be4b76574ba55307b3e567983f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2018
ms.locfileid: "52576893"
---
# <a name="getting-started-with-the-powershell-gallery"></a>Rozpoczęcie korzystania z galerii programu PowerShell

Galeria programu PowerShell jest zawierający skrypty, moduły i zasobów DSC można pobrać i wykorzystać repozytorium pakietów. Użyj polecenia cmdlet w [PowerShellGet](/powershell/module/powershellget) modułu, aby zainstalować pakiety z galerii programu PowerShell. Nie musisz zalogować się do pobierania elementów z galerii programu PowerShell.

> [!NOTE]
> Istnieje możliwość pobrania pakietu z galerii programu PowerShell bezpośrednio, ale nie jest to zalecane podejście.
> Aby uzyskać więcej informacji, zobacz [Pobieranie pakietu ręczne](/powershell/gallery/how-to/working-with-packages/manual-download).

## <a name="discovering-packages-from-the-powershell-gallery"></a>Wykrywanie pakietów z galerii programu PowerShell

Pakietów można znaleźć w galerii programu PowerShell, za pomocą **wyszukiwania** kontrolkę w galerii programu PowerShell [strony głównej](https://www.powershellgallery.com), lub za pośrednictwem modułów i skryptów z [strony pakietów ](https://www.powershellgallery.com/packages). Można również wyszukiwać pakiety z galerii programu PowerShell, uruchamiając [Find-Module][], [Find-DscResource], i [Find-Script][] poleceń cmdlet, w zależności od typu pakietu za pomocą `-Repository PSGallery`.

Można filtrować wyniki z galerii przy użyciu następujących parametrów:

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

## <a name="learning-about-packages-in-the-powershell-gallery"></a>Informacje o pakietach w galerii programu PowerShell

Po zidentyfikowaniu pakietu, który chcesz wziąć można dowiedzieć się więcej na ten temat. Można to zrobić, sprawdzając tego pakietu w określonej strony w galerii. Na tej stronie można będzie wyświetlić wszystkie metadane zostały przesłane z pakietu. Te metadane są dostarczane przez autora pakietu, a nie został zweryfikowany przez firmę Microsoft. Właściciel pakietu jest ściśle powiązane konto galerii, używane do opublikowania pakietu i jest bardziej wiarygodne niż pola Autor.

Jeśli użytkownik zauważy, pakietów, które uważasz, że nie został opublikowany w dobrej wierze, kliknij przycisk **Zgłoś nadużycie** na stronie tego pakietu.

Jeśli korzystasz z [Find-Module][] lub [Find-Script][], dane te można wyświetlić w zwracany obiekt PSGetModuleInfo. Na przykład uruchomiony `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`
Zwraca dane na temat modułu PSReadLine w galerii.

## <a name="downloading-packages-from-the-powershell-gallery"></a>Pobieranie pakietów z galerii programu PowerShell

Firma Microsoft zachęca następujący proces pobierania pakietów z galerii programu PowerShell:

### <a name="inspect"></a>Sprawdzanie

Aby pobrać pakiet z galerii w celu przeprowadzenia inspekcji, uruchom [Save-Module][] lub [Save-Script][] polecenia cmdlet, w zależności od typu pakietu. Dzięki temu można zapisać pakiet lokalnie bez instalowania i sprawdź zawartość pakietu. Pamiętaj, aby ręcznie usunąć zapisanego pakietu.

Niektóre z tych pakietów są tworzone przez firmę Microsoft, a inne są tworzone przez społeczność użytkowników programu PowerShell.
Firma Microsoft zaleca przejrzenie treści i kodu pakietów w tej galerii, przed instalacją.

Jeśli użytkownik zauważy, pakietów, które uważasz, że nie został opublikowany w dobrej wierze, kliknij przycisk **Zgłoś nadużycie** na stronie tego pakietu.

### <a name="install"></a>Instalowanie w klastrze zarządzania systemu

Aby zainstalować pakiet z galerii do użycia, uruchom [Install-Module][] lub [Install-Script][] polecenia cmdlet, w zależności od typu pakietu.

[Install-Module][] instaluje moduł do `$env:ProgramFiles\WindowsPowerShell\Modules` domyślnie.
Wymaga to konto administratora. Jeśli dodasz `-Scope CurrentUser` parametru moduł jest zainstalowany na `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .

[Install-Script][] instaluje skrypt, aby `$env:ProgramFiles\WindowsPowerShell\Scripts` domyślnie.
Wymaga to konto administratora. Jeśli dodasz `-Scope CurrentUser` parametru skryptu jest instalowana na `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .

Domyślnie [Install-Module][] i [Install-Script][] instaluje najnowszą wersję pakietu.
Aby zainstalować starszą wersję pakietu, Dodaj `-RequiredVersion` parametru.

### <a name="deploy"></a>Wdróż program

Aby wdrożyć pakiet z galerii programu PowerShell w usłudze Azure Automation, kliknij przycisk **usługi Azure Automation**, następnie kliknij przycisk **wdrażanie w usłudze Azure Automation** na stronie szczegółów pakietu. Nastąpi przekierowanie do portalu zarządzania systemu Azure, w którym możesz logować się przy użyciu poświadczeń konta platformy Azure. Należy pamiętać, że wdrażanie pakietów zależności służy do wdrażania wszystkich zależności do usługi Azure Automation. Można wyłączyć przez dodanie przycisku "Wdroż do usługi Azure Automation" **AzureAutomationNotSupported** tagu metadanych pakietu.

Aby dowiedzieć się więcej o usłudze Azure Automation, zobacz [usługi Azure Automation](/azure/automation) dokumentacji.

## <a name="updating-packages-from-the-powershell-gallery"></a>Trwa aktualizowanie pakietów z galerii programu PowerShell

Aby zaktualizować pakiety zainstalowany z galerii programu PowerShell, uruchom [Update-Module] [] lub polecenia cmdlet [] [skrypt aktualizacji]. Po uruchomieniu, bez żadnych dodatkowych parametrów, [] [Update-Module] próbuje zaktualizować wszystkie moduły zainstalowane, uruchamiając [Install-Module][]. Aby selektywnie aktualizowanie modułów, należy dodać `-Name` parametru. 

Podobnie, gdy są uruchomione bez żadnych dodatkowych parametrów, [[skrypt aktualizacji]] próbuje również zaktualizować wszystkie skrypty zainstalowane, uruchamiając [Install-Script][]. Aby selektywnie zaktualizować skrypty, Dodaj `-Name` parametru.

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a>Lista pakietów, zainstalowanych z galerii programu PowerShell

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
