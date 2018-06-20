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
ms.locfileid: "30954130"
---
# <a name="performing-networking-tasks"></a><span data-ttu-id="eb667-103">Wykonywanie zadań w sieci</span><span class="sxs-lookup"><span data-stu-id="eb667-103">Performing Networking Tasks</span></span>

<span data-ttu-id="eb667-104">Ponieważ protokół TCP/IP jest najczęściej używany protokół sieciowy, większości zadań administracyjnych protokołu niskiego poziomu sieci obejmują TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="eb667-104">Because TCP/IP is the most commonly used network protocol, most low-level network protocol administration tasks involve TCP/IP.</span></span> <span data-ttu-id="eb667-105">W tej sekcji używamy środowiska Windows PowerShell i usługi WMI do wykonywania tych zadań.</span><span class="sxs-lookup"><span data-stu-id="eb667-105">In this section, we use Windows PowerShell and WMI to do these tasks.</span></span>

### <a name="listing-ip-addresses-for-a-computer"></a><span data-ttu-id="eb667-106">Lista adresów IP dla komputera</span><span class="sxs-lookup"><span data-stu-id="eb667-106">Listing IP Addresses for a Computer</span></span>

<span data-ttu-id="eb667-107">Aby uzyskać wszystkie adresy IP, używana na komputerze lokalnym, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="eb667-107">To get all IP addresses in use on the local computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

<span data-ttu-id="eb667-108">Dane wyjściowe tego polecenia różni się od większości list właściwości, ponieważ są ujęte w nawiasy klamrowe:</span><span class="sxs-lookup"><span data-stu-id="eb667-108">The output of this command differs from most property lists, because values are enclosed in braces:</span></span>

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

<span data-ttu-id="eb667-109">Aby zrozumieć, dlaczego nawiasy klamrowe są wyświetlane, należy użyć polecenia cmdlet Get-członka do sprawdzenia **IPAddress** właściwości:</span><span class="sxs-lookup"><span data-stu-id="eb667-109">To understand why the braces appear, use the Get-Member cmdlet to examine the **IPAddress** property:</span></span>

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

<span data-ttu-id="eb667-110">Właściwość adres IP dla każdej karty sieciowej jest rzeczywiście tablicy.</span><span class="sxs-lookup"><span data-stu-id="eb667-110">The IPAddress property for each network adapter is actually an array.</span></span> <span data-ttu-id="eb667-111">Nawiasy klamrowe w definicji wskazują, że **IPAddress** nie jest **System.String** wartość, ale tablica **System.String** wartości.</span><span class="sxs-lookup"><span data-stu-id="eb667-111">The braces in the definition indicate that **IPAddress** is not a **System.String** value, but an array of **System.String** values.</span></span>

### <a name="listing-ip-configuration-data"></a><span data-ttu-id="eb667-112">Wyświetlanie danych konfiguracji protokołu IP</span><span class="sxs-lookup"><span data-stu-id="eb667-112">Listing IP Configuration Data</span></span>

<span data-ttu-id="eb667-113">Aby wyświetlić szczegółowe danych konfiguracji protokołu IP dla każdej karty sieciowej, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="eb667-113">To display detailed IP configuration data for each network adapter, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

<span data-ttu-id="eb667-114">Ekran domyślny dla obiekt konfiguracji karty sieciowej jest bardzo ograniczonego zestawu dostępnych informacji.</span><span class="sxs-lookup"><span data-stu-id="eb667-114">The default display for the network adapter configuration object is a very reduced set of the available information.</span></span> <span data-ttu-id="eb667-115">Szczegółowe inspekcji i rozwiązywania problemów Użyj Select-Object lub formatowania polecenia cmdlet, takich jak lista formatów, aby określić właściwości, które mają być wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="eb667-115">For in-depth inspection and troubleshooting, use Select-Object or a formatting cmdlet, such as Format-List, to specify the properties to be displayed.</span></span>

<span data-ttu-id="eb667-116">Jeśli nie jesteś zainteresowany właściwości IPX lub usługi WINS — prawdopodobnie w przypadku nowoczesnych sieci TCP/IP — parametr ExcludeProperty Select-Object umożliwia ukrywanie właściwości za pomocą nazw, które zaczynają się od "WINS" lub "IPX:"</span><span class="sxs-lookup"><span data-stu-id="eb667-116">If you are not interested in IPX or WINS properties—probably the case in a modern TCP/IP network—you can use the ExcludeProperty parameter of Select-Object to hide properties with names that begin with "WINS" or "IPX:"</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

