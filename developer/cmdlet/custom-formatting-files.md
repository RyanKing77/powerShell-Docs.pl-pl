---
title: Niestandardowe formatowanie plików | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068304"
---
# <a name="custom-formatting-files"></a><span data-ttu-id="16fb8-102">Niestandardowe pliki formatujące</span><span class="sxs-lookup"><span data-stu-id="16fb8-102">Custom Formatting Files</span></span>

<span data-ttu-id="16fb8-103">Format wyświetlania dla obiektów zwróconych przez polecenia cmdlet, funkcji i skryptów są definiowane za pomocą formatowania pliki (format.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="16fb8-103">The display format for the objects returned by cmdlets, functions, and scripts are defined using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="16fb8-104">Niektóre z tych plików są dostarczane przez programu Windows PowerShell, aby zdefiniować domyślny format wyświetlania tych obiektów zwróconych przez polecenia cmdlet programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="16fb8-104">Several of these files are provided by Windows PowerShell to define the default display format for those objects returned by Windows PowerShell cmdlets.</span></span> <span data-ttu-id="16fb8-105">Jednak można również utworzyć własne niestandardowe pliki formatowania, aby zastąpić domyślny format wyświetlania lub do określania sposobu wyświetlania obiektów zwróconych przez własne polecenia.</span><span class="sxs-lookup"><span data-stu-id="16fb8-105">However, you can also create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

<span data-ttu-id="16fb8-106">Programu Windows PowerShell wykorzystuje dane w tych plikach formatowania, aby określić, co jest wyświetlane, i jak dane są sformatowane.</span><span class="sxs-lookup"><span data-stu-id="16fb8-106">Windows PowerShell uses the data in these formatting files to determine what is displayed and how the data is formatted.</span></span> <span data-ttu-id="16fb8-107">Dane wyświetlane może zawierać właściwości obiektu lub wartość blok skryptu.</span><span class="sxs-lookup"><span data-stu-id="16fb8-107">The displayed data can include the properties of an object or the value of a script block.</span></span>  <span data-ttu-id="16fb8-108">Bloki skryptu są używane, jeśli chcesz wyświetlić niektóre wartości, która nie jest dostępna bezpośrednio z właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="16fb8-108">Script blocks are used if you want to display some value that is not available directly from the properties of an object.</span></span> <span data-ttu-id="16fb8-109">Na przykład można ulepszyć dwie właściwości obiektu i sumy są wyświetlane jako osobne elementu danych.</span><span class="sxs-lookup"><span data-stu-id="16fb8-109">For example, you may want to add the value of two properties of an object and display the sum as a separate piece of data.</span></span> <span data-ttu-id="16fb8-110">Podczas pisania własnego formatowania pliku, należy zdefiniować *widoków* obiektów, które mają być wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="16fb8-110">When you write your own formatting file, you will need to define *views* for the objects that you want to display.</span></span> <span data-ttu-id="16fb8-111">Można zdefiniować pojedynczy widok dla każdego obiektu, można zdefiniować pojedynczy widok dla wielu obiektów lub można zdefiniować wiele widoków dla tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="16fb8-111">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="16fb8-112">Nie ma żadnego limitu liczby wyświetleń, które można zdefiniować.</span><span class="sxs-lookup"><span data-stu-id="16fb8-112">There is no limit to the number of views that you can define.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="16fb8-113">Pliki formatowania nie może określić elementy obiektu, które są zwracane do potoku.</span><span class="sxs-lookup"><span data-stu-id="16fb8-113">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="16fb8-114">Gdy obiekt jest zwracany do potoku, wszystkie elementy członkowskie tego obiektu są dostępne.</span><span class="sxs-lookup"><span data-stu-id="16fb8-114">When an object is returned to the pipeline, all members of that object are available.</span></span>

## <a name="format-views"></a><span data-ttu-id="16fb8-115">Format widoków</span><span class="sxs-lookup"><span data-stu-id="16fb8-115">Format Views</span></span>

<span data-ttu-id="16fb8-116">Widoki formatowania można wyświetlić obiekty w postaci tabeli, format listy, formacie szerokim i formatu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="16fb8-116">Formatting views can display objects in a table format, a list format, a wide format, and a custom format.</span></span> <span data-ttu-id="16fb8-117">W większości przypadków każdego formatowania definicja jest określana przez zbiór znaczników XML, zawierających opis widoku.</span><span class="sxs-lookup"><span data-stu-id="16fb8-117">For the most part, each formatting definition is described by a set of XML tags that describe a view.</span></span> <span data-ttu-id="16fb8-118">Każdy widok zawiera nazwę widoku, obiekty korzystające z tego widoku i elementy widoku, takie jak informacje wierszy i kolumn w widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="16fb8-118">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="16fb8-119">Dostępne są następujące widoki.</span><span class="sxs-lookup"><span data-stu-id="16fb8-119">The following views are available.</span></span>

<span data-ttu-id="16fb8-120">Widok tabeli przedstawiono listę właściwości obiektu lub wartość bloku skryptu w co najmniej jedną kolumnę.</span><span class="sxs-lookup"><span data-stu-id="16fb8-120">Table view Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="16fb8-121">Każda kolumna reprezentuje właściwość obiektu lub wartość bloku skryptu.</span><span class="sxs-lookup"><span data-stu-id="16fb8-121">Each column represents a property of the object or a script block value.</span></span> <span data-ttu-id="16fb8-122">Można zdefiniować wyświetlony widok tabeli wszystkich właściwości obiektu, podzbiór właściwości obiektu lub kombinacji właściwości i wartości bloku skryptu.</span><span class="sxs-lookup"><span data-stu-id="16fb8-122">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script block values.</span></span> <span data-ttu-id="16fb8-123">Każdy wiersz w tabeli reprezentuje zwrócony obiekt.</span><span class="sxs-lookup"><span data-stu-id="16fb8-123">Each row of the table represents a returned object.</span></span> <span data-ttu-id="16fb8-124">Aby uzyskać więcej informacji na temat tego widoku, zobacz [widok tabeli](../format/creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="16fb8-124">For more information about this view, see [Table View](../format/creating-a-table-view.md).</span></span>

<span data-ttu-id="16fb8-125">Widok listy zawiera listę właściwości obiektu lub wartość bloku skryptu w jednej kolumnie.</span><span class="sxs-lookup"><span data-stu-id="16fb8-125">List view Lists the properties of an object or a script block value in a single column.</span></span> <span data-ttu-id="16fb8-126">Każdy wiersz listy zawiera opcjonalną etykietę lub nazwę właściwości, a następnie wartość właściwości lub skrypt bloku.</span><span class="sxs-lookup"><span data-stu-id="16fb8-126">Each row of the list displays an optional label or the property name followed by the value of the property or script block.</span></span> <span data-ttu-id="16fb8-127">Aby uzyskać więcej informacji na temat tego widoku, zobacz [widok listy](../format/creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="16fb8-127">For more information about this view, see [List View](../format/creating-a-list-view.md).</span></span>

<span data-ttu-id="16fb8-128">Szerokie wymieniono pojedynczej właściwości obiektu lub wartość bloku skryptu w co najmniej jedną kolumnę.</span><span class="sxs-lookup"><span data-stu-id="16fb8-128">Wide view Lists a single property of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="16fb8-129">Nie ma etykiety lub nagłówek dla tego widoku.</span><span class="sxs-lookup"><span data-stu-id="16fb8-129">There is no label or header for this view.</span></span> <span data-ttu-id="16fb8-130">Aby uzyskać więcej informacji na temat tego widoku, zobacz [szerokie](../format/creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="16fb8-130">For more information about this view, see [Wide View](../format/creating-a-wide-view.md).</span></span>

<span data-ttu-id="16fb8-131">Widok niestandardowy przedstawia widok można dostosować właściwości obiektów lub wartości bloku skryptu niezgodny sztywne struktury widoki tabel, widoków listy lub szerokie widoków.</span><span class="sxs-lookup"><span data-stu-id="16fb8-131">Custom view Displays a customizable view of object properties or script block values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="16fb8-132">Można zdefiniować niestandardowy widok autonomiczny lub można zdefiniować widoku niestandardowego, który jest używany przez inny widok, takiego jak widok tabeli lub widoku listy.</span><span class="sxs-lookup"><span data-stu-id="16fb8-132">You can define a standalone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="16fb8-133">Aby uzyskać więcej informacji na temat tego widoku, zobacz [widok niestandardowy](../format/creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="16fb8-133">For more information about this view, see [Custom View](../format/creating-custom-controls.md).</span></span>

## <a name="view-xml-elements"></a><span data-ttu-id="16fb8-134">Wyświetl elementy XML</span><span class="sxs-lookup"><span data-stu-id="16fb8-134">View XML Elements</span></span>

<span data-ttu-id="16fb8-135">Poniższy przykład pokazuje tagów XML używanych do definiowania widoku tabeli, która zawiera dwie kolumny.</span><span class="sxs-lookup"><span data-stu-id="16fb8-135">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="16fb8-136">[ViewDefinitions](../format/viewdefinitions-element-format.md) element jest elementem kontenera dla wszystkich widoków, które są zdefiniowane w pliku formatowania.</span><span class="sxs-lookup"><span data-stu-id="16fb8-136">The [ViewDefinitions](../format/viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="16fb8-137">[Widoku](../format/view-element-format.md) element definiuje określonej tabeli, lista, szeroki lub niestandardowy widok.</span><span class="sxs-lookup"><span data-stu-id="16fb8-137">The [View](../format/view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="16fb8-138">W ramach każdego widoku [nazwa](../format/name-element-for-view-format.md) element Określa nazwę widoku, [ViewSelectedBy](../format/viewselectedby-element-format.md) element definiuje obiekty korzystające z tego widoku i elementy innej kontrolki (takie jak `TableControl` element) definiują format widoku.</span><span class="sxs-lookup"><span data-stu-id="16fb8-138">Within each view, the [Name](../format/name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](../format/viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element) define the format of the view.</span></span>

```xml
ViewDefinitions
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

## <a name="see-also"></a><span data-ttu-id="16fb8-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16fb8-139">See Also</span></span>

[<span data-ttu-id="16fb8-140">Widok tabeli</span><span class="sxs-lookup"><span data-stu-id="16fb8-140">Table View</span></span>](../format/creating-a-table-view.md)

[<span data-ttu-id="16fb8-141">Widok listy</span><span class="sxs-lookup"><span data-stu-id="16fb8-141">List View</span></span>](../format/creating-a-list-view.md)

[<span data-ttu-id="16fb8-142">Szerokie</span><span class="sxs-lookup"><span data-stu-id="16fb8-142">Wide View</span></span>](../format/creating-a-wide-view.md)

[<span data-ttu-id="16fb8-143">Widok niestandardowy</span><span class="sxs-lookup"><span data-stu-id="16fb8-143">Custom View</span></span>](../format/creating-custom-controls.md)

[<span data-ttu-id="16fb8-144">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="16fb8-144">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
