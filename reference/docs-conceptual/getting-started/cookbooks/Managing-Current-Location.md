---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Zarządzanie bieżącą lokalizacją
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
ms.openlocfilehash: 8d529bf4a85553b95a9cab2739016859662486f2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="managing-current-location"></a><span data-ttu-id="b3aa6-103">Zarządzanie bieżącą lokalizacją</span><span class="sxs-lookup"><span data-stu-id="b3aa6-103">Managing Current Location</span></span>

<span data-ttu-id="b3aa6-104">Przy przechodzeniu systemach folder w Eksploratorze plików, zwykle mają określonej lokalizacji pracy — a mianowicie bieżącego Otwórz folder.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-104">When navigating folder systems in File Explorer, you usually have a specific working location - namely, the current open folder.</span></span> <span data-ttu-id="b3aa6-105">Elementy w bieżącym folderze może manipulować łatwo za pomocą kliknięcia.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-105">Items in the current folder can be manipulated easily by clicking them.</span></span> <span data-ttu-id="b3aa6-106">Dla interfejsów wiersza polecenia takich jak Cmd.exe w tym samym folderze co określonego pliku, można do niego dostęp przez określenie stosunkowo krótką nazwę, a nie trzeba określić pełną ścieżkę do pliku.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-106">For command-line interfaces such as Cmd.exe, when you are in the same folder as a particular file, you can access it by specifying a relatively short name, rather than needing to specify the entire path to the file.</span></span> <span data-ttu-id="b3aa6-107">Bieżący katalog nosi nazwę katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-107">The current directory is called the working directory.</span></span>

<span data-ttu-id="b3aa6-108">Program Windows PowerShell korzysta rzeczownikiem **lokalizacji** do odwoływania się do katalogu roboczego i implementuje rodziny poleceń cmdlet do badania i manipulowania Twojej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-108">Windows PowerShell uses the noun **Location** to refer to the working directory, and implements a family of cmdlets to examine and manipulate your location.</span></span>

### <a name="getting-your-current-location-get-location"></a><span data-ttu-id="b3aa6-109">Pobieranie bieżącej lokalizacji (Get lokalizacji)</span><span class="sxs-lookup"><span data-stu-id="b3aa6-109">Getting Your Current Location (Get-Location)</span></span>

<span data-ttu-id="b3aa6-110">Aby określić ścieżkę bieżącą lokalizację katalogu, wprowadź **lokalizacji Get** polecenia:</span><span class="sxs-lookup"><span data-stu-id="b3aa6-110">To determine the path of your current directory location, enter the **Get-Location** command:</span></span>

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="b3aa6-111">Polecenie cmdlet Get-lokalizacji jest podobny do **pwd** w powłoki BASH.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-111">The Get-Location cmdlet is similar to the **pwd** command in the BASH shell.</span></span> <span data-ttu-id="b3aa6-112">Polecenia cmdlet Set-lokalizacji jest podobny do **cd** w Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-112">The Set-Location cmdlet is similar to the **cd** command in Cmd.exe.</span></span>

### <a name="setting-your-current-location-set-location"></a><span data-ttu-id="b3aa6-113">Ustawianie bieżącej lokalizacji (zestaw lokalizacji)</span><span class="sxs-lookup"><span data-stu-id="b3aa6-113">Setting Your Current Location (Set-Location)</span></span>

<span data-ttu-id="b3aa6-114">**Lokalizacji Get** z używane jest polecenie **lokalizacją zestawu** polecenia.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-114">The **Get-Location** command is used with the **Set-Location** command.</span></span> <span data-ttu-id="b3aa6-115">**Lokalizacją zestawu** polecenia można określić bieżącą lokalizację katalogu.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-115">The **Set-Location** command allows you to specify your current directory location.</span></span>

```powershell
Set-Location -Path C:\Windows
```

<span data-ttu-id="b3aa6-116">Po wprowadzeniu polecenia, można zauważyć, że nie otrzymasz żadnych bezpośrednich swoją opinię na temat efekt polecenia.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-116">After you enter the command, you will notice that you do not receive any direct feedback about the effect of the command.</span></span> <span data-ttu-id="b3aa6-117">Większość poleceń programu Windows PowerShell, które wykonują akcję utworzyć żadnych danych wyjściowych, ponieważ dane wyjściowe nie jest zawsze przydatne.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-117">Most Windows PowerShell commands that perform an action produce little or no output because the output is not always useful.</span></span> <span data-ttu-id="b3aa6-118">Aby sprawdzić, czy katalog pomyślnym nastąpiła zmiana po wprowadzeniu **lokalizacją zestawu** polecenia, obejmują **- PassThru** parametru po wprowadzeniu **Set-lokalizacji**polecenia:</span><span class="sxs-lookup"><span data-stu-id="b3aa6-118">To verify that a successful directory change has occurred when you enter the **Set-Location** command, include the **-PassThru** parameter when you enter the **Set-Location** command:</span></span>

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