<span data-ttu-id="eb667-117">To polecenie zwraca szczegółowe informacje o routing DHCP, DNS, a inne pomocnicze właściwości konfiguracji adresu IP.</span><span class="sxs-lookup"><span data-stu-id="eb667-117">This command returns detailed information about DHCP, DNS, routing, and other minor IP configuration properties.</span></span>

### <a name="pinging-computers"></a><span data-ttu-id="eb667-118">Badanie komputerów</span><span class="sxs-lookup"><span data-stu-id="eb667-118">Pinging Computers</span></span>

<span data-ttu-id="eb667-119">Można wykonywać proste ping względem wykorzystywany przez **Win32_PingStatus**.</span><span class="sxs-lookup"><span data-stu-id="eb667-119">You can perform a simple ping against a computer using by **Win32_PingStatus**.</span></span> <span data-ttu-id="eb667-120">Polecenie wykonuje polecenie ping, ale zwraca długich danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="eb667-120">The following command performs the ping, but returns lengthy output:</span></span>

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

<span data-ttu-id="eb667-121">Bardziej użyteczne formularz podsumowanie wyświetlenie właściwości adresu, czas odpowiedzi i StatusCode wygenerowane za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="eb667-121">A more useful form for summary information a display of the Address, ResponseTime, and StatusCode properties, as generated by the following command.</span></span> <span data-ttu-id="eb667-122">Parametr Autosize Format-Table zmienia rozmiar kolumn tabeli, aby prawidłowo wyświetlić w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb667-122">The Autosize parameter of Format-Table resizes the table columns so that they display properly in Windows PowerShell.</span></span>

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

<span data-ttu-id="eb667-123">StatusCode 0 oznacza pomyślne polecenie ping.</span><span class="sxs-lookup"><span data-stu-id="eb667-123">A StatusCode of 0 indicates a successful ping.</span></span>

<span data-ttu-id="eb667-124">Tablica służy do wielu komputerów za pomocą jednego polecenia ping.</span><span class="sxs-lookup"><span data-stu-id="eb667-124">You can use an array to ping multiple computers with a single command.</span></span> <span data-ttu-id="eb667-125">Ponieważ więcej niż jeden adres, użyj **ForEach-Object** na polecenie ping każdy adres oddzielnie:</span><span class="sxs-lookup"><span data-stu-id="eb667-125">Because there is more than one address, use the **ForEach-Object** to ping each address separately:</span></span>

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="eb667-126">Można użyć tego samego formatu polecenia na polecenie ping, wszystkie komputery w podsieci, takich jak sieć VPN, która używa numeru sieci 192.168.1.0 i maski podsieci klasy C standard (255.255.255.0)., są tylko adresy z zakresu od 192.168.1.1 za pośrednictwem 192.168.1.254 prawnie adresów lokalnych (0 jest zawsze zarezerwowane dla numeru sieci i 255 jest adresem emisji podsieci).</span><span class="sxs-lookup"><span data-stu-id="eb667-126">You can use the same command format to ping all of the computers on a subnet, such as a private network that uses network number 192.168.1.0 and a standard Class C subnet mask (255.255.255.0)., Only addresses in the range of 192.168.1.1 through 192.168.1.254 are legitimate local addresses (0 is always reserved for the network number and 255 is a subnet broadcast address).</span></span>

<span data-ttu-id="eb667-127">Do reprezentowania tablicy liczb od 1 do 254 w programie Windows PowerShell, użyj instrukcji **1..254.**</span><span class="sxs-lookup"><span data-stu-id="eb667-127">To represent an array of the numbers from 1 through 254 in Windows PowerShell, use the statement **1..254.**</span></span> <span data-ttu-id="eb667-128">Ping pełną podsieci może zostać wykonana przez generowanie tablicy, a następnie dodanie wartości do częściowego adresu w instrukcji ping:</span><span class="sxs-lookup"><span data-stu-id="eb667-128">A complete subnet ping can be performed by generating the array and then adding the values onto a partial address in the ping statement:</span></span>

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="eb667-129">Należy pamiętać o tym, gdzie indziej również używana ta technika generowania zakres adresów.</span><span class="sxs-lookup"><span data-stu-id="eb667-129">Note that this technique for generating a range of addresses can be used elsewhere as well.</span></span> <span data-ttu-id="eb667-130">W ten sposób można wygenerować pełny zestaw adresów:</span><span class="sxs-lookup"><span data-stu-id="eb667-130">You can generate a complete set of addresses in this way:</span></span>

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

