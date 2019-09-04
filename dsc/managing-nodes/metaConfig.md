---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguracja, instalacja
title: Konfigurowanie Configuration Manager lokalnego
ms.openlocfilehash: 42544036d87fcea3189fd6d2e55579fe87f137e1
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215392"
---
# <a name="configuring-the-local-configuration-manager"></a>Konfigurowanie Configuration Manager lokalnego

> Dotyczy: Środowisko Windows PowerShell 5,0

Local Configuration Manager (LCM) to aparat konfiguracji żądanego stanu (DSC).
LCM działa na każdym węźle docelowym i jest odpowiedzialny za analizowanie i Konfigurowanie konfiguracji, które są wysyłane do węzła.
Jest on również odpowiedzialny za wiele innych aspektów DSC, w tym następujących.

- Określanie trybu odświeżania (wypychania lub ściągania).
- Określanie, jak często węzeł pobiera i ustala konfiguracje.
- Kojarzenie węzła z usługą ściągania.
- Określanie konfiguracji częściowych.

Należy użyć specjalnego typu konfiguracji, aby skonfigurować LCM do określenia każdego z tych zachowań.
W poniższych sekcjach opisano sposób konfigurowania LCM.

W programie Windows PowerShell 5,0 wprowadzono nowe ustawienia dotyczące zarządzania Configuration Manager lokalnego.
Aby uzyskać informacje na temat konfigurowania LCM w programie Windows PowerShell 4,0, zobacz [Konfigurowanie lokalnego Configuration Manager w poprzednich wersjach programu Windows PowerShell](metaconfig4.md).

## <a name="writing-and-enacting-an-lcm-configuration"></a>Pisanie i przetworzenie konfiguracji LCM

Aby skonfigurować LCM, należy utworzyć i uruchomić specjalny typ konfiguracji, która stosuje ustawienia LCM.
Aby określić konfigurację LCM, należy użyć atrybutu DscLocalConfigurationManager.
Poniżej przedstawiono prostą konfigurację, która ustawia tryb LCM na wypychanie.

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

Proces stosowania ustawień do LCM jest podobny do zastosowania konfiguracji DSC.
Należy utworzyć konfigurację LCM, skompilować ją do pliku MOF i zastosować ją do węzła.
W przeciwieństwie do konfiguracji DSC, konfiguracja LCM nie jest przeprowadzana przez wywołanie polecenia cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .
Zamiast tego należy wywołać polecenie [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager), podając ścieżkę do pliku MOF konfiguracji LCM jako parametr.
Po wprowadzeniu konfiguracji LCM można zobaczyć właściwości LCM, wywołując polecenie cmdlet [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) .

Konfiguracja LCM może zawierać bloki tylko dla ograniczonego zestawu zasobów.
W poprzednim przykładzie jedynym przyznanego zasobu jest **Ustawienia**.
Dostępne są następujące zasoby:

* **ConfigurationRepositoryWeb**: Określa usługę ściągania http dla konfiguracji.
* **ConfigurationRepositoryShare**: określa udział SMB dla konfiguracji.
* **ResourceRepositoryWeb**: Określa usługę ściągania http dla modułów.
* **ResourceRepositoryShare**: określa udział SMB dla modułów.
* **ReportServerWeb**: Określa usługę ŚCIĄGAnia http, do której będą wysyłane raporty.
* **PartialConfiguration**: udostępnia dane umożliwiające włączenie częściowych konfiguracji.

## <a name="basic-settings"></a>Ustawienia podstawowe

Oprócz określania punktów końcowych/ścieżek usługi ściągania i częściowych konfiguracji wszystkie właściwości LCM są konfigurowane w bloku **ustawień** .
W bloku **ustawień** dostępne są następujące właściwości.

