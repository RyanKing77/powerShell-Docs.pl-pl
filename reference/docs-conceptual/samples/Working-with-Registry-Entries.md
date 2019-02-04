---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Praca z wpisami rejestru
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: 8483b6f98739697b24a13055dfffbc7b5bacc2cc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686810"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="e7118-103">Praca z wpisami rejestru</span><span class="sxs-lookup"><span data-stu-id="e7118-103">Working with Registry Entries</span></span>

<span data-ttu-id="e7118-104">Ponieważ wpisy rejestru są właściwości kluczy, a w efekcie nie mogą być bezpośrednio przeglądane, musimy wykonać nieco innego podejścia, podczas pracy z nimi.</span><span class="sxs-lookup"><span data-stu-id="e7118-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

### <a name="listing-registry-entries"></a><span data-ttu-id="e7118-105">Wyświetlanie listy wpisów rejestru</span><span class="sxs-lookup"><span data-stu-id="e7118-105">Listing Registry Entries</span></span>

<span data-ttu-id="e7118-106">Istnieje wiele różnych sposobów, aby zbadać wpisów rejestru.</span><span class="sxs-lookup"><span data-stu-id="e7118-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="e7118-107">Najprostszym sposobem jest uzyskanie nazw właściwości skojarzone z kluczem.</span><span class="sxs-lookup"><span data-stu-id="e7118-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="e7118-108">Na przykład, aby zobaczyć nazwy wpisów w kluczu rejestru `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, użyj `Get-Item`.</span><span class="sxs-lookup"><span data-stu-id="e7118-108">For example, to see the names of the entries in the registry key `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, use `Get-Item`.</span></span> <span data-ttu-id="e7118-109">Klucze rejestru mają właściwość o nazwie ogólne "Właściwości", znajduje się lista wpisów rejestru w kluczu.</span><span class="sxs-lookup"><span data-stu-id="e7118-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span>
<span data-ttu-id="e7118-110">Następujące polecenie wybiera właściwość właściwości i rozwija elementów, dlatego, że są one wyświetlane na liście:</span><span class="sxs-lookup"><span data-stu-id="e7118-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```powershell
Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion |
  Select-Object -ExpandProperty Property
```

```Output
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="e7118-111">Aby wyświetlić wpisy rejestru w postaci bardziej czytelny, użyj `Get-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="e7118-111">To view the registry entries in a more readable form, use `Get-ItemProperty`:</span></span>

```powershell
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

```Output
PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

<span data-ttu-id="e7118-112">Właściwości związane z programu Windows PowerShell dla klucza są wszystkie prefiks "PS", takich jak **PSPath**, **PSParentPath**, **PSChildName**, i **PSProvider** .</span><span class="sxs-lookup"><span data-stu-id="e7118-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="e7118-113">Możesz użyć `*.*` notacji odwoływania się do bieżącej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="e7118-113">You can use the `*.*` notation for referring to the current location.</span></span> <span data-ttu-id="e7118-114">Możesz użyć `Set-Location` można zmienić na **CurrentVersion** rejestru kontenera pierwszy:</span><span class="sxs-lookup"><span data-stu-id="e7118-114">You can use `Set-Location` to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="e7118-115">Alternatywnie, można użyć wbudowanych PSDrive HKLM z `Set-Location`:</span><span class="sxs-lookup"><span data-stu-id="e7118-115">Alternatively, you can use the built-in HKLM PSDrive with `Set-Location`:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="e7118-116">Następnie można użyć `*.*` notacji dla bieżącej lokalizacji wyświetlić listę właściwości bez określenia pełnej ścieżki:</span><span class="sxs-lookup"><span data-stu-id="e7118-116">You can then use the `*.*` notation for the current location to list the properties without specifying a full path:</span></span>

```powershell
Get-ItemProperty -Path .
```

```Output
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="e7118-117">Ścieżka rozszerzenia działa tak samo, jak w systemie plików, dzięki czemu z tej lokalizacji można uzyskać **zmieniona właściwość elementu** dla `HKLM:\SOFTWARE\Microsoft\Windows\Help` przy użyciu `Get-ItemProperty -Path ..\Help`.</span><span class="sxs-lookup"><span data-stu-id="e7118-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for `HKLM:\SOFTWARE\Microsoft\Windows\Help` by using `Get-ItemProperty -Path ..\Help`.</span></span>

