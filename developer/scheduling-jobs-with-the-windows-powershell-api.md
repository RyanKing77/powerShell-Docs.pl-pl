---
title: Planowanie zadań przy użyciu interfejsu API programu Windows PowerShell
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 280067072c5c8e289a38745364294af842a455c6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845430"
---
# <a name="scheduling-jobs-with-the-windows-powershell-api"></a><span data-ttu-id="9efb0-102">Planowanie zadań przy użyciu interfejsu API programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9efb0-102">Scheduling Jobs with the Windows PowerShell API</span></span>

<span data-ttu-id="9efb0-103">Obiekty udostępniane przez przestrzeń nazw N:Microsoft.PowerShell.ScheduledJob umożliwia tworzenie zaplanowanego zadania, zdefiniuj po jego uruchomieniu i Pobierz wyniki dotyczące ukończone zadanie po jego wykonaniu.</span><span class="sxs-lookup"><span data-stu-id="9efb0-103">You can use the objects exposed by the N:Microsoft.PowerShell.ScheduledJob namespace to create a scheduled job, define when it runs, and get results about the completed job after it has run.</span></span>

## <a name="triggering-the-job"></a><span data-ttu-id="9efb0-104">Wyzwolenie zadania</span><span class="sxs-lookup"><span data-stu-id="9efb0-104">Triggering the Job</span></span>

<span data-ttu-id="9efb0-105">Pierwszym krokiem w tworzeniu zaplanowanego zadania jest określenie, kiedy zadanie będzie uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="9efb0-105">The first step in creating a scheduled job is specifying when the job should run.</span></span> <span data-ttu-id="9efb0-106">W tym celu tworzenia i konfigurowania T:Microsoft.PowerShell.ScheduledJob.ScheduledJobTriggerobject.</span><span class="sxs-lookup"><span data-stu-id="9efb0-106">Do this by creating and configuring a T:Microsoft.PowerShell.ScheduledJob.ScheduledJobTriggerobject.</span></span> <span data-ttu-id="9efb0-107">Poniższy kod tworzy wyzwalacz, który planuje zadanie, aby uruchomić jeden raz w przyszłości 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="9efb0-107">The following code creates a trigger that schedules a job to run a single time 20 seconds in the future.</span></span>

```csharp
ScheduledJobTrigger jobTrigger = ScheduledJobTrigger.CreateOnceTrigger(
    DateTime.Now.AddSeconds(20),        // Create trigger to start job 20 seconds after now.
    TimeSpan.Zero,                      // No random delay
    null,                               // No repetition interval time
    null,                               // No repetition interval duration
    1,                                  // Trigger Id
    true);                              // Create trigger enabled
```

## <a name="defining-the-job"></a><span data-ttu-id="9efb0-108">Definiowanie zadania</span><span class="sxs-lookup"><span data-stu-id="9efb0-108">Defining the Job</span></span>

<span data-ttu-id="9efb0-109">Tworząc słownik parametrów, należy zdefiniować zadania programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9efb0-109">You define a Windows PowerShell job by creating a parameter dictionary.</span></span> <span data-ttu-id="9efb0-110">Obsługiwane są następujące parametry.</span><span class="sxs-lookup"><span data-stu-id="9efb0-110">The following parameters are supported.</span></span>

