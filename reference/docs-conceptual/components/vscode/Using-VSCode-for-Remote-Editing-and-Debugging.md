---
title: Zdalne edytowanie i debugowanie za pomocą programu Visual Studio Code
description: Zdalne edytowanie i debugowanie za pomocą programu Visual Studio Code
ms.date: 06/13/2019
ms.openlocfilehash: ae3b7a3709498fcd547a48d0849b0dc880217225
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263910"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="91f09-103">Zdalne edytowanie i debugowanie za pomocą programu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="91f09-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="91f09-104">Dla użytkowników, którzy znają środowiska ISE, może pamiętasz, że można uruchomić `psedit file.ps1` z zintegrowana Konsola umożliwia otwieranie plików — lokalnego lub zdalnego — kliknij prawym przyciskiem myszy w środowisku ISE.</span><span class="sxs-lookup"><span data-stu-id="91f09-104">For those of you that are familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="91f09-105">Ta funkcja jest również dostępna w rozszerzeniu programu PowerShell dla programu VSCode.</span><span class="sxs-lookup"><span data-stu-id="91f09-105">This feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="91f09-106">Ten przewodnik pokazuje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="91f09-106">This guide shows you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="91f09-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="91f09-107">Prerequisites</span></span>

<span data-ttu-id="91f09-108">W tym przewodniku założono, że masz:</span><span class="sxs-lookup"><span data-stu-id="91f09-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="91f09-109">zdalnego zasobu (np: maszyna wirtualna, kontener) czy masz dostęp do</span><span class="sxs-lookup"><span data-stu-id="91f09-109">A remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="91f09-110">PowerShell działających na go i na komputerze hosta</span><span class="sxs-lookup"><span data-stu-id="91f09-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="91f09-111">VSCode i rozszerzenia programu PowerShell dla programu VSCode</span><span class="sxs-lookup"><span data-stu-id="91f09-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="91f09-112">Ta funkcja działa w programie Windows PowerShell i PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="91f09-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="91f09-113">Ta funkcja działa również podczas nawiązywania połączenia z komputerem zdalnym za pośrednictwem usługi WinRM, programu PowerShell Direct lub protokołu SSH.</span><span class="sxs-lookup"><span data-stu-id="91f09-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="91f09-114">Jeśli chcesz używać protokołu SSH, ale korzystają z Windows, zapoznaj się z [Win32 wersję protokołu SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span><span class="sxs-lookup"><span data-stu-id="91f09-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="91f09-115">`Open-EditorFile` i `psedit` polecenia działają tylko **zintegrowana konsola programu PowerShell** utworzone przez rozszerzenie programu PowerShell dla programu VSCode.</span><span class="sxs-lookup"><span data-stu-id="91f09-115">The `Open-EditorFile` and `psedit` commands only work in the **PowerShell Integrated Console** created by the PowerShell extension for VSCode.</span></span>

## <a name="usage-examples"></a><span data-ttu-id="91f09-116">Przykłady użycia</span><span class="sxs-lookup"><span data-stu-id="91f09-116">Usage examples</span></span>

