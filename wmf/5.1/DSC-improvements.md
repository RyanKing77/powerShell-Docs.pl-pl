---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
title: "Ulepszenia usługi Konfiguracja DSC w WMF 5.1"
ms.openlocfilehash: ce897dab2344455453e9bf2d0b5a897f9abb4392
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2017
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a>Ulepszenia w konfiguracji żądanego stanu (DSC) w wersji 5.1 WMF

## <a name="dsc-class-resource-improvements"></a>Ulepszenia zasobów klasy DSC

W wersji 5.1 WMF Naprawiono następujące znane problemy:
* Get-DscConfiguration może zwrócić wartości puste (null) lub błędy, jeśli typem tabeli złożone i skrótu jest zwracane przez funkcję Get() zasobu DSC klasy.
* Get-DscConfiguration zwraca błąd, jeśli poświadczeń Uruchom jako jest używane w konfiguracji DSC.
* Nie można używać zasobów na podstawie klasy w złożonych konfiguracji.
* Start-DscConfiguration zawiesza się, jeśli na podstawie klasy zasób ma właściwość jego własnego typu.
* Na podstawie klasy zasobu nie można użyć jako zasób wyłącznego.


## <a name="dsc-resource-debugging-improvements"></a>Ulepszenia debugowania zasobów DSC
W programie WMF 5.0 debuger programu PowerShell nie zatrzymał się w metodzie zasobów na podstawie klasy (Test-Get/Set) bezpośrednio.
W wersji 5.1 WMF debuger zatrzymuje się na metodę klasy zasobów w taki sam sposób jak w przypadku zasobów opartych na plikach MOF metody.

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a>Klient ściągania usługi Konfiguracja DSC obsługuje protokołu TLS 1.1 i TLS 1.2 
Wcześniej klient ściągania usługi Konfiguracja DSC obsługiwane tylko SSL3.0 i TLS1.0 za pośrednictwem połączenia HTTPS. Gdy wymuszono są używane protokoły bardziej bezpieczne, klienta ściągania będzie przestaną działać. W wersji 5.1 WMF nie jest już klienta ściągania usługi Konfiguracja DSC protokół SSL 3.0 i dodaje obsługę bezpieczniejsze protokoły TLS 1.1 i TLS 1.2.  

## <a name="improved-pull-server-registration"></a>Rejestracja serwera ściągania ulepszone ##

We wcześniejszych wersjach WMF równoczesnych rejestracji/reporting żądania do serwera ściągania usługi Konfiguracja DSC podczas korzystania z bazy danych ESENT doprowadziłoby do LCM nie powiodło się zarejestrować i/lub raportu. W takiej sytuacji dzienniki zdarzeń na serwerze ściągania ma błędu "Nazwa wystąpienia już w użyciu".
Jest to spowodowane nieprawidłowy wzorzec używane do dostępu do bazy danych ESENT w scenariuszu wielowątkowych. W wersji 5.1 WMF ten problem został rozwiązany. Równoczesnych rejestracji lub wykonywania raportu (związanej z bazą danych ESENT) działa prawidłowo w wersji 5.1 WMF. Ten problem dotyczy tylko ESENT bazy danych i nie ma zastosowania do bazy danych OLEDB. 

## <a name="enable-circular-log-on-esent-database-instance"></a>Włącz cyklicznego pliku dziennika ESENT wystąpienia bazy danych
W wersji eariler DSC PullServer pliki dziennika bazy danych ESENT zostały zapełnia się miejsca na dysku becouse pullserver, utworzenia wystąpienia bazy danych trwa bez logowanie cykliczne. W tej wersji istnieje możliwość kontrolowania zachowania logowanie cykliczne wystąpienia przy użyciu pliku web.config pullserver. Domyślnie CircularLogging ma wartość TRUE.
```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```
## <a name="pull-partial-configuration-naming-convention"></a>Ściąganie konwencji nazewnictwa częściowe konfiguracji
W poprzednich wersjach konwencji nazewnictwa w przypadku konfiguracji z częściowa został czy nazwa pliku MOF w usłudze ściągania serwer/powinna odpowiadać nazwie częściowe konfiguracji określone w ustawieniach menedżera lokalnej konfiguracji, które z kolei muszą być zgodne Nazwa konfiguracji jest osadzony w pliku MOF. 

Zobacz migawki poniżej:

• Lokalnych ustawień konfiguracji, które definiuje konfigurację częściowy, który może odbierać węzła.

