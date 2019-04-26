---
title: GetProc02 (C#) przykładowego kodu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4e1eee3-316b-43a4-8a60-313391619be6
caps.latest.revision: 6
ms.openlocfilehash: 2ac4aea2fdefdfe86349c14fe9b87cd8c41db090
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081709"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="345d2-102">Przykładowy kod GetProc02 (C#)</span><span class="sxs-lookup"><span data-stu-id="345d2-102">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="345d2-103">Poniższy kod przedstawia implementację `Get-Process` polecenia cmdlet, który akceptuje dane wejściowe wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="345d2-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="345d2-104">Należy zauważyć, że ta implementacja definiuje `Name` używa parametru umożliwia wprowadzanie wiersza polecenia, a [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) metodę jako dane wyjściowe mechanizm umożliwiający wysyłanie danych wyjściowych obiektów do potoku.</span><span class="sxs-lookup"><span data-stu-id="345d2-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="345d2-105">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="345d2-105">Code Sample</span></span>

[!code-csharp[GetProcessSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs#L11-L76 "GetProcessSample02.cs")]

## <a name="see-also"></a><span data-ttu-id="345d2-106">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="345d2-106">See Also</span></span>

[<span data-ttu-id="345d2-107">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="345d2-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)