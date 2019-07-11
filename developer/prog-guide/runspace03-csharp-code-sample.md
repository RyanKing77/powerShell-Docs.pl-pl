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
ms.openlocfilehash: e1fc91174a959d6acc306330afb8d5c2e7a9a860
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735007"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="9f29e-102">Przykładowy kod RunSpace03 (C#)</span><span class="sxs-lookup"><span data-stu-id="9f29e-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="9f29e-103">Oto C# źródła kodu dla aplikacji konsoli, opisanego w [tworzenia działa konsola aplikacji czy określony skrypt](fd).</span><span class="sxs-lookup"><span data-stu-id="9f29e-103">Here is the C# source code for the console application described in [Creating a Console Application That Runs a Specified Script](fd).</span></span> <span data-ttu-id="9f29e-104">W tym przykładzie użyto [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) klasy do uruchomienia skryptu, który pobiera przetwarzania informacji przy użyciu listy nazw procesów przekazywane do skryptu.</span><span class="sxs-lookup"><span data-stu-id="9f29e-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="9f29e-105">Pokazuje, jak przekazać obiekty wejściowe do skryptu oraz jak pobierać obiektów błędu, a także obiekty danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="9f29e-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="9f29e-106">Możesz pobrać C# pliku źródłowego (runspace03.cs) omawiany w tym przykładzie za pomocą programu Microsoft Windows oprogramowania Development Kit dla Windows Vista i składników środowiska wykonawczego programu Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="9f29e-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="9f29e-107">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="9f29e-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="9f29e-108">Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.</span><span class="sxs-lookup"><span data-stu-id="9f29e-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="9f29e-109">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="9f29e-109">Code Sample</span></span>

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a><span data-ttu-id="9f29e-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f29e-110">See Also</span></span>

[<span data-ttu-id="9f29e-111">Windows PowerShell przewodnik</span><span class="sxs-lookup"><span data-stu-id="9f29e-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="9f29e-112">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9f29e-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)