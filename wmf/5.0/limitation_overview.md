---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4b006d2ac812abf1f281b6b4e382c2760f92a95c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186834"
---
# <a name="known-issues-and-limitations"></a><span data-ttu-id="2e1ea-102">Znane problemy i ograniczenia</span><span class="sxs-lookup"><span data-stu-id="2e1ea-102">Known Issues and Limitations</span></span>

<a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="2e1ea-103">Skróty programu PowerShell są dzielone, gdy jest używany po raz pierwszy</span><span class="sxs-lookup"><span data-stu-id="2e1ea-103">PowerShell Shortcuts are broken when used for the first time</span></span>
------------------------------------------------------------

<span data-ttu-id="2e1ea-104">**Rozwiązanie:** wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="2e1ea-104">**Resolution:** Perform one of the following actions:</span></span>

1.  <span data-ttu-id="2e1ea-105">Kliknij prawym przyciskiem myszy skrót programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-105">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="2e1ea-106">Wybierz "Środowiska Windows PowerShell" można uruchomić w trybie bez podniesionych uprawnień.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-106">Select “Windows PowerShell” to launch in a non-elevated mode.</span></span>
2.  <span data-ttu-id="2e1ea-107">Kliknij prawym przyciskiem myszy skrót programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-107">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="2e1ea-108">Kliknij prawym przyciskiem myszy kliknij "Środowiska Windows PowerShell" i wybierz pozycję "Uruchom jako Administrator" były uruchamiane w trybie z podniesionymi uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-108">Right click on “Windows PowerShell” and select “Run As Administrator” to launch in an elevated mode.</span></span>

<span data-ttu-id="2e1ea-109">Po wykonaniu dowolnej z powyższych akcji skróty programu PowerShell będzie działać.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-109">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="2e1ea-110">Czynności te należy wykonać tylko raz.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-110">These actions need to be performed only once.</span></span>


<a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="2e1ea-111">Moduły programu PowerShell i zasoby DSC raportować błędy dotyczące ExecutionPolicy w systemie Windows 7</span><span class="sxs-lookup"><span data-stu-id="2e1ea-111">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>
-------------------------------------------------------------------------------------
<span data-ttu-id="2e1ea-112">W systemie Windows 7 użyj moduły programu PowerShell i zasobów DSC może spowodować błędy raportowane o ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-112">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="2e1ea-113">**Rozwiązanie:** ustawić ExecutionPolicy RemoteSigned, uruchamiając następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień (Uruchom jako Administrator):</span><span class="sxs-lookup"><span data-stu-id="2e1ea-113">**Resolution:** Set the ExecutionPolicy to RemoteSigned by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

<a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="2e1ea-114">Nawiązywanie starego zdalny punkt końcowy wymiany powoduje awarii</span><span class="sxs-lookup"><span data-stu-id="2e1ea-114">Connecting to an old remote Exchange endpoint causes a crash</span></span>
------------------------------------------------------------

<span data-ttu-id="2e1ea-115">Stary punkt końcowy wymiany przekierowuje do nowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-115">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="2e1ea-116">Usterki logiki przekierowania powstałą w jest awarii.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-116">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="2e1ea-117">**Rozwiązanie:** Połącz bezpośrednio z nowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-117">**Resolution:** Connect directly to the new endpoint.</span></span>


<a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="2e1ea-118">Funkcja rejestrowania spisu oprogramowania przez pomyłkę zostanie zatrzymana po zakończeniu instalacji WMF 5.0 w systemie Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="2e1ea-118">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>
-------------------------------------------------------------------------------------------------------------

<span data-ttu-id="2e1ea-119">Podczas instalowania WMF 5.0 na Windows Server 2012 R2, która jest już uruchomiona SIL, funkcję rejestrowania spisu oprogramowania przez pomyłkę zostanie zatrzymana po zakończeniu instalacji.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-119">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="2e1ea-120">**Rozwiązanie:** uruchomić polecenie cmdlet Start-SilLogging raz po zainstalowaniu pakietu WMF, ponieważ proces instalacji błędnie przestanie funkcję rejestrowania spisu oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-120">**Resolution:** Run the Start-SilLogging cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

<a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="2e1ea-121">Get-ChildItem nie działa, jeśli - LiteralPath i - Recurse są używane razem</span><span class="sxs-lookup"><span data-stu-id="2e1ea-121">Get-ChildItem does not work if -LiteralPath and -Recurse are used together</span></span>
--------------------------------------------------------------------------

<span data-ttu-id="2e1ea-122">Jeśli nazwa katalogu zawiera nieprawidłowy symbol wieloznaczny, następnie Get-ChildItem nie zapewni oczekiwanych rezultatów przy zarówno - LiteralPath i - Recurse są używane razem.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-122">If a directory name contains an invalid wildcard character, then Get-ChildItem will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="2e1ea-123">**Rozwiązanie:** nie nadaje się doskonale, ale bieżący obejściem jest wdrożenie rekursji w skrypcie, a nie zależą od polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-123">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>


<a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="2e1ea-124">Program Sysprep nie powiedzie się po zainstalowaniu pakietu WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="2e1ea-124">Sysprep fails after WMF 5.0 installation</span></span>
----------------------------------------

