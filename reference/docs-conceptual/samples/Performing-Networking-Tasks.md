---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Wykonywanie zadań w sieci
ms.assetid: a43cc55f-70c1-45c8-9467-eaad0d57e3b5
ms.openlocfilehash: 250ae6e5f6431ce659b3600188d7e30e501c3247
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293133"
---
# <a name="performing-networking-tasks"></a>Wykonywanie zadań w sieci

Ponieważ protokół TCP/IP jest najczęściej używany protokół sieciowy, większości zadań administracyjnych protokołu sieciowego niskiego poziomu obejmują TCP/IP. W tej sekcji używamy programu Windows PowerShell i usługi WMI do wykonywania tych zadań.

## <a name="listing-ip-addresses-for-a-computer"></a>Lista adresów IP dla komputera

Aby uzyskać wszystkie adresy IP używane na komputerze lokalnym, użyj następującego polecenia:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

Dane wyjściowe tego polecenia różni się od większości listy właściwości, ponieważ są ujęte w nawiasy klamrowe:

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

Aby zrozumieć, dlaczego nawiasy klamrowe są wyświetlane, należy użyć polecenia cmdlet Get-Member zbadanie **IPAddress** właściwości:

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

Właściwość adres IP dla każdej karty sieciowej jest faktycznie tablicą. Nawiasy klamrowe w definicji wskazują, że **IPAddress** nie **System.String** wartość, ale tablica **System.String** wartości.

## <a name="listing-ip-configuration-data"></a>Wyświetlanie danych konfiguracji protokołu IP

Aby wyświetlić szczegółowe danych konfiguracji protokołu IP dla każdej karty sieciowej, użyj następującego polecenia:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

Ekran domyślny dla obiektu konfiguracji karty sieciowej jest bardzo ograniczonym zestawie dostępne informacje. Szczegóły inspekcji i rozwiązywanie problemów należy użyć Select-Object lub formatowania polecenia cmdlet, takich jak listy Format do określania właściwości, które mają być wyświetlane.

Jeśli nie jesteś zainteresowany właściwości IPX lub usługi WINS, prawdopodobnie w przypadku nowoczesnych sieci TCP/IP — można użyć parametru ExcludeProperty Select-Object spowoduje ukrycie właściwości z nazwami, które zaczynają się od "WINS" lub "IPX:"

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

To polecenie zwraca szczegółowe informacje na temat usługi DHCP, DNS, routingu i inne drobne właściwości konfiguracji adresu IP.

## <a name="pinging-computers"></a>Pingowanie komputerów

Można wykonywać proste polecenie ping względem komputer używa przez **Win32_PingStatus**. Poniższe polecenie wykonuje polecenie ping, ale zwraca długich danych wyjściowych:

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

Bardziej użyteczny, formularz podsumowanie wyświetlania właściwości adres, czas odpowiedzi i StatusCode, tak jak w przypadku następującego polecenia. Parametr Autosize Format-Table zmienia rozmiar kolumn tabeli tak, aby prawidłowo wyświetlane w programie Windows PowerShell.

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

StatusCode 0 oznacza pomyślne polecenie ping.

Za pomocą tablicy na polecenie ping wiele komputerów za pomocą jednego polecenia. Ponieważ istnieje więcej niż jeden adres, użyj **ForEach-Object** wysłać polecenie ping każdego adresu oddzielnie:

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Można użyć tego samego formatu polecenia na polecenie ping, wszystkie komputery w podsieci, takich jak sieć VPN, która używa numeru sieci 192.168.1.0 i maskę podsieci klasy C standard (255.255.255.0)., są tylko adresy z zakresu od 192.168.1.1 do 192.168.1.254 wiarygodnych adresów lokalnych (0 jest zawsze zarezerwowane dla numer sieci i 255 jest adresem emisji podsieci).

Do reprezentowania tablicy liczb od 1 do 254 w programie Windows PowerShell, użyj instrukcji **1..254.** Ping pełną podsieci mogą być wykonywane przez generowanie tablicy, a następnie dodanie wartości do częściowego adresu w instrukcji ping:

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Należy pamiętać, że ta technika generowania zakres adresów może służyć także w innym miejscu. W ten sposób można wygenerować kompletny zestaw adresów:

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a>Trwa pobieranie właściwości karty sieciowej

Wcześniej w tym podręczniku użytkownika, wspomnieliśmy, że można pobrać właściwości ogólne konfiguracji za pomocą **Win32_NetworkAdapterConfiguration**. Chociaż nie jest właściwie informacji protokołu TCP/IP, informacje o karty sieciowej, takich jak MAC adresy i typy karty mogą być przydatne dla zrozumienia, co się dzieje z komputerem. Aby uzyskać podsumowanie tych informacji, użyj następującego polecenia:

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a>Przypisywanie domeny DNS dla karty sieciowej

Aby przypisać domeny DNS do rozpoznawania nazw automatycznego, należy użyć **SetDNSDomain pozwala ustawić Win32_NetworkAdapterConfiguration** metody. Domeny DNS dla każdej konfiguracji karty sieciowej możesz przypisać niezależnie, dlatego musisz użyć **ForEach-Object** instrukcję, aby przypisać domeny do każdej karty sieciowej:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

Filtrowanie instrukcji "IPEnabled = $true" jest to konieczne, ponieważ nawet w przypadku sieci, która używa tylko protokołu TCP/IP, kilka konfiguracji kart sieciowych na komputerze są prawdziwe TCP/IP karty; są elementy ogólne oprogramowania, obsługa RAS, PPTP, QoS i innych usług dla wszystkich kart sieciowych i dlatego nie ma adresu swoich własnych.

