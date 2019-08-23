---
ms.date: 08/15/2019
keywords: DSC, PowerShell, konfiguracja, instalacja
title: Wprowadzenie do konfiguracji żądanego stanu (DSC) dla systemu Windows
ms.openlocfilehash: a4f9db481afda65fc4ac5e553230dbba3037ac9a
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988928"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a><span data-ttu-id="1fe70-103">Wprowadzenie do konfiguracji żądanego stanu (DSC) dla systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1fe70-103">Get started with Desired State Configuration (DSC) for Windows</span></span>

<span data-ttu-id="1fe70-104">W tym temacie wyjaśniono, jak rozpocząć pracę z konfiguracją żądanego stanu (DSC) programu PowerShell dla systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1fe70-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Windows.</span></span>
<span data-ttu-id="1fe70-105">Aby uzyskać ogólne informacje na temat DSC, zobacz Wprowadzenie [do konfiguracji żądanego stanu programu Windows PowerShell](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="1fe70-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-windows-operation-system-versions"></a><span data-ttu-id="1fe70-106">Obsługiwane wersje systemu operacyjnego Windows</span><span class="sxs-lookup"><span data-stu-id="1fe70-106">Supported Windows operation system versions</span></span>

<span data-ttu-id="1fe70-107">Obsługiwane są następujące wersje:</span><span class="sxs-lookup"><span data-stu-id="1fe70-107">The following versions are supported:</span></span>

- <span data-ttu-id="1fe70-108">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="1fe70-108">Windows Server 2019</span></span>
- <span data-ttu-id="1fe70-109">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="1fe70-109">Windows Server 2016</span></span>
- <span data-ttu-id="1fe70-110">2012R2 systemu Windows Server</span><span class="sxs-lookup"><span data-stu-id="1fe70-110">Windows Server 2012R2</span></span>
- <span data-ttu-id="1fe70-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="1fe70-111">Windows Server 2012</span></span>
- <span data-ttu-id="1fe70-112">Windows Server 2008 R2 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="1fe70-112">Windows Server 2008 R2 SP1</span></span>
- <span data-ttu-id="1fe70-113">Windows 10</span><span class="sxs-lookup"><span data-stu-id="1fe70-113">Windows 10</span></span>
- <span data-ttu-id="1fe70-114">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="1fe70-114">Windows 8.1</span></span>
- <span data-ttu-id="1fe70-115">Windows 7</span><span class="sxs-lookup"><span data-stu-id="1fe70-115">Windows 7</span></span>

<span data-ttu-id="1fe70-116">Autonomiczna jednostka SKU produktu [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) nie zawiera implementacji żądanego stanu konfiguracją, więc nie może być zarządzana przez program PowerShell DSC lub konfigurację stanu Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="1fe70-116">The [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) standalone product sku does not contain an implementation of Desired State Configuraion so it cannot be managed by PowerShell DSC or Azure Automation State Configuration.</span></span>

## <a name="installing-dsc"></a><span data-ttu-id="1fe70-117">Instalowanie DSC</span><span class="sxs-lookup"><span data-stu-id="1fe70-117">Installing DSC</span></span>

<span data-ttu-id="1fe70-118">Konfiguracja żądanego stanu programu PowerShell jest dołączona do systemu Windows i aktualizowana przy użyciu środowiska Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="1fe70-118">PowerShell Desired State Configuration is included in Windows and updated through Windows Management Framework.</span></span>
<span data-ttu-id="1fe70-119">Najnowsza wersja to [Windows Management Framework 5,1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).</span><span class="sxs-lookup"><span data-stu-id="1fe70-119">The latest version is [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).</span></span>

> [!NOTE]
> <span data-ttu-id="1fe70-120">Aby zarządzać maszyną za pomocą usługi DSC, nie trzeba włączać funkcji DSC-Service w systemie Windows Server.</span><span class="sxs-lookup"><span data-stu-id="1fe70-120">You do not need to enable the Windows Server feature 'DSC-Service' to manage a machine using DSC.</span></span>
> <span data-ttu-id="1fe70-121">Ta funkcja jest wymagana tylko w przypadku kompilowania wystąpienia serwera ściągania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1fe70-121">That feature is only needed when building a Windows Pull Server instance.</span></span>

## <a name="using-dsc-for-windows"></a><span data-ttu-id="1fe70-122">Korzystanie z usługi DSC dla systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1fe70-122">Using DSC for Windows</span></span>

<span data-ttu-id="1fe70-123">W poniższych sekcjach wyjaśniono, jak tworzyć i uruchamiać konfiguracje DSC na komputerach z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="1fe70-123">The following sections explain how to create and run DSC configurations on Windows computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="1fe70-124">Tworzenie dokumentu MOF konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1fe70-124">Creating a configuration MOF document</span></span>

<span data-ttu-id="1fe70-125">Słowo kluczowe konfiguracji programu Windows PowerShell służy do tworzenia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1fe70-125">The Windows PowerShell Configuration keyword is used to create a configuration.</span></span>
<span data-ttu-id="1fe70-126">Poniższe kroki opisują Tworzenie dokumentu konfiguracji przy użyciu programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1fe70-126">The following steps describe the creation of a configuration document using Windows PowerShell.</span></span>

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a><span data-ttu-id="1fe70-127">Zdefiniuj konfigurację i Wygeneruj dokument konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="1fe70-127">Define a configuration and generate the configuration document:</span></span>

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```
#### <a name="install-a-module-containing-dsc-resources"></a><span data-ttu-id="1fe70-128">Instalowanie modułu zawierającego zasoby DSC</span><span class="sxs-lookup"><span data-stu-id="1fe70-128">Install a module containing DSC resources</span></span>

<span data-ttu-id="1fe70-129">Konfiguracja żądanego stanu programu Windows PowerShell obejmuje wbudowane moduły zawierające zasoby DSC.</span><span class="sxs-lookup"><span data-stu-id="1fe70-129">Windows PowerShell Desired State Configuration includes built-in modules containing DSC resources.</span></span>
<span data-ttu-id="1fe70-130">Moduły można również ładować ze źródeł zewnętrznych, takich jak Galeria programu PowerShell, przy użyciu poleceń cmdlet PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="1fe70-130">You can also load modules from external sources such as the PowerShell Gallery, using the PowerShellGet cmdlets.</span></span>

`Install-Module 'PSDscResources' -Verbose`

#### <a name="apply-the-configuration-to-the-machine"></a><span data-ttu-id="1fe70-131">Zastosuj konfigurację do maszyny</span><span class="sxs-lookup"><span data-stu-id="1fe70-131">Apply the configuration to the machine</span></span>

<span data-ttu-id="1fe70-132">Dokumenty konfiguracyjne (pliki MOF) można zastosować do maszyny za pomocą polecenia cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="1fe70-132">Configuration documents (MOF files) can be applied to the machine using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

`Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose`

#### <a name="get-the-current-state-of-the-configuration"></a><span data-ttu-id="1fe70-133">Pobierz bieżący stan konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1fe70-133">Get the current state of the configuration</span></span>

<span data-ttu-id="1fe70-134">Polecenie cmdlet [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) wykonuje zapytanie o bieżący stan maszyny i zwraca bieżące wartości konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1fe70-134">The [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet queries the current status of the machine and returns the current values for the configuration.</span></span>

`Get-DscConfiguration`

<span data-ttu-id="1fe70-135">Polecenie cmdlet [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) zwraca bieżącą meta-konfiguracyjną zastosowana do maszyny.</span><span class="sxs-lookup"><span data-stu-id="1fe70-135">The [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) cmdlet returns the current meta-configuration applied to the machine.</span></span>

`Get-DscLocalConfigurationManager`

#### <a name="remove-the-current-configuration-from-a-machine"></a><span data-ttu-id="1fe70-136">Usuń bieżącą konfigurację z komputera</span><span class="sxs-lookup"><span data-stu-id="1fe70-136">Remove the current configuration from a machine</span></span>

<span data-ttu-id="1fe70-137">[Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span><span class="sxs-lookup"><span data-stu-id="1fe70-137">The [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span></span>

`Remove-DscConfigurationDocument -Stage Current -Verbose`

#### <a name="configure-settings-in-local-configuration-manager"></a><span data-ttu-id="1fe70-138">Skonfiguruj ustawienia w Configuration Manager lokalnym</span><span class="sxs-lookup"><span data-stu-id="1fe70-138">Configure settings in Local Configuration Manager</span></span>

<span data-ttu-id="1fe70-139">Zastosuj plik MOF konfiguracji meta do maszyny przy użyciu polecenia cmdlet [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) .</span><span class="sxs-lookup"><span data-stu-id="1fe70-139">Apply a Meta Configuration MOF file to the machine using the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span>
<span data-ttu-id="1fe70-140">Wymaga ścieżki do pliku MOF konfiguracji meta.</span><span class="sxs-lookup"><span data-stu-id="1fe70-140">Requires the path to the Meta Configuration MOF.</span></span>

`Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose`

## <a name="windows-powershell-desired-state-configuration-log-files"></a><span data-ttu-id="1fe70-141">Pliki dziennika konfiguracji żądanego stanu programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1fe70-141">Windows PowerShell Desired State Configuration log files</span></span>

<span data-ttu-id="1fe70-142">Dzienniki usługi DSC są zapisywane w dzienniku zdarzeń systemu Windows w ścieżce `Microsoft-Windows-Dsc/Operational`.</span><span class="sxs-lookup"><span data-stu-id="1fe70-142">Logs for DSC are written to Windows Event Log in the path `Microsoft-Windows-Dsc/Operational`.</span></span>
<span data-ttu-id="1fe70-143">Dodatkowe dzienniki do celów debugowania można włączyć, wykonując czynności opisane w sekcji [gdzie znajdują się dzienniki zdarzeń DSC](/powershell/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="1fe70-143">Additional logs for debugging purposes can be enabled following the steps in [Where Are DSC Event Logs](/powershell/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).</span></span>
