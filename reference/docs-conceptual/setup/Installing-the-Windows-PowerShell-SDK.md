---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: Instalowanie zestawu SDK programu PowerShell systemu Windows
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: c6acba828e469e716c80603ec2432176652a7280
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2017
---
# <a name="installing-the-windows-powershell-sdk"></a><span data-ttu-id="a9011-103">Instalowanie zestawu SDK programu PowerShell systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a9011-103">Installing the Windows PowerShell SDK</span></span>

<span data-ttu-id="a9011-104">Poniższy temat zawiera opis sposobu instalowania zestawu SDK programu PowerShell w różnych wersjach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a9011-104">The following topic describes how to install the PowerShell SDK on different versions of Windows.</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a><span data-ttu-id="a9011-105">Instalowanie programu Windows PowerShell 3.0 SDK dla systemu Windows 8 i Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="a9011-105">Installing Windows PowerShell 3.0 SDK for Windows 8 and Windows Server 2012</span></span>

<span data-ttu-id="a9011-106">Program Windows PowerShell 3.0 jest automatycznie instalowany z systemem Windows 8 i Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="a9011-106">Windows PowerShell 3.0 is automatically installed with Windows 8 and Windows Server 2012.</span></span>
<span data-ttu-id="a9011-107">Ponadto można pobrać i zainstalować zestawów odwołań dla programu Windows PowerShell 3.0 w ramach zestawu SDK systemu Windows 8.</span><span class="sxs-lookup"><span data-stu-id="a9011-107">In addition, you can download and install the reference assemblies for Windows PowerShell 3.0 as part of the Windows 8 SDK.</span></span>
<span data-ttu-id="a9011-108">Te zestawy pozwalają na zapis poleceń cmdlet, dostawców i programy hosta dla programu Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="a9011-108">These assemblies allow you to write cmdlets, providers, and host programs for Windows PowerShell 3.0.</span></span>
<span data-ttu-id="a9011-109">Podczas instalowania zestawu SDK systemu Windows dla systemu Windows 8, zestawy programu Windows PowerShell są automatycznie instalowane w folderze zestawu odwołania w \Program plików (x86) \Reference Assemblies\Microsoft\WindowsPowerShell\3.0.</span><span class="sxs-lookup"><span data-stu-id="a9011-109">When you install the Windows SDK for Windows 8, the Windows PowerShell assemblies are automatically installed in the reference assembly folder, in \Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0.</span></span>
<span data-ttu-id="a9011-110">Aby uzyskać więcej informacji, zobacz [witryny pobierania systemu Windows 8 SDK](http://msdn.microsoft.com/windows/hardware/hh852363.aspx).</span><span class="sxs-lookup"><span data-stu-id="a9011-110">For more information, see the [Windows 8 SDK download site](http://msdn.microsoft.com/windows/hardware/hh852363.aspx).</span></span>
<span data-ttu-id="a9011-111">Przykłady kodu dla środowiska Windows PowerShell są także dostępne w Centrum opracowywania rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="a9011-111">Windows PowerShell code samples are also available on the Development Center.</span></span>
<span data-ttu-id="a9011-112">Aby uzyskać więcej informacji, zobacz strony przykładowego kodu na [witryny Centrum deweloperów](http://code.msdn.microsoft.com/windowsdesktop/).</span><span class="sxs-lookup"><span data-stu-id="a9011-112">For more information, see the Desktop code sample page on the [Dev center site](http://code.msdn.microsoft.com/windowsdesktop/).</span></span>

<span data-ttu-id="a9011-113">Ponadto program Windows PowerShell 3.0 jest wstecznie zgodna z systemem Windows PowerShell 2.0 SDK, która obejmuje określonej liczby próbek kodu.</span><span class="sxs-lookup"><span data-stu-id="a9011-113">In addition, Windows PowerShell 3.0 is backwards-compatible with the Windows PowerShell 2.0 SDK, which includes a number of code samples.</span></span>
<span data-ttu-id="a9011-114">Aby uzyskać więcej informacji o sposobie pobrania zestawu SDK systemu Windows PowerShell 2.0 zobacz poniżej.</span><span class="sxs-lookup"><span data-stu-id="a9011-114">For more information on how to download the Windows PowerShell 2.0 SDK, see below.</span></span>
<span data-ttu-id="a9011-115">(Należy pamiętać, przykłady kodu 2.0 są zgodne z systemem Windows 8 i Windows PowerShell 3.0, można zainstalować program Windows PowerShell 2.0 na platformie Windows 8).</span><span class="sxs-lookup"><span data-stu-id="a9011-115">(Note that while the 2.0 code samples are compatible with Windows 8 and Windows PowerShell 3.0, you cannot install Windows PowerShell 2.0 on a Windows 8 platform.)</span></span>

##<a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a><span data-ttu-id="a9011-116">Instalowanie programu Windows PowerShell 3.0 SDK dla systemu Windows 7 i Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="a9011-116">Installing Windows PowerShell 3.0 SDK for Windows 7 and Windows Server 2008 R2</span></span>

<span data-ttu-id="a9011-117">Windows 7 i Windows Server 2008 R2 automatycznie ma zainstalowaną środowiska PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="a9011-117">Windows 7 and Windows Server 2008 R2 automatically have PowerShell 2.0 installed.</span></span>
<span data-ttu-id="a9011-118">Ponadto w tych systemach można zainstalować programu PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="a9011-118">In addition, you can install PowerShell 3.0 on these systems.</span></span>
<span data-ttu-id="a9011-119">(Aby uzyskać więcej informacji, zobacz [Instalowanie programu Windows PowerShell](Installing-Windows-PowerShell.md).).</span><span class="sxs-lookup"><span data-stu-id="a9011-119">(For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).).</span></span>
<span data-ttu-id="a9011-120">Zgodnie z powyższym opisem można także zainstalować zestawu SDK systemu Windows 8, Windows 7 i Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="a9011-120">As described above, you can also install the Windows 8 SDK on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a><span data-ttu-id="a9011-121">Instalowanie programu Windows PowerShell 2.0 SDK dla systemu Windows 7, Vista, XP, Server 2003 i Server 2008</span><span class="sxs-lookup"><span data-stu-id="a9011-121">Installing Windows PowerShell 2.0 SDK for Windows 7, Vista, XP, Server 2003, and Server 2008</span></span>

<span data-ttu-id="a9011-122">Windows PowerShell 2.0 SDK zawiera zestawy referencyjne wymagane do zapisywania poleceń cmdlet, dostawców i hostingu aplikacji i zapewnia C# przykładowy kod, który może służyć jako punkt początkowy, po rozpoczęciu pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="a9011-122">The Windows PowerShell 2.0 SDK provides the reference assemblies needed to write cmdlets, providers, and hosting applications, and it provides C# sample code that can be used as the starting point when you begin writing code.</span></span>

<span data-ttu-id="a9011-123">Aby zainstalować zestaw SDK, zobacz [programu Windows PowerShell 2.0 SDK](http://go.microsoft.com/fwlink/?LinkId=184611).</span><span class="sxs-lookup"><span data-stu-id="a9011-123">To install this SDK, see [Windows PowerShell 2.0 SDK](http://go.microsoft.com/fwlink/?LinkId=184611).</span></span>

## <a name="reference-assemblies"></a><span data-ttu-id="a9011-124">Zestawy referencyjne</span><span class="sxs-lookup"><span data-stu-id="a9011-124">Reference assemblies</span></span>

<span data-ttu-id="a9011-125">Zestawy referencyjne są domyślnie instalowane w następującej lokalizacji: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span><span class="sxs-lookup"><span data-stu-id="a9011-125">Reference assemblies are installed in the following location by default: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span></span>

> <span data-ttu-id="a9011-126">**Uwaga**: nie można załadować kodu, który jest skompilowany zestawy Windows PowerShell 2.0 do instalacji programu Windows PowerShell w wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="a9011-126">**Note**: Code that is compiled against the Windows PowerShell 2.0 assemblies cannot be loaded into Windows PowerShell 1.0 installations.</span></span>
><span data-ttu-id="a9011-127">Jednak kod, który jest skompilowany zestawy Windows PowerShell 1.0 mogą zostać załadowane do instalacji programu Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="a9011-127">However, code that is compiled against the Windows PowerShell 1.0 assemblies can be loaded into Windows PowerShell 2.0 installations.</span></span>

## <a name="samples"></a><span data-ttu-id="a9011-128">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a9011-128">Samples</span></span>

<span data-ttu-id="a9011-129">Przykłady kodu są domyślnie instalowane w następującej lokalizacji: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span><span class="sxs-lookup"><span data-stu-id="a9011-129">Code samples are installed in the following location by default: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span></span>

<span data-ttu-id="a9011-130">Każda próbka jest krótki opis można znaleźć w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="a9011-130">The following sections provide a brief description of what each sample does.</span></span>

## <a name="cmdlet-samples"></a><span data-ttu-id="a9011-131">Polecenia cmdlet próbek</span><span class="sxs-lookup"><span data-stu-id="a9011-131">Cmdlet samples</span></span>
<span data-ttu-id="a9011-132">**GetProcessSample01**</span><span class="sxs-lookup"><span data-stu-id="a9011-132">**GetProcessSample01**</span></span>

<span data-ttu-id="a9011-133">Przedstawia sposób zapisania prostego polecenia cmdlet, które pobiera wszystkie procesy na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="a9011-133">Shows how to write a simple cmdlet that gets all the processes on the local computer.</span></span>

<span data-ttu-id="a9011-134">**GetProcessSample02**</span><span class="sxs-lookup"><span data-stu-id="a9011-134">**GetProcessSample02**</span></span>

<span data-ttu-id="a9011-135">Przedstawiono sposób dodawania parametrów do polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a9011-135">Shows how to add parameters to the cmdlet.</span></span>
<span data-ttu-id="a9011-136">Polecenie cmdlet przyjmuje jeden lub więcej nazw procesu i zwraca dopasowywania procesów.</span><span class="sxs-lookup"><span data-stu-id="a9011-136">The cmdlet takes one or more process names and returns the matching processes.</span></span>

<span data-ttu-id="a9011-137">**GetProcessSample03**</span><span class="sxs-lookup"><span data-stu-id="a9011-137">**GetProcessSample03**</span></span>

<span data-ttu-id="a9011-138">Przedstawiono sposób dodawania parametrów, które akceptuje dane wejściowe z potoku.</span><span class="sxs-lookup"><span data-stu-id="a9011-138">Shows how to add parameters that accept input from the pipeline.</span></span>

<span data-ttu-id="a9011-139">**GetProcessSample04**</span><span class="sxs-lookup"><span data-stu-id="a9011-139">**GetProcessSample04**</span></span>

<span data-ttu-id="a9011-140">Przedstawia sposób obsługi błędów nonterminating.</span><span class="sxs-lookup"><span data-stu-id="a9011-140">Shows how to handle nonterminating errors.</span></span>

<span data-ttu-id="a9011-141">**GetProcessSample05**</span><span class="sxs-lookup"><span data-stu-id="a9011-141">**GetProcessSample05**</span></span>

<span data-ttu-id="a9011-142">Pokazuje, jak można wyświetlić listę określonych procesów.</span><span class="sxs-lookup"><span data-stu-id="a9011-142">Shows how to display a list of specified processes.</span></span>

<span data-ttu-id="a9011-143">**SelectObject**</span><span class="sxs-lookup"><span data-stu-id="a9011-143">**SelectObject**</span></span>

<span data-ttu-id="a9011-144">Przedstawia sposób zapisania filtr, aby wybrać tylko niektórych obiektów.</span><span class="sxs-lookup"><span data-stu-id="a9011-144">Shows how to write a filter to select only certain objects.</span></span>

<span data-ttu-id="a9011-145">**SelectString**</span><span class="sxs-lookup"><span data-stu-id="a9011-145">**SelectString**</span></span>

<span data-ttu-id="a9011-146">Przedstawiono sposób wyszukiwania plików określonych wzorców.</span><span class="sxs-lookup"><span data-stu-id="a9011-146">Shows how to search files for specified patterns.</span></span>

<span data-ttu-id="a9011-147">**StopProcessSample01**</span><span class="sxs-lookup"><span data-stu-id="a9011-147">**StopProcessSample01**</span></span>

<span data-ttu-id="a9011-148">Pokazuje, jak wdrożyć *PassThru* parametr i jak utworzyć żądanie opinii użytkowników wywołań [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) i [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="a9011-148">Shows how to implement a *PassThru* parameter, and how to request user feedback by calls to the [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) and [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx) methods.</span></span>
<span data-ttu-id="a9011-149">Określ użytkowników *PassThru* parametru, jeśli chcą, aby wymusić polecenia cmdlet, aby zwrócić obiekt,</span><span class="sxs-lookup"><span data-stu-id="a9011-149">Users specify the *PassThru* parameter when they want to force the cmdlet to return an object,</span></span>

<span data-ttu-id="a9011-150">**StopProcessSample02**</span><span class="sxs-lookup"><span data-stu-id="a9011-150">**StopProcessSample02**</span></span>

<span data-ttu-id="a9011-151">Pokazuje, jak zatrzymać określonego procesu.</span><span class="sxs-lookup"><span data-stu-id="a9011-151">Shows how to stop a specific process.</span></span>

<span data-ttu-id="a9011-152">**StopProcessSample03**</span><span class="sxs-lookup"><span data-stu-id="a9011-152">**StopProcessSample03**</span></span>

<span data-ttu-id="a9011-153">Pokazuje sposób zadeklarować aliasów dla parametrów i obsługuje symbole wieloznaczne.</span><span class="sxs-lookup"><span data-stu-id="a9011-153">Shows how to declare aliases for parameters and how to support wildcards.</span></span>

<span data-ttu-id="a9011-154">**StopProcessSample04**</span><span class="sxs-lookup"><span data-stu-id="a9011-154">**StopProcessSample04**</span></span>

<span data-ttu-id="a9011-155">Pokazuje, jak zadeklarować zestawów parametrów obiektu cmdlet przyjmuje jako dane wejściowe i sposobu określania domyślnego parametru zestaw do użycia.</span><span class="sxs-lookup"><span data-stu-id="a9011-155">Shows how to declare parameter sets, the object that the cmdlet takes as input, and how to specify the default parameter set to use.</span></span>

## <a name="remoting-samples"></a><span data-ttu-id="a9011-156">Przykłady usługi zdalne</span><span class="sxs-lookup"><span data-stu-id="a9011-156">Remoting samples</span></span>

<span data-ttu-id="a9011-157">**RemoteRunspace01**</span><span class="sxs-lookup"><span data-stu-id="a9011-157">**RemoteRunspace01**</span></span>

<span data-ttu-id="a9011-158">Przedstawia sposób tworzenia zdalnego obszaru działania, który jest używany do ustanawiania połączenia zdalnego.</span><span class="sxs-lookup"><span data-stu-id="a9011-158">Shows how to create a remote runspace that is used to establish a remote connection.</span></span>

<span data-ttu-id="a9011-159">**RemoteRunspacePool01**</span><span class="sxs-lookup"><span data-stu-id="a9011-159">**RemoteRunspacePool01**</span></span>

<span data-ttu-id="a9011-160">Pokazuje, jak utworzyć pulę zdalnego obszaru działania i jak równoczesne uruchamianie wielu poleceń za pomocą tej puli.</span><span class="sxs-lookup"><span data-stu-id="a9011-160">Shows how to construct a remote runspace pool and how to run multiple commands concurrently by using this pool.</span></span>

<span data-ttu-id="a9011-161">**Serialization01**</span><span class="sxs-lookup"><span data-stu-id="a9011-161">**Serialization01**</span></span>

<span data-ttu-id="a9011-162">Pokazuje, jak sprawdzić w istniejącej klasy .NET, a następnie upewnij się, że informacje z wybranej właściwości publiczne tej klasy jest zachowana w serializacji/deserializacji.</span><span class="sxs-lookup"><span data-stu-id="a9011-162">Shows how to look at an existing .NET class and make sure that information from selected public properties of this class is preserved across serialization/deserialization.</span></span>

<span data-ttu-id="a9011-163">**Serialization02**</span><span class="sxs-lookup"><span data-stu-id="a9011-163">**Serialization02**</span></span>

<span data-ttu-id="a9011-164">Przedstawia sposób Spójrz na istniejącej klasy .NET i upewnij się, że informacje z wystąpienia tej klasy jest zachowywanie między serializacji/deserializacji podczas informacje nie są dostępne w publicznej właściwości klasy.</span><span class="sxs-lookup"><span data-stu-id="a9011-164">Shows how to look at an existing .NET class and make sure that information from instance of this class is preserved across serialization/deserialization when the information is not available in public properties of the class.</span></span>

<span data-ttu-id="a9011-165">**Serialization03**</span><span class="sxs-lookup"><span data-stu-id="a9011-165">**Serialization03**</span></span>

<span data-ttu-id="a9011-166">Przedstawia sposób Spójrz na istniejącej klasy .NET i upewnij się, że zdeserializować wystąpienia tej klasy i klas pochodnych (rehydrated) na żywo obiekty .NET.</span><span class="sxs-lookup"><span data-stu-id="a9011-166">Shows how to look at an existing .NET class and make sure that instances of this class and of derived classes are deserialized (rehydrated) into live .NET objects.</span></span>

## <a name="event-samples"></a><span data-ttu-id="a9011-167">Przykłady zdarzeń</span><span class="sxs-lookup"><span data-stu-id="a9011-167">Event samples</span></span>

<span data-ttu-id="a9011-168">**Event01**</span><span class="sxs-lookup"><span data-stu-id="a9011-168">**Event01**</span></span>

<span data-ttu-id="a9011-169">Przedstawia sposób tworzenia polecenia cmdlet dla rejestracji zdarzenia przez wynikających z ObjectEventRegistrationBase.</span><span class="sxs-lookup"><span data-stu-id="a9011-169">Shows how to create a cmdlet for event registration by deriving from ObjectEventRegistrationBase.</span></span>

<span data-ttu-id="a9011-170">**Event02**</span><span class="sxs-lookup"><span data-stu-id="a9011-170">**Event02**</span></span>

<span data-ttu-id="a9011-171">Pokazuje sposób do pokazano, jak otrzymywać powiadomienia zdarzeń programu Windows PowerShell, które są generowane na komputerach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="a9011-171">Shows how to shows how to receive notifications of Windows PowerShell events that are generated on remote computers.</span></span>
<span data-ttu-id="a9011-172">Używa zdarzeń PSEventReceived za pośrednictwem [obszaru działania](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx) klasy.</span><span class="sxs-lookup"><span data-stu-id="a9011-172">It uses the PSEventReceived event exposed through the [Runspace](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx) class.</span></span>

## <a name="hosting-application-samples"></a><span data-ttu-id="a9011-173">Hosting aplikacji — przykłady</span><span class="sxs-lookup"><span data-stu-id="a9011-173">Hosting application samples</span></span>

<span data-ttu-id="a9011-174">**Runspace01**</span><span class="sxs-lookup"><span data-stu-id="a9011-174">**Runspace01**</span></span>

<span data-ttu-id="a9011-175">Przedstawia sposób użycia [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) klasę, aby uruchomić [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) polecenia cmdlet synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="a9011-175">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet synchronously.</span></span>
<span data-ttu-id="a9011-176">[Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) polecenie cmdlet zwraca [procesu](https://technet.microsoft.com/library/system.diagnostics.process.aspx) obiektów dla wszystkich procesów działających na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="a9011-176">The [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer.</span></span>

<span data-ttu-id="a9011-177">**Runspace02**</span><span class="sxs-lookup"><span data-stu-id="a9011-177">**Runspace02**</span></span>

<span data-ttu-id="a9011-178">Przedstawia sposób użycia [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) klasę, aby uruchomić [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) i [sortowania obiektu](http://go.microsoft.com/fwlink/?LinkID=113403) poleceń cmdlet synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="a9011-178">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) and [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) cmdlets synchronously.</span></span>
<span data-ttu-id="a9011-179">[Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) polecenie cmdlet zwraca [procesu](https://technet.microsoft.com/library/system.diagnostics.process.aspx) obiektów dla każdego przetwarzania uruchomiony na komputerze lokalnym i obiektu sortowania sortuje obiekty na podstawie ich [identyfikator](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) właściwości.</span><span class="sxs-lookup"><span data-stu-id="a9011-179">The [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer, and the Sort-Object sorts the objects based on their [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) property.</span></span>
<span data-ttu-id="a9011-180">Wyniki z tych poleceń jest wyświetlany za pomocą [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) formantu.</span><span class="sxs-lookup"><span data-stu-id="a9011-180">The results of these commands is displayed by using a [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) control.</span></span>

<span data-ttu-id="a9011-181">**Runspace03**</span><span class="sxs-lookup"><span data-stu-id="a9011-181">**Runspace03**</span></span>

<span data-ttu-id="a9011-182">Przedstawia sposób użycia [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) klasę, aby uruchomić skrypt synchronicznie i sposób obsługi błędów niepowodujący.</span><span class="sxs-lookup"><span data-stu-id="a9011-182">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run a script synchronously, and how to handle non-terminating errors.</span></span>
<span data-ttu-id="a9011-183">Skrypt otrzymuje listę nazw procesu, a następnie pobiera tych procesów.</span><span class="sxs-lookup"><span data-stu-id="a9011-183">The script receives a list of process names and then retrieves those processes.</span></span>
<span data-ttu-id="a9011-184">Wyniki skryptu, między innymi niepowodujący błędów, które zostały wygenerowane podczas wykonywania skryptu, są wyświetlane w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="a9011-184">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

<span data-ttu-id="a9011-185">**Runspace04**</span><span class="sxs-lookup"><span data-stu-id="a9011-185">**Runspace04**</span></span>

<span data-ttu-id="a9011-186">Przedstawia sposób użycia [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) klasy na potrzeby uruchamiania poleceń i jak błędy Trwa przerywanie działania catch, które są generowane podczas uruchamiania polecenia.</span><span class="sxs-lookup"><span data-stu-id="a9011-186">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span>
<span data-ttu-id="a9011-187">Dwa polecenia są uruchamiane, a ostatnie polecenie jest przekazany argument parametru, który jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="a9011-187">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span>
<span data-ttu-id="a9011-188">W związku z tym żadne obiekty nie są zwracane i zostanie zgłoszony błąd powodujący przerwanie.</span><span class="sxs-lookup"><span data-stu-id="a9011-188">As a result, no objects are returned and a terminating error is thrown.</span></span>

<span data-ttu-id="a9011-189">**Runspace05**</span><span class="sxs-lookup"><span data-stu-id="a9011-189">**Runspace05**</span></span>

<span data-ttu-id="a9011-190">Przedstawiono sposób dodawania przystawki do [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) obiekt, tak aby polecenia cmdlet przystawki jest dostępna po otwarciu obszaru działania.</span><span class="sxs-lookup"><span data-stu-id="a9011-190">Shows how to add a snap-in to an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span>
<span data-ttu-id="a9011-191">Przystawka udostępnia polecenia cmdlet Get-Proc (zdefiniowane przez [próbki GetProcessSample01](https://technet.microsoft.com/library/ff602028.aspx)) uruchamiane synchronicznie przy użyciu [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) obiektu.</span><span class="sxs-lookup"><span data-stu-id="a9011-191">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](https://technet.microsoft.com/library/ff602028.aspx)) that is run synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="a9011-192">**Runspace06**</span><span class="sxs-lookup"><span data-stu-id="a9011-192">**Runspace06**</span></span>

<span data-ttu-id="a9011-193">Pokazuje, jak dodać moduł do [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) obiekt, tak aby po otwarciu obszaru działania ładowany jest moduł.</span><span class="sxs-lookup"><span data-stu-id="a9011-193">Shows how to add a module to an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object so that the module is loaded when the runspace is opened.</span></span>
<span data-ttu-id="a9011-194">Moduł zawiera polecenia cmdlet Get-Proc (zdefiniowane przez [próbki GetProcessSample02](https://technet.microsoft.com/library/ff602027.aspx)) uruchamiane synchronicznie przy użyciu [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) obiektu.</span><span class="sxs-lookup"><span data-stu-id="a9011-194">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](https://technet.microsoft.com/library/ff602027.aspx)) that is run synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="a9011-195">**Runspace07**</span><span class="sxs-lookup"><span data-stu-id="a9011-195">**Runspace07**</span></span>

<span data-ttu-id="a9011-196">Pokazuje, jak utworzyć obszaru działania, a następnie użyj tego obszaru działania do uruchamiania dwóch poleceń cmdlet synchronicznie przy użyciu [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) obiektu.</span><span class="sxs-lookup"><span data-stu-id="a9011-196">Shows how to create a runspace, and then use that runspace to run two cmdlets synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="a9011-197">**Runspace08**</span><span class="sxs-lookup"><span data-stu-id="a9011-197">**Runspace08**</span></span>

<span data-ttu-id="a9011-198">Przedstawiono sposób dodawania polecenia i argumentów do potoku z [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) obiektu i uruchamiania poleceń synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="a9011-198">Shows how to add commands and arguments to the pipeline of a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object and how to run the commands synchronously.</span></span>

<span data-ttu-id="a9011-199">**Runspace09**</span><span class="sxs-lookup"><span data-stu-id="a9011-199">**Runspace09**</span></span>

<span data-ttu-id="a9011-200">Pokazuje, jak dodać skrypt do potoku z [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) obiektu oraz sposobu uruchamiania skryptu asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="a9011-200">Shows how to add a script to the pipeline of a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object and how to run the script asynchronously.</span></span>
<span data-ttu-id="a9011-201">Zdarzenia są używane do obsługi danych wyjściowych skryptu.</span><span class="sxs-lookup"><span data-stu-id="a9011-201">Events are used to handle the output of the script.</span></span>

<span data-ttu-id="a9011-202">**Runspace10**</span><span class="sxs-lookup"><span data-stu-id="a9011-202">**Runspace10**</span></span>

<span data-ttu-id="a9011-203">Przedstawia sposób tworzenia domyślnej początkowy stan sesji, jak dodać polecenia cmdlet, aby [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx), jak utworzyć obszaru działania, używającej stanu sesji początkowej i sposób uruchamiania polecenia przy użyciu [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx)obiektu.</span><span class="sxs-lookup"><span data-stu-id="a9011-203">Shows how to create a default initial session state, how to add a cmdlet to the [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx), how to create a runspace that uses the initial session state, and how to run the command by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="a9011-204">**Runspace11**</span><span class="sxs-lookup"><span data-stu-id="a9011-204">**Runspace11**</span></span>

<span data-ttu-id="a9011-205">Przedstawia sposób użycia [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) klasy, aby utworzyć polecenie serwera proxy, który wywołuje istniejącego polecenia cmdlet, ale ogranicza zestaw dostępnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="a9011-205">Shows how to use the [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) class to create a proxy command that calls an existing cmdlet, but restricts the set of available parameters.</span></span>
<span data-ttu-id="a9011-206">Polecenie serwera proxy jest dodawane do stanu sesji początkowej, która służy do tworzenia ograniczonego obszaru działania.</span><span class="sxs-lookup"><span data-stu-id="a9011-206">The proxy command is then added to an initial session state that is used to create a constrained runspace.</span></span>
<span data-ttu-id="a9011-207">Oznacza to, że użytkownik ma dostęp funkcjonalność polecenia cmdlet tylko za pomocą polecenia proxy.</span><span class="sxs-lookup"><span data-stu-id="a9011-207">This means that the user can access the functionality of the cmdlet only through the proxy command.</span></span>

<span data-ttu-id="a9011-208">**PowerShell01**</span><span class="sxs-lookup"><span data-stu-id="a9011-208">**PowerShell01**</span></span>

<span data-ttu-id="a9011-209">Pokazuje, jak utworzyć za pomocą ograniczonego obszaru działania [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) obiektu.</span><span class="sxs-lookup"><span data-stu-id="a9011-209">Shows how to create a constrained runspace using an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object.</span></span>

<span data-ttu-id="a9011-210">**PowerShell02**</span><span class="sxs-lookup"><span data-stu-id="a9011-210">**PowerShell02**</span></span>

<span data-ttu-id="a9011-211">Przedstawia sposób użycia puli obszaru działania równoczesne uruchamianie wielu poleceń.</span><span class="sxs-lookup"><span data-stu-id="a9011-211">Shows how to use a runspace pool to run multiple commands concurrently.</span></span>

## <a name="host-samples"></a><span data-ttu-id="a9011-212">Przykłady hosta</span><span class="sxs-lookup"><span data-stu-id="a9011-212">Host samples</span></span>

<span data-ttu-id="a9011-213">**Host01**</span><span class="sxs-lookup"><span data-stu-id="a9011-213">**Host01**</span></span>

<span data-ttu-id="a9011-214">Przedstawia sposób wykonania aplikacji hosta, który używa hosta niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="a9011-214">Shows how to implement a host application that uses a custom host.</span></span>
<span data-ttu-id="a9011-215">W tym przykładzie obszaru działania jest tworzony, który korzysta z hosta niestandardowego a następnie [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) interfejsu API jest używany do uruchamiania skryptu, który wywołuje "exit".</span><span class="sxs-lookup"><span data-stu-id="a9011-215">In this sample a runspace is created that uses the custom host, and then the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) API is used to run a script that calls "exit".</span></span>
<span data-ttu-id="a9011-216">Następnie aplikacja hosta analizuje dane wyjściowe skryptu i wyświetla wyniki.</span><span class="sxs-lookup"><span data-stu-id="a9011-216">The host application then looks at the output of the script and prints out the results.</span></span>

<span data-ttu-id="a9011-217">**Host02**</span><span class="sxs-lookup"><span data-stu-id="a9011-217">**Host02**</span></span>

<span data-ttu-id="a9011-218">Przedstawia sposób zapisania aplikacji hosta, który używa środowiska wykonawczego programu Windows PowerShell wraz z implementacji hosta niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="a9011-218">Shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span>
<span data-ttu-id="a9011-219">Aplikacja hosta ustawia kulturę hosta na język niemiecki, uruchamia [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) polecenia cmdlet i wyświetla wyniki w postaci użytkownik zobaczy je przy użyciu pwrsh.exe, a następnie drukuje bieżąca data i godzina w języku niemieckim.</span><span class="sxs-lookup"><span data-stu-id="a9011-219">The host application sets the host culture to German, runs the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet and displays the results as you would see them by using pwrsh.exe, and then prints out the current data and time in German.</span></span>

<span data-ttu-id="a9011-220">**Host03**</span><span class="sxs-lookup"><span data-stu-id="a9011-220">**Host03**</span></span>

<span data-ttu-id="a9011-221">Przedstawia sposób tworzenia aplikacji opartych na konsoli host interaktywny, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli.</span><span class="sxs-lookup"><span data-stu-id="a9011-221">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

<span data-ttu-id="a9011-222">**Host04**</span><span class="sxs-lookup"><span data-stu-id="a9011-222">**Host04**</span></span>

<span data-ttu-id="a9011-223">Przedstawia sposób tworzenia aplikacji opartych na konsoli host interaktywny, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli.</span><span class="sxs-lookup"><span data-stu-id="a9011-223">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="a9011-224">Ta aplikacja hosta obsługuje również wyświetlania monitów, które umożliwiają użytkownikowi określenie wiele wyborów.</span><span class="sxs-lookup"><span data-stu-id="a9011-224">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

<span data-ttu-id="a9011-225">**Host05**</span><span class="sxs-lookup"><span data-stu-id="a9011-225">**Host05**</span></span>

<span data-ttu-id="a9011-226">Przedstawia sposób tworzenia aplikacji opartych na konsoli host interaktywny, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli.</span><span class="sxs-lookup"><span data-stu-id="a9011-226">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="a9011-227">Ta aplikacja hosta obsługuje również wywołania do komputerów zdalnych przy użyciu [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) i [zakończenia-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a9011-227">This host application also supports calls to remote computers by using the [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) and [Exit-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212) cmdlets.</span></span>

<span data-ttu-id="a9011-228">**Host06**</span><span class="sxs-lookup"><span data-stu-id="a9011-228">**Host06**</span></span>

<span data-ttu-id="a9011-229">Przedstawia sposób tworzenia aplikacji opartych na konsoli host interaktywny, która odczytuje poleceń w wierszu polecenia, wykonuje polecenia, a następnie wyświetla wyniki w konsoli.</span><span class="sxs-lookup"><span data-stu-id="a9011-229">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="a9011-230">Ponadto w przykładzie użyto interfejsów API Tokenizatora określić kolor tekstu wprowadzonej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a9011-230">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="provider-samples"></a><span data-ttu-id="a9011-231">Przykłady dostawcy</span><span class="sxs-lookup"><span data-stu-id="a9011-231">Provider samples</span></span>

<span data-ttu-id="a9011-232">**AccessDBProviderSample01**</span><span class="sxs-lookup"><span data-stu-id="a9011-232">**AccessDBProviderSample01**</span></span>

<span data-ttu-id="a9011-233">Pokazuje, jak można zadeklarować klasy dostawcy, który pochodzi bezpośrednio z [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx) klasy.</span><span class="sxs-lookup"><span data-stu-id="a9011-233">Shows how to declare a provider class that derives directly from the [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx) class.</span></span>
<span data-ttu-id="a9011-234">Został uwzględniony w tym miejscu jedynie, aby informacje były kompletne.</span><span class="sxs-lookup"><span data-stu-id="a9011-234">It is included here only for completeness.</span></span>

<span data-ttu-id="a9011-235">**AccessDBProviderSample02**</span><span class="sxs-lookup"><span data-stu-id="a9011-235">**AccessDBProviderSample02**</span></span>

<span data-ttu-id="a9011-236">Pokazuje, jak zastąpić [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) i [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) metody do wywołania polecenia cmdlet New-elementu PSDrive i elementu PSDrive Usuń obsługi.</span><span class="sxs-lookup"><span data-stu-id="a9011-236">Shows how to overwrite the [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) and [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) methods to support calls to the New-PSDrive and Remove-PSDrive cmdlets.</span></span>
<span data-ttu-id="a9011-237">Klasa dostawcy, w tym przykładzie pochodzi z [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx) klasy.</span><span class="sxs-lookup"><span data-stu-id="a9011-237">The provider class in this sample derives from the [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx) class.</span></span>

<span data-ttu-id="a9011-238">**AccessDBProviderSample03**</span><span class="sxs-lookup"><span data-stu-id="a9011-238">**AccessDBProviderSample03**</span></span>

<span data-ttu-id="a9011-239">Pokazuje, jak zastąpić [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) i [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) metod do obsługi wywołania do elementu Get i Set-Item poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a9011-239">Shows how to overwrite the [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) and [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) methods to support calls to the Get-Item and Set-Item cmdlets.</span></span>
<span data-ttu-id="a9011-240">Klasa dostawcy, w tym przykładzie pochodzi z [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) klasy.</span><span class="sxs-lookup"><span data-stu-id="a9011-240">The provider class in this sample derives from the [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="a9011-241">**AccessDBProviderSample04**</span><span class="sxs-lookup"><span data-stu-id="a9011-241">**AccessDBProviderSample04**</span></span>

<span data-ttu-id="a9011-242">Pokazuje, jak zastąpić metody kontenera do obsługi połączeń w celu Copy-Item, Get-ChildItem nowy element i polecenia cmdlet Remove-elementów.</span><span class="sxs-lookup"><span data-stu-id="a9011-242">Shows how to overwrite container methods to support calls to the Copy-Item, Get-ChildItem, New-Item, and Remove-Item cmdlets.</span></span>
<span data-ttu-id="a9011-243">Te metody powinny zostać wdrożone, gdy magazyn danych zawiera elementy, które są kontenerami.</span><span class="sxs-lookup"><span data-stu-id="a9011-243">These methods should be implemented when the data store contains items that are containers.</span></span>
<span data-ttu-id="a9011-244">Kontener jest grupą elementów podrzędnych w obszarze wspólnego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="a9011-244">A container is a group of child items under a common parent item.</span></span>
<span data-ttu-id="a9011-245">Klasa dostawcy, w tym przykładzie pochodzi z [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) klasy.</span><span class="sxs-lookup"><span data-stu-id="a9011-245">The provider class in this sample derives from the [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="a9011-246">**AccessDBProviderSample05**</span><span class="sxs-lookup"><span data-stu-id="a9011-246">**AccessDBProviderSample05**</span></span>

<span data-ttu-id="a9011-247">Pokazuje, jak zastąpić metody kontenera do obsługi wywołania polecenia cmdlet Move-Item i ścieżki sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="a9011-247">Shows how to overwrite container methods to support calls to the Move-Item and Join-Path cmdlets.</span></span>
<span data-ttu-id="a9011-248">Te metody powinny zostać wdrożone, gdy użytkownik chce przenieść elementów w kontenerze, a Magazyn danych zawiera zagnieżdżone kontenery.</span><span class="sxs-lookup"><span data-stu-id="a9011-248">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span>
<span data-ttu-id="a9011-249">Klasa dostawcy, w tym przykładzie pochodzi z [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) klasy.</span><span class="sxs-lookup"><span data-stu-id="a9011-249">The provider class in this sample derives from the [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="a9011-250">**AccessDBProviderSample06**</span><span class="sxs-lookup"><span data-stu-id="a9011-250">**AccessDBProviderSample06**</span></span>

<span data-ttu-id="a9011-251">Pokazuje, jak zastąpić metody zawartości do obsługi wywołania z zawartością wyczyść pobrania zawartości i polecenia cmdlet Set-zawartości.</span><span class="sxs-lookup"><span data-stu-id="a9011-251">Shows how to overwrite content methods to support calls to the Clear-Content, Get-Content, and Set-Content cmdlets.</span></span>
<span data-ttu-id="a9011-252">Te metody powinny zostać wdrożone, gdy użytkownik chce zarządzać zawartością elementów w magazynie danych.</span><span class="sxs-lookup"><span data-stu-id="a9011-252">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span>
<span data-ttu-id="a9011-253">Klasa dostawcy, w tym przykładzie pochodzi z [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) klasy która implementuje [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a9011-253">The provider class in this sample derives from the [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) class, and it implements the [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx) interface.</span></span>

