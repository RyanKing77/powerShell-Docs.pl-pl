---
title: Widok (etykiety) listy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53442bb1-74a3-49f9-9150-3bc3081a7565
caps.latest.revision: 6
ms.openlocfilehash: 27de41c88e224f7610c10a764e51524016ecc8cb
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794828"
---
# <a name="list-view-labels"></a><span data-ttu-id="29567-102">Widok listy (etykiety)</span><span class="sxs-lookup"><span data-stu-id="29567-102">List View (Labels)</span></span>

<span data-ttu-id="29567-103">Ten przykład przedstawia sposób implementowania widoku listy, który wyświetla etykiety niestandardowej dla każdego wiersza listy.</span><span class="sxs-lookup"><span data-stu-id="29567-103">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="29567-104">Ten widok listy są wyświetlane właściwości [System.Serviceprocess.Servicecontroller? Displayproperty = imię i nazwisko](/dotnet/api/System.ServiceProcess.ServiceController) obiektu, który jest zwracany przez [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="29567-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="29567-105">Aby uzyskać więcej informacji o składnikach w widoku listy, zobacz [tworzenia widoku listy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="29567-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="29567-106">Aby załadować ten plik formatowania</span><span class="sxs-lookup"><span data-stu-id="29567-106">To load this formatting file</span></span>

1. <span data-ttu-id="29567-107">Skopiuj plik XML z sekcji przykład tego tematu do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="29567-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="29567-108">Zapisz plik tekstowy.</span><span class="sxs-lookup"><span data-stu-id="29567-108">Save the text file.</span></span> <span data-ttu-id="29567-109">Pamiętaj dodać `format.ps1xml` rozszerzenie pliku, aby zidentyfikować go jako plik formatowania.</span><span class="sxs-lookup"><span data-stu-id="29567-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="29567-110">Otwórz program Windows PowerShell i uruchom następujące polecenie, aby załadować plik formatowania do bieżącej sesji: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="29567-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="29567-111">Ten plik formatowania definiuje wyświetlanie obiektu, który jest już zdefiniowana w pliku formatowania programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="29567-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="29567-112">Należy użyć `prependPath` parametru po uruchomieniu polecenia cmdlet, a nie można załadować to formatowanie pliku jako moduł.</span><span class="sxs-lookup"><span data-stu-id="29567-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="29567-113">Przedstawiono</span><span class="sxs-lookup"><span data-stu-id="29567-113">Demonstrates</span></span>

<span data-ttu-id="29567-114">Ten plik formatowania pokazuje następujące elementy XML:</span><span class="sxs-lookup"><span data-stu-id="29567-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="29567-115">[Nazwa](./name-element-for-view-format.md) elementu widoku.</span><span class="sxs-lookup"><span data-stu-id="29567-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="29567-116">[ViewSelectedBy](./viewselectedby-element-format.md) element, który definiuje, jakie obiekty są wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="29567-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="29567-117">[Elementu ListControl](./listcontrol-element-format.md) element, który definiuje, jakie właściwości jest wyświetlany w widoku.</span><span class="sxs-lookup"><span data-stu-id="29567-117">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="29567-118">[ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element, który definiuje, co jest wyświetlane w wierszu w widoku listy.</span><span class="sxs-lookup"><span data-stu-id="29567-118">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="29567-119">[Etykiety](./label-element-for-listitem-for-listcontrol-format.md) element, który definiuje, co jest wyświetlane w wierszu w widoku listy.</span><span class="sxs-lookup"><span data-stu-id="29567-119">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="29567-120">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element, który definiuje, w którym właściwość jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="29567-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="29567-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="29567-121">Example</span></span>

<span data-ttu-id="29567-122">Następujący kod XML definiuje widoku listy, który wyświetla etykiety niestandardowej w każdym wierszu.</span><span class="sxs-lookup"><span data-stu-id="29567-122">The following XML defines a list view that displays a custom label in each row.</span></span> <span data-ttu-id="29567-123">W tym przypadku etykiety zawiera nazwę właściwości, za pomocą każdej litery, wielkie litery w i słowem "property".</span><span class="sxs-lookup"><span data-stu-id="29567-123">In this case, the label includes the property name with each letter capitalized and the word "property".</span></span> <span data-ttu-id="29567-124">W każdym wierszu jest wyświetlana nazwa właściwości, następuje wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="29567-124">In each row, the name of the property is displayed followed by the value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
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
            <Label>NAME property</Label>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <Label>DISPLAYNAME property</Label>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <Label>STATUS property</Label>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <Label>SERVICETYPE property</Label>
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

<span data-ttu-id="29567-125">W poniższym przykładzie przedstawiono sposób wyświetlania środowiska Windows PowerShell [System.Serviceprocess.Servicecontroller? Displayproperty = imię i nazwisko](/dotnet/api/System.ServiceProcess.ServiceController) obiektów po załadowaniu tego formatu pliku.</span><span class="sxs-lookup"><span data-stu-id="29567-125">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
NAME property        : Fax
DISPLAYNAME property : Fax
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FCSAM
DISPLAYNAME property : Microsoft Antimalware Service
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : fdPHost
DISPLAYNAME property : Function Discovery Provider Host
STATUS property      : Stopped
SERVICETYPE property : Win32ShareProcess

NAME property        : FDResPub
DISPLAYNAME property : Function Discovery Resource Publication
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache
DISPLAYNAME property : Windows Font Cache Service
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache3.0.0.0
DISPLAYNAME property : Windows Presentation Foundation Font Cache 3.0.0.0
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FSysAgent
DISPLAYNAME property : Microsoft Forefront System Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : FwcAgent
DISPLAYNAME property : Firewall Client Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="29567-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29567-126">See Also</span></span>

[<span data-ttu-id="29567-127">Przykłady formatowania plików</span><span class="sxs-lookup"><span data-stu-id="29567-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="29567-128">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="29567-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