|  Właściwość  |  Type  |  Opis   |
|----------- |------- |--------------- |
| ActionAfterReboot| ciąg| Określa, co się stanie po ponownym uruchomieniu w trakcie stosowania konfiguracji. Możliwe wartości to __"ContinueConfiguration"__ i __"StopConfiguration"__ . <ul><li> __ContinueConfiguration__: Kontynuuj stosowanie bieżącej konfiguracji po ponownym uruchomieniu komputera. Jest to wartość domyślna</li><li>__StopConfiguration__: Zatrzymaj bieżącą konfigurację po ponownym uruchomieniu komputera.</li></ul>|
| AllowModuleOverwrite| logiczna| __$True__ , czy nowe konfiguracje pobrane z usługi ściągania mogą nadpisać stare w węźle docelowym. W przeciwnym razie $FALSE.|
| CertificateID| ciąg| Odcisk palca certyfikatu użytego do zabezpieczenia poświadczeń przekazaną w konfiguracji. Aby uzyskać więcej informacji [, zobacz czy chcesz zabezpieczyć poświadczenia w konfiguracji żądanego stanu programu Windows PowerShell](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx)?. <br> __Uwaga:__ jest to zarządzane automatycznie w przypadku korzystania z usługi ściągania Azure Automation DSC.|
| ConfigurationDownloadManagers| CimInstance[]| Nieaktualne. Użyj bloków __ConfigurationRepositoryWeb__ i __ConfigurationRepositoryShare__ , aby zdefiniować punkty końcowe usługi ściągania konfiguracji.|
| ConfigurationID| ciąg| W celu zapewnienia zgodności z poprzednimi wersjami przy użyciu starszych wersji usługi ściągania. Identyfikator GUID, który identyfikuje plik konfiguracji, który ma zostać pobrany z usługi ściągania. Węzeł będzie ściągał konfiguracje w usłudze ściągania, jeśli nazwa pliku MOF konfiguracji nosi nazwę ConfigurationID. mof.<br> __Uwaga:__ Jeśli ustawisz tę właściwość, zarejestrowanie węzła w usłudze ściągania przy użyciu usługi __RegistrationKey__ nie działa. Aby uzyskać więcej informacji, zobacz [Konfigurowanie klienta ściągania z nazwami konfiguracji](../pull-server/pullClientConfigNames.md).|
| ConfigurationMode| ciąg | Określa sposób, w jaki LCM stosuje konfigurację do węzłów docelowych. Możliwe wartości to __"ApplyOnly"__ , __"ApplyAndMonitor"__ i __"ApplyAndAutoCorrect"__ . <ul><li>__ApplyOnly__: Konfiguracja DSC stosuje konfigurację i nie wykonuje żadnych dalszych operacji, chyba że nowa konfiguracja jest wypychana do węzła docelowego lub gdy nowa konfiguracja zostanie ściągnięta z usługi. Po początkowej aplikacji nowej konfiguracji DSC nie sprawdza dryfu od wcześniej skonfigurowanego stanu. Należy pamiętać, że Konfiguracja DSC podejmie próbę zastosowania konfiguracji do momentu, aż __ApplyOnly__ zacznie obowiązywać. </li><li> __ApplyAndMonitor__: Jest to wartość domyślna. LCM stosuje wszelkie nowe konfiguracje. Po początkowej aplikacji nowej konfiguracji, jeśli węzeł docelowy zostanie przedryfem z żądanego stanu, DSC zgłosi niezgodność w dziennikach. Należy pamiętać, że Konfiguracja DSC podejmie próbę zastosowania konfiguracji do momentu, aż __ApplyAndMonitor__ zacznie obowiązywać.</li><li>__ApplyAndAutoCorrect__: Konfiguracja DSC stosuje wszelkie nowe konfiguracje. Po początkowym zastosowaniu nowej konfiguracji, jeśli węzeł docelowy dryfuje się z żądanego stanu, DSC zgłosi niezgodność w dziennikach, a następnie ponownie zastosuje bieżącą konfigurację.</li></ul>|
| ConfigurationModeFrequencyMins| UInt32| Jak często w minutach jest sprawdzana i stosowana Bieżąca konfiguracja. Ta właściwość jest ignorowana, jeśli właściwość ConfigurationMode ma wartość ApplyOnly. Wartość domyślna to 15.|
| Debugujmode| ciąg| Możliwe wartości to __none__, __ForceModuleImport__i __All__. <ul><li>Ustaw wartość __Brak__ , aby używać zasobów w pamięci podręcznej. Jest to wartość domyślna i powinna być używana w scenariuszach produkcyjnych.</li><li>Ustawienie na __ForceModuleImport__, powoduje, że LCM ponownie ładuje wszystkie moduły zasobów DSC, nawet jeśli zostały wcześniej załadowane i zbuforowane. Ma to wpływ na wydajność operacji DSC podczas ponownego ładowania każdego modułu przy użyciu. Zazwyczaj ta wartość jest używana podczas debugowania zasobu</li><li>W tej wersji __wszystkie__ są takie same jak __ForceModuleImport__</li></ul> |
| RebootNodeIfNeeded| logiczna| Ustaw tę `$true` opcję na, aby umożliwić zasobom ponowne uruchomienie węzła `$global:DSCMachineStatus` przy użyciu flagi. W przeciwnym razie konieczne będzie ręczne ponowne uruchomienie węzła dla każdej konfiguracji, która go wymaga. Wartość domyślna to `$false`. Aby użyć tego ustawienia, gdy warunek ponownego uruchomienia jest wdrażany przez inną niż DSC (na przykład Instalator Windows), Połącz to ustawienie z modułem [xPendingReboot](https://github.com/powershell/xpendingreboot) .|
| RefreshMode| ciąg| Określa, jak LCM pobiera konfiguracje. Możliwe wartości to __"Disabled"__ , __"push"__ i __"pull"__ . <ul><li>__Wyłączone__: Konfiguracje DSC są wyłączone dla tego węzła.</li><li> __Wypchnij__: Konfiguracje są inicjowane przez wywołanie polecenia cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) . Konfiguracja zostanie natychmiast zastosowana do węzła. Jest to wartość domyślna.</li><li>__Pobierać__ Węzeł jest skonfigurowany do regularnego sprawdzania konfiguracji z usługi ściągania lub ścieżki protokołu SMB. Jeśli ta właściwość jest ustawiona na __ściąganie__, należy określić ścieżkę http (usługa) lub SMB (udział) w bloku __ConfigurationRepositoryWeb__ lub __ConfigurationRepositoryShare__ .</li></ul>|
| RefreshFrequencyMins| Uint32| Przedział czasu (w minutach), w którym LCM sprawdza usługę ściągania w celu uzyskania zaktualizowanych konfiguracji. Ta wartość jest ignorowana, jeśli LCM nie jest skonfigurowany w trybie ściągania. Wartość domyślna to 30.|
| ReportManagers| CimInstance[]| Nieaktualne. Użyj bloków __ReportServerWeb__ , aby zdefiniować punkt końcowy do wysyłania danych raportowania do usługi ściągania.|
| ResourceModuleManagers| CimInstance[]| Nieaktualne. Użyj bloków __ResourceRepositoryWeb__ i __ResourceRepositoryShare__ , aby zdefiniować odpowiednio punkty końcowe http lub ścieżki protokołu SMB usługi ściągania.|
| PartialConfigurations| CimInstance| Nie zaimplementowane. Nie używaj.|
| StatusRetentionTimeInDays | UInt32| Liczba dni, przez jaką LCM zachowuje stan bieżącej konfiguracji.|

