---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Praca z wpisami rejestru
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: bffdf80931fc4dc570b584623487077dc5d449dc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="6b0d3-103">Praca z wpisami rejestru</span><span class="sxs-lookup"><span data-stu-id="6b0d3-103">Working with Registry Entries</span></span>

<span data-ttu-id="6b0d3-104">Ponieważ wpisy rejestru są właściwości kluczy, a w efekcie nie może być bezpośrednio przeglądany, musimy wykonać nieco inny sposób podczas pracy z nimi.</span><span class="sxs-lookup"><span data-stu-id="6b0d3-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

### <a name="listing-registry-entries"></a><span data-ttu-id="6b0d3-105">Wyświetlanie listy wpisów rejestru</span><span class="sxs-lookup"><span data-stu-id="6b0d3-105">Listing Registry Entries</span></span>

<span data-ttu-id="6b0d3-106">Istnieje wiele różnych sposobów Sprawdź wpisy rejestru.</span><span class="sxs-lookup"><span data-stu-id="6b0d3-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="6b0d3-107">Najprostszym sposobem jest można pobrać nazw właściwości skojarzone z kluczem.</span><span class="sxs-lookup"><span data-stu-id="6b0d3-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="6b0d3-108">Na przykład, aby wyświetlić nazwy wpisów w kluczu rejestru **HKEY_LOCAL_MACHINE\\oprogramowania\\Microsoft\\Windows\\CurrentVersion**, użyj **elementu Get** .</span><span class="sxs-lookup"><span data-stu-id="6b0d3-108">For example, to see the names of the entries in the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, use **Get-Item**.</span></span> <span data-ttu-id="6b0d3-109">Klucze rejestru ma właściwości o nazwie ogólne "Właściwości", który jest lista wpisy rejestru w kluczu.</span><span class="sxs-lookup"><span data-stu-id="6b0d3-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span> <span data-ttu-id="6b0d3-110">Polecenie wybiera właściwości property i rozwija elementów, dzięki czemu są one wyświetlane na liście:</span><span class="sxs-lookup"><span data-stu-id="6b0d3-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="6b0d3-111">Aby wyświetlić wpisy rejestru w bardziej czytelnej postaci, użyj **Get-ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="6b0d3-111">To view the registry entries in a more readable form, use **Get-ItemProperty**:</span></span>

```
PS> Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion

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

<span data-ttu-id="6b0d3-112">Właściwości związane z programu Windows PowerShell dla klucza są wszystkie prefiksem "PS", takie jak **PSPath**, **PSParentPath**, **PSChildName**, i **PSProvider** .</span><span class="sxs-lookup"><span data-stu-id="6b0d3-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="6b0d3-113">Można użyć "**.**" notation odwoływania się do bieżącej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="6b0d3-113">You can use the "**.**" notation for referring to the current location.</span></span> <span data-ttu-id="6b0d3-114">Można użyć **lokalizacją zestawu** można zmienić na **CurrentVersion** kontenera rejestru pierwszy:</span><span class="sxs-lookup"><span data-stu-id="6b0d3-114">You can use **Set-Location** to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="6b0d3-115">Alternatywnie można użyć wbudowanych elementu PSDrive HKLM z **lokalizacją zestawu**:</span><span class="sxs-lookup"><span data-stu-id="6b0d3-115">Alternatively, you can use the built-in HKLM PSDrive with **Set-Location**:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="6b0d3-116">Następnie można użyć "**.**" notation dla bieżącej lokalizacji do listy właściwości bez określania Pełna ścieżka:</span><span class="sxs-lookup"><span data-stu-id="6b0d3-116">You can then use the "**.**" notation for the current location to list the properties without specifying a full path:</span></span>

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="6b0d3-117">Ścieżka rozszerzenia działa tak samo jak w systemie plików, więc w tej lokalizacji można uzyskać **ItemProperty** dla **HKLM:\\oprogramowania\\Microsoft\\systemu Windows \\Pomocy** za pomocą **Get ItemProperty-ścieżki. \\Pomocy**.</span><span class="sxs-lookup"><span data-stu-id="6b0d3-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** by using **Get-ItemProperty -Path ..\\Help**.</span></span>

### <a name="getting-a-single-registry-entry"></a><span data-ttu-id="6b0d3-118">Pobieranie jednego wpisu rejestru</span><span class="sxs-lookup"><span data-stu-id="6b0d3-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="6b0d3-119">Jeśli chcesz pobrać określonego wpisu w kluczu rejestru, można użyć jednej z kilku metod możliwe.</span><span class="sxs-lookup"><span data-stu-id="6b0d3-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="6b0d3-120">W tym przykładzie wyszukuje wartość **DevicePath** w **HKEY_LOCAL_MACHINE\\oprogramowania\\Microsoft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="6b0d3-120">This example finds the value of **DevicePath** in **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span>

<span data-ttu-id="6b0d3-121">Przy użyciu **Get-ItemProperty**, użyj **ścieżki** parametr, aby określić nazwę klucza i **nazwa** parametr, aby określić nazwę **DevicePath** wpisu.</span><span class="sxs-lookup"><span data-stu-id="6b0d3-121">Using **Get-ItemProperty**, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

```
PS> Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath

PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

<span data-ttu-id="6b0d3-122">To polecenie zwraca standardowe właściwości środowiska Windows PowerShell, jak również **DevicePath** właściwości.</span><span class="sxs-lookup"><span data-stu-id="6b0d3-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="6b0d3-123">Mimo że **Get-ItemProperty** ma **filtru**, **Include**, i **wykluczyć** parametrów, nie można użyć do filtrowania według nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="6b0d3-123">Although **Get-ItemProperty** has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="6b0d3-124">Tych parametrów można znaleźć kluczy rejestru — które są ścieżki elementu — i nie wpisy rejestru — które są właściwości elementu.</span><span class="sxs-lookup"><span data-stu-id="6b0d3-124">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="6b0d3-125">Innym rozwiązaniem jest za pomocą narzędzia wiersza polecenia Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="6b0d3-125">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="6b0d3-126">Aby uzyskać pomoc dotyczącą reg.exe, wpisz **reg.exe /?**</span><span class="sxs-lookup"><span data-stu-id="6b0d3-126">For help with reg.exe, type **reg.exe /?**</span></span> <span data-ttu-id="6b0d3-127">w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="6b0d3-127">at a command prompt.</span></span> <span data-ttu-id="6b0d3-128">Aby znaleźć wpisu DevicePath, należy użyć reg.exe, jak pokazano w poniższym poleceniu:</span><span class="sxs-lookup"><span data-stu-id="6b0d3-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="6b0d3-129">Można również użyć **WshShell COM** obiektu, tak aby zawierał niektórych wpisów rejestru, mimo że ta metoda nie działa z dużych danych binarnych lub z nazwami wpis rejestru, które zawierają znaki, takie jak "\\").</span><span class="sxs-lookup"><span data-stu-id="6b0d3-129">You can also use the **WshShell COM** object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="6b0d3-130">Dołącz nazwę właściwości do ścieżki elementu z \\ separatora:</span><span class="sxs-lookup"><span data-stu-id="6b0d3-130">Append the property name to the item path with a \\ separator:</span></span>

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a><span data-ttu-id="6b0d3-131">Tworzenie nowych wpisów rejestru</span><span class="sxs-lookup"><span data-stu-id="6b0d3-131">Creating New Registry Entries</span></span>

<span data-ttu-id="6b0d3-132">Aby dodać nowy wpis o nazwie "PowerShellPath" do **CurrentVersion** użycie kluczy, **ItemProperty nowy** ścieżkę do klucza, wpis nazwy i wartości wpisu.</span><span class="sxs-lookup"><span data-stu-id="6b0d3-132">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use **New-ItemProperty** with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="6b0d3-133">Na przykład teraz nastąpi przekierowanie do wartości zmiennej środowiska Windows PowerShell **$PSHome**, który przechowuje ścieżkę do katalogu instalacyjnego środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6b0d3-133">For this example, we will take the value of the Windows PowerShell variable **$PSHome**, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="6b0d3-134">Można dodać nowy wpis do klucza za pomocą następującego polecenia, a polecenie zwraca też wartość informacji o nowy wpis:</span><span class="sxs-lookup"><span data-stu-id="6b0d3-134">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

