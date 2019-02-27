---
title: Element SelectionSetName EntrySelectedBy dla EnumerableExpansion (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851534"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a>SelectionSetName, element — EntrySelectedBy, EnumerableExpansion (format)

Określa zestaw typów .NET, które są rozszerzane przez tę definicję.

— Element (w formacie) DefaultSettings — Element (Format) EnumerableExpansions — Element (Format) EnumerableExpansion — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionSetName EnumerableExpansion (Format) EntrySelectedBy dla EnumerableExpansion (Format)

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
|[Element EntrySelectedBy EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md)|Definiuje obiekty kolekcji .NET, które są rozszerzane przez tę definicję.|

## <a name="text-value"></a>Wartość tekstowa

Określ nazwę zestawu wyboru.

## <a name="remarks"></a>Uwagi

Każda definicja należy określić co najmniej jedną nazwę typu, zestaw zaznaczenia lub warunek wyboru.

Wybór zestawy są zwykle używane zdefiniować grupy obiektów, które są używane w wielu widoków. Na przykład można utworzyć widoku tabeli i widok listy, aby uzyskać ten sam zestaw obiektów. Aby uzyskać więcej informacji na temat definiowania zestawów wybór zobacz [Definiowanie ustawia z obiektów w celu wyświetlenia](./defining-selection-sets.md).

## <a name="see-also"></a>Zobacz też

[Definiowanie zestawów zaznaczenia](./defining-selection-sets.md)

[Element EntrySelectedBy EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
