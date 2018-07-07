---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeria, programu powershell, polecenie cmdlet, psget
title: Uruchamianie NuGet
ms.openlocfilehash: a935b6862f3912a4b419ca00b4d4dd5aab9c20fc
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892705"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a><span data-ttu-id="938e1-103">Uruchomienie dostawcy NuGet i NuGet.exe</span><span class="sxs-lookup"><span data-stu-id="938e1-103">Bootstrap the NuGet provider and NuGet.exe</span></span>

<span data-ttu-id="938e1-104">NuGet.exe nie są objęte najnowszego dostawcę NuGet.</span><span class="sxs-lookup"><span data-stu-id="938e1-104">NuGet.exe is not included in the latest NuGet provider.</span></span>
<span data-ttu-id="938e1-105">Do publikowania w operacji modułu lub skryptu, modułu PowerShellGet wymaga binarne NuGet.exe pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="938e1-105">For publish operations of either a module or script, PowerShellGet requires the binary executable NuGet.exe.</span></span>
<span data-ttu-id="938e1-106">Dostawcy NuGet jest wymagany tylko dla wszystkich innych operacji, w tym *znaleźć*, *zainstalować*, *Zapisz*, i *odinstalować*.</span><span class="sxs-lookup"><span data-stu-id="938e1-106">Only the NuGet provider is required for all other operations, including *find*, *install*, *save*, and *uninstall*.</span></span>
<span data-ttu-id="938e1-107">Moduł PowerShellGet zawiera logikę obsługującą albo połączone bootstrap dostawcy NuGet i NuGet.exe lub bootstrap dostawcę NuGet.</span><span class="sxs-lookup"><span data-stu-id="938e1-107">PowerShellGet includes logic to handle either a combined bootstrap of the NuGet provider and NuGet.exe, or bootstrap of only the NuGet provider.</span></span>
<span data-ttu-id="938e1-108">W obu przypadkach powinien wystąpić tylko pojedynczą wiadomość szybkiego.</span><span class="sxs-lookup"><span data-stu-id="938e1-108">In either case, only a single prompt message should occur.</span></span>
<span data-ttu-id="938e1-109">Jeśli komputer nie jest połączony z Internetem, użytkownik lub administrator należy skopiować zaufanych wystąpienie dostawcy NuGet i/lub pliku NuGet.exe maszyny bez połączenia.</span><span class="sxs-lookup"><span data-stu-id="938e1-109">If the machine is not connected to the Internet, the user or an administrator must copy a trusted instance of the NuGet provider and/or the NuGet.exe file to the disconnected machine.</span></span>

