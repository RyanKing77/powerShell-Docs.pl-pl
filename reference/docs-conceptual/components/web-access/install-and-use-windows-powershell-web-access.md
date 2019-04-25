---
ms.date: 08/23/2017
keywords: polecenia cmdlet programu PowerShell
title: Instalowanie i używanie programu windows powershell web access
ms.openlocfilehash: 53558f9be5065c7f630f06e535ddab4d7ad72d9e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058574"
---
# <a name="install-and-use-windows-powershell-web-access"></a>Instalowanie i używanie programu Windows PowerShell Web Access

Zaktualizowano: 5 listopada 2013 r. (edytować: 23 sierpnia 2017 r.)

Dotyczy: Windows Server 2012 R2, Windows Server 2012

## <a name="introduction"></a>Wprowadzenie

Windows PowerShell Web Access, wprowadzona w systemie Windows Server 2012, działa jako brama programu Windows PowerShell, zapewniająca opartego na sieci web konsolę programu Windows PowerShell, ukierunkowanych na komputerze zdalnym. Umożliwia on informatykom uruchamianie poleceń programu Windows PowerShell i skryptów z poziomu konsoli programu Windows PowerShell w przeglądarce sieci web bez programu Windows PowerShell, oprogramowanie do zarządzania zdalnego lub przeglądarki wtyczki konieczności instalowania na urządzeniu klienckim. Wszystko, co jest wymagane do uruchamiania konsoli internetowej programu Windows PowerShell jest prawidłowo skonfigurowana brama programu Windows PowerShell Web Access i przeglądarka na urządzeniu klienckim obsługuje język JavaScript, która akceptuje pliki cookie.

Przykładami urządzeń klienckich laptopów, bez służbowego komputery osobiste, wypożyczone komputery, tablety, kioski internetowe, komputerów, które nie są uruchomione systemu operacyjnego Windows i przeglądarki w telefonach komórkowych. Informatycy mogą wykonywać kluczowe zadania zarządzania na zdalnych serwerów z systemem Windows z urządzeń, które mają dostęp do połączenia internetowego i przeglądarki sieci web.

Bramy pomyślnej instalacji i konfiguracji użytkownikom dostęp do konsoli środowiska Windows PowerShell przy użyciu przeglądarki sieci web. Przy otwieraniu przez użytkowników zabezpieczonej witryny sieci Web programu Windows PowerShell Web Access, można uruchomić konsoli internetowej programu Windows PowerShell, po pomyślnym uwierzytelnieniu.

Instalacja programu Windows PowerShell Web Access i konfiguracja jest procesem trzech kroków:

