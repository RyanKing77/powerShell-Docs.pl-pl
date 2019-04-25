---
title: Przykładowy kod RunSpace09 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: e21ef8685598db9a1ae0fcd86051386af526f2a5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081227"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="aa03e-102">Przykładowy kod RunSpace09</span><span class="sxs-lookup"><span data-stu-id="aa03e-102">RunSpace09 Code Sample</span></span>

<span data-ttu-id="aa03e-103">Poniżej przedstawiono kod źródłowy dla przykładowych Runspace09 opisanego w [tworzenia konsoli aplikacji, wywołuje potok asynchronicznie](http://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span><span class="sxs-lookup"><span data-stu-id="aa03e-103">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](http://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span> <span data-ttu-id="aa03e-104">Ta przykładowa aplikacja tworzy i otwiera obszar działania, tworzy i asynchronicznie wywołuje potok, a następnie używa potoku zdarzeń w celu asynchronicznego przetwarzania skryptu.</span><span class="sxs-lookup"><span data-stu-id="aa03e-104">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="aa03e-105">Skrypt, który jest uruchamiany przez tę aplikację tworzy liczb całkowitych od 1 do 10 w 0,5 sekund (500 ms).</span><span class="sxs-lookup"><span data-stu-id="aa03e-105">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="aa03e-106">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="aa03e-106">Code Sample</span></span>

[!code-csharp[Runspace09.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a><span data-ttu-id="aa03e-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa03e-107">See Also</span></span>

[<span data-ttu-id="aa03e-108">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="aa03e-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)