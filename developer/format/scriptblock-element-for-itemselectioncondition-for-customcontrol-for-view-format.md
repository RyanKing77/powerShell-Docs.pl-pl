---
title: Element ScriptBlock ItemSelectionCondition dla formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064479"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>ScriptBlock, element — ItemSelectionCondition, CustomControl, View (format)

Określa skrypt, który wyzwala warunku. Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i formant jest używany. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy, Element (Format) CustomEntries Element konfiguracji dla formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries elementu CustomItem widoku (Format) CustomEntry widoku (Format) elementu ExpressionBinding CustomItem dla formant niestandardowy dla elementu ItemSelectionCondition widoku (w formacie) dla wiązania wyrażenia dla formant niestandardowy widok (w formacie) elementu ScriptBlock ItemSelectionCondition dla Formant niestandardowy dla widoku (Format)

## <a name="syntax"></a>Składnia

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ScriptBlock` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ItemSelectionCondition dla wyrażenia wiązania dla formant niestandardowy, widoku (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Określa warunek, który musi istnieć dla tej kontrolki ma być używany.|

## <a name="text-value"></a>Wartość tekstowa

Określ skrypt, który jest oceniany.

## <a name="remarks"></a>Uwagi

Jeśli ten element jest używany, nie można określić [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) elementu podczas definiowania warunek wyboru.

## <a name="see-also"></a>Zobacz też

[Element PropertyName ItemSelectionCondition dla formant niestandardowy dla widoku (Format)](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[Element ItemSelectionCondition dla wyrażenia wiązania dla formant niestandardowy, widoku (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
