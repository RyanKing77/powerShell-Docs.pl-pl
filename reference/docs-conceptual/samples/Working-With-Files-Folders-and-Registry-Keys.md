---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Praca z folderami plików i kluczami rejestru
ms.openlocfilehash: 0c8716c384827d0816e2847ff81232c14638681b
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030762"
---
# <a name="working-with-files-folders-and-registry-keys"></a>Praca z plików, folderów i kluczy rejestru

Windows PowerShell korzysta z rzeczownikiem **elementu** do odwoływania się do elementów na dysk programu Windows PowerShell. Podczas pracy z dostawcą programu Windows PowerShell w systemie plików **elementu** może być pliku, folderu lub dysk programu Windows PowerShell. Lista i Praca z tych elementów jest krytyczne podstawowe zadania w większości ustawień administracyjnych, chcemy omówiono te zadania szczegółowo.

## <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a>Wyliczanie plików, folderów i kluczy rejestru (Get-ChildItem)

Ponieważ kolekcja elementów z określonej lokalizacji jest takiego typowe zadania, **Get-ChildItem** polecenia cmdlet jest zaprojektowany specjalnie w celu zwrócenie wszystkich elementów, które można znaleźć w kontenerze, takie jak folder.

Jeśli chcesz przywrócić wszystkie pliki i foldery, które znajdują się bezpośrednio z poziomu folderu C:\\Windows, wpisz:

```
PS> Get-ChildItem -Path C:\Windows
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-16   8:10 AM          0 0.log
-a---        2005-11-29   3:16 PM         97 acc1.txt
-a---        2005-10-23  11:21 PM       3848 actsetup.log
...
```

Listę wygląda podobnie do widoczne po wprowadzeniu **dir** polecenia w pliku **Cmd.exe**, lub **ls** polecenie w powłoce poleceń systemu UNIX.

Bardzo złożone oferty można wykonać przy użyciu parametrów **Get-ChildItem** polecenia cmdlet. Przyjrzymy się kilka scenariuszy dalej. Można zapoznać się ze składnią **Get-ChildItem** polecenia cmdlet, wpisując:

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

Te parametry można mieszać i dopasowane do uzyskania dopasowanego wyjściowych.

### <a name="listing-all-contained-items--recurse"></a>Wyświetlanie wszystkich elementów znajdujących się (-Recurse)

Aby wyświetlić elementy znajdujące się w folderze Windows i wszystkie elementy, które są zawarte w podfolderach, użyj **Recurse** parametru **Get-ChildItem**. Listę Wyświetla wszystkie elementy w folderze Windows i elementy w jego podfolderach. Przykład:

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

### <a name="filtering-items-by-name--name"></a>Filtrując elementy według nazwy (-nazwa)

Aby wyświetlić tylko nazwy elementów, użyj **nazwa** parametru **Get-Childitem**:

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

### <a name="forcibly-listing-hidden-items--force"></a>Wymuś wyświetlanie ukrytych elementów (-Force)

Elementy, które są zwykle niewidoczne w Eksploratorze plików lub Cmd.exe nie są wyświetlane w danych wyjściowych **Get-ChildItem** polecenia. Aby wyświetlić ukryte elementy, użyj **życie** parametru **Get-ChildItem**. Przykład:

```powershell
Get-ChildItem -Path C:\Windows -Force
```

Ten parametr nosi życie, ponieważ wymuszono można zastąpić normalnego zachowania **Get-ChildItem** polecenia. Wymuś jest powszechnie używany parametr, który wymusza akcję, która nie wykona zazwyczaj polecenia cmdlet, mimo że nie będzie wykonywać żadnych działań, które obniża zabezpieczeń systemu.

### <a name="matching-item-names-with-wildcards"></a>Zgodne z nazwami elementów z symbolami wieloznacznymi

**Polecenie Get-ChildItem** polecenie akceptuje symbole wieloznaczne w ścieżce elementy do listy.

Ponieważ dopasowanie z symbolami wieloznacznymi jest obsługiwany przez aparatu programu Windows PowerShell, wszystkie polecenia cmdlet, które akceptuje symbole wieloznaczne Użyj takiej samej notacji i ma takie samo zachowanie pasujące. Obejmuje notacji symbolu wieloznacznego programu Windows PowerShell:

