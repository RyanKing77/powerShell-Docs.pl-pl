---
title: Instalowanie programu PowerShell Core w systemie Windows
description: Informacje o instalowaniu programu PowerShell Core w Windows
ms.date: 08/06/2018
ms.openlocfilehash: 450a38a1ef2e2890059094774fcc3f2ad4fcda6e
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2019
ms.locfileid: "58748954"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="0a3ff-103">Instalowanie programu PowerShell Core w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="0a3ff-103">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="0a3ff-104">MSI</span><span class="sxs-lookup"><span data-stu-id="0a3ff-104">MSI</span></span>

<span data-ttu-id="0a3ff-105">Aby zainstalować program PowerShell w klienta Windows lub Windows Server (działa w systemie Windows 7 z dodatkiem SP1, Server 2008 R2 i nowszych), Pobierz pakiet MSI w usłudze GitHub [Wersje][] strony.</span><span class="sxs-lookup"><span data-stu-id="0a3ff-105">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>  <span data-ttu-id="0a3ff-106">Przewiń w dół do **zasoby** części wersji, którą chcesz zainstalować.</span><span class="sxs-lookup"><span data-stu-id="0a3ff-106">Scroll down to the **Assets** section of the Release you want to install.</span></span>  <span data-ttu-id="0a3ff-107">Sekcja zasoby mogą być zwinięte, konieczne może być kliknij, aby ją rozwinąć.</span><span class="sxs-lookup"><span data-stu-id="0a3ff-107">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="0a3ff-108">Plik MSI wyglądają następująco — `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="0a3ff-108">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="0a3ff-109">Po pobraniu, kliknij dwukrotnie Instalatora, a następnie postępuj zgodnie z monitami.</span><span class="sxs-lookup"><span data-stu-id="0a3ff-109">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="0a3ff-110">Brak skrótu umieszczone w trakcie instalacji, w Menu Start.</span><span class="sxs-lookup"><span data-stu-id="0a3ff-110">There is a shortcut placed in the Start Menu upon installation.</span></span>

- <span data-ttu-id="0a3ff-111">Domyślnie pakiet jest zainstalowany na `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="0a3ff-111">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="0a3ff-112">Można uruchomić programu PowerShell przy użyciu Start Menu lub `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="0a3ff-112">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="0a3ff-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="0a3ff-113">Prerequisites</span></span>

<span data-ttu-id="0a3ff-114">Aby włączyć komunikację zdalną programu PowerShell za pośrednictwem usługi WS-Management, muszą zostać spełnione następujące wymagania wstępne:</span><span class="sxs-lookup"><span data-stu-id="0a3ff-114">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="0a3ff-115">Zainstaluj [uniwersalnego środowiska uruchomieniowego c.](https://www.microsoft.com/download/details.aspx?id=50410) na Windows wersjach wcześniejszych niż Windows 10.</span><span class="sxs-lookup"><span data-stu-id="0a3ff-115">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="0a3ff-116">Jest ona dostępna za pośrednictwem bezpośredniego pobierania lub Windows Update.</span><span class="sxs-lookup"><span data-stu-id="0a3ff-116">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="0a3ff-117">W pełni zastosować poprawki względem jakiegokolwiek (w tym opcjonalnych pakietów), obsługiwane systemy mają już to zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="0a3ff-117">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="0a3ff-118">Windows Management Framework (WMF) 4.0 lub nowszym należy zainstalować na Windows 7 i Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="0a3ff-118">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="0a3ff-119">ZIP</span><span class="sxs-lookup"><span data-stu-id="0a3ff-119">ZIP</span></span>

<span data-ttu-id="0a3ff-120">Binarny archiwa ZIP programu PowerShell są podane w celu włączenia zaawansowanych scenariuszach wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="0a3ff-120">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="0a3ff-121">Należy zauważyć, że korzystając z archiwum ZIP, nie będą otrzymywać sprawdzania wymagań wstępnych, tak jak pakietu MSI.</span><span class="sxs-lookup"><span data-stu-id="0a3ff-121">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="0a3ff-122">Aby dla niego komunikacji zdalnej za pośrednictwem usługi WS-Management działało poprawnie, w wersjach Windows przed systemem Windows 10, należy się upewnić, [wymagania wstępne](#prerequisites) są spełnione.</span><span class="sxs-lookup"><span data-stu-id="0a3ff-122">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="0a3ff-123">Wdrażanie na Windows IoT</span><span class="sxs-lookup"><span data-stu-id="0a3ff-123">Deploying on Windows IoT</span></span>

<span data-ttu-id="0a3ff-124">Zawiera już Windows IoT za pomocą programu Windows PowerShell, które firma Microsoft będzie używany do wdrażania programu PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="0a3ff-124">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="0a3ff-125">Utwórz `PSSession` urządzenie docelowe</span><span class="sxs-lookup"><span data-stu-id="0a3ff-125">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="0a3ff-126">Skopiuj pakiet ZIP do urządzenia</span><span class="sxs-lookup"><span data-stu-id="0a3ff-126">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="0a3ff-127">Łączenie z urządzeniem, a następnie rozwiń archiwum</span><span class="sxs-lookup"><span data-stu-id="0a3ff-127">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="0a3ff-128">Konfigurowanie komunikacji zdalnej programu PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="0a3ff-128">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="0a3ff-129">Łączenie do endpoint programu PowerShell Core 6 na urządzeniu</span><span class="sxs-lookup"><span data-stu-id="0a3ff-129">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="0a3ff-130">Wdrażanie na serwerze Nano Server</span><span class="sxs-lookup"><span data-stu-id="0a3ff-130">Deploying on Nano Server</span></span>

<span data-ttu-id="0a3ff-131">W poniższych instrukcjach przyjęto, że wersja programu PowerShell jest już uruchomiona na obrazie Nano Server i czy ma zostać wygenerowane przez [Kreator obrazów serwera Nano](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="0a3ff-131">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="0a3ff-132">Serwer nano Server jest "bezobsługowe" systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="0a3ff-132">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="0a3ff-133">Podstawowe pliki binarne można wdrożyć przy użyciu dwóch różnych metod.</span><span class="sxs-lookup"><span data-stu-id="0a3ff-133">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="0a3ff-134">W trybie offline — zainstalować dysk VHD serwera Nano i rozpakuj zawartość pliku zip do wybranej lokalizacji w zainstalowanym obrazie.</span><span class="sxs-lookup"><span data-stu-id="0a3ff-134">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="0a3ff-135">Tryb online — przenoszenie pliku zip przez sesję programu PowerShell i Rozpakuj go w wybranej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="0a3ff-135">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="0a3ff-136">W obu przypadkach należy wersji systemu Windows 10 x64 ZIP pakietu i będzie konieczne uruchomienie poleceń w ramach wystąpienia programu PowerShell "Administrator".</span><span class="sxs-lookup"><span data-stu-id="0a3ff-136">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="0a3ff-137">Wdrożenie programu PowerShell Core w trybie offline</span><span class="sxs-lookup"><span data-stu-id="0a3ff-137">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="0a3ff-138">Aby rozpakować pakiet do katalogu w zainstalowanym obrazie systemu Nano Server przy użyciu usługi narzędzia zip ulubionych.</span><span class="sxs-lookup"><span data-stu-id="0a3ff-138">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="0a3ff-139">Odinstaluj obraz i jego rozruch.</span><span class="sxs-lookup"><span data-stu-id="0a3ff-139">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="0a3ff-140">Połącz z wystąpieniem skrzynki odbiorczej programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0a3ff-140">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="0a3ff-141">Postępuj zgodnie z instrukcjami, aby utworzyć punkt końcowy komunikacji zdalnej za pomocą ["inna technika wystąpienia"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="0a3ff-141">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="0a3ff-142">Online wdrożenia programu PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="0a3ff-142">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="0a3ff-143">Poniższe kroki prowadzą przez wdrożenia programu PowerShell Core do uruchomionego wystąpienia systemu Nano Server i konfiguracji jego zdalnego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="0a3ff-143">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="0a3ff-144">Połącz się z wystąpieniem skrzynki odbiorczej programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a3ff-144">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="0a3ff-145">Skopiuj plik do wystąpienia systemu Nano Server</span><span class="sxs-lookup"><span data-stu-id="0a3ff-145">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="0a3ff-146">Wprowadź sesję</span><span class="sxs-lookup"><span data-stu-id="0a3ff-146">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="0a3ff-147">Wyodrębnij plik ZIP</span><span class="sxs-lookup"><span data-stu-id="0a3ff-147">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="0a3ff-148">Chcąc oparta na usłudze WSMan komunikacji zdalnej, postępuj zgodnie z instrukcjami, aby utworzyć punkt końcowy komunikacji zdalnej przy użyciu ["inna technika wystąpienia"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="0a3ff-148">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="0a3ff-149">Instrukcje, aby utworzyć punkt końcowy komunikacji zdalnej</span><span class="sxs-lookup"><span data-stu-id="0a3ff-149">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="0a3ff-150">Program PowerShell Core obsługuje protokół komunikacji zdalnej programu PowerShell (PSRP) za pośrednictwem protokołu SSH i WSMan.</span><span class="sxs-lookup"><span data-stu-id="0a3ff-150">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span>
<span data-ttu-id="0a3ff-151">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="0a3ff-151">For more information, see:</span></span>

- <span data-ttu-id="0a3ff-152">[SSH komunikacji zdalnej w programie PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="0a3ff-152">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="0a3ff-153">[Komunikacja zdalna usługi WS-Management, w programie PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="0a3ff-153">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="0a3ff-154">Instrukcje dotyczące instalacji artefaktu</span><span class="sxs-lookup"><span data-stu-id="0a3ff-154">Artifact Installation Instructions</span></span>

<span data-ttu-id="0a3ff-155">Publikujemy archiwum z bitami CoreCLR przy każdej kompilacji ciągłej integracji przy użyciu [AppVeyor][].</span><span class="sxs-lookup"><span data-stu-id="0a3ff-155">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

<span data-ttu-id="0a3ff-156">Aby zainstalować program PowerShell Core z artefaktów CoreCLR:</span><span class="sxs-lookup"><span data-stu-id="0a3ff-156">To install PowerShell Core from the CoreCLR Artifact:</span></span>

1. <span data-ttu-id="0a3ff-157">Pobierz pakiet pliku ZIP z **artefaktów** kartę konkretnej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0a3ff-157">Download ZIP package from **artifacts** tab of the particular build.</span></span>
2. <span data-ttu-id="0a3ff-158">Odblokuj plik ZIP: kliknij prawym przyciskiem myszy w Eksploratorze plików -> Właściwości -> wyboru Zastosuj "Odblokuj" box -></span><span class="sxs-lookup"><span data-stu-id="0a3ff-158">Unblock ZIP file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
3. <span data-ttu-id="0a3ff-159">Wyodrębnij plik zip do `bin` katalogu</span><span class="sxs-lookup"><span data-stu-id="0a3ff-159">Extract zip file to `bin` directory</span></span>
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[Wersje]: https://github.com/PowerShell/PowerShell/releases
[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
