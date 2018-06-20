---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 63c3b8237a9883b147380dfe9cb173107cea9aa9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225644"
---
# <a name="updates-to-fileinfo-object"></a>Aktualizacje obiektu FileInfo
Informacje o wersji pliku mogą mylące, szczególnie w przypadkach, w którym plik został poprawkami. Ta wersja platformy WMF 5.0 dodaje nowe **FileVersionRaw** i **ProductVersionRaw** skryptu właściwości FileInfo obiektów. Oto właściwości wyświetlane powershell.exe (przy założeniu, że identyfikator procesu programu PowerShell jest $pid):

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117
