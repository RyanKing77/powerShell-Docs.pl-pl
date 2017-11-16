---
ms.date: 2017-08-23
keywords: polecenia cmdlet programu PowerShell
title: "za pomocą konsoli programu powershell systemu windows oparte na sieci web"
ms.openlocfilehash: 31ab17f1a1ea1353abc6f770285a2dca70da446d
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="use-the-web-based-windows-powershell-console"></a>Korzystanie z konsoli internetowej programu Windows PowerShell

Zaktualizowano: 24 czerwca 2013

Dotyczy: Windows Server 2012 R2, Windows Server 2012

Windows PowerShell Web Access umożliwia użytkownikom zalogować się do witryny sieci Web zabezpieczonych; Aby można było używać sesji, poleceń cmdlet i skryptów programu Windows PowerShell do zarządzania komputerem zdalnym.

Ponieważ konsolę programu Windows PowerShell jest uruchamiana w przeglądarce sieci web, można je otworzyć z szerokiej gamy urządzeń klienckich; prawie wszystkie urządzenia z przeglądarką sieci web działa.

Konsoli internetowej programu Windows PowerShell jest przeznaczona dla komputera zdalnego, który jest określony przez użytkowników w ramach procesu logowania. 

W tym temacie opisano, jak zarejestrować się w usłudze i rozpocząć korzystanie z konsoli internetowej programu Windows PowerShell Web Access.

