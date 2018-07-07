---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Rozpoczynanie pracy z Desired State Configuration (DSC) dla systemu Linux
ms.openlocfilehash: d5a4a17fbcffbbbd6df3dd902dbd104769b7d17e
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893600"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="bf219-103">Rozpoczynanie pracy z Desired State Configuration (DSC) dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="bf219-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="bf219-104">W tym temacie wyjaśniono, jak rozpocząć pracę, przy użyciu programu PowerShell Desired State Configuration (DSC) dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="bf219-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="bf219-105">Aby uzyskać ogólne informacje o DSC, zobacz [Rozpoczynanie pracy z usługą Windows PowerShell Desired State Configuration](overview.md).</span><span class="sxs-lookup"><span data-stu-id="bf219-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="bf219-106">Obsługiwane wersje systemu operacji systemu Linux</span><span class="sxs-lookup"><span data-stu-id="bf219-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="bf219-107">Następujące wersje systemu operacyjnego Linux są obsługiwane dla DSC dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="bf219-107">The following Linux operating system versions are supported for DSC for Linux.</span></span>

- <span data-ttu-id="bf219-108">CentOS 5, 6 i 7 — x86/x64 64</span><span class="sxs-lookup"><span data-stu-id="bf219-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="bf219-109">Debian GNU/Linux 6, 7 i 8 — x86/x64 64</span><span class="sxs-lookup"><span data-stu-id="bf219-109">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="bf219-110">Oracle Linux 5, 6 i 7 — x86/x64 64</span><span class="sxs-lookup"><span data-stu-id="bf219-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="bf219-111">Red Hat Enterprise Linux Server 5, 6 i 7 — x86/x64 64</span><span class="sxs-lookup"><span data-stu-id="bf219-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="bf219-112">SUSE Linux Enterprise Server 10, 11 i 12 — x86/x64 64</span><span class="sxs-lookup"><span data-stu-id="bf219-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="bf219-113">Serwer Ubuntu 12.04 LTS, 14.04 LTS i 16.04 LTS — x86/x64 64</span><span class="sxs-lookup"><span data-stu-id="bf219-113">Ubuntu Server 12.04 LTS, 14.04 LTS and 16.04 LTS (x86/x64)</span></span>

<span data-ttu-id="bf219-114">W poniższej tabeli opisano zależności pakietów wymaganych do DSC dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="bf219-114">The following table describes the required package dependencies for DSC for Linux.</span></span>

