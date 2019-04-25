---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Konfiguracje DSC
ms.openlocfilehash: 6af27f442de3080facd65892c713c989d0e388c5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080179"
---
# <a name="dsc-configurations"></a><span data-ttu-id="5456b-103">Konfiguracje DSC</span><span class="sxs-lookup"><span data-stu-id="5456b-103">DSC Configurations</span></span>

> <span data-ttu-id="5456b-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5456b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="5456b-105">Konfiguracje DSC są skrypty programu PowerShell, definiujące specjalny rodzaj funkcji.</span><span class="sxs-lookup"><span data-stu-id="5456b-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span>
<span data-ttu-id="5456b-106">Aby zdefiniować konfigurację, należy użyć programu PowerShell — słowo kluczowe **konfiguracji**.</span><span class="sxs-lookup"><span data-stu-id="5456b-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

<span data-ttu-id="5456b-107">Zapisz skrypt jako `.ps1` pliku.</span><span class="sxs-lookup"><span data-stu-id="5456b-107">Save the script as a `.ps1` file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="5456b-108">Składnia konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5456b-108">Configuration syntax</span></span>

<span data-ttu-id="5456b-109">Skrypt konfiguracji składa się z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="5456b-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="5456b-110">**Konfiguracji** bloku.</span><span class="sxs-lookup"><span data-stu-id="5456b-110">The **Configuration** block.</span></span> <span data-ttu-id="5456b-111">Jest to blok skryptu najbardziej zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="5456b-111">This is the outermost script block.</span></span> <span data-ttu-id="5456b-112">Można zdefiniować przy użyciu **konfiguracji** — słowo kluczowe i podając nazwę.</span><span class="sxs-lookup"><span data-stu-id="5456b-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="5456b-113">W takim przypadku nazwa konfiguracji jest "MyDscConfiguration".</span><span class="sxs-lookup"><span data-stu-id="5456b-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="5456b-114">Co najmniej jeden **węzła** bloków.</span><span class="sxs-lookup"><span data-stu-id="5456b-114">One or more **Node** blocks.</span></span> <span data-ttu-id="5456b-115">Te definiują węzłów (maszyn wirtualnych lub komputerach), które konfigurujesz.</span><span class="sxs-lookup"><span data-stu-id="5456b-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="5456b-116">W powyższej konfiguracji, ma jedną **węzła** bloku, który jest przeznaczony dla komputera o nazwie "TEST-PC1".</span><span class="sxs-lookup"><span data-stu-id="5456b-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span> <span data-ttu-id="5456b-117">Blok węzła może akceptować wiele nazw komputerów.</span><span class="sxs-lookup"><span data-stu-id="5456b-117">The Node block can accept multiple computer names.</span></span>
- <span data-ttu-id="5456b-118">Jeden lub więcej bloków zasobów.</span><span class="sxs-lookup"><span data-stu-id="5456b-118">One or more resource blocks.</span></span> <span data-ttu-id="5456b-119">Jest to, gdzie konfiguracja ustawia właściwości zasobów, które go służy do konfigurowania.</span><span class="sxs-lookup"><span data-stu-id="5456b-119">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="5456b-120">W tym przypadku istnieją dwa bloki zasobów, z których każde wywołanie zasobu "WindowsFeature".</span><span class="sxs-lookup"><span data-stu-id="5456b-120">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="5456b-121">W ramach **konfiguracji** bloku, można zrobić wszystko, co zwykle można w funkcji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5456b-121">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="5456b-122">Na przykład w poprzednim przykładzie, jeśli nie chcesz ciężko code nazwę komputera docelowego w konfiguracji, można dodać parametr dla nazwy węzła:</span><span class="sxs-lookup"><span data-stu-id="5456b-122">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

<span data-ttu-id="5456b-123">W tym przykładzie Określ nazwę węzła przez przekazanie jej jako **ComputerName** parametru podczas kompilowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5456b-123">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="5456b-124">Nazwa, wartość domyślna to "localhost".</span><span class="sxs-lookup"><span data-stu-id="5456b-124">The name defaults to "localhost".</span></span>

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

