---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Konfiguracje DSC
ms.openlocfilehash: 171068acb51f44e31c81e63f6640222ef71bee38
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093698"
---
# <a name="dsc-configurations"></a><span data-ttu-id="9fe8f-103">Konfiguracje DSC</span><span class="sxs-lookup"><span data-stu-id="9fe8f-103">DSC Configurations</span></span>

> <span data-ttu-id="9fe8f-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9fe8f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="9fe8f-105">Konfiguracje DSC są skrypty programu PowerShell, definiujące specjalny rodzaj funkcji.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span>
<span data-ttu-id="9fe8f-106">Aby zdefiniować konfigurację, należy użyć programu PowerShell — słowo kluczowe **konfiguracji**.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

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

<span data-ttu-id="9fe8f-107">Zapisz skrypt jako plik .ps1.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-107">Save the script as a .ps1 file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="9fe8f-108">Składnia konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9fe8f-108">Configuration syntax</span></span>

<span data-ttu-id="9fe8f-109">Skrypt konfiguracji składa się z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="9fe8f-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="9fe8f-110">**Konfiguracji** bloku.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-110">The **Configuration** block.</span></span> <span data-ttu-id="9fe8f-111">Jest to blok skryptu najbardziej zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-111">This is the outermost script block.</span></span> <span data-ttu-id="9fe8f-112">Można zdefiniować przy użyciu **konfiguracji** — słowo kluczowe i podając nazwę.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="9fe8f-113">W takim przypadku nazwa konfiguracji jest "MyDscConfiguration".</span><span class="sxs-lookup"><span data-stu-id="9fe8f-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="9fe8f-114">Co najmniej jeden **węzła** bloków.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-114">One or more **Node** blocks.</span></span> <span data-ttu-id="9fe8f-115">Te definiują węzłów (maszyn wirtualnych lub komputerach), które konfigurujesz.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="9fe8f-116">W powyższej konfiguracji, ma jedną **węzła** bloku, który jest przeznaczony dla komputera o nazwie "TEST-PC1".</span><span class="sxs-lookup"><span data-stu-id="9fe8f-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span>
- <span data-ttu-id="9fe8f-117">Jeden lub więcej bloków zasobów.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-117">One or more resource blocks.</span></span> <span data-ttu-id="9fe8f-118">Jest to, gdzie konfiguracja ustawia właściwości zasobów, które go służy do konfigurowania.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-118">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="9fe8f-119">W tym przypadku istnieją dwa bloki zasobów, z których każde wywołanie zasobu "WindowsFeature".</span><span class="sxs-lookup"><span data-stu-id="9fe8f-119">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="9fe8f-120">W ramach **konfiguracji** bloku, można zrobić wszystko, co zwykle można w funkcji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-120">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="9fe8f-121">Na przykład w poprzednim przykładzie, jeśli nie chcesz ciężko code nazwę komputera docelowego w konfiguracji, można dodać parametr dla nazwy węzła:</span><span class="sxs-lookup"><span data-stu-id="9fe8f-121">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

```powershell
Configuration MyDscConfiguration {
    param(
        [string[]]$ComputerName='localhost'
    )
    Node $ComputerName {
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
MyDscConfiguration -ComputerName $ComputerName
```

<span data-ttu-id="9fe8f-122">W tym przykładzie Określ nazwę węzła przez przekazanie jej jako **ComputerName** parametru podczas kompilowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-122">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="9fe8f-123">Nazwa, wartość domyślna to "localhost".</span><span class="sxs-lookup"><span data-stu-id="9fe8f-123">The name defaults to "localhost".</span></span>

## <a name="compiling-the-configuration"></a><span data-ttu-id="9fe8f-124">Kompilowanie konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9fe8f-124">Compiling the configuration</span></span>

