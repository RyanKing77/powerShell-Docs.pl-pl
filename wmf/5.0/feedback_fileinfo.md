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
# <a name="updates-to-fileinfo-object"></a>Aktualizacje obiektu FileInfo
Informacje o wersji pliku mogą mylące, zwłaszcza w przypadkach, w którym plik został poprawek. Ta wersja programu WMF 5.0 dodaje nowe **FileVersionRaw** i **ProductVersionRaw** właściwości do obiektów FileInfo skryptu. Oto właściwości wyświetlane powershell.exe (przy założeniu, że $pid jest identyfikator procesu programu PowerShell):

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117
