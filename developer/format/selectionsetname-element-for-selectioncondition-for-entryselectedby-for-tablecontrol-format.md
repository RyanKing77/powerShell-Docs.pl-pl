---
title: Element SelectionSetName SelectionCondition dla EntrySelectedBy dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064054"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>SelectionSetName, element — SelectionCondition, EntrySelectedBy, TableControl (format)

Określa zestaw typów .NET, które mogą powodować warunku. Jeśli typy w tym zestawie, warunek jest spełniony, a obiekt jest wyświetlana przy użyciu tej definicji widoku tabeli.

— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) elementu TableRowEntries (Format) TableRowEntry — Element (Format) EntrySelectedBy Element konfiguracji dla TableRowEntry (Format) Element SelectionCondition EntrySelectedBy TableRowEntry (Format) elementu SelectionSetName SelectionCondition dla EntrySelectedBy dla TableRowEntry (Format)

## <a name="syntax"></a>Składnia

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionSetName` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element SelectionCondition EntrySelectedBy dla TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Określa warunek, który musi istnieć na potrzeby tej definicji widoku tabeli.|

## <a name="text-value"></a>Wartość tekstowa

Określ nazwę zestawu wyboru.

## <a name="remarks"></a>Uwagi

Warunek wyboru można określić zbiór lub typ architektury .NET, ale nie można określić jednocześnie. Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).

Wybór zestawy są wspólne grupy obiektów platformy .NET, które mogą być używane przez dowolny widok, który definiuje formatowania pliku. Aby uzyskać więcej informacji na temat tworzenia i odwołania do zestawów wybór zobacz [Definiowanie ustawia z obiektów](./defining-selection-sets.md).

Aby uzyskać więcej informacji o innych składnikach szerokie, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).

## <a name="see-also"></a>Zobacz też

[Tworzenie widoku tabeli](./creating-a-table-view.md)

[Definiowanie warunków, gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md)

[Element TypeName dla SelectionCondition dla EntrySelectedBy dla TableRowEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Element SelectionCondition EntrySelectedBy dla TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
