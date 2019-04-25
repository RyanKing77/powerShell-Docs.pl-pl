---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Korzystanie z platformy DSC na serwerze Nano Server
ms.openlocfilehash: ac5eaf3885788f40e12e4f0a0f19025668280f7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079731"
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="116f7-103">Korzystanie z platformy DSC na serwerze Nano Server</span><span class="sxs-lookup"><span data-stu-id="116f7-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="116f7-104">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="116f7-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="116f7-105">**DSC na serwerze Nano Server** jest opcjonalny pakiet w `NanoServer\Packages` folderu nośników systemu Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="116f7-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="116f7-106">Po utworzeniu wirtualnego dysku twardego, określając dla serwera Nano Server można zainstalować pakietu **Microsoft-NanoServer-DSC-Package** jako wartość **pakietów** parametru **New-NanoServerImage**  funkcji.</span><span class="sxs-lookup"><span data-stu-id="116f7-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="116f7-107">Na przykład w przypadku tworzenia dysku VHD dla maszyny wirtualnej, polecenie będzie wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="116f7-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="116f7-108">Aby uzyskać informacje o instalowaniu i używaniu serwera Nano Server, a także jak zarządzać serwerem Nano Server przy użyciu komunikacji zdalnej programu PowerShell, zobacz [wprowadzenie Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span><span class="sxs-lookup"><span data-stu-id="116f7-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span></span>

## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="116f7-109">Funkcji DSC, które są dostępne na serwerze Nano Server</span><span class="sxs-lookup"><span data-stu-id="116f7-109">DSC features available on Nano Server</span></span>

<span data-ttu-id="116f7-110">Ponieważ serwer Nano Server obsługuje tylko ograniczony zestaw interfejsów API w porównaniu do pełnej wersji systemu Windows Server, DSC na serwerze Nano Server nie ma pełnych parzystość za pomocą DSC uruchomionych na pełne jednostki SKU dla przez pewien czas.</span><span class="sxs-lookup"><span data-stu-id="116f7-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="116f7-111">DSC na serwerze Nano Server jest aktywnie i nie jest jeszcze funkcji ukończone.</span><span class="sxs-lookup"><span data-stu-id="116f7-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

<span data-ttu-id="116f7-112">Następujące funkcje DSC są obecnie dostępne na serwerze Nano Server:</span><span class="sxs-lookup"><span data-stu-id="116f7-112">The following DSC features are currently available on Nano Server:</span></span>

<span data-ttu-id="116f7-113">Trybach wypychania i ściągania</span><span class="sxs-lookup"><span data-stu-id="116f7-113">Both push and pull modes</span></span>

