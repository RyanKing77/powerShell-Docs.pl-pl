---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 11b5e36f703c242e0bc820ab19d11d39305fa90c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187915"
---
# <a name="network-switch-management-with-powershell"></a><span data-ttu-id="eb730-102">Zarządzanie przełącznikiem sieciowym przy użyciu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="eb730-102">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="eb730-103">**Get NetworkSwitchEthernetPort** polecenie cmdlet zwraca teraz następujące dodatkowe informacje z wystąpień:</span><span class="sxs-lookup"><span data-stu-id="eb730-103">The **Get-NetworkSwitchEthernetPort** cmdlet now returns the following additional information with instances:</span></span>

- <span data-ttu-id="eb730-104">Adres IP — adres IP skojarzony z portem</span><span class="sxs-lookup"><span data-stu-id="eb730-104">IPAddress – the IP address associated with the port</span></span>
- <span data-ttu-id="eb730-105">PortMode — tryb portu: dostępu, trasy lub magistrali</span><span class="sxs-lookup"><span data-stu-id="eb730-105">PortMode – the port mode: access, route, or trunk</span></span>
- <span data-ttu-id="eb730-106">AccessVLAN — identyfikator sieci VLAN skojarzone z tym portem w trybie dostępu</span><span class="sxs-lookup"><span data-stu-id="eb730-106">AccessVLAN – the ID of the VLAN associated with this port in access mode</span></span>
- <span data-ttu-id="eb730-107">TrunkedVLANList — Lista identyfikatorów sieci VLAN skojarzone z tym portem w trybie magistrali</span><span class="sxs-lookup"><span data-stu-id="eb730-107">TrunkedVLANList – a list of IDs of VLANs associated with this port in trunk mode</span></span>

## <a name="fundamental-network-switch-management-with-windows-powershell"></a><span data-ttu-id="eb730-108">Zarządzanie przełącznika podstawowych sieci za pomocą środowiska Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eb730-108">Fundamental network switch management with Windows PowerShell</span></span>

