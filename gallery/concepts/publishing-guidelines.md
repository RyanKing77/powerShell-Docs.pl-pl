---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
description: Wytyczne dotyczące wydawców
title: Galeria programu PowerShell publikowania wskazówki i najlepsze rozwiązania
ms.openlocfilehash: 2ddeae9fdb33a58f97bfeb66079541bb7c5791b1
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851173"
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a>Galerii PowerShellGallery publikowania wskazówki i najlepsze rozwiązania

W tym temacie opisano zalecane kroki używana przez zespoły firmy Microsoft w zapewnienie elementów opublikowanych w galerii programu PowerShell są przyjmowane powszechnie i zapewniać wysoką wartość użytkownikom, oparte na sposób galerii programu PowerShell służy do obsługi manifestu danych i informacji zwrotnych z dużą liczbą użytkowników w galerii programu PowerShell.
Elementy, które są publikowane następujące wskazówki zostanie zainstalowany, jest bardziej prawdopodobne za zaufany i Przyciąganie uwagi większej liczby użytkowników.

Przedstawiony poniżej znajdują się wytyczne dotyczące co sprawia, że dobry element galerii programu PowerShell, jakie opcjonalne ustawienia manifestu są dla Ciebie najważniejsze, ulepszanie kodu za pomocą informacji zwrotnych od początkowego recenzentów i [analizatora skryptu programu Powershell](https://aka.ms/psscriptanalyzer), przechowywanie wersji Twoje modułu, dokumentacji, testy i przykłady dotyczące używania, zostały udostępnione.
Większość niniejszej dokumentacji następujące wytyczne dotyczące publikowania [modułów zasoby DSC w usłudze wysokiej jakości](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md).

Aby uzyskać mechanika publikowania elementu w galerii programu PowerShell, zobacz [tworzenie i publikowanie elementu](https://msdn.microsoft.com/powershell/gallery/psgallery/creating-and-publishing-an-item).

Przyjęte jest opinie na temat tych wytycznych. Jeśli chcesz przesłać opinię, otwórz problemy w naszym [repozytorium dokumentacji w witrynie Github](https://github.com/powershell/powershell-docs/).

## <a name="best-practices-for-publishing-items"></a>Najlepsze rozwiązania dotyczące publikowania elementów

Poniższe najlepsze rozwiązania są co powiedzieć użytkownikom elementów galerii programu PowerShell, ważne jest i są wymienione w kolejności priorytetu symboliczną cenę.
Elementy, które należy wykonać te wytyczne są znacznie bardziej prawdopodobna do pobrania i przyjętych przez innych użytkowników.

- Użyj PSScriptAnalyzer
- Dokumentacja i przykłady
- Szybkość reakcji na opinie
- Podaj modułów zamiast skryptów
- Zawierają linki do witryny projektu
- Uwzględnić testy za pomocą moduły
- Obejmują i/lub łącze do postanowień licencyjnych
- Zarejestruj swój kod
- Postępuj zgodnie z [SemVer](http://semver.org/) wytyczne dotyczące wersji
- Za pomocą typowych tagów, zgodnie z opisem w galerii programu PowerShell typowych tagów
- Publikowanie testu przy użyciu repozytorium lokalnego
- Publikowanie przy użyciu funkcji PowerShellGet

Każda z tych omówiono pokrótce w poniższych sekcjach.

## <a name="use-psscriptanalyzer"></a>Użyj PSScriptAnalyzer

[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) jest narzędzie do analizy kodu statycznego bezpłatne, działające w kod programu PowerShell.
PSScriptAnalyzer zidentyfikuje najbardziej typowych problemów, które są widoczne w kod programu PowerShell, a także często zalecenia dotyczące sposobu rozwiązania problemu.
Narzędzie jest łatwa w użyciu i problemach, jak błędy kategoryzuje (poważny, muszą być kierowane), ostrzegawczy (muszą być analizowane i powinny być kierowane) i informacje (warto wyewidencjonowywanie najlepsze rozwiązania dotyczące).
Wszystkie elementy elementów opublikowanych w galerii programu PowerShell ma zostać przeprowadzone skanowanie za pomocą PSScriptAnalyzer i wszelkie błędy będzie zgłaszana z powrotem do właściciela i należy rozwiązać kwestie.

Najlepszym rozwiązaniem jest uruchamianie `Invoke-ScriptAnalyzer` z `-Recurse` i `-Severity` ostrzeżenie.

Przejrzyj wyniki i upewnij się, że:

- Wszystkie błędy są naprawione lub które zostały rozwiązane w dokumentacji
- Wszystkie ostrzeżenia są przeglądane i rozwiązany, jeśli ma to zastosowanie

Użytkownicy, którzy zakupili elementów z galerii programu PowerShell są zdecydowanie zaleca się uruchamiania PSScriptAnalyzer i ocenić wszystkie błędy i ostrzeżenia.
Użytkownicy są bardzo prawdopodobne, jeśli zobaczą, że jest błąd zgłoszony przez PSScriptAnalyzer skontaktuj się z właścicielami elementów.
W przypadku istotny powód przedmiot, aby zachować kod, który jest oznaczany jako błąd, należy dodać te informacje w dokumentacji, aby uniknąć konieczności Odpowiedz na pytanie, tym samym wiele razy.

## <a name="include-documentation-and-examples"></a>Dokumentacja i przykłady

Dokumentacja i przykłady są najlepszym sposobem, aby upewnić się, że użytkownicy mogą wykorzystać udostępnionego kodu.

Dokumentacja jest najbardziej przydatne rzeczy, które mają zostać objęte elementów opublikowanych w galerii programu PowerShell.
Użytkownicy zazwyczaj będzie pomijać elementów bez dokumentacji, alternatywą jest odczytać kodu, aby zrozumieć, co to jest element i jak z niej korzystać.
Brak dostępnych kilka artykułów w witrynie MSDN na temat sposobu zapewnienia dokumentacji przy użyciu programu PowerShell elementy, takie jak:

- Wytyczne dotyczące zapewnianie pomocy znajdują się w [sposobu pisania pomoc dotyczącą polecenia Cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415)
- Tworzenie pomocy dotyczącej poleceń cmdlet, które jest najlepszym rozwiązaniem dla dowolnego skryptu programu PowerShell, funkcji lub polecenia cmdlet.
  Aby uzyskać informacje o sposobie tworzenia pomocy dotyczącej poleceń cmdlet, rozpoczynać się [sposobu pisania pomoc dotyczącą polecenia Cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415) w bibliotece MSDN.
  Aby dodać pomoc w ramach skryptów, zobacz [o pomoc na podstawie komentarz](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_comment_based_help).
- Wiele modułów także dokumentacji w formacie tekstowym, takich jak pliki MarkDown.
  Może to być szczególnie przydatne w przypadku witryny projektu w usłudze Github, w którym języka znaczników Markdown jest intensywnie używanych w formacie.
  Najlepszym rozwiązaniem jest użycie [Markdown połączonego z usługą Github](https://help.github.com/categories/writing-on-github/)

Przykłady pokazują użytkowników, jak element jest przeznaczony do użycia.
Wielu deweloperów na ekranie zostanie wyświetlona informacja wyglądają na przykłady przed dokumentację, aby dowiedzieć się, jak używać języków.
Najlepszy typ przykłady Pokaż podstawowe zastosowanie oraz przypadek użycia realistyczne symulowanego i kod jest dobrze komentarzem.
Przykłady dla modułów opublikowanych w galerii programu PowerShell powinna być w folderze Przykłady w katalogu głównym modułu.

Wzorzec dobre przykłady można znaleźć w [modułu PSDscResource](https://www.powershellgallery.com/packages/PSDscResources) w folderze Examples\RegistryResource.
Istnieją cztery przykładowe przypadki użycia z krótki opis w górnej części każdego pliku dokumentuje, co jest demonstrowany.

## <a name="respond-to-feedback"></a>Odpowiadanie na opinię

Element właścicieli, którzy prawidłowo odpowiadania na opinie są bardzo cenione przez społeczności.
Użytkownicy, którzy zwyczajowo opinii są ważne, aby odpowiedzieć, jak zainteresowane w elemencie, aby pomóc ją ulepszyć.

Dostępne są dwie metody opinii w galerii programu PowerShell:

- Skontaktuj się z pomocą właściciela: Umożliwia użytkownikowi Wyślij wiadomość e-mail do właściciele elementu. Jako właściciel elementu ważne jest, aby monitorować adres e-mail używany przy użyciu elementów galerii programu PowerShell i reagowanie na problemy, które są wywoływane. Jedną wadą tej metody jest to, czy tylko użytkowników i właściciel nigdy nie zobaczą komunikacji, aby właściciel może być konieczne Odpowiedz na pytanie, tym samym wiele razy.
- Uwagi: W dolnej części strony elementu jest pole Komentarz.
  Zaletą tego systemu jest, że użytkownicy widzieli, komentarze i odpowiedzi, co zmniejsza liczbę przypadków, gdy otrzymasz odpowiedzi na każde pytanie w jednym.
  Jako właściciel elementu zdecydowanie zaleca się postępowanie zgodnie z komentarzy dla każdego elementu.
Zobacz [zapewnianie opinii za pośrednictwem mediów społecznościowych i komentarzy](../how-to/working-with-items/social-media-feedback.md) szczegółowe informacje na temat jak to zrobić.

Właściciele, którzy konstruktywnie odpowiadania na opinie są Doceniamy przez społeczność.
Użycia szansy sprzedaży w raporcie, aby uzyskać więcej informacji, jeśli to konieczne, podaj obejście tego problemu i ustalić, czy aktualizacja rozwiązuje problem.

W przypadku niewłaściwe zachowanie zaobserwowane przy użyciu dowolnego z tych kanałów komunikacyjnych funkcja Zgłoś nadużycie z galerii programu PowerShell umożliwia kontaktować z administratorami w galerii.

## <a name="modules-versus-scripts"></a>Moduły i skrypty

Udostępniania innym użytkownikom skryptu jest doskonałym i udostępniają inne przykłady sposobów do rozwiązywania problemów, które mogą mieć.
Problem polega na tym, że skrypty w galerii programu PowerShell są pojedynczych plików bez oddzielna dokumentacja, przykłady i testy.

Moduły programu PowerShell mają strukturę folderów, która zezwala na wiele folderów i plików, które będą dołączone do pakietu.
Struktura modelu umożliwia także innych elementów na listę jako najlepsze rozwiązania: polecenia cmdlet pomocy, dokumentacji, przykładów i testów.
Największych wadą jest to, że skrypt wewnątrz modułu musi być udostępniane i pełnią funkcję.
Aby uzyskać informacje na temat tworzenia modułu, zobacz [pisanie modułu programu Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=144916).

Istnieją sytuacje, w którym skrypt zapewnia lepsze środowisko użytkownika, szczególnie przy użyciu konfiguracji DSC.
Najlepszym rozwiązaniem w przypadku konfiguracji DSC jest publikowanie konfigurację jako skrypt za pomocą towarzyszący modułu, który zawiera dokumentacja, przykłady i testy.
Skrypt wyświetla towarzyszącym modułu przy użyciu RequiredModules = @(nazwa modułu).
Takie podejście może służyć w przypadku dowolnego skryptu.

Skrypty autonomicznych, które najlepsze praktyki Podaj rzeczywistą wartość do innych użytkowników.
Udostępniając oparta na komentarzach dokumentacji i link do witryny projektu jest zdecydowanie zalecane w przypadku publikowania skryptu w galerii programu PowerShell.

## <a name="provide-a-link-to-a-project-site"></a>Podaj link do witryny projektu

Witryny projektu jest, w którym wydawcy mogą wchodzić w interakcje bezpośrednio użytkownikom ich elementów galerii programu PowerShell.
Użytkownicy preferują elementy, które to zapewnić, ponieważ pozwala ono ich w celu uzyskania informacji na temat elementu, aby łatwiej.
Wiele elementów w galerii programu PowerShell są tworzone w usłudze GitHub, inne są dostarczane przez organizacje, które prowadzą dedykowanej sieci web.
Każdy z nich jest uznawana za witryny projektu.

Dodawanie łącza odbywa się przy tym ProjectURI w sekcji PSData w manifeście w następujący sposób:

        # A URL to the main website for this project.
        ProjectUri = 'https://github.com/powershell/powershell'

Gdy ProjectURI została podana, galerii programu PowerShell będzie zawierać link do witryny projektu z lewej strony elementu.

## <a name="include-tests"></a>Uwzględnić testy

W tym testy przy użyciu kodu typu open-source ważne jest, aby użytkownicy, ponieważ umożliwia ona pewności co weryfikowania i zawiera informacje o sposobie działania kodu. Umożliwia także użytkownikom upewnić się, że ich nie przerwanie własne funkcje oryginalnego mogą modyfikować kodu dopasowany ich środowiska.

Zdecydowanie zaleca się, że testy zapisywane na korzystanie z zalet usług Pester struktura testów, który został zaprojektowany specjalnie dla programu PowerShell.
Pester jest dostępna w [GitHub](https://github.com/Pester/Pester), [galerii programu PowerShell](https://www.powershellgallery.com/packages/Pester/)i jest dostarczany w systemu Windows 10, Windows Server 2016, WMF 5.0 i platformy WMF 5.1.

[Usług Pester witryny projektu w usłudze GitHub](https://github.com/Pester/Pester) obejmuje dobra dokumentacja na temat pisania testów usług Pester od wprowadzenia do najlepszych rozwiązań.

Elementy docelowe pokrycie testu są wywoływane w [dokumentacji wysokiej jakości zasobu modułu](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md), pokrycie kodu, zaleca się testu jednostki 70%.

## <a name="include-andor-link-to-license-terms"></a>Obejmują i/lub łącze do postanowień licencyjnych

Wszystkie elementy opublikowanych w galerii programu PowerShell, należy określić postanowienia licencyjne lub związanie licencjami w [warunki użytkowania](https://www.powershellgallery.com/policies/Terms) w obszarze "Załączniku A".
Najlepszym rozwiązaniem w celu określenia innej licencji jest Podaj link, aby uzyskać licencję za pomocą LicenseURI w PSData.
Przykład można znaleźć w temacie zalecane manifeście pola.

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a>Zarejestruj swój kod

Podpisywanie kodu zapewnia użytkownikom najwyższy poziom zabezpieczeń wydawca elementu, a kopię kodu zdobycia jest dokładnie wydane wydawcy.
Aby dowiedzieć się więcej na temat ogólnie podpisywania kodu, zobacz [wprowadzenie do podpisywania kodu](http://go.microsoft.com/fwlink/?LinkId=106296).
Program PowerShell obsługuje sprawdzanie poprawności podpisywania za pomocą dwóch metod podstawowego kodu:

- Podpisywanie plików skryptu
- Moduł podpisywania w katalogu

Podpisywanie plików programu PowerShell jest sprawdzone podejście do zapewnienia wykonywany kod został wyprodukowany przez wiarygodnego źródła, która nie została zmodyfikowana.
Szczegółowe informacje na temat podpisywania plików skryptów programu PowerShell są omówione w [temat podpisywania](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_signing) tematu.
W obszarze Przegląd można dodać do żadnej sygnatury. Plik PS1, który sprawdza programu PowerShell, po załadowaniu skryptu.
Może być ograniczona dla programu PowerShell przy użyciu [zasady wykonywania](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_execution_policies) poleceń cmdlet w celu zapewnienia wykorzystania podpisane skrypty.

Wykaz podpisywania modułów to funkcja, dodany do programu PowerShell w wersji 5.1.
Jak zarejestrować moduł został omówiony w [polecenia cmdlet wykazu](https://msdn.microsoft.com/powershell/wmf/5.1/catalog-cmdlets) tematu.
W obszarze Przegląd podpisywania katalogu odbywa się przez utworzenie pliku wykazu, który zawiera wartość skrótu dla każdego pliku w module, a dopiero następnie utworzenie tego pliku.
Publikowanie modułu PowerShellGet, install-module, save-module i polecenia cmdlet update-module będzie sprawdzenia podpisu w celu zapewnienia, że jest on prawidłowy, a następnie upewnij się, że jest zgodna wartość skrótu dla każdego elementu, co znajduje się w katalogu.
Jeśli poprzednią wersję modułu jest zainstalowany w systemie, install-module potwierdzi, że urząd odpowiedzialny za podpisywanie dla nowej wersji odpowiada co została wcześniej zainstalowana.
Podpisywanie katalogu współpracuje z, ale nie zastępuje podpisywania plików skryptów. Program PowerShell nie można zweryfikować sygnatur katalogu w czasie ładowania modułu.

## <a name="follow-semver-guidelines-for-versioning"></a>Postępuj zgodnie z wytycznymi SemVer pod kątem przechowywania wersji

[SemVer](http://semver.org/) jest publiczny Konwencji, która zawiera instrukcje dotyczące struktury i zmienić wersję, aby umożliwić łatwe interpretacji zmian.
Wersja dla elementu muszą być zawarte w danych manifestu.

- Wersja powinny mieć strukturę jako 3 bloki numeryczne, oddzielone kropkami, jak 0.1.1 lub 4.11.192
- Wersje, począwszy od "0" wskazują, że element nie jest jeszcze już gotowe do produkcji i pierwszy numer należy tylko zaczynają się od "0", jeśli jest to numer tylko używane
- Zmiany w pierwszy numer (1.9.9999 2.0.0) wskazują główne i istotne zmian między wersjami
- Zmiany w drugą liczbę (elementu 1.01 1,02) wskazują zmiany poziomu funkcji, takich jak dodawanie nowych poleceń cmdlet do modułu
- Zmiany numerowi trzeci wskazywać zmian niepowodujących niezgodności, takie jak nowe parametry, przykłady zaktualizowane lub nowe testy
- Podczas wyświetlania wersji, programu PowerShell pozwala na sortowanie wersje jako ciągi, więc 1.01.0 będą traktowane jako większy niż 1.001.0

Program PowerShell został utworzony przed SemVer został opublikowany, udostępnia obsługę większości, ale nie wszystkie elementy SemVer, w szczególności:

- Wstępna ciągów nie obsługuje numerów wersji. Jest to przydatne, gdy wydawca chce dostarczać wersję zapoznawczą nowej wersji głównej po podaniu wersji 1.0.0. Będzie to możliwe w przyszłej wersji poleceń cmdlet narzędzia z galerii programu PowerShell i modułu PowerShellGet.
- Program PowerShell i galerii programu PowerShell umożliwiają ciągów w wersji 1, 2 i 4 segmentów. Wiele modułów wczesne nie korzystał z wytycznymi i wersje produktu od firmy Microsoft zawierają informacje o kompilacji, ponieważ 4 blokowanie liczb (na przykład 5.1.14393.1066). Z punktu widzenia versioning te różnice są ignorowane.

## <a name="test-using-a-local-repository"></a>Testowanie przy użyciu repozytorium lokalnego

Galeria programu PowerShell nie jest przeznaczony do obiektu docelowego dla testowania proces publikowania.
Jest najlepszym sposobem przetestowania end-to-end procesu publikowania w galerii programu PowerShell do konfigurowania i używania własnego repozytorium lokalnego.
Można to zrobić na kilka sposobów, w tym:

- Skonfiguruj lokalne wystąpienie galerii programu PowerShell, za pomocą [projektu galerią prywatną PS](https://github.com/PowerShell/PSPrivateGallery) w usłudze Github. Ten projekt w wersji zapoznawczej pomoże poświęcona jest konfigurowaniu wystąpienia galerii programu PowerShell, które możesz kontrolować i używany do testów.
- Konfigurowanie [wewnętrznego repozytorium Nuget](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/). Wymaga więcej pracy do skonfigurowania, ale ma tę zaletę, sprawdzanie poprawności kilka innych wymagań, szczególnie sprawdzania poprawności korzystanie z klucza interfejsu API i czy nie zależności znajdują się w docelowym podczas publikowania.
- Konfigurowanie udziału plików jako test "repozytorium". Jest to łatwe do skonfigurowania, ale ponieważ jest udział plików, sprawdzanie poprawności przedstawionych powyżej zaczną obowiązywać. Jedną z zalet potencjalnych w tym przypadku jest, że udział plików nie sprawdza (wymagane) klucz interfejsu API, dzięki czemu można używać tego samego klucza jak publikowanie w galerii programu PowerShell.

Za pomocą dowolnego z tych rozwiązań Użyj Register-PSRepository, aby zdefiniować nowe "repozytorium", które będzie używane we właściwości - repozytorium Publish-Module.

Jeden dodatkowy punkt o publikowaniu testu: nie można usunąć dowolny element publikowanie w galerii programu PowerShell bez pomocy działu operacyjnego, która potwierdzi, że nic nie jest zależne od elementu, którą chce opublikować.
Z tego powodu firma Microsoft nie obsługują galerii programu PowerShell jako obiekt docelowy testowania i skontaktuje się z dowolnego wydawcy, który wykonuje tę funkcję.

## <a name="use-powershellget-to-publish"></a>Publikowanie przy użyciu funkcji PowerShellGet

Zdecydowanie zaleca się, że wydawcy używają poleceń cmdlet Publish-Module i Publish-Script podczas pracy z galerii programu PowerShell. Moduł PowerShellGet został utworzony, aby pomóc w uniknięciu zapamiętywanie ważne informacje dotyczące instalowania z publikowanie w galerii programu PowerShell. Czasami wydawców wybrano opuszczenia PowerShellGet i użycia klienta programu NuGet, lub polecenia cmdlet funkcji PackageManagement, zamiast Publish-Module. Istnieje szereg szczegółowe informacje, które są łatwo przeoczyć, co skutkuje szereg żądania pomocy technicznej.

W przypadku przyczyna, że nie możesz użyć Publish-Module ani Publish-Script, Daj nam znać. Prześlij zgłoszenie w repozytorium PowerShellGet GitHub i podaj szczegółowe informacje, które można wybrać NuGet lub PackageManagement spowodować. 

## <a name="recommended-workflow"></a>Zalecanym przepływie pracy

Najbardziej podejście, które znaleźliśmy dla elementów opublikowanych w galerii programu PowerShell są następujące:

- Początkowy Programowanie w lokacji projekt open source. Zespół programu PowerShell używa usługi Github.
- Użyj opinie recenzentów i [analizatora skryptu programu Powershell](https://aka.ms/psscriptanalyzer) można pobrać kodu do czasu trwania stanu stabilnego stanu
- Obejmuje dokumentacji, więc innych wie, jak korzystać pracy
- Przetestuj publikowania akcję przy użyciu repozytorium lokalnego.
- Publikowanie wersji stałe lub alfa w galerii programu PowerShell, upewniając się uwzględnić w dokumentacji i link do witryny projektu
- Zbieraj opinie i iteracji dla kodu w witrynie usługi project, a następnie opublikować stabilną aktualizacje w galerii programu PowerShell
- Dodaj przykłady oraz usług Pester testów w projekcie i modułu
- Określenie, czy kodowi zarejestrować przedmiot
- Jeśli uważasz, że projekt jest gotowa do użycia w środowisku produkcyjnym, należy opublikować 1.0.0 wersji w galerii programu PowerShell
- Przejdź do zbierania opinii i powtarzanie czynności w kodzie, w oparciu o dane wejściowe użytkownika

