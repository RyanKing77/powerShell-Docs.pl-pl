---
title: Przykłady kodu RunSpace04 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb6fcc47-cf89-43e7-b686-3d60934ce3e7
caps.latest.revision: 6
ms.openlocfilehash: 10f236b201920d2d456af41328c7a62a9e14b571
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850379"
---
# <a name="runspace04-code-samples"></a><span data-ttu-id="18144-102">Przykłady kodu RunSpace04</span><span class="sxs-lookup"><span data-stu-id="18144-102">RunSpace04 Code Samples</span></span>

<span data-ttu-id="18144-103">Poniżej znajduje się przykładowy kod dla obszaru działania, który używa [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) klasy do uruchomienia skryptu, który generuje błąd powodujący zakończenie.</span><span class="sxs-lookup"><span data-stu-id="18144-103">Here is a code sample for a runspace that uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that generates a terminating error.</span></span> <span data-ttu-id="18144-104">Aplikacja hosta jest odpowiedzialny za Przechwytywanie błąd i interpretowanie rekordu błędu.</span><span class="sxs-lookup"><span data-stu-id="18144-104">The host application is responsible for catching the error and interpreting the error record.</span></span>

> [!NOTE]
> <span data-ttu-id="18144-105">Możesz pobrać plik źródłowy VB.NET (Runspace04.vb) dla tego obszaru działania przy użyciu Windows oprogramowania Development Kit dla Windows Vista i składników środowiska wykonawczego programu Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="18144-105">You can download the VB.NET source file (Runspace04.vb) for this runspace using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="18144-106">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="18144-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="18144-107">Możesz pobrać plik źródłowy VB.NET (Runspace04.vb) dla tego obszaru działania przy użyciu Windows oprogramowania Development Kit dla Windows Vista i składników środowiska wykonawczego programu Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="18144-107">You can download the VB.NET source file (Runspace04.vb) for this runspace using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="18144-108">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="18144-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="18144-109">Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.</span><span class="sxs-lookup"><span data-stu-id="18144-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="18144-110">Aby uzyskać kompletny przykładowy kod zobacz następujące tematy.</span><span class="sxs-lookup"><span data-stu-id="18144-110">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="18144-111">Język</span><span class="sxs-lookup"><span data-stu-id="18144-111">Language</span></span>|<span data-ttu-id="18144-112">Temat</span><span class="sxs-lookup"><span data-stu-id="18144-112">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="18144-113">VB.NET</span><span class="sxs-lookup"><span data-stu-id="18144-113">VB.NET</span></span>|[<span data-ttu-id="18144-114">Runspace01 przykładowy kod (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="18144-114">Runspace01 (VB.NET) Code Sample</span></span>](./runspace01-vb-net-code-sample.md)|

## <a name="see-also"></a><span data-ttu-id="18144-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="18144-115">See Also</span></span>

[<span data-ttu-id="18144-116">Windows PowerShell przewodnik</span><span class="sxs-lookup"><span data-stu-id="18144-116">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="18144-117">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="18144-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)