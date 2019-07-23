---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguracja, usługa, instalacja
title: Zapisywanie, kompilowanie i stosowanie konfiguracji
ms.openlocfilehash: 8bcd55518b0409b9a4b02ca95f027a0a77eb5300
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372178"
---
> <span data-ttu-id="8bba5-103">Dotyczy: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="8bba5-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="8bba5-104">Zapisywanie, kompilowanie i stosowanie konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8bba5-104">Write, Compile, and Apply a Configuration</span></span>

<span data-ttu-id="8bba5-105">To ćwiczenie polega na utworzeniu i zastosowaniu konfiguracji konfiguracji żądanego stanu (DSC) od początku do końca.</span><span class="sxs-lookup"><span data-stu-id="8bba5-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="8bba5-106">W poniższym przykładzie dowiesz się, jak napisać i zastosować bardzo prostą konfigurację.</span><span class="sxs-lookup"><span data-stu-id="8bba5-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="8bba5-107">Konfiguracja spowoduje, że plik "HelloWorld. txt" istnieje na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="8bba5-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span> <span data-ttu-id="8bba5-108">W przypadku usunięcia pliku Konfiguracja DSC zostanie ponownie utworzona podczas następnej aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="8bba5-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="8bba5-109">Aby zapoznać się z omówieniem usługi DSC i jej działaniem, zobacz [Omówienie konfiguracji żądanego stanu dla deweloperów](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="8bba5-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="8bba5-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8bba5-110">Requirements</span></span>

<span data-ttu-id="8bba5-111">Do uruchomienia tego przykładu będzie potrzebny komputer z uruchomionym programem PowerShell 4,0 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="8bba5-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="8bba5-112">Napisz konfigurację</span><span class="sxs-lookup"><span data-stu-id="8bba5-112">Write the configuration</span></span>

<span data-ttu-id="8bba5-113">[Konfiguracja](configurations.md) DSC to specjalna funkcja programu PowerShell, która definiuje, w jaki sposób należy skonfigurować co najmniej jeden komputer docelowy (węzły).</span><span class="sxs-lookup"><span data-stu-id="8bba5-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="8bba5-114">W ISE programu PowerShell lub w innym edytorze programu PowerShell wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="8bba5-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

> <span data-ttu-id="8bba5-115">! Ważne w przypadku bardziej zaawansowanych scenariuszy, w których należy zaimportować wiele modułów, aby można było pracować z wieloma zasobami DSC w tej samej konfiguracji, upewnij się, że każdy moduł został umieszczony w `Import-DscResource`osobnym wierszu przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="8bba5-115">!Important In more advanced scenarios where multiple modules need to be imported so you can work with many DSC Resources in the same configuration, make sure to put each module in a seperate line using `Import-DscResource`.</span></span>
> <span data-ttu-id="8bba5-116">Jest to łatwiejsze do utrzymania w kontroli źródła i wymagane podczas pracy z usługą DSC w konfiguracji stanu platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="8bba5-116">This is easier to maintain in source control and required when working with DSC in Azure State Configuration.</span></span>
>
> ```powershell
>  Configuration HelloWorld {
>
>   # Import the module that contains the File resource.
>   Import-DscResource -ModuleName PsDesiredStateConfiguration
>   Import-DscResource -ModuleName xWebAdministration
>
> ```

<span data-ttu-id="8bba5-117">Zapisz plik jako "HelloWorld. ps1".</span><span class="sxs-lookup"><span data-stu-id="8bba5-117">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="8bba5-118">Definiowanie konfiguracji jest podobne do definiowania funkcji.</span><span class="sxs-lookup"><span data-stu-id="8bba5-118">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="8bba5-119">Blok **węzła** określa węzeł docelowy, który ma zostać skonfigurowany w tym przypadku `localhost`.</span><span class="sxs-lookup"><span data-stu-id="8bba5-119">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="8bba5-120">Konfiguracja wywołuje jedno [zasoby](../resources/resources.md), `File` zasób.</span><span class="sxs-lookup"><span data-stu-id="8bba5-120">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="8bba5-121">Zasoby wykonują czynności, aby upewnić się, że węzeł docelowy jest w stanie zdefiniowanym przez konfigurację.</span><span class="sxs-lookup"><span data-stu-id="8bba5-121">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="8bba5-122">Kompiluj konfigurację</span><span class="sxs-lookup"><span data-stu-id="8bba5-122">Compile the configuration</span></span>

<span data-ttu-id="8bba5-123">Aby Konfiguracja DSC została zastosowana do węzła, najpierw należy ją skompilować do pliku MOF.</span><span class="sxs-lookup"><span data-stu-id="8bba5-123">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="8bba5-124">Uruchomienie konfiguracji, takiej jak funkcja, spowoduje skompilowanie jednego pliku "MOF" dla każdego węzła zdefiniowanego przez `Node` blok.</span><span class="sxs-lookup"><span data-stu-id="8bba5-124">Running the configuration, like a function, will compile one ".mof" file for every Node defined by the `Node` block.</span></span>
<span data-ttu-id="8bba5-125">Aby można było uruchomić konfigurację, należy umieścić w bieżącym zakresie skrypt "HelloWorld. ps1" jako *Źródło* danych.</span><span class="sxs-lookup"><span data-stu-id="8bba5-125">In order to run the configuration, you need to *dot source* your "HelloWorld.ps1" script into the current scope.</span></span>
<span data-ttu-id="8bba5-126">Aby uzyskać więcej informacji, zobacz [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span><span class="sxs-lookup"><span data-stu-id="8bba5-126">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<!-- markdownlint-disable MD038 -->
<span data-ttu-id="8bba5-127">*Źródło kropki* skrypt "helloworld. ps1", wpisując ścieżkę, w której został zapisany, po `. ` (kropka, spacja).</span><span class="sxs-lookup"><span data-stu-id="8bba5-127">*Dot source* your "HelloWorld.ps1" script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="8bba5-128">Następnie możesz uruchomić konfigurację, wywołując ją jako funkcję.</span><span class="sxs-lookup"><span data-stu-id="8bba5-128">You may then, run your configuration by calling it like a Function.</span></span>
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

<span data-ttu-id="8bba5-129">Spowoduje to wygenerowanie następujących danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="8bba5-129">This generates the following output:</span></span>

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="8bba5-130">Zastosuj konfigurację</span><span class="sxs-lookup"><span data-stu-id="8bba5-130">Apply the configuration</span></span>

<span data-ttu-id="8bba5-131">Teraz, gdy masz skompilowany plik MOF, możesz zastosować konfigurację do węzła docelowego (w tym przypadku komputera lokalnego) przez wywołanie polecenia cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="8bba5-131">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="8bba5-132">Polecenie cmdlet informuje [lokalny Configuration Manager (LCM)](../managing-nodes/metaConfig.md), aparat DSC, aby zastosować konfigurację. `Start-DscConfiguration`</span><span class="sxs-lookup"><span data-stu-id="8bba5-132">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="8bba5-133">LCM wykonuje działania wywołujące zasoby DSC, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="8bba5-133">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="8bba5-134">Użyj poniższego kodu, aby uruchomić `Start-DSCConfiguration` polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8bba5-134">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="8bba5-135">Określ ścieżkę katalogu, w której plik "localhost. MOF" jest przechowywany w `-Path` parametrze.</span><span class="sxs-lookup"><span data-stu-id="8bba5-135">Specify the directory path where your "localhost.mof" is stored to the `-Path` parameter.</span></span> <span data-ttu-id="8bba5-136">Polecenie cmdlet przeszuka katalog określony dla plików "\<ComputerName\>. MOF". `Start-DSCConfiguration`</span><span class="sxs-lookup"><span data-stu-id="8bba5-136">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any "\<computername\>.mof" files.</span></span> <span data-ttu-id="8bba5-137">`Start-DSCConfiguration` Polecenie cmdlet próbuje zastosować każdy plik "MOF", który znajduje się na hoście określonym przez nazwę pliku ("localhost", "Serwer01", "DC-02" itp.).</span><span class="sxs-lookup"><span data-stu-id="8bba5-137">The `Start-DSCConfiguration` cmdlet attempts to apply each ".mof" file it finds to the computername specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="8bba5-138">Jeśli parametr nie jest określony, program `Start-DSCConfiguration` tworzy zadanie w tle w celu wykonania operacji. `-Wait`</span><span class="sxs-lookup"><span data-stu-id="8bba5-138">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="8bba5-139">Określenie **parametru** pozwala obejrzeć pełne dane wyjściowe operacji. `-Verbose`</span><span class="sxs-lookup"><span data-stu-id="8bba5-139">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="8bba5-140">`-Wait`i `-Verbose` są parametrami opcjonalnymi.</span><span class="sxs-lookup"><span data-stu-id="8bba5-140">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="8bba5-141">Testowanie konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8bba5-141">Test the configuration</span></span>

<span data-ttu-id="8bba5-142">Po zakończeniu `Start-DSCConfiguration` tego polecenia cmdlet powinien zostać wyświetlony plik HelloWorld. txt w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="8bba5-142">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a "HelloWorld.txt" file in the location you specified.</span></span> <span data-ttu-id="8bba5-143">Zawartość można sprawdzić za pomocą polecenia cmdlet [Get-Content](/powershell/module/microsoft.powershell.management/get-content) .</span><span class="sxs-lookup"><span data-stu-id="8bba5-143">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="8bba5-144">Możesz również *przetestować* bieżący stan za pomocą polecenia [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="8bba5-144">You can also *test* the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="8bba5-145">Dane wyjściowe powinny mieć wartość "true", jeśli węzeł jest aktualnie zgodny z zastosowaną konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="8bba5-145">The output should be "True" if the Node is currently compliant with the applied Configuration.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a><span data-ttu-id="8bba5-146">Ponowne zastosowanie konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8bba5-146">Re-applying the configuration</span></span>

<span data-ttu-id="8bba5-147">Aby zobaczyć, że konfiguracja zostanie zastosowana ponownie, można usunąć plik tekstowy utworzony przez konfigurację.</span><span class="sxs-lookup"><span data-stu-id="8bba5-147">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="8bba5-148">Użyj `Start-DSCConfiguration` polecenia cmdlet `-UseExisting` z parametrem.</span><span class="sxs-lookup"><span data-stu-id="8bba5-148">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="8bba5-149">`-UseExisting` Parametr instruujeponowniezastosowaćplik"Current.MOF",któryreprezentuje`Start-DSCConfiguration` ostatnio zastosowaną konfigurację.</span><span class="sxs-lookup"><span data-stu-id="8bba5-149">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="8bba5-150">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="8bba5-150">Next steps</span></span>

- <span data-ttu-id="8bba5-151">Dowiedz się więcej na temat konfiguracji DSC w [konfiguracjach DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="8bba5-151">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="8bba5-152">Zobacz, jakie zasoby DSC są dostępne i jak tworzyć niestandardowe zasoby DSC w [zasobach DSC](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="8bba5-152">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="8bba5-153">Znajdź konfiguracje i zasoby DSC w [Galeria programu PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="8bba5-153">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
