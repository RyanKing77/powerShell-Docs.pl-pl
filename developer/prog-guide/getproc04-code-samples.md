---
title: Przykłady kodu GetProc04 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: d679bc8cbdb026e072628d3e0c5704de2eec7af9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846424"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="2c8bf-102">Przykłady kodu GetProc04</span><span class="sxs-lookup"><span data-stu-id="2c8bf-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="2c8bf-103">Poniżej przedstawiono przykłady kodu, aby uzyskać przykładowe polecenie cmdlet GetProc04.</span><span class="sxs-lookup"><span data-stu-id="2c8bf-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="2c8bf-104">Jest to `Get-Process` przykładowe polecenia cmdlet opisane w [Dodawanie niekończące raportowania z błędów, do polecenia Cmdlet usługi](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="2c8bf-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="2c8bf-105">To `Get-Process` wywołania polecenia cmdlet [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) zawsze, gdy jest nieprawidłowa operacja jest zwracany wyjątek podczas pobierania informacji o procesie.</span><span class="sxs-lookup"><span data-stu-id="2c8bf-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="2c8bf-106">Możesz pobrać C# pliku źródłowego (getprov04.cs) dla tego polecenia cmdlet Get-Proc, za pomocą programu Microsoft Windows oprogramowania Development Kit dla Windows Vista i składników środowiska uruchomieniowego programu .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="2c8bf-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="2c8bf-107">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="2c8bf-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="2c8bf-108">Możesz pobrać C# pliku źródłowego (getprov04.cs) dla tego polecenia cmdlet Get-Proc, za pomocą programu Microsoft Windows oprogramowania Development Kit dla Windows Vista i składników środowiska uruchomieniowego programu .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="2c8bf-108">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="2c8bf-109">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="2c8bf-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="2c8bf-110">Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.</span><span class="sxs-lookup"><span data-stu-id="2c8bf-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="2c8bf-111">Aby uzyskać kompletny przykładowy kod zobacz następujące tematy.</span><span class="sxs-lookup"><span data-stu-id="2c8bf-111">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="2c8bf-112">Język</span><span class="sxs-lookup"><span data-stu-id="2c8bf-112">Language</span></span>|<span data-ttu-id="2c8bf-113">Temat</span><span class="sxs-lookup"><span data-stu-id="2c8bf-113">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="2c8bf-114">C#</span><span class="sxs-lookup"><span data-stu-id="2c8bf-114">C#</span></span>|[<span data-ttu-id="2c8bf-115">GetProc04 (C#) przykładowego kodu</span><span class="sxs-lookup"><span data-stu-id="2c8bf-115">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="2c8bf-116">VB.NET</span><span class="sxs-lookup"><span data-stu-id="2c8bf-116">VB.NET</span></span>|[<span data-ttu-id="2c8bf-117">GetProc04 kodu przykładowego (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="2c8bf-117">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="2c8bf-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c8bf-118">See Also</span></span>

[<span data-ttu-id="2c8bf-119">Windows PowerShell przewodnik</span><span class="sxs-lookup"><span data-stu-id="2c8bf-119">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="2c8bf-120">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2c8bf-120">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)