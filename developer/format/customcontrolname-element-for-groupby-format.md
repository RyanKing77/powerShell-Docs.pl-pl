---
title: Element CustomControlName GroupBy (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849826"
---
# <a name="customcontrolname-element-for-groupby-format"></a>CustomControlName, element — GroupBy (format)

Określa nazwę kontrolki niestandardowej, która jest używana do wyświetlania nowej grupy. Ten element jest używany podczas definiowania tabel, list, szeroki lub niestandardowe kontrolki widoku.

— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu CustomControlName widoku (Format) GroupBy (Format)

## <a name="syntax"></a>Składnia

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W następujących sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne `CustomControlName` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[GroupBy — Element dla widoku (Format)](./groupby-element-for-view-format.md)|Definiuje, jak środowiska Windows PowerShell wyświetla nowe grupy obiektów.|

## <a name="text-value"></a>Wartość tekstowa

Określ nazwę kontrolki niestandardowej, która jest używana do wyświetlania nowej grupy.

## <a name="remarks"></a>Uwagi

Można utworzyć wspólnych formantów, które mogą być używane przez wszystkie widoki formatowania pliku, a następnie można utworzyć kontrolki widoku, które mogą być używane przez określonego widoku. Następujące elementy określane są nazwy tych kontrolek niestandardowych:

- [Name — Element dla formantu dla formantów dla konfiguracji (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name — Element dla formantu dla formantów widoku (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Zobacz też

[GroupBy — Element dla widoku (Format)](./groupby-element-for-view-format.md)

[Name — Element dla formantu dla formantów dla konfiguracji (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Name — Element dla formantu dla formantów widoku (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
