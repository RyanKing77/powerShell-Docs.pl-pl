---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Zmienianie stanu komputera
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
ms.openlocfilehash: c659ad54325b0f7305f882e1cb9607062abad6a4
ms.sourcegitcommit: 2ffb9fa92129c2001379ca2c17646466721f7165
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251521"
---
# <a name="changing-computer-state"></a>Zmienianie stanu komputera

Resetowanie komputera w programie Windows PowerShell, przy użyciu standardowego narzędzia wiersza polecenia lub klasy WMI. Mimo że używasz programu Windows PowerShell do uruchamiania narzędzia tylko, poznanie zmiany stanu zasilania komputera w programie Windows PowerShell ilustruje niektóre ważne informacje o pracy z zewnętrznych narzędzi w programie Windows PowerShell.

### <a name="locking-a-computer"></a>Blokowanie komputera

Jest jedynym sposobem, aby zablokować komputer bezpośrednio przy użyciu standardowych narzędzi dostępnych do wywołania **LockWorkstation()** działać w **user32.dll**:

```
rundll32.exe user32.dll,LockWorkStation
```

To polecenie natychmiast blokuje stacji roboczej. Używa *rundll32.exe*, który uruchamia biblioteki DLL systemu Windows (i zapisanie ich biblioteki do wielokrotnego użytku) do uruchamiania user32.dll, biblioteka funkcji zarządzania systemu Windows.

Po zablokowaniu stacji roboczej włączonym szybkiego przełączania użytkowników, takich jak w systemie Windows XP, komputer wyświetla ekran logowania użytkownika, a nie rozpoczyna wygaszacz ekranu bieżącego użytkownika.

Aby zamknąć określonej sesji na serwer terminali, należy użyć **tsshutdn.exe** narzędzia wiersza polecenia.

### <a name="logging-off-the-current-session"></a>Wylogowywanie bieżącej sesji

Można użyć kilku różnych technik wylogowywanie sesji w systemie lokalnym. Najprostszym sposobem jest użycie narzędzia wiersza polecenia usługi zdalnego pulpitu/Terminal **logoff.exe** (Aby uzyskać więcej informacji, w wierszu polecenia programu Windows PowerShell wpisz **wylogowanie /?**). Aby wylogować się z bieżącym aktywnej sesji, wpisz **wylogowywania** bez argumentów.

Można również użyć **shutdown.exe** narzędzie z opcją jego wylogowaniu:

```
shutdown.exe -l
```

Trzecia opcja jest korzystanie z usługi WMI. Klasy Win32_OperatingSystem ma metodę Win32Shutdown. Wywoływanie metody z ustawioną flagą 0 inicjuje wylogowaniu:

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

Aby uzyskać więcej informacji, a także znalezienia innych funkcji Metoda Win32Shutdown zobacz "Win32Shutdown metoda z klasy Win32_OperatingSystem" w witrynie MSDN.

### <a name="shutting-down-or-restarting-a-computer"></a>Wyłączanie lub ponowne uruchomienie komputera

Zamykanie i ponowne uruchamianie komputerów są zwykle te same rodzaje zadań. Narzędzia, które zamykanie komputera zazwyczaj uruchomi go również — i na odwrót. Dostępne są dwie opcje prostego do ponownego uruchomienia komputera w programie Windows PowerShell. Za pomocą Tsshutdn.exe lub Shutdown.exe odpowiednie argumenty. Można uzyskać informacji o szczegółowe dane użycia **tsshutdn.exe /?** lub **shutdown.exe /?**.

Można również wykonać zamknięcia i ponownego uruchamiania działania bezpośrednio z programu Windows PowerShell również.

Aby wyłączyć komputer, użyj polecenia ponownego uruchomienia komputera

```powershell
stop-computer
```

Aby ponownie uruchomić system operacyjny, użyj polecenia ponownego uruchomienia komputera

```powershell
restart-computer
```
