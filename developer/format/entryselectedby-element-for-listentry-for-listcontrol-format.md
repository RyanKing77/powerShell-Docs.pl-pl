---
title: Element EntrySelectedBy ListEntry dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054947"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a>EntrySelectedBy, element — ListEntry, ListControl (format)

Definiuje typy .NET, które używają tej definicji widoku listy lub warunek, który musi istnieć, aby ta definicja ma być używany. W większości przypadków tylko jedną definicję, jest wymagany dla widoku listy. Może jednak zapewniać wiele definicji widoku listy, jeśli chcesz użyć tego samego widoku listy do wyświetlenia różnych danych do różnych obiektów.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) ListEntries Element konfiguracji elementu ListControl (Format) elementu ListEntry ListEntry elementu EntrySelectedBy elementu ListControl (Format) ListEntry dla elementu ListControl (Format)

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
|[Element SelectionCondition EntrySelectedBy dla elementu ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Element opcjonalny.<br /><br /> Określa warunek, który musi istnieć dla tej definicji widoku listy ma być używany.|
|[Element SelectionSetName EntrySelectedBy dla elementu ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|Element opcjonalny.<br /><br /> Określa zestaw typów .NET, które używają tej definicji widoku listy.|
|[Element TypeName dla EntrySelectedBy dla elementu ListControl (Format)](./typename-element-for-entryselectedby-for-listcontrol-format.md)|Element opcjonalny.<br /><br /> Określa typ architektury .NET, która używa tej definicji widoku listy.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ListEntry dla elementu ListControl (Format)](./listentry-element-for-listcontrol-format.md)|Definiuje sposób wyświetlania wierszy listy.|

## <a name="remarks"></a>Uwagi

Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru definicji widoku listy. Jest nieograniczona maksymalną liczbę elementów podrzędnych, które są dostępne.

Wybór warunki są używane do definiowania warunek, który musi istnieć dla definicji, który ma być używany, na przykład jeśli obiekt ma określoną właściwość lub wartość określoną właściwość lub skrypt daje w wyniku `true`. Aby uzyskać więcej informacji o warunkach wyboru, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).

Aby uzyskać więcej informacji o składnikach w widoku listy, zobacz [tworzenia widoku listy](./creating-a-list-view.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje jak zdefiniować obiektów w celu wyświetlenia listy za pomocą nazwy typu platformy .NET.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a>Zobacz też

[Element ListEntry dla elementu ListControl (Format)](./listentry-element-for-listcontrol-format.md)

[Element SelectionCondition EntrySelectedBy dla elementu ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Element SelectionSetName EntrySelectedBy dla elementu ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Element TypeName dla EntrySelectedBy dla elementu ListControl (Format)](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[Tworzenie widoku listy](./creating-a-list-view.md)

[Definiowanie warunków, gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
