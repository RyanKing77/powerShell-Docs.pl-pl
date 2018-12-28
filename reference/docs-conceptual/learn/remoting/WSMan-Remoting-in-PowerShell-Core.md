---
title: Obsługa zdalna usługi WS-Management (WSMan) w programie PowerShell Core
description: Komunikacji zdalnej w programie PowerShell Core za pomocą usługi WS-Management
ms.date: 08/06/2018
ms.openlocfilehash: ce58ed88f59f32b0f83951e55de36e829f7fa3f4
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405567"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a><span data-ttu-id="be127-103">Obsługa zdalna usługi WS-Management (WSMan) w programie PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="be127-103">WS-Management (WSMan) Remoting in PowerShell Core</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="be127-104">Instrukcje, aby utworzyć punkt końcowy komunikacji zdalnej</span><span class="sxs-lookup"><span data-stu-id="be127-104">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="be127-105">Pakiet programu PowerShell Core for Windows obejmuje dodatku typu plug-in WinRM (`pwrshplugin.dll`) i skrypt instalacji (`Install-PowerShellRemoting.ps1`) w `$PSHome`.</span><span class="sxs-lookup"><span data-stu-id="be127-105">The PowerShell Core package for Windows includes a WinRM plug-in (`pwrshplugin.dll`) and an installation script (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span></span>
<span data-ttu-id="be127-106">Te pliki umożliwiają programu PowerShell do akceptowania przychodzących połączeń zdalnych programu PowerShell, jeśli nie określono punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="be127-106">These files enable PowerShell to accept incoming PowerShell remote connections when its endpoint is specified.</span></span>

### <a name="motivation"></a><span data-ttu-id="be127-107">Motywacją</span><span class="sxs-lookup"><span data-stu-id="be127-107">Motivation</span></span>

