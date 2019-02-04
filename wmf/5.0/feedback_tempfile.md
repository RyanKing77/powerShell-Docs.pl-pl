---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: aa2e9540af8b3d4c5de5e00377a84e0e5edd6e4a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685116"
---
# <a name="new-temporaryfile"></a>New-TemporaryFile
Czasami w skryptach, można utworzyć pliku tymczasowego. Łatwo to zrobić za pomocą **New TemporaryFile** polecenia cmdlet:

PS C:\\&gt; $tempFile = New-TemporaryFile

PS C:\\&gt; $tempFile.FullName

C:\\użytkowników\\slee\\AppData\\lokalnego\\Temp\\tmp375.tmp
