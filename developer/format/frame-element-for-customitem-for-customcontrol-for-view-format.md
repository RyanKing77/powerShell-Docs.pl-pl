---
title: Ramkę elementu dla CustomItem formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065584"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a>Frame, element — CustomItem, CustomControl, View (format)

Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy, Element (Format) CustomEntries Element konfiguracji dla formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries elementu CustomItem widoku (Format) CustomEntry CustomControlView (Format) elementu ramki CustomItem dla formant niestandardowy dla widoku (Format)

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
|[FirstLineHanging Element](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|Element opcjonalny.<br /><br /> Określa liczbę znaków w pierwszym wierszu danych zostanie przesunięty w lewo.|
|[FirstLineIndent Element](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|Element opcjonalny.<br /><br /> Określa liczbę znaków w pierwszym wierszu danych jest przesuwany w prawo.|
|[LeftIndent Element](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|Element opcjonalny.<br /><br /> Określa liczbę znaków od lewego marginesu zostanie przesunięty w danych.|
|[RightIndent Element](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|Element opcjonalny.<br /><br /> Określa liczbę znaków od prawego marginesu zostanie przesunięty w danych.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CustomItem CustomEntry widoku (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Definiuje, jakie dane są wyświetlane przez kontrolkę i sposób wyświetlania.|

## <a name="remarks"></a>Uwagi

Nie można określić [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) i [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elementów w tym samym `Frame` elementu.

## <a name="see-also"></a>Zobacz też

[FirstLineHanging Element](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[FirstLineIndent Element](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[LeftIndent Element](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[RightIndent Element](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[Element CustomItem CustomEntry widoku (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
