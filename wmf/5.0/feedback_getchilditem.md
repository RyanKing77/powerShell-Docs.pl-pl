---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 62cccabd7c63c6ba928fc2bf8addd3d11483e90f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
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