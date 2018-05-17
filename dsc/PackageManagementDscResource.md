---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób PackageManagement DSC
ms.openlocfilehash: f850c389214fe5adf139c3bd01fb60addc5ec238
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-packagemanagement-resource"></a>Zasób PackageManagement DSC

> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

**PackageManagement** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm umożliwiający instalowanie lub odinstalowywanie pakiety zarządzania pakietami w docelowym węźle. Ten zasób wymaga **PackageManagement** modułu, dostępne z http://PowerShellGallery.com.

## <a name="syntax"></a>Składnia

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ Source = [string] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ RequiredVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ MaximumVersion = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ ProviderName = [string] ]
    [ AdditionalParameters = [Microsoft.Management.Infrastructure.CimInstance[]] ]
}
```

## <a name="properties"></a>Właściwości
|  Właściwość  |  Opis   |
|---|---|
| Nazwa| Określa nazwę pakietu do zainstalowania lub odinstalowania.|
| Źródło| Określa nazwę źródła pakietów, gdzie można znaleźć pakietu. Może to być identyfikator URI lub źródło zarejestrowany w usłudze PackageSource rejestru lub PackageManagementSource DSC zasobu. Zasób DSC MSFT_PackageManagementSource można również zarejestrować źródła pakietu.|
| Upewnij się| Określa, czy pakiet jest zainstalowany lub odinstalowany.|
| RequiredVersion| Określa dokładną wersję pakietu, który chcesz zainstalować. Jeśli nie określisz ten parametr, tego zasobu DSC instaluje najnowszą wersję dostępne spełniającego wszystkie maksymalna wersja określona w parametrze MaximumVersion pakietu.|
| MinimumVersion| Określa wersję pakietu, który chcesz zainstalować dozwolony. Jeśli ten parametr to intalls zasobów DSC najwyższy dostępna wersja pakietu, który spełnia również maksymalna wersja określona określonej przez parametr MaximumVersion nie zostaną dodane.|
| MaximumVersion| Określa maksymalny dozwolony wersję pakietu, który chcesz zainstalować. Jeśli nie określisz ten parametr, ten zasób DSC instaluje najwyższym numerze wersji dostępnych pakietu.|
| SourceCredential | Określa konto użytkownika, które ma uprawnienia do zainstalowania pakietu dla określonego pakietu dostawcę lub źródło.|
| ProviderName| Określa nazwę dostawcy pakietów, do którego należy określić zakres wyszukiwania pakietu. Nazwy dostawcy pakietu można uzyskać, uruchamiając polecenie cmdlet Get-PackageProvider.|
| AdditionalParameters| Dostawca określonych parametrów, które są przekazywane jako tablica skrótów. Na przykład dla dostawcy NuGet można przekazać dodatkowe parametry, takie jak Ścieżka_docelowa.|

## <a name="additional-parameters"></a>Dodatkowe parametry
W poniższej tabeli wymieniono opcje dla właściwości AdditionalParameters.
|  Parametr  | Opis   |
|---|---|
| Ścieżka_docelowa| Używane przez dostawców, takich jak wbudowanego dostawcy Nuget. Określa lokalizację plików miejscu pakietu do zainstalowania.|
| InstallationPolicy| Używane przez dostawców, takich jak wbudowanego dostawcy Nuget. Określa, czy ufasz źródłu tego pakietu. Jeden z: "Niezaufanych", "Zaufanym".|

## <a name="example"></a>Przykład

Instalacja **JQuery** pakietu NuGet i **GistProvider** przy użyciu modułu PowerShell **PackageManagement** zasobów usługi Konfiguracja DSC. W tym przykładzie najpierw zapewnia źródeł wymaganego pakietu są dostępne, a następnie definiuje oczekiwany stan **JQuery** i **GistProvider** pakietów (NuGet i programu PowerShell, odpowiednio).

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceUri   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceUri   = "https://www.powershellgallery.com/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagement NugetPackage
    {
        Ensure               = "Present"
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1"
        DependsOn            = "[PackageManagementSource]SourceRepository"
    }

    PackageManagement PSModule
    {
        Ensure               = "Present"
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery"
    }
}
```