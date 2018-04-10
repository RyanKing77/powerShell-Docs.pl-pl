---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Praca z drukarkami
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: 5638629fdf79371c8eff9ee9194b642034250fff
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-printers"></a>Praca z drukarkami

Można użyć programu Windows PowerShell do zarządzania drukarkami przy użyciu usługi WMI i obiektu WScript.Network COM z hosta skryptów systemu Windows. Używamy kombinację obu narzędzia do zaprezentowania określonych zadań.

### <a name="listing-printer-connections"></a>Lista połączeń drukarek

Najprostszym sposobem na liście drukarek zainstalowanych na komputerze jest użycie usługi WMI **Win32_Printer** klasy:

```powershell
Get-WmiObject -Class Win32_Printer -ComputerName
```

Można również podać drukarki przy użyciu **WScript.Network** obiektu COM, która jest zwykle używana w skryptach hosta skryptów systemu Windows:

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

Ponieważ to polecenie zwraca zbiór prostego ciągu nazwy portu i nazwy urządzenia drukarek bez wyróżniającą etykiety, nie jest łatwo zinterpretować.

### <a name="adding-a-network-printer"></a>Dodawanie drukarki sieciowej

Aby dodać nowe drukarki sieciowej, użyj **WScript.Network**:

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a>Ustawienia domyślnej drukarki

Aby ustawić drukarki domyślnej za pomocą usługi WMI, Znajdź drukarki w **Win32_Printer** kolekcji, a następnie wywołać **SetDefaultPrinter** metody:

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

**WScript.Network** nieco użycie jest łatwiejsze, ponieważ ma on **SetDefaultPrinter** metody pobierającej tylko nazwa drukarki jako argument:

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a>Usuwanie połączenia drukarek

Aby usunąć połączenie drukarki, użyj **WScript.Network RemovePrinterConnection** metody:

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```