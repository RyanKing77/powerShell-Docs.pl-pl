---
title: Element TypeName dla SelectionCondition dla EntrySelectedBy dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083862"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>TypeName, element — SelectionCondition, EntrySelectedBy, ListControl (format)

Określa typ architektury .NET, która wyzwala warunku. Jeśli występuje ten typ wpisu listy jest używane.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) ListEntries Element konfiguracji elementu ListControl (Format) elementu ListEntry ListEntries elementu EntrySelectedBy elementu ListControl (Format) ListEntry elementu ListControl (Format) elementu SelectionCondition EntrySelectedBy elementu TypeName elementu ListControl (Format) SelectionCondition dla EntrySelectedBy dla elementu ListControl (Format)

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
|[Element SelectionCondition EntrySelectedBy dla elementu ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Określa warunek, który musi istnieć dla tego wpisu listy ma być używany.|

## <a name="text-value"></a>Wartość tekstowa

Określ w pełni kwalifikowaną nazwę typu .NET, taki jak `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Uwagi

Warunek wyboru można określić dowolną liczbę typów .NET lub zaznaczenie Ustawia, ale nie można określić jednocześnie. Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).

Aby uzyskać więcej informacji na temat innych części widoku listy, zobacz [tworzenia widoku listy](./creating-a-list-view.md).

## <a name="see-also"></a>Zobacz też

[Tworzenie widoku listy](./creating-a-list-view.md)

[Definiowanie warunków, gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md)

[Element SelectionCondition EntrySelectedBy dla elementu ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
