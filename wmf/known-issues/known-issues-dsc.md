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
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a><span data-ttu-id="28ba0-103">Desired State Configuration (DSC) — znane problemy i ograniczenia</span><span class="sxs-lookup"><span data-stu-id="28ba0-103">Desired State Configuration (DSC) Known Issues and Limitations</span></span>

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a><span data-ttu-id="28ba0-104">Zmiana powodująca niezgodność: Certyfikaty używane do szyfrowania/odszyfrowywania hasła w konfiguracjach DSC może nie działać po zainstalowaniu programu WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="28ba0-104">Breaking Change: Certificates used to encrypt/decrypt passwords in DSC configurations may not work after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="28ba0-105">W wersjach programu WMF 4.0 i program WMF 5.0 w wersji zapoznawczej DSC nie pozwala haseł w konfiguracji, aby się o długości ponad 121 znaków.</span><span class="sxs-lookup"><span data-stu-id="28ba0-105">In WMF 4.0 and WMF 5.0 Preview releases, DSC would not allow passwords in the configuration to be of length more than 121 characters.</span></span> <span data-ttu-id="28ba0-106">DSC dążenie do używania haseł krótki, nawet jeśli została żądanego długich i silne hasło.</span><span class="sxs-lookup"><span data-stu-id="28ba0-106">DSC was forcing to use short passwords even if lengthy and strong password was desired.</span></span> <span data-ttu-id="28ba0-107">Zezwala na tej istotnej zmiany hasła, które mają być o dowolnej długości w konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="28ba0-107">This breaking change allows passwords to be of arbitrary length in the DSC configuration.</span></span>

