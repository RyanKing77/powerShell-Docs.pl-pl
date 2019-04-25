---
ms.date: 08/23/2017
keywords: polecenia cmdlet programu PowerShell
title: za pomocą konsoli programu powershell systemu windows oparte na sieci web
ms.openlocfilehash: 2bb9c6ef486ef32012a15f9890997cf2fa6a3a0b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086647"
---
# <a name="use-the-web-based-windows-powershell-console"></a>Za pomocą konsoli programu PowerShell Windows opartej na sieci Web

Zaktualizowano: 24 czerwca 2013 r.

Dotyczy: Windows Server 2012 R2, Windows Server 2012

Windows PowerShell Web Access umożliwia użytkownikom na logowanie z zabezpieczoną witryną sieci Web; Aby można było używać sesji, poleceń cmdlet i skryptów programu Windows PowerShell do zarządzania komputerem zdalnym.

Ponieważ konsolę programu Windows PowerShell działa w przeglądarce sieci web, można je otworzyć z wielu różnych urządzeniach klienckich; prawie wszystkie urządzenia z przeglądarką sieci web działa.

Konsoli internetowej programu Windows PowerShell jest wskazywane na komputerze zdalnym, który jest określony przez użytkowników w ramach procesu logowania.

W tym temacie opisano sposób logowanie się i rozpocząć korzystanie z konsoli internetowej programu Windows PowerShell Web Access.