### <a name="getting-a-single-registry-entry"></a><span data-ttu-id="e7118-118">Pobieranie jednego wpisu rejestru</span><span class="sxs-lookup"><span data-stu-id="e7118-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="e7118-119">Jeśli chcesz pobrać określonego wpisu w kluczu rejestru, można użyć jednej z kilku możliwych podejść.</span><span class="sxs-lookup"><span data-stu-id="e7118-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="e7118-120">W tym przykładzie wyszukuje wartość **DevicePath** w `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span><span class="sxs-lookup"><span data-stu-id="e7118-120">This example finds the value of **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span></span>

<span data-ttu-id="e7118-121">Przy użyciu `Get-ItemProperty`, użyj **ścieżki** parametru do określenia nazwy klucza i **nazwa** parametru, aby określić nazwę **DevicePath** wpisu.</span><span class="sxs-lookup"><span data-stu-id="e7118-121">Using `Get-ItemProperty`, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath
```

```Output
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

<span data-ttu-id="e7118-122">To polecenie zwraca standardowe właściwości programu Windows PowerShell, jak również **DevicePath** właściwości.</span><span class="sxs-lookup"><span data-stu-id="e7118-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="e7118-123">Mimo że `Get-ItemProperty` ma **filtru**, **Include**, i **wykluczyć** parametrów, nie można ich używać do filtrowania według nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="e7118-123">Although `Get-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="e7118-124">Te parametry można znaleźć klucze rejestru, które są ścieżki elementów ale nie wpisów rejestru.</span><span class="sxs-lookup"><span data-stu-id="e7118-124">These parameters refer to registry keys, which are item paths and not registry entries.</span></span> <span data-ttu-id="e7118-125">Wpisy rejestru, które są właściwości elementu.</span><span class="sxs-lookup"><span data-stu-id="e7118-125">Registry entries which are item properties.</span></span>

<span data-ttu-id="e7118-126">Innym rozwiązaniem jest za pomocą narzędzia wiersza polecenia Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="e7118-126">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="e7118-127">Aby uzyskać pomoc dotyczącą reg.exe, wpisz `reg.exe /?` polecenie w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="e7118-127">For help with reg.exe, type `reg.exe /?` at a command prompt.</span></span> <span data-ttu-id="e7118-128">Aby znaleźć wpisu DevicePath, użyj reg.exe, jak pokazano w następującym poleceniu:</span><span class="sxs-lookup"><span data-stu-id="e7118-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="e7118-129">Można również użyć **WshShell** obiekt COM, jak również znaleźć niektóre wpisy rejestru, mimo że ta metoda nie działa z dużych danych binarnych lub nazwy wpisów rejestru, które obejmują znaki, takie jak "\\").</span><span class="sxs-lookup"><span data-stu-id="e7118-129">You can also use the **WshShell** COM object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="e7118-130">Dołącz nazwę właściwości ścieżki elementu z \\ separatora:</span><span class="sxs-lookup"><span data-stu-id="e7118-130">Append the property name to the item path with a \\ separator:</span></span>

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

### <a name="setting-a-single-registry-entry"></a><span data-ttu-id="e7118-131">Ustawianie jednego wpisu rejestru</span><span class="sxs-lookup"><span data-stu-id="e7118-131">Setting a Single Registry Entry</span></span>

<span data-ttu-id="e7118-132">Jeśli chcesz zmienić określonego wpisu w kluczu rejestru, można użyć jednej z kilku możliwych podejść.</span><span class="sxs-lookup"><span data-stu-id="e7118-132">If you want to change a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="e7118-133">Ten przykład modyfikuje **ścieżki** wpis w `HKEY_CURRENT_USER\Environment`.</span><span class="sxs-lookup"><span data-stu-id="e7118-133">This example modifies the **Path** entry under `HKEY_CURRENT_USER\Environment`.</span></span> <span data-ttu-id="e7118-134">**Ścieżki** wejścia Określa lokalizację plików wykonywalnych.</span><span class="sxs-lookup"><span data-stu-id="e7118-134">The **Path** entry specifies where to find executable files.</span></span>

