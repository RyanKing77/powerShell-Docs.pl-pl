---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Sposobu używania profilów w środowisku Windows PowerShell ISE"
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
ms.openlocfilehash: f959aeb91eecc8056c91c56162ea9bff53537be9
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a>Sposobu używania profilów w środowisku Windows PowerShell ISE
W tym temacie wyjaśniono, jak używać profili w Windows PowerShell® Integrated Scripting Environment (ISE). Firma Microsoft zaleca się przed wykonaniem zadań w tej sekcji, przejrzenie [about_Profiles [4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630)), lub w okienku konsoli typu `Get-Help about_Profiles` i naciśnij klawisz **ENTER**.

Profil jest skrypt programu Windows PowerShell ISE, który jest uruchamiany automatycznie podczas uruchamiania nowej sesji.  Można utworzyć co najmniej jeden profil programu Windows PowerShell dla programu Windows PowerShell ISE i używać ich do dodawania konfiguracji środowiska Windows PowerShell lub programu Windows PowerShell ISE przygotowania go do użycia, zmienne, aliasy, funkcje i kolorów i czcionek Preferencje, które mają być dostępne. Profil ma wpływ na każdej sesji programu Windows PowerShell ISE, który można uruchomić.

> [!NOTE]
> Zasady wykonywania programu Windows PowerShell Określa, czy można uruchamiać skrypty i ładowanie profilu. Domyślne zasady wykonywania "Restricted" uniemożliwia wszystkie skrypty uruchomiona, w tym profili. Jeśli używasz zasad "Restricted", nie można załadować profilu. Aby uzyskać więcej informacji na temat zasad wykonywania, zobacz [about_Execution_Policies [4]](https://technet.microsoft.com/library/347708dc-1515-4d74-978b-8334603472e6(v=wps.630)).

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a>Wybieranie profilu do programu Windows PowerShell ISE
Windows PowerShell ISE obsługuje profile dla bieżącego użytkownika i dla wszystkich użytkowników. Obsługuje ona również Profile programu Windows PowerShell, które są stosowane do wszystkich hostów.

Profil, którego używasz, jest określana przez sposobie korzystania z programu Windows PowerShell i Windows PowerShell ISE.

- Jeśli używasz tylko programu Windows PowerShell ISE uruchamianie środowiska Windows PowerShell, Zapisz wszystkie elementy w jeden z profilów specyficzne dla platformy ISE, takich jak profilu CurrentUserCurrentHost dla programu Windows PowerShell ISE lub AllUsersCurrentHost dla programu Windows PowerShell ISE.

- Użycie wielu hostowanie programów do uruchomienia programu Windows PowerShell, Zapisz funkcje, aliasy, zmienne i polecenia w profilu, który ma wpływ na wszystkie programy hosta, takich jak CurrentUserAllHosts lub AllUsersAllHosts i zapisać funkcji specyficznych dla platformy ISE, takich jak kolorów i czcionek dostosowania w profilu CurrentUserCurrentHost dla programu Windows PowerShell ISE profilu lub AllUsersCurrentHost dla programu Windows PowerShell ISE.

Poniżej przedstawiono profilów, które mogą być tworzone i używane w środowisku Windows PowerShell ISE. Każdy profil jest zapisywany w jego własnej określonej ścieżki.

| Typ profilu | Ścieżka profilu |
| --- | --- |
| **Bieżący użytkownik, PowerShell ISE**| `$PROFILE.CurrentUserCurrentHost`, lub`$PROFILE` |
| **Wszyscy użytkownicy, PowerShell ISE**| `$PROFILE.AllUsersCurrentHost` |
| **Bieżący użytkownik, wszystkie hosty**| `$PROFILE.CurrentUserAllHosts` |
| **Wszyscy użytkownicy, wszystkie hosty** | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a>Aby utworzyć nowy profil
Aby utworzyć nowe "bieżącego użytkownika, programu Windows PowerShell ISE" profil, uruchom to polecenie:

```powershell
if (!(Test-Path -Path $PROFILE )) 
{ New-Item -Type File -Path $PROFILE -Force }
```

Aby utworzyć nową "Wszyscy użytkownicy, programu Windows PowerShell ISE" profil, uruchom to polecenie:

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost)) 
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

Aby utworzyć nowy profil "bieżącego użytkownika, wszystkie hosty", uruchom następujące polecenie:

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts)) 
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

Aby utworzyć nowy profil "wszyscy użytkownicy, wszystkie hosty", wpisz:

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts)) 
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a>Aby edytować profilu

1. Aby otworzyć profilu, uruchom psedit polecenia ze zmienną, która określa profil, który chcesz edytować. Na przykład, aby otworzyć "bieżącego użytkownika, programu Windows PowerShell ISE" profilu, wpisz:`psEdit $PROFILE`

2. Niektóre elementy należy dodać do profilu. Poniżej przedstawiono kilka przykładów ułatwiających rozpoczęcie pracy:

    -   Aby zmienić domyślny kolor tła okienka konsoli na niebieski w typ pliku profilu: `$psISE.Options.OutputPaneBackground = 'blue'` . Aby uzyskać więcej informacji na temat zmiennej $psISE, zobacz [odwołanie modelu obiektu Windows PowerShell ISE](The-ISE-Object-Model-Hierarchy.md).

    -   Aby zmienić rozmiar czcionki do 20 w profilu typ pliku:`$psISE.Options.FontSize =20`

3. Aby zapisać plik profilu na **pliku** menu, kliknij przycisk **zapisać**. Następnym otwarciu programu Windows PowerShell ISE dostosowania są stosowane.

## <a name="see-also"></a>Zobacz też
- [about_Profiles [4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630))
- [Przy użyciu programu Windows PowerShell ISE](Using-the-Windows-PowerShell-ISE.md)