<span data-ttu-id="eb730-109">Przełącznik sieci poleceń cmdlet, wprowadzone w programie WMF 5.0, umożliwiają przełącznika, wirtualnych sieci LAN (VLAN) i podstawowa konfiguracja portu przełącznika sieci warstwy 2 przełączniki sieciowe certyfikatem logo systemu Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="eb730-109">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="eb730-110">Microsoft pozostaje starań, aby obsługa [abstrakcji centrum danych](http://technet.microsoft.com/cloud/dal.aspx) wizji warstwy (DAL) i wyświetlania wartości w naszym klientom i partnerom w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="eb730-110">Microsoft remains committed to supporting the [Datacenter Abstraction](http://technet.microsoft.com/cloud/dal.aspx) Layer (DAL) vision, and to show value for our customers and partners in this space.</span></span> <span data-ttu-id="eb730-111">Przy użyciu tych poleceń cmdlet można wykonywać:</span><span class="sxs-lookup"><span data-stu-id="eb730-111">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="eb730-112">Globalny przełącznika konfiguracji, takich jak:</span><span class="sxs-lookup"><span data-stu-id="eb730-112">Global switch configuration, such as:</span></span>
    - <span data-ttu-id="eb730-113">Nazwa hosta zestawu</span><span class="sxs-lookup"><span data-stu-id="eb730-113">Set host name</span></span>
    - <span data-ttu-id="eb730-114">Transparent przełącznika zestawu</span><span class="sxs-lookup"><span data-stu-id="eb730-114">Set switch banner</span></span>
    - <span data-ttu-id="eb730-115">Zachowaj konfigurację</span><span class="sxs-lookup"><span data-stu-id="eb730-115">Persist configuration</span></span>
    - <span data-ttu-id="eb730-116">Włączanie lub wyłączanie funkcji</span><span class="sxs-lookup"><span data-stu-id="eb730-116">Enable or disable feature</span></span>

- <span data-ttu-id="eb730-117">Konfiguracja sieci VLAN:</span><span class="sxs-lookup"><span data-stu-id="eb730-117">VLAN configuration:</span></span>
    - <span data-ttu-id="eb730-118">Tworzenie lub usuwanie sieci VLAN</span><span class="sxs-lookup"><span data-stu-id="eb730-118">Create or remove VLAN</span></span>
    - <span data-ttu-id="eb730-119">Włącz lub wyłącz sieci VLAN</span><span class="sxs-lookup"><span data-stu-id="eb730-119">Enable or disable VLAN</span></span>
    - <span data-ttu-id="eb730-120">Wyliczanie sieci VLAN</span><span class="sxs-lookup"><span data-stu-id="eb730-120">Enumerate VLAN</span></span>
    - <span data-ttu-id="eb730-121">Ustawianie przyjaznej nazwy sieć VLAN</span><span class="sxs-lookup"><span data-stu-id="eb730-121">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="eb730-122">Konfiguracja portów warstwy 2:</span><span class="sxs-lookup"><span data-stu-id="eb730-122">Layer 2 port configuration:</span></span>
    - <span data-ttu-id="eb730-123">Wyliczanie portów</span><span class="sxs-lookup"><span data-stu-id="eb730-123">Enumerate ports</span></span>
    - <span data-ttu-id="eb730-124">Włączać lub wyłączać porty</span><span class="sxs-lookup"><span data-stu-id="eb730-124">Enable or disable ports</span></span>
    - <span data-ttu-id="eb730-125">Tryby portu zestawu i właściwości</span><span class="sxs-lookup"><span data-stu-id="eb730-125">Set port modes and properties</span></span>
    - <span data-ttu-id="eb730-126">Dodawanie lub kojarzenie z sieci VLAN na magistrali lub dostęp na porcie</span><span class="sxs-lookup"><span data-stu-id="eb730-126">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="eb730-127">Rozpocznij, przeglądanie, wyszukując wszystkich poleceń cmdlet NetworkSwitch!</span><span class="sxs-lookup"><span data-stu-id="eb730-127">Start exploring by looking for all of the NetworkSwitch cmdlets!</span></span>

```powershell
PS> Get-Command *-NetworkSwitch*

| CommandType | Name                                      | Source        |
|-------------|-------------------------------------------|---------------|
|             |                                           |               |
| Function    | Disable-NetworkSwitchEthernetPort         | NetworkSwitch |
| Function    | Disable-NetworkSwitchFeature              | NetworkSwitch |
| Function    | Disable-NetworkSwitchVlan                 | NetworkSwitch |
| Function    | Enable-NetworkSwitchEthernetPort          | NetworkSwitch |
| Function    | Enable-NetworkSwitchFeature               | NetworkSwitch |
| Function    | Enable-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Get-NetworkSwitchEthernetPort             | NetworkSwitch |
| Function    | Get-NetworkSwitchFeature                  | NetworkSwitch |
| Function    | Get-NetworkSwitchGlobalData               | NetworkSwitch |
| Function    | Get-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | New-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | Remove-NetworkSwitchEthernetPortIPAddress | NetworkSwitch |
| Function    | Remove-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Restore-NetworkSwitchConfiguration        | NetworkSwitch |
| Function    | Save-NetworkSwitchConfiguration           | NetworkSwitch |
| Function    | Set-NetworkSwitchEthernetPortIPAddress    | NetworkSwitch |
| Function    | Set-NetworkSwitchPortMode                 | NetworkSwitch |
| Function    | Set-NetworkSwitchPortProperty             | NetworkSwitch |
| Function    | Set-NetworkSwitchVlanProperty             | NetworkSwitch |
```

<span data-ttu-id="eb730-128">Więcej informacji znajduje się w Jeffrey Snover WMF 5.0 Podgląd anonsu wpis w blogu: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span><span class="sxs-lookup"><span data-stu-id="eb730-128">More information is available in Jeffrey Snover’s WMF 5.0 Preview announcement blog post: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span></span>