W tym temacie nie opisano sposobu używania programu Windows PowerShell i uruchamiania poleceń cmdlet i skryptów.
Aby uzyskać informacje o sposobie używania programu Windows PowerShell i skryptów zasobów, zobacz [Zobacz też](#see-also) sekcji na końcu tego tematu.

## <a name="supported-browsers-and-client-devices"></a>Obsługiwane przeglądarki i urządzenia klienckie

Windows PowerShell Web Access obsługuje następujące przeglądarki internetowe.
Choć przeglądarki dla urządzeń przenośnych oficjalnie nie są obsługiwane, wiele można uruchomić konsoli internetowej programu Windows PowerShell.
Inne przeglądarki, które akceptują pliki cookie, obsługują skrypty języka JavaScript oraz witryny HTTPS oczekuje się pracy, ale to nie jest oficjalnie przetestowane.

### <a name="supported-desktop-computer-browsers"></a>Obsługiwane przeglądarki na komputery stacjonarne

- Windows Internet Explorer dla programu Microsoft Windows 8.0, 9.0, 10.0 i 11.0
- Mozilla Firefox 10.0.2
- Google Chrome 17.0.963.56m dla Windows
- Apple Safari 5.1.2 dla Windows
- Apple Safari 5.1.2 dla komputerów Mac OS

### <a name="minimally-tested-mobile-devices-or-browsers"></a>Minimalnie przetestowane urządzenia przenośne lub przeglądarki

- Windows Phone 7 i 7.5
- System Google Android WebKit 3.1 dla systemu Android 2.2.1 (jądro 2.6)
- Apple Safari dla iPhone systemu operacyjnego 5.0.1
- Apple Safari dla tabletu iPad 2 systemu operacyjnego 5.0.1

### <a name="browser-requirements"></a>Wymagania dotyczące przeglądarki

Aby korzystać z konsoli internetowej programu Windows PowerShell Web Access, przeglądarki muszą spełniać następujące czynności.

- Zezwalaj na pliki cookie z witryny sieci Web bramy dla programu Windows PowerShell Web Access.
- Można otworzyć i Odczyt stron protokołu HTTPS.
- Otwórz i uruchom witryn sieci Web, który jest używany język JavaScript.

## <a name="signing-in-to-windows-powershell-web-access"></a>Logowanie do programu Windows PowerShell Web Access

Administrator programu Windows PowerShell Web Access powinien podać adres URL, który jest adresem bramy systemu Windows PowerShell Web Access organizacje witryny sieci Web.
Domyślnie jest to adres witryny internetowej *https://\<nazwa_serwera\>/pswa*.

Zanim zalogujesz się do programu Windows PowerShell Web Access można się, że nazwa lub adres IP komputera zdalnego, którym chcesz zarządzać.
Musisz być autoryzowanym użytkownikiem na komputerze zdalnym, a musi być skonfigurowany w celu umożliwienia zarządzania zdalnego.
Aby uzyskać więcej informacji na temat konfigurowania komputera w celu umożliwienia zarządzania zdalnego, zobacz [Włączanie i używanie poleceń zdalnych w programie Windows PowerShell](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting).

Najprostszą metodą konfiguracji komputera w celu umożliwienia zarządzania zdalnego jest uruchomienie **Enable-PSRemoting - force** polecenia cmdlet na komputerze, w sesji środowiska Windows PowerShell, która została otwarta z podwyższonym poziomem uprawnień użytkownika (**Uruchom jako Administrator**).

### <a name="to-sign-in-to-windows-powershell-web-access"></a>Aby zarejestrować się w programie Windows PowerShell Web Access

1. Otwórz witrynę sieci Web programu Windows PowerShell Web Access w oknie przeglądarki internetowej lub na karcie.

1. W witrynie programu Windows PowerShell Web Access logowania Podaj swoją nazwę użytkownika w sieci, hasło i nazwę komputera, na którym chcesz zarządzać (i na którym jesteś autoryzowanym użytkownikiem). Jeśli administrator programu Windows PowerShell Web Access zalecił używanie identyfikatora URI do witryny niestandardowej lub serwera proxy zamiast nazwy komputera, wybierz opcję **identyfikator URI połączenia** w **typu połączenia** pola, a następnie Podaj identyfikator URI.

    > ![Uwaga](images/Note.jpeg) **Uwaga**:
    >
    > - Jeśli komputer docelowy znajduje się w grupie roboczej, użyj następującej składni, aby podać nazwę użytkownika i zalogować się do komputera: `<workgroup_name>\<user_name>`
    > - Jeśli komputer docelowy jest serwerem bramy, możesz określić `localhost` w polu nazwy komputera
    > - Jeśli komputer docelowy jest serwerem bramy, a serwer bramy znajduje się w grupie roboczej, należy użyć `<workgroup name>\<user_name>` w nazwie użytkownika zgłoszone. Możesz użyć `localhost` w polu nazwy komputera.

1. **Opcjonalne ustawienia połączenia** sekcja odnosi się do wymagań autoryzacji komputera zdalnego, którym chcesz zarządzać. Aby uzyskać więcej informacji na temat parametrów, które są równoważne opcjonalnym ustawieniom połączenia, zobacz [Enter-PSSession](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession) pomocy dotyczącej poleceń cmdlet.

    Zazwyczaj poświadczeń, których używasz do przechodzą przez tę bramę programu Windows PowerShell Web Access jest taki sam, które są rozpoznawane przez komputer zdalny, którą chcesz zarządzać. Jeśli chcesz używać innych poświadczeń do zarządzania komputerem zdalnym określoną w kroku 2, rozwiń węzeł **opcjonalne ustawienia połączenia** sekcji i podanie alternatywnych poświadczeń. W przeciwnym razie przejdź do kroku 6.

1. Jeśli administrator programu Windows PowerShell Web Access utworzył niestandardową konfigurację sesji dla użytkowników programu Windows PowerShell Web Access, wpisz nazwę konfiguracji sesji w **Nazwa konfiguracji** pola. Aby uzyskać więcej informacji na temat konfiguracji sesji, zobacz [informacje o konfiguracjach sesji](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations).

1. Zachowaj **typ uwierzytelniania** równa **domyślne** , chyba że użytkownik zalecił robić przez administratora programu Windows PowerShell Web Access.

1. Kliknij przycisk **Zaloguj**.

## <a name="signing-out-and-timing-out"></a>Wylogowywanie i limit czasu

Dowolne z następujących czynności i sytuacji powoduje wylogowanie z sesji środowiska Windows PowerShell opartego na sieci web.

- Klikając **Wyloguj** w prawym dolnym rogu konsoli. (Dotyczy tylko systemu Windows Server 2012)

- Klikając **Zapisz** lub **zakończenia** w prawym dolnym rogu konsoli (tylko w systemie Windows Server 2012 R2). Klikając **Zapisz** powoduje zapisanie i zamknięcie sesji programu Windows PowerShell Web Access; można ponownie połączyć z sesją później. Po zalogowaniu do programu Windows PowerShell Web Access ponownie, programu Windows PowerShell Web Access wyświetla listę zapisanych sesji można albo wybierz i ponownie połączyć się z zapisanych sesji lub Rozpocznij nową sesję. Maksymalna liczba otwartych sesji, które użytkownicy mogą, zarówno zapisanych, jak i aktywnych, jest skonfigurowany przez administratora bramy.

    Klikając **zakończenia** i sytuacji powoduje wylogowanie sesji programu Windows PowerShell Web Access nie został zapisany.

- Podjęto próbę Zaloguj się do zarządzania innym komputerem zdalnym w tej samej sesji przeglądarki lub na nowej karcie tej samej sesji przeglądarki. (Nie dotyczy Jeśli serwer bramy działa system Windows Server 2012 R2 Windows PowerShell Web Access uruchomiona w systemie Windows Server 2012 R2 zezwala na wiele sesji użytkownika na nowych kartach w tej samej sesji przeglądarki.) Aby uzyskać więcej informacji o sposobie używania więcej niż jednej aktywnej sesji na tym samym komputerze, zobacz łączenie z wieloma komputerami docelowymi jednocześnie w [ograniczenia konsoli internetowej](#limitations-of-the-web-based-console) części tego tematu.

- 20 minut bezczynności sesji. Administrator bramy może dostosować limit czasu bezczynności Aby uzyskać więcej informacji, zobacz [Zarządzanie sesjami](authorization-rules-and-security-features-of-windows-powershell-web-access.md#session-management).

    - Jeśli w przypadku rozłączenia z sesją w konsoli sieci web ze względu na błąd sieciowy lub innego nieplanowanego zamknięcia lub awarii, a nie zamknięcia sesji przez samodzielnie, Windows PowerShell Web Access sesji kontynuuje działanie, połączone z docelowymi komputer, do momentu przed upłynięciem limitu czasu na wygaśnie po stronie klienta. Domyślnie ten limit czasu wynosi 20 minut, a jest skonfigurowany przez administratora bramy. Sesja zostaje rozłączona po upływie domyślne 20 minut lub po upływie limitu czasu określonego przez administratora bramy, która kwota jest krótszy.

        Jeśli serwer bramy działa system Windows Server 2012 R2, Windows PowerShell Web Access umożliwia użytkownikom ponowne łączenie się z zapisanymi sesjami w późniejszym czasie, ale nie można wyświetlić lub ponownie połączyć się z zapisanych sesji do czasu po upływie limitu czasu określonego przez bramę administratora wygasły.

- Zamknięcie okna lub karty przeglądarki.

- Wyłączenie urządzenia klienckiego, na którym przeglądarki jest uruchomiona lub rozłączenie jej z sieci.

- Uruchamianie **zakończenia** polecenia w konsoli sieci web. To polecenie nie działa, jeśli konfiguracji sesji, z którą masz połączenie jest skonfigurowany do obsługi [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) trybu, lub znajduje się w ograniczonym obszarem działania.

Jeśli chcesz zalogować się ponownie, ponownie otwórz stronę sieci web programu Windows PowerShell Web Access i zaloguj się, wykonując kroki opisane w [logowanie do programu Windows PowerShell Web Access](#signing-in-to-windows-powershell-web-access) w tym temacie.

## <a name="differences-in-the-web-based-windows-powershell-console"></a>Różnice w konsoli internetowej programu Windows PowerShell

Po zalogowaniu się do programu Windows PowerShell Web Access, konsoli internetowej programu Windows PowerShell zostanie otwarta w przeglądarce lub na karcie. Ponieważ konsola jest połączona z komputerem zdalnym, który określiłeś w procesie logowania, tylko te polecenia cmdlet programu Windows PowerShell lub skryptów, które są dostępne na komputerze zdalnym może służyć w konsoli. W tej sekcji opisano inne ograniczenia konsoli programu Windows PowerShell Web Access i różnice między konsolami programu Windows PowerShell Web Access i zainstalowaną **PowerShell.exe** konsoli.

### <a name="functional-disparity-with-powershellexe"></a>Różnice funkcjonalne przy użyciu PowerShell.exe

Większość funkcji hosta programu Windows PowerShell jest dostępny w konsoli internetowej programu Windows PowerShell Web Access, ale niektóre funkcje, które nie są dostępne.

- Wyświetla postęp zagnieżdżonych.

  Windows PowerShell Web Access wyświetla graficzny interfejs użytkownika postępu dla poleceń cmdlet tego raportować postęp, ale jest wyświetlany tylko informacje o postępie najwyższego poziomu.

- Zmiana koloru okna wprowadzania.

  Nie można zmienić koloru okna wprowadzania (pierwszego planu i tła). Styl danych wyjściowych, ostrzeżeń, trybu pełnego i komunikaty o błędach można zmienić, uruchamiając skrypt.

- PSHostRawUserInterface.

  Windows PowerShell Web Access jest implementowany przez zarządzanie zdalne programu Windows PowerShell, a następnie używa zdalnego obszaru działania. Windows PowerShell Web Access nie implementuje niektórych metod, w tym interfejsie; na przykład poleceń, które zapisują do konsoli Windows. Polecenia, takie jak **PowerTab** nie działają w programie Windows PowerShell Web Access.

- Klawisze funkcyjne.

  Windows PowerShell Web Access nie obsługuje niektórych klawiszy funkcyjnych, w wielu przypadkach, ponieważ polecenia są zarezerwowane przez przeglądarkę.

### <a name="unsupported-shortcut-keys"></a>Klawisze skrótów nieobsługiwany

Klucz funkcji | Akcja
-- | --
Ctrl+C | W programie Windows PowerShell Web Access **klawisze Ctrl + C** jest używany przez przeglądarkę do kopiowania zawartości. W konsoli **anulować** przycisk, a użytkownicy mogą również użyć **Ctrl + Q** do anulowania poleceń.
ALT + SPACJA, e, l | Przewijanie buforu ekranu
ALT + SPACJA, e, f | Wyszukiwanie tekstu w buforze ekranu
ALT + SPACJA, e, k | Zaznaczenie tekstu do skopiowania z buforu ekranu
ALT + SPACJA, e, p | Wklej zawartość Schowka do konsoli środowiska Windows PowerShell
ALT + SPACJA, c | Zamknij konsolę programu Windows PowerShell
Ctrl+Break | Wymuszenie zamknięcia okna programu Windows PowerShell
Ctrl+Home | Usuwa od początku bieżącego wiersza polecenia
Ctrl+End | Usuwa do końca wiersza polecenia
F1 | Przesuń kursor o jeden znak w prawo w wierszu polecenia
F2 | Utworzenie nowego polecenia przez skopiowanie ostatniego polecenia aż wpisany znak
F3 | Zakończenie wiersza polecenia zawartością z ostatniego wiersza polecenia
F4 | Usunięcie znaków od pozycji kursora
F5 | Przeszukiwanie się, dlaczego historii poleceń. Aby uzyskać dostęp do poleceń w historii poleceń programu Windows PowerShell Web Access, kliknij przycisk **historii** przewiń przyciski w konsoli sieci web.
F7 | Interaktywne Wybieranie polecenia z historii poleceń
F8 | Przeszukanie historii i wyświetlenie poleceń zgodnych z bieżącym tekstem
F9 | Uruchomienie konkretnego numeru polecenia z historii
Page Up | Uruchomienie pierwszego polecenia w historii
Page Down | Uruchomienie ostatniego polecenia w historii
Alt+F7 | Wyczyszczenie listy historii poleceń

### <a name="limitations-of-the-web-based-console"></a>Ograniczenia związane z konsolą sieci web

- Podwójny przeskok

    Mogą wystąpić przeskokami (lub połączenia z drugim komputerem z pierwszego połączenia) ograniczenie, jeśli zostanie podjęta próba utworzenia lub pracy w nowej sesji przy użyciu programu Windows PowerShell Web Access. Windows PowerShell Web Access używa zdalnego obszaru działania, a obecnie program **PowerShell.exe** nie obsługuje połączenia zdalnego z drugim komputerem ze zdalnego obszaru działania. Jeśli spróbujesz połączyć się z drugim komputerem zdalnym z istniejącego połączenia przy użyciu **Enter-PSSession** polecenia cmdlet, na przykład uzyskasz różne błędy, takie jak €œCannot pobrać zasobów sieciowych.

    Aby uniknąć błędów podwójny przeskok, administrator powinien skonfigurować uwierzytelnianie CredSSP w danym środowisku sieciowym organizacji. Aby uzyskać więcej informacji na temat konfigurowania uwierzytelniania CredSSP, zobacz [protokół CredSSP na potrzeby komunikacji zdalnej drugiego przeskoku](https://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) w witrynie internetowej firmy Microsoft. Można też podać jawne poświadczenia, jeśli chcesz zarządzać drugim komputerem zdalnym; niejawne poświadczenia są raczej nie pozwalają na drugi przeskok.

- Komunikacja zdalna

    Windows PowerShell Web Access używa i ma te same ograniczenia co sesji zdalnej programu Windows PowerShell. Polecenia wywołujące bezpośrednio konsoli Windows interfejsów API, takich jak edytory oparte na konsoli lub programy z menu tekstowym, nie działają, ponieważ polecenia nie odczytu lub zapisu do standardowych potoków danych wejściowych, wyjściowych i błędów. W związku z tym, które uruchamiają plik wykonywalny pliku poleceń, takich jak **notepad.exe**, lub Wyświetla graficzny interfejs użytkownika, takie jak `OpenGridView` lub `ogv`, nie będą działać. Środowisko jest zależna od zachowania; wygląda na to nie odpowiada na polecenia programu Windows PowerShell Web Access.

- Uzupełnianie po naciśnięciu tabulatora

    Uzupełnianie po naciśnięciu tabulatora nie działa w konfiguracji sesji z ograniczonym obszarem działania lub w **NoLanguage** trybu. Chociaż Administratorzy mogą skonfigurować sesję do obsługi uzupełniania po naciśnięciu tabulatora, jest to odradzane ze względów bezpieczeństwa, ponieważ może uwidaczniać następujące informacje dla nieautoryzowanych użytkowników.

    - Ścieżki wewnętrznego systemu plików

    - Foldery udostępnione na komputerach wewnętrznych

    - Zmienne w obszarze działania

    - Załadowane typy or.NET Framework przestrzenie nazw

    - Zmienne środowiskowe

- **NoLanguage** sesji lub ograniczonym obszarem działania

    Użytkownicy, którzy są zalogowani na **NoLanguage** nie można uruchomić konfigurację sesji lub z ograniczonym obszarem działania w programie Windows PowerShell Web Access **zakończenia** polecenie, aby zakończyć sesję. Aby się wylogować, użytkownik powinien kliknąć pozycję **Wyloguj** na stronie konsoli.

- Połączenie z wieloma komputerami docelowymi jednocześnie.

    Jeśli serwer bramy działa system Windows Server 2012, Windows PowerShell Web Access umożliwia tylko jedno połączenie komputerem zdalnym na sesję przeglądarki. go nie zezwala użytkownikom na raz, a potem połączyć z wieloma komputerami zdalnymi przy użyciu osobnych kartach przeglądarki. Po otwarciu nowej karty lub nowe okno przeglądarki, programu Windows PowerShell Web Access monituje o rozłączenie bieżącej sesji i rozpocznij nową sesję, tak, aby nawiązać nowe (lub tym samym) komputerem zdalnym. Jeśli to konieczne są co najmniej dwa osobne sesje w przypadku różnych komputerów zdalnych, jednak funkcja w programie Internet Explorer umożliwia utworzenie nowej sesji. Aby rozpocząć nową sesję w programie Internet Explorer, naciśnij **ALT**, otwórz **pliku** menu, a następnie wybierz pozycję **nowej sesji**. Następnie otwórz witrynę sieci Web programu Windows PowerShell Web Access w nowej sesji i zaloguj się do komputera zdalnego dostępu.

    Gdy brama programu Windows PowerShell Web Access jest uruchomiona w systemie Windows Server 2012 R2, użytkownicy mogą otwierać wiele połączeń z komputerami zdalnymi na różnych kartach przeglądarki. Jeśli chcesz otworzyć więcej niż jedno połączenie z komputerem zdalnym za pomocą konsoli internetowej programu Windows PowerShell, skontaktuj się z administratorem bramy programu Windows PowerShell Web Access, aby sprawdzić, czy ta funkcja jest obsługiwana przez serwer bramy.

- Trwałe sesje programu Windows PowerShell (ponowne połączenie).

    Po użytkownik limit czasu bramy programu Windows PowerShell Web Access połączenie zdalne między bramą i komputerem docelowym jest zamknięty. Spowoduje to zatrzymanie żadnych poleceń cmdlet i skryptów, znajdujące się obecnie w toku. Zachęcamy do korzystania z programu Windows PowerShell **— zadanie** infrastruktury w przypadku wykonywania długotrwałych zadań, tak że można uruchomić zadania, odłącz od komputera, późniejsze ponowne połączenie i być utrwalonymi zadaniami. Inną zaletą używania **— zadanie** polecenia cmdlet jest, że można je uruchomić za pomocą programu Windows PowerShell Web Access, wyloguj się i później ponownego połączenia, uruchomione Windows PowerShell Web Access lub innego hosta (np. programu Windows PowerShell Integrated Scripting Environment (ISE)).

- Zmiana rozmiaru konsoli.

    **PowerShell.exe** okna konsoli można zmienić na następujące trzy sposoby.

    - Przeciągnięcie i dostosowanie rozmiaru okna konsoli za pomocą myszy

    - Zmień właściwości wysokości i szerokości przy użyciu graficznego interfejsu użytkownika właściwości konsoli

    - Zmiana wysokości i szerokości okien konsoli systemu za pośrednictwem polecenia cmdlet

        Okno konsoli programu Windows PowerShell Web Access można skonfigurować za pomocą poleceń cmdlet w następujący sposób. W poniższym przykładzie użytkownik zmienia szerokość konsoli programu Windows PowerShell Web Access, aby **20**.

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        W podobny sposób można zmienić wysokość konsoli.

        Dodatkowe przykłady dostosowywania widoku konsoli są dostępne w [Blog zespołu programu Windows PowerShell](https://blogs.msdn.com/b/powershell/).

## <a name="see-also"></a>Zobacz też

- [Dokumentacja poleceń Cmdlet programu Windows PowerShell](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
- [Program Windows PowerShell w witrynie Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
- [Repozytorium Centrum skryptów TechNet](https://gallery.technet.microsoft.com/scriptcenter)
- [Centrum skryptów — Witaj, Twórco skryptów!](https://technet.microsoft.com/scriptcenter)
- [Blog zespołu programu PowerShell Windows](https://blogs.msdn.com/b/powershell/)