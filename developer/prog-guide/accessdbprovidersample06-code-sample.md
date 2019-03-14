---
title: Przykładowy kod AccessDbProviderSample06 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: baab6a56-c199-48d7-a03e-a904b1bb1baa
caps.latest.revision: 7
ms.openlocfilehash: 6e86318573df92b9ec84056631843e0efa096a3b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795610"
---
# <a name="accessdbprovidersample06-code-sample"></a><span data-ttu-id="4f22e-102">Przykładowy kod AccessDbProviderSample06</span><span class="sxs-lookup"><span data-stu-id="4f22e-102">AccessDbProviderSample06 Code Sample</span></span>

<span data-ttu-id="4f22e-103">Poniższy kod przedstawia implementację programu Windows PowerShell, dostawcy zawartości są opisane w [Tworzenie dostawcy zawartości Windows PowerShell](./creating-a-windows-powershell-content-provider.md).</span><span class="sxs-lookup"><span data-stu-id="4f22e-103">The following code shows the implementation of the Windows PowerShell content provider described in [Creating a Windows PowerShell Content Provider](./creating-a-windows-powershell-content-provider.md).</span></span> <span data-ttu-id="4f22e-104">Ten dostawca umożliwia użytkownikowi manipulować zawartością elementów w magazynie danych.</span><span class="sxs-lookup"><span data-stu-id="4f22e-104">This provider enables the user to manipulate the contents of the items in a data store.</span></span>

> [!NOTE]
> <span data-ttu-id="4f22e-105">Możesz pobrać C# pliku źródłowego (AccessDBSampleProvider06.cs) dla tego dostawcy, za pomocą programu Microsoft Windows oprogramowania Development Kit dla Windows Vista i składników środowiska wykonawczego programu Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="4f22e-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="4f22e-106">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="4f22e-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="4f22e-107">Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.</span><span class="sxs-lookup"><span data-stu-id="4f22e-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="4f22e-108">Aby uzyskać więcej informacji na temat innych implementacji dostawcy środowiska Windows PowerShell, zobacz [projektowania Your Windows PowerShell dostawcy](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="4f22e-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="4f22e-109">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="4f22e-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="4f22e-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4f22e-110">See Also</span></span>

[<span data-ttu-id="4f22e-111">Windows PowerShell przewodnik</span><span class="sxs-lookup"><span data-stu-id="4f22e-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="4f22e-112">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4f22e-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)