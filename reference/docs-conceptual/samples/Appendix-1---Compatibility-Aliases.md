---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Dodatek 1 Aliasy zgodności
ms.openlocfilehash: 553b9f01d6b5e3f4e04f1a75c25979b54dc205da
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030327"
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
