---
title: Przykładowy kod AccessDbProviderSample01 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: 01b95e18794501c2aff13d1e51b7400ae6fb8730
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081992"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="26d21-102">Przykładowy kod AccessDbProviderSample01</span><span class="sxs-lookup"><span data-stu-id="26d21-102">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="26d21-103">Poniższy kod przedstawia implementację dostawcy środowiska Windows PowerShell opisanego w [tworzenia podstawowego dostawcy programu PowerShell Windows](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="26d21-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="26d21-104">Ta implementacja udostępnia metody, uruchamianie i zatrzymywanie dostawcy, a choć nie zapewnia sposób dostępu do magazynu danych lub pobrać lub ustawić dane w magazynie danych, zapewnia podstawową funkcjonalność, która jest wymagana przez wszystkich dostawców.</span><span class="sxs-lookup"><span data-stu-id="26d21-104">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="26d21-105">Możesz pobrać C# pliku źródłowego (AccessDBSampleProvider01.cs) dla tego dostawcy, przy użyciu Windows oprogramowania Development Kit dla Windows Vista i składników środowiska wykonawczego programu Microsoft .NET Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="26d21-105">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="26d21-106">Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="26d21-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="26d21-107">Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.</span><span class="sxs-lookup"><span data-stu-id="26d21-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="26d21-108">Aby uzyskać więcej informacji na temat innych implementacji dostawcy środowiska Windows PowerShell, zobacz [projektowania Your Windows PowerShell dostawcy](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="26d21-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="26d21-109">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="26d21-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="26d21-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26d21-110">See Also</span></span>

[<span data-ttu-id="26d21-111">Windows PowerShell przewodnik</span><span class="sxs-lookup"><span data-stu-id="26d21-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="26d21-112">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="26d21-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)