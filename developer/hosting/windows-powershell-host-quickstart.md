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
ms.openlocfilehash: cc014487a680747ad59437052f79d4576154a1cb
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059681"
---
# <a name="windows-powershell-host-quickstart"></a>Przewodnik Szybki start dotyczący hosta programu Windows PowerShell

Aby obsługiwać środowiska Windows PowerShell w aplikacji, należy użyć [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) klasy. Ta klasa dostarcza metody, które tworzenie potoku z poleceń, a następnie wykonywania tych poleceń w obszarze działania. Najprostszym sposobem na utworzenie aplikacji hosta jest używać obszarem działania domyślne. Obszarem działania domyślny zawiera wszystkie polecenia programu Windows PowerShell core. Jeśli chcesz, aby aplikacja do udostępnienia tylko podzbiór poleceń programu Windows PowerShell, należy utworzyć niestandardowe obszaru działania.

## <a name="using-the-default-runspace"></a>Za pomocą obszaru działania domyślne

Aby rozpocząć, będzie używane domyślne obszarze działania i używane w metody [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) klasy, aby dodać polecenia, parametry, instrukcje i skrypty do potoku.

### <a name="addcommand"></a>Addcommand —

Możesz użyć [System.Management.Automation.Powershell.AddCommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) metody [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) klasy, aby dodać polecenia do potoku. Na przykład załóżmy, że chcesz pobrać listę uruchomionych procesów na komputerze. Sposób uruchamiania tego polecenia jest następująca.

1. Tworzenie [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) obiektu.

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. Dodaj polecenie, które chcesz wykonać.

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. Wywołaj polecenie.

   ```csharp
   ps.Invoke();
   ```

Jeśli wywołasz [System.Management.Automation.Powershell.AddCommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) więcej niż jeden raz przed wywołaniem metody [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) metody, wynik pierwsze polecenie w potoku do drugiej i tak dalej. Jeśli nie chcesz przekazać wynik poprzedniego polecenia do polecenia, dodaj go przez wywołanie metody [System.Management.Automation.Powershell.AddStatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) zamiast tego.

### <a name="addparameter"></a>AddParameter

Poprzedni przykład wykonuje jednego polecenia bez parametrów. Można dodać parametry do polecenia przy użyciu [System.Management.Automation.PSCommand.AddParameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) metody na przykład, poniższy kod umożliwia pobranie listy wszystkich procesów, które są nazywane `PowerShell` systemem maszyny.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

Można dodać dodatkowe parametry, wywołując [System.Management.Automation.PSCommand.AddParameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) wielokrotnie.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

Możesz również dodać słownik nazw parametrów i wartości, wywołując [System.Management.Automation.PowerShell.AddParameters*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) metody.

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

Można symulować dzielenia na partie przy użyciu [System.Management.Automation.PowerShell.AddStatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) metody, która dodaje dodatkowe oświadczenie na końcu potoku, poniższy kod umożliwia pobranie listy uruchomionych procesów o nazwie `PowerShell`, a następnie pobiera listę uruchomionych usług.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

Istniejący skrypt można uruchomić, wywołując [System.Management.Automation.PowerShell.AddScript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) metody. Poniższy przykład dodaje skrypt do potoku i uruchamia go. W tym przykładzie przyjęto założenie, skrypt o nazwie istnieje już `MyScript.ps1` w folderze o nazwie `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

Jest również wersja [System.Management.Automation.PowerShell.AddScript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) metody, która przyjmuje parametr logiczny o nazwie `useLocalScope`. Jeśli ten parametr jest równa `true`, a następnie skrypt jest uruchamiany w zakresie lokalnym. Poniższy kod będzie uruchomić skrypt w zakresie lokalnym.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a>Tworzenie niestandardowego działania

Podczas działania domyślne używane w poprzednich przykładach ładuje wszystkie polecenia programu Windows PowerShell core, można utworzyć niestandardowego obszaru działania, który ładuje określony podzbiór wszystkich poleceń. Można to zrobić, aby zwiększyć wydajność (Trwa ładowanie większej liczby poleceń jest trafień wydajności), lub aby ograniczyć możliwość wykonywania operacji użytkownika. Obszar działania, który udostępnia ograniczoną liczbę poleceń jest nazywany ograniczonego obszaru działania. Aby utworzyć ograniczonego obszaru działania, należy użyć [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) i [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) klasy.

### <a name="creating-an-initialsessionstate-object"></a>Tworzenie obiektu InitialSessionState

Aby utworzyć niestandardowe obszar działania, należy najpierw utworzyć [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) obiektu. W poniższym przykładzie użyto [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) do utworzenia obszaru działania po utworzeniu domyślny [System.Management.Automation.Runspaces.InitialSessionState ](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) obiektu.

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a>Ograniczając obszarze działania

W poprzednim przykładzie utworzyliśmy domyślny [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) obiekt, który ładuje wszystkie wbudowane podstawowych programu Windows PowerShell. Firma Microsoft może mieć jest określana skrótem [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) metodę, aby utworzyć obiekt InitialSessionState, który będzie załadować tylko polecenia Microsoft.PowerShell.Core przystawki. Aby utworzyć bardziej ograniczonego obszaru działania, należy utworzyć pusty [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) obiektu przez wywołanie metody [ System.Management.Automation.Runspaces.InitialSessionState.Create*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) metody, a następnie dodać polecenia do InitialSessionState.

Za pomocą obszaru działania, który ładuje tylko polecenia, które określisz zapewnia znacznie lepszą wydajność.

Możesz użyć metody [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) klasy, aby zdefiniować poleceń cmdlet dla stanu sesji początkowej. Poniższy przykład tworzy stanie pusty początkowej sesji, a następnie definiuje i dodaje `Get-Command` i `Import-Module` poleceń do stanu początkowego sesji. Firma Microsoft Utwórz obszar działania, zależy od tego stanu sesji początkowej i wykonaj polecenia w tym obszarze działania.

Utwórz stan początkowy sesji.

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

Definiowanie i dodać polecenia do stanu początkowego sesji.

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

Utwórz i otwórz obszarze działania.

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

Wykonywanie polecenia i przedstawiają wynik pomyślnie.

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

Po uruchomieniu, dane wyjściowe ten kod będzie wyglądać w następujący sposób.

```powershell
Get-Command
Import-Module
```
