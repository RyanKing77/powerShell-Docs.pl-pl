---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób WindowsPackageCab DSC
ms.openlocfilehash: 8c4de193c8ea787dd125436f86aa0b5eafdb1509
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190353"
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="3a677-103">Zasób WindowsPackageCab DSC</span><span class="sxs-lookup"><span data-stu-id="3a677-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="3a677-104">Dotyczy: Windows PowerShell 5.1 i nowszych</span><span class="sxs-lookup"><span data-stu-id="3a677-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="3a677-105">**WindowsPackageCab** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm umożliwiający instalowanie lub odinstalowywanie pakiety cabinet (cab) systemu Windows w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="3a677-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="3a677-106">Węzeł docelowy musi mieć zainstalowany moduł PowerShell narzędzie DISM.</span><span class="sxs-lookup"><span data-stu-id="3a677-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="3a677-107">Aby uzyskać informacje, zobacz [DISM używany w programie Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span><span class="sxs-lookup"><span data-stu-id="3a677-107">For information, see [Use DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>


## <a name="syntax"></a><span data-ttu-id="3a677-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a677-108">Syntax</span></span>

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="3a677-109">Właściwości</span><span class="sxs-lookup"><span data-stu-id="3a677-109">Properties</span></span>

|  <span data-ttu-id="3a677-110">Właściwość</span><span class="sxs-lookup"><span data-stu-id="3a677-110">Property</span></span>  |  <span data-ttu-id="3a677-111">Opis</span><span class="sxs-lookup"><span data-stu-id="3a677-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="3a677-112">Nazwa</span><span class="sxs-lookup"><span data-stu-id="3a677-112">Name</span></span>| <span data-ttu-id="3a677-113">Wskazuje nazwy pakietu dla chcesz zapewnić z określonym stanem.</span><span class="sxs-lookup"><span data-stu-id="3a677-113">Indicates the name of the package for you want to ensure a specific state.</span></span>|
| <span data-ttu-id="3a677-114">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="3a677-114">Ensure</span></span>| <span data-ttu-id="3a677-115">Wskazuje, czy pakiet jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="3a677-115">Indicates if the package is installed.</span></span> <span data-ttu-id="3a677-116">Ustaw tę właściwość na "Brak", upewnij się, że pakiet nie jest zainstalowany (lub odinstalować pakiet, jeśli jest zainstalowana).</span><span class="sxs-lookup"><span data-stu-id="3a677-116">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="3a677-117">Ustaw "Przedstawić" (wartość domyślna) upewnij się, że pakiet jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="3a677-117">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="3a677-118">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="3a677-118">Path</span></span>| <span data-ttu-id="3a677-119">Określa ścieżkę, w której znajduje się pakiet.</span><span class="sxs-lookup"><span data-stu-id="3a677-119">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="3a677-120">Ścieżka dziennika</span><span class="sxs-lookup"><span data-stu-id="3a677-120">LogPath</span></span>| <span data-ttu-id="3a677-121">Określa pełną ścieżkę, w którym ma dostawcy, aby zapisać plik dziennika, aby zainstalować lub odinstalować pakiet.</span><span class="sxs-lookup"><span data-stu-id="3a677-121">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="3a677-122">dependsOn</span><span class="sxs-lookup"><span data-stu-id="3a677-122">DependsOn</span></span> | <span data-ttu-id="3a677-123">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="3a677-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="3a677-124">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest **ResourceName** i jej typ jest **ResourceType**, składnia za pomocą tej właściwości to "DependsOn ="[ResourceName ResourceType]"".</span><span class="sxs-lookup"><span data-stu-id="3a677-124">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example"></a><span data-ttu-id="3a677-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="3a677-125">Example</span></span>

<span data-ttu-id="3a677-126">Poniższa przykładowa konfiguracja pobiera parametry wejściowe i zapewnia, że plik cab określony przez `$Name` parametru jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="3a677-126">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

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