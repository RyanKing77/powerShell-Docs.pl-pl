---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: Często zadawane pytania dotyczące galerii programu PowerShell
ms.openlocfilehash: e377e71cf5eeb1f8b73430cc0b97527eac970cff
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="frequently-asked-questions"></a>Często zadawane pytania

## <a name="what-is-a-powershell-module"></a>Co to jest moduł programu PowerShell?

Moduł programu PowerShell jest wielokrotnego użytku pakiet zawierający niektóre funkcje programu PowerShell. W modułach można spakować wszystko w programie PowerShell (funkcje, zmienne, DSC zasobów itp.). Moduły są zazwyczaj folderów zawierających określonych typów plików przechowywanych w określonej ścieżce. Istnieje kilka różnych typów tam moduły programu PowerShell.

## <a name="what-is-a-powershell-script"></a>Co to jest skrypt programu PowerShell?

Skrypt programu PowerShell jest serii poleceń, które są przechowywane w pliku .ps1, aby umożliwić udostępnianie i ponowne użycie. Przepływy pracy programu PowerShell są również skrypty programu PowerShell, które przedstawiają zestaw zadań i podaj sekwencji zadań. Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie do przepływu pracy programu PowerShell](https://technet.microsoft.com/library/jj134242.aspx).

## <a name="how-are-powershell-scripts-different-from-powershell-modules"></a>Jak skrypty programu PowerShell są inne niż moduły programu PowerShell

Moduły są zazwyczaj większą do udostępniania, ale jest włączane, udostępnianie skryptu w celu ułatwienia współtworzenia przepływami pracy a skryptami społeczności. Aby uzyskać więcej informacji można znaleźć na następujących blogach:

- [Nie pisanie skryptów, moduły programu PowerShell zapisu](https://blogs.technet.microsoft.com/heyscriptingguy/2011/06/27/dont-write-scripts-write-powershell-modules/)
- [Opis modułów programu PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/07/10/understanding-powershell-modules/)

## <a name="how-can-i-publish-to-the-powershell-gallery"></a>Jak można publikować w galerii programu PowerShell?

Przed rozpoczęciem publikowania elementów galerii, musisz zarejestrować konta w galerii programu PowerShell. Jest to spowodowane publikowania elementów wymaga NuGetApiKey, która jest dostępna podczas rejestracji. Aby zarejestrować, służbowy osobiste, konta służbowego do logowania się w galerii programu PowerShell. Proces rejestracji jednorazowe jest wymagany, gdy zalogujesz się po raz pierwszy. Później NuGetApiKey programu jest dostępna na stronie profilu.

Po zarejestrowaniu się w galerii, użyj [modułu publikowania](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) lub [skryptu publikowania](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) poleceń cmdlet do publikowania tego elementu w galerii. Więcej szczegółów na temat sposobu uruchamiania tych poleceń cmdlet, odwiedź stronę karty Publikowanie lub odczytać [modułu publikowania](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) i [skryptu publikowania](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) dokumentacji.

**Nie należy do zarejestrowania lub zaloguj się do galerii, aby zainstalować lub zapisać elementów.**

## <a name="i-received-failed-to-process-request-the-specified-api-key-is-invalid-or-does-not-have-permission-to-access-the-specified-package-the-remote-server-returned-an-error-403-forbidden-error-when-i-tried-to-publish-an-item-to-the-powershell-gallery-what-does-that-mean"></a>Otrzymuję "nie można przetworzyć żądania. "Określony klucz interfejsu API jest nieprawidłowa lub nie ma uprawnień dostępu do określonego pakietu.". Serwer zdalny zwrócił błąd: (403) zabroniony. " Wystąpił błąd przy próbie opublikować element galerii programu PowerShell. Co to oznacza?

Ten błąd może wystąpić z następujących powodów:

- **Określony klucz interfejsu API jest nieprawidłowa.**
     Upewnij się, że określono nieprawidłowy klucz interfejsu API z Twojego konta. Aby uzyskać klucz interfejsu API, Wyświetl strony swojego profilu.
- **Nazwa określonego elementu właścicielem nie jest użytkownik.**
     Jeśli potwierdzeniu, że klucz interfejsu API jest poprawna, a następnie może już istnieć element o takiej samej nazwie, który próbujesz użyć. Element zostały nieznajdujące się na liście przez właściciela, przez co nie będzie wyświetlany w żadnych wyników wyszukiwania. Aby ustalić, czy element o takiej samej nazwie już istnieje, otwórz przeglądarkę i przejdź do strony szczegółów elementu: `https://www.powershellgallery.com/packages/<itemName>`. Na przykład Nawigacja bezpośrednio do `https://www.powershellgallery.com/packages/pester` spowoduje przejście do strony szczegółów modułu Pester, czy nie jest on nieznajdujące się na liście. Jeśli element o nazwie powodujące konflikt już istnieje i jest nieznajdujące się na liście, można:
    - Wybierz inną nazwę dla tego elementu.
    - Skontaktuj się z właściciele istniejący element.

## <a name="why-cant-i-sign-in-with-my-personal-account-but-i-could-sign-in-yesterday"></a>Dlaczego nie można zalogować się przy użyciu konta osobiste, ale można zarejestrować się w wczoraj?

Należy pamiętać, Twoje konto galerii nie obsługuje zmiany zmian aliasu podstawowego poczty e-mail. Aby uzyskać więcej informacji, zobacz [aliasów E-mail Microsoft](https://windows.microsoft.com/windows/outlook/add-alias-account).

## <a name="why-dont-i-see-all-the-gallery-items-when-i-select-all-the-category-checkboxes-on-the-items-tab"></a>Dlaczego nie widzisz wszystkich elementów galerii, po wybraniu wszystkich kategorii odpowiednie pola wyboru na karcie elementy?

Zaznaczając pole wyboru kategorii są podając "Chcę wyświetlić wszystkie elementy w tej kategorii." Pojawi się tylko do elementów w wybranej kategorii. Dlatego podobnie wybierając wszystkie pola wyboru kategorii, możesz są z informacją "Chcę wyświetlić wszystkie elementy w każdej kategorii." Jednak niektóre elementy w galerii należy do żadnej kategorii na liście, więc nie będą widoczne w wynikach. Aby wyświetlić wszystkie elementy w galerii, wyczyść wszystkie kategorie, lub wybierz kartę elementy ponownie.

## <a name="what-are-the-requirements-to-publish-a-module-to-the-powershell-gallery"></a>Jakie są wymagania, aby opublikować modułu w galerii programu PowerShell?

Dowolny rodzaj modułu programu PowerShell (modułów skryptów, moduły binarne lub moduły manifestu) mogą być publikowane do galerii. Aby opublikować modułu, PowerShellGet musi wiedzieć, kilka rzeczy, o - wersji, opis, autora i jak jest licencjonowana. Te informacje jest do odczytu w trakcie procesu publikowania z *manifestu modułu* pliku (psd1), lub wartość [ **modułu publikowania** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet **LicenseUri** parametru. Wszystkie moduły opublikowany w galerii musi mieć manifestów modułu. Każdy moduł, który zawiera następujące informacje w swoim manifeście można opublikować w galerii:

- Wersja
- Opis
- Autor
- Identyfikator URI postanowień licencyjnych modułu, albo w ramach **PrivateData** sekcji manifestu lub w **LicenseUri** parametr [ **Publish-Module** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) polecenia cmdlet.

## <a name="how-do-i-create-a-correctly-formatted-module-manifest"></a>Jak utworzyć manifestu modułu prawidłowo sformatowane?

Najprostszym sposobem tworzenia manifestu modułu jest uruchomienie [ **ModuleManifest nowy** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) polecenia cmdlet. W programie PowerShell 5.0 lub nowszej, New-ModuleManifest generuje manifest modułu prawidłowo sformatowane z puste pola przydatne metadanych, takich jak **ProjectUri**, **LicenseUri**, i **tagi**. Po prostu Wypełnij puste wartości, lub użyj wygenerowanego manifestu na przykład poprawnego formatowania.

Aby sprawdzić, czy wszystkie wymagane pola metadane zostały poprawnie wypełnione, użyj [ **ModuleManifest testu** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) polecenia cmdlet.

Aby zaktualizować pola pliku manifestu modułu, należy użyć [ **ModuleManifest aktualizacji** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) polecenia cmdlet.

## <a name="what-are-the-requirements-to-publish-a-script-to-the-gallery"></a>Jakie są wymagania dotyczące publikowania skrypt do galerii?

Dowolny skrypt programu PowerShell (skrypty lub przepływów pracy) mogą być publikowane do galerii. Aby opublikować skryptu, PowerShellGet musi wiedzieć, kilka rzeczy, o - wersji, opis, autora i jak jest licencjonowana. Te informacje jest do odczytu w trakcie procesu publikowania z pliku skryptu *PSScriptInfo* sekcji, lub wartość [ **publikowania skryptu** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet  **LicenseUri** parametru. Wszystkie skrypty opublikowany w galerii musi mieć informacji o metadanych. Dowolny skrypt, który zawiera następujące informacje w sekcji dotyczącej PSScriptInfo można opublikować w galerii:

- Wersja
- Opis
- Autor
- Identyfikator URI postanowienia licencyjne dotyczące skryptu, albo w ramach **PSScriptInfo** sekcji skryptu lub w **LicenseUri** parametr [ **skryptów publikowania** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) polecenia cmdlet.

## <a name="how-do-i-search"></a>Sposób wyszukiwania

Wpisz, czego szukasz w polu tekstowym. Na przykład jeśli chcesz znaleźć modułów, które odnoszą się do bazy danych SQL Azure, wpisz "azure sql". Nasze aparat wyszukiwania będzie szukać tych słów kluczowych w opublikowanych elementów, w tym tytuły i opisy oraz w metadanych. Następnie w oparciu o wynik ważoną jakości, będzie wyświetlany najbliższy dopasowań. Można także przeszukać według określonego pola za pomocą pola: "wartość" składni w kwerendzie wyszukiwania dla następujących pól:

- Tagi
- Funkcje
- Polecenia cmdlet
- DscResources
- PowerShellVersion

Tak, na przykład podczas wyszukiwania PowerShellVersion: "2.0" tylko wyniki, które są zgodne z PowerShellVersion 2.0 (oparte na ich manifest skryptu lub modułu) zostaną wyświetlone.

## <a name="how-do-i-create-a-correctly-formatted-script-file"></a>Jak utworzyć plik skryptu prawidłowo sformatowane?

Najprostszym sposobem tworzenia pliku skryptu poprawnie sformatowana jest uruchomienie [ **ScriptFileInfo nowy** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) polecenia cmdlet. W programie PowerShell 5.0, New-ScriptFileInfo generuje plik skryptu prawidłowo sformatowane z puste pola przydatne metadanych, takich jak **ProjectUri**, **LicenseUri**, i **tagi** . Po prostu Wypełnij puste wartości lub użyć pliku skryptu wygenerowany przykład poprawnego formatowania.

Aby sprawdzić, czy wszystkie wymagane pola metadane zostały poprawnie wypełnione, użyj [ **ScriptFileInfo testu** ](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) polecenia cmdlet.

Aby zaktualizować pola metadanych skryptu, użyj [ **ScriptFileInfo aktualizacji** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) polecenia cmdlet.

## <a name="what-other-types-of-powershell-modules-exist"></a>Jakie inne rodzaje moduły programu PowerShell?

Moduł PowerShell termin odnosi się także do plików, które implementuje rzeczywistej funkcji. Pliki modułu skryptu (.psm1) zawiera kod programu PowerShell. Pliki binarne modułu (.dll) zawierają skompilowany kod.

W tym miejscu jest jednym ze sposobów można traktować go: folder, który hermetyzuje modułu jest folder modułu. Folder moduł może zawierać manifestu modułu (psd1), który opisuje zawartość folderu. Pliki, które faktycznie pracy są pliki modułu skryptu (.psm1) i pliki binarne modułu (.dll). Zasoby usługi Konfiguracja DSC znajdują się w określonym folderze podrzędne i są zaimplementowane jako pliki modułu skryptu lub pliki binarne modułu.

Wszystkie moduły w galerii zawierać manifestów modułu, a większość tych modułów pliki modułu skryptu lub pliki binarne modułu. Z powodu tych inną funkcję modułu terminu może być trudne. O ile nie zaznaczono inaczej, wszystkie użycia modułu programu word na tej stronie można znaleźć folderu modułu zawierające te pliki.

## <a name="how-does-packagemanagement-relate-to-powershellget-high-level-answer"></a>Jaki jest związek między PackageManagement PowerShellGet? (Wysokiego poziomu odpowiedzi)

PackageManagement jest wspólny interfejs do pracy z dowolnego Menedżera pakietów. Po pewnym czasie czy jest zajmujących moduły programu PowerShell, MSI, gems dopisków fonetycznych, pakiety NuGet lub moduły Perl, można używać poleceń w PackageManagement (Znajdź pakiet i Install-Package), aby znaleźć i zainstalować je. PackageManagement robi to przez dostawcę pakietu dla każdego Menedżera pakietów, które podłącza się do PackageManagement. Dostawców wykonać całą pracę; Pobieranie zawartości z repozytoriami i zainstaluj zawartość lokalnie. Często dostawców pakietu po prostu otacza istniejące narzędzia menedżera pakietu dla typu danego pakietu.

PowerShellGet jest Menedżer pakietów dla elementów programu PowerShell. Brak dostawcy pakietu PSModule, który udostępnia funkcje PowerShellGet za pośrednictwem PackageManagement. W związku z tym można uruchomić [instalacji modułu](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) lub Install-Package-PSModule dostawcy, aby zainstalować moduł z galerii programu PowerShell. Niektóre funkcje PowerShellGet tym [aktualizacji modułu](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) i [modułu publikowania](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), nie będą dostępne za pośrednictwem polecenia PackageManagement.

Podsumowując PowerShellGet koncentruje się wyłącznie na o atrakcyjny interfejs zarządzania pakiet zawartości programu PowerShell. PackageManagement koncentruje się na udostępnianie wszystkie środowiska zarządzania udostępniającego pakietu za pomocą jednego ogólne zestawu narzędzi. Jeśli odpowiedzi to unsatisfying, jest długich odpowiedzi w dolnej części tego dokumentu w **jaki związek PackageManagement faktycznie między PowerShellGet?** sekcji.

Aby uzyskać więcej informacji, odwiedź stronę [PackageManagement projektu strony](https://oneget.org/).

## <a name="how-does-nuget-relate-to-powershellget"></a>Jaki jest związek między NuGet PowerShellGet?

Galerii programu PowerShell jest zmodyfikowanej wersji [galerii NuGet](https://www.nuget.org/). PowerShellGet używa dostawcy NuGet do pracy z repozytoria NuGet, na podstawie takich jak galerii programu PowerShell.

Możesz użyć PowerShellGet przed wszystkie prawidłowe NuGet repozytorium lub w udziale plików. Należy po prostu Dodaj repozytorium, uruchamiając [ **PSRepository rejestru** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) polecenia cmdlet.

## <a name="does-that-mean-i-can-use-nugetexe-to-work-with-the-gallery"></a>Czy oznacza to, że do pracy z galerii można używać NuGet.exe?

Tak.

## <a name="how-does-packagemanagement-actually-relate-to-powershellget-technical-details"></a>Jak związek PackageManagement faktycznie między PowerShellGet? (Szczegóły techniczne)

Pod maską PowerShellGet silnie wykorzystuje infrastrukturę PackageManagement.

W warstwie polecenia cmdlet programu PowerShell [instalacji modułu](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) jest rzeczywiście cienką otoką wokół Install-Package-PSModule dostawcy.

W warstwie dostawcy pakietu PackageManagement dostawcy pakietu PSModule wywołuje do innych dostawców pakietu PackageManagement. Na przykład podczas pracy z systemem NuGet galerie (na przykład galerii programu PowerShell), Dostawca pakietu PSModule używa dostawcy pakietu NuGet do pracy z repozytorium.

![Architektura PowerShellGet](Images/powershellgetArchitecture.png)

Rysunek 1: Architektura PowerShellGet

## <a name="what-is-required-to-run-powershellget"></a>Co to jest wymagany do uruchamiania PowerShellGet?

Ogólnie zaleca się pobrania najnowszej wersji modułu PowerShellGet (należy pamiętać, że wymaga platformy .NET 4.5).

**PowerShellGet** module wymaga **programu PowerShell 3.0 lub nowszej**.

W związku z tym **PowerShellGet** wymaga jednego z następujących systemów operacyjnych:

- 10 systemu Windows
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 z dodatkiem SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 z dodatkiem SP1

**PowerShellGet** również wymaga programu .NET Framework 4.5 lub nowszej. Możesz zainstalować program .NET Framework 4.5 lub nowszy z [tutaj](https://msdn.microsoft.com/library/5a4x27ek.aspx).

## <a name="is-it-possible-to-reserve-names-for-items-that-will-be-published-in-future"></a>Czy jest możliwe do zarezerwowania nazwy elementów, które zostaną opublikowane w przyszłości?

Nie jest możliwe wpuszczana w podłogę elementu nazwy. Jeśli uważasz, że istniejący element miało nazwy, która odpowiada przedmiot więcej, spróbuj [skontaktowanie się z właścicielem elementu](./how-to/working-with-items/contacting-item-owners.md). Jeśli nie otrzymasz odpowiedzi w ciągu kilku tygodni, można się z pomocą techniczną i będzie przeszukiwać zespołu galerii programu PowerShell do niego.

## <a name="how-do-i-claim-ownership-for-items-"></a>Jak potwierdzić prawa własności do elementów?

Zapoznaj się z [Zarządzanie właścicieli elementu na PowerShellGallery.com](./how-to/publishing-items/managing-item-owners.md) szczegółowe informacje.

## <a name="how-do-i-deal-with-an-item-owner-who-is-violating-my-item-license"></a>Sposób postępowania z właściciela elementu, który narusza licencję elementu

Firma Microsoft zachęca społeczności programu PowerShell współdziałają ze sobą rozwiązywać wszelkie sporów, które mogą wystąpić podczas między elementu właścicieli i innych elementów.  Firma Microsoft ma co [rozstrzygania procesu rozpoznawania](./how-to/getting-support/dispute-resolution.md) który poprosimy o należy wykonać przed intercede PowerShellGallery.com Administratorzy.