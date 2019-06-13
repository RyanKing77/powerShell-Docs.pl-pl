---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Wykonywanie zadań w sieci
ms.openlocfilehash: e581296b4b7609b374f206c447c4f797e3e2c400
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030860"
---
# <a name="performing-networking-tasks"></a><span data-ttu-id="94ce8-103">Wykonywanie zadań w sieci</span><span class="sxs-lookup"><span data-stu-id="94ce8-103">Performing Networking Tasks</span></span>

<span data-ttu-id="94ce8-104">Ponieważ protokół TCP/IP jest najczęściej używany protokół sieciowy, większości zadań administracyjnych protokołu sieciowego niskiego poziomu obejmują TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="94ce8-104">Because TCP/IP is the most commonly used network protocol, most low-level network protocol administration tasks involve TCP/IP.</span></span> <span data-ttu-id="94ce8-105">W tej sekcji używamy programu Windows PowerShell i usługi WMI do wykonywania tych zadań.</span><span class="sxs-lookup"><span data-stu-id="94ce8-105">In this section, we use Windows PowerShell and WMI to do these tasks.</span></span>

## <a name="listing-ip-addresses-for-a-computer"></a><span data-ttu-id="94ce8-106">Lista adresów IP dla komputera</span><span class="sxs-lookup"><span data-stu-id="94ce8-106">Listing IP Addresses for a Computer</span></span>

<span data-ttu-id="94ce8-107">Aby uzyskać wszystkie adresy IP używane na komputerze lokalnym, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="94ce8-107">To get all IP addresses in use on the local computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

<span data-ttu-id="94ce8-108">Dane wyjściowe tego polecenia różni się od większości listy właściwości, ponieważ są ujęte w nawiasy klamrowe:</span><span class="sxs-lookup"><span data-stu-id="94ce8-108">The output of this command differs from most property lists, because values are enclosed in braces:</span></span>

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

<span data-ttu-id="94ce8-109">Aby zrozumieć, dlaczego nawiasy klamrowe są wyświetlane, należy użyć polecenia cmdlet Get-Member zbadanie **IPAddress** właściwości:</span><span class="sxs-lookup"><span data-stu-id="94ce8-109">To understand why the braces appear, use the Get-Member cmdlet to examine the **IPAddress** property:</span></span>

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

<span data-ttu-id="94ce8-110">Właściwość adres IP dla każdej karty sieciowej jest faktycznie tablicą.</span><span class="sxs-lookup"><span data-stu-id="94ce8-110">The IPAddress property for each network adapter is actually an array.</span></span> <span data-ttu-id="94ce8-111">Nawiasy klamrowe w definicji wskazują, że **IPAddress** nie **System.String** wartość, ale tablica **System.String** wartości.</span><span class="sxs-lookup"><span data-stu-id="94ce8-111">The braces in the definition indicate that **IPAddress** is not a **System.String** value, but an array of **System.String** values.</span></span>

## <a name="listing-ip-configuration-data"></a><span data-ttu-id="94ce8-112">Wyświetlanie danych konfiguracji protokołu IP</span><span class="sxs-lookup"><span data-stu-id="94ce8-112">Listing IP Configuration Data</span></span>

<span data-ttu-id="94ce8-113">Aby wyświetlić szczegółowe danych konfiguracji protokołu IP dla każdej karty sieciowej, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="94ce8-113">To display detailed IP configuration data for each network adapter, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

<span data-ttu-id="94ce8-114">Ekran domyślny dla obiektu konfiguracji karty sieciowej jest bardzo ograniczonym zestawie dostępne informacje.</span><span class="sxs-lookup"><span data-stu-id="94ce8-114">The default display for the network adapter configuration object is a very reduced set of the available information.</span></span> <span data-ttu-id="94ce8-115">Szczegóły inspekcji i rozwiązywanie problemów należy użyć Select-Object lub formatowania polecenia cmdlet, takich jak listy Format do określania właściwości, które mają być wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="94ce8-115">For in-depth inspection and troubleshooting, use Select-Object or a formatting cmdlet, such as Format-List, to specify the properties to be displayed.</span></span>