|  <span data-ttu-id="bf219-115">Wymagany pakiet</span><span class="sxs-lookup"><span data-stu-id="bf219-115">Required package</span></span> |  <span data-ttu-id="bf219-116">Opis</span><span class="sxs-lookup"><span data-stu-id="bf219-116">Description</span></span> |  <span data-ttu-id="bf219-117">Minimalna wersja</span><span class="sxs-lookup"><span data-stu-id="bf219-117">Minimum version</span></span> |
|---|---|---|
| <span data-ttu-id="bf219-118">glibc</span><span class="sxs-lookup"><span data-stu-id="bf219-118">glibc</span></span>| <span data-ttu-id="bf219-119">Biblioteka GNU</span><span class="sxs-lookup"><span data-stu-id="bf219-119">GNU Library</span></span>| <span data-ttu-id="bf219-120">2... 4 — 31.30</span><span class="sxs-lookup"><span data-stu-id="bf219-120">2…4 – 31.30</span></span>|
| <span data-ttu-id="bf219-121">Python</span><span class="sxs-lookup"><span data-stu-id="bf219-121">python</span></span>| <span data-ttu-id="bf219-122">Python</span><span class="sxs-lookup"><span data-stu-id="bf219-122">Python</span></span>| <span data-ttu-id="bf219-123">2.4 — 3.4</span><span class="sxs-lookup"><span data-stu-id="bf219-123">2.4 – 3.4</span></span>|
| <span data-ttu-id="bf219-124">omiserver</span><span class="sxs-lookup"><span data-stu-id="bf219-124">omiserver</span></span>| <span data-ttu-id="bf219-125">Infrastruktura zarządzania otwartego</span><span class="sxs-lookup"><span data-stu-id="bf219-125">Open Management Infrastructure</span></span>| <span data-ttu-id="bf219-126">1.0.8.1</span><span class="sxs-lookup"><span data-stu-id="bf219-126">1.0.8.1</span></span>|
| <span data-ttu-id="bf219-127">biblioteki openssl</span><span class="sxs-lookup"><span data-stu-id="bf219-127">openssl</span></span>| <span data-ttu-id="bf219-128">Biblioteki OpenSSL</span><span class="sxs-lookup"><span data-stu-id="bf219-128">OpenSSL Libraries</span></span>| <span data-ttu-id="bf219-129">0.9.8 lub 1.0</span><span class="sxs-lookup"><span data-stu-id="bf219-129">0.9.8 or 1.0</span></span>|
| <span data-ttu-id="bf219-130">ctypes</span><span class="sxs-lookup"><span data-stu-id="bf219-130">ctypes</span></span>| <span data-ttu-id="bf219-131">Biblioteka CTypes języka Python</span><span class="sxs-lookup"><span data-stu-id="bf219-131">Python CTypes library</span></span>| <span data-ttu-id="bf219-132">Musi odpowiadać wersji języka Python</span><span class="sxs-lookup"><span data-stu-id="bf219-132">Must match Python version</span></span>|
| <span data-ttu-id="bf219-133">libcurl</span><span class="sxs-lookup"><span data-stu-id="bf219-133">libcurl</span></span>| <span data-ttu-id="bf219-134">biblioteki klienta http programu cURL</span><span class="sxs-lookup"><span data-stu-id="bf219-134">cURL http client library</span></span>| <span data-ttu-id="bf219-135">7.15.1</span><span class="sxs-lookup"><span data-stu-id="bf219-135">7.15.1</span></span>|

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="bf219-136">Instalowanie DSC dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="bf219-136">Installing DSC for Linux</span></span>

<span data-ttu-id="bf219-137">Należy zainstalować [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) przed zainstalowaniem DSC dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="bf219-137">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="bf219-138">Instalowanie OMI</span><span class="sxs-lookup"><span data-stu-id="bf219-138">Installing OMI</span></span>

