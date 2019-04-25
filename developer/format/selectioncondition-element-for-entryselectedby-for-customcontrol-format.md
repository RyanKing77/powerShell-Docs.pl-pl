---
title: Element SelectionCondition EntrySelectedBy dla formant niestandardowy (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075753"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a>SelectionCondition, element — EntrySelectedBy, CustomControl (format)

Określa warunek, który musi istnieć dla definicji kontrolki ma być używany. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy Element konfiguracji elementu CustomEntries widoku (Format), formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formant niestandardowy do widoku ( Format) elementu CustomItem CustomEntry dla formant niestandardowy widok (w formacie) elementu EntrySelectedBy CustomEntry dla formant niestandardowy widok (w formacie) elementu SelectionCondition EntrySelectedBy dla formant niestandardowy dla widoku (Format)

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
|[Element PropertyName SelectionCondition dla formant niestandardowy dla widoku (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Element opcjonalny.<br /><br /> Określa właściwości platformy .NET, która wyzwala warunku.|
|[Element ScriptBlock SelectionCondition dla formant niestandardowy dla widoku (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Element opcjonalny.<br /><br /> Określa skrypt, który wyzwala warunku.|
|[Element SelectionSetName SelectionCondition dla formantu niestandardowego dla widoku (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Element opcjonalny.<br /><br /> Określa zestaw typów .NET wyzwalającego warunku.|
|[Element TypeName dla SelectionCondition dla formant niestandardowy dla widoku (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Element opcjonalny.<br /><br /> Określa typ architektury .NET, która wyzwala warunku.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element EntrySelectedBy CustomEntry dla formant niestandardowy dla widoku (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Definiuje typy .NET, które używają tej definicji kontroli lub warunek, który musi istnieć, aby ta definicja ma być używany.|

## <a name="remarks"></a>Uwagi

Podczas definiowania warunek wyboru mają zastosowanie następujące wymagania:

- Warunek wyboru należy określić co najmniej jednej nazwy właściwości lub blok skryptu, ale nie można określić jednocześnie.

- Warunek wyboru można określić dowolną liczbę typów .NET lub zaznaczenie Ustawia, ale nie można określić jednocześnie.

Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Zobacz też

[Element PropertyName SelectionCondition dla formant niestandardowy dla widoku (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Element ScriptBlock SelectionCondition dla formant niestandardowy dla widoku (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Element SelectionSetName SelectionCondition dla formantu niestandardowego dla widoku (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Element TypeName dla SelectionCondition dla formant niestandardowy dla widoku (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Element EntrySelectedBy CustomEntry dla formant niestandardowy dla widoku (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
