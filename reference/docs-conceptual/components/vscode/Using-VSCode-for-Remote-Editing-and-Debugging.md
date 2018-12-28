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
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Edytowanie i debugowanie zdalne za pomocą programu Visual Studio Code

Dla osób, które były zapoznać się z środowiska ISE może pamiętasz, że można uruchomić `psedit file.ps1` z zintegrowana Konsola umożliwia otwieranie plików — lokalnego lub zdalnego — kliknij prawym przyciskiem myszy w środowisku ISE.

Jak okazuje się, ta funkcja jest również dostępna w rozszerzeniu programu PowerShell dla programu VSCode. W przewodniku opisano, jak to zrobić.

## <a name="prerequisites"></a>Wymagania wstępne

W tym przewodniku założono, że masz:

- zdalnego zasobu (np: maszyna wirtualna, kontener) czy masz dostęp do
- PowerShell działających na go i na komputerze hosta
- VSCode i rozszerzenia programu PowerShell dla programu VSCode

Ta funkcja działa w programie Windows PowerShell i PowerShell Core.

Ta funkcja działa również podczas nawiązywania połączenia z komputerem zdalnym za pośrednictwem usługi WinRM, programu PowerShell Direct lub protokołu SSH. Jeśli chcesz używać protokołu SSH, ale korzystają z Windows, zapoznaj się z [Win32 wersję protokołu SSH](https://github.com/PowerShell/Win32-OpenSSH)!

## <a name="lets-go"></a>Chodźmy

W tej sekcji I omówiono zdalne edytowanie i debugowanie z moich MacBook Pro do maszyny Wirtualnej systemu Ubuntu działających na platformie Azure. Czy mogę może nie być sygnalizowany Windows, ale **procesu jest taka sama**.

### <a name="local-file-editing-with-open-editorfile"></a>Edytowanie w programie Open EditorFile pliku lokalnego

Z rozszerzeniem programu PowerShell dla programu VSCode pracę i otwarty zintegrowana konsola programu PowerShell, firma Microsoft można wpisać `Open-EditorFile foo.ps1` lub `psedit foo.ps1` można otworzyć pliku lokalnego foo.ps1 po prawej stronie w edytorze.

![Otwórz EditorFile foo.ps1 działa lokalnie](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> foo.ps1 musi już istnieć.

Z tego miejsca możemy wykonywać następujące czynności:

dodać punkty przerwania na oprawę ![Dodawanie punkt przerwania, aby odstępu](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)

i naciśnij klawisz F5, aby debugować skrypt programu PowerShell.
![Profilowanie lokalnego skryptu programu PowerShell](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)

Podczas debugowania można korzystać z konsoli debugowania, zapoznaj się z zmienne w zakresie z lewej strony oraz wszystkich innych standardowych narzędzi do debugowania.

### <a name="remote-file-editing-with-open-editorfile"></a>Edytowanie w programie Open EditorFile pliku zdalnego

Teraz. możemy przejść do pliku zdalnego, edytowanie i debugowanie. Kroki są prawie takie same, po prostu jedyną operacją, której potrzebujemy, należy najpierw-wprowadź naszym sesji programu PowerShell do zdalnego serwera.

Aby to zrobić, istnieje dla polecenia cmdlet. Jest on nazywany `Enter-PSSession`.

To wyjaśnienie watered w dół, polecenia cmdlet:

- `Enter-PSSession -ComputerName foo` Uruchamia sesję za pośrednictwem usługi WinRM
- `Enter-PSSession -ContainerId foo` i `Enter-PSSession -VmId foo` rozpocząć sesję za pomocą programu PowerShell bezpośrednio
- `Enter-PSSession -HostName foo` Uruchamia sesję za pośrednictwem protokołu SSH

Aby uzyskać więcej informacji na `Enter-PSSession`, zapoznaj się z dokumentami [tutaj](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).

Czy mogę używać SSH dla niego komunikację zdalną ponieważ zamierzam z systemu macOS do maszyny Wirtualnej systemu Ubuntu na platformie Azure.

Po pierwsze w konsoli zintegrowane uruchommy naszych Enter-PSSession. Będziesz wiedzieć, że jesteś w sesji, ponieważ `[something]` pojawią się po lewej stronie znaku zgłoszenia.

![Wywołanie Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

Z tego miejsca możemy konkretne kroki tak, jakby możemy edytowanego lokalnego skryptu.

1. Uruchom `Open-EditorFile test.ps1` lub `psedit test.ps1` można otworzyć zdalnej `test.ps1` pliku ![Open-EditorFile pliku test.ps1](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)
2. Edytuj plik/Ustawianie punktów przerwania ![Edytuj i ustawiania punktów przerwania](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. Rozpocznij debugowanie (F5) pliku zdalnego

![debugowanie pliku zdalnego](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

To wszystko jest do niego! Mamy nadzieję, że ten przewodnik pomogła wyczyść się pytania dotyczące zdalnego debugowania i edytowania programu PowerShell w programie VSCode.

Jeśli masz jakiekolwiek problemy, możesz otworzyć problemów [w repozytorium GitHub](http://github.com/powershell/vscode-powershell).
