---
title: Element PropertyName SelectionCondition dla formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48a417-2083-46d4-ac38-16c12e65b6b9
caps.latest.revision: 7
ms.openlocfilehash: e08037d5d051d3be51e90193c7e87cc2e738f78a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064700"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a>PropertyName, element — SelectionCondition, CustomControl, View (format)

Określa właściwości platformy .NET, która wyzwala warunku. Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i jest używany przez definicję. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy Element konfiguracji elementu CustomEntries widoku (Format), formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formant niestandardowy do widoku ( Format) elementu CustomItem CustomEntry dla formant niestandardowy widok (w formacie) elementu EntrySelectedBy CustomEntry dla formant niestandardowy widok (w formacie) elementu SelectionCondition EntrySelectedBy dla formant niestandardowy do PropertyName widoku (Format) Element SelectionCondition dla formant niestandardowy dla widoku (Format)

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
|[Element SelectionCondition EntrySelectedBy dla formant niestandardowy dla widoku (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Określa warunek, który musi istnieć dla definicji kontrolki ma być używany.|

## <a name="text-value"></a>Wartość tekstowa

Określ nazwę właściwości platformy .NET.

## <a name="remarks"></a>Uwagi

Warunek wyboru należy określić co najmniej jednej nazwy właściwości lub skryptu, ale nie można określić jednocześnie. Aby uzyskać więcej informacji o używaniu wybór warunków, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Zobacz też

[Element SelectionCondition EntrySelectedBy dla formant niestandardowy dla widoku (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
