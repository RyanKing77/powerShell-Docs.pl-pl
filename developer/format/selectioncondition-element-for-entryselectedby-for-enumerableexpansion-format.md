---
title: Element SelectionCondition EntrySelectedBy dla EnumerableExpansion (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064139"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a>SelectionCondition, element — EntrySelectedBy, EnumerableExpansion (format)

Określa warunek, który musi istnieć, aby rozwinąć kolekcji obiektów tej definicji.

— Element (w formacie) DefaultSettings — Element (Format) EnumerableExpansions — Element (Format) EnumerableExpansion — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionCondition EnumerableExpansion (Format) EntrySelectedBy dla EnumerableExpansion (Format)

## <a name="syntax"></a>Składnia

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionCondition` elementu. Należy określić pojedynczy `PropertyName` lub `ScriptBlock` elementu. `SelectionSetName` i `TypeName` elementy są opcjonalne. Można określić jedną z dowolnego elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element PropertyName SelectionCondition dla EntrySelectedBy dla EnumerableExpansion (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Element opcjonalny.<br /><br /> Określa właściwości platformy .NET, która wyzwala warunku.|
|[Element ScriptBlock SelectionCondition dla EntrySelectedBy dla EnumerableExpansion (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Element opcjonalny.<br /><br /> Określa skrypt, który wyzwala warunku.|
|[Element SelectionSetName SelectionCondition dla EntrySelectedBy dla EnumerableExpansion (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Element opcjonalny.<br /><br /> Określa zestaw typów .NET wyzwalającego warunku.|
|[Element TypeName dla SelectionCondition dla EntrySelectedBy dla EnumerableExpansion (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Element opcjonalny.<br /><br /> Określa typ architektury .NET, która wyzwala warunku.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element EntrySelectedBy EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md)|Definiuje, które obiekty kolekcji .NET są rozszerzane przez tę definicję.|

## <a name="remarks"></a>Uwagi

Każda definicja musi mieć co najmniej jedną nazwę typu, wybór zestawu lub warunek wyboru.

Podczas definiowania warunek wyboru mają zastosowanie następujące wymagania:

- Warunek wyboru należy określić co najmniej jednej nazwy właściwości lub blok skryptu, ale nie można określić jednocześnie.

- Warunek wyboru można określić dowolną liczbę typów .NET lub zaznaczenie Ustawia, ale nie można określić jednocześnie.

Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [Definiowanie warunków danych Diplaying](./defining-conditions-for-displaying-data.md).

Aby uzyskać więcej informacji o innych składnikach szerokie, zobacz [szerokie](./creating-a-wide-view.md).

## <a name="see-also"></a>Zobacz też

[Definiowanie warunków, gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
