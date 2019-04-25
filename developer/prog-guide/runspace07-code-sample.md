---
title: Przykładowy kod RunSpace07 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: 064e7d7ea2ee173bbcdd75a9f3a6c12582afe17b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081295"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="f7990-102">Przykładowy kod RunSpace07</span><span class="sxs-lookup"><span data-stu-id="f7990-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="f7990-103">Poniżej przedstawiono kod źródłowy dla przykładowych Runspace07 opisanego w [tworzenia aplikacji, dodaje poleceń konsoli dla potoku](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span><span class="sxs-lookup"><span data-stu-id="f7990-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span> <span data-ttu-id="f7990-104">Ta przykładowa aplikacja tworzy obszar działania, tworzy potok, dodaje dwa polecenia do potoku i następnie uruchamia potok.</span><span class="sxs-lookup"><span data-stu-id="f7990-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="f7990-105">Polecenia dodane do potoku znajdują się `Get-Process` i `Measure-Object` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f7990-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="f7990-106">Możesz pobrać C# pliku źródłowego (runspace07.cs) przy użyciu programu Microsoft Windows oprogramowania Development Kit dla Windows Vista i programu Microsoft .NET Framework 3.0 Runtime składników.</span><span class="sxs-lookup"><span data-stu-id="f7990-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="f7990-107">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="f7990-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="f7990-108">Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.</span><span class="sxs-lookup"><span data-stu-id="f7990-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="f7990-109">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="f7990-109">Code Sample</span></span>

[!code-csharp[Runspace07.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a><span data-ttu-id="f7990-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7990-110">See Also</span></span>

[<span data-ttu-id="f7990-111">Windows PowerShell przewodnik</span><span class="sxs-lookup"><span data-stu-id="f7990-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="f7990-112">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f7990-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)