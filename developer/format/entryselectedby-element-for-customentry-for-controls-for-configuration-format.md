---
title: Element EntrySelectedBy CustomEntry dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: e930e4422afd203feda6a389655ff8a355e3bec0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848678"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>EntrySelectedBy, element — CustomEntry, Controls, Configuration (format)

Definiuje typy .NET, korzystających z definicji formantu typowego lub warunek, który musi istnieć dla tej kontrolki ma być używany. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do konfiguracji ( Format) elementu CustomEntry formant niestandardowy dla formantów EntrySelectedBy elementu konfiguracji (Format) CustomEntry dla formantów dla konfiguracji (Format)

## <a name="syntax"></a>Składnia

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `EntrySelectedBy` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element SelectionCondition EntrySelectedBy dla formantów dla konfiguracji (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Element opcjonalny.<br /><br /> Określa warunek, który musi istnieć przez wspólnej definicji kontrolki ma być używany.|
|[Element SelectionSetName EntrySelectedBy dla formantów dla konfiguracji (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Element opcjonalny.<br /><br /> Określa zestaw typów .NET, korzystających z tej definicji wspólnej kontroli.|
|[Element TypeName dla EntrySelectedBy dla formantów dla konfiguracji (Format)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|Element opcjonalny.<br /><br /> Określa typ architektury .NET, który używa tej definicji wspólnej kontroli.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CustomEntry formant niestandardowy dla formantów dla konfiguracji (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Zawiera definicję wspólnej kontroli.|

## <a name="remarks"></a>Uwagi

Jako minimum Każda definicja musi mieć co najmniej jeden typ .NET, zestawu wyboru lub wyboru warunek określony. Nie ma żadnych maksymalny limit liczby typów, ustawia zaznaczenie lub zaznaczenie warunki, które można określić.

## <a name="see-also"></a>Zobacz też

[Element SelectionCondition EntrySelectedBy dla formantów dla konfiguracji (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Element SelectionSetName EntrySelectedBy dla formantów dla konfiguracji (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Element CustomEntry formant niestandardowy dla formantów dla konfiguracji (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Element TypeName dla EntrySelectdBy dla formantów dla konfiguracji (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
