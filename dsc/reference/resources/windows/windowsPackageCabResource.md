---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób Windowspackagecab DSC
ms.openlocfilehash: 035944e7ca5c7469250c48a19b79f2f2d5d38e9a
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048398"
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="f8e45-103">Zasób Windowspackagecab DSC</span><span class="sxs-lookup"><span data-stu-id="f8e45-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="f8e45-104">Dotyczy: Program Windows PowerShell w wersji 5.1 i nowszych</span><span class="sxs-lookup"><span data-stu-id="f8e45-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="f8e45-105">**WindowsPackageCab** zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm, aby zainstalować lub odinstalować Windows pakiety cabinet (cab) na węzeł docelowy.</span><span class="sxs-lookup"><span data-stu-id="f8e45-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="f8e45-106">Węzeł docelowy musi mieć zainstalowany moduł PowerShell narzędzie DISM.</span><span class="sxs-lookup"><span data-stu-id="f8e45-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="f8e45-107">Aby uzyskać informacje, zobacz [Użyj narzędzia DISM, w programie Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span><span class="sxs-lookup"><span data-stu-id="f8e45-107">For information, see [Use DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>


## <a name="syntax"></a><span data-ttu-id="f8e45-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8e45-108">Syntax</span></span>

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="f8e45-109">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f8e45-109">Properties</span></span>

|  <span data-ttu-id="f8e45-110">Właściwość</span><span class="sxs-lookup"><span data-stu-id="f8e45-110">Property</span></span>  |  <span data-ttu-id="f8e45-111">Opis</span><span class="sxs-lookup"><span data-stu-id="f8e45-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="f8e45-112">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f8e45-112">Name</span></span>| <span data-ttu-id="f8e45-113">Określa nazwę pakietu dla chce mieć pewność, z określonym stanem.</span><span class="sxs-lookup"><span data-stu-id="f8e45-113">Indicates the name of the package for you want to ensure a specific state.</span></span>|
| <span data-ttu-id="f8e45-114">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="f8e45-114">Ensure</span></span>| <span data-ttu-id="f8e45-115">Wskazuje, czy zainstalowano pakiet.</span><span class="sxs-lookup"><span data-stu-id="f8e45-115">Indicates if the package is installed.</span></span> <span data-ttu-id="f8e45-116">Ustaw tę właściwość na "Brak", upewnij się, że nie zainstalowano pakiet (lub odinstalować pakiet, jeśli jest zainstalowana).</span><span class="sxs-lookup"><span data-stu-id="f8e45-116">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="f8e45-117">Ustaw dla niej "Przedstawia" (wartość domyślna) upewnij się, że pakiet jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="f8e45-117">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="f8e45-118">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="f8e45-118">Path</span></span>| <span data-ttu-id="f8e45-119">Wskazuje ścieżkę, w której znajduje się pakiet.</span><span class="sxs-lookup"><span data-stu-id="f8e45-119">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="f8e45-120">Ścieżka dziennika</span><span class="sxs-lookup"><span data-stu-id="f8e45-120">LogPath</span></span>| <span data-ttu-id="f8e45-121">Określa pełną ścieżkę, której chcesz dostawcę Aby zapisać plik dziennika, aby zainstalować lub odinstalować pakiet.</span><span class="sxs-lookup"><span data-stu-id="f8e45-121">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="f8e45-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f8e45-122">DependsOn</span></span> | <span data-ttu-id="f8e45-123">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="f8e45-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f8e45-124">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest **ResourceName** a jej typ jest **ResourceType**, składnia przy użyciu tej właściwości to "DependsOn ="[ ResourceName ResourceType]"".</span><span class="sxs-lookup"><span data-stu-id="f8e45-124">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example"></a><span data-ttu-id="f8e45-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8e45-125">Example</span></span>

<span data-ttu-id="f8e45-126">Poniższa przykładowa konfiguracja pobiera parametry wejściowe i gwarantuje, że pliku cab określony przez `$Name` parametru jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="f8e45-126">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

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