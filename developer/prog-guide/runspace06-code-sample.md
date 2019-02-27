---
title: Przykładowy kod RunSpace06 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: 2874f9df3f5166fbe14deb5b128674540c0d6701
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845437"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="6aea9-102">Przykładowy kod RunSpace06</span><span class="sxs-lookup"><span data-stu-id="6aea9-102">RunSpace06 Code Sample</span></span>

<span data-ttu-id="6aea9-103">Poniżej przedstawiono kod źródłowy dla przykładowych Runspace06 opisanego w [konfigurowania obszaru działania, za pomocą przystawki programu PowerShell Windows](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span><span class="sxs-lookup"><span data-stu-id="6aea9-103">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span> <span data-ttu-id="6aea9-104">Ta przykładowa aplikacja tworzy obszar działania, w oparciu o przystawki programu Windows PowerShell, który jest następnie używany do uruchomienia potoku za pomocą jednego polecenia.</span><span class="sxs-lookup"><span data-stu-id="6aea9-104">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="6aea9-105">Aby to zrobić, aplikacja tworzy informacji o konfiguracji obszaru działania, tworzy obszar działania, tworzy potok z jednym poleceniem i następnie uruchamia potok.</span><span class="sxs-lookup"><span data-stu-id="6aea9-105">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="6aea9-106">Możesz pobrać C# pliku źródłowego (runspace06.cs) przy użyciu Windows oprogramowania Development Kit dla Windows Vista i składników środowiska wykonawczego programu Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="6aea9-106">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="6aea9-107">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="6aea9-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="6aea9-108">Możesz pobrać C# pliku źródłowego (runspace06.cs) przy użyciu Windows oprogramowania Development Kit dla Windows Vista i składników środowiska wykonawczego programu Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="6aea9-108">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="6aea9-109">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="6aea9-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="6aea9-110">Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.</span><span class="sxs-lookup"><span data-stu-id="6aea9-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6aea9-111">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="6aea9-111">Code Sample</span></span>

[!code-csharp[Runspace06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a><span data-ttu-id="6aea9-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6aea9-112">See Also</span></span>

[<span data-ttu-id="6aea9-113">Windows PowerShell przewodnik</span><span class="sxs-lookup"><span data-stu-id="6aea9-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="6aea9-114">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6aea9-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)