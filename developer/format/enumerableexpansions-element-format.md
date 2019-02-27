---
title: Element EnumerableExpansions (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849791"
---
# <a name="enumerableexpansions-element-format"></a>EnumerableExpansions, element (format)

Definiuje, jak rozszerzyć obiekty kolekcji .NET, gdy są one wyświetlane w widoku.

Element EnumerableExpansions DefaultSettings — Element (w formacie) — Element (w formacie) konfiguracji (Format)

## <a name="syntax"></a>Składnia

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `EnumerableExpansions` elementu. Nie ma żadnego limitu liczby elementów podrzędnych, które są dostępne.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element EnumerableExpansion (Format)](./enumerableexpansion-element-format.md)|Element opcjonalny.<br /><br /> Definiuje określone obiekty kolekcji .NET, które są rozszerzane, gdy są one wyświetlane w widoku.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element DefaultSettings (Format)](./defaultsettings-element-format.md)|Definiuje typowe ustawienia, które są stosowane do wszystkich widoków formatowania pliku.|

## <a name="remarks"></a>Uwagi

Ten element jest używany do definiowania sposobu wyświetlania obiektów kolekcji i obiektów w kolekcji. W tym przypadku obiekt kolekcji odnosi się do dowolnego obiektu, który obsługuje **System.Collections.ICollection** interfejsu.

## <a name="see-also"></a>Zobacz też

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
