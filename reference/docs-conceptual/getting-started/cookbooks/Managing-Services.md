---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Zarządzanie usługami"
ms.assetid: 7a410e4d-514b-4813-ba0c-0d8cef88df31
ms.openlocfilehash: 1e83566b1cb3c0c9c3c78a5877e52552ee51b0e9
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="managing-services"></a>Zarządzanie usługami
Ma osiem rdzeni usługi poleceń cmdlet, przeznaczone dla wielu zadań usługi. Zajmiemy tylko wyświetlanie i zmiana w stanie uruchomionym dla usługi, ale można uzyskać listę poleceń cmdlet usługi za pomocą **Get-Help \&#42;-usługi**, oraz informacje dotyczące poszczególnych poleceń cmdlet usługi można znaleźć przy użyciu **Get-Help < nazwa polecenia Cmdlet >**, takich jak **Get-Help nową usługę**.

## <a name="getting-services"></a>Pobieranie usług
Można pobrać usługi na komputerze lokalnym lub zdalnym przy użyciu **Get-Service** polecenia cmdlet. Jak **Get-Process**za pomocą **Get-Service** polecenia bez parametrów zwraca wszystkie usługi. Można filtrować według nazwy, nawet za pomocą gwiazdki jako symbolu wieloznacznego:

```
PS> Get-Service -Name se*
Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

Ponieważ nie jest zawsze widoczne jest rzeczywistą nazwę usługi, może się okazać potrzebne do odnalezienia usług według nazwy wyświetlanej. Można to zrobić przez nazwę, przy użyciu symboli wieloznacznych, lub listę nazw wyświetlanych:

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

Parametr ComputerName polecenia cmdlet Get-Service umożliwia uzyskiwanie usług na komputerach zdalnych. Parametr nazwa_komputera akceptuje wiele wartości i symboli wieloznacznych, aby usługi na wielu komputerach za pomocą jednego polecenia. Na przykład następujące polecenie pobiera usług na komputerze zdalnym Serwer01.

```
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a>Pobieranie wymagane i usług zależnych
Polecenie cmdlet Get-Service ma dwa parametry, które są przydatne w przypadku usługi administracyjnej. Parametr DependentServices pobiera usług, które są zależne od usługi. Parametr RequiredServices pobiera usług, od których zależy od tej usługi.

Te parametry po prostu Wyświetl wartości DependentServices i ServicesDependedOn (alias = RequiredServices) właściwości obiektu System.ServiceProcess.ServiceController, które upraszczają zwraca Get-Service, ale polecenia i upewnij się, pobierania te informacje jest znacznie prostsze.

Polecenie pobiera usług, które usługa LanmanWorkstation wymaga.

```
PS> Get-Service -Name LanmanWorkstation -RequiredServices
Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

Polecenie pobiera usługi, które wymagają LanmanWorkstation usługi.

```
PS> Get-Service -Name LanmanWorkstation -DependentServices
Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

Możesz nawet uzyskać wszystkich usług, które są zależne. Polecenie nie tylko dla niej, a następnie używa polecenia cmdlet Format-Table do wyświetlenia stanu, nazwa, RequiredServices i DependentServices właściwości usług na komputerze.

```
Get-Service -Name * | where {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a>Zatrzymywanie, uruchamianie, wstrzymywanie i ponowne uruchamianie usług
Wszystkie polecenia cmdlet usługi ma tego samego formularza ogólne. Usługi można określić nazwy pospolitej lub nazwę wyświetlaną i list i symboli wieloznacznych jako wartości. Aby zatrzymać buforu wydruku, użyj polecenia:

```
Stop-Service -Name spooler
```

Aby uruchomić bufor wydruku, po zatrzymaniu, należy użyć:

```
Start-Service -Name spooler
```

Aby wstrzymać bufor wydruku, należy użyć:

```
Suspend-Service -Name spooler
```

**Restart-Service** polecenia cmdlet działa w taki sam sposób jak inne polecenia cmdlet usługi, ale pokazano przykłady bardziej złożonych dla niego. W przypadku użycia najprostszy należy określić nazwę usługi:

```
PS> Restart-Service -Name spooler
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

Można zauważyć, Pobierz powtórzony komunikat ostrzegawczy dotyczący buforu wydruku, uruchamiania. Podczas wykonywania operacji usługi, która wymaga pewnego czasu programu Windows PowerShell wyświetli powiadomienie, że nadal jest próba wykonania zadania.

Jeśli chcesz ponownie uruchomić wielu usług, możesz pobrać listę usług, ich filtrowania, a następnie wykonaj ponowne uruchomienie:

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

Te polecenia cmdlet usługi ma parametr ComputerName, ale uruchomienie na komputerze zdalnym za pomocą polecenia cmdlet Invoke-Command. Na przykład poniższe polecenie powoduje ponowne uruchomienie usługi buforu wydruku na komputerze zdalnym Serwer01.

```
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a>Ustawienie właściwości usługi
Polecenia cmdlet Set-Service zmiany właściwości usługi na komputerze lokalnym lub zdalnym. Stan usługi jest właściwością, umożliwia to polecenie cmdlet uruchamianie, zatrzymywanie i wstrzymania usługi. Polecenia cmdlet Set-Service ma także parametr StartupType, który pozwala zmienić typ uruchomienia usługi.

Aby używać zestawu usługi systemu Windows Vista i nowszych wersjach systemu Windows, Otwórz program Windows PowerShell przy użyciu opcji "Uruchom jako administrator".

Aby uzyskać więcej informacji, zobacz [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)

## <a name="see-also"></a>Zobacz też
- [Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)
- [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)
- [Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)
- [Wstrzymanie usługi [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)

