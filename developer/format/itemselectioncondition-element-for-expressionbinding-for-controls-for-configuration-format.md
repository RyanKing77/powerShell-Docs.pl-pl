---
title: Element ItemSelectionCondition ExpressionBinding dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850792"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a>ItemSelectionCondition, element — ExpressionBinding, Controls, Configuration (format)

Określa warunek, który musi istnieć dla tej kontrolki ma być używany. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do konfiguracji ( Format) elementu CustomEntry formant niestandardowy dla formantów CustomItem elementu konfiguracji (Format) CustomEntry dla formantów dla konfiguracji elementu ExpressionBinding CustomItem dla formantów dla konfiguracji (Format) Element ItemSelectionCondition ExpressionBinding dla formantów dla konfiguracji (Format)

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
|[Element PropertyName ItemSelectionCondition dla formantów dla konfiguracji (Format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|Element opcjonalny.<br /><br /> Określa właściwości platformy .NET, która wyzwala warunku.|
|[Element ScriptBlock ItemSelectionCondition dla formantów dla konfiguracji (Format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|Element opcjonalny.<br /><br /> Określa skrypt, który wyzwala warunku.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ExpressionBinding CustomItem dla formantów dla konfiguracji (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Definiuje dane, które jest wyświetlany przez kontrolkę.|

## <a name="remarks"></a>Uwagi

Można określić jedną nazwę właściwości lub skrypt dla tego warunku, ale nie można określić jednocześnie.

## <a name="see-also"></a>Zobacz też

[Element PropertyName ItemSelectionCondition dla formantów dla konfiguracji (Format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[Element ScriptBlock ItemSelectionCondition dla formantów dla konfiguracji (Format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[Element ExpressionBinding CustomItem dla formantów dla konfiguracji (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
