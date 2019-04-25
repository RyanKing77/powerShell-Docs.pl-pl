---
title: Przykładowy kod RunSpace10 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5337dc40-c56e-458b-aedc-5f5d401dfd28
caps.latest.revision: 6
ms.openlocfilehash: 77c0675b45bf4ff6f8c6a85ff9a090c13c199c6d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081244"
---
# <a name="runspace10-code-sample"></a><span data-ttu-id="8daf0-102">Przykładowy kod RunSpace10</span><span class="sxs-lookup"><span data-stu-id="8daf0-102">RunSpace10 Code Sample</span></span>

<span data-ttu-id="8daf0-103">Poniżej przedstawiono kod źródłowy przykładowej Runspace10.</span><span class="sxs-lookup"><span data-stu-id="8daf0-103">Here is the source code for the Runspace10 sample.</span></span> <span data-ttu-id="8daf0-104">Ta przykładowa aplikacja dodaje polecenia cmdlet, aby [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) , a następnie używa informacji o modyfikacji konfiguracji do utworzenia obszaru działania.</span><span class="sxs-lookup"><span data-stu-id="8daf0-104">This sample application adds a cmdlet to [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) and then uses the modified configuration information to create the runspace.</span></span>

> [!NOTE]
> <span data-ttu-id="8daf0-105">Możesz pobrać C# pliku źródłowego (runspace10.cs) przy użyciu Windows oprogramowania Development Kit dla Windows Vista i składników środowiska wykonawczego programu Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="8daf0-105">You can download the C# source file (runspace10.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="8daf0-106">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="8daf0-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="8daf0-107">Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.</span><span class="sxs-lookup"><span data-stu-id="8daf0-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="8daf0-108">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="8daf0-108">Code Sample</span></span>

[!code-csharp[Runspace10.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace10/Runspace10.cs#L11-L118 "Runspace10.cs")]

## <a name="see-also"></a><span data-ttu-id="8daf0-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8daf0-109">See Also</span></span>

[<span data-ttu-id="8daf0-110">Windows PowerShell przewodnik</span><span class="sxs-lookup"><span data-stu-id="8daf0-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="8daf0-111">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8daf0-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)