---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Instalowanie zestawu SDK programu Windows PowerShell
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: fa876bac0c1afac24f93d11dd2e7ecfb1165cf5f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893542"
---
# <a name="installing-the-windows-powershell-sdk"></a><span data-ttu-id="4ac62-103">Instalowanie zestawu SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4ac62-103">Installing the Windows PowerShell SDK</span></span>

<span data-ttu-id="4ac62-104">W poniższym temacie opisano sposób instalowania zestawu SDK programu PowerShell w różnych wersjach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4ac62-104">The following topic describes how to install the PowerShell SDK on different versions of Windows.</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a><span data-ttu-id="4ac62-105">Instalowanie programu Windows PowerShell 3.0 zestawu SDK dla systemu Windows 8 i Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="4ac62-105">Installing Windows PowerShell 3.0 SDK for Windows 8 and Windows Server 2012</span></span>

<span data-ttu-id="4ac62-106">Windows PowerShell 3.0 jest automatycznie instalowany z systemem Windows 8 i Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="4ac62-106">Windows PowerShell 3.0 is automatically installed with Windows 8 and Windows Server 2012.</span></span>
<span data-ttu-id="4ac62-107">Ponadto można pobrać i zainstalować zestawy referencyjne dla programu Windows PowerShell 3.0 w ramach zestawu SDK dla systemu Windows 8.</span><span class="sxs-lookup"><span data-stu-id="4ac62-107">In addition, you can download and install the reference assemblies for Windows PowerShell 3.0 as part of the Windows 8 SDK.</span></span>
<span data-ttu-id="4ac62-108">Te zestawy umożliwiają pisanie poleceń cmdlet, dostawców i programy hosta dla programu Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="4ac62-108">These assemblies allow you to write cmdlets, providers, and host programs for Windows PowerShell 3.0.</span></span>
<span data-ttu-id="4ac62-109">Po zainstalowaniu zestawu SDK Windows dla systemu Windows 8, zestawy programu Windows PowerShell są automatycznie instalowane w folderze zestawu odwołania w `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`.</span><span class="sxs-lookup"><span data-stu-id="4ac62-109">When you install the Windows SDK for Windows 8, the Windows PowerShell assemblies are automatically installed in the reference assembly folder, in `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`.</span></span>
<span data-ttu-id="4ac62-110">Aby uzyskać więcej informacji, zobacz [witryny pobierania systemu Windows 8 SDK](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive).</span><span class="sxs-lookup"><span data-stu-id="4ac62-110">For more information, see the [Windows 8 SDK download site](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive).</span></span>
<span data-ttu-id="4ac62-111">Przykłady kodu programu Windows PowerShell są także dostępne w Centrum opracowywania rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="4ac62-111">Windows PowerShell code samples are also available on the Development Center.</span></span>
<span data-ttu-id="4ac62-112">Aby uzyskać więcej informacji, zobacz stronę próbki kodu w [witryny Centrum deweloperów](https://code.msdn.microsoft.com:443/windowsdesktop/).</span><span class="sxs-lookup"><span data-stu-id="4ac62-112">For more information, see the Desktop code sample page on the [Dev center site](https://code.msdn.microsoft.com:443/windowsdesktop/).</span></span>

<span data-ttu-id="4ac62-113">Ponadto program Windows PowerShell 3.0 jest wstecznie zgodny z za pomocą Windows PowerShell 2.0 SDK, które zawierają wiele przykładów kodu.</span><span class="sxs-lookup"><span data-stu-id="4ac62-113">In addition, Windows PowerShell 3.0 is backwards-compatible with the Windows PowerShell 2.0 SDK, which includes a number of code samples.</span></span>
<span data-ttu-id="4ac62-114">Aby uzyskać więcej informacji na temat sposobu pobierania zestawu SDK programu Windows PowerShell 2.0 zobacz poniżej.</span><span class="sxs-lookup"><span data-stu-id="4ac62-114">For more information on how to download the Windows PowerShell 2.0 SDK, see below.</span></span>
<span data-ttu-id="4ac62-115">(Zwróć uwagę, przykłady kodu 2.0 są zgodne z systemem Windows 8 i Windows PowerShell 3.0, można zainstalować program Windows PowerShell 2.0 na platformie systemu Windows 8).</span><span class="sxs-lookup"><span data-stu-id="4ac62-115">(Note that while the 2.0 code samples are compatible with Windows 8 and Windows PowerShell 3.0, you cannot install Windows PowerShell 2.0 on a Windows 8 platform.)</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a><span data-ttu-id="4ac62-116">Instalowanie programu Windows PowerShell 3.0 SDK for Windows 7 i Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="4ac62-116">Installing Windows PowerShell 3.0 SDK for Windows 7 and Windows Server 2008 R2</span></span>

<span data-ttu-id="4ac62-117">Windows 7 i Windows Server 2008 R2 automatycznie mieć zainstalowany program PowerShell w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="4ac62-117">Windows 7 and Windows Server 2008 R2 automatically have PowerShell 2.0 installed.</span></span>
<span data-ttu-id="4ac62-118">Ponadto w tych systemach można zainstalować program PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="4ac62-118">In addition, you can install PowerShell 3.0 on these systems.</span></span>
<span data-ttu-id="4ac62-119">(Aby uzyskać więcej informacji, zobacz [Instalowanie programu Windows PowerShell](Installing-Windows-PowerShell.md).).</span><span class="sxs-lookup"><span data-stu-id="4ac62-119">(For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).).</span></span>
<span data-ttu-id="4ac62-120">Jak opisano powyżej, można także zainstalować zestaw Windows 8 SDK na Windows 7 i Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="4ac62-120">As described above, you can also install the Windows 8 SDK on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a><span data-ttu-id="4ac62-121">Instalowanie programu Windows PowerShell 2.0 SDK for Windows 7, Vista, XP, Server 2003 i Server 2008</span><span class="sxs-lookup"><span data-stu-id="4ac62-121">Installing Windows PowerShell 2.0 SDK for Windows 7, Vista, XP, Server 2003, and Server 2008</span></span>

