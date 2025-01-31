---
ms.date: 06/27/2017
keywords: polecenia cmdlet programu PowerShell
title: Reguły autoryzacji i funkcje zabezpieczeń programu Windows PowerShell Web Access
ms.openlocfilehash: c426b8cfb10829241ba244a5d840c91e1de9f66e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058424"
---
# <a name="authorization-rules-and-security-features-of-windows-powershell-web-access"></a>Reguły autoryzacji i funkcje zabezpieczeń programu Windows PowerShell Web Access

Zaktualizowano: 24 czerwca 2013 r.

Dotyczy: Windows Server 2012 R2, Windows Server 2012

Program Windows PowerShell Web Access w systemie Windows Server 2012 R2 i Windows Server 2012 ma z restrykcyjnego modelu zabezpieczeń. Użytkownikom należy jawnie udzielić dostępu przed mogą zalogować się do bramy programu Windows PowerShell Web Access i używać konsoli internetowej programu Windows PowerShell.

## <a name="configuring-authorization-rules-and-site-security"></a>Konfigurowanie reguł autoryzacji i zabezpieczeń lokacji

Po zainstalowaniu programu Windows PowerShell Web Access, a brama jest skonfigurowana, użytkownicy mogą otwierać strony logowania w przeglądarce, ale nie można zalogować do momentu administratora programu Windows PowerShell Web Access jawnego przydzielenia im dostępu. Kontrola dostępu "Windows PowerShell Web Access" odbywa się przy użyciu zestawu poleceń cmdlet Windows PowerShell opisanych w poniższej tabeli. Do dodawania lub zarządzanie regułami autoryzacji jest nie porównywalny graficzny interfejs użytkownika.
Zobacz [polecenia cmdlet programu Windows PowerShell Web Access](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Administratorzy mogą definiować `{0-n}` reguł uwierzytelniania dla programu Windows PowerShell Web Access. Zabezpieczenia domyślne są restrykcyjne, a nie zezwolenia; zero reguł uwierzytelniania oznacza, że żaden użytkownik nie ma dostępu do żadnego elementu.

[Polecenia Add-PswaAuthorizationRule](/powershell/module/powershellwebaccess/add-pswaauthorizationrule?view=winserver2012r2-ps) i [Test-PswaAuthorizationRule](/powershell/module/powershellwebaccess/test-pswaauthorizationrule?view=winserver2012r2-ps) w systemie Windows Server 2012 R2 zawiera parametr Credential, która pozwala na dodawanie i testowanie reguł autoryzacji programu Windows PowerShell Web Access z lokalizacji zdalnej komputerze lub w obrębie aktywnej sesji programu Windows PowerShell Web Access. Jak z innymi poleceniami cmdlet programu Windows PowerShell, która ma parametr Credential, można określić obiekt PSCredential jako wartość parametru. Aby utworzyć obiekt PSCredential zawierający poświadczenia, które mają być przekazywane do komputera zdalnego, uruchom [Get-Credential](/powershell/module/microsoft.powershell.security/Get-Credential) polecenia cmdlet.

Reguły uwierzytelniania programu Windows PowerShell Web Access to reguły określające elementy dozwolone. Każda reguła stanowi definicję dozwolonego połączenia między użytkownikami, komputerami docelowymi i określonego Windows PowerShell [konfiguracje sesji](/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-5.1) (określane również jako punkty końcowe lub _obszary działania_) na wskazanych komputerach docelowych.
Aby uzyskać informacje na **obszary działania** zobacz [początku użyj programu PowerShell z obszary działania](https://blogs.technet.microsoft.com/heyscriptingguy/2015/11/26/beginning-use-of-powershell-runspaces-part-1/)

> [!IMPORTANT]
> Użytkownik musi tylko jedna reguła jest prawdziwa uzyskiwanie dostępu. Jeśli użytkownik otrzyma dostęp do jednego komputera z pełną obsługą języka lub dostęp tylko do polecenia cmdlet zarządzania zdalnego programu Windows PowerShell, za pomocą konsoli sieci web użytkownik może zalogować się (lub przeskoku) na innych komputerach, które są połączone z pierwszym komputerem docelowym. Najbezpieczniejszą metodą, aby skonfigurować program Windows PowerShell Web Access jest zezwolić użytkownikom na dostęp tylko do ograniczonych konfiguracji sesji, umożliwiających im realizację określonych zadań, które muszą zwykle wykonać zdalnie.

Polecenia cmdlet, do którego odwołuje się [polecenia cmdlet programu Windows PowerShell Web Access](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps) Zezwalaj, aby utworzyć zestaw reguł dostępu, które są używane do autoryzacji użytkownika w bramie Windows PowerShell Web Access. Zasady są inne niż listy kontroli dostępu (ACL) na komputerze docelowym i zapewniają dodatkową warstwę zabezpieczeń dla dostępu do sieci web. Więcej informacji na temat zabezpieczeń są opisane w poniższej sekcji.

Jeśli użytkownicy nie przejdą którejkolwiek z poprzednich warstw zabezpieczeń, otrzymają komunikat ogólny "odmowa dostępu" w oknie przeglądarki. Chociaż szczegóły zabezpieczeń są rejestrowane na serwerze bramy, użytkownicy końcowi nie są wyświetlane informacji na temat liczby warstw zabezpieczeń, które są przekazywane lub które warstwie wystąpił błąd logowania i uwierzytelniania.

Aby uzyskać więcej informacji na temat konfigurowania reguł autoryzacji, zobacz [Konfigurowanie reguł autoryzacji](#configuring-authorization-rules-and-site-security) w tym temacie.

### <a name="security"></a>Bezpieczeństwo

Model zabezpieczeń Windows PowerShell Web Access znajdują się cztery warstwy między użytkownikiem końcowym konsoli internetowej a komputerem docelowym. Windows PowerShell Web Access, Administratorzy mogą dodawać warstwy zabezpieczeń za pomocą dodatkowych czynności konfiguracyjnych, w konsoli Menedżera usług IIS. Aby uzyskać więcej informacji na temat zabezpieczania witryn internetowych w konsoli Menedżera usług IIS, zobacz [Konfigurowanie zabezpieczeń serwera sieci Web (IIS7)](https://technet.microsoft.com/library/cc731278).

Aby uzyskać więcej informacji na temat usług IIS najlepsze rozwiązania i zapobieganie atakom typu "odmowa usługi", zobacz [najlepsze rozwiązania do zapobiegania DoS/atakom typu odmowa usługi](https://technet.microsoft.com/library/cc750213).
Administrator można kupić i zainstalować oprogramowanie uwierzytelniania dodatkowego handlu detalicznego.

W poniższej tabeli opisano cztery warstwy zabezpieczeń między użytkownikami końcowymi a komputerami docelowymi.

|Poziom|Warstwa|
|-|-|
|1|[funkcje zabezpieczeń serwera sieci web usług IIS](#iis-web-server-security-features)|
|2|[Uwierzytelnianie bramy oparte na formularzach dostęp w sieci web programu powershell systemu Windows](#windows-powershell-web-access-forms-based-gateway-authentication)|
|3|[reguły autoryzacji dostępu do sieci web programu powershell systemu Windows](#windows-powershell-web-access-authorization-rules)|
|4|[docelowe zasady uwierzytelniania i autoryzacji](#target-authentication-and-authorization-rules)|

Szczegółowe informacje na temat poszczególnych warstw można znaleźć w następujących pozycji:

#### <a name="iis-web-server-security-features"></a>Funkcje zabezpieczeń serwera sieci Web usług IIS

Windows PowerShell Web Access użytkownicy muszą zawsze podawać nazwę użytkownika i hasło do uwierzytelniania kont w bramie. Jednak administratorzy programu Windows PowerShell Web Access można również włączyć opcjonalne uwierzytelnianie certyfikatu klienta, lub wyłączyć zobacz [Instalowanie i używanie programu windows powershell web access](install-and-use-windows-powershell-web-access.md) umożliwiające certyfikat testowy i nowszych, jak skonfigurować oryginalnego certyfikatu).

Opcjonalna funkcja certyfikatu klienta wymaga od użytkowników końcowych, które mają prawidłowy certyfikat klienta, oprócz nazwy użytkownika i hasła i jest częścią konfiguracji serwera sieci Web (IIS). Po włączeniu warstwy certyfikatu klienta, strony logowania programu Windows PowerShell Web Access monit o dostarczenie prawidłowego przed wyznaczeniem poświadczeń logowania. Uwierzytelnianie certyfikatu klienta automatycznie sprawdza, czy dla certyfikatu klienta. Jeśli certyfikat nie zostanie znaleziony, programu Windows PowerShell Web Access informuje użytkowników, dzięki czemu mogą podać certyfikat. Jeśli zostanie znaleziony prawidłowy certyfikat klienta, programu Windows PowerShell Web Access otwiera stronę logowania dla użytkowników zapewnić ich nazwy użytkownika i hasła.

Jest jednym z przykładów dodatkowych ustawień zabezpieczeń, które są oferowane przez serwer sieci Web usług IIS. Aby uzyskać więcej informacji o innych funkcjach zabezpieczeń usług IIS, zobacz [Konfigurowanie zabezpieczeń serwera sieci Web (IIS 7)](https://technet.microsoft.com/library/cc731278).

#### <a name="windows-powershell-web-access-forms-based-gateway-authentication"></a>Uwierzytelnianie bramy oparte na formularzach Windows PowerShell Web Access

Strony logowania programu Windows PowerShell Web Access wymaga zestawu poświadczeń (nazwy użytkownika i hasło) i udostępniana opcja podania innych poświadczeń dla komputera docelowego.
Jeśli użytkownik nie poda innych poświadczeń, podstawowej nazwy użytkownika i hasło, które są używane do połączenia z bramą także są używane do połączenia z komputerem docelowym.

Wymagane poświadczenia są uwierzytelniane przez bramę programu Windows PowerShell Web Access. Te poświadczenia muszą odpowiadać prawidłowym kontom użytkowników albo z programu Windows PowerShell Web Access bramy serwera lokalnego lub w usłudze Active Directory.

#### <a name="windows-powershell-web-access-authorization-rules"></a>Reguły autoryzacji programu Windows PowerShell Web Access

Po uwierzytelnieniu użytkownika na bramie Windows PowerShell Web Access sprawdza reguły autoryzacji, aby sprawdzić, czy użytkownik ma dostęp do żądanego komputera docelowego. Po pomyślnej autoryzacji poświadczenia użytkownika są przekazywane do komputera docelowego.

Te reguły są oceniane tylko wtedy, gdy użytkownik został uwierzytelniony przez bramę i zanim użytkownik może zostać uwierzytelniony na komputerze docelowym.

#### <a name="target-authentication-and-authorization-rules"></a>Docelowy zasady uwierzytelniania i autoryzacji

Ostatnią warstwą zabezpieczeń programu Windows PowerShell Web Access jest konfiguracja zabezpieczeń na komputerze docelowym. Użytkownicy muszą mieć odpowiednie uprawnienia dostępu skonfigurowane na komputerze docelowym, a także w regułach autoryzacji programu Windows PowerShell Web Access, aby uruchomić konsoli sieci web programu Windows PowerShell, która ma wpływ na komputerze docelowym za pośrednictwem programu Windows PowerShell Web Access.

Ta warstwa oferuje te same mechanizmy zabezpieczeń, które są używane do oceny próby połączenia przypadku, gdy użytkownicy próbują utworzyć sesji zdalnej programu Windows PowerShell na komputerze docelowym z wnętrza programu Windows PowerShell, uruchamiając [Enter-PSSession](/powershell/module/microsoft.powershell.core/Enter-PSSession) lub [New-PSSession](/powershell/module/microsoft.powershell.core/new-pssession) polecenia cmdlet.

Domyślnie program Windows PowerShell Web Access używa podstawowej nazwy użytkownika i hasło do uwierzytelniania, zarówno brama i komputer docelowy. Oparte na sieci web strony logowania, w sekcji **opcjonalne ustawienia połączenia**, udostępniana opcja podania innych poświadczeń dla komputera docelowego, jeśli są one wymagane. Jeśli użytkownik nie poda innych poświadczeń, podstawowej nazwy użytkownika i hasło, które są używane do połączenia z bramą także są używane do połączenia z komputerem docelowym.

Reguły autoryzacji można zezwolić użytkownikom na dostęp do określonej konfiguracji sesji. Możesz utworzyć _ograniczonych obszarach działania_ lub konfiguracje sesji programu Windows PowerShell Web Access, i zezwolić określonym użytkownikom połączyć tylko określonymi konfiguracjami sesji po zalogowaniu się do programu Windows PowerShell Web Access. Użyj listy kontroli dostępu (ACL), aby określić, którzy użytkownicy mają dostęp do określonych punktów końcowych i bardziej ograniczyć dostęp do punktu końcowego dla określonych użytkowników przy użyciu reguł autoryzacji opisanych w tej sekcji. Aby uzyskać więcej informacji o ograniczonych obszarach działania, zobacz [tworzenia ograniczonego obszaru działania](https://msdn.microsoft.com/library/dn614668).

### <a name="configuring-authorization-rules"></a>Konfigurowanie reguł autoryzacji

Administratorzy mogą mają tę samą regułę autoryzacji dla użytkowników programu Windows PowerShell Web Access, które jest już zdefiniowany w swoim środowisku, do zarządzania zdalnego programu Windows PowerShell. Pierwsza procedura w tej sekcji opisano sposób dodawania bezpiecznej reguły autoryzacji przyznająca dostęp jednemu użytkownikowi logującemu się celu zarządzania jednym komputerem i w ramach jednej konfiguracji sesji. Druga procedura w tym artykule opisano sposób usuwania reguły autoryzacji, która nie jest już potrzebny.

Jeśli planujesz używanie niestandardowych konfiguracji sesji, aby zezwolić określonym użytkownikom do pracy tylko w obrębie ograniczonych obszarach działania w programie Windows PowerShell Web Access, należy utworzyć niestandardowe konfiguracje sesji przed dodaniem reguł autoryzacji, które odwołują się do nich. Nie można użyć poleceń cmdlet programu Windows PowerShell Web Access, aby utworzyć niestandardowe konfiguracje sesji. Aby uzyskać więcej informacji na temat tworzenia niestandardowych konfiguracji sesji, zobacz [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

Polecenia cmdlet programu Windows PowerShell Web Access obsługują jeden symbol wieloznaczny, znak gwiazdki ( \* ). Wieloznaczne w ciągach nie są obsługiwane. za pomocą jednej gwiazdki na każdą właściwość (użytkownicy, komputery lub konfiguracje sesji).

> [!NOTE]
> Zobacz więcej sposobów reguły autoryzacji służy do udzielania dostępu użytkownikom i pomóc w zabezpieczeniu środowiska Windows PowerShell Web Access [inne przykłady scenariuszy reguły autoryzacji](#other-authorization-rule-scenario-examples) w tym temacie.

#### <a name="to-add-a-restrictive-authorization-rule"></a>Aby dodać restrykcyjną regułę autoryzacji

1. Wykonaj jedną z następujących czynności, aby otworzyć sesję środowiska Windows PowerShell z podwyższonym poziomem uprawnień użytkownika.

   - Na pulpicie systemu Windows kliknij prawym przyciskiem myszy **środowiska Windows PowerShell** na pasku zadań, a następnie kliknij przycisk **Uruchom jako Administrator**.

   - Na Windows **Start** ekranu, kliknij prawym przyciskiem myszy **programu Windows PowerShell**, a następnie kliknij przycisk **Uruchom jako Administrator**.

2. **Krok opcjonalny** umożliwiający ograniczenie dostępu użytkowników za pomocą konfiguracji sesji:

   Sprawdź, czy konfiguracje sesji, do których chcesz użyć, już istnieją w regułach.

   Jeśli one nie zostały jeszcze utworzone, skorzystaj z instrukcji tworzenia konfiguracji sesji w [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

3. Ta reguła autoryzacji zezwala określonemu użytkownikowi na dostęp do jednego komputera w sieci, do których zwykle mają dostęp z uprawnieniami do konfiguracji określonej sesji, które są ograniczone do użytkownika "™ s typowe potrzeby skrypty i polecenia cmdlet. Wpisz następujące polecenie, a następnie naciśnij klawisz **Enter**.

   ```
   Add-PswaAuthorizationRule -UserName <domain\user | computer\user> `
      -ComputerName <computer_name> -ConfigurationName <session_configuration_name>
   ```

   - W poniższym przykładzie użytkownik o nazwie _JSmith_ w _Contoso_ domeny ma uprawnienia do zarządzania komputerem _Contoso_214_i korzystać z konfiguracji sesji o nazwie _NewAdminsOnly_.

   ```powershell
   Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' `
      -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly
   ```

4. Sprawdź, czy reguła została utworzona za pomocą **Get-PswaAuthorizationRule** polecenia cmdlet, lub `Test-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName** <computer_name>`.
   Na przykład `Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214`.

#### <a name="to-remove-an-authorization-rule"></a>Aby usunąć regułę autoryzacji

1. Jeśli w sesji programu Windows PowerShell nie jest jeszcze otwarty, zobacz krok 1 [dodać restrykcyjną regułę autoryzacji](#to-add-a-restrictive-authorization-rule) w tej sekcji.

2. Wpisz następujące polecenie, a następnie naciśnij klawisz **Enter**, gdzie *ID reguły* reprezentuje unikatowy numer identyfikacyjny reguły, która ma zostać usunięty.

   ```
   Remove-PswaAuthorizationRule -ID <rule ID>
   ```

   Alternatywnie, jeśli nie znasz numeru Identyfikacyjnego, ale znasz przyjazną nazwę reguły, której chcesz usunąć, możesz pobrać nazwę reguły i przekazać go do `Remove-PswaAuthorizationRule` polecenia cmdlet, aby usunąć regułę, jak pokazano w poniższym przykładzie:

   ```
   Get-PswaAuthorizationRule `
      -RuleName <rule-name> | Remove-PswaAuthorizationRule
   ```

> [!NOTE]
> Nie monit o potwierdzenie chęci usunięcia wskazanej reguły autoryzacji; Reguła zostanie usunięta po naciśnięciu klawisza **Enter**. Pamiętaj, że chcesz usunąć regułę autoryzacji, zanim uruchomisz `Remove-PswaAuthorizationRule` polecenia cmdlet.

#### <a name="other-authorization-rule-scenario-examples"></a>Inne przykłady scenariuszy reguły autoryzacji

Każdej sesji programu Windows PowerShell korzysta z konfiguracji sesji; Jeśli nie została wskazana dla sesji, programu Windows PowerShell korzysta z domyślną, wbudowaną konfigurację sesji programu Windows PowerShell, o nazwie Microsoft.PowerShell. Domyślna konfiguracja sesji obejmuje wszystkie polecenia cmdlet, które są dostępne na komputerze. Administratorzy mogą ograniczyć dostęp do wszystkich komputerów, definiując konfigurację sesji z ograniczonym obszarem działania (ograniczonym zakresem poleceń cmdlet i zadań, które można wykonać jego usług użytkownicy końcowi). Użytkownik, który uzyskuje dostęp do jednego komputera z pełną obsługą języka lub wyłącznie cmdlet zarządzania zdalnego programu Windows PowerShell można połączyć na innych komputerach, które są połączone z pierwszym komputerem. Definiowanie ograniczonym obszarem działania mogą uniemożliwić użytkownikom uzyskiwanie dostępu do innych komputerów z ich dozwolonych obszarem działania programu Windows PowerShell i zwiększa bezpieczeństwo środowiska Windows PowerShell Web Access. Konfiguracja sesji mogą być dystrybuowane (przy użyciu zasad grupy), do wszystkich komputerów, które Administratorzy planują udostępnić za pośrednictwem programu Windows PowerShell Web Access. Aby uzyskać więcej informacji na temat konfiguracji sesji, zobacz [informacje o konfiguracjach sesji](https://technet.microsoft.com/library/dd819508.aspx). Poniżej przedstawiono kilka przykładów tego scenariusza.

- Administrator tworzy punkt końcowy o nazwie **Punktkoncowypswa**, z ograniczonym obszarem działania. Następnie administrator tworzy regułę, `*,*,PswaEndpoint`i rozpowszechnia punkt końcowy na innych komputerach. Ta reguła zezwala wszystkim użytkownikom na dostęp do wszystkich komputerów z punktem końcowym **Punktkoncowypswa**.
  Jeśli jest to jedyna reguła autoryzacji zdefiniowana w zestawie reguł, komputery bez tego punktu końcowego będą niedostępne.

- Administrator utworzył punkt końcowy z ograniczonym obszarem działania o nazwie **Punktkoncowypswa**i chce ograniczyć dostęp do określonych użytkowników. Administrator tworzy grupę użytkowników o nazwie **pomoc1poziomu**i definiuje następującą regułę: **Pomoc1poziomu,\*, Punktkoncowypswa**. Reguła zezwala wszystkim użytkownikom w grupie **pomoc1poziomu** dostęp do wszystkich komputerów z **Punktkoncowypswa** konfiguracji. Podobnie dostęp, może być ograniczone do konkretnego zestawu komputerów.

- Niektórzy administratorzy przyznają określonym użytkownikom szerszy dostęp niż innym. Na przykład administrator tworzy dwie grupy użytkowników, **Administratorzy** i **Pomocpodstawowa**. Administrator tworzy również punkt końcowy z ograniczonym obszarem działania o nazwie **Punktkoncowypswa**i definiuje następujące dwie reguły: **Administratorzy,\*,\***  i **Pomocpodstawowa,\*, Punktkoncowypswa**. Pierwsza reguła zawiera wszystkich użytkowników w **administratora** grupie dostępu do wszystkich komputerów, a druga reguła zawiera wszystkich użytkowników w **Pomocpodstawowa** grupie dostęp tylko do komputerów z  **Punktkoncowypswa**.

- Administrator skonfigurował prywatne środowisko testowe i chce zezwolić wszystkim autoryzowanym użytkownikom sieci dostęp do wszystkich komputerów w sieci, do których zwykle mają dostęp, ze wszystkimi konfiguracjami, do których zwykle mają oni dostęp. Ponieważ jest to prywatne środowisko testowe, administrator tworzy regułę autoryzacji, która nie jest bezpieczna. -Administrator uruchamia polecenie cmdlet `Add-PswaAuthorizationRule * * *`, który używa znaku wieloznacznego **\*** do reprezentowania wszystkich użytkowników, wszystkie komputery i wszystkie konfiguracje. — Ta reguła jest odpowiednikiem następującego: `Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *`.

  > [!NOTE]
  > Ta zasada nie jest zalecane w bezpiecznym środowisku i pomija warstwę reguły autoryzacji zabezpieczeń zapewnianych przez program Windows PowerShell Web Access.

- Administrator musi zezwolić użytkownikom na łączenie się z komputerami docelowymi w środowisku, które obejmuje zarówno grupy robocze, jak i domeny, której komputery grupy roboczej są czasami używane do łączenia z komputerami docelowymi w domenach, a komputery w domenach są czasami używane Aby połączyć się z komputerami docelowymi w grupach roboczych. Administrator ma serwer bramy *PswaServer*, w grupie roboczej i komputer docelowy *srv1.contoso.com* znajduje się w domenie. Użytkownik *Chris* jest autoryzowanym użytkownikiem lokalnym na serwerze bramy grupy roboczej i komputer docelowy. Jego nazwa użytkownika na serwerze grupy roboczej jest *chrisLocal*; a jego nazwa użytkownika na komputerze docelowym jest *contoso\\chris*. Aby autoryzować dostęp do komputera srv1.contoso.com Krzysztofa, administrator dodaje następującą regułę.

```powershell
Add-PswaAuthorizationRule -userName PswaServer\chrisLocal `
   -computerName srv1.contoso.com -configurationName Microsoft.PowerShell
```

Reguła z powyższego przykładu powoduje uwierzytelnienie Chrisa na serwerze bramy, a następnie autoryzację jego dostępu do *srv1*. Na stronie logowania Chris musi podać drugi zestaw poświadczeń w **opcjonalne ustawienia połączenia** obszaru (*contoso\\chris*). Serwer bramy zastosuje dodatkowy zestaw poświadczeń w celu uwierzytelnienia użytkownika na komputerze docelowym *srv1.contoso.com*.

W powyższym scenariuszu program Windows PowerShell Web Access ustanawia pomyślnie połączenie z komputerem docelowym, tylko wtedy, gdy poniżej zostały pomyślnie i dopuszczeniu przez co najmniej jedną regułę autoryzacji.

1. Uwierzytelnianie na serwerze bramy grupy roboczej przez dodanie nazwy użytkownika w formacie *nazwa_serwera*\\*nazwa_użytkownika* reguły autoryzacji

2. Uwierzytelnianie na komputerze docelowym, korzystając z poświadczeń wprowadzonych na stronie logowania w **opcjonalne ustawienia połączenia** obszaru

   > [!NOTE]
   > Jeśli brama i komputer docelowy znajdują się w różnych grupach roboczych lub domenach, należy ustanowić relację zaufania między dwoma komputerami grupy roboczej, obiema domenami lub grupą roboczą a domeny. Ta relacja nie można skonfigurować za pomocą poleceń cmdlet reguł autoryzacji programu Windows PowerShell Web Access. Reguły autoryzacji nie definiują relacji zaufania między komputerami; jedynie autoryzują użytkowników, aby nawiązać połączenie z określonymi komputerami docelowymi i konfiguracjami sesji. Aby uzyskać więcej informacji na temat sposobu konfigurowania relacji zaufania między domenami, zobacz [Tworzenie domeny i relacje zaufania lasu](https://technet.microsoft.com/library/cc794775.aspx).
   > Aby uzyskać więcej informacji na temat dodawania komputerów grupy roboczej do listy zaufanych hostów, zobacz [zdalne zarządzanie za pomocą Menedżera serwera](https://technet.microsoft.com/library/dd759202.aspx).

### <a name="using-a-single-set-of-authorization-rules-for-multiple-sites"></a>Przy użyciu jednego zestawu reguł autoryzacji dla wielu witryn

Reguły autoryzacji są przechowywane w pliku XML. Domyślnie nazwa ścieżki pliku XML jest `$env:windir\Web\PowershellWebAccess\data\AuthorizationRules.xml`.

Ścieżka do pliku XML z regułami autoryzacji jest przechowywana w **powwa.config** pliku, który znajduje się w `$env:windir\Web\PowershellWebAccess\data`. Administrator ma może zmienić odwołanie do ścieżki domyślnej w **powwa.config** do preferencji lub potrzeb. Administratora zmienić lokalizację pliku umożliwia wielu bram Windows PowerShell Web Access, użyj tych samych reguł autoryzacji, jeśli taka konfiguracja jest pożądane.

## <a name="session-management"></a>Zarządzanie sesjami

Domyślnie program Windows PowerShell Web Access ogranicza użytkownikowi trzy sesji w tym samym czasie. Można edytować aplikacji sieci web **web.config** plików w Menedżerze usług IIS w celu obsługi innej liczby sesji na użytkownika. Ścieżka do **web.config** plik jest `$env:windir\Web\PowerShellWebAccess\wwwroot\Web.config`.

Domyślnie serwer sieci Web usług IIS jest skonfigurowany na ponowne uruchomienie puli aplikacji, jeśli jakichkolwiek zmian ustawień. Na przykład, ponownym uruchomieniu puli aplikacji, jeśli zmiany zostały wprowadzone **web.config** pliku. > ponieważ **programu Windows PowerShell Web Access** używa stanów sesji w pamięci > Użytkownicy zalogowani celu **programu Windows PowerShell Web Access** sesje tracą swoje sesje, po ponownym uruchomieniu puli aplikacji.

### <a name="setting-default-parameters-on-the-sign-in-page"></a>Ustawianie parametrów domyślnych na stronie logowania

Jeśli brama programu Windows PowerShell Web Access jest uruchomiony w systemie Windows Server 2012 R2, można skonfigurować domyślne wartości ustawień, które są wyświetlane na stronie logowania programu Windows PowerShell Web Access. Możesz skonfigurować wartości w **web.config** pliku, który jest opisany w poprzednim akapicie. Wartości domyślne ustawień strony logowania znajdują się w **appSettings** sekcji w pliku web.config; Oto przykład **appSettings** sekcji. Prawidłowe wartości dla wielu z tych ustawień są takie same jak w przypadku odpowiednich parametrów [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) polecenia cmdlet programu Windows PowerShell.

Na przykład `defaultApplicationName` klucza, jak pokazano w poniższym fragmencie kodu jest wartością **$PSSessionApplicationName** zmiennej preferencji na komputerze docelowym.

```xml
  <appSettings>
      <add key="maxSessionsAllowedPerUser" value="3"/>
      <add key="defaultPortNumber" value="5985"/>
      <add key="defaultSSLPortNumber" value="5986"/>
      <add key="defaultApplicationName" value="WSMAN"/>
      <add key="defaultUseSslSelection" value="0"/>
      <add key="defaultAuthenticationType" value="0"/>
      <add key="defaultAllowRedirection" value="0"/>
      <add key="defaultConfigurationName" value="Microsoft.PowerShell"/>
  </appSettings>
```

### <a name="time-outs-and-unplanned-disconnections"></a>Limity czasu i rozłączenia nieplanowane

Przekroczono limit czasu sesji programu Windows PowerShell Web Access. W programie Windows PowerShell Web Access uruchomiona w systemie Windows Server 2012 komunikat o limicie czasu jest wyświetlany użytkownikom logował się po 15 minutach nieaktywności sesji. Jeśli użytkownik nie odpowie w ciągu pięciu minut po wyświetleniu komunikatu o limicie czasu, sesja zostanie zakończona, a użytkownik zostanie wylogowany. Możesz zmienić okresy limitu czasu sesji w ustawieniach witryny sieci Web w Menedżerze usług IIS.

W programie Windows PowerShell Web Access uruchomiona w systemie Windows Server 2012 R2 limit czasu sesji, domyślnie, po upływie 20 minut braku aktywności. Przypadku rozłączenia sesji w konsoli sieci web z powodu błędów sieci lub innych nieplanowane wyłączenie lub błędy, a nie, ponieważ mają one zamknięciem sesji przez sesji programu Windows PowerShell Web Access w dalszym ciągu uruchamiać, nawiązanie połączenia komputerów docelowych, aż do limitu czasu na wygaśnie po stronie klienta. Sesja zostaje rozłączona po upływie domyślne 20 minut lub po upływie limitu czasu określonego przez administratora bramy, która kwota jest krótszy.

Jeśli serwer bramy działa system Windows Server 2012 R2, Windows PowerShell Web Access umożliwia użytkownikom ponowne połączenia z zapisanymi sesjami w późniejszym czasie, ale w przypadku rozłączenia sesji błędy sieci, nieplanowane wyłączenie lub inne błędy użytkownik nie może zobaczyć i ponownie zapisać sesje, aż po upływie limitu czasu określonego przez bramę wygasł administratora.

## <a name="see-also"></a>Zobacz też

[Instalowanie i używanie programu Windows PowerShell Web Access](https://technet.microsoft.com/library/hh831611(v=ws.11).aspx)

[about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)

[Polecenia cmdlet programu Windows PowerShell Web Access](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps)