1. <span data-ttu-id="e7118-135">Pobieranie bieżącej wartości **ścieżki** przy użyciu wpisu `Get-ItemProperty`.</span><span class="sxs-lookup"><span data-stu-id="e7118-135">Retrieve the current value of the **Path** entry using `Get-ItemProperty`.</span></span>
2. <span data-ttu-id="e7118-136">Dodaj nową wartość, oddzielając je za pomocą `;`.</span><span class="sxs-lookup"><span data-stu-id="e7118-136">Add the new value, separating it with a `;`.</span></span>
3. <span data-ttu-id="e7118-137">Użyj `Set-ItemProperty` przy użyciu określonego klucza, wpis nazwy i wartości, aby zmodyfikować wpis rejestru.</span><span class="sxs-lookup"><span data-stu-id="e7118-137">Use `Set-ItemProperty` with the specified key, entry name, and value to modify the registry entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> <span data-ttu-id="e7118-138">Mimo że `Set-ItemProperty` ma **filtru**, **Include**, i **wykluczyć** parametrów, nie można ich używać do filtrowania według nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="e7118-138">Although `Set-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="e7118-139">Parametry te dotyczą klucze rejestru — służą do ścieżki elementu — i nie wpisy rejestru — służą do właściwości elementu.</span><span class="sxs-lookup"><span data-stu-id="e7118-139">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="e7118-140">Innym rozwiązaniem jest za pomocą narzędzia wiersza polecenia Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="e7118-140">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="e7118-141">Aby uzyskać pomoc dotyczącą reg.exe, wpisz **reg.exe /?**</span><span class="sxs-lookup"><span data-stu-id="e7118-141">For help with reg.exe, type **reg.exe /?**</span></span>
<span data-ttu-id="e7118-142">w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="e7118-142">at a command prompt.</span></span>

<span data-ttu-id="e7118-143">Następujący przykład zmienia **ścieżki** zgłoszenia przez usunięcie ścieżki dodane w powyższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e7118-143">The following example changes the **Path** entry by removing the path added in the example above.</span></span>
<span data-ttu-id="e7118-144">`Get-ItemProperty` nadal służy do pobierania bieżącą wartość, aby uniknąć konieczności przeanalizować ciągu zwróconego przez `reg query`.</span><span class="sxs-lookup"><span data-stu-id="e7118-144">`Get-ItemProperty` is still used to retrieve the current value to avoid having to parse the string returned from `reg query`.</span></span> <span data-ttu-id="e7118-145">**Podciąg** i **LastIndexOf** metody są używane do pobierania ścieżki ostatniego dodane do **ścieżki** wpisu.</span><span class="sxs-lookup"><span data-stu-id="e7118-145">The **SubString** and **LastIndexOf** methods are used to retrieve the last path added to the **Path** entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

### <a name="creating-new-registry-entries"></a><span data-ttu-id="e7118-146">Tworzenie nowych wpisów rejestru</span><span class="sxs-lookup"><span data-stu-id="e7118-146">Creating New Registry Entries</span></span>

<span data-ttu-id="e7118-147">Aby dodać nowy wpis o nazwie "PowerShellPath" do **CurrentVersion** użycia klucza, `New-ItemProperty` przy użyciu ścieżki do klucza, wprowadzona nazwa i wartość wpisu.</span><span class="sxs-lookup"><span data-stu-id="e7118-147">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use `New-ItemProperty` with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="e7118-148">W tym przykładzie pobierzemy wartości zmiennej środowiska Windows PowerShell `$PSHome`, który przechowuje ścieżki do katalogu instalacyjnego dla środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e7118-148">For this example, we will take the value of the Windows PowerShell variable `$PSHome`, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="e7118-149">Można dodać nowy wpis do klucza przy użyciu następującego polecenia, a polecenie zwraca też wartość informacji na temat nowego wpisu:</span><span class="sxs-lookup"><span data-stu-id="e7118-149">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

```Output
PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

