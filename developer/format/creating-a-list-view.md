---
title: Tworzenie widoku listy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066859"
---
# <a name="creating-a-list-view"></a><span data-ttu-id="eef4c-102">Tworzenie widoku listy</span><span class="sxs-lookup"><span data-stu-id="eef4c-102">Creating a List View</span></span>

<span data-ttu-id="eef4c-103">Widok listy wyświetla dane w jednej kolumnie (w kolejności sekwencyjnej).</span><span class="sxs-lookup"><span data-stu-id="eef4c-103">A list view displays data in a single column (in sequential order).</span></span> <span data-ttu-id="eef4c-104">Dane wyświetlane na liście można wartość właściwości platformy .NET lub wartość skryptu.</span><span class="sxs-lookup"><span data-stu-id="eef4c-104">The data displayed in the list can be the value of a .NET property or the value of a script.</span></span>

## <a name="a-list-view-display"></a><span data-ttu-id="eef4c-105">Wyświetlanie widoku listy</span><span class="sxs-lookup"><span data-stu-id="eef4c-105">A List View Display</span></span>

<span data-ttu-id="eef4c-106">Następujące dane wyjściowe pokazują, jak środowiska Windows PowerShell Wyświetla właściwości [System.Serviceprocess.Servicecontroller? Displayproperty = imię i nazwisko](/dotnet/api/System.ServiceProcess.ServiceController) obiekty, które są zwracane przez [Get-Service](/powershell/module/microsoft.powershell.management/get-service) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eef4c-106">The following output shows how Windows PowerShell displays the properties of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects that are returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="eef4c-107">W tym przykładzie trzy obiekty zostały zwrócone z każdym obiektem oddzielone z poprzednim obiektu pusty wiersz.</span><span class="sxs-lookup"><span data-stu-id="eef4c-107">In this example, three objects were returned, with each object separated from the preceding object by a blank line.</span></span>

```powershell
Get-Service | format-list
```

```output
Name                : AEADIFilters
DisplayName         : Andrea ADI Filters Service
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess

Name                : AeLookupSvc
DisplayName         : Application Experience
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32ShareProcess

Name                : AgereModemAudio
DisplayName         : Agere Modem Call Progress Audio
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess
...
```

## <a name="defining-the-list-view"></a><span data-ttu-id="eef4c-108">Definiowanie widoku listy</span><span class="sxs-lookup"><span data-stu-id="eef4c-108">Defining the List View</span></span>

<span data-ttu-id="eef4c-109">Następujący kody XML pokazuje schematu widok listy do wyświetlania kilka właściwości [System.Serviceprocess.Servicecontroller? Displayproperty = imię i nazwisko](/dotnet/api/System.ServiceProcess.ServiceController) obiektu.</span><span class="sxs-lookup"><span data-stu-id="eef4c-109">The following XML shows the list view schema for displaying several properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="eef4c-110">Należy określić każdej właściwości, które mają być wyświetlane w widoku listy.</span><span class="sxs-lookup"><span data-stu-id="eef4c-110">You must specify each property that you want displayed in the list view.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

<span data-ttu-id="eef4c-111">Następujące elementy XML są używane do definiowania widoku listy:</span><span class="sxs-lookup"><span data-stu-id="eef4c-111">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="eef4c-112">[Widoku](./view-element-format.md) element jest elementem nadrzędnym elementu widoku listy.</span><span class="sxs-lookup"><span data-stu-id="eef4c-112">The [View](./view-element-format.md) element is the parent element of the list view.</span></span> <span data-ttu-id="eef4c-113">(Jest to tego samego elementu nadrzędnego dla tabeli, widoki kontrolne szerokiej i niestandardowych).</span><span class="sxs-lookup"><span data-stu-id="eef4c-113">(This is the same parent element for the table, wide, and custom control views.)</span></span>

