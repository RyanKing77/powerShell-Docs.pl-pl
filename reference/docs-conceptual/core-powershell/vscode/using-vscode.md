# <a name="using-visual-studio-code-for-powershell-development"></a>Przy użyciu kodu programu Visual Studio do tworzenia środowiska PowerShell

Oprócz [PowerShell ISE][ise], programu PowerShell jest również powszechnie obsługiwanych w programie Visual Studio Code.
Ponadto ISE nie jest obsługiwane podstawowych programu PowerShell, podczas Visual Studio Code jest obsługiwana dla środowiska PowerShell rdzeni na wszystkich platformach (z systemem Windows, system macOS i Linux)

Możesz użyć programu Visual Studio Code w systemie Windows przy użyciu programu PowerShell w wersji 5 przy użyciu systemu Windows 10 lub instalując [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) dla niskiego poziomu OSs systemu Windows (Windows 8.1, itp.).

Przed uruchomieniem go, upewnij się, że programu PowerShell znajduje się w tym systemie.
W przypadku nowoczesnych obciążeń w systemie Windows macOS i Linux, zobacz:

- [Instalowanie programu PowerShell Core na macOS i Linux][install-pscore-linux]
- [Instalowanie programu PowerShell Core w systemie Windows][install-pscore-windows]

Dla tradycyjnych obciążeń programu Windows PowerShell, zobacz [Instalowanie programu Windows PowerShell][install-winps].

## <a name="editing-with-visual-studio-code"></a>Edytowanie kodu programu Visual Studio

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[1. Instalowanie programu Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview)

