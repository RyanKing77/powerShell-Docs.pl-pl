---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguracja, instalacja
title: Używanie polecenia Import-DSCResource
ms.openlocfilehash: e1c2c06d756a70c2de516f330e3123235ce740ba
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215409"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="f4a5e-103">Używanie polecenia Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="f4a5e-103">Using Import-DSCResource</span></span>

<span data-ttu-id="f4a5e-104">`Import-DScResource`jest dynamicznym słowem kluczowym, którego można używać tylko wewnątrz bloku skryptu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="f4a5e-105">`Import-DSCResource` Słowo kluczowe służące do importowania wszelkich zasobów wymaganych w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="f4a5e-106">Zasoby w `$pshome` obszarze są importowane automatycznie, ale nadal jest uważane za najlepsze rozwiązanie do jawnego importowania wszystkich zasobów używanych w [konfiguracji](Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="f4a5e-106">Resources under `$pshome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="f4a5e-107">Składnia dla `Import-DSCResource` jest pokazana poniżej.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-107">The syntax for `Import-DSCResource` is shown below.</span></span>  <span data-ttu-id="f4a5e-108">W przypadku określania modułów według nazwy jest wymagane, aby wyświetlić każdą z nich w nowym wierszu.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-108">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|<span data-ttu-id="f4a5e-109">Parametr</span><span class="sxs-lookup"><span data-stu-id="f4a5e-109">Parameter</span></span>  |<span data-ttu-id="f4a5e-110">Opis</span><span class="sxs-lookup"><span data-stu-id="f4a5e-110">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="f4a5e-111">Nazwy zasobów DSC, które należy zaimportować.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-111">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="f4a5e-112">Jeśli nazwa modułu jest określona, polecenie wyszukuje te zasoby DSC w ramach tego modułu; w przeciwnym razie polecenie przeszukuje zasoby DSC we wszystkich ścieżkach zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-112">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="f4a5e-113">Symbole wieloznaczne są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-113">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="f4a5e-114">Nazwa modułu lub Specyfikacja modułu.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-114">The module name, or module specification.</span></span>  <span data-ttu-id="f4a5e-115">W przypadku określenia zasobów do zaimportowania z modułu polecenie spowoduje próbę zaimportowania tylko tych zasobów.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-115">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="f4a5e-116">Jeśli określisz tylko moduł, polecenie importuje wszystkie zasoby DSC w module.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-116">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="f4a5e-117">Przykład: Używanie elementu import-DSCResource w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f4a5e-117">Example: Use Import-DSCResource within a configuration</span></span>

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry
    
    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    Import-DSCResource -ModuleName ComputerManagementDsc
...
```

> [!NOTE]
> <span data-ttu-id="f4a5e-118">Określanie wielu wartości nazw zasobów i nazw modułów w tym samym poleceniu nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-118">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="f4a5e-119">Może mieć niedeterministyczne zachowanie dotyczące tego, który zasób jest ładowany, z którego modułu w przypadku tego samego zasobu istnieje w wielu modułach.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-119">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="f4a5e-120">Poniższe polecenie spowoduje błąd podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-120">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="f4a5e-121">Kwestie, które należy wziąć pod uwagę w przypadku używania tylko parametru name:</span><span class="sxs-lookup"><span data-stu-id="f4a5e-121">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="f4a5e-122">Jest to operacja intensywnie korzystająca z zasobów w zależności od liczby modułów zainstalowanych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-122">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="f4a5e-123">Zostanie załadowany pierwszy znaleziony zasób o podaną nazwę.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-123">It will load the first resource found with the given name.</span></span> <span data-ttu-id="f4a5e-124">W przypadku, gdy zainstalowano więcej niż jeden zasób o tej samej nazwie, może załadować niewłaściwy zasób.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-124">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="f4a5e-125">Zalecanym użyciem jest określenie `–ModuleName` `-Name` parametru z parametrem, zgodnie z poniższym opisem.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-125">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="f4a5e-126">To użycie ma następujące zalety:</span><span class="sxs-lookup"><span data-stu-id="f4a5e-126">This usage has the following benefits:</span></span>

- <span data-ttu-id="f4a5e-127">Zmniejsza to wpływ na wydajność, ograniczając zakres wyszukiwania dla określonego zasobu.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-127">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="f4a5e-128">Jawnie definiuje moduł definiujący zasób, upewniając się, że jest ładowany prawidłowy zasób.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-128">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="f4a5e-129">W programie PowerShell 5,0 zasoby DSC mogą mieć wiele wersji, a wersje można instalować na komputerze obok siebie.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-129">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="f4a5e-130">Jest to implementowane przez posiadanie wielu wersji modułu zasobów, które znajdują się w tym samym folderze modułu.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-130">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="f4a5e-131">Aby uzyskać więcej informacji, zobacz [Korzystanie z zasobów z wieloma wersjami](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="f4a5e-131">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="f4a5e-132">Technologia IntelliSense z usługą import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="f4a5e-132">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="f4a5e-133">Podczas tworzenia konfiguracji DSC w programie ISE program PowerShell udostępnia IntelliSence dla zasobów i właściwości zasobów.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-133">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="f4a5e-134">Definicje zasobów w `$pshome` ścieżce modułu są ładowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-134">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="f4a5e-135">Po zaimportowaniu zasobów przy `Import-DSCResource` użyciu słowa kluczowego określone definicje zasobów są dodawane, a funkcja IntelliSense jest rozwinięta, aby uwzględnić schemat zaimportowanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-135">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![Technologia IntelliSense zasobów](../media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="f4a5e-137">Począwszy od programu PowerShell 5,0, uzupełnianie kart zostało dodane do ISE dla zasobów DSC i ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-137">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="f4a5e-138">Aby uzyskać więcej informacji, zobacz [zasoby](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="f4a5e-138">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="f4a5e-139">Podczas kompilowania konfiguracji program PowerShell używa zaimportowanych definicji zasobów do walidacji wszystkich bloków zasobów w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-139">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="f4a5e-140">Każdy blok zasobów jest sprawdzany przy użyciu definicji schematu zasobu dla następujących reguł.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-140">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="f4a5e-141">Używane są tylko właściwości zdefiniowane w schemacie.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-141">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="f4a5e-142">Typy danych dla każdej właściwości są poprawne.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-142">The data types for each property are correct.</span></span>
- <span data-ttu-id="f4a5e-143">Określono właściwości kluczy.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-143">Keys properties are specified.</span></span>
- <span data-ttu-id="f4a5e-144">Nie jest używana właściwość tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-144">No read-only property is used.</span></span>
- <span data-ttu-id="f4a5e-145">Sprawdzanie poprawności typów map wartości.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-145">Validation on value maps types.</span></span>

<span data-ttu-id="f4a5e-146">Weź pod uwagę następującą konfigurację:</span><span class="sxs-lookup"><span data-stu-id="f4a5e-146">Consider the following configuration:</span></span>

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

<span data-ttu-id="f4a5e-147">Skompilowanie tej konfiguracji spowoduje wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-147">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="f4a5e-148">Funkcja IntelliSense i sprawdzanie poprawności schematu umożliwiają przechwytywanie większej liczby błędów podczas analizowania i kompilowania, unikając komplikacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-148">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="f4a5e-149">Każdy zasób DSC może mieć nazwę i **FriendlyName** zdefiniowane przez schemat zasobu.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-149">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="f4a5e-150">Poniżej znajdują się pierwsze dwa wiersze pliku "MSFT_ServiceResource. Shema. MOF".</span><span class="sxs-lookup"><span data-stu-id="f4a5e-150">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="f4a5e-151">W przypadku korzystania z tego zasobu w konfiguracji można określić **MSFT_ServiceResource** lub **usługę**.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-151">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="f4a5e-152">Różnice w programie PowerShell w wersji 4 i 5</span><span class="sxs-lookup"><span data-stu-id="f4a5e-152">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="f4a5e-153">Istnieje wiele różnic, które są widoczne podczas tworzenia konfiguracji w programie PowerShell 4,0 a Program PowerShell 5,0 i nowsze.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-153">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="f4a5e-154">W tej sekcji zostaną wyróżnione różnice, które są odpowiednie dla tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-154">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="f4a5e-155">Wiele wersji zasobów</span><span class="sxs-lookup"><span data-stu-id="f4a5e-155">Multiple Resource Versions</span></span>

<span data-ttu-id="f4a5e-156">Instalowanie i używanie wielu wersji zasobów obok siebie nie jest obsługiwane w programie PowerShell 4,0.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-156">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="f4a5e-157">Jeśli zauważysz problemy z importowaniem zasobów do konfiguracji, upewnij się, że zainstalowano tylko jedną wersję zasobu.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-157">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="f4a5e-158">Na poniższym obrazie zainstalowano dwie wersje modułu **xPSDesiredStateConfiguration** .</span><span class="sxs-lookup"><span data-stu-id="f4a5e-158">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Rozwiązano wiele wersji zasobów](../media/multiple-resource-versions-broken.png)

<span data-ttu-id="f4a5e-160">Skopiuj zawartość żądanej wersji modułu do najwyższego poziomu katalogu modułów.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-160">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Rozwiązano wiele wersji zasobów](../media/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a><span data-ttu-id="f4a5e-162">Lokalizacja zasobu</span><span class="sxs-lookup"><span data-stu-id="f4a5e-162">Resource location</span></span>

<span data-ttu-id="f4a5e-163">Podczas tworzenia i kompilowania konfiguracji zasoby mogą być przechowywane w dowolnym katalogu określonym przez [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span><span class="sxs-lookup"><span data-stu-id="f4a5e-163">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="f4a5e-164">W programie PowerShell 4,0 LCM wymaga, aby wszystkie moduły zasobów DSC były przechowywane w obszarze "program Files\WindowsPowerShell\Modules" `$pshome\Modules`lub.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-164">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="f4a5e-165">Począwszy od programu PowerShell 5,0, to wymaganie zostało usunięte, a moduły zasobów mogą być przechowywane w dowolnym katalogu `PSModulePath`określonym przez.</span><span class="sxs-lookup"><span data-stu-id="f4a5e-165">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4a5e-166">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4a5e-166">See also</span></span>

- [<span data-ttu-id="f4a5e-167">Zasoby</span><span class="sxs-lookup"><span data-stu-id="f4a5e-167">Resources</span></span>](../resources/resources.md)
