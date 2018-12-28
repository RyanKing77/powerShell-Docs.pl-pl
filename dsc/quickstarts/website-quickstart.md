---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Przewodnik Szybki Start — tworzenie witryny sieci Web za pomocą DSC
ms.openlocfilehash: c62e2d8af46bf74c4dd13069ddff6cc39763a209
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404676"
---
> <span data-ttu-id="670c8-103">Dotyczy: Program Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="670c8-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="quickstart---create-a-website-with-dsc"></a><span data-ttu-id="670c8-104">Przewodnik Szybki Start — tworzenie witryny sieci Web za pomocą DSC</span><span class="sxs-lookup"><span data-stu-id="670c8-104">Quickstart - Create a website with DSC</span></span>

<span data-ttu-id="670c8-105">To ćwiczenie zawiera opis sposobu tworzenia i stosowania konfiguracji Desired State Configuration (DSC), od początku do końca.</span><span class="sxs-lookup"><span data-stu-id="670c8-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="670c8-106">Przykład użyjemy gwarantuje, że serwer ma `Web-Server` aktywna (IIS), a zawartość prostą witrynę sieci Web "Hello World" znajduje się w `intepub\wwwroot` katalogu tego serwera.</span><span class="sxs-lookup"><span data-stu-id="670c8-106">The example we'll use ensures that a server has the `Web-Server` (IIS) feature enabled, and that the content for a simple "Hello World" website is present in the `intepub\wwwroot` directory of that server.</span></span>