<span data-ttu-id="e7118-150">**PropertyType** musi być nazwą **Microsoft.Win32.RegistryValueKind** składowej wyliczenia z poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="e7118-150">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="e7118-151">Wartość PropertyType</span><span class="sxs-lookup"><span data-stu-id="e7118-151">PropertyType Value</span></span>|<span data-ttu-id="e7118-152">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="e7118-152">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="e7118-153">Binarny</span><span class="sxs-lookup"><span data-stu-id="e7118-153">Binary</span></span>|<span data-ttu-id="e7118-154">Dane binarne</span><span class="sxs-lookup"><span data-stu-id="e7118-154">Binary data</span></span>|
|<span data-ttu-id="e7118-155">DWord</span><span class="sxs-lookup"><span data-stu-id="e7118-155">DWord</span></span>|<span data-ttu-id="e7118-156">Liczba, która jest nieprawidłowa UInt32</span><span class="sxs-lookup"><span data-stu-id="e7118-156">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="e7118-157">ExpandString</span><span class="sxs-lookup"><span data-stu-id="e7118-157">ExpandString</span></span>|<span data-ttu-id="e7118-158">Ciąg, który może zawierać zmienne środowiskowe, które są dynamicznie powiększane</span><span class="sxs-lookup"><span data-stu-id="e7118-158">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="e7118-159">MultiString</span><span class="sxs-lookup"><span data-stu-id="e7118-159">MultiString</span></span>|<span data-ttu-id="e7118-160">Wielowierszowy ciąg</span><span class="sxs-lookup"><span data-stu-id="e7118-160">A multiline string</span></span>|
|<span data-ttu-id="e7118-161">Ciąg</span><span class="sxs-lookup"><span data-stu-id="e7118-161">String</span></span>|<span data-ttu-id="e7118-162">Dowolną wartość ciągu</span><span class="sxs-lookup"><span data-stu-id="e7118-162">Any string value</span></span>|
|<span data-ttu-id="e7118-163">QWord</span><span class="sxs-lookup"><span data-stu-id="e7118-163">QWord</span></span>|<span data-ttu-id="e7118-164">8 bajtów danych binarnych</span><span class="sxs-lookup"><span data-stu-id="e7118-164">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="e7118-165">Można dodać wpis rejestru do wielu lokalizacji, określając szereg wartości **ścieżki** parametru:</span><span class="sxs-lookup"><span data-stu-id="e7118-165">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="e7118-166">Można również zastąpić istniejące wartości wpisu rejestru, dodając **życie** parametru do dowolnego `New-ItemProperty` polecenia.</span><span class="sxs-lookup"><span data-stu-id="e7118-166">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any `New-ItemProperty` command.</span></span>

### <a name="renaming-registry-entries"></a><span data-ttu-id="e7118-167">Zmiana nazwy wpisów rejestru</span><span class="sxs-lookup"><span data-stu-id="e7118-167">Renaming Registry Entries</span></span>

<span data-ttu-id="e7118-168">Aby zmienić nazwę **PowerShellPath** wpis "PSHome", użyj `Rename-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="e7118-168">To rename the **PowerShellPath** entry to "PSHome," use `Rename-ItemProperty`:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="e7118-169">Aby wyświetlić wartość, których nazwy zostały zmienione, należy dodać **PassThru** do polecenia.</span><span class="sxs-lookup"><span data-stu-id="e7118-169">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a><span data-ttu-id="e7118-170">Usuwanie wpisów rejestru</span><span class="sxs-lookup"><span data-stu-id="e7118-170">Deleting Registry Entries</span></span>

<span data-ttu-id="e7118-171">Aby usunąć PSHome i PowerShellPath wpisy rejestru, użyj `Remove-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="e7118-171">To delete both the PSHome and PowerShellPath registry entries, use `Remove-ItemProperty`:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
