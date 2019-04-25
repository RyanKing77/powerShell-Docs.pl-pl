---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasoby DSC
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076634"
---
# <a name="dsc-resources"></a><span data-ttu-id="c47cc-103">Zasoby DSC</span><span class="sxs-lookup"><span data-stu-id="c47cc-103">DSC Resources</span></span>

><span data-ttu-id="c47cc-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c47cc-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="c47cc-105">Desired State Configuration, że zasoby (DSC) zawierają bloki konstrukcyjne konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="c47cc-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="c47cc-106">Zasób udostępnia właściwości, które mogą być skonfigurowane (schemat) i zawiera funkcje skrypt programu PowerShell, które lokalne Configuration Manager (LCM) wywołuje być "tak".</span><span class="sxs-lookup"><span data-stu-id="c47cc-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="c47cc-107">Zasób można modelować coś ogólnego jako plik lub jako określone w ustawieniach serwera usług IIS.</span><span class="sxs-lookup"><span data-stu-id="c47cc-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="c47cc-108">Grupy takich jak zasoby są łączone w modułu DSC, która organizuje wszystkie wymagane pliki w do struktury, która jest przenośny i obejmuje metadane, aby zidentyfikować, jak zasoby są przeznaczone do użycia.</span><span class="sxs-lookup"><span data-stu-id="c47cc-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="c47cc-109">Każdy zasób ma \* schemat, który określa składni potrzebnych do korzystania z zasobów w [konfiguracji](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="c47cc-109">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="c47cc-110">Schemat zasobu można zdefiniować w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c47cc-110">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="c47cc-111">**"Schema.Mof"** pliku: Zdefiniuj większość zasobów ich *schematu* w schema.mof plików, przy użyciu [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="c47cc-111">**'Schema.Mof'** file: Most resources define their *schema* in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="c47cc-112">**"\<Nazwa zasobu\>. schema.psm1"** pliku: [Zasoby złożone](../configurations/compositeConfigs.md) definiowanie ich *schematu* w "<ResourceName>. schema.psm1" plik za pomocą [blok parametrów](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span><span class="sxs-lookup"><span data-stu-id="c47cc-112">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="c47cc-113">**"\<Nazwa zasobu\>psm1"** pliku: Klasy oparte na zasoby DSC zdefiniować ich *schematu* w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="c47cc-113">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their *schema* in the class definition.</span></span> <span data-ttu-id="c47cc-114">Elementy składni są wskazywane jako właściwości klasy.</span><span class="sxs-lookup"><span data-stu-id="c47cc-114">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="c47cc-115">Aby uzyskać więcej informacji, zobacz [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span><span class="sxs-lookup"><span data-stu-id="c47cc-115">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="c47cc-116">Aby pobrać składnia dla zasobów DSC, użyj [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) polecenia cmdlet z `-Syntax` parametru.</span><span class="sxs-lookup"><span data-stu-id="c47cc-116">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="c47cc-117">To obciążenie jest podobne do [Get-Command](/powershell/module/microsoft.powershell.core/get-command) z `-Syntax` parametru, aby pobrać Składnia poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c47cc-117">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="c47cc-118">Widoczne dane wyjściowe zostaną wyświetlone z szablonu użytego do bloku zasobu dla zasobu, które określisz.</span><span class="sxs-lookup"><span data-stu-id="c47cc-118">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="c47cc-119">Widoczne dane wyjściowe powinny być podobne do danych wyjściowych poniżej, chociaż Składnia tego zasobu można zmienić w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="c47cc-119">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="c47cc-120">Składnia poleceń cmdlet, takich jak *klucze* widać w nawiasach kwadratowych, są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="c47cc-120">Like cmdlet syntax, the *keys* seen in square brackets, are optional.</span></span> <span data-ttu-id="c47cc-121">Typy określić rodzaj danych, który oczekuje, że każdy klucz.</span><span class="sxs-lookup"><span data-stu-id="c47cc-121">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="c47cc-122">**Upewnij się, że** klucz jest opcjonalny, ponieważ jego wartość domyślna to "Istnieje".</span><span class="sxs-lookup"><span data-stu-id="c47cc-122">The **Ensure** key is optional because it defaults to "Present".</span></span>

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

<span data-ttu-id="c47cc-123">W konfiguracji **usługi** blok zasobu może wyglądać jak ten element, aby **upewnij się, że** uruchomioną usługę buforowania.</span><span class="sxs-lookup"><span data-stu-id="c47cc-123">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="c47cc-124">Przed rozpoczęciem korzystania z zasobów w ramach konfiguracji należy zaimportować go za pomocą [Import-DSCResource](../configurations/import-dscresource.md).</span><span class="sxs-lookup"><span data-stu-id="c47cc-124">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

<span data-ttu-id="c47cc-125">Konfiguracje mogą zawierać wiele wystąpień tego samego typu zasobu.</span><span class="sxs-lookup"><span data-stu-id="c47cc-125">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="c47cc-126">Każde wystąpienie musi mieć jednoznacznie nazwę.</span><span class="sxs-lookup"><span data-stu-id="c47cc-126">Each instance must be uniquely named.</span></span> <span data-ttu-id="c47cc-127">W poniższym przykładzie sekundy **usługi** bloku zasobów jest dodawany do skonfigurowania usługi "DHCP".</span><span class="sxs-lookup"><span data-stu-id="c47cc-127">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="c47cc-128">Począwszy od programu PowerShell w wersji 5.0, dodano intellisense DSC.</span><span class="sxs-lookup"><span data-stu-id="c47cc-128">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="c47cc-129">Ta nowa funkcja umożliwia \<kartę\> i \<Ctrl + spacja\> do automatycznego uzupełniania nazw kluczy.</span><span class="sxs-lookup"><span data-stu-id="c47cc-129">This new feature allows you to use \<TAB\> and \<Ctrl+Space\> to auto-complete key names.</span></span>

![Uzupełnianie kartę zasobów](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a><span data-ttu-id="c47cc-131">Zasoby wbudowane</span><span class="sxs-lookup"><span data-stu-id="c47cc-131">Built-in resources</span></span>

<span data-ttu-id="c47cc-132">Oprócz zasobów społeczności istnieją wbudowane zasoby dla Windows, zasoby dla systemu Linux i zasoby dla zależności między węzłami.</span><span class="sxs-lookup"><span data-stu-id="c47cc-132">In addition to community resources, there are built-in resources for Windows, resources for Linux, and resources for cross-node dependency.</span></span> <span data-ttu-id="c47cc-133">Skorzystaj z powyższych kroków, składni tych zasobów i sposobu ich używania.</span><span class="sxs-lookup"><span data-stu-id="c47cc-133">You can use the steps above to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="c47cc-134">Stron, które pełnią te zasoby zostały zarchiwizowane w obszarze **odwołania**.</span><span class="sxs-lookup"><span data-stu-id="c47cc-134">The pages that serve these resources have been archived under **Reference**.</span></span>

<span data-ttu-id="c47cc-135">Wbudowane zasoby systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c47cc-135">Windows built-in resources</span></span>

* [<span data-ttu-id="c47cc-136">Zasób archiwum</span><span class="sxs-lookup"><span data-stu-id="c47cc-136">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
* [<span data-ttu-id="c47cc-137">Zasób środowiska</span><span class="sxs-lookup"><span data-stu-id="c47cc-137">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
* [<span data-ttu-id="c47cc-138">Zasób pliku</span><span class="sxs-lookup"><span data-stu-id="c47cc-138">File Resource</span></span>](../reference/resources/windows/fileResource.md)
* [<span data-ttu-id="c47cc-139">Zasób grupy</span><span class="sxs-lookup"><span data-stu-id="c47cc-139">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
* [<span data-ttu-id="c47cc-140">Zasób GroupSet</span><span class="sxs-lookup"><span data-stu-id="c47cc-140">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
* [<span data-ttu-id="c47cc-141">Zasób dziennika</span><span class="sxs-lookup"><span data-stu-id="c47cc-141">Log Resource</span></span>](../reference/resources/windows/logResource.md)
* [<span data-ttu-id="c47cc-142">Zasób pakietu</span><span class="sxs-lookup"><span data-stu-id="c47cc-142">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
* [<span data-ttu-id="c47cc-143">Zasób ProcessSet</span><span class="sxs-lookup"><span data-stu-id="c47cc-143">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
* [<span data-ttu-id="c47cc-144">Zasób rejestru</span><span class="sxs-lookup"><span data-stu-id="c47cc-144">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
* [<span data-ttu-id="c47cc-145">Zasób skryptu</span><span class="sxs-lookup"><span data-stu-id="c47cc-145">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
* [<span data-ttu-id="c47cc-146">Zasób usługi</span><span class="sxs-lookup"><span data-stu-id="c47cc-146">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
* [<span data-ttu-id="c47cc-147">Zasób ServiceSet</span><span class="sxs-lookup"><span data-stu-id="c47cc-147">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
* [<span data-ttu-id="c47cc-148">Zasób użytkownika</span><span class="sxs-lookup"><span data-stu-id="c47cc-148">User Resource</span></span>](../reference/resources/windows/userResource.md)
* [<span data-ttu-id="c47cc-149">Zasób WindowsFeature</span><span class="sxs-lookup"><span data-stu-id="c47cc-149">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
* [<span data-ttu-id="c47cc-150">Zasób WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="c47cc-150">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
* [<span data-ttu-id="c47cc-151">Zasób WindowsOptionalFeature</span><span class="sxs-lookup"><span data-stu-id="c47cc-151">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [<span data-ttu-id="c47cc-152">Zasób WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="c47cc-152">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [<span data-ttu-id="c47cc-153">WindowsPackageCabResource Resource</span><span class="sxs-lookup"><span data-stu-id="c47cc-153">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
* [<span data-ttu-id="c47cc-154">Zasób WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="c47cc-154">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

<span data-ttu-id="c47cc-155">[Zależności między węzłami](../configurations/crossNodeDependencies.md) zasobów</span><span class="sxs-lookup"><span data-stu-id="c47cc-155">[Cross-Node dependency](../configurations/crossNodeDependencies.md) resources</span></span>

* [<span data-ttu-id="c47cc-156">WaitForAll zasobów</span><span class="sxs-lookup"><span data-stu-id="c47cc-156">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
* [<span data-ttu-id="c47cc-157">WaitForSome zasobów</span><span class="sxs-lookup"><span data-stu-id="c47cc-157">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
* [<span data-ttu-id="c47cc-158">WaitForAny zasobów</span><span class="sxs-lookup"><span data-stu-id="c47cc-158">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

<span data-ttu-id="c47cc-159">Pakiet zarządzania zasobami</span><span class="sxs-lookup"><span data-stu-id="c47cc-159">Package Management resources</span></span>

* [<span data-ttu-id="c47cc-160">Zasób funkcji PackageManagement</span><span class="sxs-lookup"><span data-stu-id="c47cc-160">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [<span data-ttu-id="c47cc-161">PackageManagementSource Resource</span><span class="sxs-lookup"><span data-stu-id="c47cc-161">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

<span data-ttu-id="c47cc-162">Zasoby systemu Linux</span><span class="sxs-lookup"><span data-stu-id="c47cc-162">Linux resources</span></span>

* [<span data-ttu-id="c47cc-163">Zasób archiwum systemu Linux</span><span class="sxs-lookup"><span data-stu-id="c47cc-163">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
* [<span data-ttu-id="c47cc-164">Zasób środowiska systemu Linux</span><span class="sxs-lookup"><span data-stu-id="c47cc-164">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
* [<span data-ttu-id="c47cc-165">Zasób FileLine systemu Linux</span><span class="sxs-lookup"><span data-stu-id="c47cc-165">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
* [<span data-ttu-id="c47cc-166">Zasób pliku systemu Linux</span><span class="sxs-lookup"><span data-stu-id="c47cc-166">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
* [<span data-ttu-id="c47cc-167">Zasób grupy systemu Linux</span><span class="sxs-lookup"><span data-stu-id="c47cc-167">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
* [<span data-ttu-id="c47cc-168">Zasób pakietu systemu Linux</span><span class="sxs-lookup"><span data-stu-id="c47cc-168">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
* [<span data-ttu-id="c47cc-169">Zasób skryptu systemu Linux</span><span class="sxs-lookup"><span data-stu-id="c47cc-169">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
* [<span data-ttu-id="c47cc-170">Zasób usługi w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="c47cc-170">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
* [<span data-ttu-id="c47cc-171">Zasób SshAuthorizedKeys systemu Linux</span><span class="sxs-lookup"><span data-stu-id="c47cc-171">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [<span data-ttu-id="c47cc-172">Zasób użytkownika w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="c47cc-172">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
