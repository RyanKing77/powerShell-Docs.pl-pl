---
title: Element CustomControlName ExpressionBinding dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5242935-2782-4d23-84f5-2446b2b7ba83
caps.latest.revision: 8
ms.openlocfilehash: c9abd9f22907b87323c16d603a9f75bb3d375a03
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066638"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format"></a>CustomControlName, element — ExpressionBinding, Controls, Configuration (format)

Określa nazwę formantu wspólnego. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do konfiguracji ( Format) elementu CustomEntry formant niestandardowy dla formantów CustomItem elementu konfiguracji (Format) CustomEntry dla formantów dla konfiguracji elementu ExpressionBinding CustomItem dla kontrolki CustomControlName konfiguracji (Format) Element ExpressionBinding dla formantów dla konfiguracji (Format)

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
|[Element ExpressionBinding CustomItem dla formantów dla konfiguracji (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Definiuje dane, które jest wyświetlany przez kontrolkę.|

## <a name="text-value"></a>Wartość tekstowa

Należy określić nazwę formantu.

## <a name="remarks"></a>Uwagi

Można utworzyć wspólnych formantów, które mogą być używane przez wszystkie widoki formatowania pliku, a następnie można utworzyć kontrolki widoku, które mogą być używane przez określonego widoku. Następujące elementy określane są nazwy tych formantów:

- [Name — Element dla formantu dla formantów dla konfiguracji (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name — Element dla formantu dla formantów widoku (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Zobacz też

[Name — Element dla formantu dla formantów dla konfiguracji (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Name — Element dla formantu dla formantów widoku (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Element ExpressionBinding CustomItem dla formantów dla konfiguracji (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
