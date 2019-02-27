---
title: Element EntrySelectedBy CustomEntry dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849287"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a>EntrySelectedBy, element — CustomEntry, Controls, View (format)

Definiuje typy .NET, które używają tej definicji kontroli lub warunek, który musi istnieć, aby ta definicja ma być używany. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy dla formantów widoku (Format) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu EntrySelectedBy CustomEntry dla formantów widoku (Format)

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
|[Element SelectionCondition EntrySelectedBy dla formantów widoku (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Element opcjonalny.<br /><br /> Określa warunek, który musi istnieć, aby ta definicja ma być używany.|
|[Element SelectionSetName EntrySelectedBy dla formantów widoku (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|Element opcjonalny.<br /><br /> Określa zestaw typów .NET, korzystających z tej definicji formantu.|
|[Element TypeName dla EntrySelectedBy dla formantów widoku (Format)](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|Element opcjonalny.<br /><br /> Określa typ architektury .NET, która używa tej definicji kontrolki.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CustomEntry CustomEntries dla formantów widoku (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Zawiera definicję formantu.|

## <a name="remarks"></a>Uwagi

Wybór warunki są używane do definiowania warunek, który musi istnieć definicja ma być używany, np. Jeśli obiekt ma określoną właściwość lub gdy wartość określoną właściwość lub skryptu, które daje w wyniku `true`. Aby uzyskać więcej informacji o warunkach wyboru, zobacz [definiujący warunki dla, gdy wpis widoku lub służy element](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Zobacz też

[Element CustomEntry CustomEntries dla formantów widoku (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