<span data-ttu-id="b3aa6-119">**- PassThru** parametru można z wielu zestaw poleceń w programie Windows PowerShell do zwracania informacji dotyczących wynik w przypadkach, w których nie ma żadnych danych wyjściowych domyślnego.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-119">The **-PassThru** parameter can be used with many Set commands in Windows PowerShell to return information about the result in cases in which there is no default output.</span></span>

<span data-ttu-id="b3aa6-120">Można określić ścieżki względem bieżącej lokalizacji w taki sam sposób, jak w większości systemu UNIX i systemu Windows będzie można polecenia powłoki.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-120">You can specify paths relative to your current location in the same way as you would in most UNIX and Windows command shells.</span></span> <span data-ttu-id="b3aa6-121">W standardowej notacji dla ścieżek względnych okres (**.**) reprezentuje folder bieżący i podwójna okres (**...** ) reprezentuje katalogu nadrzędnego dla bieżącej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-121">In standard notation for relative paths, a period (**.**)represents your current folder, and a doubled period (**..**) represents the parent directory of your current location.</span></span>

<span data-ttu-id="b3aa6-122">Na przykład, jeśli są w **C:\\Windows** folderu, kropka (**.**) reprezentuje **C:\\Windows** i dwukrotnie kropki (**...** ) reprezentuje **C:**.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-122">For example, if you are in the **C:\\Windows** folder, a period (**.**)represents **C:\\Windows** and double periods (**..**) represent **C:**.</span></span> <span data-ttu-id="b3aa6-123">Możesz zmienić w bieżącej lokalizacji w katalogu głównym dysku C:, wpisując:</span><span class="sxs-lookup"><span data-stu-id="b3aa6-123">You can change from your current location to the root of the C: drive by typing:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

<span data-ttu-id="b3aa6-124">Ta sama metoda działa na dyskach środowiska Windows PowerShell, które nie są dyski systemu plików, takich jak **HKLM:**.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-124">The same technique works on Windows PowerShell drives that are not file system drives, such as **HKLM:**.</span></span> <span data-ttu-id="b3aa6-125">Możesz ustawić dla Twojej lokalizacji HKLM\\oprogramowania klucz rejestru, wpisując:</span><span class="sxs-lookup"><span data-stu-id="b3aa6-125">You can set your location to the HKLM\\Software key in the registry by typing:</span></span>

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

<span data-ttu-id="b3aa6-126">Następnie można zmienić na lokalizację katalogu do katalogu nadrzędnego, który jest głównym HKLM programu PowerShell systemu Windows: dysku za pomocą ścieżki względnej:</span><span class="sxs-lookup"><span data-stu-id="b3aa6-126">You can then change the directory location to the parent directory, which is the root of the Windows PowerShell HKLM: drive, by using a relative path:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

<span data-ttu-id="b3aa6-127">Można wpisać lokalizacją zestawu lub użyć dowolnego z wbudowanych aliasy programu Windows PowerShell do lokalizacji zestawu (cd, chdir, sl).</span><span class="sxs-lookup"><span data-stu-id="b3aa6-127">You can type Set-Location or use any of the built-in Windows PowerShell aliases for Set-Location (cd, chdir, sl).</span></span> <span data-ttu-id="b3aa6-128">Przykład:</span><span class="sxs-lookup"><span data-stu-id="b3aa6-128">For example:</span></span>

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

### <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a><span data-ttu-id="b3aa6-129">Zapisywanie i odwołująca ostatnie lokalizacje (lokalizacja wypychania i lokalizacji Pop)</span><span class="sxs-lookup"><span data-stu-id="b3aa6-129">Saving and Recalling Recent Locations (Push-Location and Pop-Location)</span></span>

<span data-ttu-id="b3aa6-130">W przypadku zmiany lokalizacji, warto śledzić gdy zostały oraz aby można było powrócić do poprzedniej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-130">When changing locations, it is helpful to keep track of where you have been and to be able to return to your previous location.</span></span> <span data-ttu-id="b3aa6-131">**Lokalizacji wypychania** polecenia cmdlet programu Windows PowerShell tworzy uporządkowanej historię ("stosu") ścieżek katalogów, w którym nastąpiło i można przejść za pośrednictwem historii ścieżek katalogów przy użyciu uzupełniające  **Lokalizacji POP** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-131">The **Push-Location** cmdlet in Windows PowerShell creates a ordered history (a "stack") of directory paths where you have been, and you can step back through the history of directory paths by using the complementary **Pop-Location** cmdlet.</span></span>

<span data-ttu-id="b3aa6-132">Na przykład programu Windows PowerShell zazwyczaj rozpoczyna się w katalogu macierzystego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-132">For example, Windows PowerShell typically starts in the user's home directory.</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="b3aa6-133">Wyraz *stosu* ma specjalne znaczenie w wielu ustawień programowania, w tym .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-133">The word *stack* has a special meaning in many programming settings, including .NET Framework.</span></span> <span data-ttu-id="b3aa6-134">Podobnie jak fizyczny stosu elementów ostatni element, który można umieścić na stosie jest pierwszy element, który może pobierać ze stosu.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-134">Like a physical stack of items, the last item you put onto the stack is the first item that you can pull off the stack.</span></span> <span data-ttu-id="b3aa6-135">Dodawanie elementu stos potocznie nazywa się "PUSH" element na stosie.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-135">Adding an item to a stack is colloquially known as "pushing" the item onto the stack.</span></span> <span data-ttu-id="b3aa6-136">Ściąganie elementu ze stosu potocznie nazywa się "wyświetlanie" elementu ze stosu.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-136">Pulling an item off the stack is colloquially known as "popping" the item off the stack.</span></span>

