---
title: Tworzenie szerokie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066723"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="593a4-102">Tworzenie widoku szerokiego</span><span class="sxs-lookup"><span data-stu-id="593a4-102">Creating a Wide View</span></span>

<span data-ttu-id="593a4-103">Szerokie Wyświetla pojedynczą wartość dla każdego obiektu, który jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="593a4-103">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="593a4-104">Wartość właściwości obiektu platformy .NET lub wartość skryptu, może być wyświetlana wartość.</span><span class="sxs-lookup"><span data-stu-id="593a4-104">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="593a4-105">Domyślnie istnieje etykiety lub nagłówek dla tego widoku.</span><span class="sxs-lookup"><span data-stu-id="593a4-105">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="593a4-106">Wyświetlanie szerokie</span><span class="sxs-lookup"><span data-stu-id="593a4-106">A Wide View Display</span></span>

<span data-ttu-id="593a4-107">W poniższym przykładzie przedstawiono sposób wyświetlania środowiska Windows PowerShell [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu, który jest zwracany przez [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) polecenia cmdlet, gdy jego dane wyjściowe w potoku do [ Format całej](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="593a4-107">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="593a4-108">(Domyślnie [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) polecenie cmdlet zwraca widok tabeli.) W tym przykładzie dwie kolumny są używane do wyświetlania nazwę procesu dla każdego zwróconego obiektu.</span><span class="sxs-lookup"><span data-stu-id="593a4-108">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="593a4-109">Nazwa właściwości obiektu nie jest wyświetlana, tylko wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="593a4-109">The name of the object's property is not displayed, only the value of the property.</span></span>

```
Get-Process | format-wide
AEADISRV                     agrsmsvc
Ati2evxx                     Ati2evxx
audiodg                      CCC
CcmExec                      communicator
Crypserv                     csrss
csrss                        DevDtct2
DM1Service                   dpupdchk
dwm                          DxStudio
EXCEL                        explorer
GoogleToolbarNotifier        GrooveMonitor
hpqwmiex                     hpservice
Idle                         InoRpc
InoRT                        InoTask
ipoint                       lsass
lsm                          MOM
MSASCui                      notepad
...                          ...

```

## <a name="defining-the-wide-view"></a><span data-ttu-id="593a4-110">Definiowanie szerokie</span><span class="sxs-lookup"><span data-stu-id="593a4-110">Defining the Wide View</span></span>

<span data-ttu-id="593a4-111">Następujący kody XML pokazuje schemat szerokie [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu.</span><span class="sxs-lookup"><span data-stu-id="593a4-111">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <GroupBy>...</GroupBy>
  <Controls>...</Controls>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

<span data-ttu-id="593a4-112">Następujące elementy XML są używane do definiowania szerokie:</span><span class="sxs-lookup"><span data-stu-id="593a4-112">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="593a4-113">[Widoku](./view-element-format.md) element jest elementem nadrzędnym szerokiego widoku.</span><span class="sxs-lookup"><span data-stu-id="593a4-113">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="593a4-114">(Jest to ten sam element nadrzędny dla tabeli, listy i widoki kontrolki niestandardowej).</span><span class="sxs-lookup"><span data-stu-id="593a4-114">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="593a4-115">[Nazwa](./name-element-for-view-format.md) element Określa nazwę widoku.</span><span class="sxs-lookup"><span data-stu-id="593a4-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="593a4-116">Ten element jest wymagany dla wszystkich widoków.</span><span class="sxs-lookup"><span data-stu-id="593a4-116">This element is required for all views.</span></span>

- <span data-ttu-id="593a4-117">[ViewSelectedBy](./viewselectedby-element-format.md) element definiuje obiekty, które przy użyciu widoku.</span><span class="sxs-lookup"><span data-stu-id="593a4-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="593a4-118">Ten element jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="593a4-118">This element is required.</span></span>

- <span data-ttu-id="593a4-119">[GroupBy](./groupby-element-for-view-format.md) element definiuje, gdy zostanie wyświetlona nowa grupa obiektów.</span><span class="sxs-lookup"><span data-stu-id="593a4-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="593a4-120">Nowa grupa została uruchomiona, zawsze wtedy, gdy zmieni się wartość określoną właściwość lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="593a4-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="593a4-121">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="593a4-121">This element is optional.</span></span>

- <span data-ttu-id="593a4-122">[Formantów](./controls-element-for-view-format.md) elementy definiuje niestandardowe formanty, które są definiowane przez szerokie.</span><span class="sxs-lookup"><span data-stu-id="593a4-122">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="593a4-123">Formanty zapewniają sposób, aby bardziej szczegółowo określić sposób wyświetlania danych.</span><span class="sxs-lookup"><span data-stu-id="593a4-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="593a4-124">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="593a4-124">This element is optional.</span></span> <span data-ttu-id="593a4-125">Widok można zdefiniować własne niestandardowe formanty, lub może używać wspólnych formantów, które mogą być używane przez dowolny widok w formatowaniu pliku.</span><span class="sxs-lookup"><span data-stu-id="593a4-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="593a4-126">Aby uzyskać więcej informacji na temat formantów niestandardowych, zobacz [Tworzenie niestandardowych formantów](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="593a4-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="593a4-127">[WideControl](./widecontrol-element-format.md) elementu i jego elementy podrzędne należy zdefiniować, co jest wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="593a4-127">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="593a4-128">W powyższym przykładzie widok służy do wyświetlania [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) właściwości.</span><span class="sxs-lookup"><span data-stu-id="593a4-128">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="593a4-129">Na przykład kompletny plik formatowania, który definiuje prosty szerokie zobacz [szerokie (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="593a4-129">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="593a4-130">Zapewnianie definicje dla szerokiego widoku</span><span class="sxs-lookup"><span data-stu-id="593a4-130">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="593a4-131">Szerokie widoków może zapewnić co najmniej jedna definicja przy użyciu elementów podrzędnych [WideControl](./widecontrol-element-format.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="593a4-131">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="593a4-132">Zazwyczaj widok będzie mieć tylko jedną definicję.</span><span class="sxs-lookup"><span data-stu-id="593a4-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="593a4-133">W poniższym przykładzie, widok zawiera jednej definicji, który wyświetla wartość [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) właściwości.</span><span class="sxs-lookup"><span data-stu-id="593a4-133">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="593a4-134">Wartość właściwości lub wartość skryptu (nie pokazano w przykładzie), można wyświetlić szerokie.</span><span class="sxs-lookup"><span data-stu-id="593a4-134">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber></ColumnNumber>
  <WideEntries>
    <WideEntry>
      <WideItem>
        <PropertyName>ProcessName</PropertyName>
      </WideItem>
    </WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="593a4-135">Następujące elementy XML może służyć do zapewnienia definicje szerokie:</span><span class="sxs-lookup"><span data-stu-id="593a4-135">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="593a4-136">[WideControl](./widecontrol-element-format.md) elementu i jego elementy podrzędne należy zdefiniować, co jest wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="593a4-136">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="593a4-137">[AutoSize](./autosize-element-for-widecontrol-format.md) element określa, czy rozmiar kolumny i liczba kolumn są dostosowywane na podstawie rozmiaru danych.</span><span class="sxs-lookup"><span data-stu-id="593a4-137">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="593a4-138">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="593a4-138">This element is optional.</span></span>

- <span data-ttu-id="593a4-139">[ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element określa liczbę kolumn wyświetlanych w szerokim oknie.</span><span class="sxs-lookup"><span data-stu-id="593a4-139">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="593a4-140">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="593a4-140">This element is optional.</span></span>

- <span data-ttu-id="593a4-141">[WideEntries](./wideentries-element-for-widecontrol-format.md) element udostępnia definicji widoku.</span><span class="sxs-lookup"><span data-stu-id="593a4-141">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="593a4-142">W większości przypadków widok będzie mieć tylko jedną definicję.</span><span class="sxs-lookup"><span data-stu-id="593a4-142">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="593a4-143">Ten element jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="593a4-143">This element is required.</span></span>

- <span data-ttu-id="593a4-144">[WideEntry](./wideentry-element-for-widecontrol-format.md) element zawiera definicję widoku.</span><span class="sxs-lookup"><span data-stu-id="593a4-144">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="593a4-145">Co najmniej jeden [WideEntry](./wideentry-element-for-widecontrol-format.md) jest wymagana; jednak nie ma żadnego limitu maksymalną liczbę elementów, które można dodać.</span><span class="sxs-lookup"><span data-stu-id="593a4-145">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="593a4-146">W większości przypadków widok będzie mieć tylko jedną definicję.</span><span class="sxs-lookup"><span data-stu-id="593a4-146">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="593a4-147">[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element określa obiekty, które są wyświetlane zgodnie z definicją określonych.</span><span class="sxs-lookup"><span data-stu-id="593a4-147">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="593a4-148">Ten element jest opcjonalna i jest potrzebny tylko wtedy, gdy można zdefiniować wiele [WideEntry](./wideentry-element-for-widecontrol-format.md) elementy wyświetlające różnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="593a4-148">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="593a4-149">[WideItem](./wideitem-element-for-widecontrol-format.md) element określa dane, które jest wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="593a4-149">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="593a4-150">W przeciwieństwie do innych rodzajów widoków szerokości kontrolki można wyświetlić tylko jeden element.</span><span class="sxs-lookup"><span data-stu-id="593a4-150">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="593a4-151">[PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element Określa właściwość, którego wartość jest wyświetlana w widoku.</span><span class="sxs-lookup"><span data-stu-id="593a4-151">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="593a4-152">Należy określić właściwość lub skryptu, ale nie możesz określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="593a4-152">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="593a4-153">[ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element określa skrypt, którego wartość jest wyświetlana w widoku.</span><span class="sxs-lookup"><span data-stu-id="593a4-153">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="593a4-154">Należy określić skrypt lub właściwości, ale nie możesz określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="593a4-154">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="593a4-155">[FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element określa wzorzec, który służy do wyświetlania danych.</span><span class="sxs-lookup"><span data-stu-id="593a4-155">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="593a4-156">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="593a4-156">This element is optional.</span></span>

<span data-ttu-id="593a4-157">Na przykład kompletny plik formatowania, który definiuje definicji szerokie zobacz [szerokie (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="593a4-157">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="593a4-158">Definiowanie obiektów, które szerokie</span><span class="sxs-lookup"><span data-stu-id="593a4-158">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="593a4-159">Istnieją dwa sposoby, aby zdefiniować, które obiekty .NET przy użyciu szerokiej widoku.</span><span class="sxs-lookup"><span data-stu-id="593a4-159">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="593a4-160">Możesz użyć [ViewSelectedBy](./viewselectedby-element-format.md) elementu, aby zdefiniować obiekty, które mogą być wyświetlane przez wszystkich definicji widoku lub możesz użyć [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elementu, aby zdefiniować, które obiekty są wyświetlane przez określonej definicji widoku.</span><span class="sxs-lookup"><span data-stu-id="593a4-160">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="593a4-161">W większości przypadków widok ma tylko jedną definicję, więc obiekty są zazwyczaj definiowane przez [ViewSelectedBy](./viewselectedby-element-format.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="593a4-161">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="593a4-162">Poniższy przykład pokazuje jak zdefiniować obiekty, które są wyświetlane przy użyciu szerokie [ViewSelectedBy](./viewselectedby-element-format.md) i [TypeName](./typename-element-for-viewselectedby-format.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="593a4-162">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="593a4-163">Nie ma żadnego limitu liczby [TypeName](./typename-element-for-viewselectedby-format.md) elementów, że można określić i ich kolejność nie jest znaczący.</span><span class="sxs-lookup"><span data-stu-id="593a4-163">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="593a4-164">Następujące elementy XML może służyć do określenia obiektów, które są używane przez szerokie:</span><span class="sxs-lookup"><span data-stu-id="593a4-164">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="593a4-165">[ViewSelectedBy](./viewselectedby-element-format.md) element definiuje obiekty, które są wyświetlane przez szerokie.</span><span class="sxs-lookup"><span data-stu-id="593a4-165">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="593a4-166">[TypeName](./typename-element-for-viewselectedby-format.md) element określa platformy .NET, który jest wyświetlany w widoku.</span><span class="sxs-lookup"><span data-stu-id="593a4-166">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="593a4-167">W pełni kwalifikowana nazwa typu .NET jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="593a4-167">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="593a4-168">Należy określić co najmniej jeden typ lub zaznaczenia, ustaw dla widoku, ale ma nie maksymalną liczbę elementów, które mogą być określone.</span><span class="sxs-lookup"><span data-stu-id="593a4-168">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="593a4-169">Na przykład cały plik formatowania zobacz [szerokie (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="593a4-169">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="593a4-170">W poniższym przykładzie użyto [ViewSelectedBy](./viewselectedby-element-format.md) i [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="593a4-170">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="593a4-171">Używać zestawów wybór, w którym znajduje się zestaw powiązanych obiektów, które są wyświetlane przy użyciu wielu widoków, takich jak podczas definiowania szerokie i widoku tabeli dla tych samych obiektów.</span><span class="sxs-lookup"><span data-stu-id="593a4-171">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="593a4-172">Aby uzyskać więcej informacji o sposobie tworzenia zestawu wyboru, zobacz [Definiowanie zestawów wybór](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="593a4-172">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="593a4-173">Następujące elementy XML może służyć do określenia obiektów, które są używane przez szerokie:</span><span class="sxs-lookup"><span data-stu-id="593a4-173">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="593a4-174">[ViewSelectedBy](./viewselectedby-element-format.md) element definiuje obiekty, które są wyświetlane przez szerokie.</span><span class="sxs-lookup"><span data-stu-id="593a4-174">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="593a4-175">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element określa zestaw obiektów, które mogą być wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="593a4-175">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="593a4-176">Należy określić co najmniej jeden zbiór lub typu widoku, ale ma nie maksymalną liczbę elementów, które mogą być określone.</span><span class="sxs-lookup"><span data-stu-id="593a4-176">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="593a4-177">Poniższy przykład pokazuje jak zdefiniować obiekty wyświetlane przez definicję określonej za pomocą szerokie [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="593a4-177">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="593a4-178">Ten element można określić nazwę typu .NET, obiektu, wybór zestaw obiektów, lub warunek wyboru, który określa, kiedy jest używane definicji.</span><span class="sxs-lookup"><span data-stu-id="593a4-178">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="593a4-179">Aby uzyskać więcej informacji o sposobie tworzenia wyboru warunków, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="593a4-179">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="593a4-180">Następujące elementy XML może służyć do określenia obiektów, które są używane przez określone definicji szerokie:</span><span class="sxs-lookup"><span data-stu-id="593a4-180">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="593a4-181">[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element definiuje obiekty, które są wyświetlane przez definicję.</span><span class="sxs-lookup"><span data-stu-id="593a4-181">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="593a4-182">[TypeName](./typename-element-for-viewselectedby-format.md) element określa platformy .NET, który jest wyświetlany przez definicję.</span><span class="sxs-lookup"><span data-stu-id="593a4-182">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="593a4-183">Korzystając z tego elementu w pełni kwalifikowana nazwa typu .NET jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="593a4-183">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="593a4-184">Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru definicji, ale ma nie maksymalną liczbę elementów, które mogą być określone.</span><span class="sxs-lookup"><span data-stu-id="593a4-184">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="593a4-185">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) — element (niewyświetlany) określa zestaw obiektów, które mogą być wyświetlane przez tę definicję.</span><span class="sxs-lookup"><span data-stu-id="593a4-185">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="593a4-186">Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru definicji, ale ma nie maksymalną liczbę elementów, które mogą być określone.</span><span class="sxs-lookup"><span data-stu-id="593a4-186">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="593a4-187">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) — element (niewyświetlany) określa warunek, który musi istnieć dla tej definicji, które ma być używany.</span><span class="sxs-lookup"><span data-stu-id="593a4-187">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="593a4-188">Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru definicji, ale ma nie maksymalną liczbę elementów, które mogą być określone.</span><span class="sxs-lookup"><span data-stu-id="593a4-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="593a4-189">Aby uzyskać więcej informacji na temat definiowania warunków wybór zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="593a4-189">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="593a4-190">Wyświetlanie grup obiektów w szerokim oknie</span><span class="sxs-lookup"><span data-stu-id="593a4-190">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="593a4-191">Można oddzielić obiektów, które są wyświetlane przez szerokie w grupach.</span><span class="sxs-lookup"><span data-stu-id="593a4-191">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="593a4-192">Nie oznacza to, że zdefiniowanie grupy, tylko program Windows PowerShell rozpoczyna nową grupę, w każdym przypadku, gdy zmieni się wartość określoną właściwość lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="593a4-192">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="593a4-193">W poniższym przykładzie tworzona nowa grupa zawsze wtedy, gdy wartość [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) zmiany właściwości.</span><span class="sxs-lookup"><span data-stu-id="593a4-193">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="593a4-194">Następujące elementy XML są używane do definiowania, gdy tworzona jest grupa:</span><span class="sxs-lookup"><span data-stu-id="593a4-194">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="593a4-195">[GroupBy](./groupby-element-for-view-format.md) element definiuje właściwość lub skrypt, który uruchamia nową grupę i definiuje sposób wyświetlania grupy.</span><span class="sxs-lookup"><span data-stu-id="593a4-195">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="593a4-196">[PropertyName](./propertyname-element-for-groupby-format.md) element Określa właściwość, która uruchamia nową grupę, zmianie wartości.</span><span class="sxs-lookup"><span data-stu-id="593a4-196">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="593a4-197">Należy określić właściwość lub skrypt, aby rozpocząć grupy, ale nie możesz określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="593a4-197">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="593a4-198">[ScriptBlock](./scriptblock-element-for-groupby-format.md) element określa skrypt, który uruchamia nową grupę, zmianie wartości.</span><span class="sxs-lookup"><span data-stu-id="593a4-198">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="593a4-199">Należy określić skrypt lub właściwości, które można uruchomić grupy, ale nie możesz określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="593a4-199">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="593a4-200">[Etykiety](./label-element-for-groupby-format.md) element definiuje etykietę, która jest wyświetlana na początku każdej grupy.</span><span class="sxs-lookup"><span data-stu-id="593a4-200">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="593a4-201">Oprócz tekstu określonego przez ten element programu Windows PowerShell Wyświetla wartość, która wyzwolone nową grupę, a następnie dodaje pusty wiersz, przed i po etykiecie.</span><span class="sxs-lookup"><span data-stu-id="593a4-201">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="593a4-202">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="593a4-202">This element is optional.</span></span>

- <span data-ttu-id="593a4-203">[Formant niestandardowy](./customcontrol-element-for-groupby-format.md) element definiuje formant, który służy do wyświetlania danych.</span><span class="sxs-lookup"><span data-stu-id="593a4-203">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="593a4-204">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="593a4-204">This element is optional.</span></span>

- <span data-ttu-id="593a4-205">[CustomControlName](./customcontrolname-element-for-groupby-format.md) element określa wspólny lub wyświetlić formant, który służy do wyświetlania danych.</span><span class="sxs-lookup"><span data-stu-id="593a4-205">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="593a4-206">Ten element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="593a4-206">This element is optional.</span></span>

<span data-ttu-id="593a4-207">Na przykład kompletny plik formatowania, który definiuje grupy zobacz [szerokie (grupowania)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="593a4-207">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="593a4-208">Za pomocą ciągów formatu</span><span class="sxs-lookup"><span data-stu-id="593a4-208">Using Format Strings</span></span>

<span data-ttu-id="593a4-209">Ciągi formatowania można dodać do szerokie, aby lepiej zdefiniować sposób wyświetlania danych.</span><span class="sxs-lookup"><span data-stu-id="593a4-209">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="593a4-210">Poniższy przykład pokazuje jak zdefiniować ciąg formatowania dla wartości `StartTime` właściwości.</span><span class="sxs-lookup"><span data-stu-id="593a4-210">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="593a4-211">Następujące elementy XML może służyć do określania wzorca format:</span><span class="sxs-lookup"><span data-stu-id="593a4-211">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="593a4-212">[WideItem](./wideitem-element-for-widecontrol-format.md) element określa dane, które jest wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="593a4-212">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="593a4-213">[PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element Określa właściwość, którego wartość jest wyświetlana w widoku.</span><span class="sxs-lookup"><span data-stu-id="593a4-213">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="593a4-214">Należy określić właściwość lub skryptu, ale nie możesz określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="593a4-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="593a4-215">[FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element określa wzorzec formatu, który definiuje sposób wyświetlania wartości właściwości lub skryptu w widoku</span><span class="sxs-lookup"><span data-stu-id="593a4-215">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="593a4-216">[ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) — element (niewyświetlany) określa skrypt, którego wartość jest wyświetlana w widoku.</span><span class="sxs-lookup"><span data-stu-id="593a4-216">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="593a4-217">Należy określić skrypt lub właściwości, ale nie możesz określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="593a4-217">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="593a4-218">W poniższym przykładzie `ToString` metoda jest wywoływana, aby sformatować wartość argumentu skryptu.</span><span class="sxs-lookup"><span data-stu-id="593a4-218">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="593a4-219">Skrypty można wywołać dowolnej metody obiektu.</span><span class="sxs-lookup"><span data-stu-id="593a4-219">Scripts can call any method of an object.</span></span> <span data-ttu-id="593a4-220">W związku z tym jeśli obiekt ma metodę `ToString`, który ma następujące parametry formatowania, skrypt może wywołać tej metody, aby sformatować wartość danych wyjściowych skryptu.</span><span class="sxs-lookup"><span data-stu-id="593a4-220">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="593a4-221">Następujący element XML może służyć do wywołania `ToString` metody:</span><span class="sxs-lookup"><span data-stu-id="593a4-221">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="593a4-222">[WideItem](./wideitem-element-for-widecontrol-format.md) element określa dane, które jest wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="593a4-222">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="593a4-223">[ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) — element (niewyświetlany) określa skrypt, którego wartość jest wyświetlana w widoku.</span><span class="sxs-lookup"><span data-stu-id="593a4-223">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="593a4-224">Należy określić skrypt lub właściwości, ale nie możesz określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="593a4-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="593a4-225">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="593a4-225">See Also</span></span>

[<span data-ttu-id="593a4-226">Szerokie (Basic)</span><span class="sxs-lookup"><span data-stu-id="593a4-226">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="593a4-227">Szerokie (grupowania)</span><span class="sxs-lookup"><span data-stu-id="593a4-227">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="593a4-228">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="593a4-228">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
