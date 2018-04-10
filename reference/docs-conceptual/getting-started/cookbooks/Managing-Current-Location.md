---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Zarządzanie bieżącą lokalizacją
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
ms.openlocfilehash: 8d529bf4a85553b95a9cab2739016859662486f2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="managing-current-location"></a>Zarządzanie bieżącą lokalizacją

Przy przechodzeniu systemach folder w Eksploratorze plików, zwykle mają określonej lokalizacji pracy — a mianowicie bieżącego Otwórz folder. Elementy w bieżącym folderze może manipulować łatwo za pomocą kliknięcia. Dla interfejsów wiersza polecenia takich jak Cmd.exe w tym samym folderze co określonego pliku, można do niego dostęp przez określenie stosunkowo krótką nazwę, a nie trzeba określić pełną ścieżkę do pliku. Bieżący katalog nosi nazwę katalogu roboczego.

Program Windows PowerShell korzysta rzeczownikiem **lokalizacji** do odwoływania się do katalogu roboczego i implementuje rodziny poleceń cmdlet do badania i manipulowania Twojej lokalizacji.

### <a name="getting-your-current-location-get-location"></a>Pobieranie bieżącej lokalizacji (Get lokalizacji)

Aby określić ścieżkę bieżącą lokalizację katalogu, wprowadź **lokalizacji Get** polecenia:

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Polecenie cmdlet Get-lokalizacji jest podobny do **pwd** w powłoki BASH. Polecenia cmdlet Set-lokalizacji jest podobny do **cd** w Cmd.exe.

### <a name="setting-your-current-location-set-location"></a>Ustawianie bieżącej lokalizacji (zestaw lokalizacji)

**Lokalizacji Get** z używane jest polecenie **lokalizacją zestawu** polecenia. **Lokalizacją zestawu** polecenia można określić bieżącą lokalizację katalogu.

```powershell
Set-Location -Path C:\Windows
```

Po wprowadzeniu polecenia, można zauważyć, że nie otrzymasz żadnych bezpośrednich swoją opinię na temat efekt polecenia. Większość poleceń programu Windows PowerShell, które wykonują akcję utworzyć żadnych danych wyjściowych, ponieważ dane wyjściowe nie jest zawsze przydatne. Aby sprawdzić, czy katalog pomyślnym nastąpiła zmiana po wprowadzeniu **lokalizacją zestawu** polecenia, obejmują **- PassThru** parametru po wprowadzeniu **Set-lokalizacji**polecenia:

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

**- PassThru** parametru można z wielu zestaw poleceń w programie Windows PowerShell do zwracania informacji dotyczących wynik w przypadkach, w których nie ma żadnych danych wyjściowych domyślnego.

Można określić ścieżki względem bieżącej lokalizacji w taki sam sposób, jak w większości systemu UNIX i systemu Windows będzie można polecenia powłoki. W standardowej notacji dla ścieżek względnych okres (**.**) reprezentuje folder bieżący i podwójna okres (**...** ) reprezentuje katalogu nadrzędnego dla bieżącej lokalizacji.

Na przykład, jeśli są w **C:\\Windows** folderu, kropka (**.**) reprezentuje **C:\\Windows** i dwukrotnie kropki (**...** ) reprezentuje **C:**. Możesz zmienić w bieżącej lokalizacji w katalogu głównym dysku C:, wpisując:

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

Ta sama metoda działa na dyskach środowiska Windows PowerShell, które nie są dyski systemu plików, takich jak **HKLM:**. Możesz ustawić dla Twojej lokalizacji HKLM\\oprogramowania klucz rejestru, wpisując:

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

Następnie można zmienić na lokalizację katalogu do katalogu nadrzędnego, który jest głównym HKLM programu PowerShell systemu Windows: dysku za pomocą ścieżki względnej:

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

Można wpisać lokalizacją zestawu lub użyć dowolnego z wbudowanych aliasy programu Windows PowerShell do lokalizacji zestawu (cd, chdir, sl). Przykład:

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

### <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a>Zapisywanie i odwołująca ostatnie lokalizacje (lokalizacja wypychania i lokalizacji Pop)

W przypadku zmiany lokalizacji, warto śledzić gdy zostały oraz aby można było powrócić do poprzedniej lokalizacji. **Lokalizacji wypychania** polecenia cmdlet programu Windows PowerShell tworzy uporządkowanej historię ("stosu") ścieżek katalogów, w którym nastąpiło i można przejść za pośrednictwem historii ścieżek katalogów przy użyciu uzupełniające  **Lokalizacji POP** polecenia cmdlet.

Na przykład programu Windows PowerShell zazwyczaj rozpoczyna się w katalogu macierzystego użytkownika.

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Wyraz *stosu* ma specjalne znaczenie w wielu ustawień programowania, w tym .NET Framework. Podobnie jak fizyczny stosu elementów ostatni element, który można umieścić na stosie jest pierwszy element, który może pobierać ze stosu. Dodawanie elementu stos potocznie nazywa się "PUSH" element na stosie. Ściąganie elementu ze stosu potocznie nazywa się "wyświetlanie" elementu ze stosu.

Aby wypychanie bieżącej lokalizacji na stosie, a następnie przejdź do folderu Ustawienia lokalne, wpisz:

```powershell
Push-Location -Path "Local Settings"
```

Można następnie Wypchnij lokalizacji lokalnej ustawień na stosie i i przejdź do folderu tymczasowego, wpisując:

```powershell
Push-Location -Path Temp
```

Możesz sprawdzić, zmienić katalogi, wprowadzając **lokalizacji Get** polecenia:

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

Można następnie pop do katalogu ostatnio odwiedzonych przez wprowadzenie **lokalizacji Pop** polecenia i Sprawdź zmiany, wprowadzając **lokalizacji Get** polecenia:

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

Tylko jako z **lokalizacją zestawu** polecenia cmdlet, można dołączyć **- PassThru** parametru po wprowadzeniu **lokalizacji Pop** polecenia cmdlet, aby wyświetlić katalog wprowadzony:

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

Można również używać poleceń cmdlet lokalizacji z ścieżek sieciowych. Jeśli masz serwer o nazwie FS01 z udziałem o nazwie Public, można zmienić lokalizację, wpisując

```powershell
Set-Location \\FS01\Public
```

lub

```powershell
Push-Location \\FS01\Public
```

Można użyć **lokalizacji wypychania** i **lokalizacją zestawu** poleceń, aby zmienić lokalizację do dowolnego dostępnego dysku. Na przykład, jeśli stacja CD-ROM lokalnego z literą dysku D, który zawiera dysk CD z danymi, można zmienić lokalizacji na dysku CD, wprowadzając **D: lokalizacją zestawu** polecenia.

Jeśli dysk jest pusty, otrzymasz następujący komunikat o błędzie:

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

Korzystając z interfejsu wiersza polecenia, nie jest wygodne zbadać dostępne dyski fizyczne za pomocą Eksploratora plików. Ponadto Eksploratora plików czy są wyświetlane wszystkie dyski środowiska Windows PowerShell. Programu Windows PowerShell udostępnia zestaw poleceń do manipulowania dyski środowiska Windows PowerShell, a będzie omawianiu te dalej.