![Metakonfigurację próbki](../images/MetaConfigPartialOne.png)

• Przykładowej konfiguracji z częściowa definicji 

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

• "ConfigurationName" osadzona w wygenerowanym pliku MOF.

![Przykładowy plik mof wygenerowany](../images/PartialGeneratedMof.png)

• FileName w repozytorium konfiguracji replikacji ściąganej 

![Nazwa pliku w repozytorium konfiguracji](../images/PartialInConfigRepository.png)

Nazwa usługi Automatyzacja Azure wygenerowanych plików MOF jako `<ConfigurationName>.<NodeName>.mof`. Dlatego konfiguracja poniżej kompiluje do PartialOne.localhost.mof.

To uniemożliwił do ściągania jedną z częściowa konfiguracji od usługi Automatyzacja Azure.

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

W wersji 5.1 WMF, częściowe konfiguracji w usłudze ściągania serwer/może mieć nazwę jako `<ConfigurationName>.<NodeName>.mof`. Ponadto jeśli maszyna jest ściąganie pojedynczą konfiguracją z ściąganie usługa następnie pliku konfiguracji w repozytorium konfiguracji serwera ściągania może mieć dowolną nazwę pliku. Taka elastyczność nazewnictwa pozwala na zarządzanie węzły częściowo przez usługi Automatyzacja Azure, gdzie konfiguracyjnych dla węzeł pochodzi z usługi Konfiguracja DSC automatyzacji Azure i z częściowa konfiguracji, którą zarządzasz lokalnie.

Metakonfigurację poniżej konfiguruje węzeł, aby być zarządzane zarówno lokalnie, a także przez usługi Automatyzacja Azure usługi.

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

# <a name="using-psdscrunascredential-with-dsc-composite-resources"></a>Przy użyciu PsDscRunAsCredential z zasobami złożonego DSC   

Dodano obsługę protokołu [ *PsDscRunAsCredential* ](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) usłudze Konfiguracja DSC [złożonego](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite) zasobów.    

Teraz można określić wartość dla PsDscRunAsCredential, korzystając z zasobów złożonego w konfiguracji. W przypadku uruchamiania wszystkich zasobów wewnątrz złożonego zasobów użytkownika Uruchom jako. Złożone zasobów wywołuje inny zasób złożonego, wszystkie jej zasoby są również wykonywane jako użytkownika Uruchom jako. Poświadczenia programu RunAs są propagowane do dowolnego poziomu hierarchii złożonego zasobów. Jeśli dowolnego zasobu wewnątrz złożonego zasobu określa własnej wartości PsDscRunAsCredential, błąd scalania wyniki podczas kompilacji konfiguracji.

W tym przykładzie pokazano sposób użycia z [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources) złożonego zasobu zawarte w PSDesiredStateConfiguration module. 



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

##<a name="dsc-module-and-configuration-signing-validations"></a>Moduł DSC i podpisywania operacji sprawdzania poprawności konfiguracji
W konfiguracji DSC konfiguracji i moduły są dystrybuowane do zarządzanych komputerów z serwera ściągania. W przypadku naruszenia zabezpieczeń serwera ściągania osoba atakująca może potencjalnie zmodyfikować konfiguracje i modułów na serwerze ściągania a go rozłożone na wszystkie węzły zarządzane, naruszania ich wszystkich. 

 W wersji 5.1 WMF, obsługuje weryfikowania podpisów cyfrowych w katalogu i konfiguracji DSC (. Pliki MOF). Ta funkcja zapobiega wykonywania konfiguracji lub moduł pliki, które nie są podpisane przez zaufane osoby podpisującej lub które zostały zmodyfikowane po zostały podpisane przez zaufane osoby podpisującej węzłów. 



