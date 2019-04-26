---
ms.date: 12/12/2018
keywords: DSC, powershell, zasób, galerii, Instalator
title: Zainstaluj DSC dodatkowe zasoby
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080086"
---
# <a name="install-additional-dsc-resources"></a><span data-ttu-id="cca9c-103">Zainstaluj DSC dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="cca9c-103">Install Additional DSC Resources</span></span>

<span data-ttu-id="cca9c-104">Program PowerShell zawiera kilka zasobów poza pole dla Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="cca9c-104">PowerShell includes several Out-of-the-box resources for Desired State Configuration (DSC).</span></span> <span data-ttu-id="cca9c-105">**PSDesiredStateConfiguration** moduł zawiera wszystkie zasoby DSC OOB dostępne w ramach określonego wystąpienia programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cca9c-105">The **PSDesiredStateConfiguration** module contains all of the OOB DSC resources available on your specific instance of PowerShell.</span></span>

<span data-ttu-id="cca9c-106">Jest to lista zasobów OOB zawartych w programie PowerShell 4.0 i opis możliwości w zakresie zasobów.</span><span class="sxs-lookup"><span data-stu-id="cca9c-106">This is a list of the OOB resources included in PowerShell 4.0 and a description of the resource's capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="cca9c-107">To jest niekompletny, jak wiele zasobów OOB, która wzrosła z każdą wersją programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cca9c-107">This is an incomplete list, as the number of OOB resources has grown with each version of PowerShell.</span></span>