### <a name="retrieving-network-adapter-properties"></a><span data-ttu-id="eb667-131">Podczas pobierania właściwości karty sieciowej</span><span class="sxs-lookup"><span data-stu-id="eb667-131">Retrieving Network Adapter Properties</span></span>

<span data-ttu-id="eb667-132">Wcześniej w tym podręczniku użytkownika, wspomniano, że można pobrać właściwości ogólne konfiguracji za pomocą **Win32_NetworkAdapterConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="eb667-132">Earlier in this user's guide, we mentioned that you could retrieve general configuration properties by using **Win32_NetworkAdapterConfiguration**.</span></span> <span data-ttu-id="eb667-133">Chociaż nie wyłącznie informacje TCP/IP adresów informacje dotyczące karty sieciowej, takich jak MAC, i typy karty mogą być przydatne dla zrozumienia, co dzieje się z komputerem.</span><span class="sxs-lookup"><span data-stu-id="eb667-133">Although not strictly TCP/IP information, network adapter information such as MAC addresses and adapter types can be useful for understanding what is going on with a computer.</span></span> <span data-ttu-id="eb667-134">Aby uzyskać podsumowanie informacji, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="eb667-134">To get a summary of this information, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

### <a name="assigning-the-dns-domain-for-a-network-adapter"></a><span data-ttu-id="eb667-135">Przypisywanie domeny DNS dla karty sieciowej</span><span class="sxs-lookup"><span data-stu-id="eb667-135">Assigning the DNS Domain for a Network Adapter</span></span>

<span data-ttu-id="eb667-136">Aby przypisać domeny DNS do rozpoznawania nazw automatyczne, użyj **SetDNSDomain pozwala ustawić Win32_NetworkAdapterConfiguration** metody.</span><span class="sxs-lookup"><span data-stu-id="eb667-136">To assign the DNS domain for automatic name resolution, use the **Win32_NetworkAdapterConfiguration SetDNSDomain** method.</span></span> <span data-ttu-id="eb667-137">Ponieważ niezależnie przypisać domenę DNS dla każdej konfiguracji karty sieciowej, należy użyć **ForEach-Object** instrukcji, aby przypisać domeny do każdej karty:</span><span class="sxs-lookup"><span data-stu-id="eb667-137">Because you assign the DNS domain for each network adapter configuration independently, you need to use a **ForEach-Object** statement to assign the domain to each adapter:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

<span data-ttu-id="eb667-138">Filtrowanie instrukcji "IPEnabled = $true" jest to konieczne, ponieważ nawet w sieci, która wykorzystuje tylko protokół TCP/IP, nie są kilka konfiguracji kart sieciowych na komputerze, na wartość true, kart TCP/IP; są elementy oprogramowania ogólne obsługi RAS, PPTP, QoS i innych usług dla wszystkich kart sieciowych i dlatego nie ma adresu we własnym.</span><span class="sxs-lookup"><span data-stu-id="eb667-138">The filtering statement "IPEnabled=$true" is necessary, because even on a network that uses only TCP/IP, several of the network adapter configurations on a computer are not true TCP/IP adapters; they are general software elements supporting RAS, PPTP, QoS, and other services for all adapters and thus do not have an address of their own.</span></span>

<span data-ttu-id="eb667-139">Polecenie można filtrować przy użyciu **Where-Object** polecenia cmdlet, zamiast **Get-WmiObject** filtru.</span><span class="sxs-lookup"><span data-stu-id="eb667-139">You can filter the command by using the **Where-Object** cmdlet, instead of using the **Get-WmiObject** filter.</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

