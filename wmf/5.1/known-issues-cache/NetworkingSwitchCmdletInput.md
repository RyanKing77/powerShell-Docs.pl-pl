---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
contributor: vaibch
title: Błąd polecenia cmdlet Menedżer przełącznika sieci
ms.openlocfilehash: a0f84c35974b6674faba4b0f19a28bd6e2490a96
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685249"
---
# <a name="network-switch-manager-cmdlets-failure"></a><span data-ttu-id="2762b-103">Błąd polecenia cmdlet Menedżer przełącznika sieci</span><span class="sxs-lookup"><span data-stu-id="2762b-103">Network Switch Manager Cmdlets Failure</span></span>

<span data-ttu-id="2762b-104">Polecenia cmdlet Menedżer przełącznika sieci może służyć do zarządzania przełącznikami sieciowymi za pośrednictwem usługi WS-MANAGEMENT.</span><span class="sxs-lookup"><span data-stu-id="2762b-104">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="2762b-105">Kilka poleceń cmdlet tego modułu są w stanie akceptując wartości z potoków.</span><span class="sxs-lookup"><span data-stu-id="2762b-105">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="2762b-106">W programu WMF 5.1 (wersja zapoznawcza) polecenia cmdlet, które może akceptować wartości z potoku nie do wykonania, gdy wartości nie zostaną przekazane za pośrednictwem potoków.</span><span class="sxs-lookup"><span data-stu-id="2762b-106">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="2762b-107">Jeśli parametr "InputObject" nie jest używany, polecenia cmdlet powinny nadal wykonane bez błędów.</span><span class="sxs-lookup"><span data-stu-id="2762b-107">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="2762b-108">Poniżej przedstawiono listę poleceń cmdlet dotyczy tj tych poleceń cmdlet może akceptować wartość dla parametru "InputObject" z potoku.</span><span class="sxs-lookup"><span data-stu-id="2762b-108">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="2762b-109">Jeśli ta wartość nie zostanie przekazany z potoku wykonywania polecenia cmdlet nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="2762b-109">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="2762b-110">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="2762b-110">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="2762b-111">Włącz NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="2762b-111">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="2762b-112">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="2762b-112">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="2762b-113">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="2762b-113">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="2762b-114">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="2762b-114">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="2762b-115">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="2762b-115">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="2762b-116">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="2762b-116">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="2762b-117">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="2762b-117">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="2762b-118">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="2762b-118">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="2762b-119">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="2762b-119">Set-NetworkSwitchVlanProperty</span></span>

## <a name="resolution"></a><span data-ttu-id="2762b-120">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="2762b-120">Resolution</span></span>

<span data-ttu-id="2762b-121">Dobrym rozwiązaniem, gdy wartość parametru InputObject są przekazywane do niego za pośrednictwem potoku pracy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2762b-121">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="2762b-122">Kilka przykładów, które działają w przypadku powyższych poleceń cmdlet są:</span><span class="sxs-lookup"><span data-stu-id="2762b-122">A few examples that work for the above cmdlets are:</span></span>

- `Disable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Enable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Remove-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $ipAddress = "192.168.10.1"
  $subnetAddress = "255.255.255.0"
  $port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchPortProperty`

  ```powershell
  $portProperties = @{Caption = "New Caption"}
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
  ```

- `Disable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Disable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Enable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Enable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Set-NetworkSwitchVlanProperty`

  ```powershell
  $properties = @{Caption = "New Caption"}
  $vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
  $vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
  ```