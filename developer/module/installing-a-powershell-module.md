---
title: Instalowanie modułu programu PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: 7c2bfca50de4645676eafc01bbf23d9797e8b758
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082196"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="b03c0-102">Instalowanie modułu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="b03c0-102">Installing a PowerShell Module</span></span>

<span data-ttu-id="b03c0-103">Po utworzeniu modułu programu PowerShell, prawdopodobnie należy zainstalować moduł w systemie, aby inni użytkownicy mogą go używać.</span><span class="sxs-lookup"><span data-stu-id="b03c0-103">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="b03c0-104">Ogólnie rzecz biorąc to po prostu składa się z modułu pliki kopiowane (ie, psm1 lub zestawie binarnym, manifestu modułu i inne skojarzone pliki) do katalogu na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b03c0-104">Generally speaking, this simply consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="b03c0-105">Dla bardzo małym projektem może to być proste i polega na kopiowanie i wklejanie plików za pomocą Eksploratora Windows na pojedynczym komputerze zdalnym; Jednak w przypadku większych rozwiązań możesz korzystać z bardziej zaawansowanych procesu instalacji.</span><span class="sxs-lookup"><span data-stu-id="b03c0-105">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="b03c0-106">Niezależnie od tego, jak się dostać modułu do systemu programu PowerShell można użyć szereg technik, które umożliwi użytkownikom wyszukiwanie i korzystanie z modułów.</span><span class="sxs-lookup"><span data-stu-id="b03c0-106">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="b03c0-107">(Aby uzyskać więcej informacji, zobacz [zaimportowanie modułu PowerShell](./importing-a-powershell-module.md).) W związku z tym główny problem w przypadku instalacji jest zapewnienie środowiska PowerShell będzie można znaleźć modułu.</span><span class="sxs-lookup"><span data-stu-id="b03c0-107">(For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).) Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span>

<span data-ttu-id="b03c0-108">Ten temat zawiera następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="b03c0-108">This topic contains the following sections:</span></span>

- <span data-ttu-id="b03c0-109">Zasady dotyczące instalowania modułów</span><span class="sxs-lookup"><span data-stu-id="b03c0-109">Rules for Installing Modules</span></span>

- <span data-ttu-id="b03c0-110">Gdzie można zainstalować moduły</span><span class="sxs-lookup"><span data-stu-id="b03c0-110">Where to Install Modules</span></span>

- <span data-ttu-id="b03c0-111">Instalowanie wielu wersji modułu</span><span class="sxs-lookup"><span data-stu-id="b03c0-111">Installing Multiple Versions of a Module</span></span>

- <span data-ttu-id="b03c0-112">Wystąpił konflikt między nazwą polecenia obsługi</span><span class="sxs-lookup"><span data-stu-id="b03c0-112">Handling Command Name Conflicts</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="b03c0-113">Zasady dotyczące instalowania modułów</span><span class="sxs-lookup"><span data-stu-id="b03c0-113">Rules for Installing Modules</span></span>

<span data-ttu-id="b03c0-114">Poniższe informacje odnoszą się do wszystkich modułów, w tym moduły, które tworzysz własne użytkowania, moduły, które otrzymujesz pochodzące od innych firm i moduły, które możesz udostępnić innym osobom.</span><span class="sxs-lookup"><span data-stu-id="b03c0-114">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="b03c0-115">Zainstaluj moduły w PSModulePath</span><span class="sxs-lookup"><span data-stu-id="b03c0-115">Install Modules in PSModulePath</span></span>

<span data-ttu-id="b03c0-116">Jeśli to możliwe, należy zainstalować wszystkie moduły w ścieżce, która znajduje się w **PSModulePath** zmiennej środowiskowej lub ścieżka modułu, aby dodać **PSModulePath** wartości zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="b03c0-116">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="b03c0-117">**PSModulePath** zmienna środowiskowa ($Env: PSModulePath) zawiera lokalizacje modułów programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b03c0-117">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="b03c0-118">Polecenia cmdlet oparte na wartość tej zmiennej środowiskowej, aby znaleźć modułów.</span><span class="sxs-lookup"><span data-stu-id="b03c0-118">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="b03c0-119">Domyślnie **PSModulePath** wartości zmiennej środowiskowej zawiera następujące systemu i użytkownika modułu katalogów, ale można dodać do i edytować wartość.</span><span class="sxs-lookup"><span data-stu-id="b03c0-119">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="b03c0-120">$PSHome\Modules (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span><span class="sxs-lookup"><span data-stu-id="b03c0-120">$PSHome\Modules (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="b03c0-121">Ta lokalizacja jest zarezerwowana dla modułów, które są dostarczane z Windows.</span><span class="sxs-lookup"><span data-stu-id="b03c0-121">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="b03c0-122">Nie należy instalować modułów do tej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="b03c0-122">Do not install modules to this location.</span></span>

