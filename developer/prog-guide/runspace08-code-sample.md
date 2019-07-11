---
title: Przykładowy kod RunSpace08 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: ec6aae544eafea1dedc1379dab00beeed2c7c436
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734915"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="3a3ee-102">Przykładowy kod RunSpace08</span><span class="sxs-lookup"><span data-stu-id="3a3ee-102">RunSpace08 Code Sample</span></span>

<span data-ttu-id="3a3ee-103">Poniżej przedstawiono kod źródłowy dla przykładowych Runspace08 opisanego w [tworzyć konsoli aplikacji, dodaje parametry do polecenia](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span><span class="sxs-lookup"><span data-stu-id="3a3ee-103">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span> <span data-ttu-id="3a3ee-104">Ta przykładowa aplikacja tworzy obszar działania, tworzy potok, dodaje dwa polecenia do potoku, dodaje dwa parametry do drugiego polecenia i następnie uruchamia potok.</span><span class="sxs-lookup"><span data-stu-id="3a3ee-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="3a3ee-105">Polecenia, które są dodawane do potoku znajdują się `Get-Process` i `Sort-Object` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3a3ee-105">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="3a3ee-106">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="3a3ee-106">Code Sample</span></span>

[!code-csharp[Runspace08.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a><span data-ttu-id="3a3ee-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a3ee-107">See Also</span></span>

[<span data-ttu-id="3a3ee-108">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3a3ee-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)