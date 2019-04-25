---
title: Element SelectionSetName EntrySelectedBy dla formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063981"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a>SelectionSetName, element — EntrySelectedBy, CustomControl, View (format)

Określa zestaw obiektów platformy .NET dla wpisu listy. Nie ma żadnego limitu liczby zestawów wybór, które można określić dla wpisu.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy, Element (Format) CustomEntries Element konfiguracji dla formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla EntrySelectedBy widoku (Format) Element CustomEntry widoku (Format) elementu SelectionSetName EntrySelectedBy dla CustomEntry (Format)

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
|[Element EntrySelectedBy CustomEntry widoku (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Definiuje typy .NET, korzystające z tego wpisu niestandardowych lub warunek, który musi istnieć dla tego wpisu do użycia.|

## <a name="text-value"></a>Wartość tekstowa

Określ nazwę zestawu wyboru.

## <a name="remarks"></a>Uwagi

Każdy wpis formant niestandardowy musi mieć co najmniej jedną nazwę typu, wybór zestawu lub warunek wyboru.

Wybór zestawy są zwykle używane zdefiniować grupy obiektów, które są używane w wielu widoków. Na przykład można utworzyć widoku tabeli i widok listy, aby uzyskać ten sam zestaw obiektów. Aby uzyskać więcej informacji na temat definiowania zestawów wybór zobacz [Definiowanie ustawia wybór](./defining-selection-sets.md).

Aby uzyskać więcej informacji o składnikach widoku kontrolki niestandardowej, zobacz [Tworzenie niestandardowych formantów](./creating-custom-controls.md).

## <a name="see-also"></a>Zobacz też

[Element EntrySelectedBy CustomEntry widoku (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Wyświetl formant niestandardowy](./creating-custom-controls.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