###<a name="how-to-sign-configuration-and-module"></a>Jak zarejestrować konfiguracji i modułu 
***
* Pliki konfiguracji (. Za): istniejącego polecenia cmdlet programu PowerShell [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) jest rozszerzony do obsługi podpisywania plików MOF.  
* Moduły: Podpisywanie modułów można to zrobić po zarejestrowaniu odpowiedniego katalogu modułu, wykonując poniższe kroki: 
    1. Utworzenie pliku wykazu: plik katalogu zawiera kolekcję skróty kryptograficzne lub odciski palców. 
       Każdy odcisk palca odnosi się do pliku, który znajduje się w module. 
       Nowe polecenia cmdlet [FileCatalog nowy](https://technet.microsoft.com/library/cc732148.aspx), dodano umożliwiające użytkownikom tworzenie plik katalogu dla ich modułu.
    2. Podpisać plik wykazu: Użyj [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) do podpisywania pliku wykazu.
    3. Umieść plik wykazu znajdujące się w folderze modułu.
Według Konwencji modułu katalogu plik należy umieścić w folderze modułu o nazwie identycznej z nazwą modułu.

###<a name="localconfigurationmanager-settings-to-enable-signing-validations"></a>LocalConfigurationManager ustawienia, aby włączyć sprawdzanie poprawności podpisywania

####<a name="pull"></a>Ściągania
LocalConfigurationManager węzła sprawdza poprawność podpisywania modułów i konfiguracji w oparciu o bieżące ustawienia. Domyślnie jest wyłączona Walidacja podpisu. Walidacja podpisu można włączyć przez dodanie bloku "SignatureValidation" do definicji meta konfiguracji węzła jak pokazano poniżej:

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
        # By default, LCM uses the default Windows trusted publisher store to validate the certificate chain. If TrustedStorePath property is specified, LCM uses this custom store for retrieving the trusted publishers to validate the content.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'            
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.       
    }
 
}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose 
 ```

Ustawienie metakonfigurację powyżej w węźle umożliwia weryfikację podpisu na konfiguracje pobrane i modułów. Lokalny program Configuration Manager wykonuje następujące czynności w celu zweryfikowania podpisów cyfrowych.

1. Weryfikacja podpisu w pliku konfiguracji (. MOF) jest nieprawidłowa. 
   Używa polecenia cmdlet programu PowerShell [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), który został rozszerzony w wersji 5.1 do obsługi sprawdzania poprawności podpisu MOF.
2. Sprawdź, czy urząd certyfikacji, który autoryzowane osoby podpisującej jest zaufany.
3. Pobierz moduł zasobów zależności konfiguracji do tymczasowej lokalizacji.
4. Weryfikacja podpisu katalogu uwzględniony w module.
    * Znajdź `<moduleName>.cat` i sprawdzić jego podpisu za pomocą polecenia cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).
    * Sprawdź, czy urząd certyfikacji, który uwierzytelnieni osoby podpisującej jest zaufany.
    * Sprawdź nie został naruszony zawartość modułów za pomocą polecenia cmdlet nowe [FileCatalog testu](https://technet.microsoft.com/library/cc732148.aspx).
5. Install-moduł $env: ProgramFiles\WindowsPowerShell\Modules\
6. Konfiguracja procesu

> Uwaga: Walidacja podpisu na katalog modułu oraz konfiguracji jest realizowane wyłącznie podczas stosowania konfiguracji systemu, po raz pierwszy lub gdy moduł jest pobierane i instalowane. Uruchamia spójności nie weryfikują podpisu Current.mof lub jego zależności modułu.
Jeśli weryfikacja nie powiodła się na każdym etapie, na przykład, jeśli konfiguracji są pobierane z z serwerem ściągania nie jest podpisany, następnie kończy przetwarzanie konfiguracji z powodu błędu, pokazano poniżej i wszystkie pliki tymczasowe są usuwane.

![Przykładowa konfiguracja danych wyjściowych błędu](../images/PullUnsignedConfigFail.png)

Podobnie ściąganie modułu, którego katalogu nie jest podpisany powoduje następujący błąd:

![Moduł wyjściowej błąd próbki](../images/PullUnisgnedCatalog.png)

####<a name="push"></a>Push
Konfiguracji wydana za pomocą wypychania może niepowołane w jego źródle przed on dostarczony do tego węzła. Lokalny program Configuration Manager wykonuje podobne kroki weryfikacji podpisu dla konfiguracje wciśnięcia lub opublikowany.
Poniżej znajduje się pełny przykład Walidacja podpisu do wypychania.

* Włącz weryfikację podpisu na węźle.

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
* Utwórz przykładowy plik konfiguracji.

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

* Spróbuj wypychanie pliku konfiguracji bez znaku do węzła. 

```powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
``` 
![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

* Zaloguj się przy użyciu certyfikatu podpisywania kodu pliku konfiguracji.

![SignMofFile](../images/SignMofFile.png)

* Spróbuj wypychanie podpisany plik MOF.

![SignMofFile](../images/PushSignedMof.png)

