---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Za pomocą Import-DSCResource
ms.openlocfilehash: 6bc3c1aa1d34a05e3188666da825322235c0672e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405113"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="9f446-103">Za pomocą Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="9f446-103">Using Import-DSCResource</span></span>

<span data-ttu-id="9f446-104">`Import-DScResource` jest dynamiczne słowo kluczowe, które można używać tylko wewnątrz bloku skryptu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9f446-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="9f446-105">`Import-DSCResource` — Słowo kluczowe, aby zaimportować wszystkie zasoby potrzebne w danej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9f446-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="9f446-106">Zasobów w ramach `$phsome` są importowane automatycznie, ale nadal jest uważany za najlepszym rozwiązaniem, aby jawnie importujesz wszelkie zasoby używane w Twojej [konfiguracji](Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="9f446-106">Resources under `$phsome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="9f446-107">Składnia `Import-DSCResource` znajdują się poniżej.</span><span class="sxs-lookup"><span data-stu-id="9f446-107">The syntax for `Import-DSCResource` is shown below.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>]
```

|<span data-ttu-id="9f446-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="9f446-108">Parameter</span></span>  |<span data-ttu-id="9f446-109">Opis</span><span class="sxs-lookup"><span data-stu-id="9f446-109">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="9f446-110">Nazwy zasobów DSC, należy zaimportować.</span><span class="sxs-lookup"><span data-stu-id="9f446-110">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="9f446-111">Jeśli nazwa modułu jest określony, polecenie wyszukuje te zasoby DSC, w tym module; w przeciwnym razie polecenie przeszukuje zasoby DSC w wszystkich ścieżek zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="9f446-111">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="9f446-112">Symbole wieloznaczne są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="9f446-112">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="9f446-113">Nazwy modułu kontenera lub specyfikacje modułu.</span><span class="sxs-lookup"><span data-stu-id="9f446-113">The container module name(s), or module specification(s).</span></span>  <span data-ttu-id="9f446-114">Jeśli określisz zasoby do zaimportowania z modułu, polecenie podejmie próbę importowanie tylko tych zasobów.</span><span class="sxs-lookup"><span data-stu-id="9f446-114">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="9f446-115">Jeśli określisz tylko moduł, polecenie importuje wszystkie zasoby DSC w module.</span><span class="sxs-lookup"><span data-stu-id="9f446-115">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|

<span data-ttu-id="9f446-116">Można używać symboli wieloznacznych, za pomocą `-Name` parametru w przypadku korzystania z `Import-DSCResource`.</span><span class="sxs-lookup"><span data-stu-id="9f446-116">You can use wildcards with the `-Name` parameter when using `Import-DSCResource`.</span></span>

```powershell
Import-DscResource -Name * -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="9f446-117">Przykład: Użyj Import-DSCResource w ramach konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9f446-117">Example: Use Import-DSCResource within a configuration</span></span>

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName MS_DSC1 -name Service, File, Registry

    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    Import-DSCResource -Name File, TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
...
```

> [!NOTE]
> <span data-ttu-id="9f446-118">Określanie wielu wartości dla nazwy zasobów i moduły w tym samym poleceniu nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="9f446-118">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="9f446-119">Może mieć niedeterministyczne zachowanie dotyczące zasobu, który można załadować z modułu, którego, w przypadku, gdy ten sam zasób istnieje wiele modułów.</span><span class="sxs-lookup"><span data-stu-id="9f446-119">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="9f446-120">Poniższego polecenia spowoduje błąd podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9f446-120">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="9f446-121">Warto wziąć pod uwagę podczas korzystania z parametr Name:</span><span class="sxs-lookup"><span data-stu-id="9f446-121">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="9f446-122">Jest to operacja intensywnie korzystających z zasobów, w zależności od liczby modułów zainstalowanych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="9f446-122">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="9f446-123">Będzie on ładować się pierwszy zasób znaleziono o podanej nazwie.</span><span class="sxs-lookup"><span data-stu-id="9f446-123">It will load the first resource found with the given name.</span></span> <span data-ttu-id="9f446-124">W przypadku, gdy istnieje więcej niż jeden zasób o takiej samej nazwie, zainstalowane, można załadować niewłaściwych zasobów.</span><span class="sxs-lookup"><span data-stu-id="9f446-124">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="9f446-125">Użycie zalecane jest, aby określić `–ModuleName` z `-Name` parametru, zgodnie z poniższym opisem.</span><span class="sxs-lookup"><span data-stu-id="9f446-125">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="9f446-126">Użycie tych ma następujące zalety:</span><span class="sxs-lookup"><span data-stu-id="9f446-126">This usage has the following benefits:</span></span>

- <span data-ttu-id="9f446-127">Zmniejsza to negatywny wpływ na wydajność, ograniczając zakres wyszukiwania dla określonego zasobu.</span><span class="sxs-lookup"><span data-stu-id="9f446-127">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="9f446-128">Jawnie definiuje moduł definiowania zasobu, zapewnienie, że właściwy zasób jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="9f446-128">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="9f446-129">W programie PowerShell 5.0 zasoby DSC może mieć wiele wersji i wersje, które można zainstalować na komputerze side-by-side.</span><span class="sxs-lookup"><span data-stu-id="9f446-129">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="9f446-130">To jest implementowany przez korzystanie z kilku wersji moduł zasobów, które są zawarte w tym samym folderze modułu.</span><span class="sxs-lookup"><span data-stu-id="9f446-130">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="9f446-131">Aby uzyskać więcej informacji, zobacz [korzystanie z zasobów z wieloma wersjami](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="9f446-131">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="9f446-132">Funkcja IntelliSense z Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="9f446-132">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="9f446-133">Podczas tworzenia konfiguracji DSC w środowisku ISE, program PowerShell udostępnia IntelliSence dla zasobów i właściwości zasobów.</span><span class="sxs-lookup"><span data-stu-id="9f446-133">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="9f446-134">Definicje zasobów w ramach `$pshome` ścieżka modułu są ładowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="9f446-134">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="9f446-135">Podczas importowania zasobów przy użyciu `Import-DSCResource` — słowo kluczowe, definicje określonego zasobu zostaną dodane, a funkcja Intellisense jest rozwinięta i obejmuje schemat importowanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="9f446-135">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![Funkcja Intellisense zasobów](/media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="9f446-137">Począwszy od programu PowerShell w wersji 5.0, dodano uzupełnianie po naciśnięciu tabulatora ISE dla zasobów DSC oraz ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="9f446-137">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="9f446-138">Aby uzyskać więcej informacji, zobacz [zasobów](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="9f446-138">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="9f446-139">Podczas kompilowania konfiguracji, programu PowerShell używa definicji zasobów zaimportowanych do sprawdzania poprawności wszystkich bloków zasobów w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9f446-139">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="9f446-140">Każdy blok zasobu jest weryfikowana, za pomocą definicji schematu do zasobu, dla następujących reguł.</span><span class="sxs-lookup"><span data-stu-id="9f446-140">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="9f446-141">Używane są tylko właściwości zdefiniowane w schemacie.</span><span class="sxs-lookup"><span data-stu-id="9f446-141">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="9f446-142">Typy danych dla każdej właściwości są poprawne.</span><span class="sxs-lookup"><span data-stu-id="9f446-142">The data types for each property are correct.</span></span>
- <span data-ttu-id="9f446-143">Określono właściwości kluczy.</span><span class="sxs-lookup"><span data-stu-id="9f446-143">Keys properties are specified.</span></span>
- <span data-ttu-id="9f446-144">Nie właściwości tylko do odczytu jest używany.</span><span class="sxs-lookup"><span data-stu-id="9f446-144">No read-only property is used.</span></span>
- <span data-ttu-id="9f446-145">Sprawdzanie poprawności na podstawie wartości mapowania typów.</span><span class="sxs-lookup"><span data-stu-id="9f446-145">Validation on value maps types.</span></span>

<span data-ttu-id="9f446-146">Rozważmy następującą konfigurację:</span><span class="sxs-lookup"><span data-stu-id="9f446-146">Consider the following configuration:</span></span>

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

<span data-ttu-id="9f446-147">Kompilowanie tej konfiguracji będzie skutkowało błędem.</span><span class="sxs-lookup"><span data-stu-id="9f446-147">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="9f446-148">Funkcja IntelliSense i schematu sprawdzania poprawności pozwalają przechwytywać więcej błędów podczas analizy i kompilacja, unikając kompilacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9f446-148">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="9f446-149">Każdy zasób DSC może mieć nazwę, a **FriendlyName** definiowana przez schemat zasobu.</span><span class="sxs-lookup"><span data-stu-id="9f446-149">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="9f446-150">Poniżej przedstawiono dwa pierwsze wiersze "MSFT_ServiceResource.shema.mof".</span><span class="sxs-lookup"><span data-stu-id="9f446-150">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="9f446-151">Korzystając z tego zasobu w konfiguracji, można określić **MSFT_ServiceResource** lub **usługi**.</span><span class="sxs-lookup"><span data-stu-id="9f446-151">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="9f446-152">Różnice w wersji 4 i 5 programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="9f446-152">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="9f446-153">Istnieje wiele różnice, które zobaczysz podczas tworzenia konfiguracji w programie PowerShell 4.0 vs. Program PowerShell 5.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="9f446-153">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="9f446-154">W tej sekcji zostanie podkreślić różnice zostanie wyświetlony odpowiedni do tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="9f446-154">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="9f446-155">Wiele wersji zasobu</span><span class="sxs-lookup"><span data-stu-id="9f446-155">Multiple Resource Versions</span></span>

<span data-ttu-id="9f446-156">Zainstalowanie i używanie wielu wersji obok siebie zasobów nie jest obsługiwana w programie PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="9f446-156">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="9f446-157">Jeśli zauważysz problemów dotyczących importowania zasobów do konfiguracji, upewnij się, mieć tylko jedną wersję zasobu zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="9f446-157">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="9f446-158">Na ilustracji poniżej dwie wersje **xPSDesiredStateConfiguration** moduł są zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="9f446-158">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Wiele wersji zasobu, stała](/media/multiple-resource-versions-broken.md)

<span data-ttu-id="9f446-160">Skopiuj zawartość tej wersji żądany moduł najwyższego poziomu katalog modułu.</span><span class="sxs-lookup"><span data-stu-id="9f446-160">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Wiele wersji zasobu, stała](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a><span data-ttu-id="9f446-162">Lokalizacja zasobu</span><span class="sxs-lookup"><span data-stu-id="9f446-162">Resource location</span></span>

<span data-ttu-id="9f446-163">Podczas tworzenia i kompilowanie konfiguracji, Twoje zasoby mogą być przechowywane w dowolnym katalogu określonego przez użytkownika [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span><span class="sxs-lookup"><span data-stu-id="9f446-163">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="9f446-164">W programie PowerShell 4.0 LCM wymaga wszystkie moduły zasobów DSC mają być przechowywane w obszarze "Program Files\WindowsPowerShell\Modules" lub `$pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="9f446-164">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="9f446-165">Począwszy od programu PowerShell w wersji 5.0, wymóg ten został usunięty i modułów zasoby mogą być przechowywane w dowolnym katalogu określonego przez `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="9f446-165">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f446-166">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f446-166">See also</span></span>

- [<span data-ttu-id="9f446-167">Zasoby</span><span class="sxs-lookup"><span data-stu-id="9f446-167">Resources</span></span>](../resources/resources.md)
