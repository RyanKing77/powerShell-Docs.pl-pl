---
title: Określa Element konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850435"
---
# <a name="controls-element-for-configuration-format"></a>Controls, element — Configuration (format)

Definiuje typowe formanty, które mogą być używane przez wszystkie widoki formatowania pliku.

Element kontrolki elementu (w formacie) konfiguracji konfiguracji (Format)

## <a name="syntax"></a>Składnia

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Controls` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Elementu formantu dla formantów dla konfiguracji (Format)](./control-element-for-controls-for-configuration-format.md)|Element wymagany.<br /><br /> Definiuje typowe formant, który może być używany przez wszystkie widoki formatowania pliku.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element konfiguracji (Format)](./configuration-element-format.md)|Reprezentuje element najwyższego poziomu w pliku formatowania.|

## <a name="remarks"></a>Uwagi

Można utworzyć dowolną liczbę wspólnych formantów. Dla każdego formantu należy określić nazwę, która jest używana do odwoływania się kontrolki i składniki formantu.

## <a name="see-also"></a>Zobacz też

[Element konfiguracji (Format)](./configuration-element-format.md)

[Elementu formantu dla formantów dla konfiguracji (Format)](./control-element-for-controls-for-configuration-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
