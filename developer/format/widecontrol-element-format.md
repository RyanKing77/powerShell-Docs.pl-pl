---
title: Element WideControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849490"
---
# <a name="widecontrol-element-format"></a>WideControl, element (format)

Definiuje całej (pojedyncza wartość) format listy dla widoku. Ten widok przedstawia jedną właściwość wartość lub wartość skryptu dla każdego obiektu.

Konfiguracji elementu (w formacie) Element ViewDefinitions (Format) widoku elementu (w formacie) WideControl elemencie (Format)

## <a name="syntax"></a>Składnia

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `WideControl` elementu. Nie można określić `AutoSize` i `ColumnNumber` elementy w tym samym czasie.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element AutoSize WideControl (Format)](./autosize-element-for-widecontrol-format.md)|Element opcjonalny.<br /><br /> Określa, czy rozmiar kolumny i liczba kolumn są dostosowywane na podstawie rozmiaru danych.|
|[Element ColumnNumber WideControl (Format)](./columnnumber-element-for-widecontrol-format.md)|Element opcjonalny.<br /><br /> Określa liczbę kolumn wyświetlanych w szerokim oknie.|
|[Element WideEntries (Format)](./wideentries-element-for-widecontrol-format.md)|Element wymagany.<br /><br /> Zawiera definicje szerokie.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Widok elementu (w formacie)](./view-element-format.md)|Określa widok, który służy do wyświetlania jeden lub więcej obiektów platformy .NET.|

## <a name="remarks"></a>Uwagi

Podczas definiowania szerokie, możesz dodać `AutoSize` element lub `ColumnNumber` , ale nie można dodać oba.

W większości przypadków tylko jedną definicję, jest wymagana dla każdego szerokie, ale użytkownik może mieć wielu definicji, jeśli chcesz wyświetlić różne obiekty platformy .NET przy użyciu tego samego widoku. W takich przypadkach możesz podać definicję osobne dla każdego obiektu lub grupy obiektów.

Aby uzyskać więcej informacji na temat składników szerokie, zobacz [szeroki składniki widoków](./creating-a-wide-view.md).

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `WideControl` element, który służy do wyświetlania właściwości [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu.

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

Aby uzyskać pełny przykład szerokie, zobacz [szerokie (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Zobacz też

[Element AutoSize WideControl (Format)](./autosize-element-for-widecontrol-format.md)

[Element ColumnNumber WideControl (Format)](./columnnumber-element-for-widecontrol-format.md)

[Widok elementu (w formacie)](./view-element-format.md)

[Element WideEntries (Format)](./wideentries-element-for-widecontrol-format.md)

[Szerokie (Basic)](./wide-view-basic.md)

[Tworzenie szerokiej widoku](./creating-a-wide-view.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
