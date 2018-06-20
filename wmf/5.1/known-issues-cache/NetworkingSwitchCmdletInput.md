---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
contributor: vaibch
title: Błąd polecenia cmdlet Menedżera przełącznika sieciowego
ms.openlocfilehash: 197a25411a82e5d256a9420706535d5411991f1b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188687"
---
<span data-ttu-id="ac5e9-103">Polecenia cmdlet Menedżera przełącznika sieciowego może służyć do zarządzania przełączników sieciowych za pośrednictwem usługi WSMAN.</span><span class="sxs-lookup"><span data-stu-id="ac5e9-103">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="ac5e9-104">Kilka poleceń cmdlet tego modułu są w stanie akceptowania wartości z potoków.</span><span class="sxs-lookup"><span data-stu-id="ac5e9-104">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="ac5e9-105">W wersji zapoznawczej 5.1 WMF poleceń cmdlet, które może akceptować wartości z potoku wykonanie nie powiodło się podczas wartości nie są przekazywane za pośrednictwem potoków.</span><span class="sxs-lookup"><span data-stu-id="ac5e9-105">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="ac5e9-106">Jeśli parametr "InputObject" nie jest używany, polecenia cmdlet powinno być kontynuowane bez błędów.</span><span class="sxs-lookup"><span data-stu-id="ac5e9-106">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="ac5e9-107">Poniżej przedstawiono listę odpowiednich poleceń cmdlet tj. te polecenia cmdlet można zaakceptować wartości dla parametru "InputObject" z potoku.</span><span class="sxs-lookup"><span data-stu-id="ac5e9-107">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="ac5e9-108">Jeśli ta wartość nie zostanie przekazany z potoku wykonywania polecenia cmdlet nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="ac5e9-108">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="ac5e9-109">Wyłącz NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="ac5e9-109">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="ac5e9-110">Włącz NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="ac5e9-110">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="ac5e9-111">Usuń NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="ac5e9-111">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="ac5e9-112">Zestaw NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="ac5e9-112">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="ac5e9-113">Zestaw NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="ac5e9-113">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="ac5e9-114">Zestaw NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="ac5e9-114">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="ac5e9-115">Wyłącz NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="ac5e9-115">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="ac5e9-116">Włącz NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="ac5e9-116">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="ac5e9-117">Usuń NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="ac5e9-117">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="ac5e9-118">Zestaw NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="ac5e9-118">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="ac5e9-119">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="ac5e9-119">Resolution</span></span>
<span data-ttu-id="ac5e9-120">Polecenia cmdlet pracy poprawnie, gdy wartość parametru InputObject są przekazywane do niego za pośrednictwem potoku.</span><span class="sxs-lookup"><span data-stu-id="ac5e9-120">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="ac5e9-121">Kilka przykładów, które działają dla powyższych poleceń cmdlet są:</span><span class="sxs-lookup"><span data-stu-id="ac5e9-121">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="ac5e9-122">Wyłącz NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="ac5e9-122">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="ac5e9-123">Włącz NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="ac5e9-123">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="ac5e9-124">Usuń NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="ac5e9-124">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="ac5e9-125">Zestaw NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="ac5e9-125">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="ac5e9-126">Zestaw NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="ac5e9-126">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="ac5e9-127">Wyłącz NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="ac5e9-127">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="ac5e9-128">Włącz NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="ac5e9-128">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="ac5e9-129">Zestaw NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="ac5e9-129">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```
