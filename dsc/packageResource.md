---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób pakietu DSC
ms.openlocfilehash: cfa9d53d5ea588b0ec97e5503302a451caa09e03
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-package-resource"></a><span data-ttu-id="9dbaf-103">Zasób pakietu DSC</span><span class="sxs-lookup"><span data-stu-id="9dbaf-103">DSC Package Resource</span></span>

> <span data-ttu-id="9dbaf-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9dbaf-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="9dbaf-105">**Pakietu** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm umożliwiający instalowanie lub odinstalowywanie pakiety, takie jak pakietów Instalatora Windows i setup.exe w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="9dbaf-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="9dbaf-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="9dbaf-106">Syntax</span></span>

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="9dbaf-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="9dbaf-107">Properties</span></span>
|  <span data-ttu-id="9dbaf-108">Właściwość</span><span class="sxs-lookup"><span data-stu-id="9dbaf-108">Property</span></span>  |  <span data-ttu-id="9dbaf-109">Opis</span><span class="sxs-lookup"><span data-stu-id="9dbaf-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="9dbaf-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="9dbaf-110">Name</span></span>| <span data-ttu-id="9dbaf-111">Określa nazwę pakietu, dla którego chcesz zapewnić z określonym stanem.</span><span class="sxs-lookup"><span data-stu-id="9dbaf-111">Indicates the name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="9dbaf-112">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="9dbaf-112">Path</span></span>| <span data-ttu-id="9dbaf-113">Określa ścieżkę, w której znajduje się pakiet.</span><span class="sxs-lookup"><span data-stu-id="9dbaf-113">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="9dbaf-114">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="9dbaf-114">ProductId</span></span>| <span data-ttu-id="9dbaf-115">Wskazuje identyfikator produktu, który unikatowo identyfikuje pakiet.</span><span class="sxs-lookup"><span data-stu-id="9dbaf-115">Indicates the product ID that uniquely identifies the package.</span></span>|
| <span data-ttu-id="9dbaf-116">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9dbaf-116">Arguments</span></span>| <span data-ttu-id="9dbaf-117">Wyświetla ciąg argumentów, które zostaną przekazane do pakietu, tak jak została podana.</span><span class="sxs-lookup"><span data-stu-id="9dbaf-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="9dbaf-118">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="9dbaf-118">Credential</span></span>| <span data-ttu-id="9dbaf-119">Umożliwia dostęp do pakietu zdalnego źródła.</span><span class="sxs-lookup"><span data-stu-id="9dbaf-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="9dbaf-120">Ta właściwość nie jest używana do zainstalowania pakietu.</span><span class="sxs-lookup"><span data-stu-id="9dbaf-120">This property is not used to install the package.</span></span> <span data-ttu-id="9dbaf-121">Pakiet jest zawsze instalowany w systemie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="9dbaf-121">The package is always installed on the local system.</span></span>|
| <span data-ttu-id="9dbaf-122">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="9dbaf-122">Ensure</span></span>| <span data-ttu-id="9dbaf-123">Wskazuje, czy pakiet jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="9dbaf-123">Indicates if the package is installed.</span></span> <span data-ttu-id="9dbaf-124">Ustaw tę właściwość na "Brak", upewnij się, że pakiet nie jest zainstalowany (lub odinstalować pakiet, jeśli jest zainstalowana).</span><span class="sxs-lookup"><span data-stu-id="9dbaf-124">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="9dbaf-125">Ustaw "Przedstawić" (wartość domyślna) upewnij się, że pakiet jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="9dbaf-125">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="9dbaf-126">Ścieżka dziennika</span><span class="sxs-lookup"><span data-stu-id="9dbaf-126">LogPath</span></span>| <span data-ttu-id="9dbaf-127">Określa pełną ścieżkę, w którym ma dostawcy, aby zapisać plik dziennika, aby zainstalować lub odinstalować pakiet.</span><span class="sxs-lookup"><span data-stu-id="9dbaf-127">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="9dbaf-128">dependsOn</span><span class="sxs-lookup"><span data-stu-id="9dbaf-128">DependsOn</span></span> | <span data-ttu-id="9dbaf-129">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="9dbaf-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="9dbaf-130">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest **ResourceName** i jej typ jest **ResourceType**, składnia za pomocą tej właściwości to "DependsOn ="[ResourceName ResourceType]"".</span><span class="sxs-lookup"><span data-stu-id="9dbaf-130">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|
| <span data-ttu-id="9dbaf-131">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="9dbaf-131">ReturnCode</span></span>| <span data-ttu-id="9dbaf-132">Wskazuje oczekiwany kod powrotny.</span><span class="sxs-lookup"><span data-stu-id="9dbaf-132">Indicates the expected return code.</span></span> <span data-ttu-id="9dbaf-133">Jeśli kod powrotu rzeczywiste nie odpowiada oczekiwanej wartości podane w tym miejscu konfiguracji spowoduje zwrócenie błędu.</span><span class="sxs-lookup"><span data-stu-id="9dbaf-133">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|

## <a name="example"></a><span data-ttu-id="9dbaf-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="9dbaf-134">Example</span></span>

<span data-ttu-id="9dbaf-135">W tym przykładzie jest uruchamiany Instalator MSI, który znajduje się w określonej ścieżce i ma identyfikator określonego produktu.</span><span class="sxs-lookup"><span data-stu-id="9dbaf-135">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```