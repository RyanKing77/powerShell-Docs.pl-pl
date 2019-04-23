---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Zarządzanie bieżącą lokalizacją
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
ms.openlocfilehash: f5e0653b2c3bbc9d2526c7a1c2ff88a8a6641695
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984429"
---
# <a name="managing-current-location"></a><span data-ttu-id="9bd87-103">Zarządzanie bieżącą lokalizacją</span><span class="sxs-lookup"><span data-stu-id="9bd87-103">Managing Current Location</span></span>

<span data-ttu-id="9bd87-104">Podczas przechodzenia systemów folder w Eksploratorze plików, zwykle mają konkretną lokalizację pracy — to znaczy, bieżącego polecenia Otwórz folder.</span><span class="sxs-lookup"><span data-stu-id="9bd87-104">When navigating folder systems in File Explorer, you usually have a specific working location - namely, the current open folder.</span></span> <span data-ttu-id="9bd87-105">Elementy w bieżącym folderze można łatwo manipulować, klikając je.</span><span class="sxs-lookup"><span data-stu-id="9bd87-105">Items in the current folder can be manipulated easily by clicking them.</span></span> <span data-ttu-id="9bd87-106">Dla interfejsów wiersza polecenia, takich jak Cmd.exe podczas pracy w tym samym folderze co określonego pliku, możesz do niego dostęp przez określenie stosunkowo krótka nazwa zamiast konieczności określania pełną ścieżkę do pliku.</span><span class="sxs-lookup"><span data-stu-id="9bd87-106">For command-line interfaces such as Cmd.exe, when you are in the same folder as a particular file, you can access it by specifying a relatively short name, rather than needing to specify the entire path to the file.</span></span> <span data-ttu-id="9bd87-107">Bieżący katalog nosi nazwę katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="9bd87-107">The current directory is called the working directory.</span></span>

<span data-ttu-id="9bd87-108">Windows PowerShell korzysta z rzeczownikiem **lokalizacji** do odwoływania się do katalogu roboczego i implementuje rodzinę poleceń cmdlet do badania i manipulowania Twojej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="9bd87-108">Windows PowerShell uses the noun **Location** to refer to the working directory, and implements a family of cmdlets to examine and manipulate your location.</span></span>

## <a name="getting-your-current-location-get-location"></a><span data-ttu-id="9bd87-109">Pobieranie bieżącej lokalizacji (Get lokalizacji)</span><span class="sxs-lookup"><span data-stu-id="9bd87-109">Getting Your Current Location (Get-Location)</span></span>

<span data-ttu-id="9bd87-110">Aby określić ścieżkę swoją bieżącą lokalizację katalogu, wpisz **Get-Location** polecenia:</span><span class="sxs-lookup"><span data-stu-id="9bd87-110">To determine the path of your current directory location, enter the **Get-Location** command:</span></span>

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="9bd87-111">Polecenie cmdlet Get-Location jest podobny do **pwd** polecenie w powłoce BASH.</span><span class="sxs-lookup"><span data-stu-id="9bd87-111">The Get-Location cmdlet is similar to the **pwd** command in the BASH shell.</span></span> <span data-ttu-id="9bd87-112">Polecenia cmdlet Set-Location jest podobny do **cd** polecenia w pliku Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="9bd87-112">The Set-Location cmdlet is similar to the **cd** command in Cmd.exe.</span></span>

## <a name="setting-your-current-location-set-location"></a><span data-ttu-id="9bd87-113">Ustawianie bieżącej lokalizacji (zestaw lokalizacji)</span><span class="sxs-lookup"><span data-stu-id="9bd87-113">Setting Your Current Location (Set-Location)</span></span>

<span data-ttu-id="9bd87-114">**Get-Location** polecenie jest używane z **Ustawianie lokalizacji** polecenia.</span><span class="sxs-lookup"><span data-stu-id="9bd87-114">The **Get-Location** command is used with the **Set-Location** command.</span></span> <span data-ttu-id="9bd87-115">**Ustawianie lokalizacji** polecenia można określić swoją bieżącą lokalizację katalogu.</span><span class="sxs-lookup"><span data-stu-id="9bd87-115">The **Set-Location** command allows you to specify your current directory location.</span></span>

