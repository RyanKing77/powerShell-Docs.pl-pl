---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób PackageManagementSource DSC
ms.openlocfilehash: 3e67cec9058ecb0e43f882f98f5ec8b92e261a09
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="60abe-103">Zasób PackageManagementSource DSC</span><span class="sxs-lookup"><span data-stu-id="60abe-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="60abe-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="60abe-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="60abe-105">**PackageManagementSource** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm do zarejestrowania lub wyrejestrowania źródła zarządzania pakietami w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="60abe-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="60abe-106">**Pakiet zarządzania źródeł zarejestrowanych w ten sposób są rejestrowane w kontekście systemu, można używać z konta System lub przez aparat DSC.**</span><span class="sxs-lookup"><span data-stu-id="60abe-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="60abe-107">Ten zasób wymaga **PackageManagement** modułu, dostępne z http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="60abe-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="60abe-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="60abe-108">Syntax</span></span>

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="60abe-109">Właściwości</span><span class="sxs-lookup"><span data-stu-id="60abe-109">Properties</span></span>
|  <span data-ttu-id="60abe-110">Właściwość</span><span class="sxs-lookup"><span data-stu-id="60abe-110">Property</span></span>  |  <span data-ttu-id="60abe-111">Opis</span><span class="sxs-lookup"><span data-stu-id="60abe-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="60abe-112">Nazwa</span><span class="sxs-lookup"><span data-stu-id="60abe-112">Name</span></span>| <span data-ttu-id="60abe-113">Określa nazwę źródła pakietu jest zarejestrowany lub wyrejestrowany w systemie.</span><span class="sxs-lookup"><span data-stu-id="60abe-113">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="60abe-114">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="60abe-114">Ensure</span></span>| <span data-ttu-id="60abe-115">Określa, czy źródło pakietu ma zostać zarejestrowany lub wyrejestrowany.</span><span class="sxs-lookup"><span data-stu-id="60abe-115">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="60abe-116">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="60abe-116">InstallationPolicy</span></span>| <span data-ttu-id="60abe-117">Określa, czy masz zaufanie źródła pakietu.</span><span class="sxs-lookup"><span data-stu-id="60abe-117">Determines whether you trust the package source.</span></span> <span data-ttu-id="60abe-118">Jeden z: "Niezaufanych", "Zaufanym".</span><span class="sxs-lookup"><span data-stu-id="60abe-118">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="60abe-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="60abe-119">ProviderName</span></span>| <span data-ttu-id="60abe-120">Określa nazwę dostawcy OneGet za pośrednictwem której można współdziałanie ze źródłem pakietu.</span><span class="sxs-lookup"><span data-stu-id="60abe-120">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="60abe-121">SourceUri</span><span class="sxs-lookup"><span data-stu-id="60abe-121">SourceUri</span></span>| <span data-ttu-id="60abe-122">Określa identyfikator URI źródła pakietu.</span><span class="sxs-lookup"><span data-stu-id="60abe-122">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="60abe-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="60abe-123">SourceCredential</span></span>| <span data-ttu-id="60abe-124">Umożliwia dostęp do pakietu zdalnego źródła.</span><span class="sxs-lookup"><span data-stu-id="60abe-124">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="60abe-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="60abe-125">Example</span></span>

<span data-ttu-id="60abe-126">W tym przykładzie rejestruje http://nuget.org źródła pakietu przy użyciu **PackageManagementSource** zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="60abe-126">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceUri   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```