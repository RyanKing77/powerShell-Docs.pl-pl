---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: Update-Module
ms.openlocfilehash: 89b0111eda4421606843f108dca90519b2c9379e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="update-module"></a><span data-ttu-id="00474-103">Update-Module</span><span class="sxs-lookup"><span data-stu-id="00474-103">Update-Module</span></span>

<span data-ttu-id="00474-104">Pobiera i instaluje najnowszą wersję określone moduły z galerii online na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="00474-104">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

## <a name="description"></a><span data-ttu-id="00474-105">Opis</span><span class="sxs-lookup"><span data-stu-id="00474-105">Description</span></span>

<span data-ttu-id="00474-106">Polecenie cmdlet Update-Module instaluje nowsza wersja modułu programu Windows PowerShell, który został zainstalowany z galerii online, uruchamiając modułu instalacji na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="00474-106">The Update-Module cmdlet installs a newer version of a Windows PowerShell module that was installed from the online gallery by running Install-Module on the local computer.</span></span>

<span data-ttu-id="00474-107">Domyślnie najnowsza wersja określony moduł w galerii online jest zainstalowany, chyba że zostanie wymagana wersja.</span><span class="sxs-lookup"><span data-stu-id="00474-107">By default, the newest version of the specified module available in online gallery is installed, unless you specify a required version.</span></span> <span data-ttu-id="00474-108">Możesz zaktualizować istniejący, zainstalowany moduł, określając nazwę modułu; Moduł aktualizacji wyszukuje $env: PSModulePath modułów, które chcesz zaktualizować.</span><span class="sxs-lookup"><span data-stu-id="00474-108">You can update an existing, installed module by specifying the name of the module; Update-Module searches $env:PSModulePath for the module that you want to update.</span></span>

<span data-ttu-id="00474-109">Uruchomienie modułu aktualizacji bez parametr Name aktualizuje wszystkie moduły, które mogą zostać zaktualizowane na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="00474-109">Running Update-Module without the Name parameter updates all modules that can be updated on the local computer.</span></span>

### <a name="notes"></a><span data-ttu-id="00474-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="00474-110">Notes</span></span>

- <span data-ttu-id="00474-111">To polecenie cmdlet jest uruchamiane w środowisku Windows PowerShell 3.0 ani nowszych wersji środowiska Windows PowerShell w systemie Windows 7 lub Windows 2008 R2 i nowszych wersjach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="00474-111">This cmdlet runs on Windows PowerShell 3.0 or later releases of Windows PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>
- <span data-ttu-id="00474-112">Jeśli moduł, który należy określić przy użyciu parametru Name nie został zainstalowany przy użyciu instalacji modułu, wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="00474-112">If the module that you specify with the Name parameter was not installed by using Install-Module, an error occurs.</span></span> <span data-ttu-id="00474-113">Moduł aktualizacji można uruchamiać tylko w modułach zainstalowanych z galerii online, uruchamiając instalacji modułu.</span><span class="sxs-lookup"><span data-stu-id="00474-113">You can only run Update-Module on modules that you installed from the online gallery by running Install-Module.</span></span>
- <span data-ttu-id="00474-114">Jeśli aktualizacja modułu próbuje zaktualizować pliki binarne, które są używane, aktualizacji modułu zwraca błąd, który identyfikuje procesy problem i informuje użytkownika, aby ponowić próbę aktualizacji modułu po zatrzymaniu procesów.</span><span class="sxs-lookup"><span data-stu-id="00474-114">If Update-Module attempts to update binaries that are in use, Update-Module returns an error that identifies the problem processes, and informs the user to retry Update-Module after stopping the processes.</span></span>
- <span data-ttu-id="00474-115">Na programu PowerShell w wersji 5.0 lub nowszej wersji podczas aktualizacji modułu aktualizacji modułu, dodaje najnowszej (lub został określony) wersji modułu, więc starszej i nowszych wersji są teraz side-by-side w tym samym katalogu.</span><span class="sxs-lookup"><span data-stu-id="00474-115">On PowerShell 5.0 or newer versions, when Update-Module updates a module, it adds the latest (or specified) version of the module, so the older and newer versions are now side-by-side in the same directory.</span></span> <span data-ttu-id="00474-116">Jest przydatne, to znaczy i wyświetlania przykładowe dane wyjściowe tych poleceń.</span><span class="sxs-lookup"><span data-stu-id="00474-116">It would be useful to say so and to show an example of the output from these commands.</span></span>


## <a name="cmdlet-syntax"></a><span data-ttu-id="00474-117">Składnia polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="00474-117">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Update-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="00474-118">Dokumentacja poleceń cmdlet pomocy online</span><span class="sxs-lookup"><span data-stu-id="00474-118">Cmdlet online help reference</span></span>

[<span data-ttu-id="00474-119">Update-Module</span><span class="sxs-lookup"><span data-stu-id="00474-119">Update-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398576)


## <a name="example-commands"></a><span data-ttu-id="00474-120">Przykładowe polecenia</span><span class="sxs-lookup"><span data-stu-id="00474-120">Example commands</span></span>

```powershell
PS C:\windows\system32> Update-Module -Name ContosoServer -RequiredVersion 1.5
PS C:\windows\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.0
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
PS C:\windows\system32> Update-Module -Name ContosoServer
PS C:\windows\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.8.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.8.1
Name : ContosoServer
Version : 2.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.0
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
```

### <a name="update-the-module-with-a-prerelease-version-requires--allowprerelease-flag"></a><span data-ttu-id="00474-121">Aktualizacji modułu z wersji wstępnej, wymaga flagi - AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="00474-121">Update the module with a prerelease version, requires -AllowPrerelease flag</span></span>
```powershell
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module

PS C:\windows\system32> Find-Module ContosoServer -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
3.0.0-alpha    ConstosoServer                      MSPSGallery          The PowerShell Contoso Server deployment tools...

PS C:\windows\system32> Update-Module -Name ContosoServer -AllowPrerelease
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
3.0.0-alpha ContosoServer MSPSGallery ContosoServer module

```


### <a name="update-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a><span data-ttu-id="00474-122">Zaktualizuj moduł TestDepWithNestedRequiredModules1 z zależności.</span><span class="sxs-lookup"><span data-stu-id="00474-122">Update the TestDepWithNestedRequiredModules1 module with dependencies.</span></span>
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module



```