<span data-ttu-id="9fe8f-125">Przed może przyjąć konfiguracji, należy skompilować go na dokument MOF.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-125">Before you can enact a configuration, you have to compile it into a MOF document.</span></span>
<span data-ttu-id="9fe8f-126">Możesz to zrobić, wywołując konfiguracji, takie jak wywoływałby funkcję programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-126">You do this by calling the configuration like you would call a PowerShell function.</span></span>
<span data-ttu-id="9fe8f-127">Ostatni wiersz przykład zawierający tylko nazwę konfiguracji, wywołuje konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-127">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="9fe8f-128">Aby wywołać konfigurację, funkcja musi być w zakresie globalnym (podobnie jak w przypadku innych funkcji programu PowerShell).</span><span class="sxs-lookup"><span data-stu-id="9fe8f-128">To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span>
> <span data-ttu-id="9fe8f-129">Ułatwia to możliwe albo przez "Funkcja dot-sourcing" skryptu, lub przez uruchomienie skryptu konfiguracji przy użyciu klawisza F5 lub klikając **uruchamianie skryptu** przycisku w środowisku ISE.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-129">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span>
> <span data-ttu-id="9fe8f-130">Do źródła skryptu, kropka, uruchom polecenie `. .\myConfig.ps1` gdzie `myConfig.ps1` to nazwa pliku skryptu, który zawiera konfigurację.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-130">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="9fe8f-131">Gdy wywołujesz konfiguracji, go:</span><span class="sxs-lookup"><span data-stu-id="9fe8f-131">When you call the configuration, it:</span></span>

- <span data-ttu-id="9fe8f-132">Usuwa wszystkie zmienne</span><span class="sxs-lookup"><span data-stu-id="9fe8f-132">Resolves all variables</span></span>
- <span data-ttu-id="9fe8f-133">Tworzy folder w bieżącym katalogu o nazwie identycznej z nazwą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-133">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="9fe8f-134">Tworzy plik o nazwie _NodeName_MOF w nowy katalog, gdzie _NodeName_ jest nazwa konfiguracji węzła docelowego.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-134">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span>
  <span data-ttu-id="9fe8f-135">W przypadku węzłów więcej niż jeden plik MOF będzie można utworzyć dla każdego węzła.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-135">If there are more than one nodes, a MOF file will be created for each node.</span></span>

