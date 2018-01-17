---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Zasób PackageManagement DSC"
ms.openlocfilehash: 4cd7625af7ed0bb3fe971c826ac2075841cdfdc5
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="6840a-103">Zasób PackageManagement DSC</span><span class="sxs-lookup"><span data-stu-id="6840a-103">DSC PackageManagement Resource</span></span>

> <span data-ttu-id="6840a-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6840a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="6840a-105">**PackageManagement** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm umożliwiający instalowanie lub odinstalowywanie pakiety zarządzania pakietami w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="6840a-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="6840a-106">Ten zasób wymaga **PackageManagement** modułu, dostępne z http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="6840a-106">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="6840a-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="6840a-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="6840a-108">Właściwości</span><span class="sxs-lookup"><span data-stu-id="6840a-108">Properties</span></span>
|  <span data-ttu-id="6840a-109">Właściwość</span><span class="sxs-lookup"><span data-stu-id="6840a-109">Property</span></span>  |  <span data-ttu-id="6840a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="6840a-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="6840a-111">Nazwa</span><span class="sxs-lookup"><span data-stu-id="6840a-111">Name</span></span>| <span data-ttu-id="6840a-112">Określa nazwę pakietu do zainstalowania lub odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="6840a-112">Specifies the name of the Package to be installed or uninstalled.</span></span>| 
| <span data-ttu-id="6840a-113">Źródło</span><span class="sxs-lookup"><span data-stu-id="6840a-113">Source</span></span>| <span data-ttu-id="6840a-114">Określa nazwę źródła pakietów, gdzie można znaleźć pakietu.</span><span class="sxs-lookup"><span data-stu-id="6840a-114">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="6840a-115">Może to być identyfikator URI lub źródło zarejestrowany w usłudze PackageSource rejestru lub PackageManagementSource DSC zasobu.</span><span class="sxs-lookup"><span data-stu-id="6840a-115">This can either be a URI or a source registered with Register-PackageSource or PackageManagementSource DSC resource.</span></span> <span data-ttu-id="6840a-116">Zasób DSC MSFT_PackageManagementSource można również zarejestrować źródła pakietu.</span><span class="sxs-lookup"><span data-stu-id="6840a-116">The DSC resource MSFT_PackageManagementSource can also register a package source.</span></span>| 
| <span data-ttu-id="6840a-117">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="6840a-117">Ensure</span></span>| <span data-ttu-id="6840a-118">Określa, czy pakiet jest zainstalowany lub odinstalowany.</span><span class="sxs-lookup"><span data-stu-id="6840a-118">Determines whether the package is to be installed or uninstalled.</span></span>| 
| <span data-ttu-id="6840a-119">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="6840a-119">RequiredVersion</span></span>| <span data-ttu-id="6840a-120">Określa dokładną wersję pakietu, który chcesz zainstalować.</span><span class="sxs-lookup"><span data-stu-id="6840a-120">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="6840a-121">Jeśli nie określisz ten parametr, tego zasobu DSC instaluje najnowszą wersję dostępne spełniającego wszystkie maksymalna wersja określona w parametrze MaximumVersion pakietu.</span><span class="sxs-lookup"><span data-stu-id="6840a-121">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the MaximumVersion parameter.</span></span>| 
| <span data-ttu-id="6840a-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="6840a-122">MinimumVersion</span></span>| <span data-ttu-id="6840a-123">Określa wersję pakietu, który chcesz zainstalować dozwolony.</span><span class="sxs-lookup"><span data-stu-id="6840a-123">Specifies the minimum allowed version of the package that you want to install.</span></span> <span data-ttu-id="6840a-124">Jeśli ten parametr to intalls zasobów DSC najwyższy dostępna wersja pakietu, który spełnia również maksymalna wersja określona określonej przez parametr MaximumVersion nie zostaną dodane.</span><span class="sxs-lookup"><span data-stu-id="6840a-124">If you do not add this parameter, this DSC resource intalls the highest available version of the package that also satisfies any maximum specified version specified by the MaximumVersion parameter.</span></span>| 
| <span data-ttu-id="6840a-125">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="6840a-125">MaximumVersion</span></span>| <span data-ttu-id="6840a-126">Określa maksymalny dozwolony wersję pakietu, który chcesz zainstalować.</span><span class="sxs-lookup"><span data-stu-id="6840a-126">Specifies the maximum allowed version of the package that you want to install.</span></span> <span data-ttu-id="6840a-127">Jeśli nie określisz ten parametr, ten zasób DSC instaluje najwyższym numerze wersji dostępnych pakietu.</span><span class="sxs-lookup"><span data-stu-id="6840a-127">If you do not specify this parameter, this DSC resource installs the highest-numbered available version of the package.</span></span>| 
| <span data-ttu-id="6840a-128">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="6840a-128">SourceCredential</span></span> | <span data-ttu-id="6840a-129">Określa konto użytkownika, które ma uprawnienia do zainstalowania pakietu dla określonego pakietu dostawcę lub źródło.</span><span class="sxs-lookup"><span data-stu-id="6840a-129">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>| 
| <span data-ttu-id="6840a-130">ProviderName</span><span class="sxs-lookup"><span data-stu-id="6840a-130">ProviderName</span></span>| <span data-ttu-id="6840a-131">Określa nazwę dostawcy pakietów, do którego należy określić zakres wyszukiwania pakietu.</span><span class="sxs-lookup"><span data-stu-id="6840a-131">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="6840a-132">Nazwy dostawcy pakietu można uzyskać, uruchamiając polecenie cmdlet Get-PackageProvider.</span><span class="sxs-lookup"><span data-stu-id="6840a-132">You can get package provider names by running the Get-PackageProvider cmdlet.</span></span>| 
| <span data-ttu-id="6840a-133">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="6840a-133">AdditionalParameters</span></span>| <span data-ttu-id="6840a-134">Dostawca określonych parametrów, które są przekazywane jako tablica skrótów.</span><span class="sxs-lookup"><span data-stu-id="6840a-134">Provider specific parameters that are passed as an Hashtable.</span></span> <span data-ttu-id="6840a-135">Na przykład dla dostawcy NuGet można przekazać dodatkowe parametry, takie jak Ścieżka_docelowa.</span><span class="sxs-lookup"><span data-stu-id="6840a-135">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>| 

