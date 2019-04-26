---
title: Runspace01 (C#) przykładowego kodu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: 59320365c4a35c3d71af10273eb21b1ce01e5c0c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081465"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="74269-102">Przykładowy kod Runspace01 (C#)</span><span class="sxs-lookup"><span data-stu-id="74269-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="74269-103">Poniżej przedstawiono przykłady kodu dla obszaru działania opisane w [tworzenia działa konsola aplikacji czy określone polecenie](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span><span class="sxs-lookup"><span data-stu-id="74269-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span></span> <span data-ttu-id="74269-104">Aby to zrobić, aplikacja wywołuje obszarem działania, a następnie wywołuje polecenie.</span><span class="sxs-lookup"><span data-stu-id="74269-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="74269-105">(Zwróć uwagę, że ta aplikacja nie określa informacje o konfiguracji obszaru działania ani go jawnie tworzy potok).</span><span class="sxs-lookup"><span data-stu-id="74269-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="74269-106">Polecenie, które jest wywoływane jest `Get-Process` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="74269-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="74269-107">Możesz pobrać C# pliku źródłowego (runspace01.cs) dla tego obszaru działania, za pomocą programu Microsoft Windows oprogramowania Development Kit dla Windows Vista i składników środowiska wykonawczego programu Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="74269-107">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="74269-108">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="74269-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="74269-109">Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.</span><span class="sxs-lookup"><span data-stu-id="74269-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="74269-110">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="74269-110">Code Sample</span></span>

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a><span data-ttu-id="74269-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="74269-111">See Also</span></span>

[<span data-ttu-id="74269-112">Windows PowerShell przewodnik</span><span class="sxs-lookup"><span data-stu-id="74269-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="74269-113">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="74269-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)