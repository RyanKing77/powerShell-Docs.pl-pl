---
ms.date: 06/05/2017
keywords: PowerShell, polecenie cmdlet
title: Zmienianie stanu komputera
ms.openlocfilehash: de3e31e358548943a015b7bba275c4461202b20f
ms.sourcegitcommit: d1ba596f9e0d4df9565601a70687a126d535c917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2019
ms.locfileid: "70386283"
---
# <a name="changing-computer-state"></a>Zmienianie stanu komputera

Aby zresetować komputer w programie Windows PowerShell, należy użyć standardowego narzędzia wiersza polecenia, usługi WMI lub klasy CIM. Chociaż używasz programu Windows PowerShell tylko do uruchamiania tego narzędzia, zapoznaj się z informacjami na temat zmiany stanu zasilacza komputera w programie Windows PowerShell. przedstawiono w nim pewne istotne informacje dotyczące pracy z narzędziami zewnętrznymi w programie Windows PowerShell.

## <a name="locking-a-computer"></a>Blokowanie komputera

Jedynym sposobem blokowania komputera bezpośrednio przy użyciu standardowych dostępnych narzędzi jest wywołanie funkcji **LockWorkstation ()** w **User32. dll**:

```
rundll32.exe user32.dll,LockWorkStation
```

To polecenie natychmiast blokuje stację roboczą. Używa *rundll32. exe*, który uruchamia biblioteki DLL systemu Windows (i zapisuje ich biblioteki do wielokrotnego użycia) do uruchamiania User32. dll, biblioteki funkcji zarządzania systemu Windows.

Po zablokowaniu stacji roboczej, gdy jest włączone szybkie przełączanie użytkowników, na przykład w systemie Windows XP, komputer wyświetla ekran logowania użytkownika zamiast uruchamiania wygaszacza ekranu bieżącego użytkownika.

Aby zamknąć określone sesje na serwerze terminali, użyj narzędzia wiersza polecenia **tsshutdn. exe** .

## <a name="logging-off-the-current-session"></a>Wylogowywanie z bieżącej sesji

Można użyć kilku różnych technik do wylogowywania sesji w systemie lokalnym. Najprostszym sposobem jest użycie narzędzia wiersza polecenia Pulpit zdalny/Terminal Services, **Logoff. exe** (Aby uzyskać szczegółowe informacje, w wierszu poleceń programu Windows PowerShell wpisz **Logoff/?** ). Aby wylogować bieżącą aktywną sesję, wpisz polecenie **Logoff** bez argumentów.

Można również użyć narzędzia **Shutdown. exe** z opcją wylogowania:

```
shutdown.exe -l
```

Innym rozwiązaniem jest użycie usługi WMI. Klasa Win32_OperatingSystem ma metodę Win32Shutdown. Wywoływanie metody z flagą 0 inicjuje wylogowanie:

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

Aby uzyskać więcej informacji i znaleźć inne funkcje metody Win32Shutdown, zobacz "Metoda Win32Shutdown klasy Win32_OperatingSystem" w witrynie MSDN.

Na koniec można użyć modelu CIM z tą samą klasą Win32_OperatingSystem, jak opisano powyżej w metodzie WMI.

```powershell
Get-CIMInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a>Zamykanie lub ponowne uruchamianie komputera

Zamykanie i ponowne uruchamianie komputerów jest zwykle tymi samymi typami zadań. Narzędzia, które wyłączają komputer, będą na ogół również ponownie uruchomione i na odwrót. Dostępne są dwie proste opcje ponownego uruchamiania komputera z programu Windows PowerShell. Użyj programu TSShutdn. exe lub Shutdown. exe z odpowiednimi argumentami. Możesz uzyskać szczegółowe informacje dotyczące użycia z programu **tsshutdn. exe/?** lub **Shutdown. exe/?** .

Można również wykonywać operacje zamykania i ponownego uruchamiania bezpośrednio z programu Windows PowerShell.

Aby zamknąć komputer, użyj polecenia Stop-Computer

```powershell
Stop-Computer
```

Aby ponownie uruchomić system operacyjny, użyj polecenia Uruchom ponownie komputer.

```powershell
Restart-Computer
```

Aby wymusić natychmiastowe ponowne uruchomienie komputera, użyj parametru-Force.

```powershell
Restart-Computer -Force
```
