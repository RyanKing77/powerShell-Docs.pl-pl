---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 66ceea383b78b2654caa4f1de16a30beea0e7fd3
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a>Konfiguracji żądanego stanu (DSC) — znane problemy i ograniczenia

<a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a>Fundamentalne zmiany: Certyfikaty używane do szyfrowania/odszyfrowywania hasła w konfiguracji DSC mogą nie działać po zainstalowaniu pakietu WMF 5.0 RTM
--------------------------------------------------------------------------------------------------------------------------------

W wersjach WMF 4.0 i WMF 5.0 w wersji zapoznawczej usługi Konfiguracja DSC nie pozwala haseł w konfiguracji, aby mieć długość 121 więcej niż znaków. DSC został wymuszanie używanie haseł krótkie, nawet jeśli została potrzeby długich i silne hasło. Ta zmiana podziału umożliwia hasła, które mają być o dowolnej długości w konfiguracji DSC.

**Rozwiązanie:** ponownie utworzyć certyfikat z użycia szyfrowanie danych lub klucz szyfrowanie klucza i użycia klucza rozszerzonego szyfrowania dokumentu (1.3.6.1.4.1.311.80.1). Artykuł w witrynie TechNet <https://technet.microsoft.com/library/dn807171.aspx> zawiera więcej informacji.


<a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a>Polecenia cmdlet DSC może zakończyć się niepowodzeniem po zainstalowaniu pakietu WMF 5.0 RTM
------------------------------------------------------------------------------------
Start DscConfiguration i innych poleceń cmdlet DSC może zakończyć się niepowodzeniem po zainstalowaniu pakietu WMF 5.0 RTM z powodu następującego błędu:
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

**Rozwiązanie:** Usuń DSCEngineCache.mof, uruchamiając następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień (Uruchom jako Administrator):

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```


<a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a>Polecenia cmdlet DSC mogą nie działać, jeśli WMF 5.0 RTM jest zainstalowany na górze WMF 5.0 produkcji podglądu
------------------------------------------------------
**Rozwiązanie:** uruchom następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień (Uruchom jako administrator):
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```


<a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a>LCM może przejść w niestabilnym stanie podczas używania Get-DscConfiguration w DebugMode
-------------------------------------------------------------------------------

Jeśli LCM DebugMode, naciskając klawisze CTRL + C, aby zatrzymać przetwarzanie Get-DscConfiguration może spowodować LCM przejść w niestabilnym stanie takie tego większości poleceń cmdlet DSC nie będą działać.

**Rozwiązanie:** nie naciśnij klawisze CTRL + C podczas debugowania polecenia cmdlet Get-DscConfiguration.


<a name="stop-dscconfiguration-may-hang-in-debugmode"></a>Stop-DscConfiguration mogą wykraczać w DebugMode
------------------------------------------------------------------------------------------------------------------------
Jeśli LCM DebugMode, Zatrzymaj DscConfiguration mogą wykraczać podczas próby zatrzymania operacji uruchomione przez Get DscConfiguration

**Rozwiązanie:** zakończyć debugowanie operacji uruchomione przez Get DscConfiguration, jak opisano w sekcji "[zasobów debugowania DSC](https://msdn.microsoft.com/powershell/dsc/debugresource)".


<a name="no-verbose-error-messages-are-shown-in-debugmode"></a>Żadne pełne komunikaty o błędach są wyświetlane w DebugMode
-----------------------------------------------------------------------------------
Jeśli LCM DebugMode, nie pełnych komunikatów o błędach są wyświetlane od zasobów usługi Konfiguracja DSC.

**Rozwiązanie:** wyłączyć *DebugMode* Aby wyświetlić komunikaty pełne z zasobu


<a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a>Nie można pobrać DscResource wywołania operacji przez polecenie cmdlet Get-DscConfigurationStatus
--------------------------------------------------------------------------------------
Po użyciu polecenia cmdlet Invoke-DscResource do bezpośredniego wywoływania metod dowolnego zasobu, rekordy takich operacji nie można pobrać za pomocą Get DscConfigurationStatus w późniejszym czasie.

**Rozwiązanie:** None.


<a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a>Get-DscConfigurationStatus zwraca ściągania cyklu operacje jako typ *spójności*
---------------------------------------------------------------------------------
Gdy węzeł ma ustawioną wartość trybu odświeżania ŚCIĄGANIA, dla każdej operacji ściągania wykonywana, polecenia cmdlet Get-DscConfigurationStatus raporty typ operacji jako *spójności* zamiast *początkowej*

**Rozwiązanie:** None.

<a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a>DscResource Wywołaj polecenie cmdlet nie zwraca komunikat w kolejności, które zostały wyprodukowane
---------------------------------------------------------------------------------
Polecenie cmdlet Invoke-DscResource nie może zwracać pełne, ostrzeżenie, i komunikaty o błędach w kolejności, które zostały one utworzone przez LCM lub zasobu usługi Konfiguracja DSC.

**Rozwiązanie:** None.


