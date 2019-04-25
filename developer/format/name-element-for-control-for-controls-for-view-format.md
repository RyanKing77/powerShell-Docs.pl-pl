---
title: Nazwa elementu dla formantu dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065108"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a>Name, element — Control, Controls, View (format)

Określa nazwę formantu.

Konfiguracji elementu (w formacie) ViewDefinitions — Element (Format) widok Element (Format) kontroluje elementu formantu elementu (w formacie) dla formantów dla elementu nazwa widoku (Format) dla kontrolki widoku (Format)

## <a name="syntax"></a>Składnia

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Name` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Elementu formantu dla formantów widoku (Format)](./control-element-for-controls-for-view-format.md)|Definiuje formant, który może służyć przez widok i nazwę, która jest używana do odwołania kontrolki.|

## <a name="text-value"></a>Wartość tekstowa

Określ nazwę, która jest używana do odwołania kontrolki.

## <a name="remarks"></a>Uwagi

Nazwa określona w tym miejscu może służyć w następujących elementów można odwoływać się do tego formantu.

- Podczas tworzenia tabeli, lista, szeroki lub niestandardowe kontrolki widoku, można określić formantu przez następujący element: [GroupBy — Element dla widoku (Format)](./groupby-element-for-view-format.md)

- Podczas tworzenia inny formant, który może służyć przez widok, można określić tego formantu przez następujący element: [Element ExpressionBinding CustomItem dla formantów widoku (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Zobacz też

[GroupBy — Element dla widoku (Format)](./groupby-element-for-view-format.md)

[Element ExpressionBinding CustomItem dla formantów widoku (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Elementu formantu dla formantów widoku (Format)](./control-element-for-controls-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
