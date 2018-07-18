---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób DSC pakietu
ms.openlocfilehash: 3046ba7d57776a996a0b917348a0e863db6cd0c8
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093807"
---
# <a name="dsc-package-resource"></a><span data-ttu-id="ccdf1-103">Zasób DSC pakietu</span><span class="sxs-lookup"><span data-stu-id="ccdf1-103">DSC Package Resource</span></span>

> <span data-ttu-id="ccdf1-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ccdf1-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="ccdf1-105">**Pakietu** zasobów w Windows PowerShell Desired State Configuration (DSC) udostępnia mechanizm do zainstalowania lub odinstalowania pakietów, takie jak pakiety Instalatora Windows i setup.exe, w węźle docelowym.</span><span class="sxs-lookup"><span data-stu-id="ccdf1-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="ccdf1-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ccdf1-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="ccdf1-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="ccdf1-107">Properties</span></span>

|  <span data-ttu-id="ccdf1-108">Właściwość</span><span class="sxs-lookup"><span data-stu-id="ccdf1-108">Property</span></span>  |  <span data-ttu-id="ccdf1-109">Opis</span><span class="sxs-lookup"><span data-stu-id="ccdf1-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="ccdf1-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="ccdf1-110">Name</span></span>| <span data-ttu-id="ccdf1-111">Określa nazwę pakietu, dla którego chcesz zapewnić określonego stanu.</span><span class="sxs-lookup"><span data-stu-id="ccdf1-111">Indicates the name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="ccdf1-112">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="ccdf1-112">Path</span></span>| <span data-ttu-id="ccdf1-113">Wskazuje ścieżkę, w której znajduje się pakiet.</span><span class="sxs-lookup"><span data-stu-id="ccdf1-113">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="ccdf1-114">Identyfikator produktu</span><span class="sxs-lookup"><span data-stu-id="ccdf1-114">ProductId</span></span>| <span data-ttu-id="ccdf1-115">Określa identyfikator produktu, który unikatowo identyfikuje pakiet.</span><span class="sxs-lookup"><span data-stu-id="ccdf1-115">Indicates the product ID that uniquely identifies the package.</span></span>|
| <span data-ttu-id="ccdf1-116">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ccdf1-116">Arguments</span></span>| <span data-ttu-id="ccdf1-117">Wyświetla listę ciągów argumentów, które zostaną przekazane do pakietu dokładnie zgodnie z postanowieniami.</span><span class="sxs-lookup"><span data-stu-id="ccdf1-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="ccdf1-118">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="ccdf1-118">Credential</span></span>| <span data-ttu-id="ccdf1-119">Umożliwia dostęp do pakietu zdalnego źródła.</span><span class="sxs-lookup"><span data-stu-id="ccdf1-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="ccdf1-120">Ta właściwość nie jest używana do zainstalowania pakietu.</span><span class="sxs-lookup"><span data-stu-id="ccdf1-120">This property is not used to install the package.</span></span> <span data-ttu-id="ccdf1-121">Pakiet jest zawsze instalowany w systemie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="ccdf1-121">The package is always installed on the local system.</span></span>|
| <span data-ttu-id="ccdf1-122">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="ccdf1-122">Ensure</span></span>| <span data-ttu-id="ccdf1-123">Wskazuje, czy zainstalowano pakiet.</span><span class="sxs-lookup"><span data-stu-id="ccdf1-123">Indicates if the package is installed.</span></span> <span data-ttu-id="ccdf1-124">Ustaw tę właściwość na "Brak", upewnij się, że nie zainstalowano pakiet (lub odinstalować pakiet, jeśli jest zainstalowana).</span><span class="sxs-lookup"><span data-stu-id="ccdf1-124">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="ccdf1-125">Ustaw dla niej "Przedstawia" (wartość domyślna) upewnij się, że pakiet jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="ccdf1-125">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="ccdf1-126">Ścieżka dziennika</span><span class="sxs-lookup"><span data-stu-id="ccdf1-126">LogPath</span></span>| <span data-ttu-id="ccdf1-127">Określa pełną ścieżkę, której chcesz dostawcę Aby zapisać plik dziennika, aby zainstalować lub odinstalować pakiet.</span><span class="sxs-lookup"><span data-stu-id="ccdf1-127">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="ccdf1-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ccdf1-128">DependsOn</span></span> | <span data-ttu-id="ccdf1-129">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="ccdf1-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ccdf1-130">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest **ResourceName** a jej typ jest **ResourceType**, składnia przy użyciu tej właściwości to "DependsOn ="[ ResourceName ResourceType]"".</span><span class="sxs-lookup"><span data-stu-id="ccdf1-130">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|
| <span data-ttu-id="ccdf1-131">Kod zwrotny</span><span class="sxs-lookup"><span data-stu-id="ccdf1-131">ReturnCode</span></span>| <span data-ttu-id="ccdf1-132">Wskazuje oczekiwany kod powrotny.</span><span class="sxs-lookup"><span data-stu-id="ccdf1-132">Indicates the expected return code.</span></span> <span data-ttu-id="ccdf1-133">Jeśli rzeczywiste zwróci kod nie odpowiada oczekiwanej wartości zostanie podany tutaj, konfiguracja zwróci błąd.</span><span class="sxs-lookup"><span data-stu-id="ccdf1-133">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|

## <a name="example"></a><span data-ttu-id="ccdf1-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccdf1-134">Example</span></span>

<span data-ttu-id="ccdf1-135">W tym przykładzie jest uruchamiany Instalator MSI, który znajduje się w określonej ścieżce i ma identyfikator określonego produktu.</span><span class="sxs-lookup"><span data-stu-id="ccdf1-135">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

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