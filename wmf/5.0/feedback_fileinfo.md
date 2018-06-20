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
# <a name="updates-to-fileinfo-object"></a><span data-ttu-id="714c0-102">Aktualizacje obiektu FileInfo</span><span class="sxs-lookup"><span data-stu-id="714c0-102">Updates to FileInfo object</span></span>
<span data-ttu-id="714c0-103">Informacje o wersji pliku mogą mylące, szczególnie w przypadkach, w którym plik został poprawkami.</span><span class="sxs-lookup"><span data-stu-id="714c0-103">File version information can be misleading, particularly in cases where the file was patched.</span></span> <span data-ttu-id="714c0-104">Ta wersja platformy WMF 5.0 dodaje nowe **FileVersionRaw** i **ProductVersionRaw** skryptu właściwości FileInfo obiektów.</span><span class="sxs-lookup"><span data-stu-id="714c0-104">This release of WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to FileInfo objects.</span></span> <span data-ttu-id="714c0-105">Oto właściwości wyświetlane powershell.exe (przy założeniu, że identyfikator procesu programu PowerShell jest $pid):</span><span class="sxs-lookup"><span data-stu-id="714c0-105">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117
