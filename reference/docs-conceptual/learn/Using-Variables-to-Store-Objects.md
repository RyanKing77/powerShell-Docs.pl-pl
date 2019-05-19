---
ms.date: 08/27/2018
keywords: polecenia cmdlet programu PowerShell
title: Używanie zmiennych na potrzeby przechowywania obiektów
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: 16e82b83df967674da11193c8ac60d637687a01b
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854331"
---
# <a name="using-variables-to-store-objects"></a>Używanie zmiennych na potrzeby przechowywania obiektów

Program PowerShell działa z obiektami. Program PowerShell umożliwia tworzenie nazwane obiekty znane jako zmienne.
Nazwy zmiennych może zawierać znaku podkreślenia i znaków alfanumerycznych. W przypadku użycia w programie PowerShell, zmienna jest zawsze określona za pomocą \$ znak następuje nazwa zmiennej.

## <a name="creating-a-variable"></a>Tworzenie zmiennej

Można utworzyć zmienną, wpisując prawidłową nazwę zmiennej:

```
PS> $loc
PS>
```

W tym przykładzie zwraca żadnego wyniku, ponieważ `$loc` nie ma wartości. Można utworzyć zmienną i przypisać jej wartości w tym samym kroku. Programu PowerShell tworzy zmienną tylko, jeśli nie istnieje.
W przeciwnym razie przypisuje określoną wartość do istniejącej zmiennej. Poniższy przykład zapisuje bieżącej lokalizacji w zmiennej `$loc`:

```powershell
$loc = Get-Location
```

Program PowerShell nie wyświetla danych wyjściowych po wpisaniu tego polecenia. Program PowerShell wysyła dane wyjściowe "Get-Location" `$loc`. W programie PowerShell, który nie jest przypisany lub przekierowanie przesyłane do ekranu. Wpisywanie `$loc` pokazuje bieżącą lokalizację:

```
PS> $loc

Path
----
C:\temp
```

Możesz użyć `Get-Member` do wyświetlania informacji o zawartości zmiennych. `Get-Member` Pokazuje, że `$loc` jest **PATHINFO zawiera** obiektu, podobnie jak dane wyjściowe z `Get-Location`:

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a>Manipulowanie zmiennych

Program PowerShell udostępnia kilka poleceń do manipulowania zmiennych. Aby zobaczyć pełną listę w postaci do odczytu, należy wpisać:

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

Program PowerShell tworzy również kilka zmiennych zdefiniowanych w systemie. Możesz użyć `Remove-Variable` polecenie cmdlet do usuwania zmiennych, które nie są kontrolowane przez program PowerShell z bieżącej sesji. Wpisz następujące polecenie, aby wyczyścić wszystkie zmienne:

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

Po uruchomieniu poprzednie polecenie `Get-Variable` polecenie cmdlet pokazuje zmiennych systemowych programu PowerShell.

Programu PowerShell tworzy dysk zmiennej. Skorzystaj z następującego przykładu, aby wyświetlić wszystkie zmienne programu PowerShell przy użyciu zmiennej dysku:

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a>Używanie zmiennych cmd.exe

Program PowerShell można użyć tego samego zmiennych środowiskowych dostępnych do dowolnego procesu Windows łącznie **cmd.exe**. Te zmienne są udostępniane za pośrednictwem dysku o nazwie `env:`. Te zmienne można wyświetlić, wpisując następujące polecenie:

```powershell
Get-ChildItem env:
```

Standardowa `*-Variable` poleceń cmdlet nie są zaprojektowane do pracy ze zmiennymi środowiskowymi. Zmienne środowiskowe są dostępne przy użyciu `env:` prefiksu dysku. Na przykład **% SystemRoot %** zmienną **cmd.exe** zawiera nazwę katalogu głównego systemu operacyjnego. W programie PowerShell użyj `$env:SystemRoot` dostępu do tej samej wartości.

```
PS> $env:SystemRoot
C:\WINDOWS
```

Można również tworzyć i modyfikować zmiennych środowiskowych z programu PowerShell. Zmienne środowiskowe w programie PowerShell, wykonaj te same zasady stosowania zmienne środowiskowe używane w innym miejscu w systemie operacyjnym. Poniższy przykład tworzy nową zmienną środowiskową:

```powershell
$env:LIB_PATH='/usr/local/lib'
```

Nie jest to wymagane, ale jest typowe dla nazwy zmiennych środowiskowych użyć wielkie litery.
