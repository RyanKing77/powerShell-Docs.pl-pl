---
title: Element ScriptBlock ItemSelectionCondition dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064547"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a>ScriptBlock, element — ItemSelectionCondition, GroupBy (format)

Określa skrypt, który wyzwala warunku. Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i formant jest używany. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu CustomItem CustomEntry GroupBy (Format) elementu ExpressionBinding CustomItem GroupBy (Format) elementu ItemSelectionCondition ExpressionBinding elementu ScriptBlock GroupBy (Format) ItemSelectionCondition dla grupowania (w formacie)

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
|[Element ItemSelectionCondition ExpressionBinding dla grupowania (w formacie)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Określa warunek, który musi istnieć dla tej kontrolki ma być używany.|

## <a name="text-value"></a>Wartość tekstowa

Określ skrypt, który jest oceniany.

## <a name="remarks"></a>Uwagi

Jeśli ten element jest używany, nie można określić [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) elementu podczas definiowania warunek wyboru.

## <a name="see-also"></a>Zobacz też

[Element ItemSelectionCondition ExpressionBinding dla grupowania (w formacie)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Element PropertyName ItemSelectionCondition dla grupowania (w formacie)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
