---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: aa2e9540af8b3d4c5de5e00377a84e0e5edd6e4a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057859"
---
# <a name="new-temporaryfile"></a>New-TemporaryFile
Czasami w skryptach, można utworzyć pliku tymczasowego. Łatwo to zrobić za pomocą **New TemporaryFile** polecenia cmdlet:

PS C:\\&gt; $tempFile = New-TemporaryFile

PS C:\\&gt; $tempFile.FullName

C:\\użytkowników\\slee\\AppData\\lokalnego\\Temp\\tmp375.tmp
