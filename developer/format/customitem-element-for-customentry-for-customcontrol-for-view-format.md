---
title: Element CustomItem CustomEntry dla formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066417"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>CustomItem, element — CustomEntry, CustomControl, View (format)

Definiuje, jakie dane są wyświetlane w widoku formantu niestandardowego i sposób wyświetlania. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy, Element (Format) CustomEntries Element konfiguracji dla formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries elementu CustomItem widoku (Format) CustomEntry widoku (Format)

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
|[Element ExpressionBinding CustomItem dla formant niestandardowy dla widoku (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Element opcjonalny.<br /><br /> Definiuje dane, które jest wyświetlany przez kontrolkę.|
|[Element ramki dla CustomItem dla formant niestandardowy dla widoku (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Element opcjonalny.<br /><br /> Definiuje, jakie dane są wyświetlane w widoku formantu niestandardowego i sposób wyświetlania.|
|[Element nowego wiersza dla CustomItem dla formantu niestandardowego dla widoku (Format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|Element opcjonalny.<br /><br /> Dodaje pusty wiersz do wyświetlania kontrolki.|
|[Tekst elementu CustomItem dla formant niestandardowy dla widoku (Format)](./text-element-for-customitem-for-customview-for-view-format.md)|Element opcjonalny.<br /><br /> Określa dodatkowy tekst z danymi, wyświetlany przez kontrolkę.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CustomEntry CustomEntries dla formant niestandardowy dla widoku (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Zawiera definicję widoku formantu niestandardowego.|

## <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Element CustomEntry CustomEntries widoku (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Element ExpressionBinding CustomItem dla formant niestandardowy dla widoku (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[Element ramki dla CustomItem dla formant niestandardowy dla widoku (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Element nowego wiersza dla CustomItem dla formant niestandardowy dla widoku (Format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[Tekst elementu CustomItem dla formant niestandardowy dla widoku (Format)](./text-element-for-customitem-for-customview-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
