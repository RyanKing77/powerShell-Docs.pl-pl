---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Żądany stan konfiguracji Szybki Start"
ms.openlocfilehash: 295a78f3fd85464239d51d7be0defa04d2344689
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/13/2017
---
> <span data-ttu-id="4da5b-103">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4da5b-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="desired-state-configuration-quick-start"></a><span data-ttu-id="4da5b-104">Żądany stan konfiguracji Szybki Start</span><span class="sxs-lookup"><span data-stu-id="4da5b-104">Desired State Configuration Quick Start</span></span>

<span data-ttu-id="4da5b-105">Tego ćwiczenia przeprowadzi Cię przez tworzenia i stosowania konfiguracji konfiguracji żądanego stanu (DSC) od początku do końca.</span><span class="sxs-lookup"><span data-stu-id="4da5b-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="4da5b-106">Przykład użyjemy gwarantuje, że serwer ma `Web-Server` włączona funkcja (IIS), a zawartość witryny sieci Web "Hello World" proste znajduje się w `intepub\wwwroot` katalogu tego serwera.</span><span class="sxs-lookup"><span data-stu-id="4da5b-106">The example we'll use ensures that a server has the `Web-Server` (IIS) feature enabled, and that the content for a simple "Hello World" website is present in the `intepub\wwwroot` directory of that server.</span></span>

