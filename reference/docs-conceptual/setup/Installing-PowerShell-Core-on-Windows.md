---
title: Instalowanie programu PowerShell Core w systemie Windows
description: Informacje o instalowaniu programu PowerShell Core w Windows
ms.date: 08/06/2018
ms.openlocfilehash: ba159a69df7e117e90e21dd26228b61146260475
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320895"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="9c621-103">Instalowanie programu PowerShell Core w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="9c621-103">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="9c621-104">TOŻSAMOŚCI USŁUGI ZARZĄDZANEJ</span><span class="sxs-lookup"><span data-stu-id="9c621-104">MSI</span></span>

<span data-ttu-id="9c621-105">Aby zainstalować program PowerShell w klienta Windows lub Windows Server (działa w systemie Windows 7 z dodatkiem SP1, Server 2008 R2 i nowszych), Pobierz pakiet MSI w usłudze GitHub [zwalnia][] strony.</span><span class="sxs-lookup"><span data-stu-id="9c621-105">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>

<span data-ttu-id="9c621-106">Plik MSI wyglądają następująco — `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well --></span><span class="sxs-lookup"><span data-stu-id="9c621-106">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well --></span></span>

<span data-ttu-id="9c621-107">Po pobraniu, kliknij dwukrotnie Instalatora, a następnie postępuj zgodnie z monitami.</span><span class="sxs-lookup"><span data-stu-id="9c621-107">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="9c621-108">Brak skrótu umieszczone w trakcie instalacji, w Menu Start.</span><span class="sxs-lookup"><span data-stu-id="9c621-108">There is a shortcut placed in the Start Menu upon installation.</span></span>

- <span data-ttu-id="9c621-109">Domyślnie pakiet jest zainstalowany na `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="9c621-109">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="9c621-110">Można uruchomić programu PowerShell przy użyciu Start Menu lub `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="9c621-110">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="9c621-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="9c621-111">Prerequisites</span></span>

<span data-ttu-id="9c621-112">Aby włączyć komunikację zdalną programu PowerShell za pośrednictwem usługi WS-Management, muszą zostać spełnione następujące wymagania wstępne:</span><span class="sxs-lookup"><span data-stu-id="9c621-112">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="9c621-113">Zainstaluj [uniwersalnego środowiska uruchomieniowego c.](https://www.microsoft.com/download/details.aspx?id=50410) na Windows wersjach wcześniejszych niż Windows 10.</span><span class="sxs-lookup"><span data-stu-id="9c621-113">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="9c621-114">Jest ona dostępna za pośrednictwem bezpośredniego pobierania lub Windows Update.</span><span class="sxs-lookup"><span data-stu-id="9c621-114">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="9c621-115">W pełni zastosować poprawki względem jakiegokolwiek (w tym opcjonalnych pakietów), obsługiwane systemy mają już to zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="9c621-115">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="9c621-116">Windows Management Framework (WMF) 4.0 lub nowszym należy zainstalować na Windows 7 i Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="9c621-116">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="9c621-117">ZIP</span><span class="sxs-lookup"><span data-stu-id="9c621-117">ZIP</span></span>

<span data-ttu-id="9c621-118">Binarny archiwa ZIP programu PowerShell są podane w celu włączenia zaawansowanych scenariuszach wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="9c621-118">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="9c621-119">Należy zauważyć, że korzystając z archiwum ZIP, nie będą otrzymywać sprawdzania wymagań wstępnych, tak jak pakietu MSI.</span><span class="sxs-lookup"><span data-stu-id="9c621-119">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="9c621-120">Aby dla niego komunikacji zdalnej za pośrednictwem usługi WS-Management działało poprawnie, w wersjach Windows przed systemem Windows 10, należy się upewnić, [wymagania wstępne](#prerequisites) są spełnione.</span><span class="sxs-lookup"><span data-stu-id="9c621-120">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="9c621-121">Wdrażanie na Windows IoT</span><span class="sxs-lookup"><span data-stu-id="9c621-121">Deploying on Windows IoT</span></span>

<span data-ttu-id="9c621-122">Zawiera już Windows IoT za pomocą programu Windows PowerShell, które firma Microsoft będzie używany do wdrażania programu PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="9c621-122">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="9c621-123">Utwórz `PSSession` urządzenie docelowe</span><span class="sxs-lookup"><span data-stu-id="9c621-123">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="9c621-124">Skopiuj pakiet ZIP do urządzenia</span><span class="sxs-lookup"><span data-stu-id="9c621-124">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.1.0-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="9c621-125">Łączenie z urządzeniem, a następnie rozwiń archiwum</span><span class="sxs-lookup"><span data-stu-id="9c621-125">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.1.0-win-arm32.zip
   ```

4. <span data-ttu-id="9c621-126">Konfigurowanie komunikacji zdalnej programu PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="9c621-126">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-6.1.0-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="9c621-127">Łączenie do endpoint programu PowerShell Core 6 na urządzeniu</span><span class="sxs-lookup"><span data-stu-id="9c621-127">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.1.0
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="9c621-128">Wdrażanie na serwerze Nano Server</span><span class="sxs-lookup"><span data-stu-id="9c621-128">Deploying on Nano Server</span></span>