<span data-ttu-id="670c8-107">Aby uzyskać omówienie DSC i jak to działa, zobacz [Przegląd Desired State Configuration dla osób podejmujących](../overview/decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="670c8-107">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Decision Makers](../overview/decisionMaker.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="670c8-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="670c8-108">Requirements</span></span>

<span data-ttu-id="670c8-109">Aby uruchomić ten przykład, należy komputer z systemem Windows Server 2012 lub nowszego oraz programu PowerShell 4.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="670c8-109">To run this example, you will need a computer running Windows Server 2012 or later and PowerShell 4.0 or later.</span></span>

## <a name="write-and-place-the-indexhtm-file"></a><span data-ttu-id="670c8-110">Pisanie i umieścić ten plik index.htm</span><span class="sxs-lookup"><span data-stu-id="670c8-110">Write and place the index.htm file</span></span>

<span data-ttu-id="670c8-111">Najpierw utworzymy plik HTML, który będzie używany jako zawartość witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="670c8-111">First, we'll create the HTML file that we will use as the website content.</span></span>

<span data-ttu-id="670c8-112">W folderze głównym, Utwórz folder o nazwie `test`.</span><span class="sxs-lookup"><span data-stu-id="670c8-112">In your root folder, create a folder named `test`.</span></span>

<span data-ttu-id="670c8-113">W edytorze tekstów wpisz następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="670c8-113">In a text editor, type the following text:</span></span>

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

<span data-ttu-id="670c8-114">Zapisz jako `index.htm` w `test` folderu utworzonego wcześniej.</span><span class="sxs-lookup"><span data-stu-id="670c8-114">Save this as `index.htm` in the `test` folder you created earlier.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="670c8-115">Zapisz konfigurację</span><span class="sxs-lookup"><span data-stu-id="670c8-115">Write the configuration</span></span>

<span data-ttu-id="670c8-116">A [konfiguracji DSC](../configurations/configurations.md) jest specjalną funkcję programu PowerShell, który definiuje, jak chcesz skonfigurować jeden lub więcej komputerów docelowych (węzły).</span><span class="sxs-lookup"><span data-stu-id="670c8-116">A [DSC configuration](../configurations/configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (nodes).</span></span>

<span data-ttu-id="670c8-117">Wpisz następujące polecenie w środowisku PowerShell ISE:</span><span class="sxs-lookup"><span data-stu-id="670c8-117">In the PowerShell ISE, type the following:</span></span>

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

<span data-ttu-id="670c8-118">Zapisz plik jako `WebsiteTest.ps1`.</span><span class="sxs-lookup"><span data-stu-id="670c8-118">Save the file as `WebsiteTest.ps1`.</span></span>

<span data-ttu-id="670c8-119">Zostanie wyświetlony, wygląda na funkcję programu PowerShell dodając słowa kluczowego **konfiguracji** używane przed nazwą funkcji.</span><span class="sxs-lookup"><span data-stu-id="670c8-119">You can see that it looks like a PowerShell function, with the addition of the keyword **Configuration** used before the name of the function.</span></span>

<span data-ttu-id="670c8-120">**Węzła** bloku określa węzeł docelowy należy skonfigurować w tym przypadku `localhost`.</span><span class="sxs-lookup"><span data-stu-id="670c8-120">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="670c8-121">Konfiguracja wymaga dwóch [zasobów](../resources/resources.md), **WindowsFeature** i **pliku**.</span><span class="sxs-lookup"><span data-stu-id="670c8-121">The configuration calls two [resources](../resources/resources.md), **WindowsFeature** and **File**.</span></span>
<span data-ttu-id="670c8-122">Zasoby wykonują pracę zapewnienia, że węzeł docelowy jest w stanie zdefiniowane przez tą konfigurację.</span><span class="sxs-lookup"><span data-stu-id="670c8-122">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="670c8-123">Kompilowanie konfiguracji w</span><span class="sxs-lookup"><span data-stu-id="670c8-123">Compile the configuration</span></span>

<span data-ttu-id="670c8-124">Dla konfiguracji DSC do zastosowania do węzła jej muszą najpierw być skompilowane w pliku MOF.</span><span class="sxs-lookup"><span data-stu-id="670c8-124">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="670c8-125">Aby to zrobić, należy uruchomić konfiguracji, takich jak funkcja.</span><span class="sxs-lookup"><span data-stu-id="670c8-125">To do this, you run the configuration like a function.</span></span>
<span data-ttu-id="670c8-126">W konsoli programu PowerShell przejdź do tego samego folderu, w której zapisano konfigurację i uruchom następujące polecenia, aby skompilować konfigurację do pliku MOF:</span><span class="sxs-lookup"><span data-stu-id="670c8-126">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following commands to compile the configuration into a MOF file:</span></span>

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

<span data-ttu-id="670c8-127">Spowoduje to wygenerowanie następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="670c8-127">This generates the following output:</span></span>

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

<span data-ttu-id="670c8-128">Pierwszy wiersz sprawia, że funkcja konfiguracji jest dostępny w konsoli.</span><span class="sxs-lookup"><span data-stu-id="670c8-128">The first line makes the configuration function available in the console.</span></span>
<span data-ttu-id="670c8-129">Drugi wiersz uruchamia konfigurację.</span><span class="sxs-lookup"><span data-stu-id="670c8-129">The second line runs the configuration.</span></span>
<span data-ttu-id="670c8-130">Wynik jest, że nowy folder o nazwie `WebsiteTest` jest tworzony jako podfolder bieżącego folderu.</span><span class="sxs-lookup"><span data-stu-id="670c8-130">The result is that a new folder, named `WebsiteTest` is created as a subfolder of the current folder.</span></span>
<span data-ttu-id="670c8-131">`WebsiteTest` Folder zawiera plik o nazwie `localhost.mof`.</span><span class="sxs-lookup"><span data-stu-id="670c8-131">The `WebsiteTest` folder contains a file named `localhost.mof`.</span></span>
<span data-ttu-id="670c8-132">Jest to plik, który można następnie zastosować do węzła docelowego.</span><span class="sxs-lookup"><span data-stu-id="670c8-132">It is this file that can then be applied to the target node.</span></span>

## <a name="apply-the-configuration"></a><span data-ttu-id="670c8-133">Zastosuj konfigurację</span><span class="sxs-lookup"><span data-stu-id="670c8-133">Apply the configuration</span></span>

<span data-ttu-id="670c8-134">Teraz, gdy masz skompilowany plik MOF, konfigurację można zastosować do węzła docelowego (w tym przypadku komputer lokalny) przez wywołanie metody [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="670c8-134">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="670c8-135">`Start-DscConfiguration` Informuje polecenia cmdlet [lokalnego Configuration Manager (LCM)](../managing-nodes/metaConfig.md), czyli aparatu DSC, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="670c8-135">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), which is the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="670c8-136">LCM działa wywoływania zasoby DSC, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="670c8-136">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="670c8-137">W konsoli programu PowerShell przejdź do folderu, w której zapisano konfigurację, a następnie uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="670c8-137">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following command:</span></span>

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a><span data-ttu-id="670c8-138">Testowanie konfiguracji</span><span class="sxs-lookup"><span data-stu-id="670c8-138">Test the configuration</span></span>

<span data-ttu-id="670c8-139">Możesz wywołać [Get DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) polecenia cmdlet, aby zobaczyć, czy konfiguracja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="670c8-139">You can call the [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet to see whether the configuration succeeded.</span></span>

<span data-ttu-id="670c8-140">Możesz również przetestować wyniki bezpośrednio, w tym przypadku, przechodząc do `http://localhost/` w przeglądarce sieci web.</span><span class="sxs-lookup"><span data-stu-id="670c8-140">You can also test the results directly, in this case by browsing to `http://localhost/` in a web browser.</span></span>
<span data-ttu-id="670c8-141">Powinna zostać wyświetlona strona "Hello World" HTML, który został utworzony, w pierwszym kroku w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="670c8-141">You should see the "Hello World" HTML page you created as the first step in this example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="670c8-142">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="670c8-142">Next steps</span></span>

- <span data-ttu-id="670c8-143">Dowiedz się więcej na temat konfiguracji DSC w [konfiguracje DSC](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="670c8-143">Find out more about DSC configurations at [DSC configurations](../configurations/configurations.md).</span></span>
- <span data-ttu-id="670c8-144">Zobacz, jakie zasoby DSC są dostępne i jak tworzyć niestandardowe zasoby DSC w [zasoby DSC](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="670c8-144">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="670c8-145">Konfiguracje DSC i zasoby w [galerii programu PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="670c8-145">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
