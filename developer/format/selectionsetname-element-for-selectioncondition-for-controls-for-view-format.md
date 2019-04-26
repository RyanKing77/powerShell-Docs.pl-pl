---
title: Element SelectionSetName SelectionCondition dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: daea8c6f-873a-4639-9eee-599642822958
caps.latest.revision: 6
ms.openlocfilehash: 697f2ea284393ebddd77a862c408f27f3d332900
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063891"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a>SelectionSetName, element — SelectionCondition, Controls, View (format)

Określa zestaw typów .NET, które mogą powodować warunku. Gdy dowolnego typu, w tym zestawie, warunek jest spełniony, i jest wyświetlany obiekt, za pomocą tego formantu. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy dla formantów widoku (Format) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu EntrySelectedBy CustomEntry dla formantów widoku (Format) elementu SelectionCondition EntrySelectedBy dla kontrolki (Widok Format) elementu SelectionSetName SelectionCondition dla formantów widoku (Format)

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
|[Element SelectionCondition EntrySelectedBy dla formantów widoku (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Określa warunek, który musi istnieć dla definicji kontrolki ma być używany.|

## <a name="text-value"></a>Wartość tekstowa

Określ nazwę zestawu wyboru.

## <a name="remarks"></a>Uwagi

Wybór zestawy są wspólne grupy obiektów platformy .NET, które mogą być używane przez dowolny widok, który definiuje formatowania pliku. Aby uzyskać więcej informacji na temat tworzenia i odwołania do zestawów wybór zobacz [Definiowanie ustawia wybór](./defining-selection-sets.md).

Warunek wyboru można określić zbiór lub typ architektury .NET, ale nie można określić jednocześnie. Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Zobacz też

[Element SelectionCondition EntrySelectedBy dla formantów widoku (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[Definiowanie warunków, gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md)

[Definiowanie zestawów zaznaczenia](./defining-selection-sets.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
