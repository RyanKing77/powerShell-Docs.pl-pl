---
ms.date: 06/20/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób PackageManagementSource DSC
ms.openlocfilehash: e51b5318288bef458567dd4b58d17caaea3ed69b
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048373"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="d037d-103">Zasób PackageManagementSource DSC</span><span class="sxs-lookup"><span data-stu-id="d037d-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="d037d-104">Dotyczy: Program Windows PowerShell 4.0, Windows PowerShell 5.0, programu Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="d037d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="d037d-105">**PackageManagementSource** zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm, aby zarejestrować lub wyrejestrować źródła zarządzania pakietami na węzeł docelowy.</span><span class="sxs-lookup"><span data-stu-id="d037d-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="d037d-106">**Pakiet zarządzania źródeł zarejestrowanych w ten sposób są rejestrowane w kontekście systemu, można używać konta systemowego lub aparatu DSC.**</span><span class="sxs-lookup"><span data-stu-id="d037d-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="d037d-107">Ten zasób wymaga **PackageManagement** modułu dostępnym http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="d037d-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d037d-108">**PackageManagement** moduł powinien wynosić co najmniej wersji 1.1.7.0 podanie następujących informacji właściwość prawdopodobnie jest niepoprawny.</span><span class="sxs-lookup"><span data-stu-id="d037d-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="d037d-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="d037d-109">Syntax</span></span>

```
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [InstallationPolicy = [string]{ Trusted | Untrusted }]
    [PsDscRunAsCredential = [PSCredential]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a><span data-ttu-id="d037d-110">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d037d-110">Properties</span></span>

|  <span data-ttu-id="d037d-111">Właściwość</span><span class="sxs-lookup"><span data-stu-id="d037d-111">Property</span></span>  |  <span data-ttu-id="d037d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d037d-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="d037d-113">Nazwa</span><span class="sxs-lookup"><span data-stu-id="d037d-113">Name</span></span>| <span data-ttu-id="d037d-114">Określa nazwę źródła pakietu do zarejestrowania lub niezarejestrowanych w Twoim systemie.</span><span class="sxs-lookup"><span data-stu-id="d037d-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="d037d-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="d037d-115">ProviderName</span></span>| <span data-ttu-id="d037d-116">Określa nazwę dostawca funkcji OneGet za pomocą którego można współdziałania ze źródłem pakietu.</span><span class="sxs-lookup"><span data-stu-id="d037d-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="d037d-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="d037d-117">SourceLocation</span></span>| <span data-ttu-id="d037d-118">Określa identyfikator URI źródła pakietu.</span><span class="sxs-lookup"><span data-stu-id="d037d-118">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="d037d-119">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="d037d-119">Ensure</span></span>| <span data-ttu-id="d037d-120">Określa, czy ma być rejestrowany i wyrejestrowywany źródła pakietu.</span><span class="sxs-lookup"><span data-stu-id="d037d-120">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="d037d-121">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="d037d-121">InstallationPolicy</span></span>| <span data-ttu-id="d037d-122">Używane przez dostawców, takich jak wbudowanego dostawcy Nuget.</span><span class="sxs-lookup"><span data-stu-id="d037d-122">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="d037d-123">Określa, czy ufasz źródłu pakietu.</span><span class="sxs-lookup"><span data-stu-id="d037d-123">Determines whether you trust the package's source.</span></span> <span data-ttu-id="d037d-124">Jeden z: "Niezaufanych", "zaufany".</span><span class="sxs-lookup"><span data-stu-id="d037d-124">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="d037d-125">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="d037d-125">SourceCredential</span></span>| <span data-ttu-id="d037d-126">Umożliwia dostęp do pakietu zdalnego źródła.</span><span class="sxs-lookup"><span data-stu-id="d037d-126">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="d037d-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="d037d-127">Example</span></span>

<span data-ttu-id="d037d-128">W tym przykładzie rejestruje http://nuget.org źródła pakietu przy użyciu **PackageManagementSource** zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="d037d-128">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```