- **Linux**: postępuj zgodnie z instrukcjami instalacji [uruchomić kod programu VS w systemie Linux](https://code.visualstudio.com/docs/setup/linux) strony

- **System macOS**: postępuj zgodnie z instrukcjami instalacji [uruchomić kod VS na macOS](https://code.visualstudio.com/docs/setup/mac) strony

> [!IMPORTANT]
> Na macOS należy zainstalować biblioteki OpenSSL rozszerzenia programu PowerShell, aby działać poprawnie.
> Najprostszym sposobem, w tym celu jest zainstalowanie [Homebrew](http://brew.sh/) , a następnie uruchom `brew install openssl`.
> Teraz będzie można pomyślnie załadować rozszerzenia programu PowerShell.

- **Windows**: postępuj zgodnie z instrukcjami instalacji [uruchomić kod programu VS w systemie Windows](https://code.visualstudio.com/docs/setup/windows) strony

### <a name="2-installing-powershell-extension"></a>2. Instalowanie rozszerzenia programu PowerShell

- Uruchom program Visual Studio Code aplikacji przez:
    - **Windows**: wpisywanie `code` w sesji programu PowerShell
    - **Linux**: wpisywanie `code` w terminalu
    - **System macOS**: wpisywanie `code` w terminalu

- Uruchom **szybkie Otwórz** naciskając **Ctrl + P** (**Cmd + P** dla komputerów Mac).
- W polu Szybkie Otwórz wpisz `ext install powershell` i trafień **Enter**.
- **Rozszerzenia** widok zostanie otwarty na pasku bocznym. Wybierz rozszerzenia programu PowerShell firmy Microsoft.
  Powinny pojawić się dane, takich jak poniżej:

  ![VSCode](../../images/vscode.png)

- Kliknij przycisk **zainstalować** przycisk rozszerzenia programu PowerShell firmy Microsoft.
- Po zakończeniu instalacji, zobaczysz **zainstalować** przycisk przechodzi w **Załaduj ponownie**.
  Polecenie **Załaduj ponownie**.
- Visual Studio Code po Załaduj ponownie, możesz przystąpić do edycji.

Na przykład, aby utworzyć nowy plik, kliknij przycisk **Plik -> New**.
Aby zapisać je, kliknij przycisk **Plik -> Zapisz** , a następnie wprowadź nazwę pliku, teraz załóżmy `HelloWorld.ps1`.
Aby zamknąć plik, kliknij pozycję "x" obok nazwy pliku.
Aby zakończyć działanie programu Visual Studio Code, **Plik -> Zakończ**.

#### <a name="using-a-specific-installed-version-of-powershell"></a>Przy użyciu określonych zainstalowana wersja programu PowerShell

Jeśli chcesz używać określonego instalacji programu PowerShell z kodem Visual Studio, należy dodać nową zmienną do pliku ustawień użytkownika.

1. Kliknij przycisk **Plik -> Preferencje -> Ustawienia**
1. Pojawi się dwie części edytora.
   W okienku prawej krawędzi (`settings.json`), włóż do poniższych ustawień odpowiedni dla Twojego systemu operacyjnego między dwoma nawiasów klamrowych (`{` i `}`) i Zastąp *<version>* z zainstalowana Wersja programu PowerShell:

  ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
  ```
1. Zastąp ustawienia ścieżka do żądanego pliku wykonywalnego programu PowerShell
1. Zapisz plik ustawień i ponownie uruchom Visual Studio Code

#### <a name="configuration-settings-for-visual-studio-code"></a>Ustawienia konfiguracji dla programu Visual Studio Code

Wykonując kroki opisane w poprzednim akapicie można dodać ustawienia konfiguracji w `settings.json`.

Zaleca się następujące ustawienia konfiguracji dla programu Visual Studio Code:

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a>Profilowanie kodu Visual Studio

### <a name="no-workspace-debugging"></a>Obszar roboczy bez debugowania

Począwszy od wersji programu Visual Studio Code 1.9 można debugować skryptów programu PowerShell bez konieczności otwierania folder zawierający skrypt programu PowerShell.
Po prostu otwórz plik skryptu programu PowerShell z **Plik -> Otwórz plik...** , ustaw punkt przerwania w wierszu (naciśnij klawisz F9), a następnie naciśnij klawisz F5, aby rozpocząć debugowania.
Zostanie wyświetlony w okienku Akcje debugowania są wyświetlane, co pozwala podzielić debugera, krok, wznowienie i zatrzymanie debugowania.

### <a name="workspace-debugging"></a>Debugowanie obszaru roboczego

Obszar roboczy debugowania odwołuje się do debugowania w kontekście folderu, który został otwarty w programie Visual Studio Code przy użyciu **Otwórz Folder...**  z **pliku** menu.
Folder, który można otworzyć jest zwykle folderu projektu programu PowerShell i/lub katalogu głównego repozytorium Git.

Nawet w tym trybie można uruchomić debugowania aktualnie zaznaczonego skryptu PowerShell po prostu naciskając klawisz F5.
Jednak debugowania obszaru roboczego można zdefiniować wiele konfiguracji debugowania, niż tylko debugowanie aktualnie otwarty plik.
Na przykład można dodać konfiguracji, aby:

- Uruchom testy Pester w debugerze
- Uruchom określony plik z argumentami w debugerze
- Uruchamianie sesji interaktywnej w debugerze
- Dołącz debuger do procesu hosta programu PowerShell

Wykonaj następujące kroki, aby utworzyć plik konfiguracji debugowania:

1. Otwórz **debugowania** widoku naciskając **Ctrl + Shift + D** (**Cmd + Shift + D** dla komputerów Mac).
1. Naciśnij klawisz **Konfiguruj** koło zębate ikonę na pasku narzędzi.
1. Visual Studio Code spowoduje wyświetlenie monitu o **wybierz środowisko**.
   Wybierz **PowerShell**.

   Gdy to zrobisz, Visual Studio Code tworzy katalog i plik ".vscode\launch.json" w katalogu głównym folderu roboczego.
   Jest to przechowywania konfiguracji debugowania. Jeśli pliki znajdują się w repozytorium Git, zwykle można przekazać plik launch.json.
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
Jednak po otwarciu tego pliku w edytorze, zobaczysz **Dodawanie konfiguracji...**  przycisku.
Można nacisnąć przycisk, aby dodać więcej konfiguracji debugowania programu PowerShell. Jest jedną konfigurację przydatną, aby dodać **środowiska PowerShell: uruchamianie skryptu**.
W tej konfiguracji można określić specjalny plik z argumentów opcjonalnych, które można uruchomić przy każdym naciśnięciu klawisza F5 niezależnie od tego, który plik jest aktualnie aktywne w edytorze.

Po ustanowieniu z konfiguracji debugowania, można wybrać konfigurację, która ma być używany podczas sesji debugowania, wybierając jedną z listy rozwijanej w konfiguracji debugowania **debugowania** narzędzi widoku.

Istnieje kilka blogów, które mogą być pomocne ułatwiających rozpoczęcie pracy przy użyciu rozszerzenia programu PowerShell dla programu Visual Studio Code

- Kod Visual Studio: [rozszerzenia programu PowerShell][ps-extension]
- [Zapis i debugowania skryptów programu PowerShell w programie Visual Studio Code][debug]
- [Debugowanie wskazówki kodu programu Visual Studio][vscode-guide]
- [Debugowanie programu PowerShell w programie Visual Studio Code][ps-vscode]
- [Wprowadzenie do rozwoju programu PowerShell w programie Visual Studio Code][getting-started]
- [Visual Studio Code edycji funkcje do tworzenia aplikacji programu PowerShell — część 1][editing-part1]
- [Visual Studio Code edycji funkcje do tworzenia aplikacji programu PowerShell — część 2][editing-part2]
- [Debugowanie skryptów programu PowerShell w programie Visual Studio Code — część 1][debugging-part1]
- [Debugowanie skryptów programu PowerShell w programie Visual Studio Code — część 2][debugging-part2]

[ise]: ../ise-guide.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-macOS-and-Linux.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]:https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]:https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]:https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]:https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]:https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a>Rozszerzenie programu PowerShell dla programu Visual Studio Code

Kod źródłowy rozszerzenia programu PowerShell można znaleźć w [GitHub](https://github.com/PowerShell/vscode-powershell).