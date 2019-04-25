---
title: Element CustomItem CustomEntry dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066434"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a>CustomItem, element — CustomEntry, Controls, Configuration (Format)

Definiuje, jakie dane są wyświetlane przez kontrolkę i sposób wyświetlania. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do konfiguracji ( Format) elementu CustomEntry formant niestandardowy dla formantów CustomItem elementu konfiguracji (Format) CustomEntry dla formantów dla konfiguracji

## <a name="syntax"></a>Składnia

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `CustomItem` elementu. Aby uzyskać więcej informacji zobacz uwagi.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ExpressionBinding CustomItem dla formantów dla konfiguracji (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Element opcjonalny.<br /><br /> Definiuje dane, które jest wyświetlany przez kontrolkę.|
|[Element ramki dla CustomItem dla formantów dla konfiguracji (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Element opcjonalny.<br /><br /> Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony.|
|[Element nowego wiersza dla CustomItem dla formantów dla konfiguracji (Format)](./newline-element-for-customitem-for-controls-for-configuration-format.md)|Element opcjonalny.<br /><br /> Dodaje pusty wiersz do wyświetlania kontrolki.|
|[Tekst elementu CustomItem dla formantów dla konfiguracji (Format)](./text-element-for-customitem-for-controls-for-configuration-format.md)|Element opcjonalny.<br /><br /> Dodaje tekstu, na przykład nawiasów zwykłych lub nawiasy kwadratowe, do wyświetlania kontrolki.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CustomEntry formant niestandardowy dla formantów dla konfiguracji (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Zawiera definicję formantu.|

## <a name="remarks"></a>Uwagi

Podczas określania elementów podrzędnych `CustomItem` elementu pamiętać o następujących czynności:

- Elementy podrzędne muszą zostać dodane w następującej kolejności: `ExpressionBinding`, `NewLine`, `Text`, i `Frame`.

- Nie ma żadnych maksymalnego limitu numer sekwencji, które można określić.

- W każdej sekwencji nie ma limitu maksymalnej liczby `ExpressionBinding` elementy, których można użyć.

## <a name="see-also"></a>Zobacz też

[Element ExpressionBinding CustomItem dla formantów dla konfiguracji (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Element ramki dla CustomItem dla formantów dla konfiguracji (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Element nowego wiersza dla CustomItem dla formantów dla konfiguracji (Format)](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[Tekst elementu CustomItem dla formantów dla konfiguracji (Format)](./text-element-for-customitem-for-controls-for-configuration-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
