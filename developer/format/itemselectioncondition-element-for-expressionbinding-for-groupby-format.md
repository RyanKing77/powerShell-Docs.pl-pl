---
title: Element ItemSelectionCondition ExpressionBinding dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844807"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a>ItemSelectionCondition, element — ExpressionBinding, GroupBy (format)

Określa warunek, który musi istnieć dla tej kontrolki ma być używany. Nie ma żadnego limitu, liczbę warunków wyboru, które mogą być określone dla elementu kontrolki. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu CustomItem CustomEntry GroupBy (Format) elementu ExpressionBinding CustomItem GroupBy (Format) elementu ItemSelectionCondition ExpressionBinding dla grupowania (w formacie)

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
|[Element PropertyName ItemSelectionCondition dla grupowania (w formacie)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|Element opcjonalny.<br /><br /> Określa właściwości platformy .NET, która wyzwala warunku.|
|[Element ScriptBlock ItemSelectionCondition dla grupowania (w formacie)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|Element opcjonalny.<br /><br /> Określa skrypt, który wyzwala warunku.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ExpressionBinding CustomItem dla grupowania (w formacie)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Definiuje dane, które jest wyświetlany przez kontrolkę.|

## <a name="remarks"></a>Uwagi

Można określić jedną nazwę właściwości lub skrypt dla tego warunku, ale nie można określić jednocześnie.

## <a name="see-also"></a>Zobacz też

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)

[Element ExpressionBinding CustomItem dla grupowania (w formacie)](./expressionbinding-element-for-customitem-for-groupby-format.md)
