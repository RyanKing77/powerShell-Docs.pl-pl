---
title: Element FirstLineIndent ramki dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33be3b9e-53c8-433f-8c11-c65b0d46744c
caps.latest.revision: 6
ms.openlocfilehash: 9ba6fc1b9924a4b0d5b56ee15290a2293217403c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065856"
---
# <a name="firstlineindent-element-for-frame-for-groupby-format"></a>FirstLineIndent, element — Frame, GroupBy (format)

Określa liczbę znaków w pierwszym wierszu danych jest przesuwany w prawo. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu CustomItem CustomEntry GroupBy (Format) elementu ramki CustomItem GroupBy (Format) elementu FirstLineIndent ramki dla grupowania (w formacie)

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
|[Element ramki dla CustomItem dla grupowania (w formacie)](./frame-element-for-customitem-for-groupby-format.md)|Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony.|

## <a name="text-value"></a>Wartość tekstowa

Określ liczbę znaków, które mają zostać przesunięte na pierwszy wiersz danych.

## <a name="remarks"></a>Uwagi

Jeśli ten element jest określony, nie można określić [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) elementu.

## <a name="see-also"></a>Zobacz też

[Element FirstLineHanging ramki dla grupowania (w formacie)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[Element ramki dla CustomItem dla grupowania (w formacie)](./frame-element-for-customitem-for-groupby-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
