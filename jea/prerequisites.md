---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea, programu powershell, zabezpieczeń"
title: "Wymagania wstępne JEA"
ms.openlocfilehash: e6ee16e34eb9f1f0b2f3601c1aa9e90ab4f785f1
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="prerequisites"></a>Wymagania wstępne

> Dotyczy: środowiska Windows PowerShell 5.0

Tylko tyle administracji jest to funkcja dostępna z programu Windows PowerShell 5.0 lub nowszej.
W tym temacie opisano wymagania wstępne, które muszą być spełnione, aby rozpocząć korzystanie z JEA.

## <a name="install-jea"></a>Zainstaluj JEA

Technologia JEA jest dostępna w programie Windows PowerShell 5.0 lub nowszej, ale do pełnego zestawu funkcji zalecane jest, zainstaluj najnowszą wersję programu PowerShell, dostępna dla systemu.
W poniższej tabeli opisano w JEA dostępności w systemie Windows Server:

System operacyjny serwera   | Dostępność JEA
--------------------------|--------------------------------
Windows Server 2016       | Preinstalowane
Windows Server 2012 R2    | Pełnej funkcjonalności z WMF 5.1
Windows Server 2012       | Pełnej funkcjonalności z WMF 5.1
Windows Server 2008 R2    | Funkcjonalność ograniczona<sup>1</sup> z WMF 5.1

Można także użyć JEA na komputerze domowej lub firmowej:

System operacyjny klienta   | Dostępność JEA
--------------------------|-----------------------------------------------------
Windows 10 1607+          | Preinstalowane
Windows 10 1603, 1511     | Preinstalowane, dzięki ograniczone funkcje<sup>2</sup>
Windows 10 1507           | Niedostępne
Windows 8, 8.1            | Pełnej funkcjonalności z WMF 5.1
Windows 7                 | Funkcjonalność ograniczona<sup>1</sup> z WMF 5.1

<sup>1</sup> JEA nie może być skonfigurowana do używania konta usług zarządzane przez grupę w systemie Windows Server 2008 R2 lub Windows 7.
Kont wirtualnych i inne funkcje JEA *są* obsługiwane.

<sup>2</sup> systemu Windows 10 w wersji 1511 i 1603 nie obsługują następujące funkcje JEA: uruchamianie zgodnie z grupą zarządzane konto usługi, zasady dostępu warunkowego w konfiguracji sesji, dysku użytkownika i udzielenie dostępu do kont użytkowników lokalnych.
Aby uzyskać pomoc techniczną dla tych funkcji, należy zaktualizować system Windows do wersji 1607 (rocznicy aktualizacji) lub nowszej.

### <a name="check-which-version-of-powershell-is-installed"></a>Sprawdź, która wersja programu PowerShell jest zainstalowany

Aby sprawdzić, która wersja programu PowerShell jest zainstalowana w systemie, sprawdź `$PSVersionTable` zmiennej w wierszu polecenia programu Windows PowerShell.

```powershell
PS C:\> $PSVersionTable.PSVersion

Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

Wszystko jest gotowe do użycia JEA, jeśli *głównych* wersja jest równa lub większa niż **5**.
Aby uzyskać najlepsze wyniki, a dostęp do najnowszych funkcji, zaleca się uaktualnienie do wersji programu PowerShell **5.1** Jeśli to możliwe.

### <a name="install-windows-management-framework"></a>Zainstaluj oprogramowanie Windows Management Framework

Jeśli używasz starszej wersji programu PowerShell, należy zaktualizować system z najnowszą aktualizacją Windows Management Framework (WMF).
Pakiety aktualizacji i łącze do najnowszej wersji platformy WMF są dostępne w [Centrum pobierania](https://aka.ms/WMF5).

Zdecydowanie zaleca się przetestowanie Twoje obciążenie zgodność z WMF przed uaktualnieniem wszystkich serwerów.

Użytkownicy systemu Windows 10 należy zainstalować najnowsze aktualizacje funkcji, aby uzyskać bieżącą wersję środowiska Windows PowerShell.

## <a name="enable-powershell-remoting"></a>Włącz obsługę zdalną środowiska PowerShell

Obsługę zdalną środowiska PowerShell stanowi podstawę, na którym jest oparty JEA.
W związku z tym jest to niezbędne do zapewnienia komunikacji zdalnej programu PowerShell jest włączona i [zabezpieczenie](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity) w systemie, zanim będzie możliwe użycie JEA.

Usługi zdalne środowiska PowerShell jest włączona domyślnie w systemie Windows Server 2012 i 2012 R2, 2016.
Można włączyć obsługę zdalną środowiska PowerShell, uruchamiając następujące polecenie w oknie programu PowerShell z podwyższonym poziomem uprawnień.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>Włączanie rejestrowania bloku skryptu (opcjonalnie) i moduł programu PowerShell

Poniższe kroki należy włączyć rejestrowanie dla wszystkich działań programu PowerShell w systemie.
Rejestrowanie modułu programu PowerShell nie jest wymagane dla JEA, jednak zalecane jest włączenie go w celu upewnij się, że użytkownicy poleceń uruchom są rejestrowane w centralnej lokalizacji.

Można skonfigurować za pomocą zasad grupy zasady logowania modułu programu PowerShell.

1. Otwórz Edytor lokalnych zasad grupy na stacji roboczej lub obiektu zasad grupy w konsoli zarządzania zasadami grupy na kontrolerze domeny usługi Active Directory
2. Przejdź do **Konfiguracja komputera\\Szablony administracyjne\\składniki systemu Windows\\środowiska Windows PowerShell**
3. Kliknij dwukrotnie **Włącz rejestrowanie modułu**
4. Kliknij przycisk **włączone**
5. W sekcji Opcje, kliknij polecenie **Pokaż** obok nazwy modułu
6. Typ "**\***" w wyświetlonym oknie. To powoduje, że programu PowerShell do rejestrowania poleceń ze wszystkich modułów.
7. Kliknij przycisk **OK** ustawić zasad
8. Kliknij dwukrotnie **Włącz rejestrowanie bloku skryptu PowerShell**
9. Kliknij przycisk **włączone**
10. Kliknij przycisk **OK** ustawić zasad
11. (Maszynach przyłączonych do domeny jedynie) Uruchom **gpupdate** lub zaczekaj na mają zostać zaktualizowane zasady przetwarzania i stosować ustawienia zasad grupy

Można również włączyć przekształcania PowerShell całego systemu za pomocą zasad grupy.

## <a name="next-steps"></a>Następne kroki

- [Utwórz plik możliwości roli](role-capabilities.md)
- [Utwórz plik konfiguracji sesji](session-configurations.md)

## <a name="see-also"></a>Zobacz też

- [Dodatkowe informacje o zabezpieczeniach usługi zdalne środowiska PowerShell i usługi WinRM](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity)
- [*PowerShell ♥ niebieski zespołu* wpis w blogu dotyczące zabezpieczeń](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)

