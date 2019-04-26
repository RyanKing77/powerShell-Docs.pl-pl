---
title: Element SelectionSetName EntrySelectedBy dla WideControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064034"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a>SelectionSetName, element — EntrySelectedBy, WideControl (format)

Określa zestaw obiektów platformy .NET dla definicji. Definicja jest używana zawsze, gdy wyświetlony zostanie jeden z tych obiektów.

— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) WideControl — Element (Format) WideEntries — Element (Format) WideEntry — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionSetName WideEntry (Format) EntrySelectedBy dla WideEntry (Format)

## <a name="syntax"></a>Składnia

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionSetName` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element EntrySelectedBy WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Definiuje typy .NET, korzystające z tego wpisu szeroki lub warunek, który musi istnieć dla tego wpisu do użycia.|

## <a name="text-value"></a>Wartość tekstowa

Określ nazwę zestawu wyboru.

## <a name="remarks"></a>Uwagi

Każda definicja należy określić jedną nazwę typu, wybór zestawu lub warunek wyboru.

Wybór zestawy są zwykle używane zdefiniować grupy obiektów, które są używane w wielu widoków. Na przykład można utworzyć widoku tabeli i widok listy, aby uzyskać ten sam zestaw obiektów. Aby uzyskać więcej informacji na temat definiowania zestawów wybór zobacz [Definiowanie ustawia z obiektów w celu wyświetlenia](./defining-selection-sets.md).

Aby uzyskać więcej informacji o innych składnikach szerokie, zobacz [tworzenia szerokiej widoku](./creating-a-wide-view.md).

## <a name="see-also"></a>Zobacz też

[Tworzenie szerokiej widoku](./creating-a-wide-view.md)

[Definiowanie zestawów zaznaczenia](./defining-selection-sets.md)

[Element EntrySelectedBy WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
