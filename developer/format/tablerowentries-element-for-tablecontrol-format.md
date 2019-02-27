---
title: Element TableRowEntries tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: d93750f919c1075f173dc9ac70324cc003e36879
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851142"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a>TableRowEntries, element — TableControl (format)

Definiuje wiersze w tabeli.

— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) tablecontrol — Element (w formacie) TableRowEntries Element konfiguracji dla tablecontrol — (w formacie)

## <a name="syntax"></a>Składnia

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TableRowEntries` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element TableRowEntry TableRowEntries dla tablecontrol — (w formacie)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|Element wymagany.<br /><br /> Definiuje dane, które są wyświetlane w wierszu tabeli.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Tablecontrol — Element (Format)](./tablecontrol-element-format.md)|Definiuje format tabeli w celu wyświetlenia.|

## <a name="remarks"></a>Uwagi

Należy określić co najmniej jedną `TableRowEntry` elementów do widoku tabeli. Nie ma żadnego limitu maksymalnej liczby `TableRowEntry` elementy, które można dodać ani nie jest ważna ich kolejność.

Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `TableRowEntries` element, który definiuje wiersza, który wyświetla wartości właściwości dwóch [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu.

```xml
<TableRowEntries>
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
</TableRowEntries>

```

## <a name="see-also"></a>Zobacz też

[Tworzenie widoku tabeli](./creating-a-table-view.md)

[Tablecontrol — Element (Format)](./tablecontrol-element-format.md)

[Element TableRowEntry (Format)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
