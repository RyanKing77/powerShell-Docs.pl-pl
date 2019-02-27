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
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="bf00a-102">Definiowanie warunków wyświetlania danych</span><span class="sxs-lookup"><span data-stu-id="bf00a-102">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="bf00a-103">Podczas definiowania, jakie dane są wyświetlane w widoku lub kontrolki, można określić warunek, który musi istnieć dla danych, które mają być wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="bf00a-103">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="bf00a-104">Warunek mogą być wyzwalane przez określoną właściwość lub skryptu, lub wartość właściwości, które daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="bf00a-104">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="bf00a-105">Po spełnieniu warunku wyboru definicji widoku lub formant jest używany.</span><span class="sxs-lookup"><span data-stu-id="bf00a-105">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="bf00a-106">Określania warunku wybór definicji</span><span class="sxs-lookup"><span data-stu-id="bf00a-106">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="bf00a-107">Podczas tworzenia definicji widoku lub formantu, `EntrySelectedBy` element jest używany do określenia obiekty, które będą używać definicji lub jakie warunek musi istnieć dla definicji, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="bf00a-107">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="bf00a-108">Warunek jest określona przez `SelectionCondition` elementu.</span><span class="sxs-lookup"><span data-stu-id="bf00a-108">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="bf00a-109">W poniższym przykładzie jest określony warunek wyboru, aby uzyskać pełną definicję widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="bf00a-109">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="bf00a-110">W tym przykładzie definicji jest używana tylko wtedy, gdy określony skrypt jest oceniany w celu `true`.</span><span class="sxs-lookup"><span data-stu-id="bf00a-110">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

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

<span data-ttu-id="bf00a-111">Nie ma żadnego limitu, liczbę warunków wyboru, które można określić dla definicji widoku lub formantu.</span><span class="sxs-lookup"><span data-stu-id="bf00a-111">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="bf00a-112">Jedynymi wymogami są następujące:</span><span class="sxs-lookup"><span data-stu-id="bf00a-112">The only requirements are the following:</span></span>

- <span data-ttu-id="bf00a-113">Warunek wyboru należy określić jedną nazwę właściwości lub skrypt, aby wyzwolić warunek, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="bf00a-113">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="bf00a-114">Warunek wyboru można określić dowolną liczbę typów .NET lub zaznaczenie Ustawia, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="bf00a-114">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="bf00a-115">Określania warunku zaznaczenie elementu</span><span class="sxs-lookup"><span data-stu-id="bf00a-115">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="bf00a-116">Można również określić, gdy elementu widoku listy lub formantu, jest używany przez dołączenie `ItemSelectionCondition` elementu w definicji elementu.</span><span class="sxs-lookup"><span data-stu-id="bf00a-116">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="bf00a-117">W poniższym przykładzie warunek wyboru jest określona dla elementu widoku listy.</span><span class="sxs-lookup"><span data-stu-id="bf00a-117">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="bf00a-118">W tym przykładzie element jest używany tylko wtedy, gdy skrypt jest oceniany w celu `true`.</span><span class="sxs-lookup"><span data-stu-id="bf00a-118">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="bf00a-119">Można określić warunku wybór tylko jednego elementu.</span><span class="sxs-lookup"><span data-stu-id="bf00a-119">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="bf00a-120">I stan, należy określić jedną nazwę właściwości lub skrypt, aby wyzwolić warunek, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="bf00a-120">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="bf00a-121">Elementy XML</span><span class="sxs-lookup"><span data-stu-id="bf00a-121">XML Elements</span></span>

 <span data-ttu-id="bf00a-122">Następujące elementy XML są używane do tworzenia warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="bf00a-122">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="bf00a-123">Następujące elementy określają warunki wyboru definicji widoku:</span><span class="sxs-lookup"><span data-stu-id="bf00a-123">The following elements specify selection conditions for view definitions:</span></span>

    - [<span data-ttu-id="bf00a-124">Element SelectionCondition EntrySelectedBy dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="bf00a-124">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="bf00a-125">Element SelectionCondition EntrySelectedBy dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bf00a-125">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="bf00a-126">Element SelectionCondition EntrySelectedBy dla WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bf00a-126">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="bf00a-127">Element SelectionCondition EntrySelectedBy dla formant niestandardowy (Format)</span><span class="sxs-lookup"><span data-stu-id="bf00a-127">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="bf00a-128">Następujące elementy określ wybór warunki typowe i widoku kontroli definicje:</span><span class="sxs-lookup"><span data-stu-id="bf00a-128">The following elements specify selection conditions for common and view control definitions:</span></span>

    - [<span data-ttu-id="bf00a-129">Element SelectionCondition EntrySelectedBy dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="bf00a-129">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="bf00a-130">Element SelectionCondition EntrySelectedBy dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="bf00a-130">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="bf00a-131">Następujący element określa warunek wyboru dotyczące rozszerzania kolekcji obiektów:</span><span class="sxs-lookup"><span data-stu-id="bf00a-131">The following element specifies the selection condition for expanding collection objects:</span></span>

    - [<span data-ttu-id="bf00a-132">Element SelectionCondition EntrySelectedBy dla EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="bf00a-132">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="bf00a-133">Następujący element określa warunek wyboru, aby wyświetlić nową grupę danych:</span><span class="sxs-lookup"><span data-stu-id="bf00a-133">The following element specifies the selection condition for displaying a new group of data:</span></span>

    - [<span data-ttu-id="bf00a-134">Element SelectionCondition EntrySelectedBy dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="bf00a-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="bf00a-135">Następujący element określa warunek wyboru elementu widoku listy:</span><span class="sxs-lookup"><span data-stu-id="bf00a-135">The following element specifies an item selection condition for a list view:</span></span>

    - [<span data-ttu-id="bf00a-136">Element ItemSelectionCondition dla elementu listy dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bf00a-136">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="bf00a-137">Następujące elementy określić warunek Wybór elementu kontrolki:</span><span class="sxs-lookup"><span data-stu-id="bf00a-137">The following elements specify an item selection condition for controls:</span></span>

    - [<span data-ttu-id="bf00a-138">Element ItemSelectionCondition ExpressionBinding dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="bf00a-138">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="bf00a-139">Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="bf00a-139">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [<span data-ttu-id="bf00a-140">Element ItemSelectionCondition ExpressionBinding dla formant niestandardowy (Format)</span><span class="sxs-lookup"><span data-stu-id="bf00a-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="bf00a-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bf00a-141">See Also</span></span>

[<span data-ttu-id="bf00a-142">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="bf00a-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
