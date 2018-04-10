---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Dodatek 1 Aliasy zgodności
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: 113bbee1af185f98777df5767022d54accb69447
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="appendix-1---compatibility-aliases"></a>Dodatek 1 - zgodność aliasów

Programu Windows PowerShell zawiera kilka aliasy przejścia, których użytkownicy systemów UNIX i Cmd do używania nazwy znanych poleceń w programie Windows PowerShell. Najbardziej typowe aliasy przedstawiono w poniższej tabeli, wraz z polecenia programu Windows PowerShell za alias i standardowe alias programu Windows PowerShell, jeśli taka istnieje.

Można znaleźć polecenia programu Windows PowerShell, wskazujące dowolnego aliasu z wewnątrz środowiska Windows PowerShell za pomocą polecenia cmdlet Get-aliasu. Na przykład wpisz **get-alias ze specyfikacją cls**.

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|Polecenie CMD|Polecenie systemu UNIX|PS Polecenie|PS Alias|
|---------------|----------------|--------------|------------|
|**dir**|**Ls**|**Get-ChildItem**|**gci**|
|**ze specyfikacją CLS**|**Wyczyść**|**Wyczyść hosta** (funkcja)|**ze specyfikacją CLS**|
|**DEL, czyszczenie, rmdir**|**rm**|**Remove-Item**|**ri**|
|**copy**|**cp**|**Copy-Item**|**ci**|
|**Przenieś**|**mv**|**Move-Item**|**mi**|
|**Zmień nazwę**|**mv**|**Rename-Item**|**rni**|
|**Typ**|**cat**|**Get-Content**|**gc**|
|**cd**|**cd**|**Set-Location**|**sl**|
|**md**|**mkdir**|**New-Item**|**ni**|
|**pushd**|**pushd**|**Lokalizacja wypychania**|**pushd**|
|**popd**|**popd**|**Lokalizacji POP**|**popd**|