```powershell
Set-Location -Path C:\Windows
```

<span data-ttu-id="9bd87-116">Po wprowadzeniu polecenia, można zauważyć, że nie otrzymasz żadnych informacji zwrotnych o efekt polecenia.</span><span class="sxs-lookup"><span data-stu-id="9bd87-116">After you enter the command, you will notice that you do not receive any direct feedback about the effect of the command.</span></span> <span data-ttu-id="9bd87-117">Większość poleceń programu Windows PowerShell, którzy wykonują akcję generuje niewielkiego lub żadnego danych wyjściowych, ponieważ dane wyjściowe nie są zawsze przydatne.</span><span class="sxs-lookup"><span data-stu-id="9bd87-117">Most Windows PowerShell commands that perform an action produce little or no output because the output is not always useful.</span></span> <span data-ttu-id="9bd87-118">Aby sprawdzić, czy katalog pomyślne uległo zmianie po wprowadzeniu **Ustawianie lokalizacji** polecenie, podając **- PassThru** parametru po wprowadzeniu **Set-Location**polecenia:</span><span class="sxs-lookup"><span data-stu-id="9bd87-118">To verify that a successful directory change has occurred when you enter the **Set-Location** command, include the **-PassThru** parameter when you enter the **Set-Location** command:</span></span>

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

<span data-ttu-id="9bd87-119">**- PassThru** parametru należy używać za pomocą wielu poleceń Set w programie Windows PowerShell do zwracania informacji dotyczących wynik w przypadkach, w których jest nie domyślne dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="9bd87-119">The **-PassThru** parameter can be used with many Set commands in Windows PowerShell to return information about the result in cases in which there is no default output.</span></span>

<span data-ttu-id="9bd87-120">Można określić ścieżki względem Twojej bieżącej lokalizacji w taki sam sposób, jak w większości systemów UNIX i Windows będzie można poleceń powłoki.</span><span class="sxs-lookup"><span data-stu-id="9bd87-120">You can specify paths relative to your current location in the same way as you would in most UNIX and Windows command shells.</span></span> <span data-ttu-id="9bd87-121">W standardowej notacji dla ścieżek względnych okres (**.**) reprezentuje bieżącego folderu i podwojone okres (**...** ) reprezentuje katalog nadrzędny Twojej bieżącej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="9bd87-121">In standard notation for relative paths, a period (**.**)represents your current folder, and a doubled period (**..**) represents the parent directory of your current location.</span></span>

<span data-ttu-id="9bd87-122">Na przykład, jeśli znajdują się w **C:\\Windows** folderu, kropka (**.**) reprezentuje **C:\\Windows** i podwojonym współczynnikiem kropki (**...** ) reprezentują **C:**.</span><span class="sxs-lookup"><span data-stu-id="9bd87-122">For example, if you are in the **C:\\Windows** folder, a period (**.**)represents **C:\\Windows** and double periods (**..**) represent **C:**.</span></span> <span data-ttu-id="9bd87-123">Możesz zmienić z bieżącej lokalizacji w katalogu głównym dysku C:, wpisując:</span><span class="sxs-lookup"><span data-stu-id="9bd87-123">You can change from your current location to the root of the C: drive by typing:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

<span data-ttu-id="9bd87-124">Ta sama technika działa na dyskach programu Windows PowerShell, które nie są dysków z systemem plików, takich jak **HKLM:**.</span><span class="sxs-lookup"><span data-stu-id="9bd87-124">The same technique works on Windows PowerShell drives that are not file system drives, such as **HKLM:**.</span></span> <span data-ttu-id="9bd87-125">Można ustawić dla Twojej lokalizacji HKLM\\oprogramowania klucz rejestru, wpisując:</span><span class="sxs-lookup"><span data-stu-id="9bd87-125">You can set your location to the HKLM\\Software key in the registry by typing:</span></span>

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

<span data-ttu-id="9bd87-126">Można później zmienić lokalizację katalogu, na katalog nadrzędny, który jest katalogiem głównym Windows PowerShell HKLM: dysk przy użyciu ścieżki względnej:</span><span class="sxs-lookup"><span data-stu-id="9bd87-126">You can then change the directory location to the parent directory, which is the root of the Windows PowerShell HKLM: drive, by using a relative path:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

