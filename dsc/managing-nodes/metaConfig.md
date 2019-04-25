---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Konfigurowanie programu Local Configuration Manager
ms.openlocfilehash: 86d2cc17872692a738e9c68121b8931833d2a251
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079681"
---
# <a name="configuring-the-local-configuration-manager"></a>Konfigurowanie programu Local Configuration Manager

> Dotyczy: Windows PowerShell 5.0

Lokalne Configuration Manager (LCM) to aparat z Desired State Configuration (DSC).
LCM działa na każdy węzeł docelowy i odpowiada za analizowanie i realizacja konfiguracji, które są wysyłane do węzła.
Jest również odpowiedzialny za wiele innych aspektów DSC, w tym następujące czynności.

- Określanie trybu odświeżania (wypychania lub ściągania).
- Określenie, jak często pobiera węzeł, a enacts konfiguracje.
- Kojarzenie węzła przy użyciu usługi ściągania.
- Określanie konfiguracje częściowe.

Specjalny rodzaj konfiguracji umożliwia konfigurowanie programu LCM, aby określić każdy z tych zachowań.
Konfigurowanie programu LCM można znaleźć w następujących sekcjach.

Windows PowerShell 5.0 wprowadzono nowe ustawienia dla zarządzania Local Configuration Manager.
Aby dowiedzieć się, jak konfigurowanie programu LCM w programie Windows PowerShell 4.0, zobacz [Konfigurowanie programu Local Configuration Manager w poprzednich wersjach Windows PowerShell](metaconfig4.md).

## <a name="writing-and-enacting-an-lcm-configuration"></a>Pisanie i realizacja konfiguracji LCM

Konfigurowanie programu LCM, możesz utworzyć i uruchomić specjalny rodzaj konfigurację, która stosuje ustawienia LCM.
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

Stosowanie ustawień do LCM proces jest podobny do stosowania konfiguracji DSC.
Będzie Utwórz konfigurację adresu LCM, skompiluj go do pliku MOF i zastosować je do węzła.
W przeciwieństwie do konfiguracji DSC, konfiguracja LCM nie wprowadza przez wywołanie metody [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) polecenia cmdlet.
Zamiast tego należy wywołać [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager), podając ścieżkę w konfiguracji LCM MOF jako parametr.
Po użytkownik wprowadza konfiguracji LCM, można sprawdzić właściwości LCM przez wywołanie metody [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) polecenia cmdlet.

Konfiguracja LCM mogą zawierać bloki tylko w przypadku ograniczony zestaw zasobów.
W poprzednim przykładzie, jest tylko zasób o nazwie **ustawienia**.
Są dostępne zasoby:

* **ConfigurationRepositoryWeb**: określa usługi ściągania HTTP do konfiguracji.
* **ConfigurationRepositoryShare**: Określa udziału SMB w przypadku konfiguracji.
* **ResourceRepositoryWeb**: określa usługi ściągania HTTP dla modułów.
* **ResourceRepositoryShare**: Określa udziału SMB dla modułów.
* **ReportServerWeb**: Określa usługa ściągania HTTP, do którego są wysyłane raporty.
* **PartialConfiguration**: udostępnia dane w celu włączenia konfiguracje częściowe.

## <a name="basic-settings"></a>Ustawienia podstawowe

Inne niż określanie usługi ściągania punktów końcowych i ścieżki i konfiguracje częściowe, wszystkie właściwości LCM są konfigurowane w **ustawienia** bloku.
Następujące właściwości są dostępne w **ustawienia** bloku.

