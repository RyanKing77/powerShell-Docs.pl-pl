---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasoby DSC
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686068"
---
# <a name="dsc-resources"></a>Zasoby DSC

>Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0

Desired State Configuration, że zasoby (DSC) zawierają bloki konstrukcyjne konfiguracji DSC. Zasób udostępnia właściwości, które mogą być skonfigurowane (schemat) i zawiera funkcje skrypt programu PowerShell, które lokalne Configuration Manager (LCM) wywołuje być "tak".

Zasób można modelować coś ogólnego jako plik lub jako określone w ustawieniach serwera usług IIS.  Grupy takich jak zasoby są łączone w modułu DSC, która organizuje wszystkie wymagane pliki w do struktury, która jest przenośny i obejmuje metadane, aby zidentyfikować, jak zasoby są przeznaczone do użycia.

Każdy zasób ma * schemat, który określa składni potrzebnych do korzystania z zasobów w [konfiguracji](../configurations/configurations.md). Schemat zasobu można zdefiniować w następujący sposób:

- **"Schema.Mof"** pliku: Zdefiniuj większość zasobów ich *schematu* w schema.mof plików, przy użyciu [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).
- **"\<Nazwa zasobu\>. schema.psm1"** pliku: [Zasoby złożone](../configurations/compositeConfigs.md) definiowanie ich *schematu* w "<ResourceName>. schema.psm1" plik za pomocą [blok parametrów](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).
- **"\<Nazwa zasobu\>psm1"** pliku: Klasy oparte na zasoby DSC zdefiniować ich *schematu* w definicji klasy. Elementy składni są wskazywane jako właściwości klasy. Aby uzyskać więcej informacji, zobacz [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).

Aby pobrać składnia dla zasobów DSC, użyj [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) polecenia cmdlet z `-Syntax` parametru. To obciążenie jest podobne do [Get-Command](/powershell/module/microsoft.powershell.core/get-command) z `-Syntax` parametru, aby pobrać Składnia poleceń cmdlet. Widoczne dane wyjściowe zostaną wyświetlone z szablonu użytego do bloku zasobu dla zasobu, które określisz.

```powershell
Get-DscResource -Syntax Service
```

Widoczne dane wyjściowe powinny być podobne do danych wyjściowych poniżej, chociaż Składnia tego zasobu można zmienić w przyszłości. Składnia poleceń cmdlet, takich jak *klucze* widać w nawiasach kwadratowych, są opcjonalne. Typy określić rodzaj danych, który oczekuje, że każdy klucz.

> [!NOTE]
> **Upewnij się, że** klucz jest opcjonalny, ponieważ jego wartość domyślna to "Istnieje".

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

W konfiguracji **usługi** blok zasobu może wyglądać jak ten element, aby **upewnij się, że** uruchomioną usługę buforowania.

> [!NOTE]
> Przed rozpoczęciem korzystania z zasobów w ramach konfiguracji należy zaimportować go za pomocą [Import-DSCResource](../configurations/import-dscresource.md).

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

Konfiguracje mogą zawierać wiele wystąpień tego samego typu zasobu. Każde wystąpienie musi mieć jednoznacznie nazwę. W poniższym przykładzie sekundy **usługi** bloku zasobów jest dodawany do skonfigurowania usługi "DHCP".

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
> Począwszy od programu PowerShell w wersji 5.0, dodano intellisense DSC. Ta nowa funkcja umożliwia \<kartę\> i \<Ctrl + spacja\> do automatycznego uzupełniania nazw kluczy.

![Uzupełnianie kartę zasobów](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a>Zasoby wbudowane

Oprócz zasobów społeczności istnieją wbudowane zasoby dla Windows, zasoby dla systemu Linux i zasoby dla zależności między węzłami. Skorzystaj z powyższych kroków, składni tych zasobów i sposobu ich używania. Stron, które pełnią te zasoby zostały zarchiwizowane w obszarze **odwołania**.

Wbudowane zasoby systemu Windows

* [Zasób archiwum](../reference/resources/windows/archiveResource.md)
* [Zasób środowiska](../reference/resources/windows/environmentResource.md)
* [Zasób pliku](../reference/resources/windows/fileResource.md)
* [Zasób grupy](../reference/resources/windows/groupResource.md)
* [Zasób GroupSet](../reference/resources/windows/groupSetResource.md)
* [Zasób dziennika](../reference/resources/windows/logResource.md)
* [Zasób pakietu](../reference/resources/windows/packageResource.md)
* [Zasób ProcessSet](../reference/resources/windows/ProcessSetResource.md)
* [Zasób rejestru](../reference/resources/windows/registryResource.md)
* [Zasób skryptu](../reference/resources/windows/scriptResource.md)
* [Zasób usługi](../reference/resources/windows/serviceResource.md)
* [Zasób ServiceSet](../reference/resources/windows/serviceSetResource.md)
* [Zasób użytkownika](../reference/resources/windows/userResource.md)
* [Zasób WindowsFeature](../reference/resources/windows/windowsFeatureResource.md)
* [Zasób WindowsFeatureSet](../reference/resources/windows/windowsFeatureSetResource.md)
* [Zasób WindowsOptionalFeature](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [Zasób WindowsOptionalFeatureSet](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [WindowsPackageCabResource Resource](../reference/resources/windows/windowsPackageCabResource.md)
* [Zasób WindowsProcess](../reference/resources/windows/windowsProcessResource.md)

[Zależności między węzłami](../configurations/crossNodeDependencies.md) zasobów

* [WaitForAll zasobów](../reference/resources/windows/waitForAllResource.md)
* [WaitForSome zasobów](../reference/resources/windows/waitForSomeResource.md)
* [WaitForAny zasobów](../reference/resources/windows/waitForAnyResource.md)

Pakiet zarządzania zasobami

* [Zasób funkcji PackageManagement](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [PackageManagementSource Resource](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

Zasoby systemu Linux

* [Zasób archiwum systemu Linux](../reference/resources/linux/lnxArchiveResource.md)
* [Zasób środowiska systemu Linux](../reference/resources/linux/lnxEnvironmentResource.md)
* [Zasób FileLine systemu Linux](../reference/resources/linux/lnxFileLineResource.md)
* [Zasób pliku systemu Linux](../reference/resources/linux/lnxFileResource.md)
* [Zasób grupy systemu Linux](../reference/resources/linux/lnxGroupResource.md)
* [Zasób pakietu systemu Linux](../reference/resources/linux/lnxPackageResource.md)
* [Zasób skryptu systemu Linux](../reference/resources/linux/lnxScriptResource.md)
* [Zasób usługi w systemie Linux](../reference/resources/linux/lnxServiceResource.md)
* [Zasób SshAuthorizedKeys systemu Linux](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [Zasób użytkownika w systemie Linux](../reference/resources/linux/lnxUserResource.md)
