---
title: Element ExpressionBinding CustomItem dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846060"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>ExpressionBinding, element — CustomItem, GroupBy (format)

Definiuje dane, które jest wyświetlany przez kontrolkę. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu CustomItem CustomEntry GroupBy (Format) elementu ExpressionBinding CustomItem dla grupowania (w formacie)

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
|[Element CustomControlName ExpressionBinding dla grupowania (w formacie)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|Element opcjonalny.<br /><br /> Określa nazwę wspólne kontrolki lub kontrolki widoku.|
|[Element EnumerateCollection ExpressionBinding dla grupowania (w formacie)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection elementu ExpressionBinding dla grupowania (w formacie)|Element opcjonalny.<br /><br /> Określono, że elementy kolekcji są wyświetlane.|
|[Element ItemSelectionCondition ExpressionBinding dla grupowania (w formacie)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Element opcjonalny.<br /><br /> Określa warunek, który musi istnieć dla tej kontrolki ma być używany.|
|[Element PropertyName ExpressionBinding dla grupowania (w formacie)](./propertyname-element-for-expressionbinding-for-groupby-format.md)|Element opcjonalny.<br /><br /> Określa właściwości platformy .NET, którego wartość jest wyświetlany przez kontrolkę.|
|[Element ScriptBlock ExpressionBinding dla grupowania (w formacie)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|Element opcjonalny.<br /><br /> Określa skrypt, którego wartość jest wyświetlany przez kontrolkę.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CustomItem CustomEntry dla grupowania (w formacie)](./customitem-element-for-customentry-for-groupby-format.md)|Definiuje, jakie dane są wyświetlane w widoku formantu niestandardowego i sposób wyświetlania.|

## <a name="see-also"></a>Zobacz też

[Element CustomControlName ExpressionBinding dla grupowania (w formacie)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Element EnumerateCollection ExpressionBinding dla grupowania (w formacie)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[Element ItemSelectionCondition ExpressionBinding dla grupowania (w formacie)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Element PropertyName ExpressionBinding dla grupowania (w formacie)](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[Element ScriptBlock ExpressionBinding dla grupowania (w formacie)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[Element CustomItem CustomEntry dla grupowania (w formacie)](./customitem-element-for-customentry-for-groupby-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
