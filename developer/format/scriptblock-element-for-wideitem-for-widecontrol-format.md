---
title: Element ScriptBlock WideItem dla WideControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848230"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>ScriptBlock, element — WideItem, WideControl (format)

Określa skrypt, którego wartość jest wyświetlana w szerokim oknie.

— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) WideControl — Element (Format) WideEntries — Element (Format) elementu WideEntry (Format) WideItem — Element (Format) ScriptBlock Element konfiguracji dla WideItem (Format)

## <a name="syntax"></a>Składnia

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
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
|[Element WideItem (Format)](./wideitem-element-for-widecontrol-format.md)|Definiuje właściwości lub skrypt bloku, którego wartość jest wyświetlana w szerokim oknie.|

## <a name="text-value"></a>Wartość tekstowa

Określ skrypt, którego wartość jest wyświetlana.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat składników szerokie, zobacz [tworzenia szerokiej widoku](./creating-a-wide-view.md).

## <a name="example"></a>Przykład

W tym przykładzie `WideItem` element, który definiuje skryptu, którego wartość jest wyświetlana w widoku.

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>Zobacz też

[Element WideItem (Format)](./wideitem-element-for-widecontrol-format.md)

[Tworzenie szerokiej widoku](./creating-a-wide-view.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
