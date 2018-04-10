---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Najlepsze rozwiązania dotyczące serwera ściągania
ms.openlocfilehash: 7de523ad16aee77d87ec4d3334d296997020aa19
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="pull-server-best-practices"></a><span data-ttu-id="ed871-103">Najlepsze rozwiązania dotyczące serwera ściągania</span><span class="sxs-lookup"><span data-stu-id="ed871-103">Pull server best practices</span></span>

><span data-ttu-id="ed871-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ed871-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="ed871-105">Podsumowanie: Ten dokument jest przeznaczony do uwzględnienia procesu i rozszerzalność ułatwiających engineers, którzy są przygotowywanie do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="ed871-105">Summary: This document is intended to include process and extensibility to assist engineers who are preparing for the solution.</span></span> <span data-ttu-id="ed871-106">Szczegóły powinny udostępnienie najlepszych rozwiązań, określonych przez klientów i następnie zweryfikowany przez zespół pracujący nad produktem zalecenia są skierowane do przyszłych i uznawane za stabilną.</span><span class="sxs-lookup"><span data-stu-id="ed871-106">Details should provide best practices as identified by customers and then validated by the product team to ensure recommendations are future facing and considered stable.</span></span>

| |<span data-ttu-id="ed871-107">Informacje o dokumencie</span><span class="sxs-lookup"><span data-stu-id="ed871-107">Doc Info</span></span>|
|:---|:---|
<span data-ttu-id="ed871-108">Autor</span><span class="sxs-lookup"><span data-stu-id="ed871-108">Author</span></span> | <span data-ttu-id="ed871-109">Jan Greene</span><span class="sxs-lookup"><span data-stu-id="ed871-109">Michael Greene</span></span>
<span data-ttu-id="ed871-110">Recenzenci</span><span class="sxs-lookup"><span data-stu-id="ed871-110">Reviewers</span></span> | <span data-ttu-id="ed871-111">Ben Gelens, Ravikanth Chaganti Aleksandar Nikolic</span><span class="sxs-lookup"><span data-stu-id="ed871-111">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span></span>
<span data-ttu-id="ed871-112">Opublikowane</span><span class="sxs-lookup"><span data-stu-id="ed871-112">Published</span></span> | <span data-ttu-id="ed871-113">Kwietnia 2015 r.</span><span class="sxs-lookup"><span data-stu-id="ed871-113">April, 2015</span></span>

## <a name="abstract"></a><span data-ttu-id="ed871-114">Abstrakcyjny</span><span class="sxs-lookup"><span data-stu-id="ed871-114">Abstract</span></span>