- Gwiazdka (\*) dopasowuje zero lub więcej wystąpień dowolnego znaku.

- Znak zapytania (?) dopasowuje dokładnie jeden znak.

- Lewy nawias kwadratowy (\[) znaków prawego nawiasu (]) i otoczyć zestaw znaków, które mają zostać dopasowane.

Poniżej przedstawiono kilka przykładów sposobu działania Specyfikacja symboli wieloznacznych.

Aby znaleźć wszystkie pliki w katalogu Windows wraz z sufiksem **.log** i dokładnie pięć znaków w nazwie podstawowej, wprowadź następujące polecenie:

```
PS> Get-ChildItem -Path C:\Windows\?????.log

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
...
-a---        2006-05-11   6:31 PM     204276 ocgen.log
-a---        2006-05-11   6:31 PM      22365 ocmsn.log
...
-a---        2005-11-11   4:55 AM         64 setup.log
-a---        2005-12-15   2:24 PM      17719 VxSDM.log
...
```

Aby znaleźć wszystkie pliki, które zaczynają się od litery **x** w katalogu Windows, wpisz:

```powershell
Get-ChildItem -Path C:\Windows\x*
```

Aby znaleźć wszystkie pliki, których nazwy zaczynają się od **x** lub **z**, wpisz:

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

### <a name="excluding-items--exclude"></a>Wykluczanie elementów (— wyklucz)

Można wykluczyć konkretne elementy za pomocą **wykluczyć** parametr Get-ChildItem. Dzięki temu można wykonywać złożone filtrowanie w pojedynczej instrukcji.

Na przykład załóżmy, że próbujesz odnaleźć biblioteki DLL Windows czasu usługi w folderze System32, a wszystko, czego należy pamiętać, o nazwie biblioteki DLL jest zaczyna się od "W" i zawiera "32".

Wyrażenie, takie jak **w\&#42; 32\&#42;. Biblioteka DLL** znajdzie wszystkie biblioteki dll, które spełniają warunki, ale może również zwrócić Windows 95 i zgodności Windows 16-bitowych bibliotek DLL, które zawierają "95" lub "16" w nazwach. Możesz pominąć pliki, które nie ma żadnej z tych liczb w nazwach przy użyciu **wykluczyć** parametru za pomocą wzorca  **\&#42;\[ 9516]\&#42;** :

```
PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude *[9516]*

Directory: Microsoft.PowerShell.Core\FileSystem::C:\WINDOWS\System32
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     174592 w32time.dll
-a---        2004-08-04   8:00 AM      22016 w32topl.dll
-a---        2004-08-04   8:00 AM     101888 win32spl.dll
-a---        2004-08-04   8:00 AM     172032 wldap32.dll
-a---        2004-08-04   8:00 AM     264192 wow32.dll
-a---        2004-08-04   8:00 AM      82944 ws2_32.dll
-a---        2004-08-04   8:00 AM      42496 wsnmp32.dll
-a---        2004-08-04   8:00 AM      22528 wsock32.dll
-a---        2004-08-04   8:00 AM      18432 wtsapi32.dll
```

### <a name="mixing-get-childitem-parameters"></a>Mieszanie polecenie Get-ChildItem parametrów

Można użyć kilku parametrów **Get-ChildItem** polecenia cmdlet w tym samym poleceniu. Zanim mieszać parametrów, upewnij się, że rozumiesz dopasowanie z symbolami wieloznacznymi. Na przykład poniższe polecenie zwraca żadnych wyników:

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

Brak wyników, mimo że istnieją dwa pliki dll, które zaczynają się od litery "z" w folderze Windows.

Ponieważ firma Microsoft określona jako część ścieżki symbolu wieloznacznego nie zwrócono żadnych wyników. Mimo że polecenie zostało rekursywny, **Get-ChildItem** polecenia cmdlet z ograniczeniami elementy do tych, które znajdują się w folderze Windows za pomocą nazwy kończące się ciągiem ".dll".

Aby określić wyszukiwania rekurencyjne dla plików, których nazwy odpowiadają wzorcowi specjalne, należy użyć **— obejmują** parametru.

```
PS> Get-ChildItem -Path C:\Windows -Include *.dll -Recurse -Exclude [a-y]*.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32\Setup

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM       8261 zoneoc.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     337920 zipfldr.dll
```
