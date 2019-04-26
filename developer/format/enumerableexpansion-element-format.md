---
title: Element EnumerableExpansion (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066145"
---
# <a name="enumerableexpansion-element-format"></a>EnumerableExpansion, element (format)

Definiuje sposób określonej kolekcji .NET, które obiekty są rozszerzane, gdy są one wyświetlane w widoku.

Konfiguracji elementu (w formacie) elementu DefaultSettings (Format) EnumerableExpansions — Element (Format) EnumerableExpansion elementu (w formacie)

## <a name="syntax"></a>Składnia

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `EnumerableExpansion` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element EntrySelectedBy EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md)|Element opcjonalny.<br /><br /> Definiuje, które obiekty kolekcji .NET są rozszerzane przez tę definicję.|
|[Rozwiń Element (Format)](./expand-element-format.md)|Określa, jak obiekt kolekcji jest rozwinięta, dla tej definicji.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element EnumerableExpansions (Format)](./enumerableexpansions-element-format.md)|Definiuje różne sposoby tej kolekcji .NET, które obiekty są rozszerzane, gdy są one wyświetlane w widoku.|

## <a name="remarks"></a>Uwagi

Ten element jest używany do definiowania sposobu wyświetlania obiektów kolekcji i obiektów w kolekcji. W tym przypadku obiekt kolekcji odnosi się do dowolnego obiektu, który obsługuje **System.Collections.ICollection** interfejsu.

Zachowanie domyślne jest do wyświetlenia tylko właściwości obiektów w kolekcji.

## <a name="see-also"></a>Zobacz też

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
