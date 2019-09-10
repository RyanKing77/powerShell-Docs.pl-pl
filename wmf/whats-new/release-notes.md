---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Informacje o wersji programu WMF 5.x
ms.openlocfilehash: 8924240a4bbedcd34bc68b7cacdd23189a3716d6
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848142"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a><span data-ttu-id="c64c7-103">Informacje o wersji systemu Windows Management Framework (WMF) 5. x</span><span class="sxs-lookup"><span data-stu-id="c64c7-103">Windows Management Framework (WMF) 5.x Release Notes</span></span>

## <a name="wmf-50-changes"></a><span data-ttu-id="c64c7-104">Zmiany w programie WMF 5,0</span><span class="sxs-lookup"><span data-stu-id="c64c7-104">WMF 5.0 Changes</span></span>

- <span data-ttu-id="c64c7-105">Program PowerShell 5,0 dodaje nowy strumień **informacji o** strukturze</span><span class="sxs-lookup"><span data-stu-id="c64c7-105">PowerShell 5.0 adds a new structured **Information** stream</span></span>
- <span data-ttu-id="c64c7-106">Ulepszenia konfiguracji DSC, w tym cztery nowe zasoby DSC:</span><span class="sxs-lookup"><span data-stu-id="c64c7-106">Improvements to DSC including four new DSC resources:</span></span>
  - <span data-ttu-id="c64c7-107">Zasób windowsfeatureset</span><span class="sxs-lookup"><span data-stu-id="c64c7-107">WindowsFeatureSet</span></span>
  - <span data-ttu-id="c64c7-108">Zasób windowsoptionalfeatureset</span><span class="sxs-lookup"><span data-stu-id="c64c7-108">WindowsOptionalFeatureSet</span></span>
  - <span data-ttu-id="c64c7-109">Zasób serviceset</span><span class="sxs-lookup"><span data-stu-id="c64c7-109">ServiceSet</span></span>
  - <span data-ttu-id="c64c7-110">Zasób processset</span><span class="sxs-lookup"><span data-stu-id="c64c7-110">ProcessSet</span></span>
- <span data-ttu-id="c64c7-111">Dodano tylko wystarczającą administrację, aby umożliwić administrację opartą na rolach za pośrednictwem komunikacji zdalnej programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="c64c7-111">Added Just Enough Administration to enable role-based administration through PowerShell remoting</span></span>
- <span data-ttu-id="c64c7-112">Program PowerShell 5,0 rozszerza język, tak aby obejmował klasy i wyliczenia zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="c64c7-112">PowerShell 5.0 extends the language to include user-defined classes and enumerations</span></span>
- <span data-ttu-id="c64c7-113">Udoskonalone funkcje debugowania w programie PowerShell ISE i dodane debugowanie zdalne</span><span class="sxs-lookup"><span data-stu-id="c64c7-113">Improved debugging features in PowerShell ISE and added remote debugging</span></span>
- <span data-ttu-id="c64c7-114">Dodano moduły PowerShellGet i PackageManagement</span><span class="sxs-lookup"><span data-stu-id="c64c7-114">Added the PowerShellGet and PackageManagement modules</span></span>
- <span data-ttu-id="c64c7-115">Ulepszone rejestrowanie i transkrypcje skryptu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="c64c7-115">Enhanced PowerShell script logging and transcripts</span></span>
- <span data-ttu-id="c64c7-116">Dodawanie poleceń cmdlet składni wiadomości kryptograficznych</span><span class="sxs-lookup"><span data-stu-id="c64c7-116">Add Cryptographic Message Syntax cmdlets</span></span>
- <span data-ttu-id="c64c7-117">Program WMF 5,0 zawiera moduł NetworkSwitchManager dla systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c64c7-117">WMF 5.0 includes the NetworkSwitchManager module for Windows</span></span>
- <span data-ttu-id="c64c7-118">Dodano moduł Microsoft. PowerShell. ODataUtils</span><span class="sxs-lookup"><span data-stu-id="c64c7-118">Added the Microsoft.PowerShell.ODataUtils module</span></span>
- <span data-ttu-id="c64c7-119">Dodano obsługę rejestrowania spisu oprogramowania (SIL)</span><span class="sxs-lookup"><span data-stu-id="c64c7-119">Added support for Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="c64c7-120">Nowe lub zaktualizowane polecenia cmdlet w odpowiedzi na żądania i problemy użytkowników</span><span class="sxs-lookup"><span data-stu-id="c64c7-120">Sever new or update cmdlets in response to user requests and issues</span></span>

## <a name="wmf-51-changes"></a><span data-ttu-id="c64c7-121">Zmiany w programie WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="c64c7-121">WMF 5.1 Changes</span></span>

