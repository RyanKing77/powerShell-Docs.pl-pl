---
title: Element PropertyName ItemSelectionCondition dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075855"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a>PropertyName, element — ItemSelectionCondition, Controls, View (format)

Określa właściwości platformy .NET, która wyzwala warunku. Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i formant jest używany. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu CustomItem CustomEntry dla formantów widoku (Format) elementu ExpressionBinding CustomItem dla formantów widoku (Format) Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format) elementu PropertyName ItemSelectionCondition dla formantów widoku (Format)

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
|[Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Określa warunek, który musi istnieć dla tej kontrolki ma być używany.|

## <a name="text-value"></a>Wartość tekstowa

Określ nazwę właściwości platformy .NET, która wyzwala warunku.

## <a name="remarks"></a>Uwagi

Jeśli ten element jest używany, nie można określić [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) elementu podczas definiowania warunek wyboru.

## <a name="see-also"></a>Zobacz też

[Element ScriptBlock ItemSelectionCondition dla formantów widoku (Format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