<span data-ttu-id="94ce8-116">Jeśli nie jesteś zainteresowany właściwości IPX lub usługi WINS, prawdopodobnie w przypadku nowoczesnych sieci TCP/IP — można użyć parametru ExcludeProperty Select-Object spowoduje ukrycie właściwości z nazwami, które zaczynają się od "WINS" lub "IPX:"</span><span class="sxs-lookup"><span data-stu-id="94ce8-116">If you are not interested in IPX or WINS properties—probably the case in a modern TCP/IP network—you can use the ExcludeProperty parameter of Select-Object to hide properties with names that begin with "WINS" or "IPX:"</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

<span data-ttu-id="94ce8-117">To polecenie zwraca szczegółowe informacje na temat usługi DHCP, DNS, routingu i inne drobne właściwości konfiguracji adresu IP.</span><span class="sxs-lookup"><span data-stu-id="94ce8-117">This command returns detailed information about DHCP, DNS, routing, and other minor IP configuration properties.</span></span>

## <a name="pinging-computers"></a><span data-ttu-id="94ce8-118">Pingowanie komputerów</span><span class="sxs-lookup"><span data-stu-id="94ce8-118">Pinging Computers</span></span>

<span data-ttu-id="94ce8-119">Można wykonywać proste polecenie ping względem komputer używa przez **Win32_PingStatus**.</span><span class="sxs-lookup"><span data-stu-id="94ce8-119">You can perform a simple ping against a computer using by **Win32_PingStatus**.</span></span> <span data-ttu-id="94ce8-120">Poniższe polecenie wykonuje polecenie ping, ale zwraca długich danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="94ce8-120">The following command performs the ping, but returns lengthy output:</span></span>

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

<span data-ttu-id="94ce8-121">Bardziej użyteczny, formularz podsumowanie wyświetlania właściwości adres, czas odpowiedzi i StatusCode, tak jak w przypadku następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="94ce8-121">A more useful form for summary information a display of the Address, ResponseTime, and StatusCode properties, as generated by the following command.</span></span> <span data-ttu-id="94ce8-122">Parametr Autosize Format-Table zmienia rozmiar kolumn tabeli tak, aby prawidłowo wyświetlane w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="94ce8-122">The Autosize parameter of Format-Table resizes the table columns so that they display properly in Windows PowerShell.</span></span>

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

<span data-ttu-id="94ce8-123">StatusCode 0 oznacza pomyślne polecenie ping.</span><span class="sxs-lookup"><span data-stu-id="94ce8-123">A StatusCode of 0 indicates a successful ping.</span></span>

<span data-ttu-id="94ce8-124">Za pomocą tablicy na polecenie ping wiele komputerów za pomocą jednego polecenia.</span><span class="sxs-lookup"><span data-stu-id="94ce8-124">You can use an array to ping multiple computers with a single command.</span></span> <span data-ttu-id="94ce8-125">Ponieważ istnieje więcej niż jeden adres, użyj **ForEach-Object** wysłać polecenie ping każdego adresu oddzielnie:</span><span class="sxs-lookup"><span data-stu-id="94ce8-125">Because there is more than one address, use the **ForEach-Object** to ping each address separately:</span></span>

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="94ce8-126">Można użyć tego samego formatu polecenia na polecenie ping, wszystkie komputery w podsieci, takich jak sieć VPN, która używa numeru sieci 192.168.1.0 i maskę podsieci klasy C standard (255.255.255.0)., są tylko adresy z zakresu od 192.168.1.1 do 192.168.1.254 wiarygodnych adresów lokalnych (0 jest zawsze zarezerwowane dla numer sieci i 255 jest adresem emisji podsieci).</span><span class="sxs-lookup"><span data-stu-id="94ce8-126">You can use the same command format to ping all of the computers on a subnet, such as a private network that uses network number 192.168.1.0 and a standard Class C subnet mask (255.255.255.0)., Only addresses in the range of 192.168.1.1 through 192.168.1.254 are legitimate local addresses (0 is always reserved for the network number and 255 is a subnet broadcast address).</span></span>

