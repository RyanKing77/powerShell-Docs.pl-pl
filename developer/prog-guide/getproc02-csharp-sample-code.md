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
ms.openlocfilehash: c4e7c13ffc26980e533530965187df8563003470
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301550"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="b118c-102">Przykładowy kod GetProc02 (C#)</span><span class="sxs-lookup"><span data-stu-id="b118c-102">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="b118c-103">Poniższy kod przedstawia implementację `Get-Process` polecenia cmdlet, który akceptuje dane wejściowe wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="b118c-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="b118c-104">Należy zauważyć, że ta implementacja definiuje `Name` używa parametru umożliwia wprowadzanie wiersza polecenia, a [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) metodę jako mechanizm dane wyjściowe do wysyłania danych wyjściowych, obiekty do potok.</span><span class="sxs-lookup"><span data-stu-id="b118c-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="b118c-105">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="b118c-105">Code Sample</span></span>

[!code-csharp[GetProcessSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs#L11-L76 "GetProcessSample02.cs")]

## <a name="see-also"></a><span data-ttu-id="b118c-106">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b118c-106">See Also</span></span>

[<span data-ttu-id="b118c-107">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b118c-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
