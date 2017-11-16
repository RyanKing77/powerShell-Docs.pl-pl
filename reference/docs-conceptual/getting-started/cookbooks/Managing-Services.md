---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Zarządzanie usługami"
ms.assetid: 7a410e4d-514b-4813-ba0c-0d8cef88df31
ms.openlocfilehash: 9fd6c8bcfecc99756188409629ddf94b880aab91
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2017
---
# <a name="managing-services"></a><span data-ttu-id="160ae-103">Zarządzanie usługami</span><span class="sxs-lookup"><span data-stu-id="160ae-103">Managing Services</span></span>
<span data-ttu-id="160ae-104">Ma osiem rdzeni usługi poleceń cmdlet, przeznaczone dla wielu zadań usługi.</span><span class="sxs-lookup"><span data-stu-id="160ae-104">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="160ae-105">Zajmiemy tylko wyświetlanie i zmiana w stanie uruchomionym dla usługi, ale można uzyskać listę poleceń cmdlet usługi za pomocą **Get-Help \&#42;-usługi**, oraz informacje dotyczące poszczególnych poleceń cmdlet usługi można znaleźć przy użyciu **Get-Help < nazwa polecenia Cmdlet >**, takich jak **Get-Help nową usługę**.</span><span class="sxs-lookup"><span data-stu-id="160ae-105">We will look only at listing and changing running state for services, but you can get a list Service cmdlets by using **Get-Help \&#42;-Service**, and you can find information about each Service cmdlet by using **Get-Help<Cmdlet-Name>**, such as **Get-Help New-Service**.</span></span>

## <a name="getting-services"></a><span data-ttu-id="160ae-106">Pobieranie usług</span><span class="sxs-lookup"><span data-stu-id="160ae-106">Getting Services</span></span>
<span data-ttu-id="160ae-107">Można pobrać usługi na komputerze lokalnym lub zdalnym przy użyciu **Get-Service** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="160ae-107">You can get the services on a local or remote computer by using the **Get-Service** cmdlet.</span></span> <span data-ttu-id="160ae-108">Jak **Get-Process**za pomocą **Get-Service** polecenia bez parametrów zwraca wszystkie usługi.</span><span class="sxs-lookup"><span data-stu-id="160ae-108">As with **Get-Process**, using the **Get-Service** command without parameters returns all services.</span></span> <span data-ttu-id="160ae-109">Można filtrować według nazwy, nawet za pomocą gwiazdki jako symbolu wieloznacznego:</span><span class="sxs-lookup"><span data-stu-id="160ae-109">You can filter by name, even using an asterisk as a wildcard:</span></span>

```
PS> Get-Service -Name se*
Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="160ae-110">Ponieważ nie jest zawsze widoczne jest rzeczywistą nazwę usługi, może się okazać potrzebne do odnalezienia usług według nazwy wyświetlanej.</span><span class="sxs-lookup"><span data-stu-id="160ae-110">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="160ae-111">Można to zrobić przez nazwę, przy użyciu symboli wieloznacznych, lub listę nazw wyświetlanych:</span><span class="sxs-lookup"><span data-stu-id="160ae-111">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

```
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

<span data-ttu-id="160ae-112">Parametr ComputerName polecenia cmdlet Get-Service umożliwia uzyskiwanie usług na komputerach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="160ae-112">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="160ae-113">Parametr nazwa_komputera akceptuje wiele wartości i symboli wieloznacznych, aby usługi na wielu komputerach za pomocą jednego polecenia.</span><span class="sxs-lookup"><span data-stu-id="160ae-113">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="160ae-114">Na przykład następujące polecenie pobiera usług na komputerze zdalnym Serwer01.</span><span class="sxs-lookup"><span data-stu-id="160ae-114">For example, the following command gets the services on the Server01 remote computer.</span></span>

```
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="160ae-115">Pobieranie wymagane i usług zależnych</span><span class="sxs-lookup"><span data-stu-id="160ae-115">Getting Required and Dependent Services</span></span>
<span data-ttu-id="160ae-116">Polecenie cmdlet Get-Service ma dwa parametry, które są przydatne w przypadku usługi administracyjnej.</span><span class="sxs-lookup"><span data-stu-id="160ae-116">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="160ae-117">Parametr DependentServices pobiera usług, które są zależne od usługi.</span><span class="sxs-lookup"><span data-stu-id="160ae-117">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="160ae-118">Parametr RequiredServices pobiera usług, od których zależy od tej usługi.</span><span class="sxs-lookup"><span data-stu-id="160ae-118">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="160ae-119">Te parametry po prostu Wyświetl wartości DependentServices i ServicesDependedOn (alias = RequiredServices) właściwości obiektu System.ServiceProcess.ServiceController, które upraszczają zwraca Get-Service, ale polecenia i upewnij się, pobierania te informacje jest znacznie prostsze.</span><span class="sxs-lookup"><span data-stu-id="160ae-119">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="160ae-120">Polecenie pobiera usług, które usługa LanmanWorkstation wymaga.</span><span class="sxs-lookup"><span data-stu-id="160ae-120">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```
PS> Get-Service -Name LanmanWorkstation -RequiredServices
Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="160ae-121">Polecenie pobiera usługi, które wymagają LanmanWorkstation usługi.</span><span class="sxs-lookup"><span data-stu-id="160ae-121">The following command gets the services that require the LanmanWorkstation service.</span></span>

