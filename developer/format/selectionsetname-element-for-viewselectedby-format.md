---
title: Element SelectionSetName ViewSelectedBy (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848447"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>SelectionSetName, element — ViewSelectedBy (format)

Określa zestaw obiektów platformy .NET, które są wyświetlane w widoku.

— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) elementu ViewSelectedBy (Format) SelectionSetName Element konfiguracji dla ViewSelectedBy (Format)

## <a name="syntax"></a>Składnia

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionSetName` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ViewSelectedBy (Format)](./viewselectedby-element-format.md)|Definiuje obiekty .NET, które są wyświetlane w widoku.|

## <a name="text-value"></a>Wartość tekstowa

Określ nazwę zestawu wyboru, który jest definiowany przez `Name` element do zestawu wyboru.

## <a name="remarks"></a>Uwagi

Można użyć zestawów zaznaczenie, gdy masz zestaw powiązanych obiektów, które odwołują się za pomocą jednej nazwy, takiego jak zestaw obiektów, które są powiązane z dziedziczenia. Aby uzyskać więcej informacji o definiowaniu i odwołania do zestawów wyboru, zobacz [Definiowanie ustawia z obiektów](./defining-selection-sets.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak określić zbiór w celu wyświetlenia listy opcji. Ten sam schemat jest używany dla tabeli, szeroką i niestandardowe widoki.

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Zobacz też

[Definiowanie zestawów zaznaczenia](./defining-selection-sets.md)

[Element ViewSelectedBy (Format)](./viewselectedby-element-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