> [!NOTE]
> LCM uruchamia cykl **ConfigurationModeFrequencyMins** na podstawie:
>
> - Nowa konfiguracja jest stosowana przy użyciu`Set-DscLocalConfigurationManager`
> - Ponowne uruchomienie komputera
>
> W przypadku każdego warunku, w którym proces czasomierza napotka awarię, który zostanie wykryty w ciągu 30 sekund, a cykl zostanie uruchomiony ponownie.
> Współbieżna operacja może opóźnić uruchomienie cyklu, jeśli czas trwania tej operacji przekracza skonfigurowaną częstotliwość cyklu, kolejny czasomierz nie zostanie uruchomiony.
>
> Przykładowa konfiguracja jest konfigurowana z częstotliwością ściągania 15 minut, a ściąganie występuje w T1.  Węzeł nie kończy pracy przez 16 minut.  Pierwszy 15-minutowy cykl jest ignorowany, a następne ściąganie nastąpi przy T1 + 15 + 15.

## <a name="pull-service"></a>Usługa ściągania

Konfiguracja LCM obsługuje definiowanie następujących typów punktów końcowych usługi ściągania:

- **Serwer konfiguracji**: Repozytorium konfiguracji DSC. Zdefiniuj serwery konfiguracji za pomocą **ConfigurationRepositoryWeb** (dla serwerów sieci Web) i **ConfigurationRepositoryShare** (dla serwerów opartych na protokole SMB).
- **Serwer zasobów**: Repozytorium dla zasobów DSC, spakowane jako moduły programu PowerShell. Definiowanie serwerów zasobów przy użyciu usługi **ResourceRepositoryWeb** (dla serwerów sieci Web) i **ResourceRepositoryShare** (dla serwerów opartych na protokole SMB).
- **Serwer raportów**: Usługa, do której są wysyłane dane raportów DSC. Zdefiniuj serwery raportów przy użyciu bloków **ReportServerWeb** . Serwer raportów musi być usługą sieci Web.

Aby uzyskać więcej informacji na temat usługi ściągania, zobacz [Usługa ściągania konfiguracji żądanego stanu](../pull-server/pullServer.md).