<span data-ttu-id="bf219-139">Desired State Configuration for Linux wymaga, aby serwer modelu CIM Open Management Infrastructure (OMI), wersja 1.0.8.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="bf219-139">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="bf219-140">OMI można pobrać z Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span><span class="sxs-lookup"><span data-stu-id="bf219-140">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="bf219-141">Aby zainstalować OMI, należy zainstalować pakiet, który jest odpowiedni dla systemu Linux (.rpm lub .deb) i wersją biblioteki OpenSSL (ssl_098 lub ssl_100) i architektura (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="bf219-141">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="bf219-142">Pakiety RPM są odpowiednie dla CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server i Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="bf219-142">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="bf219-143">DEB pakiety są odpowiednie dla Debian GNU/Linux i Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="bf219-143">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="bf219-144">Pakiety ssl_098 są odpowiednie dla komputerów z protokołem OpenSSL 0.9.8 instalowane, gdy pakiety ssl_100 są odpowiednie dla komputerów z biblioteki OpenSSL zainstalowany w wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="bf219-144">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="bf219-145">Aby określić zainstalowaną wersją biblioteki OpenSSL, uruchom polecenie `openssl version`.</span><span class="sxs-lookup"><span data-stu-id="bf219-145">To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="bf219-146">Uruchom następujące polecenie, aby zainstalować w systemie CentOS 7 x64 OMI.</span><span class="sxs-lookup"><span data-stu-id="bf219-146">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="bf219-147">Instalowanie DSC</span><span class="sxs-lookup"><span data-stu-id="bf219-147">Installing DSC</span></span>

<span data-ttu-id="bf219-148">DSC dla systemu Linux jest dostępna do pobrania [tutaj](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span><span class="sxs-lookup"><span data-stu-id="bf219-148">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span></span>

<span data-ttu-id="bf219-149">Aby zainstalować DSC, należy zainstalować pakiet, który jest odpowiedni dla systemu Linux (.rpm lub .deb) i wersją biblioteki OpenSSL (ssl_098 lub ssl_100) i architektura (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="bf219-149">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="bf219-150">Pakiety RPM są odpowiednie dla CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server i Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="bf219-150">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="bf219-151">DEB pakiety są odpowiednie dla Debian GNU/Linux i Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="bf219-151">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="bf219-152">Pakiety ssl_098 są odpowiednie dla komputerów z protokołem OpenSSL 0.9.8 instalowane, gdy pakiety ssl_100 są odpowiednie dla komputerów z biblioteki OpenSSL zainstalowany w wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="bf219-152">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="bf219-153">Aby określić zainstalowaną wersją biblioteki OpenSSL, uruchom polecenie wersją biblioteki openssl.</span><span class="sxs-lookup"><span data-stu-id="bf219-153">To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="bf219-154">Uruchom następujące polecenie, aby zainstalować w systemie CentOS 7 x64 DSC.</span><span class="sxs-lookup"><span data-stu-id="bf219-154">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a><span data-ttu-id="bf219-155">Za pomocą DSC dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="bf219-155">Using DSC for Linux</span></span>

<span data-ttu-id="bf219-156">W poniższych sekcjach opisano sposób tworzenia i uruchomionych konfiguracjach DSC na komputerach z systemem Linux.</span><span class="sxs-lookup"><span data-stu-id="bf219-156">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="bf219-157">Tworzenie dokumentów w pliku MOF konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bf219-157">Creating a configuration MOF document</span></span>

<span data-ttu-id="bf219-158">Konfiguracja programu Windows PowerShell — słowo kluczowe jest używany do utworzenia konfiguracji dla komputerów z systemem Linux, podobnie jak na komputerach Windows.</span><span class="sxs-lookup"><span data-stu-id="bf219-158">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="bf219-159">W poniższych krokach opisano tworzenie dokumentu konfiguracji dla komputera z systemem Linux przy użyciu programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bf219-159">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="bf219-160">Zaimportuj moduł nx.</span><span class="sxs-lookup"><span data-stu-id="bf219-160">Import the nx module.</span></span> <span data-ttu-id="bf219-161">Moduł programu Windows PowerShell nx zawiera schemat wbudowane zasoby DSC dla systemu Linux i musi być zainstalowane na komputerze lokalnym i zaimportowane w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bf219-161">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

   - <span data-ttu-id="bf219-162">Aby zainstalować moduł nx, skopiuj katalog modułu nx do jednej `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` lub `$PSHOME\Modules`.</span><span class="sxs-lookup"><span data-stu-id="bf219-162">To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="bf219-163">Moduł nx znajduje się w DSC pakietu instalacyjnego systemu Linux (MSI).</span><span class="sxs-lookup"><span data-stu-id="bf219-163">The nx module is included in the DSC for Linux installation package (MSI).</span></span> <span data-ttu-id="bf219-164">Aby zaimportować moduł nx w konfiguracji, należy użyć `Import-DSCResource` polecenia:</span><span class="sxs-lookup"><span data-stu-id="bf219-164">To import the nx module in your configuration, use the `Import-DSCResource` command:</span></span>

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. <span data-ttu-id="bf219-165">Definiowanie konfiguracji i generowania dokumentu konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="bf219-165">Define a configuration and generate the configuration document:</span></span>

   ```powershell
   Configuration ExampleConfiguration
   {
        Import-DscResource -Module nx

        Node  "linuxhost.contoso.com"
        {
            nxFile ExampleFile 
            {
                DestinationPath = "/tmp/example"
                Contents = "hello world `n"
                Ensure = "Present"
                Type = "File"
            }
        }
   }

   ExampleConfiguration -OutputPath:"C:\temp"
   ```

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="bf219-166">Wypychanie konfiguracji na komputerze z systemem Linux</span><span class="sxs-lookup"><span data-stu-id="bf219-166">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="bf219-167">Konfiguracja dokumentów (pliki MOF) może być przyczyną do komputera systemu Linux przy użyciu [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bf219-167">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.</span></span> <span data-ttu-id="bf219-168">Aby można było użyć tego polecenia cmdlet, wraz z [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), lub [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) poleceń cmdlet, zdalnie do komputera z systemem Linux, należy użyć CIMSession.</span><span class="sxs-lookup"><span data-stu-id="bf219-168">In order to use this cmdlet, along with the [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), or [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="bf219-169">[New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) polecenie cmdlet służy do tworzenia CIMSession na komputerze z systemem Linux.</span><span class="sxs-lookup"><span data-stu-id="bf219-169">The [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="bf219-170">Poniższy kod przedstawia sposób tworzenia CIMSession DSC dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="bf219-170">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90
```

