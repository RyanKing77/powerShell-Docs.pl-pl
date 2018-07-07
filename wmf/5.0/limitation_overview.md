---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4eb2f0bac4f2169a9a06d80cb4fa214a09cdfa86
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892988"
---
# <a name="known-issues-and-limitations"></a><span data-ttu-id="e27a4-102">Znane problemy i ograniczenia</span><span class="sxs-lookup"><span data-stu-id="e27a4-102">Known Issues and Limitations</span></span>

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="e27a4-103">Skróty programu PowerShell są otwarte w przypadku, gdy po raz pierwszy użyty</span><span class="sxs-lookup"><span data-stu-id="e27a4-103">PowerShell Shortcuts are broken when used for the first time</span></span>

<span data-ttu-id="e27a4-104">**Rozwiązanie:** wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="e27a4-104">**Resolution:** Perform one of the following actions:</span></span>

1. <span data-ttu-id="e27a4-105">Kliknij prawym przyciskiem myszy skrót programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e27a4-105">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="e27a4-106">Wybierz pozycję "Windows PowerShell", aby uruchomić w trybie bez podniesionych uprawnień.</span><span class="sxs-lookup"><span data-stu-id="e27a4-106">Select “Windows PowerShell” to launch in a non-elevated mode.</span></span>
2. <span data-ttu-id="e27a4-107">Kliknij prawym przyciskiem myszy skrót programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e27a4-107">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="e27a4-108">Kliknij prawym przyciskiem myszy kliknij "Windows PowerShell" i wybierz pozycję "Uruchom jako Administrator" można uruchomić w trybie podniesionych uprawnień.</span><span class="sxs-lookup"><span data-stu-id="e27a4-108">Right click on “Windows PowerShell” and select “Run As Administrator” to launch in an elevated mode.</span></span>

<span data-ttu-id="e27a4-109">Po wykonaniu jednej z powyższych akcji skróty programu PowerShell będzie działać.</span><span class="sxs-lookup"><span data-stu-id="e27a4-109">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="e27a4-110">Te akcje muszą być wykonywane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="e27a4-110">These actions need to be performed only once.</span></span>

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="e27a4-111">Moduły programu PowerShell i zasobów DSC raportowania błędów dotyczących ExecutionPolicy Windows 7</span><span class="sxs-lookup"><span data-stu-id="e27a4-111">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>

<span data-ttu-id="e27a4-112">Windows 7 korzystanie z modułów programu PowerShell i zasobów DSC może spowodować błędy raportowane o ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="e27a4-112">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="e27a4-113">**Rozwiązanie:** ustawić ExecutionPolicy RemoteSigned, uruchamiając następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień (Uruchom jako Administrator):</span><span class="sxs-lookup"><span data-stu-id="e27a4-113">**Resolution:** Set the ExecutionPolicy to RemoteSigned by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="e27a4-114">Łączenie do starego zdalnego punktu końcowego programu Exchange powoduje awarię</span><span class="sxs-lookup"><span data-stu-id="e27a4-114">Connecting to an old remote Exchange endpoint causes a crash</span></span>

<span data-ttu-id="e27a4-115">Stary punkt końcowy wymiany przekierowuje do nowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e27a4-115">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="e27a4-116">Brak usterkę w logice przekierowania powstałą w awarii.</span><span class="sxs-lookup"><span data-stu-id="e27a4-116">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="e27a4-117">**Rozwiązanie:** Połącz bezpośrednio z nowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e27a4-117">**Resolution:** Connect directly to the new endpoint.</span></span>

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="e27a4-118">Funkcja rejestrowania spisu oprogramowania jest błędnie zatrzymana po zakończeniu instalacji programu WMF 5.0 w systemie Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="e27a4-118">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>

<span data-ttu-id="e27a4-119">Podczas instalowania programu WMF 5.0 na Windows Server 2012 R2, który jest już uruchomiony program SIL, funkcję rejestrowania spisu oprogramowania jest błędnie zatrzymana po zakończeniu instalacji.</span><span class="sxs-lookup"><span data-stu-id="e27a4-119">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="e27a4-120">**Rozwiązanie:** Uruchom polecenie cmdlet Start-SilLogging raz po zakończeniu instalacji programu WMF, ponieważ proces instalacji błędnie przestanie funkcję rejestrowania spisu oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="e27a4-120">**Resolution:** Run the Start-SilLogging cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="e27a4-121">`Get-ChildItem` nie działa, jeśli - LiteralPath i - Recurse są używane razem</span><span class="sxs-lookup"><span data-stu-id="e27a4-121">`Get-ChildItem` does not work if -LiteralPath and -Recurse are used together</span></span>

<span data-ttu-id="e27a4-122">Jeśli nazwa katalogu zawiera nieprawidłowy symbol wieloznaczny, następnie `Get-ChildItem` nie przyniesie oczekiwanych rezultatów, gdy - LiteralPath i - Recurse są używane razem.</span><span class="sxs-lookup"><span data-stu-id="e27a4-122">If a directory name contains an invalid wildcard character, then `Get-ChildItem` will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="e27a4-123">**Rozwiązanie:** nie idealnym rozwiązaniem, ale bieżące obejście polega na implementowanie rekursji w skrypcie, zamiast polegać na polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e27a4-123">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>

## <a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="e27a4-124">Program Sysprep zakończy się niepowodzeniem po instalacji programu WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="e27a4-124">Sysprep fails after WMF 5.0 installation</span></span>

