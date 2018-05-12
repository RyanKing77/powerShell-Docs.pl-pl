
---
MS.Date: współautora 2017-06/12: manikb ms.topic: odwołanie słów kluczowych: galerii, programu powershell, polecenia cmdlet, tytuł psget: uruchamianie NuGet
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a>Bootstrap dostawcy NuGet i NuGet.exe

NuGet.exe nie jest uwzględniony w najnowszą wersję dostawcy NuGet.
W przypadku opublikować operacje modułu lub skryptu, PowerShellGet wymaga binarne NuGet.exe pliku wykonywalnego.
Dostawca NuGet jest wymagany tylko dla wszystkich innych operacji, w tym *znaleźć*, *zainstalować*, *zapisać*, i *odinstalować*.
PowerShellGet zawiera logikę do obsługi albo Scalonej bootstrap dostawcy NuGet i NuGet.exe lub bootstrap dostawcę NuGet.
W obu przypadkach powinien wystąpić tylko monitu o pojedynczym komunikacie.
Jeśli komputer nie jest połączony z Internetem, użytkownik lub administrator musi skopiować zaufanych wystąpienie dostawcy programu NuGet i/lub pliku NuGet.exe do odłączonego maszyny.

>**Uwaga**: począwszy od wersji 6, dostawca NuGet jest dostępny w instalacji programu PowerShell. [http://github.com/powershell/powershell](http://github.com/powershell/powershell)

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a>Rozpoznawanie błąd, gdy dostawca NuGet nie został zainstalowany na komputerze, na którym jest Internet połączone

```powershell
PS> Find-Module -Repository PSGallery -Verbose -Name Contoso

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

PS> Find-Module -Repository PSGallery -Verbose -Name Contoso

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

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Rozwiązywanie błędów po udostępnieniu dostawcy NuGet i NuGet.exe jest niedostępne podczas operacji publikowania na komputerze, na którym jest Internet połączone

```powershell
PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module

PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Rozwiązywanie błędów podczas zarówno dostawcy NuGet i NuGet.exe nie są dostępne podczas operacji publikowania na komputerze, na którym jest Internet połączone

```powershell
PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

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

PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a>Ręczne uruchamianie dostawcy NuGet, na komputerze, na którym nie jest połączony z Internetem

Procesy przedstawionej powyżej założono komputer jest połączony z Internetem i pobrać plików z lokalizacji publicznej.
Jeśli nie jest to możliwe, jedyną opcją jest bootstrap maszynie przy użyciu procesów powyższych i ręcznie skopiować dostawcy do izolowanego węzła za pośrednictwem procesu zaufane w trybie offline.
Najbardziej typowe przypadek użycia dla tego scenariusza jest po do obsługi izolowanym środowisku prywatnej galerii.

Po wykonaniu procesu powyżej, aby zainicjować maszyny podłączonej do Internetu, można znaleźć dostawcy plików w lokalizacji:

```
C:\Program Files\PackageManagement\ProviderAssemblies\
```

Struktura folderów i plików dostawcy NuGet będzie (prawdopodobnie z numerem wersji o różnych):

NuGet<br>
--2.8.5.208<br>
---Microsoft.PackageManagement.NuGetProvider.dll

Skopiuj te foldery i plik przy użyciu zaufanego procesu na komputerach w trybie offline.

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a>Ręczne uruchamianie NuGet.exe do obsługi publikowania operacji na komputerze, na którym nie jest połączony z Internetem

Oprócz proces ręcznie bootstrap dostawcę programu NuGet, jeśli komputer będzie używany do publikowania modułów lub skrypty w galerii prywatnej przy użyciu *modułu publikowania* lub *skryptu publikowania* poleceń cmdlet programu plik wykonywalny binarne NuGet.exe będzie wymagane.
Najbardziej typowe przypadek użycia dla tego scenariusza jest po do obsługi izolowanym środowisku prywatnej galerii.
Dostępne są dwie opcje, aby uzyskać plik NuGet.exe.

Jedną z opcji jest bootstrap na komputerze, który jest połączonych z Internetem i skopiuj pliki do maszyn w trybie offline przy użyciu zaufanego procesu.
Po uruchamianie maszyny połączenia internetowego, NuGet.exe binary będą znajdować się w jednym z dwóch folderów:

Jeśli *modułu publikowania* lub *skryptu publikowania* poleceń cmdlet zostały wykonane z podwyższonym poziomem uprawnień (jako Administrator):

```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Jeśli polecenia cmdlet zostały wykonane jako użytkownik bez uprawnień z podwyższonym poziomem uprawnień:

```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

Drugą opcją jest do pobrania z witryny sieci Web NuGet.Org NuGet.exe: [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html)<br>
Po wybraniu wersji NugGet dla maszyn w środowisku produkcyjnym, upewnij się, że jest nowszy niż 2.8.5.208 i identyfikowania wersji, który został oznaczony "zalecane".
Pamiętaj, aby odblokować plik, jeśli został on pobrany przy użyciu przeglądarki.
Można to wykonać przy użyciu *odblokowanie pliku* polecenia cmdlet.

W obu przypadkach można skopiować pliku NuGet.exe w dowolne miejsce w *$env: ścieżka*, ale są standardowe lokalizacje:

Aby udostępnić plik wykonywalny, aby wszyscy użytkownicy mogli używać *modułu publikowania* i *skryptu publikowania* poleceń cmdlet:

```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Aby udostępnić plik wykonywalny dla określonego użytkownika, skopiuj do lokalizacji w ramach tylko profil użytkownika:

```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```