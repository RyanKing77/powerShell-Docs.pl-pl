---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Zarządzanie usługami
ms.assetid: 7a410e4d-514b-4813-ba0c-0d8cef88df31
ms.openlocfilehash: 81fd8802215da80ce22fa3fd4750b1df6efe8206
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086191"
---
# <a name="managing-services"></a>Zarządzanie usługami

Ma osiem rdzeni usługi poleceń cmdlet przeznaczone dla różnych zadań usługi. Przyjrzymy się tylko wyświetlanie i zmiana w stanie uruchomionym dla usługi, ale można uzyskać listę poleceń cmdlet usługi za pomocą `Get-Help \*-Service`, oraz informacje dotyczące każdego polecenia cmdlet usługi można znaleźć przy użyciu `Get-Help <Cmdlet-Name>`, takich jak `Get-Help New-Service`.

## <a name="getting-services"></a>Uzyskiwanie usługi

Można uzyskać usługi na komputerze lokalnym lub zdalnym za pomocą `Get-Service` polecenia cmdlet. Podobnie jak w przypadku `Get-Process`przy użyciu `Get-Service` polecenie bez parametrów zwraca wszystkie usługi. Możesz filtrować według nazwy, nawet przy użyciu gwiazdki jako symbolu wieloznacznego:

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

Ponieważ nie zawsze jest oczywiste co to jest to prawdziwa nazwa usługi, może się okazać potrzebne do znalezienia usługi, według nazwy wyświetlanej. Można to zrobić przy użyciu określonej nazwy, przy użyciu symboli wieloznacznych lub listę nazw wyświetlanych:

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

Można użyć parametru ComputerName polecenia cmdlet Get-Service, można pobrać usługi na komputerach zdalnych. Parametr ComputerName akceptuje wiele wartości, jak i symboli wieloznacznych, Uzyskaj dostęp do usług na wielu komputerach przy użyciu jednego polecenia. Na przykład następujące polecenie pobiera usług na komputerze zdalnym Serwer01.

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a>Pobieranie wymaganych i usług zależnych

Polecenie cmdlet Get-Service ma dwa parametry, które są przydatne w przypadku administrowania usługami. Parametr DependentServices pobiera usług, które są zależne od usługi. Parametr RequiredServices pobiera usług, od których zależy od tej usługi.

Te parametry są wyświetlane tylko wartości DependentServices i ServicesDependedOn (alias = RequiredServices) właściwości obiektu System.ServiceProcess.ServiceController, które upraszczają zwraca Get-Service, ale polecenia i upewnij się, wprowadzenie te informacje jest znacznie prostsze.

Następujące polecenie pobiera usługi, których wymaga usługa LanmanWorkstation.

```powershell
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

Następujące polecenie pobiera usług, które wymagają usługa LanmanWorkstation.

```powershell
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

Możesz nawet uzyskać wszystkie usługi, które mają zależności. Następujące polecenie właśnie to robi, a następnie używa polecenia cmdlet Format-Table Aby wyświetlić stan, Name, RequiredServices i DependentServices właściwości usług na komputerze.

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a>Zatrzymywanie, uruchamianie, wstrzymywanie i ponowne uruchamianie usług

Wszystkie polecenia cmdlet usługi mają tego samego formularza ogólne. Usługi można określić nazwy pospolitej lub nazwę wyświetlaną i list i symboli wieloznacznych jako wartości. Aby zatrzymać buforu wydruku, należy użyć:

```powershell
Stop-Service -Name spooler
```

Aby uruchomić bufor wydruku, po jest zatrzymana, należy użyć:

```powershell
Start-Service -Name spooler
```

Aby wstrzymać bufor wydruku, należy użyć:

```powershell
Suspend-Service -Name spooler
```

`Restart-Service` Polecenia cmdlet działa w taki sam sposób jak inne polecenia cmdlet usługi, ale w tekście objaśniono niektóre przykłady bardziej złożonych dla niego. Najprostsza używany należy określić nazwę usługi:

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

Zauważysz, Pobierz powtarzanych komunikat ostrzegawczy informujący o bufor wydruku, uruchamiania. Podczas wykonywania operacji usługi, która wymaga pewnego czasu, programu Windows PowerShell wyświetli powiadomienie, że nadal podejmuje ono próbę wykonania zadania.

Jeśli chcesz ponownie uruchomić wiele usług, możesz pobrać listę usług, filtrować je, a następnie wykonaj ponowne uruchomienie:

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

Te polecenia cmdlet usługi ma parametr ComputerName, ale można je też uruchamiać na komputerze zdalnym za pomocą polecenia cmdlet Invoke-Command. Na przykład następujące polecenie uruchamia ponownie usługę Bufor na komputerze zdalnym Serwer01.

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a>Ustawianie właściwości usługi

`Set-Service` Polecenie cmdlet zmienia właściwości usługi na komputerze lokalnym lub zdalnym. Ponieważ stan usługi jest właściwością, umożliwia to polecenie cmdlet uruchamianie, zatrzymywanie i wstrzymania usługi.
Polecenia cmdlet Set-Service ma również parametr StartupType, który pozwala zmienić typ uruchamiania usługi.

Aby użyć `Set-Service` na Windows Vista i nowszych wersjach systemu Windows, Otwórz program Windows PowerShell przy użyciu opcji "Uruchom jako administrator".

Aby uzyskać więcej informacji, zobacz [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)

## <a name="see-also"></a>Zobacz też

- [Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)
- [Ustawianie usługi [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)
- [Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)
- [Wstrzymywanie usługi [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)