---
title: Element CustomEntries formant niestandardowy dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066587"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>CustomEntries, element — CustomControl, Controls, View (format)

Zawiera definicje dla formantu. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy dla formantów widoku (Format)

## <a name="syntax"></a>Składnia

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne `CustomEntries` elementu. Nie ma żadnego limitu maksymalną liczbę elementów podrzędnych, które można określić.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CustomEntry CustomEntries dla formantów widoku (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Element wymagany.<br /><br /> Zawiera definicję formantu.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Formant niestandardowy Element dla formantu dla formantów widoku (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Definiuje kontrolki użytej w widoku.|

## <a name="remarks"></a>Uwagi

W większości przypadków formant ma tylko jedną definicję, która jest określona w jednym `CustomEntry` elementu. Jednak jest możliwe podanie wiele definicji, jeśli chcesz używać tej samej kontrolki do wyświetlania różnych obiektów platformy .NET. W takich przypadkach można zdefiniować `CustomEntry` elementu dla każdego obiektu lub grupy obiektów.

## <a name="see-also"></a>Zobacz też

[Element CustomEntry CustomEntries dla formantów widoku (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Formant niestandardowy Element dla formantu dla formantów widoku (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