```
PS> Get-Service -Name LanmanWorkstation -DependentServices
Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="160ae-122">Możesz nawet uzyskać wszystkich usług, które są zależne.</span><span class="sxs-lookup"><span data-stu-id="160ae-122">You can even get all services that have dependencies.</span></span> <span data-ttu-id="160ae-123">Polecenie nie tylko dla niej, a następnie używa polecenia cmdlet Format-Table do wyświetlenia stanu, nazwa, RequiredServices i DependentServices właściwości usług na komputerze.</span><span class="sxs-lookup"><span data-stu-id="160ae-123">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```
Get-Service -Name * | where {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="160ae-124">Zatrzymywanie, uruchamianie, wstrzymywanie i ponowne uruchamianie usług</span><span class="sxs-lookup"><span data-stu-id="160ae-124">Stopping, Starting, Suspending, and Restarting Services</span></span>
<span data-ttu-id="160ae-125">Wszystkie polecenia cmdlet usługi ma tego samego formularza ogólne.</span><span class="sxs-lookup"><span data-stu-id="160ae-125">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="160ae-126">Usługi można określić nazwy pospolitej lub nazwę wyświetlaną i list i symboli wieloznacznych jako wartości.</span><span class="sxs-lookup"><span data-stu-id="160ae-126">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="160ae-127">Aby zatrzymać buforu wydruku, użyj polecenia:</span><span class="sxs-lookup"><span data-stu-id="160ae-127">To stop the print spooler, use:</span></span>

```
Stop-Service -Name spooler
```

<span data-ttu-id="160ae-128">Aby uruchomić bufor wydruku, po zatrzymaniu, należy użyć:</span><span class="sxs-lookup"><span data-stu-id="160ae-128">To start the print spooler after it is stopped, use:</span></span>

```
Start-Service -Name spooler
```

<span data-ttu-id="160ae-129">Aby wstrzymać bufor wydruku, należy użyć:</span><span class="sxs-lookup"><span data-stu-id="160ae-129">To suspend the print spooler, use:</span></span>

```
Suspend-Service -Name spooler
```

<span data-ttu-id="160ae-130">**Restart-Service** polecenia cmdlet działa w taki sam sposób jak inne polecenia cmdlet usługi, ale pokazano przykłady bardziej złożonych dla niego.</span><span class="sxs-lookup"><span data-stu-id="160ae-130">The **Restart-Service** cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="160ae-131">W przypadku użycia najprostszy należy określić nazwę usługi:</span><span class="sxs-lookup"><span data-stu-id="160ae-131">In the simplest use, you specify the name of the service:</span></span>

```
PS> Restart-Service -Name spooler
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="160ae-132">Można zauważyć, Pobierz powtórzony komunikat ostrzegawczy dotyczący buforu wydruku, uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="160ae-132">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="160ae-133">Podczas wykonywania operacji usługi, która wymaga pewnego czasu programu Windows PowerShell wyświetli powiadomienie, że nadal jest próba wykonania zadania.</span><span class="sxs-lookup"><span data-stu-id="160ae-133">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="160ae-134">Jeśli chcesz ponownie uruchomić wielu usług, możesz pobrać listę usług, ich filtrowania, a następnie wykonaj ponowne uruchomienie:</span><span class="sxs-lookup"><span data-stu-id="160ae-134">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

```
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

<span data-ttu-id="160ae-135">Te polecenia cmdlet usługi ma parametr ComputerName, ale uruchomienie na komputerze zdalnym za pomocą polecenia cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="160ae-135">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="160ae-136">Na przykład poniższe polecenie powoduje ponowne uruchomienie usługi buforu wydruku na komputerze zdalnym Serwer01.</span><span class="sxs-lookup"><span data-stu-id="160ae-136">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="160ae-137">Ustawienie właściwości usługi</span><span class="sxs-lookup"><span data-stu-id="160ae-137">Setting Service Properties</span></span>
<span data-ttu-id="160ae-138">Polecenia cmdlet Set-Service zmiany właściwości usługi na komputerze lokalnym lub zdalnym.</span><span class="sxs-lookup"><span data-stu-id="160ae-138">The Set-Service cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="160ae-139">Stan usługi jest właściwością, umożliwia to polecenie cmdlet uruchamianie, zatrzymywanie i wstrzymania usługi.</span><span class="sxs-lookup"><span data-stu-id="160ae-139">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span> <span data-ttu-id="160ae-140">Polecenia cmdlet Set-Service ma także parametr StartupType, który pozwala zmienić typ uruchomienia usługi.</span><span class="sxs-lookup"><span data-stu-id="160ae-140">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="160ae-141">Aby używać zestawu usługi systemu Windows Vista i nowszych wersjach systemu Windows, Otwórz program Windows PowerShell przy użyciu opcji "Uruchom jako administrator".</span><span class="sxs-lookup"><span data-stu-id="160ae-141">To use Set-Service on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="160ae-142">Aby uzyskać więcej informacji, zobacz [Set-Service [m2]](https://technet.microsoft.com/en-us/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="160ae-142">For more information, see [Set-Service [m2]](https://technet.microsoft.com/en-us/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>

## <a name="see-also"></a><span data-ttu-id="160ae-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="160ae-143">See Also</span></span>
- <span data-ttu-id="160ae-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span><span class="sxs-lookup"><span data-stu-id="160ae-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span></span>
- <span data-ttu-id="160ae-145">[Set-Service [m2]](https://technet.microsoft.com/en-us/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="160ae-145">[Set-Service [m2]](https://technet.microsoft.com/en-us/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>
- <span data-ttu-id="160ae-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span><span class="sxs-lookup"><span data-stu-id="160ae-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span></span>
- <span data-ttu-id="160ae-147">[Wstrzymanie usługi [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span><span class="sxs-lookup"><span data-stu-id="160ae-147">[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span></span>