<span data-ttu-id="9bd87-127">Można wpisać Ustawianie lokalizacji lub użyć dowolnej z wbudowanych aliasy środowiska Windows PowerShell dla lokalizacji zestawu (cd, chdir, sl).</span><span class="sxs-lookup"><span data-stu-id="9bd87-127">You can type Set-Location or use any of the built-in Windows PowerShell aliases for Set-Location (cd, chdir, sl).</span></span> <span data-ttu-id="9bd87-128">Przykład:</span><span class="sxs-lookup"><span data-stu-id="9bd87-128">For example:</span></span>

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

## <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a><span data-ttu-id="9bd87-129">Zapisywanie i ponowne wywoływanie ostatnich lokalizacji (lokalizacja wypychania i lokalizacji Pop)</span><span class="sxs-lookup"><span data-stu-id="9bd87-129">Saving and Recalling Recent Locations (Push-Location and Pop-Location)</span></span>

<span data-ttu-id="9bd87-130">Zmiana lokalizacji, jest przydatne, aby śledzić, gdy zostały i aby można było powrócić do poprzedniej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="9bd87-130">When changing locations, it is helpful to keep track of where you have been and to be able to return to your previous location.</span></span> <span data-ttu-id="9bd87-131">**Lokalizacji wypychania** polecenie cmdlet w programie Windows PowerShell tworzy uporządkowane historii ("stos") ścieżek katalogów, w którym nastąpiło i możesz przejść wstecz przez historię ścieżek katalogów przy użyciu uzupełniające  **Lokalizacji POP** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9bd87-131">The **Push-Location** cmdlet in Windows PowerShell creates a ordered history (a "stack") of directory paths where you have been, and you can step back through the history of directory paths by using the complementary **Pop-Location** cmdlet.</span></span>

<span data-ttu-id="9bd87-132">Na przykład programu Windows PowerShell zazwyczaj rozpoczyna się w katalogu macierzystym użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9bd87-132">For example, Windows PowerShell typically starts in the user's home directory.</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="9bd87-133">Wyraz *stosu* ma specjalne znaczenie w wielu ustawień programowania, w tym .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9bd87-133">The word *stack* has a special meaning in many programming settings, including .NET Framework.</span></span> <span data-ttu-id="9bd87-134">Podobnie jak fizyczny stosu elementów ostatni element, które można umieścić na stosie jest pierwszym elementem, którego możesz ściągnąć ze stosu.</span><span class="sxs-lookup"><span data-stu-id="9bd87-134">Like a physical stack of items, the last item you put onto the stack is the first item that you can pull off the stack.</span></span> <span data-ttu-id="9bd87-135">Dodanie elementu do stosu potocznie jest określany jako "wypychania" element na stosie.</span><span class="sxs-lookup"><span data-stu-id="9bd87-135">Adding an item to a stack is colloquially known as "pushing" the item onto the stack.</span></span> <span data-ttu-id="9bd87-136">Pobieranie elementu ze stosu potocznie jest określany jako "o wyświetlaniu" element ze stosu.</span><span class="sxs-lookup"><span data-stu-id="9bd87-136">Pulling an item off the stack is colloquially known as "popping" the item off the stack.</span></span>

<span data-ttu-id="9bd87-137">Aby wypychanie bieżącej lokalizacji na stosie, a następnie przejdź do folderu Ustawienia lokalne, wpisz:</span><span class="sxs-lookup"><span data-stu-id="9bd87-137">To push the current location onto the stack, and then move to the Local Settings folder, type:</span></span>

```powershell
Push-Location -Path "Local Settings"
```

<span data-ttu-id="9bd87-138">Możesz następnie Wypychanie do lokalizacji ustawienia lokalne na stosie i przejdź do folderu Temp, wpisując:</span><span class="sxs-lookup"><span data-stu-id="9bd87-138">You can then push the Local Settings location onto the stack and move to the Temp folder by typing:</span></span>

```powershell
Push-Location -Path Temp
```