- <span data-ttu-id="b03c0-123">$Home\Documents\WindowsPowerShell\Modules (%UserProfile%\Documents\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="b03c0-123">$Home\Documents\WindowsPowerShell\Modules (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="b03c0-124">$Env: ProgramFiles\WindowsPowerShell\Modules (% ProgramFiles%\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="b03c0-124">$Env:ProgramFiles\WindowsPowerShell\Modules (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="b03c0-125">Aby uzyskać wartość **PSModulePath** zmiennej środowiskowej, użyj jednej z następujących poleceń.</span><span class="sxs-lookup"><span data-stu-id="b03c0-125">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="b03c0-126">Aby dodać ścieżkę modułu wartość **PSModulePath** zmiennej środowiskowej wartość, należy użyć następującego formatu polecenia.</span><span class="sxs-lookup"><span data-stu-id="b03c0-126">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="b03c0-127">Ten format używa **setenvironmentvariable nie zawiera** metody **System.Environment** klasy w celu zmiany niezależne od sesji **PSModulePath** środowiska Zmienna.</span><span class="sxs-lookup"><span data-stu-id="b03c0-127">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell

  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="b03c0-128">Po dodaniu ścieżki do **PSModulePath**, należy emisji komunikat środowiska o zmianie.</span><span class="sxs-lookup"><span data-stu-id="b03c0-128">Once you have added the path to **PSModulePath**, you should broadcast an environment message about the change.</span></span> <span data-ttu-id="b03c0-129">Zmianie rozgłaszania umożliwia innych aplikacji, takich jak powłoki wczytać zmiany.</span><span class="sxs-lookup"><span data-stu-id="b03c0-129">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="b03c0-130">Do emisji przeznaczonych jest zmiana, mają kodów instalacji produktu, Wyślij **WM_SETTINGCHANGE** komunikatu o `lParam` ustawiony na ciąg "Environment".</span><span class="sxs-lookup"><span data-stu-id="b03c0-130">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="b03c0-131">Pamiętaj wysłać wiadomość po kodzie instalacji modułu został zaktualizowany **PSModulePath**.</span><span class="sxs-lookup"><span data-stu-id="b03c0-131">Be sure to send the message after your module installation code has updated **PSModulePath**.</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="b03c0-132">Użyj nazwy katalogu poprawny modułu</span><span class="sxs-lookup"><span data-stu-id="b03c0-132">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="b03c0-133">Moduł "sformułowany" jest to moduł, który jest przechowywany w katalogu, który ma taką samą nazwę jak podstawowa nazwa co najmniej jeden plik w katalogu modułu.</span><span class="sxs-lookup"><span data-stu-id="b03c0-133">A "well-formed" module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="b03c0-134">Jeśli moduł nie jest poprawnie sformułowany, programu Windows PowerShell nie rozpoznaje je jako moduł.</span><span class="sxs-lookup"><span data-stu-id="b03c0-134">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="b03c0-135">"Nazwa podstawowa" pliku jest nazwę bez rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="b03c0-135">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="b03c0-136">W module poprawnie sformułowany nazwę katalogu, który zawiera pliki modułu musi odpowiadać nazwa podstawowa co najmniej jeden plik w module.</span><span class="sxs-lookup"><span data-stu-id="b03c0-136">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="b03c0-137">Na przykład w module Fabrikam przykładowe katalogu, który zawiera pliki modułu nosi nazwę "Fabrikam", a nazwa podstawowa "Fabrikam" ma co najmniej jeden plik.</span><span class="sxs-lookup"><span data-stu-id="b03c0-137">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="b03c0-138">W takim przypadku zarówno Fabrikam.psd1 Fabrikam.dll się nazwa podstawowa "Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="b03c0-138">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="b03c0-139">Efekt niepoprawne instalacji</span><span class="sxs-lookup"><span data-stu-id="b03c0-139">Effect of Incorrect Installation</span></span>

<span data-ttu-id="b03c0-140">Jeśli moduł nie jest poprawnie sformułowany, a jego lokalizacja jest niedostępna w wartości **PSModulePath** zmiennej środowiskowej, odnajdywania podstawowe funkcje programu Windows PowerShell, podobny do następującego nie będą działać.</span><span class="sxs-lookup"><span data-stu-id="b03c0-140">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="b03c0-141">Funkcja automatycznego modułu ładowania nie może automatycznie zaimportować moduł.</span><span class="sxs-lookup"><span data-stu-id="b03c0-141">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="b03c0-142">`ListAvailable` Parametru [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) polecenie cmdlet nie można odnaleźć modułu.</span><span class="sxs-lookup"><span data-stu-id="b03c0-142">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="b03c0-143">[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) polecenie cmdlet nie można odnaleźć modułu.</span><span class="sxs-lookup"><span data-stu-id="b03c0-143">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="b03c0-144">Aby zaimportować moduł, należy podać pełną ścieżkę do pliku modułu głównego lub plik manifestu modułu.</span><span class="sxs-lookup"><span data-stu-id="b03c0-144">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="b03c0-145">Dodatkowe funkcje, takie jak następujące polecenie, nie działają, chyba że moduł są importowane do sesji.</span><span class="sxs-lookup"><span data-stu-id="b03c0-145">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="b03c0-146">W modułach sformułowany **PSModulePath** zmiennej środowiskowej, te funkcje działają, nawet wtedy, gdy moduł nie są importowane do sesji.</span><span class="sxs-lookup"><span data-stu-id="b03c0-146">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="b03c0-147">[Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) polecenie cmdlet nie może odnaleźć poleceń w module.</span><span class="sxs-lookup"><span data-stu-id="b03c0-147">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="b03c0-148">[Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) i [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) poleceń cmdlet nie można zaktualizować ani zapisać Pomoc dla modułu.</span><span class="sxs-lookup"><span data-stu-id="b03c0-148">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="b03c0-149">[Polecenie Pokaż](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) polecenie cmdlet nie może znaleźć i wyświetlić poleceń w module.</span><span class="sxs-lookup"><span data-stu-id="b03c0-149">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="b03c0-150">Brakuje poleceń w module `Show-Command` okna w Windows PowerShell zintegrowane Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="b03c0-150">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="b03c0-151">Gdzie można zainstalować moduły</span><span class="sxs-lookup"><span data-stu-id="b03c0-151">Where to Install Modules</span></span>

<span data-ttu-id="b03c0-152">W tej sekcji opisano miejsca w systemie plików, aby zainstalować moduły programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b03c0-152">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="b03c0-153">Lokalizacja zależy od tego, jak moduł jest używany.</span><span class="sxs-lookup"><span data-stu-id="b03c0-153">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="b03c0-154">Instalowanie modułów dla określonego użytkownika</span><span class="sxs-lookup"><span data-stu-id="b03c0-154">Installing Modules for a Specific User</span></span>

<span data-ttu-id="b03c0-155">Jeśli możesz utworzyć własny moduł lub uzyskać modułu z drugiej strony, takich jak witryny internetowej społeczności programu Windows PowerShell, i chcesz, aby moduł, który ma być dostępny dla tego konta użytkownika, należy zainstalować moduł, w katalogu moduły specyficzne dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b03c0-155">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

```
$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

<span data-ttu-id="b03c0-156">Katalog moduły specyficzne dla użytkownika jest dodawany do wartości **PSModulePath** zmiennej środowiskowej domyślnie.</span><span class="sxs-lookup"><span data-stu-id="b03c0-156">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="b03c0-157">Instalowanie modułów dla wszystkich użytkowników w folderze Program Files</span><span class="sxs-lookup"><span data-stu-id="b03c0-157">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="b03c0-158">Jeśli chcesz, aby moduł mają być dostępne dla wszystkich kont użytkowników na komputerze, należy zainstalować moduł, w lokalizacji plików programów.</span><span class="sxs-lookup"><span data-stu-id="b03c0-158">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

```
$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

> [!NOTE]
> <span data-ttu-id="b03c0-159">Lokalizacja plików programu zostanie dodany do wartości zmiennej środowiskowej PSModulePath domyślnie w programie Windows PowerShell 4.0 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="b03c0-159">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="b03c0-160">We wcześniejszych wersjach programu Windows PowerShell, można ręcznie utworzyć ((%ProgramFiles%\WindowsPowerShell\Modules) lokalizacji Program Files i Dodaj tę ścieżkę do zmiennej środowiskowej PSModulePath, zgodnie z powyższym opisem.</span><span class="sxs-lookup"><span data-stu-id="b03c0-160">For earlier versions of Windows PowerShell, you can manually create the Program Files location ((%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="b03c0-161">Instalowanie modułów w katalogu produktów</span><span class="sxs-lookup"><span data-stu-id="b03c0-161">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="b03c0-162">Jeśli przekazujesz modułu do innych stron, użyj domyślna lokalizacja plików programu opisanych powyżej, lub Utwórz własne podkatalogu specyficzny dla firmy lub specyficzne dla produktu z katalogu % ProgramFiles %.</span><span class="sxs-lookup"><span data-stu-id="b03c0-162">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="b03c0-163">Na przykład fikcyjnej firmy Fabrikam technologii dostarcza modułu programu Windows PowerShell dla ich firmy Fabrikam, Menedżer produktu.</span><span class="sxs-lookup"><span data-stu-id="b03c0-163">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="b03c0-164">Ich Instalator modułu tworzy podkatalog modułów w podkatalogu Fabrikam Menedżera produktu.</span><span class="sxs-lookup"><span data-stu-id="b03c0-164">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="b03c0-165">Aby włączyć funkcje odnajdywania modułu programu Windows PowerShell można znaleźć modułu firmy Fabrikam, Instalator modułu Fabrikam dodaje wartość lokalizacja modułu **PSModulePath** zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="b03c0-165">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += "C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="b03c0-166">Instalowanie modułów w katalogu wspólnych plików</span><span class="sxs-lookup"><span data-stu-id="b03c0-166">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="b03c0-167">Jeśli moduł jest używany przez wiele składników produktu lub przez wiele wersji produktu, należy zainstalować moduł w podkatalogu podkatalogu Files\Modules %ProgramFiles%\Common specyficzne dla modułu.</span><span class="sxs-lookup"><span data-stu-id="b03c0-167">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="b03c0-168">W poniższym przykładzie moduł Fabrikam jest zainstalowany w podkatalogu Fabrikam podkatalogu Files\Modules %ProgramFiles%\Common.</span><span class="sxs-lookup"><span data-stu-id="b03c0-168">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span> <span data-ttu-id="b03c0-169">Należy pamiętać, że każdy moduł znajduje się w jego własnej podkatalogu w podkatalogu modułów.</span><span class="sxs-lookup"><span data-stu-id="b03c0-169">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)

```

<span data-ttu-id="b03c0-170">Następnie Instalator gwarantuje wartość **PSModulePath** zmienna środowiskowa zawiera ścieżkę podkatalogu wspólnego moduły plików.</span><span class="sxs-lookup"><span data-stu-id="b03c0-170">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="b03c0-171">Instalowanie wielu wersji modułu</span><span class="sxs-lookup"><span data-stu-id="b03c0-171">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="b03c0-172">Aby zainstalować wiele wersji tego samego modułu, użyj następującej procedury.</span><span class="sxs-lookup"><span data-stu-id="b03c0-172">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="b03c0-173">Utwórz katalog dla każdej wersji modułu.</span><span class="sxs-lookup"><span data-stu-id="b03c0-173">Create a directory for each version of the module.</span></span> <span data-ttu-id="b03c0-174">Numer wersji należy uwzględnić w nazwie katalogu.</span><span class="sxs-lookup"><span data-stu-id="b03c0-174">Include the version number in the directory name.</span></span>

2. <span data-ttu-id="b03c0-175">Tworzenie manifestu modułu dla każdej wersji modułu.</span><span class="sxs-lookup"><span data-stu-id="b03c0-175">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="b03c0-176">W wartości **ModuleVersion** klucza w manifeście, wprowadź numer wersji modułu.</span><span class="sxs-lookup"><span data-stu-id="b03c0-176">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="b03c0-177">Zapisz plik manifestu (psd1), w tym katalogu specyficzny dla wersji modułu.</span><span class="sxs-lookup"><span data-stu-id="b03c0-177">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>

3. <span data-ttu-id="b03c0-178">Dodaj ścieżka folderu głównego modułu wartość **PSModulePath** zmiennej środowiskowej, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="b03c0-178">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="b03c0-179">Aby zaimportować określoną wersję modułu, można użyć użytkownik końcowy `MinimumVersion` lub `RequiredVersion` parametry [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b03c0-179">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="b03c0-180">Na przykład jeśli moduł Fabrikam jest dostępny w wersji 8.0 i 9.0, struktura katalogów modułu Fabrikam może wyglądać w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="b03c0-180">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

<span data-ttu-id="b03c0-181">Instalator dodaje obu ścieżek modułu do **PSModulePath** wartości zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="b03c0-181">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="b03c0-182">Po zakończeniu tych kroków **ListAvailable** parametru [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) polecenie cmdlet pobiera oba moduły firmy Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="b03c0-182">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="b03c0-183">Aby zaimportować konkretnym module, użyj `MinimumVersion` lub `RequiredVersion` parametry [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b03c0-183">To import a particular module, use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="b03c0-184">Jeśli oba moduły są importowane do tej samej sesji i moduły zawierają polecenia cmdlet, za pomocą tej samej nazwy, polecenia cmdlet, które są importowane ostatnio obowiązują w sesji.</span><span class="sxs-lookup"><span data-stu-id="b03c0-184">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="b03c0-185">Wystąpił konflikt między nazwą polecenia obsługi</span><span class="sxs-lookup"><span data-stu-id="b03c0-185">Handling Command Name Conflicts</span></span>

<span data-ttu-id="b03c0-186">Konfliktom nazw poleceń może wystąpić, gdy polecenia, które eksportuje modułu mają taką samą nazwę jak polecenia w sesji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b03c0-186">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="b03c0-187">W przypadku sesji zawiera dwa polecenia, które mają taką samą nazwę, programu Windows PowerShell działa typ polecenia, który ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="b03c0-187">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="b03c0-188">Gdy sesja zawiera dwa polecenia, które mają taką samą nazwę i ten sam typ, programu Windows PowerShell uruchamia polecenia, który został dodany ostatnio do sesji.</span><span class="sxs-lookup"><span data-stu-id="b03c0-188">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="b03c0-189">Aby uruchomić polecenie, które nie jest uruchamiane domyślnie, użytkownicy mogą polecenia Zakwalifikuj nazwę przez określenie z nazwą modułu.</span><span class="sxs-lookup"><span data-stu-id="b03c0-189">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="b03c0-190">Na przykład, jeśli sesja zawiera `Get-Date` funkcji i `Get-Date` funkcja domyślnie uruchamia polecenie cmdlet programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b03c0-190">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="b03c0-191">Aby uruchomić polecenia cmdlet, należy poprzedzić polecenie nazwę modułu, takie jak:</span><span class="sxs-lookup"><span data-stu-id="b03c0-191">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="b03c0-192">Aby zapobiec konfliktom nazw, można użyć autorzy modułów **DefaultCommandPrefix** klucza w manifeście modułu do określania prefiksu rzeczownik dla wszystkich poleceń wyeksportowane z modułu.</span><span class="sxs-lookup"><span data-stu-id="b03c0-192">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="b03c0-193">Użytkownicy mogą używać **prefiks** parametru `Import-Module` polecenia cmdlet, aby używać alternatywnego prefiks.</span><span class="sxs-lookup"><span data-stu-id="b03c0-193">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="b03c0-194">Wartość **prefiksu** parametru mają pierwszeństwo przed wartością **DefaultCommandPrefix** klucza.</span><span class="sxs-lookup"><span data-stu-id="b03c0-194">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="b03c0-195">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b03c0-195">See Also</span></span>

[<span data-ttu-id="b03c0-196">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="b03c0-196">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="b03c0-197">Pisanie modułu programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b03c0-197">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
