---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, usługi, Instalator
title: Zapis, skompilowania i zastosowania konfiguracji
ms.openlocfilehash: fa4d98fd12202439ba7025fd8af3fa398653ca05
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404795"
---
> <span data-ttu-id="b2a40-103">Dotyczy: Program Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b2a40-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="b2a40-104">Zapis, skompilowania i zastosowania konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b2a40-104">Write, Compile, and Apply a Configuration</span></span>

<span data-ttu-id="b2a40-105">To ćwiczenie zawiera opis sposobu tworzenia i stosowania konfiguracji Desired State Configuration (DSC), od początku do końca.</span><span class="sxs-lookup"><span data-stu-id="b2a40-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="b2a40-106">W poniższym przykładzie dowiesz się, jak pisać i Zastosuj konfigurację bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="b2a40-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="b2a40-107">Konfiguracja będzie upewnij się, że plik "HelloWorld.txt" istnieje na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="b2a40-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span> <span data-ttu-id="b2a40-108">Jeśli usuniesz plik, DSC ponownie utworzy go następnym razem, który aktualizuje.</span><span class="sxs-lookup"><span data-stu-id="b2a40-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="b2a40-109">Aby uzyskać omówienie DSC i jak to działa, zobacz [omówienie Desired State Configuration dla deweloperów](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="b2a40-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="b2a40-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2a40-110">Requirements</span></span>

<span data-ttu-id="b2a40-111">Aby uruchomić ten przykład, należy komputer z systemem programu PowerShell w wersji 4.0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="b2a40-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="b2a40-112">Zapisz konfigurację</span><span class="sxs-lookup"><span data-stu-id="b2a40-112">Write the configuration</span></span>

<span data-ttu-id="b2a40-113">DSC [konfiguracji](configurations.md) jest specjalną funkcję programu PowerShell, który definiuje, jak chcesz skonfigurować jeden lub więcej komputerów docelowych (węzły).</span><span class="sxs-lookup"><span data-stu-id="b2a40-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="b2a40-114">W środowisku ISE programu PowerShell lub innego edytora programu PowerShell wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="b2a40-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

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

<span data-ttu-id="b2a40-115">Zapisz plik jako "HelloWorld.ps1".</span><span class="sxs-lookup"><span data-stu-id="b2a40-115">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="b2a40-116">Definiowanie konfiguracji jest podobne do definiowania funkcji.</span><span class="sxs-lookup"><span data-stu-id="b2a40-116">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="b2a40-117">**Węzła** bloku określa węzeł docelowy należy skonfigurować w tym przypadku `localhost`.</span><span class="sxs-lookup"><span data-stu-id="b2a40-117">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="b2a40-118">Konfiguracja wywołuje jedną [zasobów](../resources/resources.md), `File` zasobów.</span><span class="sxs-lookup"><span data-stu-id="b2a40-118">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="b2a40-119">Zasoby wykonują pracę zapewnienia, że węzeł docelowy jest w stanie zdefiniowane przez tą konfigurację.</span><span class="sxs-lookup"><span data-stu-id="b2a40-119">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="b2a40-120">Kompilowanie konfiguracji w</span><span class="sxs-lookup"><span data-stu-id="b2a40-120">Compile the configuration</span></span>

<span data-ttu-id="b2a40-121">Dla konfiguracji DSC do zastosowania do węzła jej muszą najpierw być skompilowane w pliku MOF.</span><span class="sxs-lookup"><span data-stu-id="b2a40-121">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="b2a40-122">Uruchamianie konfiguracji, takich jak funkcja zostanie skompilowany jeden plik "MOF" dla każdego węzła zdefiniowane przez `Node` bloku.</span><span class="sxs-lookup"><span data-stu-id="b2a40-122">Running the configuration, like a function, will compile one ".mof" file for every Node defined by the `Node` block.</span></span>
<span data-ttu-id="b2a40-123">Aby uruchomić konfigurację, trzeba *źródła z dot* skryptu "HelloWorld.ps1" w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="b2a40-123">In order to run the configuration, you need to *dot source* your "HelloWorld.ps1" script into the current scope.</span></span>
<span data-ttu-id="b2a40-124">Aby uzyskać więcej informacji, zobacz [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span><span class="sxs-lookup"><span data-stu-id="b2a40-124">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<span data-ttu-id="b2a40-125">*Źródło z dot* skryptu "HelloWorld.ps1", wpisując w polu Ścieżka, w której przechowywane, po `. ` (kropka, miejsca).</span><span class="sxs-lookup"><span data-stu-id="b2a40-125">*Dot source* your "HelloWorld.ps1" script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="b2a40-126">Następnie możesz uruchomić konfigurację wywołując takich jak funkcja.</span><span class="sxs-lookup"><span data-stu-id="b2a40-126">You may then, run your configuration by calling it like a Function.</span></span>

```powershell
. C:\Scripts\WebsiteTest.ps1
HelloWolrd
```

<span data-ttu-id="b2a40-127">Spowoduje to wygenerowanie następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="b2a40-127">This generates the following output:</span></span>

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="b2a40-128">Zastosuj konfigurację</span><span class="sxs-lookup"><span data-stu-id="b2a40-128">Apply the configuration</span></span>

<span data-ttu-id="b2a40-129">Teraz, gdy masz skompilowany plik MOF, konfigurację można zastosować do węzła docelowego (w tym przypadku komputer lokalny) przez wywołanie metody [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b2a40-129">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="b2a40-130">`Start-DscConfiguration` Informuje polecenia cmdlet [lokalnego Configuration Manager (LCM)](../managing-nodes/metaConfig.md), aparatu DSC, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="b2a40-130">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="b2a40-131">LCM działa wywoływania zasoby DSC, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="b2a40-131">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="b2a40-132">Użyj poniższego kodu do wykonania `Start-DSCConfiguration` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b2a40-132">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="b2a40-133">Określ ścieżkę katalogu, do przechowywania Twojego "localhost.mof" Aby `-Path` parametru.</span><span class="sxs-lookup"><span data-stu-id="b2a40-133">Specify the directory path where your "localhost.mof" is stored to the `-Path` parameter.</span></span> <span data-ttu-id="b2a40-134">`Start-DSCConfiguration` Polecenia cmdlet wygląda za pośrednictwem katalogu określonym dla dowolnego "\<computername\>MOF" pliki.</span><span class="sxs-lookup"><span data-stu-id="b2a40-134">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any "\<computername\>.mof" files.</span></span> <span data-ttu-id="b2a40-135">`Start-DSCConfiguration` Polecenie cmdlet podejmie próbę dotyczą każdego pliku "MOF" znajdzie computername określony przez nazwę pliku ("localhost", "Serwer01", "dc-02" itp.).</span><span class="sxs-lookup"><span data-stu-id="b2a40-135">The `Start-DSCConfiguration` cmdlet attempts to apply each ".mof" file it finds to the computername specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="b2a40-136">Jeśli `-Wait` parametr nie jest określony, `Start-DSCConfiguration` tworzy zadania w tle do wykonania tej operacji.</span><span class="sxs-lookup"><span data-stu-id="b2a40-136">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="b2a40-137">Określanie `-Verbose` parametr umożliwia Obejrzyj **pełne** wynik operacji.</span><span class="sxs-lookup"><span data-stu-id="b2a40-137">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="b2a40-138">`-Wait`, a `-Verbose` są oba parametry opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="b2a40-138">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="b2a40-139">Testowanie konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b2a40-139">Test the configuration</span></span>

<span data-ttu-id="b2a40-140">Raz `Start-DSCConfiguration` polecenie cmdlet zostało zakończone, powinien zostać wyświetlony plik "HelloWorld.txt" w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="b2a40-140">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a "HelloWorld.txt" file in the location you specified.</span></span> <span data-ttu-id="b2a40-141">Można sprawdzić zawartość z [pobrania zawartości](/powershell/module/microsoft.powershell.management/get-content) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b2a40-141">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="b2a40-142">Możesz również *test* bieżący stan za pomocą [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="b2a40-142">You can also *test* the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="b2a40-143">Dane wyjściowe powinny być "True", jeśli węzeł jest aktualnie zgodny ze stosowanych konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b2a40-143">The output should be "True" if the Node is currently compliant with the applied Configuration.</span></span>

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

## <a name="re-applying-the-configuration"></a><span data-ttu-id="b2a40-144">Ponowne zastosowanie konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b2a40-144">Re-applying the configuration</span></span>

<span data-ttu-id="b2a40-145">Aby sprawdzić konfigurację, ponownie zastosowane, można usunąć pliku tekstowego, utworzone przez konfigurację.</span><span class="sxs-lookup"><span data-stu-id="b2a40-145">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="b2a40-146">Użycie `Start-DSCConfiguration` polecenia cmdlet z `-UseExisting` parametru.</span><span class="sxs-lookup"><span data-stu-id="b2a40-146">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="b2a40-147">`-UseExisting` Powoduje, że parametr `Start-DSCConfiguration` Ponowne zgłoszenie chęci pliku "current.mof", która reprezentuje ostatnio pomyślnie zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="b2a40-147">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="b2a40-148">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="b2a40-148">Next steps</span></span>

- <span data-ttu-id="b2a40-149">Dowiedz się więcej na temat konfiguracji DSC w [konfiguracje DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="b2a40-149">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="b2a40-150">Zobacz, jakie zasoby DSC są dostępne i jak tworzyć niestandardowe zasoby DSC w [zasoby DSC](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="b2a40-150">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="b2a40-151">Konfiguracje DSC i zasoby w [galerii programu PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="b2a40-151">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