|<span data-ttu-id="9efb0-111">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="9efb0-111">Parameter Name</span></span>|<span data-ttu-id="9efb0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9efb0-112">Description</span></span>|
|---|---|
|<span data-ttu-id="9efb0-113">Nazwa</span><span class="sxs-lookup"><span data-stu-id="9efb0-113">Name</span></span>|<span data-ttu-id="9efb0-114">Nazwa zadania.</span><span class="sxs-lookup"><span data-stu-id="9efb0-114">The name of the job.</span></span>|
|<span data-ttu-id="9efb0-115">ScriptBock</span><span class="sxs-lookup"><span data-stu-id="9efb0-115">ScriptBock</span></span>|<span data-ttu-id="9efb0-116">Blok skryptu programu Windows PowerShell, który określa, jak działa zadanie.</span><span class="sxs-lookup"><span data-stu-id="9efb0-116">A Windows PowerShell script block that specifies what the job does.</span></span>|
|<span data-ttu-id="9efb0-117">FilePath</span><span class="sxs-lookup"><span data-stu-id="9efb0-117">FilePath</span></span>|<span data-ttu-id="9efb0-118">Ścieżka do pliku, który zawiera blok skryptu programu Windows PowerShell, który określa, jak działa zadanie.</span><span class="sxs-lookup"><span data-stu-id="9efb0-118">A path to a file that contains Windows PowerShell script block that specifies what the job does.</span></span>|
|<span data-ttu-id="9efb0-119">InitializationScript</span><span class="sxs-lookup"><span data-stu-id="9efb0-119">InitializationScript</span></span>|<span data-ttu-id="9efb0-120">Blok skryptu programu Windows PowerShell, która inicjuje zadania.</span><span class="sxs-lookup"><span data-stu-id="9efb0-120">A Windows PowerShell script block that initializes the job.</span></span>|
|<span data-ttu-id="9efb0-121">Listaargumentów</span><span class="sxs-lookup"><span data-stu-id="9efb0-121">ArgumentList</span></span>|<span data-ttu-id="9efb0-122">Tablica obiektów, które określają argumenty, które zadanie trwa.</span><span class="sxs-lookup"><span data-stu-id="9efb0-122">An array of objects that specify arguments that the job takes.</span></span>|
|<span data-ttu-id="9efb0-123">RunAs32</span><span class="sxs-lookup"><span data-stu-id="9efb0-123">RunAs32</span></span>|<span data-ttu-id="9efb0-124">Wartość logiczna określająca, czy uruchomić zadanie w procesie 32-bitowym.</span><span class="sxs-lookup"><span data-stu-id="9efb0-124">A boolean value that specifies whether to run the job in a 32-bit process.</span></span>|

<span data-ttu-id="9efb0-125">Poniższy kod tworzy obiekt słownika parametru i ustawia parametry nazwy i blok skryptu.</span><span class="sxs-lookup"><span data-stu-id="9efb0-125">The following code creates a parameter dictionary object and sets the Name and ScriptBlock parameters.</span></span>

```csharp
string schedJobDefName = "MySampleSchedJob";
Dictionary<string, object> jobDefParameters = new Dictionary<string, object>();
jobDefParameters.Add("Name", schedJobDefName);      // Unique name is requiried.

ScriptBlock scriptBlock = ScriptBlock.Create(@"1..5 | foreach {sleep 1; ""SchedJobOutput $_""}");
jobDefParameters.Add("ScriptBlock", scriptBlock);  // A scriptblock or script FilePath
                                                   // is required.
```

## <a name="creating-the-invocation-and-job-definition-objects"></a><span data-ttu-id="9efb0-126">Tworzenie wywołania i obiekty definicji zadania</span><span class="sxs-lookup"><span data-stu-id="9efb0-126">Creating the Invocation and Job Definition Objects</span></span>

<span data-ttu-id="9efb0-127">Następnie można utworzyć obiektów ScheduledJobInvicationInfo i SheduledJobDefinition do uruchomienia zadania.</span><span class="sxs-lookup"><span data-stu-id="9efb0-127">You then create ScheduledJobInvicationInfo and SheduledJobDefinition objects to run the job.</span></span> <span data-ttu-id="9efb0-128">Poniższy kod przedstawia to.</span><span class="sxs-lookup"><span data-stu-id="9efb0-128">The following code demonstrates this.</span></span>

```csharp
ScheduledJobInvocationInfo jobInvocationInfo = new ScheduledJobInvocationInfo(
    nw JobDefinition(typeof(ScheduledJobSourceAdapter), scriptBlock.ToString(), schedJobDefName),
    jobDefParameters);

schedJobDefinition = new ScheduledJobDefinition(
    jobInvocationInfo,                          // Defines the PowerShell job to run.
    new ScheduledJobTrigger[1] { jobTrigger },  // Defines when to run the PowerShell job.
    null,                                       // No custom options.  We accept default.
    null);                                      // No credentials.  PowerShell job is run
                                                // in default Task Scheduler process, account.
```

