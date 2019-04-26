---
title: Element SelectionSetName EntrySelectedBy dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063925"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a>SelectionSetName, element — EntrySelectedBy, TableControl (format)

Określa, że zestaw .NET typy użycia tego wpisu w widoku tabeli. Nie ma żadnego limitu liczby zestawów wybór, które można określić dla wpisu.

— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) elementu TableRowEntries (Format) TableRowEntry — Element (Format) EntrySelectedBy — Element (Format) SelectionSetName Element konfiguracji dla EntrySelectedBy dla TableRowEntry (Format)

## <a name="syntax"></a>Składnia

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

Poniżej opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element EntrySelectedBy (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Definiuje typy .NET, korzystające z tego wpisu lub warunek, który musi istnieć dla tego wpisu do użycia.|

## <a name="text-value"></a>Wartość tekstowa

Określ nazwę zestawu wyboru.

## <a name="remarks"></a>Uwagi

Wybór zestawy są zwykle używane zdefiniować grupy obiektów, które są używane w wielu widoków. Na przykład można utworzyć widoku tabeli i widok listy, aby uzyskać ten sam zestaw obiektów. Aby uzyskać więcej informacji na temat definiowania zestawów wybór zobacz [Definiowanie ustawia obiektów w celu wyświetlenia](./defining-selection-sets.md).

Jeśli określisz zaznaczenia, ustaw dla wpisu, nie można określić nazwę typu. Aby uzyskać więcej informacji na temat sposobu określania typu .NET, zobacz [TypeName Element dla EntrySelectedBy dla TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).

Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).

## <a name="see-also"></a>Zobacz też

[Element EntrySelectedBy (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Definiowanie zestawów obiektów w celu wyświetlenia](./defining-selection-sets.md)

[Tworzenie widoku tabeli](./creating-a-table-view.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