<span data-ttu-id="4ac62-122">Windows PowerShell 2.0 SDK zawiera zestawy odwołań wymagane do zapisania poleceń cmdlet, dostawców i hostowanie aplikacji i udostępnia C# przykładowy kod, który może służyć jako punkt początkowy, po rozpoczęciu pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="4ac62-122">The Windows PowerShell 2.0 SDK provides the reference assemblies needed to write cmdlets, providers, and hosting applications, and it provides C# sample code that can be used as the starting point when you begin writing code.</span></span>

<span data-ttu-id="4ac62-123">Aby zainstalować zestaw SDK, zobacz [zestawu SDK programu Windows PowerShell 2.0](http://www.microsoft.com/en-us/download/details.aspx?id=2560).</span><span class="sxs-lookup"><span data-stu-id="4ac62-123">To install this SDK, see [Windows PowerShell 2.0 SDK](http://www.microsoft.com/en-us/download/details.aspx?id=2560).</span></span>

## <a name="reference-assemblies"></a><span data-ttu-id="4ac62-124">Zestawy referencyjne</span><span class="sxs-lookup"><span data-stu-id="4ac62-124">Reference assemblies</span></span>

<span data-ttu-id="4ac62-125">Zestawy odwołania są instalowane domyślnie w następującej lokalizacji: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span><span class="sxs-lookup"><span data-stu-id="4ac62-125">Reference assemblies are installed in the following location by default: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span></span>

> [!NOTE] 
> <span data-ttu-id="4ac62-126">Nie można załadować kodu, który jest kompilowany dla zestawów programu Windows PowerShell 2.0 do instalacji programu Windows PowerShell w wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="4ac62-126">Code that is compiled against the Windows PowerShell 2.0 assemblies cannot be loaded into Windows PowerShell 1.0 installations.</span></span>
> <span data-ttu-id="4ac62-127">Jednak kod, który jest kompilowany dla zestawów programu Windows PowerShell w wersji 1.0 mogą zostać załadowane do instalacji programu Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="4ac62-127">However, code that is compiled against the Windows PowerShell 1.0 assemblies can be loaded into Windows PowerShell 2.0 installations.</span></span>

## <a name="samples"></a><span data-ttu-id="4ac62-128">Przykłady</span><span class="sxs-lookup"><span data-stu-id="4ac62-128">Samples</span></span>

<span data-ttu-id="4ac62-129">Przykłady kodu są instalowane domyślnie w następującej lokalizacji: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span><span class="sxs-lookup"><span data-stu-id="4ac62-129">Code samples are installed in the following location by default: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span></span>

<span data-ttu-id="4ac62-130">Każda próbka jest krótki opis można znaleźć w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="4ac62-130">The following sections provide a brief description of what each sample does.</span></span>

## <a name="cmdlet-samples"></a><span data-ttu-id="4ac62-131">Przykłady polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="4ac62-131">Cmdlet samples</span></span>

### <a name="getprocesssample01"></a><span data-ttu-id="4ac62-132">GetProcessSample01</span><span class="sxs-lookup"><span data-stu-id="4ac62-132">GetProcessSample01</span></span>

<span data-ttu-id="4ac62-133">Pokazuje, jak pisanie prostego polecenia cmdlet, które pobiera wszystkie procesy na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="4ac62-133">Shows how to write a simple cmdlet that gets all the processes on the local computer.</span></span>

### <a name="getprocesssample02"></a><span data-ttu-id="4ac62-134">GetProcessSample02</span><span class="sxs-lookup"><span data-stu-id="4ac62-134">GetProcessSample02</span></span>

<span data-ttu-id="4ac62-135">Pokazuje, jak dodać parametry do polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4ac62-135">Shows how to add parameters to the cmdlet.</span></span>
<span data-ttu-id="4ac62-136">Polecenie cmdlet przyjmuje jedną lub więcej nazw proces i zwraca pasujących procesów.</span><span class="sxs-lookup"><span data-stu-id="4ac62-136">The cmdlet takes one or more process names and returns the matching processes.</span></span>

### <a name="getprocesssample03"></a><span data-ttu-id="4ac62-137">GetProcessSample03</span><span class="sxs-lookup"><span data-stu-id="4ac62-137">GetProcessSample03</span></span>

<span data-ttu-id="4ac62-138">Pokazuje, jak dodać parametry, które akceptują dane wejściowe z potoku.</span><span class="sxs-lookup"><span data-stu-id="4ac62-138">Shows how to add parameters that accept input from the pipeline.</span></span>

### <a name="getprocesssample04"></a><span data-ttu-id="4ac62-139">GetProcessSample04</span><span class="sxs-lookup"><span data-stu-id="4ac62-139">GetProcessSample04</span></span>

<span data-ttu-id="4ac62-140">Pokazuje, jak obsługiwać błędy niekończące.</span><span class="sxs-lookup"><span data-stu-id="4ac62-140">Shows how to handle nonterminating errors.</span></span>

### <a name="getprocesssample05"></a><span data-ttu-id="4ac62-141">GetProcessSample05</span><span class="sxs-lookup"><span data-stu-id="4ac62-141">GetProcessSample05</span></span>

<span data-ttu-id="4ac62-142">Pokazuje, jak wyświetlić listę określonych procesów.</span><span class="sxs-lookup"><span data-stu-id="4ac62-142">Shows how to display a list of specified processes.</span></span>

### <a name="selectobject"></a><span data-ttu-id="4ac62-143">SelectObject —</span><span class="sxs-lookup"><span data-stu-id="4ac62-143">SelectObject</span></span>

<span data-ttu-id="4ac62-144">Przedstawia sposób zapisania filtru, aby wybrać tylko niektórych obiektów.</span><span class="sxs-lookup"><span data-stu-id="4ac62-144">Shows how to write a filter to select only certain objects.</span></span>

### <a name="selectstring"></a><span data-ttu-id="4ac62-145">SelectString</span><span class="sxs-lookup"><span data-stu-id="4ac62-145">SelectString</span></span>

<span data-ttu-id="4ac62-146">Pokazuje, jak na potrzeby wyszukiwania plików pod kątem określonego wzorców.</span><span class="sxs-lookup"><span data-stu-id="4ac62-146">Shows how to search files for specified patterns.</span></span>

### <a name="stopprocesssample01"></a><span data-ttu-id="4ac62-147">StopProcessSample01</span><span class="sxs-lookup"><span data-stu-id="4ac62-147">StopProcessSample01</span></span>

<span data-ttu-id="4ac62-148">Pokazuje, jak zaimplementować *PassThru* parametr i jak prośba o opinię użytkownika przez wywołania [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) i [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue) metody.</span><span class="sxs-lookup"><span data-stu-id="4ac62-148">Shows how to implement a *PassThru* parameter, and how to request user feedback by calls to the [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) and [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue) methods.</span></span>
<span data-ttu-id="4ac62-149">Określ użytkowników *PassThru* parametr, gdy chce wymusić polecenia cmdlet, aby zwrócić obiekt,</span><span class="sxs-lookup"><span data-stu-id="4ac62-149">Users specify the *PassThru* parameter when they want to force the cmdlet to return an object,</span></span>

### <a name="stopprocesssample02"></a><span data-ttu-id="4ac62-150">StopProcessSample02</span><span class="sxs-lookup"><span data-stu-id="4ac62-150">StopProcessSample02</span></span>

<span data-ttu-id="4ac62-151">Pokazuje, jak można zatrzymać określonego procesu.</span><span class="sxs-lookup"><span data-stu-id="4ac62-151">Shows how to stop a specific process.</span></span>

### <a name="stopprocesssample03"></a><span data-ttu-id="4ac62-152">StopProcessSample03</span><span class="sxs-lookup"><span data-stu-id="4ac62-152">StopProcessSample03</span></span>

<span data-ttu-id="4ac62-153">Pokazuje sposób deklarowania aliasów parametrów i sposób obsługi symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="4ac62-153">Shows how to declare aliases for parameters and how to support wildcards.</span></span>

### <a name="stopprocesssample04"></a><span data-ttu-id="4ac62-154">StopProcessSample04</span><span class="sxs-lookup"><span data-stu-id="4ac62-154">StopProcessSample04</span></span>

<span data-ttu-id="4ac62-155">Pokazuje sposób deklarowania zestawów parametrów, obiekt, który jest polecenie cmdlet przyjmuje jako dane wejściowe i jak określić domyślnego parametru skonfigurowany do używania.</span><span class="sxs-lookup"><span data-stu-id="4ac62-155">Shows how to declare parameter sets, the object that the cmdlet takes as input, and how to specify the default parameter set to use.</span></span>

## <a name="remoting-samples"></a><span data-ttu-id="4ac62-156">Przykłady usług zdalnych</span><span class="sxs-lookup"><span data-stu-id="4ac62-156">Remoting samples</span></span>

### <a name="remoterunspace01"></a><span data-ttu-id="4ac62-157">RemoteRunspace01</span><span class="sxs-lookup"><span data-stu-id="4ac62-157">RemoteRunspace01</span></span>

<span data-ttu-id="4ac62-158">Pokazuje, jak utworzyć zdalnego obszaru działania, który jest używany do ustanawiania połączenia zdalnego.</span><span class="sxs-lookup"><span data-stu-id="4ac62-158">Shows how to create a remote runspace that is used to establish a remote connection.</span></span>

### <a name="remoterunspacepool01"></a><span data-ttu-id="4ac62-159">RemoteRunspacePool01</span><span class="sxs-lookup"><span data-stu-id="4ac62-159">RemoteRunspacePool01</span></span>

<span data-ttu-id="4ac62-160">Pokazuje sposób tworzenia puli zdalnego obszaru działania oraz sposobu uruchamiania wielu poleceń, jednocześnie przy użyciu tej puli.</span><span class="sxs-lookup"><span data-stu-id="4ac62-160">Shows how to construct a remote runspace pool and how to run multiple commands concurrently by using this pool.</span></span>

### <a name="serialization01"></a><span data-ttu-id="4ac62-161">Serialization01</span><span class="sxs-lookup"><span data-stu-id="4ac62-161">Serialization01</span></span>

<span data-ttu-id="4ac62-162">Pokazuje, jak ocenić istniejącej klasy .NET i upewnij się, że informacje z wybranej właściwości publiczne tej klasy jest zachowywany między serializacji/deserializacji.</span><span class="sxs-lookup"><span data-stu-id="4ac62-162">Shows how to look at an existing .NET class and make sure that information from selected public properties of this class is preserved across serialization/deserialization.</span></span>

### <a name="serialization02"></a><span data-ttu-id="4ac62-163">Serialization02</span><span class="sxs-lookup"><span data-stu-id="4ac62-163">Serialization02</span></span>

<span data-ttu-id="4ac62-164">Pokazuje, jak ocenić istniejącej klasy .NET i upewnij się, że informacji z wystąpienia tej klasy jest zachowywany między serializacji/deserializacji, jeśli informacje nie są dostępne w publicznej właściwości klasy.</span><span class="sxs-lookup"><span data-stu-id="4ac62-164">Shows how to look at an existing .NET class and make sure that information from instance of this class is preserved across serialization/deserialization when the information is not available in public properties of the class.</span></span>

### <a name="serialization03"></a><span data-ttu-id="4ac62-165">Serialization03</span><span class="sxs-lookup"><span data-stu-id="4ac62-165">Serialization03</span></span>

<span data-ttu-id="4ac62-166">Pokazuje, jak Przyjrzyj się istniejącej klasy .NET i upewnij się, deserializacji wystąpienia tej klasy i klas pochodnych (wypełnienia) na obiekty .NET na żywo.</span><span class="sxs-lookup"><span data-stu-id="4ac62-166">Shows how to look at an existing .NET class and make sure that instances of this class and of derived classes are deserialized (rehydrated) into live .NET objects.</span></span>

## <a name="event-samples"></a><span data-ttu-id="4ac62-167">Przykłady zdarzeń</span><span class="sxs-lookup"><span data-stu-id="4ac62-167">Event samples</span></span>

### <a name="event01"></a><span data-ttu-id="4ac62-168">Event01</span><span class="sxs-lookup"><span data-stu-id="4ac62-168">Event01</span></span>

<span data-ttu-id="4ac62-169">Pokazuje, jak utworzyć polecenie cmdlet służące do rejestrowania zdarzeń pochodząca od ObjectEventRegistrationBase.</span><span class="sxs-lookup"><span data-stu-id="4ac62-169">Shows how to create a cmdlet for event registration by deriving from ObjectEventRegistrationBase.</span></span>

### <a name="event02"></a><span data-ttu-id="4ac62-170">Event02</span><span class="sxs-lookup"><span data-stu-id="4ac62-170">Event02</span></span>

<span data-ttu-id="4ac62-171">Pokazuje, jak do pokazuje, jak otrzymywać powiadomienia zdarzenia programu Windows PowerShell, które są generowane na komputerach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="4ac62-171">Shows how to shows how to receive notifications of Windows PowerShell events that are generated on remote computers.</span></span>
<span data-ttu-id="4ac62-172">Zdarzenie PSEventReceived udostępniane za pośrednictwem [obszarem działania](/dotnet/api/system.management.automation.runspaces.runspace) klasy.</span><span class="sxs-lookup"><span data-stu-id="4ac62-172">It uses the PSEventReceived event exposed through the [Runspace](/dotnet/api/system.management.automation.runspaces.runspace) class.</span></span>

## <a name="hosting-application-samples"></a><span data-ttu-id="4ac62-173">Przykłady aplikacji hostingu</span><span class="sxs-lookup"><span data-stu-id="4ac62-173">Hosting application samples</span></span>

### <a name="runspace01"></a><span data-ttu-id="4ac62-174">Runspace01</span><span class="sxs-lookup"><span data-stu-id="4ac62-174">Runspace01</span></span>

<span data-ttu-id="4ac62-175">Ilustruje sposób używania [PowerShell](/dotnet/api/system.management.automation.powershell) klasy, aby uruchomić [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) polecenia cmdlet synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="4ac62-175">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously.</span></span>
<span data-ttu-id="4ac62-176">[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) polecenie cmdlet zwraca [procesu](https://technet.microsoft.com/library/system.diagnostics.process.aspx) obiektów dla wszystkich procesów działających na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="4ac62-176">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer.</span></span>

### <a name="runspace02"></a><span data-ttu-id="4ac62-177">Runspace02</span><span class="sxs-lookup"><span data-stu-id="4ac62-177">Runspace02</span></span>

<span data-ttu-id="4ac62-178">Ilustruje sposób używania [PowerShell](/dotnet/api/system.management.automation.powershell) klasy, aby uruchomić [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) i [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) poleceń cmdlet synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="4ac62-178">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span>
<span data-ttu-id="4ac62-179">[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) polecenie cmdlet zwraca [procesu](https://technet.microsoft.com/library/system.diagnostics.process.aspx) obiektów dla wszystkich procesów działających na komputerze lokalnym i `Sort-Object` sortuje obiekty, w zależności od ich [identyfikator](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) Właściwość.</span><span class="sxs-lookup"><span data-stu-id="4ac62-179">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer, and the `Sort-Object` sorts the objects based on their [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) property.</span></span>
<span data-ttu-id="4ac62-180">Wyniki tych poleceń jest wyświetlana przy użyciu [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) kontroli.</span><span class="sxs-lookup"><span data-stu-id="4ac62-180">The results of these commands is displayed by using a [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) control.</span></span>

### <a name="runspace03"></a><span data-ttu-id="4ac62-181">Runspace03</span><span class="sxs-lookup"><span data-stu-id="4ac62-181">Runspace03</span></span>

<span data-ttu-id="4ac62-182">Ilustruje sposób używania [PowerShell](/dotnet/api/system.management.automation.powershell) klasy, aby uruchomić skrypt synchronicznie i sposób obsługi błędy niepowodujące.</span><span class="sxs-lookup"><span data-stu-id="4ac62-182">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run a script synchronously, and how to handle non-terminating errors.</span></span>
<span data-ttu-id="4ac62-183">Skrypt otrzymuje listę nazw procesu, a następnie pobierze te procesy.</span><span class="sxs-lookup"><span data-stu-id="4ac62-183">The script receives a list of process names and then retrieves those processes.</span></span>
<span data-ttu-id="4ac62-184">Wyniki skryptu, między innymi niepowodujące błędy, które zostały wygenerowane podczas uruchamiania skryptu, są wyświetlane w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="4ac62-184">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

### <a name="runspace04"></a><span data-ttu-id="4ac62-185">Runspace04</span><span class="sxs-lookup"><span data-stu-id="4ac62-185">Runspace04</span></span>

<span data-ttu-id="4ac62-186">Ilustruje sposób używania [PowerShell](/dotnet/api/system.management.automation.powershell) klasy do uruchamiania poleceń oraz jak catch kończący błędów, które są zgłaszane w przypadku uruchamiania polecenia.</span><span class="sxs-lookup"><span data-stu-id="4ac62-186">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span>
<span data-ttu-id="4ac62-187">Dwa polecenia są uruchamiane, a ostatnie polecenie jest przekazany argument parametru, który jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="4ac62-187">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span>
<span data-ttu-id="4ac62-188">W rezultacie żadne obiekty nie są zwracane i generowany jest błąd powodujący zakończenie.</span><span class="sxs-lookup"><span data-stu-id="4ac62-188">As a result, no objects are returned and a terminating error is thrown.</span></span>

### <a name="runspace05"></a><span data-ttu-id="4ac62-189">Runspace05</span><span class="sxs-lookup"><span data-stu-id="4ac62-189">Runspace05</span></span>

<span data-ttu-id="4ac62-190">Przedstawiono sposób dodawania przystawki do [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) obiekt cmdlet przystawki jest dostępne po otwarciu obszaru działania.</span><span class="sxs-lookup"><span data-stu-id="4ac62-190">Shows how to add a snap-in to an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span>
<span data-ttu-id="4ac62-191">Przystawka udostępnia polecenia cmdlet Get-Proc (zdefiniowane przez [GetProcessSample01 przykładowe](https://technet.microsoft.com/library/ff602028.aspx)) uruchamiane synchronicznie przy użyciu [PowerShell](/dotnet/api/system.management.automation.powershell) obiektu.</span><span class="sxs-lookup"><span data-stu-id="4ac62-191">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](https://technet.microsoft.com/library/ff602028.aspx)) that is run synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace06"></a><span data-ttu-id="4ac62-192">Runspace06</span><span class="sxs-lookup"><span data-stu-id="4ac62-192">Runspace06</span></span>

<span data-ttu-id="4ac62-193">Przedstawiono sposób dodawania modułu, aby [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) obiekt moduł jest załadowany po otwarciu obszaru działania.</span><span class="sxs-lookup"><span data-stu-id="4ac62-193">Shows how to add a module to an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object so that the module is loaded when the runspace is opened.</span></span>
<span data-ttu-id="4ac62-194">Moduł zawiera polecenia cmdlet Get-Proc (zdefiniowane przez [przykładowe GetProcessSample02](https://technet.microsoft.com/library/ff602027.aspx)) uruchamiane synchronicznie przy użyciu [PowerShell](/dotnet/api/system.management.automation.powershell) obiektu.</span><span class="sxs-lookup"><span data-stu-id="4ac62-194">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](https://technet.microsoft.com/library/ff602027.aspx)) that is run synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace07"></a><span data-ttu-id="4ac62-195">Runspace07</span><span class="sxs-lookup"><span data-stu-id="4ac62-195">Runspace07</span></span>

<span data-ttu-id="4ac62-196">Pokazuje, jak utworzyć obszar działania, a następnie użyj tego obszaru działania na dwa polecenia cmdlet były uruchamiane synchronicznie przy użyciu [PowerShell](/dotnet/api/system.management.automation.powershell) obiektu.</span><span class="sxs-lookup"><span data-stu-id="4ac62-196">Shows how to create a runspace, and then use that runspace to run two cmdlets synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace08"></a><span data-ttu-id="4ac62-197">Runspace08</span><span class="sxs-lookup"><span data-stu-id="4ac62-197">Runspace08</span></span>

<span data-ttu-id="4ac62-198">Pokazuje, jak dodać do potoku z poleceń i argumentów [PowerShell](/dotnet/api/system.management.automation.powershell) obiektu i jak polecenia były uruchamiane synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="4ac62-198">Shows how to add commands and arguments to the pipeline of a [PowerShell](/dotnet/api/system.management.automation.powershell) object and how to run the commands synchronously.</span></span>

### <a name="runspace09"></a><span data-ttu-id="4ac62-199">Runspace09</span><span class="sxs-lookup"><span data-stu-id="4ac62-199">Runspace09</span></span>

<span data-ttu-id="4ac62-200">Pokazuje, jak dodać skrypt do potoku [PowerShell](/dotnet/api/system.management.automation.powershell) obiektu oraz sposobu uruchamiania skryptu asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="4ac62-200">Shows how to add a script to the pipeline of a [PowerShell](/dotnet/api/system.management.automation.powershell) object and how to run the script asynchronously.</span></span>
<span data-ttu-id="4ac62-201">Zdarzenia są używane do obsługi danych wyjściowych skryptu.</span><span class="sxs-lookup"><span data-stu-id="4ac62-201">Events are used to handle the output of the script.</span></span>

### <a name="runspace10"></a><span data-ttu-id="4ac62-202">Runspace10</span><span class="sxs-lookup"><span data-stu-id="4ac62-202">Runspace10</span></span>

<span data-ttu-id="4ac62-203">Pokazuje, jak utworzyć domyślny początkowy stan sesji, jak dodać polecenia cmdlet, aby [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate), jak utworzyć obszar działania, używającej stanu sesji początkowej i jak uruchamiać polecenia przy użyciu [PowerShell](/dotnet/api/system.management.automation.powershell)obiektu.</span><span class="sxs-lookup"><span data-stu-id="4ac62-203">Shows how to create a default initial session state, how to add a cmdlet to the [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate), how to create a runspace that uses the initial session state, and how to run the command by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace11"></a><span data-ttu-id="4ac62-204">Runspace11</span><span class="sxs-lookup"><span data-stu-id="4ac62-204">Runspace11</span></span>

<span data-ttu-id="4ac62-205">Ilustruje sposób używania [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) klasy, aby utworzyć polecenie proxy, który wywołuje istniejące polecenia cmdlet, ale ogranicza zestaw dostępnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="4ac62-205">Shows how to use the [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) class to create a proxy command that calls an existing cmdlet, but restricts the set of available parameters.</span></span>
<span data-ttu-id="4ac62-206">Polecenie proxy jest dodawane do stanu sesji początkowej, która służy do tworzenia ograniczonego obszaru działania.</span><span class="sxs-lookup"><span data-stu-id="4ac62-206">The proxy command is then added to an initial session state that is used to create a constrained runspace.</span></span>
<span data-ttu-id="4ac62-207">Oznacza to, że użytkownik ma dostęp funkcjonalność polecenia cmdlet tylko za pomocą polecenia proxy.</span><span class="sxs-lookup"><span data-stu-id="4ac62-207">This means that the user can access the functionality of the cmdlet only through the proxy command.</span></span>

### <a name="powershell01"></a><span data-ttu-id="4ac62-208">PowerShell01</span><span class="sxs-lookup"><span data-stu-id="4ac62-208">PowerShell01</span></span>

<span data-ttu-id="4ac62-209">Pokazuje, jak utworzyć za pomocą ograniczonego obszaru działania [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) obiektu.</span><span class="sxs-lookup"><span data-stu-id="4ac62-209">Shows how to create a constrained runspace using an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object.</span></span>

### <a name="powershell02"></a><span data-ttu-id="4ac62-210">PowerShell02</span><span class="sxs-lookup"><span data-stu-id="4ac62-210">PowerShell02</span></span>

<span data-ttu-id="4ac62-211">Pokazuje, jak użyć puli obszarem działania w celu jednoczesnego uruchamiania wielu poleceń.</span><span class="sxs-lookup"><span data-stu-id="4ac62-211">Shows how to use a runspace pool to run multiple commands concurrently.</span></span>

## <a name="host-samples"></a><span data-ttu-id="4ac62-212">Przykładowe pliki hosta</span><span class="sxs-lookup"><span data-stu-id="4ac62-212">Host samples</span></span>

### <a name="host01"></a><span data-ttu-id="4ac62-213">Host01</span><span class="sxs-lookup"><span data-stu-id="4ac62-213">Host01</span></span>

<span data-ttu-id="4ac62-214">Pokazuje sposób implementacji aplikacji hosta, który używa niestandardowego hosta.</span><span class="sxs-lookup"><span data-stu-id="4ac62-214">Shows how to implement a host application that uses a custom host.</span></span>
<span data-ttu-id="4ac62-215">W tym przykładzie zostanie utworzony obszar działania, który używa niestandardowego hosta a następnie [PowerShell](/dotnet/api/system.management.automation.powershell) interfejsu API jest używane do uruchamiania skryptu, który wywołuje "Zamknij".</span><span class="sxs-lookup"><span data-stu-id="4ac62-215">In this sample a runspace is created that uses the custom host, and then the [PowerShell](/dotnet/api/system.management.automation.powershell) API is used to run a script that calls "exit".</span></span>
<span data-ttu-id="4ac62-216">Aplikacja hosta następnie analizuje dane wyjściowe skryptu i wyświetla wyniki.</span><span class="sxs-lookup"><span data-stu-id="4ac62-216">The host application then looks at the output of the script and prints out the results.</span></span>

### <a name="host02"></a><span data-ttu-id="4ac62-217">Host02</span><span class="sxs-lookup"><span data-stu-id="4ac62-217">Host02</span></span>

<span data-ttu-id="4ac62-218">Pokazuje, jak napisać aplikację hosta, która używa środowiska wykonawczego programu Windows PowerShell, oraz implementacji niestandardowego hosta.</span><span class="sxs-lookup"><span data-stu-id="4ac62-218">Shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span>
<span data-ttu-id="4ac62-219">Aplikacja hosta ustawia kulturę hosta na język niemiecki, przebiegów [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) polecenia cmdlet i wyświetla wynik jako użytkownik je zobaczy przy użyciu pwrsh.exe, a następnie Drukuje bieżące data i godzina w języku niemieckim.</span><span class="sxs-lookup"><span data-stu-id="4ac62-219">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them by using pwrsh.exe, and then prints out the current data and time in German.</span></span>

### <a name="host03"></a><span data-ttu-id="4ac62-220">Host03</span><span class="sxs-lookup"><span data-stu-id="4ac62-220">Host03</span></span>

<span data-ttu-id="4ac62-221">Pokazuje, jak utworzyć aplikację interaktywnego hosta opartego na konsoli, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli.</span><span class="sxs-lookup"><span data-stu-id="4ac62-221">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

### <a name="host04"></a><span data-ttu-id="4ac62-222">Host04</span><span class="sxs-lookup"><span data-stu-id="4ac62-222">Host04</span></span>

<span data-ttu-id="4ac62-223">Pokazuje, jak utworzyć aplikację interaktywnego hosta opartego na konsoli, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli.</span><span class="sxs-lookup"><span data-stu-id="4ac62-223">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="4ac62-224">Ta aplikacja hosta obsługuje również wyświetlania monitów, które umożliwiają użytkownikom określić wiele opcji do wyboru.</span><span class="sxs-lookup"><span data-stu-id="4ac62-224">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

### <a name="host05"></a><span data-ttu-id="4ac62-225">Host05</span><span class="sxs-lookup"><span data-stu-id="4ac62-225">Host05</span></span>

<span data-ttu-id="4ac62-226">Pokazuje, jak utworzyć aplikację interaktywnego hosta opartego na konsoli, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli.</span><span class="sxs-lookup"><span data-stu-id="4ac62-226">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="4ac62-227">Ta aplikacja hosta obsługuje również połączenia z komputerami zdalnymi przy użyciu [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) i [PsSession zakończenia](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4ac62-227">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets.</span></span>

### <a name="host06"></a><span data-ttu-id="4ac62-228">Host06</span><span class="sxs-lookup"><span data-stu-id="4ac62-228">Host06</span></span>

<span data-ttu-id="4ac62-229">Pokazuje, jak utworzyć aplikację interaktywnego hosta opartego na konsoli, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli.</span><span class="sxs-lookup"><span data-stu-id="4ac62-229">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="4ac62-230">Ponadto w przykładzie użyto interfejsów API Tokenizatora określić kolor tekstu, wprowadzonej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4ac62-230">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="provider-samples"></a><span data-ttu-id="4ac62-231">Przykłady dostawcy</span><span class="sxs-lookup"><span data-stu-id="4ac62-231">Provider samples</span></span>

### <a name="accessdbprovidersample01"></a><span data-ttu-id="4ac62-232">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="4ac62-232">AccessDBProviderSample01</span></span>

<span data-ttu-id="4ac62-233">Pokazuje sposób deklarowania klas dostawcy, który pochodzi bezpośrednio z [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider) klasy.</span><span class="sxs-lookup"><span data-stu-id="4ac62-233">Shows how to declare a provider class that derives directly from the [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider) class.</span></span>
<span data-ttu-id="4ac62-234">Została ona tutaj uwzględniona tylko w przypadku informacje były kompletne.</span><span class="sxs-lookup"><span data-stu-id="4ac62-234">It is included here only for completeness.</span></span>

### <a name="accessdbprovidersample02"></a><span data-ttu-id="4ac62-235">AccessDBProviderSample02</span><span class="sxs-lookup"><span data-stu-id="4ac62-235">AccessDBProviderSample02</span></span>

<span data-ttu-id="4ac62-236">Pokazuje, jak zastąpić [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) i [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) metody umożliwiające obsługę wywołań `New-PSDrive` i `Remove-PSDrive` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4ac62-236">Shows how to overwrite the [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) and [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) methods to support calls to the `New-PSDrive` and `Remove-PSDrive` cmdlets.</span></span>
<span data-ttu-id="4ac62-237">Klasa dostawcy, w tym przykładzie pochodzi z [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider) klasy.</span><span class="sxs-lookup"><span data-stu-id="4ac62-237">The provider class in this sample derives from the [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider) class.</span></span>

### <a name="accessdbprovidersample03"></a><span data-ttu-id="4ac62-238">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="4ac62-238">AccessDBProviderSample03</span></span>

<span data-ttu-id="4ac62-239">Pokazuje, jak zastąpić [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) i [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) metody umożliwiające obsługę wywołań `Get-Item` i `Set-Item` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4ac62-239">Shows how to overwrite the [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) and [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span>
<span data-ttu-id="4ac62-240">Klasa dostawcy, w tym przykładzie pochodzi z [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) klasy.</span><span class="sxs-lookup"><span data-stu-id="4ac62-240">The provider class in this sample derives from the [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample04"></a><span data-ttu-id="4ac62-241">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="4ac62-241">AccessDBProviderSample04</span></span>

<span data-ttu-id="4ac62-242">Pokazuje, jak zastąpić obsługuje wywołań metod kontener `Copy-Item`, `Get-ChildItem`, `New-Item`, i `Remove-Item` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4ac62-242">Shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span>
<span data-ttu-id="4ac62-243">Metody te powinny być zrealizowane, gdy magazyn danych zawiera elementy, które są kontenery.</span><span class="sxs-lookup"><span data-stu-id="4ac62-243">These methods should be implemented when the data store contains items that are containers.</span></span>
<span data-ttu-id="4ac62-244">Kontener jest grupą elementów podrzędnych w ramach wspólnego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="4ac62-244">A container is a group of child items under a common parent item.</span></span>
<span data-ttu-id="4ac62-245">Klasa dostawcy, w tym przykładzie pochodzi z [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) klasy.</span><span class="sxs-lookup"><span data-stu-id="4ac62-245">The provider class in this sample derives from the [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample05"></a><span data-ttu-id="4ac62-246">AccessDBProviderSample05</span><span class="sxs-lookup"><span data-stu-id="4ac62-246">AccessDBProviderSample05</span></span>

<span data-ttu-id="4ac62-247">Pokazuje, jak zastąpić obsługuje wywołań metod kontener `Move-Item` i `Join-Path` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4ac62-247">Shows how to overwrite container methods to support calls to the `Move-Item` and `Join-Path` cmdlets.</span></span>
<span data-ttu-id="4ac62-248">Metody te powinny być zrealizowane, gdy użytkownik chce przenieść elementy znajdujące się w kontenerze, a Magazyn danych zawiera zagnieżdżone kontenery.</span><span class="sxs-lookup"><span data-stu-id="4ac62-248">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span>
<span data-ttu-id="4ac62-249">Klasa dostawcy, w tym przykładzie pochodzi z [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) klasy.</span><span class="sxs-lookup"><span data-stu-id="4ac62-249">The provider class in this sample derives from the [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample06"></a><span data-ttu-id="4ac62-250">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="4ac62-250">AccessDBProviderSample06</span></span>

<span data-ttu-id="4ac62-251">Pokazuje, jak i Zastąp zawartość metody umożliwiające obsługę wywołań `Clear-Content`, `Get-Content`, i `Set-Content` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4ac62-251">Shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span>
<span data-ttu-id="4ac62-252">Te metody powinny zostać wdrożone, gdy użytkownik musi zarządzać zawartością elementów w magazynie danych.</span><span class="sxs-lookup"><span data-stu-id="4ac62-252">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span>
<span data-ttu-id="4ac62-253">Klasa dostawcy, w tym przykładzie pochodzi z [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) klasy która implementuje [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4ac62-253">The provider class in this sample derives from the [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) class, and it implements the [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) interface.</span></span>