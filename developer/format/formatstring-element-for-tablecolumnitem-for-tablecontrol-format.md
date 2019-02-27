---
title: Element FormatString dla TableColumnItem dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845640"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a>FormatString, element — TableColumnItem, TableControl (format)

Określa wzorzec formatu, który definiuje sposób wyświetlania wartości właściwości lub skrypt tabeli.

— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) elementu TableRowEntries (Format) TableRowEntry — Element (Format) TableColumnItems — Element (Format) TableColumnItem Element konfiguracji (Format) Element FormatString dla TableColumnItem (Format)

## <a name="syntax"></a>Składnia

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `FormatString` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element TableColumnItem (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w kolumnie wiersza.|

## <a name="text-value"></a>Wartość tekstowa

Określ wzorzec, który jest używany do formatowania danych. Na przykład, ten wzorzec może służyć do formatowania wartości dowolnej właściwości, która jest typu [System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {0:HH}: {0:mm}.

## <a name="remarks"></a>Uwagi

Ciągi formatu mogą być używane, podczas tworzenia widoki tabel, widoków listy, widoki szeroki lub widoków niestandardowych. Aby uzyskać więcej informacji na temat formatowania wartości wyświetlane w widoku, zobacz [formatowania danych wyświetlane](./formatting-displayed-data.md).

Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [widok tabeli](./creating-a-table-view.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje jak zdefiniować ciąg formatowania dla wartości `StartTime` właściwości.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a>Zobacz też

[Tworzenie widoku tabeli](./creating-a-table-view.md)

[Formatowanie wyświetlanych danych](./formatting-displayed-data.md)

[Element TableColumnItem (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
