---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: e6b54519d878ab572662075709beb4cf4454b0c6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="clipboard-cmdlets"></a>Polecenia cmdlet schowka
**Get-Schowka** i **Schowka zestaw** ułatwić przesyłanie zawartości do i z sesji środowiska Windows PowerShell. Na przykład skopiuj trzy pliki do Schowka za pomocą Eksploratora Windows (zaznaczając je i naciskając klawisz `ctrl-c`, na przykład), następnie móc zawartość Schowka jako lista plików:

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


Polecenia cmdlet Schowek obsługuje obrazów, plików audio listy plików i tekst.
