---
title: GetProc02 kodu przykładowego (VB.NET) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3497546-5b3a-4e29-84ba-cd9747be64b3
caps.latest.revision: 6
ms.openlocfilehash: 5b5cefae1be3ccf6aec819df83363b7161955b0c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849742"
---
# <a name="getproc02-vbnet-sample-code"></a><span data-ttu-id="3dd1a-102">Przykładowy kod GetProc02 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="3dd1a-102">GetProc02 (VB.NET) Sample Code</span></span>

<span data-ttu-id="3dd1a-103">Poniższy kod przedstawia implementację `Get-Process` polecenia cmdlet, który akceptuje dane wejściowe wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="3dd1a-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="3dd1a-104">Należy zauważyć, że ta implementacja definiuje `Name` używa parametru umożliwia wprowadzanie wiersza polecenia, a [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) metodę jako dane wyjściowe mechanizm umożliwiający wysyłanie danych wyjściowych obiektów do potoku.</span><span class="sxs-lookup"><span data-stu-id="3dd1a-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="3dd1a-105">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="3dd1a-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a><span data-ttu-id="3dd1a-106">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3dd1a-106">See Also</span></span>

[<span data-ttu-id="3dd1a-107">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3dd1a-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)