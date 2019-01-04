---
title: Jak replikować obsługę środowiska ISE w programie Visual Studio Code
description: Jak replikować obsługę środowiska ISE w programie Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: 9df29dfc637191b62ca591893c251c1e02d4eb4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54012487"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>Jak replikować obsługę środowiska ISE w programie Visual Studio Code

Rozszerzenie programu PowerShell dla programu VSCode nie Szukaj równoważności funkcji pełną przy użyciu programu PowerShell ISE, są funkcje aby usprawnić środowisko programu VSCode stosować bardziej naturalne użytkownikom środowiska ISE.

Ten dokument usiłuje ustawienia listy, które można skonfigurować w VSCode, aby ułatwić bardziej powszechnie znane w porównaniu do środowiska ISE.

## <a name="key-bindings"></a>Powiązania klawiszy

| Funkcja                              | Powiązanie środowiska ISE                  | Powiązanie programu VSCode                              |
| ----------------                      | -----------                  | --------------                              |
| Przerwij i przerwać debugera          | <kbd>CTRL</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
| Wykonaj bieżący wiersz/wyróżniony tekst | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
| Dostępne fragmenty kodu list               | <kbd>CTRL</kbd>+<kbd>"j"</kbd> | <kbd>CTRL</kbd>+<kbd>Alt</kbd>+<kbd>"j"</kbd> |

### <a name="custom-key-bindings"></a>Powiązania niestandardowe klucza

Możesz [skonfigurować własne powiązania klawiszy](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) w VSCode także.

## <a name="tab-completion"></a>Uzupełnianie po naciśnięciu tabulatora

Aby włączyć bardziej przypominające ISE uzupełniania po naciśnięciu tabulatora, należy dodać ustawienie:

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> To ustawienie zostało dodane bezpośrednio do programu VSCode (a nie w rozszerzeniu). Jego zachowanie jest określana przez VSCode bezpośrednio i nie można zmienić przez rozszerzenie.

## <a name="no-focus-on-console-when-executing"></a>Nie szczególnym uwzględnieniem konsoli podczas wykonywania

Aby utrzymać uwagę w edytorze podczas wykonywania za pomocą <kbd>F8</kbd>:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

Wartość domyślna to `true` potrzeby ułatwień dostępu.

## <a name="dont-start-integrated-console-on-startup"></a>Nie uruchamiaj zintegrowana Konsola przy uruchamianiu

Aby zatrzymać zintegrowana Konsola podczas uruchamiania, należy ustawić:

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> Tło procesu programu PowerShell nadal rozpocznie się od czasu, który oferuje funkcję IntelliSense, analizy skryptu, nawigacji symboli, itp. Jednak konsoli nie był już wyświetlany.

## <a name="assume-files-are-powershell-by-default"></a>Przyjęto założenie, że pliki są PowerShell domyślnie

Aby wprowadzić nowy/bez nazwy plików, zarejestruj się jako programu PowerShell, domyślnie:

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a>Schemat kolorów

Są dostępne dla programu VSCode się Edytor wyglądała znacznie bardziej jak środowiska ISE liczby motywów ISE.

W [Paleta poleceń] typu `theme` można pobrać `Preferences: Color Theme` i naciśnij klawisz <kbd>Enter</kbd>.
Z listy rozwijanej wybierz `PowerShell ISE`.

Ten motyw można ustawić w ustawieniach za pomocą:

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a>Eksplorator polecenia programu PowerShell

Dzięki rozłożeniu pracy [ @corbob ](https://github.com/corbob), rozszerzenie programu PowerShell ma początku własne polecenia Eksploratora.

W [Paleta poleceń], wprowadź `PowerShell Command Explorer` i naciśnij klawisz <kbd>Enter</kbd>.

## <a name="open-in-the-ise"></a>Otwórz w środowisku ISE

Jeśli znajdą się chce otworzyć plik w środowisku ISE mimo to, możesz użyć <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.

## <a name="other-resources"></a>Inne zasoby

- ma 4sysops [doskonałe artykułu](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) na temat konfigurowania programu VSCode bardziej, takich jak środowiska ISE.
- Mike F Robbins ma [doskonałe wpis](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) na temat konfigurowania programu VSCode.
- Dowiedz się, programu PowerShell ma [doskonałą zapisu w górę](https://www.learnpwsh.com/setup-vs-code-for-powershell/) na temat pobierania programu VSCode konfiguracji dla programu PowerShell.

## <a name="more-settings"></a>Więcej ustawień

Jeśli znasz więcej sposobów tworzenia możesz lepiej zapoznać się dla użytkowników w środowisku ISE programu VSCode przyczyniają się do tego dokumentu. Jeśli jest Konfiguracja zgodności, czego szukasz, ale nie można odnaleźć dowolny sposób, aby ją włączyć, [Otwórz problem](https://github.com/PowerShell/vscode-powershell/issues/new/choose) i Pytaj do woli!

Zawsze nam miło do akceptowania żądań ściągnięcia oraz kod wniesiony przez także!

## <a name="vscode-tips"></a>Wskazówki dotyczące programu VSCode

### <a name="command-palette"></a>Paleta poleceń

<kbd>F1</kbd> lub <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd> Przenieś</kbd>+<kbd>P</kbd> w systemie macOS)

Wygodny sposób wykonywania poleceń w VSCode.
Aby uzyskać więcej informacji, zobacz [VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).

[Paleta poleceń]: #command-palette