W tym temacie nie opisano sposobu używania programu Windows PowerShell i uruchamiania poleceń cmdlet i skryptów. Aby uzyskać informacje o sposobie używania programu Windows PowerShell i zasobów skryptów, zobacz [Zobacz też](#see-also) sekcji na końcu tego tematu.

## <a name="supported-browsers-and-client-devices"></a>Obsługiwane przeglądarki i urządzenia klienckie

Windows PowerShell Web Access obsługuje następujące przeglądarki internetowe. Choć przeglądarki dla urządzeń przenośnych oficjalnie nie są obsługiwane, wiele można uruchomić konsoli internetowej programu Windows PowerShell. Konsola prawdopodobnie działa w innych przeglądarkach, które akceptują pliki cookie i obsługują skrypty języka JavaScript oraz witryny HTTPS, ale nie zostały one oficjalnie przetestowane.

### <a name="supported-desktop-computer-browsers"></a>Obsługiwane przeglądarki na komputery stacjonarne

- Windows Internet Explorer dla systemu Microsoft Windows 8.0, 9.0, 10.0 i 11.0
- Mozilla Firefox 10.0.2
- Google chromowana 17.0.963.56m dla systemu Windows
- Apple Safari 5.1.2 dla systemu Windows
- Apple Safari 5.1.2 dla komputerów Mac OS

### <a name="minimally-tested-mobile-devices-or-browsers"></a>Minimalnie przetestowane urządzenia przenośne lub przeglądarki

- Windows Phone 7 i 7.5
- System Google Android WebKit 3.1 dla systemu Android 2.2.1 (jądro 2.6)
- iPhone, przeglądarka Apple Safari dla systemu operacyjnego 5.0.1
- Apple Safari dla urządzenia iPad 2 systemu operacyjnego 5.0.1

### <a name="browser-requirements"></a>Wymagania dotyczące przeglądarek

Aby korzystać z konsoli internetowej programu Windows PowerShell Web Access, wykonaj następujące czynności przeglądarki.

- Zezwalaj na pliki cookie z witryny sieci Web dla bramy systemu Windows PowerShell Web Access.
- Otwieranie i odczyt stron korzystających z protokołu HTTPS.
- Otwieranie i obsługa witryn, w których jest używany język JavaScript.

## <a name="signing-in-to-windows-powershell-web-access"></a>Logowanie się do programu Windows PowerShell Web Access

Administrator programu Windows PowerShell Web Access powinien podać adres URL, którego adres bramy systemu Windows PowerShell Web Access organizacji witryny sieci Web.
Domyślnie ten adres witryny sieci Web jest *https://\<nazwa_serwera\>/pswa*.

Zanim zalogujesz się do programu Windows PowerShell Web Access można się, że nazwa lub adres IP komputera zdalnego, którym chcesz zarządzać.
Musisz być autoryzowanym użytkownikiem na komputerze zdalnym. Ponadto komputer musi być skonfigurowany pod kątem zarządzania zdalnego.
Aby uzyskać więcej informacji o konfigurowaniu komputera w celu umożliwienia zarządzania zdalnego, zobacz [Włączanie i używanie poleceń zdalnych w programie Windows PowerShell](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enable-psremoting).

Najprostszą metodą konfiguracji komputera w celu umożliwienia zarządzania zdalnego jest uruchomienie **Enable-PSRemoting - force** polecenia cmdlet na komputerze, w sesji środowiska Windows PowerShell, która została otwarta z podwyższonym poziomem uprawnień użytkownika (**Uruchom jako Administrator**).

### <a name="to-sign-in-to-windows-powershell-web-access"></a>Aby zalogować się do programu Windows PowerShell Web Access

1. Otwórz witrynę sieci Web Windows PowerShell Web Access w oknie przeglądarki internetowej lub na karcie.

1. W witrynie Windows PowerShell Web Access logowania Podaj swoją nazwę użytkownika w sieci, hasło i nazwę komputera, na którym chcesz zarządzać (i na którym jesteś autoryzowanym użytkownikiem). Jeśli administrator programu Windows PowerShell Web Access zalecił używanie identyfikatora URI do witryny niestandardowej lub serwera proxy zamiast nazwy komputera, zaznacz **identyfikator URI połączenia** w **typ połączenia** pola, a następnie Podaj identyfikator URI.

    > ![Uwaga](images/Note.jpeg) **Uwaga**:
    >
    > - Jeśli komputer docelowy do grupy roboczej, aby podać nazwę użytkownika i zaloguj się do komputera należy użyć następującej składni:`<workgroup_name>\<user_name>`
    > - Jeśli komputer docelowy jest serwerem bramy, można określić `localhost` w polu Nazwa komputera
    > - Jeśli komputer docelowy jest serwerem bramy, a serwer bramy znajduje się w grupie roboczej, należy użyć `<workgroup name>\<user_name>` w nazwie użytkownika usterki. Można użyć `localhost` w polu nazwy komputera.

1. **Opcjonalne ustawienia połączenia** sekcji dotyczy wymagań autoryzacji komputera zdalnego, którym chcesz zarządzać. Aby uzyskać więcej informacji na temat parametrów, które są równoważne opcjonalnym ustawieniom połączenia, zobacz [Enter-PSSession](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession) pomocy polecenia cmdlet.

    Zwykle poświadczenia przekazywane za pośrednictwem bramy systemu Windows PowerShell Web Access są takie same, które są rozpoznawane przez komputer zdalny, które mają być zarządzane. Jeśli chcesz użyć innych poświadczeń do zarządzania komputerem zdalnym określoną w kroku 2, rozwiń węzeł **opcjonalne ustawienia połączenia** sekcji i udostępnienie alternatywnych poświadczeń. W przeciwnym razie przejdź do kroku 6.

1. Jeśli administrator programu Windows PowerShell Web Access utworzył niestandardową konfigurację sesji dla użytkowników programu Windows PowerShell Web Access, wpisz nazwę konfiguracji sesji w **Nazwa konfiguracji** pola. Aby uzyskać więcej informacji na temat konfiguracji sesji, zobacz [informacje o konfiguracjach sesji](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_session_configurations).

1. Zachowaj **typ uwierzytelniania** ustawioną **domyślne** , chyba że użytkownik ma zalecił inaczej przez administratora programu Windows PowerShell Web Access.

1. Kliknij przycisk **Zaloguj**.

## <a name="signing-out-and-timing-out"></a>Wylogowywanie i limit czasu

Jedną z następujących czynności i sytuacji powoduje wylogowanie z sesji środowiska Windows PowerShell opartych na sieci web.

- Kliknięcie przycisku **Wyloguj** w prawym dolnym rogu konsoli. (Dotyczy tylko systemu Windows Server 2012)

- Kliknięcie przycisku **zapisać** lub **zakończenia** w prawym dolnym rogu konsoli (tylko w systemie Windows Server 2012 R2). Kliknięcie przycisku **zapisać** powoduje zapisanie i zamknięcie sesji programu Windows PowerShell Web Access; można ponownie połączyć się z sesją później. Gdy użytkownik zaloguje się do programu Windows PowerShell Web Access ponownie, Windows PowerShell Web Access wyświetlana lista zapisanych sesji. Możesz wybrać i ponowne łączenie się z zapisanej sesji lub uruchomić nową sesję. Maksymalna dozwolona liczba otwartych sesji użytkownika, zarówno zapisanych, jak i aktywnych, jest skonfigurowana przez administratora bramy.

    Kliknięcie przycisku **zakończenia** i sytuacji powoduje wylogowanie sesji programu Windows PowerShell Web Access bez jej zapisania.

- Próba zalogowania się w celu zarządzania innym komputerem zdalnym w tej samej sesji przeglądarki lub na nowej karcie tej samej sesji przeglądarki. (Nie dotyczy to jeśli serwer bramy działa system Windows Server 2012 R2; Windows PowerShell Web Access uruchomiona w systemie Windows Server 2012 R2 Zezwalaj na wiele sesji użytkownika na nowych kartach w tej samej sesji przeglądarki.) Aby uzyskać więcej informacji o sposobie używania więcej niż jednej aktywnej sesji na tym samym komputerze, zobacz łączenie z wieloma komputerami docelowymi jednocześnie w [ograniczenia konsoli internetowej](#limitations-of-the-web-based-console) tego tematu.

- 20 minut bezczynności sesji. Administrator bramy może dostosować limit czasu bezczynności. Aby uzyskać więcej informacji, zobacz [zarządzania sesjami](authorization-rules-and-security-features-of-windows-powershell-web-access.md#session-management).

    - Przypadku rozłączenia z sesją w konsoli sieci web ze względu na błąd sieci lub innych nieplanowanego zamknięcia lub awarii, a nie zamknięcia sesji przez użytkownika, Windows PowerShell Web Access sesji jest nadal uruchomiona, połączone z docelowymi komputer, przed upłynięciem limitu czasu na wygaśnie po stronie klienta. Domyślny limit czasu wynosi 20 minut. Konfiguruje go administratora bramy. Sesja zostaje rozłączona po upływie domyślnego limitu 20 minut lub innego limitu czasu określonego przez administratora bramy — w zależności od tego, który z tych limitów jest krótszy.

        Jeśli serwer bramy działa system Windows Server 2012 R2, Windows PowerShell Web Access umożliwia użytkownikom ponowne łączenie się z zapisanymi sesjami w późniejszym czasie, ale nie można wyświetlić lub ponownie połączyć się zapisanych sesji do czasu po upływie limitu czasu określonego przez bramę administratora wygasły.

- Zamknięcie okna lub karty przeglądarki.

- Wyłączenie urządzenia klienckiego, na którym uruchomiono przeglądarkę, lub rozłączenie jej z siecią.

- Uruchomiona **zakończenia** w konsoli sieci web. To polecenie nie działa, jeśli konfiguracji sesji, z którym nawiązano jest skonfigurowany do obsługi [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) trybu, lub znajduje się w ograniczonym obszarem działania.

Jeśli chcesz zalogować się ponownie, ponownie otwórz stronę sieci web Windows PowerShell Web Access i zaloguj się, wykonując kroki opisane w [rejestrowania się w programie Windows PowerShell Web Access](#signing-in-to-windows-powershell-web-access) w tym temacie.

## <a name="differences-in-the-web-based-windows-powershell-console"></a>Różnice w konsoli internetowej programu Windows PowerShell

Po zalogowaniu się do programu Windows PowerShell Web Access, konsoli internetowej programu Windows PowerShell otwiera w przeglądarce lub na karcie. Ponieważ konsola jest połączony z komputerem zdalnym, który określone w procesie logowania, tylko te polecenia cmdlet programu Windows PowerShell lub skryptów, które są dostępne na komputerze zdalnym, można w konsoli. W tej sekcji opisano inne ograniczenia konsoli programu Windows PowerShell Web Access i różnice między konsole programu Windows PowerShell Web Access i zainstalowaną **PowerShell.exe** konsoli.

### <a name="functional-disparity-with-powershellexe"></a>Różnice funkcjonalne z porównaniu z programem PowerShell.exe

Większość funkcji hosta programu Windows PowerShell jest dostępny w konsoli internetowej programu Windows PowerShell Web Access, ale niektóre funkcje, które nie są dostępne.

- Wyświetla postęp zagnieżdżonych.

  Windows PowerShell Web Access wyświetla graficzny interfejs użytkownika postępu dla poleceń cmdlet postęp tego raportu, ale jest wyświetlany tylko informacje o postępie najwyższego poziomu.

- Zmiana koloru okna wprowadzania.

  Nie można zmienić koloru okna wprowadzania (pierwszego planu i tła). Styl danych wyjściowych, ostrzeżeń, trybu pełnego i komunikatów o błędach można zmienić, uruchamiając skrypt.

- PSHostRawUserInterface.

  Windows PowerShell Web Access jest implementowany przez zarządzanie zdalne programu Windows PowerShell, a następnie używa zdalnego obszaru działania. Windows PowerShell Web Access nie implementuje niektórych metod, w tym interfejsie; na przykład poleceń, które zapisują do konsoli systemu Windows. Polecenia takie jak **PowerTab** nie działają w programie Windows PowerShell Web Access.

- Klawisze funkcyjne.

  Windows PowerShell Web Access nie obsługuje niektórych klawiszy funkcyjnych w wielu przypadkach, ponieważ poleceń jest zarezerwowanych przez przeglądarkę.

### <a name="unsupported-shortcut-keys"></a>Nieobsługiwane klawisze

Klawisze funkcyjne | Akcja
-- | --
CTRL+C | W programie Windows PowerShell Web Access **klawisze Ctrl + C** jest używana przez przeglądarkę do kopiowania zawartości. W konsoli jest **anulować** przycisk, a użytkownicy mogą także użyć **klawisze Ctrl + Q** do anulowania poleceń.
Alt+spacja, e, l | Przewijanie buforu ekranu
Alt+spacja, e, f | Wyszukiwanie tekstu w buforze ekranu
Alt+spacja, e, k | Zaznaczenie tekstu do skopiowania z buforu ekranu
Alt+spacja, e, p | Wklej zawartość Schowka do konsoli środowiska Windows PowerShell
Alt+spacja, c | Zamknij konsolę programu Windows PowerShell
CTRL+Break | Wymuś okno programu Windows PowerShell, aby zamknąć
Ctrl+Home | Usunięcie zawartości od początku bieżącego wiersza polecenia
CTRL+End | Usunięcie zawartości do końca wiersza polecenia
F1 | Przesunięcie kursora o jeden znak w prawo w wierszu polecenia
F2 | Utworzenie nowego polecenia przez skopiowanie ostatniego polecenia aż do wpisywanego znaku
F3 | Zakończenie wiersza polecenia zawartością z ostatniego wiersza polecenia
F4 | Usunięcie znaków od pozycji kursora
F5 | Przeszukiwanie historii poleceń. Aby uzyskać dostęp do poleceń w historii poleceń programu Windows PowerShell Web Access, kliknij przycisk **historii** przewiń przyciski w konsoli sieci web.
F7 | Interaktywne wybieranie polecenia z historii poleceń
F8 | Przeszukanie historii i wyświetlenie poleceń zgodnych z bieżącym tekstem
F9 | Uruchomienie konkretnego numeru polecenia z historii
Page Up | Uruchomienie pierwszego polecenia w historii
Page Down | Uruchomienie ostatniego polecenia w historii
ALT+F7 | Wyczyszczenie listy historii poleceń

### <a name="limitations-of-the-web-based-console"></a>Ograniczenia konsoli internetowej

- Podwójny przeskok

    Połączenie z dwoma przeskokami (lub połączenia z drugim komputerem z pierwszego połączenia) może wystąpić ograniczenie podczas tworzenia lub działają w nowej sesji przy użyciu programu Windows PowerShell Web Access. Windows PowerShell Web Access używa zdalnego obszaru działania, a obecnie program **PowerShell.exe** nie obsługuje połączenia zdalnego z drugim komputerem ze zdalnego obszaru działania. Jeśli próba nawiązania połączenia z drugim komputerem zdalnym z istniejącego połączenia przy użyciu **Enter-PSSession** polecenia cmdlet, na przykład można uzyskać różne błędy, takie jak €œCannot pobrać zasobów sieciowych.

    Aby uniknąć podwójnego przeskoku błędów, administrator powinien skonfigurować uwierzytelnianie CredSSP w danym środowisku sieciowym organizacji. Aby uzyskać więcej informacji na temat konfigurowania uwierzytelniania CredSSP, zobacz [protokół CredSSP na potrzeby komunikacji zdalnej drugiego przeskoku](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) w witrynie firmy Microsoft. Jeśli chcesz zarządzać drugim komputerem zdalnym, możesz też podać jawne poświadczenia. Niejawne poświadczenia raczej nie pozwalają na drugi przeskok.

- Usługi zdalne

    Windows PowerShell Web Access używa i ma te same ograniczenia co sesji zdalnej programu Windows PowerShell. Nie działają polecenia wywołujące bezpośrednio interfejsy API konsoli systemu Windows, takie jak edytory oparte na konsoli lub programy z menu tekstowym, ponieważ polecenia nie odczytują standardowych potoków danych wejściowych, wyjściowych i błędów ani nie zapisują do nich. W związku z tym polecenia, które uruchamiają plik wykonywalny plików, takich jak **notepad.exe**, ani nie wyświetlają graficzny interfejs użytkownika, takich jak `OpenGridView` lub `ogv`, nie działają. Wpływ na pracę tego zachowania; prawdopodobnie nie odpowiada na polecenia programu Windows PowerShell Web Access.

- Uzupełnianie po naciśnięciu tabulatora

    Uzupełnianie po naciśnięciu tabulatora nie działa w konfiguracji sesji z ograniczonym obszarem działania lub w **NoLanguage** tryb. Chociaż administratorzy mogą skonfigurować sesję do obsługi uzupełniania po naciśnięciu tabulatora, jest to odradzane ze względów bezpieczeństwa. Może bowiem spowodować ujawnienie następujących informacji nieupoważnionym użytkownikom.

    - Ścieżki wewnętrznego systemu plików

    - Foldery udostępnione na komputerach wewnętrznych

    - Zmienne w obszarze działania

    - Załadowane typy lub przestrzenie nazw programu .NET Framework

    - Zmienne środowiskowe

- **NoLanguage** sesji lub ograniczonego obszaru działania

    Użytkownicy, którzy są zalogowani na **NoLanguage** nie można uruchomić sesji konfiguracji lub ograniczonym obszarem działania w programie Windows PowerShell Web Access **zakończenia** polecenie, aby zakończyć sesję. Aby się wylogować, użytkownik powinien kliknąć pozycję **Wyloguj** na stronie konsoli.

- Połączenie z wieloma komputerami docelowymi jednocześnie.

    Jeśli serwer bramy działa system Windows Server 2012, Windows PowerShell Web Access umożliwia tylko jedno połączenie z komputerem zdalnym na sesję przeglądarki. nie umożliwia użytkownikom zalogować się raz i nawiązywania z wieloma komputerami zdalnymi przy użyciu osobnych kartach przeglądarki. Po otwarciu nowej karty lub nowego okna przeglądarki programu Windows PowerShell Web Access monituje o rozłączenie bieżącej sesji i rozpocznij nową sesję, dzięki czemu można łączyć się z nowym (lub taka sama) zdalnego komputera. Jeśli potrzebne są co najmniej dwa osobne sesje w przypadku różnych komputerów zdalnych, jednak funkcja w programie Internet Explorer umożliwia utworzenie nowej sesji. Aby uruchomić nową sesję w programie Internet Explorer, naciśnij klawisz **ALT**, otwórz **pliku** menu, a następnie wybierz **nowej sesji**. Następnie otwórz witrynę sieci Web Windows PowerShell Web Access w nowej sesji i zaloguj się do komputera zdalnego dostępu.

    Jeśli brama programu Windows PowerShell Web Access jest uruchomiona w systemie Windows Server 2012 R2, użytkownicy mogą otwierać wiele połączeń z komputerami zdalnymi na różnych kartach przeglądarki. Jeśli chcesz otworzyć więcej niż jedno połączenie z komputerem zdalnym za pomocą konsoli internetowej programu Windows PowerShell, skontaktuj się z administratorem bramy Windows PowerShell Web Access, aby sprawdzić, czy ta funkcja jest obsługiwana przez serwer bramy.

- Trwałe sesje programu Windows PowerShell (ponowne połączenie).

    Po możesz limitu czasu bramy programu Windows PowerShell Web Access połączenie zdalne między bramą i komputerem docelowym jest zamknięty. Powoduje to zatrzymanie wszystkich wykonywanych wówczas poleceń cmdlet i skryptów. Zaleca się używanie środowiska Windows PowerShell **-zadania** infrastruktury, w przypadku wykonywania długotrwałych zadań, dzięki czemu można uruchamiać zadania, odłączenie komputera, późniejsze ponowne połączenie i utrwalonymi zadaniami. Inną zaletą używania **-zadania** polecenia cmdlet jest, że można je uruchomić przy użyciu programu Windows PowerShell Web Access, wyloguj się i później ponownego połączenia, uruchomione Windows PowerShell Web Access lub innego hosta (na przykład programu Windows PowerShell Zintegrowane środowisko obsługi skryptów (ISE)).

- Zmiana rozmiaru konsoli.

    **PowerShell.exe** okna konsoli można zmieniać następujące trzy sposoby.

    - Przeciągnięcie i dostosowanie rozmiaru okna konsoli za pomocą myszy

    - Zmiana wysokości i szerokości przy użyciu graficznego interfejsu użytkownika właściwości konsoli

    - Zmiana wysokości i szerokości okien konsoli systemu za pomocą polecenia cmdlet

        Okno konsoli programu Windows PowerShell Web Access można skonfigurować przy użyciu poleceń cmdlet w następujący sposób. W poniższym przykładzie użytkownik zmienia szerokość konsoli programu Windows PowerShell Web Access, aby **20**.

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        W podobny sposób można zmienić wysokość konsoli.

        Dodatkowe przykłady dostosowywania widoku konsoli są dostępne w [Blog zespołu programu Windows PowerShell](http://blogs.msdn.com/b/powershell/).

## <a name="see-also"></a>Zobacz też

- [Dokumentacji poleceń Cmdlet programu Windows PowerShell](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
- [Środowisko Windows PowerShell w witrynie Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
- [Repozytorium Centrum skryptów w witrynie TechNet](http://gallery.technet.microsoft.com/scriptcenter)
- [Centrum skryptów — Witaj, Twórco skryptów!](https://technet.microsoft.com/scriptcenter)
- [Blog zespołu programu PowerShell systemu Windows](http://blogs.msdn.com/b/powershell/)
