---
title: RunSpace03 (C#) przykładowego kodu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 0e80f4d850a7c6dc044526a56b92f16eea4040b5
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429911"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="3920c-102">Przykładowy kod RunSpace03 (C#)</span><span class="sxs-lookup"><span data-stu-id="3920c-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="3920c-103">Oto C# źródła kodu dla aplikacji konsoli, opisanego w [tworzenia działa konsola aplikacji czy określony skrypt](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68).</span><span class="sxs-lookup"><span data-stu-id="3920c-103">Here is the C# source code for the console application described in [Creating a Console Application That Runs a Specified Script](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68).</span></span> <span data-ttu-id="3920c-104">W tym przykładzie użyto [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) klasy do uruchomienia skryptu, który pobiera przetwarzania informacji przy użyciu listy nazw procesów przekazywane do skryptu.</span><span class="sxs-lookup"><span data-stu-id="3920c-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="3920c-105">Pokazuje, jak przekazać obiekty wejściowe do skryptu oraz jak pobierać obiektów błędu, a także obiekty danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="3920c-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="3920c-106">Możesz pobrać C# pliku źródłowego (runspace03.cs) omawiany w tym przykładzie za pomocą programu Microsoft Windows oprogramowania Development Kit dla Windows Vista i składników środowiska wykonawczego programu Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="3920c-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="3920c-107">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="3920c-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="3920c-108">Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.</span><span class="sxs-lookup"><span data-stu-id="3920c-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="3920c-109">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="3920c-109">Code Sample</span></span>

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a><span data-ttu-id="3920c-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3920c-110">See Also</span></span>

[<span data-ttu-id="3920c-111">Windows PowerShell przewodnik</span><span class="sxs-lookup"><span data-stu-id="3920c-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="3920c-112">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3920c-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)