<span data-ttu-id="9bd87-139">Możesz sprawdzić, czy katalogi zmienione przystępując **Get-Location** polecenia:</span><span class="sxs-lookup"><span data-stu-id="9bd87-139">You can verify that you changed directories by entering the **Get-Location** command:</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

<span data-ttu-id="9bd87-140">Możesz następnie pop do ostatnio odwiedzonego katalogu, wprowadzając **lokalizacji Pop** polecenia i sprawdzić zmiany, wprowadzając **Get-Location** polecenia:</span><span class="sxs-lookup"><span data-stu-id="9bd87-140">You can then pop back into the most recently visited directory by entering the **Pop-Location** command, and verify the change by entering the **Get-Location** command:</span></span>

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

<span data-ttu-id="9bd87-141">Podobnie jak **Ustawianie lokalizacji** polecenia cmdlet, można dołączyć **- PassThru** parametru po wprowadzeniu **lokalizacji Pop** polecenia cmdlet, aby wyświetlić katalog, w którym możesz wprowadzić:</span><span class="sxs-lookup"><span data-stu-id="9bd87-141">Just as with the **Set-Location** cmdlet, you can include the **-PassThru** parameter when you enter the **Pop-Location** cmdlet to display the directory that you entered:</span></span>

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

<span data-ttu-id="9bd87-142">Można również używać poleceń cmdlet lokalizacji, za pomocą ścieżek sieciowych.</span><span class="sxs-lookup"><span data-stu-id="9bd87-142">You can also use the Location cmdlets with network paths.</span></span> <span data-ttu-id="9bd87-143">Jeśli masz serwer o nazwie FS01 udział o nazwie publiczne, można zmienić lokalizacji, wpisując</span><span class="sxs-lookup"><span data-stu-id="9bd87-143">If you have a server named FS01 with an share named Public, you can change your location by typing</span></span>

```powershell
Set-Location \\FS01\Public
```

<span data-ttu-id="9bd87-144">lub</span><span class="sxs-lookup"><span data-stu-id="9bd87-144">or</span></span>

```powershell
Push-Location \\FS01\Public
```

<span data-ttu-id="9bd87-145">Możesz użyć **lokalizacji wypychania** i **Ustawianie lokalizacji** polecenia, aby zmienić lokalizację do dowolnego dostępnego dysku.</span><span class="sxs-lookup"><span data-stu-id="9bd87-145">You can use the **Push-Location** and **Set-Location** commands to change the location to any available drive.</span></span> <span data-ttu-id="9bd87-146">Na przykład, jeśli masz dysk CD-ROM lokalny z literą dysku D, który zawiera dysk CD z danymi, zmianą lokalizacji na dysku CD, wprowadzając **D: Ustawianie lokalizacji** polecenia.</span><span class="sxs-lookup"><span data-stu-id="9bd87-146">For example, if you have a local CD-ROM drive with drive letter D that contains a data CD, you can change the location to the CD drive by entering the **Set-Location D:** command.</span></span>

<span data-ttu-id="9bd87-147">Jeśli dysk jest pusta, zostanie wyświetlony następujący komunikat o błędzie:</span><span class="sxs-lookup"><span data-stu-id="9bd87-147">If the drive is empty, you will get the following error message:</span></span>

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

<span data-ttu-id="9bd87-148">Korzystając z interfejsu wiersza polecenia, nie jest wygodne, użyj Eksploratora plików, aby sprawdzić dostępne dyski fizyczne.</span><span class="sxs-lookup"><span data-stu-id="9bd87-148">When you are using a command-line interface, it is not convenient to use File Explorer to examine the available physical drives.</span></span> <span data-ttu-id="9bd87-149">Ponadto Eksploratora plików będą wyświetlane wszystkie dyski programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9bd87-149">Also, File Explorer would not show you the all of the Windows PowerShell drives.</span></span> <span data-ttu-id="9bd87-150">Programu Windows PowerShell udostępnia zestaw poleceń do manipulowania dysków programu Windows PowerShell, a następnie zostaną omówione te dalej.</span><span class="sxs-lookup"><span data-stu-id="9bd87-150">Windows PowerShell provides a set of commands for manipulating Windows PowerShell drives, and we will talk about these next.</span></span>