<span data-ttu-id="2e1ea-125">Istnieją dwa obejścia tego problemu, w zależności od wersji systemu Windows Server są uruchomione.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-125">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="2e1ea-126">**Rozwiązanie:**</span><span class="sxs-lookup"><span data-stu-id="2e1ea-126">**Resolution:**</span></span>
- <span data-ttu-id="2e1ea-127">Dla komputerów z systemami **systemu Windows Server 2008 R2**</span><span class="sxs-lookup"><span data-stu-id="2e1ea-127">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="2e1ea-128">Otwórz program Powershell jako administrator</span><span class="sxs-lookup"><span data-stu-id="2e1ea-128">Open Powershell as an administrator</span></span>
  2. <span data-ttu-id="2e1ea-129">Uruchom następujące polecenie</span><span class="sxs-lookup"><span data-stu-id="2e1ea-129">Run the following command</span></span>

  ```powershell
    Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
  ```
  3. <span data-ttu-id="2e1ea-130">Uruchom polecenie i zignorować błąd, są one prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-130">Run the command and ignore the error, as they are expected.</span></span>

  ```powershell
    Publish-SilData
   ```
  4. <span data-ttu-id="2e1ea-131">Usuń pliki w katalogu \Windows\System32\Logfiles\SIL\\</span><span class="sxs-lookup"><span data-stu-id="2e1ea-131">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>

  ```powershell
    Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
  ```
  5. <span data-ttu-id="2e1ea-132">Zainstalowanie dostępne ważne aktualizacje systemu Windows oraz operacji Sysyprep normalnie.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-132">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>

- <span data-ttu-id="2e1ea-133">Dla komputerów z systemami **systemu Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="2e1ea-133">For systems running **Windows Server 2012**</span></span>
  1.    <span data-ttu-id="2e1ea-134">Po zainstalowaniu pakietu WMF 5.0 na serwerze, aby być w Sysprep d, zaloguj się jako administrator.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-134">After installing WMF 5.0 on the server to be Sysprep’d, login as administrator.</span></span>
  2.    <span data-ttu-id="2e1ea-135">Skopiuj Generize.xml z katalogu \Windows\System32\Sysprep\ActionFiles\ do lokalizacji poza katalog Windows C:\ na przykład.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-135">Copy Generize.xml from directory \Windows\System32\Sysprep\ActionFiles\ to a location outside of the Windows directory, C:\ for example.</span></span>
  3.    <span data-ttu-id="2e1ea-136">Twoja kopia Generalize.xml Otwórz w Notatniku.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-136">Open your Generalize.xml copy with notepad.</span></span>
  4.    <span data-ttu-id="2e1ea-137">Znajdź i usuń następujący tekst: jedno wystąpienie każdego musi zostać usunięte (zostaną one zbliża się koniec dokumentu).</span><span class="sxs-lookup"><span data-stu-id="2e1ea-137">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

    ```
    <sysprepOrder order="0x3200"></sysprepOrder>
    <sysprepOrder order="0x3300"></sysprepOrder>
    ```

  5.    <span data-ttu-id="2e1ea-138">Zapisywania edytowanej kopii Generalize.xml i zamknij plik.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-138">Save the edited copy of Generalize.xml and close the file.</span></span>
  6.    <span data-ttu-id="2e1ea-139">Otwórz wiersz polecenia jako administrator</span><span class="sxs-lookup"><span data-stu-id="2e1ea-139">Open a command prompt as administrator</span></span>
  7.    <span data-ttu-id="2e1ea-140">Uruchom następujące polecenie, aby przejąć na własność pliku Generalize.xml w folderze system32:</span><span class="sxs-lookup"><span data-stu-id="2e1ea-140">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

    ```
    Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```

  8.    <span data-ttu-id="2e1ea-141">Uruchom następujące polecenie, aby ustawić odpowiednie uprawnienia do pliku:</span><span class="sxs-lookup"><span data-stu-id="2e1ea-141">Run the following command to set appropriate permission on the file:</span></span>

    ```
    Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
    ```
      * <span data-ttu-id="2e1ea-142">Odpowiedź tak na monit o potwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-142">Answer Yes at the prompt for confirmation.</span></span>
      * <span data-ttu-id="2e1ea-143">Należy pamiętać, że `<AdministratorUserName>` powinna zostać zastąpiona przez nazwę użytkownika, który jest administratorem na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-143">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="2e1ea-144">Na przykład "Administrator".</span><span class="sxs-lookup"><span data-stu-id="2e1ea-144">For example, "Administrator".</span></span>

  9.    <span data-ttu-id="2e1ea-145">Skopiuj plik, edytować i zapisać za pośrednictwem katalogu Sysprep przy użyciu następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="2e1ea-145">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

    ```
    xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```
      * <span data-ttu-id="2e1ea-146">Odpowiedź tak, aby zastąpić (należy pamiętać, że jeśli nie ma żadnego monitu, aby zastąpić, double Sprawdź wprowadzona ścieżka).</span><span class="sxs-lookup"><span data-stu-id="2e1ea-146">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
      * <span data-ttu-id="2e1ea-147">Przyjęto założenie, że Twoje edytowanej kopii Generalize.xml został skopiowany do C:\.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-147">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10.   <span data-ttu-id="2e1ea-148">Generalize.XML został zaktualizowany o obejście.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-148">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="2e1ea-149">Uruchom program Sysprep z włączoną opcją generalize.</span><span class="sxs-lookup"><span data-stu-id="2e1ea-149">Please run Sysprep with the generalize option enabled.</span></span>
