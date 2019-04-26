---
title: Element CustomEntry formant niestandardowy do grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066489"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a>CustomEntry, element — CustomControl, GroupBy (format)

Zawiera definicję formantu. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy do grupowania (w formacie)

## <a name="syntax"></a>Składnia

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne `CustomEntry` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element EntrySelectedBy CustomEntry dla grupowania (w formacie)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Element opcjonalny.<br /><br /> Definiuje typy .NET, które używają tej definicji kontroli lub warunek, który musi istnieć, aby ta definicja ma być używany.|
|[Element CustomItem CustomEntry dla grupowania (w formacie)](./customitem-element-for-customentry-for-groupby-format.md)|Element wymagany.<br /><br /> Definiuje, jak kontrolka ma wyświetlać dane.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CustomEntries formant niestandardowy do grupowania (w formacie)](./customentries-element-for-customcontrol-for-groupby-format.md)|Zawiera definicje dla formantu.|

## <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Element EntrySelectedBy CustomEntry dla grupowania (w formacie)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Element CustomItem CustomEntry dla grupowania (w formacie)](./customitem-element-for-customentry-for-groupby-format.md)

[Element CustomEntries formant niestandardowy do grupowania (w formacie)](./customentries-element-for-customcontrol-for-groupby-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