<span data-ttu-id="c64c7-122">Program WMF 5,1 zawiera składniki programu PowerShell, usługi WMI, usługi WinRM i spisu oprogramowania SIL, które zostały wydane z systemem Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="c64c7-122">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span> <span data-ttu-id="c64c7-123">Program WMF 5,1 można zainstalować w systemie Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 i 2012 R2 i oferuje kilka ulepszeń w porównaniu z modelem 5,0 WMF, w tym:</span><span class="sxs-lookup"><span data-stu-id="c64c7-123">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides several improvements over WMF 5.0 including:</span></span>

- <span data-ttu-id="c64c7-124">Nowe polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="c64c7-124">New cmdlets</span></span>
- <span data-ttu-id="c64c7-125">Ulepszenia rozwiązania PowerShellGet obejmują wymuszanie podpisanych modułów i instalowanie modułów JEA</span><span class="sxs-lookup"><span data-stu-id="c64c7-125">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="c64c7-126">Dodano obsługę funkcji PackageManagement na potrzeby kontenerów, instalacji CBS, instalacji opartej na plikach EXE i pakietów CAB</span><span class="sxs-lookup"><span data-stu-id="c64c7-126">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="c64c7-127">Ulepszenia debugowania dla klas konfiguracji DSC i programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="c64c7-127">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="c64c7-128">Ulepszenia zabezpieczeń obejmują wymuszanie modułów podpisanych w wykazie pochodzących z serwera ściągania oraz w przypadku korzystania z poleceń cmdlet PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="c64c7-128">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="c64c7-129">Odpowiedzi na wiele problemów i żądań użytkowników</span><span class="sxs-lookup"><span data-stu-id="c64c7-129">Responses to a number of user requests and issues</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c64c7-130">Przed zainstalowaniem programu WMF 5,1 w systemie Windows Server 2008 lub Windows 7 upewnij się, że nie zainstalowano plików WMF 3,0.</span><span class="sxs-lookup"><span data-stu-id="c64c7-130">Before you install WMF 5.1 on Windows Server 2008 or Windows 7, confirm that WMF 3.0 isn't installed.</span></span> <span data-ttu-id="c64c7-131">Aby uzyskać więcej informacji, zobacz [wymagania wstępne dotyczące WMF 5,1 dla systemu Windows Server 2008 R2 z dodatkiem SP1 i Windows 7 z dodatkiem SP1](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1).</span><span class="sxs-lookup"><span data-stu-id="c64c7-131">For more information, see [WMF 5.1 Prerequisites for Windows Server 2008 R2 SP1 and Windows 7 SP1](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1).</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="c64c7-132">Wersje programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="c64c7-132">PowerShell Editions</span></span>

<span data-ttu-id="c64c7-133">Począwszy od wersji 5,1, program PowerShell jest dostępny w różnych wersjach, które oznaczają różne zestawy funkcji i zgodność platformy.</span><span class="sxs-lookup"><span data-stu-id="c64c7-133">Starting with version 5.1, PowerShell is available in different editions that denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="c64c7-134">**Wersja klasyczna:** Oparta na .NET Framework i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w pełnych wersjach systemu Windows, takich jak Server Core i Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="c64c7-134">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="c64c7-135">**Wersja podstawowa:** Oparta na oprogramowaniu .NET Core i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w zmniejszonych wersjach systemu Windows, takich jak nano Server i Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="c64c7-135">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="learn-more-about-using-powershell-editions"></a><span data-ttu-id="c64c7-136">Dowiedz się więcej o korzystaniu z wersji programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="c64c7-136">Learn more about using PowerShell Editions</span></span>