<span data-ttu-id="4da5b-107">Omówienie usługi Konfiguracja DSC jest i jak działa, zobacz [żądany przegląd stanu konfiguracji dla inne osoby podejmujące decyzje](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="4da5b-107">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="4da5b-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4da5b-108">Requirements</span></span>

<span data-ttu-id="4da5b-109">Aby uruchomić ten przykład, należy komputer z systemem Windows Server 2012 lub nowszym i programu PowerShell 4.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="4da5b-109">To run this example, you will need a computer running Windows Server 2012 or later and PowerShell 4.0 or later.</span></span>

## <a name="write-and-place-the-indexhtm-file"></a><span data-ttu-id="4da5b-110">Zapis i umieścić go index.htm</span><span class="sxs-lookup"><span data-stu-id="4da5b-110">Write and place the index.htm file</span></span>

<span data-ttu-id="4da5b-111">Najpierw utworzymy plik HTML, który będzie używany jako zawartości witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4da5b-111">First, we'll create the HTML file that we will use as the website content.</span></span>

<span data-ttu-id="4da5b-112">W folderze głównym, Utwórz folder o nazwie `test`.</span><span class="sxs-lookup"><span data-stu-id="4da5b-112">In your root folder, create a folder named `test`.</span></span>

<span data-ttu-id="4da5b-113">W edytorze tekstów należy wpisać następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="4da5b-113">In a text editor, type the following text:</span></span>

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

<span data-ttu-id="4da5b-114">Zapisz jako `index.htm` w `test` folderu utworzonego wcześniej.</span><span class="sxs-lookup"><span data-stu-id="4da5b-114">Save this as `index.htm` in the `test` folder you created earlier.</span></span> 

## <a name="write-the-configuration"></a><span data-ttu-id="4da5b-115">Zapisać konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4da5b-115">Write the configuration</span></span>

<span data-ttu-id="4da5b-116">A [konfiguracji DSC](configurations.md) jest specjalnych funkcji programu PowerShell, która definiuje sposób skonfigurowania jednego lub więcej komputerów docelowych (węzłów).</span><span class="sxs-lookup"><span data-stu-id="4da5b-116">A [DSC configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (nodes).</span></span>

<span data-ttu-id="4da5b-117">W programie PowerShell ISE wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="4da5b-117">In the PowerShell ISE, type the following:</span></span>

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

<span data-ttu-id="4da5b-118">Zapisz plik jako `WebsiteTest.ps1`.</span><span class="sxs-lookup"><span data-stu-id="4da5b-118">Save the file as `WebsiteTest.ps1`.</span></span>

<span data-ttu-id="4da5b-119">Widać wygląda funkcji programu PowerShell, dodając słowa kluczowego **konfiguracji** używany przed nazwę funkcji.</span><span class="sxs-lookup"><span data-stu-id="4da5b-119">You can see that it looks like a PowerShell function, with the addition of the keyword **Configuration** used before the name of the function.</span></span>

<span data-ttu-id="4da5b-120">**Węzła** bloku określa węzeł docelowy jest skonfigurowany w tym przypadku `localhost`.</span><span class="sxs-lookup"><span data-stu-id="4da5b-120">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="4da5b-121">Konfiguracja wymaga dwóch [zasobów](resources.md), [WindowsFeature](windowsFeatureResource.md) i [pliku](fileResource.md).</span><span class="sxs-lookup"><span data-stu-id="4da5b-121">The configuration calls two [resources](resources.md), [WindowsFeature](windowsFeatureResource.md) and [File](fileResource.md).</span></span>
<span data-ttu-id="4da5b-122">Zasoby czy pracy zapewnienie węzeł docelowy jest w stanie określonym w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4da5b-122">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="4da5b-123">Konfiguracja kompilacji</span><span class="sxs-lookup"><span data-stu-id="4da5b-123">Compile the configuration</span></span>

<span data-ttu-id="4da5b-124">Dla konfiguracji DSC ma zostać zastosowany do węzła go musi najpierw zostać skompilowany w pliku MOF.</span><span class="sxs-lookup"><span data-stu-id="4da5b-124">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="4da5b-125">Aby to zrobić, należy uruchomić konfiguracji, takich jak funkcja.</span><span class="sxs-lookup"><span data-stu-id="4da5b-125">To do this, you run the configuration like a function.</span></span>
<span data-ttu-id="4da5b-126">W konsoli programu PowerShell przejdź do folderu, w którym zapisano konfigurację i uruchom następujące polecenia, aby skompilować konfigurację do pliku MOF:</span><span class="sxs-lookup"><span data-stu-id="4da5b-126">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following commands to compile the configuration into a MOF file:</span></span>

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

<span data-ttu-id="4da5b-127">Spowoduje to wygenerowanie następujących danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="4da5b-127">This generates the following output:</span></span>

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

<span data-ttu-id="4da5b-128">Pierwszy wiersz sprawia, że funkcja konfiguracji jest dostępne w konsoli.</span><span class="sxs-lookup"><span data-stu-id="4da5b-128">The first line makes the configuration function available in the console.</span></span>
<span data-ttu-id="4da5b-129">Drugi wiersz uruchamia konfigurację.</span><span class="sxs-lookup"><span data-stu-id="4da5b-129">The second line runs the configuration.</span></span>
<span data-ttu-id="4da5b-130">Wynik jest, że nowy folder o nazwie `WebsiteTest` zostanie utworzona jako podfolder bieżącego folderu.</span><span class="sxs-lookup"><span data-stu-id="4da5b-130">The result is that a new folder, named `WebsiteTest` is created as a subfolder of the current folder.</span></span>
<span data-ttu-id="4da5b-131">`WebsiteTest` Folder zawiera plik o nazwie `localhost.mof`.</span><span class="sxs-lookup"><span data-stu-id="4da5b-131">The `WebsiteTest` folder contains a file named `localhost.mof`.</span></span>
<span data-ttu-id="4da5b-132">Jest to plik, który można zastosować do węzła docelowego.</span><span class="sxs-lookup"><span data-stu-id="4da5b-132">It is this file that can then be applied to the target node.</span></span>

## <a name="apply-the-configuration"></a><span data-ttu-id="4da5b-133">Zastosuj konfigurację</span><span class="sxs-lookup"><span data-stu-id="4da5b-133">Apply the configuration</span></span>

<span data-ttu-id="4da5b-134">Teraz, gdy masz skompilowanych MOF konfiguracji można stosować do węzła docelowego (w tym przypadku komputer lokalny) przez wywołanie metody [Start DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4da5b-134">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.</span></span>

<span data-ttu-id="4da5b-135">`Start-DscConfiguration` Informuje polecenia cmdlet [lokalnego Configuration Manager (LCM)](metaConfig.md), która jest aparat DSC, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="4da5b-135">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](metaConfig.md), which is the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="4da5b-136">LCM działa wywoływania zasobów DSC, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="4da5b-136">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="4da5b-137">W konsoli programu PowerShell przejdź do folderu, w którym zapisano konfigurację i uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="4da5b-137">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following command:</span></span>

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a><span data-ttu-id="4da5b-138">Przetestuj konfigurację</span><span class="sxs-lookup"><span data-stu-id="4da5b-138">Test the configuration</span></span>

<span data-ttu-id="4da5b-139">Możesz wywołać [Get-DscConfigurationStatus](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus) polecenia cmdlet, aby zobaczyć, czy konfiguracja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4da5b-139">You can call the [Get-DscConfigurationStatus](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet to see whether the configuration succeeded.</span></span> 

<span data-ttu-id="4da5b-140">Można również sprawdzić wyniki bezpośrednio, w tym przypadku przechodząc do `http://localhost/` w przeglądarce sieci web.</span><span class="sxs-lookup"><span data-stu-id="4da5b-140">You can also test the results directly, in this case by browsing to `http://localhost/` in a web browser.</span></span>
<span data-ttu-id="4da5b-141">Powinna zostać wyświetlona strona "Hello World" HTML, który został utworzony jako pierwszy krok w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4da5b-141">You should see the "Hello World" HTML page you created as the first step in this example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4da5b-142">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="4da5b-142">Next steps</span></span>

- <span data-ttu-id="4da5b-143">Dowiedz się więcej o konfiguracji DSC w [konfiguracji DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="4da5b-143">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="4da5b-144">Zobacz, jakie zasoby DSC są dostępne oraz sposobu tworzenia niestandardowych zasobów DSC w [zasobów DSC](resources.md).</span><span class="sxs-lookup"><span data-stu-id="4da5b-144">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](resources.md).</span></span>
- <span data-ttu-id="4da5b-145">Znajdź konfiguracji DSC i zasobów w [galerii programu PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="4da5b-145">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>



