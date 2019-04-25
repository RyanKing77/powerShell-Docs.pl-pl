---
title: Element TypeName dla EntrySelectedBy dla CustomEntry widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083981"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a>TypeName, element — EntrySelectedBy, CustomEntry, View (format)

Określa typ architektury .NET, który używa tej definicji widoku formantu niestandardowego. Nie ma żadnego limitu liczby typów, które można określić dla definicji.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy, Element (Format) CustomEntries Element konfiguracji dla formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla EntrySelectedBy widoku (Format) Element CustomEntry widoku (Format) elementu TypeName EntrySelectedBy dla CustomEntry widoku (Format)

## <a name="syntax"></a>Składnia

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TypeName` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element EntrySelectedBy CustomEntry widoku (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Definiuje typy .NET, używające tej kontrolki niestandardowej definicji widoku lub warunek, który musi istnieć, aby ta definicja ma być używany.|

## <a name="text-value"></a>Wartość tekstowa

Określ w pełni kwalifikowaną nazwę typu .NET, taki jak `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Uwagi

Każda definicja widoku formantu niestandardowego musi mieć co najmniej jedną nazwę typu, wybór zestawu lub warunek wyboru.

Aby uzyskać więcej informacji o składnikach widoku kontrolki niestandardowej, zobacz [Tworzenie niestandardowych formantów](./creating-custom-controls.md).

## <a name="see-also"></a>Zobacz też

[Tworzenie niestandardowych formantów](./creating-custom-controls.md)

[Element EntrySelectedBy CustomEntry widoku (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
