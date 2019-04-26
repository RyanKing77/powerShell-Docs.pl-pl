---
title: Element FirstLineIndent ramki dla formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb4e1564-3fd3-4be3-b93e-ac90480e05c0
caps.latest.revision: 6
ms.openlocfilehash: 3130ecc69f7d1568bcbd392dd24e8cdcc3382905
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065873"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a>FirstLineIndent, element — Frame, CustomControl, View (format)

Określa liczbę znaków w pierwszym wierszu danych jest przesuwany w prawo. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy, Element (Format) CustomEntries Element konfiguracji dla formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries elementu CustomItem widoku (Format) CustomEntry CustomControlView (Format) elementu ramki CustomItem dla formant niestandardowy do elementu FirstLineIndent widoku (Format)

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
|[Element ramki dla CustomItem dla formant niestandardowy dla widoku (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony.|

## <a name="text-value"></a>Wartość tekstowa

Określ liczbę znaków, które mają zostać przesunięte na pierwszy wiersz danych.

## <a name="remarks"></a>Uwagi

Jeśli ten element jest określony, nie można określić [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) elementu.

## <a name="see-also"></a>Zobacz też

[Element FirstLineHanging ramki dla formant niestandardowy dla widoku (Format)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[Element ramki dla CustomItem dla formant niestandardowy dla widoku (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
