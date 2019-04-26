---
title: Formatowanie plików — omówienie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065737"
---
# <a name="formatting-file-overview"></a><span data-ttu-id="d9bb2-102">Omówienie plików formatujących</span><span class="sxs-lookup"><span data-stu-id="d9bb2-102">Formatting File Overview</span></span>

<span data-ttu-id="d9bb2-103">Format wyświetlania dla obiektów, które są zwracane przez polecenia (polecenia cmdlet, funkcji i skryptów) są definiowane za pomocą formatowania pliki (format.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="d9bb2-103">The display format for the objects that are returned by commands (cmdlets, functions, and scripts) are defined by using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="d9bb2-104">Niektóre z tych plików są dostarczane przez programu PowerShell, aby określić format wyświetlania tych obiektów zwróconych przez polecenia programu PowerShell — pod warunkiem, takich jak [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu zwróconego przez `Get-Process` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-104">Several of these files are provided by PowerShell to define the display format for those objects returned by PowerShell-provided commands, such as the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object returned by the `Get-Process` cmdlet.</span></span> <span data-ttu-id="d9bb2-105">Możesz również utworzyć własne niestandardowe pliki formatowania, aby zastąpić domyślny format wyświetlania lub, można napisać niestandardowy plik formatowania do określania sposobu wyświetlania obiektów zwróconych przez własne polecenia.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-105">However, you can also create your own custom formatting files to overwrite the default display formats or you can write a custom formatting file to define the display of objects returned by your own commands.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d9bb2-106">Pliki formatowania nie może określić elementy obiektu, które są zwracane do potoku.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-106">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="d9bb2-107">Gdy obiekt jest zwracany do potoku, wszystkie elementy członkowskie tego obiektu są dostępne, nawet jeśli niektóre nie są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-107">When an object is returned to the pipeline, all members of that object are available even if some are not displayed.</span></span>

<span data-ttu-id="d9bb2-108">Programu PowerShell używa danych w tych plikach formatowania, aby określić, co jest wyświetlane i sposobu formatowania wyświetlanych danych.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-108">PowerShell uses the data in these formatting files to determine what is displayed and how the displayed data is formatted.</span></span> <span data-ttu-id="d9bb2-109">Dane wyświetlane może zawierać właściwości obiektu lub wartość skryptu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-109">The displayed data can include the properties of an object or the value of a script.</span></span> <span data-ttu-id="d9bb2-110">Skrypty są używane, jeśli chcesz wyświetlić niektóre wartości, która nie jest dostępna bezpośrednio z właściwości obiektu, takie jak dodanie wartości dwie właściwości obiektu, a następnie wyświetlając Suma jako część danych.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-110">Scripts are used if you want to display some value that is not available directly from the properties of an object, such as adding the value of two properties of an object and then displaying the sum as a piece of data.</span></span> <span data-ttu-id="d9bb2-111">Formatowanie wyświetlanych danych odbywa się przez definiowanie widoków dla obiektów, które mają być wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-111">Formatting of the displayed data is done by defining views for the objects that you want to display.</span></span> <span data-ttu-id="d9bb2-112">Można zdefiniować pojedynczy widok dla każdego obiektu, można zdefiniować pojedynczy widok dla wielu obiektów lub można zdefiniować wiele widoków dla tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-112">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="d9bb2-113">Nie ma żadnego limitu liczby wyświetleń, które można zdefiniować.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-113">There is no limit to the number of views that you can define.</span></span>

## <a name="common-features-of-formatting-files"></a><span data-ttu-id="d9bb2-114">Często używane funkcje pliki formatowania</span><span class="sxs-lookup"><span data-stu-id="d9bb2-114">Common Features of Formatting Files</span></span>

<span data-ttu-id="d9bb2-115">Każdy plik formatowania można zdefiniować następujące składniki, które mogą być współużytkowane przez wszystkie widoki zdefiniowane w pliku:</span><span class="sxs-lookup"><span data-stu-id="d9bb2-115">Each formatting file can define the following components that can be shared across all the views defined by the file:</span></span>

- <span data-ttu-id="d9bb2-116">Domyślne ustawienia konfiguracji, takich jak tego, czy dane wyświetlane w wierszach tabel będą wyświetlane w następnym wierszu, jeśli danych jest dłuższa niż szerokość kolumny.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-116">Default configuration setting, such as whether the data displayed in the rows of tables will be displayed on the next line if the data is longer than the width of the column.</span></span> <span data-ttu-id="d9bb2-117">Aby uzyskać więcej informacji o tych ustawieniach, zobacz [Definiowanie wspólne ustawienia konfiguracyjne](./defining-common-configuration-features.md).</span><span class="sxs-lookup"><span data-stu-id="d9bb2-117">For more information about these settings, see [Defining Common Configuration Settings](./defining-common-configuration-features.md).</span></span>

- <span data-ttu-id="d9bb2-118">Ustawia obiekty, które mogą być wyświetlane przez jeden z widoków formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-118">Sets of objects that can be displayed by any of the views of the formatting file.</span></span> <span data-ttu-id="d9bb2-119">Aby uzyskać więcej informacji na temat tych zestawów (nazywane *zestawami zaznaczenia*), zobacz [Definiowanie ustawia z obiektów](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="d9bb2-119">For more information about these sets (referred to as *selection sets*), see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

- <span data-ttu-id="d9bb2-120">Wspólnych formantów, które mogą być używane przez wszystkie widoki formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-120">Common controls that can be used by all the views of the formatting file.</span></span> <span data-ttu-id="d9bb2-121">Formanty zapewniają bardziej precyzyjną kontrolę na sposób wyświetlania danych.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-121">Controls give you finer control on how data is displayed.</span></span> <span data-ttu-id="d9bb2-122">Aby uzyskać więcej informacji na temat formantów, zobacz [Definiowanie kontrolek niestandardowych](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d9bb2-122">For more information about controls, see [Defining Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="formatting-views"></a><span data-ttu-id="d9bb2-123">Formatowanie widoków</span><span class="sxs-lookup"><span data-stu-id="d9bb2-123">Formatting Views</span></span>

<span data-ttu-id="d9bb2-124">Widoki formatowania można wyświetlić obiekty w formacie tabeli, format listy, formacie szerokim i formatu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-124">Formatting views can display objects in a table format, list format, wide format, and custom format.</span></span> <span data-ttu-id="d9bb2-125">W większości przypadków każdego formatowania definicja jest określana przez zbiór znaczników XML, które opisują widoku.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-125">For the most part, each formatting definition is described by a set of XML tags that describe the view.</span></span> <span data-ttu-id="d9bb2-126">Każdy widok zawiera nazwę widoku, obiekty korzystające z tego widoku i elementy widoku, takie jak informacje wierszy i kolumn w widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-126">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="d9bb2-127">Tabela Wyświetl listę właściwości obiektu lub wartość bloku skryptu w co najmniej jedną kolumnę.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-127">Table View Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="d9bb2-128">Każda kolumna reprezentuje pojedynczej właściwości obiektu lub wartość skryptu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-128">Each column represents a single property of the object or a script value.</span></span> <span data-ttu-id="d9bb2-129">Można zdefiniować wyświetlony widok tabeli wszystkich właściwości obiektu, podzbiór właściwości obiektu lub kombinacji właściwości i wartości skryptu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-129">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script values.</span></span> <span data-ttu-id="d9bb2-130">Każdy wiersz w tabeli reprezentuje zwrócony obiekt.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-130">Each row of the table represents a returned object.</span></span> <span data-ttu-id="d9bb2-131">Tworzenie widoku tabeli jest bardzo podobny do kiedy przekazać obiekt, do którego `Format-Table` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-131">Creating a table view is very similar to when you pipe an object to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="d9bb2-132">Aby uzyskać więcej informacji na temat tego widoku, zobacz [widok tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="d9bb2-132">For more information about this view, see [Table View](./creating-a-table-view.md).</span></span>

<span data-ttu-id="d9bb2-133">Wyświetl listę widok zawiera listę właściwości obiektu lub wartość skryptu w jednej kolumnie.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-133">List View Lists the properties of an object or a script value in a single column.</span></span> <span data-ttu-id="d9bb2-134">Każdy wiersz listy zawiera opcjonalną etykietę lub nazwę właściwości, a następnie według wartości właściwości lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-134">Each row of the list displays an optional label or the property name followed by the value of the property or script.</span></span> <span data-ttu-id="d9bb2-135">Tworzenie widoku listy jest bardzo podobny do przekazanie w potoku obiektu `Format-List` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-135">Creating a list view is very similar to piping an object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="d9bb2-136">Aby uzyskać więcej informacji na temat tego widoku, zobacz [widok listy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="d9bb2-136">For more information about this view, see [List View](./creating-a-list-view.md).</span></span>

<span data-ttu-id="d9bb2-137">Szerokie wymieniono pojedynczej właściwości obiektu lub wartość skryptu w co najmniej jedną kolumnę.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-137">Wide View Lists a single property of an object or a script value in one or more columns.</span></span> <span data-ttu-id="d9bb2-138">Nie ma etykiety lub nagłówek dla tego widoku.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-138">There is no label or header for this view.</span></span> <span data-ttu-id="d9bb2-139">Tworzenie szerokiej widoku jest bardzo podobny do przekazanie w potoku obiektu `Format-Wide` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-139">Creating a wide view is very similar to piping an object to the `Format-Wide` cmdlet.</span></span> <span data-ttu-id="d9bb2-140">Aby uzyskać więcej informacji na temat tego widoku, zobacz [szerokie](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="d9bb2-140">For more information about this view, see [Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="d9bb2-141">Widok niestandardowy przedstawia widok można dostosować właściwości obiektów lub wartości skryptu niezgodny sztywne struktury widoki tabel, widoków listy lub szerokie widoków.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-141">Custom View Displays a customizable view of object properties or script values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="d9bb2-142">Można zdefiniować autonomiczny widok niestandardowy, lub można zdefiniować widoku niestandardowego, który jest używany przez inny widok, takiego jak widok tabeli lub widoku listy.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-142">You can define a stand-alone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="d9bb2-143">Tworzenie widoku niestandardowego jest bardzo podobny do przekazanie w potoku obiektu `Format-Custom` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-143">Creating a custom view is very similar to piping an object to the `Format-Custom` cmdlet.</span></span> <span data-ttu-id="d9bb2-144">Aby uzyskać więcej informacji na temat tego widoku, zobacz [widok niestandardowy](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d9bb2-144">For more information about this view, see [Custom View](./creating-custom-controls.md).</span></span>

## <a name="components-of-a-view"></a><span data-ttu-id="d9bb2-145">Składnikami widoku</span><span class="sxs-lookup"><span data-stu-id="d9bb2-145">Components of a View</span></span>

<span data-ttu-id="d9bb2-146">Poniższe przykłady XML pokazują podstawowe składniki XML w widoku.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-146">The following XML examples show the basic XML components of a view.</span></span> <span data-ttu-id="d9bb2-147">Poszczególne elementy XML różnią się w zależności od tego, w którym widok ma zostać utworzona, ale podstawowe składniki widoków są takie same.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-147">The individual XML elements vary depending on which view you want to create, but the basic components of the views are all the same.</span></span>

<span data-ttu-id="d9bb2-148">Na początek z każdego widoku ma `Name` element, który określa przyjazną dla użytkownika nazwę służący do odwoływać się do widoku.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-148">To start with, each view has a `Name` element that specifies a user friendly name that is used to reference the view.</span></span> <span data-ttu-id="d9bb2-149">`ViewSelectedBy` element, który definiuje obiekty .NET, które są wyświetlane w widoku i *kontroli* element, który definiuje widoku.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-149">a `ViewSelectedBy` element that defines which .NET objects are displayed by the view, and a *control* element that defines the view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <ListControl>...</ListControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <WideControl>...</WideControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <CustomControl>...</CustomControl>
  </View>
</ViewDefinitions>

```

<span data-ttu-id="d9bb2-150">W elemencie kontrolki można zdefiniować co najmniej jeden *wpis* elementów.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-150">Within the control element, you can define one or more *entry* elements.</span></span> <span data-ttu-id="d9bb2-151">Jeśli używasz wielu definicjach, należy określić, które obiekty .NET Użyj Każda definicja.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-151">If you use multiple definitions, you must specify which .NET objects use each definition.</span></span> <span data-ttu-id="d9bb2-152">Tylko jeden wpis z tylko jedną definicję, jest potrzebna dla każdego formantu.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-152">Typically only one entry, with only one definition, is needed for each control.</span></span>

```xml
<ListControl>
  <ListEntries>
    <ListEntry>
      <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
  </ListEntries>
</ListControl>

```

<span data-ttu-id="d9bb2-153">W ramach każdego wpisu elementu widoku, należy określić *elementu* elementy, które definiują właściwości platformy .NET lub skrypty, które są wyświetlane w tym widoku.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-153">Within each entry element of a view, you specify the *item* elements that define the .NET properties or scripts that are displayed by that view.</span></span>

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

<span data-ttu-id="d9bb2-154">Jak pokazano w poprzednich przykładach, formatowania plik może zawierać wiele widoków, widok może zawierać wiele definicji i każda definicja może zawierać wiele elementów.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-154">As shown in the preceding examples, the formatting file can contain multiple views, a view can contain multiple definitions, and each definition can contain multiple items.</span></span>

## <a name="example-of-a-table-view"></a><span data-ttu-id="d9bb2-155">Przykładowy widok tabeli</span><span class="sxs-lookup"><span data-stu-id="d9bb2-155">Example of a Table View</span></span>

<span data-ttu-id="d9bb2-156">Poniższy przykład pokazuje tagów XML używanych do definiowania widoku tabeli, która zawiera dwie kolumny.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-156">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="d9bb2-157">[ViewDefinitions](./viewdefinitions-element-format.md) element jest elementem kontenera dla wszystkich widoków, które są zdefiniowane w pliku formatowania.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-157">The [ViewDefinitions](./viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="d9bb2-158">[Widoku](./view-element-format.md) element definiuje określonej tabeli, lista, szeroki lub niestandardowy widok.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-158">The [View](./view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="d9bb2-159">W ramach każdej [widoku](./view-element-format.md) elementu [nazwa](./name-element-for-view-format.md) element Określa nazwę widoku, [ViewSelectedBy](./viewselectedby-element-format.md) element definiuje obiekty korzystające z tego widoku i różnic kontroluje elementy (takie jak `TableControl` pokazano w poniższym przykładzie element) określ typ widoku.</span><span class="sxs-lookup"><span data-stu-id="d9bb2-159">Within each [View](./view-element-format.md) element, the [Name](./name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element shown in the following example) define the type of the view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="d9bb2-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9bb2-160">See Also</span></span>

[<span data-ttu-id="d9bb2-161">Tworzenie widoku listy</span><span class="sxs-lookup"><span data-stu-id="d9bb2-161">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="d9bb2-162">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="d9bb2-162">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d9bb2-163">Tworzenie szerokiej widoku</span><span class="sxs-lookup"><span data-stu-id="d9bb2-163">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d9bb2-164">Tworzenie niestandardowych formantów</span><span class="sxs-lookup"><span data-stu-id="d9bb2-164">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="d9bb2-165">Pisanie programu PowerShell, formatowanie i typy plików</span><span class="sxs-lookup"><span data-stu-id="d9bb2-165">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