<span data-ttu-id="e27a4-125">Istnieją dwa obejścia tego problemu, w zależności od wersji systemu Windows Server są uruchomione.</span><span class="sxs-lookup"><span data-stu-id="e27a4-125">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="e27a4-126">**Rozwiązanie:**</span><span class="sxs-lookup"><span data-stu-id="e27a4-126">**Resolution:**</span></span>

- <span data-ttu-id="e27a4-127">Dla komputerów z systemami **systemu Windows Server 2008 R2**</span><span class="sxs-lookup"><span data-stu-id="e27a4-127">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="e27a4-128">Otwórz program Powershell jako administrator</span><span class="sxs-lookup"><span data-stu-id="e27a4-128">Open Powershell as an administrator</span></span>
  2. <span data-ttu-id="e27a4-129">Uruchom następujące polecenie</span><span class="sxs-lookup"><span data-stu-id="e27a4-129">Run the following command</span></span>

     ```powershell
     Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
     ```

  3. <span data-ttu-id="e27a4-130">Uruchom polecenie i zignorować błąd, ponieważ oczekuje.</span><span class="sxs-lookup"><span data-stu-id="e27a4-130">Run the command and ignore the error, as they are expected.</span></span>

     ```powershell
     Publish-SilData
     ```

  4. <span data-ttu-id="e27a4-131">Usuwanie plików w katalogu \Windows\System32\Logfiles\SIL\\</span><span class="sxs-lookup"><span data-stu-id="e27a4-131">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. <span data-ttu-id="e27a4-132">Instalowanie wszystkich dostępnych ważnych aktualizacji Windows i rozpocząć operację Sysyprep normalnie.</span><span class="sxs-lookup"><span data-stu-id="e27a4-132">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>

- <span data-ttu-id="e27a4-133">Dla komputerów z systemami **systemu Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="e27a4-133">For systems running **Windows Server 2012**</span></span>
  1. <span data-ttu-id="e27a4-134">Po zainstalowaniu programu WMF 5.0 na serwerze, aby być w Sysprep'd, zaloguj się jako administrator.</span><span class="sxs-lookup"><span data-stu-id="e27a4-134">After installing WMF 5.0 on the server to be Sysprep’d, login as administrator.</span></span>
  2. <span data-ttu-id="e27a4-135">Skopiuj Generize.xml z \Windows\System32\Sysprep\ActionFiles\ katalogu do lokalizacji poza katalogiem Windows, C:\ na przykład.</span><span class="sxs-lookup"><span data-stu-id="e27a4-135">Copy Generize.xml from directory \Windows\System32\Sysprep\ActionFiles\ to a location outside of the Windows directory, C:\ for example.</span></span>
  3. <span data-ttu-id="e27a4-136">Otwórz kopii Generalize.xml w Notatniku.</span><span class="sxs-lookup"><span data-stu-id="e27a4-136">Open your Generalize.xml copy with notepad.</span></span>
  4. <span data-ttu-id="e27a4-137">Znajdź i usuń następujący tekst: jedno wystąpienie każdego musi zostać usunięte (będą one osiągnie koniec dokumentu).</span><span class="sxs-lookup"><span data-stu-id="e27a4-137">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. <span data-ttu-id="e27a4-138">Zapisywania edytowanej kopii Generalize.xml i zamknij plik.</span><span class="sxs-lookup"><span data-stu-id="e27a4-138">Save the edited copy of Generalize.xml and close the file.</span></span>
  6. <span data-ttu-id="e27a4-139">Otwórz wiersz polecenia jako administrator</span><span class="sxs-lookup"><span data-stu-id="e27a4-139">Open a command prompt as administrator</span></span>
  7. <span data-ttu-id="e27a4-140">Uruchom następujące polecenie, aby przejąć na własność pliku Generalize.xml w folderze system32:</span><span class="sxs-lookup"><span data-stu-id="e27a4-140">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. <span data-ttu-id="e27a4-141">Uruchom następujące polecenie, aby ustawić odpowiednie uprawnienia do pliku:</span><span class="sxs-lookup"><span data-stu-id="e27a4-141">Run the following command to set appropriate permission on the file:</span></span>

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - <span data-ttu-id="e27a4-142">Wybierz odpowiedź tak, w wierszu o potwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="e27a4-142">Answer Yes at the prompt for confirmation.</span></span>
     - <span data-ttu-id="e27a4-143">Należy pamiętać, że `<AdministratorUserName>` powinna zostać zastąpiona przez nazwę użytkownika, który jest administratorem na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e27a4-143">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="e27a4-144">Na przykład, "Administrator".</span><span class="sxs-lookup"><span data-stu-id="e27a4-144">For example, "Administrator".</span></span>

  9. <span data-ttu-id="e27a4-145">Skopiuj plik, edytować i zapisać za pośrednictwem katalogu programu Sysprep przy użyciu następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="e27a4-145">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - <span data-ttu-id="e27a4-146">Wybierz odpowiedź tak, aby zastąpić (należy pamiętać, że jeśli nie ma żadnego monitu, aby zastąpić, lub sprawdź wprowadzona ścieżka).</span><span class="sxs-lookup"><span data-stu-id="e27a4-146">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
     - <span data-ttu-id="e27a4-147">Przyjęto założenie, że Twoje edytowanej kopii Generalize.xml zostały skopiowane do C:\.</span><span class="sxs-lookup"><span data-stu-id="e27a4-147">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10. <span data-ttu-id="e27a4-148">Generalize.XML został zaktualizowany o obejście.</span><span class="sxs-lookup"><span data-stu-id="e27a4-148">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="e27a4-149">Po włączeniu opcji generalize, uruchom program Sysprep.</span><span class="sxs-lookup"><span data-stu-id="e27a4-149">Please run Sysprep with the generalize option enabled.</span></span>