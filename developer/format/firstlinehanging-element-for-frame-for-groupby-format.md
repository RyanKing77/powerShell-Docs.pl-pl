---
title: Element FirstLineHanging ramki dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cdcf66e-96a5-47b5-9269-b4330bde29f2
caps.latest.revision: 6
ms.openlocfilehash: 08db1f2d89c3fe6c1e9a5a522de3071425042c3f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065837"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a>FirstLineHanging, element — Frame, GroupBy (format)

Określa liczbę znaków w pierwszym wierszu danych zostanie przesunięty w lewo. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu CustomItem CustomEntry GroupBy (Format) elementu ramki CustomItem GroupBy (Format) elementu FirstLineHanging ramki dla grupowania (w formacie)

## <a name="syntax"></a>Składnia

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `FirstLineHanging` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ramki dla CustomItem dla grupowania (w formacie)](./frame-element-for-customitem-for-groupby-format.md)|Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony.|

## <a name="text-value"></a>Wartość tekstowa

Określ liczbę znaków, które mają zostać przesunięte na pierwszy wiersz danych.

## <a name="remarks"></a>Uwagi

Jeśli ten element jest określony, nie można określić [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elementu.

## <a name="see-also"></a>Zobacz też

[Element FirstLineIndent ramki dla grupowania (w formacie)](./firstlineindent-element-for-frame-for-groupby-format.md)

[Element ramki dla CustomItem dla grupowania (w formacie)](./frame-element-for-customitem-for-groupby-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
