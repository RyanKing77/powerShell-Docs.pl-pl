---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 11b5e36f703c242e0bc820ab19d11d39305fa90c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="network-switch-management-with-powershell"></a>Zarządzanie przełącznikiem sieciowym przy użyciu programu PowerShell

**Get NetworkSwitchEthernetPort** polecenie cmdlet zwraca teraz następujące dodatkowe informacje z wystąpień:

- Adres IP — adres IP skojarzony z portem
- PortMode — tryb portu: dostępu, trasy lub magistrali
- AccessVLAN — identyfikator sieci VLAN skojarzone z tym portem w trybie dostępu
- TrunkedVLANList — Lista identyfikatorów sieci VLAN skojarzone z tym portem w trybie magistrali

## <a name="fundamental-network-switch-management-with-windows-powershell"></a>Zarządzanie przełącznika podstawowych sieci za pomocą środowiska Windows PowerShell

Przełącznik sieci poleceń cmdlet, wprowadzone w programie WMF 5.0, umożliwiają przełącznika, wirtualnych sieci LAN (VLAN) i podstawowa konfiguracja portu przełącznika sieci warstwy 2 przełączniki sieciowe certyfikatem logo systemu Windows Server 2012 R2. Microsoft pozostaje starań, aby obsługa [abstrakcji centrum danych](http://technet.microsoft.com/cloud/dal.aspx) wizji warstwy (DAL) i wyświetlania wartości w naszym klientom i partnerom w tym miejscu. Przy użyciu tych poleceń cmdlet można wykonywać:

- Globalny przełącznika konfiguracji, takich jak:
    - Nazwa hosta zestawu
    - Transparent przełącznika zestawu
    - Zachowaj konfigurację
    - Włączanie lub wyłączanie funkcji

- Konfiguracja sieci VLAN:
    - Tworzenie lub usuwanie sieci VLAN
    - Włącz lub wyłącz sieci VLAN
    - Wyliczanie sieci VLAN
    - Ustawianie przyjaznej nazwy sieć VLAN

- Konfiguracja portów warstwy 2:
    - Wyliczanie portów
    - Włączać lub wyłączać porty
    - Tryby portu zestawu i właściwości
    - Dodawanie lub kojarzenie z sieci VLAN na magistrali lub dostęp na porcie

Rozpocznij, przeglądanie, wyszukując wszystkich poleceń cmdlet NetworkSwitch!

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

Więcej informacji znajduje się w Jeffrey Snover WMF 5.0 Podgląd anonsu wpis w blogu: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx>