## <a name="configuration-server-blocks"></a>Bloki serwera konfiguracji

Aby zdefiniować serwer konfiguracji oparty na sieci Web, należy utworzyć blok **ConfigurationRepositoryWeb** .
**ConfigurationRepositoryWeb** definiuje następujące właściwości.

|Właściwość|Type|Opis|
|---|---|---|
|AllowUnsecureConnection|logiczna|Ustaw wartość **$true** , aby zezwolić na połączenia z węzła z serwerem bez uwierzytelniania. Ustaw wartość **$false** , aby wymagać uwierzytelniania.|
|CertificateID|ciąg|Odcisk palca certyfikatu używanego do uwierzytelniania na serwerze.|
|ConfigurationNames|Ciąg []|Tablica nazw konfiguracji do ściągnięcia przez węzeł docelowy. Są one używane tylko wtedy, gdy węzeł jest zarejestrowany w usłudze ściągania przy użyciu **RegistrationKey**. Aby uzyskać więcej informacji, zobacz [Konfigurowanie klienta ściągania z nazwami konfiguracji](../pull-server/pullClientConfigNames.md).|
|RegistrationKey|ciąg|Identyfikator GUID, który rejestruje węzeł za pomocą usługi ściągania. Aby uzyskać więcej informacji, zobacz [Konfigurowanie klienta ściągania z nazwami konfiguracji](../pull-server/pullClientConfigNames.md).|
|ServerURL|ciąg|Adres URL usługi konfiguracji.|
|ProxyURL*|ciąg|Adres URL serwera proxy HTTP, który ma być używany podczas komunikacji z usługą konfiguracji.|
|ProxyCredential*|PSCredential|Poświadczenie do użycia dla serwera proxy HTTP.|

> [!NOTE]
> * Obsługiwane w systemie Windows w wersji 1809 i nowszych.