> [!NOTE]
> <span data-ttu-id="9fe8f-136">Plik MOF zawiera wszystkie informacje o konfiguracji dla węzła docelowego.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-136">The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="9fe8f-137">W związku z tym należy Przechowuj w bezpiecznym miejscu.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-137">Because of this, it’s important to keep it secure.</span></span>
> <span data-ttu-id="9fe8f-138">Aby uzyskać więcej informacji, zobacz [Zabezpieczanie pliku MOF](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="9fe8f-138">For more information, see [Securing the MOF file](secureMOF.md).</span></span>

<span data-ttu-id="9fe8f-139">Kompilowanie to pierwsza Konfiguracja powyżej skutkuje następującą strukturę folderów:</span><span class="sxs-lookup"><span data-stu-id="9fe8f-139">Compiling the first configuration above results in the following folder structure:</span></span>

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

<span data-ttu-id="9fe8f-140">Jeśli konfiguracja przyjmuje parametr, jak w drugim przykładzie, który ma zostać dostarczona w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-140">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="9fe8f-141">Poniżej przedstawiono, jak będzie wyglądać:</span><span class="sxs-lookup"><span data-stu-id="9fe8f-141">Here's how that would look:</span></span>

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

## <a name="using-dependson"></a><span data-ttu-id="9fe8f-142">Za pomocą DependsOn</span><span class="sxs-lookup"><span data-stu-id="9fe8f-142">Using DependsOn</span></span>

<span data-ttu-id="9fe8f-143">Jest przydatne — słowo kluczowe DSC **DependsOn**.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-143">A useful DSC keyword is **DependsOn**.</span></span> <span data-ttu-id="9fe8f-144">Zazwyczaj (chociaż niekoniecznie), DSC, ma zastosowanie zasobów w kolejności, w jakiej występują w ramach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-144">Typically (though not necessarily always), DSC applies the resources in the order that they appear within the configuration.</span></span>
<span data-ttu-id="9fe8f-145">Jednak **DependsOn** Określa, która zasoby zależne inne zasoby, a LCM gwarantuje, że są stosowane w odpowiedniej kolejności, niezależnie od kolejności, w zasobach, które są zdefiniowane wystąpień.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-145">However, **DependsOn** specifies which resources depend on other resources, and the LCM ensures that they are applied in the correct order, regardless of the order in which resource instances are defined.</span></span>
<span data-ttu-id="9fe8f-146">Na przykład konfiguracji może określić, że wystąpienie **użytkownika** zasobów zależy od istnienia **grupy** wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="9fe8f-146">For example, a configuration might specify that an instance of the **User** resource depends on the existence of a **Group** instance:</span></span>

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = 'Present'
            GroupName = 'TestGroup'
        }

        User UserExample {
            Ensure = 'Present'
            UserName = 'TestUser'
            FullName = 'TestUser'
            DependsOn = '[Group]GroupExample'
        }
    }
}
```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="9fe8f-147">Za pomocą nowych zasobów w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9fe8f-147">Using new resources in Your configuration</span></span>

<span data-ttu-id="9fe8f-148">Po przeprowadzeniu poprzednich przykładach, można zauważyć, że zostały ostrzegani, które były używane zasób bez jawnie jego importowania.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-148">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="9fe8f-149">Już dziś DSC jest dostarczany z 12 zasobów jako część modułu PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-149">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>
<span data-ttu-id="9fe8f-150">Inne zasoby zewnętrznych modułów muszą być umieszczone w `$env:PSModulePath` uznawane przez LCM.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-150">Other resources in external modules must be placed in `$env:PSModulePath` in order to be recognized by the LCM.</span></span>
<span data-ttu-id="9fe8f-151">Nowe polecenie cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), może służyć do określenia, jakie zasoby są zainstalowane w systemie i dostępne do użycia przez LCM.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-151">A new cmdlet, [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="9fe8f-152">Gdy te moduły zostały umieszczone w `$env:PSModulePath` i prawidłowo rozpoznawane przez [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), są nadal muszą być ładowane w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-152">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), they still need to be loaded within your configuration.</span></span>
<span data-ttu-id="9fe8f-153">**Import-DscResource** jest dynamiczne słowo kluczowe, które mogą być rozpoznawane tylko w ramach **konfiguracji** bloku (czyli nie jest poleceniem cmdlet).</span><span class="sxs-lookup"><span data-stu-id="9fe8f-153">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block (i.e. it is not a cmdlet).</span></span>
<span data-ttu-id="9fe8f-154">**Import-DscResource** obsługuje dwa parametry:</span><span class="sxs-lookup"><span data-stu-id="9fe8f-154">**Import-DscResource** supports two parameters:</span></span>

- <span data-ttu-id="9fe8f-155">**ModuleName** jest to zalecany sposób korzystania z **Import-DscResource**.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-155">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="9fe8f-156">Przyjmuje nazwę modułu, która zawiera zasoby do zaimportowania (a także ciąg na tablicę nazwy modułów).</span><span class="sxs-lookup"><span data-stu-id="9fe8f-156">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="9fe8f-157">**Nazwa** to nazwa zasobu do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="9fe8f-157">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="9fe8f-158">Nie jest to przyjazna nazwa jako "Name" zwróciło [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), ale nazwa klasy używane podczas definiowania schematu zasobów (zwracane jako **ResourceType** przez [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)).</span><span class="sxs-lookup"><span data-stu-id="9fe8f-158">This is not the friendly name returned as "Name" by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)).</span></span>

## <a name="see-also"></a><span data-ttu-id="9fe8f-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9fe8f-159">See Also</span></span>

- [<span data-ttu-id="9fe8f-160">Program Windows PowerShell Desired State Configuration — omówienie</span><span class="sxs-lookup"><span data-stu-id="9fe8f-160">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="9fe8f-161">Zasoby DSC</span><span class="sxs-lookup"><span data-stu-id="9fe8f-161">DSC Resources</span></span>](resources.md)
- [<span data-ttu-id="9fe8f-162">Konfigurowanie programu Local Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="9fe8f-162">Configuring The Local Configuration Manager</span></span>](metaConfig.md)