<span data-ttu-id="b3aa6-137">Aby wypychanie bieżącej lokalizacji na stosie, a następnie przejdź do folderu Ustawienia lokalne, wpisz:</span><span class="sxs-lookup"><span data-stu-id="b3aa6-137">To push the current location onto the stack, and then move to the Local Settings folder, type:</span></span>

```powershell
Push-Location -Path "Local Settings"
```

<span data-ttu-id="b3aa6-138">Można następnie Wypchnij lokalizacji lokalnej ustawień na stosie i i przejdź do folderu tymczasowego, wpisując:</span><span class="sxs-lookup"><span data-stu-id="b3aa6-138">You can then push the Local Settings location onto the stack and and move to the Temp folder by typing:</span></span>

```powershell
Push-Location -Path Temp
```

<span data-ttu-id="b3aa6-139">Możesz sprawdzić, zmienić katalogi, wprowadzając **lokalizacji Get** polecenia:</span><span class="sxs-lookup"><span data-stu-id="b3aa6-139">You can verify that you changed directories by entering the **Get-Location** command:</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

<span data-ttu-id="b3aa6-140">Można następnie pop do katalogu ostatnio odwiedzonych przez wprowadzenie **lokalizacji Pop** polecenia i Sprawdź zmiany, wprowadzając **lokalizacji Get** polecenia:</span><span class="sxs-lookup"><span data-stu-id="b3aa6-140">You can then pop back into the most recently visited directory by entering the **Pop-Location** command, and verify the change by entering the **Get-Location** command:</span></span>

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

<span data-ttu-id="b3aa6-141">Tylko jako z **lokalizacją zestawu** polecenia cmdlet, można dołączyć **- PassThru** parametru po wprowadzeniu **lokalizacji Pop** polecenia cmdlet, aby wyświetlić katalog wprowadzony:</span><span class="sxs-lookup"><span data-stu-id="b3aa6-141">Just as with the **Set-Location** cmdlet, you can include the **-PassThru** parameter when you enter the **Pop-Location** cmdlet to display the directory that you entered:</span></span>

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

<span data-ttu-id="b3aa6-142">Można również używać poleceń cmdlet lokalizacji z ścieżek sieciowych.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-142">You can also use the Location cmdlets with network paths.</span></span> <span data-ttu-id="b3aa6-143">Jeśli masz serwer o nazwie FS01 z udziałem o nazwie Public, można zmienić lokalizację, wpisując</span><span class="sxs-lookup"><span data-stu-id="b3aa6-143">If you have a server named FS01 with an share named Public, you can change your location by typing</span></span>

```powershell
Set-Location \\FS01\Public
```

<span data-ttu-id="b3aa6-144">lub</span><span class="sxs-lookup"><span data-stu-id="b3aa6-144">or</span></span>

```powershell
Push-Location \\FS01\Public
```

<span data-ttu-id="b3aa6-145">Można użyć **lokalizacji wypychania** i **lokalizacją zestawu** poleceń, aby zmienić lokalizację do dowolnego dostępnego dysku.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-145">You can use the **Push-Location** and **Set-Location** commands to change the location to any available drive.</span></span> <span data-ttu-id="b3aa6-146">Na przykład, jeśli stacja CD-ROM lokalnego z literą dysku D, który zawiera dysk CD z danymi, można zmienić lokalizacji na dysku CD, wprowadzając **D: lokalizacją zestawu** polecenia.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-146">For example, if you have a local CD-ROM drive with drive letter D that contains a data CD, you can change the location to the CD drive by entering the **Set-Location D:** command.</span></span>

<span data-ttu-id="b3aa6-147">Jeśli dysk jest pusty, otrzymasz następujący komunikat o błędzie:</span><span class="sxs-lookup"><span data-stu-id="b3aa6-147">If the drive is empty, you will get the following error message:</span></span>

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

<span data-ttu-id="b3aa6-148">Korzystając z interfejsu wiersza polecenia, nie jest wygodne zbadać dostępne dyski fizyczne za pomocą Eksploratora plików.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-148">When you are using a command-line interface, it is not convenient to use File Explorer to examine the available physical drives.</span></span> <span data-ttu-id="b3aa6-149">Ponadto Eksploratora plików czy są wyświetlane wszystkie dyski środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-149">Also, File Explorer would not show you the all of the Windows PowerShell drives.</span></span> <span data-ttu-id="b3aa6-150">Programu Windows PowerShell udostępnia zestaw poleceń do manipulowania dyski środowiska Windows PowerShell, a będzie omawianiu te dalej.</span><span class="sxs-lookup"><span data-stu-id="b3aa6-150">Windows PowerShell provides a set of commands for manipulating Windows PowerShell drives, and we will talk about these next.</span></span>