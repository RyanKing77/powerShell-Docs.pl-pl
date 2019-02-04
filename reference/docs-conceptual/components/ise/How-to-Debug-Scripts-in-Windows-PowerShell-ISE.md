---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Jak debugować skrypty w środowisku Windows PowerShell ISE
ms.openlocfilehash: b7af2de83a3f796a2057514e36ad8b74367e8ce2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684577"
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a>Jak debugować skrypty w środowisku Windows PowerShell ISE

W tym artykule opisano sposób debugowania skryptów na komputerze lokalnym za pomocą funkcji debugowania visual Windows PowerShell zintegrowane Scripting Environment (ISE).

## <a name="how-to-manage-breakpoints"></a>Jak zarządzać punktów przerwania

Punkt przerwania jest wyznaczonym miejscu w skrypcie, gdzie chcesz operację, aby wstrzymać tak, aby sprawdzić bieżący stan zmiennych i środowisko, w którym skrypt jest uruchomiony. Po skryptu jest wstrzymane przez punkt przerwania, możesz uruchamiać polecenia w okienku konsoli, aby sprawdzić stan skryptu.  Można danych wyjściowych zmiennych lub innych poleceń. Można nawet modyfikować wartości żadnych zmiennych, które są widoczne dla kontekstu obecnie uruchamianie skryptu. Po zbadaniu mają być wyświetlane, można wznowić działanie skryptu.

Trzy typy punktów przerwania można ustawić w środowisku debugowania programu Windows PowerShell:

1. **Wiersz punktu przerwania**. Skrypt wstrzymuje po osiągnięciu wiersza wyznaczonej podczas działania skryptu

2. **Punkt przerwania w zmiennej.** Skrypt wstrzymuje zawsze wtedy, gdy zmieni się wartość zmiennej wyznaczonym.

3. **Polecenie punkt przerwania.** Skrypt wstrzymuje zawsze wtedy, gdy wyznaczonym polecenia ma być uruchomiona podczas działania skryptu. Może zawierać parametrów, aby dokładniej przefiltrować punkt przerwania do operacji, które chcesz. Polecenie może być również funkcji, w której został utworzony.

