---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Ulepszenia debugowania skryptów programu PowerShell
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856175"
---
# <a name="improvements-in-powershell-script-debugging"></a>Ulepszenia debugowania skryptów programu PowerShell

PowerShell 5.0 zawiera kilka ulepszeń, które usprawniają środowisko debugowania.

## <a name="break-all"></a>Przerwij wszystko

Konsola programu PowerShell i środowisku PowerShell ISE teraz umożliwiają wkroczenia do debugera do uruchamiania skryptów. Działa to zarówno lokalnych, jak i zdalnych sesji.

W konsoli, naciśnij klawisz <kbd>Ctrl</kbd>+<kbd>Przerwij</kbd>.

W środowisku ISE, naciśnij klawisz <kbd>Ctrl</kbd>+<kbd>B</kbd>, lub użyj **Debuguj -> Przerwij wszystko** polecenia menu.

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a>Zdalne debugowanie i zdalne edytowanie plików w środowisku PowerShell ISE

Program PowerShell ISE umożliwia teraz otwierać i edytować pliki w sesji zdalnej za pomocą polecenia PSEdit.
Na przykład można otworzyć pliku do edycji z wiersza polecenia w sesji zdalnej w następujący sposób:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Ponadto można edytować i zapisać zmiany w pliku zdalnego, który jest automatycznie otwierany w środowisku PowerShell ISE, po osiągnięciu punktu przerwania. Można teraz debugować plik skryptu, który jest uruchomiony na komputerze zdalnym, Edytuj plik, aby naprawić błąd, a następnie ponownie uruchom zmodyfikowany skrypt.

## <a name="advanced-script-debugging"></a>Debugowanie skryptów zaawansowane

Istnieją nowe, zaawansowane funkcje debugowania, które umożliwiają dołączanie do każdego procesu komputer lokalny, który został załadowany PowerShell i debugowania dowolnego obszarach działania w tym procesie.

### <a name="runspace-debugging"></a>Debugowanie obszarem działania

Nowe polecenia cmdlet zostały dodane, umożliwiające listy obszary bieżącego działania w ramach procesu i dołączyć do tego obszaru działania dotyczące debugowania skryptów konsolę programu PowerShell lub środowisku PowerShell ISE debugera:

- Get-obszarem działania
- Obszar działania debugowania
- Enable-RunspaceDebug
- Disable-RunspaceDebug
- Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>Dołącz do procesu hostingu programu PowerShell

Teraz można dołączyć do procesu dowolnego komputera, który został załadowany PowerShell. Można to zrobić, należy wprowadzić w interaktywnej sesji z procesem hosta. Aby uzyskać więcej informacji, zobacz:

- [Enter-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [Exit-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
