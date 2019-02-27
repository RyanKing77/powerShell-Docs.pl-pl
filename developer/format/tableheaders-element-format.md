---
title: Element TableHeaders (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847425"
---
# <a name="tableheaders-element-format"></a>TableHeaders, element (format)

Określa nagłówki kolumn w tabeli.

Element ViewDefinitions (Format) widoku elementu (w formacie) tablecontrol — Element (w formacie) TableHeaders elementu tablecontrol — (w formacie)

## <a name="syntax"></a>Składnia

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W następujących sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne `TableHeaders` elementu. Musi to być element podrzędny dla każdej właściwości obiektu, który ma być wyświetlana. Informacje nagłówka kolumny są wyświetlane w kolejności, że elementy podrzędne są określone.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element TableColumnHeader (Format)](./tablecolumnheader-element-format.md)|Element opcjonalny.<br /><br /> Definiuje etykietę, szerokości i wyrównania danych dla kolumny widoku tabeli.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Tablecontrol — Element (Format)](./tablecontrol-element-format.md)|Definiuje format tabeli w celu wyświetlenia.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).

## <a name="example"></a>Przykład

W tym przykładzie `TableHeaders` element, który definiuje dwa nagłówki kolumn.

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

[Tworzenie widoku tabeli](./creating-a-table-view.md)

[Element TableColumnHeader (Format)](./tablecolumnheader-element-format.md)

[Tablecontrol — Element (Format)](./tablecontrol-element-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
