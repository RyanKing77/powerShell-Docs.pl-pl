---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: fa972b68015d9b6e14508ccda562cfa5ebd632ac
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2018
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="9f274-102">Obsługa modułów deklarowania zakresu (1.\* itp.)</span><span class="sxs-lookup"><span data-stu-id="9f274-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="9f274-103">Połączone z **- MinimumVersion**, **- MaximumVersion** teraz zezwala użytkownikowi na module get/import określonego zakresu.</span><span class="sxs-lookup"><span data-stu-id="9f274-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="9f274-104">Obsługiwane jest również parametr \*\*. \*\*\*.</span><span class="sxs-lookup"><span data-stu-id="9f274-104">The parameter also support \*\*.\*\*\*.</span></span> <span data-ttu-id="9f274-105">W poniższym przykładzie pokazano, jak to działa:</span><span class="sxs-lookup"><span data-stu-id="9f274-105">The following example shows how it works:</span></span>

```powershell
Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:

PS C:\> Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*

VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

