---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Pobieranie obiektów WMI pobrać WmiObject"
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
ms.openlocfilehash: fbaac2797dd62eb03a2be581b3b5f8be6dafc0ad
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="getting-wmi-objects-get-wmiobject"></a>Pobieranie obiektów WMI (Get-WmiObject)

## <a name="getting-wmi-objects-get-wmiobject"></a>Pobieranie obiektów WMI (Get-WmiObject)
Instrumentacja zarządzania Windows (WMI) jest technologią podstawową do administrowania systemem Windows, ponieważ ujawnia on również szereg informacji w jednolity sposób. Ze względu na ilość WMI sprawia, że to możliwe, polecenia cmdlet programu Windows PowerShell do uzyskiwania dostępu do obiektów WMI **Get-WmiObject**, jest jednym z najbardziej przydatne do wykonywania pracy prawdziwe. Zamierzamy omówiono sposób użycia Get-WmiObject dostęp do obiektów WMI, a następnie jak wykonywanie określonych czynności, za pomocą obiektów WMI.

### <a name="listing-wmi-classes"></a>Listę klas usługi WMI
Pierwszy problem napotykanych przez większość użytkowników usługi WMI próbuje sprawdzić, co można zrobić za pomocą usługi WMI. Klasy WMI, które opisują zasoby, które mogą być zarządzane. Brak setki klas WMI, z których część zawiera dziesiątki właściwości.

**Get-WmiObject** rozwiązano ten problem, tworząc wykrywalny WMI. Można wyświetlić listę dostępnych klas usługi WMI na komputerze lokalnym, wpisując:

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

Można pobrać te same informacje z komputera zdalnego za pomocą parametr ComputerName, określając nazwę komputera lub adres IP:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

Na liście klasy zwrócony przez komputery zdalne mogą się różnić z powodu określonego systemu operacyjnego na komputerze jest zainstalowany i określonych rozszerzeń WMI dodane przez zainstalowanych aplikacji.

> [!NOTE]
> Podczas nawiązywania połączenia z komputerem zdalnym za pomocą Get-WmiObject, komputer zdalny musi być uruchomiony WMI, a następnie w obszarze Konfiguracja domyślna konta, którego używasz, musi być w lokalnej grupy administratorów na komputerze zdalnym. System zdalny musi mieć zainstalowane środowisko Windows PowerShell. Dzięki temu można administrować systemów operacyjnych, które nie są uruchomione środowiska Windows PowerShell, ale masz usługę WMI.

Właściwość ComputerName można uwzględnić nawet podczas nawiązywania połączenia systemu lokalnego. Możesz użyć nazwy komputera lokalnego, adres IP (lub adres sprzężenia zwrotnego 127.0.0.1), lub WMI-style "." jako nazwy komputera. Jeśli używasz programu Windows PowerShell na komputerze o nazwie Admin01 o adresie IP 192.168.1.90, następujące polecenia wszystkie zwróci klasy usługi WMI dla tego komputera:

```
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

Get-WmiObject domyślnie używa głównego/cimv2 przestrzeni nazw. Jeśli chcesz określić inny obszar nazw usługi WMI, użyj **Namespace** parametru i określ odpowiednie ścieżki przestrzeni nazw:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a>Wyświetlanie szczegółów klasy usługi WMI
Jeśli znasz już nazwę klasy usługi WMI, można użyć go można uzyskać informacji o natychmiast. Na przykład jednej z klas WMI często używane do pobierania informacji o komputerze jest **Win32_OperatingSystem**.

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

Mimo że firma Microsoft są wyświetlane wszystkie parametry, polecenie może być wyrażona w sposób bardziej zwięzły. **ComputerName** parametru nie jest konieczne, łącząc się z systemu lokalnego. Zostanie przedstawiony pokazują przypadku najbardziej ogólnym i przypominać o parametrze. **Namespace** domyślnie główny/cimv2 i można również pominąć. Na koniec większości poleceń cmdlet umożliwiają pominąć nazwę typowych parametrów. Z Get-WmiObject, jeśli nie określono nazwy dla pierwszego parametru środowiska Windows PowerShell traktuje ją jako **klasy** parametru. Oznacza to, że ostatnie polecenie może wystawiony przez wpisanie:

```
Get-WmiObject Win32_OperatingSystem
```

**Win32_OperatingSystem** klasa ma wiele właściwości więcej niż wyświetlone tutaj. Aby wyświetlić wszystkie właściwości, można użyć elementu członkowskiego Get. Właściwości klasy WMI są automatycznie dostępne, podobnie jak inne właściwości obiektu:

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>Wyświetlanie właściwości innych niż domyślne za pomocą poleceń cmdlet formatu
Jeśli chcesz, aby informacje zawarte w **Win32_OperatingSystem** klasy, czyli nie jest wyświetlany domyślnie, można je wyświetlić przy użyciu **Format** polecenia cmdlet. Na przykład jeśli chcesz wyświetlić dane dostępnej pamięci, wpisz:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> Symbole wieloznaczne pracować z nazwy właściwości w **Format-Table**, dlatego elementu końcowego potoku można zmniejszyć do  **Format-Table-właściwość całkowita*, wolne*

Dane pamięci mogą być bardziej czytelny, jeśli zostanie sformatowany jako listy, wpisując:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```

