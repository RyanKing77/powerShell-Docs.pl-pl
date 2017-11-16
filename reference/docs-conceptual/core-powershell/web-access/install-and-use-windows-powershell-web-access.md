---
ms.date: 2017-08-23
keywords: polecenia cmdlet programu PowerShell
title: "zainstalować i używać programu windows powershell web access"
ms.openlocfilehash: 63e25fa2b1fc7c0a2b57763e337c25ece17a3296
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/13/2017
---
# <a name="install-and-use-windows-powershell-web-access"></a>Instalowanie programu Windows PowerShell Web Access i korzystanie z niego

Zaktualizowano: 5 listopad 2013 (edytować: 23 sierpnia 2017 r.)

Dotyczy: Windows Server 2012 R2, Windows Server 2012

## <a name="introduction"></a>Wprowadzenie

Windows PowerShell Web Access, wprowadzony po raz pierwszy w systemie Windows Server 2012, działa jak brama programu Windows PowerShell, zapewniając opartych na sieci web konsoli środowiska Windows PowerShell, która jest skierowana na komputerze zdalnym. Umożliwia on informatykom uruchamianie poleceń środowiska Windows PowerShell i skryptów z poziomu konsoli programu Windows PowerShell w przeglądarce sieci web bez programu Windows PowerShell, oprogramowanie do zarządzania zdalnego i instalacja dodatku przeglądarki niezbędne na urządzeniu klienckim. Jest wymagany do uruchamiania konsoli internetowej programu Windows PowerShell jest prawidłowo skonfigurowana brama programu Windows PowerShell Web Access i przeglądarka na urządzeniu klienckim obsługująca język JavaScript i akceptuje pliki cookie.

Przykładami urządzeń klienckich są laptopy, nieprzeznaczone do użytku służbowego komputery osobiste, wypożyczone komputery, tablety, kioski internetowe, komputery z systemami operacyjnymi innymi niż Windows i przeglądarki w telefonach komórkowych. Informatycy mogą wykonywać kluczowe zadania zarządzania na zdalnych serwerach z systemami Windows, korzystając z urządzeń, które mają dostęp do połączenia internetowego i przeglądarki internetowej.

Po pomyślnym bramy instalację i konfigurację użytkownicy można uzyskiwać dostęp do konsoli środowiska Windows PowerShell za pomocą przeglądarki sieci web. Po otwarciu zabezpieczonej witryny sieci Web Windows PowerShell Web Access, mogą uruchamiać konsolę programu Windows PowerShell opartych na sieci web po pomyślnym uwierzytelnieniu.

Windows PowerShell Web Access i konfiguracja jest procesem trzech etapów:

