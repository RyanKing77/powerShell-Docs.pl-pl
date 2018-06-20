---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Jak debugować skrypty w środowisku Windows PowerShell ISE
ms.openlocfilehash: b7af2de83a3f796a2057514e36ad8b74367e8ce2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953409"
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a>Jak debugować skrypty w środowisku Windows PowerShell ISE

W tym artykule opisano sposób debugowania skryptów na komputerze lokalnym przy użyciu funkcji debugowania visual Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="how-to-manage-breakpoints"></a>Jak zarządzać punkty przerwania

Punkt przerwania jest wyznaczony miejscu w skrypcie miejsce chcesz operacji wstrzymania, dzięki czemu można sprawdzić bieżącego stanu zmienne i środowisko, w którym uruchomiony jest skrypt. Gdy skrypt jest wstrzymane przez punkt przerwania, możesz uruchamiać polecenia w okienku konsoli, aby sprawdzić stan skryptu.  Możesz output zmienne lub innych poleceń. Nawet można modyfikować wartości zmiennych, które są widoczne w kontekście obecnie uruchamianie skryptu. Po zostały zbadane, mają być wyświetlane, możesz wznowić działanie skryptu.

Można ustawić trzy typy punktów przerwania w środowisku debugowania programu Windows PowerShell:

1. **Wiersz punktu przerwania**. Skrypt wstrzymuje po osiągnięciu wyznaczonych wiersza podczas działania skryptu

2. **Zmienna punktu przerwania.** Skrypt wstrzymuje przy każdej zmianie wyznaczonych zmienna.

3. **Polecenie punktu przerwania.** Skrypt wstrzymuje zawsze, gdy wyznaczonych polecenia ma być uruchomiona podczas działania skryptu. Może zawierać parametrów, aby dokładniej przefiltrować punktu przerwania działania, które mają. Polecenie można także funkcji, do której został utworzony.

