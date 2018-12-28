---
ms.date: 08/27/2018
keywords: polecenia cmdlet programu PowerShell
title: Używanie znanych nazw poleceń
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: c5665f64fd832eb9c807f413a8e879f63db7f8c6
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405603"
---
# <a name="using-familiar-command-names"></a>Używanie znanych nazw poleceń

Program PowerShell obsługuje aliasów do odwoływania się do polecenia przy użyciu alternatywnych nazw. Tworzenie aliasów umożliwia użytkownikom ze środowiskiem, w innych powłoki, aby używać typowych nazw poleceń, które już znasz dla podobnych działań w programie PowerShell.

Aliasów kojarzy nazwę przy użyciu innego polecenia. Na przykład programu PowerShell ma funkcji o nazwie wewnętrznej `Clear-Host` , czyści okno danych wyjściowych. Można wpisać `cls` lub `clear` aliasu w wierszu polecenia. Program PowerShell interpretuje te aliasy i uruchamia `Clear-Host` funkcji.

Ta funkcja pozwala użytkownikom, aby dowiedzieć się, programu PowerShell. Po pierwsze większość **cmd.exe** i dużych dostępnych poleceń, które użytkownicy znanych według nazwy użytkowników systemu Unix. Odpowiedniki w programie PowerShell nie może utworzyć takie same wyniki. Wyniki są jednak Zamknij wystarczająco dużo, które użytkownicy mogą działać bez znajomości nazwa polecenia programu PowerShell. "Finger pamięci" jest inny główne źródło Rozczarowanie podczas nauki nowych powłoki poleceń. Jeśli używano **cmd.exe** przez wiele lat, możesz reflexively wpisać `cls` polecenie, aby wyczyścić ekran. Bez alias `Clear-Host`, otrzymujesz komunikat o błędzie i nie będą wiedzieli, co należy zrobić, aby wyczyścić dane wyjściowe.

Na poniższej liście przedstawiono niektóre typowe **cmd.exe** i polecenia systemu Unix, których można użyć w programie PowerShell:

|||||
|-|-|-|-|
|CAT|dir|instalacji|Menedżer zasobów|
|ciągłe dostarczanie|Echo|Przenieś|rmdir|
|chdir|Wymazywanie|popd|stan uśpienia|
|Usuń zaznaczenie|GODZ.|PS|Sortowanie|
|ze specyfikacją CLS|Historia|pushd|Program Tee|
|Kopiuj|Zakończ|pwd|typ|
|del|LP|r|zapis|
|diff|Ls|ren||

`Get-Alias` Polecenie cmdlet Pokazuje rzeczywistą nazwą polecenia programu PowerShell natywnych skojarzonych z aliasem.

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a>Interpretowanie standardowa aliasów

Aliasy możemy opisanego w poprzedniej zostały zaprojektowane dla nazwy — zgodność z innymi powłoki poleceń.
Większość aliasów utworzone w programie PowerShell są przeznaczone do skrócenia programu. Krótsze nazwy są łatwiejsze do typu, ale są trudne do odczytania, jeśli nie znasz odwołują się.

Aliasy środowiska PowerShell próbować naruszyć między przejrzystości i skrócenia programu. PowerShell używa standardowy zestaw aliasy rzeczowniki typowe i zleceń.

Przykład skrótów:

| Rzeczownik lub zlecenie | Skrót |
|--------------|--------------|
| Pobranie          | G            |
| Ustaw          | s            |
| Element         | i            |
| Lokalizacja     | l            |
| Polecenie      | Menedżer certyfikatów           |
| Alias        | Al           |

Te aliasy są zrozumiałe, gdy wiadomo, skrócone nazwy.

| Nazwa polecenia cmdlet    | Alias |
|----------------|-------|
| `Get-Item `    | GI    |
| `Set-Item`     | SI    |
| `Get-Location` | GL    |
| `Set-Location` | SL    |
| `Get-Command`  | usługi gcm   |
| `Get-Alias`    | GAL   |

Po zapoznaniu się z programu PowerShell aliasów się, jest łatwe do odgadnięcia, **sal** alias odwołuje się do `Set-Alias`.

## <a name="creating-new-aliases"></a>Tworzenie nowego aliasów

Możesz utworzyć własne aliasy, za pomocą `Set-Alias` polecenia cmdlet. Na przykład poniższe instrukcje tworzenia aliasów standardowe polecenia cmdlet omówionych wcześniej:

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

Wewnętrznie programu PowerShell używa podobnych poleceń podczas uruchamiania, ale te aliasy nie są zmieniane.
Jeśli spróbujesz wykonać jedną z tych poleceń, otrzymasz błąd z informacją, że alias nie może być modyfikowany. Przykład:

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```