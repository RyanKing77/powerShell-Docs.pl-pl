---
title: Edytowanie i debugowanie zdalne za pomocą programu Visual Studio Code
description: Edytowanie i debugowanie zdalne za pomocą programu Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: bab1a629a7e9dafd5957cf93025abb18b8a4f326
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655544"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="5c1e4-103">Edytowanie i debugowanie zdalne za pomocą programu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5c1e4-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="5c1e4-104">Dla osób, które były zapoznać się z środowiska ISE może pamiętasz, że można uruchomić `psedit file.ps1` z zintegrowana Konsola umożliwia otwieranie plików — lokalnego lub zdalnego — kliknij prawym przyciskiem myszy w środowisku ISE.</span><span class="sxs-lookup"><span data-stu-id="5c1e4-104">For those of you that were familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="5c1e4-105">Jak okazuje się, ta funkcja jest również dostępna w rozszerzeniu programu PowerShell dla programu VSCode.</span><span class="sxs-lookup"><span data-stu-id="5c1e4-105">As it turns out, this feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="5c1e4-106">W przewodniku opisano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="5c1e4-106">This guide will show you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5c1e4-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="5c1e4-107">Prerequisites</span></span>

<span data-ttu-id="5c1e4-108">W tym przewodniku założono, że masz:</span><span class="sxs-lookup"><span data-stu-id="5c1e4-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="5c1e4-109">zdalnego zasobu (np: maszyna wirtualna, kontener) czy masz dostęp do</span><span class="sxs-lookup"><span data-stu-id="5c1e4-109">a remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="5c1e4-110">PowerShell działających na go i na komputerze hosta</span><span class="sxs-lookup"><span data-stu-id="5c1e4-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="5c1e4-111">VSCode i rozszerzenia programu PowerShell dla programu VSCode</span><span class="sxs-lookup"><span data-stu-id="5c1e4-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="5c1e4-112">Ta funkcja działa w programie Windows PowerShell i PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="5c1e4-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="5c1e4-113">Ta funkcja działa również podczas nawiązywania połączenia z komputerem zdalnym za pośrednictwem usługi WinRM, programu PowerShell Direct lub protokołu SSH.</span><span class="sxs-lookup"><span data-stu-id="5c1e4-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="5c1e4-114">Jeśli chcesz używać protokołu SSH, ale korzystają z Windows, zapoznaj się z [Win32 wersję protokołu SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span><span class="sxs-lookup"><span data-stu-id="5c1e4-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

## <a name="lets-go"></a><span data-ttu-id="5c1e4-115">Chodźmy</span><span class="sxs-lookup"><span data-stu-id="5c1e4-115">Let's go</span></span>

<span data-ttu-id="5c1e4-116">W tej sekcji I omówiono zdalne edytowanie i debugowanie z moich MacBook Pro do maszyny Wirtualnej systemu Ubuntu działających na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="5c1e4-116">In this section, I'll walk through remote editing and debugging from my MacBook Pro, to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="5c1e4-117">Czy mogę może nie być sygnalizowany Windows, ale **procesu jest taka sama**.</span><span class="sxs-lookup"><span data-stu-id="5c1e4-117">I might not be using Windows, but **the process is identical**.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="5c1e4-118">Edytowanie w programie Open EditorFile pliku lokalnego</span><span class="sxs-lookup"><span data-stu-id="5c1e4-118">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="5c1e4-119">Z rozszerzeniem programu PowerShell dla programu VSCode pracę i otwarty zintegrowana konsola programu PowerShell, firma Microsoft można wpisać `Open-EditorFile foo.ps1` lub `psedit foo.ps1` można otworzyć pliku lokalnego foo.ps1 po prawej stronie w edytorze.</span><span class="sxs-lookup"><span data-stu-id="5c1e4-119">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Otwórz EditorFile foo.ps1 działa lokalnie](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> <span data-ttu-id="5c1e4-121">foo.ps1 musi już istnieć.</span><span class="sxs-lookup"><span data-stu-id="5c1e4-121">foo.ps1 must already exist.</span></span>

<span data-ttu-id="5c1e4-122">Z tego miejsca możemy wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="5c1e4-122">From there, we can:</span></span>

