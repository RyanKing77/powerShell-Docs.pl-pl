---
title: Element EntrySelectedBy TableRowEntry dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066162"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a>EntrySelectedBy, element — TableRowEntry, TableControl (format)

Definiuje typy .NET używających tej definicji widoku tabeli lub warunek, który musi istnieć, aby ta definicja ma być używany.

— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) tablecontrol — Element (Format) TableRowEntries — Element (Format) TableRowEntry — Element (Format) EntrySelectedBy Element konfiguracji (Format)

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
|[Element SelectionCondition EntrySelectedBy dla tablecontrol — (w formacie)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Element opcjonalny.<br /><br /> Określa warunek, który musi istnieć dla tej definicji widoku tabeli ma być używany.|
|[Element SelectionSetName EntrySelectedBy dla tablecontrol — (w formacie)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|Element opcjonalny.<br /><br /> Określa zestaw typów .NET, korzystających z tej definicji widoku tabeli.|
|[Element TypeName dla EntrySelectedBy dla tablecontrol — (w formacie)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|Element opcjonalny.<br /><br /> Określa typ architektury .NET, która używa tej definicji widoku tabeli.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element TableRowEntry tablecontrol — (w formacie)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Definiuje dane, które są wyświetlane w wierszu tabeli.|

## <a name="remarks"></a>Uwagi

Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru definicji widoku tabeli. Jest nieograniczona maksymalną liczbę elementów podrzędnych, które są dostępne.

Wybór warunki są używane do definiowania warunek, który musi istnieć dla definicji, który ma być używany, na przykład jeśli obiekt ma określoną właściwość lub wartość określoną właściwość lub skrypt daje w wyniku `true`. Aby uzyskać więcej informacji o warunkach wyboru, zobacz [definiujący warunki dla, gdy wpis widoku lub służy element](./defining-conditions-for-displaying-data.md).

Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `TableRowEntry` element, który służy do wyświetlania właściwości [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a>Zobacz też

[Tworzenie widoku tabeli](./creating-a-table-view.md)

[Element SelectionCondition EntrySelectedBy dla tablecontrol — (w formacie)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Element SelectionSetName EntrySelectedBy dla tablecontrol — (w formacie)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[Element TableRowEntry tablecontrol — (w formacie)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Element TypeName dla EntrySelectedBy dla tablecontrol — (w formacie)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
