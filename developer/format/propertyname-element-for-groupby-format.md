---
title: Element PropertyName GroupBy (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851898"
---
# <a name="propertyname-element-for-groupby-format"></a>PropertyName, element — GroupBy (format)

Określa właściwości platformy .NET, który uruchamia nową grupę, zmianie wartości.

— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu PropertyName widoku (w formacie) dla grupowania (w formacie)

## <a name="syntax"></a>Składnia

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `PropertyName` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[GroupBy — Element dla widoku (Format)](./groupby-element-for-view-format.md)|Definiuje sposób wyświetlania grupy obiektów platformy .NET.|

## <a name="text-value"></a>Wartość tekstowa

Określ nazwę właściwości platformy .NET.

## <a name="remarks"></a>Uwagi

Rozpoczyna się nowej grupy programu Windows PowerShell, zawsze wtedy, gdy zmieni się wartość tej właściwości.

Gdy ten element jest określony, nie można określić [ScriptBlock](./scriptblock-element-for-groupby-format.md) element, aby rozpocząć nową grupę.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak uruchomić nową grupę, po zmianie wartości właściwości.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Na przykład kompletny plik formatowania, który zawiera ten element zobacz [szerokie (grupowania)](./wide-view-groupby.md).

## <a name="see-also"></a>Zobacz też

[GroupBy — Element dla widoku (Format)](./groupby-element-for-view-format.md)

[Element ScriptBlock GroupBy (Format)](./scriptblock-element-for-groupby-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