<span data-ttu-id="ed871-115">Celem niniejszego dokumentu jest oficjalnego wytyczne dla każdego Planowanie wdrożenia serwera ściągania konfiguracji żądanego stanu programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ed871-115">This document is designed to provide official guidance for anyone planning for a Windows PowerShell Desired State Configuration pull server implementation.</span></span> <span data-ttu-id="ed871-116">Serwerem ściągania jest proste usługi, które powinien wykonać tylko minut do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="ed871-116">A pull server is a simple service that should take only minutes to deploy.</span></span> <span data-ttu-id="ed871-117">Mimo że ten dokument zostanie oferują techniczne porad wskazówki, które mogą być używane w ramach wdrożenia, wartość tego dokumentu jest jako punkt odniesienia dla najlepszych rozwiązań i co można traktować przed wdrożeniem.</span><span class="sxs-lookup"><span data-stu-id="ed871-117">Although this document will offer technical how-to guidance that can be used in a deployment, the value of this document is as a reference for best practices and what to think about before deploying.</span></span>
<span data-ttu-id="ed871-118">Czytniki powinny mieć podstawowe znajomość DSC i terminów używanych do opisywania składników, które są zawarte w wdrożenia usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="ed871-118">Readers should have basic familiarity with DSC, and the terms used to describe the components that are included in a DSC deployment.</span></span> <span data-ttu-id="ed871-119">Aby uzyskać więcej informacji, zobacz [żądany stan konfiguracji Omówienie środowiska Windows PowerShell](https://technet.microsoft.com/library/dn249912.aspx) tematu.</span><span class="sxs-lookup"><span data-stu-id="ed871-119">For more information, see the [Windows PowerShell Desired State Configuration Overview](https://technet.microsoft.com/library/dn249912.aspx)  topic.</span></span>
<span data-ttu-id="ed871-120">Oczekiwaniami DSC podlegać ewolucji w chmurze okresach podstawową technologią, łącznie z serwera ściągania również oczekuje rozwijać i wprowadzenie nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="ed871-120">As DSC is expected to evolve at cloud cadence, the underlying technology including pull server is also expected to evolve and to introduce new capabilities.</span></span> <span data-ttu-id="ed871-121">Ten dokument zawiera tabelę wersji w dodatku, który zawiera odwołania do poprzednich wersji i odwołania do przyszłych wyglądającej rozwiązania zachęca nowoczesne projektów.</span><span class="sxs-lookup"><span data-stu-id="ed871-121">This document includes a version table in the appendix that provides references to previous releases and references to future looking solutions to encourage forward-looking designs.</span></span>

<span data-ttu-id="ed871-122">Dwóch głównych sekcji tego dokumentu:</span><span class="sxs-lookup"><span data-stu-id="ed871-122">The two major sections of this document:</span></span>

 - <span data-ttu-id="ed871-123">Planowanie konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ed871-123">Configuration Planning</span></span>
 - <span data-ttu-id="ed871-124">Przewodnik instalacji</span><span class="sxs-lookup"><span data-stu-id="ed871-124">Installation Guide</span></span>

### <a name="versions-of-the-windows-management-framework"></a><span data-ttu-id="ed871-125">Wersje systemu Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="ed871-125">Versions of the Windows Management Framework</span></span>
<span data-ttu-id="ed871-126">Informacje w tym dokumencie mają na celu dotyczą Windows Management Framework 5.0.</span><span class="sxs-lookup"><span data-stu-id="ed871-126">The information in this document is intended to apply to Windows Management Framework 5.0.</span></span> <span data-ttu-id="ed871-127">WMF 5.0 nie jest wymagany do wdrażania i obsługi serwera ściągania, w wersji 5.0 jest celem tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ed871-127">While WMF 5.0 is not required for deploying and operating a pull server, version 5.0 is the focus of this document.</span></span>

### <a name="windows-powershell-desired-state-configuration"></a><span data-ttu-id="ed871-128">Środowisko Windows PowerShell Konfiguracja żądanego stanu</span><span class="sxs-lookup"><span data-stu-id="ed871-128">Windows PowerShell Desired State Configuration</span></span>
<span data-ttu-id="ed871-129">Żądana Konfiguracja stanu (DSC) to platforma zarządzania, która umożliwia wdrażanie i zarządzanie nimi danych konfiguracji przy użyciu składni branży o nazwie Managed Object Format (MOF) do opisywania modelu informacji wspólnych (CIM).</span><span class="sxs-lookup"><span data-stu-id="ed871-129">Desired State Configuration (DSC) is a management platform that enables deploying and managing configuration data by using an industry syntax named the Managed Object Format (MOF) to describe the Common Information Model (CIM).</span></span> <span data-ttu-id="ed871-130">Istnieje projekt typu open source, Open Management Infrastructure (OMI), do dalszego programowanie z tymi standardami różnych platform, łącznie z systemem Linux i sieciowe systemy operacyjne sprzętu.</span><span class="sxs-lookup"><span data-stu-id="ed871-130">An open source project, Open Management Infrastructure (OMI), exists to further development of these standards across platforms including Linux and network hardware operating systems.</span></span> <span data-ttu-id="ed871-131">Aby uzyskać więcej informacji, zobacz [strony DMTF łączenia ze specyfikacjami MOF](http://dmtf.org/standards/cim), i [OMI dokumentów i źródła](https://collaboration.opengroup.org/omi/documents.php).</span><span class="sxs-lookup"><span data-stu-id="ed871-131">For more information, see the [DMTF page linking to MOF specifications](http://dmtf.org/standards/cim), and [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php).</span></span>

<span data-ttu-id="ed871-132">Programu Windows PowerShell udostępnia zestaw rozszerzeń języka żądany stan konfiguracji, który służy do tworzenia i zarządzania nimi deklaratywne konfiguracjach.</span><span class="sxs-lookup"><span data-stu-id="ed871-132">Windows PowerShell provides a set of language extensions for Desired State Configuration that you can use to create and manage declarative configurations.</span></span>

### <a name="pull-server-role"></a><span data-ttu-id="ed871-133">Rola serwera ściągania</span><span class="sxs-lookup"><span data-stu-id="ed871-133">Pull server role</span></span>
<span data-ttu-id="ed871-134">Serwer ściągania zapewnia scentralizowane usługi do przechowywania konfiguracji, które będą dostępne dla węzły docelowe.</span><span class="sxs-lookup"><span data-stu-id="ed871-134">A pull server provides a centralized service to store configurations that will be accessible to target nodes.</span></span>

<span data-ttu-id="ed871-135">Rola serwera ściągania może być wdrożony jako wystąpienie serwera sieci Web lub udziału plików SMB.</span><span class="sxs-lookup"><span data-stu-id="ed871-135">The pull server role can be deployed as either a Web Server instance or an SMB file share.</span></span> <span data-ttu-id="ed871-136">Funkcja serwer sieci web zawiera interfejs OData i opcjonalnie możliwości węzły docelowe wysyłać raporty potwierdzenie powodzenie lub niepowodzenie zgodnie z konfiguracji są stosowane.</span><span class="sxs-lookup"><span data-stu-id="ed871-136">The web server capability includes an OData interface and can optionally include capabilities for target nodes to report back confirmation of success or failure as configurations are applied.</span></span> <span data-ttu-id="ed871-137">Ta funkcja jest przydatna w środowiskach, w których istnieje wiele węzłów docelowych.</span><span class="sxs-lookup"><span data-stu-id="ed871-137">This functionality is useful in environments where there are a large number of target nodes.</span></span>
<span data-ttu-id="ed871-138">Po skonfigurowaniu węzła docelowego (zwaną także klienta), aby wskazywały serwer ściągnięcia z najnowszą konfiguracją danych i wszystkie wymagane skrypty, zostały pobrane i zastosowane.</span><span class="sxs-lookup"><span data-stu-id="ed871-138">After configuring a target node (also referred to as a client) to point to the pull server the latest configuration data and any required scripts are downloaded and applied.</span></span> <span data-ttu-id="ed871-139">Może to nastąpić jako jednorazowego wdrażania lub ponownie występującą zadania, które powoduje z serwerem ściągania istotny element zarządzania zmiany na dużą skalę.</span><span class="sxs-lookup"><span data-stu-id="ed871-139">This can happen as a one-time deployment or as a re-occurring job which also makes the pull server an important asset for managing change at scale.</span></span> <span data-ttu-id="ed871-140">Aby uzyskać więcej informacji, zobacz [Windows PowerShell żądanego stanu ściągnięcia serwery konfiguracji](https://technet.microsoft.com/library/dn249913.aspx) i [wypychania i ściągania trybów konfiguracji](https://technet.microsoft.com/library/dn249913.aspx).</span><span class="sxs-lookup"><span data-stu-id="ed871-140">For more information, see [Windows PowerShell Desired State Configuration Pull Servers](https://technet.microsoft.com/library/dn249913.aspx) and [Push and Pull Configuration Modes](https://technet.microsoft.com/library/dn249913.aspx).</span></span>

## <a name="configuration-planning"></a><span data-ttu-id="ed871-141">Planowanie konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ed871-141">Configuration planning</span></span>

<span data-ttu-id="ed871-142">Wszystkie wdrożenia oprogramowania przedsiębiorstwa jest informacje, które mogą być zbierane z wyprzedzeniem pomóc w planowaniu architektury i przygotowywane dla czynności wymagane do ukończenia wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="ed871-142">For any enterprise software deployment there is information that can be collected in advance to help plan for the correct architecture and to be prepared for the steps required to complete the deployment.</span></span> <span data-ttu-id="ed871-143">Poniższe sekcje zawierają informacje dotyczące sposobu przygotowania i organizacyjne połączeń, które prawdopodobnie będą musieli się zdarzyć z wyprzedzeniem.</span><span class="sxs-lookup"><span data-stu-id="ed871-143">The following sections provide information regarding how to prepare and the organizational connections that will likely need to happen in advance.</span></span>

### <a name="software-requirements"></a><span data-ttu-id="ed871-144">Wymagania dotyczące oprogramowania</span><span class="sxs-lookup"><span data-stu-id="ed871-144">Software requirements</span></span>

<span data-ttu-id="ed871-145">Wdrożenie serwera ściągania wymaga funkcji DSC usługi systemu Windows Server.</span><span class="sxs-lookup"><span data-stu-id="ed871-145">Deployment of a pull server requires the DSC Service feature of Windows Server.</span></span> <span data-ttu-id="ed871-146">Ta funkcja została wprowadzona w systemie Windows Server 2012 i został zaktualizowany przy użyciu bieżących wersjach systemu Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="ed871-146">This feature was introduced in Windows Server 2012, and has been updated through ongoing releases of Windows Management Framework (WMF).</span></span>

### <a name="software-downloads"></a><span data-ttu-id="ed871-147">Pobieranie oprogramowania</span><span class="sxs-lookup"><span data-stu-id="ed871-147">Software downloads</span></span>

<span data-ttu-id="ed871-148">Oprócz instalowania najnowszej zawartości z usługi Windows Update, istnieją dwa pliki do pobrania, które są traktowane jako najlepsze rozwiązanie do wdrożenia serwera ściągania usługi Konfiguracja DSC: najnowszą wersję programu Windows Management Framework i moduł DSC w celu zautomatyzowania serwera ściągania inicjowania obsługi administracyjnej.</span><span class="sxs-lookup"><span data-stu-id="ed871-148">In addition to installing the latest content from Windows Update, there are two downloads considered best practice to deploy a DSC pull server: The latest version of Windows Management Framework, and a DSC module to automate pull server provisioning.</span></span>

### <a name="wmf"></a><span data-ttu-id="ed871-149">WMF</span><span class="sxs-lookup"><span data-stu-id="ed871-149">WMF</span></span>

<span data-ttu-id="ed871-150">Windows Server 2012 R2 zawiera funkcję o nazwie usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="ed871-150">Windows Server 2012 R2 includes a feature named the DSC Service.</span></span> <span data-ttu-id="ed871-151">Funkcja usługi Konfiguracja DSC zapewnia funkcje serwera ściągania, w tym pliki binarne, które obsługują punktu końcowego OData.</span><span class="sxs-lookup"><span data-stu-id="ed871-151">The DSC Service feature provides the pull server functionality, including the binaries that support the OData endpoint.</span></span>
<span data-ttu-id="ed871-152">WMF znajduje się w systemie Windows Server i jest aktualizowane na elastyczne okresach między wersjami systemu Windows Server.</span><span class="sxs-lookup"><span data-stu-id="ed871-152">WMF is included in Windows Server and is updated on an agile cadence between Windows Server releases.</span></span> <span data-ttu-id="ed871-153">[Nowe wersje WMF 5.0](http://aka.ms/wmf5latest) mogą obejmować aktualizacje do funkcji usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="ed871-153">[New versions of WMF 5.0](http://aka.ms/wmf5latest)  can include updates to the DSC Service feature.</span></span> <span data-ttu-id="ed871-154">Z tego powodu najlepszym rozwiązaniem jest Pobierz najnowszą wersję platformy WMF oraz do kontroli wersji, aby określić, czy wersja zawiera aktualizację do funkcji usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="ed871-154">For this reason, it is a best practice to download the latest release of WMF and to review the release notes to determine if the release includes an update to the DSC service feature.</span></span> <span data-ttu-id="ed871-155">Należy także przejrzeć sekcję w informacjach o wersji wskazuje, czy stan projektowania dla aktualizacji lub scenariusza jest wymienione jako trwała lub eksperymentalne.</span><span class="sxs-lookup"><span data-stu-id="ed871-155">You should also review the section of the release notes that indicates whether the design status for an update or scenario is listed as stable or experimental.</span></span>
<span data-ttu-id="ed871-156">Aby umożliwić cyklu zlecenia zwinnego poszczególne funkcje mogą być deklarowane stabilny, co oznacza funkcję jest gotowa do użycia w środowisku produkcyjnym, nawet wtedy, gdy WMF wprowadzone w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="ed871-156">To allow for an agile release cycle, individual features can be declared stable, which indicates the feature is ready to be used in a production environment even while WMF is released in preview.</span></span>
<span data-ttu-id="ed871-157">Inne funkcje, które wcześniej zostały zaktualizowane przez wersje WMF (zobacz dalsze szczegółowe informacje o wersji platformy WMF):</span><span class="sxs-lookup"><span data-stu-id="ed871-157">Other features that have historically been updated by WMF releases (see the WMF Release Notes for further detail):</span></span>

 - <span data-ttu-id="ed871-158">Windows PowerShell, Windows PowerShell zintegrowane skryptów</span><span class="sxs-lookup"><span data-stu-id="ed871-158">Windows PowerShell Windows PowerShell Integrated Scripting</span></span>
 - <span data-ttu-id="ed871-159">(Zarządzanie OData usługi sieci Web (ISE) środowiska Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ed871-159">Environment (ISE) Windows PowerShell Web Services (Management OData</span></span>
 - <span data-ttu-id="ed871-160">Rozszerzenie usług IIS) systemu Windows PowerShell Konfiguracja żądanego stanu (DSC)</span><span class="sxs-lookup"><span data-stu-id="ed871-160">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span></span>
 - <span data-ttu-id="ed871-161">Windows Remote Management (WinRM) Instrumentacji zarządzania Windows (WMI)</span><span class="sxs-lookup"><span data-stu-id="ed871-161">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span></span>

### <a name="dsc-resource"></a><span data-ttu-id="ed871-162">Zasób DSC</span><span class="sxs-lookup"><span data-stu-id="ed871-162">DSC resource</span></span>

<span data-ttu-id="ed871-163">Wdrożenie serwera ściągania można uprościć przez usługi za pomocą skryptu konfiguracji DSC inicjowania obsługi administracyjnej.</span><span class="sxs-lookup"><span data-stu-id="ed871-163">A pull server deployment can be simplified by provisioning the service using a DSC configuration script.</span></span> <span data-ttu-id="ed871-164">Ten dokument zawiera skrypty do konfiguracji, które mogą być używane do wdrażania węźle gotowy serwerów produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="ed871-164">This document includes configuration scripts that can be used to deploy a production ready server node.</span></span> <span data-ttu-id="ed871-165">Aby użyć skryptów konfiguracyjnych, moduł DSC jest wymagane oznacza to nie jest uwzględniony w systemie Windows Server.</span><span class="sxs-lookup"><span data-stu-id="ed871-165">To use the configuration scripts, a DSC module is required that is not included in Windows Server.</span></span> <span data-ttu-id="ed871-166">Nazwa modułu wymagane jest **xPSDesiredStateConfiguration**, która obejmuje zasobów DSC **xDscWebService**.</span><span class="sxs-lookup"><span data-stu-id="ed871-166">The required module name is **xPSDesiredStateConfiguration**, which includes the DSC resource **xDscWebService**.</span></span> <span data-ttu-id="ed871-167">Moduł xPSDesiredStateConfiguration można pobrać [tutaj](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span><span class="sxs-lookup"><span data-stu-id="ed871-167">The xPSDesiredStateConfiguration module can be downloaded [here](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span></span>

<span data-ttu-id="ed871-168">Użyj **instalacji modułu** polecenia cmdlet z **PowerShellGet** modułu.</span><span class="sxs-lookup"><span data-stu-id="ed871-168">Use the **Install-Module** cmdlet from the **PowerShellGet** module.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="ed871-169">**PowerShellGet** moduł pobierze modułu do:</span><span class="sxs-lookup"><span data-stu-id="ed871-169">The **PowerShellGet** module will download the module to:</span></span>

`C:\Program Files\Windows PowerShell\Modules`

<span data-ttu-id="ed871-170">Planowanie zadań</span><span class="sxs-lookup"><span data-stu-id="ed871-170">Planning task</span></span>|
---|
<span data-ttu-id="ed871-171">Czy masz dostęp do plików instalacji systemu Windows Server 2012 R2?</span><span class="sxs-lookup"><span data-stu-id="ed871-171">Do you have access to the installation files for Windows Server 2012 R2?</span></span>|
<span data-ttu-id="ed871-172">Środowisko wdrażania będą miały dostęp do Internetu, aby pobrać WMF i modułu z galerii online?</span><span class="sxs-lookup"><span data-stu-id="ed871-172">Will the deployment environment have Internet access to download WMF and the module from the online gallery?</span></span>|
<span data-ttu-id="ed871-173">Jak należy zainstalować najnowsze aktualizacje zabezpieczeń po zainstalowaniu systemu operacyjnego?</span><span class="sxs-lookup"><span data-stu-id="ed871-173">How will you install the latest security updates after installing the operating system?</span></span>|
<span data-ttu-id="ed871-174">Środowisko mają dostęp do Internetu w celu uzyskania aktualizacji lub ma lokalnego serwera Windows Server Update Services (WSUS)?</span><span class="sxs-lookup"><span data-stu-id="ed871-174">Will the environment have Internet access to obtain updates, or will it have a local Windows Server Update Services (WSUS) server?</span></span>|
<span data-ttu-id="ed871-175">Czy masz dostęp do plików instalacji systemu Windows Server, które już zawierają aktualizacje za pomocą iniekcji w trybie offline?</span><span class="sxs-lookup"><span data-stu-id="ed871-175">Do you have access to Windows Server installation files that already include updates through offline injection?</span></span>|

### <a name="hardware-requirements"></a><span data-ttu-id="ed871-176">Wymagania sprzętowe</span><span class="sxs-lookup"><span data-stu-id="ed871-176">Hardware requirements</span></span>

<span data-ttu-id="ed871-177">Wdrożeń na serwerze ściągania są obsługiwane na serwerach fizycznych i wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="ed871-177">Pull server deployments are supported on both physical and virtual servers.</span></span> <span data-ttu-id="ed871-178">Dostosowanie rozmiaru wymagania dotyczące serwera ściągania wymagania dotyczące systemu Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="ed871-178">The sizing requirements for pull server align with the requirements for Windows Server 2012 R2.</span></span>

<span data-ttu-id="ed871-179">Procesor: 1,4 GHz 64-bitowy procesor pamięci: 512 MB miejsca na dysku: 32 GB sieci: kartę Ethernet Gigabit Ethernet</span><span class="sxs-lookup"><span data-stu-id="ed871-179">CPU: 1.4 GHz 64-bit processor Memory: 512 MB Disk Space: 32 GB Network: Gigabit Ethernet Adapter</span></span>

<span data-ttu-id="ed871-180">Planowanie zadań</span><span class="sxs-lookup"><span data-stu-id="ed871-180">Planning task</span></span>|
---|
<span data-ttu-id="ed871-181">Będzie można wdrożyć na sprzęcie fizycznym lub na platformie wirtualizacji?</span><span class="sxs-lookup"><span data-stu-id="ed871-181">Will you deploy on physical hardware or on a virtualization platform?</span></span>|
<span data-ttu-id="ed871-182">Co to jest proces, aby zażądać nowego serwera dla środowiska docelowego?</span><span class="sxs-lookup"><span data-stu-id="ed871-182">What is the process to request a new server for your target environment?</span></span>|
<span data-ttu-id="ed871-183">Co to jest średnią łączny czas serwer stanie się dostępne?</span><span class="sxs-lookup"><span data-stu-id="ed871-183">What is the average turnaround time for a server to become available?</span></span>|
<span data-ttu-id="ed871-184">Jakie serwera rozmiar będzie żądać?</span><span class="sxs-lookup"><span data-stu-id="ed871-184">What size server will you request?</span></span>|

### <a name="accounts"></a><span data-ttu-id="ed871-185">Konta</span><span class="sxs-lookup"><span data-stu-id="ed871-185">Accounts</span></span>

<span data-ttu-id="ed871-186">Nie istnieją wymagania konta usługi do wdrożenia wystąpienie serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="ed871-186">There are no service account requirements to deploy a pull server instance.</span></span>
<span data-ttu-id="ed871-187">Istnieją jednak scenariuszy, w którym można uruchomić witryny sieci Web w kontekście konta użytkownika lokalnego.</span><span class="sxs-lookup"><span data-stu-id="ed871-187">However, there are scenarios where the website could run in the context of a local user account.</span></span>
<span data-ttu-id="ed871-188">Na przykład jeśli istnieje potrzeba do dostępu do udziału magazynu dla zawartości witryny sieci Web i serwera systemu Windows lub urządzenia obsługującego udziału magazynu nie są przyłączone do domeny.</span><span class="sxs-lookup"><span data-stu-id="ed871-188">For example, if there is a need to access a storage share for website content and either the Windows Server or the device hosting the storage share are not domain joined.</span></span>

### <a name="dns-records"></a><span data-ttu-id="ed871-189">Rekordy DNS</span><span class="sxs-lookup"><span data-stu-id="ed871-189">DNS records</span></span>

<span data-ttu-id="ed871-190">Konieczne będzie nazwę serwera do użycia podczas konfigurowania klientów do pracy z środowisku serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="ed871-190">You will need a server name to use when configuring clients to work with a pull server environment.</span></span>
<span data-ttu-id="ed871-191">W środowisku testowym zazwyczaj jest używana nazwa hosta serwera lub adres IP serwera mogą być używane, gdy rozpoznawania nazw DNS jest niedostępna.</span><span class="sxs-lookup"><span data-stu-id="ed871-191">In test environments, typically the server hostname is used, or the IP address for the server can be used if DNS name resolution is not available.</span></span>
<span data-ttu-id="ed871-192">W środowisku produkcyjnym lub w środowisku laboratoryjnym, który reprezentuje wdrożenia produkcyjnego najlepszym rozwiązaniem jest utworzenie rekordu CNAME systemu DNS.</span><span class="sxs-lookup"><span data-stu-id="ed871-192">In production environments or in a lab environment that is intended to represent a production deployment, the best practice is to create a DNS CNAME record.</span></span>

<span data-ttu-id="ed871-193">Rekordu CNAME systemu DNS umożliwia tworzenie aliasów do odwoływania się do hosta () rekordu.</span><span class="sxs-lookup"><span data-stu-id="ed871-193">A DNS CNAME allows you to create an alias to refer to your host (A) record.</span></span>
<span data-ttu-id="ed871-194">Celem rekordu dodatkowe nazwy jest większą elastyczność zmiany należy wymagać w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="ed871-194">The intent of the additional name record is to increase flexibility should a change be required in the future.</span></span>
<span data-ttu-id="ed871-195">Rekord CNAME może pomóc izolowania konfiguracji klienta, tak aby zmian w środowisku serwera, takie jak zastępowania serwera ściągania lub dodawanie ściągania dodatkowych serwerów, nie będzie wymagać odpowiednie zmiany w konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="ed871-195">A CNAME can help to isolate the client configuration so that changes to the server environment, such as replacing a pull server or adding additional pull servers, will not require a corresponding change to the client configuration.</span></span>

<span data-ttu-id="ed871-196">Przy wyborze nazwy rekordu DNS należy pamiętać o architektury rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="ed871-196">When choosing a name for the DNS record, keep the solution architecture in mind.</span></span>
<span data-ttu-id="ed871-197">Jeśli przy użyciu równoważenia obciążenia, certyfikat używany do zabezpieczania ruchu za pośrednictwem protokołu HTTPS należy do tej samej nazwie jako rekord DNS.</span><span class="sxs-lookup"><span data-stu-id="ed871-197">If using load balancing, the certificate used to secure traffic over HTTPS will need to share the same name as the DNS record.</span></span>

<span data-ttu-id="ed871-198">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="ed871-198">Scenario</span></span> |<span data-ttu-id="ed871-199">Najlepsze praktyki</span><span class="sxs-lookup"><span data-stu-id="ed871-199">Best Practice</span></span>
:---|:---
<span data-ttu-id="ed871-200">Środowisko testowe</span><span class="sxs-lookup"><span data-stu-id="ed871-200">Test Environment</span></span> |<span data-ttu-id="ed871-201">Odtwórz środowisko produkcyjne, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="ed871-201">Reproduce the planned production environment, if possible.</span></span> <span data-ttu-id="ed871-202">Nazwa hosta serwera jest odpowiednia dla prostego konfiguracje.</span><span class="sxs-lookup"><span data-stu-id="ed871-202">A server hostname is suitable for simple configurations.</span></span> <span data-ttu-id="ed871-203">Jeśli usługa DNS nie jest dostępna, można użyć adresu IP zamiast nazwy hosta.</span><span class="sxs-lookup"><span data-stu-id="ed871-203">If DNS is not available, an IP address may be used in lieu of a hostname.</span></span>|
<span data-ttu-id="ed871-204">Wdrażanie jednego węzła</span><span class="sxs-lookup"><span data-stu-id="ed871-204">Single Node Deployment</span></span> |<span data-ttu-id="ed871-205">Tworzenie rekordu CNAME systemu DNS, który wskazuje nazwę hosta serwera.</span><span class="sxs-lookup"><span data-stu-id="ed871-205">Create a DNS CNAME record that points to the server hostname.</span></span>|

<span data-ttu-id="ed871-206">Aby uzyskać więcej informacji, zobacz [Konfigurowanie okrężnego DNS w systemie Windows Server](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="ed871-206">For more information, see [Configuring DNS Round Robin in Windows Server](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx).</span></span>

<span data-ttu-id="ed871-207">Planowanie zadań</span><span class="sxs-lookup"><span data-stu-id="ed871-207">Planning task</span></span>|
---|
<span data-ttu-id="ed871-208">Czy wiesz, który można skontaktować się z mają rekordy DNS tworzonych i zmienianych?</span><span class="sxs-lookup"><span data-stu-id="ed871-208">Do you know who to contact to have DNS records created and changed?</span></span>|
<span data-ttu-id="ed871-209">Co to jest średnią przetwarzania żądania dotyczące rekordu DNS?</span><span class="sxs-lookup"><span data-stu-id="ed871-209">What is the average turnaround for a request for a DNS record?</span></span>|
<span data-ttu-id="ed871-210">Czy trzeba żądania rekordów statycznych nazwy hosta (A) dla serwerów?</span><span class="sxs-lookup"><span data-stu-id="ed871-210">Do you need to request static Hostname (A) records for servers?</span></span>|
<span data-ttu-id="ed871-211">Co użytkownik zażąda jako rekord CNAME</span><span class="sxs-lookup"><span data-stu-id="ed871-211">What will you request as a CNAME?</span></span>|
<span data-ttu-id="ed871-212">Jeśli to konieczne, jakiego typu rozwiązania do równoważenia obciążenia można korzystają?</span><span class="sxs-lookup"><span data-stu-id="ed871-212">If needed, what type of Load Balancing solution will you utilize?</span></span> <span data-ttu-id="ed871-213">(patrz sekcja zatytułowany równoważenia obciążenia, aby uzyskać szczegółowe informacje)</span><span class="sxs-lookup"><span data-stu-id="ed871-213">(see section titled Load Balancing for details)</span></span>|

### <a name="public-key-infrastructure"></a><span data-ttu-id="ed871-214">Infrastruktura kluczy publicznych</span><span class="sxs-lookup"><span data-stu-id="ed871-214">Public Key Infrastructure</span></span>

<span data-ttu-id="ed871-215">Większość organizacji dzisiaj wymagają czy ruch sieciowy, szczególnie w przypadku ruchu, który obejmuje takie dane poufne, jak serwery są skonfigurowane, musi być weryfikowane i/lub szyfrowane podczas przesyłania.</span><span class="sxs-lookup"><span data-stu-id="ed871-215">Most organizations today require that network traffic, especially traffic that includes such sensitive data as how servers are configured, must be validated and/or encrypted during transit.</span></span>
<span data-ttu-id="ed871-216">Mimo że jest możliwa do wdrożenia serwera ściągania przy użyciu protokołu HTTP, która ułatwia żądań klientów w zwykły tekst, jest najlepszym rozwiązaniem jest bezpieczny ruch przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ed871-216">While it is possible to deploy a pull server using HTTP which facilitates client requests in clear text, it is a best practice to secure traffic using HTTPS.</span></span> <span data-ttu-id="ed871-217">Usługę można skonfigurować do używania protokołu HTTPS przy użyciu zestawu parametrów w zasobie DSC **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="ed871-217">The service can be configured to use HTTPS using a set of parameters in the DSC resource **xPSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="ed871-218">Wymagania dotyczące certyfikatów w celu zabezpieczania ruchu HTTPS na serwerze ściągania nie są inne niż zabezpieczenia inne witryny sieci web HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ed871-218">The certificate requirements to secure HTTPS traffic for pull server are not different than securing any other HTTPS web site.</span></span> <span data-ttu-id="ed871-219">**Serwera sieci Web** możliwości wymagane spełniający szablon usług certyfikatów serwera systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ed871-219">The **Web Server** template in a Windows Server Certificate Services satisfies the required capabilities.</span></span>

<span data-ttu-id="ed871-220">Planowanie zadań</span><span class="sxs-lookup"><span data-stu-id="ed871-220">Planning task</span></span>|
---|
<span data-ttu-id="ed871-221">Jeśli nie są automatycznego żądania certyfikatów, który trzeba będzie skontaktuj się z żądania certyfikatu?</span><span class="sxs-lookup"><span data-stu-id="ed871-221">If certificate requests are not automated, who will you need to contact to requests a certificate?</span></span>|
<span data-ttu-id="ed871-222">Co to jest średnią przetwarzania żądania?</span><span class="sxs-lookup"><span data-stu-id="ed871-222">What is the average turnaround for the request?</span></span>|
<span data-ttu-id="ed871-223">Jak zostanie plik certyfikatu przeniesiona do Ciebie?</span><span class="sxs-lookup"><span data-stu-id="ed871-223">How will the certificate file be transferred to you?</span></span>|
<span data-ttu-id="ed871-224">Jak będzie klucz prywatny certyfikatu przekazywanych do Ciebie?</span><span class="sxs-lookup"><span data-stu-id="ed871-224">How will the certificate private key be transferred to you?</span></span>|
<span data-ttu-id="ed871-225">Jak długo trwa domyślny czas wygaśnięcia?</span><span class="sxs-lookup"><span data-stu-id="ed871-225">How long is the default expiration time?</span></span>|
<span data-ttu-id="ed871-226">Ma rozliczane na nazwę DNS w środowisku serwera ściągania, używanego programu nazwę certyfikatu?</span><span class="sxs-lookup"><span data-stu-id="ed871-226">Have you settled on a DNS name for the pull server environment, that you can use for the certificate name?</span></span>|

### <a name="choosing-an-architecture"></a><span data-ttu-id="ed871-227">Wybieranie architektury</span><span class="sxs-lookup"><span data-stu-id="ed871-227">Choosing an architecture</span></span>

<span data-ttu-id="ed871-228">Serwer ściągania można wdrożyć przy użyciu jednej usługi sieci web na usług IIS lub udziału plików SMB.</span><span class="sxs-lookup"><span data-stu-id="ed871-228">A pull server can be deployed using either a web service hosted on IIS, or an SMB file share.</span></span> <span data-ttu-id="ed871-229">W większości przypadków opcji usługi sieci web zapewni większą elastyczność.</span><span class="sxs-lookup"><span data-stu-id="ed871-229">In most situations, the web service option will provide greater flexibility.</span></span> <span data-ttu-id="ed871-230">Nie jest nietypowe dla ruchu HTTPS przechodzenia przez granice sieci, często filtrowane lub zablokowane między sieciami ruchu SMB.</span><span class="sxs-lookup"><span data-stu-id="ed871-230">It is not uncommon for HTTPS traffic to traverse network boundaries, whereas SMB traffic is often filtered or blocked between networks.</span></span> <span data-ttu-id="ed871-231">Usługa sieci web oferuje również możliwość dołączenia serwera zgodność lub sieci Web Reporting Manager (zarówno tematy mogą być adresowane w przyszłych wersjach tego dokumentu), które udostępniają mechanizm dla klientów w celu zgłoszenia stanu wstecz do serwera w celu scentralizowanego widoczności.</span><span class="sxs-lookup"><span data-stu-id="ed871-231">The web service also offers the option to include a Conformance Server or Web Reporting Manager (both topics to be addressed in a future version of this document) that provide a mechanism for clients to report status back to a server for centralized visibility.</span></span>
<span data-ttu-id="ed871-232">Protokół SMB zapewnia opcję dla środowisk, w którym zasady wymuszają serwera sieci web nie powinien zostać użyte, a pozostałe wymagania środowiska, wchodzące w roli serwera sieci web niepożądane.</span><span class="sxs-lookup"><span data-stu-id="ed871-232">SMB provides an option for environments where policy dictates that a web server should not be utilized, and for other environmental requirements that make a web server role undesirable.</span></span>
<span data-ttu-id="ed871-233">W obu przypadkach należy pamiętać oszacować wymagania dotyczące podpisywania i szyfrowania ruchu sieciowego.</span><span class="sxs-lookup"><span data-stu-id="ed871-233">In either case, remember to evaluate the requirements for signing and encrypting traffic.</span></span> <span data-ttu-id="ed871-234">HTTPS, podpisywania SMB i zasady IPSEC są wszystkie opcje warto uwzględnieniu.</span><span class="sxs-lookup"><span data-stu-id="ed871-234">HTTPS, SMB signing, and IPSEC policies are all options worth considering.</span></span>

#### <a name="load-balancing"></a><span data-ttu-id="ed871-235">Równoważenie obciążenia</span><span class="sxs-lookup"><span data-stu-id="ed871-235">Load balancing</span></span>
<span data-ttu-id="ed871-236">Klienci interakcji z usługą sieci web należy żądanie informacji, która jest zwracana w jednej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="ed871-236">Clients interacting with the web service make a request for information that is returned in a single response.</span></span> <span data-ttu-id="ed871-237">Żadne kolejne żądania są wymagane, więc nie jest niezbędna dla platformy, aby upewnić się, że sesje są zachowywane na jednym serwerze w dowolnym momencie w czasie równoważenia obciążenia.</span><span class="sxs-lookup"><span data-stu-id="ed871-237">No sequential requests are required, so it is not necessary for the load balancing platform to ensure sessions are maintained on a single server at any point in time.</span></span>

<span data-ttu-id="ed871-238">Planowanie zadań</span><span class="sxs-lookup"><span data-stu-id="ed871-238">Planning task</span></span>|
---|
<span data-ttu-id="ed871-239">Jakie rozwiązanie będzie służyć do Równoważenie obciążenia ruchu w serwerów?</span><span class="sxs-lookup"><span data-stu-id="ed871-239">What solution will be used for load balancing traffic across servers?</span></span>|
<span data-ttu-id="ed871-240">Jeśli używasz sprzętowego równoważenia obciążenia, który zajmie żądanie, aby dodać nową konfigurację do urządzenia?</span><span class="sxs-lookup"><span data-stu-id="ed871-240">If using a hardware load balancer, who will take a request to add a new configuration to the device?</span></span>|
<span data-ttu-id="ed871-241">Co to jest średnią przetwarzania dla żądania skonfigurować nowe obciążenia zrównoważonym usługi sieci web?</span><span class="sxs-lookup"><span data-stu-id="ed871-241">What is the average turnaround for a request to configure a new load balanced web service?</span></span>|
<span data-ttu-id="ed871-242">Jakie informacje będą wymagane dla żądania?</span><span class="sxs-lookup"><span data-stu-id="ed871-242">What information will be required for the request?</span></span>|
<span data-ttu-id="ed871-243">Trzeba będzie żądać dodatkowych adresów IP lub zespołu odpowiedzialnego za równoważenie obciążenia obsłuży który?</span><span class="sxs-lookup"><span data-stu-id="ed871-243">Will you need to request an additional IP or will the team responsible for load balancing handle that?</span></span>|
<span data-ttu-id="ed871-244">Czy masz wymagane rekordy DNS i będzie to wymagane przez zespół odpowiedzialny za konfigurację rozwiązania do równoważenia obciążenia?</span><span class="sxs-lookup"><span data-stu-id="ed871-244">Do you have the DNS records needed, and will this be required by the team responsible for configuring the load balancing solution?</span></span>|
<span data-ttu-id="ed871-245">Rozwiązanie równoważenia obciążenia wymaga obsługi infrastruktury kluczy publicznych przez urządzenie lub może on równoważyć obciążenie przez ruch protokołu HTTPS, dopóki nie ma żadnych wymagań sesji?</span><span class="sxs-lookup"><span data-stu-id="ed871-245">Does the load balancing solution require that PKI be handled by the device or can it load balance HTTPS traffic as long as there are no session requirements?</span></span>|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a><span data-ttu-id="ed871-246">Konfiguracje przemieszczania i modułów na serwerze ściągania</span><span class="sxs-lookup"><span data-stu-id="ed871-246">Staging configurations and modules on the pull server</span></span>

<span data-ttu-id="ed871-247">W ramach planowania konfiguracji konieczne będzie traktować, o których DSC moduły i konfiguracje będzie obsługiwana przez z serwerem ściągania.</span><span class="sxs-lookup"><span data-stu-id="ed871-247">As part of configuration planning, you will need to think about which DSC modules and configurations will be hosted by the pull server.</span></span> <span data-ttu-id="ed871-248">Na potrzeby planowania konfiguracji, należy mieć podstawową wiedzę na temat sposobu przygotowania i wdrożenia zawartości na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="ed871-248">For the purpose of configuration planning it is important to have a basic understanding of how to prepare and deploy content to a pull server.</span></span>

<span data-ttu-id="ed871-249">W przyszłości w tej sekcji zostanie rozwinięty i zawarte w przewodniku obsługi dla serwera ściągania usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="ed871-249">In the future, this section will be expanded and included in an Operations Guide for DSC Pull Server.</span></span>  <span data-ttu-id="ed871-250">Przewodnika przedstawimy codziennie proces zarządzania moduły i konfiguracje w czasie automatyzacji.</span><span class="sxs-lookup"><span data-stu-id="ed871-250">The guide will discuss the day to day process for managing modules and configurations over time with automation.</span></span>

#### <a name="dsc-modules"></a><span data-ttu-id="ed871-251">Moduły DSC</span><span class="sxs-lookup"><span data-stu-id="ed871-251">DSC modules</span></span>
<span data-ttu-id="ed871-252">Żądania konfiguracji klientów należy wymagane moduły DSC.</span><span class="sxs-lookup"><span data-stu-id="ed871-252">Clients that request a configuration will need the required DSC modules.</span></span> <span data-ttu-id="ed871-253">Funkcje serwera ściągania jest zautomatyzować dystrybucji na żądanie DSC modułów do klientów.</span><span class="sxs-lookup"><span data-stu-id="ed871-253">A functionality of the pull server is to automate distribution on demand of DSC modules to clients.</span></span> <span data-ttu-id="ed871-254">Wdrażając serwera ściągania po raz pierwszy, prawdopodobnie jako laboratorium lub Weryfikacja koncepcji, prawdopodobnie zamierzasz są zależne od konfiguracji DSC modułów, które są dostępne z repozytoria publicznej, takich jak galerii programu PowerShell lub repozytoriów PowerShell.org GitHub dla modułów DSC .</span><span class="sxs-lookup"><span data-stu-id="ed871-254">If you are deploying a pull server for the first time, perhaps as a lab or proof of concept, you are likely going to depend on DSC modules that are available from public repositories such as the PowerShell Gallery or the PowerShell.org GitHub repositories for DSC modules.</span></span>

<span data-ttu-id="ed871-255">Należy pamiętać, że nawet w przypadku zaufanej online źródeł, takich jak galerii programu PowerShell, każdy moduł, który jest pobierany z publicznej repozytorium należy ją sprawdzić przez innego środowiska PowerShell i wiedzy środowisko, w której będzie modułów używane przed ich użyciem w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="ed871-255">It is critical to remember that even for trusted online sources such as the PowerShell Gallery, any module that is downloaded from a public repository should be reviewed by someone with PowerShell experience and knowledge of the environment where the modules will be used prior to being used in production.</span></span> <span data-ttu-id="ed871-256">Podczas wykonywania tego zadania jest odpowiedni moment, aby sprawdzić wszelkie dodatkowe ładunku w module, który może być usunięty, takie jak dokumentacja i przykładowe skrypty.</span><span class="sxs-lookup"><span data-stu-id="ed871-256">While completing this task it is a good time to check for any additional payload in the module that can be removed such as documentation and example scripts.</span></span> <span data-ttu-id="ed871-257">Zmniejsza to przepustowość sieci dla klienta w ich pierwsze żądanie po moduły będą pobierane przez sieć z serwera do klienta.</span><span class="sxs-lookup"><span data-stu-id="ed871-257">This will reduce the network bandwidth per client in their first request, when modules will be downloaded over the network from server to client.</span></span>

<span data-ttu-id="ed871-258">Każdy moduł muszą być spakowane w określonym formacie pliku ZIP o nazwie ModuleName_Version.zip, który zawiera ładunek modułu.</span><span class="sxs-lookup"><span data-stu-id="ed871-258">Each module must be packaged in a specific format, a ZIP file named ModuleName_Version.zip that contains the module payload.</span></span> <span data-ttu-id="ed871-259">Po skopiowaniu pliku na serwerze, należy utworzyć plik sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="ed871-259">After the file is copied to the server a checksum file must be created.</span></span> <span data-ttu-id="ed871-260">Jeżeli klienci łączą się z serwerem, suma kontrolna służy do Sprawdź, czy zawartość modułu DSC nie zmienił się od momentu jego opublikowania.</span><span class="sxs-lookup"><span data-stu-id="ed871-260">When clients connect to the server, the checksum is used to verify the content of the DSC module has not changed since it was published.</span></span>

```powershell
New-DscCheckSum -ConfigurationPath .\ -OutPath .\
```

<span data-ttu-id="ed871-261">Planowanie zadań</span><span class="sxs-lookup"><span data-stu-id="ed871-261">Planning task</span></span>|
---|
<span data-ttu-id="ed871-262">Jeśli planujesz środowiska testu lub w laboratorium, jakie scenariusze są kluczem do sprawdzania poprawności?</span><span class="sxs-lookup"><span data-stu-id="ed871-262">If you are planning a test or lab environment which scenarios are key to validate?</span></span>|
<span data-ttu-id="ed871-263">Czy istnieją publicznie dostępnych modułów, które zawierają zasoby, aby pokrywał się wszystko, czego potrzebujesz lub czy będzie potrzebna do tworzenia własnych zasobów?</span><span class="sxs-lookup"><span data-stu-id="ed871-263">Are there publicly available modules that contain resources to cover everything you need or will you need to author your own resources?</span></span>|
<span data-ttu-id="ed871-264">Środowisko będą miały dostęp do Internetu do pobierania modułów publicznych?</span><span class="sxs-lookup"><span data-stu-id="ed871-264">Will your environment have Internet access to retrieve public modules?</span></span>|
<span data-ttu-id="ed871-265">Kto będzie odpowiedzialny za recenzowania modułów DSC?</span><span class="sxs-lookup"><span data-stu-id="ed871-265">Who will be responsible for reviewing DSC modules?</span></span>|
<span data-ttu-id="ed871-266">Jeśli planujesz środowiska produkcyjnego co będzie używana jako lokalnego repozytorium do przechowywania modułów DSC?</span><span class="sxs-lookup"><span data-stu-id="ed871-266">If you are planning a production environment what will you use as a local repository for storing DSC modules?</span></span>|
<span data-ttu-id="ed871-267">Zespołu centralnego zaakceptuje DSC modułów zespoły aplikacji?</span><span class="sxs-lookup"><span data-stu-id="ed871-267">Will a central team accept DSC modules from application teams?</span></span> <span data-ttu-id="ed871-268">Co to jest proces?</span><span class="sxs-lookup"><span data-stu-id="ed871-268">What will the process be?</span></span>|
<span data-ttu-id="ed871-269">Zostanie automatyzacji pakowania, kopiowanie i Tworzenie sumy kontrolnej dla modułów DSC gotowe do produkcji na serwer, z Twojego repozytorium źródła?</span><span class="sxs-lookup"><span data-stu-id="ed871-269">Will you automate packaging, copying, and creating a checksum for production-ready DSC modules to the server, from your source repo?</span></span>|
<span data-ttu-id="ed871-270">Zespół będzie odpowiedzialny za zarządzanie z platformy automatyzacji?</span><span class="sxs-lookup"><span data-stu-id="ed871-270">Will your team be responsible for managing the automation platform as well?</span></span>|

#### <a name="dsc-configurations"></a><span data-ttu-id="ed871-271">Konfiguracji DSC</span><span class="sxs-lookup"><span data-stu-id="ed871-271">DSC configurations</span></span>

<span data-ttu-id="ed871-272">Cel serwera ściągania jest zapewnienie scentralizowane mechanizm dystrybuowania konfiguracji DSC dla węzłów klienta.</span><span class="sxs-lookup"><span data-stu-id="ed871-272">The purpose of a pull server is to provide a centralized mechanism for distributing DSC configurations to client nodes.</span></span> <span data-ttu-id="ed871-273">Konfiguracje są przechowywane na serwerze jako dokumenty MOF.</span><span class="sxs-lookup"><span data-stu-id="ed871-273">The configurations are stored on the server as MOF documents.</span></span>
<span data-ttu-id="ed871-274">Każdy dokument będą miały nazwę nadaną przez unikatowy identyfikator GUID.</span><span class="sxs-lookup"><span data-stu-id="ed871-274">Each document will be named with a unique GUID.</span></span> <span data-ttu-id="ed871-275">Jeśli klientów skonfigurowano nawiązać połączenia z serwerem ściągania, otrzymuje także identyfikatora GUID dla konfiguracji, należy zażądać ich.</span><span class="sxs-lookup"><span data-stu-id="ed871-275">When clients are configured to connect with a pull server, they are also given the GUID for the configuration they should request.</span></span> <span data-ttu-id="ed871-276">Ten system odwołujące się do konfiguracji przez identyfikator GUID gwarantuje unikatowości globalne i jest elastyczny tak, aby konfiguracji mogą być stosowane z szczegółowości na węzeł lub Konfiguracja roli obejmującej wiele serwerów, które powinny mieć identyczne konfiguracje.</span><span class="sxs-lookup"><span data-stu-id="ed871-276">This system of referencing configurations by GUID guarantees global uniqueness and is flexible such that a configuration can be applied with granularity per node, or as a role configuration that spans many servers that should have identical configurations.</span></span>

#### <a name="guids"></a><span data-ttu-id="ed871-277">Identyfikatory GUID</span><span class="sxs-lookup"><span data-stu-id="ed871-277">GUIDs</span></span>

<span data-ttu-id="ed871-278">Planowanie konfiguracji identyfikatorów GUID warto uwagi dodatkowe w przypadku poprzez wdrożenie serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="ed871-278">Planning for configuration GUIDs is worth additional attention when thinking through a pull server deployment.</span></span> <span data-ttu-id="ed871-279">Nie jest wymagane określonego sposobu obsługi identyfikatorów GUID i proces może być unikatowe dla każdego środowiska.</span><span class="sxs-lookup"><span data-stu-id="ed871-279">There is no specific requirement for how to handle GUIDs and the process is likely to be unique for each environment.</span></span> <span data-ttu-id="ed871-280">Proces może należeć do zakresu od prostego do złożonych: centralnie przechowywany plik CSV, prosty tabeli SQL, CMDB lub złożonych rozwiązania wymagających integracji z innego narzędzia lub oprogramowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="ed871-280">The process can range from simple to complex: a centrally stored CSV file, a simple SQL table, a CMDB, or a complex solution requiring integration with another tool or software solution.</span></span> <span data-ttu-id="ed871-281">Istnieją dwie metody ogólne:</span><span class="sxs-lookup"><span data-stu-id="ed871-281">There are two general approaches:</span></span>

 - <span data-ttu-id="ed871-282">**Przypisywanie identyfikatorów GUID na serwer** — zawiera miary gwarancji, że każdy serwer konfiguracji jest kontrolowany pojedynczo.</span><span class="sxs-lookup"><span data-stu-id="ed871-282">**Assigning GUIDs per server** — Provides a measure of assurance that every server configuration is controlled individually.</span></span> <span data-ttu-id="ed871-283">Poziom dokładności wokół aktualizacji i nie może działać również w środowiskach z kilku serwerów.</span><span class="sxs-lookup"><span data-stu-id="ed871-283">This provides a level of precision around updates and can work well in environments with few servers.</span></span>
 - <span data-ttu-id="ed871-284">**Przypisywanie identyfikatorów GUID dla każdej roli serwera** — wszystkie serwery, które wykonują tę samą funkcję, takich jak serwery sieci web, użyj tego samego identyfikatora GUID aby odwoływał się do danych konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ed871-284">**Assigning GUIDs per server role** — All servers that perform the same function, such as web servers, use the same GUID to reference the required configuration data.</span></span>  <span data-ttu-id="ed871-285">Należy pamiętać, że jeśli wiele serwerów współużytkować ten sam identyfikator GUID, wszystkie z nich będzie można zaktualizować jednocześnie podczas zmiany konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ed871-285">Be aware that if many servers share the same GUID, all of them would be updated simultaneously when the configuration changes.</span></span>

<span data-ttu-id="ed871-286">Identyfikator GUID to element, którego należy traktować jako poufnych danych, ponieważ może być wykorzystywana przez osobę mającą złośliwymi działaniami w celu uzyskania informacji dotyczących sposobu wdrożone i skonfigurowane w środowisku serwerów.</span><span class="sxs-lookup"><span data-stu-id="ed871-286">The GUID is something that should be considered sensitive data because it could be leveraged by someone with malicious intent to gain intelligence about how servers are deployed and configured in your environment.</span></span> <span data-ttu-id="ed871-287">Aby uzyskać więcej informacji, zobacz [bezpiecznie alokacji identyfikatorów GUID w trybie programu PowerShell żądanego stanu konfiguracji ściągnięcia](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx).</span><span class="sxs-lookup"><span data-stu-id="ed871-287">For more information, see [Securely allocating GUIDs in PowerShell Desired State Configuration Pull Mode](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx).</span></span>

<span data-ttu-id="ed871-288">Planowanie zadań</span><span class="sxs-lookup"><span data-stu-id="ed871-288">Planning task</span></span>|
---|
<span data-ttu-id="ed871-289">Kto będzie odpowiedzialny za kopiowanie konfiguracji do folderu na serwerze ściągania, gdy są one gotowe?</span><span class="sxs-lookup"><span data-stu-id="ed871-289">Who will be responsible for copying configurations in to the pull server folder when they are ready?</span></span>|
<span data-ttu-id="ed871-290">Konfiguracje są tworzone przez zespół aplikacji, co procesu należy przekazują je?</span><span class="sxs-lookup"><span data-stu-id="ed871-290">If Configurations are authored by an application team, what will the process be to hand them off?</span></span>|
<span data-ttu-id="ed871-291">Będzie można korzystać z repozytorium do przechowywania konfiguracji, jak długo muszą one być utworzone, zespołów?</span><span class="sxs-lookup"><span data-stu-id="ed871-291">Will you leverage a repository to store configurations as they are being authored, across teams?</span></span>|
<span data-ttu-id="ed871-292">Będzie można zautomatyzować proces kopiowanie konfiguracji na serwerze i tworzenia sumy kontrolnej, gdy są one gotowe?</span><span class="sxs-lookup"><span data-stu-id="ed871-292">Will you automate the process of copying configurations to the server and creating a checksum when they are ready?</span></span>|
<span data-ttu-id="ed871-293">Jak można przypisze identyfikatorów GUID do serwerów i ról i będzie to przechowywania?</span><span class="sxs-lookup"><span data-stu-id="ed871-293">How will you map GUIDs to servers or roles, and where will this be stored?</span></span>|
<span data-ttu-id="ed871-294">Jakie będzie używana jako proces konfigurowania komputerów klienckich i jak będą ją zintegrować z procesem tworzenia i przechowywania identyfikatorów GUID konfiguracji?</span><span class="sxs-lookup"><span data-stu-id="ed871-294">What will you use as a process to configure client machines, and how will it integrate with your process for creating and storing Configuration GUIDs?</span></span>|

## <a name="installation-guide"></a><span data-ttu-id="ed871-295">Przewodnik instalacji</span><span class="sxs-lookup"><span data-stu-id="ed871-295">Installation Guide</span></span>

<span data-ttu-id="ed871-296">*Skrypty podanych w tym dokumencie przedstawiono stabilna. Zawsze skrypty należy dokładnie przejrzeć przed wykonaniem ich w środowisku produkcyjnym.*</span><span class="sxs-lookup"><span data-stu-id="ed871-296">*Scripts given in this document are stable examples. Always review scripts carefully before executing them in a production environment.*</span></span>

### <a name="prerequisites"></a><span data-ttu-id="ed871-297">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="ed871-297">Prerequisites</span></span>

<span data-ttu-id="ed871-298">Aby sprawdzić wersję programu PowerShell na serwerze, użyj następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="ed871-298">To verify the version of PowerShell on your server use the following command.</span></span>

```powershell
$PSVersionTable.PSVersion
```

<span data-ttu-id="ed871-299">Jeśli to możliwe należy uaktualnić do najnowszej wersji Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="ed871-299">If possible, upgrade to the latest version of Windows Management Framework.</span></span>
<span data-ttu-id="ed871-300">Następnie należy pobrać `xPsDesiredStateConfiguration` modułu przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="ed871-300">Next, download the `xPsDesiredStateConfiguration` module using the following command.</span></span>


```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="ed871-301">Polecenie poprosi użytkownika o zgodę przed pobraniem modułu.</span><span class="sxs-lookup"><span data-stu-id="ed871-301">The command will ask for your approval before downloading the module.</span></span>

### <a name="installation-and-configuration-scripts"></a><span data-ttu-id="ed871-302">Instalacja i konfiguracja skryptów</span><span class="sxs-lookup"><span data-stu-id="ed871-302">Installation and configuration scripts</span></span>
-

<span data-ttu-id="ed871-303">Najlepszą metodą wdrażania serwera ściągania usługi Konfiguracja DSC jest użyć skryptu konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="ed871-303">The best method to deploy a DSC pull server is to use a DSC configuration script.</span></span> <span data-ttu-id="ed871-304">Ten dokument przedstawia skrypty w tym zarówno podstawowe ustawienia, które konfiguruje się tylko DSC usługi sieci web oraz zaawansowane ustawienia konfigurujące systemu Windows Server na trasie między innymi DSC usługi sieci web.</span><span class="sxs-lookup"><span data-stu-id="ed871-304">This document will present scripts including both basic settings that would configure only the DSC web service and advanced settings that would configure a Windows Server end-to-end including DSC web service.</span></span>

<span data-ttu-id="ed871-305">Uwaga: Obecnie `xPSDesiredStateConfiguation` modułu DSC wymaga serwer do ustawień regionalnych pl-pl.</span><span class="sxs-lookup"><span data-stu-id="ed871-305">Note:  Currently the `xPSDesiredStateConfiguation` DSC module requires the server to be EN-US locale.</span></span>

### <a name="basic-configuration-for-windows-server-2012"></a><span data-ttu-id="ed871-306">Podstawowa konfiguracja systemu Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="ed871-306">Basic configuration for Windows Server 2012</span></span>
-------------------------------------------
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

### <a name="advanced-configuration-for-windows-server-2012-r2"></a><span data-ttu-id="ed871-307">Konfiguracja zaawansowana dla systemu Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ed871-307">Advanced configuration for Windows Server 2012 R2</span></span>

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


### <a name="verify-pull-server-functionality"></a><span data-ttu-id="ed871-308">Sprawdź funkcje serwera ściągania</span><span class="sxs-lookup"><span data-stu-id="ed871-308">Verify pull server functionality</span></span>

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](invoke-webrequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}
Verify-DSCPullServer 'INSERT SERVER FQDN'

Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a><span data-ttu-id="ed871-309">Konfigurowanie klientów</span><span class="sxs-lookup"><span data-stu-id="ed871-309">Configure clients</span></span>

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


## <a name="additional-references-snippets-and-examples"></a><span data-ttu-id="ed871-310">Dodatkowe informacje, wstawki i przykłady</span><span class="sxs-lookup"><span data-stu-id="ed871-310">Additional references, snippets, and examples</span></span>

<span data-ttu-id="ed871-311">Ten przykład przedstawia sposób ręcznie zainicjować połączenie klienta (wymaga WMF5) do testowania.</span><span class="sxs-lookup"><span data-stu-id="ed871-311">This example shows how to manually initiate a client connection (requires WMF5) for testing.</span></span>

```powershell
Update-DSCConfiguration –Wait -Verbose
```

<span data-ttu-id="ed871-312">[DnsServerResourceRecordName Dodaj](http://bit.ly/1G1H31L) polecenie cmdlet umożliwia dodanie typu rekordu CNAME do strefy DNS.</span><span class="sxs-lookup"><span data-stu-id="ed871-312">The [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet is used to add a type CNAME record to a DNS zone.</span></span>

<span data-ttu-id="ed871-313">Funkcja programu PowerShell do [utworzyć sumy kontrolnej i opublikować MOF DSC serwerem ściągania SMB](http://bit.ly/1E46BhI) automatycznie generuje wymagane sumy kontrolnej, a następnie kopiuje pliki sumy kontrolnej i MOF konfiguracji na serwerze ściągania SMB.</span><span class="sxs-lookup"><span data-stu-id="ed871-313">The PowerShell Function to [Create a Checksum and Publish DSC MOF to SMB Pull Server](http://bit.ly/1E46BhI) automatically generates the required checksum, and then copies both the MOF configuration and checksum files to the SMB pull server.</span></span>

## <a name="appendix---understanding-odata-service-data-file-types"></a><span data-ttu-id="ed871-314">Dodatek — opis ODATA typów plików usługi danych</span><span class="sxs-lookup"><span data-stu-id="ed871-314">Appendix - Understanding ODATA service data file types</span></span>

<span data-ttu-id="ed871-315">Plik danych są przechowywane do utworzenia informacji podczas wdrażania serwera ściągania, która obejmuje usługę sieci web OData.</span><span class="sxs-lookup"><span data-stu-id="ed871-315">A data file is stored to create information during deployment of a pull server that includes the OData web service.</span></span> <span data-ttu-id="ed871-316">Typ pliku zależy od systemu operacyjnego, zgodnie z poniższym opisem.</span><span class="sxs-lookup"><span data-stu-id="ed871-316">The type of file depends on the operating system, as described below.</span></span>

 - <span data-ttu-id="ed871-317">**Windows Server 2012** zawsze będzie typ .mdb</span><span class="sxs-lookup"><span data-stu-id="ed871-317">**Windows Server 2012** The file type will always be   .mdb</span></span>
 - <span data-ttu-id="ed871-318">**Windows Server 2012 R2** typ pliku zostaną domyślnie .edb, chyba że .mdb jest określona w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ed871-318">**Windows Server 2012 R2** The file type will default to .edb unless a .mdb is specified in the configuration</span></span>

<span data-ttu-id="ed871-319">W [zaawansowane przykładowy skrypt](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) instalacji serwera ściągania, będzie również znaleźć przykład automatycznie kontrolować ustawienia pliku web.config w celu zapobieżenia wszelkie ryzyko błąd spowodowany przez typ pliku.</span><span class="sxs-lookup"><span data-stu-id="ed871-319">In the [Advanced example script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) for installing a Pull Server, you will also find an example of how to automatically control the web.config file settings to prevent any chance of error caused by file type.</span></span>