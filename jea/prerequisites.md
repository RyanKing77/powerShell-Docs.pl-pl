---
ms.date: 07/10/2019
keywords: jea, programu powershell, zabezpieczeń
title: Wymagania wstępne dotyczące usługi JEA
ms.openlocfilehash: 8fca5c068412e86acfdb8bed400699f721b76191
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734280"
---
# <a name="prerequisites"></a>Wymagania wstępne

Just Enough Administration, jest to funkcja dostępna w programie PowerShell 5.0 lub nowszy. W tym artykule opisano wymagania wstępne, które muszą zostać spełnione, aby rozpocząć korzystanie z technologii JEA.


## <a name="check-which-version-of-powershell-is-installed"></a>Sprawdź, która wersja programu PowerShell jest zainstalowana

Aby sprawdzić, jaka wersja programu PowerShell jest zainstalowany w systemie, zapoznaj się z `$PSVersionTable` zmiennej w wierszu polecenia programu Windows PowerShell.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

JEA jest dostępne przy użyciu programu PowerShell w wersji 5.0 lub nowszy. Do pełnej funkcjonalności zalecane jest, zainstaluj najnowszą wersję programu PowerShell dostępnych w systemie. W poniższej tabeli opisano dostępności JEA firmy w systemie Windows Server:

| System operacyjny serwera |                Dostępność usługi JEA                |
| ----------------------- | ---------------------------------------------- |
| Windows Server 2016+    | Wstępnie zainstalowane                                   |
| Windows Server 2012 R2  | Pełna funkcjonalność z programem WMF 5.1                |
| Windows Server 2012     | Pełna funkcjonalność z programem WMF 5.1                |
| Windows Server 2008 R2  | Ograniczona funkcjonalność<sup>1</sup> z programem WMF 5.1 |

Umożliwia także JEA na komputerze domowe lub firmowe:

| System operacyjny klienta |                   Dostępność usługi JEA                   |
| ----------------------- | ---------------------------------------------------- |
| Windows 10 1607+        | Wstępnie zainstalowane                                         |
| Windows 10 1603, 1511   | Wstępnie zainstalowane, za pomocą funkcjonalność ograniczona<sup>2</sup> |
| Windows 10 1507         | Niedostępne                                        |
| Windows 8, 8.1          | Pełna funkcjonalność z programem WMF 5.1                      |
| Windows 7               | Ograniczona funkcjonalność<sup>1</sup> z programem WMF 5.1       |

- <sup>1</sup> JEA nie można skonfigurować konta usług zarządzane przez grupę w systemie Windows Server 2008 R2 lub Windows 7. Kont wirtualnych i innych funkcji JEA *są* obsługiwane.

- <sup>2</sup> następujące funkcje usługi JEA nie są obsługiwane w systemie Windows 10 w wersji 1511 i 1603:

  - Uruchamianie jako konto usługi zarządzane przez grupę
  - Zasady dostępu warunkowego w konfiguracji sesji
  - Stacji użytkownika
  - Udzielanie dostępu do kont użytkowników lokalnych

  Aby uzyskać pomoc techniczną dla tych funkcji, należy zaktualizować Windows do wersji 1607 (Rocznicowa aktualizacja) lub nowszej.

### <a name="install-windows-management-framework"></a>Zainstaluj program Windows Management Framework

Jeśli używasz starszej wersji programu PowerShell może być konieczne zaktualizowanie systemu klienta przy użyciu najnowszych aktualizacji Windows Management Framework (WMF). Aby uzyskać więcej informacji, zobacz [dokumentacji programu WMF](/powershell/wmf/overview).

Zaleca się testowanie zgodności Twojego obciążenia za pomocą programu WMF przed uaktualnieniem wszystkich serwerów.

Użytkownicy systemu Windows 10, należy zainstalować najnowsze aktualizacje funkcji, aby uzyskać bieżącą wersję środowiska Windows PowerShell.

## <a name="enable-powershell-remoting"></a>Włączanie komunikacji zdalnej programu PowerShell

Komunikacja zdalna programu PowerShell zapewnia podstawę, na którym bazuje JEA. Jest to niezbędne do zapewnienia komunikacji zdalnej programu PowerShell jest włączona i odpowiednio zabezpieczony, zanim będzie można użyć technologii JEA. Aby uzyskać więcej informacji, zobacz [zabezpieczeń WinRM](/powershell/scripting/learn/remoting/winrmsecurity).

Komunikacja zdalna programu PowerShell jest włączona domyślnie w systemie Windows Server 2012, 2012 R2 i 2016. Komunikacja zdalna programu PowerShell można włączyć, uruchamiając następujące polecenie w oknie programu PowerShell z podwyższonym poziomem uprawnień.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>Włączanie rejestrowania blok skryptu jest (opcjonalnie) i moduł programu PowerShell

Następujące kroki włączyć rejestrowanie dla wszystkich akcji programu PowerShell w systemie. Rejestrowanie modułu programu PowerShell nie jest wymagana dla usługi JEA, jednak zaleca się, że włączyć rejestrowanie, aby upewnić się, że użytkownicy polecenia uruchamiają są rejestrowane w centralnej lokalizacji.

Można skonfigurować zasad logowania modułu programu PowerShell, za pomocą zasad grupy.

1. Otwórz Edytor lokalnych zasad grupy na stacji roboczej lub obiektu zasad grupy w konsoli zarządzania zasadami grupy na kontrolerze domeny usługi Active Directory
2. Przejdź do **konfiguracji komputera\\Szablony administracyjne\\składników Windows\\programu Windows PowerShell**
3. Kliknij dwukrotnie **Włączanie logowania modułu**
4. Kliknij przycisk **włączone**
5. W sekcji Opcje kliknąć **Pokaż** obok nazwy modułu
6. Typ `*` w oknie podręcznym logowania polecenia ze wszystkich modułów.
7. Kliknij przycisk **OK** do ustawiania zasad
8. Kliknij dwukrotnie **włączyć w bloku skryptu środowiska PowerShell rejestrowania**
9. Kliknij przycisk **włączone**
10. Kliknij przycisk **OK** do ustawiania zasad
11. (W przypadku przyłączonych do domeny komputerów tylko) Uruchom `gpupdate` lub zaczekaj na przetwarzanie zaktualizowane zasady i zastosować ustawienia zasad grupy

Można również włączyć transkrypcji PowerShell całego systemu za pomocą zasad grupy.

## <a name="next-steps"></a>Następne kroki

[Utwórz plik możliwości roli](role-capabilities.md)

[Utwórz plik konfiguracji sesji](session-configurations.md)

## <a name="see-also"></a>Zobacz też

[Zabezpieczenia usługi WinRM](/powershell/scripting/learn/remoting/winrmsecurity)

[Program PowerShell ♥ zespołem niebieskim](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