|<span data-ttu-id="cca9c-108">Zasób</span><span class="sxs-lookup"><span data-stu-id="cca9c-108">Resource</span></span>  |<span data-ttu-id="cca9c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="cca9c-109">Description</span></span>  |
|---------|---------|
|<span data-ttu-id="cca9c-110">**Plik**</span><span class="sxs-lookup"><span data-stu-id="cca9c-110">**File**</span></span>|<span data-ttu-id="cca9c-111">Steruje stanem plików i katalogów.</span><span class="sxs-lookup"><span data-stu-id="cca9c-111">Controls the state of files and directories.</span></span> <span data-ttu-id="cca9c-112">Kopiuje pliki z **źródła** do **docelowy** i aktualizuje je, gdy **źródła** zmiany wprowadzane przez porównywanie dat, sumy kontrolne i skróty.</span><span class="sxs-lookup"><span data-stu-id="cca9c-112">Copies files from a **Source** to a **Destination** and updates them when the **Source** changes by comparing dates, checksums, and hashes.</span></span>|
|<span data-ttu-id="cca9c-113">**Archiwizowanie**</span><span class="sxs-lookup"><span data-stu-id="cca9c-113">**Archive**</span></span>|<span data-ttu-id="cca9c-114">Wypakowuje archiwa i określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="cca9c-114">Unpacks archives and a specified location.</span></span> <span data-ttu-id="cca9c-115">Waliduje archiwach z określonym **sumy kontrolnej**.</span><span class="sxs-lookup"><span data-stu-id="cca9c-115">Validates the archives with a specified **Checksum**.</span></span>|
|<span data-ttu-id="cca9c-116">**Środowisko**</span><span class="sxs-lookup"><span data-stu-id="cca9c-116">**Environment**</span></span>|<span data-ttu-id="cca9c-117">Zarządza zmiennych środowiskowych.</span><span class="sxs-lookup"><span data-stu-id="cca9c-117">Manages environment variables.</span></span>|
|<span data-ttu-id="cca9c-118">**Grupa**</span><span class="sxs-lookup"><span data-stu-id="cca9c-118">**Group**</span></span>|<span data-ttu-id="cca9c-119">Zarządza grupami lokalnymi i kontroluje członkostwo w grupie.</span><span class="sxs-lookup"><span data-stu-id="cca9c-119">Manages local groups and controls group membership.</span></span>|
|<span data-ttu-id="cca9c-120">**Dziennik**</span><span class="sxs-lookup"><span data-stu-id="cca9c-120">**Log**</span></span>|<span data-ttu-id="cca9c-121">Zapisuje komunikaty `Microsoft-Windows-Desired State Configuration/Analytic` dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="cca9c-121">Writes messages to the `Microsoft-Windows-Desired State Configuration/Analytic` event log.</span></span>|
|<span data-ttu-id="cca9c-122">**Pakiet**</span><span class="sxs-lookup"><span data-stu-id="cca9c-122">**Package**</span></span>|<span data-ttu-id="cca9c-123">Instaluje lub odinstalowuje pakietów przy użyciu **argumenty**, **LogPath**, **ReturnCode**, inne ustawienia.</span><span class="sxs-lookup"><span data-stu-id="cca9c-123">Installs or uninstalls packages using **Arguments**, **LogPath**, **ReturnCode**, other settings.</span></span>|
|<span data-ttu-id="cca9c-124">**Registry**</span><span class="sxs-lookup"><span data-stu-id="cca9c-124">**Registry**</span></span>|<span data-ttu-id="cca9c-125">Umożliwia zarządzanie kluczami i wartościami rejestru.</span><span class="sxs-lookup"><span data-stu-id="cca9c-125">Manages registry keys and values.</span></span>|
|<span data-ttu-id="cca9c-126">**Skrypt**</span><span class="sxs-lookup"><span data-stu-id="cca9c-126">**Script**</span></span>|<span data-ttu-id="cca9c-127">Pozwala Ci projektować własne [get-test-set](../resources/get-test-set.md) bloki skryptów.</span><span class="sxs-lookup"><span data-stu-id="cca9c-127">Allows you to design your own [get-test-set](../resources/get-test-set.md) script blocks.</span></span>|
|<span data-ttu-id="cca9c-128">**Usługa**</span><span class="sxs-lookup"><span data-stu-id="cca9c-128">**Service**</span></span>|<span data-ttu-id="cca9c-129">Konfiguruje usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="cca9c-129">Configures Windows services.</span></span>|
|<span data-ttu-id="cca9c-130">**Użytkownik**</span><span class="sxs-lookup"><span data-stu-id="cca9c-130">**User**</span></span> |<span data-ttu-id="cca9c-131">Zarządza lokalnych użytkowników i atrybuty.</span><span class="sxs-lookup"><span data-stu-id="cca9c-131">Manages local users and attributes.</span></span>|
|<span data-ttu-id="cca9c-132">**WindowsFeature**</span><span class="sxs-lookup"><span data-stu-id="cca9c-132">**WindowsFeature**</span></span>|<span data-ttu-id="cca9c-133">Zarządza rolami i funkcjami.</span><span class="sxs-lookup"><span data-stu-id="cca9c-133">Manages roles and features.</span></span>|
|<span data-ttu-id="cca9c-134">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="cca9c-134">**WindowsProcess**</span></span>|<span data-ttu-id="cca9c-135">Konfiguruje Windows procesów.</span><span class="sxs-lookup"><span data-stu-id="cca9c-135">Configures Windows processes.</span></span>|

