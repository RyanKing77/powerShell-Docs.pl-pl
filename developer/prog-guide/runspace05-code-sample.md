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
ms.openlocfilehash: abf19d848f6150d005c63bb0fc2ffbe1de405e2a
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734974"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="6eb08-102">Przykładowy kod RunSpace05</span><span class="sxs-lookup"><span data-stu-id="6eb08-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="6eb08-103">Poniżej przedstawiono kod źródłowy przykładowej Runspace05 opisaną w [konfigurowania obszaru działania przy użyciu RunspaceConfiguration](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span><span class="sxs-lookup"><span data-stu-id="6eb08-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span></span> <span data-ttu-id="6eb08-104">W tym przykładzie przedstawiono sposób tworzenia informacji o konfiguracji obszaru działania, Utwórz obszar działania, tworzenie potoku za pomocą jednego polecenia, a następnie wykonywania potoku.</span><span class="sxs-lookup"><span data-stu-id="6eb08-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="6eb08-105">Polecenia, który jest wykonywany jest `Get-Process` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6eb08-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="6eb08-106">Możesz pobrać C# pliku źródłowego (runspace05.cs) przy użyciu programu Microsoft Windows oprogramowania Development Kit dla Windows Vista i składników środowiska wykonawczego programu Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="6eb08-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="6eb08-107">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="6eb08-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="6eb08-108">Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.</span><span class="sxs-lookup"><span data-stu-id="6eb08-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6eb08-109">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="6eb08-109">Code Sample</span></span>

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a><span data-ttu-id="6eb08-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6eb08-110">See Also</span></span>

[<span data-ttu-id="6eb08-111">Windows PowerShell przewodnik</span><span class="sxs-lookup"><span data-stu-id="6eb08-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="6eb08-112">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6eb08-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)