Polecenia można filtrować przy użyciu **Where-Object** zamiast przy użyciu polecenia cmdlet **Get-WmiObject** filtru.

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a>Wykonywanie zadań konfiguracyjnych DHCP

Modyfikowanie szczegóły DHCP polega na pracę z zestawem kart sieciowych, podobnie jak konfiguracji DNS. Istnieje kilka różnych akcji, które można wykonać przy użyciu usługi WMI, a firma Microsoft będzie przejść przez niektóre typowe z nich.

### <a name="determining-dhcp-enabled-adapters"></a>Określanie karty obsługujących protokół DHCP

Aby znaleźć kart sieciowych obsługujących protokół DHCP na komputerze, użyj następującego polecenia:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

Aby wykluczyć kart z problemów z konfiguracją adresów IP, możesz pobrać tylko kart sieciowych obsługujących protokół IP:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

### <a name="retrieving-dhcp-properties"></a>Trwa pobieranie właściwości DHCP

Ponieważ właściwości związanych z usługą DHCP dla karty zwykle zaczyna się od "DHCP", można użyć parametru właściwości Format-Table, aby wyświetlić tylko te właściwości:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a>Włączenie protokołu DHCP na poszczególnych kartach

Aby włączyć DHCP dla wszystkich kart sieciowych, użyj następującego polecenia:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

Możesz użyć **filtru** instrukcji "IPEnabled = $true i DHCPEnabled = $false" w celu uniknięcia włączania protokołu DHCP, gdy jest włączony, ale pominięcie tego kroku nie będą powodować błędy.

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a>Zwalnianie i odnawianie dzierżawy DHCP dla określonych kart

**Win32_NetworkAdapterConfiguration** klasa ma **ReleaseDHCPLease** i **RenewDHCPLease** metody. Oba są używane w taki sam sposób. Ogólnie rzecz biorąc należy użyć tych metod, jeśli potrzebujesz zwolnić lub odnowić adresów dla karty w określonej podsieci. Najprostszym sposobem kart filtru w podsieci jest wybranie konfiguracji karty sieciowej, korzystających z bramy dla tej podsieci. Na przykład następujące polecenie zwalnia wszystkie dzierżawy DHCP na kartach na komputerze lokalnym, które są uzyskiwane dzierżawy DHCP z 192.168.1.254:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

Jedyna zmiana odnowienia dzierżawy DHCP jest użycie **RenewDHCPLease** zamiast metody **ReleaseDHCPLease** metody:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> Korzystając z tych metod na komputerze zdalnym, należy pamiętać, że można utraty dostępu do systemu zdalnego. Jeśli łączysz się je za pośrednictwem karty wydana lub odnowionej dzierżawy.

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a>Zwalnianie i odnawianie dzierżawy DHCP na wszystkich kartach

Możesz wykonać globalnej wersji adres DHCP lub odnowienia na wszystkich kartach przy użyciu **Win32_NetworkAdapterConfiguration** metod **ReleaseDHCPLeaseAll** i **RenewDHCPLeaseAll** . Jednak polecenia należy zastosować do klasy usługi WMI, a nie dla określonej karty, ponieważ przy zwalnianiu i globalnie odnawianie dzierżawy jest wykonywana na tej klasy, a nie na określonej karty.

Wyświetlanie listy wszystkich klas usługi WMI, a następnie wybierając odpowiednią klasę o nazwie można uzyskać odwołanie do klasy usługi WMI, zamiast wystąpienia klasy. Na przykład poniższe polecenie zwraca klasy Win32_NetworkAdapterConfiguration:

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

Można traktować cały polecenia jako klasy, a następnie wywołaj **ReleaseDHCPAdapterLease** metody na nim. W poniższym poleceniu nawiasy otaczające **Get-WmiObject** i **Where-Object** elementów potoku bezpośrednie programu Windows PowerShell, aby ich oceny na pierwsze:

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

Można użyć tego samego formatu polecenie do wywołania **RenewDHCPLeaseAll** metody:

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a>Utworzenie udziału sieciowego

Aby utworzyć udział sieciowy, użyj **tworzenie Win32_Share** metody:

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

Można również utworzyć przy użyciu udziału **polecenie net share** w programie Windows PowerShell:

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a>Usuwanie udziału sieciowego

Można usunąć udziału sieciowego przy użyciu **Win32_Share**, ale proces różni się nieco od tworzenia udziału, ponieważ trzeba pobrać określonego udziału do usunięcia, a nie **Win32_Share** Klasa. Poniższa instrukcja umożliwia usunięcie udziału "TempShare":

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

**Polecenie net share** działa także:

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a>Łączenie z dyskiem sieciowym dostępnym Windows

**New PSDrive** poleceń cmdlet tworzy dysk programu Windows PowerShell, ale dyski utworzone w ten sposób są dostępne tylko dla programu Windows PowerShell. Aby utworzyć nowego dysku sieciowym, można użyć **WScript.Network** obiektu COM. Następujące polecenie mapuje udziału \\ \\FPS01\\użytkownikom na dysku lokalnym B:

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

**Net użyj** polecenie działa również:

```powershell
net use B: \\FPS01\users
```

Dyski mapowane z oboma **WScript.Network** lub polecenie net use są natychmiast dostępne dla programu Windows PowerShell.