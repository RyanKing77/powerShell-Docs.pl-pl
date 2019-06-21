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
ms.openlocfilehash: a0a88ca517347a94fc81534caace6efa0f13fdd7
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301569"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="2d9f0-102">Przykładowy kod GetProc03 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="2d9f0-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="2d9f0-103">Poniższy kod przedstawia implementację `Get-Process` polecenia cmdlet, który może akceptować potokowe danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="2d9f0-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="2d9f0-104">Ta implementacja definiuje `Name` parametr, który akceptuje wejście potokowe umożliwia pobranie informacji o procesie z komputera lokalnego, w oparciu o podanej nazwy, a następnie używa [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)metodę jako wysyłanie obiektów do potoku przy użyciu mechanizmu danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="2d9f0-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="2d9f0-105">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="2d9f0-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
