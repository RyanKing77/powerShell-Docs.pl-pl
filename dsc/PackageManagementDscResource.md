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
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="7cda4-103">Zasób PackageManagement DSC</span><span class="sxs-lookup"><span data-stu-id="7cda4-103">DSC PackageManagement Resource</span></span>

> <span data-ttu-id="7cda4-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0, środowiska Windows PowerShell w wersji 5.1</span><span class="sxs-lookup"><span data-stu-id="7cda4-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="7cda4-105">**PackageManagement** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm umożliwiający instalowanie lub odinstalowywanie pakiety zarządzania pakietami w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="7cda4-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="7cda4-106">Ten zasób wymaga **PackageManagement** modułu, dostępne z http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="7cda4-106">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7cda4-107">**PackageManagement** modułu powinna wynosić co najmniej wersji 1.1.7.0 następujących informacji właściwości są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="7cda4-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="7cda4-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="7cda4-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="7cda4-109">Właściwości</span><span class="sxs-lookup"><span data-stu-id="7cda4-109">Properties</span></span>

|  <span data-ttu-id="7cda4-110">Właściwość</span><span class="sxs-lookup"><span data-stu-id="7cda4-110">Property</span></span>  |  <span data-ttu-id="7cda4-111">Opis</span><span class="sxs-lookup"><span data-stu-id="7cda4-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="7cda4-112">Nazwa</span><span class="sxs-lookup"><span data-stu-id="7cda4-112">Name</span></span>| <span data-ttu-id="7cda4-113">Określa nazwę pakietu do zainstalowania lub odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="7cda4-113">Specifies the name of the Package to be installed or uninstalled.</span></span>|
| <span data-ttu-id="7cda4-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="7cda4-114">AdditionalParameters</span></span>| <span data-ttu-id="7cda4-115">Dostawca hashtable określonych parametrów, które zostaną przekazane do `Get-Package -AdditionalArguments`.</span><span class="sxs-lookup"><span data-stu-id="7cda4-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="7cda4-116">Na przykład dla dostawcy NuGet można przekazać dodatkowe parametry, takie jak Ścieżka_docelowa.</span><span class="sxs-lookup"><span data-stu-id="7cda4-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>|
| <span data-ttu-id="7cda4-117">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="7cda4-117">Ensure</span></span>| <span data-ttu-id="7cda4-118">Określa, czy pakiet jest zainstalowany lub odinstalowany.</span><span class="sxs-lookup"><span data-stu-id="7cda4-118">Determines whether the package is to be installed or uninstalled.</span></span>|
| <span data-ttu-id="7cda4-119">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="7cda4-119">MaximumVersion</span></span>|<span data-ttu-id="7cda4-120">Określa maksymalny dozwolony wersji pakietu, który ma zostać znaleziona.</span><span class="sxs-lookup"><span data-stu-id="7cda4-120">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="7cda4-121">Jeśli ten parametr nie zostanie dodany, zasób znajduje najwyższy dostępna wersja pakietu.</span><span class="sxs-lookup"><span data-stu-id="7cda4-121">If you do not add this parameter, the resource finds the highest available version of the package.</span></span>|
| <span data-ttu-id="7cda4-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="7cda4-122">MinimumVersion</span></span>|<span data-ttu-id="7cda4-123">Określa minimalną dozwoloną wersji pakietu, który ma zostać znaleziona.</span><span class="sxs-lookup"><span data-stu-id="7cda4-123">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="7cda4-124">Jeśli ten parametr nie zostanie dodany, zasobu znajdzie najwyższy dostępna wersja pakietu, który spełnia również maksymalna wersja określona określony przez _MaximumVersion_ parametru.</span><span class="sxs-lookup"><span data-stu-id="7cda4-124">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="7cda4-125">ProviderName</span><span class="sxs-lookup"><span data-stu-id="7cda4-125">ProviderName</span></span>| <span data-ttu-id="7cda4-126">Określa nazwę dostawcy pakietów, do którego należy określić zakres wyszukiwania pakietu.</span><span class="sxs-lookup"><span data-stu-id="7cda4-126">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="7cda4-127">Nazwy dostawców pakietu można uzyskać, uruchamiając `Get-PackageProvider` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7cda4-127">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>|
| <span data-ttu-id="7cda4-128">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="7cda4-128">RequiredVersion</span></span>| <span data-ttu-id="7cda4-129">Określa dokładną wersję pakietu, który chcesz zainstalować.</span><span class="sxs-lookup"><span data-stu-id="7cda4-129">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="7cda4-130">Jeśli nie określisz ten parametr, ten zasób DSC instaluje najnowszą wersję dostępny pakiet, który również spełnia wszelkie maksymalna wersja określona przez _MaximumVersion_ parametru.</span><span class="sxs-lookup"><span data-stu-id="7cda4-130">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="7cda4-131">Źródło</span><span class="sxs-lookup"><span data-stu-id="7cda4-131">Source</span></span>| <span data-ttu-id="7cda4-132">Określa nazwę źródła pakietów, gdzie można znaleźć pakietu.</span><span class="sxs-lookup"><span data-stu-id="7cda4-132">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="7cda4-133">Może to być identyfikator URI lub źródło zarejestrowany w usłudze `Register-PackageSource` lub zasobu PackageManagementSource DSC.</span><span class="sxs-lookup"><span data-stu-id="7cda4-133">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span>|
| <span data-ttu-id="7cda4-134">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="7cda4-134">SourceCredential</span></span> | <span data-ttu-id="7cda4-135">Określa konto użytkownika, które ma uprawnienia do zainstalowania pakietu dla określonego pakietu dostawcę lub źródło.</span><span class="sxs-lookup"><span data-stu-id="7cda4-135">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>|

