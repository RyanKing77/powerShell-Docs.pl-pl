---
title: Element EntrySelectedBy EnumerableExpansion (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066213"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a>EntrySelectedBy, element — EnumerableExpansion (format)

Definiuje typy .NET, które używają tej definicji lub warunek, który musi istnieć, aby ta definicja ma być używany.

— Element (Format) DefaultSettings — Element (Format) elementu EnumerableExpansions (Format) elementu EnumerableExpansion (Format) EntrySelectedBy Element konfiguracji dla EnumerableExpansion (Format)

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
|[Element SelectionCondition EntrySelectedBy dla EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Element opcjonalny.<br /><br /> Określa warunek, który musi istnieć, aby rozwinąć kolekcji obiektów tej definicji.|
|[Element SelectionSetName EntrySelectedBy dla EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|Element opcjonalny.<br /><br /> Określa zestaw typów .NET, korzystających z tej definicji jak obiekty kolekcji zostaną rozwinięte.|
|[Element TypeName dla EntrySelectedBy dla EnumerableExpansion (Format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|Element opcjonalny.<br /><br /> Określa typ architektury .NET, który używa tej definicji jak obiekty kolekcji zostaną rozwinięte.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element EnumerableExpansion (Format)](./enumerableexpansion-element-format.md)|Definiuje sposób określonej kolekcji .NET, które obiekty są rozszerzane, gdy są one wyświetlane w widoku.|

## <a name="remarks"></a>Uwagi

Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru dla wpisu definicji. Jest nieograniczona maksymalną liczbę elementów podrzędnych, które są dostępne.

Wybór warunki są używane do definiowania warunek, który musi istnieć dla definicji, który ma być używany, na przykład jeśli obiekt ma określoną właściwość lub wartość określoną właściwość lub skrypt daje w wyniku `true`. Aby uzyskać więcej informacji o warunkach wyboru, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Zobacz też

[Definiowanie warunków do wyświetlania danych](./defining-conditions-for-displaying-data.md)

[Element EnumerableExpansion (Format)](./enumerableexpansion-element-format.md)

[Element SelectionCondition EntrySelectedBy dla EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Element SelectionSetName EntrySelectedBy dla EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Element TypeName dla EntrySelectedBy dla EnumerableExpansion (Format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
