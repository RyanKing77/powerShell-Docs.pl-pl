---
title: Rozwiń Element (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848615"
---
# <a name="expand-element-format"></a>Expand, element (format)

Określa, jak obiekt kolekcji jest rozwinięta, dla tej definicji.

Konfiguracji elementu (w formacie) elementu DefaultSettings (Format) EnumerableExpansions — Element (Format) EnumerableExpansion elementu (w formacie), rozwiń Element (Format)

## <a name="syntax"></a>Składnia

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Expand` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element EnumerableExpansion (Format)](./enumerableexpansion-element-format.md)|Definiuje sposób określonej kolekcji .NET, które obiekty są rozszerzane, gdy są one wyświetlane w widoku.|

## <a name="text-value"></a>Wartość tekstowa

Określ jedną z następujących wartości:

- EnumOnly: Wyświetla tylko właściwości obiektów w kolekcji.

- CoreOnly: Wyświetla tylko właściwości obiektu kolekcji.

- Zarówno: Wyświetla właściwości obiektów w kolekcji i właściwości obiektu kolekcji.

## <a name="remarks"></a>Uwagi

Ten element jest używany do definiowania sposobu wyświetlania obiektów kolekcji i obiektów w kolekcji. W tym przypadku obiekt kolekcji odnosi się do dowolnego obiektu, który obsługuje **System.Collections.ICollection** interfejsu.

Zachowanie domyślne jest do wyświetlenia tylko właściwości obiektów w kolekcji.

## <a name="see-also"></a>Zobacz też

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
