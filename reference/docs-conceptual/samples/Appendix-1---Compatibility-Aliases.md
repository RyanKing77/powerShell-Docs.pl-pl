---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Dodatek 1 Aliasy zgodności
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: 113bbee1af185f98777df5767022d54accb69447
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684689"
---
# <a name="appendix-1---compatibility-aliases"></a>Dodatek 1 - aliasy zgodności

Programu Windows PowerShell zawiera kilka aliasy przejścia, które umożliwiają użytkownikom z systemami UNIX i Cmd, można użyć znanych nazw poleceń w programie Windows PowerShell. Najbardziej typowe aliasy są wyświetlane w poniższej tabeli, wraz z polecenia środowiska Windows PowerShell, aliasu i standardowych alias programu Windows PowerShell, jeśli taka istnieje.

Można znaleźć polecenia programu Windows PowerShell, wskazujący dowolnego aliasu z wnętrza programu Windows PowerShell za pomocą polecenia cmdlet Get-Alias. Na przykład wpisz **get-alias zgodny ze specyfikacją**.

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|Polecenie CMD|Polecenie systemu UNIX|PS Polecenie|PS Alias|
|---------------|----------------|--------------|------------|
|**dir**|**Ls**|**Get-ChildItem**|**gci**|
|**cls**|**Usuń zaznaczenie**|**Wyczyść hosta** (funkcja)|**cls**|
|**DEL, czyszczenie, rmdir**|**rm**|**Remove-Item**|**ri**|
|**Kopiuj**|**cp**|**Kopiuj element**|**ci**|
|**Przenieś**|**mV**|**Move-Item**|**mi**|
|**Zmień nazwę**|**mV**|**Zmień nazwę elementu**|**rni**|
|**type**|**cat**|**Get-Content**|**gc**|
|**cd**|**cd**|**Ustawianie lokalizacji**|**sl**|
|**md**|**mkdir**|**Nowy element**|**ni**|
|**pushd**|**pushd**|**Lokalizacja wypychania**|**pushd**|
|**popd**|**popd**|**Lokalizacji POP**|**popd**|