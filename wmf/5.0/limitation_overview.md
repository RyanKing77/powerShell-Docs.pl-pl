---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4b006d2ac812abf1f281b6b4e382c2760f92a95c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186834"
---
# <a name="known-issues-and-limitations"></a>Znane problemy i ograniczenia

<a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a>Skróty programu PowerShell są dzielone, gdy jest używany po raz pierwszy
------------------------------------------------------------

**Rozwiązanie:** wykonaj jedną z następujących czynności:

1.  Kliknij prawym przyciskiem myszy skrót programu PowerShell. Wybierz "Środowiska Windows PowerShell" można uruchomić w trybie bez podniesionych uprawnień.
2.  Kliknij prawym przyciskiem myszy skrót programu PowerShell. Kliknij prawym przyciskiem myszy kliknij "Środowiska Windows PowerShell" i wybierz pozycję "Uruchom jako Administrator" były uruchamiane w trybie z podniesionymi uprawnieniami.

Po wykonaniu dowolnej z powyższych akcji skróty programu PowerShell będzie działać. Czynności te należy wykonać tylko raz.


<a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a>Moduły programu PowerShell i zasoby DSC raportować błędy dotyczące ExecutionPolicy w systemie Windows 7
-------------------------------------------------------------------------------------
W systemie Windows 7 użyj moduły programu PowerShell i zasobów DSC może spowodować błędy raportowane o ExecutionPolicy.

**Rozwiązanie:** ustawić ExecutionPolicy RemoteSigned, uruchamiając następujące polecenie w sesji programu PowerShell z podwyższonym poziomem uprawnień (Uruchom jako Administrator):

```powershell
Set-ExecutionPolicy RemoteSigned
```

<a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a>Nawiązywanie starego zdalny punkt końcowy wymiany powoduje awarii
------------------------------------------------------------

Stary punkt końcowy wymiany przekierowuje do nowego punktu końcowego. Usterki logiki przekierowania powstałą w jest awarii.

**Rozwiązanie:** Połącz bezpośrednio z nowego punktu końcowego.


<a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a>Funkcja rejestrowania spisu oprogramowania przez pomyłkę zostanie zatrzymana po zakończeniu instalacji WMF 5.0 w systemie Windows Server 2012 R2
-------------------------------------------------------------------------------------------------------------

Podczas instalowania WMF 5.0 na Windows Server 2012 R2, która jest już uruchomiona SIL, funkcję rejestrowania spisu oprogramowania przez pomyłkę zostanie zatrzymana po zakończeniu instalacji.

**Rozwiązanie:** uruchomić polecenie cmdlet Start-SilLogging raz po zainstalowaniu pakietu WMF, ponieważ proces instalacji błędnie przestanie funkcję rejestrowania spisu oprogramowania.

<a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a>Get-ChildItem nie działa, jeśli - LiteralPath i - Recurse są używane razem
--------------------------------------------------------------------------

Jeśli nazwa katalogu zawiera nieprawidłowy symbol wieloznaczny, następnie Get-ChildItem nie zapewni oczekiwanych rezultatów przy zarówno - LiteralPath i - Recurse są używane razem.

**Rozwiązanie:** nie nadaje się doskonale, ale bieżący obejściem jest wdrożenie rekursji w skrypcie, a nie zależą od polecenia cmdlet.


<a name="sysprep-fails-after-wmf-50-installation"></a>Program Sysprep nie powiedzie się po zainstalowaniu pakietu WMF 5.0
----------------------------------------

Istnieją dwa obejścia tego problemu, w zależności od wersji systemu Windows Server są uruchomione.

**Rozwiązanie:**
- Dla komputerów z systemami **systemu Windows Server 2008 R2**
  1. Otwórz program Powershell jako administrator
  2. Uruchom następujące polecenie

  ```powershell
    Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
  ```
  3. Uruchom polecenie i zignorować błąd, są one prawidłowo.

  ```powershell
    Publish-SilData
   ```
  4. Usuń pliki w katalogu \Windows\System32\Logfiles\SIL\

  ```powershell
    Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
  ```
  5. Zainstalowanie dostępne ważne aktualizacje systemu Windows oraz operacji Sysyprep normalnie.

- Dla komputerów z systemami **systemu Windows Server 2012**
  1.    Po zainstalowaniu pakietu WMF 5.0 na serwerze, aby być w Sysprep d, zaloguj się jako administrator.
  2.    Skopiuj Generize.xml z katalogu \Windows\System32\Sysprep\ActionFiles\ do lokalizacji poza katalog Windows C:\ na przykład.
  3.    Twoja kopia Generalize.xml Otwórz w Notatniku.
  4.    Znajdź i usuń następujący tekst: jedno wystąpienie każdego musi zostać usunięte (zostaną one zbliża się koniec dokumentu).

    ```
    <sysprepOrder order="0x3200"></sysprepOrder>
    <sysprepOrder order="0x3300"></sysprepOrder>
    ```

  5.    Zapisywania edytowanej kopii Generalize.xml i zamknij plik.
  6.    Otwórz wiersz polecenia jako administrator
  7.    Uruchom następujące polecenie, aby przejąć na własność pliku Generalize.xml w folderze system32:

    ```
    Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```

  8.    Uruchom następujące polecenie, aby ustawić odpowiednie uprawnienia do pliku:

    ```
    Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
    ```
      * Odpowiedź tak na monit o potwierdzenie.
      * Należy pamiętać, że `<AdministratorUserName>` powinna zostać zastąpiona przez nazwę użytkownika, który jest administratorem na tym komputerze. Na przykład "Administrator".

  9.    Skopiuj plik, edytować i zapisać za pośrednictwem katalogu Sysprep przy użyciu następującego polecenia:

    ```
    xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```
      * Odpowiedź tak, aby zastąpić (należy pamiętać, że jeśli nie ma żadnego monitu, aby zastąpić, double Sprawdź wprowadzona ścieżka).
      * Przyjęto założenie, że Twoje edytowanej kopii Generalize.xml został skopiowany do C:\.

  10.   Generalize.XML został zaktualizowany o obejście. Uruchom program Sysprep z włączoną opcją generalize.
