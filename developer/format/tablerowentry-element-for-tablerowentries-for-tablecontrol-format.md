---
title: Element TableRowEntry TableRowEntries dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075328"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a>TableRowEntry, element — TableRowEntries, TableControl (format)

Definiuje dane, które są wyświetlane w wierszu tabeli.

— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) TableRowEntries Element konfiguracji elementu TableRowEntry tablecontrol — (w formacie) TableRowEntries dla tablecontrol — (w formacie)

## <a name="syntax"></a>Składnia

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TableRowEntry` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element EntrySelectedBy TableRowEntry dla tablecontrol — (w formacie)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Element wymagany.<br /><br /> Definiuje obiekty, których wartości właściwości są wyświetlane w wierszu.|
|[Element TableColumnItems TableRowEntry dla tablecontrol — (w formacie)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Element wymagany.<br /><br /> Definiuje właściwości lub skryptów, których wartości są wyświetlane.|
|[OPAKOWYWANIE Element do TableRowEntry dla tablecontrol — (w formacie)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|Element opcjonalny.<br /><br /> Określa, czy tekst przekraczający szerokość kolumny jest wyświetlane w następnym wierszu.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element TableRowEntries tablecontrol — (w formacie)](./tablerowentries-element-for-tablecontrol-format.md)|Definiuje wiersze w tabeli.|

## <a name="remarks"></a>Uwagi

Jeden `TableColumnItems` elementu i jeden `EntrySelectedBy` element musi być określona.

Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `TableRowEntry` element, który definiuje wiersza, który wyświetla wartości właściwości dwóch [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName> Property for first column</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName> Property for second column</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a>Zobacz też

[Tworzenie widoku tabeli](./creating-a-table-view.md)

[Element EntrySelectedBy TableRowEntry dla tablecontrol — (w formacie)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Element TableColumnItems TableRowEntry dla tablecontrol — (w formacie)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[Element TableRowEntries tablecontrol — (w formacie)](./tablerowentries-element-for-tablecontrol-format.md)

[OPAKOWYWANIE Element do TableRowEntry dla tablecontrol — (w formacie)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
