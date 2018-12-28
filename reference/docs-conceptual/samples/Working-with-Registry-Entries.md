---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Praca z wpisami rejestru
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: bffdf80931fc4dc570b584623487077dc5d449dc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405372"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="68f97-103">Praca z wpisami rejestru</span><span class="sxs-lookup"><span data-stu-id="68f97-103">Working with Registry Entries</span></span>

<span data-ttu-id="68f97-104">Ponieważ wpisy rejestru są właściwości kluczy, a w efekcie nie mogą być bezpośrednio przeglądane, musimy wykonać nieco innego podejścia, podczas pracy z nimi.</span><span class="sxs-lookup"><span data-stu-id="68f97-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

### <a name="listing-registry-entries"></a><span data-ttu-id="68f97-105">Wyświetlanie listy wpisów rejestru</span><span class="sxs-lookup"><span data-stu-id="68f97-105">Listing Registry Entries</span></span>

<span data-ttu-id="68f97-106">Istnieje wiele różnych sposobów, aby zbadać wpisów rejestru.</span><span class="sxs-lookup"><span data-stu-id="68f97-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="68f97-107">Najprostszym sposobem jest uzyskanie nazw właściwości skojarzone z kluczem.</span><span class="sxs-lookup"><span data-stu-id="68f97-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="68f97-108">Na przykład, aby zobaczyć nazwy wpisów w kluczu rejestru **HKEY_LOCAL_MACHINE\\oprogramowania\\Microsoft\\Windows\\CurrentVersion**, użyj **elementu Get** .</span><span class="sxs-lookup"><span data-stu-id="68f97-108">For example, to see the names of the entries in the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, use **Get-Item**.</span></span> <span data-ttu-id="68f97-109">Klucze rejestru mają właściwość o nazwie ogólne "Właściwości", znajduje się lista wpisów rejestru w kluczu.</span><span class="sxs-lookup"><span data-stu-id="68f97-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span> <span data-ttu-id="68f97-110">Następujące polecenie wybiera właściwość właściwości i rozwija elementów, dlatego, że są one wyświetlane na liście:</span><span class="sxs-lookup"><span data-stu-id="68f97-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="68f97-111">Aby wyświetlić wpisy rejestru w postaci bardziej czytelny, użyj **Get-zmieniona właściwość elementu**:</span><span class="sxs-lookup"><span data-stu-id="68f97-111">To view the registry entries in a more readable form, use **Get-ItemProperty**:</span></span>

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

<span data-ttu-id="68f97-112">Właściwości związane z programu Windows PowerShell dla klucza są wszystkie prefiks "PS", takich jak **PSPath**, **PSParentPath**, **PSChildName**, i **PSProvider** .</span><span class="sxs-lookup"><span data-stu-id="68f97-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="68f97-113">Można użyć "**.**" notation odwoływania się do bieżącej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="68f97-113">You can use the "**.**" notation for referring to the current location.</span></span> <span data-ttu-id="68f97-114">Możesz użyć **Ustawianie lokalizacji** można zmienić na **CurrentVersion** rejestru kontenera pierwszy:</span><span class="sxs-lookup"><span data-stu-id="68f97-114">You can use **Set-Location** to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="68f97-115">Alternatywnie, można użyć wbudowanych PSDrive HKLM z **Ustawianie lokalizacji**:</span><span class="sxs-lookup"><span data-stu-id="68f97-115">Alternatively, you can use the built-in HKLM PSDrive with **Set-Location**:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="68f97-116">Następnie można użyć "**.**" notacji dla bieżącej lokalizacji wyświetlić listę właściwości bez określenia pełnej ścieżki:</span><span class="sxs-lookup"><span data-stu-id="68f97-116">You can then use the "**.**" notation for the current location to list the properties without specifying a full path:</span></span>

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="68f97-117">Ścieżka rozszerzenia działa tak samo, jak w systemie plików, dzięki czemu z tej lokalizacji można uzyskać **zmieniona właściwość elementu** dla **HKLM:\\oprogramowania\\Microsoft\\Windows \\Pomocy** przy użyciu **Get-zmieniona właściwość elementu — ścieżka... \\Pomocy**.</span><span class="sxs-lookup"><span data-stu-id="68f97-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** by using **Get-ItemProperty -Path ..\\Help**.</span></span>

