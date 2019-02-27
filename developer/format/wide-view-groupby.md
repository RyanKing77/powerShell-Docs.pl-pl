---
title: Szerokie (grupowania) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39388197-4ff9-4889-aa32-526011afa1f6
caps.latest.revision: 6
ms.openlocfilehash: e95ec550a7815a76a8bd7f9526dfa405a9644360
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850750"
---
# <a name="wide-view-groupby"></a><span data-ttu-id="fb723-102">Widok szeroki (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="fb723-102">Wide View (GroupBy)</span></span>

<span data-ttu-id="fb723-103">W tym przykładzie pokazano, jak zaimplementować szerokie, który wyświetla grupy [System.Serviceprocess.Servicecontroller? Displayproperty = imię i nazwisko](/dotnet/api/System.ServiceProcess.ServiceController) obiektów zwróconych przez `Get-Service` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fb723-103">This example shows how to implement a wide view that displays groups of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="fb723-104">Aby uzyskać więcej informacji na temat składników szerokie, zobacz [tworzenia szerokiej widoku](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="fb723-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="fb723-105">Aby załadować ten plik formatowania</span><span class="sxs-lookup"><span data-stu-id="fb723-105">To load this formatting file</span></span>

1. <span data-ttu-id="fb723-106">Skopiuj plik XML z sekcji przykład tego tematu do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="fb723-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="fb723-107">Zapisz plik tekstowy.</span><span class="sxs-lookup"><span data-stu-id="fb723-107">Save the text file.</span></span> <span data-ttu-id="fb723-108">Pamiętaj dodać `format.ps1xml` rozszerzenie pliku, aby zidentyfikować go jako plik formatowania.</span><span class="sxs-lookup"><span data-stu-id="fb723-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="fb723-109">Otwórz program Windows PowerShell i uruchom następujące polecenie, aby załadować plik formatowania do bieżącej sesji: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="fb723-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="fb723-110">Ten plik formatowania definiuje wyświetlanie obiektu, który jest już zdefiniowany programu Windows PowerShell, formatowanie plików.</span><span class="sxs-lookup"><span data-stu-id="fb723-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting files.</span></span> <span data-ttu-id="fb723-111">Należy użyć `prependPath` parametru po uruchomieniu polecenia cmdlet, a nie można załadować to formatowanie pliku jako moduł.</span><span class="sxs-lookup"><span data-stu-id="fb723-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="fb723-112">Przedstawiono</span><span class="sxs-lookup"><span data-stu-id="fb723-112">Demonstrates</span></span>

<span data-ttu-id="fb723-113">Ten plik formatowania pokazuje następujące elementy XML:</span><span class="sxs-lookup"><span data-stu-id="fb723-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="fb723-114">[Nazwa](./name-element-for-view-format.md) elementu widoku.</span><span class="sxs-lookup"><span data-stu-id="fb723-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="fb723-115">[ViewSelectedBy](./viewselectedby-element-format.md) element, który definiuje, jakie obiekty są wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="fb723-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="fb723-116">[GroupBy](./groupby-element-for-view-format.md) element, który definiuje, gdy zostanie wyświetlona nowa grupa.</span><span class="sxs-lookup"><span data-stu-id="fb723-116">The [GroupBy](./groupby-element-for-view-format.md) element that defines when a new group is displayed.</span></span>

- <span data-ttu-id="fb723-117">[WideItem](./wideitem-element-for-widecontrol-format.md) element, który definiuje, jakie właściwości jest wyświetlany w widoku.</span><span class="sxs-lookup"><span data-stu-id="fb723-117">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="fb723-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb723-118">Example</span></span>

<span data-ttu-id="fb723-119">Następujący kod XML definiuje szerokie, który wyświetla grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="fb723-119">The following XML defines a wide view that displays groups of objects.</span></span> <span data-ttu-id="fb723-120">Każda nowa grupa została uruchomiona po wartości [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) zmiany właściwości.</span><span class="sxs-lookup"><span data-stu-id="fb723-120">Each new group is started when the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <Label>Service Type</Label>
        <PropertyName>ServiceType</PropertyName>
      </GroupBy>
      <WideControl>
        <WideEntries>
          <WideEntry>
            <WideItem>
              <PropertyName>ServiceName</PropertyName>
            </WideItem>
          </WideEntry>
        </WideEntries>
      </WideControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="fb723-121">W poniższym przykładzie przedstawiono sposób wyświetlania środowiska Windows PowerShell [System.Serviceprocess.Servicecontroller? Displayproperty = imię i nazwisko](/dotnet/api/System.ServiceProcess.ServiceController) obiektów po załadowaniu tego formatu pliku.</span><span class="sxs-lookup"><span data-stu-id="fb723-121">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
   Service Type: Win32OwnProcess

Fax                             FCSAM

   Service Type: Win32ShareProcess

fdPHost                         FDResPub
FontCache

   Service Type: Win32OwnProcess

FontCache3.0.0.0                FSysAgent
FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="fb723-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb723-122">See Also</span></span>

[<span data-ttu-id="fb723-123">Przykłady formatowania plików</span><span class="sxs-lookup"><span data-stu-id="fb723-123">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="fb723-124">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="fb723-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