1. [Instalowanie programu Windows PowerShell Web Access](#install-windows-powershell-web-access)
1. [Konfigurowanie bramy](#configure-the-gateway)
1. [Konfigurowanie restrykcyjnej reguły autoryzacji](#configure-a-restrictive-authorization-rule)

Przed zainstalowaniem i skonfigurowaniem programu Windows PowerShell Web Access, firma Microsoft zaleca, aby odczytać całości tego przewodnika, który zawiera instrukcje dotyczące instalowania, zabezpieczania i odinstalowywania programu Windows PowerShell Web Access.
[Za pomocą konsoli programu PowerShell systemu Windows oparte na sieci Web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx) temacie opisano sposób logowania się do konsoli internetowej, a także jej ograniczenia i różnice między konsoli internetowej programu Windows PowerShell i  **PowerShell.exe** konsoli. Użytkownicy końcowi konsoli sieci web należy przeczytać [konsoli programu PowerShell systemu Windows na podstawie użycia sieci Web](use-the-web-based-windows-powershell-console.md), ale nie muszą czytać dalszej części tego przewodnika.

Ten temat nie zawiera szczegółowych wskazówek operacji serwera sieci Web usług IIS; w tym temacie opisano tylko kroki wymagane do skonfigurowania bramy programu Windows PowerShell Web Access. Aby uzyskać więcej informacji na temat konfigurowania i zabezpieczania witryn internetowych w usługach IIS, zobacz zasoby dokumentacji usług IIS w sekcji Zobacz też.

Na poniższym diagramie przedstawiono sposób działania programu Windows PowerShell Web Access.

![Diagram funkcji Windows PowerShell Web Access](images/Windows-PowerShell-Web-Access-diagram.jpg)

## <a name="requirements-for-running-windows-powershell-web-access"></a>Wymagania dotyczące działania programu Windows PowerShell Web Access

Windows PowerShell Web Access wymaga serwera sieci Web (IIS), .NET Framework 4.5 i programu Windows PowerShell 3.0 lub programu Windows PowerShell 4.0 uruchomiony na serwerze, na którym chcesz uruchomić bramy. Windows PowerShell Web Access można zainstalować na serwerze, na którym jest uruchomiony system Windows Server 2012 R2 lub Windows Server 2012 przy użyciu albo Kreatora dodawania ról i funkcji w Menedżerze serwera lub środowiska Windows PowerShell polecenia cmdlet wdrażania Menedżera serwera. Po zainstalowaniu programu Windows PowerShell Web Access za pomocą Menedżera serwera lub jego poleceń wdrażania cmdlet wymagane role i funkcje są automatycznie dodawane jako część procesu instalacji.

Windows PowerShell Web Access umożliwia użytkownikom zdalnym dostęp do komputerów w organizacji za pomocą środowiska Windows PowerShell w przeglądarce sieci web. Windows PowerShell Web Access jest narzędziem do zarządzania wygodnym i zaawansowanym, dostępu do sieci web stanowi zagrożenia bezpieczeństwa, a powinien być skonfigurowany jako bezpieczny sposób. Zalecamy Administratorzy, którzy konfigurują bramę programu Windows PowerShell Web Access za pomocą warstw zabezpieczeń dostępne reguły autoryzacji na podstawie polecenia cmdlet dołączony do programu Windows PowerShell Web Access i zabezpieczeń warstwy, które są dostępne w (serwer sieci Web Usługi IIS) i aplikacje innych producentów. W tej dokumentacji opisano zarówno przykłady niezabezpieczone, które są zalecane tylko dla środowisk testowych, jak również przykłady, które są zalecane w przypadku wdrożeń zabezpieczonych.

## <a name="browser-and-client-device-support"></a>Obsługa przeglądarek i urządzeń klienckich

Windows PowerShell Web Access obsługuje następujące przeglądarki internetowe.
Choć przeglądarki dla urządzeń przenośnych oficjalnie nie są obsługiwane, wiele można uruchomić konsoli internetowej programu Windows PowerShell. Konsola prawdopodobnie działa w innych przeglądarkach, które akceptują pliki cookie i obsługują skrypty języka JavaScript oraz witryny HTTPS, ale nie zostały one oficjalnie przetestowane.

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

## <a name="recommended-quick-deployment"></a>Zalecane szybkiego wdrożenia

Bramę programu Windows PowerShell Web Access można zainstalować na serwerze z systemem Windows Server 2012 R2 lub Windows Server 2012, przy użyciu albo poleceń cmdlet programu Windows PowerShell lub przy użyciu Dodaj role i funkcje kreatora, który jest otwierany z Menedżera serwera. Dla szybką instalację i konfigurację użyj polecenia cmdlet programu Windows PowerShell, zgodnie z opisem w tej sekcji.

1. [Instalowanie programu Windows PowerShell Web Access](#install-Windows-powershell-web-access)
1. [Konfigurowanie bramy](#configure-the-gateway)
1. [Konfigurowanie restrykcyjnej reguły autoryzacji](#configure-a-restrictive-authorization-rule)

### <a name="install-windows-powershell-web-access"></a>Instalowanie programu Windows PowerShell Web Access

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a>Aby zainstalować program Windows PowerShell Web Access za pomocą poleceń cmdlet programu Windows PowerShell

1. Wykonaj jedną z następujących czynności, aby otworzyć sesję środowiska Windows PowerShell z podwyższonym poziomem uprawnień użytkownika.
    - Na pulpicie systemu Windows kliknij prawym przyciskiem myszy **środowiska Windows PowerShell** na pasku zadań, a następnie kliknij przycisk **Uruchom jako Administrator**.
    - W systemie Windows **Start** ekranu, kliknij prawym przyciskiem myszy **programu Windows PowerShell**, a następnie kliknij przycisk **Uruchom jako Administrator**.

    >**![Uwaga](images/note.jpeg) Uwaga** w programie Windows PowerShell 3.0 i 4.0, nie jest konieczne do Zaimportuj moduł poleceń cmdlet Menedżera serwera do sesji środowiska Windows PowerShell, przed uruchomieniem poleceń cmdlet, które są częścią tego modułu. Moduł jest automatycznie importowany podczas pierwszego uruchomienia polecenia cmdlet wchodzącego w skład modułu. Ponadto poleceń cmdlet programu Windows PowerShell nie jest rozróżniana.

1. Wpisz następujące polecenie, a następnie naciśnij klawisz **Enter**, gdzie *nazwa_komputera* reprezentuje komputer zdalny, na którym chcesz zainstalować program Windows PowerShell Web Access, jeśli ma to zastosowanie. Parametr `-Restart` spowoduje automatyczne ponowne uruchomienie serwerów docelowych, jeśli jest to wymagane.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart`

   >**![Uwaga](images/note.jpeg) Uwaga**
   >
   >Domyślnie instalowanie programu Windows PowerShell Web Access za pomocą poleceń cmdlet programu Windows PowerShell nie powoduje dodania narzędzi do zarządzania serwerem sieci Web (IIS). Jeśli chcesz zainstalować narzędzia do zarządzania na tym samym serwerze co brama programu Windows PowerShell Web Access, Dodaj `-IncludeManagementTools` do polecenia instalacji (co zostało opisane w tym kroku). Jeśli zarządzasz witryny sieci Web Windows PowerShell Web Access z komputera zdalnego, zainstaluj przystawkę Menedżer usług IIS przez zainstalowanie [Windows 8.1 Toolsfor administracji zdalnej serwera](http://go.microsoft.com/fwlink/?LinkID=304145) lub [administracji zdalnej serwera Narzędzia dla systemu Windows 8](http://go.microsoft.com/fwlink/p/?LinkID=238560) na komputerze, z którego chcesz zarządzania bramą.
   
   Aby zainstalować role i funkcje na dysku VHD trybu offline, należy dodać parametr `-ComputerName` i parametr `-VHD`. Parametr `-ComputerName` zawiera nazwę serwera, na którym należy zainstalować dysk VHD, a parametr `-VHD` zawiera ścieżkę do pliku dysku VHD na określonym serwerze.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart`

1. Po zakończeniu instalacji sprawdź, czy program Windows PowerShell Web Access zostało zainstalowane na serwerach docelowych, uruchamiając **Get-WindowsFeature** polecenia cmdlet na serwerze docelowym, w konsoli środowiska Windows PowerShell, która została otwarta z podwyższonym poziomem uprawnień użytkownika. Można również sprawdzić, czy Windows PowerShell Web Access został zainstalowany w konsoli Menedżera serwera, wybierając serwer docelowy, na **wszystkie serwery** strony, a następnie wyświetlić **ról i funkcji** Kafelek dla wybranego serwera. Można również przejrzeć plik readme dla programu Windows PowerShell Web Access.

1. Po zainstalowaniu programu Windows PowerShell Web Access, monit o przejrzenie pliku readme, który zawiera instrukcje dotyczące podstawowych instalacji wymagane dla bramy. Te instrukcje instalacji zawarte są również w poniższej sekcji [skonfigurować bramę](#configure-the-gateway). Ścieżka do pliku readme jest **C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt**.

### <a name="configure-the-gateway"></a>Konfigurowanie bramy

**Install-PswaWebApplication** polecenia cmdlet jest szybkie uzyskanie skonfigurowany program Windows PowerShell Web Access. Chociaż w celu zainstalowania certyfikatu SSL z podpisem własnym na potrzeby testowania można dodać parametr `UseTestCertificate` do polecenia cmdlet `Install-PswaWebApplication`, nie jest to bezpieczny sposób. W zabezpieczonym środowisku produkcyjnym zawsze używaj prawidłowego certyfikatu SSL, który został podpisany przez urząd certyfikacji (CA).
Administratorzy mogą zastąpić certyfikat testowy wybranym przez siebie certyfikatem podpisanym przy użyciu konsoli Menedżera usług IIS.

Możesz ukończyć konfigurację aplikacji sieci web programu Windows PowerShell Web Access uruchamiając `Install-PswaWebApplication` polecenia cmdlet lub wykonując kroki konfiguracji graficznego interfejsu użytkownika w Menedżerze usług IIS. Domyślnie to polecenie cmdlet instaluje aplikację sieci web **pswa** (i jego pulę aplikacji, **pswa_pool**) w **domyślnej witryny sieci Web** kontenera, jak pokazano w Menedżerze usług IIS; Jeśli konieczne, możesz wydać polecenie cmdlet, aby zmienić kontener domyślnej witryny aplikacji sieci web. Menedżer usług IIS oferuje opcje konfiguracji, które są dostępne dla aplikacji sieci Web, takie jak zmiana numeru portu lub certyfikatu protokołu Secure Sockets Layer (SSL).

>**![Uwaga dotycząca zabezpieczeń](images/securitynote.jpeg) Uwaga dotycząca zabezpieczeń**
> 
>Zdecydowanie zaleca się, aby administratorzy skonfigurowali bramę do użycia prawidłowego certyfikatu, który został podpisany przez urząd certyfikacji. 

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a>Aby skonfigurować bramę programu Windows PowerShell Web Access z certyfikatem testowym przy użyciu polecenia cmdlet Install-PswaWebApplication

1. Wykonaj jedną z następujących czynności, aby otworzyć sesję środowiska Windows PowerShell.

    - Na pulpicie systemu Windows kliknij prawym przyciskiem myszy **programu Windows PowerShell** na pasku zadań.

    - W systemie Windows **Start** kliknij **programu Windows PowerShell**.

2. Wpisz następujące polecenie, a następnie naciśnij klawisz **Enter**.

    **Polecenia cmdlet Install-PswaWebApplication - UseTestCertificate**

  >**![Uwaga dotycząca zabezpieczeń](images/securitynote.jpeg) Uwaga dotycząca zabezpieczeń**
  >
  >Parametru `UseTestCertificate` należy używać tylko w prywatnym środowisku testowym. W zabezpieczonym środowisku produkcyjnym zaleca się użycie prawidłowego certyfikatu, który został podpisany przez urząd certyfikacji.

Uruchomienie polecenia cmdlet instaluje aplikację sieci web programu Windows PowerShell Web Access w kontenerze domyślna witryna sieci Web usług IIS. Polecenie cmdlet tworzy infrastrukturę niezbędną do uruchomienia programu Windows PowerShell Web Access w domyślnej witrynie sieci Web, `https://<server_name>/pswa`. Aby zainstalować aplikację sieci Web w innej witrynie internetowej, podaj nazwę witryny internetowej przez dodanie parametru `WebSiteName`. Aby zmienić nazwę aplikacji sieci Web (nazwa domyślna to `pswa`), dodaj parametr `WebApplicationName`.

Następujące ustawienia są konfigurowane przez uruchomienie tego polecenia cmdlet. W razie potrzeby można je zmienić ręcznie w konsoli Menedżera usług IIS.

- Path: / pswa
- ApplicationPool: pswa_pool
- EnabledProtocols: http
- PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot

**Przykład**:`Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate`

W tym przykładzie wynikowa witryna internetowa dla programu Windows PowerShell Web Access jest https://\<*nazwa_serwera*\>/myWebApp.

>**![Uwaga](images/note.jpeg) Uwaga** 
> 
>Użytkownicy będą mogli się zalogować dopiero po udzieleniu im dostępu do tej witryny internetowej przez dodanie reguł autoryzacji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie restrykcyjnej reguły autoryzacji](#configure-a-restrictive-authorization-rule) i [reguł autoryzacji i zabezpieczeń funkcje programu Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a>Aby skonfigurować bramę programu Windows PowerShell Web Access z oryginalnym certyfikatem przy użyciu polecenia cmdlet Install-PswaWebApplication i Menedżera usług IIS

1. Wykonaj jedną z następujących czynności, aby otworzyć sesję środowiska Windows PowerShell.

    - Na pulpicie systemu Windows kliknij prawym przyciskiem myszy **programu Windows PowerShell** na pasku zadań.

    - W systemie Windows **Start** kliknij **programu Windows PowerShell**.

2. Wpisz następujące polecenie, a następnie naciśnij klawisz **Enter**.

    **Polecenia cmdlet Install-PswaWebApplication**

    Następujące ustawienia bramy są konfigurowane przez uruchomienie tego polecenia cmdlet.
    W razie potrzeby można je zmienić ręcznie w konsoli Menedżera usług IIS.
    Można również określić wartości dla parametrów `WebsiteName` i `WebApplicationName` polecenia cmdlet `Install-PswaWebApplication`.

    - Path: / pswa

    - ApplicationPool: pswa_pool

    - EnabledProtocols: http

    - PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot

3. Otwórz konsolę Menedżera usług IIS, wykonując jedną z następujących czynności.

    - Na pulpicie systemu Windows, uruchom Menedżera serwera, klikając **Menedżera serwera** na pasku zadań systemu Windows. Na **narzędzia** menu w Menedżerze serwera kliknij **Internet Information Services (IIS) Manager**.

    - W systemie Windows **Start** kliknij **Menedżera serwera**.

4. W okienku drzewa Menedżera usług IIS, rozwiń węzeł serwera, na którym zainstalowany jest program Windows PowerShell Web Access do **witryny** będzie widoczny folder. Rozwiń węzeł **witryny** folderu.

5. Wybierz witrynę internetową, w którym zainstalowano aplikację sieci web programu Windows PowerShell Web Access. W **akcje** okienku, kliknij przycisk **powiązania**.

6. W **powiązania witryny** okno dialogowe, kliknij przycisk **Dodaj**.

7. W **Dodawanie powiązania witryny** okna dialogowego, **typu** pól, zaznacz **https**.

8. W **certyfikat SSL** wybierz Twój podpisany certyfikat z listy rozwijanej. Kliknij przycisk **OK**. Zobacz [skonfigurować certyfikat SSL w Menedżerze usług IIS](#to-configure-an-ssl-certificate-in-iis-Manager) w tym temacie, aby uzyskać więcej informacji dotyczących uzyskiwania certyfikatu.

    Aplikacja sieci web programu Windows PowerShell Web Access jest teraz skonfigurowane do korzystania z podpisanego certyfikatu SSL.

    Dostęp do programu Windows PowerShell Web Access, otwierając **https://\<nazwa_serwera\>/pswa** w oknie przeglądarki.

>**![Uwaga](images/note.jpeg) Uwaga** 
> 
>Użytkownicy będą mogli się zalogować dopiero po udzieleniu im dostępu do tej witryny internetowej przez dodanie reguł autoryzacji. 
>Aby uzyskać więcej informacji, zobacz [Konfigurowanie restrykcyjnej reguły autoryzacji](#configure-a-restrictive-authorization-rule), w tym temacie i [reguł autoryzacji i zabezpieczeń funkcje programu Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configure-a-restrictive-authorization-rule"></a>Konfigurowanie restrykcyjnej reguły autoryzacji

Po zainstalowaniu programu Windows PowerShell Web Access i skonfigurować bramy, użytkownik będzie mógł otworzyć stronę logowania w przeglądarce, ale nie można zalogować do momentu administratora programu Windows PowerShell Web Access jawnego przydzielenia im dostępu. Kontrola dostępu programu Windows PowerShell Web Access jest zarządzana przy użyciu zestawu poleceń cmdlet programu Windows PowerShell opisanych w poniższej tabeli. Nie istnieje porównywalny graficzny interfejs użytkownika umożliwiający dodawanie reguł autoryzacji lub zarządzanie nimi. Aby uzyskać szczegółowe informacje o poleceniach cmdlet programu Windows PowerShell Web Access, zobacz tematy dokumentacji polecenia cmdlet, [polecenia cmdlet programu Windows PowerShell Web Access](cmdlets/web-access-cmdlets.md).

Aby uzyskać więcej szczegółów na temat reguł autoryzacji programu Windows PowerShell Web Access i zabezpieczeń, zobacz [reguł autoryzacji i zabezpieczeń funkcje programu Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-add-a-restrictive-authorization-rule"></a>Aby dodać restrykcyjną regułę autoryzacji

1. Wykonaj jedną z następujących czynności, aby otworzyć sesję środowiska Windows PowerShell z podwyższonym poziomem uprawnień użytkownika.

    - Na pulpicie systemu Windows kliknij prawym przyciskiem myszy **środowiska Windows PowerShell** na pasku zadań, a następnie kliknij przycisk **Uruchom jako Administrator**.

    - W systemie Windows **Start** ekranu, kliknij prawym przyciskiem myszy **programu Windows PowerShell**, a następnie kliknij przycisk **Uruchom jako Administrator**.

2. Krok opcjonalny umożliwiający ograniczenie dostępu użytkowników za pomocą konfiguracji sesji: Sprawdź, czy konfiguracje sesji, których chcesz użyć w regułach już istnieją. Jeśli ich nie jeszcze utworzono, skorzystaj z instrukcji tworzenia konfiguracji sesji w [informacje o plikach](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_session_configurations).

3. Wpisz następujące polecenie, a następnie naciśnij klawisz **Enter**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Ta reguła autoryzacji zezwala określonemu użytkownikowi na dostęp do jednego komputera w sieci, do której zwykle mają oni dostęp z dostępem do Konfiguracja określonej sesji, które są ograniczone do typowych skryptów użytkownika i polecenia cmdlet musi.
   
   W poniższym przykładzie użytkownik o nazwie `JSmith` w domenie `Contoso` otrzymuje dostęp umożliwiający zarządzanie komputerem o nazwie `Contoso_214` przy użyciu konfiguracji sesji o nazwie `NewAdminsOnly`.

   `Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

4. Sprawdź, czy reguła została utworzona za pomocą `Get-PswaAuthorizationRule` polecenia cmdlet, lub`Test-PswaAuthorizationRule -UserName <domain\user> -ComputerName <computer-name>`

5. Na przykład `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

Po skonfigurowaniu reguły autoryzacji można przystąpić do autoryzowanych użytkowników zalogować się do konsoli internetowej i rozpocząć korzystanie z programu Windows PowerShell Web Access.

## <a name="custom-deployment"></a>Wdrażanie niestandardowe

Możesz zainstalować bramę programu Windows PowerShell Web Access na serwerze z systemem Windows Server 2012 R2 lub Windows Server 2012 za pomocą funkcji Kreatora dodawania ról i w Menedżerze serwera. Po zainstalowaniu programu Windows PowerShell Web Access, można dostosować konfigurację bramy w Menedżerze usług IIS.

### <a name="install-windows-powershell-web-access"></a>Instalowanie programu Windows PowerShell Web Access

#### <a name="to-install-windows-powershell-web-access-by-using-the-add-roles-and-features-wizard"></a>Aby zainstalować program Windows PowerShell Web Access przy użyciu Kreatora dodawania ról i funkcji

1. Jeśli Menedżer serwera jest już otwarty, przejdź do następnego kroku. Jeśli Menedżer serwera nie jest już otwarty, otwórz go, wykonując jedną z następujących czynności.

    - Na pulpicie systemu Windows, uruchom Menedżera serwera, klikając **Menedżera serwera** na pasku zadań systemu Windows.

    - W systemie Windows **Start** kliknij **Menedżera serwera**.

2. Na **Zarządzaj** menu, kliknij przycisk **Dodaj role i funkcje**.

3. Na **Wybieranie typu instalacji** wybierz **Instalacja roli lub funkcji**. Kliknij przycisk **Dalej**.

4. Na **serwer docelowy wybierz** strony, wybierz serwer z puli serwerów lub wybierz dysk VHD trybu offline. Aby wybrać dysk VHD w trybie offline jako serwer docelowy, najpierw wybierz serwer, na którym należy zainstalować dysk VHD, a następnie wybierz plik dysku VHD. Aby uzyskać informacje o sposobie dodawania serwerów do puli serwerów Zobacz Pomoc Menedżera serwera. Po wybraniu serwera docelowego kliknij **Dalej**.

5. Na **wybierz funkcje** strony kreatora, rozwiń węzeł **programu Windows PowerShell**, a następnie wybierz **programu Windows PowerShell Web Access**.

6. Zostanie wyświetlony monit o dodanie wymaganych funkcji, takich jak środowisko .NET Framework 4.5 oraz usługi ról serwera sieci Web (IIS). Dodaj wymagane funkcje i kontynuuj.

    >**![Uwaga](images/note.jpeg) Uwaga** 
    >
    >Instalowanie programu Windows PowerShell Web Access za pomocą funkcji Kreatora dodawania ról i instaluje serwer sieci Web (IIS), łącznie z przystawki Menedżera usług IIS. Ta przystawka i inne narzędzia do zarządzania usług IIS są instalowane domyślnie, jeśli używasz Kreatora dodawania ról i funkcji. Po zainstalowaniu programu Windows PowerShell Web Access za pomocą poleceń cmdlet programu Windows PowerShell, zgodnie z opisem w poniższej procedurze, narzędzia do zarządzania nie są dodawane domyślnie.

7. Na **Potwierdź wybrane opcje instalacji** strony, jeśli pliki funkcji programu Windows PowerShell Web Access nie są przechowywane na serwerze docelowym, które wybrano w kroku 4, kliknij **określenie alternatywnej ścieżki źródłowej**i podaj ścieżkę do plików funkcji. W przeciwnym razie kliknij przycisk **zainstalować**.

8. Po kliknięciu **zainstalować**, **postęp instalacji** zostanie wyświetlona strona postępu instalacji, wyniki i komunikaty, takie jak ostrzeżenia, niepowodzenia lub czynności konfiguracyjnych po instalacji, które są wymagany dla programu Windows PowerShell Web Access. Po zainstalowaniu programu Windows PowerShell Web Access, monit o przejrzenie pliku readme, który zawiera instrukcje dotyczące podstawowych instalacji wymagane dla bramy. Te instrukcje znajdują się również w tym temacie. Ścieżka do pliku readme jest `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>Konfigurowanie bramy

Instrukcje w tej sekcji dotyczą instalowania aplikacji sieci web programu Windows PowerShell Web Access w podkatalogu, a nie w katalogu głównym witryny sieci Web. Ta procedura to oparta na graficznym interfejsie użytkownika wersja działań wykonywanych przez polecenie cmdlet `Install-PswaWebApplication`. Ta sekcja zawiera również instrukcje dotyczące sposobu konfigurowania bramy systemu Windows PowerShell Web Access jako głównej witryny internetowej za pomocą Menedżera usług IIS.

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a>Aby użyć Menedżera usług IIS do skonfigurowania bramy w istniejącą witrynie internetowej

1. Otwórz konsolę Menedżera usług IIS, wykonując jedną z następujących czynności.

    - Na pulpicie systemu Windows, uruchom Menedżera serwera, klikając **Menedżera serwera** na pasku zadań systemu Windows. Na **narzędzia** menu w Menedżerze serwera kliknij **Internet Information Services (IIS) Manager**.

    - W systemie Windows **Start** ekranu, wpisz dowolną część nazwy **Internet Information Services (IIS) Manager**. Kliknij skrót jest wyświetlany w **aplikacji** wyników.

2. Utwórz nową pulę aplikacji dla programu Windows PowerShell Web Access. Rozwiń węzeł serwera bramy w okienku drzewa Menedżera usług IIS wybierz **pul aplikacji**i kliknij przycisk **Dodawanie puli aplikacji** w **akcje** okienka.

3. Dodaj nową pulę aplikacji o nazwie **pswa_pool**, lub podaj inną nazwę. Kliknij przycisk **OK**.

4. W okienku drzewa Menedżera usług IIS, rozwiń węzeł serwera, na którym zainstalowany jest program Windows PowerShell Web Access do **witryny** będzie widoczny folder. Wybierz **witryny** folderu.

5. Kliknij prawym przyciskiem myszy witrynę sieci Web (na przykład **domyślna witryna sieci Web**), do której chcesz dodać witrynę sieci Web Windows PowerShell Web Access, a następnie kliknij przycisk **Dodawanie aplikacji**.

6. W **Alias** pola, wpisz pswa lub dowolny inny alias. Ten alias będzie nazwą katalogu wirtualnego. Na przykład **pswa** następujący adres URL reprezentuje alias określony w tym kroku: **https://\<nazwa serwera\>/pswa**.

7. W **puli aplikacji** wybierz pulę aplikacji, który został utworzony w kroku 3.

8. W **ścieżka fizyczna** przejdź do lokalizacji aplikacji. Możesz użyć domyślnej lokalizacji: %windir%/Web/PowerShellWebAccess/wwwroot. Kliknij przycisk **OK**.

9. Wykonaj kroki procedury, aby skonfigurować certyfikat SSL w usługach IIS manager](#to-configure-an-ssl-certificate-in-iis-Manager) w tym temacie.

10. ![](images/SecurityNote.jpeg)Opcjonalny krok dotyczący zabezpieczeń:

    Z witryny sieci Web, dla wybranego w okienku drzewa, kliknij dwukrotnie **ustawienia protokołu SSL** w okienku zawartości. Wybierz **Wymagaj protokołu SSL**, a następnie w **akcje** okienku, kliknij przycisk **Zastosuj**. Opcjonalnie w **ustawienia protokołu SSL** okienku można wymagać posiadania certyfikatów klienta użytkowników łączących się z witryny sieci Web Windows PowerShell Web Access. Certyfikaty klienta pomagają zweryfikować tożsamość użytkownika urządzenia klienckiego. Aby uzyskać więcej informacji na temat jak wymóg posiadania certyfikatów klienta może zwiększyć bezpieczeństwo programu Windows PowerShell Web Access, zobacz [reguł autoryzacji i zabezpieczeń funkcje programu Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md) w tym przewodniku.

11. Otwórz sesję przeglądarki na urządzeniu klienckim. Aby uzyskać więcej informacji o obsługiwanych przeglądarkach i urządzeniach, zobacz [przeglądarki i urządzenia klienta obsługuje](#browser-and-client-device-support) w tym temacie.

12. Otwórz nową witrynę sieci Web Windows PowerShell Web Access  **https://\<*nazwa serwera bramy*\>/pswa**.

    Przeglądarki powinien być wyświetlany Windows PowerShell Web Access konsoli strony logowania.

    >**![Uwaga](images/note.jpeg) Uwaga** 
    > 
    >Użytkownicy będą mogli się zalogować dopiero po udzieleniu im dostępu do tej witryny internetowej przez dodanie reguł autoryzacji. 
    >Aby uzyskać więcej informacji, zobacz [Konfigurowanie restrykcyjnej reguły autoryzacji](#configure-a-restrictive-authorization-rule), w tym temacie i [reguł autoryzacji i zabezpieczeń funkcje programu Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

13. W sesji środowiska Windows PowerShell, która została otwarta z podwyższonym poziomem uprawnień użytkownika (Uruchom jako Administrator), uruchom następujący skrypt, w którym *nazwa_puli_aplikacji* reprezentuje nazwę puli aplikacji, który został utworzony w kroku 3, Aby udzielić tej puli aplikacji uprawnień dostępu do pliku autoryzacji.

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    Aby wyświetlić istniejące prawa dostępu do pliku autoryzacji, uruchom następujące polecenie:

        c:\windows\system32\icacls.exe $authorizationFile

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a>Aby użyć Menedżera usług IIS do skonfigurowania bramy jako głównej witryny internetowej przy użyciu certyfikatu testowego

1. Otwórz konsolę Menedżera usług IIS, wykonując jedną z następujących czynności.

    - Na pulpicie systemu Windows, uruchom Menedżera serwera, klikając **Menedżera serwera** na pasku zadań systemu Windows. Na **narzędzia** menu w Menedżerze serwera kliknij **Internet Information Services (IIS) Manager**.

    - W systemie Windows **Start** ekranu, wpisz dowolną część nazwy **Internet Information Services (IIS) Manager**. Kliknij skrót jest wyświetlany w **aplikacji** wyników.

2. W okienku drzewa Menedżera usług IIS, rozwiń węzeł serwera, na którym zainstalowany jest program Windows PowerShell Web Access do **witryny** będzie widoczny folder. Wybierz **witryny** folderu.

3. W **akcje** okienku, kliknij przycisk **Dodawanie witryny sieci Web**.

4. Wpisz nazwę witryny sieci Web, takich jak **programu Windows PowerShell Web Access**.

5. Dla nowej witryny internetowej zostanie automatycznie utworzona pula aplikacji. Aby użyć innej puli aplikacji, kliknij przycisk **wybierz** można wybrać pulę aplikacji do skojarzenia z nowej witryny sieci Web. Wybierz alternatywną pulę aplikacji w **Wybieranie puli aplikacji** , a następnie kliknij przycisk **OK**.

6. W **ścieżka fizyczna** tekst pola, przejdź do %*windir*% / Web/PowerShellWebAccess/wwwroot.

7. W **typu** pole **powiązanie** wybierz opcję **https**.

8. Przypisz do witryny internetowej numer portu, który nie jest jeszcze używany przez inną witrynę lub aplikację. Aby zlokalizować otwarte porty, można uruchomić **netstat** polecenie w oknie wiersza polecenia. Domyślny numer portu to 443.

    Zmień domyślny port, jeśli inna witryna internetowa korzysta już z portu 443 lub jeśli istnieją inne względy bezpieczeństwa przemawiające za zmianą numeru portu. Jeśli z wybranego portu korzysta inna witryna sieci Web, która jest uruchomiona na serwerze bramy, wyświetlane jest ostrzeżenie, po kliknięciu **OK** w **Dodawanie witryny sieci Web** okno dialogowe. Aby uruchomić program Windows PowerShell Web Access, należy użyć nieużywanego portu.

9. Opcjonalnie w razie potrzeby dla Twojej organizacji, określ nazwę hosta pasującą do organizacji i użytkownikach, takich jak **www.contoso.com**. Kliknij przycisk **OK**.

10. Aby zwiększyć bezpieczeństwo środowiska produkcyjnego, zdecydowanie zaleca się użycie prawidłowego certyfikatu, który został podpisany przez urząd certyfikacji. Należy podać certyfikat SSL, ponieważ użytkownicy można połączyć tylko Windows PowerShell Web Access za pośrednictwem protokołu HTTPS, witryny sieci Web. Zobacz [skonfigurować certyfikat SSL w Menedżerze usług IIS](#to-configure-an-ssl-certificate-in-iis-Manager) w tym temacie, aby uzyskać więcej informacji dotyczących uzyskiwania certyfikatu.

11. Kliknij przycisk **OK** zamknąć **Dodawanie witryny sieci Web** okno dialogowe.

12. W sesji środowiska Windows PowerShell, która została otwarta z podwyższonym poziomem uprawnień użytkownika (Uruchom jako Administrator), uruchom następujący skrypt, w którym *nazwa_puli_aplikacji* reprezentuje nazwę puli aplikacji, która została utworzona w kroku 4, Aby udzielić tej puli aplikacji uprawnień dostępu do pliku autoryzacji.

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    Aby wyświetlić istniejące prawa dostępu do pliku autoryzacji, uruchom następujące polecenie:

        c:\windows\system32\icacls.exe $authorizationFile

13. Nowej witryny internetowej, w okienku drzewa Menedżera usług IIS, kliknij przycisk **Start** w **akcje** okienko, aby uruchomić witrynę internetową.

14. Otwórz sesję przeglądarki na urządzeniu klienckim. Aby uzyskać więcej informacji o obsługiwanych przeglądarkach i urządzeniach, zobacz [przeglądarki i urządzenia klienta obsługuje](#browser-and-client-device-support) w tym dokumencie.

15. Otwórz nową witrynę sieci Web Windows PowerShell Web Access.

    Ponieważ główna witryna internetowa wskazuje folder programu Windows PowerShell Web Access, przeglądarce powinna zostać wyświetlona strona logowania programu Windows PowerShell Web Access po otwarciu  **https://\<*nazwa_serwera_bramy* \>**. Należy nie trzeba dodawać **/pswa** do adresu URL.

    >**![Uwaga](images/note.jpeg) Uwaga** 
    > 
    >Użytkownicy będą mogli się zalogować dopiero po udzieleniu im dostępu do tej witryny internetowej przez dodanie reguł autoryzacji. 
    >Aby uzyskać więcej informacji, zobacz [Konfigurowanie restrykcyjnej reguły autoryzacji](#configure-a-restrictive-authorization-rule), w tym temacie i [reguł autoryzacji i zabezpieczeń funkcje programu Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configure-a-restrictive-authorization-rule"></a>Konfigurowanie restrykcyjnej reguły autoryzacji

Po zainstalowaniu programu Windows PowerShell Web Access i skonfigurować bramy, użytkownik będzie mógł otworzyć stronę logowania w przeglądarce, ale nie można zalogować do momentu administratora programu Windows PowerShell Web Access jawnego przydzielenia im dostępu. Kontrola dostępu programu Windows PowerShell Web Access jest zarządzana przy użyciu zestawu poleceń cmdlet programu Windows PowerShell opisanych w poniższej tabeli. Nie istnieje porównywalny graficzny interfejs użytkownika umożliwiający dodawanie reguł autoryzacji lub zarządzanie nimi. Aby uzyskać szczegółowe informacje o poleceniach cmdlet programu Windows PowerShell Web Access, zobacz tematy dokumentacji polecenia cmdlet, [polecenia cmdlet programu Windows PowerShell Web Access](cmdlets/web-access-cmdlets.md).

Aby uzyskać więcej szczegółów na temat reguł autoryzacji programu Windows PowerShell Web Access i zabezpieczeń, zobacz [reguł autoryzacji i zabezpieczeń funkcje programu Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-add-a-restrictive-authorization-rule"></a>Aby dodać restrykcyjną regułę autoryzacji

1. Wykonaj jedną z następujących czynności, aby otworzyć sesję środowiska Windows PowerShell z podwyższonym poziomem uprawnień użytkownika.

    - Na pulpicie systemu Windows kliknij prawym przyciskiem myszy **środowiska Windows PowerShell** na pasku zadań, a następnie kliknij przycisk **Uruchom jako Administrator**.

    - W systemie Windows **Start** ekranu, kliknij prawym przyciskiem myszy **programu Windows PowerShell**, a następnie kliknij przycisk **Uruchom jako Administrator**.

2. ![Uwaga dotycząca zabezpieczeń](images/SecurityNote.jpeg) Krok opcjonalny, umożliwiający ograniczenie dostępu użytkowników za pomocą konfiguracji sesji:

    Sprawdź, czy konfiguracje sesji, których chcesz użyć w regułach, już istnieją. Jeśli ich nie jeszcze utworzono, skorzystaj z instrukcji tworzenia konfiguracji sesji w [informacje o plikach](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_session_configurations).

3. Wpisz następujące polecenie, a następnie naciśnij klawisz **Enter**.

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    Ta reguła autoryzacji zezwala określonemu użytkownikowi na dostęp do jednego komputera w sieci, do których zwykle mają dostęp z dostępem do Konfiguracja określonej sesji, które są ograniczone do użytkownika "™ s typowe potrzeby skryptów i polecenia cmdlet. 
    
    W poniższym przykładzie użytkownik o nazwie `JSmith` w domenie `Contoso` otrzymuje dostęp umożliwiający zarządzanie komputerem o nazwie `Contoso_214` przy użyciu konfiguracji sesji o nazwie `NewAdminsOnly`.

        Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4. Sprawdź, czy reguła została utworzona za pomocą `Get-PswaAuthorizationRule` polecenia cmdlet, lub `Test-PswaAuthorizationRule -UserName '<domain\user>' -ComputerName <computer-name>`. 

    Na przykład `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

Po skonfigurowaniu reguły autoryzacji można przystąpić do autoryzowanych użytkowników zalogować się do konsoli internetowej i rozpocząć korzystanie z programu Windows PowerShell Web Access.

## <a name="configure-a-genuine-certificate"></a>Konfigurowanie oryginalnego certyfikatu

W bezpiecznym środowisku produkcyjnym zawsze używaj prawidłowego certyfikatu SSL, który został podpisany przez urząd certyfikacji (CA). W procedurze w tej sekcji opisano sposób uzyskiwania prawidłowego certyfikatu SSL z urzędu certyfikacji i stosowania go.

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a>Aby skonfigurować certyfikat SSL w Menedżerze usług IIS

1. W okienku drzewa Menedżera usług IIS wybierz serwer, na którym jest zainstalowany program Windows PowerShell Web Access.

2. W okienku zawartości kliknij dwukrotnie **certyfikaty serwera**.

3. W **akcje** okienko, wykonaj jedną z następujących czynności. Aby uzyskać więcej informacji na temat konfigurowania certyfikatów serwera w usługach IIS, zobacz [Konfigurowanie certyfikatów serwerów w usługach IIS 7](https://technet.microsoft.com/library/cc732230.aspx).

    - Kliknij przycisk **zaimportować** Aby zaimportować istniejący, prawidłowy certyfikat z lokalizacji w sieci.

    - Kliknij przycisk **Utwórz żądanie certyfikatu** Aby zażądać certyfikatu od urzędu certyfikacji, takich jak [VeriSign](http://www.verisign.com/), [Thawte](https://www.thawte.com/), lub [GeoTrust](https://www.geotrust.com/). Nazwa pospolita certyfikatu musi być zgodna z nagłówkiem hosta w żądaniu.

      Na przykład jeśli przeglądarka klienta żąda adresu http://www.contoso.com/, nazwą pospolitą również musi być http://www.contoso.com/. Jest to najbardziej bezpieczna i zalecana opcja używania bramy systemu Windows PowerShell Web Access przy użyciu certyfikatu.

    - Kliknij przycisk **Utwórz certyfikat z podpisem własnym** można utworzyć certyfikatu można użyć od razu i podpisać później przez urząd certyfikacji w razie potrzeby. Określ przyjazną nazwę certyfikatu z podpisem własnym, takich jak **programu Windows PowerShell Web Access**. Ta opcja jest uważana za niebezpieczną i jest zalecana tylko na potrzeby prywatnego środowiska testowego.

4. Po utworzeniu lub otrzymaniu certyfikatu, wybierz witrynę internetową, do którego zastosowano certyfikatu (na przykład **domyślna witryna sieci Web**) w okienku drzewa Menedżera usług IIS, a następnie kliknij przycisk **powiązania** w **Akcje** okienka.

5. W **Dodawanie powiązania witryny** okno dialogowe Dodaj **https** powiązania dla witryny, jeśli nie jest już wyświetlany. Jeśli nie używasz certyfikatu z podpisem własnym, określ nazwę hosta z kroku 3 tej procedury. Jeśli używasz certyfikatu z podpisem własnym, ten krok nie jest wymagany.

6. Wybierz certyfikat uzyskany lub utworzony w kroku 3 tej procedury, a następnie kliknij przycisk **OK**.

## <a name="using-the-web-based-windows-powershell-console"></a>Korzystanie z konsoli internetowej programu Windows PowerShell

Po zainstalowaniu programu Windows PowerShell Web Access i zakończeniu konfigurowania bramy, zgodnie z opisem w tym temacie, konsoli internetowej programu Windows PowerShell jest gotowe do użycia. Aby uzyskać więcej informacji na temat uzyskiwania pracę w konsoli sieci web, zobacz [za pomocą konsoli programu PowerShell systemu Windows oparte na sieci Web](use-the-web-based-windows-powershell-console.md).

## <a name="see-also"></a>Zobacz też

- [Internetowe usługi informacyjne (IIS) 7.0 dokumentacji](https://technet.microsoft.com/library/cc753433.aspx)
- [Pomoc Menedżera 7.0 usług IIS](https://technet.microsoft.com/library/cc732664.aspx)
- [Konfigurowanie zabezpieczeń serwera sieci Web (IIS 7)](https://technet.microsoft.com/library/cc731278.aspx)
- [Zasoby dotyczące wdrażania protokołu IPsec](https://technet.microsoft.com/network/bb531150)