Z tych opcji, w środowisku debugowania środowiska Windows PowerShell ISE można ustawić tylko punkty przerwania wiersza przy użyciu menu lub skróty klawiaturowe. Można ustawić dwa typy punktów przerwania, ale są skonfigurowane w okienku konsoli przy użyciu [PSBreakpoint zestaw](https://technet.microsoft.com/library/88d2d9ad-17dc-44ae-99aa-f841125b9dc8) polecenia cmdlet. W tej sekcji opisano, jak można wykonywać zadania debugowania w środowisku Windows PowerShell ISE przy użyciu menu, gdzie są dostępne i wykonywać szerszego zakresu poleceń w okienku konsoli, za pomocą skryptów.

### <a name="to-set-a-breakpoint"></a>Aby ustawić punkt przerwania

Można ustawić punkt przerwania w skrypcie tylko wtedy, gdy został on zapisany. Kliknij wiersz, w której chcesz ustawić punkt przerwania w wierszu, a następnie kliknij prawym przyciskiem myszy **Przełącz punkt przerwania**. Lub kliknij wiersz, w której chcesz ustawić punkt przerwania wiersza i naciśnij klawisz **F9** lub na **debugowania** menu, kliknij przycisk **Przełącz punkt przerwania**.

Poniższy skrypt znajduje się przykład jak można ustawić zmiennej punkt przerwania w okienku konsoli, za pomocą [PSBreakpoint zestaw](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420) polecenia cmdlet.

```powershell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a>Lista wszystkich punktów przerwania

Wyświetla wszystkie punkty przerwania w bieżącej sesji programu Windows PowerShell.

Na **debugowania** menu, kliknij przycisk **listy punktów przerwania**. Poniższy skrypt znajduje się przykład jak możesz wyświetlić listę wszystkich punktów przerwania w okienku konsoli przy użyciu [Get PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) polecenia cmdlet.

```powershell
# This command lists all breakpoints in the current session.
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a>Usuń punkt przerwania

Usuwanie punktu przerwania go kasuje.

Jeśli uważasz, że możesz chcieć użyć go później, należy wziąć pod uwagę [Wyłącz punkt przerwania](#disable-a-breakpoint) go zamiast tego.
Kliknij prawym przyciskiem myszy wiersza, które chcesz usunąć punkt przerwania, a następnie kliknij przycisk **Przełącz punkt przerwania**.
Lub kliknij wiersz, w której chcesz usunąć punkt przerwania, a następnie na **debugowania** menu, kliknij przycisk **Przełącz punkt przerwania**.
Poniższy skrypt jest przykładem sposobu usuwania punktu przerwania o określonym identyfikatorze z poziomu okienka konsoli przy użyciu [PSBreakpoint Usuń](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) polecenia cmdlet.

```powershell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a>Usuń wszystkie punkty przerwania

Aby usunąć wszystkie punkty przerwania w bieżącej sesji, wobec **debugowania** menu, kliknij przycisk **Usuń wszystkie punkty przerwania**.

Poniższy skrypt jest przykładem usunąć wszystkie punkty przerwania w okienku konsoli, za pomocą [PSBreakpoint Usuń](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) polecenia cmdlet.

```powershell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <a name="disable-a-breakpoint"></a>Wyłącz punkt przerwania

Wyłączenie punktu przerwania nie spowoduje usunięcia go; wyłącza ona go, dopóki nie jest włączone.  Aby wyłączyć określony wiersz punktu przerwania, kliknij prawym przyciskiem myszy wiersz, w którym chcesz wyłączyć punkt przerwania, a następnie kliknij przycisk **Wyłącz punkt przerwania**. Lub kliknij wiersz, w którym chcesz wyłączyć punkt przerwania, i naciśnij klawisz **F9** lub na **debugowania** menu, kliknij przycisk **Wyłącz punkt przerwania**. Poniższy skrypt znajduje się przykład jak usunąć punkt przerwania o określonym identyfikatorze z poziomu okienka konsoli przy użyciu [PSBreakpoint Wyłącz](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) polecenia cmdlet.

```powershell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a>Wyłącz wszystkie punkty przerwania

Wyłączenie punktu przerwania nie spowoduje usunięcia go; wyłącza ona go, dopóki nie jest włączone.  Aby wyłączyć wszystkie punkty przerwania w bieżącej sesji, na **debugowania** menu, kliknij przycisk **Wyłącz wszystkie punkty przerwania**. Poniższy skrypt znajduje się przykład jak wyłączyć wszystkie punkty przerwania w okienku konsoli, za pomocą [PSBreakpoint Wyłącz](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) polecenia cmdlet.

```powershell
# This command disables all breakpoints in the current session.
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a>Włącz punkt przerwania

Aby włączyć określonego punktu przerwania, kliknij prawym przyciskiem myszy wiersz, w którym chcesz włączyć punkt przerwania, a następnie kliknij przycisk **Włącz punkt przerwania**. Lub kliknij wiersz, w którym chcesz włączyć punkt przerwania, a następnie naciśnij klawisz **F9** lub na **debugowania** menu, kliknij przycisk **Włącz punkt przerwania**. Poniższy skrypt znajduje się przykład jak włączyć określonych punktów przerwania w okienku konsoli, za pomocą [PSBreakpoint Włącz](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) polecenia cmdlet.

```powershell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a>Włącz wszystkie punkty przerwania

Aby włączyć wszystkie punkty przerwania w bieżącej sesji, wobec **debugowania** menu, kliknij przycisk **Włącz wszystkie punkty przerwania**. Poniższy skrypt znajduje się przykład jak włączyć wszystkie punkty przerwania z poziomu okienka konsoli przy użyciu [PSBreakpoint Włącz](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) polecenia cmdlet.

```powershell
# This command enables all breakpoints in the current session.
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <a name="how-to-manage-a-debugging-session"></a>Jak zarządzać sesji debugowania

Przed rozpoczęciem debugowania, należy ustawić co najmniej jednego punktu przerwania. Nie można ustawić punktu przerwania, chyba że zostanie zapisany skrypt, który chcesz debugować. Kierunki w sposób ustawić punkt przerwania, można zobaczyć [jak zarządzanie punktami przerwania](#how-to-manage-breakpoints) lub [PSBreakpoint zestaw](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint). Po rozpoczęciu debugowania, nie można edytować skryptu, dopóki nie zatrzymasz debugowanie. Skrypt, który ma co najmniej jeden punkty przerwania ustawione są automatycznie zapisywane przed uruchomieniem.

### <a name="to-start-debugging"></a>Aby rozpocząć debugowanie

Naciśnij klawisz **F5** lub na pasku narzędzi kliknij **uruchamianie skryptu** ikony, lub na **debugowania** kliknij menu **Uruchom/Kontynuuj**. Skrypt jest uruchamiany, aż do napotkania pierwszego punktu przerwania. On wstrzymuje działanie ma i podświetla wiersz, w którym wstrzymana.

### <a name="to-continue-debugging"></a>Aby kontynuować debugowanie

Naciśnij klawisz **F5** lub na pasku narzędzi kliknij **uruchamianie skryptu** ikony, lub na **debugowania** menu, kliknij przycisk **Uruchom/Kontynuuj** lub wpisz w okienku konsoli **C** , a następnie naciśnij klawisz **ENTER**. Powoduje to skrypt, aby kontynuować uruchamianie następnego punktu przerwania lub na końcu skryptu, jeśli nie zostaną napotkane nie dodatkowe punkty przerwania.

### <a name="to-view-the-call-stack"></a>Aby wyświetlić stos wywołań

Stos wywołań jest wyświetlana bieżąca lokalizacja uruchamiania skryptu. Jeśli skrypt jest uruchamiany w funkcji, która została wywołana przez inną funkcję, następnie które odpowiada na wyświetlaczu dodatkowe wiersze w danych wyjściowych. Wiersz najniższy Wyświetla oryginalny skrypt i wiersz w nim, w którym funkcja została wywołana. Następne wiersz w górę pokazuje tę funkcję i wiersza w nim, w którym inna funkcja może być została wywołana.  Wiersz najważniejsze pokazuje bieżący kontekst bieżącego wiersza, w którym ustawiono punkt przerwania.

Podczas wstrzymania, aby wyświetlić bieżący stos wywołań, naciśnij klawisz **CTRL + SHIFT + D** lub na **debugowania** menu, kliknij przycisk **wyświetlanie stosu wywołań** lub wpisz w okienku konsoli **K**  , a następnie naciśnij klawisz **ENTER**.

### <a name="to-stop-debugging"></a>Aby zatrzymać debugowanie

Naciśnij klawisz **SHIFT-F5** lub na **debugowania** menu, kliknij przycisk **Zatrzymaj debuger**, lub wpisz w okienku konsoli **Q** , a następnie naciśnij klawisz  **Wprowadź**.

## <a name="how-to-step-over-step-into-and-step-out-while-debugging"></a>Przekrocz nad, wejdź do i wyjdź podczas debugowania

Przechodzenie krok po kroku jest proces uruchamiania jednej instrukcji w danym momencie. Można zatrzymać na wiersz kodu i sprawdzić wartości zmiennych i stanu systemu. W poniższej tabeli opisano typowe zadania debugowania, takich jak pominięcie, przechodzenie do i przechodzenie krok po kroku,.

| Debugowanie zadań | Opis | Jak wykonać je w środowisku PowerShell ISE |
| --- | --- | --- |
| **Wkrocz** | Wykonuje instrukcję bieżący, a następnie zatrzymuje się na następnej instrukcji. W przypadku bieżącej instrukcji funkcji lub wywołanie skryptu, a następnie debuger nie wchodzi do tej funkcji lub skryptu, w przeciwnym razie zatrzymuje się w następnej instrukcji. | Naciśnij klawisz **F11** lub na **debugowania** menu, kliknij przycisk **Step Into**, lub wpisz w okienku konsoli **S** i naciśnij klawisz **ENTER**. |
| **Przekrocz nad** | Wykonuje instrukcję bieżący, a następnie zatrzymuje się na następnej instrukcji. Jeśli bieżąca instrukcja funkcji lub wywołanie skryptu, a następnie debuger wykonuje całą funkcji lub skryptu, a następnie zatrzymuje się na następną instrukcję po wywołaniu funkcji. | Naciśnij klawisz **F10** lub na **debugowania** menu, kliknij przycisk **Step Over**, lub wpisz w okienku konsoli **V** i naciśnij klawisz **ENTER**. |
| **Wyjdź** | Kroki poza bieżącą funkcję i jeden poziom, jeśli funkcja jest zagnieżdżony w górę. Jeśli w głównym, skrypt zostanie wykonany na końcu lub do następnego punktu przerwania. Pominięto instrukcje są wykonywane, ale nie jest zmieniana za pośrednictwem. | Naciśnij klawisz **SHIFT + F11**, lub na **debugowania** menu, kliknij przycisk **Step Out**, lub wpisz w okienku konsoli **O** i naciśnij klawisz **ENTER**. |
| **Kontynuuj** | Kontynuuje wykonywanie na końcu lub do następnego punktu przerwania. Pominięte funkcje i wywołania są wykonywane, ale nie jest zmieniana za pośrednictwem. | Naciśnij klawisz **F5** lub na **debugowania** menu, kliknij przycisk **Uruchom/Kontynuuj**, lub wpisz w okienku konsoli **C** i naciśnij klawisz **ENTER**. |

## <a name="how-to-display-the-values-of-variables-while-debugging"></a>Wyświetlanie wartości zmiennych podczas debugowania

Jak przejść przez kod, możesz wyświetlić bieżące wartości zmiennych w skrypcie.

### <a name="to-display-the-values-of-standard-variables"></a>Aby wyświetlić wartości zmiennych standardowa

Użyj jednej z następujących metod:

- W okienku skryptów umieść kursor zmiennej, aby wyświetlić jego wartość jako etykietka narzędzia.

- W okienku konsoli, wpisz nazwę zmiennej i naciśnij klawisz **ENTER**.

Wszystkie okienka w środowisku ISE zawsze znajdują się w tym samym zakresie. Dlatego podczas debugowania skryptu, poleceń, które możesz wpisać w okienku konsoli uruchamiać w zakresie skryptu. Dzięki temu można używać okienka konsoli, aby znaleźć wartości zmiennych i wywoływać funkcje, które są zdefiniowane tylko w skrypcie.

### <a name="to-display-the-values-of-automatic-variables"></a>Aby wyświetlić wartości zmiennych automatycznych

Powyższa metoda służy do wyświetlania wartości prawie wszystkich zmiennych podczas debugowania skryptu. Jednak te metody nie działają w przypadku następujących zmiennych automatycznych.

- $_

- $Input

- $MyInvocation

- $PSBoundParameters

- $Args

Jeśli zostanie podjęta próba wyświetlenia wartości tych zmiennych, otrzymasz wartość tej zmiennej, dla w potoku usługi wewnętrzne debugera, nie wartość zmiennej w skrypcie. Można obejść to kilka zmiennych ($_, $Input, $MyInvocation, $PSBoundParameters i $Args) przy użyciu następującej metody:

1. W skrypcie należy przypisać wartość zmiennej automatyczne do nowej zmiennej.

2. Wyświetl wartość nowej zmiennej, ustawiając kursor nad nową zmienną, w okienku skryptów lub wpisując nową zmienną w okienku konsoli.

Na przykład aby wyświetlić wartość zmiennej $MyInvocation w skrypcie, przypisać wartość do nowej zmiennej, takich jak $scriptname i następnie umieść kursor nad lub typ zmiennej $scriptname, aby wyświetlić jego wartość.

```powershell
# In C:\ps-test\MyScript.ps1
$scriptname = $MyInvocation.MyCommand.Path
```

```output
# In the Console Pane:
PS> .\MyScript.ps1
PS> $scriptname
C:\ps-test\MyScript.ps1
```

## <a name="see-also"></a>Zobacz też

- [Eksplorowanie środowiska Windows PowerShell ISE](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)