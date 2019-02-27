---
title: Element SelectionCondition EntrySelectedBy dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845514"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a>SelectionCondition, element — EntrySelectedBy, Controls, Configuration (format)

Określa warunek, który musi istnieć do wspólnej definicji kontrolki ma być używany. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do kontrolki Element CustomEntry konfiguracji (w formacie) dla formant niestandardowy dla formantów EntrySelectedBy elementu konfiguracji (Format) CustomEntry dla formantów SelectionCondition elementu konfiguracji (Format) EntrySelectedBy dla CustomEntry dla Konfiguracja (Format)

## <a name="syntax"></a>Składnia

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionCondition` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element PropertyName SelectionCondition dla formantów dla konfiguracji (Format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Element opcjonalny.<br /><br /> Określa właściwości platformy .NET, która wyzwala warunku.|
|[Element ScriptBlock SelectionCondition dla formantów dla konfiguracji (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|Element opcjonalny.<br /><br /> Określa skrypt, który wyzwala warunku.|
|[Element SelectionSetName SelectionCondition dla formantów dla konfiguracji (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Element opcjonalny.<br /><br /> Określa zestaw typów .NET wyzwalającego warunku.|
|[Element TypeName dla SelectionCondition dla formantów dla konfiguracji (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|Element opcjonalny.<br /><br /> Określa typ architektury .NET, która wyzwala warunku.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element EntrySelectedBy CustomEntry dla formantów dla konfiguracji (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Definiuje typy .NET, korzystających z tego wpisu wspólnej definicji kontroli.|

## <a name="remarks"></a>Uwagi

Podczas definiowania warunek wyboru należy przestrzegać następujących wytycznych:

- Warunek wyboru należy określić co najmniej jednej nazwy właściwości lub blok skryptu, ale nie można określić jednocześnie.

- Warunek wyboru można określić dowolną liczbę typów .NET lub zaznaczenie Ustawia, ale nie można określić jednocześnie.

Aby uzyskać więcej informacji o używaniu wybór warunków, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Zobacz też

[Element PropertyName SelectionCondition dla formantów dla konfiguracji (Format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Element ScriptBlock SelectionCondition dla formantów dla konfiguracji (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Element SelectionSetName SelectionCondition dla formantów dla konfiguracji (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Element TypeName dla SelectionCondition dla formantów dla konfiguracji (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Element EntrySelectedBy CustomEntry dla formantów dla konfiguracji (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[Pisanie programu Windows PowerShell, formatowania i typy plików](./writing-a-powershell-formatting-file.md)
