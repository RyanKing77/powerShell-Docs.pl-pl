---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Konfiguracji DSC
ms.openlocfilehash: 14db60126fd6c3d11d425a28c749a8e8b81122ca
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="dsc-configurations"></a><span data-ttu-id="6a765-103">Konfiguracji DSC</span><span class="sxs-lookup"><span data-stu-id="6a765-103">DSC Configurations</span></span>

><span data-ttu-id="6a765-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6a765-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="6a765-105">Konfiguracji DSC są skrypty programu PowerShell, które definiują specjalny typ funkcji.</span><span class="sxs-lookup"><span data-stu-id="6a765-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span> <span data-ttu-id="6a765-106">Aby zdefiniować konfigurację, użyj programu PowerShell — słowo kluczowe **konfiguracji**.</span><span class="sxs-lookup"><span data-stu-id="6a765-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

```powershell
Configuration MyDscConfiguration {

    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration

```

<span data-ttu-id="6a765-107">Zapisz skrypt jako plik .ps1.</span><span class="sxs-lookup"><span data-stu-id="6a765-107">Save the script as a .ps1 file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="6a765-108">Składnia konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6a765-108">Configuration syntax</span></span>

<span data-ttu-id="6a765-109">Skrypt konfiguracji składa się z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="6a765-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="6a765-110">**Konfiguracji** bloku.</span><span class="sxs-lookup"><span data-stu-id="6a765-110">The **Configuration** block.</span></span> <span data-ttu-id="6a765-111">To jest blok skryptu najbardziej zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="6a765-111">This is the outermost script block.</span></span> <span data-ttu-id="6a765-112">Należy zdefiniować za pomocą **konfiguracji** — słowo kluczowe i podanie nazwy.</span><span class="sxs-lookup"><span data-stu-id="6a765-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="6a765-113">W takim przypadku nazwa konfiguracji jest "MyDscConfiguration".</span><span class="sxs-lookup"><span data-stu-id="6a765-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="6a765-114">Co najmniej jeden **węzła** bloków.</span><span class="sxs-lookup"><span data-stu-id="6a765-114">One or more **Node** blocks.</span></span> <span data-ttu-id="6a765-115">Zdefiniuj te węzły (komputerach lub maszynach wirtualnych), które są konfigurowane.</span><span class="sxs-lookup"><span data-stu-id="6a765-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="6a765-116">W powyższej konfiguracji istnieje **węzła** bloku przeznaczonego komputerze o nazwie "TEST-PC1".</span><span class="sxs-lookup"><span data-stu-id="6a765-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span>
- <span data-ttu-id="6a765-117">Co najmniej jeden zasób bloków.</span><span class="sxs-lookup"><span data-stu-id="6a765-117">One or more resource blocks.</span></span> <span data-ttu-id="6a765-118">Jest to, gdzie konfiguracji ustawia właściwości zasobów, które jest jej konfigurowanie.</span><span class="sxs-lookup"><span data-stu-id="6a765-118">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="6a765-119">W takim przypadku są dwa bloki zasobów, z których każde wywołanie zasobu "WindowsFeature".</span><span class="sxs-lookup"><span data-stu-id="6a765-119">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="6a765-120">W ramach **konfiguracji** bloku, można wykonywać wszystkie zwykle można w funkcji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6a765-120">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="6a765-121">Na przykład w poprzednim przykładzie, jeśli nie chcesz twardego kodu nazwę komputera docelowego w konfiguracji, możesz można dodać parametr nazwy węzła:</span><span class="sxs-lookup"><span data-stu-id="6a765-121">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$ComputerName="localhost"
    )
    Node $ComputerName {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration -ComputerName $ComputerName

```

<span data-ttu-id="6a765-122">W tym przykładzie, określ nazwę węzła przekazując go jako **ComputerName** parametr podczas kompilowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6a765-122">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="6a765-123">Wartość Nazwa domyślna to "localhost".</span><span class="sxs-lookup"><span data-stu-id="6a765-123">The name defaults to "localhost".</span></span>

## <a name="compiling-the-configuration"></a><span data-ttu-id="6a765-124">Kompilowanie konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6a765-124">Compiling the configuration</span></span>

<span data-ttu-id="6a765-125">Zanim użytkownik wprowadza konfigurację, należy go skompilować do dokumentu MOF.</span><span class="sxs-lookup"><span data-stu-id="6a765-125">Before you can enact a configuration, you have to compile it into a MOF document.</span></span> <span data-ttu-id="6a765-126">W tym celu wywoływania konfiguracji, jak w przypadku funkcji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6a765-126">You do this by calling the configuration like you would a PowerShell function.</span></span>  
<span data-ttu-id="6a765-127">Ostatni wiersz przykład zawierający tylko nazwę konfiguracji, wywołuje konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6a765-127">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

><span data-ttu-id="6a765-128">**Uwaga:** do wywołania konfiguracji, funkcja musi być w zakresie globalnym (podobnie jak w przypadku innych funkcji programu PowerShell).</span><span class="sxs-lookup"><span data-stu-id="6a765-128">**Note:** To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span> 
><span data-ttu-id="6a765-129">Ułatwia to wystąpić albo przez "dot-sourcing" skryptu, lub przez uruchomienie skryptu konfiguracji za pomocą F5 lub klikając **Uruchom skrypt** przycisk w ISE.</span><span class="sxs-lookup"><span data-stu-id="6a765-129">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span> 
><span data-ttu-id="6a765-130">Aby kropka źródła skryptu, uruchom polecenie `. .\myConfig.ps1` gdzie `myConfig.ps1` to nazwa pliku skryptu, który zawiera konfigurację.</span><span class="sxs-lookup"><span data-stu-id="6a765-130">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="6a765-131">Podczas wywoływania konfiguracji, go:</span><span class="sxs-lookup"><span data-stu-id="6a765-131">When you call the configuration, it:</span></span>

- <span data-ttu-id="6a765-132">Usuwa wszystkie zmienne</span><span class="sxs-lookup"><span data-stu-id="6a765-132">Resolves all variables</span></span> 
- <span data-ttu-id="6a765-133">Tworzy folder w bieżącym katalogu o nazwie identycznej z nazwą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6a765-133">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="6a765-134">Tworzy plik o nazwie _NodeName_MOF w nowy katalog, gdy _NodeName_ jest nazwa konfiguracji węzła docelowego.</span><span class="sxs-lookup"><span data-stu-id="6a765-134">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span> 
    <span data-ttu-id="6a765-135">Jeśli istnieje więcej niż jeden węzeł, pliku MOF zostaną utworzone dla każdego węzła.</span><span class="sxs-lookup"><span data-stu-id="6a765-135">If there are more than one nodes, a MOF file will be created for each node.</span></span>

><span data-ttu-id="6a765-136">**Uwaga**: plik MOF zawiera wszystkie informacje o konfiguracji dla węzła docelowego.</span><span class="sxs-lookup"><span data-stu-id="6a765-136">**Note**: The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="6a765-137">W związku z tym ważne jest podlegać ochronie.</span><span class="sxs-lookup"><span data-stu-id="6a765-137">Because of this, it’s important to keep it secure.</span></span> 
><span data-ttu-id="6a765-138">Aby uzyskać więcej informacji, zobacz [Zabezpieczanie pliku MOF](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="6a765-138">For more information, see [Securing the MOF file](secureMOF.md).</span></span>

<span data-ttu-id="6a765-139">Kompilowanie pierwszy konfiguracji powyżej powoduje następującą strukturę folderów:</span><span class="sxs-lookup"><span data-stu-id="6a765-139">Compiling the first configuration above results in the following folder structure:</span></span>

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

<span data-ttu-id="6a765-140">Jeśli konfiguracja przyjmuje parametr, jak pokazano w przykładzie drugiej, który ma zostać podany w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6a765-140">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="6a765-141">Oto, którego wygląd:</span><span class="sxs-lookup"><span data-stu-id="6a765-141">Here's how that would look:</span></span>

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

## <a name="using-dependson"></a><span data-ttu-id="6a765-142">Przy użyciu DependsOn</span><span class="sxs-lookup"><span data-stu-id="6a765-142">Using DependsOn</span></span>

<span data-ttu-id="6a765-143">Jest przydatne słowa kluczowego DSC **DependsOn**.</span><span class="sxs-lookup"><span data-stu-id="6a765-143">A useful DSC keyword is **DependsOn**.</span></span> <span data-ttu-id="6a765-144">Zwykle (chociaż niekoniecznie), DSC stosuje zasobów w kolejności ich występowania w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6a765-144">Typically (though not necessarily always), DSC applies the resources in the order that they appear within the configuration.</span></span> <span data-ttu-id="6a765-145">Jednak **DependsOn** określa zasoby zależne inne zasoby, a LCM gwarantuje, że są stosowane w odpowiedniej kolejności, niezależnie od kolejności w zasobie, które są zdefiniowane wystąpień.</span><span class="sxs-lookup"><span data-stu-id="6a765-145">However, **DependsOn** specifies which resources depend on other resources, and the LCM ensures that they are applied in the correct order, regardless of the order in which resource instances are defined.</span></span> <span data-ttu-id="6a765-146">Na przykład konfiguracji może określić, że wystąpienie **użytkownika** istnienie zależy od zasobu **grupy** wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="6a765-146">For example, a configuration might specify that an instance of the **User** resource depends on the existence of a **Group** instance:</span></span>

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = "Present"
            GroupName = "TestGroup"
        }

        User UserExample {
            Ensure = "Present"
            UserName = "TestUser"
            FullName = "TestUser"
            DependsOn = "[Group]GroupExample"
        }
    }
}

```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="6a765-147">Przy użyciu nowych zasobów w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6a765-147">Using new resources in Your configuration</span></span>

<span data-ttu-id="6a765-148">W przypadku uruchomienia poprzednich przykładach, można zauważyć, że zostały ostrzeżenie, że zostały przy użyciu zasobu nie jest jawnie importowany.</span><span class="sxs-lookup"><span data-stu-id="6a765-148">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="6a765-149">Obecnie DSC jest dostarczany z 12 zasobów w ramach modułu PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="6a765-149">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span> <span data-ttu-id="6a765-150">Inne zasoby w modułach zewnętrznych muszą znajdować się w `$env:PSModulePath` uznawane za LCM.</span><span class="sxs-lookup"><span data-stu-id="6a765-150">Other resources in external modules must be placed in `$env:PSModulePath` in order to be recognized by the LCM.</span></span> <span data-ttu-id="6a765-151">Nowe polecenie cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), może służyć do określenia, jakie zasoby są zainstalowane w systemie i dostępne do użycia przez LCM.</span><span class="sxs-lookup"><span data-stu-id="6a765-151">A new cmdlet, [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span> <span data-ttu-id="6a765-152">Gdy te moduły zostały umieszczone w `$env:PSModulePath` i są prawidłowo rozpoznawane przez [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), nadal muszą być ładowane w ramach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6a765-152">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), they still need to be loaded within your configuration.</span></span> 
<span data-ttu-id="6a765-153">**Import-DscResource** jest dynamiczne słowo kluczowe rozpoznawany tylko w ramach **konfiguracji** bloku (tj. go nie jest poleceniem cmdlet).</span><span class="sxs-lookup"><span data-stu-id="6a765-153">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block (i.e. it is not a cmdlet).</span></span> 
<span data-ttu-id="6a765-154">**Import-DscResource** obsługuje dwa parametry:</span><span class="sxs-lookup"><span data-stu-id="6a765-154">**Import-DscResource** supports two parameters:</span></span>
- <span data-ttu-id="6a765-155">**Nazwa modułu** jest zalecanym sposobem przy użyciu **DscResource importu**.</span><span class="sxs-lookup"><span data-stu-id="6a765-155">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="6a765-156">Przyjmuje nazwę modułu, który zawiera zasoby do zaimportowania (a także tablicy ciągów nazw modułu).</span><span class="sxs-lookup"><span data-stu-id="6a765-156">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span> 
- <span data-ttu-id="6a765-157">**Nazwa** jest nazwa zasobu do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="6a765-157">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="6a765-158">Nie jest to przyjazna nazwa zwracane w postaci "Name" przez [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), ale nazwa klasy używane podczas definiowania schematu zasobów (zwracane jako **ResourceType** przez [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)).</span><span class="sxs-lookup"><span data-stu-id="6a765-158">This is not the friendly name returned as "Name" by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)).</span></span> 

## <a name="see-also"></a><span data-ttu-id="6a765-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6a765-159">See Also</span></span>
* [<span data-ttu-id="6a765-160">Omówienie stanu konfiguracji żądanego programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6a765-160">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
* [<span data-ttu-id="6a765-161">Zasoby usługi Konfiguracja DSC</span><span class="sxs-lookup"><span data-stu-id="6a765-161">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="6a765-162">Konfigurowanie lokalny program Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="6a765-162">Configuring The Local Configuration Manager</span></span>](metaConfig.md)

