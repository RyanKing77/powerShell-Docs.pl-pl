---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Korzystanie z platformy DSC na serwerze Nano Server
ms.openlocfilehash: fb826455c21833ae4c8dc2ecd731ffce6bf7eaba
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734615"
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="730c0-103">Korzystanie z platformy DSC na serwerze Nano Server</span><span class="sxs-lookup"><span data-stu-id="730c0-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="730c0-104">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="730c0-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="730c0-105">**DSC na serwerze Nano Server** jest opcjonalny pakiet w `NanoServer\Packages` folderu nośników systemu Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="730c0-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="730c0-106">Po utworzeniu wirtualnego dysku twardego, określając dla serwera Nano Server można zainstalować pakietu **Microsoft-NanoServer-DSC-Package** jako wartość **pakietów** parametru **New-NanoServerImage**  funkcji.</span><span class="sxs-lookup"><span data-stu-id="730c0-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="730c0-107">Na przykład w przypadku tworzenia dysku VHD dla maszyny wirtualnej, polecenie będzie wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="730c0-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="730c0-108">Aby uzyskać informacje o instalowaniu i używaniu serwera Nano Server, a także jak zarządzać serwerem Nano Server przy użyciu komunikacji zdalnej programu PowerShell, zobacz [wprowadzenie Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span><span class="sxs-lookup"><span data-stu-id="730c0-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span></span>

## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="730c0-109">Funkcji DSC, które są dostępne na serwerze Nano Server</span><span class="sxs-lookup"><span data-stu-id="730c0-109">DSC features available on Nano Server</span></span>

<span data-ttu-id="730c0-110">Ponieważ serwer Nano Server obsługuje tylko ograniczony zestaw interfejsów API w porównaniu do pełnej wersji systemu Windows Server, DSC na serwerze Nano Server nie ma pełnych parzystość za pomocą DSC uruchomionych na pełne jednostki SKU dla przez pewien czas.</span><span class="sxs-lookup"><span data-stu-id="730c0-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="730c0-111">DSC na serwerze Nano Server jest aktywnie i nie jest jeszcze funkcji ukończone.</span><span class="sxs-lookup"><span data-stu-id="730c0-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

<span data-ttu-id="730c0-112">Następujące funkcje DSC są obecnie dostępne na serwerze Nano Server:</span><span class="sxs-lookup"><span data-stu-id="730c0-112">The following DSC features are currently available on Nano Server:</span></span>

<span data-ttu-id="730c0-113">Trybach wypychania i ściągania</span><span class="sxs-lookup"><span data-stu-id="730c0-113">Both push and pull modes</span></span>

