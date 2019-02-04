---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Zarządzanie bieżącą lokalizacją
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
ms.openlocfilehash: d1ebc9507a45841e6d4d8219e45c002990e1328c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686509"
---
# <a name="managing-current-location"></a>Zarządzanie bieżącą lokalizacją

Podczas przechodzenia systemów folder w Eksploratorze plików, zwykle mają konkretną lokalizację pracy — to znaczy, bieżącego polecenia Otwórz folder. Elementy w bieżącym folderze można łatwo manipulować, klikając je. Dla interfejsów wiersza polecenia, takich jak Cmd.exe podczas pracy w tym samym folderze co określonego pliku, możesz do niego dostęp przez określenie stosunkowo krótka nazwa zamiast konieczności określania pełną ścieżkę do pliku. Bieżący katalog nosi nazwę katalogu roboczego.

Windows PowerShell korzysta z rzeczownikiem **lokalizacji** do odwoływania się do katalogu roboczego i implementuje rodzinę poleceń cmdlet do badania i manipulowania Twojej lokalizacji.

### <a name="getting-your-current-location-get-location"></a>Pobieranie bieżącej lokalizacji (Get lokalizacji)

Aby określić ścieżkę swoją bieżącą lokalizację katalogu, wpisz **Get-Location** polecenia:

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Polecenie cmdlet Get-Location jest podobny do **pwd** polecenie w powłoce BASH. Polecenia cmdlet Set-Location jest podobny do **cd** polecenia w pliku Cmd.exe.

### <a name="setting-your-current-location-set-location"></a>Ustawianie bieżącej lokalizacji (zestaw lokalizacji)

**Get-Location** polecenie jest używane z **Ustawianie lokalizacji** polecenia. **Ustawianie lokalizacji** polecenia można określić swoją bieżącą lokalizację katalogu.

```powershell
Set-Location -Path C:\Windows
```

Po wprowadzeniu polecenia, można zauważyć, że nie otrzymasz żadnych informacji zwrotnych o efekt polecenia. Większość poleceń programu Windows PowerShell, którzy wykonują akcję generuje niewielkiego lub żadnego danych wyjściowych, ponieważ dane wyjściowe nie są zawsze przydatne. Aby sprawdzić, czy katalog pomyślne uległo zmianie po wprowadzeniu **Ustawianie lokalizacji** polecenie, podając **- PassThru** parametru po wprowadzeniu **Set-Location**polecenia:

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

**- PassThru** parametru należy używać za pomocą wielu poleceń Set w programie Windows PowerShell do zwracania informacji dotyczących wynik w przypadkach, w których jest nie domyślne dane wyjściowe.

Można określić ścieżki względem Twojej bieżącej lokalizacji w taki sam sposób, jak w większości systemów UNIX i Windows będzie można poleceń powłoki. W standardowej notacji dla ścieżek względnych okres (**.**) reprezentuje bieżącego folderu i podwojone okres (**...** ) reprezentuje katalog nadrzędny Twojej bieżącej lokalizacji.

Na przykład, jeśli znajdują się w **C:\\Windows** folderu, kropka (**.**) reprezentuje **C:\\Windows** i podwojonym współczynnikiem kropki (**...** ) reprezentują **C:**. Możesz zmienić z bieżącej lokalizacji w katalogu głównym dysku C:, wpisując:

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

Ta sama technika działa na dyskach programu Windows PowerShell, które nie są dysków z systemem plików, takich jak **HKLM:**. Można ustawić dla Twojej lokalizacji HKLM\\oprogramowania klucz rejestru, wpisując:

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

Można później zmienić lokalizację katalogu, na katalog nadrzędny, który jest katalogiem głównym Windows PowerShell HKLM: dysk przy użyciu ścieżki względnej:

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

Można wpisać Ustawianie lokalizacji lub użyć dowolnej z wbudowanych aliasy środowiska Windows PowerShell dla lokalizacji zestawu (cd, chdir, sl). Przykład:

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

### <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a>Zapisywanie i ponowne wywoływanie ostatnich lokalizacji (lokalizacja wypychania i lokalizacji Pop)

Zmiana lokalizacji, jest przydatne, aby śledzić, gdy zostały i aby można było powrócić do poprzedniej lokalizacji. **Lokalizacji wypychania** polecenie cmdlet w programie Windows PowerShell tworzy uporządkowane historii ("stos") ścieżek katalogów, w którym nastąpiło i możesz przejść wstecz przez historię ścieżek katalogów przy użyciu uzupełniające  **Lokalizacji POP** polecenia cmdlet.

Na przykład programu Windows PowerShell zazwyczaj rozpoczyna się w katalogu macierzystym użytkownika.

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Wyraz *stosu* ma specjalne znaczenie w wielu ustawień programowania, w tym .NET Framework. Podobnie jak fizyczny stosu elementów ostatni element, które można umieścić na stosie jest pierwszym elementem, którego możesz ściągnąć ze stosu. Dodanie elementu do stosu potocznie jest określany jako "wypychania" element na stosie. Pobieranie elementu ze stosu potocznie jest określany jako "o wyświetlaniu" element ze stosu.

Aby wypychanie bieżącej lokalizacji na stosie, a następnie przejdź do folderu Ustawienia lokalne, wpisz:

```powershell
Push-Location -Path "Local Settings"
```

Możesz następnie Wypychanie do lokalizacji ustawienia lokalne na stosie i przejdź do folderu Temp, wpisując:

```powershell
Push-Location -Path Temp
```

Możesz sprawdzić, czy katalogi zmienione przystępując **Get-Location** polecenia:

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

Możesz następnie pop do ostatnio odwiedzonego katalogu, wprowadzając **lokalizacji Pop** polecenia i sprawdzić zmiany, wprowadzając **Get-Location** polecenia:

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

Podobnie jak **Ustawianie lokalizacji** polecenia cmdlet, można dołączyć **- PassThru** parametru po wprowadzeniu **lokalizacji Pop** polecenia cmdlet, aby wyświetlić katalog, w którym możesz wprowadzić:

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

Można również używać poleceń cmdlet lokalizacji, za pomocą ścieżek sieciowych. Jeśli masz serwer o nazwie FS01 udział o nazwie publiczne, można zmienić lokalizacji, wpisując

```powershell
Set-Location \\FS01\Public
```

lub

```powershell
Push-Location \\FS01\Public
```

Możesz użyć **lokalizacji wypychania** i **Ustawianie lokalizacji** polecenia, aby zmienić lokalizację do dowolnego dostępnego dysku. Na przykład, jeśli masz dysk CD-ROM lokalny z literą dysku D, który zawiera dysk CD z danymi, zmianą lokalizacji na dysku CD, wprowadzając **D: Ustawianie lokalizacji** polecenia.

Jeśli dysk jest pusta, zostanie wyświetlony następujący komunikat o błędzie:

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

Korzystając z interfejsu wiersza polecenia, nie jest wygodne, użyj Eksploratora plików, aby sprawdzić dostępne dyski fizyczne. Ponadto Eksploratora plików będą wyświetlane wszystkie dyski programu Windows PowerShell. Programu Windows PowerShell udostępnia zestaw poleceń do manipulowania dysków programu Windows PowerShell, a następnie zostaną omówione te dalej.
