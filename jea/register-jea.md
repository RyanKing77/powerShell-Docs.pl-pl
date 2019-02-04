---
ms.date: 06/12/2017
keywords: jea, programu powershell, zabezpieczeń
title: Rejestrowanie usługi JEA konfiguracji
ms.openlocfilehash: 160aa95283da57a10aad5fdd4043adb1354a5db5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55689064"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="83a07-103">Rejestrowanie usługi JEA konfiguracji</span><span class="sxs-lookup"><span data-stu-id="83a07-103">Registering JEA Configurations</span></span>

> <span data-ttu-id="83a07-104">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="83a07-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="83a07-105">Po utworzeniu usługi [możliwości roli](role-capabilities.md) i [plik konfiguracji sesji](session-configurations.md) utworzone, ostatnim krokiem, zanim będzie można użyć technologii JEA jest rejestrowanie punktu końcowego usługi JEA.</span><span class="sxs-lookup"><span data-stu-id="83a07-105">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step before you can use JEA is to register the JEA endpoint.</span></span>
<span data-ttu-id="83a07-106">Rejestrowanie punktu końcowego JEA w systemie sprawia, że punkt końcowy do użycia przez użytkowników i aparatów automatyzacji.</span><span class="sxs-lookup"><span data-stu-id="83a07-106">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="83a07-107">Konfiguracja pojedynczego komputera</span><span class="sxs-lookup"><span data-stu-id="83a07-107">Single machine configuration</span></span>