<span data-ttu-id="be127-108">Instalacja programu PowerShell mogą nawiązywać sesje programu PowerShell z komputerów zdalnych przy użyciu `New-PSSession` i `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="be127-108">An installation of PowerShell can establish PowerShell sessions to remote computers using `New-PSSession` and `Enter-PSSession`.</span></span>
<span data-ttu-id="be127-109">Aby włączyć ją do akceptowania przychodzących połączeń zdalnych programu PowerShell, użytkownik musi utworzyć punkt końcowy komunikacji zdalnej usługi WinRM.</span><span class="sxs-lookup"><span data-stu-id="be127-109">To enable it to accept incoming PowerShell remote connections, the user must create a WinRM remoting endpoint.</span></span>
<span data-ttu-id="be127-110">Jest to jawne uczestnictwo scenariusz gdy użytkownik uruchamia PowerShellRemoting.ps1 instalacji, aby utworzyć punkt końcowy usługi WinRM.</span><span class="sxs-lookup"><span data-stu-id="be127-110">This is an explicit opt-in scenario where the user runs Install-PowerShellRemoting.ps1 to create the WinRM endpoint.</span></span>
<span data-ttu-id="be127-111">Skrypt instalacji jest rozwiązaniem krótkoterminowym, dopóki nie możemy dodać kolejne funkcje do `Enable-PSRemoting` do wykonania tego samego działania.</span><span class="sxs-lookup"><span data-stu-id="be127-111">The installation script is a short-term solution until we add additional functionality to `Enable-PSRemoting` to perform the same action.</span></span>
<span data-ttu-id="be127-112">Aby uzyskać więcej informacji, zobacz problem [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span><span class="sxs-lookup"><span data-stu-id="be127-112">For more details, please see issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span></span>

### <a name="script-actions"></a><span data-ttu-id="be127-113">Akcje skryptu</span><span class="sxs-lookup"><span data-stu-id="be127-113">Script Actions</span></span>

<span data-ttu-id="be127-114">Skrypt</span><span class="sxs-lookup"><span data-stu-id="be127-114">The script</span></span>

1. <span data-ttu-id="be127-115">Tworzy katalog dla wtyczki w ramach %windir%\System32\PowerShell</span><span class="sxs-lookup"><span data-stu-id="be127-115">Creates a directory for the plug-in within %windir%\System32\PowerShell</span></span>
1. <span data-ttu-id="be127-116">Kopiuje pwrshplugin.dll do tej lokalizacji</span><span class="sxs-lookup"><span data-stu-id="be127-116">Copies pwrshplugin.dll to that location</span></span>
1. <span data-ttu-id="be127-117">Generuje plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="be127-117">Generates a configuration file</span></span>
1. <span data-ttu-id="be127-118">Rejestruje to wtyczki za pomocą usługi WinRM</span><span class="sxs-lookup"><span data-stu-id="be127-118">Registers that plug-in with WinRM</span></span>

### <a name="registration"></a><span data-ttu-id="be127-119">Rejestracja</span><span class="sxs-lookup"><span data-stu-id="be127-119">Registration</span></span>

<span data-ttu-id="be127-120">Skrypt musi zostać wykonana w ramach sesji programu PowerShell z poziomu administratora i jest uruchamiany w dwóch trybach.</span><span class="sxs-lookup"><span data-stu-id="be127-120">The script must be executed within an Administrator-level PowerShell session and runs in two modes.</span></span>

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a><span data-ttu-id="be127-121">Wykonane przez to wystąpienie programu PowerShell, która zarejestruje</span><span class="sxs-lookup"><span data-stu-id="be127-121">Executed by the instance of PowerShell that it will register</span></span>

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a><span data-ttu-id="be127-122">Wykonane przez inne wystąpienie programu PowerShell w imieniu wystąpienia, które zarejestruje</span><span class="sxs-lookup"><span data-stu-id="be127-122">Executed by another instance of PowerShell on behalf of the instance that it will register</span></span>

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

<span data-ttu-id="be127-123">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="be127-123">For Example:</span></span>

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

<span data-ttu-id="be127-124">**UWAGA:** Skrypt rejestrowania komunikacji zdalnej spowoduje ponowne uruchomienie usługi WinRM, dzięki czemu wszystkie istniejące sesje PSRP przestanie obowiązywać natychmiast, po uruchomieniu skryptu.</span><span class="sxs-lookup"><span data-stu-id="be127-124">**NOTE:** The remoting registration script will restart WinRM, so all existing PSRP sessions will terminate immediately after the script is run.</span></span> <span data-ttu-id="be127-125">Jeśli podczas sesji zdalnej, utracą połączenia.</span><span class="sxs-lookup"><span data-stu-id="be127-125">If run during a remote session, this will terminate the connection.</span></span>

## <a name="how-to-connect-to-the-new-endpoint"></a><span data-ttu-id="be127-126">Jak połączyć się z nowego punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="be127-126">How to Connect to the New Endpoint</span></span>

<span data-ttu-id="be127-127">Utwórz sesję programu PowerShell do nowego punktu końcowego programu PowerShell, określając `-ConfigurationName "some endpoint name"`.</span><span class="sxs-lookup"><span data-stu-id="be127-127">Create a PowerShell session to the new PowerShell endpoint by specifying `-ConfigurationName "some endpoint name"`.</span></span> <span data-ttu-id="be127-128">Aby nawiązać połączenie z wystąpieniem programu PowerShell w powyższym przykładzie, należy użyć albo:</span><span class="sxs-lookup"><span data-stu-id="be127-128">To connect to the PowerShell instance from the example above, use either:</span></span>

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

<span data-ttu-id="be127-129">Należy pamiętać, że `New-PSSession` i `Enter-PSSession` wywołań, które nie określają `-ConfigurationName` będą ukierunkowane na domyślny punkt końcowy programu PowerShell, `microsoft.powershell`.</span><span class="sxs-lookup"><span data-stu-id="be127-129">Note that `New-PSSession` and `Enter-PSSession` invocations that do not specify `-ConfigurationName` will target the default PowerShell endpoint, `microsoft.powershell`.</span></span>