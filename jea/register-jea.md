---
ms.date: 07/10/2019
keywords: jea, programu powershell, zabezpieczeń
title: Rejestrowanie usługi JEA konfiguracji
ms.openlocfilehash: c85eddea2196e4db4bbeea54bde11074f3d1c927
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726600"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="e8885-103">Rejestrowanie usługi JEA konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e8885-103">Registering JEA Configurations</span></span>

<span data-ttu-id="e8885-104">Po utworzeniu usługi [możliwości roli](role-capabilities.md) i [plik konfiguracji sesji](session-configurations.md) ostatnim krokiem jest utworzone, można zarejestrować punktu końcowego JEA.</span><span class="sxs-lookup"><span data-stu-id="e8885-104">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step is to register the JEA endpoint.</span></span> <span data-ttu-id="e8885-105">Rejestrowanie punktu końcowego JEA w systemie sprawia, że punkt końcowy do użycia przez użytkowników i aparatów automatyzacji.</span><span class="sxs-lookup"><span data-stu-id="e8885-105">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="e8885-106">Konfiguracja pojedynczego komputera</span><span class="sxs-lookup"><span data-stu-id="e8885-106">Single machine configuration</span></span>

<span data-ttu-id="e8885-107">W przypadku małych środowisk można wdrożyć JEA, rejestrując się, używając pliku konfiguracji sesji [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e8885-107">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="e8885-108">Przed rozpoczęciem upewnij się, że zostały spełnione następujące wymagania wstępne:</span><span class="sxs-lookup"><span data-stu-id="e8885-108">Before you begin, ensure that the following prerequisites have been met:</span></span>

- <span data-ttu-id="e8885-109">Utworzono i umieszczane w co najmniej jedną rolę **RoleCapabilities** folderu modułu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8885-109">One or more roles has been created and placed in the **RoleCapabilities** folder of a PowerShell module.</span></span>
- <span data-ttu-id="e8885-110">Utworzono plik konfiguracji sesji i przetestowane.</span><span class="sxs-lookup"><span data-stu-id="e8885-110">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="e8885-111">Użytkownik, o których rejestrowanie usługi JEA konfiguracji ma prawa administratora w systemie.</span><span class="sxs-lookup"><span data-stu-id="e8885-111">The user registering the JEA configuration has administrator rights on the system.</span></span>
- <span data-ttu-id="e8885-112">Wybrana nazwa dla punktu końcowego usługi JEA.</span><span class="sxs-lookup"><span data-stu-id="e8885-112">You've selected a name for your JEA endpoint.</span></span>

<span data-ttu-id="e8885-113">Nazwa punktu końcowego usługi JEA jest wymagana, kiedy użytkownicy łączą się systemu przy użyciu technologii JEA.</span><span class="sxs-lookup"><span data-stu-id="e8885-113">The name of the JEA endpoint is required when users connect to the system using JEA.</span></span> <span data-ttu-id="e8885-114">[Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) polecenie cmdlet wyświetla listę nazw punktów końcowych w systemie.</span><span class="sxs-lookup"><span data-stu-id="e8885-114">The [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet lists the names of the endpoints on a system.</span></span> <span data-ttu-id="e8885-115">Punkty końcowe, które zaczyna się `microsoft` zwykle są dostarczane z programem Windows.</span><span class="sxs-lookup"><span data-stu-id="e8885-115">Endpoints that start with `microsoft` are typically shipped with Windows.</span></span> <span data-ttu-id="e8885-116">`microsoft.powershell` Punkt końcowy jest domyślny punkt końcowy używany podczas nawiązywania połączenia zdalnego punktu końcowego programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8885-116">The `microsoft.powershell` endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

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

<span data-ttu-id="e8885-117">Uruchom następujące polecenie, aby zarejestrować punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="e8885-117">Run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="e8885-118">Poprzednie polecenie uruchamia ponownie usługę WinRM w systemie.</span><span class="sxs-lookup"><span data-stu-id="e8885-118">The previous command restarts the WinRM service on the system.</span></span> <span data-ttu-id="e8885-119">To kończy wszystkie sesje komunikacji zdalnej programu PowerShell i wszystkie trwające operacje konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="e8885-119">This terminates all PowerShell remoting sessions and any ongoing DSC configurations.</span></span> <span data-ttu-id="e8885-120">Zalecamy na komputerach produkcyjnych w trybie offline należy wykonać przed uruchomieniem polecenia, aby uniknąć zakłócenia operacji biznesowych.</span><span class="sxs-lookup"><span data-stu-id="e8885-120">We recommended you take production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="e8885-121">Po rejestracji możesz przystąpić do [używać technologii JEA](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="e8885-121">After registration, you're ready to [use JEA](using-jea.md).</span></span> <span data-ttu-id="e8885-122">Plik konfiguracji sesji można usunąć w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="e8885-122">You may delete the session configuration file at any time.</span></span> <span data-ttu-id="e8885-123">Plik konfiguracyjny nie jest używana po opcji rejestracji, punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e8885-123">The configuration file isn't used after registration of the endpoint.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="e8885-124">Konfiguracja wielu maszyn za pomocą DSC</span><span class="sxs-lookup"><span data-stu-id="e8885-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="e8885-125">Podczas wdrażania usługi JEA na wielu komputerach, najprostszym modelem wdrażania korzysta z technologii JEA [Desired State Configuration (DSC)](/powershell/dsc/overview) zasób, aby szybko i spójnie wdrażać JEA na każdym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e8885-125">When deploying JEA on multiple machines, the simplest deployment model uses the JEA [Desired State Configuration (DSC)](/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="e8885-126">Aby wdrożyć JEA za pomocą DSC, upewnij się, że spełniono następujące wymagania wstępne:</span><span class="sxs-lookup"><span data-stu-id="e8885-126">To deploy JEA with DSC, ensure the following prerequisites are met:</span></span>

- <span data-ttu-id="e8885-127">Jeden lub więcej możliwości roli zostały utworzone i dodane do modułu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8885-127">One or more role capabilities have been authored and added to a PowerShell module.</span></span>
- <span data-ttu-id="e8885-128">Moduł programu PowerShell zawierający role są przechowywane w udziale plików (tylko do odczytu), które jest dostępne przy każdej maszyny.</span><span class="sxs-lookup"><span data-stu-id="e8885-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="e8885-129">Zostały uznane za ustawienia konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="e8885-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="e8885-130">Nie musisz utworzyć plik konfiguracji sesji, korzystając z zasobów DSC JEA.</span><span class="sxs-lookup"><span data-stu-id="e8885-130">You don't need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="e8885-131">Masz poświadczenia, które umożliwią działań administracyjnych na każdym komputerze lub dostęp do serwera ściągania DSC, które są używane do zarządzania maszynami.</span><span class="sxs-lookup"><span data-stu-id="e8885-131">You have credentials that allow administrative actions on each machine or access to the DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="e8885-132">Pobrano [zasobów DSC JEA](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).</span><span class="sxs-lookup"><span data-stu-id="e8885-132">You've downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).</span></span>

<span data-ttu-id="e8885-133">Utwórz konfigurację DSC dla punktu końcowego usługi JEA na serwerze docelowym, komputera lub ściągania.</span><span class="sxs-lookup"><span data-stu-id="e8885-133">Create a DSC configuration for your JEA endpoint on a target machine or pull server.</span></span> <span data-ttu-id="e8885-134">W tej konfiguracji **JustEnoughAdministration** zasób DSC definiuje plik konfiguracji sesji i **pliku** zasobów kopiuje możliwości roli z udziału plików.</span><span class="sxs-lookup"><span data-stu-id="e8885-134">In this configuration, the **JustEnoughAdministration** DSC resource defines the session configuration file and the **File** resource copies the role capabilities from the file share.</span></span>

<span data-ttu-id="e8885-135">Można skonfigurować za pomocą zasobów DSC są następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="e8885-135">The following properties are configurable using the DSC resource:</span></span>

- <span data-ttu-id="e8885-136">Definicje ról</span><span class="sxs-lookup"><span data-stu-id="e8885-136">Role Definitions</span></span>
- <span data-ttu-id="e8885-137">Grupy wirtualne kont</span><span class="sxs-lookup"><span data-stu-id="e8885-137">Virtual account groups</span></span>
- <span data-ttu-id="e8885-138">Nazwa konta usługi zarządzanego przez grupę</span><span class="sxs-lookup"><span data-stu-id="e8885-138">Group-managed service account name</span></span>
- <span data-ttu-id="e8885-139">Katalog transkrypcji</span><span class="sxs-lookup"><span data-stu-id="e8885-139">Transcript directory</span></span>
- <span data-ttu-id="e8885-140">Dysku użytkownika</span><span class="sxs-lookup"><span data-stu-id="e8885-140">User drive</span></span>
- <span data-ttu-id="e8885-141">Zasady dostępu warunkowego</span><span class="sxs-lookup"><span data-stu-id="e8885-141">Conditional access rules</span></span>
- <span data-ttu-id="e8885-142">Skrypty uruchamiania dla sesji usługi JEA</span><span class="sxs-lookup"><span data-stu-id="e8885-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="e8885-143">Składnia dla każdego z tych właściwości w konfiguracji DSC jest zgodna z pliku konfiguracji sesji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8885-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="e8885-144">Poniżej znajduje się Przykładowa konfiguracja DSC dla modułu konserwacji serwera ogólnego.</span><span class="sxs-lookup"><span data-stu-id="e8885-144">Below is a sample DSC configuration for a general server maintenance module.</span></span> <span data-ttu-id="e8885-145">Przyjęto założenie, że prawidłowy modułu programu PowerShell zawierający możliwości roli znajduje się na `\\myfileshare\JEA` udziału plików.</span><span class="sxs-lookup"><span data-stu-id="e8885-145">It assumes that a valid PowerShell module containing role capabilities is located on the `\\myfileshare\JEA` file share.</span></span>

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

<span data-ttu-id="e8885-146">Następnie konfiguracja jest stosowana w systemie przez bezpośrednie wywołanie [Local Configuration Manager](/powershell/dsc/managing-nodes/metaConfig) lub aktualizowania [konfiguracji serwera ściągania](/powershell/dsc/pull-server/pullServer).</span><span class="sxs-lookup"><span data-stu-id="e8885-146">Next, the configuration is applied on a system by directly invoking the [Local Configuration Manager](/powershell/dsc/managing-nodes/metaConfig) or updating the [pull server configuration](/powershell/dsc/pull-server/pullServer).</span></span>

<span data-ttu-id="e8885-147">Zasób DSC umożliwia również zastąpić domyślną **Microsoft.PowerShell** punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e8885-147">The DSC resource also allows you to replace the default **Microsoft.PowerShell** endpoint.</span></span> <span data-ttu-id="e8885-148">Po wymianie, zasobu powoduje automatyczne zarejestrowanie punktu kopii zapasowej końcowego o nazwie **Microsoft.PowerShell.Restricted**.</span><span class="sxs-lookup"><span data-stu-id="e8885-148">When replaced, the resource automatically registers a backup endpoint named **Microsoft.PowerShell.Restricted**.</span></span> <span data-ttu-id="e8885-149">Punkt końcowy kopii zapasowej ma wartości domyślnej listy ACL usługi WinRM, która umożliwia użytkownicy zarządzania zdalnego i Administratorzy lokalni, członkowie grupy mogli uzyskać do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="e8885-149">The backup endpoint has the default WinRM ACL that allows Remote Management Users and local Administrators group members to access it.</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="e8885-150">Wyrejestrowywanie konfiguracje usługi JEA</span><span class="sxs-lookup"><span data-stu-id="e8885-150">Unregistering JEA configurations</span></span>

<span data-ttu-id="e8885-151">[Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) polecenie cmdlet usuwa punktu końcowego JEA.</span><span class="sxs-lookup"><span data-stu-id="e8885-151">The [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet removes a JEA endpoint.</span></span> <span data-ttu-id="e8885-152">Wyrejestrowywanie punktu końcowego usługi JEA uniemożliwia tworzenie nowych technologii JEA sesji w systemie w nowych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="e8885-152">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span> <span data-ttu-id="e8885-153">W tym obszarze pozwala również zaktualizować konfigurację usługi JEA rejestrując ponownie plik konfiguracji sesji zaktualizowane przy użyciu tej samej nazwy punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e8885-153">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="e8885-154">Wyrejestrowywanie JEA punktu końcowego powoduje ponowne uruchomienie usługi WinRM.</span><span class="sxs-lookup"><span data-stu-id="e8885-154">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span> <span data-ttu-id="e8885-155">Przerywa to działanie najbardziej zdalnego operacji zarządzania w toku, w tym innych sesji programu PowerShell, wywołań usługi WMI i niektóre narzędzia do zarządzania.</span><span class="sxs-lookup"><span data-stu-id="e8885-155">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span> <span data-ttu-id="e8885-156">Punkty końcowe programu PowerShell można wyrejestrować dopiero podczas planowanej konserwacji systemu windows.</span><span class="sxs-lookup"><span data-stu-id="e8885-156">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e8885-157">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="e8885-157">Next steps</span></span>

[<span data-ttu-id="e8885-158">Testowanie punktu końcowego usługi JEA</span><span class="sxs-lookup"><span data-stu-id="e8885-158">Test the JEA endpoint</span></span>](using-jea.md)
