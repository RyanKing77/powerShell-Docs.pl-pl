---
title: Element SelectionCondition EntrySelectedBy dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064237"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a>SelectionCondition, element — EntrySelectedBy, Controls, View (format)

Określa warunek, który musi istnieć dla definicji kontrolki ma być używany. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy dla formantów widoku (Format) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu EntrySelectedBy CustomEntry dla formantów widoku (Format) elementu SelectionCondition EntrySelectedBy dla kontrolki (Widok Format)

## <a name="syntax"></a>Składnia

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionCondition` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element PropertyName SelectionCondition dla formantów widoku (Format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|Element opcjonalny.<br /><br /> Określa właściwości platformy .NET, która wyzwala warunku.|
|[Element ScriptBlock SelectionCondition dla formantów widoku (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|Element opcjonalny.<br /><br /> Określa skrypt, który wyzwala warunku.|
|[Element SelectionSetName SelectionCondition dla formantów widoku (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|Element opcjonalny.<br /><br /> Określa zestaw typów .NET wyzwalającego warunku.|
|[Element TypeName dla SelectionCondition dla formantów widoku (Format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|Element opcjonalny.<br /><br /> Określa typ architektury .NET, która wyzwala warunku.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element EntrySelectedBy CustomEntry dla formantów widoku (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Definiuje typy .NET, które używają tej definicji kontroli lub warunek, który musi istnieć, aby ta definicja ma być używany.|

## <a name="remarks"></a>Uwagi

Podczas definiowania warunek wyboru mają zastosowanie następujące wymagania:

- Warunek wyboru należy określić co najmniej jednej nazwy właściwości lub blok skryptu, ale nie można określić jednocześnie.

- Warunek wyboru można określić dowolną liczbę typów .NET lub zaznaczenie Ustawia, ale nie można określić jednocześnie.

Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Zobacz też

[Element PropertyName SelectionCondition dla formantów widoku (Format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[Element ScriptBlock SelectionCondition dla formantów widoku (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[Element SelectionSetName SelectionCondition dla formantów widoku (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[Element TypeName dla SelectionCondition dla formantów widoku (Format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[Element EntrySelectedBy CustomEntry dla formantów widoku (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
