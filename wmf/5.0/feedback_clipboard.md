---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: d34a267bae7e48afe4442256d7f112da3a97eb7d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
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