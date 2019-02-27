---
title: StopProc Tutorial | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a142aeb6-9c11-44a0-b34f-1f9470fa347b
caps.latest.revision: 5
ms.openlocfilehash: 6e1c8a4709988adfa59bda14eb3af52b0a79f1df
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847061"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="4099f-102">StopProc — samouczek</span><span class="sxs-lookup"><span data-stu-id="4099f-102">StopProc Tutorial</span></span>

<span data-ttu-id="4099f-103">Ta sekcja zawiera samouczek tworzenia polecenia cmdlet Stop-Proc, co jest bardzo podobne do [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) dostarczane przez środowisko Windows PowerShell polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4099f-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="4099f-104">Ten samouczek zawiera fragmenty kodu, które ilustrują implementacji poleceń cmdlet oraz objaśnienia dotyczące kodu.</span><span class="sxs-lookup"><span data-stu-id="4099f-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>
<span data-ttu-id="4099f-105">Ta sekcja zawiera samouczek tworzenia polecenia cmdlet Stop-Proc, co jest bardzo podobne do [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) dostarczane przez środowisko Windows PowerShell polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4099f-105">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="4099f-106">Ten samouczek zawiera fragmenty kodu, które ilustrują implementacji poleceń cmdlet oraz objaśnienia dotyczące kodu.</span><span class="sxs-lookup"><span data-stu-id="4099f-106">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="4099f-107">Tematy w tym samouczku</span><span class="sxs-lookup"><span data-stu-id="4099f-107">Topics in this Tutorial</span></span>

<span data-ttu-id="4099f-108">Tematy w tym samouczku są przeznaczone do przeczytania po kolei, za pomocą każdego tematu, opierając się na co zostało omówione w poprzednim temacie.</span><span class="sxs-lookup"><span data-stu-id="4099f-108">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="4099f-109">[Tworzenie polecenia Cmdlet, który modyfikuje System](./creating-a-cmdlet-that-modifies-the-system.md) w tej sekcji opisano sposób tworzenia polecenia cmdlet, które obsługuje modyfikacji systemu, takie jak zatrzymywanie procesu uruchomionego na komputerze.</span><span class="sxs-lookup"><span data-stu-id="4099f-109">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="4099f-110">[Dodawanie użytkownika wiadomości do polecenia Cmdlet usługi](./adding-user-messages-to-your-cmdlet.md) w tej sekcji opisano sposób dodawania możliwość zapisu komunikaty użytkownika, komunikaty debugowania, ostrzeżenia i informacje o postępie do Twojego polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4099f-110">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="4099f-111">[Dodawanie aliasy, rozszerzenia symboli wieloznacznych i pomocy do parametrów polecenia Cmdlet](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) w tej sekcji opisano sposób tworzenia polecenia cmdlet, które obsługuje aliasów parametrów, pomocy i rozwijanie symbolu wieloznacznego.</span><span class="sxs-lookup"><span data-stu-id="4099f-111">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="4099f-112">[Dodawanie Ustawia parametr do poleceń cmdlet](./adding-parameter-sets-to-a-cmdlet.md) w tej sekcji opisano sposób dodawania zestawami parametrów do polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4099f-112">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="4099f-113">Zestawy parametrów Zezwalaj na polecenie cmdlet, aby działać inaczej w zależności od parametry są określone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4099f-113">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="4099f-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4099f-114">See Also</span></span>

[<span data-ttu-id="4099f-115">Tworzenie polecenia Cmdlet, który modyfikuje systemu</span><span class="sxs-lookup"><span data-stu-id="4099f-115">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="4099f-116">Dodawanie użytkownika wiadomości do Twojego polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4099f-116">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="4099f-117">Dodawanie aliasy, rozszerzenia symboli wieloznacznych i pomocy do parametrów polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4099f-117">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="4099f-118">Dodanie parametru ustawia do poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="4099f-118">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="4099f-119">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4099f-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
