---
title: Używanie programu Visual Studio Code do tworzenia aplikacji programu PowerShell
description: Używanie programu Visual Studio Code do tworzenia aplikacji programu PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 0d796460511b273771eacb03d0df4d90e1e9c322
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854398"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>Używanie programu Visual Studio Code do tworzenia aplikacji programu PowerShell

Oprócz [PowerShell ISE][ise], programu PowerShell jest również dobrze jest obsługiwany w programie Visual Studio Code.
Ponadto środowiska ISE nie jest obsługiwana przy użyciu programu PowerShell Core, chociaż program Visual Studio Code jest przeznaczony dla programu PowerShell Core na wszystkich platformach (Windows, macOS i Linux)

Można użyć programu Visual Studio Code na Windows przy użyciu programu PowerShell w wersji 5 przy użyciu systemu Windows 10 lub dzięki zainstalowaniu [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) dla niskiego poziomu OSs Windows (Windows 8.1, itp.).

Przed jej rozpoczęciem, upewnij się, że program PowerShell znajduje się w Twoim systemie.
W przypadku nowoczesnych obciążeń w Windows, macOS i Linux zobacz:

- [Instalowanie programu PowerShell Core w systemie Linux][install-pscore-linux]
- [Instalowanie programu PowerShell Core w systemie macOS][install-pscore-macos]
- [Instalowanie programu PowerShell Core w Windows][install-pscore-windows]

W przypadku tradycyjnych obciążeń programu Windows PowerShell, zobacz [Instalowanie programu Windows PowerShell][install-winps].

## <a name="editing-with-visual-studio-code"></a>Edytowanie w programie Visual Studio Code

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[1. Instalowanie programu Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview)