<span data-ttu-id="9c621-129">W poniższych instrukcjach przyjęto, że wersja programu PowerShell jest już uruchomiona na obrazie Nano Server i czy ma zostać wygenerowane przez [Kreator obrazów serwera Nano](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="9c621-129">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="9c621-130">Serwer nano Server jest "bezobsługowe" systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="9c621-130">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="9c621-131">Podstawowe pliki binarne można wdrożyć przy użyciu dwóch różnych metod.</span><span class="sxs-lookup"><span data-stu-id="9c621-131">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="9c621-132">W trybie offline — zainstalować dysk VHD serwera Nano i rozpakuj zawartość pliku zip do wybranej lokalizacji w zainstalowanym obrazie.</span><span class="sxs-lookup"><span data-stu-id="9c621-132">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="9c621-133">Tryb online — przenoszenie pliku zip przez sesję programu PowerShell i Rozpakuj go w wybranej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="9c621-133">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="9c621-134">W obu przypadkach należy wersji systemu Windows 10 x64 ZIP pakietu i będzie konieczne uruchomienie poleceń w ramach wystąpienia programu PowerShell "Administrator".</span><span class="sxs-lookup"><span data-stu-id="9c621-134">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="9c621-135">Wdrożenie programu PowerShell Core w trybie offline</span><span class="sxs-lookup"><span data-stu-id="9c621-135">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="9c621-136">Aby rozpakować pakiet do katalogu w zainstalowanym obrazie systemu Nano Server przy użyciu usługi narzędzia zip ulubionych.</span><span class="sxs-lookup"><span data-stu-id="9c621-136">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="9c621-137">Odinstaluj obraz i jego rozruch.</span><span class="sxs-lookup"><span data-stu-id="9c621-137">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="9c621-138">Połącz z wystąpieniem skrzynki odbiorczej programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9c621-138">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="9c621-139">Postępuj zgodnie z instrukcjami, aby utworzyć punkt końcowy komunikacji zdalnej za pomocą ["inna technika wystąpienia"](../core-powershell/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="9c621-139">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../core-powershell/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="9c621-140">Online wdrożenia programu PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="9c621-140">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="9c621-141">Poniższe kroki prowadzą przez wdrożenia programu PowerShell Core do uruchomionego wystąpienia systemu Nano Server i konfiguracji jego zdalnego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="9c621-141">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="9c621-142">Połącz się z wystąpieniem skrzynki odbiorczej programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9c621-142">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="9c621-143">Skopiuj plik do wystąpienia systemu Nano Server</span><span class="sxs-lookup"><span data-stu-id="9c621-143">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="9c621-144">Wprowadź sesję</span><span class="sxs-lookup"><span data-stu-id="9c621-144">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="9c621-145">Wyodrębnij plik ZIP</span><span class="sxs-lookup"><span data-stu-id="9c621-145">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="9c621-146">Chcąc oparta na usłudze WSMan komunikacji zdalnej, postępuj zgodnie z instrukcjami, aby utworzyć punkt końcowy komunikacji zdalnej przy użyciu ["inna technika wystąpienia"](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="9c621-146">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="9c621-147">Instrukcje, aby utworzyć punkt końcowy komunikacji zdalnej</span><span class="sxs-lookup"><span data-stu-id="9c621-147">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="9c621-148">Program PowerShell Core obsługuje protokół komunikacji zdalnej programu PowerShell (PSRP) za pośrednictwem protokołu SSH i WSMan.</span><span class="sxs-lookup"><span data-stu-id="9c621-148">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span>
<span data-ttu-id="9c621-149">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="9c621-149">For more information, see:</span></span>

- <span data-ttu-id="9c621-150">[SSH komunikacji zdalnej w programie PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="9c621-150">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="9c621-151">[Komunikacja zdalna usługi WS-Management, w programie PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="9c621-151">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="9c621-152">Instrukcje dotyczące instalacji artefaktu</span><span class="sxs-lookup"><span data-stu-id="9c621-152">Artifact Installation Instructions</span></span>

<span data-ttu-id="9c621-153">Publikujemy archiwum z bitami CoreCLR przy każdej kompilacji ciągłej integracji przy użyciu [AppVeyor][].</span><span class="sxs-lookup"><span data-stu-id="9c621-153">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

<span data-ttu-id="9c621-154">Aby zainstalować program PowerShell Core z artefaktów CoreCLR:</span><span class="sxs-lookup"><span data-stu-id="9c621-154">To install PowerShell Core from the CoreCLR Artifact:</span></span>

1. <span data-ttu-id="9c621-155">Pobierz pakiet pliku ZIP z **artefaktów** kartę konkretnej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9c621-155">Download ZIP package from **artifacts** tab of the particular build.</span></span>
2. <span data-ttu-id="9c621-156">Odblokuj plik ZIP: kliknij prawym przyciskiem myszy w Eksploratorze plików -> Właściwości -> wyboru Zastosuj "Odblokuj" box -></span><span class="sxs-lookup"><span data-stu-id="9c621-156">Unblock ZIP file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
3. <span data-ttu-id="9c621-157">Wyodrębnij plik zip do `bin` katalogu</span><span class="sxs-lookup"><span data-stu-id="9c621-157">Extract zip file to `bin` directory</span></span>
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[zwalnia]: https://github.com/PowerShell/PowerShell/releases
[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
