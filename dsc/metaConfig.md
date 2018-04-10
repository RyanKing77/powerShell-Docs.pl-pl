---
ms.date: 10/11/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Konfigurowanie lokalny program Configuration Manager
ms.openlocfilehash: d5a2584b23abd8eb0f1359bc452d16c7380dbaac
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="configuring-the-local-configuration-manager"></a>Konfigurowanie lokalny program Configuration Manager

> Dotyczy: Środowiska Windows PowerShell 5.0

Menedżer konfiguracji lokalnego (LCM) to aparat z konfiguracji żądanego stanu (DSC).
LCM działa na każdy węzeł docelowy i jest odpowiedzialny za analizowanie i wprowadzania konfiguracje, które są wysyłane do węzła.
Również jest odpowiedzialny za wiele innych aspektów DSC, m.in.

- Określanie trybu odświeżania (wypychania lub ściągania).
- Określanie, jak często węzła ściąga i enacts konfiguracji.
- Kojarzenie węzeł z usługą ściągania.
- Określenie konfiguracji częściowej.

Specjalny typ konfiguracji umożliwia konfigurowanie LCM do określ każdy z tych zachowań.
W poniższych sekcjach opisano sposób konfigurowania LCM.

Windows PowerShell 5.0 wprowadzono nowe ustawienia zarządzania lokalny program Configuration Manager.
Aby uzyskać informacje o konfigurowaniu LCM w programie Windows PowerShell 4.0, zobacz [Konfigurowanie lokalny program Configuration Manager w poprzedniej wersji systemu Windows PowerShell](metaconfig4.md).

## <a name="writing-and-enacting-an-lcm-configuration"></a>Zapisywanie i wprowadzania konfiguracji LCM

Aby skonfigurować LCM, Utwórz i uruchom specjalny typ konfiguracji, które stosuje ustawienia LCM.
Aby określić konfigurację LCM, należy użyć atrybutu DscLocalConfigurationManager.
Poniżej przedstawiono prostą konfigurację, która ustawia LCM w trybie wypychania.

```powershell
[DSCLocalConfigurationManager()]
configuration LCMConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
        }
    }
}
```