<span data-ttu-id="28ba0-108">**Rozwiązanie:** Ponownie utworzyć certyfikat z użycia szyfrowanie danych lub klucz szyfrowanie klucza i użycia klucza rozszerzonego szyfrowania dokumentu (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="28ba0-108">**Resolution:** Re-create the certificate with Data Encipherment or Key Encipherment Key usage, and Document Encryption Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span></span> <span data-ttu-id="28ba0-109">Aby uzyskać więcej informacji, zobacz [CmsMessage Chroń](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).</span><span class="sxs-lookup"><span data-stu-id="28ba0-109">For more information, see [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).</span></span>

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a><span data-ttu-id="28ba0-110">Polecenia cmdlet DSC może zakończyć się niepowodzeniem po zainstalowaniu programu WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="28ba0-110">DSC cmdlets may fail after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="28ba0-111">`Start-DscConfiguration` i inne polecenia cmdlet DSC może zakończyć się niepowodzeniem po zainstalowaniu programu WMF 5.0 RTM z następującym błędem:</span><span class="sxs-lookup"><span data-stu-id="28ba0-111">`Start-DscConfiguration` and other DSC cmdlets may fail after installing WMF 5.0 RTM with the following error:</span></span>

```Output
LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
+ CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
+ FullyQualifiedErrorId : MI RESULT 6
+ PSComputerName : localhost
```

<span data-ttu-id="28ba0-112">**Rozwiązanie:** Aby usunąć DSCEngineCache.mof, uruchamiając następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień (Uruchom jako Administrator):</span><span class="sxs-lookup"><span data-stu-id="28ba0-112">**Resolution:** Delete DSCEngineCache.mof by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a><span data-ttu-id="28ba0-113">Polecenia cmdlet DSC może nie działać, jeśli program WMF 5.0 RTM jest zainstalować dla już zainstalowanego programu WMF 5.0 produkcyjnych (wersja zapoznawcza)</span><span class="sxs-lookup"><span data-stu-id="28ba0-113">DSC cmdlets may not work if WMF 5.0 RTM is installed on top of WMF 5.0 Production Preview</span></span>

<span data-ttu-id="28ba0-114">**Rozwiązanie:** Uruchom następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień (Uruchom jako administrator):</span><span class="sxs-lookup"><span data-stu-id="28ba0-114">**Resolution:** Run the following command in an elevated PowerShell session (run as administrator):</span></span>

```powershell
mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a><span data-ttu-id="28ba0-115">LCM przejść w niestabilnym stanie podczas korzystania z Get-DscConfiguration w element DebugMode</span><span class="sxs-lookup"><span data-stu-id="28ba0-115">LCM can go into an unstable state while using Get-DscConfiguration in DebugMode</span></span>

<span data-ttu-id="28ba0-116">Jeśli element DebugMode LCM, naciskając klawisze CTRL + C powoduje zatrzymanie przetwarzania `Get-DscConfiguration` może spowodować, że LCM przejść do stanu niestabilnego. takie tego większości poleceń cmdlet DSC nie będzie działać.</span><span class="sxs-lookup"><span data-stu-id="28ba0-116">If LCM is in DebugMode, pressing CTRL+C to stop the processing of `Get-DscConfiguration` can cause LCM to go into an unstable state such that majority of DSC cmdlets won’t work.</span></span>

<span data-ttu-id="28ba0-117">**Rozwiązanie:** Nie, naciśnij klawisze CTRL + C podczas debugowania `Get-DscConfiguration` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="28ba0-117">**Resolution:** Don’t press CTRL+C while debugging `Get-DscConfiguration` cmdlet.</span></span>

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a><span data-ttu-id="28ba0-118">Stop-DscConfiguration może nie odpowiadać w element DebugMode</span><span class="sxs-lookup"><span data-stu-id="28ba0-118">Stop-DscConfiguration may not respond in DebugMode</span></span>

<span data-ttu-id="28ba0-119">Jeśli element DebugMode, LCM `Stop-DscConfiguration` może nie odpowiadać podczas próby zatrzymania operacji uruchomione przez `Get-DscConfiguration`</span><span class="sxs-lookup"><span data-stu-id="28ba0-119">If LCM is in DebugMode, `Stop-DscConfiguration` may not respond while trying to stop an operation started by `Get-DscConfiguration`</span></span>

<span data-ttu-id="28ba0-120">**Rozwiązanie:** Zakończ debugowania rozpoczęto przez `Get-DscConfiguration` zgodnie z opisem w [zasoby DSC debugowania](/powershell/dsc/troubleshooting/debugResource).</span><span class="sxs-lookup"><span data-stu-id="28ba0-120">**Resolution:** Finish the debugging of the operation started by `Get-DscConfiguration` as outlined in [Debugging DSC resources](/powershell/dsc/troubleshooting/debugResource).</span></span>

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a><span data-ttu-id="28ba0-121">Żadne pełne komunikaty o błędach są wyświetlane w element DebugMode</span><span class="sxs-lookup"><span data-stu-id="28ba0-121">No Verbose Error Messages are shown in DebugMode</span></span>

<span data-ttu-id="28ba0-122">Jeśli LCM **element DebugMode**, żadne komunikaty o błędach pełne są wyświetlane z zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="28ba0-122">If LCM is in **DebugMode**, no verbose error messages are displayed from DSC Resources.</span></span>

<span data-ttu-id="28ba0-123">**Rozwiązanie:** Wyłącz **element DebugMode** aby zobaczyć pełne komunikaty z zasobu</span><span class="sxs-lookup"><span data-stu-id="28ba0-123">**Resolution:** Disable **DebugMode** to see verbose messages from the resource</span></span>

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="28ba0-124">Invoke-DscResource operacji nie można pobrać przy użyciu polecenia cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="28ba0-124">Invoke-DscResource operations cannot be retrieved by Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="28ba0-125">Po zakończeniu korzystania z `Invoke-DscResource` polecenia cmdlet, aby bezpośrednio wywoływać metody dowolnego zasobu, rekordy takich operacji nie można pobrać za pośrednictwem `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="28ba0-125">After using `Invoke-DscResource` cmdlet to directly invoke any resource’s methods, the records of such operation cannot be retrieved through `Get-DscConfigurationStatus`.</span></span>

<span data-ttu-id="28ba0-126">**Rozwiązanie:** Brak.</span><span class="sxs-lookup"><span data-stu-id="28ba0-126">**Resolution:** None.</span></span>

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a><span data-ttu-id="28ba0-127">Get-DscConfigurationStatus zwraca ściągnięcia cyklu operacje jako typ **spójności**</span><span class="sxs-lookup"><span data-stu-id="28ba0-127">Get-DscConfigurationStatus returns pull cycle operations as type **Consistency**</span></span>

<span data-ttu-id="28ba0-128">Gdy węzeł ma wartość trybu odświeżania ŚCIĄGANIA, dla każdej operacji ściągania wykonywane, `Get-DscConfigurationStatus` polecenie cmdlet zgłasza typ operacji jako **spójności** zamiast *początkowej*</span><span class="sxs-lookup"><span data-stu-id="28ba0-128">When a node is set to PULL refresh mode, for each pull operation performed, `Get-DscConfigurationStatus` cmdlet reports the operation type as **Consistency** instead of *Initial*</span></span>

<span data-ttu-id="28ba0-129">**Rozwiązanie:** Brak.</span><span class="sxs-lookup"><span data-stu-id="28ba0-129">**Resolution:** None.</span></span>

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a><span data-ttu-id="28ba0-130">Polecenie cmdlet Invoke-DscResource nie zwróci komunikatu w kolejności, w której zostały wyprodukowane</span><span class="sxs-lookup"><span data-stu-id="28ba0-130">Invoke-DscResource cmdlet does not return message in the order they were produced</span></span>

<span data-ttu-id="28ba0-131">`Invoke-DscResource` Polecenie cmdlet nie może zwracać pełne, ostrzeżenie, i komunikaty o błędach w kolejności zostały wyprodukowane przez LCM lub zasobu DSC.</span><span class="sxs-lookup"><span data-stu-id="28ba0-131">The `Invoke-DscResource` cmdlet does not return verbose, warning, and error messages in the order they were produced by LCM or the DSC resource.</span></span>

<span data-ttu-id="28ba0-132">**Rozwiązanie:** Brak.</span><span class="sxs-lookup"><span data-stu-id="28ba0-132">**Resolution:** None.</span></span>

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a><span data-ttu-id="28ba0-133">Zasoby DSC nie można łatwo debugować, gdy jest używane z Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="28ba0-133">DSC Resources cannot be debugged easily when used with Invoke-DscResource</span></span>

<span data-ttu-id="28ba0-134">Gdy LCM działa w trybie debugowania, `Invoke-DscResource` polecenie cmdlet nie powoduje przekazania informacji o obszarze działania, aby nawiązać połączenie do debugowania.</span><span class="sxs-lookup"><span data-stu-id="28ba0-134">When LCM is running in debug mode, `Invoke-DscResource` cmdlet does not give information about runspace to connect to for debugging.</span></span> <span data-ttu-id="28ba0-135">Aby uzyskać więcej informacji, zobacz [zasoby DSC debugowania](/powershell/dsc/troubleshooting/debugResource).</span><span class="sxs-lookup"><span data-stu-id="28ba0-135">For more information, see [Debugging DSC resources](/powershell/dsc/troubleshooting/debugResource).</span></span>

<span data-ttu-id="28ba0-136">**Rozwiązanie:** Odnajdywanie i dołączyć do obszaru działania, za pomocą poleceń cmdlet `Get-PSHostProcessInfo`, `Enter-PSHostProcess` , `Get-Runspace` i `Debug-Runspace` debugowanie zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="28ba0-136">**Resolution:** Discover and attach to the runspace using cmdlets `Get-PSHostProcessInfo`, `Enter-PSHostProcess` , `Get-Runspace` and `Debug-Runspace` to debug the DSC resource.</span></span>

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

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a><span data-ttu-id="28ba0-137">Różne dokumenty częściowe konfiguracji dla tego samego węzła nie może mieć nazwy zasobów identyczne</span><span class="sxs-lookup"><span data-stu-id="28ba0-137">Various Partial Configuration documents for same node cannot have identical resource names</span></span>

<span data-ttu-id="28ba0-138">W przypadku kilku częściowe konfiguracji, które zostały wdrożone na jednym węźle identyczne nazwy zasobów Przyczyna Uruchom błąd w czasie.</span><span class="sxs-lookup"><span data-stu-id="28ba0-138">For several partial configurations that are deployed onto a single node, identical names of resources cause run time error.</span></span>

<span data-ttu-id="28ba0-139">**Rozwiązanie:** Używać różnych nazw nawet w tych samych zasobów w różnych konfiguracjach częściowe.</span><span class="sxs-lookup"><span data-stu-id="28ba0-139">**Resolution:** Use different names for even same resources in different partial configurations.</span></span>

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a><span data-ttu-id="28ba0-140">Start-DscConfiguration — UseExisting nie działa z - Credential</span><span class="sxs-lookup"><span data-stu-id="28ba0-140">Start-DscConfiguration –UseExisting does not work with -Credential</span></span>

<span data-ttu-id="28ba0-141">Korzystając z `Start-DscConfiguration` z **UseExisting** parametru **poświadczeń** parametr jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="28ba0-141">When using `Start-DscConfiguration` with **UseExisting** parameter, the **Credential** parameter is ignored.</span></span> <span data-ttu-id="28ba0-142">DSC używa domyślna tożsamość procesu, można kontynuować operacji.</span><span class="sxs-lookup"><span data-stu-id="28ba0-142">DSC uses default process identity to proceed the operation.</span></span> <span data-ttu-id="28ba0-143">Powoduje błąd, gdy pozwala przejść na węźle zdalnym na potrzeby innego poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="28ba0-143">This causes error when a different credential is needed to proceed on remote node.</span></span>

<span data-ttu-id="28ba0-144">**Rozwiązanie:** Użyj sesji CIM do operacji zdalnych DSC:</span><span class="sxs-lookup"><span data-stu-id="28ba0-144">**Resolution:** Use CIM session for remote DSC operations:</span></span>

```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a><span data-ttu-id="28ba0-145">Adresy IPv6 jako nazwy węzła w konfiguracjach DSC</span><span class="sxs-lookup"><span data-stu-id="28ba0-145">IPv6 Addresses as Node Names in DSC configurations</span></span>

<span data-ttu-id="28ba0-146">Adresy IPv6 jako nazwy węzła w skrypty konfiguracji DSC nie są obsługiwane w tej wersji.</span><span class="sxs-lookup"><span data-stu-id="28ba0-146">IPv6 addresses as node names in DSC configuration scripts are not supported in this release.</span></span>

<span data-ttu-id="28ba0-147">**Rozwiązanie:** Brak.</span><span class="sxs-lookup"><span data-stu-id="28ba0-147">**Resolution:** None.</span></span>

## <a name="debugging-of-class-based-dsc-resources"></a><span data-ttu-id="28ba0-148">Debugowanie `Class-Based` zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="28ba0-148">Debugging of `Class-Based` DSC Resources</span></span>

<span data-ttu-id="28ba0-149">Debugowanie zasobów DSC oparte na klasach nie jest obsługiwane w tej wersji.</span><span class="sxs-lookup"><span data-stu-id="28ba0-149">Debugging of class-based DSC Resources is not supported in this release.</span></span>

<span data-ttu-id="28ba0-150">**Rozwiązanie:** Brak.</span><span class="sxs-lookup"><span data-stu-id="28ba0-150">**Resolution:** None.</span></span>

## <a name="variables-and-functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a><span data-ttu-id="28ba0-151">Zmienne i funkcje zdefiniowane w zakresie $script DSC oparte na klasach zasobów nie są zachowywane w wielu wywołań do zasobu DSC</span><span class="sxs-lookup"><span data-stu-id="28ba0-151">Variables and functions defined in $script scope in DSC Class-Based Resource are not preserved across multiple calls to a DSC Resource</span></span>

<span data-ttu-id="28ba0-152">Wiele kolejnych wywołań `Start-DSCConfiguration` zakończy się niepowodzeniem, jeśli konfiguracja jest za pomocą dowolnego oparte na klasach zasobu, który ma zmiennych lub funkcje zdefiniowane w `$script` zakresu.</span><span class="sxs-lookup"><span data-stu-id="28ba0-152">Multiple consecutive calls to `Start-DSCConfiguration` fails if the configuration is using any class-based resource which has variables or functions defined in `$script` scope.</span></span>

<span data-ttu-id="28ba0-153">**Rozwiązanie:** Zdefiniuj wszystkie zmienne i funkcje w samej klasy zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="28ba0-153">**Resolution:** Define all variables and functions in DSC Resource class itself.</span></span> <span data-ttu-id="28ba0-154">Nie `$script` funkcje zmiennych zakresu.</span><span class="sxs-lookup"><span data-stu-id="28ba0-154">No `$script` scope variables/functions.</span></span>

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a><span data-ttu-id="28ba0-155">Korzystając z zasobem jest PSDscRunAsCredential debugowanie zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="28ba0-155">DSC Resource Debugging when a resource is using PSDscRunAsCredential</span></span>

<span data-ttu-id="28ba0-156">Debugowanie zasobów DSC korzystając zasób **PSDscRunAsCredential** właściwość w konfiguracji nie jest obsługiwana w tej wersji.</span><span class="sxs-lookup"><span data-stu-id="28ba0-156">DSC Resource debugging when a resource is using the **PSDscRunAsCredential** property in the configuration is not supported in this release.</span></span>

<span data-ttu-id="28ba0-157">**Rozwiązanie:** Brak.</span><span class="sxs-lookup"><span data-stu-id="28ba0-157">**Resolution:** None.</span></span>

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a><span data-ttu-id="28ba0-158">PsDscRunAsCredential nie jest obsługiwany dla złożonego zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="28ba0-158">PsDscRunAsCredential is not supported for DSC Composite Resources</span></span>

<span data-ttu-id="28ba0-159">**Rozwiązanie:** Użyj właściwości Credential, jeśli jest dostępne.</span><span class="sxs-lookup"><span data-stu-id="28ba0-159">**Resolution:** Use Credential property if available.</span></span> <span data-ttu-id="28ba0-160">Przykład ServiceSet i WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="28ba0-160">Example ServiceSet and WindowsFeatureSet</span></span>

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a><span data-ttu-id="28ba0-161">Get-DscResource — składnia nie będzie odzwierciedlał PsDscRunAsCredential poprawnie</span><span class="sxs-lookup"><span data-stu-id="28ba0-161">Get-DscResource -Syntax does not reflect PsDscRunAsCredential correctly</span></span>

<span data-ttu-id="28ba0-162">**Składni** parametr nie będzie odzwierciedlał **PsDscRunAsCredential** poprawnie, gdy zasobu oznacza je jako wymagane lub nie obsługuje.</span><span class="sxs-lookup"><span data-stu-id="28ba0-162">The **Syntax** parameter does not reflect **PsDscRunAsCredential** correctly when resource marks it as mandatory or does not support it.</span></span>

<span data-ttu-id="28ba0-163">**Rozwiązanie:** Brak.</span><span class="sxs-lookup"><span data-stu-id="28ba0-163">**Resolution:** None.</span></span> <span data-ttu-id="28ba0-164">Jednak tworzenie konfiguracji w środowisku ISE odzwierciedla prawidłowych metadanych dotyczących **PsDscRunAsCredential** właściwości, korzystając z funkcji IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="28ba0-164">However, authoring configuration in ISE reflects correct metadata about **PsDscRunAsCredential** property when using IntelliSense.</span></span>

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a><span data-ttu-id="28ba0-165">WindowsOptionalFeature nie jest dostępna w Windows 7</span><span class="sxs-lookup"><span data-stu-id="28ba0-165">WindowsOptionalFeature is not available in Windows 7</span></span>

<span data-ttu-id="28ba0-166">**WindowsOptionalFeature** zasób DSC nie jest dostępna w Windows 7.</span><span class="sxs-lookup"><span data-stu-id="28ba0-166">The **WindowsOptionalFeature** DSC resource is not available in Windows 7.</span></span> <span data-ttu-id="28ba0-167">Ten zasób wymaga modułu DISM i poleceń cmdlet DISM, które są dostępne, począwszy od systemu Windows 8 i nowszych wersjach systemu operacyjnego Windows.</span><span class="sxs-lookup"><span data-stu-id="28ba0-167">This resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.</span></span>

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a><span data-ttu-id="28ba0-168">Dla zasobów DSC oparte na klasach Import-DscResource - ModuleVersion może nie działać zgodnie z oczekiwaniami</span><span class="sxs-lookup"><span data-stu-id="28ba0-168">For Class-based DSC resources, Import-DscResource -ModuleVersion may not work as expected</span></span>

<span data-ttu-id="28ba0-169">Jeśli węzeł kompilacji ma wiele wersji moduł oparte na klasach zasobów DSC `Import-DscResource -ModuleVersion` nie odbiera określonej wersji i powoduje następujący błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="28ba0-169">If the compilation node has multiple versions of a class-based DSC resource module, `Import-DscResource -ModuleVersion` does not pick the specified version and results in following compilation error.</span></span>

```Output
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s):
 "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