Te w środowisku Windows PowerShell ISE debugowania za pomocą menu lub skróty klawiaturowe można ustawić tylko punkty przerwania wiersza. Można ustawić dwa typy punktów przerwania, ale są skonfigurowane w okienku konsoli przy użyciu [PSBreakpoint zestaw](https://technet.microsoft.com/library/88d2d9ad-17dc-44ae-99aa-f841125b9dc8) polecenia cmdlet. W tej sekcji opisano, jak można wykonać zadania debugowania w środowisku Windows PowerShell ISE przy użyciu menu, jeśli jest on dostępny i wykonywać szerszej grupy poleceń w okienku konsoli przy użyciu skryptów.

### <a name="to-set-a-breakpoint"></a>Aby ustawić punkt przerwania

Można ustawić punktu przerwania w skrypcie dopiero po jego zapisaniu. Kliknij wiersz, w którym chcesz ustawić punkt przerwania wiersza, a następnie kliknij prawym przyciskiem myszy **Przełącz punkt przerwania**. Lub kliknij wiersz, w którym chcesz ustawić punkt przerwania wiersza i naciśnij klawisz **F9** lub na **debugowania** menu, kliknij przycisk **Przełącz punkt przerwania**.

Poniższy skrypt to przykład sposobu można ustawić punktu przerwania zmiennej w okienku konsoli przy użyciu [PSBreakpoint zestaw](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420) polecenia cmdlet.

```powershell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a>Wyświetl listę wszystkich punktów przerwania

Wyświetla wszystkie punkty przerwania w bieżącej sesji programu Windows PowerShell.

Na **debugowania** menu, kliknij przycisk **listy punktów przerwania**. Poniższy skrypt to przykład sposobu można wyświetlić listę wszystkich punktów przerwania w okienku konsoli przy użyciu [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) polecenia cmdlet.

```powershell
# This command lists all breakpoints in the current session.
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a>Usuwanie punktu przerwania

Usuwanie punktu przerwania usunięcia go.

Jeśli uważasz, że możesz chcieć użyć go później, należy wziąć pod uwagę [wyłączenie punktu przerwania](#disable-a-breakpoint) go zamiast tego.
Kliknij wiersz, w której chcesz usunąć punkt przerwania, a następnie kliknij prawym przyciskiem myszy **Przełącz punkt przerwania**.
Lub kliknij wiersz, w której chcesz usunąć punkt przerwania, a następnie na **debugowania** menu, kliknij przycisk **Przełącz punkt przerwania**.
Poniższy skrypt jest przykładem usunąć punkt przerwania o określonym identyfikatorze w okienku konsoli za pomocą [PSBreakpoint Usuń](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) polecenia cmdlet.

```powershell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a>Usuń wszystkie punkty przerwania

Aby usunąć wszystkie punkty przerwania zdefiniowana w bieżącej sesji, na **debugowania** menu, kliknij przycisk **Usuń wszystkie punkty przerwania**.

Poniższy skrypt jest przykładem usunąć wszystkie punkty przerwania w okienku konsoli za pomocą [PSBreakpoint Usuń](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) polecenia cmdlet.

```powershell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <a name="disable-a-breakpoint"></a>Wyłączenie punktu przerwania

Wyłączenie punktu przerwania nie powoduje jego usunięcia; wyłącza ona go dopóki nie jest włączona.  Aby wyłączyć określony wiersz punkt przerwania, kliknij prawym przyciskiem myszy wiersz, w którym chcesz wyłączyć punkt przerwania, a następnie kliknij przycisk **wyłączyć punkt przerwania**. Lub kliknij wiersz, w którym chcesz wyłączyć punkt przerwania, i naciśnij klawisz **F9** lub na **debugowania** menu, kliknij przycisk **wyłączyć punkt przerwania**. Poniższy skrypt to przykład jak usunąć punkt przerwania o określonym identyfikatorze w okienku konsoli przy użyciu [PSBreakpoint Wyłącz](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) polecenia cmdlet.

```powershell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a>Wyłącz wszystkie punkty przerwania

Wyłączenie punktu przerwania nie powoduje jego usunięcia; wyłącza ona go dopóki nie jest włączona.  Aby wyłączyć wszystkie punkty przerwania w bieżącej sesji, na **debugowania** menu, kliknij przycisk **Wyłącz wszystkie punkty przerwania**. Poniższy skrypt to przykład jak wyłączyć wszystkie punkty przerwania w okienku konsoli przy użyciu [PSBreakpoint Wyłącz](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) polecenia cmdlet.

```powershell
# This command disables all breakpoints in the current session.
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a>Włącz punkt przerwania

Aby włączyć określonego punktu przerwania, kliknij prawym przyciskiem myszy wiersz, w której chcesz włączyć punkt przerwania, a następnie kliknij przycisk **włączyć punkt przerwania**. Lub kliknij wiersz, w której chcesz włączyć punkt przerwania, a następnie naciśnij klawisz **F9** lub na **debugowania** menu, kliknij przycisk **włączyć punkt przerwania**. Poniższy skrypt to przykład sposobu określonych punktów przerwania w okienku konsoli można włączyć za pomocą [PSBreakpoint Włącz](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) polecenia cmdlet.

```powershell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a>Włącz wszystkie punkty przerwania

Aby włączyć wszystkie punkty przerwania zdefiniowana w bieżącej sesji, na **debugowania** menu, kliknij przycisk **Włącz wszystkie punkty przerwania**. Poniższy skrypt to przykład sposobu wszystkie punkty przerwania w okienku konsoli można włączyć za pomocą [PSBreakpoint Włącz](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) polecenia cmdlet.

```powershell
# This command enables all breakpoints in the current session.
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <a name="how-to-manage-a-debugging-session"></a>Jak zarządzać sesji debugowania

Przed rozpoczęciem debugowania, należy ustawić co najmniej jednego punktu przerwania. Nie można ustawić punktu przerwania, chyba że zostanie zapisany skrypt, który chcesz debugować. Dla kierunków na jak ustawić punkt przerwania, zobacz [jak zarządzać punktów przerwania](#how-to-manage-breakpoints) lub [PSBreakpoint zestawu](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint). Po rozpoczęciu debugowania, nie można edytować skryptu, aż do zatrzymania debugowania. Skrypt, który zawiera jeden lub więcej punktów przerwania ustawionych są automatycznie zapisywane przed uruchomieniem.

### <a name="to-start-debugging"></a>Aby rozpocząć debugowanie

Naciśnij klawisz **F5** lub na pasku narzędzi kliknij **Uruchom skrypt** ikony, lub na **debugowania** kliknij menu **Uruchom/Kontynuuj**. Skrypt jest uruchamiany, aż do napotkania pierwszego punktu przerwania. Wstrzymuje działanie istnieje, a wyróżnia wiersza, w którym wstrzymana.

### <a name="to-continue-debugging"></a>Aby kontynuować debugowanie

Naciśnij klawisz **F5** lub na pasku narzędzi kliknij **Uruchom skrypt** ikony, lub na **debugowania** menu, kliknij przycisk **Uruchom/Kontynuuj** lub wpisz w okienku konsoli **C** , a następnie naciśnij klawisz **ENTER**. Powoduje to, że skrypt do kontynuowania pracy do następnego punktu przerwania lub na końcu skryptu, jeśli nie zostaną napotkane nie dodatkowe punkty przerwania.

### <a name="to-view-the-call-stack"></a>Aby wyświetlić stosu wywołań

Stos wywołań Wyświetla bieżący przebieg lokalizacji w skrypcie. Jeśli skrypt jest uruchamiany w funkcji, która została wywołana przez inną funkcję, następnie reprezentowaną wyświetlania przez dodatkowe wiersze w danych wyjściowych. Wiersz najniższy Wyświetla oryginalny skrypt i wiersza w nim, w którym została wywołana funkcja. Dalej wiersz wskazuje tej funkcji i wiersza w nim, w którym innej funkcji może zostać wywołany.  Wiersz najwyżej pokazuje bieżący kontekst bieżącego wiersza, w którym ustawiono punktu przerwania.

Podczas wstrzymania, aby wyświetlić bieżący stos wywołań, naciśnij klawisz **CTRL + SHIFT + D** lub na **debugowania** menu, kliknij przycisk **stos wywołań wyświetlania** lub, w okienku konsoli wpisz **K**  , a następnie naciśnij klawisz **ENTER**.

### <a name="to-stop-debugging"></a>Aby zatrzymać debugowanie

Naciśnij klawisz **SHIFT-F5** lub na **debugowania** menu, kliknij przycisk **zatrzymać debuger**, lub wpisz w okienku konsoli **Q** , a następnie naciśnij klawisz  **Wprowadź**.

## <a name="how-to-step-over-step-into-and-step-out-while-debugging"></a>Przekrocz nad, Wkrocz i wyjdź podczas debugowania

Wykonywanie krok po kroku jest procesem działających w czasie jednej instrukcji. Można zatrzymać na wiersz kodu i sprawdzić wartości zmiennych i stanu systemu. W poniższej tabeli opisano typowe debugowania zadań, takich jak pominięcie Wkraczanie do i wykonywanie krok po kroku,.

| Zadanie debugowania | Opis | Jak wykonać je w środowisku PowerShell ISE |
| --- | --- | --- |
| **Wkrocz** | Wykonuje bieżącej instrukcji, a następnie zatrzymuje w następnej instrukcji. W przypadku bieżącej instrukcji funkcji lub wywołań skryptów, a następnie kroków debugera w tej funkcji lub skrypt, w przeciwnym razie zatrzymuje się w następnej instrukcji. | Naciśnij klawisz **F11** lub na **debugowania** menu, kliknij przycisk **Step Into**, lub wpisz w okienku konsoli **S** i naciśnij klawisz **ENTER**. |
| **Przekrocz** | Wykonuje bieżącej instrukcji, a następnie zatrzymuje w następnej instrukcji. W przypadku bieżącej instrukcji funkcji lub wywołań skryptów, a następnie debuger wykonuje całej funkcji lub skrypcie, i zatrzymuje się w następnej instrukcji po wywołaniu funkcji. | Naciśnij klawisz **F10** lub na **debugowania** menu, kliknij przycisk **Step Over**, lub wpisz w okienku konsoli **V** i naciśnij klawisz **ENTER**. |
| **Wyjdź** | Kroki poza bieżącą funkcję i uogólnianie po jednym poziomie, jeśli funkcja jest zagnieżdżony. Jeśli w głównym, skrypt zostanie wykonany na końcu lub do następnego punktu przerwania. Pominięto instrukcje są wykonywane, ale nie przeprowadził przez. | Naciśnij klawisz **SHIFT + F11**, lub na **debugowania** menu, kliknij przycisk **Wyjdź**, lub wpisz w okienku konsoli **O** i naciśnij klawisz **ENTER**. |
| **Kontynuuj** | Kontynuuje wykonywanie na końcu lub do następnego punktu przerwania. Pominięto funkcje i wywołania są wykonywane, ale nie przeprowadził przez. | Naciśnij klawisz **F5** lub na **debugowania** menu, kliknij przycisk **Uruchom/Kontynuuj**, lub wpisz w okienku konsoli **C** i naciśnij klawisz **ENTER**. |

## <a name="how-to-display-the-values-of-variables-while-debugging"></a>Wyświetlanie wartości zmiennych podczas debugowania

Podczas wykonywania kroków za pomocą kodu można wyświetlić bieżące wartości zmiennych w skrypcie.

### <a name="to-display-the-values-of-standard-variables"></a>Aby wyświetlić wartości zmiennych standardowe

Użyj jednej z następujących metod:

- W okienku skryptów umieść kursor nad zmienną do wyświetlania wartości jako etykietka narzędzia.

- W okienku konsoli, wpisz nazwę zmiennej i naciśnij klawisz **ENTER**.

Wszystkie okienka w ISE zawsze znajdują się w tym samym zakresie. W związku z tym podczas debugowania skryptu, z poleceniami, które można wpisać w okienku konsoli Uruchom skrypt zakresu. Dzięki temu można używać w okienku konsoli można znaleźć wartości zmiennych i wywołanie funkcji, które są definiowane tylko w skrypcie.

### <a name="to-display-the-values-of-automatic-variables"></a>Aby wyświetlić wartości zmiennych automatycznych

Powyższa metoda służy do wyświetlania wartości zmiennych prawie wszystkie podczas debugowania skryptu. Jednak te metody nie działają następujące zmienne automatyczne.

- $_

- $Input

- $MyInvocation

- $PSBoundParameters

- $Args

Próba wyświetlenia wartości tych zmiennych można uzyskać wartość tej zmiennej w potoku wewnętrzny debuger używa, nie wartość zmiennej w skrypcie. Można obejść, to w przypadku kilku zmiennych ($_, $Input $MyInvocation, $PSBoundParameters i $Args) przy użyciu następujących metod:

1. W skrypcie należy przypisać wartość zmiennej automatycznego do nowej zmiennej.

2. Wyświetl wartość z nową zmienną, ustawiając kursor nad nowej zmiennej w okienku skryptów lub wpisując nowej zmiennej w okienku konsoli.

Na przykład aby wyświetlić wartość zmiennej $MyInvocation w skrypcie, przypisuje wartość do nowej zmiennej, takich jak $scriptname i następnie umieść kursor nad lub typu zmienną $scriptname do wyświetlania wartości.

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