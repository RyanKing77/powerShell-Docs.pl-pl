---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Zmienianie stanu komputera
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
ms.openlocfilehash: f8a2ed6a1a0390021eb633c9af64a725146ad136
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293065"
---
# <a name="changing-computer-state"></a>Zmienianie stanu komputera

Można zresetować komputera w programie Windows PowerShell, użyj standardowych narzędzi wiersza polecenia lub klasy WMI. Mimo, że używasz programu Windows PowerShell tylko po to, aby uruchomić narzędzie, jak zmienić stanu zasilania komputera w programie Windows PowerShell ilustruje niektóre ważne informacje o pracy z zewnętrznych narzędzi w programie Windows PowerShell.

## <a name="locking-a-computer"></a>Blokowanie komputera

Jedynym sposobem, aby zablokować komputer bezpośrednio przy użyciu standardowych narzędzi dostępnych jest wywołanie **LockWorkstation()** działa w programach **user32.dll**:

```
rundll32.exe user32.dll,LockWorkStation
```

To polecenie natychmiast blokuje stacji roboczej. Używa ona *rundll32.exe*, który uruchamia Windows biblioteki dll (i zapisuje ich bibliotek do wielokrotnego użytku) do uruchamiania user32.dll, bibliotekę funkcji zarządzania Windows.

Gdy możesz zablokować stacji roboczej podczas szybkiego przełączania użytkowników jest włączone, takie jak Windows XP, komputer wyświetli ekran logowania użytkownika, a nie od bieżącego użytkownika wygaszacz ekranu.

Aby zamknąć określonej sesji na serwerze terminali, należy użyć **tsshutdn.exe** narzędzie wiersza polecenia.

## <a name="logging-off-the-current-session"></a>Trwa wylogowywanie w bieżącej sesji

Aby wylogować sesji w systemie lokalnym, można użyć kilku różnych technik. Najprostszym sposobem jest użycie narzędzia wiersza polecenia zdalnego pulpitu/usługi terminalowe **logoff.exe** (Aby uzyskać szczegółowe informacje w wierszu polecenia programu Windows PowerShell wpisz **wylogowania /?**). Aby wylogować się z bieżącej aktywnej sesji, wpisz **wylogowania** bez argumentów.

Można również użyć **shutdown.exe** narzędzia z opcją jego wylogowania:

```
shutdown.exe -l
```

Trzecią opcją jest korzystanie z usługi WMI. Klasy Win32_OperatingSystem ma metodę Win32Shutdown. Wywoływanie metody z flagą 0 inicjuje wylogowaniu:

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

Aby uzyskać więcej informacji i znaleźć inne funkcje Metoda Win32Shutdown zobacz "Win32Shutdown metody z klasy Win32_OperatingSystem" w bibliotece MSDN.

## <a name="shutting-down-or-restarting-a-computer"></a>Zamykanie lub ponowne uruchomienie komputera

Zamykanie i ponowne uruchamianie komputerów są zwykle te same typy zadań. Narzędzia, które zamykanie komputera uruchomi ogólnie ją ponownie także — i odwrotnie. Istnieją dwie proste opcje ponownego uruchamiania komputera za pomocą programu Windows PowerShell. Za pomocą Tsshutdn.exe lub Shutdown.exe odpowiednie argumenty. Można uzyskać informacji o szczegółowym zestawieniem użycia **tsshutdn.exe /?** lub **shutdown.exe /?**.

Możesz również wykonać zamknięcia i ponownego uruchamiania działania bezpośrednio z programu Windows PowerShell również.

Aby wyłączyć komputer, użyj polecenia Stop-Computer

```powershell
Stop-Computer
```

Aby ponownie uruchomić system operacyjny, użyj polecenia Restart-Computer

```powershell
Restart-Computer
```

Aby wymusić natychmiastowe ponowne uruchomienie komputera, użyj parametru - Force.

```powershell
Restart-Computer -Force
```