- **Linux**: postępuj zgodnie z instrukcjami instalacji na [uruchomiony program VS Code w systemie Linux](https://code.visualstudio.com/docs/setup/linux) strony

- **System macOS**: postępuj zgodnie z instrukcjami instalacji na [uruchomiony program VS Code w systemie macOS](https://code.visualstudio.com/docs/setup/mac) strony

  > [!IMPORTANT]
  > W systemie macOS należy zainstalować protokół OpenSSL rozszerzenia programu PowerShell, do prawidłowego działania.
  > W tym celu najłatwiej zainstalował [Homebrew](https://brew.sh/) , a następnie uruchom `brew install openssl`.
  > Program VS Code można teraz pomyślnie załadować rozszerzenia programu PowerShell.

- **Windows**: postępuj zgodnie z instrukcjami instalacji na [uruchomiony program VS Code w Windows](https://code.visualstudio.com/docs/setup/windows) strony

### <a name="2-installing-powershell-extension"></a>2. Instalowanie rozszerzenia programu PowerShell

- Uruchomienie programu Visual Studio Code aplikacji przez:
  - **Windows**: wpisywanie `code` w sesji programu PowerShell
  - **Linux**: wpisywanie `code` w terminalu
  - **System macOS**: wpisywanie `code` w terminalu

- Uruchom **szybkiego otwierania** , naciskając klawisz **Ctrl + P** (**Cmd + P** na komputerze Mac).
- W szybkiego otwierania wpisz `ext install powershell` i kliknij przycisk **Enter**.
- **Rozszerzenia** zostanie otwarty widok na pasku bocznym. Zaznacz rozszerzenie programu PowerShell firmy Microsoft.
  Powinny zostać wyświetlone informacje, takie jak poniżej:

  ![VSCode](../../images/vscode.png)

- Kliknij przycisk **zainstalować** przycisku na rozszerzeniu programu PowerShell firmy Microsoft.
- Po zakończeniu instalacji zostanie wyświetlony **zainstalować** przechodzi przycisk **Załaduj ponownie**.
  Kliknij pozycję **Załaduj ponownie**.
- Visual Studio Code po Załaduj ponownie, wszystko jest gotowe do edycji.

Na przykład, aby utworzyć nowy plik, kliknij przycisk **Plik -> Nowy**.
Aby zapisać go, kliknij przycisk **Plik -> Zapisz** a następnie podaj nazwę pliku, teraz załóżmy, że `HelloWorld.ps1`.
Aby zamknąć plik, kliknij symbol "x" obok nazwy pliku.
Aby zakończyć działanie programu Visual Studio Code, **Plik -> Zakończ**.

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>Instalowanie rozszerzenia programu PowerShell w systemach z ograniczeniami

Niektóre systemy są konfigurowane w sposób, który wymaga wszystkie podpisy kod do kontroli, a zatem Edytor programu PowerShell usługi ręcznie zatwierdzić do uruchomienia w systemie.
Aktualizacji zasad grupy, który zmienia zasady wykonywania jest prawdopodobną przyczyną, jeśli zainstalowano rozszerzenie programu PowerShell, ale zbliżają się błąd, taki jak:

```
Language server startup failed.
```

Aby ręcznie zatwierdzić usług Edytor programu PowerShell, a tym samym rozszerzenie programu PowerShell dla programu VSCode Otwórz program PowerShell, wiersz polecenia:

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

Zostanie wyświetlony monit z "Czy chcesz uruchamiać oprogramowania z tego wydawcy niezaufanych?"
Typ `R` do uruchomienia pliku. Następnie otwórz w programie Visual Studio Code i sprawdź, czy rozszerzenia programu PowerShell działa prawidłowo. Jeśli nadal masz problemy, wprowadzenie, Daj nam znać na [GitHub](https://github.com/PowerShell/vscode-powershell/issues).

#### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a>Wybieranie wersji programu PowerShell do korzystania z rozszerzeniem

Za pomocą programu PowerShell Core instalowanie side-by-side przy użyciu programu Windows PowerShell jest teraz możliwe do określonej wersji programu PowerShell z rozszerzeniem programu PowerShell. Należy użyć następującego poniższe kroki, aby wybrać wersję:

1. Otwórz paletę poleceń (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> na Windows i Linux, <kbd>Cmd</kbd> + <kbd>Shift</kbd>+<kbd>P</kbd> w systemie macOS).
1. Wyszukaj "Sesja".
1. Kliknij pozycję "programu PowerShell: Pokaż Menu sesji".
1. Wybierz wersję programu PowerShell, którego chcesz użyć z listy — na przykład programu PowerShell Core"".

>[!IMPORTANT]
> Ta funkcja sprawdza kilka znanych ścieżek w różnych systemach operacyjnych, aby odnaleźć lokalizacji instalacji programu PowerShell. Po zainstalowaniu programu PowerShell — typowej lokalizacji go może nie być wyświetlana początkowo w Menu sesji. Możesz rozszerzyć menu sesji przez [Dodawanie własnych niestandardowych ścieżek](#adding-your-own-powershell-paths-to-the-session-menu) zgodnie z poniższym opisem.

>[!NOTE]
> Istnieje inny sposób, aby przejść do menu sesji. Po otwarciu w edytorze pliku programu PowerShell zostanie wyświetlony numer wersji zielony w prawym dolnym rogu. Klikając ten numer wersji zostanie wyświetlone menu sesji.

##### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a>Dodawanie własnego ścieżki programu PowerShell do menu sesji

Do menu sesji za pomocą ustawienia programu VS Code, możesz dodać inne ścieżki pliku wykonywalnego programu PowerShell.

Dodaj element do listy `powershell.powerShellAdditionalExePaths` lub utworzyć listę, jeśli nie istnieje w Twojej `settings.json`:

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],
    
    // other settings...
}
```

Każdy element musi mieć:

* `exePath`: Ścieżka do `pwsh` lub `powershell` pliku wykonywalnego.
* `versionName`: Tekst, który będzie wyświetlany w menu sesji.

Można ustawić domyślną wersję programu PowerShell do użycia przy użyciu `powershell.powerShellDefaultVersion` ustawienie przez ustawienie, to w tekście wyświetlane w menu sesji (zwane również `versionName` w ostatnim ustawieniu):

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],
    
    "powershell.powerShellDefaultVersion": "Downloaded PowerShell",
    
    // other settings...
}
```

Po ustawieniu to ustawienie, uruchom ponownie program Visual Studio Code, lub użyj "dla deweloperów: Ponowne załadowanie okna"akcji wiersza polecenia palety ponownie załadować bieżące okno vscode.

Po otwarciu menu sesji, zostanie wyświetlona swoje dodatkowe wersje programu PowerShell!

> [!NOTE]
> Jeśli tworzysz Środowisko PowerShell ze źródła, to doskonały sposób na poziomie lokalnych kompilacji programu PowerShell.

#### <a name="configuration-settings-for-visual-studio-code"></a>Ustawienia konfiguracji dla programu Visual Studio Code

Wykonując kroki opisane w poprzednim akapicie można dodać ustawień konfiguracji w `settings.json`.

Zalecamy następujące ustawienia konfiguracji dla programu Visual Studio Code:

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Jeśli nie chcesz, aby te ustawienia mają wpływ na wszystkie typy plików, programu VSCode umożliwia także konfiguracje między językami. Utwórz ustawienie określonego języka, umieszczając ustawienia `[<language-name>]` pola. Przykład:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Aby uzyskać więcej informacji o pliku kodowania w programie VS Code, zobacz [zrozumienie kodowanie pliku](understanding-file-encoding.md).

## <a name="debugging-with-visual-studio-code"></a>Debugowanie za pomocą programu Visual Studio Code

### <a name="no-workspace-debugging"></a>Obszar roboczy bez debugowania

Począwszy od wersji programu Visual Studio Code 1.9 można debugować skrypty programu PowerShell, bez konieczności otwierania folderu zawierającego skrypt programu PowerShell. Otwórz plik skryptu programu PowerShell przy użyciu **Plik -> Otwórz plik...** , ustaw punkt przerwania w wierszu (naciśnij klawisz F9), a następnie naciśnij klawisz F5, aby rozpocząć debugowanie. Powinien zostać wyświetlony w okienku Akcje debugowania są wyświetlane, co pozwala na przerwanie w debugerze, krok, wznowienie i zatrzymać debugowanie.

### <a name="workspace-debugging"></a>Debugowanie obszaru roboczego

Obszar roboczy profilowanie odnosi się do debugowania w kontekście folder, który został otwarty w programie Visual Studio Code przy użyciu **Otwórz Folder...**  z **pliku** menu.
Folder, który można otworzyć, jest zazwyczaj do folderu projektu programu PowerShell i/lub w katalogu głównym repozytorium Git.

Nawet w tym trybie można uruchomić debugowania aktualnie zaznaczonego skryptu programu PowerShell, po prostu naciskając klawisz F5.
Jednakże debugowanie obszaru roboczego umożliwia definiowanie wielu konfiguracji debugowania innych niż po prostu debugowania aktualnie otwarty plik.
Na przykład można dodać konfiguracji do:

- Uruchom testy usług Pester w debugerze
- Uruchom określony plik z argumentami w debugerze
- Uruchomienie interaktywnej sesji w debugerze
- Dołącz debuger do procesu hosta programu PowerShell

Wykonaj następujące kroki, aby utworzyć plik konfiguracji debugowania:

  1. Otwórz **debugowania** widoku, naciskając klawisz **Ctrl + Shift + D** (**Cmd + Shift + D** na komputerze Mac).
  2. Naciśnij klawisz **Konfiguruj** ikonę koła zębatego w pasku narzędzi.
  3. Visual Studio Code wyświetli monit o **wybierz środowisko**. Wybierz **PowerShell**.

  Gdy to zrobisz, Visual Studio Code tworzy katalog i plik ".vscode\launch.json" w katalogu głównym folderu obszaru roboczego.
  Jest to, gdzie są przechowywane z konfiguracji debugowania. Jeśli pliki znajdują się w repozytorium Git, zazwyczaj chcesz zatwierdzić pliku launch.json.
  Zawartość pliku launch.json są:

  ```json
  {
    "version": "0.2.0",
    "configurations": [
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Launch (current file)",
            "script": "${file}",
            "args": [],
            "cwd": "${file}"
        },
        {
            "type": "PowerShell",
            "request": "attach",
            "name": "PowerShell Attach to Host Process",
            "processId": "${command.PickPSHostProcess}",
            "runspaceId": 1
        },
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Interactive Session",
            "cwd": "${workspaceRoot}"
        }
    ]
  }
  ```

  Reprezentuje typowe scenariusze debugowania.
  Jednak po otwarciu tego pliku w edytorze można zobaczyć **Dodawanie konfiguracji...**  przycisku.
  Można nacisnąć ten przycisk, aby dodać większą liczbę konfiguracji debugowania programu PowerShell. Jedna konfiguracja przydatna, aby dodać jest **programu PowerShell: Uruchom skrypt**.
  W przypadku tej konfiguracji można określić specjalny plik z argumentów opcjonalnych, które powinien zostać uruchomiony po każdym naciśnięciu klawisza F5 niezależnie od tego, plik, który jest aktualnie aktywne w edytorze.

  Gdy zostanie nawiązane z konfiguracji debugowania, możesz wybrać konfigurację, która ma być używany podczas sesji debugowania, wybierając jedną z listy rozwijanej w konfiguracji debugowania **debugowania** narzędzi widoku.

Istnieje kilka blogi, które mogą być przydatne ułatwią Ci rozpoczęcie pracy przy użyciu rozszerzenia programu PowerShell dla programu Visual Studio Code:

- [Rozszerzenie programu PowerShell][ps-extension]
- [Twórz i Debuguj skrypty programu PowerShell w programie Visual Studio Code][debug]
- [Wskazówki dotyczące kodu programu Visual Studio do debugowania][vscode-guide]
- [Debugowanie programu PowerShell w programie Visual Studio Code][ps-vscode]
- [Wprowadzenie do rozwoju środowiska PowerShell w programie Visual Studio Code][getting-started]
- [Visual Studio Code edytowanie funkcje opracowywania programu PowerShell — część 1][editing-part1]
- [Visual Studio Code edytowanie funkcje opracowywania programu PowerShell — część 2][editing-part2]
- [Debugowanie skryptu programu PowerShell w programie Visual Studio Code — część 1][debugging-part1]
- [Debugowanie skryptu programu PowerShell w programie Visual Studio Code — część 2][debugging-part2]

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a>Rozszerzenie programu PowerShell dla programu Visual Studio Code

Kod źródłowy rozszerzenia programu PowerShell można znaleźć na [GitHub](https://github.com/PowerShell/vscode-powershell).
