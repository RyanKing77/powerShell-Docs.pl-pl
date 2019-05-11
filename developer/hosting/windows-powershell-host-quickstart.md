---
title: Przewodnik Szybki Start Windows hosta programu PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: 9a080b6db7416ae6bf65a1b0353e9f17a56cc6c5
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64530625"
---
# <a name="windows-powershell-host-quickstart"></a><span data-ttu-id="5a9be-102">Przewodnik Szybki start dotyczący hosta programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a9be-102">Windows PowerShell Host Quickstart</span></span>

<span data-ttu-id="5a9be-103">Aby obsługiwać środowiska Windows PowerShell w aplikacji, należy użyć [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) klasy.</span><span class="sxs-lookup"><span data-stu-id="5a9be-103">To host Windows PowerShell in your application, you use the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class.</span></span>
<span data-ttu-id="5a9be-104">Ta klasa dostarcza metody, które tworzenie potoku z poleceń, a następnie wykonywania tych poleceń w obszarze działania.</span><span class="sxs-lookup"><span data-stu-id="5a9be-104">This class provides methods that create a pipeline of commands and then execute those commands in a runspace.</span></span>
<span data-ttu-id="5a9be-105">Najprostszym sposobem na utworzenie aplikacji hosta jest używać obszarem działania domyślne.</span><span class="sxs-lookup"><span data-stu-id="5a9be-105">The simplest way to create a host application is to use the default runspace.</span></span>
<span data-ttu-id="5a9be-106">Obszarem działania domyślny zawiera wszystkie polecenia programu Windows PowerShell core.</span><span class="sxs-lookup"><span data-stu-id="5a9be-106">The default runspace contains all of the core Windows PowerShell commands.</span></span>
<span data-ttu-id="5a9be-107">Jeśli chcesz, aby aplikacja do udostępnienia tylko podzbiór poleceń programu Windows PowerShell, należy utworzyć niestandardowe obszaru działania.</span><span class="sxs-lookup"><span data-stu-id="5a9be-107">If you want your application to expose only a subset of the Windows PowerShell commands, you must create a custom runspace.</span></span>

## <a name="using-the-default-runspace"></a><span data-ttu-id="5a9be-108">Za pomocą obszaru działania domyślne</span><span class="sxs-lookup"><span data-stu-id="5a9be-108">Using the default runspace</span></span>

<span data-ttu-id="5a9be-109">Aby rozpocząć, będzie używane domyślne obszarze działania i używane w metody [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) klasy, aby dodać polecenia, parametry, instrukcje i skrypty do potoku.</span><span class="sxs-lookup"><span data-stu-id="5a9be-109">To start, we'll use the default runspace, and use the methods of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands, parameters, statements, and scripts to a pipeline.</span></span>

### <a name="addcommand"></a><span data-ttu-id="5a9be-110">Addcommand —</span><span class="sxs-lookup"><span data-stu-id="5a9be-110">AddCommand</span></span>