### <a name="performing-dhcp-configuration-tasks"></a><span data-ttu-id="eb667-140">Wykonywanie zadań konfiguracji DHCP</span><span class="sxs-lookup"><span data-stu-id="eb667-140">Performing DHCP Configuration Tasks</span></span>

<span data-ttu-id="eb667-141">Modyfikowanie szczegóły DHCP polega na stosowaniu zestaw kart sieciowych, podobnie jak konfiguracja DNS.</span><span class="sxs-lookup"><span data-stu-id="eb667-141">Modifying DHCP details involves working with a set of network adapters, just as the DNS configuration does.</span></span> <span data-ttu-id="eb667-142">Istnieje kilka różnych akcji, które można wykonać za pomocą usługi WMI, a niektóre z najczęściej spotykane firma Microsoft będzie kroków.</span><span class="sxs-lookup"><span data-stu-id="eb667-142">There are several distinct actions you can perform by using WMI, and we will step through a few of the common ones.</span></span>

#### <a name="determining-dhcp-enabled-adapters"></a><span data-ttu-id="eb667-143">Określanie karty obsługujących protokół DHCP</span><span class="sxs-lookup"><span data-stu-id="eb667-143">Determining DHCP-Enabled Adapters</span></span>

<span data-ttu-id="eb667-144">Aby znaleźć kart sieciowych obsługujących protokół DHCP na komputerze, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="eb667-144">To find the DHCP-enabled adapters on a computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

<span data-ttu-id="eb667-145">Aby wykluczyć kart z problemów z konfiguracją IP, można pobrać tylko kart sieciowych obsługujących protokół IP:</span><span class="sxs-lookup"><span data-stu-id="eb667-145">To exclude adapters with IP configuration problems, you can retrieve only IP-enabled adapters:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

#### <a name="retrieving-dhcp-properties"></a><span data-ttu-id="eb667-146">Podczas pobierania właściwości DHCP</span><span class="sxs-lookup"><span data-stu-id="eb667-146">Retrieving DHCP Properties</span></span>

<span data-ttu-id="eb667-147">Ponieważ związanych z usługą DHCP właściwości kart sieciowych zwykle zaczyna się od "DHCP", można użyć parametru właściwości formatu tabeli do wyświetlenia tylko właściwości:</span><span class="sxs-lookup"><span data-stu-id="eb667-147">Because DHCP-related properties for an adapter generally begin with "DHCP," you can use the Property parameter of Format-Table to display only those properties:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

#### <a name="enabling-dhcp-on-each-adapter"></a><span data-ttu-id="eb667-148">Włączanie DHCP dla każdej karty</span><span class="sxs-lookup"><span data-stu-id="eb667-148">Enabling DHCP on Each Adapter</span></span>

<span data-ttu-id="eb667-149">Aby włączyć protokół DHCP na wszystkich kartach, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="eb667-149">To enable DHCP on all adapters, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

<span data-ttu-id="eb667-150">Można użyć **filtru** instrukcji "IPEnabled = $true i DHCPEnabled = $false" Aby uniknąć włączania DHCP, na którym jest już włączony, ale pominięcie tego kroku nie będą powodować błędy.</span><span class="sxs-lookup"><span data-stu-id="eb667-150">You can use the **Filter** statement "IPEnabled=$true and DHCPEnabled=$false" to avoid enabling DHCP where it is already enabled, but omitting this step will not cause errors.</span></span>

#### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a><span data-ttu-id="eb667-151">Zwalnianie i odnawiania dzierżawy DHCP dla określonych kart</span><span class="sxs-lookup"><span data-stu-id="eb667-151">Releasing and Renewing DHCP Leases on Specific Adapters</span></span>

