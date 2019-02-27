---
title: Element FormatString dla WideItem dla WideControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850267"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a>FormatString, element — WideItem, WideControl (format)

Określa wzorzec formatu, który definiuje sposób wyświetlania wartości właściwości lub skryptu w widoku.

— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) WideControl — Element (Format) WideEntries — Element (Format) WideEntry Element konfiguracji dla elementu WideItem WideControl (w formacie) dla elementu FormatString WideControl (Format) Aby uzyskać WideItem dla WideControl (Format)

## <a name="syntax"></a>Składnia

```xml
<FormatString>PropertyPattern</FormatString>
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
|[Element WideItem WideControl (Format)](./wideitem-element-for-widecontrol-format.md)|Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w wierszu w widoku listy.|

## <a name="text-value"></a>Wartość tekstowa

Określ wzorzec, który jest używany do formatowania danych. Na przykład, można używać tego wzorca do formatowania wartości dowolnej właściwości, która jest typu [System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {0:HH}: {0:mm}.

## <a name="remarks"></a>Uwagi

Ciągi formatu mogą być używane, podczas tworzenia widoki tabel, widoków listy, widoki szeroki lub widoków niestandardowych. Aby uzyskać więcej informacji na temat formatowania wartości wyświetlane w widoku, zobacz [formatowania danych wyświetlane](./formatting-displayed-data.md).

Aby uzyskać więcej informacji na temat używania ciągów formatu w widokach szerokiego zobacz [tworzenia szerokiej widoku](./creating-a-wide-view.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje jak zdefiniować ciąg formatowania dla wartości `StartTime` właściwości.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a>Zobacz też

[Tworzenie szerokiej widoku](./creating-a-wide-view.md)

[Element WideItem WideControl (Format)](./wideitem-element-for-widecontrol-format.md)

[Pisanie programu Windows PowerShell, formatowania i typy plików](./writing-a-powershell-formatting-file.md)