|  Właściwość  |  Typ  |  Opis   |
|----------- |------- |--------------- |
| ActionAfterReboot| ciąg| Określa, co się dzieje po ponownym uruchomieniu podczas stosowania konfiguracji. Możliwe wartości to __"ContinueConfiguration"__ i __"StopConfiguration"__. <ul><li> __ContinueConfiguration__: Kontynuuj, stosowanie bieżącą konfigurację po ponownym rozruchu komputera. Jest to wartość domyślna</li><li>__StopConfiguration__: Zatrzymaj bieżącą konfigurację po ponownym rozruchu komputera.</li></ul>|
| AllowModuleOverwrite| wartość logiczna| __$TRUE__ Jeśli nowe konfiguracje pobrane z usługi ściągania mogą nadpisać stare w docelowym węźle. W przeciwnym razie $FALSE.|
| CertificateID| ciąg| Odcisk palca certyfikatu używany do zabezpieczania poświadczeń przekazanych w konfiguracji. Aby uzyskać więcej informacji, zobacz [chcesz zabezpieczyć poświadczenia w Desired State Configuration programu Windows PowerShell](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx)?. <br> __Uwaga:__ to odbywa się automatycznie, jeśli przy użyciu usługi ściągania usługi Azure Automation DSC.|
| ConfigurationDownloadManagers| CimInstance[]| Nieaktualne. Użyj __ConfigurationRepositoryWeb__ i __ConfigurationRepositoryShare__ bloków, aby zdefiniować ściągania konfiguracji punkty końcowe usługi.|
| ConfigurationID| ciąg| Dla wstecznej zgodności ze starszych ściągania usługi wersji. Identyfikator GUID, który identyfikuje plik konfiguracji, który można pobrać z usługi ściągania. Węzeł będzie pobierać konfiguracje usługi ściągania, jeśli nazwa konfiguracji MOF nosi nazwę ConfigurationID.mof.<br> __Uwaga:__ Jeśli ustawisz tę właściwość, rejestrowanie węzła przy użyciu usługi ściągania przy użyciu __RegistrationKey__ nie działa. Aby uzyskać więcej informacji, zobacz [Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji](../pull-server/pullClientConfigNames.md).|
| ConfigurationMode| ciąg | Określa, jak LCM faktycznie ma zastosowanie do konfiguracji do węzłów docelowych. Możliwe wartości to __"ApplyOnly"__,__"ApplyAndMonitor"__, i __"ApplyAndAutoCorrect"__. <ul><li>__ApplyOnly__: Ma zastosowanie do konfiguracji DSC, a nie robi nic więcej, chyba że nowa konfiguracja zostanie przypisany do węzła docelowego lub nowej konfiguracji są pobierane z usługi. Po początkowej stosowania nowej konfiguracji DSC nie sprawdza odejście od stanu wcześniej skonfigurowany. Należy pamiętać, że DSC podejmie próbę zastosowania konfiguracji, dopóki nie zostanie pomyślnie przed __ApplyOnly__ staje się skuteczny. </li><li> __ApplyAndMonitor__: Jest to wartość domyślna. LCM stosuje wszystkie nowe konfiguracje. Po początkowym aplikacji nowej konfiguracji Jeśli węzeł docelowy drifts z żądanego stanu DSC raporty niezgodności w dziennikach. Należy pamiętać, że DSC podejmie próbę zastosowania konfiguracji, dopóki nie zostanie pomyślnie przed __ApplyAndMonitor__ staje się skuteczny.</li><li>__ApplyAndAutoCorrect__: DSC stosuje wszystkie nowe konfiguracje. Po początkowym aplikacji nowej konfiguracji Jeśli węzeł docelowy drifts z żądanego stanu DSC raporty niezgodności w dziennikach, a następnie ponownie stosuje bieżącej konfiguracji.</li></ul>|
| ConfigurationModeFrequencyMins| UInt32| W ciągu kilku minut, bieżąca konfiguracja jest jak często sprawdzane i stosowane. Ta właściwość jest ignorowana, jeśli ustawiono właściwość ConfigurationMode ApplyOnly. Wartość domyślna to 15.|
| Element DebugMode| ciąg| Możliwe wartości to __Brak__, __ForceModuleImport__, i __wszystkich__. <ul><li>Ustaw __Brak__ zasoby pamięci podręcznej. To jest ustawieniem domyślnym i powinny być używane w scenariuszach produkcyjnych.</li><li>Ustawienie __ForceModuleImport__, powoduje, że LCM załadować ponownie wszystkie moduły zasobów DSC, nawet jeśli zostały wcześniej załadowane i pamięci podręcznej. Ma to wpływ na wydajność operacji DSC, ponieważ każdy moduł jest załadowany ponownie, przy użyciu. Zazwyczaj używasz tej wartości podczas debugowania zasobu</li><li>W tej wersji __wszystkich__ jest taka sama jak __ForceModuleImport__</li></ul> |
| RebootNodeIfNeeded| wartość logiczna| Ustaw tę opcję na `$true` umożliwia zasobów do ponownego rozruchu przy użyciu węzła `$global:DSCMachineStatus` flagi. W przeciwnym razie trzeba będzie ręcznie wykonać ponowne uruchomienie węzła dla żadnej konfiguracji, który go wymaga. Wartość domyślna to `$false`. Aby użyć tego ustawienia, jeśli warunek jest ponowny rozruch jest wprowadzany przez coś innego niż DSC (np. Instalator Windows), należy połączyć to ustawienie za pomocą [xPendingReboot](https://github.com/powershell/xpendingreboot) modułu.|
| Trybów RefreshMode| ciąg| Określa, jak LCM pobiera konfiguracje. Możliwe wartości to __"Wyłączone"__, __"Push"__, i __"Ściągania"__. <ul><li>__Wyłączone__: Konfiguracje DSC są wyłączone dla tego węzła.</li><li> __Wypychanie__: Konfiguracje są inicjowane przez wywołanie metody [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) polecenia cmdlet. Konfiguracja jest stosowana od razu do węzła. Jest to wartość domyślna.</li><li>__Ściągnij:__ Węzeł jest skonfigurowany do regularne sprawdzanie konfiguracji z usługi ściągania lub ścieżka SMB. Jeśli ta właściwość jest ustawiona __ściągnięcia__, należy określić HTTP (usługa) lub ścieżka SMB (udział) w __ConfigurationRepositoryWeb__ lub __ConfigurationRepositoryShare__ bloku.</li></ul>|
| RefreshFrequencyMins| Uint32| Interwał czasu w minutach, w których LCM sprawdza, czy usługa ściągania, aby uzyskać zaktualizowane konfiguracje. Ta wartość jest ignorowana, jeśli nie skonfigurowano programu LCM w trybie ściągnięcia. Wartość domyślna to 30.|
| ReportManagers| CimInstance[]| Nieaktualne. Użyj __ReportServerWeb__ bloków, aby zdefiniować punkt końcowy, aby wysłać dane raportowania usługi ściągania.|
| ResourceModuleManagers| CimInstance[]| Nieaktualne. Użyj __ResourceRepositoryWeb__ i __ResourceRepositoryShare__ bloków, aby zdefiniować ściągania usługi punktów końcowych HTTP lub ścieżek protokołu SMB, odpowiednio.|
| PartialConfigurations| CimInstance| Nie zaimplementowano. Nie używaj.|
| StatusRetentionTimeInDays | UInt32| Liczba dni, przez które LCM śledzi stan bieżącej konfiguracji.|

> [!NOTE]
> Rozpoczyna się LCM **ConfigurationModeFrequencyMins** na podstawie cyklu:
>
> - Nowe metaconfig jest stosowany przy użyciu `Set-DscLocalConfigurationManager`
> - Ponowne uruchomienie komputera
>
> Aby uzyskać dowolny warunek, gdzie proces czasomierza napotyka awarii, który zostanie wykryty w ciągu 30 sekund, a cykl zostanie ponownie uruchomiona.
> Operacja współbieżna może opóźnić cyklu z pracę, jeśli czas trwania tej operacji przekracza częstotliwość cyklu skonfigurowany, następnym czasomierza nie zostanie uruchomiona.
>
> Przykład metaconfig jest skonfigurowany z częstotliwością co 15 min ściągania i ściąganie odbywa się T1.  Węzeł nie zakończy pracę dla 16 w ciągu kilku minut.  Pierwszy cykl 15 minut jest ignorowana, a następnego ściągania nastąpi T1 + 15 + 15.

## <a name="pull-service"></a>Usługa ściągania

Konfiguracja LCM obsługuje definiowanie następujących typów punktów końcowych usługi ściągania:

- **Serwer konfiguracji**: Repozytorium w przypadku konfiguracji DSC. Definiowanie konfiguracji serwerów przy użyciu **ConfigurationRepositoryWeb** (dla serwerów opartych na sieci web) i **ConfigurationRepositoryShare** (dla serwerów opartych na SMB) bloki.
- **Serwer zasobów**: Repozytorium dla zasobów DSC, spakowany jako moduły programu PowerShell. Definiowanie serwerów zasobów przy użyciu **ResourceRepositoryWeb** (dla serwerów opartych na sieci web) i **ResourceRepositoryShare** (dla serwerów opartych na SMB) bloki.
- **Serwer raportów**: Usługa, która DSC wysyła dane raportu do. Definiowanie serwerów raportów przy użyciu **ReportServerWeb** bloków. Na serwerze raportów należy usługi sieci web.

Aby wyświetlić szczegółowe informacje na temat usługi ściągania, [Desired State Configuration usługi ściągania](../pull-server/pullServer.md).

## <a name="configuration-server-blocks"></a>Bloki serwera konfiguracji

Aby zdefiniować serwera konfiguracji opartej na sieci web, należy utworzyć **ConfigurationRepositoryWeb** bloku.
A **ConfigurationRepositoryWeb** definiuje następujące właściwości.

|Właściwość|Typ|Opis|
|---|---|---|
|AllowUnsecureConnection|wartość logiczna|Ustaw **$TRUE** umożliwia nawiązywanie połączeń z węzła do serwera bez uwierzytelniania. Ustaw **$FALSE** wymagające uwierzytelniania.|
|CertificateID|ciąg|Odcisk palca certyfikatu używany do uwierzytelniania serwera.|
|ConfigurationNames|Ciąg]|Tablica nazw konfiguracji do ściągnięcia przez węzeł docelowy. Są one używane tylko wtedy, gdy węzeł jest zarejestrowana przy użyciu usługi ściągania przy użyciu **RegistrationKey**. Aby uzyskać więcej informacji, zobacz [Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji](../pull-server/pullClientConfigNames.md).|
|RegistrationKey|ciąg|Identyfikator GUID, który rejestruje węzła przy użyciu usługi ściągania. Aby uzyskać więcej informacji, zobacz [Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji](../pull-server/pullClientConfigNames.md).|
|ServerURL|ciąg|Adres URL usługi konfiguracji.|

