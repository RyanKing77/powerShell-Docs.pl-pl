---
ms.date: 07/10/2019
keywords: jea, PowerShell, zabezpieczenia
title: Rejestrowanie konfiguracji JEA
ms.openlocfilehash: c85eddea2196e4db4bbeea54bde11074f3d1c927
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017867"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="db2c5-103">Rejestrowanie konfiguracji JEA</span><span class="sxs-lookup"><span data-stu-id="db2c5-103">Registering JEA Configurations</span></span>

<span data-ttu-id="db2c5-104">Po utworzeniu [możliwości roli](role-capabilities.md) i [pliku konfiguracji sesji](session-configurations.md) , ostatnim krokiem jest zarejestrowanie punktu końcowego jea.</span><span class="sxs-lookup"><span data-stu-id="db2c5-104">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step is to register the JEA endpoint.</span></span> <span data-ttu-id="db2c5-105">Zarejestrowanie punktu końcowego JEA w systemie sprawia, że punkt końcowy jest dostępny do użycia przez użytkowników i aparaty automatyzacji.</span><span class="sxs-lookup"><span data-stu-id="db2c5-105">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="db2c5-106">Konfiguracja pojedynczego komputera</span><span class="sxs-lookup"><span data-stu-id="db2c5-106">Single machine configuration</span></span>

