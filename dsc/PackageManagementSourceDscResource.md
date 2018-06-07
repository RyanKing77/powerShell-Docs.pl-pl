---
ms.date: 06/20/2018
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób PackageManagementSource DSC
ms.openlocfilehash: 5d049b05c387cafe27edb202d569852b10852dce
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753774"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="bd247-103">Zasób PackageManagementSource DSC</span><span class="sxs-lookup"><span data-stu-id="bd247-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="bd247-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0, środowiska Windows PowerShell w wersji 5.1</span><span class="sxs-lookup"><span data-stu-id="bd247-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="bd247-105">**PackageManagementSource** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm do zarejestrowania lub wyrejestrowania źródła zarządzania pakietami w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="bd247-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="bd247-106">**Pakiet zarządzania źródeł zarejestrowanych w ten sposób są rejestrowane w kontekście systemu, można używać z konta System lub przez aparat DSC.**</span><span class="sxs-lookup"><span data-stu-id="bd247-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="bd247-107">Ten zasób wymaga **PackageManagement** modułu, dostępne z http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="bd247-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bd247-108">**PackageManagement** modułu powinna wynosić co najmniej wersji 1.1.7.0 następujących informacji właściwości są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="bd247-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="bd247-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd247-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="bd247-110">Właściwości</span><span class="sxs-lookup"><span data-stu-id="bd247-110">Properties</span></span>

|  <span data-ttu-id="bd247-111">Właściwość</span><span class="sxs-lookup"><span data-stu-id="bd247-111">Property</span></span>  |  <span data-ttu-id="bd247-112">Opis</span><span class="sxs-lookup"><span data-stu-id="bd247-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="bd247-113">Nazwa</span><span class="sxs-lookup"><span data-stu-id="bd247-113">Name</span></span>| <span data-ttu-id="bd247-114">Określa nazwę źródła pakietu jest zarejestrowany lub wyrejestrowany w systemie.</span><span class="sxs-lookup"><span data-stu-id="bd247-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="bd247-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="bd247-115">ProviderName</span></span>| <span data-ttu-id="bd247-116">Określa nazwę dostawcy OneGet za pośrednictwem której można współdziałanie ze źródłem pakietu.</span><span class="sxs-lookup"><span data-stu-id="bd247-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="bd247-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="bd247-117">SourceLocation</span></span>| <span data-ttu-id="bd247-118">Określa identyfikator URI źródła pakietu.</span><span class="sxs-lookup"><span data-stu-id="bd247-118">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="bd247-119">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="bd247-119">Ensure</span></span>| <span data-ttu-id="bd247-120">Określa, czy źródło pakietu ma zostać zarejestrowany lub wyrejestrowany.</span><span class="sxs-lookup"><span data-stu-id="bd247-120">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="bd247-121">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="bd247-121">InstallationPolicy</span></span>| <span data-ttu-id="bd247-122">Używane przez dostawców, takich jak wbudowanego dostawcy Nuget.</span><span class="sxs-lookup"><span data-stu-id="bd247-122">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="bd247-123">Określa, czy ufasz źródłu tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="bd247-123">Determines whether you trust the package's source.</span></span> <span data-ttu-id="bd247-124">Jeden z: "Niezaufanych", "Zaufanym".</span><span class="sxs-lookup"><span data-stu-id="bd247-124">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="bd247-125">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="bd247-125">SourceCredential</span></span>| <span data-ttu-id="bd247-126">Umożliwia dostęp do pakietu zdalnego źródła.</span><span class="sxs-lookup"><span data-stu-id="bd247-126">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="bd247-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="bd247-127">Example</span></span>

<span data-ttu-id="bd247-128">W tym przykładzie rejestruje http://nuget.org źródła pakietu przy użyciu **PackageManagementSource** zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="bd247-128">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

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