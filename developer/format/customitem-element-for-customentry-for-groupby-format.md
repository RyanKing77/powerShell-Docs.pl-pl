---
title: Element CustomItem CustomEntry dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066401"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a>CustomItem, element — CustomEntry, GroupBy (format)

Definiuje, jakie dane są wyświetlane w widoku formantu niestandardowego i sposób wyświetlania. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomItem GroupBy (Format) CustomEntry dla grupowania (w formacie)

## <a name="syntax"></a>Składnia

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `CustomItem` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ExpressionBinding CustomItem dla grupowania (w formacie)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Element opcjonalny.<br /><br /> Definiuje dane, które jest wyświetlany przez kontrolkę.|
|[Element ramki dla CustomItem dla grupowania (w formacie)](./frame-element-for-customitem-for-groupby-format.md)|Element opcjonalny.<br /><br /> Definiuje, jakie dane są wyświetlane w widoku formantu niestandardowego i sposób wyświetlania.|
|[Element nowego wiersza dla CustomItem dla grupowania (w formacie)](./newline-element-for-customitem-for-groupby-format.md)|Element opcjonalny.<br /><br /> Dodaje pusty wiersz do wyświetlania kontrolki.|
|[Tekst elementu CustomItem dla grupowania (w formacie)](./text-element-for-customitem-for-groupby-format.md)|Element opcjonalny.<br /><br /> Określa dodatkowy tekst z danymi, wyświetlany przez kontrolkę.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CustomEntry formant niestandardowy do grupowania (w formacie)](./customentry-element-for-customcontrol-for-groupby-format.md)|Zawiera definicję widoku formantu niestandardowego.|

## <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Element CustomEntry formant niestandardowy do grupowania (w formacie)](./customentry-element-for-customcontrol-for-groupby-format.md)

[Element ExpressionBinding CustomItem dla grupowania (w formacie)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Element ramki dla CustomItem dla grupowania (w formacie)](./frame-element-for-customitem-for-groupby-format.md)

[Element nowego wiersza dla CustomItem dla grupowania (w formacie)](./newline-element-for-customitem-for-groupby-format.md)

[Tekst elementu CustomItem dla grupowania (w formacie)](./text-element-for-customitem-for-groupby-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
