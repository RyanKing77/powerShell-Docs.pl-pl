---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Ulepszenia DSC w programie WMF 5.1
ms.openlocfilehash: e7f20bfa865777aeac8f083959782317cfdf6cde
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856231"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a>Ulepszenia w Desired State Configuration (DSC) w programie WMF 5.1

## <a name="dsc-class-resource-improvements"></a>Ulepszenia zasobów klasy DSC

W program WMF 5.1 usunęliśmy następujące znane problemy:

- Get-DscConfiguration może zwracać wartości puste (null) lub błędy, jeśli typ tabeli złożone i skrótu jest zwracana przez funkcję Get() zasobu DSC oparte na klasach.
- Get-DscConfiguration zwraca błąd, jeśli poświadczeń Uruchom jako jest używany w konfiguracji DSC.
- Nie można używać zasobów na podstawie klasy złożonej konfiguracji.
- Start-DscConfiguration zawiesza się, jeśli właściwość swój własny typ oparte na klasach zasobów.
- Oparte na klasach zasobów nie można użyć jako zasób wyłączności.

## <a name="dsc-resource-debugging-improvements"></a>Zasób DSC ulepszenia debugowania

W programie WMF 5.0 debuger programu PowerShell nie zatrzymają w metodzie oparte na klasach zasobów (Get/Set/Test) bezpośrednio. W program WMF 5.1 debuger zatrzymuje się na metody oparte na klasach zasobów w taki sam sposób jak w przypadku metod zasoby oparte na pliku MOF.

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a>DSC pull klient obsługuje protokół TLS 1.1 i TLS 1.2

Wcześniej klienta ściągania DSC obsługiwane tylko SSL3.0 lub TLS1.0 za pośrednictwem połączenia HTTPS. Przy wymuszonego, aby użyć bardziej bezpieczne protokoły, klienta ściągania może przestać działać. W program WMF 5.1 klienta ściągania DSC nie są już obsługuje protokół SSL 3.0 i dodaje obsługę bardziej bezpieczne protokoły TLS 1.1 i TLS 1.2.

## <a name="improved-pull-server-registration"></a>Rejestracja serwera ściągania ulepszone

We wcześniejszych wersjach programu WMF równoczesnych rejestracji/zgłoszenie żądania do serwera ściągania DSC podczas korzystania z bazy danych ESENT doprowadziłoby do LCM, których nie można zarejestrować i/lub raportu. W takiej sytuacji dzienniki zdarzeń na serwerze ściągania występuje błąd "Nazwa wystąpienia już w użyciu". Było to spowodowane przez nieprawidłowy wzorzec używany do uzyskiwania ESENT bazy danych w scenariuszu wielowątkowych. Ten problem został rozwiązany w program WMF 5.1. Jednoczesnych rejestracji lub raportowania (obejmujące ESENT bazy danych) działa poprawnie WMF 5.1. Ten problem ma zastosowanie tylko do bazy danych ESENT i nie ma zastosowania do bazy danych OLE DB.

## <a name="enable-circular-log-on-esent-database-instance"></a>Włącz dziennik cykliczne w wystąpieniu bazy danych ESENT

W wersji eariler DSC PullServer pliki dziennika bazy danych ESENT zostały zapełnia się miejsca na dysku becouse pullserver, utworzenia wystąpienia bazy danych jest bez logowanie cykliczne. W tej wersji masz możliwość sterowania zachowaniem tego wystąpienia przy użyciu pliku web.config pullserver logowanie cykliczne. Domyślnie CircularLogging jest ustawiona na wartość TRUE.

