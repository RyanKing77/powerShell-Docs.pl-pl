---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: keithb
title: Instalowanie i konfigurowanie WMF 5.1
ms.openlocfilehash: e5c7968744a442b4be9f1e43a45e91429a6d6165
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="install-and-configure-wmf-51"></a><span data-ttu-id="95fcc-103">Instalowanie i konfigurowanie WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="95fcc-103">Install and Configure WMF 5.1</span></span> #


## <a name="download-and-install-the-wmf-51-package"></a><span data-ttu-id="95fcc-104">Pobierz i zainstaluj pakiet WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="95fcc-104">Download and install the WMF 5.1 package</span></span>

<span data-ttu-id="95fcc-105">Pobierz pakiet WMF 5.1 dla systemu operacyjnego i architektury, które chcesz zainstalować ją na:</span><span class="sxs-lookup"><span data-stu-id="95fcc-105">Download the WMF 5.1 package for the operating system and architecture you wish to install it on:</span></span>

| <span data-ttu-id="95fcc-106">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="95fcc-106">Operating System</span></span>       | <span data-ttu-id="95fcc-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="95fcc-107">Prerequisites</span></span>           | <span data-ttu-id="95fcc-108">Łącza pakietu</span><span class="sxs-lookup"><span data-stu-id="95fcc-108">Package Links</span></span>                          |
|------------------------|-------------------------|----------------------------------------|
| <span data-ttu-id="95fcc-109">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="95fcc-109">Windows Server 2012 R2</span></span> |                         | <span data-ttu-id="95fcc-110">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="95fcc-110">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span> |
| <span data-ttu-id="95fcc-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="95fcc-111">Windows Server 2012</span></span>    |                         | <span data-ttu-id="95fcc-112">[W2K12-KB3191565-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="95fcc-112">[W2K12-KB3191565-x64.msu][]</span></span>            |
| <span data-ttu-id="95fcc-113">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="95fcc-113">Windows Server 2008 R2</span></span> | <span data-ttu-id="95fcc-114">[.NET framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="95fcc-114">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="95fcc-115">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="95fcc-115">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span>    |
| <span data-ttu-id="95fcc-116">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="95fcc-116">Windows 8.1</span></span>            |                         | <span data-ttu-id="95fcc-117">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="95fcc-117">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span></br><span data-ttu-id="95fcc-118">**x86:** [systemu Win8.1-KB3191564-x86.msu][]</span><span class="sxs-lookup"><span data-stu-id="95fcc-118">**x86:** [Win8.1-KB3191564-x86.msu][]</span></span> |
| <span data-ttu-id="95fcc-119">Windows 7 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="95fcc-119">Windows 7 SP1</span></span>          | <span data-ttu-id="95fcc-120">[.NET framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="95fcc-120">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="95fcc-121">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="95fcc-121">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span></br><span data-ttu-id="95fcc-122">**x86:** [Win7-KB3191566-x86.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="95fcc-122">**x86:** [Win7-KB3191566-x86.ZIP][]</span></span> |

[.NET framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[systemu Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a><span data-ttu-id="95fcc-129">Zainstaluj WMF 5.1 dla systemu Windows Server 2008 R2 i Windows 7</span><span class="sxs-lookup"><span data-stu-id="95fcc-129">Install WMF 5.1 for Windows Server 2008 R2 and Windows 7</span></span>

> <span data-ttu-id="95fcc-130">**Uwaga:** instrukcje instalacji systemu Windows Server 2008 R2 i Windows 7 zostały zmienione i różnią się od instrukcji dla innych pakietów.</span><span class="sxs-lookup"><span data-stu-id="95fcc-130">**Note:** Installation instructions for Windows Server 2008 R2 and Windows 7 have changed, and differ from the instructions for the other packages.</span></span> <span data-ttu-id="95fcc-131">Instrukcje dotyczące instalacji systemu Windows Server 2012 R2, Windows Server 2012 i Windows 8.1 są poniżej.</span><span class="sxs-lookup"><span data-stu-id="95fcc-131">Installation instructions for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1 are below.</span></span>

<span data-ttu-id="95fcc-132">**Instalowanie WMF 5.1 w systemie Windows Server 2008 R2 i Windows 7**</span><span class="sxs-lookup"><span data-stu-id="95fcc-132">**Installing WMF 5.1 on Windows Server 2008 R2 and Windows 7**</span></span>

1. <span data-ttu-id="95fcc-133">Przejdź do folderu, do którego został pobrany plik ZIP.</span><span class="sxs-lookup"><span data-stu-id="95fcc-133">Navigate to the folder into which you downloaded the ZIP file.</span></span>

2. <span data-ttu-id="95fcc-134">Kliknij prawym przyciskiem myszy w pliku ZIP, a następnie wybierz "Wyodrębnij wszystkie...".</span><span class="sxs-lookup"><span data-stu-id="95fcc-134">Right-click on the ZIP file, and select "Extract All...".</span></span> <span data-ttu-id="95fcc-135">Zip zawiera pliki 2: MSU i w pliku skryptu instalacji WMF5.1.PS1.</span><span class="sxs-lookup"><span data-stu-id="95fcc-135">The Zip contains 2 files: an MSU and the Install-WMF5.1.PS1 script file.</span></span>
<span data-ttu-id="95fcc-136">Po wypakowaniu plików ZIP, zawartość można skopiować na dowolnym komputerze z systemem Windows 7 lub Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="95fcc-136">Once you have unpacked the ZIP file, you can copy the contents to any machine running Windows 7 or Windows Server 2008 R2.</span></span>

3. <span data-ttu-id="95fcc-137">Po wyodrębnieniu zawartości pliku ZIP, Otwórz program PowerShell jako administrator, a następnie przejdź do folderu zawierającego zawartość pliku ZIP.</span><span class="sxs-lookup"><span data-stu-id="95fcc-137">After extracting the ZIP file contents, open PowerShell as administrator, then navigate to the folder containing the contents of the ZIP file.</span></span>

4. <span data-ttu-id="95fcc-138">Uruchom skrypt instalacji Wmf5.1.ps1 w tym folderze, a następnie postępuj zgodnie z instrukcjami.</span><span class="sxs-lookup"><span data-stu-id="95fcc-138">Run the Install-Wmf5.1.ps1 script in that folder, and follow the instructions.</span></span> <span data-ttu-id="95fcc-139">Ten skrypt Sprawdzanie wymagań wstępnych na komputerze lokalnym i zainstaluj WMF 5.1, jeśli wymagania wstępne zostały spełnione.</span><span class="sxs-lookup"><span data-stu-id="95fcc-139">This script will check the prerequisites on the local machine, and install WMF 5.1 if the prerequisites have been met.</span></span> <span data-ttu-id="95fcc-140">Poniżej przedstawiono wymagania wstępne.</span><span class="sxs-lookup"><span data-stu-id="95fcc-140">The prerequisites are listed below.</span></span>

<span data-ttu-id="95fcc-141">Zainstaluj WMF5.1.ps1 przyjmuje następujące parametry do jej obsługi ułatwiają automatyzowanie instalacji w systemie Windows Server 2008 R2 i Windows 7:</span><span class="sxs-lookup"><span data-stu-id="95fcc-141">Install-WMF5.1.ps1 takes the following parameters to ease automating the installation on Windows Server 2008 R2 and Windows 7:</span></span>

- <span data-ttu-id="95fcc-142">AcceptEula: Jeśli ten parametr jest dostarczany, Umowa licencyjna jest akceptowane automatycznie i nie będą wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="95fcc-142">AcceptEula: When this parameter is included, the EULA is automatically accepted and will not be displayed.</span></span>
- <span data-ttu-id="95fcc-143">AllowRestart: Ten parametr tylko można użyć, gdy AcceptEula został określony.</span><span class="sxs-lookup"><span data-stu-id="95fcc-143">AllowRestart: This parameter can only be used if AcceptEula is specified.</span></span> <span data-ttu-id="95fcc-144">Jeśli ten parametr jest dołączony, a następnie ponowne uruchomienie jest wymagane po zainstalowaniu pakietu WMF 5.1, ponowne uruchomienie nastąpi bez monitowania natychmiast po zakończeniu instalacji.</span><span class="sxs-lookup"><span data-stu-id="95fcc-144">If this parameter is included, and a restart is required after installing WMF 5.1, the restart will happen without prompting immediately after the installation is completed.</span></span>

<span data-ttu-id="95fcc-145">**WMF 5.1 wymagania wstępne dotyczące systemu Windows Server 2008 R2 z dodatkiem SP1 i Windows 7 z dodatkiem SP1**</span><span class="sxs-lookup"><span data-stu-id="95fcc-145">**WMF 5.1 Prerequisites for Windows Server 2008 R2 SP1 and Windows 7 SP1**</span></span>

<span data-ttu-id="95fcc-146">Instalacja programu WMF 5.1 w systemie Windows Server 2008 R2 z dodatkiem SP1 lub Windows 7 z dodatkiem SP1 wymaga następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="95fcc-146">Installation of WMF 5.1 on either Windows Server 2008 R2 SP1 or Windows 7 SP1, requires the following:</span></span>
- <span data-ttu-id="95fcc-147">Musi być zainstalowany najnowszy dodatek service pack.</span><span class="sxs-lookup"><span data-stu-id="95fcc-147">Latest service pack must be installed.</span></span>
- <span data-ttu-id="95fcc-148">WMF 3.0 **nie mogą** można zainstalować.</span><span class="sxs-lookup"><span data-stu-id="95fcc-148">WMF 3.0 **must not** be installed.</span></span> <span data-ttu-id="95fcc-149">Instalowanie WMF 5.1 za pośrednictwem WMF 3.0 spowoduje utratę PSModulePath, co może powodować inne aplikacje, aby zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="95fcc-149">Installing WMF 5.1 over WMF 3.0 will result in the loss of the PSModulePath, which can cause other applications to fail.</span></span> <span data-ttu-id="95fcc-150">Przed zainstalowaniem WMF 5.1, należy albo odinstalować pakietu AMF 3.0 lub Zapisz PSModulePath i przywracania go ręcznie po zakończeniu instalacji WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="95fcc-150">Before installing WMF 5.1, you must either un-install WMF 3.0, or save the PSModulePath and then restore it manually after WMF 5.1 installation is complete.</span></span>
- <span data-ttu-id="95fcc-151">WMF 5.1 wymaga co najmniej [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).</span><span class="sxs-lookup"><span data-stu-id="95fcc-151">WMF 5.1 requires at least [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).</span></span>
<span data-ttu-id="95fcc-152">Można zainstalować programu Microsoft .NET Framework 4.5.2, zgodnie z instrukcjami w lokalizacji pobierania.</span><span class="sxs-lookup"><span data-stu-id="95fcc-152">You can install Microsoft .NET Framework 4.5.2 by following the instructions at the download location.</span></span>

<span data-ttu-id="95fcc-153">**Zależności usługi WinRM**</span><span class="sxs-lookup"><span data-stu-id="95fcc-153">**WinRM Dependency**</span></span>

<span data-ttu-id="95fcc-154">Windows PowerShell Desired stan konfiguracji (DSC) zależy od usługi WinRM.</span><span class="sxs-lookup"><span data-stu-id="95fcc-154">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span>
<span data-ttu-id="95fcc-155">Usługa WinRM nie jest włączona domyślnie w systemie Windows Server 2008 R2 i Windows 7.</span><span class="sxs-lookup"><span data-stu-id="95fcc-155">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span>
<span data-ttu-id="95fcc-156">Uruchom `Set-WSManQuickConfig`, w programie Windows PowerShell z podwyższonym poziomem uprawnień sesji, aby włączyć usługę WinRM.</span><span class="sxs-lookup"><span data-stu-id="95fcc-156">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>


## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a><span data-ttu-id="95fcc-157">Zainstaluj WMF 5.1 dla systemu Windows Server 2012 R2, Windows Server 2012 i Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="95fcc-157">Install WMF 5.1 for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1</span></span>
<span data-ttu-id="95fcc-158">**Zainstaluj z Eksploratora Windows (lub Eksploratora plików w systemie Windows Server 2012 R2 lub Windows 8.1)**</span><span class="sxs-lookup"><span data-stu-id="95fcc-158">**Install from Windows Explorer (or File Explorer in Windows Server 2012 R2 or Windows 8.1)**</span></span>

1. <span data-ttu-id="95fcc-159">Przejdź do folderu, do którego został pobrany plik MSU.</span><span class="sxs-lookup"><span data-stu-id="95fcc-159">Navigate to the folder into which you downloaded the MSU file.</span></span>
2. <span data-ttu-id="95fcc-160">Kliknij dwukrotnie MSU go uruchomić.</span><span class="sxs-lookup"><span data-stu-id="95fcc-160">Double-click the MSU to run it.</span></span>

<span data-ttu-id="95fcc-161">**Instalowanie przy użyciu wiersza polecenia**</span><span class="sxs-lookup"><span data-stu-id="95fcc-161">**Installing from the Command Prompt**</span></span>

1. <span data-ttu-id="95fcc-162">Po pobraniu poprawny pakiet dla architektury komputera, Otwórz okno wiersza polecenia z podwyższonym poziomem uprawnień użytkownika (Uruchom jako Administrator).</span><span class="sxs-lookup"><span data-stu-id="95fcc-162">After downloading the correct package for your computer's architecture, open a Command Prompt window with elevated user rights (Run as Administrator).</span></span> <span data-ttu-id="95fcc-163">W opcji instalacji Server Core systemu Windows Server 2012 R2, Windows Server 2012 lub Windows Server 2008 R2 z dodatkiem SP1 wiersz polecenia z podwyższonym poziomem uprawnień użytkownika domyślnie otwierany.</span><span class="sxs-lookup"><span data-stu-id="95fcc-163">On the Server Core installation options of Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1, Command Prompt opens with elevated user rights by default.</span></span>
2. <span data-ttu-id="95fcc-164">Przejdź do folderu, do którego została pobrana lub kopiowane do pakietu instalacyjnego WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="95fcc-164">Change directories to the folder into which you have downloaded or copied the WMF 5.1 installation package.</span></span>
3. <span data-ttu-id="95fcc-165">Uruchom jedno z następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="95fcc-165">Run one of the following commands:</span></span>
   - <span data-ttu-id="95fcc-166">Uruchom na komputerach z systemem Windows Server 2012 R2 lub Windows 8.1 x64 `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="95fcc-166">On computers that are running Windows Server 2012 R2 or Windows 8.1 x64, run `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="95fcc-167">Na komputerach z systemem Windows Server 2012 Uruchom `W2K12-KB3191565-x64.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="95fcc-167">On computers that are running Windows Server 2012, run `W2K12-KB3191565-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="95fcc-168">Uruchom na komputerach z systemem Windows 8.1 x86 `Win8.1-KB3191564-x86.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="95fcc-168">On computers that are running Windows 8.1 x86, run `Win8.1-KB3191564-x86.msu /quiet`.</span></span>

> [!NOTE]
> <span data-ttu-id="95fcc-169">Instalowanie WMF 5.1 wymaga ponownego uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="95fcc-169">Installing WMF 5.1 requires a reboot.</span></span> <span data-ttu-id="95fcc-170">Przy użyciu `/quiet` opcja zostanie wykonany ponowny rozruch systemu bez ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="95fcc-170">Using the `/quiet` option will reboot the system without warning.</span></span>
> <span data-ttu-id="95fcc-171">Użyj `/norestart` opcję, aby uniknąć ponownego rozruchu.</span><span class="sxs-lookup"><span data-stu-id="95fcc-171">Use the `/norestart` option to avoid rebooting.</span></span> <span data-ttu-id="95fcc-172">Jednak WMF 5.1 nie zostanie zainstalowana, dopóki ponownym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="95fcc-172">However, WMF 5.1 will not be installed until you have rebooted.</span></span>
