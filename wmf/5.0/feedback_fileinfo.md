---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5280ef5ff95679dc8721be8f5f81031a4ffe796f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687069"
---
# <a name="updates-to-fileinfo-object"></a><span data-ttu-id="1abfc-102">Aktualizacje obiektu FileInfo</span><span class="sxs-lookup"><span data-stu-id="1abfc-102">Updates to FileInfo object</span></span>
<span data-ttu-id="1abfc-103">Informacje o wersji pliku mogą mylące, zwłaszcza w przypadkach, w którym plik został poprawek.</span><span class="sxs-lookup"><span data-stu-id="1abfc-103">File version information can be misleading, particularly in cases where the file was patched.</span></span> <span data-ttu-id="1abfc-104">Ta wersja programu WMF 5.0 dodaje nowe **FileVersionRaw** i **ProductVersionRaw** właściwości do obiektów FileInfo skryptu.</span><span class="sxs-lookup"><span data-stu-id="1abfc-104">This release of WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to FileInfo objects.</span></span> <span data-ttu-id="1abfc-105">Oto właściwości wyświetlane powershell.exe (przy założeniu, że $pid jest identyfikator procesu programu PowerShell):</span><span class="sxs-lookup"><span data-stu-id="1abfc-105">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117