<span data-ttu-id="94ce8-127">Do reprezentowania tablicy liczb od 1 do 254 w programie Windows PowerShell, użyj instrukcji **1..254.**</span><span class="sxs-lookup"><span data-stu-id="94ce8-127">To represent an array of the numbers from 1 through 254 in Windows PowerShell, use the statement **1..254.**</span></span> <span data-ttu-id="94ce8-128">Ping pełną podsieci mogą być wykonywane przez generowanie tablicy, a następnie dodanie wartości do częściowego adresu w instrukcji ping:</span><span class="sxs-lookup"><span data-stu-id="94ce8-128">A complete subnet ping can be performed by generating the array and then adding the values onto a partial address in the ping statement:</span></span>

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="94ce8-129">Należy pamiętać, że ta technika generowania zakres adresów może służyć także w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="94ce8-129">Note that this technique for generating a range of addresses can be used elsewhere as well.</span></span> <span data-ttu-id="94ce8-130">W ten sposób można wygenerować kompletny zestaw adresów:</span><span class="sxs-lookup"><span data-stu-id="94ce8-130">You can generate a complete set of addresses in this way:</span></span>

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a><span data-ttu-id="94ce8-131">Trwa pobieranie właściwości karty sieciowej</span><span class="sxs-lookup"><span data-stu-id="94ce8-131">Retrieving Network Adapter Properties</span></span>

<span data-ttu-id="94ce8-132">Wcześniej w tym podręczniku użytkownika, wspomnieliśmy, że można pobrać właściwości ogólne konfiguracji za pomocą **Win32_NetworkAdapterConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="94ce8-132">Earlier in this user's guide, we mentioned that you could retrieve general configuration properties by using **Win32_NetworkAdapterConfiguration**.</span></span> <span data-ttu-id="94ce8-133">Chociaż nie jest właściwie informacji protokołu TCP/IP, informacje o karty sieciowej, takich jak MAC adresy i typy karty mogą być przydatne dla zrozumienia, co się dzieje z komputerem.</span><span class="sxs-lookup"><span data-stu-id="94ce8-133">Although not strictly TCP/IP information, network adapter information such as MAC addresses and adapter types can be useful for understanding what is going on with a computer.</span></span> <span data-ttu-id="94ce8-134">Aby uzyskać podsumowanie tych informacji, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="94ce8-134">To get a summary of this information, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a><span data-ttu-id="94ce8-135">Przypisywanie domeny DNS dla karty sieciowej</span><span class="sxs-lookup"><span data-stu-id="94ce8-135">Assigning the DNS Domain for a Network Adapter</span></span>

<span data-ttu-id="94ce8-136">Aby przypisać domeny DNS do rozpoznawania nazw automatycznego, należy użyć **SetDNSDomain pozwala ustawić Win32_NetworkAdapterConfiguration** metody.</span><span class="sxs-lookup"><span data-stu-id="94ce8-136">To assign the DNS domain for automatic name resolution, use the **Win32_NetworkAdapterConfiguration SetDNSDomain** method.</span></span> <span data-ttu-id="94ce8-137">Domeny DNS dla każdej konfiguracji karty sieciowej możesz przypisać niezależnie, dlatego musisz użyć **ForEach-Object** instrukcję, aby przypisać domeny do każdej karty sieciowej:</span><span class="sxs-lookup"><span data-stu-id="94ce8-137">Because you assign the DNS domain for each network adapter configuration independently, you need to use a **ForEach-Object** statement to assign the domain to each adapter:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

<span data-ttu-id="94ce8-138">Filtrowanie instrukcji "IPEnabled = $true" jest to konieczne, ponieważ nawet w przypadku sieci, która używa tylko protokołu TCP/IP, kilka konfiguracji kart sieciowych na komputerze są prawdziwe TCP/IP karty; są elementy ogólne oprogramowania, obsługa RAS, PPTP, QoS i innych usług dla wszystkich kart sieciowych i dlatego nie ma adresu swoich własnych.</span><span class="sxs-lookup"><span data-stu-id="94ce8-138">The filtering statement "IPEnabled=$true" is necessary, because even on a network that uses only TCP/IP, several of the network adapter configurations on a computer are not true TCP/IP adapters; they are general software elements supporting RAS, PPTP, QoS, and other services for all adapters and thus do not have an address of their own.</span></span>

