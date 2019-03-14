---
title: Zadania w tle | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794709"
---
# <a name="background-jobs"></a><span data-ttu-id="4355e-102">Zadania w tle</span><span class="sxs-lookup"><span data-stu-id="4355e-102">Background Jobs</span></span>

<span data-ttu-id="4355e-103">Polecenia cmdlet akcję można wykonać ich wewnętrznie lub programu Windows PowerShell*zadania w tle*.</span><span class="sxs-lookup"><span data-stu-id="4355e-103">Cmdlets can perform their action internally or as a Windows PowerShell*background job*.</span></span> <span data-ttu-id="4355e-104">Po uruchomieniu polecenia cmdlet jako zadanie w tle zadania są wykonywane asynchronicznie w jego własnym wątku, niezależnie od wątku potoku, która używa polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4355e-104">When a cmdlet runs as a background job, the work is done asynchronously in its own thread separate from the pipeline thread that the cmdlet is using.</span></span> <span data-ttu-id="4355e-105">Z punktu widzenia użytkownika gdy polecenia cmdlet jest uruchamiane jako zadanie w tle, wiersza polecenia zwraca natychmiast nawet, jeśli zadanie trwa zbyt długo, a użytkownik może kontynuować bez zakłóceń, podczas gdy zadanie zostanie uruchomione.</span><span class="sxs-lookup"><span data-stu-id="4355e-105">From the user perspective, when a cmdlet runs as a background job, the command prompt returns immediately even if the job takes an extended amount of time to complete, and the user can continue without interruption while the job runs.</span></span>

## <a name="background-jobs-child-jobs-and-the-job-repository"></a><span data-ttu-id="4355e-106">Zadania w tle i zadań podrzędnych, repozytorium zadania</span><span class="sxs-lookup"><span data-stu-id="4355e-106">Background Jobs, Child Jobs, and the Job Repository</span></span>

<span data-ttu-id="4355e-107">Obiekt zadania, który jest zwracany przez polecenia cmdlet używane do obsługi zadań w tle definiuje zadania.</span><span class="sxs-lookup"><span data-stu-id="4355e-107">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="4355e-108">( [Zadanie rozpoczęcia](/powershell/module/Microsoft.PowerShell.Core/Start-Job) polecenie cmdlet zwraca również wartość obiektu zadania.) Nazwa zadania, identyfikator, który jest używany do określenia zadania, informacje o stanie i zadania podrzędne znajdują się w tej definicji.</span><span class="sxs-lookup"><span data-stu-id="4355e-108">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="4355e-109">Zadanie nie powoduje wykonania żadnej pracy.</span><span class="sxs-lookup"><span data-stu-id="4355e-109">The job does not perform any of the work.</span></span> <span data-ttu-id="4355e-110">Każde zadanie w tle ma co najmniej jedno zadanie podrzędne, ponieważ zadanie podrzędne wykonuje rzeczywistą pracę.</span><span class="sxs-lookup"><span data-stu-id="4355e-110">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="4355e-111">Po uruchomieniu polecenia cmdlet, aby praca jest wykonywana w tle, polecenia cmdlet należy dodać zadanie i zadania podrzędne do wspólnego repozytorium, nazywane *repozytorium zadania*.</span><span class="sxs-lookup"><span data-stu-id="4355e-111">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>

<span data-ttu-id="4355e-112">Aby uzyskać więcej informacji na temat obsługi zadania w tle w wierszu polecenia zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="4355e-112">For more information about how background jobs are handled at the command line, see the following:</span></span>