- [<span data-ttu-id="c64c7-137">Określanie uruchomionej wersji programu PowerShell przy użyciu $PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="c64c7-137">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="c64c7-138">Filtrowanie wyników Get-module według CompatiblePSEditions przy użyciu parametru PSEdition</span><span class="sxs-lookup"><span data-stu-id="c64c7-138">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="c64c7-139">Zapobiegaj wykonywaniu skryptów, chyba że jest uruchomiona w zgodnej wersji programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="c64c7-139">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="c64c7-140">Deklarowanie zgodności modułu z określonymi wersjami programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="c64c7-140">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a><span data-ttu-id="c64c7-141">Pamięć podręczna analizy modułów</span><span class="sxs-lookup"><span data-stu-id="c64c7-141">Module Analysis Cache</span></span>

<span data-ttu-id="c64c7-142">Począwszy od programu WMF 5,1, program PowerShell zapewnia kontrolę nad plikiem używanym do buforowania danych dotyczących modułu, takich jak eksportowane polecenia.</span><span class="sxs-lookup"><span data-stu-id="c64c7-142">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="c64c7-143">Domyślnie ta pamięć podręczna jest przechowywana w pliku `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="c64c7-143">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span> <span data-ttu-id="c64c7-144">Pamięć podręczna jest zwykle odczytywana podczas uruchamiania podczas wyszukiwania polecenia i jest zapisywana w wątku w tle, gdy moduł zostanie zaimportowany.</span><span class="sxs-lookup"><span data-stu-id="c64c7-144">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="c64c7-145">Aby zmienić domyślną lokalizację pamięci podręcznej, należy ustawić `$env:PSModuleAnalysisCachePath` zmienną środowiskową przed uruchomieniem programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c64c7-145">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span> <span data-ttu-id="c64c7-146">Zmiany w tej zmiennej środowiskowej będą miały wpływ tylko na procesy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="c64c7-146">Changes to this environment variable will only affect children processes.</span></span> <span data-ttu-id="c64c7-147">Wartość powinna mieć nazwę pełną ścieżkę (łącznie z nazwą pliku), która ma uprawnienia do tworzenia i zapisywania plików przez program PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c64c7-147">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span> <span data-ttu-id="c64c7-148">Aby wyłączyć pamięć podręczną plików, ustaw tę wartość na nieprawidłową lokalizację, na przykład:</span><span class="sxs-lookup"><span data-stu-id="c64c7-148">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="c64c7-149">Spowoduje to ustawienie ścieżki do nieprawidłowego urządzenia.</span><span class="sxs-lookup"><span data-stu-id="c64c7-149">This sets the path to an invalid device.</span></span> <span data-ttu-id="c64c7-150">Jeśli program PowerShell nie może zapisać do ścieżki, żaden błąd nie jest zwracany, ale raportowanie błędów można zobaczyć przy użyciu śledzenia:</span><span class="sxs-lookup"><span data-stu-id="c64c7-150">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="c64c7-151">Podczas zapisywania pamięci podręcznej program PowerShell sprawdzi istnienie modułów, które już nie istnieją, aby uniknąć niepotrzebnej dużej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="c64c7-151">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span> <span data-ttu-id="c64c7-152">Czasami te testy nie są pożądane, w takim przypadku można je wyłączyć przez ustawienie:</span><span class="sxs-lookup"><span data-stu-id="c64c7-152">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="c64c7-153">Ustawienie tej zmiennej środowiskowej zacznie obowiązywać natychmiast w bieżącym procesie.</span><span class="sxs-lookup"><span data-stu-id="c64c7-153">Setting this environment variable will take effect immediately in the current process.</span></span>

## <a name="specifying-module-version"></a><span data-ttu-id="c64c7-154">Określanie wersji modułu</span><span class="sxs-lookup"><span data-stu-id="c64c7-154">Specifying module version</span></span>

<span data-ttu-id="c64c7-155">W programie WMF 5,1 `using module` działa tak samo jak w przypadku innych konstrukcji związanych z modułami w programie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c64c7-155">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span>
<span data-ttu-id="c64c7-156">Wcześniej nie było możliwości określenia konkretnej wersji modułu; Jeśli istnieją różne wersje, spowoduje to błąd.</span><span class="sxs-lookup"><span data-stu-id="c64c7-156">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="c64c7-157">W programie WMF 5,1:</span><span class="sxs-lookup"><span data-stu-id="c64c7-157">In WMF 5.1:</span></span>

- <span data-ttu-id="c64c7-158">Można użyć [konstruktora ModuleSpecification (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="c64c7-158">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

  <span data-ttu-id="c64c7-159">Ta tabela skrótów ma ten sam format co `Get-Module -FullyQualifiedName`.</span><span class="sxs-lookup"><span data-stu-id="c64c7-159">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

  <span data-ttu-id="c64c7-160">**Przykład:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="c64c7-160">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

- <span data-ttu-id="c64c7-161">Jeśli istnieje wiele wersji modułu, program PowerShell używa tej **samej logiki rozpoznawania** jak `Import-Module` i nie zwróci błędu--takie samo zachowanie jak `Import-Module` i `Import-DscResource`.</span><span class="sxs-lookup"><span data-stu-id="c64c7-161">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

## <a name="improvements-to-pester"></a><span data-ttu-id="c64c7-162">Ulepszenia dla szkodnika</span><span class="sxs-lookup"><span data-stu-id="c64c7-162">Improvements to Pester</span></span>

<span data-ttu-id="c64c7-163">W programie WMF 5,1 wersja szkodnika, która jest dostarczana z programem PowerShell, została zaktualizowana z 3.3.5 na 3.4.0.</span><span class="sxs-lookup"><span data-stu-id="c64c7-163">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0.</span></span>
<span data-ttu-id="c64c7-164">Ta aktualizacja umożliwia lepsze zachowanie szkodnika na serwerze nano Server.</span><span class="sxs-lookup"><span data-stu-id="c64c7-164">This update enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="c64c7-165">Zmiany w szkodnikach można przejrzeć, sprawdzając [Dziennik zmian](https://github.com/pester/Pester/blob/master/CHANGELOG.md) w repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="c64c7-165">You can review the changes in Pest by inspecting the [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) in the GitHub repository.</span></span>
