---
title: Element PropertyName SelectionCondition dla EntrySelectedBy dla WideEntry (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064683"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a>PropertyName, element — SelectionCondition, EntrySelectedBy, WideEntry (format)

Określa właściwości platformy .NET, która wyzwala warunku. Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i jest używany przez definicję.

— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) WideControl — Element (Format) WideEntries — Element (Format) WideEntry — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionCondition WideEntry (Format) EntrySelectedBy WideEntry (Format) elementu PropertyName SelectionCondition dla EntrySelectedBy dla WideEntry (Format)

## <a name="syntax"></a>Składnia

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

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
|[Element SelectionCondition EntrySelectedBy dla WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Określa warunek, który musi istnieć, aby ta definicja ma być używany.|

## <a name="text-value"></a>Wartość tekstowa

Określ nazwę właściwości platformy .NET.

## <a name="remarks"></a>Uwagi

Warunek wyboru należy określić co najmniej jedną właściwość name lub skryptu w celu oceny, ale nie można podać obydwie wartości. Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).

Aby uzyskać więcej informacji o innych składnikach szerokie, zobacz [szerokie](./creating-a-wide-view.md).

## <a name="see-also"></a>Zobacz też

[Tworzenie szerokiej widoku](./creating-a-wide-view.md)

[Definiowanie warunków, gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md)

[Element ScriptBlock SelectionCondition dla EntrySelectedBy dla WideEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[Element SelectionCondition EntrySelectedBy dla WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