- [<span data-ttu-id="4355e-113">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="4355e-113">about_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [<span data-ttu-id="4355e-114">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="4355e-114">about_Job_Details</span></span>](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [<span data-ttu-id="4355e-115">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="4355e-115">about_Remote_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a><span data-ttu-id="4355e-116">Zapisywanie polecenia Cmdlet, które jest uruchamiane jako zadanie w tle</span><span class="sxs-lookup"><span data-stu-id="4355e-116">Writing a Cmdlet That Runs as a Background Job</span></span>

<span data-ttu-id="4355e-117">Aby zapisać polecenia cmdlet, które mogą być uruchamiane jako zadanie w tle, należy wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="4355e-117">To write a cmdlet that can be run as a background job, you must complete the following tasks:</span></span>

- <span data-ttu-id="4355e-118">Zdefiniuj `asJob` Przełącz parametr, dzięki czemu użytkownik może zdecydować, czy uruchomić polecenie cmdlet jako zadanie w tle.</span><span class="sxs-lookup"><span data-stu-id="4355e-118">Define an `asJob` switch parameter so that the user can decide whether to run the cmdlet as a background job.</span></span>

- <span data-ttu-id="4355e-119">Utworzyć obiekt, który pochodzi od klasy [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) klasy.</span><span class="sxs-lookup"><span data-stu-id="4355e-119">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="4355e-120">Ten obiekt może być obiektu niestandardowego zadania lub obiektu zadania dostarczone przez program Windows PowerShell, takie jak [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) obiektu.</span><span class="sxs-lookup"><span data-stu-id="4355e-120">This object can be a custom job object or a job object provided by Windows PowerShell, such as a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

- <span data-ttu-id="4355e-121">W metodzie przetwarzania rekordów, Dodaj `if` instrukcję, która wykrywa, czy polecenia cmdlet powinny być uruchamiany jako zadanie w tle.</span><span class="sxs-lookup"><span data-stu-id="4355e-121">In a record processing method, add an `if` statement that detects whether the cmdlet should run as a background job.</span></span>

- <span data-ttu-id="4355e-122">Dla obiektów niestandardowych zadań implementacji klasy zadania.</span><span class="sxs-lookup"><span data-stu-id="4355e-122">For custom job objects, implement the job class.</span></span>

- <span data-ttu-id="4355e-123">Zwróć odpowiednich obiektów, w zależności od tego, czy polecenie cmdlet jest uruchamiane jako zadanie w tle.</span><span class="sxs-lookup"><span data-stu-id="4355e-123">Return the appropriate objects, depending on whether the cmdlet is run as a background job.</span></span>

<span data-ttu-id="4355e-124">Dla przykładu kodu zobacz [sposobu obsługi zadań](./how-to-support-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="4355e-124">For a code example, see [How to Support Jobs](./how-to-support-jobs.md).</span></span>

## <a name="background-job-related-apis"></a><span data-ttu-id="4355e-125">Interfejsy API związane z zadania w tle</span><span class="sxs-lookup"><span data-stu-id="4355e-125">Background Job-Related APIs</span></span>

<span data-ttu-id="4355e-126">Następujące interfejsy API są dostarczane przez programu Windows PowerShell do zarządzania zadania w tle.</span><span class="sxs-lookup"><span data-stu-id="4355e-126">The following APIs are provided by Windows PowerShell to manage background jobs.</span></span>

<span data-ttu-id="4355e-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) pochodzi obiektów niestandardowych zadań.</span><span class="sxs-lookup"><span data-stu-id="4355e-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Derives custom job objects.</span></span> <span data-ttu-id="4355e-128">Jest klasą abstrakcyjną.</span><span class="sxs-lookup"><span data-stu-id="4355e-128">This is an abstract class.</span></span>

<span data-ttu-id="4355e-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) służy do zarządzania i zawiera informacje dotyczące bieżącego zadania w tle active.</span><span class="sxs-lookup"><span data-stu-id="4355e-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Manages and provides information about the current active background jobs.</span></span>

<span data-ttu-id="4355e-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) definiuje stan zadania w tle.</span><span class="sxs-lookup"><span data-stu-id="4355e-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) Defines the state of the background job.</span></span> <span data-ttu-id="4355e-131">Stany to uruchomiona, uruchomione i zatrzymane.</span><span class="sxs-lookup"><span data-stu-id="4355e-131">States include Started, Running, and Stopped.</span></span>

<span data-ttu-id="4355e-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) zawiera informacje o stanie zadania w tle, a w przypadku zmiany stanu ostatniego zostało spowodowane przez błąd, przyczyna zadania wprowadzono swojego bieżącego stanu.</span><span class="sxs-lookup"><span data-stu-id="4355e-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) Provides information about the state of a background job and, if the last state change was caused by an error, the reason the job entered its current state.</span></span>

<span data-ttu-id="4355e-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) zawiera argumenty dla zdarzenia, które jest wywoływane, gdy zmieni się stan zadania w tle.</span><span class="sxs-lookup"><span data-stu-id="4355e-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) Provides the arguments for an event that is raised when a background job changes state.</span></span>

## <a name="windows-powershell-job-cmdlets"></a><span data-ttu-id="4355e-134">Polecenia cmdlet programu Windows PowerShell zadania</span><span class="sxs-lookup"><span data-stu-id="4355e-134">Windows PowerShell Job Cmdlets</span></span>

<span data-ttu-id="4355e-135">Następujące polecenia cmdlet są dostarczane przez programu Windows PowerShell do zarządzania zadania w tle.</span><span class="sxs-lookup"><span data-stu-id="4355e-135">The following cmdlets are provided by Windows PowerShell to manage background jobs.</span></span>

[<span data-ttu-id="4355e-136">Get-Job</span><span class="sxs-lookup"><span data-stu-id="4355e-136">Get-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

<span data-ttu-id="4355e-137">Pobiera zadania w tle programu Windows PowerShell, które są uruchomione w bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="4355e-137">Gets Windows PowerShell background jobs that are running in the current session.</span></span>

[<span data-ttu-id="4355e-138">Odbieranie — zadanie</span><span class="sxs-lookup"><span data-stu-id="4355e-138">Receive-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

<span data-ttu-id="4355e-139">Pobiera wyniki zadania w tle programu Windows PowerShell w bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="4355e-139">Gets the results of the Windows PowerShell background jobs in the current session.</span></span>

[<span data-ttu-id="4355e-140">Usuń zadanie</span><span class="sxs-lookup"><span data-stu-id="4355e-140">Remove-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

<span data-ttu-id="4355e-141">Usuwa zadania w tle programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4355e-141">Deletes a Windows PowerShell background job.</span></span>

[<span data-ttu-id="4355e-142">Zadanie rozpoczęcia</span><span class="sxs-lookup"><span data-stu-id="4355e-142">Start-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

<span data-ttu-id="4355e-143">Uruchamia zadanie w tle programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4355e-143">Starts a Windows PowerShell background job.</span></span>

[<span data-ttu-id="4355e-144">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="4355e-144">Stop-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

<span data-ttu-id="4355e-145">Zatrzymuje wykonywanie zadania w tle programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4355e-145">Stops a Windows PowerShell background job.</span></span>

[<span data-ttu-id="4355e-146">WAIT — zadanie</span><span class="sxs-lookup"><span data-stu-id="4355e-146">Wait-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

<span data-ttu-id="4355e-147">Pomija wiersz polecenia, dopiero po zakończeniu jednego lub wszystkich zadań w tle programu Windows PowerShell, uruchomiony w sesji.</span><span class="sxs-lookup"><span data-stu-id="4355e-147">Suppresses the command prompt until one or all of the Windows PowerShell background jobs running in the session are complete.</span></span>

## <a name="see-also"></a><span data-ttu-id="4355e-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4355e-148">See Also</span></span>

[<span data-ttu-id="4355e-149">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4355e-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
