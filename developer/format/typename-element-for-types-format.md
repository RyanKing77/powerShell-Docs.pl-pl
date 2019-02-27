---
title: Element TypeName dla typów (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: 4f463ac6b70a00f628c5b93b112c5fa510ff3bfb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845115"
---
# <a name="typename-element-for-types-format"></a>TypeName, element — Types (format)

Określa typ architektury .NET, obiektu, który należy do zestawu zaznaczenia.

Element SelectionSet SelectionSets — Element (w formacie) — Element (w formacie) konfiguracji (Format) typy elementu TypeName elementu (w formacie) typy (Format)

## <a name="syntax"></a>Składnia

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TypeName` elementu. Co najmniej jeden `TypeName` element musi być uwzględniony w zestawie zaznaczenia.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Typy elementu (w formacie)](./types-element-for-selectionset-format.md)|Definiuje obiekty .NET, ustawionych w zaznaczeniu.|

## <a name="text-value"></a>Wartość tekstowa

Określ w pełni kwalifikowana nazwa typ architektury .NET.

## <a name="remarks"></a>Uwagi

Można użyć zestawów zaznaczenie, gdy masz zestaw powiązanych obiektów, które odwołują się za pomocą jednej nazwy, takiego jak zestaw obiektów, które są powiązane z dziedziczenia. Podczas definiowania widoków, można określić zestaw obiektów przy użyciu nazwy wybór zestawu, zamiast wymieniać wszystkich obiektów w ramach każdego widoku.

Wspólne wybór zestawy są określane przez ich nazwy, podczas definiowania widoków formatowania pliku. W takich przypadkach `SelectionSetName` element podrzędny elementu `ViewSelectedBy` elementu widoku określa zestaw. Jednakże wpisy widoku można również określić zestaw zaznaczenia dotyczy tylko ten wpis z widoku. Aby uzyskać więcej informacji na temat zestawów wybór zobacz [Definiowanie ustawia z obiektów](./defining-selection-sets.md).

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `SelectionSet` element, który definiuje cztery typy .NET.

```
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

[Element SelectionSets (Format)](./selectionsets-element-format.md)

[Typy elementu (w formacie)](./types-element-for-selectionset-format.md)

[Zapisywanie Windows PowDefining zestawy ObjecterShell formatowanie pliku](./writing-a-powershell-formatting-file.md)