<span data-ttu-id="5456b-125">**Węzła** bloku mogą również akceptować wiele nazw komputerów.</span><span class="sxs-lookup"><span data-stu-id="5456b-125">The **Node** block can also accept multiple computer names.</span></span> <span data-ttu-id="5456b-126">W powyższym przykładzie, można użyć `-ComputerName` parametr lub — dostęp próbny rozdzielonych przecinkami listę komputerów, bezpośrednio do **węzła** bloku.</span><span class="sxs-lookup"><span data-stu-id="5456b-126">In the above example, you can either use the `-ComputerName` parameter, or pass a comma-separated list of computers directly to the **Node** block.</span></span>

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

<span data-ttu-id="5456b-127">Podczas określania listy komputerów do **węzła** bloku, z w ramach konfiguracji, należy użyć tablicy notacji.</span><span class="sxs-lookup"><span data-stu-id="5456b-127">When specifying a list of computers to the **Node** block, from within a Configuration, you need to use array-notation.</span></span>

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

## <a name="compiling-the-configuration"></a><span data-ttu-id="5456b-128">Kompilowanie konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5456b-128">Compiling the configuration</span></span>

<span data-ttu-id="5456b-129">Przed może przyjąć konfiguracji, należy skompilować go na dokument MOF.</span><span class="sxs-lookup"><span data-stu-id="5456b-129">Before you can enact a configuration, you have to compile it into a MOF document.</span></span>
<span data-ttu-id="5456b-130">Możesz to zrobić, wywołując konfiguracji, takie jak wywoływałby funkcję programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5456b-130">You do this by calling the configuration like you would call a PowerShell function.</span></span>
<span data-ttu-id="5456b-131">Ostatni wiersz przykład zawierający tylko nazwę konfiguracji, wywołuje konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5456b-131">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="5456b-132">Aby wywołać konfigurację, funkcja musi być w zakresie globalnym (podobnie jak w przypadku innych funkcji programu PowerShell).</span><span class="sxs-lookup"><span data-stu-id="5456b-132">To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span>
> <span data-ttu-id="5456b-133">Ułatwia to możliwe albo przez "Funkcja dot-sourcing" skryptu, lub przez uruchomienie skryptu konfiguracji przy użyciu klawisza F5 lub klikając **uruchamianie skryptu** przycisku w środowisku ISE.</span><span class="sxs-lookup"><span data-stu-id="5456b-133">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span>
> <span data-ttu-id="5456b-134">Do źródła skryptu, kropka, uruchom polecenie `. .\myConfig.ps1` gdzie `myConfig.ps1` to nazwa pliku skryptu, który zawiera konfigurację.</span><span class="sxs-lookup"><span data-stu-id="5456b-134">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="5456b-135">Gdy wywołujesz konfiguracji, go:</span><span class="sxs-lookup"><span data-stu-id="5456b-135">When you call the configuration, it:</span></span>

- <span data-ttu-id="5456b-136">Usuwa wszystkie zmienne</span><span class="sxs-lookup"><span data-stu-id="5456b-136">Resolves all variables</span></span>
- <span data-ttu-id="5456b-137">Tworzy folder w bieżącym katalogu o nazwie identycznej z nazwą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5456b-137">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="5456b-138">Tworzy plik o nazwie _NodeName_MOF w nowy katalog, gdzie _NodeName_ jest nazwa konfiguracji węzła docelowego.</span><span class="sxs-lookup"><span data-stu-id="5456b-138">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span>
  <span data-ttu-id="5456b-139">Jeśli istnieje więcej niż jeden węzeł, zostanie utworzony plik MOF dla każdego węzła.</span><span class="sxs-lookup"><span data-stu-id="5456b-139">If there is more than one node, a MOF file will be created for each node.</span></span>

