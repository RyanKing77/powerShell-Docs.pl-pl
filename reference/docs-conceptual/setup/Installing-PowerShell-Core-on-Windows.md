# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="3be90-101">Instalowanie programu PowerShell Core w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="3be90-101">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="3be90-102">MSI</span><span class="sxs-lookup"><span data-stu-id="3be90-102">MSI</span></span>

<span data-ttu-id="3be90-103">Do zainstalowania programu PowerShell na klientach z systemem Windows lub Windows Server (działa w systemie Windows 7 z dodatkiem SP1, Server 2008 R2 lub nowszy), Pobierz pakiet MSI z naszej usługi GitHub [zwalnia][] strony.</span><span class="sxs-lookup"><span data-stu-id="3be90-103">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>

<span data-ttu-id="3be90-104">Plik MSI wygląda tak-`PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="3be90-104">The MSI file looks like this - `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="3be90-105">Po pobraniu, kliknij dwukrotnie Instalatora, a następnie postępuj zgodnie z monitami.</span><span class="sxs-lookup"><span data-stu-id="3be90-105">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="3be90-106">Brak skrót umieszczone w Menu Start, podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="3be90-106">There is a shortcut placed in the Start Menu upon installation.</span></span>

* <span data-ttu-id="3be90-107">Domyślnie pakiet jest zainstalowany na`$env:ProgramFiles\PowerShell\`</span><span class="sxs-lookup"><span data-stu-id="3be90-107">By default the package is installed to `$env:ProgramFiles\PowerShell\`</span></span>
* <span data-ttu-id="3be90-108">Można uruchomić programu PowerShell za pomocą Start Menu lub`$env:ProgramFiles\PowerShell\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="3be90-108">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="3be90-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="3be90-109">Prerequisites</span></span>

<span data-ttu-id="3be90-110">Aby włączyć obsługę zdalną środowiska PowerShell przez WSMan, muszą zostać spełnione następujące wymagania wstępne:</span><span class="sxs-lookup"><span data-stu-id="3be90-110">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

