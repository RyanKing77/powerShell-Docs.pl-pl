---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Konfigurowanie maszyny wirtualnej podczas początkowego rozruchu — za pomocą DSC
ms.openlocfilehash: f9634c330832e23fb2c6f08c5b299b55a5505ac9
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059426"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="1871a-103">Konfigurowanie maszyny wirtualnej podczas początkowego rozruchu — za pomocą DSC</span><span class="sxs-lookup"><span data-stu-id="1871a-103">Configure a virtual machines at initial boot-up by using DSC</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1871a-104">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1871a-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="requirements"></a><span data-ttu-id="1871a-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1871a-105">Requirements</span></span>

> [!NOTE]
> <span data-ttu-id="1871a-106">**DSCAutomationHostEnabled** klucz rejestru opisany w tym temacie nie jest dostępna w programie PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="1871a-106">The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span>
> <span data-ttu-id="1871a-107">Aby uzyskać informacje na temat konfigurowania nowych maszyn wirtualnych podczas początkowego rozruchu w programie PowerShell 4.0, zobacz [chcesz automatycznie skonfigurować swój maszyn za pomocą DSC podczas rozruchu początkowego?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span><span class="sxs-lookup"><span data-stu-id="1871a-107">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

<span data-ttu-id="1871a-108">Aby uruchomić te przykłady, są potrzebne:</span><span class="sxs-lookup"><span data-stu-id="1871a-108">To run these examples, you will need:</span></span>

- <span data-ttu-id="1871a-109">Rozruchowy wirtualny dysk twardy chcesz pracować.</span><span class="sxs-lookup"><span data-stu-id="1871a-109">A bootable VHD to work with.</span></span> <span data-ttu-id="1871a-110">Możesz pobrać obrazu ISO z kopię ewaluacyjną systemu Windows Server 2016 na [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="1871a-110">You can download an ISO with an evaluation copy of Windows Server 2016 at [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>
  <span data-ttu-id="1871a-111">Instrukcje można znaleźć na temat sposobu tworzenia dysku VHD z obrazu ISO w [tworzenie rozruchowych wirtualnych dysków twardych](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="1871a-111">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span></span>
- <span data-ttu-id="1871a-112">Komputer hosta, który ma włączoną funkcją Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="1871a-112">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="1871a-113">Aby uzyskać informacje, zobacz [omówienie funkcji Hyper-V](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="1871a-113">For information, see [Hyper-V overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span></span>

  <span data-ttu-id="1871a-114">Za pomocą DSC, możesz zautomatyzować instalację oprogramowania i konfiguracji na komputerze podczas początkowego rozruchu.</span><span class="sxs-lookup"><span data-stu-id="1871a-114">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span>
  <span data-ttu-id="1871a-115">Można to zrobić, należy albo wstrzykiwania dokument MOF konfiguracji lub metaconfiguration do nośnika rozruchowego (np. dysk VHD), dzięki czemu są uruchamiane podczas początkowego procesu rozruchu.</span><span class="sxs-lookup"><span data-stu-id="1871a-115">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span>
  <span data-ttu-id="1871a-116">To zachowanie jest określony przez [klucz rejestru DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) klucza rejestru w `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.</span><span class="sxs-lookup"><span data-stu-id="1871a-116">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.</span></span>
  <span data-ttu-id="1871a-117">Domyślnie wartość tego klucza jest 2, co pozwala DSC w czasie rozruchu.</span><span class="sxs-lookup"><span data-stu-id="1871a-117">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

  <span data-ttu-id="1871a-118">Jeśli użytkownik nie chce DSC w czasie rozruchu, ustaw wartość [klucz rejestru DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) klucz rejestru na 0.</span><span class="sxs-lookup"><span data-stu-id="1871a-118">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="1871a-119">Wstawić dokument MOF konfiguracji do wirtualnego dysku twardego</span><span class="sxs-lookup"><span data-stu-id="1871a-119">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="1871a-120">Wstrzyknięcie DSC metaconfiguration do wirtualnego dysku twardego</span><span class="sxs-lookup"><span data-stu-id="1871a-120">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="1871a-121">Wyłącz DSC w czasie rozruchu</span><span class="sxs-lookup"><span data-stu-id="1871a-121">Disable DSC at boot time</span></span>

> [!NOTE]
> <span data-ttu-id="1871a-122">Można wprowadzić zarówno `Pending.mof` i `MetaConfig.mof` do komputera, w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="1871a-122">You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
> <span data-ttu-id="1871a-123">Jeśli obecne są oba pliki, ustawienia określone w `MetaConfig.mof` wyższy priorytet.</span><span class="sxs-lookup"><span data-stu-id="1871a-123">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="1871a-124">Wstawić dokument MOF konfiguracji do wirtualnego dysku twardego</span><span class="sxs-lookup"><span data-stu-id="1871a-124">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="1871a-125">Wprowadzenie konfiguracji podczas początkowego rozruchu, można wstawić dokument MOF skompilowaną konfigurację do wirtualnego dysku twardego jako jego `Pending.mof` pliku.</span><span class="sxs-lookup"><span data-stu-id="1871a-125">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span>
<span data-ttu-id="1871a-126">Jeśli **DSCAutomationHostEnabled** klucz rejestru jest ustawiony na 2 (wartość domyślna), DSC zastosuje konfiguracją zdefiniowaną przez `Pending.mof` po rozruchu komputera dla po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="1871a-126">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="1871a-127">W tym przykładzie używamy następującej konfiguracji, co spowoduje zainstalowanie usług IIS na nowym komputerze:</span><span class="sxs-lookup"><span data-stu-id="1871a-127">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

```powershell
Configuration SampleIISInstall
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    node ('localhost')
    {
        WindowsFeature IIS
        {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
    }
}
```

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="1871a-128">Aby wstawić dokument MOF konfiguracji do wirtualnego dysku twardego</span><span class="sxs-lookup"><span data-stu-id="1871a-128">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="1871a-129">Zainstalować dysk VHD, do którego chcesz wstawić konfiguracji przez wywołanie metody [Instalowanie wirtualnego dysku twardego](/powershell/module/hyper-v/mount-vhd) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1871a-129">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="1871a-130">Przykład:</span><span class="sxs-lookup"><span data-stu-id="1871a-130">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="1871a-131">Na komputerze z uruchomionym PowerShell 5.0 lub nowszy, Zapisz konfigurację powyżej (**SampleIISInstall**) jako plik skryptu (ps1) programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1871a-131">On a computer running PowerShell 5.0 or later, save the above configuration (**SampleIISInstall**) as a PowerShell script (.ps1) file.</span></span>

3. <span data-ttu-id="1871a-132">W konsoli programu PowerShell przejdź do folderu, w którym został zapisany plik .ps1.</span><span class="sxs-lookup"><span data-stu-id="1871a-132">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

4. <span data-ttu-id="1871a-133">Uruchom następujące polecenia programu PowerShell, aby skompilować pliku MOF (Aby dowiedzieć się, jak kompilowanie konfiguracji DSC, zobacz [konfiguracje DSC](../configurations/configurations.md):</span><span class="sxs-lookup"><span data-stu-id="1871a-133">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. <span data-ttu-id="1871a-134">Spowoduje to utworzenie `localhost.mof` plik w nowym folderze o nazwie `SampleIISInstall`.</span><span class="sxs-lookup"><span data-stu-id="1871a-134">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span>
   <span data-ttu-id="1871a-135">Zmień nazwę, a następnie przenieść ten plik do właściwego położenia wirtualnego dysku twardego jako `Pending.mof` przy użyciu [Przenieś element](/powershell/module/microsoft.powershell.management/move-item) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1871a-135">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span> <span data-ttu-id="1871a-136">Przykład:</span><span class="sxs-lookup"><span data-stu-id="1871a-136">For example:</span></span>

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. <span data-ttu-id="1871a-137">Odinstaluj wirtualny dysk twardy, wywołując [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1871a-137">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="1871a-138">Przykład:</span><span class="sxs-lookup"><span data-stu-id="1871a-138">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. <span data-ttu-id="1871a-139">Tworzenie maszyny Wirtualnej przy użyciu dysku VHD, w którym zainstalowano dokument DSC MOF.</span><span class="sxs-lookup"><span data-stu-id="1871a-139">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="1871a-140">Po początkowej rozruchu i instalacji systemu operacyjnego zostaną zainstalowane usługi IIS.</span><span class="sxs-lookup"><span data-stu-id="1871a-140">After initial boot-up and operating system installation, IIS will be installed.</span></span>
<span data-ttu-id="1871a-141">Można to sprawdzić przez wywołanie metody [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1871a-141">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="1871a-142">Wstrzyknięcie DSC metaconfiguration do wirtualnego dysku twardego</span><span class="sxs-lookup"><span data-stu-id="1871a-142">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="1871a-143">Możesz również skonfigurować komputer w celu ściągania konfiguracji podczas początkowego rozruchu przez iniekcję metaconfiguration (zobacz [Konfigurowanie lokalnego Configuration Manager (LCM)](../managing-nodes/metaConfig.md)) do wirtualnego dysku twardego jako jego `MetaConfig.mof` pliku.</span><span class="sxs-lookup"><span data-stu-id="1871a-143">You can also configure a computer to pull a configuration at initial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span>
<span data-ttu-id="1871a-144">Jeśli **DSCAutomationHostEnabled** klucz rejestru jest ustawiony na 2 (wartość domyślna), DSC zastosuje metaconfiguration definicją `MetaConfig.mof` do LCM, gdy komputer uruchamia się potrzeby po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="1871a-144">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value),  DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span>
<span data-ttu-id="1871a-145">Jeśli metaconfiguration Określa, że LCM należy ściągnąć konfiguracji z serwera ściągania, komputer będzie podejmować próby ściągania konfiguracji z tego serwera ściągania podczas początkowego rozruchu.</span><span class="sxs-lookup"><span data-stu-id="1871a-145">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at initial boot-up.</span></span>
<span data-ttu-id="1871a-146">Aby uzyskać informacje o konfigurowaniu serwera ściągania DSC, zobacz [Konfigurowanie internetowego serwera ściągania DSC](../pull-server/pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="1871a-146">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](../pull-server/pullServer.md).</span></span>

<span data-ttu-id="1871a-147">W tym przykładzie użyjemy konfiguracji opisanych w poprzedniej sekcji (**SampleIISInstall**), a metaconfiguration następujące:</span><span class="sxs-lookup"><span data-stu-id="1871a-147">For this example, we will use both the configuration described in the previous section (**SampleIISInstall**), and the following metaconfiguration:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientBootstrap
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('SampleIISInstall')
        }
    }
}
```

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="1871a-148">Aby wstawić dokument MOF metaconfiguration do wirtualnego dysku twardego</span><span class="sxs-lookup"><span data-stu-id="1871a-148">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="1871a-149">Zainstalować dysk VHD, do którego chcesz wstawić metaconfiguration przez wywołanie metody [Instalowanie wirtualnego dysku twardego](/powershell/module/hyper-v/mount-vhd) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1871a-149">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="1871a-150">Przykład:</span><span class="sxs-lookup"><span data-stu-id="1871a-150">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="1871a-151">[Konfigurowanie internetowego serwera ściągania DSC](../pull-server/pullServer.md)i Zapisz **SampleIISInstall** konfiguracji do odpowiedniego folderu.</span><span class="sxs-lookup"><span data-stu-id="1871a-151">[Set up a DSC web pull server](../pull-server/pullServer.md), and save the **SampleIISInstall** configuration to the appropriate folder.</span></span>

3. <span data-ttu-id="1871a-152">Na komputerze z uruchomionym PowerShell 5.0 lub nowszy, Zapisz metaconfiguration powyżej (**PullClientBootstrap**) jako plik skryptu (ps1) programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1871a-152">On a computer running PowerShell 5.0 or later, save the above metaconfiguration (**PullClientBootstrap**) as a PowerShell script (.ps1) file.</span></span>

4. <span data-ttu-id="1871a-153">W konsoli programu PowerShell przejdź do folderu, w którym został zapisany plik .ps1.</span><span class="sxs-lookup"><span data-stu-id="1871a-153">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

5. <span data-ttu-id="1871a-154">Uruchom następujące polecenia programu PowerShell, aby skompilować dokument MOF metaconfiguration (Aby dowiedzieć się, jak kompilowanie konfiguracji DSC, zobacz [konfiguracje DSC](../configurations/configurations.md):</span><span class="sxs-lookup"><span data-stu-id="1871a-154">Run the following PowerShell commands to compile the  metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. <span data-ttu-id="1871a-155">Spowoduje to utworzenie `localhost.meta.mof` plik w nowym folderze o nazwie `PullClientBootstrap`.</span><span class="sxs-lookup"><span data-stu-id="1871a-155">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span>
   <span data-ttu-id="1871a-156">Zmień nazwę, a następnie przenieść ten plik do właściwego położenia wirtualnego dysku twardego jako `MetaConfig.mof` przy użyciu [Przenieś element](/powershell/module/microsoft.powershell.management/move-item) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1871a-156">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. <span data-ttu-id="1871a-157">Odinstaluj wirtualny dysk twardy, wywołując [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1871a-157">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="1871a-158">Przykład:</span><span class="sxs-lookup"><span data-stu-id="1871a-158">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. <span data-ttu-id="1871a-159">Tworzenie maszyny Wirtualnej przy użyciu dysku VHD, w którym zainstalowano dokument DSC MOF.</span><span class="sxs-lookup"><span data-stu-id="1871a-159">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="1871a-160">Po początkowej rozruchu i instalacji systemu operacyjnego DSC będzie pobierać konfiguracji z serwera ściągania i zostaną zainstalowane usługi IIS.</span><span class="sxs-lookup"><span data-stu-id="1871a-160">After initial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span>
<span data-ttu-id="1871a-161">Można to sprawdzić przez wywołanie metody [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1871a-161">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="1871a-162">Wyłącz DSC w czasie rozruchu</span><span class="sxs-lookup"><span data-stu-id="1871a-162">Disable DSC at boot time</span></span>

<span data-ttu-id="1871a-163">Domyślnie wartość `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled` klucza jest równa 2, co pozwala konfiguracji DSC do uruchomienia, jeśli komputer jest w stanie Oczekujące na zatwierdzenie lub bieżącego.</span><span class="sxs-lookup"><span data-stu-id="1871a-163">By default, the value of the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled` key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="1871a-164">Jeśli nie mają konfiguracji do uruchomienia podczas początkowego rozruchu, należy więc ustawić wartość tego klucza na 0:</span><span class="sxs-lookup"><span data-stu-id="1871a-164">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="1871a-165">Zainstalować dysk VHD, wywołując [Instalowanie wirtualnego dysku twardego](/powershell/module/hyper-v/mount-vhd) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1871a-165">Mount the VHD by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="1871a-166">Przykład:</span><span class="sxs-lookup"><span data-stu-id="1871a-166">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="1871a-167">Ładowanie rejestru `HKLM\Software` podkluczy z wirtualnego dysku twardego, wywołując `reg load`.</span><span class="sxs-lookup"><span data-stu-id="1871a-167">Load the registry `HKLM\Software` subkey from the VHD by calling `reg load`.</span></span>

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. <span data-ttu-id="1871a-168">Przejdź do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` przy użyciu dostawcy rejestru programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1871a-168">Navigate to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` by using the PowerShell Registry provider.</span></span>

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System`
   ```

4. <span data-ttu-id="1871a-169">Zmień wartość właściwości `DSCAutomationHostEnabled` na 0.</span><span class="sxs-lookup"><span data-stu-id="1871a-169">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. <span data-ttu-id="1871a-170">Zwolnij rejestru, uruchamiając następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="1871a-170">Unload the registry by running the following commands:</span></span>

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a><span data-ttu-id="1871a-171">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1871a-171">See Also</span></span>

[<span data-ttu-id="1871a-172">Konfiguracje DSC</span><span class="sxs-lookup"><span data-stu-id="1871a-172">DSC Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="1871a-173">Klucz rejestru DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="1871a-173">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)

[<span data-ttu-id="1871a-174">Konfigurowanie programu Local Configuration Manager (LCM)</span><span class="sxs-lookup"><span data-stu-id="1871a-174">Configuring the Local Configuration Manager (LCM)</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="1871a-175">Konfigurowanie internetowego serwera ściągania DSC</span><span class="sxs-lookup"><span data-stu-id="1871a-175">Setting up a DSC web pull server</span></span>](../pull-server/pullServer.md)
