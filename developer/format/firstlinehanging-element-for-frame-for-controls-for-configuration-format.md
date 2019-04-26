---
title: Element FirstLineHanging ramki dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 679c8bcb-b49d-4bb4-91f5-ea1af6c217e3
caps.latest.revision: 8
ms.openlocfilehash: 4553f95e48a2b1440c00b4951bea56376b00628a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065890"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-configuration-format"></a>FirstLineHanging, element — Frame, Controls, Configuration (format)

Określa liczbę znaków w pierwszym wierszu danych zostanie przesunięty w lewo. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do konfiguracji ( Format) elementu CustomEntry formant niestandardowy dla formantów CustomItem elementu konfiguracji (Format) CustomEntry dla formantów dla konfiguracji elementu ramki CustomItem dla formantów dla elementu FirstLineHanging konfiguracji (w formacie) dla ramki dla formantów dla konfiguracji (Format)

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
|[Element ramki dla CustomItem dla formantów dla konfiguracji (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony.|

## <a name="text-value"></a>Wartość tekstowa

Określ liczbę znaków, które mają zostać przesunięte na pierwszy wiersz danych.

## <a name="remarks"></a>Uwagi

Jeśli ten element jest określony, nie można określić `FirstLineIndent` elementu.

## <a name="see-also"></a>Zobacz też

[Element ramki dla CustomItem dla formantów dla konfiguracji (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
