---
title: Element PropertyName ItemSeclectionCondition dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad8ab181-c559-492e-a0cf-299e381fdcc3
caps.latest.revision: 6
ms.openlocfilehash: ce25789bdfc2679372ca9e42f99dcc6a30ae2def
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064908"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a>PropertyName, element — ItemSelectionCondition, Controls, Configuration (format)

Określa właściwości platformy .NET, która wyzwala warunku. Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i formant jest używany. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do konfiguracji ( Format) elementu CustomEntry formant niestandardowy dla formantów CustomItem elementu konfiguracji (Format) CustomEntry dla formantów dla konfiguracji elementu ExpressionBinding CustomItem dla formantów dla konfiguracji (Format) Element ItemSelectionCondition ExpressionBinding dla formantów PropertyName elementu konfiguracji (Format) ItemSeclectionCondition dla formantów dla konfiguracji (Format)

## <a name="syntax"></a>Składnia

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `PropertyName` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ItemSelectionCondition ExpressionBinding dla formantów dla konfiguracji (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Określa warunek, który musi istnieć dla tej kontrolki ma być używany.|

## <a name="text-value"></a>Wartość tekstowa

Określ nazwę właściwości platformy .NET, która wyzwala warunku.

## <a name="remarks"></a>Uwagi

Jeśli ten element jest używany, nie można określić [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) elementu podczas definiowania warunek wyboru.

## <a name="see-also"></a>Zobacz też

[Element ScriptBlock ItemSeclectionCondition dla formantów dla konfiguracji (Format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[Element ItemSelectionCondition ExpressionBinding dla formantów dla konfiguracji (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
