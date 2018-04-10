---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
contributor: vaibch
title: Błąd polecenia cmdlet Menedżera przełącznika sieciowego
ms.openlocfilehash: 626809513e7a8f1aa2c47a48c74e69ca4077f598
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
<span data-ttu-id="3d718-103">Polecenia cmdlet Menedżera przełącznika sieciowego może służyć do zarządzania przełączników sieciowych za pośrednictwem usługi WSMAN.</span><span class="sxs-lookup"><span data-stu-id="3d718-103">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="3d718-104">Kilka poleceń cmdlet tego modułu są w stanie akceptowania wartości z potoków.</span><span class="sxs-lookup"><span data-stu-id="3d718-104">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="3d718-105">W wersji zapoznawczej 5.1 WMF poleceń cmdlet, które może akceptować wartości z potoku wykonanie nie powiodło się podczas wartości nie są przekazywane za pośrednictwem potoków.</span><span class="sxs-lookup"><span data-stu-id="3d718-105">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="3d718-106">Jeśli parametr "InputObject" nie jest używany, polecenia cmdlet powinno być kontynuowane bez błędów.</span><span class="sxs-lookup"><span data-stu-id="3d718-106">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="3d718-107">Poniżej przedstawiono listę odpowiednich poleceń cmdlet tj. te polecenia cmdlet można zaakceptować wartości dla parametru "InputObject" z potoku.</span><span class="sxs-lookup"><span data-stu-id="3d718-107">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="3d718-108">Jeśli ta wartość nie zostanie przekazany z potoku wykonywania polecenia cmdlet nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="3d718-108">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="3d718-109">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="3d718-109">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="3d718-110">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="3d718-110">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="3d718-111">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="3d718-111">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="3d718-112">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="3d718-112">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="3d718-113">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="3d718-113">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="3d718-114">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="3d718-114">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="3d718-115">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="3d718-115">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="3d718-116">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="3d718-116">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="3d718-117">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="3d718-117">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="3d718-118">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="3d718-118">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="3d718-119">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="3d718-119">Resolution</span></span>
<span data-ttu-id="3d718-120">Polecenia cmdlet pracy poprawnie, gdy wartość parametru InputObject są przekazywane do niego za pośrednictwem potoku.</span><span class="sxs-lookup"><span data-stu-id="3d718-120">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="3d718-121">Kilka przykładów, które działają dla powyższych poleceń cmdlet są:</span><span class="sxs-lookup"><span data-stu-id="3d718-121">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="3d718-122">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="3d718-122">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="3d718-123">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="3d718-123">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="3d718-124">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="3d718-124">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="3d718-125">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="3d718-125">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="3d718-126">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="3d718-126">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="3d718-127">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="3d718-127">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="3d718-128">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="3d718-128">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="3d718-129">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="3d718-129">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```