---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Na serwerze Nano przy użyciu usługi Konfiguracja DSC"
ms.openlocfilehash: 7427d6bb7644f513b9b523f284109f5ae0f8ef27
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="0bdb8-103">Na serwerze Nano przy użyciu usługi Konfiguracja DSC</span><span class="sxs-lookup"><span data-stu-id="0bdb8-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="0bdb8-104">Dotyczy: Środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0bdb8-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="0bdb8-105">**DSC na serwerze Nano** jest opcjonalny pakiet w `NanoServer\Packages` folderu nośnika systemu Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="0bdb8-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="0bdb8-106">Pakiet można zainstalować podczas tworzenia dysku VHD dla Nano Server określając **Microsoft-NanoServer-DSC-Package** jako wartość **pakiety** parametr **NanoServerImage nowy**  funkcji.</span><span class="sxs-lookup"><span data-stu-id="0bdb8-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="0bdb8-107">Na przykład w przypadku tworzenia dysku VHD dla maszyny wirtualnej, polecenie będzie wyglądać podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="0bdb8-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="0bdb8-108">Aby uzyskać informacje o instalowaniu i używaniu Nano Server, a także sposobu zarządzania Nano Server z usługi zdalne środowiska PowerShell, zobacz [wprowadzenie Nano Server](https://technet.microsoft.com/en-us/library/mt126167.aspx).</span><span class="sxs-lookup"><span data-stu-id="0bdb8-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](https://technet.microsoft.com/en-us/library/mt126167.aspx).</span></span>


## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="0bdb8-109">Dostępne na serwerze Nano funkcje DSC</span><span class="sxs-lookup"><span data-stu-id="0bdb8-109">DSC features available on Nano Server</span></span>

 <span data-ttu-id="0bdb8-110">Ponieważ Nano Server obsługuje tylko ograniczony zestaw interfejsów API w porównaniu do pełnej wersji systemu Windows Server, usłudze Konfiguracja DSC systemem pełnej wersji produktu w chwili obecnej DSC na serwerze Nano nie ma pełnej funkcjonalności parzystości.</span><span class="sxs-lookup"><span data-stu-id="0bdb8-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="0bdb8-111">DSC na serwerze Nano trwa opracowywanie aktywne i nie jest jeszcze funkcja, pełny.</span><span class="sxs-lookup"><span data-stu-id="0bdb8-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>
 
 <span data-ttu-id="0bdb8-112">Następujące funkcje usługi Konfiguracja DSC są obecnie dostępne na serwerze Nano:</span><span class="sxs-lookup"><span data-stu-id="0bdb8-112">The following DSC features are currently available on Nano Server:</span></span> 


* <span data-ttu-id="0bdb8-113">Trybach wypychania i ściągania</span><span class="sxs-lookup"><span data-stu-id="0bdb8-113">Both push and pull modes</span></span>

* <span data-ttu-id="0bdb8-114">Wszystkie polecenia cmdlet DSC, które istnieją w pełnej wersji systemu Windows Server, w tym następujące:</span><span class="sxs-lookup"><span data-stu-id="0bdb8-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span> 
  * [<span data-ttu-id="0bdb8-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="0bdb8-115">Get-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/en-us/library/dn407378.aspx)
  * [<span data-ttu-id="0bdb8-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="0bdb8-116">Set-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/en-us/library/dn521621.aspx)   
  * [<span data-ttu-id="0bdb8-117">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="0bdb8-117">Enable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [<span data-ttu-id="0bdb8-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="0bdb8-118">Disable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517872.aspx)       
  * [<span data-ttu-id="0bdb8-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="0bdb8-119">Start-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [<span data-ttu-id="0bdb8-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="0bdb8-120">Stop-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [<span data-ttu-id="0bdb8-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="0bdb8-121">Get-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [<span data-ttu-id="0bdb8-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="0bdb8-122">Test-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407382.aspx)      
  * [<span data-ttu-id="0bdb8-123">Publish-DscConfiguraiton</span><span class="sxs-lookup"><span data-stu-id="0bdb8-123">Publish-DscConfiguraiton</span></span>](https://technet.microsoft.com/en-us/library/mt517875.aspx) 
  * [<span data-ttu-id="0bdb8-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="0bdb8-124">Update-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [<span data-ttu-id="0bdb8-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="0bdb8-125">Restore-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407383.aspx)
  * [<span data-ttu-id="0bdb8-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="0bdb8-126">Remove-DscConfigurationDocument</span></span>](https://technet.microsoft.com/en-us/library/mt143544.aspx)
  * [<span data-ttu-id="0bdb8-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="0bdb8-127">Get-DscConfigurationStatus</span></span>](https://technet.microsoft.com/en-us/library/mt517868.aspx)
  * [<span data-ttu-id="0bdb8-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="0bdb8-128">Invoke-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [<span data-ttu-id="0bdb8-129">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="0bdb8-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [<span data-ttu-id="0bdb8-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="0bdb8-130">Get-DscResource</span></span>](https://technet.microsoft.com/en-us/library/dn521625.aspx)
  * [<span data-ttu-id="0bdb8-131">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="0bdb8-131">New-DscChecksum</span></span>](https://technet.microsoft.com/en-us/library/dn521622.aspx)    

* <span data-ttu-id="0bdb8-132">Konfiguracje kompilacji (zobacz [konfiguracji DSC](configurations.md))</span><span class="sxs-lookup"><span data-stu-id="0bdb8-132">Compiling configurations (see [DSC configurations](configurations.md))</span></span>

  <span data-ttu-id="0bdb8-133">**Problem:** hasła szyfrowania (zobacz [Zabezpieczanie pliku MOF](securemof.md)) podczas konfigurowania kompilacji nie działa.</span><span class="sxs-lookup"><span data-stu-id="0bdb8-133">**Issue:** Password encryption (see [Securing the MOF File](securemof.md)) during configuration compilation doesn't work.</span></span>

* <span data-ttu-id="0bdb8-134">Kompilowanie metaconfigurations (zobacz [Konfigurowanie lokalny program Configuration Manager](metaConfig.md))</span><span class="sxs-lookup"><span data-stu-id="0bdb8-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](metaConfig.md))</span></span>

* <span data-ttu-id="0bdb8-135">Z zasobów w kontekście użytkownika (zobacz [DSC uruchomiony przy użyciu poświadczeń użytkownika (Uruchom jako)](runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="0bdb8-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](runAsUser.md))</span></span>

* <span data-ttu-id="0bdb8-136">Zasoby oparte na klasie (zobacz [pisania niestandardowego zasobu DSC środowiska PowerShell klasy](authoringResourceClass.md))</span><span class="sxs-lookup"><span data-stu-id="0bdb8-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](authoringResourceClass.md))</span></span>

* <span data-ttu-id="0bdb8-137">Debugowanie zasobów DSC (zobacz [zasobów debugowania DSC](debugresource.md))</span><span class="sxs-lookup"><span data-stu-id="0bdb8-137">Debugging of DSC resources (see [Debugging DSC resources](debugresource.md))</span></span>
  
  <span data-ttu-id="0bdb8-138">**Problem:** nie działa, jeśli zasób jest za pomocą PsDscRunAsCredential (zobacz [DSC uruchomiony przy użyciu poświadczeń użytkownika](runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="0bdb8-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](runAsUser.md))</span></span>

* [<span data-ttu-id="0bdb8-139">Określanie zależności między węzłami</span><span class="sxs-lookup"><span data-stu-id="0bdb8-139">Specifying cross-node dependencies</span></span>](crossNodeDependencies.md) 

* [<span data-ttu-id="0bdb8-140">Wersjonowanie zasobów</span><span class="sxs-lookup"><span data-stu-id="0bdb8-140">Resource versioning</span></span>](sxsResource.md)

* <span data-ttu-id="0bdb8-141">Klient ściągania (konfiguracje i zasobów) (zobacz [Konfigurowanie klienta ściągania przy użyciu nazwy konfiguracji](pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="0bdb8-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](pullClientConfigNames.md))</span></span>

* [<span data-ttu-id="0bdb8-142">Konfiguracje częściowe (ściągania i wypychania)</span><span class="sxs-lookup"><span data-stu-id="0bdb8-142">Partial configurations (pull & push)</span></span>](partialConfigs.md)

* [<span data-ttu-id="0bdb8-143">Raportowania na serwerze ściągania</span><span class="sxs-lookup"><span data-stu-id="0bdb8-143">Reporting to pull server</span></span>](reportServer.md) 

* <span data-ttu-id="0bdb8-144">Szyfrowanie MOF</span><span class="sxs-lookup"><span data-stu-id="0bdb8-144">MOF encryption</span></span>

* <span data-ttu-id="0bdb8-145">Rejestrowanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="0bdb8-145">Event logging</span></span>

* <span data-ttu-id="0bdb8-146">Raportowanie usługi Konfiguracja DSC automatyzacji Azure</span><span class="sxs-lookup"><span data-stu-id="0bdb8-146">Azure Automation DSC reporting</span></span>

* <span data-ttu-id="0bdb8-147">Zasoby, które są w pełni funkcjonalne</span><span class="sxs-lookup"><span data-stu-id="0bdb8-147">Resources that are fully functional</span></span>
  * [<span data-ttu-id="0bdb8-148">Archiwum</span><span class="sxs-lookup"><span data-stu-id="0bdb8-148">Archive</span></span>](archiveResource.md)
  * [<span data-ttu-id="0bdb8-149">Środowisko</span><span class="sxs-lookup"><span data-stu-id="0bdb8-149">Environment</span></span>](environmentResource.md)
  * [<span data-ttu-id="0bdb8-150">Plik</span><span class="sxs-lookup"><span data-stu-id="0bdb8-150">File</span></span>](fileResource.md)
  * [<span data-ttu-id="0bdb8-151">Dziennik</span><span class="sxs-lookup"><span data-stu-id="0bdb8-151">Log</span></span>](logResource.md)
  * <span data-ttu-id="0bdb8-152">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="0bdb8-152">ProcessSet</span></span>
  * [<span data-ttu-id="0bdb8-153">Registry</span><span class="sxs-lookup"><span data-stu-id="0bdb8-153">Registry</span></span>](registryResource.md)
  * [<span data-ttu-id="0bdb8-154">Skrypt</span><span class="sxs-lookup"><span data-stu-id="0bdb8-154">Script</span></span>](scriptResource.md)
  * <span data-ttu-id="0bdb8-155">WindowsPackageCab</span><span class="sxs-lookup"><span data-stu-id="0bdb8-155">WindowsPackageCab</span></span>
  * [<span data-ttu-id="0bdb8-156">WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="0bdb8-156">WindowsProcess</span></span>](windowsProcessResource.md)
  * <span data-ttu-id="0bdb8-157">WaitForAll (zobacz [określania zależności między węzłami](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="0bdb8-157">WaitForAll (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="0bdb8-158">WaitForAny (zobacz [określania zależności między węzłami](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="0bdb8-158">WaitForAny (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="0bdb8-159">WaitForSome (zobacz [określania zależności między węzłami](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="0bdb8-159">WaitForSome (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>

* <span data-ttu-id="0bdb8-160">Zasoby, które działają częściowo</span><span class="sxs-lookup"><span data-stu-id="0bdb8-160">Resources that are partially functional</span></span>
  * [<span data-ttu-id="0bdb8-161">Grupa</span><span class="sxs-lookup"><span data-stu-id="0bdb8-161">Group</span></span>](groupResource.md)
  * <span data-ttu-id="0bdb8-162">GroupSet</span><span class="sxs-lookup"><span data-stu-id="0bdb8-162">GroupSet</span></span>
  
  <span data-ttu-id="0bdb8-163">**Problem:** powyżej zasobów się niepowodzeniem, jeśli określone wystąpienie jest wywoływana dwukrotnie (uruchomiony dwukrotnie tę samą konfigurację)</span><span class="sxs-lookup"><span data-stu-id="0bdb8-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>
  
  * [<span data-ttu-id="0bdb8-164">Usługi</span><span class="sxs-lookup"><span data-stu-id="0bdb8-164">Service</span></span>](serviceResource.md)
  * <span data-ttu-id="0bdb8-165">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="0bdb8-165">ServiceSet</span></span>
  
  <span data-ttu-id="0bdb8-166">**Problem:** działa tylko w przypadku uruchamiania/zatrzymywania usługi (stan).</span><span class="sxs-lookup"><span data-stu-id="0bdb8-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="0bdb8-167">Kończy się niepowodzeniem, jeśli jeden próbuje zmienić innych atrybutów usługi, takich jak startuptype, poświadczenia, opis itp.</span><span class="sxs-lookup"><span data-stu-id="0bdb8-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="0bdb8-168">Zgłoszono błąd jest podobny do:</span><span class="sxs-lookup"><span data-stu-id="0bdb8-168">The error thrown is similar to:</span></span>
  
  <span data-ttu-id="0bdb8-169">*Nie można odnaleźć typu [management.managementobject]: Sprawdź, czy zestaw zawierający ten typ jest załadowany.*</span><span class="sxs-lookup"><span data-stu-id="0bdb8-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>
  
* <span data-ttu-id="0bdb8-170">Zasoby, które nie działają</span><span class="sxs-lookup"><span data-stu-id="0bdb8-170">Resources that are not functional</span></span>
  * [<span data-ttu-id="0bdb8-171">Użytkownika</span><span class="sxs-lookup"><span data-stu-id="0bdb8-171">User</span></span>](userResource.md)
  

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="0bdb8-172">Nie jest dostępny na serwerze Nano funkcje DSC</span><span class="sxs-lookup"><span data-stu-id="0bdb8-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="0bdb8-173">Następujące funkcje usługi Konfiguracja DSC nie są obecnie dostępne na serwerze Nano:</span><span class="sxs-lookup"><span data-stu-id="0bdb8-173">The following DSC features are not currently available on Nano Server:</span></span>

* <span data-ttu-id="0bdb8-174">Odszyfrowywanie MOF dokument z zaszyfrowane hasło</span><span class="sxs-lookup"><span data-stu-id="0bdb8-174">Decrypting MOF document with encrypted password(s)</span></span> 
* <span data-ttu-id="0bdb8-175">Serwerem ściągania — nie można obecnie skonfigurować serwera ściągania, na serwerze Nano</span><span class="sxs-lookup"><span data-stu-id="0bdb8-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
* <span data-ttu-id="0bdb8-176">Wszystko, co nie jest na liście działania funkcji</span><span class="sxs-lookup"><span data-stu-id="0bdb8-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="0bdb8-177">Na serwerze Nano przy użyciu niestandardowych zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="0bdb8-177">Using custom DSC resources on Nano Server</span></span>
 
<span data-ttu-id="0bdb8-178">Z powodu ograniczonej zestawów interfejsów API systemu Windows i bibliotek CLR dostępne na serwerze Nano DSC zasoby, które działają w pełnej wersji środowiska CLR systemu Windows nie działać na serwerze Nano.</span><span class="sxs-lookup"><span data-stu-id="0bdb8-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span> <span data-ttu-id="0bdb8-179">Ukończ testowanie end-to-end przed wdrożeniem wszystkich zasobów niestandardowych DSC w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="0bdb8-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="0bdb8-180">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0bdb8-180">See Also</span></span>
- [<span data-ttu-id="0bdb8-181">Wprowadzenie do korzystania z Nano Server</span><span class="sxs-lookup"><span data-stu-id="0bdb8-181">Getting Started with Nano Server</span></span>](https://technet.microsoft.com/en-us/library/mt126167.aspx)

