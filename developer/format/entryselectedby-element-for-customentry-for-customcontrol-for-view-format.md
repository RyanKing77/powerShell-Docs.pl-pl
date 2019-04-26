---
title: Element EntrySelectedBy CustomEntry dla formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066281"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>EntrySelectedBy, element — CustomEntry, CustomControl, View (format)

Definiuje typy .NET, korzystające z tego wpisu niestandardowych lub warunek, który musi istnieć dla tego wpisu do użycia.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy, Element (Format) CustomEntries Element konfiguracji dla formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla EntrySelectedBy widoku (Format) Element CustomEntry widoku (Format)

## <a name="syntax"></a>Składnia

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `EntrySelectedBy` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element SelectionCondition EntrySelectedBy dla CustomEntry (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Element opcjonalny.<br /><br /> Określa warunek, który musi istnieć, aby ta definicja ma być używany.|
|[Element SelectionSetName EntrySelectedBy dla CustomEntry (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|Element opcjonalny.<br /><br /> Określa zestaw typów .NET, korzystających z tej definicji widoku kontrolnym.|
|[Element TypeName dla EntrySelectedBy dla CustomEntry (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Element opcjonalny.<br /><br /> Określa typ architektury .NET, który używa tej definicji widoku kontrolnym.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CustomEntry CustomEntries widoku (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Definiuje kontrolki, używany przez konkretne obiekty platformy .NET.|

## <a name="remarks"></a>Uwagi

Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru dla wpisu. Jest nieograniczona maksymalną liczbę elementów podrzędnych, które są dostępne.

Wybór warunki są używane do definiowania warunek, który musi istnieć wpis, który ma być używany, np. Jeśli obiekt ma określoną właściwość lub gdy wartość określoną właściwość lub skryptu, które daje w wyniku `true`. Aby uzyskać więcej informacji o warunkach wyboru, zobacz [definiujący warunki dla, gdy wpis widoku lub służy element](./defining-conditions-for-displaying-data.md).

Aby uzyskać więcej informacji o składnikach widoku kontrolki niestandardowej, zobacz [widok niestandardowy formant](./creating-custom-controls.md).

## <a name="see-also"></a>Zobacz też

[Element SelectionCondition EntrySelectedBy dla CustomEntry (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Element SelectionSetName EntrySelectedBy dla CustomEntry (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[Element TypeName dla EntrySelectedBy dla CustomEntry (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Element CustomEntry CustomEntries widoku (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Wyświetl formant niestandardowy](./creating-custom-controls.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
