---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Desired State Configuration (DSC) — znane problemy i ograniczenia
ms.openlocfilehash: 6faf24795d14a93f265943029d9f6f1388f32263
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856196"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a>Desired State Configuration (DSC) — znane problemy i ograniczenia

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a>Zmiana powodująca niezgodność: Certyfikaty używane do szyfrowania/odszyfrowywania hasła w konfiguracjach DSC może nie działać po zainstalowaniu programu WMF 5.0 RTM

W wersjach programu WMF 4.0 i program WMF 5.0 w wersji zapoznawczej DSC nie pozwala haseł w konfiguracji, aby się o długości ponad 121 znaków. DSC dążenie do używania haseł krótki, nawet jeśli została żądanego długich i silne hasło. Zezwala na tej istotnej zmiany hasła, które mają być o dowolnej długości w konfiguracji DSC.

**Rozwiązanie:** Ponownie utworzyć certyfikat z użycia szyfrowanie danych lub klucz szyfrowanie klucza i użycia klucza rozszerzonego szyfrowania dokumentu (1.3.6.1.4.1.311.80.1). Aby uzyskać więcej informacji, zobacz [CmsMessage Chroń](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a>Polecenia cmdlet DSC może zakończyć się niepowodzeniem po zainstalowaniu programu WMF 5.0 RTM

`Start-DscConfiguration` i inne polecenia cmdlet DSC może zakończyć się niepowodzeniem po zainstalowaniu programu WMF 5.0 RTM z następującym błędem:

```Output
LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
+ CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
+ FullyQualifiedErrorId : MI RESULT 6
+ PSComputerName : localhost
```

**Rozwiązanie:** Aby usunąć DSCEngineCache.mof, uruchamiając następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień (Uruchom jako Administrator):

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a>Polecenia cmdlet DSC może nie działać, jeśli program WMF 5.0 RTM jest zainstalować dla już zainstalowanego programu WMF 5.0 produkcyjnych (wersja zapoznawcza)

**Rozwiązanie:** Uruchom następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień (Uruchom jako administrator):

```powershell
mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a>LCM przejść w niestabilnym stanie podczas korzystania z Get-DscConfiguration w element DebugMode

Jeśli element DebugMode LCM, naciskając klawisze CTRL + C powoduje zatrzymanie przetwarzania `Get-DscConfiguration` może spowodować, że LCM przejść do stanu niestabilnego. takie tego większości poleceń cmdlet DSC nie będzie działać.

**Rozwiązanie:** Nie, naciśnij klawisze CTRL + C podczas debugowania `Get-DscConfiguration` polecenia cmdlet.

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a>Stop-DscConfiguration może nie odpowiadać w element DebugMode

Jeśli element DebugMode, LCM `Stop-DscConfiguration` może nie odpowiadać podczas próby zatrzymania operacji uruchomione przez `Get-DscConfiguration`

**Rozwiązanie:** Zakończ debugowania rozpoczęto przez `Get-DscConfiguration` zgodnie z opisem w [zasoby DSC debugowania](/powershell/dsc/troubleshooting/debugResource).

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a>Żadne pełne komunikaty o błędach są wyświetlane w element DebugMode

Jeśli LCM **element DebugMode**, żadne komunikaty o błędach pełne są wyświetlane z zasobów DSC.

**Rozwiązanie:** Wyłącz **element DebugMode** aby zobaczyć pełne komunikaty z zasobu

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a>Invoke-DscResource operacji nie można pobrać przy użyciu polecenia cmdlet Get-DscConfigurationStatus

Po zakończeniu korzystania z `Invoke-DscResource` polecenia cmdlet, aby bezpośrednio wywoływać metody dowolnego zasobu, rekordy takich operacji nie można pobrać za pośrednictwem `Get-DscConfigurationStatus`.

**Rozwiązanie:** Brak.

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a>Get-DscConfigurationStatus zwraca ściągnięcia cyklu operacje jako typ **spójności**

Gdy węzeł ma wartość trybu odświeżania ŚCIĄGANIA, dla każdej operacji ściągania wykonywane, `Get-DscConfigurationStatus` polecenie cmdlet zgłasza typ operacji jako **spójności** zamiast *początkowej*

**Rozwiązanie:** Brak.

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a>Polecenie cmdlet Invoke-DscResource nie zwróci komunikatu w kolejności, w której zostały wyprodukowane

`Invoke-DscResource` Polecenie cmdlet nie może zwracać pełne, ostrzeżenie, i komunikaty o błędach w kolejności zostały wyprodukowane przez LCM lub zasobu DSC.

**Rozwiązanie:** Brak.

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a>Zasoby DSC nie można łatwo debugować, gdy jest używane z Invoke-DscResource

Gdy LCM działa w trybie debugowania, `Invoke-DscResource` polecenie cmdlet nie powoduje przekazania informacji o obszarze działania, aby nawiązać połączenie do debugowania. Aby uzyskać więcej informacji, zobacz [zasoby DSC debugowania](/powershell/dsc/troubleshooting/debugResource).

**Rozwiązanie:** Odnajdywanie i dołączyć do obszaru działania, za pomocą poleceń cmdlet `Get-PSHostProcessInfo`, `Enter-PSHostProcess` , `Get-Runspace` i `Debug-Runspace` debugowanie zasobów DSC.

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName    ProcessId AppDomainName
-----------    --------- -------------
powershell          3932 DefaultAppDomain
powershell_ise      2304 DefaultAppDomain
WmiPrvSE            3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name       ComputerName Type  State  Availability
-- ----       ------------ ----  -----  ------------
 2 Runspace2  localhost    Local Opened InBreakpoint
 5 RemoteHost localhost    Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a>Różne dokumenty częściowe konfiguracji dla tego samego węzła nie może mieć nazwy zasobów identyczne

W przypadku kilku częściowe konfiguracji, które zostały wdrożone na jednym węźle identyczne nazwy zasobów Przyczyna Uruchom błąd w czasie.

**Rozwiązanie:** Używać różnych nazw nawet w tych samych zasobów w różnych konfiguracjach częściowe.

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a>Start-DscConfiguration — UseExisting nie działa z - Credential

Korzystając z `Start-DscConfiguration` z **UseExisting** parametru **poświadczeń** parametr jest ignorowany. DSC używa domyślna tożsamość procesu, można kontynuować operacji. Powoduje błąd, gdy pozwala przejść na węźle zdalnym na potrzeby innego poświadczenia.

**Rozwiązanie:** Użyj sesji CIM do operacji zdalnych DSC:

```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a>Adresy IPv6 jako nazwy węzła w konfiguracjach DSC

Adresy IPv6 jako nazwy węzła w skrypty konfiguracji DSC nie są obsługiwane w tej wersji.

**Rozwiązanie:** Brak.

## <a name="debugging-of-class-based-dsc-resources"></a>Debugowanie `Class-Based` zasobów DSC

Debugowanie zasobów DSC oparte na klasach nie jest obsługiwane w tej wersji.

**Rozwiązanie:** Brak.

## <a name="variables-and-functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a>Zmienne i funkcje zdefiniowane w zakresie $script DSC oparte na klasach zasobów nie są zachowywane w wielu wywołań do zasobu DSC

Wiele kolejnych wywołań `Start-DSCConfiguration` zakończy się niepowodzeniem, jeśli konfiguracja jest za pomocą dowolnego oparte na klasach zasobu, który ma zmiennych lub funkcje zdefiniowane w `$script` zakresu.

**Rozwiązanie:** Zdefiniuj wszystkie zmienne i funkcje w samej klasy zasobów DSC. Nie `$script` funkcje zmiennych zakresu.

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a>Korzystając z zasobem jest PSDscRunAsCredential debugowanie zasobów DSC

Debugowanie zasobów DSC korzystając zasób **PSDscRunAsCredential** właściwość w konfiguracji nie jest obsługiwana w tej wersji.

**Rozwiązanie:** Brak.

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a>PsDscRunAsCredential nie jest obsługiwany dla złożonego zasobów DSC

**Rozwiązanie:** Użyj właściwości Credential, jeśli jest dostępne. Przykład ServiceSet i WindowsFeatureSet

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a>Get-DscResource — składnia nie będzie odzwierciedlał PsDscRunAsCredential poprawnie

**Składni** parametr nie będzie odzwierciedlał **PsDscRunAsCredential** poprawnie, gdy zasobu oznacza je jako wymagane lub nie obsługuje.

**Rozwiązanie:** Brak. Jednak tworzenie konfiguracji w środowisku ISE odzwierciedla prawidłowych metadanych dotyczących **PsDscRunAsCredential** właściwości, korzystając z funkcji IntelliSense.

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a>WindowsOptionalFeature nie jest dostępna w Windows 7

**WindowsOptionalFeature** zasób DSC nie jest dostępna w Windows 7. Ten zasób wymaga modułu DISM i poleceń cmdlet DISM, które są dostępne, począwszy od systemu Windows 8 i nowszych wersjach systemu operacyjnego Windows.

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a>Dla zasobów DSC oparte na klasach Import-DscResource - ModuleVersion może nie działać zgodnie z oczekiwaniami

Jeśli węzeł kompilacji ma wiele wersji moduł oparte na klasach zasobów DSC `Import-DscResource -ModuleVersion` nie odbiera określonej wersji i powoduje następujący błąd kompilacji.

```Output
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s):
 "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

**Rozwiązanie:** Importowanie wymaganą wersję, definiując **ModuleSpecification** obiekt **ModuleName** parametrem **RequiredVersion** klucza określonego w następujący sposób:

```powershell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a>Niektóre zasoby DSC, takich jak zasób rejestru może zacząć zająć dużo czasu, aby przetworzyć żądanie.

**Rozwiązanie nr 1.** Tworzenie zadania harmonogramu Okresowo czyści następujący folder.

```powershell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

**Rozwiązanie nr 2.** Zmień konfigurację DSC, aby wyczyścić *CommandAnalysis* folder po zakończeniu konfiguracji.

```powershell
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
        DependsOn = "[Registry]SetRegisteredOwner"
        getscript = "@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```
