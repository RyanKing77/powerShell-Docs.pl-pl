---
title: Modyfikowanie ścieżki instalacji PSModulePath | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082213"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="5f5f8-102">Modyfikowanie ścieżki instalacji PSModulePath</span><span class="sxs-lookup"><span data-stu-id="5f5f8-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="5f5f8-103">`PSModulePath` Zmiennej środowiskowej przechowuje ścieżki do lokalizacji modułów, które są zainstalowane na dysku.</span><span class="sxs-lookup"><span data-stu-id="5f5f8-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="5f5f8-104">Programu Windows PowerShell korzysta z tej zmiennej do zlokalizowania modułów, gdy użytkownik nie określi Pełna ścieżka do modułu.</span><span class="sxs-lookup"><span data-stu-id="5f5f8-104">Windows PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="5f5f8-105">Ścieżki w tej zmiennej są przeszukiwane w kolejności, w jakiej są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="5f5f8-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="5f5f8-106">Po uruchomieniu programu Windows PowerShell `PSModulePath` jest tworzona jako zmienna środowiskowa z następującą wartością domyślną: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="5f5f8-106">When Windows PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="5f5f8-107">Aby wyświetlić zmiennej PSModulePath</span><span class="sxs-lookup"><span data-stu-id="5f5f8-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="5f5f8-108">Aby wyświetlić ścieżek, które są określone w `PSModulePath` zmiennej, wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="5f5f8-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="5f5f8-109">Aby dodać lokalizacje do zmiennej PSModulePath</span><span class="sxs-lookup"><span data-stu-id="5f5f8-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="5f5f8-110">Aby dodać ścieżki do zmiennej, użyj jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="5f5f8-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="5f5f8-111">Aby dodać wartości tymczasowej, która jest dostępna tylko dla bieżącej sesji, uruchom następujące polecenie w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="5f5f8-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- <span data-ttu-id="5f5f8-112">Aby dodać wartością stałą, która jest dostępna, przy każdym otwarciu sesji, należy dodać następujące polecenie do profilu programu Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5f5f8-112">To add a persistent value that is available whenever a session is opened, add the following command to a Windows PowerShell profile:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  <span data-ttu-id="5f5f8-113">Aby uzyskać więcej informacji na temat profilów, zobacz [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) w bibliotece Microsoft TechNet.</span><span class="sxs-lookup"><span data-stu-id="5f5f8-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in the Microsoft TechNet library.</span></span>

- <span data-ttu-id="5f5f8-114">Aby dodać zmienną trwałego w rejestrze, Utwórz nową zmienną środowiskową użytkownika o nazwie `PSModulePath` za pomocą edytora zmiennych środowiskowych w **właściwości systemu** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="5f5f8-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="5f5f8-115">Aby dodać zmienną trwałych, za pomocą skryptu, użyj **setenvironmentvariable nie zawiera** metody w klasie środowiska.</span><span class="sxs-lookup"><span data-stu-id="5f5f8-115">To add a persistent variable by using a script, use the **SetEnvironmentVariable** method on the Environment class.</span></span> <span data-ttu-id="5f5f8-116">Na przykład poniższy skrypt dodaje "C:\Program Files\Fabrikam\Module ścieżkę do wartości zmiennej środowiskowej PSModulePath dla komputera.</span><span class="sxs-lookup"><span data-stu-id="5f5f8-116">For example, the following script adds the "C:\Program Files\Fabrikam\Module path to the value of the PSModulePath environment variable for the computer.</span></span> <span data-ttu-id="5f5f8-117">Aby dodać ścieżkę do zmiennej środowiskowej PSModulePath użytkownika, Ustaw element docelowy "User".</span><span class="sxs-lookup"><span data-stu-id="5f5f8-117">To add the path to the user PSModulePath environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="5f5f8-118">Usuwanie lokalizacji PSModulePath</span><span class="sxs-lookup"><span data-stu-id="5f5f8-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="5f5f8-119">Możesz usunąć ścieżki ze zmiennej za pomocą metod podobnych: na przykład `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` spowoduje usunięcie **c:\ModulePath** ścieżki z bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="5f5f8-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f5f8-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f5f8-120">See Also</span></span>

[<span data-ttu-id="5f5f8-121">Pisanie modułu programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f5f8-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
