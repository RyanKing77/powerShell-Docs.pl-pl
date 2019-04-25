---
title: Element SelectionSetName SelectionCondition dla EntrySelectedBy dla EnumerableExpansion (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063864"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>SelectionSetName, element — SelectionCondition, EntrySelectedBy, EnumerableExpansion (format)

Określa zestaw typów .NET, które mogą powodować warunku. Jeśli jeden z typów, w tym zestawie, warunek jest spełniony.

Element DefaultSettings — Element (Format) EnumerableExpansions — Element (w formacie) EnumerableExpansions — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionCondition EnumerableExpansion (Format) EntrySelectedBy dla Element SelectionSetName EnumerableExpansion (w formacie) dla SelectionCondition dla EntrySelectedBy dla EnumerableExpansion (Format)

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
|[Element SelectionCondition EntrySelectedBy dla EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Określa warunek, który musi istnieć, aby rozwinąć kolekcji obiektów tej definicji.|

## <a name="text-value"></a>Wartość tekstowa

Określ nazwę zestawu wyboru.

## <a name="remarks"></a>Uwagi

Warunek wyboru można określić zbiór lub typ architektury .NET, ale nie można określić jednocześnie. Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).

Wybór zestawy są wspólne grupy obiektów platformy .NET, które mogą być używane przez dowolny widok, który definiuje formatowania pliku. Aby uzyskać więcej informacji na temat tworzenia i odwołania do zestawów wybór zobacz [Definiowanie ustawia wybór](./defining-selection-sets.md).

## <a name="see-also"></a>Zobacz też

[Definiowanie zestawów zaznaczenia](./defining-selection-sets.md)

[Element SelectionCondition EntrySelectedBy dla EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
