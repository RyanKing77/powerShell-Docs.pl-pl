---
title: Element ExpressionBinding CustomItem dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848419"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>ExpressionBinding, element — CustomItem, Controls, View (format)

Definiuje dane, które jest wyświetlany przez kontrolkę. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu CustomItem CustomEntry dla formantów widoku (Format) elementu ExpressionBinding CustomItem dla formantów widoku (Format)

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
|[Element CustomControlName ExpressionBinding dla formantów widoku (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|Element opcjonalny.<br /><br /> Określa nazwę wspólne kontrolki lub kontrolki widoku.|
|[Element EnumerateCollection ExpressionBinding dla formantów widoku (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|Element opcjonalny.<br /><br /> Określa, czy elementy kolekcji są wyświetlane.|
|[Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Element opcjonalny.<br /><br /> Określa warunek, który musi istnieć dla tej kontrolki ma być używany.|
|[Element PropertyName ExpressionBinding dla formantów widoku (Format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|Element opcjonalny.<br /><br /> Określa właściwości platformy .NET, którego wartość jest wyświetlany przez kontrolkę.|
|[Element ScriptBlock ExpressionBinding dla formantów widoku (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|Element opcjonalny.<br /><br /> Określa skrypt, którego wartość jest wyświetlany przez kontrolkę.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CustomItem CustomEntry dla formantów widoku (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Definiuje, jakie dane są wyświetlane przez kontrolkę i sposób wyświetlania.|

## <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Element CustomItem CustomEntry dla formantów widoku (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Element CustomControlName ExpressionBinding dla formantów widoku (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[Element EnumerateCollection ExpressionBinding dla formantów widoku (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Element PropertyName ExpressionBinding dla formantów widoku (Format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[Element ScriptBlock ExpressionBinding dla formantów widoku (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
