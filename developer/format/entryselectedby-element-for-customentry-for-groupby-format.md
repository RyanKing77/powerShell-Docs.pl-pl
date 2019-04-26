---
title: Element EntrySelectedBy CustomEntry dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066230"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a>EntrySelectedBy, element — CustomEntry, GroupBy (format)

Definiuje typy .NET, które używają tej definicji kontroli lub warunek, który musi istnieć, aby ta definicja ma być używany. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu EntrySelectedBy CustomEntry dla grupowania (w formacie)

## <a name="syntax"></a>Składnia

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `EntrySelectedBy` elementu. Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru dla definicji. Jest nieograniczona maksymalną liczbę elementów podrzędnych, które są dostępne.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element SelectionCondition EntrySelectedBy dla grupowania (w formacie)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Element opcjonalny.<br /><br /> Określa warunek, który musi istnieć, aby ta definicja ma być używany.|
|[Element SelectionSetName EntrySelectedBy dla grupowania (w formacie)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|Element opcjonalny.<br /><br /> Określa zestaw typów .NET, korzystających z tej definicji formantu.|
|[Element TypeName dla EntrySelectedBy dla grupowania (w formacie)](./typename-element-for-entryselectedby-for-groupby-format.md)|Element opcjonalny.<br /><br /> Określa typ architektury .NET, która używa tej definicji kontrolki.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CustomEntry formant niestandardowy do grupowania (w formacie)](./customentry-element-for-customcontrol-for-groupby-format.md)|Zawiera definicję formantu.|

## <a name="remarks"></a>Uwagi

Wybór warunki są używane do definiowania warunek, który musi istnieć definicja ma być używany, np. Jeśli obiekt ma określoną właściwość lub gdy wartość określoną właściwość lub skryptu, które daje w wyniku `true`. Aby uzyskać więcej informacji o warunkach wyboru, zobacz [definiujący warunki dla, gdy wpis widoku lub służy element](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Zobacz też

[Element SelectionCondition EntrySelectedBy dla grupowania (w formacie)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[Element SelectionSetName EntrySelectedBy dla grupowania (w formacie)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[Element TypeName dla EntrySelectedBy dla grupowania (w formacie)](./typename-element-for-entryselectedby-for-groupby-format.md)

[Element CustomEntry CustomEntries dla formantów widoku (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
