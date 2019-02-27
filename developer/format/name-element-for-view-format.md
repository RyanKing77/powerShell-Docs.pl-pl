---
title: Nazwa elementu widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849266"
---
# <a name="name-element-for-view-format"></a>Name, element — View (format)

Określa nazwę, która służy do identyfikacji tego widoku.

Widok elementu ViewDefinitions (Format) — Element (w formacie) konfiguracji elementu (w formacie) elementu Name (Format)

## <a name="syntax"></a>Składnia

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Name` elementu. Tylko jeden `Name` element jest dozwolony dla każdego widoku.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Widok elementu (w formacie)](./view-element-format.md)|Określa widok, który służy do wyświetlania elementów członkowskich jeden lub więcej obiektów platformy .NET.|

## <a name="text-value"></a>Wartość tekstowa

Określ unikatową przyjazną nazwę dla widoku. Ta nazwa może zawierać odwołanie do typu widoku (np. widok tabeli lub widoku listy), które obiekt lub zestaw obiektów przy użyciu widoku, jakie polecenie zwraca obiekty lub kombinację tych.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji o różnych typach widoków zobacz następujące tematy: [Widok tabeli](./creating-a-table-view.md), [widok listy](./creating-a-list-view.md), [szerokie](./creating-a-wide-view.md), i [widok niestandardowy](./creating-custom-controls.md).

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `View` element, który definiuje widoku tabeli dla [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) obiektu. Nazwa widoku jest "Usługa".

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a>Zobacz też

[Tworzenie widoku listy](./creating-a-list-view.md)

[Tworzenie widoku tabeli](./creating-a-table-view.md)

[Tworzenie szerokiej widoku](./creating-a-wide-view.md)

[Tworzenie niestandardowych formantów](./creating-custom-controls.md)

[Widok elementu (w formacie)](./view-element-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
