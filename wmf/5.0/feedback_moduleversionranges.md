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
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="db33b-102">Obsługa modułów na potrzeby deklarowania zakresów wersji (1.\* itp.)</span><span class="sxs-lookup"><span data-stu-id="db33b-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="db33b-103">W połączeniu z **- MinimumVersion**, **- MaximumVersion** teraz umożliwia użytkownikowi get/importu modułu w obrębie określonego zakresu.</span><span class="sxs-lookup"><span data-stu-id="db33b-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="db33b-104">Obsługiwane jest również parametr **.** \*.</span><span class="sxs-lookup"><span data-stu-id="db33b-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="db33b-105">Poniższy przykład pokazuje, jak to działa:</span><span class="sxs-lookup"><span data-stu-id="db33b-105">The following example shows how it works:</span></span>

<span data-ttu-id="db33b-106">Teraz możesz połączyć **- MinimumVersion** i **- MaximumVersion** można zaimportować modułu w określonym zakresie:</span><span class="sxs-lookup"><span data-stu-id="db33b-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

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
