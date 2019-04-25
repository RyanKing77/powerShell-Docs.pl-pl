---
title: Element WideItem WideControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083641"
---
# <a name="wideitem-element-for-widecontrol-format"></a>WideItem, element — WideControl (format)

Definiuje właściwości lub skryptu, którego wartość jest wyświetlana.

— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) WideControl — Element (Format) elementu WideEntries (Format) WideEntry — Element (Format) WideItem Element konfiguracji (Format)

## <a name="syntax"></a>Składnia

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `WideItem` elementu. `FormatString` Element jest opcjonalne. Jednakże, należy określić `PropertyName` lub `ScriptBlock` element, ale nie można określić jednocześnie.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element FormatString dla WideItem dla WideControl (Format)](./formatstring-element-for-wideitem-for-widecontrol-format.md)|Element opcjonalny.<br /><br /> Określa wzorzec formatu, który definiuje sposób wyświetlania wartości właściwości lub skryptu w widoku.|
|[Element PropertyName WideItem (Format)](./propertyname-element-for-wideitem-for-widecontrol-format.md)|Określa właściwość obiektu, którego wartość jest wyświetlana w szerokim oknie.|
|[Element ScriptBlock WideItem (Format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|Określa skrypt, którego wartość jest wyświetlana w szerokim oknie.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)|Zawiera definicję szerokie.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat składników szerokie, zobacz [szerokie](./creating-a-wide-view.md).

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `WideEntry` element, który definiuje pojedynczy `WideItem` elementu. `WideItem` Element definiuje właściwość lub skryptu, którego wartość jest wyświetlana w widoku.

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

Aby uzyskać pełny przykład szerokie, zobacz [szerokie (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Zobacz też

[Element FormatString dla WideItem dla WideControl (Format)](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[Element PropertyName WideItem (Format)](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[Element ScriptBlock WideItem (Format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[Element WideEntry (Format)](./wideentry-element-for-widecontrol-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