> [!NOTE]
> <span data-ttu-id="938e1-110">Począwszy od wersji 6 dostawcy NuGet znajduje się w instalacji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="938e1-110">Starting with version 6, the NuGet provider is included in the installation of PowerShell.</span></span> [http://github.com/powershell/powershell](http://github.com/powershell/powershell)

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="938e1-111">Rozwiązywanie błędów podczas dostawcy NuGet nie został zainstalowany na komputerze, na którym jest Internet połączone</span><span class="sxs-lookup"><span data-stu-id="938e1-111">Resolving error when the NuGet provider has not been installed on a machine that is Internet connected</span></span>

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
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
```

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
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

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="938e1-112">Rozwiązywanie błędów podczas dostawcy NuGet jest dostępny i NuGet.exe jest niedostępne podczas operacji publikowania na komputerze, na którym jest Internet połączone</span><span class="sxs-lookup"><span data-stu-id="938e1-112">Resolving error when the NuGet provider is available and NuGet.exe is not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module

```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="938e1-113">Rozwiązywanie błędów podczas dostawcy NuGet i NuGet.exe nie są dostępne podczas operacji publikowania na komputerze, na którym jest Internet połączone</span><span class="sxs-lookup"><span data-stu-id="938e1-113">Resolving error when both NuGet provider and NuGet.exe are not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
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

```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="938e1-114">Ręczne uruchamianie dostawcy NuGet na komputerze, który nie jest połączony z Internetem</span><span class="sxs-lookup"><span data-stu-id="938e1-114">Manually bootstrapping the NuGet provider on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="938e1-115">Procesy pokazano powyżej przyjęto założenie, komputer jest połączony z Internetem i mogą pobierać pliki z lokalizacji publicznej.</span><span class="sxs-lookup"><span data-stu-id="938e1-115">The processes demonstrated above assume the machine is connected to the Internet and can download files from a public location.</span></span>
<span data-ttu-id="938e1-116">Jeśli nie jest to możliwe, jedyną opcją jest uruchamiania na maszynie za pomocą procesów podanej powyżej, a następnie ręcznie skopiuj dostawcę z izolowanym węzłem proces zaufanego w trybie offline.</span><span class="sxs-lookup"><span data-stu-id="938e1-116">If that is not possible, the only option is to bootstrap a machine using the processes given above, and manually copy the provider to the isolated node through an offline trusted process.</span></span>
<span data-ttu-id="938e1-117">Najbardziej typowy przypadek użycia, w tym scenariuszu to ona prywatną galerię do obsługi środowiska izolowanego.</span><span class="sxs-lookup"><span data-stu-id="938e1-117">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>

<span data-ttu-id="938e1-118">Po wykonaniu powyższych uruchomienie maszynę połączoną z Internetem, pliki dostawcy znajduje się w lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="938e1-118">After following the process above to bootstrap an Internet connected machine, you will find provider files in the location:</span></span>

```
C:\Program Files\PackageManagement\ProviderAssemblies\
```

<span data-ttu-id="938e1-119">Struktura folderów i plików dostawcy NuGet będzie (także z liczbą innej wersji):</span><span class="sxs-lookup"><span data-stu-id="938e1-119">The folder/file structure of the NuGet provider will be (possibly with a different version number):</span></span>

```
NuGet
--2.8.5.208
----Microsoft.PackageManagement.NuGetProvider.dll
```

<span data-ttu-id="938e1-120">Skopiuj te foldery i plik przy użyciu zaufanego proces maszyny w trybie offline.</span><span class="sxs-lookup"><span data-stu-id="938e1-120">Copy these folders and file using a trusted process to the offline machines.</span></span>

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="938e1-121">Ręczne uruchamianie NuGet.exe pozwalające obsługiwać publikowanie operacji na komputerze, na którym nie jest połączony z Internetem</span><span class="sxs-lookup"><span data-stu-id="938e1-121">Manually bootstrapping NuGet.exe to support publish operations on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="938e1-122">Oprócz procesu ręczne uruchomienie dostawcy NuGet, jeśli maszyna będzie używana do publikowania modułów i skryptów za pomocą galerii prywatnej `Publish-Module` lub `Publish-Script` poleceń cmdlet programu NuGet.exe binarny plik wykonywalny będzie wymagane.</span><span class="sxs-lookup"><span data-stu-id="938e1-122">In addition to the process to manually bootstrap the NuGet provider, if the machine will be used to publish modules or scripts to a private gallery using the `Publish-Module` or `Publish-Script` cmdlets, the NuGet.exe binary executable file will be required.</span></span>

<span data-ttu-id="938e1-123">Najbardziej typowy przypadek użycia, w tym scenariuszu to ona prywatną galerię do obsługi środowiska izolowanego.</span><span class="sxs-lookup"><span data-stu-id="938e1-123">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>
<span data-ttu-id="938e1-124">Istnieją dwa sposoby uzyskania pliku NuGet.exe.</span><span class="sxs-lookup"><span data-stu-id="938e1-124">There are two options to obtain the NuGet.exe file.</span></span>

<span data-ttu-id="938e1-125">Jedną z opcji jest uruchomienie na komputerze, na którym jest połączonych z Internetem, a następnie skopiuj pliki do przy użyciu zaufanym procesie maszyny w trybie offline.</span><span class="sxs-lookup"><span data-stu-id="938e1-125">One option is to bootstrap a machine that is Internet connected and copy the files to the offline machines using a trusted process.</span></span>
<span data-ttu-id="938e1-126">Po uruchamianie maszynę połączoną Internet, NuGet.exe binary będą znajdować się w jednym z dwóch folderów:</span><span class="sxs-lookup"><span data-stu-id="938e1-126">After bootstrapping the Internet connected machine, the NuGet.exe binary will be located in one of two folders:</span></span>

<span data-ttu-id="938e1-127">Jeśli `Publish-Module` lub `Publish-Script` polecenia cmdlet zostały wykonane z podwyższonym poziomem uprawnień (dla administratora):</span><span class="sxs-lookup"><span data-stu-id="938e1-127">If the `Publish-Module` or `Publish-Script` cmdlets were executed with elevated permissions (As an Administrator):</span></span>

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="938e1-128">Jeśli polecenia cmdlet zostały wykonane jako użytkownik bez uprawnień z podwyższonym poziomem uprawnień:</span><span class="sxs-lookup"><span data-stu-id="938e1-128">If the cmdlets were executed as a user without elevated permissions:</span></span>

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

<span data-ttu-id="938e1-129">Drugą opcją jest pobranie NuGet.exe w witrynie NuGet.Org: [ https://dist.nuget.org/index.html ](https://www.nuget.org/downloads) po wybraniu wersji NugGet dla maszyn w środowisku produkcyjnym, upewnij się, że jest późniejsza niż 2.8.5.208 i identyfikowania wersji, które zostały oznaczone " Zaleca się".</span><span class="sxs-lookup"><span data-stu-id="938e1-129">A second option is to download NuGet.exe from the NuGet.Org website: [https://dist.nuget.org/index.html](https://www.nuget.org/downloads) When selecting a NugGet version for production machines, make sure it is later than 2.8.5.208, and identify the version that has been labeled "recommended".</span></span>
<span data-ttu-id="938e1-130">Pamiętaj, aby odblokować plik, jeśli został on pobrany przy użyciu przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="938e1-130">Remember to unblock the file if it was downloaded using a browser.</span></span>
<span data-ttu-id="938e1-131">Można to wykonać za pomocą `Unblock-File` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="938e1-131">This can be performed by using the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="938e1-132">W obu przypadkach można skopiować do dowolnej lokalizacji w pliku NuGet.exe `$env:path`, ale standardowe lokalizacje:</span><span class="sxs-lookup"><span data-stu-id="938e1-132">In either case, the NuGet.exe file can be copied to any location in `$env:path`, but the standard locations are:</span></span>

<span data-ttu-id="938e1-133">Aby udostępnić plik wykonywalny, tak aby wszyscy użytkownicy mogą używać `Publish-Module` i `Publish-Script` poleceń cmdlet:</span><span class="sxs-lookup"><span data-stu-id="938e1-133">To make the executable available so that all users can use `Publish-Module` and `Publish-Script` cmdlets:</span></span>

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="938e1-134">Aby udostępnić plik wykonywalny dla określonego użytkownika, skopiuj do lokalizacji, w ramach tylko ten użytkownik profilu:</span><span class="sxs-lookup"><span data-stu-id="938e1-134">To make the executable available to only a specific user, copy to the location within only that user's profile:</span></span>

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```