---
title: Kontrolowanie elementu dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848832"
---
# <a name="control-element-for-controls-for-configuration-format"></a>Control, element — Controls, Configuration (format)

Definiuje typowe formant, który może być używany przez wszystkie widoki formatowania pliku i nazwę, która jest używana do odwołania kontrolki.

Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla konfiguracji (Format)

## <a name="syntax"></a>Składnia

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny dla `Control` elementu. Należy określić tylko jeden z każdego elementu podrzędnego.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Formant niestandardowy Element dla formantu dla formantów dla konfiguracji (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Element wymagany.<br /><br /> Definiuje kontrolki.|
|[Name — Element dla formantu konfiguracji (Format)](./name-element-for-control-for-controls-for-configuration-format.md)|Element wymagany.<br /><br /> Określa nazwę używaną do odwoływać się do kontrolki.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Kontrolki elementu konfiguracji (Format)](./controls-element-for-configuration-format.md)|Definiuje typowe formanty, które mogą być używane przez wszystkie widoki formatowania pliku lub przez inne kontrolki.|

## <a name="remarks"></a>Uwagi

Nazwa nadana tej kontrolki może znajdować się w następujących elementów:

- [Element ExpressionBinding CustomItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [GroupBy Element View(Format)](./groupby-element-for-view-format.md)

## <a name="see-also"></a>Zobacz też

[Kontrolki elementu konfiguracji (Format)](./controls-element-for-configuration-format.md)

[Element formant niestandardowy do sterowania do konfiguracji (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[Element ExpressionBinding CustomItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[GroupBy Element View(Format)](./groupby-element-for-view-format.md)

[Name — Element dla formantu dla formantów dla konfiguracji (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
