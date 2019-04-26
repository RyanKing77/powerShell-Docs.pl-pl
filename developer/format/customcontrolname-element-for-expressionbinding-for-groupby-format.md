---
title: Element CustomControlName ExpressionBinding dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066572"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a>CustomControlName, element — ExpressionBinding, GroupBy (format)

Określa nazwę wspólne kontrolki lub kontrolki widoku. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu CustomItem CustomEntry GroupBy (Format) elementu ExpressionBinding CustomItem GroupBy (Format) elementu CustomControlName ExpressionBinding dla grupowania (w formacie)

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
|[Element ExpressionBinding CustomItem dla grupowania (w formacie)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Definiuje dane, które jest wyświetlany przez kontrolkę.|

## <a name="text-value"></a>Wartość tekstowa

Należy określić nazwę formantu.

## <a name="remarks"></a>Uwagi

Można utworzyć wspólnych formantów, które mogą być używane przez wszystkie widoki formatowania pliku, a następnie można utworzyć kontrolki widoku, które mogą być używane przez określonego widoku. Następujące elementy określane są nazwy tych formantów:

- [Name — Element dla formantu dla formantów dla konfiguracji (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name — Element dla formantu dla formantów widoku (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Zobacz też

[Name — Element dla formantu dla formantów dla konfiguracji (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Name — Element dla formantu dla formantów widoku (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Element ExpressionBinding CustomItem dla grupowania (w formacie)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
