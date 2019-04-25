---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Rozpoczynanie pracy z Desired State Configuration (DSC) dla systemu Linux
ms.openlocfilehash: a18b226d4b2d8b8e1ba8b4168ec6ad8f73c73c42
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079697"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="b36ea-103">Rozpoczynanie pracy z Desired State Configuration (DSC) dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="b36ea-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="b36ea-104">W tym temacie wyjaśniono, jak rozpocząć pracę, przy użyciu programu PowerShell Desired State Configuration (DSC) dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="b36ea-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="b36ea-105">Aby uzyskać ogólne informacje o DSC, zobacz [Rozpoczynanie pracy z usługą Windows PowerShell Desired State Configuration](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="b36ea-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="b36ea-106">Obsługiwane wersje systemu operacji systemu Linux</span><span class="sxs-lookup"><span data-stu-id="b36ea-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="b36ea-107">Następujące wersje systemu operacyjnego Linux są obsługiwane dla DSC dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="b36ea-107">The following Linux operating system versions are supported for DSC for Linux.</span></span>

- <span data-ttu-id="b36ea-108">CentOS 5, 6 i 7 — x86/x64 64</span><span class="sxs-lookup"><span data-stu-id="b36ea-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="b36ea-109">Debian GNU/Linux 6, 7 i 8 — x86/x64 64</span><span class="sxs-lookup"><span data-stu-id="b36ea-109">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="b36ea-110">Oracle Linux 5, 6 i 7 — x86/x64 64</span><span class="sxs-lookup"><span data-stu-id="b36ea-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="b36ea-111">Red Hat Enterprise Linux Server 5, 6 i 7 — x86/x64 64</span><span class="sxs-lookup"><span data-stu-id="b36ea-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="b36ea-112">SUSE Linux Enterprise Server 10, 11 i 12 — x86/x64 64</span><span class="sxs-lookup"><span data-stu-id="b36ea-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="b36ea-113">Serwer Ubuntu 12.04 LTS, 14.04 LTS i 16.04 LTS — x86/x64 64</span><span class="sxs-lookup"><span data-stu-id="b36ea-113">Ubuntu Server 12.04 LTS, 14.04 LTS and 16.04 LTS (x86/x64)</span></span>

<span data-ttu-id="b36ea-114">W poniższej tabeli opisano zależności pakietów wymaganych do DSC dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="b36ea-114">The following table describes the required package dependencies for DSC for Linux.</span></span>