<a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a>Zasoby DSC nie można debugować łatwo, gdy jest używany z Invoke DscResource
-----------------------------------------------------------------------
Gdy LCM jest uruchomiony w trybie debugowania (zobacz [zasobów debugowania DSC](https://msdn.microsoft.com/powershell/dsc/debugresource) więcej szczegółów), polecenia cmdlet Invoke-DscResource nie zapewnia informacje o obszarze działania, aby nawiązać połączenie do debugowania.
**Rozwiązanie:** odnajdowania i dołączyć do działania za pomocą poleceń cmdlet **Get-PSHostProcessInfo**, **Enter PSHostProcess** , **obszaru działania Get** i **Obszaru działania debugowania** debugowania zasobów usługi Konfiguracja DSC.

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell 3932 DefaultAppDomain
powershell_ise 2304 DefaultAppDomain
WmiPrvSE 3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name ComputerName Type State Availability
-- ---- ------------ ---- ----- ------------
2 Runspace2 localhost Local Opened InBreakpoint
5 RemoteHost localhost Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```


<a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a>Różnych dokumentów częściowe konfiguracji dla tego samego węzła nie może mieć nazwy identyczne zasobów
------------------------------------------------------------------------------------------

W przypadku kilku częściowe konfiguracji wdrożonych na jednym węźle identycznych nazw zasobów Przyczyna Uruchom błąd w czasie.

**Rozwiązanie:** Użyj różnych nazw dla nawet tych samych zasobów w różnych konfiguracjach częściowej.


<a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a>Początek DscConfiguration — UseExisting nie działa z - Credential
------------------------------------------------------------------

Podczas korzystania z parametrem – UseExisting Start DscConfiguration Credential parametru jest ignorowana. DSC używa domyślna tożsamość procesu, aby kontynuować operację. W przypadku różnych poświadczeń są potrzebne, aby kontynuować na węźle zdalnym powoduje błąd.

**Rozwiązanie:** Użyj modelu wspólnych informacji sesji dla operacji zdalnych DSC:
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```


<a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a>Adresy IPv6 jako nazwy węzła w konfiguracji DSC
--------------------------------------------------
Adresy IPv6 jako nazwy węzła w skrypty do konfiguracji DSC nie są obsługiwane w tej wersji.

**Rozwiązanie:** None.


<a name="debugging-of-class-based-dsc-resources"></a>Debugowanie zasobów na podstawie klasy DSC
--------------------------------------
Debugowanie zasobów opartych na klasie DSC nie jest obsługiwane w tej wersji.

**Rozwiązanie:** None.


<a name="variables--functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a>Zmienne & funkcje zdefiniowane w zakresie zasobów na podstawie klasy DSC $script nie są zachowywane między wiele wywołań do zasobu usługi Konfiguracja DSC
-------------------------------------------------------------------------------------------------------------------------------------

Wiele kolejnych wywołań Start DSCConfiguration zakończy się niepowodzeniem, jeśli konfiguracja jest za pomocą dowolnego zasobu na podstawie klasy mającej zmiennych lub funkcje zdefiniowana w zakresie $script.

**Rozwiązanie:** zdefiniować wszystkie zmienne i funkcje w samej klasy zasobu usługi Konfiguracja DSC. Zmienne zakresu No $script/funkcje.


<a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a>Korzystając z zasobów jest PSDscRunAsCredential debugowanie zasobów DSC
----------------------------------------------------------------------
Debugowanie zasobów DSC używając zasobu *PSDscRunAsCredential* właściwość w konfiguracji nie jest suported w tej wersji.

**Rozwiązanie:** None.


<a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a>PsDscRunAsCredential nie jest obsługiwany dla złożonego zasobów DSC
----------------------------------------------------------------

**Rozwiązanie:** właściwości Użyj poświadczeń, jeśli jest dostępna. Przykład ServiceSet i WindowsFeatureSet


<a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a>*Get-DscResource-składni* nie odzwierciedla PsDscRunAsCredential poprawnie
-------------------------------------------------------------------------
Get-DscResource-składni nie odzwierciedla PsDscRunAsCredential poprawnie zasobów oznacza je jako wymagane lub nie jest ona obsługiwana.

**Rozwiązanie:** None. Jednak tworzenia konfiguracji w ISE odzwierciedla prawidłowych metadanych dotyczących PsDscRunAsCredential właściwości, korzystając z funkcji IntelliSense.


<a name="windowsoptionalfeature-is-not-available-in-windows-7"></a>WindowsOptionalFeature nie jest dostępna w systemie Windows 7
-----------------------------------------------------

Zasób WindowsOptionalFeature DSC nie jest dostępna w systemie Windows 7. Ten zasób wymaga modułu narzędzia DISM i poleceń cmdlet DISM, które są dostępne począwszy od systemu Windows 8 i nowszych wersjach systemu operacyjnego Windows.

<a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a>Dla zasobów na podstawie klasy DSC Import DscResource - ModuleVersion może nie działać zgodnie z oczekiwaniami
------------------------------------------------------------------------------------------
Jeśli węzeł kompilacji ma wiele wersji moduł klasy zasobu DSC `Import-DscResource -ModuleVersion` nie odbiera określonej wersji i powoduje następujący błąd kompilacji.

```
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s): "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

**Rozwiązanie:** zaimportować wymaganą wersję, definiując *ModuleSpecification* do obiektu `-ModuleName` z `RequiredVersion` klucz określony w następujący sposób:
``` PowerShell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

<a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a>Niektórych zasobów DSC, takich jak rejestru zasobu rozpoczęcie może zająć dużo czasu przetwarzania żądania.
--------------------------------------------------------------------------------------------------------------------------------

**Resolution1:** Tworzenie zadania harmonogramu czyści folderu Okresowo.
``` PowerShell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

**Resolution2:** zmiany konfiguracji DSC, aby wyczyścić *CommandAnalysis* folder po zakończeniu konfiguracji.
``` PowerShell
Configuration $configName
{

   # User Data
    Registry SetRegisteredOwner
    {
        Ensure = 'Present'
        Force = $True
        Key = $Node.RegisteredKey
        ValueName = $Node.RegisteredOwnerValue
        ValueType = 'String'
        ValueData = $Node.RegisteredOwnerData
    }
    #
    # Script to delete the config
    #
    script DeleteCommandAnalysisCache
    {
        DependsOn="[Registry]SetRegisteredOwner"
        getscript="@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```