---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9ead27fd5d4f146e9062488c1c8cc22a073b922e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187106"
---
# <a name="improvements-in-powershell-script-debugging"></a>Ulepszenia debugowania skryptów programu PowerShell

Wiele ulepszeń zostały wprowadzone w programie PowerShell 5.0 udoskonalenie debugowania:

## <a name="break-all"></a>Przerwij wszystkie

Konsola programu PowerShell i Windows PowerShell ISE teraz umożliwiają wkroczenia do debugera do uruchamiania skryptów. Działa to zarówno lokalnych, jak i zdalnych sesji.

W konsoli, naciśnij klawisz **klawisze Ctrl + Break**.

ISE, naciśnij klawisz **Ctrl + B**, lub użyj **debugowanie -> Przerwij wszystkie** polecenia menu.

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a>Debugowanie zdalne i zdalne edytowanie plików w środowisku Windows PowerShell ISE

Windows PowerShell ISE umożliwia teraz otworzyć i edytować pliki w sesji zdalnej, uruchamiając polecenie PSEdit.
Na przykład można otworzyć pliku do edycji z wiersza polecenia w sesji zdalnej w następujący sposób:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Ponadto można edytować i zapisać zmiany w pliku zdalnego, który jest automatycznie otwierane w programie Windows PowerShell ISE po trafieniu punktu przerwania.
Teraz możesz debugowania pliku skryptu, który jest uruchomiony na komputerze zdalnym, edytować plik, aby naprawić błąd, a następnie ponownie uruchom zmodyfikowanego skryptu.

## <a name="advanced-script-debugging"></a>Debugowanie skryptów zaawansowane

Istnieją nowe, zaawansowane funkcje debugowania, które umożliwiają dołączanie do każdy proces komputera lokalnego, który został załadowany środowiska Windows PowerShell i debugowania dowolnych obszarach działania w tym procesie.

### <a name="runspace-debugging"></a>Debugowanie obszaru działania

Nowe polecenia cmdlet dodano umożliwiające listę obszarach bieżącego działania w ramach procesu i dołączyć do tego obszaru działania do debugowania skryptów konsoli środowiska Windows PowerShell lub debugera ISE:

-   Get-obszaru działania
-   Obszarze działania debugowania
-   Włącz RunspaceDebug
-   Wyłącz RunspaceDebug
-   Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>Dołączanie do procesu hostingu środowiska PowerShell

Teraz można dołączyć do procesu dowolnego komputera, który ma środowiska Windows PowerShell, załadować. W tym celu należy wprowadzić w sesji interaktywnej z procesem, podobnie jak wprowadzić w sesji interaktywnej zdalnego przy użyciu polecenia cmdlet Enter-PSSession:

-   Wprowadź PSHostProcess
-   PSHostProcess zakończenia