### <a name="getting-a-single-registry-entry"></a><span data-ttu-id="68f97-118">Pobieranie jednego wpisu rejestru</span><span class="sxs-lookup"><span data-stu-id="68f97-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="68f97-119">Jeśli chcesz pobrać określonego wpisu w kluczu rejestru, można użyć jednej z kilku możliwych podejść.</span><span class="sxs-lookup"><span data-stu-id="68f97-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="68f97-120">W tym przykładzie wyszukuje wartość **DevicePath** w **HKEY_LOCAL_MACHINE\\oprogramowania\\Microsoft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="68f97-120">This example finds the value of **DevicePath** in **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span>

<span data-ttu-id="68f97-121">Za pomocą **Get-zmieniona właściwość elementu**, użyj **ścieżki** parametru do określenia nazwy klucza i **nazwa** parametru, aby określić nazwę **DevicePath** wpisu.</span><span class="sxs-lookup"><span data-stu-id="68f97-121">Using **Get-ItemProperty**, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

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

<span data-ttu-id="68f97-122">To polecenie zwraca standardowe właściwości programu Windows PowerShell, jak również **DevicePath** właściwości.</span><span class="sxs-lookup"><span data-stu-id="68f97-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="68f97-123">Mimo że **Get-zmieniona właściwość elementu** ma **filtru**, **Include**, i **wykluczyć** parametrów, nie można ich używać do filtrowania według nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="68f97-123">Although **Get-ItemProperty** has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="68f97-124">Parametry te dotyczą klucze rejestru — służą do ścieżki elementu — i nie wpisy rejestru — służą do właściwości elementu.</span><span class="sxs-lookup"><span data-stu-id="68f97-124">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="68f97-125">Innym rozwiązaniem jest za pomocą narzędzia wiersza polecenia Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="68f97-125">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="68f97-126">Aby uzyskać pomoc dotyczącą reg.exe, wpisz **reg.exe /?**</span><span class="sxs-lookup"><span data-stu-id="68f97-126">For help with reg.exe, type **reg.exe /?**</span></span> <span data-ttu-id="68f97-127">w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="68f97-127">at a command prompt.</span></span> <span data-ttu-id="68f97-128">Aby znaleźć wpisu DevicePath, użyj reg.exe, jak pokazano w następującym poleceniu:</span><span class="sxs-lookup"><span data-stu-id="68f97-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="68f97-129">Można również użyć **WshShell COM** obiektu również znaleźć niektóre wpisy rejestru, mimo że ta metoda nie działa z dużych danych binarnych lub nazwy wpisów rejestru, które obejmują znaki, takie jak "\\").</span><span class="sxs-lookup"><span data-stu-id="68f97-129">You can also use the **WshShell COM** object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="68f97-130">Dołącz nazwę właściwości ścieżki elementu z \\ separatora:</span><span class="sxs-lookup"><span data-stu-id="68f97-130">Append the property name to the item path with a \\ separator:</span></span>

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a><span data-ttu-id="68f97-131">Tworzenie nowych wpisów rejestru</span><span class="sxs-lookup"><span data-stu-id="68f97-131">Creating New Registry Entries</span></span>

<span data-ttu-id="68f97-132">Aby dodać nowy wpis o nazwie "PowerShellPath" do **CurrentVersion** użycia klucza, **New-zmieniona właściwość elementu** przy użyciu ścieżki do klucza, wprowadzona nazwa i wartość wpisu.</span><span class="sxs-lookup"><span data-stu-id="68f97-132">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use **New-ItemProperty** with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="68f97-133">W tym przykładzie pobierzemy wartości zmiennej środowiska Windows PowerShell **$PSHome**, który przechowuje ścieżki do katalogu instalacyjnego dla środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="68f97-133">For this example, we will take the value of the Windows PowerShell variable **$PSHome**, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="68f97-134">Można dodać nowy wpis do klucza przy użyciu następującego polecenia, a polecenie zwraca też wartość informacji na temat nowego wpisu:</span><span class="sxs-lookup"><span data-stu-id="68f97-134">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

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

