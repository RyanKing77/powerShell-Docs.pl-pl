---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4eb2f0bac4f2169a9a06d80cb4fa214a09cdfa86
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892988"
---
# <a name="known-issues-and-limitations"></a>Znane problemy i ograniczenia

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a>Skróty programu PowerShell są otwarte w przypadku, gdy po raz pierwszy użyty

**Rozwiązanie:** wykonaj jedną z następujących czynności:

1. Kliknij prawym przyciskiem myszy skrót programu PowerShell. Wybierz pozycję "Windows PowerShell", aby uruchomić w trybie bez podniesionych uprawnień.
2. Kliknij prawym przyciskiem myszy skrót programu PowerShell. Kliknij prawym przyciskiem myszy kliknij "Windows PowerShell" i wybierz pozycję "Uruchom jako Administrator" można uruchomić w trybie podniesionych uprawnień.

Po wykonaniu jednej z powyższych akcji skróty programu PowerShell będzie działać. Te akcje muszą być wykonywane tylko raz.

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a>Moduły programu PowerShell i zasobów DSC raportowania błędów dotyczących ExecutionPolicy Windows 7

Windows 7 korzystanie z modułów programu PowerShell i zasobów DSC może spowodować błędy raportowane o ExecutionPolicy.

**Rozwiązanie:** ustawić ExecutionPolicy RemoteSigned, uruchamiając następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień (Uruchom jako Administrator):

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a>Łączenie do starego zdalnego punktu końcowego programu Exchange powoduje awarię

Stary punkt końcowy wymiany przekierowuje do nowego punktu końcowego. Brak usterkę w logice przekierowania powstałą w awarii.

**Rozwiązanie:** Połącz bezpośrednio z nowego punktu końcowego.

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a>Funkcja rejestrowania spisu oprogramowania jest błędnie zatrzymana po zakończeniu instalacji programu WMF 5.0 w systemie Windows Server 2012 R2

Podczas instalowania programu WMF 5.0 na Windows Server 2012 R2, który jest już uruchomiony program SIL, funkcję rejestrowania spisu oprogramowania jest błędnie zatrzymana po zakończeniu instalacji.

**Rozwiązanie:** Uruchom polecenie cmdlet Start-SilLogging raz po zakończeniu instalacji programu WMF, ponieważ proces instalacji błędnie przestanie funkcję rejestrowania spisu oprogramowania.

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a>`Get-ChildItem` nie działa, jeśli - LiteralPath i - Recurse są używane razem

Jeśli nazwa katalogu zawiera nieprawidłowy symbol wieloznaczny, następnie `Get-ChildItem` nie przyniesie oczekiwanych rezultatów, gdy - LiteralPath i - Recurse są używane razem.

**Rozwiązanie:** nie idealnym rozwiązaniem, ale bieżące obejście polega na implementowanie rekursji w skrypcie, zamiast polegać na polecenia cmdlet.

## <a name="sysprep-fails-after-wmf-50-installation"></a>Program Sysprep zakończy się niepowodzeniem po instalacji programu WMF 5.0

Istnieją dwa obejścia tego problemu, w zależności od wersji systemu Windows Server są uruchomione.

**Rozwiązanie:**

- Dla komputerów z systemami **systemu Windows Server 2008 R2**
  1. Otwórz program Powershell jako administrator
  2. Uruchom następujące polecenie

     ```powershell
     Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
     ```

  3. Uruchom polecenie i zignorować błąd, ponieważ oczekuje.

     ```powershell
     Publish-SilData
     ```

  4. Usuwanie plików w katalogu \Windows\System32\Logfiles\SIL\

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. Instalowanie wszystkich dostępnych ważnych aktualizacji Windows i rozpocząć operację Sysyprep normalnie.

- Dla komputerów z systemami **systemu Windows Server 2012**
  1. Po zainstalowaniu programu WMF 5.0 na serwerze, aby być w Sysprep'd, zaloguj się jako administrator.
  2. Skopiuj Generize.xml z \Windows\System32\Sysprep\ActionFiles\ katalogu do lokalizacji poza katalogiem Windows, C:\ na przykład.
  3. Otwórz kopii Generalize.xml w Notatniku.
  4. Znajdź i usuń następujący tekst: jedno wystąpienie każdego musi zostać usunięte (będą one osiągnie koniec dokumentu).

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. Zapisywania edytowanej kopii Generalize.xml i zamknij plik.
  6. Otwórz wiersz polecenia jako administrator
  7. Uruchom następujące polecenie, aby przejąć na własność pliku Generalize.xml w folderze system32:

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. Uruchom następujące polecenie, aby ustawić odpowiednie uprawnienia do pliku:

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - Wybierz odpowiedź tak, w wierszu o potwierdzenie.
     - Należy pamiętać, że `<AdministratorUserName>` powinna zostać zastąpiona przez nazwę użytkownika, który jest administratorem na komputerze. Na przykład, "Administrator".

  9. Skopiuj plik, edytować i zapisać za pośrednictwem katalogu programu Sysprep przy użyciu następującego polecenia:

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - Wybierz odpowiedź tak, aby zastąpić (należy pamiętać, że jeśli nie ma żadnego monitu, aby zastąpić, lub sprawdź wprowadzona ścieżka).
     - Przyjęto założenie, że Twoje edytowanej kopii Generalize.xml zostały skopiowane do C:\.

  10. Generalize.XML został zaktualizowany o obejście. Po włączeniu opcji generalize, uruchom program Sysprep.