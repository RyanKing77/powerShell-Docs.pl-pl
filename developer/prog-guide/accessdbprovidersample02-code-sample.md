---
title: Przykładowy kod AccessDbProviderSample02 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 67a169bfac0b0fc90e6ccd276d3d3592d1b70bb0
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795491"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="1f4c3-102">Przykładowy kod AccessDbProviderSample02</span><span class="sxs-lookup"><span data-stu-id="1f4c3-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="1f4c3-103">Poniższy kod przedstawia implementację dostawcy środowiska Windows PowerShell opisanego w [Tworzenie dostawcy dysków Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).</span><span class="sxs-lookup"><span data-stu-id="1f4c3-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span> <span data-ttu-id="1f4c3-104">Ta implementacja powoduje utworzenie ścieżki, nawiązuje połączenie z bazą danych programu Access, a następnie usuwa dysk.</span><span class="sxs-lookup"><span data-stu-id="1f4c3-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="1f4c3-105">Możesz pobrać C# pliku źródłowego (AccessDBSampleProvider02.cs) dla tego dostawcy, za pomocą programu Microsoft Windows oprogramowania Development Kit dla Windows Vista i składników środowiska wykonawczego programu Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="1f4c3-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="1f4c3-106">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="1f4c3-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="1f4c3-107">Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.</span><span class="sxs-lookup"><span data-stu-id="1f4c3-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="1f4c3-108">Aby uzyskać więcej informacji na temat innych implementacji dostawcy środowiska Windows PowerShell, zobacz [projektowania Your Windows PowerShell dostawcy](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="1f4c3-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="1f4c3-109">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="1f4c3-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a><span data-ttu-id="1f4c3-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f4c3-110">See Also</span></span>

[<span data-ttu-id="1f4c3-111">Windows PowerShell przewodnik</span><span class="sxs-lookup"><span data-stu-id="1f4c3-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="1f4c3-112">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f4c3-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)