---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: 80852bf750700d549de24e150ffd89ac55b7bf88
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="network-switch-management-with-powershell"></a><span data-ttu-id="af243-102">Zarządzanie przełącznik sieci za pomocą programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="af243-102">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="af243-103">**Get NetworkSwitchEthernetPort** polecenie cmdlet zwraca teraz następujące dodatkowe informacje z wystąpień:</span><span class="sxs-lookup"><span data-stu-id="af243-103">The **Get-NetworkSwitchEthernetPort** cmdlet now returns the following additional information with instances:</span></span>

- <span data-ttu-id="af243-104">Adres IP — adres IP skojarzony z portem</span><span class="sxs-lookup"><span data-stu-id="af243-104">IPAddress – the IP address associated with the port</span></span>
- <span data-ttu-id="af243-105">PortMode — tryb portu: dostępu, trasy lub magistrali</span><span class="sxs-lookup"><span data-stu-id="af243-105">PortMode – the port mode: access, route, or trunk</span></span>
- <span data-ttu-id="af243-106">AccessVLAN — identyfikator sieci VLAN skojarzone z tym portem w trybie dostępu</span><span class="sxs-lookup"><span data-stu-id="af243-106">AccessVLAN – the ID of the VLAN associated with this port in access mode</span></span>
- <span data-ttu-id="af243-107">TrunkedVLANList — Lista identyfikatorów sieci VLAN skojarzone z tym portem w trybie magistrali</span><span class="sxs-lookup"><span data-stu-id="af243-107">TrunkedVLANList – a list of IDs of VLANs associated with this port in trunk mode</span></span>

## <a name="fundamental-network-switch-management-with-windows-powershell"></a><span data-ttu-id="af243-108">Zarządzanie przełącznika podstawowych sieci za pomocą środowiska Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="af243-108">Fundamental network switch management with Windows PowerShell</span></span>

<span data-ttu-id="af243-109">Przełącznik sieci poleceń cmdlet, wprowadzone w programie WMF 5.0, umożliwiają przełącznika, wirtualnych sieci LAN (VLAN) i podstawowa konfiguracja portu przełącznika sieci warstwy 2 przełączniki sieciowe certyfikatem logo systemu Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="af243-109">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="af243-110">Microsoft pozostaje starań, aby obsługa [abstrakcji centrum danych](http://technet.microsoft.com/en-us/cloud/dal.aspx) wizji warstwy (DAL) i wyświetlania wartości w naszym klientom i partnerom w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="af243-110">Microsoft remains committed to supporting the [Datacenter Abstraction](http://technet.microsoft.com/en-us/cloud/dal.aspx) Layer (DAL) vision, and to show value for our customers and partners in this space.</span></span> <span data-ttu-id="af243-111">Przy użyciu tych poleceń cmdlet można wykonywać:</span><span class="sxs-lookup"><span data-stu-id="af243-111">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="af243-112">Globalny przełącznika konfiguracji, takich jak:</span><span class="sxs-lookup"><span data-stu-id="af243-112">Global switch configuration, such as:</span></span>
    - <span data-ttu-id="af243-113">Nazwa hosta zestawu</span><span class="sxs-lookup"><span data-stu-id="af243-113">Set host name</span></span>
    - <span data-ttu-id="af243-114">Transparent przełącznika zestawu</span><span class="sxs-lookup"><span data-stu-id="af243-114">Set switch banner</span></span>
    - <span data-ttu-id="af243-115">Zachowaj konfigurację</span><span class="sxs-lookup"><span data-stu-id="af243-115">Persist configuration</span></span>
    - <span data-ttu-id="af243-116">Włączanie lub wyłączanie funkcji</span><span class="sxs-lookup"><span data-stu-id="af243-116">Enable or disable feature</span></span>

- <span data-ttu-id="af243-117">Konfiguracja sieci VLAN:</span><span class="sxs-lookup"><span data-stu-id="af243-117">VLAN configuration:</span></span>
    - <span data-ttu-id="af243-118">Tworzenie lub usuwanie sieci VLAN</span><span class="sxs-lookup"><span data-stu-id="af243-118">Create or remove VLAN</span></span>
    - <span data-ttu-id="af243-119">Włącz lub wyłącz sieci VLAN</span><span class="sxs-lookup"><span data-stu-id="af243-119">Enable or disable VLAN</span></span>
    - <span data-ttu-id="af243-120">Wyliczanie sieci VLAN</span><span class="sxs-lookup"><span data-stu-id="af243-120">Enumerate VLAN</span></span>
    - <span data-ttu-id="af243-121">Ustawianie przyjaznej nazwy sieć VLAN</span><span class="sxs-lookup"><span data-stu-id="af243-121">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="af243-122">Konfiguracja portów warstwy 2:</span><span class="sxs-lookup"><span data-stu-id="af243-122">Layer 2 port configuration:</span></span>
    - <span data-ttu-id="af243-123">Wyliczanie portów</span><span class="sxs-lookup"><span data-stu-id="af243-123">Enumerate ports</span></span>
    - <span data-ttu-id="af243-124">Włączać lub wyłączać porty</span><span class="sxs-lookup"><span data-stu-id="af243-124">Enable or disable ports</span></span>
    - <span data-ttu-id="af243-125">Tryby portu zestawu i właściwości</span><span class="sxs-lookup"><span data-stu-id="af243-125">Set port modes and properties</span></span>
    - <span data-ttu-id="af243-126">Dodawanie lub kojarzenie z sieci VLAN na magistrali lub dostęp na porcie</span><span class="sxs-lookup"><span data-stu-id="af243-126">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="af243-127">Rozpocznij, przeglądanie, wyszukując wszystkich poleceń cmdlet NetworkSwitch!</span><span class="sxs-lookup"><span data-stu-id="af243-127">Start exploring by looking for all of the NetworkSwitch cmdlets!</span></span>

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

<span data-ttu-id="af243-128">Więcej informacji znajduje się w Jeffrey Snover WMF 5.0 Podgląd anonsu wpis w blogu: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span><span class="sxs-lookup"><span data-stu-id="af243-128">More information is available in Jeffrey Snover’s WMF 5.0 Preview announcement blog post: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span></span>

