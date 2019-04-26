---
title: Deklaracji atrybutu OutputType | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067607"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="ca1ae-102">OutputType, deklaracja atrybutu</span><span class="sxs-lookup"><span data-stu-id="ca1ae-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="ca1ae-103">`OutputType` Atrybut identyfikuje typów programu .NET Framework, zwracany przez polecenie cmdlet, funkcji lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="ca1ae-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="ca1ae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca1ae-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="ca1ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ca1ae-105">Parameters</span></span>

<span data-ttu-id="ca1ae-106">Typ (`string[]` lub `Type[]`) wymagane.</span><span class="sxs-lookup"><span data-stu-id="ca1ae-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="ca1ae-107">Określa typy zwracane przez polecenia cmdlet funkcji lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="ca1ae-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="ca1ae-108">ParameterSetName (ciąg[]) atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ca1ae-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="ca1ae-109">Określa zestawy parametrów, które zwracają typów określonych w `type` parametru.</span><span class="sxs-lookup"><span data-stu-id="ca1ae-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="ca1ae-110">providerCmdlet atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ca1ae-110">providerCmdlet Optional.</span></span> <span data-ttu-id="ca1ae-111">Określa polecenia cmdlet dostawcy, która zwraca typów określonych w `type` parametru.</span><span class="sxs-lookup"><span data-stu-id="ca1ae-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca1ae-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ca1ae-112">See Also</span></span>

[<span data-ttu-id="ca1ae-113">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ca1ae-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
