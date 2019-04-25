---
title: GetProc04 kodu przykładowego (VB.NET) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d22f47b-3679-4587-a559-94454415d2dd
caps.latest.revision: 5
ms.openlocfilehash: 0d0d1a3f82bc2cee025139d69fee02eb601fa563
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081531"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="6a56c-102">Przykładowy kod GetProc04 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="6a56c-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="6a56c-103">Poniższy kod przedstawia implementację `Get-Process` polecenia cmdlet, który zgłasza błędy niekończące.</span><span class="sxs-lookup"><span data-stu-id="6a56c-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="6a56c-104">Ta implementacja wywołuje [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metodę, aby błędy niekończące raportu.</span><span class="sxs-lookup"><span data-stu-id="6a56c-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="6a56c-105">Możesz pobrać C# pliku źródłowego (getprov04.cs) dla tego polecenia cmdlet Get-Proc, za pomocą programu Microsoft Windows oprogramowania Development Kit dla Windows Vista i składników środowiska uruchomieniowego programu .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="6a56c-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="6a56c-106">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="6a56c-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="6a56c-107">Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.</span><span class="sxs-lookup"><span data-stu-id="6a56c-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6a56c-108">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="6a56c-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="6a56c-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6a56c-109">See Also</span></span>

[<span data-ttu-id="6a56c-110">Windows PowerShell przewodnik</span><span class="sxs-lookup"><span data-stu-id="6a56c-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="6a56c-111">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6a56c-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)