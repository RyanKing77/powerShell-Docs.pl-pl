---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: 4185d9395f2f3e5ba1c8daa0c365cb2bf322936b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
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

