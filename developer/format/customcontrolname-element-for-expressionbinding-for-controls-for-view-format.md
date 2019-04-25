---
title: Element CustomControlName ExpressionBinding dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066655"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a>CustomControlName, element — ExpressionBinding, Controls, View (format)

Określa nazwę wspólne kontrolki lub kontrolki widoku. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu CustomItem CustomEntry dla formantów widoku (Format) elementu ExpressionBinding CustomItem dla kontrolki CustomControlName widoku (Format) Element ExpressionBindine dla formantów widoku (Format)

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
|[Element ExpressionBinding CustomItem dla formantów widoku (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Definiuje dane, które jest wyświetlany przez kontrolkę.|

## <a name="text-value"></a>Wartość tekstowa

Należy określić nazwę formantu.

## <a name="remarks"></a>Uwagi

Można utworzyć wspólnych formantów, które mogą być używane przez wszystkie widoki formatowania pliku, a następnie można utworzyć kontrolki widoku, które mogą być używane przez określonego widoku. Następujące elementy określane są nazwy tych formantów:

- [Name — Element dla formantu dla formantów dla konfiguracji (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name — Element dla formantu dla formantów widoku (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Zobacz też

[Name — Element dla formantu dla formantów dla konfiguracji (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Name — Element dla formantu dla formantów widoku (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Element ExpressionBinding CustomItem dla formantów widoku (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
