---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: d5ec95abb1d3160afc4179cff991cb5ef72d85fe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057302"
---
# <a name="clipboard-cmdlets"></a>Polecenia cmdlet schowka
**Get-Schowka** i **Schowka zestaw** ułatwić transferu zawartości do i z sesji środowiska Windows PowerShell. Na przykład, jeśli korzystasz z Eksploratora Windows do skopiowania trzy pliki do Schowka (wybierając je i naciskając klawisz `ctrl-c`, na przykład), następnie łatwo dostępnej zawartość Schowka jako lista plików:

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


Polecenia cmdlet Schowka obsługuje obrazy, pliki audio, listy plików i tekst.
