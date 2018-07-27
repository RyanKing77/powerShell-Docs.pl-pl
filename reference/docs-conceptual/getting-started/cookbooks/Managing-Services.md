---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Zarządzanie usługami
ms.assetid: 7a410e4d-514b-4813-ba0c-0d8cef88df31
ms.openlocfilehash: 81fd8802215da80ce22fa3fd4750b1df6efe8206
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268079"
---
# <a name="managing-services"></a><span data-ttu-id="43b6b-103">Zarządzanie usługami</span><span class="sxs-lookup"><span data-stu-id="43b6b-103">Managing Services</span></span>

<span data-ttu-id="43b6b-104">Ma osiem rdzeni usługi poleceń cmdlet przeznaczone dla różnych zadań usługi.</span><span class="sxs-lookup"><span data-stu-id="43b6b-104">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="43b6b-105">Przyjrzymy się tylko wyświetlanie i zmiana w stanie uruchomionym dla usługi, ale można uzyskać listę poleceń cmdlet usługi za pomocą `Get-Help \*-Service`, oraz informacje dotyczące każdego polecenia cmdlet usługi można znaleźć przy użyciu `Get-Help <Cmdlet-Name>`, takich jak `Get-Help New-Service`.</span><span class="sxs-lookup"><span data-stu-id="43b6b-105">We will look only at listing and changing running state for services, but you can get a list of Service cmdlets by using `Get-Help \*-Service`, and you can find information about each Service cmdlet by using `Get-Help <Cmdlet-Name>`, such as `Get-Help New-Service`.</span></span>

## <a name="getting-services"></a><span data-ttu-id="43b6b-106">Uzyskiwanie usługi</span><span class="sxs-lookup"><span data-stu-id="43b6b-106">Getting Services</span></span>

<span data-ttu-id="43b6b-107">Można uzyskać usługi na komputerze lokalnym lub zdalnym za pomocą `Get-Service` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="43b6b-107">You can get the services on a local or remote computer by using the `Get-Service` cmdlet.</span></span> <span data-ttu-id="43b6b-108">Podobnie jak w przypadku `Get-Process`przy użyciu `Get-Service` polecenie bez parametrów zwraca wszystkie usługi.</span><span class="sxs-lookup"><span data-stu-id="43b6b-108">As with `Get-Process`, using the `Get-Service` command without parameters returns all services.</span></span> <span data-ttu-id="43b6b-109">Możesz filtrować według nazwy, nawet przy użyciu gwiazdki jako symbolu wieloznacznego:</span><span class="sxs-lookup"><span data-stu-id="43b6b-109">You can filter by name, even using an asterisk as a wildcard:</span></span>

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="43b6b-110">Ponieważ nie zawsze jest oczywiste co to jest to prawdziwa nazwa usługi, może się okazać potrzebne do znalezienia usługi, według nazwy wyświetlanej.</span><span class="sxs-lookup"><span data-stu-id="43b6b-110">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="43b6b-111">Można to zrobić przy użyciu określonej nazwy, przy użyciu symboli wieloznacznych lub listę nazw wyświetlanych:</span><span class="sxs-lookup"><span data-stu-id="43b6b-111">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

