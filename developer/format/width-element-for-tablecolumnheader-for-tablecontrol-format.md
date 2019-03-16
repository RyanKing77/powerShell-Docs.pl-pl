---
title: Szerokość elementu TableColumnHeader dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055193"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>Width, element — TableColumnHeader, TableControl (format)

Określa szerokość (w znakach) kolumny.

— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) tablecontrol — Element (Format) TableHeaders Element konfiguracji dla TableHeaders elementu TableColumnHeader tablecontrol — (w formacie) dla elementu szerokość (w formacie) tablecontrol — TableColumnHeader dla tablecontrol — (w formacie)

## <a name="syntax"></a>Składnia

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Width` element używany podczas definiowania nagłówków kolumn.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element TableColumnHeader TableHeaders dla tablecontrol — (w formacie)](./tablecolumnheader-element-format.md)|Definiuje etykietę, szerokości i wyrównania danych dla kolumny tabeli.|

## <a name="text-value"></a>Wartość tekstowa

Gdy na wszystkich możliwych określić szerokość (w znakach), która jest większa niż długość wartości właściwości wyświetlanych.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `TableColumnHeader` elementu, którego szerokość jest 16 znaków.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Zobacz też

[Tworzenie widoku tabeli](./creating-a-table-view.md)

[Element TableColumnHeader TableHeader dla tablecontrol — (w formacie)](./tablecolumnheader-element-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
