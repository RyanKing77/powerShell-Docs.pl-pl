---
title: Przykładowe Events01 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27d0ee5e-2589-4530-92ef-c09996b80994
caps.latest.revision: 10
ms.openlocfilehash: c9963819f1842d1245735dabc487babaa566c160
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057165"
---
# <a name="events01-sample"></a><span data-ttu-id="15f50-102">Przykład Events01</span><span class="sxs-lookup"><span data-stu-id="15f50-102">Events01 Sample</span></span>

<span data-ttu-id="15f50-103">W tym przykładzie przedstawiono sposób tworzenia polecenia cmdlet, które umożliwia użytkownikowi rejestrowania zdarzeń, które są wywoływane przez [Klasa System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="15f50-103">This sample shows how to create a cmdlet that allows the user to register for events that are raised by [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span> <span data-ttu-id="15f50-104">Za pomocą tego polecenia cmdlet użytkownicy będą mogli zarejestrować akcję do wykonania po utworzeniu pliku w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="15f50-104">With this cmdlet, users can register an action to execute when a file is created under a specific directory.</span></span> <span data-ttu-id="15f50-105">W tym przykładzie pochodzi z [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="15f50-105">This sample derives from the [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="15f50-106">Jak skompilować przykład za pomocą programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="15f50-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="15f50-107">Za pomocą Windows PowerShell 2.0 zainstalowany zestaw SDK przejdź do folderu Events01.</span><span class="sxs-lookup"><span data-stu-id="15f50-107">With the Windows PowerShell 2.0 SDK installed, navigate to the Events01 folder.</span></span> <span data-ttu-id="15f50-108">Domyślna lokalizacja to C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01.</span><span class="sxs-lookup"><span data-stu-id="15f50-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01.</span></span>

2. <span data-ttu-id="15f50-109">Kliknij dwukrotnie ikonę pliku rozwiązania (.sln).</span><span class="sxs-lookup"><span data-stu-id="15f50-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="15f50-110">Spowoduje to otwarcie z przykładowym projektem w programie Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="15f50-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="15f50-111">W **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="15f50-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="15f50-112">Biblioteka dla przykładu, zostanie utworzona w folderze \bin lub \bin\debug domyślny.</span><span class="sxs-lookup"><span data-stu-id="15f50-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="15f50-113">Jak uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="15f50-113">How to run the sample</span></span>

1. <span data-ttu-id="15f50-114">Utwórz następujący folder modułu:</span><span class="sxs-lookup"><span data-stu-id="15f50-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/events01`

2. <span data-ttu-id="15f50-115">Skopiuj plik biblioteki, na przykład do folderu modułu.</span><span class="sxs-lookup"><span data-stu-id="15f50-115">Copy the library file for the sample to the module folder.</span></span>

3. <span data-ttu-id="15f50-116">Uruchom program Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="15f50-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="15f50-117">Uruchom następujące polecenie, aby załadować polecenia cmdlet w programie Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="15f50-117">Run the following command to load the cmdlet into Windows PowerShell:</span></span>

    ```powershell
    import-module events01
    ```

5. <span data-ttu-id="15f50-118">Użyj polecenia cmdlet Register-FileSystemEvent zarejestrować akcję, która zapisze komunikat, gdy plik jest tworzony w katalogu TEMP.</span><span class="sxs-lookup"><span data-stu-id="15f50-118">Use the Register-FileSystemEvent cmdlet to register an action that will write a message when a file is created under the TEMP directory.</span></span>

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. <span data-ttu-id="15f50-119">Utwórz plik w katalogu TEMP i należy pamiętać, że akcja jest wykonywana (zostanie wyświetlony komunikat).</span><span class="sxs-lookup"><span data-stu-id="15f50-119">Create a file under the TEMP directory and note that the action is executed (the message is displayed).</span></span>

<span data-ttu-id="15f50-120">To przykładowe dane wyjściowe, powstałego wykonaj następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="15f50-120">This is a sample output that results by following these steps.</span></span>

```output
Id              Name            State      HasMoreData     Location             Command
--              ----            -----      -----------     --------             -------
1               26932870-d3b... NotStarted False                                 Write-Host "A f...

```

```powershell
Set-Content $env:temp\test.txt "This is a test file"
```

```output
A file was created in the TEMP directory
```

## <a name="requirements"></a><span data-ttu-id="15f50-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="15f50-121">Requirements</span></span>

<span data-ttu-id="15f50-122">Ten przykładowy skrypt wymaga programu Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="15f50-122">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="15f50-123">Przedstawiono</span><span class="sxs-lookup"><span data-stu-id="15f50-123">Demonstrates</span></span>

<span data-ttu-id="15f50-124">W przykładzie pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="15f50-124">This sample demonstrates the following.</span></span>

- <span data-ttu-id="15f50-125">Jak napisać polecenie cmdlet służące do rejestrowania zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="15f50-125">How to write a cmdlet for event registration.</span></span> <span data-ttu-id="15f50-126">Polecenia cmdlet jest pochodną [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) klasy, która zapewnia obsługę typowych parametrów do Register-\* zdarzeń poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="15f50-126">The cmdlet derives from the [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) class, which provides support for parameters common to the Register-\*Event cmdlets.</span></span> <span data-ttu-id="15f50-127">Polecenia cmdlet, które są uzyskiwane z [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) musi mieć możliwość definiowania ich poszczególnych parametrów i zastąpić `GetSourceObject` i `GetSourceObjectEventName` metody abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="15f50-127">Cmdlets that are derived from [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) need only to define their particular parameters and override the `GetSourceObject` and `GetSourceObjectEventName` abstract methods.</span></span>

## <a name="example"></a><span data-ttu-id="15f50-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="15f50-128">Example</span></span>

<span data-ttu-id="15f50-129">W tym przykładzie pokazano, jak zarejestrować zdarzenia wygenerowane przez [Klasa System.IO.FileSystemWatcher](https://msdn.microsoft.com/en-us/library/system.io.filesystemwatcher\(v=vs.110\).aspx).</span><span class="sxs-lookup"><span data-stu-id="15f50-129">This sample shows how to register for events raised by [System.IO.FileSystemWatcher](https://msdn.microsoft.com/en-us/library/system.io.filesystemwatcher\(v=vs.110\).aspx).</span></span>

```csharp
namespace Sample
{
    using System;
    using System.IO;
    using System.Management.Automation;
    using System.Management.Automation.Runspaces;
    using Microsoft.PowerShell.Commands;

    [Cmdlet(VerbsLifecycle.Register, "FileSystemEvent")]
    public class RegisterObjectEventCommand : ObjectEventRegistrationBase
    {
        /// <summary>The FileSystemWatcher that exposes the events.</summary>
        private FileSystemWatcher fileSystemWatcher = new FileSystemWatcher();

        /// <summary>Name of the event to which the cmdlet registers.</summary>
        private string eventName = null;

        /// <summary>
        /// Gets or sets the path that will be monitored by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = true, Position = 0)]
        public string Path
        {
            get
            {
                return this.fileSystemWatcher.Path;
            }

            set
            {
                this.fileSystemWatcher.Path = value;
            }
        }

        /// <summary>
        /// Gets or sets the name of the event to which the cmdlet registers.
        /// <para>
        /// Currently System.IO.FileSystemWatcher exposes 6 events: Changed, Created,
        /// Deleted, Disposed, Error, and Renamed. Check the MSDN documentation of
        /// FileSystemWatcher for details on each event.
        /// </para>
        /// </summary>
        [Parameter(Mandatory = true, Position = 1)]
        public string EventName
        {
            get
            {
                return this.eventName;
            }

            set
            {
                this.eventName = value;
            }
        }

        /// <summary>
        /// Gets or sets the filter that will be user by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = false)]
        public string Filter
        {
            get
            {
                return this.fileSystemWatcher.Filter;
            }

            set
            {
                this.fileSystemWatcher.Filter = value;
            }
        }

        /// <summary>
        /// Derived classes must implement this method to return the object that generates
        /// the events to be monitored.
        /// </summary>
        /// <returns> This sample returns an instance of System.IO.FileSystemWatcher</returns>
        protected override object GetSourceObject()
        {
            return this.fileSystemWatcher;
        }

        /// <summary>
        /// Derived classes must implement this method to return the name of the event to
        /// be monitored. This event must be exposed by the input object.
        /// </summary>
        /// <returns> This sample returns the event specified by the user with the -EventName parameter.</returns>
        protected override string GetSourceObjectEventName()
        {
            return this.eventName;
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="15f50-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15f50-130">See Also</span></span>

[<span data-ttu-id="15f50-131">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="15f50-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)