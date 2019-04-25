---
title: Element CustomEntry CustomEntries dla formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066451"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a>CustomEntry, element — CustomEntries, CustomControl, View (format)

Zawiera definicję widoku formantu niestandardowego.

— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy, Element (w formacie) CustomEntries Element konfiguracji dla formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries widoku (Format)

## <a name="syntax"></a>Składnia

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `CustomEntry` elementu. Należy określić elementów wyświetlanych przez definicję.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element EntrySelectedBy CustomEntry widoku (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Element opcjonalny.<br /><br /> Definiuje typy .NET, korzystających z definicji widoku kontrolkę niestandardową lub warunek, który musi istnieć, aby ta definicja ma być używany.|
|[Element CustomItem CustomEntry widoku (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Definiuje formant do zdefiniowania kontrolki niestandardowej.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CustomEntries formant niestandardowy dla widoku (Format)](./customentries-element-for-customcontrol-for-view-format.md)|Zawiera definicje widoku formantu niestandardowego. Wyświetl formant niestandardowy, należy określić co najmniej jedną definicję.|

## <a name="remarks"></a>Uwagi

W większości przypadków tylko jedną definicję, jest wymagana dla każdego widoku formant niestandardowy, ale użytkownik może mieć wielu definicji, jeśli chcesz wyświetlić różne obiekty platformy .NET przy użyciu tego samego widoku. W takich przypadkach możesz podać definicję osobne dla każdego obiektu lub grupy obiektów.

## <a name="see-also"></a>Zobacz też

[Formant niestandardowy Element widoku (Format)](./customcontrol-element-for-view-format.md)

[Element CustomItem CustomEntry widoku (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Element EntrySelectedBy CustomEntry widoku (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
