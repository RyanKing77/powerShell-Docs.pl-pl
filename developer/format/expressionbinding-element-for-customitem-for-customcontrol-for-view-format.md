---
title: Element ExpressionBinding CustomItem dla formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850092"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>ExpressionBinding, element — CustomItem, CustomControl, View (format)

Definiuje dane, które jest wyświetlany przez kontrolkę. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy Element konfiguracji elementu CustomEntries widoku (Format), formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formant niestandardowy do widoku ( Format) elementu CustomItem CustomEntry dla formant niestandardowy widok (w formacie) elementu ExpressionBinding CustomItem dla formant niestandardowy dla widoku (Format)

## <a name="syntax"></a>Składnia

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ExpressionBinding` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|`CustomControl Element`|Element opcjonalny.<br /><br /> Definiuje formant, który jest używany przez tę kontrolkę.|
|[Element CustomControlName ExpressionBinding dla formant niestandardowy dla widoku (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Element opcjonalny.<br /><br /> Określa nazwę wspólne kontrolki lub kontrolki widoku.|
|[Element EnumerateCollection ExpressionBinding dla formant niestandardowy dla widoku (Format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Element opcjonalny.<br /><br /> Określono, że elementy kolekcji są wyświetlane.|
|[Element ItemSelectionCondition ExpressionBinding dla formant niestandardowy dla widoku (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Element opcjonalny.<br /><br /> Określa warunek, który musi istnieć dla tej kontrolki ma być używany.|
|[Element PropertyName ExpressionBinding dla formant niestandardowy dla widoku (Format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Element opcjonalny.<br /><br /> Określa właściwości platformy .NET, którego wartość jest wyświetlany przez kontrolkę.|
|[Element ScriptBlock ExpressionBinding dla CustomCustomControl widoku (Format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Element opcjonalny.<br /><br /> Określa skrypt, którego wartość jest wyświetlany przez kontrolkę.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CustomItem CustomEntry dla formant niestandardowy dla widoku (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Definiuje, jakie dane są wyświetlane w widoku formantu niestandardowego i sposób wyświetlania.|

## <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Element CustomControlName ExpressionBinding dla formant niestandardowy dla widoku (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Element EnumerateCollection ExpressionBinding dla formant niestandardowy dla widoku (Format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Element ItemSelectionCondition ExpressionBinding dla formant niestandardowy dla widoku (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Element PropertyName ExpressionBinding dla formant niestandardowy dla widoku (Format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Element ScriptBlock ExpressionBinding dla formant niestandardowy dla widoku (Format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Element CustomItem CustomEntry dla formant niestandardowy dla widoku (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
