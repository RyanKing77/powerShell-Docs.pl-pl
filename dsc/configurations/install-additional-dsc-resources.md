---
ms.date: 12/12/2018
keywords: DSC, powershell, zasób, galerii, Instalator
title: Zainstaluj DSC dodatkowe zasoby
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405215"
---
# <a name="install-additional-dsc-resources"></a>Zainstaluj DSC dodatkowe zasoby

Program PowerShell zawiera kilka zasobów poza pole dla Desired State Configuration (DSC). **PSDesiredStateConfiguration** moduł zawiera wszystkie zasoby DSC OOB dostępne w ramach określonego wystąpienia programu PowerShell.

Jest to lista zasobów OOB zawartych w programie PowerShell 4.0 i opis możliwości w zakresie zasobów.

> [!NOTE]
> To jest niekompletny, jak wiele zasobów OOB, która wzrosła z każdą wersją programu PowerShell.

|Zasób  |Opis  |
|---------|---------|
|**Plik**|Steruje stanem plików i katalogów. Kopiuje pliki z **źródła** do **docelowy** i aktualizuje je, gdy **źródła** zmiany wprowadzane przez porównywanie dat, sumy kontrolne i skróty.|
|**Archiwum**|Wypakowuje archiwa i określonej lokalizacji. Waliduje archiwach z określonym **sumy kontrolnej**.|
|**Środowisko**|Zarządza zmiennych środowiskowych.|
|**Grupa**|Zarządza grupami lokalnymi i kontroluje członkostwo w grupie.|
|**Dziennik**|Zapisuje komunikaty `Microsoft-Windows-Desired State Configuration/Analytic` dziennika zdarzeń.|
|**Pakiet**|Instaluje lub odinstalowuje pakietów przy użyciu **argumenty**, **LogPath**, **ReturnCode**, inne ustawienia.|
|**Registry**|Umożliwia zarządzanie kluczami i wartościami rejestru.|
|**Skrypt**|Pozwala Ci projektować własne [get-test-set](../resources/get-test-set.md) bloki skryptów.|
|**Usługa**|Konfiguruje usługi Windows.|
|**Użytkownik** |Zarządza lokalnych użytkowników i atrybuty.|
|**WindowsFeature**|Zarządza rolami i funkcjami.|
|**WindowsProcess**|Konfiguruje Windows procesów.|

Zasoby OOB umożliwiają dobry punkt wyjścia dla typowych operacji. Jeśli zasoby OOB nie odpowiada Twoim potrzebom, możesz napisać własne [zasób dostosowany](../resources/authoringResource.md). Przed przystąpieniem do napisania zasobów niestandardowych, aby pomóc w rozwiązaniu problemu powinien wyglądać za pośrednictwem ogromną liczbę zasobów DSC, które zostały już utworzone przez firmę Microsoft i społeczność programu PowerShell.

Zasoby DSC można znaleźć w obu [galerii programu PowerShell](https://www.powershellgallery.com/) i [GitHub](https://github.com/). Zasoby DSC można także zainstalować bezpośrednio z poziomu przy użyciu konsoli programu PowerShell [PowerShellGet](/powershell/module/powershellget/).

## <a name="installing-powershellget"></a>Instalowanie menedżera pakietów PowerShellGet

Aby ustalić, czy masz już **PowerShell** uzyskać lub Aby uzyskać pomoc dotyczącą instalowania go, zapoznaj się z następującymi wskazówkami: [Instalowanie modułu PowerShellGet](/powershell/gallery/installing-psget).

## <a name="finding-dsc-resources-using-powershellget"></a>Znajdowanie zasobów DSC przy użyciu funkcji PowerShellGet

Gdy **PowerShellGet** jest zainstalowany w systemie, można znaleźć i zainstalować zasoby DSC hostowane w [galerii programu PowerShell](https://www.powershellgallery.com/).

Najpierw za pomocą [Znajdź-DSCResource](/powershell/module/powershellget/find-dscresource) polecenia cmdlet, aby znaleźć zasoby DSC. Po uruchomieniu `Find-DSCResource` po raz pierwszy, zobaczysz następujący monit, aby zainstalować dostawcę"NuGet".

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

Po naciskając klawisz "y" "NuGet" dostawca jest zainstalowany, pojawi się lista zasobów DSC, które można zainstalować z galerii programu PowerShell.

> [!NOTE]
> Lista nie jest wyświetlany, ponieważ jest bardzo duża.

Można również określić `-Name` przy użyciu symboli wieloznacznych, parametr lub `-Filter` parametru bez symboli wieloznacznych, aby zawęzić kryteria wyszukiwania. W tym przykładzie próbuje znaleźć zasobu "Strefa czasowa" DSC przy użyciu symboli wieloznacznych.

> [!IMPORTANT]
> Obecnie ma błędów w `Find-DSCResource` polecenia cmdlet, który uniemożliwia przy użyciu symboli wieloznacznych w obu `-Name` i `-Filter` parametrów. Drugi przykład poniżej przedstawiono obejście przy użyciu `Where-Object`.

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

Można również użyć `Where-Object` znajdowanie zasobów DSC przy użyciu bardziej szczegółowego filtrowania. Ta metoda będzie przebiegać wolniej niż wbudowane filtrowanie parametrów.

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

Aby uzyskać więcej informacji na temat filtrowania, zobacz [Where-Object](/powershell/module/microsoft.powershell.core/where-object).

## <a name="installing-dsc-resources-using-powershellget"></a>Instalowanie zasobów DSC przy użyciu funkcji PowerShellGet

Aby zainstalować zasobów DSC, użyj [Install-Module](/powershell/module/PowershellGet/Install-Module) polecenia cmdlet, określając nazwę modułu, wyświetlany w obszarze **modułu** nazwy w wynikach wyszukiwania.

"Strefa czasowa" istnieje zasób w module "ComputerManagementDSC", więc to znaczy instaluje w tym przykładzie moduł.

> [!NOTE]
> Jeśli nie ma zaufany galerii programu PowerShell, zostanie wyświetlone ostrzeżenie poniżej monitowania o potwierdzenie i pokazanie, jak unikać kolejnych monitów instaluje.

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Naciśnij klawisz t, aby kontynuować instalację modułu. Po instalacji, możesz sprawdzić, czy nowy zasób jest instalowana za pomocą [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).

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

Inne zasoby można również wyświetlić w nowo zainstalowanym module, określając `-ModuleName` parametru.

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

## <a name="see-also"></a>Zobacz też

- [Co to są zasoby?](../resources/resources.md)
