---
title: Element ScriptBlock dla elementu listy dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064581"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>ScriptBlock, element — ListItem, ListControl (format)

Określa skrypt, którego wartość jest wyświetlana w wierszu.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) ListEntries Element konfiguracji elementu ListControl (Format) elementu ListEntry ListEntries elementu ListControl (Format) elementu ListItems ListEntry dla elementu ListControl (Format) elementu ListItem ListItems elementu ListControl (Format) ScriptBlock elementu ListItem dla elementu ListControl (Format)

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
|[ListItem — Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w wierszu w widoku listy.|

## <a name="text-value"></a>Wartość tekstowa

Określ skrypt, którego wartość jest wyświetlana w wierszu.

## <a name="remarks"></a>Uwagi

Gdy ten element jest określony, nie można określić [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elementu.

Aby uzyskać więcej informacji na temat określania skryptów w widoku listy, zobacz [widok listy](./creating-a-list-view.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób określania właściwości, którego wartość jest wyświetlana.

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a>Zobacz też

[Element PropertyName dla elementu listy dla elementu ListControl (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Tworzenie widoku listy](./creating-a-list-view.md)

[Element ListItem ListItems dla elementu ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
