---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Dodatek 1 Aliasy zgodności
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: 113bbee1af185f98777df5767022d54accb69447
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405555"
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
|**dir**|**Ls**|**Polecenie GET-ChildItem**|**gci**|
|**ze specyfikacją CLS**|**Usuń zaznaczenie**|**Wyczyść hosta** (funkcja)|**ze specyfikacją CLS**|
|**DEL, czyszczenie, rmdir**|**Menedżer zasobów**|**Usuń element**|**wystąpienie zarezerwowane**|
|**Kopiuj**|**CP**|**Kopiuj element**|**ciągła Integracja**|
|**Przenieś**|**mV**|**Przenieś element**|**wystąpienia zarządzanego**|
|**Zmień nazwę**|**mV**|**Zmień nazwę elementu**|**rni**|
|**Typ**|**CAT**|**Pobierz zawartość**|**odzyskiwanie pamięci**|
|**ciągłe dostarczanie**|**ciągłe dostarczanie**|**Ustawianie lokalizacji**|**SL**|
|**MD**|**mkdir**|**Nowy element**|**Ni**|
|**pushd**|**pushd**|**Lokalizacja wypychania**|**pushd**|
|**popd**|**popd**|**Lokalizacji POP**|**popd**|