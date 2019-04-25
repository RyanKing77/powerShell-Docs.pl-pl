---
title: Przykładowy kod AccessDbProviderSample04 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: 43f01b9cd6af3ab6c26f88ee0c1e9269499b2bc3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081958"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="1ba6d-102">Przykładowy kod AccessDbProviderSample04</span><span class="sxs-lookup"><span data-stu-id="1ba6d-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="1ba6d-103">Poniższy kod przedstawia implementację dostawcy środowiska Windows PowerShell opisanego w [Tworzenie dostawcy kontenera Windows PowerShell](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="1ba6d-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span> <span data-ttu-id="1ba6d-104">Ten dostawca działa w przypadku magazynów danych w wielu warstwach.</span><span class="sxs-lookup"><span data-stu-id="1ba6d-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="1ba6d-105">Dla tego typu magazynu danych najwyższy poziom magazynu zawiera elementy katalogu głównego, a każdy kolejnych poziom jest określany jako węzeł elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="1ba6d-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="1ba6d-106">Przez umożliwienie użytkownikowi pracować nad tych węzłów podrzędnych, użytkownik może wchodzić hierarchicznie przez Magazyn danych.</span><span class="sxs-lookup"><span data-stu-id="1ba6d-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="1ba6d-107">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="1ba6d-107">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="1ba6d-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ba6d-108">See Also</span></span>

[<span data-ttu-id="1ba6d-109">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1ba6d-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)