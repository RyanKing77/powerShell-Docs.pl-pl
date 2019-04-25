---
title: Element ColumnNumber WideControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066910"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>ColumnNumber, element — WideControl (format)

Określa liczbę kolumn wyświetlanych w szerokim oknie.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) WideControl — Element (Format) ColumnNumber Element konfiguracji dla WideControl (Format)

## <a name="syntax"></a>Składnia

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ColumnNumber` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element WideControl (Format)](./widecontrol-element-format.md)|Definiuje całej (pojedyncza wartość) format listy dla widoku.|

## <a name="text-value"></a>Wartość tekstowa

Określ wartość dodatnią liczbą całkowitą.

## <a name="remarks"></a>Uwagi

Podczas definiowania szerokie, możesz dodać `AutoSize` element lub `ColumnNumber` element, ale nie można dodać oba.

Aby uzyskać więcej informacji na temat składników szerokie, zobacz [tworzenia szerokiej widoku](./creating-a-wide-view.md).

Na przykład szerokie zobacz [szerokie (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Zobacz też

[Element AutoSize WideControl (Format)](./autosize-element-for-widecontrol-format.md)

[Tworzenie szerokiej widoku](./creating-a-wide-view.md)

[Szerokie (Basic)](./wide-view-basic.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
