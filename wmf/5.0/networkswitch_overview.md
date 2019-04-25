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
# <a name="network-switch-management-with-powershell"></a>Zarządzanie przełącznikiem sieciowym przy użyciu programu PowerShell

**Get NetworkSwitchEthernetPort** polecenie cmdlet zwraca teraz następujące dodatkowe informacje o wystąpieniach:

- Adres IP — adres IP skojarzony z portem
- PortMode — tryb portu: dostępu, trasy lub magistrali
- AccessVLAN — identyfikator sieci VLAN skojarzone z tym portem w trybie dostępu
- TrunkedVLANList — Lista identyfikatorów sieci VLAN skojarzone z tym portem w trybie magistrali

## <a name="fundamental-network-switch-management-with-windows-powershell"></a>Zarządzanie przełącznikiem sieciowym podstawowe za pomocą programu Windows PowerShell

Przełącznika sieci poleceń cmdlet, wprowadzone w programie WMF 5.0 umożliwiają zastosowanie przełącznika, wirtualnej sieci LAN (VLAN) i podstawowa konfiguracja portu przełącznika sieci warstwy 2 do przełączników sieciowych z certyfikatem logo systemu Windows Server 2012 R2. Firmy Microsoft pozostaje wszelkich starań, aby obsługa [abstrakcji centrum danych](http://technet.microsoft.com/cloud/dal.aspx) wizji warstwy (DAL) i wyświetlania wartości dla klientów i partnerów, w tym miejscu. Za pomocą tych poleceń cmdlet można wykonywać:

- Globalne przełącznika konfiguracji, takich jak:
    - Ustaw nazwę hosta
    - Transparent przełącznik set
    - Zachowaj konfigurację
    - Włącza lub wyłącza funkcję

- Konfiguracja sieci VLAN:
    - Tworzenie lub usuwanie sieci VLAN
    - Włączanie lub wyłączanie sieci VLAN
    - Wyliczanie sieci VLAN
    - Przyjazna nazwa zestawu do sieci VLAN

- Konfiguracja portu warstwy 2:
    - Wyliczanie portów
    - Włączać lub wyłączać porty
    - Tryby portu zestawu i właściwości
    - Dodawanie lub kojarzenie sieci VLAN na magistrali lub dostęp przy użyciu portu

Zacznij jego eksplorację od wyszukiwania dla wszystkich poleceń cmdlet NetworkSwitch!

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

Więcej informacji znajduje się w Jeffrey Snover WMF 5.0 Podgląd ogłoszenia wpis w blogu: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx>
