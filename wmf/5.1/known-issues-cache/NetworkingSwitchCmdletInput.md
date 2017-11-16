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
Polecenia cmdlet Menedżera przełącznika sieciowego może służyć do zarządzania przełączników sieciowych za pośrednictwem usługi WSMAN. Kilka poleceń cmdlet tego modułu są w stanie akceptowania wartości z potoków. W wersji zapoznawczej 5.1 WMF poleceń cmdlet, które może akceptować wartości z potoku wykonanie nie powiodło się podczas wartości nie są przekazywane za pośrednictwem potoków.

Jeśli parametr "InputObject" nie jest używany, polecenia cmdlet powinno być kontynuowane bez błędów.

Poniżej przedstawiono listę odpowiednich poleceń cmdlet tj. te polecenia cmdlet można zaakceptować wartości dla parametru "InputObject" z potoku. Jeśli ta wartość nie zostanie przekazany z potoku wykonywania polecenia cmdlet nie powiedzie się.

- Wyłącz NetworkSwitchEthernetPort
- Włącz NetworkSwitchEthernetPort
- Usuń NetworkSwitchEthernetPortIPAddress
- Zestaw NetworkSwitchEthernetPortIPAddress
- Zestaw NetworkSwitchPortMode
- Zestaw NetworkSwitchPortProperty
- Wyłącz NetworkSwitchFeature
- Włącz NetworkSwitchFeature
- Usuń NetworkSwitchVlan
- Zestaw NetworkSwitchVlanProperty

### <a name="resolution"></a>Rozwiązanie
Polecenia cmdlet pracy poprawnie, gdy wartość parametru InputObject są przekazywane do niego za pośrednictwem potoku. Kilka przykładów, które działają dla powyższych poleceń cmdlet są:

- Wyłącz NetworkSwitchEthernetPort
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- Włącz NetworkSwitchEthernetPort
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- Usuń NetworkSwitchEthernetPortIPAddress
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- Zestaw NetworkSwitchEthernetPortIPAddress
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- Zestaw NetworkSwitchPortProperty
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- Wyłącz NetworkSwitchFeature
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- Włącz NetworkSwitchFeature
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- Zestaw NetworkSwitchVlanProperty
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```