<span data-ttu-id="5c1e4-123">dodać punkty przerwania na oprawę ![Dodawanie punkt przerwania, aby odstępu](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span><span class="sxs-lookup"><span data-stu-id="5c1e4-123">add breakpoints to the gutter ![adding breakpoint to gutter](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span></span>

<span data-ttu-id="5c1e4-124">i naciśnij klawisz F5, aby debugować skrypt programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5c1e4-124">and hit F5 to debug the PowerShell script.</span></span>
<span data-ttu-id="5c1e4-125">![Profilowanie lokalnego skryptu programu PowerShell](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span><span class="sxs-lookup"><span data-stu-id="5c1e4-125">![debugging the PowerShell local script](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span></span>

<span data-ttu-id="5c1e4-126">Podczas debugowania można korzystać z konsoli debugowania, zapoznaj się z zmienne w zakresie z lewej strony oraz wszystkich innych standardowych narzędzi do debugowania.</span><span class="sxs-lookup"><span data-stu-id="5c1e4-126">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="5c1e4-127">Edytowanie w programie Open EditorFile pliku zdalnego</span><span class="sxs-lookup"><span data-stu-id="5c1e4-127">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="5c1e4-128">Teraz. możemy przejść do pliku zdalnego, edytowanie i debugowanie.</span><span class="sxs-lookup"><span data-stu-id="5c1e4-128">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="5c1e4-129">Kroki są prawie takie same, po prostu jedyną operacją, której potrzebujemy, należy najpierw-wprowadź naszym sesji programu PowerShell do zdalnego serwera.</span><span class="sxs-lookup"><span data-stu-id="5c1e4-129">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="5c1e4-130">Aby to zrobić, istnieje dla polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5c1e4-130">There's a cmdlet for to do so.</span></span> <span data-ttu-id="5c1e4-131">Jest on nazywany `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="5c1e4-131">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="5c1e4-132">To wyjaśnienie watered w dół, polecenia cmdlet:</span><span class="sxs-lookup"><span data-stu-id="5c1e4-132">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="5c1e4-133">`Enter-PSSession -ComputerName foo` Uruchamia sesję za pośrednictwem usługi WinRM</span><span class="sxs-lookup"><span data-stu-id="5c1e4-133">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="5c1e4-134">`Enter-PSSession -ContainerId foo` i `Enter-PSSession -VmId foo` rozpocząć sesję za pomocą programu PowerShell bezpośrednio</span><span class="sxs-lookup"><span data-stu-id="5c1e4-134">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="5c1e4-135">`Enter-PSSession -HostName foo` Uruchamia sesję za pośrednictwem protokołu SSH</span><span class="sxs-lookup"><span data-stu-id="5c1e4-135">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="5c1e4-136">Aby uzyskać więcej informacji na `Enter-PSSession`, zapoznaj się z dokumentami [tutaj](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="5c1e4-136">For more info on `Enter-PSSession`, check out the docs [here](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span></span>

<span data-ttu-id="5c1e4-137">Czy mogę używać SSH dla niego komunikację zdalną ponieważ zamierzam z systemu macOS do maszyny Wirtualnej systemu Ubuntu na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="5c1e4-137">I'll be using SSH for remoting since I'm going from macOS to an Ubuntu VM in Azure.</span></span>

<span data-ttu-id="5c1e4-138">Po pierwsze w konsoli zintegrowane uruchommy naszych Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="5c1e4-138">First, in the Integrated Console, let's run our Enter-PSSession.</span></span> <span data-ttu-id="5c1e4-139">Będziesz wiedzieć, że jesteś w sesji, ponieważ `[something]` pojawią się po lewej stronie znaku zgłoszenia.</span><span class="sxs-lookup"><span data-stu-id="5c1e4-139">You'll know that you're in the session because `[something]` will show up to the left of your prompt.</span></span>

![Wywołanie Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

<span data-ttu-id="5c1e4-141">Z tego miejsca możemy konkretne kroki tak, jakby możemy edytowanego lokalnego skryptu.</span><span class="sxs-lookup"><span data-stu-id="5c1e4-141">From there, we can do the exact steps as if we were editing a local script.</span></span>

1. <span data-ttu-id="5c1e4-142">Uruchom `Open-EditorFile test.ps1` lub `psedit test.ps1` można otworzyć zdalnej `test.ps1` pliku ![Open-EditorFile pliku test.ps1](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span><span class="sxs-lookup"><span data-stu-id="5c1e4-142">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file ![Open-EditorFile the test.ps1 file](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span></span>
2. <span data-ttu-id="5c1e4-143">Edytuj plik/Ustawianie punktów przerwania</span><span class="sxs-lookup"><span data-stu-id="5c1e4-143">Edit the file/set breakpoints</span></span> ![Edytuj i ustawiania punktów przerwania](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. <span data-ttu-id="5c1e4-145">Rozpocznij debugowanie (F5) pliku zdalnego</span><span class="sxs-lookup"><span data-stu-id="5c1e4-145">Start debugging (F5) the remote file</span></span>

![debugowanie pliku zdalnego](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

<span data-ttu-id="5c1e4-147">To wszystko jest do niego!</span><span class="sxs-lookup"><span data-stu-id="5c1e4-147">That's all there's to it!</span></span> <span data-ttu-id="5c1e4-148">Mamy nadzieję, że ten przewodnik pomogła wyczyść się pytania dotyczące zdalnego debugowania i edytowania programu PowerShell w programie VSCode.</span><span class="sxs-lookup"><span data-stu-id="5c1e4-148">We hope that this guide helped clear up any questions about remote debugging and editing PowerShell in VSCode.</span></span>

<span data-ttu-id="5c1e4-149">Jeśli masz jakiekolwiek problemy, możesz otworzyć problemów [w repozytorium GitHub](http://github.com/powershell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="5c1e4-149">If you have any problems, feel free to open issues [on the GitHub repo](http://github.com/powershell/vscode-powershell).</span></span>
