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
ms.openlocfilehash: d0330f082262b68486a582ed95c7a520be1e184c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081312"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="64bc0-102">Przykładowy kod RunSpace06</span><span class="sxs-lookup"><span data-stu-id="64bc0-102">RunSpace06 Code Sample</span></span>

<span data-ttu-id="64bc0-103">Poniżej przedstawiono kod źródłowy dla przykładowych Runspace06 opisanego w [konfigurowania obszaru działania, za pomocą przystawki programu PowerShell Windows](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span><span class="sxs-lookup"><span data-stu-id="64bc0-103">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span> <span data-ttu-id="64bc0-104">Ta przykładowa aplikacja tworzy obszar działania, w oparciu o przystawki programu Windows PowerShell, który jest następnie używany do uruchomienia potoku za pomocą jednego polecenia.</span><span class="sxs-lookup"><span data-stu-id="64bc0-104">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="64bc0-105">Aby to zrobić, aplikacja tworzy informacji o konfiguracji obszaru działania, tworzy obszar działania, tworzy potok z jednym poleceniem i następnie uruchamia potok.</span><span class="sxs-lookup"><span data-stu-id="64bc0-105">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="64bc0-106">Możesz pobrać C# pliku źródłowego (runspace06.cs) przy użyciu Windows oprogramowania Development Kit dla Windows Vista i składników środowiska wykonawczego programu Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="64bc0-106">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="64bc0-107">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="64bc0-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="64bc0-108">Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.</span><span class="sxs-lookup"><span data-stu-id="64bc0-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="64bc0-109">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="64bc0-109">Code Sample</span></span>

[!code-csharp[Runspace06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a><span data-ttu-id="64bc0-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="64bc0-110">See Also</span></span>

[<span data-ttu-id="64bc0-111">Windows PowerShell przewodnik</span><span class="sxs-lookup"><span data-stu-id="64bc0-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="64bc0-112">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="64bc0-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)