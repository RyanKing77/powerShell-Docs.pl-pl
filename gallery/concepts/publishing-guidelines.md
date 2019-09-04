---
ms.date: 06/12/2017
contributor: JKeithB, SydneyhSmith
keywords: Galeria, PowerShell, cmdlet, psgallery
description: Wytyczne dla wydawców
title: Galeria programu PowerShell wskazówki dotyczące publikowania i najlepsze rozwiązania
ms.openlocfilehash: aa7ac4eeb96e8234bbac820fea6cab2b37f688d0
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215368"
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a>Wskazówki dotyczące publikowania PowerShellGallery i najlepsze rozwiązania

W tym artykule opisano zalecane kroki używane przez zespoły Microsoft Teams w celu zapewnienia, że pakiety opublikowane w Galeria programu PowerShell będą powszechnie stosowane i zapewniają wysoką wartość użytkownikom, na podstawie sposobu, w jaki Galeria programu PowerShell obsługuje dane manifestu i informacje zwrotne z dużych Liczba użytkowników, którzy Galeria programu PowerShell. Pakiety opublikowane w ramach tych wytycznych będą prawdopodobnie zainstalowane, zaufane i przyciągnąć większej liczby użytkowników.

Poniżej przedstawiono wskazówki dotyczące tego, co to jest dobry pakiet Galeria programu PowerShell, jakie opcjonalne ustawienia manifestu są najważniejsze, ulepszanie kodu z informacjami zwrotnymi od recenzentów początkowych i [analizatora skryptów programu PowerShell](https://aka.ms/psscriptanalyzer), przechowywanie wersji modułu, Dokumentacja, testy i przykłady dotyczące korzystania z udostępnionych elementów. W większości tej dokumentacji przedstawiono wskazówki dotyczące publikowania [modułów zasobów o wysokiej jakości DSC](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md).

Mechanics publikowania pakietu do Galeria programu PowerShell można znaleźć w temacie [Tworzenie i publikowanie pakietu](/powershell/gallery/how-to/publishing-packages/publishing-a-package).

Opinie dotyczące tych wytycznych zostały zawitane.
Jeśli masz opinię, Otwórz problemy w naszym [repozytorium dokumentacji usługi GitHub](https://github.com/powershell/powershell-docs/issues).

## <a name="best-practices-for-publishing-packages"></a>Najlepsze rozwiązania dotyczące publikowania pakietów

Poniżej przedstawiono najlepsze rozwiązania dotyczące tego, co jest ważne dla użytkowników Galeria programu PowerShell elementów i są one wymienione w kolejności nominalnego priorytetu. Pakiety, które są zgodne z tymi wytycznymi, są znacznie łatwiejsze do pobrania i przyjęcia przez inne osoby.

- Użyj PSScriptAnalyzer
- Dołącz dokumentację i przykłady
- Reagowanie na Opinie
- Dostarczanie modułów zamiast skryptów
- Udostępnianie linków do witryny projektu
- Oznacz swój pakiet za pomocą zgodnych PSEdition i platform
- Uwzględnij testy z modułami
- Dołącz i/lub Połącz z postanowieniami licencyjnymi
- Podpisz swój kod
- Postępuj zgodnie z [SemVer](https://semver.org/) wytycznych dotyczących przechowywania wersji
- Używaj typowych tagów, jak opisano w typowych tagach Galeria programu PowerShell
- Testowanie publikacji przy użyciu repozytorium lokalnego
- Użyj PowerShellGet do opublikowania

Każda z nich została omówiona krótko w poniższych sekcjach.

## <a name="use-psscriptanalyzer"></a>Użyj PSScriptAnalyzer

[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) to bezpłatne narzędzie do analizy kodu statycznego, które działa w kodzie programu PowerShell. **PSScriptAnalyzer** będzie identyfikować najczęstsze problemy występujące w kodzie programu PowerShell i często zalecenia dotyczące sposobu rozwiązania problemu. Narzędzie jest łatwe w użyciu i klasyfikuje problemy jako błędy (poważne, muszą być rozwiązane), ostrzeżenie (należy sprawdzić i należy je rozwiązać) oraz informacje (co jest przydatne w przypadku najlepszych rozwiązań). Wszystkie pakiety opublikowane w Galeria programu PowerShell będą skanowane przy użyciu **PSScriptAnalyzer**, a wszelkie błędy zostaną zgłoszone do właściciela i należy je rozwiązać.

Najlepszym rozwiązaniem jest uruchomienie `Invoke-ScriptAnalyzer` z `-Recurse` i `-Severity` ostrzeżenie.

Przejrzyj wyniki i upewnij się, że:

- Wszystkie błędy są poprawiane lub rozwiązane w dokumentacji.
- Wszystkie ostrzeżenia są analizowane i są rozwiązywane, gdy ma to zastosowanie.

Użytkownicy, którzy pobierają pakiety z Galeria programu PowerShell, zdecydowanie zachęca się do uruchamiania **PSScriptAnalyzer** i szacowania wszystkich błędów i ostrzeżeń. Użytkownicy bardzo mogą kontaktować się z właścicielami pakietów, Jeśli zobaczysz, że wystąpił błąd zgłoszony przez **PSScriptAnalyzer**. Jeśli istnieje atrakcyjny powód, aby pakiet mógł zachować kod oflagowany jako błąd, Dodaj te informacje do dokumentacji, aby uniknąć konieczności odpowiedzi na to samo pytanie wiele razy.

## <a name="include-documentation-and-examples"></a>Dołącz dokumentację i przykłady

Dokumentacja i przykłady są najlepszym sposobem zapewnienia, że użytkownicy będą mogli korzystać z dowolnego kodu udostępnionego.

Dokumentacja jest najbardziej przydatna do uwzględnienia w pakietach opublikowanych w Galeria programu PowerShell.
Użytkownicy zwykle omijają pakiety bez dokumentacji, ponieważ alternatywą jest odczytanie kodu, aby zrozumieć, co to jest pakiet i jak go używać. Dostępnych jest kilka artykułów o udostępnianiu dokumentacji z pakietami programu PowerShell, w tym:

- Wskazówki dotyczące udostępniania pomocy znajdują się w temacie [jak pisać pomoc poleceń cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415).
- Tworzenie pomocy dotyczącej poleceń cmdlet, która jest najlepszym rozwiązaniem dla dowolnego skryptu, funkcji lub polecenia cmdlet programu PowerShell.
  Aby uzyskać informacje o sposobach tworzenia pomocy dotyczącej poleceń cmdlet, Zacznij od [pisania pomocy poleceń cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415).
  Aby dodać pomoc w ramach skryptu, zobacz [Informacje o pomocy na temat komentarzy](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).
- Wiele modułów zawiera również dokumentację w formacie tekstowym, na przykład pliki o promocji. Może to być szczególnie przydatne, gdy w serwisie GitHub znajduje się witryna projektu, w której jest to wysoce używany format. Najlepszym rozwiązaniem jest użycie [promocji z obsługą usługi GitHub](https://help.github.com/categories/writing-on-github/).

Przykłady przedstawiają sposób, w jaki pakiet jest przeznaczony do użycia. Wielu deweloperów zobaczy, że zapoznają się z przykładami przed dokumentacją, aby zrozumieć, jak to zrobić. Najlepsze typy przykładów pokazują podstawowe użycie oraz symulowany realistyczny przypadek użycia i kod jest dobrze komentarz. Przykłady dla modułów opublikowanych w Galeria programu PowerShell powinny znajdować się w folderze przykładów w katalogu głównym modułu.

Dobry wzorzec przykładów można znaleźć w `Examples\RegistryResource` [module PSDscResource](https://www.powershellgallery.com/packages/PSDscResources) w folderze. Istnieją cztery przykładowe przypadki użycia z krótkim opisem w górnej części każdego pliku, który dokumentuje co jest prezentowane.

## <a name="manage-dependencies"></a>Zarządzanie zależnościami

Ważne jest, aby określić moduły, od których moduł jest zależny w manifeście modułu. Dzięki temu użytkownik końcowy nie musi martwić się o zainstalowanie odpowiednich wersji modułów, na których należy wziąć zależność. Aby określić moduły zależne, należy użyć pola wymagane modułu w manifeście modułu. Spowoduje to załadowanie dowolnego z wymienionych modułów do środowiska globalnego przed zaimportowaniem modułu, chyba że zostały już załadowane. Na przykład niektóre moduły mogą już być załadowane przez inny moduł. Istnieje również możliwość określenia konkretnej wersji do załadowania przy użyciu pola **RequiredVersion** , a nie pola **ModuleVersion** . W przypadku korzystania z programu **ModuleVersion**zostanie załadowana Najnowsza wersja dostępna z co najmniej określoną wersją. Gdy nie korzystasz z pola **RequiredVersion** , aby określić konkretną wersję, ważne jest, aby monitorować aktualizacje wersji do wymaganego modułu. Szczególnie ważne jest, aby mieć świadomość wszelkich istotnych zmian, które mogą mieć wpływ na środowisko użytkownika w Twoim module.

```powershell
Example: RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})

Example: RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})
```

## <a name="respond-to-feedback"></a>Odpowiedź na opinię

Właściciele pakietu, którzy prawidłowo reagują na opinie, mają wysoką wartość przez społeczność. Użytkownicy, którzy przedstawiają konstruktywną opinię, są ważną odpowiedzią, ponieważ są one wystarczająco interesujące w pakiecie, aby pomóc w ulepszaniu tego rozwiązania.

W Galeria programu PowerShell są dostępne dwie metody przesyłania opinii:

- Właściciel kontaktu: Dzięki temu użytkownik może wysłać wiadomość e-mail do właściciela pakietu. Jako właściciel pakietu jest ważne, aby monitorować adres e-mail używany z pakietami Galeria programu PowerShell i odpowiadać na zgłoszone problemy. Wadą tej metody jest to, że tylko użytkownik i właściciel będą widzieli komunikację, więc właściciel może mieć wiele razy odpowiedzieć na to samo pytanie.
- Komentarz W dolnej części strony pakietu znajduje się pole **komentarz** . Zaletą tego systemu jest to, że inni użytkownicy mogą zobaczyć Komentarze i odpowiedzi, co zmniejsza liczbę przypadków, w których należy odpowiedzieć na pojedyncze pytanie. Jako właściciel pakietu zdecydowanie zalecamy przestrzeganie komentarzy wykonanych dla każdego pakietu. Aby uzyskać szczegółowe informacje o tym, jak to zrobić, zobacz [przekazywanie opinii za pośrednictwem mediów społecznościowych i komentarzy](../how-to/working-with-packages/social-media-feedback.md) .

Właściciele, którzy reagują na opinie, zwyczajowo doceniają społeczność. Aby uzyskać więcej informacji, Skorzystaj z szansy sprzedaży w raporcie. W razie konieczności należy zastosować obejście lub określić, czy aktualizacja rozwiązuje problem.

W przypadku niewłaściwego zachowania zaobserwowanego z dowolnego z tych kanałów komunikacji Użyj funkcji Zgłoś nadużycie w Galeria programu PowerShell, aby skontaktować się z administratorami galerii.

## <a name="modules-versus-scripts"></a>Moduły a skrypty

Udostępnianie skryptu innym użytkownikom jest doskonałe i zawiera inne przykłady sposobu rozwiązywania problemów, które mogą mieć. Problem polega na tym, że skrypty w Galeria programu PowerShell są pojedynczymi plikami bez oddzielnej dokumentacji, przykładów i testów.

Moduły programu PowerShell mają strukturę folderów, która umożliwia dołączenie wielu folderów i plików do pakietu. Struktura modułów umożliwia uwzględnienie innych pakietów, które są wystawiane jako najlepsze rozwiązania: pomoc poleceń cmdlet, dokumentacja, przykłady i testy. Największą wadą jest to, że skrypt wewnątrz modułu musi być uwidoczniony i używany jako funkcja. Aby uzyskać informacje na temat sposobu tworzenia modułu, zobacz [pisanie modułu programu Windows PowerShell](/powershell/developer/module/writing-a-windows-powershell-module).

Istnieją sytuacje, w których skrypt zapewnia lepszy interfejs użytkownika, w szczególności konfiguracje DSC. Najlepszym rozwiązaniem w przypadku konfiguracji DSC jest opublikowanie konfiguracji jako skryptu z towarzyszącym modułem zawierającym dokumenty, przykłady i testy. Skrypt zawiera listę towarzyszącego modułu przy `RequiredModules = @(Name of the Module)`użyciu. Takie podejście może być używane z dowolnym skryptem.

Skrypty autonomiczne, które są zgodne z innymi najlepszymi rozwiązaniami, zapewniają wartość rzeczywistą innym użytkownikom. Udostępnianie dokumentacji opartej na komentarzach i link do witryny projektu jest zdecydowanie zalecane podczas publikowania skryptu do Galeria programu PowerShell.

## <a name="provide-a-link-to-a-project-site"></a>Podaj link do witryny projektu

Witryna projektu to miejsce, w którym Wydawca może współdziałać bezpośrednio z użytkownikami ich pakietów Galeria programu PowerShell. Użytkownicy preferują pakiety, które je zapewniają, ponieważ umożliwiają im łatwiejsze uzyskiwanie informacji o pakiecie. Wiele pakietów w Galeria programu PowerShell są opracowywane w serwisie GitHub, a inne są udostępniane przez organizacje z dedykowaną obecnością w sieci Web. Każdy z nich może być traktowany jako witryna projektu.

Dodawanie linku odbywa się przez włączenie ProjectURI w sekcji PSData manifestu w następujący sposób:

        # A URL to the main website for this project.
        ProjectUri = 'https://github.com/powershell/powershell'

Gdy ProjectURI jest podany, Galeria programu PowerShell będzie zawierać link do witryny projektu po lewej stronie pakietu.

## <a name="tag-your-package-with-the-compatible-pseditions-and-platforms"></a>Oznacz swój pakiet za pomocą zgodnych PSEdition i platform

Użyj następujących tagów, aby zademonstrować użytkownikom, które pakiety będą dobrze współpracować ze swoimi środowiskami:

- PSEdition_Desktop: Pakiety zgodne z programem Windows PowerShell
- PSEdition_Core: Pakiety zgodne z programem PowerShell Core
- W systemie Windows: Pakiety zgodne z systemem operacyjnym Windows
- W systemie Linux: Pakiety zgodne z systemami operacyjnymi Linux
- MacOS Pakiety zgodne z systemem operacyjnym Mac

Tagowanie pakietu przy użyciu zgodnych platform, które zostaną dołączone do filtrów wyszukiwania galerii w lewym okienku wyników wyszukiwania. Jeśli pakiet jest hostowany w serwisie GitHub, po oznaczeniu pakietu możesz skorzystać z naszej![osłony](https://img.shields.io/powershellgallery/p/CosmosDB.svg)zgodności z usługą [Galeria programu PowerShell Compatibility](https://img.shields.io/powershellgallery/p/:packageName.svg)
.

## <a name="include-tests"></a>Uwzględnij testy

Uwzględnienie testów z kodem Open Source jest ważne dla użytkowników, ponieważ daje im gwarancje dotyczące tego, co jest sprawdzane i zawiera informacje na temat sposobu działania kodu. Umożliwia ona również użytkownikom zagwarantowanie, że nie przerywają pierwotnych funkcji, jeśli zmodyfikujesz swój kod w celu dopasowania go do środowiska.

Zdecydowanie zaleca się, aby testy były napisane w celu skorzystania z platformy testów szkodników, która została zaprojektowana specjalnie dla programu PowerShell. Program szkodnik jest dostępny w witrynie [GitHub](https://github.com/Pester/Pester), [Galeria programu PowerShell](https://www.powershellgallery.com/packages/Pester/)i dostarcza w systemie Windows 10, Windows Server 2016, wmf 5,0 i WMF 5,1.

[Witryna projektu szkodników w usłudze GitHub](https://github.com/Pester/Pester) zawiera dobrą dokumentację dotyczącą pisania testów szkodników, od rozpoczęcia do najlepszych rozwiązań.

Elementy docelowe dla pokrycia testu są wywoływane w [dokumentacji modułu zasobów o wysokiej jakości](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md)z zalecanym pokryciem kodu w przypadku 70%.

## <a name="include-andor-link-to-license-terms"></a>Dołącz i/lub Połącz z postanowieniami licencyjnymi

Wszystkie pakiety opublikowane w Galeria programu PowerShell muszą określać postanowienia licencyjne lub być powiązane z licencją zawartą w [warunkach użytkowania](https://www.powershellgallery.com/policies/Terms) w obszarze **wystawiony A**. Najlepszym podejściem do określenia innej licencji jest udostępnienie linku do licencji przy użyciu **LicenseURI** w **PSData**. Aby uzyskać więcej informacji, zobacz [interfejs użytkownika manifestu i kolekcji pakietów](package-manifest-affecting-ui.md).

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a>Podpisz swój kod

Podpisywanie kodu zapewnia użytkownikom najwyższy poziom pewności, kto opublikował pakiet, i że kopia pobieranego kodu jest dokładnie wydaną przez wydawcę. Aby dowiedzieć się więcej na temat ogólnego podpisywania kodu, zobacz [wprowadzenie do podpisywania kodu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85)).
Program PowerShell obsługuje sprawdzanie poprawności podpisywania kodu przez dwa podstawowe podejścia:

- Podpisywanie plików skryptu
- Podpisywanie modułu przez katalog

Podpisywanie plików programu PowerShell to dobrze ustalone podejście do zapewnienia, że wykonywany kod został wyprodukowany przez niezawodne źródło i nie został zmodyfikowany. Szczegóły dotyczące podpisywania plików skryptów programu PowerShell znajdują się w artykule [dotyczącym podpisywania](/powershell/module/microsoft.powershell.core/about/about_signing) . W obszarze przegląd można dodać podpis do każdego `.PS1` pliku, który program PowerShell sprawdza po załadowaniu skryptu. Program PowerShell można ograniczyć za pomocą poleceń cmdlet [zasad wykonywania](/powershell/module/microsoft.powershell.core/about/about_execution_policies) , aby zapewnić możliwość korzystania ze podpisanych skryptów.

Moduły podpisywania katalogu to funkcja dodana do programu PowerShell w wersji 5,1. Sposób podpisywania modułu znajduje się w artykule [polecenia cmdlet katalogu](/powershell/wmf/5.1/catalog-cmdlets) . W obszarze przegląd podpisywanie wykazu jest wykonywane przez utworzenie pliku wykazu, który zawiera wartość skrótu dla każdego pliku w module, a następnie podpisuje ten plik.

**PowerShellGet** `Publish-Module`, ,`Install-Module`i poleceniacmdletsprawdzająpodpis,abyupewnićsię,żejestonprawidłowy,anastępniepotwierdź,żewartośćskrótudlakażdegopakietujestzgodnaztym,coznajduje`Update-Module` się w katalogu. `Save-Module`nie weryfikuje podpisu. Jeśli w systemie zainstalowano poprzednią wersję modułu, `Install-Module` program potwierdzi, że urząd podpisywania dla nowej wersji pasuje do tego, co zostało wcześniej zainstalowane. `Install-Module`i `Update-Module` użyje podpisu `.PSD1` w pliku, jeśli pakiet nie jest podpisany w wykazie. Podpisywanie wykazu współpracuje z programem, ale nie zastępuje plików skryptów podpisywania. Program PowerShell nie weryfikuje podpisów wykazu w czasie ładowania modułu.

## <a name="follow-semver-guidelines-for-versioning"></a>Postępuj zgodnie z SemVer wytycznych dotyczących przechowywania wersji

[SemVer](https://semver.org/) to publiczna Konwencja opisująca sposób tworzenia struktury i zmiany wersji, aby umożliwić łatwą interpretację zmian. Wersja pakietu musi być uwzględniona w danych manifestu.

- Wersja powinna mieć strukturę jako trzy bloki liczbowe oddzielone kropkami, jak w `0.1.1` lub `4.11.192`.
- Wersje zaczynające `0` się od wskazują, że pakiet nie jest jeszcze gotowy do produkcji, a pierwszy numer powinien `0` rozpoczynać się tylko wtedy, gdy jest to jedyna użyta liczba.
- Zmiany w pierwszej liczbie (`1.9.9999` do `2.0.0`) wskazują na główne i istotne zmiany między wersjami.
- Zmiany w drugiej liczbie (`1.1` do `1.2`) wskazują zmiany na poziomie funkcji, takie jak dodawanie nowych poleceń cmdlet do modułu.
- Zmiany trzeciego numeru wskazują na niekrytyczne zmiany, takie jak nowe parametry, zaktualizowane przykłady lub nowe testy.
- Podczas tworzenia listy wersji program PowerShell sortuje wersje jako ciągi, więc `1.01.0` będzie traktowany jako większy niż `1.001.0`.

Program PowerShell został utworzony przed opublikowaniem SemVer, więc zapewnia obsługę większości, ale nie wszystkich elementów SemVer, w szczególności:

- Nie obsługuje on parametrów wersji wstępnej w numerach wersji. Jest to przydatne, gdy Wydawca chce dostarczyć wersję zapoznawczą nowej wersji głównej po udostępnieniu wersji `1.0.0`. Ta wartość będzie obsługiwana w przyszłych wersjach Galeria programu PowerShell i poleceń cmdlet programu **PowerShellGet** .
- Program PowerShell i Galeria programu PowerShell umożliwiają stosowanie ciągów wersji z 1, 2 i 4 segmentami. Wiele wczesnych modułów nie była zgodna z wytycznymi, a wydania produktów firmy Microsoft zawierają informacje o kompilacji jako czwarty blok liczb ( `5.1.14393.1066`na przykład). Różnice między wersjami punktu widzenia są ignorowane.

## <a name="test-using-a-local-repository"></a>Testowanie przy użyciu repozytorium lokalnego

Galeria programu PowerShell nie jest celem do testowania procesu publikowania. Najlepszym sposobem na przetestowanie kompleksowego procesu publikowania w Galeria programu PowerShell jest skonfigurowanie i użycie własnego repozytorium lokalnego. Można to zrobić na kilka sposobów, w tym:

- Skonfiguruj lokalne wystąpienie Galeria programu PowerShell przy użyciu [projektu galerii prywatnej PS](https://github.com/PowerShell/PSPrivateGallery) w serwisie GitHub. Ten projekt w wersji zapoznawczej pomoże Ci skonfigurować wystąpienie Galeria programu PowerShell, które można kontrolować, i użyć dla testów.
- Skonfiguruj [wewnętrzne repozytorium NuGet](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/).
  Będzie to wymagało więcej pracy do skonfigurowania, ale będzie można sprawdzić, czy nie ma kilku innych wymagań, szczególnie sprawdzać użycie klucza interfejsu API oraz czy nie występują zależności w miejscu docelowym podczas publikowania.
- Skonfiguruj udział plików jako **repozytorium**testowe. Jest to łatwe do skonfigurowania, ale ponieważ jest to udział plików, zanotowane powyżej dane nie będą wykonywane. Jedną z potencjalnych zalet w tym przypadku jest to, że udział plików nie sprawdza wymaganego klucza interfejsu API, dlatego można użyć tego samego klucza, który będzie używany do publikowania w Galeria programu PowerShell.

Za pomocą dowolnego `Register-PSRepository` z tych rozwiązań Zdefiniuj nowe **repozytorium**, którego używasz w `-Repository` parametrze dla. `Publish-Module`

Jeden dodatkowy punkt dotyczący publikowania testów: każdy pakiet publikowany w Galeria programu PowerShell nie może zostać usunięty bez pomocy zespołu operacyjnego, który potwierdzi, że nic nie zależy od pakietu, który chcesz opublikować. Z tego powodu nie obsługujemy Galeria programu PowerShell jako celu testowania i skontaktuje się z każdym wydawcą.

## <a name="use-powershellget-to-publish"></a>Użyj PowerShellGet do opublikowania

Zdecydowanie zaleca się, aby wydawcy używali `Publish-Module` poleceń `Publish-Script` cmdlet i podczas pracy z Galeria programu PowerShell. **PowerShellGet** został utworzony, aby zapobiec zapamiętaniu ważnych informacji o instalowaniu i publikowaniu w Galeria programu PowerShell. W przypadku wydawców wybrano pominięcie **PowerShellGet** i użycie klienta **NuGet** lub `Publish-Module`poleceń cmdlet programu **PackageManagement** , zamiast. Istnieje wiele szczegółów, które można łatwo pominąć, co skutkuje różnymi żądaniami obsługi.

Jeśli nie masz przyczyny, że nie możesz korzystać `Publish-Module` z `Publish-Script`programu lub, daj nam znać.
Zaplikowanie problemu w repozytorium GitHub usługi **PowerShellGet** i podaj szczegóły, które powodują wybranie **NuGet** lub **PackageManagement**.

## <a name="recommended-workflow"></a>Zalecany przepływ pracy

Najbardziej myślnym podejściem znalezionym w przypadku pakietów opublikowanych w Galeria programu PowerShell jest:

- Wykonaj wstępne programowanie w witrynie projektu Open Source. Zespół programu PowerShell używa usługi GitHub.
- Aby uzyskać stabilny stan kodu, użyj opinii recenzentów i [analizatora skryptów programu PowerShell](https://aka.ms/psscriptanalyzer) .
- Dołącz dokumentację, aby inni wiedzieli, jak korzystać z pracy.
- Przetestuj akcję publikowania przy użyciu repozytorium lokalnego.
- Opublikuj w Galeria programu PowerShell stabilną lub alfa wersję, pamiętając o uwzględnieniu dokumentacji i linku do witryny projektu.
- Zbierz informacje zwrotne i wykonaj iterację kodu w witrynie projektu, a następnie opublikuj stabilne aktualizacje Galeria programu PowerShell.
- Dodaj przykłady i testy szkodników w projekcie i module.
- Zdecyduj, czy chcesz podpisać pakiet.
- Jeśli uważasz, że projekt jest gotowy do użycia w środowisku produkcyjnym, Opublikuj `1.0.0` wersję do Galeria programu PowerShell.
- Kontynuuj zbieranie opinii i Iterowanie w kodzie na podstawie danych wejściowych użytkownika.