```powershell
PS> Get-Service -DisplayName se*

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Running  SamSs              Security Accounts Manager
Running  seclogon           Secondary Logon
Stopped  ServiceLayer       ServiceLayer
Running  wscsvc             Security Center

PS> Get-Service -DisplayName ServiceLayer,Server

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="43b6b-112">Można użyć parametru ComputerName polecenia cmdlet Get-Service, można pobrać usługi na komputerach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="43b6b-112">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="43b6b-113">Parametr ComputerName akceptuje wiele wartości, jak i symboli wieloznacznych, Uzyskaj dostęp do usług na wielu komputerach przy użyciu jednego polecenia.</span><span class="sxs-lookup"><span data-stu-id="43b6b-113">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="43b6b-114">Na przykład następujące polecenie pobiera usług na komputerze zdalnym Serwer01.</span><span class="sxs-lookup"><span data-stu-id="43b6b-114">For example, the following command gets the services on the Server01 remote computer.</span></span>

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="43b6b-115">Pobieranie wymaganych i usług zależnych</span><span class="sxs-lookup"><span data-stu-id="43b6b-115">Getting Required and Dependent Services</span></span>

<span data-ttu-id="43b6b-116">Polecenie cmdlet Get-Service ma dwa parametry, które są przydatne w przypadku administrowania usługami.</span><span class="sxs-lookup"><span data-stu-id="43b6b-116">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="43b6b-117">Parametr DependentServices pobiera usług, które są zależne od usługi.</span><span class="sxs-lookup"><span data-stu-id="43b6b-117">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="43b6b-118">Parametr RequiredServices pobiera usług, od których zależy od tej usługi.</span><span class="sxs-lookup"><span data-stu-id="43b6b-118">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="43b6b-119">Te parametry są wyświetlane tylko wartości DependentServices i ServicesDependedOn (alias = RequiredServices) właściwości obiektu System.ServiceProcess.ServiceController, które upraszczają zwraca Get-Service, ale polecenia i upewnij się, wprowadzenie te informacje jest znacznie prostsze.</span><span class="sxs-lookup"><span data-stu-id="43b6b-119">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="43b6b-120">Następujące polecenie pobiera usługi, których wymaga usługa LanmanWorkstation.</span><span class="sxs-lookup"><span data-stu-id="43b6b-120">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="43b6b-121">Następujące polecenie pobiera usług, które wymagają usługa LanmanWorkstation.</span><span class="sxs-lookup"><span data-stu-id="43b6b-121">The following command gets the services that require the LanmanWorkstation service.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="43b6b-122">Możesz nawet uzyskać wszystkie usługi, które mają zależności.</span><span class="sxs-lookup"><span data-stu-id="43b6b-122">You can even get all services that have dependencies.</span></span> <span data-ttu-id="43b6b-123">Następujące polecenie właśnie to robi, a następnie używa polecenia cmdlet Format-Table Aby wyświetlić stan, Name, RequiredServices i DependentServices właściwości usług na komputerze.</span><span class="sxs-lookup"><span data-stu-id="43b6b-123">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="43b6b-124">Zatrzymywanie, uruchamianie, wstrzymywanie i ponowne uruchamianie usług</span><span class="sxs-lookup"><span data-stu-id="43b6b-124">Stopping, Starting, Suspending, and Restarting Services</span></span>

<span data-ttu-id="43b6b-125">Wszystkie polecenia cmdlet usługi mają tego samego formularza ogólne.</span><span class="sxs-lookup"><span data-stu-id="43b6b-125">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="43b6b-126">Usługi można określić nazwy pospolitej lub nazwę wyświetlaną i list i symboli wieloznacznych jako wartości.</span><span class="sxs-lookup"><span data-stu-id="43b6b-126">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="43b6b-127">Aby zatrzymać buforu wydruku, należy użyć:</span><span class="sxs-lookup"><span data-stu-id="43b6b-127">To stop the print spooler, use:</span></span>

```powershell
Stop-Service -Name spooler
```

<span data-ttu-id="43b6b-128">Aby uruchomić bufor wydruku, po jest zatrzymana, należy użyć:</span><span class="sxs-lookup"><span data-stu-id="43b6b-128">To start the print spooler after it is stopped, use:</span></span>

```powershell
Start-Service -Name spooler
```

<span data-ttu-id="43b6b-129">Aby wstrzymać bufor wydruku, należy użyć:</span><span class="sxs-lookup"><span data-stu-id="43b6b-129">To suspend the print spooler, use:</span></span>

```powershell
Suspend-Service -Name spooler
```

<span data-ttu-id="43b6b-130">`Restart-Service` Polecenia cmdlet działa w taki sam sposób jak inne polecenia cmdlet usługi, ale w tekście objaśniono niektóre przykłady bardziej złożonych dla niego.</span><span class="sxs-lookup"><span data-stu-id="43b6b-130">The `Restart-Service` cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="43b6b-131">Najprostsza używany należy określić nazwę usługi:</span><span class="sxs-lookup"><span data-stu-id="43b6b-131">In the simplest use, you specify the name of the service:</span></span>

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="43b6b-132">Zauważysz, Pobierz powtarzanych komunikat ostrzegawczy informujący o bufor wydruku, uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="43b6b-132">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="43b6b-133">Podczas wykonywania operacji usługi, która wymaga pewnego czasu, programu Windows PowerShell wyświetli powiadomienie, że nadal podejmuje ono próbę wykonania zadania.</span><span class="sxs-lookup"><span data-stu-id="43b6b-133">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="43b6b-134">Jeśli chcesz ponownie uruchomić wiele usług, możesz pobrać listę usług, filtrować je, a następnie wykonaj ponowne uruchomienie:</span><span class="sxs-lookup"><span data-stu-id="43b6b-134">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

```powershell
PS> Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service

WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
Restart-Service : Cannot stop service 'Logical Disk Manager (dmserver)' because
 it has dependent services. It can only be stopped if the Force flag is set.
At line:1 char:57
+ Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service <<<<
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
```

<span data-ttu-id="43b6b-135">Te polecenia cmdlet usługi ma parametr ComputerName, ale można je też uruchamiać na komputerze zdalnym za pomocą polecenia cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="43b6b-135">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="43b6b-136">Na przykład następujące polecenie uruchamia ponownie usługę Bufor na komputerze zdalnym Serwer01.</span><span class="sxs-lookup"><span data-stu-id="43b6b-136">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="43b6b-137">Ustawianie właściwości usługi</span><span class="sxs-lookup"><span data-stu-id="43b6b-137">Setting Service Properties</span></span>

<span data-ttu-id="43b6b-138">`Set-Service` Polecenie cmdlet zmienia właściwości usługi na komputerze lokalnym lub zdalnym.</span><span class="sxs-lookup"><span data-stu-id="43b6b-138">The `Set-Service` cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="43b6b-139">Ponieważ stan usługi jest właściwością, umożliwia to polecenie cmdlet uruchamianie, zatrzymywanie i wstrzymania usługi.</span><span class="sxs-lookup"><span data-stu-id="43b6b-139">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span>
<span data-ttu-id="43b6b-140">Polecenia cmdlet Set-Service ma również parametr StartupType, który pozwala zmienić typ uruchamiania usługi.</span><span class="sxs-lookup"><span data-stu-id="43b6b-140">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="43b6b-141">Aby użyć `Set-Service` na Windows Vista i nowszych wersjach systemu Windows, Otwórz program Windows PowerShell przy użyciu opcji "Uruchom jako administrator".</span><span class="sxs-lookup"><span data-stu-id="43b6b-141">To use `Set-Service` on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="43b6b-142">Aby uzyskać więcej informacji, zobacz [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="43b6b-142">For more information, see [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>

## <a name="see-also"></a><span data-ttu-id="43b6b-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43b6b-143">See Also</span></span>

- <span data-ttu-id="43b6b-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span><span class="sxs-lookup"><span data-stu-id="43b6b-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span></span>
- <span data-ttu-id="43b6b-145">[Ustawianie usługi [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="43b6b-145">[Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>
- <span data-ttu-id="43b6b-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span><span class="sxs-lookup"><span data-stu-id="43b6b-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span></span>
- <span data-ttu-id="43b6b-147">[Wstrzymywanie usługi [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span><span class="sxs-lookup"><span data-stu-id="43b6b-147">[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span></span>