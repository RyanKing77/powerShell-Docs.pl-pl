---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Wykonywanie zadań w sieci
ms.assetid: a43cc55f-70c1-45c8-9467-eaad0d57e3b5
ms.openlocfilehash: 64c57c95a70bc4cad4b695a59d96673ed18afdf4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="performing-networking-tasks"></a>Wykonywanie zadań w sieci

Ponieważ protokół TCP/IP jest najczęściej używany protokół sieciowy, większości zadań administracyjnych protokołu niskiego poziomu sieci obejmują TCP/IP. W tej sekcji używamy środowiska Windows PowerShell i usługi WMI do wykonywania tych zadań.

### <a name="listing-ip-addresses-for-a-computer"></a>Lista adresów IP dla komputera

Aby uzyskać wszystkie adresy IP, używana na komputerze lokalnym, użyj następującego polecenia:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

Dane wyjściowe tego polecenia różni się od większości list właściwości, ponieważ są ujęte w nawiasy klamrowe:

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

Aby zrozumieć, dlaczego nawiasy klamrowe są wyświetlane, należy użyć polecenia cmdlet Get-członka do sprawdzenia **IPAddress** właściwości:

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

Właściwość adres IP dla każdej karty sieciowej jest rzeczywiście tablicy. Nawiasy klamrowe w definicji wskazują, że **IPAddress** nie jest **System.String** wartość, ale tablica **System.String** wartości.

### <a name="listing-ip-configuration-data"></a>Wyświetlanie danych konfiguracji protokołu IP

Aby wyświetlić szczegółowe danych konfiguracji protokołu IP dla każdej karty sieciowej, użyj następującego polecenia:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

Ekran domyślny dla obiekt konfiguracji karty sieciowej jest bardzo ograniczonego zestawu dostępnych informacji. Szczegółowe inspekcji i rozwiązywania problemów Użyj Select-Object lub formatowania polecenia cmdlet, takich jak lista formatów, aby określić właściwości, które mają być wyświetlane.

Jeśli nie jesteś zainteresowany właściwości IPX lub usługi WINS — prawdopodobnie w przypadku nowoczesnych sieci TCP/IP — parametr ExcludeProperty Select-Object umożliwia ukrywanie właściwości za pomocą nazw, które zaczynają się od "WINS" lub "IPX:"

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

To polecenie zwraca szczegółowe informacje o routing DHCP, DNS, a inne pomocnicze właściwości konfiguracji adresu IP.

### <a name="pinging-computers"></a>Badanie komputerów

Można wykonywać proste ping względem wykorzystywany przez **Win32_PingStatus**. Polecenie wykonuje polecenie ping, ale zwraca długich danych wyjściowych:

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

Bardziej użyteczne formularz podsumowanie wyświetlenie właściwości adresu, czas odpowiedzi i StatusCode wygenerowane za pomocą następującego polecenia. Parametr Autosize Format-Table zmienia rozmiar kolumn tabeli, aby prawidłowo wyświetlić w programie Windows PowerShell.

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

StatusCode 0 oznacza pomyślne polecenie ping.

Tablica służy do wielu komputerów za pomocą jednego polecenia ping. Ponieważ więcej niż jeden adres, użyj **ForEach-Object** na polecenie ping każdy adres oddzielnie:

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Można użyć tego samego formatu polecenia na polecenie ping, wszystkie komputery w podsieci, takich jak sieć VPN, która używa numeru sieci 192.168.1.0 i maski podsieci klasy C standard (255.255.255.0)., są tylko adresy z zakresu od 192.168.1.1 za pośrednictwem 192.168.1.254 prawnie adresów lokalnych (0 jest zawsze zarezerwowane dla numeru sieci i 255 jest adresem emisji podsieci).

Do reprezentowania tablicy liczb od 1 do 254 w programie Windows PowerShell, użyj instrukcji **1..254.** Ping pełną podsieci może zostać wykonana przez generowanie tablicy, a następnie dodanie wartości do częściowego adresu w instrukcji ping:

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Należy pamiętać o tym, gdzie indziej również używana ta technika generowania zakres adresów. W ten sposób można wygenerować pełny zestaw adresów:

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

### <a name="retrieving-network-adapter-properties"></a>Podczas pobierania właściwości karty sieciowej

Wcześniej w tym podręczniku użytkownika, wspomniano, że można pobrać właściwości ogólne konfiguracji za pomocą **Win32_NetworkAdapterConfiguration**. Chociaż nie wyłącznie informacje TCP/IP adresów informacje dotyczące karty sieciowej, takich jak MAC, i typy karty mogą być przydatne dla zrozumienia, co dzieje się z komputerem. Aby uzyskać podsumowanie informacji, użyj następującego polecenia:

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

### <a name="assigning-the-dns-domain-for-a-network-adapter"></a>Przypisywanie domeny DNS dla karty sieciowej

Aby przypisać domeny DNS do rozpoznawania nazw automatyczne, użyj **SetDNSDomain pozwala ustawić Win32_NetworkAdapterConfiguration** metody. Ponieważ niezależnie przypisać domenę DNS dla każdej konfiguracji karty sieciowej, należy użyć **ForEach-Object** instrukcji, aby przypisać domeny do każdej karty:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

Filtrowanie instrukcji "IPEnabled = $true" jest to konieczne, ponieważ nawet w sieci, która wykorzystuje tylko protokół TCP/IP, nie są kilka konfiguracji kart sieciowych na komputerze, na wartość true, kart TCP/IP; są elementy oprogramowania ogólne obsługi RAS, PPTP, QoS i innych usług dla wszystkich kart sieciowych i dlatego nie ma adresu we własnym.