> [!NOTE]
> <span data-ttu-id="5456b-140">Plik MOF zawiera wszystkie informacje o konfiguracji dla węzła docelowego.</span><span class="sxs-lookup"><span data-stu-id="5456b-140">The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="5456b-141">W związku z tym należy Przechowuj w bezpiecznym miejscu.</span><span class="sxs-lookup"><span data-stu-id="5456b-141">Because of this, it’s important to keep it secure.</span></span>
> <span data-ttu-id="5456b-142">Aby uzyskać więcej informacji, zobacz [Zabezpieczanie pliku MOF](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="5456b-142">For more information, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>

<span data-ttu-id="5456b-143">Kompilowanie to pierwsza Konfiguracja powyżej skutkuje następującą strukturę folderów:</span><span class="sxs-lookup"><span data-stu-id="5456b-143">Compiling the first configuration above results in the following folder structure:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

<span data-ttu-id="5456b-144">Jeśli konfiguracja przyjmuje parametr, jak w drugim przykładzie, który ma zostać dostarczona w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5456b-144">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="5456b-145">Poniżej przedstawiono, jak będzie wyglądać:</span><span class="sxs-lookup"><span data-stu-id="5456b-145">Here's how that would look:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="5456b-146">Za pomocą nowych zasobów w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5456b-146">Using new resources in Your configuration</span></span>

<span data-ttu-id="5456b-147">Po przeprowadzeniu poprzednich przykładach, można zauważyć, że zostały ostrzegani, które były używane zasób bez jawnie jego importowania.</span><span class="sxs-lookup"><span data-stu-id="5456b-147">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="5456b-148">Już dziś DSC jest dostarczany z 12 zasobów jako część modułu PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="5456b-148">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>

<span data-ttu-id="5456b-149">Polecenia cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), może służyć do określenia, jakie zasoby są zainstalowane w systemie i dostępne do użycia przez LCM.</span><span class="sxs-lookup"><span data-stu-id="5456b-149">The cmdlet, [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="5456b-150">Gdy te moduły zostały umieszczone w `$env:PSModulePath` i prawidłowo rozpoznawane przez [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), są nadal muszą być ładowane w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5456b-150">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), they still need to be loaded within your configuration.</span></span>

<span data-ttu-id="5456b-151">**Import-DscResource** jest dynamiczne słowo kluczowe, które mogą być rozpoznawane tylko w ramach **konfiguracji** bloku, nie jest poleceniem cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5456b-151">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block, it is not a cmdlet.</span></span>
<span data-ttu-id="5456b-152">**Import-DscResource** obsługuje dwa parametry:</span><span class="sxs-lookup"><span data-stu-id="5456b-152">**Import-DscResource** supports two parameters:</span></span>

- <span data-ttu-id="5456b-153">**ModuleName** jest to zalecany sposób korzystania z **Import-DscResource**.</span><span class="sxs-lookup"><span data-stu-id="5456b-153">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="5456b-154">Przyjmuje nazwę modułu, która zawiera zasoby do zaimportowania (a także ciąg na tablicę nazwy modułów).</span><span class="sxs-lookup"><span data-stu-id="5456b-154">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="5456b-155">**Nazwa** to nazwa zasobu do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="5456b-155">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="5456b-156">Nie jest to przyjazna nazwa jako "Name" zwróciło [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), ale nazwa klasy używane podczas definiowania schematu zasobów (zwracane jako **ResourceType** przez [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span><span class="sxs-lookup"><span data-stu-id="5456b-156">This is not the friendly name returned as "Name" by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span></span>

<span data-ttu-id="5456b-157">Aby uzyskać więcej informacji na temat korzystania z `Import-DSCResource`, zobacz [Import-DSCResource przy użyciu](import-dscresource.md)</span><span class="sxs-lookup"><span data-stu-id="5456b-157">For more information on using `Import-DSCResource`, see [Using Import-DSCResource](import-dscresource.md)</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="5456b-158">Różnice w wersji 4 i 5 programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="5456b-158">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="5456b-159">Istnieją różnice w których zasoby DSC muszą znajdować się w programie PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="5456b-159">There are differences in where DSC resources need to be stored in PowerShell 4.0.</span></span> <span data-ttu-id="5456b-160">Aby uzyskać więcej informacji, zobacz [lokalizacja zasobu](import-dscresource.md#resource-location).</span><span class="sxs-lookup"><span data-stu-id="5456b-160">For more information, see [Resource location](import-dscresource.md#resource-location).</span></span>

## <a name="see-also"></a><span data-ttu-id="5456b-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5456b-161">See Also</span></span>

- [<span data-ttu-id="5456b-162">Program Windows PowerShell Desired State Configuration — omówienie</span><span class="sxs-lookup"><span data-stu-id="5456b-162">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="5456b-163">Zasoby DSC</span><span class="sxs-lookup"><span data-stu-id="5456b-163">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="5456b-164">Konfigurowanie programu Local Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="5456b-164">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
