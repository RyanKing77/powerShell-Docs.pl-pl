---
ms.date: 06/20/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób PackageManagement DSC
ms.openlocfilehash: 18cbbfe0715c82dcfdf4a5fb6ee36ee814e43d3b
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268096"
---
# <a name="dsc-packagemanagement-resource"></a>Zasób PackageManagement DSC

Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0, programu Windows PowerShell 5.1

**PackageManagement** zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm, aby zainstalować lub odinstalować pakiety zarządzania pakietami na węzeł docelowy. Ten zasób wymaga **PackageManagement** modułu dostępnym [ http://PowerShellGallery.com ](http://PowerShellGallery.com).

> [!IMPORTANT]
> **PackageManagement** moduł powinien wynosić co najmniej wersji 1.1.7.0 podanie następujących informacji właściwość prawdopodobnie jest niepoprawny.

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

| Właściwość | Opis |
| --- | --- |
| Nazwa| Określa nazwę pakietu do zainstalowania lub odinstalowania.|
| AdditionalParameters| Dostawca hashtable określonych parametrów, które zostaną przekazane do `Get-Package -AdditionalArguments`. Na przykład dla dostawcy NuGet można przekazywać dodatkowych parametrów, takich jak Ścieżka_docelowa.|
| Upewnij się| Określa, czy pakiet jest zainstalowane lub odinstalowane.|
| MaximumVersion|Określa maksymalną dozwoloną wersję pakietu, który ma zostać odnaleziona. Jeśli ten parametr nie zostanie dodany, zasób znajduje najwyższej dostępnej wersji pakietu.|
| MinimumVersion|Określa minimalną dozwoloną wersję pakietu, który ma zostać odnaleziona. Jeśli ten parametr nie zostanie dodany, zasób znajdzie najwyższej dostępnej wersji pakietu, który także spełnia wszelkie maksymalnej określonej wersji określonej przez _MaximumVersion_ parametru.|
| ProviderName| Określa nazwę dostawcy pakiet, dla której chcesz ograniczyć wyszukiwanie pakietu. Nazwy dostawcy pakietu można uzyskać, uruchamiając `Get-PackageProvider` polecenia cmdlet.|
| RequiredVersion| Określa dokładną wersję pakietu, który chcesz zainstalować. Jeśli ten parametr nie jest określony, ten zasób DSC instalacji najnowszej dostępnej wersji pakietu, który także spełnia wszelkie maksymalnej wersji określonej przez _MaximumVersion_ parametru.|
| Źródło| Określa nazwę źródła pakietu, gdzie można znaleźć pakietu. Może to być identyfikator URI lub źródłem zarejestrowane w usłudze `Register-PackageSource` lub zasób DSC PackageManagementSource.|
| SourceCredential | Określa konto użytkownika, które ma uprawnienia do zainstalowania pakietu dla dostawcy określonego pakietu lub źródła.|

## <a name="additional-parameters"></a>Dodatkowe parametry

W poniższej tabeli wymieniono opcje dla właściwości AdditionalParameters.

| Parametr | Opis |
| --- | --- |
| Ścieżka_docelowa| Używane przez dostawców, takich jak wbudowanego dostawcy Nuget. Określa lokalizację pliku, którego pakiet do zainstalowania.|
| InstallationPolicy| Używane przez dostawców, takich jak wbudowanego dostawcy Nuget. Określa, czy ufasz źródłu pakietu. Jeden z: `Untrusted`, `Trusted`.|

## <a name="example"></a>Przykład

W tym przykładzie instaluje **JQuery** pakietu NuGet i **GistProvider** przy użyciu modułu PowerShell **PackageManagement** zasobów DSC. W tym przykładzie najpierw zapewnia źródeł wymaganego pakietu są dostępne, a następnie definiuje oczekiwany stan **JQuery** i **GistProvider** pakietów (NuGet i programu PowerShell, odpowiednio).

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