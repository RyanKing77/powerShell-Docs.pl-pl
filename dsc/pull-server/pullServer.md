---
ms.date: 03/04/2019
keywords: DSC, powershell, konfiguracja, ustawienia
title: Usługa ściągania platformy DSC
ms.openlocfilehash: 64c22bc021666026ae58a4c4fb4e3d31b25bae5c
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429962"
---
# <a name="desired-state-configuration-pull-service"></a>Usługa ściągania Desired State Configuration

> [!IMPORTANT]
> Serwera ściągania (funkcja Windows *usługi DSC*) jest obsługiwanych składników systemu Windows Server jednak nie jest planowane oferują nowe funkcje lub możliwości osobno. Zaleca się rozpocząć przechodzenie zarządzanych klientom [usługi Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (w tym funkcje poza serwera ściągania w systemie Windows Server) lub jeden z członków społeczności na liście [tutaj](pullserver.md#community-solutions-for-pull-service).

Local Configuration Manager mogą centralnie zarządzane przez rozwiązanie usługi ściągania.
Korzystając z tego podejścia, węzeł, który jest zarządzany jest zarejestrowana przy użyciu usługi i przypisany konfiguracji w ustawieniach LCM.
Konfiguracji i wszystkie zasoby DSC, wymagane jako zależności w konfiguracji są pobierane do maszyny i używane przez LCM do zarządzania konfiguracją.
Informacje o stanie maszyny zarządzany jest przekazywany do usługi raportowania.
Takie podejście jest określany jako "Usługa pull".

Bieżące opcje dla usługi ściągania obejmują:

- Usługa Azure Automation Desired State Configuration
- Usługa ściągania, w systemie Windows Server
- Obsługiwane rozwiązań typu open source społeczności
- Udział SMB

**Zalecanym rozwiązaniem**, a opcja najbardziej funkcje dostępne, jest [usługi Azure Automation DSC](/azure/automation/automation-dsc-getting-started).

Usługi platformy Azure można zarządzać węzłów lokalnych w centrach danych prywatnych lub w chmurach publicznych, takich jak Azure i AWS.
Prywatne środowiska, w której serwery bezpośrednio nie może połączyć się z Internetem, należy rozważyć ograniczenie ruchu wychodzącego do tylko opublikowane zakres adresów IP platformy Azure (zobacz [zakresów adresów IP centrum danych Azure](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).

Funkcje usługi online, które nie są obecnie dostępne w usługi ściągania w systemie Windows Server:

- Wszystkie dane są szyfrowane podczas przesyłania i magazynowanych
- Certyfikaty klienta są tworzone i zarządzane automatycznie
- Wpisy tajne przechowywane centralnie zarządzanie [haseł lub poświadczeń](/azure/automation/automation-credentials), lub [zmienne](/azure/automation/automation-variables) takich jak nazwy serwera lub parametry połączenia
- Centralnie Zarządzaj węzłem [LCM konfiguracji](../managing-nodes/metaConfig.md#basic-settings)
- Centralnie Przypisz konfiguracje do węzłów klienta
- Konfiguracja wydania zmienia się na "canary groups" do testowania przed dotarciem do produkcji
- Graficzny raportowania
  - Szczegóły stanu na poziomie szczegółowości zasobów DSC
  - Pełne komunikaty z komputerów klienckich w celu rozwiązywania problemów
- [Integracja z usługą Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) alertów, automatycznych zadań Android/aplikacji dla systemu iOS raportowania i zgłaszania alertów

## <a name="dsc-pull-service-in-windows-server"></a>Usługa ściągania DSC w systemie Windows Server

Istnieje możliwość konfigurowania usługi ściągania, aby uruchomić w systemie Windows Server.
Należy pamiętać, że rozwiązania usługi ściągania, które są zawarte w systemie Windows Server zawiera tylko możliwości przechowywania konfiguracje/modules do pobrania i przechwytywania danych raportu w bazie danych.
Nie obejmuje wiele możliwości oferowanych przez usługę w systemie Azure, a zatem nie jest dobrym narzędziem do oceny, jak usługa będzie używana.

Usługa ściągania oferowanych w systemie Windows Server jest usługi sieci web w usługach IIS, który używa interfejsu OData, aby udostępnić pliki konfiguracji DSC węzły docelowe w przypadku tych węzłów, zadaj je.

Wymagania dotyczące korzystania z serwera ściągania:

- Serwer z systemem:
  - WMF/PowerShell 4.0 lub nowszej
  - Rola serwera IIS
  - DSC Service
- W idealnym przypadku niektóre oznacza, że generowania certyfikatu, aby zabezpieczyć poświadczenia przekazywane do lokalnego Configuration Manager (LCM) na węzłach docelowych

Najlepszym sposobem na konfigurowanie systemu Windows Server do usługi ściągania hosta jest korzysta z konfiguracji DSC.
Przykładowy skrypt znajduje się poniżej.

### <a name="supported-database-systems"></a>Systemy obsługiwanych baz danych

|WMF 4.0   |WMF 5.0  |WMF 5.1 |WMF 5.1 (system Windows Server Insider Preview 17090)|
|---------|---------|---------|---------|
|MDB     |ESENT (ustawienie domyślne), MDB |ESENT (ustawienie domyślne), MDB|ESENT (ustawienie domyślne), programu SQL Server MDB

Począwszy od wersji 17090 z [systemu Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server jest obsługiwaną opcją dla usługi ściągania (funkcja Windows *usługi DSC*). Zapewnia to nowa opcja skalowania dużych środowiskach DSC, które nie zostały przeniesione do [usługi Azure Automation DSC](/azure/automation/automation-dsc-getting-started).

> **Uwaga**: Obsługa programu SQL Server nie zostanie dodany do poprzednich wersji programu WMF 5.1 (lub starszy) i jest on dostępny w wersjach systemu Windows Server, większa niż lub równa 17090 tylko.

Aby skonfigurować serwer ściągania używać programu SQL Server, należy ustawić **SqlProvider** do `$true` i **SqlConnectionString** na prawidłowe parametry połączenia programu SQL Server. Aby uzyskać więcej informacji, zobacz [ciągi połączeń klient SQL](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).
Przykład konfiguracji programu SQL Server za pomocą **xDscWebService**, najpierw przeczytać artykuł [przy użyciu zasobów xDscWebService](#using-the-xdscwebservice-resource) a następnie przejrzyj [Sample_xDscWebServiceRegistration_ UseSQLProvider.ps1 w serwisie GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).

### <a name="using-the-xdscwebservice-resource"></a>Przy użyciu zasobów xDscWebService

Najprostszym sposobem skonfigurowania internetowego serwera ściągania jest użycie **xDscWebService** zasobu, objęte **xPSDesiredStateConfiguration** modułu.
Poniższe kroki wyjaśniają jak używać zasobów w konfiguracji, który konfiguruje usługę sieci web.

1. Wywołaj [Install-Module](/powershell/module/PowershellGet/Install-Module) polecenia cmdlet, aby zainstalować **xPSDesiredStateConfiguration** modułu.
   > [!NOTE]
   > **Install-Module** znajduje się w **PowerShellGet** moduł, który znajduje się w programie PowerShell 5.0. Możesz pobrać **PowerShellGet** modułu PowerShell 3.0 i 4.0 w [Podgląd modułów programu PowerShell PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).
2. Pobieranie certyfikatu SSL dla serwera ściągania DSC od zaufanego urzędu certyfikacji, albo w ramach organizacji lub publicznego urzędu. Certyfikat odebrany od urzędu zwykle jest w formacie PFX.
3. Zainstaluj certyfikat na węzeł, który będzie serwerem ściągania DSC w lokalizacji domyślnej, która powinna być `CERT:\LocalMachine\My`.
   - Zanotuj odcisk palca certyfikatu.
4. Wybierz identyfikator GUID, który ma być używany jako klucz rejestracji. Aby wygenerować za pomocą programu PowerShell wprowadź następujące polecenie w wierszu PS, a następnie naciśnij klawisz enter: ` [guid]::newGuid()` lub `New-Guid`. Ten klucz będzie używany przez węzły klienta jako klucza wstępnego, do uwierzytelniania podczas rejestracji. Aby uzyskać więcej informacji zobacz poniżej sekcję klucza rejestracji.
5. W środowisku PowerShell ISE Uruchom (F5) poniższy skrypt konfiguracji (zawarte w folderze przykłady **xPSDesiredStateConfiguration** modułu jako `Sample_xDscWebServiceRegistration.ps1`). Ten skrypt konfiguruje serwera ściągania.

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

        Import-DSCResource -ModuleName PSDesiredStateConfiguration
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
                UseSecurityBestPractices     = $true
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

6. Uruchom konfigurację, przekazując odcisk palca certyfikatu SSL jako **certificateThumbPrint** parametr i rejestracji identyfikator GUID klucza jako **RegistrationKey** parametru:

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a>Klucz rejestracji

Aby zezwolić na węzły, które można zarejestrować na serwerze, tak aby używały nazwy konfiguracji zamiast Identyfikatora konfiguracji klienta, klucza rejestracji, który został utworzony za pomocą powyższych konfiguracji jest zapisywany w pliku o nazwie `RegistrationKeys.txt` w `C:\Program Files\WindowsPowerShell\DscService`. Klucz rejestracji działa jako wspólny klucz tajny, używane podczas wstępnej rejestracji przez klienta z serwera ściągania. Klient wygeneruje certyfikat z podpisem własnym, który jest używany do jednoznacznego uwierzytelniania na serwerze ściągania po pomyślnym zakończeniu rejestracji. Odcisk palca certyfikatu jest przechowywana lokalnie i skojarzone z adresem URL serwera ściągania.

> [!NOTE]
> Klucze rejestracji nie są obsługiwane w programie PowerShell 4.0.

W celu skonfigurowania węzła do uwierzytelniania za pomocą serwera ściągania, klucz rejestracji musi być w metaconfiguration dla dowolnego węzła docelowego, który będzie zarejestrowanie z tym serwerem ściągania. Należy pamiętać, że **RegistrationKey** w metaconfiguration poniżej zostanie usunięty po pomyślnie zarejestrowała maszynie docelowej, a wartość musi być zgodna wartość przechowywaną w `RegistrationKeys.txt` pliku na serwerze ściągania (" 140a952b-b9d6-406b-b416-e0f759c9c0e4 "w tym przykładzie). Jest zawsze traktowany wartość klucza rejestracji bezpieczne, ponieważ wiedząc o tym pozwala na dowolnej maszynie docelowej, można zarejestrować za pomocą serwera ściągania.

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to set up pull server in previous configuration

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

> [!NOTE]
> **ReportServerWeb** sekcja umożliwia raportowanie danych, które mają być wysyłane do serwera ściągania.

Brak **ConfigurationID** właściwości w pliku metaconfiguration niejawnie oznacza, że tego serwera ściągania obsługuje protokół serwera ściągania w wersji V2, więc wstępnej rejestracji jest wymagana.
Z kolei obecność **ConfigurationID** oznacza, że jest używany protokół serwera ściągania w wersji V1 jest nie przetwarzania rejestracji.

> [!NOTE]
> W przypadku scenariusza WYPYCHANIA usterkę istnieje w bieżącej wersji, która sprawia, że konieczne jest określenie właściwości ConfigurationID w pliku metaconfiguration dla węzłów, które nigdy nie zostały zarejestrowane przy użyciu serwera ściągania. Spowoduje to wymusić protokołu serwera ściągania V1 i uniknąć komunikaty o błędach rejestracji.

## <a name="placing-configurations-and-resources"></a>Wprowadzenie do konfiguracji i zasobów

Po ściągnięcia kończy instalacji serwera, folderów, określone przez **ConfigurationPath** i **ModulePath** właściwości w konfiguracji serwera ściągania są, gdzie zostaną umieszczone modułów i konfiguracji który będzie dostępny dla węzły docelowe ściągnąć.
Te pliki muszą znajdować się w określonym formacie w kolejności dla serwera ściągania poprawnie przetworzyć je.

### <a name="dsc-resource-module-package-format"></a>Format pakietu modułu zasobów DSC

Każdy moduł zasobów musi być spakowane i nazwanych zgodnie z następującym wzorcem `{Module Name}_{Module Version}.zip`.

Na przykład, czy nazwany moduł o nazwie xWebAdminstration przy użyciu wersji modułu 3.1.2.0 `xWebAdministration_3.2.1.0.zip`.
Każda wersja modułu musi być zawarty w pliku zip jednego.
Ponieważ istnieje tylko jedną wersję zasobu w każdym pliku zip, format modułu, dodane w programie WMF 5.0 z obsługą wielu wersji modułu w pojedynczym katalogu nie jest obsługiwany.
Oznacza to, że przed pakowaniu modułów zasoby DSC do użytku z serwera ściągania należy wprowadź niewielką zmianę do struktury katalogu.
Domyślny format modułów zawierających zasobów DSC w programie WMF 5.0 jest `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.
Przed pakowania dla serwera ściągania, Usuń **{wersja modułu}** folderu, tak aby stał się ścieżkę `{Module Folder}\DscResources\{DSC Resource Folder}\`.
Dzięki tej zmianie folder zip zgodnie z powyższym opisem i umieścić te pliki zip w **ModulePath** folderu.

Użyj `New-DscChecksum {module zip file}` utworzyć sumy kontrolnej pliku dla nowo dodanym modułem.

### <a name="configuration-mof-format"></a>Format pliku MOF konfiguracji

Pliku MOF konfiguracji musi łączyć się z plikiem sumy kontrolnej, aby LCM w węźle docelowym można zweryfikować jej konfigurację.
Aby utworzyć sumy kontrolnej, wywołaj [New DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) polecenia cmdlet.
Polecenie cmdlet pobiera **ścieżki** parametr, który określa folder, w którym znajduje się plik MOF konfiguracji.
Polecenie cmdlet tworzy sumy kontrolnej pliku o nazwie `ConfigurationMOFName.mof.checksum`, gdzie `ConfigurationMOFName` to nazwa pliku mof konfiguracji.
Jeśli istnieje więcej niż jedną konfigurację pliki MOF we wskazanym folderze, suma kontrolna jest tworzony dla każdej konfiguracji w folderze.
Umieść pliki MOF i skojarzone sumy kontrolnej plików w **ConfigurationPath** folderu.

> [!NOTE]
> Jeśli zmienisz pliku MOF konfiguracji w jakikolwiek sposób, należy odtworzyć pliku sumy kontrolnej.

### <a name="tooling"></a>Narzędzia

Aby uzupełnić ustawienie, sprawdzanie poprawności i zarządzanie nimi było prostsze, serwerze ściągania następujące narzędzia są dołączone jako przykłady w najnowszej wersji modułu xPSDesiredStateConfiguration:

1. Moduł, który pomoże pakowanie modułów zasoby DSC oraz pliki konfiguracji do użycia na serwerze ściągania.
   [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).
   Poniższe przykłady:

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. Skrypt, który sprawdza poprawność serwera ściągania jest poprawnie skonfigurowany. [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).

## <a name="community-solutions-for-pull-service"></a>Rozwiązania społeczności dla usługi ściągania

Społeczność DSC ma utworzonych wiele rozwiązań, aby zaimplementować Protokół usługi ściągania.
W środowiskach lokalnych oferują one możliwości usługi ściągania oraz możliwość współtworzenia społeczności ulepszeń przyrostowych.

- [Holownik](https://github.com/powershellorg/tug)
- [DSC-TRÆK](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a>Ściąganie konfiguracji klienta

Konfigurowanie klientów ściągnięcia szczegółowo można znaleźć w następujących tematach:

- [Konfigurowanie klienta ściągania DSC przy użyciu Identyfikatora konfiguracji](pullClientConfigID.md)
- [Konfigurowanie klienta ściągania DSC przy użyciu nazw konfiguracji](pullClientConfigNames.md)
- [Konfiguracje częściowe](partialConfigs.md)

## <a name="see-also"></a>Zobacz też

- [Program Windows PowerShell Desired State Configuration — omówienie](../overview/overview.md)
- [Realizacja konfiguracji](enactingConfigurations.md)
- [Używanie serwera raportów platformy DSC](reportServer.md)
- [[MS-DSCPM]: Desired State Configuration protokołu modelu ściągania](https://msdn.microsoft.com/library/dn393548.aspx)
- [[MS-DSCPM]: Desired State Configuration Errata protokołu modelu ściągania](https://msdn.microsoft.com/library/mt612824.aspx)
