---
title: Element ItemSelectionCondition dla elementu listy dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850918"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a>ItemSelectionCondition, element — ListItem, ListControl (format)

Określa warunek, który musi istnieć przez ten element listy do użycia.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) ListEntries Element konfiguracji elementu ListControl (Format) elementu ListEntry ListEntries elementu ListControl (Format) elementu ListItems ListEntry dla elementu ListControl (Format) elementu ListItem ListItems elementu ListControl (Format) ItemSelectionCondition elementu ListItem dla elementu ListControl (Format)

## <a name="syntax"></a>Składnia

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ItemSelectionCondition` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element PropertyName ItemSelectionCondition dla elementu ListControl (Format)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|Element opcjonalny.<br /><br /> Określa właściwości platformy .NET, która wyzwala warunku.|
|[Element ScriptBlock ItemSelectionCondition dla elementu ListControl (Format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|Element opcjonalny.<br /><br /> Określa skrypt, który wyzwala warunku.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ListItem ListItems dla elementu ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w wierszu w widoku listy.|

## <a name="remarks"></a>Uwagi

Można określić jedną nazwę właściwości lub skrypt dla tego warunku, ale nie można określić jednocześnie.

## <a name="see-also"></a>Zobacz też

[Element ListItem ListItems dla elementu ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Element PropertyName ItemSelectionCondition dla elementu ListControl (Format)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[Element ScriptBlock ItemSelectionCondition dla elementu ListControl (Format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
