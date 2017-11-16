---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
contributor: vaibch
title: "Błąd polecenia cmdlet Menedżera przełącznika sieciowego"
ms.openlocfilehash: d9fcdedbfc7d0c3f68624ed1db6259e04c3d06d1
ms.sourcegitcommit: fee03bb9802222078c8d5f6c8efb0698024406ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2017
---
<span data-ttu-id="3a2ca-103">Polecenia cmdlet Menedżera przełącznika sieciowego może służyć do zarządzania przełączników sieciowych za pośrednictwem usługi WSMAN.</span><span class="sxs-lookup"><span data-stu-id="3a2ca-103">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span> <span data-ttu-id="3a2ca-104">Kilka poleceń cmdlet tego modułu są w stanie akceptowania wartości z potoków.</span><span class="sxs-lookup"><span data-stu-id="3a2ca-104">A few cmdlets of this module are capable of accepting values from pipelines.</span></span> <span data-ttu-id="3a2ca-105">W wersji zapoznawczej 5.1 WMF poleceń cmdlet, które może akceptować wartości z potoku wykonanie nie powiodło się podczas wartości nie są przekazywane za pośrednictwem potoków.</span><span class="sxs-lookup"><span data-stu-id="3a2ca-105">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="3a2ca-106">Jeśli parametr "InputObject" nie jest używany, polecenia cmdlet powinno być kontynuowane bez błędów.</span><span class="sxs-lookup"><span data-stu-id="3a2ca-106">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="3a2ca-107">Poniżej przedstawiono listę odpowiednich poleceń cmdlet tj. te polecenia cmdlet można zaakceptować wartości dla parametru "InputObject" z potoku.</span><span class="sxs-lookup"><span data-stu-id="3a2ca-107">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span> <span data-ttu-id="3a2ca-108">Jeśli ta wartość nie zostanie przekazany z potoku wykonywania polecenia cmdlet nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="3a2ca-108">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="3a2ca-109">Wyłącz NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="3a2ca-109">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="3a2ca-110">Włącz NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="3a2ca-110">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="3a2ca-111">Usuń NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="3a2ca-111">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="3a2ca-112">Zestaw NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="3a2ca-112">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="3a2ca-113">Zestaw NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="3a2ca-113">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="3a2ca-114">Zestaw NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="3a2ca-114">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="3a2ca-115">Wyłącz NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="3a2ca-115">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="3a2ca-116">Włącz NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="3a2ca-116">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="3a2ca-117">Usuń NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="3a2ca-117">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="3a2ca-118">Zestaw NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="3a2ca-118">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="3a2ca-119">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="3a2ca-119">Resolution</span></span>
<span data-ttu-id="3a2ca-120">Polecenia cmdlet pracy poprawnie, gdy wartość parametru InputObject są przekazywane do niego za pośrednictwem potoku.</span><span class="sxs-lookup"><span data-stu-id="3a2ca-120">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="3a2ca-121">Kilka przykładów, które działają dla powyższych poleceń cmdlet są:</span><span class="sxs-lookup"><span data-stu-id="3a2ca-121">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="3a2ca-122">Wyłącz NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="3a2ca-122">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="3a2ca-123">Włącz NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="3a2ca-123">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="3a2ca-124">Usuń NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="3a2ca-124">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="3a2ca-125">Zestaw NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="3a2ca-125">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="3a2ca-126">Zestaw NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="3a2ca-126">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="3a2ca-127">Wyłącz NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="3a2ca-127">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="3a2ca-128">Włącz NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="3a2ca-128">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="3a2ca-129">Zestaw NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="3a2ca-129">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```

