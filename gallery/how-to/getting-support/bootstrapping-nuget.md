---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeria, programu powershell, polecenie cmdlet, psget
title: Uruchamianie NuGet
ms.openlocfilehash: 2d321097fda201c0d8f843b2194a161eceabe4e1
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094021"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a>Uruchomienie dostawcy NuGet i NuGet.exe

NuGet.exe nie są objęte najnowszego dostawcę NuGet.
Do publikowania w operacji modułu lub skryptu, modułu PowerShellGet wymaga binarne NuGet.exe pliku wykonywalnego.
Dostawcy NuGet jest wymagany tylko dla wszystkich innych operacji, w tym *znaleźć*, *zainstalować*, *Zapisz*, i *odinstalować*.
Moduł PowerShellGet zawiera logikę obsługującą albo połączone bootstrap dostawcy NuGet i NuGet.exe lub bootstrap dostawcę NuGet.
W obu przypadkach powinien wystąpić tylko pojedynczą wiadomość szybkiego.
Jeśli komputer nie jest połączony z Internetem, użytkownik lub administrator należy skopiować zaufanych wystąpienie dostawcy NuGet i/lub pliku NuGet.exe maszyny bez połączenia.

> [!NOTE]
> Począwszy od wersji 6 dostawcy NuGet znajduje się w instalacji programu PowerShell. [http://github.com/powershell/powershell](http://github.com/powershell/powershell)

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a>Rozwiązywanie błędów podczas dostawcy NuGet nie został zainstalowany na komputerze, na którym jest Internet połączone

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

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Rozwiązywanie błędów podczas dostawcy NuGet jest dostępny i NuGet.exe jest niedostępne podczas operacji publikowania na komputerze, na którym jest Internet połączone

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

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Rozwiązywanie błędów podczas dostawcy NuGet i NuGet.exe nie są dostępne podczas operacji publikowania na komputerze, na którym jest Internet połączone

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

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a>Ręczne uruchamianie dostawcy NuGet na komputerze, który nie jest połączony z Internetem

Procesy pokazano powyżej przyjęto założenie, komputer jest połączony z Internetem i mogą pobierać pliki z lokalizacji publicznej.
Jeśli nie jest to możliwe, jedyną opcją jest uruchamiania na maszynie za pomocą procesów podanej powyżej, a następnie ręcznie skopiuj dostawcę z izolowanym węzłem proces zaufanego w trybie offline.
Najbardziej typowy przypadek użycia, w tym scenariuszu to ona prywatną galerię do obsługi środowiska izolowanego.

Po wykonaniu powyższych uruchomienie maszynę połączoną z Internetem, pliki dostawcy znajduje się w lokalizacji:

```
C:\Program Files\PackageManagement\ProviderAssemblies\
```

Struktura folderów i plików dostawcy NuGet będzie (także z liczbą innej wersji):

```
NuGet
--2.8.5.208
----Microsoft.PackageManagement.NuGetProvider.dll
```

Skopiuj te foldery i plik przy użyciu zaufanego proces maszyny w trybie offline.

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a>Ręczne uruchamianie NuGet.exe pozwalające obsługiwać publikowanie operacji na komputerze, na którym nie jest połączony z Internetem

Oprócz procesu ręczne uruchomienie dostawcy NuGet, jeśli maszyna będzie używana do publikowania modułów i skryptów za pomocą galerii prywatnej `Publish-Module` lub `Publish-Script` poleceń cmdlet programu NuGet.exe binarny plik wykonywalny będzie wymagane.

Najbardziej typowy przypadek użycia, w tym scenariuszu to ona prywatną galerię do obsługi środowiska izolowanego.
Istnieją dwa sposoby uzyskania pliku NuGet.exe.

Jedną z opcji jest uruchomienie na komputerze, na którym jest połączonych z Internetem, a następnie skopiuj pliki do przy użyciu zaufanym procesie maszyny w trybie offline.
Po uruchamianie maszynę połączoną Internet, NuGet.exe binary będą znajdować się w jednym z dwóch folderów:

Jeśli `Publish-Module` lub `Publish-Script` polecenia cmdlet zostały wykonane z podwyższonym poziomem uprawnień (dla administratora):

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Jeśli polecenia cmdlet zostały wykonane jako użytkownik bez uprawnień z podwyższonym poziomem uprawnień:

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

Drugą opcją jest pobranie NuGet.exe w witrynie NuGet.Org: [ https://dist.nuget.org/index.html ](https://www.nuget.org/downloads) po wybraniu wersji NugGet dla maszyn w środowisku produkcyjnym, upewnij się, że jest późniejsza niż 2.8.5.208 i identyfikowania wersji, które zostały oznaczone " Zaleca się".
Pamiętaj, aby odblokować plik, jeśli został on pobrany przy użyciu przeglądarki.
Można to wykonać za pomocą `Unblock-File` polecenia cmdlet.

W obu przypadkach można skopiować do dowolnej lokalizacji w pliku NuGet.exe `$env:path`, ale standardowe lokalizacje:

Aby udostępnić plik wykonywalny, tak aby wszyscy użytkownicy mogą używać `Publish-Module` i `Publish-Script` poleceń cmdlet:

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Aby udostępnić plik wykonywalny dla określonego użytkownika, skopiuj do lokalizacji, w ramach tylko ten użytkownik profilu:

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```