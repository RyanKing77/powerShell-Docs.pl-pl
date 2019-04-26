---
title: Element CustomEntries formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066519"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a>CustomEntries, element — CustomControl, View (format)

Zawiera definicje widoku formantu niestandardowego. Wyświetl formant niestandardowy, należy określić co najmniej jedną definicję.

— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy, Element (w formacie) CustomEntries Element konfiguracji dla formant niestandardowy dla widoku (Format)

## <a name="syntax"></a>Składnia

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `CustomControlEntries` elementu. Należy określić jeden lub więcej elementów podrzędnych.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CustomEntry CustomEntries widoku (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Element wymagany.<br /><br /> Zawiera definicję widoku formantu niestandardowego.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Formant niestandardowy Element widoku (Format)](./customcontrol-element-for-view-format.md)|Element wymagany.<br /><br /> Definiuje format formantu niestandardowego dla widoku.|

## <a name="remarks"></a>Uwagi

W większości przypadków formant ma tylko jedną definicję, która jest zdefiniowana w ramach pojedynczej `CustomEntry` elementu. Jednak użytkownik może mieć wielu definicji, jeśli chcesz używać tej samej kontrolki do wyświetlania różnych obiektów platformy .NET. W takich przypadkach można zdefiniować `CustomEntry` elementu dla każdego obiektu lub grupy obiektów.

## <a name="see-also"></a>Zobacz też

[Formant niestandardowy Element widoku (Format)](./customcontrol-element-for-view-format.md)

[Element CustomEntry CustomEntries widoku (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