```xml
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="wow64-support-for-configuration-keyword"></a>Obsługa środowiska WOW64 na potrzeby słowa kluczowego konfiguracji

`Configuration` — Słowo kluczowe jest teraz obsługiwana w emulatorze WOW64 na komputerze 64-bitowym. Oznacza to, że konfiguracji DSC mogą być definiowane i kompilowany w obrębie 32-bitowy proces takich jak Windows PowerShell ISE (x 86) uruchomionego na komputerze 64-bitowych.

## <a name="pull-partial-configuration-naming-convention"></a>Ściągnij konwencji nazewnictwa częściowe konfiguracji

W poprzedniej wersji konwencji nazewnictwa częściowe konfiguracji został, czy nazwa pliku MOF usługi ściągania serwer/powinna odpowiadać nazwie częściowe konfiguracji, w określonego w ustawieniach Menedżera konfiguracji lokalnej, które z kolei muszą być zgodne Nazwa konfiguracji jest osadzony w pliku MOF.

Zobacz poniższe migawki:

- Ustawienia konfiguracji lokalnej, które definiuje częściowe konfiguracji, który węzeł może odbierać.

  ![Przykładowe metaconfiguration](../images/MetaConfigPartialOne.png)

- Przykładowa definicja częściowe konfiguracji

  ```powershell
  Configuration PartialOne
  {
      Node('localhost')
      {
          File test
          {
              DestinationPath = "$env:TEMP\partialconfigexample.txt"
              Contents = 'Partial Config Example'
          }
      }
  }
  PartialOne
  ```

- "ConfigurationName" osadzona w wygenerowanym pliku MOF.

  ![Przykładowy plik mof wygenerowany](../images/PartialGeneratedMof.png)

- Nazwa pliku w repozytorium konfiguracji ściągania

  ![Nazwa pliku w repozytorium konfiguracji](../images/PartialInConfigRepository.png)

  Nazwa usługi w usłudze Azure Automation wygenerowanych plików MOF jako `<ConfigurationName>.<NodeName>.mof`. Dlatego konfiguracji poniżej kompiluje, aby PartialOne.localhost.mof.

  To uniemożliwił do ściągnięcia jeden częściowe konfiguracji z usługi Azure Automation.

  ```powershell
  Configuration PartialOne
  {
      Node('localhost')
      {
          File test
          {
              DestinationPath = "$env:TEMP\partialconfigexample.txt"
              Contents = 'Partial Config Example'
          }
      }
  }
  PartialOne
  ```

  W program WMF 5.1 częściowe konfiguracji w pull server/service może mieć nazwę jako `<ConfigurationName>.<NodeName>.mof`. Ponadto jeśli maszyna jest ściąganie konfiguracji jednego z ściąganie usługa następnie plik konfiguracji do repozytorium konfiguracji serwera ściągania mogą mieć dowolną nazwę pliku. Ta elastyczność nazewnictwa pozwala na zarządzanie węzły częściowo przez usługę Azure Automation, gdzie niektóre konfiguracji dla węzła pochodzi z usługi Azure Automation DSC i częściowe konfiguracji, który można zarządzać lokalnie.

  Metaconfiguration poniżej skonfigurowanie węzła jako zarządzane, zarówno lokalnie, jak również przez usługę Azure Automation do usługi.

  ```powershell
  [DscLocalConfigurationManager()]
  Configuration RegistrationMetaConfig
  {
      Settings
      {
          RefreshFrequencyMins = 30
          RefreshMode = "PULL"
      }

      ConfigurationRepositoryWeb web
      {
          ServerURL =  $endPoint
          RegistrationKey = $registrationKey
          ConfigurationNames = $configurationName
      }

      # Partial configuration managed by Azure Automation service.
      PartialConfiguration PartialConfigurationManagedByAzureAutomation
      {
          ConfigurationSource = "[ConfigurationRepositoryWeb]Web"
      }

      # This partial configuration is managed locally.
      PartialConfiguration OnPremisesConfig
      {
          RefreshMode = "PUSH"
          ExclusiveResources = @("Script")
      }

  }

  RegistrationMetaConfig
  Set-DscLocalConfigurationManager -Path .\RegistrationMetaConfig -Verbose
  ```

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a>Za pomocą PsDscRunAsCredential za pomocą DSC zasoby złożone

Dodaliśmy obsługę [PsDscRunAsCredential](/powershell/dsc/configurations/runAsUser) za pomocą DSC [złożonego](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) zasobów.

Teraz można określić wartość dla **PsDscRunAsCredential** korzystając zasoby złożone w konfiguracji. Jeśli zostanie określony, wszystkie zasoby są uruchamiane wewnątrz złożonego zasobów w jako użytkownika Uruchom jako. Jeśli złożonego zasobów wywołuje inny zasób złożonego, te zasoby również są wykonywane jako użytkownika Uruchom jako. Poświadczenia programu RunAs są propagowane do dowolnego poziomu hierarchii złożonego zasobów. Określa wartość dla dowolnego zasobu wewnątrz złożonego zasobów **PsDscRunAsCredential**, błąd scalania wyniki podczas kompilacji konfiguracji.

W tym przykładzie przedstawiono sposób użycia za pomocą [WindowsFeatureSet](/powershell/dsc/reference/resources/windows/windowsfeaturesetresource) złożonego zasobów zawartych w PSDesiredStateConfiguration module.

```powershell
Configuration InstallWindowsFeature
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        WindowsFeatureSet features
        {
            Name = @("Telnet-Client","SNMP-Service")
            Ensure = "Present"
            IncludeAllSubFeature = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost'
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

InstallWindowsFeature -ConfigurationData $configData
```

## <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a>Zezwalanie na identycznych powielonych zasobów w konfiguracji

DSC Zezwalaj lub nie obsługiwać sprzeczne definicje zasobów w ramach konfiguracji. Zamiast próbować rozwiązać konflikt, ją po prostu nie powiedzie się. Jak ponowne użycie konfiguracji staje się bardziej wykorzystywany przez zasoby złożone, konflikty itp. nastąpi częściej. W przypadku identyczne sprzecznych definicji zasobu DSC należy inteligentne i zezwolić na to. W tej wersji obsługiwane jest posiadanie wielu wystąpień zasobów, które mają identyczne definicje:

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

W poprzednich wersjach wynik będzie, że zainstalowano kompilacji nie powiodło się z powodu konfliktu między WindowsFeature FE_IIS i wystąpień WindowsFeature Worker_IIS próby zapewnienia rolę "Serwer sieci Web". Należy zauważyć, że *wszystkich* właściwości, które są konfigurowane są identyczne w dwóch konfiguracjach. Ponieważ *wszystkich* właściwości w te dwa zasoby są identyczne, wynikiem będzie teraz pomyślnej kompilacji.

Jeśli dowolne z właściwości różnią się między dwa zasoby, one nie zostanie uwzględniony identyczne i kompilacja zakończy się niepowodzeniem.

## <a name="dsc-module-and-configuration-signing-validations"></a>Moduł DSC i podpisywania operacji sprawdzania poprawności konfiguracji

W DSC konfiguracji i modułów są dystrybuowane do komputerów zarządzanych z serwera ściągania. W przypadku naruszenia zabezpieczeń serwera ściągania osoba atakująca może potencjalnie modyfikować konfiguracje i modułów na serwerze ściągania i jest dystrybuowane do wszystkich zarządzanych węzłów.

Program WMF 5.1 DSC obsługuje sprawdzanie podpisów cyfrowych w katalogu i konfiguracji (. Pliki MOF). Ta funkcja zapobiega wykonywania konfiguracji lub plikach modułów, które nie są podpisane przez zaufane osoby podpisującej lub które zostały naruszone po zostały podpisane przez zaufane osoby podpisującej węzłów.

### <a name="how-to-sign-configuration-and-module"></a>Jak zarejestrować konfiguracji i modułów

- Pliki konfiguracji (. Pliki MOF): Istniejące polecenia cmdlet programu PowerShell [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) jest rozszerzona na potrzeby obsługi podpisywania plików MOF.
- Moduły: Podpisywanie modułów można to zrobić, rejestrując odpowiedniego katalogu modułu wykonując następujące czynności:
  1. Utwórz plik w katalogu: Plik wykazu zawiera zbiór skróty kryptograficzne lub odciski palców. Każdy odcisk palca odnosi się do pliku, który znajduje się w module. Nowe polecenie cmdlet [New FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), została dodana do Zezwól użytkownikom na tworzenie plik katalogu dla swojego modułu.
  2. Utwórz plik w katalogu: Użyj [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) do podpisania pliku wykazu.
  3. Umieść plik wykazu znajdujące się w folderze modułu. Zgodnie z Konwencją plik do katalogu modułu powinna zostać umieszczona w folderze modułu o nazwie identycznej z nazwą modułu.

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a>Ustawienia LocalConfigurationManager, aby umożliwić sprawdzanie poprawności podpisywania

#### <a name="pull"></a>Ściągnij

LocalConfigurationManager węzła przeprowadza weryfikację podpisywania modułów i konfiguracji, w oparciu o bieżące ustawienia. Domyślnie Weryfikacja podpisu jest wyłączona. Weryfikacja podpisu można włączyć poprzez dodanie bloku "SignatureValidation" do definicji metadanych konfiguracji węzła jak pokazano poniżej:

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'
    }

    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # If the TrustedStorePath property is provided then LCM will use the custom path. Otherwise, the LCM will use default trusted store path (Cert:\LocalMachine\DSCStore) to find the signing certificate.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

Ustawienie metaconfiguration powyżej w węźle umożliwia weryfikację podpisu na konfiguracje pobrane i modułów. Local Configuration Manager wykonuje następujące kroki, aby sprawdzanie podpisów cyfrowych.

1. Weryfikuje podpis w pliku konfiguracji (. Nadaje MOF) przy użyciu `Get-AuthenticodeSignature` polecenia cmdlet.
2. Sprawdź, czy urząd certyfikacji, który autoryzowane osoby podpisującej jest zaufany.
3. Pobierz moduł lub zasobu zależności w konfiguracji w tymczasowej lokalizacji.
4. Zweryfikować podpisu wykazu zawarte wewnątrz modułu.
   - Znajdź `<moduleName>.cat` i sprawdzić jego za pomocą podpisu `Get-AuthenticodeSignature`.
   - Sprawdź, czy urząd certyfikacji, który uwierzytelnił podpisującego jest zaufany.
   - Sprawdź, nie został zmodyfikowany zawartość modułów za pomocą nowego polecenia cmdlet `Test-FileCatalog`.
5. `Install-Module` Aby `$env:ProgramFiles\WindowsPowerShell\Modules\`
6. Konfiguracja procesu

> [!NOTE]
> Weryfikacja podpisu na katalog modułu i konfiguracji jest realizowane wyłącznie, gdy po raz pierwszy lub w przypadku, gdy moduł jest pobierany i instalowany, konfiguracja jest stosowana do systemu.
> Przebiegi spójności nie weryfikują podpisu Current.mof lub jego zależności modułu. Jeśli weryfikacja nie powiodła się na każdym etapie, na przykład jeśli konfiguracji są pobierane z serwera ściągania jest podpisany, a następnie przetwarzania konfiguracji kończy się błędem pokazany poniżej i zostaną usunięte wszystkie pliki tymczasowe.

![Przykładowa konfiguracja danych wyjściowych błędu](../images/PullUnsignedConfigFail.png)

Podobnie ściąganie modułu, którego katalog nie jest podpisany wyniki w następujący błąd:

![Przykładowe błąd danych wyjściowych modułu](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a>wypychania

Konfiguracja dostarczane za pomocą instalacji wypychanej może dało się w ich źródle przed dostarczeniem jej do węzła. Local Configuration Manager wykonuje podobne kroki weryfikacji podpisu konfiguracje nastąpiło wypychanie oraz opublikowane. Poniżej znajduje się pełny przykład Weryfikacja podpisu do wypychania.

- Włącz weryfikację podpisu na węźle.

  ```powershell
  [DSCLocalConfigurationManager()]
  Configuration EnableSignatureValidation
  {
      Settings
      {
          RefreshMode = 'PUSH'
      }
      SignatureValidation validations{
          TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
          SignedItemType =  'Configuration','Module'
      }

  }
  EnableSignatureValidation
  Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
  ```

- Utwórz przykładowy plik konfiguracji.

  ```powershell
  # Sample configuration
  Configuration Test
  {

      File foo
      {
          DestinationPath =  "$env:TEMP\signingTest.txt"
          Contents = "ABC"
      }
  }
  Test
  ```

- Spróbuj wypychaniu można znaleźć pliku konfiguracji bez znaku w do węzła.

  ```powershell
  Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
  ```

  ![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

- Zaloguj się przy użyciu certyfikatu podpisywania kodu pliku konfiguracji.

  ![SignMofFile](../images/SignMofFile.png)

- Spróbuj wypychanie podpisany plik MOF.

  ![SignMofFile](../images/PushSignedMof.png)
