---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: d9f1ca10c948b06b234e17f688b8f899ed41c5d6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="get-childitem-has--depth-parameter"></a>Get-ChildItem ma - parametr głębokość
**Get-ChildItem** ma teraz **— głębokość** korzystasz z parametru **— Recurse** ograniczenie rekursji:

PS C:\\użytkowników\\slee\\pobiera\\przykład&gt; Get-ChildItem-Recurse - głębokość 0

Katalog: C:\\użytkowników\\slee\\pobiera\\przykład

Nazwa trybu LastWriteTime długość

---- ------------- ------ ----

d---4/14/2015 Depth0 17:36:00

----2015-4-14 13:19 będzie więc Plik1.txt 0

----2015-4-14:19 godz Plik2.txt 0

----2015-4-14:19 godz 0 File3.txt

PS C:\\użytkowników\\slee\\pobiera\\przykład&gt; Get-ChildItem-Recurse - głębokość 1

Katalog: C:\\użytkowników\\slee\\pobiera\\przykład

Nazwa trybu LastWriteTime długość

---- ------------- ------ ----

d---4/14/2015 Depth0 17:36:00

----2015-4-14 13:19 będzie więc Plik1.txt 0

----2015-4-14:19 godz Plik2.txt 0

----2015-4-14:19 godz 0 File3.txt

Katalog: C:\\użytkowników\\slee\\pobiera\\przykład\\Depth0

Nazwa trybu LastWriteTime długość

---- ------------- ------ ----

d---Depth1 5:33 PM 4/14/2015
