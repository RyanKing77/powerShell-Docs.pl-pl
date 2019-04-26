---
title: Nazwa elementu dla SelectionSet (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065159"
---
# <a name="name-element-for-selectionset-format"></a>Name, element — SelectionSet (format)

Określa nazwę używaną do odwoływać się do zestawu wyboru.

Konfiguracji elementu (w formacie) elementu SelectionSets (Format) elementu SelectionSet (Format) nazwa elementu SelectionSet (Format)

## <a name="syntax"></a>Składnia

```xml
<Name>Name of selection set</Name>
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
|[Element SelectionSet (Format)](./selectionset-element-format.md)|Definiuje pojedynczy zestaw obiektów platformy .NET, które mogą być przywoływane przez nazwę zestawu.|

## <a name="text-value"></a>Wartość tekstowa

Określ nazwę aby odwoływać się do zestawu wyboru. Istnieją żadne ograniczenia dotyczące znaków, które można użyć.

## <a name="remarks"></a>Uwagi

Nazwa określona w tym miejscu jest używana w `SelectionSetName` elementu. Zbiór, który może służyć przez widok, zgodnie z definicją widoku (widoki mogą mieć wiele definicji), lub podczas określania warunku zaznaczenia. Aby uzyskać więcej informacji na temat zestawów wybór zobacz [Definiowanie ustawia z obiektów](./defining-selection-sets.md).

## <a name="example"></a>Przykład

W tym przykładzie `SelectionSet` element, który definiuje cztery typy .NET. Nazwa zestawu wyboru jest "FileSystemTypes".

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

[Element SelectionSet (Format)](./selectionset-element-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
