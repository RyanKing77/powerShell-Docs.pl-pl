---
title: Element CustomEntries formant niestandardowy do grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845185"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a>CustomEntries, element — CustomControl, GroupBy (format)

Zawiera definicje dla formantu. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy do grupowania (w formacie)

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
|[Element CustomEntry formant niestandardowy do grupowania (w formacie)](./customentry-element-for-customcontrol-for-groupby-format.md)|Element wymagany.<br /><br /> Zawiera definicję formantu.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element formant niestandardowy do grupowania (w formacie)](./customcontrol-element-for-groupby-format.md)|Definiuje kontrolki niestandardowej, która przedstawia nową grupę.|

## <a name="remarks"></a>Uwagi

W większości przypadków formant ma tylko jedną definicję, która jest określona w jednym `CustomEntry` elementu. Jednak jest możliwe podanie wiele definicji, jeśli chcesz używać tej samej kontrolki do wyświetlania różnych grup. W takich przypadkach można zdefiniować `CustomEntry` elementu dla grupy.

## <a name="see-also"></a>Zobacz też

[Element CustomEntry CustomEntries dla formantów widoku (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Element formant niestandardowy do grupowania (w formacie)](./customcontrol-element-for-groupby-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
