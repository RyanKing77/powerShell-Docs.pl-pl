---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Praca z folderami plików i kluczami rejestru
ms.assetid: e6cf87aa-b5f8-48d5-a75a-7cb7ecb482dc
ms.openlocfilehash: a09b127d4ba37d33cb4c0f0ce0819e645fd4b137
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952311"
---
# <a name="working-with-files-folders-and-registry-keys"></a>Praca z plików, folderów i kluczy rejestru

Program Windows PowerShell korzysta rzeczownikiem **elementu** do odwoływania się do elementów na dysk programu Windows PowerShell. Podczas pracy z dostawcą programu Windows PowerShell w systemie plików **elementu** może być pliku, folderu lub dysk programu Windows PowerShell. Wyświetlanie i Praca z tych elementów jest krytyczne zadanie podstawowe w większość ustawień administracyjnych, więc chcemy tych zadań szczegółowo omówiono w nim.

### <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a>Wyliczanie plików, folderów i kluczy rejestru (Get-ChildItem)

Ponieważ pobierania kolekcję elementów z określonej lokalizacji jest takie typowe zadania, **Get-ChildItem** polecenia cmdlet zaprojektowane z myślą o zwraca wszystkie elementy znalezione w kontenerze, takie jak folder.

Jeśli chcesz przywrócić wszystkie pliki i foldery, które znajdują się bezpośrednio w folderze C:\\systemu Windows, wpisz:

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

Listę wygląda podobnie do będzie widoczna po wprowadzeniu **dir** w **Cmd.exe**, lub **ls** polecenie w powłoce poleceń systemu UNIX.

Listy bardzo skomplikowane, można wykonać przy użyciu parametrów **Get-ChildItem** polecenia cmdlet. Przedstawiono kilka scenariuszy dalej. Można sprawdzić składnię **Get-ChildItem** polecenia cmdlet, wpisując:

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

Te parametry można mieszany i dopasować do pobrania danych wyjściowych wysoce dostosowane.

#### <a name="listing-all-contained-items--recurse"></a>Wyświetlanie wszystkich elementów zawartych (-Recurse)

Aby wyświetlić elementów znajduje się w folderze systemu Windows i wszystkie elementy, które są zawarte w podfolderach, użyj **Recurse** parametr **Get-ChildItem**. Listę Wyświetla wszystkie elementy w folderze systemu Windows i elementów w jego podfolderach. Przykład:

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

#### <a name="filtering-items-by-name--name"></a>Filtrowanie elementów według nazwy (-Name)

Aby wyświetlić tylko nazwy elementów, użyj **nazwa** parametr **Get-Childitem**:

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

#### <a name="forcibly-listing-hidden-items--force"></a>Wymuś wyświetlanie ukrytych elementów (-Force)

Elementy, które nie są zwykle widoczne w Eksploratorze plików lub Cmd.exe nie są wyświetlane w danych wyjściowych **Get-ChildItem** polecenia. Aby wyświetlić ukryte elementy, użyj **życie** parametr **Get-ChildItem**. Przykład:

```powershell
Get-ChildItem -Path C:\Windows -Force
```

Ten parametr jest o nazwie Force, ponieważ wymuszanie można zastąpić normalne zachowanie **Get-ChildItem** polecenia. Wymuś jest powszechnie używany parametr, który wymusza akcję, która zwykle nie może wykonać polecenia cmdlet, mimo że nie będzie wykonywać żadnych czynności, które obniża zabezpieczeń systemu.

#### <a name="matching-item-names-with-wildcards"></a>Zgodne z nazwami elementów z symbolami wieloznacznymi

**Get-ChildItem** polecenie akceptuje symbole wieloznaczne w ścieżce elementów do listy.

Ponieważ wieloznacznych jest obsługiwany przez aparat programu Windows PowerShell, wszystkie polecenia cmdlet, które akceptuje symboli wieloznacznych używają tego samego notacji i ma takie samo zachowanie dopasowania. Obejmuje notacji symbolu wieloznacznego środowiska Windows PowerShell:

- Znak gwiazdki (\*) dopasowuje dowolny znak zero lub więcej wystąpień.

- Znak zapytania (?) odpowiada dokładnie jeden znak.

- Lewy nawias (\[) znaków i znak prawego nawiasu (]) otaczające zestaw znaków do dopasowania.

Oto kilka przykładów działania Specyfikacja symboli wieloznacznych.

Aby znaleźć wszystkie pliki w katalogu systemu Windows wraz z sufiksem **log** i dokładnie pięć znaków w nazwie podstawowej, wprowadź następujące polecenie:

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

Aby znaleźć wszystkie pliki, które zaczynają się od litery **x** w katalogu systemu Windows, wpisz:

```powershell
Get-ChildItem -Path C:\Windows\x*
```

Aby znaleźć wszystkie pliki, których nazwy zaczynają się od **x** lub **z**, wpisz:

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

#### <a name="excluding-items--exclude"></a>Wykluczanie elementów (— wyklucz)

Można wykluczyć określone elementy za pomocą **wykluczyć** parametr Get-ChildItem. Dzięki temu można wykonywać złożonych filtrowanie w jednej instrukcji.

Na przykład załóżmy, że próbujesz odnaleźć biblioteki DLL usługi Czas systemu Windows w folderze System32, a wszystko, co może zapamiętać o nazwę biblioteki DLL jest zaczyna się od litery "W" i ma w nim "32".

Wyrażenie, takich jak **w\&#42; 32\&#42;. biblioteki dll** znajdziesz wszystkie biblioteki dll, które spełniają warunki, ale może również zwrócić Windows 95 i zgodności z systemem Windows 16-bitowych bibliotek DLL, które obejmują "95" lub "16" w ich nazwy. W przypadku pominięcia pliki, które nie ma żadnej z tych numerów w nazwach przy użyciu **wykluczyć** parametru za pomocą wzorca  **\&#42;\[ 9516]\&#42;**:

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

#### <a name="mixing-get-childitem-parameters"></a>Mieszanie Get-ChildItem parametrów

Można użyć kilku parametrów **Get-ChildItem** polecenia cmdlet w tym samym poleceniu. Przed mieszać parametrów, upewnij się, że rozumiesz wieloznacznych. Na przykład poniższe polecenie zwraca nie zwróciło żadnych wyników:

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

Nie ma żadnych wyników, nawet jeśli istnieją dwa pliki dll, które zaczynają się od litery "z" w folderze systemu Windows.

Ponieważ firma Microsoft określony jako część ścieżki symbolu wieloznacznego nie zwrócono żadnych wyników. Mimo że polecenie to cykliczne, **Get-ChildItem** polecenia cmdlet ograniczone elementy do tych, które znajdują się w folderze systemu Windows z nazwami kończą się ciągiem "dll".

Aby określić cykliczne wyszukiwanie plików, których nazwy zgodne ze wzorcem specjalne, użyj **-obejmują** parametru.

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