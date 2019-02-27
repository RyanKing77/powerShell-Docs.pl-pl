---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Używanie polecenia Import-DSCResource
ms.openlocfilehash: ee0b2f0469c6507c8f0148138198597a9e57cdd7
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2019
ms.locfileid: "56803416"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="6a7ac-103">Używanie polecenia Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="6a7ac-103">Using Import-DSCResource</span></span>

<span data-ttu-id="6a7ac-104">`Import-DScResource` jest dynamiczne słowo kluczowe, które można używać tylko wewnątrz bloku skryptu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="6a7ac-105">`Import-DSCResource` — Słowo kluczowe, aby zaimportować wszystkie zasoby potrzebne w danej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="6a7ac-106">Zasobów w ramach `$pshome` są importowane automatycznie, ale nadal jest uważany za najlepszym rozwiązaniem, aby jawnie importujesz wszelkie zasoby używane w Twojej [konfiguracji](Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="6a7ac-106">Resources under `$pshome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="6a7ac-107">Składnia `Import-DSCResource` znajdują się poniżej.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-107">The syntax for `Import-DSCResource` is shown below.</span></span>  <span data-ttu-id="6a7ac-108">Podczas określania moduły według nazwy, jest wymaganie, aby wyświetlić listę każdy w nowym wierszu.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-108">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|<span data-ttu-id="6a7ac-109">Parametr</span><span class="sxs-lookup"><span data-stu-id="6a7ac-109">Parameter</span></span>  |<span data-ttu-id="6a7ac-110">Opis</span><span class="sxs-lookup"><span data-stu-id="6a7ac-110">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="6a7ac-111">Nazwy zasobów DSC, należy zaimportować.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-111">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="6a7ac-112">Jeśli nazwa modułu jest określony, polecenie wyszukuje te zasoby DSC, w tym module; w przeciwnym razie polecenie przeszukuje zasoby DSC w wszystkich ścieżek zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-112">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="6a7ac-113">Symbole wieloznaczne są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-113">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="6a7ac-114">Nazwa modułu lub specyfikacji modułu.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-114">The module name, or module specification.</span></span>  <span data-ttu-id="6a7ac-115">Jeśli określisz zasoby do zaimportowania z modułu, polecenie podejmie próbę importowanie tylko tych zasobów.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-115">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="6a7ac-116">Jeśli określisz tylko moduł, polecenie importuje wszystkie zasoby DSC w module.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-116">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="6a7ac-117">Przykład: Użyj Import-DSCResource w ramach konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6a7ac-117">Example: Use Import-DSCResource within a configuration</span></span>

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
> <span data-ttu-id="6a7ac-118">Określanie wielu wartości dla nazwy zasobów i moduły w tym samym poleceniu nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-118">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="6a7ac-119">Może mieć niedeterministyczne zachowanie dotyczące zasobu, który można załadować z modułu, którego, w przypadku, gdy ten sam zasób istnieje wiele modułów.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-119">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="6a7ac-120">Poniższego polecenia spowoduje błąd podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-120">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="6a7ac-121">Warto wziąć pod uwagę podczas korzystania z parametr Name:</span><span class="sxs-lookup"><span data-stu-id="6a7ac-121">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="6a7ac-122">Jest to operacja intensywnie korzystających z zasobów, w zależności od liczby modułów zainstalowanych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-122">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="6a7ac-123">Będzie on ładować się pierwszy zasób znaleziono o podanej nazwie.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-123">It will load the first resource found with the given name.</span></span> <span data-ttu-id="6a7ac-124">W przypadku, gdy istnieje więcej niż jeden zasób o takiej samej nazwie, zainstalowane, można załadować niewłaściwych zasobów.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-124">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="6a7ac-125">Użycie zalecane jest, aby określić `–ModuleName` z `-Name` parametru, zgodnie z poniższym opisem.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-125">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="6a7ac-126">Użycie tych ma następujące zalety:</span><span class="sxs-lookup"><span data-stu-id="6a7ac-126">This usage has the following benefits:</span></span>

- <span data-ttu-id="6a7ac-127">Zmniejsza to negatywny wpływ na wydajność, ograniczając zakres wyszukiwania dla określonego zasobu.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-127">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="6a7ac-128">Jawnie definiuje moduł definiowania zasobu, zapewnienie, że właściwy zasób jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-128">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="6a7ac-129">W programie PowerShell 5.0 zasoby DSC może mieć wiele wersji i wersje, które można zainstalować na komputerze side-by-side.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-129">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="6a7ac-130">To jest implementowany przez korzystanie z kilku wersji moduł zasobów, które są zawarte w tym samym folderze modułu.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-130">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="6a7ac-131">Aby uzyskać więcej informacji, zobacz [korzystanie z zasobów z wieloma wersjami](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="6a7ac-131">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="6a7ac-132">Funkcja IntelliSense z Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="6a7ac-132">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="6a7ac-133">Podczas tworzenia konfiguracji DSC w środowisku ISE, program PowerShell udostępnia IntelliSence dla zasobów i właściwości zasobów.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-133">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="6a7ac-134">Definicje zasobów w ramach `$pshome` ścieżka modułu są ładowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-134">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="6a7ac-135">Podczas importowania zasobów przy użyciu `Import-DSCResource` — słowo kluczowe, definicje określonego zasobu zostaną dodane, a funkcja Intellisense jest rozwinięta i obejmuje schemat importowanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-135">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![Funkcja Intellisense zasobów](/media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="6a7ac-137">Począwszy od programu PowerShell w wersji 5.0, dodano uzupełnianie po naciśnięciu tabulatora ISE dla zasobów DSC oraz ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-137">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="6a7ac-138">Aby uzyskać więcej informacji, zobacz [zasobów](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="6a7ac-138">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="6a7ac-139">Podczas kompilowania konfiguracji, programu PowerShell używa definicji zasobów zaimportowanych do sprawdzania poprawności wszystkich bloków zasobów w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-139">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="6a7ac-140">Każdy blok zasobu jest weryfikowana, za pomocą definicji schematu do zasobu, dla następujących reguł.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-140">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="6a7ac-141">Używane są tylko właściwości zdefiniowane w schemacie.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-141">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="6a7ac-142">Typy danych dla każdej właściwości są poprawne.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-142">The data types for each property are correct.</span></span>
- <span data-ttu-id="6a7ac-143">Określono właściwości kluczy.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-143">Keys properties are specified.</span></span>
- <span data-ttu-id="6a7ac-144">Nie właściwości tylko do odczytu jest używany.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-144">No read-only property is used.</span></span>
- <span data-ttu-id="6a7ac-145">Sprawdzanie poprawności na podstawie wartości mapowania typów.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-145">Validation on value maps types.</span></span>

<span data-ttu-id="6a7ac-146">Rozważmy następującą konfigurację:</span><span class="sxs-lookup"><span data-stu-id="6a7ac-146">Consider the following configuration:</span></span>

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

<span data-ttu-id="6a7ac-147">Kompilowanie tej konfiguracji będzie skutkowało błędem.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-147">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="6a7ac-148">Funkcja IntelliSense i schematu sprawdzania poprawności pozwalają przechwytywać więcej błędów podczas analizy i kompilacja, unikając kompilacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-148">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="6a7ac-149">Każdy zasób DSC może mieć nazwę, a **FriendlyName** definiowana przez schemat zasobu.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-149">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="6a7ac-150">Poniżej przedstawiono dwa pierwsze wiersze "MSFT_ServiceResource.shema.mof".</span><span class="sxs-lookup"><span data-stu-id="6a7ac-150">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="6a7ac-151">Korzystając z tego zasobu w konfiguracji, można określić **MSFT_ServiceResource** lub **usługi**.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-151">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="6a7ac-152">Różnice w wersji 4 i 5 programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="6a7ac-152">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="6a7ac-153">Istnieje wiele różnice, które zobaczysz podczas tworzenia konfiguracji w programie PowerShell 4.0 vs. Program PowerShell 5.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-153">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="6a7ac-154">W tej sekcji zostanie podkreślić różnice zostanie wyświetlony odpowiedni do tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-154">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="6a7ac-155">Wiele wersji zasobu</span><span class="sxs-lookup"><span data-stu-id="6a7ac-155">Multiple Resource Versions</span></span>

<span data-ttu-id="6a7ac-156">Zainstalowanie i używanie wielu wersji obok siebie zasobów nie jest obsługiwana w programie PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-156">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="6a7ac-157">Jeśli zauważysz problemów dotyczących importowania zasobów do konfiguracji, upewnij się, mieć tylko jedną wersję zasobu zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-157">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="6a7ac-158">Na ilustracji poniżej dwie wersje **xPSDesiredStateConfiguration** moduł są zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-158">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Wiele wersji zasobu, stała](/media/multiple-resource-versions-broken.md)

<span data-ttu-id="6a7ac-160">Skopiuj zawartość tej wersji żądany moduł najwyższego poziomu katalog modułu.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-160">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Wiele wersji zasobu, stała](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a><span data-ttu-id="6a7ac-162">Lokalizacja zasobu</span><span class="sxs-lookup"><span data-stu-id="6a7ac-162">Resource location</span></span>

<span data-ttu-id="6a7ac-163">Podczas tworzenia i kompilowanie konfiguracji, Twoje zasoby mogą być przechowywane w dowolnym katalogu określonego przez użytkownika [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span><span class="sxs-lookup"><span data-stu-id="6a7ac-163">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="6a7ac-164">W programie PowerShell 4.0 LCM wymaga wszystkie moduły zasobów DSC mają być przechowywane w obszarze "Program Files\WindowsPowerShell\Modules" lub `$pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-164">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="6a7ac-165">Począwszy od programu PowerShell w wersji 5.0, wymóg ten został usunięty i modułów zasoby mogą być przechowywane w dowolnym katalogu określonego przez `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="6a7ac-165">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a7ac-166">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6a7ac-166">See also</span></span>

- [<span data-ttu-id="6a7ac-167">Zasoby</span><span class="sxs-lookup"><span data-stu-id="6a7ac-167">Resources</span></span>](../resources/resources.md)
