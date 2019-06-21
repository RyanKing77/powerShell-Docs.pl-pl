---
title: GetProc03 (C#) przykładowego kodu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: 116a116a5ba5b81a77b4432a81f001cc999fe46d
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301357"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="28de6-102">Przykładowy kod GetProc03 (C#)</span><span class="sxs-lookup"><span data-stu-id="28de6-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="28de6-103">Poniższy kod przedstawia implementację `Get-Process` polecenia cmdlet, który może akceptować potokowe danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="28de6-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="28de6-104">Ta implementacja definiuje `Name` parametr, który akceptuje wejście potokowe umożliwia pobranie informacji o procesie z komputera lokalnego, w oparciu o podanej nazwy, a następnie używa [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)metodę jako wysyłanie obiektów do potoku przy użyciu mechanizmu danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="28de6-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="28de6-105">Możesz pobrać C# pliku źródłowego (getprov03.cs) dla tego polecenia cmdlet Get-Proc, za pomocą programu Microsoft Windows oprogramowania Development Kit dla Windows Vista i składników środowiska uruchomieniowego programu .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="28de6-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="28de6-106">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="28de6-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="28de6-107">Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.</span><span class="sxs-lookup"><span data-stu-id="28de6-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="28de6-108">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="28de6-108">Code Sample</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="28de6-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28de6-109">See Also</span></span>

[<span data-ttu-id="28de6-110">Windows PowerShell przewodnik</span><span class="sxs-lookup"><span data-stu-id="28de6-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="28de6-111">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="28de6-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
