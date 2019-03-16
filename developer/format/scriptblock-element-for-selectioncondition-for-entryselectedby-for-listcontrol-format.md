---
title: Element ScriptBlock SelectionCondition dla EntrySelectedBy dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: b65d953169f6daf15fb617ce4d0303cf4cb584ee
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057777"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>ScriptBlock, element — SelectionCondition, EntrySelectedBy, ListControl (format)

Określa skrypt, który wyzwala warunku. Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i wpis na liście jest używany.

— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) elementu ListEntries (Format) ListEntry — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionCondition ListEntry (Format) EntrySelectedBy ListEntry (Format) elementu ScriptBlock SelectionCondition dla EntrySelectedBy dla ListEntry (Format)

## <a name="syntax"></a>Składnia

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ScriptBlock` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element SelectionCondition EntrySelectedBy dla ListEntry (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Określa warunek, który musi istnieć dla tego wpisu listy ma być używany.|

## <a name="text-value"></a>Wartość tekstowa

Określ skrypt, który jest oceniany.

## <a name="remarks"></a>Uwagi

Warunek wyboru należy określić co najmniej jedną nazwę skryptu lub właściwości do oceny, ale nie można podać obydwie wartości. (Aby uzyskać więcej informacji o używaniu wybór warunków, zobacz [definiujący warunki dla, gdy wpis widoku lub służy element](./defining-conditions-for-displaying-data.md).)

Aby uzyskać więcej informacji o innych składnikach widoku listy, zobacz [widok listy](./creating-a-list-view.md).

## <a name="see-also"></a>Zobacz też

[Element ListEntry (Format)](./listentry-element-for-listcontrol-format.md)

[Element PropertyName SelectionCondition dla EntrySelectedBy dla ListEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[Element SelectionCondition EntrySelectedBy dla ListEntry (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Widok listy](./creating-a-list-view.md)

[Definiowanie warunki, gdy jest używany widok wpisu lub elementu](./defining-conditions-for-displaying-data.md)

[Pisanie programu Windows PowerShell, formatowania i typy plików](./writing-a-powershell-formatting-file.md)
