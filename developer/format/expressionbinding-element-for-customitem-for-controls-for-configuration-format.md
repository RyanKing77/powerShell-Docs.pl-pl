---
title: Element ExpressionBinding CustomItem dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065950"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a>ExpressionBinding, element — CustomItem, Controls, Configuration (format)

Definiuje dane, które jest wyświetlany przez kontrolkę. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do konfiguracji ( Format) elementu CustomEntry formant niestandardowy dla formantów CustomItem elementu konfiguracji (Format) CustomEntry dla formantów dla konfiguracji elementu ExpressionBinding CustomItem dla formantów dla konfiguracji (Format)

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
|[Element CustomControlName ExpressionBinding dla formantów dla konfiguracji (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Element opcjonalny.<br /><br /> Określa nazwę wspólne kontrolki lub kontrolki widoku.|
|[Element EnumerateCollection ExpressionBinding dla formantów dla konfiguracji (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|Element opcjonalny.<br /><br /> Określono, że elementy kolekcji są wyświetlane przez kontrolkę.|
|[Element ItemSelectionCondition ExpressionBinding dla formantów dla konfiguracji (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Element opcjonalny.<br /><br /> Określa warunek, który musi istnieć dla tego wspólnego formantu ma być używany.|
|[Element PropertyName ExpressionBinding dla formantów dla konfiguracji (Format)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Element opcjonalny.<br /><br /> Określa właściwości platformy .NET, którego wartość jest wyświetlana za pomocą wspólnej kontroli.|
|[Element ScriptBlock ExpressionBinding dla formantów dla konfiguracji (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|Element opcjonalny.<br /><br /> Określa skrypt, którego wartość jest wyświetlana za pomocą wspólnej kontroli.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CustomItem CustomEntry dla formantów dla konfiguracji](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Definiuje, jakie dane są wyświetlane w widoku formantu niestandardowego i sposób wyświetlania.|

## <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Element CustomItem CustomEntry dla formantów dla konfiguracji](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