<span data-ttu-id="83a07-108">W przypadku małych środowisk można wdrożyć JEA, rejestrując się, używając pliku konfiguracji sesji [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="83a07-108">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="83a07-109">Przed rozpoczęciem upewnij się, że zostały spełnione następujące wymagania wstępne:</span><span class="sxs-lookup"><span data-stu-id="83a07-109">Before you begin, ensure that the following prerequisites have been met:</span></span>
- <span data-ttu-id="83a07-110">Co najmniej jednej roli został utworzony i umieszczane w folderze "RoleCapabilities" prawidłowy modułu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83a07-110">One or more roles has been created and placed in the 'RoleCapabilities' folder of a valid PowerShell module.</span></span>
- <span data-ttu-id="83a07-111">Utworzono plik konfiguracji sesji i przetestowane.</span><span class="sxs-lookup"><span data-stu-id="83a07-111">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="83a07-112">Użytkownik rejestrowanie usługi JEA konfiguracji ma prawa administratora na systemy.</span><span class="sxs-lookup"><span data-stu-id="83a07-112">The user registering the JEA configuration has administrator rights on the system(s).</span></span>

<span data-ttu-id="83a07-113">Należy również wybranie nazwy dla punktu końcowego usługi JEA.</span><span class="sxs-lookup"><span data-stu-id="83a07-113">You also need to select a name for your JEA endpoint.</span></span>
<span data-ttu-id="83a07-114">Nazwa punktu końcowego usługi JEA jest wymagana, gdy użytkownicy chcą nawiązać połączenie z tego systemu przy użyciu technologii JEA.</span><span class="sxs-lookup"><span data-stu-id="83a07-114">The name of the JEA endpoint is required when users want to connect to the system using JEA.</span></span>
<span data-ttu-id="83a07-115">Możesz użyć [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) polecenia cmdlet, aby sprawdzić nazwy istniejące punkty końcowe w systemie.</span><span class="sxs-lookup"><span data-stu-id="83a07-115">You can use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet to check the names of existing endpoints on the system.</span></span>
<span data-ttu-id="83a07-116">Punkty końcowe, które zaczyna się "microsoft" zwykle są dostarczane z programem Windows.</span><span class="sxs-lookup"><span data-stu-id="83a07-116">Endpoints that start with 'microsoft' are typically shipped with Windows.</span></span>
<span data-ttu-id="83a07-117">Punkt końcowy "microsoft.powershell" jest domyślny punkt końcowy używany podczas nawiązywania połączenia zdalnego punktu końcowego programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83a07-117">The 'microsoft.powershell' endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="83a07-118">Po określeniu odpowiednią nazwę punktu końcowego usługi JEA, uruchom następujące polecenie, aby zarejestrować punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="83a07-118">When you have determined an appropriate name for your JEA endpoint, run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="83a07-119">Powyższe polecenie uruchamia ponownie usługę WinRM w systemie.</span><span class="sxs-lookup"><span data-stu-id="83a07-119">The above command restarts the WinRM service on the system.</span></span>
> <span data-ttu-id="83a07-120">To kończy wszystkie sesje komunikacji zdalnej programu PowerShell, a także wszystkie trwające operacje konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="83a07-120">This terminates all PowerShell remoting sessions as well as any ongoing DSC configurations.</span></span>
> <span data-ttu-id="83a07-121">Zalecane jest, należy wykonać żadnych produkcyjnych maszyn w tryb offline przed uruchomieniem polecenia, aby uniknąć zakłócenia operacji biznesowych.</span><span class="sxs-lookup"><span data-stu-id="83a07-121">It is recommended that you take any production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="83a07-122">Jeśli rejestracja zakończy się pomyślnie, można przystąpić do [używać technologii JEA](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="83a07-122">If registration is successful, you are ready to [use JEA](using-jea.md).</span></span>
<span data-ttu-id="83a07-123">Plik konfiguracji sesji możesz usunąć w dowolnym momencie; nie jest używana po rejestracji, punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="83a07-123">You may delete the session configuration file at any time; it is not used after registration of the end point.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="83a07-124">Konfiguracja wielu maszyn za pomocą DSC</span><span class="sxs-lookup"><span data-stu-id="83a07-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="83a07-125">Jeśli wdrażasz JEA na wielu komputerach, najprostszym modelem wdrażania jest użycie usługi JEA [Desired State Configuration](https://msdn.microsoft.com/powershell/dsc/overview) zasób, aby szybko i spójnie wdrażać JEA na każdym komputerze.</span><span class="sxs-lookup"><span data-stu-id="83a07-125">If you are deploying JEA on multiple machines, the simplest deployment model is to use the JEA [Desired State Configuration](https://msdn.microsoft.com/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="83a07-126">Aby wdrożyć JEA za pomocą DSC, należy upewnić się, że spełniono następujące wymagania wstępne:</span><span class="sxs-lookup"><span data-stu-id="83a07-126">To deploy JEA with DSC, you need to ensure the following prerequisites are met:</span></span>
- <span data-ttu-id="83a07-127">Jeden lub więcej możliwości roli zostały utworzone i dodane do prawidłowy modułu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83a07-127">One or more role capabilities have been authored and added to a valid PowerShell module.</span></span>
- <span data-ttu-id="83a07-128">Moduł programu PowerShell zawierający role są przechowywane w udziale plików (tylko do odczytu), które jest dostępne przy każdej maszyny.</span><span class="sxs-lookup"><span data-stu-id="83a07-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="83a07-129">Zostały uznane za ustawienia konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="83a07-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="83a07-130">Nie trzeba utworzyć plik konfiguracji sesji, korzystając z zasobów DSC JEA.</span><span class="sxs-lookup"><span data-stu-id="83a07-130">You do not need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="83a07-131">Poświadczenia, które umożliwiają wykonywanie akcji administracyjnych na każdym komputerze lub mają dostęp do serwera ściągania DSC, używany do zarządzania maszynami.</span><span class="sxs-lookup"><span data-stu-id="83a07-131">You have credentials that allow you to perform administrative actions on each machine, or have access to a DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="83a07-132">Pobrano [zasobów DSC usługi JEA](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span><span class="sxs-lookup"><span data-stu-id="83a07-132">You have downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span></span>

<span data-ttu-id="83a07-133">Na docelowym komputerze (lub serwerze ściągania, jeśli używana jest jedna) należy utworzyć konfigurację DSC dla punktu końcowego usługi JEA.</span><span class="sxs-lookup"><span data-stu-id="83a07-133">On a target machine (or pull server, if you are using one), create a DSC configuration for your JEA endpoint.</span></span>
<span data-ttu-id="83a07-134">W tej konfiguracji za pomocą zasobów DSC JustEnoughAdministration pliku konfiguracji sesji oraz zasobów plików do skopiowania możliwości roli z udziału plików.</span><span class="sxs-lookup"><span data-stu-id="83a07-134">In this configuration, you use the JustEnoughAdministration DSC resource to set up the session configuration file and the File resource to copy over the role capabilities from the file share.</span></span>

<span data-ttu-id="83a07-135">Można skonfigurować za pomocą zasobów DSC są następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="83a07-135">The following properties are configurable using the DSC resource:</span></span>
- <span data-ttu-id="83a07-136">Definicje ról</span><span class="sxs-lookup"><span data-stu-id="83a07-136">Role Definitions</span></span>
- <span data-ttu-id="83a07-137">Grupy wirtualne konta</span><span class="sxs-lookup"><span data-stu-id="83a07-137">Virtual Account groups</span></span>
- <span data-ttu-id="83a07-138">Nazwa konta usługi zarządzanego przez grupę</span><span class="sxs-lookup"><span data-stu-id="83a07-138">Group Managed Service Account name</span></span>
- <span data-ttu-id="83a07-139">Katalog transkrypcji</span><span class="sxs-lookup"><span data-stu-id="83a07-139">Transcript directory</span></span>
- <span data-ttu-id="83a07-140">Dysku użytkownika</span><span class="sxs-lookup"><span data-stu-id="83a07-140">User drive</span></span>
- <span data-ttu-id="83a07-141">Zasady dostępu warunkowego</span><span class="sxs-lookup"><span data-stu-id="83a07-141">Conditional access rules</span></span>
- <span data-ttu-id="83a07-142">Skrypty uruchamiania dla sesji usługi JEA</span><span class="sxs-lookup"><span data-stu-id="83a07-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="83a07-143">Składnia dla każdego z tych właściwości w konfiguracji DSC jest zgodna z pliku konfiguracji sesji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83a07-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="83a07-144">Poniżej znajduje się Przykładowa konfiguracja DSC dla modułu konserwacji serwera ogólnego.</span><span class="sxs-lookup"><span data-stu-id="83a07-144">Below is a sample DSC configuration for a general server maintenance module.</span></span>

<span data-ttu-id="83a07-145">Przyjęto założenie, że prawidłowy modułu programu PowerShell zawierający możliwości roli w podfolderze "RoleCapabilities" znajduje się na "\\\\myfileshare\\JEA" udziału plików.</span><span class="sxs-lookup"><span data-stu-id="83a07-145">It assumes that a valid PowerShell module containing role capabilities in a 'RoleCapabilities' subfolder is located on the '\\\\myfileshare\\JEA' file share.</span></span>


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

<span data-ttu-id="83a07-146">Tę konfigurację można następnie zastosować funkcje w systemie przez [bezpośrednie wywołanie programu Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig) lub aktualizowania [konfiguracji serwera ściągania](https://msdn.microsoft.com/powershell/dsc/pullserver).</span><span class="sxs-lookup"><span data-stu-id="83a07-146">This configuration can then be applied on a system by [directly invoking the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig) or updating the [pull server configuration](https://msdn.microsoft.com/powershell/dsc/pullserver).</span></span>

<span data-ttu-id="83a07-147">Zasób DSC pozwala również zastąpić domyślny punkt końcowy komunikacji zdalnej Microsoft.PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83a07-147">The DSC resource also allows you to replace the default Microsoft.PowerShell remoting endpoint.</span></span>
<span data-ttu-id="83a07-148">Jeśli to zrobisz, zasobu powoduje automatyczne zarejestrowanie punktu końcowego unconstrainted kopii zapasowych o nazwie "Microsoft.PowerShell.Restricted", który ma wartości domyślnej listy ACL usługi WinRM (dzięki czemu użytkownicy zarządzania zdalnego i Administratorzy lokalni członkowie grupy mogli uzyskać do niego dostęp).</span><span class="sxs-lookup"><span data-stu-id="83a07-148">If you do this, the resource automatically registers a backup unconstrainted endpoint named "Microsoft.PowerShell.Restricted" which has the default WinRM ACL (allowing Remote Management Users and local Administrators group members to access it).</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="83a07-149">Wyrejestrowywanie konfiguracje usługi JEA</span><span class="sxs-lookup"><span data-stu-id="83a07-149">Unregistering JEA configurations</span></span>

<span data-ttu-id="83a07-150">Aby usunąć punkt końcowy usługi JEA w systemie, użyj [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="83a07-150">To remove a JEA endpoint on a system, use the [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span></span>
<span data-ttu-id="83a07-151">Wyrejestrowywanie punktu końcowego usługi JEA uniemożliwia tworzenie nowych technologii JEA sesji w systemie w nowych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="83a07-151">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span>
<span data-ttu-id="83a07-152">W tym obszarze pozwala również zaktualizować konfigurację usługi JEA rejestrując ponownie plik konfiguracji sesji zaktualizowane przy użyciu tej samej nazwy punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="83a07-152">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="83a07-153">Wyrejestrowywanie JEA punktu końcowego powoduje ponowne uruchomienie usługi WinRM.</span><span class="sxs-lookup"><span data-stu-id="83a07-153">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span>
> <span data-ttu-id="83a07-154">Przerywa to działanie najbardziej zdalnego operacji zarządzania w toku, w tym innych sesji programu PowerShell, wywołań usługi WMI i niektóre narzędzia do zarządzania.</span><span class="sxs-lookup"><span data-stu-id="83a07-154">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span>
> <span data-ttu-id="83a07-155">Punkty końcowe programu PowerShell można wyrejestrować dopiero podczas planowanej konserwacji systemu windows.</span><span class="sxs-lookup"><span data-stu-id="83a07-155">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="83a07-156">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="83a07-156">Next steps</span></span>

- [<span data-ttu-id="83a07-157">Testowanie punktu końcowego usługi JEA</span><span class="sxs-lookup"><span data-stu-id="83a07-157">Test the JEA endpoint</span></span>](using-jea.md)
