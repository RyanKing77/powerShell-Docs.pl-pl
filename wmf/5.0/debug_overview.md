---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 22a027ebc97e15075980bc77ce272d8ecdae0b5f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058668"
---
# <a name="improvements-in-powershell-script-debugging"></a>Ulepszenia debugowania skryptów programu PowerShell

Szereg ulepszeń zostały wprowadzone w programie PowerShell 5.0, aby ulepszyć środowisko debugowania:

## <a name="break-all"></a>Przerwij wszystko

Konsola programu PowerShell i Windows PowerShell ISE teraz umożliwiają wkroczenia do debugera do uruchamiania skryptów. Działa to zarówno lokalnych, jak i zdalnych sesji.

W konsoli, naciśnij klawisz **Ctrl + Break**.

W środowisku ISE, naciśnij klawisz **Ctrl + B**, lub użyj **Debuguj -> Przerwij wszystko** polecenia menu.

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a>Zdalne debugowanie i zdalne edytowanie plików w środowisku Windows PowerShell ISE

Windows PowerShell ISE umożliwia teraz otwierać i edytować pliki w sesji zdalnej za pomocą polecenia PSEdit.
Na przykład można otworzyć pliku do edycji z wiersza polecenia w sesji zdalnej w następujący sposób:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Ponadto można edytować i zapisać zmiany w pliku zdalnego, który jest automatycznie otwierany w środowisku Windows PowerShell ISE, po osiągnięciu punktu przerwania.
Można teraz debugować plik skryptu, który jest uruchomiony na komputerze zdalnym, Edytuj plik, aby naprawić błąd, a następnie ponownie uruchom zmodyfikowany skrypt.

## <a name="advanced-script-debugging"></a>Debugowanie skryptów zaawansowane

Istnieją nowe, zaawansowane funkcje debugowania, które umożliwiają dołączanie do każdego procesu komputer lokalny, który został załadowany programu Windows PowerShell i debugowania dowolnego obszarach działania w tym procesie.

### <a name="runspace-debugging"></a>Debugowanie obszarem działania

Nowe polecenia cmdlet zostały dodane, umożliwiające listy obszary bieżącego działania w ramach procesu i dołączyć do tego obszaru działania dotyczące debugowania skryptów konsoli środowiska Windows PowerShell lub debugera ISE:

-   Get-obszarem działania
-   Obszar działania debugowania
-   Enable-RunspaceDebug
-   Disable-RunspaceDebug
-   Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>Dołącz do procesu hostingu programu PowerShell

Teraz można dołączyć do procesu dowolnego komputera, który został załadowany w programie Windows PowerShell. Możesz to zrobić, należy wprowadzić w interaktywnej sesji z procesem, podobnie jak możesz wprowadzić do interaktywnej sesji zdalnej, uruchamiając polecenie cmdlet Enter-PSSession:

-   Enter-PSHostProcess
-   Zakończ PSHostProcess