<span data-ttu-id="db2c5-107">W przypadku małych środowisk można wdrożyć JEA, rejestrując plik konfiguracji sesji za pomocą polecenia cmdlet [register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="db2c5-107">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="db2c5-108">Przed rozpoczęciem upewnij się, że zostały spełnione następujące wymagania wstępne:</span><span class="sxs-lookup"><span data-stu-id="db2c5-108">Before you begin, ensure that the following prerequisites have been met:</span></span>

- <span data-ttu-id="db2c5-109">Co najmniej jedna rola została utworzona i umieszczona w folderze **RoleCapabilities** modułu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="db2c5-109">One or more roles has been created and placed in the **RoleCapabilities** folder of a PowerShell module.</span></span>
- <span data-ttu-id="db2c5-110">Plik konfiguracji sesji został utworzony i przetestowany.</span><span class="sxs-lookup"><span data-stu-id="db2c5-110">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="db2c5-111">Użytkownik rejestrujący konfigurację JEA ma prawa administratora w systemie.</span><span class="sxs-lookup"><span data-stu-id="db2c5-111">The user registering the JEA configuration has administrator rights on the system.</span></span>
- <span data-ttu-id="db2c5-112">Wybrano nazwę punktu końcowego JEA.</span><span class="sxs-lookup"><span data-stu-id="db2c5-112">You've selected a name for your JEA endpoint.</span></span>

<span data-ttu-id="db2c5-113">Nazwa punktu końcowego JEA jest wymagana, gdy użytkownicy łączą się z systemem przy użyciu JEA.</span><span class="sxs-lookup"><span data-stu-id="db2c5-113">The name of the JEA endpoint is required when users connect to the system using JEA.</span></span> <span data-ttu-id="db2c5-114">Polecenie cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) wyświetla nazwy punktów końcowych w systemie.</span><span class="sxs-lookup"><span data-stu-id="db2c5-114">The [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet lists the names of the endpoints on a system.</span></span> <span data-ttu-id="db2c5-115">Punkty końcowe rozpoczynające `microsoft` się od są zwykle dostarczane z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="db2c5-115">Endpoints that start with `microsoft` are typically shipped with Windows.</span></span> <span data-ttu-id="db2c5-116">`microsoft.powershell` Punkt końcowy jest domyślnym punktem końcowym używanym podczas nawiązywania połączenia z punktem końcowym zdalnego programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="db2c5-116">The `microsoft.powershell` endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
Get-PSSessionConfiguration | Select-Object Name
```

```Output
Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="db2c5-117">Uruchom następujące polecenie, aby zarejestrować punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="db2c5-117">Run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="db2c5-118">Poprzednie polecenie ponownie uruchamia usługę WinRM w systemie.</span><span class="sxs-lookup"><span data-stu-id="db2c5-118">The previous command restarts the WinRM service on the system.</span></span> <span data-ttu-id="db2c5-119">Kończy wszystkie sesje komunikacji zdalnej programu PowerShell i wszystkie bieżące konfiguracje DSC.</span><span class="sxs-lookup"><span data-stu-id="db2c5-119">This terminates all PowerShell remoting sessions and any ongoing DSC configurations.</span></span> <span data-ttu-id="db2c5-120">Zaleca się przełączenie maszyn produkcyjnych do trybu offline przed uruchomieniem polecenia, aby uniknąć zakłócania operacji działania biznesowego.</span><span class="sxs-lookup"><span data-stu-id="db2c5-120">We recommended you take production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="db2c5-121">Po zarejestrowaniu możesz przystąpić do [korzystania z jea](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="db2c5-121">After registration, you're ready to [use JEA](using-jea.md).</span></span> <span data-ttu-id="db2c5-122">Plik konfiguracji sesji można usunąć w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="db2c5-122">You may delete the session configuration file at any time.</span></span> <span data-ttu-id="db2c5-123">Plik konfiguracji nie jest używany po rejestracji punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="db2c5-123">The configuration file isn't used after registration of the endpoint.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="db2c5-124">Konfiguracja wielomaszynowa z konfiguracją DSC</span><span class="sxs-lookup"><span data-stu-id="db2c5-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="db2c5-125">Podczas wdrażania JEA na wielu maszynach najprostszy model wdrażania używa zasobu [konfiguracji żądanego stanu (DSC)](/powershell/dsc/overview) jea, aby szybko i spójnie wdrożyć jea na każdym komputerze.</span><span class="sxs-lookup"><span data-stu-id="db2c5-125">When deploying JEA on multiple machines, the simplest deployment model uses the JEA [Desired State Configuration (DSC)](/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="db2c5-126">Aby wdrożyć JEA za pomocą DSC, upewnij się, że zostały spełnione następujące wymagania wstępne:</span><span class="sxs-lookup"><span data-stu-id="db2c5-126">To deploy JEA with DSC, ensure the following prerequisites are met:</span></span>

- <span data-ttu-id="db2c5-127">Co najmniej jedna możliwość roli została utworzona i dodana do modułu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="db2c5-127">One or more role capabilities have been authored and added to a PowerShell module.</span></span>
- <span data-ttu-id="db2c5-128">Moduł programu PowerShell zawierający role jest przechowywany w udziale plików (tylko do odczytu) dostępnym na poszczególnych komputerach.</span><span class="sxs-lookup"><span data-stu-id="db2c5-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="db2c5-129">Określono ustawienia konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="db2c5-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="db2c5-130">Nie musisz tworzyć pliku konfiguracji sesji podczas korzystania z zasobu JEA DSC.</span><span class="sxs-lookup"><span data-stu-id="db2c5-130">You don't need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="db2c5-131">Masz poświadczenia zezwalające na akcje administracyjne na każdej maszynie lub dostęp do serwera ściągania DSC używanego do zarządzania maszynami.</span><span class="sxs-lookup"><span data-stu-id="db2c5-131">You have credentials that allow administrative actions on each machine or access to the DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="db2c5-132">Pobrano [zasób jea DSC](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).</span><span class="sxs-lookup"><span data-stu-id="db2c5-132">You've downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).</span></span>

<span data-ttu-id="db2c5-133">Utwórz konfigurację DSC dla punktu końcowego JEA na maszynie docelowej lub serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="db2c5-133">Create a DSC configuration for your JEA endpoint on a target machine or pull server.</span></span> <span data-ttu-id="db2c5-134">W tej konfiguracji zasób **JustEnoughAdministration** DSC definiuje plik konfiguracji sesji, a zasób **pliku** kopiuje możliwości roli z udziału plików.</span><span class="sxs-lookup"><span data-stu-id="db2c5-134">In this configuration, the **JustEnoughAdministration** DSC resource defines the session configuration file and the **File** resource copies the role capabilities from the file share.</span></span>

<span data-ttu-id="db2c5-135">Następujące właściwości można skonfigurować przy użyciu zasobu DSC:</span><span class="sxs-lookup"><span data-stu-id="db2c5-135">The following properties are configurable using the DSC resource:</span></span>

- <span data-ttu-id="db2c5-136">Definicje ról</span><span class="sxs-lookup"><span data-stu-id="db2c5-136">Role Definitions</span></span>
- <span data-ttu-id="db2c5-137">Grupy kont wirtualnych</span><span class="sxs-lookup"><span data-stu-id="db2c5-137">Virtual account groups</span></span>
- <span data-ttu-id="db2c5-138">Nazwa konta usługi zarządzanego przez grupę</span><span class="sxs-lookup"><span data-stu-id="db2c5-138">Group-managed service account name</span></span>
- <span data-ttu-id="db2c5-139">Katalog transkrypcji</span><span class="sxs-lookup"><span data-stu-id="db2c5-139">Transcript directory</span></span>
- <span data-ttu-id="db2c5-140">Dysk użytkownika</span><span class="sxs-lookup"><span data-stu-id="db2c5-140">User drive</span></span>
- <span data-ttu-id="db2c5-141">Reguły dostępu warunkowego</span><span class="sxs-lookup"><span data-stu-id="db2c5-141">Conditional access rules</span></span>
- <span data-ttu-id="db2c5-142">Skrypty uruchamiania dla sesji JEA</span><span class="sxs-lookup"><span data-stu-id="db2c5-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="db2c5-143">Składnia dla każdej z tych właściwości w konfiguracji DSC jest zgodna z plikiem konfiguracji sesji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="db2c5-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="db2c5-144">Poniżej znajduje się Przykładowa konfiguracja DSC dla ogólnego modułu konserwacji serwera.</span><span class="sxs-lookup"><span data-stu-id="db2c5-144">Below is a sample DSC configuration for a general server maintenance module.</span></span> <span data-ttu-id="db2c5-145">Przyjęto założenie, że prawidłowy moduł programu PowerShell zawierający możliwości roli znajduje `\\myfileshare\JEA` się w udziale plików.</span><span class="sxs-lookup"><span data-stu-id="db2c5-145">It assumes that a valid PowerShell module containing role capabilities is located on the `\\myfileshare\JEA` file share.</span></span>

```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

<span data-ttu-id="db2c5-146">Następnie konfiguracja jest stosowana w systemie przez bezpośrednie wywołanie [Configuration Manager lokalnego](/powershell/dsc/managing-nodes/metaConfig) lub zaktualizowanie [konfiguracji serwera ściągania](/powershell/dsc/pull-server/pullServer).</span><span class="sxs-lookup"><span data-stu-id="db2c5-146">Next, the configuration is applied on a system by directly invoking the [Local Configuration Manager](/powershell/dsc/managing-nodes/metaConfig) or updating the [pull server configuration](/powershell/dsc/pull-server/pullServer).</span></span>

<span data-ttu-id="db2c5-147">Zasób DSC umożliwia również zastąpienie domyślnego punktu końcowego **programu Microsoft. PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="db2c5-147">The DSC resource also allows you to replace the default **Microsoft.PowerShell** endpoint.</span></span> <span data-ttu-id="db2c5-148">Po zastąpieniu zasób automatycznie rejestruje punkt końcowy kopii zapasowej o nazwie **Microsoft. PowerShell.** z ograniczeniami.</span><span class="sxs-lookup"><span data-stu-id="db2c5-148">When replaced, the resource automatically registers a backup endpoint named **Microsoft.PowerShell.Restricted**.</span></span> <span data-ttu-id="db2c5-149">Punkt końcowy kopii zapasowej ma domyślną listę ACL usługi WinRM umożliwiającą użytkownikom zdalnego zarządzania i członkom lokalnej grupy administratorów dostęp do niej.</span><span class="sxs-lookup"><span data-stu-id="db2c5-149">The backup endpoint has the default WinRM ACL that allows Remote Management Users and local Administrators group members to access it.</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="db2c5-150">Wyrejestrowywanie konfiguracji JEA</span><span class="sxs-lookup"><span data-stu-id="db2c5-150">Unregistering JEA configurations</span></span>

<span data-ttu-id="db2c5-151">Polecenie cmdlet [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) usuwa punkt końcowy jea.</span><span class="sxs-lookup"><span data-stu-id="db2c5-151">The [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet removes a JEA endpoint.</span></span> <span data-ttu-id="db2c5-152">Wyrejestrowanie punktu końcowego JEA uniemożliwia nowym użytkownikom tworzenie nowych sesji usługi JEA w systemie.</span><span class="sxs-lookup"><span data-stu-id="db2c5-152">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span> <span data-ttu-id="db2c5-153">Umożliwia również zaktualizowanie konfiguracji JEA przez ponowne zarejestrowanie zaktualizowanego pliku konfiguracji sesji przy użyciu tej samej nazwy punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="db2c5-153">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="db2c5-154">Wyrejestrowanie punktu końcowego JEA powoduje ponowne uruchomienie usługi WinRM.</span><span class="sxs-lookup"><span data-stu-id="db2c5-154">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span> <span data-ttu-id="db2c5-155">Spowoduje to przerwanie większości operacji zarządzania zdalnego w toku, w tym innych sesji programu PowerShell, wywołań usługi WMI i niektórych narzędzi do zarządzania.</span><span class="sxs-lookup"><span data-stu-id="db2c5-155">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span> <span data-ttu-id="db2c5-156">Wyrejestruj punkty końcowe programu PowerShell tylko podczas planowanych okien obsługi.</span><span class="sxs-lookup"><span data-stu-id="db2c5-156">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="db2c5-157">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="db2c5-157">Next steps</span></span>

[<span data-ttu-id="db2c5-158">Testowanie punktu końcowego JEA</span><span class="sxs-lookup"><span data-stu-id="db2c5-158">Test the JEA endpoint</span></span>](using-jea.md)