Przykładowy skrypt służący do uproszczenia konfigurowania wartości ConfigurationRepositoryWeb dla węzłów lokalnych jest dostępny-zobacz [generowanie konfiguracji DSC](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Aby zdefiniować serwer konfiguracji oparty na protokole SMB, należy utworzyć blok **ConfigurationRepositoryShare** .
**ConfigurationRepositoryShare** definiuje następujące właściwości.

|Właściwość|Type|Opis|
|---|---|---|
|Poświadczenie|MSFT_Credential|Poświadczenie używane do uwierzytelniania w udziale SMB.|
|SourcePath|ciąg|Ścieżka udziału SMB.|

## <a name="resource-server-blocks"></a>Bloki serwera zasobów

Aby zdefiniować serwer zasobów oparty na sieci Web, należy utworzyć blok **ResourceRepositoryWeb** .
**ResourceRepositoryWeb** definiuje następujące właściwości.

|Właściwość|Type|Opis|
|---|---|---|
|AllowUnsecureConnection|logiczna|Ustaw wartość **$true** , aby zezwolić na połączenia z węzła z serwerem bez uwierzytelniania. Ustaw wartość **$false** , aby wymagać uwierzytelniania.|
|CertificateID|ciąg|Odcisk palca certyfikatu używanego do uwierzytelniania na serwerze.|
|RegistrationKey|ciąg|Identyfikator GUID, który identyfikuje węzeł usługi ściągania.|
|ServerURL|ciąg|Adres URL serwera konfiguracji.|
|ProxyURL*|ciąg|Adres URL serwera proxy HTTP, który ma być używany podczas komunikacji z usługą konfiguracji.|
|ProxyCredential*|PSCredential|Poświadczenie do użycia dla serwera proxy HTTP.|

> [!NOTE]
> * Obsługiwane w systemie Windows w wersji 1809 i nowszych.

Przykładowy skrypt służący do uproszczenia konfigurowania wartości ResourceRepositoryWeb dla węzłów lokalnych jest dostępny-zobacz [generowanie konfiguracji DSC](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Aby zdefiniować serwer zasobów oparty na protokole SMB, należy utworzyć blok **ResourceRepositoryShare** .
**ResourceRepositoryShare** definiuje następujące właściwości.

|Właściwość|Type|Opis|
|---|---|---|
|Poświadczenie|MSFT_Credential|Poświadczenie używane do uwierzytelniania w udziale SMB. Przykład przekazywania poświadczeń można znaleźć w temacie [Konfigurowanie serwera ściągania SMB protokołu DSC](../pull-server/pullServerSMB.md)|
|SourcePath|ciąg|Ścieżka udziału SMB.|

## <a name="report-server-blocks"></a>Bloki serwera raportów

Aby zdefiniować serwer raportów, należy utworzyć blok **ReportServerWeb** .
Rola serwera raportów nie jest zgodna z usługą ściągania opartą na protokole SMB.
**ReportServerWeb** definiuje następujące właściwości.

|Właściwość|Type|Opis|
|---|---|---|
|AllowUnsecureConnection|logiczna|Ustaw wartość **$true** , aby zezwolić na połączenia z węzła z serwerem bez uwierzytelniania. Ustaw wartość **$false** , aby wymagać uwierzytelniania.|
|CertificateID|ciąg|Odcisk palca certyfikatu używanego do uwierzytelniania na serwerze.|
|RegistrationKey|ciąg|Identyfikator GUID, który identyfikuje węzeł usługi ściągania.|
|ServerURL|ciąg|Adres URL serwera konfiguracji.|
|ProxyURL*|ciąg|Adres URL serwera proxy HTTP, który ma być używany podczas komunikacji z usługą konfiguracji.|
|ProxyCredential*|PSCredential|Poświadczenie do użycia dla serwera proxy HTTP.|

> [!NOTE]
> * Obsługiwane w systemie Windows w wersji 1809 i nowszych.

Przykładowy skrypt służący do uproszczenia konfigurowania wartości ReportServerWeb dla węzłów lokalnych jest dostępny-zobacz [generowanie konfiguracji DSC](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

## <a name="partial-configurations"></a>Konfiguracje częściowe

Aby zdefiniować konfigurację częściową, należy utworzyć blok **PartialConfiguration** .
Aby uzyskać więcej informacji o konfiguracjach częściowych, zobacz [częściowe konfiguracje DSC](../pull-server/partialConfigs.md).
**PartialConfiguration** definiuje następujące właściwości.

|Właściwość|Type|Opis|
|---|---|---|
|ConfigurationSource|ciąg []|Tablica nazw serwerów konfiguracji, wcześniej zdefiniowana w blokach **ConfigurationRepositoryWeb** i **ConfigurationRepositoryShare** , z których pobierana jest częściowa konfiguracja.|
|DependsOn|parametry{}|Lista nazw innych konfiguracji, które muszą zostać wykonane przed zastosowaniem tej konfiguracji częściowej.|
|Opis|ciąg|Tekst służący do opisywania konfiguracji częściowej.|
|ExclusiveResources|ciąg []|Tablica zasobów wyłącznie do tej konfiguracji częściowej.|
|RefreshMode|ciąg|Określa, jak LCM pobiera tę konfigurację częściową. Możliwe wartości to __"Disabled"__ , __"push"__ i __"pull"__ . <ul><li>__Wyłączone__: Ta częściowa konfiguracja jest wyłączona.</li><li> __Wypchnij__: Częściowa konfiguracja jest wypychana do węzła przez wywołanie polecenia cmdlet [Publish-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) . Gdy wszystkie częściowe konfiguracje węzła są wypychane lub ściągane z usługi, konfiguracja może być uruchamiana przez wywołanie `Start-DscConfiguration –UseExisting`. Jest to wartość domyślna.</li><li>__Pobierać__ Węzeł jest skonfigurowany do regularnego sprawdzania pod kątem częściowej konfiguracji z usługi ściągania. Jeśli ta właściwość jest ustawiona na __ściąganie__, należy określić usługę ściągania we właściwości __ConfigurationSource__ . Aby uzyskać więcej informacji na temat Azure Automation ściągania, zobacz [Omówienie usługi Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview).</li></ul>|
|ResourceModuleSource|ciąg []|Tablica nazw serwerów zasobów, z których mają zostać pobrane wymagane zasoby dla tej częściowej konfiguracji. Te nazwy muszą odwoływać się do punktów końcowych usługi zdefiniowanych wcześniej w blokach **ResourceRepositoryWeb** i **ResourceRepositoryShare** .|

__Uwaga:__ częściowa konfiguracja jest obsługiwana w przypadku Azure Automation DSC, ale tylko jedna konfiguracja może być pobierana z poszczególnych kont usługi Automation na węzeł.

## <a name="see-also"></a>Zobacz też

### <a name="concepts"></a>Pojęcia
[Przegląd konfiguracji żądanego stanu](../overview/overview.md)

[Wprowadzenie do Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-getting-started)

### <a name="other-resources"></a>Inne zasoby

[Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)

[Konfigurowanie klienta ściągania z nazwami konfiguracji](../pull-server/pullClientConfigNames.md)
