---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Praca z drukarkami
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: 77ebb26369b6a40e9c8c7bbbc52347d614cbf083
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59292997"
---
# <a name="working-with-printers"></a><span data-ttu-id="db991-103">Praca z drukarkami</span><span class="sxs-lookup"><span data-stu-id="db991-103">Working with Printers</span></span>

<span data-ttu-id="db991-104">Za pomocą programu Windows PowerShell do zarządzania drukarkami przy użyciu usługi WMI i obiekt WScript.Network COM z hosta skryptów systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="db991-104">You can use Windows PowerShell to manage printers by using WMI and the WScript.Network COM object from WSH.</span></span> <span data-ttu-id="db991-105">Firma Microsoft użyje kombinacji obu narzędzia do zademonstrowania określonych zadań.</span><span class="sxs-lookup"><span data-stu-id="db991-105">We will use a mix of both tools to demonstrate specific tasks.</span></span>

## <a name="listing-printer-connections"></a><span data-ttu-id="db991-106">Lista połączeń drukarek</span><span class="sxs-lookup"><span data-stu-id="db991-106">Listing Printer Connections</span></span>

<span data-ttu-id="db991-107">Najprostszym sposobem, aby wyświetlić listę drukarek zainstalowanych na komputerze jest użycie usługi WMI **Win32_Printer** klasy:</span><span class="sxs-lookup"><span data-stu-id="db991-107">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```powershell
Get-WmiObject -Class Win32_Printer -ComputerName
```

<span data-ttu-id="db991-108">Możesz także wyświetlić listę drukarek za pomocą **WScript.Network** obiekt COM, która jest zwykle używana w skryptach hosta skryptów systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="db991-108">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="db991-109">Ponieważ to polecenie zwraca kolekcję prostego ciągu nazwy portu i nazwy urządzenia drukarki, bez żadnych wyróżniający etykiet, nie jest łatwe do interpretowania.</span><span class="sxs-lookup"><span data-stu-id="db991-109">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

## <a name="adding-a-network-printer"></a><span data-ttu-id="db991-110">Dodawanie drukarki sieciowej</span><span class="sxs-lookup"><span data-stu-id="db991-110">Adding a Network Printer</span></span>

<span data-ttu-id="db991-111">Aby dodać nowe drukarki sieciowej, użyj **WScript.Network**:</span><span class="sxs-lookup"><span data-stu-id="db991-111">To add a new network printer, use **WScript.Network**:</span></span>

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a><span data-ttu-id="db991-112">Ustawienia drukarki domyślnej</span><span class="sxs-lookup"><span data-stu-id="db991-112">Setting a Default Printer</span></span>

<span data-ttu-id="db991-113">Aby ustawić domyślną drukarkę za pomocą usługi WMI, Znajdź drukarki w **Win32_Printer** kolekcji i Wywołaj **SetDefaultPrinter** metody:</span><span class="sxs-lookup"><span data-stu-id="db991-113">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

<span data-ttu-id="db991-114">**WScript.Network** jest nieco uproszczona do użycia, ponieważ ma ona **SetDefaultPrinter** metody, która przyjmuje jako argument tylko nazwę drukarki:</span><span class="sxs-lookup"><span data-stu-id="db991-114">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a><span data-ttu-id="db991-115">Usunięcie połączenia drukarki</span><span class="sxs-lookup"><span data-stu-id="db991-115">Removing a Printer Connection</span></span>

<span data-ttu-id="db991-116">Aby usunąć połączenie drukarki, użyj **WScript.Network RemovePrinterConnection** metody:</span><span class="sxs-lookup"><span data-stu-id="db991-116">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```