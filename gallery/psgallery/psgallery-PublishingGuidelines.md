---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
description: "Wytyczne dotyczące wydawcy"
title: "Galerii programu PowerShell publikowania wskazówki i najlepsze rozwiązania"
ms.openlocfilehash: 25bbe31bcc805808c311829598e3c29991f72aad
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a>PowerShellGallery publikowania wskazówki i najlepsze rozwiązania

W tym temacie opisano kroki zalecane do wykonania używane przez zespoły firmy Microsoft w celu zapewnienia elementów opublikowany w galerii programu PowerShell powszechnie stosowane i zapewnia wysoką wartość do użytkowników, na podstawie sposobu obsługi danych manifestu w galerii programu PowerShell a opinii z dużą liczbą użytkowników galerii programu PowerShell.
Elementy, które są publikowane następujące wskazówki zostanie bardziej prawdopodobne, że można zainstalować uważany za zaufany i zwróć więcej użytkowników.

Przedstawionym poniżej przedstawiono wskazówki dotyczące co sprawia, że dobrej elementu galerii programu PowerShell, które opcjonalne ustawienia manifestu są najważniejsze, poprawy kodu za pomocą opinii recenzentów początkowej i [analizator skrypt programu Powershell](https://aka.ms/psscriptanalyzer), przechowywanie wersji z modułu, dokumentacji, testy i przykłady dotyczące używania zostały udostępnione.
Większość tej dokumentacji następuje wytyczne dotyczące publikowania [wysokiej jakości DSC zasobów modułów](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md).

Aby mechanika publikowania elementu w galerii programu PowerShell, zobacz [tworzenie i publikowanie elementu](https://msdn.microsoft.com/powershell/gallery/psgallery/creating-and-publishing-an-item).

Jest przyjęła opinię na poniższych wskazówek. Jeśli masz opinię, otwórz problemy w naszym [repozytorium Github dokumentacji](https://github.com/powershell/powershell-docs/).

## <a name="best-practices-for-publishing-items"></a>Najlepsze rozwiązania dotyczące publikowania elementów

Następujące najlepsze rozwiązania są co powiedzieć użytkowników elementy galerii programu PowerShell, ważne jest i są wymienione w kolejności priorytetu nominalnego.
Elementy, które jest zgodna z tymi wytycznymi prawdopodobnie znacznie bardziej zostanie pobrany i stosowane przez osoby trzecie.

* Użyj PSScriptAnalyzer
* Dokumentacja i przykłady
* Reagować na opinie
* Podaj modułów zamiast skryptów
* Zawierają łącza do witryny projektu
* Uwzględniania testów z własnych modułów
* Obejmują i/lub łącze do postanowień licencyjnych
* Zaloguj się w kodzie
* Postępuj zgodnie z [programu SemVer](http://semver.org/) wytyczne dotyczące kontroli wersji
* Użyj typowych tagów, zgodnie z opisem w galerii programu PowerShell typowe tagów
* Publikowanie za pomocą lokalnego repozytorium testu

Każdy z tych posiada krótko w poniższych sekcjach.

## <a name="use-psscriptanalyzer"></a>Użyj PSScriptAnalyzer

[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) jest narzędzie do analizy wolnego statycznych kod, który działa na kod programu PowerShell.
PSScriptAnalyzer określi najbardziej typowe problemy, które są widoczne w kodzie programu PowerShell i często zalecenia dotyczące sposobu rozwiązania problemu.
Narzędzie jest łatwy w użyciu i kategoryzuje problemach, jak błędy (poważny, należy się zmierzyć), ostrzeżenie (wymagają przejrzenia & powinny być kierowane) oraz informacje (warto wyewidencjonowywanie najlepsze praktyki dotyczące).
Przy użyciu PSScriptAnalyzer skanowanego elementu wszystkie elementy opublikowany w galerii programu PowerShell, a wszelkie błędy będzie zgłaszana z powrotem do właściciela i należy się zmierzyć.

Najlepszym rozwiązaniem jest uruchomienie `Invoke-ScriptAnalyzer` z `-Recurse` i `-Severity` ostrzeżenie.

Przejrzyj wyniki i upewnij się, że:

* Wszystkie błędy są poprawione lub opisany w dokumentacji
* Wszystkie ostrzeżenia sprawdzone, a problemu, jeśli to możliwe

Zdecydowanie zaleca się uruchomienie PSScriptAnalyzer i ocenić wszystkie błędy i ostrzeżenia są użytkownicy, którzy nabyli elementów z galerii programu PowerShell.
Użytkownicy są bardzo prawdopodobne, skontaktuj się z pomocą elementu właścicieli, zobaczą, że istnieje błędu zgłoszonego przez PSScriptAnalyzer.
Jeśli jest przekonujący powód dla tego elementu zachować kod, który jest oznaczony jako błąd, należy dodać te informacje do dokumentacji, aby uniknąć konieczności odpowiedzi na pytanie tego samego wiele razy.

## <a name="include-documentation-and-examples"></a>Dokumentacja i przykłady

Dokumentacja i przykłady to najlepszy sposób, aby upewnić się, że użytkownicy mogą wykorzystać udostępnionego kodu.

Dokumentacja jest najbardziej przydatny element do uwzględnienia w elementach opublikowany w galerii programu PowerShell.
Użytkownicy będą zazwyczaj pomijać elementów bez dokumentacji, jako alternatywnej odczytać kodu, aby zrozumieć element jest i jak z niego korzystać.
Kilka artykułów są dostępne w witrynie MSDN dotyczące dokumentację z elementów programu PowerShell, w tym:

* Wytyczne dotyczące zapewnianie pomocy znajdują się w [jak zapisać pomoc dotyczącą polecenia Cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415)
* Tworzenie pomocy polecenia cmdlet, które jest najlepszym rozwiązaniem dla dowolnego skryptu programu PowerShell, funkcji lub polecenia cmdlet.
  Informacje o sposobie tworzenia pomocy polecenia cmdlet, rozpoczynać się od [jak zapisać pomoc dotyczącą polecenia Cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415) w bibliotece MSDN.
  Aby dodać pomocy w skrypcie, zobacz [o komentarz na podstawie pomocy](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_comment_based_help).
* Wiele modułów również uwzględnić w dokumentacji w formacie tekstowym, takich jak pliki MarkDown.
  Może to być szczególnie przydatne w przypadku braku witryny projektu w witrynie Github, gdzie Markdown jest mocno format.
  Najlepszym rozwiązaniem jest użycie [Github języka znaczników Markdown](https://help.github.com/categories/writing-on-github/)

Przykłady przedstawiają użytkowników, jak element jest przeznaczona do użycia.
Wielu deweloperów dowiesz się wyglądają na przykłady przed dokumentacji, aby zrozumieć, jak używać elementu.
Najlepszy typ przykłady Pokaż podstawowe wykorzystanie oraz przypadek użycia realistyczne symulowane i kod jest dobrze komentarze.
Przykłady dla modułów opublikowany w galerii programu PowerShell powinna być w folderze Przykłady w katalogu głównym modułu.

Wzorzec dobre przykłady można znaleźć w [modułu PSDscResource](https://www.powershellgallery.com/packages/PSDscResources) w folderze Examples\RegistryResource.
Istnieją cztery przykładowe przypadki użycia krótki opis u góry każdego pliku tego dokumenty, co przedstawionej.

## <a name="respond-to-feedback"></a>Odpowiedzi na opinie

Element właścicieli, którzy prawidłowo uwzględniał opinie użytkowników są wysokiej wartości przez społeczność.
Użytkowników, którzy wyrazić swoją opinię zwyczajowo są należy odpowiedzieć, ponieważ są one zainteresowane w elemencie, aby spróbować go poprawić.

Dostępne są dwie metody opinii w galerii programu PowerShell:

* Skontaktuj się z pomocą właściciel: Umożliwia użytkownikowi wysłanie wiadomości e-mail do jego właściciela elementu. Jako właściciel elementu ważne jest, aby monitorować adres e-mail używany z elementów galerii programu PowerShell i reagowanie na problemy, które są wywoływane. Niedogodność do tej metody jest to, czy tylko użytkowników i właściciel kiedykolwiek zobaczą komunikacji, więc właściciela może być konieczne odpowiedzi na pytanie tego samego wiele razy.
* Uwagi: W dolnej części strony elementu jest polem komentarza.
  Korzyści z tym systemem to, czy inni użytkownicy widzą komentarze i odpowiedzi, co zmniejsza liczbę razy, które należy odpowiedzieć na każde pytanie pojedynczego.
  Jako właściciel elementu zdecydowanie zaleca się przestrzeganie uwag dla każdego elementu.
Zobacz [dostarczanie opinię za pośrednictwem mediów społecznościowych i komentarze](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-SocialMediaFeedback) szczegółowe informacje o tym, jak to zrobić.

Właścicieli, którzy konstruktywnie uwzględniał opinie użytkowników są docenia przez społeczność.
Użyj możliwość w raporcie, aby uzyskać więcej informacji, jeśli to konieczne, podaj obejście tego problemu, lub ustalić, czy aktualizacja rozwiązuje problem.

W przypadku niewłaściwe zachowanie obserwowanych przy użyciu dowolnego z tych kanałów komunikacji, funkcja zgłaszania nadużyć z galerii programu PowerShell do kontaktowania się z administratorami w galerii.

## <a name="modules-versus-scripts"></a>Moduły i skryptów

Skrypt do udostępniania innym użytkownikom stanowi doskonałe rozwiązanie i udostępnia inne przykłady sposobu rozwiązywania problemów, które mogą mieć.
Problem polega na tym, czy pojedynczych plików bez testy oddzielna dokumentacja i przykłady skryptów w galerii programu PowerShell.

Moduły programu PowerShell mają strukturę folderów, umożliwiającą wielu folderów i plików do uwzględnienia w pakiecie.
Struktura modułu umożliwia tym inne elementy na listę jako najlepsze rozwiązania w zakresie: polecenia cmdlet pomocy, dokumentację, przykłady i testy.
Największych wadą jest to, że skryptu wewnątrz modułu musi być udostępniane i jako funkcji.
Aby uzyskać informacje na temat tworzenia modułu, zobacz [pisanie modułu programu Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=144916).

Istnieją sytuacje, w którym skrypt zapewnia lepsze środowisko dla użytkowników, szczególnie w przypadku konfiguracji DSC.
Najlepszym rozwiązaniem w przypadku konfiguracji DSC jest publikowanie konfiguracji jako skryptu z towarzyszącym moduł, który zawiera dokumenty, przykłady i testy.
Skrypt zawiera towarzyszący modułu przy użyciu RequiredModules = @(nazwa modułu).
Takie podejście można używać w przypadku dowolnego skryptu.

Autonomiczny skrypty, które należy stosować najlepsze rozwiązania Podaj rzeczywistą wartość dla innych użytkowników.
Jeśli oparta na komentarzach dokumentacji i łącze do witryny projektu są zdecydowanie zalecany podczas publikowania skryptu w galerii programu PowerShell.

## <a name="provide-a-link-to-a-project-site"></a>Podaj łącze do witryny projektu

Witryny projektu jest, gdzie wydawcy można bezpośrednią interakcję z użytkownikami ich elementów galerii programu PowerShell.
Użytkownicy preferowane elementów, które zapewniają, ponieważ pozwala uzyskać informacje o elemencie łatwiej.
Wiele elementów w galerii programu PowerShell są tworzone w usłudze GitHub, inne są dostarczane przez organizacje obecności dedykowanych sieci web.
Każdy z nich mogą zostać uwzględnione witryny projektu.

Dodanie łącz odbywa się przy tym ProjectURI w sekcji PSData manifestu w następujący sposób:

        # A URL to the main website for this project.
        ProjectUri = 'https://github.com/powershell/powershell'

Gdy ProjectURI jest podana w galerii programu PowerShell zawiera łącze do witryny projektu w lewej części strony elementu.

## <a name="include-tests"></a>Uwzględniania testów

W tym testy z kodem źródłowym Otwórz ważne jest, aby użytkownicy, zgodnie z ich udostępnia pewności co weryfikowania i zawiera informacje dotyczące sposobu działania kodu. Umożliwia także użytkownikom upewnij się, że nie awarie z oryginalnego funkcji ich zmodyfikowania swój kod, aby zmieścić ją w swoim środowisku.

Zdecydowanie zaleca się, że testy można zapisywać na korzystanie z platformy testu Pester, który został zaprojektowany specjalnie z myślą o programu PowerShell.
Pester jest dostępna w [GitHub](https://github.com/Pester/Pester), [galerii programu PowerShell](https://www.powershellgallery.com/packages/Pester/)i jest dostarczany w systemu Windows 10, Windows Server 2016 i WMF 5.0, WMF 5.1.

[Pester witryny projektu w serwisie GitHub](https://github.com/Pester/Pester) zawiera wyczerpujące na zapisywanie testy Pester z wprowadzenie do najlepszych rozwiązań.

Docelowe pokrycie testu są wywoływane [dokumentacji wysokiej jakości zasób modułu](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md), z jednostką 70% test zalecane pokrycia kodu.

## <a name="include-andor-link-to-license-terms"></a>Obejmują i/lub łącze do postanowień licencyjnych

Wszystkie elementy opublikowany w galerii programu PowerShell należy określić postanowienia licencyjne lub związanie licencji objęte [warunki użytkowania](https://www.powershellgallery.com/policies/Terms) w obszarze "Zawiera A".
Najlepszym rozwiązaniem do określenia innej licencji jest zapewnienie łącze do licencji za pomocą LicenseURI w PSData.
Przykład można znaleźć w temacie zalecane pola manifestu.

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a>Zaloguj się w kodzie

Podpisywanie kodu zapewnia użytkownikom najwyższy poziom gwarancji dla wydawca elementu, a kopia kodu zdobycia jest dokładnie wydane wydawcy.
Aby dowiedzieć się więcej na temat zazwyczaj podpisywania kodu, zobacz [wprowadzenie do podpisywania kodu](http://go.microsoft.com/fwlink/?LinkId=106296).
PowerShell obsługuje sprawdzanie poprawności kodu podpisywania przez dwa podejścia głównej:

* Podpisywanie plików skryptu
* Moduł podpisywania katalogu

Podpisywanie plików programu PowerShell jest ustalonym podejście do zapewnienia wykonywany kod wygenerowany za pomocą wiarygodnego źródła, a nie został zmodyfikowany.
Więcej informacji na temat podpisywania plików skryptu programu PowerShell jest objęte [o podpisywania](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_signing) tematu.
W obszarze Przegląd można dodać do dowolnego podpisu. Plik PS1 PowerShell weryfikuje po załadowaniu skryptu.
PowerShell można ograniczyć przy użyciu [zasady wykonywania](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_execution_policies) poleceń cmdlet w celu zapewnienia wykorzystania podpisany skryptów.

Podpisywanie modułów katalogu jest funkcją dodany do programu PowerShell w wersji 5.1.
Jak podpisać moduł jest objęte [poleceń cmdlet katalogu](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/catalog-cmdlets) tematu.
W obszarze Przegląd katalogu podpisywania odbywa się tworzenie pliku wykazu, który zawiera wartość skrótu dla każdego pliku w module, a następnie podpisywania tego pliku.
Publikowanie modułu PowerShellGet, Zainstaluj moduł, moduł zapisywania i polecenia cmdlet modułu aktualizacji zostanie sprawdzenia podpisu, aby upewnić się, że jest prawidłowy, a następnie upewnij się, że wartość skrótu dla każdego elementu odpowiada elementom w katalogu.
Jeśli poprzednia wersja modułu jest zainstalowana w systemie, Zainstaluj moduł potwierdzić, czy urząd podpisywania dla nowej wersji jest zgodny z wcześniej zainstalowano co.
Podpisywanie katalogu współpracuje z, ale nie zastępuje podpisywania plików skryptów. PowerShell nie można zweryfikować sygnatur katalogu w czasie ładowania modułu.

## <a name="follow-semver-guidelines-for-versioning"></a>Postępuj zgodnie z wytycznymi programu SemVer dla wersji

[Programu SemVer](http://semver.org/) Konwencji publicznego, który opisuje sposób struktury i Zmień wersję, aby umożliwić łatwe interpretacji zmian.
Wersja dla tego elementu muszą być zawarte w danych manifestu.

* Wersja ma być struktura jako 3 bloki liczbowego, oddzielone kropkami, jak 0.1.1 lub 4.11.192
* Wersje, począwszy od "0" oznaczają, że element nie jest jeszcze gotowy produkcyjnego oraz numer pierwszej tylko powinny rozpoczynać się od "0", jeżeli jest to numer tylko używane
* Zmiany w pierwszy numer (1.9.9999 2.0.0) wskazują główne i fundamentalne zmiany między wersjami
* Zmiany druga liczba (elementu 1.01 1,02) wskazuje poziom funkcji zmiany, takie jak dodawanie nowych poleceń cmdlet do modułu
* Zmiany liczby trzeci wskazywać nierozdzielające zmiany, takie jak nowe parametry, przykłady zaktualizowane lub nowych testów
* Podczas wyświetlania wersji, programu PowerShell sortowania wersje jako ciągi, więc 1.01.0 będą traktowane jako większa niż 1.001.0

PowerShell został utworzony przed programu SemVer został opublikowany, zapewnia obsługę większości, ale nie wszystkie elementy programu SemVer, w szczególności:

* Wstępna ciągów nie obsługuje numerów wersji. Jest to przydatne, gdy wydawca chce dostarczyć wersję zapoznawczą nowej wersji głównej po podaniu wersja 1.0.0. Będą to obsługiwane w przyszłym wydaniu poleceń cmdlet programu PowerShell galerii i PowerShellGet.
* Środowiska PowerShell i galerii programu PowerShell umożliwiają ciągów w wersji 1, 2 i 4 segmentów. Wiele modułów wczesne nie postępuj zgodnie z wytycznymi, oraz wersje produktu od firmy Microsoft informacje kompilacji jako 4 zablokować liczb (na przykład 5.1.14393.1066). Z punktu widzenia versioning te różnice są ignorowane.

## <a name="test-using-a-local-repository"></a>Testowanie przy użyciu lokalnego repozytorium

Galerii programu PowerShell nie została zaprojektowana jako element docelowy do testowania proces publikowania.
Jest najlepszy sposób, aby przetestować end-to-end proces publikowania w galerii programu PowerShell do konfigurowania i używania lokalnym repozytorium.
Można to zrobić na kilka sposobów, w tym:

* Konfigurowanie lokalnego wystąpienia galerii programu PowerShell, za pomocą [projektu galerii prywatnego PS](https://github.com/PowerShell/PSPrivateGallery) w witrynie Github. Ten projekt w wersji zapoznawczej pomoże Ci skonfigurować wystąpienie galerii programu PowerShell, który można kontrolować i używany do testów.
* Konfigurowanie [wewnętrzny repozytorium Nuget](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/). Wymaga więcej pracy, aby skonfigurować, ale będzie miał zaletą sprawdzanie poprawności kilka innych wymagań, szczególnie sprawdzanie poprawności klucza interfejsu API oraz czy zależności są obecne w miejscu docelowym podczas publikowania.
* Konfigurowanie udziału plików jako test "repository". Jest to łatwa do skonfigurowania, ale ponieważ jest udział plików, sprawdzaniu poprawności opisanymi powyżej nie będą wykonywane. Jedną z zalet potencjalnych w tym przypadku jest, że udziału plików nie sprawdza klucz interfejsu API (wymagane), więc można używać tego samego klucza jak do publikowania w galerii programu PowerShell.

Za pomocą dowolnego z tych rozwiązań umożliwia definiowanie nowych "repository", używanego we właściwości — repozytorium dla modułu publikowania PSRepository rejestru.

Jeden dodatkowy punkt o publikowaniu testu: nie można usunąć dowolny element publikowania w galerii programu PowerShell bez pomocy od zespołu operacji, która potwierdzi, że nic nie jest zależny od elementu chcesz opublikować.
Z tego powodu firma Microsoft nie obsługują galerii programu PowerShell jako cel testowania i skontaktuje się z dowolnego wydawcę, który wykonuje.

## <a name="recommended-workflow"></a>Zalecane przepływu pracy

Najbardziej popularnych podejście, które znaleziono dla elementów opublikowany w galerii programu PowerShell są następujące:

* Początkowa Programowanie w lokacji projekt open source. Zespół programu PowerShell używa usługi Github.
* Użyj informacje i opinie od osób dokonujących przeglądu i [analizator skrypt programu Powershell](https://aka.ms/psscriptanalyzer) można pobrać kodu do stabilnego stanu
* Dołączać dokumentację, aby inne osoby wiedzieć, jak służbowy
* Przetestuj publikowania akcji przy użyciu lokalnego repozytorium.
* Publikowanie wersji stabilnej lub alfa w galerii programu PowerShell, upewniając się uwzględnić w dokumentacji i łącze do witryny projektu
* Zbieranie opinii i iteracji kod w witrynie projektu, a następnie publikowanie stabilna aktualizacji w galerii programu PowerShell
* Dodaj przykłady i Pester testów w projekcie i modułu
* Zdecyduj, czy chcesz oznaczyć podpisania tego elementu
* Jeśli uważasz, że projekt jest gotowy do użycia w środowisku produkcyjnym, publikować 1.0.0 wersji w galerii programu PowerShell
* Nadal zbieranie opinii i przejść na kodzie oparte na dane wejściowe użytkownika
