---
title: Definiowanie zestawów wybór | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848860"
---
# <a name="defining-selection-sets"></a>Definiowanie zestawów zaznaczeń

Podczas tworzenia wielu widoków i kontrolek, można zdefiniować rodzaje obiektów, które są określane jako zestawy zaznaczenia. Zestaw zaznaczenia umożliwia zdefiniowanie obiekty w jeden raz bez konieczności wcześniejszego definiowania je wielokrotnie do każdego widoku lub kontrolki. Wybór zestawy są zazwyczaj używane w przypadku zestaw powiązanych obiektów platformy .NET. Na przykład `FileSystem` formatowania pliku (FileSystem.format.ps1xml) definiuje zestaw wybór typów systemów plików korzystających z wielu widoków.

## <a name="where-selection-sets-are-defined-and-referenced"></a>Gdzie zestawy wyboru są zdefiniowane i do którego się odwoływano

Należy zdefiniować zaznaczenie zestawów jako części wspólnych danych, używany przez wszystkie widoki i formanty zdefiniowane w pliku formatowania. Poniższy przykład pokazuje jak zdefiniować trzech zestawów zaznaczenia.

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

Możesz odwoływać się do wyboru ustawia w następujący sposób:

- Każdy widok zawiera `ViewSelectedBy` element, który definiuje obiekty, które są wyświetlane, korzystając z widoku. `ViewSelectedBy` Element ma `SelectionSetName` elementu podrzędnego, który określa zaznaczenie ustaw wszystkie definicje użytkowania widoku. Nie ma żadnych ograniczeń dotyczących liczby zestawów wyboru, które odwołują się z widoku.

- W każdej definicji widoku lub formantu `EntrySelectedBy` element definiuje obiekty, które są wyświetlane przy użyciu tej definicji. Zazwyczaj widoku lub kontroli ma tylko jedną definicję, więc obiekty są definiowane przez `ViewSelectedBy` elementu. `EntrySelectedBy` Element definicja ma `SelectionSetName` elementu podrzędnego, który określa zestaw zaznaczenia. Jeśli określisz zaznaczenia, ustaw dla definicji, nie można określić dowolne inne elementy podrzędne `EntrySelectedBy` elementu.

- W każdej definicji widoku lub formantu `SelectionCondition` element może służyć do określania warunku gdy definicja jest używany. `SelectionCondition` Element ma `SelectionSetName` element podrzędny, który określa zestaw zaznaczenie, która wyzwala warunku. Warunek jest wyzwalany, gdy obiekty zdefiniowane w zestawie wyboru są wyświetlane. Aby uzyskać więcej informacji na temat ustawiania tych warunków, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).

## <a name="selection-set-example"></a>Wybór zestawu przykład

W poniższym przykładzie przedstawiono zestaw zaznaczenia, który pochodzi bezpośrednio z `FileSystem` formatowania pliku dostarczonego przez program Windows PowerShell. Aby uzyskać więcej informacji na temat innych Windows PowerShell, formatowanie pliki Zobacz [pliki formatowania programu Windows PowerShell](./powershell-formatting-files.md).

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

Poprzedni zestaw wybór mowa w punkcie `ViewSelectedBy` elementu widoku tabeli.

```xml
<ViewDefinitions>
  <View>
    <Name>Files</Name>
    <ViewSelectedBy>
      <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="xml-elements"></a>Elementy XML

 Nie ma żadnego limitu liczby zestawów wyboru, które można zdefiniować. Następujące elementy XML są używane do tworzenia zestawu wyboru.

- [SelectionSets](./selectionsets-element-format.md) element definiuje zestawów obiektów platformy .NET, które są przywoływane przez widoki i kontrolki formatowania pliku.

- [SelectionSet](./selectionset-element-format.md) element definiuje pojedynczy zestaw obiektów platformy .NET.

- [Nazwa](./name-element-for-selectionset-format.md) element Określa nazwę, która jest używana do odwołania zestawu wyboru.

- [Typy](./types-element-for-selectionset-format.md) element określa typy .NET obiektów zestawu wyboru. (W ciągu formatowania pliki obiektów są określane przez ich typ architektury .NET.)

 Następujące elementy XML są używane do określenia zestawu zaznaczenia.

- Następujący element Określa wybór skonfigurowany do używania w definicji widoku:

    - [Element SelectionSetName ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md)

    - [Element SelectionSetName EntrySelectedBy dla grupowania (w formacie)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- Następujące elementy określić zbiór używane zgodnie z definicją pojedynczy widok:

    - [Element SelectionSetName EntrySelectedBy dla elementu ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [Element SelectionSetName EntrySelectedBy dla tablecontrol — (w formacie)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [Element SelectionSetName EntrySelectedBy dla WideControl (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [Element SelectionSetName EntrySelectedBy dla formant niestandardowy dla widoku (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- Następujące elementy określić zbiór posługują się typowe i wyświetlać definicje sterowania:

    - [Element SelectionSetName EntrySelectedBy dla formantów widoku (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [Element SelectionSetName EntrySelectedBy dla formantów dla konfiguracji (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- Następujące elementy określić zbiór używane podczas definiowania obiektu, który można rozwinąć:

    - [Element SelectionSetName EntrySelectedBy dla EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Następujące elementy określić elementu set wyboru używany przez zaznaczenie warunków.

    - [Element SelectionSetName SelectionCondition dla formantów dla konfiguracji (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [Element SelectionSetName SelectionCondition dla formantów widoku (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [Element SelectionSetName SelectionCondition dla formant niestandardowy dla widoku (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [Element SelectionSetName SelectionCondition dla EntrySelectedBy dla EnumerableExpansion (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [Element SelectionSetName SelectionCondition dla EntrySelectedBy dla ListEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [Element SelectionSetName SelectionCondition dla EntrySelectedBy dla tablecontrol — (w formacie)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [Element SelectionSetName SelectionCondition dla EntrySelectedBy dla WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [Element SelectionSetName SelectionCondition dla grupowania (w formacie)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a>Zobacz też

[SelectionSets](./selectionsets-element-format.md)

[SelectionSet](./selectionset-element-format.md)

[Nazwa](./name-element-for-selectionset-format.md)

[Typy](./types-element-for-selectionset-format.md)

[Pliki formatowania programu PowerShell](./powershell-formatting-files.md)

[Definiowanie warunków, gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md)

[Pisanie programu PowerShell, formatowanie i typy plików](./writing-a-powershell-formatting-file.md)