1. [Instalowanie programu Windows PowerShell Web Access](#install-windows-powershell-web-access-using-powershell-cmdlets)
1. [Konfigurowanie bramy](#configure-the-gateway)
1. [Konfigurowanie restrykcyjnej reguły autoryzacji](#configure-a-restrictive-authorization-rule)

Aby zainstalować i skonfigurować program Windows PowerShell Web Access, firma Microsoft zaleca, w tym przewodniku całego, który zawiera instrukcje dotyczące sposobu instalowania, zabezpieczania i odinstalowywania programu Windows PowerShell Web Access. [Za pomocą konsoli programu PowerShell Windows opartej na sieci Web](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11)) tematu w tym artykule opisano, jak użytkownicy logują się do konsoli sieci web, a także jej ograniczenia i różnice między konsolą sieci web programu Windows PowerShell i  **PowerShell.exe** konsoli. Użytkownicy końcowi konsoli internetowej powinni przeczytać [korzystanie konsoli internetowej Windows PowerShell](use-the-web-based-windows-powershell-console.md), ale muszą czytać dalszej części tego przewodnika.

W tym temacie nie zawiera szczegółowych wskazówek operacji serwera sieci Web usług IIS; w tym temacie opisano tylko kroki wymagane do skonfigurowania bramy programu Windows PowerShell Web Access. Aby uzyskać więcej informacji na temat konfigurowania i zabezpieczania witryn internetowych w usługach IIS Zobacz zasoby dokumentacji usług IIS w sekcji Zobacz też.

Na poniższym diagramie przedstawiono, jak działa program Windows PowerShell Web Access.

![Diagram programu Windows PowerShell Web Access](images/Windows-PowerShell-Web-Access-diagram.jpg)

## <a name="requirements-for-running-windows-powershell-web-access"></a>Wymagania systemu Windows PowerShell Web Access

Windows PowerShell Web Access wymaga serwera sieci Web (IIS), .NET Framework 4.5 i programu Windows PowerShell 3.0 lub Windows PowerShell 4.0 jest uruchomiony na serwerze, na którym ma działać brama działał. Windows PowerShell Web Access można zainstalować na serwerze, na którym jest uruchomiony system Windows Server 2012 R2 lub Windows Server 2012, przy użyciu Dodaj role i funkcje kreatora w Menedżerze serwera lub polecenia cmdlet wdrażania programu Windows PowerShell dla programu Menedżer serwera. Po zainstalowaniu programu Windows PowerShell Web Access za pomocą Menedżera serwera lub jego polecenia cmdlet wdrażania wymagane role i funkcje są automatycznie dodawane jako część procesu instalacji.

Windows PowerShell Web Access umożliwia użytkownikom zdalnym dostęp do komputerów w organizacji za pomocą programu Windows PowerShell w przeglądarce sieci web. Mimo że program Windows PowerShell Web Access jest narzędziem do zarządzania wygodnym i zaawansowanym, dostępu opartego na sieci web stanowi zagrożenia bezpieczeństwa i powinny być konfigurowane w bezpieczny sposób. Zalecamy Administratorzy, którzy konfigurują bramę programu Windows PowerShell Web Access za pomocą warstw zabezpieczeń dostępne reguły autoryzacji opartej na polecenia cmdlet dołączone do programu Windows PowerShell Web Access i zabezpieczeń warstwy, które są dostępne w serwerze sieci Web ( Usługi IIS) i aplikacji innych firm. W tej dokumentacji opisano zarówno przykłady niezabezpieczone, które są zalecane tylko dla środowisk testowych, a także przykłady, które są zalecane w przypadku wdrożeń zabezpieczonych.

## <a name="browser-and-client-device-support"></a>Obsługa urządzeń przeglądarki i klienta

Windows PowerShell Web Access obsługuje następujące przeglądarki internetowe. Choć przeglądarki dla urządzeń przenośnych oficjalnie nie są obsługiwane, wiele można uruchomić konsoli internetowej programu Windows PowerShell.
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

## <a name="recommended-quick-deployment"></a>Zalecane szybkiego wdrażania

Bramę programu Windows PowerShell Web Access można zainstalować na serwerze, na którym jest uruchomiony system Windows Server 2012 R2 lub Windows Server 2012, przy użyciu albo polecenia cmdlet programu Windows PowerShell lub przy użyciu Dodaj role i funkcje kreatora, który jest otwierany z w Menedżerze serwera. Dla przeprowadzić szybką instalację i konfigurację użyj polecenia cmdlet programu Windows PowerShell, zgodnie z opisem w tej sekcji.

1. [Instalowanie programu Windows PowerShell Web Access](#install-windows-powershell-web-access-using-powershell-cmdlets)
1. [Konfigurowanie bramy](#configure-the-gateway)
1. [Konfigurowanie restrykcyjnej reguły autoryzacji](#configure-a-restrictive-authorization-rule)

### <a name="install-windows-powershell-web-access-using-powershell-cmdlets"></a>Zainstaluj system Windows PowerShell Web Access za pomocą poleceń cmdlet programu PowerShell

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a>Aby zainstalować program Windows PowerShell Web Access za pomocą poleceń cmdlet programu Windows PowerShell

1. Wykonaj jedną z następujących czynności, aby otworzyć sesję środowiska Windows PowerShell z podwyższonym poziomem uprawnień użytkownika.

   - Na pulpicie systemu Windows kliknij prawym przyciskiem myszy **środowiska Windows PowerShell** na pasku zadań, a następnie kliknij przycisk **Uruchom jako Administrator**.
   - Na Windows **Start** ekranu, kliknij prawym przyciskiem myszy **programu Windows PowerShell**, a następnie kliknij przycisk **Uruchom jako Administrator**.

   > [!NOTE]
   > W programie Windows PowerShell 3.0 i 4.0 istnieje nie trzeba importować modułu poleceń cmdlet Menedżera serwera do sesji środowiska Windows PowerShell, przed uruchomieniem poleceń cmdlet, które są częścią tego modułu. Moduł jest automatycznie importowany podczas pierwszego uruchomienia polecenia cmdlet, które są częścią tego modułu.
   > Ponadto poleceń cmdlet programu Windows PowerShell nie jest rozróżniana wielkość liter.

1. Wpisz następujące polecenie, a następnie naciśnij klawisz **Enter**, gdzie *nazwa_komputera* reprezentuje komputer zdalny, na którym chcesz zainstalować program Windows PowerShell Web Access, jeśli ma to zastosowanie. `-Restart` Parametru spowoduje automatyczne ponowne uruchomienie serwerów docelowych w razie potrzeby.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart`

   > [!NOTE]
   > Instalowanie programu Windows PowerShell Web Access za pomocą poleceń cmdlet programu Windows PowerShell nie powoduje dodania narzędzi do zarządzania serwerem sieci Web (IIS) domyślnie. Jeśli chcesz zainstalować narzędzia do zarządzania na tym samym serwerze co brama programu Windows PowerShell Web Access, należy dodać `-IncludeManagementTools` do polecenia instalacji (co zostało opisane w tym kroku). Jeśli zarządzasz witryny sieci Web programu Windows PowerShell Web Access z komputera zdalnego, zainstaluj przystawkę Menedżer usług IIS, instalując [zdalnego serwera Administracja narzędzia dla Windows 8.1](https://www.microsoft.com/en-us/download/details.aspx?id=39296) lub [administracji zdalnej serwera Narzędzia dla systemu Windows 8](https://www.microsoft.com/en-us/download/details.aspx?id=28972) na komputerze, z którego chcesz do zarządzania bramą.

   Aby zainstalować role i funkcje na dysku VHD trybu offline, należy dodać `-ComputerName` parametru i `-VHD` parametru. `-ComputerName` Parametr zawiera nazwę serwera, na którym należy zainstalować dysk VHD, a `-VHD` parametr zawiera ścieżkę do pliku VHD na określonym serwerze.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart`

1. Po zakończeniu instalacji sprawdź, czy program Windows PowerShell Web Access zostało zainstalowane na serwerach docelowych, uruchamiając `Get-WindowsFeature` polecenia cmdlet na serwerze docelowym, w konsoli programu Windows PowerShell, która została otwarta z podwyższonym poziomem uprawnień użytkownika. Można też sprawdzić, czy program Windows PowerShell Web Access został zainstalowany w konsoli Menedżera serwera, wybierając serwer docelowy na **wszystkie serwery** strony, a następnie wyświetlić **ról i funkcji** Kafelek dla wybranego serwera. Można również wyświetlić plik readme dla programu Windows PowerShell Web Access.

1. Po zainstalowaniu programu Windows PowerShell Web Access, wyświetlany jest monit o przejrzenie pliku readme, który zawiera instrukcje dotyczące konfigurowania podstawowych, jest wymagane dla bramy. Te instrukcje instalacji znajdują się również w poniższej sekcji [skonfigurować bramę](#configure-the-gateway). Ścieżka do pliku readme jest `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>Konfigurowanie bramy

**Install-PswaWebApplication** polecenie cmdlet jest szybkim sposobem uzyskania skonfigurowany program Windows PowerShell Web Access. Chociaż możesz dodać `UseTestCertificate` parametr `Install-PswaWebApplication` polecenia cmdlet, aby zainstalować certyfikat protokołu SSL z podpisem własnym dla testu w celach, to nie jest bezpieczna, zabezpieczonym środowisku produkcyjnym zawsze używaj prawidłowego certyfikatu SSL, który został podpisany przez Urząd certyfikacji (CA). Administratorzy mogą zastąpić certyfikat testowy z certyfikatem z podpisem dowolnego przy użyciu konsoli Menedżera usług IIS.

Możesz ukończyć konfigurację aplikacji sieci web programu Windows PowerShell Web Access albo uruchamiając `Install-PswaWebApplication` polecenia cmdlet lub wykonując kroki konfiguracji graficznego interfejsu użytkownika w Menedżerze usług IIS.
Domyślnie to polecenie cmdlet instaluje aplikację sieci web **pswa** (i jego pulę aplikacji, **pswa_pool**) w polu **domyślna witryna sieci Web** kontenera, jak pokazano w Menedżerze usług IIS; Jeśli żądane, może wydać polecenie cmdlet, aby zmienić kontener domyślnej witryny aplikacji sieci web. Menedżer usług IIS oferuje opcje konfiguracji, które są dostępne dla aplikacji sieci web, takich jak zmiana numeru portu lub certyfikatu protokołu Secure Sockets Layer (SSL).

> **![Uwaga dotycząca zabezpieczeń](images/securitynote.jpeg) Uwaga dotycząca zabezpieczeń** zdecydowanie zalecamy, aby administratorzy skonfigurowali bramę do użycia prawidłowego certyfikatu, który został podpisany przez urząd certyfikacji.

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a>Aby skonfigurować bramę programu Windows PowerShell Web Access z certyfikatem testowym przy użyciu polecenia cmdlet Install-PswaWebApplication

1. Wykonaj jedną z następujących czynności, aby otworzyć sesję środowiska Windows PowerShell.

   - Na pulpicie Windows kliknij prawym przyciskiem myszy **programu Windows PowerShell** na pasku zadań.
   - Na Windows **Start** ekranu, kliknij przycisk **programu Windows PowerShell**.

2. Wpisz następujące polecenie, a następnie naciśnij klawisz **Enter**.

   `Install-PswaWebApplication -UseTestCertificate`

   > **![Uwaga dotycząca zabezpieczeń](images/securitynote.jpeg) Uwaga dotycząca zabezpieczeń** `UseTestCertificate` parametru należy używać tylko w prywatnym środowisku testowym. Dla zabezpieczonym środowisku produkcyjnym zaleca się użycie prawidłowego certyfikatu, który został podpisany przez urząd certyfikacji.

   Uruchamiając polecenie cmdlet instaluje aplikację sieci web programu Windows PowerShell Web Access w kontenerze domyślna witryna sieci Web usług IIS. Polecenie cmdlet tworzy infrastrukturę niezbędną do uruchomienia programu Windows PowerShell Web Access w domyślnej witrynie sieci Web, `https://<server_name>/pswa`. Aby zainstalować aplikację sieci web w innej witryny, należy podać nazwę witryny sieci Web, dodając `WebSiteName` parametru. Aby zmienić nazwę aplikacji sieci web (wartość domyślna to `pswa`), Dodaj `WebApplicationName` parametru.

   Następujące ustawienia są konfigurowane przy użyciu polecenia cmdlet. W razie potrzeby można zmienić je ręcznie w konsoli Menedżera usług IIS.

   - Path: /pswa
   - ApplicationPool: pswa_pool
   - EnabledProtocols: http
   - PhysicalPath: %windir%/Web/PowerShellWebAccess/wwwroot

   **Przykład**: `Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate`

   W tym przykładzie wynikowa witryna internetowa dla programu Windows PowerShell Web Access jest `https://<server_name>/myWebApp`.

   > [!NOTE]
   > Nie można zalogować się do momentu użytkownikom udzielono dostępu do witryny internetowej przez dodanie reguł autoryzacji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie restrykcyjnej reguły autoryzacji](#configure-a-restrictive-authorization-rule) i [reguły autoryzacji i zabezpieczeń funkcji programu Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a>Aby skonfigurować bramę programu Windows PowerShell Web Access z oryginalnym certyfikatem przy użyciu polecenia cmdlet Install-PswaWebApplication i Menedżera usług IIS

1. Wykonaj jedną z następujących czynności, aby otworzyć sesję środowiska Windows PowerShell.

   - Na pulpicie Windows kliknij prawym przyciskiem myszy **programu Windows PowerShell** na pasku zadań.
   - Na Windows **Start** ekranu, kliknij przycisk **programu Windows PowerShell**.

2. Wpisz następujące polecenie, a następnie naciśnij klawisz **Enter**.

   `Install-PswaWebApplication`

   Następujące ustawienia bramy są konfigurowane przy użyciu polecenia cmdlet. W razie potrzeby można zmienić je ręcznie w konsoli Menedżera usług IIS. Można również określić wartości dla `WebsiteName` i `WebApplicationName` parametry `Install-PswaWebApplication` polecenia cmdlet.

   - Path: /pswa
   - ApplicationPool: pswa_pool
   - EnabledProtocols: http
   - PhysicalPath: %windir%/Web/PowerShellWebAccess/wwwroot

3. Otwórz konsolę Menedżera usług IIS, wykonując jedną z następujących czynności.

   - Na pulpicie systemu Windows, uruchom Menedżera serwera, klikając **Menedżera serwera** na pasku zadań systemu Windows. Na **narzędzia** menu w Menedżerze serwera kliknij **Internet Information Services (IIS) Manager**.
   - Na Windows **Start** ekranu, kliknij przycisk **Menedżera serwera**.

4. W okienku drzewa Menedżera usług IIS, rozwiń węzeł serwera, na którym zainstalowany jest program Windows PowerShell Web Access, aż do **witryn** folder jest widoczny. Rozwiń **witryn** folderu.

5. Wybierz witrynę sieci Web, w którym zainstalowano aplikację sieci web programu Windows PowerShell Web Access.
   W **akcje** okienku kliknij **powiązania**.

6. W **powiązania witryny** okno dialogowe, kliknij przycisk **Dodaj**.

7. W **Dodawanie powiązania witryny** dialogowym **typu** pól, zaznacz **https**.

8. W **certyfikat SSL** wybierz Twój podpisany certyfikat z menu rozwijanego.
   Kliknij przycisk **OK**. Zobacz [skonfigurować certyfikat SSL w Menedżerze usług IIS](#to-configure-an-ssl-certificate-in-iis-manager) w tym temacie, aby uzyskać więcej informacji o sposobie uzyskiwania certyfikatu.

   Aplikacja sieci web programu Windows PowerShell Web Access jest skonfigurowany do korzystania z podpisanego certyfikatu SSL.

   Dostęp do programu Windows PowerShell Web Access, otwierając `https://<server_name>/pswa` w oknie przeglądarki.

   > [!NOTE]
   > Nie można zalogować się do momentu użytkownikom udzielono dostępu do witryny internetowej przez dodanie reguł autoryzacji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie restrykcyjnej reguły autoryzacji](#configure-a-restrictive-authorization-rule), w tym temacie i [reguły autoryzacji i zabezpieczeń funkcji programu Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configure-a-restrictive-authorization-rule"></a>Konfigurowanie restrykcyjnej reguły autoryzacji

Po zainstalowaniu programu Windows PowerShell Web Access, a brama jest skonfigurowana, użytkownicy mogą otwierać strony logowania w przeglądarce, ale nie można zalogować do momentu administratora programu Windows PowerShell Web Access jawnego przydzielenia im dostępu. Kontrola dostępu w programie Windows PowerShell Web Access odbywa się przy użyciu zestawu poleceń cmdlet Windows PowerShell opisanych w poniższej tabeli. Do dodawania lub zarządzanie regułami autoryzacji jest nie porównywalny graficzny interfejs użytkownika. Aby uzyskać szczegółowe informacje o poleceniach cmdlet programu Windows PowerShell Web Access, zobacz tematy dokumentacja poleceń cmdlet, [polecenia cmdlet programu Windows PowerShell Web Access](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Aby uzyskać więcej szczegółów na temat reguł autoryzacji programu Windows PowerShell Web Access i zabezpieczeń, zobacz [reguły autoryzacji i zabezpieczeń funkcji programu Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-add-a-restrictive-authorization-rule"></a>Aby dodać restrykcyjną regułę autoryzacji

1. Wykonaj jedną z następujących czynności, aby otworzyć sesję środowiska Windows PowerShell z podwyższonym poziomem uprawnień użytkownika.

   - Na pulpicie systemu Windows kliknij prawym przyciskiem myszy **środowiska Windows PowerShell** na pasku zadań, a następnie kliknij przycisk **Uruchom jako Administrator**.
   - Na Windows **Start** ekranu, kliknij prawym przyciskiem myszy **programu Windows PowerShell**, a następnie kliknij przycisk **Uruchom jako Administrator**.

2. Krok opcjonalny, umożliwiający ograniczenie dostępu użytkowników za pomocą konfiguracji sesji: Sprawdź, czy konfiguracje sesji, których chcesz użyć w regułach już istnieją. Jeśli one nie zostały jeszcze utworzone, skorzystaj z instrukcji tworzenia konfiguracji sesji w [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configurations).

3. Wpisz następujące polecenie, a następnie naciśnij klawisz **Enter**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Ta reguła autoryzacji zezwala określonemu użytkownikowi na dostęp do jednego komputera w sieci, do których zwykle mają oni dostęp z uprawnieniami do konfiguracji określonej sesji, które są ograniczone do użytkownika Typowa skryptów i polecenie cmdlet musi.

   W poniższym przykładzie użytkownik o nazwie `JSmith` w `Contoso` domeny ma uprawnienia do zarządzania komputerem `Contoso_214`i korzystać z konfiguracji sesji o nazwie `NewAdminsOnly`.

   `Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

4. Sprawdź, czy reguła została utworzona za pomocą `Get-PswaAuthorizationRule` polecenia cmdlet, lub `Test-PswaAuthorizationRule -UserName <domain\user> -ComputerName <computer-name>`

   Na przykład `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

Po skonfigurowaniu reguły autoryzacji, jesteś gotowy autoryzowani użytkownicy będą logować się do konsoli sieci web i rozpocząć korzystanie z programu Windows PowerShell Web Access.

## <a name="custom-deployment"></a>Niestandardowe wdrożenie

Bramę programu Windows PowerShell Web Access można zainstalować na serwerze, na którym jest uruchomiony system Windows Server 2012 R2 lub Windows Server 2012, przy użyciu Dodaj role i funkcje kreatora w Menedżerze serwera.
Po zainstalowaniu programu Windows PowerShell Web Access, należy dostosować konfigurację bramy w Menedżerze usług IIS.

### <a name="install-windows-powershell-web-access-using-the-add-roles-and-features-wizard"></a>Instalowanie przy użyciu funkcji Kreatora dodawania ról i program Windows PowerShell Web Access

1. Jeśli Menedżer serwera jest już otwarty, przejdź do następnego kroku. Jeśli Menedżer serwera nie jest już otwarty, otwórz go, wykonując jedną z następujących czynności.

   - Na pulpicie systemu Windows, uruchom Menedżera serwera, klikając **Menedżera serwera** na pasku zadań systemu Windows.
   - Na Windows **Start** ekranu, kliknij przycisk **Menedżera serwera**.

2. Na **Zarządzaj** menu, kliknij przycisk **Dodaj role i funkcje**.

3. Na **Wybieranie typu instalacji** wybierz **Instalacja oparta na rolach lub oparta na funkcjach**.
   Kliknij przycisk **Dalej**.

4. Na **serwer docelowy wybierz** strony, wybierz serwer z puli serwerów lub wybierz dysk VHD trybu offline. Aby wybrać dysk VHD trybu offline jako serwer docelowy, najpierw wybierz serwer, na którym chcesz zainstalować dysk VHD, a następnie wybierz plik wirtualnego dysku twardego. Aby uzyskać informacje na temat dodawania serwerów do puli serwerów, należy zajrzeć do pomocy Menedżera serwera. Po wybraniu serwera docelowego kliknij **Dalej**.

5. Na **wybierz funkcje** strony kreatora, należy rozwinąć **programu Windows PowerShell**, a następnie wybierz pozycję **programu Windows PowerShell Web Access**.

6. Należy pamiętać, że monit o dodanie wymaganych funkcji, takich jak .NET Framework 4.5 i usługi roli Serwer sieci Web (IIS). Dodaj wymagane funkcje i Kontynuuj.

   > [!NOTE]
   > Instalowanie programu Windows PowerShell Web Access przy użyciu funkcji Kreatora dodawania ról i instaluje serwer sieci Web (IIS), łącznie z przystawki Menedżer usług IIS. Ta przystawka i inne narzędzia do zarządzania usług IIS są instalowane domyślnie, jeśli używasz Kreatora dodawania ról i funkcji. Po zainstalowaniu programu Windows PowerShell Web Access za pomocą poleceń cmdlet programu Windows PowerShell, zgodnie z opisem w poniższej procedurze, narzędzia do zarządzania nie są dodawane domyślnie.

7. Na **Potwierdź wybrane opcje instalacji** strony, jeśli pliki funkcji programu Windows PowerShell Web Access nie są przechowywane na serwerze docelowym, który został wybrany w kroku 4, kliknij **określenie alternatywnej ścieżki źródłowej**i podaj ścieżkę do plików funkcji. W przeciwnym razie kliknij przycisk **zainstalować**.

8. Po kliknięciu **zainstalować**, **postęp instalacji** strony wyświetla postęp instalacji, wyniki i komunikaty, takie jak ostrzeżenia, błędy lub czynności konfiguracyjnych po instalacji, które są wymagane dla programu Windows PowerShell Web Access. Po zainstalowaniu programu Windows PowerShell Web Access, wyświetlany jest monit o przejrzenie pliku readme, który zawiera instrukcje dotyczące konfigurowania podstawowych, jest wymagane dla bramy. Te instrukcje znajdują się również w tym temacie. Ścieżka do pliku readme jest `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>Konfigurowanie bramy

Instrukcje w tej sekcji dotyczą instalowania aplikacji sieci web programu Windows PowerShell Web Access w podkatalogu, a nie w katalogu głównym witryny sieci Web. Ta procedura jest odpowiednikiem Graficznym interfejsem użytkownika akcje wykonywane przez `Install-PswaWebApplication` polecenia cmdlet. Ta sekcja zawiera również instrukcje dotyczące sposobu konfigurowania bramy systemu Windows PowerShell Web Access jako głównej witryny internetowej za pomocą Menedżera usług IIS.

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a>Aby skonfigurować bramę w istniejącej witryny sieci Web za pomocą Menedżera usług IIS

1. Otwórz konsolę Menedżera usług IIS, wykonując jedną z następujących czynności.

   - Na pulpicie systemu Windows, uruchom Menedżera serwera, klikając **Menedżera serwera** na pasku zadań systemu Windows. Na **narzędzia** menu w Menedżerze serwera kliknij **Internet Information Services (IIS) Manager**.
   - Na Windows **Start** ekranu, wpisz dowolną część nazwy **Internet Information Services (IIS) Manager**. Kliknij skrót, gdy jest on wyświetlany w **aplikacje** wyników.

2. Utwórz nową pulę aplikacji dla programu Windows PowerShell Web Access. Rozwiń węzeł serwera bramy w okienku drzewa Menedżera usług IIS wybierz **pul aplikacji**i kliknij przycisk **Dodawanie puli aplikacji** w **akcje** okienka.

3. Dodawanie nowej puli aplikacji o nazwie **pswa_pool**, lub podaj inną nazwę. Kliknij przycisk **OK**.

4. W okienku drzewa Menedżera usług IIS, rozwiń węzeł serwera, na którym zainstalowany jest program Windows PowerShell Web Access, aż do **witryn** folder jest widoczny. Wybierz **witryn** folderu.

5. Kliknij prawym przyciskiem myszy witrynę sieci Web (na przykład **domyślna witryna sieci Web**), do której chcesz dodać witrynę sieci Web programu Windows PowerShell Web Access, a następnie kliknij przycisk **Add Application**.

6. W **Alias** pola, wpisz pswa lub dowolny inny alias. Ten alias będzie nazwą katalogu wirtualnego. Na przykład **pswa** następujący adres URL reprezentuje alias określony w tym kroku: `https://<server-name>/pswa`.

7. W **puli aplikacji** wybierz pulę aplikacji, który został utworzony w kroku 3.

8. W **ścieżkę fizyczną** pola, przejdź do lokalizacji aplikacji. Można użyć domyślnej lokalizacji `$env:windir/Web/PowerShellWebAccess/wwwroot`. Kliknij przycisk **OK**.

9. Wykonaj kroki opisane w procedurze [skonfigurować certyfikat SSL w Menedżerze usług IIS](#to-configure-an-ssl-certificate-in-iis-manager) w tym temacie.

10. ![](images/SecurityNote.jpeg) Opcjonalny krok dotyczący zabezpieczeń:

    Z witryną sieci Web, dla wybranego w okienku drzewa, kliknij dwukrotnie **ustawienia protokołu SSL** w okienku zawartości.
    Wybierz **Wymagaj protokołu SSL**, a następnie w polu **akcje** okienku kliknij **Zastosuj**. Opcjonalnie w **ustawienia protokołu SSL** okienku możesz wymagać od użytkowników łączących się z witryny sieci Web programu Windows PowerShell Web Access posiadania certyfikatów klienta. Certyfikaty klienta pomagają zweryfikować tożsamość użytkownika urządzenia klienckiego. Aby uzyskać więcej informacji na temat jak wymóg posiadania certyfikatów klienta może zwiększyć bezpieczeństwo programu Windows PowerShell Web Access, zobacz [reguły autoryzacji i zabezpieczeń funkcji programu Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md) w tym przewodniku.

11. Otwórz sesję przeglądarki na urządzeniu klienckim. Aby uzyskać więcej informacji o obsługiwanych przeglądarkach i urządzeniach, zobacz [przeglądarki i urządzenia klienckiego, które obsługują](#browser-and-client-device-support) w tym temacie.

12. Otwórz nową witrynę sieci Web programu Windows PowerShell Web Access **https://\<*serwer bramy*\>/pswa**.

    Przeglądarki powinien być wyświetlany w konsoli programu Windows PowerShell Web Access logowania strony.

    > [!NOTE]
    > Nie można zalogować się do momentu użytkownikom udzielono dostępu do witryny internetowej przez dodanie reguł autoryzacji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie restrykcyjnej reguły autoryzacji](#configure-a-restrictive-authorization-rule), w tym temacie i [reguły autoryzacji i zabezpieczeń funkcji programu Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

13. W sesji środowiska Windows PowerShell, która została otwarta z podwyższonym poziomem uprawnień użytkownika (Uruchom jako Administrator), uruchom następujący skrypt, w którym *nazwa_puli_aplikacji* reprezentuje nazwę puli aplikacji, który został utworzony w kroku 3 Aby udzielić tej puli aplikacji uprawnień dostępu do pliku autoryzacji.

    ```powershell
    $applicationPoolName = "<application_pool_name>"
    $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
    c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null
    ```

    Aby wyświetlić istniejące prawa dostępu do pliku autoryzacji, uruchom następujące polecenie:

    ```powershell
    c:\windows\system32\icacls.exe $authorizationFile
    ```

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a>Aby użyć Menedżera usług IIS do skonfigurowania bramy jako głównej witryny internetowej za pomocą certyfikatu testu

1. Otwórz konsolę Menedżera usług IIS, wykonując jedną z następujących czynności.

   - Na pulpicie systemu Windows, uruchom Menedżera serwera, klikając **Menedżera serwera** na pasku zadań systemu Windows. Na **narzędzia** menu w Menedżerze serwera kliknij **Internet Information Services (IIS) Manager**.
   - Na Windows **Start** ekranu, wpisz dowolną część nazwy **Internet Information Services (IIS) Manager**. Kliknij skrót, gdy jest on wyświetlany w **aplikacje** wyników.

1. W okienku drzewa Menedżera usług IIS, rozwiń węzeł serwera, na którym zainstalowany jest program Windows PowerShell Web Access, aż do **witryn** folder jest widoczny. Wybierz **witryn** folderu.

1. W **akcje** okienku kliknij **Dodawanie witryny sieci Web**.

1. Wpisz nazwę witryny sieci Web, takie jak **programu Windows PowerShell Web Access**.

1. Pula aplikacji jest tworzona automatycznie dla nowej witryny sieci Web. Aby użyć innej puli aplikacji, kliknij **wybierz** można wybrać pulę aplikacji do skojarzenia z nową witrynę sieci Web. Wybierz alternatywną pulę aplikacji w **Wybieranie puli aplikacji** okno dialogowe, a następnie kliknij przycisk **OK**.

1. W **ścieżkę fizyczną** tekstu, przejdź do % windir%/Web/PowerShellWebAccess/wwwroot.

1. W **typu** pole **powiązanie** wybierz opcję **https**.

1. Przypisz numer portu witryny sieci Web, który nie jest już używany przez inną witrynę lub aplikację.
   Aby zlokalizować otwarte porty, można uruchomić **netstat** polecenia w oknie wiersza polecenia. Domyślny numer portu to 443.

   Zmienić port domyślny, jeśli inna witryna internetowa korzysta już z 443 lub mają inne względy bezpieczeństwa przemawiające za zmianą numeru portu. Jeśli z wybranego portu korzysta inna witryna internetowa, która jest uruchomiona na serwerze bramy, po kliknięciu zostanie wyświetlone ostrzeżenie **OK** w **Dodawanie witryny sieci Web** okno dialogowe. Aby uruchomić program Windows PowerShell Web Access, należy użyć nieużywanego portu.

1. Opcjonalnie, w razie potrzeby w swojej organizacji, określ nazwę hosta pasującą do organizacji i użytkowników, takie jak **`www.contoso.com`**. Kliknij przycisk **OK**.

1. Zwiększyć bezpieczeństwo środowiska produkcyjnego zaleca się prawidłowego certyfikatu, który został podpisany przez urząd certyfikacji. Musisz podać certyfikat SSL, ponieważ użytkownicy mogą łączyć się tylko z programu Windows PowerShell Web Access za pośrednictwem witryny internetowej HTTPS. Zobacz [skonfigurować certyfikat SSL w Menedżerze usług IIS](#to-configure-an-ssl-certificate-in-iis-manager) w tym temacie, aby uzyskać więcej informacji o sposobie uzyskiwania certyfikatu.

1. Kliknij przycisk **OK** zamknąć **Dodawanie witryny sieci Web** okno dialogowe.

1. W sesji środowiska Windows PowerShell, która została otwarta z podwyższonym poziomem uprawnień użytkownika (Uruchom jako Administrator), uruchom następujący skrypt, w którym _nazwa_puli_aplikacji_ reprezentuje nazwę puli aplikacji, który został utworzony w kroku 4, Aby udzielić tej puli aplikacji uprawnień dostępu do pliku autoryzacji.

   ```powershell
   $applicationPoolName = "<application_pool_name>"
   $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
   c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null
   ```

   Aby wyświetlić istniejące prawa dostępu do pliku autoryzacji, uruchom następujące polecenie:

   ```powershell
   c:\windows\system32\icacls.exe $authorizationFile
   ```

1. Z wybraniu nowej witryny internetowej w okienku drzewa Menedżera usług IIS, kliknij przycisk **Start** w **akcje** okienko, aby uruchomić witrynę internetową.

1. Otwórz sesję przeglądarki na urządzeniu klienckim. Aby uzyskać więcej informacji o obsługiwanych przeglądarkach i urządzeniach, zobacz [przeglądarki i urządzenia klienckiego, które obsługują](#browser-and-client-device-support) w tym dokumencie.

1. Otwórz nową witrynę sieci Web programu Windows PowerShell Web Access.

   Ponieważ główna witryna internetowa wskazuje folder programu Windows PowerShell Web Access, przeglądarce powinna zostać wyświetlona strona logowania programu Windows PowerShell Web Access, po otwarciu `https://<gateway_server_name>`. Nie należy dodać **/pswa** do adresu URL.

   > [!NOTE]
   > Nie można zalogować się do momentu użytkownikom udzielono dostępu do witryny internetowej przez dodanie reguł autoryzacji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie restrykcyjnej reguły autoryzacji](#configure-a-restrictive-authorization-rule), w tym temacie i [reguły autoryzacji i zabezpieczeń funkcji programu Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configuring-a-restrictive-authorization-rule"></a>Konfigurowanie restrykcyjnej reguły autoryzacji

Po zainstalowaniu programu Windows PowerShell Web Access, a brama jest skonfigurowana, użytkownicy mogą otwierać strony logowania w przeglądarce, ale nie można zalogować do momentu administratora programu Windows PowerShell Web Access jawnego przydzielenia im dostępu. Kontrola dostępu w programie Windows PowerShell Web Access odbywa się przy użyciu zestawu poleceń cmdlet Windows PowerShell opisanych w poniższej tabeli. Do dodawania lub zarządzanie regułami autoryzacji jest nie porównywalny graficzny interfejs użytkownika. Aby uzyskać szczegółowe informacje o poleceniach cmdlet programu Windows PowerShell Web Access, zobacz tematy dokumentacja poleceń cmdlet, [polecenia cmdlet programu Windows PowerShell Web Access](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Aby uzyskać więcej szczegółów na temat reguł autoryzacji programu Windows PowerShell Web Access i zabezpieczeń, zobacz [reguły autoryzacji i zabezpieczeń funkcji programu Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="adding-a-restrictive-authorization-rule"></a>Dodawanie restrykcyjnej reguły autoryzacji

1. Wykonaj jedną z następujących czynności, aby otworzyć sesję środowiska Windows PowerShell z podwyższonym poziomem uprawnień użytkownika.

   - Na pulpicie systemu Windows kliknij prawym przyciskiem myszy **środowiska Windows PowerShell** na pasku zadań, a następnie kliknij przycisk **Uruchom jako Administrator**.
   - Na Windows **Start** ekranu, kliknij prawym przyciskiem myszy **programu Windows PowerShell**, a następnie kliknij przycisk **Uruchom jako Administrator**.

1. ![Uwaga dotycząca zabezpieczeń](images/SecurityNote.jpeg) Krok opcjonalny, umożliwiający ograniczenie dostępu użytkowników za pomocą konfiguracji sesji:

   Sprawdź, czy konfiguracje sesji, których chcesz użyć w regułach już istnieją. Jeśli one nie zostały jeszcze utworzone, skorzystaj z instrukcji tworzenia konfiguracji sesji w [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configurations).

1. Wpisz następujące polecenie, a następnie naciśnij klawisz **Enter**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Ta reguła autoryzacji zezwala określonemu użytkownikowi na dostęp do jednego komputera w sieci, do których zwykle mają dostęp z uprawnieniami do konfiguracji określonej sesji, które są ograniczone do użytkownika "™ s typowe potrzeby skrypty i polecenia cmdlet.

   W poniższym przykładzie użytkownik o nazwie `JSmith` w `Contoso` domeny ma uprawnienia do zarządzania komputerem `Contoso_214`i korzystać z konfiguracji sesji o nazwie `NewAdminsOnly`.

   `Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

1. Sprawdź, czy reguła została utworzona za pomocą `Get-PswaAuthorizationRule` polecenia cmdlet, lub `Test-PswaAuthorizationRule -UserName '<domain\user>' -ComputerName <computer-name>`.

   Na przykład `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

   Po skonfigurowaniu reguły autoryzacji, jesteś gotowy autoryzowani użytkownicy będą logować się do konsoli sieci web i rozpocząć korzystanie z programu Windows PowerShell Web Access.

## <a name="configure-a-genuine-certificate"></a>Konfigurowanie oryginalnego certyfikatu

Dla zabezpieczonym środowisku produkcyjnym zawsze używaj prawidłowego certyfikatu SSL, który został podpisany przez urząd certyfikacji (CA). Procedura w tej sekcji opisano, jak uzyskać i zastosować ważnego certyfikatu SSL od urzędu certyfikacji.

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a>Aby skonfigurować certyfikat SSL w Menedżerze usług IIS

1. W okienku drzewa Menedżera usług IIS wybierz serwer, na którym jest zainstalowany program Windows PowerShell Web Access.

1. W okienku zawartości kliknij dwukrotnie **certyfikaty serwera**.

1. W **akcje** okienko, wykonaj jedną z następujących czynności. Aby uzyskać więcej informacji na temat konfigurowania certyfikatów serwera w usługach IIS, zobacz [Konfigurowanie certyfikatów serwera w usługach IIS 7](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).

   - Kliknij przycisk **zaimportować** Aby zaimportować istniejący, prawidłowy certyfikat z lokalizacji w sieci.
   - Kliknij przycisk **Utwórz żądanie certyfikatu** żądania certyfikatu od urzędu certyfikacji, takich jak [VeriSign](https://www.verisign.com/), [Thawte](https://www.thawte.com/), lub [GeoTrust](https://www.geotrust.com/). Nazwa pospolita certyfikatu musi być zgodna z nagłówkiem hosta w żądaniu.

     Na przykład, jeśli przeglądarka klienta żąda `http://www.contoso.com/`, a następnie nazwę pospolitą również musi być `http://www.contoso.com/`. Jest to najbardziej bezpieczna i zalecana opcja umożliwiająca dostarczanie bramę programu Windows PowerShell Web Access przy użyciu certyfikatu.

   - Kliknij przycisk **Utwórz certyfikat z podpisem własnym** do utworzenia certyfikatu można użyć od razu i podpisać później przez urząd certyfikacji w razie potrzeby. Określ przyjazną nazwę certyfikatu z podpisem własnym, taki jak **programu Windows PowerShell Web Access**. Ta opcja jest uważana za niebezpieczną i jest zalecana tylko na potrzeby prywatnego środowiska testowego.

1. Po utworzeniu lub otrzymaniu certyfikatu, wybierz witrynę sieci Web, do którego zastosowano certyfikatu (na przykład **domyślna witryna sieci Web**) okienku drzewa Menedżera usług IIS, a następnie kliknij przycisk **powiązania** w **Akcje** okienka.

1. W **Dodawanie powiązania witryny** okna dialogowego Dodaj **https** wiązanie dla danej lokacji, jeśli nie jest już wyświetlany. Jeśli nie używasz certyfikatu z podpisem własnym, należy określić nazwę hosta z kroku 3 tej procedury. Jeśli używasz certyfikatu z podpisem własnym, ten krok nie jest wymagane.

1. Wybierz certyfikat uzyskany lub utworzony w kroku 3 tej procedury, a następnie kliknij przycisk **OK**.

## <a name="using-the-web-based-windows-powershell-console"></a>Za pomocą konsoli internetowej programu Windows PowerShell

Po zainstalowaniu programu Windows PowerShell Web Access i zakończeniu konfigurowania bramy, zgodnie z opisem w tym temacie, konsoli internetowej programu Windows PowerShell jest gotowe do użycia. Aby uzyskać więcej informacji na temat pobierania pracę w konsoli sieci web, zobacz [za pomocą konsoli programu PowerShell Windows opartej na sieci Web](use-the-web-based-windows-powershell-console.md).

## <a name="see-also"></a>Zobacz też

[Internetowe usługi informacyjne (IIS) 7.0 dokumentacji](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753433(v=ws.10))

[Pomoc Menedżera 7.0 usług IIS](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732664(v=ws.11))

[Konfigurowanie zabezpieczeń serwera sieci Web (IIS 7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731278(v=ws.10))

[Zasoby dotyczące wdrażania protokołu IPsec](/previous-versions/windows/it-pro/windows-server-2003/cc776369(v=ws.10))