## <a name="registering-the-job-with-the-task-scheduler"></a><span data-ttu-id="9efb0-129">Rejestrowanie zadania za pomocą harmonogramu zadań</span><span class="sxs-lookup"><span data-stu-id="9efb0-129">Registering the Job with the Task Scheduler</span></span>

<span data-ttu-id="9efb0-130">Poniższy kod rejestruje zadanie z harmonogramu zadań Windows.</span><span class="sxs-lookup"><span data-stu-id="9efb0-130">The following code registers the job with the Windows Task Scheduler.</span></span>

```csharp
schedJobDefinition.Register();
registrationSucceeded = true;
Console.WriteLine("Scheduled job has been registered.  Waiting 30 seconds for it to be started and run.");
```

## <a name="complete-code-example"></a><span data-ttu-id="9efb0-131">Pełny przykład kodu</span><span class="sxs-lookup"><span data-stu-id="9efb0-131">Complete Code Example</span></span>

<span data-ttu-id="9efb0-132">Oto przykład kompletny kod, z którego wykonano poprzednich fragmentach kodu.</span><span class="sxs-lookup"><span data-stu-id="9efb0-132">The following is the complete code example from which the previous snippets were taken.</span></span>

```csharp
using System;
using System.Threading;
using System.Collections.Generic;
using System.Management.Automation;             // Windows PowerShell namespace.
using Microsoft.PowerShell.ScheduledJob;        // Windows PowerShell ScheduledJob namespace.

namespace Microsoft.Samples.PowerShell.ScheduledJob
{
    /// <summary>
    /// This class contains the Main enrty point for the application.
    /// </summary>
    public class ScheduledJobSample
    {
        /// <summary>
        /// This sample shows how to use the PowerShell ScheduledJob API to create
        /// a simple PowerShell scheduled job, register it with a trigger object
        /// that defines when the job will run and retrieve job run results from
        /// the job file store.
        /// </summary>
        /// <param name="args"></param>
        public static void Main(string[] args)
        {
            // ScheduledJobDefinition contains all elements of a PowerShell scheduled
            // job including the PowerShell job script or script file path, scheduling
            // triggers, and scheduling options.
            ScheduledJobDefinition schedJobDefinition = null;
            bool registrationSucceeded = false;

            try
            {
                // First create a scheduled job trigger object.  This object will
                // define when the PowerShell job is scheduled to run.  For this
                // example we will create a trigger to run the job just one time
                // 20 seconds after the trigger object is created.
                // Note: If you are stepping through this code in a debugger you
                // may want to increase the 20 seconds value so that the trigger time
                // remains in the future once you register the scheduled job.
                ScheduledJobTrigger jobTrigger = ScheduledJobTrigger.CreateOnceTrigger(
                    DateTime.Now.AddSeconds(20),        // Create trigger to start job 20 seconds after now.
                    TimeSpan.Zero,                      // No random delay
                    null,                               // No repetition interval time
                    null,                               // No repetition interval duration
                    1,                                  // Trigger Id
                    true);                              // Create trigger enabled

                // Create a parameter dictionary that defines the PowerShell job.
                // For this example we will create a simple script that runs for
                // 5 seconds generating output.
                // Here are the parameters supported to define the PowerShell job.
                // Name                 - Job name string.
                // ScriptBlock          - PowerShell ScriptBlock type.
                // FilePath             - PowerShell script file path string.
                // InitializationScript - PowerShell Scriptblock type.
                // ArgumentList         - object[] type.
                // RunAs32              - Switch (boolean type).
                string schedJobDefName = "MySampleSchedJob";
                Dictionary<string, object> jobDefParameters = new Dictionary<string, object>();
                jobDefParameters.Add("Name", schedJobDefName);      // Unique name is requiried.

                ScriptBlock scriptBlock = ScriptBlock.Create(@"1..5 | foreach {sleep 1; ""SchedJobOutput $_""}");
                jobDefParameters.Add("ScriptBlock", scriptBlock);  // A scriptblock or script FilePath
                                                                   // is required.

                // Now create a JobInvocation object that contains all information about
                // the PowerShell job to run.
                ScheduledJobInvocationInfo jobInvocationInfo = new ScheduledJobInvocationInfo(
                    new JobDefinition(typeof(ScheduledJobSourceAdapter), scriptBlock.ToString(), schedJobDefName),
                    jobDefParameters);

                // Finally create the scheduled job definition object that pulls all
                // of this information together.
                schedJobDefinition = new ScheduledJobDefinition(
                    jobInvocationInfo,                          // Defines the PowerShell job to run.
                    new ScheduledJobTrigger[1] { jobTrigger },  // Defines when to run the PowerShell job.
                    null,                                       // No custom options.  We accept default.
                    null);                                      // No credentials.  PowerShell job is run
                                                                // in default Task Scheduler process, account.

                // Next we register this scheduled job object with Windows Task Scheduler.
                // The Task Scheduler will run the PowerShell script based on the provided job trigger.
                schedJobDefinition.Register();
                registrationSucceeded = true;
                Console.WriteLine("Scheduled job has been registered.  Waiting 30 seconds for it to be started and run.");

                // You can see this PowerShell job task registered in the Task Scheduler UI.
                // Look under path: Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs

                // Wait for Task Scheduler to run the PowerShell job.  This should happen in 20 seconds
                // and then the job will take about 5 seconds to run.  If PowerShell job task doesn't
                // run try increasing the trigger time in the ScheduledJobTrigger object.  You can also
                // run this task manully from the Task Scheduler UI.
                for (int count = 1; count < 31; ++count)
                {
                    Thread.Sleep(1000);
                    Console.WriteLine(count + " seconds elapsed");
                }

                Console.WriteLine();
                Console.WriteLine("Job run results.");
                Console.WriteLine();

                // Since the PowerShell job runs in a non-interactive Task Scheduler
                // process the job status and output data is written to a file based
                // job store and the directory location is the current user local app
                // data ($env:LOCALAPPDATA).
                // This job store can be accessed through the ScheduledJobSourceAdapter class.
                ScheduledJobSourceAdapter schedJobSourceAdpater = new ScheduledJobSourceAdapter();
                IList<Job2> jobRuns = schedJobSourceAdpater.GetJobs();
                foreach (var jobRun in jobRuns)
                {
                    // Check for jobs in finished state.
                    // Note that job data is not written to the job store until the job
                    // has reached a finished state.
                    JobState jobState = jobRun.JobStateInfo.State;
                    if (jobState == JobState.Completed ||
                        jobState == JobState.Stopped ||
                        jobState == JobState.Failed)
                    {
                        // Write job run finished state.
                        Console.WriteLine("Job Status: " + jobRun.JobStateInfo.State);
                        Console.WriteLine();
                        Console.WriteLine("Job Data");

                        // Write output data.
                        foreach (var item in jobRun.Output)
                        {
                            Console.WriteLine(item.ToString());
                        }

                        // Write any errors.
                        foreach (var item in jobRun.Error)
                        {
                            Console.WriteLine(item.ToString());
                        }
                    }
                }

                Console.WriteLine();
                Console.WriteLine("Press any key to continue...");
                Console.ReadKey();
            }
            catch (ScheduledJobException e)
            {
                Console.WriteLine("Error: " + e.Message);
            }
            finally
            {
                // Unregister this scheduled job or an error will be thrown when
                // running this sample code again (scheduled job already exists.)
                // because all registered scheduled jobs must have a unique name.
                if (registrationSucceeded)
                {
                    schedJobDefinition.Remove(true);
                }
            }
        }
    }
}
```
