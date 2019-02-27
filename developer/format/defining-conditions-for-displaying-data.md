---
title: Definiowanie warunków do wyświetlania danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846564"
---
# <a name="defining-conditions-for-displaying-data"></a>Definiowanie warunków wyświetlania danych

Podczas definiowania, jakie dane są wyświetlane w widoku lub kontrolki, można określić warunek, który musi istnieć dla danych, które mają być wyświetlane. Warunek mogą być wyzwalane przez określoną właściwość lub skryptu, lub wartość właściwości, które daje w wyniku `true`. Po spełnieniu warunku wyboru definicji widoku lub formant jest używany.

## <a name="specifying-a-selection-condition-for-a-definition"></a>Określania warunku wybór definicji

Podczas tworzenia definicji widoku lub formantu, `EntrySelectedBy` element jest używany do określenia obiekty, które będą używać definicji lub jakie warunek musi istnieć dla definicji, który ma być używany. Warunek jest określona przez `SelectionCondition` elementu.

W poniższym przykładzie jest określony warunek wyboru, aby uzyskać pełną definicję widoku tabeli. W tym przykładzie definicji jest używana tylko wtedy, gdy określony skrypt jest oceniany w celu `true`.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <SelectionCondition>
      <ScriptBlock>ScriptToEvaluate</ScriptBlock>
    </SelectionCondition>
  </EntrySelectedBy>
  <TableColumnItems>
  </TableColumnItems>
</TableRowEntry>

```

Nie ma żadnego limitu, liczbę warunków wyboru, które można określić dla definicji widoku lub formantu. Jedynymi wymogami są następujące:

- Warunek wyboru należy określić jedną nazwę właściwości lub skrypt, aby wyzwolić warunek, ale nie można określić jednocześnie.

- Warunek wyboru można określić dowolną liczbę typów .NET lub zaznaczenie Ustawia, ale nie można określić jednocześnie.

## <a name="specifying-a-selection-condition-for-an-item"></a>Określania warunku zaznaczenie elementu

Można również określić, gdy elementu widoku listy lub formantu, jest używany przez dołączenie `ItemSelectionCondition` elementu w definicji elementu. W poniższym przykładzie warunek wyboru jest określona dla elementu widoku listy. W tym przykładzie element jest używany tylko wtedy, gdy skrypt jest oceniany w celu `true`.

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

Można określić warunku wybór tylko jednego elementu. I stan, należy określić jedną nazwę właściwości lub skrypt, aby wyzwolić warunek, ale nie można określić jednocześnie.

## <a name="xml-elements"></a>Elementy XML

 Następujące elementy XML są używane do tworzenia warunek wyboru.

- Następujące elementy określają warunki wyboru definicji widoku:

    - [Element SelectionCondition EntrySelectedBy dla tablecontrol — (w formacie)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [Element SelectionCondition EntrySelectedBy dla elementu ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [Element SelectionCondition EntrySelectedBy dla WideControl (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [Element SelectionCondition EntrySelectedBy dla formant niestandardowy (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- Następujące elementy określ wybór warunki typowe i widoku kontroli definicje:

    - [Element SelectionCondition EntrySelectedBy dla formantów dla konfiguracji (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [Element SelectionCondition EntrySelectedBy dla formantów widoku (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- Następujący element określa warunek wyboru dotyczące rozszerzania kolekcji obiektów:

    - [Element SelectionCondition EntrySelectedBy dla EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Następujący element określa warunek wyboru, aby wyświetlić nową grupę danych:

    - [Element SelectionCondition EntrySelectedBy dla grupowania (w formacie)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- Następujący element określa warunek wyboru elementu widoku listy:

    - [Element ItemSelectionCondition dla elementu listy dla elementu ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- Następujące elementy określić warunek Wybór elementu kontrolki:

    - [Element ItemSelectionCondition ExpressionBinding dla formantów dla konfiguracji (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [Element ItemSelectionCondition ExpressionBinding dla formant niestandardowy (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>Zobacz też

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
