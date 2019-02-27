---
title: Element ViewSelectedBy (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851842"
---
# <a name="viewselectedby-element-format"></a>ViewSelectedBy, element (format)

Definiuje obiekty .NET, które są wyświetlane w widoku. Każdy widok należy określić co najmniej jednego obiektu .NET.

Element ViewDefinitions (Format) widok elementów (w formacie) ViewSelectedBy elemencie (Format)

## <a name="syntax"></a>Składnia

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ViewSelectedBy` elementu. Ten element musi zawierać co najmniej jeden `TypeName` lub `SelectionSetName` elementu podrzędnego. Nie ma żadnego limitu liczby elementów podrzędnych, które można określić ani nie jest ważna ich kolejność.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element TypeName dla ViewSelectedBy (Format)](./typename-element-for-viewselectedby-format.md)|Element opcjonalny.<br /><br /> Określa obiekt .NET, który jest wyświetlany w widoku.|
|[Element SelectionSetName ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md)|Element opcjonalny.<br /><br /> Określa zestaw obiektów platformy .NET, które są wyświetlane w widoku.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Widok elementu (w formacie)](./view-element-format.md)|Określa widok, który zawiera jeden lub więcej obiektów platformy .NET.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji o sposobie korzystania z tego elementu w różnych widokach, zobacz [składników widok tabeli](./creating-a-table-view.md), [składniki widok listy](./creating-a-list-view.md), [szeroki składniki widoków](./creating-a-wide-view.md)i [Kontrolek niestandardowych składników](./creating-custom-controls.md).

`SelectionSetName` Element jest używany podczas formatowania plik definiuje zestaw obiektów, które są wyświetlane przez wiele widoków. Aby uzyskać więcej informacji o wybór zestawów są zdefiniowane i odwołania, zobacz [Definiowanie ustawia z obiektów](./defining-selection-sets.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak określić [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) obiekt widoku listy. Ten sam schemat jest używany dla tabeli, szeroką i niestandardowe widoki.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Zobacz też

[Tworzenie widoku listy](./creating-a-list-view.md)

[Tworzenie widoku tabeli](./creating-a-table-view.md)

[Tworzenie szerokiej widoku](./creating-a-wide-view.md)

[Tworzenie niestandardowych formantów](./creating-custom-controls.md)

[Definiowanie zestawów zaznaczenia](./defining-selection-sets.md)

[Element SelectionSetName ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md)

[Element TypeName (Format)](./typename-element-for-viewselectedby-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
