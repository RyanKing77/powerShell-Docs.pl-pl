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
# <a name="defining-selection-sets"></a><span data-ttu-id="e61a1-102">Definiowanie zestawów zaznaczeń</span><span class="sxs-lookup"><span data-stu-id="e61a1-102">Defining Selection Sets</span></span>

<span data-ttu-id="e61a1-103">Podczas tworzenia wielu widoków i kontrolek, można zdefiniować rodzaje obiektów, które są określane jako zestawy zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="e61a1-103">When creating multiple views and controls, you can define sets of objects that are referred to as selection sets.</span></span> <span data-ttu-id="e61a1-104">Zestaw zaznaczenia umożliwia zdefiniowanie obiekty w jeden raz bez konieczności wcześniejszego definiowania je wielokrotnie do każdego widoku lub kontrolki.</span><span class="sxs-lookup"><span data-stu-id="e61a1-104">A selection set enables you to define the objects one time, without having to define them repeatedly for each view or control.</span></span> <span data-ttu-id="e61a1-105">Wybór zestawy są zazwyczaj używane w przypadku zestaw powiązanych obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="e61a1-105">Typically, selection sets are used when you have a set of related .NET objects.</span></span> <span data-ttu-id="e61a1-106">Na przykład `FileSystem` formatowania pliku (FileSystem.format.ps1xml) definiuje zestaw wybór typów systemów plików korzystających z wielu widoków.</span><span class="sxs-lookup"><span data-stu-id="e61a1-106">For example, The `FileSystem` formatting file (FileSystem.format.ps1xml) defines a selection set of the file system types that several views use.</span></span>

## <a name="where-selection-sets-are-defined-and-referenced"></a><span data-ttu-id="e61a1-107">Gdzie zestawy wyboru są zdefiniowane i do którego się odwoływano</span><span class="sxs-lookup"><span data-stu-id="e61a1-107">Where Selection Sets are Defined and Referenced</span></span>

<span data-ttu-id="e61a1-108">Należy zdefiniować zaznaczenie zestawów jako części wspólnych danych, używany przez wszystkie widoki i formanty zdefiniowane w pliku formatowania.</span><span class="sxs-lookup"><span data-stu-id="e61a1-108">You define selection sets as part of the common data that can be used by all the views and controls defined in the formatting file.</span></span> <span data-ttu-id="e61a1-109">Poniższy przykład pokazuje jak zdefiniować trzech zestawów zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="e61a1-109">The following example shows how to define three selection sets.</span></span>

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

<span data-ttu-id="e61a1-110">Możesz odwoływać się do wyboru ustawia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e61a1-110">You can reference a selection sets in the following ways:</span></span>

- <span data-ttu-id="e61a1-111">Każdy widok zawiera `ViewSelectedBy` element, który definiuje obiekty, które są wyświetlane, korzystając z widoku.</span><span class="sxs-lookup"><span data-stu-id="e61a1-111">Each view has a `ViewSelectedBy` element that defines which objects are displayed by using the view.</span></span> <span data-ttu-id="e61a1-112">`ViewSelectedBy` Element ma `SelectionSetName` elementu podrzędnego, który określa zaznaczenie ustaw wszystkie definicje użytkowania widoku.</span><span class="sxs-lookup"><span data-stu-id="e61a1-112">The `ViewSelectedBy` element has a `SelectionSetName` child element that specifies the selection set that all the definitions of the view use.</span></span> <span data-ttu-id="e61a1-113">Nie ma żadnych ograniczeń dotyczących liczby zestawów wyboru, które odwołują się z widoku.</span><span class="sxs-lookup"><span data-stu-id="e61a1-113">There is no restriction on the number of selection sets that you can reference from a view.</span></span>

- <span data-ttu-id="e61a1-114">W każdej definicji widoku lub formantu `EntrySelectedBy` element definiuje obiekty, które są wyświetlane przy użyciu tej definicji.</span><span class="sxs-lookup"><span data-stu-id="e61a1-114">In each definition of a view or control, the `EntrySelectedBy` element defines which objects are displayed by using that definition.</span></span> <span data-ttu-id="e61a1-115">Zazwyczaj widoku lub kontroli ma tylko jedną definicję, więc obiekty są definiowane przez `ViewSelectedBy` elementu.</span><span class="sxs-lookup"><span data-stu-id="e61a1-115">Typically a view or control has only one definition so the objects are defined by the `ViewSelectedBy` element.</span></span> <span data-ttu-id="e61a1-116">`EntrySelectedBy` Element definicja ma `SelectionSetName` elementu podrzędnego, który określa zestaw zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="e61a1-116">The `EntrySelectedBy` element of the definition has a `SelectionSetName` child element that specifies the selection set.</span></span> <span data-ttu-id="e61a1-117">Jeśli określisz zaznaczenia, ustaw dla definicji, nie można określić dowolne inne elementy podrzędne `EntrySelectedBy` elementu.</span><span class="sxs-lookup"><span data-stu-id="e61a1-117">If you specify the selection set for a definition, you cannot specify any of the other child elements of the `EntrySelectedBy` element.</span></span>

