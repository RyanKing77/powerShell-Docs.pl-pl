---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasoby DSC
ms.openlocfilehash: 542a210ab47c650eac625108a78e76bc2cd55572
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404814"
---
# <a name="dsc-resources"></a>Zasoby DSC

>Dotyczy: Program Windows PowerShell 4.0, Windows PowerShell 5.0

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

![Uzupełnianie kartę zasobów](/media/resource-tabcompletion.png)
