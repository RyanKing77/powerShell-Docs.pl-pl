---
title: Element EntrySelectedBy WideEntry (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066179"
---
# <a name="entryselectedby-element-for-wideentry-format"></a>EntrySelectedBy, element — WideEntry (format)

Definiuje typy .NET używających tej definicji szerokie lub warunek, który musi istnieć, aby ta definicja ma być używany.

— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) elementu WideControl (Format) WideEntries — Element (Format) WideEntry — Element (Format) EntrySelectedBy Element konfiguracji dla WideEntry (Format)

## <a name="syntax"></a>Składnia

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `EntrySelectedBy` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element SelectionCondition EntrySelectedBy dla WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Element opcjonalny.<br /><br /> Określa warunek, który musi istnieć dla tej definicji szerokie ma być używany.|
|[Element SelectionSetName EntrySelectedBy dla WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|Element opcjonalny.<br /><br /> Określa zestaw typów .NET, które używają tej definicji szerokie.|
|[Element TypeName dla EntrySelectedBy dla WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md)|Element opcjonalny.<br /><br /> Określa typ architektury .NET, która używa tej definicji szerokie.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)|Zawiera definicję szerokie.|

## <a name="remarks"></a>Uwagi

Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru dla definicji szerokie. Jest nieograniczona maksymalną liczbę elementów podrzędnych, które są dostępne.

Wybór warunki są używane do definiowania warunek, który musi istnieć dla definicji, który ma być używany, na przykład jeśli obiekt ma określoną właściwość lub wartość określoną właściwość lub wartość skryptu daje w wyniku `true`. Aby uzyskać więcej informacji o warunkach wyboru, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).

Aby uzyskać więcej informacji o innych składnikach szerokie, zobacz [tworzenia szerokiej widoku](./creating-a-wide-view.md).

## <a name="see-also"></a>Zobacz też

[Element WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)

[Element SelectionCondition EntrySelectedBy dla WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Element SelectionSetName EntrySelectedBy dla WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[Element TypeName dla EntrySelectedBy dla WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Tworzenie szerokiej widoku](./creating-a-wide-view.md)

[Definiowanie warunków do wyświetlania danych](./defining-conditions-for-displaying-data.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
