---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób DSC pakietu
ms.openlocfilehash: 9285df71a303c9a53dd50d450272575a64e962e7
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268674"
---
# <a name="dsc-package-resource"></a><span data-ttu-id="aaa09-103">Zasób DSC pakietu</span><span class="sxs-lookup"><span data-stu-id="aaa09-103">DSC Package Resource</span></span>

<span data-ttu-id="aaa09-104">_Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="aaa09-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="aaa09-105">**Pakietu** zasobów w Windows PowerShell Desired State Configuration (DSC) udostępnia mechanizm do zainstalowania lub odinstalowania pakietów, takie jak pakiety Instalatora Windows i setup.exe, w węźle docelowym.</span><span class="sxs-lookup"><span data-stu-id="aaa09-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="aaa09-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="aaa09-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="aaa09-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="aaa09-107">Properties</span></span>

| <span data-ttu-id="aaa09-108">Właściwość</span><span class="sxs-lookup"><span data-stu-id="aaa09-108">Property</span></span> | <span data-ttu-id="aaa09-109">Opis</span><span class="sxs-lookup"><span data-stu-id="aaa09-109">Description</span></span> |
| --- | --- |
| <span data-ttu-id="aaa09-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="aaa09-110">Name</span></span>| <span data-ttu-id="aaa09-111">Określa nazwę pakietu, dla którego chcesz zapewnić określonego stanu.</span><span class="sxs-lookup"><span data-stu-id="aaa09-111">Indicates the name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="aaa09-112">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="aaa09-112">Path</span></span>| <span data-ttu-id="aaa09-113">Wskazuje ścieżkę, w której znajduje się pakiet.</span><span class="sxs-lookup"><span data-stu-id="aaa09-113">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="aaa09-114">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="aaa09-114">ProductId</span></span>| <span data-ttu-id="aaa09-115">Określa identyfikator produktu, który unikatowo identyfikuje pakiet.</span><span class="sxs-lookup"><span data-stu-id="aaa09-115">Indicates the product ID that uniquely identifies the package.</span></span>|
| <span data-ttu-id="aaa09-116">Argumenty</span><span class="sxs-lookup"><span data-stu-id="aaa09-116">Arguments</span></span>| <span data-ttu-id="aaa09-117">Wyświetla listę ciągów argumentów, które zostaną przekazane do pakietu dokładnie zgodnie z postanowieniami.</span><span class="sxs-lookup"><span data-stu-id="aaa09-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="aaa09-118">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="aaa09-118">Credential</span></span>| <span data-ttu-id="aaa09-119">Umożliwia dostęp do pakietu zdalnego źródła.</span><span class="sxs-lookup"><span data-stu-id="aaa09-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="aaa09-120">Ta właściwość nie jest używana do zainstalowania pakietu.</span><span class="sxs-lookup"><span data-stu-id="aaa09-120">This property is not used to install the package.</span></span> <span data-ttu-id="aaa09-121">Pakiet jest zawsze instalowany w systemie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="aaa09-121">The package is always installed on the local system.</span></span>|
| <span data-ttu-id="aaa09-122">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="aaa09-122">Ensure</span></span>| <span data-ttu-id="aaa09-123">Wskazuje, czy zainstalowano pakiet.</span><span class="sxs-lookup"><span data-stu-id="aaa09-123">Indicates if the package is installed.</span></span> <span data-ttu-id="aaa09-124">Ustaw tę właściwość na "Brak", upewnij się, że nie zainstalowano pakiet (lub odinstalować pakiet, jeśli jest zainstalowana).</span><span class="sxs-lookup"><span data-stu-id="aaa09-124">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="aaa09-125">Ustaw dla niej "Przedstawia" (wartość domyślna) upewnij się, że pakiet jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="aaa09-125">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="aaa09-126">Ścieżka dziennika</span><span class="sxs-lookup"><span data-stu-id="aaa09-126">LogPath</span></span>| <span data-ttu-id="aaa09-127">Określa pełną ścieżkę, której chcesz dostawcę Aby zapisać plik dziennika, aby zainstalować lub odinstalować pakiet.</span><span class="sxs-lookup"><span data-stu-id="aaa09-127">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="aaa09-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="aaa09-128">DependsOn</span></span> | <span data-ttu-id="aaa09-129">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="aaa09-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="aaa09-130">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest **ResourceName** a jej typ jest **ResourceType**, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="aaa09-130">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="aaa09-131">Kod zwrotny</span><span class="sxs-lookup"><span data-stu-id="aaa09-131">ReturnCode</span></span>| <span data-ttu-id="aaa09-132">Wskazuje oczekiwany kod powrotny.</span><span class="sxs-lookup"><span data-stu-id="aaa09-132">Indicates the expected return code.</span></span> <span data-ttu-id="aaa09-133">Jeśli rzeczywiste zwróci kod nie odpowiada oczekiwanej wartości zostanie podany tutaj, konfiguracja zwróci błąd.</span><span class="sxs-lookup"><span data-stu-id="aaa09-133">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|

## <a name="example"></a><span data-ttu-id="aaa09-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="aaa09-134">Example</span></span>

<span data-ttu-id="aaa09-135">W tym przykładzie jest uruchamiany Instalator MSI, który znajduje się w określonej ścieżce i ma identyfikator określonego produktu.</span><span class="sxs-lookup"><span data-stu-id="aaa09-135">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

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