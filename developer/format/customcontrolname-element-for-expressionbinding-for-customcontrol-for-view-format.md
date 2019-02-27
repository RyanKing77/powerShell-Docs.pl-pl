---
title: Element CustomControlName ExpressionBinding dla formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849917"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a>CustomControlName, element — ExpressionBinding, CustomControl, View (format)

Określa nazwę wspólne kontrolki lub kontrolki widoku. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy Element konfiguracji elementu CustomEntries widoku (Format), formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla CustomItem widoku (Format) Element CustomEntry dla elementu ExpressionBinding widoku (w formacie) dla elementu CustomControlName CustomItem (w formacie) dla wyrażenia wiązania dla CustomItem (Format)

## <a name="syntax"></a>Składnia

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `CustomControlName` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ExpressionBinding CustomItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Definiuje dane, które jest wyświetlany przez kontrolkę.|

## <a name="text-value"></a>Wartość tekstowa

Należy określić nazwę formantu.

## <a name="remarks"></a>Uwagi

Można utworzyć wspólnych formantów, które mogą być używane przez wszystkie widoki formatowania pliku, a następnie można utworzyć kontrolki widoku, które mogą być używane przez określonego widoku. Nazwy te kontrolki są określone przez następujące elementy.

- [Name — Element dla formantu dla formantów dla konfiguracji (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name — Element dla formantu dla formantów widoku (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Zobacz też

[Name — Element dla formantu dla formantów dla konfiguracji (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Name — Element dla formantu dla formantów widoku (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Element ExpressionBinding CustomItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
