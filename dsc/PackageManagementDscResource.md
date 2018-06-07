---
ms.date: 06/20/2018
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób PackageManagement DSC
ms.openlocfilehash: 3d52934b130d59acee4d7f8a92da2c743c1eb305
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753791"
---
# <a name="dsc-packagemanagement-resource"></a>Zasób PackageManagement DSC

> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0, środowiska Windows PowerShell w wersji 5.1

**PackageManagement** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm umożliwiający instalowanie lub odinstalowywanie pakiety zarządzania pakietami w docelowym węźle. Ten zasób wymaga **PackageManagement** modułu, dostępne z http://PowerShellGallery.com.

> [!IMPORTANT]
> **PackageManagement** modułu powinna wynosić co najmniej wersji 1.1.7.0 następujących informacji właściwości są prawidłowe.

## <a name="syntax"></a>Składnia

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [AdditionalParameters = [HashTable]]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [MaximumVersion = [string]]
    [MinimumVersion = [string]]
    [ProviderName = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [RequiredVersion = [string]]
    [Source = [string]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a>Właściwości

|  Właściwość  |  Opis   |
|---|---|
| Nazwa| Określa nazwę pakietu do zainstalowania lub odinstalowania.|
| AdditionalParameters| Dostawca hashtable określonych parametrów, które zostaną przekazane do `Get-Package -AdditionalArguments`. Na przykład dla dostawcy NuGet można przekazać dodatkowe parametry, takie jak Ścieżka_docelowa.|
| Upewnij się| Określa, czy pakiet jest zainstalowany lub odinstalowany.|
| MaximumVersion|Określa maksymalny dozwolony wersji pakietu, który ma zostać znaleziona. Jeśli ten parametr nie zostanie dodany, zasób znajduje najwyższy dostępna wersja pakietu.|
| MinimumVersion|Określa minimalną dozwoloną wersji pakietu, który ma zostać znaleziona. Jeśli ten parametr nie zostanie dodany, zasobu znajdzie najwyższy dostępna wersja pakietu, który spełnia również maksymalna wersja określona określony przez _MaximumVersion_ parametru.|
| ProviderName| Określa nazwę dostawcy pakietów, do którego należy określić zakres wyszukiwania pakietu. Nazwy dostawców pakietu można uzyskać, uruchamiając `Get-PackageProvider` polecenia cmdlet.|
| RequiredVersion| Określa dokładną wersję pakietu, który chcesz zainstalować. Jeśli nie określisz ten parametr, ten zasób DSC instaluje najnowszą wersję dostępny pakiet, który również spełnia wszelkie maksymalna wersja określona przez _MaximumVersion_ parametru.|
| Źródło| Określa nazwę źródła pakietów, gdzie można znaleźć pakietu. Może to być identyfikator URI lub źródło zarejestrowany w usłudze `Register-PackageSource` lub zasobu PackageManagementSource DSC.|
| SourceCredential | Określa konto użytkownika, które ma uprawnienia do zainstalowania pakietu dla określonego pakietu dostawcę lub źródło.|

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
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2/"
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