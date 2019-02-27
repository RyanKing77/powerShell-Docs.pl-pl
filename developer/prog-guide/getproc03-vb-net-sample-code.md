---
title: GetProc03 kodu przykładowego (VB.NET) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: da85155c43471150a7b35ac37c1dce0790277084
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845857"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="452c4-102">Przykładowy kod GetProc03 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="452c4-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="452c4-103">Poniższy kod przedstawia implementację `Get-Process` polecenia cmdlet, który może akceptować potokowe danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="452c4-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="452c4-104">Ta implementacja definiuje `Name` parametr, który akceptuje wejście potokowe umożliwia pobranie informacji o procesie z komputera lokalnego, w oparciu o podanej nazwy, a następnie używa [System.Management.Automation.Cmdlet.Writeobject% 28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) metodę jako wysyłanie obiektów do potoku przy użyciu mechanizmu danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="452c4-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="452c4-105">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="452c4-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->