- <span data-ttu-id="e61a1-118">W każdej definicji widoku lub formantu `SelectionCondition` element może służyć do określania warunku gdy definicja jest używany.</span><span class="sxs-lookup"><span data-stu-id="e61a1-118">In each definition of a view or control, the `SelectionCondition` element can be used to specify a condition for when the definition is used.</span></span> <span data-ttu-id="e61a1-119">`SelectionCondition` Element ma `SelectionSetName` element podrzędny, który określa zestaw zaznaczenie, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="e61a1-119">The `SelectionCondition` element has a `SelectionSetName` child element that specifies the selection set that triggers the condition.</span></span> <span data-ttu-id="e61a1-120">Warunek jest wyzwalany, gdy obiekty zdefiniowane w zestawie wyboru są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="e61a1-120">The condition is triggered when any of the objects defined in the selection set are displayed.</span></span> <span data-ttu-id="e61a1-121">Aby uzyskać więcej informacji na temat ustawiania tych warunków, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e61a1-121">For more information about how to set these conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="selection-set-example"></a><span data-ttu-id="e61a1-122">Wybór zestawu przykład</span><span class="sxs-lookup"><span data-stu-id="e61a1-122">Selection Set Example</span></span>

<span data-ttu-id="e61a1-123">W poniższym przykładzie przedstawiono zestaw zaznaczenia, który pochodzi bezpośrednio z `FileSystem` formatowania pliku dostarczonego przez program Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e61a1-123">The following example shows a selection set that is taken directly from the `FileSystem` formatting file provided by Windows PowerShell.</span></span> <span data-ttu-id="e61a1-124">Aby uzyskać więcej informacji na temat innych Windows PowerShell, formatowanie pliki Zobacz [pliki formatowania programu Windows PowerShell](./powershell-formatting-files.md).</span><span class="sxs-lookup"><span data-stu-id="e61a1-124">For more information about other Windows PowerShell formatting files, see [Windows PowerShell Formatting Files](./powershell-formatting-files.md).</span></span>

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

<span data-ttu-id="e61a1-125">Poprzedni zestaw wybór mowa w punkcie `ViewSelectedBy` elementu widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="e61a1-125">The previous selection set is referenced in the `ViewSelectedBy` element of a table view.</span></span>

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

## <a name="xml-elements"></a><span data-ttu-id="e61a1-126">Elementy XML</span><span class="sxs-lookup"><span data-stu-id="e61a1-126">XML Elements</span></span>

 <span data-ttu-id="e61a1-127">Nie ma żadnego limitu liczby zestawów wyboru, które można zdefiniować.</span><span class="sxs-lookup"><span data-stu-id="e61a1-127">There is no limit to the number of selection sets that you can define.</span></span> <span data-ttu-id="e61a1-128">Następujące elementy XML są używane do tworzenia zestawu wyboru.</span><span class="sxs-lookup"><span data-stu-id="e61a1-128">The following XML elements are used to create a selection set.</span></span>

- <span data-ttu-id="e61a1-129">[SelectionSets](./selectionsets-element-format.md) element definiuje zestawów obiektów platformy .NET, które są przywoływane przez widoki i kontrolki formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="e61a1-129">The [SelectionSets](./selectionsets-element-format.md) element defines the sets of .NET objects that are referenced by the views and controls of the formatting file.</span></span>

- <span data-ttu-id="e61a1-130">[SelectionSet](./selectionset-element-format.md) element definiuje pojedynczy zestaw obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="e61a1-130">The [SelectionSet](./selectionset-element-format.md) element defines a single set of .NET objects.</span></span>

- <span data-ttu-id="e61a1-131">[Nazwa](./name-element-for-selectionset-format.md) element Określa nazwę, która jest używana do odwołania zestawu wyboru.</span><span class="sxs-lookup"><span data-stu-id="e61a1-131">The [Name](./name-element-for-selectionset-format.md) element specifies the name that is used to reference the selection set.</span></span>

