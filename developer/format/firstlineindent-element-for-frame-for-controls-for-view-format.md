---
title: Element FirstLineIndent ramki dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec63f4f9-8858-4529-8646-ffbbc278f83e
caps.latest.revision: 7
ms.openlocfilehash: 694c5baaa5e90a772257276ba139d90acf7ec0e3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845633"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-view-format"></a>FirstLineIndent, element — Frame, Controls, View (format)

Określa liczbę znaków w pierwszym wierszu danych jest przesuwany w prawo. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu CustomItem CustomEntry dla formantów widoku (Format) elementu ramki CustomItem dla formantów dla elementu FirstLineIndent widoku (Format) ramki formantów widoku (Format)

## <a name="syntax"></a>Składnia

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `FirstLineIndent` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ramki dla CustomItem dla formantów widoku (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)|Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony.|

## <a name="text-value"></a>Wartość tekstowa

Określ liczbę znaków, które mają zostać przesunięte na pierwszy wiersz danych.

## <a name="remarks"></a>Uwagi

Jeśli ten element jest określony, nie można określić [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) elementu.

## <a name="see-also"></a>Zobacz też

[Element FirstLineHanging ramki dla formantów widoku (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[Element ramki dla CustomItem dla formantów widoku (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
