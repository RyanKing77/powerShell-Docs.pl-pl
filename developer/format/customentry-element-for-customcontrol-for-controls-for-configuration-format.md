---
title: Element CustomEntry formant niestandardowy dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849476"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a>CustomEntry, element — CustomControl, Controls, Configuration (format)

Zawiera definicję wspólnej kontroli. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do konfiguracji ( Format) elementu CustomEntry formant niestandardowy dla formantów dla konfiguracji (Format)

## <a name="syntax"></a>Składnia

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `CustomEntry` elementu. Należy określić elementów wyświetlanych przez definicję.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element EntrySelectedBy CustomEntry dla formantów dla konfiguracji (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Element opcjonalny.<br /><br /> Definiuje typy .NET, korzystających z definicji formantu typowego lub warunek, który musi istnieć dla tej kontrolki ma być używany.|
|[Element CustomItem CustomEntry dla formantów dla konfiguracji](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Element wymagany.<br /><br /> Definiuje, jakie dane są wyświetlane przez kontrolkę i sposób wyświetlania.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CustomEntries formant niestandardowy do konfiguracji (Format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|Zawiera definicje wspólnej kontroli.|

## <a name="remarks"></a>Uwagi

W większości przypadków tylko jedną definicję, jest wymagana dla poszczególnych typowych kontrolek niestandardowych, ale użytkownik może mieć wielu definicji, jeśli chcesz używać tej samej kontrolki do wyświetlania różnych obiektów platformy .NET. W takich przypadkach możesz podać definicję osobne dla każdego obiektu lub grupy obiektów.

## <a name="see-also"></a>Zobacz też

[Element CustomEntries formant niestandardowy do konfiguracji (Format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[Element CustomItem CustomEntry dla formantów dla konfiguracji](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
