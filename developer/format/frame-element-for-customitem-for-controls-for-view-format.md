---
title: Ramkę elementu CustomItem dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065720"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>Frame, element — CustomItem, Controls, View (format)

Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu CustomItem CustomEntry dla formantów widoku (Format) elementu ramki CustomItem dla formantów widoku (Format)

## <a name="syntax"></a>Składnia

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Frame` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|`CustomItem Element`|Wymagany Element|
|[Element FirstLineHanging ramki kontrolki widoku (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|Element opcjonalny.<br /><br /> Określa, ile znaków pierwszy wiersz jest przesuwane w lewo.|
|[Element FirstLineIndent ramki kontrolki widoku (Format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|Element opcjonalny.<br /><br /> Określa, ile znaków pierwszy wiersz jest przesuwany w prawo.|
|[Element LeftIndent ramki kontrolki widoku (Format)](./leftindent-element-for-frame-for-controls-for-view-format.md)|Element opcjonalny.<br /><br /> Określa liczbę znaków od lewego marginesu zostanie przesunięty w danych.|
|[Element RightIndent ramki kontrolki widoku (Format)](./rightindent-element-for-frame-for-controls-for-view-format.md)|Element opcjonalny.<br /><br /> Określa liczbę znaków od prawego marginesu zostanie przesunięty w danych.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CustomItem CustomEntry dla formantów widoku (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Definiuje, jakie dane są wyświetlane przez kontrolkę i sposób wyświetlania.|

## <a name="remarks"></a>Uwagi

Nie można określić [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) i [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elementów w tym samym `Frame` elementu.

## <a name="see-also"></a>Zobacz też

[Element FirstLineHanging ramki kontrolki widoku (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[Element FirstLineIndent ramki kontrolki widoku (Format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[Element LeftIndent ramki kontrolki widoku (Format)](./leftindent-element-for-frame-for-controls-for-view-format.md)

[Element RightIndent ramki kontrolki widoku (Format)](./rightindent-element-for-frame-for-controls-for-view-format.md)

[Element CustomItem CustomEntry dla formantów widoku (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