Zastosowanie ustawień do LCM proces jest podobny do stosowania konfiguracji DSC.
Zostanie utworzenie konfiguracji LCM, go skompilować pliku MOF i zastosować je do węzła.
W przeciwieństwie do konfiguracji DSC nie wprowadza konfiguracji LCM wywołując [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) polecenia cmdlet.
Zamiast tego należy wywołać [DscLocalConfigurationManager zestaw](https://technet.microsoft.com/en-us/library/dn521621.aspx), podając ścieżkę do konfiguracji LCM MOF jako parametr.
Po wprowadza konfiguracji LCM, wywołując można wyświetlić właściwości LCM [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) polecenia cmdlet.

Konfiguracja LCM może zawierać bloków tylko dla określonych zasobów.
W poprzednim przykładzie, tylko zasób o nazwie jest **ustawienia**.
Są dostępne zasoby:

* **ConfigurationRepositoryWeb**: Określa usługa HTTP ściągania dla konfiguracji.
* **ConfigurationRepositoryShare**: Określa udziału SMB do konfiguracji.
* **ResourceRepositoryWeb**: Określa usługa HTTP ściągania dla modułów.
* **ResourceRepositoryShare**: Określa udziału SMB dla modułów.
* **ReportServerWeb**: Określa usługę ściągania HTTP, do którego będą wysyłane raporty.
* **PartialConfiguration**: udostępnia dane umożliwiające konfiguracje częściowej.

## <a name="basic-settings"></a>Ustawienia podstawowe

Inne niż Określanie punktów końcowych usługi ściągania i ścieżki i częściowe konfiguracje, wszystkie właściwości LCM są konfigurowane w **ustawienia** bloku.
Następujące właściwości są dostępne w **ustawienia** bloku.

|  Właściwość  |  Typ  |  Opis   |
|----------- |------- |--------------- |
| ActionAfterReboot| ciąg| Określa, co się stanie po ponownym uruchomieniu podczas stosowania konfiguracji. Możliwe wartości to __"ContinueConfiguration"__ i __"StopConfiguration"__. <ul><li> __ContinueConfiguration__: kontynuować stosowanie bieżącej konfiguracji po ponownym uruchomieniu komputera. Jest to wartość domyślna</li><li>__StopConfiguration__: Zatrzymaj bieżącą konfigurację po ponownym uruchomieniu komputera.</li></ul>|
| AllowModuleOverwrite| bool| __$TRUE__ czy nowe konfiguracje pobrane z usługi replikacji ściąganej mogą nadpisać stare w docelowym węźle. W przeciwnym razie $FALSE.|
| CertificateID| ciąg| Odcisk palca certyfikatu używany do zabezpieczania poświadczeń przekazanych w konfiguracji. Aby uzyskać więcej informacji, zobacz [chcesz zabezpieczyć poświadczenia w konfiguracji żądanego stanu programu Windows PowerShell](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx)?. <br> __Uwaga:__ to odbywa się automatycznie, jeśli przy użyciu usługi ściągania usługi Konfiguracja DSC automatyzacji Azure.|
| ConfigurationDownloadManagers| CimInstance[]| Nieaktualne. Użyj __ConfigurationRepositoryWeb__ i __ConfigurationRepositoryShare__ punkty końcowe usługi bloków, aby zdefiniować ściągania konfiguracji.|
| ConfigurationID| ciąg| Zapewnienia zgodności z ściągania starszej usługi wersji. Identyfikator GUID, który identyfikuje plik konfiguracji można pobrać z usługi ściągania. Węzeł będzie pobierać konfiguracji w usłudze replikacji ściąganej, jeśli nazwa konfiguracji MOF nosi nazwę ConfigurationID.mof.<br> __Uwaga:__ Jeśli ustawisz tę właściwość, rejestrowanie węzeł usłudze ściągania przy użyciu __RegistrationKey__ nie działa. Aby uzyskać więcej informacji, zobacz [Konfigurowanie klienta ściągnięcia z nazwy konfiguracji](pullClientConfigNames.md).|
| ConfigurationMode| ciąg | Określa, jak LCM faktycznie ma zastosowanie do konfiguracji w węzłach docelowych. Możliwe wartości to __"ApplyOnly"__,__"ApplyAndMonitor"__, i __"ApplyAndAutoCorrect"__. <ul><li>__ApplyOnly__: DSC ma zastosowanie do konfiguracji i nie działają dalsze, chyba że nowa konfiguracja zostanie przypisany do węzła docelowego lub nowej konfiguracji są pobierane z usługi. Po początkowej stosowania nowej konfiguracji DSC nie sprawdza odejście od stanu wcześniej skonfigurowany. Należy pamiętać, że DSC spróbuje zastosować konfigurację, dopóki nie zostanie pomyślnie przed __ApplyOnly__ obowiązuje. </li><li> __ApplyAndMonitor__: jest to wartość domyślna. LCM stosuje wszelkie nowe konfiguracje. Po początkowej stosowania nowej konfiguracji Jeśli węzeł docelowy drifts z żądanego stanu usługi Konfiguracja DSC raporty niezgodności w dziennikach. Należy pamiętać, że DSC spróbuje zastosować konfigurację, dopóki nie zostanie pomyślnie przed __ApplyAndMonitor__ obowiązuje.</li><li>__ApplyAndAutoCorrect__: DSC stosuje wszelkie nowe konfiguracje. Po początkowej stosowania nowej konfiguracji Jeśli węzeł docelowy drifts z żądanego stanu usługi Konfiguracja DSC raporty niezgodności w dziennikach, a następnie ponownie stosuje bieżącej konfiguracji.</li></ul>|
| ConfigurationModeFrequencyMins| UInt32| (W minutach) bieżącej konfiguracji jest jak często sprawdzone i zastosowane. Ta właściwość jest ignorowana, jeśli właściwość ConfigurationMode jest ustawiona na ApplyOnly. Wartość domyślna to 15.|
| DebugMode| ciąg| Możliwe wartości to __Brak__, __ForceModuleImport__, i __wszystkich__. <ul><li>Ustaw __Brak__ zasoby pamięci podręcznej. To jest domyślna i powinny być używane w scenariuszach produkcji.</li><li>Ustawienie __ForceModuleImport__, powoduje, że LCM ponowne załadowanie wszelkich modułów zasobów DSC, nawet jeśli zostały wcześniej załadowane i pamięci podręcznej. Wpływa na wydajność DSC operacji, ponieważ każdy moduł zostanie ponownie załadowana z użyciem. Zwykle użyje tę wartość podczas debugowania zasobu</li><li>W tej wersji __wszystkie__ jest taka sama jak __ForceModuleImport__</li></ul> |
| RebootNodeIfNeeded| bool| Ustaw tę wartość na __$true__ do automatyczny ponowny rozruch węzła po konfiguracji, która wymaga ponownego rozruchu jest stosowany. W przeciwnym razie trzeba będzie ręcznie ponownie uruchomić węzeł dla żadnej konfiguracji, która go wymaga. Wartość domyślna to __$false__. Aby użyć tego ustawienia, gdy warunek ponowne uruchomienie jest wdrożonych przez inną niż DSC (takich jak Instalator systemu Windows), należy połączyć tego ustawienia z [xPendingReboot](https://github.com/powershell/xpendingreboot) modułu.|
| RefreshMode| ciąg| Określa, jak LCM pobiera konfiguracje. Możliwe wartości to __"Wyłączone"__, __"Push"__, i __"Pull"__. <ul><li>__Wyłączone__: konfiguracji DSC są wyłączone dla tego węzła.</li><li> __Wypychanie__: konfiguracje są inicjowane przez wywołanie metody [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) polecenia cmdlet. Konfiguracja jest stosowany od razu do węzła. Jest to wartość domyślna.</li><li>__Ściągające:__ węzeł jest skonfigurowany do regularne sprawdzanie konfiguracji usługi ściągania lub ścieżka SMB. Jeśli ta właściwość jest ustawiona na __ściągnięcia__, należy określić HTTP (usługa) lub ścieżkę protokołu SMB (udział) w __ConfigurationRepositoryWeb__ lub __ConfigurationRepositoryShare__ bloku.</li></ul>|
| RefreshFrequencyMins| Uint32| Przedział czasu, w minutach, po których LCM sprawdza usługą ściągnięcia w celu pobrania zaktualizowanej konfiguracji. Ta wartość jest ignorowana, jeśli nie skonfigurowano LCM w trybie ściągania. Wartość domyślna to 30.|
| ReportManagers| CimInstance[]| Nieaktualne. Użyj __ReportServerWeb__ bloków, aby zdefiniować punkt końcowy do wysyłania danych raportowania usługi ściągania.|
| ResourceModuleManagers| CimInstance[]| Nieaktualne. Użyj __ResourceRepositoryWeb__ i __ResourceRepositoryShare__ bloków, aby zdefiniować ściągania usługi odpowiednio punktów końcowych HTTP lub ścieżki SMB.|
| PartialConfigurations| CimInstance| Nie jest zaimplementowana. Nie używaj.|
| StatusRetentionTimeInDays | UInt32| Liczba dni, przez które LCM śledzi stan bieżącej konfiguracji.|

## <a name="pull-service"></a>Usługa replikacji ściąganej

Konfiguracja LCM obsługuje definiowanie następujące ściągające punkty końcowe usługi:

- **Serwer konfiguracji**: repozytorium konfiguracji DSC. Definiowanie konfiguracji serwerów przy użyciu **ConfigurationRepositoryWeb** (dla serwerów opartych na sieci web) i **ConfigurationRepositoryShare** (w przypadku serwerów na bazie protokołu SMB) bloków.
- **Serwer zasobów**: repozytorium dla zasobów usługi Konfiguracja DSC, dostarczana w moduły programu PowerShell. Zdefiniuj serwery zasobów za pomocą **ResourceRepositoryWeb** (dla serwerów opartych na sieci web) i **ResourceRepositoryShare** (w przypadku serwerów na bazie protokołu SMB) bloków.
- **Serwer raportów**: usługa, która DSC wysyła dane raportu do. Zdefiniuj serwerów raportów za pomocą **ReportServerWeb** bloków. Serwer raportów należy usługi sieci web.

Więcej informacji na temat usługi ściągania można znaleźć, [żądanego stanu konfiguracji ściągania usługi](pullServer.md).

## <a name="configuration-server-blocks"></a>Bloki serwera konfiguracji

Aby zdefiniować serwera konfiguracji opartej na sieci web, należy utworzyć **ConfigurationRepositoryWeb** bloku.
A **ConfigurationRepositoryWeb** definiuje następujące właściwości.

|Właściwość|Typ|Opis|
|---|---|---|
|AllowUnsecureConnection|bool|Ustaw **$TRUE** umożliwia nawiązywanie połączeń z węzła do serwera bez uwierzytelniania. Ustaw **$FALSE** wymagające uwierzytelniania.|
|CertificateID|ciąg|Odcisk palca certyfikatu używany do uwierzytelniania na serwerze.|
|ConfigurationNames|String[]|Tablicę nazw konfiguracji, które można ściągnąć przez węzeł docelowy. Są one używane tylko wtedy, gdy węzeł jest zarejestrowany w usłudze replikacji ściąganej przy użyciu **RegistrationKey**. Aby uzyskać więcej informacji, zobacz [Konfigurowanie klienta ściągnięcia z nazwy konfiguracji](pullClientConfigNames.md).|
|RegistrationKey|ciąg|Identyfikator GUID, który rejestruje węzeł z usługą ściągania. Aby uzyskać więcej informacji, zobacz [Konfigurowanie klienta ściągnięcia z nazwy konfiguracji](pullClientConfigNames.md).|
|ServerURL|ciąg|Adres URL usługi konfiguracji.|

Zobacz przykład skryptu do uproszczenia Konfigurowanie wartość ConfigurationRepositoryWeb do węzłów lokalnie jest niedostępna - [metaconfigurations generowania DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Aby zdefiniować serwera konfiguracji na bazie protokołu SMB, należy utworzyć **ConfigurationRepositoryShare** bloku.
A **ConfigurationRepositoryShare** definiuje następujące właściwości.

|Właściwość|Typ|Opis|
|---|---|---|
|Poświadczenie|MSFT_Credential|Poświadczenia używane do uwierzytelniania w udziale SMB.|
|SourcePath|ciąg|Ścieżka udziału SMB.|

## <a name="resource-server-blocks"></a>Bloki serwer zasobów

Aby określić serwer zasobów opartych na sieci web, należy utworzyć **ResourceRepositoryWeb** bloku.
A **ResourceRepositoryWeb** definiuje następujące właściwości.

|Właściwość|Typ|Opis|
|---|---|---|
|AllowUnsecureConnection|bool|Ustaw **$TRUE** umożliwia nawiązywanie połączeń z węzła do serwera bez uwierzytelniania. Ustaw **$FALSE** wymagające uwierzytelniania.|
|CertificateID|ciąg|Odcisk palca certyfikatu używany do uwierzytelniania na serwerze.|
|RegistrationKey|ciąg|Identyfikator GUID, który identyfikuje węzeł z usługą ściągania.|
|ServerURL|ciąg|Adres URL serwera konfiguracji.|

Zobacz przykład skryptu do uproszczenia Konfigurowanie wartość ResourceRepositoryWeb do węzłów lokalnie jest niedostępna - [metaconfigurations generowania DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Aby określić serwer zasobów na bazie protokołu SMB, należy utworzyć **ResourceRepositoryShare** bloku.
**ResourceRepositoryShare** definiuje następujące właściwości.

|Właściwość|Typ|Opis|
|---|---|---|
|Poświadczenie|MSFT_Credential|Poświadczenia używane do uwierzytelniania w udziale SMB. Na przykład poświadczenia przekazywanie zobacz [ustawienie serwera ściągania usługi Konfiguracja DSC SMB](pullServerSMB.md)|
|SourcePath|ciąg|Ścieżka udziału SMB.|

## <a name="report-server-blocks"></a>Bloki serwera raportów

Aby zdefiniować serwera raportów, należy utworzyć **ReportServerWeb** bloku.
Rola serwera raportów nie jest zgodny z protokołu SMB, na podstawie ściągania usługi.
**ReportServerWeb** definiuje następujące właściwości.

|Właściwość|Typ|Opis|
|---|---|---|
|AllowUnsecureConnection|bool|Ustaw **$TRUE** umożliwia nawiązywanie połączeń z węzła do serwera bez uwierzytelniania. Ustaw **$FALSE** wymagające uwierzytelniania.|
|CertificateID|ciąg|Odcisk palca certyfikatu używany do uwierzytelniania na serwerze.|
|RegistrationKey|ciąg|Identyfikator GUID, który identyfikuje węzeł z usługą ściągania.|
|ServerURL|ciąg|Adres URL serwera konfiguracji.|

Zobacz przykład skryptu do uproszczenia Konfigurowanie wartość ReportServerWeb do węzłów lokalnie jest niedostępna - [metaconfigurations generowania DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

## <a name="partial-configurations"></a>Konfiguracje z częściowa

Aby zdefiniować częściowe konfiguracji, należy utworzyć **PartialConfiguration** bloku.
Aby uzyskać więcej informacji o konfiguracjach częściowe, zobacz [konfiguracji DSC częściowego](partialConfigs.md).
**PartialConfiguration** definiuje następujące właściwości.

|Właściwość|Typ|Opis|
|---|---|---|
|ConfigurationSource|ciąg]|Tablicę nazw konfiguracji serwerów, wcześniej zdefiniowanej w **ConfigurationRepositoryWeb** i **ConfigurationRepositoryShare** bloków, gdzie pobieranych z częściowa konfiguracji.|
|dependsOn|{} ciągu|Lista nazw inne konfiguracje, które należy wykonać przed zastosowaniem tej konfiguracji częściowej.|
|Opis|ciąg|Tekst opisujący częściowe konfiguracji.|
|ExclusiveResources|ciąg]|Tablica zasobów dotyczących wyłącznie tej konfiguracji częściowej.|
|RefreshMode|ciąg|Określa, jak LCM pobiera tej konfiguracji częściowej. Możliwe wartości to __"Wyłączone"__, __"Push"__, i __"Pull"__. <ul><li>__Wyłączone__: Ta konfiguracja częściowe jest wyłączona.</li><li> __Wypychanie__: częściowe konfiguracji zostanie przypisany do węzła wywołując [DscConfiguration publikowania](https://technet.microsoft.com/en-us/library/mt517875.aspx) polecenia cmdlet. Po wszystkich konfiguracji z częściowa dla węzła są wypychana lub pobierane z usługi, konfiguracji mogą być uruchamiane przez wywołanie `Start-DscConfiguration –UseExisting`. Jest to wartość domyślna.</li><li>__Ściągające:__ węzeł jest skonfigurowany do regularne sprawdzanie częściowe konfiguracji od usługi ściągania. Jeśli ta właściwość jest ustawiona na __ściągania__, należy określić w usługach ściągania __ConfigurationSource__ właściwości. Aby uzyskać więcej informacji o usłudze ściągania usługi Automatyzacja Azure, zobacz [Przegląd usługi Konfiguracja DSC automatyzacji Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview).</li></ul>|
|ResourceModuleSource|ciąg]|Tablica nazw zasobów serwerów do pobrania wymaganych zasobów dla tej konfiguracji częściowej. Te nazwy musi odwoływać się do wcześniej zdefiniowanej w punktów końcowych usługi **ResourceRepositoryWeb** i **ResourceRepositoryShare** bloków.|

__Uwaga:__ konfiguracje częściowe są obsługiwane w usłudze Konfiguracja DSC automatyzacji Azure, ale tylko jedną konfigurację mogą być pobierane z każde konto usługi Automatyzacja na węzeł.

## <a name="see-also"></a>Zobacz też

### <a name="concepts"></a>Pojęcia
[Żądany przegląd stanu konfiguracji](overview.md)

[Wprowadzenie do korzystania z usługi Konfiguracja DSC automatyzacji Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started)

### <a name="other-resources"></a>Inne zasoby

[Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx)

[Konfigurowanie klienta ściągnięcia z nazwy konfiguracji](pullClientConfigNames.md)