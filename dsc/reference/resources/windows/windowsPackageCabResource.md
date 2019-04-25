---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: DSC WindowsPackageCab Resource
ms.openlocfilehash: 035944e7ca5c7469250c48a19b79f2f2d5d38e9a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076943"
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="38281-103">DSC WindowsPackageCab Resource</span><span class="sxs-lookup"><span data-stu-id="38281-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="38281-104">Dotyczy: Program Windows PowerShell w wersji 5.1 i nowszych</span><span class="sxs-lookup"><span data-stu-id="38281-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="38281-105">**WindowsPackageCab** zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm, aby zainstalować lub odinstalować Windows pakiety cabinet (cab) na węzeł docelowy.</span><span class="sxs-lookup"><span data-stu-id="38281-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="38281-106">Węzeł docelowy musi mieć zainstalowany moduł PowerShell narzędzie DISM.</span><span class="sxs-lookup"><span data-stu-id="38281-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="38281-107">Aby uzyskać informacje, zobacz [Użyj narzędzia DISM, w programie Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span><span class="sxs-lookup"><span data-stu-id="38281-107">For information, see [Use DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>


## <a name="syntax"></a><span data-ttu-id="38281-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="38281-108">Syntax</span></span>

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="38281-109">Właściwości</span><span class="sxs-lookup"><span data-stu-id="38281-109">Properties</span></span>

|  <span data-ttu-id="38281-110">Właściwość</span><span class="sxs-lookup"><span data-stu-id="38281-110">Property</span></span>  |  <span data-ttu-id="38281-111">Opis</span><span class="sxs-lookup"><span data-stu-id="38281-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="38281-112">Nazwa</span><span class="sxs-lookup"><span data-stu-id="38281-112">Name</span></span>| <span data-ttu-id="38281-113">Określa nazwę pakietu dla chce mieć pewność, z określonym stanem.</span><span class="sxs-lookup"><span data-stu-id="38281-113">Indicates the name of the package for you want to ensure a specific state.</span></span>|
| <span data-ttu-id="38281-114">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="38281-114">Ensure</span></span>| <span data-ttu-id="38281-115">Wskazuje, czy zainstalowano pakiet.</span><span class="sxs-lookup"><span data-stu-id="38281-115">Indicates if the package is installed.</span></span> <span data-ttu-id="38281-116">Ustaw tę właściwość na "Brak", upewnij się, że nie zainstalowano pakiet (lub odinstalować pakiet, jeśli jest zainstalowana).</span><span class="sxs-lookup"><span data-stu-id="38281-116">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="38281-117">Ustaw dla niej "Przedstawia" (wartość domyślna) upewnij się, że pakiet jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="38281-117">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="38281-118">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="38281-118">Path</span></span>| <span data-ttu-id="38281-119">Wskazuje ścieżkę, w której znajduje się pakiet.</span><span class="sxs-lookup"><span data-stu-id="38281-119">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="38281-120">Ścieżka dziennika</span><span class="sxs-lookup"><span data-stu-id="38281-120">LogPath</span></span>| <span data-ttu-id="38281-121">Określa pełną ścieżkę, której chcesz dostawcę Aby zapisać plik dziennika, aby zainstalować lub odinstalować pakiet.</span><span class="sxs-lookup"><span data-stu-id="38281-121">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="38281-122">dependsOn</span><span class="sxs-lookup"><span data-stu-id="38281-122">DependsOn</span></span> | <span data-ttu-id="38281-123">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="38281-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="38281-124">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest **ResourceName** a jej typ jest **ResourceType**, składnia przy użyciu tej właściwości to "DependsOn ="[ ResourceName ResourceType]"".</span><span class="sxs-lookup"><span data-stu-id="38281-124">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example"></a><span data-ttu-id="38281-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="38281-125">Example</span></span>

<span data-ttu-id="38281-126">Poniższa przykładowa konfiguracja pobiera parametry wejściowe i gwarantuje, że pliku cab określony przez `$Name` parametru jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="38281-126">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```