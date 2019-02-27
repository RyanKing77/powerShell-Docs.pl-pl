---
title: Raportowanie błędów programu Windows PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61b7773a-c346-4835-a928-7212dc4c85bc
caps.latest.revision: 7
ms.openlocfilehash: 259de341fd2fcce2b0c4629f806b4348cba1ff2c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846921"
---
# <a name="windows-powershell-error-reporting"></a><span data-ttu-id="71671-102">Raportowanie błędów programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="71671-102">Windows PowerShell Error Reporting</span></span>

<span data-ttu-id="71671-103">Tematy w tej sekcji omówiono, jak polecenia cmdlet raportowania błędów.</span><span class="sxs-lookup"><span data-stu-id="71671-103">The topics in this section discuss how cmdlets report errors.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="71671-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="71671-104">In This Section</span></span>

<span data-ttu-id="71671-105">[Pojęcia zgłoszenie błędu](./error-reporting-concepts.md) opisano dwa mechanizmy, które poleceń cmdlet służy do zgłaszania błędów.</span><span class="sxs-lookup"><span data-stu-id="71671-105">[Error Reporting Concepts](./error-reporting-concepts.md) Describes the two mechanisms that cmdlets can use to report errors.</span></span>

<span data-ttu-id="71671-106">[Kończenie błędy](./terminating-errors.md) opisuje metody używane do zgłaszania przerywa błędy, gdzie tę metodę można wywołać z w ramach polecenia cmdlet i wyjątki, które mogą być zwrócone przez środowisko uruchomieniowe programu Windows PowerShell, gdy wywoływana jest metoda.</span><span class="sxs-lookup"><span data-stu-id="71671-106">[Terminating Errors](./terminating-errors.md) Describes the method used to report terminating errors, where that method can be called from within the cmdlet, and exceptions that can be returned by the Windows PowerShell runtime when the method is called.</span></span>

<span data-ttu-id="71671-107">[Błędy niepowodujący](./non-terminating-errors.md) opisuje metody używane do zgłaszania błędy niepowodujące i gdzie tę metodę można wywołać z w ramach polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="71671-107">[Non-Terminating Errors](./non-terminating-errors.md) Describes the method used to report non-terminating errors and where that method can be called from within the cmdlet.</span></span>

<span data-ttu-id="71671-108">[Wyświetlanie informacji o błędzie według kategorii](./displaying-error-information.md) w tym artykule omówiono sposób, że użytkownicy mogą wyświetlić błąd.</span><span class="sxs-lookup"><span data-stu-id="71671-108">[Displaying Error Information by Category](./displaying-error-information.md) Discusses the ways that users can display error.</span></span>

<span data-ttu-id="71671-109">[Windows PowerShell błąd rekordów](./windows-powershell-error-records.md) zawiera opis składników rekord błędu.</span><span class="sxs-lookup"><span data-stu-id="71671-109">[Windows PowerShell Error Records](./windows-powershell-error-records.md) Describes the components of an error record.</span></span>

<span data-ttu-id="71671-110">[Interpretowanie obiektów rekord błędu](./interpreting-errorrecord-objects.md) w tym artykule omówiono, jak rekord błędu obiekty są interpretowane.</span><span class="sxs-lookup"><span data-stu-id="71671-110">[Interpreting ErrorRecord Objects](./interpreting-errorrecord-objects.md) Discusses how ErrorRecord objects are interpreted.</span></span>

## <a name="see-also"></a><span data-ttu-id="71671-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71671-111">See Also</span></span>

[<span data-ttu-id="71671-112">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="71671-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