|  <span data-ttu-id="b36ea-115">Wymagany pakiet</span><span class="sxs-lookup"><span data-stu-id="b36ea-115">Required package</span></span> |  <span data-ttu-id="b36ea-116">Opis</span><span class="sxs-lookup"><span data-stu-id="b36ea-116">Description</span></span> |  <span data-ttu-id="b36ea-117">Minimalna wersja</span><span class="sxs-lookup"><span data-stu-id="b36ea-117">Minimum version</span></span> |
|---|---|---|
| <span data-ttu-id="b36ea-118">glibc</span><span class="sxs-lookup"><span data-stu-id="b36ea-118">glibc</span></span>| <span data-ttu-id="b36ea-119">Biblioteka GNU</span><span class="sxs-lookup"><span data-stu-id="b36ea-119">GNU Library</span></span>| <span data-ttu-id="b36ea-120">2…4 – 31.30</span><span class="sxs-lookup"><span data-stu-id="b36ea-120">2…4 – 31.30</span></span>|
| <span data-ttu-id="b36ea-121">python</span><span class="sxs-lookup"><span data-stu-id="b36ea-121">python</span></span>| <span data-ttu-id="b36ea-122">Python</span><span class="sxs-lookup"><span data-stu-id="b36ea-122">Python</span></span>| <span data-ttu-id="b36ea-123">2.4 – 3.4</span><span class="sxs-lookup"><span data-stu-id="b36ea-123">2.4 – 3.4</span></span>|
| <span data-ttu-id="b36ea-124">omiserver</span><span class="sxs-lookup"><span data-stu-id="b36ea-124">omiserver</span></span>| <span data-ttu-id="b36ea-125">Infrastruktura zarządzania otwartego</span><span class="sxs-lookup"><span data-stu-id="b36ea-125">Open Management Infrastructure</span></span>| <span data-ttu-id="b36ea-126">1.0.8.1</span><span class="sxs-lookup"><span data-stu-id="b36ea-126">1.0.8.1</span></span>|
| <span data-ttu-id="b36ea-127">openssl</span><span class="sxs-lookup"><span data-stu-id="b36ea-127">openssl</span></span>| <span data-ttu-id="b36ea-128">Biblioteki OpenSSL</span><span class="sxs-lookup"><span data-stu-id="b36ea-128">OpenSSL Libraries</span></span>| <span data-ttu-id="b36ea-129">0.9.8 lub 1.0</span><span class="sxs-lookup"><span data-stu-id="b36ea-129">0.9.8 or 1.0</span></span>|
| <span data-ttu-id="b36ea-130">ctypes</span><span class="sxs-lookup"><span data-stu-id="b36ea-130">ctypes</span></span>| <span data-ttu-id="b36ea-131">Biblioteka CTypes języka Python</span><span class="sxs-lookup"><span data-stu-id="b36ea-131">Python CTypes library</span></span>| <span data-ttu-id="b36ea-132">Musi odpowiadać wersji języka Python</span><span class="sxs-lookup"><span data-stu-id="b36ea-132">Must match Python version</span></span>|
| <span data-ttu-id="b36ea-133">libcurl</span><span class="sxs-lookup"><span data-stu-id="b36ea-133">libcurl</span></span>| <span data-ttu-id="b36ea-134">biblioteki klienta http programu cURL</span><span class="sxs-lookup"><span data-stu-id="b36ea-134">cURL http client library</span></span>| <span data-ttu-id="b36ea-135">7.15.1</span><span class="sxs-lookup"><span data-stu-id="b36ea-135">7.15.1</span></span>|

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="b36ea-136">Instalowanie DSC dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="b36ea-136">Installing DSC for Linux</span></span>

<span data-ttu-id="b36ea-137">Należy zainstalować [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) przed zainstalowaniem DSC dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="b36ea-137">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="b36ea-138">Instalowanie OMI</span><span class="sxs-lookup"><span data-stu-id="b36ea-138">Installing OMI</span></span>

