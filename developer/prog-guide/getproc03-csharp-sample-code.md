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
ms.openlocfilehash: 4d921dd62999bc68b80838bafa2a3da8d4df3ebb
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057524"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="babad-102">Przykładowy kod GetProc03 (C#)</span><span class="sxs-lookup"><span data-stu-id="babad-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="babad-103">Poniższy kod przedstawia implementację `Get-Process` polecenia cmdlet, który może akceptować potokowe danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="babad-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="babad-104">Ta implementacja definiuje `Name` parametr, który akceptuje wejście potokowe umożliwia pobranie informacji o procesie z komputera lokalnego, w oparciu o podanej nazwy, a następnie używa [System.Management.Automation.Cmdlet.WriteObject% 28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) metodę jako wysyłanie obiektów do potoku przy użyciu mechanizmu danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="babad-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="babad-105">Możesz pobrać C# pliku źródłowego (getprov03.cs) dla tego polecenia cmdlet Get-Proc, za pomocą programu Microsoft Windows oprogramowania Development Kit dla Windows Vista i składników środowiska uruchomieniowego programu .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="babad-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="babad-106">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="babad-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="babad-107">Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.</span><span class="sxs-lookup"><span data-stu-id="babad-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="babad-108">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="babad-108">Code Sample</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="babad-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="babad-109">See Also</span></span>

[<span data-ttu-id="babad-110">Windows PowerShell przewodnik</span><span class="sxs-lookup"><span data-stu-id="babad-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="babad-111">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="babad-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)