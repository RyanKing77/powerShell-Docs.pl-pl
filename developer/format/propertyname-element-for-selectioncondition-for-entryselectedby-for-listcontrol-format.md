---
title: Element PropertyName SelectionCondition dla EntrySelectedBy dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: 7d526372cf80327b3fb9b79b6e83429c57780183
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064895"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>PropertyName, element — SelectionCondition, EntrySelectedBy, ListControl (format)

Określa właściwości platformy .NET, która wyzwala warunku. Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i wpis na liście jest używany.

— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) elementu ListEntries (Format) ListEntry — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionCondition ListEntry (Format) EntrySelectedBy ListEntry (Format) elementu PropertyName SelectionCondition dla EntrySelectedBy dla ListEntry (Format)

## <a name="syntax"></a>Składnia

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `PropertyName` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element SelectionCondition EntrySelectedBy dla ListEntry (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Określa warunek, który musi istnieć dla tego wpisu listy ma być używany.|

## <a name="text-value"></a>Wartość tekstowa

Określ nazwę właściwości platformy .NET.

## <a name="remarks"></a>Uwagi

Warunek wyboru należy określić co najmniej jedną właściwość name lub blok skryptu, ale nie można określić jednocześnie. Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [definiujący warunki dla, gdy wpis widoku lub służy element](./defining-conditions-for-displaying-data.md).

Aby uzyskać więcej informacji o innych składnikach widoku listy, zobacz [tworzenia widoku listy](./creating-a-list-view.md).

## <a name="see-also"></a>Zobacz też

[Tworzenie widoku listy](./creating-a-list-view.md)

[Definiowanie warunków podczas danych jest wyświetlana.](./defining-conditions-for-displaying-data.md)

[Element ListEntry (Format)](./listentry-element-for-listcontrol-format.md)

[Element ScriptBlock SelectionCondition dla EntrySelectedBy dla ListEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
