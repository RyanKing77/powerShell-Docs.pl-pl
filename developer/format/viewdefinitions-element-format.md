---
title: Element ViewDefinitions (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851072"
---
# <a name="viewdefinitions-element-format"></a>ViewDefinitions, element (format)

Zawiera definicje widoków, używany do wyświetlania obiektów platformy .NET. Widoki te można wyświetlić właściwości i wartości obiektu w skrypcie w formacie tabeli, format listy, formacie szerokim i format formantu niestandardowego.

Element ViewDefinitions (Format XML) (w formacie) elementu konfiguracji

## <a name="syntax"></a>Składnia

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ViewDefinitions` elementu. Nie ma żadnego limitu liczby widoków, które mogą być definiowane w pliku formatowania i mogą być dodawane w dowolnej kolejności.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Widok elementu (w formacie)](./view-element-format.md)|Określa widok, który służy do wyświetlania jeden lub więcej obiektów platformy .NET.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element konfiguracji (Format)](./configuration-element-format.md)|Reprezentuje element najwyższego poziomu w pliku formatowania.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat składników różne typy widoków zobacz następujące tematy:

- [Tworzenie widoku tabeli](./creating-a-table-view.md)

- [Tworzenie widoku listy](./creating-a-list-view.md)

- [Tworzenie szerokiej widoku](./creating-a-wide-view.md)

- [Formanty niestandardowe](./creating-custom-controls.md)

## <a name="example"></a>Przykład

W tym przykładzie `ViewDefinitions` element, który zawiera elementy nadrzędne w widoku tabeli i widok listy.

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a>Zobacz też

[Element konfiguracji (Format)](./configuration-element-format.md)

[Widok elementu (w formacie)](./view-element-format.md)

[Tworzenie widoku tabeli](./creating-a-table-view.md)

[Tworzenie widoku listy](./creating-a-list-view.md)

[Tworzenie szerokiej widoku](./creating-a-wide-view.md)

[Formanty niestandardowe](./creating-custom-controls.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
