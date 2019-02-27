---
title: Element SelectionCondition EntrySelectedBy dla WideControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845493"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a>SelectionCondition, element — EntrySelectedBy, WideControl (format)

Określa warunek, który musi istnieć, aby ta definicja ma być używany. Nie ma żadnego limitu, liczbę warunków wyboru, które można określić dla definicji szerokiego wpisu.

— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) WideControl — Element (Format) WideEntries — Element (Format) WideEntry — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionCondition WideEntry (Format) EntrySelectedBy dla WideEntry (Format)

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
|[Element PropertyName SelectionCondition dla EntrySelectedBy dla WideEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|Element opcjonalny.<br /><br /> Określa właściwości platformy .NET, która wyzwala warunku.|
|[Element ScriptBlock SelectionCondition dla EntrySelectedBy dla WideEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|Element opcjonalny.<br /><br /> Określa blok skryptu, który wyzwala warunku.|
|[Element SelectionSetName SelectionCondition dla EntrySelectedBy dla WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|Element opcjonalny.<br /><br /> Określa zestaw typów .NET wyzwalającego warunku.|
|[Element TypeName dla SelectionCondition dla EntrySelectedBy dla WideEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|Element opcjonalny.<br /><br /> Określa typ architektury .NET, która wyzwala warunku.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element EntrySelectedBy WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Definiuje typy .NET, korzystające z tego wpisu szeroki lub warunek, który musi istnieć dla tego wpisu do użycia.|

## <a name="remarks"></a>Uwagi

Każdy wpis szerokiego musi mieć co najmniej jedną nazwę typu, wybór zestawu lub warunek wyboru.

Podczas definiowania warunek wyboru mają zastosowanie następujące wymagania:

- Warunek wyboru należy określić co najmniej jednej nazwy właściwości lub blok skryptu, ale nie można określić jednocześnie.

- Warunek wyboru można określić dowolną liczbę typów .NET lub zaznaczenie Ustawia, ale nie można określić jednocześnie.

Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [definiujący warunki dla, gdy wpis widoku lub służy element](./defining-conditions-for-displaying-data.md).

Aby uzyskać więcej informacji o innych składnikach szerokie, zobacz [tworzenia szerokiej widoku](./creating-a-wide-view.md).

## <a name="see-also"></a>Zobacz też

[Tworzenie szerokiej widoku](./creating-a-wide-view.md)

[Definiowanie warunków, gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md)

[Element EntrySelectedBy WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)

[Element PropertyName SelectionCondition dla EntrySelectedBy dla WideEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Element ScriptBlock SelectionCondition dla EntrySelectedBy dla WideEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[Element SelectionSetName SelectionCondition dla EntrySelectedBy dla WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Element TypeName dla SelectionCondition dla EntrySelectedBy dla WideEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
