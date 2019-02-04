---
ms.date: 06/20/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: DSC PackageManagementSource Resource
ms.openlocfilehash: e51b5318288bef458567dd4b58d17caaea3ed69b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686320"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="5d9e3-103">DSC PackageManagementSource Resource</span><span class="sxs-lookup"><span data-stu-id="5d9e3-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="5d9e3-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="5d9e3-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="5d9e3-105">**PackageManagementSource** zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm, aby zarejestrować lub wyrejestrować źródła zarządzania pakietami na węzeł docelowy.</span><span class="sxs-lookup"><span data-stu-id="5d9e3-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="5d9e3-106">**Pakiet zarządzania źródeł zarejestrowanych w ten sposób są rejestrowane w kontekście systemu, można używać konta systemowego lub aparatu DSC.**</span><span class="sxs-lookup"><span data-stu-id="5d9e3-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="5d9e3-107">Ten zasób wymaga **PackageManagement** modułu dostępnym http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="5d9e3-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5d9e3-108">**PackageManagement** moduł powinien wynosić co najmniej wersji 1.1.7.0 podanie następujących informacji właściwość prawdopodobnie jest niepoprawny.</span><span class="sxs-lookup"><span data-stu-id="5d9e3-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="5d9e3-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d9e3-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="5d9e3-110">Właściwości</span><span class="sxs-lookup"><span data-stu-id="5d9e3-110">Properties</span></span>

|  <span data-ttu-id="5d9e3-111">Właściwość</span><span class="sxs-lookup"><span data-stu-id="5d9e3-111">Property</span></span>  |  <span data-ttu-id="5d9e3-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5d9e3-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="5d9e3-113">Nazwa</span><span class="sxs-lookup"><span data-stu-id="5d9e3-113">Name</span></span>| <span data-ttu-id="5d9e3-114">Określa nazwę źródła pakietu do zarejestrowania lub niezarejestrowanych w Twoim systemie.</span><span class="sxs-lookup"><span data-stu-id="5d9e3-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="5d9e3-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="5d9e3-115">ProviderName</span></span>| <span data-ttu-id="5d9e3-116">Określa nazwę dostawca funkcji OneGet za pomocą którego można współdziałania ze źródłem pakietu.</span><span class="sxs-lookup"><span data-stu-id="5d9e3-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="5d9e3-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="5d9e3-117">SourceLocation</span></span>| <span data-ttu-id="5d9e3-118">Określa identyfikator URI źródła pakietu.</span><span class="sxs-lookup"><span data-stu-id="5d9e3-118">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="5d9e3-119">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="5d9e3-119">Ensure</span></span>| <span data-ttu-id="5d9e3-120">Określa, czy ma być rejestrowany i wyrejestrowywany źródła pakietu.</span><span class="sxs-lookup"><span data-stu-id="5d9e3-120">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="5d9e3-121">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="5d9e3-121">InstallationPolicy</span></span>| <span data-ttu-id="5d9e3-122">Używane przez dostawców, takich jak wbudowanego dostawcy Nuget.</span><span class="sxs-lookup"><span data-stu-id="5d9e3-122">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="5d9e3-123">Określa, czy ufasz źródłu pakietu.</span><span class="sxs-lookup"><span data-stu-id="5d9e3-123">Determines whether you trust the package's source.</span></span> <span data-ttu-id="5d9e3-124">Jeden z: "Niezaufanych", "zaufany".</span><span class="sxs-lookup"><span data-stu-id="5d9e3-124">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="5d9e3-125">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="5d9e3-125">SourceCredential</span></span>| <span data-ttu-id="5d9e3-126">Umożliwia dostęp do pakietu zdalnego źródła.</span><span class="sxs-lookup"><span data-stu-id="5d9e3-126">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="5d9e3-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d9e3-127">Example</span></span>

<span data-ttu-id="5d9e3-128">W tym przykładzie rejestruje http://nuget.org źródła pakietu przy użyciu **PackageManagementSource** zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="5d9e3-128">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

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