---
title: Element CustomEntries formant niestandardowy dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066604"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a>CustomEntries, element — CustomControl, Controls, Configuration (format)

Zawiera definicje wspólnej kontroli. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do konfiguracji ( Format)

## <a name="syntax"></a>Składnia

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `CustomEntries` elementu. Należy określić jeden lub więcej elementów podrzędnych.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CustomEntry formant niestandardowy dla formantów dla konfiguracji (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Zawiera definicję wspólnej kontroli.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element formant niestandardowy do sterowania do konfiguracji (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Określa wspólną kontrolą.|

## <a name="remarks"></a>Uwagi

W większości przypadków formant ma tylko jedną definicję, która jest zdefiniowana w ramach pojedynczej `CustomEntry` elementu. Jednak użytkownik może mieć wielu definicji, jeśli chcesz używać tej samej kontrolki do wyświetlania różnych obiektów platformy .NET. W takich przypadkach można zdefiniować `CustomEntry` elementu dla każdego obiektu lub grupy obiektów.

## <a name="see-also"></a>Zobacz też

[Element formant niestandardowy do sterowania do konfiguracji (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[Element CustomEntry formant niestandardowy dla formantów dla konfiguracji (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
