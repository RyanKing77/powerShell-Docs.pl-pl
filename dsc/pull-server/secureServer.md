---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Najlepsze rozwiązania dotyczące serwera ściągania
ms.openlocfilehash: da67f8fd793878b097ffb260afad0fcf5c69bb04
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405264"
---
# <a name="pull-server-best-practices"></a><span data-ttu-id="5bb17-103">Najlepsze rozwiązania dotyczące serwera ściągania</span><span class="sxs-lookup"><span data-stu-id="5bb17-103">Pull server best practices</span></span>

<span data-ttu-id="5bb17-104">Dotyczy: Program Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5bb17-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5bb17-105">Serwera ściągania (funkcja Windows *usługi DSC*) jest obsługiwanych składników systemu Windows Server jednak nie jest planowane oferują nowe funkcje lub możliwości osobno.</span><span class="sxs-lookup"><span data-stu-id="5bb17-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="5bb17-106">Zaleca się rozpocząć przechodzenie zarządzanych klientom [usługi Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (w tym funkcje poza serwera ściągania w systemie Windows Server) lub jeden z członków społeczności na liście [tutaj](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="5bb17-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="5bb17-107">Podsumowanie: Ten dokument jest przeznaczony do uwzględnienia procesów i rozszerzalność do pomocy inżynierów, którzy są przygotowywanie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="5bb17-107">Summary: This document is intended to include process and extensibility to assist engineers who are preparing for the solution.</span></span> <span data-ttu-id="5bb17-108">Szczegółowe informacje, należy zapewnić najlepsze rozwiązania, jak identyfikowane przez klientów i zweryfikowany przez zespół pracujący nad produktem zalecenia są przyszłych umożliwiających dostęp i uznawana za stabilną.</span><span class="sxs-lookup"><span data-stu-id="5bb17-108">Details should provide best practices as identified by customers and then validated by the product team to ensure recommendations are future facing and considered stable.</span></span>

| |<span data-ttu-id="5bb17-109">Informacje o dokumencie</span><span class="sxs-lookup"><span data-stu-id="5bb17-109">Doc Info</span></span>|
|:---|:---|
<span data-ttu-id="5bb17-110">Autor</span><span class="sxs-lookup"><span data-stu-id="5bb17-110">Author</span></span> | <span data-ttu-id="5bb17-111">Michael Greene</span><span class="sxs-lookup"><span data-stu-id="5bb17-111">Michael Greene</span></span>
<span data-ttu-id="5bb17-112">Recenzenci</span><span class="sxs-lookup"><span data-stu-id="5bb17-112">Reviewers</span></span> | <span data-ttu-id="5bb17-113">Ben Gelens, Ravikanth Chaganti Aleksandar Nikolic</span><span class="sxs-lookup"><span data-stu-id="5bb17-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span></span>
<span data-ttu-id="5bb17-114">Opublikowane</span><span class="sxs-lookup"><span data-stu-id="5bb17-114">Published</span></span> | <span data-ttu-id="5bb17-115">Kwietnia 2015 r.</span><span class="sxs-lookup"><span data-stu-id="5bb17-115">April, 2015</span></span>

## <a name="abstract"></a><span data-ttu-id="5bb17-116">Abstrakcyjny</span><span class="sxs-lookup"><span data-stu-id="5bb17-116">Abstract</span></span>

<span data-ttu-id="5bb17-117">Ten dokument jest przeznaczony oficjalne wytyczne dla każdego, kto Planowanie wdrożenia serwera ściągania Desired State Configuration programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5bb17-117">This document is designed to provide official guidance for anyone planning for a Windows PowerShell Desired State Configuration pull server implementation.</span></span> <span data-ttu-id="5bb17-118">Serwer ściągania jest prostą usługę, które powinny zająć tylko kilka minut wdrożyć.</span><span class="sxs-lookup"><span data-stu-id="5bb17-118">A pull server is a simple service that should take only minutes to deploy.</span></span> <span data-ttu-id="5bb17-119">Mimo że ten dokument będzie oferować wskazówek porad technicznych, używanej we wdrożeniu, wartość w tym dokumencie jest jako odniesienie do najlepszych rozwiązań i co wziąć pod uwagę przed wdrożeniem.</span><span class="sxs-lookup"><span data-stu-id="5bb17-119">Although this document will offer technical how-to guidance that can be used in a deployment, the value of this document is as a reference for best practices and what to think about before deploying.</span></span>
<span data-ttu-id="5bb17-120">Czytelnicy powinny mieć podstawowe znajomość DSC i terminy używane do opisywania składników, które są uwzględnione w wdrożenia DSC.</span><span class="sxs-lookup"><span data-stu-id="5bb17-120">Readers should have basic familiarity with DSC, and the terms used to describe the components that are included in a DSC deployment.</span></span> <span data-ttu-id="5bb17-121">Aby uzyskać więcej informacji, zobacz [Windows PowerShell Desired State Configuration Overview](/powershell/dsc/overview) tematu.</span><span class="sxs-lookup"><span data-stu-id="5bb17-121">For more information, see the [Windows PowerShell Desired State Configuration Overview](/powershell/dsc/overview)  topic.</span></span>
<span data-ttu-id="5bb17-122">Oczekiwaniami DSC podlegać ewolucji w erze chmury podstawowej technologii, w tym serwera ściągania również oczekuje się rozwijać i wprowadzają nowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="5bb17-122">As DSC is expected to evolve at cloud cadence, the underlying technology including pull server is also expected to evolve and to introduce new capabilities.</span></span> <span data-ttu-id="5bb17-123">Ten dokument zawiera tabelę wersji w dodatku, który zawiera odwołania do poprzednich wersji i odwołań pozwalającą na przyszłe wyglądających rozwiązania do tworzenia, nowoczesne projekty.</span><span class="sxs-lookup"><span data-stu-id="5bb17-123">This document includes a version table in the appendix that provides references to previous releases and references to future looking solutions to encourage forward-looking designs.</span></span>

<span data-ttu-id="5bb17-124">Dwie główne części tego dokumentu:</span><span class="sxs-lookup"><span data-stu-id="5bb17-124">The two major sections of this document:</span></span>

- <span data-ttu-id="5bb17-125">Planowanie konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5bb17-125">Configuration Planning</span></span>
- <span data-ttu-id="5bb17-126">Przewodnik instalacji</span><span class="sxs-lookup"><span data-stu-id="5bb17-126">Installation Guide</span></span>

### <a name="versions-of-the-windows-management-framework"></a><span data-ttu-id="5bb17-127">Wersje Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="5bb17-127">Versions of the Windows Management Framework</span></span>

<span data-ttu-id="5bb17-128">Informacje przedstawione w tym dokumencie jest przeznaczony do zastosowania do systemu Windows Management Framework 5.0.</span><span class="sxs-lookup"><span data-stu-id="5bb17-128">The information in this document is intended to apply to Windows Management Framework 5.0.</span></span> <span data-ttu-id="5bb17-129">Program WMF 5.0 nie jest wymagany do wdrażania i obsługi serwera ściągania, wersja 5.0 jest celem tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5bb17-129">While WMF 5.0 is not required for deploying and operating a pull server, version 5.0 is the focus of this document.</span></span>

### <a name="windows-powershell-desired-state-configuration"></a><span data-ttu-id="5bb17-130">Program Windows PowerShell Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="5bb17-130">Windows PowerShell Desired State Configuration</span></span>

<span data-ttu-id="5bb17-131">Desired State Configuration (DSC) to platforma zarządzania, która umożliwia wdrażanie i zarządzanie nimi danych konfiguracji za pomocą składni branży o nazwie Managed Object Format (MOF) do opisywania modelu wspólnych informacji (CIM).</span><span class="sxs-lookup"><span data-stu-id="5bb17-131">Desired State Configuration (DSC) is a management platform that enables deploying and managing configuration data by using an industry syntax named the Managed Object Format (MOF) to describe the Common Information Model (CIM).</span></span> <span data-ttu-id="5bb17-132">Projekt open source, Open Management Infrastructure (OMI), istnieje w celu dalszego rozwoju norm między platformami, łącznie z systemem Linux i sieć sprzętu, systemów operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="5bb17-132">An open source project, Open Management Infrastructure (OMI), exists to further development of these standards across platforms including Linux and network hardware operating systems.</span></span> <span data-ttu-id="5bb17-133">Aby uzyskać więcej informacji, zobacz [DMTF strony łączenia z pliku MOF specyfikacje](https://www.dmtf.org/standards/cim), i [OMI dokumentów i źródła](https://collaboration.opengroup.org/omi/documents.php).</span><span class="sxs-lookup"><span data-stu-id="5bb17-133">For more information, see the [DMTF page linking to MOF specifications](https://www.dmtf.org/standards/cim), and [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php).</span></span>

<span data-ttu-id="5bb17-134">Program Windows PowerShell zawiera zbiór rozszerzenia językowe dla Desired State Configuration, który umożliwia tworzenie i zarządzanie konfiguracjami deklaratywne.</span><span class="sxs-lookup"><span data-stu-id="5bb17-134">Windows PowerShell provides a set of language extensions for Desired State Configuration that you can use to create and manage declarative configurations.</span></span>

### <a name="pull-server-role"></a><span data-ttu-id="5bb17-135">Rola serwera ściągania</span><span class="sxs-lookup"><span data-stu-id="5bb17-135">Pull server role</span></span>

<span data-ttu-id="5bb17-136">Serwerze ściągania zapewnia scentralizowane service do przechowywania konfiguracji, które będą dostępne dla węzłów docelowych.</span><span class="sxs-lookup"><span data-stu-id="5bb17-136">A pull server provides a centralized service to store configurations that will be accessible to target nodes.</span></span>

<span data-ttu-id="5bb17-137">Rola serwera ściągania może być wdrożony jako wystąpienia serwera sieci Web lub udziału plików SMB.</span><span class="sxs-lookup"><span data-stu-id="5bb17-137">The pull server role can be deployed as either a Web Server instance or an SMB file share.</span></span> <span data-ttu-id="5bb17-138">Funkcja serwer sieci web obejmuje interfejsu OData i może opcjonalnie uwzględnić możliwości dla węzłów docelowych się wstecz potwierdzeniem powodzenia lub niepowodzenia na konfiguracje są stosowane.</span><span class="sxs-lookup"><span data-stu-id="5bb17-138">The web server capability includes an OData interface and can optionally include capabilities for target nodes to report back confirmation of success or failure as configurations are applied.</span></span> <span data-ttu-id="5bb17-139">Ta funkcja jest przydatna w środowiskach, w przypadku dużej liczby węzłów docelowych.</span><span class="sxs-lookup"><span data-stu-id="5bb17-139">This functionality is useful in environments where there are a large number of target nodes.</span></span>
<span data-ttu-id="5bb17-140">Po skonfigurowaniu węzła docelowego (określane również jako klienta), aby wskazywały serwer ściągania z ostatnią konfiguracją danych i wszystkie wymagane skrypty są pobierane i stosowane.</span><span class="sxs-lookup"><span data-stu-id="5bb17-140">After configuring a target node (also referred to as a client) to point to the pull server the latest configuration data and any required scripts are downloaded and applied.</span></span> <span data-ttu-id="5bb17-141">Może to nastąpić jako jednorazowego wdrażania lub ponownie występujące zadania, które sprawia, że serwera ściągania istotny element zarządzania zmiany na dużą skalę.</span><span class="sxs-lookup"><span data-stu-id="5bb17-141">This can happen as a one-time deployment or as a re-occurring job which also makes the pull server an important asset for managing change at scale.</span></span> <span data-ttu-id="5bb17-142">Aby uzyskać więcej informacji, zobacz [Windows PowerShell Desired State Configuration ściągnięcia serwerów](/powershell/dsc/pullServer) i</span><span class="sxs-lookup"><span data-stu-id="5bb17-142">For more information, see [Windows PowerShell Desired State Configuration Pull Servers](/powershell/dsc/pullServer) and</span></span>

<span data-ttu-id="5bb17-143">[Wypychanie i ściąganie trybów konfiguracji](/powershell/dsc/pullServer).</span><span class="sxs-lookup"><span data-stu-id="5bb17-143">[Push and Pull Configuration Modes](/powershell/dsc/pullServer).</span></span>

## <a name="configuration-planning"></a><span data-ttu-id="5bb17-144">Planowanie konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5bb17-144">Configuration planning</span></span>

<span data-ttu-id="5bb17-145">Dla każdego wdrożenia oprogramowania przedsiębiorstwa ma informacji, które mogą być zbierane z wyprzedzeniem ułatwiające Planowanie architektury i przygotować czynności wymagane do ukończenia wdrażania.</span><span class="sxs-lookup"><span data-stu-id="5bb17-145">For any enterprise software deployment there is information that can be collected in advance to help plan for the correct architecture and to be prepared for the steps required to complete the deployment.</span></span> <span data-ttu-id="5bb17-146">Poniższe sekcje zawierają informacje dotyczące sposobu przygotowania i połączenia organizacji, które prawdopodobnie wystąpi konieczność się tak zdarzyć z wyprzedzeniem.</span><span class="sxs-lookup"><span data-stu-id="5bb17-146">The following sections provide information regarding how to prepare and the organizational connections that will likely need to happen in advance.</span></span>

### <a name="software-requirements"></a><span data-ttu-id="5bb17-147">Wymagania dotyczące oprogramowania</span><span class="sxs-lookup"><span data-stu-id="5bb17-147">Software requirements</span></span>

<span data-ttu-id="5bb17-148">Wdrożenie serwera ściągania wymaga funkcji DSC usługi systemu Windows Server.</span><span class="sxs-lookup"><span data-stu-id="5bb17-148">Deployment of a pull server requires the DSC Service feature of Windows Server.</span></span> <span data-ttu-id="5bb17-149">Ta funkcja została wprowadzona w systemie Windows Server 2012 i został zaktualizowany przy użyciu bieżących wersji Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="5bb17-149">This feature was introduced in Windows Server 2012, and has been updated through ongoing releases of Windows Management Framework (WMF).</span></span>

### <a name="software-downloads"></a><span data-ttu-id="5bb17-150">Pobieranie oprogramowania</span><span class="sxs-lookup"><span data-stu-id="5bb17-150">Software downloads</span></span>

<span data-ttu-id="5bb17-151">Oprócz instalowania najnowszej zawartości z usługi Windows Update, istnieją dwa pliki do pobrania, które są traktowane jako najlepsze rozwiązanie, aby wdrożyć serwer ściągania DSC: Najnowsza wersja programu Windows Management Framework i modułu DSC, aby zautomatyzować aprowizację serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="5bb17-151">In addition to installing the latest content from Windows Update, there are two downloads considered best practice to deploy a DSC pull server: The latest version of Windows Management Framework, and a DSC module to automate pull server provisioning.</span></span>

### <a name="wmf"></a><span data-ttu-id="5bb17-152">WMF</span><span class="sxs-lookup"><span data-stu-id="5bb17-152">WMF</span></span>

<span data-ttu-id="5bb17-153">Windows Server 2012 R2 zawiera funkcję o nazwie usługi DSC.</span><span class="sxs-lookup"><span data-stu-id="5bb17-153">Windows Server 2012 R2 includes a feature named the DSC Service.</span></span> <span data-ttu-id="5bb17-154">Funkcja usługi DSC udostępnia funkcje serwera ściągania, w tym pliki binarne, które obsługują punkt końcowy OData.</span><span class="sxs-lookup"><span data-stu-id="5bb17-154">The DSC Service feature provides the pull server functionality, including the binaries that support the OData endpoint.</span></span>
<span data-ttu-id="5bb17-155">WMF znajduje się w systemie Windows Server i jest aktualizowany w erze agile między wersjami systemu Windows Server.</span><span class="sxs-lookup"><span data-stu-id="5bb17-155">WMF is included in Windows Server and is updated on an agile cadence between Windows Server releases.</span></span> <span data-ttu-id="5bb17-156">[Nowe wersje programu WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616) mogą obejmować aktualizacje funkcji usługi DSC.</span><span class="sxs-lookup"><span data-stu-id="5bb17-156">[New versions of WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616)  can include updates to the DSC Service feature.</span></span> <span data-ttu-id="5bb17-157">Z tego powodu jest najlepszym rozwiązaniem jest, aby pobrać najnowszą wersję programu WMF i przejrzyj informacje o wersji, aby określić, jeśli ta wersja obejmuje aktualizację funkcji usługi DSC.</span><span class="sxs-lookup"><span data-stu-id="5bb17-157">For this reason, it is a best practice to download the latest release of WMF and to review the release notes to determine if the release includes an update to the DSC service feature.</span></span> <span data-ttu-id="5bb17-158">Należy również sprawdzić sekcji informacje o wersji, wskazującą, czy stan projektu dla aktualizacji lub scenariusz jest wymieniony jako stałe lub eksperymentalne.</span><span class="sxs-lookup"><span data-stu-id="5bb17-158">You should also review the section of the release notes that indicates whether the design status for an update or scenario is listed as stable or experimental.</span></span>
<span data-ttu-id="5bb17-159">Umożliwia elastyczne cyklu, poszczególne funkcje mogą być deklarowane stabilny, co oznacza, funkcja jest gotowa do użycia w środowisku produkcyjnym, nawet wtedy, gdy program WMF została wydana w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="5bb17-159">To allow for an agile release cycle, individual features can be declared stable, which indicates the feature is ready to be used in a production environment even while WMF is released in preview.</span></span>
<span data-ttu-id="5bb17-160">Inne funkcje, które wcześniej zostały zaktualizowane przez program WMF wersje (patrz dalsze szczegółowe informacje o wersji programu WMF):</span><span class="sxs-lookup"><span data-stu-id="5bb17-160">Other features that have historically been updated by WMF releases (see the WMF Release Notes for further detail):</span></span>

- <span data-ttu-id="5bb17-161">Windows PowerShell, Windows PowerShell Integrated Scripting</span><span class="sxs-lookup"><span data-stu-id="5bb17-161">Windows PowerShell Windows PowerShell Integrated Scripting</span></span>
- <span data-ttu-id="5bb17-162">(ISE) środowiska Windows PowerShell Web Services (Zarządzanie OData</span><span class="sxs-lookup"><span data-stu-id="5bb17-162">Environment (ISE) Windows PowerShell Web Services (Management OData</span></span>
- <span data-ttu-id="5bb17-163">Rozszerzenie usług IIS) Windows PowerShell Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="5bb17-163">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="5bb17-164">Windows Remote Management (WinRM) Instrumentacji zarządzania Windows (WMI)</span><span class="sxs-lookup"><span data-stu-id="5bb17-164">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span></span>

### <a name="dsc-resource"></a><span data-ttu-id="5bb17-165">Zasób DSC</span><span class="sxs-lookup"><span data-stu-id="5bb17-165">DSC resource</span></span>

<span data-ttu-id="5bb17-166">Wdrożenie serwera ściągania można uprościć Inicjowanie obsługi usługi przy użyciu skryptu konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="5bb17-166">A pull server deployment can be simplified by provisioning the service using a DSC configuration script.</span></span> <span data-ttu-id="5bb17-167">Ten dokument zawiera skrypty konfiguracji, których można użyć do wdrożenia węźle gotowe serwerów produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="5bb17-167">This document includes configuration scripts that can be used to deploy a production ready server node.</span></span> <span data-ttu-id="5bb17-168">Aby użyć skryptów konfiguracyjnych, modułu DSC jest wymagana oznacza to nie jest uwzględniony w systemie Windows Server.</span><span class="sxs-lookup"><span data-stu-id="5bb17-168">To use the configuration scripts, a DSC module is required that is not included in Windows Server.</span></span> <span data-ttu-id="5bb17-169">Nazwa modułu wymagane jest **xPSDesiredStateConfiguration**, który zawiera zasób DSC **xDscWebService**.</span><span class="sxs-lookup"><span data-stu-id="5bb17-169">The required module name is **xPSDesiredStateConfiguration**, which includes the DSC resource **xDscWebService**.</span></span> <span data-ttu-id="5bb17-170">Można go pobrać moduł xPSDesiredStateConfiguration [tutaj](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span><span class="sxs-lookup"><span data-stu-id="5bb17-170">The xPSDesiredStateConfiguration module can be downloaded [here](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span></span>

<span data-ttu-id="5bb17-171">Użyj `Install-Module` polecenia cmdlet z **PowerShellGet** modułu.</span><span class="sxs-lookup"><span data-stu-id="5bb17-171">Use the `Install-Module` cmdlet from the **PowerShellGet** module.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="5bb17-172">**PowerShellGet** modułu pobierze modułu do:</span><span class="sxs-lookup"><span data-stu-id="5bb17-172">The **PowerShellGet** module will download the module to:</span></span>

`C:\Program Files\Windows PowerShell\Modules`

<span data-ttu-id="5bb17-173">Planowanie zadań</span><span class="sxs-lookup"><span data-stu-id="5bb17-173">Planning task</span></span>|
---|
<span data-ttu-id="5bb17-174">Czy masz dostęp do plików instalacji systemu Windows Server 2012 R2?</span><span class="sxs-lookup"><span data-stu-id="5bb17-174">Do you have access to the installation files for Windows Server 2012 R2?</span></span>|
<span data-ttu-id="5bb17-175">Środowisko wdrażania, będą miały dostęp do Internetu Pobierz program WMF oraz modułu z galerii online?</span><span class="sxs-lookup"><span data-stu-id="5bb17-175">Will the deployment environment have Internet access to download WMF and the module from the online gallery?</span></span>|
<span data-ttu-id="5bb17-176">Jak należy zainstalować najnowsze aktualizacje zabezpieczeń, po zainstalowaniu systemu operacyjnego?</span><span class="sxs-lookup"><span data-stu-id="5bb17-176">How will you install the latest security updates after installing the operating system?</span></span>|
<span data-ttu-id="5bb17-177">Środowiska mają dostęp do Internetu, aby uzyskać aktualizacje, czy mają lokalnego serwera Windows Server Update Services (WSUS)?</span><span class="sxs-lookup"><span data-stu-id="5bb17-177">Will the environment have Internet access to obtain updates, or will it have a local Windows Server Update Services (WSUS) server?</span></span>|
<span data-ttu-id="5bb17-178">Czy masz dostęp do plików instalacyjnych systemu Windows Server, które już zawierają aktualizacje za pomocą iniekcji w trybie offline?</span><span class="sxs-lookup"><span data-stu-id="5bb17-178">Do you have access to Windows Server installation files that already include updates through offline injection?</span></span>|

### <a name="hardware-requirements"></a><span data-ttu-id="5bb17-179">Wymagania sprzętowe</span><span class="sxs-lookup"><span data-stu-id="5bb17-179">Hardware requirements</span></span>

<span data-ttu-id="5bb17-180">Wdrożenia serwera ściągania są obsługiwane na serwerach fizycznych i wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="5bb17-180">Pull server deployments are supported on both physical and virtual servers.</span></span> <span data-ttu-id="5bb17-181">Wymagania w zakresie rozmiaru na serwerze ściągania dostosowanie wymagania dotyczące systemu Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="5bb17-181">The sizing requirements for pull server align with the requirements for Windows Server 2012 R2.</span></span>

<span data-ttu-id="5bb17-182">Procesor: 1.4 GHz 64-bitowy procesor pamięci: 512 MB miejsca na dysku: Sieć 32 GB: Dwie karty Ethernet</span><span class="sxs-lookup"><span data-stu-id="5bb17-182">CPU: 1.4 GHz 64-bit processor Memory: 512 MB Disk Space: 32 GB Network: Gigabit Ethernet Adapter</span></span>

<span data-ttu-id="5bb17-183">Planowanie zadań</span><span class="sxs-lookup"><span data-stu-id="5bb17-183">Planning task</span></span>|
---|
<span data-ttu-id="5bb17-184">Będzie można wdrożyć na sprzęcie fizycznym lub na platformie wirtualizacji?</span><span class="sxs-lookup"><span data-stu-id="5bb17-184">Will you deploy on physical hardware or on a virtualization platform?</span></span>|
<span data-ttu-id="5bb17-185">Co to jest proces, aby zażądać nowego serwera w środowisku docelowym?</span><span class="sxs-lookup"><span data-stu-id="5bb17-185">What is the process to request a new server for your target environment?</span></span>|
<span data-ttu-id="5bb17-186">Co to jest średnia łączny czas serwera staną się dostępne?</span><span class="sxs-lookup"><span data-stu-id="5bb17-186">What is the average turnaround time for a server to become available?</span></span>|
<span data-ttu-id="5bb17-187">Jakiego rozmiaru serwera będzie żądać?</span><span class="sxs-lookup"><span data-stu-id="5bb17-187">What size server will you request?</span></span>|

### <a name="accounts"></a><span data-ttu-id="5bb17-188">Konta</span><span class="sxs-lookup"><span data-stu-id="5bb17-188">Accounts</span></span>

<span data-ttu-id="5bb17-189">Nie istnieją wymagania konta usługi do wdrożenia wystąpienia serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="5bb17-189">There are no service account requirements to deploy a pull server instance.</span></span>
<span data-ttu-id="5bb17-190">Jednak istnieją scenariusze, w której witryny sieci Web może działać w kontekście konta użytkownika lokalnego.</span><span class="sxs-lookup"><span data-stu-id="5bb17-190">However, there are scenarios where the website could run in the context of a local user account.</span></span>
<span data-ttu-id="5bb17-191">Na przykład jeśli istnieje potrzeba dostępu udostępniania magazynu zawartości witryny sieci Web i systemu Windows Server lub urządzenie hostujące udział plików magazynu nie są przyłączone do domeny.</span><span class="sxs-lookup"><span data-stu-id="5bb17-191">For example, if there is a need to access a storage share for website content and either the Windows Server or the device hosting the storage share are not domain joined.</span></span>

### <a name="dns-records"></a><span data-ttu-id="5bb17-192">Rekordy DNS</span><span class="sxs-lookup"><span data-stu-id="5bb17-192">DNS records</span></span>

<span data-ttu-id="5bb17-193">Konieczne będzie nazwę serwera do użycia podczas konfigurowania klientów do pracy ze środowiskiem serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="5bb17-193">You will need a server name to use when configuring clients to work with a pull server environment.</span></span>
<span data-ttu-id="5bb17-194">W środowiskach testowych zazwyczaj jest używana nazwa hosta serwera lub adres IP serwera umożliwia rozpoznawanie nazw DNS nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="5bb17-194">In test environments, typically the server hostname is used, or the IP address for the server can be used if DNS name resolution is not available.</span></span>
<span data-ttu-id="5bb17-195">W środowisku produkcyjnym lub w środowisku laboratoryjnym, która reprezentuje wdrożenia produkcyjnego najlepszym rozwiązaniem jest tworzenie rekordu CNAME systemu DNS.</span><span class="sxs-lookup"><span data-stu-id="5bb17-195">In production environments or in a lab environment that is intended to represent a production deployment, the best practice is to create a DNS CNAME record.</span></span>

<span data-ttu-id="5bb17-196">CNAME systemu DNS umożliwia tworzenie aliasów do odwoływania się do hosta () rekordu.</span><span class="sxs-lookup"><span data-stu-id="5bb17-196">A DNS CNAME allows you to create an alias to refer to your host (A) record.</span></span>
<span data-ttu-id="5bb17-197">Celem rekordu dodatkowych nazw jest zwiększenie elastyczności zmiany należy wymagać w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="5bb17-197">The intent of the additional name record is to increase flexibility should a change be required in the future.</span></span>
<span data-ttu-id="5bb17-198">Rekord CNAME ułatwiają izolowanie konfiguracji klienta, tak aby zmiany w środowisku serwera, takie jak zastąpienie serwera ściągania lub dodawanie ściągnięcia dodatkowych serwerów, nie będzie wymagać odpowiednie zmiany w konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="5bb17-198">A CNAME can help to isolate the client configuration so that changes to the server environment, such as replacing a pull server or adding additional pull servers, will not require a corresponding change to the client configuration.</span></span>

<span data-ttu-id="5bb17-199">Wybierając nazwę rekordu DNS, należy wziąć pod uwagę architektury rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="5bb17-199">When choosing a name for the DNS record, keep the solution architecture in mind.</span></span>
<span data-ttu-id="5bb17-200">Jeśli przy użyciu równoważenia obciążenia, certyfikat używany do zabezpieczenia komunikacji za pośrednictwem protokołu HTTPS należy udostępnić taką samą nazwę jak rekord DNS.</span><span class="sxs-lookup"><span data-stu-id="5bb17-200">If using load balancing, the certificate used to secure traffic over HTTPS will need to share the same name as the DNS record.</span></span>

<span data-ttu-id="5bb17-201">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="5bb17-201">Scenario</span></span> |<span data-ttu-id="5bb17-202">Najlepszym rozwiązaniem jest</span><span class="sxs-lookup"><span data-stu-id="5bb17-202">Best Practice</span></span>
:---|:---
<span data-ttu-id="5bb17-203">Środowisko testowe</span><span class="sxs-lookup"><span data-stu-id="5bb17-203">Test Environment</span></span> |<span data-ttu-id="5bb17-204">Odtwórz środowisko produkcyjne, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="5bb17-204">Reproduce the planned production environment, if possible.</span></span> <span data-ttu-id="5bb17-205">Nazwa hosta serwera jest odpowiednia dla prostych konfiguracje.</span><span class="sxs-lookup"><span data-stu-id="5bb17-205">A server hostname is suitable for simple configurations.</span></span> <span data-ttu-id="5bb17-206">Jeśli serwer DNS nie jest dostępny, mogą służyć adresu IP zamiast nazwy hosta.</span><span class="sxs-lookup"><span data-stu-id="5bb17-206">If DNS is not available, an IP address may be used in lieu of a hostname.</span></span>|
<span data-ttu-id="5bb17-207">Wdrożeniem pojedynczego węzła</span><span class="sxs-lookup"><span data-stu-id="5bb17-207">Single Node Deployment</span></span> |<span data-ttu-id="5bb17-208">Tworzenie rekordu CNAME systemu DNS, który wskazuje na nazwę hosta serwera.</span><span class="sxs-lookup"><span data-stu-id="5bb17-208">Create a DNS CNAME record that points to the server hostname.</span></span>|

<span data-ttu-id="5bb17-209">Aby uzyskać więcej informacji, zobacz [Konfigurowanie okrężnego DNS w systemie Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="5bb17-209">For more information, see [Configuring DNS Round Robin in Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).</span></span>

<span data-ttu-id="5bb17-210">Planowanie zadań</span><span class="sxs-lookup"><span data-stu-id="5bb17-210">Planning task</span></span>|
---|
<span data-ttu-id="5bb17-211">Czy wiesz, kim się skontaktować, aby rekordy DNS tworzonych i zmienianych?</span><span class="sxs-lookup"><span data-stu-id="5bb17-211">Do you know who to contact to have DNS records created and changed?</span></span>|
<span data-ttu-id="5bb17-212">Co to jest średnia przetwarzania żądania dotyczące rekordu DNS?</span><span class="sxs-lookup"><span data-stu-id="5bb17-212">What is the average turnaround for a request for a DNS record?</span></span>|
<span data-ttu-id="5bb17-213">Potrzebujesz żądania rekordów statycznych nazwy hosta (A) dla serwerów?</span><span class="sxs-lookup"><span data-stu-id="5bb17-213">Do you need to request static Hostname (A) records for servers?</span></span>|
<span data-ttu-id="5bb17-214">Co użytkownik zażąda jako rekord CNAME</span><span class="sxs-lookup"><span data-stu-id="5bb17-214">What will you request as a CNAME?</span></span>|
<span data-ttu-id="5bb17-215">Jeśli to konieczne, jakiego rodzaju rozwiązanie do równoważenia obciążenia będzie można wykorzystują?</span><span class="sxs-lookup"><span data-stu-id="5bb17-215">If needed, what type of Load Balancing solution will you utilize?</span></span> <span data-ttu-id="5bb17-216">(zobacz sekcję pod tytułem równoważenia obciążenia, aby uzyskać szczegółowe informacje)</span><span class="sxs-lookup"><span data-stu-id="5bb17-216">(see section titled Load Balancing for details)</span></span>|

### <a name="public-key-infrastructure"></a><span data-ttu-id="5bb17-217">Infrastruktura kluczy publicznych</span><span class="sxs-lookup"><span data-stu-id="5bb17-217">Public Key Infrastructure</span></span>

<span data-ttu-id="5bb17-218">Większość organizacji dzisiejsze wymagają, że ruchu w sieci, szczególnie w przypadku ruchu, który obejmuje takie dane poufne, jak serwery są skonfigurowane, musi zostać zweryfikowane i/lub szyfrowane podczas przesyłania.</span><span class="sxs-lookup"><span data-stu-id="5bb17-218">Most organizations today require that network traffic, especially traffic that includes such sensitive data as how servers are configured, must be validated and/or encrypted during transit.</span></span>
<span data-ttu-id="5bb17-219">Choć jest możliwe do wdrożenia serwera ściągania przy użyciu protokołu HTTP, która ułatwia żądań klientów w zwykły tekst, jest najlepszym rozwiązaniem, aby zabezpieczać ruch przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5bb17-219">While it is possible to deploy a pull server using HTTP which facilitates client requests in clear text, it is a best practice to secure traffic using HTTPS.</span></span> <span data-ttu-id="5bb17-220">Usługę można skonfigurować do używania protokołu HTTPS przy użyciu zestawu parametrów w zasobie DSC **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="5bb17-220">The service can be configured to use HTTPS using a set of parameters in the DSC resource **xPSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="5bb17-221">Wymagania dotyczące certyfikatów do zabezpieczenia ruchu HTTPS na serwerze ściągania nie są inne niż zabezpieczenia inne witryny sieci web protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5bb17-221">The certificate requirements to secure HTTPS traffic for pull server are not different than securing any other HTTPS web site.</span></span> <span data-ttu-id="5bb17-222">**Serwera sieci Web** szablon w usługach certyfikatów systemu Windows Server spełnia wymagane możliwości.</span><span class="sxs-lookup"><span data-stu-id="5bb17-222">The **Web Server** template in a Windows Server Certificate Services satisfies the required capabilities.</span></span>

<span data-ttu-id="5bb17-223">Planowanie zadań</span><span class="sxs-lookup"><span data-stu-id="5bb17-223">Planning task</span></span>|
---|
<span data-ttu-id="5bb17-224">Jeśli żądania certyfikatu nie jest zautomatyzowane, który będzie należy skontaktować się z żądania certyfikatu?</span><span class="sxs-lookup"><span data-stu-id="5bb17-224">If certificate requests are not automated, who will you need to contact to requests a certificate?</span></span>|
<span data-ttu-id="5bb17-225">Co to jest średnia przetwarzania żądania?</span><span class="sxs-lookup"><span data-stu-id="5bb17-225">What is the average turnaround for the request?</span></span>|
<span data-ttu-id="5bb17-226">Jak będzie plik certyfikatu przeniesienia do Ciebie?</span><span class="sxs-lookup"><span data-stu-id="5bb17-226">How will the certificate file be transferred to you?</span></span>|
<span data-ttu-id="5bb17-227">Jak będzie klucz prywatny certyfikatu przeniesienia do Ciebie?</span><span class="sxs-lookup"><span data-stu-id="5bb17-227">How will the certificate private key be transferred to you?</span></span>|
<span data-ttu-id="5bb17-228">Jak długo trwa domyślny czas wygaśnięcia?</span><span class="sxs-lookup"><span data-stu-id="5bb17-228">How long is the default expiration time?</span></span>|
<span data-ttu-id="5bb17-229">Zostały uregulowane na nazwę DNS w środowisku serwera ściągania, używanego do nazwy certyfikatu?</span><span class="sxs-lookup"><span data-stu-id="5bb17-229">Have you settled on a DNS name for the pull server environment, that you can use for the certificate name?</span></span>|

### <a name="choosing-an-architecture"></a><span data-ttu-id="5bb17-230">Wybieranie architekturę</span><span class="sxs-lookup"><span data-stu-id="5bb17-230">Choosing an architecture</span></span>

<span data-ttu-id="5bb17-231">Można wdrożyć serwera ściągania przy użyciu jednej usługi sieci web hostowanych w usługach IIS lub udziału plików SMB.</span><span class="sxs-lookup"><span data-stu-id="5bb17-231">A pull server can be deployed using either a web service hosted on IIS, or an SMB file share.</span></span> <span data-ttu-id="5bb17-232">W większości sytuacji opcja usługi sieci web oferuje większą elastyczność.</span><span class="sxs-lookup"><span data-stu-id="5bb17-232">In most situations, the web service option will provide greater flexibility.</span></span> <span data-ttu-id="5bb17-233">Nie jest niczym niezwykłym ruch HTTPS na przechodzenie przez granice sieci, natomiast ruch SMB często jest filtrowana lub zablokowany między sieciami.</span><span class="sxs-lookup"><span data-stu-id="5bb17-233">It is not uncommon for HTTPS traffic to traverse network boundaries, whereas SMB traffic is often filtered or blocked between networks.</span></span> <span data-ttu-id="5bb17-234">Usługa sieci web oferuje również możliwość dołączenia serwera zgodności lub sieci Web raportowania Menedżera (zarówno tematy które zostaną rozwiązane w przyszłych wersjach tego dokumentu), zapewniają mechanizm dla klientów, aby zgłosić stan ponownie do serwera w celu centralnego wglądu.</span><span class="sxs-lookup"><span data-stu-id="5bb17-234">The web service also offers the option to include a Conformance Server or Web Reporting Manager (both topics to be addressed in a future version of this document) that provide a mechanism for clients to report status back to a server for centralized visibility.</span></span>
<span data-ttu-id="5bb17-235">Protokół SMB zapewnia opcję dla środowiska, w której zasady mówią, serwer sieci web nie powinny być wykorzystywane i inne wymagania środowiska, wchodzące w roli serwera sieci web niepożądane.</span><span class="sxs-lookup"><span data-stu-id="5bb17-235">SMB provides an option for environments where policy dictates that a web server should not be utilized, and for other environmental requirements that make a web server role undesirable.</span></span>
<span data-ttu-id="5bb17-236">W obu przypadkach należy pamiętać ocenić wymagania dotyczące podpisywania i szyfrowania ruchu sieciowego.</span><span class="sxs-lookup"><span data-stu-id="5bb17-236">In either case, remember to evaluate the requirements for signing and encrypting traffic.</span></span> <span data-ttu-id="5bb17-237">Protokół HTTPS, podpisywanie SMB i zasad protokołu IPSEC są wszystkie opcje warte biorąc pod uwagę.</span><span class="sxs-lookup"><span data-stu-id="5bb17-237">HTTPS, SMB signing, and IPSEC policies are all options worth considering.</span></span>

#### <a name="load-balancing"></a><span data-ttu-id="5bb17-238">Równoważenie obciążenia</span><span class="sxs-lookup"><span data-stu-id="5bb17-238">Load balancing</span></span>

<span data-ttu-id="5bb17-239">Klienci, interakcje z usługą sieci web zgłosić wniosek informacji, które są zwracane w pojedynczą odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="5bb17-239">Clients interacting with the web service make a request for information that is returned in a single response.</span></span> <span data-ttu-id="5bb17-240">Żadne kolejne żądania nie są wymagane, więc nie jest konieczne dla platform, aby upewnić się, że sesje są zachowywane na jednym serwerze w dowolnym momencie w czasie równoważenia obciążenia.</span><span class="sxs-lookup"><span data-stu-id="5bb17-240">No sequential requests are required, so it is not necessary for the load balancing platform to ensure sessions are maintained on a single server at any point in time.</span></span>

<span data-ttu-id="5bb17-241">Planowanie zadań</span><span class="sxs-lookup"><span data-stu-id="5bb17-241">Planning task</span></span>|
---|
<span data-ttu-id="5bb17-242">Jakich rozwiązań stosowanych w odniesieniu do Równoważenie obciążenia ruchu między serwerami?</span><span class="sxs-lookup"><span data-stu-id="5bb17-242">What solution will be used for load balancing traffic across servers?</span></span>|
<span data-ttu-id="5bb17-243">Jeśli używasz sprzętowego równoważenia obciążenia, który spowoduje przejście na żądanie, aby dodać nową konfigurację do urządzenia?</span><span class="sxs-lookup"><span data-stu-id="5bb17-243">If using a hardware load balancer, who will take a request to add a new configuration to the device?</span></span>|
<span data-ttu-id="5bb17-244">Co to jest średnia przetwarzania żądania skonfigurować nowe obciążenia zrównoważone usługi sieci web?</span><span class="sxs-lookup"><span data-stu-id="5bb17-244">What is the average turnaround for a request to configure a new load balanced web service?</span></span>|
<span data-ttu-id="5bb17-245">Jakie informacje będą wymagane dla żądania?</span><span class="sxs-lookup"><span data-stu-id="5bb17-245">What information will be required for the request?</span></span>|
<span data-ttu-id="5bb17-246">Będzie trzeba zażądać dodatkowych adresów IP lub będą zespołu odpowiedzialnego za równoważenie obciążenia obsługiwały?</span><span class="sxs-lookup"><span data-stu-id="5bb17-246">Will you need to request an additional IP or will the team responsible for load balancing handle that?</span></span>|
<span data-ttu-id="5bb17-247">Czy masz wymagane rekordy DNS i będzie to wymagane przez zespół odpowiedzialny za konfigurowanie rozwiązania do równoważenia obciążenia?</span><span class="sxs-lookup"><span data-stu-id="5bb17-247">Do you have the DNS records needed, and will this be required by the team responsible for configuring the load balancing solution?</span></span>|
<span data-ttu-id="5bb17-248">To rozwiązanie do równoważenia obciążenia wymaga obsługiwania infrastruktury kluczy publicznych przez urządzenie lub można załadować saldo, które ruch protokołu HTTPS, tak długo, jak nie ma żadnych wymagań sesji?</span><span class="sxs-lookup"><span data-stu-id="5bb17-248">Does the load balancing solution require that PKI be handled by the device or can it load balance HTTPS traffic as long as there are no session requirements?</span></span>|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a><span data-ttu-id="5bb17-249">Tymczasowe konfiguracji i modułów na serwerze ściągania</span><span class="sxs-lookup"><span data-stu-id="5bb17-249">Staging configurations and modules on the pull server</span></span>

<span data-ttu-id="5bb17-250">W ramach planowania konfiguracji należy traktować, o które DSC modułów i konfiguracji będzie obsługiwana przez serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="5bb17-250">As part of configuration planning, you will need to think about which DSC modules and configurations will be hosted by the pull server.</span></span> <span data-ttu-id="5bb17-251">Na potrzeby planowania konfiguracji należy mieć podstawową wiedzę na temat jak przygotować i wdrożyć zawartości na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="5bb17-251">For the purpose of configuration planning it is important to have a basic understanding of how to prepare and deploy content to a pull server.</span></span>

<span data-ttu-id="5bb17-252">W przyszłości w tej sekcji zostaną rozwinięte i zawartych w przewodniku obsługi dla serwera ściągania DSC.</span><span class="sxs-lookup"><span data-stu-id="5bb17-252">In the future, this section will be expanded and included in an Operations Guide for DSC Pull Server.</span></span>  <span data-ttu-id="5bb17-253">Przewodnika przedstawimy proces codziennie zarządzania modułów i konfiguracji wraz z upływem czasu za pomocą usługi automation.</span><span class="sxs-lookup"><span data-stu-id="5bb17-253">The guide will discuss the day to day process for managing modules and configurations over time with automation.</span></span>

#### <a name="dsc-modules"></a><span data-ttu-id="5bb17-254">Moduły DSC</span><span class="sxs-lookup"><span data-stu-id="5bb17-254">DSC modules</span></span>

<span data-ttu-id="5bb17-255">Klientom żądającym konfiguracji należy wymagane moduły DSC.</span><span class="sxs-lookup"><span data-stu-id="5bb17-255">Clients that request a configuration will need the required DSC modules.</span></span> <span data-ttu-id="5bb17-256">Funkcje serwera ściągania jest zautomatyzować dystrybucji na żądanie modułów DSC na klientach.</span><span class="sxs-lookup"><span data-stu-id="5bb17-256">A functionality of the pull server is to automate distribution on demand of DSC modules to clients.</span></span> <span data-ttu-id="5bb17-257">Jeśli serwera ściągania są wdrażane po raz pierwszy, może być jako laboratorium lub weryfikacji koncepcji, prawdopodobnie będą zależeć od modułów DSC, które są dostępne z repozytoriów publicznych, takich jak Galeria programu PowerShell lub repozytoriów PowerShell.org GitHub dla modułów DSC .</span><span class="sxs-lookup"><span data-stu-id="5bb17-257">If you are deploying a pull server for the first time, perhaps as a lab or proof of concept, you are likely going to depend on DSC modules that are available from public repositories such as the PowerShell Gallery or the PowerShell.org GitHub repositories for DSC modules.</span></span>

<span data-ttu-id="5bb17-258">Warto pamiętać, że nawet w przypadku zaufanej online źródeł, takich jak Galeria programu PowerShell, dowolny moduł, który jest pobierany z publicznego repozytorium powinny być zweryfikowane pod przez użytkownika za pomocą środowiska PowerShell i wiedzę na temat środowiska, w której będzie modułów używane przed ich użyciem w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="5bb17-258">It is critical to remember that even for trusted online sources such as the PowerShell Gallery, any module that is downloaded from a public repository should be reviewed by someone with PowerShell experience and knowledge of the environment where the modules will be used prior to being used in production.</span></span> <span data-ttu-id="5bb17-259">Podczas wykonywania tego zadania jest odpowiedni moment, aby sprawdzić wszelkie dodatkowe ładunku w module, który może zostać usunięty, takie jak dokumentacja i przykładowe skrypty.</span><span class="sxs-lookup"><span data-stu-id="5bb17-259">While completing this task it is a good time to check for any additional payload in the module that can be removed such as documentation and example scripts.</span></span> <span data-ttu-id="5bb17-260">Zmniejszy to przepustowość sieci na kliencie w ich pierwsze żądanie, gdy moduły będą pobierane przez sieć z serwera do klienta.</span><span class="sxs-lookup"><span data-stu-id="5bb17-260">This will reduce the network bandwidth per client in their first request, when modules will be downloaded over the network from server to client.</span></span>

<span data-ttu-id="5bb17-261">Każdy moduł musi zostać spakowana w określonym formacie pliku ZIP o nazwie ModuleName_Version.zip, który zawiera ładunek modułu.</span><span class="sxs-lookup"><span data-stu-id="5bb17-261">Each module must be packaged in a specific format, a ZIP file named ModuleName_Version.zip that contains the module payload.</span></span> <span data-ttu-id="5bb17-262">Po plik jest kopiowany do serwera, należy utworzyć plik sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="5bb17-262">After the file is copied to the server a checksum file must be created.</span></span> <span data-ttu-id="5bb17-263">Gdy klienci łączą się z serwerem, sumę kontrolną służy do Sprawdź, czy zawartość modułu DSC nie zmienił się od momentu jego opublikowania.</span><span class="sxs-lookup"><span data-stu-id="5bb17-263">When clients connect to the server, the checksum is used to verify the content of the DSC module has not changed since it was published.</span></span>

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

<span data-ttu-id="5bb17-264">Planowanie zadań</span><span class="sxs-lookup"><span data-stu-id="5bb17-264">Planning task</span></span>|
---|
<span data-ttu-id="5bb17-265">Jeśli jest planowane w środowisku testowym lub laboratorium scenariuszy, do których są kluczem do sprawdzania poprawności?</span><span class="sxs-lookup"><span data-stu-id="5bb17-265">If you are planning a test or lab environment which scenarios are key to validate?</span></span>|
<span data-ttu-id="5bb17-266">Są publicznie dostępne moduły, które zawierają zasoby obejmują wszystkie elementy, których potrzebujesz, czy będziesz tworzyć własne zasoby?</span><span class="sxs-lookup"><span data-stu-id="5bb17-266">Are there publicly available modules that contain resources to cover everything you need or will you need to author your own resources?</span></span>|
<span data-ttu-id="5bb17-267">Środowiska mają dostęp do Internetu na pobranie publicznych modułów?</span><span class="sxs-lookup"><span data-stu-id="5bb17-267">Will your environment have Internet access to retrieve public modules?</span></span>|
<span data-ttu-id="5bb17-268">Kto będzie odpowiedzialny za przegląd moduły DSC?</span><span class="sxs-lookup"><span data-stu-id="5bb17-268">Who will be responsible for reviewing DSC modules?</span></span>|
<span data-ttu-id="5bb17-269">Jeśli planowane jest do środowiska produkcyjnego co będzie używana jako repozytorium lokalne przechowywanie modułów DSC?</span><span class="sxs-lookup"><span data-stu-id="5bb17-269">If you are planning a production environment what will you use as a local repository for storing DSC modules?</span></span>|
<span data-ttu-id="5bb17-270">Centralny zespół zaakceptuje modułów DSC od zespołów aplikacji?</span><span class="sxs-lookup"><span data-stu-id="5bb17-270">Will a central team accept DSC modules from application teams?</span></span> <span data-ttu-id="5bb17-271">Jaka będzie procesu?</span><span class="sxs-lookup"><span data-stu-id="5bb17-271">What will the process be?</span></span>|
<span data-ttu-id="5bb17-272">Będzie automatyzować pakowania, kopiowanie i Tworzenie sumy kontrolnej dla modułów, gotowe do produkcji DSC na serwerze, z repozytorium źródła?</span><span class="sxs-lookup"><span data-stu-id="5bb17-272">Will you automate packaging, copying, and creating a checksum for production-ready DSC modules to the server, from your source repo?</span></span>|
<span data-ttu-id="5bb17-273">Twój zespół będzie odpowiedzialny za zarządzanie także platforma automatyzacji?</span><span class="sxs-lookup"><span data-stu-id="5bb17-273">Will your team be responsible for managing the automation platform as well?</span></span>|

#### <a name="dsc-configurations"></a><span data-ttu-id="5bb17-274">Konfiguracje DSC</span><span class="sxs-lookup"><span data-stu-id="5bb17-274">DSC configurations</span></span>

<span data-ttu-id="5bb17-275">Przeznaczenie serwera ściągania jest zapewnienie mechanizm scentralizowanego dystrybuowania konfiguracji DSC do węzłów klienta.</span><span class="sxs-lookup"><span data-stu-id="5bb17-275">The purpose of a pull server is to provide a centralized mechanism for distributing DSC configurations to client nodes.</span></span> <span data-ttu-id="5bb17-276">Konfiguracje są przechowywane na serwerze jako dokument MOF.</span><span class="sxs-lookup"><span data-stu-id="5bb17-276">The configurations are stored on the server as MOF documents.</span></span>
<span data-ttu-id="5bb17-277">Każdy dokument będą miały nazwę nadaną przy użyciu unikatowego **Guid**.</span><span class="sxs-lookup"><span data-stu-id="5bb17-277">Each document will be named with a unique **Guid**.</span></span> <span data-ttu-id="5bb17-278">Gdy klienci są skonfigurowani do nawiązać połączenie z serwerem ściągania, otrzymuje także **Guid** konfiguracji należy żądają.</span><span class="sxs-lookup"><span data-stu-id="5bb17-278">When clients are configured to connect with a pull server, they are also given the **Guid** for the configuration they should request.</span></span> <span data-ttu-id="5bb17-279">Odwoływanie się do konfiguracji przez ten system **Guid** gwarantuje unikatowość globalnych i jest elastyczne w taki sposób, że można zastosować konfiguracji z dokładnością na węzeł lub jako konfiguracji roli, która obejmuje wiele serwerów, które powinny mieć identycznych konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5bb17-279">This system of referencing configurations by **Guid** guarantees global uniqueness and is flexible such that a configuration can be applied with granularity per node, or as a role configuration that spans many servers that should have identical configurations.</span></span>

#### <a name="guids"></a><span data-ttu-id="5bb17-280">Identyfikatory GUID</span><span class="sxs-lookup"><span data-stu-id="5bb17-280">Guids</span></span>

<span data-ttu-id="5bb17-281">Planowanie konfiguracji **identyfikatorów GUID** warto wymagają dodatkowej uwagi, gdy obsługiwanego przez wdrożenie serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="5bb17-281">Planning for configuration **Guids** is worth additional attention when thinking through a pull server deployment.</span></span> <span data-ttu-id="5bb17-282">Nie ma określonego sposobu obsługi **identyfikatorów GUID** i proces może być unikatowy dla każdego środowiska.</span><span class="sxs-lookup"><span data-stu-id="5bb17-282">There is no specific requirement for how to handle **Guids** and the process is likely to be unique for each environment.</span></span> <span data-ttu-id="5bb17-283">Ten proces może wynosić od prostych po złożone: centralnie przechowywane pliku CSV, prostą tabela SQL, CMDB lub złożone rozwiązania wymagające integracji z innego narzędzia lub oprogramowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="5bb17-283">The process can range from simple to complex: a centrally stored CSV file, a simple SQL table, a CMDB, or a complex solution requiring integration with another tool or software solution.</span></span> <span data-ttu-id="5bb17-284">Dostępne są dwie opcje ogólne:</span><span class="sxs-lookup"><span data-stu-id="5bb17-284">There are two general approaches:</span></span>

- <span data-ttu-id="5bb17-285">**Przypisywanie identyfikatorów GUID na serwer** — jest miarą wiarygodności konfiguracji każdego serwera są sterowane indywidualnie.</span><span class="sxs-lookup"><span data-stu-id="5bb17-285">**Assigning Guids per server** — Provides a measure of assurance that every server configuration is controlled individually.</span></span> <span data-ttu-id="5bb17-286">To zapewnia poziom dokładności wokół aktualizacji i może działać dobrze w środowiskach z kilku serwerów.</span><span class="sxs-lookup"><span data-stu-id="5bb17-286">This provides a level of precision around updates and can work well in environments with few servers.</span></span>
- <span data-ttu-id="5bb17-287">**Przypisywanie identyfikatorów GUID dla roli serwera** — wszystkie serwery, które wykonują tę samą funkcję, takich jak serwery sieci web, użyj tego samego identyfikatora GUID odwołania do wybranych danych wymaganej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5bb17-287">**Assigning Guids per server role** — All servers that perform the same function, such as web servers, use the same GUID to reference the required configuration data.</span></span>  <span data-ttu-id="5bb17-288">Należy pamiętać, że jeśli wiele serwerów mają ten sam identyfikator GUID, wszystkie z nich zostałaby zaktualizowana jednocześnie po zmianie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5bb17-288">Be aware that if many servers share the same GUID, all of them would be updated simultaneously when the configuration changes.</span></span>

  <span data-ttu-id="5bb17-289">Identyfikator GUID jest coś, co powinien być uważany za poufne dane ponieważ może być wykorzystywane przez osobę z wyrządzenia w celu uzyskania informacji na temat sposobu wdrażania i skonfigurowanych w środowisku serwerów.</span><span class="sxs-lookup"><span data-stu-id="5bb17-289">The GUID is something that should be considered sensitive data because it could be leveraged by someone with malicious intent to gain intelligence about how servers are deployed and configured in your environment.</span></span> <span data-ttu-id="5bb17-290">Aby uzyskać więcej informacji, zobacz [bezpiecznie alokacji identyfikatorów GUID w programie PowerShell Desired State Configuration ściągnięcia trybie](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).</span><span class="sxs-lookup"><span data-stu-id="5bb17-290">For more information, see [Securely allocating Guids in PowerShell Desired State Configuration Pull Mode](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).</span></span>

<span data-ttu-id="5bb17-291">Planowanie zadań</span><span class="sxs-lookup"><span data-stu-id="5bb17-291">Planning task</span></span>|
---|
<span data-ttu-id="5bb17-292">Kto będzie odpowiedzialny za kopiowanie do folderu na serwerze ściągania konfiguracji w, gdy są one gotowe?</span><span class="sxs-lookup"><span data-stu-id="5bb17-292">Who will be responsible for copying configurations in to the pull server folder when they are ready?</span></span>|
<span data-ttu-id="5bb17-293">Konfiguracje są tworzone przez zespół aplikacji, co ten proces należy przekazują je?</span><span class="sxs-lookup"><span data-stu-id="5bb17-293">If Configurations are authored by an application team, what will the process be to hand them off?</span></span>|
<span data-ttu-id="5bb17-294">Będzie można wykorzystać repozytorium do przechowywania konfiguracji zgodnie z ich są są tworzone, w zespołach?</span><span class="sxs-lookup"><span data-stu-id="5bb17-294">Will you leverage a repository to store configurations as they are being authored, across teams?</span></span>|
<span data-ttu-id="5bb17-295">Czy zautomatyzujesz proces kopiowania serwer konfiguracji i Tworzenie sumy kontrolnej, gdy są one gotowe?</span><span class="sxs-lookup"><span data-stu-id="5bb17-295">Will you automate the process of copying configurations to the server and creating a checksum when they are ready?</span></span>|
<span data-ttu-id="5bb17-296">Jak będzie mapowania identyfikatorów GUID do serwerów lub ról i gdzie będą to przechowywane?</span><span class="sxs-lookup"><span data-stu-id="5bb17-296">How will you map Guids to servers or roles, and where will this be stored?</span></span>|
<span data-ttu-id="5bb17-297">Co użytkownik użyje jako proces konfigurowania komputerów klienckich i jak będzie ją zintegrować z procesem tworzenia i przechowywania identyfikatorów GUID konfiguracji?</span><span class="sxs-lookup"><span data-stu-id="5bb17-297">What will you use as a process to configure client machines, and how will it integrate with your process for creating and storing Configuration Guids?</span></span>|

## <a name="installation-guide"></a><span data-ttu-id="5bb17-298">Przewodnik instalacji</span><span class="sxs-lookup"><span data-stu-id="5bb17-298">Installation Guide</span></span>

<span data-ttu-id="5bb17-299">*Skrypty podanych w tym dokumencie przedstawiono stabilne. Zawsze skryptów należy uważnie przeczytać przed wykonaniem ich w środowisku produkcyjnym.*</span><span class="sxs-lookup"><span data-stu-id="5bb17-299">*Scripts given in this document are stable examples. Always review scripts carefully before executing them in a production environment.*</span></span>

### <a name="prerequisites"></a><span data-ttu-id="5bb17-300">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="5bb17-300">Prerequisites</span></span>

<span data-ttu-id="5bb17-301">Aby sprawdzić, która wersja programu PowerShell na serwerze, użyj następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="5bb17-301">To verify the version of PowerShell on your server use the following command.</span></span>

```powershell
$PSVersionTable.PSVersion
```

<span data-ttu-id="5bb17-302">Jeśli to możliwe Uaktualnij do najnowszej wersji programu Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="5bb17-302">If possible, upgrade to the latest version of Windows Management Framework.</span></span>
<span data-ttu-id="5bb17-303">Następnie należy pobrać `xPsDesiredStateConfiguration` modułu przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="5bb17-303">Next, download the `xPsDesiredStateConfiguration` module using the following command.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="5bb17-304">Polecenie będzie monitować użytkownika o zgodę przed pobraniem modułu.</span><span class="sxs-lookup"><span data-stu-id="5bb17-304">The command will ask for your approval before downloading the module.</span></span>

### <a name="installation-and-configuration-scripts"></a><span data-ttu-id="5bb17-305">Skrypty instalacji i konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5bb17-305">Installation and configuration scripts</span></span>

<span data-ttu-id="5bb17-306">Najlepszą metodą wdrażania serwera ściągania DSC jest użyć skryptu konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="5bb17-306">The best method to deploy a DSC pull server is to use a DSC configuration script.</span></span> <span data-ttu-id="5bb17-307">W tym dokumencie spowoduje wyświetlenie skryptów, w tym zarówno podstawowe ustawienia, które będzie skonfigurować usługi sieci web DSC i zaawansowanych ustawień skonfigurowanych systemu Windows Server end-to-end tym DSC usługi sieci web.</span><span class="sxs-lookup"><span data-stu-id="5bb17-307">This document will present scripts including both basic settings that would configure only the DSC web service and advanced settings that would configure a Windows Server end-to-end including DSC web service.</span></span>

<span data-ttu-id="5bb17-308">Uwaga:  Obecnie `xPSDesiredStateConfiguation` DSC moduł wymaga serwera, aby był ustawień regionalnych EN-US.</span><span class="sxs-lookup"><span data-stu-id="5bb17-308">Note:  Currently the `xPSDesiredStateConfiguation` DSC module requires the server to be EN-US locale.</span></span>

### <a name="basic-configuration-for-windows-server-2012"></a><span data-ttu-id="5bb17-309">Podstawowa konfiguracja systemu Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="5bb17-309">Basic configuration for Windows Server 2012</span></span>

```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a><span data-ttu-id="5bb17-310">Zaawansowana konfiguracja dla systemu Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="5bb17-310">Advanced configuration for Windows Server 2012 R2</span></span>

```powershell
# This is an advanced Configuration example for Pull Server production deployments on Windows Server 2012 R2.
# Many of the features demonstrated are optional and provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority, complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider modifying the default port, possibly leveraging port 443 in environments where that is enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }

PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```

### <a name="verify-pull-server-functionality"></a><span data-ttu-id="5bb17-311">Sprawdź funkcje serwera ściągania</span><span class="sxs-lookup"><span data-stu-id="5bb17-311">Verify pull server functionality</span></span>

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a><span data-ttu-id="5bb17-312">Konfigurowanie klientów</span><span class="sxs-lookup"><span data-stu-id="5bb17-312">Configure clients</span></span>

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}

PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```

## <a name="additional-references-snippets-and-examples"></a><span data-ttu-id="5bb17-313">Dodatkowe informacje, fragmenty kodu i przykłady</span><span class="sxs-lookup"><span data-stu-id="5bb17-313">Additional references, snippets, and examples</span></span>

<span data-ttu-id="5bb17-314">Ten przykład pokazuje, jak ręcznie zainicjować połączenie klienta (wymaga WMF5) do testowania.</span><span class="sxs-lookup"><span data-stu-id="5bb17-314">This example shows how to manually initiate a client connection (requires WMF5) for testing.</span></span>

```powershell
Update-DscConfiguration –Wait -Verbose
```

<span data-ttu-id="5bb17-315">[DnsServerResourceRecordName Dodaj](http://bit.ly/1G1H31L) polecenie cmdlet służy do dodawania typu rekordu CNAME do strefy DNS.</span><span class="sxs-lookup"><span data-stu-id="5bb17-315">The [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet is used to add a type CNAME record to a DNS zone.</span></span>

<span data-ttu-id="5bb17-316">Funkcja programu PowerShell [utworzyć sumy kontrolnej i opublikować MOF DSC do serwera ściągania SMB](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) automatycznie generuje wymagane sumy kontrolnej, a następnie kopiuje pliki sumy kontrolnej i pliku MOF konfiguracji serwera ściągania SMB.</span><span class="sxs-lookup"><span data-stu-id="5bb17-316">The PowerShell Function to [Create a Checksum and Publish DSC MOF to SMB Pull Server](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) automatically generates the required checksum, and then copies both the MOF configuration and checksum files to the SMB pull server.</span></span>

## <a name="appendix---understanding-odata-service-data-file-types"></a><span data-ttu-id="5bb17-317">Dodatek — opis ODATA typy plików danych usługi</span><span class="sxs-lookup"><span data-stu-id="5bb17-317">Appendix - Understanding ODATA service data file types</span></span>

<span data-ttu-id="5bb17-318">Plik danych są przechowywane do utworzenia informacji podczas wdrażania serwera ściągania, która obejmuje usługę sieci web OData.</span><span class="sxs-lookup"><span data-stu-id="5bb17-318">A data file is stored to create information during deployment of a pull server that includes the OData web service.</span></span> <span data-ttu-id="5bb17-319">Typ pliku jest zależna od systemu operacyjnego, zgodnie z poniższym opisem.</span><span class="sxs-lookup"><span data-stu-id="5bb17-319">The type of file depends on the operating system, as described below.</span></span>

- <span data-ttu-id="5bb17-320">**Windows Server 2012** typ pliku będzie zawsze mdb</span><span class="sxs-lookup"><span data-stu-id="5bb17-320">**Windows Server 2012** The file type will always be   .mdb</span></span>
- <span data-ttu-id="5bb17-321">**Windows Server 2012 R2** typ pliku będą domyślnie .edb, chyba że .mdb jest określona w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5bb17-321">**Windows Server 2012 R2** The file type will default to .edb unless a .mdb is specified in the configuration</span></span>

<span data-ttu-id="5bb17-322">W [zaawansowane przykładowy skrypt](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) instalacji serwera ściągania, można również znaleźć przykład sposobu automatycznie kontrolować ustawienia pliku web.config w celu zapobieżenia każdej okazji błąd spowodowany przez typ pliku.</span><span class="sxs-lookup"><span data-stu-id="5bb17-322">In the [Advanced example script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) for installing a Pull Server, you will also find an example of how to automatically control the web.config file settings to prevent any chance of error caused by file type.</span></span>
