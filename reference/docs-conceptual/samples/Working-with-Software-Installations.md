---
ms.date: 06/03/2019
keywords: polecenia cmdlet programu PowerShell
title: Praca z instalacjami oprogramowania
ms.openlocfilehash: 6d2111a332f0e8c1b545186d3d950e936aed1834
ms.sourcegitcommit: 4ec9e10647b752cc62b1eabb897ada3dc03c93eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830300"
---
# <a name="working-with-software-installations"></a>Praca z instalacjami oprogramowania

Aplikacje, które są przeznaczone do przy użyciu Instalatora Windows jest możliwy za pośrednictwem usługi WMI **klasy Win32_Product** klasy, ale nie wszystkie aplikacje używane obecnie za pomocą Instalatora Windows.
Zazwyczaj aplikacje korzystające z Instalatora alternatywnego procedury nie są zarządzane przez Instalatora Windows.
Określone techniki pracy z tymi aplikacjami zależy od tego, Instalator oprogramowania i decyzje podjęte przez dewelopera aplikacji. Na przykład aplikacje zainstalowane przez kopiowanie plików do folderu na komputerze, zwykle nie można zarządzać za pomocą techniki opisane poniżej. Można zarządzać te aplikacje jako plików i folderów za pomocą procedur omówionych w [Praca z plikami i folderami](Working-with-Files-and-Folders.md).

