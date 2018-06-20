---
ms.date: 06/12/2017
keywords: jea, programu powershell, zabezpieczeń
title: Rejestrowanie JEA konfiguracji
ms.openlocfilehash: cda899b20378b0183a3d88ecfd593aaf7356e967
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188517"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="09a0a-103">Rejestrowanie JEA konfiguracji</span><span class="sxs-lookup"><span data-stu-id="09a0a-103">Registering JEA Configurations</span></span>

> <span data-ttu-id="09a0a-104">Dotyczy: środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="09a0a-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="09a0a-105">Ostatnim krokiem przed użyciem JEA po utworzeniu sieci [możliwości roli](role-capabilities.md) i [pliku konfiguracji sesji](session-configurations.md) utworzony się zarejestrować punkt końcowy JEA.</span><span class="sxs-lookup"><span data-stu-id="09a0a-105">The last step before you can use JEA once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created is to register the JEA endpoint.</span></span>
<span data-ttu-id="09a0a-106">Ten proces dotyczy informacje o konfiguracji sesji systemu i udostępnia punkt końcowy do użycia przez użytkowników i aparatów automatyzacji.</span><span class="sxs-lookup"><span data-stu-id="09a0a-106">This process applies the session configuration information to the system and makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="09a0a-107">Konfiguracja pojedynczego komputera</span><span class="sxs-lookup"><span data-stu-id="09a0a-107">Single machine configuration</span></span>

