---
title: Element SelectionSets (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845108"
---
# <a name="selectionsets-element-format"></a>SelectionSets, element (format)

Definiuje typowe rodzaje obiektów platformy .NET, które mogą być używane przez wszystkie widoki formatowania pliku. Widoki i kontrolki formatowania pliku odwoływać kompletny zestaw obiektów za pomocą tylko nazwę zestawu wyboru.

Format elementu SelectionSets elementu konfiguracji

## <a name="syntax"></a>Składnia

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionSets` elementu. Każdy element podrzędny definiuje zestaw obiektów, które mogą być przywoływane przez nazwę zestawu. Kolejność elementów podrzędnych nie ma znaczenia.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element SelectionSet (Format)](./selectionset-element-format.md)|Element wymagany.<br /><br /> Definiuje pojedynczy zestaw obiektów platformy .NET, które mogą być przywoływane przez nazwę zestawu.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element konfiguracji](./configuration-element-format.md)|Reprezentuje element najwyższego poziomu w pliku formatowania.|

## <a name="remarks"></a>Uwagi

Można użyć zestawów zaznaczenie, gdy masz zestaw powiązanych obiektów, które odwołują się za pomocą jednej nazwy, takiego jak zestaw obiektów, które są powiązane z dziedziczenia. Podczas definiowania widoków, można określić zestaw obiektów przy użyciu nazwy wybór zestawu, zamiast wymieniać wszystkich obiektów w ramach każdego widoku.

Wspólne wybór zestawy są określane przez ich nazwy, podczas definiowania widoków formatowania pliku lub w definicjach widoków. W takich przypadkach `SelectionSetName` element podrzędny elementu `ViewSelectedBy` i `EntrySelectedBy` elementy określa zestaw, który ma być używany. Aby uzyskać więcej informacji na temat zestawów wybór zobacz [Definiowanie ustawia z obiektów](./defining-selection-sets.md).

## <a name="see-also"></a>Zobacz też

[Element konfiguracji](./configuration-element-format.md)

[Definiowanie zestawów zaznaczenia](./defining-selection-sets.md)

[Element SelectionSet (Format)](./selectionset-element-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
