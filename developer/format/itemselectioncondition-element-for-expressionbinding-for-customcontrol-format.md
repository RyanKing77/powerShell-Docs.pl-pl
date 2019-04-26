---
title: Element ItemSelectionCondition ExpressionBinding dla formant niestandardowy (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065828"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a>ItemSelectionCondition, element — ExpressionBinding, CustomControl (format)

Określa warunek, który musi istnieć dla tej kontrolki ma być używany. Nie ma żadnego limitu, liczbę warunków wyboru, które mogą być określone dla elementu kontrolki. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy, Element (Format) CustomEntries Element konfiguracji dla formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries elementu CustomItem widoku (Format) CustomEntry widoku (Format) elementu ExpressionBinding CustomItem dla formant niestandardowy dla elementu ItemSelectionCondition widoku (w formacie) dla wyrażenia wiązania dla formant niestandardowy, widoku (Format)

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
|[Element PropertyName ItemSelectionCondition dla formant niestandardowy dla widoku (w formacie](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Element opcjonalny.<br /><br /> Określa właściwości platformy .NET, która wyzwala warunku.|
|[Element ScriptBlock ItemSelectionCondition dla formant niestandardowy dla widoku (Format)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Element opcjonalny.<br /><br /> Określa skrypt, który wyzwala warunku.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ExpressionBinding CustomItem dla formant niestandardowy dla widoku (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Definiuje dane, które jest wyświetlany przez kontrolkę.|

## <a name="remarks"></a>Uwagi

Można określić jedną nazwę właściwości lub skrypt dla tego warunku, ale nie można określić jednocześnie.

## <a name="see-also"></a>Zobacz też

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)

[Element ExpressionBinding CustomItem dla formant niestandardowy dla widoku (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