<span data-ttu-id="cca9c-136">Zasoby OOB umożliwiają dobry punkt wyjścia dla typowych operacji.</span><span class="sxs-lookup"><span data-stu-id="cca9c-136">The OOB resources allow a good starting point for common operations.</span></span> <span data-ttu-id="cca9c-137">Jeśli zasoby OOB nie odpowiada Twoim potrzebom, możesz napisać własne [zasób dostosowany](../resources/authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="cca9c-137">If the OOB resources do not meet your needs, you can write your own [Custom Resource](../resources/authoringResource.md).</span></span> <span data-ttu-id="cca9c-138">Przed przystąpieniem do napisania zasobów niestandardowych, aby pomóc w rozwiązaniu problemu powinien wyglądać za pośrednictwem ogromną liczbę zasobów DSC, które zostały już utworzone przez firmę Microsoft i społeczność programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cca9c-138">Before you write a custom resource to solve your problem, you should look through the vast number of DSC resources that have already been created by both Microsoft and the PowerShell community.</span></span>

<span data-ttu-id="cca9c-139">Zasoby DSC można znaleźć w obu [galerii programu PowerShell](https://www.powershellgallery.com/) i [GitHub](https://github.com/).</span><span class="sxs-lookup"><span data-stu-id="cca9c-139">You can find DSC resources in both the [PowerShell Gallery](https://www.powershellgallery.com/) and [GitHub](https://github.com/).</span></span> <span data-ttu-id="cca9c-140">Zasoby DSC można także zainstalować bezpośrednio z poziomu przy użyciu konsoli programu PowerShell [PowerShellGet](/powershell/module/powershellget/).</span><span class="sxs-lookup"><span data-stu-id="cca9c-140">You can also install DSC resources directly from the PowerShell console using [PowerShellGet](/powershell/module/powershellget/).</span></span>

## <a name="installing-powershellget"></a><span data-ttu-id="cca9c-141">Instalowanie menedżera pakietów PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="cca9c-141">Installing PowerShellGet</span></span>

<span data-ttu-id="cca9c-142">Aby ustalić, czy masz już **PowerShell** uzyskać lub Aby uzyskać pomoc dotyczącą instalowania go, zapoznaj się z następującymi wskazówkami: [Instalowanie modułu PowerShellGet](/powershell/gallery/installing-psget).</span><span class="sxs-lookup"><span data-stu-id="cca9c-142">To determine if you already have **PowerShell** get, or to get help installing it, see the following guide: [Installing PowerShellGet](/powershell/gallery/installing-psget).</span></span>

## <a name="finding-dsc-resources-using-powershellget"></a><span data-ttu-id="cca9c-143">Znajdowanie zasobów DSC przy użyciu funkcji PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="cca9c-143">Finding DSC resources using PowerShellGet</span></span>

<span data-ttu-id="cca9c-144">Gdy **PowerShellGet** jest zainstalowany w systemie, można znaleźć i zainstalować zasoby DSC hostowane w [galerii programu PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="cca9c-144">Once **PowerShellGet** is installed on your system, you can find and install DSC resources hosted in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

<span data-ttu-id="cca9c-145">Najpierw za pomocą [Znajdź-DSCResource](/powershell/module/powershellget/find-dscresource) polecenia cmdlet, aby znaleźć zasoby DSC.</span><span class="sxs-lookup"><span data-stu-id="cca9c-145">First, use the [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet to find DSC resources.</span></span> <span data-ttu-id="cca9c-146">Po uruchomieniu `Find-DSCResource` po raz pierwszy, zobaczysz następujący monit, aby zainstalować dostawcę"NuGet".</span><span class="sxs-lookup"><span data-stu-id="cca9c-146">When you run `Find-DSCResource` for the first time, you see the following prompt to install the "NuGet provider".</span></span>

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

<span data-ttu-id="cca9c-147">Po naciskając klawisz "y" "NuGet" dostawca jest zainstalowany, pojawi się lista zasobów DSC, które można zainstalować z galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cca9c-147">After pressing 'y', the "NuGet" provider is installed, you see a list of DSC resources that you can install from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="cca9c-148">Lista nie jest wyświetlany, ponieważ jest bardzo duża.</span><span class="sxs-lookup"><span data-stu-id="cca9c-148">List is not shown because it is very large.</span></span>

<span data-ttu-id="cca9c-149">Można również określić `-Name` przy użyciu symboli wieloznacznych, parametr lub `-Filter` parametru bez symboli wieloznacznych, aby zawęzić kryteria wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="cca9c-149">You can also specify the `-Name` parameter using wildcards, or `-Filter` parameter without wildcards to narrow down your search.</span></span> <span data-ttu-id="cca9c-150">W tym przykładzie próbuje znaleźć zasobu "Strefa czasowa" DSC przy użyciu symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="cca9c-150">This example attempts to find a "TimeZone" DSC resource using the wildcards.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cca9c-151">Obecnie ma błędów w `Find-DSCResource` polecenia cmdlet, który uniemożliwia przy użyciu symboli wieloznacznych w obu `-Name` i `-Filter` parametrów.</span><span class="sxs-lookup"><span data-stu-id="cca9c-151">Currently there is a bug in the `Find-DSCResource` cmdlet that prevents using wildcards in both the `-Name` and `-Filter` parameters.</span></span> <span data-ttu-id="cca9c-152">Drugi przykład poniżej przedstawiono obejście przy użyciu `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="cca9c-152">The second example below shows a workaround using `Where-Object`.</span></span>

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

<span data-ttu-id="cca9c-153">Można również użyć `Where-Object` znajdowanie zasobów DSC przy użyciu bardziej szczegółowego filtrowania.</span><span class="sxs-lookup"><span data-stu-id="cca9c-153">You can also use `Where-Object` to find DSC resources with more granular filtering.</span></span> <span data-ttu-id="cca9c-154">Ta metoda będzie przebiegać wolniej niż wbudowane filtrowanie parametrów.</span><span class="sxs-lookup"><span data-stu-id="cca9c-154">This approach will be slower than using built in filtering parameters.</span></span>

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

<span data-ttu-id="cca9c-155">Aby uzyskać więcej informacji na temat filtrowania, zobacz [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span><span class="sxs-lookup"><span data-stu-id="cca9c-155">For more information on filtering, see [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span>

## <a name="installing-dsc-resources-using-powershellget"></a><span data-ttu-id="cca9c-156">Instalowanie zasobów DSC przy użyciu funkcji PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="cca9c-156">Installing DSC Resources using PowerShellGet</span></span>

<span data-ttu-id="cca9c-157">Aby zainstalować zasobów DSC, użyj [Install-Module](/powershell/module/PowershellGet/Install-Module) polecenia cmdlet, określając nazwę modułu, wyświetlany w obszarze **modułu** nazwy w wynikach wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="cca9c-157">To install a DSC resource, use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, specifying the name of the module shown under **Module** name in your search results.</span></span>

<span data-ttu-id="cca9c-158">"Strefa czasowa" istnieje zasób w module "ComputerManagementDSC", więc to znaczy instaluje w tym przykładzie moduł.</span><span class="sxs-lookup"><span data-stu-id="cca9c-158">The "TimeZone" resource exists in the "ComputerManagementDSC" module, so that is the module this example installs.</span></span>

> [!NOTE]
> <span data-ttu-id="cca9c-159">Jeśli nie ma zaufany galerii programu PowerShell, zostanie wyświetlone ostrzeżenie poniżej monitowania o potwierdzenie i pokazanie, jak unikać kolejnych monitów instaluje.</span><span class="sxs-lookup"><span data-stu-id="cca9c-159">If you have not trusted the PowerShell gallery, you see the warning below asking for confirmation, and instructing you how to avoid subsequent prompts on installs.</span></span>

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="cca9c-160">Naciśnij klawisz t, aby kontynuować instalację modułu.</span><span class="sxs-lookup"><span data-stu-id="cca9c-160">Press 'y' to continue installing the module.</span></span> <span data-ttu-id="cca9c-161">Po instalacji, możesz sprawdzić, czy nowy zasób jest instalowana za pomocą [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span><span class="sxs-lookup"><span data-stu-id="cca9c-161">After install, you can verify that your new resource is installed using [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span></span>

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

<span data-ttu-id="cca9c-162">Inne zasoby można również wyświetlić w nowo zainstalowanym module, określając `-ModuleName` parametru.</span><span class="sxs-lookup"><span data-stu-id="cca9c-162">You can also view other resources in your newly installed module, by specifying the `-ModuleName` parameter.</span></span>

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a><span data-ttu-id="cca9c-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cca9c-163">See also</span></span>

- [<span data-ttu-id="cca9c-164">Co to są zasoby?</span><span class="sxs-lookup"><span data-stu-id="cca9c-164">What are Resources?</span></span>](../resources/resources.md)
