---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Konfigurowanie maszyn wirtualnych na początkowego rozruchu w górę przy użyciu usługi Konfiguracja DSC
ms.openlocfilehash: e6ff83b9a09f93277904c80e8e52f3db5e818739
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
><span data-ttu-id="49818-103">Dotyczy: Środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="49818-103">Applies To: Windows PowerShell 5.0</span></span>

><span data-ttu-id="49818-104">**Uwaga:** **DSCAutomationHostEnabled** klucz rejestru opisany w tym temacie nie jest dostępna w programie PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="49818-104">**Note:** The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span>
<span data-ttu-id="49818-105">Aby uzyskać informacje na temat konfigurowania nowych maszyn wirtualnych w początkowej up rozruchu w środowisku PowerShell w wersji 4.0, zobacz [chcesz automatycznie skonfigurować swój maszyny przy użyciu usługi Konfiguracja DSC w początkowego rozruchu w górę?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span><span class="sxs-lookup"><span data-stu-id="49818-105">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="49818-106">Konfigurowanie maszyn wirtualnych na początkowego rozruchu w górę przy użyciu usługi Konfiguracja DSC</span><span class="sxs-lookup"><span data-stu-id="49818-106">Configure a virtual machines at initial boot-up by using DSC</span></span>

## <a name="requirements"></a><span data-ttu-id="49818-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="49818-107">Requirements</span></span>

<span data-ttu-id="49818-108">Aby uruchomić te przykłady, będą potrzebne:</span><span class="sxs-lookup"><span data-stu-id="49818-108">To run these examples, you will need:</span></span>

- <span data-ttu-id="49818-109">Rozruchowy dysk VHD do pracy z.</span><span class="sxs-lookup"><span data-stu-id="49818-109">A bootable VHD to work with.</span></span> <span data-ttu-id="49818-110">Możesz pobrać plik ISO z wersję ewaluacyjną programu Windows Server 2016 na [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="49818-110">You can download an ISO with an evaluation copy of Windows Server 2016 at [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016).</span></span> <span data-ttu-id="49818-111">Instrukcje można znaleźć na temat tworzenia dysku VHD z obrazu ISO w [tworzenie rozruchowych wirtualnych dysków twardych](https://technet.microsoft.com/library/gg318049.aspx).</span><span class="sxs-lookup"><span data-stu-id="49818-111">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](https://technet.microsoft.com/library/gg318049.aspx).</span></span>
- <span data-ttu-id="49818-112">Komputer hosta, który ma włączoną funkcją Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="49818-112">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="49818-113">Aby uzyskać informacje, zobacz [omówienie funkcji Hyper-V](https://technet.microsoft.com/library/hh831531.aspx).</span><span class="sxs-lookup"><span data-stu-id="49818-113">For information, see [Hyper-V overview](https://technet.microsoft.com/library/hh831531.aspx).</span></span>

<span data-ttu-id="49818-114">Przy użyciu usługi Konfiguracja DSC, można zautomatyzować instalację oprogramowania i konfiguracji na komputerze w początkowej rozruchu w górę.</span><span class="sxs-lookup"><span data-stu-id="49818-114">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span>
<span data-ttu-id="49818-115">W tym celu albo wstrzykiwania metakonfigurację lub dokumentu MOF konfiguracji do nośnika rozruchowego (np. dysk VHD), dzięki czemu są one uruchamiane podczas początkowego procesu rozruchu w górę.</span><span class="sxs-lookup"><span data-stu-id="49818-115">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span>
<span data-ttu-id="49818-116">To zachowanie jest określona przez [klucza rejestru DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) klucza rejestru w kluczu **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies**.</span><span class="sxs-lookup"><span data-stu-id="49818-116">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies**.</span></span>
<span data-ttu-id="49818-117">Domyślnie wartość tego klucza jest 2, dzięki czemu DSC w czasie rozruchu.</span><span class="sxs-lookup"><span data-stu-id="49818-117">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

<span data-ttu-id="49818-118">Jeśli nie chcesz, aby DSC w czasie rozruchu, ustaw wartość [klucza rejestru DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) klucza rejestru na 0.</span><span class="sxs-lookup"><span data-stu-id="49818-118">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="49818-119">Wstaw dokument MOF konfiguracji do dysku VHD</span><span class="sxs-lookup"><span data-stu-id="49818-119">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="49818-120">Wstaw metakonfigurację DSC do dysku VHD</span><span class="sxs-lookup"><span data-stu-id="49818-120">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="49818-121">Wyłącz usługi Konfiguracja DSC w czasie rozruchu</span><span class="sxs-lookup"><span data-stu-id="49818-121">Disable DSC at boot time</span></span>

><span data-ttu-id="49818-122">**Uwaga:** można wprowadzić obu `Pending.mof` i `MetaConfig.mof` do komputera, w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="49818-122">**Note:** You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
<span data-ttu-id="49818-123">Jeśli oba pliki są obecne, ustawienia określone w `MetaConfig.mof` pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="49818-123">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="49818-124">Wstaw dokument MOF konfiguracji do dysku VHD</span><span class="sxs-lookup"><span data-stu-id="49818-124">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="49818-125">Wprowadzenie konfiguracji w początkowej rozruchu w górę, można wstrzyknąć dokumentu MOF skompilowanych konfiguracji do wirtualnego dysku twardego jako jego `Pending.mof` pliku.</span><span class="sxs-lookup"><span data-stu-id="49818-125">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span>
<span data-ttu-id="49818-126">Jeśli **DSCAutomationHostEnabled** klucz rejestru jest ustawiona na 2 (wartość domyślna), DSC zostaną zastosowane konfiguracji zdefiniowanej `Pending.mof` gdy komputer jest uruchamiany dla po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="49818-126">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="49818-127">W tym przykładzie używamy następującej konfiguracji, co spowoduje zainstalowanie usług IIS na nowym komputerze:</span><span class="sxs-lookup"><span data-stu-id="49818-127">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

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

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="49818-128">Aby wstawić dokument MOF konfiguracji na dysku VHD</span><span class="sxs-lookup"><span data-stu-id="49818-128">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="49818-129">Zainstalowanie dysku VHD, do którego chcesz wstrzyknąć konfiguracji przez wywołanie metody [Instalowanie wirtualnego dysku twardego](https://technet.microsoft.com/library/hh848551.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="49818-129">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span></span> <span data-ttu-id="49818-130">Przykład:</span><span class="sxs-lookup"><span data-stu-id="49818-130">For example:</span></span>

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```
2. <span data-ttu-id="49818-131">Na komputerze z uruchomionym programu PowerShell w wersji 5.0 lub nowszy, Zapisz powyższej konfiguracji (**SampleIISInstall**) jako pliku skryptu (ps1) programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49818-131">On a computer running PowerShell 5.0 or later, save the above configuration (**SampleIISInstall**) as a PowerShell script (.ps1) file.</span></span>

3. <span data-ttu-id="49818-132">W konsoli programu PowerShell przejdź do folderu, w której zapisano plik .ps1.</span><span class="sxs-lookup"><span data-stu-id="49818-132">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

4. <span data-ttu-id="49818-133">Uruchom następujące polecenia programu PowerShell, aby skompilować pliku MOF (informacje o kompilacji konfiguracji DSC znajdują się w temacie [konfiguracji DSC](configurations.md):</span><span class="sxs-lookup"><span data-stu-id="49818-133">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](configurations.md):</span></span>

    ```powershell
    . .\SampleIISInstall.ps1
    SampleIISInstall
    ```

5. <span data-ttu-id="49818-134">Spowoduje to utworzenie `localhost.mof` plik w nowym folderze o nazwie `SampleIISInstall`.</span><span class="sxs-lookup"><span data-stu-id="49818-134">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span>
<span data-ttu-id="49818-135">Zmień nazwę i przenieść ten plik do właściwego położenia na wirtualny dysk twardy jako `Pending.mof` za pomocą [Przenieś element](https://technet.microsoft.comlibrary/hh849852.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="49818-135">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span></span> <span data-ttu-id="49818-136">Przykład:</span><span class="sxs-lookup"><span data-stu-id="49818-136">For example:</span></span>

    ```powershell
        Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
    ```
6. <span data-ttu-id="49818-137">Odinstalować dysku VHD, wywołując [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="49818-137">Dismount the VHD by calling the [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet.</span></span> <span data-ttu-id="49818-138">Przykład:</span><span class="sxs-lookup"><span data-stu-id="49818-138">For example:</span></span>

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

7. <span data-ttu-id="49818-139">Utwórz maszynę Wirtualną przy użyciu dysku VHD, w którym zainstalowano pliku MOF usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="49818-139">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>
<span data-ttu-id="49818-140">Po początkowe up rozruchu i instalacji systemu operacyjnego zostaną zainstalowane usługi IIS.</span><span class="sxs-lookup"><span data-stu-id="49818-140">After intial boot-up and operating system installation, IIS will be installed.</span></span>
<span data-ttu-id="49818-141">Można to sprawdzić, wywołując [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="49818-141">You can verify this by calling the [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="49818-142">Wstaw metakonfigurację DSC do dysku VHD</span><span class="sxs-lookup"><span data-stu-id="49818-142">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="49818-143">Można również skonfigurować komputer w celu ściągania konfiguracji na początkowe up rozruchu przez wstrzykiwanie metakonfigurację (zobacz [Konfigurowanie lokalnego Menedżera konfiguracji (LCM)](metaConfig.md)) do wirtualnego dysku twardego jako jego `MetaConfig.mof` pliku.</span><span class="sxs-lookup"><span data-stu-id="49818-143">You can also configure a computer to pull a configuration at intial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span>
<span data-ttu-id="49818-144">Jeśli **DSCAutomationHostEnabled** klucz rejestru jest ustawiona na 2 (wartość domyślna), DSC zostaną zastosowane metakonfigurację zdefiniowane przez `MetaConfig.mof` do LCM, gdy komputer jest uruchamiany dla po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="49818-144">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value),  DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span>
<span data-ttu-id="49818-145">Jeśli metakonfigurację Określa, że LCM powinien pobierać konfiguracji z serwera ściągania, komputer podejmie próbę ściągania konfiguracji z tego serwera ściągania w początkowej rozruchu w górę.</span><span class="sxs-lookup"><span data-stu-id="49818-145">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at inital boot-up.</span></span>
<span data-ttu-id="49818-146">Aby uzyskać informacje dotyczące konfigurowania serwera ściągania usługi Konfiguracja DSC, zobacz [ustawienie serwera ściągania usługi Konfiguracja DSC sieci web](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="49818-146">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](pullServer.md).</span></span>

<span data-ttu-id="49818-147">W tym przykładzie używamy konfiguracji opisanych w poprzedniej sekcji (**SampleIISInstall**), a metakonfigurację następujące:</span><span class="sxs-lookup"><span data-stu-id="49818-147">For this example, we will use both the configuration described in the previous section (**SampleIISInstall**), and the following metaconfiguration:</span></span>

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

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="49818-148">Można wstawić dokument MOF metakonfigurację na wirtualny dysk twardy</span><span class="sxs-lookup"><span data-stu-id="49818-148">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="49818-149">Zainstalowanie dysku VHD, do którego chcesz wstrzyknąć metakonfigurację przez wywołanie metody [Instalowanie wirtualnego dysku twardego](https://technet.microsoft.com/library/hh848551.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="49818-149">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span></span> <span data-ttu-id="49818-150">Przykład:</span><span class="sxs-lookup"><span data-stu-id="49818-150">For example:</span></span>

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. <span data-ttu-id="49818-151">[Konfigurowanie serwera ściągania usługi Konfiguracja DSC](pullServer.md)i Zapisz **SampleIISInistall** konfiguracji do odpowiedniego folderu.</span><span class="sxs-lookup"><span data-stu-id="49818-151">[Set up a DSC web pull server](pullServer.md), and save the **SampleIISInistall** configuration to the appropriate folder.</span></span>

3. <span data-ttu-id="49818-152">Na komputerze z uruchomionym programu PowerShell w wersji 5.0 lub później, Zapisz powyżej metakonfigurację (**PullClientBootstrap**) jako pliku skryptu (ps1) programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49818-152">On a computer running PowerShell 5.0 or later, save the above metaconfiguration (**PullClientBootstrap**) as a PowerShell script (.ps1) file.</span></span>

4. <span data-ttu-id="49818-153">W konsoli programu PowerShell przejdź do folderu, w której zapisano plik .ps1.</span><span class="sxs-lookup"><span data-stu-id="49818-153">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

5. <span data-ttu-id="49818-154">Uruchom następujące polecenia programu PowerShell, aby skompilować pliku MOF metakonfigurację (informacje o kompilacji konfiguracji DSC znajdują się w temacie [konfiguracji DSC](configurations.md):</span><span class="sxs-lookup"><span data-stu-id="49818-154">Run the following PowerShell commands to compile the  metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](configurations.md):</span></span>

    ```powershell
    . .\PullClientBootstrap.ps1
    PullClientBootstrap
    ```

6. <span data-ttu-id="49818-155">Spowoduje to utworzenie `localhost.meta.mof` plik w nowym folderze o nazwie `PullClientBootstrap`.</span><span class="sxs-lookup"><span data-stu-id="49818-155">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span>
<span data-ttu-id="49818-156">Zmień nazwę i przenieść ten plik do właściwego położenia na wirtualny dysk twardy jako `MetaConfig.mof` za pomocą [Przenieś element](https://technet.microsoft.comlibrary/hh849852.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="49818-156">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.</span></span>

    ```powershell
    Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\Sytem32\Configuration\MetaConfig.mof
    ```

7. <span data-ttu-id="49818-157">Odinstalować dysku VHD, wywołując [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="49818-157">Dismount the VHD by calling the [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet.</span></span> <span data-ttu-id="49818-158">Przykład:</span><span class="sxs-lookup"><span data-stu-id="49818-158">For example:</span></span>

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

8. <span data-ttu-id="49818-159">Utwórz maszynę Wirtualną przy użyciu dysku VHD, w którym zainstalowano pliku MOF usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="49818-159">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>
<span data-ttu-id="49818-160">Po początkowe up rozruchu i instalacji systemu operacyjnego DSC będzie pobierać konfiguracji z serwera ściągania i będzie można zainstalować usług IIS.</span><span class="sxs-lookup"><span data-stu-id="49818-160">After intial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span>
<span data-ttu-id="49818-161">Można to sprawdzić, wywołując [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="49818-161">You can verify this by calling the [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="49818-162">Wyłącz usługi Konfiguracja DSC w czasie rozruchu</span><span class="sxs-lookup"><span data-stu-id="49818-162">Disable DSC at boot time</span></span>

<span data-ttu-id="49818-163">Domyślnie wartość **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled** klucza wynosi 2, dzięki czemu konfiguracji DSC do uruchomienia, jeśli komputer znajduje się w oczekujące lub bieżącego Stan.</span><span class="sxs-lookup"><span data-stu-id="49818-163">By default, the value of the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled** key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="49818-164">Jeśli nie chcesz, aby konfiguracji, aby były uruchamiane po początkowej rozruchu w górę, należy więc ustaw wartość tego klucza na 0:</span><span class="sxs-lookup"><span data-stu-id="49818-164">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="49818-165">Zainstalować dysk VHD, wywołując [Instalowanie wirtualnego dysku twardego](https://technet.microsoft.com/library/hh848551.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="49818-165">Mount the VHD by calling the [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet.</span></span> <span data-ttu-id="49818-166">Przykład:</span><span class="sxs-lookup"><span data-stu-id="49818-166">For example:</span></span>

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. <span data-ttu-id="49818-167">Załadować rejestru **kluczu HKLM\Software** podkluczy z wirtualnego dysku twardego, wywołując `reg load`.</span><span class="sxs-lookup"><span data-stu-id="49818-167">Load the registry **HKLM\Software** subkey from the VHD by calling `reg load`.</span></span>

    ```
    reg load HKLM\Vhd E:\Windows\System32\Config\Software`
    ```

3. <span data-ttu-id="49818-168">Przejdź do **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\***  przy użyciu dostawcy rejestru programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49818-168">Navigate to the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*** by using the PowerShell Registry provider.</span></span>

    ```powershell
    Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
    ```

4. <span data-ttu-id="49818-169">Zmień wartość `DSCAutomationHostEnabled` na 0.</span><span class="sxs-lookup"><span data-stu-id="49818-169">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

    ```powershell
    Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
    ```

5. <span data-ttu-id="49818-170">Zwolnienia rejestru, uruchamiając następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="49818-170">Unload the registry by running the following commands:</span></span>

    ```powershell
    [gc]::Collect()
    reg unload HKLM\Vhd
    ```

## <a name="see-also"></a><span data-ttu-id="49818-171">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="49818-171">See Also</span></span>

- [<span data-ttu-id="49818-172">Konfiguracji DSC</span><span class="sxs-lookup"><span data-stu-id="49818-172">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="49818-173">Klucz rejestru DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="49818-173">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)
- [<span data-ttu-id="49818-174">Konfigurowanie programu Local Configuration Manager (LCM)</span><span class="sxs-lookup"><span data-stu-id="49818-174">Configuring the Local Configuration Manager (LCM)</span></span>](metaConfig.md)
- [<span data-ttu-id="49818-175">Konfigurowanie serwera ściągania usługi Konfiguracja DSC sieci web</span><span class="sxs-lookup"><span data-stu-id="49818-175">Setting up a DSC web pull server</span></span>](pullServer.md)