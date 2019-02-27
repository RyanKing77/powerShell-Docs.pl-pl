---
title: Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850904"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a>ItemSelectionCondition, element — ExpressionBinding, Controls, View (format)

Określa warunek, który musi istnieć dla tej kontrolki ma być używany. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu CustomItem CustomEntry dla formantów widoku (Format) elementu ExpressionBinding CustomItem dla formantów widoku (Format) Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format)

## <a name="syntax"></a>Składnia

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ItemSelectionCondition` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element PropertyName ItemSelectionCondition dla formantów widoku (Format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|Element opcjonalny.<br /><br /> Określa właściwości platformy .NET, która wyzwala warunku.|
|[Element ScriptBlock ItemSelectionCondition dla formantów widoku (Format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|Element opcjonalny.<br /><br /> Określa skrypt, który wyzwala warunku.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ExpressionBinding CustomItem dla formantów widoku (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Definiuje dane, które jest wyświetlany przez kontrolkę.|

## <a name="remarks"></a>Uwagi

Można określić jedną nazwę właściwości lub skrypt dla tego warunku, ale nie można określić jednocześnie.

## <a name="see-also"></a>Zobacz też

[Element PropertyName ItemSelectionCondition dla formantów widoku (Format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Element ScriptBlock ItemSelectionCondition dla formantów widoku (Format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Element ExpressionBinding CustomItem dla formantów widoku (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