<span data-ttu-id="eb667-152">**Win32_NetworkAdapterConfiguration** klasa ma **ReleaseDHCPLease** i **RenewDHCPLease** metody.</span><span class="sxs-lookup"><span data-stu-id="eb667-152">The **Win32_NetworkAdapterConfiguration** class has **ReleaseDHCPLease** and **RenewDHCPLease** methods.</span></span> <span data-ttu-id="eb667-153">Są używane w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="eb667-153">Both are used in the same way.</span></span> <span data-ttu-id="eb667-154">Ogólnie rzecz biorąc należy użyć tych metod, jeśli należy zwolnić lub odnowić adresów dla karty w określonej podsieci.</span><span class="sxs-lookup"><span data-stu-id="eb667-154">In general, use these methods if you only need to release or renew addresses for an adapter on a specific subnet.</span></span> <span data-ttu-id="eb667-155">Najprostszym sposobem kart filtru w podsieci jest możliwość konfiguracji karty sieciowej, które używają bramy dla tej podsieci.</span><span class="sxs-lookup"><span data-stu-id="eb667-155">The easiest way to filter adapters on a subnet is to choose only the adapter configurations that use the gateway for that subnet.</span></span> <span data-ttu-id="eb667-156">Na przykład następujące polecenie zwalnia wszystkie dzierżawy DHCP dla kart na komputerze lokalnym, które są uzyskiwane dzierżawy DHCP z 192.168.1.254:</span><span class="sxs-lookup"><span data-stu-id="eb667-156">For example, the following command releases all DHCP leases on adapters on the local computer that are obtaining DHCP leases from 192.168.1.254:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

<span data-ttu-id="eb667-157">Jedyna różnica dla odnawiania dzierżawy DHCP jest użycie **RenewDHCPLease** zamiast metody **ReleaseDHCPLease** metody:</span><span class="sxs-lookup"><span data-stu-id="eb667-157">The only change for renewing a DHCP lease is to use the **RenewDHCPLease** method instead of the **ReleaseDHCPLease** method:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> <span data-ttu-id="eb667-158">Korzystając z tych metod na komputerze zdalnym, należy pamiętać, że można stracić dostęp do systemu zdalnego połączenia do niego za pośrednictwem karty dzierżawy zwolniony lub odnowionego.</span><span class="sxs-lookup"><span data-stu-id="eb667-158">When using these methods on a remote computer, be aware that you can lose access to the remote system if you are connected to it through the adapter with the released or renewed lease.</span></span>

#### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a><span data-ttu-id="eb667-159">Zwalnianie i odnawiania dzierżawy DHCP na wszystkich kartach</span><span class="sxs-lookup"><span data-stu-id="eb667-159">Releasing and Renewing DHCP Leases on All Adapters</span></span>

<span data-ttu-id="eb667-160">Na wszystkich kartach mogą wykonywać globalne wersje adresów DHCP lub odnowienia za pomocą **Win32_NetworkAdapterConfiguration** metod, **ReleaseDHCPLeaseAll** i **RenewDHCPLeaseAll** .</span><span class="sxs-lookup"><span data-stu-id="eb667-160">You can perform global DHCP address releases or renewals on all adapters by using the **Win32_NetworkAdapterConfiguration** methods, **ReleaseDHCPLeaseAll** and **RenewDHCPLeaseAll**.</span></span> <span data-ttu-id="eb667-161">Jednak zastosować polecenia do klasy usługi WMI, a nie dla określonej karty, ponieważ zwalniania i odnawiania dzierżawy globalnie jest wykonywana na tej klasy, a nie na określonej karty.</span><span class="sxs-lookup"><span data-stu-id="eb667-161">However, the command must apply to the WMI class, rather than a particular adapter, because releasing and renewing leases globally is performed on the class, not on a specific adapter.</span></span>

<span data-ttu-id="eb667-162">Odwołanie do klasy usługi WMI, zamiast wystąpień klasy, można uzyskać listę wszystkich klas usługi WMI, a następnie zaznaczając odpowiednią klasę według nazwy.</span><span class="sxs-lookup"><span data-stu-id="eb667-162">You can get a reference to a WMI class, instead of class instances, by listing all WMI classes and then selecting only the desired class by name.</span></span> <span data-ttu-id="eb667-163">Na przykład poniższe polecenie zwraca klasy Win32_NetworkAdapterConfiguration:</span><span class="sxs-lookup"><span data-stu-id="eb667-163">For example, the following command returns the Win32_NetworkAdapterConfiguration class:</span></span>

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