Polecenie można filtrować przy użyciu **Where-Object** polecenia cmdlet, zamiast **Get-WmiObject** filtru.

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

### <a name="performing-dhcp-configuration-tasks"></a>Wykonywanie zadań konfiguracji DHCP

Modyfikowanie szczegóły DHCP polega na stosowaniu zestaw kart sieciowych, podobnie jak konfiguracja DNS. Istnieje kilka różnych akcji, które można wykonać za pomocą usługi WMI, a niektóre z najczęściej spotykane firma Microsoft będzie kroków.

#### <a name="determining-dhcp-enabled-adapters"></a>Określanie karty obsługujących protokół DHCP

Aby znaleźć kart sieciowych obsługujących protokół DHCP na komputerze, użyj następującego polecenia:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

Aby wykluczyć kart z problemów z konfiguracją IP, można pobrać tylko kart sieciowych obsługujących protokół IP:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

#### <a name="retrieving-dhcp-properties"></a>Podczas pobierania właściwości DHCP

Ponieważ związanych z usługą DHCP właściwości kart sieciowych zwykle zaczyna się od "DHCP", można użyć parametru właściwości formatu tabeli do wyświetlenia tylko właściwości:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

#### <a name="enabling-dhcp-on-each-adapter"></a>Włączanie DHCP dla każdej karty

Aby włączyć protokół DHCP na wszystkich kartach, użyj następującego polecenia:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

Można użyć **filtru** instrukcji "IPEnabled = $true i DHCPEnabled = $false" Aby uniknąć włączania DHCP, na którym jest już włączony, ale pominięcie tego kroku nie będą powodować błędy.

#### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a>Zwalnianie i odnawiania dzierżawy DHCP dla określonych kart

**Win32_NetworkAdapterConfiguration** klasa ma **ReleaseDHCPLease** i **RenewDHCPLease** metody. Są używane w taki sam sposób. Ogólnie rzecz biorąc należy użyć tych metod, jeśli należy zwolnić lub odnowić adresów dla karty w określonej podsieci. Najprostszym sposobem kart filtru w podsieci jest możliwość konfiguracji karty sieciowej, które używają bramy dla tej podsieci. Na przykład następujące polecenie zwalnia wszystkie dzierżawy DHCP dla kart na komputerze lokalnym, które są uzyskiwane dzierżawy DHCP z 192.168.1.254:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

Jedyna różnica dla odnawiania dzierżawy DHCP jest użycie **RenewDHCPLease** zamiast metody **ReleaseDHCPLease** metody:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> Korzystając z tych metod na komputerze zdalnym, należy pamiętać, że można stracić dostęp do systemu zdalnego połączenia do niego za pośrednictwem karty dzierżawy zwolniony lub odnowionego.

#### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a>Zwalnianie i odnawiania dzierżawy DHCP na wszystkich kartach

Na wszystkich kartach mogą wykonywać globalne wersje adresów DHCP lub odnowienia za pomocą **Win32_NetworkAdapterConfiguration** metod, **ReleaseDHCPLeaseAll** i **RenewDHCPLeaseAll** . Jednak zastosować polecenia do klasy usługi WMI, a nie dla określonej karty, ponieważ zwalniania i odnawiania dzierżawy globalnie jest wykonywana na tej klasy, a nie na określonej karty.

Odwołanie do klasy usługi WMI, zamiast wystąpień klasy, można uzyskać listę wszystkich klas usługi WMI, a następnie zaznaczając odpowiednią klasę według nazwy. Na przykład poniższe polecenie zwraca klasy Win32_NetworkAdapterConfiguration:

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

Można traktować jako klasa całego polecenia, a następnie wywołaj **ReleaseDHCPAdapterLease** dla niego metodę. W poniższym poleceniu nawiasy otaczające **Get-WmiObject** i **Where-Object** środowiska Windows PowerShell można obliczyć je najpierw bezpośrednie elementy potoku:

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

W tym samym formacie polecenia można użyć do wywołania **RenewDHCPLeaseAll** metody:

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

### <a name="creating-a-network-share"></a>Utworzenie udziału sieciowego

Aby utworzyć udział sieciowy, użyj **utworzyć Win32_Share** metody:

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

Można również utworzyć udział za pomocą **polecenie net share** w programie Windows PowerShell:

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

### <a name="removing-a-network-share"></a>Usuwanie udziału sieciowego

Możesz usunąć udział sieciowy z **Win32_Share**, ale proces jest nieco inne niż Tworzenie udziału, ponieważ należy do pobrania określonego udziału do usunięcia, a nie **Win32_Share** Klasa. Następująca instrukcja usuwa udział "TempShare":

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

**Polecenie net share** działa również:

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

### <a name="connecting-a-windows-accessible-network-drive"></a>Łączenie dostępny dysk sieciowy systemu Windows

**Elementu PSDrive nowy** poleceń cmdlet tworzy dysk programu Windows PowerShell, ale dyski utworzone w ten sposób są dostępne tylko dla programu Windows PowerShell. Aby utworzyć nowego dysku sieciowego, można użyć **WScript.Network** obiektu COM. Polecenie mapuje udział \\ \\FPS01\\użytkownikom na lokalnym dysku B:

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

**Net użyj** polecenie działa również:

```powershell
net use B: \\FPS01\users
```

Dyski mapowane przy użyciu jednej **WScript.Network** lub polecenie net use są natychmiast dostępne dla środowiska Windows PowerShell.