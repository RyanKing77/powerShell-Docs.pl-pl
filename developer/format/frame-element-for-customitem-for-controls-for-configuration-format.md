---
title: Ramkę elementu CustomItem dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065567"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>Frame, element — CustomItem, Controls, Configuration (format)

Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do konfiguracji ( Format) elementu CustomEntry formant niestandardowy dla formantów CustomItem elementu konfiguracji (Format) CustomEntry dla formantów dla konfiguracji elementu ramki CustomItem dla formantów dla konfiguracji (Format)

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
|[Element FirstLineHanging ramki dla formantów dla konfiguracji (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|Element opcjonalny.<br /><br /> Określa liczbę znaków w pierwszym wierszu danych zostanie przesunięty w lewo.|
|[Element FirstLineIndent ramki dla formantów dla konfiguracji (Format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|Element opcjonalny.<br /><br /> Określa liczbę znaków w pierwszym wierszu danych jest przesuwany w prawo.|
|[Element LeftIndent ramki dla formantów dla konfiguracji (Format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|Element opcjonalny.<br /><br /> Określa liczbę znaków od lewego marginesu zostanie przesunięty w danych.|
|[Element RightIndent ramki dla formantów dla konfiguracji (Format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|Element opcjonalny.<br /><br /> Określa liczbę znaków od prawego marginesu zostanie przesunięty w danych.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CustomItem CustomEntry dla formantów dla konfiguracji](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Definiuje, jakie dane są wyświetlane przez kontrolkę i sposób wyświetlania.|

## <a name="remarks"></a>Uwagi

Nie można określić [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) i [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elementów w tym samym `Frame` elementu.

## <a name="see-also"></a>Zobacz też

[Element FirstLineHanging ramki dla formantów dla konfiguracji (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[Element FirstLineIndent ramki dla formantów dla konfiguracji (Format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[Element LeftIndent ramki dla formantów dla konfiguracji (Format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[Element RightIndent ramki dla formantów dla konfiguracji (Format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[Element CustomItem CustomEntry dla formantów dla konfiguracji](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
