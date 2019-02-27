---
title: Element ListItem ListItems dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846221"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>ListItem, element — ListItems, ListControl (format)

Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w wierszu w widoku listy.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) ListEntries Element konfiguracji dla elementu ListEntry elementu ListControl (w formacie) dla elementu ListItems elementu ListControl (w formacie) dla elementu ListControl (Format) ListItem dla elementu elementu ListControl (Format)

## <a name="syntax"></a>Składnia

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ListItem` elementu. Można określić tylko jedną właściwość lub skryptu.

### <a name="attributes"></a>Atrybuty

Brak

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element FormatString dla elementu listy dla elementu ListControl (Format)](./formatstring-element-for-listitem-for-listcontrol-format.md)|Element opcjonalny.<br /><br /> Określa ciąg formatu, który definiuje sposób wyświetlania wartości właściwości lub skryptu.|
|[Element ItemSelectionCondition dla elementu listy dla elementu ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Element opcjonalny.<br /><br /> Określa warunek, który musi istnieć przez ten element listy do użycia.|
|[Element LABEL dla elementu listy dla elementu ListControl (Format)](./label-element-for-listitem-for-listcontrol-format.md)|Opcjonalny element<br /><br /> Określa etykietę, który jest wyświetlany po lewej stronie wartości właściwości lub skryptu w wierszu.|
|[Element PropertyName dla elementu listy dla elementu ListControl (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md)|Element opcjonalny.<br /><br /> Określa właściwości platformy .NET, którego wartość jest wyświetlana w wierszu.|
|[Element ScriptBlock dla elementu listy dla elementu ListControl (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)|Element opcjonalny.<br /><br /> Określa skrypt, którego wartość jest wyświetlana w wierszu.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ListItems dla kontrolki listy (Format)](./listitems-element-for-listentry-for-listcontrol-format.md)|Definiuje właściwości i skrypty, których wartości są wyświetlane w widoku listy.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji o składnikach w widoku listy, zobacz [tworzenia widoku listy](./creating-a-list-view.md).

## <a name="example"></a>Przykład

Ten przykład pokazuje elementy XML, które określają trzy wiersze w widoku listy. Pierwsze dwa wiersze wyświetlić wartość właściwości platformy .NET, a ostatni wiersz wyświetla wartość wygenerowaną przez skrypt.

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a>Zobacz też

[Element ListItems (Format)](./listitems-element-for-listentry-for-listcontrol-format.md)

[Element FormatString dla elementu listy (Format)](./formatstring-element-for-listitem-for-listcontrol-format.md)

[Etykieta elementu ListItem (Format)](./label-element-for-listitem-for-listcontrol-format.md)

[PropertyName Element ListItem (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Blok skryptu Element ListItem (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Tworzenie widoku listy](./creating-a-list-view.md)

[Pisanie programu Windows PowerShell, formatowania i typy plików](./writing-a-powershell-formatting-file.md)
