---
title: Element WideEntry WideControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847180"
---
# <a name="wideentry-element-for-widecontrol-format"></a>WideEntry, element — WideControl (format)

Zawiera definicję szerokie.

Konfiguracji elementu (w formacie) Element ViewDefinitions (Format) widoku elementu (w formacie) WideControl — Element (Format) elementu WideEntries (Format) WideEntry elemencie (Format)

## <a name="syntax"></a>Składnia

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `WideEntry` elementu. Należy określić pojedynczy `WideItem` elementu podrzędnego.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element EntrySelectedBy WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Element opcjonalny.<br /><br /> Definiuje typy .NET, które używają tej definicji szerokiego wpisu lub warunek, który musi istnieć, aby ta definicja ma być używany.|
|[Element WideItem (Format)](./wideitem-element-for-widecontrol-format.md)|Element wymagany.<br /><br /> Definiuje właściwości lub skryptu, którego wartość jest wyświetlana.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element WideEntries (Format)](./wideentries-element-for-widecontrol-format.md)|Zawiera definicje szerokie.|

## <a name="remarks"></a>Uwagi

Szerokie jest format listy, który wyświetla wartość właściwości jednego lub wartość skryptu dla każdego obiektu. W odróżnieniu od innych rodzajów widoków można określić tylko jeden element elementu dla każdego definicji widoku. Aby uzyskać więcej informacji o innych składnikach szerokie, zobacz [tworzenia szerokiej widoku](./creating-a-wide-view.md).

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `WideEntry` element, który definiuje pojedynczy `WideItem` elementu. `WideItem` Element definiuje właściwość, którego wartość jest wyświetlana w widoku.

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

Aby uzyskać pełny przykład szerokie, zobacz [szerokie (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Zobacz też

[Tworzenie szerokiej widoku](./creating-a-wide-view.md)

[Element SelectionCondition WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Element SelectionSetName WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[Element TypeName dla WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Element WideEntries (Format)](./wideentries-element-for-widecontrol-format.md)

[Element WideItem (Format)](./wideitem-element-for-widecontrol-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