- <span data-ttu-id="730c0-114">Wszystkie polecenia cmdlet DSC, które istnieją w pełnej wersji systemu Windows Server, w tym następujące:</span><span class="sxs-lookup"><span data-stu-id="730c0-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
- [<span data-ttu-id="730c0-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="730c0-115">Get-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [<span data-ttu-id="730c0-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="730c0-116">Set-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [<span data-ttu-id="730c0-117">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="730c0-117">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [<span data-ttu-id="730c0-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="730c0-118">Disable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [<span data-ttu-id="730c0-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="730c0-119">Start-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [<span data-ttu-id="730c0-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="730c0-120">Stop-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [<span data-ttu-id="730c0-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="730c0-121">Get-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [<span data-ttu-id="730c0-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="730c0-122">Test-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [<span data-ttu-id="730c0-123">Publish-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="730c0-123">Publish-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [<span data-ttu-id="730c0-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="730c0-124">Update-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [<span data-ttu-id="730c0-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="730c0-125">Restore-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [<span data-ttu-id="730c0-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="730c0-126">Remove-DscConfigurationDocument</span></span>](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [<span data-ttu-id="730c0-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="730c0-127">Get-DscConfigurationStatus</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [<span data-ttu-id="730c0-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="730c0-128">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [<span data-ttu-id="730c0-129">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="730c0-129">Find-DscResource</span></span>](/powershell/module/powershellget/find-dscresource?view=powershell-6)
- [<span data-ttu-id="730c0-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="730c0-130">Get-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [<span data-ttu-id="730c0-131">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="730c0-131">New-DscChecksum</span></span>](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- <span data-ttu-id="730c0-132">Kompilowanie konfiguracji (zobacz [konfiguracje DSC](../configurations/configurations.md))</span><span class="sxs-lookup"><span data-stu-id="730c0-132">Compiling configurations (see [DSC configurations](../configurations/configurations.md))</span></span>

  <span data-ttu-id="730c0-133">**Problem:** Hasło szyfrowania (zobacz [Zabezpieczanie pliku MOF](../pull-server/secureMOF.md)) podczas konfiguracji kompilacji nie działa.</span><span class="sxs-lookup"><span data-stu-id="730c0-133">**Issue:** Password encryption (see [Securing the MOF File](../pull-server/secureMOF.md)) during configuration compilation doesn't work.</span></span>

- <span data-ttu-id="730c0-134">Kompilowanie metaconfigurations (zobacz [Konfigurowanie programu Local Configuration Manager](../managing-nodes/metaConfig.md))</span><span class="sxs-lookup"><span data-stu-id="730c0-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md))</span></span>

- <span data-ttu-id="730c0-135">Uruchamianie zasobami dostępnymi w ramach kontekstu użytkownika (zobacz [systemem DSC przy użyciu poświadczeń użytkownika (Uruchom jako)](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="730c0-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](../configurations/runAsUser.md))</span></span>

- <span data-ttu-id="730c0-136">Zasoby oparte na klasach (zobacz [pisanie zasobu DSC niestandardowych przy użyciu klas programu PowerShell](/previous-versions//dn948461(v=technet.10)))</span><span class="sxs-lookup"><span data-stu-id="730c0-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](/previous-versions//dn948461(v=technet.10)))</span></span>

- <span data-ttu-id="730c0-137">Debugowanie zasobów DSC (zobacz [zasoby DSC debugowania](../troubleshooting/debugResource.md))</span><span class="sxs-lookup"><span data-stu-id="730c0-137">Debugging of DSC resources (see [Debugging DSC resources](../troubleshooting/debugResource.md))</span></span>

  <span data-ttu-id="730c0-138">**Problem:** Nie działa, jeśli zasób jest za pomocą PsDscRunAsCredential (zobacz [systemem DSC przy użyciu poświadczeń użytkownika](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="730c0-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](../configurations/runAsUser.md))</span></span>

- [<span data-ttu-id="730c0-139">Określanie zależności między węzłami</span><span class="sxs-lookup"><span data-stu-id="730c0-139">Specifying cross-node dependencies</span></span>](../configurations/crossNodeDependencies.md)

- [<span data-ttu-id="730c0-140">Przechowywanie wersji zasobu</span><span class="sxs-lookup"><span data-stu-id="730c0-140">Resource versioning</span></span>](../configurations/sxsResource.md)

- <span data-ttu-id="730c0-141">Klienta ściągania (konfiguracji i zasobów) (zobacz [Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji](../pull-server/pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="730c0-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](../pull-server/pullClientConfigNames.md))</span></span>

- [<span data-ttu-id="730c0-142">Konfiguracje częściowe (ściągania i wypychania)</span><span class="sxs-lookup"><span data-stu-id="730c0-142">Partial configurations (pull & push)</span></span>](../pull-server/partialConfigs.md)

- [<span data-ttu-id="730c0-143">Raportowanie do serwera ściągania</span><span class="sxs-lookup"><span data-stu-id="730c0-143">Reporting to pull server</span></span>](../pull-server/reportServer.md)

- <span data-ttu-id="730c0-144">Szyfrowanie pliku MOF</span><span class="sxs-lookup"><span data-stu-id="730c0-144">MOF encryption</span></span>

- <span data-ttu-id="730c0-145">Rejestrowanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="730c0-145">Event logging</span></span>

- <span data-ttu-id="730c0-146">Raporty usługi Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="730c0-146">Azure Automation DSC reporting</span></span>

- <span data-ttu-id="730c0-147">Zasoby, które są w pełni funkcjonalne</span><span class="sxs-lookup"><span data-stu-id="730c0-147">Resources that are fully functional</span></span>

- <span data-ttu-id="730c0-148">**Archiwizowanie**</span><span class="sxs-lookup"><span data-stu-id="730c0-148">**Archive**</span></span>
- <span data-ttu-id="730c0-149">**Środowisko**</span><span class="sxs-lookup"><span data-stu-id="730c0-149">**Environment**</span></span>
- <span data-ttu-id="730c0-150">**Plik**</span><span class="sxs-lookup"><span data-stu-id="730c0-150">**File**</span></span>
- <span data-ttu-id="730c0-151">**Dziennik**</span><span class="sxs-lookup"><span data-stu-id="730c0-151">**Log**</span></span>
- <span data-ttu-id="730c0-152">**ProcessSet**</span><span class="sxs-lookup"><span data-stu-id="730c0-152">**ProcessSet**</span></span>
- <span data-ttu-id="730c0-153">**Registry**</span><span class="sxs-lookup"><span data-stu-id="730c0-153">**Registry**</span></span>
- <span data-ttu-id="730c0-154">**Skrypt**</span><span class="sxs-lookup"><span data-stu-id="730c0-154">**Script**</span></span>
- <span data-ttu-id="730c0-155">**WindowsPackageCab**</span><span class="sxs-lookup"><span data-stu-id="730c0-155">**WindowsPackageCab**</span></span>
- <span data-ttu-id="730c0-156">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="730c0-156">**WindowsProcess**</span></span>
- <span data-ttu-id="730c0-157">**WaitForAll** (zobacz [określanie zależności między węzłami](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="730c0-157">**WaitForAll** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="730c0-158">**WaitForAny** (zobacz [określanie zależności między węzłami](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="730c0-158">**WaitForAny** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="730c0-159">**WaitForSome** (zobacz [określanie zależności między węzłami](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="730c0-159">**WaitForSome** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>

- <span data-ttu-id="730c0-160">Zasoby, które są częściowo funkcjonalności</span><span class="sxs-lookup"><span data-stu-id="730c0-160">Resources that are partially functional</span></span>
- <span data-ttu-id="730c0-161">**Grupa**</span><span class="sxs-lookup"><span data-stu-id="730c0-161">**Group**</span></span>
- <span data-ttu-id="730c0-162">**GroupSet**</span><span class="sxs-lookup"><span data-stu-id="730c0-162">**GroupSet**</span></span>

  <span data-ttu-id="730c0-163">**Problem:** Powyżej zasobów się niepowodzeniem, jeśli określone wystąpienie jest wywoływana dwa razy (uruchomione dwa razy tę samą konfigurację)</span><span class="sxs-lookup"><span data-stu-id="730c0-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

- <span data-ttu-id="730c0-164">**Usługa**</span><span class="sxs-lookup"><span data-stu-id="730c0-164">**Service**</span></span>
- <span data-ttu-id="730c0-165">**ServiceSet**</span><span class="sxs-lookup"><span data-stu-id="730c0-165">**ServiceSet**</span></span>

  <span data-ttu-id="730c0-166">**Problem:** Działa tylko w przypadku uruchamiania/zatrzymywania usługi (stan).</span><span class="sxs-lookup"><span data-stu-id="730c0-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="730c0-167">Kończy się niepowodzeniem, jeśli jeden próbuje zmienić inne atrybuty usługi, takie jak startuptype poświadczeń, opis itp.</span><span class="sxs-lookup"><span data-stu-id="730c0-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="730c0-168">Podobnie jak zostaje zgłoszony błąd:</span><span class="sxs-lookup"><span data-stu-id="730c0-168">The error thrown is similar to:</span></span>

  <span data-ttu-id="730c0-169">*Nie można odnaleźć typu [management.managementobject]: Sprawdź, czy zestaw zawierający ten typ jest ładowany.*</span><span class="sxs-lookup"><span data-stu-id="730c0-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>

- <span data-ttu-id="730c0-170">Zasoby, które nie działają</span><span class="sxs-lookup"><span data-stu-id="730c0-170">Resources that are not functional</span></span>
- <span data-ttu-id="730c0-171">**Użytkownik**</span><span class="sxs-lookup"><span data-stu-id="730c0-171">**User**</span></span>

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="730c0-172">Funkcji DSC nie są dostępne na serwerze Nano Server</span><span class="sxs-lookup"><span data-stu-id="730c0-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="730c0-173">Następujące funkcje DSC nie są obecnie dostępne na serwerze Nano Server:</span><span class="sxs-lookup"><span data-stu-id="730c0-173">The following DSC features are not currently available on Nano Server:</span></span>

- <span data-ttu-id="730c0-174">Odszyfrowywanie dokument MOF przy użyciu zaszyfrowane hasło</span><span class="sxs-lookup"><span data-stu-id="730c0-174">Decrypting MOF document with encrypted password(s)</span></span>
- <span data-ttu-id="730c0-175">Serwerze ściągania — nie można obecnie skonfigurować serwer ściągania na serwerze Nano Server</span><span class="sxs-lookup"><span data-stu-id="730c0-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
- <span data-ttu-id="730c0-176">Wszystko, co nie ma na liście prac funkcji</span><span class="sxs-lookup"><span data-stu-id="730c0-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="730c0-177">Korzystanie z niestandardowych zasobów DSC na serwerze Nano Server</span><span class="sxs-lookup"><span data-stu-id="730c0-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="730c0-178">Ze względu na ograniczone zestawy interfejsów API Windows i biblioteki CLR dostępne na serwerze Nano Server zasoby DSC, które działają na pełną wersję środowiska CLR programu Windows nie działać na serwerze Nano Server.</span><span class="sxs-lookup"><span data-stu-id="730c0-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="730c0-179">Ukończ testowanie end-to-end, przed wdrożeniem wszelkie niestandardowe zasoby DSC w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="730c0-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="730c0-180">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="730c0-180">See Also</span></span>

- [<span data-ttu-id="730c0-181">Wprowadzenie do systemu Nano Server</span><span class="sxs-lookup"><span data-stu-id="730c0-181">Getting Started with Nano Server</span></span>](/windows-server/get-started/getting-started-with-nano-server)
