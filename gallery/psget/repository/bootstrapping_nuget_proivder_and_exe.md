---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: Inicjowanie dostawcy NuGet i EXE
ms.openlocfilehash: 0036972eb9a0c20469da1aadafe223e6ec80f16a
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2017
---
# <a name="bootstrap-both-nuget-provider-and-nugetexe-or-bootstrap-only-nuget-provider"></a><span data-ttu-id="8109f-103">Bootstrap zarówno dostawcy NuGet i NuGet.exe lub bootstrap tylko NuGet dostawcy</span><span class="sxs-lookup"><span data-stu-id="8109f-103">Bootstrap both NuGet provider and NuGet.exe or bootstrap only NuGet provider</span></span>

<span data-ttu-id="8109f-104">NuGet.exe nie jest uwzględniony w najnowszą wersję dostawcy NuGet.</span><span class="sxs-lookup"><span data-stu-id="8109f-104">NuGet.exe is not included in the latest NuGet provider.</span></span>
<span data-ttu-id="8109f-105">W przypadku opublikować operacje modułu lub skryptu, PowerShellGet wymaga binarne NuGet.exe pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="8109f-105">For publish operations of either a module or script, PowerShellGet requires the binary executable NuGet.exe.</span></span>
<span data-ttu-id="8109f-106">Dostawca NuGet jest wymagany tylko dla wszystkich innych operacji, w tym *znaleźć*, *zainstalować*, *zapisać*, i *odinstalować*.</span><span class="sxs-lookup"><span data-stu-id="8109f-106">Only the NuGet provider is required for all other operations, including *find*, *install*, *save*, and *uninstall*.</span></span>
<span data-ttu-id="8109f-107">PowerShellGet zawiera logikę do obsługi albo Scalonej bootstrap dostawcy NuGet i NuGet.exe lub bootstrap dostawcę NuGet.</span><span class="sxs-lookup"><span data-stu-id="8109f-107">PowerShellGet includes logic to handle either a combined bootstrap of the NuGet provider and NuGet.exe, or bootstrap of only the NuGet provider.</span></span>
<span data-ttu-id="8109f-108">W obu przypadkach powinien wystąpić tylko monitu o pojedynczym komunikacie.</span><span class="sxs-lookup"><span data-stu-id="8109f-108">In either case, only a single prompt message should occur.</span></span>
<span data-ttu-id="8109f-109">Jeśli komputer nie jest połączony z Internetem, użytkownik lub administrator musi skopiować zaufanych wystąpienie dostawcy programu NuGet i/lub pliku NuGet.exe do odłączonego maszyny.</span><span class="sxs-lookup"><span data-stu-id="8109f-109">If the machine is not connected to the Internet, the user or an administrator must copy a trusted instance of the NuGet provider and/or the NuGet.exe file to the disconnected machine.</span></span>

><span data-ttu-id="8109f-110">**Uwaga**: począwszy od wersji 6, dostawca NuGet jest dostępny w instalacji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8109f-110">**Note**: Starting with version 6, the NuGet provider is included in the installation of PowerShell.</span></span> [<span data-ttu-id="8109f-111">http://github.com/PowerShell/PowerShell</span><span class="sxs-lookup"><span data-stu-id="8109f-111">http://github.com/powershell/powershell</span></span>](http://github.com/powershell/powershell)

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="8109f-112">Rozpoznawanie błąd, gdy dostawca NuGet nie został zainstalowany na komputerze, na którym jest Internet połączone</span><span class="sxs-lookup"><span data-stu-id="8109f-112">Resolving error when the NuGet provider has not been installed on a machine that is Internet connected</span></span>

```powershell
PS C:\> Find-Module -Repository PSGallery -Verbose -Name Contoso

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n
Find-Module : NuGet provider is required to interact with NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed.
At line:1 char:1
+ Find-Module -Repository PSGallery -Verbose -Name Contoso
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Find-Module], InvalidOperationException
   + FullyQualifiedErrorId : CouldNotInstallNuGetProvider,Find-Module

PS C:\> Find-Module -Repository PSGallery -Verbose -Name Contoso

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     PSGallery        Contoso module
```
## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="8109f-113">Rozwiązywanie błędów po udostępnieniu dostawcy NuGet i NuGet.exe jest niedostępne podczas operacji publikowania na komputerze, na którym jest Internet połączone</span><span class="sxs-lookup"><span data-stu-id="8109f-113">Resolving error when the NuGet provider is available and NuGet.exe is not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module

PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="8109f-114">Rozwiązywanie błędów podczas zarówno dostawcy NuGet i NuGet.exe nie są dostępne podczas operacji publikowania na komputerze, na którym jest Internet połączone</span><span class="sxs-lookup"><span data-stu-id="8109f-114">Resolving error when both NuGet provider and NuGet.exe are not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed and NuGet.exe is available under 
one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetBinaries,Publish-Module

PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="8109f-115">Ręczne uruchamianie dostawcy NuGet, na komputerze, na którym nie jest połączony z Internetem</span><span class="sxs-lookup"><span data-stu-id="8109f-115">Manually bootstrapping the NuGet provider on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="8109f-116">Procesy przedstawionej powyżej założono komputer jest połączony z Internetem i pobrać plików z lokalizacji publicznej.</span><span class="sxs-lookup"><span data-stu-id="8109f-116">The processes demonstrated above assume the machine is connected to the Internet and can download files from a public location.</span></span>
<span data-ttu-id="8109f-117">Jeśli nie jest to możliwe, jedyną opcją jest bootstrap maszynie przy użyciu procesów powyższych i ręcznie skopiować dostawcy do izolowanego węzła za pośrednictwem procesu zaufane w trybie offline.</span><span class="sxs-lookup"><span data-stu-id="8109f-117">If that is not possible, the only option is to bootstrap a machine using the processes given above, and manually copy the provider to the isolated node through an offline trusted process.</span></span>
<span data-ttu-id="8109f-118">Najbardziej typowe przypadek użycia dla tego scenariusza jest po do obsługi izolowanym środowisku prywatnej galerii.</span><span class="sxs-lookup"><span data-stu-id="8109f-118">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>

<span data-ttu-id="8109f-119">Po wykonaniu procesu powyżej, aby zainicjować maszyny podłączonej do Internetu, można znaleźć dostawcy plików w lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="8109f-119">After following the process above to bootstrap an Internet connected machine, you will find provider files in the location:</span></span>
```
C:\Program Files\PackageManagement\ProviderAssemblies\
```

<span data-ttu-id="8109f-120">Struktura folderów i plików dostawcy NuGet będzie (prawdopodobnie z numerem wersji o różnych):</span><span class="sxs-lookup"><span data-stu-id="8109f-120">The folder/file structure of the NuGet provider will be (possibly with a different version number):</span></span>

<span data-ttu-id="8109f-121">NuGet</span><span class="sxs-lookup"><span data-stu-id="8109f-121">NuGet</span></span><br>
<span data-ttu-id="8109f-122">--2.8.5.208</span><span class="sxs-lookup"><span data-stu-id="8109f-122">--2.8.5.208</span></span><br>
<span data-ttu-id="8109f-123">---Microsoft.PackageManagement.NuGetProvider.dll</span><span class="sxs-lookup"><span data-stu-id="8109f-123">----Microsoft.PackageManagement.NuGetProvider.dll</span></span>

<span data-ttu-id="8109f-124">Skopiuj te foldery i plik przy użyciu zaufanego procesu na komputerach w trybie offline.</span><span class="sxs-lookup"><span data-stu-id="8109f-124">Copy these folders and file using a trusted process to the offline machines.</span></span>

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="8109f-125">Ręczne uruchamianie NuGet.exe do obsługi publikowania operacji na komputerze, na którym nie jest połączony z Internetem</span><span class="sxs-lookup"><span data-stu-id="8109f-125">Manually bootstrapping NuGet.exe to support publish operations on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="8109f-126">Oprócz proces ręcznie bootstrap dostawcę programu NuGet, jeśli komputer będzie używany do publikowania modułów lub skrypty w galerii prywatnej przy użyciu *modułu publikowania* lub *skryptu publikowania* poleceń cmdlet programu plik wykonywalny binarne NuGet.exe będzie wymagane.</span><span class="sxs-lookup"><span data-stu-id="8109f-126">In addition to the process to manually bootstrap the NuGet provider, if the machine will be used to publish modules or scripts to a private gallery using the *Publish-Module* or *Publish-Script* cmdlets, the NuGet.exe binary executable file will be required.</span></span>
<span data-ttu-id="8109f-127">Najbardziej typowe przypadek użycia dla tego scenariusza jest po do obsługi izolowanym środowisku prywatnej galerii.</span><span class="sxs-lookup"><span data-stu-id="8109f-127">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>
<span data-ttu-id="8109f-128">Dostępne są dwie opcje, aby uzyskać plik NuGet.exe.</span><span class="sxs-lookup"><span data-stu-id="8109f-128">There are two options to obtain the NuGet.exe file.</span></span>

