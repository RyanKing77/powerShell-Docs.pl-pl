---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: Praca z drukarkami
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: c8b4d728c9fddd39e1aeb56d6f9b8ffffe4c7292
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2017
---
# <a name="working-with-printers"></a><span data-ttu-id="1dac6-103">Praca z drukarkami</span><span class="sxs-lookup"><span data-stu-id="1dac6-103">Working with Printers</span></span>
<span data-ttu-id="1dac6-104">Można użyć programu Windows PowerShell do zarządzania drukarkami przy użyciu usługi WMI i obiektu WScript.Network COM z hosta skryptów systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1dac6-104">You can use Windows PowerShell to manage printers by using WMI and the WScript.Network COM object from WSH.</span></span> <span data-ttu-id="1dac6-105">Używamy kombinację obu narzędzia do zaprezentowania określonych zadań.</span><span class="sxs-lookup"><span data-stu-id="1dac6-105">We will use a mix of both tools to demonstrate specific tasks.</span></span>

### <a name="listing-printer-connections"></a><span data-ttu-id="1dac6-106">Lista połączeń drukarek</span><span class="sxs-lookup"><span data-stu-id="1dac6-106">Listing Printer Connections</span></span>
<span data-ttu-id="1dac6-107">Najprostszym sposobem na liście drukarek zainstalowanych na komputerze jest użycie usługi WMI **Win32_Printer** klasy:</span><span class="sxs-lookup"><span data-stu-id="1dac6-107">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```
Get-WmiObject -Class Win32_Printer -ComputerName
```

<span data-ttu-id="1dac6-108">Można również podać drukarki przy użyciu **WScript.Network** obiektu COM, która jest zwykle używana w skryptach hosta skryptów systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="1dac6-108">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="1dac6-109">Ponieważ to polecenie zwraca zbiór prostego ciągu nazwy portu i nazwy urządzenia drukarek bez wyróżniającą etykiety, nie jest łatwo zinterpretować.</span><span class="sxs-lookup"><span data-stu-id="1dac6-109">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

### <a name="adding-a-network-printer"></a><span data-ttu-id="1dac6-110">Dodawanie drukarki sieciowej</span><span class="sxs-lookup"><span data-stu-id="1dac6-110">Adding a Network Printer</span></span>
<span data-ttu-id="1dac6-111">Aby dodać nowe drukarki sieciowej, użyj **WScript.Network**:</span><span class="sxs-lookup"><span data-stu-id="1dac6-111">To add a new network printer, use **WScript.Network**:</span></span>

```
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a><span data-ttu-id="1dac6-112">Ustawienia domyślnej drukarki</span><span class="sxs-lookup"><span data-stu-id="1dac6-112">Setting a Default Printer</span></span>
<span data-ttu-id="1dac6-113">Aby ustawić drukarki domyślnej za pomocą usługi WMI, Znajdź drukarki w **Win32_Printer** kolekcji, a następnie wywołać **SetDefaultPrinter** metody:</span><span class="sxs-lookup"><span data-stu-id="1dac6-113">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

<span data-ttu-id="1dac6-114">**WScript.Network** nieco użycie jest łatwiejsze, ponieważ ma on **SetDefaultPrinter** metody pobierającej tylko nazwa drukarki jako argument:</span><span class="sxs-lookup"><span data-stu-id="1dac6-114">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a><span data-ttu-id="1dac6-115">Usuwanie połączenia drukarek</span><span class="sxs-lookup"><span data-stu-id="1dac6-115">Removing a Printer Connection</span></span>
<span data-ttu-id="1dac6-116">Aby usunąć połączenie drukarki, użyj **WScript.Network RemovePrinterConnection** metody:</span><span class="sxs-lookup"><span data-stu-id="1dac6-116">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```

