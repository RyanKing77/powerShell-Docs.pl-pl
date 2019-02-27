---
title: Etykiety elementów dla elementu listy dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845955"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>Label, element — ListItem, ListControl (format)

Określa etykietę, który jest wyświetlany po lewej stronie wartości właściwości lub skryptu w wierszu.

— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) ListEntries Element konfiguracji elementu ListControl (Format) elementu ListEntry ListItems elementu ListControl (w formacie) dla ListEntry dla elementu elementu ListControl ( Element ListItem Format) dla ListItems elementu ListControl (Format) etykiety elementu ListItem dla elementu ListControl (Format)

## <a name="syntax"></a>Składnia

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Label` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ListItem ListItems dla elementu ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w wierszu w widoku listy.|

## <a name="text-value"></a>Wartość tekstowa

Określ etykietę być wyświetlana po lewej stronie wartości właściwości lub skryptu.

## <a name="remarks"></a>Uwagi

Jeśli etykieta nie zostanie określony, jest wyświetlana nazwa właściwości lub skryptu. Aby uzyskać więcej informacji na temat używania etykiet w widoku listy zobacz [tworzenia widoku listy](./creating-a-list-view.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak dodać etykietę do wiersza.

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Zobacz też

[Tworzenie widoku listy](./creating-a-list-view.md)

[ListItem — Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
