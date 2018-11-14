---
ms.date: 11/06/2018
contributor: JKeithB
keywords: Galeria programu powershell, polecenie cmdlet, galerii programu PowerShell, psget
title: Praca z lokalnym PSRepositories
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619257"
---
# <a name="working-with-local-powershellget-repositories"></a><span data-ttu-id="df4dc-103">Praca z lokalne repozytoria modułu PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="df4dc-103">Working with local PowerShellGet Repositories</span></span>

<span data-ttu-id="df4dc-104">Repozytoriów Obsługa modułu PowerShellGet innych niż Galeria programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df4dc-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="df4dc-105">Te polecenia cmdlet Włącz następujące scenariusze:</span><span class="sxs-lookup"><span data-stu-id="df4dc-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="df4dc-106">Obsługuje zestaw zaufanych, wstępnie zatwierdzonych modułów programu PowerShell do użycia w danym środowisku</span><span class="sxs-lookup"><span data-stu-id="df4dc-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="df4dc-107">Testowanie potoku ciągłej integracji/ciągłego wdrażania, który kompiluje modułów programu PowerShell lub skryptów</span><span class="sxs-lookup"><span data-stu-id="df4dc-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="df4dc-108">Dostarczanie modułów i skryptów programu PowerShell do systemów, które nie mogą uzyskać dostęp do Internetu</span><span class="sxs-lookup"><span data-stu-id="df4dc-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>

<span data-ttu-id="df4dc-109">W tym artykule opisano sposób konfigurowania lokalnego repozytorium programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df4dc-109">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="df4dc-110">Artykuł obejmuje również [OfflinePowerShellGetDeploy][] modułu, które są dostępne z galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df4dc-110">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="df4dc-111">Ten moduł zawiera polecenia cmdlet, aby zainstalować najnowszą wersję modułu PowerShellGet w lokalnym repozytorium.</span><span class="sxs-lookup"><span data-stu-id="df4dc-111">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="df4dc-112">Typy repozytorium lokalnego</span><span class="sxs-lookup"><span data-stu-id="df4dc-112">Local repository types</span></span>

<span data-ttu-id="df4dc-113">Istnieją dwa sposoby tworzenia lokalnego PSRepository: NuGet serwer lub udział plików.</span><span class="sxs-lookup"><span data-stu-id="df4dc-113">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="df4dc-114">Każdy typ ma zalety i wady:</span><span class="sxs-lookup"><span data-stu-id="df4dc-114">Each type has advantages and disadvantages:</span></span>

<span data-ttu-id="df4dc-115">Serwer NuGet</span><span class="sxs-lookup"><span data-stu-id="df4dc-115">NuGet Server</span></span>

| <span data-ttu-id="df4dc-116">Zalety</span><span class="sxs-lookup"><span data-stu-id="df4dc-116">Advantages</span></span>| <span data-ttu-id="df4dc-117">Wady</span><span class="sxs-lookup"><span data-stu-id="df4dc-117">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="df4dc-118">Ścisłe naśladowanie funkcji galerii PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="df4dc-118">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="df4dc-119">Wymaga aplikacji wielowarstwowej, operacje, planowania i pomoc techniczna</span><span class="sxs-lookup"><span data-stu-id="df4dc-119">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="df4dc-120">NuGet jest zintegrowany z programem Visual Studio i innych narzędzi</span><span class="sxs-lookup"><span data-stu-id="df4dc-120">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="df4dc-121">Model uwierzytelniania i konieczne zarządzanie kontami NuGet</span><span class="sxs-lookup"><span data-stu-id="df4dc-121">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="df4dc-122">NuGet obsługuje metadanych w `.Nupkg` pakietów</span><span class="sxs-lookup"><span data-stu-id="df4dc-122">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="df4dc-123">Publikowanie wymaga klucza interfejsu API zarządzania i konserwacji</span><span class="sxs-lookup"><span data-stu-id="df4dc-123">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="df4dc-124">Umożliwia wyszukiwanie pakietów administracyjnych, itp.</span><span class="sxs-lookup"><span data-stu-id="df4dc-124">Provides search, package administration, etc.</span></span> | |

<span data-ttu-id="df4dc-125">Udział plików</span><span class="sxs-lookup"><span data-stu-id="df4dc-125">File Share</span></span>

