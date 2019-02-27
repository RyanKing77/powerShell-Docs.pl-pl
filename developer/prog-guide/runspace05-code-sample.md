---
title: Przykładowy kod RunSpace05 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: 2b5ac097e8a52832b0f8cfb93b84eef56fc64858
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845829"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="1aedd-102">Przykładowy kod RunSpace05</span><span class="sxs-lookup"><span data-stu-id="1aedd-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="1aedd-103">Poniżej przedstawiono kod źródłowy przykładowej Runspace05 opisaną w [konfigurowania obszaru działania przy użyciu RunspaceConfiguration](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span><span class="sxs-lookup"><span data-stu-id="1aedd-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span></span> <span data-ttu-id="1aedd-104">W tym przykładzie przedstawiono sposób tworzenia informacji o konfiguracji obszaru działania, Utwórz obszar działania, tworzenie potoku za pomocą jednego polecenia, a następnie wykonywania potoku.</span><span class="sxs-lookup"><span data-stu-id="1aedd-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="1aedd-105">Polecenia, który jest wykonywany jest `Get-Process` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1aedd-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="1aedd-106">Możesz pobrać C# pliku źródłowego (runspace05.cs) przy użyciu programu Microsoft Windows oprogramowania Development Kit dla Windows Vista i składników środowiska wykonawczego programu Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="1aedd-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="1aedd-107">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="1aedd-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="1aedd-108">Możesz pobrać C# pliku źródłowego (runspace05.cs) przy użyciu programu Microsoft Windows oprogramowania Development Kit dla Windows Vista i składników środowiska wykonawczego programu Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="1aedd-108">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="1aedd-109">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="1aedd-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="1aedd-110">Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.</span><span class="sxs-lookup"><span data-stu-id="1aedd-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="1aedd-111">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="1aedd-111">Code Sample</span></span>

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a><span data-ttu-id="1aedd-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1aedd-112">See Also</span></span>

[<span data-ttu-id="1aedd-113">Windows PowerShell przewodnik</span><span class="sxs-lookup"><span data-stu-id="1aedd-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="1aedd-114">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1aedd-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)