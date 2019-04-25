---
ms.date: 06/12/2017
keywords: jea, programu powershell, zabezpieczeń
title: Wymagania wstępne dotyczące usługi JEA
ms.openlocfilehash: acc16c0c7eec357b621c0706a66b8752ae5578cd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084848"
---
# <a name="prerequisites"></a>Wymagania wstępne

> Dotyczy: Windows PowerShell 5.0

Just Enough Administration, jest to funkcja dostępna przy użyciu programu Windows PowerShell 5.0 lub nowszy.
W tym temacie opisano wymagania wstępne, które muszą zostać spełnione, aby rozpocząć korzystanie z usługi JEA.

## <a name="install-jea"></a>Instalowanie usługi JEA

Technologia JEA jest dostępny za pomocą programu Windows PowerShell 5.0 lub nowszy, ale do pełnego zestawu funkcji zalecane jest, zainstaluj najnowszą wersję programu PowerShell dostępnych w systemie.
W poniższej tabeli opisano dostępności JEA firmy w systemie Windows Server:

System operacyjny serwera   | Dostępność usługi JEA
--------------------------|--------------------------------
Windows Server 2016       | Wstępnie zainstalowane
Windows Server 2012 R2    | Pełna funkcjonalność z programem WMF 5.1
Windows Server 2012       | Pełna funkcjonalność z programem WMF 5.1
Windows Server 2008 R2    | Ograniczona funkcjonalność<sup>1</sup> z programem WMF 5.1

Umożliwia także JEA na komputerze domowe lub firmowe:

System operacyjny klienta   | Dostępność usługi JEA
--------------------------|-----------------------------------------------------
Windows 10 1607+          | Wstępnie zainstalowane
Windows 10 1603, 1511     | Wstępnie zainstalowane, za pomocą funkcjonalność ograniczona<sup>2</sup>
Windows 10 1507           | Niedostępne
Windows 8, 8.1            | Pełna funkcjonalność z programem WMF 5.1
Windows 7                 | Ograniczona funkcjonalność<sup>1</sup> z programem WMF 5.1

<sup>1</sup> JEA nie można skonfigurować do kont usług zarządzanych przez grupę w systemie Windows Server 2008 R2 lub Windows 7.
Kont wirtualnych i innych funkcji JEA *są* obsługiwane.

<sup>2</sup> systemu Windows 10 w wersji 1511 i 1603 nie obsługują następujące funkcje usługi JEA: uruchamianie zgodnie z grupą zarządzane konta usług, zasady dostępu warunkowego w konfiguracji sesji, dysku użytkownika i musi udzielać dostępu do kont użytkowników lokalnych.
Aby uzyskać pomoc techniczną dla tych funkcji, należy zaktualizować Windows do wersji 1607 (Rocznicowa aktualizacja) lub nowszej.

### <a name="check-which-version-of-powershell-is-installed"></a>Sprawdź, która wersja programu PowerShell jest zainstalowana

Aby sprawdzić, jaka wersja programu PowerShell jest zainstalowany w systemie, zapoznaj się z `$PSVersionTable` zmiennej w wierszu polecenia programu Windows PowerShell.

```powershell
$PSVersionTable.PSVersion
```

```output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

Jesteś gotowy do użycia usługi JEA, jeśli *głównych* wersja jest równa lub większa niż **5**.
Aby uzyskać najlepsze wyniki, a dostęp do najnowszych funkcji, zaleca się uaktualnienie do wersji programu PowerShell **5.1** gdy jest to możliwe.

### <a name="install-windows-management-framework"></a>Zainstaluj program Windows Management Framework

Jeśli używasz starszej wersji programu PowerShell, należy zaktualizować system najnowsza aktualizacja usługi Windows Management Framework (WMF).
Pakiety aktualizacji i link do najnowszej wersji programu WMF są dostępne w [Centrum pobierania](https://blogs.msdn.microsoft.com/powershell/2016/02/24/windows-management-framework-wmf-5-0-rtm-packages-has-been-republished/).

Zdecydowanie zaleca się testowanie zgodności Twojego obciążenia za pomocą programu WMF przed uaktualnieniem wszystkich serwerów.

Użytkownicy systemu Windows 10, należy zainstalować najnowsze aktualizacje funkcji, aby uzyskać bieżącą wersję środowiska Windows PowerShell.

## <a name="enable-powershell-remoting"></a>Włączanie komunikacji zdalnej programu PowerShell

Komunikacja zdalna programu PowerShell zapewnia podstawę, na którym bazuje JEA.
W związku z tym jest niezbędne do zapewnienia komunikacji zdalnej programu PowerShell jest włączona i [zabezpieczenie](/powershell/scripting/setup/winrmsecurity) w systemie, zanim użyjesz usługi JEA.

Komunikacja zdalna programu PowerShell jest włączona domyślnie w systemie Windows Server 2012, 2012 R2 i 2016.
Komunikacja zdalna programu PowerShell można włączyć, uruchamiając następujące polecenie w oknie programu PowerShell z podwyższonym poziomem uprawnień.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>Włączanie rejestrowania blok skryptu jest (opcjonalnie) i moduł programu PowerShell

Następujące kroki włączyć rejestrowanie dla wszystkich akcji programu PowerShell w systemie.
Rejestrowanie modułu programu PowerShell nie jest wymagane dla usługi JEA, jednak zdecydowanie zalecane jest włączenie go w celu upewnij się, że użytkownicy polecenia uruchamiają są rejestrowane w centralnej lokalizacji.

Można skonfigurować zasad logowania modułu programu PowerShell, za pomocą zasad grupy.

1. Otwórz Edytor lokalnych zasad grupy na stacji roboczej lub obiektu zasad grupy w konsoli zarządzania zasadami grupy na kontrolerze domeny usługi Active Directory
2. Przejdź do **konfiguracji komputera\\Szablony administracyjne\\składników Windows\\programu Windows PowerShell**
3. Kliknij dwukrotnie **mogą włączyć rejestrowanie modułów**
4. Kliknij przycisk **włączone**
5. W sekcji Opcje kliknąć **Pokaż** obok nazwy modułu
6. Typ `\*` w wyświetlonym oknie. To powoduje, że rejestrowanie poleceń z wszystkich modułów programu PowerShell.
7. Kliknij przycisk **OK** do ustawiania zasad
8. Kliknij dwukrotnie **mogą włączyć rejestrowanie programu PowerShell skrypt bloku**
9. Kliknij przycisk **włączone**
10. Kliknij przycisk **OK** do ustawiania zasad
11. (W przypadku przyłączonych do domeny komputerów tylko) Uruchom `gpupdate` lub zaczekaj na przetwarzanie zaktualizowane zasady i zastosować ustawienia zasad grupy

Można również włączyć transkrypcji PowerShell całego systemu za pomocą zasad grupy.

## <a name="next-steps"></a>Następne kroki

[Utwórz plik możliwości roli](role-capabilities.md)

[Utwórz plik konfiguracji sesji](session-configurations.md)

## <a name="see-also"></a>Zobacz też

[Dodatkowe informacje na temat zabezpieczeń komunikacji zdalnej programu PowerShell i usługi WinRM](/powershell/scripting/setup/winrmsecurity)

[*Program PowerShell ♥ zespołem niebieskim* wpis w blogu dotyczący zabezpieczeń](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)