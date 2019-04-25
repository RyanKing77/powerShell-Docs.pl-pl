---
title: Widok (grupowania) listy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2e66c86-83a7-4148-8575-c28d6d429d4f
caps.latest.revision: 6
ms.openlocfilehash: c178c4a48f9595001bcc249d5f55886fa54bb9f2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065295"
---
# <a name="list-view-groupby"></a><span data-ttu-id="19caf-102">Widok listy (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="19caf-102">List View (GroupBy)</span></span>

<span data-ttu-id="19caf-103">Ten przykład przedstawia sposób implementowania widoku listy, wierszami listy do grup.</span><span class="sxs-lookup"><span data-stu-id="19caf-103">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="19caf-104">Ten widok listy są wyświetlane właściwości [System.Serviceprocess.Servicecontroller? Displayproperty = imię i nazwisko](/dotnet/api/System.ServiceProcess.ServiceController) obiektów zwróconych przez [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="19caf-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="19caf-105">Aby uzyskać więcej informacji o składnikach w widoku listy, zobacz [tworzenia widoku listy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="19caf-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="19caf-106">Aby załadować ten plik formatowania</span><span class="sxs-lookup"><span data-stu-id="19caf-106">To load this formatting file</span></span>

1. <span data-ttu-id="19caf-107">Skopiuj plik XML z sekcji przykład tego tematu do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="19caf-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="19caf-108">Zapisz plik tekstowy.</span><span class="sxs-lookup"><span data-stu-id="19caf-108">Save the text file.</span></span> <span data-ttu-id="19caf-109">Pamiętaj dodać `format.ps1xml` rozszerzenie pliku, aby zidentyfikować go jako plik formatowania.</span><span class="sxs-lookup"><span data-stu-id="19caf-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="19caf-110">Otwórz program Windows PowerShell i uruchom następujące polecenie, aby załadować plik formatowania do bieżącej sesji: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="19caf-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="19caf-111">Ten plik formatowania definiuje wyświetlanie obiektu, który jest już zdefiniowana w pliku formatowania programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="19caf-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="19caf-112">Należy użyć `prependPath` parametru po uruchomieniu polecenia cmdlet, a nie można załadować to formatowanie pliku jako moduł.</span><span class="sxs-lookup"><span data-stu-id="19caf-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="19caf-113">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="19caf-113">Demonstrates</span></span>

<span data-ttu-id="19caf-114">Ten plik formatowania pokazuje następujące elementy XML:</span><span class="sxs-lookup"><span data-stu-id="19caf-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="19caf-115">[Nazwa](./name-element-for-view-format.md) elementu widoku.</span><span class="sxs-lookup"><span data-stu-id="19caf-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="19caf-116">[ViewSelectedBy](./viewselectedby-element-format.md) element, który definiuje, jakie obiekty są wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="19caf-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="19caf-117">[GroupBy](./viewselectedby-element-format.md) element, który definiuje sposób wyświetlania nowej grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="19caf-117">The [GroupBy](./viewselectedby-element-format.md) element that defines how a new group of objects is displayed.</span></span>

- <span data-ttu-id="19caf-118">[Elementu ListControl](./listcontrol-element-format.md) element, który definiuje, jakie właściwości jest wyświetlany w widoku.</span><span class="sxs-lookup"><span data-stu-id="19caf-118">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="19caf-119">[ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element, który definiuje, co jest wyświetlane w wierszu w widoku listy.</span><span class="sxs-lookup"><span data-stu-id="19caf-119">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="19caf-120">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element, który definiuje, w którym właściwość jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="19caf-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="19caf-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="19caf-121">Example</span></span>

<span data-ttu-id="19caf-122">Następujący kod XML definiuje widoku listy, który rozpoczyna się nowej grupie zawsze, gdy wartość [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) zmiany właściwości.</span><span class="sxs-lookup"><span data-stu-id="19caf-122">The following XML defines a list view that starts a new group whenever the value of the [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) property changes.</span></span> <span data-ttu-id="19caf-123">Po uruchomieniu każdej grupy jest wyświetlana etykiety niestandardowej zawierającego nowe wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="19caf-123">When each group is started, a custom label is displayed that includes the new value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.ServiceProcess.ServiceController</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>Status</PropertyName>
        <Label>New Service Status</Label>
      </GroupBy>
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
                <PropertyName>ServiceType</PropertyName>
              </ListItem>
            </ListItems>
          </ListEntry>
        </ListEntries>
      </ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="19caf-124">W poniższym przykładzie przedstawiono sposób wyświetlania środowiska Windows PowerShell [System.Serviceprocess.Servicecontroller? Displayproperty = imię i nazwisko](/dotnet/api/System.ServiceProcess.ServiceController) obiektów po załadowaniu tego formatu pliku.</span><span class="sxs-lookup"><span data-stu-id="19caf-124">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span> <span data-ttu-id="19caf-125">Puste wiersze przed i po etykiecie grupy są automatycznie dodawane przez program Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="19caf-125">The blank lines added before and after the group label are automatically added by Windows PowerShell.</span></span>

```powershell
Get-Service f*
```

```output
   New Service Status: Stopped

Name        : Fax
DisplayName : Fax
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
ServiceType : Win32OwnProcess

   New Service Status: Stopped

Name        : fdPHost
DisplayName : Function Discovery Provider Host
ServiceType : Win32ShareProcess

   New Service Status: Running

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
ServiceType : Win32ShareProcess

   New Service Status: Stopped

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="19caf-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19caf-126">See Also</span></span>

[<span data-ttu-id="19caf-127">Przykłady formatowania plików</span><span class="sxs-lookup"><span data-stu-id="19caf-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="19caf-128">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="19caf-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
