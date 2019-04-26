---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Galeria programu PowerShell — często zadawane pytania
ms.openlocfilehash: bcbb36a9ec60d88d1ef56fd270f0ae1862d5ca6b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084624"
---
# <a name="frequently-asked-questions"></a>Często zadawane pytania

## <a name="what-is-a-powershell-module"></a>Co to jest moduł programu PowerShell?

Moduł programu PowerShell to do ponownego użycia pakietu zawierającego niektóre funkcje programu PowerShell. Wszystko, co w programie PowerShell (funkcje, zmienne, zasoby DSC, itp.) można spakować w modułach. Zazwyczaj moduły są foldery zawierające określonych typów plików przechowywanych w określonej ścieżce. Istnieje kilka różnych typów modułów programu PowerShell tam.

## <a name="what-is-a-powershell-script"></a>Co to jest skrypt programu PowerShell?

Skrypt programu PowerShell jest serię poleceń, które są przechowywane w pliku .ps1, aby umożliwić udostępnianie i ponowne użycie. Przepływy pracy programu PowerShell są również skrypty programu PowerShell, które opisują zestaw zadań i podać sekwencji zadań. Aby uzyskać więcej informacji, odwiedź [rozpoczęcie korzystania z przepływu pracy programu PowerShell](https://technet.microsoft.com/library/jj134242.aspx).

## <a name="how-are-powershell-scripts-different-from-powershell-modules"></a>Czym różnią się skryptów programu PowerShell z modułów programu PowerShell?

Moduły są zazwyczaj większą do udostępniania, ale jest włączane, udostępnianie skrypt, aby ułatwić współtworzyć przepływami pracy a skryptami społeczności. Aby uzyskać więcej informacji można znaleźć na następujących blogach:

- [Nie zapisuj skryptów i modułów programu PowerShell Write](https://blogs.technet.microsoft.com/heyscriptingguy/2011/06/27/dont-write-scripts-write-powershell-modules/)
- [Opis modułów programu PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/07/10/understanding-powershell-modules/)

## <a name="how-can-i-publish-to-the-powershell-gallery"></a>Jak mogę opublikować w galerii programu PowerShell

Konto należy zarejestrować w galerii programu PowerShell, zanim będzie można opublikować pakietów do galerii. Jest to spowodowane publikowania pakietów wymaga NuGetApiKey, która jest dostarczana w chwili rejestracji. Aby się zarejestrować, użyj osobistego, konta służbowego do logowania się w galerii programu PowerShell. Po zalogowaniu się po raz pierwszy, proces rejestracji jednorazowy jest wymagany. Później Twoje NuGetApiKey jest dostępna na stronie profilu.

Po zarejestrowaniu się w galerii, użyj [Publish-Module][] lub [Publish-Script][] poleceń cmdlet do opublikowania pakietu do galerii.
Aby uzyskać więcej informacji na temat sposobu uruchamiania tych poleceń cmdlet można znaleźć na karcie publikowanie lub przeczytaj [Publish-Module][] i [Publish-Script][] dokumentacji.

**Nie musisz zarejestrować się lub zaloguj się do galerii, aby zainstalować lub zapisać pakietów.**

## <a name="i-received-failed-to-process-request-the-specified-api-key-is-invalid-or-does-not-have-permission-to-access-the-specified-package-the-remote-server-returned-an-error-403-forbidden-error-when-i-tried-to-publish-a-package-to-the-powershell-gallery-what-does-that-mean"></a>Został wyświetlony "nie można przetworzyć żądania. "Określony klucz interfejsu API jest nieprawidłowa lub nie ma uprawnień do dostępu do określonego pakietu.". Serwer zdalny zwrócił błąd: (403) zabroniony." Wystąpił błąd podczas próby opublikowania pakietu w galerii programu PowerShell. Co to oznacza?

Ten błąd może wystąpić z następujących powodów:

- **Określony klucz interfejsu API jest nieprawidłowa.**
     Upewnij się, że określono prawidłowego klucza interfejsu API z Twojego konta. Aby uzyskać klucz interfejsu API, wyświetlać stronę profilu.
- **Nazwa pakietu określona właścicielem nie jest użytkownik.**
     Jeśli potwierdzeniu, że klucz interfejsu API jest poprawna, a następnie może już istnieć pakiet o tej samej nazwie, który próbujesz użyć. Pakiet zostały nieznajdujące się na liście przez właściciela, w tym przypadku nie będzie wyświetlany w żadnych wyników wyszukiwania. Aby ustalić, czy pakiet o tej samej nazwie już istnieje, otwórz przeglądarkę i przejdź do strony szczegółów pakietu: `https://www.powershellgallery.com/packages/<packageName>`. Na przykład, przechodząc bezpośrednio do `https://www.powershellgallery.com/packages/pester` spowoduje przejście do strony szczegółów modułu usług Pester, czy jest ono nieznajdujące się na liście, czy nie. Jeśli pakiet o nazwie powodujące konflikt już istnieje i jest nieobecne na liście, możesz to zrobić:
    - Wybierz inną nazwę dla pakietu.
    - Skontaktuj się z właścicielami istniejącego pakietu.

## <a name="why-cant-i-sign-in-with-my-personal-account-but-i-could-sign-in-yesterday"></a>Dlaczego nie można zarejestrować się przy użyciu osobistego konta, ale można zarejestrować się w wczoraj?

Należy pamiętać, Twoje konto galerii nie obsługuje zmiany zmiany alias podstawowy adres e-mail. Aby uzyskać więcej informacji, zobacz [aliasy poczty E-mail firmy Microsoft](https://windows.microsoft.com/windows/outlook/add-alias-account).

## <a name="why-dont-i-see-all-the-gallery-packages-when-i-select-all-the-category-checkboxes-on-the-packages-tab"></a>Dlaczego nie widzisz wszystkie pakiety galerii, po wybraniu wszystkich pól kategorii wyboru na karcie pakiety?

Zaznaczając pole wyboru kategorii, są informacją "Czy chcesz zobaczyć wszystkie pakiety z tej kategorii." Wyświetlane są tylko pakiety z wybranych kategorii. Dlatego podobnie zaznaczenie wszystkich pól wyboru kategorii, możesz są z informacją "Czy chcesz zobaczyć wszystkie pakiety w dowolnej kategorii." Jednak niektóre pakiety w galerii nie należą do żadnej z kategorii na liście, dzięki czemu będą widoczne w wynikach. Aby wyświetlić wszystkie pakiety w galerii, usuń zaznaczenie wszystkich kategorii lub ponownie wybierz kartę pakietów.

## <a name="what-are-the-requirements-to-publish-a-module-to-the-powershell-gallery"></a>Jakie są wymagania, aby opublikować moduł galerii programu PowerShell?

Dowolny rodzaj modułu programu PowerShell (moduły skryptów, moduły binarne lub moduły manifestu) mogą być publikowane w galerii.
Aby opublikować modułu, PowerShellGet musi wiedzieć, kilka kwestii, o nim — wersji, opis, autora i jak jest licencjonowana.
Informacja ta jest do odczytu w ramach procesu publikowania z *manifestu modułu* pliku (psd1), lub wartość [Publish-Module][] polecenia cmdlet **LicenseUri** parametr.
Wszystkie moduły, opublikowane w galerii, musi mieć manifesty modułu.
Każdy moduł, który zawiera następujące informacje w swoim manifeście mogą być publikowane w galerii:

- Wersja
- Opis
- Autor
- Identyfikator URI do postanowień licencyjnych w module, albo w ramach **PrivateData** sekcji manifestu lub w **LicenseUri** parametru [Publish-Module][] polecenia cmdlet.

## <a name="how-do-i-create-a-correctly-formatted-module-manifest"></a>Jak utworzyć manifest poprawnie sformatowany modułu?

Najprostszym sposobem utworzenia manifestu modułu jest uruchomienie [New-ModuleManifest][] polecenia cmdlet. W programie PowerShell 5.0 lub nowszego, New-ModuleManifest generuje manifestu modułu poprawnie sformatowany za pomocą puste pola, aby uzyskać przydatne metadane, takie jak **ProjectUri**, **LicenseUri**, i **tagi**. Po prostu Wypełnij puste wartości lub użyć wygenerowanego manifestu, na przykład prawidłowe formatowanie.

Aby sprawdzić, czy wszystkie wymagane pola metadanych została prawidłowo wypełniona, użyj [Test-ModuleManifest][] polecenia cmdlet.

Aby zaktualizować pola pliku manifestu modułu, należy użyć [Update-ModuleManifest][] polecenia cmdlet.

## <a name="what-are-the-requirements-to-publish-a-script-to-the-gallery"></a>Jakie są wymagania, aby opublikować skrypt do galerii?

Dowolny skrypt programu PowerShell (skrypty lub przepływów pracy) mogą być publikowane w galerii.
Aby opublikować skryptu, PowerShellGet musi wiedzieć, kilka kwestii, o nim — wersji, opis, autora i jak jest licencjonowana.
Informacja ta jest do odczytu w ramach procesu publikowania z pliku skryptu *PSScriptInfo* sekcji, lub wartość [Publish-Script][] polecenia cmdlet **LicenseUri**parametru.
Wszystkie skrypty, opublikowane w galerii, musi mieć informacji o metadanych.
Dowolny skrypt, który zawiera następujące informacje w sekcji PSScriptInfo mogą być publikowane w galerii:

- Wersja
- Opis
- Autor
- Identyfikator URI postanowienia licencyjne dotyczące skryptu, albo w ramach **PSScriptInfo** sekcji skryptu lub w **LicenseUri** parametru [Publish-Script][] polecenia cmdlet.

## <a name="how-do-i-search"></a>Jak wyszukiwanie

Wpisz, czego szukasz w polu tekstowym. Na przykład jeśli chcesz znaleźć moduły, które są powiązane z usługi Azure SQL, po prostu wpisz "sql platformy azure". Naszego aparatu wyszukiwania będzie szukał tych słów kluczowych w wszystkie opublikowane pakiety, w tym tytuły i opisy i w ramach metadanych. Następnie na podstawie ważonej jakości wyniku, wyświetli najbliższego dopasowań. Możesz również wyszukiwać według określonego pola za pomocą pola: "wartość" składni w zapytaniu wyszukiwania dla następujących pól:

- Znaczniki
- Funkcje
- Polecenia cmdlet
- DscResources
- PowerShellVersion

Tak więc, na przykład podczas wyszukiwania PowerShellVersion: "2.0" tylko wyniki, które są zgodne z 2.0 PowerShellVersion (oparte na manifeście modułu skryptu) zostaną wyświetlone.

## <a name="how-do-i-create-a-correctly-formatted-script-file"></a>Jak utworzyć plik skryptu poprawnie sformatowany?

Najprostszym sposobem utworzenia pliku skryptu poprawnie sformatowana, jest uruchomienie [New-ScriptFileInfo][] polecenia cmdlet. W programie PowerShell 5.0, New-ScriptFileInfo generuje plik skryptu poprawnie sformatowany za pomocą pustych pól dla przydatne metadane, takie jak **ProjectUri**, **LicenseUri**, i **tagi** . Po prostu Wypełnij puste wartości lub użyć pliku skryptu wygenerowanego na przykład prawidłowe formatowanie.

Aby sprawdzić, czy wszystkie wymagane pola metadanych została prawidłowo wypełniona, użyj [Test-ScriptFileInfo][] polecenia cmdlet.

Aby zaktualizować pola metadanych skryptu, użyj [Update-ScriptFileInfo][] polecenia cmdlet.

## <a name="what-other-types-of-powershell-modules-exist"></a>Jakie inne rodzaje modułów programu PowerShell?

Moduł PowerShell termin odnosi się także do plików, które implementują funkcjonalność rzeczywiste. Pliki modułu skryptu (.psm1) zawierają kod programu PowerShell. Pliki binarne modułu (.dll) zawierają kod skompilowany.

W tym miejscu jest jednym ze sposobów myślenia o nim: folder, który hermetyzuje modułu jest folderem modułu. Folder modułu może zawierać manifest modułu (psd1), który opisuje zawartość tego folderu. Pliki, które rzeczywiście wykonują pracę są pliki modułu skryptu (.psm1) i pliki binarne modułu (.dll). Zasoby DSC znajdują się w określonym folderze podrzędnych i są implementowane jako pliki modułów skryptów lub pliki binarne modułu.

Wszystkie moduły w galerii zawierać manifesty modułu, a większość z tych modułów zawierają pliki modułów skryptów lub pliki binarne modułu. Ze względu na te różne znaczenie modułu terminu może być mylące. O ile nie zaznaczono inaczej, wszystkie przypadki użycia modułu programu word na tej stronie można znaleźć folderu modułu zawierającego te pliki.

## <a name="how-does-packagemanagement-relate-to-powershellget-high-level-answer"></a>Jaki jest związek między PackageManagement PowerShellGet? (Wysokiego poziomu odpowiedzi)

Funkcja PackageManagement jest wspólny interfejs do pracy z dowolnym Menedżera pakietów. Po pewnym czasie czy jesteś zajmujących modułów programu PowerShell, MSI, klejnoty języka Ruby, pakietów NuGet lub moduły języka Perl, można używać poleceń firmy PackageManagement (Znajdź pakiet i Install-Package), aby znaleźć i zainstalować je. Funkcja PackageManagement robi to przez dostawcę pakietu dla każdego Menedżera pakietów, które podłącza się do funkcji PackageManagement. Dostawców przyspieszające rzeczywista praca; Pobierz zawartość z repozytoriów i instalowanie zawartości lokalnie. Często dostawców pakietu po prostu otacza istniejące narzędzia Menedżera pakietów dla typu danego pakietu.

Moduł PowerShellGet to Menedżer pakietów dla pakietów programu PowerShell.
Brak dostawcy pakietu PSModule, który udostępnia funkcje PowerShellGet za pomocą modułu PackageManagement.
W związku z tym można uruchomić [Install-Module][] lub Install-Package-PSModule dostawcy, aby zainstalować moduł z galerii programu PowerShell.
Niektórych funkcji modułu PowerShellGet, w tym [Update-Module][] i [Publish-Module][], nie są dostępne za pomocą modułu PackageManagement poleceń.

Podsumowanie PowerShellGet jest wyłącznie koncentruje się na o środowisko zarządzania pakiet w wersji premium dla zawartości programu PowerShell. Funkcja PackageManagement koncentruje się na udostępnianie wszystkich pakietów środowiska zarządzania za pośrednictwem jednego ogólnego zestawu narzędzi. Odnalezienie unsatisfying tej odpowiedzi jest długi odpowiedzi w dolnej części tego dokumentu w **jak PackageManagement faktycznie jest związek z modułu PowerShellGet?** sekcji.

Aby uzyskać więcej informacji, odwiedź [strony projektu PackageManagement](https://oneget.org/).

## <a name="how-does-nuget-relate-to-powershellget"></a>Jaki jest związek między NuGet modułu PowerShellGet?

Galeria programu PowerShell to zmodyfikowana wersja [galerii pakietów NuGet](https://www.nuget.org/). Moduł PowerShellGet używa dostawcy NuGet do pracy z NuGet na podstawie repozytoriów, takich jak Galeria programu PowerShell.

Możesz używać modułu PowerShellGet, względem wszystkie prawidłowe NuGet repozytorium lub w udziale plików. Po prostu musisz dodać repozytorium, uruchamiając [Register-PSRepository][] polecenia cmdlet.

## <a name="does-that-mean-i-can-use-nugetexe-to-work-with-the-gallery"></a>Oznacza, że NuGet.exe można używać do pracy z galerii?

Tak.

## <a name="how-does-packagemanagement-actually-relate-to-powershellget-technical-details"></a>Jaki związek PackageManagement faktycznie między PowerShellGet? (Szczegóły techniczne)

Kulisy PowerShellGet intensywnie korzysta z infrastruktury PackageManagement.

W warstwie polecenia cmdlet programu PowerShell [Install-Module][] jest faktycznie alokowania elastycznego otokę Install-Package-PSModule dostawcy.

W warstwie dostawcy PackageManagement pakietu Dostawca pakietu PSModule rzeczywiście wywoła innych dostawców rozwiązań w pakiecie PackageManagement. Na przykład podczas pracy oparte na pakietach NuGet galerie (na przykład w galerii programu PowerShell), Dostawca pakietu PSModule używa dostawcy pakietu NuGet do pracy z repozytorium.

![Architektura modułu PowerShellGet](Images/powershellgetArchitecture.png)

Rysunek 1: Architektura modułu PowerShellGet

## <a name="what-is-required-to-run-powershellget"></a>Co to jest wymagane do uruchamiania modułu PowerShellGet?

Ogólnie rzecz biorąc zalecamy pobranie najnowszej wersji modułu PowerShellGet (należy zauważyć, że wymaga platformy .NET 4.5).

**PowerShellGet** moduł wymaga **programu PowerShell w wersji 3.0 lub nowszej**.

W związku z tym **PowerShellGet** wymaga jednej z następujących systemów operacyjnych:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 z dodatkiem SP1

**Moduł PowerShellGet** wymaga również programu .NET Framework 4.5 lub nowszej. Możesz zainstalować program .NET Framework 4.5 lub nowszy z [tutaj](https://msdn.microsoft.com/library/5a4x27ek.aspx).

## <a name="is-it-possible-to-reserve-names-for-packages-that-will-be-published-in-future"></a>Czy jest możliwe do zarezerwowania nazwy pakietów, które mają zostać opublikowane w przyszłości?

Nie jest możliwe nazwy wpuszczana w podłogę pakietów. Jeśli uważasz, że istniejący pakiet miało nazwę, która odpowiada pakietu więcej, spróbuj [skontaktować się z właścicielem pakietu](./how-to/working-with-packages/contacting-package-owners.md). Jeśli nie otrzymasz odpowiedzi w ciągu kilku tygodni, możesz się z pomocą techniczną i zespołu galerii programu PowerShell będzie wyglądał w nim.

## <a name="how-do-i-claim-ownership-for-packages"></a>Jak oświadczenia własności dla pakietów?

Zapoznaj się z [Zarządzanie właścicieli pakietu na PowerShellGallery.com](./how-to/publishing-packages/managing-package-owners.md) Aby uzyskać szczegółowe informacje.

## <a name="how-do-i-deal-with-a-package-owner-who-is-violating-my-package-license"></a>Sposób postępowania z właścicielem pakietu, który narusza licencję pakietu

Firma Microsoft zachęca do społeczności programu PowerShell, aby współpracują ze sobą w celu rozwiązania wszelkich sporów, które mogą wystąpić między właścicieli pakietu i innych pakietów.  Firma Microsoft ma specjalnie [proces rozstrzygania sporów](./how-to/getting-support/dispute-resolution.md) , poprosimy Cię, które należy wykonać przed intercede PowerShellGallery.com administratorów.

[New-ModuleManifest]: /powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest
[Test-ModuleManifest]: /powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest
[Update-ModuleManifest]: /powershell/module/Microsoft.PowerShell.Core/Update-ModuleManifest

[Install-Module]: /powershell/module/PowershellGet/Install-Module
[New-ScriptFileInfo]: /powershell/module/PowershellGet/New-ScriptFileInfo
[Publish-Module]: /powershell/module/PowershellGet/Publish-Module
[Publish-Script]: /powershell/module/PowershellGet/Publish-Script
[Register-PSRepository]: /powershell/module/PowershellGet/Register-PSRepository
[Test-ScriptFileInfo]: /powershell/module/PowershellGet/Test-ScriptFileInfo
[Update-Module]: /powershell/module/PowershellGet/Update-Module
[Update-ScriptFileInfo]: /powershell/module/PowershellGet/Update-ScriptFileInfo
