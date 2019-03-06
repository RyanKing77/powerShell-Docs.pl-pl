---
title: GetProc04 (C#) przykładowego kodu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 439ba3f3-91b1-46a4-8d07-9af6edb71bc4
caps.latest.revision: 5
ms.openlocfilehash: 1fc1ab58ae651239937e36c8bb08fda3d3272b2a
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429690"
---
# <a name="getproc04-c-sample-code"></a><span data-ttu-id="e8fca-102">Przykładowy kod GetProc04 (C#)</span><span class="sxs-lookup"><span data-stu-id="e8fca-102">GetProc04 (C#) Sample Code</span></span>

<span data-ttu-id="e8fca-103">Poniższy kod przedstawia implementację `Get-Process` polecenia cmdlet, który zgłasza błędy niekończące.</span><span class="sxs-lookup"><span data-stu-id="e8fca-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="e8fca-104">Ta implementacja wywołuje [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metodę, aby błędy niekończące raportu.</span><span class="sxs-lookup"><span data-stu-id="e8fca-104">This implementation calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="e8fca-105">Możesz pobrać C# pliku źródłowego (getprov04.cs) dla tego polecenia cmdlet Get-Proc, za pomocą programu Microsoft Windows oprogramowania Development Kit dla Windows Vista i składników środowiska uruchomieniowego programu .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="e8fca-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="e8fca-106">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="e8fca-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="e8fca-107">Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.</span><span class="sxs-lookup"><span data-stu-id="e8fca-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e8fca-108">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="e8fca-108">Code Sample</span></span>

[!code-csharp[GetProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs#L11-L98 "GetProcessSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="e8fca-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8fca-109">See Also</span></span>

[<span data-ttu-id="e8fca-110">Windows PowerShell przewodnik</span><span class="sxs-lookup"><span data-stu-id="e8fca-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="e8fca-111">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e8fca-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)