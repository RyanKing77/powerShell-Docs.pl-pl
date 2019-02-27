---
title: Etykieta elementu dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851289"
---
# <a name="label-element-for-groupby-format"></a>Label, element — GroupBy (format)

Określa etykietę, która jest wyświetlana, gdy zostanie osiągnięty nowej grupy.

— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu Label widoku (w formacie) dla grupowania (w formacie)

## <a name="syntax"></a>Składnia

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Label` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[GroupBy — Element dla widoku (Format)](./groupby-element-for-view-format.md)|Definiuje sposób wyświetlania nowej grupy obiektów.|

## <a name="text-value"></a>Wartość tekstowa

Podaj tekst, który jest wyświetlany zawsze wtedy, gdy napotka programu Windows PowerShell, nową właściwość lub wartość skryptu.

## <a name="remarks"></a>Uwagi

Oprócz tekstu określonego przez ten element programu Windows PowerShell Wyświetla nową wartość, która rozpoczyna się w grupie, a następnie dodaje pusty wiersz, przed i po niej.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia etykietę dla nowej grupy. Wyświetlanej etykiety powinien wyglądać mniej więcej tak: `Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Na przykład kompletny plik formatowania, który zawiera ten element zobacz [szerokie (grupowania)](./wide-view-groupby.md).

## <a name="see-also"></a>Zobacz też

[GroupBy — Element dla widoku (Format)](./groupby-element-for-view-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
