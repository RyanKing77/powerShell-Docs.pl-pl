# [Omówienie](overview.md)

## [Omówienie platformy Desired State Configuration dla osób podejmujących decyzje](decisionMaker.md)

## [Omówienie platformy Desired State Configuration dla inżynierów](DscForEngineers.md)

## [DSC — szybki start](quickStart.md)

# [Konfiguracje](configurations.md)

## [Realizacja konfiguracji](enactingConfigurations.md)

## [Oddzielanie danych konfiguracji i środowiska](separatingEnvData.md)

## [Korzystanie z zasobów z wieloma wersjami](sxsResource.md)

## [Uruchamianie platformy DSC przy użyciu poświadczeń użytkownika](runAsUser.md)

## [Określanie zależności między węzłami](crossNodeDependencies.md)

## [Dane konfiguracji](configData.md)

### [Opcje poświadczeń w danych konfiguracji](configDataCredentials.md)

## [Zagnieżdżanie konfiguracji](compositeConfigs.md)

## [Zabezpieczanie pliku MOF konfiguracji](secureMOF.md)

## [Konfiguracje częściowe](partialConfigs.md)

## [Pisanie tematów pomocy dotyczących konfiguracji DSC](configHelp.md)

## [Konfigurowanie maszyny wirtualnej podczas początkowego rozruchu przy użyciu platformy DSC](bootstrapDsc.md)

### [Klucz rejestru DSCAutomationHostEnabled](DSCAutomationHostEnabled.md)

# [Zasoby](resources.md)

## [Zasoby wbudowane](builtInResource.md)

### [Zasób archiwum](archiveResource.md)

### [Zasób środowiska](environmentResource.md)

### [Zasób pliku](fileResource.md)

### [Zasób grupy](groupResource.md)

### [Zasób GroupSet](groupSetResource.md)

### [Zasób dziennika](logResource.md)

### [Zasób pakietu](packageResource.md)

### [Zasób ProcessSet](processSetResource.md)

### [Zasób rejestru](registryResource.md)

### [Zasób skryptu](scriptResource.md)

### [Zasób usługi](serviceResource.md)

### [Zasób ServiceSet](serviceSetResource.md)

### [Zasób użytkownika](userResource.md)

### [WaitForAllResource](waitForAllResource.md)

### [WaitForAnyResource](waitForAnyResource.md)

### [WaitForSomeResource](waitForSomeResource.md)

### [Zasób WindowsFeature](windowsfeatureResource.md)

### [Zasób WindowsFeatureSet](windowsFeatureSetResource.md)

### [Zasób WindowsOptionalFeature](windowsOptionalFeatureResource.md)

### [Zasób WindowsOptionalFeatureSet](windowsOptionalFeatureSetResource.md)

### [Zasób WindowsPackageCab](windowsPackageCabResource.md)

### [Zasób WindowsProcess](windowsProcessResource.md)

## [Tworzenie zasobów niestandardowych](authoringResource.md) 

### [Zasoby niestandardowe oparte na pliku MOF](authoringResourceMOF.md)

#### [Zasób oparty na pliku MOF w języku C#](authoringResourceMofCS.md)

### [Zasoby niestandardowe oparte na klasie](authoringResourceClass.md)

### [Zasoby złożone](authoringResourceComposite.md)

### [Pisanie zasobu DSC jednego wystąpienia (najlepsze rozwiązanie)](singleInstance.md)

### [Lista kontrolna tworzenia zasobu](resourceAuthoringChecklist.md)

## [Debugowanie zasobów DSC](debugResource.md)

## [Bezpośrednie wywoływanie metod zasobów DSC](directCallResource.md)

# Local Configuration Manager

## [Konfigurowanie programu Local Configuration Manager (LCM)](metaConfig.md)

## [Konfigurowanie programu LCM w programie PowerShell 4.0](metaConfig4.md)

# Model ściągania platformy DSC

## [Konfigurowanie internetowego serwera ściągania](pullServer.md)

## [Konfigurowanie serwera ściągania SMB platformy DSC](pullServerSMB.md)

## [Konfigurowanie klienta ściągania](pullClient.md)

### [Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji](pullClientConfigNames.md)

### [Konfigurowanie klienta ściągania przy użyciu identyfikatora konfiguracji](pullClientConfigID.md)

## [Używanie serwera raportów platformy DSC](reportServer.md)

## [Najlepsze rozwiązania dotyczące serwera ściągania](secureServer.md)

# [Przykłady konfiguracji DSC](dscExamples.md)

## [Tworzenie potoku CI/CD przy użyciu platformy DSC oraz usług Pester i Visual Studio Team Services](dscCiCd.md)

## [Oddzielanie danych konfiguracji i środowiska](separatingEnvData.md)

# [Rozwiązywanie problemów z platformą DSC](troubleshooting.md)

# [Korzystanie z platformy DSC na serwerze Nano Server](nanoDsc.md)

# Platforma DSC w systemie Linux

## [Wprowadzenie do platformy DSC dla systemu Linux](lnxGettingStarted.md)

## [Wbudowane zasoby dla systemu Linux](lnxBuiltInResources.md)

### [Zasób nxArchive](lnxArchiveResource.md)

### [Zasób nxEnvironment](lnxEnvironmentResource.md)

### [Zasób nxFile](lnxFileResource.md)

### [Zasób nxFileLine](lnxFileLineResource.md)

### [Zasób nxGroup](lnxGroupResource.md)

### [Zasób nxPackage](lnxPackageResource.md)

### [Zasób nxService](lnxServiceResource.md)

### [Zasób nxSshAuthorizedKeys](lnxSshAuthorizedKeysResource.md)

### [Zasób nxUser](lnxUserResource.md)

# [Korzystanie z platformy DSC na platformie Microsoft Azure](azureDsc.md)

# Dokumentacja dotycząca plików MOF platformy DSC

## [Klasa MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager.md)

### [Metoda ApplyConfiguration klasy MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-applyconfiguration.md)

### [Metoda DisableDebugConfiguration klasy MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)

### [Metoda EnableDebugConfiguration klasy MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)

### [Metoda GetConfiguration klasy MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-getconfiguration.md)

### [Metoda GetConfigurationResultOutput klasy MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)

### [Metoda GetConfigurationStatus klasy MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)

### [Metoda GetMetaConfiguration klasy MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)

### [Metoda PerformRequiredConfigurationChecks klasy MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)

### [Metoda RemoveConfiguration klasy MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-removeconfiguration.md)

### [Metoda ResourceGet klasy MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-resourceget.md)

### [Metoda ResourceSet klasy MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-resourceset.md)

### [Metoda ResourceTest klasy MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-resourcetest.md)

### [Metoda RollBack klasy MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-rollback.md)

### [Metoda SendConfiguration klasy MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-sendconfiguration.md)

### [Metoda SendConfigurationApply klasy MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)

### [Metoda SendConfigurationApplyAsync klasy MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)

### [Metoda SendMetaConfigurationApply klasy MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)

### [Metoda StopConfiguration klasy MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-stopconfiguration.md)

### [Metoda TestConfiguration klasy MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-testconfiguration.md)

# Dalsze zasoby

## [Oficjalne dokumenty](whitepapers.md)
