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
# <a name="outputtype-attribute-declaration"></a>OutputType, deklaracja atrybutu

`OutputType` Atrybut identyfikuje typów programu .NET Framework, zwracany przez polecenie cmdlet, funkcji lub skryptu.

## <a name="syntax"></a>Składnia

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>Parametry

Typ (`string[]` lub `Type[]`) wymagane. Określa typy zwracane przez polecenia cmdlet funkcji lub skryptu.

ParameterSetName (ciąg[]) atrybut opcjonalny. Określa zestawy parametrów, które zwracają typów określonych w `type` parametru.

providerCmdlet atrybut opcjonalny. Określa polecenia cmdlet dostawcy, która zwraca typów określonych w `type` parametru.

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
