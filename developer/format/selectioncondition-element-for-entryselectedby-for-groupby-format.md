---
title: Element SelectionCondition EntrySelectedBy dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846228"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a>SelectionCondition, element — EntrySelectedBy, GroupBy (format)

Określa warunek, który musi istnieć dla definicji kontrolki ma być używany. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu EntrySelectedBy CustomEntry GroupBy (Format) elementu SelectionCondition EntrySelectedBy dla grupowania (w formacie)

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
|[Element PropertyName SelectionCondition dla grupowania (w formacie)](./propertyname-element-for-selectioncondition-for-groupby-format.md)|Element opcjonalny.<br /><br /> Określa właściwości platformy .NET, która wyzwala warunku.|
|[Element ScriptBlock SelectionCondition dla grupowania (w formacie)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|Element opcjonalny.<br /><br /> Określa skrypt, który wyzwala warunku.|
|[Element SelectionSetName SelectionCondition dla grupowania (w formacie)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|Element opcjonalny.<br /><br /> Określa zestaw typów .NET wyzwalającego warunku.|
|[Element TypeName dla SelectionCondition dla grupowania (w formacie)](./typename-element-for-selectioncondition-for-groupby-format.md)|Element opcjonalny.<br /><br /> Określa typ architektury .NET, która wyzwala warunku.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element EntrySelectedBy CustomEntry dla grupowania (w formacie)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Definiuje typy .NET, które używają tej definicji kontroli lub warunek, który musi istnieć, aby ta definicja ma być używany.|

## <a name="remarks"></a>Uwagi

Podczas definiowania warunek wyboru mają zastosowanie następujące wymagania:

- Warunek wyboru należy określić co najmniej jednej nazwy właściwości lub blok skryptu, ale nie można określić jednocześnie.

- Warunek wyboru można określić dowolną liczbę typów .NET lub zaznaczenie Ustawia, ale nie można określić jednocześnie.

Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Zobacz też

[Element PropertyName SelectionCondition dla formant niestandardowy dla widoku (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Element ScriptBlock SelectionCondition dla formant niestandardowy dla widoku (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Element SelectionSetName SelectionCondition dla formantu niestandardowego dla widoku (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Element TypeName dla SelectionCondition dla grupowania (w formacie)](./typename-element-for-selectioncondition-for-groupby-format.md)

[Element EntrySelectedBy CustomEntry dla grupowania (w formacie)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
