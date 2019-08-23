---
ms.date: 03/04/2019
keywords: DSC, PowerShell, konfiguracja, instalacja
title: Usługa ściągania platformy DSC
ms.openlocfilehash: 865eae5813e0c7b656a4158f0b1350e60f1e3291
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986539"
---
# <a name="desired-state-configuration-pull-service"></a>Usługa ściągania konfiguracji żądanego stanu

> [!IMPORTANT]
> Serwer ściągania (Windows Feature *DSC-Service*) jest obsługiwanym składnikiem systemu Windows Server, ale nie ma żadnych planów do oferowania nowych funkcji. Zalecane jest, aby rozpocząć przechodzenie zarządzanych klientów do [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (obejmuje funkcje wykraczające poza serwer ściągający w systemie Windows Server) lub jedno z rozwiązań społecznościowych wymienionych w [tym miejscu](pullserver.md#community-solutions-for-pull-service).

Lokalne Configuration Manager mogą być zarządzane centralnie przez rozwiązanie usługi ściągania.
W przypadku korzystania z tej metody zarządzany węzeł jest rejestrowany w usłudze i przypisuje konfigurację w ustawieniach LCM.
Konfiguracja i wszystkie zasoby DSC wymaganych jako zależności konfiguracji są pobierane na maszynę i używane przez LCM do zarządzania konfiguracją.
Informacje o stanie zarządzanej maszyny są przekazywane do usługi na potrzeby raportowania.
Pojęcie to jest nazywane "usługą ściągania".

Bieżące opcje usługi ściągania obejmują:

- Azure Automation usługi konfiguracji żądanego stanu
- Usługa ściągania działająca w systemie Windows Server
- Społeczność z obsługiwanymi rozwiązaniami "open source"
- Udział SMB

**Zalecanym rozwiązaniem**i opcją z największą liczbą dostępnych funkcji jest [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).

Usługa platformy Azure umożliwia zarządzanie węzłami lokalnie w prywatnych centrach danych lub w chmurach publicznych, takich jak Azure i AWS.
W przypadku środowisk prywatnych, w których serwery nie mogą łączyć się bezpośrednio z Internetem, należy rozważyć ograniczenie ruchu wychodzącego tylko do opublikowanego zakresu adresów IP platformy Azure (zobacz [zakres adresów IP centrum danych platformy Azure](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).

Funkcje usługi online, które nie są obecnie dostępne w usłudze ściągania w systemie Windows Server, obejmują:

- Wszystkie dane są szyfrowane podczas przesyłania i przechowywania
- Certyfikaty klienta są tworzone i zarządzane automatycznie
- Wpisy tajne do centralnego zarządzania [hasłami/poświadczeniami](/azure/automation/automation-credentials)lub [zmiennymi](/azure/automation/automation-variables) , takimi jak nazwy serwerów lub parametry połączenia
- Centralne zarządzanie konfiguracją [LCM](../managing-nodes/metaConfig.md#basic-settings) Node
- Centralne przypisywanie konfiguracji do węzłów klienta
- Wprowadzenie zmian w konfiguracji "grup Kanaryjskich" w celu przetestowania przed osiągnięciem produkcji
- Raportowanie graficzne
  - Szczegóły stanu na poziomie szczegółowości zasobów DSC
  - Pełne komunikaty o błędach z komputerów klienckich w celu rozwiązywania problemów
- [Integracja z usługą Azure log Analytics](/azure/automation/automation-dsc-diagnostics) na potrzeby alertów, zautomatyzowanych zadań, aplikacji systemu Android/iOS na potrzeby raportowania i alertów

## <a name="dsc-pull-service-in-windows-server"></a>Usługa ściągania DSC w systemie Windows Server

Istnieje możliwość skonfigurowania usługi ściągania do uruchamiania w systemie Windows Server.
Zaleca się, aby rozwiązanie usługi ściągania dołączone do systemu Windows Server zawierało tylko możliwości przechowywania konfiguracji/modułów do pobierania i przechwytywania danych raportu w bazie danych.
Nie obejmuje to wielu możliwości oferowanych przez usługę na platformie Azure i dlatego nie jest dobrym narzędziem do oceny sposobu korzystania z usługi.

Usługa ściągania oferowana w systemie Windows Server jest usługą sieci Web w usługach IIS, która korzysta z interfejsu OData do udostępniania plików konfiguracji DSC węzłom docelowym, gdy te węzły poproszą z nimi.

Wymagania dotyczące korzystania z serwera ściągania:

- Serwer z systemem:
  - WMF/PowerShell 4,0 lub nowszej
  - Rola serwera IIS
  - Usługa DSC
- W idealnym przypadku niektóre sposoby generowania certyfikatu w celu zabezpieczenia poświadczeń przekazaną do lokalnego Configuration Manager (LCM) na węzłach docelowych

Najlepszym sposobem skonfigurowania usługi ściągania systemu Windows Server jest użycie konfiguracji DSC.
Poniżej przedstawiono przykładowy skrypt.

### <a name="supported-database-systems"></a>Obsługiwane systemy baz danych

|WMF 4,0   |WMF 5.0  |WMF 5.1 |WMF 5,1 (wersja zapoznawcza programu Windows Server w wersji zapoznawczej 17090)|
|---------|---------|---------|---------|
|MDB     |ESENT (domyślnie), MDB |ESENT (domyślnie), MDB|ESENT (domyślnie), SQL Server, MDB

Począwszy od wersji 17090 wersji zapoznawczej programu [Windows Server](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server jest obsługiwaną opcją dla usługi ściągania (Windows Feature *DSC-Service*). Zapewnia to nową opcję skalowania dużych środowisk DSC, które nie zostały zmigrowane do [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).

> [!NOTE]
> Obsługa SQL Server nie zostanie dodana do poprzednich wersji programu WMF 5,1 (lub starszych) i będzie dostępna tylko w systemie Windows Server w wersji większej niż lub równej 17090.

Aby skonfigurować serwer ściągania tak, aby używał SQL Server , należy ustawić element `$true` na i SqlConnectionString na prawidłowe parametry połączenia SQL Server. Aby uzyskać więcej informacji, zobacz [Parametry połączenia SqlClient](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).
Aby zapoznać się z przykładem konfiguracji SQL Server z **xDscWebService**, najpierw Przeczytaj [przy użyciu zasobu xDscWebService](#using-the-xdscwebservice-resource) , a następnie przejrzyj [Sample_xDscWebServiceRegistration_UseSQLProvider. ps1 w serwisie GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).

### <a name="using-the-xdscwebservice-resource"></a>Korzystanie z zasobu xDscWebService

Najprostszym sposobem skonfigurowania serwera ściągania sieci Web jest użycie zasobu **xDscWebService** znajdującego się w module **xPSDesiredStateConfiguration** .
Poniższe kroki wyjaśniają, jak używać zasobu w konfiguracji, która konfiguruje usługę sieci Web.

1. Wywołaj polecenie cmdlet [Install-module](/powershell/module/PowershellGet/Install-Module) , aby zainstalować moduł **xPSDesiredStateConfiguration** .
   > [!NOTE]
   > Polecenie **Install-module** jest dołączone do modułu **PowerShellGet** , który jest zawarty w programie PowerShell 5,0. Moduł **PowerShellGet** dla programu PowerShell 3,0 i 4,0 można pobrać na stronie [PackageManagement programu PowerShell w wersji](https://www.microsoft.com/en-us/download/details.aspx?id=49186)zapoznawczej.
2. Pobierz certyfikat protokołu SSL dla serwera ściągania DSC z zaufanego urzędu certyfikacji w ramach organizacji lub urzędu publicznego. Certyfikat otrzymany od urzędu jest zwykle w formacie PFX.
3. Zainstaluj certyfikat w węźle, który będzie serwerem ściągania DSC w domyślnej lokalizacji, która powinna być `CERT:\LocalMachine\My`.
   - Zanotuj odcisk palca certyfikatu.
4. Wybierz identyfikator GUID, który ma być używany jako klucz rejestracji. Aby wygenerować go przy użyciu programu PowerShell, wprowadź następujące w wierszu polecenia PS i naciśnij `[guid]::newGuid()` klawisz `New-Guid`ENTER: lub. Ten klucz będzie używany przez węzły klienta jako klucz współużytkowany do uwierzytelniania podczas rejestracji. Aby uzyskać więcej informacji, zobacz sekcję klucz rejestracji poniżej.
5. W programie PowerShell ISE Uruchom (F5) następujący skrypt konfiguracyjny (zawarty w folderze przykłady modułu **xPSDesiredStateConfiguration** jako `Sample_xDscWebServiceRegistration.ps1`). Ten skrypt konfiguruje serwer ściągania.

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

6. Uruchom konfigurację, przekazując odcisk palca certyfikatu SSL jako parametr **certificateThumbPrint** i klucz rejestracji identyfikatora GUID jako parametr **RegistrationKey** :

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

Aby umożliwić węzłom klienckim zarejestrowanie się na serwerze, tak aby mogły używać nazw konfiguracji zamiast identyfikatora konfiguracji, klucz rejestracji utworzony przez powyższą konfigurację jest zapisywany w pliku o nazwie `RegistrationKeys.txt` w. `C:\Program Files\WindowsPowerShell\DscService` Klucz rejestracji działa jako wspólny klucz tajny używany podczas wstępnej rejestracji przez klienta z serwerem ściągania. Klient wygeneruje certyfikat z podpisem własnym, który jest używany do jednoznacznego uwierzytelniania na serwerze ściągania po pomyślnym zakończeniu rejestracji. Odcisk palca tego certyfikatu jest przechowywany lokalnie i skojarzony z adresem URL serwera ściągania.

> [!NOTE]
> Klucze rejestracji nie są obsługiwane w programie PowerShell 4,0.

W celu skonfigurowania węzła do uwierzytelniania przy użyciu serwera ściągania klucz rejestracji musi znajdować się w konfiguracji z dowolnego węzła docelowego, który zostanie zarejestrowany na tym serwerze ściągania. Należy pamiętać, że **RegistrationKey** w konfiguracji poniżej jest usuwany po pomyślnym zarejestrowaniu maszyny docelowej i że wartość musi być zgodna z wartością przechowywaną `RegistrationKeys.txt` w pliku na serwerze ściągania (" 140a952b-b9d6-406B-b416-e0f759c9c0e4 "w tym przykładzie). Należy zawsze traktować bezpieczną wartość klucza rejestracji, ponieważ wiedzą, że każdy komputer docelowy może zarejestrować się na serwerze ściągania.

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
> Sekcja **ReportServerWeb** umożliwia wysyłanie danych raportowania do serwera ściągania.

Brak właściwości **ConfigurationID** w pliku konfiguracji niejawnie oznacza, że serwer ściągania obsługuje wersję v2 protokołu serwera ściągania, więc wymagana jest rejestracja wstępna.
Z drugiej strony, obecność **ConfigurationID** oznacza, że używana jest wersja v1 protokołu serwera ściągania i nie ma żadnego przetwarzania rejestracji.

> [!NOTE]
> W scenariuszu WYPYCHANia usterka istnieje w bieżącej wersji, która wymaga zdefiniowania w pliku konfiguracji właściwości ConfigurationID dla węzłów, które nigdy nie zostały zarejestrowane na serwerze ściągania. Spowoduje to wymuszenie protokołu serwera ściągania V1 i uniknięcie komunikatów o niepowodzeniu rejestracji.

## <a name="placing-configurations-and-resources"></a>Umieszczanie konfiguracji i zasobów

Po zakończeniu instalacji serwera ściągania foldery zdefiniowane przez właściwości **ConfigurationPath** i **ModulePath** w konfiguracji serwera ściągania są miejscem, w którym zostaną umieszczone moduły i konfiguracje, które będą dostępne dla węzłów docelowych do ściągnięcia.
Te pliki muszą być w określonym formacie, aby serwer ściągania mógł prawidłowo je przetworzyć.

### <a name="dsc-resource-module-package-format"></a>Format pakietu modułu zasobów DSC

Każdy moduł zasobów musi być spakowany i nazwany zgodnie z poniższym wzorcem `{Module Name}_{Module Version}.zip`.

Na przykład moduł o nazwie xWebAdminstration z wersją modułu 3.1.2.0 powinien mieć nazwę `xWebAdministration_3.1.2.0.zip`.
Każda wersja modułu musi być zawarta w pojedynczym pliku zip.
Ponieważ w każdym pliku zip istnieje tylko jedna wersja zasobu, format modułu dodany w programie WMF 5,0 z obsługą wielu wersji modułów w jednym katalogu nie jest obsługiwany.
Oznacza to, że przed spakowaniem modułów zasobów DSC do użycia z serwerem ściągania należy wprowadzić małą zmianę w strukturze katalogów.
Domyślny format modułów zawierających zasób DSC w programie WMF 5,0 to `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.
Przed spakowaniem na serwer ściągania Usuń folder **{module Version}** , aby ścieżka się popełniła `{Module Folder}\DscResources\{DSC Resource Folder}\`.
W przypadku tej zmiany należy umieścić folder zip zgodnie z powyższym opisem i umieocić te pliki zip w folderze **ModulePath** .

Użyj `New-DscChecksum {module zip file}` polecenia, aby utworzyć plik sumy kontrolnej dla nowo dodanego modułu.

### <a name="configuration-mof-format"></a>Format MOF konfiguracji

Plik MOF konfiguracji musi być sparowany z plikiem sum kontrolnych tak, aby LCM w węźle docelowym mógł sprawdzić poprawność konfiguracji.
Aby utworzyć sumę kontrolną, wywołaj polecenie cmdlet [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) .
Polecenie cmdlet przyjmuje parametr **Path** , który określa folder, w którym znajduje się plik MOF konfiguracji.
Polecenie cmdlet tworzy plik sumy kontrolnej `ConfigurationMOFName.mof.checksum`o nazwie `ConfigurationMOFName` , gdzie jest nazwą pliku MOF konfiguracji.
Jeśli w określonym folderze znajduje się więcej niż jeden plik MOF konfiguracji, zostanie utworzona suma kontrolna dla każdej konfiguracji w folderze.
Umieść pliki MOF i skojarzone z nimi pliki sum kontrolnych w folderze **ConfigurationPath** .

> [!NOTE]
> Jeśli plik MOF konfiguracji zostanie zmieniony w dowolny sposób, należy również ponownie utworzyć plik sum kontrolnych.

### <a name="tooling"></a>Narzędzi

W celu ułatwienia konfigurowania, weryfikowania i zarządzania serwerem ściągania są dostępne następujące narzędzia jako przykłady w najnowszej wersji modułu xPSDesiredStateConfiguration:

1. Moduł, który będzie pomocny przy pakowaniu modułów zasobów DSC i plików konfiguracji do użycia na serwerze ściągania.
   [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).
   Poniższe przykłady:

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. Skrypt, który sprawdza poprawność serwera ściągania, jest poprawnie skonfigurowany. [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).

## <a name="community-solutions-for-pull-service"></a>Rozwiązania społeczności dla usługi ściągania

Społeczność DSC utworzyła wiele rozwiązań do wdrożenia protokołu usługi ściągania.
W przypadku środowisk lokalnych te oferty oferują możliwości usługi ściągania i możliwość współtworzenia do społeczności użytkowników przy użyciu ulepszeń przyrostowych.

- [Tug](https://github.com/powershellorg/tug)
- [DSC-TRÆK](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a>Konfiguracja klienta ściągania

W poniższych tematach opisano szczegółowo konfigurację klientów ściągania:

- [Konfigurowanie klienta ściągania DSC przy użyciu identyfikatora konfiguracji](pullClientConfigID.md)
- [Konfigurowanie klienta ściągania DSC przy użyciu nazw konfiguracji](pullClientConfigNames.md)
- [Konfiguracje częściowe](partialConfigs.md)

## <a name="see-also"></a>Zobacz też

- [Przegląd konfiguracji żądanego stanu programu Windows PowerShell](../overview/overview.md)
- [Realizacja konfiguracji](enactingConfigurations.md)
- [Używanie serwera raportów platformy DSC](reportServer.md)
- [[MS-DSCPM]: Protokół ściągania konfiguracji żądanego stanu](https://msdn.microsoft.com/library/dn393548.aspx)
- [[MS-DSCPM]: Konfiguracja żądanego stanu Errata modelu ściągania](https://msdn.microsoft.com/library/mt612824.aspx)
