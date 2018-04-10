---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Używanie zmiennych na potrzeby przechowywania obiektów
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: e52f0a344d0ad13db42b34bed912d584c99b0e30
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="using-variables-to-store-objects"></a>Używanie zmiennych na potrzeby przechowywania obiektów
PowerShell współpracuje z obiektami. PowerShell umożliwia tworzenie zmiennych zasadniczo o nazwie obiektów, aby zachować dane wyjściowe do późniejszego użycia. Jeśli są używane do pracy z zmiennych w innych powłok należy pamiętać, że zmienne środowiska PowerShell obiektów, nie tekstu.

Zmienne zawsze są określane za pomocą $ litery i może zawierać dowolne znaki alfanumeryczne lub podkreślenie w nazwach.

### <a name="creating-a-variable"></a>Tworzenie zmiennej
Można utworzyć zmiennej, wpisz prawidłową nazwę zmiennej:

```
PS> $loc
PS>
```

Zwraca żadnego wyniku, ponieważ **$loc** nie ma wartości. Można utworzyć zmienną i przypisz mu wartość w tym samym kroku. PowerShell tylko tworzy zmiennej, jeśli nie istnieją; w przeciwnym razie przypisuje określona wartość istniejącej zmiennej. Do przechowywania bieżącej lokalizacji w zmiennej **$loc**, wpisz:

```
$loc = Get-Location
```

Brak żadnych danych wyjściowych wyświetlane po wpisaniu tego polecenia, ponieważ dane wyjściowe są wysyłane do $loc. W programie PowerShell wyświetlanych wyników jest efektem ubocznym fakt, że dane, który nie jest w przeciwnym razie skierowany, zawsze są wysyłane do ekranu. Wpisywanie $loc wyświetli bieżącej lokalizacji:

```
PS> $loc

Path
----
C:\temp
```

Można użyć **elementu członkowskiego Get** do wyświetlania informacji o zawartości zmiennych. Przekazanie w potoku $loc do elementu członkowskiego Get będzie pokazują, że jest **PATHINFO zawiera** obiektu, podobnie jak dane wyjściowe z lokalizacji pobierania:

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### <a name="manipulating-variables"></a>Manipulowanie zmiennych
PowerShell zawiera kilka poleceń do modyfikowania zmiennych. Aby zobaczyć pełną listę w czytelnej postaci, należy wpisać:

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

Oprócz zmiennych tworzonych w bieżącej sesji programu PowerShell istnieje kilka zmienne zdefiniowane w systemie. Można użyć **Remove-Variable** polecenia cmdlet, aby umożliwić wyczyszczenie wszystkich zmiennych, które nie są kontrolowane przez programu PowerShell. Wpisz następujące polecenie, aby wyczyścić wszystkie zmienne:

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

Spowoduje to utworzenie poniższą monit o potwierdzenie.

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

Jeśli następnie uruchom **Get-Variable** polecenia cmdlet, zobaczysz pozostałych zmiennych środowiska PowerShell. Ponieważ jest również zmienną dysku środowiska PowerShell, można także wyświetlić wszystkich zmiennych środowiska PowerShell, wpisując:

```
Get-ChildItem variable:
```

### <a name="using-cmdexe-variables"></a>Korzystając ze zmiennych Cmd.exe
Mimo że programu PowerShell nie jest Cmd.exe, jest uruchamiany w środowisku powłoki poleceń i można używać tego samego zmiennych dostępnych w każdym środowisku w systemie Windows. Te zmienne są dostępne za pośrednictwem dysku o nazwie **env**:. Te zmienne można wyświetlić, wpisując:

```
Get-ChildItem env:
```

Mimo że cmdlet zmiennej standardowe nie są zaprojektowane do pracy z **env:** zmiennych, nadal można je, określając **env:** prefiks. Na przykład, aby wyświetlić katalog główny systemu operacyjnego, można użyć powłoki poleceń **katalogu % SystemRoot %** zmienną z wewnątrz środowiska PowerShell, wpisując:

```
PS> $env:SystemRoot
C:\WINDOWS
```

Można również tworzyć i modyfikować zmiennych środowiskowych z wewnątrz środowiska PowerShell. Zmienne środowiskowe dostępne z programu Windows PowerShell jest zgodna z normalnym reguły dotyczące zmiennych środowiskowych w innym miejscu w systemie Windows.