## <a name="additional-parameters"></a><span data-ttu-id="7cda4-136">Dodatkowe parametry</span><span class="sxs-lookup"><span data-stu-id="7cda4-136">Additional Parameters</span></span>

<span data-ttu-id="7cda4-137">W poniższej tabeli wymieniono opcje dla właściwości AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="7cda4-137">The following table lists options for the AdditionalParameters property.</span></span>
|  <span data-ttu-id="7cda4-138">Parametr</span><span class="sxs-lookup"><span data-stu-id="7cda4-138">Parameter</span></span>  | <span data-ttu-id="7cda4-139">Opis</span><span class="sxs-lookup"><span data-stu-id="7cda4-139">Description</span></span>   |
|---|---|
| <span data-ttu-id="7cda4-140">Ścieżka_docelowa</span><span class="sxs-lookup"><span data-stu-id="7cda4-140">DestinationPath</span></span>| <span data-ttu-id="7cda4-141">Używane przez dostawców, takich jak wbudowanego dostawcy Nuget.</span><span class="sxs-lookup"><span data-stu-id="7cda4-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="7cda4-142">Określa lokalizację plików miejscu pakietu do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="7cda4-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="7cda4-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="7cda4-143">InstallationPolicy</span></span>| <span data-ttu-id="7cda4-144">Używane przez dostawców, takich jak wbudowanego dostawcy Nuget.</span><span class="sxs-lookup"><span data-stu-id="7cda4-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="7cda4-145">Określa, czy ufasz źródłu tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="7cda4-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="7cda4-146">Jeden z: "Niezaufanych", "Zaufanym".</span><span class="sxs-lookup"><span data-stu-id="7cda4-146">One of: "Untrusted", "Trusted".</span></span>|

## <a name="example"></a><span data-ttu-id="7cda4-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cda4-147">Example</span></span>

<span data-ttu-id="7cda4-148">Instalacja **JQuery** pakietu NuGet i **GistProvider** przy użyciu modułu PowerShell **PackageManagement** zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="7cda4-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="7cda4-149">W tym przykładzie najpierw zapewnia źródeł wymaganego pakietu są dostępne, a następnie definiuje oczekiwany stan **JQuery** i **GistProvider** pakietów (NuGet i programu PowerShell, odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="7cda4-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

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