<span data-ttu-id="94ce8-139">Polecenia można filtrować przy użyciu **Where-Object** zamiast przy użyciu polecenia cmdlet **Get-WmiObject** filtru.</span><span class="sxs-lookup"><span data-stu-id="94ce8-139">You can filter the command by using the **Where-Object** cmdlet, instead of using the **Get-WmiObject** filter.</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a><span data-ttu-id="94ce8-140">Wykonywanie zadań konfiguracyjnych DHCP</span><span class="sxs-lookup"><span data-stu-id="94ce8-140">Performing DHCP Configuration Tasks</span></span>

<span data-ttu-id="94ce8-141">Modyfikowanie szczegóły DHCP polega na pracę z zestawem kart sieciowych, podobnie jak konfiguracji DNS.</span><span class="sxs-lookup"><span data-stu-id="94ce8-141">Modifying DHCP details involves working with a set of network adapters, just as the DNS configuration does.</span></span> <span data-ttu-id="94ce8-142">Istnieje kilka różnych akcji, które można wykonać przy użyciu usługi WMI, a firma Microsoft będzie przejść przez niektóre typowe z nich.</span><span class="sxs-lookup"><span data-stu-id="94ce8-142">There are several distinct actions you can perform by using WMI, and we will step through a few of the common ones.</span></span>

### <a name="determining-dhcp-enabled-adapters"></a><span data-ttu-id="94ce8-143">Określanie karty obsługujących protokół DHCP</span><span class="sxs-lookup"><span data-stu-id="94ce8-143">Determining DHCP-Enabled Adapters</span></span>

<span data-ttu-id="94ce8-144">Aby znaleźć kart sieciowych obsługujących protokół DHCP na komputerze, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="94ce8-144">To find the DHCP-enabled adapters on a computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

<span data-ttu-id="94ce8-145">Aby wykluczyć kart z problemów z konfiguracją adresów IP, możesz pobrać tylko kart sieciowych obsługujących protokół IP:</span><span class="sxs-lookup"><span data-stu-id="94ce8-145">To exclude adapters with IP configuration problems, you can retrieve only IP-enabled adapters:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

### <a name="retrieving-dhcp-properties"></a><span data-ttu-id="94ce8-146">Trwa pobieranie właściwości DHCP</span><span class="sxs-lookup"><span data-stu-id="94ce8-146">Retrieving DHCP Properties</span></span>

<span data-ttu-id="94ce8-147">Ponieważ właściwości związanych z usługą DHCP dla karty zwykle zaczyna się od "DHCP", można użyć parametru właściwości Format-Table, aby wyświetlić tylko te właściwości:</span><span class="sxs-lookup"><span data-stu-id="94ce8-147">Because DHCP-related properties for an adapter generally begin with "DHCP," you can use the Property parameter of Format-Table to display only those properties:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a><span data-ttu-id="94ce8-148">Włączenie protokołu DHCP na poszczególnych kartach</span><span class="sxs-lookup"><span data-stu-id="94ce8-148">Enabling DHCP on Each Adapter</span></span>

<span data-ttu-id="94ce8-149">Aby włączyć DHCP dla wszystkich kart sieciowych, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="94ce8-149">To enable DHCP on all adapters, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

<span data-ttu-id="94ce8-150">Możesz użyć **filtru** instrukcji "IPEnabled = $true i DHCPEnabled = $false" w celu uniknięcia włączania protokołu DHCP, gdy jest włączony, ale pominięcie tego kroku nie będą powodować błędy.</span><span class="sxs-lookup"><span data-stu-id="94ce8-150">You can use the **Filter** statement "IPEnabled=$true and DHCPEnabled=$false" to avoid enabling DHCP where it is already enabled, but omitting this step will not cause errors.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a><span data-ttu-id="94ce8-151">Zwalnianie i odnawianie dzierżawy DHCP dla określonych kart</span><span class="sxs-lookup"><span data-stu-id="94ce8-151">Releasing and Renewing DHCP Leases on Specific Adapters</span></span>

