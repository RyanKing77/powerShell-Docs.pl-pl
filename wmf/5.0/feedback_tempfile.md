---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: 90e0ab3579e1840598cc3050c27db0b73ba6f69d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="new-temporaryfile"></a>Nowe TemporaryFile
Czasami w skryptach, można utworzyć pliku tymczasowego. Można łatwo to zrobić z **TemporaryFile nowy** polecenia cmdlet:

PS C:\\ &gt; $tempFile = New-TemporaryFile

PS C:\\ &gt; $tempFile.FullName

C:\\użytkowników\\slee\\AppData\\lokalnego\\Temp\\tmp375.tmp