| <span data-ttu-id="df4dc-126">Zalety</span><span class="sxs-lookup"><span data-stu-id="df4dc-126">Advantages</span></span>| <span data-ttu-id="df4dc-127">Wady</span><span class="sxs-lookup"><span data-stu-id="df4dc-127">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="df4dc-128">Łatwe konfigurowanie, tworzenie kopii zapasowej i konserwacji</span><span class="sxs-lookup"><span data-stu-id="df4dc-128">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="df4dc-129">Metadane używane przez moduł PowerShellGet jest niedostępna</span><span class="sxs-lookup"><span data-stu-id="df4dc-129">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="df4dc-130">Model zabezpieczeń proste — uprawnienia użytkownika do udziału</span><span class="sxs-lookup"><span data-stu-id="df4dc-130">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="df4dc-131">Brak interfejsu użytkownika po przekroczeniu podstawowy udział pliku</span><span class="sxs-lookup"><span data-stu-id="df4dc-131">No UI beyond basic file share</span></span> |
| <span data-ttu-id="df4dc-132">Bez ograniczeń, takich jak zastąpienie istniejących elementów</span><span class="sxs-lookup"><span data-stu-id="df4dc-132">No constraints such as replacing existing items</span></span> | <span data-ttu-id="df4dc-133">Ograniczonych zabezpieczeń i kto co aktualizacji nie rejestrowania</span><span class="sxs-lookup"><span data-stu-id="df4dc-133">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="df4dc-134">Moduł PowerShellGet współpracuje z typu i obsługuje lokalizowanie wersje i zależności instalacji.</span><span class="sxs-lookup"><span data-stu-id="df4dc-134">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="df4dc-135">Jednak niektóre funkcje, które działają w przypadku galerii programu PowerShell nie są dostępne dla podstawowej serwerów NuGet ani udziałów plików.</span><span class="sxs-lookup"><span data-stu-id="df4dc-135">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="df4dc-136">Wszystko, co jest pakietem - rozróżnienia skryptów, moduły, zasoby DSC lub możliwości roli.</span><span class="sxs-lookup"><span data-stu-id="df4dc-136">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="df4dc-137">Serwery udziału plików nie może wyświetlić metadane pakietów, łącznie z tagami.</span><span class="sxs-lookup"><span data-stu-id="df4dc-137">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="df4dc-138">Tworzenia repozytorium lokalnego</span><span class="sxs-lookup"><span data-stu-id="df4dc-138">Creating a local repository</span></span>

<span data-ttu-id="df4dc-139">Następujący artykuł zawiera kroki dotyczące konfigurowania serwera NuGet.</span><span class="sxs-lookup"><span data-stu-id="df4dc-139">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="df4dc-140">[NuGet.Server][]</span><span class="sxs-lookup"><span data-stu-id="df4dc-140">[NuGet.Server][]</span></span>

