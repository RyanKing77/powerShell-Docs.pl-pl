---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Pobieranie obiektów WMI Pobierz WmiObject
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
ms.openlocfilehash: 522822ac3ea6f08b20fa5af6c9accb48b01035d3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058254"
---
# <a name="getting-wmi-objects-get-wmiobject"></a>Pobieranie obiektów WMI (Get-WmiObject)

## <a name="getting-wmi-objects-get-wmiobject"></a>Pobieranie obiektów WMI (Get-WmiObject)

Instrumentacja zarządzania Windows (WMI) jest technologią podstawową do administrowania systemem Windows, ponieważ ujawnia on szerokiej gamy informacji w jednolity sposób. Ze względu na ilość WMI sprawia, że to możliwe, polecenia cmdlet programu Windows PowerShell do uzyskiwania dostępu do obiektów WMI **Get-WmiObject**, jest jednym z najbardziej przydatne do wykonywania faktyczną pracę. Firma Microsoft zamierza omówiono sposób używania Get-WmiObject dostępu do obiektów WMI, a następnie sposób wykorzystania obiektów WMI do wykonywania określonych czynności.

### <a name="listing-wmi-classes"></a>Lista klas usługi WMI

Pierwszy problem, który wystąpi większość użytkowników usługi WMI próbuje sprawdzić, co można zrobić z usługą WMI. Klasy usługi WMI Opisz zasoby, które mogą być zarządzane. Istnieją setki klasy usługi WMI, z których część zawiera dziesiątek, jak właściwości.

**Get-WmiObject** rozwiązuje ten problem, wprowadzając wykrywalny WMI. Można wyświetlić listę dostępnych klas usługi WMI na komputerze lokalnym, wpisując:

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

Możesz pobrać te same informacje z komputera zdalnego za pomocą parametru ComputerName określania nazwy komputera lub adres IP:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

Lista klas zwrócony przez komputer zdalny mogą się różnić od określonego systemu operacyjnego, który komputer działa i określonych rozszerzeń usługi WMI, dodane przez zainstalowanych aplikacji.

> [!NOTE]
> Podczas nawiązywania połączenia z komputerem zdalnym za pomocą Get-WmiObject, komputer zdalny musi działać usługa WMI, a następnie w domyślnej konfiguracji konta, którego używasz, musi być w lokalnej grupy administratorów na komputerze zdalnym. W systemie zdalnym nie trzeba mieć program Windows PowerShell. Dzięki temu można administrować systemy operacyjne, które nie jest uruchomiony program Windows PowerShell, ale mają usługę WMI.

Można nawet dołączyć nazwa_komputera podczas nawiązywania połączenia z systemu lokalnego. Można użyć nazwy komputera lokalnego, jego adres IP (lub na adres sprzężenia zwrotnego 127.0.0.1), lub stylu WMI "." jako nazwę komputera. Jeśli używasz programu Windows PowerShell na komputerze o nazwie Admin01 za pomocą adresu IP 192.168.1.90, następujące polecenia wszystkie zwróci klasy usługi WMI dla tego komputera:

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

Get-WmiObject używa przestrzeni nazw root/cimv2 domyślnie. Jeśli chcesz określić inny przestrzeni nazw usługi WMI, użyj **Namespace** parametru i określ odpowiednie ścieżki przestrzeni nazw:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a>Wyświetlanie szczegółów klasy usługi WMI

Jeśli znasz już nazwę klasy usługi WMI, można użyć go można pobrać informacji o natychmiast. Na przykład jeden z najczęściej używanych do odzyskiwania informacji o komputerze klasy usługi WMI jest **Win32_OperatingSystem**.

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

Mimo że firma Microsoft są wyświetlane wszystkie parametry, polecenia mogą być wyrażone w sposób bardziej zwięzły. **ComputerName** parametr nie jest konieczne, łącząc się z systemu lokalnego. Pokazujemy pokazują przypadek najbardziej ogólny i przypominać o parametrze. **Namespace** wartość domyślna to root/cimv2, a także można pominąć. Większość poleceń cmdlet pozwalają na koniec pominąć nazwy wspólnych parametrów. Przy użyciu Get-WmiObject, jeśli nazwa nie jest określony jako pierwszy parametr środowiska Windows PowerShell traktuje je jako **klasy** parametru. Oznacza to, że ostatnie polecenie może został wystawiony przez wpisanie:

```powershell
Get-WmiObject Win32_OperatingSystem
```

**Win32_OperatingSystem** klasa ma wiele właściwości więcej niż te są wyświetlane w tym miejscu. Get-Member można użyć, aby wyświetlić wszystkie właściwości. Właściwości klasy WMI są automatycznie dostępne, podobnie jak inne właściwości obiektu:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Get-Member -MemberType Property

   TypeName: System.Management.ManagementObject#root\cimv2\Win32_OperatingSyste
m

Name                                      MemberType Definition
----                                      ---------- ----------
__CLASS                                   Property   System.String __CLASS {...
...
BootDevice                                Property   System.String BootDevic...
BuildNumber                               Property   System.String BuildNumb...
...
```

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>Wyświetlanie właściwości innych niż domyślne za pomocą poleceń cmdlet Format

Jeśli chcesz, aby uzyskać informacje zawarte w **Win32_OperatingSystem** klasy, to znaczy nie są wyświetlane domyślnie, możesz wyświetlić ją za pomocą **Format** polecenia cmdlet. Na przykład jeśli chcesz wyświetlić dane dostępnej pamięci, wpisz:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> Symbole wieloznaczne pracować nazwy właściwości w **Format-Table**, więc elementu końcowego potoku można ograniczyć do `Format-Table -Property Total,Free`

Dane pamięci może być bardziej czytelny, jeśli należy sformatować jako listę, wpisując:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```
