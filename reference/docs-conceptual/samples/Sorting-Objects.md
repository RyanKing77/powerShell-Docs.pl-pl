---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Sortowanie obiektów
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 06aa15d89888f1ecbe60b8e1dfb4efebb1d73673
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086055"
---
# <a name="sorting-objects"></a>Sortowanie obiektów

Firma Microsoft można organizować wyświetlanych danych, aby ułatwić skanowania za pomocą `Sort-Object` polecenia cmdlet. `Sort-Object` pobiera nazwę jedną lub więcej właściwości, które ma być wykonywane sortowanie i zwraca dane posortowane według wartości tych właściwości.

## <a name="basic-sorting"></a>Sortowanie podstawowe

Należy wziąć pod uwagę ten problem, wyświetlanie podkatalogów i plików w bieżącym katalogu.
Jeśli chcemy posortować według **LastWriteTime** a następnie według **nazwa**, możemy to zrobić, wpisując:

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
11/6/2017 10:10:11 AM  .localization-config
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:15 AM  tests
6/6/2018 7:58:59 PM    CONTRIBUTING.md
6/6/2018 7:58:59 PM    README.md
...
```

Możesz również obiekty można sortować w kolejności odwrotnej, określając **Descending** parametr przełącznika.

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name -Descending |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  reference
12/1/2018 10:13:50 PM  dsc
...
6/6/2018 7:58:59 PM    README.md
6/6/2018 7:58:59 PM    CONTRIBUTING.md
11/6/2017 10:10:15 AM  tests
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  .localization-config
```

## <a name="using-hash-tables"></a>Przy użyciu tabel skrótów

Inne właściwości w różnej kolejności można sortować przy użyciu tabel skrótów w tablicy.
Każda tabela skrótów używa **wyrażenie** klawisz, aby określić nazwę właściwości jako ciąg i **rosnąco** lub **Descending** klawisz, aby określić kolejność sortowania według `$true` lub `$false`.
**Wyrażenie** klucz jest wymagany.
**Ascending** lub **Descending** klucz jest opcjonalny.

Poniższy przykład sortuje obiektów w malejącej **LastWriteTime** kolejności i rosnącej **nazwa** zamówienia.

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = 'LastWriteTime'; Descending = $true }, @{ Expression = 'Name'; Ascending = $true } |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  dsc
12/1/2018 10:13:50 PM  reference
11/29/2018 6:56:01 PM  .openpublishing.redirection.json
11/29/2018 6:56:01 PM  gallery
11/24/2018 10:33:22 AM developer
11/20/2018 7:22:19 PM  .markdownlint.json
...
```

Można również ustawić scriptblock **wyrażenie** klucza.
Podczas uruchamiania `Sort-Object` polecenia cmdlet, jest wykonywany blok skryptu, a wynik jest używane do sortowania.

Poniższy przykład sortuje obiekty w kolejności malejącej według przedział czasu między **CreationTime** i **LastWriteTime**.

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = { $_.LastWriteTime - $_.CreationTime }; Descending = $true } |
  Format-Table -Property LastWriteTime, CreationTime
```

```output
LastWriteTime          CreationTime
-------------          ------------
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:15 AM
11/3/2018 9:58:17 AM   11/6/2017 10:10:11 AM
10/26/2018 4:50:21 PM  11/6/2017 10:10:11 AM
11/17/2018 1:10:57 PM  11/29/2017 5:48:30 PM
11/12/2018 6:29:53 PM  12/7/2017 7:57:07 PM
...
```

## <a name="tips"></a>Porady

Możesz pominąć **właściwość** Nazwa parametru jako pokazano poniżej:

```powershell
Sort-Object LastWriteTime, Name
```

Ponadto możesz zapoznać się z `Sort-Object` przez jego wbudowanych aliasu `sort`:

```powershell
sort LastWriteTime, Name
```

Klucze w tabelach skrótów do sortowania można stosować skrót, jako pokazano poniżej:

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

W tym przykładzie **e** oznacza **wyrażenie**, **d** oznacza **Descending**i **a** oznacza **rosnąco**.

Aby poprawić czytelność, możesz umieścić tabel skrótów do oddzielnych zmiennej:

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```