Przykładowy skrypt ułatwiają konfigurowanie wartość ConfigurationRepositoryWeb dla węzłów lokalnych jest dostępna — zobacz [metaconfigurations generowania DSC](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Aby zdefiniować serwer konfiguracji opartej na protokole SMB, należy utworzyć **ConfigurationRepositoryShare** bloku.
A **ConfigurationRepositoryShare** definiuje następujące właściwości.

|Właściwość|Typ|Opis|
|---|---|---|
|Poświadczenie|MSFT_Credential|Poświadczenia używane do uwierzytelniania w udziale SMB.|
|SourcePath|ciąg|Ścieżka udziału SMB.|

## <a name="resource-server-blocks"></a>Bloki serwera zasobów

Aby zdefiniować serwer zasobów opartych na sieci web, należy utworzyć **ResourceRepositoryWeb** bloku.
A **ResourceRepositoryWeb** definiuje następujące właściwości.

|Właściwość|Typ|Opis|
|---|---|---|
|AllowUnsecureConnection|wartość logiczna|Ustaw **$TRUE** umożliwia nawiązywanie połączeń z węzła do serwera bez uwierzytelniania. Ustaw **$FALSE** wymagające uwierzytelniania.|
|CertificateID|ciąg|Odcisk palca certyfikatu używany do uwierzytelniania serwera.|
|RegistrationKey|ciąg|Identyfikator GUID, który identyfikuje węzeł, aby usługa ściągania.|
|ServerURL|ciąg|Adres URL serwera konfiguracji.|

Przykładowy skrypt ułatwiają konfigurowanie wartość ResourceRepositoryWeb dla węzłów lokalnych jest dostępna — zobacz [metaconfigurations generowania DSC](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Aby zdefiniować serwer opartych na SMB zasobów, należy utworzyć **ResourceRepositoryShare** bloku.
**ResourceRepositoryShare** definiuje następujące właściwości.

|Właściwość|Typ|Opis|
|---|---|---|
|Poświadczenie|MSFT_Credential|Poświadczenia używane do uwierzytelniania w udziale SMB. Na przykład przekazywać poświadczenia zobacz [Konfigurowanie serwera ściągania DSC SMB](../pull-server/pullServerSMB.md)|
|SourcePath|ciąg|Ścieżka udziału SMB.|

## <a name="report-server-blocks"></a>Bloki serwera raportów

Aby zdefiniować serwera raportów, należy utworzyć **ReportServerWeb** bloku.
Rola serwera raportów nie jest zgodny z usługi ściągania opartych na SMB.
**ReportServerWeb** definiuje następujące właściwości.

|Właściwość|Typ|Opis|
|---|---|---|
|AllowUnsecureConnection|wartość logiczna|Ustaw **$TRUE** umożliwia nawiązywanie połączeń z węzła do serwera bez uwierzytelniania. Ustaw **$FALSE** wymagające uwierzytelniania.|
|CertificateID|ciąg|Odcisk palca certyfikatu używany do uwierzytelniania serwera.|
|RegistrationKey|ciąg|Identyfikator GUID, który identyfikuje węzeł, aby usługa ściągania.|
|ServerURL|ciąg|Adres URL serwera konfiguracji.|

Przykładowy skrypt ułatwiają konfigurowanie wartość ReportServerWeb dla węzłów lokalnych jest dostępna — zobacz [metaconfigurations generowania DSC](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

## <a name="partial-configurations"></a>Konfiguracje częściowe

Aby zdefiniować częściowe konfiguracji, należy utworzyć **PartialConfiguration** bloku.
Aby uzyskać więcej informacji na temat konfiguracje częściowe zobacz [konfiguracje DSC częściowego](../pull-server/partialConfigs.md).
**PartialConfiguration** definiuje następujące właściwości.

|Właściwość|Typ|Opis|
|---|---|---|
|ConfigurationSource|ciąg]|Tablica nazw serwerów konfiguracji, wcześniej zdefiniowanej w **ConfigurationRepositoryWeb** i **ConfigurationRepositoryShare** bloków, gdzie częściowe konfiguracji jest określany na podstawie.|
|dependsOn|ciąg{}|Lista nazw inne konfiguracje, które należy wykonać przed zastosowaniem tej konfiguracji częściowe.|
|Opis|ciąg|Tekst opisujący częściowe konfiguracji.|
|ExclusiveResources|ciąg]|Tablica zasobów dotyczących wyłącznie tej konfiguracji częściowe.|
|Trybów RefreshMode|ciąg|Określa, jak LCM pobiera tę konfigurację częściowe. Możliwe wartości to __"Wyłączone"__, __"Push"__, i __"Ściągania"__. <ul><li>__Wyłączone__: Ta konfiguracja częściowe jest wyłączona.</li><li> __Wypychanie__: Częściowe konfiguracji zostanie przypisany do węzła, wywołując [Publish-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) polecenia cmdlet. Po skopiowaniu wszystkie konfiguracje częściowe dla węzła, są wypychane lub pobierane z usługi, konfiguracji mogą być uruchamiane przez wywołanie `Start-DscConfiguration –UseExisting`. Jest to wartość domyślna.</li><li>__Ściągnij:__ Węzeł jest skonfigurowany do regularne sprawdzanie częściowe konfiguracji przy użyciu usługi ściągania. Jeśli ta właściwość jest ustawiona __ściągnięcia__, należy określić usługę ściągania __ConfigurationSource__ właściwości. Aby uzyskać więcej informacji na temat usługi ściągania usługi Azure Automation, zobacz [Omówienie usługi Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview).</li></ul>|
|ResourceModuleSource|ciąg]|Tablica nazw zasobów serwerów do pobrania wymaganych zasobów dla tej konfiguracji częściowe. Te nazwy muszą odwoływać się do punktów końcowych usługi wcześniej zdefiniowanej w **ResourceRepositoryWeb** i **ResourceRepositoryShare** bloków.|

__Uwaga:__ konfiguracje częściowe są obsługiwane za pomocą usługi Azure Automation DSC, ale tylko w jednej konfiguracji mogą być ściągane z każdego konta usługi automation w każdym węźle.

## <a name="see-also"></a>Zobacz też

### <a name="concepts"></a>Pojęcia
[Desired State Configuration — omówienie](../overview/overview.md)

[Wprowadzenie do usługi Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-getting-started)

### <a name="other-resources"></a>Inne zasoby

[Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)

[Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji](../pull-server/pullClientConfigNames.md)
