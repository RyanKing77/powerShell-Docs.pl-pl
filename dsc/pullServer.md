---
ms.date: 04/11/2018
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Usługa ściągania platformy DSC
ms.openlocfilehash: 057da50843e79ae31eef4fea1fa58e882a9d1ace
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="desired-state-configuration-pull-service"></a>Usługa replikacji ściąganej konfiguracji żądanego stanu

> Dotyczy: Środowiska Windows PowerShell 5.0

> [!IMPORTANT]
> Ściągnięcia serwera (funkcja Windows *DSC usługi*) jest obsługiwanych składników systemu Windows Server jednak nie ma żadnych planów oferować nowe funkcje lub możliwości. Zaleca się rozpocząć przechodzenie zarządzanych klientów do [Konfiguracja DSC automatyzacji Azure](/azure/automation/automation-dsc-getting-started) (w tym funkcji poza ściągnięcia serwera w systemie Windows Server) lub jednego z rozwiązań społeczności wymienionych [tutaj](pullserver.md#community-solutions-for-pull-service).

Lokalny program Configuration Manager mogą centralnie zarządzane przez rozwiązanie do ściągania usługi.
Podczas korzystania z tej metody, węzeł, który jest zarządzany jest zarejestrowany za pomocą usługi i przypisany konfigurację w ustawieniach LCM.
Konfiguracja i wszystkie zasoby DSC, wymagane jako zależności w konfiguracji są pobierane do maszyny i używane przez LCM do zarządzanie konfiguracją.
Informacje o stanie komputera zarządzanego jest przekazywane do usługi raportowania.
To pojęcie jest określany jako "Usługa ściągania".

Dla aktualnych opcji ściągania usługi obejmują:

- Usługa konfiguracji stanu pożądanej usługi Automatyzacja Azure
- Usługa replikacji ściąganej w systemie Windows Server
- Społeczność utrzymywane rozwiązania open source
- Udział SMB

**Zalecane rozwiązanie**, a opcja z najbardziej funkcje dostępne, jest [Konfiguracja DSC automatyzacji Azure](/azure/automation/automation-dsc-getting-started).

Usługa Azure mogą zarządzać węzłów lokalnie w centrach danych prywatnych lub chmur publicznych, takich jak Azure i usług AWS.
W środowiskach prywatne, gdzie serwery bezpośrednio nie może połączyć się z Internetem, należy wziąć pod uwagę Ograniczanie ruchu wychodzącego tylko opublikowane zakres IP platformy Azure (zobacz [zakresów IP centrum danych Azure](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).

Funkcje usługi online, które nie są obecnie dostępne w usłudze replikacji ściąganej w systemie Windows Server:
- Wszystkie dane są szyfrowane podczas przesyłania i magazynowane
- Certyfikaty klienta są tworzone i zarządzane automatycznie
- Przechowywanie kluczy tajnych centralnego zarządzania [haseł lub poświadczeń](/azure/automation/automation-credentials), lub [zmienne](/azure/automation/automation-variables) takich jak nazwy serwera lub parametry połączenia
- Centralne zarządzanie węzła [LCM konfiguracji](metaConfig.md#basic-settings)
- Centralnie Przypisz konfiguracje do węzłów klienta
- Zmiany konfiguracji wersji do "grup mozgi" do testowania przed dotarciem do produkcji
- Raportowania graficznego
  - Szczegóły stanu na poziomie szczegółowości zasobów DSC
  - Pełne komunikaty z komputerów klienckich do rozwiązywania problemów
- [Integracja z usługą Analiza dzienników Azure](/azure/automation/automation-dsc-diagnostics) alertów, automatycznych zadań Android/aplikacji systemu iOS dla raportowania i alerty

## <a name="dsc-pull-service-in-windows-server"></a>Usługa ściągania usługi Konfiguracja DSC w systemie Windows Server

Istnieje możliwość konfigurowania usługi ściągnięcia do uruchamiania w systemie Windows Server.
Można wskazać, że rozwiązania usługi ściągania zawarte w systemie Windows Server zawiera tylko możliwości przechowywania moduły konfiguracji do pobrania i przechwytywanie danych raportów w bazie danych.
Nie obejmuje wiele możliwości oferowane przez usługę w systemie Azure i tak nie jest dobrym narzędzia do oceny, czy użycia usługi.

Usługa replikacji ściąganej oferowanych w systemie Windows Server jest usługi sieci web w usługach IIS, który używa interfejsu OData, aby udostępnić pliki konfiguracji DSC węzły docelowe podczas tych węzłów, poproś o ich.

Wymagania dotyczące korzystania z serwera ściągania:

- Serwer z systemem:
  - WMF PowerShell 5.0 lub nowszej
  - Rola serwera IIS
  - Usługi Konfiguracja DSC
- Najlepiej, jeśli niektóre oznacza generowania certyfikatu, aby zabezpieczyć poświadczenia przekazywane do lokalnego Menedżera konfiguracji (LCM) węzły docelowe

Najlepszym sposobem konfigurowania systemu Windows Server do usługi replikacji ściąganej hosta jest korzysta z konfiguracji DSC.
Poniżej znajduje się przykład skryptu.

### <a name="supported-database-systems"></a>Systemy obsługiwanych baz danych

|WMF 4.0   |WMF 5.0  |WMF 5.1 |WMF 5.1 (z systemem Windows Server niejawnego Podgląd 17090)|
|---------|---------|---------|---------|
|MDB     |ESENT (ustawienie domyślne), MDB |ESENT (ustawienie domyślne), MDB|ESENT (ustawienie domyślne), programu SQL Server MDB

Począwszy od wersji 17090 z [systemu Windows Server niejawnego Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), programu SQL Server jest obsługiwane opcji ściągania usługi (funkcji systemu Windows *usługi Konfiguracja DSC*).  Zapewnia to nowa opcja skalowania dużych środowiskach DSC, które nie zostały zmigrowane do [Konfiguracja DSC automatyzacji Azure](/azure/automation/automation-dsc-getting-started).

> **Uwaga**: Obsługa programu SQL Server nie zostanie dodany do poprzednich wersji WMF 5.1 (lub starszym), a tylko będą dostępne w wersjach systemu Windows Server większa niż lub równa 17090.

Aby skonfigurować serwer ściągnięcia do korzystania z programu SQL Server, należy ustawić **SqlProvider** do `$true` i **SqlConnectionString** do prawidłowego ciągu połączenia serwera SQL.  Aby uzyskać więcej informacji, zobacz [parametry połączenia SqlClient](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).
Na przykład konfigurację programu SQL Server z **xDscWebService**, najpierw przeczytać artykuł [przy użyciu zasobów xDscWebService](#using-the-xdscwebservice-resource) , a następnie przejrzyj [Sample_xDscWebServiceRegistration_ UseSQLProvider.ps1 w serwisie GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).

### <a name="using-the-xdscwebservice-resource"></a>Przy użyciu zasobów xDscWebService

Najprostszym sposobem konfigurowania serwera ściągania sieci web jest użycie **xDscWebService** zasobów objętych **xPSDesiredStateConfiguration** modułu.
Poniższych krokach opisano sposób użycia zasobu w konfiguracji, który konfiguruje usługę sieci web.

1. Wywołanie [instalacji modułu](/powershell/module/PowershellGet/Install-Module) polecenia cmdlet, aby zainstalować **xPSDesiredStateConfiguration** modułu. **Uwaga**: **instalacji modułu** znajduje się w **PowerShellGet** moduł, który jest dostępny w programie PowerShell 5.0. Możesz pobrać **PowerShellGet** modułu PowerShell 3.0 i 4.0 w [PackageManagement moduły programu PowerShell w wersji zapoznawczej](https://www.microsoft.com/en-us/download/details.aspx?id=49186).
1. Uzyskać certyfikat SSL z serwerem ściągania usługi Konfiguracja DSC od zaufanego urzędu certyfikacji, albo w ramach organizacji lub publicznego urzędu. Certyfikat odebrany od urzędu jest zwykle w formacie PFX. Zainstaluj certyfikat w węźle, który ma zostać z serwerem ściągania usługi Konfiguracja DSC w domyślnej lokalizacji, która powinna być CERT: \LocalMachine\My. Zanotuj odcisk palca certyfikatu.
1. Wybierz identyfikator GUID ma być używany jako klucz rejestracji. Aby wygenerować za pomocą programu PowerShell wpisz następujące polecenie w wierszu PS, a następnie naciśnij klawisz enter: "``` [guid]::newGuid()```"lub"```New-Guid```". Ten klucz będzie służyć przez węzły klienta jako klucza wspólnego uwierzytelnianie podczas rejestracji. Aby uzyskać więcej informacji zobacz sekcję poniżej klucz rejestracji.
1. W programie PowerShell ISE start (F5) następującego skryptu konfiguracji (zawarte w folderze przykłady **xPSDesiredStateConfiguration** modułu jako Sample_xDscWebServiceRegistration.ps1). Ten skrypt powoduje ustawienie z serwerem ściągania.

```powershell
configuration Sample_xDscWebServiceRegistration
{
    param
    (
        [string[]]$NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $certificateThumbPrint,

        [Parameter(HelpMessage='This should be a string with enough entropy (randomness) to protect the registration of clients to the pull server.  We will use new GUID by default.')]
        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey   # A guid that clients use to initiate conversation with pull server
    )

    Import-DSCResource -ModuleName xPSDesiredStateConfiguration

    Node $NodeName
    {
        WindowsFeature DSCServiceFeature
        {
            Ensure = "Present"
            Name   = "DSC-Service"
        }

        xDscWebService PSDSCPullServer
        {
            Ensure                  = "Present"
            EndpointName            = "PSDSCPullServer"
            Port                    = 8080
            PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer"
            CertificateThumbPrint   = $certificateThumbPrint
            ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
            ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
            State                   = "Started"
            DependsOn               = "[WindowsFeature]DSCServiceFeature"
            RegistrationKeyPath     = "$env:PROGRAMFILES\WindowsPowerShell\DscService"
            AcceptSelfSignedCertificates = $true
            Enable32BitAppOnWin64   = $false
        }

        File RegistrationKeyFile
        {
            Ensure          = 'Present'
            Type            = 'File'
            DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
            Contents        = $RegistrationKey
        }
    }
}
```

1. Uruchom konfigurację, przekazywanie odcisk palca certyfikatu SSL jako **certificateThumbPrint** parametru i rejestracji GUID klucz jako **RegistrationKey** parametru:

```powershell
# To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
# and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
dir Cert:\LocalMachine\my

# Then include this thumbprint when running the configuration
Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

# Run the compiled configuration to make the target node a DSC Pull Server
Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
```

#### <a name="registration-key"></a>Klucz rejestracji

Aby umożliwić węzłów do rejestrowania na serwerze, tak aby używały nazwy konfiguracji zamiast Identyfikatora konfiguracji klienta, klucz rejestracyjny, który został utworzony przez powyższej konfiguracji są zapisywane w pliku o nazwie `RegistrationKeys.txt` w `C:\Program Files\WindowsPowerShell\DscService`. Klucz rejestracji działa jako wspólny klucz tajny, używane podczas wstępnej przez klienta z serwerem ściągania. Klient wygeneruje certyfikat z podpisem własnym używany do jednoznacznego uwierzytelnienie na serwerze ściągania, po pomyślnym zakończeniu rejestracji. Odcisk palca certyfikatu jest przechowywana lokalnie i skojarzone z adresem URL serwera ściągania.
> **Uwaga**: klucze rejestracji nie są obsługiwane w programie PowerShell w wersji 4.0.

W celu skonfigurowania węzła w celu uwierzytelnienia na serwerze ściągania, klucz rejestracji musi być w metakonfigurację dla każdego węzła docelowego będzie rejestrowanie z tym serwerem ściągania. Należy pamiętać, że **RegistrationKey** w metakonfigurację poniżej zostanie usunięta po pomyślnie zarejestrowała maszyny docelowej, a wartość "140a952b-b9d6-406b-b416-e0f759c9c0e4" musi odpowiadać wartości przechowywanej w Plik RegistrationKeys.txt na serwerze ściągania. Jest zawsze traktowany wartość klucza rejestracji bezpieczne, ponieważ wiedząc o tym umożliwia żadnej maszyny docelowej, można zarejestrować na serwerze ściągania.

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to setup pull server in previous configuration

        [ValidateNotNullOrEmpty()]
        [string] $ServerName = 'localhost' #node name of the pull server, same as $NodeName used in previous configuration
    )

    Node $NodeName
    {
        Settings
        {
            RefreshMode        = 'Pull'
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey    = $RegistrationKey
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey = $RegistrationKey
        }
    }
}

Sample_MetaConfigurationToRegisterWithLessSecurePullServer -RegistrationKey $RegistrationKey -OutputPath c:\Configs\TargetNodes
```

> **Uwaga**: **ReportServerWeb** sekcja umożliwia raportowanie danych, które zostanie wysłane do serwera ściągania.

Brak **ConfigurationID** właściwość w pliku metakonfigurację niejawnie oznacza, że ten serwer ściągania obsługuje V2 wersji protokołu serwera ściągania, jest wymagana rejestracja początkowej.
Z drugiej strony, obecności **ConfigurationID** oznacza, że używana wersja V1 protokół serwera ściągania i nie istnieje żadne przetwarzania rejestracji.

>**Uwaga**: W trybie PUSH scenariuszu usterki istnieje w bieżącej wersji, który ułatwia określenie właściwości ConfigurationID w pliku metakonfigurację dla węzłów, które nigdy nie została zarejestrowana na serwerze ściągania. Spowoduje to wymusić protokół serwera ściągania V1 i uniknąć komunikaty o błędach rejestracji.

## <a name="placing-configurations-and-resources"></a>Wprowadzenie do konfiguracji i zasobów

Po ściągania kończy instalacji serwera, folderów, zdefiniowane przez **ConfigurationPath** i **ModulePath** właściwości w konfiguracji serwera ściągania są umieszczane moduły i konfiguracji który będzie dostępna dla węzły docelowe do ściągnięcia.
Te pliki muszą znajdować się w określonym formacie serwer ściągnięcia poprawnie przetworzyć je.

### <a name="dsc-resource-module-package-format"></a>Format pakietu moduł zasobu DSC

Każdy moduł zasobu musi być spakowane i o nazwie zgodnie z następującego wzorca `{Module Name}_{Module Version}.zip`.
Na przykład moduł o nazwie xWebAdminstration z wersją modułu 3.1.2.0 będą miały postać "xWebAdministration_3.2.1.0.zip".
Każda wersja programu modułu muszą być zawarte w pliku zip pojedynczego.
Ponieważ tylko jedną wersję zasobu w każdym pliku zip, format modułu, dodane w programie WMF 5.0 z obsługą wielu wersji modułu w jednym katalogu, nie jest obsługiwany.
Oznacza to, że przed grupowanie DSC modułów zasobów do użycia z serwera ściągania należy wprowadzić niewielkie zmiany w strukturze katalogu.
Domyślny format modułów zawierających DSC zasobów w programie WMF 5.0 "{modułu Folder}\{wersji modułu} \DscResources\{Folder zasobów DSC}\'.
Przed pakowania dla serwera ściągania, Usuń **{wersji modułu}** folderu, tak aby stał się ścieżka "{modułu Folder} \DscResources\{Folder zasobów DSC}\'.
Dzięki tej zmianie skompresować folder zgodnie z powyższym opisem i umieszczenie tych plików zip w **ModulePath** folderu.

Użyj `New-DscChecksum {module zip file}` do utworzenia pliku sumy kontrolnej dla nowo dodanym module.

### <a name="configuration-mof-format"></a>Format MOF konfiguracji

Plik MOF konfiguracji musi łączyć się z plikiem sumy kontrolnej, aby LCM w docelowym węźle można sprawdzić poprawność konfiguracji.
Aby utworzyć sumy kontrolnej, należy wywołać [DscChecksum nowy](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) polecenia cmdlet.
Polecenie cmdlet przyjmuje **ścieżki** parametr, który określa folder, w którym znajduje się konfiguracji MOF.
Polecenie cmdlet tworzy plik sumy kontrolnej o nazwie `ConfigurationMOFName.mof.checksum`, gdzie `ConfigurationMOFName` to nazwa pliku mof konfiguracji.
Jeśli istnieje więcej niż jedna konfiguracja pliki MOF we wskazanym folderze, suma kontrolna jest tworzony dla każdej konfiguracji w folderze.
Umieścić pliki MOF i ich skojarzonych sumy kontrolnej plików w **ConfigurationPath** folderu.

>**Uwaga**: w przypadku zmiany pliku MOF konfiguracji w dowolny sposób, należy również ponownie utworzyć plik sumy kontrolnej.

### <a name="tooling"></a>Narzędzia

Aby można było uzupełnić ustawienie, sprawdzanie poprawności i zarządzanie nimi z serwerem ściągania łatwiejsze, następujących narzędzi są dołączone jako przykłady w najnowszej wersji modułu xPSDesiredStateConfiguration:

1. Moduł, który pomoże pakowania DSC zasobów modułów i pliki konfiguracyjne do użycia na serwerze ściągania. [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1). Poniższe przykłady:

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. Skrypt, który sprawdza poprawność z serwerem ściągania jest poprawnie skonfigurowany. [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).

## <a name="community-solutions-for-pull-service"></a>Społeczności rozwiązań dla usługi replikacji ściąganej

Społeczność DSC ma przypisany wielu rozwiązań do implementowania protokołu usługi ściągania.
W środowiskach lokalnych oferuje możliwości usługi ściągania i możliwość współtworzenia społeczności ulepszeń przyrostowych.

- [Holownik](https://github.com/powershellorg/tug)
- [DSC TRÆK](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a>Konfiguracja klienta ściągania

Konfigurowanie klientów ściągania szczegóły można znaleźć w następujących tematach:

- [Konfigurowanie klienta ściągania usługi Konfiguracja DSC przy użyciu Identyfikatora konfiguracji](pullClientConfigID.md)
- [Konfigurowanie klienta ściągania usługi Konfiguracja DSC przy użyciu nazwy konfiguracji](pullClientConfigNames.md)
- [Konfiguracje z częściowa](partialConfigs.md)

## <a name="see-also"></a>Zobacz też

- [Omówienie stanu konfiguracji żądanego programu Windows PowerShell](overview.md)
- [Realizacja konfiguracji](enactingConfigurations.md)
- [Używanie serwera raportów platformy DSC](reportServer.md)
- [[MS-DSCPM]: żądany protokół Model ściągania konfiguracji stanu](https://msdn.microsoft.com/library/dn393548.aspx)
- [[MS-DSCPM]: żądany stan konfiguracji replikacji ściąganej modelu protokołu erracie](https://msdn.microsoft.com/library/mt612824.aspx)