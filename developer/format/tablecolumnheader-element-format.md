---
title: Element TableColumnHeader (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: 15f47c97ac5d55cb76e153af86672b3ffaf176c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848629"
---
# <a name="tablecolumnheader-element-format"></a>TableColumnHeader, element (format)

Definiuje etykietę, szerokość kolumny i wyrównanie etykiety w kolumnie tabeli.

— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) TableHeaders Element konfiguracji elementu TableColumnHeader tablecontrol — (w formacie) TableHeaders dla tablecontrol — (w formacie)

## <a name="syntax"></a>Składnia

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TableColumnHeader` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element LABEL dla TableColumnHeader dla tablecontrol — (w formacie)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|Element opcjonalny.<br /><br /> Definiuje etykietę, która jest wyświetlana w górnej części kolumny. Jeśli żadna etykieta nie zostanie określona, jest używana nazwa właściwości, którego wartość jest wyświetlana w wierszach.|
|[Szerokość elementu TableColumnHeader dla tablecontrol — (w formacie)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|Element wymagany.<br /><br /> Określa szerokość (w znakach) kolumny.|
|[Wyrównanie elementu TableColumbnHeader dla tablecontrol — (w formacie)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|Element opcjonalny.<br /><br /> Określa, jak jest wyświetlana etykieta kolumny. Jeśli określono bez wyrównania, etykieta jest wyrównany po lewej stronie.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element TableHeaders (Format)](./tableheaders-element-format.md)|Definiuje kolumny widoku tabeli.|

## <a name="remarks"></a>Uwagi

Określ nagłówek dla każdej kolumny w tabeli. Kolumny są wyświetlane w kolejności, w którym `TableColumnHeader` elementy są zdefiniowane.

Tabela musi mieć taką samą liczbę `TableColumnHeader` elementy jako `TableRowEntry` elementów. Nagłówek kolumny definiuje sposób wyświetlania tekstu w górnej części tabeli. Wpisy wiersz definiują, jakie dane są wyświetlane w wierszach tabeli.

Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [widok tabeli](./creating-a-table-view.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano dwa `TableColumnHeader` elementów. Pierwszy element określa kolumnę, której etykietę "kolumna 1" ma szerokość o długości 16 znaków i którego etykieta jest wyrównany po lewej stronie. Drugi element określa kolumnę, której etykietę "kolumna 2" ma szerokość 10 znaków i której etykietę skupia się w kolumnie.

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
    <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a>Zobacz też

[Wyrównanie elementu TableColumnHeader dla TableContrl (Format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Tworzenie widoku tabeli](./creating-a-table-view.md)

[Element LABEL dla TableColumnHeader dla tablecontrol — (w formacie)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Element TableHeaders tablecontrol — (w formacie)](./tableheaders-element-format.md)

[Szerokość TableColumnHeader dla tablecontrol — Element (Format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
