---
title: Element ListItems ListEntry dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065244"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>ListItems, element — ListEntry, ListControl (format)

Definiuje właściwości i skrypty, których wartości są wyświetlane w wierszach widoku listy.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) ListEntries Element konfiguracji dla elementu ListEntry List kontroli (w formacie) dla elementu ListItems elementu ListControl (w formacie) dla elementu ListControl (Format)

## <a name="syntax"></a>Składnia

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ListItems` elementu. Nie ma żadnego limitu liczby elementów podrzędnych, które można określić. Kolejność elementów podrzędnych definiuje kolejność wyświetlania wartości w widoku listy.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ListItem dla elementu ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Element wymagany.<br /><br /> Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w widoku listy.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ListEntry dla elementu ListControl (Format)](./listentry-element-for-listcontrol-format.md)|Zawiera definicję widoku listy.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat tego typu widoku, zobacz [tworzenia widoku listy](./creating-a-list-view.md).

## <a name="example"></a>Przykład

Ten przykład pokazuje elementy XML, które określają trzy wiersze w widoku listy.

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a>Zobacz też

[Element ListEntry dla elementu ListControl (Format)](./listentry-element-for-listcontrol-format.md)

[Element ListItem dla elementu ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Tworzenie widoku listy](./creating-a-list-view.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
