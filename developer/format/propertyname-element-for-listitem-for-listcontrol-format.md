---
title: Element PropertyName dla elementu listy dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064921"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a>PropertyName, element — ListItem, ListControl (format)

Określa właściwości platformy .NET, którego wartość jest wyświetlana na liście.

— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) elementu ListEntries (Format) ListEntry — Element (Format) ListItems — Element (Format) Element ListItem (Format) PropertyName Element konfiguracji dla ListItem (Format)

## <a name="syntax"></a>Składnia

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `PropertyName` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[ListItem — Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w wierszu w widoku listy.|

## <a name="text-value"></a>Wartość tekstowa

Określ nazwę właściwości, którego wartość jest wyświetlana.

## <a name="remarks"></a>Uwagi

Gdy ten element jest określony, nie można określić [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elementu.

Oprócz wyświetlania wartości właściwości, można również określić etykietę dla wartość lub ciąg formatu, który może służyć do zmienić sposób wyświetlania wartości. Aby uzyskać więcej informacji na temat określania danych w widoku listy, zobacz [tworzenia widoku listy](./creating-a-list-view.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak określić etykietę i właściwości, którego wartość jest wyświetlana.

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Zobacz też

[Element ScriptBlock dla elementu listy dla elementu ListControl (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Tworzenie widoku listy](./creating-a-list-view.md)

[ListItem Element ListControl(Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