<span data-ttu-id="b36ea-139">Desired State Configuration for Linux wymaga, aby serwer modelu CIM Open Management Infrastructure (OMI), wersja 1.0.8.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="b36ea-139">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="b36ea-140">OMI można pobrać z Open Group: [Otwórz Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span><span class="sxs-lookup"><span data-stu-id="b36ea-140">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="b36ea-141">Aby zainstalować OMI, należy zainstalować pakiet, który jest odpowiedni dla systemu Linux (.rpm lub .deb) i wersją biblioteki OpenSSL (ssl_098 lub ssl_100) i architektura (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="b36ea-141">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="b36ea-142">Pakiety RPM są odpowiednie dla CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server i Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="b36ea-142">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="b36ea-143">DEB pakiety są odpowiednie dla Debian GNU/Linux i Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="b36ea-143">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="b36ea-144">Pakiety ssl_098 są odpowiednie dla komputerów z protokołem OpenSSL 0.9.8 instalowane, gdy pakiety ssl_100 są odpowiednie dla komputerów z biblioteki OpenSSL zainstalowany w wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="b36ea-144">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="b36ea-145">Aby określić zainstalowaną wersją biblioteki OpenSSL, uruchom polecenie `openssl version`.</span><span class="sxs-lookup"><span data-stu-id="b36ea-145">To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="b36ea-146">Uruchom następujące polecenie, aby zainstalować w systemie CentOS 7 x64 OMI.</span><span class="sxs-lookup"><span data-stu-id="b36ea-146">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="b36ea-147">Instalowanie DSC</span><span class="sxs-lookup"><span data-stu-id="b36ea-147">Installing DSC</span></span>

<span data-ttu-id="b36ea-148">DSC dla systemu Linux jest dostępna do pobrania [tutaj](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span><span class="sxs-lookup"><span data-stu-id="b36ea-148">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span></span>

<span data-ttu-id="b36ea-149">Aby zainstalować DSC, należy zainstalować pakiet, który jest odpowiedni dla systemu Linux (.rpm lub .deb) i wersją biblioteki OpenSSL (ssl_098 lub ssl_100) i architektura (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="b36ea-149">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="b36ea-150">Pakiety RPM są odpowiednie dla CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server i Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="b36ea-150">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="b36ea-151">DEB pakiety są odpowiednie dla Debian GNU/Linux i Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="b36ea-151">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="b36ea-152">Pakiety ssl_098 są odpowiednie dla komputerów z protokołem OpenSSL 0.9.8 instalowane, gdy pakiety ssl_100 są odpowiednie dla komputerów z biblioteki OpenSSL zainstalowany w wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="b36ea-152">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="b36ea-153">Aby określić zainstalowaną wersją biblioteki OpenSSL, uruchom polecenie wersją biblioteki openssl.</span><span class="sxs-lookup"><span data-stu-id="b36ea-153">To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="b36ea-154">Uruchom następujące polecenie, aby zainstalować w systemie CentOS 7 x64 DSC.</span><span class="sxs-lookup"><span data-stu-id="b36ea-154">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a><span data-ttu-id="b36ea-155">Za pomocą DSC dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="b36ea-155">Using DSC for Linux</span></span>

<span data-ttu-id="b36ea-156">W poniższych sekcjach opisano sposób tworzenia i uruchomionych konfiguracjach DSC na komputerach z systemem Linux.</span><span class="sxs-lookup"><span data-stu-id="b36ea-156">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="b36ea-157">Tworzenie dokumentów w pliku MOF konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b36ea-157">Creating a configuration MOF document</span></span>

<span data-ttu-id="b36ea-158">Konfiguracja programu Windows PowerShell — słowo kluczowe jest używany do utworzenia konfiguracji dla komputerów z systemem Linux, podobnie jak na komputerach Windows.</span><span class="sxs-lookup"><span data-stu-id="b36ea-158">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="b36ea-159">W poniższych krokach opisano tworzenie dokumentu konfiguracji dla komputera z systemem Linux przy użyciu programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b36ea-159">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="b36ea-160">Zaimportuj moduł nx.</span><span class="sxs-lookup"><span data-stu-id="b36ea-160">Import the nx module.</span></span> <span data-ttu-id="b36ea-161">Moduł programu Windows PowerShell nx zawiera schemat wbudowane zasoby DSC dla systemu Linux i musi być zainstalowane na komputerze lokalnym i zaimportowane w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b36ea-161">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

   - <span data-ttu-id="b36ea-162">Aby zainstalować moduł nx, skopiuj katalog modułu nx do jednej `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` lub `$PSHOME\Modules`.</span><span class="sxs-lookup"><span data-stu-id="b36ea-162">To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="b36ea-163">Moduł nx znajduje się w DSC pakietu instalacyjnego systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="b36ea-163">The nx module is included in the DSC for Linux installation package.</span></span> <span data-ttu-id="b36ea-164">Aby zaimportować moduł nx w konfiguracji, należy użyć `Import-DSCResource` polecenia:</span><span class="sxs-lookup"><span data-stu-id="b36ea-164">To import the nx module in your configuration, use the `Import-DSCResource` command:</span></span>

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. <span data-ttu-id="b36ea-165">Definiowanie konfiguracji i generowania dokumentu konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="b36ea-165">Define a configuration and generate the configuration document:</span></span>

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

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="b36ea-166">Wypychanie konfiguracji na komputerze z systemem Linux</span><span class="sxs-lookup"><span data-stu-id="b36ea-166">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="b36ea-167">Konfiguracja dokumentów (pliki MOF) może być przyczyną do komputera systemu Linux przy użyciu [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b36ea-167">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="b36ea-168">Aby można było użyć tego polecenia cmdlet, wraz z [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), lub [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) poleceń cmdlet, zdalnie do komputera z systemem Linux, należy użyć CIMSession.</span><span class="sxs-lookup"><span data-stu-id="b36ea-168">In order to use this cmdlet, along with the [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), or [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="b36ea-169">[New-CimSession](/powershell/module/CimCmdlets/New-CimSession) polecenie cmdlet służy do tworzenia CIMSession na komputerze z systemem Linux.</span><span class="sxs-lookup"><span data-stu-id="b36ea-169">The [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="b36ea-170">Poniższy kod przedstawia sposób tworzenia CIMSession DSC dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="b36ea-170">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName "root" -Message "Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl $true -SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl $true
$Sess=New-CimSession -Credential $credential -ComputerName $Node -Port 5986 -Authentication basic -SessionOption $opt -OperationTimeoutSec 90
```

> [!NOTE]
> <span data-ttu-id="b36ea-171">W trybie "Push" poświadczenia użytkownika musi być zalogowany jako użytkownik root na komputerze z systemem Linux.</span><span class="sxs-lookup"><span data-stu-id="b36ea-171">For “Push” mode, the user credential must be the root user on the Linux computer.</span></span>
> <span data-ttu-id="b36ea-172">Tylko połączeń SSL/TLS są obsługiwane w przypadku DSC dla systemu Linux, `New-CimSession` musi być używana z parametrem – UseSSL ustawionym na $true.</span><span class="sxs-lookup"><span data-stu-id="b36ea-172">Only SSL/TLS connections are supported for DSC for Linux, the `New-CimSession` must be used with the –UseSSL parameter set to $true.</span></span>
> <span data-ttu-id="b36ea-173">Certyfikat SSL używany przez OMI (w przypadku DSC) jest określona w pliku: `/opt/omi/etc/omiserver.conf` z właściwościami: pemfile i keyfile.</span><span class="sxs-lookup"><span data-stu-id="b36ea-173">The SSL certificate used by OMI (for DSC) is specified in the file: `/opt/omi/etc/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
> <span data-ttu-id="b36ea-174">Jeśli ten certyfikat nie jest zaufany przez komputer Windows, które są uruchomione [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) polecenia cmdlet na możesz zignorować weryfikację certyfikatu przy użyciu opcji CIMSession: `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`</span><span class="sxs-lookup"><span data-stu-id="b36ea-174">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`</span></span>

<span data-ttu-id="b36ea-175">Uruchom następujące polecenie, aby wypchnąć konfiguracji DSC do węzłów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="b36ea-175">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession $Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="b36ea-176">Dystrybucja konfiguracji z serwera ściągania</span><span class="sxs-lookup"><span data-stu-id="b36ea-176">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="b36ea-177">Konfiguracje mogą być dystrybuowane do komputera z systemem Linux z serwera ściągania, podobnie jak dla komputerów Windows.</span><span class="sxs-lookup"><span data-stu-id="b36ea-177">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="b36ea-178">Aby uzyskać wskazówki na temat korzystania z serwera ściągania, zobacz [Windows PowerShell Desired State Configuration ściągnięcia serwerów](../pull-server/pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="b36ea-178">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](../pull-server/pullServer.md).</span></span> <span data-ttu-id="b36ea-179">Ograniczenia, powiązane z użyciem komputerów z systemem Linux z serwera ściągania i dodatkowe informacje Zobacz informacje o wersji dla Desired State Configuration dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="b36ea-179">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="b36ea-180">Praca z konfiguracjami lokalnie</span><span class="sxs-lookup"><span data-stu-id="b36ea-180">Working with configurations locally</span></span>

<span data-ttu-id="b36ea-181">DSC dla systemu Linux zawiera skrypty do pracy z konfiguracją z lokalnym komputerze z systemem Linux.</span><span class="sxs-lookup"><span data-stu-id="b36ea-181">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="b36ea-182">Te skrypty są zlokalizuj w `/opt/microsoft/dsc/Scripts` i obejmują następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="b36ea-182">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>

- <span data-ttu-id="b36ea-183">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="b36ea-183">GetDscConfiguration.py</span></span>

<span data-ttu-id="b36ea-184">Zwraca bieżącą konfigurację, które są stosowane do komputera.</span><span class="sxs-lookup"><span data-stu-id="b36ea-184">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="b36ea-185">Podobne do polecenia cmdlet programu Windows PowerShell `Get-DscConfiguration` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b36ea-185">Similar to the Windows PowerShell cmdlet `Get-DscConfiguration` cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

- <span data-ttu-id="b36ea-186">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="b36ea-186">GetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="b36ea-187">Zwraca bieżącą meta konfigurację zastosowane do komputera.</span><span class="sxs-lookup"><span data-stu-id="b36ea-187">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="b36ea-188">Podobne do polecenia cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b36ea-188">Similar to the cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

- <span data-ttu-id="b36ea-189">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="b36ea-189">InstallModule.py</span></span>

<span data-ttu-id="b36ea-190">Instaluje niestandardowego modułu zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="b36ea-190">Installs a custom DSC resource module.</span></span> <span data-ttu-id="b36ea-191">Wymaga ścieżkę do pliku zip zawierającego biblioteki udostępnionej obiektów modułu i pliki MOF schematu.</span><span class="sxs-lookup"><span data-stu-id="b36ea-191">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- <span data-ttu-id="b36ea-192">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="b36ea-192">RemoveModule.py</span></span>

<span data-ttu-id="b36ea-193">Usuwa niestandardowego modułu zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="b36ea-193">Removes a custom DSC resource module.</span></span> <span data-ttu-id="b36ea-194">Wymaga nazwy modułu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="b36ea-194">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

- <span data-ttu-id="b36ea-195">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="b36ea-195">StartDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="b36ea-196">Zastosowanie pliku MOF konfiguracji na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b36ea-196">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="b36ea-197">Podobnie jak [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b36ea-197">Similar to the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="b36ea-198">Wymaga ścieżkę do pliku MOF, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="b36ea-198">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- <span data-ttu-id="b36ea-199">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="b36ea-199">SetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="b36ea-200">Zastosowanie pliku MOF konfiguracji Meta na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b36ea-200">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="b36ea-201">Podobnie jak [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b36ea-201">Similar to the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span> <span data-ttu-id="b36ea-202">Wymaga ścieżkę do pliku MOF konfiguracji Meta do zastosowania.</span><span class="sxs-lookup"><span data-stu-id="b36ea-202">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="b36ea-203">Program PowerShell Desired State Configuration dla plików dziennika systemu Linux</span><span class="sxs-lookup"><span data-stu-id="b36ea-203">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="b36ea-204">Następujące pliki dziennika są generowane dla DSC dla systemu Linux wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b36ea-204">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="b36ea-205">Plik dziennika</span><span class="sxs-lookup"><span data-stu-id="b36ea-205">Log file</span></span>|<span data-ttu-id="b36ea-206">Katalog</span><span class="sxs-lookup"><span data-stu-id="b36ea-206">Directory</span></span>|<span data-ttu-id="b36ea-207">Opis</span><span class="sxs-lookup"><span data-stu-id="b36ea-207">Description</span></span>|
|---|---|---|
|<span data-ttu-id="b36ea-208">**omiserver.log**</span><span class="sxs-lookup"><span data-stu-id="b36ea-208">**omiserver.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="b36ea-209">Komunikaty dotyczące operacji serwer modelu CIM OMI.</span><span class="sxs-lookup"><span data-stu-id="b36ea-209">Messages relating to the operation of the OMI CIM server.</span></span>|
|<span data-ttu-id="b36ea-210">**dsc.log**</span><span class="sxs-lookup"><span data-stu-id="b36ea-210">**dsc.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="b36ea-211">Komunikaty dotyczące operacji operacje zasobów lokalnych Configuration Manager (LCM) i DSC.</span><span class="sxs-lookup"><span data-stu-id="b36ea-211">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|
