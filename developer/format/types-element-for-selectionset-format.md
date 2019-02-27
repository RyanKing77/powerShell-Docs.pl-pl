---
title: Typy elementu SelectionSet (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851275"
---
# <a name="types-element-for-selectionset-format"></a>Types, element — SelectionSet (format)

Definiuje obiekty .NET, ustawionych w zaznaczeniu.

Element SelectionSet SelectionSets — Element (w formacie) — Element (w formacie) konfiguracji (Format) typy elementu (w formacie)

## <a name="syntax"></a>Składnia

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Types` elementu. Musi istnieć co najmniej jeden element podrzędny, ale nie ma żadnego limitu maksymalnej liczby elementów podrzędnych, które mogą zostać dodane.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element TypeName typów (Format)](./typename-element-for-types-format.md)|Element wymagany.<br /><br /> Określa obiekt .NET, który należy do zestawu zaznaczenia.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element SelectionSet (Format)](./selectionset-element-format.md)|Definiuje zestaw obiektów platformy .NET, które mogą być przywoływane przez nazwę zestawu.|

## <a name="remarks"></a>Uwagi

Obiekty zdefiniowane przez ten element tworzą zbiór, który może służyć przez widok, zgodnie z definicją widoku (widoki mogą mieć wiele definicji), lub podczas określania warunku zaznaczenia.  Aby uzyskać więcej informacji na temat zestawów wybór zobacz [Definiowanie ustawia z obiektów](./defining-selection-sets.md).

## <a name="example"></a>Przykład

W tym przykładzie `SelectionSet` element, który definiuje cztery typy .NET.

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

[Definiowanie zestawów obiektów](./defining-selection-sets.md)

[Element SelectionSet (Format)](./selectionset-element-format.md)

[Element TypeName typów (Format)](./typename-element-for-types-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