## <a name="additional-parameters"></a><span data-ttu-id="6840a-136">Dodatkowe parametry</span><span class="sxs-lookup"><span data-stu-id="6840a-136">Additional Parameters</span></span>
<span data-ttu-id="6840a-137">W poniższej tabeli wymieniono opcje dla właściwości AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="6840a-137">The following table lists options for the AdditionalParameters property.</span></span>
|  <span data-ttu-id="6840a-138">Parametr</span><span class="sxs-lookup"><span data-stu-id="6840a-138">Parameter</span></span>  | <span data-ttu-id="6840a-139">Opis</span><span class="sxs-lookup"><span data-stu-id="6840a-139">Description</span></span>   | 
|---|---|
| <span data-ttu-id="6840a-140">Ścieżka_docelowa</span><span class="sxs-lookup"><span data-stu-id="6840a-140">DestinationPath</span></span>| <span data-ttu-id="6840a-141">Używane przez dostawców, takich jak wbudowanego dostawcy Nuget.</span><span class="sxs-lookup"><span data-stu-id="6840a-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="6840a-142">Określa lokalizację plików miejscu pakietu do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="6840a-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="6840a-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="6840a-143">InstallationPolicy</span></span>| <span data-ttu-id="6840a-144">Używane przez dostawców, takich jak wbudowanego dostawcy Nuget.</span><span class="sxs-lookup"><span data-stu-id="6840a-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="6840a-145">Określa, czy ufasz źródłu tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="6840a-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="6840a-146">One of: "Untrusted", "Trusted".</span><span class="sxs-lookup"><span data-stu-id="6840a-146">One of: "Untrusted", "Trusted".</span></span>|

## <a name="example"></a><span data-ttu-id="6840a-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="6840a-147">Example</span></span>

<span data-ttu-id="6840a-148">Instalacja **JQuery** pakietu NuGet i **GistProvider** przy użyciu modułu PowerShell **PackageManagement** zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="6840a-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="6840a-149">W tym przykładzie najpierw zapewnia źródeł wymaganego pakietu są dostępne, a następnie definiuje oczekiwany stan **JQuery** i **GistProvider** pakietów (NuGet i programu PowerShell, odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="6840a-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

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