- <span data-ttu-id="e61a1-132">[Typy](./types-element-for-selectionset-format.md) element określa typy .NET obiektów zestawu wyboru.</span><span class="sxs-lookup"><span data-stu-id="e61a1-132">The [Types](./types-element-for-selectionset-format.md) element specifies the .NET types of the objects of the selection set.</span></span> <span data-ttu-id="e61a1-133">(W ciągu formatowania pliki obiektów są określane przez ich typ architektury .NET.)</span><span class="sxs-lookup"><span data-stu-id="e61a1-133">(Within formatting files, objects are specified by their .NET type.)</span></span>

 <span data-ttu-id="e61a1-134">Następujące elementy XML są używane do określenia zestawu zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="e61a1-134">The following XML elements are used to specify a selection set.</span></span>

- <span data-ttu-id="e61a1-135">Następujący element Określa wybór skonfigurowany do używania w definicji widoku:</span><span class="sxs-lookup"><span data-stu-id="e61a1-135">The following element specifies the selection set to use in all the definitions of the view:</span></span>

    - [<span data-ttu-id="e61a1-136">Element SelectionSetName ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e61a1-136">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

    - [<span data-ttu-id="e61a1-137">Element SelectionSetName EntrySelectedBy dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="e61a1-137">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="e61a1-138">Następujące elementy określić zbiór używane zgodnie z definicją pojedynczy widok:</span><span class="sxs-lookup"><span data-stu-id="e61a1-138">The following elements specify the selection set used by a single view definition:</span></span>

    - [<span data-ttu-id="e61a1-139">Element SelectionSetName EntrySelectedBy dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e61a1-139">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="e61a1-140">Element SelectionSetName EntrySelectedBy dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="e61a1-140">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="e61a1-141">Element SelectionSetName EntrySelectedBy dla WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e61a1-141">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="e61a1-142">Element SelectionSetName EntrySelectedBy dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="e61a1-142">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- <span data-ttu-id="e61a1-143">Następujące elementy określić zbiór posługują się typowe i wyświetlać definicje sterowania:</span><span class="sxs-lookup"><span data-stu-id="e61a1-143">The following elements specify the selection set used by common and view control definitions:</span></span>

    - [<span data-ttu-id="e61a1-144">Element SelectionSetName EntrySelectedBy dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="e61a1-144">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [<span data-ttu-id="e61a1-145">Element SelectionSetName EntrySelectedBy dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="e61a1-145">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- <span data-ttu-id="e61a1-146">Następujące elementy określić zbiór używane podczas definiowania obiektu, który można rozwinąć:</span><span class="sxs-lookup"><span data-stu-id="e61a1-146">The following elements specify the selection set used when you define which object to expand:</span></span>

    - [<span data-ttu-id="e61a1-147">Element SelectionSetName EntrySelectedBy dla EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="e61a1-147">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="e61a1-148">Następujące elementy określić elementu set wyboru używany przez zaznaczenie warunków.</span><span class="sxs-lookup"><span data-stu-id="e61a1-148">The following elements specify the selection set used by selection conditions.</span></span>

    - [<span data-ttu-id="e61a1-149">Element SelectionSetName SelectionCondition dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="e61a1-149">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="e61a1-150">Element SelectionSetName SelectionCondition dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="e61a1-150">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [<span data-ttu-id="e61a1-151">Element SelectionSetName SelectionCondition dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="e61a1-151">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [<span data-ttu-id="e61a1-152">Element SelectionSetName SelectionCondition dla EntrySelectedBy dla EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="e61a1-152">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [<span data-ttu-id="e61a1-153">Element SelectionSetName SelectionCondition dla EntrySelectedBy dla ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e61a1-153">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [<span data-ttu-id="e61a1-154">Element SelectionSetName SelectionCondition dla EntrySelectedBy dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="e61a1-154">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="e61a1-155">Element SelectionSetName SelectionCondition dla EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e61a1-155">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [<span data-ttu-id="e61a1-156">Element SelectionSetName SelectionCondition dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="e61a1-156">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="e61a1-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e61a1-157">See Also</span></span>

[<span data-ttu-id="e61a1-158">SelectionSets</span><span class="sxs-lookup"><span data-stu-id="e61a1-158">SelectionSets</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="e61a1-159">SelectionSet</span><span class="sxs-lookup"><span data-stu-id="e61a1-159">SelectionSet</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="e61a1-160">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e61a1-160">Name</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="e61a1-161">Typy</span><span class="sxs-lookup"><span data-stu-id="e61a1-161">Types</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="e61a1-162">Pliki formatowania programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="e61a1-162">PowerShell Formatting Files</span></span>](./powershell-formatting-files.md)

[<span data-ttu-id="e61a1-163">Definiowanie warunków, gdy dane są wyświetlane</span><span class="sxs-lookup"><span data-stu-id="e61a1-163">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e61a1-164">Pisanie programu PowerShell, formatowanie i typy plików</span><span class="sxs-lookup"><span data-stu-id="e61a1-164">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
