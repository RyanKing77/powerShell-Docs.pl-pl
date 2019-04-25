---
title: Tworzenie widoku tabeli | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 862f942facafff6cea66c4f8f1040772c6a62ec3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066842"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="d9d76-102">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="d9d76-102">Creating a Table View</span></span>

<span data-ttu-id="d9d76-103">Widok tabeli wyświetla dane w co najmniej jedną kolumnę.</span><span class="sxs-lookup"><span data-stu-id="d9d76-103">A table view displays data in one or more columns.</span></span> <span data-ttu-id="d9d76-104">Każdy wiersz w tabeli reprezentuje obiekt .NET, a każda kolumna w tabeli reprezentuje właściwość obiektu lub wartość skryptu.</span><span class="sxs-lookup"><span data-stu-id="d9d76-104">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="d9d76-105">Można zdefiniować widoku tabeli, powoduje wyświetlenie wszystkich właściwości obiektu lub podzbiór właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="d9d76-105">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="d9d76-106">Wyświetlanie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="d9d76-106">A Table View Display</span></span>

<span data-ttu-id="d9d76-107">W poniższym przykładzie przedstawiono sposób wyświetlania środowiska Windows PowerShell [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) obiektu, który jest zwracany przez [Get-Service](/powershell/module/microsoft.powershell.management/get-service) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d9d76-107">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="d9d76-108">Dla tego obiektu, programu Windows PowerShell został zdefiniowany widok tabeli, która wyświetla `Status` właściwości `Name` właściwości (Ta właściwość jest właściwością aliasu dla `ServiceName` właściwości), a `DisplayName` właściwości.</span><span class="sxs-lookup"><span data-stu-id="d9d76-108">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="d9d76-109">Każdy wiersz w tabeli reprezentuje obiekt zwracany przez polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d9d76-109">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="d9d76-110">Definiowanie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="d9d76-110">Defining the Table View</span></span>

<span data-ttu-id="d9d76-111">Następujący kody XML pokazuje schemat tabeli widok do wyświetlania [System.Serviceprocess.Servicecontroller? Displayproperty = imię i nazwisko](/dotnet/api/System.ServiceProcess.ServiceController) obiektu.</span><span class="sxs-lookup"><span data-stu-id="d9d76-111">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="d9d76-112">Należy określić każdej właściwości, które mają być wyświetlane w widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="d9d76-112">You must specify each property that you want displayed in the table view.</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>8</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>18</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>38</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

<span data-ttu-id="d9d76-113">Następujące elementy XML są używane do definiowania widoku listy:</span><span class="sxs-lookup"><span data-stu-id="d9d76-113">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="d9d76-114">[Widoku](./view-element-format.md) element jest elementem nadrzędnym w widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="d9d76-114">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="d9d76-115">(Jest to tego samego elementu nadrzędnego dla listy, widoki kontrolne szerokiej i niestandardowych).</span><span class="sxs-lookup"><span data-stu-id="d9d76-115">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="d9d76-116">[Nazwa](./name-element-for-view-format.md) element Określa nazwę widoku.</span><span class="sxs-lookup"><span data-stu-id="d9d76-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="d9d76-117">Ten element jest wymagany dla wszystkich widoków.</span><span class="sxs-lookup"><span data-stu-id="d9d76-117">This element is required for all views.</span></span>

- <span data-ttu-id="d9d76-118">[ViewSelectedBy](./viewselectedby-element-format.md) element definiuje obiekty, które przy użyciu widoku.</span><span class="sxs-lookup"><span data-stu-id="d9d76-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="d9d76-119">Ten element jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="d9d76-119">This element is required.</span></span>

- <span data-ttu-id="d9d76-120">[GroupBy](./groupby-element-for-view-format.md) definiuje element (nie pokazane w tym przykładzie), gdy zostanie wyświetlona nowa grupa obiektów.</span><span class="sxs-lookup"><span data-stu-id="d9d76-120">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="d9d76-121">Nowa grupa została uruchomiona, zawsze wtedy, gdy zmieni się wartość określoną właściwość lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="d9d76-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="d9d76-122">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="d9d76-122">This element is optional.</span></span>