<span data-ttu-id="df4dc-141">Postępuj zgodnie z instrukcjami aż do momentu dodania pakietów.</span><span class="sxs-lookup"><span data-stu-id="df4dc-141">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="df4dc-142">Kroki [publikowania pakietu](#publishing-to-a-local-repository) zostały omówione w dalszej części tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="df4dc-142">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="df4dc-143">W przypadku repozytorium opartych na udziałach plików upewnij się, czy użytkownicy mają uprawnienia dostępu do udziału plików.</span><span class="sxs-lookup"><span data-stu-id="df4dc-143">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="df4dc-144">Rejestrowanie repozytorium lokalnego</span><span class="sxs-lookup"><span data-stu-id="df4dc-144">Registering a local repository</span></span>

<span data-ttu-id="df4dc-145">Przed użyciem repozytorium, musi być zarejestrowana, za pomocą `Register-PSRepository` polecenia.</span><span class="sxs-lookup"><span data-stu-id="df4dc-145">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="df4dc-146">W poniższych przykładach **InstallationPolicy** ustawiono *zaufanego*, przy założeniu, że masz zaufanie własnego repozytorium.</span><span class="sxs-lookup"><span data-stu-id="df4dc-146">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="df4dc-147">Zwróć uwagę na różnicę między jak obsługiwać dwa polecenia **ScriptSourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="df4dc-147">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="df4dc-148">W przypadku repozytoriów z opartych na udziałach plików **SourceLocation** i **ScriptSourceLocation** muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="df4dc-148">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="df4dc-149">Repozytorium opartego na sieci web, muszą być różne, dlatego w tym przykładzie końcowe "/" zostanie dodany do **SourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="df4dc-149">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="df4dc-150">Jeśli chcesz, aby nowo utworzony PSRepository jako repozytorium domyślne, należy wyrejestrować wszystkie inne PSRepositories.</span><span class="sxs-lookup"><span data-stu-id="df4dc-150">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="df4dc-151">Przykład:</span><span class="sxs-lookup"><span data-stu-id="df4dc-151">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="df4dc-152">Nazwa repozytorium "Galerii programu PowerShell" jest zarezerwowana do użytku w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df4dc-152">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="df4dc-153">Można wyrejestrować galerii programu PowerShell, ale nie można ponownie użyć nazwy galerii programu PowerShell, która znajduje się w przypadku dowolnego innego repozytorium.</span><span class="sxs-lookup"><span data-stu-id="df4dc-153">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="df4dc-154">Jeśli trzeba przywrócić galerii programu PowerShell, uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="df4dc-154">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="df4dc-155">Publikowanie lokalnego repozytorium</span><span class="sxs-lookup"><span data-stu-id="df4dc-155">Publishing to a local repository</span></span>

<span data-ttu-id="df4dc-156">Po zarejestrowaniu PSRepository lokalnym, możesz opublikować swoje lokalne PSRepository.</span><span class="sxs-lookup"><span data-stu-id="df4dc-156">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="df4dc-157">Istnieją dwa główne scenariusze publikowania: publikowanie własny moduł i publikowania modułu z galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df4dc-157">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="df4dc-158">Publikowanie modułu Twojego autorstwa</span><span class="sxs-lookup"><span data-stu-id="df4dc-158">Publishing a module you authored</span></span>

<span data-ttu-id="df4dc-159">Użyj `Publish-Module` i `Publish-Script` do publikowania modułu swoje lokalne PSRepository taki sam sposób jak w przypadku galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df4dc-159">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="df4dc-160">Określ lokalizację, w kodzie</span><span class="sxs-lookup"><span data-stu-id="df4dc-160">Specify the location for your code</span></span>
- <span data-ttu-id="df4dc-161">Podaj klucz interfejsu API</span><span class="sxs-lookup"><span data-stu-id="df4dc-161">Supply an API key</span></span>
- <span data-ttu-id="df4dc-162">Określ nazwę repozytorium.</span><span class="sxs-lookup"><span data-stu-id="df4dc-162">Specify the repository name.</span></span> <span data-ttu-id="df4dc-163">Na przykład `-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="df4dc-163">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="df4dc-164">Należy utworzyć konto w serwer NuGet, a następnie zaloguj się wygenerować i zapisać klucz interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="df4dc-164">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="df4dc-165">Dla udziału plików należy użyć wartości NuGetApiKey dowolny ciąg nie jest pusty.</span><span class="sxs-lookup"><span data-stu-id="df4dc-165">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="df4dc-166">Przykłady:</span><span class="sxs-lookup"><span data-stu-id="df4dc-166">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="df4dc-167">Aby zapewnić bezpieczeństwo, klucze interfejsu API nie może być zakodowane w skryptach.</span><span class="sxs-lookup"><span data-stu-id="df4dc-167">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="df4dc-168">Należy używać systemu bezpieczne zarządzanie kluczami.</span><span class="sxs-lookup"><span data-stu-id="df4dc-168">Use a secure key management system.</span></span>

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="df4dc-169">Publikowanie modułu z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="df4dc-169">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="df4dc-170">Aby opublikować modułu z galerii programu PowerShell do swojej lokalnej PSRepository, można użyć polecenia cmdlet "Zapisz pakiet".</span><span class="sxs-lookup"><span data-stu-id="df4dc-170">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="df4dc-171">Określ nazwę pakietu</span><span class="sxs-lookup"><span data-stu-id="df4dc-171">Specify the Name of the Package</span></span>
- <span data-ttu-id="df4dc-172">Określ "NuGet" jako dostawcy</span><span class="sxs-lookup"><span data-stu-id="df4dc-172">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="df4dc-173">Określ lokalizację galerii programu PowerShell jako (źródła https://www.powershellgallery.com/api/v2)</span><span class="sxs-lookup"><span data-stu-id="df4dc-173">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="df4dc-174">Określ ścieżkę do repozytorium lokalnego</span><span class="sxs-lookup"><span data-stu-id="df4dc-174">Specify the path to your local Repository</span></span>

<span data-ttu-id="df4dc-175">Przykład:</span><span class="sxs-lookup"><span data-stu-id="df4dc-175">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="df4dc-176">Jeśli Twoje lokalne PSRepository jest oparte na sieci web, wymaga dodatkowego kroku, który używa nuget.exe do publikowania.</span><span class="sxs-lookup"><span data-stu-id="df4dc-176">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="df4dc-177">Zajrzyj do dokumentacji przy użyciu [nuget.exe][].</span><span class="sxs-lookup"><span data-stu-id="df4dc-177">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="df4dc-178">Instalowanie modułu PowerShellGet w systemie bez połączenia</span><span class="sxs-lookup"><span data-stu-id="df4dc-178">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="df4dc-179">Wdrażanie modułu PowerShellGet jest trudne w środowiskach, które wymagają systemów, które mogą być rozłączone z Internetu.</span><span class="sxs-lookup"><span data-stu-id="df4dc-179">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="df4dc-180">Moduł PowerShellGet ma ładowania początkowego procesu, który instaluje najnowszą wersję z pierwszym, który jest używany.</span><span class="sxs-lookup"><span data-stu-id="df4dc-180">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="df4dc-181">Moduł OfflinePowerShellGetDeploy w galerii programu PowerShell udostępnia polecenia cmdlet, który obsługuje ten proces ładowania.</span><span class="sxs-lookup"><span data-stu-id="df4dc-181">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="df4dc-182">Uruchomienie wdrożenie w trybie offline, należy:</span><span class="sxs-lookup"><span data-stu-id="df4dc-182">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="df4dc-183">Pobierz i zainstaluj system OfflinePowerShellGetDeploy usługi połączonej z Internetem i z odrębnych systemów</span><span class="sxs-lookup"><span data-stu-id="df4dc-183">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="df4dc-184">Pobieranie modułu PowerShellGet oraz jego zależności w systemie podłączonej do Internetu przy użyciu `Save-PowerShellGetForOffline` polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="df4dc-184">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="df4dc-185">Skopiuj modułu PowerShellGet oraz jego zależności z systemu podłączonej do Internetu do odłączonego systemu</span><span class="sxs-lookup"><span data-stu-id="df4dc-185">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="df4dc-186">Użyj `Install-PowerShellGetOffline` systemie odłączonego umieszcza modułu PowerShellGet oraz jego zależności w odpowiednich folderów</span><span class="sxs-lookup"><span data-stu-id="df4dc-186">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="df4dc-187">Następujące polecenia, użyj `Save-PowerShellGetForOffline` do wszystkich składników należy umieścić w folderze `f:\OfflinePowerShellGet`</span><span class="sxs-lookup"><span data-stu-id="df4dc-187">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="df4dc-188">W tym momencie należy udostępnić zawartość `F:\OfflinePowerShellGet` dostępne dla odłączonych systemów.</span><span class="sxs-lookup"><span data-stu-id="df4dc-188">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="df4dc-189">Uruchom `Install-PowerShellGetOffline` polecenia cmdlet do zainstalowania modułu PowerShellGet w systemie bez połączenia.</span><span class="sxs-lookup"><span data-stu-id="df4dc-189">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="df4dc-190">Należy pamiętać, że nie zostanie uruchomiony moduł PowerShellGet w sesji programu PowerShell, przed uruchomieniem tych poleceń.</span><span class="sxs-lookup"><span data-stu-id="df4dc-190">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="df4dc-191">Po załadowaniu modułu PowerShellGet w sesji nie można zaktualizować składniki.</span><span class="sxs-lookup"><span data-stu-id="df4dc-191">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="df4dc-192">W przypadku uruchomienia modułu PowerShellGet przez pomyłkę, zamknij i ponownie uruchom program PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df4dc-192">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="df4dc-193">Po uruchomieniu tych poleceń, jesteś gotowy do opublikowania PowerShellGet do lokalnego repozytorium.</span><span class="sxs-lookup"><span data-stu-id="df4dc-193">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="df4dc-194">Aby zapewnić bezpieczeństwo, klucze interfejsu API nie może być zakodowane w skryptach.</span><span class="sxs-lookup"><span data-stu-id="df4dc-194">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="df4dc-195">Należy używać systemu bezpieczne zarządzanie kluczami.</span><span class="sxs-lookup"><span data-stu-id="df4dc-195">Use a secure key management system.</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