<span data-ttu-id="09a0a-108">W przypadku małych środowisk można wdrożyć JEA przez zarejestrowanie sesji konfiguracji plików przy użyciu [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="09a0a-108">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="09a0a-109">Przed rozpoczęciem upewnij się, że zostały spełnione następujące wymagania wstępne:</span><span class="sxs-lookup"><span data-stu-id="09a0a-109">Before you begin, ensure that the following prerequisites have been met:</span></span>
- <span data-ttu-id="09a0a-110">Co najmniej jedną rolę został utworzony i umieszczane w folderze "RoleCapabilities" nieprawidłowy modułu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="09a0a-110">One or more roles has been created and placed in the 'RoleCapabilities' folder of a valid PowerShell module.</span></span>
- <span data-ttu-id="09a0a-111">Utworzono plik konfiguracji sesji i przetestowane.</span><span class="sxs-lookup"><span data-stu-id="09a0a-111">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="09a0a-112">Użytkownik rejestrujący konfiguracji JEA ma prawa administratora na systemy.</span><span class="sxs-lookup"><span data-stu-id="09a0a-112">The user registering the JEA configuration has administrator rights on the system(s).</span></span>

<span data-ttu-id="09a0a-113">Należy również wybrać nazwę punktu końcowego JEA.</span><span class="sxs-lookup"><span data-stu-id="09a0a-113">You will also need to select a name for your JEA endpoint.</span></span>
<span data-ttu-id="09a0a-114">Nazwa punktu końcowego JEA będzie wymagane, kiedy użytkownik chce nawiązać połączenie przy użyciu JEA systemu.</span><span class="sxs-lookup"><span data-stu-id="09a0a-114">The name of the JEA endpoint will be required when users want to connect to the system using JEA.</span></span>
<span data-ttu-id="09a0a-115">Można użyć [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) polecenia cmdlet, aby sprawdzić nazwy istniejące punkty końcowe w systemie.</span><span class="sxs-lookup"><span data-stu-id="09a0a-115">You can use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet to check the names of existing endpoints on the system.</span></span>
<span data-ttu-id="09a0a-116">Punkty końcowe rozpoczynających się od 'microsoft' zwykle są dostarczane z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="09a0a-116">Endpoints that start with 'microsoft' are typically shipped with Windows.</span></span>
<span data-ttu-id="09a0a-117">Punkt końcowy "microsoft.powershell" jest używany podczas nawiązywania połączenia zdalnego punktu końcowego programu PowerShell domyślny punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="09a0a-117">The 'microsoft.powershell' endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="09a0a-118">Po określeniu odpowiednią nazwę punktu końcowego JEA, uruchom następujące polecenie, aby zarejestrować punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="09a0a-118">When you have determined an appropriate name for your JEA endpoint, run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="09a0a-119">Powyższe polecenie uruchomi usługę WinRM na komputerze.</span><span class="sxs-lookup"><span data-stu-id="09a0a-119">The above command will restart the WinRM service on the system.</span></span>
> <span data-ttu-id="09a0a-120">Spowoduje to przerwanie wszystkich sesji komunikacji zdalnej programu PowerShell, a także wszystkie trwające operacje konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="09a0a-120">This will terminate all PowerShell remoting sessions as well as any ongoing DSC configurations.</span></span>
> <span data-ttu-id="09a0a-121">Zaleca się wyłączeniem wszelkich maszyn produkcyjnym przed uruchomieniem polecenia, aby uniknąć zakłóceń w działalności firmy.</span><span class="sxs-lookup"><span data-stu-id="09a0a-121">It is recommended that you take any production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="09a0a-122">Jeśli rejestracja powiodła się, można przystąpić do [Użyj JEA](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="09a0a-122">If registration was successful, you are ready to [use JEA](using-jea.md).</span></span>
<span data-ttu-id="09a0a-123">Plik konfiguracji sesji można usunąć w dowolnym momencie; nie jest on używany po rejestracji.</span><span class="sxs-lookup"><span data-stu-id="09a0a-123">You may delete the session configuration file at any time; it is not used after registration.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="09a0a-124">Konfiguracja obsługi wielu komputerów z usługi Konfiguracja DSC</span><span class="sxs-lookup"><span data-stu-id="09a0a-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="09a0a-125">Jeśli wdrażasz JEA na wielu komputerach, najprostszym modelem wdrożenia jest użycie JEA [konfiguracji żądanego stanu](https://msdn.microsoft.com/en-us/powershell/dsc/overview) zasób, aby szybko i spójne wdrażanie JEA na każdym komputerze.</span><span class="sxs-lookup"><span data-stu-id="09a0a-125">If you are deploying JEA on multiple machines, the simplest deployment model is to use the JEA [Desired State Configuration](https://msdn.microsoft.com/en-us/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="09a0a-126">Aby wdrożyć JEA usłudze Konfiguracja DSC, należy upewnić się, że są spełnione następujące wymagania wstępne:</span><span class="sxs-lookup"><span data-stu-id="09a0a-126">To deploy JEA with DSC, you will need to ensure the following prerequisites are met:</span></span>
- <span data-ttu-id="09a0a-127">Jeden lub więcej możliwości roli zostały utworzone i dodane do prawidłowy modułu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="09a0a-127">One or more role capabilities have been authored and added to a valid PowerShell module.</span></span>
- <span data-ttu-id="09a0a-128">Moduł PowerShell zawierającego role są przechowywane w udziale plików (tylko do odczytu) dostępny przy każdej maszyny.</span><span class="sxs-lookup"><span data-stu-id="09a0a-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="09a0a-129">Określono ustawienia konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="09a0a-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="09a0a-130">Nie trzeba utworzyć plik konfiguracji sesji, korzystając z zasobów JEA DSC.</span><span class="sxs-lookup"><span data-stu-id="09a0a-130">You do not need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="09a0a-131">Masz poświadczenia, które umożliwiają wykonywanie zadań administracyjnych na każdym komputerze, lub korzystać z serwera ściągania usługi Konfiguracja DSC używane do zarządzania na komputerach.</span><span class="sxs-lookup"><span data-stu-id="09a0a-131">You have credentials that will allow you to perform administrative actions on each machine, or have access to a DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="09a0a-132">Pobrano [JEA DSC zasobów](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span><span class="sxs-lookup"><span data-stu-id="09a0a-132">You have downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span></span>

<span data-ttu-id="09a0a-133">Na docelowej maszynie (lub serwera ściągania, jeśli używasz) utworzenie konfiguracji DSC dla punktu końcowego JEA.</span><span class="sxs-lookup"><span data-stu-id="09a0a-133">On a target machine (or pull server, if you are using one), create a DSC configuration for your JEA endpoint.</span></span>
<span data-ttu-id="09a0a-134">W tej konfiguracji użyje zasobu JustEnoughAdministration DSC pliku konfiguracji sesji i zasobu pliku kopiować możliwości roli z udziału plików.</span><span class="sxs-lookup"><span data-stu-id="09a0a-134">In this configuration, you will use the JustEnoughAdministration DSC resource to set up the session configuration file and the File resource to copy over the role capabilities from the file share.</span></span>

<span data-ttu-id="09a0a-135">Można konfigurować przy użyciu zasobów DSC są następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="09a0a-135">The following properties are configurable using the DSC resource:</span></span>
- <span data-ttu-id="09a0a-136">Definicje ról</span><span class="sxs-lookup"><span data-stu-id="09a0a-136">Role Definitions</span></span>
- <span data-ttu-id="09a0a-137">Wirtualny grup kont</span><span class="sxs-lookup"><span data-stu-id="09a0a-137">Virtual Account groups</span></span>
- <span data-ttu-id="09a0a-138">Nazwa konta usługi zarządzanego przez grupę</span><span class="sxs-lookup"><span data-stu-id="09a0a-138">Group Managed Service Account name</span></span>
- <span data-ttu-id="09a0a-139">Wykaz katalogu</span><span class="sxs-lookup"><span data-stu-id="09a0a-139">Transcript directory</span></span>
- <span data-ttu-id="09a0a-140">Stacji użytkownika</span><span class="sxs-lookup"><span data-stu-id="09a0a-140">User drive</span></span>
- <span data-ttu-id="09a0a-141">Zasady dostępu warunkowego</span><span class="sxs-lookup"><span data-stu-id="09a0a-141">Conditional access rules</span></span>
- <span data-ttu-id="09a0a-142">Skrypty uruchamiania dla sesji JEA</span><span class="sxs-lookup"><span data-stu-id="09a0a-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="09a0a-143">Składnia dla każdej z tych właściwości w konfiguracji DSC jest zgodna z pliku konfiguracji sesji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="09a0a-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="09a0a-144">Poniżej znajduje się Przykładowa konfiguracja DSC modułu obsługi ogólnych.</span><span class="sxs-lookup"><span data-stu-id="09a0a-144">Below is a sample DSC configuration for a general server maintenance module.</span></span>

<span data-ttu-id="09a0a-145">Przyjęto założenie, że prawidłowy moduł PowerShell zawierający możliwości roli w podfolderze "RoleCapabilities" znajduje się na "\\\\myfileshare\\JEA" udziału plików.</span><span class="sxs-lookup"><span data-stu-id="09a0a-145">It assumes that a valid PowerShell module containing role capabilities in a 'RoleCapabilities' subfolder is located on the '\\\\myfileshare\\JEA' file share.</span></span>


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

<span data-ttu-id="09a0a-146">Tę konfigurację można zastosować w systemie przez [bezpośrednie wywoływanie lokalny program Configuration Manager](https://msdn.microsoft.com/en-us/powershell/dsc/metaconfig) lub aktualizowania [konfiguracji serwera ściągania](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver).</span><span class="sxs-lookup"><span data-stu-id="09a0a-146">This configuration can then be applied on a system by [directly invoking the Local Configuration Manager](https://msdn.microsoft.com/en-us/powershell/dsc/metaconfig) or updating the [pull server configuration](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver).</span></span>

<span data-ttu-id="09a0a-147">Zasobów DSC pozwala również zastąpić domyślny punkt końcowy komunikacji zdalnej Microsoft.PowerShell.</span><span class="sxs-lookup"><span data-stu-id="09a0a-147">The DSC resource also allows you to replace the default Microsoft.PowerShell remoting endpoint.</span></span>
<span data-ttu-id="09a0a-148">Jeśli to zrobisz, zasobu zostanie automatycznie zarejestrować punkt końcowy unconstrainted kopii zapasowej o nazwie "Microsoft.PowerShell.Restricted", którego domyślne WinRM listy kontroli dostępu (dzięki czemu użytkownicy zarządzania zdalnego i Administratorzy lokalni członków grupy dostępu do niego).</span><span class="sxs-lookup"><span data-stu-id="09a0a-148">If you do this, the resource will automatically register a backup unconstrainted endpoint named "Microsoft.PowerShell.Restricted" which has the default WinRM ACL (allowing Remote Management Users and local Administrators group members to access it).</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="09a0a-149">Wyrejestrowywanie konfiguracje JEA</span><span class="sxs-lookup"><span data-stu-id="09a0a-149">Unregistering JEA configurations</span></span>

<span data-ttu-id="09a0a-150">Aby usunąć punkt końcowy JEA w systemie, użyj [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="09a0a-150">To remove a JEA endpoint on a system, use the [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span></span>
<span data-ttu-id="09a0a-151">Wyrejestrowywanie punktu końcowego JEA uniemożliwi nowych użytkowników do tworzenia nowych JEA sesji w systemie.</span><span class="sxs-lookup"><span data-stu-id="09a0a-151">Unregistering a JEA endpoint will prevent new users from creating new JEA sessions on the system.</span></span>
<span data-ttu-id="09a0a-152">Umożliwia on również zaktualizować konfiguracji JEA rejestrując ponownie plik konfiguracji sesji zaktualizowane przy użyciu tej samej nazwy punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="09a0a-152">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="09a0a-153">Wyrejestrowywanie JEA punktu końcowego spowoduje ponowne uruchomienie usługi WinRM.</span><span class="sxs-lookup"><span data-stu-id="09a0a-153">Unregistering a JEA endpoint will cause the WinRM service to restart.</span></span>
> <span data-ttu-id="09a0a-154">Spowoduje to zakłóceń najbardziej zdalnego zarządzania operacji w toku, łącznie z innych sesji programu PowerShell, wywołań usługi WMI i niektóre narzędzia do zarządzania.</span><span class="sxs-lookup"><span data-stu-id="09a0a-154">This will interrupt most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span>
> <span data-ttu-id="09a0a-155">Punkty końcowe programu PowerShell można wyrejestrować dopiero podczas zaplanowanej konserwacji systemu windows.</span><span class="sxs-lookup"><span data-stu-id="09a0a-155">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="09a0a-156">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="09a0a-156">Next steps</span></span>

- [<span data-ttu-id="09a0a-157">Testowanie JEA punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="09a0a-157">Test the JEA endpoint</span></span>](using-jea.md)