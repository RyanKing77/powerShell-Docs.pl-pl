---
title: Element TypeName dla SelectionCondition dla EntrySelectedBy dla WideControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056011"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a>TypeName, element — SelectionCondition, EntrySelectedBy, WideControl (format)

Określa typ architektury .NET, która wyzwala warunku. Jeśli występuje ten typ definicji jest używany.

— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) WideControl — Element (Format) WideEntries — Element (Format) WideEntry — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionCondition WideEntry (Format) EntrySelectedBy WideEntry (Format) elementu TypeName SelectionCondition dla EntrySelectedBy dla WideEntry (Format)

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
|[Element SelectionCondition EntrySelectedBy dla WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Określa warunek, który musi istnieć dla tego wpisu szerokiego ma być używany.|

## <a name="text-value"></a>Wartość tekstowa

Określ w pełni kwalifikowaną nazwę typu .NET, taki jak `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Uwagi

Warunek wyboru można określić typ architektury .NET lub zaznaczenie ustawiona, ale nie można podać obydwie wartości. Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).

Aby uzyskać więcej informacji o innych składnikach szerokie, zobacz [tworzenia szerokiej widoku](./creating-a-wide-view.md).

## <a name="see-also"></a>Zobacz też

[Tworzenie szerokiej widoku](./creating-a-wide-view.md)

[Definiowanie warunków, gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md)

[Element SelectionCondition EntrySelectedBy dla WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Element SelectionSetName SelectionCondition dla EntrySelectedBy dla WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