- <span data-ttu-id="116f7-114">Wszystkie polecenia cmdlet DSC, które istnieją w pełnej wersji systemu Windows Server, w tym następujące:</span><span class="sxs-lookup"><span data-stu-id="116f7-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
- [<span data-ttu-id="116f7-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="116f7-115">Get-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [<span data-ttu-id="116f7-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="116f7-116">Set-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [<span data-ttu-id="116f7-117">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="116f7-117">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [<span data-ttu-id="116f7-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="116f7-118">Disable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [<span data-ttu-id="116f7-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="116f7-119">Start-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [<span data-ttu-id="116f7-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="116f7-120">Stop-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [<span data-ttu-id="116f7-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="116f7-121">Get-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [<span data-ttu-id="116f7-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="116f7-122">Test-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [<span data-ttu-id="116f7-123">Publish-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="116f7-123">Publish-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [<span data-ttu-id="116f7-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="116f7-124">Update-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [<span data-ttu-id="116f7-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="116f7-125">Restore-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [<span data-ttu-id="116f7-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="116f7-126">Remove-DscConfigurationDocument</span></span>](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [<span data-ttu-id="116f7-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="116f7-127">Get-DscConfigurationStatus</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [<span data-ttu-id="116f7-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="116f7-128">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [<span data-ttu-id="116f7-129">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="116f7-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
- [<span data-ttu-id="116f7-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="116f7-130">Get-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [<span data-ttu-id="116f7-131">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="116f7-131">New-DscChecksum</span></span>](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- <span data-ttu-id="116f7-132">Kompilowanie konfiguracji (zobacz [konfiguracje DSC](../configurations/configurations.md))</span><span class="sxs-lookup"><span data-stu-id="116f7-132">Compiling configurations (see [DSC configurations](../configurations/configurations.md))</span></span>

  <span data-ttu-id="116f7-133">**Problem:** Hasło szyfrowania (zobacz [Zabezpieczanie pliku MOF](../pull-server/secureMOF.md)) podczas konfiguracji kompilacji nie działa.</span><span class="sxs-lookup"><span data-stu-id="116f7-133">**Issue:** Password encryption (see [Securing the MOF File](../pull-server/secureMOF.md)) during configuration compilation doesn't work.</span></span>

- <span data-ttu-id="116f7-134">Kompilowanie metaconfigurations (zobacz [Konfigurowanie programu Local Configuration Manager](../managing-nodes/metaConfig.md))</span><span class="sxs-lookup"><span data-stu-id="116f7-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md))</span></span>

- <span data-ttu-id="116f7-135">Uruchamianie zasobami dostępnymi w ramach kontekstu użytkownika (zobacz [systemem DSC przy użyciu poświadczeń użytkownika (Uruchom jako)](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="116f7-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](../configurations/runAsUser.md))</span></span>

- <span data-ttu-id="116f7-136">Zasoby oparte na klasach (zobacz [pisanie zasobu DSC niestandardowych przy użyciu klas programu PowerShell](../resources/authoringResourceClass.md))</span><span class="sxs-lookup"><span data-stu-id="116f7-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](../resources/authoringResourceClass.md))</span></span>

- <span data-ttu-id="116f7-137">Debugowanie zasobów DSC (zobacz [zasoby DSC debugowania](../troubleshooting/debugResource.md))</span><span class="sxs-lookup"><span data-stu-id="116f7-137">Debugging of DSC resources (see [Debugging DSC resources](../troubleshooting/debugResource.md))</span></span>

  <span data-ttu-id="116f7-138">**Problem:** Nie działa, jeśli zasób jest za pomocą PsDscRunAsCredential (zobacz [systemem DSC przy użyciu poświadczeń użytkownika](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="116f7-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](../configurations/runAsUser.md))</span></span>

- [<span data-ttu-id="116f7-139">Określanie zależności między węzłami</span><span class="sxs-lookup"><span data-stu-id="116f7-139">Specifying cross-node dependencies</span></span>](../configurations/crossNodeDependencies.md)

- [<span data-ttu-id="116f7-140">Przechowywanie wersji zasobu</span><span class="sxs-lookup"><span data-stu-id="116f7-140">Resource versioning</span></span>](../configurations/sxsResource.md)

- <span data-ttu-id="116f7-141">Klienta ściągania (konfiguracji i zasobów) (zobacz [Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji](../pull-server/pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="116f7-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](../pull-server/pullClientConfigNames.md))</span></span>

- [<span data-ttu-id="116f7-142">Konfiguracje częściowe (ściągania i wypychania)</span><span class="sxs-lookup"><span data-stu-id="116f7-142">Partial configurations (pull & push)</span></span>](../pull-server/partialConfigs.md)

- [<span data-ttu-id="116f7-143">Raportowanie do serwera ściągania</span><span class="sxs-lookup"><span data-stu-id="116f7-143">Reporting to pull server</span></span>](../pull-server/reportServer.md)

- <span data-ttu-id="116f7-144">Szyfrowanie pliku MOF</span><span class="sxs-lookup"><span data-stu-id="116f7-144">MOF encryption</span></span>

- <span data-ttu-id="116f7-145">Rejestrowanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="116f7-145">Event logging</span></span>

- <span data-ttu-id="116f7-146">Raporty usługi Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="116f7-146">Azure Automation DSC reporting</span></span>

- <span data-ttu-id="116f7-147">Zasoby, które są w pełni funkcjonalne</span><span class="sxs-lookup"><span data-stu-id="116f7-147">Resources that are fully functional</span></span>

- <span data-ttu-id="116f7-148">**Archiwizowanie**</span><span class="sxs-lookup"><span data-stu-id="116f7-148">**Archive**</span></span>
- <span data-ttu-id="116f7-149">**Środowisko**</span><span class="sxs-lookup"><span data-stu-id="116f7-149">**Environment**</span></span>
- <span data-ttu-id="116f7-150">**Plik**</span><span class="sxs-lookup"><span data-stu-id="116f7-150">**File**</span></span>
- <span data-ttu-id="116f7-151">**Dziennik**</span><span class="sxs-lookup"><span data-stu-id="116f7-151">**Log**</span></span>
- <span data-ttu-id="116f7-152">**ProcessSet**</span><span class="sxs-lookup"><span data-stu-id="116f7-152">**ProcessSet**</span></span>
- <span data-ttu-id="116f7-153">**Registry**</span><span class="sxs-lookup"><span data-stu-id="116f7-153">**Registry**</span></span>
- <span data-ttu-id="116f7-154">**Skrypt**</span><span class="sxs-lookup"><span data-stu-id="116f7-154">**Script**</span></span>
- <span data-ttu-id="116f7-155">**WindowsPackageCab**</span><span class="sxs-lookup"><span data-stu-id="116f7-155">**WindowsPackageCab**</span></span>
- <span data-ttu-id="116f7-156">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="116f7-156">**WindowsProcess**</span></span>
- <span data-ttu-id="116f7-157">**WaitForAll** (zobacz [określanie zależności między węzłami](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="116f7-157">**WaitForAll** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="116f7-158">**WaitForAny** (zobacz [określanie zależności między węzłami](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="116f7-158">**WaitForAny** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="116f7-159">**WaitForSome** (zobacz [określanie zależności między węzłami](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="116f7-159">**WaitForSome** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>

- <span data-ttu-id="116f7-160">Zasoby, które są częściowo funkcjonalności</span><span class="sxs-lookup"><span data-stu-id="116f7-160">Resources that are partially functional</span></span>
- <span data-ttu-id="116f7-161">**Grupa**</span><span class="sxs-lookup"><span data-stu-id="116f7-161">**Group**</span></span>
- <span data-ttu-id="116f7-162">**GroupSet**</span><span class="sxs-lookup"><span data-stu-id="116f7-162">**GroupSet**</span></span>

  <span data-ttu-id="116f7-163">**Problem:** Powyżej zasobów się niepowodzeniem, jeśli określone wystąpienie jest wywoływana dwa razy (uruchomione dwa razy tę samą konfigurację)</span><span class="sxs-lookup"><span data-stu-id="116f7-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

- <span data-ttu-id="116f7-164">**Usługa**</span><span class="sxs-lookup"><span data-stu-id="116f7-164">**Service**</span></span>
- <span data-ttu-id="116f7-165">**ServiceSet**</span><span class="sxs-lookup"><span data-stu-id="116f7-165">**ServiceSet**</span></span>

  <span data-ttu-id="116f7-166">**Problem:** Działa tylko w przypadku uruchamiania/zatrzymywania usługi (stan).</span><span class="sxs-lookup"><span data-stu-id="116f7-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="116f7-167">Kończy się niepowodzeniem, jeśli jeden próbuje zmienić inne atrybuty usługi, takie jak startuptype poświadczeń, opis itp.</span><span class="sxs-lookup"><span data-stu-id="116f7-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="116f7-168">Podobnie jak zostaje zgłoszony błąd:</span><span class="sxs-lookup"><span data-stu-id="116f7-168">The error thrown is similar to:</span></span>

  <span data-ttu-id="116f7-169">*Nie można odnaleźć typu [management.managementobject]: Sprawdź, czy zestaw zawierający ten typ jest ładowany.*</span><span class="sxs-lookup"><span data-stu-id="116f7-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>

- <span data-ttu-id="116f7-170">Zasoby, które nie działają</span><span class="sxs-lookup"><span data-stu-id="116f7-170">Resources that are not functional</span></span>
- <span data-ttu-id="116f7-171">**Użytkownik**</span><span class="sxs-lookup"><span data-stu-id="116f7-171">**User**</span></span>

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="116f7-172">Funkcji DSC nie są dostępne na serwerze Nano Server</span><span class="sxs-lookup"><span data-stu-id="116f7-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="116f7-173">Następujące funkcje DSC nie są obecnie dostępne na serwerze Nano Server:</span><span class="sxs-lookup"><span data-stu-id="116f7-173">The following DSC features are not currently available on Nano Server:</span></span>

- <span data-ttu-id="116f7-174">Odszyfrowywanie dokument MOF przy użyciu zaszyfrowane hasło</span><span class="sxs-lookup"><span data-stu-id="116f7-174">Decrypting MOF document with encrypted password(s)</span></span>
- <span data-ttu-id="116f7-175">Serwerze ściągania — nie można obecnie skonfigurować serwer ściągania na serwerze Nano Server</span><span class="sxs-lookup"><span data-stu-id="116f7-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
- <span data-ttu-id="116f7-176">Wszystko, co nie ma na liście prac funkcji</span><span class="sxs-lookup"><span data-stu-id="116f7-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="116f7-177">Korzystanie z niestandardowych zasobów DSC na serwerze Nano Server</span><span class="sxs-lookup"><span data-stu-id="116f7-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="116f7-178">Ze względu na ograniczone zestawy interfejsów API Windows i biblioteki CLR dostępne na serwerze Nano Server zasoby DSC, które działają na pełną wersję środowiska CLR programu Windows nie działać na serwerze Nano Server.</span><span class="sxs-lookup"><span data-stu-id="116f7-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="116f7-179">Ukończ testowanie end-to-end, przed wdrożeniem wszelkie niestandardowe zasoby DSC w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="116f7-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="116f7-180">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="116f7-180">See Also</span></span>

- [<span data-ttu-id="116f7-181">Wprowadzenie do systemu Nano Server</span><span class="sxs-lookup"><span data-stu-id="116f7-181">Getting Started with Nano Server</span></span>](/windows-server/get-started/getting-started-with-nano-server)