- <span data-ttu-id="d9d76-123">[Formantów](./controls-element-for-view-format.md) — element (nie pokazane w tym przykładzie) definiuje niestandardowe formanty, które są zdefiniowane w widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="d9d76-123">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="d9d76-124">Formanty zapewniają sposób, aby bardziej szczegółowo określić sposób wyświetlania danych.</span><span class="sxs-lookup"><span data-stu-id="d9d76-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="d9d76-125">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="d9d76-125">This element is optional.</span></span> <span data-ttu-id="d9d76-126">Widok można zdefiniować własne niestandardowe formanty, lub może używać wspólnych formantów, które mogą być używane przez dowolny widok w formatowaniu pliku.</span><span class="sxs-lookup"><span data-stu-id="d9d76-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="d9d76-127">Aby uzyskać więcej informacji na temat formantów niestandardowych, zobacz [Tworzenie niestandardowych formantów](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d9d76-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="d9d76-128">[HideTableHeaders](./hidetableheaders-element-format.md) — element (nie show w tym przykładzie) Określa tabelę nie będą widoczne dla wszystkich etykiet w górnej części tabeli.</span><span class="sxs-lookup"><span data-stu-id="d9d76-128">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="d9d76-129">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="d9d76-129">This element is optional.</span></span>

- <span data-ttu-id="d9d76-130">[Tablecontrol —](./tablecontrol-element-format.md) element, który definiuje informacje o nagłówku i wierszu tabeli.</span><span class="sxs-lookup"><span data-stu-id="d9d76-130">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="d9d76-131">Podobnie jak w innych widoków, widok tabeli wyświetlić wartości właściwości obiektu lub wartości generowanych przez skrypty.</span><span class="sxs-lookup"><span data-stu-id="d9d76-131">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="d9d76-132">Definiowanie nagłówków kolumn</span><span class="sxs-lookup"><span data-stu-id="d9d76-132">Defining Column Headers</span></span>

1. <span data-ttu-id="d9d76-133">[TableHeaders](./tableheaders-element-format.md) elementu i jego elementy podrzędne należy zdefiniować, co jest wyświetlane w górnej części tabeli.</span><span class="sxs-lookup"><span data-stu-id="d9d76-133">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="d9d76-134">[TableColumnHeader](./tablecolumnheader-element-format.md) element definiuje, co jest wyświetlane w górnej części kolumny tabeli.</span><span class="sxs-lookup"><span data-stu-id="d9d76-134">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="d9d76-135">Należy określić te elementy w kolejności, nagłówki wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="d9d76-135">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="d9d76-136">Nie ma żadnego limitu liczba tych elementu, którego można używać, ale liczba [TableColumnHeader](./tablecolumnheader-element-format.md) elementy w widoku tabeli musi być równa liczbie [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elementów, których używasz.</span><span class="sxs-lookup"><span data-stu-id="d9d76-136">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="d9d76-137">[Etykiety](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element Określa tekst, który jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="d9d76-137">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="d9d76-138">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="d9d76-138">This element is optional.</span></span>

4. <span data-ttu-id="d9d76-139">[Szerokość](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element Określa szerokość (w znakach) kolumny.</span><span class="sxs-lookup"><span data-stu-id="d9d76-139">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="d9d76-140">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="d9d76-140">This element is optional.</span></span>

5. <span data-ttu-id="d9d76-141">[Wyrównanie](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element określa sposób wyświetlania etykiety.</span><span class="sxs-lookup"><span data-stu-id="d9d76-141">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="d9d76-142">Etykiety można wyrównane do lewej, z prawej strony lub wyśrodkowany.</span><span class="sxs-lookup"><span data-stu-id="d9d76-142">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="d9d76-143">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="d9d76-143">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="d9d76-144">Definiowanie wiersze tabeli</span><span class="sxs-lookup"><span data-stu-id="d9d76-144">Defining the Table Rows</span></span>

<span data-ttu-id="d9d76-145">Widoki tabel może zapewnić co najmniej jedną definicję, które określają, jakie dane są wyświetlane w wierszach tabeli przy użyciu elementów podrzędnych [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="d9d76-145">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="d9d76-146">Należy zauważyć, że można określić wiele definicji dla wierszy w tabeli, ale nagłówki wierszy pozostają takie same, niezależnie od tego, jakie definicji wiersza jest używany.</span><span class="sxs-lookup"><span data-stu-id="d9d76-146">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="d9d76-147">Zazwyczaj tabela będzie mieć tylko jedną definicję.</span><span class="sxs-lookup"><span data-stu-id="d9d76-147">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="d9d76-148">W poniższym przykładzie, widok zawiera jednej definicji, który wyświetla wartości kilka właściwości [System.Diagnostics.Process? Displayproperty = imię i nazwisko](/dotnet/api/System.Diagnostics.Process) obiektu.</span><span class="sxs-lookup"><span data-stu-id="d9d76-148">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="d9d76-149">Widok tabeli można wyświetlić wartość właściwości lub wartość skryptu (nie pokazano w przykładzie), w jej wiersze.</span><span class="sxs-lookup"><span data-stu-id="d9d76-149">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

```xml
<TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>

```

<span data-ttu-id="d9d76-150">Następujące elementy XML może służyć do zapewnienia definicje dla wiersza:</span><span class="sxs-lookup"><span data-stu-id="d9d76-150">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="d9d76-151">[TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) elementu i jego elementy podrzędne należy zdefiniować, co jest wyświetlane w wierszach tabeli.</span><span class="sxs-lookup"><span data-stu-id="d9d76-151">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="d9d76-152">[TableRowEntry](./listentry-element-for-listcontrol-format.md) element zawiera definicję wiersza.</span><span class="sxs-lookup"><span data-stu-id="d9d76-152">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="d9d76-153">Co najmniej jeden [TableRowEntry](./listentry-element-for-listcontrol-format.md) jest wymagana; jednak nie ma żadnego limitu maksymalną liczbę elementów, które można dodać.</span><span class="sxs-lookup"><span data-stu-id="d9d76-153">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="d9d76-154">W większości przypadków widok będzie mieć tylko jedną definicję.</span><span class="sxs-lookup"><span data-stu-id="d9d76-154">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="d9d76-155">[EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element określa obiekty, które są wyświetlane zgodnie z definicją określonych.</span><span class="sxs-lookup"><span data-stu-id="d9d76-155">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="d9d76-156">Ten element jest opcjonalna i jest potrzebny tylko wtedy, gdy można zdefiniować wiele [TableRowEntry](./listentry-element-for-listcontrol-format.md) elementy wyświetlające różnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="d9d76-156">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="d9d76-157">[Opakować](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element określa, że tekst przekraczający szerokość kolumny są wyświetlane w następnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="d9d76-157">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="d9d76-158">Domyślnie tekst przekraczający szerokość kolumny zostały obcięte.</span><span class="sxs-lookup"><span data-stu-id="d9d76-158">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="d9d76-159">[TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element definiuje właściwości lub skryptów, których wartości są wyświetlane w wierszu.</span><span class="sxs-lookup"><span data-stu-id="d9d76-159">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="d9d76-160">[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element definiuje właściwość lub skryptu, którego wartość jest wyświetlana w kolumnie wiersza.</span><span class="sxs-lookup"><span data-stu-id="d9d76-160">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="d9d76-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element jest wymagany dla każdej kolumny wiersza.</span><span class="sxs-lookup"><span data-stu-id="d9d76-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="d9d76-162">Pierwszy wpis jest wyświetlany w pierwszej kolumnie, drugi wpis w drugiej kolumnie i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="d9d76-162">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="d9d76-163">[PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element Określa właściwość, którego wartość jest wyświetlana w wierszu.</span><span class="sxs-lookup"><span data-stu-id="d9d76-163">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="d9d76-164">Należy określić właściwość lub skryptu, ale nie możesz określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="d9d76-164">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="d9d76-165">[ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element określa skrypt, którego wartość jest wyświetlana w wierszu.</span><span class="sxs-lookup"><span data-stu-id="d9d76-165">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="d9d76-166">Należy określić skrypt lub właściwości, ale nie możesz określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="d9d76-166">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="d9d76-167">[FormatString](./label-element-for-listitem-for-listcontrol-format.md) element określa wzorzec formatu, który definiuje sposób wyświetlania wartości właściwości lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="d9d76-167">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="d9d76-168">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="d9d76-168">This element is optional.</span></span>

- <span data-ttu-id="d9d76-169">[Wyrównanie](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element określa sposób wyświetlania wartości właściwości lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="d9d76-169">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="d9d76-170">Wartość można wyrównane do lewej, z prawej strony lub wyśrodkowany.</span><span class="sxs-lookup"><span data-stu-id="d9d76-170">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="d9d76-171">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="d9d76-171">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="d9d76-172">Definiowanie obiektów, które widok tabeli</span><span class="sxs-lookup"><span data-stu-id="d9d76-172">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="d9d76-173">Istnieją dwa sposoby, aby zdefiniować, które obiekty platformy .NET przy użyciu widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="d9d76-173">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="d9d76-174">Możesz użyć [ViewSelectedBy](./viewselectedby-element-format.md) elementu, aby zdefiniować obiekty, które mogą być wyświetlane przez wszystkich definicji widoku lub możesz użyć [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elementu, aby zdefiniować, które obiekty są wyświetlane przez określonej definicji widoku.</span><span class="sxs-lookup"><span data-stu-id="d9d76-174">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="d9d76-175">W większości przypadków widok ma tylko jedną definicję, więc obiekty są zazwyczaj definiowane przez [ViewSelectedBy](./viewselectedby-element-format.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="d9d76-175">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="d9d76-176">Poniższy przykład pokazuje jak zdefiniować obiekty, które są wyświetlane przy użyciu widoku tabeli [ViewSelectedBy](./viewselectedby-element-format.md) i [TypeName](./typename-element-for-viewselectedby-format.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="d9d76-176">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="d9d76-177">Nie ma żadnego limitu liczby [TypeName](./typename-element-for-viewselectedby-format.md) elementów, że można określić i ich kolejność nie jest znaczący.</span><span class="sxs-lookup"><span data-stu-id="d9d76-177">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="d9d76-178">Następujące elementy XML może służyć do określenia obiektów, które są używane przez widok tabeli:</span><span class="sxs-lookup"><span data-stu-id="d9d76-178">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="d9d76-179">[ViewSelectedBy](./viewselectedby-element-format.md) element definiuje obiekty, które są wyświetlane w widoku listy.</span><span class="sxs-lookup"><span data-stu-id="d9d76-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="d9d76-180">[TypeName](./typename-element-for-viewselectedby-format.md) element określa obiekt .NET, który jest wyświetlany w widoku.</span><span class="sxs-lookup"><span data-stu-id="d9d76-180">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="d9d76-181">W pełni kwalifikowana nazwa typu .NET jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="d9d76-181">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="d9d76-182">Należy określić co najmniej jeden typ lub zaznaczenia, ustaw dla widoku, ale ma nie maksymalną liczbę elementów, które mogą być określone.</span><span class="sxs-lookup"><span data-stu-id="d9d76-182">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="d9d76-183">W poniższym przykładzie użyto [ViewSelectedBy](./viewselectedby-element-format.md) i [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="d9d76-183">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="d9d76-184">Używać zestawów wybór, w którym znajduje się zestaw powiązanych obiektów, które są wyświetlane przy użyciu wielu widoków, takich jak podczas definiowania widoku listy i widok tabeli dla tych samych obiektów.</span><span class="sxs-lookup"><span data-stu-id="d9d76-184">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="d9d76-185">Aby uzyskać więcej informacji o sposobie tworzenia zestawu wyboru, zobacz [Definiowanie zestawów wybór](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="d9d76-185">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="d9d76-186">Następujące elementy XML może służyć do określenia obiektów, które są używane przez widok listy:</span><span class="sxs-lookup"><span data-stu-id="d9d76-186">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="d9d76-187">[ViewSelectedBy](./viewselectedby-element-format.md) element definiuje obiekty, które są wyświetlane w widoku listy.</span><span class="sxs-lookup"><span data-stu-id="d9d76-187">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="d9d76-188">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element określa zestaw obiektów, które mogą być wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="d9d76-188">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="d9d76-189">Należy określić co najmniej jeden zbiór lub typu widoku, ale ma nie maksymalną liczbę elementów, które mogą być określone.</span><span class="sxs-lookup"><span data-stu-id="d9d76-189">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="d9d76-190">Poniższy przykład pokazuje jak zdefiniować obiekty wyświetlane przez określonej definicji widoku tabeli za pomocą [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="d9d76-190">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="d9d76-191">Ten element można określić nazwę typu .NET, obiektu, wybór zestaw obiektów, lub warunek wyboru, który określa, kiedy jest używane definicji.</span><span class="sxs-lookup"><span data-stu-id="d9d76-191">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="d9d76-192">Aby uzyskać więcej informacji o sposobie tworzenia wyboru warunków, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d9d76-192">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="d9d76-193">Podczas tworzenia wiele definicji widoku tabeli nie można określić innej kolumny nagłówków.</span><span class="sxs-lookup"><span data-stu-id="d9d76-193">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="d9d76-194">Można określić, co wyświetlane w wierszach tabeli, na przykład które obiekty są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="d9d76-194">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="d9d76-195">Następujące elementy XML może służyć do określenia obiektów, które są używane przez określone definicji widoku listy:</span><span class="sxs-lookup"><span data-stu-id="d9d76-195">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="d9d76-196">[EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element definiuje obiekty, które są wyświetlane przez definicję.</span><span class="sxs-lookup"><span data-stu-id="d9d76-196">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="d9d76-197">[TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element określa obiekt .NET, który jest wyświetlany przez definicję.</span><span class="sxs-lookup"><span data-stu-id="d9d76-197">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="d9d76-198">Korzystając z tego elementu, w pełni kwalifikowana nazwa typu .NET jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="d9d76-198">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="d9d76-199">Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru definicji, ale ma nie maksymalną liczbę elementów, które mogą być określone.</span><span class="sxs-lookup"><span data-stu-id="d9d76-199">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="d9d76-200">[SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) — element (niewyświetlany) określa zestaw obiektów, które mogą być wyświetlane przez tę definicję.</span><span class="sxs-lookup"><span data-stu-id="d9d76-200">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="d9d76-201">Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru definicji, ale ma nie maksymalną liczbę elementów, które mogą być określone.</span><span class="sxs-lookup"><span data-stu-id="d9d76-201">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="d9d76-202">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) — element (niewyświetlany) określa warunek, który musi istnieć dla tej definicji, które ma być używany.</span><span class="sxs-lookup"><span data-stu-id="d9d76-202">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="d9d76-203">Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru definicji, ale ma nie maksymalną liczbę elementów, które mogą być określone.</span><span class="sxs-lookup"><span data-stu-id="d9d76-203">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="d9d76-204">Aby uzyskać więcej informacji na temat definiowania warunków wybór zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d9d76-204">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="d9d76-205">Za pomocą ciągów formatu</span><span class="sxs-lookup"><span data-stu-id="d9d76-205">Using Format Strings</span></span>

<span data-ttu-id="d9d76-206">Ciągi formatowania można dodać do widoku, aby lepiej zdefiniować sposób wyświetlania danych.</span><span class="sxs-lookup"><span data-stu-id="d9d76-206">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="d9d76-207">Poniższy przykład pokazuje jak zdefiniować ciąg formatowania dla wartości `StartTime` właściwości.</span><span class="sxs-lookup"><span data-stu-id="d9d76-207">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="d9d76-208">Następujące elementy XML może służyć do określania wzorca format:</span><span class="sxs-lookup"><span data-stu-id="d9d76-208">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="d9d76-209">[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element definiuje właściwość lub skryptu, którego wartość jest wyświetlana w kolumnie wiersza.</span><span class="sxs-lookup"><span data-stu-id="d9d76-209">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="d9d76-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element jest wymagany dla każdej kolumny wiersza.</span><span class="sxs-lookup"><span data-stu-id="d9d76-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="d9d76-211">Pierwszy wpis jest wyświetlany w pierwszej kolumnie, drugi wpis w drugiej kolumnie i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="d9d76-211">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="d9d76-212">[PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element Określa właściwość, którego wartość jest wyświetlana w wierszu.</span><span class="sxs-lookup"><span data-stu-id="d9d76-212">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="d9d76-213">Należy określić właściwość lub skryptu, ale nie możesz określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="d9d76-213">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="d9d76-214">[FormatString](./label-element-for-listitem-for-listcontrol-format.md) element określa wzorzec formatu, który definiuje sposób wyświetlania wartości właściwości lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="d9d76-214">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="d9d76-215">W poniższym przykładzie `ToString` metoda jest wywoływana, aby sformatować wartość argumentu skryptu.</span><span class="sxs-lookup"><span data-stu-id="d9d76-215">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="d9d76-216">Skrypty można wywołać dowolnej metody obiektu.</span><span class="sxs-lookup"><span data-stu-id="d9d76-216">Scripts can call any method of an object.</span></span> <span data-ttu-id="d9d76-217">W związku z tym jeśli obiekt ma metodę `ToString`, który ma następujące parametry formatowania, skrypt może wywołać tej metody, aby sformatować wartość danych wyjściowych skryptu.</span><span class="sxs-lookup"><span data-stu-id="d9d76-217">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="d9d76-218">Następujący element XML może służyć do wywołania `ToString` metody:</span><span class="sxs-lookup"><span data-stu-id="d9d76-218">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="d9d76-219">[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element definiuje właściwość lub skryptu, którego wartość jest wyświetlana w kolumnie wiersza.</span><span class="sxs-lookup"><span data-stu-id="d9d76-219">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="d9d76-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element jest wymagany dla każdej kolumny wiersza.</span><span class="sxs-lookup"><span data-stu-id="d9d76-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="d9d76-221">Pierwszy wpis jest wyświetlany w pierwszej kolumnie, drugi wpis w drugiej kolumnie i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="d9d76-221">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="d9d76-222">[ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element określa skrypt, którego wartość jest wyświetlana w wierszu.</span><span class="sxs-lookup"><span data-stu-id="d9d76-222">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="d9d76-223">Należy określić skrypt lub właściwości, ale nie możesz określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="d9d76-223">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9d76-224">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9d76-224">See Also</span></span>

[<span data-ttu-id="d9d76-225">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="d9d76-225">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