> [!CAUTION]
> **Klasy Win32_Product** klasa nie jest zoptymalizowany pod kątem zapytań. Zapytań, które używają filtrów symboli wieloznacznych spowodować WMI w celu użycia dostawcy tożsamości usługi Zarządzanej wyliczyć wszystkich zainstalowanych produktów, a następnie przeanalizować pełną listę po kolei, aby obsłużyć filtru. To również inicjuje Sprawdzanie spójności tego pakietów zainstalowanych, weryfikowanie i naprawić instalację. Sprawdzanie poprawności jest procesem powolnym i może powodować błędy w dziennikach zdarzeń. Aby uzyskać więcej informacji, wyszukaj [artykuł bazy wiedzy 974524](https://support.microsoft.com/help/974524).

## <a name="listing-windows-installer-applications"></a>Wyświetlanie listy aplikacji Instalatora Windows

Aby wyświetlić listę aplikacji, instalowane przy użyciu Instalatora Windows w systemie lokalnym lub zdalnym, użyj następującego prostego zapytania usługi WMI:

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)"
```

```Output
Name               Caption                     Vendor                 Version      IdentifyingNumber
----               -------                     ------                 -------      -----------------
Microsoft .NET ... Microsoft .NET Core Runt... Microsoft Corporation  16.72.26629  {ACC73072-9AD5-416C-94B...
```

Aby wyświetlić wszystkie właściwości **klasy Win32_Product** obiektu do wyświetlenia, użyj **właściwości** parametru formatowania poleceń cmdlet, takich jak `Format-List` polecenia cmdlet, o wartości `*` (wszystkie).

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)" |
    Format-List -Property *
```

```Output
Name                  : Microsoft .NET Core Runtime - 2.1.2 (x64)
Version               : 16.72.26629
InstallState          : 5
Caption               : Microsoft .NET Core Runtime - 2.1.2 (x64)
Description           : Microsoft .NET Core Runtime - 2.1.2 (x64)
IdentifyingNumber     : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
SKUNumber             :
Vendor                : Microsoft Corporation
AssignmentType        : 1
HelpLink              :
HelpTelephone         :
InstallDate           : 20180816
InstallDate2          :
InstallLocation       :
InstallSource         : C:\ProgramData\Package Cache\{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}v16.72.26629\
Language              : 1033
LocalPackage          : C:\WINDOWS\Installer\414c96e.msi
PackageCache          : C:\WINDOWS\Installer\414c96e.msi
PackageCode           : {D20AC783-1EC5-4A58-9277-F452F5EB9AD9}
PackageName           : dotnet-runtime-2.1.2-win-x64.msi
ProductID             :
RegCompany            :
RegOwner              :
Transforms            :
URLInfoAbout          :
URLUpdateInfo         :
WordCount             : 0
PSComputerName        :
CimClass              : root/cimv2:Win32_Product
CimInstanceProperties : {Caption, Description, IdentifyingNumber, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

Alternatywnie można użyć `Get-CimInstance` **filtru** parametru, aby wybrać tylko Microsoft .NET Framework 2.0. Wartość **filtru** parametr używa składni języka zapytań usługi WMI (WQL), nie składni programu Windows PowerShell. Przykład:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property *
```

Aby wyświetlić listę właściwości, które Cię interesują, należy użyć **właściwość** parametru formatowania poleceń cmdlet, aby wyświetlić listę odpowiednich właściwości.

```powershell
Get-CimInstance -Class Win32_Product  -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
```

```Output
Name              : Microsoft .NET Core Runtime - 2.1.2 (x64)
InstallDate       : 20180816
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\414c96e.msi
Vendor            : Microsoft Corporation
Version           : 16.72.26629
IdentifyingNumber : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
```

## <a name="listing-all-uninstallable-applications"></a>Wyświetlanie listy wszystkich do odinstalowania aplikacji

Większość standardowych aplikacji zarejestrować dezinstalatora za pomocą Windows, firma Microsoft może pracować z tymi znajdując je lokalnie w rejestrze systemu Windows. Nie ma gwarancji możliwości można znaleźć każdej aplikacji w systemie. Jednak istnieje możliwość znaleźć wszystkie programy, w których wyświetlane na listach zawartości **apletu Dodaj lub usuń programy**. **Dodaj lub usuń programy** znajdzie te aplikacje w następującym kluczu rejestru:

`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.

Firma Microsoft, można sprawdzić ten klucz, aby znaleźć aplikacje. Aby ułatwić wyświetlanie klucza Odinstaluj, firma Microsoft mapowania dysku środowiska PowerShell do tej lokalizacji rejestru:

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```
W efekcie powstał dysk o nazwie "Odinstaluj:" można szybko i wygodnie poszukaj instalacje aplikacji. Możemy znaleźć liczba aplikacji zainstalowanych przez liczenie klucze rejestru w dezinstalacji: Dysk programu PowerShell:

```
(Get-ChildItem -Path Uninstall:).Count
459
```

Firma Microsoft można wyszukiwać tej listy dalsze aplikacji za pomocą różnych technik, począwszy od **Get-ChildItem**. Aby uzyskać listę aplikacji i zapisywać je w **$UninstallableApplications** zmiennej, użyj następującego polecenia:

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

Aby wyświetlić wartości wpisów rejestru w kluczach rejestru w ramach odinstalowywania, należy użyć metody GetValue kluczy rejestru. Wartość metody jest nazwę wpisu rejestru.

Na przykład można znaleźć nazwy wyświetlane aplikacje w kluczu dezinstalacji, należy użyć następującego polecenia:

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

Nie ma żadnej gwarancji, że te wartości są unikatowe. W poniższym przykładzie dwa elementy zainstalowane są wyświetlane jako "Windows Media Encoder Seria 9":

```powershell
$UninstallableApplications | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}
```

```Output
Name                           Property
----                           --------
{ACC73072-9AD5-416C-94BF-D82DD AuthorizedCDFPrefix :
CEA0F1B}                       Comments            :
                               Contact             :
                               DisplayVersion      : 16.72.26629
                               HelpLink            :
                               HelpTelephone       :
                               InstallDate         : 20180816
                               InstallLocation     :
                               InstallSource       : C:\ProgramData\Package
                               Cache\{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}v16.72.26629\
                               ModifyPath          : MsiExec.exe /X{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
                               NoModify            : 1
                               Publisher           : Microsoft Corporation
                               Readme              :
                               Size                :
                               EstimatedSize       : 67156
                               SystemComponent     : 1
                               UninstallString     : MsiExec.exe /X{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
                               URLInfoAbout        :
                               URLUpdateInfo       :
                               VersionMajor        : 16
                               VersionMinor        : 72
                               WindowsInstaller    : 1
                               Version             : 273180677
                               Language            : 1033
                               DisplayName         : Microsoft .NET Core Runtime - 2.1.2 (x64)
```

## <a name="installing-applications"></a>Instalowanie aplikacji

Możesz użyć **klasy Win32_Product** klasy w celu zainstalowania pakietów Instalatora Windows, lokalnie i zdalnie.

> [!NOTE]
> Aby zainstalować aplikację, należy uruchomić program PowerShell przy użyciu opcji "Uruchom jako administrator".

Podczas instalowania zdalnie, należy użyć ścieżkę sieciową Universal Naming Convention (UNC) do określenia ścieżki do pakietu msi, ponieważ w podsystemie WMI nie rozpoznaje ścieżki programu PowerShell. Na przykład, aby zainstalować pakiet NewPackage.msi znajduje się w udziale sieciowym `\\AppServ\dsp` na komputerze zdalnym PC01, wpisz następujące polecenie w wierszu polecenia programu PowerShell:

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

Aplikacje, które nie korzystają z technologii Instalatora Windows może mieć metody specyficzne dla aplikacji dla automatycznego wdrażania. Zapoznaj się z dokumentacją dla aplikacji lub zapoznaj się z dostawcą aplikacji, system pomocy technicznej.

## <a name="removing-applications"></a>Usuwanie aplikacji

Usuwanie pakietu Instalatora Windows, przy użyciu programu PowerShell działa w przybliżeniu taki sam sposób jak instalowania pakietu. Oto przykład, który wybiera pakiet do odinstalowania, na podstawie jego nazwy; w niektórych przypadkach może być łatwiej filtrować za pomocą **Numer_identyfikacyjny**:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

Usunięcie innych aplikacji nie jest to jednak takie proste, nawet wtedy, gdy jest wykonywane lokalnie. Znaleziono ciągi dezinstalacji wiersza polecenia dla tych aplikacji, dzięki możliwości wyodrębniania **UninstallString** właściwości.
Ta metoda działa w dla aplikacji Instalatora Windows i starszych programów znajdujących się w kluczu dezinstalacji:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Dane wyjściowe można filtrować według nazwy wyświetlanej, jeśli chcesz:

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Jednak te ciągi mogą nie być bezpośrednio można używać z wiersz polecenia programu PowerShell bez modyfikacji niektórych.

## <a name="upgrading-windows-installer-applications"></a>Uaktualnianie aplikacji Instalatora Windows

Aby uaktualnić aplikację, musisz znać nazwę aplikacji i ścieżkę do pakietu uaktualnienia aplikacji. Dzięki tym informacjom można uaktualnić aplikacji za pomocą jednego polecenia programu PowerShell:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