<span data-ttu-id="eb667-164">Można traktować jako klasa całego polecenia, a następnie wywołaj **ReleaseDHCPAdapterLease** dla niego metodę.</span><span class="sxs-lookup"><span data-stu-id="eb667-164">You can treat the entire command as the class and then invoke the **ReleaseDHCPAdapterLease** method on it.</span></span> <span data-ttu-id="eb667-165">W poniższym poleceniu nawiasy otaczające **Get-WmiObject** i **Where-Object** środowiska Windows PowerShell można obliczyć je najpierw bezpośrednie elementy potoku:</span><span class="sxs-lookup"><span data-stu-id="eb667-165">In the following command, the parentheses surrounding the **Get-WmiObject** and **Where-Object** pipeline elements direct Windows PowerShell to evaluate them first:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

<span data-ttu-id="eb667-166">W tym samym formacie polecenia można użyć do wywołania **RenewDHCPLeaseAll** metody:</span><span class="sxs-lookup"><span data-stu-id="eb667-166">You can use the same command format to invoke the **RenewDHCPLeaseAll** method:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

### <a name="creating-a-network-share"></a><span data-ttu-id="eb667-167">Utworzenie udziału sieciowego</span><span class="sxs-lookup"><span data-stu-id="eb667-167">Creating a Network Share</span></span>

<span data-ttu-id="eb667-168">Aby utworzyć udział sieciowy, użyj **utworzyć Win32_Share** metody:</span><span class="sxs-lookup"><span data-stu-id="eb667-168">To create a network share, use the **Win32_Share Create** method:</span></span>

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

<span data-ttu-id="eb667-169">Można również utworzyć udział za pomocą **polecenie net share** w programie Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="eb667-169">You can also create the share by using **net share** in Windows PowerShell:</span></span>

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

### <a name="removing-a-network-share"></a><span data-ttu-id="eb667-170">Usuwanie udziału sieciowego</span><span class="sxs-lookup"><span data-stu-id="eb667-170">Removing a Network Share</span></span>

<span data-ttu-id="eb667-171">Możesz usunąć udział sieciowy z **Win32_Share**, ale proces jest nieco inne niż Tworzenie udziału, ponieważ należy do pobrania określonego udziału do usunięcia, a nie **Win32_Share** Klasa.</span><span class="sxs-lookup"><span data-stu-id="eb667-171">You can remove a network share with **Win32_Share**, but the process is slightly different from creating a share, because you need to retrieve the specific share to be removed, rather than the **Win32_Share** class.</span></span> <span data-ttu-id="eb667-172">Następująca instrukcja usuwa udział "TempShare":</span><span class="sxs-lookup"><span data-stu-id="eb667-172">The following statement deletes the share "TempShare":</span></span>

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

<span data-ttu-id="eb667-173">**Polecenie net share** działa również:</span><span class="sxs-lookup"><span data-stu-id="eb667-173">**Net share** works as well:</span></span>

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

### <a name="connecting-a-windows-accessible-network-drive"></a><span data-ttu-id="eb667-174">Łączenie dostępny dysk sieciowy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="eb667-174">Connecting a Windows Accessible Network Drive</span></span>

<span data-ttu-id="eb667-175">**Elementu PSDrive nowy** poleceń cmdlet tworzy dysk programu Windows PowerShell, ale dyski utworzone w ten sposób są dostępne tylko dla programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb667-175">The **New-PSDrive** cmdlets creates a Windows PowerShell drive, but drives created this way are available only to Windows PowerShell.</span></span> <span data-ttu-id="eb667-176">Aby utworzyć nowego dysku sieciowego, można użyć **WScript.Network** obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="eb667-176">To create a new networked drive, you can use the **WScript.Network** COM object.</span></span> <span data-ttu-id="eb667-177">Polecenie mapuje udział \\ \\FPS01\\użytkownikom na lokalnym dysku B:</span><span class="sxs-lookup"><span data-stu-id="eb667-177">The following command maps the share \\\\FPS01\\users to local drive B:</span></span>

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

<span data-ttu-id="eb667-178">**Net użyj** polecenie działa również:</span><span class="sxs-lookup"><span data-stu-id="eb667-178">The **net use** command works as well:</span></span>

```powershell
net use B: \\FPS01\users
```

<span data-ttu-id="eb667-179">Dyski mapowane przy użyciu jednej **WScript.Network** lub polecenie net use są natychmiast dostępne dla środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb667-179">Drives mapped with either **WScript.Network** or net use are immediately available to Windows PowerShell.</span></span>