> [!NOTE]
> <span data-ttu-id="bf219-171">W trybie "Push" poświadczenia użytkownika musi być zalogowany jako użytkownik root na komputerze z systemem Linux.</span><span class="sxs-lookup"><span data-stu-id="bf219-171">For “Push” mode, the user credential must be the root user on the Linux computer.</span></span>
> <span data-ttu-id="bf219-172">Tylko połączeń SSL/TLS są obsługiwane w przypadku DSC dla systemu Linux, `New-CimSession` musi być używana z parametrem – UseSSL ustawionym na $true.</span><span class="sxs-lookup"><span data-stu-id="bf219-172">Only SSL/TLS connections are supported for DSC for Linux, the `New-CimSession` must be used with the –UseSSL parameter set to $true.</span></span>
> <span data-ttu-id="bf219-173">Certyfikat SSL używany przez OMI (w przypadku DSC) jest określona w pliku: `/opt/omi/etc/omiserver.conf` z właściwościami: pemfile i keyfile.</span><span class="sxs-lookup"><span data-stu-id="bf219-173">The SSL certificate used by OMI (for DSC) is specified in the file: `/opt/omi/etc/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
> <span data-ttu-id="bf219-174">Jeśli ten certyfikat nie jest zaufany przez komputer Windows, które są uruchomione [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) polecenia cmdlet na możesz zignorować weryfikację certyfikatu przy użyciu opcji CIMSession: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span><span class="sxs-lookup"><span data-stu-id="bf219-174">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span></span>

<span data-ttu-id="bf219-175">Uruchom następujące polecenie, aby wypchnąć konfiguracji DSC do węzłów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="bf219-175">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="bf219-176">Dystrybucja konfiguracji z serwera ściągania</span><span class="sxs-lookup"><span data-stu-id="bf219-176">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="bf219-177">Konfiguracje mogą być dystrybuowane do komputera z systemem Linux z serwera ściągania, podobnie jak dla komputerów Windows.</span><span class="sxs-lookup"><span data-stu-id="bf219-177">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="bf219-178">Aby uzyskać wskazówki na temat korzystania z serwera ściągania, zobacz [Windows PowerShell Desired State Configuration ściągnięcia serwerów](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="bf219-178">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="bf219-179">Ograniczenia, powiązane z użyciem komputerów z systemem Linux z serwera ściągania i dodatkowe informacje Zobacz informacje o wersji dla Desired State Configuration dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="bf219-179">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="bf219-180">Praca z konfiguracjami lokalnie</span><span class="sxs-lookup"><span data-stu-id="bf219-180">Working with configurations locally</span></span>

<span data-ttu-id="bf219-181">DSC dla systemu Linux zawiera skrypty do pracy z konfiguracją z lokalnym komputerze z systemem Linux.</span><span class="sxs-lookup"><span data-stu-id="bf219-181">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="bf219-182">Te skrypty są zlokalizuj w `/opt/microsoft/dsc/Scripts` i obejmują następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="bf219-182">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>

- <span data-ttu-id="bf219-183">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="bf219-183">GetDscConfiguration.py</span></span>

<span data-ttu-id="bf219-184">Zwraca bieżącą konfigurację, które są stosowane do komputera.</span><span class="sxs-lookup"><span data-stu-id="bf219-184">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="bf219-185">Podobne do polecenia cmdlet programu Windows PowerShell `Get-DscConfiguration` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bf219-185">Similar to the Windows PowerShell cmdlet `Get-DscConfiguration` cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

- <span data-ttu-id="bf219-186">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="bf219-186">GetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="bf219-187">Zwraca bieżącą meta konfigurację zastosowane do komputera.</span><span class="sxs-lookup"><span data-stu-id="bf219-187">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="bf219-188">Podobne do polecenia cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bf219-188">Similar to the cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

- <span data-ttu-id="bf219-189">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="bf219-189">InstallModule.py</span></span>

<span data-ttu-id="bf219-190">Instaluje niestandardowego modułu zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="bf219-190">Installs a custom DSC resource module.</span></span> <span data-ttu-id="bf219-191">Wymaga ścieżkę do pliku zip zawierającego biblioteki udostępnionej obiektów modułu i pliki MOF schematu.</span><span class="sxs-lookup"><span data-stu-id="bf219-191">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- <span data-ttu-id="bf219-192">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="bf219-192">RemoveModule.py</span></span>

<span data-ttu-id="bf219-193">Usuwa niestandardowego modułu zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="bf219-193">Removes a custom DSC resource module.</span></span> <span data-ttu-id="bf219-194">Wymaga nazwy modułu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="bf219-194">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

- <span data-ttu-id="bf219-195">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="bf219-195">StartDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="bf219-196">Zastosowanie pliku MOF konfiguracji na komputerze.</span><span class="sxs-lookup"><span data-stu-id="bf219-196">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="bf219-197">Podobnie jak [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bf219-197">Similar to the [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.</span></span> <span data-ttu-id="bf219-198">Wymaga ścieżkę do pliku MOF, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="bf219-198">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- <span data-ttu-id="bf219-199">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="bf219-199">SetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="bf219-200">Zastosowanie pliku MOF konfiguracji Meta na komputerze.</span><span class="sxs-lookup"><span data-stu-id="bf219-200">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="bf219-201">Podobnie jak [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bf219-201">Similar to the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span> <span data-ttu-id="bf219-202">Wymaga ścieżkę do pliku MOF konfiguracji Meta do zastosowania.</span><span class="sxs-lookup"><span data-stu-id="bf219-202">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="bf219-203">Program PowerShell Desired State Configuration dla plików dziennika systemu Linux</span><span class="sxs-lookup"><span data-stu-id="bf219-203">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="bf219-204">Następujące pliki dziennika są generowane dla DSC dla systemu Linux wiadomości.</span><span class="sxs-lookup"><span data-stu-id="bf219-204">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="bf219-205">Plik dziennika</span><span class="sxs-lookup"><span data-stu-id="bf219-205">Log file</span></span>|<span data-ttu-id="bf219-206">Katalog</span><span class="sxs-lookup"><span data-stu-id="bf219-206">Directory</span></span>|<span data-ttu-id="bf219-207">Opis</span><span class="sxs-lookup"><span data-stu-id="bf219-207">Description</span></span>|
|---|---|---|
|<span data-ttu-id="bf219-208">**omiserver.log**</span><span class="sxs-lookup"><span data-stu-id="bf219-208">**omiserver.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="bf219-209">Komunikaty dotyczące operacji serwer modelu CIM OMI.</span><span class="sxs-lookup"><span data-stu-id="bf219-209">Messages relating to the operation of the OMI CIM server.</span></span>|
|<span data-ttu-id="bf219-210">**DSC.log**</span><span class="sxs-lookup"><span data-stu-id="bf219-210">**dsc.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="bf219-211">Komunikaty dotyczące operacji operacje zasobów lokalnych Configuration Manager (LCM) i DSC.</span><span class="sxs-lookup"><span data-stu-id="bf219-211">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|