<span data-ttu-id="28ba0-170">**Rozwiązanie:** Importowanie wymaganą wersję, definiując **ModuleSpecification** obiekt **ModuleName** parametrem **RequiredVersion** klucza określonego w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="28ba0-170">**Resolution:** Import the required version by defining the **ModuleSpecification** object to the **ModuleName** parameter with **RequiredVersion** key specified as follows:</span></span>

```powershell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a><span data-ttu-id="28ba0-171">Niektóre zasoby DSC, takich jak zasób rejestru może zacząć zająć dużo czasu, aby przetworzyć żądanie.</span><span class="sxs-lookup"><span data-stu-id="28ba0-171">Some DSC resources like registry resource may start to take a long time to process the request.</span></span>

<span data-ttu-id="28ba0-172">**Rozwiązanie nr 1.** Tworzenie zadania harmonogramu Okresowo czyści następujący folder.</span><span class="sxs-lookup"><span data-stu-id="28ba0-172">**Resolution 1:** Create a schedule task that cleans up the following folder periodically.</span></span>

```powershell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

<span data-ttu-id="28ba0-173">**Rozwiązanie nr 2.** Zmień konfigurację DSC, aby wyczyścić *CommandAnalysis* folder po zakończeniu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="28ba0-173">**Resolution 2:** Change the DSC configuration to clean up the *CommandAnalysis* folder at the end of the configuration.</span></span>

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
