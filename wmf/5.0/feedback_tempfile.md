---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 08f431c27cd0ee769518b5246af2fa95aa499d54
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34217995"
---
# <a name="new-temporaryfile"></a>New-TemporaryFile
Czasami w skryptach, można utworzyć pliku tymczasowego. Można łatwo to zrobić z **TemporaryFile nowy** polecenia cmdlet:

PS C:\\ &gt; $tempFile = New-TemporaryFile

PS C:\\ &gt; $tempFile.FullName

C:\\użytkowników\\slee\\AppData\\lokalnego\\Temp\\tmp375.tmp
