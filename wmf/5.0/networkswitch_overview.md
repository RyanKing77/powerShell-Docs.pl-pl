---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 61c5df1b64cb9c54f9c7372a56e77abf319658dd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085141"
---
# <a name="network-switch-management-with-powershell"></a><span data-ttu-id="b0bda-102">Zarządzanie przełącznikiem sieciowym przy użyciu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="b0bda-102">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="b0bda-103">**Get NetworkSwitchEthernetPort** polecenie cmdlet zwraca teraz następujące dodatkowe informacje o wystąpieniach:</span><span class="sxs-lookup"><span data-stu-id="b0bda-103">The **Get-NetworkSwitchEthernetPort** cmdlet now returns the following additional information with instances:</span></span>

- <span data-ttu-id="b0bda-104">Adres IP — adres IP skojarzony z portem</span><span class="sxs-lookup"><span data-stu-id="b0bda-104">IPAddress – the IP address associated with the port</span></span>
- <span data-ttu-id="b0bda-105">PortMode — tryb portu: dostępu, trasy lub magistrali</span><span class="sxs-lookup"><span data-stu-id="b0bda-105">PortMode – the port mode: access, route, or trunk</span></span>
- <span data-ttu-id="b0bda-106">AccessVLAN — identyfikator sieci VLAN skojarzone z tym portem w trybie dostępu</span><span class="sxs-lookup"><span data-stu-id="b0bda-106">AccessVLAN – the ID of the VLAN associated with this port in access mode</span></span>
- <span data-ttu-id="b0bda-107">TrunkedVLANList — Lista identyfikatorów sieci VLAN skojarzone z tym portem w trybie magistrali</span><span class="sxs-lookup"><span data-stu-id="b0bda-107">TrunkedVLANList – a list of IDs of VLANs associated with this port in trunk mode</span></span>

## <a name="fundamental-network-switch-management-with-windows-powershell"></a><span data-ttu-id="b0bda-108">Zarządzanie przełącznikiem sieciowym podstawowe za pomocą programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b0bda-108">Fundamental network switch management with Windows PowerShell</span></span>

<span data-ttu-id="b0bda-109">Przełącznika sieci poleceń cmdlet, wprowadzone w programie WMF 5.0 umożliwiają zastosowanie przełącznika, wirtualnej sieci LAN (VLAN) i podstawowa konfiguracja portu przełącznika sieci warstwy 2 do przełączników sieciowych z certyfikatem logo systemu Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="b0bda-109">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="b0bda-110">Firmy Microsoft pozostaje wszelkich starań, aby obsługa [abstrakcji centrum danych](http://technet.microsoft.com/cloud/dal.aspx) wizji warstwy (DAL) i wyświetlania wartości dla klientów i partnerów, w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="b0bda-110">Microsoft remains committed to supporting the [Datacenter Abstraction](http://technet.microsoft.com/cloud/dal.aspx) Layer (DAL) vision, and to show value for our customers and partners in this space.</span></span> <span data-ttu-id="b0bda-111">Za pomocą tych poleceń cmdlet można wykonywać:</span><span class="sxs-lookup"><span data-stu-id="b0bda-111">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="b0bda-112">Globalne przełącznika konfiguracji, takich jak:</span><span class="sxs-lookup"><span data-stu-id="b0bda-112">Global switch configuration, such as:</span></span>
    - <span data-ttu-id="b0bda-113">Ustaw nazwę hosta</span><span class="sxs-lookup"><span data-stu-id="b0bda-113">Set host name</span></span>
    - <span data-ttu-id="b0bda-114">Transparent przełącznik set</span><span class="sxs-lookup"><span data-stu-id="b0bda-114">Set switch banner</span></span>
    - <span data-ttu-id="b0bda-115">Zachowaj konfigurację</span><span class="sxs-lookup"><span data-stu-id="b0bda-115">Persist configuration</span></span>
    - <span data-ttu-id="b0bda-116">Włącza lub wyłącza funkcję</span><span class="sxs-lookup"><span data-stu-id="b0bda-116">Enable or disable feature</span></span>

- <span data-ttu-id="b0bda-117">Konfiguracja sieci VLAN:</span><span class="sxs-lookup"><span data-stu-id="b0bda-117">VLAN configuration:</span></span>
    - <span data-ttu-id="b0bda-118">Tworzenie lub usuwanie sieci VLAN</span><span class="sxs-lookup"><span data-stu-id="b0bda-118">Create or remove VLAN</span></span>
    - <span data-ttu-id="b0bda-119">Włączanie lub wyłączanie sieci VLAN</span><span class="sxs-lookup"><span data-stu-id="b0bda-119">Enable or disable VLAN</span></span>
    - <span data-ttu-id="b0bda-120">Wyliczanie sieci VLAN</span><span class="sxs-lookup"><span data-stu-id="b0bda-120">Enumerate VLAN</span></span>
    - <span data-ttu-id="b0bda-121">Przyjazna nazwa zestawu do sieci VLAN</span><span class="sxs-lookup"><span data-stu-id="b0bda-121">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="b0bda-122">Konfiguracja portu warstwy 2:</span><span class="sxs-lookup"><span data-stu-id="b0bda-122">Layer 2 port configuration:</span></span>
    - <span data-ttu-id="b0bda-123">Wyliczanie portów</span><span class="sxs-lookup"><span data-stu-id="b0bda-123">Enumerate ports</span></span>
    - <span data-ttu-id="b0bda-124">Włączać lub wyłączać porty</span><span class="sxs-lookup"><span data-stu-id="b0bda-124">Enable or disable ports</span></span>
    - <span data-ttu-id="b0bda-125">Tryby portu zestawu i właściwości</span><span class="sxs-lookup"><span data-stu-id="b0bda-125">Set port modes and properties</span></span>
    - <span data-ttu-id="b0bda-126">Dodawanie lub kojarzenie sieci VLAN na magistrali lub dostęp przy użyciu portu</span><span class="sxs-lookup"><span data-stu-id="b0bda-126">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="b0bda-127">Zacznij jego eksplorację od wyszukiwania dla wszystkich poleceń cmdlet NetworkSwitch!</span><span class="sxs-lookup"><span data-stu-id="b0bda-127">Start exploring by looking for all of the NetworkSwitch cmdlets!</span></span>

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

<span data-ttu-id="b0bda-128">Więcej informacji znajduje się w Jeffrey Snover WMF 5.0 Podgląd ogłoszenia wpis w blogu: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span><span class="sxs-lookup"><span data-stu-id="b0bda-128">More information is available in Jeffrey Snover’s WMF 5.0 Preview announcement blog post: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span></span>