<span data-ttu-id="91f09-117">W tych przykładach zdalnego, edytowanie i debugowanie z MacBook Pro do maszyny Wirtualnej systemu Ubuntu działających na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="91f09-117">These examples show remote editing and debugging from a MacBook Pro to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="91f09-118">Ten proces jest taka sama na Windows.</span><span class="sxs-lookup"><span data-stu-id="91f09-118">The process is identical on Windows.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="91f09-119">Edytowanie w programie Open EditorFile pliku lokalnego</span><span class="sxs-lookup"><span data-stu-id="91f09-119">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="91f09-120">Z rozszerzeniem programu PowerShell dla programu VSCode pracę i otwarty zintegrowana konsola programu PowerShell, firma Microsoft można wpisać `Open-EditorFile foo.ps1` lub `psedit foo.ps1` można otworzyć pliku lokalnego foo.ps1 po prawej stronie w edytorze.</span><span class="sxs-lookup"><span data-stu-id="91f09-120">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Otwórz EditorFile foo.ps1 działa lokalnie](images/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> <span data-ttu-id="91f09-122">Plik `foo.ps1` musi już istnieć.</span><span class="sxs-lookup"><span data-stu-id="91f09-122">The file `foo.ps1` must already exist.</span></span>

<span data-ttu-id="91f09-123">Z tego miejsca możemy wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="91f09-123">From there, we can:</span></span>

- <span data-ttu-id="91f09-124">Dodawanie punktów przerwania do odstępu</span><span class="sxs-lookup"><span data-stu-id="91f09-124">Add breakpoints to the gutter</span></span>

  ![dodając punkt przerwania, aby odstępu](images/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- <span data-ttu-id="91f09-126">Naciśnij klawisz F5, aby debugować skrypt programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="91f09-126">Hit F5 to debug the PowerShell script.</span></span>

  ![Profilowanie lokalnego skryptu programu PowerShell](images/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

<span data-ttu-id="91f09-128">Podczas debugowania można korzystać z konsoli debugowania, zapoznaj się z zmienne w zakresie z lewej strony oraz wszystkich innych standardowych narzędzi do debugowania.</span><span class="sxs-lookup"><span data-stu-id="91f09-128">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="91f09-129">Edytowanie w programie Open EditorFile pliku zdalnego</span><span class="sxs-lookup"><span data-stu-id="91f09-129">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="91f09-130">Teraz. możemy przejść do pliku zdalnego, edytowanie i debugowanie.</span><span class="sxs-lookup"><span data-stu-id="91f09-130">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="91f09-131">Kroki są prawie takie same, po prostu jedyną operacją, której potrzebujemy, należy najpierw-wprowadź naszym sesji programu PowerShell do zdalnego serwera.</span><span class="sxs-lookup"><span data-stu-id="91f09-131">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="91f09-132">Aby to zrobić, istnieje dla polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="91f09-132">There's a cmdlet for to do so.</span></span> <span data-ttu-id="91f09-133">Jest on nazywany `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="91f09-133">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="91f09-134">To wyjaśnienie watered w dół, polecenia cmdlet:</span><span class="sxs-lookup"><span data-stu-id="91f09-134">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="91f09-135">`Enter-PSSession -ComputerName foo` Uruchamia sesję za pośrednictwem usługi WinRM</span><span class="sxs-lookup"><span data-stu-id="91f09-135">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="91f09-136">`Enter-PSSession -ContainerId foo` i `Enter-PSSession -VmId foo` rozpocząć sesję za pomocą programu PowerShell bezpośrednio</span><span class="sxs-lookup"><span data-stu-id="91f09-136">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="91f09-137">`Enter-PSSession -HostName foo` Uruchamia sesję za pośrednictwem protokołu SSH</span><span class="sxs-lookup"><span data-stu-id="91f09-137">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="91f09-138">Aby uzyskać więcej informacji, zobacz dokumentację dla [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="91f09-138">For more information, see the documentation for [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span></span>

<span data-ttu-id="91f09-139">Ponieważ użyjemy z systemu macOS do maszyny Wirtualnej systemu Ubuntu na platformie Azure, możemy korzystają z protokołu SSH dla niego komunikację zdalną.</span><span class="sxs-lookup"><span data-stu-id="91f09-139">Since we are going from macOS to an Ubuntu VM in Azure, we are using SSH for remoting.</span></span>

<span data-ttu-id="91f09-140">Najpierw w zintegrowana Konsola Uruchom `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="91f09-140">First, in the Integrated Console, run `Enter-PSSession`.</span></span> <span data-ttu-id="91f09-141">Masz połączenie sesji zdalnej podczas `[<hostname>]` pokazano maksymalnie z lewej strony z wiersza.</span><span class="sxs-lookup"><span data-stu-id="91f09-141">You're connected to the remote session when `[<hostname>]` shows up to the left of your prompt.</span></span>

![Wywołanie Enter-PSSession](images/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

<span data-ttu-id="91f09-143">Teraz możemy te same kroki tak, jakby możemy edytowania lokalnego skryptu.</span><span class="sxs-lookup"><span data-stu-id="91f09-143">Now, we can do the same steps as if we are editing a local script.</span></span>

1. <span data-ttu-id="91f09-144">Uruchom `Open-EditorFile test.ps1` lub `psedit test.ps1` można otworzyć zdalnej `test.ps1` pliku</span><span class="sxs-lookup"><span data-stu-id="91f09-144">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file</span></span>

  ![Open — EditorFile pliku test.ps1](images/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. <span data-ttu-id="91f09-146">Edytuj plik/Ustawianie punktów przerwania</span><span class="sxs-lookup"><span data-stu-id="91f09-146">Edit the file/set breakpoints</span></span>

   ![Edytuj i ustawiania punktów przerwania](images/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. <span data-ttu-id="91f09-148">Rozpocznij debugowanie (F5) pliku zdalnego</span><span class="sxs-lookup"><span data-stu-id="91f09-148">Start debugging (F5) the remote file</span></span>

   ![debugowanie pliku zdalnego](images/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

<span data-ttu-id="91f09-150">Jeśli masz jakiekolwiek problemy, możesz otworzyć problemy w [repozytorium GitHub](https://github.com/powershell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="91f09-150">If you have any problems, you can open issues in the [GitHub repo](https://github.com/powershell/vscode-powershell).</span></span>
