---
ms.date: 06/20/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób PackageManagement DSC
ms.openlocfilehash: 18cbbfe0715c82dcfdf4a5fb6ee36ee814e43d3b
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048487"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="d5e65-103">Zasób PackageManagement DSC</span><span class="sxs-lookup"><span data-stu-id="d5e65-103">DSC PackageManagement Resource</span></span>

<span data-ttu-id="d5e65-104">Dotyczy: Program Windows PowerShell 4.0, Windows PowerShell 5.0, programu Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="d5e65-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="d5e65-105">**PackageManagement** zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm, aby zainstalować lub odinstalować pakiety zarządzania pakietami na węzeł docelowy.</span><span class="sxs-lookup"><span data-stu-id="d5e65-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="d5e65-106">Ten zasób wymaga **PackageManagement** modułu dostępnym [ http://PowerShellGallery.com ](http://PowerShellGallery.com).</span><span class="sxs-lookup"><span data-stu-id="d5e65-106">This resource requires the **PackageManagement** module, available from [http://PowerShellGallery.com](http://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d5e65-107">**PackageManagement** moduł powinien wynosić co najmniej wersji 1.1.7.0 podanie następujących informacji właściwość prawdopodobnie jest niepoprawny.</span><span class="sxs-lookup"><span data-stu-id="d5e65-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="d5e65-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="d5e65-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="d5e65-109">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d5e65-109">Properties</span></span>

| <span data-ttu-id="d5e65-110">Właściwość</span><span class="sxs-lookup"><span data-stu-id="d5e65-110">Property</span></span> | <span data-ttu-id="d5e65-111">Opis</span><span class="sxs-lookup"><span data-stu-id="d5e65-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="d5e65-112">Nazwa</span><span class="sxs-lookup"><span data-stu-id="d5e65-112">Name</span></span>| <span data-ttu-id="d5e65-113">Określa nazwę pakietu do zainstalowania lub odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="d5e65-113">Specifies the name of the Package to be installed or uninstalled.</span></span>|
| <span data-ttu-id="d5e65-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="d5e65-114">AdditionalParameters</span></span>| <span data-ttu-id="d5e65-115">Dostawca hashtable określonych parametrów, które zostaną przekazane do `Get-Package -AdditionalArguments`.</span><span class="sxs-lookup"><span data-stu-id="d5e65-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="d5e65-116">Na przykład dla dostawcy NuGet można przekazywać dodatkowych parametrów, takich jak Ścieżka_docelowa.</span><span class="sxs-lookup"><span data-stu-id="d5e65-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>|
| <span data-ttu-id="d5e65-117">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="d5e65-117">Ensure</span></span>| <span data-ttu-id="d5e65-118">Określa, czy pakiet jest zainstalowane lub odinstalowane.</span><span class="sxs-lookup"><span data-stu-id="d5e65-118">Determines whether the package is to be installed or uninstalled.</span></span>|
| <span data-ttu-id="d5e65-119">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="d5e65-119">MaximumVersion</span></span>|<span data-ttu-id="d5e65-120">Określa maksymalną dozwoloną wersję pakietu, który ma zostać odnaleziona.</span><span class="sxs-lookup"><span data-stu-id="d5e65-120">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="d5e65-121">Jeśli ten parametr nie zostanie dodany, zasób znajduje najwyższej dostępnej wersji pakietu.</span><span class="sxs-lookup"><span data-stu-id="d5e65-121">If you do not add this parameter, the resource finds the highest available version of the package.</span></span>|
| <span data-ttu-id="d5e65-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="d5e65-122">MinimumVersion</span></span>|<span data-ttu-id="d5e65-123">Określa minimalną dozwoloną wersję pakietu, który ma zostać odnaleziona.</span><span class="sxs-lookup"><span data-stu-id="d5e65-123">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="d5e65-124">Jeśli ten parametr nie zostanie dodany, zasób znajdzie najwyższej dostępnej wersji pakietu, który także spełnia wszelkie maksymalnej określonej wersji określonej przez _MaximumVersion_ parametru.</span><span class="sxs-lookup"><span data-stu-id="d5e65-124">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="d5e65-125">ProviderName</span><span class="sxs-lookup"><span data-stu-id="d5e65-125">ProviderName</span></span>| <span data-ttu-id="d5e65-126">Określa nazwę dostawcy pakiet, dla której chcesz ograniczyć wyszukiwanie pakietu.</span><span class="sxs-lookup"><span data-stu-id="d5e65-126">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="d5e65-127">Nazwy dostawcy pakietu można uzyskać, uruchamiając `Get-PackageProvider` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d5e65-127">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>|
| <span data-ttu-id="d5e65-128">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="d5e65-128">RequiredVersion</span></span>| <span data-ttu-id="d5e65-129">Określa dokładną wersję pakietu, który chcesz zainstalować.</span><span class="sxs-lookup"><span data-stu-id="d5e65-129">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="d5e65-130">Jeśli ten parametr nie jest określony, ten zasób DSC instalacji najnowszej dostępnej wersji pakietu, który także spełnia wszelkie maksymalnej wersji określonej przez _MaximumVersion_ parametru.</span><span class="sxs-lookup"><span data-stu-id="d5e65-130">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="d5e65-131">Źródło</span><span class="sxs-lookup"><span data-stu-id="d5e65-131">Source</span></span>| <span data-ttu-id="d5e65-132">Określa nazwę źródła pakietu, gdzie można znaleźć pakietu.</span><span class="sxs-lookup"><span data-stu-id="d5e65-132">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="d5e65-133">Może to być identyfikator URI lub źródłem zarejestrowane w usłudze `Register-PackageSource` lub zasób DSC PackageManagementSource.</span><span class="sxs-lookup"><span data-stu-id="d5e65-133">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span>|
| <span data-ttu-id="d5e65-134">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="d5e65-134">SourceCredential</span></span> | <span data-ttu-id="d5e65-135">Określa konto użytkownika, które ma uprawnienia do zainstalowania pakietu dla dostawcy określonego pakietu lub źródła.</span><span class="sxs-lookup"><span data-stu-id="d5e65-135">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>|

## <a name="additional-parameters"></a><span data-ttu-id="d5e65-136">Dodatkowe parametry</span><span class="sxs-lookup"><span data-stu-id="d5e65-136">Additional Parameters</span></span>

<span data-ttu-id="d5e65-137">W poniższej tabeli wymieniono opcje dla właściwości AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="d5e65-137">The following table lists options for the AdditionalParameters property.</span></span>

| <span data-ttu-id="d5e65-138">Parametr</span><span class="sxs-lookup"><span data-stu-id="d5e65-138">Parameter</span></span> | <span data-ttu-id="d5e65-139">Opis</span><span class="sxs-lookup"><span data-stu-id="d5e65-139">Description</span></span> |
| --- | --- |
| <span data-ttu-id="d5e65-140">Ścieżka_docelowa</span><span class="sxs-lookup"><span data-stu-id="d5e65-140">DestinationPath</span></span>| <span data-ttu-id="d5e65-141">Używane przez dostawców, takich jak wbudowanego dostawcy Nuget.</span><span class="sxs-lookup"><span data-stu-id="d5e65-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="d5e65-142">Określa lokalizację pliku, którego pakiet do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="d5e65-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="d5e65-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="d5e65-143">InstallationPolicy</span></span>| <span data-ttu-id="d5e65-144">Używane przez dostawców, takich jak wbudowanego dostawcy Nuget.</span><span class="sxs-lookup"><span data-stu-id="d5e65-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="d5e65-145">Określa, czy ufasz źródłu pakietu.</span><span class="sxs-lookup"><span data-stu-id="d5e65-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="d5e65-146">Jeden z: `Untrusted`, `Trusted`.</span><span class="sxs-lookup"><span data-stu-id="d5e65-146">One of: `Untrusted`, `Trusted`.</span></span>|

## <a name="example"></a><span data-ttu-id="d5e65-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5e65-147">Example</span></span>

<span data-ttu-id="d5e65-148">W tym przykładzie instaluje **JQuery** pakietu NuGet i **GistProvider** przy użyciu modułu PowerShell **PackageManagement** zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="d5e65-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="d5e65-149">W tym przykładzie najpierw zapewnia źródeł wymaganego pakietu są dostępne, a następnie definiuje oczekiwany stan **JQuery** i **GistProvider** pakietów (NuGet i programu PowerShell, odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="d5e65-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

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