---
title: Element SelectionCondition EntrySelectedBy dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: 633204f3b181316761746ea2679910216fb74657
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058968"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a>SelectionCondition, element — EntrySelectedBy, ListControl (format)

Określa warunek, którego można użyć tej definicji widoku listy, musi istnieć. Nie ma żadnego limitu liczby warunki wyboru, które mogą być określone dla definicji listy.

— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) elementu ListEntries (Format) ListEntry — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionCondition ListEntry (Format) EntrySelectedBy dla ListEntry (Format)

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

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionCondition` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element PropertyName SelectionCondition dla EntrySelectedBy dla ListEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Element opcjonalny.<br /><br /> Określa właściwości platformy .NET, która wyzwala warunku.|
|[Element ScriptBlock SelectionCondition dla EntrySelectedBy dla ListEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Element opcjonalny.<br /><br /> Określa skrypt, który wyzwala warunku.|
|[Element SelectionSetName SelectionCondition dla EntrySelectedBy dla ListEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|Element opcjonalny.<br /><br /> Określa zestaw typów .NET, które mogą powodować warunku.|
|[Element TypeName dla SelectionCondition dla EntrySelectedBy dla ListEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Element opcjonalny.<br /><br /> Określa typ architektury .NET, która wyzwala warunku.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element EntrySelectedBy TableRowEntry (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Definiuje typy .NET, korzystające z tego wpisu w tabeli lub warunek, który musi istnieć dla tego wpisu do użycia.|

## <a name="remarks"></a>Uwagi

określasz warunek wyboru lWhen, obowiązują następujące wymagania:

- Warunek wyboru należy określić co najmniej jednej nazwy właściwości lub blok skryptu, ale nie można określić jednocześnie.

- Warunek wyboru można określić dowolną liczbę typów .NET lub zaznaczenie Ustawia, ale nie można określić jednocześnie.

Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).

Aby uzyskać więcej informacji o innych składnikach widoku listy, zobacz [tworzenia widoku listy](./creating-a-list-view.md).

## <a name="see-also"></a>Zobacz też

[Tworzenie widoku listy](./creating-a-list-view.md)

[Definiowanie warunków, gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md)

[Element ListEntry (Format)](./listentry-element-for-listcontrol-format.md)

[Element SelectionSetName EntrySelectedBy dla ListEntry (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Element TypeName dla EntrySelectedBy dla ListEntry (Format)](http://msdn.microsoft.com/en-us/fcd4daa6-f3fd-43f7-a468-03c582d34533)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