* <span data-ttu-id="3be90-111">Zainstaluj [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) w wersjach systemu Windows przed systemem Windows 10.</span><span class="sxs-lookup"><span data-stu-id="3be90-111">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="3be90-112">Jest ona dostępna za pośrednictwem bezpośredniego pobierania lub usługi Windows Update.</span><span class="sxs-lookup"><span data-stu-id="3be90-112">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="3be90-113">Poprawiono pełni (w tym opcjonalnych pakietów), obsługiwane systemy mają już to zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="3be90-113">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
* <span data-ttu-id="3be90-114">Zainstaluj zestaw Windows Management Framework (WMF) [4.0](https://www.microsoft.com/download/details.aspx?id=40855) lub nowszą ([5.1](https://www.microsoft.com/download/details.aspx?id=54616)) w systemie Windows 7 i Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="3be90-114">Install the Windows Management Framework (WMF) [4.0](https://www.microsoft.com/download/details.aspx?id=40855) or newer ([5.1](https://www.microsoft.com/download/details.aspx?id=54616)) on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="3be90-115">ZIP</span><span class="sxs-lookup"><span data-stu-id="3be90-115">ZIP</span></span>

<span data-ttu-id="3be90-116">Binarny archiwum ZIP programu PowerShell umożliwiające zaawansowanych scenariuszach wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="3be90-116">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="3be90-117">Należy zauważyć, że podczas korzystania z archiwum ZIP, nie będzie otrzymywał sprawdzania wymagań wstępnych, tak jak pakiet MSI.</span><span class="sxs-lookup"><span data-stu-id="3be90-117">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="3be90-118">Dlatego w celu komunikacji zdalnej za pośrednictwem usługi WSMan działają prawidłowo w wersjach systemu Windows przed systemem Windows 10, trzeba upewnij się, że [wymagania wstępne](#prerequisites) są spełnione.</span><span class="sxs-lookup"><span data-stu-id="3be90-118">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-nano-server"></a><span data-ttu-id="3be90-119">Wdrażanie na serwerze Nano</span><span class="sxs-lookup"><span data-stu-id="3be90-119">Deploying on Nano Server</span></span>

<span data-ttu-id="3be90-120">W poniższych instrukcjach przyjęto, że wersja programu PowerShell jest już uruchomiona w obrazie Nano Server i że ma zostać wygenerowane przez [Nano Server Image Builder](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="3be90-120">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="3be90-121">Nano Server jest "bezobsługowe" systemu operacyjnego i wdrożenia plików binarnych programu PowerShell Core może się zdarzyć na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="3be90-121">Nano Server is a "headless" OS and deployment of PowerShell Core binaries can happen in two different ways:</span></span>

1. <span data-ttu-id="3be90-122">W trybie offline — zainstalować dysk VHD Nano Server i rozpakuj zawartość pliku zip do wybranej lokalizacji w zainstalowanym obrazie.</span><span class="sxs-lookup"><span data-stu-id="3be90-122">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
1. <span data-ttu-id="3be90-123">Tryb online — transferu pliku zip w sesji programu PowerShell i Rozpakuj go w wybranej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="3be90-123">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="3be90-124">W obu przypadkach należy wersji systemu Windows 10 x64 Zip pakietu i będzie musiał uruchomić polecenia w ramach wystąpienia programu PowerShell "Administrator".</span><span class="sxs-lookup"><span data-stu-id="3be90-124">In both cases, you will need the Windows 10 x64 Zip release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="3be90-125">W trybie offline wdrażania podstawowych programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="3be90-125">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="3be90-126">Rozpakuj pakiet do katalogu w zainstalowanym obrazie Nano Server za pomocą narzędzia Twoje ulubione zip.</span><span class="sxs-lookup"><span data-stu-id="3be90-126">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
1. <span data-ttu-id="3be90-127">Odinstaluj obraz i uruchom go.</span><span class="sxs-lookup"><span data-stu-id="3be90-127">Unmount the image and boot it.</span></span>
1. <span data-ttu-id="3be90-128">Połącz się z wystąpieniem skrzynki odbiorczej, programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3be90-128">Connect to the inbox instance of Windows PowerShell.</span></span>
1. <span data-ttu-id="3be90-129">Postępuj zgodnie z instrukcjami, aby utworzyć punktu końcowego usług zdalnych za pomocą [innej techniki wystąpienia](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="3be90-129">Follow the instructions to create a remoting endpoint using the [another instance technique](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="3be90-130">Wdrożenie online PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="3be90-130">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="3be90-131">Następujące kroki przeprowadzi Cię przez wdrożenia programu PowerShell Core uruchomione wystąpienie Nano Server i konfiguracji punktu końcowego zdalnego.</span><span class="sxs-lookup"><span data-stu-id="3be90-131">The following steps will guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

* <span data-ttu-id="3be90-132">Połącz z wystąpieniem skrzynki odbiorczej programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3be90-132">Connect to the inbox instance of Windows PowerShell</span></span>

```powershell
$session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
```

* <span data-ttu-id="3be90-133">Skopiuj plik do wystąpienia Nano Server</span><span class="sxs-lookup"><span data-stu-id="3be90-133">Copy the file to the Nano Server instance</span></span>

```powershell
Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
```

* <span data-ttu-id="3be90-134">Wprowadź sesji</span><span class="sxs-lookup"><span data-stu-id="3be90-134">Enter the session</span></span>

```powershell
Enter-PSSession $session
```

* <span data-ttu-id="3be90-135">Wyodrębnij plik Zip</span><span class="sxs-lookup"><span data-stu-id="3be90-135">Extract the Zip file</span></span>

```powershell
# Insert the appropriate version.
Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
```

* <span data-ttu-id="3be90-136">Oparta na usłudze WSMan komunikacji zdalnej, wykonaj instrukcje tworzenia punktu końcowego usług zdalnych za pomocą [innej techniki wystąpienia](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="3be90-136">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the [another instance technique](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="3be90-137">Instrukcje dotyczące tworzenia punktu końcowego usługi zdalne</span><span class="sxs-lookup"><span data-stu-id="3be90-137">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="3be90-138">PowerShell Core obsługuje protokół komunikacji zdalnej programu PowerShell (PSRP) za pośrednictwem protokołów SSH, jak i WSMan.</span><span class="sxs-lookup"><span data-stu-id="3be90-138">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="3be90-139">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="3be90-139">For more information, see:</span></span>

* <span data-ttu-id="3be90-140">[SSH komunikację zdalną środowiska PowerShell główną][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="3be90-140">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
* <span data-ttu-id="3be90-141">[Usługi zdalne WSMan główną programu PowerShell][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="3be90-141">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="3be90-142">Instrukcje dotyczące instalacji artefaktów</span><span class="sxs-lookup"><span data-stu-id="3be90-142">Artifact Installation Instructions</span></span>

<span data-ttu-id="3be90-143">Firma Microsoft publikowania archiwum środowisko CoreCLR bitów w każdej kompilacji CI z [AppVeyor][].</span><span class="sxs-lookup"><span data-stu-id="3be90-143">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

## <a name="coreclr-artifacts"></a><span data-ttu-id="3be90-144">Środowisko CoreCLR artefaktów</span><span class="sxs-lookup"><span data-stu-id="3be90-144">CoreCLR Artifacts</span></span>

* <span data-ttu-id="3be90-145">Pobierz pakiet zip z **artefakty** kartę określonej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3be90-145">Download zip package from **artifacts** tab of the particular build.</span></span>
* <span data-ttu-id="3be90-146">Plik zip Odblokuj: kliknij prawym przyciskiem myszy w Eksploratorze plików -> Właściwości -> Zastosuj "Odblokuj" -> pole wyboru</span><span class="sxs-lookup"><span data-stu-id="3be90-146">Unblock zip file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
* <span data-ttu-id="3be90-147">Wyodrębnij plik zip do `bin` katalogu</span><span class="sxs-lookup"><span data-stu-id="3be90-147">Extract zip file to `bin` directory</span></span>
* `./bin/pwsh.exe`

<!-- [download-center]: TODO -->
[zwalnia]: https://github.com/PowerShell/PowerShell/releases
[signing]: ../../tools/Sign-Package.ps1
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
