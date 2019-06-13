---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Jak używać profilów w środowisku Windows PowerShell ISE
ms.openlocfilehash: 28354f39aaaa577cec69c1b3f62cfe16ef091218
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030601"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a>Jak używać profilów w środowisku Windows PowerShell ISE

W tym temacie wyjaśniono, jak używać profilów w Windows PowerShell® zintegrowane Scripting Environment (ISE). Zaleca się, że przed przystąpieniem do wykonywania zadań w tej sekcji, możesz przejrzeć [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), lub w okienku konsoli typu `Get-Help about_Profiles` i naciśnij klawisz **ENTER**.

Profil jest skrypt programu Windows PowerShell ISE, który jest uruchamiany automatycznie po uruchomieniu nowej sesji.  Można utworzyć co najmniej jeden profil programu Windows PowerShell dla programu Windows PowerShell ISE i ich używać do dodawania Konfigurowanie środowiska programu Windows PowerShell lub programu Windows PowerShell ISE przygotowania go do swojego użytku, za pomocą zmiennych, aliasy, funkcje i kolorów i czcionek Preferencje, które mają być dostępne. Profil, który ma wpływ na każdą sesję środowiska Windows PowerShell ISE, rozpoczęcie.

> [!NOTE]
> Zasady wykonywania programu Windows PowerShell Określa, czy można uruchamiać skrypty i Załaduj profil. Domyślne zasady wykonywania "Restricted" uniemożliwia wszystkie skrypty uruchamiania, w tym profile. Jeśli używasz zasad "Restricted", nie można załadować profilu. Aby uzyskać więcej informacji na temat zasad wykonywania, zobacz [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a>Wybieranie profilu do użycia w środowisku Windows PowerShell ISE

Windows PowerShell ISE obsługuje profile dla bieżącego użytkownika i dla wszystkich użytkowników. Obsługuje ona również Profile programu Windows PowerShell, które są stosowane do wszystkich hostów.

Profil, którego używasz zależy od sposobu korzystania z programu Windows PowerShell i Windows PowerShell ISE.

- Jeśli używasz tylko Windows PowerShell ISE, aby uruchomić program Windows PowerShell, Zapisz wszystkie elementy w jeden z profilów specyficzne dla środowiska ISE, takich jak profilu CurrentUserCurrentHost w środowisku Windows PowerShell ISE lub AllUsersCurrentHost dla środowiska Windows PowerShell ISE.

- Jeśli używasz wielu programów hosta do uruchamiania środowiska Windows PowerShell, Zapisz funkcje, aliasy, zmienne i poleceń w profilu, który ma wpływ na wszystkie programy hosta, takie jak CurrentUserAllHosts lub AllUsersAllHosts, a następnie zapisz funkcjami specyficznymi dla środowiska ISE, takich jak kolory i czcionki dostosowania w profilu CurrentUserCurrentHost dla środowiska Windows PowerShell ISE profilu lub AllUsersCurrentHost dla środowiska Windows PowerShell ISE.

Dostępne są następujące profile, które mogą być tworzone i używane w środowisku Windows PowerShell ISE. Każdy profil są zapisywane w jego własnej określonej ścieżki.

| Typ profilu | Ścieżka profilu |
| --- | --- |
| **Bieżący użytkownik, program PowerShell ISE**| `$PROFILE.CurrentUserCurrentHost`, lub `$PROFILE` |
| **Wszyscy użytkownicy, program PowerShell ISE**| `$PROFILE.AllUsersCurrentHost` |
| **Bieżący użytkownik, wszystkie hosty**| `$PROFILE.CurrentUserAllHosts` |
| **Wszyscy użytkownicy, wszystkie hosty** | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a>Aby utworzyć nowy profil

Aby utworzyć nowe "bieżącego użytkownika, środowiska Windows PowerShell ISE" profilu, uruchom następujące polecenie:

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

Aby utworzyć nowy "Wszyscy użytkownicy, środowiska Windows PowerShell ISE" profilu, uruchom następujące polecenie:

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

Aby utworzyć nowy profil "bieżącego użytkownika, wszystkie hosty", uruchom następujące polecenie:

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

Aby utworzyć nowy profil "wszystkich użytkowników i wszystkie hosty", wpisz:

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a>Aby dokonać edycji profilu

1. Aby otworzyć profil, należy uruchomić psedit polecenia ze zmienną, która określa profil, który chcesz edytować. Na przykład, aby otworzyć "bieżącego użytkownika, środowiska Windows PowerShell ISE" profilu, wpisz: `psEdit $PROFILE`

2. Dodaj kilka elementów do Twojego profilu. Poniżej przedstawiono kilka przykładów, które ułatwią Ci rozpoczęcie pracy:

   - Aby zmienić domyślny kolor tła w okienku konsoli na niebieski w typ pliku profilu: `$psISE.Options.OutputPaneBackground = 'blue'` . Aby uzyskać więcej informacji na temat zmiennej $psISE zobacz [dokumentacja modelu obiektów programu Windows PowerShell ISE](object-model/The-ISE-Object-Model-Hierarchy.md).

   - Aby zmienić rozmiar czcionki do 20 plików typu profilu: `$psISE.Options.FontSize =20`

3. Można zapisać w pliku profilu, **pliku** menu, kliknij przycisk **Zapisz**. Gdy następnym razem otworzysz środowiska Windows PowerShell ISE dostosowania są stosowane.

## <a name="see-also"></a>Zobacz też

- [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [Wprowadzenie do programu Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
