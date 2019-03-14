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
ms.openlocfilehash: 27c8e2c7525aba38e69e50b2b7fd3b18b8e54989
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794403"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="56ff4-102">StopProc — samouczek</span><span class="sxs-lookup"><span data-stu-id="56ff4-102">StopProc Tutorial</span></span>

<span data-ttu-id="56ff4-103">Ta sekcja zawiera samouczek tworzenia polecenia cmdlet Stop-Proc, co jest bardzo podobne do [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) dostarczane przez środowisko Windows PowerShell polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="56ff4-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="56ff4-104">Ten samouczek zawiera fragmenty kodu, które ilustrują implementacji poleceń cmdlet oraz objaśnienia dotyczące kodu.</span><span class="sxs-lookup"><span data-stu-id="56ff4-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="56ff4-105">Tematy w tym samouczku</span><span class="sxs-lookup"><span data-stu-id="56ff4-105">Topics in this Tutorial</span></span>

<span data-ttu-id="56ff4-106">Tematy w tym samouczku są przeznaczone do przeczytania po kolei, za pomocą każdego tematu, opierając się na co zostało omówione w poprzednim temacie.</span><span class="sxs-lookup"><span data-stu-id="56ff4-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="56ff4-107">[Tworzenie polecenia Cmdlet, który modyfikuje System](./creating-a-cmdlet-that-modifies-the-system.md) w tej sekcji opisano sposób tworzenia polecenia cmdlet, które obsługuje modyfikacji systemu, takie jak zatrzymywanie procesu uruchomionego na komputerze.</span><span class="sxs-lookup"><span data-stu-id="56ff4-107">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="56ff4-108">[Dodawanie użytkownika wiadomości do polecenia Cmdlet usługi](./adding-user-messages-to-your-cmdlet.md) w tej sekcji opisano sposób dodawania możliwość zapisu komunikaty użytkownika, komunikaty debugowania, ostrzeżenia i informacje o postępie do Twojego polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="56ff4-108">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="56ff4-109">[Dodawanie aliasy, rozszerzenia symboli wieloznacznych i pomocy do parametrów polecenia Cmdlet](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) w tej sekcji opisano sposób tworzenia polecenia cmdlet, które obsługuje aliasów parametrów, pomocy i rozwijanie symbolu wieloznacznego.</span><span class="sxs-lookup"><span data-stu-id="56ff4-109">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="56ff4-110">[Dodawanie Ustawia parametr do poleceń cmdlet](./adding-parameter-sets-to-a-cmdlet.md) w tej sekcji opisano sposób dodawania zestawami parametrów do polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="56ff4-110">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="56ff4-111">Zestawy parametrów Zezwalaj na polecenie cmdlet, aby działać inaczej w zależności od parametry są określone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="56ff4-111">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="56ff4-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56ff4-112">See Also</span></span>

[<span data-ttu-id="56ff4-113">Tworzenie polecenia Cmdlet, który modyfikuje systemu</span><span class="sxs-lookup"><span data-stu-id="56ff4-113">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="56ff4-114">Dodawanie użytkownika wiadomości do Twojego polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="56ff4-114">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="56ff4-115">Dodawanie aliasy, rozszerzenia symboli wieloznacznych i pomocy do parametrów polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="56ff4-115">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="56ff4-116">Dodanie parametru ustawia do poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="56ff4-116">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="56ff4-117">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="56ff4-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
