---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: cc5d2d799c1292f68de5fb2360fcba220c2c010b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085298"
---
# <a name="get-childitem-has--depth-parameter"></a>Polecenie GET-ChildItem ma parametr - Depth
**Polecenie GET-ChildItem** ma teraz **— głębokość** korzystasz z parametru **— Recurse** ograniczyć rekursji:

PS C:\\użytkowników\\slee\\pliki do pobrania\\przykład&gt; Get-ChildItem-Recurse - głębokość 0

Katalog: C:\\użytkowników\\slee\\pliki do pobrania\\przykład

Tryb LastWriteTime długość nazwy

---- ------------- ------ ----

d---Depth0 o godzinie 17:36 4/14/2015

----4/14/2015 r. 13:19:00 więc Plik1.txt 0

----4/14/2015 r. 13:19:00 Plik2.txt 0

----4/14/2015 r. 13:19:00 0 File3.txt

PS C:\\użytkowników\\slee\\pliki do pobrania\\przykład&gt; Get-ChildItem-Recurse - 1 głębokości

Katalog: C:\\użytkowników\\slee\\pliki do pobrania\\przykład

Tryb LastWriteTime długość nazwy

---- ------------- ------ ----

d---Depth0 o godzinie 17:36 4/14/2015

----4/14/2015 r. 13:19:00 więc Plik1.txt 0

----4/14/2015 r. 13:19:00 Plik2.txt 0

----4/14/2015 r. 13:19:00 0 File3.txt

Katalog: C:\\użytkowników\\slee\\pliki do pobrania\\przykład\\Depth0

Tryb LastWriteTime długość nazwy

---- ------------- ------ ----

d---Depth1 o godzinie 17:33 4/14/2015
