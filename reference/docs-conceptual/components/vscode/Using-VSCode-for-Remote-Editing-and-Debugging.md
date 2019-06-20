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
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Zdalne edytowanie i debugowanie za pomocą programu Visual Studio Code

Dla użytkowników, którzy znają środowiska ISE, może pamiętasz, że można uruchomić `psedit file.ps1` z zintegrowana Konsola umożliwia otwieranie plików — lokalnego lub zdalnego — kliknij prawym przyciskiem myszy w środowisku ISE.

Ta funkcja jest również dostępna w rozszerzeniu programu PowerShell dla programu VSCode. Ten przewodnik pokazuje, jak to zrobić.

## <a name="prerequisites"></a>Wymagania wstępne

W tym przewodniku założono, że masz:

- zdalnego zasobu (np: maszyna wirtualna, kontener) czy masz dostęp do
- PowerShell działających na go i na komputerze hosta
- VSCode i rozszerzenia programu PowerShell dla programu VSCode

Ta funkcja działa w programie Windows PowerShell i PowerShell Core.

Ta funkcja działa również podczas nawiązywania połączenia z komputerem zdalnym za pośrednictwem usługi WinRM, programu PowerShell Direct lub protokołu SSH. Jeśli chcesz używać protokołu SSH, ale korzystają z Windows, zapoznaj się z [Win32 wersję protokołu SSH](https://github.com/PowerShell/Win32-OpenSSH)!

> [!IMPORTANT]
> `Open-EditorFile` i `psedit` polecenia działają tylko **zintegrowana konsola programu PowerShell** utworzone przez rozszerzenie programu PowerShell dla programu VSCode.

## <a name="usage-examples"></a>Przykłady użycia

W tych przykładach zdalnego, edytowanie i debugowanie z MacBook Pro do maszyny Wirtualnej systemu Ubuntu działających na platformie Azure. Ten proces jest taka sama na Windows.

### <a name="local-file-editing-with-open-editorfile"></a>Edytowanie w programie Open EditorFile pliku lokalnego

Z rozszerzeniem programu PowerShell dla programu VSCode pracę i otwarty zintegrowana konsola programu PowerShell, firma Microsoft można wpisać `Open-EditorFile foo.ps1` lub `psedit foo.ps1` można otworzyć pliku lokalnego foo.ps1 po prawej stronie w edytorze.

![Otwórz EditorFile foo.ps1 działa lokalnie](images/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> Plik `foo.ps1` musi już istnieć.

Z tego miejsca możemy wykonywać następujące czynności:

- Dodawanie punktów przerwania do odstępu

  ![dodając punkt przerwania, aby odstępu](images/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- Naciśnij klawisz F5, aby debugować skrypt programu PowerShell.

  ![Profilowanie lokalnego skryptu programu PowerShell](images/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

Podczas debugowania można korzystać z konsoli debugowania, zapoznaj się z zmienne w zakresie z lewej strony oraz wszystkich innych standardowych narzędzi do debugowania.

### <a name="remote-file-editing-with-open-editorfile"></a>Edytowanie w programie Open EditorFile pliku zdalnego

Teraz. możemy przejść do pliku zdalnego, edytowanie i debugowanie. Kroki są prawie takie same, po prostu jedyną operacją, której potrzebujemy, należy najpierw-wprowadź naszym sesji programu PowerShell do zdalnego serwera.

Aby to zrobić, istnieje dla polecenia cmdlet. Jest on nazywany `Enter-PSSession`.

To wyjaśnienie watered w dół, polecenia cmdlet:

- `Enter-PSSession -ComputerName foo` Uruchamia sesję za pośrednictwem usługi WinRM
- `Enter-PSSession -ContainerId foo` i `Enter-PSSession -VmId foo` rozpocząć sesję za pomocą programu PowerShell bezpośrednio
- `Enter-PSSession -HostName foo` Uruchamia sesję za pośrednictwem protokołu SSH

Aby uzyskać więcej informacji, zobacz dokumentację dla [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).

Ponieważ użyjemy z systemu macOS do maszyny Wirtualnej systemu Ubuntu na platformie Azure, możemy korzystają z protokołu SSH dla niego komunikację zdalną.

Najpierw w zintegrowana Konsola Uruchom `Enter-PSSession`. Masz połączenie sesji zdalnej podczas `[<hostname>]` pokazano maksymalnie z lewej strony z wiersza.

![Wywołanie Enter-PSSession](images/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

Teraz możemy te same kroki tak, jakby możemy edytowania lokalnego skryptu.

1. Uruchom `Open-EditorFile test.ps1` lub `psedit test.ps1` można otworzyć zdalnej `test.ps1` pliku

  ![Open — EditorFile pliku test.ps1](images/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. Edytuj plik/Ustawianie punktów przerwania

   ![Edytuj i ustawiania punktów przerwania](images/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. Rozpocznij debugowanie (F5) pliku zdalnego

   ![debugowanie pliku zdalnego](images/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

Jeśli masz jakiekolwiek problemy, możesz otworzyć problemy w [repozytorium GitHub](https://github.com/powershell/vscode-powershell).