<span data-ttu-id="94ce8-152">**Win32_NetworkAdapterConfiguration** klasa ma **ReleaseDHCPLease** i **RenewDHCPLease** metody.</span><span class="sxs-lookup"><span data-stu-id="94ce8-152">The **Win32_NetworkAdapterConfiguration** class has **ReleaseDHCPLease** and **RenewDHCPLease** methods.</span></span> <span data-ttu-id="94ce8-153">Oba są używane w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="94ce8-153">Both are used in the same way.</span></span> <span data-ttu-id="94ce8-154">Ogólnie rzecz biorąc należy użyć tych metod, jeśli potrzebujesz zwolnić lub odnowić adresów dla karty w określonej podsieci.</span><span class="sxs-lookup"><span data-stu-id="94ce8-154">In general, use these methods if you only need to release or renew addresses for an adapter on a specific subnet.</span></span> <span data-ttu-id="94ce8-155">Najprostszym sposobem kart filtru w podsieci jest wybranie konfiguracji karty sieciowej, korzystających z bramy dla tej podsieci.</span><span class="sxs-lookup"><span data-stu-id="94ce8-155">The easiest way to filter adapters on a subnet is to choose only the adapter configurations that use the gateway for that subnet.</span></span> <span data-ttu-id="94ce8-156">Na przykład następujące polecenie zwalnia wszystkie dzierżawy DHCP na kartach na komputerze lokalnym, które są uzyskiwane dzierżawy DHCP z 192.168.1.254:</span><span class="sxs-lookup"><span data-stu-id="94ce8-156">For example, the following command releases all DHCP leases on adapters on the local computer that are obtaining DHCP leases from 192.168.1.254:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

<span data-ttu-id="94ce8-157">Jedyna zmiana odnowienia dzierżawy DHCP jest użycie **RenewDHCPLease** zamiast metody **ReleaseDHCPLease** metody:</span><span class="sxs-lookup"><span data-stu-id="94ce8-157">The only change for renewing a DHCP lease is to use the **RenewDHCPLease** method instead of the **ReleaseDHCPLease** method:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> <span data-ttu-id="94ce8-158">Korzystając z tych metod na komputerze zdalnym, należy pamiętać, że można utraty dostępu do systemu zdalnego. Jeśli łączysz się je za pośrednictwem karty wydana lub odnowionej dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="94ce8-158">When using these methods on a remote computer, be aware that you can lose access to the remote system if you are connected to it through the adapter with the released or renewed lease.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a><span data-ttu-id="94ce8-159">Zwalnianie i odnawianie dzierżawy DHCP na wszystkich kartach</span><span class="sxs-lookup"><span data-stu-id="94ce8-159">Releasing and Renewing DHCP Leases on All Adapters</span></span>

<span data-ttu-id="94ce8-160">Możesz wykonać globalnej wersji adres DHCP lub odnowienia na wszystkich kartach przy użyciu **Win32_NetworkAdapterConfiguration** metod **ReleaseDHCPLeaseAll** i **RenewDHCPLeaseAll** .</span><span class="sxs-lookup"><span data-stu-id="94ce8-160">You can perform global DHCP address releases or renewals on all adapters by using the **Win32_NetworkAdapterConfiguration** methods, **ReleaseDHCPLeaseAll** and **RenewDHCPLeaseAll**.</span></span> <span data-ttu-id="94ce8-161">Jednak polecenia należy zastosować do klasy usługi WMI, a nie dla określonej karty, ponieważ przy zwalnianiu i globalnie odnawianie dzierżawy jest wykonywana na tej klasy, a nie na określonej karty.</span><span class="sxs-lookup"><span data-stu-id="94ce8-161">However, the command must apply to the WMI class, rather than a particular adapter, because releasing and renewing leases globally is performed on the class, not on a specific adapter.</span></span>

<span data-ttu-id="94ce8-162">Wyświetlanie listy wszystkich klas usługi WMI, a następnie wybierając odpowiednią klasę o nazwie można uzyskać odwołanie do klasy usługi WMI, zamiast wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="94ce8-162">You can get a reference to a WMI class, instead of class instances, by listing all WMI classes and then selecting only the desired class by name.</span></span> <span data-ttu-id="94ce8-163">Na przykład poniższe polecenie zwraca klasy Win32_NetworkAdapterConfiguration:</span><span class="sxs-lookup"><span data-stu-id="94ce8-163">For example, the following command returns the Win32_NetworkAdapterConfiguration class:</span></span>

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

