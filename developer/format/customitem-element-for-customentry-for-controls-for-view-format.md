---
title: Element CustomItem CustomEntry dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066384"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>CustomItem, element — CustomEntry, Controls, View (format)

Definiuje, jakie dane są wyświetlane przez kontrolkę i sposób wyświetlania. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu CustomItem CustomEntry dla formantów widoku (Format)

## <a name="syntax"></a>Składnia

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `CustomItem` elementu. Aby uzyskać więcej informacji zobacz uwagi.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ExpressionBinding CustomItem dla formantów widoku (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Element opcjonalny.<br /><br /> Definiuje dane, które jest wyświetlany przez kontrolkę.|
|[Element ramki dla CustomItem dla formantów widoku (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)|Element opcjonalny.<br /><br /> Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony.|
|[Element nowego wiersza dla CustomItem dla formantów widoku (Format)](./newline-element-for-customitem-for-controls-for-view-format.md)|Element opcjonalny.<br /><br /> Dodaje pusty wiersz do wyświetlania kontrolki.|
|[Tekst elementu CustomItem dla formantów widoku (Format)](./text-element-for-customitem-for-controls-for-view-format.md)|Element opcjonalny.<br /><br /> Dodaje tekstu, na przykład nawiasów zwykłych lub nawiasy kwadratowe, do wyświetlania kontrolki.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CustomEntry CustomEntries dla formantów widoku (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Zawiera definicję formantu.|

## <a name="remarks"></a>Uwagi

Podczas określania elementów podrzędnych `CustomItem` elementu pamiętać o następujących czynności:

- Elementy podrzędne muszą zostać dodane w następującej kolejności: `ExpressionBinding`, `NewLine`, `Text`, i `Frame`.

- Nie ma żadnych maksymalnego limitu numer sekwencji, które można określić.

- W każdej sekwencji nie ma limitu maksymalnej liczby `ExpressionBinding` elementy, których można użyć.

## <a name="see-also"></a>Zobacz też

[Element ExpressionBinding CustomItem dla formantów widoku (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Element ramki dla CustomItem dla formantów widoku (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Element nowego wiersza dla CustomItem dla formantów widoku (Format)](./newline-element-for-customitem-for-controls-for-view-format.md)

[Tekst elementu CustomItem dla formantów widoku (Format)](./text-element-for-customitem-for-controls-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
