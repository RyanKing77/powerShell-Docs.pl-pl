---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: e2c9233734a6ede04e8ec2bbad05950cbb31cbba
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057514"
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a>Obsługa modułów na potrzeby deklarowania zakresów wersji (1.* itp.)
W połączeniu z **- MinimumVersion**, **- MaximumVersion** teraz umożliwia użytkownikowi get/importu modułu w obrębie określonego zakresu. Obsługiwane jest również parametr **.** \*. Poniższy przykład pokazuje, jak to działa:

Teraz możesz połączyć **- MinimumVersion** i **- MaximumVersion** można zaimportować modułu w określonym zakresie:

```powershell
PS C:\> Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*

VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```
