---
title: Przykład koduC#RunSpace03 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 9afdb97b8ae2919f091ca5bacccedbe37c2e1584
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848031"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="d5fc8-102">Przykładowy kod RunSpace03 (C#)</span><span class="sxs-lookup"><span data-stu-id="d5fc8-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="d5fc8-103">Poniżej znajduje się C# kod źródłowy aplikacji konsolowej opisanej w temacie "Tworzenie aplikacji konsolowej, która uruchamia określony skrypt".</span><span class="sxs-lookup"><span data-stu-id="d5fc8-103">Here is the C# source code for the console application described in "Creating a Console Application That Runs a Specified Script".</span></span> <span data-ttu-id="d5fc8-104">Ten przykład używa klasy [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) do wykonywania skryptu pobierającego informacje o procesie przy użyciu listy nazw procesów przekazaną do skryptu.</span><span class="sxs-lookup"><span data-stu-id="d5fc8-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="d5fc8-105">Pokazuje sposób przekazywania obiektów wejściowych do skryptu i sposobu pobierania obiektów błędów oraz obiektów wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="d5fc8-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="d5fc8-106">Możesz pobrać plik C# źródłowy (runspace03.cs) dla tego przykładu, korzystając z zestawu Microsoft Windows Software Development Kit dla systemów Windows Vista i Microsoft .NET Framework 3,0 Runtime.</span><span class="sxs-lookup"><span data-stu-id="d5fc8-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="d5fc8-107">Aby uzyskać instrukcje dotyczące pobierania, zobacz [jak zainstalować program Windows PowerShell i pobrać zestaw SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="d5fc8-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="d5fc8-108">Pobrane pliki źródłowe są dostępne w  **\<przykładach programu PowerShell >** Directory.</span><span class="sxs-lookup"><span data-stu-id="d5fc8-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="d5fc8-109">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="d5fc8-109">Code Sample</span></span>

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a><span data-ttu-id="d5fc8-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5fc8-110">See Also</span></span>

[<span data-ttu-id="d5fc8-111">Przewodnik programisty programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5fc8-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="d5fc8-112">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5fc8-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)