```
PS> New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome

PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

<span data-ttu-id="6b0d3-135">**PropertyType** musi być nazwą **Microsoft.Win32.RegistryValueKind** element członkowski wyliczenia z następującej tabeli:</span><span class="sxs-lookup"><span data-stu-id="6b0d3-135">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="6b0d3-136">Wartość elementu PropertyType</span><span class="sxs-lookup"><span data-stu-id="6b0d3-136">PropertyType Value</span></span>|<span data-ttu-id="6b0d3-137">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="6b0d3-137">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="6b0d3-138">Binarny</span><span class="sxs-lookup"><span data-stu-id="6b0d3-138">Binary</span></span>|<span data-ttu-id="6b0d3-139">Dane binarne</span><span class="sxs-lookup"><span data-stu-id="6b0d3-139">Binary data</span></span>|
|<span data-ttu-id="6b0d3-140">DWord</span><span class="sxs-lookup"><span data-stu-id="6b0d3-140">DWord</span></span>|<span data-ttu-id="6b0d3-141">Liczbę, która jest nieprawidłowa UInt32</span><span class="sxs-lookup"><span data-stu-id="6b0d3-141">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="6b0d3-142">ExpandString</span><span class="sxs-lookup"><span data-stu-id="6b0d3-142">ExpandString</span></span>|<span data-ttu-id="6b0d3-143">Ciąg, który może zawierać zmienne środowiskowe, które zostaną rozwinięte dynamicznie</span><span class="sxs-lookup"><span data-stu-id="6b0d3-143">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="6b0d3-144">Kolumny</span><span class="sxs-lookup"><span data-stu-id="6b0d3-144">MultiString</span></span>|<span data-ttu-id="6b0d3-145">Wielowierszowy ciąg</span><span class="sxs-lookup"><span data-stu-id="6b0d3-145">A multiline string</span></span>|
|<span data-ttu-id="6b0d3-146">Ciąg</span><span class="sxs-lookup"><span data-stu-id="6b0d3-146">String</span></span>|<span data-ttu-id="6b0d3-147">Dowolną wartością ciągu</span><span class="sxs-lookup"><span data-stu-id="6b0d3-147">Any string value</span></span>|
|<span data-ttu-id="6b0d3-148">QWord</span><span class="sxs-lookup"><span data-stu-id="6b0d3-148">QWord</span></span>|<span data-ttu-id="6b0d3-149">8 bajtów danych binarnych</span><span class="sxs-lookup"><span data-stu-id="6b0d3-149">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="6b0d3-150">W wielu lokalizacjach można dodać wpis rejestru, określając tablicę wartości **ścieżki** parametru:</span><span class="sxs-lookup"><span data-stu-id="6b0d3-150">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

<span data-ttu-id="6b0d3-151">Można również zastąpić istniejące wartości wpisu rejestru, dodając **życie** parametru do dowolnego **ItemProperty nowy** polecenia.</span><span class="sxs-lookup"><span data-stu-id="6b0d3-151">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any **New-ItemProperty** command.</span></span>

### <a name="renaming-registry-entries"></a><span data-ttu-id="6b0d3-152">Zmiana nazwy wpisy rejestru</span><span class="sxs-lookup"><span data-stu-id="6b0d3-152">Renaming Registry Entries</span></span>

<span data-ttu-id="6b0d3-153">Aby zmienić nazwę **PowerShellPath** wpisu "PSHome", użyj **ItemProperty zmiany nazwy**:</span><span class="sxs-lookup"><span data-stu-id="6b0d3-153">To rename the **PowerShellPath** entry to "PSHome," use **Rename-ItemProperty**:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="6b0d3-154">Aby wyświetlić wartość zmieniono nazwę, Dodaj **PassThru** do polecenia parametr.</span><span class="sxs-lookup"><span data-stu-id="6b0d3-154">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a><span data-ttu-id="6b0d3-155">Usuwanie wpisów rejestru</span><span class="sxs-lookup"><span data-stu-id="6b0d3-155">Deleting Registry Entries</span></span>

<span data-ttu-id="6b0d3-156">Aby usunąć wpisy rejestru PSHome i PowerShellPath, użyj **ItemProperty Usuń**:</span><span class="sxs-lookup"><span data-stu-id="6b0d3-156">To delete both the PSHome and PowerShellPath registry entries, use **Remove-ItemProperty**:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```