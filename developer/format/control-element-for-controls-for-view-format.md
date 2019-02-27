---
title: Kontrolowanie elementu dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845220"
---
# <a name="control-element-for-controls-for-view--format"></a>Control, element — Controls, View (format)

Definiuje formant, który może służyć przez widok i nazwę, która jest używana do odwołania kontrolki.

Element widoku elementu ViewDefinitions (Format) — Element (w formacie) konfiguracji (Format) kontrolki elementu formantu elementu (w formacie) dla formantów widoku (Format)

## <a name="syntax"></a>Składnia

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Control` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Name — Element dla kontrolki widoku (Format)](./name-element-for-control-for-controls-for-view-format.md)|Element wymagany.<br /><br /> Określa nazwę formantu.|
|[Formant niestandardowy Element dla formantu dla formantów widoku (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Element wymagany.<br /><br /> Definiuje kontrolki, używany przez ten widok.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element kontrolki (Format)](./controls-element-for-view-format.md)|Definiuje kontrolki widoku, które mogą być używane przez określonego widoku.|

## <a name="remarks"></a>Uwagi

Ten formant, można określić następujące elementy:

- [Element CustomControlName ExpressionBinding dla formantów widoku (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [Element CustomControlName ExpressionBinding dla formant niestandardowy dla widoku (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [Element CustomControlName ExpressionBinding dla grupowania (w formacie)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [Element CustomControlName GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>Zobacz też

[Formant niestandardowy Element dla formantu dla formantów widoku (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Element CustomControlName ExpressionBinding dla formantów widoku (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[Element CustomControlName ExpressionBinding dla formant niestandardowy dla widoku (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Element CustomControlName ExpressionBinding dla grupowania (w formacie)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Element CustomControlName ExpressionBinding dla grupowania (w formacie)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Element kontrolki (Format)](./controls-element-for-view-format.md)

[Name — Element dla formantu dla formantów widoku (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
