---
title: Modułów i przystawek | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849959"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="a25a8-102">Moduły i przystawki</span><span class="sxs-lookup"><span data-stu-id="a25a8-102">Modules and Snap-ins</span></span>

<span data-ttu-id="a25a8-103">Polecenia cmdlet można dodać do sesji przy użyciu przystawki lub modułów (rozpoczętymi przez program Windows PowerShell 2.0). Gdy polecenie cmdlet jest dodawany do sesji, która może być uruchamiane programowo przez aplikację hosta lub interaktywnie w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="a25a8-103">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="a25a8-104">Zaleca się używać modułów jako metodę dostarczania dodanie polecenia cmdlet w sesji z następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="a25a8-104">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="a25a8-105">Moduły umożliwiają dodanie polecenia cmdlet, ładując zestaw gdzie polecenie cmdlet został zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="a25a8-105">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="a25a8-106">Nie ma potrzeby wdrażania klasy przystawki.</span><span class="sxs-lookup"><span data-stu-id="a25a8-106">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="a25a8-107">Moduły umożliwiają dodanie innych zasobów, takich jak zmienne, funkcje, skrypty, typy i formatowania plików i inne.</span><span class="sxs-lookup"><span data-stu-id="a25a8-107">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="a25a8-108">Przystawki można jedynie dodać polecenia cmdlet i dostawców do sesji.</span><span class="sxs-lookup"><span data-stu-id="a25a8-108">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="a25a8-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a25a8-109">See Also</span></span>

[<span data-ttu-id="a25a8-110">Pisanie modułu programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a25a8-110">Writing a Windows PowerShell Module</span></span>](../module/writing-a-windows-powershell-module.md)

[<span data-ttu-id="a25a8-111">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a25a8-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
