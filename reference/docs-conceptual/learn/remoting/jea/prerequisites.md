---
ms.date: 07/10/2019
keywords: jea, PowerShell, zabezpieczenia
title: Wymagania wstępne JEA
ms.openlocfilehash: 8fca5c068412e86acfdb8bed400699f721b76191
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017937"
---
# <a name="prerequisites"></a>Wymagania wstępne

Wystarczy, że jest dostępna funkcja programu PowerShell w wersji 5,0 lub nowszej. W tym artykule opisano wymagania wstępne, które należy spełnić, aby rozpocząć korzystanie z usługi JEA.


## <a name="check-which-version-of-powershell-is-installed"></a>Sprawdź, która wersja programu PowerShell jest zainstalowana

Aby sprawdzić, która wersja programu PowerShell jest zainstalowana w systemie, sprawdź `$PSVersionTable` zmienną w wierszu polecenia programu Windows PowerShell.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

JEA jest dostępny w programie PowerShell 5,0 i nowszych. W celu zapewnienia pełnej funkcjonalności zaleca się zainstalowanie najnowszej wersji programu PowerShell dostępnej dla danego systemu. W poniższej tabeli opisano dostępność JEA w systemie Windows Server:

| System operacyjny serwera |                Dostępność JEA                |
| ----------------------- | ---------------------------------------------- |
| Windows Server 2016 +    | Wstępnie zainstalowane                                   |
| Windows Server 2012 R2  | Pełna funkcjonalność z funkcją WMF 5,1                |
| Windows Server 2012     | Pełna funkcjonalność z funkcją WMF 5,1                |
| Windows Server 2008 R2  | Zredukowanie funkcjonalności<sup>1</sup> przy użyciu programu WMF 5,1 |

Możesz również użyć JEA na komputerze w domu lub pracy:

| System operacyjny klienta |                   Dostępność JEA                   |
| ----------------------- | ---------------------------------------------------- |
| Windows 10 1607+        | Wstępnie zainstalowane                                         |
| Windows 10 1603, 1511   | Preinstalacja z ograniczoną funkcjonalnością<sup>2</sup> |
| Windows 10 1507         | Niedostępne                                        |
| Windows 8, 8.1          | Pełna funkcjonalność z funkcją WMF 5,1                      |
| Windows 7               | Zredukowanie funkcjonalności<sup>1</sup> przy użyciu programu WMF 5,1       |

- <sup>1</sup> jea nie można skonfigurować do korzystania z kont usług zarządzanych przez grupę w systemie windows Server 2008 R2 lub Windows 7. Obsługiwane *są* konta wirtualne i inne funkcje jea.

- <sup>2</sup> następujące funkcje jea nie są obsługiwane w systemie Windows 10 w wersji 1511 i 1603:

  - Uruchamianie jako konto usługi zarządzane przez grupę
  - Reguły dostępu warunkowego w konfiguracjach sesji
  - Dysk użytkownika
  - Udzielanie dostępu do kont użytkowników lokalnych

  Aby uzyskać pomoc techniczną dotyczącą tych funkcji, zaktualizuj system Windows do wersji 1607 (Aktualizacja z rocznicą) lub wyższą.

### <a name="install-windows-management-framework"></a>Zainstaluj program Windows Management Framework

Jeśli używasz starszej wersji programu PowerShell, może być konieczne zaktualizowanie systemu przy użyciu najnowszej aktualizacji Windows Management Framework (WMF). Aby uzyskać więcej informacji, zobacz [dokumentację dotyczącą WMF](/powershell/wmf/overview).

Zaleca się przetestowanie zgodności obciążenia z pakietem WMF przed uaktualnieniem wszystkich serwerów.

Użytkownicy systemu Windows 10 powinni zainstalować najnowsze aktualizacje funkcji, aby uzyskać aktualną wersję programu Windows PowerShell.

## <a name="enable-powershell-remoting"></a>Włącz obsługę zdalną programu PowerShell

Komunikacja zdalna programu PowerShell zapewnia podstawę, na której jest zbudowany JEA. Jest to konieczne, aby zapewnić, że komunikacja zdalna programu PowerShell jest włączona i prawidłowo zabezpieczona przed użyciem JEA. Aby uzyskać więcej informacji, zobacz [zabezpieczenia usługi WinRM](/powershell/scripting/learn/remoting/winrmsecurity).

Komunikacja zdalna programu PowerShell jest domyślnie włączona w systemach Windows Server 2012, 2012 R2 i 2016. Aby włączyć obsługę zdalną programu PowerShell, należy uruchomić następujące polecenie w oknie programu PowerShell z podwyższonym poziomem uprawnień.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>Włącz rejestrowanie bloków skryptów i modułów programu PowerShell (opcjonalnie)

Poniższe kroki umożliwiają rejestrowanie wszystkich akcji programu PowerShell w systemie. Rejestrowanie modułu programu PowerShell nie jest wymagane dla JEA, jednak zaleca się włączenie rejestrowania, aby upewnić się, że polecenia uruchamiane przez użytkowników są rejestrowane w centralnej lokalizacji.

Zasady rejestrowania modułu programu PowerShell można skonfigurować przy użyciu zasady grupy.

1. Otwórz Edytor lokalnych zasad grupy na stacji roboczej lub obiekcie zasady grupy w Konsola zarządzania zasadami grupy na kontrolerze domena usługi Active Directory
2. Przejdź do **\\konfiguracji komputera Szablony administracyjne\\\\składniki systemu Windows Windows PowerShell**
3. Kliknij dwukrotnie pozycję **Włącz rejestrowanie modułu**
4. Kliknij pozycję **włączone**
5. W sekcji Opcje kliknij pozycję **Pokaż** obok pozycji nazwy modułów
6. Wpisz `*` w oknie podręcznym, aby rejestrować polecenia ze wszystkich modułów.
7. Kliknij przycisk **OK** , aby ustawić zasady
8. Kliknij dwukrotnie pozycję **Włącz rejestrowanie bloku skryptu programu PowerShell**
9. Kliknij pozycję **włączone**
10. Kliknij przycisk **OK** , aby ustawić zasady
11. (Tylko w przypadku komputerów przyłączonych do domeny) Uruchom `gpupdate` lub zaczekaj na zasady grupy, aby przetworzyć zaktualizowane zasady i zastosować ustawienia

Można również włączyć transkrypcję programu PowerShell dla całego systemu za poorednictwem zasady grupy.

## <a name="next-steps"></a>Następne kroki

[Utwórz plik możliwości roli](role-capabilities.md)

[Utwórz plik konfiguracji sesji](session-configurations.md)

## <a name="see-also"></a>Zobacz też

[Zabezpieczenia usługi WinRM](/powershell/scripting/learn/remoting/winrmsecurity)

[Program PowerShell ♥ niebieskiego zespołu](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
