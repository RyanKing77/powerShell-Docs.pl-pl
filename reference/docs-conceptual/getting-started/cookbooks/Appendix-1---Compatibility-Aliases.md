---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Dodatek 1 zgodności aliasów"
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: d789139ef80d4208b56e0b2930f04f824a00537d
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2017
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
|**dir**|**ls**|**Get-ChildItem**|**gci**|
|**ze specyfikacją CLS**|**Wyczyść**|**Wyczyść hosta** (funkcja)|**ze specyfikacją CLS**|
|**DEL, czyszczenie, rmdir**|**Menedżer zasobów**|**Usuń element**|**RI**|
|**Kopiuj**|**Zasady certyfikatów**|**Kopiuj element**|**elementu konfiguracji**|
|**Przenieś**|**mV**|**Przenieś element**|**mi**|
|**Zmień nazwę**|**mV**|**Zmiana nazwy elementu**|**rni**|
|**Typ**|**CAT**|**Get zawartości**|**wykaz globalny**|
|**dysku CD**|**dysku CD**|**Ustawianie lokalizacji**|**SL**|
|**MD**|**mkdir**|**Nowy element**|**Ni**|
|**pushd**|**pushd**|**Lokalizacja wypychania**|**pushd**|
|**popd**|**popd**|**Lokalizacji POP**|**popd**|