<span data-ttu-id="5a9be-111">Możesz użyć [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) metodę, aby dodać polecenia do potoku.</span><span class="sxs-lookup"><span data-stu-id="5a9be-111">You use the [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method to add commands to the pipeline.</span></span>
<span data-ttu-id="5a9be-112">Na przykład załóżmy, że chcesz pobrać listę uruchomionych procesów na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5a9be-112">For example, suppose you want to get the list of running processes on the machine.</span></span>
<span data-ttu-id="5a9be-113">Sposób uruchamiania tego polecenia jest następująca.</span><span class="sxs-lookup"><span data-stu-id="5a9be-113">The way to run this command is as follows.</span></span>

1. <span data-ttu-id="5a9be-114">Tworzenie [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) obiektu.</span><span class="sxs-lookup"><span data-stu-id="5a9be-114">Create a [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="5a9be-115">Dodaj polecenie, które chcesz wykonać.</span><span class="sxs-lookup"><span data-stu-id="5a9be-115">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="5a9be-116">Wywołaj polecenie.</span><span class="sxs-lookup"><span data-stu-id="5a9be-116">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="5a9be-117">Jeśli więcej niż jeden raz wywołać metodę addcommand — przed wywołaniem [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) potoku wynik pierwszego polecenia metody do drugiej i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="5a9be-117">If you call the AddCommand method more than once before you call the [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span>
<span data-ttu-id="5a9be-118">Jeśli nie chcesz przekazać wynik poprzedniego polecenia do polecenia, dodaj go przez wywołanie metody [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="5a9be-118">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="5a9be-119">AddParameter</span><span class="sxs-lookup"><span data-stu-id="5a9be-119">AddParameter</span></span>

<span data-ttu-id="5a9be-120">Poprzedni przykład wykonuje jednego polecenia bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="5a9be-120">The previous example executes a single command without any parameters.</span></span>
<span data-ttu-id="5a9be-121">Można dodać parametry do polecenia przy użyciu [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) metody.</span><span class="sxs-lookup"><span data-stu-id="5a9be-121">You can add parameters to the command by using the [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method.</span></span>
<span data-ttu-id="5a9be-122">Na przykład, poniższy kod umożliwia pobranie listy wszystkich procesów, które są nazywane `PowerShell` uruchomionego na maszynie.</span><span class="sxs-lookup"><span data-stu-id="5a9be-122">For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="5a9be-123">Możesz dodać dodatkowe parametry, przez wywołanie metody AddParameter wielokrotnie.</span><span class="sxs-lookup"><span data-stu-id="5a9be-123">You can add additional parameters by calling the AddParameter method repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

<span data-ttu-id="5a9be-124">Możesz również dodać słownik nazw parametrów i wartości, wywołując [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) metody.</span><span class="sxs-lookup"><span data-stu-id="5a9be-124">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="5a9be-125">AddStatement</span><span class="sxs-lookup"><span data-stu-id="5a9be-125">AddStatement</span></span>

<span data-ttu-id="5a9be-126">Można symulować dzielenia na partie przy użyciu [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) metody, która dodaje dodatkowe oświadczenie na końcu potoku.</span><span class="sxs-lookup"><span data-stu-id="5a9be-126">You can simulate batching by using the [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline.</span></span>
<span data-ttu-id="5a9be-127">Poniższy kod umożliwia pobranie listy uruchomionych procesów o nazwie `PowerShell`, a następnie pobiera listę uruchomionych usług.</span><span class="sxs-lookup"><span data-stu-id="5a9be-127">The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="5a9be-128">AddScript</span><span class="sxs-lookup"><span data-stu-id="5a9be-128">AddScript</span></span>

<span data-ttu-id="5a9be-129">Istniejący skrypt można uruchomić, wywołując [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) metody.</span><span class="sxs-lookup"><span data-stu-id="5a9be-129">You can run an existing script by calling the [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span>
<span data-ttu-id="5a9be-130">Poniższy przykład dodaje skrypt do potoku i uruchamia go.</span><span class="sxs-lookup"><span data-stu-id="5a9be-130">The following example adds a script to the pipeline and runs it.</span></span>
<span data-ttu-id="5a9be-131">W tym przykładzie przyjęto założenie, skrypt o nazwie istnieje już `MyScript.ps1` w folderze o nazwie `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="5a9be-131">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="5a9be-132">Jest również wersja metody AddScript, który przyjmuje parametr logiczny o nazwie `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="5a9be-132">There is also a version of the AddScript method that takes a boolean parameter named `useLocalScope`.</span></span>
<span data-ttu-id="5a9be-133">Jeśli ten parametr jest równa `true`, a następnie skrypt jest uruchamiany w zakresie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="5a9be-133">If this parameter is set to `true`, then the script is run in the local scope.</span></span>
<span data-ttu-id="5a9be-134">Poniższy kod będzie uruchomić skrypt w zakresie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="5a9be-134">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a><span data-ttu-id="5a9be-135">Tworzenie niestandardowego działania</span><span class="sxs-lookup"><span data-stu-id="5a9be-135">Creating a custom runspace</span></span>

<span data-ttu-id="5a9be-136">Podczas działania domyślne używane w poprzednich przykładach ładuje wszystkie polecenia programu Windows PowerShell core, można utworzyć niestandardowego obszaru działania, który ładuje określony podzbiór wszystkich poleceń.</span><span class="sxs-lookup"><span data-stu-id="5a9be-136">While the default runspace used in the previous examples loads all of the core Windows PowerShell commands, you can create a custom runspace that loads only a specified subset of all commands.</span></span>
<span data-ttu-id="5a9be-137">Można to zrobić, aby zwiększyć wydajność (Trwa ładowanie większej liczby poleceń jest trafień wydajności), lub aby ograniczyć możliwość wykonywania operacji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5a9be-137">You might want to do this to improve performance (loading a larger number of commands is a performance hit), or to restrict the capability of the user to perform operations.</span></span>
<span data-ttu-id="5a9be-138">Obszar działania, który udostępnia ograniczoną liczbę poleceń jest nazywany ograniczonego obszaru działania.</span><span class="sxs-lookup"><span data-stu-id="5a9be-138">A runspace that exposes only a limited number of commands is called a constrained runspace.</span></span>
<span data-ttu-id="5a9be-139">Aby utworzyć ograniczonego obszaru działania, należy użyć [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) i [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) klasy.</span><span class="sxs-lookup"><span data-stu-id="5a9be-139">To create a constrained runspace, you use the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) and [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span></span>

### <a name="creating-an-initialsessionstate-object"></a><span data-ttu-id="5a9be-140">Tworzenie obiektu InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="5a9be-140">Creating an InitialSessionState object</span></span>

<span data-ttu-id="5a9be-141">Aby utworzyć niestandardowe obszar działania, należy najpierw utworzyć [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) obiektu.</span><span class="sxs-lookup"><span data-stu-id="5a9be-141">To create a custom runspace, you must first create an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>
<span data-ttu-id="5a9be-142">W poniższym przykładzie użyto [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) do utworzenia obszaru działania po utworzeniu obiektu InitialSessionState domyślne.</span><span class="sxs-lookup"><span data-stu-id="5a9be-142">In the following example, we use the [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) to create a runspace after creating a default InitialSessionState object.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a><span data-ttu-id="5a9be-143">Ograniczając obszarze działania</span><span class="sxs-lookup"><span data-stu-id="5a9be-143">Constraining the runspace</span></span>

<span data-ttu-id="5a9be-144">W poprzednim przykładzie utworzyliśmy domyślny [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) obiekt, który ładuje wszystkie wbudowane podstawowych programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a9be-144">In the previous example, we created a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object that loads all of the built-in core Windows PowerShell.</span></span>
<span data-ttu-id="5a9be-145">Firma Microsoft może mieć jest określana skrótem [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) metodę, aby utworzyć obiekt InitialSessionState, który będzie załadować tylko polecenia Microsoft.PowerShell.Core przystawki.</span><span class="sxs-lookup"><span data-stu-id="5a9be-145">We could also have called the [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) method to create an InitialSessionState object that would load only the commands in the Microsoft.PowerShell.Core snapin.</span></span>
<span data-ttu-id="5a9be-146">Aby utworzyć bardziej ograniczonego obszaru działania, należy utworzyć pusty obiekt InitialSessionState przez wywołanie metody [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) metody, a następnie dodać polecenia do InitialSessionState.</span><span class="sxs-lookup"><span data-stu-id="5a9be-146">To create a more constrained runspace, you must create an empty InitialSessionState object by calling the [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add commands to the InitialSessionState.</span></span>

<span data-ttu-id="5a9be-147">Za pomocą obszaru działania, który ładuje tylko polecenia, które określisz zapewnia znacznie lepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="5a9be-147">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

<span data-ttu-id="5a9be-148">Możesz użyć metody [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) klasy, aby zdefiniować poleceń cmdlet dla stanu sesji początkowej.</span><span class="sxs-lookup"><span data-stu-id="5a9be-148">You use the methods of the [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>
<span data-ttu-id="5a9be-149">Poniższy przykład tworzy stanie pusty początkowej sesji, a następnie definiuje i dodaje `Get-Command` i `Import-Module` poleceń do stanu początkowego sesji.</span><span class="sxs-lookup"><span data-stu-id="5a9be-149">The following example creates an empty initial session state, then defines and adds the `Get-Command` and `Import-Module` commands to the initial session state.</span></span>
<span data-ttu-id="5a9be-150">Firma Microsoft Utwórz obszar działania, zależy od tego stanu sesji początkowej i wykonaj polecenia w tym obszarze działania.</span><span class="sxs-lookup"><span data-stu-id="5a9be-150">We then create a runspace constrained by that initial session state, and execute the commands in that runspace.</span></span>

<span data-ttu-id="5a9be-151">Utwórz stan początkowy sesji.</span><span class="sxs-lookup"><span data-stu-id="5a9be-151">Create the initial session state.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

<span data-ttu-id="5a9be-152">Definiowanie i dodać polecenia do stanu początkowego sesji.</span><span class="sxs-lookup"><span data-stu-id="5a9be-152">Define and add commands to the initial session state.</span></span>

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

<span data-ttu-id="5a9be-153">Utwórz i otwórz obszarze działania.</span><span class="sxs-lookup"><span data-stu-id="5a9be-153">Create and open the runspace.</span></span>

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

<span data-ttu-id="5a9be-154">Wykonywanie polecenia i przedstawiają wynik pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="5a9be-154">Execute a command and show the result.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
Collection<CommandInfo> result = ps.Invoke<CommandInfo>();
foreach (var entry in result)
{
       Console.WriteLine(entry.Name);
}
```

<span data-ttu-id="5a9be-155">Po uruchomieniu, dane wyjściowe ten kod będzie wyglądać w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="5a9be-155">When run, the output of this code will look as follows.</span></span>

```powershell
Get-Command
Import-Module
```