<span data-ttu-id="68f97-135">**PropertyType** musi być nazwą **Microsoft.Win32.RegistryValueKind** składowej wyliczenia z poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="68f97-135">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="68f97-136">Wartość PropertyType</span><span class="sxs-lookup"><span data-stu-id="68f97-136">PropertyType Value</span></span>|<span data-ttu-id="68f97-137">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="68f97-137">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="68f97-138">Binarny</span><span class="sxs-lookup"><span data-stu-id="68f97-138">Binary</span></span>|<span data-ttu-id="68f97-139">Dane binarne</span><span class="sxs-lookup"><span data-stu-id="68f97-139">Binary data</span></span>|
|<span data-ttu-id="68f97-140">DWord</span><span class="sxs-lookup"><span data-stu-id="68f97-140">DWord</span></span>|<span data-ttu-id="68f97-141">Liczba, która jest nieprawidłowa UInt32</span><span class="sxs-lookup"><span data-stu-id="68f97-141">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="68f97-142">ExpandString</span><span class="sxs-lookup"><span data-stu-id="68f97-142">ExpandString</span></span>|<span data-ttu-id="68f97-143">Ciąg, który może zawierać zmienne środowiskowe, które są dynamicznie powiększane</span><span class="sxs-lookup"><span data-stu-id="68f97-143">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="68f97-144">FixedLength</span><span class="sxs-lookup"><span data-stu-id="68f97-144">MultiString</span></span>|<span data-ttu-id="68f97-145">Wielowierszowy ciąg</span><span class="sxs-lookup"><span data-stu-id="68f97-145">A multiline string</span></span>|
|<span data-ttu-id="68f97-146">Ciąg</span><span class="sxs-lookup"><span data-stu-id="68f97-146">String</span></span>|<span data-ttu-id="68f97-147">Dowolną wartość ciągu</span><span class="sxs-lookup"><span data-stu-id="68f97-147">Any string value</span></span>|
|<span data-ttu-id="68f97-148">QWord</span><span class="sxs-lookup"><span data-stu-id="68f97-148">QWord</span></span>|<span data-ttu-id="68f97-149">8 bajtów danych binarnych</span><span class="sxs-lookup"><span data-stu-id="68f97-149">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="68f97-150">Można dodać wpis rejestru do wielu lokalizacji, określając szereg wartości **ścieżki** parametru:</span><span class="sxs-lookup"><span data-stu-id="68f97-150">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

<span data-ttu-id="68f97-151">Można również zastąpić istniejące wartości wpisu rejestru, dodając **życie** parametru do dowolnego **New-zmieniona właściwość elementu** polecenia.</span><span class="sxs-lookup"><span data-stu-id="68f97-151">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any **New-ItemProperty** command.</span></span>

### <a name="renaming-registry-entries"></a><span data-ttu-id="68f97-152">Zmiana nazwy wpisów rejestru</span><span class="sxs-lookup"><span data-stu-id="68f97-152">Renaming Registry Entries</span></span>

<span data-ttu-id="68f97-153">Aby zmienić nazwę **PowerShellPath** wpis "PSHome", użyj **Rename-zmieniona właściwość elementu**:</span><span class="sxs-lookup"><span data-stu-id="68f97-153">To rename the **PowerShellPath** entry to "PSHome," use **Rename-ItemProperty**:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="68f97-154">Aby wyświetlić wartość, których nazwy zostały zmienione, należy dodać **PassThru** do polecenia.</span><span class="sxs-lookup"><span data-stu-id="68f97-154">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a><span data-ttu-id="68f97-155">Usuwanie wpisów rejestru</span><span class="sxs-lookup"><span data-stu-id="68f97-155">Deleting Registry Entries</span></span>

<span data-ttu-id="68f97-156">Aby usunąć PSHome i PowerShellPath wpisy rejestru, użyj **Remove-zmieniona właściwość elementu**:</span><span class="sxs-lookup"><span data-stu-id="68f97-156">To delete both the PSHome and PowerShellPath registry entries, use **Remove-ItemProperty**:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```