<span data-ttu-id="8109f-129">Jedną z opcji jest bootstrap na komputerze, który jest połączonych z Internetem i skopiuj pliki do maszyn w trybie offline przy użyciu zaufanego procesu.</span><span class="sxs-lookup"><span data-stu-id="8109f-129">One option is to bootstrap a machine that is Internet connected and copy the files to the offline machines using a trusted process.</span></span>
<span data-ttu-id="8109f-130">Po uruchamianie maszyny połączenia internetowego, NuGet.exe binary będą znajdować się w jednym z dwóch folderów:</span><span class="sxs-lookup"><span data-stu-id="8109f-130">After bootstrapping the Internet connected machine, the NuGet.exe binary will be located in one of two folders:</span></span>

<span data-ttu-id="8109f-131">Jeśli *modułu publikowania* lub *skryptu publikowania* poleceń cmdlet zostały wykonane z podwyższonym poziomem uprawnień (jako Administrator):</span><span class="sxs-lookup"><span data-stu-id="8109f-131">If the *Publish-Module* or *Publish-Script* cmdlets were executed with elevated permissions (As an Administrator):</span></span>
```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="8109f-132">Jeśli polecenia cmdlet zostały wykonane jako użytkownik bez uprawnień z podwyższonym poziomem uprawnień:</span><span class="sxs-lookup"><span data-stu-id="8109f-132">If the cmdlets were executed as a user without elevated permissions:</span></span>
```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

<span data-ttu-id="8109f-133">Drugą opcją jest do pobrania z witryny sieci Web NuGet.Org NuGet.exe: [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html)</span><span class="sxs-lookup"><span data-stu-id="8109f-133">A second option is to download NuGet.exe from the NuGet.Org website: [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html)</span></span><br>
<span data-ttu-id="8109f-134">Po wybraniu wersji NugGet dla maszyn w środowisku produkcyjnym, upewnij się, że jest nowszy niż 2.8.5.208 i identyfikowania wersji, który został oznaczony "zalecane".</span><span class="sxs-lookup"><span data-stu-id="8109f-134">When selecting a NugGet version for production machines, make sure it is later than 2.8.5.208, and identify the version that has been labeled "recommended".</span></span>
<span data-ttu-id="8109f-135">Pamiętaj, aby odblokować plik, jeśli został on pobrany przy użyciu przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="8109f-135">Remember to unblock the file if it was downloaded using a browser.</span></span>
<span data-ttu-id="8109f-136">Można to wykonać przy użyciu *odblokowanie pliku* polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8109f-136">This can be performed by using the *Unblock-File* cmdlet.</span></span>

<span data-ttu-id="8109f-137">W obu przypadkach można skopiować pliku NuGet.exe w dowolne miejsce w *$env: ścieżka*, ale są standardowe lokalizacje:</span><span class="sxs-lookup"><span data-stu-id="8109f-137">In either case, the NuGet.exe file can be copied to any location in *$env:path*, but the standard locations are:</span></span>

<span data-ttu-id="8109f-138">Aby udostępnić plik wykonywalny, aby wszyscy użytkownicy mogli używać *modułu publikowania* i *skryptu publikowania* poleceń cmdlet:</span><span class="sxs-lookup"><span data-stu-id="8109f-138">To make the executable available so that all users can use *Publish-Module* and *Publish-Script* cmdlets:</span></span>
```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="8109f-139">Aby udostępnić plik wykonywalny dla określonego użytkownika, skopiuj do lokalizacji w ramach tylko profil użytkownika:</span><span class="sxs-lookup"><span data-stu-id="8109f-139">To make the executable available to only a specific user, copy to the location within only that user's profile:</span></span>
```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