<span data-ttu-id="94ce8-164">Można traktować cały polecenia jako klasy, a następnie wywołaj **ReleaseDHCPAdapterLease** metody na nim.</span><span class="sxs-lookup"><span data-stu-id="94ce8-164">You can treat the entire command as the class and then invoke the **ReleaseDHCPAdapterLease** method on it.</span></span> <span data-ttu-id="94ce8-165">W poniższym poleceniu nawiasy otaczające **Get-WmiObject** i **Where-Object** elementów potoku bezpośrednie programu Windows PowerShell, aby ich oceny na pierwsze:</span><span class="sxs-lookup"><span data-stu-id="94ce8-165">In the following command, the parentheses surrounding the **Get-WmiObject** and **Where-Object** pipeline elements direct Windows PowerShell to evaluate them first:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

<span data-ttu-id="94ce8-166">Można użyć tego samego formatu polecenie do wywołania **RenewDHCPLeaseAll** metody:</span><span class="sxs-lookup"><span data-stu-id="94ce8-166">You can use the same command format to invoke the **RenewDHCPLeaseAll** method:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a><span data-ttu-id="94ce8-167">Utworzenie udziału sieciowego</span><span class="sxs-lookup"><span data-stu-id="94ce8-167">Creating a Network Share</span></span>

<span data-ttu-id="94ce8-168">Aby utworzyć udział sieciowy, użyj **tworzenie Win32_Share** metody:</span><span class="sxs-lookup"><span data-stu-id="94ce8-168">To create a network share, use the **Win32_Share Create** method:</span></span>

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

<span data-ttu-id="94ce8-169">Można również utworzyć przy użyciu udziału **polecenie net share** w programie Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="94ce8-169">You can also create the share by using **net share** in Windows PowerShell:</span></span>

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a><span data-ttu-id="94ce8-170">Usuwanie udziału sieciowego</span><span class="sxs-lookup"><span data-stu-id="94ce8-170">Removing a Network Share</span></span>

<span data-ttu-id="94ce8-171">Można usunąć udziału sieciowego przy użyciu **Win32_Share**, ale proces różni się nieco od tworzenia udziału, ponieważ trzeba pobrać określonego udziału do usunięcia, a nie **Win32_Share** Klasa.</span><span class="sxs-lookup"><span data-stu-id="94ce8-171">You can remove a network share with **Win32_Share**, but the process is slightly different from creating a share, because you need to retrieve the specific share to be removed, rather than the **Win32_Share** class.</span></span> <span data-ttu-id="94ce8-172">Poniższa instrukcja umożliwia usunięcie udziału "TempShare":</span><span class="sxs-lookup"><span data-stu-id="94ce8-172">The following statement deletes the share "TempShare":</span></span>

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

<span data-ttu-id="94ce8-173">**Polecenie net share** działa także:</span><span class="sxs-lookup"><span data-stu-id="94ce8-173">**Net share** works as well:</span></span>

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a><span data-ttu-id="94ce8-174">Łączenie z dyskiem sieciowym dostępnym Windows</span><span class="sxs-lookup"><span data-stu-id="94ce8-174">Connecting a Windows Accessible Network Drive</span></span>

<span data-ttu-id="94ce8-175">**New PSDrive** poleceń cmdlet tworzy dysk programu Windows PowerShell, ale dyski utworzone w ten sposób są dostępne tylko dla programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="94ce8-175">The **New-PSDrive** cmdlets creates a Windows PowerShell drive, but drives created this way are available only to Windows PowerShell.</span></span> <span data-ttu-id="94ce8-176">Aby utworzyć nowego dysku sieciowym, można użyć **WScript.Network** obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="94ce8-176">To create a new networked drive, you can use the **WScript.Network** COM object.</span></span> <span data-ttu-id="94ce8-177">Następujące polecenie mapuje udziału \\ \\FPS01\\użytkownikom na dysku lokalnym B:</span><span class="sxs-lookup"><span data-stu-id="94ce8-177">The following command maps the share \\\\FPS01\\users to local drive B:</span></span>

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

<span data-ttu-id="94ce8-178">**Net użyj** polecenie działa również:</span><span class="sxs-lookup"><span data-stu-id="94ce8-178">The **net use** command works as well:</span></span>

```powershell
net use B: \\FPS01\users
```

<span data-ttu-id="94ce8-179">Dyski mapowane z oboma **WScript.Network** lub polecenie net use są natychmiast dostępne dla programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="94ce8-179">Drives mapped with either **WScript.Network** or net use are immediately available to Windows PowerShell.</span></span>
