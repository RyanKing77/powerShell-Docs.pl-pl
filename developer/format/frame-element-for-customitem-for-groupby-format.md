---
title: Ramkę elementu CustomItem dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065601"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a>Frame, element — CustomItem, GroupBy (format)

Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu CustomItem CustomEntry GroupBy (Format) elementu ramki CustomItem dla grupowania (w formacie)

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
|[Element FirstLineHanging ramki dla grupowania (w formacie)](./firstlinehanging-element-for-frame-for-groupby-format.md)|Element opcjonalny.<br /><br /> Określa liczbę znaków w pierwszym wierszu danych zostanie przesunięty w lewo.|
|[Element FirstLineIndent ramki dla grupowania (w formacie)](./firstlineindent-element-for-frame-for-groupby-format.md)|Element opcjonalny.<br /><br /> Określa liczbę znaków w pierwszym wierszu danych jest przesuwany w prawo.|
|[Element LeftIndent ramki dla grupowania (w formacie)](./leftindent-element-for-frame-for-groupby-format.md)|Element opcjonalny.<br /><br /> Określa liczbę znaków od lewego marginesu zostanie przesunięty w danych.|
|[Element RightIndent ramki dla grupowania (w formacie)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent — Element|Element opcjonalny.<br /><br /> Określa liczbę znaków od prawego marginesu zostanie przesunięty w danych.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CustomItem CustomEntry dla grupowania (w formacie)](./customitem-element-for-customentry-for-groupby-format.md)|Definiuje, jakie dane są wyświetlane przez kontrolkę i sposób wyświetlania.|

## <a name="remarks"></a>Uwagi

Nie można określić [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) i [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elementów w tym samym `Frame` elementu.

## <a name="see-also"></a>Zobacz też

[Element FirstLineHanging ramki dla grupowania (w formacie)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[Element FirstLineIndent ramki dla grupowania (w formacie)](./firstlineindent-element-for-frame-for-groupby-format.md)

[Element LeftIndent ramki dla grupowania (w formacie)](./leftindent-element-for-frame-for-groupby-format.md)

[Element RightIndent ramki dla grupowania (w formacie)](./rightindent-element-for-frame-for-groupby-format.md)

[Element CustomItem CustomEntry dla grupowania (w formacie)](./customitem-element-for-customentry-for-groupby-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
