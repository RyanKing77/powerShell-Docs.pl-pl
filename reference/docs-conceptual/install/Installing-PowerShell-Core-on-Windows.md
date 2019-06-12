---
title: Instalowanie programu PowerShell Core w systemie Windows
description: Informacje o instalowaniu programu PowerShell Core w Windows
ms.date: 08/06/2018
ms.openlocfilehash: 3f21761037311891162f1083234edb0aca80d28b
ms.sourcegitcommit: 4ec9e10647b752cc62b1eabb897ada3dc03c93eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830224"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="c98ad-103">Instalowanie programu PowerShell Core w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="c98ad-103">Installing PowerShell Core on Windows</span></span>

<span data-ttu-id="c98ad-104">Istnieje wiele sposobów, aby zainstalować program PowerShell Core w Windows.</span><span class="sxs-lookup"><span data-stu-id="c98ad-104">There are multiple ways to install PowerShell Core in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c98ad-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="c98ad-105">Prerequisites</span></span>

<span data-ttu-id="c98ad-106">Aby włączyć komunikację zdalną programu PowerShell za pośrednictwem usługi WS-Management, muszą zostać spełnione następujące wymagania wstępne:</span><span class="sxs-lookup"><span data-stu-id="c98ad-106">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="c98ad-107">Zainstaluj [uniwersalnego środowiska uruchomieniowego c.](https://www.microsoft.com/download/details.aspx?id=50410) na Windows wersjach wcześniejszych niż Windows 10.</span><span class="sxs-lookup"><span data-stu-id="c98ad-107">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="c98ad-108">Jest ona dostępna za pośrednictwem bezpośredniego pobierania lub Windows Update.</span><span class="sxs-lookup"><span data-stu-id="c98ad-108">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="c98ad-109">W pełni zastosować poprawki względem jakiegokolwiek (w tym opcjonalnych pakietów), obsługiwane systemy mają już to zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="c98ad-109">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="c98ad-110">Windows Management Framework (WMF) 4.0 lub nowszym należy zainstalować na Windows 7 i Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="c98ad-110">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="c98ad-111">Aby uzyskać więcej informacji na temat programu WMF, zobacz [Przegląd WMF](/powershell/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="c98ad-111">For more information about WMF, see [WMF Overview](/powershell/wmf/overview).</span></span>

## <a name="a-idmsi-installing-the-msi-package"></a><span data-ttu-id="c98ad-112"><a id="msi" />Instalowanie pakietu MSI</span><span class="sxs-lookup"><span data-stu-id="c98ad-112"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="c98ad-113">Aby zainstalować program PowerShell w klienta Windows lub Windows Server (działa w systemie Windows 7 z dodatkiem SP1, Server 2008 R2 i nowszych), Pobierz pakiet MSI w usłudze GitHub [zwalnia] [ releases] strony.</span><span class="sxs-lookup"><span data-stu-id="c98ad-113">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="c98ad-114">Przewiń w dół do **zasoby** części wersji, którą chcesz zainstalować.</span><span class="sxs-lookup"><span data-stu-id="c98ad-114">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="c98ad-115">Sekcja zasoby mogą być zwinięte, konieczne może być kliknij, aby ją rozwinąć.</span><span class="sxs-lookup"><span data-stu-id="c98ad-115">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="c98ad-116">Plik MSI wyglądają następująco — `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="c98ad-116">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="c98ad-117">Po pobraniu, kliknij dwukrotnie Instalatora, a następnie postępuj zgodnie z monitami.</span><span class="sxs-lookup"><span data-stu-id="c98ad-117">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="c98ad-118">Instalator tworzy skrót, w Windows Start Menu.</span><span class="sxs-lookup"><span data-stu-id="c98ad-118">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="c98ad-119">Domyślnie pakiet jest zainstalowany na `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="c98ad-119">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="c98ad-120">Można uruchomić programu PowerShell przy użyciu Start Menu lub `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="c98ad-120">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="c98ad-121">Administracyjne instalacji z wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="c98ad-121">Administrative install from the command line</span></span>

<span data-ttu-id="c98ad-122">Pakiety MSI można zainstalować z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c98ad-122">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="c98ad-123">Dzięki temu administratorzy mogą wdrażać pakiety bez interakcji z użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="c98ad-123">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="c98ad-124">Pakiet MSI środowiska PowerShell obejmuje następujące właściwości, aby określić opcje instalacji:</span><span class="sxs-lookup"><span data-stu-id="c98ad-124">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="c98ad-125">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** — ta właściwość określa opcję dodawania **Otwórz program PowerShell** element do menu kontekstowego w Eksploratorze Windows.</span><span class="sxs-lookup"><span data-stu-id="c98ad-125">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="c98ad-126">**ENABLE_PSREMOTING** — ta właściwość określa opcja włączania komunikacji zdalnej programu PowerShell podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="c98ad-126">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="c98ad-127">**REGISTER_MANIFEST** — ta właściwość określa opcję rejestrowania manifestu rejestrowania zdarzeń Windows.</span><span class="sxs-lookup"><span data-stu-id="c98ad-127">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="c98ad-128">Poniższy przykład pokazuje, jak do przeprowadzenia instalacji dyskretnej programu PowerShell Core ze wszystkimi opcjami instalacji włączone.</span><span class="sxs-lookup"><span data-stu-id="c98ad-128">The following examples shows how to silently install PowerShell Core with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="c98ad-129">Aby uzyskać pełną listę opcji wiersza polecenia msiexec.exe zobacz [opcje wiersza polecenia](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="c98ad-129">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="a-idzip-installing-the-zip-package"></a><span data-ttu-id="c98ad-130"><a id="zip" />Instalowanie pakietu ZIP</span><span class="sxs-lookup"><span data-stu-id="c98ad-130"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="c98ad-131">Binarny archiwa ZIP programu PowerShell są podane w celu włączenia zaawansowanych scenariuszach wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="c98ad-131">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="c98ad-132">Należy zauważyć, że korzystając z archiwum ZIP, nie będą otrzymywać sprawdzania wymagań wstępnych, tak jak pakietu MSI.</span><span class="sxs-lookup"><span data-stu-id="c98ad-132">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="c98ad-133">Dla niego komunikacji zdalnej za pośrednictwem usługi WS-Management, aby zapewnić prawidłowe działanie, upewnij się, że zostały spełnione [wymagania wstępne](#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="c98ad-133">For remoting over WSMan to work properly, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="c98ad-134">Wdrażanie na Windows IoT</span><span class="sxs-lookup"><span data-stu-id="c98ad-134">Deploying on Windows IoT</span></span>

<span data-ttu-id="c98ad-135">Zawiera już Windows IoT za pomocą programu Windows PowerShell, które firma Microsoft będzie używany do wdrażania programu PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="c98ad-135">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="c98ad-136">Utwórz `PSSession` urządzenie docelowe</span><span class="sxs-lookup"><span data-stu-id="c98ad-136">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="c98ad-137">Skopiuj pakiet ZIP do urządzenia</span><span class="sxs-lookup"><span data-stu-id="c98ad-137">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="c98ad-138">Łączenie z urządzeniem, a następnie rozwiń archiwum</span><span class="sxs-lookup"><span data-stu-id="c98ad-138">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="c98ad-139">Konfigurowanie komunikacji zdalnej programu PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="c98ad-139">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="c98ad-140">Łączenie do endpoint programu PowerShell Core 6 na urządzeniu</span><span class="sxs-lookup"><span data-stu-id="c98ad-140">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="c98ad-141">Wdrażanie na serwerze Nano Server</span><span class="sxs-lookup"><span data-stu-id="c98ad-141">Deploying on Nano Server</span></span>

<span data-ttu-id="c98ad-142">W poniższych instrukcjach przyjęto, że wersja programu PowerShell jest już uruchomiona na obrazie Nano Server i czy ma zostać wygenerowane przez [Kreator obrazów serwera Nano](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="c98ad-142">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="c98ad-143">Serwer nano Server jest "bezobsługowe" systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="c98ad-143">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="c98ad-144">Podstawowe pliki binarne można wdrożyć przy użyciu dwóch różnych metod.</span><span class="sxs-lookup"><span data-stu-id="c98ad-144">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="c98ad-145">W trybie offline — zainstalować dysk VHD serwera Nano i rozpakuj zawartość pliku zip do wybranej lokalizacji w zainstalowanym obrazie.</span><span class="sxs-lookup"><span data-stu-id="c98ad-145">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="c98ad-146">Tryb online — przenoszenie pliku zip przez sesję programu PowerShell i Rozpakuj go w wybranej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="c98ad-146">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="c98ad-147">W obu przypadkach należy wersji systemu Windows 10 x64 ZIP pakietu i będzie konieczne uruchomienie poleceń w ramach wystąpienia programu PowerShell "Administrator".</span><span class="sxs-lookup"><span data-stu-id="c98ad-147">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="c98ad-148">Wdrożenie programu PowerShell Core w trybie offline</span><span class="sxs-lookup"><span data-stu-id="c98ad-148">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="c98ad-149">Aby rozpakować pakiet do katalogu w zainstalowanym obrazie systemu Nano Server przy użyciu usługi narzędzia zip ulubionych.</span><span class="sxs-lookup"><span data-stu-id="c98ad-149">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="c98ad-150">Odinstaluj obraz i jego rozruch.</span><span class="sxs-lookup"><span data-stu-id="c98ad-150">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="c98ad-151">Połącz z wystąpieniem skrzynki odbiorczej programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c98ad-151">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="c98ad-152">Postępuj zgodnie z instrukcjami, aby utworzyć punkt końcowy komunikacji zdalnej za pomocą ["inna technika wystąpienia"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="c98ad-152">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="c98ad-153">Online wdrożenia programu PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="c98ad-153">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="c98ad-154">Poniższe kroki prowadzą przez wdrożenia programu PowerShell Core do uruchomionego wystąpienia systemu Nano Server i konfiguracji jego zdalnego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c98ad-154">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="c98ad-155">Połącz się z wystąpieniem skrzynki odbiorczej programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c98ad-155">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="c98ad-156">Skopiuj plik do wystąpienia systemu Nano Server</span><span class="sxs-lookup"><span data-stu-id="c98ad-156">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="c98ad-157">Wprowadź sesję</span><span class="sxs-lookup"><span data-stu-id="c98ad-157">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="c98ad-158">Wyodrębnij plik ZIP</span><span class="sxs-lookup"><span data-stu-id="c98ad-158">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="c98ad-159">Chcąc oparta na usłudze WSMan komunikacji zdalnej, postępuj zgodnie z instrukcjami, aby utworzyć punkt końcowy komunikacji zdalnej przy użyciu ["inna technika wystąpienia"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="c98ad-159">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="c98ad-160">Jak utworzyć punkt końcowy komunikacji zdalnej</span><span class="sxs-lookup"><span data-stu-id="c98ad-160">How to create a remoting endpoint</span></span>

<span data-ttu-id="c98ad-161">Program PowerShell Core obsługuje protokół komunikacji zdalnej programu PowerShell (PSRP) za pośrednictwem protokołu SSH i WSMan.</span><span class="sxs-lookup"><span data-stu-id="c98ad-161">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="c98ad-162">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="c98ad-162">For more information, see:</span></span>

- <span data-ttu-id="c98ad-163">[SSH komunikacji zdalnej w programie PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="c98ad-163">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="c98ad-164">[Komunikacja zdalna usługi WS-Management, w programie PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="c98ad-164">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
