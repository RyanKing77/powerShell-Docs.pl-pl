---
title: Element SelectionSet (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850421"
---
# <a name="selectionset-element-format"></a>SelectionSet, element (format)

Definiuje zestaw obiektów platformy .NET, które mogą być przywoływane przez nazwę zestawu.

Element SelectionSet SelectionSets — Element (w formacie) — Element (w formacie) konfiguracji (Format)

## <a name="syntax"></a>Składnia

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionSet` elementu. Każdy zestaw wybór musi mieć nazwę i musi on również określać obiektów platformy .NET, zestawu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Name — Element dla SelectionSet (Format)](./name-element-for-selectionset-format.md)|Element wymagany.<br /><br /> Określa nazwę używaną do odwoływać się do zestawu wyboru.|
|[Typy elementu (w formacie)](./types-element-for-selectionset-format.md)|Element wymagany.<br /><br /> Definiuje obiekty .NET, ustawionych w zaznaczeniu.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Format elementu SelectionSets](./selectionsets-element-format.md)|Definiuje typowe rodzaje obiektów platformy .NET, które mogą być używane przez wszystkie widoki formatowania pliku.|

## <a name="remarks"></a>Uwagi

Można użyć zestawów zaznaczenie, gdy masz zestaw powiązanych obiektów, które odwołują się za pomocą jednej nazwy, takiego jak zestaw obiektów, które są powiązane z dziedziczenia. Podczas definiowania widoków, można określić zestaw obiektów przy użyciu nazwy wybór zestawu, zamiast wymieniać wszystkich obiektów w ramach każdego widoku.

Wspólne wybór zestawy są określane przez ich nazwy, podczas definiowania widoków formatowania pliku lub w definicjach widoków. W takich przypadkach `SelectionSetName` element podrzędny elementu `ViewSelectedBy` i `EntrySelectedBy` elementy określa zestaw, który ma być używany. Aby uzyskać więcej informacji na temat zestawów wybór zobacz [Definiowanie ustawia z obiektów](./defining-selection-sets.md).

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `SelectionSet` element, który definiuje cztery typy .NET.

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a>Zobacz też

[Definiowanie zestawów zaznaczenia](./defining-selection-sets.md)

[Nazwa elementu SelectionSet (Format)](./name-element-for-selectionset-format.md)

[Element SelectionSets (Format)](./selectionsets-element-format.md)

[Typy elementu (w formacie)](./types-element-for-selectionset-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
