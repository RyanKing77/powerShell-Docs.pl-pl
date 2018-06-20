---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Rozpoczynanie pracy z konfiguracji żądanego stanu (DSC) dla systemu Linux
ms.openlocfilehash: 0534cede979eb2917adb608dba622539fe4bdc45
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189435"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="e14cf-103">Rozpoczynanie pracy z konfiguracji żądanego stanu (DSC) dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="e14cf-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="e14cf-104">W tym temacie wyjaśniono, jak rozpocząć korzystanie z konfiguracji żądanego stanu środowiska PowerShell (DSC) dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="e14cf-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="e14cf-105">Aby uzyskać ogólne informacje o konfiguracji DSC, zobacz [wprowadzenie do konfiguracji żądanego stanu programu Windows PowerShell](overview.md).</span><span class="sxs-lookup"><span data-stu-id="e14cf-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="e14cf-106">Obsługiwane wersje systemu operacji systemu Linux</span><span class="sxs-lookup"><span data-stu-id="e14cf-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="e14cf-107">Następujące wersje systemu operacyjnego Linux są obsługiwane dla konfiguracji DSC dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="e14cf-107">The following Linux operating system versions are supported for DSC for Linux.</span></span>
- <span data-ttu-id="e14cf-108">CentOS 5, 6 i 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="e14cf-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="e14cf-109">Debian GNU/Linux 6, 7 i 8 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="e14cf-109">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="e14cf-110">Oracle Linux 5, 6 i 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="e14cf-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="e14cf-111">Red Hat Enterprise Linux Server 5, 6 i 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="e14cf-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="e14cf-112">SUSE Linux Enterprise Server 10, 11 i 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="e14cf-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="e14cf-113">Ubuntu Server 12.04 LTS, 14.04 LTS i 16.04 LTS (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="e14cf-113">Ubuntu Server 12.04 LTS, 14.04 LTS and 16.04 LTS (x86/x64)</span></span>

<span data-ttu-id="e14cf-114">W poniższej tabeli opisano zależności wymagany pakiet dla konfiguracji DSC dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="e14cf-114">The following table describes the required package dependencies for DSC for Linux.</span></span>

|  <span data-ttu-id="e14cf-115">Wymagany pakiet</span><span class="sxs-lookup"><span data-stu-id="e14cf-115">Required package</span></span> |  <span data-ttu-id="e14cf-116">Opis</span><span class="sxs-lookup"><span data-stu-id="e14cf-116">Description</span></span> |  <span data-ttu-id="e14cf-117">Minimalna wersja</span><span class="sxs-lookup"><span data-stu-id="e14cf-117">Minimum version</span></span> |
|---|---|---|
| <span data-ttu-id="e14cf-118">Glibc</span><span class="sxs-lookup"><span data-stu-id="e14cf-118">glibc</span></span>| <span data-ttu-id="e14cf-119">Biblioteka GNU</span><span class="sxs-lookup"><span data-stu-id="e14cf-119">GNU Library</span></span>| <span data-ttu-id="e14cf-120">2... 4-31.30</span><span class="sxs-lookup"><span data-stu-id="e14cf-120">2…4 – 31.30</span></span>|
| <span data-ttu-id="e14cf-121">Python</span><span class="sxs-lookup"><span data-stu-id="e14cf-121">python</span></span>| <span data-ttu-id="e14cf-122">Python</span><span class="sxs-lookup"><span data-stu-id="e14cf-122">Python</span></span>| <span data-ttu-id="e14cf-123">2.4 — 3.4</span><span class="sxs-lookup"><span data-stu-id="e14cf-123">2.4 – 3.4</span></span>|
| <span data-ttu-id="e14cf-124">omiserver</span><span class="sxs-lookup"><span data-stu-id="e14cf-124">omiserver</span></span>| <span data-ttu-id="e14cf-125">Infrastruktura zarządzania otwartego</span><span class="sxs-lookup"><span data-stu-id="e14cf-125">Open Management Infrastructure</span></span>| <span data-ttu-id="e14cf-126">1.0.8.1</span><span class="sxs-lookup"><span data-stu-id="e14cf-126">1.0.8.1</span></span>|
| <span data-ttu-id="e14cf-127">Biblioteki Openssl</span><span class="sxs-lookup"><span data-stu-id="e14cf-127">openssl</span></span>| <span data-ttu-id="e14cf-128">Biblioteki OpenSSL</span><span class="sxs-lookup"><span data-stu-id="e14cf-128">OpenSSL Libraries</span></span>| <span data-ttu-id="e14cf-129">0.9.8 lub 1.0</span><span class="sxs-lookup"><span data-stu-id="e14cf-129">0.9.8 or 1.0</span></span>|
| <span data-ttu-id="e14cf-130">ctypes</span><span class="sxs-lookup"><span data-stu-id="e14cf-130">ctypes</span></span>| <span data-ttu-id="e14cf-131">Biblioteka języka Python CTypes</span><span class="sxs-lookup"><span data-stu-id="e14cf-131">Python CTypes library</span></span>| <span data-ttu-id="e14cf-132">Musi odpowiadać wersji języka Python</span><span class="sxs-lookup"><span data-stu-id="e14cf-132">Must match Python version</span></span>|
| <span data-ttu-id="e14cf-133">libcurl</span><span class="sxs-lookup"><span data-stu-id="e14cf-133">libcurl</span></span>| <span data-ttu-id="e14cf-134">Biblioteka klienta http cURL</span><span class="sxs-lookup"><span data-stu-id="e14cf-134">cURL http client library</span></span>| <span data-ttu-id="e14cf-135">7.15.1</span><span class="sxs-lookup"><span data-stu-id="e14cf-135">7.15.1</span></span>|

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="e14cf-136">Instalowanie usługi Konfiguracja DSC dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="e14cf-136">Installing DSC for Linux</span></span>

<span data-ttu-id="e14cf-137">Musisz zainstalować [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) przed zainstalowaniem usługi Konfiguracja DSC dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="e14cf-137">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="e14cf-138">Instalowanie OMI</span><span class="sxs-lookup"><span data-stu-id="e14cf-138">Installing OMI</span></span>

<span data-ttu-id="e14cf-139">Żądany stan konfiguracji dla systemu Linux wymaga serwera modelu wspólnych informacji Open Management Infrastructure (OMI), wersja 1.0.8.1 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="e14cf-139">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="e14cf-140">OMI można pobrać z Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span><span class="sxs-lookup"><span data-stu-id="e14cf-140">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="e14cf-141">Aby zainstalować OMI, należy zainstalować pakiet, który jest odpowiedni dla systemu Linux (.rpm lub .deb) i wersji biblioteki OpenSSL (ssl_098 lub ssl_100) i architektury (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="e14cf-141">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="e14cf-142">Pakiety RPM są odpowiednie dla CentOS, Red Hat Enterprise Linux SUSE Linux Enterprise Server i Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="e14cf-142">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="e14cf-143">Pakiety DEB są odpowiednie dla Debian GNU/Linux i Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="e14cf-143">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="e14cf-144">Pakiety ssl_098 są odpowiednie dla komputerów z biblioteki OpenSSL 0.9.8 zainstalowane pakiety ssl_100 są odpowiednie dla komputerów z biblioteki OpenSSL zainstalowany w wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="e14cf-144">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> <span data-ttu-id="e14cf-145">**Uwaga**: Aby ustalić, z zainstalowaną wersją biblioteki OpenSSL, uruchom polecenie `openssl version`.</span><span class="sxs-lookup"><span data-stu-id="e14cf-145">**Note**: To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="e14cf-146">Uruchom następujące polecenie, aby zainstalować OMI w systemie CentOS 7 x64.</span><span class="sxs-lookup"><span data-stu-id="e14cf-146">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="e14cf-147">Instalowanie usługi Konfiguracja DSC</span><span class="sxs-lookup"><span data-stu-id="e14cf-147">Installing DSC</span></span>

<span data-ttu-id="e14cf-148">DSC dla systemu Linux jest dostępna do pobrania [tutaj](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="e14cf-148">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest).</span></span>

<span data-ttu-id="e14cf-149">Aby zainstalować usługi Konfiguracja DSC, należy zainstalować pakiet, który jest odpowiedni dla systemu Linux (.rpm lub .deb) i wersji biblioteki OpenSSL (ssl_098 lub ssl_100) i architektury (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="e14cf-149">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="e14cf-150">Pakiety RPM są odpowiednie dla CentOS, Red Hat Enterprise Linux SUSE Linux Enterprise Server i Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="e14cf-150">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="e14cf-151">Pakiety DEB są odpowiednie dla Debian GNU/Linux i Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="e14cf-151">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="e14cf-152">Pakiety ssl_098 są odpowiednie dla komputerów z biblioteki OpenSSL 0.9.8 zainstalowane pakiety ssl_100 są odpowiednie dla komputerów z biblioteki OpenSSL zainstalowany w wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="e14cf-152">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> <span data-ttu-id="e14cf-153">**Uwaga**: Aby określić zainstalowaną wersją biblioteki OpenSSL, uruchom polecenie wersji biblioteki openssl.</span><span class="sxs-lookup"><span data-stu-id="e14cf-153">**Note**: To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="e14cf-154">Uruchom następujące polecenie, aby zainstalować usługi Konfiguracja DSC w systemie CentOS 7 x64.</span><span class="sxs-lookup"><span data-stu-id="e14cf-154">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`


## <a name="using-dsc-for-linux"></a><span data-ttu-id="e14cf-155">Dla systemu Linux przy użyciu usługi Konfiguracja DSC</span><span class="sxs-lookup"><span data-stu-id="e14cf-155">Using DSC for Linux</span></span>

<span data-ttu-id="e14cf-156">W poniższych sekcjach opisano sposób tworzenia i uruchamiania na komputerach z systemem Linux konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="e14cf-156">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="e14cf-157">Tworzenie dokumentu MOF konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e14cf-157">Creating a configuration MOF document</span></span>

<span data-ttu-id="e14cf-158">Konfiguracja programu Windows PowerShell — słowo kluczowe jest używany do utworzenia konfiguracji dla komputerów z systemem Linux, podobnie jak na komputerach z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="e14cf-158">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="e14cf-159">W poniższych krokach opisano tworzenie dokumentu konfiguracji dla komputera z systemem Linux przy użyciu programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e14cf-159">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="e14cf-160">Zaimportuj moduł nx.</span><span class="sxs-lookup"><span data-stu-id="e14cf-160">Import the nx module.</span></span> <span data-ttu-id="e14cf-161">Moduł programu Windows PowerShell nx zawiera schemat wbudowany zasobów dla konfiguracji DSC dla systemu Linux i musi być zainstalowana na komputerze lokalnym i zaimportować w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e14cf-161">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

    <span data-ttu-id="e14cf-162">— Aby zainstalować moduł nx, skopiuj katalog modułu nx jednej `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` lub `$PSHOME\Modules`.</span><span class="sxs-lookup"><span data-stu-id="e14cf-162">-To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="e14cf-163">Moduł nx znajduje się w konfiguracji DSC pakietu instalacyjnego systemu Linux (MSI).</span><span class="sxs-lookup"><span data-stu-id="e14cf-163">The nx module is included in the DSC for Linux installation package (MSI).</span></span> <span data-ttu-id="e14cf-164">Aby zaimportować moduł nx w konfiguracji, należy użyć __DSCResource importu__ polecenia:</span><span class="sxs-lookup"><span data-stu-id="e14cf-164">To import the nx module in your configuration, use the __Import-DSCResource__ command:</span></span>

```powershell
Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

}
```
2. <span data-ttu-id="e14cf-165">Definiowanie konfiguracji i generowania dokumentu konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="e14cf-165">Define a configuration and generate the configuration document:</span></span>

```powershell
Configuration ExampleConfiguration{

    Import-DscResource -Module nx

    Node  "linuxhost.contoso.com"{
    nxFile ExampleFile {

        DestinationPath = "/tmp/example"
        Contents = "hello world `n"
        Ensure = "Present"
        Type = "File"
    }

    }
}
ExampleConfiguration -OutputPath:"C:\temp"
```

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="e14cf-166">Wypychana konfiguracji na komputerze z systemem Linux</span><span class="sxs-lookup"><span data-stu-id="e14cf-166">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="e14cf-167">Konfiguracja dokumentów (pliki MOF) może zostać umieszczony na komputerze systemu Linux za pomocą [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e14cf-167">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span> <span data-ttu-id="e14cf-168">Aby można było używać tego polecenia cmdlet, wraz z [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx), lub [DscConfiguration testu](https://technet.microsoft.com/en-us/library/dn407382.aspx) poleceń cmdlet, zdalnie do komputera z systemem Linux, musi użyć CIMSession.</span><span class="sxs-lookup"><span data-stu-id="e14cf-168">In order to use this cmdlet, along with the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx), or [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="e14cf-169">[New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) polecenia cmdlet służy do tworzenia CIMSession na komputerze z systemem Linux.</span><span class="sxs-lookup"><span data-stu-id="e14cf-169">The [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="e14cf-170">Poniższy kod przedstawia sposób tworzenia CIMSession dla konfiguracji DSC dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="e14cf-170">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90
```

> <span data-ttu-id="e14cf-171">**Uwaga**:</span><span class="sxs-lookup"><span data-stu-id="e14cf-171">**Note**:</span></span>
* <span data-ttu-id="e14cf-172">W trybie "Push" poświadczeń użytkownika musi być użytkownika głównego na komputerze z systemem Linux.</span><span class="sxs-lookup"><span data-stu-id="e14cf-172">For “Push” mode, the user credential must be the root user on the Linux computer.</span></span>
* <span data-ttu-id="e14cf-173">Dla systemu Linux, New-CimSession musi używać z parametrem – UseSSL wartość $true, dla DSC obsługiwane są tylko połączenia SSL/TLS.</span><span class="sxs-lookup"><span data-stu-id="e14cf-173">Only SSL/TLS connections are supported for DSC for Linux, the New-CimSession must be used with the –UseSSL parameter set to $true.</span></span>
* <span data-ttu-id="e14cf-174">Certyfikat SSL używany przez OMI (dla DSC) jest określona w pliku: `/opt/omi/etc/omiserver.conf` z właściwościami: pemfile i keyfile.</span><span class="sxs-lookup"><span data-stu-id="e14cf-174">The SSL certificate used by OMI (for DSC) is specified in the file: `/opt/omi/etc/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
<span data-ttu-id="e14cf-175">Jeśli ten certyfikat nie jest zaufany przez komputer z systemem Windows, które są uruchomione [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) polecenia cmdlet na, możesz zignorować weryfikacji certyfikatu przy użyciu opcji CIMSession: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span><span class="sxs-lookup"><span data-stu-id="e14cf-175">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span></span>

<span data-ttu-id="e14cf-176">Uruchom następujące polecenie, aby wypchnąć konfiguracji DSC do węzła systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="e14cf-176">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="e14cf-177">Przekazują konfigurację z serwerem ściągania</span><span class="sxs-lookup"><span data-stu-id="e14cf-177">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="e14cf-178">Konfiguracje mogą być dystrybuowane do komputera z systemem Linux na serwerze ściągania, podobnie jak na komputerach z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="e14cf-178">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="e14cf-179">Aby uzyskać wskazówki dotyczące korzystania z serwera ściągania, zobacz [Windows PowerShell żądanego stanu ściągania serwery konfiguracji](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="e14cf-179">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="e14cf-180">Dodatkowe informacje i ograniczenia dotyczące korzystania z serwera ściągania komputery z systemem Linux zobacz informacje o wersji dla konfiguracji żądanego stanu dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="e14cf-180">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="e14cf-181">Praca z konfiguracjami lokalnie</span><span class="sxs-lookup"><span data-stu-id="e14cf-181">Working with configurations locally</span></span>

<span data-ttu-id="e14cf-182">DSC Linux obejmuje skrypty do pracy z konfiguracji z komputera lokalnego systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="e14cf-182">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="e14cf-183">Skrypty te są zlokalizować w `/opt/microsoft/dsc/Scripts` i są następujące:</span><span class="sxs-lookup"><span data-stu-id="e14cf-183">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>
* <span data-ttu-id="e14cf-184">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="e14cf-184">GetDscConfiguration.py</span></span>

 <span data-ttu-id="e14cf-185">Zwraca bieżącą konfigurację, które są stosowane do komputera.</span><span class="sxs-lookup"><span data-stu-id="e14cf-185">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="e14cf-186">Podobne do polecenia cmdlet programu Windows PowerShell polecenia cmdlet Get-DscConfiguration.</span><span class="sxs-lookup"><span data-stu-id="e14cf-186">Similar to the Windows PowerShell cmdlet Get-DscConfiguration cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

* <span data-ttu-id="e14cf-187">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="e14cf-187">GetDscLocalConfigurationManager.py</span></span>

 <span data-ttu-id="e14cf-188">Zwraca bieżącą meta konfigurację zastosowane do komputera.</span><span class="sxs-lookup"><span data-stu-id="e14cf-188">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="e14cf-189">Podobne do polecenia cmdlet [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e14cf-189">Similar to the cmdlet [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

* <span data-ttu-id="e14cf-190">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="e14cf-190">InstallModule.py</span></span>

 <span data-ttu-id="e14cf-191">Instaluje niestandardowego modułu zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="e14cf-191">Installs a custom DSC resource module.</span></span> <span data-ttu-id="e14cf-192">Wymaga ścieżkę do pliku zip zawierającego biblioteki udostępnionej modułu i pliki MOF schematu.</span><span class="sxs-lookup"><span data-stu-id="e14cf-192">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

* <span data-ttu-id="e14cf-193">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="e14cf-193">RemoveModule.py</span></span>

 <span data-ttu-id="e14cf-194">Usuwa niestandardowego modułu zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="e14cf-194">Removes a custom DSC resource module.</span></span> <span data-ttu-id="e14cf-195">Wymaga Nazwa modułu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="e14cf-195">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

* <span data-ttu-id="e14cf-196">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="e14cf-196">StartDscLocalConfigurationManager.py</span></span>

 <span data-ttu-id="e14cf-197">Zastosowanie pliku MOF konfiguracji na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e14cf-197">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="e14cf-198">Podobnie jak [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e14cf-198">Similar to the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span> <span data-ttu-id="e14cf-199">Wymaga ścieżka do konfiguracji MOF do zastosowania.</span><span class="sxs-lookup"><span data-stu-id="e14cf-199">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

* <span data-ttu-id="e14cf-200">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="e14cf-200">SetDscLocalConfigurationManager.py</span></span>

 <span data-ttu-id="e14cf-201">Zastosowanie pliku MOF konfiguracji Meta na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e14cf-201">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="e14cf-202">Podobnie jak [DSCLocalConfigurationManager zestaw](https://technet.microsoft.com/en-us/library/dn521621.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e14cf-202">Similar to the [Set-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) cmdlet.</span></span> <span data-ttu-id="e14cf-203">Wymaga ścieżki do MOF konfiguracji Meta do zastosowania.</span><span class="sxs-lookup"><span data-stu-id="e14cf-203">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="e14cf-204">PowerShell Konfiguracja żądanego stanu dla plików dziennika systemu Linux</span><span class="sxs-lookup"><span data-stu-id="e14cf-204">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="e14cf-205">Następujące pliki dziennika są generowane dla DSC komunikatów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="e14cf-205">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="e14cf-206">Plik dziennika</span><span class="sxs-lookup"><span data-stu-id="e14cf-206">Log file</span></span>|<span data-ttu-id="e14cf-207">Katalog</span><span class="sxs-lookup"><span data-stu-id="e14cf-207">Directory</span></span>|<span data-ttu-id="e14cf-208">Opis</span><span class="sxs-lookup"><span data-stu-id="e14cf-208">Description</span></span>|
|---|---|---|
|<span data-ttu-id="e14cf-209">omiserver.log</span><span class="sxs-lookup"><span data-stu-id="e14cf-209">omiserver.log</span></span>|<span data-ttu-id="e14cf-210">/var/OPT/OMI/log</span><span class="sxs-lookup"><span data-stu-id="e14cf-210">/var/opt/omi/log</span></span>|<span data-ttu-id="e14cf-211">Komunikaty dotyczące operacji serwera modelu wspólnych informacji OMI.</span><span class="sxs-lookup"><span data-stu-id="e14cf-211">Messages relating to the operation of the OMI CIM server.</span></span>|
|<span data-ttu-id="e14cf-212">DSC.log</span><span class="sxs-lookup"><span data-stu-id="e14cf-212">dsc.log</span></span>|<span data-ttu-id="e14cf-213">/var/OPT/OMI/log</span><span class="sxs-lookup"><span data-stu-id="e14cf-213">/var/opt/omi/log</span></span>|<span data-ttu-id="e14cf-214">Komunikaty dotyczące operacji operacji zasobu lokalnego Configuration Manager (LCM) i usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="e14cf-214">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|