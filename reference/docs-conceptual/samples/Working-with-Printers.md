---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Praca z drukarkami
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: fce1bc129ada3c509c55941a59a70de230edf68f
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470956"
---
# <a name="working-with-printers"></a>Praca z drukarkami

Za pomocą programu Windows PowerShell do zarządzania drukarkami przy użyciu usługi WMI i obiekt WScript.Network COM z hosta skryptów systemu Windows. Firma Microsoft użyje kombinacji obu narzędzia do zademonstrowania określonych zadań.

## <a name="listing-printer-connections"></a>Lista połączeń drukarek

Najprostszym sposobem, aby wyświetlić listę drukarek zainstalowanych na komputerze jest użycie usługi WMI **Win32_Printer** klasy:

```powershell
Get-WmiObject -Class Win32_Printer
```

Możesz także wyświetlić listę drukarek za pomocą **WScript.Network** obiekt COM, która jest zwykle używana w skryptach hosta skryptów systemu Windows:

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

Ponieważ to polecenie zwraca kolekcję prostego ciągu nazwy portu i nazwy urządzenia drukarki, bez żadnych wyróżniający etykiet, nie jest łatwe do interpretowania.

## <a name="adding-a-network-printer"></a>Dodawanie drukarki sieciowej

Aby dodać nowe drukarki sieciowej, użyj **WScript.Network**:

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a>Ustawienia drukarki domyślnej

Aby ustawić domyślną drukarkę za pomocą usługi WMI, Znajdź drukarki w **Win32_Printer** kolekcji i Wywołaj **SetDefaultPrinter** metody:

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

**WScript.Network** jest nieco uproszczona do użycia, ponieważ ma ona **SetDefaultPrinter** metody, która przyjmuje jako argument tylko nazwę drukarki:

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a>Usunięcie połączenia drukarki

Aby usunąć połączenie drukarki, użyj **WScript.Network RemovePrinterConnection** metody:

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```