- <span data-ttu-id="eef4c-114">[Nazwa](./name-element-for-view-format.md) element Określa nazwę widoku.</span><span class="sxs-lookup"><span data-stu-id="eef4c-114">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="eef4c-115">Ten element jest wymagany dla wszystkich widoków.</span><span class="sxs-lookup"><span data-stu-id="eef4c-115">This element is required for all views.</span></span>

- <span data-ttu-id="eef4c-116">[ViewSelectedBy](./viewselectedby-element-format.md) element definiuje obiekty, które przy użyciu widoku.</span><span class="sxs-lookup"><span data-stu-id="eef4c-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="eef4c-117">Ten element jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="eef4c-117">This element is required.</span></span>

- <span data-ttu-id="eef4c-118">[GroupBy](./groupby-element-for-view-format.md) element definiuje, gdy zostanie wyświetlona nowa grupa obiektów.</span><span class="sxs-lookup"><span data-stu-id="eef4c-118">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="eef4c-119">Nowa grupa została uruchomiona, zawsze wtedy, gdy zmieni się wartość określoną właściwość lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="eef4c-119">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="eef4c-120">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="eef4c-120">This element is optional.</span></span>

- <span data-ttu-id="eef4c-121">[Formantów](./controls-element-for-view-format.md) element definiuje niestandardowe formanty, które są zdefiniowane w widoku listy.</span><span class="sxs-lookup"><span data-stu-id="eef4c-121">The [Controls](./controls-element-for-view-format.md) element defines the custom controls that are defined by the list view.</span></span> <span data-ttu-id="eef4c-122">Formanty zapewniają sposób, aby bardziej szczegółowo określić sposób wyświetlania danych.</span><span class="sxs-lookup"><span data-stu-id="eef4c-122">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="eef4c-123">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="eef4c-123">This element is optional.</span></span> <span data-ttu-id="eef4c-124">Widok można zdefiniować własne niestandardowe formanty, lub może używać wspólnych formantów, które mogą być używane przez dowolny widok w formatowaniu pliku.</span><span class="sxs-lookup"><span data-stu-id="eef4c-124">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="eef4c-125">Aby uzyskać więcej informacji na temat formantów niestandardowych, zobacz [Tworzenie niestandardowych formantów](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="eef4c-125">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="eef4c-126">[Elementu ListControl](./listcontrol-element-format.md) element definiuje, co jest wyświetlane w widoku oraz sposób jego sformatowania.</span><span class="sxs-lookup"><span data-stu-id="eef4c-126">The [ListControl](./listcontrol-element-format.md) element defines what is displayed in the view and how it is formatted.</span></span> <span data-ttu-id="eef4c-127">Podobnie jak w innych widoków, widok listy lub można wyświetlić wartości właściwości obiektu wartości generowane przez skrypt.</span><span class="sxs-lookup"><span data-stu-id="eef4c-127">Similar to all other views, a list view can display the values of object properties or values generated by script.</span></span>

<span data-ttu-id="eef4c-128">Na przykład kompletny plik formatowania, który definiuje widoku prostej listy zobacz [widok listy (Basic)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="eef4c-128">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-list-view"></a><span data-ttu-id="eef4c-129">Podając w definicji widoku listy</span><span class="sxs-lookup"><span data-stu-id="eef4c-129">Providing Definitions for Your List View</span></span>

<span data-ttu-id="eef4c-130">Widoki list można podać jeden lub więcej definicji przy użyciu elementów podrzędnych [elementu ListControl](./listcontrol-element-format.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="eef4c-130">List views can provide one or more definitions by using the child elements of the [ListControl](./listcontrol-element-format.md) element.</span></span> <span data-ttu-id="eef4c-131">Zazwyczaj widok będzie mieć tylko jedną definicję.</span><span class="sxs-lookup"><span data-stu-id="eef4c-131">Typically, a view will have only one definition.</span></span> <span data-ttu-id="eef4c-132">W poniższym przykładzie, widok zawiera jednej definicji, który wyświetla kilka właściwości [System.Diagnostics.Process? Displayproperty = imię i nazwisko](/dotnet/api/System.Diagnostics.Process) obiektu.</span><span class="sxs-lookup"><span data-stu-id="eef4c-132">In the following example, the view provides a single definition that displays several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="eef4c-133">Wartość właściwości lub wartość skryptu (nie pokazano w przykładzie), można wyświetlić widoku listy.</span><span class="sxs-lookup"><span data-stu-id="eef4c-133">A list view can display the value of a property or the value of a script (not shown in the example).</span></span>

```xml
<ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>

```

<span data-ttu-id="eef4c-134">Następujące elementy XML może służyć do zapewnienia definicji widoku listy:</span><span class="sxs-lookup"><span data-stu-id="eef4c-134">The following XML elements can be used to provide definitions for a list view:</span></span>

- <span data-ttu-id="eef4c-135">[Elementu ListControl](./listcontrol-element-format.md) elementu i jego elementy podrzędne należy zdefiniować, co jest wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="eef4c-135">The [ListControl](./listcontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="eef4c-136">[ListEntries](./listentries-element-for-listcontrol-format.md) element udostępnia definicji widoku.</span><span class="sxs-lookup"><span data-stu-id="eef4c-136">The [ListEntries](./listentries-element-for-listcontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="eef4c-137">W większości przypadków widok będzie mieć tylko jedną definicję.</span><span class="sxs-lookup"><span data-stu-id="eef4c-137">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="eef4c-138">Ten element jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="eef4c-138">This element is required.</span></span>

- <span data-ttu-id="eef4c-139">[ListEntry](./listentry-element-for-listcontrol-format.md) element zawiera definicję widoku.</span><span class="sxs-lookup"><span data-stu-id="eef4c-139">The [ListEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="eef4c-140">Co najmniej jeden [ListEntry](./listentry-element-for-listcontrol-format.md) jest wymagana; jednak nie ma żadnego limitu maksymalną liczbę elementów, które można dodać.</span><span class="sxs-lookup"><span data-stu-id="eef4c-140">At least one [ListEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="eef4c-141">W większości przypadków widok będzie mieć tylko jedną definicję.</span><span class="sxs-lookup"><span data-stu-id="eef4c-141">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="eef4c-142">[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element określa obiekty, które są wyświetlane zgodnie z definicją określonych.</span><span class="sxs-lookup"><span data-stu-id="eef4c-142">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="eef4c-143">Ten element jest opcjonalna i jest potrzebny tylko wtedy, gdy można zdefiniować wiele [ListEntry](./listentry-element-for-listcontrol-format.md) elementy wyświetlające różnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="eef4c-143">This element is optional and is needed only when you define multiple [ListEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="eef4c-144">[ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element określa właściwości i skrypty, których wartości są wyświetlane w wierszach widoku listy.</span><span class="sxs-lookup"><span data-stu-id="eef4c-144">The [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies the properties and scripts whose values are displayed in the rows of the list view.</span></span>

- <span data-ttu-id="eef4c-145">[ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element Określa właściwość lub skryptu, którego wartość jest wyświetlana w wierszu w widoku listy.</span><span class="sxs-lookup"><span data-stu-id="eef4c-145">The [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies a property or script whose value is displayed in a row of the list view.</span></span> <span data-ttu-id="eef4c-146">Widok listy, należy określić co najmniej jedną właściwość lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="eef4c-146">A list view must specify at least one property or script.</span></span> <span data-ttu-id="eef4c-147">Nie ma żadnego limitu maksymalną liczbę wierszy, które można określić.</span><span class="sxs-lookup"><span data-stu-id="eef4c-147">There is no maximum limit to the number of rows that can be specified.</span></span>

- <span data-ttu-id="eef4c-148">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element Określa właściwość, którego wartość jest wyświetlana w wierszu.</span><span class="sxs-lookup"><span data-stu-id="eef4c-148">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="eef4c-149">Należy określić właściwość lub skryptu, ale nie możesz określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="eef4c-149">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="eef4c-150">[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element określa skrypt, którego wartość jest wyświetlana w wierszu.</span><span class="sxs-lookup"><span data-stu-id="eef4c-150">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="eef4c-151">Należy określić skrypt lub właściwości, ale nie możesz określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="eef4c-151">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="eef4c-152">[Etykiety](./label-element-for-listitem-for-listcontrol-format.md) element Określa etykietę, która jest wyświetlana po lewej stronie wartości właściwości lub skryptu w wierszu.</span><span class="sxs-lookup"><span data-stu-id="eef4c-152">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element specifies the label that is displayed to the left of the property or script value in the row.</span></span> <span data-ttu-id="eef4c-153">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="eef4c-153">This element is optional.</span></span> <span data-ttu-id="eef4c-154">Jeśli etykieta nie zostanie określony, jest wyświetlana nazwa właściwości lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="eef4c-154">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="eef4c-155">Aby uzyskać kompletny przykład, zobacz [widok listy (etykiety)](./list-view-labels.md).</span><span class="sxs-lookup"><span data-stu-id="eef4c-155">For a complete example, see [List View (Labels)](./list-view-labels.md).</span></span>

- <span data-ttu-id="eef4c-156">[ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element określa warunek, który musi istnieć dla wiersza, które mają być wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="eef4c-156">The [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element specifies a condition that must exist for the row to be displayed.</span></span> <span data-ttu-id="eef4c-157">Aby uzyskać więcej informacji o dodawaniu warunków do widoku listy, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="eef4c-157">For more information about adding conditions to the list view, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span> <span data-ttu-id="eef4c-158">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="eef4c-158">This element is optional.</span></span>

- <span data-ttu-id="eef4c-159">[FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element określa wzorzec, który służy do wyświetlania wartości właściwości lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="eef4c-159">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a pattern that is used to display the value of the property or script.</span></span> <span data-ttu-id="eef4c-160">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="eef4c-160">This element is optional.</span></span>

<span data-ttu-id="eef4c-161">Na przykład kompletny plik formatowania, który definiuje widoku prostej listy zobacz [widok listy (Basic)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="eef4c-161">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-list-view"></a><span data-ttu-id="eef4c-162">Definiowanie obiektów, które w widoku listy</span><span class="sxs-lookup"><span data-stu-id="eef4c-162">Defining the Objects That Use the List View</span></span>

<span data-ttu-id="eef4c-163">Istnieją dwa sposoby, aby zdefiniować, które obiekty platformy .NET przy użyciu widoku listy.</span><span class="sxs-lookup"><span data-stu-id="eef4c-163">There are two ways to define which .NET objects use the list view.</span></span> <span data-ttu-id="eef4c-164">Możesz użyć [ViewSelectedBy](./viewselectedby-element-format.md) elementu, aby zdefiniować obiekty, które mogą być wyświetlane przez wszystkich definicji widoku lub możesz użyć [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elementu, aby zdefiniować, które obiekty są wyświetlane przez określonej definicji widoku.</span><span class="sxs-lookup"><span data-stu-id="eef4c-164">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="eef4c-165">W większości przypadków widok ma tylko jedną definicję, więc obiekty są zazwyczaj definiowane przez [ViewSelectedBy](./viewselectedby-element-format.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="eef4c-165">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="eef4c-166">Poniższy przykład pokazuje jak zdefiniować obiekty, które są wyświetlane przy użyciu widoku listy [ViewSelectedBy](./viewselectedby-element-format.md) i [TypeName](./typename-element-for-viewselectedby-format.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="eef4c-166">The following example shows how to define the objects that are displayed by the list view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="eef4c-167">Nie ma żadnego limitu liczby [TypeName](./typename-element-for-viewselectedby-format.md) elementów, że można określić i ich kolejność nie jest znaczący.</span><span class="sxs-lookup"><span data-stu-id="eef4c-167">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="eef4c-168">Następujące elementy XML może służyć do określenia obiektów, które są używane przez widok listy:</span><span class="sxs-lookup"><span data-stu-id="eef4c-168">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="eef4c-169">[ViewSelectedBy](./viewselectedby-element-format.md) element definiuje obiekty, które są wyświetlane w widoku listy.</span><span class="sxs-lookup"><span data-stu-id="eef4c-169">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="eef4c-170">[TypeName](./typename-element-for-viewselectedby-format.md) element określa obiekt .NET, który jest wyświetlany w widoku.</span><span class="sxs-lookup"><span data-stu-id="eef4c-170">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="eef4c-171">W pełni kwalifikowana nazwa typu .NET jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="eef4c-171">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="eef4c-172">Należy określić co najmniej jeden typ lub zaznaczenia, ustaw dla widoku, ale ma nie maksymalną liczbę elementów, które mogą być określone.</span><span class="sxs-lookup"><span data-stu-id="eef4c-172">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="eef4c-173">Na przykład cały plik formatowania zobacz [widok listy (Basic)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="eef4c-173">For an example of a complete formatting file, see [List View (Basic)](./list-view-basic.md).</span></span>

<span data-ttu-id="eef4c-174">W poniższym przykładzie użyto [ViewSelectedBy](./viewselectedby-element-format.md) i [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="eef4c-174">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="eef4c-175">Używać zestawów wybór, w którym znajduje się zestaw powiązanych obiektów, które są wyświetlane przy użyciu wielu widoków, takich jak podczas definiowania widoku listy i widok tabeli dla tych samych obiektów.</span><span class="sxs-lookup"><span data-stu-id="eef4c-175">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="eef4c-176">Aby uzyskać więcej informacji o sposobie tworzenia zestawu wyboru, zobacz [Definiowanie zestawów wybór](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="eef4c-176">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="eef4c-177">Następujące elementy XML może służyć do określenia obiektów, które są używane przez widok listy:</span><span class="sxs-lookup"><span data-stu-id="eef4c-177">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="eef4c-178">[ViewSelectedBy](./viewselectedby-element-format.md) element definiuje obiekty, które są wyświetlane w widoku listy.</span><span class="sxs-lookup"><span data-stu-id="eef4c-178">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="eef4c-179">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element określa zestaw obiektów, które mogą być wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="eef4c-179">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="eef4c-180">Należy określić co najmniej jeden zbiór lub typu widoku, ale ma nie maksymalną liczbę elementów, które mogą być określone.</span><span class="sxs-lookup"><span data-stu-id="eef4c-180">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="eef4c-181">Poniższy przykład pokazuje jak zdefiniować obiekty wyświetlane przez określonej definicji widoku listy przy użyciu [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="eef4c-181">The following example shows how to define the objects displayed by a specific definition of the list view using the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element.</span></span> <span data-ttu-id="eef4c-182">Ten element można określić nazwę typu .NET, obiektu, wybór zestaw obiektów, lub warunek wyboru, który określa, kiedy jest używane definicji.</span><span class="sxs-lookup"><span data-stu-id="eef4c-182">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="eef4c-183">Aby uzyskać więcej informacji o sposobie tworzenia wyboru warunków, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="eef4c-183">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

<span data-ttu-id="eef4c-184">Następujące elementy XML może służyć do określenia obiektów, które są używane przez określone definicji widoku listy:</span><span class="sxs-lookup"><span data-stu-id="eef4c-184">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="eef4c-185">[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element definiuje obiekty, które są wyświetlane przez definicję.</span><span class="sxs-lookup"><span data-stu-id="eef4c-185">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="eef4c-186">[TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element określa obiekt .NET, który jest wyświetlany przez definicję.</span><span class="sxs-lookup"><span data-stu-id="eef4c-186">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="eef4c-187">Korzystając z tego elementu, w pełni kwalifikowana nazwa typu .NET jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="eef4c-187">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="eef4c-188">Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru definicji, ale ma nie maksymalną liczbę elementów, które mogą być określone.</span><span class="sxs-lookup"><span data-stu-id="eef4c-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="eef4c-189">[SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) — element (niewyświetlany) określa zestaw obiektów, które mogą być wyświetlane przez tę definicję.</span><span class="sxs-lookup"><span data-stu-id="eef4c-189">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="eef4c-190">Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru definicji, ale ma nie maksymalną liczbę elementów, które mogą być określone.</span><span class="sxs-lookup"><span data-stu-id="eef4c-190">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="eef4c-191">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) — element (niewyświetlany) określa warunek, który musi istnieć dla tej definicji, które ma być używany.</span><span class="sxs-lookup"><span data-stu-id="eef4c-191">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="eef4c-192">Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru definicji, ale ma nie maksymalną liczbę elementów, które mogą być określone.</span><span class="sxs-lookup"><span data-stu-id="eef4c-192">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="eef4c-193">Aby uzyskać więcej informacji na temat definiowania warunków wybór zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="eef4c-193">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-list-view"></a><span data-ttu-id="eef4c-194">Wyświetlanie grup obiektów w widoku listy</span><span class="sxs-lookup"><span data-stu-id="eef4c-194">Displaying Groups of Objects in a List View</span></span>

<span data-ttu-id="eef4c-195">Można oddzielić obiektów, które są wyświetlane w widoku listy do grup.</span><span class="sxs-lookup"><span data-stu-id="eef4c-195">You can separate the objects that are displayed by the list view into groups.</span></span> <span data-ttu-id="eef4c-196">Nie oznacza to, że zdefiniowanie grupy, tylko program Windows PowerShell rozpoczyna nową grupę, w każdym przypadku, gdy zmieni się wartość określoną właściwość lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="eef4c-196">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="eef4c-197">W poniższym przykładzie tworzona nowa grupa zawsze wtedy, gdy wartość [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) zmiany właściwości.</span><span class="sxs-lookup"><span data-stu-id="eef4c-197">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="eef4c-198">Następujące elementy XML są używane do definiowania, gdy tworzona jest grupa:</span><span class="sxs-lookup"><span data-stu-id="eef4c-198">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="eef4c-199">[GroupBy](./groupby-element-for-view-format.md) element definiuje właściwość lub skrypt, który uruchamia nową grupę i definiuje sposób wyświetlania grupy.</span><span class="sxs-lookup"><span data-stu-id="eef4c-199">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="eef4c-200">[PropertyName](./propertyname-element-for-groupby-format.md) element Określa właściwość, która uruchamia nową grupę, zmianie wartości.</span><span class="sxs-lookup"><span data-stu-id="eef4c-200">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="eef4c-201">Należy określić właściwość lub skrypt, aby rozpocząć grupy, ale nie możesz określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="eef4c-201">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="eef4c-202">[ScriptBlock](./scriptblock-element-for-groupby-format.md) element określa skrypt, który uruchamia nową grupę, zmianie wartości.</span><span class="sxs-lookup"><span data-stu-id="eef4c-202">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="eef4c-203">Należy określić skrypt lub właściwości, które można uruchomić grupy, ale nie możesz określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="eef4c-203">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="eef4c-204">[Etykiety](./label-element-for-groupby-format.md) element definiuje etykietę, która jest wyświetlana na początku każdej grupy.</span><span class="sxs-lookup"><span data-stu-id="eef4c-204">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="eef4c-205">Oprócz tekstu określonego przez ten element programu Windows PowerShell Wyświetla wartość, która wyzwolone nową grupę, a następnie dodaje pusty wiersz, przed i po etykiecie.</span><span class="sxs-lookup"><span data-stu-id="eef4c-205">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="eef4c-206">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="eef4c-206">This element is optional.</span></span>

- <span data-ttu-id="eef4c-207">[Formant niestandardowy](./customcontrol-element-for-groupby-format.md) element definiuje formant, który służy do wyświetlania danych.</span><span class="sxs-lookup"><span data-stu-id="eef4c-207">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="eef4c-208">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="eef4c-208">This element is optional.</span></span>

- <span data-ttu-id="eef4c-209">[CustomControlName](./customcontrolname-element-for-groupby-format.md) element określa wspólny lub wyświetlić formant, który służy do wyświetlania danych.</span><span class="sxs-lookup"><span data-stu-id="eef4c-209">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="eef4c-210">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="eef4c-210">This element is optional.</span></span>

<span data-ttu-id="eef4c-211">Na przykład kompletny plik formatowania, który definiuje grupy zobacz [widok listy (grupowania)](./list-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="eef4c-211">For an example of a complete formatting file that defines groups, see [List View (GroupBy)](./list-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="eef4c-212">Za pomocą ciągów formatu</span><span class="sxs-lookup"><span data-stu-id="eef4c-212">Using Format Strings</span></span>

<span data-ttu-id="eef4c-213">Ciągi formatowania można dodać do widoku, aby lepiej zdefiniować sposób wyświetlania danych.</span><span class="sxs-lookup"><span data-stu-id="eef4c-213">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="eef4c-214">Poniższy przykład pokazuje jak zdefiniować ciąg formatowania dla wartości `StartTime` właściwości.</span><span class="sxs-lookup"><span data-stu-id="eef4c-214">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

<span data-ttu-id="eef4c-215">Następujące elementy XML może służyć do określania wzorca format:</span><span class="sxs-lookup"><span data-stu-id="eef4c-215">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="eef4c-216">[ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element określa dane, które jest wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="eef4c-216">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="eef4c-217">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element Określa właściwość, którego wartość jest wyświetlana w widoku.</span><span class="sxs-lookup"><span data-stu-id="eef4c-217">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="eef4c-218">Należy określić właściwość lub skryptu, ale nie możesz określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="eef4c-218">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="eef4c-219">[FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element określa wzorzec formatu, który definiuje sposób wyświetlania wartości właściwości lub skryptu w widoku.</span><span class="sxs-lookup"><span data-stu-id="eef4c-219">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

- <span data-ttu-id="eef4c-220">[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) — element (niewyświetlany) określa skrypt, którego wartość jest wyświetlana w widoku.</span><span class="sxs-lookup"><span data-stu-id="eef4c-220">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="eef4c-221">Należy określić skrypt lub właściwości, ale nie możesz określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="eef4c-221">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="eef4c-222">W poniższym przykładzie `ToString` metoda jest wywoływana, aby sformatować wartość argumentu skryptu.</span><span class="sxs-lookup"><span data-stu-id="eef4c-222">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="eef4c-223">Skrypty można wywołać dowolnej metody obiektu.</span><span class="sxs-lookup"><span data-stu-id="eef4c-223">Scripts can call any method of an object.</span></span> <span data-ttu-id="eef4c-224">W związku z tym jeśli obiekt ma metodę `ToString`, który ma następujące parametry formatowania, skrypt może wywołać tej metody, aby sformatować wartość danych wyjściowych skryptu.</span><span class="sxs-lookup"><span data-stu-id="eef4c-224">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="eef4c-225">Następujący element XML może służyć do wywołania `ToString` metody:</span><span class="sxs-lookup"><span data-stu-id="eef4c-225">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="eef4c-226">[ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element określa dane, które jest wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="eef4c-226">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="eef4c-227">[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) — element (niewyświetlany) określa skrypt, którego wartość jest wyświetlana w widoku.</span><span class="sxs-lookup"><span data-stu-id="eef4c-227">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="eef4c-228">Należy określić skrypt lub właściwości, ale nie możesz określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="eef4c-228">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="eef4c-229">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eef4c-229">See Also</span></span>

[<span data-ttu-id="eef4c-230">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eef4c-230">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/writing-a-windows-powershell-cmdlet.md)
